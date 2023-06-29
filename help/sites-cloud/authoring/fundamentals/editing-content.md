---
title: 페이지 콘텐츠 편집
description: 페이지를 생성하면 콘텐츠를 편집하여 필요한 업데이트를 수행할 수 있습니다.
exl-id: 8af0f621-14e8-4605-a51a-a3be21f19092
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2990'
ht-degree: 68%

---

# 페이지 콘텐츠 편집{#editing-page-content}

페이지가 만들어지면(launch 또는 live copy의 일부 또는 신규) 콘텐츠를 편집하여 필요한 업데이트 작업을 수행할 수 있습니다.

콘텐츠는 페이지로 끌 수 있는 [구성 요소](/help/sites-cloud/authoring/features/components-console.md)(콘텐츠 유형에 맞는)를 사용하여 추가됩니다. 그런 다음 그 자리에서 편집하거나, 이동하거나 삭제할 수 있습니다.

>[!NOTE]
>
>페이지를 편집하기 위해서는 계정에 적절한 액세스 권한과 사용 권한이 있어야 합니다.
>
>문제가 발생하면 시스템 관리자에게 문의하십시오.
<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to edit pages.
-->

>[!NOTE]
>
>페이지 및/또는 템플릿이 적절하게 설정된 경우 편집할 때 [응답형 레이아웃](/help/sites-cloud/authoring/features/responsive-layout.md)을 사용할 수 있습니다.

