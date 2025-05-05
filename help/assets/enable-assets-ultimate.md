---
title: Assets Ultimate 활성화
description: 신규 및 기존 고객을 위해 Assets Ultimate을 활성화하는 방법을 알아봅니다.
feature: Asset Management
role: User, Admin
exl-id: 45cd8ccd-e5cf-42cd-aa7f-4ae59d0587f7
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 4%

---

# [!DNL Assets] as a Cloud Service Ultimate 사용 {#enable-assets-cloud-service-ultimate}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

![자산 Cloud Service Ultimate으로 업그레이드](/help/assets/assets/upgrade-assets-cs-ultimate-package-banner.png)

Assets as a Cloud Service Ultimate을 사용하면 에셋 관리 및 라이브러리 서비스, 보안 및 권한 관리, Creative 및 Experience Cloud 연결, UI 확장성, API 기반 자동화, Adobe 및 비 Adobe 애플리케이션과의 통합, 사용자 지정 코드 배포 등과 같은 다양한 주요 DAM 기능을 수행할 수 있습니다. 전체 목록은 [Assets as a Cloud Service Ultimate 개요](/help/assets/assets-ultimate-overview.md)를 참조하십시오.

## Assets Ultimate 활성화 {#enable-assets-ultimate}

새로운 Assets as a Cloud Service 고객은 먼저 Cloud Manager을 사용하여 새 프로그램을 만들어 Assets Ultimate을 활성화해야 합니다.

다음 단계를 실행합니다.

1. 시스템 관리자로 Cloud Manager에 로그온합니다. 로그인하는 동안 올바른 조직을 선택해야 합니다.

   >[!NOTE]
   >
   >새 프로그램을 추가할 적절한 Cloud Manager 제품 프로필에 추가되었는지 확인합니다. 자세한 내용은 [Cloud Manager의 역할 기반 권한](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)을 참조하세요.

