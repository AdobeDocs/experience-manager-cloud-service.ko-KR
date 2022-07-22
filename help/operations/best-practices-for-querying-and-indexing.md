---
title: 쿼리 및 색인 생성에 대한 우수 사례
seo-title: Best Practices for Queries and Indexing
description: 이 문서에서는 인덱스 및 쿼리를 최적화하는 방법에 대한 지침을 제공합니다.
seo-description: This article provides guidelines on how to optimize your indexes and queries.
topic-tags: best-practices
source-git-commit: 85cbdaa6e6d01856005cb47f289d391fb44bd65e
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 0%

---


# 쿼리 및 색인 생성에 대한 우수 사례{#best-practices-for-queries-and-indexing}

AEM의 이전 버전과 달리, 색인에 대한 모든 운영 측면은 자동화되어 있습니다. 이를 통해 개발자는 효율적인 쿼리 및 해당 색인 정의를 만드는 데 집중할 수 있습니다.

## 쿼리를 사용해야 하는 경우 {#when-to-use-queries}

쿼리는 컨텐츠에 액세스할 수 있는 방법이지만 유일한 방법은 아닙니다. 이러한 이유로 쿼리가 컨텐츠에 액세스하는 가장 뛰어난 성능 방법인 경우 평가해야 합니다. 리포지토리의 컨텐츠에 다른 방법을 사용하여 더 나은 성능을 제공할 수 있는 경우가 많습니다.

### 저장소 및 분류 체계 디자인 {#repository-and-taxonomy-design}

저장소의 분류 체계를 디자인할 때 몇 가지 요소를 고려해야 합니다. 여기에는 액세스 제어, 로컬라이제이션, 구성 요소 및 페이지 속성 상속이 포함됩니다.

이러한 문제를 해결하는 분류법을 디자인하는 동안 색인 설계의 &quot;순회 기능&quot;을 고려해야 합니다. 이 컨텍스트에서 순회 기능은 경로를 기반으로 컨텐츠를 예측 가능하게 액세스할 수 있는 분류법의 기능입니다. 이렇게 하면 많은 쿼리를 실행해야 하는 것보다 쉽게 유지 관리할 수 있는 성능 시스템이 향상됩니다.

또한 분류법을 디자인할 때는 순서 지정이 중요한지 고려해야 합니다. 명시적 순서가 필요하지 않고 동위 노드의 수가 많은 경우 다음과 같이 순서가 지정되지 않은 노드 유형을 사용하는 것이 좋습니다 `sling:Folder` 또는 `oak:Unstructured`. 주문이 필요한 경우, `nt:unstructured` 및 `sling:OrderedFolder` 더 적절할 것 같습니다

### 구성 요소의 쿼리 {#queries-in-components}

쿼리는 AEM 시스템에서 수행되는 더 많은 과세 작업 중 하나일 수 있으므로 구성 요소에서 쿼리를 피하는 것이 좋습니다. 페이지를 렌더링할 때마다 몇 개의 쿼리가 실행되면 시스템의 성능이 저하될 수 있습니다. 구성 요소를 렌더링할 때 쿼리를 실행하지 않도록 하는 두 가지 전략이 있습니다. **탐색 노드** 및 **프리페치 결과**.

### 노드 탐색 {#traversing-nodes}

저장소가 필요한 데이터의 위치를 미리 알 수 있도록 설계된 경우 필요한 경로에서 이 데이터를 검색하는 코드를 배포하기 위해 쿼리를 실행하지 않고도 배포할 수 있습니다.

특정 카테고리에 맞는 콘텐츠를 렌더링하는 것이 예시입니다. 한 가지 방법은 컨텐츠를 카테고리의 항목을 표시하는 구성 요소를 채우기 위해 쿼리할 수 있는 카테고리 속성으로 구성하는 것입니다.

보다 나은 접근 방법은 이 컨텐츠를 카테고리별로 분류하여 수동으로 검색할 수 있도록 구성하는 것입니다.

예를 들어 다음과 유사한 분류법에 컨텐츠가 저장되는 경우

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

a `/content/myUnstructuredContent/parentCategory/childCategory` 노드를 간단히 검색할 수 있으며, 해당 하위 노드를 구문 분석하여 구성 요소를 렌더링하는 데 사용할 수 있습니다.

