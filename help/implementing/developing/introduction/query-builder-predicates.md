---
title: 쿼리 빌더 조건자 참조
description: AEMas a Cloud Service 의 Query Builder API에 대한 설명 참조.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
source-git-commit: e10c39c1d7fa05b738dd8f25662617a3a9568f83
workflow-type: tm+mt
source-wordcount: '2295'
ht-degree: 1%

---

# 쿼리 빌더 조건자 참조 {#query-builder-predicate-reference}

## 일반 {#general}

### 루트 {#root}

루트 조건자 그룹입니다. 그룹의 모든 기능을 지원하고 전역 쿼리 매개 변수를 설정할 수 있습니다.

&quot;루트&quot;라는 이름은 쿼리에서 사용되지 않으며 암시적입니다.

#### 속성 {#properties-18}

* **`p.offset`** - 결과 페이지의 시작, 즉 건너뛸 항목의 수를 나타내는 숫자입니다.
* **`p.limit`** - 페이지 크기를 나타내는 숫자입니다.
* **`p.guessTotal`** - 권장: 비용이 많이 들 수 있는 전체 결과 합계를 계산하지 마십시오. 계산할 최대 합계를 나타내는 숫자(예: 1000, 대략적인 크기에 대한 충분한 피드백과 더 작은 결과에 대한 정확한 숫자)입니다. 또는, `true` 필요한 최소값까지만 계산하다 `p.offset` + `p.limit`.
* **`p.excerpt`** - 로 설정된 경우 `true`를 입력하면 결과에 전체 텍스트 발췌가 포함됩니다.
* **`p.indexTag`** - 설정하면 쿼리에 색인 태그 옵션이 포함됩니다(참조). [쿼리 옵션 색인 태그](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-option-index-tag)).
* **`p.facetStrategy`** - 로 설정된 경우 `oak`, Query Builder는 Oak에 Facet 추출을 위임합니다( 참조) [패싯](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#facets)).
* **`p.hits`** - (JSON 서블릿만 해당) 히트가 JSON으로 기록되는 방식을 선택합니다(ResultHitWriter 서비스를 통해 확장 가능).
   * **`simple`** - 다음과 같은 최소 항목 `path`, `title`, `lastmodified`, `excerpt` (설정된 경우).
   * **`full`** - 노드의 sling JSON 렌더링, `jcr:path` 히트의 경로를 나타냅니다. 기본적으로 에는 노드의 직접 속성만 나열되며 다음과 같은 심층 트리가 포함됩니다. `p.nodedepth=N`를 0으로 지정하면 전체, 무한 하위 트리를 의미합니다. 추가 `p.acls=true` 주어진 결과 항목에 현재 세션의 JCR 권한을 포함시키려면 다음을 수행합니다(매핑: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).
   * **`selective`** - 다음에서 지정된 속성만 `p.properties`: 분리된 공간입니다(사용) `+` 상대 경로의 URL 목록. 상대 경로에 깊이가 있는 경우 `>1`, 이러한 속성은 하위 개체로 표시됩니다. 더 스페셜 `jcr:path` 속성에는 히트의 경로가 포함됩니다.

### 그룹 {#group}

이 술어를 사용하여 중첩된 조건을 작성할 수 있습니다. 그룹은 중첩 그룹을 포함할 수 있습니다. Query Builder 쿼리의 모든 항목은 암시적으로 루트 그룹에 있으며 `p.or` 및 `p.not` 매개 변수도 마찬가지입니다.

다음은 값에 대해 두 속성 중 하나를 일치시키는 예입니다.

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

개념상 다음과 같습니다. `(1_property` 또는 `2_property)`.

중첩 그룹의 예는 다음과 같습니다.

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

검색어를 찾습니다 **관리** 의 페이지 내 `/content/wknd/ch/de` 또는 의 에셋에서 `/content/dam/wknd`.

개념상 다음과 같습니다. `fulltext AND ( (path AND type) OR (path AND type) )`. 이러한 OR 조인은 성능상의 이유로 좋은 색인이 필요합니다.

#### 속성 {#properties-6}

* **`p.or`** - 로 설정된 경우 `true`, 그룹의 한 개의 술어만 일치해야 합니다. 기본값은 입니다. `false`즉, 모두 일치해야 합니다.
* **`p.not`** - 로 설정된 경우 `true`, 그룹을 부정합니다(기본값: `false`)
* **`<predicate>`** - 중첩된 술어 추가
* **`N_<predicate>`** - 다음과 같이 중첩된 여러 술어를 동시에 추가합니다. `1_property, 2_property, ...`

### orderby {#orderby}

이 술어를 사용하면 결과를 정렬할 수 있습니다. 여러 속성별 순서 지정이 필요한 경우 숫자 접두사를 사용하여 이 조건자를 여러 번 추가해야 합니다. 예: `1_orderby=first`, `2_oderby=second`.

#### 속성 {#properties-13}

* **`orderby`** - 앞에 @가 있는 JCR 속성 이름(예: ) `@jcr:lastModified` 또는 `@jcr:content/jcr:title`또는 쿼리의 다른 조건자(예: ) `2_property`, 정렬 대상
* **`sort`** - 정렬 방향, 다음 중 하나 `desc` 내림차순 또는 `asc` 오름차순(기본값)
* **`case`** - 로 설정된 경우 `ignore`, 정렬에서 대/소문자를 구분하지 않습니다. 즉, `a` 다음 앞에 옴 `B`; 비어 있거나 누락된 경우 정렬은 대소문자를 구분하며, 즉 `B` 다음 앞에 옴 `a`

## 술어 {#predicates}

### 부울 속성 {#boolproperty}

이 술어는 JCR 부울 속성에서 일치합니다. 값만 수락 `true` 및 `false`. 값이 인 경우 `false`속성에 값이 있으면 일치합니다 `false`또는 존재하지 않는 경우입니다. 이 술어는 활성화된 경우에만 설정되는 부울 플래그를 확인하는 데 유용합니다.

상속됨 `operation` 매개 변수에 의미가 없습니다.

이 술어는 패싯 추출을 지원하고 각 항목에 대한 버킷을 제공합니다 `true` 또는 `false` 값(기존 속성만 해당).

#### 속성 {#properties}

* **`boolproperty`** - 속성에 대한 상대 경로(예: `myFeatureEnabled` 또는 `jcr:content/myFeatureEnabled`
* **`value`** - 속성을 확인할 값, `true` 또는 `false`

### contentfragment {#contentfragment}

이 조건자는 결과를 콘텐츠 조각으로 제한합니다.

* 필터링을 지원하지 않습니다.
* 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-1}

* **`contentfragment`** - 모든 값과 함께 사용하여 콘텐츠 조각을 확인할 수 있습니다.

### `dateComparison` {#datecomparison}

이 술어는 두 JCR 날짜 속성을 서로 비교합니다. 같음, 같지 않음, 크거나 같음 또는 같은지 테스트할 수 있습니다.

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

#### 속성 {#properties-2}

* **`property1`** - 첫 번째 날짜 속성에 대한 경로
* **`property2`** - 두 번째 날짜 속성에 대한 경로
* **`operation`**
   * `=` 정확한 일치(기본값)
   * `!=` 같지 않음 비교용
   * `>` 대상 `property1` 보다 큼 `property2`
   * `>=` 대상 `property1` 크거나 같음 `property2`

### 다터랑주 {#daterange}

이 술어는 날짜/시간 간격에 대해 JCR 날짜 속성을 일치시킵니다. 날짜 및 시간에 ISO8601 형식 사용(`YYYY-MM-DDTHH:mm:ss.SSSZ`) 및 는 다음과 같은 부분 표현도 허용합니다. `YYYY-MM-DD`. 또는 타임스탬프를 POSIX 시간으로 제공할 수 있습니다.

두 타임스탬프 사이에 있는 모든 항목, 지정된 날짜보다 최신 항목 또는 오래된 항목을 찾을 수 있으며 포함 간격과 열기 간격 사이에서 선택할 수도 있습니다.

Facet 추출을 지원하고 버킷을 제공합니다 `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year`, 및 `earlier than last year`.

필터링을 지원하지 않습니다.

#### 속성 {#properties-3}

* **`property`** - 의 상대 경로 `DATE` 속성(예: ) `jcr:lastModified`
* **`lowerBound`** - 예를 들어 의 속성을 확인하기 위해 바인딩된 보다 작은 날짜 `2014-10-01`
* **`lowerOperation`** - `>` (최신 버전) 또는 `>=` (또는 그 이상)에 적용됩니다. `lowerBound`. 기본값은 입니다 `>`
* **`upperBound`** - 속성을 확인할 상한값(예: ) `2014-10-01T12:15:00`
* **`upperOperation`** - `<` (이전) 또는 `<=` (또는 그 이상)에 적용됩니다. `upperBound`. 기본값은 입니다 `<`
* **`timeZone`** - ISO-8601 날짜 문자열로 제공되지 않을 때 사용할 표준 시간대의 ID입니다. 기본값은 시스템의 기본 시간대입니다.

### excludepaths {#excludepaths}

이 조건자는 해당 경로가 정규 표현식과 일치하는 결과에서 노드를 제외합니다.

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-4}

