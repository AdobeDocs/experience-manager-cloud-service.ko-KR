---
title: GraphQL이 있는 컨텐츠 조각을 사용하여 헤드리스 컨텐츠 전달
description: AEM(Adobe Experience Manager)의 컨텐츠 조각을 헤드리스 컨텐츠 전달을 위해 GraphQL이 있는 Cloud Service으로 사용하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 54b377c6d98398fd5066dc4a3337a3877b9e3ed7
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 1%

---


# GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}의 컨텐츠 조각을 사용하여 헤드리스 컨텐츠 배달

AEM(Adobe Experience Manager)을 Cloud Service으로 사용하면 AEM GraphQL API(표준 GraphQL을 기반으로 사용자 정의된 구현)과 함께 컨텐츠 조각을 사용하여 애플리케이션에서 사용할 수 있도록 구조화된 컨텐츠를 제공할 수 있습니다. 단일 API 쿼리를 사용자 지정하는 기능을 사용하면 렌더링할 특정 컨텐츠를 검색하고 전달할 수 있습니다(단일 API 쿼리에 대한 응답).

>[!NOTE]
>
>Cloud Service으로 AEM Sites에 대한 헤드리스 개발에 대한 소개를 보려면 [헤드리스 및 AEM](/help/implementing/developing/headless/introduction.md)을 참조하십시오.

## 헤드리스 CMS {#headless-cms}

헤드리스 콘텐츠 관리 시스템(CMS)은 다음과 같습니다.

* &quot;*헤드리스 콘텐츠 관리 시스템 또는 헤드리스 CMS는 처음부터 API를 통해 콘텐츠를 액세스할 수 있도록 콘텐츠를 모든 장치에 표시하는 콘텐츠 저장소로 구축된 백엔드 전용 콘텐츠 관리 시스템(CMS)입니다.*

   [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system)을(를) 참조하십시오.

AEM에서 컨텐츠 조각을 작성하는 관점에서 볼 때, 이것은 다음을 의미합니다.

* 컨텐츠 조각을 사용하면 기본적으로 서식이 지정된 페이지에 직접 게시되지 않은 컨텐츠를 작성할 수 있습니다(1:1).

* 컨텐츠 조각 모델에 따라 컨텐츠 조각 컨텐츠가 미리 결정된 방식으로 구조화됩니다. 이렇게 하면 응용 프로그램에 대한 액세스가 간소화되므로 응용 프로그램을 더욱 세부적으로 처리할 수 있습니다.

## GraphQL - 개요 {#graphql-overview}

GraphQL:

* &quot;*...API에 대한 쿼리 언어 및 기존 데이터를 사용한 쿼리를 충족하는 런타임입니다.*&quot;

   [GraphQL.org](https://graphql.org) 참조

[AEM GraphQL API](#aem-graphql-api)에서는 [컨텐츠 조각](/help/assets/content-fragments/content-fragments.md);에 대해 (복잡한) 쿼리를 수행할 수 있습니다.각 쿼리는 특정 모델 유형에 따라 달라집니다. 그런 다음 반환된 컨텐츠를 애플리케이션에서 사용할 수 있습니다.

## AEM GraphQL API {#aem-graphql-api}

Adobe Experience as a Cloud Experience의 경우, 표준 GraphQL API의 맞춤형 구현이 개발되었습니다. 자세한 내용은 [AEM GraphQL API를 참조하십시오](/help/assets/content-fragments/graphql-api-content-fragments.md).

AEM GraphQL API 구현은 [GraphQL Java 라이브러리](https://graphql.org/code/#java)을 기반으로 합니다.

## AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}에 사용할 컨텐츠 조각

[컨텐츠 ](#content-fragments) 조각은 다음과 같이 AEM 쿼리에 대한 GraphQL의 기초로 사용됩니다.

* 페이지와 독립된 컨텐츠를 디자인, 제작, 조정 및 게시할 수 있습니다.
* [컨텐츠 조각 모델](#content-fragments-models)은 정의된 데이터 유형을 통해 필요한 구조를 제공합니다.
* 모델을 정의할 때 사용할 수 있는 [조각 참조](#fragment-references)는 구조의 추가 레이어를 정의하는 데 사용할 수 있습니다.

![GraphQL에 사용할 ](assets/cfm-nested-01.png "GraphQLContent 조각에 사용할 컨텐츠 조각")

### 콘텐츠 조각 {#content-fragments}

컨텐츠 조각:

* 구조화된 컨텐츠를 포함합니다.

* 이 모델은 결과 조각의 구조를 미리 정의하는 [컨텐츠 조각 모델](#content-fragments-models)을 기반으로 합니다.

### 컨텐츠 조각 모델 {#content-fragments-models}

다음 [컨텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md):

* [스키마](https://graphql.org/learn/schema/)을(를) 생성하는 데 사용됩니다. **활성화됨**.

* GraphQL에 필요한 데이터 유형과 필드를 제공합니다. 응용 프로그램이 가능한 것만 요청하고 예상대로 수신하도록 합니다.

* 데이터 유형 **[조각 참조](#fragment-references)**&#x200B;는 모델에서 다른 컨텐츠 조각을 참조하기 위해 사용할 수 있으므로 추가 구조 수준을 활용할 수 있습니다.

### 조각 참조 {#fragment-references}

**[조각 참조](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* GraphQL과 함께 사용하는 경우에 특히 유용합니다.

* 컨텐츠 조각 모델을 정의할 때 사용할 수 있는 특정 데이터 유형입니다.

* 특정 컨텐츠 조각 모델에 따라 다른 조각을 참조합니다.

* 구조화된 데이터를 검색할 수 있습니다.

   * **다중 피드**&#x200B;로 정의되면 여러 하위 조각을 기본 조각의 참조(검색)할 수 있습니다.

### JSON 미리 보기 {#json-preview}

컨텐츠 조각 모델을 디자인하고 개발하는 데 도움이 되도록 [JSON 출력](/help/assets/content-fragments/content-fragments-json-preview.md)을 미리 볼 수 있습니다.

## AEM에서 GraphQL 사용 방법 학습 - 샘플 컨텐츠 및 쿼리 {#learn-graphql-with-aem-sample-content-queries}

AEM GraphQL API 사용에 대한 자세한 내용은 [AEM에서 GraphQL을 사용하는 방법 학습 - 샘플 컨텐츠 및 쿼리](/help/assets/content-fragments/content-fragments-graphql-samples.md)을 참조하십시오.

## 자습서 - AEM 헤드리스 및 GraphQL 시작하기

실습 자습서를 찾고 계십니까? AEM GraphQL API를 사용하여 콘텐츠를 빌드하고 노출하고 헤드리스 CMS 시나리오에서 외부 앱에서 사용하는 방법을 소개하는 [AEM 헤드리스 시작하기 및 GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) 엔드 투 엔드 자습서를 참조하십시오.