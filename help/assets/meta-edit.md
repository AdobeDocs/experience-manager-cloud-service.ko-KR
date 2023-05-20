---
title: 메타데이터 편집 또는 추가 방법
description: 에서 에셋 메타데이터에 대해 알아보기 [!DNL Experience Manager Assets] 에셋 메타데이터를 편집할 수 있는 다양한 방법입니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 15%

---

# 메타데이터 편집 또는 추가 방법 {#how-to-edit-or-add-metadata}

메타데이터는 검색할 수 있는 에셋에 대한 추가 정보입니다. 이미지를 업로드하면 자동으로 추출됩니다. 기존 메타데이터를 편집하거나 기존 필드에 새 메타데이터 속성을 추가할 수 있습니다(예: 메타데이터 필드가 비어 있는 경우).

기업들은 통제되고 신뢰할 수 있는 메타데이터 어휘를 필요로 하기 때문에, [!DNL Experience Manager Assets] 는 새 메타데이터 속성을 애드혹 추가할 수 없습니다. 작성자는 에셋에 대한 새 메타데이터 필드를 추가할 수 없지만 개발자는 추가할 수 있습니다. 다음을 참조하십시오 [자산에 대한 새 메타데이터 속성 만들기](meta-edit.md#editing-metadata-schema).

## 에셋의 메타데이터 편집 {#editing-metadata-for-an-asset}

메타데이터를 편집하려면:

1. 다음 중 하나를 수행하십시오.

   * 에셋 UI에서 에셋을 선택하고 **[!UICONTROL 속성 보기]** 아이콘을 클릭합니다.
   * 에셋 썸네일에서 다음을 선택합니다. **[!UICONTROL 속성 보기]** 빠른 작업.
   * 에셋 페이지에서 을 클릭/탭합니다. **[!UICONTROL 속성 보기]** 을 클릭합니다.

   에셋 페이지에는 에셋의 모든 메타데이터가 표시됩니다. 이 메타데이터는 Experience Manager Assets에 업로드(수집)될 때 자동으로 추출되었습니다.

1. Make edits to the metadata under the various tabs, as required, and when completed, click/tap **[!UICONTROL Save]** from the toolbar to save your changes. Click/tap **[!UICONTROL Close]** to return to the Assets web interface.

   >[!NOTE]
   >
   >텍스트 필드가 비어 있으면 기존 메타데이터 세트가 없습니다. 필드에 값을 입력하고 저장하여 해당 메타데이터 속성을 추가할 수 있습니다.

에셋의 메타데이터에 대한 모든 변경 사항은 XMP 데이터의 일부로 원래 바이너리에 다시 기록됩니다. 이 작업은 Experience Manager 메타데이터 쓰기 되돌림 워크플로우를 통해 수행됩니다. 기존 속성에 대한 변경 사항(예: `dc:title`)은 덮어쓰기되며 새로 생성된 속성(과 같은 사용자 지정 속성 포함)입니다 `cq:tags`)가 스키마와 함께 추가됩니다.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## 메타데이터 스키마 편집 {#editing-metadata-schema}

메타데이터 스키마를 편집하는 방법에 대한 자세한 내용은 [메타데이터 스키마 양식 편집](metadata-schemas.md#edit-metadata-schema-forms).

## Experience Manager 내에서 사용자 지정 네임스페이스 등록 {#registering-a-custom-namespace-within-aem}

Experience Manager 내에 고유한 네임스페이스를 추가할 수 있습니다. cq, jcr 및 sling과 같이 사전 정의된 네임스페이스가 있는 것처럼 저장소 메타데이터 및 xml 처리를 위한 네임스페이스를 가질 수 있습니다.

1. 노드 유형 관리 페이지로 이동합니다. *https://&lt;host>:&lt;port>/crx/explorer/nodetypes/index.jsp*.
1. 클릭 또는 탭 **[!UICONTROL 네임스페이스]** 을 클릭합니다. 창에 네임스페이스 관리 페이지가 표시됩니다.

1. 네임스페이스를 추가하려면 을(를) 클릭하거나 탭합니다 **[!UICONTROL 신규]** 맨 아래에
1. XML 네임스페이스 규칙에서 사용자 지정 네임스페이스를 지정하고(URI 및 ID에 대한 연결된 접두사의 형태로 ID 지정) 을 클릭하거나 탭합니다 **[!UICONTROL 저장]**.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [에셋이 지원되는 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 에셋](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