또한 작은 결과 세트 또는 균일한 결과 세트를 처리하는 경우 동일한 결과 세트를 반환하도록 쿼리를 만드는 대신 리포지토리를 트래버스하고 필요한 노드를 수집하는 것이 더 빠를 수 있습니다. 일반적으로 쿼리는 가능한 곳에서 피해야 합니다.

### 프리페치 결과 {#prefetching-results}

경우에 따라 구성 요소에 대한 컨텐츠 또는 요구 사항에 따라 필요한 데이터를 검색하는 방법으로 노드 순회를 사용할 수 없습니다. 이 경우 최적의 성능을 보장하기 위해 구성 요소를 렌더링하기 전에 필요한 쿼리를 실행해야 합니다.

구성 요소에 필요한 결과를 작성 시 계산할 수 있고 컨텐츠가 변경될 기대 상태가 없는 경우 변경이 완료된 후 쿼리를 실행할 수 있습니다.

데이터 또는 컨텐츠가 정기적으로 변경되는 경우 기본 데이터에 대한 업데이트를 위해 일정 또는 수신기를 통해 쿼리를 실행할 수 있습니다. 그런 다음 리포지토리의 공유 위치에 결과를 쓸 수 있습니다. 이 데이터가 필요한 모든 구성 요소는 런타임 시 쿼리를 실행할 필요 없이 이 단일 노드에서 값을 가져올 수 있습니다.
유사한 전략을 사용하여 결과를 메모리 내 캐시에 유지할 수 있습니다. 이 캐시는 시작 시 채워지고 변경 사항이 수행될 때마다 업데이트됩니다(JCR ObservationListener 또는 Sling ResourceChangeListener 사용).

## 쿼리 최적화 {#optimizing-queries}

Oak 설명서는 다음을 제공합니다. [쿼리 실행 방식의 개요](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing). 이 양식은 이 문서에 설명된 모든 최적화 활동의 기반입니다.

AEM as a Cloud Service에서는 효율적인 쿼리 구현을 지원하도록 설계된 쿼리 성능 도구를 제공합니다.
* 해당 성능 특성과 쿼리 계획이 있는 이미 실행된 쿼리를 표시합니다.
* 쿼리 계획을 표시하는 것에서부터 전체 쿼리 실행까지 다양한 수준에서 임시 쿼리를 수행할 수 있습니다.

