---
title: AEM에서 자산 다운로드
description: AEM에서 자산을 다운로드하고 다운로드 기능을 활성화하거나 비활성화하는 방법에 대해 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# AEM에서 자산 다운로드 {#download-assets-from-aem}

정적 및 동적 표현물을 포함한 자산을 다운로드할 수 있습니다. 다운로드한 자산은 ZIP 파일에 번들로 포함되어 있습니다. 압축 ZIP 파일의 최대 파일 크기는 내보내기 작업의 경우 1GB입니다. 내보내기 작업당 최대 500개의 에셋이 허용됩니다.

>[!NOTE]
>
>자산을 다운로드할 수 있으려면 멤버는 자산 다운로드를 트리거하는 워크플로우를 시작할 권한이 있어야 합니다.

자산을 다운로드하려면 자산으로 이동하고 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 다운로드]** 아이콘을 탭/클릭합니다. 결과 대화 상자에서 다운로드 옵션을 지정합니다.

자산 유형 이미지 세트, 스핀 세트, 혼합 미디어 세트 및 캐러셀 세트는 다운로드할 수 없습니다.

![AEM 자산에서 자산을 다운로드할 때 사용할 수 있는](assets/asset_download_dialog.png)옵션&#x200B;*그림:AEM 자산에서 자산을 다운로드할 때 사용할 수 있는 옵션*

내보내기/다운로드 옵션은 다음과 같습니다. 다이내믹 표현물은 다이내믹 미디어에 고유하며 선택한 자산 외에 즉각적으로 표현물을 생성할 수 있습니다. 이 옵션은 다이내믹 미디어가 활성화된 경우에만 사용할 수 있습니다.

| 내보내기 또는 다운로드 옵션 | 설명 |
|---|---|
| [!UICONTROL 자산] | 변환 없이 자산을 원래 형식으로 다운로드하려면 이 옵션을 선택합니다. |
| [!UICONTROL 표현물] | 표현물은 자산의 이진 표현입니다. 자산은 업로드된 파일의 기본 표현입니다. 그것들은 어떤 수의 진술도 가질 수 있습니다. <br> 이 옵션을 사용하여 다운로드할 변환을 선택할 수 있습니다. 사용할 수 있는 변환은 선택한 자산에 따라 다릅니다. |
| [!UICONTROL 동적 표현물] | 동적 표현물은 다른 표현물을 즉석에서 생성합니다. 이 옵션을 선택하면 이미지 사전 설정 목록에서 선택하여 동적으로 만들 표현물도 선택할 수 있습니다. 또한 측정 크기 및 단위, 형식, 색상 공간, 해상도 및 이미지 수정자(예: 이미지 반전) 선택 |
| [!UICONTROL 각 자산에 대해 별도의 폴더 만들기] | 자산을 다운로드하는 동안 폴더 계층을 유지하려면 이 옵션을 선택합니다. 기본적으로 폴더 계층은 무시되고 모든 자산은 로컬 시스템의 한 폴더에 다운로드됩니다. |

자산에 변환이 있는 경우 옵션 변환 옵션을 사용할 수 있습니다. 자산에 하위 자산이 포함된 경우 하위 자산 옵션을 사용할 수 있습니다.

다운로드할 폴더를 선택하면 폴더 아래의 전체 자산 계층이 다운로드됩니다. 다운로드한 각 자산(상위 폴더 아래에 중첩된 하위 폴더의 자산 포함)을 개별 폴더에 포함하려면 각 자산에 **[!UICONTROL 대해]**&#x200B;별도의 폴더 만들기를 선택합니다.

## 자산 다운로드 서블릿 활성화 {#enable-asset-download-servlet}

AEM의 기본 서블릿을 사용하면 인증된 사용자가 서버와 네트워크를 오버로드할 수 있는 표시된 자산의 ZIP 파일을 만들기 위해 임의로 대규모 동시 다운로드 요청을 발행할 수 있습니다. 이 기능으로 인해 발생할 수 있는 DoS 위험을 줄이기 위해 `AssetDownloadServlet` 게시 인스턴스에 대해 기본적으로 OSGi 구성 요소가 비활성화됩니다.

DAM에서 에셋을 다운로드할 수 있도록 하려면 Asset Share Commons나 기타 포털과 같은 구현을 사용할 때 OSGi 구성을 통해 서블릿을 수동으로 활성화합니다. Adobe에서는 일상적인 다운로드 요구 사항에 영향을 주지 않고 가능한 한 낮은 다운로드 크기를 설정할 것을 권장합니다. 높은 가치는 성능에 영향을 줄 수 있습니다.

