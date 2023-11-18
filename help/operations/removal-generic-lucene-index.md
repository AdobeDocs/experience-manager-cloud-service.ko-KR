---
title: 일반 Lucene 인덱스 제거
description: 일반 Lucene 색인의 제거 계획과 영향을 받는 방법에 대해 알아봅니다.
exl-id: 3b966d4f-6897-406d-ad6e-cd5cda020076
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 0%

---

# 일반 Lucene 인덱스 제거 {#generic-lucene-index-removal}

Adobe이 &quot;일반 Lucene&quot; 인덱스(`/oak:index/lucene-*`)을 Adobe Experience Manager as a Cloud Service에서 가져왔습니다. 이 색인은 AEM 6.5 이후 더 이상 사용되지 않습니다. 이 문서에서는 AEM 인스턴스가 영향을 받는지 여부를 검사하는 방법에 대한 자세한 설명과 함께 이 결정의 영향에 대해 설명합니다. 또한 일반 Lucene 인덱스 없이 계속 작동하도록 쿼리를 변경하는 방법이 포함되어 있습니다.

## 배경 {#background}

AEM에서 전체 텍스트 쿼리는 다음 함수를 사용하는 쿼리입니다.

* `jcr:contains()` JCR XPATH에서
* `CONTAINS` JCR-SQL2에서

이러한 쿼리는 색인을 사용하지 않으면 결과를 반환할 수 없습니다. 경로 또는 속성 제한만 포함하는 쿼리와 달리, 인덱스를 찾을 수 없는 전체 텍스트 제한(따라서 순회가 수행됨)이 포함된 쿼리는 항상 0개의 결과를 반환합니다.

일반 Lucene 인덱스(`/oak:index/lucene-*`)는 AEM 6.0 / Oak 1.0 이후 존재하여 다음과 같은 일부 경로가 있지만 대부분의 저장소 계층 구조에서 전체 텍스트 검색을 제공합니다. `/jcr:system` 및 `/var` 이 항목에서 항상 제외되었습니다. 그러나 이 색인은 주로 더 구체적인 노드 유형에 대한 색인으로 대체되었습니다(예: `damAssetLucene-*` 대상: `dam:Asset` 전체 텍스트와 속성 검색을 모두 지원하는 노드 유형)

AEM 6.5에서 일반 Lucene 색인은 더 이상 사용되지 않는 것으로 표시되어 이후 버전에서 제거됨을 나타냅니다. 이후 다음 로그 스니펫에서 설명한 대로 색인이 사용되면 WARN이 기록됩니다.

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Change the query or the index definitions.
```

최근 AEM 버전에서는 매우 적은 수의 기능을 지원하는 데 일반 Lucene 색인이 사용되었습니다. 다른 색인을 사용하도록 다시 작업하거나 이 색인에 대한 종속성을 제거하기 위해 수정합니다.

예를 들어 다음 예제와 같은 참조 조회 쿼리는 이제 의 인덱스를 사용해야 합니다. `/oak:index/pathreference`, 색인만 `String` jcr 경로를 찾는 정규 표현식과 일치하는 속성 값입니다.

```text
//*[jcr:contains(., '"/content/dam/mysite"')]
```

대규모 고객 데이터 볼륨을 지원하기 위해 Adobe은 더 이상 새로운 AEM as a Cloud Service 환경에서 일반 Lucene 인덱스를 만들지 않습니다. 또한 Adobe은 기존 저장소에서 인덱스를 제거합니다. [타임라인 보기](#timeline) 자세한 내용은 이 문서 끝에 있습니다.

Adobe은 이미 다음을 통해 색인 비용을 조정했습니다. `costPerEntry` 및 `costPerExecution` 속성을 사용하여 다음과 같은 다른 색인을 확인합니다. `/oak:index/pathreference` 는 가능한 한 우선적으로 사용됩니다.

여전히 이 색인에 의존하는 쿼리를 사용하는 고객 애플리케이션은 다른 기존 색인을 사용하도록 즉시 업데이트해야 하며, 필요한 경우 이를 사용자 정의할 수 있습니다. 또는 고객 애플리케이션에 새로운 사용자 정의 인덱스를 추가할 수 있습니다. AEM as a Cloud Service의 색인 관리에 대한 전체 지침은 [색인 지정 문서](/help/operations/indexing.md).

## 영향을 받습니까? {#are-you-affected}

다른 전체 텍스트 인덱스로 쿼리를 처리할 수 없는 경우 일반 Lucene 인덱스가 현재 대체 항목으로 사용됩니다. 더 이상 사용되지 않는 이 색인을 사용하면 다음과 유사한 메시지가 WARN 수준에서 기록됩니다.

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Change the query or the index definitions.
```