* **`excludepaths`** - 정규 표현식이 결과 경로에 대해 일치합니다. 단, 일치하는 표현식은 결과에서 제외합니다.

### 전체 텍스트 {#fulltext}

전체 텍스트 색인에서 용어를 검색합니다.

필터링을 지원하지 않습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-5}

* **`fulltext`** - 전체 텍스트 검색어
* **`relPath`** - 속성 또는 하위 노드에서 검색할 상대 경로입니다. 이 속성은 선택 사항입니다.

### hasPermission {#haspermission}

이 조건자는 현재 세션에 지정된 항목으로 결과를 제한합니다 [JCR 권한.](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다. 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-7}

* **`hasPermission`** - 해당 노드에 대해 현재 사용자 세션에 있어야 하는 모든 쉼표로 구분된 JCR 권한. 예, `jcr:write`, `jcr:modifyAccessControl`

### 언어 {#language}

이 술어는 특정 언어로 된 AEM 페이지를 찾습니다. 페이지 언어 속성과 종종 최상위 사이트 구조에 언어 또는 로케일을 포함하는 페이지 경로를 모두 살펴봅니다.

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

패싯 추출을 지원하고 각 고유 언어 코드에 대한 버킷을 제공합니다.

#### 속성 {#properties-8}

* **`language`** - ISO 언어 코드(예: ) `de`

