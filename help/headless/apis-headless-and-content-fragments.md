---
title: 구조화된 컨텐츠 전달 및 컨텐츠 조각 관리를 위한 AEM API
description: 구조화된 컨텐츠 전달 및 컨텐츠 조각 관리에 사용할 수 있는 API에 대해 알아봅니다
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
source-git-commit: 21599676916068f3529976410a93951b02f750b0
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 1%

---


# 구조화된 컨텐츠 전달 및 관리를 위한 AEM API {#aem-apis-structured-content-delivery-and-management}

Adobe Experience Manager(AEM as a Cloud Service)는 구조화된 컨텐츠 조각과 컨텐츠 조각 관리를 모두 위한 여러 API를 제공합니다. 특정 API에 대한 자세한 내용은 개별 페이지 를 참조하십시오.

* [콘텐츠 조각 배달을 위한 AEM REST OpenAPI](/help/headless/aem-rest-openapi-content-fragment-delivery.md)
   * 이 API는 AEM의 콘텐츠 조각에서 구조화된 콘텐츠를 제공하기 위한 JSON 응답을 생성합니다.
   * 콘텐츠 조각에 대한 경로를 끝점으로 사용합니다.
   * 이 API는 REST를 기반으로 합니다.
   * CDN 통합을 포함하여 콘텐츠 전달에 최적화되었습니다.
* [컨텐츠 조각 전달을 위한 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)
   * 이 API는 스키마 기반입니다. API 스키마는 콘텐츠 구조를 정의하는 콘텐츠 조각 모델로 표시됩니다.
   * 이 API는 GraphQL 기반입니다.
* [콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)
   * 이러한 API는 구조화된 컨텐츠 관리를 위한 것입니다.
   * 각 GET 연산자는 컨텐츠 전달에 최적화되지 않습니다.
   * 이 API는 REST를 기반으로 합니다.
* [AEM Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)
   * AEM의 구조화된 컨텐츠 제공을 위한 JSON 출력을 위한 원래 API입니다.
      * 강력하고 입증된 이 API는 *완전 하이드레이션된* JSON 출력을 제공하지 않습니다. 참조는 경로로만 출력되므로 추가 콘텐츠 검색을 위해 보조 API 요청이 필요합니다.
   * Assets HTTP API는 콘텐츠 조각 및 콘텐츠 조각 모델(CRUD)을 관리하는 데에도 사용할 수 있습니다.
   * 이 API는 REST를 기반으로 합니다.
   * Assets HTTP API의 콘텐츠 조각 지원은 Edge Delivery Services JSON REST API에 의해 승계되므로 향후 더 이상 사용되지 않습니다. 아직 타임스케일이 결정되지 않았습니다.

<!--
## JSON vs HTML {#json-vs-HTML}

The content delivery format used is driven by frontend implementation. Unstructured content/HTML for full-stack implementations, structured content/JSON for headless implementations, or a combination of both in hybrid implementations. 

Key considerations include:

* Definition
  * JSON (JavaScript Object Notation) - used to represent, access and process structured data. 
  * HTML (HyperText Markup Language) - a markup language of tags and elements in a hierarchical structure.
* Primary Purpose
  * JSON is often used for transferring structure content between the server and client app.
  * HTML is the standard markup language for creating and rendering web pages in a browser.
-->

## REST 및 GraphQL {#rest-vs-graphql}

사용된 API는 개발자를 위한 의사 결정이며 AEM은 두 가지를 모두 지원합니다.

많은 비교가 온라인에서 사용할 수 있지만 REST의 몇 가지 특징 및 이점은 다음과 같습니다.

* 단순성

   * 개발자는 HTTP 및 REST에 익숙한 경우가 많습니다. [API의 Postman 상태 보고서](https://www.postman.com/state-of-api/)에 따르면 개발자의 높은 비율이 REST를 사용합니다.

   * 단순함에는 친숙함이 따른다. REST에서는 쿼리를 누가 소유하고 앱을 누가 소유하는지에 대한 조직의 질문이 없지만, GraphQL에서는 이러한 질문이 발생할 수 있습니다.

   * 친숙하게(일반적으로) 광범위한 커뮤니티 및 도구 환경이 제공됩니다. GraphQL의 고유한 단점은 아니지만 REST를 위해 더 광범위하고 더 깊이 있을 수 있습니다.

   * 더 간단한 접근 방식은 보안 구현을 더 쉽게 할 수도 있다. REST를 사용하면 렌더링할 콘텐츠를 결정하는 필터링이 클라이언트 앱에서 모두 수행됩니다. GraphQL을 사용하면 클라이언트와 서버 간의 스키마 기반 쿼리에서 발생합니다.

* 유연성

   * REST를 사용하면 개발자는 모든 리소스를 `GET`할 수 있습니다. GraphQL에서는 스키마 내에 정의된 리소스로 제한됩니다.

* 캐싱

   * REST `GET` 요청에 대한 JSON 응답은 기본적으로 캐시할 수 있습니다. GraphQL `POST` 요청은 캐시되지 않는 한 캐시할 수 없습니다. 예를 들어 서버에 저장되고 REST와 유사한 `GET` 요청으로 요청된 AEM 지속 쿼리를 사용합니다.

GraphQL의 이점은 다음과 같습니다.

* 콘텐츠 전달 효율성

   * 초점

      * GraphQL 클라이언트 애플리케이션을 사용하면 렌더링에 필요한 정확한 콘텐츠를 요청할 수 있으며, 더 이상 필요하지 않습니다. 이 접근 방식은 과도한 콘텐츠 페이로드 및 불필요한 대역폭 소비를 통해 콘텐츠 과다 전달을 방지합니다.

   * 단일 엔드포인트

      * REST에서는 모든 API 요청이 끝점이지만 GraphQL에서는 하나의 공통 끝점만 있으며 다른 콘텐츠 요청은 해당 공통 끝점을 사용하는 쿼리로 표현됩니다.

* 래피드 프로토타이핑

   * GraphQL을 사용하면 GraphQL 쿼리에 포함된 1단계 프로세스로서 프로토타입을 보다 쉽게 만들 수 있습니다. 반면에 REST는 2단계 프로세스입니다.

      1. API로 콘텐츠를 가져옵니다.
      2. JSON 응답에서 클라이언트 앱에서 렌더링에 사용할 항목을 결정합니다.