경우에 따라 Oak가 다른 전체 텍스트 인덱스(예: `/oak:index/pathreference`) 전체 텍스트 쿼리를 지원하지만 쿼리 문자열이 인덱스 정의의 정규 표현식과 일치하지 않으면 메시지가 WARN 수준에서 기록되며 쿼리가 결과를 반환하지 않을 수 있습니다.

```text
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

일반 Lucene 색인이 제거되면, 전체 텍스트 쿼리에서 적절한 색인 정의를 찾을 수 없는 경우 아래에 표시된 것처럼 메시지가 경고 수준으로 기록됩니다.

```text
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results are returned
```

>[!IMPORTANT]
>
>**고객 조치 필요**
>
> 앞서 언급한 경고 메시지가 기록되는 경우 쿼리를 다시 작업하여 다른 전체 텍스트 인덱스를 사용하거나 새 인덱스를 제공하여 쿼리를 지원해야 할 수 있습니다.
>
>표시되는 종속성 유형과 이를 해결하는 방법에 대한 자세한 내용은 다음 섹션에 나와 있습니다.

## 일반 Lucene 인덱스에 대한 잠재적 종속성 {#potential-dependencies}

애플리케이션 및 AEM 설치가 작성자 및 게시 인스턴스 모두에서 일반 Lucene 인덱스에 종속될 수 있는 몇 가지 영역이 있습니다.

### 게시 인스턴스 {#publish-instance}

#### 사용자 정의 응용 프로그램 쿼리 {#custom-application-queries}

게시 인스턴스에서 일반 Lucene 인덱스를 사용하는 가장 일반적인 쿼리 소스는 사용자 지정 애플리케이션 쿼리입니다.

가장 간단한 경우는 노드 유형이 지정되지 않았으므로 이를 암시하는 쿼리일 수 있습니다 `nt:base` 또는 `nt:base` 명시적으로 지정된 항목:

```text
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

>[!IMPORTANT]
>
>**고객 조치 필요**
>
>앞서 언급한 쿼리는 다음 섹션에 설명된 대로 적절한 노드 유형을 사용하도록 수정해야 합니다.

예를 들어 페이지 또는 그 아래의 합계 와 일치하는 결과를 반환하도록 쿼리를 수정할 수 있습니다. `cq:Page node`. 따라서 쿼리는 다음과 같이 될 수 있습니다.

```text
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

다른 경우, 쿼리는 노드 유형을 지정할 수 있지만 다음과 같은 다른 전체 텍스트 인덱스로 처리할 수 없는 전체 텍스트 제한을 포함할 수 있습니다.

```text
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

이 경우 쿼리에 `dam:Asset` 노드 유형이지만 상대에 대한 전체 텍스트 제한이 포함되어 있음 `jcr:content/metadata/@cq:tags` 속성.

이 속성은 다음에서 분석된 것으로 표시되지 않습니다. `damAssetLucene` index: 쿼리에 가장 일반적으로 사용되는 전체 텍스트 색인입니다. `dam:Asset` 노드 유형. 따라서 이 색인은 이 쿼리에 사용할 수 없습니다.

이에 따라 쿼리는 포함된 모든 속성이 와일드카드 일치에 의해 분석된 것으로 표시되는 일반 전체 텍스트 인덱스로 대체됩니다. `/oak:index/lucene-2/indexRules/nt:base/properties/prop`.

>[!IMPORTANT]
>
>**고객 조치 필요**
>
>다음을 표시 `jcr:content/metadata/@cq:tags` 의 사용자 지정 버전에서 분석된 속성 `damAssetLucene` 인덱스로 인해 이 쿼리가 이 인덱스로 처리되며 WARN이 기록되지 않습니다.

### 작성자 인스턴스 {#author-instance}

고객 애플리케이션 서블릿, OSGi 구성 요소 및 렌더링 스크립트의 쿼리 외에도 몇 가지 작성자별 일반 Lucene 인덱스 사용이 있을 수 있습니다.

