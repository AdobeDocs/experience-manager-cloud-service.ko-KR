---
title: 일반 lucene 인덱스 제거
description: 일반 lucene 인덱스 제거
exl-id: fe0e00ac-f9c8-43cf-83c2-5a353f5eaeab
source-git-commit: bc7ef6567ad5baa4becd28a7e7d96bd6b579e1ad
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 0%

---

# &#39;일반 lucene&#39; 인덱스 제거

Adobe이 &#39;일반 lucene&#39; 인덱스(`/oak:index/lucene-*`) 내의 아무 곳에나 삽입할 수 있습니다. 이 색인은 AEM 6.5 이후 더 이상 사용되지 않습니다. 이 설명서에서는 AEM 인스턴스가 영향을 받는지 여부를 검사하는 자세한 설명과 함께 이 결정의 영향을 설명합니다. 마지막으로 쿼리를 변경할 수 있는 방법이 포함되어 있으므로 이 색인이 없는 작업이 수행됩니다.

## 배경

AEM에서 &#39;fulltext&#39;는 다음 함수를 사용하는 것으로 쿼리합니다.

* `jcr:contains()` JCR XPATH에서
* `CONTAINS` JCR-SQL2에서

이러한 쿼리는 인덱스를 사용하지 않으면 결과를 반환할 수 없습니다. 경로나 속성 제한만 포함하는 질의와 달리 색인을 찾을 수 없는 전체 텍스트 제한이 포함된 쿼리는 항상 0 결과를 반환합니다.

&#39;일반 lucene&#39; 인덱스(`/oak:index/lucene-*`)은 대부분의 저장소 계층(예: 일부 경로)에서 전체 텍스트 검색을 제공하기 위해 AEM 6.0 / Oak 1.0 이후에 존재했습니다 `/jcr:system` 및 `/var` 이 색인은 항상 이로부터 제외됨) 하지만 보다 특정 노드 유형의 색인에 의해 대체되었습니다(예: `damAssetLucene-*` fulltext와 property 검색을 모두 지원하는 &#39;dam:Asset&#39; nodetype)입니다.

AEM 6.5에서 &#39;generic lucene&#39; 색인은 사용되지 않음으로 표시되었으며(향후 버전에서 제거될 것임을 표시) 이후 색인이 사용되었을 때 WARN이 기록됩니다.

```
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Please change the query or the index definitions.
```

최근 AEM 버전에서는 &#39;일반 lucene&#39; 색인이 매우 적은 수의 기능을 지원하는 데 사용되었습니다. 다른 인덱스를 사용하기 위해 다시 작업하거나 다른 방법으로 수정되어 이 인덱스에 대한 종속성을 제거합니다.
예를 들어, 아래 표시된 양식의 &#39;참조 조회&#39; 쿼리는 이제 &#39;/oak:index/paterference&#39;의 인덱스를 사용해야 합니다(JCR 경로를 찾는 정규식과 일치하는 String 속성 값만 인덱싱함). 

```
//*[jcr:contains(., '"/content/dam/mysite"')]
```

더 큰 고객 데이터 볼륨을 지원하기 위해 Adobe은 더 이상 새 AEM as a Cloud Service 환경에서 &#39;일반 lucene&#39; 인덱스를 만들지 않으며, 이를 통해 기존 저장소에서 색인을 제거하기 시작합니다. 다른 인덱스(예: `/oak:index/pathreference`)이 `/oak:index/lucene-*` 가능하다면 어디든 간에 

이 인덱스에 따라 쿼리를 사용하는 고객 응용 프로그램은 다른 기존 인덱스를 활용하기 위해 즉시 업데이트되어야 합니다(필요한 경우 사용자 지정할 수 있음). 또는 새 사용자 지정 인덱스를 고객 응용 프로그램에 추가해야 합니다. AEM as a Cloud Service의 색인 관리에 대한 전체 지침은 [색인 설명서](/help/operations/indexing.md).

## 응용 프로그램이 &#39;일반 lucene&#39; 인덱스에 따라 달라지는지 확인하는 방법

