---
title: AEM 태깅 프레임워크
description: 컨텐츠에 태그를 지정하고 AEM Tagging 인프라를 활용하여 분류하고 구성할 수 있습니다.
translation-type: tm+mt
source-git-commit: 4bf023068aa69fb6b69c6f2443703ea2bbbf7d42
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 0%

---


# AEM Tagging Framework {#aem-tagging-framework}

태깅을 사용하면 컨텐츠를 분류하고 구성할 수 있습니다. 태그는 네임스페이스 및 분류법으로 분류할 수 있습니다. 태그 사용에 대한 자세한 내용은 다음을 참조하십시오.

* 컨텐츠 작성자의 컨텐츠 태그 지정에 대한 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/features/tags.md)을 참조하십시오.
* 태그 만들기 및 관리와 컨텐츠 태그가 적용된 관리자 관점에 대한 태그 관리를 참조하십시오.

이 문서에서는 AEM의 태그 지정을 지원하는 기본 프레임워크와 이를 개발자로서 활용하는 방법에 대해 집중적으로 살펴봅니다.

## 소개 {#introduction}

컨텐츠에 태그를 지정하고 AEM Tagging 인프라를 활용하려면 다음을 수행하십시오.

* 태그는 [분류 루트 노드 아래에 [`cq:Tag`](#cq-tag-node-type) 유형의 노드로 있어야 합니다.](#taxonomy-root-node)
* 태그가 지정된 컨텐트 노드의 `NodeType`에는 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 믹신이 포함되어야 합니다.
* [`TagID`](#tagid)이(가) 콘텐트 노드의 [`cq:tags`](#cq-tags-property) 속성에 추가되고 [`cq:Tag` 유형의 노드로 확인됩니다.](#cq-tag-node-type)

## cq:태그 노드 유형 {#cq-tag-node-type}

태그 선언이 `cq:Tag.` 유형의 노드의 저장소에 캡처됩니다.

* 태그는 단순한 단어(예:`sky`) 또는 계층적 분류(예:`fruit/apple`(일반 과일과 보다 구체적인 사과를 모두 의미합니다).
* 태그는 고유한 `TagID`으로 식별됩니다.
* 태그에는 제목, 현지화된 제목 및 설명과 같은 선택적 메타 정보가 있습니다. 제목이 있을 때 `TagID` 대신 사용자 인터페이스에 표시되어야 합니다.

또한 태깅 프레임워크에서는 작성자 및 사이트 방문자가 특정 사전 정의된 태그만 사용하도록 제한할 수 있습니다.

### 태그 특성 {#tag-characteristics}

* 노드 유형은 `cq:Tag`입니다.
* 노드 이름은 [`TagID`의 구성 요소입니다.](#tagid)
* [`TagID`](#tagid)에는 항상 [네임스페이스가 포함됩니다.](#tag-namespace)
* `jcr:title` 속성(UI에 표시할 제목)은 선택 사항입니다.
* `jcr:description` 속성은 선택 사항입니다.
* 하위 노드를 포함하는 경우 는 [컨테이너 태그로 참조됩니다.](#container-tags)
* 태그는 [분류 루트 노드라는 기본 경로 아래의 저장소에 저장됩니다.](#taxonomy-root-node)

### 태그 ID {#tagid}

`TagID`은 저장소의 태그 노드로 확인되는 경로를 식별합니다.

일반적으로 `TagID`은 네임스페이스로 시작하는 축약형 `TagID`이거나 [분류 루트 노드에서 시작하는 절대 `TagID`일 수 있습니다.](#taxonomy-root-node)

콘텐츠에 태그가 지정되면 콘텐츠가 아직 존재하지 않으면 [`cq:tags`](#cq-tags-property) 속성이 콘텐츠 노드에 추가되고 `TagID`이 속성의 `String` 배열 값에 추가됩니다.

`TagID`은 [네임스페이스](#tag-namespace)에 로컬 `TagID`으로 구성됩니다. [컨테이너 ](#container-tags) 태그는 분류에서 계층적 순서를 나타내는 하위 태그입니다. 하위 태그를 사용하여 로컬 `TagID`과 동일한 태그를 참조할 수 있습니다. 예를 들어 `fruit`이(가) `fruit/apple` 및 `fruit/banana` 등의 하위 태그가 있는 컨테이너 태그인 경우에도 컨텐츠를 태깅할 수 있습니다.

### 분류 루트 노드 {#taxonomy-root-node}

분류 루트 노드는 저장소의 모든 태그에 대한 기본 경로입니다. 분류 루트 노드는 *이(가) 아닌*&#x200B;이어야 합니다. `cq:Tag` 유형의 노드여야 합니다.

AEM에서 기본 경로는 `/content/cq:tags`이고 루트 노드는 `cq:Folder` 유형입니다.

### 태그 네임스페이스 {#tag-namespace}

네임스페이스를 통해 여러 항목을 그룹화할 수 있습니다. 가장 일반적인 사용 사례는 사이트당(예: 공개 및 내부) 또는 더 큰 응용 프로그램(예: 사이트 또는 에셋)당 네임스페이스를 갖는 것이지만, 네임스페이스는 다양한 기타 요구 사항에 사용할 수 있습니다. 네임스페이스는 사용자 인터페이스에서 현재 콘텐츠에 적용되는 태그의 하위 집합(즉, 특정 네임스페이스의 태그)만 표시하는 데 사용됩니다.

태그의 네임스페이스는 분류 하위 트리에서 첫 번째 레벨이며, 분류법 루트 노드 바로 아래의 노드입니다.[](#taxonomy-root-node) 네임스페이스는 부모가 노드 유형이  `cq:Tag` 아닌 유형의  `cq:Tag` 노드입니다.

모든 태그에는 네임스페이스가 있습니다. 네임스페이스를 지정하지 않으면 태그가 기본 네임스페이스에 지정됩니다. 즉, `TagID` `default``/content/cq:tags/default`.  이러한 경우 제목은 기본적으로 `Standard Tags`으로 설정됩니다.

### 컨테이너 태그 {#container-tags}

컨테이너 태그는 자식 노드의 수와 유형을 포함하는 `cq:Tag` 유형의 노드로서, 사용자 지정 메타데이터로 태그 모델을 향상시킬 수 있습니다.

또한 택소노미의 컨테이너 태그(또는 super 태그)는 모든 하위 태그의 하위 합계로 사용됩니다.예를 들어 `fruit/apple`으로 태그가 지정된 컨텐츠는 `fruit` 태그로 인식됩니다. 예를 들어 `fruit`로 태그가 지정된 컨텐츠도 검색하면 `fruit/apple`로 태그가 지정된 컨텐츠도 검색됩니다.

### TagID 해결 중 {#resolving-tagids}

태그 ID에 콜론(`:`)이 포함되어 있으면 콜론은 네임스페이스를 태그 또는 하위 분류에서 분리한 다음 일반 슬래시(`/`)로 구분합니다. 태그 ID에 콜론이 없는 경우 기본 네임스페이스는 암시됩니다.

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

### 태그 제목 {#localization-of-tag-title} 현지화

태그에 선택적 제목 문자열 `jcr:title`이 포함된 경우 속성 `jcr:title.<locale>`을 추가하여 표시할 제목을 현지화할 수 있습니다.

자세한 내용은 다음을 참조하십시오.

* [API를 개발자로 ](tagging-applications.md#tags-in-different-languages) 사용하는 방법을 설명하는 다른 언어의 태그
* 다른 언어로 태그 관리 - Tagging 콘솔을 관리자로 사용하는 방법을 설명합니다.

### 액세스 제어 {#access-control}

태그는 [분류 루트 노드 아래의 저장소에 노드로 존재합니다.](#taxonomy-root-node) 작성자와 사이트 방문자가 지정된 네임스페이스에 태그를 만들 수 있도록 허용하거나 거부하려면 저장소에서 적절한 ACL을 설정하여 수행할 수 있습니다.

특정 태그 또는 네임스페이스에 대한 읽기 권한을 거부하면 특정 콘텐츠에 태그를 적용하는 기능이 제어됩니다.

일반적인 방법은 다음과 같습니다.

* `tag-administrators` 그룹/역할 쓰기 액세스 권한을 모든 네임스페이스에 부여할 수 있습니다(`/content/cq:tags` 아래에 추가/수정). 이 그룹에는 AEM이 기본적으로 포함되어 있습니다.
* 사용자/작성자가 읽을 수 있어야 하는 모든 네임스페이스에 대한 읽기 액세스 권한을 부여할 수 있습니다(대부분 모두).
* 사용자/작성자가 태그를 자유롭게 정의해야 하는 네임스페이스에 대한 액세스 권한 허용(`/content/cq:tags/some_namespace` 아래의 `add_node`)

## 태그 가능한 컨텐츠:cq:Taggable Mixin {#taggable-content-cq-taggable-mixin}

애플리케이션 개발자가 컨텐트 유형에 태깅을 첨부하려면 노드의 등록([CND](https://jackrabbit.apache.org/node-type-notation.html))에 `cq:Taggable` 믹싱 또는 `cq:OwnerTaggable` 믹신이 포함되어야 합니다.

`cq:Taggable`에서 상속되는 `cq:OwnerTaggable` 혼합은 컨텐츠를 소유자/작성자가 분류할 수 있음을 나타내기 위한 것입니다. AEM에서는 `cq:PageContent` 노드의 속성만 나타냅니다. 태깅 프레임워크에서는 `cq:OwnerTaggable` 믹신이 필요하지 않습니다.

>[!NOTE]
>
>집계된 컨텐츠 항목(또는 해당 `jcr:content` 노드)의 최상위 노드에서만 태그를 활성화하는 것이 좋습니다. 예:
>
>* 페이지(`cq:Page`). 여기서 `jcr:content`node는 `cq:Taggable` 믹싱을 포함하는 `cq:PageContent` 유형입니다.
>* 자산(`cq:Asset`). 여기서 `jcr:content/metadata` 노드에는 항상 `cq:Taggable` 믹신이 있습니다.


### 노드 유형 표기법(CND) {#node-type-notation-cnd}

노드 유형 정의는 저장소에 CND 파일로 있습니다. CND 표기법은 [JCR 설명서의 일부로 정의됩니다.](https://jackrabbit.apache.org/node-type-notation.html).

AEM에 포함된 노드 유형에 대한 기본 정의는 다음과 같습니다.

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

`cq:tags` 속성은 작성자 또는 사이트 방문자가 컨텐츠에 적용할 때 하나 이상의 `TagID`s를 저장하는 데 사용되는 `String` 배열입니다. 속성에는 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 혼합으로 정의된 노드에 추가할 때만 의미가 있습니다.

>[!NOTE]
>
>AEM 태그 지정 기능을 활용하려면 사용자 정의 개발 응용 프로그램이 `cq:tags` 이외의 태그 속성을 정의해서는 안 됩니다.

## 태그 이동 및 병합 {#moving-and-merging-tags}

다음은 태깅 콘솔을 사용하여 태그를 이동하거나 병합할 때 저장소의 효과에 대한 설명입니다.

태그 A가 `/content/cq:tags` 아래의 태그 B로 이동 또는 병합될 때:

* 태그 A는 삭제되지 않으며 `cq:movedTo` 속성을 받습니다.
   * `cq:movedTo` 태그 B를 가리킵니다.
   * 이 속성은 태그 A가 태그 B로 이동 또는 병합되었음을 의미합니다.
   * 태그 B를 이동하면 그에 따라 이 속성이 업데이트됩니다.
   * 태그 A는 숨겨진 상태로 보관되므로 태그 A를 가리키는 컨텐트 노드의 태그 ID만 확인할 수 있습니다.
   * 태그 가비지 수집기는 더 이상 컨텐트 노드가 해당 태그를 가리키지 않으면 태그 A와 같은 태그를 제거합니다.
   * `cq:movedTo` 속성에 대한 특수 값은 `nirvana`입니다. 이 값은 태그를 삭제할 때 적용되지만 `cq:movedTo`의 하위 태그가 있기 때문에 저장소에서 제거할 수 없습니다.

      >[!NOTE]
      >
      >`cq:movedTo` 속성은 다음 조건 중 하나가 충족되는 경우에만 이동되거나 병합된 태그에만 추가됩니다.
      >
      > 1. 이 태그는 컨텐츠에 사용됩니다(참조). 또는
      > 1. 태그에 이미 이동한 하위 항목이 있습니다.


* 태그 B가 만들어지고(이동 시) `cq:backlinks` 속성을 받습니다.
   * `cq:backlinks` 참조를 다른 방향으로 유지합니다. 즉, 태그 B로 이동하거나 병합한 모든 태그의 목록을 유지합니다.
   * 태그 B를 이동/병합/삭제할 때나 태그 B를 활성화할 때 `cq:movedTo` 속성을 최신 상태로 유지하는 데 필요합니다. 이 경우 모든 backlinks 태그도 활성화해야 합니다.

      >[!NOTE]
      >
      >`cq:backlinks` 속성은 다음 조건 중 하나가 충족되는 경우에만 이동되거나 병합된 태그에만 추가됩니다.
      >
      > 1. 이 태그는 컨텐츠에 사용됩니다(참조). 또는
      > 1. 태그에 이미 이동한 하위 항목이 있습니다.


콘텐트 노드의 `cq:tags` 속성을 읽으면 다음 해상도가 포함됩니다.

1. `/content/cq:tags` 아래에 일치하는 태그가 없으면 반환되지 않습니다.
1. 태그에 `cq:movedTo` 속성 집합이 있으면 참조된 태그 ID가 따릅니다.
   * 이 단계는 뒤에 오는 태그에 `cq:movedTo` 속성이 있으면 반복됩니다.
1. 뒤에 오는 태그에 `cq:movedTo` 속성이 없으면 태그가 읽혀집니다.

태그를 이동하거나 병합할 때 변경 내용을 게시하려면 `cq:Tag` 노드 및 모든 해당 백링크가 복제되어야 합니다. 태그 관리 콘솔에서 태그가 활성화되면 자동으로 수행됩니다.

나중에 페이지의 `cq:tags` 속성이 업데이트되면 이전 참조가 자동으로 정리됩니다. API를 통해 이동한 태그를 확인하면 대상 태그가 반환되므로 대상 태그 ID를 제공하므로 실행됩니다.
