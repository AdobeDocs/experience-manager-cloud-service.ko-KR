---
title: 컨텐츠 조각에 사용할 AEM GraphQL API
description: AEM(Adobe Experience Manager)의 컨텐츠 조각을 헤드리스 컨텐츠 전달을 위해 AEM GraphQL API를 사용하는 Cloud Service으로 사용하는 방법을 살펴볼 수 있습니다.
feature: 컨텐츠 조각,GraphQL API
exl-id: bdd60e7b-4ab9-4aa5-add9-01c1847f37f6
translation-type: tm+mt
source-git-commit: dab4c9393c26f5c3473e96fa96bf7ec51e81c6c5
workflow-type: tm+mt
source-wordcount: '3901'
ht-degree: 2%

---


# 컨텐츠 조각에 사용할 AEM GraphQL API {#graphql-api-for-use-with-content-fragments}

AEM(Adobe Experience Manager)의 컨텐츠 조각을 헤드리스 컨텐츠 전달을 위해 AEM GraphQL API를 사용하는 Cloud Service으로 사용하는 방법을 살펴볼 수 있습니다.

AEM은 컨텐츠 조각에 사용되는 Cloud Service GraphQL API로서 표준 오픈 소스 GraphQL API를 기반으로 합니다.

AEM에서 GraphQL API를 사용하면 헤드리스 CMS 구현에서 컨텐츠 조각을 JavaScript 클라이언트에 효율적으로 전달할 수 있습니다.

* REST와 같이 반복적인 API 요청 방지,
* 전달이 특정 요구 사항에 한정되어 있다는 것을 보장하는
* 단일 API 쿼리에 대한 응답으로 렌더링하는 데 필요한 내용을 정확하게 일괄적으로 전달할 수 있도록 허용합니다.

>[!NOTE]
>
>GraphQL은 현재 AEM(Adobe Experience Manager)의 두 가지(별도) 시나리오에서 Cloud Service으로 사용됩니다.
>
>* [AEM Commerce는 GraphQL을 통해 상거래 플랫폼의 데이터를 사용합니다](/help/commerce-cloud/integrating/magento.md).
>* AEM 컨텐츠 조각은 AEM GraphQL API(표준 GraphQL을 기반으로 사용자 정의된 구현)와 함께 작동하여 애플리케이션에서 사용할 수 있도록 구조화된 컨텐츠를 제공합니다.


## GraphQL API {#graphql-api}

GraphQL:

