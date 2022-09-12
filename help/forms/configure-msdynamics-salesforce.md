---
title: 적응형 양식에 대한 기본 양식 데이터 모델에서 Microsoft Dynamics 365 및 Salesforce를 구성하는 방법
description: Microsoft Dynamics 365 및 Salesforce를 적응형 양식과 통합하는 방법을 알아봅니다.
exl-id: 2a43b2db-2dfb-4c79-88be-ea770b44dac1
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 1%

---

# [!DNL Microsoft Dynamics 365]및[!DNL Salesforce]클라우드 서비스 구성 {#configure-azure-storage}

[[!DNL Experience Manager Forms] 데이터 통합](data-integration.md) 제공 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 클라우드 서비스를 통해 적응형 양식을 기본 양식 데이터 모델과 통합할 수 있습니다. 그러면 적응형 Forms이 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 비즈니스 워크플로우를 활성화하는 서버 예:

* 에 데이터 쓰기 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 적응형 양식 제출에서 참조할 수 있습니다.
* 데이터 쓰기 위치 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 양식 데이터 모델에 정의된 사용자 지정 엔티티를 통해 또는 그 반대의 경우도 마찬가지입니다.
* 쿼리 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 데이터를 위한 서버 및 적응형 Forms 미리 채우기.
* 데이터 읽기 [!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] server.

