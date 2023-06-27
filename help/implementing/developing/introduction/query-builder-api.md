---
title: 쿼리 빌더 API
description: 자산 공유 쿼리 빌더의 기능은 Java&trade; API 및 REST API를 통해 노출됩니다.
exl-id: d5f22422-c9da-4c9d-b81c-ffa5ea7cdc87
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '2008'
ht-degree: 0%

---

# 쿼리 빌더 API {#query-builder-api}

Query Builder를 사용하면 AEM의 콘텐츠 저장소를 쉽게 쿼리할 수 있습니다. 기능은 Java™ API 및 REST API를 통해 노출됩니다. 이 문서에서는 이러한 API에 대해 설명합니다.

서버측 쿼리 빌더([`QueryBuilder`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html))는 쿼리 설명을 수락하고 XPath 쿼리를 만들고 실행하며 선택적으로 결과 세트를 필터링하고 원하는 경우 패싯을 추출합니다.

쿼리 설명은 단순히 술어 집합([`Predicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/Predicate.html)). 예를 들면 전체 텍스트 조건자가 있으며, 이는 `jcr:contains()` 함수(XPath).

각 술어 유형에 대해 평가기 구성 요소([`PredicateEvaluator`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html))를 사용하여 XPath, 필터링 및 패싯 추출에 대한 특정 조건자를 처리할 수 있습니다. OSGi 구성 요소 런타임을 통해 플러그인된 사용자 지정 평가자를 쉽게 만들 수 있습니다.

REST API는 JSON으로 전송되는 응답과 함께 HTTP를 통해 동일한 기능에 대한 액세스를 제공합니다.

>[!NOTE]
>
>QueryBuilder API는 JCR API를 사용하여 빌드됩니다. OSGi 번들 내에서 JCR API를 사용하여 AEM JCR을 쿼리할 수도 있습니다. 자세한 내용은 [JCR API를 사용하여 Adobe Experience Manager 데이터 쿼리](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/query-builder/querybuilder-api.html).

## Gem 세션 {#gem-session}

[AEM Gems](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/overview.html?lang=en) 는 Adobe 전문가가 Adobe Experience Manager에 제공하는 일련의 기술적인 분석입니다.

다음을 수행할 수 있습니다. [쿼리 빌더 전용 세션 검토](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2017/aem-search-forms-using-querybuilder.html?lang=en) 을 참조하십시오.

## 샘플 쿼리 {#sample-queries}

이러한 샘플은 Java™ 속성 스타일 표기법으로 제공됩니다. Java™ API와 함께 사용하려면 Java를 사용하십시오™ `HashMap` 다음 API 샘플에서와 같이.

의 경우 `QueryBuilder` JSON 서블릿, 각 예에는 AEM 설치에 대한 샘플 링크가 포함되어 있습니다(기본 위치, `http://<host>:<port>`). 이러한 링크를 사용하기 전에 AEM 인스턴스에 로그온합니다.

>[!CAUTION]
>
>기본적으로 Query Builder JSON 서블릿은 최대 10개의 히트를 표시합니다.
>
>다음 매개 변수를 추가하면 서블릿이 모든 쿼리 결과를 표시할 수 있습니다.
>
>`p.limit=-1`

>[!NOTE]
>
>브라우저에서 반환된 JSON 데이터를 보려면 Firefox용 JSONView와 같은 플러그인을 사용할 수 있습니다.

### 모든 결과 반환 {#returning-all-results}

다음 쿼리 **10개의 결과 반환** (또는 정확히 말하면 최대 10개), 하지만 다음을 사용자에게 알립니다. **히트 수:** 사용 가능한 값:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

동일한 쿼리(매개 변수 포함) `p.limit=-1`) **모든 결과 반환** (인스턴스에 따라 높은 숫자가 될 수 있습니다.)

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path&p.limit=-1`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.limit=-1
orderby=path
```

### p.guessTotal을 사용하여 결과 반환 {#using-p-guesstotal-to-return-the-results}

의 목적 `p.guessTotal` 매개 변수는 최소 실행 가능 수를 결합하여 표시할 수 있는 적절한 결과 수를 반환하는 것입니다 `p.offset` 및 `p.limit` 값. 이 매개 변수를 사용하면 결과 세트 크기가 클수록 성능이 향상됩니다. 이 매개 변수는 전체 합계를 계산하는 것을 방지합니다(예: 호출). `result.getSize()`)를 참조하고 Oak 엔진 및 색인까지 최적화된 전체 결과 세트를 읽습니다. 이 프로세스는 실행 시간과 메모리 사용량 모두에서 수십만 개의 결과가 있을 때 상당한 차이가 될 수 있습니다.

