---
title: GraphQL이 있는 컨텐츠 조각을 사용하여 헤드리스 컨텐츠 전달
description: AEM(Adobe Experience Manager)의 컨텐츠 조각을 헤드리스 컨텐츠 전달을 위해 GraphQL이 있는 Cloud Service으로 사용하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: da8fcf1288482d406657876b5d4c00b413461b21
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---


# GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}의 컨텐츠 조각을 사용하여 헤드리스 컨텐츠 배달

>[!CAUTION]
>
>요청에 따라 컨텐츠 조각 전달용 AEM GraphQL API를 사용할 수 있습니다.
>
>AEM용 API를 Cloud Service 프로그램으로 활성화하려면 [Adobe 지원](https://experienceleague.adobe.com/?lang=en&amp;support-solution=General#support)에 문의하십시오.

AEM(Adobe Experience Manager)을 Cloud Service으로 사용하면 AEM GraphQL API(표준 GraphQL을 기반으로 사용자 정의된 구현)과 함께 컨텐츠 조각을 사용하여 애플리케이션에서 사용할 수 있도록 구조화된 컨텐츠를 제공할 수 있습니다.

## 헤드리스 CMS {#headless-cms}

헤드리스 콘텐츠 관리 시스템(CMS)은 다음과 같습니다.

* &quot;*헤드리스 콘텐츠 관리 시스템 또는 헤드리스 CMS는 처음부터 API를 통해 콘텐츠를 액세스할 수 있도록 콘텐츠를 모든 장치에 표시하는 콘텐츠 저장소로 구축된 백엔드 전용 콘텐츠 관리 시스템(CMS)입니다.*

   *&quot;헤드리스&quot;라는 용어는 &quot;본문&quot;(즉, 컨텐츠 저장소)의 &quot;헤드&quot;(즉, 웹 사이트)를 잘라내는 개념에서 유래합니다.*&quot;

   [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system)을(를) 참조하십시오.

AEM에서 컨텐츠 조각을 작성하는 관점에서 볼 때, 이것은 다음을 의미합니다.

* 컨텐츠 조각을 사용하면 기본적으로 서식이 지정된 페이지에 직접 게시되지 않은 컨텐츠를 작성할 수 있습니다(1:1).

* 컨텐츠 조각 모델에 따라 컨텐츠 조각 컨텐츠가 미리 결정된 방식으로 구조화됩니다. 이렇게 하면 응용 프로그램에 대한 액세스가 간소화되므로 응용 프로그램을 더욱 세부적으로 처리할 수 있습니다.

>[!NOTE]
>
>Cloud Service으로 AEM Sites에 대한 헤드리스 개발에 대한 소개를 보려면 [헤드리스 및 AEM](/help/implementing/developing/headless/introduction.md)을 참조하십시오.

## GraphQL - 개요 {#graphql-overview}

GraphQL:

* &quot;*...API에 대한 쿼리 언어 및 기존 데이터와 관련 쿼리를 충족하는 런타임입니다. GraphQL은 API에 있는 데이터에 대한 완벽하고 이해할 수 있는 설명을 제공하며 고객에게 필요한 것과 더 이상 필요한 것을 정확하게 요청할 수 있는 기능을 제공하고 시간이 지남에 따라 API를 보다 쉽게 발전시켜 주며 강력한 개발자 도구를 활성화합니다.*&quot;

   [GraphQL.org](https://graphql.org) 참조

* &quot;*...유연한 API 레이어의 개방형 사양입니다. GraphQL을 기존 백엔드에 배치하여 보다 신속하게 제품을 구축할 수 있습니다..*&quot;

   [GraphQL 탐색](https://www.graphql.com)을 참조하십시오. &quot;*Explore GraphQL은 Apollo 팀이 유지 관리합니다. Adobe의 목표는 GraphQL*&quot;을 이해하고 채택하는 데 필요한 모든 툴을 전세계 개발자와 기술 리더에게 제공하는 것입니다.

[AEM GraphQL API](#aem-graphql-api)에서는 [컨텐츠 조각](/help/assets/content-fragments/content-fragments.md);에 대해 (복잡한) 쿼리를 수행할 수 있습니다.각 쿼리는 특정 모델 유형에 따라 달라집니다. 그런 다음 반환된 컨텐츠를 애플리케이션에서 사용할 수 있습니다.

### GraphQL 용어 {#graphql-terminology}

GraphQL은 다음을 사용합니다.

* **[쿼리](https://graphql.org/learn/queries/)**

* **[스키마 및 유형](https://graphql.org/learn/schema/)**  - GraphQL은 이 기능을 사용하여 AEM용 GraphQL 구현에 허용된 유형과 작업을 표시합니다.

* **[필드](https://graphql.org/learn/queries/#fields)**

* **GraphQL 끝점**  - GraphQL 쿼리에 응답하고 GraphQL 스키마에 대한 액세스를 제공하는 AEM의 경로입니다.

[우수 사례](https://graphql.org/learn/best-practices/)를 비롯한 자세한 내용은 [(GraphQL.org) GraphQL 소개](https://graphql.org/learn/)을 참조하십시오.

### GraphQL 쿼리 유형 {#graphql-query-types}

GraphQL을 사용하여 다음 중 하나에 대한 쿼리를 수행할 수 있습니다.

* **단일 항목**

* **[항목 목록](https://graphql.org/learn/schema/#lists-and-non-null)**

## AEM GraphQL API {#aem-graphql-api}

[클라우드 경험으로서 Adobe Experience의 경우 표준 GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)의 사용자 지정된 구현이 구현되었습니다.

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