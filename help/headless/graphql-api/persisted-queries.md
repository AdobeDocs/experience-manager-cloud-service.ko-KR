---
title: 지속 GraphQL 쿼리
description: 성능을 최적화하기 위해 Adobe Experience Manager as a Cloud Service에서 GraphQL 쿼리를 지속하는 방법을 알아봅니다. HTTP GET 메서드를 사용하여 클라이언트 애플리케이션에서 지속 쿼리를 요청할 수 있으며 응답을 Dispatcher 및 CDN 계층에서 캐시할 수 있으므로 궁극적으로 클라이언트 애플리케이션의 성능이 향상됩니다.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 368c2d537d740b2126aa7cce657ca54f7ad6b329
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 94%

---

# 지속 GraphQL 쿼리 {#persisted-queries-caching}

지속 쿼리는 Adobe Experience Manager(AEM) as a Cloud Service 서버에서 생성 및 저장되는 GraphQL 쿼리입니다. 클라이언트 애플리케이션에서 GET 요청을 사용하여 요청할 수 있습니다. GET 요청의 응답은 Dispatcher 및 CDN 계층에서 캐시될 수 있으므로 궁극적으로 요청하는 애플리케이션의 성능이 향상됩니다. 이 경우 응답을 쉽게 캐시할 수 없는 POST 요청을 사용하여 실행되는 표준 GraphQL 쿼리와는 다릅니다.

>[!NOTE]
>
>지속되는 쿼리를 사용하는 것이 좋습니다. 자세한 내용은 [GraphQL 쿼리 우수 사례(Dispatcher)](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) 자세한 내용 및 관련 Dispatcher 구성을 참조하십시오.

