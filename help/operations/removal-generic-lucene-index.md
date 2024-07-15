---
title: 일반 Lucene 인덱스 제거
description: 일반 Lucene 색인의 제거 계획과 영향을 받는 방법에 대해 알아봅니다.
exl-id: 3b966d4f-6897-406d-ad6e-cd5cda020076
feature: Operations
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 0%

---

# 일반 Lucene 인덱스 제거 {#generic-lucene-index-removal}

Adobe이 Adobe Experience Manager as a Cloud Service에서 &quot;일반 Lucene&quot; 인덱스(`/oak:index/lucene-*`)를 제거하려고 합니다. 이 색인은 AEM 6.5 이후 더 이상 사용되지 않습니다. 이 문서에서는 AEM 인스턴스가 영향을 받는지 여부를 검사하는 방법에 대한 자세한 설명과 함께 이 결정의 영향에 대해 설명합니다. 또한 일반 Lucene 인덱스 없이 계속 작동하도록 쿼리를 변경하는 방법이 포함되어 있습니다.

## 배경 {#background}

AEM에서 전체 텍스트 쿼리는 다음 함수를 사용하는 쿼리입니다.

* JCR XPATH의 `jcr:contains()`
* JCR-SQL2의 `CONTAINS`

이러한 쿼리는 색인을 사용하지 않으면 결과를 반환할 수 없습니다. 경로 또는 속성 제한만 포함하는 쿼리와 달리, 인덱스를 찾을 수 없는 전체 텍스트 제한(따라서 순회가 수행됨)이 포함된 쿼리는 항상 0개의 결과를 반환합니다.

일반 Lucene 인덱스(`/oak:index/lucene-*`)는 AEM 6.0 / Oak 1.0 이후 존재하여 대부분의 저장소 계층 구조에서 전체 텍스트 검색을 제공했지만 `/jcr:system` 및 `/var`과(와) 같은 일부 경로는 항상 이 항목에서 제외되었습니다. 그러나 이 인덱스는 주로 전체 텍스트와 속성 검색을 모두 지원하는 특정 노드 형식(예: `dam:Asset` 노드 형식의 경우 `damAssetLucene-*`)에 대한 인덱스로 대체되었습니다.

AEM 6.5에서 일반 Lucene 색인은 더 이상 사용되지 않는 것으로 표시되어 이후 버전에서 제거됨을 나타냅니다. 이후 다음 로그 스니펫에서 설명한 대로 색인이 사용되면 WARN이 기록됩니다.

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Change the query or the index definitions.
```

최근 AEM 버전에서는 매우 적은 수의 기능을 지원하는 데 일반 Lucene 색인이 사용되었습니다. 다른 색인을 사용하도록 다시 작업하거나 이 색인에 대한 종속성을 제거하기 위해 수정합니다.

예를 들어 다음 예제와 같은 참조 조회 쿼리는 이제 JCR 경로를 찾는 정규 표현식과 일치하는 `String` 속성 값만 인덱싱하는 `/oak:index/pathreference`의 인덱스를 사용해야 합니다.

```text
//*[jcr:contains(., '"/content/dam/mysite"')]
```

대규모 고객 데이터 볼륨을 지원하기 위해 Adobe은 더 이상 새로운 AEM as a Cloud Service 환경에서 일반 Lucene 인덱스를 만들지 않습니다. 또한 Adobe은 기존 저장소에서 인덱스를 제거합니다. 자세한 내용은 이 문서 끝에 있는 [타임라인을 참조하십시오](#timeline).

Adobe은 `costPerEntry` 및 `costPerExecution` 속성을 통해 인덱스 비용을 이미 조정했습니다. `/oak:index/pathreference`과(와) 같은 다른 인덱스가 가능한 한 기본 설정에서 사용되도록 합니다.

여전히 이 색인에 의존하는 쿼리를 사용하는 고객 애플리케이션은 다른 기존 색인을 사용하도록 즉시 업데이트해야 하며, 필요한 경우 이를 사용자 정의할 수 있습니다. 또는 고객 애플리케이션에 새로운 사용자 정의 인덱스를 추가할 수 있습니다. AEM as a Cloud Service의 인덱스 관리에 대한 전체 지침은 [인덱싱 문서](/help/operations/indexing.md)에서 찾을 수 있습니다.

## 영향을 받습니까? {#are-you-affected}

다른 전체 텍스트 인덱스로 쿼리를 처리할 수 없는 경우 일반 Lucene 인덱스가 현재 대체 항목으로 사용됩니다. 더 이상 사용되지 않는 이 색인을 사용하면 다음과 유사한 메시지가 WARN 수준에서 기록됩니다.

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Change the query or the index definitions.
```

