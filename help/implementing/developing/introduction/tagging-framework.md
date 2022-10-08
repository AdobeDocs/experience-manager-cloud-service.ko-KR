---
title: AEM 태그 지정 프레임워크
description: 컨텐츠를 분류하고 구성하려면 컨텐츠 태깅 및 AEM 태깅 인프라를 활용합니다.
exl-id: 25418d44-aace-4e73-be1a-4b1902f40403
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '1570'
ht-degree: 0%

---

# AEM 태깅 프레임워크 {#aem-tagging-framework}

태깅을 사용하면 컨텐츠를 분류하고 구성할 수 있습니다. 태그는 네임스페이스 및 분류법으로 분류할 수 있습니다. 태그 사용에 대한 자세한 내용은

* 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/features/tags.md) 컨텐츠 작성자로서 컨텐츠를 태깅하는 방법에 대한 정보입니다.
* 태그 작성 및 관리 방법과 컨텐츠 태그가 적용되는 항목에 대한 관리자의 관점에서 태그 관리를 참조하십시오.

이 문서에서는 AEM에서 태깅을 지원하는 기본 프레임워크와 이를 개발자로서 활용하는 방법에 중점을 둡니다.

## 소개 {#introduction}

컨텐츠에 태그를 지정하고 AEM 태깅 인프라를 활용하려면 다음과 같이 하십시오.

