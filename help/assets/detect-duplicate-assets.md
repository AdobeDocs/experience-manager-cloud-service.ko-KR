---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]에 대해 중복 에셋 감지'
description: 중복 에셋을 감지하는 방법 알아보기
contentOwner: KK
mini-toc-levels: 3
feature: Asset Management, Publishing,Collaboration, Asset Processing
role: User, Architect, Admin
exl-id: 40f63933-4f4e-4318-8d42-4b5c9b01f7cd
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 10%

---


# 중복 자산 감지 {#detect-duplicate-assets}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

DAM 사용자가 저장소에 이미 있는 하나 이상의 자산을 업로드하는 경우 [!DNL Experience Manager]에서 중복을 감지하여 사용자에게 알립니다. 중복 검색은 저장소 크기 및 업로드된 에셋 수에 따라 성능에 영향을 줄 수 있으므로 기본적으로 비활성화됩니다.

기능을 활성화하려면 다음을 수행하십시오.

1. **[!UICONTROL 도구 > Assets > Assets 구성]**(으)로 이동합니다.

1. **[!UICONTROL 자산 중복 감지기]**&#x200B;를 클릭합니다.

1. [!UICONTROL 자산 중복 검색기 페이지]에서 **[!UICONTROL 사용]**&#x200B;을 클릭하세요.

   메타데이터 검색 필드의 `dam:sha1` 값은 파일 이름이 다른 경우에도 중복 에셋이 검색되도록 합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![자산 중복 감지기](assets/asset-duplication-detector.png)

>[!NOTE]
>
>`/apps/example/config.author/com.adobe.cq.assetcompute.impl.assetprocessor.AssetDuplicationDetector.cfg.json` 구성 파일(OSGi 구성)을 사용하여 중복 감지기를 구성한 경우 계속 사용할 수 있지만, Adobe은 새 메서드를 사용하는 것을 권장합니다.


활성화되면 Experience Manager은 중복 에셋에 대한 알림을 Experience Manager 받은 편지함으로 보냅니다. 여러 개의 중복에 대한 집계 결과입니다. 사용자는 결과에 따라 에셋을 제거하도록 선택할 수 있습니다.

![중복 에셋에 대한 받은 편지함 알림](assets/duplicate-detect-inbox-notification.png)

>[!NOTE]
>
>에셋을 저장소에 업로드하면 Experience Manager에서 중복을 감지하여 처음 100개의 중복 에셋에 대해 알려 줍니다.
