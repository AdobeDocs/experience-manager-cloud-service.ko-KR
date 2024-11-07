---
title: Experience Manager Assets에서 렌디션 보기 및 관리
description: AEM Assets 및 Dynamic Media이 정적 및 동적 이미지 렌디션을 사용하여 효과적인 이미지 관리를 간소화하는 방법에 대해 알아봅니다.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: a3a6456dec178c36c9fe8acfb6f98915fc86e490
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 4%

---

# Experience Manager Assets에서 렌디션 보기 및 관리{#renditions}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능 포함 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Adobe Experience Manager(AEM)의 렌디션은 최적의 성능을 보장하기 위해 다양한 디바이스 및 플랫폼에 맞게 디자인된 이미지와 같은 디지털 에셋의 사용자 지정 버전입니다. AEM을 사용하면 이러한 렌디션을 쉽게 만들고 관리할 수 있으므로 사용자 경험이 향상됩니다. 썸네일을 만들고, 웹 또는 모바일용 이미지를 최적화하고, 워터마크를 추가하고, 동적 렌디션 또는 스마트 자르기 렌디션을 보고 다운로드하고, 더 많은 작업을 수행할 수 있습니다.

Dynamic Media 이미지 사전 설정 및 스마트 자르기 렌디션은 브랜드 표준에 맞는 체계적인 이미지 관리를 촉진하여 브랜드 통합을 극대화합니다. 따라서 관리자 액세스 없이 필요에 따라 동적 이미지 렌디션을 빠르게 찾고 사용하는 프로세스가 간소화됩니다.

렌디션은 정적 및 동적 렌디션으로 분류되며, 각 유형은 보다 자세히 설명되어 있는 고유한 기능을 제공합니다.

## 정적 표현물 {#static-renditions}

정적 렌디션은 디지털 에셋의 사전 생성된 버전으로, 일반적으로 에셋 수집 또는 수정 중에 만들어집니다. 이러한 렌디션은 웹 썸네일, 응답형 디자인을 위한 모바일 친화적 형식 또는 인쇄용 고해상도 버전과 같은 특정 목적 및 플랫폼에 최적화되어 효율적이고 일관된 경험을 보장합니다.
[!DNL Experience Manager Assets]에서 [정적 표현물을 보고 다운로드하는 방법](#view-dynamic-renditions)을 알아보세요.

## 동적 변환 {#dynamic-renditions}

동적 변환은 장치 해상도에 따라 이미지 크기를 조정하거나 다양한 종횡비에 맞게 자르는 것과 같이 특정 요구 사항을 충족하도록 실시간으로 만들어진 자산의 사용자 지정 버전입니다.
이러한 렌디션을 통해 조직은 다양한 대상 요구 사항에 개인화되고 최적화된 경험을 전달할 수 있습니다. [!DNL Experience Manager Assets]에서 동적 변환을 보고 다운로드할 수 있습니다.

## Dynamic Media 렌디션 {#dynamic-media-renditions}

### 시작하기에 앞서

* 라이선스가 있는 AEM Dynamic Media 사용자여야 합니다.
* [!UICONTROL 관리자 보기]를 사용하여 다음을 설정하십시오.
   * [스마트 자르기 이미지 프로필](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [이미지 사전 설정](/help/assets/dynamic-media/managing-image-presets.md)

  나중에 [보기를 전환](/help/assets/assets-view-introduction.md#how-to-access-assets-view)하여 Assets 보기에서 동적 변환을 미리 볼 수 있습니다.
* Publish assets to Dynamic Media 를 사용하여 Assets 보기에서 Dynamic Media 렌디션을 사용할 수 있도록 합니다. 자세한 내용은 [AEM 및 Dynamic Media으로 Publish Assets](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm)를 참조하십시오.


### Dynamic Media 렌디션 보기 및 다운로드 {#view-download-dm-renditions}

Experience Manager Assets에서 이미지의 동적 변환을 보거나 다운로드하려면 다음 단계를 따르십시오.

1. **[!UICONTROL Assets 관리]** > **[!UICONTROL Assets]**(으)로 이동합니다.

1. 해당 에셋 폴더로 이동합니다.

1. 보려는 자산을 클릭하고 **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.

1. 오른쪽 메뉴에서 **[!UICONTROL Dynamic Media]** 아이콘을 클릭합니다. **[!UICONTROL Dynamic Media]** 패널에 Dynamic Media 및 스마트 자르기 렌디션이 표시됩니다.

   ![동적 변환](/help/assets/assets/dm-scene7-renditions.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. 미리 볼 렌디션을 선택하고 **URL 복사**&#x200B;를 클릭하여 선택한 렌디션의 URL을 복사합니다. 이미지 에셋 렌디션을 다운로드하려면 **렌디션 다운로드**&#x200B;를 클릭하십시오.
1. 미리 볼 스마트 자르기 렌디션을 선택하고 **URL 복사**&#x200B;를 클릭하여 선택한 렌디션의 URL을 복사합니다.
1. 사용 가능한 모든 스마트 자르기 렌디션을 단일 zip 파일로 다운로드하려면 ![다운로드 아이콘](assets/do-not-localize/download-icon.png)을 클릭하십시오.
   ![다운로드 아이콘](/help/assets/assets/smartcrop-rendition.png)

   >[!NOTE]
   >
   >이러한 렌디션은 이미지 에셋에만 사용할 수 있습니다.

## OpenAPI 기능 렌디션이 포함된 Dynamic Media {#dm-with-openapi-renditions}

### 시작하기에 앞서

* 라이선스가 있는 AEM Dynamic Media 사용자여야 합니다.
* OpenAPI 기능 렌디션이 포함된 Dynamic Media을 표시하려면 Assets을 승인해야 합니다. 자세한 내용은 [Experience Manager에서 자산 승인](/help/assets/approve-assets.md#copy-delivery-url-approved-assets)을 참조하세요.
* OpenAPI 기능이 있는 Dynamic Media은 AEM as a Cloud Service 인스턴스에서 활성화해야 합니다.

### OpenAPI 기능 렌디션을 사용하여 Dynamic Media 보기 {#view-download-dm-with-openapi-renditions}

1. 자산을 선택하고 **세부 정보**&#x200B;를 클릭합니다.
1. 오른쪽 창에서 사용할 수 있는 Dynamic Media 아이콘을 클릭합니다. Dynamic Media 패널에는 모든 에셋 유형에 대한 Dynamic Media OpenAPI 기능 렌디션이 표시됩니다.
   ![다운로드 아이콘](/help/assets/assets/dm-with-open-api-copy-url.png)
1. **OpenAPI를 사용하는 Dynamic Media** 옵션을 선택한 다음 **URL 복사**&#x200B;를 클릭하여 자산의 배달 URL을 복사합니다.