경우에 따라 Oak에서 다른 전체 텍스트 인덱스(예: `/oak:index/pathreference`)를 사용하여 전체 텍스트 쿼리를 지원하려고 시도할 수 있지만 쿼리 문자열이 인덱스 정의의 정규 표현식과 일치하지 않으면 메시지가 WARN 수준에서 기록되고 쿼리가 결과를 반환하지 않을 수 있습니다.

```text
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

일반 Lucene 색인이 제거되면, 전체 텍스트 쿼리에서 적절한 색인 정의를 찾을 수 없는 경우 아래에 표시된 것처럼 메시지가 경고 수준으로 기록됩니다.

```text
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results are returned
```

>[!IMPORTANT]
>
>**고객 작업 필요**
>
> 앞서 언급한 경고 메시지가 기록되는 경우 쿼리를 다시 작업하여 다른 전체 텍스트 인덱스를 사용하거나 새 인덱스를 제공하여 쿼리를 지원해야 할 수 있습니다.
>
>표시되는 종속성 유형과 이를 해결하는 방법에 대한 자세한 내용은 다음 섹션에 나와 있습니다.

## 일반 Lucene 인덱스에 대한 잠재적 종속성 {#potential-dependencies}

애플리케이션 및 AEM 설치가 작성자 및 게시 인스턴스 모두에서 일반 Lucene 인덱스에 종속될 수 있는 몇 가지 영역이 있습니다.

### 게시 인스턴스 {#publish-instance}

#### 사용자 정의 응용 프로그램 쿼리 {#custom-application-queries}

게시 인스턴스에서 일반 Lucene 인덱스를 사용하는 가장 일반적인 쿼리 소스는 사용자 지정 애플리케이션 쿼리입니다.

가장 간단한 경우는 다음과 같이 노드 유형이 지정되지 않아 명시적으로 지정된 `nt:base` 또는 `nt:base`을(를) 의미하는 쿼리일 수 있습니다.

```text
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

>[!IMPORTANT]
>
>**고객 작업 필요**
>
>앞서 언급한 쿼리는 다음 섹션에 설명된 대로 적절한 노드 유형을 사용하도록 수정해야 합니다.

예를 들어 쿼리는 `cq:Page node` 아래에 있는 집계 또는 페이지와 일치하는 결과를 반환하도록 수정할 수 있습니다. 따라서 쿼리는 다음과 같이 될 수 있습니다.

```text
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

다른 경우, 쿼리는 노드 유형을 지정할 수 있지만 다음과 같은 다른 전체 텍스트 인덱스로 처리할 수 없는 전체 텍스트 제한을 포함할 수 있습니다.

```text
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

이 경우 쿼리에 `dam:Asset` 노드 유형이 있지만 상대 `jcr:content/metadata/@cq:tags` 속성에 대한 전체 텍스트 제한이 있습니다.

이 속성은 `dam:Asset` 노드 유형에 대한 쿼리에 가장 일반적으로 사용되는 전체 텍스트 인덱스인 `damAssetLucene` 인덱스에서 분석된 것으로 표시되지 않습니다. 따라서 이 색인은 이 쿼리에 사용할 수 없습니다.

따라서 쿼리는 포함된 모든 속성이 `/oak:index/lucene-2/indexRules/nt:base/properties/prop`에서 와일드카드 일치 항목으로 분석된 것으로 표시되는 일반 전체 텍스트 인덱스로 대체됩니다.

>[!IMPORTANT]
>
>**고객 작업 필요**
>
>`damAssetLucene` 인덱스의 사용자 지정 버전에서 분석된 대로 `jcr:content/metadata/@cq:tags` 속성을 표시하면 이 쿼리가 이 인덱스로 처리되고 WARN이 기록되지 않습니다.

### 작성자 인스턴스 {#author-instance}

고객 애플리케이션 서블릿, OSGi 구성 요소 및 렌더링 스크립트의 쿼리 외에도 몇 가지 작성자별 일반 Lucene 인덱스 사용이 있을 수 있습니다.

