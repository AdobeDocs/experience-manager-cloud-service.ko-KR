---
title: Dynamic Media에서의 접근성
description: 비디오 인코딩, YouTube에 비디오 게시 및 비디오 보고서 보기 모범 사례와 같이 Dynamic Media에서 비디오로 작업하는 방법을 알아봅니다. 또한 폐쇄 캡션, 캡션 또는 챕터 마커를 비디오에 추가하는 방법도 알아봅니다.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Accessibility
role: Admin,User
exl-id: f8d2dcbf-f61a-4b27-a3fc-406e3662adcb
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 1%

---

# Dynamic Media에서의 접근성 {#accessibility-in-dm}

{{work-with-dynamic-media}}

Dynamic Media는 작성 사용자 인터페이스에서 키보드 제어와 JAWS 및 NVDA 화면 판독기와 같은 보조 기술을 지원합니다.

## Dynamic Media의 키보드 접근성 지원 {#keyboard-support-in-dm}

Dynamic Media는 [!DNL Experience Manager Assets]에 대한 플러그인이므로 대부분의 키보드 제어 동작은 [!DNL Experience Manager Assets]과(와) 동일합니다. 예를 들어 Dynamic Media의 `Cancel` 단추는 [!DNL Experience Manager Assets]과(와) 동일한 포커스 강조 표시를 갖습니다. 또한 [!DNL Experience Manager Assets]에서와 같이 `Spacebar` 키에도 반응합니다. [Assets의 키보드 단축키](/help/assets/accessibility.md#keyboard-shortcuts)를 참조하십시오.

Dynamic Media의 개별 사용자 인터페이스 요소에서 지원하는 키 입력은 대부분의 경우 명확하고 쉽게 찾을 수 있습니다. Dynamic Media의 키보드 제어는 다음과 같습니다.

* `Tab` 및 `Shift+Tab` 키 입력을 사용하여 페이지의 대화형 요소 사이를 탐색하는 기능.
`Tab`을(를) 사용하면 입력 포커스가 탭 순서의 다음 사용자 인터페이스 요소로 이동합니다. `Shift+Tab`을(를) 사용하면 입력 포커스가 이전 사용자 인터페이스 요소로 돌아갑니다.
포커스 트래버스는 화면의 자연어 사용자 인터페이스 요소 위치를 따라가며 왼쪽에서 오른쪽으로, 위에서 아래로 이동합니다. 또한 오류가 있는 필드가 있으면 `Tab`을 눌러 포커스를 이동할 수 있습니다.
* `Spacebar` 및 `Enter` 키를 사용하여 단추 및 드롭다운 목록과 같은 표준 사용자 인터페이스 요소를 활성화하는 기능.
* 활성 요소에서 키보드 포커스 강조 표시를 확인하는 기능. 입력 포커스를 갖는 사용자 인터페이스 요소는 사용자 인터페이스 요소 주위에 렌더링된 경계로서 시각적 포커스 표시를 수신하였다.
* 핫스팟 편집기에서 화살표 키와 같은 사용자 지정 키 입력을 사용하여 복잡한 사용자 인터페이스 요소와 상호 작용하여 핫스팟의 위치를 변경할 수 있습니다.
* 대화형 비디오 편집기에서 `Spacebar`을(를) 사용하여 이미지를 선택하고 세그먼트에 추가할 수 있습니다. 또한 `Backspace` 키를 사용하여 **[!UICONTROL 콘텐츠]** 탭에서 선택한 항목을 삭제할 수 있습니다. 또한 `Tab`을(를) 누르면 페이지의 대화형 요소 사이를 탐색할 수 있습니다.
* 이미지 자르기/스마트 자르기 편집기에서 다음 작업을 수행할 수 있습니다.
   * 화살표 키를 사용하여 프레임 크기를 자르거나 이미지 위치를 변경하거나 둘 다 수행합니다.
   * 첫 번째 `Tab` 중지를 수행하면 전체 이미지 프레임이 강조 표시됩니다. 그런 다음 키보드의 화살표 키를 사용하여 프레임의 위치를 변경할 수 있습니다.
   * 다음 네 개의 `Tab` 정지는 프레임의 네 모퉁이입니다. 프레임 모서리에 포커스를 놓으면 코너가 강조 표시됩니다. 키보드의 화살표 키를 사용하여 포커스가 있는 모서리를 이동할 수 있습니다.
[단일 이미지의 스마트 자르기 또는 스마트 색상 견본 편집](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)을 참조하십시오.

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (Experience Manager 6.5) or Coral Spectrum (in Skyline)) as entire Experience Manager Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Dynamic Media의 보조 기술 지원 {#assistive-technology=support-for-dm}

Dynamic Media 사용자 인터페이스 요소는 화면 판독기와 같은 보조 기술과 함께 작동합니다. 예를 들어, 키보드 단축키 `D`을(를) 사용하여 랜드마크를 탐색하거나 키보드 단축키 `R`을(를) 사용하여 영역을 탐색할 때 페이지에서 랜드마크를 인식합니다. 또한 제목 키보드 단축키 `H`을(를) 사용하여 탐색할 때 제목의 내레이션이 적용됩니다.

## Dynamic Media 뷰어의 키보드 접근성 지원 {#keyboard-accessibility-for-dm-viewers}

모든 Dynamic Media 뷰어 구성 요소는 고객을 위해 키보드 접근성을 지원합니다.

Dynamic Media 뷰어 참조 안내서에서 [키보드 접근성 및 탐색](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html?lang=ko)을 참조하십시오.

## Dynamic Media 뷰어의 보조 기술 지원 {#assistive-technology=support-for-dm-viewers}

모든 Dynamic Media 뷰어 구성 요소는 ARIA(Accessible Rich Internet Applications) 역할 및 속성을 지원하여 화면 판독기와 같은 보조 기술과의 통합을 향상시킵니다.
Dynamic Media 뷰어 참조 안내서의 뷰어 사용자 지정 항목에서 **보조 기술 지원** 도움말 항목을 참조하십시오. 예를 들어 비디오 뷰어의 경우 [보조 기술 지원](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html?lang=ko) 또는 대화형 이미지 뷰어의 경우 [보조 기술 지원](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=ko#viewers-for-aem-assets-only)을 참조하십시오.

## [!DNL Dynamic Media]에서 폐쇄 캡션 지원 {#closed-caption-support}

Dynamic Media는 자막이 있는 비디오 및 적응형 비디오 세트 배달을 지원합니다. 캡션은 비디오 콘텐츠 위에 표시되어야 합니다.

[Dynamic Media의 비디오 - 비디오에 폐쇄 캡션 추가](/help/assets/dynamic-media/video.md#adding-captions-to-video)를 참조하십시오.


>[!MORELIKETHIS]
>
>* [Adobe 솔루션에 대한 접근성](https://www.adobe.com/accessibility.html)
>* [Experience Manager Assets의 접근성](/help/assets/dynamic-media/accessibility-dm.md)
