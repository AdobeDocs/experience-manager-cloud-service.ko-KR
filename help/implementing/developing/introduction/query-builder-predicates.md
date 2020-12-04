---
title: Query Builder 설명 참조
description: 쿼리 빌더 API에 대한 설명 참조입니다.
translation-type: tm+mt
source-git-commit: 90b635cb31af910e08bdee7925cec0c7beb05318
workflow-type: tm+mt
source-wordcount: '2221'
ht-degree: 2%

---


# Query Builder 설명 참조 {#query-builder-predicate-reference}

## 일반 {#general}

### 루트 {#root}

루트 설명 그룹입니다. 그룹의 모든 기능을 지원하고 전역 쿼리 매개 변수를 설정할 수 있습니다.

&quot;root&quot;라는 이름은 쿼리에서 사용되지 않으며 암시적입니다.

#### 속성 {#properties-18}

* **`p.offset`** - 결과 페이지의 시작을 나타내는 숫자(즉, 건너뛸 항목 수)
* **`p.limit`** - 페이지 크기를 나타내는 숫자
* **`p.guessTotal`** - 권장:비용이 많이 들 수 있는 전체 결과 합계를 계산하지 마십시오.최대 계산 총계를 나타내는 숫자(예: 1000, 러프 크기 및 더 작은 결과를 위한 정확한 숫자에 대한 사용자 충분한 피드백을 제공하는 숫자) 또는 필요한 최소  `true`   `p.offset` +  `p.limit`
* **`p.excerpt`** - 로  `true`설정하면 결과에 전체 텍스트 발췌문을 포함할 수 있습니다.
* **`p.hits`** - (JSON 서블릿에만 해당) 다음과 같은 표준 히트(ResultHitWriter 서비스를 통해 확장 가능)를 사용하여 히트가 JSON으로 작성되는 방식을 선택합니다.
   * **`simple`** - 최소 항목 `path`,  `title`,  `lastmodified` `excerpt` (설정된 경우)
   * **`full`** - 히트 경로를  `jcr:path` 나타내는 노드의 JSON 렌더링 처리:기본적으로 노드의 직접 속성을 나열하고, 0을 의미하는  `p.nodedepth=N`전체 무한 하위 트리를 포함하는 더 깊은 트리를 포함합니다.지정된 결과 항목 `p.acls=true` 에 현재 세션의 JCR 권한을 포함하는 추가(매핑: `create` =  `add_node`,  `modify` =  `set_property`,  `delete` =  `remove`)
   * **`selective`** - 에 지정된 속성만 `p.properties`으로, 상대 경로 목록 `+` 에서 공백 구분(URL에서 사용)상대 경로에 심도가  `>1` 있는 경우 하위 개체로 표시됩니다.특수  `jcr:path` 속성에는 히트의 경로가 포함됩니다

### 그룹 {#group}

이 조건자는 중첩된 조건을 작성할 수 있습니다. 그룹에는 중첩된 그룹이 포함될 수 있습니다. 쿼리 빌더 쿼리의 모든 항목은 `p.or` 및 `p.not` 매개 변수를 가질 수 있는 루트 그룹에 암시적으로 포함됩니다.

다음은 값에 대해 두 속성 중 하나를 일치시키는 예입니다.

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

개념적으로는 `(1_property` OR `2_property)`입니다.

중첩 그룹의 예는 다음과 같습니다.

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

이 항목은 `/content/wknd/ch/de`의 페이지 내에서 또는 `/content/dam/wknd`의 자산에서 **Management**&#x200B;이라는 용어를 검색합니다.

개념적으로는 `fulltext AND ( (path AND type) OR (path AND type) )`입니다. 이러한 OR 조인은 성능상의 이유로 좋은 색인이 필요합니다.

#### 속성 {#properties-6}

* **`p.or`** - 로 설정된 경우 그룹의  `true`하나의 술자만 일치해야 합니다. 기본값은 `false`입니다. 즉, 모든 항목이 일치해야 합니다.
* **`p.not`** - 로 설정하면  `true`그룹이 무효화됩니다(기본값  `false`).
* **`<predicate>`** - 중첩 설명 추가
* **`N_<predicate>`** - 다음과 같은 여러 중첩 예측  `1_property, 2_property, ...`

### orderby {#orderby}

이 조건자는 결과를 정렬할 수 있습니다. 여러 속성별로 순서가 필요한 경우 이 술어는 숫자 접두어(예: `1_orderby=first`, `2_oderby=second`)를 사용하여 여러 번 추가해야 합니다.

