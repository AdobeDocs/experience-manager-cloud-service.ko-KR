---
title: 에셋 다운로드
description: 다음에서 자산 다운로드 [!DNL Adobe Experience Manager Assets] 다운로드 기능을 활성화하거나 비활성화합니다.
contentOwner: VG
feature: Asset Management
role: User
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: 797f0e6585666196acf7972f93d936fc54359c4a
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 3%

---

# 다음에서 자산 다운로드 [!DNL Adobe Experience Manager] {#download-assets-from-aem}

정적 및 동적 표현물을 포함한 자산을 다운로드할 수 있습니다. 또는 다음에서 바로 자산에 대한 링크가 있는 이메일을 보낼 수 있습니다 [!DNL Adobe Experience Manager Assets]. 다운로드한 자산은 ZIP 파일에 번들로 제공됩니다. <!-- The compressed ZIP file has a maximum file size of 1 GB for the export job. A maximum of 500 total assets per export job are allowed. -->

<!--
>[!NOTE]
>
>Recipients of emails must be members of the `dam-users` group to access the ZIP download link in the email message. To be able to download the assets, the members must have permissions to launch workflows that trigger downloading of assets.
-->

자산 유형 이미지 세트, 스핀 세트, 혼합 미디어 세트 및 회전 세트는 다운로드할 수 없습니다.

다음 방법을 사용하여 Experience Manager 자산을 다운로드할 수 있습니다.

