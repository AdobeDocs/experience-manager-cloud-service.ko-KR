---
title: 360/VR 비디오
description: Dynamic Media에서 360 및 VR(Virtual Reality) 비디오로 작업하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: 360 VR Video
role: User
exl-id: ffd092d3-2188-47b0-a475-8bfa660c03c1
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 0%

---

# 360/VR 비디오 {#vr-video}

360° 비디오가 모든 방향에서 동시에 보기를 기록합니다. 그것들은 전방향 카메라나 카메라 모음을 사용하여 촬영된다. 재생 중에 플랫 디스플레이에서 사용자는 보기 각도를 제어할 수 있습니다. 모바일 장치에서 재생은 일반적으로 내장된 회전 제어 기능을 적용합니다.

Dynamic Media에는 360개의 비디오 자산 전달에 대한 기본 지원이 포함되어 있습니다. 기본적으로 보거나 재생하는 데 추가 구성이 필요하지 않습니다. .mp4, .mkv 및 .mov와 같은 표준 비디오 확장 기능을 사용하여 360 비디오를 제공합니다. 가장 일반적인 코덱은 H.264입니다.

360/VR 비디오 뷰어를 사용하여 필요한 사각형 비디오를 렌더링할 수 있습니다. 그 결과, 방, 속성, 위치, 가로, 의료 시술 등의 몰입형 시청 환경이 제공됩니다.

공간 오디오가 현재 지원되지 않습니다. 오디오가 스테레오에 혼합되어 있는 경우 고객이 카메라 보기 각도를 변경할 때 균형(L/R)이 변경되지 않습니다.

