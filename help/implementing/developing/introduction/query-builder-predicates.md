---
title: 쿼리 빌더 조건자 참조
description: AEM as a Cloud Service의 Query Builder API에 대한 설명 참조.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2270'
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
* **`p.guessTotal`** - 권장: 비용이 많이 들 수 있는 전체 결과 합계를 계산하지 마십시오. 계산할 최대 합계를 나타내는 숫자(예: 1000, 대략적인 크기에 대한 충분한 피드백과 더 작은 결과에 대한 정확한 숫자)입니다. 또는 `true`은(는) 필요한 최소 `p.offset` + `p.limit`까지만 계산합니다.
* **`p.excerpt`** - `true`(으)로 설정된 경우 결과에 전체 텍스트 발췌를 포함하십시오.
* **`p.indexTag`** - 설정하면 쿼리에 색인 태그 옵션이 포함됩니다([쿼리 옵션 색인 태그](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-option-index-tag) 참조).
* **`p.facetStrategy`** - `oak`(으)로 설정하면 Query Builder가 패싯 추출을 Oak에 위임합니다([패싯](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#facets) 참조).
* **`p.hits`** - (JSON 서블릿에만 해당) 히트가 JSON으로 기록되는 방식을 선택합니다(ResultHitWriter 서비스를 통해 확장 가능).
   * **`simple`** - `path`, `title`, `lastmodified`, `excerpt`과(와) 같은 최소 항목(설정된 경우)
   * **`full`** - 노드의 sling JSON 렌더링(`jcr:path`은(는) 히트의 경로를 나타냅니다. 기본적으로 은(는) 노드의 직접 속성만 나열하며 `p.nodedepth=N`이(가) 있는 더 깊은 트리를 포함합니다. 0은(는) 전체 무한 하위 트리를 의미합니다. 지정된 결과 항목에 현재 세션의 JCR 권한을 포함하려면 `p.acls=true`을(를) 추가하십시오(매핑: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).
   * **`selective`** - `p.properties`에 지정된 속성만 상대 경로의 공백으로 구분된 속성(URL에서 `+` 사용) 목록입니다. 상대 경로에 `>1` 깊이가 있으면 이러한 속성은 자식 개체로 표시됩니다. 특수 `jcr:path` 속성에 히트의 경로가 포함됩니다.

### 그룹 {#group}

이 술어를 사용하여 중첩된 조건을 작성할 수 있습니다. 그룹은 중첩 그룹을 포함할 수 있습니다. Query Builder 쿼리의 모든 항목은 암시적으로 루트 그룹에 있으며, 여기에는 `p.or` 및 `p.not` 매개 변수도 있을 수 있습니다.

다음은 값에 대해 두 속성 중 하나를 일치시키는 예입니다.

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

개념상 `(1_property` 또는 `2_property)`입니다.

중첩 그룹의 예는 다음과 같습니다.

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

`/content/wknd/ch/de`의 페이지 또는 `/content/dam/wknd`의 자산에서 **관리**&#x200B;라는 용어를 검색합니다.

개념상 `fulltext AND ( (path AND type) OR (path AND type) )`입니다. 이러한 OR 조인은 성능상의 이유로 좋은 색인이 필요합니다.

#### 속성 {#properties-6}

* **`p.or`** - `true`(으)로 설정된 경우 그룹의 한 조건자만 일치해야 합니다. 기본값은 `false`입니다. 즉, 모두 일치해야 합니다.
* **`p.not`** - `true`(으)로 설정된 경우 그룹을 부정합니다(기본값: `false`).
* **`<predicate>`** - 중첩된 조건자 추가
* **`N_<predicate>`** - `1_property, 2_property, ...`과(와) 같이 중첩된 술어를 동시에 여러 개 추가합니다.

### orderby {#orderby}

이 술어를 사용하면 결과를 정렬할 수 있습니다. 여러 속성별 순서 지정이 필요한 경우 숫자 접두사를 사용하여 이 조건자를 여러 번 추가해야 합니다(예: `1_orderby=first`, `2_oderby=second`).

#### 속성 {#properties-13}

* **`orderby`** - `@jcr:lastModified` 또는 `@jcr:content/jcr:title`과(와) 같은 선행 @으로 표시된 JCR 속성 이름이나 `2_property`과(와) 같은 쿼리의 정렬할 다른 조건자
* **`sort`** - 정렬 방향, 내림차순의 경우 `desc`, 오름차순의 경우 `asc`(기본값)
* **`case`** - `ignore`(으)로 설정하면 정렬 대소문자를 구분하지 않습니다. 즉, `a`이(가) `B` 앞에 옵니다. 비어 있거나 누락된 경우 정렬은 대소문자를 구분하며, `B`이(가) `a` 앞에 옵니다.

## 술어 {#predicates}

### 부울 속성 {#boolproperty}

이 술어는 JCR 부울 속성에서 일치합니다. `true` 및 `false` 값만 허용합니다. 값이 `false`이면 속성에 값이 `false`인지 또는 값이 전혀 없는 경우 일치합니다. 이 술어는 활성화된 경우에만 설정되는 부울 플래그를 확인하는 데 유용합니다.

상속된 `operation` 매개 변수는 의미가 없습니다.

이 조건자는 패싯 추출을 지원하고 각 `true` 또는 `false` 값에 대한 버킷을 제공하지만 기존 속성에 대해서만 제공합니다.

#### 속성 {#properties}

* **`boolproperty`** - 속성에 대한 상대 경로(예: `myFeatureEnabled` 또는 `jcr:content/myFeatureEnabled`)
* **`value`** - `true` 또는 `false`에 대한 속성을 확인할 값

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
   * 정확히 일치시키기 위한 `=`(기본값)
   * 같지 않음 비교에 대한 `!=`
   * `property1`의 `>`이(가) `property2`보다 큼
   * `property1`의 `>=`이(가) `property2`보다 크거나 같음

### 다터랑주 {#daterange}

이 술어는 날짜/시간 간격에 대해 JCR 날짜 속성을 일치시킵니다. ISO8601 사용
날짜 및 시간 형식(`YYYY-MM-DDTHH:mm:ss.SSSZ`)을 지정하고 `YYYY-MM-DD`과 같은 부분 표현도 허용합니다. 또는 타임스탬프를 POSIX 시간으로 제공할 수 있습니다.

두 타임스탬프 사이에 있는 모든 항목, 지정된 날짜보다 최신 항목 또는 오래된 항목을 찾을 수 있으며 포함 간격과 열기 간격 사이에서 선택할 수도 있습니다.

패싯 추출을 지원하고 버킷 `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` 및 `earlier than last year`을(를) 제공합니다.

필터링을 지원하지 않습니다.

#### 속성 {#properties-3}

* **`property`** - `DATE` 속성에 대한 상대 경로(예: `jcr:lastModified`)
* **`lowerBound`** - `2014-10-01`과(와) 같은 속성을 확인하기 위해 바인딩된 하한 날짜
* **`lowerOperation`** - `>`(최신) 또는 `>=`(다음 이상)이 `lowerBound`에 적용됩니다. 기본값은 `>`입니다.
* **`upperBound`** - `2014-10-01T12:15:00`과(와) 같은 속성을 확인할 상한입니다.
* **`upperOperation`** - `<`(이전) 또는 `<=`(이전)이(가) `upperBound`에 적용됩니다. 기본값은 `<`입니다.
* **`timeZone`** - ISO-8601 날짜 문자열로 제공되지 않을 때 사용할 표준 시간대의 ID입니다. 기본값은 시스템의 기본 시간대입니다.

### excludepaths {#excludepaths}

이 조건자는 해당 경로가 정규 표현식과 일치하는 결과에서 노드를 제외합니다.

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-4}

* **`excludepaths`** - 결과 경로에 대해 일치하는 정규 표현식이며, 결과에서 일치하는 정규 표현식은 제외합니다.

### 전체 텍스트 {#fulltext}

전체 텍스트 색인에서 용어를 검색합니다.

필터링을 지원하지 않습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-5}

* **`fulltext`** - 전체 텍스트 검색어
* **`relPath`** - 속성 또는 하위 노드에서 검색할 상대 경로입니다. 이 속성은 선택 사항입니다.

### hasPermission {#haspermission}

이 조건자는 현재 세션에 지정된 [JCR 권한이 있는 항목으로 결과를 제한합니다.](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다. 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-7}

* **`hasPermission`** - 해당 노드에 대해 현재 사용자 세션에 있어야 하는 쉼표로 구분된 모든 JCR 권한. 예: `jcr:write`, `jcr:modifyAccessControl`

### 언어 {#language}

이 술어는 특정 언어로 된 AEM 페이지를 찾습니다. 페이지 언어 속성과 종종 최상위 사이트 구조에 언어 또는 로케일을 포함하는 페이지 경로를 모두 살펴봅니다.

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

패싯 추출을 지원하고 각 고유 언어 코드에 대한 버킷을 제공합니다.

#### 속성 {#properties-8}

* **`language`** - ISO 언어 코드(예: `de`)

### 주요 자산 {#mainasset}

이 조건자는 노드가 DAM 주 자산이고 하위 자산이 아닌지 확인합니다. 이는 기본적으로 하위 에셋 노드 내에 있지 않은 모든 노드입니다. `dam:Asset` 노드 형식을 확인하지 않습니다. 이 조건자를 사용하려면 `mainasset=true` 또는 `mainasset=false`을(를) 설정하십시오. 추가 속성이 없습니다.

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

Facet 추출을 지원하고 기본 및 하위 에셋에 대해 두 개의 버킷을 제공합니다.

#### 속성 {#properties-9}

* **`mainasset`** - 부울, 기본 자산의 경우 `true`, 하위 자산의 경우 `false`

### memberOf {#memberof}

이 조건자는 특정 [sling 리소스 컬렉션](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/resource/collection/ResourceCollection.html)에 속하는 항목을 찾습니다.

필터링 전용 조건자이며 검색 색인을 사용할 수 없습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-10}

