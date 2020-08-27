---
title: 디지털 자산의 메타데이터를 관리할 수 있습니다 [!DNL Adobe Experience Manager].
description: 메타데이터의 유형과 메타데이터를 기반으로 에셋을 자동으로 구성하고 [!DNL Adobe Experience Manager Assets] helps manage metadata for assets to allow easier categorization and organization of assets. [!DNL Experience Manager] 처리하는 방법을 살펴볼 수 있습니다.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: d6a0848547a6dcbb058576827d3cacbc8045ae79
workflow-type: tm+mt
source-wordcount: '1933'
ht-degree: 0%

---


# 디지털 자산의 메타데이터 관리 {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] 모든 에셋에 대한 메타데이터를 유지합니다. 또한 보다 쉽게 에셋을 분류하고 구성할 수 있으며 특정 에셋을 찾는 사용자에게 도움이 됩니다. 메타데이터 관리는 업로드된 파일에서 메타데이터를 추출하는 기능 [!DNL Experience Manager Assets]을 통해 크리에이티브 워크플로우와 통합됩니다. 자산을 사용하여 메타데이터를 유지 및 관리할 수 있으므로 메타데이터를 기반으로 자산을 자동으로 구성하고 처리할 수 있습니다.

>[!MORELIKETHIS]
>
>* [XMP 메타데이터](xmp-metadata.md)
>* [메타데이터를 편집하거나 추가하는 방법](meta-edit.md)


<!-- 
* [Metadata Schemata Reference](meta-ref.md)
-->

## 메타데이터가 필요한 이유 {#why-metadata}

메타데이터는 데이터에 대한 데이터를 의미합니다. 이러한 점에서 데이터는 디지털 자산, 즉 이미지를 나타냅니다. 메타데이터는 효율적인 에셋 관리를 위해 중요합니다.

메타데이터는 자산에 사용할 수 있는 모든 데이터의 집합이지만 해당 이미지에 반드시 포함되지는 않습니다. 메타데이터의 몇 가지 예는 다음과 같습니다.

* 자산의 이름입니다.
* 마지막 수정 시간 및 날짜
* 저장소에 저장된 자산의 크기입니다.
* 포함된 폴더의 이름입니다.
* 관련 자산 또는 적용된 태그

위의 메타데이터 속성은 자산에 대해 관리할 [!DNL Experience Manager] 수 있으며, 이를 통해 사용자는 모든 자산을 볼 수 있습니다. 예를 들어, 마지막 수정 날짜별로 자산을 정렬하는 것은 최근에 추가된 자산을 검색하려고 할 때 유용합니다.

디지털 자산에 더 많은 고급 데이터를 추가할 수 있습니다. 예:

* 에셋 유형(이미지, 비디오, 오디오 클립 또는 문서입니까?).
* 자산의 소유자입니다.
* 자산의 제목입니다.
* 자산의 설명입니다.
* 자산에 지정된 태그.

더 많은 메타데이터는 자산을 더 분류하는 데 도움이 되며, 디지털 정보의 양이 증가함에 따라 유용합니다. 파일 이름만 기준으로 수백 개의 파일을 관리할 수 있습니다. 그러나 이 방법은 확장 가능하지 않습니다. 관련된 사람의 수와 관리되는 자산의 수가 증가하는 것은 짧다.

메타데이터가 추가되면서 디지털 자산의 값이 커집니다.

* 더욱 편리해진 시스템 및 사용자 정의
* 관리가 간편함 - 동일한 속성 세트를 사용하여 보다 손쉽게 에셋을 찾을 수 있고 변경 사항을 적용할 수 있습니다.
* 전체 - 더 많은 메타데이터가 포함된 추가 정보 및 컨텍스트를 자산에 전달합니다.

이러한 이유로 디지털 자산에 대한 메타데이터를 만들고, 관리하고, 교환할 수 있는 적절한 방법을 제공합니다. [!DNL Assets]

## 메타데이터 유형 {#types-of-metadata}

