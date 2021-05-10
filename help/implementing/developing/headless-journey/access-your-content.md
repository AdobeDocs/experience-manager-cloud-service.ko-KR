---
title: AEM 배달 API를 통해 콘텐츠에 액세스하는 방법
description: AEM 헤드리스 개발자 여정의 이 부분에서 GraphQL 쿼리를 사용하여 콘텐츠 조각 컨텐츠에 액세스하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: d21d5a496d4a82dd569e582b5b7d7425bd50077f
workflow-type: tm+mt
source-wordcount: '2155'
ht-degree: 1%

---

# AEM 배달 API {#access-your-content}를 통해 콘텐츠에 액세스하는 방법

>[!CAUTION]
>
>진행 중인 작업 - 이 문서의 작성은 진행 중이며 완전한 또는 최종적인 것으로 해석되거나 제작 목적으로 사용되어서는 안 됩니다.

[AEM 헤드리스 개발자 여정의 이 부분에서는 GraphQL 쿼리를 사용하여 콘텐츠 조각의 콘텐츠에 액세스하고 이를 앱에 피드(헤드리스 배달)하는 방법을 배울 수 있습니다.](overview.md)

## 지금까지 스토리 {#story-so-far}

AEM 헤드리스 여정의 이전 문서인 [컨텐츠를 모델링하는 방법](model-your-content.md)에서는 AEM에서 컨텐츠 모델링의 기본 사항을 학습했으므로 이제 컨텐츠 구조를 모델링하는 방법을 이해하고 AEM 컨텐츠 조각 모델 및 컨텐츠 조각을 사용하여 해당 구조를 구현해야 합니다.

* 컨텐트 모델링과 관련된 개념과 용어를 인식합니다.
* 헤드리스 컨텐츠 전달에 컨텐츠 모델링이 필요한 이유를 파악합니다.
* AEM 컨텐츠 조각 모델을 사용하여 이 구조를 실현하는 방법을 이해하고 컨텐츠 조각으로 컨텐츠를 작성합니다.
* 컨텐츠를 모델링하는 방법을 이해합니다.기본 견본과 원칙.

이 문서는 AEM GraphQL API를 사용하여 AEM에서 기존 헤드리스 콘텐츠에 액세스하는 방법을 이해할 수 있도록 이러한 기본 사항을 기반으로 합니다.

* **대상**:초급
* **목표**:AEM GraphQL 쿼리를 사용하여 컨텐츠 조각 컨텐츠에 액세스하는 방법을 알아봅니다.
   * GraphQL 및 AEM GraphQL API를 소개합니다.
   * AEM GraphQL API에 대한 세부 정보를 참조하십시오.
   * 몇 가지 샘플 쿼리를 살펴보면서 실제로 어떻게 작동하는지 확인할 수 있습니다.

## 콘텐츠를 이용하시겠습니까?{#so-youd-like-to-access-your-content}

그래서...깔끔하게 정리된 콘텐츠(콘텐츠 조각)가 있고 새로운 앱 피드를 기다리고 있습니다. 질문은 - 어떻게 거기에 갈 수 있는가?

필요한 것은 특정 컨텐츠를 타깃팅하고 필요한 항목을 선택한 다음 앱에 반환하여 추가 처리를 수행할 수 있는 방법입니다.

AEM(Adobe Experience Manager)을 Cloud Service으로 사용하면 AEM GraphQL API를 사용하여 선택적으로 컨텐츠 조각에 액세스하여 필요한 컨텐츠만 반환할 수 있습니다. 즉, 애플리케이션에서 사용할 수 있도록 구조화된 컨텐츠를 헤드리스 없이 전달할 수 있습니다.

>[!NOTE]
>
>AEM GraphQL API는 표준 GraphQL API 사양에 따라 맞춤화된 구현입니다.

## GraphQL - 소개 {#graphql-introduction}

GraphQL은 다음을 제공하는 오픈 소스 사양입니다.

* 구조화된 오브젝트에서 특정 컨텐츠를 선택할 수 있는 쿼리 언어
* 구조화된 컨텐츠로 이러한 쿼리를 충족하는 런타임입니다.

