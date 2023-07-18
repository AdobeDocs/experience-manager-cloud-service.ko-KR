---
title: 적응형 양식을 위한 기본 양식 데이터 모델을 사용하여 Microsoft Dynamics 365 및 Salesforce를 구성하는 방법
description: Microsoft Dynamics 365 및 Salesforce를 적응형 양식과 통합하는 방법을 알아봅니다.
exl-id: 2a43b2db-2dfb-4c79-88be-ea770b44dac1
source-git-commit: b6dcb6308d1f4af7a002671f797db766e5cfe9b5
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 2%

---

# [!DNL Microsoft Dynamics 365]및[!DNL Salesforce]Cloud Service 구성 {#configure-azure-storage}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | 이 문서 |

[[!DNL Experience Manager Forms] 데이터 통합](data-integration.md) 다음을 제공합니다 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 적응형 양식을 즉시 사용할 수 있는 양식 데이터 모델과 통합하는 클라우드 서비스 그런 다음 적응형 Forms은 와 상호 작용할 수 있습니다. [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 비즈니스 워크플로를 활성화하는 서버입니다. 예:

* 에 데이터 쓰기 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 을 참조하십시오.
* 데이터 쓰기 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 를 통해 양식 데이터 모델에 정의된 사용자 지정 엔티티 또는 그 반대로
* 쿼리 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 서버입니다. 또한 적응형 Forms을 미리 채웁니다.
* 데이터 읽기 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 서버입니다.

[!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 클라우드 서비스 및 양식 데이터 모델은 [!DNL AEM Forms] 서버 [Experience Manager archetype을 기반으로 Forms용 개발 프로젝트 설정](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Microsoft Dynamics 365 [!DNL Salesforce] 클라우드 서비스 및 양식 데이터 모델은 를 설정하는 경우에만 즉시 사용할 수 있습니다. [!DNL Experience Manager Forms] as a [!DNL Cloud Service] 프로젝트 기준 [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) 나중에

## 구성 [!DNL Salesforce] 클라우드 서비스 {#configure-salesforce-cloud-service}

을(를) 구성하기 전에 [!DNL Salesforce] cloud services에서 다음 작업을 수행하는지 확인합니다.

* [연결된 OAuth 활성화 만들기 [!DNL Salesforce] 애플리케이션](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&amp;type=5). 연결된 을(를) 만드는 경우 [!DNL Salesforce] 응용 프로그램에서 콜백 URL을 다음 형식으로 지정합니다.

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  여기서 서버 및 포트는 의 호스트 이름과 포트 번호를 나타냅니다. [!DNL AEM Forms] 서버입니다.

* 연결된 을(를) 만드는 동안 [!DNL Salesforce] 응용 프로그램, 지정 `full` 및 `offline_access` 를 OAuth 범위 값으로 사용합니다.

* 연결된 애플리케이션의 클라이언트 ID(소비자 키라고 함) 및 클라이언트 암호(소비자 암호라고 함)에 대한 값을 기록해 둡니다.

다음 단계를 수행하여 을 구성합니다 [!DNL Salesforce] 클라우드 서비스:

1. 날짜 [!DNL AEM Forms] 작성자 인스턴스, 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL 데이터 소스]**. 사용 가능한 래퍼 폴더 목록에에 제목이 지정된 폴더가 포함됩니다. `DappTitle`  while [AEM Archetype 프로젝트 생성](setup-local-development-environment.md##forms-cloud-service-local-development-environment).
1. 폴더 이름을 탭하고 다음을 선택합니다. **[!UICONTROL Salesforce 클라우드 구성]**, 및 탭 **[!UICONTROL 속성]**.
1. 다음에서 **[!UICONTROL 인증 설정]** 탭:
   1. 다음을 지정합니다. [!DNL Salesforce] 의 도메인 URL **[!UICONTROL 호스트]** 필드. 예를 들어, [도메인 이름].my.salesforce.com입니다.
   1. 연결된 애플리케이션에 대한 클라이언트 ID(소비자 키라고 함)와 클라이언트 암호(소비자 암호라고 함)를 지정합니다.
   1. 지정 **full offline_access** (`full` 및 `offine_access` 값(공백)으로 구분됨 **[!UICONTROL 인증 범위]** 필드.
   1. 누르기 **[!UICONTROL OAuth에 연결]**. (으)로 리디렉션됩니다. [!DNL Microsoft Dynamics] 로그인 페이지입니다.
   1. 로 로그인 [!DNL Salesforce] 자격 증명 및 동의 를 선택하여 cloud service 구성 연결 [!DNL Salesforce] 서비스. 연결에 성공하면 로 리디렉션됩니다. [!DNL Salesforce] 성공 메시지를 표시하는 클라우드 서비스 구성 페이지
1. 누르기 **[!UICONTROL 저장 및 닫기]** 구성 설정을 완료합니다.

### 즉시 사용 가능한 액세스 [!DNL Salesforce] 양식 데이터 모델

A [!DNL Salesforce] 양식 데이터 모델은 [!DNL AEM Forms] 서버 [Experience Manager archetype을 기반으로 Forms용 개발 프로젝트 설정](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

양식 데이터 모델에 액세스하려면 다음으로 이동합니다. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL 데이터 통합]**. 사용 가능한 폴더 목록에는 제목이 지정된 폴더가 포함됩니다. `DappTitle`  while [AEM Archetype 프로젝트 생성](setup-local-development-environment.md##forms-cloud-service-local-development-environment). 폴더 이름을 탭하고 **[!UICONTROL Salesforce 데이터 모델]**&#x200B;을 클릭하고 편집을 탭합니다 ![편집](assets/edit.png) 양식 데이터 모델을 보기 위한 아이콘입니다.

구성 후 [[!DNL Salesforce] 클라우드 구성 서비스](#configure-salesforce-cloud-service)를 사용하면 적응형 양식을 즉시 통합할 수 있습니다 [!DNL Salesforce] 데이터 모델.

## 구성 [!DNL Microsoft Dynamics 365] 클라우드 서비스 {#configure-dynamics-cloud-service}

을(를) 구성하기 전에 [!DNL Microsoft Dynamics 365] cloud service, 다음 작업을 수행하는지 확인합니다.

* [다음에 대한 애플리케이션 등록 [!DNL Microsoft Dynamics 365] azure Active Directory 사용](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/walkthrough-register-app-azure-active-directory). 연결된 을(를) 만드는 경우 [!DNL Microsoft Dynamics 365] 응용 프로그램에서 다음 형식으로 회신 URL을 지정합니다.

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  여기서 서버 및 포트는 의 호스트 이름과 포트 번호를 나타냅니다. [!DNL AEM Forms] 서버입니다.

* 클라이언트 ID(애플리케이션 ID라고도 함) 및 연결된 애플리케이션의 클라이언트 암호 값을 기록해 두십시오.

다음 단계를 수행하여 을 구성합니다 [!DNL Microsoft Dynamics 365] 클라우드 서비스:

1. 날짜 [!DNL AEM Forms] 작성자 인스턴스, 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL 데이터 소스]**. 사용 가능한 래퍼 폴더 목록에에 제목이 지정된 폴더가 포함됩니다. `DappTitle`  while [AEM Archetype 프로젝트 생성](setup-local-development-environment.md##forms-cloud-service-local-development-environment).
1. 폴더 이름을 탭하고 다음을 선택합니다. **[!UICONTROL Microsoft Dynamics 365 클라우드 구성]**, 및 탭 **[!UICONTROL 속성]**.
1. 다음에서 **[!UICONTROL 인증 설정]** 탭:
   1. 다음에 대한 값 입력 **[!UICONTROL 서비스 루트]** 필드. Dynamics 인스턴스로 이동하여 다음 위치로 이동 [개발자 리소스](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/view-download-developer-resources) 서비스 루트 필드에 대한 값을 보려면 다음을 수행하십시오. 예, `https://<tenant-name>.dynamics.com/api/data/v9.1/`
   1. 연결된 응용 프로그램에 대한 클라이언트 ID(응용 프로그램 ID라고도 함)와 클라이언트 암호를 지정합니다.
   1. 바꾸기 `{tenant}` 다음에 테넌트 ID가 있는 **[!UICONTROL OAuth URL]**, **[!UICONTROL 토큰 URL 새로 고침]**, 및 **[!UICONTROL 토큰 URL 액세스]** 필드.
   1. 에서 동적 인스턴스 URL 지정 **[!UICONTROL 리소스]** 구성할 필드 [!UICONTROL Microsoft Dynamics] (양식 데이터 모델 포함) 서비스 루트 URL을 사용하여 Dynamics 인스턴스 URL을 파생합니다. (예: `https://<tenant-name>.dynamics.com`)

   1. 지정 `openid` 다음에서 **[!UICONTROL 인증 범위]** 인증 프로세스용 필드 [!DNL Microsoft Dynamics 365].
   1. 로 로그인 [!DNL Microsoft Dynamics 365] 자격 증명 및 동의 를 선택하여 cloud service 구성 연결 [!DNL Microsoft Dynamics 365] 서비스. 연결에 성공하면 로 리디렉션됩니다. [!DNL Microsoft Dynamics 365] 성공 메시지를 표시하는 클라우드 서비스 구성 페이지
1. 누르기 **[!UICONTROL 저장 및 닫기]** 구성 설정을 완료합니다.

### 즉시 사용 가능한 액세스 [!DNL Microsoft Dynamics 365] 양식 데이터 모델

A [!DNL Microsoft Dynamics 365] 양식 데이터 모델은 [!DNL AEM Forms] 서버 [Experience Manager archetype을 기반으로 Forms용 개발 프로젝트 설정](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

양식 데이터 모델에 액세스하려면 다음으로 이동합니다. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL 데이터 통합]**. 사용 가능한 폴더 목록에는 제목이 지정된 폴더가 포함됩니다. `DappTitle`  while [AEM Archetype 프로젝트 생성](setup-local-development-environment.md##forms-cloud-service-local-development-environment). 폴더 이름을 탭하고 **[!UICONTROL Microsoft Dynamics 365 데이터 모델]**&#x200B;을 클릭하고 편집을 탭합니다 ![편집](assets/edit.png) 양식 데이터 모델을 보기 위한 아이콘입니다.

구성 후 [[!DNL Microsoft Dynamics 365] 클라우드 구성 서비스](#configure-dynamics-cloud-service)를 사용하면 적응형 양식을 즉시 통합할 수 있습니다 [!DNL Microsoft Dynamics 365] 데이터 모델.
