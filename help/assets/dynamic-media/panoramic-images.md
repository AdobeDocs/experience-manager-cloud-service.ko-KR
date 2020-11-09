---
title: 파노라마 이미지
description: Dynamic Media에서 파노라마 이미지를 사용하여 작업하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 2%

---


# Panoramic images{#panoramic-images}

이 섹션에서는 [파노라마 이미지] 뷰어를 사용하여 회의실, 속성, 위치 또는 조경의 몰입형 360° 보기 경험을 위해 구형 파노라마 이미지를 렌더링하는 작업에 대해 설명합니다.

See also [Managing Viewer Presets](/help/assets/dynamic-media/managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## 파노라마 이미지 뷰어에 사용할 에셋 업로드 {#uploading-assets-for-use-with-the-panoramic-image-viewer}

업로드된 자산이 파노라마 이미지 뷰어와 함께 사용할 구형 파노라마 이미지로 자격을 갖추려면 자산에 다음 중 하나 또는 둘 다가 있어야 합니다.

* 2 종횡비

<!--  You can override the default aspect ratio setting of 2 in CRXDE Lite at the following:
  `/conf/global/settings/cloudconfigs/dmscene7/jcr:content` -->
* 키워드 `equirectangular`, `spherical`및 `panorama`및 `spherical` 및 `panoramic`으로 태그되었습니다. 태그 [사용을 참조하십시오](/help/sites-cloud/authoring/features/tags.md).

종횡비와 키워드 기준은 모두 자산 세부 사항 페이지와 WCM 구성 요소의 파노라마 자산에 `Panoramic Media` 적용됩니다.

파노라마 이미지 뷰어에 사용할 자산을 업로드하려면 자산 [업로드를 참조하십시오](/help/assets/manage-digital-assets.md#uploading-assets).

<!--  NEED TO CHECK IF DM CLASSIC PART OF SKYLINE 

## Configuring Dynamic Media Classic (Scene7) {#configuring-dynamic-media-classic-scene}

For the Panoramic Image viewer to work properly within AEM, you must synchronize the Panoramic Image viewer presets with Dynamic Media Classic (Scene7) and Dynamic Media Classic (Scene7)-specific metadata so the viewer presets get updated in the JCR. To accomplish this, configure Dynamic Media Classic (Scene7) in the following manner:

1. [Log into your instance of Dynamic Media Classic (Scene7)](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) for each company account.

1. Near the upper-right corner of the page, click **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**.
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

1. At the bottom of the Image Server Publish page, on the left side, click **[!UICONTROL Save]**.

1. In the lower-right corner, click **[!UICONTROL Close]**.

### Troubleshooting the Panoramic Media WCM component {#troubleshooting-the-panoramic-media-wcm-component}

If you dropped an image into the Panoramic Media component in your WCM and the component placeholder collapsed, you may want to troubleshoot the following:

* If you experience a 403 Forbidden error, it may have been caused by the requested image size being too large. Review the **[!UICONTROL Reply Image Size Limit]** settings in [Configuring Dynamic Media Classic (Scene7)](/help/assets/dynamic-media/panoramic-images.md#configuring%20dynamic%20media%20classic%20(scene7)).

* For an "Invalid lock" on the asset or "Parsing error" displayed on the page, check Request Obfuscation Mode and Request Locking Mode to ensure they are disabled.
* For a tainted canvas error, setup a Rule Set Definition File Path and Invalidate CTN for the previous requests for the image asset.
* If image quality becomes very low after an image request with sizing above the supported limit, check that the **[!UICONTROL JPEG Encoding Attributes > Quality]** setting is not empty. A typical setting for the **[!UICONTROL Quality]** field is `95`. You can find the setting on the Image Server Publish page. To access the page, see [Configuring Dynamic Media Classic (Scene7)](/help/assets/dynamic-media/panoramic-images.md#configuring%20dynamic%20media%20classic%20(scene7)).

-->

## 파노라마 이미지 미리 보기 {#previewing-panoramic-images}

자산 [미리 보기를 참조하십시오](/help/assets/dynamic-media/previewing-assets.md).

## 파노라마 이미지 게시 {#publishing-panoramic-images}

자산 [게시를 참조하십시오](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).