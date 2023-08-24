---
title: 개발자 및 배포 관리자 작업
description: 시스템 관리자가 필요한 클라우드 리소스를 설정한 후 개발자와 배포 관리자가 git에 액세스하여 애플리케이션을 개발하고 파이프라인을 사용하여 배포하는 방법을 알아봅니다.
feature: Onboarding
role: Admin, User, Developer
exl-id: f57a856b-0932-4e8f-be59-a19fe692e2ab
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: ht
source-wordcount: '1415'
ht-degree: 100%

---


# 개발자 및 배포 관리자 작업 {#developer-deployment-manager}

[온보딩 여정](overview.md)의 이 선택적 부분에서는 개발자와 배포 관리자가 git에 액세스하여 애플리케이션을 개발하고 파이프라인을 사용하여 배포하는 방법을 배웁니다.

## 지금까지의 스토리 {#story-so-far}

온보딩 여정의 먼 길을 진행하시느라 수고하셨습니다. 축하합니다! 시스템 관리자가 [AEM 제품 프로필](assign-profiles-aem.md) 할당 문서를 통해 필요한 클라우드 리소스를 설정하고 액세스 권한을 부여하는 온보딩 여정을 완료했습니다.

이 시점에서 개발자와 배포 관리자는 고유한 애플리케이션 만들기를 시작할 수 있고 AEM 사용자는 콘텐츠 만들기를 시작할 수 있습니다. 이러한 의미에서 온보딩이 완료되었으며 이제 이 문서에서 설명하는 새 AEM as a Cloud Service 시스템을 사용할 수 있습니다.

## 대상자 {#audience}

이 문서는 **개발자** 및 **배포 관리자**&#x200B;의 관점에서 작성되었습니다.

시스템 관리자도 이와 동일한 작업을 수행할 수 있지만 일반적으로 이러한 역할은 다른 사용자가 담당합니다.

## 목표 {#objective}

이 문서는 시스템 관리자가 모든 사용자를 온보딩하고 필요한 클라우드 리소스를 생성한 후 개발자 및 배포 관리자의 기본 작업을 보여 주기 위한 온보딩 프로세스의 보충 자료입니다.

이 문서를 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* 개발자로서 Cloud Manager git 저장소에 액세스하고 관리하는 방법을 이해할 수 있습니다.
* 배포 관리자로서 파이프라인을 설정하고 Cloud Manager에서 코드를 배포할 수 있습니다.

## 개발자 및 배포 관리자 {#roles}

시스템 관리자가 사용자 생성 및 클라우드 리소스 설정의 주요 온보딩 작업을 완료한 후 일반적으로 시스템에 대한 액세스가 가장 필요한 사용자는 개발자와 배포 관리자입니다. 이는 AEM as a Cloud Service를 기반으로 사용자 정의 애플리케이션을 구축하는 책임이 있는 사용자이기 때문입니다.

* **개발자** - Cloud Manager git 저장소에 액세스하여 AEM 사용자 정의 애플리케이션에 대한 코드를 관리할 수 있습니다.
* **배포 관리자** - Cloud Manager를 사용하여 git 저장소에서 실행 중인 AEM 환경으로 코드를 배포하는 파이프라인을 만들고 실행합니다.

조직의 요구 사항에 따라 동일한 사용자가 두 역할을 모두 수행할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

개발자 또는 배포 관리자로서 이 문서에 설명된 작업을 시작하기 전에 시스템 관리자가 이 온보딩 여정의 모든 단계를 완료했는지 확인하십시오. 이 의미는 다음과 같습니다.

* 시스템 관리자가 개발자 및 배포 관리자를 해당 제품 프로필에 할당했습니다.
* 개발자도 AEM을 사용하게 하려면 **AEM 사용자** 또는 **AEM 관리자** 제품 프로필에 추가로 할당해야 합니다.
* 클라우드 리소스가 설정되었습니다.

## git 액세스 {#accessing-git}

