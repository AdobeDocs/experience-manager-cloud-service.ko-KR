---
title: Cloud Manager 액세스
description: 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
source-git-commit: 5c9dbaa25f0142afdae8b09dc18d1e1aaaf4c1fb
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 52%

---

# Cloud Manager 액세스 {#cloud-resources}

의 이 부분에서 [온보딩 여정,](overview.md) 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 배웁니다.

## 목표 {#objective}

이 온보딩 여정의 이전 문서인 [Cloud Manager 제품 프로필에 팀원 할당](assign-profiles-cloud-manager.md)에서 AEMaaCS 팀에 적절한 역할을 부여했습니다 이제 팀에서 사용하는 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다.

이 여정의 이전 단계를 완료했으므로 팀에서 Cloud Manager에 액세스할 수 있습니다. Cloud Manager는 프로그램 및 환경과 같은 프로젝트 리소스를 생성하고 관리하는 데 사용됩니다.

이 문서를 읽고 나면 다음 사항을 이해할 수 있습니다.

* 시스템 관리자가 **비즈니스 소유자** 역할은 조직에서 가장 먼저 Cloud Manager에 로그온하고 액세스해야 합니다.
* Cloud Manager에 로그인하는 방법을 이해합니다.

## Cloud Manager {#cloud-manager}

Cloud Manager는 AEM as a Cloud Service의 필수 구성 요소이며 팀의 단일 진입점 역할을 합니다. Cloud Manager는 철저한 테스트와 최고의 코드 품질을 보장하여 탁월한 경험을 제공할 수 있도록 기업 개발 설정 및 특수 목적으로 구축된 CI/CD 파이프라인을 통해 기업 개발 설정을 통해 고객을 지원합니다. Cloud Manager는 클라우드 리소스 및 환경을 생성하는 기능을 포함하여 셀프서비스 방식으로 시작하는 데 필요한 모든 기능을 제공합니다.

일반적으로 **비즈니스 소유자** 제품 프로필에 할당된 팀원은 프로그램 및 환경과 같은 클라우드 리소스를 추가할 책임이 있습니다. 이 개인은 비즈니스 요구 사항을 이해하며 초기 Cloud Manager 설정을 완료합니다.

이 온보딩 여정의 목적을 위해 시스템 관리자는 이미 자신에게 할당되었습니다. **비즈니스 소유자** 제품 프로필 이며 클라우드 리소스를 설정할 수 있습니다. 비즈니스 소유자는 실제 프로젝트 요구 사항에 따라 시스템 관리자와 동일하거나 동일하지 않을 수 있습니다.

## 시스템 관리자 및 비즈니스 소유자로 Cloud Manager에 액세스 {#access-sysadmin-bo}

에 할당한 팀원 앞 **비즈니스 소유자** 역할은 cloud manager에 액세스하여 클라우드 리소스 생성을 시작할 수 있습니다. 시스템 관리자에게 **비즈니스 소유자** 역할. 또한 이 온보딩 여정의 이전 단계에서와 같이 Cloud Manager에 로그인해야 합니다.

1. 시스템 관리자로서 **비즈니스 소유자** 역할이 할당되었는지 확인합니다.

   * 이 여정의 이전 단계로 돌아갑니다. [Cloud Manager 제품 프로필에 팀원 할당,](assign-profiles-cloud-manager.md) 을(를) 할당하는 방법에 대한 자세한 내용을 보려면 **비즈니스 소유자** 시스템 관리자에게 역할.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인하면 일반 랜딩 페이지가 표시됩니다.

**비즈니스 소유자** 역할이 있는 시스템 관리자로 성공적으로 로그인하여 **비즈니스 소유자** 역할이 있는 다른 사용자가 사용할 수 있도록 Cloud Manager를 초기화합니다. 확인 또는 메시지를 받지 못했습니다. 로그인하기만 하면 됩니다.

를 사용하여 시스템 관리자로 Cloud Manager에 로그인할 때까지 **비즈니스 소유자** 역할, 을(를) 가진 다른 사용자 **비즈니스 소유자** 역할은 Cloud Manager에서 프로그램을 만들 수 없습니다. 이 규칙은 올바른 역할이 할당된 경우에도 적용됩니다.

## Cloud Manager로 이동 {#navigate-cloud-manager}

을(를) 가진 사용자 **비즈니스 소유자** 역할 시작하기 위한 링크가 포함된 시작 이메일을 받습니다. 이 시작 이메일을 사용하여 Cloud Manager로 이동하려면 아래 단계를 따르십시오.

1. 시작 이메일에서 **시작**을 참조하십시오.
   ![이메일 예](/help/journey-onboarding/assets/get-started-email.png)

