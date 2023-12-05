---
title: 콘솔 사용자 정의
description: 작성 인스턴스의 콘솔을 사용자 정의할 수 있도록 AEM이 제공하는 다양한 옵션에 대해 알아봅니다.
exl-id: 832f9a86-07c4-4229-a0dc-8ad50a8195b0
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 87%

---

# 콘솔 사용자 정의 {#customizing-consoles}

AEM은 작성 인스턴스의 콘솔(및 [페이지 작성 기능](/help/implementing/developing/extending/page-authoring.md))을 사용자 정의할 수 있는 옵션을 제공합니다.

## Clientlibs {#clientlibs}

Clientlibs를 사용하면 기본 구현을 확장하여 새로운 기능을 제공하면서 표준 기능, 오브젝트 및 메서드를 재사용할 수 있습니다. clientlibs를 사용하여 사용자 정의하는 경우 `/apps.` 예를 들어 사용자 지정 구성 요소에 필요한 코드를 보유할 수 있습니다.

다음을 참조하십시오 [AEM에서 클라이언트측 라이브러리 as a Cloud Service 사용](/help/implementing/developing/introduction/clientlibs.md).

## 오버레이 {#overlays}

오버레이는 노드 정의를 기반으로 하며 이를 통해 `/apps`아래의 사용자 정의 기능으로 `/libs`에서 확인 가능한 표준 기능을 오버레이할 수 있습니다. 오버레이를 만들 때 원본의 1:1 사본은 필요하지 않습니다. [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md)을 통해 상속되기 때문입니다.

오버레이는 AEM 콘솔을 확장하는 데 여러 가지 방법으로 사용할 수 있습니다. 다음 섹션에서 몇 가지 예를 제공합니다.

참조: [Adobe Experience Manager as a Cloud Service용 오버레이](/help/implementing/developing/introduction/overlays.md).

>[!TIP]
>
>작성 환경을 사용자 지정하는 옵션에 관심이 있는 경우 다음을 참조하십시오. [페이지 작성 사용자 지정](/help/implementing/developing/extending/page-authoring.md).

## 콘솔의 기본 보기 사용자 정의 {#customizing-the-default-view-for-a-console}

콘솔의 기본 보기(열, 카드, 목록)를 사용자 정의할 수 있습니다.

* 다음 위치 아래에서 필수 항목을 오버레이하여 보기를 재정렬할 수 있습니다.

   * `/libs/wcm/core/content/sites/jcr:content/views`

   * 첫 번째 항목은 기본값입니다.

   * 사용 가능한 노드는 다음과 같이 사용 가능한 보기 옵션과 관련이 있습니다.

      * `column`
      * `card`
      * `list`

* 예를 들어 다음과 같은 목록의 오버레이가 있다고 가정해 보겠습니다.

   * `/apps/wcm/core/content/sites/jcr:content/views/list`

   * 다음 속성을 정의합니다.

      * **이름**: `sling:orderBefore`
      * **유형**: `String`
      * **값**: `column`

### 도구 모음에 새 작업 추가 {#add-a-new-action-to-the-toolbar}

고유한 구성 요소를 빌드하고 사용자 정의 작업을 위한 해당 클라이언트 라이브러리를 포함시킬 수 있습니다.

* 예를 들어 다음 위치에서 **소셜 미디어에 홍보** 작업을 만든다고 가정해 보겠습니다.

   * `/apps/wcm/core/clientlibs/sites/js/socialmedia.js`

   * 이를 다음과 같은 콘솔의 도구 모음 항목에 연결할 수 있습니다.

   * `/apps/<yourProject>/admin/ext/launches`

   * 예를 들어 선택 모드에서 다음과 같은 항목입니다.

   * `content/jcr:content/body/content/header/items/selection/items/socialmedia`

### 도구 모음 작업을 특정 그룹으로 제한 {#restrict-a-toolbar-action-to-a-specific-group}

사용자 정의 렌더링 조건을 사용하여 표준 작업을 오버레이하고, 렌더링되기 전에 충족되어야 하는 특정 조건을 부과할 수 있습니다.

예를 들어 다음과 같이 그룹에 따라 렌더링 조건을 제어하는 구성 요소를 만들 수 있습니다.

* `/apps/myapp/components/renderconditions/group`

이를 사이트 콘솔의 **사이트 만들기** 작업에 적용하려면 다음 작업을 수행하십시오.

* `/libs/wcm/core/content/sites`

1. 다음과 같이 오버레이를 만듭니다.

   * `/apps/wcm/core/content/sites`

1. 그런 다음 다음과 같이 작업에 대한 렌더링 조건을 추가합니다.

   * `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

이 노드의 속성을 사용하여 특정 작업을 수행할 수 있는 `groups`를 정의할 수 있습니다(예: `administrators`).

### 목록 보기에서 열 사용자 정의 {#customizing-columns-in-list-view}

목록 보기에서 열을 사용자 정의하려면 다음 작업을 수행하십시오.

1. 사용 가능한 열 목록을 오버레이합니다.

   * 다음 노드에서:

     `/apps/wcm/core/content/common/availablecolumns`

1. 새 열을 추가하거나 기존 열을 제거합니다.

추가 데이터를 삽입하려면 `pageInfoProviderType` 속성을 포함하여 [PageInfoProvider](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageInfoProvider.html)를 작성해야 합니다.

>[!NOTE]
>
>이 기능은 텍스트 필드의 열에 최적화되어 있습니다. 다른 데이터 유형의 경우 `/apps`에서 `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer`를 오버레이할 수 있습니다.

### 리소스 필터링 {#filtering-resources}

콘솔을 사용할 때 사용자는 흔히 페이지, 구성 요소 또는 자산과 같은 리소스 중에서 선택해야 합니다. 이는 작성자가 항목을 선택해야 하는 목록의 형태를 취할 수 있습니다.

목록을 적당한 크기로 유지하고 사용 사례와도 관련되게 하려면 필터를 사용자 정의 조건자 형태로 구현할 수 있습니다. 다음을 참조하십시오 [페이지 작성 사용자 지정](/help/implementing/developing/extending/page-authoring.md#filtering-resources) 을 참조하십시오.
