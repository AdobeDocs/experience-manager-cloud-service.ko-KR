---
title: Cloud Manager 액세스
description: 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
source-git-commit: fbf1e0b7cefb1dc981d7ee106283280fb2225007
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 1%

---

# Cloud Manager 액세스 {#cloud-resources}

의 이 부분에서 [온보딩 여정,](overview.md) 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다.

## 목표 {#objective}

이 온보딩 여정의 이전 문서에서, [Cloud Manager 제품 프로필에 팀 구성원 할당,](assign-profiles-cloud-manager.md) aemAaCS 팀에게 적절한 역할을 부여했습니다. 이제 팀에서 사용할 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다.

이 여정에서 이전 단계를 완료했으므로 팀이 Cloud Manager에 액세스할 수 있습니다. Cloud Manager는 프로그램 및 환경과 같은 프로젝트 리소스를 만들고 관리하는 데 사용됩니다.

이 문서를 읽은 후에는 다음 사항을 이해해야 합니다.

* 시스템 관리자가 **비즈니스 소유자** 역할은 조직에서 처음으로 Cloud Manager에 로그인하여 액세스하는 역할이어야 합니다.
* Cloud Manager에 로그인하는 방법

## Cloud Manager {#cloud-manager}

Cloud Manager는 AEM as a Cloud Service의 필수 구성 요소이며 팀의 단일 시작 지점으로 사용됩니다. 완벽한 테스트 및 최상의 코드 품질을 보장하여 탁월한 경험을 제공할 수 있도록 설계된 CI/CD 파이프라인이 내장된 엔터프라이즈 개발 설정을 지원하는 제품입니다. Cloud Manager는 클라우드 리소스 및 환경을 만드는 기능을 포함하여 셀프서비스 방식으로 시작하는 데 필요한 모든 것을 제공합니다.

일반적으로 **비즈니스 소유자** 제품 프로필은 프로그램 및 환경과 같은 클라우드 리소스를 추가할 책임이 있습니다. 이 사용자는 비즈니스 요구 사항을 이해하고 초기 Cloud Manager 설정을 완료하는 사용자를 파악합니다.

이 온보딩 여정을 위해 시스템 관리자는 이미 **비즈니스 소유자** 제품 프로필 및 은 클라우드 리소스를 설정합니다. 실제 프로젝트 요구 사항에 따라 비즈니스 소유자는 시스템 관리자와 동일하거나 그렇지 않을 수 있습니다.

>[!NOTE]
>
>기본적으로 AEM 환경에 액세스할 수 있는 사용자도 Cloud >Manager 사용자 역할을 갖습니다. 의 이 역할 자체는 사용자에게 프로그램 세부 사항 보기에 대한 액세스 권한을 제공하기에 충분하지 않습니다. 이러한 Cloud Manager 사용자 역할만 있는 사용자는 프로그램 메뉴 옵션을 통해 AEM 환경 작성자 URL로 이동할 수 있습니다(환경이 있는 경우). 이러한 사용자는 프로그램 수준 액세스 권한을 얻으려면 관리자에게 문의해야 합니다.

## 시스템 관리자 및 비즈니스 소유자로서 Cloud Manager에 액세스 {#access-sysadmin-bo}

에 할당한 팀 멤버 전에 **비즈니스 소유자** 역할은 cloud manager에 액세스하여 클라우드 리소스 만들기를 시작할 수 있으며, 시스템 관리자에게 **비즈니스 소유자** 이 온보딩 여정의 이전 단계에서 수행한 대로 Cloud Manager에 역할과 로그인합니다.

1. 시스템 관리자가 **비즈니스 소유자** 할당된 역할.

   * 이 여정의 이전 단계로 돌아갑니다. [Cloud Manager 제품 프로필에 팀 구성원 할당,](assign-profiles-cloud-manager.md) 을 참조하십시오 **비즈니스 소유자** 이 작업을 아직 수행하지 않았다면 시스템 관리자에게 문의하십시오.

