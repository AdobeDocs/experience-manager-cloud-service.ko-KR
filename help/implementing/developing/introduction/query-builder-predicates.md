---
title: Query Builder 설명 참조
description: Query Builder API에 대한 설명 참조입니다.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '2219'
ht-degree: 2%

---

# Query Builder 설명 참조 {#query-builder-predicate-reference}

## 일반 {#general}

### 루트 {#root}

루트 조건자 그룹입니다. 그룹의 모든 기능을 지원하고 전역 쿼리 매개 변수를 설정할 수 있도록 해줍니다.

&quot;root&quot;라는 이름은 쿼리에 사용되지 않고 암시적으로 사용됩니다.

#### 속성 {#properties-18}

* **`p.offset`** - 결과 페이지의 시작을 나타내는 숫자(즉, 건너뛸 항목 수)
* **`p.limit`** - 페이지 크기를 나타내는 숫자
* **`p.guessTotal`** - 권장:비용이 많이 들 수 있는 전체 결과 합계를 계산하지 마십시오.최대 계산할 최대 총계를 나타내는 숫자(예: 1000, 대략적인 크기와 더 작은 결과를 위한 정확한 숫자를 사용자에게 제공하는 숫자) 또는 필요한 최소값 `true` 의  `p.offset` +  `p.limit`
* **`p.excerpt`** - 로 설정하면  `true`결과에 전체 텍스트 발췌문을 포함합니다
* **`p.hits`** - (JSON 서블릿에 대해서만) 히트가 JSON으로 기록되는 방식(이러한 표준 방식(ResultHitWriter 서비스를 통해 확장 가능)을 선택합니다.
   * **`simple`** -  `path`,  `title`,  `lastmodified`,  `excerpt` (설정된 경우)과 같은 최소 항목
   * **`full`** - 히트의 경로를  `jcr:path` 나타내는 노드의 sling JSON 렌더링:기본적으로 노드의 직접 속성을 나열하고, 0은 전체 무한 하위 트리를 의미함 `p.nodedepth=N`과 함께 더 깊은 트리를 포함합니다.지정된 결과 항목 `p.acls=true` 에 현재 세션의 JCR 권한을 포함하도록 추가합니다(매핑: `create` =  `add_node`,  `modify`  =  `set_property`,  `delete`  =  `remove`)
   * **`selective`** - 상대 경로 목록 `p.properties`으로 구분된 공간(URL에서 사용) 목록인  `+` 에 지정된 속성만상대 경로에 깊이가  `>1` 있으면 자식 개체로 표시됩니다.특수  `jcr:path` 속성에는 히트의 경로가 포함됩니다

### 그룹 {#group}

이 조건에서는 중첩된 조건을 작성할 수 있습니다. 그룹에는 중첩된 그룹이 포함될 수 있습니다. Query Builder 쿼리의 모든 항목이 암시적으로 루트 그룹에 있습니다. 이 그룹은 `p.or` 및 `p.not` 매개 변수도 가질 수 있습니다.

다음은 값에 두 속성 중 하나를 일치시키는 예입니다.

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

개념적으로 `(1_property` 또는 `2_property)`입니다.

중첩 그룹의 예는 다음과 같습니다.

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

`/content/wknd/ch/de`의 페이지 내에서 또는 `/content/dam/wknd`의 자산에서 **Management**&#x200B;라는 용어를 검색합니다.

개념적으로는 `fulltext AND ( (path AND type) OR (path AND type) )`입니다. 이러한 OR 조인은 성능상의 이유로 적합한 인덱스가 필요합니다.

#### 속성 {#properties-6}

* **`p.or`** - 로  `true`설정하면 그룹의 술어가 하나만 일치해야 합니다. 기본값은 `false`입니다. 이것은 모두 일치해야 함을 의미합니다
* **`p.not`** - 로  `true`설정하면 그룹을 무효화합니다(기본값은  `false`).
* **`<predicate>`** - 중첩 설명 추가
* **`N_<predicate>`** - 과 같이 여러 중첩 설명을 동시에 추가합니다.  `1_property, 2_property, ...`

### orderby {#orderby}

이 조건에서는 결과를 정렬할 수 있습니다. 여러 속성으로 순서를 지정해야 하는 경우 `1_orderby=first`, `2_oderby=second` 등의 숫자 접두어를 사용하여 이 조건자를 여러 번 추가해야 합니다.

#### 속성 {#properties-13}

* **`orderby`** - 선행 @(예:  `@jcr:lastModified` 또는  `@jcr:content/jcr:title`)로 표시된 JCR 속성 이름 또는 정렬할 쿼리의 다른 설명(예:  `2_property`)으로 표시됩니다
* **`sort`** - 정렬 방향, 내림차순 또 `desc` 는 오름차순 `asc` 에 대해 정렬(기본값)
* **`case`** - 로 설정하면  `ignore` 대소문자를 구분하지 않게 됩니다. 이것은 앞에 오는  `a` 것을 의미합니다 `B`.비워 두거나 비워 둘 경우 정렬은 대/소문자를 구분합니다. 즉,  `B` 앞에 옵니다  `a`

## 설명 {#predicates}

### 부울 속성 {#boolproperty}

이 조건자는 JCR 부울 속성에서 일치합니다. `true` 및 `false` 값만 허용합니다. `false`의 경우, 속성에 `false` 값이 있거나 값이 전혀 없는 경우 일치합니다. 이 기능은 활성화되었을 때만 설정되는 부울 플래그를 확인하는 데 유용합니다.

상속된 `operation` 매개 변수는 의미가 없습니다.

이 조건부는 패싯 추출을 지원하고 각 `true` 또는 `false` 값에 대한 버킷을 제공하지만 기존 속성에만 제공합니다.

#### 속성 {#properties}

* **`boolproperty`** - 속성에 대한 상대 경로(예:  `myFeatureEnabled` 또는 )  `jcr:content/myFeatureEnabled`
* **`value`** - 또는 `true` 에 대한 속성을 확인할 값  `false`

### contentfragment {#contentfragment}

이 조건부는 결과를 컨텐츠 조각으로 제한합니다.

* 필터링을 지원하지 않습니다.
* 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-1}

