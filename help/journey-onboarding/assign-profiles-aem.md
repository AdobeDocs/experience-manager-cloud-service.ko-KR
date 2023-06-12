---
title: AEM 제품 프로필 할당
description: 클라우드 리소스를 구성한 후에는 AEM 제품 프로필을 사용하여 AEM 자체에 대한 액세스 권한을 팀에 부여해야 합니다.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: fd14d9f88fed4ef0f90b5dd0c92c53b1a298bd76
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 100%

---

# AEM 제품 프로필 할당 {#assign-profiles-aem}

>[!CONTEXTUALHELP]
>id="assets_user_entitlements"
>title="AEM 제품 프로필 할당"
>abstract="Experience Manager Assets를 사용할 권한이 없습니다. 관리자에게 문의하십시오."

이 [온보딩 여정](overview.md) 부분에서는 AEM 제품 프로필을 사용하여 팀에 AEM 액세스 권한을 부여하는 방법을 배웁니다.

## 목표 {#objective}

이 온보딩 여정의 이전 문서인 [환경 만들기](create-environments.md)를 읽고 클라우드 리소스를 구성한 후에는 AEM 제품 프로필을 사용하여 AEM 자체에 대한 액세스 권한을 팀에 부여해야 합니다. 시스템 관리자는 AEM 제품 프로필을 할당하여 이 작업을 수행합니다.

이 문서를 읽은 후에는 다음 사항을 이해할 수 있습니다.

* AEM 제품 프로필의 정의
* AEM 사용자 제품 프로필에 팀원을 추가하는 방법
* AEM 관리자 제품 프로필에 팀원을 추가하는 방법

## AEM 제품 프로필 {#aem-product-profiles}

AEM을 사용하려면 팀원이 하나 이상의 AEM 제품 프로필에 할당되어야 합니다. Cloud Manager에 액세스할 수 있는 권한이 충분하지 않습니다. 사용자는 다음 두 제품 프로필 중 하나에 속해야 합니다.

* `AEM Users` - 이 그룹에는 일상적인 콘텐츠 작성 작업을 수행하는 일반 사용자가 포함됩니다.
* `AEM Administrators` - 이 그룹에는 고급 기능 또는 AEM을 담당하는 사용자가 포함됩니다.

AEM 제품 프로필에 할당된 모든 사용자는 Cloud Manager에 대한 읽기 전용 액세스 권한도 갖게 됩니다. Cloud Manager에 대한 쓰기 액세스 권한은 다른 제품 프로필을 통해 부여될 수 있습니다.

>[!CAUTION]
>
>제품 프로필 중 AEM 관리자 또는 AEM 사용자를 편집하거나 삭제하지 마십시오. 이러한 프로필 이름을 편집하면 AEM 클라우드 인스턴스에 대한 로그인이 중단될 수 있습니다.

## 사전 요구 사항 {#prerequisites}

이 섹션을 읽기 전에 AEM을 사용할 팀에 대해 다음 정보를 알고 있어야 합니다.

* 이름
* 이메일 주소
* 역할 및 책임

>[!TIP]
>
>온보딩을 위해 관리자, 개발자 및 콘텐츠 작성자와 같이 즉각적인 작업에 참여할 사용자를 초기에 추가하는 것이 좋습니다. 모든 사용자를 추가하지 않고 나머지 온보딩을 계속할 수 있습니다. 온보딩을 마친 후에는 나중에 더 많은 사용자로 확장할 수 있습니다.

## AEM 제품 프로필 보기 {#view-profiles}

Admin Console에서 AEM 제품 프로필을 보려면 다음 단계를 따르십시오.

1. Admin Console([`https://adminconsole.adobe.com`)에 로그인합니다.](https://adminconsole.adobe.com)

1. **개요** 페이지의 **제품 및 서비스** 카드에서 **Adobe Experience Manager as a Cloud Service**&#x200B;를 선택합니다.

   ![제품 및 서비스 카드](/help/journey-onboarding/assets/assign-team1.png)

1. 인스턴스로 이동하여 선택합니다.

   ![인스턴스 선택](/help/journey-onboarding/assets/cloud-profiles-1.png)

1. 역할에 따라 사용자에게 할당할 수 있는 AEM as a Cloud Service 제품 프로필 목록이 표시됩니다.

   ![제품 프로필](/help/journey-onboarding/assets/cloud-profiles-2.png)

## 제품 프로필에 팀원 추가 {#add-team-members}

이제 사용 가능한 프로필에 익숙해졌으므로 필요에 따라 팀원에게 할당할 수 있습니다.

이러한 작업을 수행하려면 **비즈니스 소유자** Cloud Manager 제품 프로필이 있는 시스템 관리자여야 합니다.

1. Cloud Manager에서 프로그램으로 이동하고 관심 환경 컨텍스트에서 **액세스 관리** 버튼을 선택합니다.

   ![액세스 관리](/help/journey-onboarding/assets/add-team1.png)

1. 새 탭은 환경의 작성자 인스턴스에 액세스할 수 있는 Admin Console로 이동합니다. 이 개인에게 부여해야 하는 권한에 따라 **AEM 관리자** 또는 **AEM 사용자**&#x200B;를 선택합니다.

   ![액세스 할당](/help/journey-onboarding/assets/add-team2.png)

1. `AEM Administrator` 또는 `AEM User`를 선택하고 아래와 같이 **사용자 추가**&#x200B;를 클릭한 다음 필요한 세부 정보를 제출하여 팀원을 추가합니다.

   ![팀원 추가](/help/journey-onboarding/assets/add-team3.png)

1. 액세스 권한이 필요한 팀원의 정보가 있는 경우 개발, 스테이징 및 프로덕션을 포함한 모든 환경에 대해 이 단계를 반복합니다.

추가한 사용자는 이제 AEM as a Cloud Service 작성자 서비스에 액세스할 수 있습니다.

## 여정의 끝 {#the-end}

축하합니다! AEM as a Cloud Service 제품 프로필에 할당한 사용자는 이제 AEM 작성 환경에 액세스하고 AEM as a Cloud Service를 사용하여 콘텐츠를 만들 수 있습니다. 마찬가지로 개발자는 이제 Cloud Manager에 액세스하여 git을 사용하여 사용자 정의 애플리케이션 코드를 저장하고 배포할 수 있습니다. 이제 온보딩 여정이 완료되었으며 사용자는 AEMaaCS를 사용할 수 있습니다.

그러나 작성자와 개발자가 시스템을 사용하는 방법을 더 잘 이해하려면 이 온보딩 여정의 두 가지 선택적 단계를 계속 진행할 수 있습니다.

* [개발자 및 배포 관리자 작업](developers.md) - 개발자가 git에 액세스하여 사용자 정의 코드를 저장하고 Cloud Manager 파이프라인을 사용하여 배포하는 방법을 배울 수 있습니다.
* [AEM 사용자 작업](aem-users.md) - 콘텐츠 작성을 시작할 수 있는 AEM 환경에 액세스하는 방법을 배울 수 있습니다.

## 추가 리소스 {#additional-resources}

온보딩 여정의 콘텐츠를 능가하려는 경우 다음은 추가적인 옵션 리소스입니다.

* [Admin Console에서 제품 및 사용자 액세스 관리](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) - Admin Console을 사용하여 사용 액세스를 관리하는 방법을 알아봅니다.
* [AEM에 대한 액세스 구성 설명](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=ko) - Admin Console에서 Adobe IMS 사용자, 사용자 그룹 및 제품 프로필을 구성하는 방법에 대해 알아보려면 이 간략한 설명을 확인합니다.