매개 변수의 단점은 사용자가 정확한 합계를 보지 못한다는 것입니다. 하지만 다음과 같이 최소 숫자를 설정할 수 있습니다. `p.guessTotal=1000` 그래서 항상 1000까지 읽습니다. 이러한 방식으로 작은 결과 세트에 대한 정확한 합계를 얻지만, 더 많은 경우 &quot;외&quot;만 표시할 수 있습니다.

추가 `p.guessTotal=true` 작동 방식을 확인하려면 아래 쿼리를 참조하십시오.

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.guessTotal=true
orderby=path
```

이 쿼리는 `p.limit` 기본값 `10` 이 있는 결과 `0` 오프셋:

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

숫자 값을 사용하여 최대 결과의 사용자 지정 수까지 계산할 수도 있습니다. 위와 동일한 쿼리를 사용하되 값을 변경합니다. `p.guessTotal` 끝 `50`:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=50&orderby=path`

이 메서드는 오프셋이 0인 10개의 결과와 동일한 기본 제한을 반환하지만 최대 50개의 결과만 표시합니다.

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### 페이지 매김 구현 {#implementing-pagination}

기본적으로 Query Builder는 히트 수도 제공합니다. 이 숫자는 결과 크기에 따라 정확한 개수를 결정하는 데 액세스 제어에 대한 모든 결과를 확인하는 데 시간이 오래 걸릴 수 있습니다. 대부분 합계는 최종 사용자 UI에 대한 페이지 매김을 구현하는 데 사용됩니다. 정확한 카운트가 느려질 수 있으므로 guessTotal 기능을 사용하여 페이지 매김을 구현하는 것이 좋습니다.

예를 들어 UI는 다음 접근 방식을 조정할 수 있습니다.

* 총 히트 수 ( )의 정확한 개수를 가져와 표시합니다.[SearchResult.getTotalMatches()](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/SearchResult.html#getTotalMatches) 또는 의 합계 `querybuilder.json` 응답)이 100보다 작거나 같습니다.
* 설정 `guessTotal` 쿼리 빌더를 100까지 호출합니다.

* 응답은 다음과 같은 결과를 얻을 수 있습니다.

   * `total=43`, `more=false` - 총 히트 수가 43개임을 나타냅니다. UI는 최대 10개의 결과를 첫 번째 페이지의 일부로 표시하고 다음 3개 페이지에 대한 페이지 매김을 제공할 수 있습니다. 이 구현을 사용하여 다음과 같은 설명 텍스트를 표시할 수도 있습니다 **&quot;43개의 결과 찾음&quot;**.
   * `total=100`, `more=true` - 총 히트 수가 100보다 크고 정확한 카운트를 알 수 없음을 나타냅니다. UI는 첫 번째 페이지의 일부로 최대 10개를 표시하고 다음 10개 페이지에 대한 페이지 매김을 제공할 수 있습니다. 이 기능을 사용하여 다음과 같은 텍스트를 표시할 수도 있습니다 **&quot;100개 이상의 결과 검색됨&quot;**. 사용자가 다음 페이지로 이동하면 쿼리 빌더에 대한 호출이 의 제한을 늘립니다. `guessTotal` 및 `offset` 및 `limit` 매개 변수.

또한 `guessTotal` 사용자 인터페이스가 Query Builder가 정확한 히트 수를 확인하지 않도록 무한 스크롤링을 사용해야 하는 경우.

### jar 파일 찾기 및 주문, 최신 항목 먼저 {#find-jar-files-and-order-them-newest-first}

`http://<host>:<port>/bin/querybuilder.json?type=nt:file&nodename=*.jar&orderby=@jcr:content/jcr:lastModified&orderby.sort=desc`

```xml
type=nt:file
nodename=*.jar
orderby=@jcr:content/jcr:lastModified
orderby.sort=desc
```

### 모든 페이지를 찾아 마지막 수정일까지 정렬 {#find-all-pages-and-order-them-by-last-modified}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
```

### 모든 페이지를 찾아 마지막 수정 날짜, 내림차순으로 정렬 {#find-all-pages-and-order-them-by-last-modified-but-descending}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified&orderby.sort=desc`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
orderby.sort=desc
```

### 전체 텍스트 검색, 점수로 정렬 {#fulltext-search-ordered-by-score}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Management&orderby=@jcr:score&orderby.sort=desc`

```xml
fulltext=Management
orderby=@jcr:score
orderby.sort=desc
```

### 특정 태그가 있는 페이지 검색 {#search-for-pages-tagged-with-a-certain-tag}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&tagid=wknd:activity/cycling&tagid.property=jcr:content/cq:tags`

```xml
type=cq:Page
tagid=wknd:activity/cycling
tagid.property=jcr:content/cq:tags
```

사용 `tagid` 명시적 태그 ID를 알고 있는 경우 예제와 같이 조건화합니다.

사용 `tag` 태그 제목 경로(공백 없음)에 대한 조건자입니다.

이전 예제에서는 페이지를 검색하기 때문에(`cq:Page` 노드)에 대해 해당 노드의 상대 경로를 사용합니다 `tagid.property` 조건자: `jcr:content/cq:tags`. 기본적으로 `tagid.property` 다음과 같을 수 있습니다. `cq:tags`.

### 여러 경로 검색(그룹 사용) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

이 쿼리는 *그룹* (명명된) `group`)를 추가할 수 있습니다. 괄호를 사용하면 더 표준 표기법으로 괄호를 사용한 것처럼 쿼리 내에서 하위 표현식을 구분할 수 있습니다. 예를 들어 이전 쿼리는 다음과 같이 더 익숙한 스타일로 표현될 수 있습니다.

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

