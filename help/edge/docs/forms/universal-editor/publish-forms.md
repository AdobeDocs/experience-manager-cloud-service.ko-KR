---
title: Edge Delivery Services을 사용하여 적응형 Forms 게시
description: 프로덕션 사용을 위해 Edge Delivery Services을 사용하여 적응형 Forms을 게시, 구성 및 액세스하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
keywords: [양식 게시, Edge Delivery Services, 양식 구성, CORS, 레퍼러 필터]
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: 746
ht-degree: 2%

---

# Edge Delivery Services을 사용하여 적응형 Forms 게시

적응형 양식을 게시하면 최종 사용자가 액세스하고 제출할 수 있도록 Edge Delivery Services에서 사용할 수 있습니다. 이 프로세스에는 양식 게시, 보안 설정 구성 및 라이브 양식 액세스의 세 가지 주요 단계가 포함됩니다.

**수행할 작업:**

- Edge Delivery Services에 양식 게시
- 양식 제출을 위한 보안 설정 구성
- 게시된 양식 액세스 및 확인
- 적절한 URL 라우팅 및 CORS 정책 설정

## 사전 요구 사항

- Edge Delivery Services 템플릿을 사용하여 만든 적응형 양식
- 양식 테스트 및 제작 준비 완료
- AEM Forms 작성자 권한
- Cloud Manager 액세스(프로덕션 구성용)
- 양식 블록 코드에 대한 개발자 액세스(제출 설정용)

## 게시 프로세스 개요

Edge Delivery Services에 양식을 게시하는 방법은 3단계로 구성됩니다.

- **1단계: 양식 게시** - 양식을 CDN에 게시하고 게시 상태를 확인합니다.
- **2단계: 보안 구성** - 보안 제출을 위한 CORS 정책 및 레퍼러 필터 설정
- **3단계: 액세스 및 유효성 검사** - 양식 기능을 테스트하고 전체 워크플로의 유효성을 검사합니다.

각 단계는 이전 단계를 기반으로 빌드하여 안전하고 기능적인 배포를 보장합니다.

### 1단계: 양식 게시

+++ 1단계: 게시 시작

1. **양식에 액세스**: 범용 편집기에서 적응형 양식을 엽니다.
2. **게시 시작**: 도구 모음에서 **게시** 아이콘을 클릭합니다

   ![게시 클릭](/help/forms/assets/publish-icon-eds-form.png)

+++


+++ 2단계: 검토 및 확인

1. **자산 게시를 검토**: 양식을 포함하여 게시 중인 모든 자산이 시스템에 표시됩니다

   ![클릭 시 게시](/help/forms/assets/on-click-publish.png)

2. **게시 확인**: 계속하려면 **게시**&#x200B;를 클릭하십시오.
3. **성공 확인**: 확인 메시지를 찾습니다

   ![게시 성공](/help/forms/assets/publish-success.png)

+++


+++ 3단계: 게시 상태 확인

**상태 확인**: **게시** 아이콘을 다시 클릭하여 현재 상태를 확인합니다

![게시 상태](/help/forms/assets/publish-status.png)

**유효성 검사 검사점:**

- 양식에 편집기의 &quot;게시됨&quot; 상태가 표시됨
- 게시 프로세스 중 오류 메시지 없음
- 양식이 게시된 자산 목록에 표시됨

+++


+++ 게시된 Forms 관리

**양식 게시를 취소하려면:**

1. 편집기에서 양식 열기
2. 오른쪽 상단의 점 3개 메뉴(⋯)를 클릭합니다
3. **게시 취소** 선택

![양식 게시 취소](/help/forms/assets/unpublish--form.png)

+++


### 2단계: 보안 설정 구성

+++ 보안 구성이 필요한 이유

보안 양식 제출을 활성화하려면 다음과 같은 보안 설정을 구성해야 합니다.

- Edge Delivery Services에서 AEM에 데이터를 제출하도록 허용
- AEM 인스턴스에 대한 무단 액세스 방지
- 양식 제출을 위해 CORS(원본 간 리소스 공유) 활성화
- 합법적인 Edge Delivery 도메인만 허용하도록 요청 필터링

>[!IMPORTANT]
>
>**프로덕션에 필요**: 이러한 구성은 양식 제출이 프로덕션 환경에서 작동하는 데 필수입니다.

+++



+++ 1단계: 양식 제출 URL 구성

**목적**: AEM 인스턴스에 직접 양식 제출

