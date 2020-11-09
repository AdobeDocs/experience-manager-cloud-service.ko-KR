---
title: XMP 메타데이터
description: 메타데이터 관리를 위한 XMP(Extensible Metadata Platform) 메타데이터 표준에 대해 알아봅니다. AEM에서 메타데이터를 생성, 처리 및 교환하기 위한 표준화된 포맷으로 사용합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0c915b32d676ff225cbe276be075d3ae1a865f11
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 1%

---


# XMP 메타데이터 {#xmp-metadata}

XMP(Extensible Metadata Platform)은 모든 메타데이터 관리를 위해 AEM Assets이 사용하는 메타데이터 표준입니다. XMP은 다양한 응용 프로그램에 대한 메타데이터를 생성, 처리 및 교환하기 위한 표준 형식을 제공합니다.

모든 파일 포맷에 임베드할 수 있는 범용 메타데이터 인코딩을 제공하는 것 외에도 XMP은 리치 [컨텐츠 모델을](#xmp-core-concepts) 제공하고 Adobe [및 다른 회사에서](#advantages-of-xmp) 지원하기 때문에 XMP과 함께 사용하는 사용자는 강력한 플랫폼을 사용하여 구축할 수 있습니다.

## XMP 개요 및 에코시스템 {#xmp-ecosystem}

AEM Assets은 기본적으로 XMP 메타데이터 표준을 지원합니다. XMP은 표준화된 및 독점 메타데이터를 디지털 자산에 처리 및 저장하는 표준입니다. XMP은 여러 애플리케이션이 메타데이터와 효과적으로 작업할 수 있는 일반적인 표준으로 설계되었습니다.

예를 들어 프로덕션 전문가는 Adobe 애플리케이션의 내장된 XMP 지원을 사용하여 다양한 파일 포맷에 정보를 전달할 수 있습니다. AEM Assets 저장소는 XMP 메타데이터를 추출하여 컨텐츠 라이프사이클을 관리하고 자동화 워크플로우를 만드는 기능을 제공합니다.

XMP은 데이터 모델, 스토리지 모델 및 스키마를 제공하여 메타데이터가 정의, 생성 및 처리되는 방식을 표준화합니다. 이러한 모든 개념이 이 섹션에 설명되어 있습니다.

EXIF, ID3 또는 Microsoft Office의 모든 기존 메타데이터는 자동으로 XMP으로 변환되며, 제품 카탈로그와 같은 고객별 메타데이터 스키마를 지원하도록 확장할 수 있습니다.

XMP의 메타데이터는 속성 집합으로 구성됩니다. 이러한 속성은 항상 리소스라고 하는 특정 엔티티와 연결됩니다.즉, 속성은 &quot;정보&quot;입니다. XMP의 경우 리소스는 항상 자산입니다.

XMP은 정의된 메타데이터 항목 집합과 함께 사용할 수 있는 [메타데이터](https://en.wikipedia.org/wiki/Metadata) 모델을 정의합니다. 또한 XMP은 사진, [스캔](https://en.wikipedia.org/wiki/XML_schema) 또는 텍스트로 작성, 사진 편집 단계(예: [자르기](https://en.wikipedia.org/wiki/Image_scanner)또는 색상 조정)를 통해 최종 이미지를 결합하는 등 다양한 처리 단계를 거칠 때 리소스의 내역을 기록하는 데 유용한 기본 속성에 대한 특정 [스키마를 정의합니다](https://en.wikipedia.org/wiki/Cropping_%28image%29) . XMP은 각 소프트웨어 프로그램 또는 디바이스를 통해 자신의 정보를 디지털 리소스에 추가하여 최종 디지털 파일로 저장할 수 있습니다.

XMP은 [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) 리소스 설명 프레임워크(RDF)의 하위 집합을 [사용하여 가장 일반적으로](https://en.wikipedia.org/wiki/Resource_Description_Framework) 시리얼라이즈 [및](https://en.wikipedia.org/wiki/XML)저장합니다.

### XMP의 이점 {#advantages-of-xmp}

XMP은 다른 인코딩 표준 및 구성표에 비해 다음과 같은 이점이 있습니다.

* XMP 기반의 메타데이터는 매우 강력하고 세부적으로 정의됩니다.
* XMP에서는 하나의 속성에 대해 여러 값을 사용할 수 있습니다.
* XMP은 표준화된 인코딩을 제공하므로 메타데이터를 손쉽게 교환할 수 있습니다.
* XMP은 확장 가능합니다. 자산에 추가 정보를 추가할 수 있습니다.

XMP 표준은 사용자 정의 유형의 메타데이터를 XMP 데이터에 추가할 수 있도록 확장 가능하도록 고안되었습니다. 반면에 EXIF에는 확장할 수 없는 고정 속성 목록이 있습니다.

>[!NOTE]
>
>XMP에서는 일반적으로 이진 데이터 형식을 포함할 수 없습니다. 예를 들어, XMP에서 이진 데이터를 가져오려면 축소판 이미지와 같은 XML 호환 형식으로 인코딩해야 합니다 `Base64`.

### XMP 코어 개념 {#xmp-core-concepts}

**네임스페이스 및 스키마**

XMP 스키마는 데이터 유형과 설명 정보를 포함하는 공통 XML 네임스페이스에 있는 속성 이름 세트입니다. XMP 스키마는 XML 네임스페이스 URI로 식별됩니다. 네임스페이스를 사용하면 이름이 같지만 의미가 다른 여러 스키마의 속성 간 충돌을 방지할 수 있습니다.

예를 들어, 독립적으로 디자인된 두 가지 스키마의 **생성자** 속성은 자산을 만든 사람을 의미하거나 자산을 만든 응용 프로그램을 의미할 수 있습니다(예: Adobe Photoshop).

**XMP 속성 및 값**

XMP에는 하나 이상의 스키마의 속성이 포함될 수 있습니다. 예를 들어 많은 Adobe 애플리케이션에서 사용되는 일반적인 하위 세트는 다음을 포함할 수 있습니다.

* 더블린 코어 스키마: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* XMP 기본 스키마: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* XMP rights management 스키마: `xmpRights:WebStatement`, `xmpRights:Marked`
* XMP 미디어 관리 스키마: `xmpMM:DocumentID`

**언어 대체 요소**

XMP에서는 텍스트 속성에 속성을 추가하여 텍스트 언어를 지정할 수 `xml:lang` 있습니다.

## 표현물로 XMP 원본에 쓰기 {#xmp-writeback-to-renditions}

Adobe Experience Manager(AEM) 자산의 이 XMP 쓰기 되돌림 기능은 자산 변환에 대한 자산 메타데이터 변경 사항을 복제합니다.

AEM Assets 내에서 또는 자산을 업로드하는 동안 자산의 메타데이터를 변경하면 변경 내용은 처음에 CRXDE의 자산 노드 내에 저장됩니다.

XMP 다시 쓰기 기능은 메타데이터 변경 내용을 자산의 모든 표현물 또는 특정 표현물에 전파합니다.

제목이 있는 자산의 [!UICONTROL 제목] 속성을 수정하는 시나리오 `Classic Leather` 를 `Nylon`고려하십시오.

![메타데이터](assets/metadata.png)

이 경우, AEM Assets은 **[!UICONTROL 제목]** 속성에 대한 변경 사항을 자산 계층에 저장된 자산 메타데이터에 대한 `dc:title` 매개 변수에 저장합니다.

![metadata_stored](assets/metadata_stored.png)

그러나 AEM Assets은 자산의 변환에 메타데이터 변경 사항을 자동으로 전파하지 않습니다.

XMP 다시 쓰기 기능을 사용하면 메타데이터 변경 사항을 자산의 모든 표현물 또는 특정 표현물에 전파할 수 있습니다. 하지만 변경 사항은 자산 계층의 메타데이터 노드 아래에 저장되지 않습니다. 대신 이 기능에는 변환에 대한 바이너리 파일의 변경 사항이 포함됩니다.

### XMP 다시 쓰기 활성화 {#enable-xmp-writeback}

<!-- asgupta, Engg: Need attention here to update the configuration manager changes.
-->

업로드 시 메타데이터 변경 사항이 자산의 변환에 전파되도록 하려면 Configuration Manager에서 **[!UICONTROL Adobe CQ DAM Rendition Maker]** 구성을 수정하십시오.

1. 구성 관리자를 열려면 액세스 `https://[aem_server]:[port]/system/console/configMgr`를 참조하십시오.
1. **[!UICONTROL Adobe CQ DAM Rendition Maker]** 구성을 엽니다.
1. XMP **[!UICONTROL 전달]** 옵션을 선택한 다음 변경 내용을 저장합니다.

### 특정 변환에 대해 XMP 다시 쓰기 활성화 {#enable-xmp-writeback-for-specific-renditions}

XMP 쓰기 되돌림 기능이 메타데이터 변경 사항을 선택하여 변환에 적용하도록 하려면 이러한 변환을 DAM 메타데이터 쓰기 [!UICONTROL 백 워크플로우의] XMP 쓰기처리 워크플로우 단계에 지정합니다. 기본적으로 이 단계는 원래 변환으로 구성됩니다.

XMP 쓰기 되돌림 기능이 메타데이터를 변환 축소판 140.100.png 및 319.319.png에 전파하려면 다음 단계를 수행하십시오.

1. AEM 로고를 탭/클릭한 다음 **[!UICONTROL 도구]** > 워크플로우 **[!UICONTROL >]** 모델 **[!UICONTROL 으로]**&#x200B;이동합니다.
1. 모델 페이지에서 **[!UICONTROL DAM 메타데이터 쓰기]** 워크플로우 모델을 엽니다.
1. DAM **[!UICONTROL 메타데이터 원본에 쓰기]** 속성 페이지에서 **[!UICONTROL XMP 쓰기]** 처리 단계를 엽니다.
1. 단계 **[!UICONTROL 속성]** 대화 상자에서 프로세스 **[!UICONTROL 탭을 탭/]** 클릭합니다.
1. 인수 **[!UICONTROL 상자에서]** 추가한 `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`다음 확인을 탭/ **[!UICONTROL 클릭합니다]**.

   ![step_properties](assets/step_properties.png)

1. 변경 사항을 저장합니다.
1. 새로운 속성을 사용하여 다이내믹 미디어 이미지에 대한 PTIFF(Pyramid TIFF) 변환을 다시 생성하려면 DAM 메타데이터 쓰기 취소 워크플로우에 **[!UICONTROL 다이내믹 미디어 프로세스 이미지 자산]** 단계를 추가하십시오. PTIFF 변환은 Dynamic Media Hybrid 구현에서만 로컬로 만들어지고 저장됩니다.

1. 워크플로우를 저장합니다.

메타데이터 변경 사항이 변환 축소판 그림 140.100.png 및 thumbnail.319.319.png로 전파되며 다른 항목은 전파되지 않습니다.

>[!MORELIKETHIS]
>
>* [ADOBE별 XMP 사양](https://www.adobe.com/devnet/xmp.html)

