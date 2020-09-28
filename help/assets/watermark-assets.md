---
title: 자산에 워터마크 표시
description: 디지털 자산에 워터마크 추가
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 1%

---


# 자산에 워터마크 지정 {#watermark-assets}

[!DNL Adobe Experience Manager Assets] 이미지에 디지털 워터마크를 추가할 수 있습니다. [!DNL Assets] 에서는 다른 이미지 파일에 워터마크로 이미지 적용을 지원합니다. 워터마크는 사용자가 자산의 인증 및 저작권 소유권을 확인하는 데 도움이 됩니다. 또한 워터마크를 사용하여 기밀, 초안, 유효성 등과 같은 문서의 상태를 표시할 수 있습니다.

자산을 워터마킹하도록 Experience Manager을 구성하려면 다음 단계를 따르십시오.

1. PNG 파일이 워터마크로 적용됩니다. DAM 저장소에 이 파일을 업로드합니다.

1. 환경에 연결된 Cloud Manager Git 리포지토리에 액세스합니다. Cloud Manager Git 리포지토리 `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.json` 에 다음 내용으로 명명된 파일을 커밋합니다. 자세한 내용은 Experience Manager에서 Cloud Service으로 OSGi 구성을 수행하는 [방법을 참조하십시오](/help/implementing/deploying/configuring-osgi.md).

   ```json
   {
   "watermark": "/content/dam/<path-to-watermark-image.png>",
    "width": 100
   }
   ```

1. [처리 프로필을](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) 만들어 자산 마이크로서비스를 활용하여 워터마크를 적용합니다.

   ![워터마크를 만드는 자산 처리 프로필](assets/watermark-processing-profile.png)

1. [폴더에](/help/assets/asset-microservices-configure-and-use.md#use-profiles) 처리 프로필을 적용하여 워터마크가 있는 에셋을 만듭니다.

## 팁 및 제한 사항 {#tips-limitations-bestpractices}

* 단일 구성을 사용하여 모든 자산을 워터마크할 수 있습니다. 워터마크에는 하나의 이미지만 사용되고 너비가 고정됩니다.
* 타일링 없이 중앙에 워터마크를 배치할 수 있습니다.
* 텍스트 기반 워터마크는 지원되지 않습니다.

>[!MORELIKETHIS]
>
>* [에셋 마이크로서비스 개요](/help/assets/asset-microservices-overview.md).
>* [처리 프로필과 함께 에셋 마이크로서비스를 사용할 수 있습니다](/help/assets/asset-microservices-configure-and-use.md).