### 주요 자산 {#mainasset}

이 조건자는 노드가 DAM 주 자산이고 하위 자산이 아닌지 확인합니다. 이는 기본적으로 하위 에셋 노드 내에 있지 않은 모든 노드입니다. 다음을 확인하지 않습니다. `dam:Asset` 노드 유형. 이 술어를 사용하려면 을 설정합니다. `mainasset=true` 또는 `mainasset=false`. 추가 속성이 없습니다.

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

Facet 추출을 지원하고 기본 및 하위 에셋에 대해 두 개의 버킷을 제공합니다.

#### 속성 {#properties-9}

* **`mainasset`** - 부울, `true` 기본 자산의 경우 `false` 하위 자산용

### memberOf {#memberof}

이 조건자는 특정 항목의 멤버인 항목을 찾습니다. [sling 리소스 컬렉션](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/resource/collection/ResourceCollection.html).

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-10}

* **`memberOf`** - Sling 리소스 컬렉션 경로

### nodename {#nodename}

이 술어는 JCR 노드 이름에서 일치합니다.

패싯 추출을 지원하고 각 고유한 노드 이름(파일 이름)에 대한 버킷을 제공합니다.

#### 속성 {#properties-11}

* **`nodename`** - 와일드카드를 허용하는 노드 이름 패턴: `*` = any 또는 no char, `?` = 모든 문자, `[abc]` = 대괄호 안에 있는 문자만

