---
Title: How to send data to a SharePoint storage on submission of an Adaptive Form?
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list or Document library when you submit the form.
keywords: 적응형 양식에 대한 SharePoint 목록을 연결하는 방법, 적응형 양식에 대한 SharePoint 문서 라이브러리 연결, SharePoint에 제출, SharePoint 문서 라이브러리 구성 만들기, 적응형 양식의 SharePoint 제출 액션을 사용, 적응형 양식을 Microsoft&reg; SharePoint 목록에 연결.
feature: Adaptive Forms, Core Components
exl-id: e925a750-5fb5-4950-afd3-78551eec985d
title: 적응형 양식에 대한 제출 액션을 구성하는 방법
role: User, Developer
source-git-commit: 5e1d08e82cafc3a8a715653727f42ce0048f2b1f
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 31%

---

# Microsoft® SharePoint에 적응형 양식 연결

**[!UICONTROL SharePoint에 제출]** 제출 액션을 사용하면 적응형 양식을 Microsoft® SharePoint 저장소와 원활하게 연결할 수 있습니다. 양식을 제출한 후 양식 데이터를 선택한 SharePoint 저장소로 보냅니다.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.

## 장점

적응형 양식에서 SharePoint 스토리지로 데이터를 제출할 때의 몇 가지 장점은 다음과 같습니다.

* 이를 통해 양식 데이터를 SharePoint에 직접 손쉽게 제출하여 정보를 저장하고 관리할 수 있는 중앙 집중식 위치를 확보할 수 있습니다.
* SharePoint의 액세스 제어 및 권한 기능을 적용하면 승인된 사용자만 제출된 데이터를 보거나 수정할 수 있습니다.

**[!UICONTROL SharePoint에 제출]**&#x200B;을 사용하여 다음을 수행할 수 있습니다.

