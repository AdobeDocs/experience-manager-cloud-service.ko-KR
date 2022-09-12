---
title: 구성 방법 [!DNL Microsoft Dynamics] OData?
description: 에 정의된 엔티티, 속성 및 서비스를 기반으로 양식 데이터 모델을 만드는 방법을 알아봅니다 [!DNL Microsoft Dynamics] 서비스. 양식 데이터 모델 을 사용하여 와 상호 작용하는 적응형 Forms을 만들 수 있습니다 [!DNL Microsoft Dynamics] 비즈니스 워크플로우를 사용하도록 설정하는 서버입니다.
feature: Form Data Model
role: User, Developer
level: Beginner
exl-id: cb7b41f0-fd4f-4ba6-9f45-792a66ba6368
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 1%

---

# [!DNL Microsoft Dynamics] OData 구성 {#microsoft-dynamics-odata-configuration}

![데이터 통합](assets/data-integeration.png)

[!DNL Microsoft Dynamics] 는 고객 계정, 연락처, 리드, 기회 및 사례를 생성 및 관리하기 위한 엔터프라이즈 솔루션을 제공하는 CRM(Customer Relationship Management) 및 ERP(Enterprise Resource Planning) 소프트웨어입니다. [[!DNL Experience Manager Forms] 데이터 통합](data-integration.md) 은 Forms을 온라인 및 온프레미스 모두와 통합하는 OData 클라우드 서비스 구성을 제공합니다 [!DNL Microsoft Dynamics] server. 에 정의된 엔티티, 속성 및 서비스를 기반으로 양식 데이터 모델을 만들 수 있습니다 [!DNL Microsoft Dynamics] 서비스. 양식 데이터 모델 을 사용하여 와 상호 작용하는 적응형 Forms을 만들 수 있습니다 [!DNL Microsoft Dynamics] 비즈니스 워크플로우를 사용하도록 설정하는 서버입니다. 예:

* 쿼리 [!DNL Microsoft Dynamics] 데이터를 위한 서버 및 적응형 Forms 미리 채우기
* 에 데이터 쓰기 [!DNL Microsoft Dynamics] 적응형 양식 제출 시
* 데이터 쓰기 위치 [!DNL Microsoft Dynamics] 양식 데이터 모델에 정의된 사용자 지정 엔티티 사용 및 그 반대의 경우

<!--[!DNL Experience Manager Forms] add-on package also includes reference OData configuration that you can use to quickly integrate [!DNL Microsoft Dynamics] with [!DNL Experience Manager Forms].-->

<!--When the package is installed, the following entities and services are available on your [!DNL Experience Manager Forms] instance:

* MS Dynamics OData Cloud Service (OData Service)-->
<!--* Form Data Model with preconfigured [!DNL Microsoft Dynamics] entities and services.-->

