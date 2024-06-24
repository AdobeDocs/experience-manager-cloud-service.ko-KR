---
title: 컨텐츠 조각과 함께 AEM GraphQL 설정 및 사용 모범 사례
description: 콘텐츠 조각과 함께 AEM GraphQL의 설정 및 사용에 대한 권장 모범 사례에 대해 알아봅니다.
exl-id: 4d6a5aaa-c8be-4858-ad07-085dc4fb77e7
feature: Headless
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 29%

---

# 컨텐츠 조각과 함께 AEM GraphQL 설정 및 사용 모범 사례{#best-practices-setup-use-aem-graphql-content-fragments}

이 지침에서는 GraphQL 및 컨텐츠 조각의 AEM 설정, 구성 및 사용에 대한 권장 모범 사례를 요약합니다.

## 시작 {#getting-started}

다음 작업을 수행하여 속도를 높이십시오.

* [Headless 소개](/help/headless/what-is-headless.md)
* AEM의 다양한 환경에 대한 개요 [아키텍처](/help/headless/deployment/architecture.md)

## 설정 {#setup}

콘텐츠 조각 및 앱에서 사용할 AEM GraphQL을 안전하게 설정하려면 다양한 구성 요소를 구성해야 합니다.

### GraphQL 끝점 만들기(보안 포함) {#graphql-endpoint-creation}

엔드포인트는 AEM용 GraphQL에 액세스하는 데 사용되는 경로입니다. 이러한 엔드포인트는 안전하게 액세스할 수 있도록 만들고 게시해야 합니다.

#### 세부 사항 {#details-graphql-endpoint-creation}

[AEM에서 GraphQL 엔드포인트 관리](/help/headless/graphql-api/graphql-endpoint.md)

#### 환경 {#environments-graphql-endpoint-creation}

끝점은 다음 위치에 구성해야 합니다.

* 작성자
* 미리보기
* 게시

대상:

* 개발
* 테스트
* 프로덕션

### AEM Dispatcher 캐싱 {#dispatcher-caching}

>[!NOTE]
>Dispatcher에서 캐싱이 활성화되면 [CORS 설정](#cors-setup) 가 필요하지 않으므로 무시할 수 있습니다.

지속 쿼리 캐싱은 기본적으로 Dispatcher에서 활성화되어 있지 않습니다. 원본이 여러 개인 CORS(원본 간 리소스 공유)를 사용하는 고객은 Dispatcher 구성을 검토하고 업데이트해야 하므로 기본값으로 활성화할 수는 없습니다.

#### 세부 사항 {#details-dispatcher-caching}

[GraphQL 지속 쿼리 - Dispatcher에서 캐싱 활성화](/help/headless/deployment/dispatcher-caching.md)

#### 환경 {#environments-dispatcher-caching}

Dispatcher는 일반적으로 다음과 같이 구성됩니다.

* Publish: 프로덕션

### CORS 설정 {#cors-setup}

>[!NOTE]
>에서 캐시하는 경우 [AEM 디스패처](#dispatcher-caching) 가 활성화되면 CORS 설정이 필요하지 않으므로 이 섹션을 무시할 수 있습니다.

GraphQL 끝점에 액세스하려면 CORS 정책을 구성하고 Cloud Manager를 통해 AEM에 배포된 AEM 프로젝트에 추가해야 합니다. 이 작업은 원하는 끝점에 대한 적절한 OSGi CORS 구성 파일을 추가하여 수행됩니다.

#### 세부 사항 {#details-cors-setup}

[CORS(원본 간 리소스 공유) 구성](/help/headless/deployment/cross-origin-resource-sharing.md)

#### 환경 {#environments-cors-setup}

CORS는 일반적으로 다음과 같이 구성됩니다.

* Publish: 프로덕션

### 인증 {#authentication}

컨텐츠 조각 전달을 위한 Adobe Experience Manager as a Cloud Service(AEM) GraphQL API의 주요 사용 사례는 서드파티 애플리케이션 또는 서비스의 원격 쿼리를 수락하는 것입니다. Headless 콘텐츠 게재를 보호하기 위해 이러한 원격 쿼리에는 인증된 API 액세스가 필요할 수 있습니다.

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

### CDN(Content Delivery Network) 사용 {#cdn}

GraphQL 쿼리 및 해당 JSON 응답은 타깃팅한 경우 캐시될 수 있습니다. `GET` cdn 사용 시 요청. 반대로 캐시되지 않은 요청은 매우 (리소스) 비용이 많이 들고 처리 속도가 느릴 수 있으며, 이로 인해 원본 리소스에 추가 해로운 영향을 미칠 수 있습니다.

#### 세부 사항 {#details-cdn}

[AEM as a Cloud Service의 CDN](/help/implementing/dispatcher/cdn.md)

#### 환경 {#environments-cdn}

CDN은 일반적으로 다음에 대해 구성됩니다.

* Publish: 프로덕션

### 콘텐츠 조각 구성 및 만들기 {#cconfigure-create-content-fragments}

AEM GraphQL은 콘텐츠 조각에서 정보를 검색하는 데 사용됩니다. 콘텐츠를 만들기 전에 이를 구성한 다음 구조와 위치를 정의해야 합니다.

#### 세부 사항 {#details-content-fragments}

* [구성 만들기](/help/headless/setup/create-configuration.md)
* [콘텐츠 조각 모델 만들기](/help/headless/setup/create-content-model.md)
* [에셋 폴더 만들기](/help/headless/setup/create-assets-folder.md)
* [콘텐츠 조각 만들기 및 편집](/help/headless/setup/create-content-fragment.md)

#### 환경 {#eenvironments-content-fragments}

콘텐츠 조각 정의됨, 작성됨, 테스트됨, 게시됨 및 액세스됨

* 작성자
* 미리보기
* 게시

대상:

* 개발
* 테스트
* 프로덕션

## AEM GraphQL 사용 {#use-aem-graphql}

### GraphQL 쿼리 최적화 {#optimize-graphql-queries}

이 지침은 GraphQL 쿼리와 관련된 성능 문제를 방지하기 위해 제공됩니다.

#### 세부 사항 {#details-optimize-graphql-queries}

[GraphQL 쿼리 최적화](/help/headless/graphql-api/graphql-optimization.md)

>[!NOTE]
>
>최적화 지침은에서 이미 다룬 캐시 구성을 다룹니다 [설정](#setup).

### 앱에서 GraphQL에 액세스 {#access-graphql-from-your-apps}

AEM Headless CMS는 개발자가 이미 익숙한 언어, 프레임워크 및 도구를 사용하여 탁월한 경험을 구축하고 제공할 수 있는 자유를 제공합니다.

#### 세부 사항 {#details-your-apps}

* [개발을 위해 AEM SDK를 설치하고 사용합니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html)
* [AEM Headless 개발자 리소스](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=ko-KR)
* 예, 다음 포함 [반응](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/react-app.html), [Next.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/next-js.html), [Node.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/server-to-server-app.html), 기타

#### 환경 {#environments-your-apps}

앱은 일반적으로 다음 사이트에서 개발, 테스트 및 사용됩니다.

* 미리보기
* 게시

대상:

* 개발
* 테스트
* 프로덕션

### 추가 리소스

AEM GraphQL 및 컨텐츠 조각에 대한 자세한 내용은 다음을 참조하십시오.

* [콘텐츠 조각과 함께 사용하기 위한 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)
* [GraphiQL IDE 사용](/help/headless/graphql-api/graphiql-ide.md)
* [AEM Headless 개발자 리소스](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=ko-KR)
