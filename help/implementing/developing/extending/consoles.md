---
title: 콘솔 사용자 지정
description: AEM에서 작성 인스턴스의 콘솔을 사용자 지정하는 데 제공하는 다양한 옵션에 대해 알아봅니다.
source-git-commit: f159f0ef86c2b82da4e7308a0892b4947b6e43fb
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# 콘솔 사용자 지정 {#customizing-consoles}

AEM은 콘솔(및 [페이지 작성 기능](/help/implementing/developing/extending/page-authoring.md))을 참조하십시오.

## Clientlibs {#clientlibs}

Clientlib을 사용하면 기본 구현을 확장하여 새로운 기능을 제공하는 동시에 표준 함수, 개체 및 메서드를 재사용할 수 있습니다. clientlibs를 사용하여 사용자 정의하는 경우 `/apps.` 예를 들어 사용자 지정 구성 요소에 필요한 코드를 보유할 수 있습니다.

clientlib에 대한 자세한 내용은 문서를 참조하십시오. [AEM에서 클라이언트측 라이브러리 as a Cloud Service 사용.](/help/implementing/developing/introduction/clientlibs.md)

## 오버레이 {#overlays}

오버레이는 노드 정의를 기반으로 하며, 다음과 같은 표준 기능을 오버레이할 수 있습니다. `/libs` 아래에 맞춤화된 기능을 사용하여 `/apps`. 오버레이를 만들 때 다음과 같이 원본의 1:1 사본이 필요하지 않습니다. [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md) 상속을 허용합니다.

오버레이는 AEM 콘솔을 확장하는 여러 가지 방법으로 사용할 수 있습니다. 다음 섹션에 몇 가지 예가 나와 있습니다.

오버레이에 대한 자세한 내용은 문서를 참조하십시오. [Adobe Experience Manager as a Cloud Service용 오버레이](/help/implementing/developing/introduction/overlays.md)

>[!TIP]
>
>작성 환경을 사용자 지정하는 옵션에 관심이 있는 경우 문서를 참조하십시오. [페이지 작성 사용자 지정](/help/implementing/developing/extending/page-authoring.md)

## 콘솔에 대한 기본 보기 사용자 지정 {#customizing-the-default-view-for-a-console}

콘솔의 기본 보기(열, 카드, 목록)를 사용자 지정할 수 있습니다.

* 아래에 필요한 항목을 오버레이하여 뷰의 순서를 변경할 수 있습니다.

   * `/libs/wcm/core/content/sites/jcr:content/views`

   * 첫 번째 항목이 기본값입니다.

   * 사용 가능한 노드는 사용 가능한 보기 옵션과 상호 연관됩니다.

      * `column`
      * `card`
      * `list`

* 예를 들어 목록에 대한 오버레이에서 다음을 수행합니다.

   * `/apps/wcm/core/content/sites/jcr:content/views/list`

   * 다음 속성을 정의합니다.

      * **이름**: `sling:orderBefore`
      * **유형**: `String`
      * **값**: `column`

### 도구 모음에 새 작업 추가 {#add-a-new-action-to-the-toolbar}

고유한 구성 요소를 빌드하고 사용자 지정 작업에 해당하는 클라이언트 라이브러리를 포함할 수 있습니다.

* 예를 들어 다음을 만들 수 있습니다 **소셜 미디어로 승격** 작업:

   * `/apps/wcm/core/clientlibs/sites/js/socialmedia.js`

   * 그런 다음 콘솔의 도구 모음 항목에 연결할 수 있습니다.

   * `/apps/<yourProject>/admin/ext/launches`

   * 예를 들어, 선택 모드에서는 다음을 수행합니다.

   * `content/jcr:content/body/content/header/items/selection/items/socialmedia`

### 도구 모음 작업을 특정 그룹으로 제한 {#restrict-a-toolbar-action-to-a-specific-group}

사용자 지정 렌더링 조건을 사용하여 표준 작업을 오버레이하고 렌더링하기 전에 이행해야 하는 특정 조건을 부과할 수 있습니다.

예를 들어, 그룹에 따라 렌더링 조건을 제어하는 구성 요소를 만들 수 있습니다.

* `/apps/myapp/components/renderconditions/group`

이를 다음에 적용하려면 **사이트 생성** 사이트 콘솔의 작업:

* `/libs/wcm/core/content/sites`

1. 오버레이 만들기:

   * `/apps/wcm/core/content/sites`

1. 그런 다음 작업에 대한 렌더링 조건을 추가합니다.

   * `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

이 노드의 속성을 사용하여 다음을 정의할 수 있습니다. `groups` 특정 작업을 수행할 수 있습니다. 예: `administrators`

### 목록 보기에서 열 사용자 정의 {#customizing-columns-in-list-view}

목록 보기에서 열을 사용자 정의하려면 다음을 수행합니다.

1. 사용 가능한 열 목록을 오버레이합니다.

   * 노드에서 다음을 수행합니다.

     `/apps/wcm/core/content/common/availablecolumns`

1. 새 열을 추가하거나 기존 열을 제거합니다.

추가 데이터를 삽입하려면 [PageInfoProvider](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) 포함 `pageInfoProviderType` 속성.

>[!NOTE]
>
>이 기능은 텍스트 필드 열에 최적화되었습니다. 다른 데이터 유형의 경우 오버레이할 수 있습니다 `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` 위치: `/apps`.

### 리소스 필터링 {#filtering-resources}

콘솔을 사용할 때 사용자는 종종 페이지, 구성 요소 또는 에셋과 같은 리소스에서 선택해야 합니다. 이는 작성자가 항목을 선택해야 하는 목록 형식을 취할 수 있습니다.

목록을 적절한 크기로 유지하고 사용 사례와 관련이 있도록 맞춤형 술어 형식으로 필터를 구현할 수 있습니다. 문서를 참조하십시오.[페이지 작성 사용자 지정](/help/implementing/developing/extending/page-authoring.md#filtering-resources) 을 참조하십시오.
