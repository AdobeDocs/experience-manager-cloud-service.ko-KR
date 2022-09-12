---
title: 쿼리 빌더 API
description: Asset Share Query Builder의 기능은 Java API 및 REST API를 통해 노출됩니다.
exl-id: d5f22422-c9da-4c9d-b81c-ffa5ea7cdc87
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '2039'
ht-degree: 0%

---

# 쿼리 빌더 API {#query-builder-api}

Query Builder에서는 AEM의 컨텐츠 저장소를 쉽게 쿼리하는 방법을 제공합니다. 기능은 Java API 및 REST API를 통해 노출됩니다. 이 문서에서는 이러한 API에 대해 설명합니다.

서버측 쿼리 빌더([`QueryBuilder`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html))은 쿼리 설명을 적용하고, XPath 쿼리를 만들고 실행하고, 원하는 경우 결과 세트를 필터링하고, 패싯도 추출합니다.

쿼리 설명은 단순히 설명 집합입니다([`Predicate`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/Predicate.html)). 예로는 `jcr:contains()` 함수 내에 있어야 합니다.

각 설명 유형에 대해 평가기 구성 요소([`PredicateEvaluator`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)) XPath, 필터링 및 패싯 추출에 대한 특정 설명을 처리하는 방법을 알고 있습니다. OSGi 구성 요소 런타임을 통해 플러그인이 되는 사용자 정의 평가자를 만드는 것은 매우 쉽습니다.

REST API는 JSON으로 전송되는 응답을 사용하여 HTTP를 통해 정확히 동일한 기능에 대한 액세스 권한을 제공합니다.

>[!NOTE]
>
>QueryBuilder API는 JCR API를 사용하여 빌드됩니다. OSGi 번들 내에서 JCR API를 사용하여 AEM JCR을 쿼리할 수도 있습니다. 자세한 내용은 [JCR API를 사용하여 Adobe Experience Manager 데이터 쿼리](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html).

## Gem 세션 {#gem-session}

[AEM Gems](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-index.html) 는 Adobe 전문가가 제공하는 Adobe Experience Manager에 대한 일련의 기술적인 분석입니다.

다음을 수행할 수 있습니다 [query builder 전용 세션 검토](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-search-forms-using-querybuilder.html) 를 참조하십시오.

## 샘플 쿼리 {#sample-queries}

이러한 샘플은 Java 속성 스타일 표기법으로 제공됩니다. Java API에서 사용하려면 Java를 사용하십시오 `HashMap` 를 설정하는 것이 좋습니다.

대상 `QueryBuilder` JSON 서블릿, 각 예에는 AEM 설치(기본 위치: `http://<host>:<port>`). 이러한 링크를 사용하려면 먼저 AEM 인스턴스에 로그인해야 합니다.

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

다음 쿼리는 **10개의 결과 반환** (또는 최대 10개까지 정밀하게) **히트 수:** 실제로 사용 가능한 사항:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

동일한 쿼리(매개 변수 사용) `p.limit=-1`) **모든 결과 반환** (인스턴스에 따라 숫자가 높을 수 있습니다.)

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

의 목적 `p.guessTotal` 매개 변수는 최소 실행 가능한 결과를 결합하여 표시할 수 있는 적절한 수의 결과를 반환하는 것입니다 `p.offset` 및 `p.limit` 값. 이 매개 변수를 사용하면 큰 결과 세트를 사용하여 성능이 향상됩니다. 따라서 전체 합계를 계산하지 않습니다(예: 호출) `result.getSize()`)을 클릭하고 전체 결과 세트를 읽고 OAK 엔진 및 색인까지 최적화했습니다. 이는 실행 시간과 메모리 사용 모두에서 수십만 개의 결과가 있을 때 큰 차이가 될 수 있습니다.

매개 변수의 단점은 사용자가 정확한 합계를 보지 못한다는 것입니다. 그러나 다음과 같은 최소 숫자를 설정할 수 있습니다 `p.guessTotal=1000` 따라서 항상 최대 1000까지 읽히게 되므로 더 작은 결과 세트에 대한 정확한 합계를 얻을 수 있지만, 그 이상일 경우 &quot;및&quot;만 표시할 수 있습니다.

