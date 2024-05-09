---
title: 지원되는 파일 형식 및 MIME 유형
description: 에서 지원하는 파일 형식 및 MIME 유형 [!DNL Experience Manager Assets] as a [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management,Renditions
role: User,Admin
exl-id: e848aa77-7829-4adc-8b88-0279791a4525
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 34%

---

# [!DNL Assets] 지원되는 파일 형식 {#supported-file-formats}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 는 포맷과 관계없이 모든 바이너리 파일에 대해 스토리지, 온라인 메타데이터 관리, 버전 관리, 업로드 및 다운로드 등의 기본 컨텐츠 관리 기능을 지원합니다. [!DNL Adobe Experience Manager Assets] 는 다양한 파일 형식을 지원하며 각 제품 기능마다 다양한 형식을 지원합니다.

또한, [!DNL Experience Manager Assets] 에서는 미리 보기 및 렌디션을 생성하고 전체 텍스트 인덱싱을 위한 메타데이터 및 텍스트를 추출하는 확장된 지원을 제공합니다. 이 확장 지원은 다음을 사용하여 제공됩니다. [에셋 마이크로서비스](asset-microservices-configure-and-use.md).

에셋 마이크로서비스를 사용한 에셋 전환에 대한 주요 내용은 다음과 같습니다.

* 키 [Adobe 파일 형식](#adobe-formats) Adobe 애플리케이션 및 서비스에 의해 만들어짐: [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension], 및 [!DNL Adobe Acrobat] 또는 PDF.
* 키 [이미징 파일 형식](#image-formats).
* [Camera Raw 파일 형식](#camera-raw-formats) Canon, Nikon, Fujifilm, Olympus 및 기타 제조업체(Adobe Camera Raw 제공)를 비롯한 다양한 카메라
* 공통 [문서 형식](#document-formats), Microsoft® Office 및 Open Document 형식 포함.
* 의 광범위한 [비디오](#video-formats) 및 [오디오](#audio-formats) 형식.

다음 범례에서는 각 형식에 대한 지원 수준을 설명합니다.

| 지원 수준 | 설명 |
| ------------- | --------------------------- |
| ✓ | 지원됨 |
| * | 표 아래의 비고 참조 |
| - | 해당되지 않음 |

## Adobe 형식 {#adobe-formats}

| 파일 포맷 | 썸네일 생성 | 전체 텍스트 추출 | 메타데이터 추출 | 너비/높이 |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | - | ✓ | ✓ |
| 콜라주 | - | - | ✓ | - |
| DN | ✓ | - | ✓ | ✓ |
| SBSAR | ✓ | - | ✓ | ✓ |
| 아이디어 | - | - | ✓ | - |
| INDD | ✓ | - | ✓ | ✓ * |
| INDT | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | ✓ | - |
| PSB | ✓ | - | ✓ | ✓ |
| PSD | ✓ | - | ✓ | ✓ |
| XD | ✓ | - | ✓ | ✓ |

\* 대상 [!DNL Adobe InDesign] 파일(INDD), 렌디션 크기는 INDD 파일에 포함된 미리보기에 의해 결정됩니다. 에서 환경 설정 구성 [!DNL InDesign] (**[!UICONTROL 환경 설정 > 파일 처리 > 항상 미리보기 이미지를 문서와 함께 저장, 미리보기 크기]**)를 클릭하여 더 큰 렌디션을 포함할 수 있습니다.

## 이미지 형식 {#image-formats}

| 파일 포맷 | 썸네일 생성 | 메타데이터 추출 | 너비/높이 | 자르기 |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | ✓ | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| RGB | ✓ | ✓ | ✓ | ✓ |
| RGBA | ✓ | ✓ | ✓ | ✓ |
| SGI™ | ✓ | ✓ | ✓ | ✓ |
| SVG | ✓ | - | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | - |
| 웹P | ✓ | ✓ | ✓ | ✓ |

## 3D 형식 {#support-3d-formats}

지원되는 3D 형식은 다음과 같습니다.

참조: [Dynamic Media에서 3D 자산 작업](/help/assets/dynamic-media/assets-3d.md).

| 형식 | 스토리지 | 버전 관리 | 워크플로 | 게시 | 액세스 제어 | 썸네일 미리보기 | 3D 미리 보기 | Dynamic Media 게재 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | - | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| FBX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| 3DS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| SBSAR | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |

## [!DNL Camera Raw] 형식 {#camera-raw-formats}

| 파일 포맷 | 썸네일 생성 | 메타데이터 추출 | 너비/높이 |
| ----------- | -------------------- | ------------------- | ------------ |
| 3FR | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ |
| 원시 | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ |

## 문서 형식 {#document-formats}

에셋 관리 기능에 대해 지원되는 문서 형식은 다음과 같습니다.

| 파일 포맷 | 썸네일 생성 | 전체 텍스트 추출 | 너비/높이 | 메타데이터 관리 | [연결된 자산](use-assets-across-connected-assets-instances.md) | 전체 문서 미리 보기 |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |--------|
| DOC | - | - | - | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | ✓ | - | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ | - |
| ODF | ✓ | ✓ | ✓ | - | - | - |
| ODM | ✓ | ✓ | ✓ | - | - | - |
| ODP | ✓ | ✓ | ✓ | - | - | - |
| ODS | ✓ | ✓ | ✓ | - | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| OFG | ✓ | ✓ | ✓ | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PS | - | - | ✓ | - | - | - |
| RTF | - | ✓ | - | ✓ | ✓ | ✓ |
| TXT | ✓ | ✓ | - | ✓ | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | - | ✓ | - | - | - | - |

## 비디오 형식 {#video-formats}

| 파일 포맷 | 썸네일 생성 | 메타데이터 추출 | 너비/높이 | 미리보기 |
| ----------- | -------------------- | ------------------- | ------------ | ------- |
| 3G2 | - | ✓ | - | - |
| 3GP | - | ✓ | - | - |
| AVI | ✓ | ✓ | ✓ | ✓ |
| DIVX | ✓ | - | ✓ | ✓ |
| F4V | ✓ | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ | ✓ |
| M2T | ✓ | - | ✓ | ✓ |
| M2TS | ✓ | - | ✓ | ✓ |
| M2V | ✓ | - | ✓ | ✓ |
| M4V | ✓ | ✓ | ✓ | ✓ |
| MKV | ✓ | - | ✓ | ✓ |
| MOV | ✓ | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ | ✓ |
| 마일 | ✓ | ✓ | ✓ | ✓ |
| MTS | ✓ | - | ✓ | ✓ |
| MXF | ✓ | - | ✓ | ✓ |
| OGV | ✓ | - | ✓ | ✓ |
| QT | ✓ | - | ✓ | ✓ |
| R3D | - | ✓ | ✓ | ✓ |
| SWF | ✓ | - | ✓ | ✓ |
| WebM | ✓ | - | ✓ | ✓ |
| WMV | ✓ | ✓ | ✓ | ✓ |

## 오디오 형식 {#audio-formats}

[!DNL Assets] as a [!DNL Cloud Service] 는 AIF, ASF, M4A, MP3, WAV 및 WMA 오디오 형식에 대한 XMP 메타데이터 추출 지원을 제공합니다.

## 오디오 및 비디오 트랜스크립션에 대해 지원되는 입력 형식 {#audio-video-transcription-formats}

* FLV (H.264 및 AAC 코덱 포함) (.flv)
* MXF(.mxf)
* MPEG2-PS, MPEG2-TS, 3GP(.ts, .ps, .3gp, .3gpp, .mpg)
* Windows Media Video(WMV)/ASF(.wmv, .asf)
* AVI(압축되지 않은 8비트/10비트)(.avi)
* MP4(.mp4, .m4a, .m4v)
* Microsoft® 디지털 비디오 녹화(DVR-MS) (.dvr-ms)
* Matroska/WebM(.mkv)
* WAVE/WAV(.wav)
* QuickTime(.mov)

## 팁 및 제한 사항 {#limitations-and-tips}

* 현재 메타데이터 추출을 위한 파일 크기 제한은 약 15GB입니다. 큰 에셋을 업로드할 때 메타데이터 추출 작업이 실패하는 경우가 있습니다.

## Dynamic Media - 코드 변환에 지원되는 입력 비디오 형식 {#video-dynamic-media-transcoding}

| 비디오 파일 확장명 | 컨테이너 | 권장 비디오 코덱 | 지원되지 않는 비디오 코덱 |
| --- | --- | --- | --- |
| AVI | A/V 인터리브 | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3(IV30), MJPEG, Microsoft® 비디오 1(MS-CRAM) |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF(벡터 애니메이션 파일) |
| M4V | Apple iTunes | H264/AVC | − |
| MKV | 마트로스카 | H264/AVC | − |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple 애니메이션 |
| MP4 | - | H264/AVC(모든 프로필) | − |
| MPG, VOB, M2V, MP2 | - | - | − |
| MXF ‡ | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | − |
| OGV, OGG | OGG | Theora, VP3, Dirac | − |
| WebM | WebM | Google V8 | − |
| WMV | 윈도 미디어 | WMV3(v9), WMV2(v8), WMV1(v7), GoToMeeting(G2M2, G2M3, G2M4) | Microsoft® 화면(MSS2), Microsoft® 사진 스토리(WVP2) |

‡ 이 비디오 형식은 아직 Dynamic Media의 대화형 비디오와 함께 사용하거나 Experience Manager Assets의 주석과 함께 사용할 수 없습니다.

## Dynamic Media - 지원되는 문서 형식 {#document-support-dynamic-media}

| 형식 | 업로드 (입력 형식) | 이미지 사전 설정 만들기(출력 형식) | 동적 렌디션 미리 보기 | 동적 렌디션 전달 | 동적 렌디션 다운로드 |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| INDD | ✓ | - | - | - | - |
| PDF(아래 참고 참조) | ✓ | ✓ | ✓ | ✓ | ✓ |

>[!NOTE]
>
>보안 PDF의 경우 업로드만 지원됩니다.

## Dynamic Media - 지원되는 래스터 이미지 형식 {#image-support-dynamic-media}

| 형식 | 업로드 (입력 형식) | 이미지 사전 설정 만들기(출력 형식) | 동적 렌디션 미리 보기 | 동적 렌디션 전달 | 동적 렌디션 다운로드 | 이 형식을 지원하는 형식 설정 |
|---|:---:|:---:|:---:|:---:|:---:| --- |
| AVIF | − | − | − | ✓ | − | − |
| BMP | ✓ | − | − | − | − | [이미지](/help/assets/dynamic-media/image-sets.md), [혼합 미디어](/help/assets/dynamic-media/mixed-media-sets.md), 및 [회전](/help/assets/dynamic-media/spin-sets.md) |
| [EPS](/help/assets/dynamic-media/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | − |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ | − |
| HEIC | − | − | − | ✓ | − | − |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | [이미지](/help/assets/dynamic-media/image-sets.md), [혼합 미디어](/help/assets/dynamic-media/mixed-media-sets.md), 및 [회전](/help/assets/dynamic-media/spin-sets.md) |
| PICT | ✓ | − | − | − | − | − |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | [이미지](/help/assets/dynamic-media/image-sets.md), [혼합 미디어](/help/assets/dynamic-media/mixed-media-sets.md), 및 [회전](/help/assets/dynamic-media/spin-sets.md) |
| PSD ‡ | ✓ | − | − | − | − | − |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ | [이미지](/help/assets/dynamic-media/image-sets.md), [혼합 미디어](/help/assets/dynamic-media/mixed-media-sets.md), 및 [회전](/help/assets/dynamic-media/spin-sets.md) |
| WEBP | − | − | − | ✓ | − | − |
<!-- AVIF, HEIC, and WebP added to table above on March 4, 2024 based on CQDOC-21294 -->

‡ 병합된 이미지가 PSD 파일에서 추출됩니다. 에서 생성된 이미지입니다. [!DNL Adobe Photoshop] 및 가 PSD 파일에 포함됩니다. 설정에 따라 병합된 이미지가 실제 이미지가 될 수도 있고 그렇지 않을 수도 있습니다.

## Dynamic Media - 지원되지 않는 래스터 이미지 형식 {#unsupported-raster-image-formats-dm}

래스터 이미지 파일 형식의 다음과 같은 하위 유형 *아님* 지원 위치 [!DNL Dynamic Media]:

* IDAT 청크 크기가 100MB보다 큰 PNG 파일입니다.
* PSB 파일
* CMYK, RGB, 회색 음영 또는 비트맵 이외의 색상 공간이 있는 PSD 파일은 지원되지 않습니다. DuoTone, Lab 및 Indexed 색상 공간은 지원되지 않습니다.
* 비트 깊이가 16보다 큰 PSD 파일입니다.
* 부동 소수점 데이터가 있는 TIFF 파일입니다.
* Lab 색상 공간이 있는 TIFF 파일입니다.

## Dynamic Media - 지원되는 3D 파일 형식 {#support-3d-formats-dynamic-media}

참조: [지원되는 3D 형식](/help/assets/file-format-support.md#support-3d-formats)

| 3D 파일 확장명 | 파일 포맷 | MIME 유형 | 메모 |
|---|---|---|---|
| GLB | 이진 GL 전송 | model/gltf-binary | 재료 및 텍스처를 단일 자산으로 포함합니다. |
| OBJ | WaveFront 3D 개체 파일 | application/x-tgif | |
| STL | 스테레오리소그래피 | application/vnd.ms-pki.stl | |
| USDZ | 범용 장면 설명 Zip 아카이브 | model/vnd.usdz+zip | *수집 및 썸네일 생성 지원. 3D 미리보기는 아직 지원되지 않습니다.* USDZ는 Safari 또는 iOS에서 기본적으로 볼 수 있는 3D 형식입니다. |

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
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

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스를 사용한 자산 처리](asset-microservices-overview.md)
>* [텍스트 기반 에셋의 스마트 태그 지정에 지원되는 파일 형식](/help/assets/smart-tags.md#smart-tags-supported-file-formats)
