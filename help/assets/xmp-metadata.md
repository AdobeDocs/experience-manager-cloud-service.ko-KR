---
title: XMP 메타데이터
description: 메타데이터 관리를 위한 XMP(Extensible Metadata Platform) 메타데이터 표준에 대해 알아봅니다. AEM에서 메타데이터를 생성, 처리 및 교환하기 위한 표준 형식으로 사용합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# XMP 메타데이터 {#xmp-metadata}

XMP(Extensible Metadata Platform)는 모든 메타데이터 관리를 위해 AEM 자산에서 사용하는 메타데이터 표준입니다. XMP는 다양한 애플리케이션에서 메타데이터를 작성, 처리 및 교환하기 위한 표준 형식을 제공합니다.

모든 파일 포맷에 임베드할 수 있는 범용 메타데이터 인코딩을 제공하는 것 외에도 XMP는 리치 [컨텐츠 모델을](#xmp-core-concepts) 제공하고 Adobe 및 다른 회사에서 [지원되므로 AEM 자산과](#advantages-of-xmp) 함께 XMP 사용자는 강력한 플랫폼을 사용하여 구축할 수 있습니다.

## XMP 개요 및 에코시스템 {#xmp-ecosystem}

AEM Assets는 기본적으로 XMP 메타데이터 표준을 지원합니다. XMP 파섹 XMP 파섹

예를 들어 프로덕션 전문가는 Adobe 애플리케이션에서 내장된 XMP 지원을 사용하여 다양한 파일 포맷에 정보를 전달할 수 있습니다. AEM Assets 리포지토리는 XMP 메타데이터를 추출하여 이를 사용하여 콘텐츠 라이프사이클을 관리하고 자동화 워크플로우를 만드는 기능을 제공합니다.

XMP는 데이터 모델, 스토리지 모델 및 스키마를 제공하여 메타데이터가 정의, 생성 및 처리되는 방식을 표준화합니다. 이러한 모든 개념은 이 섹션에서 다룹니다.

EXIF, ID3 또는 Microsoft Office의 모든 기존 메타데이터는 XMP로 자동 변환되므로 제품 카탈로그와 같은 고객별 메타데이터 스키마를 지원하도록 확장할 수 있습니다.

XMP의 메타데이터는 속성 세트로 구성됩니다. 이러한 속성은 항상 리소스라고 하는 특정 엔티티와 연결됩니다.즉, 속성은 리소스에서 &quot;정보&quot;입니다. XMP의 경우 리소스는 항상 자산입니다.

XMP는 정의된 메타데이터 항목 집합과 함께 사용할 수 있는 [메타데이터](https://en.wikipedia.org/wiki/Metadata) 모델을 정의합니다. 또한 XMP는 사진 촬영, [스캔](https://en.wikipedia.org/wiki/XML_schema) 또는 텍스트로 제작, 사진 편집 단계( [자르기](https://en.wikipedia.org/wiki/Image_scanner)또는 색상 조정 등)에서 최종 이미지를 결합하는 등 다양한 처리 단계를 거칠 때 리소스의 내역을 기록하는 데 유용한 기본 속성에 대한 특정 [스키마를](https://en.wikipedia.org/wiki/Cropping_%28image%29) 정의합니다. XMP를 사용하면 각 소프트웨어 프로그램 또는 디바이스에서 자신의 정보를 디지털 리소스에 추가할 수 있으며, 이를 최종 디지털 파일로 저장할 수 있습니다.

XMP는 XML로 표현되는 W3C [RDF](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) ( [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) )의 하위 집합을 사용하여 [가장 일반적으로 시리얼라이즈 및](https://en.wikipedia.org/wiki/XML)저장됩니다.

### XMP의 이점 {#advantages-of-xmp}

XMP는 다른 인코딩 표준 및 구성표에 비해 다음과 같은 이점이 있습니다.

* XMP 기반의 메타데이터는 매우 강력하고 세밀하게 조정됩니다.
* XMP를 사용하면 하나의 속성에 여러 값을 사용할 수 있습니다.
* XMP 파섹
* XMP는 확장 가능합니다. 자산에 추가 정보를 추가할 수 있습니다.

XMP 표준은 XMP 데이터에 사용자 정의 유형의 메타데이터를 추가할 수 있도록 설계되어 있습니다. 반면 EXIF는 확장될 수 없는 고정 속성 목록이 있습니다.

>[!NOTE]
>
>일반적으로 XMP에서는 이진 데이터 형식을 포함할 수 없습니다. 이진 데이터를 XMP로 가져오려면 축소판 이미지와 같은 XML 친화적인 형식으로 인코딩해야 합니다 `Base64`.

### XMP 코어 개념 {#xmp-core-concepts}

**네임스페이스 및 스키마**

XMP 스키마는 데이터 유형 및 설명 정보를 포함하는 공통 XML 네임스페이스의 속성 이름 세트입니다. XMP 스키마는 XML 네임스페이스 URI로 식별됩니다. 네임스페이스를 사용하면 이름이 같지만 의미가 다른 여러 스키마에서 속성 간 충돌을 방지할 수 있습니다.

예를 들어, **독립적으로 디자인된 두** 스키마의 Creator 속성은 자산을 만든 사람이나 자산을 만든 응용 프로그램(예: Adobe Photoshop)을 의미할 수 있습니다.

**XMP 속성 및 값**

XMP에는 하나 이상의 스키마에서 생성된 속성이 포함될 수 있습니다. 예를 들어 많은 Adobe 애플리케이션에서 사용되는 일반적인 하위 세트에는 다음이 포함될 수 있습니다.

* 더블린 코어 스키마: `dc:title`, `dc:creator`, `dc:subject`, `dc:format``dc:rights`
* XMP 기본 스키마: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* XMP 권한 관리 스키마: `xmpRights:WebStatement`, `xmpRights:Marked`
* XMP 미디어 관리 스키마: `xmpMM:DocumentID`

**언어 대체 요소**

XMP에서는 텍스트 속성에 속성을 추가하여 텍스트 언어를 지정할 수 있는 기능을 제공합니다. `xml:lang`

## 표현물로 XMP 원본에 쓰기 {#xmp-writeback-to-renditions}

AEM(Adobe Experience Manager) 자산의 이 XMP 쓰기 되돌림 기능은 자산 변환에 대한 자산 메타데이터 변경 사항을 복제합니다.

AEM Assets 내에서 또는 자산을 업로드하는 동안 자산의 메타데이터를 변경하면 변경 내용이 처음에 CRXDE의 자산 노드 내에 저장됩니다.

XMP 다시 쓰기 기능은 메타데이터 변경 사항을 자산의 모든 또는 특정 표현물에 전파합니다.

제목이 [!UICONTROL 있는 자산의 제목] 속성을 수정하는 시나리오를 `Classic Leather` 고려하십시오 `Nylon`.

![메타데이터](assets/metadata.png)

이 경우 AEM Assets는 자산 계층에 저장된 **[!UICONTROL 자산]** 메타데이터의 `dc:title` 매개 변수에 Title속성에 대한 변경 사항을 저장합니다.

![metadata_stored](assets/metadata_stored.png)

그러나 AEM 자산에서는 메타데이터 변경 사항을 자산의 변환에 자동으로 전파하지 않습니다.

XMP 다시 쓰기 기능을 사용하면 메타데이터 변경 사항을 자산의 모든 표현물 또는 특정 표현물에 전파할 수 있습니다. 하지만 변경 사항은 자산 계층의 메타데이터 노드 아래에 저장되지 않습니다. 대신 이 기능에는 변환의 바이너리 파일에 변경 사항이 포함됩니다.

### XMP 다시 쓰기 활성화 {#enable-xmp-writeback}

<!-- asgupta, Engg: Need attention here to update the configuration manager changes.
-->

업로드 시 메타데이터 변경 사항이 자산의 변환에 전파되도록 하려면 Configuration Manager에서 **[!UICONTROL Adobe CQ DAM Rendition Maker]** 구성을 수정합니다.

1. Configuration Manager를 열려면 에 `https://[aem_server]:[port]/system/console/configMgr`액세스하십시오.
1. Adobe CQ **[!UICONTROL DAM Rendition Maker 구성을]** 엽니다.
1. [XMP **[!UICONTROL 전파]** ] 옵션을 선택한 다음 변경 내용을 저장합니다.

### 특정 변환에 대해 XMP 다시 쓰기 활성화 {#enable-xmp-writeback-for-specific-renditions}

XMP 쓰기 되돌림 기능이 메타데이터 변경 사항을 선택하여 표현물을 전파하도록 하려면 DAM 메타데이터 쓰기 [!UICONTROL 되돌리기 워크플로우의 XMP] 쓰기 프로세스 워크플로우 단계에 해당 변환을 지정합니다. 기본적으로 이 단계는 원래 변환으로 구성됩니다.

XMP 쓰기 되돌림 기능이 메타데이터를 변환 축소판 140.100.png 및 319.319.png에 전파하려면 다음 단계를 수행하십시오.

1. AEM 로고를 탭/클릭한 다음 도구 > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델로]** 이동합니다 ****.
1. 모델(Models) 페이지에서 DAM 메타데이터 **[!UICONTROL 원본에]** 쓰기 워크플로우 모델을 엽니다.
1. DAM 메타데이터 **[!UICONTROL 원본에]** 쓰기 **[!UICONTROL 속성 페이지에서 XMP]** 쓰기 프로세스 단계를엽니다.
1. 단계 **[!UICONTROL 속성]** 대화 상자에서 프로세스 **[!UICONTROL 탭을 탭/클릭합니다]** .
1. 인수 **[!UICONTROL 상자에서]** 추가한 `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`다음 확인을 탭/ **[!UICONTROL 클릭합니다]**.

   ![step_properties](assets/step_properties.png)

1. 변경 사항을 저장합니다.
1. 새로운 속성을 사용하여 다이내믹 미디어 이미지에 대한 PTIFF(Pyramid TIFF) 변환을 다시 생성하려면 다이내믹 미디어 프로세스 이미지 **[!UICONTROL 자산]** 단계를 DAM 메타데이터 다시 쓰기 워크플로우에 추가합니다. PTIFF 변환은 Dynamic Media Hybrid 구현에서만 로컬에 만들어지고 저장됩니다.

1. 워크플로우를 저장합니다.

메타데이터 변경 사항이 변환 변환 축소판으로 전파됩니다.140.100.png 및 thumbnail.319.319.png로 전달되며 다른 항목은 전파되지 않습니다.

<!--
>[!NOTE]
>
>For XMP writeback issues in 64 bit Linux, see [How to enable XMP write-back on 64-bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>For more information about supported platforms, see [XMP metadata write-back prerequisites](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).
-->

### XMP 메타데이터 필터링 {#filtering-xmp-metadata}

AEM Assets는 자산 이진에서 읽고 자산을 인제스트할 때 JCR에 저장된 XMP 메타데이터에 대한 속성/노드의 블랙 및 화이트 리스트 필터링을 모두 지원합니다.

블랙 필터링을 사용하면 제외에 지정된 속성을 제외한 모든 XMP 메타데이터 속성을 가져올 수 있습니다. 그러나 XMP 메타데이터가 많은 INDD 파일(예: 10,000개의 속성이 있는 1000개의 노드)과 같은 에셋 유형의 경우 필터링할 노드 이름이 항상 미리 알려지는 것은 아닙니다. 블랙 리스트 필터링을 통해 많은 XMP 메타데이터가 있는 많은 자산을 가져올 수 있는 경우 AEM 인스턴스/클러스터는 끊어진 관측 대기열과 같은 안정성 문제를 일으킬 수 있습니다.

XMP 메타데이터를 화이트 리스트 필터링하면 가져올 XMP 속성을 정의할 수 있어 이 문제를 해결합니다. 이렇게 하면 기타/알 수 없는 XMP 속성이 무시됩니다. 이전 버전과의 호환성을 위해 이러한 속성 중 일부를 블랙 리스트 필터에 추가할 수 있습니다.

>[!NOTE]
>
>필터링은 자산 바이너리의 XMP 소스에서 파생된 속성에만 작동합니다. EXIF 및 IPTC 포맷과 같이 XMP 소스가 아닌 소스에서 파생된 속성의 경우 필터링이 작동하지 않습니다. 예를 들어 에셋 작성 날짜는 EXIF TIFF `CreateDate` 에서 명명된 속성에 저장됩니다. AEM에서는 이 값이 이름이 `exif:DateTimeOriginal`지정된 메타데이터 필드에 있습니다. 소스가 XMP 소스가 아니므로 이 속성에서는 필터링이 작동하지 않습니다.

1. Configuration Manager를 열려면 에 `https://[aem_server]:[port]/system/console/configMgr`액세스하십시오.
1. Adobe CQ **[!UICONTROL DAM XmpFilter 구성을]** 엽니다.
1. 화이트 리스트 필터링을 적용하려면 [XMP **[!UICONTROL 속성에 화이트리스트 적용]**]을 선택하고 [XMP 필터링을 **[!UICONTROL 위한 화이트리스트 XML]** 이름] 상자에서 가져올 속성을 지정합니다.

1. 화이트리스트 필터링을 적용한 후 블랙리스트에 추가된 XMP 속성을 필터링하려면 XMP 필터링을 **** 위해 블랙리스트에 추가된 XML 이름 상자에서 지정합니다.

   >[!NOTE]
   >
   >[ **[!UICONTROL XMP 속성에 블랙 리스트 적용]** ] 옵션은 기본적으로 선택되어 있습니다. 다시 말해 블랙 리스트 필터링은 기본적으로 활성화되어 있습니다. 블랙 리스트 필터링을 비활성화하려면 [XMP 속성에 **[!UICONTROL 블랙 리스트 적용] 옵션을 선택]** 취소합니다.

1. 변경 사항을 저장합니다.

>[!MORELIKETHIS]
>
>* [Adobe의 XMP 사양](https://www.adobe.com/devnet/xmp.html)