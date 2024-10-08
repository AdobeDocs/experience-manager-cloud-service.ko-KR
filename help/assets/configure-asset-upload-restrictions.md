---
title: 자산 업로드 제한 사항 구성
description: 사용자가 MIME 유형에 따라 업로드할 수 있는 에셋 유형을 제한하도록 Adobe Experience Manager Assets을 구성합니다. 원하지 않는 형식 및 악성 파일이 실수로 업로드되는 것을 방지하는 데 도움이 됩니다.
exl-id: 094c31f3-f2e9-4b44-9995-c76fb78ca458
feature: Upload, Asset Ingestion
role: User, Admin, Developer
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 13%

---

# 자산 업로드 제한 사항 구성 {#configure-asset-upload-restrictions}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

사용자가 MIME 유형에 따라 업로드할 수 있는 에셋 유형을 제한하도록 Adobe Experience Manager Assets을 구성할 수 있습니다.

>[!IMPORTANT]
>
>기본적으로 Experience Manager Assets에서는 사용자가 모든 MIME 유형의 자산을 업로드할 수 있습니다. 그러나 사용자가 특정 MIME 유형의 파일만 업로드하도록 제한하는 설정을 구성할 수 있습니다.

## 사전 요구 사항 {#prerequisites-asset-upload-restrictions}

자산 업로드 제한 사항을 구성하려면 관리자 권한이 있어야 합니다.

## 에셋 업로드에 제한 적용 {#apply-restrictions-asset-uploadsssssss}

사용자가 특정 MIME 유형의 파일을 업로드하도록 제한하도록 [!DNL Experience Manager]을(를) 구성하려면 다음을 수행하십시오.

1. **[!UICONTROL 도구 > Assets > Assets 구성]**(으)로 이동합니다.

1. **[!UICONTROL 업로드 제한]**&#x200B;을 클릭합니다.

1. 허용되는 MIME 유형을 정의하려면 **[!UICONTROL 추가]**&#x200B;를 클릭하십시오.

1. 텍스트 상자에 MIME 유형을 지정합니다. **[!UICONTROL 추가]**&#x200B;를 다시 클릭하여 더 많은 MIME 유형을 지정할 수 있습니다. ![삭제 아이콘](assets/delete-icon.svg)을 클릭하여 목록에서 MIME 형식을 삭제할 수도 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

**예 1: Experience Manager Assets에 모든 이미지 및 PDF 파일 업로드 허용**

모든 형식의 이미지 및 PDF 파일을 Experience Manager Assets에 업로드할 수 있도록 하려면 다음 설정을 수행하십시오.

![에셋 업로드 제한 사항](assets/asset-upload-restrictions.png)

`image/*`을(를) MIME 형식으로 사용하면 모든 형식의 이미지를 업로드할 수 있습니다. `application/pdf`을(를) MIME 형식으로 Experience Manager Assets에 PDF 파일을 업로드할 수 있습니다.

허용되는 MIME 유형 목록에 포함되지 않은 파일을 업로드하려고 하면 Experience Manager Assets에 다음 오류 메시지가 표시됩니다.

![제한된 파일](assets/asset-upload-restricted-files.png)

`Screen Recording 2022-08-31 at 3.36.09 PM.mov`은(는) 허용된 MIME 형식에 포함되지 않은 파일 이름을 참조합니다.

**예 2: Experience Manager Assets에 특정 이미지 형식 업로드 허용**

특정 이미지 형식을 허용된 MIME 유형에 추가하고 다른 모든 에셋 형식의 업로드를 제한하려면 다음 설정을 수행하십시오.

![자산 제한](assets/asset-restrictions.png)

이미지에 표시된 설정을 기반으로 .JPG, .PNG 및 .GIF 형식의 이미지를 Experience Manager Assets에 업로드할 수 있습니다.

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
