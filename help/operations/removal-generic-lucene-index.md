---
title: 일반 Lucene 색인 제거
description: 일반 Lucene 인덱스 제거와 영향을 받는 방법에 대해 알아봅니다.
exl-id: 3b966d4f-6897-406d-ad6e-cd5cda020076
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%

---

# 일반 Lucene 색인 제거 {#generic-lucene-index-removal}

Adobe이 &quot;일반 Lucene&quot; 인덱스(`/oak:index/lucene-*`) 내의 아무 곳에나 삽입할 수 있습니다. 이 색인은 AEM 6.5 이후 더 이상 사용되지 않습니다. 이 문서에서는 AEM 인스턴스가 영향을 받는지 검사하는 방법에 대한 자세한 설명과 함께 이 결정의 영향을 설명합니다. 또한 일반 Lucene 인덱스 없이 계속 작동하도록 쿼리를 변경하는 방법도 포함되어 있습니다.

## 배경 {#background}

AEM에서 전체 텍스트 쿼리는 다음 함수를 사용하는 쿼리입니다.

* `jcr:contains()` JCR XPATH에서
* `CONTAINS` JCR-SQL2에서

이러한 쿼리는 인덱스를 사용하지 않으면 결과를 반환할 수 없습니다. 경로나 속성 제한만 포함하는 질의와 달리 색인을 찾을 수 없는 전체 텍스트 제한이 포함된 쿼리는 항상 0 결과를 반환합니다.

일반 Lucene 인덱스(`/oak:index/lucene-*`)는 일부 경로(예: )가 있지만 대부분의 저장소 계층 구조에서 전체 텍스트 검색을 제공하기 위해 AEM 6.0 / Oak 1.0 이후에 존재했습니다 `/jcr:system` 및 `/var` 항상 이 항목에서 제외되어 왔습니다. 그러나 이 인덱스는 보다 구체적인 노드 유형(예: `damAssetLucene-*` 대상 `dam:Asset` 노드 유형)으로, 전체 텍스트 및 속성 검색을 모두 지원합니다.

AEM 6.5에서 일반 Lucene 색인은 사용되지 않음으로 표시되어, 이후 버전에서 제거됨을 나타냅니다. 이후, 다음 로그 코드 조각에서 설명한 대로 색인이 사용된 경우 WARN이 기록됩니다.

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Please change the query or the index definitions.
```

최근 AEM 버전에서는 일반 Lucene 인덱스가 매우 적은 수의 기능을 지원하는 데 사용되었습니다. 다른 인덱스를 사용하기 위해 다시 작업하거나 다른 방법으로 수정되어 이 인덱스에 대한 종속성을 제거합니다.

예를 들어 다음 예와 같은 참조 조회 쿼리는 이제 의 인덱스를 사용해야 합니다. `/oak:index/pathreference`에만 색인화된 `String` JCR 경로를 찾는 정규 표현식과 일치하는 속성 값입니다.

```text
//*[jcr:contains(., '"/content/dam/mysite"')]
```

더 큰 고객 데이터 볼륨을 지원하기 위해 Adobe은 더 이상 새로운 AEM as a Cloud Service 환경에서 일반 Lucene 인덱스를 만들지 않습니다. 또한 Adobe이 기존 리포지토리에서 인덱스를 제거하기 시작합니다. [타임라인을 참조하십시오](#timeline) 자세한 내용은 이 문서의 끝에 있습니다.

Adobe은 이미 다음을 통해 색인 비용을 조정했습니다 `costPerEntry` 및 `costPerExecution` 속성을 사용하여 `/oak:index/pathreference` 가능한 모든 곳에서 우선적으로 사용됩니다.

이 인덱스에 종속된 쿼리를 사용하는 고객 응용 프로그램은 필요한 경우 사용자 정의할 수 있는 다른 기존 인덱스를 활용하도록 즉시 업데이트해야 합니다. 또는 고객 애플리케이션에 새로운 사용자 지정 인덱스를 추가할 수 있습니다. AEM as a Cloud Service의 색인 관리에 대한 전체 지침은 [인덱싱 문서](/help/operations/indexing.md)

## 영향을 받습니까? {#are-you-affected}

다른 전체 텍스트 색인이 쿼리를 처리할 수 없는 경우 일반 Lucene 인덱스가 현재 폴백으로 사용됩니다. 이 사용되지 않는 인덱스를 사용하면 다음과 같은 메시지가 WARN 수준에서 기록됩니다.

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Please change the query or the index definitions.
```