* &quot;*...API에 대한 쿼리 언어 및 기존 데이터와 관련 쿼리를 충족하는 런타임입니다. GraphQL은 API에 있는 데이터에 대한 완벽하고 이해할 수 있는 설명을 제공하며 고객에게 필요한 것과 더 이상 필요한 것을 정확하게 요청할 수 있는 기능을 제공하고 시간이 지남에 따라 API를 보다 쉽게 발전시켜 주며 강력한 개발자 도구를 활성화합니다.*&quot;

   [GraphQL.org](https://graphql.org) 참조

* &quot;*...유연한 API 레이어의 개방형 사양입니다. GraphQL을 기존 백엔드에 배치하여 보다 신속하게 제품을 구축할 수 있습니다..*&quot;

   [GraphQL 탐색](https://www.graphql.com)을 참조하십시오.

* *&quot;...2015년 공개적으로 오픈 소스로 배포되기 전에 Facebook이 2012년 내부적으로 개발한 데이터 쿼리 언어 및 사양입니다. 개발자 생산성을 높이고 데이터 전송 양을 최소화하기 위해 REST 기반 아키텍처에 대한 대체 요소를 제공합니다. GraphQL은 모든 규모의 수백 개의 조직에서 프로덕션에 사용됩니다...*

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

   * [튜토리얼](https://www.graphql.com/tutorials/)

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

>[!NOTE]
>[GraphiQL IDE](#graphiql-interface)를 사용하여 GraphQL 쿼리를 테스트하고 디버깅할 수 있습니다.

## AEM 끝점에 대한 GraphQL {#graphql-aem-endpoint}

끝점은 AEM용 GraphQL에 액세스하는 데 사용되는 경로입니다. 이 경로를 사용하여(또는 앱) 다음 작업을 수행할 수 있습니다.

* GraphQL 스키마 액세스,
* GraphQL 쿼리 보내기,
* GraphQL 쿼리에 대한 응답을 받습니다.

AEM에는 두 가지 유형의 끝점이 있습니다.

* 전역
   * 모든 사이트에서 사용할 수 있습니다.
   * 이 끝점은 모든 테넌트의 모든 콘텐츠 조각 모델을 사용할 수 있습니다.
   * 테넌트 간에 공유해야 하는 컨텐츠 조각 모델이 있는 경우 글로벌 테넌트 아래에 만들어야 합니다.
* 임차인:
   * [구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)에 정의된 테넌트 구성에 해당합니다.
   * 지정된 사이트/프로젝트에 따라 다릅니다.
   * 테넌트 특정 끝점은 글로벌 테넌트의 콘텐츠와 함께 특정 테넌트의 콘텐츠 조각 모델을 사용합니다.

>[!CAUTION]
>
>컨텐츠 조각 편집기는 특정 테넌트의 컨텐츠 조각이 정책을 통해 다른 테넌트의 컨텐츠 조각을 참조하도록 허용할 수 있습니다.
>
>이러한 경우 테넌트 특정 끝점을 사용하여 모든 콘텐츠를 검색할 수 없습니다.
>
>컨텐츠 작성자는 이 시나리오를 제어해야 합니다.예를 들어 글로벌 테넌트에 공유 컨텐츠 조각 모델을 배치하는 것이 유용할 수 있습니다.

AEM 전역 끝점에 대한 GraphQL의 리포지토리 경로는 다음과 같습니다.

`/content/cq:graphql/global/endpoint`

요청 URL에서 다음 경로를 사용할 수 있는 앱:

`/content/_cq_graphql/global/endpoint.json`

AEM용 GraphQL의 끝점을 활성화하려면 다음을 수행해야 합니다.

* [GraphQL 끝점 사용](#enabling-graphql-endpoint)
* [GraphQL 끝점 게시](#publishing-graphql-endpoint)

### GraphQL 끝점 활성화 {#enabling-graphql-endpoint}

GraphQL 끝점을 활성화하려면 먼저 적절한 구성이 있어야 합니다. [콘텐츠 조각 - 구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md)를 참조하십시오.

>[!CAUTION]
>
>[컨텐츠 조각 모델 사용이 활성화되지 않은](/help/assets/content-fragments/content-fragments-configuration-browser.md) 경우 **만들기** 옵션을 사용할 수 없습니다.

해당 끝점을 활성화하려면:

1. **도구**, **사이트**&#x200B;로 이동한 다음 **GraphQL**&#x200B;을 선택합니다.
1. **만들기**&#x200B;를 선택합니다.
1. **새 GraphQL 끝점 만들기** 대화 상자가 열립니다. 여기에서 다음을 지정할 수 있습니다.
   * **이름**:끝점의 이름;텍스트를 입력할 수 있습니다.
   * **GraphQL 스키마 사용**:드롭다운을 사용하여 필요한 사이트/프로젝트를 선택합니다.

   >[!NOTE]
   >
   >대화 상자에 다음 경고가 표시됩니다.
   >
   >* *GraphQL 엔드포인트는 신중하게 관리하지 않을 경우 데이터 보안 및 성능 문제를 초래할 수 있습니다. 엔드포인트를 만든 후 적절한 사용 권한을 설정했는지 확인하십시오.*


1. **만들기**&#x200B;로 확인합니다.
1. 새로 만든 끝점에 적절한 권한이 있는지 확인할 수 있도록 **다음 단계** 대화 상자에서 보안 콘솔에 대한 직접 링크를 제공합니다.

   >[!CAUTION]
   >
   >모든 사람이 끝점에 액세스할 수 있습니다. GraphQL 쿼리는 서버에 무거운 로드를 부과할 수 있으므로 특히 게시 인스턴스에서 보안상의 문제가 될 수 있습니다.
   >
   >종단점에서 사용 사례에 적합한 ACL을 설정할 수 있습니다.

### GraphQL 끝점 게시 중 {#publishing-graphql-endpoint}

모든 환경에서 사용할 수 있도록 하려면 새 끝점과 **게시**&#x200B;를 선택합니다.

>[!CAUTION]
>
>모든 사람이 끝점에 액세스할 수 있습니다.
>
>GraphQL 쿼리는 서버에 무거운 로드를 적용할 수 있으므로 게시 인스턴스에서는 보안 문제가 발생할 수 있습니다.
>
>종단점의 사용 사례에 적합한 ACL을 설정해야 합니다.

## 그래픽 QL 인터페이스 {#graphiql-interface}

AEM GraphQL에서 표준 [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) 인터페이스의 구현을 사용할 수 있습니다. AEM](#installing-graphiql-interface)과 함께 [설치할 수 있습니다.

이 인터페이스를 사용하면 쿼리를 직접 입력하고 테스트할 수 있습니다.

예:

* `http://localhost:4502/content/graphiql.html`

여기에는 내역 및 온라인 설명서와 함께 구문 강조, 자동 완성, 자동 제안 등의 기능이 제공됩니다.

![GraphiQL ](assets/cfm-graphiql-interface.png "인터페이스 그래픽QL 인터페이스")

### AEM GraphiQL 인터페이스 {#installing-graphiql-interface} 설치

GraphiQL 사용자 인터페이스는 전용 패키지와 함께 AEM에 설치할 수 있습니다.[GraphiQL 콘텐츠 패키지 v0.0.6(2021.3)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-graphql/graphiql-0.0.6.zip) 패키지.

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

1. 해당 GraphQL 스키마(GraphiQL 자동 설명서에서 출력):
   ![컨텐츠 조각 모델을 기반으로 하는 GraphQL ](assets/cfm-graphqlapi-02.png "스키마 컨텐츠 조각 모델 기반 QL 스키마")

   생성된 유형 `ArticleModel`에 여러 개의 [필드](#fields)가 포함되어 있음을 보여줍니다.

   * 이 중 3개는 사용자가 제어했습니다.`author`, `main` 및 `referencearticle`.

   * 다른 필드는 AEM에 의해 자동으로 추가되었으며 특정 컨텐츠 조각에 대한 정보를 제공하는 유용한 방법을 나타냅니다.이 예에서 `_path`, `_metadata`, `_variations`입니다. 이러한 [도우미 필드](#helper-fields)는 사용자가 정의한 항목과 자동 생성된 항목을 구별하기 위해 이전 `_`으로 표시됩니다.

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

### 스키마 생성 - 게시되지 않은 모델 {#schema-generation-unpublished-models}

컨텐츠 조각이 중첩되면 상위 컨텐츠 조각 모델이 게시되지만 참조된 모델은 게시되지 않을 수 있습니다.

>[!NOTE]
>
>AEM UI는 이러한 문제를 방지하지만 게시가 프로그래밍 방식으로 또는 콘텐츠 패키지로 이루어진 경우에는 발생할 수 있습니다.

이 경우 AEM은 상위 컨텐츠 조각 모델에 대한 *불완전한* 스키마를 생성합니다. 즉, 게시되지 않은 모델에 종속된 조각 참조가 스키마에서 제거됩니다.

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
| 단일 행 텍스트 | 문자열, [String] |  작성자 이름, 위치 이름 등과 같은 간단한 문자열에 사용됩니다. |
| 여러 줄 텍스트 | 문자열 |  아티클의 본문과 같은 텍스트를 출력하는 데 사용됩니다. |
| 번호 |  부동, [부동] | 부동 소수점 번호와 일반 숫자를 표시하는 데 사용됩니다. |
| 부울 |  부울 |  확인란→ 단순한 true/false 문을 표시하는 데 사용됩니다. |
| 날짜 및 시간 | 달력 |  날짜와 시간을 ISO 8086 형식으로 표시하는 데 사용됩니다. 선택한 유형에 따라 AEM GraphQL에서 사용할 수 있는 3가지 방식이 있습니다.`onlyDate`, `onlyTime`, `dateTime` |
| 열거 |  String |  모델 생성 시 정의된 옵션 목록에서 옵션을 표시하는 데 사용됩니다. |
|  태그 |  [String] |  AEM에서 사용되는 태그를 나타내는 문자열 목록을 표시하는 데 사용됩니다. |
| 컨텐츠 참조 |  문자열 |  AEM에서 다른 에셋에 대한 경로를 표시하는 데 사용됩니다. |
| 조각 참조 |  *모델 유형* |  모델이 생성될 때 정의된 특정 모델 유형의 다른 컨텐츠 조각을 참조하는 데 사용됩니다. |

### 도우미 필드 {#helper-fields}

AEM용 GraphQL은 사용자 생성 필드에 대한 데이터 유형 외에도 컨텐츠 조각을 식별하거나 컨텐츠 조각에 대한 추가 정보를 제공하기 위해 많은 *helper* 필드도 생성합니다.

#### 경로 {#path}

경로 필드는 GraphQL에서 식별자로 사용됩니다. AEM 저장소 내의 컨텐츠 조각 자산의 경로를 나타냅니다. 다음 이유로 컨텐츠 조각 식별자로 선택했습니다.

* AEM 내에서 고유하며
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

GraphQL은 쿼리에 변수를 배치할 수 있도록 허용합니다. 자세한 내용은 변수](https://graphql.org/learn/queries/#variables)에 대한 [GraphQL 설명서를 참조하십시오.

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

* AEM 확장의 [GraphQL 세부 사항](#graphql-extensions)

* [이 샘플 컨텐츠 및 구조를 사용한 샘플 쿼리](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

   * 그리고 샘플 쿼리에 사용할 수 있도록 준비된 [샘플 컨텐트 및 구조](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)

* [WKND 프로젝트를 기반으로 하는 샘플 쿼리](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## AEM용 GraphQL - 익스텐션 요약 {#graphql-extensions}

AEM용 GraphQL을 사용하는 쿼리의 기본 작업은 표준 GraphQL 사양을 따릅니다. AEM과 함께 GraphQL 쿼리에 사용할 수 있는 확장 기능은 다음과 같습니다.

* 단일 결과가 필요한 경우:
   * 모델 이름 사용;eg city

* 결과 목록이 필요한 경우:
   * 모델 이름에 `List` 추가;예를 들어 `cityList`
   * [샘플 쿼리 - 모든 도시에 대한 모든 정보](#sample-all-information-all-cities)를 참조하십시오.

* 논리 OR을 사용하려면:
   * ` _logOp: OR` 사용
   * [샘플 쿼리 - &quot;Job&quot; 또는 &quot;Smith&quot;](#sample-all-persons-jobs-smith)의 이름을 가진 모든 사람을 참조하십시오.

* 논리 AND도 존재하지만 (종종) 암시적

* 컨텐츠 조각 모델 내의 필드에 해당하는 필드 이름을 쿼리할 수 있습니다
   * [샘플 쿼리 - 회사의 CEO 및 직원의 전체 세부 정보](#sample-full-details-company-ceos-employees)를 참조하십시오.

* 모델의 필드 외에도 몇 가지 시스템 생성 필드가 있습니다(앞에 밑줄 표시).

   * 컨텐츠의 경우:

      * `_locale` :언어를 공개하려면;Language Manager 기반
         * 지정된 로케일의 여러 콘텐츠 조각에 대한 [샘플 쿼리를 참조하십시오](#sample-wknd-multiple-fragments-given-locale)
      * `_metadata` :조각에 대한 메타데이터를 표시하려면
         * [메타데이터에 대한 샘플 쿼리 - 제목이 GB](#sample-metadata-awards-gb)인 시상식에 대한 메타데이터 목록을 참조하십시오.
      * `_model` :컨텐츠 조각 모델 쿼리 허용(경로 및 제목)
         * 모델](#sample-wknd-content-fragment-model-from-model)의 컨텐츠 조각 모델에 대한 [샘플 쿼리를 참조하십시오.
      * `_path` :저장소 내 컨텐츠 조각 경로
         * [샘플 쿼리 - 단일 특정 도시 조각](#sample-single-specific-city-fragment) 참조
      * `_reference` :참조를 표시합니다.리치 텍스트 편집기에서 인라인 참조 포함
         * 프리페치된 참조](#sample-wknd-multiple-fragments-prefetched-references)가 있는 여러 컨텐츠 조각에 대한 샘플 쿼리를 참조하십시오.[
      * `_variation` :컨텐츠 조각 내에서 특정 변형을 표시하려면
         * [샘플 쿼리 - 명명된 변화가 있는 모든 도시](#sample-cities-named-variation)를 참조하십시오.
   * 작업:

      * `_operator` :특정 연산자 적용 `EQUALS`,  `EQUALS_NOT`,  `GREATER_EQUAL`,  `LOWER`, `CONTAINS`  `STARTS_WITH`
         * [샘플 쿼리 - &quot;작업&quot; 이름이 없는 모든 사람](#sample-all-persons-not-jobs)을 참조하십시오.
         * `_path`이(가) 특정 접두어](#sample-wknd-all-adventures-cycling-path-filter)로 시작하는 [샘플 쿼리 - 모든 모험을 참조하십시오.
      * `_apply` :특정 조건을 적용하는 경우예를 들어   `AT_LEAST_ONCE`
         * [샘플 쿼리 - 하나 이상 발생해야 하는 항목이 있는 배열에 대해 필터를 참조하십시오](#sample-array-item-occur-at-least-once)
      * `_ignoreCase` :쿼리 시 대/소문자를 무시하려면
         * [샘플 쿼리 - 대소문자](#sample-all-cities-san-ignore-case)에 관계없이 이름에 SAN이 있는 모든 도시 참조









* GraphQL 결합 유형은 다음과 같이 지원됩니다.

   * `... on` 사용
      * 내용 참조가 있는 특정 모델의 컨텐츠 조각에 대한 [샘플 쿼리를 참조하십시오](#sample-wknd-fragment-specific-model-content-reference)

## 지속적인 쿼리(캐싱) {#persisted-queries-caching}

POST 요청을 사용하여 쿼리를 준비한 후 HTTP 캐시 또는 CDN을 통해 캐싱할 수 있는 GET 요청을 사용하여 실행할 수 있습니다.

POST 쿼리는 일반적으로 캐시되지 않으며, 쿼리와 함께 GET을 매개 변수로 사용하는 경우 매개 변수가 HTTP 서비스 및 중계기에 너무 많이 사용되면 위험합니다.

지속적인 쿼리는 항상 [적절한(테넌트) 구성](#graphql-aem-endpoint);과 관련된 끝점을 사용해야 합니다.둘 중 하나 또는 둘 다를 사용할 수 있습니다.

* 전역 구성 및 끝점
쿼리는 모든 컨텐츠 조각 모델에 액세스할 수 있습니다.
* 특정 테넌트 구성 및 끝점
특정 테넌트 구성에 대해 지속적인 쿼리를 만들려면 해당 임차인 특정 끝점이 필요합니다(관련 컨텐츠 조각 모델에 대한 액세스 제공).
예를 들어 WKND 테넌트에 대한 지속적인 쿼리를 만들려면 해당 WKND 관련 테넌트 구성과 WKND 특정 끝점을 미리 만들어야 합니다.

>[!NOTE]
>
>자세한 내용은 [구성 브라우저에서 컨텐츠 조각 기능 활성화](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)를 참조하십시오.
>
>해당 테넌트 구성에 대해 **GraphQL 지속성 쿼리**&#x200B;를 활성화해야 합니다.

예를 들어 테넌트 구성 `my-conf`의 모델 `my-model`을 사용하는 `my-query`이라는 특정 쿼리가 있는 경우:

* `my-conf` 특정 끝점을 사용하여 쿼리를 만들면 쿼리는 다음과 같이 저장됩니다.
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* `global` 끝점을 사용하여 동일한 쿼리를 만들 수 있지만 쿼리는 다음과 같이 저장됩니다.
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>서로 다른 경로 아래에 저장된 두 개의 서로 다른 쿼리입니다.
>
>이러한 모델은 동일한 모델을 사용하지만 다른 끝점을 통해 사용됩니다.


지정된 쿼리를 유지하는 데 필요한 단계는 다음과 같습니다.

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

외부 웹 사이트에서 GraphQL 끝점에 액세스하려면 다음을 구성해야 합니다.

* [CORS 필터](#cors-filter)
* [레퍼러 필터](#referrer-filter)

### CORS 필터 {#cors-filter}

>[!NOTE]
>
>AEM의 CORS 리소스 공유 정책에 대한 자세한 개요는 [CORS(교차 도메인 리소스 공유)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=en#understand-cross-origin-resource-sharing-(cors))를 참조하십시오.

GraphQL 끝점에 액세스하려면 고객 Git 리포지토리에 CORS 정책을 구성해야 합니다. 이 작업은 원하는 끝점에 대해 적절한 OSGi CORS 구성 파일을 추가하여 수행합니다.

이 구성은 액세스 권한을 부여해야 하는 신뢰할 수 있는 웹 사이트 원본 `alloworigin` 또는 `alloworiginregexp`을 지정해야 합니다.

예를 들어 GraphQL 끝점과 `https://my.domain`에 대한 지속적인 쿼리 끝점에 대한 액세스 권한을 부여하려면 다음을 사용할 수 있습니다.

```xml
{
  "supportscredentials":true,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/_cq_graphql/global/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

끝점에 대한 별칭 경로를 구성한 경우 `allowedpaths`에서도 사용할 수 있습니다.

### 레퍼러 필터 {#referrer-filter}

CORS 구성 외에도 레퍼러 필터를 구성하여 제3자 호스트에 대한 액세스를 허용해야 합니다.

이 작업은 다음과 같은 적절한 OSGi 레퍼러 필터 구성 파일을 추가하여 수행합니다.

* 신뢰할 수 있는 웹 사이트 호스트 이름을 지정합니다.`allow.hosts` 또는 `allow.hosts.regexp`,
* 이 호스트 이름에 대한 액세스 권한을 부여합니다.

예를 들어 레퍼러 `my.domain`의 요청에 대한 액세스 권한을 부여하려면 다음을 수행할 수 있습니다.

```xml
{
    "allow.empty":false,
    "allow.hosts":[
      "my.domain"
    ],
    "allow.hosts.regexp":[
      ""
    ],
    "filter.methods":[
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp":[
      ""
    ]
}
```

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