* **`memberOf`** - Sling 리소스 컬렉션의 경로

### nodename {#nodename}

이 술어는 JCR 노드 이름에서 일치합니다.

패싯 추출을 지원하고 각 고유한 노드 이름(파일 이름)에 대한 버킷을 제공합니다.

#### 속성 {#properties-11}

* **`nodename`** - 와일드카드를 허용하는 노드 이름 패턴: `*` = any or no char, `?` = any char, `[abc]` = 대괄호 안의 문자만

### 가공되지 않음 {#notexpired}

이 술어는 JCR 날짜 속성이 현재 서버 시간보다 크거나 같은지 확인하여 항목을 일치시킵니다. `expiresAt` 값을 확인하는 데 사용할 수 있으며, 아직 만료되지 않았거나(`notexpired=true`) 이미 만료된 값(`notexpired=false`)으로만 결과를 제한합니다.

필터링을 지원하지 않습니다.

[`daterange`](#daterange) 조건자와 동일한 방식으로 패싯 추출을 지원합니다.

#### 속성 {#properties-12}

* **`notexpired`** - 부울, 아직 만료되지 않은 경우 `true`(미래 또는 같은 날짜), 만료된 경우 `false`(과거 날짜)(필수)
* **`property`** - 확인할 `DATE` 속성의 상대 경로(필수)

### 경로 {#path}

이 조건자는 주어진 경로 내에서 검색합니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-14}