#### 참조 검색 {#reference-search}

지금까지 일반 Lucene 색인은 참조 검색을 지원하거나 다른 콘텐츠 경로에 대한 참조가 포함된 콘텐츠를 검색하는 데 사용되었습니다. 이러한 쿼리는 새 쿼리를 사용하도록 이미 업데이트되었을 것입니다. `/oak:index/pathreference` 색인입니다.

#### 경로 필드 선택기 검색 {#picker-search}

AEM에는 Sling 리소스 유형으로 사용자 지정 대화 상자 구성 요소가 포함되어 있습니다 `granite/ui/components/coral/foundation/form/pathfield`: 다른 AEM 경로를 선택할 수 있는 브라우저/선택기를 제공합니다. 사용자 지정 항목이 없을 때 사용되는 기본 경로 필드 선택기 `pickerSrc` 속성은 콘텐츠 구조에 정의되어 있으며 팝업 대화 상자에서 검색 막대를 렌더링합니다.

검색할 노드 유형은 다음을 사용하여 지정할 수 있습니다. `nodeTypes` 속성.

현재, 없는 경우 `nodeTypes` 속성이 있으면 기본 검색 쿼리에서 `nt:base` node 형식이므로 일반적으로 다음과 유사한 WARN 메시지를 로깅하는 일반 Lucene 인덱스를 사용할 수 있습니다.

```text
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Change the query or the index definitions.
```

일반 Lucene 인덱스를 제거하기 전에 `pathfield` 기본 선택기를 사용하여 구성 요소에 대해 검색 상자를 숨기고 을 제공하지 않도록 구성 요소가 업데이트됩니다. `nodeTypes` 속성.

| 검색이 있는 경로 필드 선택기 | 검색이 없는 경로 필드 선택기 |
|---|---|
| ![검색이 있는 경로 필드 선택기](assets/index-pathfield-picker-with-search.png) | ![검색이 없는 경로 필드 선택기](assets/index-pathfield-picker-without-search.png) |

>[!IMPORTANT]
>
>**고객 조치 필요**
>
>고객이 경로 필드 선택기 내에서 검색 기능을 유지하려는 경우 `nodeTypes` 쿼리할 노드 유형을 나열하는 속성을 제공해야 합니다. 에서 쉼표로 구분된 노드 유형 목록으로 지정할 수 있습니다. `String` 속성. 검색이 필요하지 않은 경우 고객의 조치가 필요하지 않습니다.

>[!NOTE]
>
>콘텐츠 조각 모델 편집기는 Sling 리소스 유형의 특수 경로 필드를 사용합니다 `dam/cfm/models/editor/components/contentreference`.
> * 현재는 이러한 작업에서 노드 유형을 지정하지 않고 쿼리를 수행하므로 일반 Lucene 인덱스 사용으로 인해 WARN이 기록됩니다.
> * 이러한 구성 요소의 인스턴스는 곧 자동으로 사용을 기본값으로 설정합니다. `cq:Page` 및 `dam:Asset` 추가적인 고객 조치 없이 노드 유형.
> * 다음 `nodeTypes` 속성을 추가하여 이러한 기본 노드 유형을 재정의할 수 있습니다.

## 일반 Lucene 제거 타임라인 {#timeline}

Adobe은 일반적인 Lucene 인덱스를 제거하는 2단계 접근 방식을 취합니다.

* **단계 1** (계획된 시작 날짜: 2022년 1월 31일): 더 이상 만들지 않습니다. `/oak:index/lucene-*` 새로운 AEM as a Cloud Service 환경에서.
* **단계 2** (2022년 3월 31일에 시작 예정): 제거 `/oak:index/lucene-*` 기존 AEM as a Cloud Service 환경의 색인입니다.

Adobe은 위에 언급된 로그 메시지를 모니터링하고 일반 Lucene 색인에 계속 의존하는 고객에게 문의하려고 시도합니다.

단기적인 완화 차원에서 Adobe은 고객 시스템에 사용자 정의 인덱스 정의를 직접 추가하여 필요에 따라 일반 Lucene 인덱스를 제거하여 발생하는 기능이나 성능 문제를 방지합니다.

이러한 경우 고객은 업데이트된 색인 정의를 제공받고 Cloud Manager를 통해 향후 애플리케이션 릴리스에 이를 포함하도록 권장됩니다.
