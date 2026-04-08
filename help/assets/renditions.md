---
title: Experience Manager Assets에서 렌디션 보기 및 관리
description: AEM Assets 및 Dynamic Media가 정적 및 동적 이미지 렌디션을 사용하여 효과적인 이미지 관리를 간소화하는 방법에 대해 알아봅니다.
badgeSaas: label="AEM Assets" type="Positive" tooltip="AEM Assets에 적용됩니다)."
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: ae834c77b2f2a12cac3dde132a2357d72353cb55
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 1%

---

# Experience Manager Assets에서 렌디션 보기 및 관리{#renditions}

Adobe Experience Manager(AEM)의 렌디션은 최적의 성능을 보장하기 위해 다양한 디바이스 및 플랫폼용으로 설계된 이미지와 같은 디지털 에셋의 사용자 지정 버전입니다. AEM을 사용하면 이러한 렌디션을 쉽게 만들고 관리할 수 있으므로 사용자 경험이 향상됩니다. 썸네일을 만들고, 웹 또는 모바일용 이미지를 최적화하고, 워터마크를 추가하고, 동적 렌디션 또는 스마트 자르기 렌디션을 보고 다운로드하고, 더 많은 작업을 수행할 수 있습니다.

Dynamic Media 이미지 사전 설정 및 스마트 자르기 렌디션은 브랜드 표준에 맞는 체계적인 이미지 관리를 촉진하여 브랜드 통합을 극대화합니다. 따라서 관리자 액세스 없이 필요에 따라 동적 이미지 렌디션을 빠르게 찾고 사용하는 프로세스가 간소화됩니다.

렌디션은 정적 및 동적 렌디션으로 분류되며, 각 유형은 보다 자세히 설명되어 있는 고유한 기능을 제공합니다.

## 정적 표현물 {#static-renditions}