두 가지 기본 메타데이터 유형은 기술 메타데이터와 설명 메타데이터입니다.

기술 메타데이터는 디지털 자산을 처리하고 있지만 수동으로 유지 관리해서는 안 되는 소프트웨어 애플리케이션에 유용합니다. [!DNL Experience Manager Assets] 그리고 기타 소프트웨어는 기술 메타데이터를 자동으로 결정하며 에셋이 수정될 때 메타데이터가 변경될 수 있습니다. 자산의 사용 가능한 기술 메타데이터는 대개 자산의 파일 유형에 따라 달라집니다. 기술 메타데이터의 몇 가지 예는 다음과 같습니다.

* 파일의 크기입니다.
* 이미지의 Dimension(높이 및 너비).
* 오디오 또는 비디오 파일의 비트 전송률입니다.
* 이미지의 해상도(세부 수준).

설명 메타데이터는 애플리케이션 도메인과 관련된 메타데이터입니다(예: 자산이 만들어지는 비즈니스). 설명 메타데이터를 자동으로 결정할 수 없습니다. 수동 또는 반자동 생성됩니다. 예를 들어 GPS 지원 카메라는 위도와 경도를 자동으로 추적하고 이미지에 지리 태그를 추가할 수 있습니다.

설명 메타데이터 정보를 수동으로 만드는 데 소요되는 비용이 높습니다. 따라서 소프트웨어 시스템과 조직 전체에서 메타데이터를 간편하게 교환할 수 있는 기준이 마련되었습니다. [!DNL Experience Manager Assets] 은 메타데이터 관리에 대한 모든 관련 표준을 지원합니다.

## 인코딩 표준 {#encoding-standards}

파일에 메타데이터를 임베드하는 다양한 방법이 있습니다. 다양한 인코딩 표준이 지원됩니다.

