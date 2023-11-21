---
title: AEM as a Cloud Service 팀 및 제품 프로필
description: AEM as a Cloud Service 팀 및 제품 프로필이 사용 허가된 Adobe 솔루션에 대한 액세스 권한을 부여 및 제한할 수 있는 방법에 대해 알아봅니다.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 92%

---


# AEM as a Cloud Service 팀 및 제품 프로필 {#product-profiles}

AEM as a Cloud Service 팀 및 제품 프로필이 사용 허가된 Adobe 솔루션에 대한 액세스 권한을 부여 및 제한할 수 있는 방법에 대해 알아봅니다.

## 제품 프로필 {#profiles}

사용자에게 특정 Adobe 솔루션에 대한 액세스 권한을 부여할 때 반드시 전체 액세스 권한을 부여할 필요는 없습니다. 제품 프로필을 사용하면 각 솔루션이 고유한 사용자 권한 집합을 가질 수 있습니다. [Admin Console](/help/journey-onboarding/admin-console.md)을 통해 사용하고 액세스할 수 있습니다.

## AEM as a Cloud Service 제품 프로필 {#aem-product-profiles}

AEM as a Cloud Service는 AEM as a Service를 제공하는 완전한 클라우드 네이티브 제품입니다. 항상 켜짐, 항상 최신 상태, 항상 보안, 항상 규모에 맞게 확장과 같은 새로운 속성을 사용하여 클라우드 네이티브 방식으로 AEM을 제공합니다. 동시에 AEM이 고객에게 사용자 정의 플랫폼으로 제공하는 주요 가치 제안을 유지하고 기업 팀이 개발 및 게재 절차에 통합할 수 있도록 지원합니다. AEM as a Cloud에 대해 자세히 알아보려면 [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)를 참조하십시오.

AEM as a Cloud Service 팀원은 온보딩 중 Admin Console을 통해 다음 제품 프로필 중 하나 이상에 추가 및 할당됩니다.

* **AEM 관리자**: AEM 관리자는 일반적으로 개발자, 특히 개발 환경 등에 대한 액세스 권한이 필요한 개발자에게 할당됩니다. AEM 관리자의 제품 프로필은 연결된 AEM 인스턴스에서 관리자 권한을 부여하는 데 사용됩니다.

* **AEM 사용자**: AEM 사용자는 일반적으로 AEM as a Cloud Service를 사용하여 콘텐츠를 만드는 조직의 사용자입니다. 이러한 사용자는 작업을 수행하기 위해 AEM에 액세스해야 합니다. AEM 사용자 제품 프로필은 일반적으로 콘텐츠를 만들고 검토하는 AEM 콘텐츠 작성자에게 할당됩니다. 이 콘텐츠는 페이지, 자산, 발행물 등과 같은 매우 다양한 유형일 수 있습니다. 아래에 표시된 AEM 사용자 제품 프로필이 이러한 멤버에게 할당됩니다.

