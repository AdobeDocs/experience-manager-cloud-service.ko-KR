---
title: 지속된 GraphQL 쿼리
description: Adobe Experience Manager에서 GraphQL 쿼리를 유지하여 성능을 최적화하는 방법을 알아봅니다. HTTP GET 방법을 사용하여 클라이언트 응용 프로그램에서 지속되는 쿼리를 요청할 수 있으며 이 응답을 디스패처 및 CDN 레이어에서 캐시할 수 있으므로, 궁극적으로 클라이언트 응용 프로그램의 성능을 향상시킬 수 있습니다.
feature: Content Fragments,GraphQL API
source-git-commit: 0912cadeae13050c9cfc606d1c2b8f4236cd78ed
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 1%

---


# 지속된 GraphQL 쿼리 {#persisted-queries-caching}

지속되는 쿼리는 AEM 서버에 만들고 저장하는 GraphQL 쿼리입니다. 표준 GraphQL 쿼리는 POST 요청을 사용하여 실행되며 응답을 쉽게 캐시할 수 없습니다. 클라이언트 응용 프로그램의 GET 요청을 사용하여 지속되는 쿼리를 요청할 수 있습니다. 디스패처 및 CDN 레이어에서 GET 요청의 응답을 캐시할 수 있으므로, 궁극적으로 요청하는 클라이언트 애플리케이션의 성능을 향상시킬 수 있습니다.

지속형 쿼리는 항상 [적절한 사이트 구성](graphql-endpoint.md); 둘 중 하나 또는 둘 다 사용할 수 있습니다.

* 전역 구성 및 엔드포인트 쿼리는 모든 컨텐츠 조각 모델에 액세스할 수 있습니다.
* 특정 사이트 구성 및 끝점 특정 사이트 구성에 대해 지속적인 쿼리를 만들려면 관련 사이트 구성 관련 엔드포인트가 필요합니다(관련 컨텐츠 조각 모델에 대한 액세스 권한을 제공).
예를 들어 WKND Sites 구성을 위해 특별히 지속된 쿼리를 만들려면 해당 WKND별 Sites 구성 및 WKND별 종단점을 미리 만들어야 합니다.

>[!NOTE]
>
>자세한 내용은 [구성 브라우저에서 컨텐츠 조각 기능 활성화](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) 자세한 내용
>
>다음 **GraphQL 지속성 쿼리** 적절한 사이트 구성에 대해 를 활성화해야 합니다.

예를 들어 `my-query`- 모델을 사용합니다 `my-model` 사이트 구성에서 `my-conf`:

* 을 사용하여 쿼리를 만들 수 있습니다 `my-conf` 특정 종단점 및 다음과 같이 쿼리가 저장됩니다.
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* 을 사용하여 동일한 쿼리를 만들 수 있습니다 `global` 엔드포인트. 그러면 다음과 같이 쿼리가 저장됩니다.
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>이 두 쿼리는 서로 다른 경로에 저장됩니다.
>
>우연히 동일한 모델을 사용하지만 다른 끝점을 통해 사용됩니다.

## GraphQL 쿼리를 유지하는 방법

처음에 AEM 작성 환경에서 쿼리를 유지한 다음 [쿼리 게시](#publish-persisted-query) AEM 게시 환경에 매핑해야 합니다. 과 같은 도구 [포스트맨](https://www.postman.com/) 또는 [curl](https://curl.se/) 사용할 수 있습니다.

다음은 를 사용하여 주어진 쿼리를 유지하는 단계입니다 **curl** 명령줄 도구:

1. 새 끝점 URL에 넣어 쿼리를 준비합니다 `/graphql/persist.json/<config>/<persisted-label>`.

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

1. 이 시점에서 응답을 확인합니다.

   예를 들어, 성공을 확인합니다.

   ```xml
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. 그런 다음 URL을 입력하여 지속된 쿼리를 요청할 수 있습니다 `/graphql/execute.json/<shortPath>`.

   예를 들어, 지속된 쿼리를 사용합니다.

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. POSTing을 통해 지속된 쿼리를 이미 존재하는 쿼리 경로로 업데이트합니다.

   예를 들어, 지속된 쿼리를 사용합니다.

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

## 지속된 쿼리 게시 {#publish-persisted-query}

지속되는 쿼리는 클라이언트 애플리케이션에서 요청할 수 있는 AEM 게시 환경에 게시할 수 있습니다. 게시에서 지속된 쿼리를 사용하려면 관련 영구 트리를 복제해야 합니다.

지속적인 쿼리를 게시하는 방법에는 몇 가지가 있습니다.

* **복제에 POST 사용**:

   ```xml
   $ curl -X POST   http://localhost:4502/bin/replicate.json \
   -H 'authorization: Basic YWRtaW46YWRtaW4=' \
   -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
   -F cmd=activate
   ```

* **패키지 사용**:
   1. 새 패키지 정의를 만듭니다.
   1. 구성을 포함합니다(예: `/conf/wknd/settings/graphql/persistentQueries`).
   1. 패키지를 빌드합니다.
   1. 패키지를 복제합니다.

* **복제/배포 도구 사용**:
   1. 배포 도구로 이동합니다.
   1. 구성에 대한 트리 활성화를 선택합니다(예: `/conf/wknd/settings/graphql/persistentQueries`).

* **워크플로우 사용 (워크플로우 런처 구성을 통해)**:
   1. 다른 이벤트에서 구성을 복제하는 워크플로우 모델을 실행하기 위한 워크플로우 실행 관리자 규칙을 정의합니다(예: 만들기, 수정 등).

쿼리 구성이 게시되면 게시 끝점을 사용하기만 해도 동일한 인증 원칙이 적용됩니다.

>[!NOTE]
>
>익명 액세스의 경우 시스템은 ACL을 통해 &quot;모든 사용자&quot;가 쿼리 구성에 액세스할 수 있다고 가정합니다.
>
>그렇지 않으면 실행할 수 없습니다.

>[!NOTE]
>
>URL의 모든 세미콜론(&quot;;&quot;)을 인코딩해야 합니다.
>
>예를 들어, 지속형 쿼리 실행 요청에서와 같습니다.
>
>
```xml
>curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
>```