자세한 내용은 [AEM Assets에서 Dynamic Media 360 비디오 및 사용자 정의 비디오 축소판 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-360-video-custom-thumbnail-feature-video-use.html#dynamic-media).

참조 - [뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md).

## 360 비디오 작동 {#video-in-action}

선택 [우주 정거장 360](https://s7d1.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS) 브라우저 창을 열고 360° 비디오를 시청하십시오. 비디오 재생 중에 포인터를 새 위치로 드래그하여 보기 각도를 변경합니다.

![Space Station 360 비디오 프레임](assets/6_5_360videoiss_simplified.png)
*스페이스 스테이션 360의 비디오 프레임*

## 360/VR 비디오 및 Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Adobe Premier Pro를 사용하여 360/VR 푸티지를 보고 편집할 수 있습니다. 예를 들어 장면에 로고와 텍스트를 제대로 배치하고 특정 사각형 미디어용으로 디자인된 효과 및 전환을 적용할 수 있습니다.

자세한 내용은 [360/VR 비디오 편집](https://helpx.adobe.com/premiere-pro/how-to/edit-360-vr-video.html).

## 360 비디오 뷰어에서 사용할 자산을 업로드합니다 {#uploading-assets-for-use-with-the-video-viewer}

에 업로드된 360개의 비디오 자산 [!DNL Experience Manager] 에는 **멀티미디어** 일반 비디오 자산과 유사한 자산 페이지.

![카드 보기에서 표시된 업로드된 360-비디오 자산](assets/6_5_360video-selecttopreview.png)
*카드 보기에서 표시된 업로드된 360-비디오 자산. 자산 레이블이 멀티미디어로 지정됩니다.*

**360 비디오 뷰어에서 사용할 자산을 업로드합니다.**

1. 360 비디오 자산 전용 폴더를 만들었습니다.
1. [폴더에 응용 비디오 프로필 적용](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

   360개의 비디오 컨텐츠를 렌더링하면 표준 비360개의 비디오 컨텐츠보다 소스 비디오 해상도와 인코딩된 변환 해상도에 대한 요구 사항이 더 높습니다.

   Dynamic Media과 함께 이미 제공되는 기본 응용 비디오 프로필을 사용할 수 있습니다. 그러나 360이 아닌 비디오 뷰어로 렌더링되는 것과 동일한 설정으로 인코딩된 비360 비디오에 대해 가져올 수 있는 것보다 훨씬 낮은 360 비디오 품질을 얻을 수 있습니다. 따라서 고품질 360 비디오가 필요한 경우 다음을 수행하십시오.

   * 가장 좋은 방법은 원래 360 비디오 컨텐츠에 다음 해상도 중 하나를 사용하는 것입니다.

      * 풀 HD 또는 FHD 해상도 또는,
      * 2160p - 3840 x 2160(4k, UHD 또는 Ultra HD 해상도로 알려져 있음) 이 큰 디스플레이 해상도는 프리미엄 TV 세트와 컴퓨터 모니터에서 가장 자주 발견된다. 너비는 4000픽셀에 가깝기 때문에 2160p 해상도를 &quot;4k&quot;라고 합니다. 즉, 1080p의 4배 픽셀을 제공합니다.
   * [사용자 지정 응용 비디오 프로필 만들기](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) 고품질 표현물 사용. 예를 들어 다음 세 가지 설정을 포함하는 응용 비디오 프로필을 만들 수 있습니다.

      * Width=auto; 높이=720; 비트율=2500kbps
      * Width=auto; 높이=1080; 비트율=5000kbps
      * Width=auto; 높이=1440; 비트율=6600kbps
   * 360개의 비디오 자산만 사용하는 폴더에서 360개의 비디오 컨텐츠를 처리합니다.

   이러한 접근 방식은 최종 사용자의 네트워크 및 CPU에 더 많은 요구를 추가합니다.

1. [비디오를 폴더에 업로드합니다](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

<!--

## Overriding the default aspect ratio of 360 videos  {#overriding-the-default-aspect-ratio-of-videos}

For an uploaded asset to qualify as a 360 video that you intend to use with the 360 Video viewer, the asset must have an aspect ratio of 2.

By default, AEM detects video as "360" if its aspect ratio (width/height) is 2.0. If you are an Administrator, you can override the default aspect ratio setting of 2 by setting the optional `s7video360AR` property in CRXDE Lite at the following:

* `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

  * **Property type**: Double
  * **Value**: floating-point aspect ratio, default 2.0.

After you set this property, it takes effect immediately on both existing videos and newly uploaded videos.

The aspect ratio applies to 360 video assets for the asset details page and the [Video 360 Media WCM component](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components).

Start by uploading 360 Videos.

-->

## 비디오 미리 보기 360 {#previewing-video}

미리 보기 를 사용하여 360 비디오가 고객에게 표시되는 방식을 확인하고 예상대로 작동하는지 확인할 수 있습니다.

참조 - [뷰어 사전 설정 편집](/help/assets/dynamic-media/managing-viewer-presets.md#editing-viewer-presets).

360 비디오가 마음에 들면 게시할 수 있습니다.

자세한 내용은 [웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md).
자세한 내용은 [URL을 웹 애플리케이션에 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). 대화형 컨텐츠에 특히 [!DNL Experience Manager Sites] 페이지.
자세한 내용은 [페이지에 Dynamic Media 자산 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

**360 비디오를 미리 보려면:**

1. in **[!UICONTROL 자산]**&#x200B;를 만든 기존 360 비디오로 이동합니다. 미리 보기 모드에서 열려면 360 비디오 자산을 선택합니다.

   ![Experience Manager 카드 보기에 표시된 업로드된 360개의 비디오 자산의 스크린샷입니다.](assets/6_5_360video-selecttopreview-1.png)

   비디오를 미리 보려면 360-비디오 자산을 선택합니다.

1. 미리 보기 페이지의 왼쪽 위 모서리 근처에 있는 드롭다운 목록을 선택한 다음 을 선택합니다 **[!UICONTROL 뷰어]**.

   ![사용 가능한 비디오 뷰어 목록을 보기 위해 뷰어를 선택하는 스크린샷.](assets/6_5_360video-preview-viewers.png)

   뷰어 목록에서 를 선택합니다. **[!UICONTROL Video360_social]**&#x200B;를 입력한 후 다음 중 하나를 수행합니다.

   * 정적 장면의 보기 각도를 변경하려면 포인터를 비디오 위로 드래그합니다.
   * 재생을 시작하려면 비디오의 을(를) 선택합니다 **[!UICONTROL 재생]** 버튼을 클릭합니다. 비디오가 재생될 때 포인터를 비디오 위로 드래그하여 보기 각도를 변경합니다.

   ![Video360_Social 뷰어를 선택하여 360도 비디오를 미리 보는 사용자의 스크린샷입니다.](assets/6_5_360video-preview-video360-social.png)*360개의 비디오 스크린샷입니다.*

   * 뷰어 목록에서 를 선택합니다. **[!UICONTROL Video360VR]**.

      VR(Virtual Reality) 비디오는 가상 현실 헤드셋을 사용하여 액세스하는 몰입형 비디오 콘텐츠입니다. 일반 비디오처럼 360° 비디오 카메라를 사용하여 비디오를 녹화하거나 캡처할 때 VR 비디오를 만들 수 있습니다.
   ![Video360VR 뷰어 옵션 위로 마우스 포인터를 가져간 사용자의 스크린샷입니다.](assets/6_5_360video-preview-video360vr.png)
   *360 VR 비디오 스크린샷입니다.*

1. 미리 보기 페이지의 오른쪽 상단에서 을(를) 선택합니다 **[!UICONTROL 닫기]**.

## 360 비디오 게시 {#publishing-video}

360 비디오를 사용하려면 게시해야 합니다. 360 비디오를 게시하면 URL 및 포함 코드가 활성화됩니다. 또한 확장 가능하고 성능 전달을 위해 CDN과 통합된 Dynamic Media 클라우드에 360 비디오를 게시합니다.

자세한 내용은 [Dynamic Media 자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) 를 참조하십시오.
참조 - [웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md).
참조 - [URL을 웹 애플리케이션에 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). 대화형 컨텐츠에 특히 [!DNL Experience Manager Sites] 페이지.
참조 - [페이지에 Dynamic Media 자산 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
