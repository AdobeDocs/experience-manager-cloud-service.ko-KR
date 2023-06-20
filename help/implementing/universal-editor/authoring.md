---
title: Universal Editor로 콘텐츠 작성
description: 콘텐츠 작성자가 Universal Editor를 사용하여 얼마나 쉽고 직관적으로 콘텐츠를 만들 수 있는지 알아봅니다.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 84%

---

# Universal Editor로 콘텐츠 작성 {#authoring}

콘텐츠 작성자가 Universal Editor를 사용하여 얼마나 쉽고 직관적으로 콘텐츠를 만들 수 있는지 알아봅니다.

## 소개 {#introduction}

범용 편집기를 사용하면 모든 구현에서 콘텐츠의 모든 측면을 편집할 수 있으므로 탁월한 경험을 제공하고 콘텐츠 속도를 높이며 최신 개발자 경험을 제공할 수 있습니다.

이를 위해 제공되는 직관적인 UI는 콘텐츠 작성자가 최소한의 교육만 받으면 사용할 수 있어 바로 부담 없이 콘텐츠 편집을 시작할 수 있습니다.

>[!TIP]
>
>Universal Editor에 대한 자세한 소개는 [Universal Editor 소개](introduction.md) 문서를 참조하십시오.

>[!NOTE]
>
>Universal Editor는 아직 개발 중이며 현재 모든 콘텐츠 유형을 편집할 수 없습니다.

## 앱 준비 {#prepare-app}

범용 편집기를 사용하여 앱의 콘텐츠를 작성하려면 개발자가 앱을 계측하여 편집기를 지원해야 합니다.

>[!TIP]
>
>Universal Editor와 함께 작동하도록 AEM 앱을 구성하는 방법에 대한 예는 [AEM에서 Universal Editor 시작하기](getting-started.md) 문서를 참조하십시오.

## 로그인 {#sign-in}