* **`contentfragment`** - 값과 함께 사용하여 컨텐츠 조각을 확인할 수 있습니다.

### `dateComparison` {#datecomparison}

이 조건부는 두 JCR 날짜 속성을 서로 비교합니다. 같음, 같지 않음, 크거나 같음 여부를 테스트할 수 있습니다.

필터링 전용 조건이며 검색 색인을 활용할 수 없습니다.

#### 속성 {#properties-2}

* **`property1`** - 첫 번째 날짜 속성의 경로
* **`property2`** - 두 번째 날짜 속성의 경로
* **`operation`**
   * `=` 완전 일치(기본값)
   * `!=` 같지 않음 비교
   * `>` 보다  `property1` 큼  `property2`
   * `>=` 다음보다  `property1` 크거나 같음  `property2`

### daterange {#daterange}

이 조건자는 날짜/시간 간격에 대해 JCR 날짜 속성을 일치시킵니다. 여기서는 ISO8601을 사용합니다
날짜 및 시간 형식(`YYYY-MM-DDTHH:mm:ss.SSSZ`)을 설정하고 `YYYY-MM-DD` 등의 부분 표현을 사용할 수 있습니다. 또는 타임스탬프를 POSIX 시간으로 제공할 수 있습니다.

두 개의 타임스탬프(지정된 날짜보다 최신 또는 이전 항목) 사이의 항목을 찾고, 포함 및 열기 간격 중에서 선택할 수도 있습니다.

패싯 추출을 지원하고 버킷 `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` 및 `earlier than last year`를 제공합니다.

필터링을 지원하지 않습니다.

#### 속성 {#properties-3}

* **`property`** - 속성에 대한 상대  `DATE` 경로(예: )  `jcr:lastModified`
* **`lowerBound`** - 예를 들어 check 속성에 바인딩된 날짜가 낮은 경우  `2014-10-01`
* **`lowerOperation`** -  `>` (최신) 또는  `>=` (이상)이  `lowerBound`에 적용됩니다. 기본값은 입니다.`>`
* **`upperBound`** - 예를 들어 속성을 확인하도록 상한을 설정합니다.  `2014-10-01T12:15:00`
* **`upperOperation`** -  `<` (이전) 또는  `<=` (이상)이  `upperBound`에 적용됩니다. 기본값은 입니다.`<`
* **`timeZone`** - ISO-8601 날짜 문자열로 제공되지 않을 때 사용할 시간대 ID입니다. 기본값은 시스템의 기본 시간대입니다.

### 제외 경로 {#excludepaths}

이 조건부는 경로가 정규 표현식과 일치하는 결과에서 노드를 제외합니다.

필터링 전용 조건이며 검색 색인을 활용할 수 없습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-4}

* **`excludepaths`** - 결과 경로에 대해 일치하는 정규 표현식에서 결과에서 일치하는 항목을 제외합니다.

### 전체 텍스트 {#fulltext}

이 조건자는 전체 텍스트 색인에서 용어를 검색합니다.

