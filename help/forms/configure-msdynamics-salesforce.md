---
title: 적응형 Forms을 위한 기본 양식 데이터 모델을 통해 Microsoft Dynamics 365 및 Salesforce를 구성하는 방법
description: Microsoft Dynamics 365 및 Salesforce를 적응형 Forms과 통합하는 방법을 알아봅니다.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 2a43b2db-2dfb-4c79-88be-ea770b44dac1
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 2%

---

# Microsoft® Dynamics 365 또는 AEM Forms용 Salesforce 구성 {#configure-azure-storage}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | 이 문서 |

[[!DNL Experience Manager Forms] 데이터 통합](data-integration.md)은(는) 적응형 양식을 기본 양식 데이터 모델(FDM)과 통합하기 위해 [!DNL Microsoft® Dynamics 365] 및 [!DNL Salesforce] 클라우드 서비스를 제공합니다. 그런 다음 적응형 Forms은 [!DNL Microsoft® Dynamics 365] 및 [!DNL Salesforce] 서버와 상호 작용하여 비즈니스 워크플로우를 사용할 수 있습니다. 예:

* 적응형 양식 제출 시 [!DNL Microsoft® Dynamics 365] 및 [!DNL Salesforce]에 데이터를 작성하십시오.
* FDM(양식 데이터 모델)에 정의된 사용자 지정 엔터티를 통해 [!DNL Microsoft® Dynamics 365] 및 [!DNL Salesforce]에 데이터를 쓰고, 반대로 작성합니다.
* [!DNL Microsoft® Dynamics 365] 및 [!DNL Salesforce] 서버에 데이터를 쿼리하고 적응형 Forms을 미리 채웁니다.
* [!DNL Microsoft® Dynamics 365] 및 [!DNL Salesforce] 서버에서 데이터를 읽습니다.

[Experience Manager Archetype을 기반으로 Forms용 개발 프로젝트를 설정](setup-local-development-environment.md#forms-cloud-service-local-development-environment)한 후 [!DNL Microsoft® Dynamics 365] 및 [!DNL Salesforce] 클라우드 서비스와 FDM(양식 데이터 모델)을 [!DNL AEM Forms] 서버에서 즉시 사용할 수 있습니다.

>[!NOTE]
>
>Microsoft® Dynamics 365 및 [!DNL Salesforce] 클라우드 서비스와 FDM(양식 데이터 모델)은 [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) 이상을 기반으로 [!DNL Experience Manager Forms]을(를) [!DNL Cloud Service] 프로젝트로 설정하는 경우에만 즉시 사용할 수 있습니다.

## [!DNL Salesforce] 클라우드 서비스 구성 {#configure-salesforce-cloud-service}

[!DNL Salesforce] 클라우드 서비스를 구성하기 전에 다음 작업을 수행하는지 확인하십시오.

* [연결된 OAuth 사용 가능 [!DNL Salesforce] 응용 프로그램](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&amp;type=5)을 만듭니다. 연결된 [!DNL Salesforce] 응용 프로그램을 만드는 경우 다음 형식으로 콜백 URL을 지정하십시오.

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  여기서 서버 및 포트는 [!DNL AEM Forms] 서버의 호스트 이름과 포트 번호를 나타냅니다.

* 연결된 [!DNL Salesforce] 응용 프로그램을 만드는 동안 `full` 및 `offline_access`을(를) OAuth 범위의 값으로 지정하십시오.

* 연결된 애플리케이션의 클라이언트 ID(소비자 키라고 함) 및 클라이언트 암호(소비자 암호라고 함)에 대한 값을 기록해 둡니다.

[!DNL Salesforce] 클라우드 서비스를 구성하려면 다음 단계를 수행하십시오.

1. [!DNL AEM Forms] 작성자 인스턴스에서 **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL 데이터 소스]**&#x200B;로 이동합니다. 사용 가능한 래퍼 폴더 목록에는 [AEM Archetype 프로젝트를 생성](setup-local-development-environment.md#forms-cloud-service-local-development-environment)하는 동안 `DappTitle`에 대해 지정된 제목이 있는 폴더가 있습니다.
1. 폴더 이름을 선택하고 **[!UICONTROL Salesforce 클라우드 구성]**&#x200B;을 선택한 다음 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 인증 설정]** 탭에서:
   1. **[!UICONTROL 호스트]** 필드에 [!DNL Salesforce] 도메인 URL을 지정하십시오. 예: [Domain-name].my.salesforce.com.
   1. 연결된 애플리케이션에 대한 클라이언트 ID(소비자 키라고 함)와 클라이언트 암호(소비자 암호라고 함)를 지정합니다.
   1. **[!UICONTROL 권한 부여 범위]** 필드에 **full offline_access**(`full` 및 `offine_access` 값을 공백으로 구분)을 지정하십시오.
   1. **[!UICONTROL OAuth에 연결]**&#x200B;을 선택합니다. [!DNL Microsoft® Dynamics] 로그인 페이지로 리디렉션되었습니다.
   1. [!DNL Salesforce] 자격 증명으로 로그인하고 을(를) 수락하여 클라우드 서비스 구성이 [!DNL Salesforce] 서비스에 연결할 수 있도록 합니다. 연결이 성공하면 성공 메시지를 표시하는 [!DNL Salesforce] 클라우드 서비스 구성 페이지로 리디렉션됩니다.
