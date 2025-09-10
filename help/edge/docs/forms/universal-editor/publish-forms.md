---
title: Edge Delivery Services로 적응형 양식 게시
description: Edge Delivery Services를 사용하여 프로덕션 환경에서 Adaptive Forms를 게시, 구성 및 액세스하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
keywords: 양식 게시, Edge Delivery Services, 양식 구성, CORS, 레퍼러 필터
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 100%

---

# Edge Delivery Services로 적응형 양식 게시

적응형 양식을 게시하면 최종 사용자가 액세스하고 제출할 수 있도록 Edge Delivery Services에서 사용할 수 있게 됩니다. 이 프로세스에는 양식 게시, 보안 설정 구성, 라이브 양식 액세스의 세 가지 주요 단계가 포함됩니다.

**학습 내용:**

- 양식을 Edge Delivery Services에 게시합니다.
- 양식 제출에 대한 보안 설정을 구성합니다.
- 게시된 양식에 액세스하고 확인합니다.
- 적절한 URL 라우팅 및 CORS 정책을 설정합니다.

## 사전 요구 사항

- Edge Delivery Services 템플릿을 사용하여 만든 적응형 양식
- 테스트를 거쳐 프로덕션 용도로 준비된 양식
- AEM Forms 작성자 권한
- Cloud Manager 액세스(프로덕션 구성용)
- 양식 블록 코드에 대한 개발자 액세스(제출 설정용)

## 게시 프로세스 개요

Edge Delivery Services에 양식을 게시하는 과정은 3단계로 진행됩니다.

- **1단계: 양식 게시** - 양식을 CDN에 게시하고 게시 상태를 확인합니다.
- **2단계: 보안 구성** - 보안 제출을 위해 CORS 정책 및 레퍼러 필터를 설정합니다.
- **3단계: 액세스 및 유효성 검사** - 양식 기능을 테스트하고 전체 워크플로의 유효성을 검사합니다.

각 단계는 이전 단계를 기반으로 구축되어 안전하고 기능적인 배포를 보장합니다.

### 1단계: 양식 게시

+++ 1단계: 게시 시작

1. **양식에 액세스**: 범용 편집기에서 적응형 양식을 엽니다.
2. **게시 시작**: 도구 모음에서 **게시** 아이콘을 클릭합니다.

   ![게시 클릭](/help/edge/docs/forms/universal-editor/assets/publish-form-ue.png)

+++


+++ 2단계: 검토 및 확인

1. **게시 자산 검토**: 시스템에 양식을 비롯하여 게시되는 모든 자산이 표시됩니다.

   ![클릭 시 게시](/help/edge/docs/forms/universal-editor/assets/publish-form-ue-review.png)

2. **게시 확인**: 계속 진행하려면 **게시**&#x200B;를 클릭합니다.
3. **성공 확인**: 확인 메시지를 찾습니다.

   ![게시 성공](/help/edge/docs/forms/universal-editor/assets/publish-form-ue-success.png)

+++


+++ 3단계: 게시 상태 확인

**상태 확인**: **게시** 아이콘을 다시 클릭하여 현재 상태를 확인합니다.

![게시 상태](/help/edge/docs/forms/universal-editor/assets/publish-form-ue-validate.png)

**유효성 검사 체크포인트:**

- 편집기에서 양식에 “게시됨” 상태가 표시됩니다.
- 게시 프로세스 중에 오류 메시지가 표시되지 않습니다.
- 게시된 자산 목록에 양식이 나타납니다.

+++


+++ 게시된 양식 관리

**양식 게시 취소:**

1. 편집기에서 양식을 엽니다.
2. 오른쪽 상단에 있는 세 개의 점 메뉴(⋯)를 클릭합니다.
3. **게시 취소**&#x200B;를 선택합니다.

![양식 게시 취소](/help/edge/docs/forms/universal-editor/assets/unpublish-ue.png)

+++


### 2단계: 보안 설정 구성

+++ 보안 구성이 필요한 이유

안전한 양식 제출을 활성화하려면 다음을 수행하는 보안 설정을 구성해야 합니다.

- Edge Delivery Services가 AEM에 데이터를 제출하도록 허용
- AEM 인스턴스에 대한 미승인 액세스 방지
- 양식 제출에 대해 CORS(원본 간 리소스 공유) 활성화
- 합법적인 Edge Delivery 도메인만 허용하도록 요청 필터링

>[!IMPORTANT]
>
>**프로덕션에 필요**: 이 구성은 프로덕션 환경에서 양식 제출이 작동하는 데 필수적입니다.

+++



+++ 1단계: 양식 제출 URL 구성

**용도**: AEM 인스턴스에 양식을 직접 제출합니다.

