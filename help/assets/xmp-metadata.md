---
title: XMP 메타데이터
description: 메타데이터 관리를 위한 XMP(Extensible Metadata Platform) 메타데이터 표준에 대해 알아봅니다. AEM에서 메타데이터를 생성, 처리 및 교환하기 위한 표준화된 형식으로 사용합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0c915b32d676ff225cbe276be075d3ae1a865f11
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 1%

---


# XMP 메타데이터 {#xmp-metadata}

XMP(Extensible Metadata Platform)는 모든 메타데이터 관리를 위해 AEM Assets에서 사용하는 메타데이터 표준입니다. XMP은 다양한 응용 프로그램에 대한 메타데이터를 생성, 처리 및 교환하기 위한 표준 형식을 제공합니다.

모든 파일 포맷에 임베드할 수 있는 범용 메타데이터 인코딩을 제공하는 것 외에도 XMP은 풍부한 [컨텐츠 모델](#xmp-core-concepts)을 제공하며 Adobe](#advantages-of-xmp) 및 다른 회사에서 지원하는 [이므로 AEM Assets과 결합된 XMP 사용자는 강력한 플랫폼을 사용하여 구축할 수 있습니다.

## XMP 개요 및 에코시스템 {#xmp-ecosystem}

AEM Assets은 기본적으로 XMP 메타데이터 표준을 지원합니다. XMP은 표준화된 및 독점 메타데이터를 디지털 자산에 처리 및 저장하는 표준입니다. XMP은 여러 애플리케이션이 메타데이터와 효과적으로 작업할 수 있는 일반적인 표준으로 설계되었습니다.

예를 들어 프로덕션 전문가는 Adobe 애플리케이션의 내장된 XMP 지원을 사용하여 다양한 파일 포맷에 정보를 전달할 수 있습니다. AEM Assets 리포지토리는 XMP 메타데이터를 추출하여 컨텐츠 라이프사이클을 관리하고 자동화 워크플로우를 만드는 기능을 제공합니다.

XMP은 데이터 모델, 스토리지 모델 및 스키마를 제공하여 메타데이터가 정의, 생성 및 처리되는 방식을 표준화합니다. 이러한 모든 개념이 이 섹션에 설명되어 있습니다.

EXIF, ID3 또는 Microsoft Office의 모든 기존 메타데이터는 자동으로 XMP으로 변환되므로 제품 카탈로그 등 고객별 메타데이터 스키마를 지원하도록 확장할 수 있습니다.

XMP의 메타데이터는 일련의 속성으로 구성됩니다. 이러한 속성은 항상 리소스라고 하는 특정 엔티티와 연결됩니다.즉, 속성은 리소스에 대해 &quot;정보&quot;입니다. XMP의 경우 리소스는 항상 자산입니다.

XMP은 정의된 메타데이터 항목 집합에 사용할 수 있는 [메타데이터](https://en.wikipedia.org/wiki/Metadata) 모델을 정의합니다. XMP은 또한 사진 촬영, [스캔한](https://en.wikipedia.org/wiki/Image_scanner)에서 사진 편집 단계(예: [자르기](https://en.wikipedia.org/wiki/Cropping_%28image%29) 또는 색상 조정)를 통해 최종 이미지로 어셈블하는 등 여러 처리 단계를 거칠 때 리소스의 내역을 기록하는 데 유용한 기본 속성에 대해 특정 [스키마](https://en.wikipedia.org/wiki/XML_schema)를 정의합니다. XMP을 사용하면 각 소프트웨어 프로그램 또는 디바이스에서 자신의 정보를 디지털 리소스에 추가할 수 있으며 이러한 정보는 최종 디지털 파일로 보관할 수 있습니다.

XMP은 대부분 일반적으로 [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework)(RDF)의 하위 집합을 사용하여 시리얼라이즈 및 저장하며, 이 프레임워크는 다시 [XML](https://en.wikipedia.org/wiki/XML)로 표현됩니다.

### XMP {#advantages-of-xmp}의 이점

XMP은 다른 인코딩 표준 및 구성표에 비해 다음과 같은 이점이 있습니다.

* XMP 기반의 메타데이터는 매우 강력하고 세부적으로 정의됩니다.
* XMP에서는 하나의 속성에 여러 값을 사용할 수 있습니다.
* XMP은 표준화된 인코딩을 제공하므로 메타데이터를 손쉽게 교환할 수 있습니다.
* XMP은 확장 가능합니다. 자산에 추가 정보를 추가할 수 있습니다.

XMP 표준은 확장 가능하도록 설계되었으며, XMP 데이터에 사용자 정의 유형의 메타데이터를 추가할 수 있습니다. 반면에 EXIF에는 확장할 수 없는 고정 속성 목록이 있습니다.

>[!NOTE]
>
>XMP에서는 일반적으로 이진 데이터 형식을 포함할 수 없습니다. 이진 데이터를 XMP에 가져오려면 축소판 이미지와 같은 XML 호환 형식으로 인코딩해야 합니다(예: `Base64`).

### XMP 코어 개념 {#xmp-core-concepts}

**네임스페이스 및 스키마**

XMP 스키마는 공통 XML 네임스페이스에 포함된 속성 이름 세트입니다.
데이터 유형 및 설명 정보. XMP 스키마는 XML 네임스페이스 URI로 식별됩니다. 네임스페이스를 사용하면 이름이 같지만 의미가 다른 여러 스키마에 있는 속성 간 충돌이 방지됩니다.

예를 들어, 독립적으로 디자인된 2개의 스키마에서 **Creator** 속성은 자산을 만든 사람을 의미하거나 자산을 만든 응용 프로그램을 의미할 수 있습니다(예: Adobe Photoshop).

**XMP 속성 및 값**

XMP에는 하나 이상의 스키마에 있는 속성이 포함될 수 있습니다. 예를 들어 많은 Adobe 응용 프로그램에서 사용하는 일반적인 하위 집합은 다음을 포함할 수 있습니다.

* 더블린 코어 스키마:`dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* XMP 기본 스키마:`xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* XMP 권한 관리 스키마:`xmpRights:WebStatement`, `xmpRights:Marked`
* XMP 미디어 관리 스키마:`xmpMM:DocumentID`

**언어 대체 요소**

XMP에서는 텍스트 언어를 지정하기 위해 텍스트 속성에 `xml:lang` 속성을 추가하는 기능을 제공합니다.

## 표현물로 XMP 원본에 쓰기 {#xmp-writeback-to-renditions}

AEM(Adobe Experience Manager) Assets의 이 XMP 쓰기 되돌리기 기능은 자산 변환에 대한 자산 메타데이터 변경 내용을 복제합니다.

AEM Assets 내에서 또는 자산을 업로드하는 동안 에셋에 대한 메타데이터를 변경하면 변경 내용이 처음에 CRXDE의 에셋 노드 내에 저장됩니다.

XMP 쓰기 되돌리기 기능은 메타데이터 변경 사항을 자산의 모든 또는 특정 표현물에 전파합니다.

`Classic Leather`라는 제목의 자산의 [!UICONTROL 제목] 속성을 `Nylon`으로 수정하는 시나리오를 생각해 보십시오.

![메타데이터](assets/metadata.png)

이 경우 AEM Assets은 자산 계층 구조에 저장된 자산 메타데이터에 대한 `dc:title` 매개 변수에 **[!UICONTROL Title]** 속성에 대한 변경 내용을 저장합니다.

![metadata_stored](assets/metadata_stored.png)

그러나 AEM Assets은 자산의 변환에 메타데이터 변경 사항을 자동으로 전파하지 않습니다.

XMP 쓰기 되돌리기 기능을 사용하면 에셋의 모든 또는 특정 표현물에 메타데이터 변경 내용을 적용할 수 있습니다. 하지만 변경 사항은 자산 계층의 메타데이터 노드 아래에 저장되지 않습니다. 대신 이 기능은 변환에 대한 바이너리 파일의 변경 사항을 포함합니다.

### XMP 다시 쓰기 활성화 {#enable-xmp-writeback}

<!-- asgupta, Engg: Need attention here to update the configuration manager changes.
-->

메타데이터 변경 내용을 업로드할 때 자산의 변환에 전파되도록 하려면 Configuration Manager에서 **[!UICONTROL Adobe CQ DAM Rendition Maker]** 구성을 수정합니다.

1. 구성 관리자를 열려면 `https://[aem_server]:[port]/system/console/configMgr`에 액세스하십시오.
1. **[!UICONTROL Adobe CQ DAM Rendition Maker]** 구성을 엽니다.
1. **[!UICONTROL XMP]** 전파 옵션을 선택한 다음 변경 내용을 저장합니다.

### 특정 변환에 대해 XMP 쓰기 되돌리기 사용 {#enable-xmp-writeback-for-specific-renditions}

XMP 쓰기 되돌리기 기능이 일부 변환에 대한 메타데이터 변경 사항을 전파하도록 하려면 DAM 메타데이터 쓰기 뒤로 워크플로우의 [!UICONTROL XMP 쓰기 저장 프로세스] 워크플로우 단계에 이러한 변환을 지정합니다. 기본적으로 이 단계는 원래 변환으로 구성됩니다.

XMP 쓰기 되돌리기 기능이 변환 축소판 140.100.png 및 319.319.png에 메타데이터를 전파하려면 다음 단계를 수행합니다.

1. AEM 로고를 탭/클릭한 다음 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]**&#x200B;으로 이동합니다.
1. 모델 페이지에서 **[!UICONTROL DAM 메타데이터 쓰기 저장]** 워크플로우 모델을 엽니다.
1. **[!UICONTROL DAM 메타데이터 쓰기 저장]** 속성 페이지에서 **[!UICONTROL XMP 쓰기 저장 프로세스]** 단계를 엽니다.
1. **[!UICONTROL 단계 속성]** 대화 상자에서 **[!UICONTROL 프로세스]** 탭을 탭/클릭합니다.
1. **[!UICONTROL 인수]** 상자에서 `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`를 추가한 다음 **[!UICONTROL 확인]**&#x200B;을 탭/클릭합니다.

   ![step_properties](assets/step_properties.png)

1. 변경 사항을 저장합니다.
1. 새 특성을 사용하여 Dynamic Media 이미지에 대한 PTIFF(Pyramid TIFF) 변환을 다시 생성하려면 DAM 메타데이터 쓰기 되돌리기 워크플로에 **[!UICONTROL Dynamic Media 프로세스 이미지 자산]** 단계를 추가하십시오. PTIFF 변환은 Dynamic Media Hybrid 구현에서만 로컬에 만들어지고 저장됩니다.

1. 워크플로우를 저장합니다.

메타데이터 변경 사항은 에셋의 변환 축소판.140.100.png 및 thumbnail.319.319.png로 전파되며 다른 사항은 전파되지 않습니다.

>[!MORELIKETHIS]
>
>* [ADOBE별 XMP 사양](https://www.adobe.com/devnet/xmp.html)

