---
title: Edge Delivery Services 양식 제출에서 403 금지된 오류 해결
description: Edge Delivery Services에서 AEM Publish로 양식을 제출할 때 403 금지된 오류를 진단하고 해결하는 방법을 알아봅니다. 이 안내서에서는 CORS, Dispatcher 규칙 및 레퍼러 필터 문제를 포함한 일반적인 원인을 다룹니다.
feature: Edge Delivery Services
role: Admin, Developer
exl-id: f397e059-f1b3-4afa-bd38-8f5fc591bb22
source-git-commit: d457bf9af377176222c2b96816fbbc4265e6b167
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 3%

---

# Edge Delivery Services 양식 제출에서 403 금지된 오류 해결 {#troubleshooting-403-forbidden-edge-delivery}

Edge Delivery Services에서 AEM Publish로 양식을 제출할 때 **403 사용할 수 없음** 오류가 발생할 수 있습니다. 이 오류는 일반적으로 보안 구성으로 인해 서버가 요청 처리를 거부하고 있음을 나타냅니다. 이 문서는 이 문제의 가장 일반적인 원인을 식별하고 해결하는 데 도움이 됩니다.

## 문제 설명

Edge Delivery Services에서 AEM Publish로 양식을 제출할 때 **403 사용할 수 없음** 오류가 발생합니다. 오류는 다음과 같이 나타납니다.

- HTTP 상태 코드: 403
- 오류 메시지: &quot;금지됨&quot; 또는 &quot;액세스 거부됨&quot;
- AEM 제출 서블릿에 도달하지 않고 양식 제출이 실패합니다

이 문제는 일반적으로 Edge 도메인(`.aem.live`, `.aem.page`, `.hlx.page`, `.hlx.live`)에 호스팅된 양식이 AEM 게시 인스턴스에 데이터를 제출하려는 Edge Delivery Services 통합에서 발생합니다.

>[!IMPORTANT]
>
>신뢰 설정을 사용하면 동일한 저장소를 사용하여 여러 사이트를 호스팅할 수 있습니다. 양식 제출이 제대로 작동하려면 각 사이트 도메인을 허용 목록에 개별적으로 추가해야 합니다.
>
>**예:**
>
>- 저장소: `https://github.com/adobe/abc`
>- 사이트 1: `main--abc--adobe.aem.live`
>- 사이트 2: `main--abc1--adobe.aem.live`
>
>두 도메인 모두 양식 제출을 위해 두 사이트에서 별도의 허용 목록 항목이 필요합니다.

## 일반적인 원인 및 해결 방법

Edge Delivery Services 양식 제출에 403 금지된 오류가 발생하면 여러 가지 원인이 있을 수 있습니다. 다음 문제 해결 단계를 순서대로 수행합니다.

### &#x200B;1. CORS(원본 간 리소스 공유) 문제

**증상:**

- 브라우저 콘솔에 CORS 관련 오류 메시지가 표시됨
- 네트워크 탭에 서버에 도달하기 전에 차단되는 요청이 표시됩니다.
- &quot;원본 간 요청 차단됨&quot;을 언급한 오류 메시지

**진단:**

1. 브라우저 개발자 도구 열기(F12)
2. Console 탭에서 CORS 오류 메시지를 확인합니다.
3. 다음과 같은 메시지 찾기: `Access to fetch at 'https://publish-xxx.adobeaemcloud.com' from origin 'https://main--repo--owner.aem.live' has been blocked by CORS policy`

**솔루션:**
특정 Edge Delivery 사이트 도메인의 요청을 허용하도록 AEM에서 CORS 설정을 구성합니다.

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Sites - Add each site domain individually
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true

# Legacy Franklin domains (if still in use)
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

>[!NOTE]
>
>`main--abc--adobe.aem.live` 및 `main--abc1--adobe.aem.live`을(를) 실제 사이트 도메인으로 바꾸십시오. 동일한 저장소에서 호스팅되는 각 사이트에는 별도의 CORS 구성 항목이 필요합니다.

자세한 CORS 구성은 [CORS 구성 안내서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)를 참조하십시오.

### &#x200B;2. Dispatcher 규칙

**증상:**

- 브라우저 콘솔에서 CORS 메시지 없이 403 오류 발생
- 요청이 서버에 도달하지만 Dispatcher에 의해 차단됨
- AEM 애플리케이션 계층에 도달하기 전에 오류 발생

