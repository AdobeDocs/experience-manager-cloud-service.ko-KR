---
title: 지속 GraphQL 쿼리
description: 성능을 최적화하기 위해 Adobe Experience Manager as a Cloud Service에서 GraphQL 쿼리를 지속하는 방법을 알아봅니다. HTTP GET 메서드를 사용하여 클라이언트 애플리케이션에서 지속 쿼리를 요청할 수 있으며 응답을 Dispatcher 및 CDN 계층에서 캐시할 수 있으므로 궁극적으로 클라이언트 애플리케이션의 성능이 향상됩니다.
feature: Headless, Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: ht
source-wordcount: '1952'
ht-degree: 100%

---

# 지속 GraphQL 쿼리 {#persisted-graphql-queries}

지속 쿼리는 Adobe Experience Manager(AEM) as a Cloud Service 서버에서 생성 및 저장되는 GraphQL 쿼리입니다. 클라이언트 애플리케이션에서 GET 요청을 사용하여 요청할 수 있습니다. GET 요청의 응답은 Dispatcher 및 CDN 계층에서 캐시될 수 있으므로 궁극적으로 요청하는 클라이언트 애플리케이션의 성능이 향상됩니다. 이 경우 응답을 쉽게 캐시할 수 없는 POST 요청을 사용하여 실행되는 표준 GraphQL 쿼리와는 다릅니다.

>[!NOTE]
>
>지속 쿼리를 사용하는 것이 좋습니다. 자세한 내용은 [GraphQL 쿼리 모범 사례(Dispatcher)](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) 자세한 내용 및 관련 Dispatcher 구성을 참조하십시오.