>[!TIP]
>
>**편집** 모드에서는 콘텐츠에 링크가 표시되지만 **액세스할 수 없습니다**. 콘텐츠의 링크를 사용하여 탐색하려면 [미리보기 모드](#previewing-pages)를 사용하십시오.

## 페이지 도구 모음 {#page-toolbar}

페이지 도구 모음에서는 페이지 구성에 따라 적절한 기능에 대한 액세스 권한을 제공합니다.

![페이지 도구 모음](/help/sites-cloud/authoring/assets/editing-page-toolbar.png)

도구 모음에서는 다양한 옵션에 액세스할 수 있습니다. 현재 컨텍스트 및 구성에 따라 일부 옵션을 사용할 수 없을 수도 있습니다.

* **사이드 패널 전환**

  [에셋 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser), [구성 요소 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) 및 [콘텐츠 트리](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree)를 보유하는 사이드 패널을 열고 닫습니다.

  ![사이드 패널 전환](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

* **페이지 정보**

  에 대한 액세스 권한 제공 [페이지 정보](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) 메뉴(페이지 세부 사항 및 페이지 정보 보기 및 편집, 페이지 속성 보기, 페이지 게시/게시 취소 등 페이지에서 수행할 수 있는 작업 포함).

  ![페이지 정보 버튼](/help/sites-cloud/authoring/assets/page-information-icon.png)

* **에뮬레이터**

  다른 디바이스에서 페이지의 디자인을 에뮬레이트하는 데 사용되는 [에뮬레이터 도구 모음](/help/sites-cloud/authoring/features/responsive-layout.md#selecting-a-device-to-emulate)을 전환합니다. 이는 레이아웃 모드에서 자동으로 전환됩니다.

  ![에뮬레이터 버튼](/help/sites-cloud/authoring/assets/emulator.png)

* **ContextHub**

  [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md)를 엽니다. [미리보기 모드]에서만 사용 가능합니다.

  ![Context Hub 버튼](/help/sites-cloud/authoring/assets/context-hub.png)

* **페이지 제목**

  이는 순전히 정보 제공용입니다.

  ![페이지 제목](/help/sites-cloud/authoring/assets/page-title.png)

* **모드 선택기**

  현재 [모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)를 표시하고 편집, 레이아웃, 타임워프 또는 타겟팅과 같은 다른 모드를 선택할 수 있습니다.

  ![모드 선택기 버튼](/help/sites-cloud/authoring/assets/mode-selector.png)

* **미리보기**

  [미리보기 모드](#preview-mode)를 활성화합니다. 이렇게 하면 페이지가 게시될 때 표시되는 것과 같이 표시됩니다.

  ![미리보기 버튼](/help/sites-cloud/authoring/assets/preview.png)

* **주석**

  다음을 추가할 수 있습니다. [주석](/help/sites-cloud/authoring/fundamentals/annotations.md) 페이지를 검토할 때 페이지로 이동합니다. 첫 번째 주석 다음에 아이콘은 페이지의 주석 수를 나타내는 숫자로 전환됩니다.

  ![주석 버튼](/help/sites-cloud/authoring/assets/annotations.png)

### 상태 알림 {#status-notification}

페이지가 [워크플로](/help/sites-cloud/authoring/workflows/overview.md) 또는 다중 워크플로의 일부인 경우 페이지를 편집할 때 화면 맨 위에 있는 알림 표시줄에 이 정보가 표시됩니다.

![워크플로 알림](/help/sites-cloud/authoring/assets/editing-workflow-notification.png)

>[!NOTE]
>
>상태 표시줄은 적절한 권한이 있는 사용자 계정에만 표시됩니다.

알림은 페이지에 대해 실행 중인 워크플로를 나열합니다. 사용자가 현재 워크플로 단계에 참여 중인 경우 옵션은 [워크플로 상태](/help/sites-cloud/authoring/workflows/participating.md)에 영향을 주며 워크플로에 대한 자세한 정보는 다음과 같이 확인할 수 있습니다.

* **완료** - **작업 항목 완료** 대화 상자를 엽니다.
* **위임** - **작업 항목 완료** 대화 상자를 엽니다.
* **세부 사항 보기** - 워크플로의 **세부 사항** 창을 엽니다.

알림 표시줄을 통해 워크플로 단계를 완료하고 위임하는 것은 알림 받은 편지함에서 [워크플로에 참여](/help/sites-cloud/authoring/workflows/participating.md)할 때와 같은 방식입니다.

페이지에 여러 개의 워크플로가 있는 경우 알림 오른쪽 끝에 화살표 버튼과 함께 워크플로 개수가 표시되어 워크플로를 스크롤할 수 있습니다.

![여러 워크플로 알림](/help/sites-cloud/authoring/assets/editing-workflow-notification-multiple.png)

## 구성 요소 플레이스홀더 {#component-placeholder}

구성 요소 자리 표시자는 구성 요소를 놓을 때 현재 마우스로 가리키고 있는 구성 요소 위에 있는 위치를 보여 주는 표시기입니다.

* 페이지에 새 구성 요소를 추가할 때(구성 요소 브라우저에서 드래그):

  ![페이지에 새 구성 요소를 추가할 때의 플레이스홀더](/help/sites-cloud/authoring/assets/editing-component-placeholder.png)

* 기존 구성 요소를 이동할 때:

  ![페이지에서 기존 구성 요소를 이동할 때의 플레이스홀더](/help/sites-cloud/authoring/assets/editing-component-placeholder-existing.png)

## 구성 요소 삽입 {#inserting-a-component}

### 구성 요소 브라우저에서 구성 요소 삽입 {#inserting-a-component-from-the-components-browser}

[구성 요소 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)를 사용하여 새 구성 요소를 추가할 수 있습니다. 다음 [구성 요소 플레이스홀더](#component-placeholder) 구성 요소가 있는 위치를 보여 줍니다.

1. 페이지가 [**편집** 모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)인지 확인합니다.
1. [구성 요소 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)를 엽니다.
1. 필요한 구성 요소를 [필요한 위치](#component-placeholder)로 드래그합니다.
1. [편집](#edit-content) 구성 요소.

>[!NOTE]
>
>모바일 디바이스에서 구성 요소 브라우저가 전체 화면을 채웁니다. 구성 요소를 드래그하기 시작하면 브라우저가 닫히고 구성 요소를 배치할 수 있도록 페이지가 다시 표시됩니다.

### 단락 시스템에서 구성 요소 삽입 {#inserting-a-component-from-the-paragraph-system}

단락 시스템의 **구성 요소를 여기로 드래그하십시오.** 상자를 사용하여 새 구성 요소를 추가할 수 있습니다.

1. 페이지가 [**편집** 모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)인지 확인합니다.
1. 단락 시스템에서 새 구성 요소를 선택하고 추가하는 두 가지 방법이 있습니다.

   * 다음 항목 선택 **구성 요소 삽입** 기존 구성 요소의 도구 모음 또는 **여기에 구성 요소 드래그** 상자.

     ![구성 요소 삽입](/help/sites-cloud/authoring/assets/editing-insert-component.png)

   * 데스크탑 디바이스를 사용하는 경우 **구성 요소를 여기로 드래그하십시오.** 상자를 더블 클릭합니다.

   * 필수 구성 요소를 선택할 수 있는 **새 구성 요소 삽입** 대화 상자가 열립니다.

     ![새 구성 요소 삽입 대화 상자](/help/sites-cloud/authoring/assets/editing-insert-component-selection.png)

1. 선택한 구성 요소가 페이지 하단에 추가됩니다. [편집](#edit-content) 필요한 구성 요소입니다.

### 에셋 브라우저를 사용하여 구성 요소 삽입 {#inserting-a-component-using-the-assets-browser}

[에셋 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser)에서 에셋을 끌어 페이지에 새 구성 요소를 추가할 수도 있습니다. 이렇게 하면 적절한 유형의 새 구성 요소가 자동으로 만들어집니다(에셋이 들어 있음).

이 동작은 설치에 대해 구성할 수 있습니다. 자세한 내용은 단락 시스템 구성 및 에셋 드래그를 통한 구성 요소 인스턴스 생성을 참조하십시오. <!--This behavior can be configured for your installation. See [Configuring a Paragraph System so that Dragging an Asset Creates a Component Instance](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) for further details.-->

위의 에셋 유형 중 하나를 끌어 구성 요소를 만들려면

1. 페이지가 [**편집** 모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)인지 확인합니다.
1. [에셋 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser)를 엽니다.
1. 필요한 에셋을 필요한 위치로 드래그합니다. 다음 [구성 요소 플레이스홀더](#component-placeholder) 구성 요소가 있는 위치를 보여 줍니다.

   에셋 유형에 적절한 구성 요소가 필요한 위치에 만들어집니다. 이 구성 요소에는 선택한 에셋이 들어 있습니다.

1. [편집](#edit-content) 필요한 경우 구성 요소입니다.

>[!NOTE]
>
>모바일 디바이스에서 에셋 브라우저가 전체 화면을 채웁니다. 에셋을 드래그하면 브라우저가 닫히고 에셋을 배치할 수 있도록 페이지가 다시 표시됩니다.

에셋을 검색할 때 에셋을 빠르게 변경해야 하는 경우, 에셋의 이름 옆에 있는 편집 아이콘을 클릭하여 [에셋 편집기](/help/assets/manage-digital-assets.md)를 브라우저에서 직접 시작할 수 있습니다.

![에셋 편집 버튼](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## 구성 요소 도구 모음 {#component-toolbar}

구성 요소를 선택하면 도구 모음이 열립니다. 이 도구 모음에서는 구성 요소에서 수행할 수 있는 다양한 작업에 액세스할 수 있습니다.

사용자가 사용할 수 있는 실제 작업은 적절히 표시되며 일부 작업은 여기에서 설명되지 않을 수 있습니다.

![구성 요소 도구 모음](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

* **편집**

  [구성 요소 유형에 따라 다름](/help/sites-cloud/authoring/fundamentals/components.md), 이렇게 하면 다음 작업을 수행할 수 있습니다. [구성 요소의 콘텐츠 편집](#edit-content). 종종 도구 모음이 제공됩니다.

  ![편집 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-edit.png)

* **구성**

  [구성 요소 유형에 따라 다름](/help/sites-cloud/authoring/fundamentals/components.md)를 통해 구성 요소의 속성을 편집하고 구성할 수 있습니다. 종종 대화 상자가 열립니다.

  ![구성 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-configure.png)

* **복사**

  구성 요소가 클립보드에 복사됩니다. 붙여넣기 작업 후에는 원래 구성 요소가 유지됩니다.

  ![복사 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-copy.png)

* **잘라내기**

  구성 요소가 클립보드에 복사됩니다. 붙여넣기 작업 후 원래 구성 요소가 제거됩니다.

  ![잘라내기 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-cut.png)

* **삭제**

  이 경우 확인 표시가 있는 페이지에서 구성 요소가 삭제됩니다.

  ![삭제 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-delete.png)

* **구성 요소 삽입**

  그러면 대화 상자가 열립니다 [새 구성 요소 추가](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-from-the-paragraph-system).

  ![삽입 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-insert.png)

* **붙여넣기**

  구성 요소를 클립보드에서 페이지로 붙여넣게 됩니다. 원본이 남아 있는지 여부는 복사 또는 잘라내기 중 어느 것을 사용했는지 여부에 따라 달라집니다.

   * 동일한 페이지나 다른 페이지에 붙여넣을 수 있습니다.
   * 붙여넣은 항목은 붙여넣기 작업을 선택한 항목 위에 붙여넣습니다.
   * 클립보드에 콘텐츠가 있는 경우에만 붙여넣기 작업이 표시됩니다.

  ![붙여넣기 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-paste.png)

  >[!NOTE]
  >
  >잘라내기/복사 작업 전에 이미 열려 있는 다른 페이지에 붙여넣으면 해당 페이지를 새로 고쳐 붙여넣은 콘텐츠를 볼 수 있습니다.

* **그룹**

  여러 구성 요소를 한 번에 선택할 수 있도록 해 줍니다. **Control+Click** 또는 **Command+Click**&#x200B;하여 데스크탑 디바이스에서도 동일한 작업을 수행할 수 있습니다.

  ![그룹 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-group.png)

* **상위**

  선택한 구성 요소의 상위 구성 요소를 선택할 수 있습니다.

  ![상위 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-parent.png)

* **레이아웃**

  이를 통해 다음을 수정할 수 있습니다. [레이아웃](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout) 선택한 구성 요소. 이 기능은 선택한 구성 요소에만 적용되며 [레이아웃 모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) 전체 페이지.

  ![레이아웃 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

* **경험 조각 변형으로 변환**

  이 작업에서는 선택한 구성 요소에서 새 [경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)을 생성하거나 기존 경험 조각에 추가할 수 있습니다.

  ![경험 조각 변형으로 변환 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-xf.png)

## 콘텐츠 편집 {#edit-content}

구성 요소에서 콘텐츠를 추가 및/또는 편집하는 방법에는 두 가지가 있습니다.

* [편집하려면 구성 요소 대화 상자](#component-edit-dialog)를 엽니다.
* 에셋 브라우저에서 [에셋을 끌어다 놓아](#drag-and-drop-assets-into-component) 콘텐츠를 바로 추가합니다.

### 구성 요소 편집 대화 상자 {#component-edit-dialog}

[구성 요소 도구 모음의 편집(연필) 아이콘](#component-toolbar)을 사용하여 콘텐츠를 편집할 구성 요소를 열 수 있습니다.

정확한 편집 옵션은 구성 요소에 따라 다릅니다. 일부 구성 요소의 경우 [모든 작업은 전체 화면 모드에서만 사용할 수 있습니다.](#edit-content-full-screen-mode). 예:

* 텍스트 구성 요소

  ![텍스트 구성 요소의 도구 모음](/help/sites-cloud/authoring/assets/editing-text-component-toolbar.png)

* 이미지 구성 요소

  ![이미지 구성 요소의 도구 모음](/help/sites-cloud/authoring/assets/editing-image-component-toolbar.png)

  >[!NOTE]
  >
  >빈 이미지 구성 요소에서는 편집기가 작동하지 않습니다.
  >
  >편집을 시작할 수 있으려면 먼저 이미지를 구성 요소에 드래그하거나 업로드해야 합니다.

* 이미지 구성 요소 - 전체 화면

  [전체 화면 모드 시작](#edit-content-full-screen-mode) 이미지 구성 요소의 경우 이미지를 편집할 공간을 더 확보하고 다음과 같은 추가 편집 옵션을 표시합니다. **맵 실행** 및 **확대/축소 재설정**. In addition, full screen allows for crop presets to be selected.

  ![이미지 구성 요소의 전체 화면 모드](/help/sites-cloud/authoring/assets/editing-image-component-full-screen.png)

* 두 개 이상의 기본 구성 요소에서 만들어진 구성 요소는 우선 원하는 편집 옵션 세트를 확인할 것을 사용자에게 요구합니다.

### 구성 요소로 에셋 드래그 앤 드롭 {#drag-and-drop-assets-into-component}

특정 구성 요소 유형(이미지 등)의 경우 콘텐츠를 업데이트하려면 에셋 브라우저의 에셋을 구성 요소에 바로 드래그하여 놓으면 됩니다.

## 전체 화면 모드로 콘텐츠 편집 {#edit-content-full-screen-mode}

모든 구성 요소에 대해 다음 아이콘으로 전체 화면 모드에 액세스(및 액세스 종료)할 수 있습니다.

![전체 화면 버튼](/help/sites-cloud/authoring/assets/editing-full-screen.png)

예를 들어 **텍스트** 구성 요소:

![전체 화면의 텍스트 구성 요소](/help/sites-cloud/authoring/assets/editing-text-full-screen.png)

>[!NOTE]
>
>일부 구성 요소의 경우, 전체 화면 모드는 기본 즉석 편집기보다 사용할 수 있는 옵션이 더 많습니다.

## 구성 요소 이동 {#moving-a-component}

단락 구성 요소 이동

1. 탭한 상태로 유지하거나 클릭앤한 상태로 유지할 단락을 선택합니다.
1. 단락을 새 위치로 드래그합니다. AEM에서 단락을 둘 수 있는 위치를 보여 줍니다. 단락을 원하는 위치에 놓습니다.

   ![구성 요소 이동](/help/sites-cloud/authoring/assets/editing-moving-component.png)

1. 단락이 이동됩니다.

>[!TIP]
>
>[잘라내기 및 붙여넣기](#component-toolbar)를 사용하여 구성 요소를 이동할 수도 있습니다.

## 구성 요소 레이아웃 편집 {#edit-component-layout}

구성 요소를 조정하기 위해 편집에서 [레이아웃 모드](/help/sites-cloud/authoring/features/responsive-layout.md)로 반복적으로 전환하는 대신 해당 구성 요소의 레이아웃을 변경하려는 구성 요소에 대해 **레이아웃** 작업을 선택하면 [편집 모드]를 벗어나지 않고 시간을 절약할 수 있습니다.

1. Sites 콘솔의 **편집** 모드에 있는 경우 구성 요소를 선택하면 구성 요소의 도구 모음이 표시됩니다.

   ![페이지 구성 요소의 구성 요소 도구 모음](/help/sites-cloud/authoring/assets/editing-layout-toolbar.png)

   **레이아웃** 작업을 클릭하거나 탭하여 구성 요소의 레이아웃을 조정합니다.

   ![구성 요소 도구 모음의 레이아웃 버튼](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

1. 레이아웃 작업을 선택하면 다음 작업을 수행합니다.

   * 컴포넌트 디스플레이의 크기 조정 핸들.
   * 에뮬레이터 도구 모음이 화면 맨 위에 표시됩니다.
   * 표준 편집 작업 대신 레이아웃 작업이 구성 요소 도구 모음에 표시됩니다.

   ![레이아웃 모드의 구성 요소](/help/sites-cloud/authoring/assets/editing-layout-mode.png)

   [레이아웃 모드](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode)에서처럼 구성 요소의 레이아웃을 수정할 수 있습니다.

1. 필요한 레이아웃 변경을 만든 후 구성 요소 작업 메뉴에서 **닫기** 버튼을 클릭하여 구성 요소 레이아웃 수정을 중지할 수 있습니다. 구성 요소의 도구 모음이 일반적인 편집 상태로 돌아갑니다.

   ![페이지 구성 요소의 구성 요소 도구 모음](/help/sites-cloud/authoring/assets/editing-layout-exit.png)

>[!TIP]
>
>레이아웃 작업은 선택한 구성 요소의 범위로 제한됩니다. 예를 들어, 한 구성 요소의 레이아웃을 편집한 다음 다른 구성 요소를 클릭하면 새로 선택한 구성 요소에 대해 표준 편집 도구 모음(레이아웃 도구 모음이 아님)이 표시되고 크기 조정 핸들 및 에뮬레이터 도구 모음이 사라집니다.
>
>여러 구성 요소에 영향을 주면서 페이지의 전체 레이아웃을 편집해야 하는 경우 [레이아웃 모드](/help/sites-cloud/authoring/features/responsive-layout.md).

## 상속된 구성 요소 {#inherited-components}

상속은 콘텐츠를 한 구성 요소에서 다른 구성 요소로 자동으로 푸시할 수 있는 메커니즘입니다. 상속된 구성 요소는 다음을 포함하여 다양한 시나리오의 제품일 수 있습니다.

* [다중 사이트 관리](/help/sites-cloud/administering/msm/overview.md)
* [Launch](/help/sites-cloud/authoring/launches/overview.md)(live copy을 기반으로 할 때).

상속을 취소(그런 다음 다시 활성화)할 수 있습니다. 구성 요소에 따라 구성 요소가 Live Copy 또는 론치(Live Copy 기반)의 일부인 페이지에 있는 경우 구성 요소 도구 모음에서 상속을 사용할 수 있습니다.

![상속 관계를 보여 주는 구성 요소 도구 모음](/help/sites-cloud/authoring/assets/editing-component-toolbar-inheritance.png)

예:

* 상속 취소

  ![상속 취소 버튼](/help/sites-cloud/authoring/assets/editing-cancel-inheritance.png)

* 상속 재활성화(상속이 이미 취소된 경우)

  ![상속 재활성화 버튼](/help/sites-cloud/authoring/assets/editing-reenable-inheritance.png)

* 롤라웃 작업은 블루프린트 또는 Live Copy 소스에서도 사용 가능합니다.

  ![롤아웃 버튼](/help/sites-cloud/authoring/assets/editing-rollout.png)

## 페이지 템플릿 편집 {#editing-the-page-template}

[페이지 정보 메뉴](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information)에서 **템플릿 편집**&#x200B;을 선택하면 [템플릿 편집기](/help/sites-cloud/authoring/features/templates.md#editing-templates-template-authors)로 쉽게 전환할 수 있습니다.

[열 보기](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) 또는 [목록 보기](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view)에서 페이지를 선택하면 페이지의 기본 템플릿을 쉽게 볼 수 있습니다.

## Live Copy 상태 {#live-copy-status}

다음 [라이브 카피 상태 페이지 모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) 라이브 카피 상태 및 상속되지 않은 구성 요소에 대한 간략한 개요를 제공합니다.

* 녹색 테두리: 상속됨
* 분홍색 테두리: 상속이 취소되었습니다.

예:

![표시되는 Live Copy 상태의 예](/help/sites-cloud/authoring/assets/editing-live-copy-status.png)

## 주석 추가 {#adding-annotations}

[주석](/help/sites-cloud/authoring/fundamentals/annotations.md)을 사용하면 검토자와 다른 작성자가 콘텐츠에 대한 피드백을 제공할 수 있습니다. 이러한 지표는 종종 검토 및 유효성 검사 목적으로 사용됩니다.

## 페이지 미리보기 {#previewing-pages}

페이지를 미리 볼 수 있는 두 가지 옵션이 있습니다.

* [미리보기 모드](#preview-mode) - 빠르고 즉각적인 미리보기
* [게시됨으로 보기](#view-as-published) - 새 탭에 페이지가 열리는 전체 미리보기

>[!TIP]
>
>* 콘텐츠에 있는 링크는 볼 수는 있지만 편집 모드에서 액세스할 수는 없습니다.
>* 링크를 사용하여 탐색하려는 경우 미리보기 옵션 중 하나를 사용합니다.
>* [키보드 단축키](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Shift-M`을 사용하여 미리보기와 마지막에 선택한 모드 간에 전환할 수 있습니다.

>[!NOTE]
>
>WCM 모드 쿠키는 두 미리보기 옵션 모두에 대해 설정됩니다.

### 미리보기 모드 {#preview-mode}

내용을 편집할 때 [미리보기 모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)를 사용하여 페이지를 미리 볼 수 있습니다. 이 모드에서 다음 작업을 수행합니다.

* 게시할 때 페이지가 표시되는 모양에 대해 빠른 보기를 제공할 수 있도록 여러 가지 편집 메커니즘을 숨깁니다.
* 링크를 사용하여 탐색할 수 있습니다.
* 페이지 콘텐츠를 새로 고치지 **않습니다**.

미리보기 모드는 작성할 때 페이지 편집기의 오른쪽 상단에 있는 아이콘을 사용하면 이용할 수 있습니다.

![미리보기 버튼](/help/sites-cloud/authoring/assets/preview.png)

### 게시됨으로 보기 {#view-as-published}

다음 **게시됨으로 보기** 옵션은 다음 위치에서 사용할 수 있습니다. [페이지 정보](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) 메뉴 아래의 제품에서 사용할 수 있습니다. 이 옵션은 새 탭에 페이지를 열고, 콘텐츠를 새로 고치고, 게시 환경에 표시되는 대로 페이지를 표시합니다.

## 페이지 잠금 {#locking-a-page}

AEM을 사용하면 다른 사람이 컨텐츠를 편집할 수 없도록 페이지를 잠글 수 있습니다. 이 잠금은 하나의 특정 페이지를 여러 번 편집하거나 잠시 페이지를 동결해야 할 때 유용합니다.

다음 중 하나에서 페이지를 잠글 수 있습니다.

* **사이트** 콘솔

   1. 다음을 사용하여 페이지 선택 [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
   1. 잠금 아이콘을 선택합니다.

      ![잠금 버튼](/help/sites-cloud/authoring/assets/lock.png)

* **페이지 편집기**

   1. 다음 항목 선택 **페이지 정보** 아이콘을 클릭하여 메뉴를 엽니다.
   1. **페이지 잠금** 옵션을 선택합니다.

페이지가 잠기면 콘솔 보기 정보가 업데이트되며, 편집 시에는 잠금 기호가 도구 모음에 표시됩니다.

![잠긴 페이지의 예](/help/sites-cloud/authoring/assets/editing-locked-page.png)

>[!CAUTION]
>
>사용자를 가장할 때 페이지 잠금이 수행될 수 있습니다. 그러나 이 방법으로 잠긴 페이지는 (고객이) 가장한 사용자를 사용해서만 잠금 해제할 수 있습니다.
>
>페이지를 잠근 사용자를 가장하는 것으로는 페이지 잠금을 해제할 수 없습니다.
>
>페이지를 잠근 사용자가 페이지를 잠금 해제할 수 없는 경우 고객 지원 센터에 문의하여 잠금 해제 옵션을 평가하십시오.

## 페이지 잠금 해제 {#unlocking-a-page}

페이지 잠금을 해제하는 것은 [페이지 잠금](#locking-a-page)과 매우 유사해서, 페이지가 잠기면 잠금 옵션이 잠금 해제 동작으로 대체됩니다.

[페이지 정보] 메뉴에 **잠금 해제**&#x200B;가 옵션으로 표시되며 [사이트 콘솔]의 잠금 아이콘은 **잠금 해제** 아이콘으로 바뀝니다.

![잠금 해제 버튼](/help/sites-cloud/authoring/assets/unlock.png)

>[!CAUTION]
>
>사용자를 가장할 때 페이지 잠금이 수행될 수 있습니다. 그러나 이 방법으로 잠긴 페이지는 (고객이) 가장한 사용자를 사용해서만 잠금 해제할 수 있습니다.
>
>페이지를 잠근 사용자를 가장하는 것으로는 페이지 잠금을 해제할 수 없습니다.
>
>페이지를 잠근 사용자가 페이지를 잠금 해제할 수 없는 경우 고객 지원 센터에 문의하여 잠금 해제 옵션을 평가하십시오.

<!--
>[!CAUTION]
>
>Locking a page can be performed when impersonating a user. However a page locked in this way can only then be unlocked by the user who was impersonated, or by a user with admin rights (a member of AEM Administrator IMS profile).
>
>Pages can not be unlocked by impersonating the user who locked the page.
-->

<!--
>Locking a page can be performed when [impersonating a user](/help/sites-administering/security.md#impersonating-another-user). However a page locked in this way can only then be unlocked by the user who was impersonated or by the admin user.
-->

## 페이지 편집 실행 취소 및 재실행 {#undoing-and-redoing-page-edits}

다음 아이콘을 사용하여 작업을 실행 취소하거나 재실행할 수 있습니다. 이 아이콘들은 때에 따라 도구 모음에도 표시됩니다.

![실행 취소 및 재실행 버튼](/help/sites-cloud/authoring/assets/redo.png)

>[!TIP]
>
>* [키보드 단축키](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Z`를 사용하여 페이지 편집 작업을 취소할 수 있습니다.
>* 또한 키보드 단축키 `Ctrl-Y`를 사용하여 페이지 편집 작업을 재실행할 수 있습니다.

>[!NOTE]
>
>페이지 편집 내용을 실행 취소하거나 재실행할 때 가능한 사항에 대한 모든 세부 사항은 [페이지 편집 실행 취소 및 재실행 - 이론](#undoing-and-redoing-page-edits-the-theory)을 참조하십시오.

## 페이지 편집 내용 실행 취소 및 재실행 - 이론 {#undoing-and-redoing-page-edits-the-theory}

AEM은 사용자가 수행한 작업 내역과 해당 작업을 수행한 시퀀스를 저장하여 사용자가 수행한 순서대로 여러 작업을 실행 취소한 다음 필요한 경우 다시 실행하여 하나 이상의 작업을 다시 적용할 수 있도록 합니다.

콘텐츠 페이지의 요소(예: 텍스트 구성 요소 등)가 선택된 경우 명령을 실행 취소 및 재실행하면 선택한 항목에 적용됩니다.

실행 취소 및 재실행 명령의 동작은 다른 소프트웨어의 경우와 비슷합니다. 이러한 명령을 사용하여 웹 페이지의 콘텐츠를 편집하면서 최근 상태로 복원할 수 있습니다. 예를 들어 텍스트 단락을 페이지의 다른 위치로 이동한 후 실행 취소 명령을 사용하여 단락을 원래 위치로 되돌릴 수 있습니다. 그런 다음 이전 위치가 더 낫다고 판단되는 경우 재실행 명령을 사용하여 “실행 취소를 실행 취소”하십시오.

예를 들어 다음 작업을 수행할 수 있습니다.

* 실행 취소를 사용한 이후 페이지 편집을 하지 않은 한 작업을 재실행합니다.
* 최대 20개의 편집 작업을 실행 취소합니다(기본 설정).
* 사용 [키보드 단축키](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) 실행 취소 및 다시 실행의 경우.

다음 유형의 페이지 변경 사항에 대해 실행 취소 및 재실행을 사용할 수 있습니다.

* 단락 추가, 편집, 제거 및 이동
* 단락 콘텐츠 즉석 편집
* 페이지 내에서 항목 복사, 잘라내기 및 붙여넣기

>[!NOTE]
>
>* 파일 및 이미지 변경을 취소하거나 재실행하려면 특수 권한이 필요합니다.
>* 파일과 이미지에 대한 변경 내역은 최소 10시간 동안 지속됩니다. 그러나 이 시간 이후에는 변경 사항의 실행 취소가 보장되지 않습니다. 관리자는 기본 시간인 10시간을 변경할 수 있습니다.
>* 시스템 관리자는 인스턴스에 대한 요구 사항에 따라 실행 취소/재실행 기능의 다양한 측면을 구성할 수 있습니다.
<!--* Your system administrator can [configure various aspects of the Undo/Redo features](/help/sites-administering/config-undo.md) according to the requirements for your instance.-->