**진단:**

1. 요청 URL이 Dispatcher 필터 규칙과 일치하는지 확인
2. POST 요청을 차단할 수 있는 `/filter` 규칙에 대한 Dispatcher 구성 검토
3. 양식 제출 엔드포인트가 Dispatcher 구성에서 허용되는지 확인

**솔루션:**
양식 제출 요청을 허용하도록 Dispatcher 구성을 업데이트합니다.

1. 양식 제출 종단점에 대한 POST 요청이 허용되는지 확인
2. Edge Delivery 도메인에 대한 적절한 필터 규칙 추가
3. 제출 서블릿 경로가 차단되지 않았는지 확인

Dispatcher 필터 구성 예:

```apache
/filter {
  # Allow POST requests to form submission servlet
  /0100 { /type "allow" /method "POST" /url "/content/forms/af/*" }
  /0101 { /type "allow" /method "POST" /url "/adobe/forms/af/submit/*" }
  /0102 { /type "allow" /method "POST" /url "/content/forms/portal/submit/adaptiveform" }
}
```

### &#x200B;3. 레퍼러 필터 문제

**증상:**

- 브라우저 콘솔에 CORS 문제가 없는 403 오류
- 요청이 AEM에 도달하지만 Sling 레퍼러 필터에 의해 거부됨
- AEM 애플리케이션 계층에서 오류 발생

**진단:**
레퍼러 필터 거부 메시지에 대한 AEM 오류 로그 확인:

1. [Cloud Manager을 통해 AEM Cloud Service 로그에 액세스](/help/implementing/cloud-manager/manage-logs.md)
2. `aemerror.log`에서 다음을 포함하는 항목을 찾습니다.
   - &quot;레퍼러 필터 거부됨&quot;
   - &quot;org.apache.sling.security.impl.ReferrerFilter&quot;
   - 레퍼러 유효성 검사 실패를 나타내는 메시지

**로그 항목 예:**

```
[ERROR] org.apache.sling.security.impl.ReferrerFilter Referrer filter rejected request with referrer 'https://main--abc--adobe.aem.live' for POST /content/forms/af/submit
```

**솔루션:**
특정 Edge Delivery 사이트 도메인을 허용하도록 레퍼러 필터를 구성합니다.

1. OSGi 구성 파일 `org.apache.sling.security.impl.ReferrerFilter.cfg.json`을(를) 만들거나 업데이트합니다.

2. 특정 사이트 도메인에 다음 구성을 추가합니다.

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

3. Cloud Manager을 통해 구성 배포

>[!IMPORTANT]
>
>**오류 설정의 경우:** 각 사이트 도메인을 `allow.hosts` 배열에 개별적으로 추가해야 합니다. 정규 표현식 패턴만 사용해도 모든 시나리오에 충분하지 않을 수 있습니다. 포괄적인 내용을 제공하기 위해 특정 도메인과 정규 표현식 패턴을 모두 포함합니다.

>[!WARNING]
>
>AEM의 레퍼러 필터는 OSGi 구성 팩토리가 아니므로 한 번에 하나의 구성만 AEM 서비스에서 활성화됩니다. 가능한 경우 사용자 정의 레퍼러 필터 구성을 추가하지 마십시오. AEM의 기본 구성을 덮어쓰고 제품 기능을 손상시킬 수 있습니다.

## 진단 단계

다음 단계에 따라 403 오류의 특정 원인을 식별하십시오.

### 1단계: 브라우저 콘솔 확인

1. 브라우저 개발자 도구 열기(F12)
2. Console 탭으로 이동합니다.
3. 양식 제출 시도
4. CORS 관련 오류 메시지 찾기

**CORS 오류가 있는 경우:** 위의 CORS 솔루션을 따르십시오.
**CORS 오류가 없는 경우:** 2단계로 진행합니다.

### 2단계: 네트워크 확인 탭

1. 브라우저 개발자 도구 열기(F12)
2. 네트워크 탭으로 이동합니다.
3. 양식 제출 시도
4. 실패한 요청 세부 정보 확인
5. 응답 헤더 및 상태 확인

**요청이 서버에 도달하지 않는 경우:** Dispatcher 문제일 수 있습니다.
**요청이 서버에 도달하지만 실패한 경우:** 레퍼러 필터 문제일 수 있습니다.