1. 구성 설정을 완료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

### 기본 [!DNL Salesforce] 양식 데이터 모델(FDM) 액세스

[Experience Manager Archetype을 기반으로 Forms용 개발 프로젝트를 설정](setup-local-development-environment.md#forms-cloud-service-local-development-environment)한 후 [!DNL AEM Forms] 서버에서 [!DNL Salesforce] 양식 데이터 모델(FDM)을 즉시 사용할 수 있습니다.

양식 데이터 모델(FDM)에 액세스하려면 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL 데이터 통합]**&#x200B;으로 이동합니다. 사용 가능한 폴더 목록에는 [AEM Archetype 프로젝트를 생성](setup-local-development-environment.md#forms-cloud-service-local-development-environment)하는 동안 `DappTitle`에 대해 제목이 지정된 폴더가 포함됩니다. 폴더 이름을 선택하고 **[!UICONTROL Salesforce 데이터 모델]**&#x200B;을 선택한 다음 ![편집](assets/edit.png) 아이콘을 선택하여 FDM(양식 데이터 모델)을 봅니다.

[[!DNL Salesforce] 클라우드 구성 서비스](#configure-salesforce-cloud-service)를 구성한 후 적응형 양식을 기본 [!DNL Salesforce] 데이터 모델과 통합할 수 있습니다.

## [!DNL Microsoft® Dynamics 365] 클라우드 서비스 구성 {#configure-dynamics-cloud-service}

[!DNL Microsoft® Dynamics 365] 클라우드 서비스를 구성하기 전에 다음 작업을 수행하는지 확인하십시오.

* [Azure Active Directory에  [!DNL Microsoft® Dynamics 365] 응용 프로그램을 등록](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/walkthrough-register-app-azure-active-directory). 연결된 [!DNL Microsoft® Dynamics 365] 응용 프로그램을 만드는 경우 다음 형식으로 회신 URL을 지정하십시오.

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  여기서 서버 및 포트는 [!DNL AEM Forms] 서버의 호스트 이름과 포트 번호를 나타냅니다.

* 클라이언트 ID(애플리케이션 ID라고도 함) 및 연결된 애플리케이션의 클라이언트 암호 값을 기록해 두십시오.

[!DNL Microsoft® Dynamics 365] 클라우드 서비스를 구성하려면 다음 단계를 수행하십시오.

1. [!DNL AEM Forms] 작성자 인스턴스에서 **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL 데이터 소스]**&#x200B;로 이동합니다. 사용 가능한 래퍼 폴더 목록에는 [AEM Archetype 프로젝트를 생성](setup-local-development-environment.md#forms-cloud-service-local-development-environment)하는 동안 `DappTitle`에 대해 지정된 제목이 있는 폴더가 있습니다.
1. 폴더 이름을 선택하고 **[!UICONTROL Microsoft® Dynamics 365 클라우드 구성]**&#x200B;을 선택한 다음 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 인증 설정]** 탭에서:
   1. **[!UICONTROL 서비스 루트]** 필드에 대한 값을 입력하십시오. Dynamics 인스턴스로 이동하여 [개발자 리소스](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/view-download-developer-resources)(으)로 이동하여 서비스 루트 필드에 대한 값을 확인합니다. 예, `https://<tenant-name>.dynamics.com/api/data/v9.1/`
   1. 연결된 응용 프로그램에 대한 클라이언트 ID(응용 프로그램 ID라고도 함)와 클라이언트 암호를 지정합니다.
   1. `{tenant}`을(를) **[!UICONTROL OAuth URL]**, **[!UICONTROL 토큰 URL 새로 고침]** 및 **[!UICONTROL 액세스 토큰 URL]** 필드의 테넌트 ID로 바꾸십시오.
   1. **[!UICONTROL 리소스]** 필드에 Dynamics 인스턴스 URL을 지정하여 FDM(양식 데이터 모델)을 사용하여 [!UICONTROL Microsoft® Dynamics]을(를) 구성하십시오. 서비스 루트 URL을 사용하여 Dynamics 인스턴스 URL을 파생합니다. 예: `https://<tenant-name>.dynamics.com`

   1. [!DNL Microsoft® Dynamics 365]의 권한 부여 프로세스를 위해 **[!UICONTROL 권한 부여 범위]** 필드에 `openid`을(를) 지정하십시오.
   1. [!DNL Microsoft® Dynamics 365] 자격 증명으로 로그인하고 을(를) 수락하여 클라우드 서비스 구성이 [!DNL Microsoft® Dynamics 365] 서비스에 연결할 수 있도록 합니다. 연결이 성공하면 성공 메시지를 표시하는 [!DNL Microsoft® Dynamics 365] 클라우드 서비스 구성 페이지로 리디렉션됩니다.
