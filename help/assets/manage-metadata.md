---
title: 디지털 에셋의 메타데이터 관리
description: 메타데이터 유형에 대해 알아보고 자산의 메타데이터를 보다 쉽게 분류하고 구성할 수 있도록  [!DNL Adobe Experience Manager Assets] 이(가) 자산의 메타데이터를 관리하는 방법을 알아봅니다. [!DNL Experience Manager] 을(를) 사용하면 메타데이터를 기반으로 에셋을 자동으로 구성하고 처리할 수 있습니다.
contentOwner: AG
mini-toc-levels: 1
feature: Asset Management, Metadata
role: User, Architect, Admin
exl-id: 73a82bc2-1dda-4090-b7ee-29d1a632ba25
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1962'
ht-degree: 9%

---

# 디지털 에셋의 메타데이터 관리 {#managing-metadata-for-digital-assets}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/metadata.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Experience Manager Assets]은(는) 모든 에셋에 대한 메타데이터를 유지합니다. 에셋을 보다 쉽게 분류하고 구성할 수 있으며 특정 에셋을 찾는 사람들에게 도움이 됩니다. [!DNL Experience Manager Assets]에 업로드된 파일에서 메타데이터를 추출하는 기능을 사용하면 메타데이터 관리가 크리에이티브 워크플로우와 통합됩니다. 에셋으로 메타데이터를 보관하고 관리할 수 있으므로 에셋의 메타데이터를 기반으로 에셋을 자동으로 구성하고 처리할 수 있습니다.

<!-- 
* [Metadata Schemata Reference](meta-ref.md)
-->

## 메타데이터가 필요한 이유 {#why-metadata}

메타데이터는 데이터에 대한 데이터를 의미합니다. 이와 관련하여 데이터는 디지털 자산, 즉 이미지를 나타냅니다. 메타데이터는 효율적인 에셋 관리에 중요합니다.

메타데이터는 에셋에 사용할 수 있는 모든 데이터의 집합이지만 해당 이미지에 반드시 포함되지는 않습니다. 메타데이터의 일부 예는 다음과 같습니다.

* 에셋 이름.
* 마지막으로 수정한 시간 및 날짜입니다.
* 저장소에 저장된 에셋의 크기입니다.
* 포함된 폴더의 이름입니다.
* 관련 에셋 또는 적용된 태그.

위의 항목은 [!DNL Experience Manager]이(가) 에셋에 대해 관리할 수 있는 기본 메타데이터 속성으로, 사용자가 모든 에셋을 볼 수 있도록 합니다. 예를 들어 최근에 추가되거나 수정된 자산을 검색하려고 할 때 마지막 수정 날짜별로 자산을 정렬하는 것이 유용합니다.

디지털 에셋에 높은 수준의 데이터를 추가할 수 있습니다. 예를 들면 다음과 같습니다.

* 에셋 유형(이미지, 비디오, 오디오 클립 또는 문서입니까?).
* 에셋 소유자.
* 에셋 제목
* 에셋에 대한 설명.
* 자산에 할당된 태그.

더 많은 메타데이터는 에셋을 더 세부적으로 분류하는 데 도움이 되며 디지털 정보의 양이 증가할 때 유용합니다. 파일 이름만 기준으로 수백 개의 파일을 관리할 수 있습니다. 그러나 이 접근 방식은 확장할 수 없습니다. 관련된 사람의 수와 관리하는 자산의 수가 증가하면 부족하다.

메타데이터를 추가하면 자산이 다음과 같이 되기 때문에 디지털 자산의 가치가 증가합니다.

* 접근성 향상 - 시스템과 사용자가 쉽게 찾을 수 있습니다.
* 관리 용이성 - 동일한 속성 세트를 가진 자산을 더 쉽게 찾고 변경 사항을 적용할 수 있습니다.
* 최대 효율 - 자산은 더 많은 메타데이터로 더 많은 정보와 컨텍스트를 전달합니다.

이러한 이유로 [!DNL Assets]은(는) 디지털 에셋에 대한 메타데이터를 만들고, 관리하고, 교환할 수 있는 적절한 수단을 제공합니다.

## 메타데이터 유형 {#types-of-metadata}

메타데이터는 기술, 정보 및 관리 메타데이터로 분류됩니다.

### 기술 메타데이터

