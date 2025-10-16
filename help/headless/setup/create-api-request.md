---
title: API 요청 만들기 - Headless 설정
description: 콘텐츠 조각 콘텐츠의 Headless 게재를 위해 GraphQL API를 사용하는 방법과 콘텐츠 조각을 관리하기 위해 AEM의 자산 REST API를 사용하는 방법을 알아봅니다.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 88%

---

# API 요청 만들기 - Headless 설정 {#accessing-delivering-content-fragments}

콘텐츠 조각 콘텐츠의 Headless 게재를 위해 GraphQL API를 사용하는 방법과 콘텐츠 조각을 관리하기 위해 AEM의 자산 REST API를 사용하는 방법을 알아봅니다.

## GraphQL 및 Assets REST API란 무엇입니까? {#what-are-the-apis}

[일부 콘텐츠 조각을 만들었으므로](create-content-fragment.md) AEM의 API를 사용하여 headless로 전달할 수 있습니다.

* [GraphQL API](/help/headless/graphql-api/content-fragments.md)를 사용하여 콘텐츠 조각에 액세스하고 전달하기 위한 요청을 생성할 수 있습니다. 이 API는 콘텐츠 조각 콘텐츠를 쿼리하고 소비하기 위한 가장 강력한 기능 집합을 제공합니다.
   * API를 사용하려면 [AEM에서 엔드포인트를 정의 및 활성화하고](/help/headless/graphql-api/graphql-endpoint.md), 필요한 경우 [GraphiQL 인터페이스를 설치](/help/headless/graphql-api/graphiql-ide.md)합니다
* [구조화된 컨텐츠 배달 및 관리를 위한 AEM API](/help/headless/apis-headless-and-content-fragments.md)의 선택을 컨텐츠 조각과 함께 사용할 수 있습니다.

이 안내서의 나머지 부분에서는 GraphQL 액세스 및 콘텐츠 조각 게재에 중점을 둡니다.

## GraphQL 엔드포인트 활성화 {#enable-graphql-endpoint}

GraphQL API를 사용하려면 먼저 GraphQL 엔드포인트를 만들어야 합니다.

자세한 내용은 [AEM에서 GraphQL 끝점 관리](/help/headless/graphql-api/graphql-endpoint.md)를 참조하십시오.

## GraphiQL로 GraphQL을 사용하여 콘텐츠 쿼리

정보 아키텍트는 콘텐츠를 전달하기 위해 채널 엔드포인트에 대한 쿼리를 설계합니다. 이러한 쿼리는 모델당 엔드포인트당 한 번만 고려하십시오. 이 시작 안내서에서는 하나만 만들어야 합니다.

GraphiQL은 AEM 환경에 포함된 IDE입니다. [엔드포인트를 구성](#enable-graphql-endpoint)한 다음 액세스/볼 수 있습니다.

자세한 내용은 [GraphiQL IDE 사용](/help/headless/graphql-api/graphiql-ide.md)을 참조하세요.

GraphQL은 특정 데이터 세트 또는 개별 데이터 오브젝트를 대상으로 할 수 있을 뿐만 아니라 오브젝트의 특정 요소 및 중첩된 결과를 전달할 수 있는 구조화된 쿼리를 가능하게 하고, 쿼리 변수 등에 대한 지원을 제공합니다.

GraphQL은 반복적인 API 요청 및 초과 게재를 방지할 수 있으며 대신 단일 API 쿼리에 대한 응답으로 렌더링에 필요한 것을 정확히 대량으로 게재할 수 있도록 허용합니다. 결과 JSON은 데이터를 다른 사이트나 앱으로 전달하는 데 사용할 수 있습니다.

## 다음 단계 {#next-steps}

이번 단계가 끝났습니다! 이제 AEM의 Headless 콘텐츠 관리에 대한 기본 사항을 이해했습니다. 사용 가능한 기능을 포괄적으로 이해하기 위해 더 자세히 알아볼 수 있는 더 많은 리소스가 있습니다.

* **[콘텐츠 조각](/help/sites-cloud/administering/content-fragments/managing.md)** - 콘텐츠 조각 생성 및 관리에 대한 자세한 내용
* **[AEM Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)** - CRUD(만들기, 읽기, 업데이트, 삭제) 작업을 통해 HTTP API로 직접 AEM 콘텐츠에 액세스하는 방법에 대한 자세한 내용
* **[GraphQL API](/help/headless/graphql-api/content-fragments.md)** - 콘텐츠 조각을 Headless 방식으로 전달하는 방법에 대한 자세한 내용

>[!NOTE]
>
>[콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)도 사용하실 수 있습니다.