GraphQL은 *강력하게* 입력된 API입니다. 즉, GraphQL *은(는)*&#x200B;모든&#x200B;*컨텐츠가 유형별로 명확히 구조화되고 정리되어야 GraphQL*&#x200B;이(가) 액세스해야 하는 내용과 방법을 파악할 수 있습니다. 데이터 필드는 컨텐츠 객체의 구조를 정의하는 GraphQL 스키마 내에 정의됩니다.

GraphQL 끝점은 GraphQL 쿼리에 응답하는 경로를 제공합니다.

즉, AEM과 함께 사용할 때 필요한 콘텐츠만 정확하고 안전하게 효율적으로 선택할 수 있습니다.

>[!NOTE]
>
>*GraphQL*.org 및 *GraphQL*.com을 참조하십시오.

## AEM 및 GraphQL {#aem-graphql}

GraphQL은 AEM의 다양한 위치에 사용됩니다.예를 들면 다음과 같습니다.

* 콘텐츠 조각
   * 이 사용 사례(앱에 헤드리스 게재)에 대해 사용자 지정된 API가 개발되었습니다.
      * AEM GraphQL API입니다.
* 상거래
   * AEM Commerce는 GraphQL을 통해 상거래 플랫폼의 데이터를 사용합니다.
   * AEM과 다양한 타사 상거래 솔루션 간에 GraphQL 통합이 있으며, CIF 핵심 구성 요소에서 제공하는 확장 호크에 사용됩니다.
      * AEM GraphQL API는 사용하지 않습니다.

>[!NOTE]
>
>헤드리스 여정의 이 단계는 AEM GraphQL API 및 컨텐츠 조각에만 적용됩니다.

## AEM GraphQL API {#aem-graphql-api}

AEM GraphQL API는 컨텐츠 조각에 대한 (복잡한) 쿼리를 수행할 수 있도록 특별히 구성된 표준 GraphQL API 사양을 기반으로 하는 사용자 정의된 버전입니다.

컨텐츠 조각은 컨텐츠가 컨텐츠 조각 모델에 따라 구조화되어 사용됩니다. GraphQL의 기본 요구 사항을 충족합니다.

* 컨텐츠 조각 모델은 하나 이상의 필드로 구성됩니다.
   * 각 필드는 데이터 유형에 따라 정의됩니다.
* 컨텐츠 조각 모델은 해당 AEM GraphQL 스키마를 생성하는 데 사용됩니다.

AEM(및 내용)용 GraphQL에 실제로 액세스하려면 끝점을 사용하여 액세스 경로를 제공합니다.

AEM GraphQL API를 통해 반환된 컨텐츠는 애플리케이션에서 사용할 수 있습니다.

>[!NOTE]
>
>AEM GraphQL API 구현은 GraphQL Java 라이브러리를 기반으로 합니다.

### 작성 및 게시 환경에 대한 사용 사례 {#use-cases-author-publish-environments}

AEM GraphQL API의 사용 사례는 Cloud Service 환경으로 AEM의 유형에 따라 달라질 수 있습니다.

* 게시 환경;다음 작업에 사용됩니다.
   * JS 응용 프로그램에 대한 콘텐츠 쿼리(표준 사용 사례)

* 작성 환경;다음 작업에 사용됩니다.
   * &quot;콘텐츠 관리 목적&quot;을 위해 콘텐츠 쿼리:
      * Cloud Service으로 AEM의 GraphQL은 현재 읽기 전용 API입니다.
      * REST API는 CR(u)D 작업에 사용할 수 있습니다.

## AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}에 사용할 컨텐츠 조각

컨텐츠 조각은 다음과 같이 AEM 스키마 및 쿼리에 대한 GraphQL의 기초로 사용할 수 있습니다.

* 페이지와 독립된 컨텐츠를 디자인, 제작, 조정 및 게시할 수 있습니다.
* 정의된 데이터 유형을 통해 결과 조각의 구조를 미리 정의하는 컨텐츠 조각 모델을 기반으로 합니다.
* 모델을 정의할 때 사용할 수 있는 조각 참조 데이터 유형을 사용하여 구조의 추가 레이어를 만들 수 있습니다.

### 컨텐츠 조각 모델 {#content-fragments-models}

다음 컨텐츠 조각 모델:

* 스키마를 생성하는 데 사용됩니다(**Enabled**).

