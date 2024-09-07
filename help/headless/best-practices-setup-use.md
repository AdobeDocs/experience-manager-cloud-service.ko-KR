---
title: AEM GraphQL 설정 및 사용에 대한 모범 사례와 콘텐츠 조각
description: AEM GraphQL 설정 및 사용에 대한 권장 모범 사례와 콘텐츠 조각을 학습합니다.
exl-id: 4d6a5aaa-c8be-4858-ad07-085dc4fb77e7
feature: Headless
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: ht
source-wordcount: '702'
ht-degree: 100%

---

# AEM GraphQL 설정 및 사용에 대한 모범 사례와 콘텐츠 조각{#best-practices-setup-use-aem-graphql-content-fragments}

이 지침에는 GraphQL 및 Content Fragments와 함께 AEM을 설정, 구성 및 사용하기 위한 권장 모범 사례가 요약되어 있습니다.

## 시작 {#getting-started}

최신 정보를 위한 참고 자료:

* [Headless 소개](/help/headless/what-is-headless.md)
* AEM [아키텍처](/help/headless/deployment/architecture.md) 내 다양한 환경에 대한 개요

## 설정 {#setup}

콘텐츠 조각 및 앱과 함께 사용하기 위해 AEM GraphQL을 안전하게 설정하려면 다양한 구성 요소를 구성해야 합니다.

### GraphQL 엔드포인트 생성(보안 포함) {#graphql-endpoint-creation}

엔드포인트는 AEM용 GraphQL에 액세스하는 데 사용되는 경로입니다. 안전하게 액세스할 수 있도록 이러한 엔드포인트를 생성하고 게시해야 합니다.

#### 세부 사항 {#details-graphql-endpoint-creation}

[AEM에서 GraphQL 엔드포인트 관리](/help/headless/graphql-api/graphql-endpoint.md)

#### 환경 {#environments-graphql-endpoint-creation}

엔드포인트는 다음에서 구성되어야 합니다.

* 작성자
* 미리보기
* 게시

대상:

* 개발
* 테스트
* 프로덕션

### AEM Dispatcher 캐싱 {#dispatcher-caching}