Universal Editor와 함께 작동하도록 앱이 구성되었으면 Universal Editor에 로그인해야 합니다. 로그인하고 [Universal Editor에 액세스하려면](getting-started.md#request-access) Adobe ID가 필요합니다.

로그인한 후 편집할 페이지의 URL을 [주소 표시줄.](#address-bar) 시작할 수 있도록 [콘텐츠 편집.](#edit-content)

## UI 이해 {#ui}

UI는 크게 네 가지 영역으로 나뉩니다.

* [Experience Cloud 헤더](#experience-cloud-header)
* [Universal Editor 헤더](#universal-editor-header)
* [레일](#rail)
* [편집기](#editor)

![Universal Editor UI](assets/ui.png)

### Experience Cloud 헤더 {#experience-cloud-header}

Experience Cloud 헤더는 항상 화면 상단에 있습니다. Experience Cloud 내의 위치를 알려 주고 다른 Experience Cloud 앱으로 이동할 수 있도록 도와주는 앵커입니다.

![Experience Cloud 헤더](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

헤더 왼쪽에 있는 Adobe Experience Cloud 링크를 선택해 Experience Manager 솔루션의 루트로 이동하여 [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager,](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) [Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html) 등의 도구에 액세스합니다.

![전역 탐색 버튼](assets/global-navigation.png)

#### 조직 {#organization}

현재 로그인되어 있는 조직이 표시됩니다. Adobe ID가 여러 조직과 연결된 경우 탭하거나 클릭하여 다른 조직으로 전환합니다.

![조직 표시기](assets/organization.png)

#### 솔루션 {#solutions}

솔루션 전환기를 탭하거나 클릭하면 다른 Experience Cloud 솔루션으로 빠르게 이동할 수 있습니다.

![솔루션 전환기](assets/solutions.png)

#### 도움말 {#help}

도움말 아이콘은 학습 및 지원 리소스에 대한 빠른 액세스를 제공합니다.

![도움말](assets/help.png)

#### 알림 {#notifications}

이 아이콘에는 현재 할당된 미완료 항목 수가 배지로 지정되어 있습니다. [알림입니다.](/help/implementing/cloud-manager/notifications.md)

![알림](assets/notifications.png)

#### 사용자 속성 {#user-properties}

사용자를 나타내는 아이콘을 탭하거나 클릭하여 사용자 설정에 액세스합니다. 사용자 사진을 구성하지 않은 경우 아이콘이 임의로 할당됩니다.

![사용자 속성](assets/user-properties.png)

### Universal Editor 헤더 {#universal-editor-header}

Universal Editor 헤더는 항상 화면 상단의 [Experience Cloud 헤더 바로 아래에 있습니다.](#experience-cloud-header) 현재 페이지를 게시하고 편집할 다른 페이지에 빠르게 액세스할 수 있습니다.

![Universal Editor 헤더](assets/universal-editor-header.png)

#### 햄버거 메뉴 {#hamburger-menu}

햄버거 메뉴는 아직 구현되지 않았습니다.

![햄버거 메뉴](assets/hamburger-menu.png)

#### 위치 표시줄 {#Location-bar}

위치 표시줄에 편집 중인 페이지의 주소가 표시됩니다. 편집할 다른 페이지의 주소를 입력하려면 탭하거나 클릭합니다.

![위치 표시줄](assets/address-bar.png)

>[!TIP]
>
>단축키 `L`을 사용하여 주소 표시줄을 엽니다.

>[!NOTE]
>
>Universal Editor로 편집하려는 모든 페이지는 [Universal Editor를 지원하도록 구성](getting-started.md)되어야 합니다.

#### 앱 미리보기 열기 {#open-app-preview}

앱 미리보기 열기 아이콘을 탭하거나 클릭하면 현재 편집 중인 페이지가 자체 브라우저에서 열려 편집기 없이 변경 사항을 미리 볼 수 있습니다.

![앱 미리보기 열기](assets/open-app-preview.png)

>[!TIP]
>
>단축키 `O`를 사용하여 앱 미리보기를 엽니다.

#### 게시 {#publish}

게시 버튼을 탭하거나 클릭하여 독자가 사용할 수 있도록 콘텐츠 라이브에 변경 사항을 게시할 수 있습니다.

![게시 버튼](assets/publish.png)

>[!TIP]
>
>Universal Editor로 게시하는 방법에 대한 자세한 내용은 [Universal Visual Editor로 콘텐츠 게시](publishing.md) 문서를 참조하십시오.

### 레일 {#rail}

레일은 항상 편집기의 왼쪽에 있습니다. 이를 통해 미리보기 모드와 편집 모드 간에 편집기를 쉽게 전환할 수 있습니다.

![레일](assets/rail.png)

#### 미리보기 모드 {#preview-mode}

미리보기 모드의 페이지는 게시된 서비스에 표시되는 것처럼 편집기에서 렌더링된 페이지입니다. 따라서 콘텐츠 작성자가 링크 등을 클릭하여 콘텐츠를 탐색할 수 있습니다.

![미리보기 모드](assets/preview-mode.png)

>[!TIP]
>
>단축키 `P`를 사용하여 미리보기 모드로 전환합니다.

#### 편집 모드 {#edit-mode}

편집 모드에서는 페이지가 편집기에서 렌더링되지만 콘텐츠 작성자가 콘텐츠를 클릭하여 편집할 콘텐츠를 선택할 수 있습니다. 페이지가 로드될 때 편집기의 기본 모드입니다.

![편집 모드](assets/edit-mode.png)

### 편집기 {#editor}

편집기는 창의 대부분을 차지하며 [주소 표시줄](#address-bar)에 지정된 페이지가 렌더링되는 곳입니다.

편집기가 [편집 모드](#edit-mode)인지 [미리보기 모드](#edit-mode)인지에 따라 각각 콘텐츠를 편집하거나 탐색할 수 있습니다.

![편집기](assets/editor.png)

## 콘텐츠 편집 {#editing-content}

콘텐츠 편집은 간단하고 직관적입니다. 위치 [편집 모드,](#edit-mode) 편집기에서 콘텐츠 위로 마우스를 가져가면 편집 가능한 콘텐츠가 파란색 상자로 강조 표시됩니다.

![편집 가능한 콘텐츠는 파란색 상자로 강조 표시됩니다](assets/editable-content.png)

파란색 상자에 있는 콘텐츠를 탭하거나 클릭하면 바로 편집기를 시작하여 변경할 수 있습니다. Enter 키 또는 Return 키를 눌러 변경 사항을 저장합니다.

![콘텐츠 편집](assets/editing-content.png)

편집 모드에서 콘텐츠를 탭하거나 클릭하면 편집할 콘텐츠가 선택됩니다. 링크를 이용하여 콘텐츠를 탐색하려면 [미리보기 모드](#preview-mode)로 전환합니다.

## 콘텐츠 미리보기 {#previewing-content}

콘텐츠 편집을 마치면 콘텐츠를 탐색하여 다른 페이지의 콘텐츠에서 어떻게 보이는지 확인하고 싶은 경우가 많습니다. [미리보기 모드](#preview-mode)에서 링크를 클릭하여 독자처럼 콘텐츠를 탐색할 수 있습니다. 콘텐츠는 게시될 때 편집기에서 렌더링됩니다.

미리보기 모드에서 콘텐츠를 탭하거나 클릭하면 콘텐츠 독자에게 반응하는 것처럼 반응합니다. 편집할 콘텐츠를 선택하려면 [편집 모드](#edit-mode)로 전환합니다.

## 추가 리소스 {#additional-resources}

Universal Editor에 대해 자세히 알아보려면 다음 문서를 참조하십시오.

* [유니버설 편집기 소개](introduction.md) - Universal Editor를 통해 모든 구현에서 콘텐츠의 모든 측면을 편집할 수 있으므로 탁월한 경험을 제공하고 콘텐츠 속도를 높이며 최신 개발자 경험을 제공할 수 있습니다.
* [Universal Editor로 콘텐츠 게시](publishing.md) - Universal Visual Editor에서 콘텐츠를 게시하는 방법과 앱에서 게시된 콘텐츠를 처리하는 방법에 대해 알아봅니다.
* [AEM에서 Universal Editor 시작하기](getting-started.md) - Universal Editor에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.
* [Universal Editor 아키텍처](architecture.md) - Universal Editor의 아키텍처 및 해당 서비스와 계층 간에 데이터가 흐르는 방식에 대해 알아봅니다.
* [속성 및 유형](attributes-types.md) - Universal Editor에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [Universal Editor 인증](authentication.md) - Universal Editor의 인증 방법에 대해 알아봅니다.
