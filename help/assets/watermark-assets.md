---
title: AEM에서 에셋에 워터마크를 지정하는 방법
description: AEM에서 자산에 디지털 워터마크를 추가하는 방법을 알아봅니다. 워터마크는 사용자가 에셋의 진정성과 저작권 소유권을 확인하는 데 도움이 될 수 있습니다.
contentOwner: AG
feature: Asset Management,Publishing
role: User, Admin
exl-id: 210f8925-bd15-4b4a-8714-5a1486eeb49e
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 16%

---

# 자산에 워터마크 지정 {#watermark-assets}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/watermarking.html) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Experience Manager Assets]을(를) 사용하면 이미지 및 비디오에 디지털 워터마크를 추가할 수 있습니다. [!DNL Assets]에서는 다른 이미지 파일에 이미지를 워터마크로 적용할 수 있습니다. 워터마크는 사용자가 에셋의 진정성과 저작권 소유권을 확인하는 데 도움이 될 수 있습니다. 또한 워터마크를 사용하여 기밀, 초안, 유효성 등과 같은 문서의 상태를 표시할 수 있습니다.

자산을 워터마크 지정하도록 [!DNL Experience Manager]을(를) 구성하려면:

1. PNG 파일은 워터마크로 적용됩니다. 이 파일을 DAM 저장소에 업로드합니다.

1. **[!UICONTROL 도구 > Assets > Assets 구성]**(으)로 이동합니다.

1. **[!UICONTROL 시스템 워터마크 프로필]**&#x200B;을 클릭합니다.

1. [!UICONTROL 시스템 워터마킹 프로필 페이지]에서 1단계에서 DAM 리포지토리에 업로드된 이미지 경로를 지정합니다.

1. **[!UICONTROL 크기 조정]** 필드에 렌디션 너비를 기준으로 0.0 - 1.0 범위의 워터마크 크기를 지정합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![자산 중복 감지기](assets/system-watermarking-profile.png)

   >[!NOTE]
   >
   >`com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` 구성 파일(OSGi 구성)을 사용하여 시스템 워터마킹 프로필을 구성한 경우 계속 사용할 수 있지만, Adobe은 새 메서드를 사용하는 것을 권장합니다.


1. 자산 마이크로서비스를 사용하여 워터마크를 적용하려면 [처리 프로필을 만듭니다](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile).

   ![워터마크를 만들 자산 처리 프로필](assets/watermark-processing-profile.png)

   처리 프로필을 만드는 동안 **[!UICONTROL 워터마크]** 전환을 활성화하십시오.

1. [폴더에 처리 프로필을 적용](/help/assets/asset-microservices-configure-and-use.md#use-profiles)하여 워터마크가 지정된 자산을 만듭니다.

## 팁 및 제한 사항 {#tips-limitations-bestpractices}

* 단일 구성을 사용하여 모든 에셋에 워터마크를 지정할 수 있습니다. 워터마킹에는 하나의 이미지만 사용되며 너비는 고정되어 있습니다.
* 워터마크를 타일링 없이 중앙에 배치할 수 있습니다.
* 텍스트 기반 워터마크는 지원되지 않습니다.

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스 개요](/help/assets/asset-microservices-overview.md).
>* [처리 프로필에 자산 마이크로서비스 사용](/help/assets/asset-microservices-configure-and-use.md).