### 3단계: AEM 로그 확인

1. Cloud Manager 액세스
2. 환경 → 로그→ 이동합니다.
3. `aemerror.log` 다운로드 또는 보기
4. 양식 제출 시 항목 검색
5. 레퍼러 필터 또는 보안 관련 메시지 찾기

## 예방 및 우수 사례

### &#x200B;1. 설정 중 적절한 구성

- 초기 Edge Delivery Services 설정 중 CORS, Dispatcher 및 레퍼러 필터 설정 구성
- **새 사이트마다:** 모든 허용 목록(CORS, 레퍼러 필터)에 특정 도메인을 추가합니다.
- 시작하기 전에 개발 환경에서 양식 제출 테스트

### &#x200B;2. 환경별 구성

- 개발, 스테이징 및 프로덕션 환경에 다양한 구성 사용
- 로컬 개발 테스트를 위한 localhost 도메인 포함
- 허용 목록에 추가하다 저장소에 대한 액세스 권한이 필요한 **모든 사이트 도메인을 문서화**

### &#x200B;3. 모니터링 및 로깅

- 레퍼러 필터 거부에 대한 로그 모니터링 설정
- 양식 제출 코드에서 적절한 오류 처리 구현
- 테스트하는 동안 브라우저 개발자 도구 사용

### &#x200B;4. 설명서 및 팀 지식

- 동일한 저장소를 사용하는 모든 사이트 도메인의 **레지스트리 유지 관리**
- 개발 팀에 문제 해결 단계 교육
- Edge Delivery Services 양식 설정에 대한 체크리스트 유지
- 기존 저장소에서 새 사이트를 만들 때마다 **허용 목록 업데이트**

## Repolless 설정을 위한 사이트 도메인 관리

Helix-5 및 Repolless 아키텍처를 사용하여 다음 지침을 따르십시오.

### 새 사이트 생성 시

1. **사이트 도메인 식별**(예: `main--newsite--adobe.aem.live`)
2. 새 도메인을 포함하도록 **CORS 구성 업데이트**
3. **에 새 도메인을 포함하도록**&#x200B;레퍼러 필터 업데이트`allow.hosts`
4. 새 사이트에서 **양식 제출 테스트**
5. 사이트 레지스트리에서 **새 도메인을 문서화**

### 도메인 이름 지정 패턴

- 표준 패턴: `{branch}--{site}--{owner}.aem.live`
- 각 사이트는 동일한 저장소를 공유하는 경우에도 고유한 도메인을 가져옵니다
- `.aem.live` 및 `.aem.page` 도메인이 모두 사용될 수 있습니다.

### 구성 관리

- 보안을 강화하려면 `allow.hosts`의 특정 도메인 항목을 사용하십시오.
- 더 넓은 범위를 위해 정규 표현식 패턴으로 보충
- 사이트가 추가되거나 제거될 때 정기적으로 허용 목록을 감사 및 업데이트

## 추가 리소스

- [AEM Headless를 사용한 레퍼러 필터 구성](/help/headless/deployment/referrer-filter.md)
- [CORS 구성 안내서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [원본 간 리소스 공유 이해](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)
- [Edge Delivery Services Forms 설명서](/help/edge/docs/forms/universal-editor/publish-forms.md)

## 관련 항목

- [제출 액션 구성](/help/forms/configuring-submit-actions.md)
- [Forms 제출 서비스](/help/forms/forms-submission-service.md)
- [Edge Delivery Services 개요](/help/edge/overview.md)


**추가 도움말이 필요하십니까?** 이 문제 해결 단계를 수행한 후에도 문제가 계속 발생하면 Adobe 고객 지원 센터에 다음 방법으로 문의하십시오.

- 특정 오류 메시지
- AEM Cloud Service 환경 세부 정보
- 양식 제출 액세스 권한이 필요한 **모든 Edge Delivery Services 사이트 도메인**
- 오류 발생 시 관련 로그 항목

**추가 도움말이 필요하십니까?** 이 문제 해결 단계를 수행한 후에도 문제가 계속 발생하면 Adobe 고객 지원 센터에 다음 방법으로 문의하십시오.

- 특정 오류 메시지
- AEM Cloud Service 환경 세부 정보
- Edge Delivery Services 도메인 정보
- 오류 발생 시 관련 로그 항목
