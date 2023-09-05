---
title: 콘텐츠 조각과 함께 사용하기 위한 AEM GraphQL API
description: AEM GraphQL API와 함께 Adobe Experience Manager(AEM) as a Cloud Service에서 Headless 콘텐츠 게재를 위해 콘텐츠 조각을 사용하는 방법을 알아봅니다.
feature: Content Fragments,GraphQL API
exl-id: bdd60e7b-4ab9-4aa5-add9-01c1847f37f6
source-git-commit: f58581f6f81e60edafd79dd1d305bd479b65eed5
workflow-type: tm+mt
source-wordcount: '4922'
ht-degree: 100%

---


# 콘텐츠 조각과 함께 사용하기 위한 AEM GraphQL API {#graphql-api-for-use-with-content-fragments}

AEM GraphQL API와 함께 Adobe Experience Manager(AEM) as a Cloud Service에서 Headless 콘텐츠 게재를 위해 콘텐츠 조각을 사용하는 방법을 알아봅니다.

Content Fragments와 함께 사용되는 AEM as a Cloud Service GraphQL API는 표준 오픈 소스 GraphQL API를 기반으로 합니다.

AEM에서 GraphQL API를 사용하면 Headless CMS 구현에서 JavaScript 클라이언트에 콘텐츠 조각을 효율적으로 게재할 수 있습니다.

* REST에서처럼 반복적인 API 요청 방지,
* 게재가 특정 요구 사항으로 제한되는지 확인,
* 단일 API 쿼리에 대한 응답으로 렌더링에 필요한 것을 정확히 대량으로 게재할 수 있도록 허용.

>[!NOTE]
>
>GraphQL은 현재 Adobe Experience Manager(AEM) as a Cloud Service의 두 가지 (별도) 시나리오에서 사용됩니다.
>
>* [AEM Commerce는 GraphQL을 통해 상거래 플랫폼의 데이터를 사용합니다](/help/commerce-cloud/integrating/magento.md).
>* AEM 콘텐츠 조각은 AEM GraphQL API(표준 GraphQL 기반의 맞춤화된 구현)와 함께 작동하여 애플리케이션에서 사용할 구조화된 콘텐츠를 제공합니다.

## GraphQL API {#graphql-api}

GraphQL은