경우에 따라 Oak가 다른 전체 텍스트 인덱스(예: `/oak:index/pathreference`)를 사용하여 전체 텍스트 쿼리를 지원하지만 쿼리 문자열이 색인 정의의 정규 표현식과 일치하지 않으면 메시지가 WARN 수준에서 기록되고 쿼리는 결과를 반환하지 않을 수 있습니다.

```text
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

일반 Lucene 인덱스가 제거되면 전체 텍스트 쿼리가 적절한 인덱스 정의를 찾을 수 없을 경우 아래 표시된 메시지가 경고 수준에서 기록됩니다.

```text
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results will be returned
```

>[!IMPORTANT]
>
>**고객 작업 필요**
>
> 위의 경고 메시지가 기록되면 다른 전체 텍스트 인덱스를 사용하기 위해 질의를 재작업하거나 질의를 지원하는 새 인덱스를 제공해야 할 수 있습니다.
>
>볼 수 있는 종속성 유형과 이러한 유형에 대한 해결 방법에 대한 자세한 내용은 다음 섹션에 나와 있습니다.

## 일반 Lucene 인덱스에 대한 잠재적 종속성 {#potential-dependencies}

애플리케이션과 AEM 설치가 작성자 및 게시 인스턴스 둘 다에 따라 일반 Lucene 인덱스에 종속될 수 있는 영역이 많습니다.

### 게시 인스턴스 {#publish-instance}

#### 사용자 정의 응용 프로그램 쿼리 {#custom-application-queries}

게시 인스턴스에서 일반 Lucene 인덱스를 사용하는 쿼리의 가장 일반적인 소스는 사용자 지정 응용 프로그램 쿼리입니다.

가장 간단한 경우는 노드 유형이 지정되지 않은 질의일 수 있으며, 이는 다음을 의미합니다 `nt:base` 또는 `nt:base` 다음과 같이 명시적으로 지정됩니다.

```text
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

>[!IMPORTANT]
>
>**고객 작업 필요**
>
>위의 쿼리는 다음 섹션에 자세히 설명된 대로 적절한 노드 유형을 사용하도록 수정해야 합니다.

예를 들어 쿼리를 수정하여 페이지 또는 `cq:Page node`. 따라서 쿼리는 다음과 같습니다.

```text
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

다른 경우 쿼리는 노드 유형을 지정하지만 다음과 같은 다른 전체 텍스트 인덱스로 처리할 수 없는 전체 텍스트 제한을 포함할 수 있습니다.

```text
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

이 경우 쿼리에 `dam:Asset` 노드 유형이지만 상대 `jcr:content/metadata/@cq:tags` 속성을 사용합니다.

이 속성은 `damAssetLucene` 색인입니다. 색인은 `dam:Asset` 노드 유형입니다. 따라서 이 쿼리에 이 인덱스를 사용할 수 없습니다.

따라서 쿼리에서 포함된 모든 속성이 와일드카드 일치로 분석된 것으로 표시되는 일반 전체 텍스트 인덱스가 다시 나타납니다 `/oak:index/lucene-2/indexRules/nt:base/properties/prop`.

>[!IMPORTANT]
>
>**고객 작업 필요**
>
>표시 `jcr:content/metadata/@cq:tags` 사용자 지정 버전의 `damAssetLucene` 인덱스로 인해 이 쿼리가 처리되고 WARN이 기록되지 않습니다.

### 작성자 인스턴스 {#author-instance}

고객 애플리케이션 서블릿, OSGi 구성 요소 및 렌더링 스크립트에서 쿼리 외에도 일반 Lucene 인덱스에 대한 다양한 작성자별 사용이 있을 수 있습니다.

#### 참조 검색 {#reference-search}

