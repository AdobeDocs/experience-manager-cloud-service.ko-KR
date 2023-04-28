---
title: 디지털 자산의 메타데이터 관리
description: 메타데이터 유형과 방법에 대해 알아봅니다. [!DNL Adobe Experience Manager Assets] 자산을 보다 쉽게 분류하고 구성할 수 있도록 자산에 대한 메타데이터를 관리하는 데 도움이 됩니다. [!DNL Experience Manager] 를 사용하면 메타데이터를 기반으로 자산을 자동으로 구성하고 처리할 수 있습니다.
contentOwner: AG
mini-toc-levels: 1
feature: Asset Management,Metadata
role: User,Architect,Admin
exl-id: 73a82bc2-1dda-4090-b7ee-29d1a632ba25
source-git-commit: 91af800c8b2f83e689e057f304a8e144ae4cc5ed
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 8%

---

# 디지털 자산의 메타데이터 관리 {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] 모든 자산에 대한 메타데이터를 유지합니다. 자산을 보다 쉽게 분류하고 구성할 수 있으며 특정 자산을 찾는 사람에게 도움이 됩니다. 에 업로드된 파일에서 메타데이터를 추출하는 기능 [!DNL Experience Manager Assets], 메타데이터 관리는 크리에이티브 워크플로우와 통합됩니다. 자산으로 메타데이터를 유지 및 관리하는 기능을 사용하면 메타데이터를 기반으로 자산을 자동으로 구성하고 처리할 수 있습니다.

<!-- 
* [Metadata Schemata Reference](meta-ref.md)
-->

## 메타데이터가 필요한 이유 {#why-metadata}

메타데이터는 데이터에 대한 데이터를 의미합니다. 이러한 점에서 데이터는 디지털 자산, 즉 이미지를 나타냅니다. 메타데이터는 효율적인 에셋 관리에 있어 매우 중요합니다.

메타데이터는 자산에 사용할 수 있는 모든 데이터의 수집이지만 해당 이미지에 반드시 포함되어 있지는 않습니다. 메타데이터의 몇 가지 예는 다음과 같습니다.

* 자산의 이름입니다.
* 마지막 수정 날짜 및 시간
* 저장소에 저장된 자산의 크기입니다.
* 포함된 폴더의 이름입니다.
* 관련 자산 또는 적용된 태그.

위의 내용은 [!DNL Experience Manager] 자산을 관리할 수 있습니다. 이 경우 사용자가 모든 자산을 볼 수 있습니다. 예를 들어, 최근 수정 날짜별로 자산을 정렬하는 것은 최근에 추가되거나 수정된 자산을 검색하려고 할 때 유용합니다.

다음과 같이 디지털 자산에 고급 데이터를 추가할 수 있습니다.

* 자산 유형(이미지, 비디오, 오디오 클립 또는 문서입니까?).
* 자산의 소유자입니다.
* 자산의 제목입니다.
* 자산에 대한 설명입니다.
* 자산에 지정된 태그.

더 많은 메타데이터는 자산을 더 분류하는 데 도움이 되며, 디지털 정보의 양이 증가하면 유용합니다. 파일 이름만 기준으로 수백 개의 파일을 관리할 수 있습니다. 그러나 이 접근 방식은 확장할 수 없습니다. 관련된 사람의 수와 관리되는 자산의 수가 증가하면 부족합니다.

메타데이터를 추가하면 에셋이 다음과 같이 되기 때문에 디지털 에셋의 가치가 증가합니다.

* 접근성 향상 - 시스템과 사용자가 쉽게 찾을 수 있습니다.
* 관리 용이성 - 동일한 속성 세트를 가진 에셋을 더 쉽게 찾고 변경 사항을 적용할 수 있습니다.
* 최대 효율 - 에셋은 더 많은 메타데이터로 더 많은 정보와 컨텍스트를 전달합니다.

이런 이유로 [!DNL Assets] 는 디지털 자산에 대한 메타데이터를 만들고, 관리하고, 교환하는 올바른 방법을 제공합니다.

