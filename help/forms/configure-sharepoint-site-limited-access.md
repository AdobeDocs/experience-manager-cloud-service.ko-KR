---
Title: How to configure a SharePoint Site with limited access using authorization scope?
Description: Learn how to configure SharePoint Site with limited access using the authorization scope.
keywords: 제한된 액세스로 SharePoint 사이트를 구성하는 방법. 제한된 액세스로 SharePoint 구성, 인증 범위를 사용하여 SharePoint 사이트에 대한 액세스를 제한합니다.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: 4962c058e2cc2135dd3626655ba7b21dbdcbd455
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 15%

---


<span class="preview"> 이 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

# 인증 범위를 사용하여 제한된 액세스로 SharePoint 사이트 구성

제한 또는 제한된 액세스의 목적은 관리자가 특정 SharePoint 사이트 또는 SharePoint 사이트 그룹에 대한 사용자 액세스를 제어할 수 있도록 하여 보안 관리를 향상시키는 것입니다. 권한 수준은 허용되지 않는 다른 SharePoint 사이트를 볼 수 있도록 허용하지 않고 특정 사이트에 대한 액세스 권한을 사용자 또는 그룹에 부여해야 할 때 유용합니다.

## 제한된 액세스로 SharePoint 사이트 구성 시 이점

SharePoint 사이트에 대한 제한된 액세스를 제공하는 이점:

* **향상된 보안**: 액세스를 제한하면 권한이 있는 직원만 중요한 정보를 보거나 조작할 수 있으므로 무단 액세스의 위험을 줄일 수 있습니다.

* **최소 권한의 원칙**: 사용자에게 작업 기능을 수행하는 데 필요한 최소 수준의 액세스 또는 권한을 제공합니다. 이를 통해 각 사용자가 네트워크의 민감한 부분에 노출되는 것을 최소화하여 잠재적인 내부 위협으로부터 보호할 수 있습니다.

* **데이터 보호**: 제한된 액세스는 노출로부터 중요한 데이터를 보호하는 데 도움이 됩니다. 데이터 보호 규정 준수에 필수적인 데이터를 반드시 확인해야 하는 사용자만 액세스할 수 있도록 합니다.

* **실수로 인한 데이터 손실 방지**: 콘텐츠를 수정할 수 있는 사용자가 적을수록 중요한 데이터를 실수로 삭제하거나 변경할 가능성이 크게 줄어듭니다.

* **제어된 데이터 흐름**: 조직 내/외부의 정보 흐름을 제어하여 데이터가 잘못된 손으로 끝나지 않도록 하는 데 도움이 됩니다.

## 인증 범위를 사용하여 제한된 액세스로 SharePoint 구성

인증 범위를 사용하여 제한된 액세스로 SharePoint 사이트를 구성하려면 아래 단계를 따르십시오.

