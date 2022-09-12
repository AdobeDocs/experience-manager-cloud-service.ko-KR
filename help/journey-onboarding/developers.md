---
title: 개발자 및 배포 관리자 작업
description: 시스템 관리자가 필요한 클라우드 리소스를 설정한 후에는 개발자와 배포 관리자가 git에 액세스하여 애플리케이션을 개발하고 파이프라인을 사용하여 배포하는 방법을 알아봅니다.
feature: Onboarding
role: Admin, User, Developer
exl-id: f57a856b-0932-4e8f-be59-a19fe692e2ab
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 3%

---


# 개발자 및 배포 관리자 작업 {#developer-deployment-manager}

의 이 선택적 부분에서 [온보딩 여정,](overview.md) 개발자 및 배포 관리자가 git에 액세스하여 응용 프로그램을 개발하고 파이프라인을 사용하여 이 응용 프로그램을 배포하는 방법을 알아봅니다.

## 지금까지의 이야기 {#story-so-far}

온보딩 여정에 많이 오셨습니다! 축하합니다! 시스템 관리자가 필요한 클라우드 리소스를 설정하고 문서에서 액세스 권한을 부여하여 온보딩 여정을 완료했습니다 [AEM 제품 프로필 할당.](assign-profiles-aem.md)

이때 개발자와 배포 관리자는 AEM 사용자가 컨텐츠 만들기를 시작할 수 있는 동안 자신만의 애플리케이션을 만들 수 있습니다. 이러한 의미에서 온보딩이 완료되었으며 이제 이 문서가 예시될 새로운 AEM as a Cloud Service 시스템을 사용할 차례입니다.

## 대상자 {#audience}

따라서 이 문서는 **개발자** 및 **배포 관리자**.

시스템 관리자는 이러한 동일한 작업을 수행할 수도 있지만 일반적으로 이러한 역할은 다른 사용자가 보유합니다.

## 목표 {#objective}

이 문서는 시스템 관리자가 모든 사용자를 온보딩하고 필요한 클라우드 리소스를 만든 후 개발자 및 배포 관리자의 기본 작업을 보여주기 위한 온보딩 여정의 보조 자료입니다.

이 문서를 읽고 나면

* 개발자는 Cloud Manager git 리포지토리에 액세스하고 관리하는 방법을 이해합니다.
* 배포 관리자는 파이프라인을 설정하고 Cloud Manager에서 코드를 배포할 수 있습니다.

## 개발자 및 배포 관리자 {#roles}

시스템 관리자가 사용자를 만들고 클라우드 리소스를 설정하는 주요 온보딩 작업을 완료하면 일반적으로 시스템에 액세스하는 데 가장 많이 걱정하는 사용자는 개발자와 배포 관리자입니다. 이는 AEM as a Cloud Service 맨 위에 사용자 지정 애플리케이션을 빌드할 책임이 있는 사용자이기 때문입니다.

* **개발자** - 이 사용자는 AEM 사용자 지정 애플리케이션에 대한 코드를 관리할 Cloud Manager git 리포지토리에 액세스합니다.
* **배포 관리자** - 이 사용자는 Cloud Manager를 사용하여 Git 리포지토리에서 실행 중인 AEM 환경에 코드를 배포하는 파이프라인을 만들고 실행합니다.

조직의 요구 사항에 따라 동일한 사용자가 두 역할을 모두 가질 수 있습니다.

## 사전 요구 사항 {#prerequisites}

이 문서에 개발자 또는 배포 관리자로 설명된 작업을 시작하기 전에 시스템 관리자가 이 온보딩 여정의 모든 단계를 완료했는지 확인하십시오. 이것의 의미는 다음과 같습니다.

* 시스템 관리자가 각 제품 프로필에 개발자와 배포 관리자를 할당했습니다.
* 개발자에게는 추가로 를 할당해야 합니다. **AEM 사용자** 또는 **AEM 관리자** AEM도 사용하기 위한 제품 프로필입니다.
* 클라우드 리소스가 설정되었습니다.

## Git 액세스 {#accessing-git}