* “*...API용 쿼리 언어 및 기존 데이터로 이러한 쿼리를 수행하기 위한 런타임입니다. GraphQL은 API의 데이터에 대한 완전하고 이해하기 쉬운 설명을 제공하고, 클라이언트가 필요로 하는 것을 정확히 요청할 수 있는 권한을 주고, 시간이 지남에 따라 API를 더 쉽게 발전시킬 수 있으며, 강력한 개발자 도구를 지원합니다.*”.

  [GraphQL.org](https://graphql.org)를 참조하십시오.

* “*...유연한 API 계층을 위한 오픈 사양입니다. 기존 백엔드에 GraphQL을 추가하여 그 어느 때보다 빠르게 제품을 빌드할 수 있습니다.*”

  [GraphQL 살펴보기](https://www.graphql.com)를 참조하십시오.

* *“...2015년에 오픈 소스로 공개되기 전에 2012년 Facebook에서 내부적으로 개발한 데이터 쿼리 언어 및 사양입니다. 개발자 생산성을 높이고 전송되는 데이터 양을 최소화할 목적으로 REST 기반 아키텍처에 대한 대안을 제공합니다. GraphQL은 규모에 관계없이 수백 개의 조직에서 프로덕션에 사용됩니다.”*

  [GraphQL Foundation](https://foundation.graphql.org/)을 참조하십시오.

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world all of the tools they need to understand and adopt GraphQL.*". 
-->

GraphQL API에 대한 정보는 기타 여러 리소스 중에서도 특히 다음 섹션을 참조하십시오.

* [graphql.org](https://graphql.org):

   * [GraphQL 소개](https://graphql.org/learn)

   * [GraphQL 사양](https://spec.graphql.org/)

* [graphql.com](https://graphql.com):

   * [안내서](https://www.graphql.com/guides/)

   * [튜토리얼](https://www.graphql.com/tutorials/)

   * [사례 연구](https://www.graphql.com/case-studies/)

AEM용 GraphQL 구현은 표준 GraphQL Java 라이브러리를 기반으로 합니다. 다음을 참조하십시오.

* [graphQL.org - Java](https://graphql.org/code/#java)

* [GitHub의 GraphQL Java](https://github.com/graphql-java)

### GraphQL 용어 {#graphql-terminology}

GraphQL은 다음 용어를 사용합니다.

* **[쿼리](https://graphql.org/learn/queries/)**

* **[스키마 및 유형](https://graphql.org/learn/schema/)**:

   * 스키마는 콘텐츠 조각 모델을 기반으로 AEM에서 생성됩니다.
   * 스키마를 사용하여 GraphQL은 AEM용 GraphQL 구현에 허용되는 유형 및 작업을 제공합니다.

* **[필드](https://graphql.org/learn/queries/#fields)**

* **[GraphQL 엔드포인트](graphql-endpoint.md)**
   * GraphQL 쿼리에 응답하고 GraphQL 스키마에 대한 액세스를 제공하는 AEM의 경로입니다.

   * 자세한 내용은 [GraphQL 엔드포인트 활성화](graphql-endpoint.md)를 참조하십시오.

[모범 사례](https://graphql.org/learn/best-practices/)를 포함한 포괄적인 세부 정보는 [(GraphQL.org) GraphQL 소개](https://graphql.org/learn/)를 참조하십시오.

### GraphQL 쿼리 유형 {#graphql-query-types}

GraphQL을 사용하여 다음 중 하나를 반환하는 쿼리를 수행할 수 있습니다.

* **단일 항목**

* **[항목 목록](https://graphql.org/learn/schema/#lists-and-non-null)**

AEM은 쿼리(두 유형 모두)를 Dispatcher 및 CDN에서 [캐시할 수 있는 지속 쿼리](/help/headless/graphql-api/persisted-queries.md)로 변환하는 기능을 제공합니다.

### GraphQL 쿼리 모범 사례(Dispatcher 및 CDN) {#graphql-query-best-practices}

[지속 쿼리](/help/headless/graphql-api/persisted-queries.md)는 게시 인스턴스에서 다음과 같이 사용하도록 권장되는 방법입니다.

* 캐시됩니다.
* AEM as a Cloud Service을 통해 중앙 집중식으로 관리됩니다.

>[!NOTE]
>
>일반적으로 작성자에게는 Dispatcher/CDN이 없으므로 지속 쿼리를 사용하는 것은 이를 테스트할 수 있다는 것 외에 아무런 이점이 없습니다.

POST 요청을 사용하는 GraphQL 쿼리는 캐시되지 않으므로 권장되지 않습니다. 따라서 기본 인스턴스에서는 Dispatcher가 이러한 쿼리를 차단하도록 구성됩니다.

GraphQL은 GET 요청도 지원하지만 이러한 요청은 지속 쿼리를 사용하면 피할 수 있는 제한(예: URL 길이)에 도달할 수 있습니다.

자세한 내용은 [지속 쿼리 캐싱 활성화](/help/headless/deployment/dispatcher-caching.md)를 참조하십시오.

>[!NOTE]
>
>Dispatcher에서 직접 및/또는 POST 쿼리를 허용하려면 시스템 관리자에게 다음 작업을 요청할 수 있습니다.
>
>* `ENABLE_GRAPHQL_ENDPOINT`라는 [Cloud Manager 환경 변수](/help/implementing/cloud-manager/environment-variables.md) 생성
>* (`true` 값 포함)

>[!NOTE]
>
>직접 쿼리를 수행하는 기능은 향후의 어느 시점에서 더 이상 사용되지 않을 수 있습니다.

### GraphiQL IDE {#graphiql-ide}

[GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md)를 사용하여 GraphQL 쿼리를 테스트하고 디버그할 수 있습니다.

## 작성, 미리보기 및 게시의 사용 사례 {#use-cases-author-preview-publish}

사용 사례는 AEM as a Cloud Service 환경 유형에 따라 달라질 수 있습니다.

* 게시 환경, 다음과 같은 작업을 수행하는 데 사용됨:
   * JS 애플리케이션용 쿼리 데이터 (표준 사용 사례)

* 미리보기 환경, 다음과 같은 작업을 수행하는 데 사용됨:
   * 게시 환경에 배포하기 전 미리보기 쿼리
      * JS 애플리케이션용 쿼리 데이터 (표준 사용 사례)

* Author 환경, 다음과 같은 작업을 수행하는 데 사용됨:
   * “콘텐츠 관리 목적”용 쿼리 데이터:
      * AEM as a Cloud Service의 GraphQL은 현재 읽기 전용 API입니다.
      * REST API는 CR(u)D 작업에 사용할 수 있습니다.

## 권한 {#permission}

권한은 Assets에 액세스하는 데 필요한 권한입니다.

GraphQL 쿼리는 기본 요청의 AEM 사용자 권한으로 실행됩니다. 사용자에게 일부 조각(자산으로 저장됨)에 대한 읽기 액세스 권한이 없는 경우 이들 조각은 결과 세트의 일부가 되지 않습니다.

또한 GraphQL 쿼리를 실행할 수 있으려면 사용자가 GraphQL 엔드포인트에 대한 액세스 권한을 보유해야 합니다.

## 스키마 생성 {#schema-generation}

GraphQL은 강력한 포맷의 API입니다. 즉, 데이터는 유형별로 명확하게 구조화되고 구성되어야 합니다.

GraphQL 사양은 특정 인스턴스에서 데이터의 정보를 얻기 위해 강력한 API를 만드는 방법에 대한 일련의 지침을 제공합니다. 이렇게 하려면 클라이언트가 쿼리에 필요한 모든 유형을 포함하는 [스키마](#schema-generation)를 가져와야 합니다.

콘텐츠 조각의 경우 GraphQL 스키마(구조 및 유형)는 **활성화됨** 상태인 [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) 및 해당 데이터 형식을 기반으로 합니다.

>[!CAUTION]
>
>모든 GraphQL 스키마(**활성화됨**&#x200B;상태인 콘텐츠 조각 모델에서 파생)는 GraphQL 엔드포인트를 통해 읽을 수 있습니다.
>
>즉, 이런 식으로 유출될 수 있기 때문에 민감한 데이터가 없는지 확인해야 합니다. 예를 들어 모델 정의에서 필드 이름으로 나타날 수 있는 정보가 여기에 포함됩니다.

예를 들어 사용자가 `Article`이라는 콘텐츠 조각 모델을 만든 경우 AEM은 `ArticleModel`이라는 GraphQL 유형을 생성합니다. 이 유형 내의 필드는 모델에서 정의된 필드 및 데이터 유형에 해당합니다. 또한 `articleByPath` 또는 `articleList`와 같이 이 유형에서 작동하는 쿼리에 대한 일부 진입점을 생성합니다.

1. 콘텐츠 조각 모델:

   ![GraphQL과 함께 사용하기 위한 콘텐츠 조각 모델](assets/cfm-graphqlapi-01.png "GraphQL과 함께 사용하기 위한 콘텐츠 조각 모델")

1. 해당 GraphQL 스키마(GraphiQL 자동 문서에서 출력):
   ![콘텐츠 조각 모델 기반 GraphQL 스키마](assets/cfm-graphqlapi-02.png "콘텐츠 조각 모델 기반 GraphQL 스키마")

   이는 생성된 유형 `ArticleModel`에 여러 [필드](#fields)가 포함되어 있음을 보여 줍니다.

   * 그 중 `author`, `main`, `referencearticle` 세 가지 필드는 사용자가 제어했습니다.

   * 다른 필드는 AEM에 의해 자동으로 추가되었으며 특정 콘텐츠 조각에 대한 정보를 제공하는 유용한 방법을 표시합니다. 이 예([도우미 필드](#helper-fields))에서는 `_path`, `_metadata`, `_variations`입니다.

1. 사용자가 Article 모델을 기반으로 콘텐츠 조각을 만든 경우 GraphQL을 통해 정보를 얻을 수 있습니다. 예를 들어 [샘플 쿼리](/help/headless/graphql-api/sample-queries.md#graphql-sample-queries)([GraphQL과 함께 사용하기 위한 샘플 콘텐츠 조각 구조](/help/headless/graphql-api/sample-queries.md#content-fragment-structure-graphql) 기반)를 참조하십시오.

AEM용 GraphQL에서 스키마는 유연합니다. 즉, 콘텐츠 조각 모델이 만들어지거나 업데이트되거나 삭제될 때마다 자동 생성됩니다. 콘텐츠 조각 모델을 업데이트할 때도 데이터 스키마 캐시가 새로 고쳐집니다.

<!-- move the following to a separate "in depth" page -->

콘텐츠 조각 모델을 업데이트할 때도 데이터 스키마 캐시가 새로 고쳐집니다.

Sites GraphQL 서비스는 콘텐츠 조각 모델에 대한 수정 사항을 배경에서 수신 대기합니다. 업데이트가 감지되면 스키마의 해당 부분만 다시 생성됩니다. 이 최적화는 시간을 절약하고 안정성을 제공합니다.

예를 들어:

1. `Content-Fragment-Model-1` 및 `Content-Fragment-Model-2`가 포함된 패키지를 설치하는 경우:

   1. `Model-1` 및 `Model-2`에 대한 GraphQL 유형이 생성됩니다.

1. 그리고 `Content-Fragment-Model-2`를 수정하는 경우:

   1. `Model-2` GraphQL 유형만 업데이트됩니다.

   1. `Model-1`은 그대로 유지됩니다.

>[!NOTE]
>
>REST API 또는 다른 방법을 통해 콘텐츠 조각 모델에 대한 대량 업데이트를 수행하려는 경우에 주의해야 합니다.

스키마는 GraphQL 쿼리와 동일한 엔드포인트를 통해 제공되며 스키마가 확장자 `GQLschema`로 호출되는 것을 처리하는 클라이언트가 있습니다. 예를 들어 `/content/cq:graphql/global/endpoint.GQLschema`에 대해 간단한 `GET` 요청을 수행하면 콘텐츠 유형이 있는 스키마의 출력이 됩니다. `text/x-graphql-schema;charset=iso-8859-1`.

<!-- move through to here to a separate "in depth" page -->

### 스키마 생성 - 게시되지 않은 모델 {#schema-generation-unpublished-models}

콘텐츠 조각이 중첩되면 상위 콘텐츠 조각 모델은 게시되지만 참조된 모델은 게시되지 않을 수 있습니다.

>[!NOTE]
>
>AEM UI는 이러한 일이 발생하지 않도록 방지하지만 게시가 프로그래밍 방식으로 또는 콘텐츠 패키지를 사용하여 수행되는 경우 발생할 수 있습니다.

이런 일이 발생하면 AEM은 상위 콘텐츠 조각 모델에 대해 *불완전* 스키마를 생성합니다. 즉, 게시되지 않은 모델에 종속된 조각 참조가 스키마에서 제거됩니다.

## 필드 {#fields}

스키마 내에는 다음과 같은 두 가지 기본 범주의 개별 필드가 있습니다.

* 귀하가 생성하는 필드입니다.

  다양한 [데이터 유형](#Data-types)은 콘텐츠 조각 모델을 구성하는 방법을 기반으로 필드를 만드는 데 사용됩니다. 필드 이름은 **데이터 유형** 탭의 **속성 이름** 필드에서 가져옵니다.

   * 사용자가 특정 데이터 유형을 구성할 때 고려해야 하는 **렌더링 형식** 설정도 있습니다. 예를 들어 드롭다운에서 `multifield`를 선택하여 여러 개의 한 줄 텍스트를 포함하도록 한 줄 텍스트 필드를 구성할 수 있습니다.

* AEM용 GraphQL은 또한 여러 [도우미 필드](#helper-fields)를 생성합니다.

### 데이터 유형 {#data-types}

AEM용 GraphQL은 유형 목록을 지원합니다. 지원되는 모든 콘텐츠 조각 모델 데이터 형식 및 해당 GraphQL 유형이 표시됩니다.

| 콘텐츠 조각 모델 - 데이터 형식 | GraphQL 유형 | 설명 |
|--- |--- |--- |
| 한 줄 텍스트 | `String`, `[String]` | 작성자 이름, 위치 이름 등과 같은 간단한 문자열에 사용됨 |
| 여러 줄 텍스트 | `String`, `[String]` | 기사의 본문과 같은 텍스트 출력에 사용됨 |
| 숫자 | `Float`, `[Float]` | 부동 소수점 숫자 및 일반 숫자를 표시하는 데 사용됨 |
| 부울 | `Boolean` | 확인란을 표시하는 데 사용됨 → 간단한 참/거짓 진술 |
| 날짜 및 시간 | `Calendar` | ISO 8601 형식으로 날짜와 시간을 표시하는 데 사용됨. 선택한 유형에 따라 AEM GraphQL에서 세 가지 버전(`onlyDate`, `onlyTime`, `dateTime`)을 사용할 수 있습니다. |
| 열거 | `String` | 모델 생성 시 정의된 옵션 목록에서 옵션을 표시하는 데 사용됨 |
| 태그 | `[String]` | AEM에서 사용되는 태그를 나타내는 문자열 목록을 표시하는 데 사용됨 |
| 콘텐츠 참조 | `String`, `[String]` | AEM에서 다른 자산에 대한 경로를 표시하는 데 사용됨 |
| 조각 참조 |  *모델 유형* <br><br>단일 필드:`Model` - 모델 유형, 직접 참조 <br><br> 하나의 참조 유형이 있는 다중 필드:`[Model]` - 유형의 배열`Model`, 배열에서 직접 참조됨 <br><br> 다중 참조 유형이 있는 다중 필드:`[AllFragmentModels]` - 공용 유형의 배열에서 참조되는 모든 모델 유형의 배열 |  모델이 생성될 때 정의된 특정 모델 유형의 다른 콘텐츠 조각을 하나 이상 참조하는 데 사용됨 |

{style="table-layout:auto"}

### 도우미 필드 {#helper-fields}

사용자 생성 필드의 데이터 형식 외에도 AEM용 GraphQL은 콘텐츠 조각 식별을 돕거나 콘텐츠 조각에 대한 추가 정보를 제공하기 위해 여러 *도우미* 필드를 생성합니다.

이 [도우미 필드](#helper-fields)는 사용자가 정의한 것과 자동 생성된 것을 구별하기 위해 앞에 `_`로 표시됩니다.

#### 경로 {#path}

경로 필드는 AEM GraphQL에서 식별자로 사용됩니다. AEM 저장소 내 콘텐츠 조각 자산의 경로를 나타냅니다. 다음과 같은 이유로 콘텐츠 조각의 식별자로 선택되었습니다.

* AEM 내에서 고유합니다.
* 쉽게 가져올 수 있습니다.

다음 코드는 WKND 튜토리얼에서 제공된 대로 콘텐츠 조각 모델 `Author`를 기반으로 생성된 모든 콘텐츠 조각의 경로를 표시합니다.

```graphql
{
  authorList {
    items {
      _path
    }
  }
}
```

특정 유형의 단일 콘텐츠 조각을 검색하려면 먼저 해당 경로도 결정해야 합니다. 예:

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/sofia-sj-berg") {
    item {
      _path
      firstName
      lastName
    }
  }
}
```

[샘플 쿼리 - 단일 특정 도시 조각](/help/headless/graphql-api/sample-queries.md#sample-single-specific-city-fragment)을 참조하십시오.

#### 메타데이터 {#metadata}

AEM은 또한 GraphQL을 통해 콘텐츠 조각의 메타데이터를 노출합니다. 메타데이터는 콘텐츠 조각을 설명하는 정보이며, 콘텐츠 조각의 제목, 썸네일 경로, 콘텐츠 조각에 대한 설명, 생성일 등이 있습니다.

메타데이터는 스키마 편집기를 통해 생성되기 때문에 특정한 구조를 가지고 있지 않으므로 콘텐츠 조각의 메타데이터를 노출하기 위해 `TypedMetaData` GraphQL 유형이 구현되었습니다. `TypedMetaData`은 다음 스칼라 유형으로 그룹화된 정보를 노출합니다.

| 필드 |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!` |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

각 스칼라 유형은 단일 이름-값 쌍 또는 이름-값 쌍의 배열을 표시하며, 여기서 해당 쌍의 값은 그룹화된 유형입니다.

예를 들어 콘텐츠 조각의 제목을 검색하려는 경우 이 속성이 문자열 속성이라는 것을 알고 있으므로 모든 문자열 메타데이터를 쿼리합니다.

메타데이터를 쿼리하려면:

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/sofia-sj-berg") {
    item {
      _metadata {
        stringMetadata {
          name
          value
        }
      }
    }
  }
}
```

생성된 GraphQL 스키마를 보면 모든 메타데이터 GraphQL 유형을 볼 수 있습니다. 모든 모델 유형에는 동일한 `TypedMetaData`가 있습니다.

>[!NOTE]
>
>**일반 메타데이터와 배열 메타데이터의 차이점**
>`StringMetadata` 및 `StringArrayMetadata`는 둘 다 검색 방법을 참조하는 것이 아니라 저장소에 저장된 내용을 참조합니다.
>
>따라서 예를 들어 `stringMetadata` 필드를 호출하면 저장소에 `String`으로 저장된 모든 메타데이터의 배열을 수신하고 `stringArrayMetadata`를 호출하면 저장소에 `String[]`으로 저장된 모든 메타데이터의 배열을 수신하게 됩니다.

[메타데이터에 대한 샘플 쿼리 - GB라는 제목의 상에 대한 메타데이터 나열](/help/headless/graphql-api/sample-queries.md#sample-metadata-awards-gb)을 참조하십시오.

#### 변형 {#variations}

`_variations` 필드는 콘텐츠 조각에 있는 변형 쿼리를 단순화하기 위해 구현되었습니다. 예:

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/ian-provo") {
    item {
      _variations
    }
  }
}
```

>[!NOTE]
>
>원본 데이터(UI에서 *마스터*&#x200B;로 참조됨)는 명시적 변형으로 간주되지 않으므로 `_variations` 필드에는 `master` 변형이 포함되어 있지 않습니다.

[샘플 쿼리 - 이름이 붙은 변형이 있는 모든 도시](/help/headless/graphql-api/sample-queries.md#sample-cities-named-variation)를 참조하십시오.

>[!NOTE]
>
>콘텐츠 조각에 대한 지정된 변형이 존재하지 않는 경우, 원본 데이터(마스터 변형이라고도 함)은 (대체) 기본값으로 반환됩니다.

<!--
## Security Considerations {#security-considerations}
-->

## GraphQL 변수 {#graphql-variables}

GraphQL을 사용하면 쿼리에 변수를 배치할 수 있습니다. 보다 자세한 정보는 [변수에 대한 GraphQL 설명서](https://graphql.org/learn/queries/#variables)를 참조하십시오.

예를 들어 특정 변형에 있는 `Author` 유형의 모든 콘텐츠 조각을 가져오려면(가능한 경우) GraphiQL에서 `variation` 인수를 지정할 수 있습니다.

![GraphQL 변수](assets/cfm-graphqlapi-03.png "GraphQL 변수")

**쿼리**:

```graphql
query($variation: String!) {
  authorList(variation: $variation) {
    items {
      _variation
      lastName
      firstName
    }
  }
}
```

**쿼리 변수**:

```json
{
  "variation": "another"
}
```

이 쿼리는 작성자의 전체 목록을 반환합니다. `another` 변형이 없는 작성자는 원본 데이터로 대체됩니다(이 경우 `_variation`은 `master`를 보고함).

지정된 변형을 제공하는 작성자로 목록을 제한하고 원본 데이터로 대체되는 작성자를 건너뛰려면 [필터](#filtering)를 적용합니다.

```graphql
query($variation: String!) {
  authorList(variation: $variation, filter: {
    _variation: {
      _expressions: {
        value: $variation
      }
    }
  }) {
    items {
      _variation
      lastName
      firstName
    }
  }
}
```

## GraphQL 지시문 {#graphql-directives}

GraphQL에서는 GraphQL 지시문이라고 하는 변수를 기반으로 쿼리를 변경할 수 있습니다.

예를 들어 `includePrice` 변수를 기반으로 모든 `AdventureModels`에 대한 쿼리에 `adventurePrice` 필드를 포함할 수 있습니다.

![GraphQL 지시문](assets/cfm-graphqlapi-04.png "GraphQL 지시문")

**쿼리**:

```graphql
query GetAdventureByType($includePrice: Boolean!) {
  adventureList {
    items {
      title
      price @include(if: $includePrice)
    }
  }
}
```

**쿼리 변수**:

```json
{
    "includePrice": true
}
```

## 필터링 {#filtering}

GraphQL 쿼리에서 필터링을 사용하여 특정 데이터를 반환할 수도 있습니다.

필터링은 논리 연산자 및 표현식을 기반으로 하는 구문을 사용합니다.

가장 세밀한 부분은 특정 필드의 내용에 적용할 수 있는 단일 표현식입니다. 필드의 내용을 주어진 상수 값과 비교합니다.

예를 들어 표현식은

```graphql
{
  value: "some text"
  _op: EQUALS
}
```

필드의 내용을 `some text` 값과 비교하고 내용이 값과 동일하면 성공한 것입니다. 그렇지 않으면 해당 표현식은 실패한 것입니다.

연산자를 사용하여 필드를 특정 값과 비교할 수 있습니다.

| 연산자 | 유형 | 다음은 표현식이 성공하는 경우입니다. |
|--- |--- |--- |
| `EQUALS` | `String`, `ID`, `Boolean` | ... 값이 필드의 내용과 정확히 동일한 경우 |
| `EQUALS_NOT` | `String`, `ID` | ... 값이 필드의 내용과 정확히 동일하지 *않는* 경우 |
| `CONTAINS` | `String` | ... 필드의 내용에 값이 포함되는 경우 (`{ value: "mas", _op: CONTAINS }`는 `Christmas`, `Xmas`, `master`, ...와 일치함) |
| `CONTAINS_NOT` | `String` | ... 필드의 내용에 값이 포함되지 *않는* 경우 |
| `STARTS_WITH` | `ID` | ... ID가 특정 값으로 시작하는 경우 (`{ value: "/content/dam/", _op: STARTS_WITH`는 `/content/dam/path/to/fragment`와 일치하지만 `/namespace/content/dam/something`과는 일치하지 않음 |
| `EQUAL` | `Int`, `Float` | ... 값이 필드의 내용과 정확히 동일한 경우 |
| `UNEQUAL` | `Int`, `Float` | ... 값이 필드의 내용과 정확히 동일하지 *않는* 경우 |
| `GREATER` | `Int`, `Float` | ... 필드의 내용이 값보다 큰 경우 |
| `GREATER_EQUAL` | `Int`, `Float` | ... 필드의 내용이 값보다 크거나 같은 경우 |
| `LOWER` | `Int`, `Float` | ... 필드의 내용이 값보다 작은 경우 |
| `LOWER_EQUAL` | `Int`, `Float` | ... 필드의 내용이 값보다 작거나 같은 경우 |
| `AT` | `Calendar`, `Date`, `Time` | ... 필드의 내용이 값과 정확히 동일한 경우 (시간대 설정 포함) |
| `NOT_AT` | `Calendar`, `Date`, `Time` | ... 필드의 내용이 값과 정확히 동일하지 *않는* 경우 |
| `BEFORE` | `Calendar`, `Date`, `Time` | ... 값으로 표시되는 시점이 필드의 내용으로 표시되는 시점 이전인 경우 |
| `AT_OR_BEFORE` | `Calendar`, `Date`, `Time` | ... 값으로 표시되는 시점이 필드의 내용으로 표시되는 시점 이전이거나 동일한 경우 |
| `AFTER` | `Calendar`, `Date`, `Time` | ... 값으로 표시되는 시점이 필드의 내용으로 표시되는 시점 이후인 경우 |
| `AT_OR_AFTER` | `Calendar`, `Date`, `Time` | ... 값으로 표시되는 시점이 필드의 내용으로 표시되는 시점 이후거나 동일한 경우 |

일부 유형을 사용하면 표현식 평가 방법을 수정하는 추가 옵션을 지정할 수도 있습니다.

| 옵션 | 유형 | 설명 |
|--- |--- |--- |
| `_ignoreCase` | `String` | 문자열의 대소문자를 무시합니다(예: `time` 값은 `TIME`, `time`, `tImE`, ...과 일치함) |
| `_sensitiveness` | `Float` | `float` 값의 내부 표현으로 인한 기술적 제한을 해결하기 위해 `float` 값의 특정 여백이 동일하게 간주되도록 합니다. 이 옵션을 사용하면 성능에 부정적인 영향을 미칠 수 있으므로 피해야 합니다. |

표현식은 논리 연산자(`_logOp`)를 사용하여 세트로 결합할 수 있습니다.

* `OR` - 하나 이상의 표현식이 성공하면 표현식 세트가 성공합니다.
* `AND` - 모든 표현식이 성공하면 표현식 세트가 성공합니다(기본값).

각 필드는 자체 표현식 세트로 필터링할 수 있습니다. 필터 인수에 언급된 모든 필드의 표현식 세트는 최종적으로 자체 논리 연산자에 의해 결합됩니다.

필터 정의(쿼리에 `filter` 인수로 전달됨)에는 다음이 포함됩니다.

* 각 필드에 대한 하위 정의이며, 필드는 해당 이름을 통해 액세스할 수 있습니다. 예를 들어 데이터(필드) 유형의 `lastName` 필드에 대한 필터에는 `lastName` 필드가 있습니다.
* 각 하위 정의에는 표현식 세트를 제공하는 `_expressions` 배열과 표현식을 결합해야 하는 논리 연산자를 정의하는 `_logOp` 필드가 포함됩니다.
* 각 표현식은 필드의 내용과 비교해야 하는 값(`value` 필드)과 연산자(`_operator` 필드)로 정의됩니다.

항목을 `AND`와 결합하고자 하는 경우 `_logOp`를 생략할 수 있으며 동일한지 확인하고자 하는 경우 기본값인 `_operator`를 생략할 수 있습니다.

다음 예는 `Provo`의 `lastName` 또는 `sjö`를 포함하는 모든 사람을 대소문자에 관계없이 필터링하는 전체 쿼리를 보여 줍니다.

```graphql
{
  authorList(filter: {
    lastname: {
      _logOp: OR
      _expressions: [
        {
          value: "sjö",
          _operator: CONTAINS,
          _ignoreCase: true
        },
        {
          value: "Provo"
        }
      ]
    }
  }) {
    items {
      lastName
      firstName
    }
  }
}
```

중첩된 필드를 필터링할 수도 있지만 성능 문제가 발생할 수 있으므로 권장되지 않습니다.

더 많은 예는 다음을 참조하십시오.

* [AEM용 GraphQL 확장](#graphql-extensions)의 세부사항

* [이 샘플 콘텐츠 및 구조를 사용하는 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#graphql-sample-queries-sample-content-fragment-structure)

   * 그리고 샘플 쿼리에 사용하기 위해 준비된 [샘플 콘텐츠 및 구조](/help/headless/graphql-api/sample-queries.md#content-fragment-structure-graphql)

* [WKND 프로젝트 기반 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-queries-using-wknd-project)

## 정렬 {#sorting}

>[!NOTE]
>
>최고의 성능을 위해 [GraphQL 필터링 시 페이징 및 정렬을 위한 콘텐츠 조각 업데이트](/help/headless/graphql-api/graphql-optimized-filtering-content-update.md)를 고려하십시오.

이 기능을 사용하면 지정된 필드에 따라 쿼리 결과를 정렬할 수 있습니다.

다음은 정렬 기준에 대한 설명입니다.

* 필드 경로를 나타내는 쉼표로 구분된 값 목록입니다.
   * 목록의 첫 번째 필드는 기본 정렬 순서를 정의하고, 두 번째 필드는 기본 정렬 기준의 두 값이 동일한 경우 사용되며, 세 번째 필드는 처음 두 기준이 동일한 경우 사용됩니다.
   * 점으로 구분된 표기법 (예: field1.subfield.subfield 등)
* 선택적 정렬 방향
   * (ASC(오름차순) 또는 DESC(내림차순))이 포함되며, 기본값 ASC가 적용됩니다.
   * 방향은 필드별로 지정할 수 있습니다. 즉, 한 필드는 오름차순으로 정렬하고 다른 필드는 내림차순으로 정렬할 수 있습니다(name, firstName DESC).

예:

```graphql
query {
  authorList(sort: "lastName, firstName") {
    items {
      firstName
      lastName
    }
  }
}
```

또한

```graphql
{
  authorList(sort: "lastName DESC, firstName DESC") {
    items {
        lastName
        firstName
    }
  }
}
```

`nestedFragmentname.fieldname` 형식을 사용하여 중첩된 조각 내의 필드를 정렬할 수도 있습니다.

>[!NOTE]
>
>이렇게 하면 성능에 부정적인 영향을 미칠 수 있습니다.

예:

```graphql
query {
  articleList(sort: "authorFragment.lastName")  {
    items {
      title
      authorFragment {
        firstName
        lastName
        birthDay
      }
      slug
    }
  }
}
```

## 페이징 {#paging}

>[!NOTE]
>
>최고의 성능을 위해 [GraphQL 필터링 시 페이징 및 정렬을 위한 콘텐츠 조각 업데이트](/help/headless/graphql-api/graphql-optimized-filtering-content-update.md)를 고려하십시오.

이 기능을 사용하면 목록을 반환하는 쿼리 유형에 대해 페이징을 수행할 수 있습니다. 제공되는 메서드는 두 가지가 있습니다.

* `List` 쿼리의 `offset` 및 `limit`
* `Paginated` 쿼리의 `first` 및 `after`

### 목록 쿼리 - 오프셋 및 제한 {#list-offset-limit}

`...List`쿼리에서 `offset` 및 `limit`을 사용하여 결과의 특정 하위 집합을 반환할 수 있습니다.

* `offset`: 반환할 첫 번째 데이터 세트를 지정합니다.
* `limit`: 반환할 최대 데이터 세트 수를 지정합니다.

예를 들어 *전체* 결과 목록의 다섯 번째 문서부터 시작하여 최대 5개의 문서를 포함하는 결과 페이지를 출력하는 경우

```graphql
query {
   articleList(offset: 5, limit: 5) {
    items {
      authorFragment {
        lastName
        firstName
      }
    }
  }
}
```

<!-- When available link to BP and replace "JCR query level" with a more neutral term. -->

<!-- When available link to BP and replace "JCR query result set" with a more neutral term. -->

>[!NOTE]
>
>* 페이징이 동일한 결과 세트의 서로 다른 페이지를 요청하는 여러 쿼리에서 올바르게 작동하도록 하려면 안정적인 정렬 순서가 필요합니다. 페이징은 기본적으로 결과 세트의 각 항목에 대한 저장소 경로를 사용하여 순서가 항상 동일하도록 합니다. 다른 정렬 순서를 사용하고 해당 정렬을 JCR 쿼리 수준에서 수행할 수 없는 경우, 페이지를 결정하기 전에 전체 결과 세트를 메모리에 로드해야 하므로 성능에 부정적인 영향이 발생합니다.
>
>* 오프셋이 높을수록 전체 JCR 쿼리 결과 세트에서 항목을 건너뛰는 데 더 많은 시간이 소요됩니다. 대용량 결과 세트에 대한 대체 솔루션은 페이지가 매겨진 쿼리를 `first` 및 `after` 메서드와 함께 사용하는 것입니다.

### 페이지 매김된 쿼리 - 첫 번째 및 그 다음 페이지 {#paginated-first-after}

`...Paginated` 쿼리 유형은 대부분의 `...List` 쿼리 유형 기능(필터링, 정렬)을 재사용하지만, `offset`/`limit` 인수를 사용하는 대신 [GraphQL 커서 연결 사양](https://relay.dev/graphql/connections.htm)에 정의된 대로 `first`/`after` 인수를 사용합니다. [GraphQL 소개](https://graphql.org/learn/pagination/#pagination-and-edges)에서 좀 더 친숙한 느낌의 소개를 찾을 수 있습니다.

* `first`: 반환할 첫 번째 항목(`n`)입니다.
기본값은 `50`입니다.
최댓값은 `100`입니다.
* `after`: 요청된 페이지의 시작을 결정하는 커서입니다. 커서가 나타내는 항목은 결과 세트에 포함되지 않습니다. 항목의 커서는 `edges` 구조의 `cursor` 필드에 의해 결정됩니다.

예를 들어 *전체* 결과 목록의 주어진 커서 항목부터 시작하여 최대 5개의 모험을 포함하는 결과 페이지를 출력하는 경우

```graphql
query {
    adventurePaginated(first: 5, after: "ODg1MmMyMmEtZTAzMy00MTNjLThiMzMtZGQyMzY5ZTNjN2M1") {
        edges {
          cursor
          node {
            title
          }
        }
        pageInfo {
          endCursor
          hasNextPage
        }
    }
}
```

<!-- When available link to BP -->
<!-- Due to internal technical constraints, performance will degrade if sorting and filtering is applied on nested fields. Therefore it is recommended to use filter/sort fields stored at root level. For more information, see the [Best Practices document](link). -->

>[!NOTE]
>
>* 기본적으로 페이징은 결과의 순서가 항상 동일하도록 순서를 지정하기 위한 조각을 나타내는 저장소 노드의 UUID를 사용합니다. `sort` 사용 시 고유한 정렬을 위해 UUID가 암묵적으로 사용됩니다. 정렬 키가 동일한 두 항목의 경우에도 마찬가지입니다.
>
>* 내부 기술적 제한으로 인해 중첩된 필드에 정렬 및 필터링을 적용하면 성능이 저하됩니다. 따라서 루트 수준에서 저장된 필터/정렬 필드를 사용하는 것이 좋습니다. 페이지가 매겨진 대용량 결과 세트를 쿼리하려는 경우에도 권장되는 방법입니다.

## GraphQL 쿼리에서 웹에 최적화된 이미지 게재 {#web-optimized-image-delivery-in-graphql-queries}

웹에 최적화된 이미지 게재를 통해 Graphql 쿼리를 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* AEM Assets 이미지에 대한 URL 요청

* 이미지의 특정 렌디션이 자동으로 생성되고 반환되도록 쿼리와 함께 매개변수 전달

  >[!NOTE]
  >
  >지정된 변환은 AEM Assets에 저장되지 않습니다. 렌디션이 생성되어 짧은 기간 동안 캐시에 보관됩니다.

* JSON 게재의 일부로 URL 반환

AEM을 사용해 다음을 할 수 있습니다.

* [웹에 최적화된 이미지 게재](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html)를 GraphQL 쿼리에 전달합니다.

즉, 해당 이미지에 대한 GET 요청의 URL 매개변수와 동일한 방식으로 쿼리 실행 중에 명령이 적용됩니다.

이를 통해 JSON 게재를 위한 이미지 렌디션을 동적으로 생성할 수 있으므로 해당 렌디션을 저장소에 수동으로 만들고 저장할 필요가 없습니다.

GraphQL의 솔루션으로 다음과 같은 작업을 수행할 수 있습니다.

* `ImageRef` 참조에 `_dynamicUrl` 사용

* 필터가 정의된 목록 헤더에 `_assetTransform` 추가

### 변환 요청의 구조 {#structure-transformation-request}

`AssetTransform`(`_assetTransform`)은 URL 변환 요청을 만드는 데 사용됩니다.

구조 및 구문은 다음과 같습니다.

* `format`: GIF, PNG, PNG8, JPG, PJPG, BJPG, WEBP, WEBPLL, WEBPLY와 같이 확장자가 지원하는 모든 형식이 포함된 열거형
* `seoName`: 노드 이름 대신 파일 이름으로 사용할 문자열
* `crop`: 프레임 하위 구조(폭 또는 높이가 생략되면 높이 또는 폭이 동일한 값으로 사용됨)
   * `xOrigin`: 프레임의 x 원점(필수)
   * `yOrigin`: 프레임의 y 원점(필수)
   * `width`: 프레임의 폭
   * `height`: 프레임의 높이
* `size`: 차원 하위 구조(폭 또는 높이가 생략되면 높이 또는 폭이 동일한 값으로 사용됨)
   * `width`: 차원의 폭
   * `height`: 차원의 높이
* `rotation`: 지원되는 모든 회전의 열거형: R90, R180, R270
* `flip`: HORIZONTAL, VERTICAL, HORIZONTAL_AND_VERTICAL의 열거형
* `quality`: 이미지 품질의 백분율을 나타내는 1~100의 정수
* `width`: 출력 이미지의 폭을 정의하지만 이미지 생성기에서 무시되는 정수
* `preferWebp`: webp가 선호되는지 여부를 나타내는 부울(기본값은 false)

URL 변환은 경로, 목록 또는 페이지 지정과 같은 모든 쿼리 유형에 사용할 수 있습니다.

### 전체 매개변수로 웹에 최적화된 이미지 게재 {#web-optimized-image-delivery-full-parameters}

다음은 전체 매개변수 세트가 포함된 샘플 쿼리입니다.

```graphql
{
  articleList(
    _assetTransform: {
      format:GIF
      seoName:"test"
      crop:{
        xOrigin:10
        yOrigin:20
        width:50
        height:45
      }
      size:{
        height:100
        width:200
      }
      rotation:R90
      flip:HORIZONTAL_AND_VERTICAL
      quality:55
      width:123
      preferWebp:true
    }
  ) {
    items {
      _path
      featuredImage {
        ... on ImageRef {
          _dynamicUrl
        }
      }
    }
  }
}
```

### 단일 쿼리 변수로 웹에 최적화된 이미지 게재 {#web-optimized-image-delivery-single-query-variable}

다음 예에서는 단일 쿼리 변수의 사용을 보여 줍니다.

```graphql
query ($seoName: String!) {
  articleList(
    _assetTransform: {
      format:GIF
      seoName:$seoName
      crop:{
        xOrigin:10
        yOrigin:20
        width:50
        height:45
      }
      size:{
        height:100
        width:200
      }
      rotation:R90
      flip:HORIZONTAL_AND_VERTICAL
      quality:55
      width:123
      preferWebp:true
    }
  ) {
    items {
      _path
      featuredImage {
        ... on ImageRef {
          _dynamicUrl
        }
      }
    }
  }
}
```

### 다중 쿼리 변수로 웹에 최적화된 이미지 게재 {#web-optimized-image-delivery-multiple-query-variables}

다음 예에서는 다중 쿼리 변수의 사용을 보여 줍니다.

```graphql
query ($seoName: String!, $format: AssetTransformFormat!) {
  articleList(
    _assetTransform: {
      format:$format
      seoName:$seoName
      crop:{
        xOrigin:10
        yOrigin:20
        width:50
        height:45
      }
      size:{
        height:100
        width:200
      }
      rotation:R90
      flip:HORIZONTAL_AND_VERTICAL
      quality:55
      width:123
      preferWebp:true
    }
  ) {
    items {
      _path
      featuredImage {
        ... on ImageRef {
          _dynamicUrl
        }
      }
    }
  }
}
```

### URL을 통한 웹에 최적화된 이미지 게재 요청 {#web-optimized-image-delivery-request-url}

쿼리를 지속 쿼리로 저장하는 경우(예: `dynamic-url-x` 이름으로) [지속 쿼리를 직접 실행](/help/headless/graphql-api/persisted-queries.md#execute-persisted-query)할 수 있습니다.

예를 들어 이전 샘플(지속 쿼리로 저장된 샘플)을 직접 실행하려면 다음 URL을 사용합니다.

* [단일 매개변수](#dynamic-image-delivery-single-specified-parameter), 이름이 `dynamic-url-x`인 지속 쿼리

   * `http://localhost:4502/graphql/execute.json/wknd-shared/dynamic-url-x;seoName=xxx`

     응답은 다음과 같이 표시됩니다.

     ![매개변수를 사용한 이미지 게재](assets/cfm-graphiql-sample-image-delivery.png "매개변수를 사용한 이미지 게재")

* [다중 매개변수](#dynamic-image-delivery-multiple-specified-parameters), 이름이 `dynamic`인 지속 쿼리

   * `http://localhost:4502/graphql/execute.json/wknd-shared/dynamic;seoName=billiboy;format=GIF;`

     >[!CAUTION]
     >
     >후행 `;`은 매개변수 목록을 완전히 종료하려면 필수입니다.

### 이미지 게재의 제한 사항 {#image-delivery-limitations}

다음과 같은 제한 사항이 있습니다.

* 쿼리의 모든 이미지 부분에 적용되는 수정자(전역 매개변수)

* 캐싱 헤더

   * 작성자에 대한 캐싱 없음
   * 게시 시 캐싱 - 최대 수명 10분 (클라이언트에서 변경할 수 없음)

## AEM용 GraphQL - 확장 요약 {#graphql-extensions}

AEM용 GraphQL을 사용한 쿼리의 기본 작업은 표준 GraphQL 사양을 따릅니다. AEM의 GraphQL 쿼리에 몇 가지 확장이 있습니다.

* 하나의 결과가 필요한 경우:
   * 모델 이름을 사용하십시오. 예: 도시

* 결과 목록을 기대하는 경우:
   * 모델 이름에 `List`를 추가하십시오. 예: `cityList`
   * [샘플 쿼리 - 모든 도시에 대한 모든 정보](/help/headless/graphql-api/sample-queries.md#sample-all-information-all-cities)를 참조하십시오

  이후에 다음과 같은 작업을 수행할 수 있습니다.

   * [결과 정렬](#sorting)

      * `ASC`: 오름차순
      * `DESC`: 내림차순

   * 다음 중 하나를 사용하여 결과 페이지를 반환합니다.

      * [오프셋 및 제한이 포함된 목록 쿼리](#list-offset-limit)
      * [첫 번째 및 그 다음 페이지가 포함된 페이지 매김된 쿼리](#paginated-first-after)

   * [샘플 쿼리 - 모든 도시에 대한 모든 정보](/help/headless/graphql-api/sample-queries.md#sample-all-information-all-cities)를 참조하십시오

* 필터 `includeVariations`은 `List` 및 `Paginated` 쿼리 유형에 포함되어 있습니다.  쿼리 결과에서 콘텐츠 조각 변형을 검색하려면 `includeVariations` 필터를 `true`로 설정해야 합니다.

   * [주어진 모델의 복수 콘텐츠 조각과 변형에 대한 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-wknd-multiple-fragment-variations-given-model) 참조

  >[!CAUTION]
  >필터 `includeVariations` 및 시스템 생성 필드 `_variation`은 동일한 쿼리 정의에서 함께 사용할 수 없습니다.

* 논리적 OR을 사용하려는 경우:
   * ` _logOp: OR` 사용
   * [샘플 쿼리 - 이름이 “Jobs” 또는 “Smith”인 모든 사람](/help/headless/graphql-api/sample-queries.md#sample-all-persons-jobs-smith)을 참조하십시오

* 논리적 AND도 존재하지만 (흔히) 암시적

* 콘텐츠 조각 모델 내의 필드에 해당하는 필드 이름을 쿼리할 수 있습니다.
   * [샘플 쿼리 - 회사 CEO 및 직원의 전체 세부 정보](/help/headless/graphql-api/sample-queries.md#sample-full-details-company-ceos-employees)를 참조하십시오

* 모델의 필드 외에도 일부 시스템 생성 필드(앞에 밑줄 표시)가 있습니다.

   * 콘텐츠의 경우:

      * `_locale`: 언어 표시, 언어 관리자 기반
         * [주어진 로케일의 복수 콘텐츠 조각에 대한 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-wknd-multiple-fragments-given-locale)를 참조하십시오

      * `_metadata`: 조각에 대한 메타데이터 표시
         * [메타데이터에 대한 샘플 쿼리 - GB라는 제목의 상에 대한 메타데이터 나열](/help/headless/graphql-api/sample-queries.md#sample-metadata-awards-gb)을 참조하십시오

      * `_model`: 콘텐츠 조각 모델에 대한 쿼리 허용 (경로 및 제목)
         * [모델의 콘텐츠 조각 모델에 대한 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-wknd-content-fragment-model-from-model)를 참조하십시오

      * `_path`: 저장소 내의 콘텐츠 조각에 대한 경로
         * [샘플 쿼리 - 단일 특정 도시 조각](/help/headless/graphql-api/sample-queries.md#sample-single-specific-city-fragment)을 참조하십시오

      * `_reference`: 참조 표시, 서식 있는 텍스트 편집기에 인라인 참조 포함
         * [프리페치된 참조가 포함된 복수 콘텐츠 조각에 대한 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-wknd-multiple-fragments-prefetched-references)를 참조하십시오

      * `_variation`: 콘텐츠 조각 내 특정 변형 표시

        >[!NOTE]
        >
        >지정된 변형이 콘텐츠 조각에 존재하지 않는 경우, 마스터 변형은 (대체) 기본값으로 반환됩니다.

        >[!CAUTION]
        >
        >시스템 생성 필드 `_variation`은 필터 `includeVariations`과 함께 사용할 수 없습니다.

         * [샘플 쿼리 - 이름이 붙은 변형이 있는 모든 도시](/help/headless/graphql-api/sample-queries.md#sample-cities-named-variation)를 참조하십시오

   * [이미지 게재](#image-delivery):

      * `ImageRef`: `_dynamicUrl` 참조

      * `_assetTransform`: 필터가 정의된 목록 헤더

      * 다음을 참조하십시오.

         * [전체 매개변수가 포함된 이미지 게재를 위한 샘플 쿼리](#image-delivery-full-parameters)

         * [지정된 단일 매개변수가 있는 이미지 게재를 위한 샘플 쿼리](#image-delivery-single-specified-parameter)

   * `_tags`: 태그가 포함된 콘텐츠 조각 ID 또는 변형 표시, `cq:tags` 식별자 배열,

      * [샘플 쿼리 - City Break로 태그된 모든 도시의 이름](/help/headless/graphql-api/sample-queries.md#sample-names-all-cities-tagged-city-breaks) 참조
      * [특정 태그가 첨부된 주어진 모델의 콘텐츠 조각 변형에 대한 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-wknd-fragment-variations-given-model-specific-tag) 참조
      * [태그 ID별로 필터링하고 변형을 제외하는 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-filtering-tag-not-variations) 참조
      * [태그 ID별로 필터링하고 변형을 포함하는 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-filtering-tag-with-variations) 참조

     >[!NOTE]
     >
     >콘텐츠 조각의 메타데이터를 나열하여 태그를 쿼리할 수도 있습니다.

   * 작업:

      * `_operator`: 특정 연산자 적용 - `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`, `STARTS_WITH`
         * [샘플 쿼리 - 이름이 “Jobs”가 아닌 모든 사람](/help/headless/graphql-api/sample-queries.md#sample-all-persons-not-jobs)을 참조하십시오
         * [샘플 쿼리 - `_path`가 특정 접두사로 시작하는 모든 모험](/help/headless/graphql-api/sample-queries.md#sample-wknd-all-adventures-cycling-path-filter)을 참조하십시오

      * `_apply`: 특정 조건 적용. 예: `AT_LEAST_ONCE`
         * [샘플 쿼리 - 적어도 한 번은 발생해야 하는 항목이 있는 배열 필터링](/help/headless/graphql-api/sample-queries.md#sample-array-item-occur-at-least-once)을 참조하십시오

      * `_ignoreCase`: 쿼리할 때 대소문자 무시
         * [샘플 쿼리 - 대소문자에 관계없이 이름에 SAN이 있는 모든 도시](/help/headless/graphql-api/sample-queries.md#sample-all-cities-san-ignore-case)를 참조하십시오

* GraphQL 공용 구조체 형식이 지원됩니다.

   * `... on` 사용
      * [콘텐츠 참조가 있는 특정 모델의 콘텐츠 조각에 대한 샘플 쿼리](/help/headless/graphql-api/sample-queries.md#sample-wknd-fragment-specific-model-content-reference)를 참조하십시오

* 중첩된 조각 쿼리 시 대체:

   * 주어진 변형이 중첩된 조각에 존재하지 않으면&#x200B;**마스터** 변형이 반환됩니다.

## 외부 웹 사이트에서 GraphQL 엔드포인트 쿼리 {#query-graphql-endpoint-from-external-website}

외부 웹 사이트에서 GraphQL 엔드포인트에 액세스하려면 다음을 구성해야 합니다.

* [CORS 필터](/help/headless/deployment/cross-origin-resource-sharing.md)
* [레퍼러 필터](/help/headless/deployment/referrer-filter.md)

## 인증 {#authentication}

[콘텐츠 조각의 원격 AEM GraphQL 쿼리 인증](/help/headless/security/authentication.md)을 참조하십시오.

## FAQ {#faqs}

제기된 질문:

1. **Q**: “*AEM용 GraphQL API는 쿼리 빌더 API와 어떻게 다릅니까?*”

   * **A**:
“*AEM GraphQL API는 JSON 출력에 대한 전체 제어를 제공하며 콘텐츠 쿼리를 위한 업계 표준입니다.
앞으로 AEM은 AEM GraphQL API에 투자할 계획입니다.*”

## 튜토리얼 - AEM Headless 및 GraphQL 시작하기 {#tutorial}

실습형 튜토리얼을 찾고 계십니까? Headless CMS 시나리오에서 AEM의 GraphQL API를 사용하여 콘텐츠를 빌드하고 노출하고 외부 앱에서 사용하는 방법을 보여 주는 [AEM Headless 및 GraphQL 시작하기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) 엔드투엔드 튜토리얼을 확인하십시오.