Cloud Manager에서 셀프서비스 git 계정 관리를 사용하여 git 저장소에 액세스하고 관리할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 **저장소 정보 액세스** 버튼을 찾아 git 저장소에 액세스하고 관리합니다.

   ![환경 카드의 저장소 정보 액세스 버튼](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. **저장소 정보 보기** 버튼을 클릭하여 다음 정보가 표시되는 대화 상자를 엽니다.

   * Cloud Manager git 저장소의 URL
   * git 사용자 이름
   * git 암호. 이 값은 **암호 생성** 버튼을 클릭할 때 표시됩니다.

   ![저장소 정보](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

사용자는 이러한 자격 증명을 사용하여 저장소의 로컬 복사본을 복제하고 해당 로컬 저장소를 변경할 수 있으며 준비가 되면 Cloud Manager의 원격 코드 저장소에 코드 변경 사항을 다시 커밋할 수 있습니다.

## 파이프라인 설정 {#setup-pipeline}

개발자가 git 저장소에 사용자 정의 코드를 추가하면 배포 관리자가 파이프라인을 만들고 실행하여 해당 코드를 AEM 환경에 배포할 수 있습니다.

다음 단계에 따라 첫 번째 비프로덕션 배포 파이프라인을 만듭니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. Cloud Manager 홈 화면에서 **파이프라인** 카드에 액세스합니다. **+추가**&#x200B;를 클릭하고 **비프로덕션 파이프라인 추가**&#x200B;를 선택합니다.

   ![비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **비프로덕션 파이프라인 추가** 대화 상자의 **구성** 탭에서 추가할 비프로덕션 파이프라인 유형을 선택합니다. 이 예에서는 **파이프라인 배포**&#x200B;를 선택합니다.

   ![비프로덕션 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. 파이프라인을 식별할 수 있도록 다음 추가 정보와 함께 **비프로덕션 파이프라인 이름**&#x200B;을 입력합니다.

1. **배포 트리거**&#x200B;에 대해 **수동**&#x200B;을 선택하여 파이프라인을 시작할 때만 실행되도록 합니다.

1. **계속**&#x200B;을 클릭합니다.

1. **비프로덕션 파이프라인 추가** 대화 상자의 **소스 코드** 탭에서 파이프라인이 처리해야 하는 코드 유형을 선택해야 합니다. 이 예에서는 **전체 스택 코드**&#x200B;를 선택합니다.

1. **소스 코드** 탭에서 다음 옵션을 정의해야 합니다.

   * **적합한 배포 환경** - 파이프라인을 배포할 환경을 선택해야 합니다.
   * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 git 저장소를 정의합니다.
   * **Git 분기** - 이 옵션은 선택한 파이프라인에서 코드를 검색해야 하는 분기를 정의합니다.
      * 분기 이름의 처음 몇 글자를 입력하면 이 필드의 자동 완성 기능이 일치하는 분기를 찾아 선택하는 데 도움이 됩니다.

   ![전체 스택 파이프라인](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. **저장**&#x200B;을 클릭합니다.

이제 첫 번째 파이프라인을 만들었습니다! 이제 배포 관리자 역할이 있는 사용자가 Cloud Manager UI에서 파이프라인을 시작할 수 있습니다.

## 배포 {#deploy}

이제 개발자가 git 저장소에 사용자 정의 코드를 추가했고 해당 코드를 배포하기 위한 파이프라인이 만들어졌으므로 파이프라인을 실행하여 실제로 해당 코드를 git에서 사용자 환경으로 이동할 차례입니다.

![Cloud Manager의 파이프라인 카드](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 이전 섹션에서 만든 파이프라인 옆에 있는 줄임표 버튼을 클릭하고 메뉴에서 **실행**&#x200B;을 선택합니다.

1. 파이프라인 실행이 시작되고 **상태** 열에 표시됩니다.

줄임표 버튼을 다시 클릭하고 **세부 정보 보기**&#x200B;를 선택하면 실행 세부 정보를 볼 수 있습니다.

축하합니다! 이제 git 저장소에서 비프로덕션 환경으로 코드를 배포했습니다!

## 다음 단계 {#whats-next}

이 문서를 읽고 나면 다음과 같은 작업을 수행할 수 있습니다.

* 개발자로서 Cloud Manager git 저장소에 액세스하고 관리하는 방법을 이해할 수 있습니다.
* 배포 관리자로서 파이프라인을 설정하고 Cloud Manager에서 코드를 배포할 수 있습니다.

Cloud Manager뿐 아니라 작업 환경, 저장소 및 파이프라인에 대한 실무 지식을 갖춘 개발자 또는 배포 관리자로서 첫 발을 내디뎠습니다! 그러나 AEM as a Cloud Service의 강력한 CI/CD 도구에 대해 더 알아볼 수 있습니다. 자세한 내용은 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

콘텐츠 작성자가 AEM as a Cloud service에 액세스하고 사용하는 방법에 관심이 있는 경우 온보딩 여정의 마지막 부분인 [AEM 사용자 작업](aem-users.md)을 계속 진행하십시오.

>[!TIP]
>
>이제 온보딩되었으므로 최소한의 AEM 구성으로 [AEM 참조 데모 추가 기능을 샌드박스 환경에 손쉽게 추가](/help/journey-sites/demos-add-on/overview.md)하는 방법을 배우고 모범 사례를 기반으로 하는 풍부한 예를 통해 AEM의 강력한 기능을 테스트할 수 있습니다.

## 추가 리소스 {#additional-resources}

온보딩 여정의 콘텐츠를 능가하려는 경우 다음은 추가적인 옵션 리소스입니다.

* [저장소 액세스](/help/implementing/cloud-manager/managing-code/accessing-repos.md) - Cloud Manager의 셀프서비스 git 계정 관리를 사용하여 git 저장소에 액세스하고 관리하는 방법을 알아봅니다.
* [Cloud Manager와 함께 git 사용](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) - Cloud Manager의 git 저장소를 사용하는 방법과 자체 On-Premise 고객 관리 git 저장소를 Cloud Manager와 통합하는 방법을 알아봅니다.
* [로컬 개발 환경 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) - 이 튜토리얼에서는 AEM as a Cloud Service SDK를 사용하여 Adobe Experience Manager(AEM)용 로컬 개발 환경을 설정하는 과정을 안내합니다.
* [AEM Sites 시작하기 - WKND 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) - Adobe Experience Manager(AEM)를 처음 사용하는 개발자를 위해 설계된 멀티 파트 튜토리얼에 오신 것을 환영합니다. 이 튜토리얼은 WKND의 가상 라이프스타일 브랜드를 위한 AEM 사이트의 구현 과정을 안내합니다. 이 튜토리얼은 Adobe Experience Manager Sites를 통한 사용한 프로젝트 설정, 핵심 구성 요소, 편집 가능한 템플릿, 클라이언트측 라이브러리 및 구성 요소 개발 등의 기본 주제를 다룹니다.
* [React를 사용하여 AEM에서 SPA 시작하기](/help/implementing/developing/hybrid/getting-started-react.md) - 이 문서에서는 샘플 SPA 애플리케이션을 제공하고, 구성 방법을 설명하며, React 프레임워크를 사용하여 SPA를 빠르게 시작하고 실행할 수 있도록 지원합니다.
* [Angular 사용하여 AEM에서 SPA 시작하기](/help/implementing/developing/hybrid/getting-started-angular.md) - 이 문서에서는 샘플 SPA 애플리케이션을 제공하고, 구성 방법을 설명하며, Angular 프레임워크를 사용하여 SPA를 빠르게 시작하고 실행할 수 있도록 지원합니다.
* [Headless 개발자 여정](/help/journey-headless/developer/overview.md) - AEM을 사용하여 Headless 애플리케이션을 개발하기 위한 안내 과정을 보려면 여기에서 시작하십시오.