기술 메타데이터는 디지털 에셋의 기술적 측면에 중점을 두며, 다음과 관련된 중요한 정보를 제공합니다.

* 파일 크기
* 형식
* 해결 방법
* 치수
* 색상 모드

이러한 유형의 메타데이터는 사용자가 디지털 에셋을 이해하고 효율적으로 사용하는 데 도움이 됩니다.

### 정보 메타데이터

정보 메타데이터는 콘텐츠 이해를 높이고 콘텐츠 검색 및 검색 기능을 지원하기 위해 설명 정보를 제공합니다. 여기에는 키워드, 캡션 및 설명이 포함됩니다. <br>예를 들어 Experience Manager Assets에서 비디오를 관리할 때 다음 정보 메타데이터를 포함할 수 있습니다.

* **키워드**: 마케팅, 제품 출시, 프로모션
* **캡션**: 흥미로운 기능을 갖춘 최신 제품 소개
* **설명**: 비디오 콘텐츠에 대한 자세한 개요입니다.

### 관리 메타데이터

관리 메타데이터는 디지털 자산의 관리적 측면을 다룬다. 디지털 자산 관리 시스템 내에서 자산의 전체 라이프사이클을 액세스 제어, 규정 준수 및 관리할 수 있습니다. 여기에는 다음과 관련된 정보가 포함됩니다.

* 자산 소유권
* 사용 권한
* 권한
* 기타 관리 세부 정보

이 메타데이터 유형을 사용하면 효과적인 에셋 관리, 액세스 제어 및 규정 준수가 가능합니다.

<!-- Learn more about [metadata best practices](metadata-best-practices.md) to manage your digital assets effectively. -->

<!-- The two basic types of metadata are technical metadata and descriptive metadata.

Technical metadata is useful for software applications that are dealing with digital assets and should not be maintained manually. [!DNL Experience Manager Assets] and other software automatically determine technical metadata and the metadata may change when the asset is modified. The available technical metadata of an asset depends largely on the file type of the asset. Some examples of technical metadata are:

* Size of a file.
* Dimensions (height and width) of an image.
* Bit rate of an audio or video file.
* Resolution (level of detail) of an image.

Descriptive metadata is metadata concerned with the application domain, for example, the business that an asset is coming from. Descriptive metadata cannot be determined automatically. It is created manually or semi-automatically. For example, a GPS-enabled camera can automatically track the latitude and longitude and add geotag the image.

The cost of manually creating descriptive metadata information is high. So, standards are established to ease the exchange of metadata across software systems and organizations. [!DNL Experience Manager Assets] supports all relevant standards for metadata management. -->

## 메타데이터 및 마지막 수정 {#last-modification}

에셋의 마지막 수정 날짜는 에셋의 원본 파일이 마지막으로 수정된 시간을 반영합니다. 따라서 수정 날짜 및 사용자는 다음과 같은 경우에만 변경됩니다.

* 에셋의 새 버전이 업로드됨
* 자산이 재처리되었습니다.

마지막 수정 날짜 및 사용자는 변경되지 않습니다.

* 에셋을 이동하거나 이름을 변경하는 경우
* 에셋이 체크 아웃, 체크 인 또는 버전인 경우
* 에셋이 게시되거나 게시되지 않을 때
* 메타데이터 업데이트 시
* 참조 또는 컬렉션 업데이트

## 인코딩 표준 {#encoding-standards}

파일에 메타데이터를 임베드하는 방법은 다양합니다. 다양한 인코딩 표준이 지원됩니다.

* XMP: [!DNL Assets]이(가) 저장소에서 추출된 메타데이터를 저장하는 데 사용합니다.
* ID3: 오디오 및 비디오 파일용.
* Exif: 이미지 파일용.
* 기타/레거시: [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel] 등.

### XMP {#xmp}

