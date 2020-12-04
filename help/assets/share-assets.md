---
title: 자산, 폴더 및 컬렉션을 링크로 공유
description: 이 문서에서는 Experience Manager 자산 내에서 자산, 폴더 및 컬렉션을 하이퍼링크로 공유하는 방법에 대해 설명합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ce22a7ba95942881b90a4f3f22d89bcd35b5e559
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 1%

---


# Experience Manager {#share-assets-from-aem}에서 관리되는 에셋 공유 및 배포

Adobe Experience Manager(AEM) 자산을 사용하여 자산, 폴더 및 컬렉션을 조직 구성원 및 파트너 및 벤더를 비롯한 외부 엔티티의 구성원과 공유할 수 있습니다. 다음 방법을 사용하여 Experience Manager 자산의 자산을 [!DNL Cloud Service]으로 공유합니다.

* 링크로 공유
* 에셋을 다운로드하고 별도로 공유할 수 있습니다.
* AEM 데스크탑 앱을 통해 공유
* Adobe 에셋 링크를 통해 공유합니다.
* (향후 기능) 브랜드 포털을 사용하여 공유

## 링크로 자산 공유 {#sharelink}

사용자와 공유할 에셋의 URL을 생성하려면 링크 공유 대화 상자를 사용합니다. 관리자 권한이 있거나 읽기 권한이 `/var/dam/share` 위치에 있는 사용자는 자신과 공유된 링크를 볼 수 있습니다. 링크를 통해 자산을 공유하는 것은 외부 당사자가 먼저 AEM Assets에 로그인하지 않고도 리소스를 사용할 수 있도록 하는 편리한 방법입니다.

>[!NOTE]
>
>* 링크로 공유할 폴더 또는 자산에 대해 ACL 편집 권한이 필요합니다.
>* 사용자와 링크를 공유하기 전에 요일 CQ 메일 서비스가 구성되어 있는지 확인합니다. 그렇지 않으면 오류가 발생합니다.


1. 자산 사용자 인터페이스에서 링크로 공유할 자산을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 링크 공유]**&#x200B;를 클릭/탭합니다. 자산 링크가 **[!UICONTROL 링크 공유]** 필드에 자동으로 만들어집니다. 이 링크를 복사하고 사용자와 공유합니다. 링크에 대한 기본 만료 시간은 하루입니다.

   >[!NOTE]
   >
   >공유 에셋이 다른 위치로 이동되면 해당 링크가 작동하지 않습니다. 링크를 다시 만들고 사용자와 다시 공유합니다.

<!--
## Share assets as a link {#sharelink}

To generate the URL for assets you want to share with users, use the Link Sharing dialog. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Sharing assets through a link is a convenient way of making resources available to external parties without them having to first log in to AEM Assets.

>[!NOTE]
>
>* You need Edit ACL permission on the folder or the asset that you want to share as a link.
>* Before you share a link with users, ensure that Day CQ Mail Service is configured. Otherwise, an error occurs.

1. In the Assets user interface, select the asset to share as a link.
1. From the toolbar, click/tap the **[!UICONTROL Share Link]**.

   An asset link is auto-created in the **[!UICONTROL Share Link]** field. Copy this link and share it with the users. The default expiration time for the link is one day.

   Alternatively, proceed to perform steps 3-7 of this procedure to add email recipients, configure the expiration time for the link, and send it from the dialog.

   >[!NOTE]
   >
   >If a shared asset is moved to a different location, its link stops working. Re-create the link and re-share with the users.

1. From the web console, open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against each:

    * local
    * author
    * publish

   For the local and author properties, provide the URL for the local and author instance respectively. Both local and author properties have the same value if you run a single AEM author instance. For publish, provide the URL for the publish instance.

