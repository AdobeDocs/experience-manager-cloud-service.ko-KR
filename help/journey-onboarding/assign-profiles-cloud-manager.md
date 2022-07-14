---
title: Cloud Manager 제품 프로필에 팀 구성원 할당
description: 팀 구성원을 Cloud Manager 제품 프로필에 할당하는 방법을 알려면 이 페이지를 따르십시오
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 2%

---


# Cloud Manager 제품 프로필에 팀 멤버 할당 {#assign-team-members}

의 이 부분에서 [온보딩 여정,](overview.md) 팀원을 Cloud Manager 제품 프로필에 할당하는 방법을 알아봅니다.

## 목표 {#objective}

이 여정의 이전 단계에서 [Admin Console 액세스,](admin-console.md) 이제 Admin Console에 로그인하고 시스템 관리자로서의 권한을 확인했습니다. 이제 팀 구성원이 Cloud Manager에 액세스할 수 있도록 할 준비가 되었습니다. 제품 프로필을 할당하여 이렇게 합니다.

사용자에게 Adobe 솔루션에 대한 액세스 권한을 부여할 때 반드시 전체 액세스 권한을 부여할 필요는 없습니다. 제품 프로필을 사용하면 각 솔루션에 고유한 사용자 권한 세트를 가질 수 있습니다. Admin Console을 사용하여 제품 프로필을 지정합니다.

첫 번째 단계는 사용자에게 Cloud Manager에 대한 액세스 권한을 부여하는 것입니다. Cloud Manager는 탁월한 경험을 제공하기 위해 철저한 테스트와 최고 코드 품질을 보장하도록 설계된 엔터프라이즈 개발 설정과 용도에 맞는 CI/CD 파이프라인을 지원합니다.

이 문서를 읽고 나면

* 제품 프로필을 파악합니다.
* Cloud Manager 정의 이해
* 다음 세 가지 중요한 Cloud Manager 제품 프로필을 알고 있습니다. **비즈니스 소유자**, **배포 관리자**, 및 **개발자**.
* 팀 구성원을 Cloud Manager 제품 프로필에 할당할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

제품 프로필에 팀 구성원을 할당하려면 다음과 같이 AEM as a Cloud Service에 액세스해야 하는 팀 구성원에 대한 세부 사항이 있어야 합니다.

* 이름
* 이메일 주소
* 역할 및 책임

>[!TIP]
>
>온보딩을 위해 관리자는 처음에 관리자, 개발자 및 컨텐츠 작성자와 같은 즉각적인 작업에 참여할 사용자를 추가할 것을 권장합니다.
>
>모든 사용자를 추가하지 않고 온보딩 프로세스를 계속할 수 있습니다. 온보딩을 완료하면 추가 사용자를 추가할 수 있습니다.

## 제품 프로필 {#product-profiles}

사용자에게 Adobe 솔루션에 대한 액세스 권한을 부여할 때 반드시 전체 액세스 권한을 부여할 필요는 없습니다. 제품 프로필을 사용하면 각 솔루션에 Admin Console을 사용하여 설정된 고유한 사용자 권한 세트를 가질 수 있습니다.

예를 들어 이 여정의 후반부에 Admin Console을 사용하여 AEM 관리자 및 AEM 작성자를 위한 제품 프로필을 할당하여 사용자에게 AEM 솔루션에 대한 액세스 권한을 부여합니다.

하지만 다음 단계는 팀 구성원이 먼저 Cloud Manager에 액세스할 수 있도록 제품 프로필을 부여하는 것입니다.

## Cloud Manager {#cloud-manager}

시스템 관리자로서 성공적인 AEM as a Cloud Service 프로젝트는 AEM을 사용하여 멋진 컨텐츠를 만드는 것뿐만 아니라 AEM 컨텐츠를 전달하는 사용자 지정 코드 및 애플리케이션의 개발 및 배포에 달려 있습니다.

Cloud Manager는 AEM as a Cloud Service의 필수적인 부분이며, 코드 배포를 위한 CI/CD 파이프라인을 관리하고 코드 저장소를 관리하며 환경을 관리하는 데 사용됩니다.

