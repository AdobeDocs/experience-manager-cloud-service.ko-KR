---
title: Cloud Manager를 통해 클라우드 리소스 설정
description: Cloud Manager를 사용하여 고유한 클라우드 리소스를 설정 및 관리하는 방법을 알아봅니다.
role: Admin, User, Developer
exl-id: de3a33b7-b459-4e47-b232-a0f88e2ce22e
source-git-commit: 0db24518610fccf0d2ea5e0620a0c6a5f8009ea8
workflow-type: tm+mt
source-wordcount: '1369'
ht-degree: 1%

---

# Cloud Manager를 통해 클라우드 리소스 설정 {#setup-cloud-resources}

Cloud Manager를 사용하여 고유한 클라우드 리소스를 설정 및 관리하는 방법을 알아봅니다.

## 목표 {#objective}

이 문서는 클라우드 리소스를 만드는 방법과 누가 만들 수 있는지를 이해하는 데 도움이 됩니다. 이 섹션을 읽은 후에는 다음 사항을 이해해야 합니다.

* 시스템 관리자가 **비즈니스 소유자** 역할은 조직에서 처음으로 Cloud Manager에 로그인하여 액세스하는 역할이어야 합니다.
* 클라우드 프로그램 및 환경을 만드는 방법.

## 소개 {#introduction}

클라우드 리소스 추가는 **비즈니스 소유자** 제품 프로필 . 일반적으로 비즈니스 요구 사항을 이해하고 초기 Cloud Manager 설정을 완료하는 사용자입니다.

