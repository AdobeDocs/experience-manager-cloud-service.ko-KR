---
title: 지원되는 파일 포맷 및 MIME 유형
description: 파일 형식 및 MIME 형식은 Cloud Service으로 [!DNL Experience Manager Assets] 에서 지원합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7e5ea5ccf0110d1fb55449c9c1933aff6aba0065
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 8%

---


# [!DNL Assets] 지원되는 파일 포맷  {#supported-file-formats}

[!DNL Adobe Experience Manager] cloud service은 포맷과 상관없이 모든 바이너리 파일에 대해 저장, 온라인 메타데이터 관리, 버전 관리, 업로드 및 다운로드 등의 기본적인 컨텐츠 관리 기능을 지원합니다. [!DNL Adobe Experience Manager Assets] 다양한 파일 포맷을 지원하고 각 제품 기능은 서로 다른 포맷을 지원합니다.

또한 [!DNL Experience Manager Assets]은 미리 보기 및 표현물을 생성하고 전체 텍스트 인덱싱을 위한 메타데이터와 텍스트를 추출하는 확장된 지원을 제공합니다. 이 확장 지원은 [asset microservices](asset-microservices-configure-and-use.md)를 사용하여 제공됩니다.

자산 마이크로서비스를 사용하는 자산 전환의 주요 특징은 다음과 같습니다.