* [적응형 양식을 SharePoint 문서 라이브러리에 연결](#connect-af-sharepoint-doc-library)
* [SharePoint 목록에 적응형 양식 연결](#connect-af-sharepoint-list)

## 적응형 양식을 SharePoint 문서 라이브러리에 연결 {#connect-af-sharepoint-doc-library}

적응형 양식에서 **[!UICONTROL SharePoint 문서 라이브러리에 제출]** 제출 액션을 사용하려면:

1. [SharePoint 문서 라이브러리 구성 만들기](#create-a-sharepoint-configuration-create-sharepoint-configuration): AEM Forms을 Microsoft® Sharepoint 저장소에 연결합니다.
2. [적응형 양식에서 SharePoint에 제출 액션 사용](#use-sharepoint-configuartion-in-af): Adaptive Form을 구성된 Microsoft® SharePoint에 연결합니다.

### SharePoint 문서 라이브러리 구성 만들기 {#create-sharepoint-configuration}

AEM Forms을 Microsoft® Sharepoint Document Library 스토리지에 연결하려면

1. **AEM Forms 작성자** 인스턴스 > **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Microsoft® SharePoint]**(으)로 이동합니다.
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

1. **[!UICONTROL 연결]**&#x200B;을 클릭합니다. 연결이 완료되면 `Connection Successful` 메시지가 나타납니다.

1. 이제 **SharePoint 사이트** > **문서 라이브러리** > **SharePoint 폴더**&#x200B;를 선택하여 데이터를 저장합니다.

   >[!NOTE]
   >
   >* 기본적으로 `forms-ootb-storage-adaptive-forms-submission`은(는) 선택한 SharePoint 사이트에 있습니다.
   >* **폴더 만들기**&#x200B;를 클릭하여 선택한 SharePoint 사이트의 `Documents` 라이브러리에 아직 없는 경우 폴더를 `forms-ootb-storage-adaptive-forms-submission`(으)로 만듭니다.

이제 적응형 양식의 제출 작업에 이 SharePoint Sites 구성을 사용할 수 있습니다.

### 적응형 양식에서 SharePoint 문서 라이브러리 구성 사용 {#use-sharepoint-configuartion-in-af}

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

## Microsoft® SharePoint 목록에 적응형 양식 연결 {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

적응형 양식에서 [!UICONTROL SharePoint 목록에 제출] 제출 액션을 사용하려면:

1. [SharePoint 목록 구성 만들기](#create-sharepoint-list-configuration): AEM Forms을 Microsoft® Sharepoint 목록 저장소에 연결합니다.
1. [적응형 양식에서 FDM(양식 데이터 모델)을 사용하여 제출](#use-submit-using-fdm): 적응형 양식을 구성된 Microsoft® SharePoint에 연결합니다.

### SharePoint 목록 구성 만들기 {#create-sharepoint-list-configuration}

AEM Forms을 Microsoft® Sharepoint 목록에 연결하려면:

1. **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Microsoft® SharePoint]**&#x200B;로 이동합니다.
1. **구성 컨테이너**&#x200B;를 선택합니다. 선택한 구성 컨테이너에 구성을 저장합니다.
1. 드롭다운 목록에서 **[!UICONTROL 만들기]** > **[!UICONTROL SharePoint 목록]**&#x200B;을 클릭합니다. SharePoint 구성 마법사가 나타납니다.
1. **[!UICONTROL 제목]**, **[!UICONTROL 클라이언트 ID]**, **[!UICONTROL 클라이언트 보안]** 및 **[!UICONTROL OAuth URL]**&#x200B;을 지정합니다. OAuth URL의 클라이언트 ID, 클라이언트 보안, 테넌트 ID를 검색하는 방법에 대한 자세한 내용은 [Microsoft® Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2)을 참조하십시오.
   * Microsoft® Azure 포털에서 앱의 `Client ID` 및 `Client Secret`를 검색할 수 있습니다.
   * Microsoft® Azure 포털에서 리디렉션 URI를 `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`로 추가합니다. `[author-instance]`를 작성자 인스턴스의 URL로 대체합니다.
   * 읽기/쓰기 권한을 제공하려면 **Microsoft® 그래프** 탭에서 API 권한 `offline_access` 및 `Sites.Manage.All`을(를) 추가하십시오. SharePoint 데이터와 원격으로 상호 작용하려면 **Sharepoint** 탭에 `AllSites.Manage` 권한을 추가하십시오.
   * OAuth URL 사용: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Microsoft® Azure 포털에서 `<tenant-id>`를 앱의 `tenant-id`로 대체합니다.

     >[!NOTE]
     >
     > **클라이언트 보안** 필드는 Azure Active Directory 애플리케이션 구성에 따라 필수 또는 선택 사항입니다. 애플리케이션을 구성하여 클라이언트 보안을 사용하는 경우 클라이언트 보안을 제공해야 합니다.

1. **[!UICONTROL 연결]**&#x200B;을 클릭합니다. 연결이 완료되면 `Connection Successful` 메시지가 나타납니다.
1. 드롭다운 목록에서 **[!UICONTROL SharePoint 사이트]** 및 **[!UICONTROL SharePoint 목록]**&#x200B;을 선택합니다.
1. Microsoft® SharePointList에 대한 클라우드 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.


### 적응형 양식에서 FDM(양식 데이터 모델)을 사용하여 제출 사용 {#use-submit-using-fdm}

적응형 양식에서 생성된 SharePoint 목록 구성을 사용하여 데이터나 생성된 기록 문서를 SharePoint 목록에 저장할 수 있습니다. 적응형 양식의 SharePoint 목록을 다음으로 사용하려면 다음 단계를 수행하십시오.

1. [Microsoft을 사용하여 양식 데이터 모델(FDM) 만들기](/help/forms/create-form-data-models.md)
1. [데이터를 검색하고 보내도록 양식 데이터 모델(FDM) 구성](/help/forms/work-with-form-data-model.md#configure-services)
1. [적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md)
1. [FDM(양식 데이터 모델)을 사용하여 제출 액션 구성](/help/forms/using-form-data-model.md)

양식을 제출하면 데이터가 지정된 Microsoft® Sharepoint 목록 저장소에 저장됩니다.

>[!NOTE]
>
> Microsoft® SharePoint 목록에서는 다음 열 유형이 지원되지 않습니다.
> * 이미지 열
> * 메타데이터 열
> * 개인 열
> * 외부 데이터 열

## 관련 문서

{{af-submit-action}}