아래 섹션을 따라 를 작성하는 방법을 알아보십시오 [클라우드 서비스 프로그램](#create-cloud-service-program) 및 [환경.](#create-cloud-environments)

### 전제 조건 {#prerequisites}

* 시스템 관리자가 **비즈니스 소유자** 역할은 Cloud Manager에 로그인한 후에 **비즈니스 소유자** 이 문서에 설명된 단계 및 수행을 위해 Cloud Manager에 액세스하려고 하는 역할입니다.

   * 로 돌아갑니다. [Cloud Manager 제품 프로필에 팀 구성원 할당](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) 자세한 내용은 이 여정 문서를 참조하십시오.

* 당신은 어떻게 해야 하는지 이해해야 합니다 [cloud Manager로 이동하여 로그인합니다.](/help/onboarding/learn-concepts/cloud-manager-introduction.md)

* 잘 아셔야 합니다 [Cloud Manager 제품 프로필.](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md#cloud-manager-product-profiles)

* Cloud Manager의 개념을 이해해야 합니다 [프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) 및 [환경.](/help/implementing/cloud-manager/manage-environments.md)

## 시스템 관리자 및 비즈니스 소유자로서 Cloud Manager에 액세스 {#access-sysadmin-bo}

에 할당한 팀 멤버 전에 **비즈니스 소유자** 역할은 cloud manager에 액세스하여 클라우드 리소스 작성을 시작할 수 있으며, 시스템 관리자에게 **비즈니스 소유자** Cloud Manager에 역할 및 로그인.

1. 시스템 관리자는 **비즈니스 소유자** 할당된 역할.

   * 이 여정의 이전 단계로 돌아갑니다. [Cloud Manager 제품 프로필에 팀 구성원 할당,](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) 을 참조하십시오 **비즈니스 소유자** 이 작업을 아직 수행하지 않았다면 시스템 관리자에게 문의하십시오.

1. Cloud Manager에 로그인 위치: [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 일반 랜딩 페이지로 표시됩니다.

시스템 관리자로 **비즈니스 소유자** 역할을 사용하면, **비즈니스 소유자** 역할. 이 메시지나 메시지의 확인을 받지 않습니다. 단순히 서명만 하면 됩니다.

Cloud Manager를 **비즈니스 소유자** 역할, 다른 사용자와 **비즈니스 소유자** 역할이 올바른 역할을 할당하더라도 Cloud Manager에서 프로그램을 만들 수 없습니다.

## Cloud Manager로 이동 {#navigate-cloud-manager}

을 사용하는 사용자 **비즈니스 소유자** 시작하는 링크가 있는 환영 이메일을 역할 이 받게 됩니다. 이 환영 이메일을 사용하여 Cloud Manager로 이동하려면 아래 단계를 따르십시오.

1. 환영 이메일에서 클릭 **시작**아래 그림과 같이,
   ![이메일 예](/help/journey-onboarding/assets/get-started-email.png)

1. Cloud Manager의 **프로그램 및 제품** 페이지.

   >[!TIP]
   >
   >또한 다음 위치에서 Cloud Manager의 로그인 페이지로 직접 이동할 수도 있습니다 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). 나중에 참조할 수 있도록 이 페이지에 책갈피를 지정 하십시오.

1. Cloud Manager의 랜딩 페이지로 이동합니다. 자세한 내용은 [Cloud Manager 프로그램 보기](#viewing-programs) 섹션을 참조하십시오.

Cloud Manager의 **프로그램 및 제품** 다음 단계에 따라 Adobe Experience Cloud 홈페이지에서 페이지를 실행하십시오

1. 로 바로 이동 [Adobe Experience Cloud](https://experience.adobe.com) Adobe ID을 사용하여 로그인합니다.

1. Adobe Experience Cloud 홈페이지에서 Select **Experience Manager**.

   ![Experience Cloud 홈페이지](/help/journey-onboarding/assets/setup-resources2.png)

1. AEM 홈 페이지로 이동합니다. 여기에서 **Launch** on **Cloud Manager** 타일.

   ![AEM 홈 페이지](/help/journey-onboarding/assets/setup-resources3.png)

1. 로그인하면 Cloud Manager의 랜딩 페이지로 이동합니다. 자세한 내용은 [Cloud Manager 프로그램 보기](#viewing-programs) 섹션을 참조하십시오.

Cloud Manager를 통해 프로그램 및 제품에 액세스하는 방법은 사용자에 따라 다르며, Cloud Manager 사용 방식이나 프로그램 관리 방법에는 영향을 주지 않습니다.

>[!NOTE]
>
>에 할당된 역할에 따라 [!UICONTROL Cloud Manager] 응용 프로그램의 상태에서는 [!UICONTROL Cloud Manager] UI.

### 프로그램 보기 {#viewing-programs}

Cloud Manager에 성공적으로 액세스하면 표시되는 내용은 다음 섹션에 자세히 설명된 프로그램 상태에 따라 달라집니다.

#### 프로그램이 없는 경우 {#no-programs}

조직에 프로그램이 없는 경우 랜딩 페이지에서 첫 번째 프로그램을 생성하도록 안내합니다.

![프로그램 없음](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### 프로그램이 이미 있는 경우 {#programs-exist}

조직에 프로그램이 이미 존재하는 경우 랜딩 페이지에 기존 프로그램이 표시되고 추가 프로그램을 추가하는 버튼이 제공됩니다.

![프로그램이 있습니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### 프로그램이 존재하며 사용자가 시스템 관리자인 경우 {#programs-exist-sysadmin}

조직에 프로그램이 이미 있고 시스템 관리자라면 랜딩 페이지가 표시됩니다 **액세스 관리** 와 함께 사용할 단추 **프로그램 추가** 선택 사항입니다.

![시스템 관리자 보기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## 사용자 역할 확인 {#verify-user-roles}

Cloud Manager에 성공적으로 로그인하면 사용자에게 **비즈니스 소유자** 제품 프로필 .

1. 창 오른쪽 상단에서 프로필을 선택합니다.

   ![사용자 프로필](/help/journey-onboarding/assets/setup-resources5.png)

1. 선택 **사용자 역할** 사용자에게 할당된 역할을 표시합니다.

   ![사용자 역할](/help/journey-onboarding/assets/setup-resources6.png)

1. 사용자에게 **비즈니스 소유자** 역할.

   ![사용자 역할 목록](/help/journey-onboarding/assets/setup-resources7.png)

비즈니스 소유자로서 Cloud Manager에 성공적으로 로그인했습니다! 을 지정하지 않은 경우 **비즈니스 소유자** 역할, 시스템 관리자에게 문의하십시오.

## Cloud Service 프로그램 만들기 {#create-cloud-service-program}

적절한 액세스 권한을 보장했으므로 첫 번째 프로그램을 만들 수 있습니다.

1. 의 Cloud Manager 랜딩 페이지로 이동합니다 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 로그인하고

1. Cloud Manager 랜딩 페이지에서 **프로그램 추가** 프로그램 추가 마법사를 시작하려면 다음을 수행하십시오.

   ![랜딩 페이지](/help/journey-onboarding/assets/setup-resources4.png)

   >[!TIP]
   >
   >프로그램 추가 마법사를 사용하는 방법에 대한 단계별 지침은 문서를 참조하십시오 [프로덕션 프로그램 생성](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) 이걸 보고 [비디오](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) AEM as a Cloud Program을 만들고 프로그램을 만들기 전에 중요한 고려 사항에 대해 학습하는 방법을 알아봅니다.


1. 클라우드 프로그램을 성공적으로 만들면 Cloud Manager 랜딩 페이지에서 프로그램으로 이동하여 를 볼 수 있습니다. **개요** 프로그램의 페이지입니다.

   ![프로그램 개요](/help/journey-onboarding/assets/setup-resources8.png)

1. 개발자 제품 프로필에 할당된 구성원은 Cloud Manager에 로그인하고 Cloud Manager git 리포지토리를 관리할 수 있습니다.

   * 아직 그렇게 하지 않았다면 지금이 구성원을 **개발자** Cloud Manager 팀의 역할. 로 돌아갑니다. [Cloud Manager 제품 프로필에 팀 구성원 할당](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) 자세한 내용은 이 여정 문서를 참조하십시오.

이제 프로그램이 성공적으로 만들어졌고 개발자가 액세스할 수 있는 Cloud Manager git 저장소를 사용할 수 있습니다.

## 클라우드 환경 만들기 {#create-cloud-environments}

클라우드 프로그램을 성공적으로 만든 후 클라우드 환경을 만듭니다.

1. 의 Cloud Manager 랜딩 페이지로 이동합니다 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 을(를) 선택합니다. **추가** 환경 카드에서

   ![환경 추가 단추](/help/journey-onboarding/assets/setup-resources9.png)

1. 환경 추가 마법사가 실행되고 환경을 추가하는 과정을 안내합니다. 먼저 개발 환경을 추가하여 마법사를 잘 이해합니다.

   >[!TIP]
   >
   >문서를 참조하십시오 [환경 추가](/help/implementing/cloud-manager/manage-environments.md#adding-environments) 자세히 알아보기 또는 보기 [이 빠른 비디오 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) cloud Manager 환경 및 프로그램에 추가하는 방법에 대해 알아봅니다.

1. 에 지정된 구성원 **개발자** 제품 프로필은 Cloud Manager에 로그인하고 Cloud Manager git 리포지토리를 관리할 수 있습니다.

이제 프로그램이 성공적으로 만들어졌고 개발자가 액세스할 수 있는 Cloud Manager git을 사용할 수 있습니다.

## 다음은 무엇입니까? {#whats-next}

클라우드 리소스가 생성되어 팀이 액세스할 준비가 되었으므로 시스템 관리자는 Adobe Admin Console에서 AEM as a Cloud Service 제품 프로필에 팀 구성원을 할당하여 해당 리소스에 액세스해야 합니다.

다음에 문서를 검토하여 온보딩 여정을 계속해야 합니다 [AEM as a Cloud Service 제품 프로필에 팀 구성원 할당](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md) 여기서 팀 구성원에게 새 환경에 액세스하는 데 필요한 권한을 부여하는 방법을 알아봅니다.

## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* [프로그램 유형 및 프로그램 추가](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)
* [환경 유형 및 환경 추가](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)
* [Cloud Manager Git 관리](/help/implementing/cloud-manager/managing-code/accessing-repos.md)
* [Admin Console에서 AEM as a Cloud Service에 대한 액세스 구성](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html#adobe-ims-users)
