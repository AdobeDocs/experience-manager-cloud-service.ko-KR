---
title: Cloud Manager를 통해 Cloud 리소스 설정
description: Cloud Manager를 통해 클라우드 리소스를 설정하는 방법을 배우려면 이 페이지를 따르십시오
hide: true
hidefromtoc: true
index: false
source-git-commit: 7dc150c51888ff2bfd80969d901f4996805498bf
workflow-type: tm+mt
source-wordcount: '1387'
ht-degree: 0%

---

# Cloud Manager를 통해 Cloud 리소스 설정 {#setup-cloud-resources}

*비즈니스 소유자* 역할에 할당된 시스템 관리자는 Cloud Manager에 액세스하여 로그인해야 합니다. 따라서 *비즈니스 소유자* 제품 프로필에 할당된 팀 구성원이 Cloud Manager에 로그인하여 클라우드 프로그램과 환경을 만들어야 전문가 팀을 시작할 수 있습니다.

## 목표 {#objective}

이 문서는 클라우드 리소스를 만드는 방법과 이 작업을 수행할 수 있는 사용자를 이해하는 데 도움이 됩니다.

이 섹션을 읽은 후에는 다음 사항을 이해해야 합니다.

* *비즈니스 소유자* 역할에 할당된 시스템 관리자는 Cloud Manager에 처음으로 액세스하여 로그인해야 합니다.
* 클라우드 프로그램 및 환경을 만드는 방법.

## 소개 {#introduction}

클라우드 리소스 추가는 Cloud Manager 비즈니스 소유자 제품 프로필에 할당된 팀 구성원이 Cloud Manager를 통해 수행됩니다. 일반적으로 비즈니스 요구 사항을 이해하고 초기 Cloud Manager 설정을 완료하는 사용자입니다.

아래 섹션을 따라 [클라우드 서비스 프로그램](#create-cloud-service-program) 및 [환경](#create-cloud-environments)을 만드는 방법을 알아보십시오.

### 전제 조건 {#prerequisites}

* *비즈니스 소유자* 역할에 할당된 시스템 관리자는 Cloud Manager에 액세스하여 로그인해야 합니다.

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/navigate-to-cloud-manager.html?lang=en)로 이동하여 로그인하는 방법을 이해합니다.

* [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)에 익숙해지십시오.

* 프로그램을 만들기 위한 고려 사항을 이해합니다. 자세한 내용은 이 비디오를 참조하십시오.

* Cloud Manager [프로그램](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html?lang=en) 및 [환경](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en)의 개념을 이해합니다

## Cloud Manager로 이동 {#navigate-cloud-manager}

*비즈니스 소유자* 사용자는 시작할 수 있는 위치에서 환영 이메일을 받거나, 찾을 수 없는 경우 [Adobe Experience Cloud](https://experience.adobe.com)로 직접 이동하여 Adobe ID을 사용하여 로그인합니다.

Cloud Manager로 이동하려면 아래 단계를 따르십시오.

1. 시작 이메일에서 아래 그림과 같이 **시작하기**를 클릭합니다.
   ![](/help/onboarding/onboarding-journey/assets/get-started-email.png)

1. Cloud Manager의 **프로그램 및 제품** 페이지로 이동합니다.

   >[!IMPORTANT]
   >또는 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager의 로그인 페이지로 직접 이동할 수도 있습니다. 나중에 이 페이지를 책갈피로 지정하여 Cloud Manager의 랜딩 페이지로 직접 이동하세요.

또한 Adobe Experience Cloud 홈 페이지에서 Cloud Manager의 **프로그램 및 제품** 페이지로 이동할 수 있습니다. 아래 단계를 따르십시오.

1. [Adobe Experience Cloud](https://experience.adobe.com)로 직접 이동하여 Adobe ID을 사용하여 로그인합니다.

1. Adobe Experience Cloud 홈 페이지에서 **Experience Manager**&#x200B;을 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources2.png)

1. AEM 홈 페이지로 이동합니다. 여기에서 **Cloud Manager** 를 시작합니다.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources3.png)

1. 로그인하면 Cloud Manager의 랜딩 페이지로 이동합니다.

   >[!NOTE]
   >[!UICONTROL Cloud Manager]에 할당된 역할과 응용 프로그램의 상태에 따라 [!UICONTROL Cloud Manager] UI를 사용하는 동안 다른 화면이 표시됩니다.

   아래에 설명된 세 가지 옵션 중 하나가 표시됩니다.

   * **Cloud Manager에 프로그램 없음**

      조직에 프로그램이 없는 경우 랜딩 페이지에서 아래 그림과 같이 첫 번째 프로그램을 만들라고 안내합니다.
      ![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

   * **Cloud Manager에 프로그램이 이미 있는 경우**

      조직에 프로그램이 이미 존재하는 경우 랜딩 페이지에서 아래 그림과 같이 다른 프로그램을 추가하고 기존 프로그램도 모두 표시합니다.

      ![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

   * **프로그램이 있고 사용자가 시스템 관리자인 경우**

      조직에 프로그램이 이미 있고 사용자가 시스템 관리자인 경우 랜딩 페이지에 **액세스 관리** 단추가 **프로그램 추가** 옵션과 함께 표시됩니다. 아래 그림은 아래 그림과 같습니다.

      ![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## 사용자 역할 확인 {#verify-user-roles}

Cloud Manager에 성공적으로 로그인했으면 아래 절차에 따라 비즈니스 소유자 제품 프로필이 할당되었는지 확인하십시오.

1. 아래 표시된 것처럼 오른쪽 상단에서 프로필을 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources5.png)

1. **사용자 역할**&#x200B;을 선택하고 비즈니스 소유자에게 할당되었는지 확인합니다.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources6.png)

1. 이를 통해 비즈니스 소유자로서의 사용자 역할이 확인됩니다.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources7.png)

   잘했어요! 비즈니스 소유자로서 Cloud Manager에 성공적으로 로그인했습니다!

## Cloud Service 프로그램 만들기 {#create-cloud-service-program}

Cloud Manager에서 클라우드 서비스 프로그램을 만들려면 아래 절차를 따르십시오.

1. 아래 표시된 대로 Cloud Manager 랜딩 페이지로 이동합니다.

   >[!NOTE]
   >이 단계를 성공적으로 완료하려면 Cloud Manager 비즈니스 소유자 제품 프로필에 할당된 팀 구성원이어야 합니다.

   여기서 **프로그램 추가**&#x200B;를 클릭하여 프로그램 추가 마법사를 시작합니다.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources4.png)

   >[!NOTE]
   >AEM as a Cloud Program을 만들고 프로그램을 만들기 전에 중요한 고려 사항에 대해 알아보려면 [비디오](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en)를 시청하십시오.

   >[!IMPORTANT]
   >프로그램 추가 마법사를 사용하는 방법에 대한 단계별 지침을 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/production-programs/creating-production-program.html?lang=en)로 이동하십시오.
   >
   >* 만든 후에는 프로그램 이름을 변경할 수 없습니다. 프로그램에 어떤 이름을 지정할 것인지 확인하는 것이 좋습니다.
   >* 프로그램 이름을 변경해야 하는 경우, Adobe 지원이 있는 사례를 열거나 Adobe 담당자에게 문의하십시오. 그들은 프로그램을 효과적으로 삭제하는 데 도움을 줄 것이다. 팀원들이 한 잠재적인 업무 손실과 함께 처음부터 다시 시작해야 합니다.


1. 클라우드 프로그램을 성공적으로 만들면 프로그램으로 이동하여 아래와 같이 프로그램의 **개요** 페이지를 볼 수 있습니다.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources8.png)

   >[!NOTE]
   >아직 그렇게 하지 않았다면 지금이 Cloud Manager 팀에 개발자 구성원을 추가할 적기입니다. 개발자 제품 프로필에 사용자 추가 를 참조하여 요약된 단계를 따르십시오.

