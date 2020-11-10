---
title: 액세스 가능성 [!DNL Dynamic Media]
description: 다이내믹 미디어 및 다이내믹 미디어 뷰어의 액세스 가능성에 대해 알아봅니다.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: 97c53ec4317657beeb3619b2f56915a1e649dd9b
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---


# 다이내믹 미디어의 접근성 {#working-with-three-d-assets-dm}

Dynamic Media는 저작 사용자 인터페이스 전반에서 JAWS 및 NVDA 화면 판독기와 같은 키보드 제어 및 보조 기술을 지원합니다.

## Dynamic Media의 키보드 액세스 지원

Dynamic Media는 AEM Assets에 대한 플러그인이므로 대부분의 키보드 제어 동작은 AEM Assets과 동일합니다. 예를 들어 Dynamic Media의 `Cancel` 단추는 AEM Assets과 동일한 초점 강조 표시를 가지며 AEM Assets에서와 같이 `Spacebar` 키에 반응합니다. 자산에서 [키보드 단축키를 참조하십시오](/help/assets/accessibility.md#keyboard-shortcuts).

Dynamic Media의 개별 사용자 인터페이스 요소에서 지원하는 키 입력은 대부분의 경우 명확하고 쉽게 찾을 수 있습니다. Dynamic Media의 키보드 제어는 다음과 같습니다.

* 페이지에서 인터랙티브한 요소 간 `Tab` 을 탐색하기 위해 키 `Shift+Tab` 입력과 키를 사용하는 기능
탭 순서에서 다음 사용자 인터페이스 요소로 입력 포커스를 `Tab` 이동합니다.를 `Shift+Tab` 사용하면 입력 포커스가 이전 사용자 인터페이스 요소로 돌아갑니다.
초점 트래픽은 화면의 자연스러운 사용자 인터페이스 요소 위치를 따르며 왼쪽에서 오른쪽, 위에서 아래로 이동합니다. 또한 필드에 오류가 있으면 키를 눌러 포커스를 이동할 수 `Tab` 있습니다.
* 버튼, `Spacebar` 드롭다운 목록 등과 같은 표준 사용자 인터페이스 요소를 활성화하는 데 `Enter` 및키를 사용하는 기능입니다.
* 활성 요소에서 키보드 초점 강조 표시를 보는 기능 입력 포커스가 있는 사용자 인터페이스 요소는 사용자 인터페이스 요소 주위에 렌더링된 테두리로 시각적 초점 표시를 받을 수 있습니다.
* 핫스팟 편집기에서 화살표 키와 같은 일부 사용자 정의 키 입력을 사용하여 복잡한 사용자 인터페이스 요소와 상호 작용하여 핫스팟 위치를 변경할 수 있습니다.
* 대화형 비디오 편집기에서 아이콘을 사용하여 이미지를 선택하고 세그먼트에 추가할 수 `Spacebar` 있습니다. 또한 `Backspace` 키를 사용하여 [콘텐트] 탭에서 선택한 항목을 삭제할 수 **[!UICONTROL 있습니다]** . 또한 페이지에서 대화형 요소 간을 탐색하기 위해 필요에 따라 키를 `Tab` 누릅니다.
* 이미지 자르기/스마트 자르기 편집기에서 다음을 수행할 수 있습니다.
   * 화살표 키를 사용하여 프레임 크기를 자르거나 이미지 또는 둘 다의 위치를 다시 지정할 수 있습니다.
   * 첫 번째 `Tab` 정지점은 전체 이미지 프레임을 강조 표시합니다. 그런 다음 키보드의 화살표 키를 사용하여 프레임의 위치를 다시 지정할 수 있습니다.
   * 다음 네 `Tab` 정거장은 골조의 네 모퉁이이다. 프레임 모서리에 초점을 두면 모서리가 강조 표시됩니다. 키보드의 화살표 키를 사용하여 포커스가 있는 모서리를 이동할 수도 있습니다.
단일 [이미지의 스마트 자르기 또는 스마트 견본 편집을 참조하십시오.](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Dynamic Media의 보조 기술 지원 {#assistive-technology=support-for-dm}

다이내믹 미디어 사용자 인터페이스 요소는 화면 판독기와 같은 보조 기술과 함께 작동합니다. 예를 들어 키보드 단축키를 사용하여 랜드마크를 탐색하거나 키보드 단축키 `D` 를 사용하여 영역을 탐색할 때 페이지의 랜드마크를 인식합니다 `R`. 제목 키보드 단축키를 사용하여 탐색할 때 제목 내레이션이 적용됩니다 `H`.

## Dynamic Media 뷰어의 키보드 접근성 지원 {#keyboard-accessibility-for-dm-viewers}

즉시 사용 가능한 모든 다이내믹 미디어 뷰어 구성 요소는 고객의 키보드 접근성을 지원합니다.

Dynamic [Media Viewers Reference Guide의 Keyboard accessibility and navigation](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) 을 참조하십시오.

## 다이내믹 미디어 뷰어의 보조 기술 지원 {#assistive-technology=support-for-dm-viewers}

모든 Dynamic Media 뷰어 구성 요소는 ARIA(Accessible Rich Internet Application) 역할 및 속성을 지원하여 화면 판독기와 같은 보조 기술과의 통합을 향상시킵니다.
Dynamic **Media Viewers Reference Guide의 사용자 정의 뷰어 항목에 있는 보조 기술 지원** 도움말 항목을 참조하십시오. 예를 들어 비디오 뷰어에 대한 [보조 기술 지원](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) 또는 대화형 이미지 뷰어에 대한 [보조 기술 지원을](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=en#viewers-for-aem-assets-only) 참조하십시오.

>[!MORELIKETHIS]
>
>* [Adobe 솔루션에 대한 액세스 가능성](https://www.adobe.com/accessibility.html)
>* [Experience Manager 자산의 액세스 가능성](/help/assets/dynamic-media/accessibility-dm.md)

