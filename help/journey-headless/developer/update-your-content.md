---
title: AEM API를 통해 콘텐츠를 업데이트하는 방법
description: 이 AEM Headless 개발자 여정 부분에서는 사용 가능한 API를 통해 콘텐츠 조각의 콘텐츠에 액세스하고 업데이트하는 방법에 대해 알아봅니다.
exl-id: 84120856-fd1d-40f7-8df4-73d4cdfcc43b
solution: Experience Manager
feature: Headless, Content Fragments, GraphQL API
role: Admin, Architect, Developer
source-git-commit: 8a3ee333a0bd5904c43c424967a7b9c752fd38c2
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 99%

---

# AEM API를 통해 콘텐츠를 업데이트하는 방법 {#update-your-content}

이 [AEM Headless 개발자 여정](overview.md) 부분에서는 사용 가능한 API를 통해 콘텐츠 조각의 콘텐츠에 액세스하고 업데이트하는 방법에 대해 알아봅니다.

## 지금까지의 스토리 {#story-so-far}

AEM Headless 번역 여정의 이전 문서인 [AEM Delivery API를 통해 콘텐츠를 액세스하는 방법](access-your-content.md)에서 AEM GraphQL API를 통해 AEM의 Headless 콘텐츠에 액세스하는 방법에 대해 알아보았습니다. 여기에서 알게 된 내용은 다음과 같습니다.

* 고차원의 GraphQL을 이해해야 합니다.
* AEM GraphQL API Target의 작동 방식을 이해할 수 있습니다.
* 몇 가지 실용적인 샘플 쿼리를 이해할 수 있습니다.

이 문서는 해당 기본 사항을 기본으로 하며, 이를 통해 사용 가능한 API를 통해 AEM의 기존 Headless 콘텐츠를 업데이트하는 방법을 살펴볼 수 있습니다.

## 목표 {#objective}

* **대상자**: 고급
* **목표**: 콘텐츠 조각의 콘텐츠에 액세스하고 업데이트하는 데 사용할 수 있는 API에 대해 알아봅니다.

## 콘텐츠 조각과 함께 사용하기 위한 AEM API {#aem-apis-for-use-with-content-fragments}

Adobe Experience Manager(AEM) as a Cloud Service는 콘텐츠 조각에서 구조화된 콘텐츠 게재와 콘텐츠 조각 관리를 위한 여러 API를 제공합니다. 특정 API에 대한 자세한 내용은 개별 페이지를 참조하시기 바랍니다.

* OpenAPI와 함께 사용하는 AEM 콘텐츠 조각 게재
   * 이 API는 AEM의 콘텐츠 조각에서 구조화된 콘텐츠를 제공하기 위한 JSON 응답을 생성합니다.
   * 콘텐츠 조각에 대한 경로를 엔드포인트로 사용합니다.
   * 이 API는 REST 기반입니다.
   * CDN 통합을 비롯한 콘텐츠 게재에 최적화되어 있습니다.
* 콘텐츠 조각 게재를 위한 AEM GraphQL API
   * 이 API는 스키마 기반입니다. API 스키마는 콘텐츠 구조를 정의하는 콘텐츠 조각 모델로 표현됩니다.
   * 이 API는 GraphQL 기반입니다.
* 콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI
   * 이러한 API는 구조화된 콘텐츠 관리에 사용됩니다.
   * 각 GET 연산자는 콘텐츠 게재에 최적화되어 있지 않습니다.
   * 이 API는 REST 기반입니다.

>[!NOTE]
>
>[Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)은 현재 [더 이상 사용되지 않습니다](/help/release-notes/deprecated-removed-features.md). 이는 [OpenAPI를 통한 콘텐츠 조각 게재](/help/headless/aem-content-fragment-delivery-with-openapi.md) 및 [콘텐츠 조각 및 콘텐츠 조각 모델 관리 OpenAPI](/help/headless/content-fragment-openapis.md)로 대체되었습니다.

## 다음 단계 {#whats-next}

AEM Headless 개발자 여정의 한 부분을 완료했으므로,

* 사용 가능한 AEM API를 이해합니다.
* 이 API에서 콘텐츠 조각을 지원하는 방법을 이해합니다.

다음 문서인 [결합 방법 - AEM Headless의 앱과 콘텐츠](put-it-all-together.md)를 검토하여 AEM Headless 여정을 계속하는 것이 좋습니다(애플리케이션 결합에 사용해야 할 AEM 아키텍처 기본 사항 및 도구에 익숙한 경우).

## 추가 리소스 {#additional-resources}

* [Adobe Experience Manager as a Cloud Service API](https://developer.adobe.com/experience-cloud/experience-manager-apis/)
* [구조화된 콘텐츠 게재 및 관리를 위한 AEM API](/help/headless/apis-headless-and-content-fragments.md)
* [OpenAPI와 함께 사용하는 AEM 콘텐츠 조각 게재](/help/headless/aem-content-fragment-delivery-with-openapi.md)
* [콘텐츠 조각 게재를 위한 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)
* [콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)
* [AEM Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)
* [콘텐츠 조각을 사용하여 작업](/help/sites-cloud/administering/content-fragments/overview.md)
* [AEM 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
* [CORS/AEM 설명](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html)
* [비디오 - AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/develop-for-cross-origin-resource-sharing.html)에서 CORS용 개발
* [AEM as a Headless CMS 소개](/help/headless/introduction.md)
* [AEM 개발자 포털](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [AEM의 Headless 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
