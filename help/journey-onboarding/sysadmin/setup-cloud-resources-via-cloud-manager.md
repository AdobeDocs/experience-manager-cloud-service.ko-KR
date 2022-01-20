---
title: Cloud Manager를 통해 클라우드 리소스 설정
description: Cloud Manager를 통해 클라우드 리소스를 설정하는 방법을 배우려면 이 페이지를 따르십시오
role: Admin, User, Developer
exl-id: de3a33b7-b459-4e47-b232-a0f88e2ce22e
source-git-commit: 7fe39bbc8d5e965af7f339b2a524420c76360552
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 1%

---

# Cloud Manager를 통해 클라우드 리소스 설정 {#setup-cloud-resources}

비즈니스 소유자 역할에 할당된 시스템 관리자는 Cloud Manager에 액세스하여 로그인해야 합니다. 뒤이어 비즈니스 소유자 제품 프로필에 할당된 팀 구성원이 Cloud Manager에 로그인하여 클라우드 프로그램 및 환경을 만들어야 전문가 팀을 시작할 수 있습니다.

## 목표 {#objective}

이 문서는 클라우드 리소스를 만드는 방법과 이 작업을 수행할 수 있는 사용자를 이해하는 데 도움이 됩니다.

이 섹션을 읽은 후에는 다음 사항을 이해해야 합니다.

* 비즈니스 소유자 역할에 할당된 시스템 관리자가 먼저 Cloud Manager에 액세스하여 로그인해야 합니다.
* 클라우드 프로그램 및 환경을 만드는 방법.

## 소개 {#introduction}

클라우드 리소스 추가는 Cloud Manager 비즈니스 소유자 제품 프로필에 할당된 팀 구성원이 Cloud Manager를 통해 수행됩니다. 일반적으로 비즈니스 요구 사항을 이해하고 초기 Cloud Manager 설정을 완료하는 사용자입니다.

