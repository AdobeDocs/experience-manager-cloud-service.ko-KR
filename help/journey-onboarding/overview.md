---
title: AEM as a Cloud Service 온보딩 여정 소개
description: AEM as a Cloud Service로의 온보드 프로세스를 통해 안내하는 여정에 대한 개요를 보려면 여기를 클릭하십시오.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
source-git-commit: 75c0e8cbaa409fa48750e794c27ace98eda107d0
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 16%

---


# 온보딩 여정 {#onboarding-journey}

AEM as a Cloud Service을 선택하신 것을 축하합니다! 이 문서는 온보딩 프로세스를 통한 안내 여정의 시작점입니다. 새 애플리케이션을 배포하든 기존 애플리케이션을 마이그레이션하든 관계없이 이 온보딩 여정을 통해 팀이 AEM as a Cloud Service에 액세스할 수 있습니다.

## 소개 {#introduction}

온보딩은 지정된 시스템 관리자가 조직에 대해 AEM as a Cloud Service을 설정하는 프로세스입니다. 여기에는 초기 클라우드 리소스 프로비저닝과 작업 권한에 따라 역할에 사용자를 할당하는 작업이 포함됩니다. 따라서 각 구성원은 AEM as a Cloud Service 리소스에 로그인하여 액세스할 수 있습니다.

![온보딩 여정](/help/journey-onboarding/assets/onboarding-journey.png)

이 안내서는 가장 중요한 온보딩 항목을 안내하여 완료되면 다음 내용을 보게 합니다.

* 온보딩 프로세스와 관련된 다양한 용어, 서비스 및 사용자를 완벽하게 이해합니다.
* 팀을 활성화하여 AEM as a Cloud Service 애플리케이션용 컨텐츠를 작성하고 개발하는 방법을 학습하고 첫 번째 단계를 수행할 수 있습니다.

그 결과:

* 팀이 설정되고 클라우드 리소스에 대한 액세스 권한이 있습니다.
* AEM 작성자는 AEM as a Cloud Service에 액세스할 수 있고 컨텐츠 만들기를 시작할 수 있습니다.
* AEM 개발자 및 배포 관리자는 AEM as a Cloud Service에 액세스할 수 있으며 사용자 지정 애플리케이션 만들기 및 배포를 시작할 수 있습니다.

## 개념 및 목표 {#concepts}

AEM as a Cloud Service을 시작할 때 배울 점이 많을 수 있지만 개념적으로는 몇 가지 논리적 부분만 있습니다.

* **계약** - 온보딩 프로세스의 측면을 정의하므로 Adobe 계약을 잘 알고 있어야 합니다.
* **Admin Console** - 사용자가 관리되고 역할이 할당됩니다.
* **Cloud Manager** - 프로그램 및 환경과 같은 리소스를 설정하는 도구입니다. 또한 Git에 액세스하고 파이프라인을 만들어 사용자 지정 코드를 관리하고 배포할 수도 있습니다.

이러한 개념은 이 온보딩 여정에서 자세히 설명합니다. 목표는 여정 끝에 있는 사용자가

* 필요한 사용자에게 AEM AaCS에 대한 액세스 권한을 부여했습니다
* 프로젝트에 대한 첫 번째 클라우드 리소스를 설정했습니다
* 첫 번째 코드를 배포하고 첫 번째 콘텐츠를 작성하는 방법을 알아봅니다.

기본적으로 당신은 당신의 새로운 AEM as a Cloud Service 프로젝트를 실행하게 될 것입니다!

## 대상자 {#audience}

온보딩 여정은 특별히 **시스템 관리자** 일반적으로 AEM의 신규 고객 및 AEM에 대한 내용입니다. 시스템 관리자는 AEM as a Cloud Service 계약이 서명된 후 Adobe에 의해 처음 연락되는 개인이며 일반적으로 AEM as a Cloud Service 리소스에 액세스하여 설정하는 첫 번째 사용자입니다. 이 내용을 읽는 경우 시스템 관리자가 될 수 있습니다.

시스템 관리자는 액세스 권한부터 조직의 AEMaaCS 사용자의 모든 측면을 관리합니다. 그러나 시스템 관리자는 계속 다른 사용자와 상호 작용해야 합니다.

| 담당자 | 설명 | 여정에서의 역할 |
|---|---|---|
| 시스템 관리자 | 이 여정의 Target은 첫 번째 클라우드 리소스 프로비저닝 및 사용자의 작업 책임을 기반으로 적절한 역할에 사용자를 할당합니다 | 액세스 권한에서 사용자의 모든 측면을 관리합니다 |
| 컨텐츠 작성자 | AEM에서 컨텐츠를 만들고 검토합니다 | 시스템 관리자가 권한을 부여하면 작성자가 여정 만들기를 시작할 수 있습니다 |
| 개발자 | 다양한 소스의 컨텐츠를 소비하는 AEM 애플리케이션을 개발합니다. | 시스템 관리자가 권한을 부여하면 개발자는 자체 여정 개발 솔루션을 시작할 수 있습니다 |
| 배포 관리자 | 환경을 추가 또는 업데이트하고, 파이프라인을 실행하고, 코드를 AEM 환경 또는 코드 품질에 배포합니다. | 시스템 관리자가 권한을 부여하면 배포 관리자가 자체 여정 관리를 시작할 수 있습니다 |

