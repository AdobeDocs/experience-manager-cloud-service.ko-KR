---
title: AEM Assets을 다운스트림 애플리케이션과 통합
description: AEM Assets을 다운스트림 애플리케이션과 통합
role: User
exl-id: abd48b5d-2b43-453c-8eb6-31ff509245ca
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 8%

---

# AEM Assets을 다운스트림 애플리케이션과 통합 {#integrate-dynamic-media-open-apis}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능 포함 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>이제 OpenAPI 기능 안내서를 포함한 Dynamic Media을 PDF 형식으로 사용할 수 있습니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI Assistant를 사용하여 질문에 답변합니다.
>
>[!BADGE OpenAPI 기능을 사용하는 Dynamic Media 안내서 PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Experience Manager 에셋 저장소에서 사용할 수 있는 [승인된 에셋](/help/assets/approve-assets.md)은 모두 다운스트림 응용 프로그램으로 전달할 수 있습니다.

검색 및 게재 API를 사용하여 자체 사용자 지정 사용자 인터페이스를 Experience Manager Assets 저장소와 통합하거나 Adobe의 Micro-Frontend 자산 선택기를 사용할 수 있습니다.

![AEM Assets 리포지토리와 통합](assets/asset-selector-integration.png)

API를 사용하면 AEM Assets 저장소에서 승인된 에셋을 검색한 다음 배달 URL을 사용하여 다운스트림 애플리케이션에 에셋을 게재할 수 있습니다. 자세한 내용은 [검색](/help/assets/search-assets-api.md) 및 [배달](/help/assets/deliver-assets-apis.md) API를 참조하십시오.

Adobe의 Micro-Frontend 자산 선택기는 [!DNL Experience Manager Assets as a Cloud Service] 리포지토리와 쉽게 통합되는 사용자 인터페이스를 제공하므로 리포지토리에서 사용할 수 있는 승인된 디지털 자산을 찾아보거나 검색하고 응용 프로그램 작성 환경에서 사용할 수 있습니다. 자세한 내용은 [Micro-Frontend 자산 선택기](/help/assets/overview-asset-selector.md)를 참조하십시오.

>[!MORELIKETHIS]
>
* [다양한 응용 프로그램과 자산 선택기 통합](/help/assets/integrate-asset-selector.md)
* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
* [자산 선택기 사용자 지정](/help/assets/asset-selector-customization.md)