* ](#adobe-formats), [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD] 및 [!DNL Adobe Dimension] 또는 PDF를 비롯한 Adobe 응용 프로그램 및 서비스에서 생성된 Adobe 파일 형식[을 키 지정합니다.[!DNL Adobe Acrobat]
* [이미징 파일 포맷](#image-formats)을 키웁니다.
* [Canon, Camera Raw Nikon, Fujifilm, Olympus 및 기타 제조업체(Adobe Camera Raw 제공)를 비롯한 다양한 카메라의 파일 포맷 ](#camera-raw-formats) 
* Microsoft Office 및 Open Document 형식을 포함한 일반적인 [문서 형식](#document-formats)입니다.
* 광범위한 [video](#video-formats) 및 [audio](#audio-formats) 형식.

다음 범례에서는 지원 수준을 설명합니다.

| 지원 수준 | 설명 |
| ------------- | --------------------------- |
| ✓ | 지원됨 |
| * | 표 아래의 참고 사항 보기 |
| - | 해당 사항 없음 |

## Adobe 형식 {#adobe-formats}

| 파일 포맷 | 축소판 생성 | 전체 텍스트 추출 | 메타데이터 추출 | 너비/높이 |
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

\* INDD(A0/> 파일)의 경우 INDD 파일에 포함된 미리 보기에 따라 변환 크기가 결정됩니다. [!DNL Adobe InDesign] [!DNL InDesign](**[!UICONTROL 환경 설정 > 파일 처리 > 항상 문서와 함께 미리 보기 이미지 저장, 미리 보기 크기]**)에서 기본 설정을 구성하여 더 큰 변환을 포함합니다.

## 이미지 형식 {#image-formats}

| 파일 포맷 | 축소판 생성 | 메타데이터 추출 | 너비/높이 | 자르기 |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | - | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | - |
| SVG | ✓ | - | ✓ | ✓ |
| SGI | ✓ | ✓ | ✓ | ✓ |
| RGB | ✓ | ✓ | ✓ | ✓ |
| RGBA | ✓ | ✓ | ✓ | ✓ |

## [!DNL Dynamic Media] {#image-support-dynamic-media}의 이미지 형식

| 형식 | 업로드(입력 형식) | 이미지 사전 설정 만들기(출력 형식) | 동적 변환 미리 보기 | 동적 변환 전달 | 동적 변환 다운로드 |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | - | - | - | - |
| PSD   ‡ | ✓ | - | - | - | - |
| EPS | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ | - | - | - | - |

병합된 ‡ 이미지는 PSD 파일에서 추출됩니다. 이 이미지는 [!DNL Adobe Photoshop]에 의해 생성되며 PSD 파일에 포함됩니다. 설정에 따라 병합된 이미지가 실제 이미지이거나 아닐 수 있습니다.

[!DNL Dynamic Media]에서 지원되지 않는 다음 래스터 이미지 파일 형식의 하위 형식입니다.

* IDAT 청크 크기가 100MB보다 큰 PNG 파일
* PSB 파일.
* CMYK, RGB, 회색 음영 또는 비트맵 이외의 색상 공간이 있는 PSD 파일은 지원되지 않습니다. DuoTone, Lab 및 Indexed 색상 공간은 지원되지 않습니다.
* 16보다 비트 심도가 높은 PSD 파일
* 부동 소수점 데이터가 있는 TIFF 파일
* Lab 색상 공간이 있는 TIFF 파일

## 3D 형식 {#support-3d-formats}

다음 3D 형식 목록이 지원됩니다.

[다이내믹 미디어에서 3D 자산을 사용한 작업을 참조하십시오.](/help/assets/dynamic-media/assets-3d.md)

| 형식 | 저장 용량 | 버전 관리 | 워크플로우 | 게시 | 액세스 제어 | 축소판 미리 보기 | 3D 미리 보기 | 다이내믹 미디어 전달 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | - | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | - | - | ✓ |

## [!DNL Camera RAW] formats  {#camera-raw-formats}

| 파일 포맷 | 축소판 생성 | 메타데이터 추출 | 너비/높이 |
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
| RAW | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ |

## 문서 형식 {#document-formats}

자산 관리 기능에 지원되는 문서 형식은 다음과 같습니다.

| 파일 포맷 | 축소판 생성 | 전체 텍스트 추출 | 너비/높이 | 메타데이터 관리 | [연결된 자산](use-assets-across-connected-assets-instances.md) |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOC | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | - | - |
| OFG | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | ✓ | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ |
| PS | - | - | ✓ | - | - |
| RTF | - | ✓ | - | ✓ | ✓ |
| TXT | - | ✓ | - | ✓ | ✓ |
| XML | - | ✓ | - | - | - |

## [!DNL Dynamic Media] {#document-support-dynamic-media}의 문서 형식

| 형식 | 업로드(입력 형식) | 이미지 사전 설정 만들기(출력 형식) | 동적 변환 미리 보기 | 동적 변환 전달 | 동적 변환 다운로드 |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| INDD | ✓ | - | - | - | - |

## 비디오 형식 {#video-formats}

| 파일 포맷 | 축소판 생성 | 메타데이터 추출 | 너비/높이 |
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
| MOV | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ |
| MTS | ✓ | - | ✓ |
| OGV | ✓ | - | ✓ |
| QT | ✓ | - | ✓ |
| R3D | - | ✓ | ✓ |
| SWF | ✓ | - | ✓ |
| WebM | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ |

## {#video-dynamic-media-transcoding} 트랜스코딩용 [!DNL Dynamic Media]의 비디오 포맷

| 비디오 파일 확장자 | 컨테이너 | 권장 비디오 코덱스 | 지원되지 않는 비디오 코덱입니다. |
|------------------------|--------------------|--------|-------|
| MP4 | MPEG-4 | H264/AVC(모든 프로필) | - |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV(DV25), Apple PhotoJPEG, Sorenson, Avid DNHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF(벡터 애니메이션 파일) |
| WMV | Windows Media 9 | WMV3(v9), WMV2(v8), WMV1(v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen(MSS2), Microsoft Photo Story(WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | - |
| M4V | Apple iTunes | H264/AVC | - |
| AVI | A/V 인터리브 | XVID, DIVX, HDV, MiniDV(DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3(IV30), MJPEG, Microsoft Video 1(MS-CRAM) |
| WebM | WebM | Google VP8 | - |
| OGV, OGG | Ogg | Theora, VP3, Dirac | - |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | - |
| MTS | AVCHD | H264/AVC | - |
| MKV | 마트로스카 | H264/AVC | - |
| R3D, RM | Red Raw 비디오 | MJPEG 2000 | - |
| RAM, RM | RealVideo | 지원되지 않음 | Real G2(RV20), Real 8(RV30), Real 10(RV40) |
| FLAC | 기본 Flac | 무손실 오디오 코덱입니다. | - |
| MJ2 | 모션 JPEG 2000 | 모션 JPEG 2000 코덱입니다. | - |

## 오디오 형식 {#audio-formats}

[!DNL Assets] cloud service은 AIF, ASF, M4A, MP3, WAV 및 WMA 오디오 포맷에 대한 XMP 메타데이터 추출 지원을 제공합니다.

>[!MORELIKETHIS]
>
>* [에셋 마이크로서비스를 사용한 에셋 처리](asset-microservices-overview.md)

