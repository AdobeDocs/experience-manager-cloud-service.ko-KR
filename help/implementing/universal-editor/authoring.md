---
title: 범용 편집기를 사용하여 컨텐츠 작성
description: 컨텐츠 작성자가 범용 편집기를 사용하여 컨텐츠를 만드는 것이 얼마나 쉽고 직관적인지를 알아봅니다.
source-git-commit: 0e66c379e10d275610d85a699da272dc0c32a9a8
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 2%

---


# 범용 편집기를 사용하여 컨텐츠 작성 {#authoring}

컨텐츠 작성자가 범용 편집기를 사용하여 컨텐츠를 만드는 것이 얼마나 쉽고 직관적인지를 알아봅니다.

## 소개 {#introduction}

범용 편집기를 사용하면 구현에서 모든 컨텐츠의 모든 측면을 편집하여 뛰어난 경험을 제공하고 컨텐츠 속도를 높이며 최신 개발자 경험을 제공할 수 있습니다.

이를 위해 컨텐츠 작성자에게 간단하게 참여하여 컨텐츠 편집을 시작할 수 있도록 최소한의 교육을 필요로 하는 직관적인 UI를 제공합니다.

>[!TIP]
>
>범용 편집기에 대한 자세한 내용은 문서를 참조하십시오 [범용 편집기 소개.](introduction.md)

>[!NOTE]
>
>범용 편집기는 아직 개발 중이며 현재 모든 컨텐츠 유형을 편집할 수 없습니다.

## 앱 준비 {#prepare-app}

범용 편집기를 사용하여 앱의 컨텐츠를 작성하려면 개발자가 해당 앱을 계측하여 편집기를 지원해야 합니다.

>[!TIP]
>
>문서 보기 [AEM에서 범용 편집기 시작하기](getting-started.md) 범용 편집기에서 작동하도록 AEM 앱을 구성하는 방법에 대한 예입니다.

## 로그인 {#sign-in}