#### 참조 검색 {#reference-search}

지금까지 일반 Lucene 색인은 참조 검색을 지원하거나 다른 콘텐츠 경로에 대한 참조가 포함된 콘텐츠를 검색하는 데 사용되었습니다. 새 `/oak:index/pathreference` 인덱스를 사용하도록 이러한 쿼리가 이미 업데이트되었을 것입니다.

#### 경로 필드 선택기 검색 {#picker-search}

AEM에는 다른 AEM 경로를 선택할 수 있는 브라우저/선택기를 제공하는 Sling 리소스 유형이 `granite/ui/components/coral/foundation/form/pathfield`인 사용자 지정 대화 상자 구성 요소가 포함되어 있습니다. 콘텐츠 구조에 사용자 지정 `pickerSrc` 속성이 정의되지 않은 경우 사용되는 기본 경로 필드 선택기는 팝업 대화 상자에서 검색 창을 렌더링합니다.

`nodeTypes` 속성을 사용하여 검색할 노드 형식을 지정할 수 있습니다.

현재 `nodeTypes` 속성이 없으면 기본 검색 쿼리에서 `nt:base` 노드 형식을 사용하므로 일반적으로 다음과 유사한 WARN 메시지를 로깅하는 일반 Lucene 인덱스를 사용할 수 있습니다.

```text
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Change the query or the index definitions.
```

일반 Lucene 인덱스를 제거하기 전에 `nodeTypes` 속성을 제공하지 않는 기본 선택기를 사용하는 구성 요소에 대해 검색 상자가 숨겨지도록 `pathfield` 구성 요소가 업데이트됩니다.

| 검색이 있는 경로 필드 선택기 | 검색이 없는 경로 필드 선택기 |
|---|---|
| ![검색이 있는 경로 필드 선택기](assets/index-pathfield-picker-with-search.png) | ![검색이 없는 경로 필드 선택기](assets/index-pathfield-picker-without-search.png) |

>[!IMPORTANT]
>
>**고객 작업 필요**
>
>고객이 경로 필드 선택기 내에서 검색 기능을 유지하려면 쿼리할 노드 유형을 나열하는 `nodeTypes` 속성을 제공해야 합니다. `String` 속성에서 쉼표로 구분된 노드 형식 목록으로 지정할 수 있습니다. 검색이 필요하지 않은 경우 고객의 조치가 필요하지 않습니다.

>[!NOTE]
>
>콘텐츠 조각 모델 편집기에서 Sling 리소스 형식이 `dam/cfm/models/editor/components/contentreference`인 특수 경로 필드를 사용합니다.
>
> * 현재는 이러한 작업에서 노드 유형을 지정하지 않고 쿼리를 수행하므로 일반 Lucene 인덱스 사용으로 인해 WARN이 기록됩니다.
> * 이러한 구성 요소의 인스턴스는 추가 고객 조치 없이 곧 자동으로 `cq:Page` 및 `dam:Asset` 노드 유형을 사용하는 것으로 설정됩니다.
> * 이러한 기본 노드 형식을 재정의하기 위해 `nodeTypes` 속성을 추가할 수 있습니다.

## 일반 Lucene 제거 타임라인 {#timeline}

Adobe은 일반적인 Lucene 인덱스를 제거하는 2단계 접근 방식을 취합니다.

* **단계 1**(2022년 1월 31일 시작 예정): 더 이상 새 AEM as a Cloud Service 환경에서 `/oak:index/lucene-*`을(를) 만들지 않습니다.
* **2단계**(2022년 3월 31일 시작 예정): 기존 AEM as a Cloud Service 환경에서 `/oak:index/lucene-*` 인덱스를 제거하십시오.

Adobe은 위에 언급된 로그 메시지를 모니터링하고 일반 Lucene 색인에 계속 의존하는 고객에게 문의하려고 시도합니다.

단기적인 완화 차원에서 Adobe은 고객 시스템에 사용자 정의 인덱스 정의를 직접 추가하여 필요에 따라 일반 Lucene 인덱스를 제거하여 발생하는 기능이나 성능 문제를 방지합니다.

이러한 경우 고객에게 업데이트된 색인 정의가 제공되며 이를 Cloud Manager을 통한 향후 애플리케이션 릴리스에 포함하는 것이 좋습니다.