이 온보딩 안내서는 시스템 관리자로서 온보딩의 전체 프로세스를 보여줍니다. AEM 사용자, 개발자 및 배포 관리자의 역할은 여정의 추가적인 선택적 부분으로 간략하게 살펴봅니다.

>[!TIP]
>
>AEM as a Cloud Service을 처음 사용하지만 이미 AEM에 익숙하며 온-프레미스 또는 Adobe Managed Services에서 마이그레이션하는 경우에는 다음을 확인하십시오. [AEM as a Cloud Service 마이그레이션 여정.](/help/journey-migration/getting-started.md)

## 온보딩 여정 개요 {#overview}

다음 문서는 코어 온보딩 개념에 대해 자세히 설명하고 AEM as a Cloud Service에 대한 기본 지식을 제공합니다. 여정의 특정 부분으로 바로 이동할 수 있지만, 많은 개념이 이전 문서의 개념을 기반으로 합니다. 따라서 온보딩을 처음 사용하는 경우에는 시작 부분부터 시작하여 순차적으로 진행하는 것이 좋습니다.

| # | 문서 | 설명 | 대상자 |
|---|---|---|---|
| 0 | 온보딩 여정 | 이 문서 | 시스템 관리자 |
| 1 | [온보딩 준비](preparation.md) | 온보딩 프로세스가 시작되기 전에 시스템 관리자가 시스템에 로그인하기 전에 알고 있어야 하는 몇 가지 또는 준비 단계가 있습니다. | 시스템 관리자 |
| 2 | [AEM as a Cloud Service 용어](terminology.md) | AEMaaCS에 처음 로그인하기 전에 시스템의 용어 및 기본 구조의 일부를 이해하는 것이 도움이 됩니다. | 시스템 관리자 |
| 3 | [Admin Console](admin-console.md) | Admin Console 정의, 로그인 방법 및 시스템 관리자로 프로필을 확인하는 방법을 알아봅니다. | 시스템 관리자 |
| 4 | [Cloud Manager 제품 프로필 할당](assign-profiles-cloud-manager.md) | Cloud Manager 제품 프로필을 검토하고 팀 구성원을 Cloud Manager 제품 프로필에 할당하는 방법을 알아보십시오. | 시스템 관리자 |
| 5 | [Cloud Manager 액세스](cloud-manager.md) | 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다. | 시스템 관리자 |
| 6 | [프로그램 제작](create-program.md) | Cloud Manager를 사용하여 프로그램을 만드는 방법을 알아봅니다. | 시스템 관리자 |
| 7 | [환경 만들기](create-environments.md) | Cloud Manager를 사용하여 환경을 만드는 방법을 알아봅니다. | 시스템 관리자 |
| 8 | [AEM 제품 프로필 할당](assign-profiles-aem.md) | 시스템 관리자가 팀 구성원을 AEM as a Cloud Service 제품 프로필에 할당하는 방법을 알아봅니다. | 시스템 관리자 |
| 9 | [개발자 및 배포 관리자 작업](developers.md) | 선택 사항 - 개발자로서 Cloud Manager Git에 액세스 및 관리할 수 있는 방법과 배포 관리자로서 Cloud Manager에서 파이프라인을 설정하고 코드를 배포할 수 있는 방법을 알아봅니다. | 개발자 및 배포 관리자 |
| 10 | [AEM 사용자 작업](aem-users.md) | 선택 사항 - AEM 작성자로서 AEM as a Cloud Service 인스턴스에 액세스하고 AEM용 컨텐츠 작성에 익숙해지는 방법을 배웁니다. | AEM 사용자 |

## 다음 단계 {#what-is-next}

이제 AEM as a Cloud Service 온보딩 여정을 시작할 준비가 되었습니다. 여정의 다음 부분으로 계속 이동하여 문서를 읽어 보십시오 [온보딩 준비](preparation.md)

## AEM 설명서 여정 {#documentation-journeys}

[설명서 여정](/help/journey-documentation/documentation-journeys.md)은 AEM을 처음 접할 수 있는 독자가 최소한의 사전 주제 또는 AEM 지식을 전제로 비즈니스 문제를 처음부터 끝까지 이해하고 해결하는 데 도움이 되는 묘사를 제공하여 다양하고 복잡한 주제와 기능을 결합합니다.

설명서 여정은 Adobe의 최신 연구, Adobe 컨설턴트의 입증된 구현 경험 및 고객 프로젝트의 피드백을 통해 제공되는 모범 사례 원칙을 중심으로 설계되었습니다.

Adobe이 새로운 AEM as a Cloud Service 애플리케이션에 팀을 온보딩하는 방법을 알려면 여기에서 시작할 수 있습니다.
