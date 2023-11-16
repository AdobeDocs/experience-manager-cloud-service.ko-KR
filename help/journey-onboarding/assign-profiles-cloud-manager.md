---
title: Cloud Manager 제품 프로필에 팀원 할당
description: 이 페이지를 따라 Cloud Manager 제품 프로필에 팀원을 할당하는 방법을 알아봅니다.
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1528'
ht-degree: 94%

---


# Cloud Manager 제품 프로필에 팀원 할당 {#assign-team-members}

의 이 부분에서 [온보딩 여정,](overview.md) cloud Manager 제품 프로필에 팀원을 할당하는 방법을 배웁니다.

## 목표 {#objective}

이 여정의 이전 단계인 [Admin Console 액세스](admin-console.md)에서 Admin Console에 로그인하고 시스템 관리자의 권한을 확인하는 방법을 배웠습니다. 이제 팀원이 Cloud Manager에 액세스하도록 허용할 준비가 되었습니다. 제품 프로필을 할당하면 됩니다.

사용자에게 Adobe 솔루션에 대한 액세스 권한을 부여할 때 반드시 전체 액세스 권한을 부여할 필요는 없습니다. 제품 프로필을 사용하면 각 솔루션이 고유한 사용자 권한 집합을 가질 수 있습니다. Admin Console을 사용하여 제품 프로필을 할당합니다.

첫 번째 단계는 사용자에게 Cloud Manager에 대한 액세스 권한을 부여하는 것입니다. Cloud Manager는 철저한 테스트와 최고의 코드 품질을 보장하여 탁월한 경험을 제공할 수 있도록 기업 개발 설정 및 특수 목적으로 구축된 CI/CD 파이프라인을 지원합니다.

이 문서를 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* 제품 프로필이 무엇인지 이해합니다.
* Cloud Manager가 무엇인지 이해합니다.
* Cloud Manager의 세 가지 중요한 제품 프로필인 **비즈니스 소유자**, **배포 관리자**, and **개발자**&#x200B;를 알게 됩니다.
* Cloud Manager 제품 프로필에 팀원을 할당할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

제품 프로필에 팀원을 할당하려면 다음을 포함하여 AEM에 as a Cloud Service으로 액세스해야 하는 팀원에 대한 세부 정보가 있어야 합니다.

* 이름
* 이메일 주소
* 역할 및 책임

>[!TIP]
>
>Adobe는 온보딩을 위해 관리자, 개발자 및 콘텐츠 작성자와 같이 즉각적인 작업에 참여할 사용자를 초기에 추가할 것을 권장합니다.
>
>모든 사용자를 추가하지 않고 온보딩 프로세스를 계속할 수 있습니다. 온보딩을 완료한 후 사용자를 추가할 수 있습니다.

## 제품 프로필 {#product-profiles}

사용자에게 Adobe 솔루션에 대한 액세스 권한을 부여할 때 반드시 전체 액세스 권한을 부여할 필요는 없습니다. 제품 프로필을 사용하면 각 솔루션이 Admin Console을 사용하여 설정한 고유한 사용자 권한 집합을 가질 수 있습니다.

예를 들어 이 과정의 뒷부분에서는 Admin Console을 사용하여 AEM 관리자 및 AEM 작성자에 대한 제품 프로필을 할당하여 사용자에게 AEM 솔루션에 대한 액세스 권한을 부여합니다.

그러나 다음 단계는 팀원이 먼저 Cloud Manager에 액세스할 수 있도록 제품 프로필을 부여하는 것입니다.

## Cloud Manager {#cloud-manager}

시스템 관리자로서 성공적인 AEM as a Cloud Service 프로젝트는 AEM을 사용하여 놀라운 콘텐츠를 생성할 뿐만 아니라 AEM 콘텐츠를 제공하기 위한 자체 사용자 정의 코드 및 애플리케이션의 개발 및 배포에 달려 있다는 것을 알고 있습니다.

Cloud Manager는 AEM as a Cloud Service의 필수적인 부분이며 코드 배포를 위한 CI/CD 파이프라인을 관리하고, 코드 저장소를 관리하며, 환경을 관리하는 데 사용됩니다.

팀이 다른 작업을 수행하려면 먼저 필요한 제품 프로필을 부여하여 Cloud Manager에 온보딩해야 합니다. 다음 단계에서는 Admin Console을 사용하여 Cloud Manager 제품 프로필을 찾는 위치와 해당 프로필을 팀원에게 할당하는 방법을 보여 줍니다.

## Cloud Manager 제품 프로필 검토 {#review-product-profiles}

Admin Console을 사용하여 Cloud Manager 프로필 목록을 볼 수 있습니다.