1. In the email address box of the **[!UICONTROL Link Sharing]** dialog, type the email ID of the user you want to share the link with. You can also share the link with multiple users.

   If the user is a member of your organization, select the user's email ID from the suggested email IDs that appear in the list below the typing area. For an external user, type the complete email ID and then select it from the list.

   To enable emails to be sent out to users, configure the SMTP server details in [Day CQ Mail Service](/help/assets/configure-asset-sharing.md#configmailservice).

   >[!NOTE]
   >
   >If you enter an email ID of a user that is not a member of your organization, the words "External User" are prefixed with the email ID of the user.

1. In the **[!UICONTROL Subject]** box, enter a subject for the asset you want to share.
1. In the **[!UICONTROL Message]** box, enter an optional message.
1. In the **[!UICONTROL Expiration]** field, specify an expiration date and time for the link using the date picker. By default, the expiration date is set for a week from the date you share the link.
1. To let users download the original image along with the renditions, select **[!UICONTROL Allow download of original file]**.

   >[!NOTE]
   >
   >By default, users can only download the renditions of the asset that you share as a link.

1. Click **[!UICONTROL Share]**. A message confirms that the link is shared with the users through an email.
1. To view the shared asset, click/tap the link in the email that is sent to the user. The shared asset is displayed in the **[!UICONTROL Adobe Marketing Cloud]** page.

   To toggle to the list view, click/tap the layout icon in the toolbar.

1. To generate a preview of the asset, click/tap the shared asset. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click/tap **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click/tap **[!UICONTROL Parent Folder]** to return to the parent folder.

   >[!NOTE]
   >
   >AEM supports generating the preview of assets of these MIME types: JPG, PNG, GIF, BMP, INDD, PDF, and PPT. You can only download the assets of the other MIME types.

1. To download the shared asset, click/tap **[!UICONTROL Select]** from the toolbar, click/tap the asset, and then click/tap **[!UICONTROL Download]** from the toolbar.
1. To view the assets you shared as links, go to the Assets user interface and click/tap the GlobalNav icon. Choose **[!UICONTROL Navigation]** from the list to display the Navigation pane.
1. From the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.
1. To un-share an asset, select it and tap/click **[!UICONTROL Unshare]** from the toolbar.

A message confirms that you unshared the asset. In addition, the entry for the asset is removed from the list.
-->

## 자산 다운로드 및 공유 {#download-and-share-assets}

사용자는 필요한 에셋을 다운로드하고 [!DNL Experience Manager] 외부에서 공유할 수 있습니다. 자세한 내용은 [자산 검색 방법](/help/assets/search-assets.md), [자산 다운로드 방법](/help/assets/download-assets-from-aem.md) 및 [컬렉션 다운로드 방법](manage-collections.md#download-a-collection)을 참조하십시오.

## 크리에이티브 전문가와 에셋 공유 {#share-with-creatives}

마케터와 업무 부문 사용자는

* **AEM 데스크탑 앱**:이 앱은 Windows 및 Mac에서 작동합니다. [데스크탑 앱 개요](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)를 참조하십시오. 권한이 있는 데스크톱 사용자가 공유 에셋에 쉽게 액세스할 수 있는 방법을 알아보려면 [에셋 검색 및 미리 보기](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets)를 참조하십시오. 데스크탑 사용자는 예를 들어 새 이미지를 업로드하여 자산을 만들고 AEM 사용자와 다시 공유할 수 있습니다. 데스크톱 앱[을 사용하여 자산 업로드를 참조하십시오.](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem)

* **Adobe 자산 링크**:크리에이티브 전문가는 Adobe InDesign, Adobe Illustrator 및 Adobe Photoshop에서 바로 에셋을 검색하고 사용할 수 있습니다.

## 자산 공유 구성 {#configure-sharing}

자산을 공유하는 다른 옵션은 특정 구성이 필요하며 특정 사전 요구 사항을 갖습니다.

### 자산 링크 공유 구성 {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

사용자와 공유할 에셋의 URL을 생성하려면 링크 공유 대화 상자를 사용합니다. 관리자 권한이 있거나 읽기 권한이 `/var/dam/share` 위치에 있는 사용자는 자신과 공유된 링크를 볼 수 있습니다. 링크를 통해 자산을 공유하는 것은 외부 당사자가 먼저 AEM Assets에 로그인하지 않고도 리소스를 사용할 수 있도록 하는 편리한 방법입니다.

>[!NOTE]
>
>AEM 작성자 인스턴스의 링크를 외부 엔티티에 공유하려면 `GET` 요청에 대해 다음 URL만 표시해야 합니다. 다른 URL을 차단하여 AEM 작성자 인스턴스가 안전한지 확인합니다.
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


<!--
## Configure Day CQ mail service {#configmailservice}

Before you can share assets as links, configure the email service.

1. Click or tap the AEM logo, and then navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. From the list of services, locate **[!UICONTROL Day CQ Mail Service]**.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **Day CQ Mail Service]** with the details mentioned against their names:

    * SMTP server host name: email server host name
    * SMTP server port: email server port
    * SMTP user: email server user name
    * SMTP password: email server password

1. Click/tap **[!UICONTROL Save]**.
-->

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.
### Configure maximum data size {#maxdatasize}

When you download assets from the link shared using the Link Sharing feature, AEM compresses the asset hierarchy from the repository and then returns the asset in a ZIP file. However, in the absence of limits to the amount of data that can be compressed in a ZIP file, huge amounts of data is subjected to compression, which causes out of memory errors in JVM. To secure the system from a potential denial of service attack due to this situation, you can configure the maximum size of the downloaded files. If uncompressed size of the asset exceeds the configured value, asset download requests are rejected. The default value is 100 MB.

1. Click/Tap the AEM logo and then go to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. From the web console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Open the configuration in edit mode, and modify the value of the **[!UICONTROL Max Content Size (uncompressed)]** parameter.
1. Save the changes.
-->

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->

### 데스크탑 앱 {#desktop-actions}에 사용할 데스크톱 작업 활성화

브라우저의 자산 사용자 인터페이스 내에서 자산 위치를 탐색하거나 체크 아웃하고 자산을 열어 데스크탑 애플리케이션에서 편집할 수 있습니다. 이러한 옵션은 데스크톱 작업이라고 하며 이를 활성화하려면 AEM 웹 인터페이스[에서 데스크톱 작업 활성화를 참조하십시오.](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2)

![데스크탑 앱 작업 시 바로 가기를 사용할 수 있도록 데스크탑 작업 활성화](assets/enable_desktop_actions.png)

### Adobe 자산 링크 {#configure-asset-link} 사용 구성

Adobe Asset Link를 사용하면 컨텐츠 제작 과정에서 크리에이티브 팀과 마케터 간의 공동 작업을 간소화할 수 있습니다. Adobe Experience Manager(AEM) 에셋을 Creative Cloud 데스크탑 앱인 Adobe InDesign, Adobe Photoshop 및 Adobe Illustrator과 연결할 수 있습니다. 크리에이티브 전문가는 Adobe 에셋 링크 패널을 통해 가장 익숙한 크리에이티브 앱을 종료하지 않고도 AEM Assets에 저장되어 있는 컨텐츠에 액세스하고 수정할 수 있습니다.

Adobe 자산 링크[에 사용할 AEM을 구성하는 방법을 참조하십시오.](https://helpx.adobe.com/kr/enterprise/using/configure-aem-assets-for-asset-link.html)

## 우수 사례 및 문제 해결 {#bestpractices}

* 이름에 공백이 포함된 자산 폴더 또는 컬렉션은 공유되지 않을 수 있습니다.
* 사용자가 공유 자산을 다운로드할 수 없는 경우 AEM 관리자에게 [다운로드 제한](#maxdatasize)이 무엇인지 문의하십시오.

<!--
* If you cannot send email with links to shared assets or if the other users cannot receive your email, check with your AEM administrator if the [email service](/help/assets/configure-asset-sharing.md#configmailservice) is configured or not. 
* If you cannot share assets using link sharing functionality, ensure that you have the appropriate permissions. See [share assets](#sharelink).
-->

<!-- TBD: Add content or link about how to share using Brand Portal when it is available on [!DNL Cloud Service].
-->
