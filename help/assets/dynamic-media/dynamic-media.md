---
title: Dynamic Media 작업
description: Dynamic Media을 사용하여 웹, 모바일 및 소셜 사이트에서 사용할 에셋을 제공하는 방법을 살펴봅니다.
translation-type: tm+mt
source-git-commit: a8eb6a88b889facca8518c05a80051fc17dd0617
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 22%

---


# Dynamic Media 작업 {#working-with-dynamic-media}

[Dynamic Media](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html)는 다양한 시각적 머천다이징 및 마케팅 자산을 웹, 모바일 및 소셜 사이트에 맞게 자동으로 크기를 조정하여 주문형으로 제공하는 데 도움이 됩니다. 기본 소스 자산 세트를 사용하면 Dynamic Media는 글로벌, 확장 가능 및 성능 최적화 네트워크를 통해 실시간으로 다양한 유형의 풍부한 컨텐츠를 생성하고 전달합니다.

Dynamic Media은 확대/축소, 360도 회전, 비디오 등 인터랙티브한 보기 경험을 제공합니다. Dynamic Media은 Adobe Experience Manager 디지털 에셋 관리(Assets) 솔루션의 워크플로우를 고유하게 통합하여 디지털 캠페인 관리 프로세스를 간소화합니다.

<!-- >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Dynamic Media {#what-you-can-do-with-dynamic-media}로 수행할 수 있는 작업

Dynamic Media을 사용하면 자산을 게시하기 전에 자산을 관리할 수 있습니다. 일반적으로 자산을 사용하여 작업하는 방법은 [디지털 자산 작업](/help/assets/manage-digital-assets.md)에서 자세히 다룹니다. 일반적인 주제에는 자산 업로드, 다운로드, 편집 및 게시가 포함됩니다.속성 보기 및 편집, 자산 검색 등

Dynamic Media 전용 기능은 다음과 같습니다.

* [회전 배너](carousel-banners.md)
* [이미지 세트](image-sets.md)
* [대화형 이미지](interactive-images.md)
* [대화형 비디오](interactive-videos.md)
* [혼합 미디어 세트](mixed-media-sets.md)
* [파노라마 이미지](panoramic-images.md)

* [스핀 세트](spin-sets.md)
* [비디오](video.md)
* [Dynamic Media 자산 제공](delivering-dynamic-media-assets.md)
* [자산 관리](managing-assets.md)
* [빠른 보기를 사용하여 사용자 정의 팝업 창 만들기](custom-pop-ups.md)

[Dynamic Media](administering-dynamic-media.md) 설정을 참조하십시오.

<!-- 

OBSOLETE UNTIL INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE
>[!NOTE]
>
>To understand the differences between using Dynamic Media and integrating Dynamic Media Classic with AEM, see [Dynamic Media Classic integration versus Dynamic Media](/help/sites-cloud/administering/integrating-scene7.md#aem-scene-integration-versus-dynamic-media).

-->

## Dynamic Media이 활성화된 경우와 Dynamic Media이 비활성화된 경우 {#dynamic-media-on-versus-dynamic-media-off}

다음 특성을 사용하여 Dynamic Media의 활성화(활성화) 여부를 알 수 있습니다.

* 다이내믹 표현물은 자산을 다운로드하거나 미리 볼 때 사용할 수 있습니다.
* 이미지 세트, 스핀 세트, 혼합 미디어 집합을 사용할 수 있습니다.
* PTIFF 변환이 생성됩니다.

이미지 자산을 클릭하면 자산 보기가 Dynamic Media이 활성화되면 다릅니다. Dynamic Media은 on-demand HTML5 뷰어를 사용합니다.

### 동적 표현물 {#dynamic-renditions}

Dynamic Media이 활성화되면 이미지 및 뷰어 사전 설정과 같은 동적 변환(**[!UICONTROL 동적]** 아래)을 사용할 수 있습니다.

![chlimage_1-358](assets/chlimage_1-358.png)

### 이미지 세트, 회전 집합, 혼합 미디어 집합 {#image-sets-spins-sets-mixed-media-sets}

Dynamic Media이 활성화된 경우 이미지 세트, 스핀 세트 및 혼합 미디어 집합을 사용할 수 있습니다.

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF 변환 {#ptiff-renditions}

Dynamic Media이 활성화된 자산은 `pyramid.tiffs`입니다.

![chlimage_1-360](assets/chlimage_1-360.png)

### 자산 보기 변경: {#asset-views-change}

Dynamic Media이 활성화되면 `+` 및 `-` 단추를 클릭하여 확대/축소할 수 있습니다. 클릭/탭하여 특정 영역을 확대할 수도 있습니다. [되돌리기]를 선택하면 원래 버전으로 이동하며 대각선 화살표를 클릭하여 이미지를 전체 화면으로 만들 수 있습니다. Dynamic Media에서 활성화한 모습은 다음과 같습니다.

![chlimage_1-361](assets/chlimage_1-361.png)

Dynamic Media이 비활성화되어 있으면 확대 및 축소하고 원래 크기로 되돌릴 수 있습니다.

![chlimage_1-362](assets/chlimage_1-362.png)
