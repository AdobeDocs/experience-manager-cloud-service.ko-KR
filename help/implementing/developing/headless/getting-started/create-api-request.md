---
title: 헤드리스 빠른 시작 가이드 컨텐츠 조각 액세스 및 전달
description: 자산 REST API를 사용하면 컨텐츠 조각을 관리할 수 있으며 GraphQL API를 통해 컨텐츠 조각 컨텐츠를 헤드리스(heads-less) 배달할 수 있습니다.
translation-type: tm+mt
source-git-commit: 7ed96dc0da879800d731983a0399b4f4fb3d7d41
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---


# 콘텐츠 조각 액세스 및 제공 헤드리스 빠른 시작 안내서 {#accessing-delivering-content-fragments}

자산 REST API를 사용하면 컨텐츠 조각을 관리할 수 있으며 GraphQL API를 통해 컨텐츠 조각 컨텐츠를 헤드리스(heads-less) 배달할 수 있습니다.

## GraphQL 및 자산 REST API란 무엇입니까?{#what-are-the-apis}

[일부 컨텐츠 조각을 생성했으므로 AEM API를 사용하여 ](create-content-fragment.md) 헤드라인으로 전달할 수 있습니다.

* [GraphQL ](/help/assets/content-fragments/graphql-api-content-fragments.md) API를 사용하면 컨텐츠 조각에 액세스하고 전달할 요청을 만들 수 있습니다.
* [자산 REST ](/help/assets/content-fragments/assets-api-content-fragments.md) API를 사용하여 컨텐츠 조각(및 기타 자산)을 만들고 수정할 수 있습니다.

이 안내서의 나머지 부분에서는 GraphQL 액세스 및 컨텐츠 조각 전달에 중점을 둡니다.

## GraphQL {#how-to-deliver-a-content-fragment}을(를) 사용하여 컨텐츠 조각을 제공하는 방법

정보 설계자는 컨텐츠를 제공하기 위해 채널 끝점에 대한 쿼리를 설계해야 합니다. 이러한 쿼리는 일반적으로 모델당 종단점당 한 번만 고려되어야 합니다. 이 시작 가이드의 목적을 위해 Adobe는 가이드를 제작하기만 하면 됩니다.

1. AEM에 Cloud Service으로 로그인하고 주 메뉴에서 **도구 -> 자산 -> GraphQL**&#x200B;을 선택합니다.
   * 또는 `https://<host>:<port>/content/graphiql.html`에서 페이지를 직접 엽니다.

1. GraphiQL은 GraphQL에 대한 브라우저 내 쿼리 편집기입니다. 쿼리를 작성하여 콘텐츠 조각을 JSON으로 간편하게 전달할 수 있습니다.
   * 왼쪽 패널에서 쿼리를 작성할 수 있습니다.
   * 오른쪽 패널에 결과가 표시됩니다.
   * 쿼리 편집기는 쿼리를 쉽게 실행하기 위한 코드 완성 및 핫키를 제공합니다.
      ![GraphiQL 편집기](../assets/graphiql.png)

1. 우리가 만든 모델을 필드 `firstName`, `lastName` 및 `position`과(와) 함께 `person`이라고 가정할 경우, 간단한 쿼리를 작성하여 컨텐츠 조각의 컨텐츠를 검색할 수 있습니다.

   ```
   query {
     persons {
       items {
         _path
         firstName
         lastName
         position
       }
     }
   }
   ```

1. 왼쪽 패널에 쿼리를 입력합니다.
   ![GraphiQL 쿼리](../assets/graphiql-query.png)

1. **쿼리 실행** 단추를 클릭하거나 `Ctrl-Enter` 핫키를 사용하면 결과가 오른쪽 패널에 JSON으로 표시됩니다.
   ![GraphiQL 결과](../assets/graphiql-results.png)

1. 페이지 오른쪽 상단에 있는 **Docs** 링크를 클릭하여 자체 모델에 맞는 쿼리를 작성하는 데 도움이 되는 in-context 설명서를 표시합니다.
   ![GraphiQL 설명서](../assets/graphiql-documentation.png)

GraphQL은 특정 데이터 세트 또는 개별 데이터 객체뿐만 아니라 객체의 특정 요소, 중첩된 결과, 쿼리 변수에 대한 지원 등을 제공할 수 있는 구조화된 쿼리를 활성화합니다.

GraphQL은 반복적인 API 요청과 과잉 전달을 방지할 수 있으며 대신 단일 API 쿼리에 대한 응답으로 렌더링하는 데 필요한 정확한 내용을 대량 배달할 수 있습니다. 결과 JSON을 사용하여 데이터를 다른 사이트 또는 앱에 제공할 수 있습니다.

## 다음 단계 {#next-steps}

바로 그거야! 이제 AEM에서 헤드리스 컨텐츠 관리에 대한 기본적인 이해가 필요합니다. 물론 이용 가능한 기능에 대한 포괄적인 이해를 위해 더 자세히 살펴볼 수 있는 다양한 리소스가 있습니다.

* **구성 브라우저**  - AEM 구성 브라우저에 대한 자세한 정보
* **[컨텐츠 조각](/help/assets/content-fragments/content-fragments.md)**  - 컨텐츠 조각 만들기 및 관리에 대한 자세한 내용
* **[AEM Assets HTTP API의 컨텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)**  - CRUD 작업을 통해 HTTP API를 통해 직접 AEM 컨텐츠에 액세스하는 방법에 대한 자세한 내용(만들기, 읽기, 업데이트, 삭제)
* **[GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)**  - 콘텐츠 조각을 헤드없이 제공하는 방법에 대한 자세한 내용
