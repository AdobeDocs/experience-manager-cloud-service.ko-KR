---
title: Cloud Manager 액세스
description: 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
feature: Onboarding
source-git-commit: 0db48ef4c15b6ca530b2626f7078c7172c872fff
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 63%

---

# Cloud Manager 액세스 {#cloud-resources}

이 [온보딩 여정](overview.md) 부분에서는 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 배웁니다.

## 목표 {#objective}

이 온보딩 여정의 이전 문서인 [Cloud Manager 제품 프로필에 팀원 할당](assign-profiles-cloud-manager.md)에서 AEMaaCS 팀에 적절한 역할을 부여했습니다 이제 팀에서 사용하려는 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다.

이 여정의 이전 단계를 완료했으므로 팀에서 Cloud Manager에 액세스할 수 있습니다. Cloud Manager은 프로그램 및 환경과 같은 프로젝트 리소스를 만들고 관리하는 데 사용됩니다.

이 문서를 읽은 후에는 다음과 같은 사항을 이해할 수 있습니다.

* **비즈니스 소유자** 역할에 할당된 시스템 관리자가 조직에서 가장 먼저 Cloud Manager에 로그인하고 액세스해야 합니다.
* Cloud Manager에 로그인하는 방법을 이해합니다.

## Cloud Manager {#cloud-manager}

Cloud Manager는 AEM as a Cloud Service의 필수 구성 요소이며 팀의 단일 진입점 역할을 합니다. Cloud Manager는 철저한 테스트와 최고의 코드 품질을 보장하여 탁월한 경험을 제공할 수 있도록 기업 개발 설정 및 특수 목적으로 구축된 CI/CD 파이프라인을 통해 기업 개발 설정을 통해 고객을 지원합니다. Cloud Manager은 클라우드 리소스 및 환경을 만드는 기능을 포함하여 셀프서비스 방식으로 시작하는 데 필요한 모든 기능을 제공합니다.

일반적으로 **비즈니스 소유자** 제품 프로필에 할당된 팀원은 프로그램 및 환경과 같은 클라우드 리소스를 추가할 책임이 있습니다. 이 개인은 비즈니스 요구 사항을 이해하며 초기 Cloud Manager 설정을 완료합니다.

이 온보딩 여정의 목적을 위해 시스템 관리자는 이미 자신을 **비즈니스 소유자** 제품 프로필에 할당하고 클라우드 리소스를 설정할 수 있습니다. 비즈니스 소유자는 실제 프로젝트 요구 사항에 따라 시스템 관리자와 동일하거나 동일하지 않을 수 있습니다.

## 시스템 관리자 및 비즈니스 소유자로 Cloud Manager에 액세스 {#access-sysadmin-bo}

**비즈니스 소유자** 역할에 할당한 팀원이 Cloud Manager에 액세스하여 클라우드 리소스 생성을 시작하려면 먼저 시스템 관리자에게 **비즈니스 소유자** 역할을 할당해야 합니다. 이 온보딩 여정의 이전 단계에서와 같이 Cloud Manager에 로그인해야 합니다.

1. 시스템 관리자로서 **비즈니스 소유자** 역할이 할당되었는지 확인합니다.

   시스템 관리자에게 [비즈니스 소유자](assign-profiles-cloud-manager.md) 역할을 할당하는 방법에 대한 자세한 내용을 보려면 이전 단계인 **Cloud Manager 제품 프로필에 팀원 할당**(으)로 돌아가십시오.

