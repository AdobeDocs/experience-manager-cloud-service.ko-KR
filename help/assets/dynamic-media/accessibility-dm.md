---
title: 액세스 가능성 [!DNL Dynamic Media]
description: Dynamic Media에서 3D 자산으로 작업하는 방법 살펴보기
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: 7af8ddda4aee093b22147db9be9f65cd0c131c04
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---


# 다이내믹 미디어의 접근성 {#working-with-three-d-assets-dm}

Dynamic Media는 저작 사용자 인터페이스 전반에서 JAWS 및 NVDA 화면 판독기와 같은 키보드 제어 및 보조 기술을 지원합니다.



## Dynamic Media의 키보드 액세스 지원

개별 사용자 인터페이스 요소에서 지원하는 키 입력은 대부분의 경우 명확하고 쉽게 찾을 수 있습니다. Dynamic Media의 키보드 제어는 다음과 같습니다.

* 페이지에서 인터랙티브한 요소 간 `Tab` 을 탐색하기 위해 키 `Shift+Tab` 입력과 키를 사용하는 기능
탭 순서에서 다음 사용자 인터페이스 요소로 입력 포커스를 `Tab` 이동합니다.를 `Shift+Tab` 사용하면 입력 포커스가 이전 사용자 인터페이스 요소로 돌아갑니다.
초점 트래픽은 화면의 자연스러운 사용자 인터페이스 요소 위치를 따르며 왼쪽에서 오른쪽, 위에서 아래로 이동합니다.
* 버튼, `Spacebar` 드롭다운 목록 등과 같은 표준 사용자 인터페이스 요소를 활성화하는 데 `Enter` 및키를 사용하는 기능입니다.
* 활성 요소에서 키보드 초점 강조 표시를 보는 기능 입력 포커스가 있는 사용자 인터페이스 요소는 사용자 인터페이스 요소 주위에 렌더링된 테두리로 시각적 초점 표시를 받을 수 있습니다.
* 핫 스팟 편집기의 화살표 키와 같은 복잡한 UI 요소와 상호 작용하는 사용자 정의 키 입력을 사용하는 기능 이미지 자르기/스마트 자르기 편집기에서는 화살표 키를 사용하여 프레임 크기를 자르거나 이미지의 위치를 다시 지정하거나 둘 다 지정할 수 있습니다.

Dynamic Media는 AEM Assets에 대한 플러그인이므로 대부분의 키보드 제어 동작은 AEM Assets과 동일합니다. 예를 들어 Dynamic Media의 `Cancel` 단추는 AEM Assets과 동일한 초점 강조 표시를 가지며 AEM Assets에서와 같이 `Spacebar` 키에 반응합니다. 자산에서 [키보드 단축키를 참조하십시오](/help/assets/accessibility.md#keyboard-shortcuts). 핫스팟 편집기와 이미지 자르기/스마트 자르기 편집기는 예외입니다.

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

핫스팟 편집기에서 화살표 키를 사용하여 핫 스팟 위치를 제어할 수 있습니다. 회전판 [배너](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) 또는 [대화형 이미지 참조](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)

이미지 자르기/스마트 자르기 편집기에서 화살표 키를 사용하여 프레임 크기를 자르거나 이미지의 위치를 다시 지정하거나 둘 다 지정합니다. 단일 [이미지의 스마트 자르기 또는 스마트 견본 편집을 참조하십시오.](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## 다이내믹 미디어 뷰어에 대한 키보드 액세스 지원 {#keyboard-accessibility-for-dm-viewers}

즉시 사용 가능한 모든 다이내믹 미디어 뷰어 구성 요소는 고객의 키보드 접근성을 지원합니다.

Dynamic [Media Viewers Reference Guide의 Keyboard accessibility and navigation](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) 을 참조하십시오.

## 다이내믹 미디어 뷰어를 위한 보조 기술 지원 {#assistive-technology=support-for-dm-viewers}

Dynamic Media의 모든 뷰어 구성 요소는 ARIA(Accessible Rich Internet Application) 역할 및 속성을 지원하여 화면 판독기와 같은 보조 기술과의 통합을 향상시킵니다.

Dynamic **Media Viewers Reference Guide의 사용자 정의 뷰어 항목에 있는 보조 기술 지원** 도움말 항목을 참조하십시오. 예를 들어 비디오 뷰어에 대한 [보조 기술 지원](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) 또는 대화형 이미지 뷰어에 대한 [보조 기술 지원을](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=en#viewers-for-aem-assets-only) 참조하십시오.

>[!MORELIKETHIS]
>
>* [Adobe 솔루션에 대한 액세스 가능성](https://www.adobe.com/accessibility.html)
>* [Experience Manager 자산의 액세스 가능성](/help/assets/dynamic-media/accessibility-dm.md)