이 예제의 그룹 내에서 `path` 조건자가 여러 번 사용됩니다. 술어의 두 인스턴스를 구분하고 순서를 지정하려면(일부 술어의 경우 순서 지정 필요) 술어 앞에 를 붙여야 합니다 `N_` 위치 `N` 는 순서 지정 색인입니다. 앞의 예에서 그 결과 술어는 다음과 같습니다 `1_path` 및 `2_path`.

다음 `p` 위치: `p.or` 는 다음에 오는 것을 나타내는 특수 구분 기호입니다(이 경우 `or`) *매개 변수* 그룹의 하위 조건자와 반대로 `1_path`.

없는 경우 `p.or` 가 주어지면 모든 술어가 AND가 됩니다. 즉, 각 결과는 모든 술어를 만족해야 합니다.

>[!NOTE]
>
>다른 술어에 대해서도 하나의 쿼리에 동일한 숫자 접두사를 사용할 수 없습니다.

### 속성 검색 {#search-for-properties}

여기서는 다음을 사용하여 주어진 템플릿의 모든 페이지를 검색합니다. `cq:template` 속성:

`http://<host>:<port>/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

단점은 `jcr:content` 페이지 자체가 아니라 페이지의 노드가 반환됩니다. 이 문제를 해결하려면 상대 경로로 검색할 수 있습니다.

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3acontent%2fcq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPage`

```xml
type=cq:Page
property=jcr:content/cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

### 여러 속성 검색 {#search-for-multiple-properties}

속성 술어를 여러 번 사용할 때 숫자 접두사를 다시 추가해야 합니다.

`http://<host>:<port>/bin/querybuilder.json?1_property=jcr%3acontent%2fcq%3atemplate&1_property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&2_property=jcr%3acontent%2fjcr%3atitle&2_property.value=Cycling%20Tuscany&type=cq%3aPage`

```xml
type=cq:Page
1_property=jcr:content/cq:template
1_property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
2_property=jcr:content/jcr:title
2_property.value=Cycling Tuscany
```

### 여러 속성 값 검색 {#search-for-multiple-property-values}

속성의 여러 값을 검색하려는 경우 큰 그룹을 사용하지 않으려면 (`"A" or "B" or "C"`)에 여러 값을 제공할 수 있습니다. `property` 조건자:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

다중 값 속성의 경우 여러 값이 일치해야 할 수도 있습니다(`"A" and "B" and "C"`):

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.and=true&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.and=true
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

## 반환 항목 구체화 {#refining-what-is-returned}

기본적으로 QueryBuilder JSON 서블릿은 검색 결과의 각 노드에 대한 기본 속성 집합(예: 경로, 이름 및 제목)을 반환합니다. 반환되는 속성을 제어하기 위해 다음 중 하나를 수행할 수 있습니다.

지정

```xml
p.hits=full
```

이 경우 각 노드에 대한 모든 속성이 포함됩니다.

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
```

사용

```xml
p.hits=selective
```

가져올 속성을 지정합니다.

```xml
p.properties
```

공백으로 구분:

`http://<host>:<port>/bin/querybuilder.json?p.hits=selective&p.properties=sling%3aresourceType%20jcr%3aprimaryType&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=selective
p.properties=sling:resourceType jcr:primaryType
```

또한 쿼리 빌더 응답에 하위 노드를 포함할 수도 있습니다. 지정

```xml
p.nodedepth=n
```

위치 `n` 는 쿼리가 반환할 수준의 수입니다. 하위 노드를 반환하려면 속성 선택기에서 지정해야 합니다

```xml
p.hits=full
```

예:

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&p.nodedepth=5&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
p.nodedepth=5
```

