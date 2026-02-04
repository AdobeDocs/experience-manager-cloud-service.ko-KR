---
title: 게시 인스턴스에서 연결 UI 호출
description: 게시할 때 AEM Forms Associate UI를 통합하고 호출하여 고객 지원 전문가가 실시간으로 개인화된 대화형 커뮤니케이션을 생성할 수 있도록 하는 방법에 대해 알아봅니다.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
hidefromtoc: true
source-git-commit: bfee883205f81012fea75cbd7dc5fddd7169fdbb
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 2%

---


# UI를 연결하여 개인화된 커뮤니케이션 생성

<span> 대화형 통신 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 주소에서 `aem-forms-ea@adobe.com`(으)로 전자 메일을 보내십시오.</span>

Associate UI는 게시 인스턴스에서 직접 호출할 수 있으므로 필드 연결자 및 서비스 에이전트와 같은 고객 응대 전문가가 고객 상호 작용 중에 실시간으로 개인화된 커뮤니케이션을 생성할 수 있습니다.

아래 표는 UI 연결 을 통해 고객에게 개인화된 메시지를 보낼 수 있는 다양한 실제 시나리오를 보여 줍니다.

| 업계 | 사용 사례 |
|----------|----------|
| **금융 서비스** | 고객 미팅 중 실시간 대출 확인서, 계정 명세서 및 위험 프로필 요약 생성 |
| **보험** | 즉시 보험 증빙 카드 제작 및 서비스 카운터에서 청구 처리 요약 작성 |
| **헬스 케어** | 계산된 급여 금액 및 일정을 사용하여 환자 치료 계획 요약 생성 |
| **정부** | 즉석에서 경찰 확인 보고서, 시민 서비스 영수증 및 사례 업데이트 요약 생성 |

## 사전 요구 사항

UI와 응용 프로그램을 통합하기 전에 다음을 확인하십시오.