팀이 다른 작업을 수행하기 전에 필요한 제품 프로필을 부여하여 Cloud Manager에 온보딩해야 합니다. 다음 단계는 Admin Console을 사용하여 Cloud Manager 제품 프로필을 찾을 위치와 팀 구성원에게 할당하는 방법을 보여줍니다.

## Cloud Manager 제품 프로필 검토 {#review-product-profiles}

Admin Console을 사용하면 Cloud Manager 프로필 목록을 볼 수 있습니다.

1. Adobe Admin Console에 로그인 위치 [adminconsole.adobe.com](https://adminconsole.adobe.com/) 그리고 **개요** 페이지를 선택하고 **Adobe Experience Manager as a Cloud Service** 에서 **제품 및 서비스** 카드.

   ![AEM as a product](/help/journey-onboarding/assets/assign-team1.png)

1. 로 이동합니다 **Cloud Manager** 모든 인스턴스 목록에서 인스턴스를 생성합니다.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. 사전 구성된 Cloud Manager 제품 프로필 목록이 표시됩니다.

   ![제품 프로필](/help/journey-onboarding/assets/assign-team3.png)

초기 온보딩 프로세스의 일부로 할당해야 하는 가장 중요한 프로필은 다음과 같습니다.

* **비즈니스 소유자** - 이 사용자들은 다양한 프로그램을 관리합니다.
* **배포 관리자** - 이 사용자는 리포지토리에서 실행 중인 AEM 환경에 코드를 배포합니다.
* **개발자** - 이 사용자는 사용자 지정 AEM 애플리케이션을 개발하고 저장소에 코드를 커밋합니다.

이러한 역할이 무엇이며 어떻게 작동하는지 파악하려면 팀 구성원 목록을 검토하여 어떤 프로필이 필요한지 결정해야 합니다. 사용자는 자신의 팀에서 여러 역할을 가질 수 있으며 종종 여러 프로필이 필요하기 때문입니다.

## 비즈니스 소유자 제품 프로필 지정 {#assign-business-owner}

이제 사용자를 추가하고 이 사용자를 **비즈니스 소유자** 제품 프로필 .

1. Cloud Manager 프로그램을 관리해야 하는 사용자를 식별합니다. 이게 바로 **비즈니스 소유자**.

1. Admin Console에 로그인합니다. `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` 그리고 **개요** 페이지를 선택하고 **Adobe Experience Manager as a Cloud Service** product from **제품 및 서비스** 카드.

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

사용자 **비즈니스 소유자**&#x200B;이 할당되어 이제 Cloud Manager에 액세스할 수 있습니다. 시스템 관리자로 자신을 **비즈니스 소유자** 프로필 참조.

## 배포 관리자 제품 프로필 할당 {#assign-deployment-manager}

1. 코드를 배포해야 하는 사용자를 식별합니다.

1. Admin Console에 로그인합니다. `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` 그리고 **개요** 페이지 선택 **Adobe Experience Manager as a Cloud Service** 제품에서 **제품 및 서비스** 카드.

   ![제품 및 서비스](/help/journey-onboarding/assets/assign-team1.png)

1. 을(를) 선택합니다 **사용자** 위쪽 탐색에서 tab 키를 누른 다음 을 선택합니다 **사용자 추가**.

   ![사용자 추가](/help/journey-onboarding/assets/assign-team4.png)

1. 에서 **팀에 사용자 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다.

   * 팀 구성원의 페더레이션 ID를 아직 설정하지 않은 경우 을 선택합니다 **Adobe ID** 대상 **ID 유형**.

   ![ID 입력](/help/journey-onboarding/assets/assign-team5.png)

1. 아래의 더하기 단추를 클릭합니다. **제품 또는 사용자 그룹 선택** 제품 선택을 시작하고 을(를) 선택합니다. **Adobe Experience Manager as a Cloud Service** 및 할당 **배포 관리자** 제품 프로필을 사용자 지정 합니다.

   ![프로필 할당](/help/journey-onboarding/assets/assign-team6.png)

사용자 **배포 관리자**&#x200B;이 할당되어 이제 Cloud Manager에 액세스할 수 있습니다. 사용자의 향후 권한에 따라, 시스템 관리자로 자신을 **배포 관리자** 프로필 참조.

## 개발자 제품 프로필 할당 {#assign-developer}

1. AEM 애플리케이션을 개발하고 코드를 관리해야 하는 사용자를 식별합니다.

1. Admin Console에 로그인합니다. `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` 그리고 **개요** 페이지 선택 **Adobe Experience Manager as a Cloud Service** 제품에서 **제품 및 서비스** 카드.

   ![제품 및 서비스](/help/journey-onboarding/assets/assign-team1.png)

1. 을(를) 선택합니다 **사용자** 위쪽 탐색에서 tab 키를 누른 다음 을 선택합니다 **사용자 추가**.

   ![사용자 추가](/help/journey-onboarding/assets/assign-team4.png)

1. in **팀에 사용자 추가** 대화 상자에서 추가할 사용자의 이메일 ID를 입력합니다.

   * 팀 구성원의 페더레이션 ID를 아직 설정하지 않은 경우 을 선택합니다 **Adobe ID** 대상 **ID 유형**.

   ![사용자 ID 추가](/help/journey-onboarding/assets/assign-team5.png)

1. 아래의 더하기 단추를 클릭합니다. **제품 또는 사용자 그룹 선택** 제품 선택을 시작하고 을(를) 선택합니다. **Adobe Experience Manager as a Cloud Service** 및 할당 **개발자** 제품 프로필을 사용자 지정 합니다.

   ![프로필 할당](/help/journey-onboarding/assets/assign-team6.png).

사용자 **개발자**&#x200B;이 할당되어 이제 Cloud Manager에 액세스할 수 있습니다. 사용자의 향후 권한에 따라, 시스템 관리자로 자신을 **개발자** 프로필 참조.

## 다음은 무엇입니까? {#whats-next}

축하합니다! 새로 구성된 Cloud Manager 팀(자신에게 지정된 팀 포함) **비즈니스 소유자** 프로필)이 설정되었습니다. 의 역할에서 **비즈니스 소유자**&#x200B;이제 Cloud Manager에 로그인하고 클라우드 리소스를 만들 수 있도록 한 단계 더 떨어져 있습니다.

