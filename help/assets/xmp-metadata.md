---
title: XMP 메타데이터
description: 메타데이터 관리를 위한 XMP(Extensible Metadata Platform) 메타데이터 표준에 대해 알아봅니다. 메타데이터의 생성, 처리 및 교환을 위한 표준화된 형식으로 Experience Manager에서 사용됩니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: fd9af408-d2a3-4c7a-9423-c4b69166f873
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 18%

---

# XMP 메타데이터 {#xmp-metadata}

XMP(Extensible Metadata Platform)은 모든 메타데이터 관리를 위해 Experience Manager Assets에서 사용하는 메타데이터 표준입니다. XMP은 다양한 애플리케이션에 대한 메타데이터를 생성하고, 처리하고, 교환할 수 있는 표준 포맷을 제공합니다.

모든 파일 형식에 임베드할 수 있는 범용 메타데이터 인코딩을 제공하는 것 외에도 XMP에서는 다양한 기능을 제공합니다 [콘텐츠 모델](#xmp-core-concepts) 및 [Adobe에서 지원](#advantages-of-xmp) 및 기타 회사가 XMP의 사용자를 [!DNL Assets] 구축할 강력한 플랫폼이 있습니다.

## XMP 개요 및 에코시스템 {#xmp-ecosystem}

[!DNL Assets] 기본적으로 XMP 메타데이터 표준을 지원합니다. XMP은 디지털 자산에서 표준화되고 독점 메타데이터를 처리하고 저장하는 표준입니다. XMP은 여러 애플리케이션이 메타데이터를 사용하여 효과적으로 작업할 수 있도록 하는 공통 표준으로 설계되었습니다.

예를 들어 프로덕션 전문가는 Adobe 애플리케이션 내의 기본 제공 XMP 지원을 사용하여 여러 파일 형식에 걸쳐 정보를 전달합니다. 다음 [!DNL Assets] 저장소는 XMP 메타데이터를 추출하고 이를 사용하여 콘텐츠 라이프사이클을 관리하고 자동화 워크플로를 만들 수 있는 기능을 제공합니다.

XMP은 데이터 모델, 스토리지 모델 및 스키마를 제공하여 메타데이터의 정의, 생성 및 처리 방법을 표준화합니다. 이 개념들은 모두 이 섹션에서 다룹니다.

EXIF, ID3 또는 Microsoft Office의 모든 기존 메타데이터는 자동으로 XMP으로 변환되며, 이를 제품 카탈로그와 같은 고객별 메타데이터 스키마를 지원하도록 확장할 수 있습니다.

XMP의 메타데이터는 속성 세트로 구성됩니다. 이러한 속성은 항상 리소스라고 하는 특정 엔티티와 연결됩니다. 즉, 속성은 리소스 &quot;정보&quot;입니다. XMP의 경우 리소스는 항상 자산입니다.

XMP defines a [metadata](https://en.wikipedia.org/wiki/Metadata) model that can be used with any defined set of metadata items. XMP also defines particular [schemas](https://en.wikipedia.org/wiki/XML_schema) for basic properties useful for recording the history of a resource as it passes through multiple processing steps, from being photographed, [scanned](https://en.wikipedia.org/wiki/Image_scanner), or authored as text, through photo editing steps (such as [cropping](https://en.wikipedia.org/wiki/Cropping_%28image%29) or color adjustment), to assembly into a final image. XMP allows each software program or device along the way to add its own information to a digital resource, which can then be retained in the final digital file.

XMP is most commonly serialized and stored using a subset of the [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF), which is in turn expressed in [XML](https://en.wikipedia.org/wiki/XML).

### XMP의 장점 {#advantages-of-xmp}

XMP은 다른 인코딩 표준 및 스키마타에 비해 다음과 같은 이점이 있습니다.

* XMP 기반 메타데이터는 매우 강력하고 세분화되었습니다.
* XMP을 사용하면 하나의 속성에 대해 여러 값을 가질 수 있습니다.
* XMP에는 메타데이터를 쉽게 교환할 수 있는 표준화된 인코딩이 있습니다.
* XMP은 확장 가능합니다. 에셋에 추가 정보를 추가할 수 있습니다.

XMP standard는 확장 가능하도록 설계되어 사용자 지정 메타데이터 유형을 XMP 데이터에 추가할 수 있습니다. 반면 EXIF에는 확장될 수 없는 고정 속성 목록이 있습니다.

>[!NOTE]
>
>XMP에서는 일반적으로 이진 데이터 형식을 포함할 수 없습니다. 이진 데이터(예: 썸네일 이미지)를 XMP으로 전달하려면 다음과 같이 XML에 친숙한 형식으로 인코딩해야 합니다 `Base64`.

### XMP 핵심 개념 {#xmp-core-concepts}

**네임스페이스 및 스키마**

XMP 스키마는 데이터 형식 및 설명 정보를 포함하는 일반적인 XML 네임스페이스의 속성 이름 집합입니다. XMP 스키마는 XML 네임스페이스 URI로 식별됩니다. 네임스페이스를 사용하면 이름은 같지만 의미가 다른 여러 스키마의 속성 간 충돌을 방지할 수 있습니다.

예를 들어 **작성자** 독립적으로 디자인된 두 개의 스키마의 속성은 에셋을 만든 사람을 의미할 수 있으며, 에셋을 만든 애플리케이션(예: Adobe Photoshop)을 의미할 수도 있습니다.

**XMP 속성 및 값**

XMP은 하나 이상의 스키마에서 속성을 포함할 수 있습니다. 예를 들어 많은 Adobe 애플리케이션에서 사용하는 일반적인 하위 집합은 다음과 같습니다.

* 더블린 코어 스키마: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* XMP 기본 스키마: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* XMP 권한 관리 스키마: `xmpRights:WebStatement`, `xmpRights:Marked`
* XMP 미디어 관리 스키마: `xmpMM:DocumentID`

**언어 대체 요소**

XMP에서는 다음을 추가할 수 있는 기능을 제공합니다. `xml:lang` 속성을 텍스트 속성에 추가하여 텍스트의 언어를 지정합니다.

## 표현물로 XMP 원본에 쓰기 {#xmp-writeback-to-renditions}

의 이 XMP 원본에 쓰기 기능 [!DNL Adobe Experience Manager Assets] 메타데이터 변경 사항을 원본 에셋의 렌디션에 복제합니다.
내에서 에셋의 메타데이터를 변경하는 경우 [!DNL Assets] 또는 에셋을 업로드하는 동안 변경 사항은 에셋 계층의 메타데이터 노드에 처음 저장됩니다. 쓰기 저장(writeback) 기능을 사용하면 메타데이터 변경 내용을 에셋의 모든 또는 특정 렌디션에 전파할 수 있습니다. 이 기능은 를 사용하는 메타데이터 속성만 기록합니다. `jcr` 네임스페이스, 즉 `dc:title` 은(는) 다시 기록되지만 라는 속성이 있습니다. `mytitle` 아님.

예를 들어 을 수정하는 시나리오를 생각해 보십시오. [!UICONTROL 제목] 제목이 있는 자산의 속성 `Classic Leather` 끝 `Nylon`.

![메타데이터](assets/metadata.png)

이 경우, [!DNL Assets] 의 변경 사항을 **[!UICONTROL 제목]** 의 속성 `dc:title` 에셋 계층에 저장된 에셋 메타데이터의 매개 변수.

![저장소의 자산 노드에 저장된 메타데이터](assets/metadata_stored.png)

>[!IMPORTANT]
>
>쓰기 저장(writeback) 기능은 기본적으로 [!DNL Assets]. 방법 보기 [메타데이터 원본에 쓰기 활성화](#enable-xmp-writeback). 디지털 자산용 MSM은 메타데이터 원본에 쓰기 기능이 활성화된 상태에서 작동하지 않습니다. 원본에 쓰기 시 상속이 중단됩니다.

### XMP 원본에 쓰기 활성화 {#enable-xmp-writeback}

[!UICONTROL DAM 메타데이터 원본에 쓰기] 워크플로는 자산의 메타데이터를 원본에 쓰는 데 사용됩니다. 원본에 쓰기 기능을 사용하려면 다음 세 가지 방법 중 하나를 따르십시오.

* 런처를 사용합니다.
* 수동 시작 `DAM MetaData Writeback` 워크플로입니다.
* 사후 처리에 포함되도록 워크플로우를 구성합니다.

런처를 사용하려면 다음 단계를 수행합니다.

1. 관리자로서 액세스 권한 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로]** > **[!UICONTROL 런처]**.
1. 다음 항목 선택 [!UICONTROL 런처] 대상 **[!UICONTROL 워크플로]** 열 표시 **[!UICONTROL DAM 메타데이터 원본에 쓰기]**. 클릭 **[!UICONTROL 속성]** 을 클릭합니다.

   ![속성을 수정하고 활성화하려면 DAM 메타데이터 원본에 쓰기 시작 관리자 선택](assets/launcher-properties-metadata-writeback1.png)

1. 선택 **[!UICONTROL 활성화]** 다음에 있음 **[!UICONTROL 런처 속성]** 페이지를 가리키도록 업데이트하는 중입니다. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

자산에 워크플로우를 한 번만 수동으로 적용하려면 을 적용합니다 [!UICONTROL DAM 메타데이터 원본에 쓰기] 왼쪽 레일의 워크플로입니다.

업로드된 모든 에셋에 워크플로를 적용하려면 사후 처리 프로필에 워크플로를 추가합니다.

<!-- Commenting for now. Need to document how to enable metadata writeback. See CQDOC-17254.

### Enable XMP writeback {#enable-xmp-writeback}

To enable the metadata changes to be propagated to the renditions of the asset when uploading it, modify the **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuration in Configuration Manager.

1. To open Configuration Manager, access `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuration.
1. Select the **[!UICONTROL Propagate XMP]** option, and then save the changes.

### Enable XMP write-back for specific renditions {#enable-xmp-writeback-for-specific-renditions}

To let the XMP write-back feature propagate metadata changes to select renditions, specify these renditions to the [!UICONTROL XMP Writeback Process] workflow step of DAM Metadata WriteBack workflow. By default, this step is configured with the original rendition.

For the XMP write-back feature to propagate metadata to the rendition thumbnails 140.100.png and 319.319.png, perform these steps.

1. Tap/click the Experience Manager logo, and then navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Workflow]** &gt; **[!UICONTROL Models]**.
1. From the Models page, open the **[!UICONTROL DAM Metadata Writeback]** workflow model.
1. In the **[!UICONTROL DAM Metadata Writeback]** properties page, open the **[!UICONTROL XMP Writeback Process]** step.
1. In the **[!UICONTROL Step Properties]** dialog box, tap/click the **[!UICONTROL Process]** tab.
1. In the **[!UICONTROL Arguments]** box, add `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`, and then tap/click **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Save the changes.
1. To regenerate the Pyramid TIFF (PTIFF) renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata write-back workflow. PTIFF renditions are only created and stored locally in a Dynamic Media Hybrid implementation.

1. Save the workflow.

The metadata changes are propagated to the renditions renditions thumbnail.140.100.png and thumbnail.319.319.png of the asset, and not the others.
-->

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
