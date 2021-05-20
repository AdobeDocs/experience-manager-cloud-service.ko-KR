---
title: 자산에 워터마크 지정
description: 디지털 자산에 워터마크를 추가합니다.
contentOwner: AG
feature: 자산 관리,게시
role: Business Practitioner,Administrator
exl-id: 210f8925-bd15-4b4a-8714-5a1486eeb49e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# 자산에 워터마크 지정 {#watermark-assets}

[!DNL Adobe Experience Manager Assets] 이미지에 디지털 워터마크를 추가할 수 있습니다. [!DNL Assets] 이미지를 다른 이미지 파일에 워터마크로 적용할 수 있도록 지원합니다. 워터마크는 사용자가 자산의 정품 및 저작권 소유권을 확인하는 데 도움이 될 수 있습니다. 또한 워터마크를 사용하여 기밀, 초안, 유효성 등과 같은 문서의 상태를 표시할 수 있습니다.

자산을 워터마킹하도록 [!DNL Experience Manager]을 구성하려면 다음 단계를 수행합니다.

1. PNG 파일은 워터마크로 적용됩니다. DAM 저장소에 이 파일을 업로드합니다.

1. 환경과 연결된 [!DNL Cloud Manager] Git 리포지토리에 액세스합니다. 다음 내용을 사용하여 저장소에서 `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` 파일을 커밋합니다. 지침은 [OSGi 구성을 [!DNL Experience Manager] 에서 [!DNL Cloud Service]](/help/implementing/deploying/configuring-osgi.md)로 수행하는 방법을 참조하십시오.

   ```json
   {
   "watermark": "/content/dam/<path-to-watermark-image.png>",
    "width": 100
   }
   ```

1. [자산 마이크로서비스](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) 를 활용하여 워터마크를 적용하는 처리 프로필을 만듭니다.

   ![워터마크를 만들기 위한 자산 처리 프로필](assets/watermark-processing-profile.png)

1. [폴더에 처리 프로필을 ](/help/assets/asset-microservices-configure-and-use.md#use-profiles) 적용하여 워터마크가 지정된 자산을 만듭니다.

## 팁 및 제한 사항 {#tips-limitations-bestpractices}

* 단일 구성을 사용하여 모든 자산을 워터마크 지정할 수 있습니다. 워터마킹에는 하나의 이미지만 사용되고 너비는 고정됩니다.
* 티링 없이 중앙에 워터마크를 배치할 수 있습니다.
* 텍스트 기반 워터마크는 지원되지 않습니다.

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스 개요](/help/assets/asset-microservices-overview.md).
>* [처리 프로필과 함께 자산 마이크로서비스 를 사용합니다](/help/assets/asset-microservices-configure-and-use.md).