#### 속성 {#properties-13}

* **`orderby`** - JCR 속성 이름(예: 행간 @ `@jcr:lastModified` 나  `@jcr:content/jcr:title`또는 쿼리의 다른 설명(예: 정렬 기준) `2_property`으로 표시됨
* **`sort`** - 정렬 방향, 내림차순 또는 오름차순 `desc` 에  `asc` 대해(기본값)
* **`case`** - if set to  `ignore` make sorting case insensitive, means  `a` comes before  `B`비어 있거나 비워 둘 경우, 정렬은 대/소문자를 구분하며, 이것은  `B` 앞에 오는  `a`

## {#predicates} 예측

### boolproperty {#boolproperty}

이 술어는 JCR 부울 속성에 일치합니다. `true` 및 `false` 값만 허용됩니다. `false`의 경우 속성에 `false` 값이 있거나 없는 경우 일치합니다. 활성화되었을 때만 설정되는 부울 플래그를 확인하는 데 유용합니다.

상속된 `operation` 매개 변수는 의미가 없습니다.

이 술어는 패싯 추출을 지원하고 기존 속성에만 해당하는 각 `true` 또는 `false` 값에 대한 버킷을 제공합니다.

#### 속성 {#properties}

* **`boolproperty`** - 속성에 대한 상대 경로(예:  `myFeatureEnabled` 또는  `jcr:content/myFeatureEnabled`
* **`value`** - 속성을 확인할 값  `true` 또는  `false`

### contentfragment {#contentfragment}

이 조건자는 결과를 컨텐츠 조각으로 제한합니다.

* 필터링을 지원하지 않습니다.
* 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-1}

* **`contentfragment`** - 컨텐츠 조각을 확인하는 데 모든 값과 함께 사용할 수 있습니다.

### `dateComparison` {#datecomparison}

이 술어는 두 JCR 날짜 속성을 서로 비교합니다. 같거나 불평등한지, 크거나 같은지 테스트할 수 있습니다.

이것은 필터링 전용 조건자이며 검색 색인을 활용할 수 없습니다.

#### 속성 {#properties-2}

* **`property1`** - 첫 번째 날짜 속성에 대한 경로
* **`property2`** - 두 번째 날짜 속성에 대한 경로
* **`operation`**
   * `=` 정확히 일치(기본값)
   * `!=` 불평등 비교
   * `>` 보다  `property1` 큰  `property2`
   * `>=` 을  `property1` 크거나 같음  `property2`

### daterange {#daterange}

이 술어는 날짜/시간 간격에 대해 JCR 날짜 속성과 일치합니다. ISO8601을 사용합니다
날짜 및 시간에 대한 형식(`YYYY-MM-DDTHH:mm:ss.SSSZ`)을 지정하고 `YYYY-MM-DD` 등의 부분 표현을 허용합니다. 또는 타임스탬프를 POSIX 시간으로 제공할 수 있습니다.

지정된 날짜보다 최신 또는 오래된 타임스탬프, 두 개의 타임스탬프 사이의 항목을 찾을 수 있으며, 포함 및 열기 간격 간을 선택할 수도 있습니다.

패싯 추출을 지원하고 버킷 `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` 및 `earlier than last year`을 제공합니다.

필터링을 지원하지 않습니다.

#### 속성 {#properties-3}

* **`property`** - 속성에 대한 상대  `DATE` 경로(예:  `jcr:lastModified`
* **`lowerBound`** - check 속성을 확인할 날짜가 낮은 경우  `2014-10-01`
* **`lowerOperation`** -  `>` (최신)  `>=` 또는 (이후))은 에  `lowerBound`적용됩니다. 기본값은 입니다.`>`
* **`upperBound`** - check 속성 위에  `2014-10-01T12:15:00`
* **`upperOperation`** -  `<` (이전)  `<=` 또는 (이상))은 에  `upperBound`적용됩니다. 기본값은 입니다.`<`
* **`timeZone`** - ISO-8601 날짜 문자열로 제공되지 않을 때 사용할 표준 시간대의 ID. 기본값은 시스템의 기본 표준 시간대입니다.

### excludepaths {#excludepaths}

이 조건자는 경로가 정규 표현식과 일치하는 결과에서 노드를 제외합니다.

이것은 필터링 전용 조건자이며 검색 색인을 활용할 수 없습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-4}