* XMP:추출된 메타데이터 [!DNL Assets] 를 저장소 내에 저장하는 데 사용됩니다.
* ID3:for audio and video files.
* Exif:for image files.
* 기타/레거시:출처 [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel]등

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP)은 모든 메타데이터 관리에 사용되는 개방형 표준 [!DNL Experience Manager Assets] 입니다. 표준은 모든 파일 포맷에 임베드할 수 있는 범용 메타데이터 인코딩을 제공합니다. Adobe과 다른 회사는 리치 컨텐츠 모델을 제공하면서 XMP standard를 지원합니다. XMP 표준과 PC 사용자는 강력한 플랫폼을 [!DNL Experience Manager Assets] 갖추고 있으며 자세한 내용은 [XMP을 참조하십시오](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

컴퓨터 또는 휴대용 MP3 플레이어에서 디지털 오디오 파일을 재생할 때 이러한 ID3 태그에 저장된 데이터가 표시됩니다.

ID3 태그는 MP3 파일 포맷용으로 설계되었습니다. 형식에 대한 추가 정보:

* ID3 태그는 MP3 및 mp3PRO 파일에서 작동합니다.
* WAV에는 태그가 없습니다.
* WMA에는 오픈 소스 구현을 허용하지 않는 전용 태그가 있습니다.
* Ogg Vorbis는 Ogg 컨테이너에 포함된 Xiph 주석을 사용합니다.
* AAC는 독점적 태깅 포맷을 사용합니다.

### Exif {#exif}

Exif(Exchange) 는 디지털 사진 분야에서 가장 널리 사용되는 메타데이터 포맷입니다. JPEG, TIFF, RIFF 및 WAV와 같은 다양한 파일 포맷으로 메타데이터 속성의 고정된 용어를 임베드하는 방법을 제공합니다. Exif는 메타데이터를 메타데이터 이름 및 메타데이터 값의 쌍으로 저장합니다. 이러한 메타데이터 이름-값-쌍은 태그라고도 합니다. 태깅과 혼동하지 마십시오 [!DNL Experience Manager]. 최신 디지털 카메라는 Exif 메타데이터와 이를 지원하는 최신 그래픽 소프트웨어를 제작합니다. Exif 형식은 특히 이미지에 대한 메타데이터 관리를 위한 가장 일반적인 분모입니다.

Exif의 주요 제한 사항은 BMP, GIF 또는 PNG와 같이 널리 사용되는 몇 가지 이미지 파일 형식이 지원되지 않는다는 것입니다.

Exif에서 정의한 메타데이터 필드는 일반적으로 기술적 사항이며 수사적 메타데이터 관리를 위해 제한된 용도로 사용됩니다. 이러한 이유로, Exif 속성을 [!DNL Experience Manager Assets] 일반적인 메타데이터 스키마 [](metadata-schemas.md) 및 XMP에 매핑하는 기능을 제공합니다.

#### 기타 메타데이터 {#other-metadata}

파일에서 임베드할 수 있는 기타 메타데이터에는 [!DNL Microsoft Word][!DNL PowerPoint], [!DNL Excel]등이 포함됩니다.

## 디지털 자산의 메타데이터 관리 {#manage-assets-metadata}

Enterprise Manager 자산을 사용하면 여러 자산의 메타데이터를 동시에 편집할 수 있으므로 일반적인 메타데이터 변경 사항을 자산에 일괄적으로 신속하게 전파할 수 있습니다. 속성  페이지를 사용하여 메타데이터 속성을 일반 값으로 변경하거나 태그를 추가하거나 수정할 수 있습니다. 메타데이터 속성 추가, 수정, 삭제 등 메타데이터 속성 페이지를 사용자 정의하려면 스키마 편집기를 사용합니다.

>[!NOTE]
>
>벌크 편집 방법은 폴더 또는 컬렉션에서 사용할 수 있는 자산에 대해 작동합니다. 여러 폴더에서 사용할 수 있거나 일반적인 기준과 일치하는 자산의 경우 검색 후 메타데이터를 [일괄 업데이트할 수 있습니다](/help/assets/search-assets.md#metadataupdates).

1. 편집할 자산의 위치로 이동합니다.
1. 공통 속성을 편집할 자산을 선택합니다.
1. 도구 모음에서 속성 **[!UICONTROL 을 탭/클릭하여]** 선택한 자산에 대한 [!UICONTROL 속성] 페이지를 엽니다.

   >[!NOTE]
   >
   >여러 자산을 선택하면 자산에 대해 가장 낮은 공통 상위 양식이 선택됩니다. 즉, [!UICONTROL 속성] 페이지에는 모든 개별 자산의 [!UICONTROL 속성] 페이지에서 공통인 메타데이터 필드만 표시됩니다.

1. 다양한 탭에서 선택한 자산에 대한 메타데이터 속성을 수정합니다.
1. 특정 자산에 대한 메타데이터 편집기를 보려면 목록에서 나머지 자산을 선택 취소합니다. 메타데이터 편집기 필드는 특정 자산에 대한 메타데이터로 채워집니다.

   >[!NOTE]
   >
   >* [ [!UICONTROL 속성] ] 페이지에서 자산의 선택을 취소하여 자산 목록에서 자산을 제거할 수 있습니다. 자산 목록에는 기본적으로 모든 자산이 선택되어 있습니다. 목록에서 제거하는 자산에 대한 메타데이터는 업데이트되지 않습니다.
   >* 자산 목록 맨 위에서 **[!UICONTROL 제목]** 근처의 확인란을 선택하여 자산 선택과 목록 지우기 간을 전환합니다.


1. 자산에 대해 다른 메타데이터 스키마를 선택하려면 도구 모음에서 **[!UICONTROL 설정을]** 탭/클릭하고 원하는 스키마를 선택합니다. 변경 사항을 저장합니다.
1. 여러 값이 들어 있는 필드에 기존 메타데이터와 함께 새 메타데이터를 추가하려면 추가 모드 **[!UICONTROL 를 선택합니다]**. 이 옵션을 선택하지 않으면 새 메타데이터가 필드에 있는 기존 메타데이터를 대체합니다. 제출을 탭/ **[!UICONTROL 클릭합니다]**.

   >[!CAUTION]
   >
   >단일 값 필드의 경우 추가 모드를 선택하더라도 새 메타데이터는 필드의 기존 값에 추가되지 **[!UICONTROL 않습니다]**.

## 처리 프로필을 사용한 사용자 지정 메타데이터 {#metadata-compute-service}

Cloud Service으로 에셋은 클라우드 기본 서비스를 사용하여 자산에 대한 사용자 정의 메타데이터를 생성할 수 있습니다. 사용자 지정 메타데이터를 생성하도록 처리 프로필을 구성합니다. 처리 프로필 [사용 방법을 참조하십시오](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

![처리 프로필의 메타데이터 변환](assets/processing-profile-metadata.png)

>[!TIP]
>
>하나의 처리 프로필만 폴더에 적용할 수 있습니다. 한 폴더의 자산에 여러 처리를 적용하려면 단일 처리 프로필에 더 많은 옵션을 추가하십시오. 예를 들어 단일 프로필에서는 표현물을 생성하고, 자산을 트랜스코딩하고, 사용자 지정 메타데이터를 생성하는 등의 작업을 할 수 있습니다. 각 작업에 대해 MIME 유형 필터를 적용하여 필요한 파일 형식에 대해 적절한 작업이 트리거되도록 할 수 있습니다.

## 일괄 메타데이터 업데이트에 대한 제한 구성 {#configlimit}

AEM은 DOS와 같은 상황을 방지하기 위해 Sling 요청에서 지원되는 매개 변수의 수를 제한합니다. 한 번에 많은 자산의 메타데이터를 업데이트할 때 한도에 도달해도 메타데이터가 더 많은 자산에 대해 업데이트되지 않습니다. AEM은 로그에 다음 경고를 생성합니다.

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

제한을 변경하려면 웹 콘솔( **[!UICONTROL 도구]** > **[!UICONTROL 작업]** > **[!UICONTROL 웹 콘솔]**)에 액세스하고 최대 POST 매개 변수 **[!UICONTROL 변경Maximum의 값 변경]** **** Apache Apache Sling 요청 매개 변수 처리OSGi 구성에 액세스합니다.

## 메타데이터 스키마 {#metadata-schemata}

메타데이터 스키마는 다양한 애플리케이션에서 사용할 수 있는 메타데이터 속성 정의의 사전 정의된 세트입니다. 속성은 항상 자산과 연결되어 있습니다. 즉, 속성이 &#39;정보&#39;임을 의미합니다.

또한 필요에 맞는 메타데이터 구성이 없는 경우 자체 메타데이터 스키마를 디자인할 수도 있습니다. 기존 정보를 복제하지 마십시오. 조직 내에서 스키마를 구분하면 보다 손쉽게 메타데이터를 공유할 수 있습니다. [!DNL Experience Manager] 에서는 가장 인기 있는 메타데이터 스키마의 기본 목록을 제공합니다. 이 목록을 사용하면 메타데이터 전략을 신속하게 시작하고 필요한 메타데이터 속성을 신속하게 선택할 수 있습니다.

지원되는 메타데이터 구성표는 아래에 나열되어 있습니다.

### 표준 메타데이터 {#standard-metadata}

* DC - [!DNL Dublin Core] 중요하며 널리 사용되는 메타데이터 세트입니다.
* DICOM - 의료 분야의 디지털 이미징 및 커뮤니케이션
* `Iptc4xmpCore` 및 `iptc4xmpExt` - International Press Communications Standard에는 많은 분야별 메타데이터가 포함되어 있습니다.
* RDF - Resource Description Framework - for generic semantic web metadata.
* XMP - [!DNL Extensible Metadata Platform].
* `xmpBJ` - 기본 작업 티켓.

### 애플리케이션별 메타데이터 {#application-specific-metadata}

애플리케이션별 메타데이터에는 기술 및 설명 메타데이터가 포함됩니다. 이러한 메타데이터를 사용하는 경우 다른 애플리케이션에서 메타데이터를 사용할 수 없을 수도 있습니다. 예를 들어, 다른 이미지 렌더링 응용 프로그램이 메타데이터에 액세스할 수 없을 수도 [!DNL Adobe Photoshop] 있습니다. 애플리케이션별 속성을 표준 속성으로 변경하는 워크플로우 단계를 만들 수 있습니다.

* ACDSee - 프로그램에서 관리하는 [!DNL ACDSee] 메타데이터입니다. www.acdsee.com [를 참조하십시오](https://www.acdsee.com/).
* 앨범 - [!DNL Adobe Photoshop Album].
* CQ - 사용됨 [!DNL Experience Manager Assets].
* DAM - 사용 [!DNL Experience Manager Assets].
* DEX - [Optima SC Description 탐색기는](http://www.optimasc.com/products/dex/index.html) Windows 운영 체제용 메타데이터 및 파일 관리를 위한 도구 모음입니다.
* CRS - [Adobe Photoshop Camera Raw](https://helpx.adobe.com/camera-raw/using/introduction-camera-raw.html).
* LR - [!DNL Adobe Lightroom].
* MediaPro - [iView MediaPro](https://en.wikipedia.org/wiki/Phase_One_Media_Pro).
* Microsoft Photo 및 MP - Microsoft Photo.
* PDF 및 PDF/X.
* Photoshop 및 psAux - [!DNL Adobe Photoshop].

### Digital Rights Management 메타데이터 {#digital-rights-management-metadata}

* 참조 - [!DNL Creative Commons].
* [!DNL XMPRights].
* PLUS - [Picture Licensing Universal System](https://www.useplus.com).
* PRISM - [업계 표준 메타데이터에 대한 게시 요구](https://www.idealliance.org/prism-metadata)사항.
* PRL - 프리즘 권한 언어.
* PUR - 프리즘 사용 권한.
* `xmpPlus` - PLUS와 XMP 통합

### 사진별 메타데이터 {#photography-specific-metadata}

* Exif - GPS 위치를 비롯한 카메라의 기술 정보.
* CRS - [!DNL Camera Raw] 스키마.
* `iptc4xmpCore` 및 `iptc4xmpExt`.
* TIFF - 이미지 메타데이터(TIFF 이미지에만 해당)

### 인쇄 관련 메타데이터 {#print-specific-metadata}

* PDF 및 PDF/X - Adobe PDF 및 타사 애플리케이션
* PRISM - [업계 표준 메타데이터에 대한 게시 요구](https://www.prismstandard.org)사항.
* XMP - [!DNL Extensible Metadata Platform].
* `xmpPG` - 페이지 텍스트를 위한 XMP 메타데이터

### 멀티미디어 관련 메타데이터 {#multimedia-specific-metadata}

* `xmpDM` - [!DNL Dynamic Media].
* `xmpMM` - 미디어 관리.

## 메타데이터 기반의 워크플로우 {#metadata-driven-workflows}

메타데이터 기반의 워크플로우를 사용하면 일부 프로세스를 자동화하여 효율성을 향상시킬 수 있습니다. 메타데이터 중심의 워크플로우에서 워크플로우 관리 시스템은 워크플로우를 읽고 그 결과 사전 정의된 작업을 수행합니다. 예를 들어 메타데이터 중심의 워크플로우를 사용할 수 있는 방법 중 몇 가지를 있습니다.

* 워크플로우는 이미지에 제목이 있는지 여부를 확인할 수 있습니다. 그렇지 않으면 제목 추가에 알립니다.
* 워크플로우는 자산에 대한 저작권 공지가 배포를 허용하는지 여부를 확인할 수 있습니다. 따라서 시스템은 자산을 한 서버나 다른 서버로 전송합니다.
* 워크플로우는 사전 정의된 필수 메타데이터 또는 *잘못된* 메타데이터가 있는 자산이 없는 자산을 확인할 수 있습니다.
