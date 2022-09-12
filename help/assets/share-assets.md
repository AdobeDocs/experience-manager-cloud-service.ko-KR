---
title: 자산, 폴더 및 컬렉션 분배 및 공유
description: 링크로 공유, 다운로드 및 와 같은 방법을 사용하여 디지털 자산을 배포합니다 [!DNL Brand Portal], [!DNL desktop app], 및 [!DNL Asset Link].
contentOwner: Vishabh Gupta
feature: Asset Management, Collaboration, Asset Distribution
role: User, Admin
exl-id: 14e897cc-75c2-42bd-8563-1f5dd23642a0
source-git-commit: 86bf6ba711740bd4c39070c2fa600d23f201ee7e
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 3%

---

# 에서 관리하는 자산 공유 및 분배 [!DNL Experience Manager] {#share-assets-from-aem}

[!DNL Adobe Experience Manager Assets] 자산, 폴더 및 컬렉션을 조직 및 외부 엔티티(파트너 및 공급업체 등)의 멤버와 공유할 수 있습니다. 다음 메서드를 사용하여 자산을 공유하십시오 [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service]:

* [링크로 공유](#sharelink).
* [자산 다운로드](/help/assets/download-assets-from-aem.md) 공유할 수도 있습니다.
* 공유 사용 [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html).
* 공유 사용 [[!DNL Adobe Asset Link]](https://www.adobe.com/kr/creativecloud/business/enterprise/adobe-asset-link.html).
* 공유 사용 [[!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html).

## 링크로 자산 공유 {#sharelink}

링크를 통해 자산을 공유하는 것은 외부 당사자, 마케터 및 기타 사용자가 리소스를 사용할 수 있도록 하는 편리한 방법입니다 [!DNL Experience Manager] 사용자 참조. 기능을 사용하면 익명의 사용자가 공유된 자산에 액세스하고 다운로드할 수 있습니다. 공유 링크에서 자산을 다운로드할 때는, [!DNL Experience Manager Assets] 는 빠르고 중단 없는 다운로드를 제공하는 비동기 서비스를 사용합니다. 다운로드할 자산은 백그라운드에서 관리할 수 있는 파일 크기의 ZIP 아카이브로 대기합니다. 대규모 다운로드의 경우 이 다운로드는 파일 크기보다 100GB의 여러 파일로 번들로 제공됩니다.

<!--
Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. 
-->

>[!NOTE]
>
>* 링크로 공유할 폴더 또는 자산에 대한 ACL 편집 권한이 필요합니다.
>* [아웃바운드 이메일 활성화](/help/implementing/developing/introduction/development-guidelines.md#sending-email) 사용자와 링크를 공유하기 전에


링크 공유 기능을 사용하여 자산을 공유하는 두 가지 방법이 있습니다.

1. 공유 링크 생성, [자산 링크 복사 및 공유](#copy-and-share-assets-link) 다른 사용자와 공유할 수 있습니다. 링크의 기본 만료 시간은 하루입니다. 복사된 링크를 다른 사용자와 공유할 때에는 만료 시간을 변경할 수 없습니다.

1. 공유 링크 생성 및 [이메일을 통해 자산 링크 공유](#share-assets-link-through-email). 이 경우 만료 날짜 및 시간과 같은 기본값을 수정하고 원래 자산 및 해당 표현물을 다운로드할 수 있습니다. 이메일 주소를 추가하여 여러 사용자에게 이메일을 보낼 수 있습니다.

![링크 공유 대화 상자](assets/link-sharing-dialog.png)

### 자산 링크 복사 및 공유{#copy-and-share-asset-link}

자산을 공개 URL로 공유하려면:

1. 에 로그인합니다. [!DNL Experience Manager Assets] 및 **[!UICONTROL 파일]**.
1. 자산이 들어 있는 자산 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 링크 공유]**.
1. 다음 **[!UICONTROL 링크 공유]** 에 자동 생성된 자산 링크가 포함된 대화 상자가 나타납니다 **[!UICONTROL 링크 공유]** 필드.
1. 자산 링크를 복사하여 사용자와 공유합니다.

### 이메일 알림을 통해 자산 링크 공유 {#share-assets-link-through-email}

이메일을 통해 자산을 공유하려면 다음을 수행하십시오.

1. 자산이 들어 있는 자산 또는 폴더를 선택합니다. 도구 모음에서 **[!UICONTROL 링크 공유]**.
1. 다음 **[!UICONTROL 링크 공유]** 에 자동 생성된 자산 링크가 포함된 대화 상자가 나타납니다 **[!UICONTROL 링크 공유]** 필드.

   * 이메일 주소 상자에 링크를 공유할 사용자의 이메일 ID를 입력합니다. You can share the link with multiple users. 사용자가 조직의 구성원인 경우 드롭다운 목록에 나타나는 제안에서 이메일 ID를 선택합니다. 사용자가 외부 사용자라면 전체 이메일 ID를 입력하고 키를 누릅니다 **[!UICONTROL Enter 키]**; 이메일 ID가 사용자 목록에 추가됩니다.

   * 에서 **[!UICONTROL 제목]** 상자에서 공유할 자산의 용도를 지정할 제목을 입력합니다.
   * 에서 **[!UICONTROL 메시지]** 상자에 필요한 경우 메시지를 입력합니다.
   * 에서 **[!UICONTROL 만료]** 필드에서 날짜 선택기를 사용하여 링크에 대한 만료 날짜 및 시간을 지정합니다.
   * 를 활성화합니다 **[!UICONTROL 원본 파일 다운로드 허용]** 수신자가 원본 변환을 다운로드할 수 있도록 하는 확인란을 선택합니다.

1. **[!UICONTROL 공유]**&#x200B;를 클릭합니다. 링크가 사용자와 공유되는지 확인하는 메시지가 나타납니다. 사용자는 공유 링크가 포함된 이메일을 받게 됩니다.

![링크 공유 전자 메일](assets/link-sharing-email-notification.png)

### 자산 링크를 사용하여 자산 다운로드

공유 자산 링크에 액세스할 수 있는 모든 사용자는 zip 폴더에 번들로 제공되는 자산을 다운로드할 수 있습니다. 다운로드 프로세스는 사용자가 복사된 자산 링크에 액세스하는지 또는 이메일을 통해 공유되는 자산 링크를 사용하는지 여부에 관계없이 동일합니다.

* 자산 링크를 클릭하거나 브라우저에 URL을 붙여넣습니다. 다음 [!UICONTROL 링크 공유] 인터페이스 열기 [!UICONTROL 카드 보기] 또는 [!UICONTROL 목록 보기].

* 에서 [!UICONTROL 카드 보기]를 클릭하고 공유 자산 또는 공유 자산 폴더 위로 마우스를 가져가면 자산을 선택하거나 큐에 올릴 수 있습니다.

* 기본적으로 사용자 인터페이스에 **[!UICONTROL 받은 편지함 다운로드]** 선택 사항입니다. 다운로드 큐에 있는 모든 공유 자산 또는 폴더의 목록과 해당 상태를 반영합니다.

* 자산 또는 폴더를 선택할 때 **[!UICONTROL 큐 다운로드]** 옵션이 화면에 표시됩니다. 을(를) 클릭합니다. **[!UICONTROL 큐 다운로드]** 다운로드 프로세스를 시작하는 옵션.

   ![큐 다운로드](assets/queue-download.png)

* 다운로드 파일이 준비되면 **[!UICONTROL 받은 편지함 다운로드]** 다운로드 상태를 보는 옵션. 대규모 다운로드의 경우 **[!UICONTROL 새로 고침]** 단추를 클릭하여 상태를 업데이트합니다.

   ![받은 편지함 다운로드](assets/link-sharing-download-inbox.png)

* 처리가 완료되면 **[!UICONTROL 다운로드]** 단추를 클릭하여 zip 파일을 다운로드합니다.

<!--
You can also copy the auto-generated link and share it with the users. The default expiration time for the link is one day.
-->

>[!NOTE]
>
>공유 자산이 다른 위치로 이동되면 해당 링크가 작동하지 않습니다. 링크를 다시 만들고 사용자와 다시 공유합니다.


<!--
## Share assets as a link {#sharelink}

To generate the URL for assets you want to share with users, use the Link Sharing dialog. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Sharing assets through a link is a convenient way of making resources available to external parties without them having to first log in to Experience Manager Assets.

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

   For the local and author properties, provide the URL for the local and author instance respectively. Both local and author properties have the same value if you run a single Experience Manager author instance. For publish, provide the URL for the publish instance.

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
   >Experience Manager supports generating the preview of assets of these MIME types: JPG, PNG, GIF, BMP, INDD, PDF, and PPT. You can only download the assets of the other MIME types.

1. To download the shared asset, click/tap **[!UICONTROL Select]** from the toolbar, click/tap the asset, and then click/tap **[!UICONTROL Download]** from the toolbar.
1. To view the assets you shared as links, go to the Assets user interface and click/tap the GlobalNav icon. Choose **[!UICONTROL Navigation]** from the list to display the Navigation pane.
1. From the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.
1. To un-share an asset, select it and tap/click **[!UICONTROL Unshare]** from the toolbar.

A message confirms that you unshared the asset. In addition, the entry for the asset is removed from the list.
-->

## 자산을 다운로드하고 별도로 공유 {#download-and-share-assets}

사용자는 필요한 자산을 다운로드하고 외부에서 공유할 수 있습니다 [!DNL Experience Manager]. 자세한 내용은 [자산을 검색하는 방법](/help/assets/search-assets.md), [자산을 다운로드하는 방법](/help/assets/download-assets-from-aem.md), 및 [컬렉션을 다운로드하는 방법](manage-collections.md#download-a-collection)

## 크리에이티브 전문가와 자산 공유 {#share-with-creatives}

마케터와 사업 부문 사용자는

* **Experience Manager 데스크탑 앱**: 이 앱은 Windows 및 Mac에서 작동합니다. 자세한 내용은 [데스크탑 앱 개요](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html). 권한이 있는 데스크톱 사용자가 공유 자산에 쉽게 액세스할 수 있는 방법을 알아보려면 [자산 찾아보기, 검색 및 미리 보기](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets). 데스크탑 사용자는 새 이미지를 업로드하여 자산을 만들고 Experience Manager 사용자인 해당 사용자와 다시 공유할 수 있습니다. 자세한 내용은 [데스크탑 앱을 사용하여 자산 업로드](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

* **Adobe 자산 링크**: 크리에이티브 전문가가 내에서 직접 자산을 검색하고 사용할 수 있습니다 [!DNL Adobe InDesign], [!DNL Adobe Illustrator], 및 [!DNL Adobe Photoshop].

## 자산 공유 구성 {#configure-sharing}

자산을 공유하는 다른 옵션은 특정 구성이 필요하며 특정 사전 요구 사항이 있습니다.

### 자산 링크 공유 구성 {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

사용자와 공유할 자산의 URL을 생성하려면 링크 공유 대화 상자를 사용합니다. 관리자 권한이 있거나 `/var/dam/share` 위치는 공유된 링크를 볼 수 있습니다. 링크를 통해 자산을 공유하는 것은 처음 로그인하지 않고도 외부 당사자가 리소스를 사용할 수 있도록 하는 편리한 방법입니다 [!DNL Assets].

>[!NOTE]
>
>작성자 인스턴스의 링크를 외부 엔티티에 공유하려면 다음 URL만 표시해야 합니다 `GET` 요청. 다른 URL을 차단하여 작성자 인스턴스가 안전한지 확인합니다.
>
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


<!--
## Configure Day CQ mail service {#configmailservice}

Before you can share assets as links, configure the email service.

1. Click or tap the Experience Manager logo, and then navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
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

When you download assets from the link shared using the Link Sharing feature, Experience Manager compresses the asset hierarchy from the repository and then returns the asset in a ZIP file. However, in the absence of limits to the amount of data that can be compressed in a ZIP file, huge amounts of data is subjected to compression, which causes out of memory errors in JVM. To secure the system from a potential denial of service attack due to this situation, you can configure the maximum size of the downloaded files. If uncompressed size of the asset exceeds the configured value, asset download requests are rejected. The default value is 100 MB.

1. Click/Tap the Experience Manager logo and then go to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. From the web console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Open the configuration in edit mode, and modify the value of the **[!UICONTROL Max Content Size (uncompressed)]** parameter.
1. Save the changes.
-->

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->

### 데스크탑 앱에서 사용할 데스크탑 작업 활성화 {#desktop-actions}

에서 [!DNL Assets] 브라우저의 사용자 인터페이스에서 자산 위치를 탐색하거나 체크 아웃하고 데스크탑 애플리케이션에서 편집할 자산을 열 수 있습니다. 이러한 옵션을 데스크톱 작업이라고 하며 사용하려면 다음을 참조하십시오 [데스크탑 작업 사용 [!DNL Assets] 웹 인터페이스](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2).

![데스크탑 앱을 사용할 때 바로 가기로 사용할 데스크탑 작업 활성화](assets/enable_desktop_actions.png)

### 사용할 구성 [!DNL Adobe Asset Link] {#configure-asset-link}

Adobe 자산 링크를 사용하면 컨텐츠 작성 프로세스에서 광고 팀과 마케터 간의 협업을 간소화할 수 있습니다. 연결 [!DNL Adobe Experience Manager Assets] with [!DNL Creative Cloud] 데스크탑 앱 [!DNL Adobe InDesign], [!DNL Adobe Photoshop], 및 [!DNL Adobe Illustrator]. 다음 [!DNL Adobe Asset Link] 패널에서는 크리에이티브 전문가가 [!DNL Assets] 친숙한 크리에이티브 앱을 종료하지 않고

자세한 내용은 [구성 방법 [!DNL Assets] 와 함께 사용 [!DNL Adobe Asset Link]](https://helpx.adobe.com/kr/enterprise/using/configure-aem-assets-for-asset-link.html).

## 우수 사례 및 문제 해결 {#bestpractices}

* 이름에 공백이 포함된 자산 폴더 또는 컬렉션은 공유되지 않을 수 있습니다.
* 사용자가 공유 자산을 다운로드할 수 없는 경우 Experience Manager 관리자에게 문의하여 다음 내용을 확인하십시오 [다운로드 제한](#maxdatasize) 입니다.
* 사용자가 링크 공유를 사용하여 공유되는 비디오를 미리 보려면 비디오에 사용 가능한 정적 비디오 표현물이 있어야 합니다. `/jcr:content/renditions` 저장소의 비디오 노드에 있는 위치입니다. 미리 보기는 사용 가능 여부에 따라 달라지지 않습니다 [!DNL Dynamic Media] 변환.
* 링크 공유를 통해 비디오 자산을 다운로드할 때는, [!DNL Dynamic Media] 표현물은 다운로드한 보관소에 포함되지 않습니다.

<!--
* If you cannot send email with links to shared assets or if the other users cannot receive your email, check with your Experience Manager administrator if the [email service](/help/assets/configure-asset-sharing.md#configmailservice) is configured or not. 
* If you cannot share assets using link sharing functionality, ensure that you have the appropriate permissions. See [share assets](#sharelink).
-->

<!-- TBD: Add content or link about how to share using Brand Portal when it is available on [!DNL Cloud Service].
-->
