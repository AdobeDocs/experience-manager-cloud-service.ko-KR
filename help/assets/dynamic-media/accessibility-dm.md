---
title: 액세스 가능성( [!DNL Dynamic Media])
description: 다이내믹 미디어 및 다이내믹 미디어 뷰어의 액세스 가능성에 대해 알아봅니다.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: d87710badeeb0518a2e51b8abc3974fa77914515
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 0%

---


# 동적 미디어 {#working-with-three-d-assets-dm}의 액세스 가능성

Dynamic Media는 저작 사용자 인터페이스 전반에서 JAWS 및 NVDA 화면 판독기와 같은 키보드 제어 및 보조 기술을 지원합니다.

## Dynamic Media의 키보드 액세스 지원

Dynamic Media는 Experience Manager 에셋에 대한 플러그인이므로 대부분의 키보드 제어 동작은 Experience Manager 에셋의 경우와 동일합니다. 예를 들어, 다이내믹 미디어의 `Cancel` 버튼은 Experience Manager 자산과 동일한 초점 강조 표시를 가지며 Experience Manager 자산에서와 마찬가지로 `Spacebar` 키에 응답합니다. 자산](/help/assets/accessibility.md#keyboard-shortcuts)의 [키보드 단축키를 참조하십시오.

Dynamic Media의 개별 사용자 인터페이스 요소에서 지원하는 키 입력은 대부분의 경우 명확하고 쉽게 찾을 수 있습니다. Dynamic Media의 키보드 제어는 다음과 같습니다.

* 페이지의 대화형 요소 간을 탐색하기 위해 `Tab` 및 `Shift+Tab` 키 입력을 사용하는 기능
`Tab`을 사용하면 입력 포커스를 탭 순서의 다음 사용자 인터페이스 요소로 이동합니다.`Shift+Tab`을(를) 사용하면 입력 포커스가 이전 사용자 인터페이스 요소로 돌아갑니다.
초점 트래픽은 화면의 자연스러운 사용자 인터페이스 요소 위치를 따르며 왼쪽에서 오른쪽, 위에서 아래로 이동합니다. 또한 필드에 오류가 있으면 `Tab`을 눌러 포커스를 이동할 수 있습니다.
* `Spacebar` 및 `Enter` 키를 사용하여 단추, 드롭다운 목록 등과 같은 표준 사용자 인터페이스 요소를 활성화할 수 있습니다.
* 활성 요소에서 키보드 초점 강조 표시를 보는 기능 입력 포커스가 있는 사용자 인터페이스 요소는 사용자 인터페이스 요소 주위에 렌더링된 테두리로 시각적 초점 표시를 받을 수 있습니다.
* 핫스팟 편집기에서 화살표 키와 같은 일부 사용자 정의 키 입력을 사용하여 복잡한 사용자 인터페이스 요소와 상호 작용하여 핫스팟 위치를 변경할 수 있습니다.
* 대화형 비디오 편집기에서 `Spacebar`을 사용하여 이미지를 선택하고 세그먼트에 추가할 수 있습니다. 또한 `Backspace` 키를 사용하여 **[!UICONTROL Content]** 탭에서 선택한 항목을 삭제할 수 있습니다. 또한 `Tab`을 누르는 것은 페이지의 대화형 요소 사이를 탐색하는 데 필요한 기능입니다.
* 이미지 자르기/스마트 자르기 편집기에서 다음을 수행할 수 있습니다.
   * 화살표 키를 사용하여 프레임 크기를 자르거나 이미지 또는 둘 다의 위치를 다시 지정할 수 있습니다.
   * 첫 번째 `Tab` 중지는 전체 이미지 프레임을 강조 표시합니다. 그런 다음 키보드의 화살표 키를 사용하여 프레임의 위치를 다시 지정할 수 있습니다.
   * 다음 네 개의 `Tab` 중지 영역은 프레임의 네 모퉁이입니다. 프레임 모서리에 초점을 두면 모서리가 강조 표시됩니다. 키보드의 화살표 키를 사용하여 포커스가 있는 모서리를 이동할 수도 있습니다.
참고 항목: [단일 이미지의 스마트 자르기 또는 스마트 견본 편집](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## 동적 미디어 {#assistive-technology=support-for-dm}의 보조 기술 지원

다이내믹 미디어 사용자 인터페이스 요소는 화면 판독기와 같은 보조 기술과 함께 작동합니다. 예를 들어 키보드 단축키 `D` 또는 키보드 단축키 `R`를 사용하여 랜드마크를 탐색할 때 페이지의 랜드마크를 인식합니다. 제목 키보드 단축키 `H`를 사용하여 탐색할 때 제목 내레이션이 적용됩니다.

## 다이내믹 미디어 뷰어에서 키보드 접근성 지원 {#keyboard-accessibility-for-dm-viewers}

즉시 사용 가능한 모든 다이내믹 미디어 뷰어 구성 요소는 고객의 키보드 접근성을 지원합니다.

다이내믹 미디어 뷰어 참조 안내서의 [키보드 액세스 및 내비게이션](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html)을 참조하십시오.

## 동적 미디어 뷰어에서 보조 기술 지원 {#assistive-technology=support-for-dm-viewers}

모든 Dynamic Media 뷰어 구성 요소는 ARIA(Accessible Rich Internet Application) 역할 및 속성을 지원하여 화면 판독기와 같은 보조 기술과의 통합을 향상시킵니다.
Dynamic Media Viewers Reference Guide의 사용자 정의 뷰어 항목에 있는 **보조 기술 지원** 도움말 항목을 참조하십시오. 예를 들어 비디오 뷰어의 경우 [보조 기술 지원](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html), 대화형 이미지 뷰어의 경우 [보조 기술 지원](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=en#viewers-for-aem-assets-only)을 참조하십시오.

>[!MORELIKETHIS]
>
>* [Adobe 솔루션에 대한 액세스 가능성](https://www.adobe.com/accessibility.html)
>* [Experience Manager 자산의 액세스 가능성](/help/assets/dynamic-media/accessibility-dm.md)

