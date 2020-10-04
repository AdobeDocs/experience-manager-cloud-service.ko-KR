---
title: 액세스 가능성 [!DNL Experience Manager Assets]
description: Cloud Service의 액세서빌러티 기능 [!DNL Adobe Experience Manager] 이 장애가 있는 사용자에게 어떤 도움이 되는지 살펴보십시오.
contentOwner: AG
translation-type: tm+mt
source-git-commit: d0be8ff6c8f9e0c37bd4dc9f66d80e19ab7e1508
workflow-type: tm+mt
source-wordcount: '1840'
ht-degree: 2%

---


<!--
Original scope of this article for Core Assets for all a11y topics is around the following topics. This has changed since then but keeping this list of topics for posterity's sake.

* Convert the absolute doc links to relative links.
* Add an overview
* Compile a list of enhancements done in the last ~1 year.
* Top-level actions supported, such as clickable UI elements, keyboard shortcuts, popup dialogs, etc.)
* Specific user tasks supported, such as, download assets, datepicker, editing metadata, etc.
* Support matrix of user tasks with browsers and screen readers + OSes combinations
* Exceptions that users should be aware of.
* CTA – what is next and more info from AEM team:
  * Link to ACRs on a.com.
  * Generic a11y info by Adobe to begin with.
  * Examples of other a11y DX Docs from Elle.
  * Link to a11y-specific channels to report issues, seek support, or request enhancements, if any. Available info from Elle.
-->

# Cloud Service [!DNL Adobe Experience Manager Assets] 의 접근성 {#accessibility-in-aem-assets}

Adobe은 장애인을 포함한 모든 사용자를 위한 제품을 만들기 위해 노력하고 있습니다. [!DNL Adobe Experience Manager] 는 모든 유형의 사용자의 요구 사항을 충족하도록 지속적으로 개선됩니다. [!DNL Experience Manager] 표준을 자세히 설명하고 제품의 액세서빌러티 기능에 대해 개요를 설명하고 규정 준수 수준을 설명하는 적합성 정보를 게시합니다. 따라서 사용자는 Adobe Acrobat Connect를 통해 Acrobat Connect Pro를 사용할 수 있습니다.

[!DNL Adobe Experience Manager] 는 다음 표준에 대한 다양한 수준의 지원을 제공합니다.

