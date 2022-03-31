---
title: 자산에 워터마크 지정
description: 디지털 자산에 워터마크를 추가합니다.
contentOwner: AG
feature: Asset Management,Publishing
role: User,Admin
exl-id: 210f8925-bd15-4b4a-8714-5a1486eeb49e
source-git-commit: cf6cfb38a43004c8ac0c1d1e99153335a47860a8
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 3%

---

# 자산에 워터마크 지정 {#watermark-assets}

[!DNL Adobe Experience Manager Assets] 이미지에 디지털 워터마크를 추가할 수 있습니다. [!DNL Assets] 이미지를 다른 이미지 파일에 워터마크로 적용할 수 있도록 지원합니다. 워터마크는 사용자가 자산의 정품 및 저작권 소유권을 확인하는 데 도움이 될 수 있습니다. 또한 워터마크를 사용하여 기밀, 초안, 유효성 등과 같은 문서의 상태를 표시할 수 있습니다.

구성하려면 [!DNL Experience Manager] 자산을 워터마크 지정하려면 다음을 수행하십시오.

1. PNG 파일은 워터마크로 적용됩니다. 이 파일을 DAM 저장소에 업로드합니다.

1. 다음으로 이동 **[!UICONTROL 도구 > 자산 > 자산 구성]**.

1. 클릭 **[!UICONTROL 시스템 워터마크 프로필]**.

1. 설정 [!UICONTROL 시스템 워터마크 프로필 페이지], 1단계에서 DAM 저장소에 업로드되는 이미지 경로를 지정합니다.

1. 에서 변환 너비를 기준으로 0.0에서 1.0 사이의 워터마크 비율을 지정합니다 **[!UICONTROL 크기 조정]** 필드.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![에셋 중복 감지기](assets/system-watermarking-profile.png)

   >[!NOTE]
   >
   >시스템 워터마크 프로파일을 `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` 구성 파일(OSGi 구성)은 계속 사용할 수 있지만 Adobe은 새 메서드를 사용하는 것이 좋습니다.


1. [처리 프로필 만들기](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) 자산 마이크로서비스를 활용하여 워터마크를 적용하려면

   ![워터마크를 만들기 위한 자산 처리 프로필](assets/watermark-processing-profile.png)

   를 활성화했는지 확인합니다. **[!UICONTROL 워터마크]** 처리 프로필을 만드는 동안 전환합니다.

1. [폴더에 처리 프로필 적용](/help/assets/asset-microservices-configure-and-use.md#use-profiles) 워터마크 자산을 만들려면

## 팁 및 제한 사항 {#tips-limitations-bestpractices}

* 단일 구성을 사용하여 모든 자산을 워터마크 지정할 수 있습니다. 워터마킹에는 하나의 이미지만 사용되고 너비는 고정됩니다.
* 티링 없이 중앙에 워터마크를 배치할 수 있습니다.
* 텍스트 기반 워터마크는 지원되지 않습니다.

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스 개요](/help/assets/asset-microservices-overview.md).
>* [처리 프로필과 함께 자산 마이크로서비스 사용](/help/assets/asset-microservices-configure-and-use.md).