다른 전체 텍스트 색인이 쿼리를 처리할 수 없는 경우 &#39;일반 lucene&#39; 인덱스가 현재 &#39;폴백&#39;으로 사용됩니다. 이 사용되지 않는 인덱스를 사용하면 다음과 같은 메시지가 WARN 수준에서 기록됩니다.

```
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Please change the query or the index definitions.
```

경우에 따라 Oak가 다른 전체 텍스트 인덱스(예: `/oak:index/pathreference`)를 사용하여 전체 텍스트 쿼리를 지원하지만 쿼리 문자열이 색인 정의의 정규 표현식과 일치하지 않으면 메시지가 WARN 수준에서 기록되고 쿼리는 결과를 반환하지 않을 수 있습니다.

```
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

&#39;일반 lucene&#39; 인덱스가 제거되면 전체 텍스트 쿼리에서 적절한 인덱스 정의를 찾을 수 없으면 아래에 표시된 메시지가 경고 수준에서 기록됩니다.

```
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results will be returned
```

이러한 인덱스가 기록되면 다른 전체 텍스트 인덱스를 사용하기 위해 쿼리를 재작업하거나 쿼리를 지원하기 위해 새 인덱스를 제공해야 할 수 있습니다. 볼 수 있는 종속성 유형과 이러한 유형에 대한 해결 방법에 대한 자세한 내용은 아래에 나와 있습니다.

## &#39;일반 lucene&#39; 인덱스에 대한 잠재적 종속성

### 게시

#### 사용자 정의 응용 프로그램 쿼리

게시에서 &#39;일반 lucene&#39; 인덱스를 사용하는 쿼리의 가장 일반적인 소스는 사용자 지정 응용 프로그램 쿼리입니다.

가장 간단한 경우는 다음 항목이 지정되지 않은 쿼리(&#39;nt:base&#39;를 의미) 또는 명시적으로 지정된 nt:base가 없는 쿼리일 수 있습니다.

```
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

