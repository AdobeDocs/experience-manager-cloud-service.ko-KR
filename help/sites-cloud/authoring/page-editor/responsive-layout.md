---
title: 반응형 레이아웃
description: AEM을 사용하면 레이아웃 컨테이너 구성 요소를 사용하여 페이지에 대한 응답형 레이아웃을 구현할 수 있습니다.
exl-id: 87202742-5bed-4e87-a427-456a1a0e72cc
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 70a35cfeb163967b0f627d3ac6495f112d922974
workflow-type: tm+mt
source-wordcount: '1789'
ht-degree: 81%

---


# 반응형 레이아웃 {#responsive-layout}

AEM에서는 **레이아웃 컨테이너** 구성 요소를 사용하여 사용자 페이지에 대한 반응형 레이아웃을 보유할 수 있습니다.

>[!TIP]
>
>이 문서에서는 콘텐츠 작성자가 사용할 수 있는 레이아웃 컨테이너의 기능에 대한 개요를 제공합니다. 추가 리소스를 사용할 수 있습니다.
>
>* 사이트 관리자의 경우 사이트에 대한 레이아웃 컨테이너를 구성하는 방법에 대한 자세한 내용은 [레이아웃 컨테이너 및 레이아웃 모드 구성 문서에 설명되어 있습니다.](/help/sites-cloud/administering/responsive-layout.md)
>* 개발자의 경우 레이아웃 컨테이너 및 응답형 그리드에 대한 자세한 내용은 사이트를 디자인할 때 레이아웃 컨테이너 및 응답형 그리드를 사용하는 데 필요한 팁과 정보를 제공하는 [응답형 디자인 문서](/help/implementing/developing/introduction/responsive-design.md)에 설명되어 있습니다.

## 개요 {#overview}

**레이아웃 컨테이너** 구성 요소는 응답형 그리드 내에 구성 요소를 배치할 수 있도록 해주는 단락 시스템을 제공합니다. 이 격자를 사용하면 디바이스/창 크기 및 포맷에 따라 레이아웃을 다시 정렬할 수 있습니다. 구성 요소는 [**레이아웃** 모드](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)와 함께 사용됩니다. 이 모드에서는 디바이스에 종속적인 응답형 레이아웃을 만들고 편집할 수 있습니다.

레이아웃 컨테이너:

* 구성 요소를 격자에 나란히 배치하고 언제 구성 요소가 축소되거나 리플로우되어야 하는지를 지정하는 기능과 함께, 수평 격자에 맞춤 기능을 제공합니다.
* 미리 정의된 중단점(예: 휴대폰, 태블릿 등)을 사용하여 관련 디바이스/방향에 대한 콘텐츠의 필수 동작을 정의할 수 있습니다.
   * 예를 들어 구성 요소 크기나 구성 요소를 특정 디바이스에서 볼 수 있도록 할지 여부를 사용자 정의할 수 있습니다.
* 열 컨트롤을 사용하도록 중첩될 수 있습니다.

그러면 사용자는 콘텐츠가 에뮬레이터를 사용하여 어떻게 특정 디바이스에 대해 렌더링될지 알 수 있습니다.

AEM에서는 메커니즘을 조합하여 페이지에 대한 반응형 레이아웃을 실현합니다.

