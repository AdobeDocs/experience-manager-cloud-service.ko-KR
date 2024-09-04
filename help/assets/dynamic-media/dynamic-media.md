---
title: Dynamic Media를 사용하여 작업
description: Dynamic Media의 의미에 대해 알아보고 Dynamic Media을 사용하여 웹, 모바일 및 소셜 사이트에서 사용할 자산을 제공할 수 있습니다.
contentOwner: Rick Brough
feature: Dynamic Media,Asset Management
role: Admin,User
exl-id: 3ec3cb85-88ce-4277-a45c-30e52c75ed42
source-git-commit: 57fb7a011cb2da853cdca4f3233cd56775f4a459
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 12%

---

# Dynamic Media를 사용하여 작업 {#working-with-dynamic-media}

[Dynamic Media](https://business.adobe.com/products/experience-manager/assets/dynamic-media.html)는 다양한 시각적 머천다이징 및 마케팅 자산을 웹, 모바일 및 소셜 사이트에 맞게 자동으로 크기를 조정하여 주문형으로 제공하는 데 도움이 됩니다. 기본 소스 자산 세트를 사용하면 Dynamic Media는 글로벌, 확장 가능 및 성능 최적화 네트워크를 통해 실시간으로 다양한 유형의 풍부한 컨텐츠를 생성하고 전달합니다.

Dynamic Media은 확대/축소, 360° 회전 및 비디오를 비롯한 대화형 보기 환경을 제공합니다. Dynamic Media은 디지털 캠페인 관리 프로세스를 간소화하고 간소화하기 위해 Adobe Experience Manager 디지털 에셋 관리(Assets) 솔루션의 워크플로를 고유하게 통합합니다.

<!-- >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Dynamic Media란?

Adobe Experience Manager의 Dynamic Media(AEM as a Cloud Service)는 디지털 플랫폼 전반에 걸쳐 이미지 및 비디오와 같은 리치 미디어 자산을 관리, 제공 및 최적화할 수 있도록 설계된 강력한 솔루션입니다. 사용자의 디바이스 또는 화면 크기에 따라 크기 조정, 자르기 및 품질 조정과 같은 실시간 수정을 허용하여 정적 미디어를 동적이고 매력적인 경험으로 변환합니다. Dynamic Media을 사용하면 사용자가 데스크탑, 모바일 또는 태블릿에 상관없이 자산이 자동으로 조정되어 최상의 시각적 경험을 제공합니다.

Dynamic Media의 주요 이점은 미디어 관리를 간소화할 수 있다는 점입니다. 여러 버전의 이미지 또는 비디오를 만들 필요가 없습니다. Dynamic Media은 각 상황에 가장 적합한 형식을 제공하여 모든 이미지를 처리합니다. 예를 들어 전자 상거래 업체는 360도 제품 보기 또는 확대/축소 가능 이미지를 활용하여 대화형 경험을 만들 수 있으며, 콘텐츠가 많은 웹 사이트는 빠르고 고품질의 비디오 스트리밍을 보장할 수 있습니다. 이를 통해 로드 시간이 빨라지고 사용자 경험이 늘어나므로 궁극적으로 고객 만족도가 높아지고 전환율이 향상됩니다.

Dynamic Media은 AEM의 DAM(디지털 에셋 관리) 시스템과 원활하게 통합되어 미디어를 저장, 구성 및 배포할 수 있는 단일 플랫폼을 제공합니다. 이 중앙 집중식 접근 방식은 팀 간의 협업을 단순화하고 자산 성능에 대한 실시간 통찰력을 제공합니다. 매혹적인 비주얼을 제공하거나 미디어 중심의 사용자 상호 작용을 향상시키는 데 주력하는 경우, Dynamic Media은 모든 채널에 대한 콘텐츠를 최적화하는 데 도움이 되므로 디지털 위상을 높이고자 하는 비즈니스에 필수적인 도구입니다.

## Dynamic Media으로 수행할 수 있는 작업 {#what-you-can-do-with-dynamic-media}

Dynamic Media을 사용하면 자산을 게시하기 전에 관리할 수 있습니다. 일반적인 자산 작업 방법은 [Digital Assets 작업](/help/assets/manage-digital-assets.md)에서 자세히 다룹니다. 일반적인 주제에는 에셋 업로드, 다운로드, 편집 및 게시, 속성 보기 및 편집, 에셋 검색 등이 있습니다.

Dynamic Media 전용 기능에는 다음이 포함됩니다.

* [회전 배너](carousel-banners.md)
* [이미지 세트](image-sets.md)
* [대화형 이미지](interactive-images.md)
* [대화형 비디오](interactive-videos.md)
* [혼합 미디어 세트](mixed-media-sets.md)
* [파노라마 이미지](panoramic-images.md)
* [스핀 세트](spin-sets.md)
* [비디오](video.md)
* [Dynamic Media Assets 제공](delivering-dynamic-media-assets.md)
* [Assets 관리](managing-assets.md)
* [빠른 보기를 사용하여 사용자 지정 팝업 창 만들기](custom-pop-ups.md)

[Dynamic Media 설정](administering-dynamic-media.md)도 참조하세요.

<!-- 

OBSOLETE UNTIL INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE
>[!NOTE]
>
>To understand the differences between using Dynamic Media and integrating Dynamic Media Classic with AEM, see [Dynamic Media Classic integration versus Dynamic Media](/help/sites-cloud/administering/integrating-scene7.md#aem-scene-integration-versus-dynamic-media).

-->

## Dynamic Media 활성화됨 대 Dynamic Media 비활성화됨 {#dynamic-media-on-versus-dynamic-media-off}

다음 특성에 의해 Dynamic Media이 활성화(켜짐)되었는지 여부를 알 수 있습니다.

* 다이내믹 렌디션은 에셋을 다운로드하거나 미리 볼 때 사용할 수 있습니다.
* 이미지 세트, 스핀 세트, 혼합 미디어 세트를 사용할 수 있습니다.
* PTIFF 렌디션이 생성됩니다.

이미지 에셋을 클릭하면 Dynamic Media이 활성화된 상태에서 에셋 보기가 달라집니다. Dynamic Media은 on-demand HTML5 뷰어를 사용합니다.

### 동적 변환 {#dynamic-renditions}

Dynamic Media이 활성화되면 이미지 및 뷰어 사전 설정(**[!UICONTROL Dynamic]** 아래)과 같은 동적 변환을 사용할 수 있습니다.

![chlimage_1-358](assets/chlimage_1-358.png)

### Dynamic Media 이미지 세트, 스핀 세트, 혼합 미디어 세트 {#image-sets-spins-sets-mixed-media-sets}

Dynamic Media이 활성화된 경우 이미지 세트, 스핀 세트 및 혼합 미디어 세트를 사용할 수 있습니다.

![chlimage_1-359](assets/chlimage_1-359.png)

### Dynamic Media 지원 PTIFF 표현물 {#ptiff-renditions}

Dynamic Media 사용 자산에는 `pyramid.tiffs`이(가) 포함됩니다.

![chlimage_1-360](assets/chlimage_1-360.png)

### Dynamic Media 자산 보기 변경 {#asset-views-change}

Dynamic Media이 활성화되면 `+` 및 `-` 단추를 클릭하여 확대하거나 축소할 수 있습니다. 특정 영역을 확대/축소하도록 선택할 수도 있습니다. 되돌리기 를 사용하면 원래 버전으로 이동할 수 있으며 대각선 화살표를 클릭하여 이미지를 전체 화면으로 만들 수 있습니다. Dynamic Media 활성화는 다음과 같이 표시됩니다.

![chlimage_1-361](assets/chlimage_1-361.png)

Dynamic Media이 비활성화되면 확대/축소하고 원래 크기로 되돌릴 수 있습니다.

![chlimage_1-362](assets/chlimage_1-362.png)