이전에 일반 Lucene 색인은 다른 컨텐츠 경로에 대한 참조가 포함된 컨텐츠를 검색하거나 참조 검색을 지원하는 데 사용되었습니다. 이러한 쿼리는 이미 새 `/oak:index/pathreference` 색인입니다.

#### 경로 필드 선택기 검색 {#picker-search}

AEM에는 Sling 리소스 유형이 있는 사용자 지정 대화 상자 구성 요소가 포함됩니다 `granite/ui/components/coral/foundation/form/pathfield`: 다른 AEM 경로를 선택할 수 있는 브라우저/선택기를 제공합니다. 사용자 지정 항목이 없을 때 사용되는 기본 경로 필드 선택기입니다 `pickerSrc` 속성은 컨텐츠 구조에 정의되어 있고 팝업 대화 상자에서 검색 막대를 렌더링합니다.

검색할 노드 유형은 `nodeTypes` 속성을 사용합니다.

없는 경우 현재 `nodeTypes` 속성이 있으면 기본 검색 쿼리에서 `nt:base` 노드 유형이며, 따라서 일반 Lucene 인덱스를 사용할 수 있으며, 일반적으로 다음과 유사한 경고 메시지를 기록합니다.

```text
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Please change the query or the index definitions.
```

일반 Lucene 인덱스를 제거하기 전에 `pathfield` 기본 선택기를 사용하여 구성 요소에 대해 검색 상자가 숨겨지도록 구성 요소가 업데이트됩니다 `nodeTypes` 속성을 사용합니다.

| 검색을 사용하는 경로 필드 선택기 | 검색 없이 경로 필드 선택기 |
|---|---|
| ![검색을 사용하는 경로 필드 선택기](assets/index-pathfield-picker-with-search.png) | ![검색 없이 경로 필드 선택기](assets/index-pathfield-picker-without-search.png) |

>[!IMPORTANT]
>
>**고객 작업 필요**
>
>고객이 경로 필드 선택기에서 검색 기능을 유지하려면 `nodeTypes` 쿼리할 노드 유형을 나열하는 속성을 제공해야 합니다. 이러한 목록은 `String` 속성을 사용합니다. 검색이 필요하지 않으면 고객으로부터 조치가 필요하지 않습니다.

>[!NOTE]
>
>컨텐츠 조각 모델 편집기는 Sling 리소스 유형이 있는 전문 경로 필드를 사용합니다 `dam/cfm/models/editor/components/contentreference`.
> * 현재 노드 유형을 지정하지 않고 쿼리를 수행하므로 일반 Lucene 인덱스를 사용하여 WARN이 기록됩니다.
> * 이러한 구성 요소의 인스턴스는 곧 자동으로 `cq:Page` 및 `dam:Asset` 추가 고객 작업이 없는 노드 유형.
> * 다음 `nodeTypes` 이러한 기본 노드 유형을 재정의하기 위해 속성을 추가할 수 있습니다.


## 일반 Lucene 제거를 위한 타임라인 {#timeline}

Adobe은 일반 Lucene 인덱스를 제거하기 위해 2단계 접근 방식을 취할 것입니다.

* **1단계** (예정 시작: 2022년 1월 31일): 더 이상 생성 안 함 `/oak:index/lucene-*` 새 AEM as a Cloud Service 환경에서 사용할 수 있습니다.
* **2단계** (예정 시작: 2022년 3월 31일): 제거 `/oak:index/lucene-*` 기존 AEM as a Cloud Service 환경의 인덱스.

Adobe은 위에 언급된 로그 메시지를 모니터링하고 일반 Lucene 인덱스에 종속되어 있는 고객에게 연락을 시도합니다.

단기적인 완화를 위해, Adobe은 필요한 경우 일반 Lucene 인덱스를 제거한 결과 기능이나 성능 문제를 방지하기 위해 고객 시스템에 직접 사용자 지정 인덱스 정의를 추가합니다.

이러한 경우 고객은 업데이트된 색인 정의를 받게 되며 Cloud Manager를 통해 향후 애플리케이션 릴리스에 이를 포함하도록 권장합니다.