앱이 범용 편집기에서 작동하도록 구현되면 범용 편집기에 로그인해야 합니다. 로그인하려면 Adobe ID이 필요합니다. [범용 편집기에 액세스할 수 있습니다.](getting-started.md#request-access)

로그인하고 나면 편집할 페이지의 URL을 [주소 표시줄.](#address-bar) 시작하기 위해 [컨텐츠 편집.](#edit-content)

## UI 이해 {#ui}

UI는 4개의 기본 영역으로 나누어집니다.

* [Experience Cloud 헤더](#experience-cloud-header)
* [범용 편집기 헤더](#universal-editor-header)
* [레일](#rail)
* [편집자](#editor)

![범용 편집기 UI](assets/ui.png)

### Experience Cloud 헤더 {#experience-cloud-header}

Experience Cloud 헤더는 항상 화면 맨 위에 있습니다. Experience Cloud 내의 위치를 알리고 다른 Experience Cloud 앱으로 이동하는 데 도움이 되는 앵커입니다.

![Experience Cloud 헤더](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

헤더 왼쪽의 Adobe Experience Cloud 링크를 선택하여 Experience Manager 솔루션의 루트로 이동하여 와 같은 도구에 액세스합니다 [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager,](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) 및 [소프트웨어 배포.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)

![전역 탐색 단추](assets/global-navigation.png)

#### 조직 {#organization}

현재 로그인한 조직이 표시됩니다. Adobe ID이 여러 조직과 연결된 경우 탭하거나 클릭하여 다른 조직으로 전환합니다.

![조직 표시기](assets/organization.png)

#### 솔루션 {#solutions}

솔루션 전환기를 탭하거나 클릭하면 다른 Experience Cloud 솔루션으로 빠르게 이동할 수 있습니다.

![솔루션 전환기](assets/solutions.png)

#### 도움말 {#help}

도움말 아이콘을 통해 학습 및 지원 리소스에 빠르게 액세스할 수 있습니다.

![도움말](assets/help.png)

#### 알림 {#notifications}

이 아이콘에는 현재 할당된 불완전 개수가 배지로 지정됩니다 [알림.](/help/implementing/cloud-manager/notifications.md)

![알림](assets/notifications.png)

#### 사용자 속성 {#user-properties}

사용자를 나타내는 아이콘을 탭하거나 클릭하여 사용자 설정에 액세스합니다. 사용자 이미지가 구성되어 있지 않으면 아이콘이 임의로 할당됩니다.

![사용자 속성](assets/user-properties.png)

### 범용 편집기 헤더 {#universal-editor-header}

범용 편집기 헤더는 항상 바로 아래 화면 맨 위에 있습니다 [Experience Cloud 헤더.](#experience-cloud-header) 이 링크를 통해 편집할 다른 페이지로 이동하여 현재 페이지를 게시할 수 있습니다.

![범용 편집기 헤더](assets/universal-editor-header.png)

#### 햄버거 메뉴 {#hamburger-menu}

햄버거 메뉴는 아직 구현되지 않았습니다.

![햄버거 메뉴](assets/hamburger-menu.png)

#### 위치 표시줄 {#Location-bar}

위치 모음에는 편집 중인 페이지의 주소가 표시됩니다. 편집할 다른 페이지의 주소를 입력하려면 탭하거나 클릭하십시오.

![위치 표시줄](assets/address-bar.png)

>[!TIP]
>
>핫키 사용 `L` 주소 표시줄을 엽니다.

>[!NOTE]
>
>범용 편집기로 편집할 모든 페이지는 [범용 편집기를 지원하도록 계측되었습니다.](getting-started.md)

#### 앱 미리 보기 열기 {#open-app-preview}

앱 미리 보기 열기 아이콘을 탭하거나 클릭하여 현재 편집 중인 페이지를 자체 브라우저에서 열고, 편집기에서 변경 사항을 미리 볼 수 있습니다.

![앱 미리 보기 열기](assets/open-app-preview.png)

>[!TIP]
>
>핫키 사용 `O` 앱 미리 보기를 열려면 다음을 수행하십시오.

#### 게시 {#publish}

독자가 사용할 수 있도록 컨텐츠 변경 사항을 라이브로 게시하려면 게시 단추를 탭하거나 클릭합니다.

![게시 버튼](assets/publish.png)

>[!TIP]
>
>문서를 참조하십시오 [범용 시각적 편집기를 사용하여 컨텐츠 게시](publishing.md) 범용 편집기를 사용한 게시에 대한 자세한 내용을 살펴보십시오.

### 레일 {#rail}

레일은 항상 편집기의 왼쪽에 표시됩니다. 미리 보기 모드와 편집 모드 간에 편집기를 쉽게 전환할 수 있습니다.

![레일](assets/rail.png)

#### 미리보기 모드 {#preview-mode}

미리 보기 모드에서는 게시된 서비스에서 볼 수 있듯이 편집기에서 렌더링됩니다. 이렇게 하면 컨텐츠 작성자가 링크 등을 클릭하여 컨텐츠를 탐색할 수 있습니다.

![미리 보기 모드](assets/preview-mode.png)

>[!TIP]
>
>핫키 사용 `P` 미리 보기 모드로 전환하려면 다음을 수행하십시오.

#### 편집 모드 {#edit-mode}

편집 모드에서는 페이지가 편집기에 렌더링되지만 컨텐츠 작성자는 클릭하여 편집할 컨텐츠를 선택할 수 있습니다. 페이지를 로드할 때 편집기의 기본 모드입니다.

![편집 모드](assets/edit-mode.png)

### 편집자 {#editor}

편집기는 창의 대부분을 차지하며 페이지가 지정된 위치입니다. [주소 표시줄](#address-bar) 가 렌더링됩니다.

편집기가 [편집 모드](#edit-mode) 또는 [미리 보기 모드,](#edit-mode) 컨텐츠는 각각 편집 가능하거나 탐색할 수 있습니다.

![편집자](assets/editor.png)

## 컨텐츠 편집 {#editing-content}

컨텐츠 편집은 간단하고 직관적입니다. in [편집 모드,](#edit-mode) 편집기에서 컨텐츠 위에 마우스를 가져가면 편집 가능한 컨텐츠가 파란색 상자로 강조 표시됩니다.

![편집 가능한 컨텐츠는 파란색 상자로 강조 표시됩니다](assets/editable-content.png)

파란색 상자에 있는 콘텐츠를 탭하거나 클릭하여 즉석 편집기를 시작하여 변경 작업을 수행하면 됩니다. Enter 키를 누르거나 Return 키를 눌러 변경 내용을 저장합니다.

![컨텐츠 편집](assets/editing-content.png)

편집 모드에서 컨텐츠를 탭하거나 클릭하면 편집할 콘텐츠를 선택하려고 합니다. 다음 링크를 통해 컨텐츠를 탐색하려면 로 전환합니다. [미리 보기 모드.](#preview-mode)

## 콘텐츠 미리보기 {#previewing-content}

컨텐츠 편집을 완료하면 컨텐츠를 탐색하여 다른 페이지의 컨텐츠에서 컨텐츠 모양을 확인하는 경우가 많습니다. in [미리 보기 모드](#preview-mode) 리더기와 마찬가지로 링크를 클릭하여 컨텐츠를 탐색할 수 있습니다. 컨텐츠가 게시되는 대로 편집기에 렌더링됩니다.

미리 보기 모드에서는 컨텐츠를 탭하거나 클릭하면 컨텐츠의 리더와 마찬가지로 반응합니다. 편집할 콘텐츠를 선택하려면 로 전환합니다. [편집 모드.](#edit-mode)

## 추가 리소스 {#additional-resources}

범용 편집기에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [범용 편집기 소개](introduction.md) - 범용 편집기를 사용하면 모든 구현에서 컨텐츠의 모든 측면을 편집할 수 있어 뛰어난 경험을 제공하고 컨텐츠 속도를 높이며 최신 개발자 경험을 제공할 수 있습니다.
* [범용 편집기를 사용하여 컨텐츠 게시](publishing.md) - 유니버설 시각적 편집기에서 콘텐츠를 게시하는 방법과 앱이 게시된 콘텐츠를 처리하는 방법을 알아봅니다.
* [AEM에서 범용 편집기 시작하기](getting-started.md) - 범용 편집기에 액세스하는 방법과 첫 번째 AEM 앱 계측을 시작하여 이를 사용하는 방법을 알아봅니다.
* [범용 편집기 아키텍처](architecture.md) - 범용 편집기의 아키텍처와 서비스 및 레이어 간에 데이터가 어떻게 이동되는지 알아봅니다.
* [속성 및 유형](attributes-types.md) - 범용 편집기에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [범용 편집기 인증](authentication.md) - 유니버설 편집기가 인증되는 방법을 알아봅니다.