* GraphQL에 필요한 데이터 유형과 필드를 제공합니다. 응용 프로그램이 가능한 것만 요청하고 예상대로 수신하도록 합니다.

* 데이터 유형 **조각 참조**&#x200B;는 모델에서 다른 컨텐츠 조각을 참조하기 위해 사용할 수 있으므로 추가 구조 수준을 활용할 수 있습니다.

### 조각 참조 {#fragment-references}

**조각 참조**:

* 컨텐츠 조각 모델을 정의할 때 사용할 수 있는 특정 데이터 유형입니다.

* 특정 컨텐츠 조각 모델에 따라 다른 조각을 참조합니다.

* 구조화된 데이터를 만들고 검색할 수 있습니다.

   * **다중 피드**&#x200B;로 정의되면 여러 하위 조각을 기본 조각의 참조(검색)할 수 있습니다.

### JSON 미리 보기 {#json-preview}

컨텐츠 조각 모델을 디자인하고 개발하는 데 도움이 되도록 컨텐츠 조각 편집기에서 JSON 출력을 미리 볼 수 있습니다.

## 컨텐츠 조각에서 GraphQL 스키마 생성 {#graphql-schema-generation-content-fragments}

GraphQL은 강력한 형식의 API로, 콘텐츠는 유형별로 명확히 구조화되고 구성되어야 합니다. GraphQL 사양에서는 특정 인스턴스에서 컨텐츠를 질문하기 위한 강력한 API를 만드는 방법에 대한 일련의 지침을 제공합니다. 이렇게 하려면 클라이언트는 쿼리에 필요한 모든 유형을 포함하는 스키마를 반입해야 합니다.

컨텐츠 조각의 경우 GraphQL 스키마(구조 및 유형)는 **Enabled** 컨텐츠 조각 모델 및 해당 데이터 유형을 기반으로 합니다.