1. [experience.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
1. 빠른 액세스 그룹화에서 **Experience Manager**&#x200B;을(를) 클릭합니다.
1. 왼쪽 패널에서 **Cloud Manager**&#x200B;을(를) 클릭합니다.

   콘솔의 ![Cloud Manager](/help/journey-onboarding/assets/consol-cloud-manager.png)

**비즈니스 소유자** 역할이 있는 시스템 관리자로 로그인하면 **비즈니스 소유자** 역할이 있는 다른 사용자가 사용할 수 있도록 Cloud Manager을 사용합니다. 이 경우 어떠한 메시지도 나타나지 않습니다. 로그인하기만 하면 됩니다.

**비즈니스 소유자** 역할을 가진 시스템 관리자로 Cloud Manager에 로그인할 때까지 **비즈니스 소유자** 역할을 가진 다른 사용자는 Cloud Manager에서 프로그램을 만들 수 없습니다. 이 규칙은 올바른 역할이 할당되더라도 true입니다.

## Cloud Manager로 이동 {#navigate-cloud-manager}

**비즈니스 소유자** 역할이 있는 사용자는 시작하기 위한 링크가 포함된 환영 이메일을 받습니다. 이 환영 이메일을 사용하여 Cloud Manager로 이동하려면 아래 단계를 따르십시오.

1. 환영 이메일에서 아래 그림과 같이 **시작하기**&#x200B;를 클릭합니다.
   ![이메일 예](/help/journey-onboarding/assets/get-started-email.png)

1. Cloud Manager의 **프로그램 및 제품** 페이지로 이동합니다.

   >[!TIP]
   >
   >`[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)`에서 Cloud Manager의 로그인 페이지로 직접 이동할 수도 있습니다. 나중에 참조할 수 있도록 이 페이지에 책갈피를 표시합니다.

1. Cloud Manager의 랜딩 페이지로 이동합니다.

<!-- OLD
Alternatively, you can navigate to Cloud Manager's **Programs and Products** page from the Adobe Experience Cloud home page using these steps.

1. Navigate directly to [Adobe Experience Cloud](https://experience.adobe.com) and login using your Adobe ID.

1. From the Adobe Experience Cloud home page, select **Experience Manager** to open the AEM home page.

   ![Experience Cloud homepage](/help/journey-onboarding/assets/setup-resources2.png)

1. On the **Cloud Manager** tile, select **Launch**.

   ![AEM home page](/help/journey-onboarding/assets/setup-resources3.png)

1. After successfully logging on, you are directed to the Cloud Manager landing page. See [Viewing Cloud Manager's Programs](#viewing-programs) for more details.

How you access your programs and products via Cloud Manager is up to you and has no effect on how you use Cloud Manager or how you manage your programs.

>[!NOTE]
>
>Depending on the roles assigned in Cloud Manager and the state of the application, you see different screens while using the Cloud Manager user interface. -->

## 프로그램 보기 {#viewing-programs}

Cloud Manager에 성공적으로 액세스하면 다음 섹션에 설명된 대로 프로그램 상태에 따라 표시되는 내용이 달라집니다.

### 프로그램이 없는 경우 {#no-programs}

조직에 프로그램이 없는 경우 랜딩 페이지에서 첫 번째 프로그램을 만들도록 지시합니다.

![프로그램 없음](/help/journey-onboarding/assets/cloud-manager-programs-do-not-exist.png)

### 프로그램이 이미 있는 경우 {#programs-exist}

조직에 프로그램이 있는 경우 랜딩 페이지에 기존 프로그램이 표시되고 다른 프로그램을 추가할 수 있는 버튼도 제공됩니다.

![프로그램 있음](/help/journey-onboarding/assets/cloud-manager-programs-exist.png)

### 프로그램이 존재하고 시스템 관리자인 경우 {#programs-exist-sysadmin}

조직에 프로그램이 있고 시스템 관리자인 경우 랜딩 페이지에 **프로그램 추가** 옵션과 함께 **액세스 관리** 단추가 표시됩니다.

![시스템 관리자 보기](/help/journey-onboarding/assets/cloud-manager-programs-as-sysadmin.png)

## 사용자 역할 확인 {#verify-user-roles}

Cloud Manager에 성공적으로 로그인하면 **비즈니스 소유자** 제품 프로필이 할당되었는지 확인할 수 있습니다.

1. 페이지의 오른쪽 상단 모서리에서 **계정** 아이콘을 클릭합니다.

1. **사용자 역할**&#x200B;을 클릭합니다.

   ![사용자 역할](/help/journey-onboarding/assets/cloud-manager-user-roles.png)

1. **사용자 역할** 대화 상자에서 사용자에게 **비즈니스 소유자** 역할이 있는지 확인합니다.

   ![사용자 역할 목록](/help/journey-onboarding/assets/cloud-manager-user-roles-business-owner.png)

Cloud Manager에 비즈니스 소유자로 로그인했습니다. **비즈니스 소유자** 역할이 할당되지 않은 경우 시스템 관리자에게 문의하십시오.

## 다음 단계 {#whats-next}

이제 시스템 관리자로 Cloud Manager에 액세스할 수 있으므로 첫 번째 프로그램을 만들 준비가 된 것입니다.

다음은 [프로그램 만들기](create-program.md) 문서를 검토하여 온보딩 여정을 계속 진행합니다.

## 추가 리소스 {#additional-resources}

온보딩 여정의 콘텐츠를 능가하려는 경우 다음은 추가적인 옵션 리소스입니다.

* [Cloud Manager 소개](/help/onboarding/cloud-manager-introduction.md) -
Cloud Manager, Cloud Manager 프로그램 및 환경에 대해 알아봅니다.
* [AEM as a Cloud Service 팀 및 제품 프로필](/help/onboarding/aem-cs-team-product-profiles.md) - AEM as a Cloud Service 팀 및 제품 프로필로 라이선스가 부여된 Adobe 솔루션에 대한 액세스 권한을 부여하고 제한하는 방법에 대해 알아봅니다.
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->
