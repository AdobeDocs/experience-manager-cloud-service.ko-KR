---
title: Experience Manager Assets에서 클라우드 서비스로 지원되는 파일 포맷 및 MIME 유형
description: Experience Manager Assets에서 클라우드 서비스로 지원되는 파일 포맷 및 MIME 유형
contentOwner: AG
translation-type: tm+mt
source-git-commit: 776b089a322cc4f86fdcb9ddf1c3cc207fc85d39

---


# 자산 지원 파일 포맷 {#supported-file-formats}

Adobe Experience Manager as a Cloud Service는 포맷에 상관없이 모든 바이너리 파일에 대해 저장, 메타데이터 온라인 관리, 버전 관리, 업로드 및 다운로드 등 기본적인 컨텐츠 관리 기능을 지원합니다. 또한 이미지, Adobe 독점적, 문서 및 비디오와 같이 일반적으로 사용되는 파일 포맷의 경우 미리 보기 및 표현물을 생성하고 전체 텍스트 인덱싱을 위한 메타데이터와 텍스트를 추출할 수 있도록 확장된 지원을 제공합니다. 이러한 확장 지원은 [에셋 마이크로서비스를](asset-microservices-configure-and-use.md)통해 제공됩니다.

확장된 지원을 통해 파일 포맷의 주요 특징은 다음과 같습니다.

* Adobe [Photoshop, InDesign, Illustrator, XD, Dimension, Acrobat / PDF 등 Adobe 애플리케이션 및 서비스에서 제작된 주요 Adobe 파일 포맷입니다](#adobe-formats) .
* 주요 [이미징 파일 포맷](#image-formats)
* [Canon, Nikon, Fujifilm, Olympus 및 기타 제조업체(Adobe Camera Raw 제공)를 비롯한 다양한 카메라를 위한 Camera Raw 파일 포맷](#camera-raw-formats)
* Microsoft Office(Word, Excel, [PowerPoint](#document-formats)) 및 [Open Document](#microsoft-office-formats) 형식 [등 일반적인 문서 형식](#opendocument-formats)
* 다양한 [비디오](#video-formats) 및 [오디오](#audio-formats) 포맷

## 범례 - 자세한 지원 정보 {#legend-for-detailed-support-information}

다음 범례에서는 기능에 대한 지원 수준에 대해 설명합니다.

| 지원 수준 | 설명 |
| ------------------------------------------------------------ | --------------------------- |
| ✓ | 지원됨 |
| * | 표 아래의 참고 사항 보기 |
| - | 해당 사항 없음 |

지원 테이블 열은 다음 정보를 제공합니다.

| 열 | 설명 |
| ------------ | --------------------------------------------------------------- |
| 형식 | 자산 원본 바이너리의 파일 형식(파일 확장명) |
| GIF | 변환 생성을 위한 GIF 형식 |
| JPEG | 변환 생성을 위한 JPEG 포맷 |
| PNG | 변환 생성을 위한 PNG 형식 |
| XMP | 원본 바이너리에서 메타데이터 추출 |
| TXT | 문서에서 색인화를 위한 텍스트 추출 |
| 너비/높이 | 변환의 폭 및 높이 정의 지원(픽셀) |

<!-- Adding this checkmark icon ✓ does not look good in table. The icon's shade and size has to be toned down for good readability and less clutter.
@gklebus: I suggest using a checkmark character, either U+2713 ✓ CHECK MARK or U+2714 ✔ HEAVY CHECK MARK
-->

## Adobe 포맷 {#adobe-formats}

| 파일 포맷 | GIF | JPEG | PNG | TXT | XMP | 너비/높이 |
| ----------- | --- | ---- | --- | --- | --- | ------------ |
| AI | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| 콜라주 | - | - | - | - | ✓ | - |
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| 아이디어 | - | - | - | - | ✓ | - |
| INDD | ✓ | ✓ | ✓ | - | ✓ | ✓* |
| INDT | - | - | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | - | - | ✓ | - |
| PSB | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| PSD | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| XD | ✓ | ✓ | ✓ | - | ✓ | ✓ |

\* INDD(InDesign 파일)의 경우 INDD 파일에 임베드된 미리 보기에 따라 변환 크기가 결정됩니다. InDesign에서 기본 설정(**[!UICONTROL [환경 설정] > [파일 처리] > [문서와 함께 미리 보기 이미지 항상 저장], [미리 보기 크기]**])을 구성하여 더 큰 변환을 포함할 수 있습니다.

## 이미지 포맷 {#image-formats}

| 파일 포맷 | GIF | JPEG | PNG | XMP | 너비/높이 |
| ----------- | --- | ---- | --- | --- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |


## Camera RAW 포맷 {#camera-raw-formats}

| 파일 포맷 | GIF | JPEG | PNG | XMP | 너비/높이 |
| ----------- | --- | ---- | --- | --- | ------------ |
| 3FR | ✓ | ✓ | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ | ✓ | ✓ |

## 문서 포맷 {#document-formats}

| 파일 포맷 | TXT | XMP |
| ----------- | --- | --- |
| EPUB | ✓ | - |
| HTML | ✓ | - |
| PS | - | ✓ |
| RTF | ✓ | - |
| 텍스트 | ✓ | - |
| XML | ✓ | - |

## Microsoft Office 포맷 {#microsoft-office-formats}

| 파일 포맷 | GIF | JPEG | PNG | 텍스트 | 너비/높이 |
| ----------- | --- | ---- | --- | ---- | ------------ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |

## OpenDocument 포맷 {#opendocument-formats}

| 파일 포맷 | GIF | JPEG | PNG | 텍스트 | 높이 |
| ----------- | --- | ---- | --- | ---- | ------ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ |
| OFG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |

## 비디오 포맷 {#video-formats}

| 파일 포맷 | GIF | JPEG | PNG | XMP | 너비/높이 |
| ----------- | --- | ---- | --- | --- | ------------ |
| 3G2 | - | - | - | ✓ | - |
| 3GP | - | - | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ | ✓ | ✓ |
| DIVX | ✓ | ✓ | ✓ |  | ✓ |
| F4V | ✓ | ✓ | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ | ✓ | ✓ |
| M2T | ✓ | ✓ | ✓ | - | ✓ |
| M2TS | ✓ | ✓ | ✓ | - | ✓ |
| M2V | ✓ | ✓ | ✓ | - | ✓ |
| M4V | ✓ | ✓ | ✓ | ✓ | ✓ |
| MKV | ✓ | ✓ | ✓ | - | ✓ |
| MOV | ✓ | ✓ | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ | ✓ | ✓ |
| MTS | ✓ | ✓ | ✓ | - | ✓ |
| OGV | ✓ | ✓ | ✓ | - | ✓ |
| QT | ✓ | ✓ | ✓ | - | ✓ |
| R3D | ✓ | ✓ | ✓ | - | ✓ |
| SWF | ✓ | ✓ | ✓ | - | ✓ |
| WEBM | ✓ | ✓ | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ | ✓ | ✓ |

## 오디오 포맷 {#audio-formats}

클라우드 서비스로서의 에셋은 다음과 같은 오디오 포맷에 대한 XMP 지원을 제공합니다.AIF, ASF, M4A, MP3, WAV 및 WMA.

<!-- TBD: Some items from https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#SupportedinputvideoformatsforDynamicMediatranscoding may be applicable.

Bring more parity with https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#SupportedMIMEtypes.
https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#Supportedmultimediaformats
-->

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스를 사용한 자산 처리](asset-microservices-overview.md)

