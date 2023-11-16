---
title: 쿼리 및 색인화 모범 사례
description: Adobe의 모범 사례 가이드라인에 기반하여 색인 및 쿼리를 최적화하는 방법에 대해 알아봅니다.
topic-tags: best-practices
exl-id: 37eae99d-542d-4580-b93f-f454008880b1
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '3133'
ht-degree: 47%

---

# 쿼리 및 색인화 모범 사례 {#query-and-indexing-best-practices}

AEM as a Cloud Service에서는 색인화와 관련된 모든 운영 측면이 자동화됩니다. 이를 통해 개발자는 효율적인 쿼리와 그에 해당하는 색인 정의를 생성하는 데 집중할 수 있습니다.

## 쿼리 사용 시기 {#when-to-use-queries}

쿼리는 콘텐츠에 액세스하는 방법 중 하나이지만 유일한 방법인 것은 아닙니다. 많은 경우에서 기타 수단을 통해 더 효과적으로 저장소의 콘텐츠에 액세스할 수 있습니다. 해당되는 사용 사례에서 콘텐츠에 액세스할 수 있는 가장 효율적인 최선의 방법이 쿼리가 맞는지 고려해야 합니다.

### 저장소 및 분류법 디자인 {#repository-and-taxonomy-design}

저장소 분류법을 디자인할 때 여러 가지 요인을 고려해야 합니다. 여기에는 액세스 제어, 지역화, 구성 요소 및 페이지 속성 상속 등이 포함됩니다.

이러한 우려사항을 고려한 분류법을 디자인하는 동안, 색인화 디자인의 &quot;트래버스 가능성&quot; 또한 고려하는 것이 중요합니다. 이 맥락에서 트래버스 가능성이란 콘텐츠가 그 경로에 따라 예측 가능한 방식으로 액세스될 수 있게 하는 분류법의 기능을 말합니다. 이는 여러 개의 쿼리를 실행해야 하는 시스템에 비해 유지 관리가 더 용이한 보다 효율적인 시스템을 완성합니다.

또한 분류법을 디자인할 때는 순서 지정 여부가 중요한지 고려해야 합니다. 명확한 순서 지정이 필요하지 않고 대량의 형제 노드가 예상되는 경우에는 `sling:Folder` 또는 `oak:Unstructured`와 같은 비순차 노드 유형을 사용하는 것이 바람직합니다. 순서 지정이 필요한 경우에는 `nt:unstructured` 및 `sling:OrderedFolder`가 더 적합할 것입니다.

### 구성 요소에서의 쿼리 {#queries-in-components}

