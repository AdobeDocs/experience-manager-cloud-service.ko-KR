---
title: AEM 태그 지정 프레임워크
description: 콘텐츠에 태그를 지정하고 AEM 태깅 인프라를 사용하여 분류 및 구성합니다.
exl-id: 25418d44-aace-4e73-be1a-4b1902f40403
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---

# AEM 태깅 프레임워크 {#aem-tagging-framework}

태깅을 사용하면 컨텐츠를 분류하고 구성할 수 있습니다. 태그는 네임스페이스와 분류법으로 분류할 수 있습니다. 태그 사용에 대한 자세한 내용은 다음을 참조하십시오.

* 콘텐츠 작성자로 콘텐츠에 태그를 지정하는 방법에 대한 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/sites-console/tags.md)을 참조하세요.
* 태그 작성 및 관리 방법과 컨텐츠 태그가 적용되는 항목에 대한 관리자 관점의 태그 관리를 참조하십시오.

이 문서에서는 AEM에서 태그 지정을 지원하는 기본 프레임워크와 개발자로 사용하는 방법에 대해 중점적으로 다룹니다.

## 소개 {#introduction}

콘텐츠에 태그를 지정하고 AEM 태그 지정 인프라를 사용하려면 다음을 수행하십시오.

* 태그는 [분류 루트 노드 아래에 [`cq:Tag`](#cq-tag-node-type) 유형의 노드로 있어야 합니다.](#taxonomy-root-node)
* 태그가 지정된 콘텐츠 노드 `NodeType`에 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin이 포함되어야 합니다.
* [`TagID`](#tagid)이(가) 콘텐츠 노드의 [`cq:tags`](#cq-tags-property) 속성에 추가되고 [`cq:Tag`.](#cq-tag-node-type) 유형의 노드로 확인됩니다.

## cq:태그 노드 유형 {#cq-tag-node-type}

태그의 선언은 `cq:Tag.` 유형의 노드에서 리포지토리에 캡처됩니다.

* 태그는 간단한 단어(예: `sky`)이거나 계층 분류법(예: `fruit/apple`, 일반 과일과 더 구체적인 사과를 모두 의미)을 나타낼 수 있습니다.
* 태그는 고유한 `TagID`(으)로 식별됩니다.
* 태그에는 제목, 현지화된 제목 및 설명과 같은 선택적 메타 정보가 있습니다. 존재하는 경우 제목은 `TagID` 대신 사용자 인터페이스에 표시되어야 합니다.

또한 태깅 프레임워크는 작성자 및 사이트 방문자가 사전 정의된 특정 태그만 사용하도록 제한합니다.

### 태그 특성 {#tag-characteristics}

* 노드 형식은 `cq:Tag`입니다.
* 노드 이름은 [`TagID`.](#tagid)의 구성 요소입니다.
* [`TagID`](#tagid)은(는) 항상 [네임스페이스를 포함합니다.](#tag-namespace)
* `jcr:title` 속성(UI에 표시할 제목)은 선택 사항입니다.
* `jcr:description` 속성은 선택 사항입니다.
* 자식 노드를 포함하는 경우 [컨테이너 태그라고 합니다.](#container-tags)
* 태그는 [분류법 루트 노드라는 기본 경로 아래의 저장소에 저장됩니다.](#taxonomy-root-node)

### 태그 ID {#tagid}

`TagID`은(는) 저장소의 태그 노드로 확인되는 경로를 식별합니다.

일반적으로 `TagID`은(는) 네임스페이스로 시작하는 축약 `TagID`이거나 [분류법 루트 노드에서 시작하는 절대 `TagID`일 수 있습니다.](#taxonomy-root-node)

컨텐츠에 태그를 지정할 때 아직 없으면 [`cq:tags`](#cq-tags-property) 속성이 컨텐츠 노드에 추가되고 `TagID`이(가) 속성의 `String` 배열 값에 추가됩니다.

`TagID`은(는) [네임스페이스](#tag-namespace) 다음에 로컬 `TagID`이(가) 옵니다. [컨테이너 태그](#container-tags)에는 분류법의 계층 순서를 나타내는 하위 태그가 있습니다. 하위 태그를 사용하여 모든 로컬 `TagID`과(와) 동일한 태그를 참조할 수 있습니다. 예를 들어 `fruit/apple` 및 `fruit/banana`과(와) 같은 하위 태그가 있는 컨테이너 태그인 경우에도 콘텐츠에 `fruit`을(를) 사용하여 태그를 지정할 수 있습니다.

### 분류 루트 노드 {#taxonomy-root-node}

분류 루트 노드는 저장소의 모든 태그에 대한 기본 경로입니다. 분류법 루트 노드는 *not*&#x200B;이(가) `cq:Tag` 유형의 노드여야 합니다.

AEM에서 기본 경로는 `/content/cq:tags`이고 루트 노드는 `cq:Folder` 유형입니다.

### 태그 네임스페이스 {#tag-namespace}

네임스페이스를 사용하면 항목을 그룹화할 수 있습니다. 가장 일반적인 사용 사례는 사이트당(예: 공개 및 내부) 또는 더 큰 애플리케이션당(예: 사이트 또는 Assets)의 네임스페이스를 사용하는 것이지만 다양한 다른 요구 사항에 맞게 네임스페이스를 사용할 수 있습니다. 네임스페이스는 사용자 인터페이스에서 현재 콘텐츠에 적용할 수 있는 태그의 하위 집합(즉, 특정 네임스페이스의 태그)만 표시하는 데 사용됩니다.

태그의 네임스페이스는 분류법 하위 트리의 첫 번째 수준이며 [분류법 루트 노드 바로 아래에 있는 노드입니다.](#taxonomy-root-node) 네임스페이스는 부모 노드가 `cq:Tag` 노드 유형이 아닌 `cq:Tag` 유형의 노드입니다.

모든 태그에는 네임스페이스가 있습니다. 네임스페이스를 지정하지 않으면 태그는 기본 네임스페이스인 `TagID` `default`, 즉 `/content/cq:tags/default`에 할당됩니다. 이 경우 Title의 기본값은 `Standard Tags`입니다.

### 컨테이너 태그 {#container-tags}

컨테이너 태그는 하위 노드의 수와 유형을 포함하는 `cq:Tag` 유형의 노드입니다. 따라서 사용자 지정 메타데이터로 태그 모델을 개선할 수 있습니다.

또한 분류법의 컨테이너 태그(또는 슈퍼 태그)는 모든 하위 태그의 하위 합계 역할을 합니다. 예를 들어 `fruit/apple`(으)로 태그가 지정된 콘텐츠는 `fruit`(으)로도 태그가 지정된 것으로 간주됩니다. 즉, `fruit`(으)로 태그가 지정된 콘텐츠를 검색하면 `fruit/apple`(으)로 태그가 지정된 콘텐츠도 검색됩니다.

### TagID 확인 {#resolving-tagids}

태그 ID에 콜론(`:`)이 포함되어 있는 경우 콜론은 태그나 하위 분류법에서 네임스페이스를 구분하고 일반 슬래시(`/`)로 구분합니다. 태그 ID에 콜론이 없으면 기본 네임스페이스가 암시됩니다.

태그의 표준 및 유일한 위치는 `/content/cq:tags` 미만입니다.

존재하지 않는 경로 또는 `cq:Tag` 노드를 가리키지 않는 경로를 참조하는 태그는 잘못된 것으로 간주되며 무시됩니다.

다음 표는 일부 샘플 `TagID`과(와) 해당 요소 및 `TagID`이(가) 리포지토리의 절대 경로로 확인되는 방식을 보여 줍니다.

| `TagID` | 네임스페이스 | 로컬 ID | 컨테이너 태그 | 리프 태그 | 저장소 절대 태그 경로 |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (없음) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (없음) | (없음) | (없음) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### 태그 제목의 현지화 {#localization-of-tag-title}

태그에 선택적 제목 문자열 `jcr:title`이(가) 포함된 경우 `jcr:title.<locale>` 속성을 추가하여 표시할 제목을 현지화할 수 있습니다.

자세한 내용은 다음을 참조하십시오.

* [다른 언어의 태그](tagging-applications.md#tags-in-different-languages)에서는 개발자로서 API 사용에 대해 설명합니다.
* 다른 언어로 태그 관리 - 태깅 콘솔을 관리자로 사용하는 방법 설명

### 액세스 제어 {#access-control}

태그는 [분류 루트 노드 아래의 저장소에 노드로 존재합니다.](#taxonomy-root-node) 작성자 및 사이트 방문자가 지정된 네임스페이스에서 태그를 만들 수 있도록 허용하거나 거부하는 작업은 저장소에서 적절한 ACL을 설정하여 수행할 수 있습니다.

특정 태그 또는 네임스페이스에 대한 읽기 권한을 거부하면 특정 콘텐츠에 태그를 적용하는 기능이 제어됩니다.

일반적인 방법은 다음과 같습니다.

* `tag-administrators` 그룹/역할에 모든 네임스페이스에 대한 쓰기 액세스 권한을 허용합니다(`/content/cq:tags` 아래 추가/수정). 이 그룹은 AEM과 함께 제공됩니다.
* 사용자/작성자가 읽을 수 있어야 하는 모든 네임스페이스(대부분 모든 네임스페이스)에 대한 읽기 액세스를 허용합니다.
* 사용자/작성자가 태그를 사용자/작성자가 자유롭게 정의할 수 있는 네임스페이스에 대한 쓰기 액세스 권한을 사용자/작성자(`/content/cq:tags/some_namespace`의 `add_node`)에게 부여합니다.

## 태그 지정 가능 콘텐츠 : cq:Taggable Mixin {#taggable-content-cq-taggable-mixin}

응용 프로그램 개발자가 콘텐츠 형식에 태깅을 첨부하려면 노드의 등록([CND](https://jackrabbit.apache.org/jcr/node-type-notation.html))에 `cq:Taggable` mixin 또는 `cq:OwnerTaggable` mixin이 포함되어야 합니다.

`cq:Taggable`에서 상속되는 `cq:OwnerTaggable` mixin은 소유자/작성자가 콘텐츠를 분류할 수 있음을 나타내기 위한 것입니다. AEM에서는 `cq:PageContent` 노드의 특성만 사용합니다. 태그 지정 프레임워크에 `cq:OwnerTaggable` mixin이 필요하지 않습니다.

>[!NOTE]
>
>집계된 콘텐츠 항목의 최상위 노드(또는 `jcr:content` 노드)에서만 태그를 활성화하는 것이 좋습니다. 예를 들면 다음과 같습니다.
>
>* `jcr:content`노드가 `cq:Taggable` mixin을 포함하는 유형 `cq:PageContent`인 페이지(`cq:Page`)입니다.
>* `jcr:content/metadata` 노드에 항상 `cq:Taggable` mixin이 있는 Assets(`cq:Asset`).

### 노드 유형 표기법(CND) {#node-type-notation-cnd}

노드 유형 정의는 저장소에 CND 파일로 존재합니다. CND 표기법은 [JCR 설명서](https://jackrabbit.apache.org/jcr/node-type-notation.html)의 일부로 정의됩니다.

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

`cq:tags` 속성은 작성자 또는 사이트 방문자가 콘텐츠에 적용할 때 하나 이상의 `TagID`을(를) 저장하는 데 사용되는 `String` 배열입니다. 속성은 [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin으로 정의된 노드에 추가되는 경우에만 의미가 있습니다.

>[!NOTE]
>
>AEM 태그 지정 기능을 사용하려면 사용자 지정 개발 응용 프로그램에서 `cq:tags` 이외의 태그 속성을 정의하면 안 됩니다.

## 태그 이동 및 병합 {#moving-and-merging-tags}

다음은 태깅 콘솔을 사용하여 태그를 이동하거나 병합할 때 저장소에 있는 효과에 대한 설명입니다.

태그 A를 `/content/cq:tags` 아래의 태그 B로 이동하거나 병합하는 경우:

* 태그 A가 삭제되지 않고 `cq:movedTo` 속성을 받습니다.
   * 태그 B를 `cq:movedTo`포인트 가리킵니다.
   * 이 속성은 태그 A가 태그 B로 이동 또는 병합되었음을 의미합니다.
   * 태그 B를 이동하면 그에 따라 이 속성이 업데이트됩니다.
   * 따라서 태그 A는 숨겨지며 저장소에만 보관되므로 태그 A를 가리키는 콘텐츠 노드의 태그 ID를 확인할 수 있습니다.
   * 태그 가비지 수집기는 더 이상 콘텐츠 노드가 이들을 가리키지 않으면 태그 A와 같은 태그를 제거합니다.
   * `cq:movedTo` 속성에 대한 특수 값은 `nirvana`입니다. 이 값은 태그가 삭제될 때 적용되지만 보관해야 하는 `cq:movedTo`이(가) 있는 하위 태그가 있으므로 리포지토리에서 제거할 수 없습니다.

     >[!NOTE]
     >
     >`cq:movedTo` 속성은 다음 조건 중 하나가 충족되는 경우에만 이동하거나 병합된 태그에 추가됩니다.
     >
     > 1. 태그는 콘텐츠에 사용됩니다(참조가 있음을 의미함). 또는
     > 1. 태그에 이미 이동된 하위 항목이 있습니다.
     >
* 태그 B가 만들어지고(이동이 있는 경우) `cq:backlinks` 속성을 받습니다.
   * `cq:backlinks`이(가) 다른 방향으로 참조를 유지합니다. 즉, 태그 B로 이동되거나 태그 B와 병합된 모든 태그의 목록을 유지합니다.
   * 이 기능은 태그 B가 이동/병합/삭제되거나 태그 B가 활성화된 경우에도 `cq:movedTo` 속성을 최신 상태로 유지하는 데 주로 필요합니다. 이 경우 모든 백링크 태그도 활성화해야 합니다.

     >[!NOTE]
     >
     >`cq:backlinks` 속성은 다음 조건 중 하나가 충족되는 경우에만 이동하거나 병합된 태그에 추가됩니다.
     >
     > 1. 태그는 콘텐츠에 사용됩니다(참조가 있음을 의미함). 또는
     > 1. 태그에 이미 이동된 하위 항목이 있습니다.

콘텐츠 노드의 `cq:tags` 속성을 읽으면 다음 해결 방법이 포함됩니다.

1. `/content/cq:tags`에 일치하는 항목이 없으면 태그가 반환되지 않습니다.
1. 태그에 `cq:movedTo` 속성이 설정되어 있으면 참조된 태그 ID가 적용됩니다.
   * 뒤에 오는 태그에 `cq:movedTo` 속성이 있는 한 이 단계를 반복합니다.
1. 뒤에 오는 태그에 `cq:movedTo` 속성이 없으면 태그를 읽습니다.

태그를 이동하거나 병합할 때 변경 내용을 게시하려면 `cq:Tag` 노드 및 모든 백링크를 복제해야 합니다. 이 복제는 태그가 태그 관리 콘솔에서 활성화될 때 자동으로 수행됩니다.

나중에 페이지의 `cq:tags` 속성을 업데이트하면 이전 참조가 자동으로 정리됩니다. API를 통해 이동된 태그를 확인하면 대상 태그가 반환되어 대상 태그 ID가 제공되므로 정리가 트리거됩니다.