* **`excludepaths`** - 결과 경로에 대해 정규 표현식이 일치하며 결과에서 일치하는 표현식은 제외합니다.

### fulltext {#fulltext}

이 술어는 전체 텍스트 색인에서 용어를 검색합니다.

필터링을 지원하지 않습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-5}

* **`fulltext`** - 전체 텍스트 검색어
* **`relPath`** - 속성 또는 하위 노드에서 검색할 상대 경로입니다. 이 속성은 선택 사항입니다.

### hasPermission {#haspermission}

이 조건자는 현재 세션에 지정된 [JCR 권한이 있는 항목으로 결과를 제한합니다.](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

이것은 필터링 전용 조건자이며 검색 색인을 활용할 수 없습니다. 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-7}

* **`hasPermission`** - 현재 사용자 세션이 해당 노드에 대해 ALL이 보유해야 하는 쉼표로 구분된 JCR 권한예를 들어,  `jcr:write`  `jcr:modifyAccessControl`

### 언어 {#language}

이 술어는 특정 언어로 AEM 페이지를 찾습니다. 페이지 언어 속성과 최상위 사이트 구조의 언어 또는 로케일을 포함하는 페이지 경로를 모두 봅니다.

이것은 필터링 전용 조건자이며 검색 색인을 활용할 수 없습니다.

패싯 추출을 지원하고 각 고유 언어 코드에 대한 버킷을 제공합니다.

#### 속성 {#properties-8}

* **`language`** - ISO 언어 코드(예:  `de`

### mainasset {#mainasset}

이 술어는 노드가 하위 자산이 아닌 DAM 기본 자산인지 확인합니다. 이것은 기본적으로 하위 자산 노드 내에 없는 모든 노드입니다. 이는 `dam:Asset` 노드 유형을 확인하지 않습니다. 이 술어를 사용하려면 `mainasset=true` 또는 `mainasset=false`을 설정하기만 하면 됩니다. 더 이상 속성이 없습니다.

이것은 필터링 전용 조건자이며 검색 색인을 활용할 수 없습니다.

패싯 추출을 지원하고 주 및 하위 자산에 대해 두 개의 버킷을 제공합니다.

#### 속성 {#properties-9}

* **`mainasset`** - boolean, 기본  `true` 자산에  `false` 대해, 하위 자산에 대해

### memberOf {#memberof}

이 조건자는 특정 [sling 리소스 컬렉션](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html)의 멤버인 항목을 찾습니다.

이것은 필터링 전용 조건자이며 검색 색인을 활용할 수 없습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-10}

* **`memberOf`** - Sling 리소스 컬렉션 경로

### nodename {#nodename}

이 술어는 JCR 노드 이름에 일치합니다.

패싯 추출을 지원하고 각 고유한 노드 이름(파일 이름)에 대한 버킷을 제공합니다.

#### 속성 {#properties-11}

* **`nodename`** - 와일드카드를 허용하는 노드 이름 패턴: `*` = any or no char,  `?` = any char,  `[abc]` = only chars

### 만료되지 않음 {#notexpired}

이 조건자는 JCR 날짜 속성이 현재 서버 시간보다 크거나 같은지 확인하여 항목을 일치시킵니다. 이 값을 사용하여 `expiresAt` 값을 확인하고 아직 만료되지 않았거나(`notexpired=true`) 이미 만료된 값(`notexpired=false`)만 제한할 수 있습니다.

필터링을 지원하지 않습니다.

또한 [`daterange`](#daterange) 조건자와 동일한 방식으로 패싯 추출을 지원합니다.

#### 속성 {#properties-12}

* **`notexpired`** - boolean, 아직  `true` 만료되지 않은 경우(미래의 날짜 또는 같음), 만료된  `false` 날짜(지난 날짜)(필수)
* **`property`** - 확인할  `DATE` 속성의 상대 경로(필수)

### 경로 {#path}

이 술어는 지정된 경로 내에서 검색됩니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-14}

* **`path`** - 경로 패턴을 정의합니다.
   * `exact` 속성에 따라 전체 하위 트리가 일치하게 됩니다(예: xpath에 `//*` 추가). 단, 기본 경로가 포함되지 않습니다. 일치하는 정확한 경로만 포함되며 와일드카드(`*`)를 포함할 수 있습니다.
      * 기본값은 입니다.`true`
   * `self`속성 이 설정되면 기본 노드를 포함한 전체 하위 트리가 검색됩니다.