**파일 위치**: Edge Delivery Services 프로젝트의 `blocks/form/constant.js`

**구성 예시:**

```javascript
// Production Environment
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';

// Local Development Environment  
export const submitBaseUrl = 'http://localhost:4503';

// Staging Environment
export const submitBaseUrl = 'https://publish-staging-p120-e12.adobeaemcloud.com';
```

**유효성 검사 체크포인트:**

- 올바른 AEM 게시 URL로 `constant.js` 파일이 업데이트되었습니다.
- URL이 사용자 환경(프로덕션, 스테이징 또는 로컬)과 일치합니다.
- URL 뒤에 슬래시가 없습니다.

+++



+++ 2단계: CORS 설정 구성

**용도**: Edge Delivery Services 도메인의 양식 제출 요청을 허용합니다.

**구현**: AEM 디스패처 또는 Apache 구성에 CORS 구성을 추가합니다.

```apache
# Local Development Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Services - Preview/Stage Environment  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true

# Edge Delivery Services - Production Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

**유효성 검사 체크포인트:**

- 디스패처 구성에 CORS 규칙이 적용됩니다.
- 필요한 모든 도메인(localhost, hlx.page, hlx.live)이 포함됩니다.
- 대상 환경에 구성이 배포됩니다.

**참조 설명서:**

- [CORS 구성 안내서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [레퍼러 필터 설명서](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)

+++



+++ 3단계: 레퍼러 필터 구성

**용도**: 쓰기 작업을 승인된 Edge Delivery Services 도메인으로 제한합니다.

**구현 방법**: AEM as a Cloud Service에서 Cloud Manager를 통해 구성합니다.

**구성 파일**: 프로젝트의 OSGi 구성에 추가합니다.

```json
{
  "allow.empty": false,
  "allow.hosts": [],
  "allow.hosts.regexp": [
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

**구성 세부 사항:**

- **`allow.empty`**: 레퍼러 헤더가 없는 요청을 거부합니다.
- **`allow.hosts.regexp`**: Edge Delivery Services 도메인의 요청을 허용합니다.
- **`filter.methods`**: 이러한 HTTP 메서드에 필터링을 적용합니다.
- **`exclude.agents.regexp`**: 필터링에서 제외된 사용자 에이전트

**유효성 검사 체크포인트:**

- Cloud Manager를 통해 배포된 레퍼러 필터 구성
- AEM 게시 인스턴스에서 활성화된 구성
- Edge Delivery Services 도메인에서 양식 제출이 작동하는지 테스트합니다.
- 승인되지 않은 도메인이 양식을 제출하지 못하도록 차단됩니다.

**참조 설명서:**

- [Cloud Manager를 통해 레퍼러 필터 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)

+++


### 3단계: 게시된 양식에 액세스



+++ Edge Delivery Services용 URL 구조

**표준 URL 형식:**

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
```

**URL 구성 요소:**

- **`<branch>`**: Git 분기 이름 (일반적으로 `main`)
- **`<repo>`**: 저장소 이름
- **`<owner>`**: GitHub 조직 또는 사용자 이름
- **`<form_name>`**: 양식 이름 (소문자, 하이픈 구분)

**환경별 URL:**

```
# Production Environment (.aem.live)
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form

# Preview Environment (.aem.page) 
https://main--universaleditor--wkndforms.aem.page/content/forms/af/wknd-form
```

+++



+++ 최종 유효성 검사 단계

**양식 접근성 확인:**

1. **양식 로드 테스트**: 양식 URL을 방문하여 제대로 로드되는지 확인합니다.
2. **양식 제출 테스트**: 양식을 작성하고 제출하여 데이터 처리를 확인합니다.
3. **반응형 디자인 확인**: 다양한 디바이스 및 화면 크기에서 양식을 테스트합니다.
4. **보안 유효성 검사**: CORS 및 레퍼러 필터가 올바르게 작동하는지 확인합니다.

**예상 결과:**

- 오류 없이 양식이 로드됩니다.
- 모든 양식 필드가 올바르게 렌더링됩니다.
- 양식 제출 프로세스가 성공적으로 처리됩니다.
- 데이터가 구성된 대상(스프레드시트, 이메일 등)에 나타납니다.
- CORS 또는 보안 정책과 관련된 콘솔 오류가 없습니다.

+++


## 다음 단계


- [양식 제출 작업 구성](/help/edge/docs/forms/universal-editor/submit-action.md)
- [양식 스타일 지정 및 테마 설정](/help/edge/docs/forms/universal-editor/style-theme-forms.md)
- [반응형 양식 레이아웃 만들기](/help/edge/docs/forms/universal-editor/responsive-layout.md)
- [reCAPTCHA 보호 추가](/help/edge/docs/forms/universal-editor/recaptcha-forms.md)