필터링을 지원하지 않습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-5}

* **`fulltext`** - 전체 텍스트 검색어
* **`relPath`** - 속성 또는 하위 노드에서 검색할 상대 경로입니다. 이 속성은 선택 사항입니다.

### hasPermission {#haspermission}

이 조건에서는 현재 세션에 지정된 [JCR 권한이 있는 항목으로 결과를 제한합니다.](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

필터링 전용 조건이며 검색 색인을 활용할 수 없습니다. 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-7}

* **`hasPermission`** - 현재 사용자 세션이 해당 노드에 대해 모두 가져야 하는 쉼표로 구분된 JCR 권한예 `jcr:write`:  `jcr:modifyAccessControl`

### 언어 {#language}

이 조건자는 특정 언어로 AEM 페이지를 찾습니다. 여기서는 페이지 언어 속성과 페이지 경로 모두를 살펴봅니다. 페이지 경로는 최상위 사이트 구조의 언어나 로케일을 종종 포함합니다.

필터링 전용 조건이며 검색 색인을 활용할 수 없습니다.

패싯 추출을 지원하고 각 고유 언어 코드에 대한 버킷을 제공합니다.

#### 속성 {#properties-8}

* **`language`** - ISO 언어 코드, 예  `de`

### 유지 관리 {#mainasset}

이 조건부는 노드가 하위 자산이 아니라 DAM 주 자산인지 확인합니다. 이것은 기본적으로 하위 자산 노드 내에 없는 모든 노드입니다. 이 옵션은 `dam:Asset` 노드 유형을 확인하지 않습니다. 이 설명을 사용하려면 `mainasset=true` 또는 `mainasset=false`을 설정하기만 하면 됩니다. 더 이상 특성이 없습니다.

필터링 전용 조건이며 검색 색인을 활용할 수 없습니다.

패싯 추출을 지원하고 기본 및 하위 자산에 대해 두 개의 버킷을 제공합니다.

#### 속성 {#properties-9}

* **`mainasset`** - 부울,  `true` 기본 자산의  `false` 경우, 하위 자산의 경우

### memberOf {#memberof}

이 조건자는 특정 [sling 리소스 컬렉션](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/resource/collection/ResourceCollection.html)에 속하는 항목을 찾습니다.

필터링 전용 조건이며 검색 색인을 활용할 수 없습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-10}

* **`memberOf`** - Sling 리소스 컬렉션의 경로

### 노네임 {#nodename}

이 조건자는 JCR 노드 이름에서 일치합니다.

패싯 추출을 지원하고 각 고유한 노드 이름(파일 이름)에 대한 버킷을 제공합니다.

#### 속성 {#properties-11}

* **`nodename`** - 와일드카드가 가능한 노드 이름 패턴: `*` = any 또는 no char,  `?`  = any char,  `[abc]`  = only chars

### 만료되지 않음 {#notexpired}

이 조건자는 JCR 날짜 속성이 현재 서버 시간보다 크거나 같은지 확인하여 항목을 일치시킵니다. 이 값은 `expiresAt` 값을 확인하고 아직 만료되지 않았거나(`notexpired=true`) 이미 만료된 값(`notexpired=false`)만 제한하는 데 사용할 수 있습니다.

필터링을 지원하지 않습니다.

[`daterange`](#daterange) 조건자와 동일한 방식으로 패싯 추출을 지원합니다.

#### 속성 {#properties-12}

* **`notexpired`** - 부울, 아직  `true` 만료되지 않은 경우(미래의 날짜 또는  `false` 같은 날짜), 만료 날짜(과거 날짜)(필수)
* **`property`** - 확인할 속성의 상대  `DATE` 경로(필수)

### 경로 {#path}

이 조건부는 지정된 경로 내에서 검색합니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-14}

* **`path`** - 경로 패턴을 정의합니다.
   * `exact` 속성에 따라 전체 하위 트리가 일치하거나(xpath에 `//*` 추가 등과 같이, 기본 경로가 포함되지 않지만) 와일드카드(`*`)를 포함할 수 있는 정확한 경로 일치만 일치시킵니다.
      * 기본값은 입니다.`true`
   * `self`속성이 설정되면 기본 노드를 포함하는 전체 하위 트리가 검색됩니다.
* **`exact`** -  `exact` 가  `true`이면 정확한 경로가 일치해야 하지만, 단순 와일드카드(`*`), 해당 일치 이름( `/`)이 포함될 수 있지만,(기본값)  `false` 모든 하위 항목이 포함됩니다(선택 사항).
* **`flat`** - 직접 1차 하위 구성요소만 검색합니다(xpath `/*` 에 추가 등).  `exact` 이 true가 아닌 경우에만 사용됨, 선택 사항)
* **`self`** - 하위 트리를 검색하지만 경로(와일드카드 없음)로 제공된 기본 노드를 포함합니다.

