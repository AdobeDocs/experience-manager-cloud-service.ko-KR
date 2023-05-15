---
title: AEM as a Cloud Service 온보딩 여정 소개
description: AEM as a Cloud Service로의 온보드 프로세스를 통해 안내하는 여정에 대한 개요를 보려면 여기를 클릭하십시오.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
source-git-commit: 98eff568686c72c626d2bf77d82e8c3f224eda42
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 58%

---


# 온보딩 여정 {#onboarding-journey}

AEM as a Cloud Service를 선택해 주셔서 감사합니다. 이 문서는 온보딩 프로세스를 통해 안내하는 여정의 시작점입니다. 새 애플리케이션을 배포하거나 기존 애플리케이션을 마이그레이션하든 관계없이 이 온보딩 여정을 통해 팀이 AEM as a Cloud Service에 액세스할 수 있습니다.

## 소개 {#introduction}

온보딩은 지정된 시스템 관리자가 조직에 대해 AEM as a Cloud Service을 설정하는 프로세스입니다. 이 프로세스에는 첫 번째 클라우드 리소스 프로비저닝과 작업 권한에 따라 역할에 사용자를 할당하는 작업이 포함됩니다. 따라서 각 구성원은 AEM as a Cloud Service에서 로그온하여 리소스에 액세스할 수 있습니다.

![온보딩 여정](/help/journey-onboarding/assets/onboarding-journey.png)

이 안내서는 가장 중요한 온보딩 항목을 안내하여 완료되면 다음을 수행할 수 있습니다.

* 온보딩 프로세스와 관련된 다양한 용어, 서비스 및 사용자를 완벽하게 이해합니다.
* 팀이 AEM as a Cloud Service 애플리케이션을 위한 콘텐츠를 작성 및 개발하는 방법을 배우기 위한 첫 단계를 시작할 수 있도록 지원합니다.

그 결과는 다음과 같습니다.

* 팀이 설정되고 클라우드 리소스에 대한 액세스 권한이 있습니다.
* AEM 작성자는 AEM as a Cloud Service에 액세스할 수 있으며 컨텐츠 만들기를 시작할 수 있습니다.
* AEM 개발자 및 배포 관리자는 AEM as a Cloud Service에 액세스할 수 있으며 사용자 정의 애플리케이션 만들기 및 배포를 시작할 수 있습니다.

## 개념 및 목표 {#concepts}

AEM as a Cloud Service를 시작할 때 알아야 할 것이 많은 것처럼 보일 수 있지만 개념적으로 논리적인 부분은 몇 개뿐입니다.

* **계약** - 온보딩 프로세스의 측면을 정의하므로 Adobe 계약에 익숙해야 합니다.
* **Admin Console** - 사용자를 관리하고 역할을 할당하는 위치
* **Cloud Manager** - 프로그램 및 환경과 같은 리소스를 설정하는 도구입니다. 또한 여기에서 git에 액세스하고 파이프라인을 만들어 사용자 정의 코드를 관리 및 배포합니다.

이러한 개념은 이 온보딩 여정에서 자세히 설명합니다. 목표는 여정이 끝날 때 다음과 같은 작업을 수행하는 것입니다.

* AEM as a Cloud Service에 필요한 사용자의 액세스 권한을 부여했습니다.
* 프로젝트에 대한 첫 번째 클라우드 리소스 설정.
* 첫 번째 코드 배포 및 첫 번째 콘텐츠 작성 방법 이해

기본적으로, 당신은 당신의 새로운 AEM as a Cloud Service 프로젝트를 실행하며 나아갑니다!

## 대상자 {#audience}

일반적으로 온보딩 여정은 AEM as a Cloud Service 및 AEM을 처음 시작하는 고객의 **시스템 관리자**&#x200B;를 위해 특별히 작성되었습니다. 시스템 관리자는 AEM as a Cloud Service 계약이 체결된 후 Adobe이 처음 연락하는 개인입니다. 일반적으로 AEM as a Cloud Service에서 리소스에 액세스하여 설정하는 첫 번째 사람입니다. 이 항목을 읽는 경우 시스템 관리자일 수 있습니다.

시스템 관리자는 액세스에서 권한에 이르기까지 조직의 AEMaaCS 사용자의 모든 측면을 관리합니다. 그러나 시스템 관리자는 그 과정에서 다른 담당자와 상호 작용해야 합니다.

| 담당자 | 설명 | 여정에서의 역할 |
|---|---|---|
| 시스템 관리자 | 이 여정의 대상은 클라우드 리소스의 초기 프로비저닝과 직무에 따라 적절한 역할에 사용자를 할당합니다. | 액세스부터 권한까지 사용자의 모든 측면을 관리합니다. |
| 콘텐츠 작성자 | AEM에서 콘텐츠를 만들고 검토합니다. | 시스템 관리자가 권한을 부여하면 작성자가 콘텐츠를 만드는 여정을 시작할 수 있습니다. |
| 개발자 | 다양한 소스의 콘텐츠를 사용하는 AEM 애플리케이션을 개발합니다. | 시스템 관리자가 권한을 부여하면 개발자는 솔루션 개발 여정을 시작할 수 있습니다. |
| 배포 관리자 | 환경을 추가 또는 업데이트하고, 파이프라인을 실행하고, AEM 환경 또는 코드 품질에 코드를 배포합니다. | 시스템 관리자가 권한을 부여하면 배포 관리자는 배포 관리 여정을 시작할 수 있습니다. |