- 만들어진 대화형 통신 및 게시됨
- 팝업 지원이 활성화된 브라우저
- [사용자 연결은 forms-associates 그룹의 일부여야 합니다](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-roles#assign-a-role-to-users-and-groups)
- AEM[에서 지원하는 &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/authentication)인증 메커니즘을 사용하여 구성된 인증(예: SAML 2.0, OAuth 또는 사용자 지정 인증 처리기)

>[!NOTE]
>
>- 이 문서에서는 [Microsoft AD(Azure AD) ID가 있는 SAML 2.0을 ID 공급자](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings)로 사용하는 인증 구성을 보여 줍니다.
>- 연결 UI의 경우 [SAML 2.0 인증](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) 문서에 설명된 표준 설정 이상의 추가 SAML 구성이 필요합니다. 자세한 내용은 [UI 연결에 대한 추가 SAML 구성](#additional-saml-configurations-for-associate-ui) 섹션을 참조하십시오.

### 연결 UI에 대한 추가 SAML 구성

연결 UI에 대한 SAML 2.0 인증을 구성할 때 OSGi 구성 파일에 다음과 같은 특정 설정을 적용해야 합니다.

#### SAML 인증 핸들러

`com.adobe.granite.auth.saml.SamlAuthenticationHandler~saml.cfg.json`에서 `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` 파일 만들기:

```json
  {
    "path": ["/libs/fd/associate"],
    "serviceProviderEntityId": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com",
    "assertionConsumerServiceURL": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/saml_login"
    "idpUrl": "https://login.microsoftonline.com/{azure-tenant-id}/saml2",
    "idpCertAlias": "{your-certificate-alias}",
    "idpIdentifier": "https://sts.windows.net/{azure-tenant-id}/",
    "userIDAttribute": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
    "createUser": true,
    "userIntermediatePath": "saml",
    "synchronizeAttributes": [
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname=profile/givenName",
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname=profile/familyName",
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress=profile/email"
      ],
      "addGroupMemberships": true,
      "defaultGroups": ["forms-associates"],
      "defaultRedirectUrl": "/libs/fd/associate/ui.html",
      "idpHttpRedirect": false,
      "service.ranking": 5002
  }
```

| 속성 | 설명 |
|----------|-------------|
| `path` | UI 연결에 대해 `/libs/fd/associate`(으)로 설정해야 합니다. |
| `defaultGroups` | 사용자를 필수 그룹에 자동으로 할당하려면 `forms-associates`(으)로 설정하십시오. |
| `defaultRedirectUrl` | 인증된 사용자를 연결 UI로 리디렉션합니다 |
| `idpHttpRedirect` | SP에서 시작된 흐름의 경우 `false`이어야 합니다. |
| `idpCertAlias` | Trust Store의 인증서 별칭과 정확히 일치해야 합니다(대/소문자 구분). |

#### Sling 인증자

`org.apache.sling.engine.impl.auth.SlingAuthenticator~saml.cfg.json`에서 `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` 파일 업데이트:

```json
{
  "sling.auth.requirements": ["+/libs/fd/associate/ui.html"],
  "sling.auth.anonymous": false
}
```

#### Dispatcher 필터

아직 없으면 `dispatcher/src/conf.dispatcher.d/filters/filters.any` 파일에 다음 규칙을 추가합니다.

```json
  # Allow Interactive Communications APIs and Associate UI
  /XXXX { /type "allow" /method '(GET|OPTIONS)' /url "/adobe/communications" }
  /XXXX { /type "allow" /method '(GET|POST|OPTIONS)' /url "/adobe/communications/*" }
  /XXXX { /type "allow" /method "GET" /url "/content/dam/fd:fonts/*" }
  /XXXX { /type "allow" /method '(GET|OPTIONS)' /url "/libs/fd/associate/*" }
```

>[!NOTE]
>
> `XXXX`을(를) 기존 `filters.any` 파일에 사용된 적절한 숫자 시퀀스로 바꾸십시오.

## 게시 인스턴스에서 UI 연결 호출

응용 프로그램에서 연결 UI를 호출하려면 게시 인스턴스 URL을 구성하고, 데이터 페이로드를 준비하고, 통합 기능을 사용하여 새 브라우저 창에서 연결 UI를 시작합니다.

### 1단계: 게시 인스턴스 URL 구성

연결 UI는 AEM Forms Cloud Service 게시 인스턴스의 특정 끝점을 통해 액세스할 수 있습니다.

```javascript
const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
```

`{program-id}` 및 `{env-id}`을(를) 실제 환경 값으로 바꾸십시오.

보안상의 이유로 대화형 통신 ID, 미리 채우기 서비스 및 서비스 매개 변수와 같은 매개 변수는 URL을 통해 전달되지 않습니다. 대신 이러한 매개 변수는 브라우저의 postMessage API를 통해 연결 UI와 통신하는 JavaScript 함수를 사용하여 안전하게 전달됩니다.

### 2단계: 데이터 페이로드 준비

데이터 페이로드를 다음 형식으로 구성합니다.

```javascript
const data = {
  id: "your-ic-id",              // Required: Interactive Communication ID
  prefill: {                      // Optional: Data to prefill the IC
    serviceName: "YourService",
    serviceParams: { key: "value" }
  },
  options: {}                     // Optional: Additional configuration options
};
```

**페이로드 구성 요소:**

| 구성 요소 | 필수 | 설명 |
|-----------|----------|-------------|
| `id` | 예 | 로드할 대화형 통신(IC)의 식별자 |
| `prefill` | 선택 사항 | 데이터 미리 채우기에 대한 서비스 구성을 포함합니다. |
| `prefill.serviceName` | 선택 사항 | 데이터 미리 채우기를 위해 호출할 양식 데이터 모델 서비스 이름 |
| `prefill.serviceParams` | 선택 사항 | 미리 채우기 서비스에 전달된 키-값 쌍 |
| `options` | 선택 사항 | PDF 렌더링에 지원되는 추가 속성 - locale, includeAttachments, embedFonts, makeAccessible |

### 3단계: 통합 기능 구현

JavaScript 함수를 만들어 Associate UI를 시작하고 메시지 통신을 처리합니다.

```javascript
function launchAssociateUI(icId, prefillService, prefillParams, options) {
  if (!icId) {
    console.error('IC ID required');
    return;
  }
   
  const data = {
    id: icId,
    prefill: {
      serviceName: prefillService || '',
      serviceParams: prefillParams || {}
    },
    options: options || {}
  };
   
  const AEM_URL = 'https://your-aem.adobeaemcloud.com/libs/fd/associate/ui.html';
  const win = window.open(AEM_URL, '_blank');
   
  if (!win) {
    alert('Please enable pop-ups for this site');
    return;
  }
   
  const readyHandler = (event) => {
    if (event.data && event.data.type === 'READY' && event.data.source === 'APP') {
      win.postMessage({ type: 'INIT', source: 'PORTAL', data: data }, '*');
      window.removeEventListener('message', readyHandler);
    }
  };
   
  window.addEventListener('message', readyHandler);
   
  // Fallback timeout in case READY message is missed
  setTimeout(() => {
    if (win && !win.closed) {
      win.postMessage({ type: 'INIT', source: 'PORTAL', data: data }, '*');
      window.removeEventListener('message', readyHandler);
    }
  }, 1000);
}
```

### 4단계: 함수 호출

적절한 매개 변수를 사용하여 함수를 호출합니다.

```javascript
// Basic invocation with IC ID only
launchAssociateUI('12345', '', {}, {});

// With prefill service
launchAssociateUI('12345', 'IC_FDM', 
  { customerId: '101'}, {});

// With all parameters
launchAssociateUI('12345', 'IC_FDM', 
  { customerId: "101" }, 
  { locale: 'en', includeAttachments: "true" });
```

## 샘플 HTML 페이지와 통합 테스트

연결 UI가 프론트엔드에 어떻게 표시되는지 관찰하고 통합을 테스트하려면 다음 간단한 HTML 예를 참조하십시오. 이 샘플 페이지에서는 IC ID를 입력하고, 서비스 매개 변수 미리 채우기를 구성하고, PDF 옵션을 설정하고, 게시 인스턴스에서 연결 UI를 시작할 수 있습니다.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Associate UI Integration</title>
  <style>
    body { 
      font-family: sans-serif; 
      max-width: 600px; 
      margin: 50px auto; 
      padding: 20px; 
    }
    .form-group { 
      margin: 20px 0; 
    }
    label { 
      display: block; 
      margin-bottom: 5px; 
      font-weight: bold; 
    }
    input, textarea { 
      width: 100%; 
      padding: 8px; 
      border: 1px solid #ccc; 
      border-radius: 4px; 
      box-sizing: border-box;
    }
    textarea { 
      height: 80px; 
      font-family: monospace; 
    }
    button { 
      padding: 10px 20px; 
      margin: 5px; 
      cursor: pointer; 
      border-radius: 4px;
    }
    .btn-primary { 
      background: #007bff; 
      color: white; 
      border: none; 
    }
    .btn-primary:hover {
      background: #0056b3;
    }
    .error { 
      color: red; 
      font-size: 12px; 
      display: none; 
    }
  </style>
</head>
<body>
  <h1>Launch Associate UI</h1>
  
  <form id="form">
    <div class="form-group">
      <label>IC ID *</label>
      <input type="text" id="icId" placeholder="Enter Interactive Communication ID" required>
    </div>
    
    <div class="form-group">
      <label>Prefill Service</label>
      <input type="text" id="serviceName" placeholder="e.g., CustomerDataService">
    </div>
    
    <div class="form-group">
      <label>Service Parameters (JSON)</label>
      <textarea id="serviceParams" placeholder='{"customerId": "12345"}'>{}</textarea>
      <span id="paramsError" class="error">Invalid JSON format</span>
    </div>
    
    <div class="form-group">
      <label>Options (JSON)</label>
      <textarea id="options" placeholder='{"mode": "edit", "locale": "en_US"}'>{}</textarea>
      <span id="optionsError" class="error">Invalid JSON format</span>
    </div>
    
    <button type="button" onclick="reset()">Reset</button>
    <button type="button" class="btn-primary" onclick="launch()">Launch Associate UI</button>
  </form>

  <script>
    // Replace with your AEM Publish instance URL
    const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
    
    function validateJSON(str, errorId) {
      const err = document.getElementById(errorId);
      try {
        const obj = JSON.parse(str || '{}');
        err.style.display = 'none';
        return obj;
      } catch (e) {
        err.style.display = 'block';
        return null;
      }
    }
    
    function launch() {
      const icId = document.getElementById('icId').value.trim();
      if (!icId) { 
        alert('IC ID is required'); 
        return; 
      }
      
      const params = validateJSON(document.getElementById('serviceParams').value, 'paramsError');
      const opts = validateJSON(document.getElementById('options').value, 'optionsError');
      
      if (!params || !opts) { 
        alert('Please fix JSON errors before launching'); 
        return; 
      }
      
      const data = {
        id: icId,
        prefill: {
          serviceName: document.getElementById('serviceName').value.trim(),
          serviceParams: params
        },
        options: opts
      };
      
      const win = window.open(AEM_URL, '_blank');
      if (!win) { 
        alert('Pop-up blocked. Please enable pop-ups for this site.'); 
        return; 
      }
      
      const handler = (e) => {
        if (e.data && e.data.type === 'READY' && e.data.source === 'APP') {
          win.postMessage({ type: 'INIT', source: 'PORTAL', data }, '*');
          window.removeEventListener('message', handler);
        }
      };
      
      window.addEventListener('message', handler);
      
      // Fallback timeout in case READY message is missed
      setTimeout(() => {
        if (win && !win.closed) {
          win.postMessage({ type: 'INIT', source: 'PORTAL', data }, '*');
          window.removeEventListener('message', handler);
        }
      }, 1000);
    }
    
    function reset() {
      document.getElementById('form').reset();
      document.getElementById('serviceParams').value = '{}';
      document.getElementById('options').value = '{}';
      document.getElementById('paramsError').style.display = 'none';
      document.getElementById('optionsError').style.display = 'none';
    }
  </script>
</body>
</html>
```

### 샘플 작동 방식

1. **IC ID 필드**: 대화형 통신 식별자를 입력하십시오(필수).
2. **미리 채우기 서비스**: 미리 채우기에 사용할 양식 데이터 모델 서비스 이름을 지정합니다.
3. **서비스 매개 변수**: 미리 채우기 서비스에 전달할 매개 변수와 함께 JSON 개체를 입력하십시오.
4. **옵션**: PDF에 대한 구성 옵션(예: locale, includeAttachments, embedFonts, makeAccessible)을 입력하십시오.
5. **시작 단추**: 새 창에서 연결 UI를 열고 초기화 데이터를 보냅니다.

## 데이터 페이로드 예

### 최소 페이로드(IC만 해당)

미리 채우기 데이터가 필요하지 않은 경우 이 옵션을 사용합니다.

```json
{
  "id": "12345",
  "prefill": { 
    "serviceName": "", 
    "serviceParams": {} 
  },
  "options": {}
}
```

### 미리 채우기 데이터 사용

이를 사용하여 IC를 고객 데이터로 동적으로 채웁니다.

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "IC_FDM",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": {}
}
```

### 옵션 구성

추가 렌더링 옵션을 지정하려면 이 옵션을 사용합니다.

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "IC_FDM",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": { 
      locale: "en_US",
      includeAttachments: "true",
      webOptimized: "false",
      embedFonts: "false",
      makeAccessible: "false"
  }
}
```

## 문제 해결

### 팝업이 차단됨

**문제**: UI 연결 창이 열리지 않습니다.

**솔루션**:
- 브라우저 설정에서 도메인에 대한 팝업 활성화
- `window.open()`이(가) 사용자 작업(예: 단추 클릭)에서 호출되는지 확인
- 다양한 브라우저로 테스트하여 차단 동작을 식별하십시오.

### 데이터 로드 안 됨

**문제**: 대화형 통신이 열리지만 데이터가 채워지지 않습니다.

**솔루션**:
- IC ID가 올바르고 IC가 게시되었는지 확인
- 브라우저 콘솔에서 JavaScript 오류 확인
- `postMessage` 구조가 사양과 정확히 일치하는지 확인합니다.
- 양식 데이터 모델 서비스가 올바르게 구성되었는지 확인

### 인증 오류

**문제**: 연결 UI가 열릴 때 사용자에게 인증 오류가 표시됩니다.

**솔루션**:
- 게시 인스턴스에서 SAML 2.0 인증 구성
- 사용자가 **forms-associates** 그룹에 속해 있는지 확인하십시오
- 세션 시간 초과 설정 확인

### CORS 오류

**문제**: 콘솔에서 원본 간 리소스 공유 오류가 발생했습니다.

**솔루션**:
- 개발용: `'*'`에서 `postMessage`을(를) 대상 원본으로 사용
- 프로덕션의 경우: 애플리케이션의 정확한 원본 URL을 지정합니다
- 게시 인스턴스 CORS 설정이 응용 프로그램 도메인을 허용하는지 확인합니다.

<!--## Best Practices

When implementing the Associate UI integration, follow these best practices:

1. **Validation**: Always validate the IC ID and JSON payload before sending
2. **Error Handling**: Implement proper error handling for `window.open()` failures
3. **User Experience**: Display a loading indicator while the Associate UI initializes
4. **Memory Management**: Remove event listeners after initialization to prevent memory leaks
5. **Testing**: Test the integration with popup blockers enabled to ensure graceful handling
6. **User Permissions**: Verify users have appropriate access to the forms-associates group-->

## 추가 참조

- [대화형 통신 편집기에서 UI 연결](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [클라우드의 대화형 통신](/help/forms/early-access-ea-features.md#interactive-communications-on-cloud)
- [조기 액세스 기능](/help/forms/early-access-ea-features.md)