다음 [GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md) GraphQL 쿼리를 개발, 테스트 및 유지할 수 있도록 AEM에서 이 기능을 사용할 수 있습니다. [프로덕션 환경으로 전송](#transfer-persisted-query-production). 맞춤화가 필요한 경우(예: [캐시를 사용자 지정](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)하는 경우) API를 사용할 수 있습니다. [GraphQL 쿼리를 지속하는 방법](#how-to-persist-query)에 제시된 curl 예제를 참조하십시오.

## 지속 쿼리 및 끝점 {#persisted-queries-and-endpoints}

지속 쿼리는 항상 [적절한 Sites 구성](graphql-endpoint.md)과 관련된 끝점을 사용해야 합니다. 따라서 다음 중 하나 또는 둘 다를 사용할 수 있습니다.

* 전역 구성 및 끝점
쿼리는 모든 콘텐츠 조각 모델에 액세스할 수 있습니다.
* 특정 Sites 구성 및 끝점
특정 Sites 구성에 대한 지속 쿼리를 만들려면 (관련 콘텐츠 조각 모델에 대한 액세스를 제공하기 위해) 해당 Sites 구성별 끝점이 필요합니다.
예를 들어 WKND Sites 구성을 위해 특별히 지속 쿼리를 만들려면 해당 WKND별 Sites 구성 및 WKND별 끝점을 미리 만들어야 합니다.

>[!NOTE]
>
>자세한 내용은 [구성 브라우저에서 콘텐츠 조각 기능 활성화](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)를 참조하십시오.
>
>적절한 Sites 구성을 위해 **GraphQL 지속 쿼리**&#x200B;를 활성화해야 합니다.

예를 들어 Sites 구성 `my-conf`의 모델 `my-model`을 사용하는 `my-query`라는 특정 쿼리가 있는 경우:

* `my-conf` 특정 끝점을 사용하여 쿼리를 만들 수 있으며 쿼리는 다음과 같이 저장됩니다.
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* `global` 끝점을 사용하여 동일한 쿼리를 생성할 수 있지만 쿼리는 다음과 같이 저장됩니다.
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>이 쿼리들을 서로 다른 경로에 저장된 두 개의 서로 다른 쿼리입니다.
>
>동일한 모델을 사용하기는 하지만 다른 끝점을 통해 발생합니다.

## GraphQL 쿼리를 지속하는 방법 {#how-to-persist-query}

처음에 AEM 작성 환경에서 쿼리를 지속한 다음 프로덕션 AEM 게시 환경에 [쿼리를 전송](#transfer-persisted-query-production)하여 애플리케이션에서 사용하는 것이 좋습니다.

다양한 방법으로 쿼리를 지속합니다(다음 포함).

* GraphiQL IDE - [지속 쿼리 저장](/help/headless/graphql-api/graphiql-ide.md##saving-persisted-queries) 참조
* curl - 다음 예제 참조
* 기타 도구, [Postman](https://www.postman.com/) 포함

**curl** 명령줄 도구를 사용하여 주어진 쿼리를 지속하는 단계는 다음과 같습니다.

1. 쿼리를 새 끝점 URL `/graphql/persist.json/<config>/<persisted-label>`에 PUT하여 준비합니다.

   예를 들어 지속 쿼리를 만듭니다.

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

1. 이 시점에서 응답을 확인합니다.

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

1. 그런 다음 URL `/graphql/execute.json/<shortPath>`을 GET하여 지속 쿼리를 요청할 수 있습니다.

   예를 들어 지속 쿼리를 사용합니다.

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. 이미 존재하는 쿼리 경로에 POST하여 지속 쿼리를 업데이트합니다.

   예를 들어 지속 쿼리를 사용합니다.

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

1. 캐시 제어를 사용하여 래핑된 일반 쿼리를 만듭니다.

   예:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. 매개 변수를 사용하여 지속 쿼리를 만듭니다.

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

1. 매개 변수를 사용하여 쿼리를 실행합니다.

   예:

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   
   $ curl -X GET \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   ```

## 프로덕션 환경에 지속 쿼리 전송 중  {#transfer-persisted-query-production}

궁극적으로 지속 쿼리는 클라이언트 애플리케이션에서 요청할 수 있는 (AEM as a Cloud Service의) 프로덕션 게시 환경에 존재해야 합니다. 프로덕션 게시 환경에서 지속 쿼리를 사용하려면 관련 지속 트리가 복제되어야 합니다.

* 처음은 쿼리로 새로 작성된 콘텐츠를 확인하기 위해 프로덕션 작성자로 복제되고,
* 마지막은 라이브 소비를 위해 프로덕션 게시로 복제됩니다.

지속 쿼리를 전송하는 방법에는 여러 가지가 있습니다.

1. 패키지 사용:
   1. 새 패키지 정의를 만듭니다.
   1. 구성을 포함합니다(예: `/conf/wknd/settings/graphql/persistentQueries`).
   1. 패키지를 빌드합니다.
   1. 패키지를 전송(다운로드/업로드 또는 복제)합니다.
   1. 패키지를 설치합니다.

1. 복제를 위해 POST 사용:

   ```xml
   $ curl -X POST   http://localhost:4502/bin/replicate.json \
   -H 'authorization: Basic YWRtaW46YWRtaW4=' \
   -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
   -F cmd=activate
   ```

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->

쿼리 구성이 프로덕션의 게시 환경에 존재하면 동일한 인증 원칙이 게시 끝점을 사용하기만 하여 적용됩니다.

>[!NOTE]
>
>익명 액세스의 경우 시스템은 ACL에서 “모든 사용자”가 쿼리 구성에 액세스할 수 있도록 허용한다고 가정합니다.
>
>그렇지 않은 경우 실행이 불가능합니다.

## 앱에서 사용하기 위해 쿼리 URL 인코딩 {#encoding-query-url}

애플리케이션에서 사용하기 위해 URL에 있는 모든 세미콜론(“;”)은 인코딩해야 합니다.

예를 들어 지속 쿼리 실행 요청에서처럼:

```xml
curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
```

클라이언트 앱에서 지속 쿼리를 사용하려면 AEM Headless 클라이언트 SDK는 [JavaScript용 AEM Headless Client](https://github.com/adobe/aem-headless-client-js)를 사용해야 합니다.