쿼리는 AEM 시스템에서 수행하는 비교적 더 까다로운 작업들 중 하나일 수 있기 때문에 구성 요소에서는 이를 피하는 것이 좋습니다. 페이지가 렌더링될 때마다 여러 쿼리가 실행되도록 할 경우 종종 시스템 성능이 저하될 수 있습니다. 구성 요소 렌더링 시 쿼리 실행을 피하는 데 이용할 수 있는 전략은 두 가지로, **[노드 트래버스](#traversing-nodes)** 전략과 **[결과 프리페치](#prefetching-results)** 전략입니다.

### 노드 트래버스 {#traversing-nodes}

필요한 데이터의 위치에 대한 사전 지식이 가능한 방식으로 저장소를 디자인한 경우 쿼리를 실행하여 찾을 필요 없이 필요한 경로에서 이 데이터를 검색하는 코드를 배포할 수 있습니다.

예를 들어 특정 카테고리에 부합하는 콘텐츠를 렌더링하는 경우가 있습니다. 한 가지 접근법은 카테고리에서 항목을 표시하는 구성 요소를 채우도록 쿼리할 수 있는 카테고리 속성을 가진 콘텐츠를 구성하는 것입니다.

그보다 나은 접근법은 이 콘텐츠를 카테고리별 분류법에 따라 구성하여 수동으로 가져올 수 있도록 하는 것입니다.

예를 들어 콘텐츠가 다음과 유사한 분류법으로 저장된다고 가정해봅시다.

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

`/content/myUnstructuredContent/parentCategory/childCategory` 노드를 간편하게 가져올 수 있으며, 그 자식 항목들은 구문 분석되어 구성 요소 렌더링에 사용될 수 있습니다.

또한 작은 크기 또는 같은 형식의 결과 세트를 다룰 때, 동일 결과 세트를 반환하는 쿼리를 만드는 것보다 저장소를 트래버스하고 필요 노드를 모으는 것이 더 빠를 수 있습니다. 일반적인 고려사항은 가능하면 쿼리를 피하는 것입니다.

### 결과 프리페치 {#prefetching-results}

가끔 콘텐츠나 구성 요소에 관한 요구 사항 때문에, 필요 데이터를 가져오는 방법으로 노드 트래버스를 사용할 수 없는 경우가 있습니다. 이 경우, 구성 요소가 렌더링되기 전에 필요 쿼리를 실행해야 최적의 성능을 보장할 수 있습니다.

구성 요소에 필요한 결과를 구성 요소 제작 당시에 계산할 수 없고 콘텐츠가 변경될 것으로 예상되지 않는 상황에서는 변경이 이루어진 후에 쿼리를 실행할 수 있습니다.

데이터나 콘텐츠가 규칙적으로 변경되는 경우에는 일정에 따라 쿼리를 실행하거나 기반 데이터의 업데이트에 대한 리스너를 사용하여 쿼리를 실행할 수 있습니다. 그러면 저장소의 공유 위치에 결과를 작성할 수 있습니다. 이 경우, 런타임 시 쿼리를 실행할 필요 없이 이 데이터를 필요로 하는 모든 구성 요소가 이 단일 노드에서 해당 값을 가져올 수 있습니다.

시작 시에 채워지고 변경사항이 적용될 때마다 업데이트되는 인메모리 캐시 결과를 보관할 때도 이와 유사한 전략을 사용할 수 있습니다(JCR `ObservationListener` 또는 Sling `ResourceChangeListener` 사용).

## 쿼리 최적화 {#optimizing-queries}

Oak 문서는 [쿼리 실행 방식에 대한 높은 수준의 개요를 제공합니다.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) 이는 본 문서에서 설명하는 모든 최적화 활동의 기반을 구성합니다.

AEM에서 제공하는 as a Cloud Service [쿼리 성능 도구](#query-performance-tool): 효율적인 쿼리 구현을 지원하도록 설계되었습니다.

* 이 도구는 이미 실행된 쿼리를 그 관련 성능 특성 및 쿼리 계획과 함께 표시합니다.
* 이 도구를 사용하면 단순히 쿼리 플랜을 표시하는 것부터 전체 쿼리를 실행하는 것까지 다양한 수준에서 애드혹 쿼리를 수행할 수 있습니다.

쿼리 성능 도구는 [Cloud Manager의 개발자 콘솔을 통해 접근 가능합니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#queries) AEM as a Cloud Service의 쿼리 성능 도구는 AEM 6.x 이상 버전에서의 쿼리 실행에 관한 세부 정보를 제공합니다.

이 차트는 쿼리 최적화를 위해 쿼리 성능 도구를 사용하는 일반적인 흐름을 설명합니다.

![쿼리 최적화 흐름](assets/query-optimization-flow.png)

### 색인 사용 {#use-an-index}

모든 쿼리는 최적의 성능을 제공하기 위해 색인을 사용해야 합니다. 대다수의 경우 기존의 기본 제공 색인으로 충분히 쿼리를 처리할 수 있습니다.

가끔은 기존 색인에 사용자 정의 속성을 추가하여, 색인을 사용해 추가적인 제한을 쿼리할 수 있습니다. 자세한 내용은 [콘텐츠 검색 및 색인화](/help/operations/indexing.md#changing-an-index) 문서를 참조하십시오. 다음 [JCR 쿼리 치트시트](#jcr-query-cheatsheet) 이 문서의 섹션에서는 특정 쿼리 유형을 지원하기 위해 색인의 속성 정의를 찾는 방법에 대해 설명합니다.

### 올바른 기준 사용 {#use-the-right-criteria}

모든 쿼리에 대한 주 제한은 속성 일치여야 합니다. 이것이 가장 효율적인 유형이기 때문입니다. 부가적인 속성 제한을 추가하면 결과가 더욱 제한됩니다.

쿼리 엔진은 단일 색인만 고려합니다. 즉, 더 많은 사용자 정의 색인 속성을 추가하여 기존 색인을 사용자 정의하는 것이 가능하고 필요하다는 의미입니다.

본 문서의 [JCR 쿼리 치트시트](#jcr-query-cheatsheet) 섹션은 이용 가능한 제한의 목록을 나열하며 또한 색인 정의가 선택되려면 어떤 형태여야 하는지 설명합니다. [쿼리 성능 도구](#query-performance-tool)를 사용하여 쿼리를 테스트할 수 있으며 올바른 색인이 사용되었는지 및 쿼리 엔진이 색인 외의 제한을 평가할 필요는 없는지 확인할 수 있습니다.

### 순서 지정 {#ordering}

결과의 특정한 순서가 필요하다면 쿼리 엔진에서 두 가지 방법으로 이를 구성할 수 있습니다.

1. 색인이 결과를 완전하게 올바른 순서에 따라 제공할 수 있습니다.
   * 이는 색인 정의에서 순서 지정에 사용되는 속성에 `ordered=true` 주석이 추가될 경우 가능합니다.
1. 쿼리 엔진이 순서 지정 프로세스를 수행합니다.
   * 이는 쿼리 엔진이 색인 외에서 필터링을 수행하거나 순서 지정 속성에 `ordered=true` 속성 주석이 추가되어 있지 않은 경우 발생할 수 있습니다.
   * 이 경우, 정렬을 위해 메모리에서 완전한 결과 세트를 읽어야 하며 이는 첫 번째 방법보다 훨씬 속도가 더딥니다.

### 결과 크기 제한 {#restrict-result-size}

쿼리 결과를 가져온 크기는 쿼리 수행에 있어 중요한 요인입니다. 결과는 소극적 방식으로 가져오게 되기 때문에, 단순히 첫 20개 결과를 가져오는 것과 10,000개 결과를 가져오는 것은 런타임과 메모리 사용량 모두의 측면에서 차이가 있습니다.

이는 또한 모든 결과를 가져오는 경우에만 결과 세트의 크기를 정확하게 측정할 수 있다는 의미입니다. 이러한 이유로 인해, 쿼리를 보강(자세한 내용은 본 문서의 [JCR 쿼리 치트시트](#jcr-query-cheatsheet) 섹션 참조)하거나 결과 읽기를 제한하여, 가져온 결과 세트는 항상 제한해야 합니다.

이러한 제한은 쿼리 엔진이 100,000노드의 **트래버스 제한**&#x200B;에 도달하는 것 또한 예방합니다. 이 제한에 도달하면 쿼리가 강제 정지됩니다.

섹션 보기 [결과 세트 크기가 큰 쿼리](#queries-with-large-result-sets) 이 문서의 경우 잠재적으로 크기가 큰 결과 세트를 완전히 처리해야 합니다.

## 쿼리 성능 도구 {#query-performance-tool}

쿼리 성능 도구(위치: `/libs/granite/operations/content/diagnosistools/queryPerformance.html` 및 를 통해 사용 가능 [Cloud Manager의 개발자 콘솔](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#queries)) - 를 제공합니다.
* 현재 5000개 이상의 행을 읽기/스캔하는 쿼리로 정의된 &#39;느린 쿼리&#39; 목록입니다.
* &#39;자주 사용하는 쿼리&#39; 목록
* Oak에서 특정 쿼리를 실행하는 방법을 이해하기 위한 &#39;쿼리 설명&#39; 도구입니다.

![쿼리 성능 도구](assets/query-performance-tool.png)

&quot;느린 쿼리&quot; 및 &quot;자주 찾는 쿼리&quot; 테이블에는 다음이 포함됩니다.
* 쿼리 문 자체입니다.
* 쿼리를 실행하는 페이지 또는 애플리케이션 기능을 식별할 수 있도록 쿼리를 실행한 마지막 스레드의 세부 정보입니다.
* 쿼리에 대한 &#39;읽기 최적화&#39; 점수.
   * 이는 쿼리를 실행하기 위해 스캔한 행/노드 수와 일치하는 결과 읽기 수 간의 비율로 계산됩니다.
   * 인덱스에서 모든 제한(및 순서 지정)을 처리할 수 있는 쿼리는 일반적으로 90% 이상을 받습니다.
* 최대 행 수 세부 정보 -
   * 읽기 - 행이 결과 세트의 일부로 포함되었음을 나타냅니다.
   * 스캔됨 - 행이 기본 색인 쿼리의 결과(색인화된 쿼리의 경우)에 포함되었거나 노드 저장소(저장소 순회의 경우)에서 읽혔음을 나타냅니다.

이러한 테이블은 완전히 색인화되지 않은 쿼리를 식별하는 데 도움이 됩니다(참조) [색인 사용](#use-an-index) 또는 가 너무 많은 노드를 읽고 있습니다(또한 참조). [저장소 트래버스](#repository-traversal) 및 [색인 순회](#index-traversal)). 이러한 쿼리는 빨간색으로 표시된 적절한 관심 영역을 사용하여 강조 표시됩니다.

다음 `Reset Statistics` 테이블에서 수집된 모든 기존 통계를 제거하는 옵션이 제공됩니다. 이렇게 하면 애플리케이션 자체 또는 쿼리 설명 도구를 통해 특정 쿼리를 실행하고 실행 통계를 분석할 수 있습니다.

### 쿼리 설명

개발자는 쿼리 설명 도구를 사용하여 쿼리 실행 계획을 이해할 수 있습니다(참조) [쿼리 실행 계획 읽기](#reading-query-execution-plan))을 사용하여 쿼리를 실행할 때 사용된 인덱스의 세부 정보를 제공합니다. 쿼리를 색인화하여 성능을 예측하거나 소급하여 분석하는 방법을 이해하는 데 사용할 수 있습니다.

#### 쿼리 설명

쿼리를 설명하려면 다음 작업을 수행하십시오.

* 다음을 사용하여 적절한 쿼리 언어 선택 `Language` 드롭다운입니다.
* 쿼리 문을 `Query` 필드.
* 필요한 경우 제공된 확인란을 사용하여 쿼리가 실행되는 방법을 선택합니다.
   * 기본적으로 JCR 쿼리는 쿼리 실행 계획을 식별하기 위해 실행할 필요가 없습니다(QueryBuilder 쿼리의 경우 아님).
   * 쿼리 실행을 위한 세 가지 옵션이 제공됩니다.
      * `Include Execution Time` - 쿼리를 실행하지만 결과를 읽지 않습니다.
      * `Read first page of results` - 쿼리를 실행하고 20개의 결과 중 첫 번째 &#39;페이지&#39;를 읽습니다(쿼리 실행에 대한 모범 사례를 복제합니다).
      * `Include Node Count` - 쿼리를 실행하고 전체 결과 세트를 읽습니다(일반적으로 권장되지 않음 - 참조 [색인 순회](#index-traversal)).

#### 쿼리 설명 팝업 {#query-explanation-popup}

![쿼리 설명 팝업](./assets/query-explanation-popup.png)

선택 후 `Explain`를 선택하면 쿼리 설명(및 선택한 경우 실행) 결과를 설명하는 팝업이 사용자에게 표시됩니다.
이 팝업에는 -에 대한 세부 사항이 포함됩니다.
* 쿼리를 실행할 때 사용되는 인덱스(또는 쿼리를 실행할 경우 사용할 인덱스 없음) [저장소 트래버스](#repository-traversal)).
* 실행 시간 (if `Include Execution Time` 확인란이 선택됨) 및 읽은 결과 수(다음 경우) `Read first page of results` 또는 `Include Node Count` 확인란이 선택되었습니다.)
* 실행 계획, 쿼리 실행 방식에 대한 자세한 분석 허용 - 다음을 참조하십시오. [쿼리 실행 계획 읽기](#reading-query-execution-plan) 를 참조하십시오.
* 처음 20개 쿼리 결과의 경로(다음의 경우) `Read first page of results` 확인란이 선택됨)
* 이 쿼리를 실행하기 위해 고려된 인덱스의 상대적 비용을 보여주는 쿼리 계획의 전체 로그(비용이 가장 낮은 인덱스가 선택됨).

#### 쿼리 실행 계획 읽기 {#reading-query-execution-plan}

쿼리 실행 계획에는 특정 쿼리의 성능을 예측(또는 설명)하는 데 필요한 모든 것이 포함되어 있습니다. 원래 JCR(또는 Query Builder) 쿼리의 제한 사항 및 순서를 기본 색인(Lucene, Elastic 또는 Property)에서 실행된 쿼리와 비교하여 쿼리가 얼마나 효율적으로 실행되는지 이해합니다.

다음 쿼리를 고려하십시오.

```
/jcr:root/content/dam//element(*, dam:Asset) [jcr:content/metadata/dc:title = "My Title"] order by jcr:created
```

...다음 포함: -
* 3개 제한 사항
   * 노드 유형 (`dam:Asset`)
   * 경로(하위 항목) `/content/dam`)
   * 속성 (`jcr:content/metadata/dc:title = "My Title"`)
* 정렬 기준: `jcr:created` 속성

이 쿼리를 설명하면 다음 플랜이 생성됩니다.

```
[dam:Asset] as [a] /* lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) +:ancestors:/content/dam +jcr:content/metadata/dc:title:My Title ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }] where ([a].[jcr:content/metadata/dc:title] = 'My Title') and (isdescendantnode([a], [/content/dam])) */
```

이 플랜 내에서 기본 색인에서 실행되는 쿼리를 설명하는 섹션은 -

```
lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) +:ancestors:/content/dam +jcr:content/metadata/dc:title:My Title ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]
```

플랜의 이 섹션에서는 다음을 명시합니다. -
* 색인은 이 쿼리를 실행하는 데 사용됩니다.
   * 이 경우 Lucene 색인 `/oak:index/damAssetLucene-9` 가 사용되므로 나머지 정보는 Lucene 쿼리 구문에 있습니다.
* 3가지 제한 사항은 모두 색인에 의해 처리됩니다.
   * 노드 유형 제한
      * 암시적, 이유 `damAssetLucene-9` dam:Asset 유형의 노드만 인덱싱합니다.
   * 경로 제한
      * 이유 `+:ancestors:/content/dam` 이 Lucene 쿼리에 나타납니다.
   * 속성 제한
      * 이유 `+jcr:content/metadata/dc:title:My Title` 이 Lucene 쿼리에 나타납니다.
* 순서는 색인에 의해 처리됩니다.
   * 이유 `ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]`  이 Lucene 쿼리에 나타납니다.

색인 쿼리에서 반환된 결과는 액세스 제어 필터링 외에 쿼리 엔진에서 더 이상 필터링되지 않으므로 이러한 쿼리는 잘 수행될 수 있습니다. 그러나 모범 사례를 따르지 않는 경우 이러한 쿼리가 천천히 실행될 수 있습니다. 다음을 참조하십시오. [색인 순회](#index-traversal) 아래요.

다른 쿼리 고려 -

```
/jcr:root/content/dam//element(*, dam:Asset) [jcr:content/metadata/myProperty = "My Property Value"] order by jcr:created
```

...다음 포함: -
* 3개 제한 사항
   * 노드 유형 (`dam:Asset`)
   * 경로(하위 항목) `/content/dam`)
   * 속성 (`jcr:content/metadata/myProperty = "My Property Value"`)
* 정렬 기준: `jcr:created` 속성**

이 쿼리를 설명하면 다음 플랜이 생성됩니다.

```
[dam:Asset] as [a] /* lucene:damAssetLucene-9-custom-1(/oak:index/damAssetLucene-9-custom-1) :ancestors:/content/dam ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }] where ([a].[jcr:content/metadata/myProperty] = 'My Property Value') and (isdescendantnode([a], [/content/dam])) */
```

이 플랜 내에서 기본 색인에서 실행되는 쿼리를 설명하는 섹션은 -

```
lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) :ancestors:/content/dam ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]
```

플랜의 이 섹션에서는 다음을 명시합니다. -
* 3개 중 2개의 제한만 색인에 의해 처리됩니다.
   * 노드 유형 제한
      * 암시적, 이유 `damAssetLucene-9` dam:Asset 유형의 노드만 인덱싱합니다.
   * 경로 제한
      * 이유 `+:ancestors:/content/dam` 이 Lucene 쿼리에 나타납니다.
* 속성 제한 `jcr:content/metadata/myProperty = "My Property Value"` 는 색인에서 실행되지 않고 기본 Lucene 쿼리의 결과에 대한 쿼리 엔진 필터링으로 적용됩니다.
   * 이유는 다음과 같습니다. `+jcr:content/metadata/myProperty:My Property Value` 이 속성은에서 색인화되지 않으므로 Lucene 쿼리에 표시되지 않습니다. `damAssetLucene-9` 이 쿼리에 사용되는 색인입니다.

이 쿼리 실행 계획을 수행하면 모든 에셋이 아래에 표시됩니다. `/content/dam` 인덱스에서 읽은 다음 쿼리 엔진에 의해 추가로 필터링됩니다(결과 세트에 인덱싱되지 않은 속성 제한과 일치하는 속성만 포함).

일부 자산만 제한 사항과 일치하는 경우에도 `jcr:content/metadata/myProperty = "My Property Value"`, 쿼리는 요청된 &#39;페이지&#39;의 결과를 채우기 위해(시도) 많은 노드를 읽어야 합니다. 이로 인해 쿼리의 성능이 저하될 수 있으며, 이 낮은 쿼리로 표시됩니다 `Read Optimization` 는 쿼리 성능 도구에서 점수를 매기고 많은 수의 노드가 트래버스됨을 나타내는 경고 메시지가 표시될 수 있습니다(참조) [색인 순회](#index-traversal)).

이 두 번째 쿼리의 성능을 최적화하려면 `damAssetLucene-9` 색인(`damAssetLucene-9-custom-1`) 다음 속성 정의를 추가합니다.

```
"myProperty": {
  "jcr:primaryType": "nt:unstructured",
  "propertyIndex": true,
  "name": "jcr:content/metadata/myProperty"
}
```

## JCR 쿼리 치트 시트 {#jcr-query-cheatsheet}

효율적인 JCR 쿼리 및 색인 정의를 생성하는 데 도움을 얻고 싶다면 [JCR 쿼리 치트시트](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html#jcrquerycheatsheet)를 다운로드하여 개발 중 참조할 수 있습니다.

여기에는 쿼리 성능이 다양한 여러 시나리오를 포괄하는 QueryBuilder, XPath, SQL-2에 대한 샘플 쿼리가 포함되어 있습니다. 이 치트시트는 또한 Oak 색인을 구축하거나 사용자 정의하는 방법에 대한 권장 사항도 제공합니다. 이 치트 시트의 콘텐츠는 AEM as a Cloud Service 및 AEM 6.5에 적용됩니다.

## 색인 정의 우수 사례 {#index-definition-best-practices}

다음은 인덱스를 정의하거나 확장할 때 고려해야 할 몇 가지 모범 사례입니다.

* 기존 색인이 있는 노드 유형의 경우(예: `dam:Asset` 또는 `cq:Page`) 새 색인의 추가보다 OOTB 색인 확장을 선호합니다.
   * 에서 새 색인(특히 전체 텍스트 색인) 추가 `dam:Asset` 노드 유형은 매우 권장되지 않습니다(참조). [이 메모](/help/operations/indexing.md##index-names-index-names)).
* 새 인덱스를 추가할 때
   * 항상 &#39;lucene&#39; 유형의 인덱스를 정의하십시오.
   * 색인 정의(및 관련 쿼리)에서 색인 태그 사용 `selectionPolicy = tag` 색인이 의도한 쿼리에만 사용되도록 하기 위해
   * 확인 `queryPaths` 및 `includedPaths` 둘 다 제공됩니다(일반적으로 동일한 값 포함).
   * 사용 `excludedPaths` 유용한 결과를 포함하지 않을 경로를 제외합니다.
   * 사용 `analyzed` 필요한 경우에만 속성(예: 해당 속성에만 대해 전체 텍스트 쿼리 제한을 사용해야 하는 경우)
   * 항상 지정 `async = [ async, nrt ] `, `compatVersion = 2` 및 `evaluatePathRestrictions = true`.
   * 다음만 지정 `nodeScopeIndex = true` nodescope 전체 텍스트 인덱스가 필요한 경우.

>[!NOTE]
>
>자세한 내용은 [Oak Lucene 색인 설명서](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

Automated Cloud Manager 파이프라인 확인은 위에서 설명한 몇 가지 모범 사례를 적용합니다.

## 결과 세트 크기가 큰 쿼리 {#queries-with-large-result-sets}

결과 세트 크기가 큰 쿼리는 피하는 것이 바람직하지만 이러한 결과 세트를 꼭 처리해야 하는 경우도 존재합니다. 결과의 크기를 정확하게 알 수 없는 경우가 많기 때문에 신뢰성 있는 처리를 위해서는 몇 가지 예방 조치를 실시해야 합니다.

* 쿼리는 요청 내에서 실행해서는 안 됩니다. 대신, Sling Job이나 AEM 워크플로의 일부로서 쿼리를 실행해야 합니다. 이 두 방법은 총 런타임에 제한이 전혀 없으며, 쿼리와 그 결과를 처리하는 동안 인스턴스가 정지되면 재시작됩니다.
* 100,000노드의 쿼리 제한을 극복하려면 [키세트 페이지 매김](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination)의 사용을 고려해야 하며 쿼리를 다양한 하위 쿼리로 분할해야 합니다.

## 저장소 트래버스 {#repository-traversal}

저장소를 트래버스하는 쿼리는 색인을 사용하지 않으며 다음과 유사한 메시지를 사용해 기록합니다.

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

이러한 로그 스니펫을 통해 다음을 파악할 수 있습니다.

* 쿼리 자체: `//*`
* 이 쿼리를 실행한 Java 코드: 쿼리 생성자를 식별하도록 도와주는 `com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics`.

이 정보가 있으면 본 문서의 [쿼리 최적화](#optimizing-queries) 섹션에 설명된 방법으로 이 쿼리를 최적화할 수 있습니다.

### 색인 순회 {#index-traversal}

인덱스를 사용하지만 여전히 많은 노드를 읽는 쿼리는 다음과 유사한 메시지와 함께 기록됩니다(용어 설명) `Index-Traversed` 보다 `Traversed`).

```text
05.10.2023 10:56:10.498 *WARN* [127.0.0.1 [1696502982443] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.search.spi.query.FulltextIndex$FulltextPathCursor Index-Traversed 60000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [dam:Asset] as a where isdescendantnode(a, '/content/dam') order by [jcr:content/metadata/unindexedProperty] /* xpath: /jcr:root/content/dam//element(*, dam:Asset) order by jcr:content/metadata/unindexedProperty */, path=/content/dam//*)
```

이 문제는 다음과 같은 여러 가지 이유로 발생할 수 있습니다.
1. 쿼리의 모든 제한을 색인에서 처리할 수 있는 것은 아닙니다.
   * 이 경우, 최종 결과 세트의 상위 집합은 색인에서 읽히고 이어서 쿼리 엔진에서 필터링됩니다.
   * 이는 기본 색인 쿼리에 제한을 적용하는 것보다 몇 배 더 느립니다.
1. 쿼리는 인덱스에서 &#39;ordered&#39;로 표시되지 않은 속성별로 정렬됩니다.
   * 이 경우 인덱스에서 반환된 모든 결과는 쿼리 엔진에서 읽고 메모리 내에서 정렬해야 합니다.
   * 이는 기본 색인 쿼리에서 정렬을 적용하는 것보다 몇 배 더 느립니다.
1. 쿼리 실행자가 큰 결과 집합을 반복하려고 합니다.
   * 이 상황은 아래와 같이 여러 가지 이유로 발생할 수 있습니다.

| 원인 | 완화 |
|----------|--------------|
| 의 생략 `p.guessTotal` (또는 매우 큰 guessTotal의 사용) QueryBuilder가 결과 계산 결과를 대량으로 반복하도록 합니다 | 제공 `p.guessTotal` 적절한 값 포함 |
| Query Builder에서 크거나 제한되지 않은 제한 사용(예: `p.limit=-1`) | 다음에 대한 적절한 값 사용 `p.limit` (이상적으로 1000 이하) |
| 기본 JCR 쿼리에서 많은 결과를 필터링하는 Query Builder의 필터링 술어 사용 | 필터링 술어를 기본 JCR 쿼리에 적용할 수 있는 제한으로 바꿉니다. |
| QueryBuilder에서 Comparator 기반 정렬 사용 | 기본 JCR 쿼리의 속성 기반 순서 지정(순서가 지정된 것으로 인덱싱된 속성 사용)으로 대체합니다. |
| 액세스 제어로 인한 많은 결과 필터링 | 추가 인덱싱된 속성 또는 경로 제한을 쿼리에 적용하여 액세스 제어를 미러링합니다 |
| 오프셋이 큰 &#39;오프셋 페이지 매김&#39; 사용 | 사용 고려 [키 집합 페이지 매김](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) |
| 많은 또는 제한되지 않은 결과 수의 반복 | 사용 고려 [키 집합 페이지 매김](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) |
| 잘못된 색인 선택됨 | 쿼리 및 색인 정의에 태그를 사용하여 예상된 색인이 사용되도록 하십시오 |
