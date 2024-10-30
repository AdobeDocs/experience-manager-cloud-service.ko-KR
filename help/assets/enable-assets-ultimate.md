---
title: Enable Assets Ultimate
description: Learn how to enable Assets Ultimate for new and existing customers.
feature: Asset Management
role: User, Admin
source-git-commit: 16ce83409044ad54140754112eb4d35b97883b44
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 2%

---

# [!DNL Assets] {#enable-assets-cloud-service-ultimate}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능 포함 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![](/help/assets/assets/upgrade-assets-cs-ultimate-package-banner.png)

Assets as a Cloud Service Ultimate enables you to perform various key DAM capabilities, such as, asset management and library services, security and rights management, Creative and Experience Cloud connections, UI extensibility, API-driven automation, integrations with Adobe and non-Adobe applications, custom code deployment and many more. [](/help/assets/assets-ultimate-overview.md)

## Enable Assets Ultimate {#enable-assets-ultimate}

New Assets as a Cloud Service customers must first enable Assets Ultimate by creating a new program using Cloud Manager.

다음 단계를 실행합니다.

1. 시스템 관리자로 Cloud Manager에 로그온합니다. Ensure that you select the right organization while logging in.

   >[!NOTE]
   >
   >Ensure that you are added to the appropriate Cloud Manager product profile to add a new program. [](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)

