---
title: 쿼리 빌더 API
description: Asset Share 쿼리 빌더의 기능은 Java&trade; API 및 REST API를 통해 노출됩니다.
exl-id: d5f22422-c9da-4c9d-b81c-ffa5ea7cdc87
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1830'
ht-degree: 0%

---

# 쿼리 빌더 API {#query-builder-api}

Query Builder를 사용하면 AEM의 콘텐츠 저장소를 쉽게 쿼리할 수 있습니다. 기능은 Java™ API 및 REST API를 통해 노출됩니다. 이 문서에서는 이러한 API에 대해 설명합니다.

서버측 쿼리 빌더([`QueryBuilder`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html))가 쿼리 설명을 수락하고 XPath 쿼리를 만들고 실행하며 선택적으로 결과 집합을 필터링하고 필요한 경우 패싯을 추출합니다.

쿼리 설명은 단순히 조건자 집합([`Predicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/Predicate.html))입니다. XPath의 `jcr:contains()` 함수에 해당하는 전체 텍스트 조건자를 예로 들 수 있습니다.

각 술어 유형에 대해 XPath, 필터링 및 Facet 추출을 위해 해당 특정 술어를 처리하는 방법을 알고 있는 평가기 구성 요소([`PredicateEvaluator`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html))가 있습니다. OSGi 구성 요소 런타임을 통해 플러그인된 사용자 지정 평가자를 쉽게 만들 수 있습니다.

REST API는 JSON으로 전송되는 응답과 함께 HTTP를 통해 동일한 기능에 대한 액세스를 제공합니다.

>[!NOTE]
>
>QueryBuilder API는 JCR API를 사용하여 빌드됩니다. OSGi 번들 내에서 JCR API를 사용하여 AEM JCR을 쿼리할 수도 있습니다. 자세한 내용은 [JCR API를 사용하여 Adobe Experience Manager 데이터 쿼리](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/query-builder/querybuilder-api.html)를 참조하십시오.

## Gem 세션 {#gem-session}

[AEM Gems](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/overview.html)은(는) Adobe 전문가가 제공하는 Adobe Experience Manager에 대한 일련의 기술적인 분석입니다.

[쿼리 빌더 전용 세션을 검토](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2017/aem-search-forms-using-querybuilder.html)하여 도구의 개요 및 사용을 확인할 수 있습니다.

## 샘플 쿼리 {#sample-queries}

이러한 샘플은 Java™ 속성 스타일 표기법으로 제공됩니다. Java™ API와 함께 사용하려면 다음 API 샘플과 같이 Java™ `HashMap`을(를) 사용하십시오.

`QueryBuilder` JSON 서블릿의 경우 각 예제는 AEM 설치(기본 위치: `http://<host>:<port>`)에 대한 샘플 링크를 포함합니다. 이러한 링크를 사용하기 전에 AEM 인스턴스에 로그온합니다.

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

다음 쿼리 **10개의 결과를 반환합니다**(또는 정확하게는 최대 10개)지만 **사용 가능한 히트 수:**&#x200B;을(를) 알려 줍니다.

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

매개 변수 `p.limit=-1`을(를) 사용하는 동일한 쿼리 **모든 결과를 반환**(인스턴스에 따라 높은 숫자일 수 있음):

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

`p.guessTotal` 매개 변수의 목적은 실행 가능한 최소 `p.offset` 및 `p.limit` 값을 결합하여 표시할 수 있는 적절한 수의 결과를 반환하는 것입니다. 이 매개 변수를 사용하면 결과 세트 크기가 클수록 성능이 향상됩니다. 또한 이 매개 변수는 전체 합계를 계산하는 것(예: `result.getSize()` 호출)과 Oak 엔진 및 인덱스까지 최적화된 전체 결과 집합을 읽는 것을 방지합니다. 이 프로세스는 실행 시간과 메모리 사용량 모두에서 수십만 개의 결과가 있을 때 상당한 차이가 될 수 있습니다.

매개 변수의 단점은 사용자가 정확한 합계를 보지 못한다는 것입니다. 그러나 `p.guessTotal=1000`과(와) 같은 최소 숫자를 설정할 수 있으므로 항상 최대 1000개까지 읽습니다. 이러한 방식으로 작은 결과 세트에 대한 정확한 합계를 얻지만, 더 많은 경우 &quot;및 더 많은&quot;만 표시할 수 있습니다.

아래 쿼리에 `p.guessTotal=true`을(를) 추가하여 작동 방식을 확인하십시오.

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.guessTotal=true
orderby=path
```

쿼리에서 `0` 오프셋이 있는 `10`개 결과의 `p.limit` 기본값을 반환합니다.

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

숫자 값을 사용하여 최대 결과의 사용자 지정 수까지 계산할 수도 있습니다. 위와 동일한 쿼리를 사용하되 `p.guessTotal`의 값을 `50`(으)로 변경합니다.

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

* 총 히트 수([SearchResult.getTotalMatches()](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/SearchResult.html#getTotalMatches) 또는 `querybuilder.json` 응답의 합계)의 정확한 개수를 가져와 표시합니다.
* 쿼리 빌더를 호출하는 `guessTotal`을(를) 100으로 설정합니다.

* 응답은 다음과 같은 결과를 얻을 수 있습니다.

   * `total=43`, `more=false` - 총 히트 수가 43개임을 나타냅니다. UI는 최대 10개의 결과를 첫 번째 페이지의 일부로 표시하고 다음 3개 페이지에 대한 페이지 매김을 제공할 수 있습니다. 이 구현을 사용하여 **&quot;43개의 검색 결과&quot;**&#x200B;와 같은 설명 텍스트를 표시할 수도 있습니다.
   * `total=100`, `more=true` - 총 히트 수가 100보다 크고 정확한 개수를 알 수 없음을 나타냅니다. UI는 첫 번째 페이지의 일부로 최대 10개를 표시하고 다음 10개 페이지에 대한 페이지 매김을 제공할 수 있습니다. 이 기능을 사용하여 **&quot;100개 이상의 검색 결과&quot;**&#x200B;와 같은 텍스트를 표시할 수도 있습니다. 사용자가 다음 페이지로 이동하면 쿼리 빌더를 호출하면 `guessTotal`과(와) `offset` 및 `limit` 매개 변수의 제한이 증가합니다.

또한 사용자 인터페이스가 무한 스크롤을 사용하여 Query Builder가 정확한 히트 수를 확인하지 않도록 해야 하는 경우에 `guessTotal`을(를) 사용합니다.

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

명시적 태그 ID를 알고 있는 경우 예제와 같이 `tagid` 조건자를 사용하십시오.

태그 제목 경로(공백 없음)에 대해 `tag` 술어를 사용하십시오.

앞의 예제에서는 페이지(`cq:Page`개 노드)를 검색하고 있으므로 `tagid.property` 조건자에 대해 해당 노드의 상대 경로(`jcr:content/cq:tags`)를 사용합니다. 기본적으로 `tagid.property`은(는) `cq:tags`이(가) 됩니다.

### 여러 경로 검색(그룹 사용) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

이 쿼리는 *group*(이름이 `group`)을 사용합니다. 이 그룹은 괄호가 보다 표준 표기법으로 사용되는 것처럼 쿼리 내에서 하위 식을 구분하는 역할을 합니다. 예를 들어 이전 쿼리는 다음과 같이 더 익숙한 스타일로 표현될 수 있습니다.

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

이 예제의 그룹 내에서 `path` 조건자가 여러 번 사용됩니다. 술어의 두 인스턴스를 구분하고 순서를 지정하려면(일부 술어에 순서 지정 필요) 술어 앞에 `N_`을 붙여야 합니다. 여기서 `N`은(는) 순서 지정 색인입니다. 앞의 예제에서 결과 조건자는 `1_path`과(와) `2_path`입니다.

`p.or`의 `p`은(는) `1_path`과(와) 같은 그룹의 하위 조건자가 아니라 뒤에 오는 것(이 경우 `or`)이 그룹의 *매개 변수*&#x200B;임을 나타내는 특수 구분 기호입니다.

`p.or`을(를) 지정하지 않으면 모든 조건자가 함께 AND됩니다. 즉, 각 결과는 모든 조건자를 만족해야 합니다.

>[!NOTE]
>
>다른 술어에 대해서도 하나의 쿼리에 동일한 숫자 접두사를 사용할 수 없습니다.

### 속성 검색 {#search-for-properties}

여기에서 `cq:template` 속성을 사용하여 지정된 템플릿의 모든 페이지를 검색하고 있습니다.

`http://<host>:<port>/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

단점은 페이지 자체가 아니라 페이지의 `jcr:content` 노드가 반환된다는 것입니다. 이 문제를 해결하려면 상대 경로로 검색할 수 있습니다.

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

속성의 여러 값(`"A" or "B" or "C"`)을 검색하려는 경우 큰 그룹을 피하려면 `property` 조건자에 여러 값을 제공할 수 있습니다.

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

다중 값 속성의 경우 여러 값이 일치해야 할 수도 있습니다(`"A" and "B" and "C"`).

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

여기서 `n`은(는) 쿼리가 반환할 수준의 수입니다. 하위 노드를 반환하려면 속성 선택기에서 지정해야 합니다

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

자세한 조건자는 [Query Builder 조건자 참조 페이지](query-builder-predicates.md)를 참조하십시오.

`PredicateEvaluator` 클래스](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)에 대한 [Javadoc을 확인할 수도 있습니다. 이러한 클래스에 대한 Javadoc에는 사용할 수 있는 속성 목록이 포함되어 있습니다.

클래스 이름의 접두사(예: [`SimilarityPredicateEvaluator`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html)의 `similar`)는 클래스의 *principal 속성*&#x200B;입니다. 이 속성은 쿼리에서 사용할 술어의 이름이기도 합니다(소문자로 표시).

이러한 주 속성의 경우 쿼리를 줄이고 정규화된 변형 `similar.similar=/content/en` 대신 `similar=/content/en`을(를) 사용할 수 있습니다. 클래스의 모든 비주요 속성에 대해 정규화된 양식을 사용해야 합니다.

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

나중에 사용할 수 있도록 쿼리를 저장소에 저장할 수 있습니다. `QueryBuilder`에서 `storeQuery` 메서드에 다음 서명을 제공합니다.

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

[`QueryBuilder#storeQuery`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#storeQuery-com.day.cq.search.Query-java.lang.String-boolean-javax.jcr.Session-) 메서드를 사용하는 경우 지정된 `Query`은(는) `createFile` 인수 값에 따라 파일이나 속성으로 리포지토리에 저장됩니다. 다음 예제에서는 `Query`을(를) `/mypath/getfiles` 경로에 파일로 저장하는 방법을 보여 줍니다.

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

이전에 저장된 모든 쿼리는 [`QueryBuilder#loadQuery`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#loadQuery-java.lang.String-javax.jcr.Session-) 메서드를 사용하여 저장소에서 로드할 수 있습니다.

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

예를 들어 `/mypath/getfiles` 경로에 저장된 `Query`은(는) 다음 코드 조각으로 로드할 수 있습니다.

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## 테스트 및 디버깅 {#testing-and-debugging}

Query Builder 쿼리를 재생하고 디버깅하기 위해에서 Query Builder 디버거 콘솔을 사용할 수 있습니다.

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

또는 의 Query Builder JSON 서블릿

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

`path=/tmp`은(는) 예제입니다.

### 일반 디버깅 Recommendations {#general-debugging-recommendations}

### 로깅을 통해 설명 가능한 XPath 얻기 {#obtain-explain-able-xpath-via-logging}

대상 인덱스 집합에 대해 개발 주기 동안 **모든** 쿼리를 설명합니다.

1. QueryBuilder에 대해 DEBUG 로그를 활성화하여 기본 설명 가능한 XPath 쿼리를 얻습니다.
   * `https://<host>:<port>/system/console/slinglog`(으)로 이동합니다. **DEBUG**&#x200B;에서 `com.day.cq.search.impl.builder.QueryImpl`에 대한 로거를 만듭니다.
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
>로거의 구성은 [로깅](/help/implementing/developing/introduction/logging.md) 문서에 설명되어 있습니다.

이전 섹션 [테스트 및 디버깅:](#testing-and-debugging)에서 설명한 쿼리를 실행할 때 쿼리 빌더 구현의 로그 출력(INFO 수준)

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

| **Javadoc** | **설명** |
|---|---|
| [com.day.cq.search](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/package-summary.html) | 기본 쿼리 빌더 및 쿼리 API |
| [com.day.cq.search.result](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/package-summary.html) | 결과 API |
| [com.day.cq.search.facet](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/package-summary.html) | 패싯 |
| [com.day.cq.search.facet.buckets](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | 버킷(패싯 내에 포함됨) |
| [com.day.cq.search.eval](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/package-summary.html) | 조건자 평가자 |
| [com.day.cq.search.facet.extractors](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | 패싯 추출기(평가자용) |
| [com.day.cq.search.writer](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/writer/package-summary.html) | Query Builder 서블릿(`/bin/querybuilder.json`)에 대한 JSON 결과 히트 기록기 |