>[!CAUTION]
>
>모든 GraphQL 스키마(**Enabled**&#x200B;인 컨텐츠 조각 모델에서 파생됨)는 GraphQL 끝점을 통해 읽을 수 있습니다.
>
>즉, 민감한 데이터가 GraphQL 끝점을 통해 노출되지 않도록 하려면 중요한 콘텐츠를 사용할 수 없도록 해야 합니다.예를 들어 모델 정의에서 필드 이름으로 존재할 수 있는 정보가 포함됩니다.

예를 들어 사용자가 `Article`이라는 컨텐츠 조각 모델을 만든 경우 AEM은 `ArticleModel` 유형의 `article` 객체를 생성합니다. 이 유형의 필드는 모델에 정의된 필드 및 데이터 유형에 해당합니다.

1. 컨텐츠 조각 모델:

   ![GraphQL에 사용할 ](assets/graphqlapi-cfmodel.png "GraphQLContent 조각 모델과 함께 사용할 컨텐츠 조각 모델")

1. 해당 GraphQL 스키마(GraphiQL 자동 설명서에서 출력):
   ![컨텐츠 조각 모델을 기반으로 하는 GraphQL ](assets/graphqlapi-cfm-schema.png "스키마 컨텐츠 조각 모델 기반 QL 스키마")

   생성된 유형 `ArticleModel`에 여러 개의 [필드](#fields)가 포함되어 있음을 보여줍니다.

   * 이 중 3개는 사용자가 제어했습니다.`author`, `main` 및 `referencearticle`.

   * 다른 필드는 AEM에 의해 자동으로 추가되었으며 특정 컨텐츠 조각에 대한 정보를 제공하는 유용한 방법을 나타냅니다.이 예에서 `_path`, `_metadata`, `_variations`입니다. 이러한 [도우미 필드](#helper-fields)는 사용자가 정의한 항목과 자동 생성된 항목을 구별하기 위해 이전 `_`으로 표시됩니다.

1. 사용자가 아티클 모델을 기반으로 컨텐츠 조각을 만든 후 GraphQL을 통해 질문할 수 있습니다. 예를 들어 GraphQL에 사용할 수 있는 샘플 컨텐츠 조각 구조를 기반으로 Sample Queries.md#graphql-sample-queries)를 참조하십시오.

AEM용 GraphQL에서 스키마는 유연합니다. 즉, 컨텐츠 조각 모델이 생성, 업데이트 또는 삭제될 때마다 매번 자동으로 생성됩니다. 컨텐츠 조각 모델을 업데이트할 때 데이터 스키마 캐시도 새로 고쳐집니다.

Sites GraphQL 서비스는 컨텐츠 조각 모델에 대한 수정 사항에 대해(백그라운드)을 수신합니다. 업데이트가 감지되면 스키마의 부분만 다시 생성됩니다. 이 최적화는 시간을 절약하고 안정성을 제공합니다.

예를 들어,

1. `Content-Fragment-Model-1` 및 `Content-Fragment-Model-2`이(가) 포함된 패키지를 설치합니다.

   1. `Model-1` 및 `Model-2`에 대한 GraphQL 유형이 생성됩니다.

1. 그런 다음 `Content-Fragment-Model-2`을(를) 수정합니다.

   1. `Model-2` GraphQL 유형만 업데이트됩니다.

   1. 반면에 `Model-1`은(는) 동일하게 유지됩니다.

>[!NOTE]
>
>REST api를 통해 컨텐츠 조각 모델에 대해 벌크 업데이트를 수행하거나, 그렇지 않을 경우 주의하는 것이 중요합니다.

스키마는 GraphQL 쿼리와 동일한 종단점을 통해 제공되며, 클라이언트는 확장명 `GQLschema`과(와) 함께 스키마를 호출한다는 사실을 처리합니다. 예를 들어 `/content/cq:graphql/global/endpoint.GQLschema`에서 간단한 `GET` 요청을 수행하면 Content-type이 있는 스키마 출력이 발생합니다.`text/x-graphql-schema;charset=iso-8859-1`.

### 스키마 생성 - 게시되지 않은 모델 {#schema-generation-unpublished-models}

컨텐츠 조각이 중첩되면 상위 컨텐츠 조각 모델이 게시되지만 참조된 모델은 게시되지 않을 수 있습니다.

>[!NOTE]
>
>AEM UI는 이러한 문제를 방지하지만 게시가 프로그래밍 방식으로 또는 콘텐츠 패키지로 이루어진 경우에는 발생할 수 있습니다.

이 경우 AEM은 상위 컨텐츠 조각 모델에 대한 *불완전한* 스키마를 생성합니다. 즉, 게시되지 않은 모델에 종속된 조각 참조가 스키마에서 제거됩니다.

## AEM GraphQL 끝점 {#aem-graphql-endpoints}

<!--
need details/examples
-->

끝점은 AEM용 GraphQL에 액세스하는 데 사용되는 경로입니다. 이 경로를 사용하여(또는 앱) 다음 작업을 수행할 수 있습니다.

* GraphQL 스키마 액세스,
* GraphQL 쿼리 보내기,
* GraphQL 쿼리에 대한 응답을 받습니다.

AEM에서 허용하는 조건:

* 전역 끝점 - 모든 사이트에서 사용할 수 있습니다.
* 테넌트 끝점 - 지정한 사이트/프로젝트에만 따라 구성할 수 있습니다.

## 권한 {#permissions}

권한은 자산에 액세스하는 데 필요한 권한입니다.

## AEM GraphiQL 인터페이스 {#aem-graphiql-interface}

AEM GraphQL에서 표준 GraphiQL 인터페이스를 구현하면 쿼리를 직접 입력하고 테스트할 수 있습니다. AEM과 함께 설치할 수 있습니다.

구문 강조, 자동 완성, 자동 제안 등의 기능과 기록 및 온라인 설명서를 함께 제공합니다.

![GraphiQL ](assets/graphiql-interface.png "인터페이스 그래픽QL 인터페이스")

## 실제로 AEM GraphQL API {#actually-using-aem-graphiql} 사용

콘텐츠에 대한 쿼리를 시작하기 전에 다음 작업을 수행해야 합니다.

* 끝점 사용
   * 도구 사용 -> 사이트 -> GraphQL

* GraphiQL 설치(필요한 경우)
   * 전용 패키지로 설치

실제로 쿼리에 AEM GraphQL API를 사용하려면 두 가지 기본 컨텐츠 조각 모델 구조를 사용할 수 있습니다.

* 회사
   * 이름
   * CEO(개인)
   * 직원(개인)
* 개인
   * 이름
   * 이름

보시다시피 CEO 및 직원 필드는 개인 조각을 참조합니다.

조각 모델이 사용됩니다.

* 컨텐츠 조각 편집기에서 컨텐츠를 작성할 때
* 쿼리할 GraphQL 스키마를 생성하려면

GraphiQL 인터페이스에서 쿼리를 입력할 수 있습니다. 예를 들면 다음과 같습니다.

* `http://localhost:4502/content/graphiql.html `

간단한 쿼리는 회사 스키마에 있는 모든 항목의 이름을 반환하는 것입니다. 여기에서 모든 회사 이름 목록을 요청합니다.

```xml
query {
  companyList {
    items {
      name
    }
  }
}
```

약간 더 복잡한 쿼리는 &quot;Job&quot;이라는 이름이 없는 모든 사람을 선택하는 것입니다. 이렇게 하면 Job이라는 이름이 없는 모든 사용자에 대해 필터링됩니다. EQUALS_NOT 연산자로 수행할 수 있습니다(더 많은 항목이 있음).

```xml
query {
  personList(filter: {
    name: {
      _expressions: [
        {
          value: "Jobs"
          _operator: EQUALS_NOT
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

보다 복잡한 쿼리를 작성할 수도 있습니다. 예를 들어 &quot;Smith&quot;라는 이름의 직원이 한 명 이상 있는 모든 회사에 대해 질의합니다. 이 쿼리는 &quot;Smith&quot;라는 이름의 모든 사용자에 대한 필터링을 보여주고 중첩된 단편에서 정보를 반환합니다.

```xml
query {
  companyList(filter: {
    employees: {
      _match: {
        name: {
          _expressions: [
            {
              value: "Smith"
            }
          ]
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
      }
    }
  }
}
```

<!-- need code / curl / cli examples-->

AEM GraphQL API 사용에 대한 자세한 내용과 필요한 요소를 구성하는 방법은 다음을 참조하십시오.

* AEM에서 GraphQL 사용 방법 학습
* 샘플 컨텐츠 조각 구조
* AEM에서 GraphQL 사용 방법 학습 - 샘플 컨텐츠 및 쿼리

## 다음 {#whats-next} 소개

이제 AEM GraphQL API를 사용하여 헤드리스 컨텐츠에 액세스하고 쿼리하는 방법을 알았으므로 [REST API를 사용하여 컨텐츠 조각](/help/implementing/developing/headless-journey/update-your-content.md)의 컨텐츠에 액세스하고 업데이트하는 방법을 배울 수 있습니다.

## 추가 리소스 {#additional-resources}

* [GraphQL.org](https://graphql.org)
   * [스키마](https://graphql.org/learn/schema/)
   * [변수](https://graphql.org/learn/queries/#variables)
   * [GraphQL Java 라이브러리](https://graphql.org/code/#java)
* [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql)
* [AEM에서 GraphQL 사용 방법 학습](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * [GraphQL 끝점 활성화](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)
   * [AEM GraphiQL 인터페이스 설치](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface)
* [샘플 컨텐츠 조각 구조](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)
* [AEM에서 GraphQL 사용 방법 학습 - 샘플 컨텐츠 및 쿼리](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [샘플 쿼리 - 단일 특정 도시 조각](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)
   * [메타데이터에 대한 샘플 쿼리 - 제목이 GB인 시상식의 메타데이터 목록](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb)
   * [샘플 쿼리 - 명명된 변화가 있는 모든 도시](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation)
* [구성 브라우저에서 컨텐츠 조각 기능 사용](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)
* [콘텐츠 조각을 사용한 작업](/help/assets/content-fragments/content-fragments.md)
   * [콘텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md)
   * [JSON 출력](/help/assets/content-fragments/content-fragments-json-preview.md)
* [CORS(Cross-Origin Resource Sharing) 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=en#understand-cross-origin-resource-sharing-(cors))
* [서버측 API에 대한 액세스 토큰 생성](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)
* [AEM 헤드리스 시작하기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html)  - 컨텐트 모델링 및 GraphQL을 비롯한 AEM 헤드리스 기능 사용에 대한 개요를 제공하는 짧은 비디오 자습서 시리즈입니다.
