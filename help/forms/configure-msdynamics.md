---
title: 적응형 Forms에 대한 기본 제공 양식 데이터 모델을 Microsoft Dynamics 365로 구성하는 방법
description: Microsoft Dynamics 365를 적응형 Forms과 통합하는 방법을 알아봅니다.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 29ee324c-cd4c-403b-bb3d-b1eda8e8ad88
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 2%

---


# Microsoft® Dynamics 365 for AEM Forms 구성

Adobe Experience Manager Forms 데이터 통합은 양식을 Microsoft Dynamics 서버와 통합하기 위한 클라우드 서비스 구성을 제공합니다. 이 옵션을 사용하면 Microsoft Dynamics 서비스에 정의된 엔티티, 속성 및 서비스를 기반으로 FDM(양식 데이터 모델)을 생성할 수 있습니다. 양식 데이터 모델(FDM)을 사용하여 Microsoft Dynamics 서버와 상호 작용하여 비즈니스 워크플로우를 가능하게 하는 적응형 Forms을 만들 수 있습니다. 예:

* Microsoft Dynamics 서버에 데이터를 쿼리하고 적응형 Forms을 미리 채웁니다.
* 적응형 양식 제출 시 Microsoft Dynamics에 데이터를 작성합니다.
* FDM(양식 데이터 모델)에 정의된 사용자 정의 엔티티를 통해 Microsoft Dynamics에서 데이터를 기록합니다.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.

<!-- 
[[!DNL Experience Manager Forms] Data Integration](data-integration.md) provides [!DNL Microsoft&reg; Dynamics 365] Cloud Services to integrate Adaptive Forms with out of the box Form Data Model (FDM). The Adaptive Forms can then interact with [!DNL Microsoft&reg; Dynamics 365] servers to enable business workflows. For example:

* Write data into [!DNL Microsoft&reg; Dynamics 365] on Adaptive Form submission.
* Write data in [!DNL Microsoft&reg; Dynamics 365] through custom entities defined in Form Data Model (FDM) and conversely.
* Query [!DNL Microsoft&reg; Dynamics 365]server for data and prepopulate Adaptive Forms.
* Read data from [!DNL Microsoft&reg; Dynamics 365] server.

[!DNL Microsoft&reg; Dynamics 365] cloud services and Form Data Model (FDM) are available out of the box on the [!DNL AEM Forms] Server after you [set up a development project for Forms based on Experience Manager archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Microsoft&reg; Dynamics 365 cloud services and Form Data Model (FDM) are available out of the box only if you set up an [!DNL Experience Manager Forms] as a [!DNL Cloud Service] project based on [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) or later.-->

## 사전 요구 사항

[!DNL Microsoft® Dynamics 365]을(를) AEM Forms as a Cloud Service과 통합하기 전에 다음 단계를 수행했는지 확인하십시오.


1. **Microsoft Dynamics 365에서 계정 설정**

   비디오에 설명된 단계에 따라 Microsoft Dynamics 365 계정을 설정합니다. 이 비디오에서는 데모용으로 체험판 계정이 만들어집니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3444389/)

1. **Power Platform 관리 센터에서 계정 만들기**

   **Power Platform 관리 센터**&#x200B;에서 계정을 만들어 다음을 수행할 수 있습니다.

   * Dataverse 추가
   * Microsoft Dynamics 365 응용 프로그램 활성화

   비디오의 단계에 따라 Power Platform 관리 센터에서 계정을 만듭니다. 이 비디오에서는 데모용으로 체험판 계정이 생성되었습니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3444388)

1. **Azure Active Directory에서 [!DNL Microsoft® Dynamics 365]에 대한 응용 프로그램을 등록**

   비디오의 단계에 따라 Azure Active Directory에 [!DNL Microsoft® Dynamics 365]에 대한 응용 프로그램을 등록합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/3444369/dynamics365integration-microsoftdynamics-apiaccess-azuread-appregistration)

   >[!NOTE]
   >
   >* 연결된 [!DNL Microsoft® Dynamics 365] 응용 프로그램을 만들려면 플랫폼으로 **Web**&#x200B;을(를) 선택하고 **형식으로**&#x200B;리디렉션 URI`https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/fdm.html`를 지정하십시오.
   >* 나중에 참조할 수 있도록 클라이언트 ID(애플리케이션 ID라고도 함)와 클라이언트 암호를 저장해야 합니다.