* [**레이아웃 컨테이너**](#adding-a-layout-container-and-its-content-edit-mode) 구성 요소

  이 구성 요소는 [구성 요소 브라우저](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser)에서 사용할 수 있으며, 응답형 그리드 내에 구성 요소를 추가 및 배치할 수 있도록 해 주는 그리드 단락 시스템을 제공합니다. 또한 페이지에서 기본 단락 시스템으로 설정할 수도 있습니다.

* [**레이아웃 모드**](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)

  레이아웃 컨테이너를 페이지에 배치하면 **레이아웃** 모드를 사용하여 콘텐츠를 응답형 그리드 내에 배치할 수 있습니다.

* [**에뮬레이터**](#selecting-a-device-to-emulate)
이를 사용하여 구성 요소의 크기를 상호 작용 방식으로 조정하여 디바이스/창 크기에 따라 레이아웃을 재정렬하는 반응형 웹 사이트를 만들고 편집할 수 있습니다. 그러면 사용자는 콘텐츠가 에뮬레이터를 사용하여 어떻게 렌더링될지 알 수 있습니다.

이러한 응답형 격자 메커니즘을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 중단점을 사용하여 디바이스 폭을 기반으로 달라지는 콘텐츠 레이아웃을 정의할 수 있습니다(디바이스 유형 및 방향과 관련).
* 동일한 중단점 및 콘텐츠 레이아웃을 사용하여 콘텐츠가 데스크탑에서 브라우저 창의 크기에 맞게 조절되도록 할 수 있습니다.
* 수평 격자에 맞춤 기능을 사용하여 구성 요소를 격자에 배치하고, 필요에 따라 크기를 변경하고, 언제 구성 요소가 나란히 또는 위/아래에 있도록 축소되거나 리플로우되어야 하는지 지정할 수 있습니다.
* 특정 디바이스 레이아웃의 구성 요소를 숨길 수 있습니다.
* 열 컨트롤을 구현할 수 있습니다.

프로젝트에 따라 레이아웃 컨테이너는 페이지의 기본 단락 시스템으로 사용되거나 구성 요소 브라우저(또는 둘 다)를 통해 페이지에 추가할 수 있는 구성 요소로 사용될 수 있습니다.

>[!NOTE]
>
>위의 메커니즘은 템플릿에 대한 구성으로 사용할 수 있게 됩니다. 자세한 내용은 [응답형 레이아웃 구성](/help/sites-cloud/administering/responsive-layout.md) 문서를 참조하십시오.

## 레이아웃 정의, 디바이스 에뮬레이션 및 중단점 {#layout-definitions-device-emulation-and-breakpoints}

웹 사이트 콘텐츠를 만들 때에는 콘텐츠를 보는 데 사용할 디바이스에 적절하게 콘텐츠가 표시되도록 해야 할 것입니다.

AEM을 사용하면 디바이스의 폭에 따라 레이아웃을 정의할 수 있습니다.

* 에뮬레이터를 사용하면 다양한 디바이스에서 이러한 레이아웃을 에뮬레이션할 수 있습니다. 디바이스 유형은 물론 **디바이스 회전** 옵션으로 선택한 방향도 폭이 변함에 따라 선택한 중단점에 영향을 줄 수 있습니다.
* 중단점은 레이아웃 정의를 분리하는 점입니다.
   * 특정 레이아웃을 사용하는 모든 디바이스의 최대 폭(픽셀 단위)도 효과적으로 정의할 수 있습니다.
   * 대개는 표시 폭에 따라 디바이스 선택에 중단점을 사용할 수 있습니다.
   * 중단점의 범위는 다음 중단점까지 왼쪽으로 확장됩니다.
   * 중단점을 명시적으로 선택할 수는 없습니다. 디바이스 및 방향을 선택하면 적절한 중단점이 자동으로 선택됩니다.

특정 너비가 없고 기본 중단점(마지막으로 구성된 중단점 위의 모든 것)과 관련된 **데스크탑** 디바이스입니다.

>[!NOTE]
>
>모든 개별 디바이스에 대해 중단점을 정의할 수는 있지만, 그렇게 되면 레이아웃 정의 및 유지 관리에 필요한 노력이 크게 증가합니다.

에뮬레이터를 사용하여 에뮬레이션하고 레이아웃을 정의할 특정 디바이스를 선택하면 관련 중단점도 강조 표시됩니다. 레이아웃 변경 사항은 중단점이 적용되는 다른 디바이스에 적용할 수 있습니다. 즉, 기본 중단점 마커의 왼쪽에 있지만 다음 중단점 마커 앞에 있는 모든 디바이스입니다.

예를 들어 에뮬레이션하고 레이아웃을 정의할 디바이스로 **iPhone 6 Plus**(폭 540픽셀로 정의됨)를 선택하면 중단점 **Phone**(768픽셀로 정의됨)도 활성화됩니다. **iPhone 6**&#x200B;에 대해 수행하는 모든 레이아웃 변경 작업은 **iPhone 5**(320픽셀로 정의됨)와 같은 **Phones** 중단점 아래의 다른 디바이스에 적용됩니다.

![에뮬레이터](/help/sites-cloud/authoring/assets/responsive-layout-emulators.png)

## 에뮬레이션할 디바이스 선택 {#selecting-a-device-to-emulate}

1. 편집에 필요한 페이지를 엽니다. 예:

   `http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

1. 맨 위 도구 모음에서 **에뮬레이터** 아이콘을 선택합니다.

   ![에뮬레이터 버튼](/help/sites-cloud/authoring/assets/emulator.png)

1. 에뮬레이터 도구 모음이 열립니다.

   ![에뮬레이터 도구 모음](/help/sites-cloud/authoring/assets/responsive-layout-emulator-toolbar.png)

   에뮬레이터 도구 모음은 추가 레이아웃 옵션을 표시합니다.

   * **장치 회전** - 장치를 세로(수직) 방향에서 가로(수평) 방향으로 역으로 회전할 수 있습니다.

   ![디바이스 회전 가로 버튼](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-landscape-button.png)
   ![디바이스 회전 세로 버튼](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-portrait-button.png)

   * **디바이스 선택** - 목록에서 에뮬레이션하려는 특정 디바이스를 정의합니다(자세한 내용은 다음 단계를 참조).

   ![디바이스 선택 버튼](/help/sites-cloud/authoring/assets/responsive-layout-select-device-button.png)

1. 에뮬레이션할 특정 디바이스를 선택하기 위해 다음 중 하나를 수행할 수 있습니다.

   * [디바이스 선택] 아이콘을 사용하고 드롭다운 선택기에서 선택합니다.
   * 에뮬레이터 도구 모음에서 장치 표시기 선택.

   ![디바이스 선택 드롭다운](/help/sites-cloud/authoring/assets/responsive-layout-select-device-dropdown.png)

1. 특정 디바이스를 선택하면 다음 작업을 수행할 수 있습니다.

   * 선택한 디바이스(예: **iPad**)에 대해 활성 마커를 봅니다.
   * 적절한 [중단점](#layout-definitions-device-emulation-and-breakpoints)(예: **태블릿**)에 대해 활성 마커를 봅니다.
   * 파란색 점선은 선택한 디바이스(여기에서는 가로로 된 **iPhone 6 Plus**)에 대한 *접힌 부분*&#x200B;을 나타냅니다.

   ![접힌 부분](/help/sites-cloud/authoring/assets/responsive-layout-fold.png)

   * 접힌 부분은 콘텐츠에 대한 페이지 줄바꿈으로 간주할 수 있습니다([중단점](#layout-definitions-device-emulation-and-breakpoints)과 혼동하지 않도록 주의하십시오). 이는 스크롤하기 전에 사용자가 디바이스에서 보게 되는 컨텐츠 부분을 표시하기 위해 편의상 표시됩니다.
   * 에뮬레이션 중인 디바이스의 높이가 화면 크기보다 높을 경우 접힌 부분의 선이 표시되지 않습니다.
   * 접힌 부분은 작성자의 편의를 위해 표시되며 게시된 페이지에는 표시되지 않습니다.

## 레이아웃 컨테이너 및 해당 콘텐츠 추가(편집 모드) {#adding-a-layout-container-and-its-content-edit-mode}

**레이아웃 컨테이너**&#x200B;는 다음과 같은 단락 시스템입니다.

* 다른 구성 요소를 포함합니다.
* 레이아웃을 정의합니다.
* 변경에 응답합니다.

>[!NOTE]
>
>아직 사용할 수 없는 경우 **레이아웃 컨테이너**&#x200B;는 단락 시스템/페이지에 대해 명시적으로 [활성화됨](/help/sites-cloud/administering/responsive-layout.md)이어야 합니다.

1. **레이아웃 컨테이너**&#x200B;는 [구성 요소 브라우저](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser)에서 표준 구성 요소로 사용할 수 있습니다. 여기에서 페이지의 필요한 위치로 드래그하면 **구성 요소를 여기로 드래그** 자리 표시자가 표시됩니다.
1. 그런 다음 구성 요소를 레이아웃 컨테이너에 추가할 수 있습니다. 이러한 구성 요소는 실제 콘텐츠를 담게 됩니다.

   ![레이아웃 컨테이너](/help/sites-cloud/authoring/assets/responsive-layout-add-to-layout-container.png)

## 레이아웃 컨테이너에서 작업 선택 및 수행(편집 모드) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

다른 구성 요소와 마찬가지로 을(를) 선택한 다음 레이아웃 컨테이너에서 작업(잘라내기, 복사, 삭제)할 수 있습니다(**편집** 모드에 있는 경우).

>[!CAUTION]
>
>레이아웃 컨테이너가 단락 시스템이므로 구성 요소를 삭제하면 레이아웃 격자와 컨테이너 내의 모든 구성 요소(및 해당 콘텐츠)가 모두 삭제됩니다.

1. 격자 자리 표시자를 마우스로 가리키거나 선택하면 작업 메뉴가 표시됩니다.

   ![레이아웃 컨테이너에 추가](/help/sites-cloud/authoring/assets/responsive-layout-container.png)

   **상위** 옵션을 선택해야 합니다.

   ![상위 버튼](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

1. 레이아웃 구성 요소가 중첩된 경우, **상위** 옵션을 선택하면 드롭다운 옵션이 표시되어 중첩된 레이아웃 컨테이너 또는 상위 항목을 선택할 수 있습니다.

   드롭다운에서 컨테이너 이름 위로 마우스를 이동하면 해당 윤곽이 페이지에 표시됩니다.

   * 가장 낮게 중첩된 레이아웃 컨테이너는 파란색으로 윤곽이 표시됩니다.
   * 연속적인 모든 컨테이너는 파란색 음영으로 표시됩니다.

   ![중첩된 컨테이너](/help/sites-cloud/authoring/assets/responsive-layout-nested.png)

1. 해당 콘텐츠가 있는 전체 격자가 강조 표시됩니다. 작업 도구 모음이 표시되고 여기서 **삭제** 등의 작업을 선택할 수 있습니다.

## 레이아웃 정의(레이아웃 모드) {#defining-layouts-layout-mode}

>[!NOTE]
>
>각 [중단점](#layout-definitions-device-emulation-and-breakpoints)에 대해 별도의 레이아웃을 정의할 수 있습니다(에뮬레이션된 디바이스 유형 및 방향으로 결정된 대로).

레이아웃 컨테이너로 구현된 응답형 그리드의 레이아웃을 구성하려면 **레이아웃** 모드를 사용해야 합니다.

**레이아웃** 모드는 두 가지 방법으로 시작할 수 있습니다.

* [도구 모음에서 모드 메뉴](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)를 사용하여 **레이아웃** 모드 선택
   * **편집** 모드나 **타겟팅** 모드로 전환하는 것처럼 **레이아웃** 모드 선택
   * **레이아웃** 모드가 지속적으로 유지되며 모드 선택기를 통해 다른 모드를 선택할 때까지 **레이아웃** 모드를 벗어나지 않습니다.
* [개별 구성 요소를 편집](/help/sites-cloud/authoring/page-editor/edit-content.md#editing-component-layout)하는 경우
   * 구성 요소의 빠른 작업 메뉴에서 **레이아웃** 옵션을 사용하여 **레이아웃** 모드로 전환할 수 있습니다.
   * 구성 요소를 편집하는 동안 **레이아웃** 모드가 지속되며 초점이 다른 구성 요소로 변경되면 **편집** 모드로 되돌아갑니다.

레이아웃 모드에 있는 경우 격자에서 다양한 작업을 수행할 수 있습니다.

* 파란색 점을 사용하여 콘텐츠 구성 요소 크기를 변경할 수 있습니다. 크기를 변경하면 항상 격자에 맞춰집니다. 크기를 변경하면 정렬을 위해 배경 격자가 표시됩니다.

  ![구성 요소 크기 조정](/help/sites-cloud/authoring/assets/responsive-layout-resizing.png)

  >[!NOTE]
  >
  >**이미지**&#x200B;와 같은 구성 요소의 크기가 변경될 때 상대적인 비율 및 비는 유지됩니다.

* 콘텐츠 구성 요소를 선택합니다. 도구 모음을 사용하면 다음 작업을 수행할 수 있습니다.
   * **상위** - 전체적으로 작업을 수행할 전체 레이아웃 컨테이너 구성 요소를 선택할 수 있습니다.
   * **새 라인으로 이동** - 그리드 내에서 사용할 수 있는 공간에 따라 구성 요소가 새 라인으로 이동됩니다.
   * **구성 요소 숨기기** - 구성 요소가 보이지 않게 됩니다(레이아웃 컨테이너의 도구 모음에서 복원 가능).

  ![구성 요소 숨기기](/help/sites-cloud/authoring/assets/responsive-layout-hide.png)

* **레이아웃** 모드에서 **구성 요소를 여기로 드래그**&#x200B;하여 전체 구성 요소를 선택할 수 있습니다. 이 모드에 대한 도구 모음이 표시됩니다.

  도구 모음은 레이아웃 구성 요소의 상태와 이에 속하는 구성 요소에 따라 옵션이 달라집니다. 예:

   * **상위** - 상위 구성 요소를 선택합니다.

     ![상위 버튼](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

   * **숨겨진 구성 요소 표시** - 모든 또는 개별 구성 요소를 표시합니다. 숫자는 현재 숨겨진 구성 요소 수를 표시합니다. 카운터는 몇 개의 구성 요소가 숨겨져 있는지 표시합니다.

     ![숨겨진 구성 요소 표시 버튼](/help/sites-cloud/authoring/assets/responsive-layout-show-button.png)

   * **중단점 레이아웃 되돌리기** - 기본 레이아웃으로 되돌립니다. 사용자 정의된 레이아웃이 적용되지 않습니다.

     ![중단점 레이아웃 되돌리기 버튼](/help/sites-cloud/authoring/assets/responsive-layout-revert-button.png)

   * **새 라인으로 이동** - 공간이 있으면 구성 요소를 위로 이동합니다.

     ![새 라인으로 이동 버튼](/help/sites-cloud/authoring/assets/responsive-layout-float-button.png)

   * **구성 요소 숨기기** - 현재 구성 요소를 숨깁니다.

     ![구성 요소 숨기기 버튼](/help/sites-cloud/authoring/assets/responsive-layout-hide-button.png)

  >[!NOTE]
  >
  >위의 예에서 이동 및 숨기기 동작은 레이아웃 컨테이너가 상위 레이아웃 컨테이너 내에서 중첩되기 때문에 가능한 것입니다.

   * **구성 요소 숨김 취소** 상위 구성 요소를 선택하여 **숨겨진 구성 요소 표시** 옵션과 함께 작업 도구 모음을 표시할 수 있습니다. 이 예시에는 두 개의 구성 요소가 숨겨져 있습니다.

     ![구성 요소 숨기기 취소](/help/sites-cloud/authoring/assets/responsive-layout-unhide.png)

  **숨겨진 구성 요소 표시** 옵션을 선택하면 원래 위치에서 현재 숨겨진 구성 요소가 파란색으로 표시됩니다.

  ![모두 복원 버튼](/help/sites-cloud/authoring/assets/responsive-layout-restore-all.png)

  **모두 복원**&#x200B;을 선택하면 숨겨진 모든 구성 요소가 숨김 취소됩니다.