1. [새 프로그램을 만들고](/help/journey-onboarding/create-program.md) [환경을 추가](/help/journey-onboarding//create-environments.md)합니다.

   새 프로그램을 만드는 동안 **[!UICONTROL 솔루션 및 추가 기능]** 탭에서 **[!UICONTROL Assets Ultimate]**&#x200B;을(를) 선택하십시오. **[!UICONTROL Assets Ultimate]**&#x200B;을(를) 확장하고 **[!UICONTROL Content Hub]**&#x200B;을(를) 선택하여 자산 배포에 [Content Hub](/help/assets/product-overview.md)을(를) 사용하도록 설정할 수도 있습니다.

   ![AEM Assets Ultimate](assets/aem-assets-ultimate-solutions.png)

1. 프로그램을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 클릭하십시오. 이제 Assets Ultimate이 Experience Manager Assets as a Cloud Service에 대해 활성화됩니다.

시스템 관리자는 Assets Ultimate에서 AEM 관리자 권한이 자동으로 부여되며 사용 가능한 제품 프로필을 관리하기 위해 Admin Console으로 이동하는 이메일을 수신합니다.

Admin Console에서 AEM as a Cloud Service 인스턴스는 다음 제품 프로필로 구성됩니다.

* AEM 관리자

* AEM 사용자

* [AEM Assets 공동 작업자 사용자](#onboard-collaborator-users)

* [AEM Assets 파워 유저](#onboard-power-users)

  ![AEM Assets 제품 프로필](assets/aem-assets-product-profiles.png)

Assets as a Cloud Service용 Content Hub을 활성화한 경우 Admin Console의 AEM Assets as a Cloud Service 내에서 접미사가 `delivery`인 새 인스턴스가 만들어집니다.

![Content Hub의 새 인스턴스](assets/new-instance-content-hub.png)

>[!NOTE]
>
>2024년 8월 14일 이전에 Content Hub을 프로비저닝한 경우 `contenthub`을(를) 접미사로 사용하여 새 인스턴스가 만들어집니다.

Content Hub의 인스턴스 이름에 `author` 또는 `publish`이(가) 없습니다.

`AEM Assets Limited Users` Content Hub 제품 프로필을 보려면 인스턴스 이름을 클릭하십시오.

![Content Hub 제품 프로필](assets/content-hub-product-profile.png)

이 제품 프로필에 사용자 또는 사용자 그룹을 추가하여 Content Hub에 대한 액세스 권한을 제공할 수 있습니다.

>[!NOTE]
>
>2024년 8월 14일 이전에 Content Hub을 프로비저닝한 경우 Content Hub 제품 프로필에 `delivery` 대신 `Limited Users` 뒤에 `contenthub`이(가) 언급되어 있습니다.

## 기존 고객을 위해 Assets Ultimate 활성화 {#enable-assets-ultimate-existing-customers}

기존 Assets as a Cloud Service 고객은 두 가지 간단한 단계를 실행하여 Assets Ultimate으로 업그레이드할 수 있습니다. Cloud Manager에서 Assets as a Cloud Service 프로그램으로 이동하고 Assets Ultimate 크레딧의 사용 가능 여부에 따라 프로그램 카드에서 업그레이드 상태를 볼 수 있습니다. Assets Ultimate으로 업그레이드할 수 있는 크레딧이 충분한 경우 다음 이미지에 표시된 대로 상태를 `Assets license upgrade required`(으)로 볼 수 있습니다.

![Assets Ultimate으로 AEM Assets 업그레이드](assets/aem-assets-upgrade-status-ultimate.png)

기존 고객이 Assets Ultimate에 대한 새 라이선스를 구입하는 경우 업그레이드 상태가 `Assets license upgrade available`(으)로 표시됩니다.

### 업그레이드 사전 요구 사항 {#prerequisites-assets-upgrade}

모든 환경을 최신 AEM as a Cloud Service 릴리스 버전 또는 최소 `2024.10.18175` 릴리스 버전으로 업그레이드해야 합니다. 최소 요구 사항을 충족하지 않는 경우 Adobe 담당자에게 문의하여 필요한 AEM 릴리스 버전으로 전환하십시오.

### Assets Ultimate로 업그레이드 {#upgrade-assets-ultimate}

다음 단계를 실행합니다.

1. AEM 릴리스 버전에 대한 최소 요구 사항으로 전환한 후 프로그램 이름을 클릭합니다. 업그레이드 카드는 다음 이미지에 표시된 대로 **[!UICONTROL 환경]** 섹션 바로 위에 표시됩니다.

   ![Assets Ultimate으로 AEM Assets 업그레이드](assets/aem-assets-upgrade-card.png)

1. **[!UICONTROL 제품 프로필 추가]**&#x200B;를 클릭합니다. Cloud Manager은 프로그램 또는 개별 환경에서 사용할 수 있는 모든 환경에 새 제품 프로필을 추가하는 옵션을 표시합니다.

   ![AEM Assets 업그레이드 옵션](assets/aem-assets-upgrade-options.png)

1. **[!UICONTROL 모든 환경]**&#x200B;을 클릭하여 프로그램의 모든 환경에 새 제품 프로필을 추가하거나 **[!UICONTROL 개별 환경]**&#x200B;을 클릭하여 선택한 환경에 새 제품 프로필을 추가합니다.

   **[!UICONTROL 개별 환경]**&#x200B;을 클릭하면 프로그램에서 사용할 수 있는 모든 환경 목록이 표시됩니다.

1. 환경에 해당하는 추가 옵션 아이콘을 클릭하고 **[!UICONTROL 제품 프로필 추가]**&#x200B;를 선택하여 선택한 환경에 새 제품 프로필을 추가합니다.

   ![AEM Assets 개별 환경 선택](assets/aem-assets-individual-environments.png)

   **[!UICONTROL 환경]** 섹션으로 이동하고 환경에 해당하는 추가 옵션 아이콘을 클릭한 다음 **[!UICONTROL 제품 프로필 추가]**&#x200B;를 선택하여 선택한 환경에 제품 프로필을 추가할 수도 있습니다.

   새 제품 프로필을 추가하는 동안 환경 상태가 `Adding Product Profiles`을(를) 표시하고 프로세스가 완료되면 `Running`을(를) 표시합니다.

   다음 단계를 실행하기 전에 프로그램에서 사용할 수 있는 모든 환경에 제품 프로필을 개별적으로 또는 모든 환경을 함께 추가해야 합니다.

1. **[!UICONTROL 업그레이드]**&#x200B;를 클릭합니다. **[!UICONTROL 업그레이드]** 옵션은 사용 가능한 모든 환경에 제품 프로필을 추가하는 경우에만 표시됩니다.

   ![업그레이드 프로세스의 마지막 단계](assets/aem-assets-upgrade-button.png)

   업그레이드 프로세스가 완료되었으며 Assets as a Cloud Service을 Assets Ultimate으로 성공적으로 업그레이드했습니다. 프로그램 상태가 `Assets Ultimate`을(를) 표시합니다.

   ![업그레이드 후 프로그램 상태](assets/program-status-post-upgrade.png)

이제 Admin Console의 AEM as a Cloud Service 인스턴스는 다음 제품 프로필로 구성됩니다.

* AEM 관리자

* AEM 사용자

* [AEM Assets 공동 작업자 사용자](#onboard-collaborator-users)

* [AEM Assets 파워 유저](#onboard-power-users)

![AEM Assets 제품 프로필](assets/aem-assets-product-profiles.png)

Content Hub을 활성화해야 하는 경우 Cloud Manager의 프로그램 이름에서 추가 옵션(...) 아이콘을 클릭하고 **[!UICONTROL 프로그램 편집]**&#x200B;을 선택합니다. **[!UICONTROL Assets Ultimate]**&#x200B;을(를) 확장하고 **[!UICONTROL Content Hub]**&#x200B;을(를) 클릭합니다. 이 단계에서는 Assets Ultimate용 Content Hub을 활성화합니다. Admin Console의 AEM Assets as a Cloud Service 내에 `delivery`을(를) 접미사로 사용하는 새 인스턴스가 생성되었습니다.

![Content Hub의 새 인스턴스](assets/new-instance-content-hub.png)

>[!NOTE]
>
>2024년 8월 14일 이전에 Content Hub을 프로비저닝한 경우 `contenthub`을(를) 접미사로 사용하여 새 인스턴스가 만들어집니다.

Content Hub의 인스턴스 이름에 `author` 또는 `publish`이(가) 없습니다.

`AEM Assets Limited Users` Content Hub 제품 프로필을 보려면 인스턴스 이름을 클릭하십시오.

![Content Hub 제품 프로필](assets/content-hub-product-profile.png)

이 제품 프로필에 사용자 또는 사용자 그룹을 추가하여 Content Hub에 대한 액세스 권한을 제공할 수 있습니다.

>[!NOTE]
>
>2024년 8월 14일 이전에 Content Hub을 프로비저닝한 경우 Content Hub 제품 프로필에 `delivery` 대신 `Limited Users` 뒤에 `contenthub`이(가) 언급되어 있습니다.

## AEM Assets Collaborator 사용자 온보드 {#onboard-collaborator-users}

AEM Assets Collaborator 사용자는 다른 Adobe 제품 및 Adobe이 아닌 애플리케이션에서 조직에서 사용할 수 있는 Assets의 통합을 통해 Experience Manager의 자산으로 작업하고, 전문적으로 디자인된 템플릿, 브랜드 키트, Adobe Stock 자산 등을 활용하여 내장 Adobe Express 및 Firefly을 사용하여 자산을 만들고 편집하고, AEM Assets Content Hub 포털을 사용하여 조직에서 승인된 자산에 액세스하고 활용할 수 있습니다.

Collaborator 사용자를 온보딩하려면 다음을 수행합니다.

1. Admin Console의 제품 목록에서 Experience Manager Assets 제품 이름을 클릭하여 AEM as a Cloud Service 제품 프로필에 액세스합니다.

1. AEM as a Cloud Service에 대한 프로덕션 작성자 인스턴스 를 클릭합니다.
   AEM as a Cloud Service의 ![제품 프로필](assets/aem-cloud-service-instances.png)

1. Collaborators 사용자 제품 프로필을 클릭하고 **[!UICONTROL 사용자 추가]**&#x200B;를 클릭하여 사용자 또는 사용자 그룹을 제품 프로필에 추가합니다.
   ![사용자 제품 프로필](assets/aem-assets-collaborator-user-permissions.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 변경 내용을 저장합니다.

다음 이미지에 표시된 대로 Collaborator 사용자에게 할당된 서비스에 액세스하고 이를 볼 수도 있습니다.

Collaborator 사용자를 위한 ![서비스](assets/aem-assets-collaborator-users.png)

기본적으로 `Adobe Express` 및 `AEM Assets Collaborator Users` 서비스를 사용할 수 있습니다.

>[!NOTE]
>
>필요에 따라 토글을 끄거나 켜서 사용 가능한 서비스를 활성화 또는 비활성화할 수 있지만, Adobe에서는 제품 프로필에 대해 활성화된 기본 서비스를 사용하는 것이 좋습니다.


## AEM Assets Power 사용자 온보드 {#onboard-power-users}

AEM Assets 파워 유저는 자산, 권한, 메타데이터 관리, 디지털 자산에 대한 전반적인 거버넌스 및 자동화를 포함한 모든 AEM Assets 기능에 액세스하고, 다른 Adobe 및 Adobe 이외의 애플리케이션에서 조직에서 사용할 수 있는 Assets의 통합을 통해 Experience Manager의 자산으로 작업하고, 내장된 Adobe Express 및 Firefly을 사용하여 전문적으로 디자인된 템플릿, 브랜드 키트, Adobe Stock 자산 등을 활용하여 자산을 만들고 편집하고, AEM Assets Content Hub 포털을 사용하여 조직에서 승인된 자산에 액세스하고 활용할 수 있습니다.

Power 사용자를 온보딩하려면:

1. Admin Console의 제품 목록에서 Experience Manager Assets 제품 이름을 클릭하여 AEM as a Cloud Service 제품 프로필에 액세스합니다.

1. AEM as a Cloud Service에 대한 프로덕션 작성자 인스턴스 를 클릭합니다.
   AEM as a Cloud Service의 ![제품 프로필](assets/aem-cloud-service-instances.png)

1. 고급 사용자 제품 프로필을 클릭하고 **[!UICONTROL 사용자 추가]**&#x200B;를 클릭하여 사용자 또는 사용자 그룹을 제품 프로필에 추가합니다.
   ![사용자 제품 프로필](assets/aem-assets-power-user-permissions.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 변경 내용을 저장합니다.

다음 이미지에 표시된 대로 고급 사용자에게 할당된 서비스에 액세스하고 서비스를 볼 수도 있습니다.

고급 사용자를 위한 ![서비스](assets/aem-assets-power-users.png)

기본적으로 `Adobe Express` 및 `AEM Assets Power Users` 서비스를 사용할 수 있습니다.

>[!NOTE]
>
>필요에 따라 토글을 끄거나 켜서 사용 가능한 서비스를 활성화 또는 비활성화할 수 있지만, Adobe에서는 제품 프로필에 대해 활성화된 기본 서비스를 사용하는 것이 좋습니다.
