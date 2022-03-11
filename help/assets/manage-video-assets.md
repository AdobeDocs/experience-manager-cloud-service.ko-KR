---
title: 비디오 에셋 관리
description: 에서 비디오 자산 업로드, 미리 보기, 주석 달기 및 게시 [!DNL Adobe Experience Manager].
contentOwner: AG
feature: Asset Management,Publishing,Collaboration,Video
role: User
exl-id: 91edce4a-dfa0-4eca-aba7-d41ac907b81e
source-git-commit: 038dbc4b0febfa58f69e05f837760162210f8689
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 6%

---

# 비디오 에셋 관리 {#manage-video-assets}

비디오 형식은 조직의 디지털 자산에 중요한 부분입니다. [!DNL Adobe Experience Manager] 에서는 비디오 자산이 만들어진 후 비디오 자산의 전체 라이프사이클을 관리하기 위한 성숙한 오퍼링과 기능을 제공합니다.

에서 비디오 자산을 관리하고 편집하는 방법을 알아봅니다 [!DNL Adobe Experience Manager Assets]. 처리 프로필과 를 사용하여 비디오 인코딩과 코드 변환(예: FFmpeg 코드 변환)을 수행할 수 있습니다 [!DNL Dynamic Media] 통합. 제외 [!DNL Dynamic Media] 라이센스, [!DNL Experience Manager] 에서는 FFmpeg를 사용한 코드 변환, 지원되는 파일 형식에 대한 미리 보기 축소판 추출, 브라우저에서 직접 재생하도록 지원되는 형식에 대한 사용자 인터페이스에서 미리 보기 등과 같은 비디오에 대한 기본 지원을 제공합니다.

## 비디오 자산 업로드 및 미리 보기 {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] 에서는 확장 MP4를 사용하여 비디오 자산에 대한 미리 보기를 생성합니다. 에서 표현물을 미리 볼 수 있습니다 [!DNL Assets] 사용자 인터페이스.

1. 디지털 자산 폴더 또는 하위 폴더에서 디지털 자산을 추가할 위치로 이동합니다.
1. 자산을 업로드하려면 **[!UICONTROL 만들기]** 도구 모음에서 **[!UICONTROL 파일]**. 또는 사용자 인터페이스에서 파일을 드래그합니다. 자세한 내용은 [자산 업로드](manage-digital-assets.md#uploading-assets) 자세한 내용
1. 카드 보기에서 비디오를 미리 보려면 **[!UICONTROL 재생]** ![재생 옵션](assets/do-not-localize/play.png) 옵션 을 클릭합니다. 카드 보기에서만 비디오를 일시 중지하거나 재생할 수 있습니다. 다음 [!UICONTROL 재생] 및 [!UICONTROL 일시 정지] 목록 보기에서는 옵션을 사용할 수 없습니다.
1. 자산 세부 사항 페이지에서 비디오를 미리 보려면 을 선택합니다 **[!UICONTROL 편집]** 카드 위에 비디오는 브라우저의 기본 비디오 플레이어에서 재생됩니다. 비디오를 전체 화면으로 재생, 일시 정지, 볼륨 제어 및 확대/축소할 수 있습니다.

## 비디오 자산 게시 {#publish-video-assets}

게시 후 비디오 자산을 웹 페이지에 URL로 포함하거나 자산을 직접 포함할 수 있습니다. 자세한 내용은 [게시 [!DNL Dynamic Media] assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## 처리 프로필을 사용하여 코드 변환 {#transcode-video}

[!DNL Experience Manager] 로서의 [!DNL Cloud Service] 처리 프로필을 사용하여 MP4 비디오 파일의 기본 코드 변환을 수행할 수 있습니다. 기능을 사용하면 MP4 비디오 파일을 업로드하는 것뿐만 아니라 미리 보고 크기를 조정할 수 있습니다.

![에서 비디오 코드 변환에 대한 처리 프로필 만들기 [!DNL Experience Manager]](assets/video-processing-profile-for-mp4.png)

*그림: 비디오 코드 변환용 처리 프로필 [!DNL Experience Manager].*

너비만 또는 높이만 제공하고 다른 필드를 비워 두면 변환은 종횡비를 유지합니다. H.264 비디오 코덱은 코드 변환에 사용할 수 있습니다.

처리 프로필을 사용하여 자산을 처리하려면 폴더에 프로필을 추가합니다. 자세한 내용은 [처리 프로필을 사용하여 자산 처리](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## 비디오 자산에 주석 달기 {#annotate-video-assets}

비디오 자산에 주석을 추가할 수 있습니다. 비디오에 주석을 추가하는 동안 플레이어는 프레임에 주석을 달 수 있도록 일시 중지합니다. 자세한 내용은 [비디오 자산 관리](manage-video-assets.md).

>[!NOTE]
>
>MXF 비디오 형식은 아직 비디오 자산 주석에서 지원되지 않습니다.

1. 에서 [!DNL Assets] 콘솔, 선택 **[!UICONTROL 편집]** 자산 카드의 자산 세부 사항 페이지를 표시합니다.
1. 비디오를 재생하려면 **[!UICONTROL 미리 보기]**.
1. 비디오에 주석을 달려면 **[!UICONTROL 주석 달기]**. 비디오에서 특정 시간(프레임)에 주석이 추가됩니다. 캔버스에 주석을 달 때 그림을 그리고 드로잉에 주석을 포함할 수 있습니다. 주석이 자동으로 저장됩니다. 주석 마법사를 종료하려면 **[!UICONTROL 닫기]**.
1. Seek to a specific point in the video, specify the time in seconds in the **text** field and click **Jump**. For example, to skip the first 20 seconds of video, enter 20 in the text field.
1. 타임라인에서 보려면 주석을 클릭합니다. 타임라인에서 주석을 삭제하려면 **[!UICONTROL 삭제]**.

## 우수 사례 및 제한 사항 {#tips-limitations}

* 제외 [!DNL Dynamic Media] 라이선스: 처리 프로필을 사용하여 MP4 파일만 처리할 수 있습니다.
* 처리 프로필을 사용하여 MP4 파일을 코드 변환할 때 다음 지침 및 제한 사항이 적용됩니다.

   * Apple ProRes 파일은 최대 해상도 1080p로만 코드 변환할 수 있습니다.
   * 소스 파일의 비트율이 200Mbps를 초과하는 경우 최대 해상도 1080p로만 코드를 변환할 수 있습니다.
   * 소스 프레임 속도 >=60fps이면 사용할 수 있는 소스 파일의 최대 크기는 다음과 같습니다.

      * 400MB(4k 코드 변환 시)
      * 1080p 코드 변환 시 800MB입니다.
      * 720p 코드 변환의 경우 8GB입니다.
   * 4k 해상도로 변환할 수 있는 최대 파일 크기는 4k 해상도의 2.55GB MP4 파일, 12Mbps 비트율 및 23fps입니다.


>[!MORELIKETHIS]
>
>* [Dynamic Media 비디오 설명서](/help/assets/dynamic-media/video.md).
>* [처리 프로필의 사용, 유형 및 구성에 대해 자세히 알아보십시오](/help/assets/asset-microservices-configure-and-use.md).

