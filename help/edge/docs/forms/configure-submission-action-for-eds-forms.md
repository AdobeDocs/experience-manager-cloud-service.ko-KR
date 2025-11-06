---
title: Edge Delivery Services를 사용하여 AEM Forms에 제출 액션 구성
description: Edge Delivery Services를 사용하여 AEM Forms에서 제출 액션을 구성하는 방법을 알아봅니다. 안전하고 효율적으로 양식 데이터를 처리하려면 Forms 제출 서비스와 AEM Publish 제출 액션 중에서 선택합니다.
feature: Edge Delivery Services
role: Admin, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 100%

---

# AEM Forms에 대한 제출 액션 구성

AEM Forms with Edge Delivery Services를 사용하여 양식 제출 처리를 구성하여 데이터를 스프레드시트, 이메일 또는 백엔드 시스템으로 라우팅합니다.

## 빠른 결정 안내서

제출 방법을 선택합니다.

| 메서드 | 적합한 대상 | 설정 복잡성 | 사용 사례 |
|--------|----------|------------------|-----------|
| **Forms 제출 서비스** | 간단한 데이터 캡처 | 낮음 | 연락처 양식, 설문 조사, 기본 데이터 수집 |
| **AEM Publish 제출** | 복잡한 워크플로 | 높음 | 엔터프라이즈 통합, 사용자 정의 처리, 워크플로 |

## 사전 요구 사항

제출 작업을 구성하기 전에 다음 사항을 확인합니다.

- AEM Forms as a Cloud Service 인스턴스
- Edge Delivery Services 프로젝트 구성
- 문서 작성 또는 범용 편집기를 사용하여 생성된 양식
- 타기팅된 대상(스프레드시트, 이메일 시스템 또는 AEM)에 필요한 권한

+++ 방법 1: 양식 제출 서비스

Forms 제출 서비스는 간단한 데이터 캡처 시나리오에 이상적인 Adobe에서 호스팅하는 엔드포인트입니다.

### 지원되는 대상

- **스프레드시트**: Google Sheets, Microsoft Excel (OneDrive/SharePoint)
- **이메일**: 양식 데이터를 지정된 이메일 주소로 보냅니다.

### 구성 단계

1. **대상 액세스 설정**
   - 스프레드시트의 경우: 대상 스프레드시트에서 `forms@adobe.com`에 편집 권한을 부여합니다.
   - 이메일의 경우: 수신자 이메일 주소에 액세스할 수 있는지 확인합니다.

2. **양식 제출 구성**
   - 저작 환경에서 양식을 엽니다.
   - 제출 작업을 “Forms 제출 서비스”로 설정합니다.
   - 대상 스프레드시트 URL 또는 이메일 주소를 지정합니다.
   - 양식을 저장하고 게시합니다.

3. **테스트 제출**
   - 양식을 통해 테스트 데이터를 제출합니다.
   - 타기팅된 대상에 데이터가 표시되는지 확인합니다.
   - 제출이 실패하면 오류 로그를 확인합니다.

### 중요 참고 사항

- 서비스 계정 `forms@adobe.com`에는 대상 스프레드시트에 대한 편집 액세스 권한이 필요합니다.
- 양식 제출 시 이메일 알림이 즉시 전송됩니다.
- 데이터 유효성 검사는 서비스 수준에서 발생합니다.

![양식 제출 서비스 플로우](/help/forms/assets/eds-fss.png)

+++

+++ 방법 2: AEM Publish 제출

복잡한 처리를 위해 양식 데이터를 AEM as a Cloud Service 게시 인스턴스에 직접 제출합니다.

### AEM 게시 사용 시기

- 제출 후 사용자 정의 AEM 워크플로가 필요한 경우
- 데이터베이스와 양식 데이터 모델(FDM) 통합
- 서드파티 서비스 통합 (Marketo, Power Automate, Workfront Fusion)
- Azure Blob Storage 또는 SharePoint 문서 라이브러리
- 복잡한 서버측 유효성 검사 또는 처리 논리

### 사용 가능한 제출 작업