1. [을(를) 사용하여 애플리케이션 만들기 ](#create-an-application-with-the-limited-permission-in-the-azure-portal)
1. [AEM 인스턴스에서 인증 범위 설정](#set-the-authorization-scope-at-aem-instance)

### Azure 포털에서 제한된 권한으로 응용 프로그램 만들기

Microsoft의 Graph API에서 `Sites.Selected` 권한 범위를 사용하여 [Microsoft Azure 포털](https://portal.azure.com/#home)에 응용 프로그램을 만듭니다.

![SharePoint 선택 사이트](/help/forms/assets/sharepoint-selected-site.png)

`OAuth URL`의 `Client ID`, `Client Secret` 및 `Tenant ID`을(를) 검색하는 방법에 대한 자세한 내용은 [Microsoft® 설명서](https://learn.microsoft.com/en-us/graph/auth-register-app-v2)를 참조하십시오.
* Microsoft® Azure 포털에서 리디렉션 URI를 `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`로 추가합니다. `[author-instance]`를 작성자 인스턴스의 URL로 대체합니다.
* 제한된 사이트 액세스를 제공하기 위해 Microsoft의 Graph API에 `offline_access` 및 `Sites.Selected` 권한 범위를 추가하십시오.
* OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Microsoft® Azure 포털에서 `<tenant-id>`를 앱의 `tenant-id`로 대체합니다.

`Sites.Selected` API 권한을 사용하려면 SharePoint Online Sites에 대해 적절한 권한이 설정된 Azure 포털에 등록된 응용 프로그램이 필요합니다. 이 설정을 사용하면 정의된 범위 내에서 SharePoint 사이트와 상호 작용하는 데 필요한 권한이 애플리케이션에 부여되므로 필요한 제한된 액세스를 제공할 수 있습니다.

SharePoint Online Sites에 대한 `Sites.Selected` 권한을 사용하는 응용 프로그램을 개발하는 방법에 대한 지침은 [문서](https://techcommunity.microsoft.com/t5/microsoft-sharepoint-blog/develop-applications-that-use-sites-selected-permissions-for-spo/ba-p/3790476)를 참조하세요.

### AEM 인스턴스에서 인증 범위 설정

Microsoft SharePoint 사이트에 대한 제한된 액세스를 제공하려면 인증 범위를 올바르게 설정해야 합니다. 인증 범위를 설정하고 AEM Forms을 Microsoft® SharePoint 스토리지에 연결하려면 다음을 수행하십시오.

1. **AEM Forms 작성자** 인스턴스 > **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Microsoft® SharePoint]**(으)로 이동합니다.
1. **[!UICONTROL Microsoft® SharePoint]**&#x200B;을(를) 선택하면 **[!UICONTROL SharePoint 브라우저]**(으)로 리디렉션됩니다.
1. **구성 컨테이너**&#x200B;를 선택합니다. 선택한 구성 컨테이너에 구성을 저장합니다.
1. 드롭다운 목록에서 **[!UICONTROL 만들기]** > **[!UICONTROL SharePoint 문서 라이브러리]**&#x200B;를 클릭합니다. SharePoint 구성 마법사가 나타납니다.

   ![SharePoint 사이트 액세스 제한](/help/forms/assets/sharepoint-doc-library-limited-scopes.png)

1. **[!UICONTROL 제목]**, **[!UICONTROL 클라이언트 ID]** 및 **[!UICONTROL 클라이언트 암호]**&#x200B;를 지정하십시오. 클라이언트 ID 및 클라이언트 암호를 검색하는 방법에 대한 자세한 내용은 [Microsoft® 설명서](https://learn.microsoft.com/en-us/graph/auth-register-app-v2)를 참조하십시오.

1. OAuth URL을 `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`(으)로 사용합니다. Microsoft® Azure 포털에서 `<tenant-id>`를 앱의 `tenant-id`로 대체합니다.

   >[!NOTE]
   >
   > **클라이언트 보안** 필드는 Azure Active Directory 애플리케이션 구성에 따라 필수 또는 선택 사항입니다. 애플리케이션을 구성하여 클라이언트 보안을 사용하는 경우 클라이언트 보안을 제공해야 합니다.

1. `Authorization Scope` 필드에 `offline_access Sites.Selected`을(를) 추가합니다. `Authorization Scope` 텍스트 상자 필드에 `offline_access Sites.Selected` 범위를 추가하면 `SharePoint Site ID` 텍스트 상자가 화면에 표시됩니다.

1. SharePoint 사이트 ID를 지정합니다. SharePoint 사이트 ID를 검색하는 방법에 대해 알아보려면 [추가 바이트](#extra-bytes) 섹션을 참조하십시오.

1. **[!UICONTROL 사이트 연결 확인]**&#x200B;을 클릭합니다. 연결이 완료되면 `Connection Successful` 메시지가 나타납니다.

1. 이제 **SharePoint 사이트** > **문서 라이브러리** > **SharePoint 폴더**&#x200B;를 선택하여 데이터를 저장합니다.

   >[!NOTE]
   >
   >* 기본적으로 `forms-ootb-storage-adaptive-forms-submission`은(는) 선택한 SharePoint 사이트에 있습니다.
   >* **폴더 만들기**&#x200B;를 클릭하여 선택한 SharePoint 사이트의 `Documents` 라이브러리에 아직 없는 경우 폴더를 `forms-ootb-storage-adaptive-forms-submission`(으)로 만듭니다.

이제 적응형 양식의 제출 액션에 이 [SharePoint Sites 구성을 사용할 수 있습니다](/help/forms/configure-submit-action-sharepoint.md#use-sharepoint-document-library-configuration-in-an-adaptive-form-use-sharepoint-configuartion-in-af).

## 추가 바이트

`SharePoint Site ID`의 값을 검색하려면 다음을 수행하십시오.
1. [Microsoft Graph Explorer API](https://developer.microsoft.com/en-us/graph/graph-explorer)(으)로 이동합니다.
1. 왼쪽 창의 `SharePoint Sites` API에서 `Search for a SharePoint site by keyword`을(를) 클릭합니다.
1. 자리 표시자 `contoso`을(를) SharePoint 사이트의 실제 이름으로 바꾸면 해당 사이트 ID를 가져올 수 있습니다.

   ![SharePoint 문서 라이브러리 ID](/help/forms/assets/sharepoint-site-id.png)

`Run Query` 단추를 클릭하면 사이트 ID가 화면에 표시됩니다.