---
Title: How to integrate Adaptive Form to a SharePoint Document Library?
Description: This article explains how to send data from your Adaptive Form to a SharePoint  Document library when you submit the form.
keywords: 적응형 양식을 위한 SharePoint 문서 라이브러리 연결, SharePoint에 제출, SharePoint 문서 라이브러리 구성 만들기, 적응형 양식에서 SharePoint에 제출 액션을 사용, AEM Forms 데이터 모델 SharePoint 문서 라이브러리, Forms 데이터 모델 SharePoint 문서 라이브러리, Forms 데이터 모델을 SharePoint 문서 라이브러리에 통합
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: 55e8f142e242f5f4010653a155a241ffcf801470
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 35%

---


# Microsoft® SharePoint 문서 라이브러리에 적응형 양식 연결 {#connect-af-sharepoint-doc-library}

>[!VIDEO](https://video.tv.adobe.com/v/3444368/formautomation-productivitytools-adaptiveforms--sharepointintegration-documentlibrary/?quality=12&learn=on)

적응형 양식에서 **[!UICONTROL SharePoint 문서 라이브러리에 제출]** 제출 액션을 사용하려면:

1. [SharePoint 문서 라이브러리 구성 만들기](#1-create-a-sharepoint-document-library-configuration): AEM Forms을 Microsoft® Sharepoint 저장소에 연결합니다.
2. [적응형 양식에서 SharePoint에 제출 액션 사용](#2-use-sharepoint-document-library-configuration-in-an-adaptive-form): Adaptive Form을 구성된 Microsoft® SharePoint에 연결합니다.

## 1. SharePoint 문서 라이브러리 구성 만들기

AEM Forms을 Microsoft® Sharepoint Document Library 스토리지에 연결하려면

1. **AEM Forms 작성자** 인스턴스 > **[!UICONTROL 도구]** > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL Microsoft® SharePoint]**(으)로 이동합니다.
1. **[!UICONTROL Microsoft® SharePoint]**&#x200B;을(를) 선택하면 **[!UICONTROL SharePoint 브라우저]**(으)로 리디렉션됩니다.
1. **구성 컨테이너**&#x200B;를 선택합니다. 선택한 구성 컨테이너에 구성을 저장합니다.
1. 드롭다운 목록에서 **[!UICONTROL 만들기]** > **[!UICONTROL SharePoint 문서 라이브러리]**&#x200B;를 클릭합니다. SharePoint 구성 마법사가 나타납니다.

   ![SharePoint 구성](/help/forms/assets/sharepoint_configuration.png)

1. **[!UICONTROL 제목]**, **[!UICONTROL 클라이언트 ID]**, **[!UICONTROL 클라이언트 보안]** 및 **[!UICONTROL OAuth URL]**&#x200B;을 지정합니다. OAuth URL의 클라이언트 ID, 클라이언트 보안, 테넌트 ID를 검색하는 방법에 대한 자세한 내용은 [Microsoft® Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2)을 참조하십시오.
   * Microsoft® Azure 포털에서 앱의 `Client ID` 및 `Client Secret`를 검색할 수 있습니다.
   * Microsoft® Azure 포털에서 리디렉션 URI를 `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`로 추가합니다. `[author-instance]`를 작성자 인스턴스의 URL로 대체합니다.
   * 읽기/쓰기 권한을 제공하려면 API 권한 `offline_access` 및 `Sites.Manage.All`을(를) 추가하십시오. `Sites.Manage.All`은(는) 응용 프로그램에 사이트 삭제 또는 수정과 같은 SharePoint 사이트의 모든 측면을 관리할 수 있는 권한을 부여하는 Microsoft Graph API의 권한 범위입니다.

     >[!NOTE]
     >
     > Microsoft의 Graph API에서 `Sites.Selected` 권한 범위를 사용하여 [액세스가 제한된 SharePoint 사이트를 구성](/help/forms/configure-sharepoint-site-limited-access.md)할 수도 있습니다. `Sites.Selected`은(는) Microsoft 사이트에 대한 보다 세분화되고 제한된 액세스를 허용하는 SharePoint Graph API의 권한 범위입니다.

   * OAuth URL 사용: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Microsoft® Azure 포털에서 `<tenant-id>`를 앱의 `tenant-id`로 대체합니다.

     >[!NOTE]
     >
     > **클라이언트 보안** 필드는 Azure Active Directory 애플리케이션 구성에 따라 필수 또는 선택 사항입니다. 애플리케이션을 구성하여 클라이언트 보안을 사용하는 경우 클라이언트 보안을 제공해야 합니다.

1. Microsoft 사이트에 대한 보다 세분화되고 제한된 액세스를 허용하는 SharePoint Graph API의 `offline_access Sites.Selected` 권한 범위입니다. SharePoint 사이트에 대한 전체 액세스를 허용하는 Microsoft Graph API의 `offline_access Sites.Manage.All` 권한 범위입니다.
1. **[!UICONTROL 연결]**&#x200B;을 클릭합니다. 연결이 완료되면 `Connection Successful` 메시지가 나타납니다.

1. 이제 **SharePoint 사이트** > **문서 라이브러리** > **SharePoint 폴더**&#x200B;를 선택하여 데이터를 저장합니다.

   >[!NOTE]
   >
   >* 기본적으로 `forms-ootb-storage-adaptive-forms-submission`은(는) 선택한 SharePoint 사이트에 있습니다.
   >* **폴더 만들기**&#x200B;를 클릭하여 선택한 SharePoint 사이트의 `Documents` 라이브러리에 아직 없는 경우 폴더를 `forms-ootb-storage-adaptive-forms-submission`(으)로 만듭니다.

이제 적응형 양식의 제출 작업에 이 SharePoint Sites 구성을 사용할 수 있습니다.

### 2. 적응형 양식에서 SharePoint 문서 라이브러리 구성 사용

적응형 양식에서 생성된 SharePoint 문서 라이브러리 구성을 사용하여 데이터나 생성된 기록 문서를 SharePoint 폴더에 저장할 수 있습니다. 적응형 양식에서 SharePoint 문서 라이브러리 스토리지 구성을 다음으로 사용하려면 다음 단계를 수행하십시오.

1. [적응형 양식](/help/forms/creating-adaptive-form-core-components.md)을 만듭니다.

   >[!NOTE]
   >
   > * 적응형 양식에 대해 동일한 [!UICONTROL 구성 컨테이너]를 선택합니다. 여기서 SharePoint 문서 라이브러리 저장소를 만들었습니다.
   > * [!UICONTROL 구성 컨테이너]가 선택되지 않은 경우 제출 액션 속성 창에 글로벌 [!UICONTROL 스토리지 구성] 폴더가 나타납니다.

1. **제출 액션**&#x200B;을 **[!UICONTROL SharePoint에 제출]**로 선택합니다.
   ![Sharepoint GIF](/help/forms/assets/sharedrive-video.gif)
1. 데이터를 저장하려는 경우 **[!UICONTROL 스토리지 구성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 제출 설정을 저장합니다.

양식을 제출하면 데이터가 지정된 Microsoft® Sharepoint 문서 라이브러리 저장소에 저장됩니다.
데이터를 저장하는 폴더 구조는 `/folder_name/form_name/year/month/date/submission_id/data`입니다.

## 관련 문서

{{af-submit-action}}