1. 게시 실행 모드를 타깃팅하는 이름 지정 규칙이 있는 폴더( `config.publish`즉,

   `/apps/<your-app-name>/config.publish`

1. 구성 폴더에서 `nt:file` 이름이 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`지정된 유형의 새 파일을 만듭니다.
1. 다음으로 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 채웁니다. 다운로드의 최대 크기(바이트)를 값으로 `asset.download.prezip.maxcontentsize`설정합니다. 아래 샘플은 ZIP 다운로드의 최대 크기를 100kB를 초과하지 않도록 구성합니다.

   ```
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 자산 다운로드 서블릿 비활성화 {#disable-asset-download-servlet}

디스패처 구성을 업데이트하여 모든 자산 다운로드 요청을 차단함으로써 AEM 게시 인스턴스에서 이 요청을 비활성화할 `Asset Download Servlet` 수 있습니다. OSGi 콘솔을 통해 직접 서블릿을 수동으로 비활성화할 수도 있습니다.

1. 발송자 구성을 통해 자산 다운로드 요청을 차단하려면 `dispatcher.any` 구성을 편집하고 [필터 섹션에](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter)새 규칙을 추가합니다.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [DRM 보호 에셋 다운로드](drm.md)
>* [Win 또는 Mac 데스크탑에서 AEM 데스크탑 앱을 사용하여 에셋 다운로드](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)
>* [지원되는 Adobe Creative Cloud 앱에서 Adobe Assets Link를 사용하여 에셋 다운로드](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html)


<!-- FULL ARTICLE ARCHIVE IS BELOW 

You can download assets including static and dynamic renditions. Alternatively, you can send emails with links to assets directly from AEM Assets. Downloaded assets are bundled in a ZIP file. The compressed ZIP file has a maximum file size of 1 GB for the export job. You are allowed a maximum of 500 total assets per export job.

>[!NOTE]
>
>Recipients of emails must be members of the `dam-users` group to access the ZIP download link in the email message. To be able to download the assets, the members must have permissions to launch workflows that trigger downloading of assets.

To download assets, navigate to an asset, select the asset, and tap/click the **[!UICONTROL Download]** icon from the toolbar. In the resulting dialog, specify your download options.

The asset types Image Sets, Spin Sets, Mixed Media Sets, and Carousel Sets cannot be downloaded.

![Available options when downloading assets from AEM Assets](assets/asset_download_dialog.png)
*Figure: Available options when downloading assets from AEM Assets*

The following are the Export/Download options. Dynamic renditions are unique to Dynamic Media and let you generate renditions on-the-fly in addition to the asset you selected - that option is only available if you have Dynamic Media enabled.

|Export or download options|Descriptions|
|---|---|
| [!UICONTROL Assets]| Select this to download the asset in its original form without any renditions.|
| [!UICONTROL Renditions] |A rendition is the binary representation of an asset. Assets have a primary representation - that of the uploaded file. They can have any number of representations. <br> With this option, you can select the renditions you want downloaded. The renditions available depend on the asset you select.|
| [!UICONTROL Dynamic Renditions] |A dynamic rendition generates other renditions on-the-fly. When you select this option, you also select the renditions you want to create dynamically by selecting from the image presets list. In addition, you can select the size and unit of measurement, format, color space, resolution, and any image modifiers (for example to invert the image)|
| [!UICONTROL Email] |An email notification is sent to the user. Standard emails templates are available at the following locations:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul> Templates that you customize during deployment should be present at these locations: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul>You can store tenant-specific custom templates at these locations:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul>|
| [!UICONTROL Create separate folder for each asset] |Select this to preserve the folder hierarchy while downloading assets. By default, the folder hierarchy is ignored and all assets are downloaded in one folder in your local system.|

The option renditions option is available if the asset has any renditions. The subassets option is available if the asset includes subassets.

When you select a folder to download, the complete asset hierarchy under the folder is downloaded. To include each asset you download (including assets in child folders nested under the parent folder) in an individual folder, select **[!UICONTROL Create separate folder for each asset]**.

## Enable asset download servlet {#enable-asset-download-servlet}

The default servlet in AEM allows authenticated users to issue arbitrarily-large, concurrent download requests for creating ZIP files of assets visible to them that can overload the server and the network. To mitigate potential DoS risks caused by this feature, `AssetDownloadServlet` OSGi component is disabled by default for publish instances.

To allow downloading assets from your DAM, say when using something like Asset Share Commons or other portal-like implementation, manually enable the servlet via an OSGi configuration. Adobe recommends setting the permissible download size as low as possible without affecting the day-to-day download requirements. A high value may impact performance.

1. Create a folder with a naming convention that targets the publish runmode, that is, `config.publish`:

   `/apps/<your-app-name>/config.publish`

1. In the config folder, create a new file of type `nt:file` named `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Populate `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` with the following. Sets a maximum size (in bytes) for the download as value of `asset.download.prezip.maxcontentsize`. The below sample configures the maximum size of the ZIP download to not exceed 100 kB.

   ```
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Disable asset download servlet {#disable-asset-download-servlet}

The `Asset Download Servlet` can be disabled on an AEM Publish instances by updating the dispatcher configuration to block any asset download requests. The servlet can also be manually disabled via the OSGi console directly.

1. To block asset download requests via a dispatcher configuration edit the `dispatcher.any` configuration and add a new rule to the [filter section](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter).

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

>[!MORELIKETHIS]
>
>* [Download DRM protected assets](drm.md)
>* [Download assets using AEM desktop app on Win or Mac desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)
>* [Download assets using Adobe Assets Link from within the supported Adobe Creative Cloud apps](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html)


-->