<!-- * [Link Share](#link-share-download) -->

* [Experience Manager 사용자 인터페이스](#download-assets)
* [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
* [데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets)

## 을 사용하여 자산 다운로드 [!DNL Experience Manager] 인터페이스 {#download-assets}

비동기 다운로드 서비스는 대형 자산을 원활하게 다운로드할 수 있는 프레임워크를 제공합니다. 100GB보다 큰 다운로드 아카이브는 최대 크기가 100GB인 다중 zip 아카이브로 분할됩니다. 이러한 파일은 개별적으로 다운로드할 수 있습니다. 작은 파일은 사용자 인터페이스에서 실시간으로 다운로드됩니다. [!DNL Experience Manager] 원본 파일이 다운로드되는 단일 자산 다운로드를 보관하지 않습니다. 이 기능을 사용하면 더 빨리 다운로드할 수 있습니다.

기본적으로 [!DNL Experience Manager] 다운로드 워크플로우가 완료되면 알림을 트리거합니다. 다운로드 알림이  [[!DNL Experience Manager] 받은 편지함](/help/sites-cloud/authoring/getting-started/inbox.md).

![받은 편지함 알림](assets/inbox-notification-for-large-downloads.png)

<!--
The large files are downloaded asynchronously and [!DNL Experience Manager] notifies of the completion via notifications in the Inbox. See [understand [!DNL Experience Manager] Inbox](/help/sites-cloud/authoring/getting-started/inbox.md).

![Download notification](assets/download-notification.png)

*Figure: Download notification via [!DNL Experience Manager] Inbox.*

Asynchronous downloads are triggered in either of the following case:

* If there are more than 10 assets or more than 100 MB to be downloaded.
* If the download takes more than 30 seconds to prepare.
-->


<!-- Go live is on 27th Jan 2022
### Enable email notifications for large downloads {#enable-emails-for-large-downloads}

Asynchronous downloads are triggered in any of the following cases:

* If there are more than ten assets 
* If the download size is more than 100 MB
* If the download takes more than 30 seconds to prepare

While the asynchronous download runs at the backend, the user can continue to explore and work further in Experience Manager. An out-of-the-box mechanism is required to notify the user upon completion of the download process. To achieve this objective, the administrators can configure email service by setting up an SMTP server. See [configure Mail Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html#sending-email).

Once the email service is configured, the administrators and users can enable email notifications from the Experience Manager interface. 

To enable email notifications:

1. Log in to [!DNL Experience Manager Assets].
1. Click the user icon from the upper-right corner and then click **[!UICONTROL My Preferences]**. The User Preferences window opens.
1. Select the **[!UICONTROL Asset Download email notifications]** check box and click **[!UICONTROL Accept]**.

   ![enable-email-notifications-for-large-downloads](/help/assets/assets/enable-email-for-large-downloads.png)

-->

자산을 다운로드하려면 다음 단계를 수행하십시오.

1. in [!DNL Experience Manager] 사용자 인터페이스, **[!UICONTROL 자산]** > **[!UICONTROL 파일]**.
1. 다운로드할 자산으로 이동합니다. 폴더를 선택하거나 폴더 내에서 하나 이상의 자산을 선택합니다. 도구 모음에서 **[!UICONTROL 다운로드]**.

   ![다음에서 자산을 다운로드할 때 사용할 수 있는 옵션 [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

1. 다운로드 대화 상자에서 원하는 다운로드 옵션을 선택합니다.

   | 다운로드 옵션 | 설명 |
   |---|---|
   | **[!UICONTROL 각 자산에 대해 별도의 폴더 만들기]** | 다운로드할 각 자산을 자산의 상위 폴더 아래에 중첩된 하위 폴더에 로컬 컴퓨터의 한 폴더로 포함하려면 이 옵션을 선택합니다. 이 옵션이 *not* 을(를) 선택합니다. 기본적으로 폴더 계층은 무시되고 모든 자산은 로컬 컴퓨터의 한 폴더에 다운로드됩니다. |
   | **[!UICONTROL 이메일]** | 다른 사용자에게 이메일 알림(다운로드 링크가 포함됨)을 보내려면 이 옵션을 선택합니다. 수신자 사용자는 `dam-users` 그룹에 속해 있어야 합니다. 표준 이메일 템플릿은 다음 위치에서 사용할 수 있습니다.<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> 배포 중에 사용자 지정하는 템플릿은 다음 위치에서 사용할 수 있습니다. <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>다음 위치에 임차인별 사용자 지정 템플릿을 저장할 수 있습니다.<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL 자산]** | 이 옵션을 선택하면 변환 없이 자산을 원래 양식으로 다운로드합니다.<br>원본 자산에 하위 자산이 있는 경우 하위 자산 옵션을 사용할 수 있습니다. |
   | **[!UICONTROL 렌디션]** | 표현물은 자산의 이진 표현입니다. 자산에는 업로드된 파일의 표현인 기본 표현이 있습니다. 레프리젠테이션들을 수 있어요 <br> 이 옵션을 사용하여 다운로드할 표현물을 선택할 수 있습니다. 사용 가능한 표현물은 선택한 자산에 따라 다릅니다. |
   | **[!UICONTROL 스마트 자르기]** | 내에서 선택한 자산의 모든 스마트 자르기 렌디션을 다운로드하려면 이 옵션을 선택합니다 [!DNL Experience Manager]. 스마트 자르기 렌디션이 있는 zip 파일이 만들어지고 로컬 컴퓨터에 다운로드됩니다. |
   | **[!UICONTROL 동적 렌디션]** | 일련의 대체 표현물을 실시간으로 생성하려면 이 옵션을 선택합니다. 이 옵션을 선택하면, [이미지 사전 설정](/help/assets/dynamic-media/image-presets.md) 목록. <br>또한 측정 크기 및 단위, 형식, 색상 공간, 해상도 및 이미지 반전 등의 선택적 이미지 수정자를 선택할 수 있습니다. 이 옵션은 [!DNL Dynamic Media] 활성화되었습니다. |

1. 대화 상자에서 **[!UICONTROL 다운로드]**.

   큰 다운로드에 대해 이메일 알림이 활성화되면 보관된 zip 폴더의 다운로드 URL이 포함된 이메일이 받은 편지함에 나타납니다. 이메일에서 다운로드 링크를 클릭하여 zip 폴더를 다운로드합니다.

   ![대규모 다운로드용 이메일 알림](/help/assets/assets/email-for-large-notification.png)

   또한 [!DNL Experience Manager] 받은 편지함.

   ![inbox-notifications-for-large-downloads](/help/assets/assets/inbox-notification-for-large-downloads.png)

## 링크 공유를 사용하여 공유된 자산 다운로드 {#link-share-download}

<!--
>[!NOTE]
>
>This functionality is available in the Experience Manager prerelease channel.
-->

링크를 사용하여 자산을 공유하는 것은 관심 있는 사람이 처음 로그인하지 않고도 이용할 수 있는 편리한 방법입니다 [!DNL Assets]. 자세한 내용은 [링크 공유 기능](/help/assets/share-assets.md#sharelink).

사용자가 공유 링크에서 자산을 다운로드하면, [!DNL Assets] 은 빠르고 중단 없는 다운로드를 제공하는 비동기 서비스를 사용합니다. 다운로드할 자산은 받은 편지함의 백그라운드에서 관리할 수 있는 파일 크기의 ZIP 아카이브로 전송됩니다. 매우 큰 다운로드의 경우 다운로드가 100GB의 파일로 청크됩니다.

받은 편지함은 각 아카이브의 처리 상태를 표시합니다. 처리가 완료되면 받은 편지함에서 아카이브를 다운로드할 수 있습니다.

![받은 편지함 다운로드](assets/download-inbox.png)

## 자산 다운로드 서블릿 활성화 {#enable-asset-download-servlet}

의 기본 서블릿 [!DNL Experience Manager] 인증된 사용자가 자산의 ZIP 파일을 만들기 위해 임의로 크기가 큰 동시 다운로드 요청을 발행할 수 있도록 해줍니다. 다운로드 준비에는 성능 문제가 있거나 서버와 네트워크에 과부하가 될 수 있습니다. 이 기능으로 인해 발생할 수 있는 DoS와 유사한 위험을 줄이려면 `AssetDownloadServlet` 게시 인스턴스에 대해 OSGi 구성 요소가 비활성화됩니다. 작성자 인스턴스에 다운로드 기능이 필요하지 않은 경우 작성자에 대한 서블릿을 비활성화합니다.

DAM에서 자산을 다운로드할 수 있도록 하려면 Asset Share Commons 또는 기타 포털과 같은 구현을 사용할 때 OSGi 구성을 통해 서블릿을 수동으로 활성화합니다. Adobe은 일상적인 다운로드 요구 사항에 영향을 주지 않고 허용된 다운로드 크기를 가능한 한 낮게 설정할 것을 권장합니다. 높은 값은 성능에 영향을 줄 수 있습니다.

1. 게시 실행 모드를 대상으로 하는 이름 지정 규칙(즉, `config.publish`:

   `/apps/<your-app-name>/config.publish`

1. 구성 폴더에서 새 유형의 파일을 만듭니다 `nt:file` 명명된 이름 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. 채우기 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 다음을 포함합니다. 다운로드에 대한 최대 크기(바이트)를 값으로 설정합니다. `asset.download.prezip.maxcontentsize`. 아래 샘플은 ZIP 다운로드의 최대 크기를 100kB를 초과하지 않도록 구성합니다.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 자산 다운로드 서블릿 비활성화 {#disable-asset-download-servlet}

다운로드 기능이 필요하지 않은 경우 DoS와 유사한 위험을 방지하기 위해 서블릿을 비활성화하십시오. 다음 `Asset Download Servlet` 는 [!DNL Experience Manager] dispatcher 구성을 업데이트하여 모든 자산 다운로드 요청을 차단하여 인스턴스를 작성 및 게시합니다. OSGi 콘솔을 통해 직접 서블릿을 수동으로 비활성화할 수도 있습니다.

1. 디스패처 구성을 통해 자산 다운로드 요청을 차단하려면 `dispatcher.any` 구성 및 새 규칙을 [필터 섹션](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring).

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

## 팁 및 제한 사항 {#tips-limitations}

* 빈 폴더를 다운로드하면, [!DNL Experience Manager] zip 아카이브 만들기에 대한 성공 메시지를 전달하지만 아카이브는 만들어지지 않습니다.

>[!MORELIKETHIS]
>
>* [DRM 보호 자산 다운로드](drm.md)
>* [Win 또는 Mac 데스크탑에서 Experience Manager 데스크탑 앱을 사용하여 자산 다운로드](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)
>* [지원되는 Adobe Creative Cloud 앱 내에서 Adobe 자산 링크를 사용하여 자산을 다운로드합니다](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html)

