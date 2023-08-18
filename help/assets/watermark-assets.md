---
title: AEM에서 에셋에 워터마크를 지정하는 방법
description: AEM에서 자산에 디지털 워터마크를 추가하는 방법을 알아봅니다. 워터마크는 사용자가 에셋의 진정성과 저작권 소유권을 확인하는 데 도움이 될 수 있습니다.
contentOwner: AG
feature: Asset Management,Publishing
role: User,Admin
exl-id: 210f8925-bd15-4b4a-8714-5a1486eeb49e
source-git-commit: d663c258a83473ec8d3c68bc5683955003d889c7
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 16%

---

# 자산에 워터마크 지정 {#watermark-assets}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/watermarking.html) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Experience Manager Assets] 이미지에 디지털 워터마크를 추가할 수 있습니다. [!DNL Assets] 는 이미지를 다른 이미지 파일에 워터마크로 적용할 수 있도록 지원합니다. 워터마크는 사용자가 에셋의 진정성과 저작권 소유권을 확인하는 데 도움이 될 수 있습니다. 또한 워터마크를 사용하여 기밀, 초안, 유효성 등과 같은 문서의 상태를 표시할 수 있습니다.

구성하려면 [!DNL Experience Manager] 에셋에 워터마크 지정 방법:

1. PNG 파일은 워터마크로 적용됩니다. 이 파일을 DAM 저장소에 업로드합니다.

1. 다음으로 이동 **[!UICONTROL 도구 > 에셋 > 에셋 구성]**.

1. 클릭 **[!UICONTROL 시스템 워터마킹 프로필]**.

1. 다음에서 [!UICONTROL 시스템 워터마킹 프로필 페이지]1단계에서 DAM 저장소에 업로드되는 이미지 경로를 지정합니다.

1. 렌디션 너비를 기준으로 0.0~1.0 범위의 워터마크 배율을 **[!UICONTROL 크기 조절]** 필드.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![에셋 중복 감지기](assets/system-watermarking-profile.png)

   >[!NOTE]
   >
   >다음을 사용하여 시스템 워터마킹 프로필을 구성한 경우 `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` Adobe 구성 파일(OSGi 구성)은 계속 사용할 수 있지만 새 메서드를 사용하는 것이 좋습니다.


1. [처리 프로필 만들기](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) 자산 마이크로서비스 를 사용하여 워터마크를 적용합니다.

   ![워터마크를 만드는 자산 처리 프로필](assets/watermark-processing-profile.png)

   다음을 활성화했는지 확인합니다. **[!UICONTROL 워터마크]** 처리 프로필을 만드는 동안 전환합니다.

1. [폴더에 처리 프로필 적용](/help/assets/asset-microservices-configure-and-use.md#use-profiles) 워터마크 에셋을 만듭니다.

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

>[!MORELIKETHIS]
>
>* [에셋 마이크로서비스 개요](/help/assets/asset-microservices-overview.md).
>* [처리 프로필에서 자산 마이크로서비스 사용](/help/assets/asset-microservices-configure-and-use.md).
