---
title: 'Cloud Manager 제품 프로필에 팀 구성원 할당 '
description: 팀 구성원을 Cloud Manager 제품 프로필에 할당하는 방법을 알려면 이 페이지를 따르십시오
hide: true
index: false
source-git-commit: 4ef8c167e24a18af578d58c21fd1079a080f71d1
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 0%

---


# Cloud Manager 제품 프로필에 팀 구성원 할당 {#assign-team-members}

[Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en)에 로그인하고 [시스템 관리자](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/system-administrator.html?lang=en)로 권한을 본 후에는 이제 Cloud Manager 제품 프로필에 팀 구성원을 할당할 준비가 되었습니다.

## 목표 {#objective}

이 문서에서는 Adobe Admin Console에서 Cloud Manager 제품 프로필에 팀 구성원을 할당하는 방법을 요약합니다.

이 섹션을 읽은 후에는 다음을 수행할 수 있습니다.

* 팀 구성원을 추가해야 하는 이유와 방법을 이해합니다.
* 비즈니스 소유자, 배포 관리자 및 개발자와 같은 세 가지 서로 다른 Cloud Manager 제품 프로필에 대해 알아봅니다.
* 비즈니스 소유자, 배포 관리자 및 개발자와 같은 Cloud Manager 제품 프로필에 팀 구성원을 지정합니다.

## 전제 조건 {#prerequisites}

이 섹션을 시작하기 전에 다음 전제 조건을 고려해야 합니다. 다음을 수행해야 합니다.

* 시스템 관리자가 되어 [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)을 이해합니다.
* [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) 기본 사항을 이해합니다.
* 팀 구성원에 대한 세부 정보를 제공합니다. 시스템 관리자는 이름, 전자 메일 주소, AEM as a Cloud Service에 액세스해야 하는 팀 구성원의 역할 및 책임이 있어야 합니다.

   >[!NOTE]
   >온보딩을 위해 관리자, 개발자 및 컨텐츠 작성자와 같은 즉각적인 작업에 참여할 사용자를 처음에 추가하는 것이 좋습니다. 모든 사용자를 추가하지 않고 온보딩의 나머지 부분을 계속 진행할 수 있습니다. 온보딩을 완료하면 나중에 더 많은 사용자 수로 확장할 수 있습니다.

## Cloud Manager 제품 프로필 검토 {#review-product-profiles}

Adobe Admin Console에서 Cloud Manager 프로필 목록을 확인할 수 있습니다.

>[!NOTE]
>Admin Console에서 Cloud Manager 제품 프로필을 검토하기 전에 사용 가능한 [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)을 검토하는 것이 좋습니다.

Cloud Manager 프로필 목록을 보려면 아래 절차를 따르십시오.