정적 렌디션은 디지털 에셋의 사전 생성된 버전으로, 일반적으로 에셋 수집 또는 수정 중에 만들어집니다. 이러한 렌디션은 웹 썸네일, 응답형 디자인을 위한 모바일 친화적 형식 또는 인쇄용 고해상도 버전과 같은 특정 목적 및 플랫폼에 최적화되어 효율적이고 일관된 경험을 보장합니다.
Experience Manager Assets에서 [정적 표현물을 보고 다운로드](#view-and-download-static-renditions)하는 방법을 알아봅니다.

### 정적 렌디션 보기 및 다운로드{#view-and-download-static-renditions}

에셋 표현물을 보고 다운로드하려면 다음 단계를 따르십시오.

1. Assets 보기에서 **Assets**&#x200B;을 클릭하고 폴더로 이동하여 자산을 선택하고 **세부 정보**&#x200B;를 클릭합니다.
1. 오른쪽 창에서 사용할 수 있는 렌디션의 아이콘을 클릭합니다.
1. 미리 볼 렌디션을 선택하고 ![다운로드 아이콘](/help/assets/assets/download-icon.svg)을 클릭하여 다운로드합니다.

   ![동적 렌디션 보기 및 다운로드](/help/assets/assets/view-download-static-rendition.png)

## 동적 변환 {#dynamic-renditions}

동적 변환은 장치 해상도에 따라 이미지 크기를 조정하거나 다양한 종횡비에 맞게 자르는 것과 같이 특정 요구 사항을 충족하도록 실시간으로 만들어진 자산의 사용자 지정 버전입니다.
이러한 렌디션을 통해 조직은 다양한 대상 요구 사항에 개인화되고 최적화된 경험을 전달할 수 있습니다. Experience Manager Assets에서 동적 변환을 보고 다운로드할 수 있습니다.

## Dynamic Media 렌디션 {#dynamic-media-renditions}

### 시작하기에 앞서

* 라이선스가 있는 AEM Dynamic Media 사용자여야 합니다.
* [!UICONTROL 관리자 보기]를 사용하여 다음을 설정하십시오.
   * [스마트 자르기 이미지 프로필](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [이미지 사전 설정](/help/assets/dynamic-media/managing-image-presets.md)

  나중에 [보기를 전환](/help/assets/assets-view-introduction.md#how-to-access-assets-view)하여 Assets 보기에서 동적 변환을 미리 볼 수 있습니다.
* 자산을 Dynamic Media에 게시하여 Assets 보기에서 Dynamic Media 변환을 사용할 수 있도록 합니다. 자세한 내용은 [AEM 및 Dynamic Media에 Assets 게시](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm)를 참조하십시오.


### Dynamic Media 렌디션 보기 및 다운로드 {#view-download-dm-renditions}

Experience Manager Assets에서 이미지의 동적 변환을 보거나 다운로드하려면 다음 단계를 따르십시오.

1. **[!UICONTROL Assets 관리]** > **[!UICONTROL Assets]**(으)로 이동합니다.

1. 해당 에셋 폴더로 이동합니다.

1. 보려는 자산을 클릭하고 **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.

1. 오른쪽 메뉴에서 **[!UICONTROL Dynamic Media]** 아이콘을 클릭합니다. **[!UICONTROL Dynamic Media]** 패널에 Dynamic Media 및 스마트 자르기 렌디션이 표시됩니다.

   ![동적 렌디션](/help/assets/assets/dm-scene7-renditions.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. 미리 볼 렌디션을 선택하고 **URL 복사**&#x200B;를 클릭하여 선택한 렌디션의 URL을 복사합니다. 이미지 에셋 렌디션을 다운로드하려면 **렌디션 다운로드**&#x200B;를 클릭하십시오.
1. 미리 볼 스마트 자르기 렌디션을 선택하고 **URL 복사**&#x200B;를 클릭하여 선택한 렌디션의 URL을 복사합니다.
1. 사용 가능한 모든 스마트 자르기 렌디션을 단일 zip 파일로 다운로드하려면 ![다운로드 아이콘](assets/do-not-localize/download-icon.png)을 클릭하십시오.
   ![다운로드 아이콘](/help/assets/assets/download-op.png)

   >[!NOTE]
   >
   >이러한 렌디션은 이미지 에셋에만 사용할 수 있습니다.

## OpenAPI 기능이 포함된 Dynamic Media 변환 {#dm-with-openapi-renditions}

### 시작하기에 앞서 {#prereqs-dm-with-openapi-renditions}

* 라이선스가 있는 AEM Dynamic Media 사용자여야 합니다.
* Assets은 OpenAPI 기능 변환이 있는 Dynamic Media를 표시하려면 공개적으로 사용할 수 있도록 승인되어야 합니다. 자세한 내용은 [Experience Manager에서 자산 승인](/help/assets/approve-assets.md#copy-delivery-url-approved-assets)을 참조하세요.
* AEM as a Cloud Service 인스턴스에서 OpenAPI 기능을 사용하는 Dynamic Media를 활성화해야 합니다.

### OpenAPI 기능 렌디션을 사용하여 Dynamic Media 보기 {#view-download-dm-with-openapi-renditions}

1. 자산을 선택하고 **세부 정보**&#x200B;를 클릭합니다.
1. 오른쪽 패널에서 사용할 수 있는 Dynamic Media 아이콘을 클릭합니다. Dynamic Media 패널에는 지원되는 에셋 유형에 대한 기본 렌디션, 동적 렌디션 및 스마트 자르기 렌디션이 표시됩니다.
   ![다운로드 아이콘](/help/assets/assets/new-new1.png)
1. **기본 렌디션**&#x200B;을(를) 선택하고 **URL 복사**&#x200B;를 클릭하여 에셋의 게재 URL을 복사하거나 **렌디션 다운로드**&#x200B;를 클릭하여 에셋을 다운로드합니다.

저장소에 대해 OpenAPI 기능이 있는 Scene7(Dynamic Media)과 Dynamic Media가 모두 활성화된 경우 사용자 인터페이스에서 둘 사이를 전환하는 토글 옵션을 사용할 수 있습니다. 표시된 렌디션과 생성된 URL은 선택한 구성에 따라 업데이트됩니다.

![옵션 전환](/help/assets/assets/new-new2.png)