Cloud Manager의 셀프 서비스 git 계정 관리를 사용하여 Git 리포지토리에 액세스하고 관리할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 다음으로 이동 **파이프라인** 카드 **프로그램 개요** 페이지를 열고 **보고서 정보에 액세스** git 리포지토리에 액세스하고 관리하는 단추.

   ![환경 카드에서 보고서 정보 액세스 단추](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. 을(를) 클릭합니다. **보고서 정보 보기** 보려는 대화 상자를 여는 단추:

   * Cloud Manager git 저장소의 URL입니다.
   * Git 사용자 이름.
   * Git 암호이며, **암호 생성** 버튼을 클릭합니다.

   ![저장소 정보](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

이러한 자격 증명을 사용하여 사용자는 리포지토리의 로컬 복사본을 복제하고 해당 로컬 리포지토리를 변경할 수 있으며, 준비가 되면 모든 코드 변경 내용을 Cloud Manager의 원격 코드 리포지토리에 다시 적용할 수 있습니다.

## 파이프라인 설정 {#setup-pipeline}

개발자가 사용자 지정 코드를 Git 리포지토리에 추가하면 배포 관리자가 파이프라인을 만들고 실행하여 해당 코드를 AEM 환경에 배포할 수 있습니다.

다음 단계에 따라 첫 번째 비프로덕션 배포 파이프라인을 만듭니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 액세스 권한 **파이프라인** Cloud Manager 홈 화면에서 카드를 생성할 수 있습니다. 클릭 **+추가** 을(를) 선택합니다. **비프로덕션 파이프라인 추가**.

   ![비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. 설정 **구성** 의 탭 **비프로덕션 파이프라인 추가** 대화 상자에서 추가할 비프로덕션 파이프라인의 유형을 선택합니다. 이 예제에서는 **배포 파이프라인**.

   ![비프로덕션 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. 다음을 제공합니다. **비프로덕션 파이프라인 이름** 를 참조하여 다음 추가 정보와 함께 파이프라인을 식별합니다.

1. 대상 **배포 트리거** 선택 **수동** 파이프라인을 시작할 때만 실행되도록 합니다.

1. 클릭 **계속**.

1. 설정 **소스 코드** 의 탭 **비프로덕션 파이프라인 추가** 대화 상자에서 파이프라인이 처리해야 하는 코드 유형을 선택해야 합니다. 이 예제에서는 **전체 스택 코드**.

1. 설정 **소스 코드** 탭에서 다음 옵션을 정의해야 합니다.

   * **적합한 배포 환경** - 파이프라인을 배포할 환경을 선택해야 합니다.
   * **저장소** - 이 옵션은 파이프라인이 코드를 검색해야 하는 Git 리포지토리를 정의합니다.
   * **Git 분기** - 이 옵션은 선택한 파이프라인의 어느 분기에서 코드를 검색해야 하는지를 정의합니다.
      * 분기 이름의 처음 몇 문자를 입력하고 이 필드의 자동 완성 기능이 선택한 데 도움이 되는 일치하는 분기를 찾습니다.

   ![전체 스택 파이프라인](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. **저장**&#x200B;을 클릭합니다.

이제 첫 번째 파이프라인을 생성했습니다! 이제 배포 관리자 역할을 가진 사용자가 Cloud Manager UI에서 파이프라인을 시작할 수 있습니다.

##  배포 {#deploy}

개발자는 사용자 지정 코드를 Git 저장소에 추가했고 해당 코드를 배포하기 위해 파이프라인을 만들었으므로 이제 해당 코드를 git에서 사용자 환경으로 실제로 이동해야 합니다.

![Cloud Manager의 파이프라인 카드](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지를 클릭하고 이전 섹션에서 만든 파이프라인 옆에 있는 줄임표 단추를 클릭하고 를 선택합니다 **실행** 메뉴 아래의 제품에서 사용할 수 있습니다.

1. 파이프라인 실행이 시작되고 로 표시됩니다 **상태** 열.

생략 부호 단추를 다시 클릭하고 을 선택하여 실행 세부 사항을 볼 수 있습니다 **세부 사항 보기**.

축하합니다! 이제 Git 리포지토리의 코드를 비프로덕션 환경에 배포했습니다!

## 다음은 무엇입니까? {#whats-next}

이 문서를 읽었으므로 다음 작업을 수행해야 합니다.

* 개발자는 Cloud Manager git 리포지토리에 액세스하고 관리하는 방법을 이해합니다.
* 배포 관리자는 파이프라인을 설정하고 Cloud Manager에서 코드를 배포할 수 있습니다.

Cloud Manager에 대한 작업 지식 뿐만 아니라 작업 환경, 저장소 및 파이프라인에 대한 지식을 사용하여 개발자 또는 배포 관리자로 실행 중인 문제를 해결했습니다. 그러나 AEM as a Cloud Service의 강력한 CI/CD 도구에 대해 자세히 알아보십시오. 다음을 확인하십시오 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

컨텐츠 작성자가 AEM as a Cloud Service에 액세스하고 사용하는 방법에 관심이 있는 경우 온보딩 여정의 최종 부분으로 계속 진행합니다. [AEM 사용자 작업.](aem-users.md)

>[!TIP]
>
>이제 온보딩되므로 [AEM 참조 데모 추가 기능을 쉽게 추가하는 방법을 알아봅니다.](/help/journey-sites/demos-add-on/overview.md) 최소한의 AEM 구성으로 샌드박스 환경을 테스트하고 모범 사례를 기반으로 한 풍부한 예를 사용하여 AEM의 강력한 기능을 테스트할 수 있습니다.

## 추가 리소스 {#additional-resources}

* [저장소 액세스](/help/implementing/cloud-manager/managing-code/accessing-repos.md) - Cloud Manager의 셀프 서비스 git 계정 관리를 사용하여 Git 리포지토리에 액세스하고 관리하는 방법을 알아봅니다.
* [Cloud Manager에서 git 사용](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) - Cloud Manager의 Git 저장소를 사용하는 방법 및 Cloud Manager와 자체 온-프레미스 고객 관리 Git 리포지토리를 통합하는 방법을 알아봅니다.
* [로컬 개발 환경 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) - 이 자습서에서는 AEM as a Cloud Service SDK를 사용하여 AEM(Adobe Experience Manager)용 로컬 개발 환경을 설정하는 방법을 안내합니다.
* [AEM Sites 시작하기 - WKND 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) - 이 여러 부분으로 된 튜토리얼은 AEM(Adobe Experience Manager)을 처음 사용하는 개발자를 위해 설계되었습니다. 이 자습서에서는 가상 라이프스타일 브랜드인 WKND에 대한 AEM 사이트 구현을 안내합니다. 이 자습서에서는 프로젝트 설정, 코어 구성 요소, 편집 가능한 템플릿, 클라이언트측 라이브러리 및 Adobe Experience Manager Sites을 사용한 구성 요소 개발과 같은 기본 주제를 다룹니다.
* [React를 사용하여 AEM에서 SPA 시작하기](/help/implementing/developing/hybrid/getting-started-react.md) - 이 문서에서는 샘플 SPA 애플리케이션을 제공하며 이 애플리케이션을 구성하는 방법을 설명하고 React 프레임워크를 사용하여 신속하게 자체 SPA을 사용하여 실행 및 실행할 수 있도록 합니다.
* [angular을 사용하여 AEM에서 SPA 시작하기](/help/implementing/developing/hybrid/getting-started-angular.md) - 이 문서에서는 샘플 SPA 애플리케이션을 제공하며 이 애플리케이션을 어떻게 구성하는지에 대해 설명하고 Angular 프레임워크을 사용하여 고유한 SPA을 빠르게 실행 및 실행할 수 있도록 해줍니다.
* [헤드리스 개발자 여정](/help/journey-headless/developer/overview.md) - AEM을 사용하여 헤드리스 애플리케이션을 개발하는 안내식 교육 과정을 살펴보려면 여기에서 시작하십시오.
