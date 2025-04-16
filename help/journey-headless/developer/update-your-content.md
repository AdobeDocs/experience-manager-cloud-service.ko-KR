---
title: AEM API를 통해 콘텐츠를 업데이트하는 방법
description: 이 AEM Headless 개발자 여정 부분에서는 사용 가능한 API를 사용하여 콘텐츠 조각의 콘텐츠에 액세스하고 업데이트하는 방법을 알아봅니다.
exl-id: 84120856-fd1d-40f7-8df4-73d4cdfcc43b
solution: Experience Manager
feature: Headless, Content Fragments, GraphQL API
role: Admin, Architect, Developer
source-git-commit: d9db32110e1e0aaa5bdc20bd6b4bff6da6a3a3a3
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 33%

---

# AEM API를 통해 콘텐츠를 업데이트하는 방법 {#update-your-content}

[AEM Headless 개발자 여정](overview.md)의 이 부분에서는 사용 가능한 API를 사용하여 콘텐츠 조각의 콘텐츠에 액세스하고 업데이트하는 방법을 알아봅니다.

## 지금까지의 스토리 {#story-so-far}

AEM Headless 번역 여정의 이전 문서인 [AEM Delivery API를 통해 콘텐츠를 액세스하는 방법](access-your-content.md)에서 AEM GraphQL API를 통해 AEM의 Headless 콘텐츠에 액세스하는 방법에 대해 알아보았습니다. 여기에서 알게 된 내용은 다음과 같습니다.

* 고차원의 GraphQL을 이해해야 합니다.
* AEM GraphQL API Target의 작동 방식을 이해할 수 있습니다.
* 몇 가지 실용적인 샘플 쿼리를 이해할 수 있습니다.

이 문서는 이러한 기본 사항을 기본으로 하며, 이를 통해 사용 가능한 API를 통해 AEM에서 기존 Headless 콘텐츠를 업데이트하는 방법을 이해합니다.

## 목표 {#objective}

* **대상자**: 고급
* **목표**: 콘텐츠 조각의 콘텐츠에 액세스하고 업데이트하는 데 사용할 수 있는 API에 대해 알아봅니다.

## 컨텐츠 조각과 함께 사용하기 위한 AEM API {#aem-apis-for-use-with-content-fragments}

Adobe Experience Manager(AEM) as a Cloud Service은 콘텐츠 조각의 구조화된 콘텐츠 전달 및 콘텐츠 조각 관리를 위한 여러 API를 제공합니다. 특정 API에 대한 자세한 내용은 개별 페이지 를 참조하십시오.

* OpenAPI를 사용한 AEM 컨텐츠 조각 게재
   * 이 API는 AEM의 콘텐츠 조각에서 구조화된 콘텐츠를 제공하기 위한 JSON 응답을 만듭니다.
   * 콘텐츠 조각에 대한 경로를 끝점으로 사용합니다.
   * 이 API는 REST를 기반으로 합니다.
   * CDN 통합을 포함하여 콘텐츠 전달에 최적화되었습니다.
* 컨텐츠 조각 전달을 위한 AEM GraphQL API
   * 이 API는 스키마 기반입니다. API 스키마는 콘텐츠 구조를 정의하는 콘텐츠 조각 모델로 표시됩니다.
   * 이 API는 GraphQL 기반입니다.
* 콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI
   * 이러한 API는 구조화된 컨텐츠 관리를 위한 것입니다.
   * 각 GET 연산자는 컨텐츠 전달에 최적화되어 있지 않습니다.
   * 이 API는 REST를 기반으로 합니다.
* AEM Assets HTTP API의 콘텐츠 조각 지원
   * AEM의 구조화된 컨텐츠 제공을 위한 JSON 출력을 위한 원래 API입니다.
      * 강력하고 입증된 이 API는 *완전 하이드레이션된* JSON 출력을 제공하지 않습니다. 참조는 경로로만 출력되므로 추가 콘텐츠 검색을 위해 보조 API 요청이 필요합니다.
   * Assets HTTP API는 콘텐츠 조각 및 콘텐츠 조각 모델(CRUD)을 관리하는 데에도 사용할 수 있습니다.
   * 이 API는 REST를 기반으로 합니다.
   * Assets HTTP API의 콘텐츠 조각 지원은 Edge Delivery Services JSON REST API에 의해 승계되므로 향후 더 이상 사용되지 않습니다. 아직 타임스케일이 결정되지 않았습니다.

## 다음 단계 {#whats-next}

AEM Headless 개발자 여정의 한 부분을 완료했으므로,

* 사용 가능한 AEM API를 이해합니다.
* 이러한 API에서 콘텐츠 조각이 지원되는 방식을 이해합니다.

다음 문서인 [결합 방법 - AEM Headless의 앱과 콘텐츠](put-it-all-together.md)를 검토하여 AEM Headless 여정을 계속하는 것이 좋습니다(애플리케이션 결합에 사용해야 할 AEM 아키텍처 기본 사항 및 도구에 익숙한 경우).

## 추가 리소스 {#additional-resources}

* [Adobe Experience Manager as a Cloud Service API](https://developer.adobe.com/experience-cloud/experience-manager-apis/)
* [구조화된 콘텐츠 게재 및 관리를 위한 AEM API](/help/headless/apis-headless-and-content-fragments.md)
* [OpenAPI를 사용한 AEM 컨텐츠 조각 게재](/help/headless/aem-content-fragment-delivery-with-openapi.md)
* [컨텐츠 조각 전달을 위한 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)
* [콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)
* [AEM Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)
* [콘텐츠 조각을 사용하여 작업](/help/sites-cloud/administering/content-fragments/overview.md)
* [AEM 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
* [CORS/AEM 설명](https://helpx.adobe.com/kr/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [비디오 - AEM](https://helpx.adobe.com/kr/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)에서 CORS용 개발
* [AEM as a Headless CMS 소개](/help/headless/introduction.md)
* [AEM 개발자 포털](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [AEM의 Headless 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
