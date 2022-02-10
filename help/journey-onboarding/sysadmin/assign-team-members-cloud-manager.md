---
title: Cloud Manager 제품 프로필에 팀 구성원 할당
description: 팀 구성원을 Cloud Manager 제품 프로필에 할당하는 방법을 알려면 이 페이지를 따르십시오
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 22a08a0cb80052485309ce3d33537e9fe303c6f5
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 1%

---

# Cloud Manager 제품 프로필에 팀 멤버 할당 {#assign-team-members}

이 여정의 이전 단계에서 [온보딩 프로세스 시작](/help/journey-onboarding/sysadmin/get-started-onboarding-journey.md)이제 Admin Console에 로그인하고 시스템 관리자로 권한이 확인되었습니다. 이제 팀 구성원을 Cloud Manager 제품 프로필에 할당할 준비가 되었습니다.

## 목표 {#objective}

이 문서에서는 Adobe Admin Console에서 Cloud Manager 제품 프로필에 팀 구성원을 할당하는 방법을 요약합니다. 할당되면 이 구성원은 이 여정의 다음 단계에 설명된 대로 액세스 클라우드 리소스를 만들 수 있습니다.

이 섹션을 읽은 후에는 다음을 수행할 수 있습니다.

* 팀 구성원을 추가해야 하는 이유와 방법을 이해합니다.
* 다음 세 가지 중요한 Cloud Manager 제품 프로필에 대해 알아보십시오. **비즈니스 소유자**, **배포 관리자**, 및 **개발자**.
* Cloud Manager 제품 프로필에 팀 구성원을 지정합니다.

>[!TIP]
>
>온보딩을 위해 Adobe은 처음에 관리자, 개발자 및 컨텐츠 작성자와 같은 즉각적인 작업에 참여할 사용자를 추가하는 것을 권장합니다. 모든 사용자를 추가하지 않고 온보딩 프로세스를 계속할 수 있습니다. 온보딩을 완료하면 추가 사용자를 추가할 수 있습니다.

## 전제 조건 {#prerequisites}

이 섹션을 시작하기 전에 다음 전제 조건을 충족해야 합니다. 다음을 수행해야 합니다.

* 시스템 관리자가 되어 Cloud Manager 제품 프로필을 이해합니다.
   * 로 돌아갑니다. [온보딩 여정 개요](onboarding-journey-overview.md) 이러한 개념을 잘 모르는 경우
* Adobe Admin Console 기본 사항을 이해합니다.
   * 로 돌아갑니다. [온보딩 여정 개요](onboarding-journey-overview.md) 이러한 개념을 잘 모르는 경우
* 다음을 포함하여 AEM as a Cloud Service에 액세스해야 하는 팀 구성원에 대한 세부 정보를 제공합니다
   * 이름
   * 이메일 주소
   * 역할 및 책임

## Cloud Manager 제품 프로필 검토 {#review-product-profiles}

Adobe Admin Console에서 Cloud Manager 프로필 목록을 확인할 수 있습니다.

1. Adobe Admin Console에 로그인 위치 [adminconsole.adobe.com](https://adminconsole.adobe.com/) 그리고 **개요** 페이지를 선택하고 **Adobe Experience Manager as a Cloud Service** 에서 **제품 및 서비스** 카드.

   ![AEM as a product](/help/journey-onboarding/assets/assign-team1.png)

1. 로 이동합니다 **Cloud Manager** 모든 인스턴스 목록에서 인스턴스를 생성합니다.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. 사전 구성된 Cloud Manager 제품 프로필 목록이 표시됩니다.

   ![제품 프로필](/help/journey-onboarding/assets/assign-team3.png)

## 비즈니스 소유자 제품 프로필에 사용자 할당 {#assign-users-business-owner}

이제 사용자를 추가하고 이 사용자를 **비즈니스 소유자** 제품 프로필 .

1. Cloud Manager 프로그램을 관리할 사용자를 식별하고 사용자를 비즈니스 소유자 제품 프로필에 추가합니다.

1. Admin Console에 로그인합니다. [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) 그리고 **개요** 페이지를 선택하고 **Adobe Experience Manager as a Cloud Service** product from **제품 및 서비스** 카드.

   ![제품 및 서비스](/help/journey-onboarding/assets/assign-team1.png)

1. 을(를) 선택합니다 **사용자** 위쪽 탐색에서 tab 키를 누른 다음 을 선택합니다 **사용자 추가**.

   ![사용자 추가](/help/journey-onboarding/assets/assign-team4.png)

1. 에서 **팀에 사용자 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다.

   * 팀 구성원의 페더레이션 ID를 아직 설정하지 않은 경우 을 선택합니다 **Adobe ID** 대상 **ID 유형**.

   ![사용자 세부 사항 추가](/help/journey-onboarding/assets/assign-team5.png)

1. 아래의 더하기 단추를 클릭합니다. **제품 또는 사용자 그룹 선택** 제품 선택을 시작하고 을(를) 선택합니다. **Adobe Experience Manager as a Cloud Service** 및 할당 **비즈니스 소유자** 제품 프로필을 사용자 지정 합니다.

   * 사용자가 Cloud Manager에 액세스할 수 있도록 모든 사용자를 하나 이상의 제품 프로필에 할당합니다.
   * 자신을 시스템 관리자로 **비즈니스 소유자** 역할.

   ![사용자 할당](/help/journey-onboarding/assets/assign-team6.png)

1. 클릭 **저장** 추가한 사용자에게 환영 이메일이 전송됩니다. 초대받은 사용자는 환영 이메일에서 링크를 클릭하고 Adobe ID을 사용하여 로그인하여 Cloud Manager에 액세스할 수 있습니다.

1. 팀의 사용자에 대해 이러한 단계를 반복합니다.

새로 구성된 Cloud Manager 팀(자신에게 지정된 팀 포함) **비즈니스 소유자** 역할)이 설정되었습니다. 의 역할에서 **비즈니스 소유자**&#x200B;이제 Cloud Manager에 로그인하고 클라우드 리소스를 만들 수 있도록 한 단계 더 떨어져 있습니다.

