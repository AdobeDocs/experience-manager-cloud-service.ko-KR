---
title: 반응형 레이아웃
description: AEM을 사용하면 페이지에 대한 응답형 레이아웃을 구현할 수 있습니다
exl-id: 87202742-5bed-4e87-a427-456a1a0e72cc
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 71%

---

# 반응형 레이아웃 {#responsive-layout}

AEM에서는 를 사용하여 페이지에 대한 응답형 레이아웃을 만들 수 있습니다. **레이아웃 컨테이너** 구성 요소.

이 레이아웃은 응답형 격자 내에 구성 요소를 배치할 수 있도록 해 주는 단락 시스템을 제공합니다. 이 격자를 사용하면 디바이스/창 크기 및 형식에 따라 레이아웃을 다시 정렬할 수 있습니다. 구성 요소는 [**레이아웃** 모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)와 함께 사용됩니다. 이 모드에서는 디바이스에 종속적인 응답형 레이아웃을 만들고 편집할 수 있습니다.

레이아웃 컨테이너:

* 구성 요소를 나란히 격자에 배치하고 언제 축소하거나 리플로우해야 하는지 정의할 수 있는 기능과 함께 격자에 대한 수평 스냅을 제공합니다.
* 미리 정의된 중단점(예: 전화, 태블릿 등)을 사용하여 관련 디바이스/방향에 대한 필수 동작을 정의할 수 있습니다.
   * 예를 들어 구성 요소 크기나 구성 요소를 특정 디바이스에서 볼 수 있도록 할지 여부를 사용자 정의할 수 있습니다.
* 열 제어를 허용하도록 중첩될 수 있습니다.

그러면 사용자는 콘텐츠가 에뮬레이터를 사용하여 어떻게 특정 디바이스에 대해 렌더링되는지 알 수 있습니다.

AEM에서는 메커니즘을 조합하여 페이지에 대한 응답형 레이아웃을 실현합니다.