온보딩 여정의 이 부분에서 Admin Console의 프로필에 팀 구성원을 지정하는 방법에 대해 학습했습니다. 이제

* 제품 프로필을 파악합니다.
* Cloud Manager 정의 이해
* 다음 세 가지 중요한 Cloud Manager 제품 프로필을 알고 있습니다. **비즈니스 소유자**, **배포 관리자**, 및 **개발자**.
* 팀 구성원을 Cloud Manager 제품 프로필에 할당할 수 있습니다.

이제 다음 번 문서를 검토하여 온보딩 여정을 계속할 준비가 되었습니다 [Cloud Manager에 액세스,](cloud-manager.md) 여기서 Cloud Manager에 액세스하고 프로젝트 리소스를 만드는 방법을 알아봅니다.

## 추가 리소스 {#additional-resources}

앞에서 설명한 대로 온보딩 여정을 계속 사용하는 것이 좋습니다. 이 여정에서 특정 주제를 자세히 살펴보려면 이러한 추가 리소스를 참조하십시오.

* [Cloud Manager 소개](/help/onboarding/cloud-manager-introduction.md) - Cloud Manager, Cloud Manager 프로그램 및 환경에 대해 알아봅니다.
* [Cloud Manager 제품 프로필](/help/onboarding/aem-cs-team-product-profiles.md) - AEM as a Cloud Service 팀 및 제품 프로필에 대해 알아봅니다.
* [Adobe Admin Console의 ID 유형](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/identity.ug.html) - Adobe의 id 관리 시스템은 관리자가 애플리케이션 및 서비스에 대한 사용자 액세스를 만들고 관리하는 데 도움이 됩니다. Adobe은 사용자를 인증하고 인증하는 이러한 ID 유형 또는 계정을 제공합니다.