필요한 작업 : 이러한 쿼리는 적절한 노드 유형을 사용하도록 수정할 수 있습니다. 예를 들어 쿼리에서 일치하는 페이지(또는 cq:Page 노드 아래에 있는 &#39;집계&#39;를 반환하도록 할 수 있습니다.)

```
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

다른 경우 쿼리는 노드 유형을 지정하지만 다음과 같은 다른 전체 텍스트 인덱스에서 처리할 수 없는 전체 텍스트 제한을 포함할 수 있습니다.

```
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

이 경우 쿼리에 &#39;dam:Asset&#39; 노드 유형이 있지만 상대적인 텍스트에 대한 전체 텍스트 제한이 포함되어 있습니다 `jcr:content/metadata/@cq:tags` 속성을 사용합니다.

이 속성은 damAssetLucene 색인에서 &#39;analytics&#39;로 표시되지 않습니다(전체 텍스트 색인은 &#39;dam:Asset&#39; 노드 유형에 대한 쿼리에 가장 일반적으로 사용됨). 따라서 이 색인은 이 쿼리에 사용할 수 없습니다.

따라서 쿼리가 포함된 모든 속성이 와일드카드 일치로 분석된 것으로 표시되는 &#39;일반 전체 텍스트&#39; 인덱스에 다시 배치됩니다. `/oak:index/lucene-2/indexRules/nt:base/properties/prop`.

고객 작업 필요 : 표시 `jcr:content/metadata/@cq:tags` damAssetLucene 인덱스의 사용자 지정 버전에서 &#39;analytics&#39;된 속성을 사용하면 이 색인이 이 쿼리를 처리하며 WARN이 기록되지 않습니다.

### 작성 

고객 애플리케이션 서블릿의 쿼리 외에 OSGI 구성 요소 및 렌더링 스크립트도 &#39;generic lucene&#39; 인덱스에 대한 다양한 작성자별 사용이 있을 수 있습니다. 

#### 참조 검색

이전에 &#39;일반 lucene&#39; 색인은 &#39;참조 검색&#39;을 지원하는 데 사용되었습니다(다른 컨텐츠 경로에 대한 참조가 포함된 컨텐츠 검색). 이러한 쿼리는 새 &#39;/oak:index/paterference&#39; 인덱스를 사용하기 위해 이미 이동했어야 합니다.
고객 작업 필요 : 고객 조치가 필요하지 않습니다.


#### 경로 필드 선택기 검색

AEM에는 다른 AEM 경로를 선택할 수 있는 브라우저(선택기)를 제공하는 사용자 지정 대화 상자 구성 요소(Sling 리소스 유형 &#39;granite/ui/components/coral/foundation/form/pathfield&#39;)가 포함되어 있습니다.  기본 경로 필드 선택기(컨텐츠 구조에 정의된 사용자 지정 &#39;pickerSrc&#39; 속성이 없을 때 사용됨)는 팝업 대화 상자에서 검색 막대를 렌더링합니다.
&#39;nodeTypes&#39; 속성을 사용하여 검색할 노드 유형을 지정할 수 있습니다.

현재 &#39;nodeTypes&#39; 속성이 없는 경우 기본 검색 쿼리는 &#39;nt:base&#39; 노드 유형을 사용하므로 &#39;generic lucene&#39; 인덱스를 사용할 수 있습니다(일반적으로 아래에 표시된 WARN 메시지를 로깅함).

```
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Please change the query or the index definitions.
```

&#39;generic lucene&#39;을 제거하기 전에 &#39;nodeTypes&#39; 속성을 제공하지 않는 기본 선택기를 사용하여 구성 요소에 대해 검색 상자가 숨겨지도록 경로 필드 구성 요소가 업데이트됩니다.

| 검색을 사용하는 경로 필드 선택기 | 검색 없이 경로 필드 선택기 |
|---|---|
| ![검색을 사용하는 경로 필드 선택기](assets/index-pathfield-picker-with-search.png) | ![검색 없이 경로 필드 선택기](assets/index-pathfield-picker-without-search.png) |


고객 작업 필요 : 검색이 필요하지 않으면 고객으로부터 조치가 필요하지 않습니다.

고객이 경로 필드 선택기에서 검색 기능을 유지하려면 쿼리할 노드 유형을 나열하는 &#39;nodeTypes&#39; 속성을 제공해야 합니다. String 속성에서 쉼표로 구분된 노드 목록으로 지정할 수 있습니다.


>[!NOTE]
>컨텐츠 조각 모델 편집기는 Sling 리소스 유형 &#39;dam/cfm/models/editor/components/contentreference&#39;가 있는 전문 경로 필드를 사용합니다.
> * 현재 노드 유형이 지정되지 않은 쿼리를 수행하여 &#39;generic lucene&#39; 인덱스를 사용하여 WARN이 기록됩니다.
> * 이러한 구성 요소의 인스턴스는 추가 고객 작업 없이 자동으로 &#39;cq:Page&#39; 및 &#39;dam:Asset&#39; 노드를 사용합니다.
> * &#39;nodeTypes&#39; 속성을 추가하여 이러한 기본 노드 유형을 재정의할 수 있습니다. 





## &#39;일반 lucene&#39; 제거를 위한 타임라인

Adobe은 &#39;일반 lucene&#39; 색인을 제거하는 2단계 접근 방식을 취할 것이다.

**1단계** (예정 시작 날짜: 2022년 1월 31일): 더 이상 새 AEM as a Cloud Service 환경에서 &#39;/oak:index/lucene-*&#39;를 만들지 않습니다.

**2단계** (예정: 2022년 3월 31일) : 새 AEM as a Cloud Service 환경에서 &#39;/oak:index/lucene-*&#39; 인덱스를 제거합니다.

Adobe은 위에 언급된 로그 메시지를 모니터링하고 &#39;generic lucene&#39; 인덱스에 종속되어 있는 고객에게 연락을 시도합니다.

단기적인 완화를 위해, 필요한 경우 Adobe이 &#39;일반 lucene&#39; 인덱스를 제거한 결과 기능이나 성능 문제를 방지하기 위해 고객 시스템에 직접 사용자 지정 인덱스 정의를 추가합니다.

이러한 경우 고객은 업데이트된 색인 정의를 받게 되며 Cloud Manager를 통해 향후 애플리케이션 릴리스에 이를 포함하도록 권장합니다.