## 기타 술어 {#morepredicates}

자세한 내용은 [Query Builder 설명 참조 페이지](query-builder-predicates.md).

다음을 확인할 수도 있습니다. [에 대한 Javadoc `PredicateEvaluator` 클래스](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html). 이러한 클래스에 대한 Javadoc에는 사용할 수 있는 속성 목록이 포함되어 있습니다.

클래스 이름의 접두사(예: `similar` 위치: [`SimilarityPredicateEvaluator`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html))은 입니다 *주요 성질* 클래스의 입니다. 이 속성은 쿼리에서 사용할 술어의 이름이기도 합니다(소문자로 표시).

이러한 주요 등록 정보의 경우 쿼리를 짧게 만든 다음 `similar=/content/en` 정규화된 변형 대신 `similar.similar=/content/en`. 클래스의 모든 비주요 속성에 대해 정규화된 양식을 사용해야 합니다.

## Query Builder API 사용 예 {#example-query-builder-api-usage}

```java
   String fulltextSearchTerm = "WKND";

    // create query description as hash map (simplest way, same as form post)
    Map<String, String> map = new HashMap<String, String>();

// create query description as hash map (simplest way, same as form post)
    map.put("path", "/content");
    map.put("type", "cq:Page");
    map.put("group.p.or", "true"); // combine this group with OR
    map.put("group.1_fulltext", fulltextSearchTerm);
    map.put("group.1_fulltext.relPath", "jcr:content");
    map.put("group.2_fulltext", fulltextSearchTerm);
    map.put("group.2_fulltext.relPath", "jcr:content/@cq:tags");

    // can be done in map or with Query methods
    map.put("p.offset", "0"); // same as query.setStart(0) below
    map.put("p.limit", "20"); // same as query.setHitsPerPage(20) below

    Query query = builder.createQuery(PredicateGroup.create(map), session);
    query.setStart(0);
    query.setHitsPerPage(20);

    SearchResult result = query.getResult();

    // paging metadata
    int hitsPerPage = result.getHits().size(); // 20 (set above) or lower
    long totalMatches = result.getTotalMatches();
    long offset = result.getStartIndex();
    long numberOfPages = totalMatches / 20;

    //Place the results in XML to return to client
    DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
    DocumentBuilder builder = factory.newDocumentBuilder();
    Document doc = builder.newDocument();

    //Start building the XML to pass back to the AEM client
    Element root = doc.createElement( "results" );
    doc.appendChild( root );

    // iterating over the results
    for (Hit hit : result.getHits()) {
       String path = hit.getPath();

      //Create a result element
      Element resultel = doc.createElement( "result" );
      root.appendChild( resultel );

      Element pathel = doc.createElement( "path" );
      pathel.appendChild( doc.createTextNode(path ) );
      resultel.appendChild( pathel );
    }
```

JSON(Query Builder) 서블릿을 사용하여 HTTP를 통해 실행된 동일한 쿼리:

`http://<host>:<port>/bin/querybuilder.json?path=/content&type=cq:Page&group.p.or=true&group.1_fulltext=WKND&group.1_fulltext.relPath=jcr:content&group.2_fulltext=WKND&group.2_fulltext.relPath=jcr:content/@cq:tags&p.offset=0&p.limit=20`

## 쿼리 저장 및 로드 {#storing-and-loading-queries}

나중에 사용할 수 있도록 쿼리를 저장소에 저장할 수 있습니다. 다음 `QueryBuilder` 다음을 제공합니다. `storeQuery` 다음 서명이 있는 메서드:

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

