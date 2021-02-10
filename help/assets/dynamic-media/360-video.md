---
title: 360/VR 비디오
description: Dynamic Media에서 360 및 VR(Virtual Reality) 비디오로 작업하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 5ff144ffd43501d04d8295d3726fe2368e9b4389
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 0%

---


# 360/VR 비디오 {#vr-video}

360도 비디오는 모든 방향에서 동시에 보기를 기록합니다. 그것들은 전방향 카메라나 카메라 모음을 사용하여 촬영한다. 재생 중에 평면 디스플레이에서 사용자는 보기 각도를 제어할 수 있습니다.모바일 디바이스에서 재생하는 것은 일반적으로 내장된 자이로스코프 컨트롤을 적용합니다.

Dynamic Media에는 360개의 비디오 에셋 전달에 대한 기본 지원이 포함되어 있습니다. 기본적으로 보거나 재생하는 데 추가 구성이 필요하지 않습니다. .mp4, .mkv 및 .mov와 같은 표준 비디오 확장을 사용하여 360개의 비디오를 제공할 수 있습니다. 가장 일반적인 코덱은 H.264입니다.

360/VR 비디오 뷰어를 사용하여 등장방형 비디오를 렌더링할 수 있습니다. 그 결과, 방, 재산, 위치, 풍경, 의료 절차 등의 매력적인 시청 경험을 얻을 수 있습니다.

공간 오디오는 현재 지원되지 않습니다.오디오가 스테레오로 혼합되어 있는 경우 고객이 카메라 보기 각도를 변경해도 균형(L/R)이 변경되지 않습니다.

AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-360-video-custom-thumbnail-feature-video-use.html#dynamic-media)에서 [Dynamic Media 360 비디오 및 사용자 정의 비디오 축소판 사용을 참조하십시오.

[뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md)도 참조하십시오.

## 360 비디오 실행 중 {#video-in-action}

