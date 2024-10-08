---
title: 비디오 자산 관리
description: ' [!DNL Adobe Experience Manager]에서 비디오 자산을 업로드, 미리 보기, 주석 달기 및 게시합니다.'
contentOwner: AG
feature: Asset Management, Publishing, Collaboration, Video
role: User
exl-id: 91edce4a-dfa0-4eca-aba7-d41ac907b81e
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '5001'
ht-degree: 6%

---

# 비디오 자산 관리 {#manage-video-assets}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-video-assets.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

비디오 형식은 조직의 디지털 에셋에 중요한 부분입니다. [!DNL Adobe Experience Manager]은(는) 생성 후 비디오 자산의 전체 라이프사이클을 관리하는 완성도 높은 서비스와 기능을 제공합니다.

[!DNL Adobe Experience Manager Assets]에서 비디오 자산을 관리하고 편집하는 방법에 대해 알아봅니다. 비디오 인코딩 및 코드 변환(예: FFmpeg 코드 변환)은 처리 프로필 및 [!DNL Dynamic Media] 통합을 사용하여 가능합니다. [!DNL Dynamic Media] 라이선스가 없으면 [!DNL Experience Manager]은(는) FFmpeg를 사용한 코드 변환, 지원되는 파일 형식에 대한 미리 보기 썸네일 추출, 브라우저에서 직접 재생할 수 있는 형식에 대한 사용자 인터페이스 미리 보기와 같은 비디오를 기본적으로 지원합니다.

## 비디오 자산 업로드 및 미리 보기 {#upload-and-preview-video-assets}

지원되는 형식의 비디오 자산을 [!DNL Experience Manager Assets]에 업로드하고 미리 볼 수 있습니다.
<!-- It generates previews for video assets with the extension MP4. -->

### 비디오 자산 업로드

비디오 자산을 업로드하려면 다음 단계를 따르십시오.

