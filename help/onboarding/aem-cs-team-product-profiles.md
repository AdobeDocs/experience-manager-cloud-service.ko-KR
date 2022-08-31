---
title: AEM as a Cloud Service 팀 및 제품 프로필
description: AEM as a Cloud Service 팀 및 제품 프로필을 확인하고 라이선스가 부여된 Adobe 솔루션에 대한 액세스 권한을 부여하고 제한하는 방법을 알아봅니다.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: d54c25791cbb06232ff6e24bb7b8005b366a2144
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 3%

---

# AEM as a Cloud Service 팀 및 제품 프로필 {#product-profiles}

AEM as a Cloud Service 팀 및 제품 프로필을 확인하고 라이선스가 부여된 Adobe 솔루션에 대한 액세스 권한을 부여하고 제한하는 방법을 알아봅니다.

## 제품 프로필 {#profiles}

특정 Adobe 솔루션에 대한 사용자 액세스 권한을 부여할 때 반드시 전체 액세스 권한을 부여할 필요는 없습니다. 제품 프로필을 사용하면 각 솔루션에 고유한 사용자 권한 세트를 가질 수 있습니다. 이러한 권한은 를 통해 사용 및 액세스할 수 있습니다 [Admin Console.](/help/journey-onboarding/admin-console.md)

## AEM as a Cloud Service 제품 프로필 {#aem-product-profiles}

AEM as a Cloud Service 은 AEM as a service를 제공하는 클라우드 기반의 서비스입니다. 항상 켜져 있고 항상 최신 상태이며 항상 안전하며 규모에 맞게 항상 새로운 특성을 사용하여 AEM을 클라우드 기반의 방식으로 전달합니다. 동시에 AEM에서 고객에게 맞춤형 플랫폼으로 제공하는 주요 가치 제안을 유지하고 엔터프라이즈급 팀이 개발 및 제공 절차에 통합할 수 있도록 지원합니다. 을(를) 참조하십시오. [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md) AEM as a Cloud Service에 대해 자세히 알아보십시오.

AEM as a Cloud Service 팀 구성원이 온보딩 중에 Admin Console을 통해 다음 제품 프로필 중 하나 이상에 추가되고 할당됩니다.

* **AEM 관리자**: AEM 관리자는 일반적으로 개발자나, 특히 개발 환경과 같은 환경에 액세스할 수 있어야 하는 개발자에게 할당됩니다. AEM 관리자의 제품 프로필이 연관된 AEM 인스턴스에서 관리자 권한을 부여하는 데 사용됩니다.

* **AEM 사용자**: AEM 사용자는 일반적으로 AEM as a Cloud Service을 사용하여 컨텐츠를 만드는 조직의 사용자입니다. 이러한 사용자는 작업을 수행하려면 AEM에 액세스해야 합니다. AEM 사용자 제품 프로필은 일반적으로 컨텐츠를 만들고 검토하는 AEM 컨텐츠 작성자에게 할당됩니다. 이 컨텐츠는 페이지, 자산, 게시물 등과 같은 많은 유형일 수 있습니다. 아래 표시된 AEM 사용자 제품 프로필은 이러한 구성원에게 지정됩니다.

![제품 프로필](/help/onboarding/assets/admin-console-profiles.png)

>[!NOTE]
>
>AEM as a Cloud Service 제품 프로필에 할당된 모든 사용자는 Cloud Manager에 (읽기 전용) 액세스할 수 있습니다.

>[!TIP]
>
>온보딩 프로세스에 대한 자세한 내용은 [온보딩 여정.](/help/journey-onboarding/overview.md)

## Cloud Manager 제품 프로필 {#cloud-manager-product-profiles}

Cloud Manager에는 역할 기반 권한으로 생각할 수 있는 사전 구성된 제품 프로필이 있습니다. 시스템 관리자는 이러한 제품 프로필에 Cloud Manager 팀을 설정하여 설정할 책임이 있습니다.

>[!TIP]
>
>문서를 참조하십시오 [Cloud Manager의 역할 기반 권한](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) 자세한 내용

각 제품 프로필에는 연관된 특정 권한이 있습니다.

* **비즈니스 소유자** - 이 역할에서는 새 프로그램을 추가하거나 프로그램을 편집하거나 환경을 추가 또는 업데이트하거나 코드를 AEM 환경에 배포하거나 코드 품질 검사를 실행할 수 있는 권한이 있습니다.
* **배포 관리자** - 이 역할에서는 환경을 추가 또는 업데이트하고, 파이프라인을 실행하고, 코드를 AEM 환경에 배포하거나, 코드 품질 검사를 실행할 수 있는 권한이 있습니다.
* **개발자** - 이 역할에서는 git에 액세스하기 위해 개인 액세스 토큰을 생성할 수 있는 권한이 있습니다.
* **프로그램 관리자** - 이 역할에서는 파이프라인을 예약하고, 3 계층 품질 게이트를 재정의하고, 프로덕션 승인을 제공할 수 있는 권한이 있습니다.

사용자는 여러 제품 프로필에 할당할 수 있습니다. 예를 들어, 둘 다 할당합니다 **비즈니스 소유자** 및 **배포 관리**&#x200B;사용자에게 롤이나 역할을 통해 이러한 권한의 합계를 제공합니다.

Cloud Manager 팀에는 적어도 다음이 포함됩니다.

* 1개 **비즈니스 소유자**- 일반적으로 시스템 관리자이며, Cloud Manager에 처음으로 로그인하고 액세스할 수 있어야 합니다.
* 1개 **배포 관리자**
* 1개 **개발자**

>[!NOTE]
>
>AEM as a Cloud Service에 대한 액세스 권한을 부여받으려면 사용자가 다음 두 제품 프로필 중 하나에 속해야 합니다. `AEM Users` 또는 `AEM Administrators`. Cloud Manager 관리 권한으로는 충분하지 않습니다.