[!DNL Extensible Metadata Platform](XMP)은 [!DNL Experience Manager Assets]에서 모든 메타데이터 관리에 사용하는 개방형 표준입니다. 이 표준은 모든 파일 형식에 임베드할 수 있는 범용 메타데이터 인코딩을 제공합니다. Adobe 및 기타 기업은 XMP standard가 풍부한 콘텐츠 모델을 제공하므로 이를 지원합니다. XMP standard 및 [!DNL Experience Manager Assets]의 사용자는 빌드할 강력한 플랫폼이 있습니다. 자세한 내용은 [XMP](https://www.adobe.com/products/xmp.html)을(를) 참조하십시오.

### ID3 {#id}

이러한 ID3 태그에 저장된 데이터는 컴퓨터 또는 휴대용 MP3 플레이어에서 디지털 오디오 파일을 재생할 때 표시됩니다.

ID3 태그는 MP3 파일 형식을 위해 설계되었습니다. 형식에 대한 추가 정보:

* ID3 태그는 MP3 및 mp3PRO 파일에서 작동합니다.
* WAV에 태그가 없습니다.
* WMA에는 오픈 소스 구현을 허용하지 않는 독점 태그가 있습니다.
* Ogg Vorbis는 Ogg 컨테이너에 포함된 Xiph 주석을 사용합니다.
* AAC는 고유한 태그 지정 형식을 사용합니다.

### Exif {#exif}

Exif(교환 이미지 파일 형식)는 디지털 사진에서 사용되는 가장 인기 있는 메타데이터 형식입니다. JPEG, TIFF, RIFF 및 WAV와 같은 다양한 파일 형식으로 메타데이터 속성에 대한 고정 어휘를 임베드하는 방법을 제공합니다. Exif는 메타데이터를 메타데이터 이름과 메타데이터 값의 쌍으로 저장합니다. 이러한 메타데이터 이름-값-쌍은 태그라고도 하며, [!DNL Experience Manager]의 태그와 혼동하면 안 됩니다. 최신 디지털 카메라는 Exif 메타데이터를 만들고 최신 그래픽 소프트웨어가 이를 지원합니다. Exif 형식은 특히 이미지에 대한 메타데이터 관리에 사용되는 가장 낮은 공통 분모입니다.

Exif의 주요 제한 사항은 BMP, GIF 또는 PNG와 같은 일부 인기 있는 이미지 파일 형식이 지원되지 않는다는 것입니다.

Exif에서 정의한 메타데이터 필드는 일반적으로 기술적 성격으로 설명 메타데이터 관리에 제한적으로 사용됩니다. 이러한 이유로 [!DNL Experience Manager Assets]은(는) Exif 속성을 [일반적인 메타데이터 스키마](metadata-schemas.md)와(과) XMP에 매핑하도록 제공합니다.

#### 기타 메타데이터 {#other-metadata}

파일에서 포함할 수 있는 다른 메타데이터에는 [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel] 등이 있습니다.

## 디지털 에셋의 메타데이터 관리 {#manage-assets-metadata}

Enterprise Manager Assets을 사용하면 여러 에셋의 메타데이터를 동시에 편집할 수 있으므로 일반적인 메타데이터 변경 사항을 에셋에 일괄적으로 빠르게 전달할 수 있습니다. [!UICONTROL 속성] 페이지에서 메타데이터 속성을 공통 값으로 변경하거나 태그를 추가하거나 수정합니다. 메타데이터 속성 추가, 수정, 삭제를 포함하여 메타데이터 속성 페이지를 사용자 정의하려면 스키마 편집기를 사용합니다.

>[!NOTE]
>
>벌크 편집 메서드는 폴더 또는 컬렉션에서 사용할 수 있는 에셋에 대해 작동합니다. 여러 폴더에서 사용할 수 있거나 일반적인 기준과 일치하는 에셋의 경우 [검색 후 메타데이터를 일괄 업데이트](/help/assets/search-assets.md#metadata-updates)할 수 있습니다.

1. 편집할 에셋의 위치로 이동합니다.
1. 공통 속성을 편집할 자산을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 선택하여 선택한 자산에 대한 [!UICONTROL 속성] 페이지를 엽니다.

   >[!NOTE]
   >
   >여러 에셋을 선택하면 에셋에 대해 가장 낮은 공통 상위 양식이 선택됩니다. 즉, [!UICONTROL 속성] 페이지에는 모든 개별 자산의 [!UICONTROL 속성] 페이지에서 공통되는 메타데이터 필드만 표시됩니다.

1. 다양한 탭에서 선택한 에셋의 메타데이터 속성을 수정합니다.
1. 특정 에셋에 대한 메타데이터 편집기를 보려면 목록에서 나머지 에셋 선택을 취소합니다. 메타데이터 편집기 필드는 특정 에셋의 메타데이터로 채워집니다.

   >[!NOTE]
   >
   >* [!UICONTROL 속성] 페이지에서 선택을 취소하여 자산 목록에서 자산을 제거할 수 있습니다. 에셋 목록에는 기본적으로 모든 에셋이 선택되어 있습니다. 목록에서 제거하는 에셋의 메타데이터는 업데이트되지 않습니다.
   >* 자산 목록의 맨 위에서 **[!UICONTROL 제목]** 옆의 확인란을 선택하여 자산을 선택하고 목록을 지우는 것을 전환합니다.

1. 에셋에 대해 다른 메타데이터 스키마를 선택하려면 도구 모음에서 **[!UICONTROL 설정]**&#x200B;을 선택하고 원하는 스키마를 선택합니다. 변경 사항을 저장합니다.
1. To append the new metadata with the existing metadata in fields that contain multiple values, select **[!UICONTROL Append mode]**. If you do not select this option, the new metadata replaces the existing metadata in the fields. **[!UICONTROL 제출]**&#x200B;을 선택합니다.

   >[!CAUTION]
   >
   >For single-value fields, the new metadata is not appended to the existing value in the field even if you select **[!UICONTROL Append mode]**.

## 처리 프로필을 사용한 사용자 지정 메타데이터 {#metadata-compute-service}

Assets as a [!DNL Cloud Service]은(는) 클라우드 네이티브 서비스를 사용하여 자산에 대한 사용자 지정 메타데이터를 생성할 수 있습니다. 처리 프로필을 구성하여 사용자 지정 메타데이터를 생성합니다. [처리 프로필 사용 방법](/help/assets/asset-microservices-configure-and-use.md#use-profiles)을 참조하세요.

![프로필을 처리하는 중 메타데이터 렌디션](assets/processing-profile-metadata.png)

>[!TIP]
>
>한 개의 처리 프로필만 폴더에 적용할 수 있습니다. 폴더의 에셋에 여러 처리를 적용하려면 단일 처리 프로필에 더 많은 옵션을 추가합니다. 예를 들어 단일 프로필은 렌디션을 생성하고, 자산을 트랜스코딩하고, 사용자 지정 메타데이터를 생성하는 등의 작업을 수행할 수 있습니다. 각 작업에 대해 MIME 유형 필터를 적용하여 필요한 파일 형식에 대해 적절한 작업이 트리거되도록 할 수 있습니다.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Configure limit for bulk metadata update {#configlimit}

To prevent DOS-like situation, [!DNL Experience Manager] limits the number of parameters supported in a Sling request. When updating metadata of many assets in one go, you may reach the limit and the metadata does not get updated for more assets. [!DNL Experience Manager] generates the following warning in the logs:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

To change the limit, access Web Console ( **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**) and change the value of **[!UICONTROL Maximum POST Parameters]** in **[!UICONTROL Apache Sling Request Parameter Handling]** OSGi configuration.
-->

## 메타데이터 스키마 {#metadata-schemata}

메타데이터 스키마는 다양한 애플리케이션에서 사용할 수 있는 사전 정의된 메타데이터 속성 정의 세트입니다. 속성은 항상 자산과 연결되어 있습니다. 즉, 속성은 리소스에 대한 &#39;정보&#39;입니다.

필요에 맞는 메타데이터 스키마가 없는 경우 고유한 메타데이터 스키마를 디자인할 수도 있습니다. 기존 정보를 복제하지 마십시오. 조직 내에서 스키마를 분리하면 메타데이터를 더 쉽게 공유할 수 있습니다. [!DNL Experience Manager]은(는) 가장 인기 있는 메타데이터 스키마의 기본 목록을 제공합니다. 이 목록을 사용하면 메타데이터 전략을 빠르게 시작하고 필요한 메타데이터 속성을 빠르게 선택할 수 있습니다.

지원되는 메타데이터 스키마 목록은 다음과 같습니다.

### 표준 메타데이터 {#standard-metadata}

* DC - [!DNL Dublin Core]은(는) 중요하고 널리 사용되는 메타데이터 집합입니다.
* DICOM - 디지털 이미징 및 의학 커뮤니케이션.
* `Iptc4xmpCore` 및 `iptc4xmpExt` - International Press Communications Standard에는 많은 주체별 메타데이터가 포함되어 있습니다.
* RDF - 리소스 설명 프레임워크 - 일반 시맨틱 웹 메타데이터용.
* XMP - [!DNL Extensible Metadata Platform].
* `xmpBJ` - 기본 작업 티켓팅입니다.

### 애플리케이션별 메타데이터 {#application-specific-metadata}

애플리케이션별 메타데이터에는 기술적 메타데이터와 기술적 메타데이터가 포함됩니다. 이러한 메타데이터를 사용하는 경우 다른 응용 프로그램에서 해당 메타데이터를 사용하지 못할 수 있습니다. 예를 들어 다른 이미지 렌더링 응용 프로그램에서 [!DNL Adobe Photoshop] 메타데이터에 액세스하지 못할 수 있습니다. 응용 프로그램별 속성을 표준 속성으로 변경하는 워크플로 단계를 만들 수 있습니다.

* ACDSee - [!DNL ACDSee] 프로그램에서 관리하는 메타데이터. [www.acdsee.com/](https://www.acdsee.com/)을(를) 참조하십시오.
* 앨범 - [!DNL Adobe Photoshop Album].
* CQ - [!DNL Experience Manager Assets]이(가) 사용합니다.
* DAM - [!DNL Experience Manager Assets]이(가) 사용합니다.
* DEX - [Optima SC 설명 탐색기](https://www.optimasc.com/products/dex/index.html)는 Windows 운영 체제용 메타데이터 및 파일 관리를 위한 도구 모음입니다.
* CRS - [Adobe Photoshop Camera Raw](https://helpx.adobe.com/camera-raw/using/introduction-camera-raw.html).
* LR - [!DNL Adobe Lightroom].
* MediaPro - [iView MediaPro](https://en.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto 및 MP - Microsoft 사진.
* PDF 및 PDF/X
* Photoshop 및 psAux - [!DNL Adobe Photoshop].

### Digital Rights Management 메타데이터 {#digital-rights-management-metadata}

* 참조 - [!DNL Creative Commons].
* [!DNL XMPRights]
* PLUS - [Picture Licensing Universal System](https://www.useplus.com).
<!--THIS LINK IS 404 WITH NO SUITABLE REPLACEMENT * PRISM - [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata). -->
* PRL - PRISM Rights 언어.
* PUR - 프리즘 사용 권한.
* `xmpPlus` - PLUS와 XMP의 통합

### 사진별 메타데이터 {#photography-specific-metadata}

* Exif - GPS 위치를 포함한 카메라의 기술 정보.
* CRS - [!DNL Camera Raw] 스키마.
* `iptc4xmpCore` 및 `iptc4xmpExt`.
* TIFF - 이미지 메타데이터(TIFF 이미지에만 해당되지 않음).

### 인쇄별 메타데이터 {#print-specific-metadata}

* PDF 및 PDF/X - Adobe PDF 및 타사 애플리케이션.
<!--THIS LINK IS 404 WITH NO SUITABLE REPLACEMENT * PRISM - [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata). -->
* XMP - [!DNL Extensible Metadata Platform].
* `xmpPG` - 페이징된 텍스트에 대한 XMP 메타데이터입니다.

### 멀티미디어별 메타데이터 {#multimedia-specific-metadata}

* `xmpDM` - [!DNL Dynamic Media].
* `xmpMM` - 미디어 관리.

## 메타데이터 기반 워크플로 {#metadata-driven-workflows}

메타데이터 기반 워크플로를 만들면 일부 프로세스를 자동화하여 효율성을 향상시킬 수 있습니다. 메타데이터 기반 워크플로에서 워크플로 관리 시스템은 워크플로를 읽고 그 결과 사전 정의된 몇 가지 작업을 수행합니다. 예를 들어 메타데이터 기반 워크플로를 사용할 수 있는 몇 가지 방법은 다음과 같습니다.

* 워크플로우는 이미지에 제목이 있는지 여부를 확인할 수 있습니다. 그렇지 않으면 시스템에서 제목을 추가하도록 알립니다.
* 워크플로우는 자산에 대한 저작권 고지가 배포를 허용하는지 여부를 확인할 수 있습니다. 따라서 시스템은 자산을 한 서버 또는 다른 서버로 전송합니다.
* 워크플로우에서는 사전 정의된 필수 메타데이터가 없는 자산 또는 *잘못된* 메타데이터가 있는 자산을 확인할 수 있습니다.

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [XMP 메타데이터](xmp-metadata.md)
>* [메타데이터를 편집하거나 추가하는 방법](meta-edit.md)
