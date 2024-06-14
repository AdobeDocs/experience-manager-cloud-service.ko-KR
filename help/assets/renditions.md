---
title: Experience Manager Assets에서 렌디션 보기 및 관리
description: AEM Assets 및 Dynamic Media이 정적 및 동적 이미지 렌디션을 사용하여 효과적인 이미지 관리를 간소화하는 방법에 대해 알아봅니다.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: 257930bc2633a0d31ad3bd28305b8159597befa5
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Experience Manager Assets에서 렌디션 보기 및 관리{#renditions}

Adobe Experience Manager(AEM)의 렌디션은 최적의 성능을 보장하기 위해 다양한 디바이스 및 플랫폼에 맞게 디자인된 이미지와 같은 디지털 에셋의 사용자 지정 버전입니다. AEM을 사용하면 이러한 렌디션을 쉽게 만들고 관리할 수 있으므로 사용자 경험이 향상됩니다. 썸네일을 만들고, 웹 또는 모바일용 이미지를 최적화하고, 워터마크를 추가하고, 동적 렌디션이나 스마트 자르기 렌디션을 보고 다운로드하고, 더 많은 작업을 수행할 수 있습니다.

Dynamic Media 이미지 사전 설정 및 스마트 자르기 렌디션은 브랜드 표준에 맞는 체계적인 이미지 관리를 촉진하여 브랜드 통합을 극대화합니다. 따라서 관리자 액세스 없이 필요에 따라 동적 이미지 렌디션을 빠르게 찾고 사용하는 프로세스가 간소화됩니다.

렌디션은 정적 및 동적 렌디션으로 분류되며, 각 유형은 보다 자세히 설명되어 있는 고유한 기능을 제공합니다.

## 정적 표현물 {#static-renditions}

정적 렌디션은 디지털 에셋의 사전 생성된 버전으로, 일반적으로 에셋 수집 또는 수정 중에 만들어집니다. 이러한 렌디션은 웹 썸네일, 응답형 디자인을 위한 모바일 친화적 형식 또는 인쇄용 고해상도 버전과 같은 특정 목적 및 플랫폼에 최적화되어 효율적이고 일관된 경험을 보장합니다.
학습 [보기 및 다운로드 방법](#view-dynamic-renditions) 의 정적 렌디션 [!DNL Experience Manager Assets].

## 동적 변환 {#dynamic-renditions}

동적 변환은 장치 해상도에 따라 이미지 크기를 조정하거나 다양한 종횡비에 맞게 자르는 것과 같이 특정 요구 사항을 충족하도록 실시간으로 만들어진 자산의 사용자 지정 버전입니다.
이러한 렌디션을 통해 조직은 다양한 대상 요구 사항에 개인화되고 최적화된 경험을 전달할 수 있습니다. 에서 동적 변환을 보고 다운로드할 수 있습니다. [!DNL Experience Manager Assets].

### 시작하기에 앞서

* 라이선스가 있는 AEM Dynamic Media 사용자여야 합니다.

* 사용 [!UICONTROL 관리자 보기] 설정하려면 다음을 수행하십시오.
   * [스마트 자르기 이미지 프로필](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [이미지 사전 설정](/help/assets/dynamic-media/managing-image-presets.md)

  다음을 수행할 수 있습니다. [보기 전환](/help/assets/assets-view-introduction.md#how-to-access-assets-view) 나중에 를 클릭하여 자산 보기에서 동적 변환을 미리 봅니다.

### 동적 변환 보기 및 다운로드 {#view-renditions}

에서 이미지의 동적 변환을 보거나 다운로드하려면 [!DNL Experience Manager Assets], 다음 단계를 수행합니다.

1. 다음으로 이동 **[!UICONTROL Assets 관리]** > **[!UICONTROL 에셋]**.

1. 해당 에셋 폴더로 이동합니다.

1. 보려는 이미지를 클릭하고 **[!UICONTROL 세부 사항]**.

1. 오른쪽 메뉴에서 **[!UICONTROL 표현물]**. <br> 다음 **[!UICONTROL 표현물]** 사용 가능한 패널 열기 **[!UICONTROL 동적]** 및 **[!UICONTROL 스마트 자르기]** 표현물.

   ![동적 변환](assets/preset_smart_crop.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. 보거나 다운로드해야 하는 렌디션을 클릭합니다.

1. 다음을 클릭합니다. ![다운로드 아이콘](assets/do-not-localize/download-icon.png) 아이콘 다운로드해야 하는 동적 렌디션 옆에 있습니다. <br> 또는 이미지 렌디션을 선택하고 **[!UICONTROL 렌디션 다운로드]** 맨 아래에 있는 옵션입니다.

   다음을 클릭할 수 있습니다 ![다운로드 아이콘](assets/do-not-localize/download-icon.png) 아이콘 위에 사용 가능 **[!UICONTROL 스마트 자르기]** 렌디션 섹션을 통해 해당 에셋에 대해 사용 가능한 모든 스마트 자르기 렌디션을 다운로드할 수 있습니다.

>[!NOTE]
>
>동적 변환은 자산이 관리자 보기에서 업로드되는 경우에만 표시됩니다.