### 가공되지 않음 {#notexpired}

이 술어는 JCR 날짜 속성이 현재 서버 시간보다 크거나 같은지 확인하여 항목을 일치시킵니다. 다음을 확인하는 데 사용할 수 있습니다. `expiresAt` 값과 제한 결과는 아직 만료되지 않은 값으로만 설정됩니다(`notexpired=true`), 또는 이미 만료된 경우(`notexpired=false`).

필터링을 지원하지 않습니다.

와 동일한 방식으로 Facet 추출을 지원합니다. [`daterange`](#daterange) 조건자.

#### 속성 {#properties-12}

* **`notexpired`** - 부울, `true` 아직 만료되지 않은 경우(미래 또는 같은 날짜), `false` 만료 날짜 (과거 날짜) (필수)
* **`property`** - 의 상대 경로 `DATE` 확인할 속성(필수)

### path {#path}

이 조건자는 주어진 경로 내에서 검색합니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-14}

* **`path`** - 경로 패턴을 정의합니다.
   * 에 따라 `exact` 전체 하위 트리가 일치하는 속성(예: 추가) `//*` xpath에 있지만 기본 경로는 포함되지 않습니다. 또는 정확한 경로만 일치하며 여기에 와일드카드(`*`).
      * 기본값은 입니다. `true`.
&lt;!— * `self`속성이 설정되면 기본 노드를 포함한 전체 하위 트리가 검색됩니다.—>
* **`exact`** - 경우 `exact` 은(는) `true`, 정확한 경로는 일치해야 하지만 단순 와일드카드(`*`), 이름과 일치하지만 일치하지 않음 `/`; 해당하는 경우 `false` (기본값) 모든 하위 항목이 포함됩니다(선택 사항).
* **`flat`** - 직접 하위만 검색합니다(예: 추가). `/*` xpath에서) (다음의 경우에만 사용됨) `exact` 참이 아님(선택 사항).
* **`self`** - 하위 트리를 검색하지만 경로로 지정된 기본 노드를 포함합니다(와일드카드 없음).
   * *중요 참고 사항*: 문제가 다음으로 식별됨: `self` query builder의 현재 구현에서 속성을 사용하고 쿼리에 사용하면 올바른 검색 결과가 생성되지 않을 수 있습니다. 의 현재 구현 변경 `self` 또한 이 속성은 이 속성에 의존하는 기존 응용 프로그램을 손상시킬 수 있으므로 실행 가능하지 않습니다. 이 기능으로 인해 `self` 이제 속성이 더 이상 사용되지 않으므로 사용하지 않는 것이 좋습니다.

### 속성 {#property}

이 술어는 JCR 속성 및 해당 값에 대해 일치합니다.

패싯 추출을 지원하고 결과에 각 고유 속성 값에 대한 버킷을 제공합니다.

#### 속성 {#properties-15}

