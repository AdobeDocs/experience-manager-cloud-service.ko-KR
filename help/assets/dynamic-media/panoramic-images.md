---
title: 파노라마 이미지
description: Dynamic Media에서 파노라마 이미지를 사용하여 작업하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Panoramic Images
role: User
exl-id: bdc5d00e-fa92-4db5-a3b2-4dd5885eec0b
source-git-commit: f6162dcbc5b7937d55922e8c963a402697110329
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 1%

---

# 파노라마 이미지{#panoramic-images}

이 섹션에서는 파노라마 이미지 뷰어를 사용하여 공간, 속성, 위치 또는 풍경을 360° 몰입형으로 볼 수 있도록 구형 파노라마 이미지를 렌더링하는 방법에 대해 설명합니다.

참조: [뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## 파노라마 이미지 뷰어에 사용할 자산 업로드 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

업로드한 에셋이 파노라마 이미지 뷰어에 사용하려는 구면 파노라마 이미지로서 적합하려면, 에셋에 다음 중 하나 또는 둘 다 있어야 합니다.

* 종횡비가 2입니다.
<!--  You can override the default aspect ratio setting of 2 in CRXDE Lite at the following:
  `/conf/global/settings/cloudconfigs/dmscene7/jcr:content` -->
* 키워드로 태그 지정됨 `equirectangular`, 또는 `spherical`및 `panorama`, 또는 `spherical` 및 `panoramic`. 다음을 참조하십시오 [태그 사용](/help/sites-cloud/authoring/sites-console/tags.md).

종횡비와 키워드 기준은 모두 자산 세부 사항 페이지 및 의 파노라마 자산에 적용됩니다. `Panoramic Media` WCM 구성 요소입니다.

파노라마 이미지 뷰어에 사용할 자산을 업로드하려면 다음을 참조하십시오. [에셋 업로드](/help/assets/manage-digital-assets.md#uploading-assets).

<!--  NEED TO CHECK IF DM CLASSIC PART OF SKYLINE 

## Configuring Dynamic Media Classic (Scene7) {#configuring-dynamic-media-classic-scene}

For the Panoramic Image viewer to work properly within AEM, you must synchronize the Panoramic Image viewer presets with Dynamic Media Classic (Scene7) and Dynamic Media Classic (Scene7)-specific metadata so the viewer presets get updated in the JCR. To accomplish this, configure Dynamic Media Classic (Scene7) in the following manner:

1. Open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account.

1. Near the upper-right corner of the page, navigate to **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]**.
1. On the Image Server Publish page, from the **[!UICONTROL Publish Context]** drop-down menu near the top, select **[!UICONTROL Image Serving]**.

1. On the same Image Server Publish page, locate the heading **[!UICONTROL Request Attributes]**.
1. Under the Request Attributes heading, locate **[!UICONTROL Reply Image Size Limit]**. Then, in the associated Width and Height fields, increase the maximum allowable image size for panoramic images.

   Dynamic Media Classic (Scene7) has a limit of 25,000,000 pixels. The maximum allowable size for images with a 2:1 aspect ratio is 7000 x 3500. However, for typical desktop screens, 4096 x 2048 pixels is sufficient.

   >[!NOTE]
   >
   >Only images that fall within the maximum allowable image size are supported. Requests for images that are above the size limit will result in a 403 response.

1. Under the Request Attributes heading, do the following:

    * Set Request Obfuscation Mode to **[!UICONTROL Disabled]**.
    * Set Request Locking Mode to **[!UICONTROL Disabled]**.

   These settings are necessary for using the `Panoramic Media` WCM component in AEM.

1. At the bottom of the Image Server Publish page, on the left side, select **[!UICONTROL Save]**.

1. In the lower-right corner, select **[!UICONTROL Close]**.

### Troubleshooting the Panoramic Media WCM component {#troubleshooting-the-panoramic-media-wcm-component}

If you dropped an image into the Panoramic Media component in your WCM and the component placeholder collapsed, you may want to troubleshoot the following:

* If you experience a 403 Forbidden error, it may have been caused by the requested image size being too large. Review the **[!UICONTROL Reply Image Size Limit]** settings in [Configuring Dynamic Media Classic (Scene7)](/help/assets/dynamic-media/panoramic-images.md#configuring%20dynamic%20media%20classic%20(scene7)).

* For an "Invalid lock" on the asset or "Parsing error" displayed on the page, check Request Obfuscation Mode and Request Locking Mode to ensure they are disabled.
* For a tainted canvas error, setup a Rule Set Definition File Path and Invalidate CTN for the previous requests for the image asset.
* If image quality becomes very low after an image request with sizing above the supported limit, check that the **[!UICONTROL JPEG Encoding Attributes > Quality]** setting is not empty. A typical setting for the **[!UICONTROL Quality]** field is `95`. You can find the setting on the Image Server Publish page. To access the page, see [Configuring Dynamic Media Classic (Scene7)](/help/assets/dynamic-media/panoramic-images.md#configuring%20dynamic%20media%20classic%20(scene7)).

-->

## 파노라마 이미지 미리 보기 {#previewing-panoramic-images}

다음을 참조하십시오 [에셋 미리보기](/help/assets/dynamic-media/previewing-assets.md).

## 파노라마 이미지 게시 {#publishing-panoramic-images}

다음을 참조하십시오 [자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
