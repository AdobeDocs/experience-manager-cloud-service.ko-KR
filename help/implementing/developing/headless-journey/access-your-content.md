---
title: AEM 배달 API를 통해 콘텐츠에 액세스하는 방법
description: AEM 헤드리스 개발자 여정의 이 부분에서 GraphQL 쿼리를 사용하여 콘텐츠 조각 컨텐츠에 액세스하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: 4a36cd3206784c0e4e3ed3d7007c83f44f1d5ee0
workflow-type: tm+mt
source-wordcount: '1381'
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

<!--
## AEM and GraphQL {#aem-graphql}

GraphQL is used in various locations in AEM; for example:

* Content Fragments
  * A customized API has been developed for this use-case (Headless Delivery to your app).
    * This is the AEM GraphQL API.
* Commerce
  * AEM Commerce consumes data from a Commerce platform via GraphQL.
  * There are GraphQL integrations between AEM and various third-party commerce solutions, used with the extension hooks provided by the CIF Core Components.
    * This does not use the AEM GraphQL API.

>[!NOTE]
>
>This step of the Headless Journey is only concerned with the AEM GraphQL API and Content Fragments.
-->

## AEM GraphQL API {#aem-graphql-api}

AEM GraphQL API는 컨텐츠 조각에 대한 (복잡한) 쿼리를 수행할 수 있도록 특별히 구성된 표준 GraphQL API 사양을 기반으로 하는 사용자 정의된 버전입니다.

컨텐츠 조각은 컨텐츠가 컨텐츠 조각 모델에 따라 구조화되어 사용됩니다. GraphQL의 기본 요구 사항을 충족합니다.

* 컨텐츠 조각 모델은 하나 이상의 필드로 구성됩니다.
   * 각 필드는 데이터 유형에 따라 정의됩니다.
* 컨텐츠 조각 모델은 해당 AEM GraphQL 스키마를 생성하는 데 사용됩니다.

AEM(및 내용)용 GraphQL에 실제로 액세스하려면 끝점을 사용하여 액세스 경로를 제공합니다.

AEM GraphQL API를 통해 반환된 컨텐츠는 애플리케이션에서 사용할 수 있습니다.

쿼리를 직접 입력하고 테스트할 수 있도록 AEM GraphQL과 함께 표준 GraphiQL 인터페이스 구현도 사용할 수 있습니다(AEM과 함께 설치할 수 있음). 구문 강조, 자동 완성, 자동 제안 등의 기능과 기록 및 온라인 설명서를 함께 제공합니다.

>[!NOTE]
>
>AEM GraphQL API 구현은 GraphQL Java 라이브러리를 기반으로 합니다.

<!--
### Use Cases for Author and Publish Environments {#use-cases-author-publish-environments}

The use cases for the AEM GraphQL API can depend on the type of AEM as a Cloud Service environment:

* Publish environment; used to: 
  * Query content for JS application (standard use-case)

* Author environment; used to: 
  * Query content for "content management purposes":
    * GraphQL in AEM as a Cloud Service is currently a read-only API.
    * The REST API can be used for CR(u)D operations.
-->

## AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}에 사용할 컨텐츠 조각

컨텐츠 조각은 다음과 같이 AEM 스키마 및 쿼리에 대한 GraphQL의 기초로 사용할 수 있습니다.

* 이러한 기능을 사용하면 페이지에 구애받지 않고 전달할 수 있는 컨텐츠를 디자인, 제작, 조정 및 게시할 수 있습니다.
* 이 모델은 데이터 유형 선택을 사용하여 결과 조각의 구조를 사전 정의하는 컨텐츠 조각 모델을 기반으로 합니다.
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

![JSON ](assets/cfm-model-json-preview.png "PreviewJSON 미리 보기")

<!--
## GraphQL Schema Generation from Content Fragments {#graphql-schema-generation-content-fragments}

GraphQL is a strongly typed API, which means that content must be clearly structured and organized by type. The GraphQL specification provides a series of guidelines on how to create a robust API for interrogating content on a certain instance. To do this, a client needs to fetch the Schema, which contains all the types necessary for a query. 

For Content Fragments, the GraphQL schemas (structure and types) are based on **Enabled** Content Fragment Models and their data types.

>[!CAUTION]
>
>All the GraphQL schemas (derived from Content Fragment Models that have been **Enabled**) are readable through the GraphQL endpoint.
>
>This means that you need to ensure that no sensitive content is available, to ensure that no sensitive data is exposed via GraphQL endpoints; for example, this includes information that could be present as field names in the model definition.

For example, if a user created a Content Fragment Model called `Article`, then AEM generates the object `article` that is of a type `ArticleModel`. The fields within this type correspond to the fields and data types defined in the model.

1. A Content Fragment Model:

   ![Content Fragment Model for use with GraphQL](assets/graphqlapi-cfmodel.png "Content Fragment Model for use with GraphQL")

