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

태깅을 사용하면 컨텐츠를 분류하고 구성할 수 있습니다. 태그는 네임스페이스와 분류법으로 분류될 수 있습니다. 태그 사용에 대한 자세한 내용은 다음을 참조하십시오.

* 컨텐츠 [작성자의](/help/sites-cloud/authoring/features/tags.md) 태그 지정에 대한 자세한 내용은 태그 사용을 참조하십시오.
* 태그 만들기 및 관리와 컨텐츠 태그가 적용된 관리자 관점에서는 태그 관리를 참조하십시오.

이 문서에서는 AEM에서 태깅을 지원하는 기본 프레임워크와 이를 개발자로서 활용하는 방법에 대해 집중적으로 살펴봅니다.

## 소개 {#introduction}

컨텐츠에 태그를 지정하고 AEM Tagging 인프라를 활용하려면

* 이 태그는 분류 루트 노드 [`cq:Tag`](#cq-tag-node-type) 아래에 [유형 노드로 존재해야 합니다.](#taxonomy-root-node)
* 태그가 지정된 컨텐츠 노드의 `NodeType` 는 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin을 포함해야 합니다.
* 이 [`TagID`](#tagid) 는 컨텐트 노드의 [`cq:tags`](#cq-tags-property) 속성에 추가되고 유형 노드로 확인됩니다 [`cq:Tag`.](#cq-tag-node-type)

## cq:태그 노드 유형 {#cq-tag-node-type}

태그의 선언은 유형 노드의 저장소에서 캡처됩니다 `cq:Tag.`

* 태그는 단순한 단어(예: `sky`) 또는 계층적 분류(예: `fruit/apple`, means both the generic fruit and the more specific apple).
* 태그는 고유으로 식별됩니다 `TagID`.
* 태그에는 제목, 지역화된 제목 및 설명과 같은 메타 정보가 선택 사항입니다. 제목은 있을 때 대신 사용자 인터페이스에 표시되어야 `TagID`합니다.

태깅 프레임워크에서는 작성자 및 사이트 방문자가 사전 정의된 특정 태그만 사용하도록 제한하는 기능도 제공합니다.

### 태그 특성 {#tag-characteristics}

* 노드 유형은 입니다 `cq:Tag`.
* 노드 이름은 The component of the [`TagID`.](#tagid)
* 항상 [`TagID`](#tagid) 네임스페이스가 [포함됩니다.](#tag-namespace)
* 속성 `jcr:title` (UI에 표시할 제목)은 선택 사항입니다.
* 이 `jcr:description` 속성은 선택 사항입니다.
* 하위 노드를 포함할 때는 [컨테이너 태그라고 합니다.](#container-tags)
* 이 태그는 분류 루트 노드라는 기본 경로 아래의 [저장소에 저장됩니다.](#taxonomy-root-node)

### 태그 ID {#tagid}

저장소의 태그 노드로 `TagID` 해결하는 경로를 식별합니다.

일반적으로 네임스페이스 `TagID` 로 `TagID` 시작하는 축약이거나 `TagID` 분류 루트 노드에서 [시작하는 절대일 수 있습니다.](#taxonomy-root-node)

컨텐츠에 태그를 지정하면 해당 속성이 아직 존재하지 않으면 [`cq:tags`](#cq-tags-property) 속성이 컨텐츠 노드에 추가되고 속성 `TagID` 의 `String` 배열 값에 추가됩니다.

이 `TagID` 는 [네임스페이스](#tag-namespace) 다음에 로컬 네임스페이스로 구성됩니다 `TagID`. [컨테이너 태그에는](#container-tags) 분류에서 계층적 순서를 나타내는 하위 태그가 있습니다. 하위 태그를 사용하여 모든 로컬 태그와 동일한 태그를 참조할 수 있습니다 `TagID`. 예를 들어, `fruit` 와 같은 하위 태그가 있는 컨테이너 태그라도 포함된 컨텐츠에 태그를 지정할 수 `fruit/apple` 있습니다 `fruit/banana`.

### 분류 루트 노드 {#taxonomy-root-node}

분류 루트 노드는 저장소의 모든 태그에 대한 기본 경로입니다. 분류 루트 노드는 유형 노드가 *아니어야* 합니다 `cq:Tag`.

AEM에서 기본 경로는 `/content/cq:tags` 이고 루트 노드는 유형입니다 `cq:Folder`.

### 태그 네임스페이스 {#tag-namespace}

네임스페이스를 통해 여러 항목을 그룹화할 수 있습니다. 가장 일반적인 사용 사례는 사이트당(예: 공개 및 내부) 또는 더 큰 응용 프로그램(예: 사이트 또는 자산)당 네임스페이스를 가지지만, 네임스페이스는 다양한 다른 요구 사항에 사용할 수 있습니다. 네임스페이스는 사용자 인터페이스에서 현재 컨텐츠에 적용할 수 있는 태그의 하위 집합(즉, 특정 네임스페이스의 태그)만 표시하는 데 사용됩니다.

태그의 네임스페이스는 분류 하위 트리에서 첫 번째 레벨이며, 분류 루트 노드 바로 아래의 [노드입니다.](#taxonomy-root-node) 네임스페이스는 상위가 노드 유형이 `cq:Tag` 아닌 유형의 `cq:Tag` 노드입니다.

모든 태그에는 네임스페이스가 있습니다. 네임스페이스를 지정하지 않으면 태그가 기본 네임스페이스에 지정되며, `TagID` 즉, `default``/content/cq:tags/default`.  이러한 경우 제목 `Standard Tags`은 기본적으로 로 설정됩니다.

### 컨테이너 태그 {#container-tags}

컨테이너 태그는 자식 노드의 수와 유형을 포함하는 유형 `cq:Tag` 의 노드로서, 이를 통해 사용자 지정 메타데이터로 태그 모델을 개선할 수 있습니다.

또한 택소노미의 컨테이너 태그(또는 super 태그)는 모든 하위 태그의 하위 합계로 사용됩니다.예를 들어 태그 지정된 컨텐츠 `fruit/apple` 에 태그되는 `fruit` 것으로 간주됩니다. 예를 들어 태그가 지정된 컨텐츠를 검색하면 태그로 지정된 컨텐츠도 찾을 `fruit` 수 있습니다 `fruit/apple`.

### 태그 ID 해결 {#resolving-tagids}

태그 ID에 콜론(`:`)이 있으면 콜론은 네임스페이스와 태그를 분리하고 이를 일반 슬래시(`/`)로 구분합니다. 태그 ID에 콜론이 없는 경우 기본 네임스페이스가 묵시적으로 사용됩니다.

태그의 표준 및 유일한 위치는 아래에 있습니다 `/content/cq:tags`.

노드를 가리키지 않는 비기존 경로 또는 경로를 참조하는 태그는 `cq:Tag` 유효하지 않은 것으로 간주되며 무시됩니다.

다음 표는 몇 가지 샘플 `TagID`과 해당 요소 및 저장소에서 `TagID` 절대 경로로 확인되는 방법을 보여줍니다.

| `TagID` | 네임스페이스 | 로컬 ID | 컨테이너 태그 | 리프 태그 | 저장소 절대 태그 경로 |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (없음) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (없음) | (없음) | (없음) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### 태그 제목 현지화 {#localization-of-tag-title}

태그에 선택 사항 제목 문자열 `jcr:title`이 포함된 경우 속성을 추가하여 표시할 제목을 현지화할 수 있습니다 `jcr:title.<locale>`.

자세한 내용은 다음을 참조하십시오.

* [API를](tagging-applications.md#tags-in-different-languages) 개발자로 사용하는 것을 설명하는 여러 언어로 된 태그
* 다른 언어로 태그 관리 - 관리자로 태그 콘솔 사용 설명

### 액세스 제어 {#access-control}

태그는 분류 루트 노드 아래의 [저장소에 노드로 존재합니다.](#taxonomy-root-node) 작성자와 사이트 방문자가 주어진 네임스페이스에 태그를 만들 수 있도록 허용하거나 거부하려면 저장소에서 적절한 ACL을 설정하여 이를 수행할 수 있습니다.

특정 태그 또는 네임스페이스에 대한 읽기 권한을 거부하면 특정 콘텐츠에 태그를 적용하는 기능이 제어됩니다.

일반적인 방법은 다음과 같습니다.

* 모든 네임스페이스에 `tag-administrators` 그룹/역할 쓰기 액세스 허용(아래에서 추가/수정 `/content/cq:tags`). 이 그룹에는 최신 AEM이 포함되어 있습니다.
* 사용자/작성자가 읽을 수 있어야 하는 모든 네임스페이스에 대한 읽기 권한을 부여할 수 있습니다(대부분 모두).
* 사용자/작성자가 사용자/작성자가 태그를 자유롭게 정의해야 하는 네임스페이스에 대한 쓰기 액세스 허용(아래`add_node` ) `/content/cq:tags/some_namespace`

## 태그가능 컨텐츠:cq:타게블 믹신 {#taggable-content-cq-taggable-mixin}

애플리케이션 개발자가 컨텐트 유형에 태깅을 첨부하려면 노드 등록([CND](https://jackrabbit.apache.org/node-type-notation.html))에 `cq:Taggable` 믹스인 또는 `cq:OwnerTaggable` 믹신이 포함되어야 합니다.

원본 `cq:OwnerTaggable` 에서 상속되는 혼합 `cq:Taggable`은 컨텐츠가 소유자/작성자에 의해 분류될 수 있음을 나타내기 위한 것입니다. AEM에서는 노드의 속성만 `cq:PageContent` 사용됩니다. 태그 `cq:OwnerTaggable` 프레임워크에서는 혼합이 필요하지 않습니다.

>[!NOTE]
>
>집계 컨텐츠 항목(또는 해당 노드)의 최상위 노드에서만 태그를 활성화하는 것이 `jcr:content` 좋습니다. 예:
>
>* 페이지 (`cq:Page`) `jcr:content`노드가 `cq:PageContent`유형(믹싱 포함)인 `cq:Taggable` 페이지입니다.
>* 자산 (`cq:Asset`) `jcr:content/metadata` 노드에 항상 `cq:Taggable` 혼합이 있는 경우


### 노드 유형 표기법(CND) {#node-type-notation-cnd}

CND 파일로 저장소에 노드 유형 정의가 있습니다. CND 표기법은 [JCR 설명서의 일부로 정의됩니다](https://jackrabbit.apache.org/node-type-notation.html).

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

이 `cq:tags` 속성은 작성자 또는 사이트 방문자가 컨텐츠에 적용할 때 하나 `String` 이상의 항목을 저장하는 데 사용되는 `TagID`배열입니다. 이 속성은 혼합으로 정의된 노드에 추가될 때만 의미가 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) 있습니다.

>[!NOTE]
>
>AEM Tagging 기능을 활용하려면 사용자 정의 개발 응용 프로그램이 태그 속성을 정의하지 않아야 `cq:tags`합니다.

## 태그 이동 및 병합 {#moving-and-merging-tags}

태깅 콘솔을 사용하여 태그를 이동하거나 병합할 때 저장소의 효과에 대한 설명입니다.

태그 A가 다음 아래에 있는 태그 B로 이동 또는 병합될 때 `/content/cq:tags`:

* 태그 A는 삭제되지 않으며 `cq:movedTo` 속성을 받습니다.
   * `cq:movedTo` 태그 B를 가리킵니다.
   * 이 속성은 태그 A가 태그 B로 이동 또는 병합되었음을 의미합니다.
   * 태그 B를 이동하면 그에 따라 이 속성이 업데이트됩니다.
   * 따라서 태그 A는 숨겨지고 태그 A를 가리키는 컨텐트 노드의 태그 ID만 확인하기 위해 보관됩니다.
   * 태그 가비지 수집기는 태그 A와 같은 태그를 더 이상 가리키지 않고 제거합니다.
   * 속성에 대한 특수 값 `cq:movedTo` 은 태그를 삭제할 때 적용되지만 보관해야 하는 하위 태그가 있기 때문에 저장소에서 제거할 수 `nirvana``cq:movedTo` 없습니다.

      >[!NOTE]
      >
      >이 `cq:movedTo` 조건 중 하나가 충족되는 경우에만 속성이 이동되거나 병합된 태그에만 추가됩니다.
      >
      > 1. 이 태그는 컨텐츠에 사용됩니다(즉, 참조가 있습니다). 또는
      > 1. 태그에 이미 이동한 하위 항목이 있습니다.


* 태그 B가 만들어지고(이동 시) 속성이 `cq:backlinks` 수신됩니다.
   * `cq:backlinks` 참조를 다른 방향으로 유지합니다. 즉, 태그 B로 이동하거나 병합한 모든 태그의 목록을 유지합니다.
   * 태그 B가 이동/병합/삭제되거나, 태그 B가 활성화된 경우에도 `cq:movedTo` 속성을 최신 상태로 유지하는 데 필요합니다. 이 경우 모든 배경 링크 태그도 활성화해야 합니다.

      >[!NOTE]
      >
      >이 `cq:backlinks` 조건 중 하나가 충족되는 경우에만 속성이 이동되거나 병합된 태그에만 추가됩니다.
      >
      > 1. 이 태그는 컨텐츠에 사용됩니다(즉, 참조가 있습니다). 또는
      > 1. 태그에 이미 이동한 하위 항목이 있습니다.


컨텐츠 노드의 `cq:tags` 속성을 읽으면 다음 해결 방법이 포함됩니다.

1. 일치하는 항목이 없으면 `/content/cq:tags`태그가 반환되지 않습니다.
1. 태그에 속성 `cq:movedTo` 집합이 있으면 참조된 태그 ID가 따릅니다.
   * 이 단계는 뒤에 나오는 태그에 속성이 있는 한 `cq:movedTo` 반복됩니다.
1. 다음 태그에 속성이 없으면 태그가 `cq:movedTo` 읽혀집니다.

태그가 이동 또는 병합되었을 때 변경 내용을 게시하려면 노드 및 모든 `cq:Tag` 해당 백링크가 복제되어야 합니다. 태그 관리 콘솔에서 태그가 활성화되면 자동으로 수행됩니다.

나중에 페이지 `cq:tags` 속성이 업데이트되어 이전 참조가 자동으로 정리됩니다. API를 통해 이동한 태그를 확인하면 대상 태그가 반환되므로 대상 태그 ID가 제공되기 때문에 트리거됩니다.