* **`path`** - 경로 패턴을 정의합니다.
   * `exact` 속성에 따라 전체 하위 트리가 일치하거나(예: xpath에 `//*`을(를) 추가하지만 기본 경로는 포함하지 않음) 와일드카드(`*`)를 포함할 수 있는 정확한 경로만 일치합니다.
      * 기본값은 `true`입니다.
&lt;!—   * `self`속성이 설정되면 기본 노드를 포함한 전체 하위 트리가 검색됩니다.—>
* **`exact`** - `exact`이(가) `true`인 경우 정확한 경로가 일치해야 하지만 이름에 일치하는 단순 와일드카드(`*`)를 포함할 수 있지만 `/`은(는) 아닙니다. `false`(기본값)인 경우 모든 하위 항목이 포함됩니다(선택 사항).
* **`flat`** - 직접 하위만 검색합니다(xpath에 `/*`을(를) 추가합니다. `exact`이(가) true가 아닌 경우에만 사용됨, 선택 사항).
* **`self`** - 하위 트리를 검색하지만 경로로 지정된 기본 노드를 포함합니다(와일드카드 없음).
   * *중요 참고*: 쿼리 빌더의 현재 구현에서 `self` 속성으로 문제가 확인되었으며 쿼리에 이 속성을 사용하면 올바른 검색 결과가 생성되지 않을 수 있습니다. `self` 속성의 현재 구현을 변경하면 해당 속성에 의존하는 기존 응용 프로그램이 손상될 수 있으므로 변경할 수도 없습니다. 이 기능 때문에 `self` 속성은 이제 사용되지 않습니다. 사용하지 않는 것이 좋습니다.

### 속성 {#property}

이 술어는 JCR 속성 및 해당 값에 대해 일치합니다.