- [REST 엔드포인트에 제출](/help/forms/configure-submit-action-restpoint.md)
- [AEM 메일 서비스를 통해 이메일 보내기](/help/forms/configure-submit-action-send-email.md)
- [양식 데이터 모델을 사용하여 제출](/help/forms/configure-data-sources.md)
- [AEM 워크플로 호출](/help/forms/aem-forms-workflow-step-reference.md)
- [SharePoint에 제출](/help/forms/configure-submit-action-sharepoint.md)
- [OneDrive에 제출](/help/forms/configure-submit-action-onedrive.md)
- [Azure Blob Storage에 제출](/help/forms/configure-submit-action-azure-blob-storage.md)
- [Microsoft Power Automate에 제출](/help/forms/forms-microsoft-power-automate-integration.md)
- [Adobe Workfront Fusion에 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [Adobe Marketo Engage에 제출](/help/forms/submit-adaptive-form-to-marketo-engage.md)

![AEM Publish 제출 플로우](/help/forms/assets/eds-aem-publish.png)

### 구성 요구 사항

#### &#x200B;1. Edge Delivery에서 AEM 인스턴스 URL 업데이트

`submitBaseUrl`의 `form` 블록 `constant.js` 파일에서 AEM Cloud Service 인스턴스 URL을 업데이트합니다. 사용자 환경에 따라 URL을 구성할 수 있습니다.

**클라우드 서비스 인스턴스의 경우**

```js
export const submitBaseUrl = '<aem-publish-instance-URL>';
```

**로컬 개발의 경우**

```js
export const submitBaseUrl = 'http://localhost:<port-number>';
```

#### &#x200B;2. OSGi 레퍼러 필터

특정 Edge Delivery 사이트 도메인을 허용하도록 참조자 필터 구성:

1. OSGi 구성 파일을 생성하거나 업데이트합니다. `org.apache.sling.security.impl.ReferrerFilter.cfg.json`

2. 특정 사이트 도메인에 다음 구성을 추가:

   ```json
   {
     "allow.empty": false,
     "allow.hosts": [
       "main--abc--adobe.aem.live",
       "main--abc1--adobe.aem.live"
     ],
     "allow.hosts.regexp": [
       "https://.*\\.aem\\.live:443",
       "https://.*\\.aem\\.page:443",
       "https://.*\\.hlx\\.page:443",
       "https://.*\\.hlx\\.live:443"
     ],
     "filter.methods": [
       "POST",
       "PUT",
       "DELETE",
       "COPY",
       "MOVE"
     ],
     "exclude.agents.regexp": [
       ""
     ]
   }
   ```

3. Cloud Manager를 통해 구성 배포

자세한 OSGi 참조자 필터 구성은 [참조자 필터](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter) 안내서를 참조하십시오.

#### &#x200B;3. CORS(원본 간 리소스 공유) 문제

AEM에서 CORS 설정을 구성하여 특정 Edge Delivery 사이트 도메인의 요청 허용:

**개발자 Localhost**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true
```

**Edge Delivery 사이트 - 각 사이트 도메인을 개별적으로 추가**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true
```

**이전 Franklin 도메인 (아직 사용 중인 경우)**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

>[!NOTE]
>
>`main--abc--adobe.aem.live` 및 `main--abc1--adobe.aem.live`를 귀하의 실제 사이트 도메인으로 바꿉니다. 동일한 저장소에서 호스팅되는 각 사이트에는 별도의 CORS 구성 항목이 필요합니다.

CORS 구성에 대한 자세한 내용은 [CORS 구성 안내서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)를 참조하십시오.


로컬 개발 환경에서 CORS를 활성화하려면 [원본 간 리소스 공유(CORS) 이해](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) 문서를 참조하십시오.

<!--
#### 4. CDN Redirect Rules

Configure your Edge Delivery CDN to route submissions:

- Route requests from `/adobe/forms/af/submit/...` to your AEM Publish instance
- Implementation varies by CDN provider (Fastly, Akamai, Cloudflare)-->

#### &#x200B;4. 양식 구성

1. 범용 편집기에서 양식을 생성합니다.
2. 제출 작업을 AEM Forms 작업을 타기팅하도록 구성합니다.
3. 제출 엔드포인트 경로를 지정합니다.
4. 양식을 Edge Delivery 사이트에 게시합니다.

+++
<!--
+++ Form Embedding

Embed forms created in one location into different web pages or sites.

### Use Cases

- Reuse standard forms across multiple landing pages
- Include specialized forms in Document-Authored content
- Maintain single form across multiple EDS projects

### CORS Configuration

Configure Cross-Origin Resource Sharing on the form source:

1. **Add CORS Headers** to form source responses:
   - `Access-Control-Allow-Origin: https://your-host-domain.com`
   - `Access-Control-Allow-Methods: GET, OPTIONS`  
   - `Access-Control-Allow-Headers: Content-Type`

2. **Example Configuration**:

        # Configuration for site hosting the form
        headers:
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS

### Embedding Steps

1. **Create and Publish Form**
   - Build form using Document Authoring or Universal Editor
   - Configure submission method (FSS or AEM Publish)
   - Publish to standalone URL

2. **Configure CORS**
   - Set up CORS headers on form source site
   - Allow host page domain to fetch form

3. **Embed in Host Page**
   - Add form embedding block to host page
   - Point block to published form URL
   - Publish host page

![Embedded Form Architecture](/help/forms/assets/eds-embedded-form.png)

+++-->

+++ 일반 문제

| 문제 | 솔루션 |
|-------|----------|
| **양식 제출 실패** | 콘솔 오류를 확인하고, 엔드포인트 URL을 확인하고, 권한을 확인합니다. |
| **임베드된 양식이 표시되지 않음** | 양식 소스에서 CORS 헤더를 구성하고 양식 URL을 확인합니다. |
| **AEM에서 403/401 오류 발생** | Sling 레퍼러 필터를 업데이트하고 인증 설정을 확인합니다. |
| **데이터가 스프레드시트에 도달하지 않음** | `forms@adobe.com`에 편집 액세스 권한이 있는지 확인하고 스프레드시트 URL을 확인합니다. |
| **CORS 오류** | 양식 소스에 적절한 `Access-Control-Allow-Origin` 헤더를 추가합니다. |

+++

## 구성 예시

+++ 스프레드시트 제출이 가능한 문서 기반 양식

1. Google Docs/Sheets에서 양식 구조를 생성합니다.
2. Forms 제출 서비스 엔드포인트를 구성합니다.
3. 대상 스프레드시트에 `forms@adobe.com` 편집 액세스 권한을 부여합니다.
4. 문서를 Edge Delivery 사이트에 게시합니다.
5. 양식 제출 및 데이터 플로우를 테스트합니다.

+++

+++ AEM 워크플로를 통한 범용 편집기 양식

1. 범용 편집기에서 양식을 작성합니다.
2. “AEM 워크플로 호출”에 대한 제출 작업을 구성합니다.
3. AEM 게시에서 Dispatcher 및 레퍼러 필터를 설정합니다.
4. CDN 라우팅 규칙을 구성합니다.
5. 양식을 게시하고 워크플로 실행을 테스트합니다.

+++

## 모범 사례

- 간단한 데이터 캡처 시나리오에 대해 **Forms 제출 서비스를 사용**&#x200B;합니다.
- 복잡한 처리 또는 통합이 필요한 경우 **AEM 게시를 선택**&#x200B;합니다.
- 프로덕션 배포 전에 스테이징 환경에서 **철저히 테스트**&#x200B;합니다.
- AEM 로그 및 콘솔 오류를 사용하여 **제출을 모니터링**&#x200B;합니다.
- 실패한 제출에 대해 **적절한 오류 처리를 구현**&#x200B;합니다.
- 클라이언트 및 서버 수준 모두에서 **데이터의 유효성을 검사**&#x200B;합니다.
- 모든 양식 제출 및 데이터 전송에 **HTTPS를 사용**&#x200B;합니다.

## 관련 항목

- [EDS 양식을 사용한 문서 기반 작성](/help/edge/docs/forms/tutorial.md)
- [EDS 양식이 포함된 범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [AEM Forms 제출 서비스](/help/forms/forms-submission-service.md)
- [데이터 소스 구성](/help/forms/configure-data-sources.md)
- [AEM Forms Workflow 참조](/help/forms/aem-forms-workflow-step-reference.md)
