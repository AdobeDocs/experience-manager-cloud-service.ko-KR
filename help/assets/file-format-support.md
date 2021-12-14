---
title: 지원되는 파일 형식 및 MIME 유형
description: 에서 지원하는 파일 형식 및 MIME 유형 [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management,Renditions
role: User,Admin
exl-id: e848aa77-7829-4adc-8b88-0279791a4525
source-git-commit: ba752888601413dd4725a7a137f8b468b92ad5c7
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 8%

---

# [!DNL Assets] 지원되는 파일 형식 {#supported-file-formats}

[!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 포맷과 상관없이 모든 바이너리 파일에 대해 저장, 메타데이터 온라인 관리, 버전 관리, 업로드 및 다운로드 등의 기본적인 컨텐츠 관리 기능을 지원합니다. [!DNL Adobe Experience Manager Assets] 는 다양한 파일 형식을 지원하며 각 제품 기능은 다양한 형식에 대한 다양한 지원을 제공합니다.

게다가, [!DNL Experience Manager Assets] 미리 보기 및 변환을 생성하고 전체 텍스트 색인을 위한 메타데이터와 텍스트를 추출할 수 있도록 확장된 지원을 제공합니다. 이 확장 지원은 [자산 마이크로서비스](asset-microservices-configure-and-use.md).

자산 마이크로서비스를 사용한 자산 전환의 주요 사항은 다음과 같습니다.

* 키 [Adobe 파일 형식](#adobe-formats) 다음을 포함한 Adobe 애플리케이션 및 서비스에서 작성 [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension], 및 [!DNL Adobe Acrobat] 또는 PDF.
* 키 [이미지 파일 형식](#image-formats).
* [Camera Raw 파일 형식](#camera-raw-formats) 캐논, 니콘, 후지필름, 올림푸스 등 다양한 카메라 제조 업체(Adobe Camera Raw 제공)에 대한 것이다.
* 공통 [문서 형식](#document-formats)( Microsoft Office 및 Open Document 형식 포함)
* Wide range of [video](#video-formats) and [audio](#audio-formats) formats.

다음 범례에서는 각 형식에 대한 지원 수준을 설명합니다.

| 지원 수준 | 설명 |
| ------------- | --------------------------- |
| ✓ | 지원됨 |
| * | 표 아래의 참고 설명을 참조하십시오 |
| - | 해당 사항 없음 |

## Adobe 형식 {#adobe-formats}

| 파일 형식 | 축소판 생성 | 전체 텍스트 추출 | 메타데이터 추출 | 너비/높이 |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | - | ✓ | ✓ |
| 콜라주 | - | - | ✓ | - |
| DN | ✓ | - | ✓ | ✓ |
| 아이디어 | - | - | ✓ | - |
| INDD | ✓ | - | ✓ | ✓ * |
| INDT | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | ✓ | - |
| PSB | ✓ | - | ✓ | ✓ |
| PSD | ✓ | - | ✓ | ✓ |
| XD | ✓ | - | ✓ | ✓ |

\* [!DNL Adobe InDesign] 파일(INDD), 표현물의 크기는 INDD 파일에 포함된 미리 보기에 의해 결정됩니다. 에서 환경 설정을 구성합니다. [!DNL InDesign] (**[!UICONTROL 환경 설정 > 파일 처리 > 항상 문서를 사용하여 미리 보기 이미지 저장, 미리 보기 크기]**)을 클릭하여 더 큰 렌디션을 포함합니다.

## 이미지 형식 {#image-formats}

| 파일 형식 | 축소판 생성 | 메타데이터 추출 | 너비/높이 | 자르기 |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | - | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| RGB | ✓ | ✓ | ✓ | ✓ |
| RGBA | ✓ | ✓ | ✓ | ✓ |
| SGI | ✓ | ✓ | ✓ | ✓ |
| SVG | ✓ | - | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | - |

## 의 이미지 형식 [!DNL Dynamic Media] {#image-support-dynamic-media}

| 형식 | 업로드(입력 형식) | 이미지 사전 설정 만들기(출력 형식) | 동적 표현물 미리 보기 | 동적 표현물 전달 | 동적 표현물 다운로드 |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| BMP | ✓ | - | - | - | - |
| EPS | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ | - | - | - | - |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PSD ‡ | ✓ | - | - | - | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |

병합된 ‡ 이미지가 PSD 파일에서 추출됩니다. 에서 생성한 이미지입니다. [!DNL Adobe Photoshop] 및 은 PSD 파일에 포함되어 있습니다. 설정에 따라 병합된 이미지가 실제 이미지이거나 아닐 수 있습니다.

에서 지원되지 않는 래스터 이미지 파일 형식의 다음 하위 유형 [!DNL Dynamic Media]:

* IDAT 청크 크기가 100MB보다 큰 PNG 파일.
* PSB 파일.
* CMYK, RGB, 회색 음영 또는 비트맵 이외의 색상 공간이 있는 PSD 파일은 지원되지 않습니다. DuoTone, Lab 및 Indexed 색상 공백은 지원되지 않습니다.
* 비트 깊이가 16보다 큰 PSD 파일.
* 부동 소수점 데이터가 있는 TIFF 파일입니다.
* Lab 색상 공간이 있는 TIFF 파일

## 3D 형식 {#support-3d-formats}

다음 3D 형식이 지원됩니다.

참조 - [Dynamic Media에서 3D 자산 작업](/help/assets/dynamic-media/assets-3d.md).

| 형식 | 저장 용량 | 버전 관리 | 워크플로 | 게시 | 액세스 제어 | 축소판 미리 보기 | 3D 미리 보기 | Dynamic Media 게재 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | - | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | - | - | ✓ |

## [!DNL Camera RAW] 포맷 {#camera-raw-formats}

| 파일 형식 | 축소판 생성 | 메타데이터 추출 | 너비/높이 |
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
| 오프 | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ |

## 문서 형식 {#document-formats}

자산 관리 기능에 대해 지원되는 문서 형식은 다음과 같습니다.

| 파일 형식 | 축소판 생성 | 전체 텍스트 추출 | 너비/높이 | 메타데이터 관리 | [연결된 자산](use-assets-across-connected-assets-instances.md) |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |
| DOC | - | - | - | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| ePub | - | ✓ | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |
| OFG | ✓ | ✓ | ✓ | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PS | - | - | ✓ | - | - |
| RTF | - | ✓ | - | ✓ | ✓ |
| TXT | ✓ | ✓ | - | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | - | ✓ | - | - | - |

## 문서 형식 [!DNL Dynamic Media] {#document-support-dynamic-media}

| 형식 | 업로드(입력 형식) | 이미지 사전 설정 만들기(출력 형식) | 동적 표현물 미리 보기 | 동적 표현물 전달 | 동적 표현물 다운로드 |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| INDD | ✓ | - | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |

## 비디오 형식 {#video-formats}

| 파일 형식 | 축소판 생성 | 메타데이터 추출 | 너비/높이 |
| ----------- | -------------------- | ------------------- | ------------ |
| 3G2 | - | ✓ | - |
| 3GP | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ |
| DIVX | ✓ | - | ✓ |
| F4V | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ |
| M2T | ✓ | - | ✓ |
| M2TS | ✓ | - | ✓ |
| M2V | ✓ | - | ✓ |
| M4V | ✓ | ✓ | ✓ |
| MKV | ✓ | - | ✓ |
| 이동 | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ |
| MTS | ✓ | - | ✓ |
| MXF | ✓ | - | ✓ |
| OGV | ✓ | - | ✓ |
| QT | ✓ | - | ✓ |
| R3D | - | ✓ | ✓ |
| SWF | ✓ | - | ✓ |
| WebM | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ |

## 의 비디오 형식 [!DNL Dynamic Media] 코드 변환 {#video-dynamic-media-transcoding}

| 비디오 파일 확장 | 컨테이너 | 권장 비디오 코덱스 | 지원되지 않는 비디오 코덱입니다 |
| --- | --- | --- | --- |
| AVI | A/V 인터리브 | XVID, DIVX, HDV, MiniDV(DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3(IV30), MJPEG, Microsoft 비디오 1(MS-CRAM) |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF(벡터 애니메이션 파일) |
| M4V | Apple iTunes | H264/AVC | - |
| MKV | 마트로스카 | H264/AVC | - |
| 이동, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV(DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| MP4 | MPEG-4 | H264/AVC(모든 프로필) | - |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | - |
| MXF ‡ | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | - |
| OGV, OGG | Ogg | Theora, VP3, Dirac | - |
| WebM | WebM | Google VP8 | - |
| WMV | Windows Media 9 | WMV3(v9), WMV2(v8), WMV1(v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft 화면(MSS2), Microsoft 사진 스토리(WVP2) |

이 ‡ 비디오 형식은 아직 Dynamic Media의 대화형 비디오에서 사용하거나 Experience Manager Assets의 주석에서 사용할 수 없습니다.

## 오디오 형식 {#audio-formats}

[!DNL Assets] 로서의 [!DNL Cloud Service] AIF, ASF, M4A, MP3, WAV 및 WMA 오디오 형식에 대한 XMP 메타데이터 추출 지원을 제공합니다.

## 오디오 및 비디오 변환에 지원되는 입력 형식 {#audio-video-transcription-formats}

* FLV(H.264 및 AAC 코덱이 있는 경우)(.flv)
* MXF(.mxf)
* MPEG2-PS, MPEG2-TS, 3GP(.ts, .ps, .3gp, .3gpp, .mpg)
* Windows Media 비디오(WMV)/ASF(.wmv, .asf)
* AVI(압축되지 않은 8비트/10비트)(.avi)
* MP4(.mp4, .m4a, .m4v)
* Microsoft 디지털 비디오 기록(DVR-MS)(.dvr-ms)
* Matroska/WebM(.mkv)
* 웨이브/WAV(.wav)
* QuickTime(.mov)

## 팁 및 제한 사항 {#limitations-and-tips}

* 현재 메타데이터 추출의 파일 크기 제한은 약 15GB입니다. 매우 큰 자산을 업로드할 때 메타데이터 추출 작업이 실패하는 경우가 있습니다.

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스를 사용한 자산 처리](asset-microservices-overview.md)
>* [텍스트 기반 자산의 스마트 태그 지정을 위해 지원되는 파일 형식](/help/assets/smart-tags.md#smart-tags-supported-file-formats)