* **`exact`** - if  `exact` is `true`, exact path must match, but it can contains simple wildcard (`*`), that match names, but not  `/`;if it is  `false` (default) all descendants are included (optional)
* **`flat`** - 직접 하위만 검색(xpath `/*` 에 첨부)(true `exact` 가 아닌 경우에만 사용됨, 선택 사항)
* **`self`** - 하위 트리를 검색하지만 경로(와일드카드가 없음)로 지정된 기본 노드를 포함합니다.

### 속성 {#property}

이 술어는 JCR 속성과 해당 값에 일치합니다.

패싯 추출을 지원하고 결과의 각 고유 속성 값에 대한 버킷을 제공합니다.

#### 속성 {#properties-15}

* **`property`** - 속성에 대한 상대 경로(예:  `jcr:title`
* **`value`** - 속성을 확인할 값;는 JCR 속성 유형을 문자열 변환으로
* **`N_value`** -  `1_value`,  `2_value`...를 사용하여 여러 값 확인(기본적으로 조합되어,  `OR` 있는 경우 `AND`   `and=true` 포함)
* **`and`** - 여러 값 `true` 을 조합하도록 설정(`N_value`)  `AND`
* **`operation`**
   * `equals` 정확히 일치(기본값)
   * `unequals` 불평등 비교
   * `like` for using  `jcr:like` xpath function (optional)
   * `not` 일치하지 않는 경우(예: xpath `not(@prop)` 에서 값 매개 변수는 무시됩니다.)
   * `exists` 존재확인
      * `true` 속성이 있어야 합니다.
      * `false` is same as  `not` and is the default
* **`depth`** - 속성/상대 경로가 존재할 수 있는 와일드카드 수준 수(예: 확인하 `property=size depth=2` 는  `node/size` `node/*/size` 및  `node/*/*/size`선택)

### rangeproperty {#rangeproperty}

이 술어는 간격과 JCR 속성을 일치시킵니다. 이는 `LONG`, `DOUBLE` 및 `DECIMAL` 같은 선형 유형의 속성에 적용됩니다. `DATE`의 경우 최적화된 날짜 형식 입력이 있는 [`daterange`](#daterange) 조건자를 참조하십시오.

하한, 상한 또는 둘 다를 정의할 수 있습니다. 하한과 상한을 개별적으로 지정할 때 작업(예: 이보다 작거나 같음)을 지정할 수도 있습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-16}

* **`property`** - 속성 상대 경로
* **`lowerBound`** - 수표 속성 하한
* **`lowerOperation`** -  `>` (기본값)  `>=`또는  `lowerValue`
* **`upperBound`** - 확인 속성 상행
* **`upperOperation`** -  `<` (기본값)  `<=`또는  `lowerValue`
* **`decimal`** - checked 속성이 Decimal  `true` 유형인 경우

### relatativedaterange {#relativedaterange}

이 조건자는 현재 서버 시간을 기준으로 시간 오프셋을 사용하여 날짜/시간 간격에 대해 `JCR DATE` 속성을 일치시킵니다. 밀리 값 또는 `lowerBound` 부가질라 구문 `1s 2m 3h 4d 5w 6M 7y`(1초, 2분, 3시간, 4일, 5주, 6개월, 7년)을 사용하여 &lt;a0/> 및 `upperBound`을 지정할 수 있습니다. 현재 시간 이전의 음수 오프셋을 나타내는 접두사는 `-`입니다. `lowerBound` 또는 `upperBound`만 지정하는 경우 다른 하나는 기본적으로 `0`로 설정되며 현재 시간을 나타냅니다.

예:

* `upperBound=1h` (and no  `lowerBound`) select anything in next hour
* `lowerBound=-1d` (and no  `upperBound`) choose anything in last 24 hours
* `lowerBound=-6M` 지난 3개월에서 6개월 동안 어떤 것도  `upperBound=-3M` 선택할 수 있습니다.
* `lowerBound=-1500` 앞으로 1500밀리초에서 5500밀리초까지의 모든 것을  `upperBound=5500` 선택합니다.
* `lowerBound=1d` 모레 `upperBound=2d` 에 있는

윤년은 고려하지 않고 모든 달은 30일입니다.

필터링을 지원하지 않습니다.

또한 [`daterange`](#daterange) 조건자와 동일한 방식으로 패싯 추출을 지원합니다.

#### 속성 {#properties-17}

* **`upperBound`** - 현재 서버 시간을 기준으로 한 밀리초 또는  `1s 2m 3h 4d 5w 6M 7y` (1초, 2분, 3시간, 4일, 5주, 6개월, 7년)의 상한 날짜입니다. 음수 오프셋 `-` 에 사용합니다.
* **`lowerBound`** - 현재 서버 시간에 대한 밀리초 또는  `1s 2m 3h 4d 5w 6M 7y` (1초, 2분, 3시간, 4일, 5주, 6개월, 7년)의 낮은 날짜 바인딩된 날짜 `-` 가 현재 서버 시간에

### savedquery {#savedquery}

이 조건에는 현재 쿼리에 하위 그룹 조건자로 지속된 쿼리 빌더 쿼리의 모든 예측자가 포함됩니다.

추가 쿼리는 실행하지 않고 현재 쿼리를 확장합니다.

쿼리는 `QueryBuilder#storeQuery()`을 사용하여 프로그래밍 방식으로 유지할 수 있습니다. 형식은 다중 줄 `String` 속성이나 Java 속성 형식의 텍스트 파일로 쿼리를 포함하는 `nt:file` 노드일 수 있습니다.

저장된 쿼리의 예측자에 대한 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-19}

* **`savedquery`** - 저장된 쿼리 경로(`String` 속성 또는  `nt:file` 노드)

### 유사 {#similar}

이 술어는 JCR XPath의 `rep:similar()`을(를) 사용하는 유사 검색입니다.

필터링을 지원하지 않으며 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-20}

