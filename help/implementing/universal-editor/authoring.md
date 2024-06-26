---
title: Universal Editor로 콘텐츠 작성
description: 콘텐츠 작성자가 Universal Editor를 사용하여 얼마나 쉽고 직관적으로 콘텐츠를 만들 수 있는지 알아봅니다.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: b42390dcecb546853380d64808bcf009680c89a3
workflow-type: tm+mt
source-wordcount: '2083'
ht-degree: 54%

---


# Universal Editor로 콘텐츠 작성 {#authoring}

콘텐츠 작성자가 Universal Editor를 사용하여 얼마나 쉽고 직관적으로 콘텐츠를 만들 수 있는지 알아봅니다.

{{universal-editor-status}}

## 소개 {#introduction}

Universal Editor를 사용하면 모든 구현에서 콘텐츠의 모든 측면을 편집할 수 있기 때문에 뛰어난 경험을 제공하고, 콘텐츠 속도를 높이고, 최신 개발자 경험을 제공할 수 있습니다.

이를 위해 제공되는 Universal Editor는 콘텐츠 작성자가 최소한의 교육만 받으면 사용할 수 있어 바로 부담 없이 콘텐츠 편집을 시작할 수 있습니다. 이 문서에서는 Universal Editor의 작성 환경에 대해 설명합니다.

>[!TIP]
>
>Universal Editor에 대한 자세한 소개는 [Universal Editor 소개](introduction.md) 문서를 참조하십시오.

## 앱 준비 {#prepare-app}

Universal Editor로 앱의 콘텐츠를 작성하려면 개발자가 앱을 계측하여 편집기를 지원해야 합니다.

>[!TIP]
>
>Universal Editor와 함께 작동하도록 AEM 앱을 구성하는 방법에 대한 예는 [AEM에서 Universal Editor 시작](getting-started.md)을 참조하십시오.

## 로그인 {#sign-in}