1. The corresponding GraphQL schema (output from GraphiQL automatic documentation):
   ![GraphQL Schema based on Content Fragment Model](assets/graphqlapi-cfm-schema.png "GraphQL Schema based on Content Fragment Model")

   This shows that the generated type `ArticleModel` contains several [fields](#fields). 
   
   * Three of them have been controlled by the user: `author`, `main` and `referencearticle`.

   * The other fields were added automatically by AEM, and represent helpful methods to provide information about a certain Content Fragment; in this example, `_path`, `_metadata`, `_variations`. These [helper fields](#helper-fields) are marked with a preceding `_` to distinguish between what has been defined by the user and what has been auto-generated.

1. After a user creates a Content Fragment based on the Article model, it can then be interrogated through GraphQL. For examples, see the Sample Queries.md#graphql-sample-queries) (based on a sample Content Fragment structure for use with GraphQL.

In GraphQL for AEM, the schema is flexible. This means that it is auto-generated each and every time a Content Fragment Model is created, updated or deleted. The data schema caches are also refreshed when you update a Content Fragment Model.

The Sites GraphQL service listens (in the background) for any modifications made to a Content Fragment Model. When updates are detected, only that part of the schema is regenerated. This optimization saves time and provides stability.

So for example, if you:

1. Install a package containing `Content-Fragment-Model-1` and `Content-Fragment-Model-2`:
 
   1. GraphQL types for `Model-1` and `Model-2` will be generated.

1. Then modify `Content-Fragment-Model-2`:

   1. Only the `Model-2` GraphQL type will get updated.

   1. Whereas `Model-1` will remain the same. 

>[!NOTE]
>
>This is important to note in case you want to do bulk updates on Content Fragment Models through the REST api, or otherwise.

The schema is served through the same endpoint as the GraphQL queries, with the client handling the fact that the schema is called with the extension `GQLschema`. For example, performing a simple `GET` request on `/content/cq:graphql/global/endpoint.GQLschema` will result in the output of the schema with the Content-type: `text/x-graphql-schema;charset=iso-8859-1`.

### Schema Generation - Unpublished Models {#schema-generation-unpublished-models}

When Content Fragments are nested it can happen that a parent Content Fragment Model is published, but a referenced model is not.

>[!NOTE]
>
>The AEM UI prevents this happening, but if publishing is made programmatically, or with content packages, it can occur.

When this happens, AEM generates an *incomplete* Schema for the parent Content Fragment Model. This means that the Fragment Reference, which is dependent on the unpublished model, is removed from the schema.

## AEM GraphQL Endpoints {#aem-graphql-endpoints}

An endpoint is the path used to access GraphQL for AEM. Using this path you (or your app) can:

* access the GraphQL schemas,
* send your GraphQL queries,
* receive the responses (to your GraphQL queries).

AEM allows for:

* A global endpoint - available for use by all sites.
* Endpoints for specific Sites configurations - that you can configure (in the Configuration Browser), specific to a specified site/project.

## Permissions {#permissions}

The permissions are those required for accessing Assets.

## The AEM GraphiQL Interface {#aem-graphiql-interface}

To help you directly input, and test queries, an implementation of the standard GraphiQL interface is available for use with AEM GraphQL. This can be installed with AEM.

>[!NOTE]
>
>GraphiQL is bound the global endpoint (and does not work with other endpoints for specific Sites configurations).

It provides features such as syntax-highlighting, auto-complete, auto-suggest, together with a history and online documentation.

![GraphiQL Interface](assets/graphiql-interface.png "GraphiQL Interface")
-->

## 실제로 AEM GraphQL API {#actually-using-aem-graphiql} 사용

### 초기 설정 {#initial-setup}

콘텐츠에 대한 쿼리를 시작하기 전에 다음 작업을 수행해야 합니다.

* 끝점 사용
   * 도구 사용 -> 사이트 -> GraphQL
   * [GraphQL 끝점 활성화](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)

* GraphiQL 설치(필요한 경우)
   * 전용 패키지로 설치
   * [AEM GraphiQL 인터페이스 설치](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface)

### 샘플 구조 {#sample-structure}

실제로 쿼리에 AEM GraphQL API를 사용하려면 두 가지 기본 컨텐츠 조각 모델 구조를 사용할 수 있습니다.

* 회사
   * 이름 - 텍스트
   * CEO(개인) - 조각 참조
   * 직원(개인) - 조각 참조
* 개인
   * 이름 - 텍스트
   * 이름 - 텍스트

보시다시피 CEO 및 직원 필드는 개인 조각을 참조합니다.

조각 모델이 사용됩니다.

* 컨텐츠 조각 편집기에서 컨텐츠를 작성할 때
* 쿼리할 GraphQL 스키마를 생성하려면

### 쿼리 테스트 위치 {#where-to-test-your-queries}

GraphiQL 인터페이스에서 쿼리를 입력할 수 있습니다. 예를 들면 다음과 같습니다.

* `http://localhost:4502/content/graphiql.html `

![GraphiQL ](assets/graphiql-interface.png "인터페이스 그래픽QL 인터페이스")

### 쿼리 시작 {#getting-Started-with-queries}

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