1. [Adobe Admin Console](https://adminconsole.adobe.com/)에 로그인합니다. **개요** 페이지에서 **Adobe Experience Manager을**&#x200B;제품 및 서비스&#x200B;**카드에서 Cloud Service**&#x200B;로 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

   >[!NOTE]
   >Admin Console 사용 방법에 대해 알아보려면 Admin Console 로그인 을 참조하십시오.


1. 모든 인스턴스 목록에서 **Cloud Manager** 인스턴스로 이동합니다.

   ![](/help/onboarding/onboarding-journey/assets/assign-team2.png)

1. 사전 구성된 [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) 목록이 표시됩니다.

   ![](/help/onboarding/onboarding-journey/assets/assign-team3.png)


## 비즈니스 소유자 제품 프로필에 사용자 할당 {#assign-users-business-owner}

이제 사용자를 추가하고 Cloud Manager 비즈니스 소유자 제품 프로필에 할당할 준비가 되었습니다.

>[!NOTE]
>이렇게 하려면 Adobe Admin Console에서 사용자를 두 제품(이 경우 Cloud Service으로 AEM)과 [Cloud Manager Business Owner 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)에 모두 추가해야 합니다.

다음 단계는 이 단계를 안내합니다.

1. Cloud Manager 프로그램을 관리할 사용자를 식별하고 사용자를 비즈니스 소유자 제품 프로필에 추가합니다. 시스템 관리자는 Cloud Manager에 액세스하여 로그인한 첫 번째 사람이어야 합니다. 먼저 비즈니스 소유자 제품 프로필에 사용자(시스템 관리자)를 추가해야 합니다.

1. [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **개요** 페이지에서 **Adobe Experience Manager을**&#x200B;제품 및 서비스&#x200B;**카드에서 Cloud Service** 제품으로 선택하십시오.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. 위쪽 탐색에서 **사용자** 탭을 선택한 다음 **사용자 추가**&#x200B;를 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. **사용자를 팀에 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다. ID 유형에 대해 팀 구성원의 Federated ID이 아직 설정되지 않은 경우 Adobe ID을 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. 제품 선택에서 **Adobe Experience Manager을 Cloud Service**&#x200B;로 선택하고 아래 표시된 대로 **비즈니스 소유자** 제품 프로필을 사용자에게 할당합니다.

   >[!NOTE]
   >아래 그림과 같이 [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)을 참조하여 올바른 사용자에게 Admin Console에서 올바른 역할이 지정되는지 확인하십시오.

   ![](/help/onboarding/onboarding-journey/assets/assign-team6.png)

   >[!NOTE]
   >사용자가 Cloud Manager에 액세스할 수 있도록 사용자를 하나 이상의 제품 프로필에 할당합니다. 비즈니스 소유자에게 사용자(시스템 관리자)를 할당해야 합니다.

1. **저장**&#x200B;을 클릭합니다. 추가한 사용자에게 환영 이메일이 전송됩니다. 초대받은 사용자는 환영 이메일에서 링크를 클릭하고 Adobe ID을 사용하여 로그인하여 Cloud Manager에 액세스할 수 있습니다.

   축하합니다! 새로 구성된 Cloud Manager 팀(&#39;비즈니스 소유자&#39; 역할에 지정된 본인 포함)이 설정되었습니다. 구성원은 로그인하여 Cloud Manager에 액세스할 수 있도록 초대하는 환영 이메일을 받게 됩니다. 비즈니스 소유자의 역할에서는 이제 Cloud Manager에 로그인하고 클라우드 리소스를 만들 수 있습니다.

## 배포 관리자에 사용자 할당 제품 프로필 {#assign-users-deployment-manager}

1. Cloud Manager 프로그램을 관리할 사용자를 식별하고 이를 Deployment Manager 제품 프로필에 추가합니다. 시스템 관리자는 Cloud Manager에 액세스하여 로그인한 첫 번째 사람이어야 합니다. 이전 섹션에 설명된 대로 먼저 비즈니스 소유자 제품 프로필에 사용자(시스템 관리자)를 추가해야 합니다.

1. [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **개요** 페이지에서 **Adobe Experience Manager을**&#x200B;제품 및 서비스&#x200B;**카드에서 Cloud Service** 제품으로 선택하십시오.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. 위쪽 탐색에서 **사용자** 탭을 선택한 다음 **사용자 추가**&#x200B;를 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. **사용자를 팀에 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다. ID 유형에 대해 팀 구성원의 Federated ID이 아직 설정되지 않은 경우 Adobe ID을 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. 제품 선택에서 **Adobe Experience Manager을 Cloud Service**&#x200B;로 선택하고 아래 표시된 대로 **배포 관리자** 제품 프로필을 사용자에게 할당합니다.

   >[!NOTE]
   >아래에서 보듯이 적절한 사용자에게 Admin Console에서 적절한 역할이 할당되었는지 확인하려면 [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) 을 참조하십시오.

   ![](/help/onboarding/onboarding-journey/assets/assign-team6.png).

   >[!IMPORTANT]
   >Cloud Manager 리소스를 만든 후 배포 관리자 제품 프로필에 사용자를 추가할 수 있습니다.

## 개발자 제품 프로필에 사용자 할당 {#assign-users-developer}

1. Cloud Manager 프로그램을 관리할 사용자를 식별하고 개발자 제품 프로필에 추가합니다. 시스템 관리자는 Cloud Manager에 액세스하여 로그인한 첫 번째 사람이어야 합니다. 먼저 비즈니스 소유자 제품 프로필에 사용자(시스템 관리자)를 추가해야 합니다.

1. [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **개요** 페이지에서 **Adobe Experience Manager을**&#x200B;제품 및 서비스&#x200B;**카드에서 Cloud Service** 제품으로 선택하십시오.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. 위쪽 탐색에서 **사용자** 탭을 선택한 다음 **사용자 추가**&#x200B;를 선택합니다.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. **사용자를 팀에 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다. ID 유형에 대해 팀 구성원의 Federated ID이 아직 설정되지 않은 경우 Adobe ID을 선택합니다.

   >[!NOTE]
   >Adobe Admin Console의 ID 유형에 대한 자세한 내용은 [ID 개요](https://helpx.adobe.com/enterprise/using/identity.html)를 참조하십시오.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. 제품 선택에서 **Adobe Experience Manager을 Cloud Service**&#x200B;로 선택하고 아래 표시된 대로 **개발자** 제품 프로필을 사용자에게 할당합니다.

   >[!NOTE]
   >아래에서 보듯이 적절한 사용자에게 Admin Console에서 적절한 역할이 할당되었는지 확인하려면 [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) 을 참조하십시오.

   ![](/help/onboarding/onboarding-journey/assets/assign-team6.png).


   >[!IMPORTANT]
   >Cloud Manager 리소스를 만든 후 개발자 제품 프로필에 사용자를 추가할 수 있습니다.

## 다음은 무엇입니까? {#whats-next}

비즈니스 소유자, 배포 관리자 및 개발자와 같은 세 가지 서로 다른 Cloud Manager 제품 프로필에 대해 학습했습니다. 다음으로 비즈니스 소유자, 배포 관리자 및 개발자와 같은 Cloud Manager 제품 프로필에 팀 구성원을 할당했습니다. 이제 Cloud Manager를 통해 문서 설정 클라우드 리소스를 검토하여 온보딩 여정을 계속할 준비가 되었습니다. 여기서 다음을 확인할 수 있습니다.

1. *비즈니스 소유자* 역할에 지정된 시스템 관리자는 Cloud Manager에 액세스하여 로그인해야 합니다.

1. 다음으로, *비즈니스 소유자* 역할의 Cloud Manager 사용자는 클라우드 프로그램 및 환경을 포함하여 클라우드 리소스에 로그인하고 설정할 수 있습니다. 이렇게 하면 전문가 팀이 가능한 한 빨리 AEM에 Cloud Service으로 액세스할 수 있습니다.

1. *비즈니스 소유자*&#x200B;가 클라우드 리소스를 설정한 후 Cloud Manager 제품 프로필에 성공적으로 추가된 *개발자* 및 *배포 관리자*&#x200B;가 Cloud Manager에 액세스하여 학습 경로를 계속 진행할 수 있는 방법에 대해 숙지할 수 있습니다.

## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=en)
* [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)
* [Admin Console ID 개요](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