![제품 프로필](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>AEM as a Cloud Service 제품 프로필에 할당된 모든 사용자는 **Cloud Manager 사용** 역할을 통해 Cloud Manager에 대한 읽기 전용 액세스 권한이 있습니다.
>
>**Cloud Manager 사용**&#x200B;역할만 있는 사용자는 **프로그램** 메뉴 옵션을 사용하여 Cloud Manager에 로그인하고 AEM 작성자 환경(존재하는 경우)으로 이동할 수 있습니다. **Cloud Manager 사용** 역할은 프로그램 세부 정보에 액세스하기에 충분하지 않습니다. 이러한 액세스 권한이 필요한 경우 사용자는 시스템 관리자로부터 추가 역할을 부여받아야 합니다.

>[!WARNING]
>
>**AEM 관리자** 제품 프로필 이름은 변경하면 안 됩니다. **AEM 관리자** 제품 프로필의 이름을 변경하면 해당 프로필에 할당된 모든 사용자의 관리자 권한이 제거됩니다.

>[!TIP]
>
>* AEM 제품 프로필에 대한 자세한 내용은 [AEM 제품 프로필 할당](/help/journey-onboarding/assign-profiles-aem.md).
>* 온보딩 프로세스에 대한 자세한 내용은 [온보딩 여정](/help/journey-onboarding/overview.md)을 참조하십시오.

## Cloud Manager 제품 프로필 {#cloud-manager-product-profiles}

Cloud Manager에는 역할 기반 권한으로 생각할 수 있는 사전 구성된 제품 프로필이 있습니다. 시스템 관리자는 이러한 제품 프로필에 할당하여 Cloud Manager 팀을 설정할 책임이 있습니다.

>[!TIP]
>
>자세한 내용은 [Cloud Manager의 역할 기반 권한](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)을 참조하십시오.

각 제품 프로필에는 연결된 특정 권한이 있습니다.

* **비즈니스 소유자**
   * 이 역할에는 새 프로그램을 추가하거나 프로그램을 편집하고, 환경을 추가 또는 업데이트하거나, AEM 환경에 코드를 배포하거나, 코드 품질 검사를 실행할 수 있는 권한이 있습니다.
   * 이 사용자는 KPI를 정의하고, 프로덕션 구축을 승인하며, 필요한 경우 중요한 3계층 오류를 재정의할 책임이 있습니다.
* **배포 관리자**
   * 이 역할에는 환경을 추가 또는 업데이트하거나, 파이프라인을 실행하거나, AEM 환경에 코드를 배포하거나, 코드 품질 검사를 실행할 수 있는 권한이 있습니다.
   * 이 사용자는 배포 작업을 관리하고 Cloud Manager를 사용하여 스테이징/프로덕션 배포를 실행하고, CI/CD 파이프라인을 편집하고, 필요한 경우 중요한 3계층 오류를 승인하며, git 저장소에 액세스할 수 있습니다.
* **개발자**
   * 이 역할에는 git에 액세스하기 위한 개인 액세스 토큰을 생성할 수 있는 권한이 있습니다.
   * 이 사용자는 사용자 정의 애플리케이션 코드를 개발 및 테스트하고 주로 Cloud Manager를 사용하여 배포 상태를 보고 코드 커밋을 위해 git 저장소에 액세스할 수 있습니다.
* **프로그램 관리자**
   * 이 역할에는 파이프라인을 예약하고, 3계층 품질 게이트를 재정의하고, 프로덕션 승인을 제공할 수 있는 권한이 있습니다.
   * 이 사용자는 Cloud Manager를 사용하여 팀 설정, 상태 검토, KPI 보기를 수행하며 필요한 경우 중요한 3계층 오류를 승인할 수 있습니다.

한 사용자에게 여러 제품 프로필을 할당할 수 있습니다. 예를 들어 사용자에게 **비즈니스 소유자** 및 **배포 관리자** 역할을 모두 할당하면 이러한 권한의 합계가 제공됩니다.

Cloud Manager 팀에는 최소한 다음 역할이 포함됩니다.

* 일반적으로 시스템 관리자이며 Cloud Manager에 로그인하고 액세스하는 첫 번째 사람인 **비즈니스 소유자** 1명
* **배포 관리자** 1명
* **개발자** 1명

>[!NOTE]
>
>AEM as a Cloud Service에 대한 액세스 권한을 부여받으려면 사용자가 `AEM Users` 또는 `AEM Administrators` 제품 프로필 중 하나에 속해야 합니다. Cloud Manager를 관리할 수 있는 권한은 충분하지 않습니다.

>[!TIP]
>
>* Cloud Manager 제품 프로필에 대한 자세한 내용은 [Cloud Manager 제품 프로필에 팀원 할당](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* 온보딩 프로세스에 대한 자세한 내용은 [온보딩 여정](/help/journey-onboarding/overview.md)을 참조하십시오.