사용 시 [`QueryBuilder#storeQuery`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#storeQuery-com.day.cq.search.Query-java.lang.String-boolean-javax.jcr.Session-) 메서드, 해당 `Query` 다음 변수에 따라 파일 또는 속성으로 저장소에 저장됩니다. `createFile` 인수 값입니다. 다음 예에서는 를 저장하는 방법을 보여 줍니다. `Query` 경로로 `/mypath/getfiles` 파일로:

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

이전에 저장된 모든 쿼리는 다음을 사용하여 저장소에서 로드할 수 있습니다. [`QueryBuilder#loadQuery`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#loadQuery-java.lang.String-javax.jcr.Session-) 방법:

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

예: `Query` 경로에 저장됨 `/mypath/getfiles` 다음 코드 조각으로 로드할 수 있습니다.

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## 테스트 및 디버깅 {#testing-and-debugging}

Query Builder 쿼리를 재생하고 디버깅하기 위해에서 Query Builder 디버거 콘솔을 사용할 수 있습니다.

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

또는 의 Query Builder JSON 서블릿

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

다음 `path=/tmp` 는 단지 예시일 뿐입니다.

### 일반 디버깅 Recommendations {#general-debugging-recommendations}

### 로깅을 통해 설명 가능한 XPath 얻기 {#obtain-explain-able-xpath-via-logging}

설명 **모두** 대상 색인 세트에 대한 개발 주기 동안의 쿼리입니다.

1. QueryBuilder에 대해 DEBUG 로그를 활성화하여 기본 설명 가능한 XPath 쿼리를 얻습니다.
   * 다음으로 이동 `https://<host>:<port>/system/console/slinglog`. 다음에 대한 로거 만들기 `com.day.cq.search.impl.builder.QueryImpl` 위치: **디버그**.
1. 위의 클래스에 대해 DEBUG가 활성화되면 로그에 쿼리 빌더에서 생성한 XPath가 표시됩니다.
1. 연관된 Query Builder 쿼리에 대한 로그 항목에서 XPath 쿼리를 복사합니다. 예를 들면 다음과 같습니다.
   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]`
1. 쿼리 계획을 가져올 수 있도록 XPath 쿼리를 XPath로 쿼리 설명에 붙여넣습니다.

### Query Builder 디버거를 통해 설명 가능한 XPath 가져오기 {#obtain-explain-able-xpath-via-the-query-builder-debugger}

AEM Query Builder 디버거를 사용하여 설명 가능한 XPath 쿼리를 생성합니다.

![Query Builder 디버거](assets/query-builder-debugger.png)

1. Query Builder 디버거에서 Query Builder 쿼리를 제공합니다.
1. 검색 실행
1. 생성된 XPath 가져오기
1. 쿼리 계획을 가져올 수 있도록 XPath 쿼리를 XPath로 쿼리 설명에 붙여넣습니다.

>[!NOTE]
>
>비쿼리 빌더 쿼리(XPath, JCR-SQL2)를 쿼리 설명에 직접 제공할 수 있습니다.

## 로깅을 사용하여 쿼리 디버깅 {#debugging-queries-with-logging}

>[!NOTE]
>
>로거의 구성은 문서에 설명되어 있습니다 [로깅](/help/implementing/developing/introduction/logging.md).

이전 섹션에서 설명한 쿼리를 실행할 때 쿼리 빌더 구현의 로그 출력(INFO 수준) [테스트 및 디버깅:](#testing-and-debugging)

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: limit=20, offset=0[
    {group=group: or=true[
        {1_fulltext=fulltext: fulltext=WKND, relPath=jcr:content}
        {2_fulltext=fulltext: fulltext=WKND, relPath=jcr:content/@cq:tags}
    ]}
    {path=path: path=/content}
    {type=type: type=cq:Page}
]
com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]
com.day.cq.search.impl.builder.QueryImpl no filtering predicates
com.day.cq.search.impl.builder.QueryImpl query execution took 69 ms
```

필터링하거나 비교기별 사용자 지정 순서를 사용하는 술어 평가자를 사용하는 쿼리가 있는 경우 쿼리에 표시됩니다.

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: [
    {nodename=nodename: nodename=*.jar}
    {orderby=orderby: orderby=@jcr:content/jcr:lastModified}
    {type=type: type=nt:file}
]
com.day.cq.search.impl.builder.QueryImpl custom order by comparator: jcr:content/jcr:lastModified
com.day.cq.search.impl.builder.QueryImpl XPath query: //element(*, nt:file)
com.day.cq.search.impl.builder.QueryImpl filtering predicates: {nodename=nodename: nodename=*.jar}
com.day.cq.search.impl.builder.QueryImpl query execution took 272 ms
```

## Javadoc 링크 {#javadoc-links}

| **자바독** | **설명** |
|---|---|
| [com.day.cq.search](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/package-summary.html) | 기본 쿼리 빌더 및 쿼리 API |
| [com.day.cq.search.result](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/package-summary.html) | 결과 API |
| [com.day.cq.search.facet](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/package-summary.html) | 패싯 |
| [com.day.cq.search.facet.buckets](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | 버킷(패싯 내에 포함됨) |
| [com.day.cq.search.eval](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/package-summary.html) | 조건자 평가자 |
| [com.day.cq.search.facet.extractors](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | 패싯 추출기(평가자용) |
| [com.day.cq.search.writer](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/writer/package-summary.html) | Query Builder 서블릿에 대한 JSON 결과 히트 작성기(`/bin/querybuilder.json`) |
