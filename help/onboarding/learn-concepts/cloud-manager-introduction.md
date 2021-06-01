---
title: Cloud Manager란?
description: Cloud Manager, Cloud Manager 프로그램 및 환경에 대해 알려면 이 페이지를 따르십시오.
source-git-commit: 7985512f664dce33aa8d3ccd7e7fdc49e63e81f8
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---


# Cloud Manager 소개 {#intro-cloud-manager}

Cloud Manager는 AEM as a Cloud Service의 필수 구성 요소이며 팀의 단일 시작 지점으로 사용됩니다.

엔터프라이즈 개발 설정으로 고객을 지원하기 위해 AEM as a Cloud Service은 철저한 테스트와 최상의 코드 품질을 보장하여 탁월한 경험을 제공할 수 있도록 Cloud Manager 및 특별히 제작된 CI/CD 파이프라인과 완벽하게 통합됩니다.

고객이 AEM as a Cloud Service으로 빠르게 시작할 수 있도록 Cloud Manager는 클라우드 리소스 및 환경을 만드는 기능을 포함하여 셀프 서비스 방식으로 시작하는 데 필요한 모든 것을 제공합니다. 이러한 방식으로 AEM 개발자는 Cloud Manager를 통해 Git 리포지토리에 액세스할 수 있습니다. 개발 팀은 Cloud Manager를 사용하여 셀프 서비스 방식으로 변경 사항을 자주 커밋하는 작업을 수행할 수 있습니다.

시스템 관리자는 클라우드 리소스 및 개발자를 생성할 개인을 포함하는 Cloud Manager 팀을 설정할 책임이 있습니다. Cloud Manager가 Enterprise Team Development Setup에서 Cloud Manager를 지원하는 방법에 대해 알아보려면 [AEM as a Cloud Service용 Enterprise Team Development Setup 을 참조하십시오.](/help/implementing/cloud-manager/enterprise-team-dev-setup.md)

## Cloud Manager 프로그램 {#cloud-manager-programs}

Cloud Manager 프로그램은 비즈니스 이니셔티브의 논리적 집합을 지원하는 Cloud Manager 환경의 집합으로, 일반적으로 구매한 SLA(서비스 수준 계약)에 해당합니다. 예를 들어, 하나의 프로그램은 전역 공용 웹 사이트를 지원하는 AEM 리소스를 나타내고, 다른 프로그램은 내부 중앙 DAM을 나타냅니다. 자세한 내용은 이 비디오를 참조하십시오.

사용자는 **Sandbox** 또는 **Production** 프로그램을 만들 수 있습니다.

* *프로덕션 프로그램*이 생성되어 미래의 적절한 시간에 라이브 트래픽을 사용할 수 있습니다.
자세한 내용은 [프로덕션 프로그램 소개](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md)를 참조하십시오.

* *샌드박스 프로그램*은 일반적으로 교육용, 데모, 지원, POC 또는 설명서를 실행하기 위해 만들어집니다. 라이브 트래픽을 전달하기 위한 것이 아니며, 프로덕션 프로그램이 허용하지 않을 수 있는 제한 사항이 있습니다. 여기에는 사이트 및 자산이 포함되며, 샘플 코드, 개발 환경 및 비프로덕션 파이프라인이 포함된 Git 분기로 자동으로 채워집니다.
자세한 내용은 [샌드박스 프로그램 소개](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)를 참조하십시오.

## Cloud Manager 환경 {#cloud-manager-environments}

클라우드 환경은 Cloud Manager를 통해 생성, 액세스 및 표시됩니다. 프로덕션 환경, 스테이지 환경 또는 개발 환경일 수 있습니다. 다른 환경은 서로 다른 목적을 지원하며 서로 다른 CI/CD 파이프라인을 사용하여 참여할 수 있습니다. 환경은 다음과 같은 서비스로 구성됩니다.

* [AEM 작성자 서비스](#author-services)
* [AEM 게시 서비스](#publish-services)
* [Dispatcher 서비스](#dispatcher-services)

   >[!NOTE]
   > 사용 가능한 환경에 대한 자세한 내용은 비디오 [Adobe Cloud Manager 환경 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager)을 참조하십시오. 또한 사용자가 만들 수 있는 환경 유형과 사용자가 환경을 만들 수 있는 방법에 대한 자세한 내용은 [환경 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en) 를 참조하십시오.

### AEM 작성자 서비스 {#author-services}

AEM 작성자 서비스는 사이트 컨텐츠 및 디지털 자산을 생성, 관리 및 업데이트하는 환경에 포함됩니다. 일반적으로 내부 사용자만 작성자 서비스에 액세스할 수 있고 로그인 화면 뒤에 있습니다. 작성 서비스는 작성 및 미리 보기 환경으로 모두 디자인되었습니다.

### AEM 게시 서비스 {#publish-services}

AEM 게시 서비스는 웹 사이트와 같은 최종 사용자 경험을 호스팅하는 환경에 포함됩니다. 사이트 방문자가 보고 상호 작용하는 서비스입니다. 일반적으로 게시 서비스는 공개적으로 사용할 수 있습니다.

### AEM Dispatcher 서비스 {#dispatcher-services}

Dispatcher는 AEM 게시 서비스 앞에 있는 보안 및 성능 레이어를 제공하는 `Apache HTTP Web server` 모듈입니다.