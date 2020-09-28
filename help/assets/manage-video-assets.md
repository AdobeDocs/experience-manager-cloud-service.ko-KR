---
title: 비디오 자산 관리
description: 비디오 에셋을 업로드, 미리 보기, 주석 달기 및 게시할 수 있습니다 [!DNL Adobe Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 1%

---


# 비디오 자산 관리 {#manage-video-assets}

비디오 포맷은 조직의 디지털 자산에 중요한 역할을 합니다. [!DNL Adobe Experience Manager] 비디오 에셋 제작 후 전체 라이프사이클을 관리할 수 있는 완벽한 솔루션과 기능을 제공합니다.

비디오 에셋을 관리하고 편집하는 방법을 살펴보십시오 [!DNL Adobe Experience Manager Assets]. 비디오 인코딩 및 트랜스코딩(예: FFmpeg 트랜스코딩)은 처리 프로필 및 [!DNL Dynamic Media] 통합을 사용하여 수행할 수 있습니다. 라이선스가 [!DNL Dynamic Media] [!DNL Experience Manager] 없으면 FFmpeg를 사용한 트랜스코딩, 지원되는 파일 포맷의 미리 보기 축소판 추출, 브라우저에서 직접 재생되는 데 지원되는 포맷을 위한 사용자 인터페이스에서 미리 보기 등 비디오에 대한 기본 지원을 제공합니다.

## 비디오 에셋 업로드 및 미리 보기 {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] 에서는 확장 MP4를 사용하여 비디오 자산에 대한 미리 보기를 생성합니다. 사용자 인터페이스에서 변환을 미리 볼 수 [!DNL Assets] 있습니다.

1. 디지털 자산 폴더 또는 하위 폴더에서 디지털 자산을 추가할 위치로 이동합니다.
1. 자산을 업로드하려면 도구 모음에서 **[!UICONTROL 만들기를]** 클릭하고 **[!UICONTROL 파일을 선택합니다]**. 또는 사용자 인터페이스에서 파일을 드래그합니다. 자세한 내용은 [자산](manage-digital-assets.md#uploading-assets) 업로드를 참조하십시오.
1. 카드 보기에서 비디오를 미리 보려면 비디오 자산에서 **[!UICONTROL 재생]** 옵션 ![](assets/do-not-localize/play.png) 옵션을 클릭합니다. 카드 보기에서만 비디오를 일시 중지하거나 재생할 수 있습니다. [ [!UICONTROL 재생] ] 및 [!UICONTROL [일시 정지] ] 옵션은 목록 보기에서 사용할 수 없습니다.
1. 자산 세부 사항 페이지에서 비디오를 미리 보려면 카드에서 **[!UICONTROL 편집을]** 선택합니다. 비디오가 브라우저의 기본 비디오 플레이어에서 재생됩니다. 비디오를 재생, 일시 정지, 볼륨 조절 및 전체 화면으로 확대/축소할 수 있습니다.

## 비디오 에셋 게시 {#publish-video-assets}

게시 후 웹 페이지에 비디오 자산을 URL로 포함하거나 자산을 직접 포함할 수 있습니다. 자세한 내용은 Dynamic Media 자산 [게시를 참조하십시오](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## 처리 프로필을 사용하여 트랜스코딩 {#transcode-video}

[!DNL Experience Manager] 를 Cloud Service으로 사용하면 처리 프로필을 사용하여 MP4 비디오 파일을 기본적인 트랜스코딩할 수 있습니다. 이 기능을 사용하면 업로드할 뿐만 아니라 MP4 비디오 파일을 미리 보고 크기를 조절할 수 있습니다.

![Experience Manager에서 비디오 트랜스코딩용 처리 프로필 만들기](assets/video-processing-profile-for-mp4.png)

*그림:비디오 트랜스코딩에 대한 처리 프로필[!DNL Experience Manager].*

너비만 또는 높이만 제공하고 다른 필드를 비워 두면 변환이 종횡비를 유지합니다. 현재 코드 변환에는 h264 코덱만 사용할 수 있습니다.

처리 프로필을 사용하여 자산을 처리하려면 폴더에 프로필을 추가하십시오. 처리 [프로필을 사용하여 자산 처리를 참조하십시오](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## 비디오 자산에 주석 달기 {#annotate-video-assets}

1. 콘솔에서 자산 카드 [!DNL Assets] 의 **[!UICONTROL 편집을]** 선택하여 자산 세부 사항 페이지를 표시합니다.
1. 비디오를 재생하려면 미리 **[!UICONTROL 보기를 클릭합니다]**.
1. 비디오에 주석을 추가하려면 [주석]을 **[!UICONTROL 클릭합니다]**. 비디오의 특정 시간(프레임)에 주석이 추가됩니다. 주석을 달 때 캔버스에서 드로잉하고 드로잉에 주석을 추가할 수 있습니다. 주석이 자동으로 저장됩니다. 주석 마법사를 종료하려면 **[!UICONTROL 닫기를 클릭합니다]**.
1. 비디오의 특정 지점을 찾아서 **텍스트** 필드(초)에서 시간을 지정하고 **이동을 클릭합니다**. 예를 들어 비디오 처음 20초를 건너뛰려면 텍스트 필드에 20을 입력합니다.
1. 타임라인에서 보려면 주석을 클릭합니다. 타임라인에서 주석을 삭제하려면 삭제 **[!UICONTROL 를 클릭합니다]**.

## 모범 사례 및 제한 사항 {#tips-limitations}

* Dynamic Media 라이선스가 없으면 처리 프로필을 사용하여 MP4 파일만 처리할 수 있습니다.
* For basic transcoding using

>[!MORELIKETHIS]
>
>* [다이내믹 미디어 비디오 설명서](/help/assets/dynamic-media/video.md).
>* [처리 프로필의 사용, 유형 및 구성에 대해 자세히 알아보십시오](/help/assets/asset-microservices-configure-and-use.md).