## 메타데이터 유형 {#types-of-metadata}

메타데이터의 두 가지 기본 유형은 기술 메타데이터와 설명 메타데이터입니다.

기술 메타데이터는 디지털 자산을 처리하는 소프트웨어 애플리케이션에 유용하며 수동으로 유지 관리해서는 안 됩니다. [!DNL Experience Manager Assets] 그리고 다른 소프트웨어는 기술 메타데이터를 자동으로 결정하며, 자산이 수정될 때 메타데이터가 변경될 수 있습니다. 자산의 사용 가능한 기술 메타데이터는 대개 자산의 파일 유형에 따라 다릅니다. 기술 메타데이터의 몇 가지 예는 다음과 같습니다.

* 파일 크기입니다.
* 이미지의 Dimension(높이 및 너비).
* 오디오 또는 비디오 파일의 비트율.
* 이미지의 해상도(세부 정보 수준).

설명 메타데이터는 애플리케이션 도메인(예: 자산이 만들어지는 비즈니스)과 관련된 메타데이터입니다. 설명 메타데이터를 자동으로 확인할 수 없습니다. 수동으로 또는 반자동으로 만들어집니다. 예를 들어 GPS 지원 카메라는 위도와 경도를 자동으로 추적하고 이미지에 지리 태그를 추가할 수 있습니다.

설명 메타데이터 정보를 수동으로 만드는 데 드는 비용이 높습니다. 따라서 소프트웨어 시스템과 조직 간에 메타데이터 교환을 쉽게 하기 위해 표준이 마련되었습니다. [!DNL Experience Manager Assets] 은 메타데이터 관리에 대한 모든 관련 표준을 지원합니다.

## 메타데이터 및 마지막 수정 사항 {#last-modification}

자산의 마지막 수정 날짜는 자산의 원본 파일을 마지막으로 수정한 시간을 반영합니다. 따라서 수정 날짜 및 사용자는 다음과 같은 경우에만 변경됩니다.

* 자산의 새 버전이 업로드됩니다
* 자산이 재처리됩니다

마지막 수정 날짜 및 사용자는 변경되지 않습니다.

* 자산을 이동하거나 이름을 바꾼 경우
* 자산을 체크 아웃하면 체크 아웃 또는 버전입니다
* 자산이 게시되거나 게시 취소된 경우
* 메타데이터 업데이트 시
* 참조 또는 컬렉션 업데이트

## 인코딩 표준 {#encoding-standards}

파일에 메타데이터를 포함하는 방법은 다양합니다. 다양한 인코딩 표준이 지원됩니다.