* **`similar`** - 유사한 노드를 찾을 노드의 절대 경로
* **`local`** - 하위 노드 또는 현재 노드 `.` 의 상대 경로(선택 사항, 기본값  `.`)

### tag {#tag}

이 술어는 태그 제목 경로를 지정하여 하나 이상의 태그가 지정된 컨텐츠를 검색합니다.

패싯 추출을 지원하고 현재 태그 제목 경로를 사용하여 각 고유한 태그에 대한 버킷을 제공합니다.

#### 속성 {#properties-21}

* **`tag`** - 찾을 태그 제목 경로(예:  `properties:orientation/landscape`
* **`N_value`** -  `1_value`,  `2_value`...를 사용하여 여러 태그 확인(기본적으로  `OR` 조합되어 있는 경우 `AND`   `and=true`)
* **`property`** - 확인할 속성(또는 속성의 상대 경로)(기본값  `cq:tags`

### tagid {#tagid}

이 술어는 태그 ID를 지정하여 하나 이상의 태그가 지정된 컨텐츠를 검색합니다.

패싯 추출을 지원하고 현재 태그 ID를 사용하여 각 고유한 태그에 대한 버킷을 제공합니다.

#### 속성 {#properties-22}

* **`tagid`** - 찾을 태그 ID(예:  `properties:orientation/landscape`
* **`N_value`** -  `1_value`,  `2_value`...를 사용하여 여러 태그 ID를 확인합니다(기본적으로 조합되어,  `OR` 있는 경우 `AND`   `and=true`와 함께 사용).
* **`property`** - 확인할 속성(또는 속성의 상대 경로)(기본값  `cq:tags`

### tagsearch {#tagsearch}

이 술어는 키워드를 지정하여 하나 이상의 태그가 지정된 컨텐츠를 검색합니다. 이렇게 하면 우선 제목에 이러한 키워드가 포함된 태그를 검색한 다음, 이 키워드가 있는 항목만 결과로 제한됩니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#Properties-1}

* **`tagsearch`** - 태그 제목에서 검색할 키워드
* **`property`** - 고려할 속성(또는 속성의 상대 경로)입니다(기본값  `cq:tags`
* **`lang`** - 특정 지역화된 태그 제목에서만 검색할 수 있습니다(예: `de`)
* **`all`** - 전체 태그 전체 텍스트, 즉 모든 제목, 설명 등을 검색하는 부울 값 (는 `lang`보다 우선함)

### 유형 {#type}

이 술어는 특정 JCR 노드 유형, 기본 노드 유형 또는 혼합 유형으로 결과를 제한합니다. 또한 해당 노드 유형의 하위 유형도 찾습니다. 저장소 검색 색인은 효율적인 실행을 위해 노드 유형을 포함해야 합니다.

패싯 추출을 지원하고 결과의 각 고유 유형에 대한 버킷을 제공합니다.

#### 속성 {#Properties-2}

* **`type`** - 검색할 노드 유형 또는 혼합 이름(예:  `cq:Page`