## 배포 관리자에 사용자 할당 제품 프로필 {#assign-users-deployment-manager}

1. Cloud Manager 프로그램을 관리할 사용자를 식별하고 이를 Deployment Manager 제품 프로필에 추가합니다.

1. Admin Console에 로그인합니다. [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) 그리고 **개요** 페이지 선택 **Adobe Experience Manager as a Cloud Service** 제품에서 **제품 및 서비스** 카드.

   ![제품 및 서비스](/help/journey-onboarding/assets/assign-team1.png)

1. 을(를) 선택합니다 **사용자** 위쪽 탐색에서 tab 키를 누른 다음 을 선택합니다 **사용자 추가**.

   ![사용자 추가](/help/journey-onboarding/assets/assign-team4.png)

1. 에서 **팀에 사용자 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다.

   * 팀 구성원의 페더레이션 ID를 아직 설정하지 않은 경우 을 선택합니다 **Adobe ID** 대상 **ID 유형**.

   ![ID 입력](/help/journey-onboarding/assets/assign-team5.png)

1. 아래의 더하기 단추를 클릭합니다. **제품 또는 사용자 그룹 선택** 제품 선택을 시작하고 을(를) 선택합니다. **Adobe Experience Manager as a Cloud Service** 및 할당 **배포 관리자** 제품 프로필을 사용자 지정 합니다.

   ![프로필 할당](/help/journey-onboarding/assets/assign-team6.png).

## 개발자 제품 프로필에 사용자 할당 {#assign-users-developer}

1. Cloud Manager 프로그램을 관리할 사용자를 식별합니다.

1. Admin Console에 로그인합니다. [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) 그리고 **개요** 페이지 선택 **Adobe Experience Manager as a Cloud Service** 제품에서 **제품 및 서비스** 카드.

   ![제품 및 서비스](/help/journey-onboarding/assets/assign-team1.png)

1. 을(를) 선택합니다 **사용자** 위쪽 탐색에서 tab 키를 누른 다음 을 선택합니다 **사용자 추가**.

   ![사용자 추가](/help/journey-onboarding/assets/assign-team4.png)

1. in **팀에 사용자 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다.

   * 팀 구성원의 페더레이션 ID를 아직 설정하지 않은 경우 을 선택합니다 **Adobe ID** 대상 **ID 유형**.

   ![사용자 ID 추가](/help/journey-onboarding/assets/assign-team5.png)

1. 아래의 더하기 단추를 클릭합니다. **제품 또는 사용자 그룹 선택** 제품 선택을 시작하고 을(를) 선택합니다. **Adobe Experience Manager as a Cloud Service** 및 할당 **개발자** 제품 프로필을 사용자 지정 합니다.

   ![프로필 할당](/help/journey-onboarding/assets/assign-team6.png).

## 다음은 무엇입니까? {#whats-next}

온보딩 여정의 이 부분에서 Admin Console의 역할에 팀 구성원을 할당하는 방법에 대해 모든 정보를 알아보았습니다. 이제 다음을 수행해야 합니다.

* 팀 구성원을 추가해야 하는 이유와 방법을 이해합니다.
* 다음 세 가지 중요한 Cloud Manager 제품 프로필을 이해합니다. **비즈니스 소유자**, **배포 관리자**, 및 **개발자**.
* 팀 구성원을 Cloud Manager 제품 프로필에 할당할 수 있습니다.

이제 다음 번 문서를 검토하여 온보딩 여정을 계속할 준비가 되었습니다 [Cloud Manager를 통해 Cloud 리소스 설정](/help/journey-onboarding/sysadmin/setup-cloud-resources-via-cloud-manager.md):

1. 다른 비즈니스 소유자가 프로그램을 생성하려면 **비즈니스 소유자** 역할, 먼저 Cloud Manager에 액세스하여 로그인해야 합니다.
1. 사용자가 **비즈니스 소유자** 역할은 클라우드 프로그램 및 환경을 포함하여 클라우드 리소스에 로그인하고 설정할 수 있습니다.
1. 사용자가 **개발자** 및 **배포 관리자** 역할은 Cloud Manager에 액세스할 수 있습니다.

## 추가 리소스 {#additional-resources}

앞에서 설명한 대로 온보딩 여정을 계속 사용하는 것이 좋습니다. 이 여정에서 특정 주제를 자세히 살펴보려면 이러한 추가 리소스를 참조하십시오.

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=en)
* [Cloud Manager 제품 프로필](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)
* [Admin Console ID 개요](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