1. [adminconsole.adobe.com](https://adminconsole.adobe.com/)에서 Adobe Admin Console에 로그인하고 **개요** 페이지의 **제품 및 서비스** 카드에서 **Adobe Experience Manager as a Cloud Service**&#x200B;를 선택합니다.

   ![제품으로서의 AEM](/help/journey-onboarding/assets/assign-team1.png)

1. 모든 인스턴스 목록에서 **Cloud Manager** 인스턴스로 이동합니다.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. 사전 구성된 Cloud Manager 제품 프로필 목록을 볼 수 있습니다.

   ![제품 프로필](/help/journey-onboarding/assets/assign-team3.png)

초기 온보딩 프로세스의 일부로 할당할 가장 중요한 프로필은 다음과 같습니다.

* **비즈니스 소유자** - 이러한 사용자는 다양한 프로그램을 관리합니다.
* **배포 관리자** - 이러한 사용자는 저장소에서 실행 중인 AEM 환경으로 코드를 배포합니다.
* **개발자** - 이러한 사용자는 사용자 정의 AEM 애플리케이션을 개발하고 저장소에 코드를 커밋합니다.

이러한 역할이 무엇이며 어떤 역할을 하는지 알게 되었으므로 이제 팀원 목록을 검토하여 누가 어떤 프로필이 필요한지 결정합니다. 사용자는 팀에서 여러 역할을 가질 수 있으므로 여러 개의 프로필이 필요합니다.

## 비즈니스 소유자 제품 프로필 할당 {#assign-business-owner}

이제 사용자를 추가하고 **비즈니스 소유자** 제품 프로필에 할당할 준비가 되었습니다.

1. Cloud Manager 프로그램을 관리해야 하는 사용자를 식별합니다. 이 사용자가 **비즈니스 소유자**&#x200B;가 됩니다.

1. `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)`에서 Admin Console에 로그온하고 **개요** 페이지의 **제품 및 서비스** 카드에서 **Adobe Experience Manager as a Cloud Service** 제품을 선택합니다.

   ![제품 및 서비스](/help/journey-onboarding/assets/assign-team1.png)

1. 상단 탐색에서 **사용자** 탭을 선택한 다음 **사용자 추가**&#x200B;를 선택합니다.

   ![사용자 추가](/help/journey-onboarding/assets/assign-team4.png)

1. **팀에 사용자 추가** 대화 상자에서 추가하려는 사용자의 이메일 ID를 입력합니다.

   * 팀원의 연합 ID가 아직 설정되지 않은 경우 **ID 유형**&#x200B;으로 **Adobe ID**&#x200B;를 선택합니다.

   ![사용자 세부 정보 추가](/help/journey-onboarding/assets/assign-team5.png)

1. **제품 또는 사용자 그룹 선택** 제목 아래에 있는 더하기 버튼을 클릭하여 제품 선택을 시작하고 **Adobe Experience Manager as a Cloud Service**&#x200B;를 선택하고 **비즈니스 소유자** 제품 프로필을 사용자에게 할당합니다.

   * 사용자가 Cloud Manager에 액세스할 수 있도록 모든 사용자를 하나 이상의 제품 프로필에 할당합니다.
   * 자신을 **비즈니스 소유자** 역할에 시스템 관리자로 할당하는 것을 잊지 마십시오.

   ![사용자 할당](/help/journey-onboarding/assets/assign-team6.png)

1. **저장**&#x200B;을 클릭하면 추가한 사용자에게 시작 이메일이 전송됩니다. 초대된 사용자는 시작 이메일의 링크를 클릭하고 Adobe ID를 사용하여 로그인함으로써 Cloud Manager에 액세스할 수 있습니다.

1. 팀의 사용자에 대해 이 단계를 반복합니다.

**비즈니스 소유자**&#x200B;가 할당되었으므로 이제 Cloud Manager에 액세스할 수 있습니다. 자신을 **비즈니스 소유자** 프로필에 시스템 관리자로 지정하는 것을 잊지 마십시오.

## 배포 관리자 제품 프로필 할당 {#assign-deployment-manager}

1. 코드를 배포해야 하는 사용자를 식별합니다.

1. `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)`에서 Admin Console에 로그인하고 **개요** 페이지의 **제품 및 서비스** 카드에서 **Adobe Experience Manager as a Cloud Service** 제품을 선택합니다.

   ![제품 및 서비스](/help/journey-onboarding/assets/assign-team1.png)

1. 상단 탐색에서 **사용자** 탭을 선택한 다음 **사용자 추가**&#x200B;를 선택합니다.

   ![사용자 추가](/help/journey-onboarding/assets/assign-team4.png)

1. **팀에 사용자 추가** 대화 상자에서 추가하려는 사용자의 이메일 ID를 입력합니다.

   * 팀원의 연합 ID가 아직 설정되지 않은 경우 **ID 유형**&#x200B;으로 **Adobe ID**&#x200B;를 선택합니다.

   ![ID 입력](/help/journey-onboarding/assets/assign-team5.png)

1. **제품 또는 사용자 그룹 선택** 제목 아래에 있는 더하기 버튼을 클릭하여 제품 선택을 시작하고 **Adobe Experience Manager as a Cloud Service**&#x200B;를 선택하고 **배포 관리자** 제품 프로필을 사용자에게 할당합니다.

   ![프로필 할당](/help/journey-onboarding/assets/assign-team6.png)

**배포 관리자**&#x200B;가 할당되었으므로 이제 Cloud Manager에 액세스할 수 있습니다. 향후 책임에 따라 자신을 **배포 관리자** 프로필에 시스템 관리자로 할당해야 할 수도 있고 할당하지 않을 수도 있습니다.

## 개발자 제품 프로필 할당 {#assign-developer}

1. AEM 애플리케이션을 개발하고 코드를 관리해야 하는 사용자를 식별합니다.

1. `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)`에서 Admin Console에 로그인하고 **개요** 페이지의 **제품 및 서비스** 카드에서 **Adobe Experience Manager as a Cloud Service** 제품을 선택합니다.

   ![제품 및 서비스](/help/journey-onboarding/assets/assign-team1.png)

1. 상단 탐색에서 **사용자** 탭을 선택한 다음 **사용자 추가**&#x200B;를 선택합니다.

   ![사용자 추가](/help/journey-onboarding/assets/assign-team4.png)

1. **팀에 사용자 추가** 대화 상자에서 추가하려는 사용자의 이메일 ID를 입력합니다.

   * 팀원의 연합 ID가 아직 설정되지 않은 경우 **ID 유형**&#x200B;으로 **Adobe ID**&#x200B;를 선택합니다.

   ![사용자 ID 추가](/help/journey-onboarding/assets/assign-team5.png)

1. **제품 또는 사용자 그룹 선택** 제목 아래에 있는 더하기 버튼을 클릭하여 제품 선택을 시작하고 **Adobe Experience Manager as a Cloud Service**&#x200B;를 선택하고 **개발자** 제품 프로필을 사용자에게 할당합니다.

   ![프로필 할당](/help/journey-onboarding/assets/assign-team6.png)

**개발자**&#x200B;가 할당되었으므로 이제 Cloud Manager에 액세스할 수 있습니다. 향후 책임에 따라 자신을 **개발자** 프로필에 시스템 관리자로 할당해야 할 수도 있고 할당하지 않을 수도 있습니다.

## 다음 단계 {#whats-next}

축하합니다! 새로 구성된 Cloud Manager 팀(**비즈니스 소유자** 프로필에 할당된 자신 포함)이 설정되었습니다. 이제 한 단계만 실행하면 **비즈니스 소유자** 역할로 Cloud Manager에 로그인하고 클라우드 리소스를 생성할 수 있습니다.

이 온보딩 여정 부분에서는 Admin Console의 프로필에 팀원을 할당하는 방법을 배웠습니다. 이제 다음과 같은 작업을 수행할 수 있습니다.

* 제품 프로필이 무엇인지 이해합니다.
* Cloud Manager가 무엇인지 이해합니다.
* Cloud Manager의 세 가지 중요한 제품 프로필인 **비즈니스 소유자**, **배포 관리자**, and **개발자**&#x200B;를 알게 됩니다.
* Cloud Manager 제품 프로필에 팀원을 할당할 수 있습니다.

이제 다음 문서를 검토하여 온보딩 여정을 계속할 준비가 되었습니다 [Cloud Manager 액세스,](cloud-manager.md) 여기에서 Cloud Manager에 액세스하고 프로젝트 리소스를 만드는 방법을 배울 수 있습니다.

## 추가 리소스 {#additional-resources}

앞에서 설명한 대로 온보딩 여정을 계속하는 것이 좋습니다. 이 여정의 특정 주제에 대해 자세히 알아보려면 다음과 같은 추가 리소스를 참조하십시오.

* [Cloud Manager 소개](/help/onboarding/cloud-manager-introduction.md) - Cloud Manager, Cloud Manager 프로그램 및 환경에 대해 알아봅니다.
* [Cloud Manager 제품 프로필](/help/onboarding/aem-cs-team-product-profiles.md) - AEM as a Cloud Service 팀 및 제품 프로필에 대해 알아봅니다.
* [Adobe Admin Console의 ID 유형](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/identity.ug.html) - Adobe의 ID 관리 시스템을 사용하여 관리자는 애플리케이션 및 서비스에 대한 사용자 이용 권한을 만들고 관리할 수 있습니다. Adobe는 사용자를 인증하고 권한을 부여하는 데 사용할 수 있는 이들 ID 유형 또는 계정을 제공합니다.