* XMP: 사용 [!DNL Assets] 추출된 메타데이터를 리포지토리 내에 저장합니다.
* ID3: 오디오 및 비디오 파일에 사용할 수 있습니다.
* 예: 이미지 파일에 사용할 수 있습니다.
* 기타/기존: 변환 전: [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel]등

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP)은 [!DNL Experience Manager Assets] 모든 메타데이터 관리에 사용됩니다. 이 표준에서는 모든 파일 형식에 포함할 수 있는 범용 메타데이터 인코딩을 제공합니다. Adobe 및 다른 회사는 풍부한 컨텐츠 모델을 제공하므로 XMP standard를 지원합니다. XMP standard 및 의 사용자 [!DNL Experience Manager Assets] 강력한 구축 플랫폼 구축 자세한 내용은 [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

컴퓨터 또는 휴대용 MP3 플레이어에서 디지털 오디오 파일을 재생할 때 이러한 ID3 태그에 저장된 데이터가 표시됩니다.

ID3 태그는 MP3 파일 형식용으로 디자인되었습니다. 형식에 대한 추가 정보:

* ID3 태그는 MP3 및 mp3PRO 파일에서 작동합니다.
* WAV에는 태그가 없습니다.
* WMA에는 오픈 소스 구현을 허용하지 않는 독점 태그가 있습니다.
* Ogg Vorbis는 Ogg 컨테이너에 포함된 Xiph 주석을 사용합니다.
* AAC는 전용 태그 지정 형식을 사용합니다.

### Exif {#exif}

Exif(Exif) 는 디지털 사진에 사용되는 가장 인기 있는 메타데이터 포맷입니다. JPEG, TIFF, RIFF 및 WAV와 같은 다양한 파일 형식으로 메타데이터 속성의 고정된 용어를 포함하는 방법을 제공합니다. Exif는 메타데이터를 메타데이터 이름 및 메타데이터 값의 쌍으로 저장합니다. 이러한 메타데이터 이름-값-쌍은 태그라고도 하며 의 태깅과 혼동하지 않도록 합니다 [!DNL Experience Manager]. 최신 디지털 카메라는 Exif 메타데이터를 만들고 최신 그래픽 소프트웨어를 지원합니다. 예를 들어 형식은 특히 이미지에 대한 메타데이터 관리를 위한 가장 낮은 공통 분모입니다.

Exif의 주요 제한 사항은 BMP, GIF 또는 PNG와 같이 널리 사용되는 몇 가지 이미지 파일 형식이 이를 지원하지 않는다는 것입니다.

Exif로 정의된 메타데이터 필드는 일반적으로 기술적인 부분이며 수사적 메타데이터 관리에 사용할 수 없습니다. 이런 이유로 [!DNL Experience Manager Assets] 은 Exif 속성을 [공통 메타데이터 스키마](metadata-schemas.md) XMP에 연결할 수도 있습니다.

#### 기타 메타데이터 {#other-metadata}

파일에서 임베드할 수 있는 기타 메타데이터에는 다음이 포함됩니다 [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel]등

## 디지털 자산의 메타데이터 관리 {#manage-assets-metadata}

Enterprise Manager Assets를 사용하면 여러 자산의 메타데이터를 동시에 편집할 수 있으므로 일반적인 메타데이터 변경 사항을 자산에 일괄 전파할 수 있습니다. 를 사용하십시오 [!UICONTROL 속성] 메타데이터 속성을 공통 값으로 변경하거나 태그를 추가 또는 수정할 수 있습니다. 메타데이터 속성 추가, 수정, 삭제를 포함하여 메타데이터 속성 페이지를 사용자 지정하려면 스키마 편집기를 사용합니다.

>[!NOTE]
>
>벌크 편집 방법은 폴더 또는 컬렉션에서 사용할 수 있는 자산에 대해 작동합니다. 여러 폴더 간에 사용할 수 있거나 공통 기준과 일치하는 자산의 경우 다음을 수행할 수 있습니다 [검색 후 메타데이터 대량 업데이트](/help/assets/search-assets.md#metadata-updates).

1. 편집할 자산의 위치로 이동합니다.
1. 공통 속성을 편집할 자산을 선택합니다.
1. 도구 모음에서 탭/클릭 **[!UICONTROL 속성]** 열다 [!UICONTROL 속성] 선택한 자산에 대한 페이지입니다.

   >[!NOTE]
   >
   >여러 자산을 선택하면 자산에 대해 가장 낮은 공통 상위 양식이 선택됩니다. 즉, [!UICONTROL 속성] 페이지에는 일반적으로 사용되는 메타데이터 필드만 표시됩니다 [!UICONTROL 속성] 모든 개별 자산의 페이지입니다.

1. 다양한 탭에서 선택한 자산에 대한 메타데이터 속성을 수정합니다.
1. 특정 자산에 대한 메타데이터 편집기를 보려면 목록에 있는 나머지 자산의 선택을 취소합니다. 메타데이터 편집기 필드는 특정 자산에 대한 메타데이터로 채워집니다.

   >[!NOTE]
   >
   >* 에서 [!UICONTROL 속성] 페이지에서, 선택 항목을 취소하여 자산 목록에서 자산을 제거할 수 있습니다. 자산 목록에는 기본적으로 선택된 모든 자산이 있습니다. 목록에서 제거하는 자산에 대한 메타데이터는 업데이트되지 않습니다.
   >* 자산 목록의 맨 위에서 근처에 있는 확인란을 선택합니다 **[!UICONTROL 제목]** 자산을 선택하고 목록 지우기 간을 전환하려면.


1. 자산에 대해 다른 메타데이터 스키마를 선택하려면 을 탭/클릭합니다 **[!UICONTROL 설정]** 도구 모음에서 원하는 스키마를 선택합니다. 변경 사항을 저장합니다.
1. To append the new metadata with the existing metadata in fields that contain multiple values, select **[!UICONTROL Append mode]**. If you do not select this option, the new metadata replaces the existing metadata in the fields. Tap/click **[!UICONTROL Submit]**.

   >[!CAUTION]
   >
   >For single-value fields, the new metadata is not appended to the existing value in the field even if you select **[!UICONTROL Append mode]**.

## 처리 프로필을 사용한 사용자 지정 메타데이터 {#metadata-compute-service}

로서의 자산 [!DNL Cloud Service] 클라우드 기본 서비스를 사용하여 자산에 대한 사용자 지정 메타데이터를 생성할 수 있습니다. 사용자 지정 메타데이터를 생성하도록 처리 프로필을 구성합니다. 자세한 내용은 [처리 프로필 사용 방법](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

![처리 프로필의 메타데이터 렌디션](assets/processing-profile-metadata.png)

>[!TIP]
>
>한 개의 처리 프로필만이 폴더에 적용될 수 있습니다. 폴더의 자산에 여러 처리를 적용하려면 단일 처리 프로필에 더 많은 옵션을 추가합니다. 예를 들어, 단일 프로필은 표현물을 생성하고, 자산을 코드 변환하고, 사용자 지정 메타데이터를 생성하는 등의 작업을 수행할 수 있습니다. 필요한 파일 형식에 대해 적절한 작업이 트리거되도록 각 작업에 MIME 유형 필터를 적용할 수 있습니다.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Configure limit for bulk metadata update {#configlimit}

To prevent DOS-like situation, [!DNL Experience Manager] limits the number of parameters supported in a Sling request. When updating metadata of many assets in one go, you may reach the limit and the metadata does not get updated for more assets. [!DNL Experience Manager] generates the following warning in the logs:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

To change the limit, access Web Console ( **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**) and change the value of **[!UICONTROL Maximum POST Parameters]** in **[!UICONTROL Apache Sling Request Parameter Handling]** OSGi configuration.
-->

## 메타데이터 스키마 {#metadata-schemata}

메타데이터 스키마는 다양한 애플리케이션에서 사용할 수 있는 미리 정의된 메타데이터 속성 정의 세트입니다. 속성은 항상 자산과 연결되어 있습니다. 즉, 속성이 리소스에 대해 &#39;정보&#39;입니다.

필요에 맞는 메타데이터 스키마가 없는 경우 자체 메타데이터 스키마를 디자인할 수도 있습니다. 기존 정보를 복제하지 마십시오. 조직 내에서 스키마를 분리하면 메타데이터를 더 쉽게 공유할 수 있습니다. [!DNL Experience Manager] 가장 인기 있는 메타데이터 스키마의 기본 목록을 제공합니다. 이 목록을 사용하면 메타데이터 전략을 시작하고 필요한 메타데이터 속성을 빠르게 선택할 수 있습니다.

지원되는 메타데이터 스키마는 아래에 나와 있습니다.

### 표준 메타데이터 {#standard-metadata}

* DC - [!DNL Dublin Core] 는 중요하며 널리 사용되는 메타데이터 세트입니다.
* DICOM - 의료 분야의 디지털 이미징 및 커뮤니케이션.
* `Iptc4xmpCore` 및 `iptc4xmpExt` - International Press Communications Standard에는 여러 제목 관련 메타데이터가 포함되어 있습니다.
* RDF - 리소스 설명 프레임워크 - 일반 시맨틱 웹 메타데이터용.
* XMP - [!DNL Extensible Metadata Platform].
* `xmpBJ` - 기본 구직 매표.

### 애플리케이션별 메타데이터 {#application-specific-metadata}

응용 프로그램별 메타데이터는 기술 및 설명 메타데이터를 포함합니다. 이러한 메타데이터를 사용하는 경우 다른 응용 프로그램에서 메타데이터를 사용하지 못할 수 있습니다. 예를 들어 다른 이미지 렌더링 응용 프로그램이 액세스할 수 없을 수 있습니다 [!DNL Adobe Photoshop] 메타데이터. 애플리케이션별 속성을 표준 속성으로 변경하는 워크플로우 단계를 만들 수 있습니다.

* ACDSee - [!DNL ACDSee] 프로그램. 자세한 내용은 [www.acdsee.com/](https://www.acdsee.com/).
* 앨범 - [!DNL Adobe Photoshop Album].
* CQ - 사용 [!DNL Experience Manager Assets].
* DAM - 사용 [!DNL Experience Manager Assets].
* DEX - [최적 SC 설명 탐색기](https://www.optimasc.com/products/dex/index.html) 는 Windows 운영 체제에 대한 메타데이터 및 파일 관리를 위한 도구 모음입니다.
* CRS - [Adobe Photoshop Camera Raw](https://helpx.adobe.com/camera-raw/using/introduction-camera-raw.html).
* LR - [!DNL Adobe Lightroom].
* MediaPro - [iView MediaPro](https://en.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto 및 MP - Microsoft 사진.
* PDF 및 PDF/X.
* Photoshop 및 psAux - [!DNL Adobe Photoshop].

### Digital Rights Management 메타데이터 {#digital-rights-management-metadata}

* 참조 - [!DNL Creative Commons].
* [!DNL XMPRights].
* 플러스 - [Picture Licensing Universal System](https://www.useplus.com).
* 프리즘 - [업계 표준 메타데이터에 대한 게시 요구 사항](https://www.idealliance.org/prism-metadata).
* PRL - 프리즘 권한 언어.
* PUR - 프리즘 사용 권한.
* `xmpPlus` - XMP과 PLUS 통합.

### 사진별 메타데이터 {#photography-specific-metadata}

* Exif - GPS 위치를 포함한 카메라의 기술 정보.
* CRS - [!DNL Camera Raw] 스키마.
* `iptc4xmpCore` 및 `iptc4xmpExt`.
* TIFF - 이미지 메타데이터(TIFF 이미지용뿐만 아니라).

### 인쇄별 메타데이터 {#print-specific-metadata}

* PDF 및 PDF/X - Adobe PDF 및 타사 애플리케이션.
* 프리즘 - [업계 표준 메타데이터에 대한 게시 요구 사항](https://www.idealliance.org/prism-metadata).
* XMP - [!DNL Extensible Metadata Platform].
* `xmpPG` - 페이징 텍스트의 XMP 메타데이터.

### 멀티미디어별 메타데이터 {#multimedia-specific-metadata}

* `xmpDM` - [!DNL Dynamic Media].
* `xmpMM` - 미디어 관리.

## 메타데이터 기반의 워크플로우 {#metadata-driven-workflows}

메타데이터 기반의 워크플로우를 만들면 일부 프로세스를 자동화할 수 있으므로 효율성이 향상됩니다. 메타데이터 기반 워크플로우에서 워크플로우 관리 시스템은 워크플로우를 읽고 그 결과 일부 사전 정의된 작업을 수행합니다. 예를 들어 메타데이터 기반 워크플로우를 사용할 수 있는 몇 가지 방법은 다음과 같습니다.

* 워크플로우는 이미지에 제목이 있는지 여부를 확인할 수 있습니다. 표시되지 않으면 시스템에서 제목을 추가하라는 메시지를 표시합니다.
* 워크플로우는 자산에 대한 저작권 공지가 배포를 허용하는지 여부를 확인할 수 있습니다. 따라서 시스템이 자산을 한 서버나 다른 서버로 전송합니다.
* 워크플로우는 사전 정의된 필수 메타데이터 또는 *잘못된* 메타데이터.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [XMP 메타데이터](xmp-metadata.md)
>* [메타데이터 편집 또는 추가 방법](meta-edit.md)