* 태그는 유형의 노드로 존재해야 합니다 [`cq:Tag`](#cq-tag-node-type) 아래에 [분류 루트 노드.](#taxonomy-root-node)
* 태그가 지정된 컨텐츠 노드의 `NodeType` 에는 다음을 포함해야 합니다 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 믹신
* 다음 [`TagID`](#tagid) 컨텐츠 노드의 [`cq:tags`](#cq-tags-property) 속성 및 가 유형의 노드로 확인됨 [`cq:Tag`.](#cq-tag-node-type)

## cq:태그 노드 유형 {#cq-tag-node-type}

태그의 선언은 유형 노드의 저장소에 캡처됩니다 `cq:Tag.`

* 태그는 단순한 단어일 수 있습니다(예: `sky`) 또는 계층 분류(예: `fruit/apple`즉, 일반 과일과 보다 구체적인 사과를 모두 의미합니다.
* 태그는 고유한 `TagID`.
* 태그에는 제목, 현지화된 제목 및 설명과 같은 선택적 메타 정보가 있습니다. 제목은 `TagID`, 있을 경우.

또한 태깅 프레임워크는 작성자와 사이트 방문자가 사전 정의된 특정 태그만 사용하도록 제한하는 기능을 제공합니다.

### 태그 특성 {#tag-characteristics}

* 노드 유형은 다음과 같습니다. `cq:Tag`.
* 노드 이름은 [`TagID`.](#tagid)
* 다음 [`TagID`](#tagid) 항상 포함 [네임스페이스.](#tag-namespace)
* 다음 `jcr:title` 속성(UI에 표시할 제목)은 선택 사항입니다.
* 다음 `jcr:description` 속성은 선택 사항입니다.
* 하위 노드를 포함할 때에는 을 [컨테이너 태그입니다.](#container-tags)
* 태그는 라는 기본 경로 아래의 저장소에 저장됩니다 [분류 루트 노드.](#taxonomy-root-node)

### 태그 ID {#tagid}

A `TagID` 저장소의 태그 노드로 확인되는 경로를 식별합니다.

일반적으로 `TagID` 축약이다 `TagID` 네임스페이스로 시작하거나 절대 네임스페이스가 될 수 있습니다. `TagID` 시작 [분류 루트 노드.](#taxonomy-root-node)

컨텐츠에 태그를 지정할 때 태그가 아직 없는 경우 [`cq:tags`](#cq-tags-property) 속성이 콘텐츠 노드 및 `TagID` 가 속성의 `String` 배열 값.

다음 `TagID` 다음으로 구성됨 [namespace](#tag-namespace) 그 다음에 `TagID`. [컨테이너 태그](#container-tags) 분류에서 계층적 순서를 나타내는 하위 태그가 있습니다. 하위 태그를 사용하여 로컬 태그와 동일한 태그를 참조할 수 있습니다 `TagID`. 예를 들어 `fruit` 과 같이 하위 태그가 있는 컨테이너 태그인 경우에도 허용됩니다. `fruit/apple` 및 `fruit/banana`.

### 분류 루트 노드 {#taxonomy-root-node}

분류 루트 노드는 저장소의 모든 태그에 대한 기본 경로입니다. 분류 루트 노드는 *not* 유형의 노드임 `cq:Tag`.

AEM에서 기본 경로는 입니다. `/content/cq:tags` 그리고 루트 노드는 유형이 됩니다. `cq:Folder`.

### 태그 네임스페이스 {#tag-namespace}

네임스페이스를 통해 항목을 그룹화할 수 있습니다. 가장 일반적인 사용 사례는 사이트당 네임스페이스(예: 공개 및 내부)나 더 큰 애플리케이션(예: 사이트 또는 자산)을 갖는 것이지만, 네임스페이스는 다양한 기타 요구 사항에 사용할 수 있습니다. 네임스페이스는 사용자 인터페이스에서 현재 컨텐츠에 적용할 수 있는 태그의 하위 집합(예: 특정 네임스페이스의 태그)만 표시하는 데 사용됩니다.

태그의 네임스페이스는 분류법 하위 트리의 첫 번째 수준이며, 이 하위 트리는 [분류 루트 노드.](#taxonomy-root-node) 네임스페이스는 유형의 노드입니다 `cq:Tag` 해당 부모가 아님 `cq:Tag` 노드 유형입니다.

모든 태그에는 네임스페이스가 있습니다. 지정된 네임스페이스가 없으면 태그가 기본 네임스페이스에 지정되며, `TagID` `default`예, `/content/cq:tags/default`.  제목은 기본적으로 `Standard Tags`이 경우

### 컨테이너 태그 {#container-tags}

컨테이너 태그는 유형의 노드입니다 `cq:Tag` 에는 임의 개수의 하위 노드 및 유형이 포함되어 있으므로 사용자 지정 메타데이터로 태그 모델을 향상시킬 수 있습니다.

또한 분류법의 컨테이너 태그(또는 수퍼 태그)는 모든 하위 태그의 하위 합계로 사용됩니다. 예를 들어 `fruit/apple` 는 태그 지정으로 간주됩니다 `fruit` 또한, `fruit` 또한 `fruit/apple`.

### TagID 해결 {#resolving-tagids}

태그 ID에 콜론()이 있는 경우`:`로 지정하면 콜론은 태그 또는 하위 분류에서 네임스페이스를 분리하며 일반 슬래시(`/`). 태그 ID에 콜론이 없는 경우 기본 네임스페이스가 암시됩니다.

태그의 표준 및 전용 위치는 다음과 같습니다 `/content/cq:tags`.

기존 경로가 아닌 경로 또는 `cq:Tag` 노드는 유효하지 않은 것으로 간주되며 무시됩니다.

다음 표에는 몇 가지 샘플이 나와 있습니다 `TagID`s, 해당 요소 및 방법 `TagID` 저장소의 절대 경로로 확인됩니다.

| `TagID` | 네임스페이스 | 로컬 ID | 컨테이너 태그 | 리프 태그 | 저장소 절대 태그 경로 |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (없음) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (없음) | (없음) | (없음) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### 태그 제목 현지화 {#localization-of-tag-title}

태그에 선택적 제목 문자열이 포함되어 있는 경우 `jcr:title`를 채울 속성을 추가하여 표시할 제목을 현지화할 수 있습니다 `jcr:title.<locale>`.

자세한 내용은 다음을 참조하십시오.

* [다른 언어로 된 태그,](tagging-applications.md#tags-in-different-languages) 개발자로서 API의 사용을 설명하는 요소
* 관리자로 Tagging 콘솔의 사용을 설명하는 다양한 언어로 태그 관리

### 액세스 제어 {#access-control}

태그는 저장소의 [분류 루트 노드.](#taxonomy-root-node) 작성자 및 사이트 방문자가 주어진 네임스페이스에서 태그를 만들 수 있도록 허용 또는 거부하는 것은 리포지토리에서 적절한 ACL을 설정하여 수행할 수 있습니다.

특정 태그나 네임스페이스에 대한 읽기 권한을 거부하면 특정 콘텐츠에 태그를 적용하는 기능이 제어됩니다.

일반적인 방법은 다음과 같습니다.

* 허용 `tag-administrators` 모든 네임스페이스에 대한 그룹/역할 쓰기 액세스 권한( `/content/cq:tags`). 이 그룹에는 기본적으로 AEM이 포함되어 있습니다.
* 사용자/작성자가 읽을 수 있어야 하는 모든 네임스페이스에 대한 읽기 액세스 권한을 부여합니다(대부분 모두).
* 사용자/작성자가 사용자/작성자가 태그를 자유롭게 정의할 수 있는 네임스페이스에 대한 쓰기 액세스 권한 허용(`add_node` 아래에 `/content/cq:tags/some_namespace`)

## 타깃팅 가능한 컨텐츠 : cq:Taggable Mixin {#taggable-content-cq-taggable-mixin}

애플리케이션 개발자가 컨텐츠 유형에 태깅을 첨부하려면 노드의 등록([CND](https://jackrabbit.apache.org/node-type-notation.html))에는 를 포함해야 합니다. `cq:Taggable` mixin 또는 `cq:OwnerTaggable` 믹신

다음 `cq:OwnerTaggable` 에서 상속하는 mixin `cq:Taggable`은(는) 컨텐츠가 소유자/작성자에 의해 분류될 수 있음을 나타내기 위한 것입니다. AEM에서 이 속성은 `cq:PageContent` 노드 아래에 있어야 합니다. 다음 `cq:OwnerTaggable` 태깅 프레임워크에서는 mixin이 필요하지 않습니다.

>[!NOTE]
>
>집계된 컨텐츠 항목의 최상위 노드(또는 해당 항목)에서만 태그를 활성화하는 것이 좋습니다 `jcr:content` 노드)에 속해 있어야 합니다. 해당 예는 다음과 같습니다.
>
>* 페이지 (`cq:Page`)에서 `jcr:content`node는 type입니다. `cq:PageContent`: `cq:Taggable` 믹신
>* 자산 (`cq:Asset`)에서 `jcr:content/metadata` 노드에는 항상 가 있습니다 `cq:Taggable` 믹신


### 노드 유형 표기법(CND) {#node-type-notation-cnd}

노드 유형 정의는 저장소에 CND 파일로 있습니다. CND 표기법은 페이지의 일부로 정의됩니다 [JCR 설명서.](https://jackrabbit.apache.org/node-type-notation.html).

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

다음 `cq:tags` 속성은 다음과 같습니다. `String` 하나 이상을 저장하는 데 사용되는 배열 `TagID`작성자 또는 사이트 방문자가 컨텐츠에 적용하는 경우입니다. 속성은 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 믹신

>[!NOTE]
>
>AEM 태그 지정 기능을 활용하려면 사용자 정의 개발 애플리케이션에서 `cq:tags`.

## 태그 이동 및 병합 {#moving-and-merging-tags}

다음은 [태깅] 콘솔을 사용하여 태그를 이동하거나 병합할 때 리포지토리의 효과에 대한 설명입니다.

태그 A를 아래의 태그 B로 이동하거나 병합하는 경우 `/content/cq:tags`:

* 태그 A는 삭제되지 않고 `cq:movedTo` 속성을 사용합니다.
   * `cq:movedTo` 태그 B를 가리킵니다.
   * 이 속성은 태그 A가 태그 B로 이동되거나 병합되었음을 의미합니다.
   * 태그 B를 이동하면 이 속성이 그에 따라 업데이트됩니다.
   * 따라서 태그 A는 숨겨져 있으며, 태그 A를 가리키는 컨텐츠 노드의 태그 ID를 확인하기 위해 저장소에만 유지됩니다.
   * 태그 가비지 수집기는 더 이상 콘텐츠 노드가 해당 태그를 가리키지 않으면 태그 A와 같은 태그를 제거합니다.
   * 에 대한 특수 값 `cq:movedTo` property `nirvana`- 태그가 삭제될 때 적용되지만, `cq:movedTo` 그건 보관해야 합니다

      >[!NOTE]
      >
      >다음 `cq:movedTo` 속성은 다음 조건 중 하나가 충족되는 경우에만 이동되거나 병합된 태그에 추가됩니다.
      >
      > 1. 태그는 컨텐츠에 사용됩니다(참조자가 있음). 또는
      > 1. 태그에 이미 이동된 하위 항목이 있습니다.

* 태그 B가 만들어지고(이동의 경우) `cq:backlinks` 속성을 사용합니다.
   * `cq:backlinks` 는 참조를 다른 방향으로 유지합니다. 즉, 태그 B로 이동했거나 태그 B와 병합된 모든 태그의 목록을 유지합니다.
   * 이것은 주로 보존하기 위해 필요합니다 `cq:movedTo` 태그 B가 이동/병합/삭제되거나 태그 B가 활성화될 때까지의 속성. 이 경우 모든 백링크 태그도 활성화해야 합니다.

      >[!NOTE]
      >
      >다음 `cq:backlinks` 속성은 다음 조건 중 하나가 충족되는 경우에만 이동되거나 병합된 태그에 추가됩니다.
      >
      > 1. 태그는 컨텐츠에 사용됩니다(참조자가 있음). 또는
      > 1. 태그에 이미 이동된 하위 항목이 있습니다.


읽기 `cq:tags` 컨텐츠 노드의 속성에는 다음 해상도가 포함됩니다.

1. 아래에 일치하는 항목이 없으면 `/content/cq:tags`, 태그가 반환되지 않습니다.
1. 태그에 `cq:movedTo` 속성 세트, 참조된 태그 ID가 따릅니다.
   * 이 단계는 뒤에 오는 태그에 `cq:movedTo` 속성을 사용합니다.
1. 다음에 나오는 태그에 `cq:movedTo` 속성, 태그를 읽습니다.

태그가 이동되거나 병합될 때 변경 내용을 게시하려면 `cq:Tag` 노드 및 모든 백링크를 복제해야 합니다. 이 작업은 태그가 태그 관리 콘솔에서 활성화되면 자동으로 수행됩니다.

페이지의 `cq:tags` 속성은 이전 참조를 자동으로 정리합니다. API를 통해 이동한 태그를 확인하면 대상 태그가 반환되어 대상 태그 ID가 제공되므로 트리거됩니다.