아래 섹션을 따라 를 작성하는 방법을 알아보십시오 [클라우드 서비스 프로그램](#create-cloud-service-program) 및 [환경.](#create-cloud-environments)

### 전제 조건 {#prerequisites}

* 비즈니스 소유자 역할에 할당된 시스템 관리자는 Cloud Manager에 액세스하여 로그인해야 합니다.

* 방법 이해 [cloud Manager로 이동하여 로그인합니다.](/help/onboarding/learn-concepts/cloud-manager-introduction.md)

* 익숙해지십시오 [Cloud Manager 제품 프로필.](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md#cloud-manager-product-profiles)

* Cloud Manager의 개념 이해 [프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/understand-program-types.md) 및 [환경.](/help/implementing/cloud-manager/manage-environments.md)

## Cloud Manager로 이동 {#navigate-cloud-manager}

비즈니스 소유자 사용자는 시작할 링크가 포함된 환영 이메일을 수신하거나, 링크를 찾을 수 없는 경우 액세스합니다 [Cloud Manager](https://my.cloudmanager.adobe.com/) Adobe ID을 사용하여 로그인함으로써 직접 액세스할 수 있습니다.

Cloud Manager로 이동하려면 아래 단계를 따르십시오.

1. 환영 이메일에서 클릭 **시작**아래 그림과 같이,
   ![](/help/journey-onboarding/assets/get-started-email.png)

1. Cloud Manager의 **프로그램 및 제품** 페이지.

   >[!IMPORTANT]
   >
   >또는 다음 위치에서 Cloud Manager의 로그인 페이지로 직접 이동할 수도 있습니다 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). 나중에 참조할 수 있도록 이 페이지에 책갈피를 지정하여 Cloud Manager의 랜딩 페이지로 직접 이동할 수 있습니다.

1. Cloud Manager의 랜딩 페이지로 이동합니다. 자세한 내용은 [Cloud Manager 프로그램 보기](#viewing-programs) 섹션을 참조하십시오.

또한 Cloud Manager의 **프로그램 및 제품** Adobe Experience Cloud 홈페이지에서 페이지를 엽니다. 아래 단계를 따르십시오.

1. 로 바로 이동 [Adobe Experience Cloud](https://experience.adobe.com) Adobe ID을 사용하여 로그인합니다.

1. Adobe Experience Cloud 홈페이지에서 Select **Experience Manager**.

   ![](/help/journey-onboarding/assets/setup-resources2.png)

1. AEM 홈 페이지로 이동합니다. 여기에서 시작 **Cloud Manager** .

   ![](/help/journey-onboarding/assets/setup-resources3.png)

1. 로그인하면 Cloud Manager의 랜딩 페이지로 이동합니다. 자세한 내용은 [Cloud Manager 프로그램 보기](#viewing-programs) 섹션을 참조하십시오.

   >[!NOTE]
   >
   >에 할당된 역할에 따라 [!UICONTROL Cloud Manager] 응용 프로그램의 상태에서는 [!UICONTROL Cloud Manager] UI.

### Cloud Manager의 랜딩 페이지에서 프로그램 보기 {#viewing-programs}

로그인하면 Cloud Manager의 랜딩 페이지로 이동합니다. 아래에 설명된 세 가지 옵션 중 하나가 표시됩니다.

#### Cloud Manager에 프로그램 없음 {#no-programs}

조직에 프로그램이 없는 경우 랜딩 페이지에서 아래 그림과 같이 첫 번째 프로그램을 만들라고 안내합니다.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Cloud Manager에 프로그램이 이미 있는 경우 {#programs-exist}

조직에 프로그램이 이미 존재하는 경우 랜딩 페이지에서 아래 그림과 같이 다른 프로그램을 추가하고 기존 프로그램도 모두 표시합니다.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### 프로그램이 있고 사용자가 시스템 관리자인 경우 {#programs-exist-sysadmin}

조직에 프로그램이 이미 있고 사용자가 시스템 관리자인 경우 랜딩 페이지가 표시됩니다 **액세스 관리** 와 함께 사용할 단추 **프로그램 추가** 옵션을 선택합니다.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## 사용자 역할 확인 {#verify-user-roles}

Cloud Manager에 성공적으로 로그인했으면 아래 절차에 따라 비즈니스 소유자 제품 프로필이 할당되었는지 확인하십시오.

1. 아래 표시된 것처럼 오른쪽 상단에서 프로필을 선택합니다.

   ![](/help/journey-onboarding/assets/setup-resources5.png)

1. 선택 **사용자 역할** 비즈니스 소유자에게 지정되었는지 확인합니다.

   ![](/help/journey-onboarding/assets/setup-resources6.png)

1. 이를 통해 비즈니스 소유자로서의 사용자 역할이 확인됩니다.

   ![](/help/journey-onboarding/assets/setup-resources7.png)

   잘했어요! 비즈니스 소유자로서 Cloud Manager에 성공적으로 로그인했습니다!

## Cloud Service 프로그램 만들기 {#create-cloud-service-program}

Cloud Manager에서 클라우드 서비스 프로그램을 만들려면 아래 절차를 따르십시오.

1. 아래 표시된 대로 Cloud Manager 랜딩 페이지로 이동합니다.

   >[!NOTE]
   >
   >이 단계를 성공적으로 완료하려면 Cloud Manager 비즈니스 소유자 제품 프로필에 할당된 팀 구성원이어야 합니다.

   여기서 을(를) 클릭합니다. **프로그램 추가** 프로그램 추가 마법사를 시작하려면 다음을 수행하십시오.

   ![](/help/journey-onboarding/assets/setup-resources4.png)

   >[!TIP]
   >
   >보기 [비디오](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) AEM as a Cloud Program을 만들고 프로그램을 만들기 전에 중요한 고려 사항에 대해 학습하는 방법을 알아봅니다.

   >[!TIP]
   >
   >프로그램 추가 마법사를 사용하는 방법에 대한 단계별 지침을 보려면 [여기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-program.md).

1. 클라우드 프로그램을 성공적으로 만들면 프로그램으로 이동하여 을 볼 수 있습니다. **개요** 아래 표시된 대로 프로그램의 페이지입니다.

   ![](/help/journey-onboarding/assets/setup-resources8.png)

   >[!NOTE]
   >
   >아직 그렇게 하지 않았다면 지금이 Cloud Manager 팀에 개발자 구성원을 추가할 적기입니다. 개발자 제품 프로필에 사용자 추가 를 참조하여 요약된 단계를 따르십시오.

1. 개발자 제품 프로필에 할당된 구성원은 Cloud Manager 및 [Cloud Manager Git 관리](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

   잘했어요! 이제 프로그램이 성공적으로 만들어지면 개발자가 액세스할 수 있는 Cloud Manager Git을 사용할 수 있습니다.


## 클라우드 환경 만들기 {#create-cloud-environments}

클라우드 프로그램을 성공적으로 만든 후 클라우드 환경을 만듭니다.

Cloud Manager에서 클라우드 환경을 만들려면 아래 절차를 따르십시오.

1. Cloud Manager의 **개요** 페이지를 선택하고 **추가** 환경 카드에서

   ![](/help/journey-onboarding/assets/setup-resources9.png)

   >[!IMPORTANT]
   >
   >이 단계를 성공적으로 완료하려면 비즈니스 소유자 또는 배포 관리자 역할의 Cloud Manager 사용자가 로그인해야 합니다.

   또한 빠른 시간 내에 [비디오](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) cloud Manager 환경 및 프로그램에 추가하는 방법에 대해 학습하는 자습서입니다.

1. 이렇게 하면 환경 추가를 안내하는 환경 추가 마법사가 시작됩니다. 먼저 개발 환경을 추가하여 마법사를 잘 이해합니다. 을(를) 참조하십시오. [환경 추가](/help/implementing/cloud-manager/manage-environments.md#adding-environments) 추가 정보

   >[!NOTE]
   >
   >아직 그렇게 하지 않았다면 지금이 Cloud Manager 팀에 개발자 구성원을 추가할 적기입니다. 개발자 제품 프로필에 사용자 추가 를 참조하여 요약된 단계를 따르십시오.

1. 개발자 제품 프로필에 할당된 구성원은 Cloud Manager 및 [Cloud Manager Git 관리.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

   잘했어요! 이제 프로그램이 성공적으로 만들어졌고 개발자가 액세스할 수 있는 Cloud Manager Git을 사용할 수 있습니다.

   축하합니다! 이제 클라우드 프로그램 환경이 만들어졌고 개발자가 팀에 추가되었습니다!

## 다음은 무엇입니까? {#whats-next}

Cloud Manager 관리 권한으로는 충분하지 않으므로 팀 구성원에게 인스턴스에 대한 권한을 부여해야 합니다. 클라우드 리소스가 생성되어 팀이 액세스할 준비가 되었으므로 시스템 관리자는 팀 구성원을 Adobe Admin Console의 AEM as a Cloud Service 제품 프로필에 할당해야 합니다.

>[!NOTE]
>
>AEM as a Cloud Service 사용자에게 액세스 권한을 부여하려면 두 제품 프로필 중 하나에 속해야 합니다 `AEM Users` 또는 `AEM Administrators`. 자세한 내용은 [Admin Console에서 제품 및 사용자 액세스 관리](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) 추가 정보

다음에 문서를 검토하여 온보딩 여정을 계속해야 합니다 [AEM as a Cloud Service 제품 프로필에 팀 구성원을 할당합니다.](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md)


## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* [프로그램 유형 및 프로그램 추가](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)
* [환경 유형 및 환경 추가](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)
* [Cloud Manager Git 관리](/help/implementing/cloud-manager/managing-code/accessing-repos.md)
* [Admin Console에서 AEM as a Cloud Service에 대한 액세스 구성](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html#adobe-ims-users)
