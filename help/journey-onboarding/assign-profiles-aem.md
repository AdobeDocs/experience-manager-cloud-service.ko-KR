---
title: AEM 제품 프로필 할당
description: 클라우드 리소스가 구성되면 AEM 제품 프로필을 사용하여 AEM 자체에 대한 액세스 권한을 팀에 부여해야 합니다.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 2%

---

# AEM 제품 프로필 할당 {#assign-profiles-aem}

의 이 부분에서 [온보딩 여정,](overview.md) AEM 제품 프로필을 사용하여 AEM에 대한 팀 액세스 권한을 부여하는 방법을 알아봅니다.

## 목표 {#objective}

이 온보딩 여정에서 이전 문서를 읽으면, [환경 만들기,](create-environments.md) 및 클라우드 리소스가 구성되도록 하려면 AEM 제품 프로필을 사용하여 AEM 자체에 대한 액세스 권한을 팀에 부여해야 합니다. 시스템 관리자는 AEM 제품 프로필을 할당하여 이 작업을 수행합니다.

이 문서를 읽은 후에는 다음 사항을 이해해야 합니다.

* AEM 제품 프로필이란 무엇입니까?
* AEM 사용자 제품 프로필에 팀 구성원을 추가하는 방법.
* AEM Administrators 제품 프로필에 팀 구성원을 추가하는 방법.

## AEM 제품 프로필 {#aem-product-profiles}

AEM을 사용하려면 팀 구성원을 하나 이상의 AEM 제품 프로필에 할당해야 합니다. Cloud Manager 액세스 권한으로는 충분하지 않습니다. 사용자는 두 제품 프로필 중 하나에 속해야 합니다.

* `AEM Users` - 이 그룹에는 일상적인 컨텐츠 작성 작업을 수행하는 일반 사용자가 포함됩니다.
* `AEM Administrators` - 이 그룹에는 고급 기능 또는 AEM을 담당하는 사용자가 포함됩니다.

AEM 제품 프로필에 할당된 모든 사용자도 Cloud Manager에 대한 읽기 전용 액세스 권한을 받습니다. Cloud Manager에 대한 쓰기 액세스 권한은 다른 제품 프로필을 통해 부여될 수 있습니다.

## 사전 요구 사항 {#prerequisites}

이 섹션을 읽기 전에 AEM을 사용할 팀에 대해 다음 정보를 사용할 수 있어야 합니다.

* 이름
* 이메일 주소
* 역할 및 책임

>[!TIP]
>
>온보딩을 위해 관리자, 개발자 및 컨텐츠 작성자와 같은 즉각적인 작업에 참여할 사용자를 처음에 추가하는 것이 좋습니다. 모든 사용자를 추가하지 않고 온보딩의 나머지 부분을 계속 진행할 수 있습니다. 온보딩을 완료하면 나중에 더 많은 사용자 수로 확장할 수 있습니다.

## AEM 제품 프로필 보기 {#view-profiles}

Admin Console에서 AEM 제품 프로필을 보려면 다음 단계를 따르십시오.

1. Admin Console에 로그인합니다. [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. 에서 **개요** 페이지를 선택하고 **Adobe Experience Manager as a Cloud Service** 에서 **제품 및 서비스** 카드.

   ![제품 및 서비스 카드](/help/journey-onboarding/assets/assign-team1.png)

1. 인스턴스를 탐색하고 선택합니다.

   ![인스턴스 선택](/help/journey-onboarding/assets/cloud-profiles-1.png)

1. 역할에 따라 사용자에게 할당할 수 있는 AEM as a Cloud Service 제품 프로필 목록이 표시됩니다.

   ![제품 프로필](/help/journey-onboarding/assets/cloud-profiles-2.png)

## 제품 프로필에 팀 구성원 추가 {#add-team-members}

사용 가능한 프로필에 익숙하므로 팀 구성원에게 필요에 따라 할당할 수 있습니다.

이러한 작업을 수행하려면 **비즈니스 소유자** Cloud Manager 제품 프로필.

1. Cloud Manager에서 프로그램으로 이동하고 **액세스 관리** 관심 환경의 컨텍스트에서 버튼입니다.

   ![액세스 관리](/help/journey-onboarding/assets/add-team1.png)

1. 새 탭이 환경의 작성자 인스턴스에 액세스할 수 있는 Admin Console으로 이동합니다. 선택 **AEM 관리자** 또는 **AEM 사용자** 권한에 따라 이 개인에게 제공되어야 합니다.

   ![액세스 권한 할당](/help/journey-onboarding/assets/add-team2.png)

1. 선택 `AEM Administrator` 또는 `AEM User` 을(를) 클릭합니다. **사용자 추가** 아래 표시된 대로 팀 구성원 추가를 완료하기 위해 필요한 세부 정보를 제출하십시오.

   ![팀 구성원 추가](/help/journey-onboarding/assets/add-team3.png)

1. 액세스 권한이 필요한 팀 구성원의 정보가 있는 경우 개발, 스테이징 및 프로덕션을 포함한 모든 환경에 대해 이 단계를 반복합니다.

추가한 사용자는 이제 AEM as a Cloud Service 작성자 서비스에 액세스할 수 있습니다.

## 여정의 끝 {#the-end}

축하합니다! AEM as a Cloud Service 제품 프로필에 할당한 사용자는 이제 AEM 작성 환경에 액세스하고 AEM으로 컨텐츠 만들기를 시작할 수 있습니다. 마찬가지로, 개발자는 이제 Cloud Manager에 액세스하여 git을 사용하여 사용자 지정 애플리케이션 코드를 저장하고 배포할 수 있습니다. 이러한 이유로 온보딩 여정이 완료되었으며 사용자는 이제 AEMaaCS를 사용할 수 있습니다.

그러나 작성자와 개발자가 시스템을 사용하는 방법을 보다 잘 이해하려면 이 온보딩 여정의 두 가지 옵션 부분으로 계속 진행할 수 있습니다.

* [개발자 및 배포 관리자 작업](developers.md) - 여기서 개발자가 Git에 액세스하여 사용자 지정 코드를 저장하고 Cloud Manager 파이프라인을 사용하여 배포하는 방법을 알아봅니다.
* [AEM 사용자 작업](aem-users.md) - 여기서 컨텐츠 만들기를 시작할 수 있는 AEM 환경에 액세스하는 방법을 알아봅니다.

## 추가 리소스 {#additional-resources}

* [Admin Console에서 제품 및 사용자 액세스 관리](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) - Admin Console을 사용하여 사용 액세스를 관리하는 방법을 알아봅니다.
* [AEM 액세스 구성 둘러보기](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en) - Admin Console에서 Adobe IMS 사용자, 사용자 그룹 및 제품 프로필을 구성하는 방법에 대해 알아보려면 이 개요를 살펴보십시오.