[프로덕션 환경으로 이전](#transfer-persisted-query-production)하기 전에 GraphQL 쿼리를 개발, 테스트 및 지속할 수 있도록 [GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md)가 AEM에 제공됩니다. 맞춤화가 필요한 경우(예: [캐시를 사용자 정의](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)하는 경우) API를 사용할 수 있습니다. [GraphQL 쿼리를 지속하는 방법](#how-to-persist-query)에 제시된 cURL 예제를 참조하십시오.

## 지속 쿼리 및 엔드포인트 {#persisted-queries-and-endpoints}

지속 쿼리는 항상 [적절한 Sites 구성](graphql-endpoint.md)과 관련된 엔드포인트를 사용해야 합니다. 따라서 다음 중 하나 또는 둘 다를 사용할 수 있습니다.

* 전역 구성 및 엔드포인트
쿼리는 모든 콘텐츠 조각 모델에 액세스할 수 있습니다.
* 특정 Sites 구성 및 엔드포인트
특정 Sites 구성에 대한 지속 쿼리를 만들려면 (관련 콘텐츠 조각 모델에 대한 액세스를 제공하기 위해) 해당 Sites 구성별 엔드포인트가 필요합니다.
예를 들어 WKND Sites 구성을 위해 특별히 지속 쿼리를 만들려면 해당 WKND별 Sites 구성 및 WKND별 엔드포인트를 미리 만들어야 합니다.

>[!NOTE]
>
>자세한 내용은 [구성 브라우저에서 콘텐츠 조각 기능 활성화](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser)를 참조하십시오.
>
>적절한 사이트 구성을 위해 **GraphQL 지속 쿼리**&#x200B;를 활성화해야 합니다.

예를 들어 Sites 구성 `my-conf`의 모델 `my-model`을 사용하는 `my-query`라는 특정 쿼리가 있는 경우:

* `my-conf` 특정 엔드포인트를 사용하여 쿼리를 만들 수 있으며 쿼리는 다음과 같이 저장됩니다.
  `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* `global` 엔드포인트를 사용하여 동일한 쿼리를 생성할 수 있지만 쿼리는 다음과 같이 저장됩니다.
  `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>이 쿼리들을 서로 다른 경로에 저장된 두 개의 서로 다른 쿼리입니다.
>
>동일한 모델을 사용하기는 하지만 다른 엔드포인트를 통해 발생합니다.

## GraphQL 쿼리를 지속하는 방법 {#how-to-persist-query}

처음에 AEM 작성 환경에서 쿼리를 지속한 다음 프로덕션 AEM 게시 환경에 [쿼리를 전송](#transfer-persisted-query-production)하여 애플리케이션에서 사용하는 것이 좋습니다.

다양한 방법으로 쿼리를 지속합니다(다음 포함).

* GraphiQL IDE - [지속 쿼리 저장](/help/headless/graphql-api/graphiql-ide.md#saving-persisted-queries) 참조(기본 방법)
* cURL - 다음 예제 참조
* 기타 도구, [Postman](https://www.postman.com/) 포함

GraphiQL IDE는 쿼리를 지속할 수 있는 **기본** 방법입니다. **cURL** 명령줄 도구를 사용하여 지정된 쿼리를 지속하려면 다음 작업을 수행하십시오.

1. 쿼리를 새 엔드포인트 URL `/graphql/persist.json/<config>/<persisted-label>`에 PUT하여 준비합니다.

   예를 들어 지속 쿼리를 만듭니다.

   ```shell
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

   ```json
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

   ```shell
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. 이미 존재하는 쿼리 경로에 POST하여 지속 쿼리를 업데이트합니다.

   예를 들어 지속 쿼리를 사용합니다.

   ```shell
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

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. 캐시 제어를 사용하여 래핑된 일반 쿼리를 만듭니다.

   예:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. 매개변수를 사용하여 지속 쿼리를 만듭니다.

   예:

   ```shell
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


## 지속 쿼리 실행 방법 {#execute-persisted-query}

지속 쿼리를 실행하기 위해 클라이언트 애플리케이션은 다음 구문을 사용하여 GET 요청을 수행합니다.

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

`PERSISTENT_PATH`는 지속 쿼리가 저장되는 위치에 대한 축약된 경로입니다.

1. 예를 들어 `wknd`는 구성 이름이며 `plain-article-query`는 지속 쿼리의 이름입니다. 쿼리를 실행하려면 다음 작업을 수행하십시오.

   ```shell
   $ curl -X GET \
       https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query
   ```

1. 매개변수를 사용하여 쿼리를 실행합니다.

   >[!NOTE]
   >
   > 지속 쿼리를 실행할 때는 쿼리 변수 및 값을 올바르게 [인코딩](#encoding-query-url)해야 합니다.

   예:

   ```xml
   $ curl -X GET \
       "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   자세한 내용은 [쿼리 변수](#query-variables) 사용을 참조하십시오.

## 쿼리 변수 사용 {#query-variables}

쿼리 변수를 지속 쿼리와 함께 사용할 수 있습니다. 쿼리 변수는 변수 이름과 값을 사용하여 앞에 세미콜론(`;`)이 붙은 요청에 추가됩니다. 여러 변수는 세미콜론으로 구분됩니다.

패턴은 다음과 같습니다.

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

예를 들어 다음 쿼리에는 활동 값을 기반으로 목록을 필터링하기 위한 변수 `activity`가 포함되어 있습니다.

```graphql
query getAdventuresByActivity($activity: String!) {
      adventureList (filter: {
        adventureActivity: {
          _expressions: [
            {
              value: $activity
            }
          ]
        }
      }){
        items {
          _path
        adventureTitle
        adventurePrice
        adventureTripLength
      }
    }
  }
```

이 쿼리는 경로 `wknd/adventures-by-activity`에서 지속할 수 있습니다. `activity=Camping` 요청이 다음과 같이 표시되는 지속 쿼리를 호출하려면 다음 작업을 수행하십시오.

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

`%3B`는 `;`에 대한 UTF-8 인코딩이며 `%3D`는 `=`에 대한 인코딩입니다. 실행할 지속 쿼리에 대해 쿼리 변수 및 특수 문자를 [올바르게 인코딩](#encoding-query-url)해야 합니다.

### 쿼리 변수 사용 - 모범 사례 {#query-variables-best-practices}

쿼리에서 변수를 사용할 때 따라야 할 몇 가지 모범 사례가 있습니다.

* 인코딩
일반적으로 모든 특수 문자를 인코딩하는 것이 좋습니다. 예를 들면 `;`, `=`, `?`, `&` 등이 있습니다.

* 세미콜론
여러 변수(세미콜론으로 구분)를 사용하는 지속 쿼리에는 다음 중 하나가 필요합니다.
   * 세미콜론 인코딩(`%3B`): URL을 인코딩하여 세미콜론을 인코딩할 수도 있습니다.
   * 또는 쿼리 끝에 세미콜론을 추가

* `CACHE_GRAPHQL_PERSISTED_QUERIES`
`CACHE_GRAPHQL_PERSISTED_QUERIES`가 Dispatcher에 대해 활성화된 경우, `/` 또는 `\` 문자를 값에 포함하는 매개변수는 Dispatcher 레벨에서 두 번 인코딩됩니다.
이를 방지하려면 다음을 따릅니다.

   * Dispatcher에서 `DispatcherNoCanonURL`을 활성화합니다.
이렇게 하면 Dispatcher가 원래 URL을 AEM으로 전달하도록 지시하여 인코딩 중복을 방지할 수 있습니다.
그러나 이 설정은 현재 `vhost` 레벨에서만 작동하므로 URL을 다시 작성하는 Dispatcher 구성이 이미 있는 경우(예: 단축 URL을 사용하는 경우) 지속 쿼리 URL에 대한 별도의 `vhost`가 필요할 수 있습니다.

   * `/` 또는 인코딩되지 않은 `\` 문자를 보냅니다.
지속형 쿼리 URL을 호출할 때 지속형 쿼리 변수의 값에 있는 모든 `/` 또는 `\` 문자가 인코딩되지 않은 상태로 유지되도록 합니다.
     >[!NOTE]
     >
     >이 옵션은 어떠한 이유에서든 `DispatcherNoCanonURL` 솔루션을 구현할 수 없는 경우에만 권장됩니다.

* `CACHE_GRAPHQL_PERSISTED_QUERIES`

  Dispatcher에 대해 `CACHE_GRAPHQL_PERSISTED_QUERIES`가 활성화된 경우, `;` 문자를 변수 값에 사용할 수 없습니다.

## 지속 쿼리 캐싱 {#caching-persisted-queries}

지속 쿼리는 [Dispatcher](/help/headless/deployment/dispatcher.md) 및 CDN(Content Delivery Network) 계층에서 캐시될 수 있어 궁극적으로 요청하는 클라이언트 애플리케이션의 성능이 향상되므로 이를 사용하는 것이 좋습니다.

기본적으로 AEM은 TTL(Time To Live) 정의에 따라 캐시를 무효화합니다. 이러한 TTL은 다음 매개변수로 정의할 수 있습니다. 이러한 매개변수는 다양한 방법으로 액세스할 수 있으며, 사용되는 메커니즘에 따라 이름이 다양합니다.

| 캐시 유형 | [HTTP 헤더](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control)  | cURL  | OSGi 구성  | Cloud Manager |
|--- |--- |--- |--- |--- |
| 브라우저 | `max-age` | `cache-control : max-age` | `cacheControlMaxAge` | `graphqlCacheControl` |
| CDN | `s-maxage` | `surrogate-control : max-age` | `surrogateControlMaxAge` | `graphqlSurrogateControl` | 60 |
| CDN | `stale-while-revalidate` | `surrogate-control : stale-while-revalidate ` | `surrogateControlStaleWhileRevalidate` | `graphqlStaleWhileRevalidate` |
| CDN | `stale-if-error` | `surrogate-control : stale-if-error` | `surrogateControlStaleIfError` | `graphqlStaleIfError` |

{style="table-layout:auto"}

### 작성자 인스턴스 {#author-instances}

작성자 인스턴스의 경우 기본값은 다음과 같습니다.

* `max-age` : 60
* `s-maxage` : 60
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

이들:

* 덮어쓸 수 없음:
   * OSGi 구성으로
* 덮어쓸 수 있음:
   * cURL을 사용하여 HTTP 헤더 설정을 정의하는 요청으로, `cache-control` 및/또는 `surrogate-control`에 적합한 설정을 포함해야 합니다(예: [지속 쿼리 수준에서 캐시 관리](#cache-persisted-query-level) 참조).
   * [GraphiQL IDE](#http-cache-headers-graphiql-ide)의 **헤더** 대화 상자에서 값을 지정하는 경우

### 게시 인스턴스 {#publish-instances}

게시 인스턴스의 경우 기본값은 다음과 같습니다.

* `max-age` : 60
* `s-maxage` : 7200
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

다음을 덮어쓸 수 있습니다.

* [GraphQL IDE에서](#http-cache-headers-graphiql-ide)

* [지속 쿼리 수준에서](#cache-persisted-query-level) 명령줄 인터페이스에서 cURL을 사용하여 AEM에 쿼리를 게시하고 지속 쿼리를 게시하는 작업이 포함됩니다.

* [Cloud Manager 변수 사용](#cache-cloud-manager-variables)

* [OSGi 구성으로](#cache-osgi-configration)

### GraphiQL IDE에서 HTTP 캐시 헤더 관리 {#http-cache-headers-graphiql-ide}

GraphiQL IDE - [지속 쿼리 저장](/help/headless/graphql-api/graphiql-ide.md#managing-cache) 참조

### 지속 쿼리 수준에서 캐시 관리 {#cache-persisted-query-level}

이는 명령줄 인터페이스의 cURL을 사용하여 AEM에 쿼리를 게시하는 것과 관련되어 있습니다.

PUT(만들기) 방법의 예:

```bash
curl -u admin:admin -X PUT \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

POST(업데이트) 방법의 예:

```bash
curl -u admin:admin -X POST \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

`cache-control`은 생성 시간(PUT) 또는 그 이후에 설정할 수 있습니다(예: 인스턴스의 POST 요청을 통해 설정). AEM에서 기본값을 제공하기 때문에 지속 쿼리 생성 시 캐시 제어는 옵션입니다. cURL을 사용하여 쿼리를 지속하는 사례는 [GraphQL 쿼리를 지속하는 방법](#how-to-persist-query)을 참조하십시오.

### Cloud Manager 변수를 사용하여 캐시 관리 {#cache-cloud-manager-variables}

[Cloud Manager 환경 변수](/help/implementing/cloud-manager/environment-variables.md)는 Cloud Manager로 정의하여 필요한 값을 정의할 수 있습니다.

| 이름 | 값 | 적용된 서비스 | 유형 |
|--- |--- |--- |--- |
| `graphqlStaleIfError` | 86400 | *적절히* | *적절히* |
| `graphqlSurrogateControl` | 600 | *적절히* | *적절히* |

{style="table-layout:auto"}

### OSGi 구성으로 캐시 관리 {#cache-osgi-configration}

캐시를 전체적으로 관리하려면 **지속 쿼리 서비스 구성**&#x200B;에 대한 [OSGi 설정을 구성](/help/implementing/deploying/configuring-osgi.md)하면 됩니다.

>[!NOTE]
>
>캐시 제어 시 OSGi 구성은 게시 인스턴스에만 적합합니다. 구성은 작성자 인스턴스에 존재하지만 무시됩니다.

>[!NOTE]
>
>**지속 쿼리 서비스 구성**&#x200B;은 [쿼리 응답 코드 구성](#configuring-query-response-code)에서도 사용됩니다.

게시 인스턴스에 대한 기본 OSGi 구성:

* 사용 가능한 경우 Cloud Manager 변수를 읽습니다.

  | OSGi 구성 속성 | 다음을 읽기 | Cloud Manager 변수 |
  |--- |--- |--- |
  | `cacheControlMaxAge` | 읽기 | `graphqlCacheControl` |
  | `surrogateControlMaxAge` | 읽기 | `graphqlSurrogateControl` |
  | `surrogateControlStaleWhileRevalidate` | 읽기 | `graphqlStaleWhileRevalidate` |
  | `surrogateControlStaleIfError` | 읽기 | `graphqlStaleIfError` |

  {style="table-layout:auto"}

* 사용할 수 없는 경우 OSGi 구성은 [게시 인스턴스에 대한 기본값](#publish-instances)을 사용합니다.

## 쿼리 응답 코드 구성 {#configuring-query-response-code}

기본적으로 `PersistedQueryServlet`은 실제 결과에 관계없이 쿼리를 실행할 때 `200` 응답을 보냅니다.

**지속 쿼리 서비스 구성**&#x200B;에 대한 [OSGi 설정을 구성](/help/implementing/deploying/configuring-osgi.md)하여 지속 쿼리에 오류가 발생하면 `/execute.json/persisted-query` 엔드포인트에서 보다 상세한 상태 코드가 반환되는지 여부를 제어할 수 있습니다.

>[!NOTE]
>
>**지속 쿼리 서비스 구성**&#x200B;은 [캐시 관리](#cache-osgi-configration)에서도 사용됩니다.

필드`Respond with application/graphql-response+json`(`responseContentTypeGraphQLResponseJson`)은 필요에 따라 정의할 수 있습니다.

* `false`(기본값):
지속 쿼리의 성공 여부는 상관없습니다. 반환되는 `Content-Type` 헤더는 `application/json`이며 `/execute.json/persisted-query`는 *항상* 상태 코드 `200`을 반환합니다.

* `true`:
반환되는 `Content-Type`은 `application/graphql-response+json`이며 엔드포인트는 지속 쿼리 실행 시 오류가 발생할 때 적절한 응답 코드를 반환합니다.

  | 코드 | 설명 |
  |--- |--- |
  | 200 | 성공적인 응답 |
  | 400 | 헤더가 누락되었거나 지속된 쿼리 경로에 문제가 있음을 나타냅니다. 예를 들어 구성 이름 미지정, 접미사 미지정 등의 문제가 있습니다.<br> [문제 해결 - GraphQL 엔드포인트 미구성](/help/headless/graphql-api/persisted-queries-troubleshoot.md#missing-path-query-url)을 참조하십시오. |
  | 404 | 요청한 리소스를 찾을 수 없습니다. 예를 들어 Graphql 엔드포인트는 서버에서 사용할 수 없습니다.<br> [문제 해결 - GraphQL 지속형 쿼리 URL 내 경로 누락](/help/headless/graphql-api/persisted-queries-troubleshoot.md#graphql-endpoint-not-configured)을 참조하십시오. |
  | 500 | 내부 서버 오류. 예를 들어 검증 오류, 지속성 오류 등이 있습니다. |

  >[!NOTE]
  >
  >https://graphql.github.io/graphql-over-http/draft/#sec-Status-Codes를 참조하십시오.

## 앱에서 사용할 쿼리 URL 인코딩 {#encoding-query-url}

애플리케이션에서 사용하는 경우, 쿼리 변수를 구성할 때 사용되는 모든 특수 문자(예: 세미콜론(`;`), 등호(`=`), 슬래시(`/`))를 해당 UTF-8 인코딩을 사용하도록 변환해야 합니다.

예:

```xml
curl -X GET \ "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/adventure-by-path%3BadventurePath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fadventures%2Fbali-surf-camp%2Fbali-surf-camp"
```

URL은 다음과 같은 부분들로 나눌 수 있습니다.

| URL 부분 | 설명 |
|----------| -------------|
| `/graphql/execute.json` | 지속 쿼리 엔드포인트 |
| `/wknd/adventure-by-path` | 지속 쿼리 경로 |
| `%3B` | `;`의 인코딩 |
| `adventurePath` | 쿼리 변수 |
| `%3D` | `=`의 인코딩 |
| `%2F` | `/`의 인코딩 |
| `%2Fcontent%2Fdam...` | 콘텐츠 조각의 인코딩된 경로 |

일반 텍스트에서 요청 URI는 다음과 같습니다.

```plaintext
/graphql/execute.json/wknd/adventure-by-path;adventurePath=/content/dam/wknd/en/adventures/bali-surf-camp/bali-surf-camp
```

클라이언트 앱에서 지속 쿼리를 사용하려면 AEM Headless 클라이언트 SDK는 [JavaScript](https://github.com/adobe/aem-headless-client-js), [Java](https://github.com/adobe/aem-headless-client-java) 또는 [NodeJS](https://github.com/adobe/aem-headless-client-nodejs)용으로 사용해야 합니다. Headless 클라이언트 SDK는 요청에서 모든 쿼리 변수를 자동으로 적절하게 인코딩합니다.

## 프로덕션 환경에 지속 쿼리 전송  {#transfer-persisted-query-production}

지속 쿼리는 항상 AEM 작성자 서비스에서 만든 다음 AEM 게시 서비스에 게시(복제)해야 합니다. 지속 쿼리는 종종 로컬 또는 개발 환경과 같은 하위 수준 환경에서 생성되고 테스트됩니다. 그런 다음 지속 쿼리를 더 높은 수준의 환경으로 승격하여 궁극적으로 클라이언트 애플리케이션이 사용할 수 있도록 프로덕션 AEM 게시 환경에서 사용할 수 있도록 해야 합니다.

### 패키지 지속 쿼리

지속 쿼리를 [AEM 패키지](/help/implementing/developing/tools/package-manager.md)에 빌드할 수 있습니다. 그런 다음 AEM 패키지를 다운로드하여 다른 환경에 설치할 수 있습니다. AEM 패키지를 AEM 작성자 환경에서 AEM 게시 환경으로 복제할 수도 있습니다.

패키지를 제작하려면 다음 작업을 수행하십시오.

1. **도구** > **배포** > **패키지**&#x200B;로 이동합니다.
1. **패키지 만들기**&#x200B;를 탭하여 새 패키지를 만듭니다. 이렇게 하면 패키지를 정의하는 대화 상자가 열립니다.
1. 패키지 정의 대화 상자에서 **일반**&#x200B;에 “wknd-persistent-queries”와 같은 **이름**&#x200B;을 입력합니다.
1. “1.0”과 같은 버전 번호를 입력합니다.
1. **필터** 아래에 새 **필터**&#x200B;를 추가합니다. 경로 파인더를 사용하여 구성 아래에서 `persistentQueries` 폴더를 선택합니다. 예를 들어 `wknd` 구성의 경우, 전체 경로는 `/conf/wknd/settings/graphql/persistentQueries`입니다.
1. **저장**&#x200B;을 선택하여 새 패키지 정의를 저장하고 대화 상자를 닫습니다.
1. 만든 패키지 정의에 있는 **빌드** 버튼을 선택합니다.

패키지를 빌드하면 다음과 같은 작업을 수행할 수 있습니다.

* 패키지를 **다운로드**&#x200B;하고 다른 환경에 다시 업로드할 수 있습니다.
* **기타** > **복제**&#x200B;를 탭하여 패키지를 **복제**&#x200B;할 수 있습니다. 이렇게 하면 연결된 AEM 게시 환경에 패키지가 복제됩니다.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->
