---
title: AEM에서 GraphiQL IDE 사용
description: Adobe Experience Manager에서 GraphiQL IDE를 사용하는 방법을 알아봅니다.
feature: Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
source-git-commit: 5f0221fad6086f8d5c5e9bd5164d05ea8d6e7d2c
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 98%

---

# GraphiQL IDE 사용 {#graphiql-ide}

표준 [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE의 구현은 Adobe Experience Manager(AEM) as a Cloud Service의 GraphQL API와 함께 사용할 수 있습니다.

>[!NOTE]
>
>이 기능 중 일부는 프리릴리스 채널에서 사용할 수 있습니다. 특히 지속 쿼리와 관련된 기능이 사용될 수 있습니다.
> 
>환경에 맞는 기능을 활성화하는 방법에 대한 자세한 내용은 [프리릴리스 채널 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease)를 참조하십시오.

>[!NOTE]
>
>GraphiQL이 AEM에 포함되지만 기본적으로 `dev-authors` 환경에서만 활성화됩니다.

>[!NOTE]
>GraphiQL IDE를 사용하기 전에 [구성 브라우저](/help/assets/content-fragments/content-fragments-configuration-browser.md)에서 [끝점을 구성](/help/headless/graphql-api/graphql-endpoint.md)해야 합니다.


**GraphiQL** 도구를 통해 다음 작업을 수행하여 GraphQL 쿼리를 테스트하고 디버그할 수 있습니다.
* 쿼리에 사용하려는 Sites 구성에 적합한 **끝점**&#x200B;을 선택합니다.
* 새 쿼리 직접 입력
* **[지속 쿼리](/help/headless/graphql-api/persisted-queries.md)** 제작 및 액세스
* 바로 결과를 조회하기 위해 쿼리 실행
* **쿼리 변수** 관리
* **지속 쿼리** 저장 및 관리
* **지속 쿼리** 게시 또는 게시 취소(`dev-publish`에/에서)
* 이전 쿼리의 **내역** 참조
* **설명서 탐색기**&#x200B;를 사용하여 설명서에 액세스합니다. 이를 통해 사용 가능한 방법을 쉽게 배우고 이해할 수 있습니다.

다음 중 하나에서 쿼리 편집기에 액세스할 수 있습니다.

* **도구** -> **일반** -> **GraphQL 쿼리 편집기**
* 직접 예 `http://localhost:4502/aem/graphiql.html`

![GraphiQL 인터페이스](assets/cfm-graphiql-interface.png "GraphiQL 인터페이스")

GET 요청을 사용하고 쿼리를 게시하여 클라이언트 애플리케이션에서 요청할 수 있도록 개발 제작자 시스템에서 GraphiQL을 사용할 수 있습니다. 프로덕션을 사용하는 경우 [쿼리를 프로덕션 환경으로 이전](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production)해야 합니다. 처음은 쿼리로 새로 작성된 콘텐츠를 확인하기 위해 프로덕션 작성자로 복제되고, 마지막은 라이브 소비를 위해 프로덕션 게시로 복제됩니다.

## 끝점 선택 중 {#selecting-endpoint}

첫 번째 단계로, 쿼리에 사용하려는 Sites 구성에 적합한 **[끝점](/help/headless/graphql-api/graphql-endpoint.md)**&#x200B;을 선택해야 합니다. 끝점은 쿼리에 사용하려는 Sites 구성에 적합합니다.

오른쪽 상단의 드롭다운 목록에서 사용할 수 있습니다.

## 새 쿼리 제작 및 지속 중 {#creating-new-query}

GraphiQL 로고 바로 아래 왼쪽 중간 패널에 있는 편집기에 새 쿼리를 입력할 수 있습니다.

>[!NOTE]
>
>이미 지속 쿼리가 선택되고 편집기 패널에 표시되는 경우 (**지속 쿼리** 옆의) `+`를 선택하여 새 쿼리에 맞는 편집기를 비웁니다.

입력이 시작되기만 하면 편집기는 다음 작업을 수행합니다.

* 마우스 오버를 사용하여 요소에 대한 추가 정보 표시
* 구문 강조, 자동 완성, 자동 제안 등의 기능 제공

>[!NOTE]
>
>GraphQL 쿼리는 일반적으로 `{` 문자로 시작됩니다.
>
>`#`으로 시작되는 라인은 무시됩니다.

**다른 이름으로 저장**&#x200B;을 사용하여 새 쿼리를 지속합니다.

## 지속 쿼리 업데이트 중 {#updating-persisted-query}

**지속 쿼리** 패널(맨 왼쪽)의 목록에서 업데이트하려는 쿼리를 선택합니다.

쿼리가 편집기 패널에 표시됩니다. 필요한 변경 내용을 적용한 다음 **저장**&#x200B;을 사용하여 지속 쿼리에 맞게 업데이트를 커밋합니다.

## 쿼리 실행 중 {#running-queries}

새 쿼리를 바로 실행하거나 지속 쿼리를 로드하고 실행할 수 있습니다. 지속 쿼리를 로드하는 경우 목록에서 선택하면 쿼리가 편집기 패널에 표시됩니다.

두 경우 모두 편집기 패널에 표시되는 쿼리는 다음 두 가지 작업을 수행하는 경우 실행되는 쿼리입니다.

* **쿼리 실행** 아이콘 클릭/탭
* 키보드 조합 `Control-Enter` 사용

## 쿼리 변수 {#query-variables}

<!-- more details needed here? -->

GraphiQL IDE를 사용하여 [쿼리 변수](/help/headless/graphql-api/content-fragments.md#graphql-variables)를 관리할 수 있습니다.

예:

![GraphQL 변수](assets/cfm-graphqlapi-03.png "GraphQL 변수")

## 지속 쿼리 게시 중(개발-게시) {#publishing-persisted-queries}

목록(왼쪽 패널)에서 지속 쿼리가 선택되면 **게시** 및 **게시 취소** 액션을 사용할 수 있습니다. 테스트할 때 애플리케이션에서 간편하게 액세스할 수 있도록 개발 게시 환경(`dev-publish`)에 맞게 액션을 활성화합니다.

>[!NOTE]
>
>지속 쿼리의 캐시 `Time To Live` {&quot;cache-control&quot;:&quot;parameter&quot;:value} 기본값은 2시간(7,200초)입니다.

## 지속 쿼리 캐싱 중 {#caching-persisted-queries}

AEM은 기본 TTL(Time to Live)에 따라 CDN(Content Delivery Network) 캐시를 무효화할 수 있습니다.

이 값을 다음으로 설정:

* Dispatcher 및 CDN(*공유 캐시*&#x200B;로도 알려짐)의 기본 TTL은 7,200초입니다.
   * 기본: s-maxage=7200
* 클라이언트(예: 브라우저)의 기본 TTL은 60초입니다.
   * 기본: maxage=60

GraphiQL UI로 지속되었던 AEM GraphQL 쿼리는 실행 시 기본 TTL을 사용합니다. GraphLQ 쿼리의 TTL을 변경하려는 경우 API 메서드를 사용하여 쿼리를 지속해야 합니다. 이는 명령줄 인터페이스의 CURL을 사용하여 AEM에 쿼리를 게시하는 것과 관련되어 있습니다.

예:

```xml
curl -X PUT \
    -H 'authorization: Basic YWRtaW46YWRtaW4=' \
    -H "Content-Type: application/json" \
    "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
    -d \
'{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
```

`cache-control`은 생성 시간(PUT) 또는 그 이후에 설정될 수 있습니다(예: 인스턴스의 POST 요청을 통해 설정). AEM에서 기본값을 제공하기 때문에 지속 쿼리 생성 시 캐시 제어는 선택 사항입니다. CURL을 사용하여 쿼리를 지속하는 사례는 [GraphQL 쿼리를 지속하는 방법](/help/headless/graphql-api/persisted-queries.md#how-to-persist-query)을 참조하십시오.

## URL을 복사하여 쿼리에 직접 액세스합니다. {#copy-url}

**URL 복사** 옵션을 통해 지속 쿼리에 직접 액세스하고 결과를 조회하는 데 사용되는 URL을 복사하여 쿼리를 시뮬레이션할 수 있습니다. 그런 다음 테스트에 사용할 수 있습니다(예: 브라우저에서 액세스).

<!--
  >[!NOTE]
  >
  >The URL will need [encoding before using programmatically](/help/headless/graphql-api/persisted-queries.md#encoding-query-url).
  >
  >The target environment might need adjusting, depending on your requirements.
-->

예:

`http://localhost:4502/graphql/execute.json/global/article-list-01`

브라우저에서 이 URL을 사용하여 다음 결과를 확인할 수 있습니다.

![GraphiQL - URL 복사](assets/cfm-graphiql-copy-url.png "GraphiQL - URL 복사")

지속 쿼리 이름(맨 왼쪽 패널) 오른쪽에 있는 세 개의 세로 점을 통해 **URL 복사** 옵션에 액세스할 수 있습니다.

![GraphiQL - URL 복사](assets/cfm-graphiql-persisted-query-options.png "GraphiQL - URL 복사")

## 지속 쿼리 삭제 중 {#deleting-persisted-queries}

지속 쿼리 이름(맨 왼쪽 패널) 오른쪽에 있는 세 개의 세로 점을 통해서도 **삭제** 옵션에 액세스할 수 있습니다.

<!-- what happens if you try to delete something that is still published? -->


## 프로덕션에 지속 쿼리 설치 중 {#installing-persisted-query-production}

GraphiQL로 지속 쿼리를 개발 및 테스트하고 나서 [프로덕션 환경으로 이전](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production)하여 애플리케이션에서 활용하는 것이 이 작업의 최종 목표입니다.

## 키보드 단축키 {#keyboard-shortcuts}

IDE에서 작업 아이콘에 직접 액세스하는 키보드 단축키의 선택 항목은 다음과 같습니다.

* 쿼리 정렬: `Shift-Control-P`
* 쿼리 병합: `Shift-Control-M`
* 쿼리 실행: `Control-Enter`
* 자동 완성: `Control-Space`

>[!NOTE]
>
>키보드에서 `Control` 키가 `Ctrl`로 레이블이 지정됩니다.
