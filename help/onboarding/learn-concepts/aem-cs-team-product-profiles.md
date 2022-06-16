---
title: AEM as a Cloud Service 팀 및 제품 프로필
description: AEM as a Cloud Service 팀 및 제품 프로필에 대해 알려면 이 페이지를 따르십시오.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
source-git-commit: fd23701414a2ae4142ea2a11cef92bc0cb202421
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# AEM as a Cloud Service 팀 및 제품 프로필 {#product-profiles}

## 제품 프로필 {#profiles}

특정 Adobe 솔루션에 대한 사용자 액세스 권한을 부여할 때 반드시 전체 액세스 권한을 부여할 필요는 없습니다. 제품 프로필을 사용하면 각 솔루션에 고유한 사용자 권한 세트를 가질 수 있습니다. 이러한 권한은 를 통해 사용 및 액세스할 수 있습니다 [Adobe Admin Console](/help/onboarding/learn-concepts/admin-console.md).

자세한 내용 [AEM as a Cloud Service 제품 프로필](#aem-product-profiles) 및 [Cloud Manager 제품 프로필](#cloud-manager-product-profiles) 팀이 설정되는 동안 이러한 작업이 어떻게 작동하는지 이해할 수 있습니다.

## AEM as a Cloud Service 제품 프로필 {#aem-product-profiles}

AEM as a Cloud Service 은 AEM as a service를 제공하는 완전히 클라우드 기반의 서비스입니다. 항상 켜져 있고 항상 최신 상태이며 항상 안전하며 규모에 맞게 항상 새로운 특성을 사용하여 AEM을 클라우드 기반의 방식으로 전달합니다. 동시에 AEM에서 고객에게 맞춤형 플랫폼으로 제공하는 주요 가치 제안을 유지하고 엔터프라이즈급 팀이 개발 및 제공 절차에 통합할 수 있도록 지원합니다. 을(를) 참조하십시오. [Adobe Experience Manager as a Cloud Service 소개](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en) AEM as a Cloud Service에 대해 자세히 알아보십시오.

AEM as a Cloud Service 팀 구성원이 온보딩 중에 Admin Console을 통해 다음 제품 프로필 중 하나 이상에 추가되고 할당됩니다.

* **AEM 관리자**: AEM 관리자는 일반적으로 개발자나, 특히 개발 환경과 같은 환경에 액세스할 수 있어야 하는 개발자에게 할당됩니다. AEM Administrators 제품 프로필은 연결된 AEM 인스턴스에서 관리자 권한을 부여하는 데 사용됩니다.

* **AEM 사용자**: AEM 사용자는 Adobe과의 계약의 일부로 AEM as a Cloud Service을 사용하는 조직의 사용자입니다. 이러한 구성원은 작업을 수행하려면 AEM에 액세스해야 합니다. AEM 사용자 제품 프로필은 일반적으로 컨텐츠를 만들고 검토하는 AEM 컨텐츠 작성자에게 할당됩니다(몇 가지 유형일 수 있습니다. 예를 들어, 페이지, 자산, 게시물 등이 웹 사이트에 게시되기 전에 게시됩니다. 아래 표시된 AEM Users 제품 프로필은 이러한 구성원에게 지정됩니다.

   ![](/help/onboarding/learn-concepts/assets/admin-console-profiles.png)

   >[!NOTE]
   >AEM as a Cloud Service 제품 프로필에 할당된 모든 사용자는 Cloud Manager에 (읽기 전용) 액세스할 수 있습니다.

## Cloud Manager 제품 프로필 {#cloud-manager-product-profiles}

Cloud Manager에는 미리 구성된 제품 프로필 또는 보다 간단한 역할 기반 권한이 있습니다. 시스템 관리자는 이러한 제품 프로필에 Cloud Manager 팀을 할당하여 Cloud Manager 팀을 설정할 책임이 있으며, 이러한 제품 프로필과 이 팀을 할당할 팀 구성원을 숙지해야 합니다.
>[!NOTE]
>을(를) 참조하십시오. [Cloud Manager의 역할 기반 권한](/help/onboarding/learn-concepts/cloud-manager-introduction.md##role-based-permissions) 자세한 내용

각 제품 프로필에는 연관된 특정 권한이 있습니다. 예를 들어 다음 역할의 경우:

* **비즈니스 소유자**&#x200B;를 지정하는 경우에는 새 프로그램을 추가하거나 프로그램을 편집하고 환경을 추가 또는 업데이트하고 파이프라인을 추가/편집/삭제하고 파이프라인을 실행하고 코드를 AEM 환경 또는 코드 품질에 배포할 수 있는 권한이 있습니다.

* **배포 관리자**&#x200B;를 사용하는 경우 환경을 추가 또는 업데이트하고, 파이프라인을 실행하고, 코드를 AEM 환경 또는 코드 품질에 배포할 수 있는 권한이 있습니다.

* **개발자** git에 액세스할 수 있는 개인 액세스 토큰을 생성할 수 있는 권한이 있습니다.

* **프로그램 관리자**&#x200B;를 지정하는 경우 파이프라인을 예약하고, 3 계층 품질 게이트를 재정의하고, 프로덕션 승인을 제공할 권한이 있습니다.

사용자는 여러 제품 프로필에 할당할 수 있습니다. 예를 들어, 사용자에게 비즈니스 소유자 및 배포 관리자 역할을 모두 할당하면 이러한 권한의 조합이나 합계가 제공됩니다.

Cloud Manager 팀에는 적어도 다음이 포함됩니다.

* 일반적으로 시스템 관리자이며 Cloud Manager에 처음으로 로그인하고 액세스할 수 있는 비즈니스 소유자 한 명
* 단일 배포 관리자
* 하나의 개발자

   >[!NOTE]
   >AEM as a Cloud Service에 대한 액세스 권한을 부여받으려면 사용자가 다음 두 제품 프로필 중 하나에 속해야 합니다. `AEM Users` 또는 `AEM Administrators`. 인스턴스에 대한 권한을 부여해야 하며, 연결된 Cloud Manager를 관리할 수 있는 권한으로는 충분하지 않습니다.
