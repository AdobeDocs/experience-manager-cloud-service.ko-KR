---
title: GraphQL에서 컨텐츠 조각을 사용하여 헤드리스 컨텐츠 전달
description: GraphQL에서 헤드리스 컨텐츠 전달을 위해 컨텐츠 조각을 사용하여 AEM 헤드리스 CMS를 구현하는 기본 개념을 알아봅니다.
feature: Content Fragments, GraphQL API
topic: Headless
role: User
exl-id: 4a3b030d-ed59-4920-bf94-e00a45f85b51
source-git-commit: f296e8cbc12c9426e0fefe6f5342374ba9b21291
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 17%

---

# GraphQL에서 컨텐츠 조각을 사용하여 헤드리스 컨텐츠 전달 {#headless-content-delivery-using-content-fragments-with-graphQL}

컨텐츠 조각 및 GraphQL API를 사용하여 AEM(Adobe Experience Manager) as a Cloud Service CMS(Headless Content Management System)로 사용할 수 있습니다.

이 작업은 AEM GraphQL API(표준 GraphQL을 기반으로 하는 사용자 정의 구현)와 함께 컨텐츠 조각을 사용하여 애플리케이션에서 사용할 구조화된 컨텐츠를 헤드리도록 합니다. 단일 API 쿼리를 사용자 지정하는 기능을 사용하면 렌더링하려는 특정 콘텐츠(단일 API 쿼리에 대한 응답)를 검색하고 전달할 수 있습니다.

>[!NOTE]
>
>자세한 내용은 [헤드리스 및 AEM](/help/headless/introduction.md) AEM Sites as a Cloud Service용 헤드리스 개발에 대한 소개.

>[!NOTE]
>
>GraphQL은 현재 Adobe Experience Manager(AEM) as a Cloud Service의 두 가지 (별도) 시나리오에서 사용됩니다.
>
>* [AEM Commerce에서는 GraphQL을 통해 상거래 플랫폼에서 데이터를 사용합니다](/help/commerce-cloud/integrating/magento.md).
>* [AEM 콘텐츠 조각은 AEM GraphQL API(표준 GraphQL 기반의 맞춤화된 구현)와 함께 작동하여 애플리케이션에서 사용할 구조화된 콘텐츠를 제공합니다](/help/headless/graphql-api/content-fragments.md).


## 헤드리스 CMS {#headless-cms}

헤드리스 콘텐츠 관리 시스템(CMS)은 다음과 같습니다.