앱이 유니버설 편집기에서 작동하도록 계측되면 유니버설 편집기에 로그인합니다. 로그인하려면 Adobe ID이 필요합니다. [유니버설 편집기에 액세스할 수 있습니다.](getting-started.md#request-access)

로그인한 후에 [위치 표시줄에 편집하려는 페이지의 URL을 입력하여](#location-bar)[텍스트 콘텐츠](#text-mode) 또는 [미디어 콘텐츠](#media-mode)와 같은 콘텐츠를 편집할 수 있습니다.

## UI 이해 {#ui}

UI는 이러한 기본 영역으로 나뉩니다.

* [Experience Cloud 헤더](#experience-cloud-header)
* [범용 편집기 도구 모음](#universal-editor-toolbar)
* [편집기](#editor)
* [속성 레일](#properties-rail)

![Universal Editor UI](assets/ui.png)

### Experience Cloud 헤더 {#experience-cloud-header}

Experience Cloud 헤더는 항상 화면 상단에 있습니다. Experience Cloud 내의 위치를 알려 주고 다른 Experience Cloud 앱으로 이동할 수 있도록 도와주는 앵커입니다.

![Experience Cloud 헤더](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

헤더 왼쪽에 있는 Adobe Experience Cloud 링크를 선택해 Experience Manager 솔루션의 루트로 이동하여 [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager,](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) [Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html) 등의 도구에 액세스합니다.

![전역 탐색 버튼](assets/global-navigation.png)

#### 조직 {#organization}

현재 로그인되어 있는 조직이 표시됩니다. Adobe ID이 여러 조직과 연결되어 있는 경우 다른 조직으로 전환하려면 선택합니다.

![조직 표시기](assets/organization.png)

#### 솔루션 {#solutions}

솔루션 전환기를 탭하거나 클릭하면 다른 Experience Cloud 솔루션으로 빠르게 이동할 수 있습니다.

![솔루션 전환기](assets/solutions.png)

#### 도움말 {#help}

도움말 아이콘은 학습 및 지원 리소스에 대한 바로 가기를 제공합니다.

![도움말](assets/help.png)

#### 알림 {#notifications}

이 아이콘에는 현재 할당된 불완전 [알림](/help/implementing/cloud-manager/notifications.md) 수가 배지로 지정됩니다.

![알림](assets/notifications.png)

#### 사용자 속성 {#user-properties}

사용자를 나타내는 아이콘을 선택하여 사용자 설정에 액세스합니다. 사용자 사진을 구성하지 않은 경우, 아이콘이 임의로 할당됩니다.

![사용자 속성](assets/user-properties.png)

### 범용 편집기 도구 모음 {#universal-editor-toolbar}

범용 편집기 도구 모음은 항상 아래 화면 상단에 있습니다 [Experience Cloud 헤더입니다.](#experience-cloud-header) 현재 페이지를 게시하고 편집할 다른 페이지에 바로 갈 수 있습니다.

![범용 편집기 도구 모음](assets/universal-editor-toolbar.png)

#### 홈 버튼 {#home-button}

홈 버튼을 누르면 유니버설 편집기의 시작 페이지로 돌아갑니다

![햄버거 메뉴](assets/home-button.png)

시작 페이지에서 범용 편집기로 편집할 사이트의 URL을 입력할 수 있습니다.

![시작 페이지](assets/start-page.png)

>[!NOTE]
>
>유니버설 편집기로 편집할 모든 페이지는 다음과 같아야 합니다. [유니버설 편집기를 지원하도록 계측되었습니다.](getting-started.md)

#### 위치 표시줄 {#location-bar}

위치 표시줄에 편집 중인 페이지의 주소가 표시됩니다. 편집할 다른 페이지의 주소를 입력하려면 선택하십시오.

![위치 표시줄](assets/location-bar.png)

>[!TIP]
>
>단축키 `L`을 사용하여 주소 표시줄을 엽니다.

>[!NOTE]
>
>유니버설 편집기로 편집할 모든 페이지는 다음과 같아야 합니다. [유니버설 편집기를 지원하도록 계측되었습니다.](getting-started.md)

#### 인증 헤더 설정 {#authentication-settings}

필요한 경우 인증 헤더 설정 아이콘 선택 [로컬 개발을 위해 사용자 지정 인증 헤더를 설정합니다.](/help/implementing/universal-editor/developer-overview.md#auth-header)

![인증 헤더 설정 단추](assets/authentication-header-settings.png)

#### 에뮬레이터 설정 {#emulator}

에뮬레이션 아이콘을 선택하여 범용 편집기에서 페이지를 렌더링하는 방법을 정의합니다.

![에뮬레이터 아이콘](assets/emulator.png)

에뮬레이션 아이콘을 탭하거나 클릭하면 옵션이 표시됩니다.

![에뮬레이션 옵션](assets/emulation-options.png)

기본적으로 편집기는 브라우저에서 높이와 너비를 자동으로 정의하는 데스크탑 레이아웃으로 열립니다.

Universal Editor에서 모바일 디바이스를 에뮬레이션할 수도 있습니다.

* 방향 정의
* 폭과 높이 정의
* 방향 변경

#### 미리보기 모드 {#preview-mode}

미리보기 모드의 페이지는 게시된 서비스에 표시되는 것처럼 편집기에서 렌더링된 페이지입니다. 이렇게 하면 콘텐츠 작성자는 링크 등을 클릭하여 콘텐츠를 탐색할 수 있습니다.

![미리보기 모드](assets/preview-mode.png)

>[!TIP]
>
>단축키 사용 `P` 을 클릭하여 미리 보기 모드에서 또는 미리 보기 모드로 전환합니다.

#### 앱 미리보기 열기 {#open-app-preview}

앱 미리 보기 열기 아이콘을 선택하여 편집기에서 벗어난 자체 브라우저 탭에서 현재 편집 중인 페이지를 열고 콘텐츠를 미리 봅니다.

![앱 미리보기 열기](assets/open-app-preview.png)

>[!TIP]
>
>단축키 `O`(O자)를 사용하여 앱 미리보기를 엽니다.

#### 게시 {#publish}

독자가 사용할 수 있도록 콘텐츠 라이브에 변경 사항을 게시할 수 있도록 게시 버튼을 선택합니다.

![게시 버튼](assets/publish.png)

>[!TIP]
>
>문서 보기 [유니버설 편집기로 콘텐츠 게시](publishing.md) 유니버설 편집기로 게시에 대한 자세한 내용을 보려면.

### 편집기 {#editor}

편집기는 창의 대부분을 차지하며 [위치 표시줄](#location-bar)에 지정된 페이지가 렌더링되는 곳입니다.

![편집기](assets/editor.png)

편집기가 [미리보기 모드](#preview-mode)에 있는 경우 콘텐츠를 탐색하고 링크를 따라갈 수 있지만, 콘텐츠를 편집할 수 없습니다.

### 속성 레일 {#properties-rail}

속성 레일은 항상 편집기의 오른쪽에 표시됩니다. 해당 모드에 따라 콘텐츠 또는 페이지 콘텐츠의 계층 구조에서 선택한 구성 요소에 대한 세부 정보를 표시할 수 있습니다.

![속성 레일](assets/component-rail.png)

#### 속성 모드 {#properties-mode}

속성 모드의 레일에 편집기에서 현재 선택한 구성 요소의 속성이 표시됩니다. 페이지가 로드될 때 속성 레일의 기본 모드입니다.

![속성 모드](assets/properties-mode.png)

선택한 구성 요소 유형에 따라 속성 레일에 세부 정보가 표시될 수 있으며 여기에서 해당 세부 정보를 수정할 수 있습니다.

![구성 요소 세부 정보](assets/component-details.png)

일부 구성 요소에 표시 및/또는 편집할 수 있는 세부 정보가 있는 것은 아닙니다.

>[!TIP]
>
>단축키 `D`를 사용하여 속성 모드로 전환합니다.

#### 콘텐츠 트리 모드 {#content-tree-mode}

콘텐츠 트리 모드의 경우 레일에 페이지 콘텐츠의 계층 구조가 표시됩니다.

![콘텐츠 트리 모드](assets/content-tree-mode.png)

콘텐츠 트리의 항목을 선택하면 편집기는 해당 콘텐츠를 스크롤하여 선택합니다.

![콘텐츠 트리](assets/content-tree.png)

>[!TIP]
>
>단축키 `F`를 사용하여 콘텐츠 트리 모드로 전환합니다.

##### 편집 {#edit}

편집할 때 선택한 구성 요소에 대한 옵션이 속성 레일에 나타나고 여기서 선택한 구성 요소를 편집할 수 있습니다. 선택한 구성 요소가 콘텐츠 조각인 경우 편집 버튼을 선택할 수도 있습니다.

![편집 아이콘](assets/edit.png)

편집 버튼을 탭하거나 클릭하면 새 탭에 [콘텐츠 조각 편집기](/help/assets/content-fragments/content-fragments-managing.md#opening-the-fragment-editor)가 열립니다. 이를 통해 콘텐츠 조각 편집기의 모든 기능에 액세스하여 연결된 콘텐츠 조각을 편집할 수 있습니다.

워크플로우의 필요에 따라 범용 편집기에서 또는 콘텐츠 조각 편집기에서 직접 콘텐츠 조각을 편집할 수 있습니다.

>[!TIP]
>
>단축키 `E`를 사용하여 선택한 구성 요소를 편집합니다.

##### 추가 {#add}

콘텐츠 트리 또는 편집기에서 컨테이너 구성 요소를 선택하면 속성 레일에 추가 옵션이 표시됩니다.

![추가 아이콘](assets/ue-add-component-icon.png)

추가 버튼을 탭하거나 클릭하면 [선택한 컨테이너에 추가](#adding-components)할 수 있는 구성 요소의 드롭다운 메뉴가 열립니다.

![상황에 맞는 메뉴 추가](assets/add-context-menu.png)

>[!TIP]
>
>단축키 `A`를 사용하여 선택한 컨테이너 구성 요소에 구성 요소를 추가합니다.

##### 삭제 {#delete}

콘텐츠 트리 또는 편집기에서 컨테이너 구성 요소 내의 구성 요소를 선택하면 속성 레일에 삭제 옵션이 표시됩니다.

![삭제 아이콘](assets/ue-delete-component-icon.png)

삭제 버튼을 탭하거나 클릭하면 [구성 요소가 삭제됩니다.](#deleting-components)

>[!TIP]
>
>단축키 `Shift+Backspace`를 사용하여 컨테이너에서 선택한 구성 요소를 삭제합니다.

## 콘텐츠 편집 {#editing-content}

콘텐츠 편집은 간단하고 직관적입니다. 편집기에서 콘텐츠 위로 마우스를 가져가면 편집 가능한 콘텐츠가 파란색 상자로 강조 표시됩니다.

![편집 가능한 콘텐츠는 파란색 상자로 강조 표시됩니다](assets/editable-content.png)

>[!TIP]
>
>기본적으로 콘텐츠를 탭하거나 클릭하면 편집할 콘텐츠가 선택됩니다. 링크를 따라 콘텐츠를 탐색하려면 다음으로 전환합니다. [미리 보기 모드.](#preview-mode)

선택한 콘텐츠에 따라 즉석 편집 옵션이 다를 수 있으며, 의 콘텐츠에 대한 추가 정보 및 옵션이 있을 수 있습니다. [속성 레일입니다.](#properties-rail)

### 일반 텍스트 편집 {#edit-plain-text}

구성 요소를 두 번 클릭하거나 두 번 탭하여 텍스트를 편집할 수 있습니다.

![콘텐츠 편집](assets/editing-content.png)

Enter/Return 키를 누르거나 텍스트 상자 바깥쪽을 선택하여 변경 내용을 저장합니다.

텍스트 구성 요소를 선택하기로 선택하면 해당 세부 사항이 속성 레일에 표시됩니다. 레일에서 텍스트를 편집할 수도 있습니다.

![속성 레일에서 텍스트 편집](assets/ue-editing-text-component-rail.png)

텍스트에 대한 자세한 내용은 속성 레일에서 확인할 수 있습니다. 포커스가 속성 레일의 편집된 필드를 떠나면 변경 사항이 자동으로 저장됩니다.

### 리치 텍스트 편집 {#edit-rich-text}

구성 요소를 두 번 클릭하거나 두 번 탭하여 텍스트를 편집할 수 있습니다.

![서식 있는 텍스트 구성 요소 편집](assets/rich-text-editing.png)

사용자의 편의를 위해 서식 옵션 및 텍스트에 대한 세부 사항을 두 곳에서 사용할 수 있습니다.

* 다음 **상황에 맞는 메뉴** 서식 있는 텍스트 블록 위에 열리며 컨텍스트에서 기본 서식 옵션을 제공합니다. 공간 제약으로 인해 일부 옵션이 줄임표 버튼 뒤에 숨겨질 수 있습니다.
* 다음 **속성 레일** 텍스트와 함께 사용할 수 있는 모든 서식 옵션을 표시합니다.

포커스가 편집된 필드를 떠나면 변경 사항이 자동으로 저장됩니다.

### 미디어 편집 {#edit-media}

속성 레일에서 세부 사항을 볼 수 있습니다.

![미디어 편집](assets/ue-edit-media.png)

1. 속성 레일에서 선택한 이미지의 미리보기를 탭하거나 클릭합니다.
1. 자산을 선택할 수 있는 [자산 선택기](/help/assets/asset-selector.md#using-asset-selector) 창이 열립니다.
1. 새 자산을 선택하려면 를 선택합니다.
1. 선택 **선택** 에셋이 교체된 속성 레일로 돌아갑니다.

변경 사항은 콘텐츠에 자동으로 저장됩니다.

### 콘텐츠 조각 편집 {#edit-content-fragment}

을(를) 선택하는 경우 [컨텐츠 조각,](/help/sites-cloud/administering/content-fragments/overview.md) 속성 레일에서 세부 사항을 편집할 수 있습니다.

![콘텐츠 조각 편집](assets/ue-edit-cf.png)

선택한 콘텐츠 조각의 콘텐츠 모델에 정의된 필드가 속성 레일에 표시되고 편집할 수 있습니다.

콘텐츠 조각과 관련된 필드를 선택하면 구성 요소 레일에 콘텐츠 조각이 로드되어 필드가 자동으로 스크롤됩니다.

포커스가 속성 레일의 편집된 필드를 떠나면 변경 사항이 자동으로 저장됩니다.

에서 콘텐츠 조각을 편집하려면 다음을 수행하십시오. [콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md) 대신 [편집 단추](#edit) 모드 레일에서 을 클릭합니다.

워크플로우의 필요에 따라 범용 편집기에서 또는 콘텐츠 조각 편집기에서 직접 콘텐츠 조각을 편집할 수 있습니다.

### 컨테이너에 구성 요소 추가 {#adding-components}

1. 콘텐츠 트리 또는 편집기에서 컨테이너 구성 요소를 선택합니다.
1. 그런 다음 속성 레일에서 추가 아이콘을 선택합니다.

   ![컨테이너에 추가할 구성 요소 선택](assets/ue-add-component.png)

구성 요소가 컨테이너에 삽입되며 편집기에서 편집할 수 있습니다.

>[!TIP]
>
>단축키 `A`를 사용하여 선택한 컨테이너에 구성 요소를 추가합니다.

### 컨테이너에서 구성 요소 삭제 {#deleting-components}

1. 콘텐츠 트리 또는 편집기에서 컨테이너 구성 요소를 선택합니다.
1. 컨테이너의 V자형 아이콘을 선택하여 콘텐츠 트리에서 해당 콘텐츠를 확장합니다.
1. 그런 다음 콘텐츠 트리에서 컨테이너 내의 구성 요소를 선택합니다.
1. 속성 레일에서 삭제 아이콘을 선택합니다.

   ![구성 요소 삭제](assets/ue-delete-component.png)

선택한 구성 요소가 삭제되었습니다.

>[!TIP]
>
>단축키 `Shift+Backspace`를 사용하여 해당 컨테이너에서 선택한 구성 요소를 삭제합니다.

### 컨테이너의 구성 요소 재정렬 {#reordering-components}

1. 콘텐츠 트리 또는 편집기에서 컨테이너 구성 요소를 선택합니다.
1. 아직 [콘텐츠 트리 모드](#content-tree-mode)가 아닌 경우 전환합니다.
1. 컨테이너의 V자형 아이콘을 선택하여 콘텐츠 트리에서 해당 콘텐츠를 확장합니다.
1. 컨테이너 내의 구성 요소 옆에 있는 드래그 핸들 아이콘은 구성 요소를 재정렬할 수 있음을 나타냅니다. 구성 요소를 드래그하여 컨테이너 내에서 재정렬합니다.

   ![구성 요소 재정렬](assets/ue-reordering-components.png)

1. 끌어온 구성 요소는 구성 요소 트리에서 회색으로 바뀌고 삽입 지점은 파란색 선으로 표시됩니다. 구성 요소를 놓아 새 위치에 배치합니다.

구성 요소는 콘텐츠 트리와 편집기 모두에서 재정렬됩니다.

## 콘텐츠 미리보기 {#previewing-content}

콘텐츠 편집을 마치면 콘텐츠를 탐색하여 다른 페이지의 콘텐츠에서 어떻게 보이는지 확인하고 싶은 경우가 많습니다. [미리보기 모드](#preview-mode)에서 링크를 클릭하여 독자처럼 콘텐츠를 탐색할 수 있습니다. 콘텐츠는 게시될 때 편집기에서 렌더링됩니다.

미리보기 모드에서 콘텐츠를 탭하거나 클릭하면 콘텐츠 판독기와 동일하게 반응합니다. 편집할 컨텐츠를 선택하려면 를 끄십시오 [미리 보기 모드.](#preview-mode)

## 추가 리소스 {#additional-resources}

Universal Editor에 대해 자세히 알아보려면 다음 문서를 참조하십시오.

* [유니버설 편집기로 콘텐츠 게시](publishing.md) - 유니버설 편집기에서 콘텐츠를 게시하는 방법과 앱에서 게시된 콘텐츠를 처리하는 방법에 대해 알아봅니다.