1. [](/help/journey-onboarding/create-program.md)[](/help/journey-onboarding//create-environments.md)

   ******** ********[](/help/assets/product-overview.md)

   ![](assets/aem-assets-ultimate-solutions.png)

1. 프로그램을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 클릭하십시오. Assets Ultimate는 이제 Experience Manager Assetsas a Cloud Service 에 대해 활성화됩니다.

시스템 관리자는 Assets Ultimate에서 AEM 관리자 권한이 자동으로 부여되며, 사용 가능한 제품 프로필을 관리하기 위해 Admin Console으로 이동할 수 있는 이메일을 받게 됩니다.

Admin Console의 AEM as a Cloud Service 인스턴스는 다음 제품 프로필로 구성됩니다.

* AEM 관리자

* AEM 사용자

* [AEM Assets Collaborator 사용자](#onboard-collaborator-users)

* [AEM Assets 고급 사용자](#onboard-power-users)

  ![AEM Assets 제품 프로필](assets/aem-assets-product-profiles.png)

Assets용 as a Cloud Service이 있는 경우 AEM Assetsas a Cloud Service 에서 접미사 `delivery`을(를) 사용하는 새로운 Content Hub Admin Console이 생성됩니다.

![Content Hub의 새 인스턴스](assets/new-instance-content-hub.png)

>[!NOTE]
>
>2024년 8월 14일 이전에 Content Hub을 프로비저닝한 경우 `contenthub`을(를) 접미사로 사용하여 새 인스턴스가 만들어집니다.

Content Hub의 인스턴스 이름에 `author` 또는 `publish`이(가) 없습니다.

`AEM Assets Limited Users` Content Hub 제품 프로필을 보려면 인스턴스 이름을 클릭하십시오.

![](assets/content-hub-product-profile.png)

You can start adding users or user groups to this product profile to provide them access to Content Hub.

>[!NOTE]
>
>`contenthub``Limited Users``delivery`

## 기존 고객을 위해 Assets Ultimate 활성화 {#enable-assets-ultimate-existing-customers}

기존 Assets as a Cloud Service 고객은 두 가지 간단한 단계를 실행하여 Assets Ultimate로 업그레이드할 수 있습니다. Cloud Manager의 Assets Assets 프로그램으로 이동하고 as a Cloud Service Ultimate 크레딧의 가용성에 따라 프로그램 카드의 업그레이드 상태를 볼 수 있습니다. Assets Ultimate로 업그레이드할 수 있는 크레딧이 충분한 경우 다음 이미지에 표시된 대로 상태를 `Assets license upgrade required`(으)로 볼 수 있습니다.

![Assets Ultimate로 AEM Assets 업그레이드](assets/aem-assets-upgrade-status-ultimate.png)

기존 고객이 Assets Ultimate에 대한 새 라이선스를 구입하는 경우 업그레이드 상태는 `Assets license upgrade available`(으)로 표시됩니다.

### 업그레이드 사전 요구 사항 {#prerequisites-assets-upgrade}

`2024.10.18175` If you do not meet the minimum requirements, contact your Adobe representative to switch to the required AEM release version.

### Assets Ultimate로 업그레이드 {#upgrade-assets-ultimate}

다음 단계를 실행합니다.

1. After switching to the minimum requirements for the AEM release version, click the program name. ****

   ![](assets/aem-assets-upgrade-card.png)

1. **[!UICONTROL 제품 프로필 추가]**&#x200B;를 클릭합니다. Cloud Manager은 프로그램 또는 개별 환경에서 사용할 수 있는 모든 환경에 새 제품 프로필을 추가하는 옵션을 표시합니다.

   ![AEM Assets 업그레이드 옵션](assets/aem-assets-upgrade-options.png)

1. **[!UICONTROL 모든 환경]**&#x200B;을 클릭하여 프로그램의 모든 환경에 새 제품 프로필을 추가하거나 **[!UICONTROL 개별 환경]**&#x200B;을 클릭하여 선택한 환경에 새 제품 프로필을 추가합니다.

   ****

1. 환경에 해당하는 추가 옵션 아이콘을 클릭하고 **[!UICONTROL 제품 프로필 추가]**&#x200B;를 선택하여 선택한 환경에 새 제품 프로필을 추가합니다.

   ![AEM Assets 개별 환경 선택](assets/aem-assets-individual-environments.png)

   **[!UICONTROL 환경]** 섹션으로 이동하고 환경에 해당하는 추가 옵션 아이콘을 클릭한 다음 **[!UICONTROL 제품 프로필 추가]**&#x200B;를 선택하여 선택한 환경에 제품 프로필을 추가할 수도 있습니다.

   새 제품 프로필을 추가하는 동안 환경 상태가 `Adding Product Profiles`을(를) 표시하고 프로세스가 완료되면 `Running`을(를) 표시합니다.

   다음 단계를 실행하기 전에 프로그램에서 사용할 수 있는 모든 환경에 제품 프로필을 개별적으로 또는 모든 환경을 함께 추가해야 합니다.

1. **[!UICONTROL 업그레이드]**&#x200B;를 클릭합니다. ****

   ![](assets/aem-assets-upgrade-button.png)

   The upgrade process is complete and you have successfully upgraded your Assets as a Cloud Service to Assets Ultimate. `Assets Ultimate`

   ![](assets/program-status-post-upgrade.png)

Your AEM as a Cloud Service instance on Admin Console now comprises the following product profiles:

* AEM Administrators

* AEM 사용자

* [AEM Assets Collaborator Users](#onboard-collaborator-users)

* [AEM Assets Power Users](#onboard-power-users)

![](assets/aem-assets-product-profiles.png)

**** ******** This step enables the Content Hub for Assets Ultimate. `delivery`

![](assets/new-instance-content-hub.png)

>[!NOTE]
>
>`contenthub`

`author``publish`

`AEM Assets Limited Users` Content Hub 제품 프로필을 보려면 인스턴스 이름을 클릭하십시오.

![](assets/content-hub-product-profile.png)

You can start adding users or user groups to this product profile to provide them access to Content Hub.

>[!NOTE]
>
>`contenthub``Limited Users``delivery`

## Onboard AEM Assets Collaborator users {#onboard-collaborator-users}

AEM Assets Collaborator users can work with assets from Experience manager via integrations of Assets available to your organization in other Adobe products and non-Adobe applications, create and edit assets using built-in Adobe Express and Firefly leveraging professionally designed templates, brand kits, Adobe Stock assets, and so on, and access and leverage approved assets from your organization using AEM Assets Content Hub portal.

Collaborator 사용자를 온보딩하려면 다음을 수행합니다.

1. Admin Console의 제품 목록에서 Experience Manager Assets 제품 이름을 클릭하여 AEM as a Cloud Service 제품 프로필에 액세스합니다.

1. AEM as a Cloud Service에 대한 프로덕션 작성자 인스턴스 를 클릭합니다.
   AEM as a Cloud Service의 ![제품 프로필](assets/aem-cloud-service-instances.png)

1. Collaborators 사용자 제품 프로필을 클릭하고 **[!UICONTROL 사용자 추가]**를 클릭하여 사용자 또는 사용자 그룹을 제품 프로필에 추가합니다.
   ![사용자 제품 프로필](assets/aem-assets-collaborator-user-permissions.png)

1. 변경 내용을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

다음 이미지에 표시된 대로 Collaborator 사용자에게 할당된 서비스에 액세스하고 이를 볼 수도 있습니다.

Collaborator 사용자를 위한 ![서비스](assets/aem-assets-collaborator-users.png)

기본적으로 `Adobe Express` 및 `AEM Assets Collaborator Users` 서비스를 사용할 수 있습니다.

>[!NOTE]
>
>Adobe 필요에 따라 토글을 끄고 켜서 사용 가능한 서비스를 활성화 또는 비활성화할 수 있지만, 제품 프로필에 대해 활성화된 기본 서비스를 사용하는 것이 좋습니다.


## AEM Assets Power 사용자 온보드 {#onboard-power-users}

AEM Assets Power 사용자는 자산, 권한, 메타데이터, 디지털 자산에 대한 전반적인 거버넌스 및 자동화 관리를 포함한 모든 AEM Assets 기능에 액세스하고, 다른 Adobe 및 Adobe이 아닌 애플리케이션에서 조직에서 사용할 수 있는 Assets의 통합을 통해 Experience Manager의 자산과 작업하고, 전문 AEM Assets이 디자인된 템플릿, 브랜드 키트, Adobe Stock 자산 등을 활용하여 내장 Adobe Express 및 Firefly을 사용하여 자산을 만들고 편집하고, Content Hub 포털을 사용하여 조직에서 승인된 자산에 액세스하고 활용할 수 있습니다.

To onboard Power users:

1. Access Experience Manager Assets product profiles by clicking the AEM as a Cloud Service product name in the list of products on Admin Console.

1. Click the production author instance for AEM as a Cloud Service:
   ![](assets/aem-cloud-service-instances.png)

1. 고급 사용자 제품 프로필을 클릭하고 **[!UICONTROL 사용자 추가]**를 클릭하여 사용자 또는 사용자 그룹을 제품 프로필에 추가합니다.
   ![사용자 제품 프로필](assets/aem-assets-power-user-permissions.png)

1. 변경 내용을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

다음 이미지에 표시된 대로 고급 사용자에게 할당된 서비스에 액세스하고 서비스를 볼 수도 있습니다.

고급 사용자를 위한 ![서비스](assets/aem-assets-power-users.png)

기본적으로 `Adobe Express` 및 `AEM Assets Power Users` 서비스를 사용할 수 있습니다.

>[!NOTE]
>
>Adobe 필요에 따라 토글을 끄고 켜서 사용 가능한 서비스를 활성화 또는 비활성화할 수 있지만, 제품 프로필에 대해 활성화된 기본 서비스를 사용하는 것이 좋습니다.