1. Cloud Manager에 로그인 위치: [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 일반 랜딩 페이지로 표시됩니다.

를 사용하여 시스템 관리자로 성공적으로 로그인함 **비즈니스 소유자** 역할을 사용하면, **비즈니스 소유자** 역할. 이 메시지나 메시지의 확인을 받지 않습니다. 단순히 서명만 하면 됩니다.

를 사용하여 시스템 관리자로 Cloud Manager에 로그인하기 전까지 **비즈니스 소유자** 역할, 다른 사용자와 **비즈니스 소유자** 역할이 올바른 역할을 할당하더라도 Cloud Manager에서 프로그램을 만들 수 없습니다.

## Cloud Manager로 이동 {#navigate-cloud-manager}

을 사용하는 사용자 **비즈니스 소유자** 시작하는 링크가 있는 환영 이메일을 역할 이 받게 됩니다. 이 환영 이메일을 사용하여 Cloud Manager로 이동하려면 아래 단계를 따르십시오.

1. 환영 이메일에서 클릭 **시작**아래 그림과 같이,
   ![이메일 예](/help/journey-onboarding/assets/get-started-email.png)

1. Cloud Manager의 **프로그램 및 제품** 페이지.

   >[!TIP]
   >
   >또한 다음 위치에서 Cloud Manager의 로그인 페이지로 직접 이동할 수도 있습니다 `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)`. 나중에 참조할 수 있도록 이 페이지에 책갈피를 지정 하십시오.

1. Cloud Manager의 랜딩 페이지로 이동합니다.

또는 Cloud Manager의 **프로그램 및 제품** 다음 단계에 따라 Adobe Experience Cloud 홈페이지에서 페이지를 실행하십시오

1. 로 바로 이동 [Adobe Experience Cloud](https://experience.adobe.com) Adobe ID을 사용하여 로그인합니다.

1. Adobe Experience Cloud 홈페이지에서 Select **Experience Manager**.

   ![Experience Cloud 홈페이지](/help/journey-onboarding/assets/setup-resources2.png)

1. AEM 홈 페이지로 이동합니다. 여기에서 **Launch** on **Cloud Manager** 타일.

   ![AEM 홈 페이지](/help/journey-onboarding/assets/setup-resources3.png)

1. 로그인하면 Cloud Manager의 랜딩 페이지로 이동합니다. 자세한 내용은 [Cloud Manager 프로그램 보기](#viewing-programs) 섹션을 참조하십시오.

Cloud Manager를 통해 프로그램 및 제품에 액세스하는 방법은 사용자에 따라 다르며, Cloud Manager 사용 방식이나 프로그램 관리 방법에는 영향을 주지 않습니다.

>[!NOTE]
>
>Cloud Manager에서 할당된 역할과 애플리케이션 상태에 따라 Cloud Manager UI를 사용하는 동안 다른 화면이 표시됩니다.

## 프로그램 보기 {#viewing-programs}

Cloud Manager에 성공적으로 액세스하면 표시되는 내용은 다음 섹션에 자세히 설명된 프로그램 상태에 따라 달라집니다.

### 프로그램이 없는 경우 {#no-programs}

조직에 프로그램이 없는 경우 랜딩 페이지에서 첫 번째 프로그램을 생성하도록 안내합니다.

![프로그램 없음](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### 프로그램이 이미 있는 경우 {#programs-exist}

조직에 프로그램이 이미 존재하는 경우 랜딩 페이지에 기존 프로그램이 표시되고 추가 프로그램을 추가하는 버튼이 제공됩니다.

![프로그램이 있습니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### 프로그램이 존재하며 사용자가 시스템 관리자인 경우 {#programs-exist-sysadmin}

조직에 프로그램이 이미 있고 시스템 관리자라면 랜딩 페이지가 표시됩니다 **액세스 관리** 와 함께 사용할 단추 **프로그램 추가** 선택 사항입니다.

![시스템 관리자 보기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## 사용자 역할 확인 {#verify-user-roles}

Cloud Manager에 성공적으로 로그인하면 사용자에게 **비즈니스 소유자** 제품 프로필 .

1. 창 오른쪽 상단에서 프로필을 선택합니다.

   ![사용자 프로필](/help/journey-onboarding/assets/setup-resources5.png)

1. 선택 **사용자 역할** 사용자에게 할당된 역할을 표시합니다.

   ![사용자 역할](/help/journey-onboarding/assets/setup-resources6.png)

1. 대화 상자에서 사용자가 **비즈니스 소유자** 역할.

   ![사용자 역할 목록](/help/journey-onboarding/assets/setup-resources7.png)

비즈니스 소유자로서 Cloud Manager에 성공적으로 로그인했습니다! 을 지정하지 않은 경우 **비즈니스 소유자** 역할, 시스템 관리자에게 문의하십시오.

## 다음은 무엇입니까? {#whats-next}

이제 시스템 관리자로 Cloud Manager에 액세스할 수 있으므로 첫 번째 프로그램을 만들 수 있습니다.

다음에 문서를 검토하여 온보딩 여정을 계속해야 합니다 [프로그램 만들기](create-program.md) 방법은 어디에서 학습합니까?

## 추가 리소스 {#additional-resources}

추가 리소스에 따라 다음 사항에 대해 자세히 알아보십시오.

* [Cloud Manager 소개](/help/onboarding/cloud-manager-introduction.md) - Cloud Manager, Cloud Manager 프로그램 및 환경에 대해 알아봅니다.