* [**레이아웃 컨테이너**](#adding-a-layout-container-and-its-content-edit-mode) 구성 요소

  이 구성 요소는 [구성 요소 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)에서 사용할 수 있으며, 응답형 그리드 내에 구성 요소를 추가 및 배치할 수 있도록 해 주는 그리드 단락 시스템을 제공합니다. 또한 페이지에서 기본 단락 시스템으로 설정할 수도 있습니다.

* [**레이아웃 모드**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)

  레이아웃 컨테이너를 페이지에 배치하면 **레이아웃** 모드를 사용하여 콘텐츠를 응답형 그리드 내에 배치할 수 있습니다.

* [**에뮬레이터**](#selecting-a-device-to-emulate)
이렇게 하면 구성 요소의 크기를 대화 방식으로 변경하여 디바이스/창 크기에 따라 레이아웃을 다시 정렬하는 응답형 웹 사이트를 만들고 편집할 수 있습니다. 그러면 사용자는 콘텐츠가 에뮬레이터를 사용하여 어떻게 렌더링되는지 볼 수 있습니다.

이러한 응답형 격자 메커니즘을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 중단점을 사용하여 디바이스 너비를 기반으로 달라지는 콘텐츠 레이아웃을 정의할 수 있습니다(디바이스 유형 및 방향과 관련).
* 동일한 중단점 및 콘텐츠 레이아웃을 사용하여 콘텐츠가 데스크탑에서 브라우저 창의 크기에 맞게 조절되도록 할 수 있습니다.
* 수평 격자에 맞춤 기능을 사용하여 구성 요소를 격자에 배치하고, 필요에 따라 크기를 변경하고, 언제 구성 요소가 나란히 또는 위/아래에 있도록 축소되거나 리플로우되어야 하는지 지정할 수 있습니다.
* 특정 디바이스 레이아웃의 구성 요소를 숨길 수 있습니다.
* 열 컨트롤을 구현할 수 있습니다.

프로젝트에 따라 레이아웃 컨테이너는 페이지의 기본 단락 시스템으로 사용되거나 구성 요소 브라우저를 통해 페이지에 추가할 수 있는 구성 요소(또는 둘 다)로 사용될 수 있습니다.

>[!TIP]
>
>Adobe는 응답형 레이아웃의 [GitHub 설명서](https://adobe-marketing-cloud.github.io/aem-responsivegrid/)를 프런트엔드 개발자에게 참조용으로 제공하여 AEM 외부 그리드를 사용할 수 있도록 합니다. 예를 들어 나중에 사용하기 위해 AEM 사이트에 대한 정적 HTML mock-up을 생성할 때 이를 사용할 수 있습니다.

>[!NOTE]
>
>위의 메커니즘은 템플릿에 대한 구성으로 사용할 수 있게 됩니다. 자세한 내용은 응답형 레이아웃 구성을 참조하십시오. <!-- Use of the above mechanisms is enabled by configuration on the template. See [Configuring Responsive Layout](/help/sites-administering/configuring-responsive-layout.md) for further information.-->

## 레이아웃 정의, 디바이스 에뮬레이션 및 중단점 {#layout-definitions-device-emulation-and-breakpoints}

웹 사이트 콘텐츠를 만들 때에는 콘텐츠를 보는 데 사용할 디바이스에 적절하게 콘텐츠가 표시되도록 해야 할 것입니다.

AEM을 사용하면 디바이스의 너비에 따라 레이아웃을 정의할 수 있습니다.

* 애뮬레이터를 사용하면 다양한 디바이스에서 이러한 레이아웃을 에뮬레이션할 수 있습니다. 디바이스 유형은 물론 **디바이스 회전** 옵션으로 선택한 방향도 너비가 변함에 따라 선택한 중단점에 영향을 줄 수 있습니다.
* 중단점은 레이아웃 정의를 분리하는 점입니다.
   * 특정 레이아웃을 사용하는 모든 디바이스의 최대 너비(픽셀 단위)도 효과적으로 정의할 수 있습니다.
   * 대개는 표시 너비에 따라 디바이스 선택에 중단점을 사용할 수 있습니다.
   * 중단점의 범위는 다음 중단점까지 왼쪽으로 확장됩니다.
   * 중단점을 명시적으로 선택할 수는 없습니다. 디바이스 및 방향을 선택하면 적절한 중단점이 자동으로 선택됩니다.

특정 너비가 없고 기본 중단점과 관련된 **데스크탑** 디바이스입니다(즉, 마지막으로 구성된 중단점 위의 모든 것).

>[!NOTE]
>
>모든 개별 디바이스에 대해 중단점을 정의할 수는 있지만, 그렇게 되면 레이아웃 정의 및 유지 관리에 필요한 노력이 크게 증가합니다.

에뮬레이터를 사용할 때 에뮬레이션하고 레이아웃을 정의할 특정 디바이스를 선택하면 관련 중단점도 강조 표시됩니다. 수행하는 모든 레이아웃 변경 작업은 중단점이 적용되는 다른 장치에 적용할 수 있습니다. 즉, 활성 중단점 마커의 왼쪽에, 하지만 다음 중단점 마커의 앞에 있는 모든 장치를 나타냅니다.

예를 들어, 장치를 선택하는 경우 **iPhone 6 Plus** (너비 540픽셀로 정의됨) 에뮬레이션하고 레이아웃을 지정하는 중단점입니다 **전화** (768픽셀로 정의됨)도 활성화됩니다. 다음에 대해 수행하는 모든 레이아웃 변경 **IPHONE 6** 아래의 다른 장치에 적용됩니다. **휴대폰** 중단점(예: ) **IPHONE 5** (320픽셀로 정의됨)

![에뮬레이터](/help/sites-cloud/authoring/assets/responsive-layout-emulators.png)

## 에뮬레이션할 디바이스 선택 {#selecting-a-device-to-emulate}

1. 편집에 필요한 페이지를 엽니다. 예:

   `http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

1. 맨 위 도구 모음에서 **에뮬레이터** 아이콘을 선택합니다.

   ![에뮬레이터 버튼](/help/sites-cloud/authoring/assets/emulator.png)

1. 에뮬레이터 도구 모음이 열립니다.

   ![에뮬레이터 도구 모음](/help/sites-cloud/authoring/assets/responsive-layout-emulator-toolbar.png)

   에뮬레이터 도구 모음은 추가 레이아웃 옵션을 표시합니다.

   * **디바이스 회전** - 디바이스를 세로(수직) 방향에서 가로(수평) 방향으로 또는 그 반대로 회전할 수 있습니다.

   ![디바이스 회전 가로 버튼](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-landscape-button.png)
   ![디바이스 회전 세로 버튼](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-portrait-button.png)

   * **디바이스 선택** - 목록에서 에뮬레이션하려는 특정 디바이스를 정의합니다(자세한 내용은 다음 단계를 참조).

   ![디바이스 선택 버튼](/help/sites-cloud/authoring/assets/responsive-layout-select-device-button.png)

1. 에뮬레이션할 특정 디바이스를 선택하기 위해 다음 중 하나를 수행할 수 있습니다.

   * [디바이스 선택] 아이콘을 사용하고 드롭다운 선택기에서 선택합니다.
   * 에뮬레이터 도구 모음에서 디바이스 표시기 클릭/탭

   ![디바이스 선택 드롭다운](/help/sites-cloud/authoring/assets/responsive-layout-select-device-dropdown.png)

1. 특정 디바이스를 선택하면 다음 작업을 수행할 수 있습니다.

   * 선택한 디바이스(예: **iPad**)에 대해 활성 마커를 봅니다.
   * 적절한 [중단점](#layout-definitions-device-emulation-and-breakpoints)(예: **태블릿**)에 대해 활성 마커를 봅니다.
   * 파란색 점선은 선택한 디바이스(여기에서는 가로로 된 **iPhone 6 Plus**)에 대한 *접힌 부분*&#x200B;을 나타냅니다.

   ![접힌 부분](/help/sites-cloud/authoring/assets/responsive-layout-fold.png)

   * 접힌 부분은 콘텐츠에 대한 페이지 줄바꿈으로 간주할 수 있습니다([중단점](#layout-definitions-device-emulation-and-breakpoints)과 혼동하지 않도록 주의하십시오). 이는 스크롤하기 전에 사용자가 디바이스에서 보게 될 내용 일부를 표시하기 위해 편의상 표시됩니다.
   * 에뮬레이션 중인 디바이스의 높이가 화면 크기보다 높을 경우 접힌 부분의 선이 표시되지 않습니다.
   * 접힌 부분은 작성자의 편의를 위해 표시되며 게시된 페이지에는 표시되지 않습니다.

## 레이아웃 컨테이너 및 해당 콘텐츠 추가(편집 모드) {#adding-a-layout-container-and-its-content-edit-mode}

**레이아웃 컨테이너**&#x200B;는 다음과 같은 단락 시스템입니다.

* 다른 구성 요소를 포함합니다.
* 레이아웃을 정의합니다.
* 변경 사항에 응답합니다.

>[!NOTE]
>
>아직 사용할 수 없는 경우에는 **레이아웃 컨테이너**&#x200B;를 단락 시스템/페이지에 대해 확실히 활성화해야 합니다. <!-- If not already available, the **Layout Container** must be explicitly [activated for a paragraph system/page](/help/sites-administering/configuring-responsive-layout.md).-->

1. The **Layout Container** is available as a standard component in the [Components Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser). From here you can drag it to the required location on the page after which you will see the **Drag Components here** placeholder.
1. 그런 다음 레이아웃 컨테이너에 구성 요소를 추가할 수 있습니다. 이러한 구성 요소는 실제 콘텐츠를 담게 됩니다.

   ![레이아웃 컨테이너](/help/sites-cloud/authoring/assets/responsive-layout-add-to-layout-container.png)

## 레이아웃 컨테이너에서 작업 선택 및 수행(편집 모드) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

선택할 수 있는 기타 구성 요소가 있으면 레이아웃 컨테이너에서 작업을 수행(복사, 잘라내기, 삭제)할 수 있습니다(**편집** 모드에 있을 때).

>[!CAUTION]
>
>레이아웃 컨테이너가 단락 시스템이므로 구성 요소를 삭제하면 레이아웃 격자와 컨테이너 내의 모든 구성 요소(및 해당 콘텐츠)가 모두 삭제됩니다.

1. 격자 자리 표시자 위에 마우스를 가져다 대거나 탭하면 작업 메뉴가 표시됩니다.

   ![레이아웃 컨테이너에 추가](/help/sites-cloud/authoring/assets/responsive-layout-container.png)

   **상위** 옵션을 선택해야 합니다.

   ![상위 버튼](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

1. 레이아웃 구성 요소가 중첩된 경우 **상위** 옵션은 중첩된 레이아웃 컨테이너 또는 해당 상위 항목을 선택할 수 있는 드롭다운 선택 사항을 제공합니다.

   드롭다운에서 컨테이너 이름을 마우스로 가리키면 컨테이너 아웃라인이 페이지에 표시됩니다.

   * 가장 낮게 중첩된 레이아웃 컨테이너는 파란색으로 윤곽이 표시됩니다.
   * 연속적인 모든 컨테이너는 파란색 음영으로 윤곽선이 표시됩니다.

   ![중첩된 컨테이너](/help/sites-cloud/authoring/assets/responsive-layout-nested.png)

1. 전체 격자가 해당 콘텐츠로 강조 표시됩니다. 다음과 같은 작업을 선택할 수 있는 작업 도구 모음이 표시됩니다. **삭제.**

## 레이아웃 정의(레이아웃 모드) {#defining-layouts-layout-mode}

>[!NOTE]
>
>각 [중단점](#layout-definitions-device-emulation-and-breakpoints)에 대해 별도의 레이아웃을 정의할 수 있습니다(에뮬레이션된 디바이스 유형 및 방향으로 결정된 대로).

레이아웃 컨테이너로 구현된 응답형 그리드의 레이아웃을 구성하려면 **레이아웃** 모드를 사용해야 합니다.

**레이아웃** 모드는 두 가지 방법으로 시작할 수 있습니다.

* [도구 모음에서 모드 메뉴](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)를 사용하여 **레이아웃** 모드 선택
   * **편집** 모드나 **타겟팅** 모드로 전환하는 것처럼 **레이아웃** 모드 선택
   * **레이아웃** 모드가 지속적으로 유지되며 모드 선택기를 통해 다른 모드를 선택할 때까지 **레이아웃** 모드를 벗어나지 않습니다.
* 날짜 [개별 구성 요소 편집](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout)
   * 를 사용하여 **레이아웃** 구성 요소의 빠른 작업 메뉴에서 다음 위치로 전환할 수 있습니다. **레이아웃** 모드.
   * **레이아웃** 모드는 구성 요소를 편집하는 동안 지속되며 로 되돌아갑니다. **편집** 포커스가 다른 구성 요소로 변경되면 모드.

레이아웃 모드에 있는 경우 그리드에서 다양한 작업을 수행할 수 있습니다.

* 파란색 점을 사용하여 콘텐츠 구성 요소 크기를 변경할 수 있습니다. 크기 조정은 항상 격자에 맞춰 조정됩니다. 크기를 조정할 때 배경 격자가 정렬에 도움이 되도록 표시됩니다.

  ![구성 요소 크기 조정](/help/sites-cloud/authoring/assets/responsive-layout-resizing.png)

  >[!NOTE]
  >
  >구성 요소(예: )가 **이미지** 크기가 조정됩니다.

* 콘텐츠 구성 요소를 클릭/탭합니다. 도구 모음에서는 다음 작업을 수행할 수 있습니다.
   * **상위** - 전체적으로 작업을 수행할 전체 레이아웃 컨테이너 구성 요소를 선택할 수 있습니다.
   * **새 라인으로 이동** - 그리드 내에서 사용할 수 있는 공간에 따라 구성 요소가 새 라인으로 이동됩니다.
   * **구성 요소 숨기기** - 구성 요소가 보이지 않게 됩니다(레이아웃 컨테이너의 도구 모음에서 복원 가능).

  ![구성 요소 숨기기](/help/sites-cloud/authoring/assets/responsive-layout-hide.png)

* **레이아웃** 모드에서 **구성 요소를 여기로 드래그하십시오.**&#x200B;를 탭/클릭하여 전체 구성 요소를 선택할 수 있습니다. 이 모드에 대한 도구 모음이 표시됩니다.

  도구 모음에는 레이아웃 구성 요소와 그 구성 요소에 속하는 구성 요소의 상태에 따라 다른 옵션이 있습니다. 예:

   * **상위** - 상위 구성 요소를 선택합니다.

     ![상위 버튼](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

   * **숨겨진 구성 요소 표시** - 모든 또는 개별 구성 요소를 표시합니다. 숫자는 현재 숨겨진 구성 요소 수를 표시합니다. 카운터는 몇 개의 구성 요소가 숨겨져 있는지 표시합니다.

     ![숨겨진 구성 요소 표시 버튼](/help/sites-cloud/authoring/assets/responsive-layout-show-button.png)

   * **중단점 레이아웃 되돌리기** - 기본 레이아웃으로 되돌립니다. 사용자 지정된 레이아웃이 적용되지 않습니다.

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