1. 구성 설정을 완료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

### 기본 [!DNL Microsoft® Dynamics 365] 양식 데이터 모델(FDM) 액세스

[Experience Manager Archetype을 기반으로 Forms용 개발 프로젝트를 설정](setup-local-development-environment.md##forms-cloud-service-local-development-environment)한 후 [!DNL AEM Forms] 서버에서 [!DNL Microsoft® Dynamics 365] 양식 데이터 모델(FDM)을 즉시 사용할 수 있습니다.

양식 데이터 모델(FDM)에 액세스하려면 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL 데이터 통합]**&#x200B;으로 이동합니다. 사용 가능한 폴더 목록에는 [AEM Archetype 프로젝트를 생성](setup-local-development-environment.md#forms-cloud-service-local-development-environment)하는 동안 `DappTitle`에 대해 제목이 지정된 폴더가 포함됩니다. 폴더 이름을 선택하고 **[!UICONTROL Microsoft® Dynamics 365 데이터 모델]**&#x200B;을(를) 선택한 다음 ![편집](assets/edit.png) 아이콘을 선택하여 FDM(양식 데이터 모델)을 봅니다.

[[!DNL Microsoft® Dynamics 365] 클라우드 구성 서비스](#configure-dynamics-cloud-service)를 구성한 후 적응형 양식을 기본 [!DNL Microsoft® Dynamics 365] 데이터 모델과 통합할 수 있습니다.

>[!MORELIKETHIS]
>
>* [AEM Forms에 대한 데이터 소스 구성](/help/forms/configure-data-sources.md)
>* [AEM Forms에 대한 Azure 저장소 구성](/help/forms/configure-azure-storage.md)
>  [AEM Sites 페이지에 Forms 포털 추가](/help/forms/configure-forms-portal.md)