1. Cloud Manager의 **프로그램 및 제품** 페이지를 가리키도록 업데이트하는 중입니다.

   >[!TIP]
   >
   >`[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)`에서 Cloud Manager의 로그인 페이지로 직접 이동할 수도 있습니다. 나중에 참조할 수 있도록 이 페이지에 책갈피를 표시합니다.

1. Cloud Manager의 랜딩 페이지로 이동합니다.

또는 다음 단계에 따라 Adobe Experience Cloud 홈 페이지에서 Cloud Manager의 **프로그램 및 제품** 페이지로 이동할 수도 있습니다.

1. [Adobe Experience Cloud](https://experience.adobe.com)로 이동한 다음 Adobe ID를 사용하여 로그인합니다.

1. Adobe Experience Cloud 홈페이지에서 을(를) 선택합니다. **Experience Manager** AEM 홈 페이지를 엽니다.

   ![Experience Cloud 홈 페이지](/help/journey-onboarding/assets/setup-resources2.png)

1. 다음에서 **Cloud Manager** 타일, 선택 **시작**.

   ![AEM 홈 페이지](/help/journey-onboarding/assets/setup-resources3.png)

1. 성공적으로 로그온하면 Cloud Manager 랜딩 페이지로 이동합니다. 다음을 참조하십시오 [Cloud Manager 프로그램 보기](#viewing-programs) 을 참조하십시오.

Cloud Manager를 통해 프로그램 및 제품에 액세스하는 방법은 귀하에게 달려 있으며 Cloud Manager를 사용하는 방법이나 프로그램을 관리하는 방법에는 영향을 미치지 않습니다.

>[!NOTE]
>
>Cloud Manager에서 할당된 역할과 애플리케이션 상태에 따라 Cloud Manager 사용자 인터페이스를 사용하는 동안 표시되는 화면이 다릅니다.

## 프로그램 보기 {#viewing-programs}

Cloud Manager에 성공적으로 액세스하면 다음 섹션에 설명된 대로 프로그램 상태에 따라 표시되는 내용이 달라집니다.

### 프로그램이 없는 경우 {#no-programs}

조직에 프로그램이 없는 경우 랜딩 페이지에서 첫 번째 프로그램을 만들도록 지시합니다.

![프로그램 없음](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### 프로그램이 이미 있는 경우 {#programs-exist}

조직에 프로그램이 있는 경우 랜딩 페이지에 기존 프로그램이 표시되고 다른 프로그램을 추가할 수 있는 버튼도 제공됩니다.

![프로그램 있음](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### 프로그램이 존재하고 시스템 관리자인 경우 {#programs-exist-sysadmin}

조직에 프로그램이 있고 시스템 관리자인 경우 랜딩 페이지가 표시됩니다 **액세스 관리** 단추(함께 표시) **프로그램 추가** 옵션을 선택합니다.

![시스템 관리자 보기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## 사용자 역할 확인 {#verify-user-roles}

Cloud Manager에 성공적으로 로그인하면 **비즈니스 소유자** 제품 프로필이 할당되었는지 확인할 수 있습니다.

1. 창의 오른쪽 상단에서 프로필을 선택합니다.

   ![사용자 프로필](/help/journey-onboarding/assets/setup-resources5.png)

1. 사용자에게 할당된 역할을 표시하려면 을 선택합니다. **사용자 역할**.

   ![사용자 역할](/help/journey-onboarding/assets/setup-resources6.png)

1. 대화 상자에서 사용자에게 **비즈니스 소유자** 역할이 있는지 확인해야 합니다.

   ![사용자 역할 목록](/help/journey-onboarding/assets/setup-resources7.png)

Cloud Manager에 비즈니스 소유자로 로그인했습니다! **비즈니스 소유자** 역할이 할당되지 않은 경우 시스템 관리자에게 문의하십시오.

## 다음 단계 {#whats-next}

이제 시스템 관리자로 Cloud Manager에 액세스할 수 있으므로 첫 번째 프로그램을 만들 준비가 된 것입니다.

다음 문서를 검토하여 온보딩 여정 계속 [프로그램 만들기](create-program.md) 여기에서 방법을 배울 수 있습니다.

## 추가 리소스 {#additional-resources}

다음은 온보딩 여정의 콘텐츠를 넘어서고자 하는 경우 선택할 수 있는 추가 리소스입니다.

* [Cloud Manager 소개](/help/onboarding/cloud-manager-introduction.md) -
Cloud Manager, Cloud Manager 프로그램 및 환경에 대해 알아봅니다.
* [AEM as a Cloud Service 팀 및 제품 프로필](/help/onboarding/aem-cs-team-product-profiles.md) - AEM as a Cloud Service 팀 및 제품 프로필로 라이선스가 부여된 Adobe 솔루션에 대한 액세스 권한을 부여하고 제한하는 방법에 대해 알아봅니다.
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->