* &quot;*헤드리스 콘텐츠 관리 시스템 또는 헤드리스 CMS는 처음부터 콘텐츠 저장소로서 구축된 백 엔드 전용 콘텐츠 관리 시스템(CMS)으로, API를 통해 콘텐츠를 액세스하여 모든 장치에 표시할 수 있도록 합니다.*

   자세한 내용은 [위키백과](https://en.wikipedia.org/wiki/Headless_content_management_system).

AEM에서 컨텐츠 조각 작성 측면에서 볼 때 이것은 다음을 의미합니다.

* 컨텐츠 조각을 사용하여 주로 형식이 지정된 페이지에 직접 게시되지 않는 컨텐츠를 작성할 수 (1:1).

* 컨텐츠 조각 모델에 따라 컨텐츠 조각의 컨텐츠가 미리 결정된 방식으로 구조화됩니다. 이렇게 하면 애플리케이션의 액세스를 간소화할 수 있으므로 컨텐츠가 더 많이 처리됩니다.

## GraphQL - 개요 {#graphql-overview}

GraphQL은

* &quot;*...api에 대한 쿼리 언어 및 기존 데이터를 사용하여 이러한 쿼리를 수행하기 위한 런타임.*&quot;.

   [GraphQL.org](https://graphql.org)를 참조하십시오.

다음 [AEM GraphQL API](#aem-graphql-api) 에서 (복잡한) 쿼리를 수행할 수 있습니다. [컨텐츠 조각](/help/assets/content-fragments/content-fragments.md); 각 쿼리가 특정 모델 유형에 따라 달라집니다. 그런 다음 반환된 컨텐츠를 애플리케이션에서 사용할 수 있습니다.

## AEM GraphQL API {#aem-graphql-api}

Adobe Experience as a Cloud Experience에서 표준 GraphQL API의 사용자 정의된 구현이 개발되었습니다. 자세한 내용은 [컨텐츠 조각에 사용할 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md) 자세한 내용

AEM GraphQL API 구현은 [GraphQL Java 라이브러리](https://graphql.org/code/#java).

## AEM GraphQL API에서 사용할 컨텐츠 조각 {#content-fragments-use-with-aem-graphql-api}

[컨텐츠 조각](#content-fragments) 는 다음과 같이 AEM 쿼리에 대한 GraphQL의 기반으로 사용할 수 있습니다.

* 페이지에 영향을 받지 않는 컨텐츠를 디자인, 작성, 조정 및 게시할 수 있도록 합니다.
* 다음 [컨텐츠 조각 모델](#content-fragments-models) 정의된 데이터 유형을 통해 필요한 구조를 제공합니다.
* 다음 [조각 참조](#fragment-references)를 사용하면 모델을 정의할 때 사용할 수 있으며 구조를 추가로 정의할 수 있습니다.

![GraphQL에서 사용할 컨텐츠 조각](assets/cfm-nested-01.png "GraphQL에서 사용할 컨텐츠 조각")

### 콘텐츠 조각 {#content-fragments}

콘텐츠 조각:

* 구조화된 컨텐츠를 포함합니다.

* 이러한 ID는 [컨텐츠 조각 모델](#content-fragments-models)- 결과 조각의 구조를 사전 정의합니다.

### 콘텐츠 조각 모델 {#content-fragments-models}

다음 [컨텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md):

* 를 생성하는 데 사용됩니다 [스키마](https://graphql.org/learn/schema/), 한 번 **활성화됨**.

* GraphQL에 필요한 데이터 유형과 필드를 제공합니다. 이 URL은 응용 프로그램이 가능한 요청만 하고 예상 내용을 수신하도록 합니다.

* 데이터 유형 **[조각 참조](#fragment-references)** 모델에서 다른 컨텐츠 조각을 참조하여 추가 구조 수준을 도입할 수 있습니다.

### 조각 참조 {#fragment-references}

다음 **[조각 참조](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* GraphQL과 함께 특정 관심이 있습니다.

* 컨텐츠 조각 모델을 정의할 때 사용할 수 있는 특정 데이터 유형입니다.

* 특정 컨텐츠 조각 모델에 따라 다른 조각을 참조합니다.

* 구조화된 데이터를 검색할 수 있습니다.

   * 로 정의된 경우 **다중 피드**&#x200B;를 채울 경우 하위 조각에서 여러 하위 조각을 참조(검색)할 수 있습니다.

### JSON 미리보기 {#json-preview}

컨텐츠 조각 모델 디자인 및 개발에 도움이 되도록 미리 볼 수 있습니다 [JSON 출력](/help/assets/content-fragments/content-fragments-json-preview.md).

## AEM으로 GraphQL을 사용하는 방법 배우기 - 샘플 콘텐츠 및 쿼리 {#learn-graphql-with-aem-sample-content-queries}

자세한 내용은 [AEM에서 GraphQL을 사용하는 방법 학습 - 샘플 컨텐츠 및 쿼리](/help/headless/graphql-api/sample-queries.md) AEM GraphQL API 사용에 대한 소개입니다.

## 튜토리얼 - AEM Headless 및 GraphQL 시작하기

실습형 튜토리얼을 찾고 계십니까? Headless CMS 시나리오에서, AEM의 GraphQL API를 사용하여 콘텐츠를 구축하고 노출하고 외부 앱에서 사용하는 방법을 보여 주는 [AEM Headless 및 GraphQL 시작하기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=ko-KR) 엔드투엔드 튜토리얼을 확인하십시오.