* **`property`** - 속성에 대한 상대 경로(예: `jcr:title`.
* **`value`** - 속성을 확인할 값. JCR 속성 유형을 따라 문자열 변환을 수행합니다.
* **`N_value`** - 사용 `1_value`, `2_value`, ...을 사용하여 여러 값(결합)을 확인하는 방법 `OR` 기본적으로, 포함 `AND` if `and=true`).
* **`and`** - 다음으로 설정 `true` 여러 값 결합용(`N_value`) 포함 `AND`
* **`operation`**
   * `equals` 정확하게 일치시키려면(기본값).
   * `unequals` 같지 않음 비교에 사용됩니다.
   * `like` 사용 `jcr:like` xpath 함수(선택 사항)입니다.
   * `not` 일치 항목 없음(예: `not(@prop)` xpath에서 값 매개 변수는 무시됩니다.
   * `exists` 존재 확인을 위해.
      * `true` 속성이 있어야 합니다.
      * `false` 은(는) 과(와) 동일합니다. `not` 및 가 기본값입니다.
* **`depth`** - 속성/상대 경로가 존재할 수 있는 와일드카드 수준의 수(예: `property=size depth=2` 확인 `node/size`, `node/*/size`, 및 `node/*/*/size`).

### rangeproperty {#rangeproperty}

이 술어는 간격에 대해 JCR 속성과 일치합니다. 다음과 같은 선형 유형이 있는 속성에 적용됩니다. `LONG`, `DOUBLE`, 및 `DECIMAL`. 대상 `DATE`, 다음을 참조하십시오. [`daterange`](#daterange) 최적화된 날짜 형식 입력이 있는 조건자입니다.

하한, 상한 또는 둘 다를 정의할 수 있습니다. 작업(예: 보다 작거나 같음)은 하한과 상한에 대해서도 개별적으로 지정할 수 있습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-16}

* **`property`** - 속성에 대한 상대 경로
* **`lowerBound`** - check 속성에 대한 하한
* **`lowerOperation`** - `>` (기본값) 또는 `>=`에 적용됩니다. `lowerValue`
* **`upperBound`** - 검사 속성의 상한
* **`upperOperation`** - `<` (기본값) 또는 `<=`에 적용됩니다. `lowerValue`
* **`decimal`** - `true` checked 속성이 Decimal 형식인 경우

### 상대 날짜 범위 {#relativedaterange}

이 술어 일치 `JCR DATE` 현재 서버 시간을 기준으로 한 시간 오프셋을 사용하는 날짜/시간 간격에 대한 등록 정보입니다. 다음을 지정할 수 있습니다. `lowerBound` 및 `upperBound` 밀리초 값 또는 Bugzilla 구문 사용 `1s 2m 3h 4d 5w 6M 7y` (1초, 2분, 3시간, 4일, 5주, 6개월, 7년) 접두어 `-` 현재 시간 이전의 음수 오프셋을 나타냅니다. 다음을 지정하는 경우 `lowerBound` 또는 `upperBound`다른 하나는 기본적으로 입니다. `0`현재 시간을 나타냅니다.

예:

* `upperBound=1h` (및 아니요 `lowerBound`)다음 시간 내에 모든 항목 선택
* `lowerBound=-1d` (및 아니요 `upperBound`) 지난 24시간 내에 아무 것이나 선택합니다
* `lowerBound=-6M` 및 `upperBound=-3M` 지난 3~6개월 동안 모든 항목 선택
* `lowerBound=-1500` 및 `upperBound=5500` 향후 1,500밀리초에서 5,500밀리초 사이의 모든 항목 선택
* `lowerBound=1d` 및 `upperBound=2d` 모레 아무 것이나 선택합니다.

윤년은 고려하지 않고 모든 달은 30일입니다.

필터링을 지원하지 않습니다.

와 동일한 방식으로 Facet 추출을 지원합니다. [`daterange`](#daterange) 조건자.

#### 속성 {#properties-17}

* **`upperBound`** - 상한 날짜(밀리초) 또는 `1s 2m 3h 4d 5w 6M 7y` (현재 서버 시간 기준 1초, 2분, 3시간, 4일, 5주, 6개월, 7년) 사용 `-` 네가티브 오프셋의 경우
* **`lowerBound`** - 하한 날짜(밀리초) 또는 `1s 2m 3h 4d 5w 6M 7y` (현재 서버 시간 기준 1초, 2분, 3시간, 4일, 5주, 6개월, 7년) 사용 `-` 네가티브 오프셋의 경우

### savedquery {#savedquery}

이 조건자에는 지속 쿼리 빌더 쿼리의 모든 조건자가 현재 쿼리에 하위 그룹 조건자로 포함됩니다.

추가 쿼리를 실행하지 않고 현재 쿼리를 확장합니다.

쿼리는 를 사용하여 프로그래밍 방식으로 지속할 수 있습니다. `QueryBuilder#storeQuery()`. 형식은 여러 줄 중 하나일 수 있습니다 `String` 속성 또는 `nt:file` 쿼리를 Java™ 속성 형식의 텍스트 파일로 포함하는 노드입니다.

저장된 쿼리의 술어에 대한 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-19}

* **`savedquery`** - 저장된 쿼리의 경로(`String` 또는 속성 `nt:file` node)

### 유사 {#similar}

이 조건자는 JCR XPath를 사용하는 유사성 검색입니다. `rep:similar()`.

필터링을 지원하지 않으며 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-20}

