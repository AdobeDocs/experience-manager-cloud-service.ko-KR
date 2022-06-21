---
title: 지속 GraphQL 쿼리
description: 성능을 최적화하기 위해 Adobe Experience Manager as a Cloud Service에서 GraphQL 쿼리를 지속하는 방법을 알아봅니다. HTTP GET 메서드를 사용하여 클라이언트 애플리케이션에서 지속 쿼리를 요청할 수 있으며 응답을 Dispatcher 및 CDN 계층에서 캐시할 수 있으므로 궁극적으로 클라이언트 애플리케이션의 성능이 향상됩니다.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 6529b4b874cd7d284b92546996e2373e59075dfd
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 47%

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

* GraphiQL IDE - 참조 [지속되는 쿼리 저장](/help/headless/graphql-api/graphiql-ide.md##saving-persisted-queries) (기본 설정 메서드)
* curl - 다음 예제 참조
* 기타 도구, [Postman](https://www.postman.com/) 포함

GraphiQL IDE는 다음과 같습니다 **기본** 쿼리를 유지하는 방법 특정 쿼리를 **curl** 명령줄 도구:

1. 쿼리를 새 끝점 URL `/graphql/persist.json/<config>/<persisted-label>`에 PUT하여 준비합니다.

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

1. 매개 변수를 사용하여 지속 쿼리를 만듭니다.

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


## 지속형 쿼리를 실행하는 방법 {#execute-persisted-query}

지속형 쿼리를 실행하기 위해 클라이언트 응용 프로그램은 다음 구문을 사용하여 GET 요청을 수행합니다.

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

위치 `PERSISTENT_PATH` 은 영구 쿼리가 저장된 위치에 대한 단축된 경로입니다.

1. 예 `wknd` 구성 이름 및 `plain-article-query` 은 영구 쿼리의 이름입니다. 쿼리를 실행하려면

   ```shell
   $ curl -X GET \
       https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query
   ```

1. 매개 변수를 사용하여 쿼리를 실행합니다.

   >[!NOTE]
   >
   > 쿼리 변수와 값이 올바르게 되어야 합니다. [인코딩됨](#encoding-query-url) 영구적 쿼리를 실행할 때

   예:

   ```xml
   $ curl -X GET \
       "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   사용 을 참조하십시오 [쿼리 변수](#query-variables) 자세한 내용

## 쿼리 변수 사용 {#query-variables}

쿼리 변수는 지속되는 쿼리와 함께 사용할 수 있습니다. 쿼리 변수는 세미콜론(`;`) 변수 이름과 값을 사용하여 규칙 세트를 만듭니다. 여러 변수는 세미콜론으로 구분됩니다.

패턴은 다음과 같습니다.

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

예를 들어 다음 쿼리에 변수가 포함되어 있습니다 `activity` 활동 값을 기반으로 목록을 필터링하려면 다음을 수행하십시오.

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

이 쿼리는 경로 아래에서 유지할 수 있습니다 `wknd/adventures-by-activity`. 지속형 쿼리를 호출하려면 `activity=Camping` 요청은 다음과 같습니다.

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

참고 사항 `%3B` 는 `;` 및 `%3D` 은 의 인코딩입니다. `=`. 쿼리 변수와 특수 문자는 [인코딩이 올바르게 수행됨](#encoding-query-url) 지속형 쿼리를 실행할 수 있습니다.

## 앱에서 사용하기 위해 쿼리 URL 인코딩 {#encoding-query-url}

응용 프로그램에서 사용하는 경우 쿼리 변수를 구성할 때 사용되는 모든 특수 문자(즉, 세미콜론(`;`), 등호( )`=`), 슬래시 `/`)에서 해당 UTF-8 인코딩을 사용하도록 변환해야 합니다.

예:

```xml
curl -X GET \ "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/adventure-by-path%3BadventurePath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fadventures%2Fbali-surf-camp%2Fbali-surf-camp"
```

URL은 다음 부분으로 나눌 수 있습니다.

| URL 부분 | 설명 |
|----------| -------------|
| `/graphql/execute.json` | 영구 쿼리 끝점 |
| `/wknd/adventure-by-path` | 영구 쿼리 경로 |
| `%3B` | 인코딩 `;` |
| `adventurePath` | 쿼리 변수 |
| `%3D` | 인코딩 `=` |
| `%2F` | 인코딩 `/` |
| `%2Fcontent%2Fdam...` | 컨텐츠 조각의 인코딩된 경로 |

일반 텍스트에서 요청 URI는 다음과 같습니다.

```plaintext
/graphql/execute.json/wknd/adventure-by-path;adventurePath=/content/dam/wknd/en/adventures/bali-surf-camp/bali-surf-camp
```

클라이언트 앱에서 지속형 쿼리를 사용하려면 AEM 헤드리스 클라이언트 SDK를에 사용해야 합니다 [JavaScript](https://github.com/adobe/aem-headless-client-js), [Java](https://github.com/adobe/aem-headless-client-java), 또는 [NodeJS](https://github.com/adobe/aem-headless-client-nodejs). 헤드리스 클라이언트 SDK는 요청에서 적절하게 모든 쿼리 변수를 자동으로 인코딩합니다.

## 프로덕션 환경에 지속 쿼리 전송 중  {#transfer-persisted-query-production}

지속되는 쿼리는 항상 AEM 작성자 서비스에서 만든 다음, AEM 게시 서비스에 게시(복제)해야 합니다. 자주, 지속적인 쿼리는 로컬 또는 개발 환경과 같은 낮은 환경에서 만들어지고 테스트됩니다. 그런 다음 클라이언트 애플리케이션에서 사용할 수 있도록 프로덕션 AEM 게시 환경에서 사용할 수 있도록 하려면, 지속형 쿼리를 더 높은 수준의 환경으로 프로모션해야 합니다.

### 패키지 영구 쿼리

영구 쿼리는 [AEM 패키지](/help/implementing/developing/tools/package-manager.md). 그런 다음 AEM 패키지를 다운로드하여 다른 환경에 설치할 수 있습니다. AEM 패키지는 AEM 작성자 환경에서 AEM 게시 환경으로 복제할 수도 있습니다.

패키지를 만들려면:

1. 다음으로 이동 **도구** > **배포** > **패키지**.
1. 를 탭하여 새 패키지 만들기 **패키지 만들기**. 그러면 패키지를 정의하는 대화 상자가 열립니다.
1. 패키지 정의 대화 상자의 **일반** 입력 **이름** &quot;wknd-persistent-queries&quot;와 같습니다.
1. &quot;1.0&quot;과 같은 버전 번호를 입력합니다.
1. 아래 **필터** 새로 추가 **필터**. 경로 파인더를 사용하여 `persistentQueries` 폴더 아래에 표시됩니다. 예: `wknd` 전체 경로 구성 `/conf/wknd/settings/graphql/persistentQueries`.
1. 탭 **저장** 새 패키지 정의를 저장하고 대화 상자를 닫으려면 를 클릭합니다.
1. 탭하기 **빌드** 새로 만든 패키지 정의에 있는 단추입니다.

패키지를 빌드하면 다음을 수행할 수 있습니다.

* **다운로드** 패키지를 다시 업로드하고 다른 환경에서 다시 업로드합니다.
* **복제** 를 탭하여 패키지 **자세히** > **복제**. 이렇게 하면 연결된 AEM 게시 환경에 패키지가 복제됩니다.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->