패싯 추출을 지원하고 결과에 각 고유 속성 값에 대한 버킷을 제공합니다.

#### 속성 {#properties-15}

* **`property`** - 속성에 대한 상대 경로(예: `jcr:title`).
* **`value`** - 속성을 확인할 값입니다. 문자열 변환에 대한 JCR 속성 형식을 따릅니다.
* **`N_value`** - `1_value`, `2_value`, ...을(를) 사용하여 여러 값을 확인합니다(기본적으로 `OR`과(와) 결합, `and=true`인 경우 `AND` 포함).
* **`and`** - 여러 값(`N_value`)을 `AND`과(와) 결합하려면 `true`(으)로 설정합니다.
* **`operation`**
   * `equals`을(를) 정확하게 일치시킵니다(기본값).
   * `unequals`(같지 않음 비교)
   * `jcr:like` xpath 함수를 사용하는 경우 `like`(선택 사항).
   * 일치 항목 없는 `not`(예: xpath의 `not(@prop)`, 값 매개 변수는 무시됨).
   * `exists`의 존재 여부를 확인합니다.
      * `true` 속성이 있어야 합니다.
      * `false`은(는) `not`과(와) 동일하며 기본값입니다.
* **`depth`** - 속성/상대 경로가 존재할 수 있는 와일드카드 수준의 수입니다(예: `property=size depth=2`개의 확인 `node/size`, `node/*/size` 및 `node/*/*/size`).

### rangeproperty {#rangeproperty}

이 술어는 간격에 대해 JCR 속성과 일치합니다. `LONG`, `DOUBLE` 및 `DECIMAL`과(와) 같은 선형 형식의 속성에 적용됩니다. `DATE`에 대해 날짜 형식 입력을 최적화한 [`daterange`](#daterange) 조건자를 참조하십시오.

하한, 상한 또는 둘 다를 정의할 수 있습니다. 작업(예: 보다 작거나 같음)은 하한과 상한에 대해서도 개별적으로 지정할 수 있습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-16}

* **`property`** - 속성에 대한 상대 경로
* **`lowerBound`** - 검사 속성의 하한
* **`lowerOperation`** - `>`(기본값) 또는 `>=`이(가) `lowerValue`에 적용됩니다.
* **`upperBound`** - 검사 속성의 상한입니다.
* **`upperOperation`** - `<`(기본값) 또는 `<=`이(가) `lowerValue`에 적용됩니다.
* 확인된 속성이 Decimal 형식인 경우 **`decimal`** - `true`

### 상대 날짜 범위 {#relativedaterange}

이 조건자는 현재 서버 시간에 상대적인 시간 오프셋을 사용하여 날짜/시간 간격에 대해 `JCR DATE` 속성을 일치시킵니다. 밀리초 값 또는 Bugzilla 구문 `1s 2m 3h 4d 5w 6M 7y`(1초, 2분, 3시간, 4일, 5주, 6개월, 7년)을 사용하여 `lowerBound` 및 `upperBound`을(를) 지정할 수 있습니다. 현재 시간 이전의 음수 오프셋을 나타내려면 `-`을(를) 접두사로 사용하십시오. `lowerBound` 또는 `upperBound`만 지정하면 나머지 하나는 기본적으로 현재 시간을 나타내는 `0`로 설정됩니다.

예:

* `upperBound=1h`(및 `lowerBound` 없음)이(가) 다음 시간 내에 모든 항목을 선택합니다.
* `lowerBound=-1d`(및 `upperBound` 없음)이(가) 지난 24시간 동안 아무 항목도 선택하지 않았습니다.
* `lowerBound=-6M` 및 `upperBound=-3M`이(가) 지난 3~6개월 동안 선택한 항목 없음
* `lowerBound=-1500` 및 `upperBound=5500`은(는) 1,500밀리초에서 5,500밀리초 사이의 모든 항목을 선택합니다.
* `lowerBound=1d` 및 `upperBound=2d`이(가) 모레 아무 항목이나 선택합니다.

윤년은 고려하지 않고 모든 달은 30일입니다.

필터링을 지원하지 않습니다.