### 속성 {#property}

이 조건자는 JCR 속성 및 해당 값에서 일치합니다.

패싯 추출을 지원하고 결과의 각 고유 속성 값에 대한 버킷을 제공합니다.

#### 속성 {#properties-15}

* **`property`** - 속성의 상대 경로(예:  `jcr:title`
* **`value`** - 속성을 확인하는 값입니다.는 JCR 속성 유형을 문자열 전환으로 따릅니다
* **`N_value`** -  `1_value`,  `2_value`, ...를 사용하여 여러 값(기본적으로 와 결합되어  `OR` 있는 경우)을 확인할 수  `AND` 있습니다 `and=true`.
* **`and`** - 여러 값( `true` )을 `N_value`와 결합하려면 로 설정합니다.  `AND`
* **`operation`**
   * `equals` 완전 일치(기본값)
   * `unequals` 같지 않음 비교
   * `like` xpath 함수 `jcr:like` 를 사용하기 위해(선택 사항)
   * `not` 일치하지 않는 경우(예: xpath `not(@prop)` 에서 값 매개 변수는 무시됩니다.)
   * `exists` 존재 확인
      * `true` 속성이 있어야 합니다.
      * `false` 은 과  `not` 동일하고 은 기본값입니다
* **`depth`** - 속성/상대 경로가 존재할 수 있는 와일드카드 레벨 수(예:  `property=size depth=2` 은  `node/size`및  `node/*/size`  `node/*/*/size`)입니다.

### rangeproperty {#rangeproperty}

이 조건자는 간격과 JCR 속성을 일치시킵니다. 이는 `LONG`, `DOUBLE` 및 `DECIMAL` 등의 선형 유형을 사용하는 속성에 적용됩니다. `DATE`에 대해서는 최적화된 날짜 형식 입력이 있는 [`daterange`](#daterange) 설명을 참조하십시오.

하행, 상행 또는 둘 다를 정의할 수 있습니다. 작업(예: 보다 작거나 같음)도 개별적으로 하한 및 상한 각각에 대해 지정할 수 있습니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-16}

* **`property`** - 속성의 상대 경로
* **`lowerBound`** - check 속성 하한값
* **`lowerOperation`** -  `>` (기본값) 또는  `>=`가 적용되는 경우  `lowerValue`
* **`upperBound`** - check 속성이 위에 추가됨
* **`upperOperation`** -  `<` (기본값) 또는  `<=`가 적용되는 경우  `lowerValue`
* **`decimal`** - 확인된  `true` 속성이 Decimal 형식인 경우

### relativedaterange {#relativedaterange}

이 조건자는 현재 서버 시간을 기준으로 시간 오프셋을 사용하여 날짜/시간 간격에 대해 `JCR DATE` 속성을 일치시킵니다. 밀리초 값 또는 Bugzilla 구문 `1s 2m 3h 4d 5w 6M 7y` (1초, 2분, 3시간, 4일, 5주, 6개월, 7년)을 사용하여 `lowerBound` 및 `upperBound`을 지정할 수 있습니다. 현재 시간 이전의 음수 오프셋을 나타내려면 `-` 접두사를 사용하십시오. `lowerBound` 또는 `upperBound`만 지정하는 경우 다른 하나는 기본적으로 현재 시간을 나타내는 `0`로 설정됩니다.

예:

* `upperBound=1h` (및 no  `lowerBound`)가 다음 시간 동안 아무 것도 선택하지 않습니다.
* `lowerBound=-1d` (및 no  `upperBound`)가 지난 24시간 동안 아무 것도 선택하지 않습니다.
* `lowerBound=-6M` 그리고  `upperBound=-3M` 지난 3~6개월 동안 어떤 것이든 선택합니다
* `lowerBound=-1500` 그리고  `upperBound=5500` 는 1500밀리초에서 5500밀리초 사이의 어떤 것이든 선택할 수 있습니다
* `lowerBound=1d` 그리고  `upperBound=2d` 내일 모레 어떤 것이든 선택해서

윤년은 고려하지 않고 모든 달은 30일입니다.

필터링을 지원하지 않습니다.

[`daterange`](#daterange) 조건자와 동일한 방식으로 패싯 추출을 지원합니다.

#### 속성 {#properties-17}

* **`upperBound`** - 현재 서버 시간에 대한 밀리초 단위 또는  `1s 2m 3h 4d 5w 6M 7y` (1초, 2분, 3시간, 4일, 5주, 6개월, 7년)인 상위 날짜, 음수 오프셋 `-` 에 사용
* **`lowerBound`** - 현재 서버 시간에 대한 밀리초 단위 또는  `1s 2m 3h 4d 5w 6M 7y` (1초, 2분, 3시간, 4일, 5주, 6개월, 7년)인 낮은 날짜, 음수 오프셋 `-` 에 사용

### savedquery {#savedquery}

이 조건에는 하위 그룹 조건자로 지속된 Query Builder 쿼리의 모든 조건자가 현재 쿼리에 포함됩니다.

추가 쿼리는 실행되지 않고 현재 쿼리를 확장합니다.

쿼리는 `QueryBuilder#storeQuery()` 을 사용하여 프로그래밍 방식으로 유지할 수 있습니다. 형식은 여러 줄 `String` 속성 또는 쿼리를 Java 속성 형식의 텍스트 파일로 포함하는 `nt:file` 노드일 수 있습니다.

저장된 쿼리의 조건자에 대한 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-19}

* **`savedquery`** - 저장된 쿼리의 경로(`String` 속성 또는  `nt:file` 노드)

### 유사 {#similar}

이 조건자는 JCR XPath의 `rep:similar()`을 사용하는 유사성 검색입니다.

필터링을 지원하지 않으며 패싯 추출을 지원하지 않습니다.

#### 속성 {#properties-20}

* **`similar`** - 유사한 노드를 찾을 노드의 절대 경로
* **`local`** - 하위 노드 또는 현재 노드 `.` 에 대한 상대 경로(선택 사항, 기본값은  `.`임)

### 태그 {#tag}

이 조건부는 태그 제목 경로를 지정하여 하나 이상의 태그가 지정된 컨텐츠를 검색합니다.

패싯 추출을 지원하고 현재 태그 제목 경로를 사용하여 각 고유 태그에 대한 버킷을 제공합니다.

#### 속성 {#properties-21}

* **`tag`** - 찾을 태그 제목 경로(예:  `properties:orientation/landscape`
* **`N_value`** -  `1_value`,  `2_value`, ...를 사용하여 여러 태그(기본적으로 와 결합되며,  `OR` if와 함께  `AND`   `and=true`사용)를 확인합니다.
* **`property`** - 확인할 속성(또는 속성의 상대 경로)(기본값  `cq:tags`

### tagid {#tagid}

이 조건부는 태그 ID를 지정하여 하나 이상의 태그가 지정된 컨텐츠를 검색합니다.

패싯 추출을 지원하고 현재 태그 ID를 사용하여 각 고유 태그에 대한 버킷을 제공합니다.

#### 속성 {#properties-22}

* **`tagid`** - 찾을 태그 ID(예:  `properties:orientation/landscape`
* **`N_value`** -  `1_value`,  `2_value`, ...를 사용하여 여러 태그 ID( `OR` if  `AND` 와 기본적으로  `and=true`결합됨)를 확인합니다.
* **`property`** - 확인할 속성(또는 속성의 상대 경로)(기본값  `cq:tags`

### tagsearch {#tagsearch}

이 조건부는 키워드를 지정하여 하나 이상의 태그가 지정된 콘텐츠를 검색합니다. 이렇게 하면 우선 제목에 이러한 키워드가 포함된 태그를 검색한 다음, 이러한 태그가 지정된 항목만 결과로 제한합니다.

패싯 추출을 지원하지 않습니다.

#### 속성 {#Properties-1}

* **`tagsearch`** - 태그 제목에서 검색할 키워드
* **`property`** - 고려할 속성(또는 속성의 상대 경로)(기본값  `cq:tags`
* **`lang`** - 현지화된 특정 태그 제목으로만 검색할 수 있습니다(예: `de`)
* **`all`** - 전체 태그 전체 텍스트, 즉 모든 제목, 설명 등을 검색하는 부울 값 (`lang`보다 우선함)

### 유형 {#type}

이 조건에서는 결과를 특정 JCR 노드 유형, 기본 노드 유형 또는 mixin 유형으로 제한합니다. 또한 해당 노드 유형의 하위 유형도 찾습니다. 저장소 검색 색인은 효율적인 실행을 위해 노드 유형을 포함해야 합니다.

패싯 추출을 지원하고 결과의 각 고유 유형에 대한 버킷을 제공합니다.

#### 속성 {#Properties-2}

* **`type`** - 검색할 노드 유형 또는 mixin 이름(예:  `cq:Page`
