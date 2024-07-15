---
title: AEM Forms에 대해  [!DNL Microsoft Dynamics] OData를 구성하는 방법
description: ' [!DNL Microsoft Dynamics] service에 정의된 엔터티, 특성 및 서비스를 기반으로 양식 데이터 모델(FDM)을 만드는 방법을 알아봅니다.'
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner
exl-id: cb7b41f0-fd4f-4ba6-9f45-792a66ba6368
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 2%

---

# [!DNL Microsoft Dynamics] OData 구성 {#microsoft-dynamics-odata-configuration}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/ms-dynamics-odata-configuration.html) |
| AEM as a Cloud Service | 이 문서 |

![데이터 통합](assets/data-integeration.png)

[!DNL Microsoft Dynamics]은(는) 고객 계정, 연락처, 리드, 기회 및 사례를 만들고 관리하기 위한 엔터프라이즈 솔루션을 제공하는 CRM(고객 관계 관리) 및 ERP(전사적 자원 관리) 소프트웨어입니다. [[!DNL Experience Manager Forms] 데이터 통합](data-integration.md)은(는) Forms을 온라인 및 온-프레미스 [!DNL Microsoft Dynamics] 서버와 통합하기 위한 OData 클라우드 서비스 구성을 제공합니다. [!DNL Microsoft Dynamics] 서비스에 정의된 엔터티, 특성 및 서비스를 기반으로 양식 데이터 모델(FDM)을 만들 수 있습니다. 양식 데이터 모델(FDM)을 사용하여 [!DNL Microsoft Dynamics] 서버와 상호 작용하여 비즈니스 워크플로를 가능하게 하는 적응형 Forms을 만들 수 있습니다. 예:

* [!DNL Microsoft Dynamics] 서버에 데이터를 쿼리하고 적응형 Forms 미리 채우기
* 적응형 양식 제출 시 [!DNL Microsoft Dynamics]에 데이터 쓰기
* 양식 데이터 모델(FDM)에 정의된 사용자 지정 엔터티를 통해 [!DNL Microsoft Dynamics]에 데이터를 쓰고, 반대로

<!--[!DNL Experience Manager Forms] add-on package also includes reference OData configuration that you can use to quickly integrate [!DNL Microsoft Dynamics] with [!DNL Experience Manager Forms].-->

<!--When the package is installed, the following entities and services are available on your [!DNL Experience Manager Forms] instance:

* MS Dynamics OData Cloud Service (OData Service)-->
<!--* Form Data Model with preconfigured [!DNL Microsoft Dynamics] entities and services.-->