[Space Station 360](http://mobiletest.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS)을 눌러 브라우저 창을 열고 360도 비디오를 보십시오. 비디오를 재생하는 동안 포인터를 새 위치로 드래그하여 보기 각도를 변경합니다.

![360 비디오 ](assets/6_5_360videoiss_simplified.png)
*샘플스페이스 스테이션 360의 비디오 프레임*

## 360/VR 비디오 및 Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Adobe Premiere Pro를 사용하여 360/VR 푸티지를 보고 편집할 수 있습니다. 예를 들어 장면에 로고와 텍스트를 제대로 배치하고 등장방형 미디어용으로 특별히 디자인된 효과 및 전환을 적용할 수 있습니다.

[360/VR 비디오 편집](https://helpx.adobe.com/premiere-pro/how-to/edit-360-vr-video.html)을 참조하십시오.

## 360 비디오 뷰어에 사용할 에셋 업로드 {#uploading-assets-for-use-with-the-video-viewer}

Experience Manager에 업로드된 360개의 비디오 에셋은 일반적인 비디오 에셋과 유사하게 자산 페이지에서 **멀티미디어**&#x200B;로 레이블이 지정됩니다.

![6_5_360video-](assets/6_5_360video-selecttopreview.png)
*selecttopreview카드 보기에 표시된 업로드된 360개의 비디오 에셋입니다. 에셋은 멀티미디어로 레이블이 지정됩니다.*

**360 비디오 뷰어와 함께 사용할 에셋을 업로드하려면:**

1. 360 비디오 자산 전용 폴더를 만들었습니다.
1. [응용 비디오 프로필을 폴더에 적용합니다](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

   360개의 비디오 컨텐츠를 렌더링하면 소스 비디오 해상도와 인코딩된 변환 해상도에 대한 요구 사항이 360개가 아닌 표준 비디오 컨텐츠보다 더 높습니다.

   이미 Dynamic Media과 함께 제공되는 즉시 사용 가능한 비디오 프로필을 사용할 수 있습니다. 그러나 360이 아닌 비디오 뷰어로 렌더링된 동일한 설정으로 인코딩된 비360 비디오에 대해 가져오는 것보다 비디오 품질이 훨씬 낮습니다. 따라서 고품질 360 비디오가 필요한 경우 다음을 수행합니다.

   * 가장 좋은 방법은 원본 360 비디오 컨텐츠에 다음 해상도 중 하나를 사용하는 것입니다.

      * 풀 HD 또는 FHD 해상도로 알려진 1080p - 1920 x 1080 또는
      * 4K, UHD 또는 Ultra HD 해상도로 알려진 2160p - 3840 x 2160 이 큰 디스플레이 해상도는 프리미엄 TV 세트와 컴퓨터 모니터에서 자주 볼 수 있습니다. 2160p 해상도는 너비가 4000픽셀과 가깝기 때문에 &quot;4K&quot;라고도 합니다. 즉, 1080p의 4배 픽셀을 제공합니다.
   * [고품질의 표현물을 사용하여 사용자 ](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) 정의 응용 비디오 프로필을 만듭니다. 예를 들어 다음 3가지 설정을 포함하는 응용 비디오 프로필을 만들 수 있습니다.

      * 너비=auto;높이=720;비트 전송률=2500kbps
      * 너비=auto;높이=1080;비트 전송률=5000kbps
      * 너비=auto;높이=1440;비트 전송률=6600kbps
   * 360개의 비디오 에셋에만 사용되는 폴더에서 360개의 비디오 컨텐츠를 처리합니다.

   이 접근 방식은 최종 사용자의 네트워크 및 CPU에 더 많은 요구를 가져옵니다.

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

## 360 비디오 미리 보기 {#previewing-video}

미리 보기를 사용하여 360 비디오가 고객에게 어떤 모습인지 보고 예상대로 작동하는지 확인할 수 있습니다.

[뷰어 사전 설정 편집](/help/assets/dynamic-media/managing-viewer-presets.md#editing-viewer-presets)을 참조하십시오.

360 비디오가 마음에 들면 게시할 수 있습니다.

[웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)을 참조하십시오.
[웹 응용 프로그램에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)을 참조하십시오. 대화형 컨텐츠에 상대 URL, 특히 Experience Manager 사이트 페이지에 대한 링크가 있는 경우에는 연결 URL 기반 방법을 사용할 수 없습니다.
[페이지에 Dynamic Media 자산 추가를 참조하십시오.](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)

**360 비디오를 미리 보려면**

1. **[!UICONTROL 자산]**&#x200B;에서 만든 기존 360 비디오로 이동합니다. 미리 보기 모드에서 열려면 360 비디오 에셋을 누릅니다.

   ![6_5_360video-selecttopreview-1](assets/6_5_360video-selecttopreview-1.png)

   비디오를 미리 보려면 360 비디오 에셋을 누릅니다.

1. 페이지의 왼쪽 위 모서리 근처에 있는 미리 보기 페이지에서 드롭다운 목록을 탭한 다음 **[!UICONTROL 뷰어]**&#x200B;를 선택합니다.

   ![6_5_360video-preview-viewers](assets/6_5_360video-preview-viewers.png)

   뷰어 목록에서 **[!UICONTROL Video360_social]**&#x200B;을 누른 다음 중 하나를 수행합니다.

   * 정적 장면의 보기 각도를 변경하려면 포인터를 비디오 위로 드래그합니다.
   * 재생을 시작하려면 비디오의 **[!UICONTROL 재생]** 단추를 누릅니다. 비디오가 재생되면 포인터를 비디오 위로 드래그하여 보기 각도를 변경합니다.

   ![6_5_360video-preview-video360-](assets/6_5_360video-preview-video360-social.png)*socialA 360 비디오 스크린샷*

   * 뷰어 목록에서 **[!UICONTROL Video360VR]**&#x200B;을 누릅니다.

      VR(Virtual Reality) 비디오는 가상 현실(VR) 헤드셋을 사용하여 액세스하는 몰입형 비디오 콘텐츠입니다. 일반 비디오와 마찬가지로 360도 비디오 카메라를 사용하여 비디오를 녹화하거나 캡처할 때 초기에 VR 비디오를 만들 수 있습니다.
   ![6_5_360video-preview-video360vr](assets/6_5_360video-preview-video360vr.png)
   *360 VR 비디오 스크린샷*

1. 미리 보기 페이지의 오른쪽 위 근처에 있는 **[!UICONTROL 닫기]**&#x200B;를 탭합니다.

## 360 비디오 게시 {#publishing-video}

360 비디오를 사용하려면 게시해야 합니다. 360 비디오를 게시하면 URL 및 포함 코드가 활성화됩니다. 또한 확장 가능한 성능 전달을 위해 CDN과 통합된 Dynamic Media 클라우드에 360 비디오를 게시합니다.

360 비디오를 게시하는 방법에 대한 자세한 내용은 [Dynamic Media Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) 게시를 참조하십시오.
웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)을 참조하십시오.
[
웹 응용 프로그램](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)에 URL 연결을 참조하십시오. [ 대화형 컨텐츠에 상대 URL, 특히 Experience Manager 사이트 페이지에 대한 링크가 있는 경우에는 연결 URL 기반 방법을 사용할 수 없습니다.
[페이지에 Dynamic Media 자산 추가를 참조하십시오.](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