쿼리 성능 도구는 [Cloud Manager의 개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#queries). 이전 버전의 AEM 6.x의 쿼리 성능 도구와 달리 AEM as a Cloud Service용 성능 쿼리 도구는 쿼리 실행 세부 사항에 대한 자세한 정보를 제공하며 이 도구를 사용하면 쿼리를 향상시키는 데 유용합니다.


이 차트에서는 쿼리 성능 도구를 사용하여 쿼리를 최적화하는 일반적인 방법을 설명합니다.
![쿼리 최적화 흐름](assets/query-optimization-flow.png)



### 인덱스 사용 {#use-an-index}

모든 쿼리는 최적의 성능을 제공하기 위해 인덱스를 사용해야 합니다. 대부분의 경우 기본적으로 제공되는 인덱스가 쿼리를 처리할 수 있을 정도로 충분해야 합니다.
경우에 따라 사용자 지정 속성을 기존 인덱스에 추가해야 하므로 이 인덱스를 사용하여 추가 제약 조건을 쿼리할 수 있습니다. 자세한 내용은 [컨텐츠 검색 및 색인 지정](/help/operations/indexing.md#changing-an-index) 자세한 내용 다음 [JCR 쿼리 체크시트](#jcr-query-cheatsheet) 특정 쿼리 유형을 지원하기 위해 인덱스에 대한 속성 정의를 찾는 방법을 설명합니다.



### 올바른 기준 사용

가장 효율적인 형식이므로 모든 쿼리에 대한 기본 제약 조건은 속성 일치여야 합니다. 속성 제약 조건을 더 추가하면 결과가 더 제한됩니다.
쿼리 엔진은 단일 색인만 고려합니다. 즉, 기존 색인이 사용자 지정 인덱스 속성을 추가하여 사용자 지정할 수 있고 사용자 지정해야 합니다.

다음 [JCR 쿼리 체크시트](#jcr-query-cheatsheet) 사용 가능한 제약 조건을 나열하고 색인 정의를 선택하도록 하는 방법을 설명합니다. 를 사용하십시오 [쿼리 성능 도구](#query-performance-tool) 쿼리를 테스트하고 올바른 인덱스가 사용되고 쿼리 엔진이 인덱스 외부의 제약 조건을 평가할 필요가 없도록 합니다.


### 순서 지정

특정 결과 순서가 요청된 경우 쿼리 엔진이 이를 수행하는 방법에는 두 가지가 있습니다.

1. 인덱스는 결과를 완전히 올바른 순서로 전달할 수 있습니다. 이는 정렬에 사용되는 속성에 주석을 달 경우 작동합니다 ```ordered=true``` 인덱스 정의에서 생성합니다.
2. 쿼리 엔진이 인덱스 외부에서 필터링을 수행해야 하거나 순서 등록 정보에 주석을 달 수 없는 경우 ```ordered=true``` 등록 정보인 쿼리 엔진도 순서 지정 프로세스를 수행합니다. 이 경우 전체 결과 세트를 정렬하기 위해 메모리로 읽어야 합니다. 이 값은 첫 번째 옵션보다 훨씬 느립니다.





### 결과 크기 제한

쿼리 결과의 검색된 크기는 쿼리 성능에 중요한 요소입니다. 따라서 지연 방식으로 가져오므로 10&#39;000 결과를 가져오는 것과 비교하여 런타임 및 메모리 사용량에 차이가 있습니다.

즉, 모든 결과를 가져오는 경우 결과 세트의 크기만 올바르게 결정할 수 있습니다. 이러한 이유로 가져온 결과 세트는 쿼리를 늘려서 항상 제한되어야 합니다(참조: [JCR 쿼리 체크시트](#jcr-query-cheatsheet) 자세한 내용) 또는 결과 읽기를 제한하여
이러한 제한은 쿼리 엔진이 **순회 제한** 100,000개 노드 중 하나를 선택하면 쿼리가 강제 중지됩니다.

섹션을 참조하십시오 [큰 결과가 있는 쿼리](#queries-with-large-result-sets) 아래에 큰 결과 세트를 완전히 처리해야 하는 경우.


## JCR 쿼리 체크시트

효율적인 JCR 쿼리 및 색인 정의 만들기를 지원하려면 [JCR 쿼리 치트 시트](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html#jcrquerycheatsheet) 는 개발 중에 다운로드하여 참조로 사용할 수 있습니다. 여기에는 쿼리 성능 측면에서 다르게 동작하는 여러 시나리오를 다루는 QueryBuilder, XPath 및 SQL-2에 대한 샘플 쿼리가 포함되어 있습니다. 또한 Oak 인덱스를 작성하거나 사용자 지정하는 방법에 대한 권장 사항을 제공합니다. 이 치트 시트의 내용은 AEM 6.5 및 AEM as a Cloud Service에 적용됩니다.


## 큰 결과 세트가 있는 쿼리

큰 결과 세트가 있는 쿼리를 피하는 것이 좋지만 큰 결과를 처리해야 하는 유효한 경우가 있습니다. 결과 크기를 사전에 알 수 없는 경우가 많으므로 처리를 안정화하기 위해 몇 가지 주의 사항이 적용되어야 합니다.

* 요청 내에서 쿼리를 실행해서는 안 됩니다. 대신 Sling 작업 또는 AEM 워크플로우의 일부로 쿼리를 실행해야 합니다. 이러한 매개 변수는 총 런타임에서 제한이 없으며 쿼리 및 그 결과 처리 중에 인스턴스가 종료되는 경우 다시 시작됩니다.
* 100개의 노드라는 쿼리 제한을 극복하려면 사용할 것을 고려해야 합니다 [키세트 페이지 매김](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) 여러 하위 쿼리에서 쿼리를 분할합니다.



## 저장소 탐색 쿼리

저장소를 탐색하는 쿼리는 인덱스를 사용하지 않으며 다음과 같이 메시지를 기록합니다.

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

이 로그 조각에는 관련 정보가 포함되어 있습니다.

* 쿼리 자체: ```//* ```
* 이 쿼리를 실행한 java 코드: ```com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics```; 이렇게 하면 이 쿼리의 작성자를 식별하는 데 도움이 됩니다.

이 정보를 사용하면 다음에 설명된 메서드를 사용하여 이 쿼리를 최적화할 수 있습니다. [쿼리 최적화](#optimizing-queries).