<!-- Preconfigured [!DNL Microsoft Dynamics] entities and services in a Form Data Model are available on your [!DNL Experience Manager Forms] instance only if the run mode for the [!DNL Experience Manager] instance is set as `samplecontent` (default). -->  MS Dynamics OData Cloud Service(OData 서비스)는 모든 실행 모드에서 사용할 수 있습니다. [!DNL Experience Manager] 인스턴스에 대한 실행 모드 구성에 대한 자세한 내용은 [실행 모드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#runmodes)를 참조하십시오.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.


## 사전 요구 사항 {#prerequisites}

[!DNL Microsoft Dynamics]을(를) 설정하고 구성하기 전에 다음을 확인하십시오.

<!--* Installed the [[!DNL Experience Manager Forms] add-on package](installing-configuring-aem-forms-osgi.md) -->
* [!DNL Microsoft Dynamics] 365를 온라인으로 구성하거나 다음 [!DNL Microsoft Dynamics] 버전 중 하나의 인스턴스를 설치했습니다.

   * [!DNL Microsoft Dynamics] 365 온-프레미스
   * [!DNL Microsoft Dynamics] 2016 온-프레미스

* [Active Directory](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory)에  [!DNL Microsoft Dynamics] 온라인 서비스에 대한 응용 프로그램을 등록했습니다.  [!DNL Microsoft Azure]  등록된 서비스에 대한 클라이언트 ID(애플리케이션 ID라고도 함) 및 클라이언트 암호의 값을 기록해 두십시오. 이 값은 [서비스에 대한 클라우드 서비스를 구성하는 동안 [!DNL Microsoft Dynamics] 서비스](#configure-cloud-service-for-your-microsoft-dynamics-service)에 사용됩니다.

## 등록된 [!DNL Microsoft Dynamics] 응용 프로그램에 대한 회신 URL 설정 {#set-reply-url-for-registered-microsoft-dynamics-application}

등록된 [!DNL Microsoft Dynamics] 응용 프로그램의 회신 URL을 설정하려면 다음을 수행하십시오.

>[!NOTE]
>
>[!DNL Experience Manager Forms]을(를) 온라인 [!DNL Microsoft Dynamics] 서버와 통합하는 동안에만 이 절차를 사용하십시오.

1. [!DNL Microsoft Azure] Active Directory 계정으로 이동하여 등록된 응용 프로그램의 **[!UICONTROL 회신 URL]** 설정에 다음 클라우드 서비스 구성 URL을 추가하십시오.

   `https://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![Azure 디렉터리](assets/azure_directory_new.png)

1. 구성을 저장합니다.

## IFD에 대해 [!DNL Microsoft Dynamics] 구성 {#configure-microsoft-dynamics-for-ifd}

[!DNL Microsoft Dynamics]은(는) 클레임 기반 인증을 사용하여 외부 사용자에게 [!DNL Microsoft Dynamics] CRM 서버의 데이터에 대한 액세스를 제공합니다. 이 기능을 사용하려면 IFD(인터넷 연결 배포)에 대해 [!DNL Microsoft Dynamics]을(를) 구성하고 클레임 설정을 구성하려면 다음을 수행하십시오.

>[!NOTE]
>
> [!DNL Experience Manager Forms]을(를) 온-프레미스 [!DNL Microsoft Dynamics] 서버와 통합하는 동안에만 이 절차를 사용하십시오.

1. [IFD 구성 [!DNL Microsoft Dynamics]](https://technet.microsoft.com/en-us/library/dn609803.aspx)에 설명된 대로 IFD에 대한 [!DNL Microsoft Dynamics] 온-프레미스 인스턴스를 구성합니다.
1. Windows PowerShell을 사용하여 다음 명령을 실행하여 IFD 사용 [!DNL Microsoft Dynamics]에 대한 클레임 설정을 구성하십시오.

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   자세한 내용은 [CRM 온-프레미스(IFD)용 앱 등록](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd)을 참조하세요.

## AD FS 컴퓨터에서 OAuth 클라이언트 구성 {#configure-oauth-client-on-ad-fs-machine}

AD FS(Active Directory Federation Services) 컴퓨터에 OAuth 클라이언트를 등록하고 AD FS 컴퓨터에 대한 액세스 권한을 부여하려면 다음을 수행하십시오.

>[!NOTE]
>
>[!DNL Experience Manager Forms]을(를) 온-프레미스 [!DNL Microsoft Dynamics] 서버와 통합하는 동안에만 이 절차를 사용하십시오.

1. 다음 명령을 실행합니다.

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   위치:

   * `Client-ID`은(는) GUID 생성기를 사용하여 생성할 수 있는 클라이언트 ID입니다.
   * `redirect-uri`은(는) [!DNL Experience Manager Forms]의 [!DNL Microsoft Dynamics] OData 클라우드 서비스에 대한 URL입니다. [!DNL Experience Manager Forms]과(와) 함께 설치된 기본 클라우드 서비스는 다음 URL에 배포됩니다.
     `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. 다음 명령을 실행하여 AD FS 컴퓨터에 대한 액세스 권한을 부여합니다.

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   위치:

   * `resource`은(는) [!DNL Microsoft Dynamics] 조직 URL입니다.

1. [!DNL Microsoft Dynamics]이(가) HTTPS 프로토콜을 사용합니다. [!DNL Forms] 서버에서 AD FS 끝점을 호출하려면 [!DNL Experience Manager Forms]을(를) 실행하는 컴퓨터에서 `keytool` 명령을 사용하여 Java 인증서 저장소에 [!DNL Microsoft Dynamics] 사이트 인증서를 설치하십시오.

## [!DNL Microsoft Dynamics] 서비스에 대한 클라우드 서비스 구성 {#configure-cloud-service-for-your-microsoft-dynamics-service}

OData 서비스는 서비스 루트 URL로 식별됩니다. as a Cloud Service [!DNL Experience Manager] OData 서비스를 구성하려면 서비스에 대한 서비스 루트 URL이 있는지 확인하고 다음을 수행합니다.

<!--The **MS Dynamics OData Cloud Service (OData Service)** configuration comes with default OData configuration. To configure it to connect with your [!DNL Microsoft Dynamics] service, do the following.-->

>[!NOTE]
>
>온라인 또는 온-프레미스에서 [!DNL Microsoft Dynamics 365]을(를) 구성하기 위한 단계별 안내서는 [[!DNL Microsoft Dynamics] OData 구성](ms-dynamics-odata-configuration.md)을 참조하십시오.

1. **[!UICONTROL 도구 > Cloud Service > 데이터 원본]**(으)로 이동합니다. 클라우드 구성을 만들 폴더를 선택하려면 를 선택합니다.

   클라우드 서비스 구성을 위한 폴더를 만들고 구성하는 방법에 대한 자세한 내용은 [클라우드 서비스 구성을 위한 폴더 구성](#cloud-folder)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 **[!UICONTROL 데이터 Source 구성 만들기 마법사]**&#x200B;를 엽니다. 구성의 이름 및 제목(선택 사항)을 지정하고, **[!UICONTROL 서비스 유형]** 드롭다운에서 **[!UICONTROL 데이터 서비스]**&#x200B;를 선택하고, 선택 사항으로 구성의 썸네일 이미지를 찾아 선택한 후 **[!UICONTROL 다음]**을 선택합니다.
**[!UICONTROL 인증 설정]** 탭에서:

   1. **[!UICONTROL 서비스 루트]** 필드에 대한 값을 입력하십시오. Dynamics 인스턴스로 이동하여 **[!UICONTROL 개발자 리소스]**(으)로 이동하여 서비스 루트 필드에 대한 값을 확인합니다. 예: https://&lt;tenant-name>/api/data/v9.1/

   1. 인증 유형으로 **[!UICONTROL OAuth 2.0]**&#x200B;을(를) 선택합니다.

   1. **[!UICONTROL 클라이언트 ID]**(**응용 프로그램 ID**&#x200B;이라고도 함), **[!UICONTROL 클라이언트 암호]**, **[!UICONTROL OAuth URL]**, **[!UICONTROL 새로 고침 토큰 URL]**, **[!UICONTROL 액세스 토큰 URL]** 및 **[!UICONTROL 리소스]** 필드의 기본값을 [!DNL Microsoft Dynamics] 서비스 구성의 값으로 바꿉니다. 양식 데이터 모델(FDM)을 사용하여 [!DNL Microsoft Dynamics]을 구성하려면 **[!UICONTROL 리소스]** 필드에 동적 인스턴스 URL을 지정해야 합니다. 서비스 루트 URL을 사용하여 dynamics 인스턴스 URL을 파생시킵니다. 예: [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).

   1. [!DNL Microsoft Dynamics]의 권한 부여 프로세스를 위해 **[!UICONTROL 권한 부여 범위]** 필드에 **[!UICONTROL openid]**&#x200B;을(를) 지정하십시오.

      ![인증 설정](assets/dynamics_authentication_settings_new.png)
양식 데이터 모델(FDM)
1. **[!UICONTROL OAuth에 연결]**&#x200B;을 클릭합니다. [!DNL Microsoft Dynamics] 로그인 페이지로 리디렉션되었습니다.
1. [!DNL Microsoft Dynamics] 자격 증명으로 로그인하고 을(를) 수락하여 클라우드 서비스 구성이 [!DNL Microsoft Dynamics] 서비스에 연결할 수 있도록 합니다. 클라우드 서비스와 서비스를 FDM(양식 데이터 모델)을 설정하는 것이 일회성 작업입니다.

   OData 구성이 성공적으로 저장되었다는 메시지를 표시하는 클라우드 서비스 구성 페이지의 양식 데이터 모델입니다.

MS Dynamics OData Cloud Service(OData 서비스) 클라우드 서비스가 구성되어 있으며 Dynamics 서비스와 연결되어 있습니다. 양식 데이터 모델(FDM)

## 양식 데이터 모델(FDM) 생성 {#create-form-data-model}

<!--When you install the [!DNL Experience Manager Forms] package, a form data model, **[!DNL Microsoft Dynamics] FDM**, is deployed on your [!DNL Experience Manager] instance. By default, the Form Data Model uses [!DNL Microsoft Dynamics] service configured in the MS Dynamics OData Cloud Service (OData Service) as its data source.

On opening the Form Data Model for the first time, it connects to the configured [!DNL Microsoft Dynamics] service and fetches entities from your [!DNL Microsoft Dynamics] instance. The "contact" and "lead" entities from [!DNL Microsoft Dynamics] are already added in the form data model.

To review the form data model, go to **[!UICONTROL Form Data Model egrations]**. Select **[!DNL Microsoft Dynamics] FDM** and click **[!UICONTROL Edit]** to open the Form Data Model in edit mode. Alternatively, you can open the Form Data Model directly from the following URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`
 Form Data Model 
![default-fdm-1](assets/default-fdm-1.png)-->

MS Dynamics OData 클라우드 서비스를 구성한 후 양식 데이터 모델(FDM)을 만드는 동안 이 서비스를 사용할 수 있습니다. 자세한 내용은 [FDM(양식 데이터 모델) 만들기](create-form-data-models.md)를 참조하십시오.

다음으로 적응형 양식 기반 양식 데이터 모델(FDM)을 만들어 다음과 같은 다양한 적응형 양식 사용 사례에 사용할 수 있습니다.

* [!DNL Microsoft Dynamics] 엔터티 및 서비스의 정보를 쿼리하여 적응형 양식 미리 채우기
* 적응형 양식 규칙을 사용하여 FDM(양식 데이터 모델)에 정의된 [!DNL Microsoft Dynamics] 서버 작업 호출
* 제출된 양식 데이터를 [!DNL Microsoft Dynamics] 엔터티에 쓰기

<!--It is recommended to create a copy of the Form Data Model provided with the [!DNL Experience Manager Forms] package and configure data models and services to suit your requirements. It will ensure that any future updates to the package do not override your form data model.-->

적응형 양식에 대해 [양식 데이터 모델 제출 액션을 구성](/help/forms/using-form-data-model.md)하여 Microsoft Dynamics OData로 데이터를 보낼 수 있습니다.

비즈니스 워크플로우에서 양식 데이터 모델(FDM)을 만들고 사용하는 방법에 대한 자세한 내용은 [데이터 통합](data-integration.md)을 참조하십시오.

## 관련 문서

{{af-submit-action}}