* **`similar`** - 유사한 노드를 찾을 노드의 절대 경로
* **`local`** - 하위 노드의 상대 경로 또는 `.` 현재 노드의 경우(선택 사항, 기본값은 임) `.`)

### 태그 {#tag}

이 조건자는 태그 제목 경로를 지정하여 하나 이상의 태그로 태그가 지정된 컨텐츠를 검색합니다.

패싯 추출을 지원하고 현재 태그 제목 경로를 사용하여 각 고유 태그에 대한 버킷을 제공합니다.

#### 속성 {#properties-21}

* **`tag`** - 찾을 태그 제목 경로(예: ) `properties:orientation/landscape`
* **`N_value`** - 사용 `1_value`, `2_value`, ... 여러 태그( 와 결합됨)를 확인하는 방법 `OR` 기본적으로, 포함 `AND` if `and=true`)
* **`property`** - 살펴볼 속성(또는 속성에 대한 상대 경로)(기본값) `cq:tags`)

### 태그 {#tagid}

이 조건자는 태그 ID를 지정하여 하나 이상의 태그로 태그가 지정된 컨텐츠를 검색합니다.

패싯 추출을 지원하고 현재 태그 ID를 사용하여 각 고유 태그에 대한 버킷을 제공합니다.

#### 속성 {#properties-22}

* **`tagid`** - 찾을 태그 ID(예: ) `properties:orientation/landscape`
* **`N_value`** - 사용 `1_value`, `2_value`, ... 여러 태그 ID( 와 결합됨)를 확인하는 방법 `OR` 기본적으로, 포함 `AND` if `and=true`)
* **`property`** - 살펴볼 속성(또는 속성에 대한 상대 경로)(기본값) `cq:tags`)

### tagsearch {#tagsearch}

이 조건자는 키워드를 지정하여 하나 이상의 태그로 태그가 지정된 콘텐츠를 검색합니다. 먼저 제목에서 이 키워드가 포함된 태그를 검색한 다음, 이 키워드가 태그가 지정된 항목으로만 결과를 제한합니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#Properties-1}

* **`tagsearch`** - 태그 제목에서 검색할 키워드
* **`property`** - 고려할 속성(또는 속성에 대한 상대 경로)(기본값) `cq:tags`)
* **`lang`** - 현지화된 특정 태그 제목에서만 검색(예: `de`)
* **`all`** - 전체 태그 전체 텍스트, 즉 모든 제목, 설명 등을 검색하는 부울 값(보다 우선함) `lang`)

### 유형 {#type}

이 술어는 결과를 기본 노드 유형 또는 을 포함하여 특정 JCR 노드 유형으로 제한합니다. `mixin` 유형. 또한 해당 노드 유형의 하위 유형을 찾습니다. 저장소 검색 인덱스는 효율적인 실행을 위해 노드 유형을 포함해야 합니다.

패싯 추출을 지원하고 결과에 각 고유 유형에 대한 버킷을 제공합니다.

#### 속성 {#Properties-2}

* **`type`** - 노드 유형 또는 `mixin` 검색할 이름(예: ) `cq:Page`
