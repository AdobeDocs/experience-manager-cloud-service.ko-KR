---
title: AEM 태깅 프레임워크
description: 컨텐츠를 분류하고 구성하려면 컨텐츠 태깅 및 AEM 태깅 인프라를 활용합니다.
exl-id: 25418d44-aace-4e73-be1a-4b1902f40403
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 0%

---

# AEM 태깅 프레임워크 {#aem-tagging-framework}

태깅을 사용하면 컨텐츠를 분류하고 구성할 수 있습니다. 태그는 네임스페이스 및 분류법으로 분류할 수 있습니다. 태그 사용에 대한 자세한 내용은

* 컨텐츠 작성자로서의 컨텐츠 태깅에 대한 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/features/tags.md)을 참조하십시오.
* 태그 작성 및 관리 방법과 컨텐츠 태그가 적용되는 항목에 대한 관리자의 관점에서 태그 관리를 참조하십시오.

이 문서에서는 AEM에서 태깅을 지원하는 기본 프레임워크와 이를 개발자로서 활용하는 방법에 중점을 둡니다.

## 소개 {#introduction}

컨텐츠에 태그를 지정하고 AEM 태깅 인프라를 활용하려면 다음과 같이 하십시오.

* 태그는 [분류 루트 노드 아래에 [`cq:Tag`](#cq-tag-node-type) 유형의 노드로 존재해야 합니다.](#taxonomy-root-node)
* 태그가 지정된 컨텐츠 노드의 `NodeType`에는 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin이 포함되어야 합니다.
* [`TagID`](#tagid)이(가) 컨텐츠 노드의 [`cq:tags`](#cq-tags-property) 속성에 추가되고 [`cq:Tag` 유형의 노드로 확인됩니다.](#cq-tag-node-type)

## cq:태그 노드 유형 {#cq-tag-node-type}

태그 선언이 `cq:Tag.` 유형의 노드의 저장소에 캡처됩니다

* 태그는 단순한 단어(예:`sky`) 또는 계층 분류(예:`fruit/apple`(일반 과일과 더 구체적인 사과를 모두 의미합니다.)
* 태그는 고유한 `TagID`으로 식별됩니다.
* 태그에는 제목, 현지화된 제목 및 설명과 같은 선택적 메타 정보가 있습니다. 제목이 있으면 `TagID` 대신 사용자 인터페이스에 표시되어야 합니다.

또한 태깅 프레임워크는 작성자와 사이트 방문자가 사전 정의된 특정 태그만 사용하도록 제한하는 기능을 제공합니다.

### 태그 특성 {#tag-characteristics}

* 노드 유형은 `cq:Tag`입니다.
* 노드 이름은 [`TagID`.](#tagid)
* [`TagID`](#tagid)은 항상 [네임스페이스를 포함합니다.](#tag-namespace)
* `jcr:title` 속성(UI에 표시할 제목)은 선택 사항입니다.
* `jcr:description` 속성은 선택 사항입니다.
* 하위 노드를 포함할 때에는 을 [컨테이너 태그라고 합니다.](#container-tags)
* 태그는 [분류 루트 노드라는 기본 경로 아래의 저장소에 저장됩니다.](#taxonomy-root-node)

### 태그 ID {#tagid}

`TagID` 은 저장소의 태그 노드로 확인되는 경로를 식별합니다.

일반적으로 `TagID`은 네임스페이스로 시작하는 축약형 `TagID`이거나 [분류 루트 노드에서 시작하는 절대 `TagID`일 수 있습니다.](#taxonomy-root-node)

컨텐츠에 태그를 지정하면, 아직 컨텐츠가 없으면 [`cq:tags`](#cq-tags-property) 속성이 컨텐츠 노드에 추가되고 `TagID` 가 속성의 `String` 배열 값에 추가됩니다.

`TagID`은 [네임스페이스](#tag-namespace)와 로컬 `TagID`로 구성됩니다. [컨테이너 ](#container-tags) 태그는 분류에서 계층 순서를 나타내는 하위 태그를 지정합니다. 하위 태그를 사용하여 로컬 `TagID` 과 동일한 태그를 참조할 수 있습니다. 예를 들어 `fruit` 이 `fruit/apple` 및 `fruit/banana` 등의 하위 태그가 있는 컨테이너 태그인 경우에도 이 컨텐츠를 사용하여 태깅할 수 있습니다.

### 분류 루트 노드 {#taxonomy-root-node}

분류 루트 노드는 저장소의 모든 태그에 대한 기본 경로입니다. 분류 루트 노드는 *이(가) 아닌*&#x200B;이(가) `cq:Tag` 유형의 노드여야 합니다.

AEM에서 기본 경로는 `/content/cq:tags`이고 루트 노드는 `cq:Folder` 유형입니다.

### 태그 네임스페이스 {#tag-namespace}

네임스페이스를 통해 항목을 그룹화할 수 있습니다. 가장 일반적인 사용 사례는 사이트당 네임스페이스(예: 공개 및 내부) 또는 더 큰 애플리케이션(예: 사이트 또는 자산)을 갖는 것이지만 네임스페이스는 다양한 기타 요구 사항에 사용할 수 있습니다. 네임스페이스는 사용자 인터페이스에서 현재 컨텐츠에 적용할 수 있는 태그의 하위 집합(예: 특정 네임스페이스의 태그)만 표시하는 데 사용됩니다.

태그의 네임스페이스는 [분류 루트 노드 바로 아래에 있는 노드인 분류 하위 트리의 첫 번째 수준입니다.](#taxonomy-root-node) 네임스페이스는 상위가  `cq:Tag` 노드 유형이 아닌 유형의  `cq:Tag` 노드입니다.

모든 태그에는 네임스페이스가 있습니다. 지정된 네임스페이스가 없으면 태그가 기본 네임스페이스에 할당됩니다(예: `TagID` `default`).`/content/cq:tags/default`  이러한 경우 제목은 기본적으로 `Standard Tags`입니다.

### 컨테이너 태그 {#container-tags}

컨테이너 태그는 임의의 수와 유형의 하위 노드를 포함하는 `cq:Tag` 유형의 노드로서, 사용자 지정 메타데이터로 태그 모델을 향상시킬 수 있습니다.

또한 분류법의 컨테이너 태그(또는 수퍼 태그)는 모든 하위 태그의 하위 합계로 사용됩니다.예를 들어 `fruit/apple` 태그가 지정된 컨텐츠도 `fruit` 태그로 지정된 것으로 간주됩니다. 즉, `fruit` 태그가 지정된 컨텐츠도 검색하면 `fruit/apple` 태그가 지정된 컨텐츠도 찾을 수 있습니다.

### TagID 확인 {#resolving-tagids}

태그 ID에 콜론(`:`)이 포함되어 있으면 콜론은 태그 또는 하위 분류에서 네임스페이스를 분리하며, 이 태그는 일반 슬래시(`/`)로 구분됩니다. 태그 ID에 콜론이 없는 경우 기본 네임스페이스가 암시됩니다.

태그의 표준 및 유일한 위치는 `/content/cq:tags` 이하여야 합니다.

기존 경로가 아닌 경로 또는 `cq:Tag` 노드를 가리키지 않는 경로를 참조하는 태그는 잘못된 것으로 간주되며 무시됩니다.

다음 표는 일부 샘플 `TagID`s, 해당 요소 및 `TagID`이 저장소의 절대 경로로 확인되는 방법을 보여줍니다.

| `TagID` | 네임스페이스 | 로컬 ID | 컨테이너 태그 | 리프 태그 | 저장소 절대 태그 경로 |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (없음) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (없음) | (없음) | (없음) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### 태그 제목 현지화 {#localization-of-tag-title}

태그에 선택적 제목 문자열 `jcr:title`이 포함되어 있으면 속성 `jcr:title.<locale>`을 추가하여 표시할 제목을 현지화할 수 있습니다.

자세한 내용은 다음을 참조하십시오.

* [API를 개발자로서 사용하는 방법을 설명하는 ](tagging-applications.md#tags-in-different-languages) 다른 언어의 태그
* 관리자로 Tagging 콘솔의 사용을 설명하는 다양한 언어로 태그 관리

### 액세스 제어 {#access-control}

태그는 [분류 루트 노드 아래에 있는 저장소의 노드로 존재합니다.](#taxonomy-root-node) 작성자 및 사이트 방문자가 주어진 네임스페이스에서 태그를 만들 수 있도록 허용 또는 거부하는 것은 리포지토리에서 적절한 ACL을 설정하여 수행할 수 있습니다.

특정 태그나 네임스페이스에 대한 읽기 권한을 거부하면 특정 콘텐츠에 태그를 적용하는 기능이 제어됩니다.

일반적인 방법은 다음과 같습니다.

* 모든 네임스페이스에 `tag-administrators` 그룹/역할 쓰기 액세스 허용(`/content/cq:tags` 아래에 추가/수정). 이 그룹에는 기본적으로 AEM이 포함되어 있습니다.
* 사용자/작성자가 읽을 수 있어야 하는 모든 네임스페이스에 대한 읽기 액세스 권한을 부여합니다(대부분 모두).
* 사용자/작성자가 사용자/작성자가 태그를 자유롭게 정의할 수 있는 네임스페이스에 대한 쓰기 액세스 허용(`/content/cq:tags/some_namespace` 아래`add_node`)

## 타깃팅 가능한 컨텐츠 :cq:Taggable Mixin {#taggable-content-cq-taggable-mixin}

애플리케이션 개발자가 컨텐츠 유형에 태깅을 첨부하려면 노드의 등록([CND](https://jackrabbit.apache.org/node-type-notation.html))에 `cq:Taggable` mixin 또는 `cq:OwnerTaggable` mixin이 포함되어야 합니다.

`cq:Taggable`에서 상속되는 `cq:OwnerTaggable` mixin은 컨텐츠가 소유자/작성자에 의해 분류될 수 있음을 나타내기 위한 것입니다. AEM에서 이 속성은 `cq:PageContent` 노드의 특성일 뿐입니다. 태깅 프레임워크에는 `cq:OwnerTaggable` mixin이 필요하지 않습니다.

>[!NOTE]
>
>집계된 컨텐츠 항목의 최상위 노드(또는 해당 `jcr:content` 노드)에서만 태그를 활성화하는 것이 좋습니다. 해당 예는 다음과 같습니다.
>
>* `jcr:content` 노드가 `cq:PageContent` 유형인 페이지(`cq:Page`)에 `cq:Taggable` mixin이 포함됩니다.
>* 자산(`cq:Asset`)으로서, 여기서 `jcr:content/metadata` 노드에는 항상 `cq:Taggable` mixin이 있습니다.


### 노드 유형 표기법(CND) {#node-type-notation-cnd}

노드 유형 정의는 저장소에 CND 파일로 있습니다. CND 표기법은 [JCR 설명서의 일부로 정의됩니다.](https://jackrabbit.apache.org/node-type-notation.html)

AEM에 포함된 노드 유형에 대한 필수 정의는 다음과 같습니다.

```xml
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## cq:tags 속성 {#cq-tags-property}

`cq:tags` 속성은 작성자 또는 사이트 방문자가 컨텐츠에 적용할 때 하나 이상의 `TagID`를 저장하는 데 사용되는 `String` 배열입니다. 속성은 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin으로 정의된 노드에 추가될 때만 의미가 있습니다.

>[!NOTE]
>
>AEM 태그 지정 기능을 활용하려면 사용자 정의 개발 애플리케이션에서 `cq:tags` 이외의 태그 속성을 정의해서는 안 됩니다.

## 태그 {#moving-and-merging-tags} 이동 및 병합

다음은 [태깅] 콘솔을 사용하여 태그를 이동하거나 병합할 때 리포지토리의 효과에 대한 설명입니다.

태그 A가 `/content/cq:tags` 아래에 있는 태그 B로 이동되거나 병합되면:

* 태그 A가 삭제되지 않고 `cq:movedTo` 속성을 수신합니다.
   * `cq:movedTo` 태그 B를 가리킵니다.
   * 이 속성은 태그 A가 태그 B로 이동되거나 병합되었음을 의미합니다.
   * 태그 B를 이동하면 이 속성이 그에 따라 업데이트됩니다.
   * 따라서 태그 A는 숨겨져 있으며, 태그 A를 가리키는 컨텐츠 노드의 태그 ID를 확인하기 위해 저장소에만 유지됩니다.
   * 태그 가비지 수집기는 더 이상 콘텐츠 노드가 해당 태그를 가리키지 않으면 태그 A와 같은 태그를 제거합니다.
   * `cq:movedTo` 속성의 특수 값은 `nirvana` 입니다. 이 값은 태그를 삭제할 때 적용되지만 `cq:movedTo` 가 있어야 하므로 저장소에서 제거할 수 없습니다.

      >[!NOTE]
      >
      >`cq:movedTo` 속성은 다음 조건 중 하나가 충족되는 경우에만 이동되거나 병합된 태그에 추가됩니다.
      >
      > 1. 태그는 컨텐츠에 사용됩니다(참조자가 있음). 또는
      > 1. 태그에 이미 이동된 하위 항목이 있습니다.


* 태그 B가 만들어지고(이동의 경우) `cq:backlinks` 속성을 받습니다.
   * `cq:backlinks` 는 참조를 다른 방향으로 유지합니다. 즉, 태그 B로 이동했거나 태그 B와 병합된 모든 태그의 목록을 유지합니다.
   * 이것은 대부분 태그 B가 이동/병합/삭제되거나 태그 B가 활성화될 때 `cq:movedTo` 속성을 최신 상태로 유지하는 데 필요합니다. 이 경우 모든 백링크 태그도 활성화해야 합니다.

      >[!NOTE]
      >
      >`cq:backlinks` 속성은 다음 조건 중 하나가 충족되는 경우에만 이동되거나 병합된 태그에 추가됩니다.
      >
      > 1. 태그는 컨텐츠에 사용됩니다(참조자가 있음). 또는
      > 1. 태그에 이미 이동된 하위 항목이 있습니다.


컨텐츠 노드의 `cq:tags` 속성을 읽으면 다음 해상도가 포함됩니다.

1. `/content/cq:tags` 아래에 일치하는 항목이 없으면 태그가 반환되지 않습니다.
1. 태그에 `cq:movedTo` 속성이 설정된 경우 참조된 태그 ID가 따릅니다.
   * 이 단계는 뒤에 오는 태그에 `cq:movedTo` 속성이 있는 한 반복됩니다.
1. 뒤에 오는 태그에 `cq:movedTo` 속성이 없으면 태그가 읽습니다.

태그를 이동하거나 병합했을 때 변경 내용을 게시하려면 `cq:Tag` 노드 및 모든 백링크를 복제해야 합니다. 이 작업은 태그가 태그 관리 콘솔에서 활성화되면 자동으로 수행됩니다.

나중에 페이지의 `cq:tags` 속성에 대한 업데이트로 이전 참조가 자동으로 정리됩니다. API를 통해 이동한 태그를 확인하면 대상 태그가 반환되어 대상 태그 ID가 제공되므로 트리거됩니다.