1. 디지털 에셋 폴더 또는 하위 폴더에서 에셋을 추가해야 하는 위치로 이동합니다.
1. 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭하고 **[!UICONTROL 파일]**&#x200B;을 선택합니다. <br>또는 사용자 인터페이스에서 파일을 끌어 놓으십시오.
[!DNL Experience Manager Assets]에서 [자산 업로드](manage-digital-assets.md#uploading-assets)에 대해 자세히 알아보세요.

<!-- 1. To preview a video in the card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. You can pause or play video in the card view only. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.
1. To preview the video in the asset details page, select **[!UICONTROL Edit]** on the card. The video plays in the native video player of the browser. You can play, pause, control the volume, and zoom the video to full screen. -->

### 비디오 자산 미리 보기

[!DNL Assets] 사용자 인터페이스에서 지원되는 표현물로 비디오를 미리 볼 수 있습니다. 비디오 자산을 미리 보려면 다음 단계를 따르십시오.

1. 지원되는 형식의 비디오 자산을 [!DNL Experience Manager Assets]에 업로드합니다. [지원되는 비디오 형식](file-format-support.md#video-formats)에 대해 자세히 알아보세요. <br>업로드되면 비디오 자산이 처리되고 미리 보기 렌디션이 생성됩니다.
1. 자산을 클릭하고 상단 도구 모음에서 ![세부 정보 옵션](assets/do-not-localize/details_icon.svg) **[!UICONTROL 세부 정보]**&#x200B;을 선택합니다. 비디오 에셋이 비디오 뷰어에서 열립니다.
1. 비디오 썸네일에서 ![재생 옵션](assets/do-not-localize/play.png) 아이콘을 클릭합니다. <br>재생, 일시 중지, 볼륨 조절 및 비디오 전체 화면으로 확대/축소할 수 있습니다.

[!DNL Experience Manager Assets]의 기존 비디오 자산에 대해 비디오 미리 보기 기능을 사용하려면 [!DNL Experience Manager]의 자산을 **[!UICONTROL 재처리]**&#x200B;해야 합니다. [!DNL Experience Manager]에서 [디지털 자산을 재처리](reprocessing.md)하는 방법에 대해 알아봅니다.

### 비디오 미리보기의 제한 사항

* 렌디션이 생성되더라도 MXF 파일에는 비디오 미리보기가 표시되지 않습니다.
* WebM 파일은 웹 브라우저에서 기본적으로 재생할 수 있으므로 미리 보기 변환을 생성하지 않습니다.

## Publish 비디오 자산 {#publish-video-assets}

게시 후 웹 페이지에 비디오 자산을 URL로 포함하거나 자산을 직접 포함할 수 있습니다. 자세한 내용은 [게시 [!DNL Dynamic Media] 자산](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)을 참조하세요.

## YouTube에 Publish 비디오 {#publishing-videos-to-youtube}

Experience Manager Assets에서 관리하는 비디오 자산을 이전에 만든 YouTube 채널에 직접 게시할 수 있습니다.

비디오 에셋을 YouTube에 게시하려면 Experience Manager Assets의 비디오 에셋에 태그를 지정합니다. 이러한 태그를 YouTube 채널과 연결합니다. 비디오 에셋의 태그가 YouTube 채널의 태그와 일치하는 경우 비디오는 YouTube에 게시됩니다. Publish to YouTube은 연결된 태그가 사용되는 한 비디오의 일반 게시와 함께 발생합니다.

YouTube은 자체 인코딩을 수행합니다. 따라서 Experience Manager에 업로드된 원본 비디오 파일은 Dynamic Media의 인코딩으로 만들어진 비디오 렌디션 대신 YouTube에 게시됩니다. Dynamic Media을 사용하여 비디오를 처리할 필요는 없지만, 재생에 뷰어 사전 설정이 필요한 경우 처리할 수 있습니다.

비디오 처리 프로필을 건너뛰고 YouTube에 바로 게시할 때 Experience Manager 에셋의 비디오 에셋에 볼 수 있는 썸네일이 표시되지 않는다는 의미입니다. 또한 인코딩되지 않은 비디오는 Dynamic Media 에셋 유형에서 작동하지 않습니다.

YouTube 서버에 비디오 자산을 게시하려면 YouTube을 사용하여 안전하고 안전한 서버 간 확인을 위해 다음 작업을 완료해야 합니다.

1. [Google 클라우드 설정 구성](#configuring-google-cloud-settings)
1. [YouTube 채널 만들기](#creating-a-youtube-channel)
1. [게시용 태그 추가](#adding-tags-for-publishing)
1. [Experience Manager에서 YouTube 설정](#setting-up-youtube-in-aem)
1. [(선택 사항) 업로드한 비디오에 대한 기본 YouTube 속성 설정을 자동화합니다](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [YouTube 채널에 Publish 비디오](#publishing-videos-to-your-youtube-channel)
1. [(선택 사항) YouTube에서 게시된 비디오를 확인합니다](/help/assets/dynamic-media/video.md#optional-verifying-the-published-video-on-youtube)
1. [웹 애플리케이션에 YouTube URL 연결](#linking-youtube-urls-to-your-web-application)

비디오를 [게시 취소하여 YouTube에서 제거할 수도 있습니다](#unpublishing-videos-to-remove-them-from-youtube).

### Google 클라우드 설정 구성 {#configuring-google-cloud-settings}

YouTube에 게시하려면 Google 계정이 필요합니다. GMAIL 계정이 있으면 이미 Google 계정이 있는 것입니다. Google 계정이 없으면 쉽게 만들 수 있습니다. 비디오 자산을 YouTube에 게시하려면 자격 증명이 필요하므로 계정이 필요합니다. <!-- hidden March 3 2022 If you have an account already created, then skip this task and proceed directly to [Create a YouTube channel](#creating-a-youtube-channel). -->

Google Cloud와 함께 사용되는 계정과 YouTube에 사용되는 Google 계정이 동일할 필요는 없습니다.

Google은 정기적으로 사용자 인터페이스를 변경합니다. 따라서 비디오를 YouTube에 게시하는 단계는 아래에 문서화된 것과 약간 다를 수 있습니다. 이 주의사항은 비디오가 YouTube에 업로드되었는지 확인하려고 할 때도 적용됩니다.

>[!NOTE]
>
>다음의 단계는 글을 쓸 때 정확했다. 그러나 Google은 예고 없이 정기적으로 클라우드 웹 페이지를 업데이트합니다. 따라서 일부 구성 옵션은 Google 사용자 인터페이스에서 단계에 사용된 이름과 약간 다르게 명명될 수 있습니다.

**Google Cloud 설정을 구성하려면:**

1. Google 계정을 만듭니다.

   이미 Google 계정이 있는 경우 다음 단계로 건너뛸 수 있습니다.

1. [https://cloud.google.com/](https://cloud.google.com/)(으)로 이동합니다.
1. **[!UICONTROL Google 클라우드]** 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 콘솔]**&#x200B;을 선택합니다.

   필요한 경우 Google 계정 자격 증명을 사용하여 **[!UICONTROL 로그인]**&#x200B;하여 **[!UICONTROL 콘솔]** 옵션을 봅니다.

1. **[!UICONTROL 대시보드]** 페이지의 **[!UICONTROL Google Cloud Platform]** 오른쪽에서 **[!UICONTROL 프로젝트]** 드롭다운 목록을 선택하여 **[!UICONTROL 프로젝트 선택]** 대화 상자를 엽니다.
1. **[!UICONTROL 프로젝트 선택]** 대화 상자에서 **[!UICONTROL 새 프로젝트]**&#x200B;를 선택합니다.
1. **[!UICONTROL 새 프로젝트]** 대화 상자의 **[!UICONTROL 프로젝트 이름]** 필드에 새 프로젝트의 이름을 입력합니다.

   프로젝트 ID는 프로젝트 이름을 기반으로 합니다. 따라서 프로젝트 이름을 신중하게 선택하십시오. 생성된 후에는 변경할 수 없습니다. 또한 나중에 Experience Manager에서 YouTube을 설정할 때 동일한 프로젝트 ID를 다시 입력해야 합니다. 그러므로, 적어 두십시오.

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

1. 다음 중 하나를 수행합니다.

   * 프로젝트의 대시보드의 **[!UICONTROL 시작하기]** 카드에서 **[!UICONTROL API 탐색 및 활성화]**&#x200B;를 선택합니다.
   * 프로젝트의 대시보드의 **[!UICONTROL API]** 카드에서 **[!UICONTROL API 개요로 이동]**&#x200B;을 선택합니다.

1. **[!UICONTROL API 및 서비스]** 페이지의 상단 가운데 가까이에서 **[!UICONTROL API 및 서비스 사용]**&#x200B;을 선택합니다.<!-- NEXT STEP BELOW IS STEP 10 -->
1. **[!UICONTROL API 라이브러리]** 페이지의 왼쪽의 **[!UICONTROL 카테고리]**&#x200B;에서 **[!UICONTROL YouTube]**&#x200B;을(를) 선택합니다. 페이지 오른쪽에서 **[!UICONTROL YouTube]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL YouTube]** 페이지에서 **[!UICONTROL YouTube Data API v3]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL YouTube 데이터 API v3]** 페이지에서 **[!UICONTROL 관리]**&#x200B;를 선택합니다.

   ![6_5_googleaccount-apis-manage](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-manage.png)

1. API를 사용하려면 자격 증명이 필요합니다. 필요한 경우 **[!UICONTROL API 및 서비스]** 페이지 왼쪽에서 **[!UICONTROL 자격 증명]**&#x200B;을(를) 선택하십시오.
1. **[!UICONTROL 자격 증명]** 페이지의 맨 위에서 **[!UICONTROL 자격 증명 만들기]**&#x200B;를 선택한 다음 **[!UICONTROL OAuth 클라이언트 ID]**&#x200B;를 선택합니다.
1. **[!UICONTROL OAuth 클라이언트 ID 만들기]** 페이지의 **[!UICONTROL 응용 프로그램 유형]** 드롭다운 목록에서 **[!UICONTROL 웹 응용 프로그램]**&#x200B;을 선택합니다.

   ![6_5_googleaccount-apis-applicationtype](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-applicationtype.png)

1. 다음 중 하나를 수행하십시오.

   * **[!UICONTROL 이름]** 필드에 OAuth 2.0 클라이언트의 고유한 이름을 입력합니다.
   * Google이 **[!UICONTROL 이름]** 필드에 이미 제공한 기본 이름을 사용하십시오.

1. **[!UICONTROL 인증된 JavaScript 원본]** 제목에서 **[!UICONTROL URI 추가]**&#x200B;를 선택합니다.

   ![6_5_googleaccount-apis-nameauthorizations](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-nameauthorizations.png)

1. **[!UICONTROL URI]** 텍스트 필드에 다음 경로를 입력하여 경로에 고유한 도메인과 포트 번호를 대체한 다음 **[!UICONTROL Enter]**&#x200B;를 눌러 목록에 경로를 추가합니다.

   `https://<servername.domain>:<port_number>`

   예, `https://1a2b3c.mycompany.com:4321`

   >[!NOTE]
   >
   >위의 URI 경로 예는 가정적이며 설명 목적으로만 사용됩니다.

1. **[!UICONTROL 승인된 리디렉션 URI]** 제목에서 URI 추가를 선택합니다.
1. **[!UICONTROL URI]** 텍스트 필드에 다음 경로를 입력하여 경로에 고유한 도메인과 포트 번호를 대체한 다음 **[!UICONTROL Enter]**&#x200B;를 눌러 목록에 경로를 추가합니다.

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   예, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   >[!NOTE]
   >
   >위의 URI 경로 예는 가정적이며 설명 목적으로만 사용됩니다.

1. **[!UICONTROL OAuth 클라이언트 ID 만들기]** 페이지 아래쪽에서 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 생성된 OAuth 클라이언트]** 대화 상자에서 다음을 수행합니다.

   * (선택 사항) **[!UICONTROL 클라이언트 ID]** 및 **[!UICONTROL 클라이언트 암호]** 필드의 값을 복사한 다음 저장합니다.
   * **[!UICONTROL JSON 다운로드]**&#x200B;를 선택한 다음 JSON 파일을 저장합니다.

   나중에 Adobe Experience Manager에서 YouTube을 설정할 때 이 다운로드한 JSON 파일이 필요합니다.

   ![6_5_googleaccount-apis-oauthclientcreated](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-oauthclientcreated.png)

1. **[!UICONTROL 생성된 OAuth]** 대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 선택합니다.
1. Google 계정에서 로그아웃합니다. 이제 YouTube 채널을 만듭니다.

### YouTube 채널 만들기 {#creating-a-youtube-channel}

YouTube에 비디오를 게시하려면 하나 이상의 채널이 필요합니다. 이미 YouTube 채널을 만든 경우 이 작업을 건너뛰고 [게시할 태그 추가](/help/assets/dynamic-media/video.md#adding-tags-for-publishing)(으)로 이동할 수 있습니다.

>[!CAUTION]
>
>YouTube에서 이미 하나 이상의 채널을 설정했는지 확인하세요. *이전* Experience Manager의 YouTube 설정에서 채널을 추가합니다(아래 [Experience Manager에서 YouTube 설정](#setting-up-youtube-in-aem) 참조). 채널 설정을 수행하지 않으면 기존 채널이 없다는 경고가 표시되지 않습니다. 그러나 채널을 추가할 때 Google 확인은 계속 실행되지만 비디오를 전송할 채널을 선택할 수 있는 옵션은 없습니다.

**YouTube 채널을 만들려면:**

1. [https://www.youtube.com](https://www.youtube.com/)(으)로 이동한 다음 Google 계정 자격 증명을 사용하여 로그인합니다.
1. YouTube 페이지의 오른쪽 상단 모서리에서 프로필 사진을 선택한 다음(단색 원 안에 글자로 표시될 수도 있음) **[!UICONTROL YouTube 설정]**(원형 톱니바퀴 아이콘)을 선택합니다.
1. 개요 페이지의 추가 기능 제목 아래에서 **[!UICONTROL 모든 채널 보기 또는 채널 만들기]**&#x200B;를 선택합니다.
1. 채널 페이지에서 **[!UICONTROL 새 채널 만들기]**&#x200B;를 선택합니다.
1. [브랜드 계정] 페이지의 [브랜드 계정 이름] 필드에 비디오 자산을 게시할 위치를 선택한 회사 이름이나 다른 채널 이름을 입력한 다음 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   여기에 입력한 이름을 기억하십시오. Experience Manager에서 YouTube을 설정해야 할 때 다시 입력해야 합니다.

1. (선택 사항) 필요한 경우 더 많은 채널을 추가합니다.

   이제 게시할 태그를 추가합니다.

### 게시용 태그 추가 {#adding-tags-for-publishing}

비디오에 YouTube을 게시하려면 Experience Manager이 태그를 하나 이상의 YouTube 채널에 연결합니다. 게시할 태그를 추가하려면 [태그 관리](/help/sites-cloud/authoring/sites-console/tags.md)를 참조하십시오.

또는 Experience Manager에서 기본 태그를 사용하려는 경우 이 작업을 건너뛰고 [Experience Manager에서 YouTube 설정](#setting-up-youtube-in-aem)(으)로 이동할 수 있습니다.

>[!NOTE]
>
>Cloud Service이 구성된 후에는 이 시점에서 YouTube Publish 복제 에이전트를 활성화하는 데 다른 구성이 필요하지 않습니다. 이는 Cloud Service 구성을 저장할 때 활성화되었기 때문입니다.

<!-- ### Enabling the YouTube Publish replication agent {#enabling-the-youtube-publish-replication-agent}

After you enable the YouTube Publish replication agent, if you want to test the connection to the Google Cloud account, select **[!UICONTROL Test Connection]**. A browser tab displays the connection results. If you have added YouTube Channels, then a listing of those is displayed as part of the test.

1. In the upper-left corner of Experience Manager, select the Experience Manager logo, then in the left rail, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. On the Agents of Author page, select **[!UICONTROL YouTube Publish (youtube)]**.
1. On the toolbar, to the right of Settings, select **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Enabled]** checkbox to turn on the replication agent.
1. Select **[!UICONTROL OK]**. -->

### Experience Manager에서 YouTube 설정 {#setting-up-youtube-in-aem}

Experience Manager 6.4부터 새로운 터치 Experience Manager 인터페이스 방식이 도입되어 YouTube에서 게시를 설정할 수 있습니다. 사용 중인 Experience Manager의 설치된 인스턴스를 기반으로 다음 중 하나를 수행합니다.

* 6.4 이전 Experience Manager에서 YouTube을 구성하려면 [6.4 이전 Experience Manager에서 YouTube 설정](/help/assets/dynamic-media/video.md#setting-up-youtube-in-aem-before)을 참조하십시오.
* Experience Manager 6.4 이상에서 YouTube을 구성하려면 [Experience Manager 6.4 이상에서 YouTube 설정](#setting-up-youtube-in-aem-and-later)을 참조하십시오.

#### Experience Manager 6.4 이상에서 YouTube 설정 {#setting-up-youtube-in-aem-and-later}

1. Dynamic Media 인스턴스에 관리자로 로그인해야 합니다.
1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 **[!UICONTROL 도구]**(망치 아이콘) > **[!UICONTROL Cloud Service]** > **[!UICONTROL YouTube 게시 구성]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 전역]**&#x200B;을(를) 선택하십시오(선택하지 마십시오).

1. 전역 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. On the Create YouTube Configuration page, under Google Cloud Platform Settings, in the **[!UICONTROL Application Name]** field, enter the Google Project ID.

   이전에 Google Cloud 설정을 처음 구성할 때 프로젝트 ID를 지정했습니다.
YouTube 구성 만들기 페이지를 열어 두십시오. 잠시 후 다시 돌아갑니다.

   ![6_5_youtubepublish-createyoutubeconfiguration](/help/assets/dynamic-media/assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. 일반 텍스트 편집기를 사용하여 [Google Cloud 설정 구성](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings) 작업에서 이전에 다운로드하여 저장한 JSON 파일을 엽니다.
1. 전체 JSON 텍스트를 선택하고 복사합니다.
1. Return to the YouTube Account Settings dialog box. In the **[!UICONTROL JSON Config]** field, paste the JSON text.
1. 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

   이제 Experience Manager에서 YouTube 채널을 설정합니다.

1. **[!UICONTROL 채널 추가]**&#x200B;를 선택합니다.
1. [채널 이름] 필드에 이전에 **[!UICONTROL YouTube에 하나 이상의 채널을 추가]**&#x200B;하는 작업에서 만든 채널의 이름을 입력합니다.

   원할 경우 선택적으로 설명을 추가할 수 있습니다.

1. **[!UICONTROL 추가]**&#x200B;를 선택합니다.
1. YouTube/Google 확인이 표시됩니다. Google Cloud 계정에 아직 로그인하지 않은 경우 이 단계를 건너뜁니다.

   * Google 프로젝트 ID와 연결된 Google 사용자 이름 및 암호와 위의 JSON 텍스트를 입력합니다.
   * 계정에 있는 채널의 수에 따라 두 개 이상의 항목이 표시됩니다. 채널을 선택합니다. 이메일 주소는 채널이 아니므로 선택하지 마십시오.
   * 다음 페이지에서 이 채널에 대한 액세스를 허용하려면 **[!UICONTROL 수락]**&#x200B;을 선택하세요.

1. **[!UICONTROL 허용]**&#x200B;을 선택하세요.

   이제 게시할 태그를 설정합니다.

1. **[!UICONTROL 게시할 태그 설정]** - Cloud Service > YouTube 페이지에서 연필 아이콘을 선택하여 사용할 태그 목록을 편집합니다.
1. 사용 가능한 태그 목록을 Experience Manager에 표시하려면 드롭다운 목록 아이콘(거꾸로 삽입 표시)을 선택합니다.
1. 태그를 추가하려면 태그를 하나 이상 선택합니다.

   추가한 태그를 삭제하려면 태그를 선택하고 **[!UICONTROL X]**&#x200B;을(를) 선택합니다.

1. 원하는 태그를 모두 추가했으면 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

   이제 YouTube 채널에 비디오를 게시합니다.

#### 6.4 이전 Experience Manager에서 YouTube 설정 {#setting-up-youtube-in-aem-before}

1. Dynamic Media 인스턴스에 관리자로 로그인해야 합니다.

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 **[!UICONTROL 도구]**(망치 아이콘) > **[!UICONTROL 배포]** > **[!UICONTROL Cloud Service]**&#x200B;로 이동합니다.
1. 서드파티 서비스 제목 아래의 YouTube에서 **[!UICONTROL 지금 구성]**&#x200B;을 선택합니다.
1. 구성 만들기 대화 상자의 각 필드에 제목(필수) 및 이름(선택 사항)을 입력합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. In the YouTube Account Settings dialog box, in the **[!UICONTROL Application Name]** field, enter the Google Project ID.

   처음에 [Google 클라우드 설정을 구성](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings)했을 때 프로젝트 ID를 지정했습니다.
YouTube 계정 설정 대화 상자를 열어 두십시오. 잠시 후 대화 상자로 돌아갑니다.

1. 일반 텍스트 편집기를 사용하여 Google Cloud 설정 구성 작업에서 이전에 다운로드하여 저장한 JSON 파일을 엽니다.
1. 전체 JSON 텍스트를 선택하고 복사합니다.
1. Return to the YouTube Account Settings dialog box. In the **[!UICONTROL JSON Config]** field, paste the JSON text.
1. **[!UICONTROL 확인]**&#x200B;을 선택합니다.

   이제 Experience Manager에서 YouTube 채널을 설정합니다.

1. **[!UICONTROL 사용 가능한 채널]** 오른쪽에서 **+**(더하기 기호 아이콘)을 선택합니다.
1. In the YouTube Channel Settings dialog box, in the Title field, enter the name of the channel that you created in the task **[!UICONTROL Adding one or more channels to YouTube]** earlier.

   원할 경우 선택적으로 설명을 추가할 수 있습니다.

1. **[!UICONTROL 확인]**&#x200B;을 선택합니다.
1. YouTube/Google 확인이 표시됩니다. Google Cloud 계정에 아직 로그인하지 않은 경우 이 단계를 건너뜁니다.

   * Google 프로젝트 ID와 연결된 Google 사용자 이름 및 암호와 위의 JSON 텍스트를 입력합니다.
   * 계정에 있는 채널의 수에 따라 두 개 이상의 항목이 표시됩니다. 채널을 선택합니다. 이메일 주소는 채널이 아니므로 선택하지 마십시오.
   * 다음 페이지에서 이 채널에 대한 액세스를 허용하려면 **[!UICONTROL 수락]**&#x200B;을 선택하세요.

1. **[!UICONTROL 허용]**&#x200B;을 선택하세요.

   이제 게시할 태그를 설정합니다.

1. **[!UICONTROL 게시할 태그 설정]** - Cloud Service > YouTube 페이지에서 연필 아이콘을 선택하여 사용할 태그 목록을 편집합니다.
1. 사용 가능한 태그 목록을 Experience Manager에 표시하려면 드롭다운 목록 아이콘(거꾸로 삽입 표시)을 선택합니다.
1. 태그를 추가하려면 태그를 하나 이상 선택합니다.

   추가한 태그를 삭제하려면 태그를 선택하고 **X**&#x200B;을(를) 선택합니다.

1. 원하는 태그를 모두 추가했으면 **[!UICONTROL 확인]**&#x200B;을 선택합니다.

   이제 YouTube 채널에 비디오를 게시합니다.

### (선택 사항) 업로드한 비디오에 대한 기본 YouTube 속성 설정을 자동화합니다 {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

비디오 업로드 시 YouTube 속성 설정을 선택적으로 자동화할 수 있습니다. Experience Manager에서 메타데이터 처리 프로필을 만듭니다.

To create the metadata processing profile, you are first going to copy values from the **[!UICONTROL Field Label]**, **[!UICONTROL Map to property]**, and **[!UICONTROL Choices]** fields, all found in Metadata Schemas for video. 그런 다음 이러한 값을 추가하여 YouTube 비디오 메타데이터 처리 프로필을 빌드합니다.

**업로드한 비디오에 대한 기본 YouTube 속성 설정을 자동화하려면:**

1. Experience Manager의 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 **[!UICONTROL 도구]**(망치 아이콘) > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.
1. **[!UICONTROL 기본]**&#x200B;을(를) 선택하십시오. (&quot;기본값&quot; 왼쪽에 선택 상자에 확인 표시를 추가하지 마십시오.)
1. **[!UICONTROL 기본]** 페이지에서 **[!UICONTROL 비디오]** 왼쪽에 있는 상자를 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 선택합니다.
1. 메타데이터 스키마 편집기 페이지에서 **[!UICONTROL 고급]** 탭을 선택합니다.
1. YouTube 게시 제목 아래에서 **[!UICONTROL YouTube 범주]**&#x200B;를 선택합니다.
1. 페이지 오른쪽의 **[!UICONTROL 설정]** 탭에서 다음을 수행합니다.

   * **[!UICONTROL 속성에 매핑]** 텍스트 필드에서 값을 선택하고 복사합니다.
복사한 값을 열린 텍스트 편집기에 붙여넣습니다. 나중에 메타데이터 처리 프로필을 만들 때 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

   * **[!UICONTROL 선택 항목]**에서 사용할 기본값(예: 사람 및 블로그 또는 과학 기술)을 선택하고 복사합니다.
복사한 값을 열린 텍스트 편집기에 붙여넣습니다. 나중에 메타데이터 처리 프로필을 만들 때 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

1. YouTube 게시 제목 아래에서 **[!UICONTROL YouTube 개인 정보]**&#x200B;를 선택합니다.
1. 페이지 오른쪽의 **[!UICONTROL 설정]** 탭에서 다음을 수행합니다.

   * **[!UICONTROL 속성에 매핑]** 텍스트 필드에서 값을 선택하고 복사합니다.
복사한 값을 열린 텍스트 편집기에 붙여넣습니다. 나중에 메타데이터 처리 프로필을 만들 때 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

   * **[!UICONTROL 선택 항목]**에서 사용할 기본값을 선택하고 복사합니다. 선택 항목은 두 개의 쌍으로 그룹화됩니다. 쌍의 맨 아래 필드는 복사할 기본값입니다(예: public, unlisted 또는 private).
복사한 값을 열린 텍스트 편집기에 붙여넣습니다. 나중에 메타데이터 처리 프로필을 만들 때 이 값이 필요합니다. 텍스트 편집기를 열어 둡니다.

1. 메타데이터 스키마 편집기 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 취소]**&#x200B;를 선택합니다.
1. Experience Manager 왼쪽 상단 모서리에서 Experience Manager 로고를 선택한 다음 왼쪽 레일에서 **[!UICONTROL 도구]**(망치 아이콘) > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 프로필]**&#x200B;을 선택합니다.

1. 메타데이터 프로필 페이지에서 페이지의 오른쪽 상단 근처에 있는 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. 메타데이터 프로필 추가 대화 상자의 **[!UICONTROL 프로필 제목]** 텍스트 필드에 `YouTube Video` 이름을 입력한 다음 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. 메타데이터 프로필 편집기 페이지에서 **[!UICONTROL 고급]** 탭을 선택합니다.
1. 다음을 수행하여 복사된 YouTube 게시 값을 프로필에 추가합니다.

   * 페이지 오른쪽에서 **[!UICONTROL 양식 작성]** 탭을 선택합니다.
   * (선택 사항) 레이블이 **[!UICONTROL Section Header]**&#x200B;인 구성 요소를 왼쪽으로 드래그하여 양식 영역에 놓습니다.
   * (선택 사항) 구성 요소를 선택하려면 **[!UICONTROL 필드 레이블]**&#x200B;을 선택하십시오.
   * (선택 사항) 페이지 오른쪽의 설정 탭의 필드 레이블 텍스트 필드에 `YouTube Publishing`을(를) 입력합니다.
   * **[!UICONTROL 양식 작성]** 탭을 선택한 다음 **[!UICONTROL 다중 값 텍스트]** 레이블이 지정된 구성 요소를 드래그하여 만든 **[!UICONTROL YouTube 게시]** 머리글 아래에 놓습니다.

   * 구성 요소를 선택하려면 **[!UICONTROL 필드 레이블]**&#x200B;을(를) 선택하십시오.
   * 페이지 오른쪽의 설정 탭 아래에서 이전에 복사한 YouTube Publishing 값(필드 레이블 값 및 속성 값에 매핑)을 양식의 해당 필드에 붙여넣습니다. 선택 항목 값을 기본값 필드에 붙여넣습니다.

1. 다음을 수행하여 복사된 YouTube 개인 정보 보호 값을 프로필에 추가합니다.

   * 페이지 오른쪽에서 **[!UICONTROL 양식 작성]** 탭을 선택합니다.
   * (선택 사항) 레이블이 **[!UICONTROL Section Header]**&#x200B;인 구성 요소를 왼쪽으로 드래그하여 양식 영역에 놓습니다.
   * (선택 사항) 구성 요소를 선택하려면 **[!UICONTROL 필드 레이블]**&#x200B;을 선택하십시오.
   * (선택 사항) 페이지 오른쪽의 설정 탭의 필드 레이블 텍스트 필드에 `YouTube Privacy`을(를) 입력합니다.
   * **[!UICONTROL 양식 작성]** 탭을 선택한 다음 **[!UICONTROL 다중 값 텍스트]** 레이블이 지정된 구성 요소를 드래그하여 만든 **[!UICONTROL YouTube 개인 정보 보호]** 머리글 아래에 놓습니다.

   * 구성 요소를 선택하려면 **[!UICONTROL 필드 레이블]**&#x200B;을(를) 선택하십시오.
   * 페이지 오른쪽의 설정 탭 아래에서 이전에 복사한 YouTube Publishing 값(필드 레이블 값 및 속성 값에 매핑)을 양식의 해당 필드에 붙여넣습니다. 선택 항목 값을 기본값 필드에 붙여넣습니다.

1. 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 저장]**&#x200B;을 선택합니다.
1. 비디오를 업로드할 폴더에 YouTube 게시 메타데이터 프로필을 적용합니다. 메타데이터 프로필과 비디오 프로필을 모두 설정해야 합니다.

   See [Metadata Profiles](/help/assets/metadata-profiles.md) and [Video Profiles](/help/assets/dynamic-media/video-profiles.md).

### YouTube 채널에 Publish 비디오 {#publishing-videos-to-your-youtube-channel}

이제 이전에 비디오 에셋에 추가한 태그를 연결합니다. 이 프로세스를 통해 Experience Manager은 YouTube 채널에 게시할 자산을 알 수 있습니다.

>[!NOTE]
>
>Publish은 즉시 YouTube에 자동으로 게시되지 않습니다. When Dynamic Media is set up, there are two publish options to choose from: **[!UICONTROL Immediately]** or **[!UICONTROL Upon Activation]**.
>
>**[!UICONTROL Publish 즉시]**&#x200B;은(는) 업로드된 에셋이 IPS로 동기화된 후 게재 시스템에 자동으로 게시됨을 의미합니다. Dynamic Media의 경우에는 사실이지만 YouTube의 경우에는 사실이 아닙니다. YouTube에 게시하려면 Experience Manager 작성자를 통해 게시해야 합니다.

>[!NOTE]
>
>YouTube에서 콘텐츠를 게시하기 위해 Experience Manager은 **[!UICONTROL Publish에서 YouTube으로]** 워크플로우를 사용하여 진행 상황을 모니터링하고 오류 정보를 볼 수 있습니다.
>
>[비디오 인코딩 및 YouTube 게시 진행 모니터링](#monitoring-video-encoding-and-youtube-publishing-progress)을 참조하십시오.
>
>자세한 진행 정보는 복제 아래의 YouTube 로그를 모니터링할 수 있습니다. 그러나 이러한 모니터링에는 관리자 액세스 권한이 필요합니다.

**YouTube 채널에 비디오를 게시하려면:**

1. Experience Manager에서 YouTube 채널에 게시하려는 비디오 자산으로 이동합니다.
1. 비디오 자산(응용 비디오 세트)을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
1. [기본] 탭의 [메타데이터] 머리글 아래에서 [태그] 필드 오른쪽에 있는 **[!UICONTROL 선택 대화 상자 열기]**&#x200B;를 선택합니다.
1. 태그 선택 페이지에서 사용할 태그로 이동한 다음 태그를 하나 이상 선택합니다.

   태그는 YouTube 채널과 연결되어 있어야 합니다.

1. 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 선택]**&#x200B;을 선택합니다.
1. 비디오 속성 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다.
1. 도구 모음에서 **[!UICONTROL 빠른 Publish]**&#x200B;를 선택합니다.

   [Experience Manager Sites에서 게시 관리 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html#page-authoring)도 참조하세요.

   YouTube 채널에서 게시된 비디오를 선택적으로 확인할 수 있습니다.

### (선택 사항) YouTube에서 게시된 비디오를 확인합니다 {#optional-verifying-the-published-video-on-youtube}

선택적으로 YouTube 게시(또는 게시 취소)의 진행 상황을 모니터링할 수 있습니다.

[비디오 인코딩 및 YouTube 게시 진행 모니터링](#monitoring-video-encoding-and-youtube-publishing-progress)을 참조하십시오.

게시 시간은 기본 소스 비디오 형식, 파일 크기 및 업로드 트래픽을 포함한 다양한 요소에 따라 크게 달라질 수 있습니다. 게시 프로세스는 몇 분에서 몇 시간 정도 소요될 수 있습니다. 또한 고해상도 형식이 훨씬 느리게 렌더링됩니다. 예를 들어 720p와 1080p는 480p보다 오래 걸립니다.

8시간 후에도 **[!UICONTROL 업로드됨(처리 중, 잠시 기다려 주십시오)]**&#x200B;이라는 상태 메시지가 계속 표시되면 사이트에서 비디오를 제거하고 다시 업로드해 보십시오.

### 웹 애플리케이션에 YouTube URL 연결 {#linking-youtube-urls-to-your-web-application}

비디오를 게시한 후 Dynamic Media에서 생성한 YouTube URL 문자열을 가져올 수 있습니다. YouTube URL을 복사하면 클립보드에 로드되므로 웹 사이트 또는 애플리케이션의 페이지에 필요에 따라 붙여넣을 수 있습니다.

>[!NOTE]
>
>YouTube URL은 비디오 자산을 YouTube에 게시하기 전까지 복사할 수 없습니다.

YouTube URL을 웹 애플리케이션에 연결하려면 다음을 수행하십시오.

1. 복사할 URL이 있는 *YouTube 게시됨* 비디오 자산으로 이동한 다음 선택합니다.

   YouTube URL은 *after*&#x200B;에만 복사할 수 있습니다. 처음 YouTube에 비디오 자산을 *게시*&#x200B;했습니다.

1. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 고급]** 탭을 선택합니다.
1. YouTube Publishing 제목 아래의 YouTube URL 목록에서 를 선택하고 URL 텍스트를 웹 브라우저에 복사하여 자산을 미리 보거나 웹 컨텐츠 페이지에 추가합니다.

### YouTube에서 제거할 수 있도록 비디오 게시 취소 {#unpublishing-videos-to-remove-them-from-youtube}

Experience Manager에서 비디오 에셋의 게시를 취소하면 비디오가 YouTube에서 제거됩니다.

>[!CAUTION]
>
>YouTube 내에서 직접 비디오를 제거하는 경우 Experience Manager은 알지 못하며 비디오가 여전히 YouTube에 게시된 것처럼 계속 동작합니다. 항상 Experience Manager을 통해 YouTube에서 비디오 자산의 게시를 취소합니다.

>[!NOTE]
>
>YouTube에서 컨텐츠를 제거하려면 Experience Manager에서 **[!UICONTROL YouTube에서 게시 취소]** 워크플로우를 사용하여 진행 상황을 모니터링하고 오류 정보를 볼 수 있습니다.
>
>[비디오 인코딩 및 YouTube 게시 진행 모니터링](#monitoring-video-encoding-and-youtube-publishing-progress)을 참조하십시오.

**YouTube에서 제거하기 위해 비디오 게시를 취소하려면 다음을 수행하십시오.**

1. YouTube 채널에서 게시를 취소할 비디오 자산으로 이동합니다.
1. 에셋 선택 모드에서 게시된 비디오 에셋을 하나 이상 선택합니다.
1. 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다. 필요한 경우 도구 모음에서 세 점 아이콘(`. . .`)을 선택하여 **[!UICONTROL 게시 관리]**&#x200B;를 확인합니다.
1. 게시 관리 페이지에서 **[!UICONTROL 게시 취소]**&#x200B;를 선택합니다.
1. 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 다음]**&#x200B;을(를) 선택합니다.
1. 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 게시 취소]**&#x200B;를 선택합니다.

## 비디오 인코딩 및 YouTube 게시 진행 모니터링 {#monitoring-video-encoding-and-youtube-publishing-progress}

비디오 인코딩이 적용되었거나 YouTube에 비디오를 게시하는 폴더에 새 비디오를 업로드할 때 비디오 인코딩/Youtube 게시가 어떻게 진행되고 있는지(또는 실패하고 있는지) 모니터링합니다. 실제 YouTube 게시 진행률은 로그를 통해서만 사용할 수 있습니다. 그러나 실패하든 성공하든 다음 절차에 설명된 다른 방법으로 나열됩니다. 또한 YouTube 게시 워크플로 또는 비디오 인코딩이 완료되거나 중단되면 이메일 알림을 받게 됩니다.

### 진행 상황 모니터링 {#monitoring-progress}

실패한 인코딩/YouTube 게시를 포함하여 진행 상황을 모니터링할 수 있습니다.

1. 에셋 폴더에서 비디오 인코딩 진행 상황 보기:

   * 카드 보기에서 에셋에 비디오 인코딩 진행률이 백분율로 표시됩니다. 오류가 있으면 이 정보도 자산에 표시됩니다.

   ![chlimage_1-429](/help/assets/dynamic-media/assets/chlimage_1-429.png)

   * 목록 보기에서 비디오 인코딩 진행률이 **[!UICONTROL 처리 상태]** 열에 표시됩니다. 오류가 있는 경우 이 메시지가 동일한 열에 표시됩니다.

   ![chlimage_1-430](/help/assets/dynamic-media/assets/chlimage_1-430.png)

   This column does not display by default. 열을 사용하려면 보기 드롭다운 메뉴에서 **[!UICONTROL 보기 설정]**&#x200B;을 선택하고 **[!UICONTROL 처리 상태]** 열을 추가한 다음 **[!UICONTROL 업데이트]**&#x200B;를 선택하십시오.

   ![chlimage_1-431](/help/assets/dynamic-media/assets/chlimage_1-431.png)

1. 에셋 세부 사항에서 진행 상황 보기 자산을 선택하면 드롭다운 메뉴를 열고 **[!UICONTROL 타임라인]**&#x200B;을 선택합니다. 인코딩 또는 YouTube 게시와 같은 워크플로우 활동으로 범위를 좁히려면 **[!UICONTROL 워크플로우]**&#x200B;를 선택하십시오.

   ![chlimage_1-432](/help/assets/dynamic-media/assets/chlimage_1-432.png)

   모든 워크플로우 정보(예: 인코딩)가 타임라인에 표시됩니다. YouTube 게시의 경우 워크플로 타임라인에는 YouTube 채널의 이름 및 YouTube 비디오 URL도 포함됩니다. 또한 게시가 완료된 후 워크플로 타임라인에 오류 알림이 표시됩니다.

   >[!NOTE]
   >
   >[https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)에서 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]** 및 **[!UICONTROL 시간 초과]**&#x200B;에 대한 여러 워크플로 구성으로 인해 실패/오류 메시지가 최종적으로 기록되는 데 시간이 오래 걸릴 수 있습니다. 예를 들면 다음과 같습니다.
   >
   >* Apache Sling 작업 큐 구성
   >* Adobe Granite 워크플로 외부 프로세스 작업 핸들러
   >* Granite 워크플로우 시간 초과 큐
   >
   >이러한 구성에서 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]** 및 **[!UICONTROL 시간 초과]** 속성을 조정할 수 있습니다.

1. For workflows in progress, see Workflow Instances available from **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Instances]**.

   >[!NOTE]
   >
   >**[!UICONTROL 도구]** 메뉴에 액세스하려면 관리 권한이 필요합니다.

   ![chlimage_1-433](/help/assets/dynamic-media/assets/chlimage_1-433.png)

   인스턴스를 선택하고 **[!UICONTROL 내역 열기]**&#x200B;를 선택합니다.

   ![chlimage_1-434](/help/assets/dynamic-media/assets/chlimage_1-434.png)

   워크플로 인스턴스 영역에서 워크플로를 일시 중단하거나 종료하거나 이름을 변경할 수도 있습니다. 자세한 내용은 [워크플로 관리](/help/sites-cloud/authoring/workflows/overview.md)를 참조하십시오.

1. For failed jobs, see Workflow Failures available from **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Failures]**. The **[!UICONTROL Workflow Failure]** lists all failed workflow activities.

   >[!NOTE]
   >
   >**[!UICONTROL 도구]** 메뉴에 액세스하려면 관리 권한이 필요합니다.

   ![chlimage_1-435](/help/assets/dynamic-media/assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >[https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)에서 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]** 및 **[!UICONTROL 시간 초과]**&#x200B;에 대한 여러 워크플로 구성으로 인해 오류 메시지가 최종적으로 기록되는 데 시간이 오래 걸릴 수 있습니다. 예:
   >
   >* Apache Sling 작업 큐 구성
   >* Adobe Granite 워크플로 외부 프로세스 작업 핸들러
   >* Granite 워크플로우 시간 초과 큐
   >
   >이러한 구성에서 **[!UICONTROL 다시 시도]**, **[!UICONTROL 다시 시도 지연]** 및 **[!UICONTROL 시간 초과]** 속성을 조정할 수 있습니다.

1. For completed workflows, see Workflow Archive available from **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Archive]**. The **[!UICONTROL Workflow Archive]** lists all completed workflow activities.

   >[!NOTE]
   >
   >**[!UICONTROL 도구]** 메뉴에 액세스하려면 관리 권한이 필요합니다.

   ![chlimage_1-436](/help/assets/dynamic-media/assets/chlimage_1-436.png)

1. 중단되거나 실패한 워크플로우 작업에 대한 이메일 알림을 받습니다. 이러한 이메일 알림은 관리자가 구성할 수 있습니다. [전자 메일 알림 구성](#configuring-e-mail-notifications)을 참조하세요.

<!-- EMAIL NOT AVAILABLE IN SKYLINE

#### Configuring e-mail notifications {#configuring-e-mail-notifications}

>[!NOTE]
>
>You may need administrative rights to access the **[!UICONTROL Tools]** menu.

How you configure notification depends on whether you want notifications for YouTube publishing jobs.

* For encoding jobs, you can access the configuration page for all Experience Manager workflow email notifications at **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** and by searching for **[!UICONTROL Day CQ Workflow Email Notification Service]**. You can select or clear the check boxes for **[!UICONTROL Notify on Abort]** or **[!UICONTROL Notify on Complete]** accordingly.

For YouTube publishing jobs, do the following:

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. On the Workflow Models page, select **[!UICONTROL Publish to YouTube]**, then select **[!UICONTROL Edit]** on the toolbar.
1. Near the upper-right corner of the Publish to YouTube workflow page, select **[!UICONTROL Edit]**.
1. Hover the mouse pointer on the YouTube Upload component, then select once to display the inline toolbar.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. On the inline toolbar, select the Configuration icon (wrench). Select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. In the YouTube Upload Process - Step Properties dialog box, select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. You can select or clear the following check boxes:

    * Publish Start
    * Publish Failure
    * Publish Completion - includes information on channels and URLs

   Clearing a check box means that you will not receive the specified email notification from the YouTube Publish workflow.

   >[!NOTE]
   >
   >These emails are specific to YouTube and are in addition to the generic workflow email notifications. As a result, you may receive two sets of email notification - the generic notification available in the **[!UICONTROL Day CQ Workflow Email Notification Service]** and one specific to YouTube depending on your configuration settings.

1. When you are finished, near the upper-right corner of the dialog box, select the **[!UICONTROL Done]** icon (check mark).
1. On the Publish to YouTube workflow page, near the upper-right corner, select **[!UICONTROL Sync]**.

-->

## 처리 프로필을 사용하여 코드 변환 {#transcode-video}

[!DNL Experience Manager]을(를) [!DNL Cloud Service](으)로 사용하면 처리 프로필을 사용하여 MP4 비디오 파일의 기본 코드 변환 작업을 수행할 수 있습니다. 이 기능을 사용하면 MP4 비디오 파일을 업로드하는 것뿐만 아니라 미리 보고 크기를 조정할 수 있습니다.

[!DNL Experience Manager]](assets/video-processing-profile-for-mp4.png)에서 비디오 코드 변환에 대한 ![처리 프로필 만들기

*그림: [!DNL Experience Manager]에서 비디오 코드 변환에 대한 처리 프로필.*

너비만 제공하거나 높이만 입력하고 다른 필드는 비워 두면 렌디션은 종횡비를 유지합니다. H.264 비디오 코덱은 코드 변환에 사용할 수 있습니다.

처리 프로필을 사용하여 에셋을 처리하려면 폴더에 프로필을 추가합니다. [처리 프로필을 사용하여 자산 처리](/help/assets/asset-microservices-configure-and-use.md#use-profiles)를 참조하십시오.

## 비디오 자산에 주석 달기 {#annotate-video-assets}

비디오 에셋에 주석을 추가할 수 있습니다. 비디오에 주석을 달 때 플레이어는 일시 중지하여 프레임에 주석을 달 수 있도록 합니다. 자세한 내용은 [비디오 자산 관리](manage-video-assets.md)를 참조하십시오.

>[!NOTE]
>
>MXF 비디오 포맷은 비디오 자산 주석에서 아직 지원되지 않습니다.

1. [!DNL Assets] 콘솔에서 자산 카드의 **[!UICONTROL 편집]**&#x200B;을 선택하여 자산 세부 정보 페이지를 표시합니다.
1. 비디오를 재생하려면 **[!UICONTROL 미리 보기]**&#x200B;를 클릭하세요.
1. 비디오에 주석을 달려면 **[!UICONTROL 주석 달기]**&#x200B;를 클릭하세요. 비디오의 특정 시간(프레임)에 주석이 추가됩니다. 주석을 추가할 때 캔버스에 그림을 그리고 그림에 주석을 포함할 수 있습니다. 주석은 자동으로 저장됩니다. 주석 마법사를 종료하려면 **[!UICONTROL 닫기]**&#x200B;를 클릭하십시오.
1. Seek to a specific point in the video, specify the time in seconds in the **text** field and click **Jump**. For example, to skip the first 20 seconds of video, enter 20 in the text field.
1. 타임라인에서 보려면 주석을 클릭합니다. 타임라인에서 주석을 삭제하려면 **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.

## 우수 사례 및 제한 사항 {#tips-limitations}

* [!DNL Dynamic Media] 라이선스가 없으면 처리 프로필을 사용하여 MP4 파일만 처리할 수 있습니다.
* 처리 프로필을 사용하여 MP4 파일을 코드 변환할 때 다음 지침과 제한 사항이 적용됩니다.

   * Apple ProRes 파일은 최대 해상도인 1080p까지만 코드 변환할 수 있습니다.
   * 소스 파일의 비트율이 200Mbps를 초과하는 경우 최대 해상도인 1080p로만 코드 변환할 수 있습니다.
   * 소스 프레임 속도가 60fps 이상인 경우 사용할 수 있는 소스 파일의 최대 크기는 다음과 같습니다.

      * 4k 코드 변환에 400MB.
      * 1080p 코드 변환의 경우 800MB입니다.
      * 720p 코드 변환의 경우 8GB입니다.

   * 4k 해상도로 변환할 수 있는 최대 파일 크기는 4k 해상도, 12Mbps 비트율 및 23fps의 2.55GB MP4 파일입니다.

  **추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Dynamic Media 비디오 설명서](/help/assets/dynamic-media/video.md).
>* [처리 프로필의 사용, 유형 및 구성에 대해 자세히 알아보세요](/help/assets/asset-microservices-configure-and-use.md).