>[!NOTE]
>Dispatcher에서 캐싱이 활성화된 경우 [CORS 설정](#cors-setup)이 필요하지 않으므로 무시해도 됩니다.

지속 쿼리 캐싱은 기본적으로 Dispatcher에서 활성화되어 있지 않습니다. 원본이 여러 개인 CORS(원본 간 리소스 공유)를 사용하는 고객은 Dispatcher 구성을 검토하고 업데이트해야 하므로 기본값으로 활성화할 수는 없습니다.

#### 세부 사항 {#details-dispatcher-caching}

[GraphQL 지속 쿼리 - Dispatcher에서 캐싱 활성화](/help/headless/deployment/dispatcher-caching.md)

#### 환경 {#environments-dispatcher-caching}

Dispatcher는 일반적으로 다음에 대해 구성됩니다.

* 게시: 프로덕션

### CORS 설정 {#cors-setup}

>[!NOTE]
>[AEM Dispatcher](#dispatcher-caching)에서 캐싱이 활성화된 경우 CORS 설정이 필요하지 않으므로 해당 섹션은 무시해도 됩니다.

GraphQL 엔드포인트에 액세스하려면 CORS 정책을 구성하고 Cloud Manager를 통해 AEM에 배포된 AEM 프로젝트에 추가해야 합니다. 원하는 엔드포인트에 대한 적절한 OSGi CORS 구성 파일 추가를 통해 수행됩니다.

#### 세부 사항 {#details-cors-setup}

[CORS(원본 간 리소스 공유) 구성](/help/headless/deployment/cross-origin-resource-sharing.md)

#### 환경 {#environments-cors-setup}

CORS는 일반적으로 다음에 대해 구성됩니다.

* 게시: 프로덕션

### 인증 {#authentication}

콘텐츠 조각 게재를 위한 AEM(Adobe Experience Manager as a Cloud Service) GraphQL API의 주요 사용 사례는 서드파티 애플리케이션 또는 서비스의 원격 쿼리를 수락하는 것입니다. Headless 콘텐츠 게재를 보호하기 위해 이러한 원격 쿼리에는 인증된 API 액세스가 필요할 수 있습니다.

#### 세부 사항 {#details-authentication}

[콘텐츠 조각의 원격 AEM GraphQL 쿼리 인증](/help/headless/security/authentication.md)

#### 환경 {#environments-authentication}

인증은 일반적으로 다음에 대해 구성됩니다.

* 미리보기
* 게시

대상:

* 개발
* 테스트
* 프로덕션

### 권한 {#permissions}

Headless 구현으로 여러 보안 및 권한 영역을 다뤄야 합니다. AEM 환경 **Author** 또는 **Publish**&#x200B;에 따라 권한 및 가상 사용자를 광범위하게 고려할 수 있습니다. 각 환경에는 다양한 가상 사용자가 포함되어 있으며 다양한 요구 사항을 가지고 있습니다.

#### 세부 사항 {#details-permissions}

[Headless 콘텐츠에 대한 권한 고려 사항](/help/headless/security/permissions.md)

#### 환경 {#environments-permissions}

권한은 일반적으로 다음에 대해 구성됩니다.

* 작성자
* 미리보기
* 게시

대상:

* 개발
* 테스트
* 프로덕션

### 콘텐츠 전송 네트워크(CDN) 사용 {#cdn}

GraphQL 쿼리와 해당 JSON 응답은 CDN을 사용할 때 `GET` 요청으로 지정되면 캐시될 수 있습니다. 반면, 캐시되지 않은 요청은 (리소스) 비용이 매우 높고 처리 속도가 느릴 수 있으며 원본 리소스에 더 해로운 영향을 미칠 가능성이 있습니다.

#### 세부 사항 {#details-cdn}

[AEM as a Cloud Service의 CDN](/help/implementing/dispatcher/cdn.md)

#### 환경 {#environments-cdn}

CDN은 일반적으로 다음에 대해 구성됩니다.

* 게시: 프로덕션

### 콘텐츠 조각 구성 및 만들기 {#cconfigure-create-content-fragments}

AEM GraphQL은 콘텐츠 조각에서 정보를 검색하는 데 사용됩니다. 콘텐츠를 만들기 전에 콘텐츠를 구성한 다음 구조와 위치를 정의해야 합니다.

#### 세부 사항 {#details-content-fragments}

* [구성 만들기](/help/headless/setup/create-configuration.md)
* [콘텐츠 조각 모델 만들기](/help/headless/setup/create-content-model.md)
* [Assets 폴더 만들기](/help/headless/setup/create-assets-folder.md)
* [콘텐츠 조각 만들기 및 편집](/help/headless/setup/create-content-fragment.md)

#### 환경 {#eenvironments-content-fragments}

콘텐츠 조각은 다음에서 정의, 작성, 테스트, 게시 및 액세스됩니다.

* 작성자
* 미리보기
* 게시

대상:

* 개발
* 테스트
* 프로덕션

## AEM GraphQL 사용 {#use-aem-graphql}

### GraphQL 쿼리 최적화 {#optimize-graphql-queries}

이러한 지침은 GraphQL 쿼리의 성능 문제를 방지하는 데 도움이 되도록 제공됩니다.

#### 세부 사항 {#details-optimize-graphql-queries}

[GraphQL 쿼리 최적화](/help/headless/graphql-api/graphql-optimization.md)

>[!NOTE]
>
>최적화 지침은 이미 [설정](#setup)에서 다룬 캐시 구성을 다룹니다.

### Access 앱의 GraphQL {#access-graphql-from-your-apps}

AEM Headless CMS를 사용하면 개발자가 이미 익숙한 언어, 프레임워크 및 도구를 사용하여 탁월한 경험을 자유롭게 구축 및 전달할 수 있습니다.

#### 세부 사항 {#details-your-apps}

* [개발용 AEM SDK 설치 및 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html?lang=ko-KR)
* [AEM Headless 개발자 리소스](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=ko-KR)
* [React](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/react-app.html?lang=ko-KR), [Next.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/next-js.html?lang=ko-KR), [Node.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/server-to-server-app.html?lang=ko-KR)를 비롯한 예시

#### 환경 {#environments-your-apps}

앱은 일반적으로 다음에서 개발, 테스트 및 사용됩니다.

* 미리보기
* 게시

대상:

* 개발
* 테스트
* 프로덕션

### 추가 리소스

AEM GraphQL 및 콘텐츠 조각에 대한 자세한 내용은 다음을 참조하십시오.

* [콘텐츠 조각과 함께 사용하기 위한 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)
* [GraphiQL IDE 사용](/help/headless/graphql-api/graphiql-ide.md)
* [AEM Headless 개발자 리소스](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=ko-KR)
