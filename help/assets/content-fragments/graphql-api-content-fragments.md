---
title: 컨텐츠 조각에 사용할 AEM GraphQL API
description: AEM(Adobe Experience Manager)의 컨텐츠 조각을 헤드리스 컨텐츠 전달을 위한 AEM GraphQL API를 사용하여 Cloud Service으로 사용하는 방법에 대해 알아보십시오.
translation-type: tm+mt
source-git-commit: 36e0fd66c9119571cde5c8791862abed8b552d5a
workflow-type: tm+mt
source-wordcount: '3220'
ht-degree: 1%

---


# 컨텐츠 조각에 사용할 AEM GraphQL API {#graphql-api-for-use-with-content-fragments}

컨텐츠 조각에 사용되는 Cloud Service(AEM) GraphQL API로 Adobe Experience Manager은 오픈 소스 GraphQL API를 기반으로 하는 것이 중요합니다.

AEM에서 GraphQL API를 사용하면 헤드리스 CMS 구현에서 컨텐츠 조각을 JavaScript 클라이언트에 효율적으로 전달할 수 있습니다.

* REST와 같이 반복적인 API 요청 방지,
* 전달이 특정 요구 사항에 한정되어 있다는 것을 보장하는
* 단일 API 쿼리에 대한 응답으로 렌더링하는 데 필요한 내용을 정확하게 일괄적으로 전달할 수 있도록 허용합니다.

>[!NOTE]
>
>GraphQL은 현재 AEM(Adobe Experience Manager)의 두 가지(별도) 시나리오에서 Cloud Service으로 사용됩니다.
>
>* [AEM Commerce는 GraphQL을 통해 상거래 플랫폼의 데이터를 사용합니다](/help/commerce-cloud/architecture/magento.md).
>* AEM 컨텐츠 조각은 AEM GraphQL API(표준 GraphQL을 기반으로 사용자 정의된 구현)와 함께 작동하여 애플리케이션에서 사용할 수 있도록 구조화된 컨텐츠를 제공합니다.


## GraphQL API {#graphql-api}

GraphQL:

