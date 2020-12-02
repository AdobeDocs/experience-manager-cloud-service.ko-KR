---
title: Dynamic Media 작업
description: Dynamic Media를 사용하여 웹, 모바일 및 소셜 사이트에서 사용할 에셋을 전달하는 방법을 살펴볼 수 있습니다.
translation-type: tm+mt
source-git-commit: a5e94003a3e9023155dc95ceba1a5531e4f20d8f
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 31%

---


# Dynamic Media 작업 {#working-with-dynamic-media}

[Dynamic Media](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html)는 다양한 시각적 머천다이징 및 마케팅 자산을 웹, 모바일 및 소셜 사이트에 맞게 자동으로 크기를 조정하여 주문형으로 제공하는 데 도움이 됩니다. 기본 소스 자산 세트를 사용하면 Dynamic Media는 글로벌, 확장 가능 및 성능 최적화 네트워크를 통해 실시간으로 다양한 유형의 풍부한 컨텐츠를 생성하고 전달합니다.

Dynamic Media는 확대/축소, 360도 회전, 비디오를 비롯한 대화형 보기 환경을 제공합니다. Dynamic Media는 Adobe Experience Manager 디지털 자산 관리(Assets) 솔루션의 워크플로우를 고유하게 통합하여 디지털 캠페인 관리 프로세스를 단순화하고 간소화합니다.

>[!NOTE]
>
>커뮤니티 아티클은 [Adobe Experience Manager 및 다이내믹 미디어 작업](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html)에서 사용할 수 있습니다.

## 다이내믹 미디어 {#what-you-can-do-with-dynamic-media}로 수행할 수 있는 작업

Dynamic Media를 사용하면 자산을 게시하기 전에 자산을 관리할 수 있습니다. 일반적으로 자산을 사용하여 작업하는 방법은 [디지털 자산 작업](/help/assets/manage-digital-assets.md)에서 자세히 다룹니다. 일반적인 주제에는 자산 업로드, 다운로드, 편집 및 게시가 포함됩니다.속성 보기 및 편집, 자산 검색.

다이내믹 미디어 전용 기능은 다음과 같습니다.

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
* [빠른 보기를 사용하여 사용자 지정 팝업 만들기](custom-pop-ups.md)

[다이내믹 미디어 설정](administering-dynamic-media.md)을 참조하십시오.

<!-- 

OBSOLETE UNTIL INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE
>[!NOTE]
>
>To understand the differences between using Dynamic Media and integrating Dynamic Media Classic with AEM, see [Dynamic Media Classic integration versus Dynamic Media](/help/sites-cloud/administering/integrating-scene7.md#aem-scene-integration-versus-dynamic-media).

-->

## 동적 미디어 활성화 대 동적 미디어 비활성화 {#dynamic-media-on-versus-dynamic-media-off}

다음 특성을 사용하여 다이내믹 미디어의 활성화(활성화) 여부를 지정할 수 있습니다.

* 자산을 다운로드하거나 미리 볼 때 동적 변환을 사용할 수 있습니다.
* 이미지 세트, 스핀 세트, 혼합 미디어 집합을 사용할 수 있습니다.
* PTIFF 변환이 생성됩니다.

이미지 자산을 클릭할 때 자산의 보기가 Dynamic Media가 활성화되면 달라집니다. Dynamic Media는 주문형 HTML5 뷰어를 사용합니다.

### 동적 변환 {#dynamic-renditions}

Dynamic Media가 활성화되면 이미지 및 뷰어 사전 설정(**[!UICONTROL Dynamic]** 아래)과 같은 동적 변환을 사용할 수 있습니다.

![chlimage_1-358](assets/chlimage_1-358.png)

### 이미지 세트, 회전 집합, 혼합 미디어 집합 {#image-sets-spins-sets-mixed-media-sets}

다이내믹 미디어가 활성화된 경우 이미지 세트, 스핀 세트 및 혼합 미디어 세트를 사용할 수 있습니다.

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF 변환 {#ptiff-renditions}

다이내믹 미디어 사용 자산은 `pyramid.tiffs`입니다.

![chlimage_1-360](assets/chlimage_1-360.png)

### 자산 보기 변경 {#asset-views-change}

Dynamic Media가 활성화되어 있으면 `+` 및 `-` 단추를 클릭하여 확대/축소할 수 있습니다. 클릭/탭하여 특정 영역을 확대할 수도 있습니다. [되돌리기]를 선택하면 원래 버전으로 전환되며, 대각선 화살표를 클릭하여 이미지를 전체 화면으로 만들 수 있습니다. Dynamic Media가 활성화된 모습은 다음과 같습니다.

![chlimage_1-361](assets/chlimage_1-361.png)

Dynamic Media를 비활성화하면 확대/축소하거나 원래 크기로 되돌릴 수 있습니다.

![chlimage_1-362](assets/chlimage_1-362.png)