<!-- Preconfigured [!DNL Microsoft Dynamics] entities and services in a Form Data Model are available on your [!DNL Experience Manager Forms] instance only if the run mode for the [!DNL Experience Manager] instance is set as `samplecontent` (default). -->  MS Dynamics OData Cloud Service (OData Service) is available with all run modes. For more information on configuring run modes for an [!DNL Experience Manager] instance, see [Run Modes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#runmodes).

## 사전 요구 사항 {#prerequisites}

설정 및 구성을 시작하기 전에 [!DNL Microsoft Dynamics]를 채울 수 있습니다.

<!--* Installed the [[!DNL Experience Manager Forms] add-on package](installing-configuring-aem-forms-osgi.md) -->
* 구성됨 [!DNL Microsoft Dynamics] 365 온라인 또는 다음 중 하나의 인스턴스 설치 [!DNL Microsoft Dynamics] 버전:

   * [!DNL Microsoft Dynamics] 구내 365
   * [!DNL Microsoft Dynamics] 2016년 온프레미스

* [응용 프로그램을 등록했습니다. [!DNL Microsoft Dynamics] 온라인 서비스 [!DNL Microsoft Azure] Active Directory](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). 등록된 서비스에 대한 클라이언트 ID(애플리케이션 ID라고도 함)와 클라이언트 암호 값을 기록해 두십시오. 이러한 값은 [에 대한 cloud service 구성 [!DNL Microsoft Dynamics] 서비스](#configure-cloud-service-for-your-microsoft-dynamics-service).

## 등록된 회신 URL 설정 [!DNL Microsoft Dynamics] 애플리케이션 {#set-reply-url-for-registered-microsoft-dynamics-application}

등록된 회신 URL을 설정하려면 다음을 수행하십시오 [!DNL Microsoft Dynamics] 애플리케이션:

>[!NOTE]
>
>통합할 때만 이 절차를 사용합니다 [!DNL Experience Manager Forms] 온라인으로 사용 [!DNL Microsoft Dynamics] server.

1. 이동 [!DNL Microsoft Azure] Active Directory 계정을 추가하고 다음 클라우드 서비스 구성 URL을 **[!UICONTROL 회신 URL]** 등록된 응용 프로그램에 대한 설정:

   `https://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![Azure 디렉토리](assets/azure_directory_new.png)

1. 구성을 저장합니다.

## 구성 [!DNL Microsoft Dynamics] IFD용 {#configure-microsoft-dynamics-for-ifd}

[!DNL Microsoft Dynamics] 에서는 클레임 기반 인증을 사용하여 [!DNL Microsoft Dynamics] 외부 사용자에게 CRM 서버. 이를 활성화하려면 다음을 수행하여 구성합니다 [!DNL Microsoft Dynamics] IFD(인터넷 연결 배포) 및 클레임 설정 구성

>[!NOTE]
>
>통합할 때만 이 절차를 사용합니다 [!DNL Experience Manager Forms] 온프레미스 사용 [!DNL Microsoft Dynamics] server.

1. 구성 [!DNL Microsoft Dynamics] 에 설명된 대로 IFD에 대한 온-프레미스 인스턴스 [에 대한 IFD 구성 [!DNL Microsoft Dynamics]](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Windows PowerShell을 사용하여 다음 명령을 실행하여 IFD 사용 시 클레임 설정을 구성합니다 [!DNL Microsoft Dynamics]:

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   자세한 내용은 [CRM 온프레미스(IFD)에 대한 앱 등록](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) 자세한 내용

## AD FS 시스템에서 OAuth 클라이언트 구성 {#configure-oauth-client-on-ad-fs-machine}

AD FS(Active Directory Federation Services) 시스템에 OAuth 클라이언트를 등록하고 AD FS 컴퓨터에 대한 액세스 권한을 부여하려면 다음을 수행합니다.

>[!NOTE]
>
>통합할 때만 이 절차를 사용합니다 [!DNL Experience Manager Forms] 온프레미스 사용 [!DNL Microsoft Dynamics] server.

1. 다음 명령을 실행합니다.

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   위치:

   * `Client-ID` 는 GUID 생성기를 사용하여 생성할 수 있는 클라이언트 ID입니다.
   * `redirect-uri` 는 URL의 [!DNL Microsoft Dynamics] 의 OData 클라우드 서비스 [!DNL Experience Manager Forms]. 와 함께 설치된 기본 클라우드 서비스 [!DNL Experience Manager Forms] 는 다음 URL에 배포됩니다.
      `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. 다음 명령을 실행하여 AD FS 컴퓨터에 대한 액세스 권한을 부여합니다.

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   위치:

   * `resource` 은 [!DNL Microsoft Dynamics] 조직 URL.

1. [!DNL Microsoft Dynamics] 은 HTTPS 프로토콜을 사용합니다. 에서 AD FS 끝점을 호출하려면 [!DNL Forms] 서버, 설치 [!DNL Microsoft Dynamics] 를 사용하여 Java 인증서 저장소에 사이트 인증서 `keytool` 실행 중인 컴퓨터의 명령 [!DNL Experience Manager Forms].

## 에 대한 클라우드 서비스 구성 [!DNL Microsoft Dynamics] 서비스 {#configure-cloud-service-for-your-microsoft-dynamics-service}

OData 서비스는 서비스 루트 URL로 식별됩니다. 에서 OData 서비스를 구성하려면 [!DNL Experience Manager] as a Cloud Service 서비스에 대한 서비스 루트 URL이 있는지 확인하고 다음을 수행합니다.

<!--The **MS Dynamics OData Cloud Service (OData Service)** configuration comes with default OData configuration. To configure it to connect with your [!DNL Microsoft Dynamics] service, do the following.-->

>[!NOTE]
>
>구성을 위한 단계별 안내서입니다. [!DNL Microsoft Dynamics 365], 온라인 또는 온프레미스에서 다음을 참조하십시오. [[!DNL Microsoft Dynamics] OData 구성](ms-dynamics-odata-configuration.md).

1. 이동 **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**. 클라우드 구성을 만들 폴더를 선택하려면 탭합니다.

   자세한 내용은 [클라우드 서비스 구성에 대한 폴더 구성](#cloud-folder) 클라우드 서비스 구성용 폴더 만들기 및 구성에 대한 자세한 내용은 을 참조하십시오.

1. 탭 **[!UICONTROL 만들기]** 열다 **[!UICONTROL 데이터 소스 구성 만들기 마법사]**. 구성 이름과 선택적으로 제목을 지정하고 **[!UICONTROL OData 서비스]** 에서 **[!UICONTROL 서비스 유형]** 드롭다운, 원하는 경우 구성에 대한 축소판 이미지를 찾아 선택한 다음 탭합니다 **[!UICONTROL 다음]**.
에서 **[!UICONTROL 인증 설정]** 탭:

   1. 값 입력 **[!UICONTROL 서비스 루트]** 필드. Dynamics 인스턴스로 이동하고 **[!UICONTROL 개발자 리소스]** 서비스 루트 필드의 값을 보려면 예: https://&lt;tenant-name>/api/data/v9.1/

   1. 선택 **[!UICONTROL OAuth 2.0]** 인증 유형으로 사용할 수 있습니다.

   1. 에서 기본값을 바꿉니다 **[!UICONTROL 클라이언트 Id]** (이하 **애플리케이션 ID**), **[!UICONTROL 클라이언트 암호]**, **[!UICONTROL OAuth URL]**, **[!UICONTROL 토큰 URL 새로 고침]**, **[!UICONTROL 액세스 토큰 URL]**, 및 **[!UICONTROL 리소스]** 값이 있는 필드 [!DNL Microsoft Dynamics] 서비스 구성. 에서 dynamics 인스턴스 URL을 지정해야 합니다 **[!UICONTROL 리소스]** 구성할 필드 [!DNL Microsoft Dynamics] 사용할 수 있습니다. 서비스 루트 URL을 사용하여 Dynamics 인스턴스 URL을 파생하십시오. 예, [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).

   1. 지정 **[!UICONTROL openid]** 에서 **[!UICONTROL 권한 부여 범위]** 인증 프로세스 필드 [!DNL Microsoft Dynamics].

      ![인증 설정](assets/dynamics_authentication_settings_new.png)
양식 데이터 모델
1. 클릭 **[!UICONTROL OAuth에 연결]**. 으로 리디렉션됩니다. [!DNL Microsoft Dynamics] 로그인 페이지.
1. 로 로그인 [!DNL Microsoft Dynamics] 클라우드 서비스 구성이 연결되도록 하는 자격 증명 및 동의 [!DNL Microsoft Dynamics] 서비스. 클라우드 서비스와 서비스 간에 양식 데이터 모델을 설정하는 것은 일회성 작업입니다.

   OData 구성이 성공적으로 저장되었다는 메시지가 표시되는 클라우드 서비스 구성 페이지의 양식 데이터 모델입니다.

MS Dynamics OData Cloud Service(OData 서비스) 클라우드 서비스가 구성되어 Dynamics 서비스와 연결되어 있습니다. 양식 데이터 모델 양식 데이터 모델

## 양식 데이터 모델 만들기 {#create-form-data-model}

<!--When you install the [!DNL Experience Manager Forms] package, a form data model, **[!DNL Microsoft Dynamics] FDM**, is deployed on your [!DNL Experience Manager] instance. By default, the Form Data Model uses [!DNL Microsoft Dynamics] service configured in the MS Dynamics OData Cloud Service (OData Service) as its data source.

On opening the Form Data Model for the first time, it connects to the configured [!DNL Microsoft Dynamics] service and fetches entities from your [!DNL Microsoft Dynamics] instance. The "contact" and "lead" entities from [!DNL Microsoft Dynamics] are already added in the form data model.

To review the form data model, go to **[!UICONTROL Form Data Model egrations]**. Select **[!DNL Microsoft Dynamics] FDM** and click **[!UICONTROL Edit]** to open the Form Data Model in edit mode. Alternatively, you can open the Form Data Model directly from the following URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`
 Form Data Model 
![default-fdm-1](assets/default-fdm-1.png)-->

MS Dynamics OData 클라우드 사용자 양식 데이터 모델 ce) 클라우드 서비스를 구성한 후 양식 데이터 모델을 만드는 동안 서비스를 사용할 수 있습니다. 자세한 내용은 [양식 데이터 모델 만들기](create-form-data-models.md).

다음으로, 양식 데이터 모델 모델을 기반으로 적응형 양식을 만들고 다음과 같은 다양한 적응형 양식 사용 사례에 사용할 수 있습니다.

* 다음에서 정보를 쿼리하여 적응형 양식 미리 채우기 [!DNL Microsoft Dynamics] 개체 및 서비스
* 호출 [!DNL Microsoft Dynamics] 적응형 양식 규칙을 사용하여 양식 데이터 모델에 정의된 서버 작업
* 제출된 양식 데이터를에 쓰기 [!DNL Microsoft Dynamics] 개체

<!--It is recommended to create a copy of the Form Data Model provided with the [!DNL Experience Manager Forms] package and configure data models and services to suit your requirements. It will ensure that any future updates to the package do not override your form data model.-->

비즈니스 워크플로우에서 양식 데이터 모델을 만들고 사용하는 방법에 대한 자세한 내용은 [데이터 통합](data-integration.md).