추가 `p.guessTotal=true` 아래 쿼리를 클릭하여 작동 방식을 확인합니다.

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.guessTotal=true
orderby=path
```

쿼리는 `p.limit` 기본값 `10` 결과 `0` offset:

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

최대 사용자 지정 최대 결과 수를 계산하기 위해 숫자 값을 사용할 수도 있습니다. 위와 동일한 쿼리를 사용하지만 값을 변경합니다. `p.guessTotal` to `50`:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=50&orderby=path`

오프셋은 0이고, 기본 제한인 10개의 결과에 동일한 숫자가 반환되지만, 최대 50개의 결과만 표시됩니다.

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### 페이지 매김 구현 {#implementing-pagination}

기본적으로 Query Builder 는 히트 수도 제공합니다. 결과 크기에 따라 정확한 카운트를 결정하는 데 액세스 제어의 모든 결과를 확인하는 데 시간이 오래 걸릴 수 있습니다. 대부분 합계는 최종 사용자 UI에 대한 페이지 매김을 구현하는 데 사용됩니다. 정확한 개수를 결정하려면 guessTotal 기능을 사용하여 페이지 매김을 구현하는 것이 좋습니다.

예를 들어 UI는 다음 접근 방식을 조정할 수 있습니다.

* 총 히트 수([SearchResult.getTotalMatches()](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/SearchResult.html#getTotalMatches) 또는 합계에 `querybuilder.json` 응답)이 100보다 작거나 같습니다.
* 설정 `guessTotal` Query Builder를 호출하는 동안 100까지 오류가 발생했습니다.

* 응답에는 다음 결과가 있을 수 있습니다.

   * `total=43`, `more=false` - 총 히트 수가 43개임을 나타냅니다. UI는 첫 번째 페이지의 일부로 최대 10개의 결과를 표시하고 다음 3개 페이지에 대한 페이지 매김을 제공할 수 있습니다. 이 구현을 사용하여 다음과 같은 설명 텍스트를 표시할 수도 있습니다. **&quot;43개의 결과 발견&quot;**.
   * `total=100`, `more=true` - 총 히트 수가 100개를 초과하고 정확한 수를 알 수 없음을 나타냅니다. UI는 첫 번째 페이지의 일부로 최대 10개까지 표시할 수 있고 다음 10페이지에 대한 페이지 매기기를 제공할 수 있습니다. 다음과 같은 텍스트를 표시하는 데 사용할 수도 있습니다 **&quot;100개 이상의 결과 발견&quot;**. 사용자가 Query Builder에 대한 다음 페이지 호출로 이동하면 제한이 증가합니다. `guessTotal` 그리고 `offset` 및 `limit` 매개 변수.

`guessTotal` Query Builder가 정확한 히트 수를 확인하지 않도록 UI에서 무한 스크롤을 사용해야 하는 경우에도 사용해야 합니다.

### jar 파일을 찾아 가장 최신 파일부터 순서대로 정렬합니다. {#find-jar-files-and-order-them-newest-first}

`http://<host>:<port>/bin/querybuilder.json?type=nt:file&nodename=*.jar&orderby=@jcr:content/jcr:lastModified&orderby.sort=desc`

```xml
type=nt:file
nodename=*.jar
orderby=@jcr:content/jcr:lastModified
orderby.sort=desc
```

### 모든 페이지를 찾아 마지막으로 수정한 순서대로 정렬합니다. {#find-all-pages-and-order-them-by-last-modified}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
```

### 모든 페이지를 찾아 마지막으로 수정한 후 내림차순으로 정렬합니다. {#find-all-pages-and-order-them-by-last-modified-but-descending}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified&orderby.sort=desc`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
orderby.sort=desc
```

### 전체 텍스트 검색, 점수로 정렬됨 {#fulltext-search-ordered-by-score}

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

를 사용하십시오 `tagid` 는 명시적 태그 ID를 알고 있는 경우 예와 같이 술어를 제공합니다.

를 사용하십시오 `tag` 태그 제목 경로 설명(공백 없음).

이전 예에서 페이지(`cq:Page` nodes) 를 사용하려면 해당 노드의 상대 경로를 `tagid.property` 조건자 `jcr:content/cq:tags`. 기본적으로 `tagid.property` 단지 `cq:tags`.

### 여러 경로 검색(그룹 사용) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

이 쿼리는 *그룹* (이름이 지정됨) `group`). 괄호가 더 표준 표기법에서 하는 것처럼 쿼리 내에서 하위 표현식을 구분하는 데 사용됩니다. 예를 들어 이전 쿼리는 다음과 같이 더 친숙한 스타일로 표시될 수 있습니다.

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

예제의 그룹 내에서는 `path` 조건부가 여러 번 사용됩니다. 조건자의 두 인스턴스를 구분하고 순서를 지정하려면(일부 조건자에 대해 순서 지정이 필요) 조건자에 접두사를 붙여야 합니다 `N_` 여기서 `N` 는 주문 색인입니다. 이전 예에서 결과 조건자는 다음과 같습니다 `1_path` 및 `2_path`.

다음 `p` in `p.or` 는 다음 항목을 나타내는 특수 구분 기호입니다(이 경우 `or`)은 *매개 변수* 그룹의 하위 조건자가 아니라 `1_path`.

없는 경우 `p.or` 이 지정되면 모든 조건자가 ANDed를 함께 사용합니다. 즉, 각 결과는 모든 조건자를 만족해야 합니다.

>[!NOTE]
>
>서로 다른 조건에도 불구하고 하나의 쿼리에서 동일한 숫자 접두어를 사용할 수 없습니다.

### 속성 검색 {#search-for-properties}

여기서는 다음을 사용하여 주어진 템플릿의 모든 페이지를 검색합니다 `cq:template` 속성:

`http://<host>:<port>/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

이것은 `jcr:content` 페이지 자체가 아니라 페이지의 노드가 반환됩니다. 이를 해결하기 위해 상대 경로별로 검색할 수 있습니다.

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3acontent%2fcq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPage`

```xml
type=cq:Page
property=jcr:content/cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

### 여러 속성 검색 {#search-for-multiple-properties}

속성 설명을 여러 번 사용하는 경우 번호 접두사를 다시 추가해야 합니다.

`http://<host>:<port>/bin/querybuilder.json?1_property=jcr%3acontent%2fcq%3atemplate&1_property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&2_property=jcr%3acontent%2fjcr%3atitle&2_property.value=Cycling%20Tuscany&type=cq%3aPage`

```xml
type=cq:Page
1_property=jcr:content/cq:template
1_property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
2_property=jcr:content/jcr:title
2_property.value=Cycling Tuscany
```

### 여러 속성 값 검색 {#search-for-multiple-property-values}

속성(`"A" or "B" or "C"`)를 채울 수도 있고, `property` 설명:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

다중 값 속성의 경우 여러 값이 일치하는지(`"A" and "B" and "C"`):

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.and=true&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.and=true
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

## 반환되는 항목 세분화하기 {#refining-what-is-returned}

기본적으로 QueryBuilder JSON 서블릿은 검색 결과의 각 노드(예: 경로, 이름, 제목 등)에 대한 기본 속성 세트를 반환합니다. 반환되는 속성을 제어하려면 다음 중 하나를 수행할 수 있습니다.

지정

```xml
p.hits=full
```

이 경우 각 노드에 대해 모든 속성이 포함됩니다.

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

그리고 가져올 속성을 지정합니다

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

Query Builder 응답에 하위 노드를 포함할 수도 있습니다. 이를 수행하려면 다음을 지정해야 합니다

```xml
p.nodedepth=n
```

여기서 `n` 은 쿼리에서 반환할 레벨 수입니다. 하위 노드를 반환하려면 속성 선택기에서 지정해야 합니다

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

## 추가 설명 {#morepredicates}

자세한 내용은 [Query Builder 설명 참조 페이지](query-builder-predicates.md).

또한 [용 Javadoc `PredicateEvaluator` 클래스](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html). 이러한 클래스의 Javadoc에는 사용할 수 있는 속성 목록이 포함되어 있습니다.

클래스 이름의 접두사(예: `similar` in [`SimilarityPredicateEvaluator`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html))은 *주체* Adobe Social이 사용자 ID로 분류되지 않습니다. 이 속성은 쿼리에 사용할 조건자의 이름이기도 합니다(소문자는).

이러한 주체 속성의 경우 쿼리를 줄이고 사용할 수 있습니다 `similar=/content/en` 정규화된 변형 대신 `similar.similar=/content/en`. 정규화된 양식은 클래스의 모든 비주체 속성에 사용해야 합니다.

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

쿼리는 나중에 사용할 수 있도록 저장소에 저장할 수 있습니다. 다음 `QueryBuilder` 은 `storeQuery` 다음 서명이 있는 메서드:

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

를 사용할 때 [`QueryBuilder#storeQuery`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#storeQuery-com.day.cq.search.Query-java.lang.String-boolean-javax.jcr.Session-) 메서드, 지정된 `Query` 는 저장소에 `createFile` 인수 값. 다음 예제는 `Query` 경로 `/mypath/getfiles` 로서의 파일:

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

이전에 저장된 쿼리는 [`QueryBuilder#loadQuery`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#loadQuery-java.lang.String-javax.jcr.Session-) 메서드:

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

예: `Query` 경로에 저장 `/mypath/getfiles` 다음 코드 조각에 의해 로드될 수 있습니다.

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## 테스트 및 디버깅 {#testing-and-debugging}

Query Builder 쿼리 주위에 재생하고 디버깅하기 위해

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

또는 Query Builder JSON 서블릿( )을

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

`path=/tmp` 는 예일 뿐입니다.

### 일반 디버깅 Recommendations {#general-debugging-recommendations}

### 로깅을 통해 탐색 가능한 XPath 획득 {#obtain-explain-able-xpath-via-logging}

설명 **모두** 대상 인덱스 세트에 대한 개발 주기 동안 질의합니다.

1. QueryBuilder에 대해 DEBUG 로그를 활성화하여 실행 가능한 기본 XPath 쿼리를 가져옵니다.
   * 다음으로 이동 `https://<host>:<port>/system/console/slinglog`. 에 대한 새 로거 만들기 `com.day.cq.search.impl.builder.QueryImpl` at **디버그**.
1. 위의 클래스에 대해 DEBUG가 활성화되면 로그에 Query Builder에서 생성한 XPath가 표시됩니다.
1. 연결된 Query Builder 쿼리의 로그 항목에서 XPath 쿼리를 복사합니다. 예:
   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]`
1. XPath 쿼리를 XPath로 Explain Query에 붙여 넣어 쿼리 계획을 가져옵니다.

### Query Builder Debugger를 통해 탐색 가능한 XPath 가져오기 {#obtain-explain-able-xpath-via-the-query-builder-debugger}

AEM Query Builder 디버거를 사용하여 명시적 XPath 쿼리를 생성합니다.

![Query Builder 디버거](assets/query-builder-debugger.png)

1. Query Builder 디버거에서 Query Builder 쿼리를 제공합니다.
1. 검색 실행
1. 생성된 XPath 가져오기
1. XPath 쿼리를 XPath로 Explain Query에 붙여 넣어 쿼리 계획을 가져옵니다

>[!NOTE]
>
>Query Builder 쿼리(XPath, JCR-SQL2)가 아닌 쿼리를 Explain Query에 직접 제공할 수 있습니다.

## 로깅을 사용하여 쿼리 디버깅 {#debugging-queries-with-logging}

>[!NOTE]
>
>로거의 구성은 문서에 설명되어 있습니다 [로깅](/help/implementing/developing/introduction/logging.md).

이전 섹션에 설명된 쿼리를 실행할 때 쿼리 빌더 구현의 로그 출력(INFO 수준)입니다 [테스트 및 디버깅:](#testing-and-debugging)

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

비교기로 사용자 지정 순서를 사용하는 조건자 평가자를 사용하여 쿼리가 있거나 비교기를 사용하여 필터링된 경우 이 값이 쿼리에 기록됩니다.

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

| **Javadoc** | **설명** |
|---|---|
| [com.day.cq.search](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/package-summary.html) | 기본 쿼리 빌더 및 쿼리 API |
| [com.day.cq.search.result](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/package-summary.html) | 결과 API |
| [com.day.cq.search.facets](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/package-summary.html) | 패싯 |
| [com.day.cq.search.facets.bucket](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | 버킷(패싯에 포함됨) |
| [com.day.cq.search.eval](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/package-summary.html) | 설명 평가자 |
| [com.day.cq.search.facets.extractors](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | 패싯 추출기(평가자용) |
| [com.day.cq.search.writer](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/writer/package-summary.html) | Query Builder 서블릿(`/bin/querybuilder.json`) |