Edge Delivery Services 프로젝트의 **파일 위치**: `blocks/form/constant.js`

**구성 예:**

```javascript
// Production Environment
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';

// Local Development Environment  
export const submitBaseUrl = 'http://localhost:4503';

// Staging Environment
export const submitBaseUrl = 'https://publish-staging-p120-e12.adobeaemcloud.com';
```

**유효성 검사 검사점:**

- `constant.js` 파일이 올바른 AEM 게시 URL로 업데이트되었습니다.
- URL이 환경(프로덕션, 스테이징 또는 로컬)과 일치함
- URL에 후행 슬래시가 없음

+++



+++ 2단계: CORS 설정 구성

**목적**: Edge Delivery Services 도메인에서 양식 제출 요청 허용

**구현**: AEM Dispatcher 또는 Apache 구성에 CORS 구성 추가

```apache
# Local Development Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Services - Preview/Stage Environment  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true

# Edge Delivery Services - Production Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

**유효성 검사 검사점:**

- Dispatcher 구성에 적용되는 CORS 규칙
- 필요한 모든 도메인(localhost, hlx.page, hlx.live)이 포함됩니다
- 타겟 환경에 배포된 구성

**참조 설명서:**

- [CORS 구성 안내서](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [레퍼러 필터 설명서](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)

+++



+++ 3단계: 레퍼러 필터 구성

**목적**: 쓰기 작업을 승인된 Edge Delivery Services 도메인으로 제한합니다.

**구현 메서드**: AEM as a Cloud Service에서 Cloud Manager을 통해 구성

**구성 파일**: 프로젝트의 OSGi 구성에 추가

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

**구성 분류:**

- **`allow.empty`**: 레퍼러 헤더 없이 요청을 거부합니다.
- **`allow.hosts.regexp`**: Edge Delivery Services 도메인의 요청을 허용합니다.
- **`filter.methods`**: 다음 HTTP 메서드에 필터링을 적용합니다
- **`exclude.agents.regexp`**: 필터링에서 제외된 사용자 에이전트

**유효성 검사 검사점:**

- Cloud Manager을 통해 배포된 레퍼러 필터 구성
- AEM 게시 인스턴스에서 활성화된 구성
- Edge Delivery Services 도메인에서 양식 제출 작업 테스트
- 승인되지 않은 도메인의 양식 제출이 차단됨

**참조 설명서:**

- [Cloud Manager을 통해 레퍼러 필터 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)

+++


### 3단계: 게시된 양식에 액세스



+++ Edge Delivery Services용 URL 구조

**표준 URL 형식:**

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
```

**URL 구성 요소:**

- **`<branch>`**: Git 분기 이름(일반적으로 `main`)
- **`<repo>`**: 저장소 이름
- **`<owner>`**: GitHub 조직 또는 사용자 이름
- **`<form_name>`**: 양식 이름(소문자, 하이픈 넣기)

**환경별 URL:**

```
# Production Environment (.aem.live)
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form

# Preview Environment (.aem.page) 
https://main--universaleditor--wkndforms.aem.page/content/forms/af/wknd-form
```

+++



+++ 최종 유효성 검사 단계

**양식 액세스 가능성 확인:**

1. **양식 로드 테스트**: 양식 URL을 방문하여 제대로 로드되는지 확인하십시오
2. **양식 제출 테스트**: 데이터 처리를 확인하기 위해 양식을 작성하고 제출합니다.
3. **응답형 디자인 확인**: 다양한 장치 및 화면 크기에서 양식을 테스트합니다.
4. **보안 유효성 검사**: CORS 및 레퍼러 필터가 제대로 작동하는지 확인하십시오.

**예상 결과:**

- 오류 없이 양식 로드
- 모든 양식 필드가 올바르게 렌더링됨
- 양식 제출 프로세스 성공
- 구성된 대상(스프레드시트, 이메일 등)에 데이터가 표시됩니다.
- CORS 또는 보안 정책과 관련된 콘솔 오류 없음

+++


## 다음 단계


- [양식 제출 작업 구성](/help/edge/docs/forms/universal-editor/submit-action.md)
- [양식 스타일 지정 및 테마 설정](/help/edge/docs/forms/universal-editor/style-theme-forms.md)
- [reCAPTCHA 보호 추가](/help/edge/docs/forms/universal-editor/recaptcha-forms.md)
- [응답형 양식 레이아웃 만들기](/help/edge/docs/forms/universal-editor/responsive-layout.md)