[!DNL Microsoft Dynamics 365] 및 [!DNL Salesforce] 클라우드 서비스 및 양식 데이터 모델은 [!DNL AEM Forms] 서버 [Experience Manager 원형 기반 Forms용 개발 프로젝트 설정](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Microsoft Dynamics 365 및 [!DNL Salesforce] 클라우드 서비스 및 양식 데이터 모델은 [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] 프로젝트 기반 [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) 또는 나중에 사용합니다.

## 구성 [!DNL Salesforce] 클라우드 서비스 {#configure-salesforce-cloud-service}

구성하기 전에 [!DNL Salesforce] cloud services에서 다음 작업을 수행해야 합니다.

* [연결된 OAuth 지원 만들기 [!DNL Salesforce] 애플리케이션](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&amp;type=5). 연결된 파일을 만들 때 [!DNL Salesforce] 응용 프로그램에서 콜백 URL을 다음 형식으로 지정합니다.

   ```
   https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
   ```

   서버 및 포트가 의 호스트 이름 및 포트 번호를 참조하는 경우 [!DNL AEM Forms] server.

* 연결된 항목을 만드는 동안 [!DNL Salesforce] 응용 프로그램, 지정 `full` 및 `offline_access` 를 입력합니다.

* 연결된 응용 프로그램에 대한 클라이언트 ID(소비자 키라고도 함) 및 클라이언트 암호(소비자 암호라고 함)의 값을 주목하십시오.

다음 단계를 수행하여 을 구성합니다 [!DNL Salesforce] 클라우드 서비스:

1. 설정 [!DNL AEM Forms] 작성자 인스턴스, 탐색 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL 데이터 소스]**. 사용 가능한 래퍼 폴더 목록에는 제목이 지정된 폴더가 포함됩니다 `DappTitle`  while [AEM 원형 프로젝트 생성](setup-local-development-environment.md##forms-cloud-service-local-development-environment).
1. 폴더 이름을 탭하고 을 선택합니다. **[!UICONTROL Salesforce Cloud 구성]**, 탭 **[!UICONTROL 속성]**.
1. 에서 **[!UICONTROL 인증 설정]** 탭:
   1. 을(를) 지정합니다. [!DNL Salesforce] 의 도메인 URL **[!UICONTROL 호스트]** 필드. 예, [도메인 이름].my.salesforce.com
   1. 연결된 응용 프로그램에 대한 클라이언트 ID(소비자 키라고도 함)와 클라이언트 암호(소비자 암호라고도 함)를 지정합니다.
   1. 지정 **full offline_access** (`full` 및 `offine_access` 에서 공백으로 구분된 값) **[!UICONTROL 권한 부여 범위]** 필드.
   1. 탭 **[!UICONTROL OAuth에 연결]**. 으로 리디렉션됩니다. [!DNL Microsoft Dynamics] 로그인 페이지.
   1. 로 로그인 [!DNL Salesforce] 클라우드 서비스 구성이 연결되도록 하는 자격 증명 및 동의 [!DNL Salesforce] 서비스. 연결에 성공하면 [!DNL Salesforce] 성공 메시지를 표시하는 클라우드 서비스 구성 페이지입니다.
1. 탭 **[!UICONTROL 저장 및 닫기]** 구성 설정을 완료하려면

### 즉시 사용 가능 [!DNL Salesforce] 양식 데이터 모델

A [!DNL Salesforce] 양식 데이터 모델은 [!DNL AEM Forms] 서버 [Experience Manager 원형 기반 Forms용 개발 프로젝트 설정](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

양식 데이터 모델에 액세스하려면 다음 위치로 이동합니다. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL 데이터 통합]**. 사용 가능한 폴더 목록에는 제목이 지정된 폴더가 포함됩니다 `DappTitle`  while [AEM 원형 프로젝트 생성](setup-local-development-environment.md##forms-cloud-service-local-development-environment). 폴더 이름을 탭하고 **[!UICONTROL Salesforce 데이터 모델]**&#x200B;를 누르고 편집을 누릅니다 ![편집](assets/edit.png) 아이콘을 클릭하여 양식 데이터 모델을 확인합니다.

구성 후 [[!DNL Salesforce] 클라우드 구성 서비스](#configure-salesforce-cloud-service)을 사용하면 적응형 양식을 즉시 통합할 수 있습니다 [!DNL Salesforce] 데이터 모델.

## 구성 [!DNL Microsoft Dynamics 365] 클라우드 서비스 {#configure-dynamics-cloud-service}

구성하기 전에 [!DNL Microsoft Dynamics 365] cloud service에서 다음 작업을 수행해야 합니다.

* [응용 프로그램 등록 [!DNL Microsoft Dynamics 365] Azure Active Directory 사용](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/walkthrough-register-app-azure-active-directory). 연결된 파일을 만들 때 [!DNL Microsoft Dynamics 365] 응용 프로그램에서 회신 URL을 다음 형식으로 지정합니다.

   ```
   https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
   ```

   서버 및 포트가 의 호스트 이름 및 포트 번호를 참조하는 경우 [!DNL AEM Forms] server.

* 연결된 응용 프로그램의 클라이언트 ID(응용 프로그램 ID라고도 함)와 클라이언트 암호 값을 기록해 둡니다.

다음 단계를 수행하여 을 구성합니다 [!DNL Microsoft Dynamics 365] 클라우드 서비스:

1. 설정 [!DNL AEM Forms] 작성자 인스턴스, 탐색 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL 데이터 소스]**. 사용 가능한 래퍼 폴더 목록에는 제목이 지정된 폴더가 포함됩니다 `DappTitle`  while [AEM 원형 프로젝트 생성](setup-local-development-environment.md##forms-cloud-service-local-development-environment).
1. 폴더 이름을 탭하고 을 선택합니다. **[!UICONTROL Microsoft Dynamics 365 클라우드 구성]**, 탭 **[!UICONTROL 속성]**.
1. 에서 **[!UICONTROL 인증 설정]** 탭:
   1. 값 입력 **[!UICONTROL 서비스 루트]** 필드. Dynamics 인스턴스로 이동하고 [개발자 리소스](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/view-download-developer-resources) 서비스 루트 필드의 값을 보려면 예, `https://<tenant-name>.dynamics.com/api/data/v9.1/`
   1. 연결된 응용 프로그램의 클라이언트 ID(응용 프로그램 ID라고도 함)와 클라이언트 암호를 지정합니다.
   1. 바꾸기 `{tenant}` 에서 테넌트 ID를 사용하여 **[!UICONTROL OAuth URL]**, **[!UICONTROL 토큰 URL 새로 고침]**, 및 **[!UICONTROL 액세스 토큰 URL]** 필드.
   1. 에서 dynamics 인스턴스 URL을 지정합니다 **[!UICONTROL 리소스]** 구성할 필드 [!UICONTROL Microsoft Dynamics] ( 양식 데이터 모델 사용) 서비스 루트 URL을 사용하여 Dynamics 인스턴스 URL을 파생하십시오. (예: `https://<tenant-name>.dynamics.com`)

   1. 지정 `openid` 에서 **[!UICONTROL 권한 부여 범위]** 인증 프로세스 필드 [!DNL Microsoft Dynamics 365].
   1. 로 로그인 [!DNL Microsoft Dynamics 365] 클라우드 서비스 구성이 연결되도록 하는 자격 증명 및 동의 [!DNL Microsoft Dynamics 365] 서비스. 연결에 성공하면 [!DNL Microsoft Dynamics 365] 성공 메시지를 표시하는 클라우드 서비스 구성 페이지입니다.
1. 탭 **[!UICONTROL 저장 및 닫기]** 구성 설정을 완료하려면

### 즉시 사용 가능 [!DNL Microsoft Dynamics 365] 양식 데이터 모델

A [!DNL Microsoft Dynamics 365] 양식 데이터 모델은 [!DNL AEM Forms] 서버 [Experience Manager 원형 기반 Forms용 개발 프로젝트 설정](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

양식 데이터 모델에 액세스하려면 다음 위치로 이동합니다. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL 데이터 통합]**. 사용 가능한 폴더 목록에는 제목이 지정된 폴더가 포함됩니다 `DappTitle`  while [AEM 원형 프로젝트 생성](setup-local-development-environment.md##forms-cloud-service-local-development-environment). 폴더 이름을 탭하고 **[!UICONTROL Microsoft Dynamics 365 데이터 모델]**&#x200B;를 누르고 편집을 누릅니다 ![편집](assets/edit.png) 아이콘을 클릭하여 양식 데이터 모델을 확인합니다.

구성 후 [[!DNL Microsoft Dynamics 365] 클라우드 구성 서비스](#configure-dynamics-cloud-service)을 사용하면 적응형 양식을 즉시 통합할 수 있습니다 [!DNL Microsoft Dynamics 365] 데이터 모델.
