---
title: 메타데이터 편집 또는 추가 방법
description: ' [!DNL Experience Manager Assets] 에셋 메타데이터를 편집할 수 있는 다양한 방법으로 에셋 메타데이터에 대해 알아봅니다.'
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 9%

---

# 메타데이터 편집 또는 추가 방법 {#how-to-edit-or-add-metadata}

메타데이터는 검색할 수 있는 에셋에 대한 추가 정보입니다. 이미지를 업로드하면 자동으로 추출됩니다. 기존 메타데이터를 편집하거나 기존 필드에 새 메타데이터 속성을 추가할 수 있습니다(예: 메타데이터 필드가 비어 있는 경우).

회사에는 제어되고 신뢰할 수 있는 메타데이터 어휘가 필요하므로 [!DNL Experience Manager Assets]에서는 주문형 새 메타데이터 속성 추가를 허용하지 않습니다. 작성자는 에셋에 대한 새 메타데이터 필드를 추가할 수 없지만 개발자는 추가할 수 있습니다. [Assets에 대한 새 메타데이터 속성 만들기](meta-edit.md#editing-metadata-schema)를 참조하십시오.

## 에셋의 메타데이터 편집 {#editing-metadata-for-an-asset}

메타데이터를 편집하려면:

1. 다음 중 하나를 수행하십시오.

   * Assets UI에서 에셋을 선택하고 도구 모음에서 **[!UICONTROL 속성 보기]** 아이콘을 선택합니다.
   * 자산 미리 보기에서 **[!UICONTROL 속성 보기]** 빠른 작업을 선택합니다.
   * 자산 페이지의 도구 모음에서 **[!UICONTROL 속성 보기]**&#x200B;를 선택합니다.

   에셋 페이지에는 에셋의 메타데이터가 표시됩니다. 이 메타데이터는 Experience Manager Assets에 업로드(수집)될 때 자동으로 추출되었습니다.

1. 필요에 따라 다양한 탭에서 메타데이터를 편집하고, 완료되면 도구 모음에서 **[!UICONTROL 저장]**&#x200B;을 선택하여 변경 내용을 저장합니다. Assets 웹 인터페이스로 돌아가려면 **[!UICONTROL 닫기]**&#x200B;를 선택하십시오.

   >[!NOTE]
   >
   >텍스트 필드가 비어 있으면 기존 메타데이터 세트가 없습니다. 필드에 값을 입력하고 저장하여 해당 메타데이터 속성을 추가할 수 있습니다.

에셋의 메타데이터에 대한 모든 변경 사항은 XMP 데이터의 일부로 원래 바이너리에 다시 기록됩니다. 이 작업은 Experience Manager 메타데이터 쓰기 되돌림 워크플로우를 통해 수행됩니다. 기존 속성(예: `dc:title`)에 대한 변경 내용을 덮어쓰고 만들어진 속성(예: `cq:tags` 등의 사용자 지정 속성 포함)을 스키마와 함께 추가합니다.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## 메타데이터 스키마 편집 {#editing-metadata-schema}

메타데이터 스키마를 편집하는 방법에 대한 자세한 내용은 [메타데이터 스키마 양식 편집](metadata-schemas.md#edit-metadata-schema-forms)을 참조하십시오.

## Experience Manager 내에서 사용자 지정 네임스페이스 등록 {#registering-a-custom-namespace-within-aem}

Experience Manager 내에 고유한 네임스페이스를 추가할 수 있습니다. cq, jcr 및 sling과 같이 사전 정의된 네임스페이스가 있는 것처럼 저장소 메타데이터 및 xml 처리를 위한 네임스페이스를 가질 수 있습니다.

1. 노드 유형 관리 페이지 *https://&lt;host>:&lt;port>/crx/explorer/nodetypes/index.jsp*(으)로 이동합니다.
1. 페이지 맨 위에서 **[!UICONTROL 네임스페이스]**&#x200B;를 선택합니다. 창에 네임스페이스 관리 페이지가 표시됩니다.

1. 네임스페이스를 추가하려면 맨 아래의 **[!UICONTROL 새로 만들기]**&#x200B;를 선택하세요.
1. XML 네임스페이스 규칙에 사용자 지정 네임스페이스를 지정하고(URI 형식의 ID와 ID에 연결된 접두사를 지정) **[!UICONTROL 저장]**&#x200B;을(를) 선택합니다.

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