* [웹 컨텐츠 액세스 가능성 지침(WCAG) 2.1](https://www.w3.org/TR/WCAG/).
* [조항 508](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines)개정
* [WAI-ARIA](https://www.w3.org/WAI/standards-guidelines/aria/).
* [EN 301 549](https://en.wikipedia.org/wiki/EN_301_549).

준수 수준을 자세히 설명하는 보고서에 액세스하려면 모든 Adobe 솔루션에 대한 [액세스 가능성 보고서 ](https://www.adobe.com/accessibility/compliance.html) (ACR) 페이지를 참조하십시오.

## 보조 기술 {#at-support}

장애가 있는 사용자는 자주 하드웨어와 소프트웨어에 의존하여 웹 컨텐츠에 액세스합니다. 이러한 도구는 보조 기술이라고 합니다. [!DNL Adobe Experience Manager Assets] 소프트웨어의 핵심 기능을 사용할 때 사용자가 지원할 수 있도록 다음과 같은 유형의 보조 기술을 사용해 작업합니다.

* 화면 판독기
* 음성 인식 소프트웨어
* 키보드 사용 - 탐색 및 바로 가기
* 스위치 컨트롤, 새로 고침 가능한 점자 디스플레이, 기타 컴퓨터 입력 디바이스 등 보조 하드웨어입니다.
* UI 확대 툴

## [!DNL Experience Manager Assets] 액세스 가능한 사용 사례 {#accessible-assets-use-cases}

액세스 [!DNL Experience Manager]기능 [!DNL Experience Manager] 은 사용자와 고객의 두 가지 주요 요구 사항을 해결합니다.

컨텐츠 디자이너와 크리에이티브를 위해 고객과 웹 사이트 방문자가 차례로 사용하는 액세스 가능한 컨텐츠를 만들고 게시하는 기능이 있습니다. 이 컨텐츠는 보조 기술의 도움을 받아 장애가 있는 사람들이 사용할 수 있습니다. 자세한 내용은 [웹 액세스 가능성 지침을 참조하십시오](/help/onboarding/accessibility/web-accessibility.md).

또한 장애가 있는 사용자와 관리자가 사용자 인터페이스와 컨트롤에 액세스하여 컨텐츠를 만들고 관리할 수 있습니다. [!DNL Experience Manager] 장애가 있는 사용자는 보조 기술을 사용하여 해당 기능을 탐색, 사용 및 관리할 수 [!DNL Assets] 있습니다.

의 핵심 기능 [!DNL Assets] 은 이전보다 더 쉽게 액세스할 수 있으며 정기적으로 업데이트되어 글로벌 표준 준수를 향상시킵니다. 자산의 CRUD 작업은 이러한 작업 내에 일종의 액세서빌러티를 가집니다. 키보드 단축키, 화면 판독기 텍스트, 색상 대비 등을 사용하면 에셋 추가, 관리, 검색 및 배포와 같은 DAM 워크플로우를 이용할 수 있습니다.

## 키보드 사용 지원 {#keyboard-use}

포인터를 사용하여 클릭 가능하거나 실행 가능한 많은 사용자 인터페이스 요소도 키보드를 사용하여 연결할 수 있습니다. 사용자는 키보드를 사용하여 UI 요소에 중점을 두고 적절한 작업을 수행할 수 있습니다. 사용자는 키보드 단축키를 사용하여 UI 요소에 초점을 맞추고 키보드를 사용하여 트리거하지 않고도 명령 또는 동작을 트리거할 수 있습니다. 예를 들어, 사용자는 키보드를 사용하여 UI 컨트롤을 탐색하고 Return 키를 누르고 `alt + 2` 키보드 단축키를 눌러 왼쪽의 에셋의 타임라인을 열 수 있습니다.

<!-- TBD items:

* The button/menu to toggle between list view and card view exposes relevant info to the screen readers. What about column view option? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* How to open and browse through the profile popup dialog in [!DNL Experience Manager] UI using a keyboard? The navigation does not match the order of visual display of options on the UI. This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’. What about setting preferences and impersonating a user?
* Using the [!DNL Experience Manager] tag browser and operating the buttons like delete tag? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* Read-only form fields can be focused with the keyboard. Can users tab to these fields to understand the contents and are they able to copy text from the fields?
-->

### 에셋의 키보드 단축키 {#keyboard-shortcuts}

<!-- TBD: Add here only those keyboard shortcuts that work for/with Assets. Do with Oct release.
-->

| 사용자 인터페이스 또는 시나리오 | 키보드 단축키 | 작업 |
|---|---|---|
| 자산 사용자 인터페이스의 열 보기 | 위쪽 및 아래쪽 화살표 키 | 동일한 계층 구조 내의 파일 및 폴더로 이동합니다. |
| 자산 사용자 인터페이스의 열 보기 | 왼쪽 및 오른쪽 화살표 키 | 현재 폴더 위 또는 아래로 파일과 폴더를 탐색합니다. |
| 자산에서 폴더 찾아보기 | `/` | Omnisearch 상자를 열어 검색을 호출합니다. |
| 자산 콘솔 | ` | 사이드 레일 전환 |
| 자산 콘솔 | Alt + 1 | 컨텐츠 트리를 엽니다. |
| 자산 콘솔 | Alt + 2 | 탐색 [!UICONTROL 사이드레이를] 엽니다. |
| 자산 콘솔 | Alt + 3 | 선택한 [!UICONTROL 자산의 타임라인] 표시 |
| 자산 콘솔 | Alt + 4 | 선택한 자산의 Live Copy 참조를 엽니다. |
| 자산 콘솔 | Alt + 5 | 선택한 폴더 내에서 검색 및 검색을 호출합니다. |
| 자산 또는 폴더를 선택했습니다. | 백스페이스 | 선택한 자산 또는 폴더를 삭제합니다. |
| 자산 또는 폴더를 선택했습니다. | `p` | 선택한 자산의 속성 페이지를 엽니다. |
| 자산 또는 폴더를 선택했습니다. | `e` | 선택한 자산을 편집합니다. |
| 자산 또는 폴더를 선택했습니다. | `m` | 선택한 자산을 이동합니다. |
| 자산 또는 폴더를 선택했습니다. | Ctrl+c | 선택한 자산을 복사합니다. |
| 자산 또는 폴더를 선택했습니다. | Esc | 선택 항목을 선택 취소합니다. |
| 대화 상자가 열리고 포커스가 있습니다. | Esc | 대화 상자 닫기 |
| DAM의 폴더 내부 | Ctrl+v | 복사한 자산을 붙여넣습니다. |
| 자산 콘솔 | Ctrl + A | 모든 자산을 선택합니다. |
| 자산 속성 페이지 | Ctrl + S | 변경 사항을 저장합니다. |
| 자산 콘솔 | `?` | 키보드 단축키 목록을 참조하십시오. |

콘솔에 적용되는 대부분의 키보드 단축키도 자산에 [!DNL Experience Manager] 적용됩니다. See [Keyboard Shortcuts for Consoles](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/essentials/keyboard-shortcuts.html). 키보드 단축키를 [활성화하거나 비활성화하는 방법을 참조하십시오](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md).

## 로그인 및 [!DNL Assets] 사용자 인터페이스 탐색 {#login}

사용자는 키보드를 사용하여 로그인 필드로 이동하여 입력하여 로그인할 수 있습니다. 로그인 페이지의 잘못된 사용자 이름과 암호 조합으로 인한 오류 메시지는 오류가 발생할 때마다 화면 판독기에서 알려줍니다.

로그인하면 DAM 사용자가 키보드를 사용하여 [!DNL Assets] 사용자 인터페이스로 이동할 수 있습니다. 키보드 탐색 순서는 왼쪽에서 오른쪽 및 위에서 아래로 지정됩니다. 키보드를 사용하여 탐색할 때 초점이 맞춰진 모든 실행 가능한 옵션은 향상된 색상 대비로 강조 표시되고 화면 판독기에서 내레이션이 적용됩니다. 메뉴에서 초점이 맞춰진 옵션의 확장 또는 축소 상태는 화면 판독기로 표시됩니다.

사용자가 메뉴에서 도움말 또는 사용자 프로필 옵션을 확장하면 해당 옵션이나 상태가 화면 판독기로 표시됩니다. 사용자가 사용자 프로필 옵션을 확장하면 키보드를 사용하여 사용 가능한 옵션을 선택할 수 있습니다. 예를 들어, 사용자는 다른 사용자로 가장할 수 있습니다. 사용자 인터페이스 옵션 및 오류 메시지

![Experience Manager 유저 인터페이스의 주요 옵션 키보드 탐색](assets/keyboard-navigation-in-aem.gif)

*그림:키를 사용하여 Experience Manager 사용자 인터페이스 상단에 있는 옵션을 탐색합니다.`Tab`*

사용자가 [!UICONTROL 도움말] 옵션에서 문자열을 검색하는 경우 내레이터는 검색이 진행 중임을 나타내는 &#39;도움말 검색&#39;을 발표합니다.

## 기존 에셋 검색 및 관련 정보 보기 {#browse}

사용자 [!DNL Assets] 인터페이스에서 사용자는 키보드를 사용하여 DAM 저장소의 기존 디지털 자산 목록을 찾아보거나, 자산을 미리 보거나 다운로드할 수 있고, 생성된 표현물을 보고, 보기를 전환하고, 생성된 표현물을 보고, 타임라인과 버전 내역을 보고, 주석과 참조를 보고, 메타데이터를 보고 관리할 수 있습니다.

<!-- TBD: Not sure about the following list items mean:

In Experience Manager header section, when navigating in browse mode, screen reader now announces,
  
  * Suggestions to search in Omnisearch.
  * The state as expanded or collapsed for Solutions, Help, Inbox and User options.
  * The Searching Help status message that is displayed when user enters a search string in Search for Help field under Help option
  * The error message if incorrect value is entered in Impersonate as field under User option and focus correctly moves to the text field (NPR-33804).

Review CQ-4282133 before adding - Close button in a coral-dialog wasn't accessible through keyboard, due to which user cannot trigger close button through keyboard press in version preview dialog. After fix, user can close dialog through close button using keyboard.

* CQ-4273122 - Assets of video/audio type will have aria-label in format "Multimedia player: <Title>" so users relying on screen-reader will get to know that they are video/audio assets.
-->

자산 저장소를 검색할 때 다음 기능을 통해 액세서빌러티가 개선됩니다.

* 화면 판독기는 이름 대신 아이콘의 용도와 기능을 설명하는 텍스트 대체 요소를 선언합니다.
* 사용자는 키보드 키를 사용하여 에셋 목록 참조에서 인터랙티브한 유저 인터페이스 옵션에 액세스하고 집중할 수 있습니다.
* 목록 보기의 각 행에 있는 요소는 화면 판독기로 동일한 행의 요소로 선언됩니다.
* 키를 사용하여 탐색할 때 사용자의 포커스가 버전 미리 보기의 닫기 옵션으로 이동할 수 `Tab` 있습니다.
* 키보드를 사용하여 검색할 때 강조 표시된 실행 가능한 유저 인터페이스 옵션은 향상된 대비 기능을 사용하여 보다 눈에 잘 띄는 초점을 갖습니다. 따라서 사용자가 집중된 영역을 보다 쉽게 식별할 수 있습니다.
* 축소판 보기에서 빠른 작업 아이콘을 제거할 때 `Esc` 키를 사용해도 마지막 초점을 맞춘 항목에서 키보드 포커스가 제거되지 않습니다.
* 자산을 선택한 상태에서 Alt + 4 키보드 단축키를 누르면 참조 목록이 열립니다. 키를 사용하여 `Tab` 아무 것도 없는 참조 항목을 탐색할 수 있습니다.
* 자산에 대한 주석을 자산 타임라인에서 사용할 수 있습니다. 키보드로 이용할 수 있습니다.
* Experience Manager의 보기 설정은 키보드를 통해 액세스할 수 있습니다. 사용자는 화살표 키를 사용하여 사용 가능한 카드 크기를 탐색하고 선택 및 탭하여 기존 보기 설정 보기에서 다른 요소를 탐색하고 설정할 수 있습니다.

<!-- TBD: Gradually,  as more enhancements are done in these categories, add more content.

## Add and upload digital assets {#upload}

## Configure and administer [!DNL Assets] {#config-admin}

* List the a11y fixes in workflows to configure and administer [!DNL Experience Manager Assets]?
* Some enhancements in Processing profiles creation or application to a folder?
* Some enhancements to metadata properties UI?

-->

## 디지털 자산을 관리합니다 {#manage-assets}

CRUD 작업, 에셋 다운로드, 메타데이터 추가 등 다양한 에셋 관리 작업을 다각도로 액세스할 수 있습니다. 에셋을 사용하면 화면 판독기 및 키보드 등 다양한 보조 기술을 사용하여 작업을 수행할 수 있습니다.

키보드를 사용하여 저장소를 [탐색하고 자산을 다운로드하는 방법에 대한 비디오 데모를 참조하십시오](https://youtu.be/K3dgqMRQJys).

마케터 및 관리자와 같은 역할에 의해 일반적으로 수행되는 메타데이터 작업의 경우 다음 기능이 액세서빌러티를 향상시킵니다.

* [!UICONTROL 자산 속성 페이지의 저장 및 닫기] 옵션은 키보드를 사용하여 액세스할 수 있습니다.
* 화면 판독기는 선택한 태그를 삭제하기 위해 자산 속성 단추의 기본 탭에서 선택한 태그를 삭제하는 옵션을 알려줍니다.
* 날짜 선택기 팝업 대화 상자는 키보드를 사용하여 사용할 수 있습니다. Datepicker는 설정 및 해제 시간을 설정하는 데 사용됩니다.
* 키보드를 사용하는 드래그 기능은 화면 판독기의 검색 모드에서 메타데이터 스키마 편집기에서 올바르게 작동합니다.
* 키보드를 사용하여 폴더 속성의 권한 탭에 있는 폐쇄된 사용자 그룹 아래의 사용자 또는 그룹 추가 필드로 초점을 이동할 수 있습니다.

## 디지털 에셋 검색 {#search-assets}

신속하고 원활한 에셋 검색 경험을 통해 콘텐츠 제작 시간을 단축할 수 있습니다. 콘텐츠 속도 사용 사례는 핵심 [!DNL Assets] 기능의 일부입니다. Omnisearch 막대에서 검색을 시작하려면 키보드 단축키 `/` 를 사용하거나 화면 판독기 `Tab` 와 함께 검색 옵션을 신속하게 찾을 수 있습니다. 포커스가 검색 옵션 [!UICONTROL 검색 옵션] 에 있으면 화면 판독기에서 옵션 이름을 [ ![검색 단추](assets/do-not-localize/search_icon.png)]로 내레이션합니다. 키를 눌러 Omnisearch 상자 `Return` 를 열 수 있습니다. 화면 판독기는 검색 상자에 입력한 키워드에 대해 내레이션할 뿐만 아니라 사용자가 제공하는 제안에도 내레이션이 있습니다 [!DNL Experience Manager Assets]. 사용자는 화살표 키 `Return`를 조합하여 사용할 수 있으며, 다양한 옵션에 액세스하여 검색을 시작할 `Tab` 수 있습니다.

검색 기능은 다음 기능을 통해 더 쉽게 액세스할 수 있습니다.

* 화면 판독기에서 사용할 수 있는 페이지 제목은 페이지를 자산의 검색 페이지로 식별하는 데 도움이 됩니다.
* 사용자는 Omnisearch 막대 내에서 자산을 검색합니다. 키보드 키 또는 키보드 단축키를 사용하여 Omnisearch 막대 `/` 에 액세스할 수 있습니다.
* 검색 키워드를 입력하고 키보드를 사용하여 자동 제안을 선택합니다. Return 키를 눌러 자동 제안된 문자열을 적용하고 해당 문자열을 검색합니다.
* 검색 결과를 필터링할 때 화면 판독기는 [필터] 패널에서 중첩된 모든 표식을 선택하지 않고 첫 번째 수준의 확인란은 선택하지 않고 통과되지 않는 혼합 상태 확인란을 식별하고 발표할 수 있습니다.
* Omnisearch 상자가 닫힌 후 사용자 포커스가 검색 옵션으로 이동합니다.

검색 결과를 필터링할 때:

* 검색 결과 페이지에는 화면 판독기 사용자를 더 잘 이해할 수 있는 정보가 포함된 제목이 있습니다.
* 화면 판독기는 검색 필터의 옵션을 확장 가능한 아코디언으로 발표합니다.
* 상태 단추가 혼합된 것은 화면 판독기에 의해 발표됩니다.

## 자산 공유 {#share-assets}

<!-- TBD: Accessibility in DA, BP, AAL? Asked CCE team for AAL content?
-->

자산을 공유할 때 다음 기능은 액세스 가능성을 개선합니다.

* 사용자는 링크 공유 대화 상자의 검색 및 이메일 주소 추가 필드 내에서 키보드를 사용하여 포커스를 이동할 수 있습니다.

* 링크 공유 대화 상자에서 찾아보기 모드에서 탐색할 때 화면 판독기에서

   * 대화 상자가 로드되는 즉시 테이블 정보를 분류하지 마십시오.
   * 나열된 모든 제안으로 이동할 수 있습니다.
   * 이메일 주소 및 검색 필드 추가에 대해 표시되는 제안을 나레이트합니다.

## 액세스 가능성 [!DNL Dynamic Media] {#dynamic-media-accessibility}

Dynamic Media 사용 시 다음 기능을 통해 액세스할 수 있습니다.

* 사용자는 에셋 세부 정보 `Flyout`에 있는 뷰어에서 키 `InlineZoom`를 사용하여 `Shoppable_Banner`, `Zoom_dark``Zoom_light`, `ZoomVertical_dark`및 `ZoomVertical_light` `Tab` [!DNL Dynamic Media]옵션에 집중할 수 있습니다.

## 액세스 가능한 설명서 {#accessible-docs}

[!DNL Experience Manager] 장애가 있는 사용자가 사용할 수 있는 액세스 가능한 설명서를 제공합니다. Adobe은 템플릿 및 컨텐츠를 계속 향상시키는 동안, 다음은 컨텐츠를 액세스할 수 있도록 하는 데 도움이 됩니다.

* 화면 판독기에서 텍스트를 읽을 수 있습니다.
* 이미지와 일러스트레이션에는 대체 텍스트가 있습니다.
* 키보드 탐색을 할 수 있습니다.
* 대비 비율은 설명서 웹 사이트의 일부 부분을 강조 표시하는 데 도움이 됩니다.

<!-- 
## More resources for accessibility {#a11y-resources}

TBD: If anyone is aware of AEM-specific resources that help users leverage any accessibility features or use any assistive technology with AEM, please share or leave a link here.
-->

## 릴리스 개선 [!DNL Experience Manager Assets] 사항 {#rn-fixes}

각 개별 릴리스에서 수행한 특정 개선 사항 목록은 해당 릴리스의 [릴리스 노트를](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/release-notes/home.html) 참조하십시오.

>[!MORELIKETHIS]
>
>* [AEM 접근성 안내](/help/onboarding/accessibility/web-accessibility.md)
>* [Adobe 솔루션 적합성 보고서](https://www.adobe.com/accessibility/compliance.html)