## Forms을 Microsoft® Dynamics 365에 연결

위의 사전 요구 사항을 구성했으면 적응형 Forms과 Microsoft® Dynamics 365의 통합을 진행할 수 있습니다. 양식 제출 시 Microsoft® Dynamics 365로 데이터를 전송하려면 아래 단계를 따르십시오.

[&#x200B;1. Microsoft Dynamics에 대한 클라우드 서비스 구성](#1-configure-cloud-service-configuration-for-microsoft-dynamics)

[&#x200B;2. 양식 데이터 모델(FDM) 만들기](#2-create-form-data-model-fdm)

### &#x200B;1. Microsoft Dynamics에 대한 클라우드 서비스 구성

>[!VIDEO](https://video.tv.adobe.com/v/3444370/cloudconfiguration-dataintegration-adobeexperiencemanager-aemforms-microsoftdynamics)

[!DNL Microsoft® Dynamics 365] 클라우드 서비스 구성을 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL 작성자 인스턴스의]**&#x200B;도구![&#x200B; &#x200B;](assets/hammer.png)hammer **[!UICONTROL >]**&#x200B;클라우드 서비스&#x200B;**[!UICONTROL >]**&#x200B;데이터 소스[!DNL AEM Forms]&#x200B;(으)로 이동합니다.

   ![클라우드 데이터 Source 선택](/help/forms/assets/dynamics-data-source.png)
1. 구성 컨테이너를 선택합니다. 선택한 구성 컨테이너에 구성을 저장합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![클라우드 구성 만들기](/help/forms/assets/dynamics-select-configuration.png)

   **데이터 Source 구성 만들기** 구성 마법사가 나타납니다.

   ![데이터 Source 구성 만들기 마법사](/help/forms/assets/dynamics-create-data-configuration.png)

1. **[!UICONTROL Title]**, **[!UICONTROL Name]**&#x200B;을(를) 지정하고 **[!UICONTROL 서비스 유형]**&#x200B;을(를) **OData 서비스**(으)로 선택하십시오.
1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다. **인증** 탭이 나타납니다.

   ![인증 탭](/help/forms/assets/dynamics-authentication-tab.png)

1. **[!UICONTROL 서비스 루트]** 필드에 대한 값을 지정하십시오.

   **Power Platform 관리 센터**&#x200B;에서 Dynamics 인스턴스로 이동하여 [개발자 리소스](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/view-download-developer-resources)으로 이동하여 **서비스 루트**&#x200B;의 값을 확인합니다. **웹 API 끝점**&#x200B;은(는) 적응형 Forms과 통합할 Dynamics 인스턴스의 **서비스 루트** 값을 나타냅니다. **서비스 루트** URL 형식은 `https://<tenant-name>.dynamics.com/api/data/v9.1/`입니다.

   ![서비스 루트 필드](/help/forms/assets/dynamics-service-root.png)

1. **[!UICONTROL 인증 유형]**&#x200B;을(를) **OAuth2.0**(으)로 선택하십시오.
1. 연결된 응용 프로그램에 대해 **클라이언트 ID**(응용 프로그램 ID라고도 함) 및 **클라이언트 암호**&#x200B;을(를) 지정하십시오.
Azure Active Directory 응용 프로그램에서 **클라이언트 ID** 및 **클라이언트 암호**&#x200B;를 검색할 수 있습니다.

   ![클라이언트 ID 및 클라이언트 암호](/help/forms/assets/dynamics-azure-app-resgistration.png)

1. **[!UICONTROL OAuth URL]**, **[!UICONTROL 새로 고침 토큰 URL]** 및 **[!UICONTROL 액세스 토큰 URL]** 필드에 다음을 지정하십시오.
Azure Active Directory 응용 프로그램의 **[!UICONTROL 끝점]** 섹션에서 **[!UICONTROL OAuth URL]**, **[!UICONTROL 새로 고침 토큰 URL]** 및 **액세스 토큰 URL**&#x200B;을(를) 검색할 수 있습니다.

   ![Azure 앱 끝점](/help/forms/assets/dynamics-azure-app-endpoints.png)

1. `openid`의 권한 부여 프로세스를 위해 **[!UICONTROL 권한 부여 범위]** 필드에 [!DNL Microsoft® Dynamics 365]을(를) 지정하십시오.
1. FDM(양식 데이터 모델)을 사용하여 **[!UICONTROL 을 구성하려면]**&#x200B;리소스[!DNL Microsoft® Dynamics 365] 필드에 동적 인스턴스 URL을 지정하십시오.
**Power Platform 관리 센터**&#x200B;에서 **환경 URL**&#x200B;을(를) 복사하거나 **서비스 루트** URL을 사용하여 Dynamics 인스턴스 URL을 파생할 수 있습니다. 리소스 URL의 형식은 `https://<tenant-name>.dynamics.com`입니다.

   ![고급 앱 리소스 필드](/help/forms/assets/dynamics-resource-field.png)

1. [!DNL Microsoft® Dynamics 365] 자격 증명으로 로그인하고 을(를) 수락하여 클라우드 서비스 구성이 [!DNL Microsoft® Dynamics 365] 서비스에 연결할 수 있도록 합니다. 연결이 성공하면 성공 메시지를 표시하는 [!DNL Microsoft® Dynamics 365] 클라우드 서비스 구성 페이지로 리디렉션됩니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 구성을 저장합니다.

### &#x200B;2. 양식 데이터 모델(FDM) 만들기

>[!VIDEO](https://video.tv.adobe.com/v/3444367/aemforms-adobeexperiencemanager-formdatamodel--dataintegration-digitalforms)

생성된 [!DNL Microsoft® Dynamics 365] 클라우드 구성을 사용하여 FDM(양식 데이터 모델)을 만들 수 있습니다. 양식 데이터 모델을 만들려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL 데이터 통합]**&#x200B;으로 이동합니다.
   ![양식 데이터 모델 만들기](/help/forms/assets/dynamics-create-fdm.png)

1. **[!UICONTROL 만들기]**&#x200B;를 클릭하고 **[!UICONTROL 양식 데이터 모델]**&#x200B;을(를) 선택합니다.
   ![양식 데이터 모델 선택](/help/forms/assets/dynamics-select-fdm.png)

   **양식 데이터 모델 만들기** 마법사가 나타납니다.
1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. **데이터 원본 선택** 탭에서 만든 클라우드 구성을 선택합니다.
   ![클라우드 구성 선택](/help/forms/assets/dynamics-select-cloud-config.png)

1. ![편집](assets/edit.png) 아이콘을 클릭하여 FDM(양식 데이터 모델)을 보고 구성합니다.

다음으로 [양식 데이터 모델(FDM)을 구성](/help/forms/work-with-form-data-model.md#configure-services)하여 다음과 같은 다양한 적응형 양식 사용 사례에 사용할 수 있습니다.

* [!DNL Microsoft Dynamics] 엔터티 및 서비스의 정보를 쿼리하여 적응형 양식 미리 채우기
* 적응형 양식 규칙을 사용하여 FDM(양식 데이터 모델)에 정의된 [!DNL Microsoft Dynamics] 서버 작업 호출
* 제출된 양식 데이터를 [!DNL Microsoft Dynamics] 엔터티에 쓰기
* 적응형 양식에 대한 양식 데이터 모델 제출 액션을 구성하여 [!DNL Microsoft Dynamics]에 데이터를 보낼 수 있습니다.

그런 다음 [적응형 양식](/help/forms/using-form-data-model.md)에서 **FDM(양식 데이터 모델)을 사용하여 제출** 옵션을 사용하여 양식의 데이터를 구성된 [!DNL Microsoft® Dynamics 365]&#x200B;(으)로 전송할 수 있습니다.


>[!MORELIKETHIS]
>
>* [AEM Forms에 대한 데이터 소스 구성](/help/forms/configure-data-sources.md)
>* [AEM Forms에 대한 Azure 저장소 구성](/help/forms/configure-azure-storage.md)
>  [AEM Sites 페이지에 Forms 포털 추가](/help/forms/configure-forms-portal.md)