1. 개발자 제품 프로필에 할당된 구성원은 Cloud Manager 및 [Cloud Manager Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en)에 로그인할 수 있습니다.

   잘했어요! 이제 프로그램이 성공적으로 만들어지면 개발자가 액세스할 수 있는 Cloud Manager Git을 사용할 수 있습니다.


## 클라우드 환경 만들기 {#create-cloud-environments}

클라우드 프로그램을 성공적으로 만든 후 클라우드 환경을 만듭니다.

Cloud Manager에서 클라우드 환경을 만들려면 아래 절차를 따르십시오.

1. Cloud Manager의 **개요** 페이지로 이동하고 환경 카드에서 **추가**&#x200B;를 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources9.png)

   >[!IMPORTANT]
   >이 단계를 성공적으로 완료하려면 비즈니스 소유자 또는 배포 관리자 역할의 Cloud Manager 사용자가 로그인해야 합니다.

   또한 빠른 [비디오](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en) 자습서를 시청하여 Cloud Manager 환경과 이를 프로그램에 추가하는 방법을 알아보십시오.

1. 이렇게 하면 환경 추가를 안내하는 환경 추가 마법사가 시작됩니다. 먼저 개발 환경을 추가하여 익숙해지십시오. 자세한 내용은 [환경 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#adding-environments)를 참조하십시오.

   >[!NOTE]
   >아직 그렇게 하지 않았다면 지금이 Cloud Manager 팀에 개발자 구성원을 추가할 적기입니다. 개발자 제품 프로필에 사용자 추가 를 참조하여 요약된 단계를 따르십시오.

1. 개발자 제품 프로필에 할당된 구성원은 Cloud Manager 및 [Cloud Manager Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en)에 로그인할 수 있습니다.

   잘했어요! 이제 프로그램이 성공적으로 만들어지면 개발자가 액세스할 수 있는 Cloud Manager Git을 사용할 수 있습니다.

   축하합니다! 이제 클라우드 프로그램 환경이 만들어졌고 개발자가 팀에 추가되었습니다!

## 다음은 무엇입니까? {#whats-next}

Cloud Manager 관리 권한으로는 충분하지 않으므로 팀 구성원에게 인스턴스에 대한 권한을 부여해야 합니다. 클라우드 리소스가 만들어지고 팀이 액세스할 준비가 되었으므로 시스템 관리자는 팀 구성원을 AEM에 Adobe Admin Console의 Cloud Service 제품 프로필로 할당해야 합니다.

>[!NOTE]
>Cloud Service 사용자로 AEM에 대한 액세스 권한을 부여받으려면 두 제품 프로필 `AEM Users` 또는 `AEM Administrators` 중 하나에 속해야 합니다. 자세한 내용은 [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#managing-products-and-user-access-in-admin-console)에서 제품 및 사용자 액세스 관리 를 참조하십시오.

다음에 AEM에 Cloud Service 제품 프로필로 팀 구성원 할당 문서를 검토하여 온보딩 여정을 계속해야 합니다.


## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* [프로그램 유형 및 프로그램 추가](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en)
* [환경 유형 및 환경 추가](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en)
* [Cloud Manager Git 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en)
* [Admin Console에서 AEM as a Cloud Service에 대한 액세스 구성](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=en#adobe-ims-users)