[`daterange`](#daterange) 조건자와 동일한 방식으로 패싯 추출을 지원합니다.

#### 속성 {#properties-17}

* **`upperBound`** - 현재 서버 시간을 기준으로 하여 밀리초 또는 `1s 2m 3h 4d 5w 6M 7y`(1초, 2분, 3시간, 4일, 5주, 6개월, 7년) 단위로 바인딩된 상한값입니다. 음수 오프셋에 대해서는 `-`을(를) 사용하십시오.
* **`lowerBound`** - 현재 서버 시간을 기준으로 `1s 2m 3h 4d 5w 6M 7y`(1초, 2분, 3시간, 4일, 5주, 6개월, 7년) 또는 밀리초로 설정된 더 낮은 날짜입니다. 음수 오프셋은 `-`을(를) 사용하십시오.

### savedquery {#savedquery}

이 조건자에는 지속 쿼리 빌더 쿼리의 모든 조건자가 현재 쿼리에 하위 그룹 조건자로 포함됩니다.

추가 쿼리를 실행하지 않고 현재 쿼리를 확장합니다.

쿼리는 `QueryBuilder#storeQuery()`을(를) 사용하여 프로그래밍 방식으로 유지할 수 있습니다. 형식은 여러 줄 `String` 속성이거나 Java™ 속성 형식의 텍스트 파일로 쿼리를 포함하는 `nt:file` 노드일 수 있습니다.

저장된 쿼리의 술어에 대한 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-19}

* **`savedquery`** - 저장된 쿼리의 경로(`String` 속성 또는 `nt:file` 노드)

### 유사 {#similar}

이 조건자는 JCR XPath의 `rep:similar()`을(를) 사용하는 유사성 검색입니다.

필터링을 지원하지 않으며 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-20}

* **`similar`** - 유사한 노드를 찾을 노드의 절대 경로
* **`local`** - 현재 노드의 하위 노드 또는 `.`에 대한 상대 경로(선택 사항, 기본값은 `.`)

### 태그 {#tag}

이 조건자는 태그 제목 경로를 지정하여 하나 이상의 태그로 태그가 지정된 컨텐츠를 검색합니다.

패싯 추출을 지원하고 현재 태그 제목 경로를 사용하여 각 고유 태그에 대한 버킷을 제공합니다.

#### 속성 {#properties-21}

* **`tag`** - 찾을 태그 제목 경로(예: `properties:orientation/landscape`)
* **`N_value`** - `1_value`, `2_value`, ...을(를) 사용하여 여러 태그(기본적으로 `OR`과(와) 결합됨, `and=true`인 경우 `AND` 포함) 확인
* **`property`** - 확인할 속성(또는 속성에 대한 상대 경로)(기본값 `cq:tags`)

### 태그 {#tagid}

이 조건자는 태그 ID를 지정하여 하나 이상의 태그로 태그가 지정된 컨텐츠를 검색합니다.

패싯 추출을 지원하고 현재 태그 ID를 사용하여 각 고유 태그에 대한 버킷을 제공합니다.

#### 속성 {#properties-22}

* **`tagid`** - 찾을 태그 ID(예: `properties:orientation/landscape`)
* **`N_value`** - `1_value`, `2_value`, ...을(를) 사용하여 여러 태그 ID(기본적으로 `OR`과(와) 결합됨, `and=true`인 경우 `AND` 포함) 확인
* **`property`** - 확인할 속성(또는 속성에 대한 상대 경로)(기본값 `cq:tags`)

### tagsearch {#tagsearch}

이 조건자는 키워드를 지정하여 하나 이상의 태그로 태그가 지정된 콘텐츠를 검색합니다. 먼저 제목에서 이 키워드가 포함된 태그를 검색한 다음, 이 키워드가 태그가 지정된 항목으로만 결과를 제한합니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#Properties-1}

* **`tagsearch`** - 태그 제목에서 검색할 키워드
* **`property`** - 고려할 속성(또는 속성에 대한 상대 경로)(기본값 `cq:tags`)
* **`lang`** - 지역화된 특정 태그 제목에서만 검색합니다(예: `de`).
* **`all`** - 전체 태그 전체 텍스트, 즉 모든 제목, 설명 등을 검색하는 부울 값(`lang`보다 우선함)

### 유형 {#type}

이 조건자는 결과를 기본 노드 유형 또는 `mixin` 유형 모두인 특정 JCR 노드 유형으로 제한합니다. 또한 해당 노드 유형의 하위 유형을 찾습니다. 저장소 검색 인덱스는 효율적인 실행을 위해 노드 유형을 포함해야 합니다.

패싯 추출을 지원하고 결과에 각 고유 유형에 대한 버킷을 제공합니다.

#### 속성 {#Properties-2}

* **`type`** - 검색할 노드 유형 또는 `mixin` 이름(예: `cq:Page`)