* &quot;*...API에 대한 쿼리 언어 및 기존 데이터와 관련 쿼리를 충족하는 런타임입니다. GraphQL은 API에 있는 데이터에 대한 완벽하고 이해할 수 있는 설명을 제공하며 고객에게 필요한 것과 더 이상 필요한 것을 정확하게 요청할 수 있는 기능을 제공하고 시간이 지남에 따라 API를 보다 쉽게 발전시켜 주며 강력한 개발자 도구를 활성화합니다.*&quot;

   [GraphQL.org](https://graphql.org) 참조

* &quot;*...유연한 API 레이어의 개방형 사양입니다. GraphQL을 기존 백엔드에 배치하여 보다 신속하게 제품을 구축할 수 있습니다..*&quot;

   [GraphQL 탐색](https://www.graphql.com)을 참조하십시오.

* *&quot;...데이터 쿼리 언어 및 사양은 2015년 공개적으로 오픈 소스로 배포되기 전에 Facebook에서 내부적으로 개발한 것으로, 개발자 생산성을 높이고 데이터 전송 양을 최소화하기 위해 REST 기반 아키텍처에 대한 대체 요소를 제공합니다. GraphQL은 모든 규모의 수백 개의 조직에서 프로덕션에 사용됩니다...*

   [GraphQL Foundation](https://foundation.graphql.org/)을 참조하십시오.

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world all of the tools they need to understand and adopt GraphQL.*". 
-->

GraphQL API에 대한 자세한 내용은 다음 섹션(다른 많은 리소스 중)을 참조하십시오.

* [graphql.org](https://graphql.org)에서:

   * [GraphQL 소개](https://graphql.org/learn)

   * [GraphQL 사양](http://spec.graphql.org/)

* [graphql.com](https://graphql.com)에서:

   * [안내선](https://www.graphql.com/guides/)

   * [자습서](https://www.graphql.com/tutorials/)

   * [사례 연구](https://www.graphql.com/case-studies/)

AEM용 GraphQL 구현은 표준 GraphQL Java 라이브러리를 기반으로 합니다. 다음을 참조하십시오.

* [graphQL.org - Java](https://graphql.org/code/#java)

* [GitHub에서 GraphQL Java](https://github.com/graphql-java)

### GraphQL 용어 {#graphql-terminology}

GraphQL은 다음을 사용합니다.

* **[쿼리](https://graphql.org/learn/queries/)**

* **[스키마 및 유형](https://graphql.org/learn/schema/)**:

   * 스키마가 컨텐츠 조각 모델을 기반으로 AEM에 의해 생성됩니다.
   * GraphQL은 스키마를 사용하여 AEM 구현을 위해 GraphQL에 허용된 유형과 작업을 표시합니다.

* **[필드](https://graphql.org/learn/queries/#fields)**

* **[GraphQL 끝점](#graphql-aem-endpoint)**
   * GraphQL 쿼리에 응답하고 GraphQL 스키마에 대한 액세스를 제공하는 AEM의 경로입니다.

   * 자세한 내용은 [GraphQL 끝점 활성화](#enabling-graphql-endpoint)를 참조하십시오.

[우수 사례](https://graphql.org/learn/best-practices/)를 비롯한 자세한 내용은 [(GraphQL.org) GraphQL 소개](https://graphql.org/learn/)을 참조하십시오.

### GraphQL 쿼리 유형 {#graphql-query-types}

GraphQL을 사용하면 다음 중 하나를 반환하기 위해 쿼리를 수행할 수 있습니다.

* **단일 항목**

* **[항목 목록](https://graphql.org/learn/schema/#lists-and-non-null)**

다음을 수행할 수도 있습니다.

* [캐시된 지속적인 쿼리](#persisted-queries-caching)

## AEM 끝점에 대한 GraphQL {#graphql-aem-endpoint}

끝점은 AEM용 GraphQL에 액세스하는 데 사용되는 경로입니다. 이 경로를 사용하여(또는 앱) 다음 작업을 수행할 수 있습니다.

* GraphQL 스키마 액세스,
* GraphQL 쿼리 보내기,
* GraphQL 쿼리에 대한 응답을 받습니다.

AEM 끝점에 대한 GraphQL의 저장소 경로는 다음과 같습니다.

`/content/cq:graphql/global/endpoint`

앱이 요청 URL에 다음 경로를 사용할 수 있습니다.

`/content/_cq_graphql/global/endpoint.json`

AEM용 GraphQL의 끝점을 활성화하려면 다음을 수행해야 합니다.

>[!CAUTION]
>
>이러한 단계는 가까운 미래에 변경될 수 있습니다.

* [GraphQL 끝점 사용](#enabling-graphql-endpoint)
* [추가 구성 수행](#additional-configurations-graphql-endpoint)

### GraphQL 끝점 활성화 {#enabling-graphql-endpoint}

>[!NOTE]
>
>이러한 단계를 간소화하는 데 도움이 되는 패키지에 대한 자세한 내용은 [지원 패키지](#supporting-packages)을 참조하십시오.

AEM에서 GraphQL 쿼리를 활성화하려면 `/content/cq:graphql/global/endpoint`에서 끝점을 만듭니다.

* 노드 `cq:graphql` 및 `global`은(는) `sling:Folder` 유형이어야 합니다.
* 노드 `endpoint`은(는) `nt:unstructured` 유형이어야 하며 `graphql/sites/components/endpoint`의 `sling:resourceType`를 포함해야 합니다.

>[!CAUTION]
>
>끝점에 현재 알려진 문제가 있습니다.
>
>* `cq:graphql` 항목은 **사이트** 콘솔에 표시됩니다.를 클릭합니다.
   >  이것은 사용하지 않아야 합니다.


>[!CAUTION]
>
>모든 사람이 끝점에 액세스할 수 있습니다. GraphQL 쿼리는 서버에 무거운 로드를 부과할 수 있으므로 특히 게시 인스턴스에서 보안상의 문제가 될 수 있습니다.
>
>종단점에서 사용 사례에 적합한 ACL을 설정할 수 있습니다.

>[!NOTE]
>
>종점이 곧바로 작동하지 않습니다. GraphQL 끝점](#additional-configurations-graphql-endpoint)에 대해 [추가 구성을 별도로 제공해야 합니다.

>[!NOTE]
>또한 [GraphiQL IDE](#graphiql-interface)를 사용하여 GraphQL 쿼리를 테스트하고 디버깅할 수 있습니다.

### GraphQL 끝점에 대한 추가 구성 {#additional-configurations-graphql-endpoint}

>[!NOTE]
>
>이러한 단계를 간소화하는 데 도움이 되는 패키지에 대한 자세한 내용은 [지원 패키지](#supporting-packages)을 참조하십시오.

추가 구성이 필요합니다.

* Dispatcher:
   * 필수 URL을 허용하려면
   * 필수
* 별칭 URL:
   * 끝점에 대해 간소화된 URL을 할당하려면
   * 선택 사항입니다
* OSGi 구성:
   * GraphQL 서블릿 구성:
      * 끝점에 대한 요청을 처리합니다.
      * 구성 이름은 `org.apache.sling.graphql.core.GraphQLServlet`입니다. OSGi 팩토리 구성으로 제공해야 합니다.
      * `sling.servlet.extensions` 을(를)  `[json]`
      * `sling.servlet.methods` 을(를)  `[GET,POST]`
      * `sling.servlet.resourceTypes` 을(를)  `[graphql/sites/components/endpoint]`
      * 필수
   * 스키마 서블릿 구성:
      * GraphQL 스키마 만들기
      * 구성 이름은 `com.adobe.aem.graphql.sites.adapters.SlingSchemaServlet`입니다. OSGi 팩토리 구성으로 제공해야 합니다.
      * `sling.servlet.extensions` 을(를)  `[GQLschema]`
      * `sling.servlet.methods` 을(를)  `[GET]`
      * `sling.servlet.resourceTypes` 을(를)  `[graphql/sites/components/endpoint]`
      * 필수
   * CSRF 구성:
      * 끝점에 대한 보안 보호
      * 구성 이름은 `com.adobe.granite.csrf.impl.CSRFFilter`입니다.
      * 제외된 경로의 기존 목록에 `/content/cq:graphql/global/endpoint`을(를) 추가합니다(`filter.excluded.paths`).
      * 필수

### 지원 패키지 {#supporting-packages}

GraphQL 끝점의 설정을 간소화하기 위해 Adobe은 [GraphQL 샘플 프로젝트](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-graphql%2Fgraphql-sample.zip) 패키지를 제공합니다.

이 아카이브는 필요한 추가 구성](#additional-configurations-graphql-endpoint) 및 [GraphQL 끝점](#enabling-graphql-endpoint)을(를) 모두 포함합니다. [ 일반 AEM 인스턴스에 설치된 경우 `/content/cq:graphql/global/endpoint`에 완전히 작동하는 GraphQL 끝점이 표시됩니다.

이 패키지는 GraphQL 프로젝트에 대한 청사진입니다. 패키지 사용 방법에 대한 자세한 내용은 **README** 패키지를 참조하십시오.

필요한 구성을 수동으로 만들려면 Adobe에서 전용 [GraphQL 끝점 콘텐츠 패키지](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-graphql%2Fgraphql-global-endpoint.zip)도 제공합니다. 이 콘텐츠 패키지에는 구성이 없는 GraphQL 끝점만 들어 있습니다.

## 그래픽 QL 인터페이스 {#graphiql-interface}

<!--
AEM Graph API includes an implementation of the standard [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) interface. This allows you to directly input, and test, queries.
-->

AEM GraphQL에서 표준 [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) 인터페이스의 구현을 사용할 수 있습니다. AEM](#installing-graphiql-interface)과 함께 [설치할 수 있습니다.

이 인터페이스를 사용하면 쿼리를 직접 입력하고 테스트할 수 있습니다.

예:

* `http://localhost:4502/content/graphiql.html`

여기에는 내역 및 온라인 설명서와 함께 구문 강조, 자동 완성, 자동 제안 등의 기능이 제공됩니다.

![GraphiQL ](assets/cfm-graphiql-interface.png "인터페이스 그래픽QL 인터페이스")

### AEM GraphiQL 인터페이스 {#installing-graphiql-interface} 설치

GraphiQL 사용자 인터페이스는 전용 패키지와 함께 AEM에 설치할 수 있습니다.[GraphiQL 컨텐츠 패키지 v0.0.4](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-graphql%2Fgraphiql-0.0.4.zip) 패키지.

<!--
See the package **README** for full details; including full details of how it can be installed on an AEM instance - in a variety of scenarios.
-->

## 작성 및 게시 환경에 대한 사용 사례 {#use-cases-author-publish-environments}

사용 사례는 Cloud Service 환경으로 AEM의 유형에 따라 달라질 수 있습니다.

* 게시 환경;다음 작업에 사용됩니다.
   * JS 응용 프로그램에 대한 쿼리 데이터(표준 사용 사례)

* 작성 환경;다음 작업에 사용됩니다.
   * &quot;컨텐츠 관리 목적&quot;을 위해 데이터 쿼리:
      * Cloud Service으로 AEM의 GraphQL은 현재 읽기 전용 API입니다.
      * REST API는 CR(u)D 작업에 사용할 수 있습니다.

## 권한 {#permission}

권한은 자산에 액세스하는 데 필요한 권한입니다.

## 스키마 생성 {#schema-generation}

GraphQL은 강력한 형식의 API로, 데이터를 유형별로 명확히 구조화하고 구성해야 합니다.

GraphQL 사양에서는 특정 인스턴스에서 데이터를 심문하기 위한 강력한 API를 만드는 방법에 대한 일련의 지침을 제공합니다. 이렇게 하려면 클라이언트는 쿼리에 필요한 모든 유형을 포함하는 [스키마](#schema-generation)를 반입해야 합니다.

컨텐츠 조각의 경우 GraphQL 스키마(구조 및 유형)는 **Enabled** [컨텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md) 및 해당 데이터 유형을 기반으로 합니다.

>[!CAUTION]
>
>모든 GraphQL 스키마(**Enabled**&#x200B;인 컨텐츠 조각 모델에서 파생됨)는 GraphQL 끝점을 통해 읽을 수 있습니다.
>
>즉, 민감한 데이터가 이러한 방식으로 누설될 수 있으므로 사용할 수 없도록 해야 합니다.예를 들어 모델 정의에서 필드 이름으로 존재할 수 있는 정보가 포함됩니다.

예를 들어 사용자가 `Article`이라는 컨텐츠 조각 모델을 만든 경우 AEM은 `ArticleModel` 유형의 `article` 객체를 생성합니다. 이 유형의 필드는 모델에 정의된 필드 및 데이터 유형에 해당합니다.

1. 컨텐츠 조각 모델:

   ![GraphQL에 사용할 ](assets/cfm-graphqlapi-01.png "GraphQLContent 조각 모델과 함께 사용할 컨텐츠 조각 모델")

1. 해당 GraphQL 스키마(GraphiQL 자동 문서에서 출력):
   ![컨텐츠 조각 모델을 기반으로 하는 GraphQL ](assets/cfm-graphqlapi-02.png "스키마 컨텐츠 조각 모델 기반 QL 스키마")

   생성된 유형 `ArticleModel`에 여러 개의 [필드](#fields)가 포함되어 있음을 보여줍니다.

   * 이 중 3개는 사용자가 제어했습니다.`author`, `main` 및 `referencearticle`.

   * 다른 필드는 AEM에 의해 자동으로 추가되었으며 특정 컨텐츠 조각에 대한 정보를 제공하는 유용한 방법을 나타냅니다.이 예에서 `_path`, `_metadata`, `_variations`입니다. 이러한 [도우미 필드](#helper-fields)는 사용자가 정의한 항목과 자동 생성된 항목을 구별하기 위해 선행 `_`으로 표시됩니다.

1. 사용자가 아티클 모델을 기반으로 컨텐츠 조각을 만든 후 GraphQL을 통해 질문할 수 있습니다. 예를 들어 [샘플 쿼리](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries)(GraphQL](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)에 사용할 [샘플 컨텐츠 조각 구조 기준)을 참조하십시오.

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

## 필드 {#fields}

스키마 내에는 두 가지 기본 카테고리 중 개별 필드가 있습니다.

* 생성하는 필드.

   [필드 유형](#field-types) 선택 항목은 컨텐츠 조각 모델을 구성하는 방법에 따라 필드를 만드는 데 사용됩니다. 필드 이름은 **데이터 유형**&#x200B;의 **속성 이름** 필드에서 가져옵니다.

   * 사용자가 특정 데이터 형식을 구성할 수 있으므로 고려할 **Render As** 속성도 있습니다.예를 들어 단일 행 텍스트 또는 다중 필드로 사용할 수 있습니다.

* AEM용 GraphQL은 또한 [도우미 필드](#helper-fields)도 많이 생성합니다.

   컨텐츠 조각을 식별하거나 컨텐츠 조각에 대한 자세한 정보를 얻는 데 사용됩니다.

### 필드 유형 {#field-types}

AEM용 GraphQL은 유형 목록을 지원합니다. 지원되는 모든 컨텐츠 조각 모델 데이터 유형과 해당 GraphQL 유형이 표시됩니다.

| 컨텐츠 조각 모델 - 데이터 유형 | GraphQL 유형 | 설명 |
|--- |--- |--- |
| 한 줄 텍스트 | 문자열, [String] |  작성자 이름, 위치 이름 등과 같은 간단한 문자열에 사용됩니다. |
| 여러 줄 텍스트 | 문자열 |  아티클의 본문과 같은 텍스트를 출력하는 데 사용됩니다. |
| 번호 |  부동, [부동] | 부동 소수점 번호와 일반 숫자를 표시하는 데 사용됩니다. |
| 부울 |  부울 |  확인란→ 단순한 true/false 문을 표시하는 데 사용됩니다. |
| 날짜 및 시간 | 달력 |  ISO 8086 형식으로 날짜 및 시간을 표시하는 데 사용됨 |
| 열거 |  String |  모델 생성 시 정의된 옵션 목록에서 옵션을 표시하는 데 사용됩니다. |
|  태그 |  [String] |  AEM에서 사용되는 태그를 나타내는 문자열 목록을 표시하는 데 사용됩니다. |
| 컨텐츠 참조 |  문자열 |  AEM에서 다른 에셋에 대한 경로를 표시하는 데 사용됩니다. |
| 조각 참조 |  *모델 유형* |  모델이 생성될 때 정의된 특정 모델 유형의 다른 컨텐츠 조각을 참조하는 데 사용됩니다. |

### 도우미 필드 {#helper-fields}

AEM용 GraphQL은 사용자 생성 필드에 대한 데이터 유형 외에도 컨텐츠 조각을 식별하거나 컨텐츠 조각에 대한 추가 정보를 제공하기 위해 많은 *helper* 필드도 생성합니다.

#### 경로 {#path}

경로 필드는 GraphQL에서 식별자로 사용됩니다. AEM 저장소 내의 컨텐츠 조각 자산의 경로를 나타냅니다. 다음 이유로 컨텐츠 조각 식별자로 선택했습니다.

* aem 내에서 고유하며
* 간편하게 가져올 수 있습니다.

다음 코드에는 컨텐츠 조각 모델 `Person`을(를) 기반으로 생성된 모든 컨텐츠 조각 경로가 표시됩니다.

```xml
{
  personList {
    items {
      _path
    }
  }
}
```

특정 유형의 단일 컨텐츠 조각을 검색하려면 먼저 해당 경로를 결정해야 합니다. 예:

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      firstName
      name
    }
  }
}
```

[샘플 쿼리 - 단일 특정 도시 조각](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)을 참조하십시오.

#### 메타데이터 {#metadata}

GraphQL을 통해 AEM은 컨텐츠 조각의 메타데이터도 표시합니다. 메타데이터는 컨텐츠 조각 제목, 축소판 경로, 컨텐츠 조각 설명, 컨텐츠 조각 작성 날짜 등 컨텐츠 조각을 설명하는 정보입니다.

메타데이터는 스키마 편집기를 통해 생성되며 특정 구조가 없으므로 `TypedMetaData` GraphQL 유형이 구현되어 컨텐츠 조각의 메타데이터를 표시합니다. `TypedMetaData` 다음 스칼라 유형별로 그룹화된 정보를 표시합니다.

| 필드 |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!`  |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

각 스칼라 유형은 단일 이름-값 쌍 또는 이름-값 쌍의 배열을 나타냅니다. 여기서 해당 쌍의 값은 그룹화된 형식의 값입니다.

예를 들어 컨텐츠 조각의 제목을 검색하려는 경우 이 속성은 문자열 속성이므로 모든 문자열 메타데이터를 쿼리할 수 있습니다.

메타데이터를 쿼리하려면:

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
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

생성된 GraphQL 스키마를 보는 경우 모든 메타데이터 GraphQL 유형을 볼 수 있습니다. 모든 모델 유형에는 동일한 `TypedMetaData`이 있습니다.

>[!NOTE]
>
>**일반 및 배열 메타데이터 간의 차이**
>`StringMetadata` 및 `StringArrayMetadata` 모두 보관소 내에 저장되어 있는 항목을 검색하는 방법이 아니라 참조합니다.
>
>예를 들어 `stringMetadata` 필드를 호출하면 저장소에 저장된 모든 메타데이터의 배열이 `String`(으)로 수신되고, `stringArrayMetadata`를 호출하면 저장소에 저장된 모든 메타데이터의 배열이 `String[]`로 수신됩니다.

[메타데이터에 대한 샘플 쿼리 - 제목이 GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb)인 시상식에 대한 메타데이터 목록을 참조하십시오.

#### 변형 {#variations}

`_variations` 필드는 컨텐츠 조각의 변형을 쿼리하는 작업을 단순화하기 위해 구현되었습니다. 예:

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _variations
    }
  }
}
```

[샘플 쿼리 - 명명된 변형이 있는 모든 도시](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation)를 참조하십시오.

<!--
## Security Considerations {#security-considerations}
-->

## GraphQL 변수 {#graphql-variables}

GraphQL은 쿼리에 변수를 배치할 수 있도록 허용합니다. 자세한 내용은 GraphiQL](https://graphql.org/learn/queries/#variables)에 대한 [GraphQL 설명서를 참조하십시오.

예를 들어 특정 변형이 있는 `Article` 유형의 모든 컨텐츠 조각을 가져오려면 GraphiQL에서 `variation` 변수를 지정할 수 있습니다.

![GraphQL ](assets/cfm-graphqlapi-03.png "변수GraphQL 변수")

```xml
### query
query GetArticlesByVariation($variation: String!) {
    articleList(variation: $variation) {
        items {
            _path
            author
        }
    }
}
 
### in query variables
{
    "variation": "uk"
}
```

## GraphQL 지시문 {#graphql-directives}

GraphQL에서는 GraphQL 지시문이라는 변수를 기반으로 쿼리를 변경할 수 있습니다.

예를 들어 변수 `includePrice`을 기준으로 모든 `AdventureModels` 쿼리에 `adventurePrice` 필드를 포함할 수 있습니다.

![GraphQL ](assets/cfm-graphqlapi-04.png "지시어GraphQL 지시문")

```xml
### query
query GetAdventureByType($includePrice: Boolean!) {
  adventureList {
    items {
      adventureTitle
      adventurePrice @include(if: $includePrice)
    }
  }
}
 
### in query variables
{
    "includePrice": true
}
```

## {#filtering} 필터링

GraphQL 쿼리에서 필터링을 사용하여 특정 데이터를 반환할 수도 있습니다.

필터링은 논리 연산자 및 표현식을 기반으로 하는 구문을 사용합니다.

예를 들어 다음(기본) 쿼리는 `Jobs` 또는 `Smith` 이름을 가진 모든 사람을 필터링합니다.

```xml
query {
  personList(filter: {
    name: {
      _logOp: OR
      _expressions: [
        {
          value: "Jobs"
        },
        {
          value: "Smith"
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

자세한 예는 다음을 참조하십시오.

* aem 확장의 [GraphQL 세부 사항](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-extensions)

* [이 샘플 컨텐츠 및 구조를 사용한 샘플 쿼리](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

   * 그리고 샘플 쿼리에 사용할 수 있도록 준비된 [샘플 컨텐트 및 구조](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)

* [WKND 프로젝트를 기반으로 하는 샘플 쿼리](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## 지속적인 쿼리(캐싱) {#persisted-queries-caching}

POST 요청을 사용하여 쿼리를 준비한 후 HTTP 캐시 또는 CDN을 통해 캐싱할 수 있는 GET 요청을 사용하여 실행할 수 있습니다.

POST 쿼리는 일반적으로 캐시되지 않으며, 쿼리와 함께 GET을 매개 변수로 사용하는 경우 매개 변수가 HTTP 서비스 및 중계기에 너무 많이 사용되면 위험합니다.

지정된 쿼리를 유지하는 데 필요한 단계는 다음과 같습니다.

>[!NOTE]
>이 전에 적절한 구성을 위해 **GraphQL 지속성 쿼리**&#x200B;를 활성화해야 합니다. 자세한 내용은 [구성 브라우저에서 컨텐츠 조각 기능 활성화](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)를 참조하십시오.

1. 새 끝점 URL `/graphql/persist.json/<config>/<persisted-label>`에 PUT을 사용하여 쿼리를 준비합니다.

   예를 들어 지속적인 쿼리를 만듭니다.

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
       }
     }
   }'
   ```

1. 이 시점에서 응답을 확인하십시오.

   예를 들어 성공 여부를 확인합니다.

   ```xml
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. 그런 다음 URL `/graphql/execute.json/<shortPath>`을(를) 사용하여 지속적인 쿼리를 다시 재생할 수 있습니다.

   예를 들어, 지속적인 쿼리를 사용합니다.

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. POST를 통해 기존 쿼리 경로로 지속적인 쿼리를 업데이트합니다.

   예를 들어, 지속적인 쿼리를 사용합니다.

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
         referencearticle {
           _path
         }
       }
     }
   }'
   ```

1. 래핑된 일반 쿼리를 만듭니다.

   예:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. 캐시 컨트롤을 사용하여 래핑된 일반 쿼리를 만듭니다.

   예:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. 매개 변수를 사용하여 지속적인 쿼리를 만듭니다.

   예:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-parameters" \
       -d \
   'query GetAsGraphqlModelTestByPath($apath: String!, $withReference: Boolean = true) {
     articleByPath(_path: $apath) {
       item {
         _path
           author
           main {
           plaintext
           }
           referencearticle @include(if: $withReference) {
           _path
           }
         }
       }
     }'
   ```

1. 매개 변수를 사용하여 쿼리 실행

   예:

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   
   $ curl -X GET \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   ```

1. 게시를 통해 쿼리를 실행하려면 관련 영구 트리가 복제되어야 합니다

   * 복제에 POST 사용:

      ```xml
      $curl -X POST   http://localhost:4502/bin/replicate.json \
        -H 'authorization: Basic YWRtaW46YWRtaW4=' \
        -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
        -F cmd=activate
      ```

   * 패키지 사용:
      1. 새 패키지 정의를 만듭니다.
      1. 구성을 포함합니다(예: `/conf/wknd/settings/graphql/persistentQueries`).
      1. 패키지를 빌드합니다.
      1. 패키지를 복제합니다.
   * 복제/배포 도구 사용
      1. 배포 도구로 이동합니다.
      1. 구성에 대한 트리 활성화를 선택합니다(예: `/conf/wknd/settings/graphql/persistentQueries`).
   * 워크플로우 사용(워크플로우 실행 구성 사용):
      1. 다른 이벤트(예: 작성, 수정 등)에서 구성을 복제하는 워크플로우 모델을 실행하기 위한 워크플로우 실행 규칙을 정의합니다.



1. 쿼리 구성이 게시되면 게시 끝점을 사용하기만 해도 동일한 원칙이 적용됩니다.

   >[!NOTE]
   >
   >익명 액세스의 경우 시스템은 ACL이 &quot;모든 사용자&quot;에게 쿼리 구성에 대한 액세스 권한을 허용한다고 가정합니다.
   >
   >그렇지 않으면 실행할 수 없습니다.

   >[!NOTE]
   >
   >URL의 모든 세미콜론(&quot;;&quot;)을 인코딩해야 합니다.
   >
   >예를 들어, 지속적인 쿼리 실행 요청에서와 같이
   >
   >
   ```xml
   >curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   >```

## 외부 웹 사이트 {#query-graphql-endpoint-from-external-website}에서 GraphQL 끝점을 쿼리하는 중

>[!NOTE]
>
>AEM의 CORS 리소스 공유 정책에 대한 자세한 개요는 [CORS(교차 도메인 리소스 공유)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=en#understand-cross-origin-resource-sharing-(cors))를 참조하십시오.

제3자 웹 사이트에서 JSON 출력을 사용하도록 허용하려면 고객 Git 리포지토리에 CORS 정책을 구성해야 합니다. 이 작업은 원하는 종단점에 대해 적절한 OSGi CORS 구성 파일을 추가하여 수행합니다. 이 구성은 액세스 권한을 부여할 신뢰할 수 있는 웹 사이트 이름(또는 regex)을 지정해야 합니다.

* GraphQL 끝점에 액세스:

   * alloworiin:[도메인] 또는 alloworiinregexp:[도메인 regex]
   * supportedmethods:[POST]
   * 할당 패스:[&quot;/content/graphql/global/endpoint.json&quot;]

* GraphQL 지속적인 쿼리 끝점에 액세스:

   * alloworiin:[도메인] 또는 alloworiinregexp:[도메인 regex]
   * supportedmethods:[GET]
   * 할당 패스:[&quot;/graphql/execute.json/.*&quot;]

>[!CAUTION]
>
>다음은 고객의 책임입니다.
>
>* 신뢰할 수 있는 도메인에 대한 액세스 권한만 부여할 수 있습니다.
>* 중요한 정보가 노출되지 않도록 합니다.
>* 와일드카드 [*] 구문을 사용하지 않음;이렇게 하면 GraphQL 끝점에 대한 인증된 액세스가 모두 비활성화되고 이를 전체 세계에 노출할 수 있습니다.


>[!CAUTION]
>
>모든 GraphQL [스키마](#schema-generation)(**Enabled**&#x200B;인 컨텐츠 조각 모델에서 파생됨)는 GraphQL 끝점을 통해 읽을 수 있습니다.
>
>즉, 민감한 데이터가 이러한 방식으로 누설될 수 있으므로 사용할 수 없도록 해야 합니다.예를 들어 모델 정의에서 필드 이름으로 존재할 수 있는 정보가 포함됩니다.

## 인증 {#authentication}

내용 조각에 대한 [원격 AEM GraphQL 쿼리](/help/assets/content-fragments/graphql-authentication-content-fragments.md)를 참조하십시오.

<!-- to be addressed later -->

<!--
## Sorting {#sorting}
-->

<!-- to be addressed later -->

<!--
## Paging {#paging}
-->

## FAQ {#faqs}

발생한 질문:

1. **Q**:&quot;*AEM용 GraphQL API는 쿼리 빌더 API와 어떻게 다릅니까?*&quot;

   * **A**:&quot;AEM *GraphQL API는 JSON 출력에 대한 전체 제어 기능을 제공하며 콘텐츠를 쿼리하는 업계 표준입니다.
앞으로 AEM은 AEM GraphQL API에 투자할 계획입니다.*&quot;

## 자습서 - AEM 헤드리스 시작하기 및 GraphQL {#tutorial}

실습 자습서를 찾고 계십니까? AEM GraphQL API를 사용하여 콘텐츠를 빌드하고 노출하고 헤드리스 CMS 시나리오에서 외부 앱에서 사용하는 방법을 소개하는 [AEM 헤드리스 시작하기 및 GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) 엔드 투 엔드 자습서를 참조하십시오.