이 온보딩 안내서는 시스템 관리자로서 온보딩하는 전체 프로세스를 보여 줍니다. AEM 사용자, 개발자 및 배포 관리자의 역할은 여정의 부가적인 선택 사항으로 간략하게 살펴봅니다.

>[!TIP]
>
>AEM에 익숙하고 AEM을 처음 사용하는 경우 온-프레미스 또는 Adobe Managed Services에서 마이그레이션하는 경우에는 다음을 확인하십시오. [AEM as a Cloud Service 마이그레이션 여정](/help/journey-migration/getting-started.md).

## 온보딩 여정 개요 {#overview}

다음 문서에서는 핵심 온보딩 개념을 자세히 설명하고 AEM as a Cloud Service에 대한 기본 지식을 제공합니다. 여정의 특정 부분으로 바로 이동할 수 있지만 많은 개념이 이전 문서의 개념을 기반으로 합니다. 따라서 온보딩을 처음 사용하는 경우 처음부터 시작하여 순차적으로 진행되는 것이 좋습니다.

| # | 문서 | 설명 | 대상자 |
|---|---|---|---|
| 0 | 온보딩 여정 | 이 문서 | 시스템 관리자 |
| 1 | [온보딩 준비](preparation.md) | 온보딩 프로세스가 시작되기 전에 시스템 관리자가 시스템에 로그인하기 위해 이해해야 하는 몇 가지 준비 단계가 있습니다. | 시스템 관리자 |
| 2 | [AEM as a Cloud Service 용어](terminology.md) | AEMaaCS에 처음 로그인하기 전에 시스템 용어와 기본 구조를 이해하는 것이 좋습니다. | 시스템 관리자 |
| 3 | [Admin Console](admin-console.md) | Admin Console이란 무엇이고, 어떻게 로그인하는지, 그리고 시스템 관리자로서 프로필을 확인하는 방법에 대해 알아봅니다. | 시스템 관리자 |
| 4 | [Cloud Manager 제품 프로필 할당](assign-profiles-cloud-manager.md) | Cloud Manager 제품 프로필을 검토하고 Cloud Manager 제품 프로필에 팀원을 할당하는 방법을 알아봅니다. | 시스템 관리자 |
| 5 | [Cloud Manager 액세스](cloud-manager.md) | 프로젝트 리소스를 설정할 수 있도록 Cloud Manager에 액세스하는 방법을 알아봅니다. | 시스템 관리자 |
| 6 | [프로그램 만들기](create-program.md) | Cloud Manager를 사용하여 프로그램을 만드는 방법을 배웁니다. | 시스템 관리자 |
| 7 | [환경 만들기](create-environments.md) | Cloud Manager를 사용하여 환경을 만드는 방법을 배웁니다. | 시스템 관리자 |
| 8 | [AEM 제품 프로필 할당](assign-profiles-aem.md) | 시스템 관리자가 AEM as a Cloud Service의 제품 프로필에 팀 구성원을 할당하는 방법을 알아봅니다. | 시스템 관리자 |
| 9 | [개발자 및 배포 관리자 작업](developers.md) | 선택 사항 - 개발자로서 Cloud Manager Git에 액세스 및 관리 방법과 배포 관리자로서 파이프라인을 설정하고 Cloud Manager에서 코드를 배포할 수 있는 방법을 알아봅니다. | 개발자 및 배포 관리자 |
| 10 | [AEM 사용자 작업](aem-users.md) | 선택 사항 - AEM 작성자로서 AEM as a Cloud Service 인스턴스에 액세스하고 AEM용 컨텐츠 작성에 익숙해지는 방법을 배웁니다. | AEM 사용자 |

## 다음 단계 {#what-is-next}

이제 AEM as a Cloud Service 온보딩 여정을 시작할 준비가 되었습니다. 여정의 다음 부분으로 계속 이동하여 해당 문서를 읽는 것이 좋습니다 [온보딩 준비](preparation.md)

## AEM 설명서 여정 {#documentation-journeys}

[설명서 여정](/help/journey-documentation/documentation-journeys.md) 여러 가지 복잡한 주제 및 기능을 함께 사용할 수 있습니다. AEM을 처음 사용하는 독자가 최소한의 이전 주제나 AEM 지식을 가정하면서 비즈니스 문제를 처음부터 끝까지 이해하고 해결하는 데 도움이 되는 설명을 제공합니다.

설명서 여정은 Adobe의 최신 연구, Adobe 컨설턴트의 입증된 구현 경험 및 고객 프로젝트의 피드백을 통해 제공되는 모범 사례 원칙을 중심으로 설계되었습니다.

새 AEM as a Cloud Service 애플리케이션에 팀을 온보딩하는 방법에 대해 Adobe이 권장하는 사항을 알아보려면 여기에서 시작하십시오!

<!-- ERROR: Not Found (HTTP error 404)
## Additional Resources {#additional-resources}

The following are additional, optional resources if you would like to go beyond the content of the onboarding journey.

* [AEM Champion Tips and Tricks - Cloud Manager Onboarding Playbook](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/onboarding-playbook.md) - Watch this video to learn Cloud Manager onboarding tips and trick from an AEM champion. -->


