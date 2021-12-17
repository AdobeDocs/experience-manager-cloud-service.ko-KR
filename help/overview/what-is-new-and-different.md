---
title: 차이점 및 새로운 기능 - Adobe Experience Manager as a Cloud Service
description: 차이점 및 새로운 기능 - Adobe Experience Manager(AEM) as a Cloud Service.
exl-id: d1ce126e-960c-4367-b741-af709dd81010
source-git-commit: cf688addd731d7a7107a648b40fbbdd149fef503
workflow-type: tm+mt
source-wordcount: '1906'
ht-degree: 10%

---

# 새로운 기능 및 차이점 {#what-is-new-and-what-is-different}

수년 동안 AEM은 다음 두 가지 모두를 사용할 수 있습니다.

* On-Premise

* as a Managed Service

이러한 이전 접근 방식과 AEM as a Cloud Service 에는 고유한 차이점이 있습니다.

* [아키텍처](#architecture)
* [업그레이드](#upgrades)
* [Cloud Manager](#cloud-manager)
* [온보딩](#onboarding)
* [개발](#developing)
* [작업 및 성능](#operations-and-performance)
* [ID 관리](#identity-management)
* [작성 사용자 인터페이스](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>이러한 개요는 완벽하지는 않지만, 개요를 제공하기 위한 것입니다.

>[!NOTE]
>
>온-프레미스 및 관리 서비스 버전에 대한 자세한 내용은 [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=ko-KR).

## 아키텍처 {#architecture}

>[!NOTE]
>
>자세한 내용은 [아키텍처](/help/overview/architecture.md).

이제 AEM as a Cloud Service에는

* AEM 이미지의 수가 다양한 동적 아키텍처가 있습니다.

![동적 아키텍처](assets/introduction-03.png "동적 아키텍처")

이 아키텍처는

* *실제* 트래픽과 *실제* 활동을 기반으로 크기가 조절됩니다.

* 필요한 경우에만 실행되는 개별 인스턴스를 포함합니다.

* 모듈식 애플리케이션을 사용합니다.

* 작성 클러스터를 기본값으로 포함합니다. 이로 인해 유지 관리 작업의 다운타임이 줄어듭니다.

따라서 다양한 사용 패턴을 자동으로 적용할 수 있습니다.

![다양한 사용 패턴을 위한 자동 크기 조절](assets/introduction-04.png "다양한 사용 패턴을 위한 자동 크기 조절")


## AEM 업데이트 {#aem-updates}

>[!NOTE]
>자세한 내용은 [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md).

이제 AEM as a Cloud Service에서는 CI/CD(Continuous Integration and Continuous Delivery)를 사용하여 프로젝트가 최신 AEM 버전에 있는지 확인합니다. 즉, 프로덕션 및 스테이지 인스턴스가 사용자를 위한 서비스를 중단 없이 최신 AEM 버전으로 업데이트됩니다.

>[!NOTE]
> 프로덕션 환경에 대한 업데이트가 실패하면 Cloud Manager는 스테이지 환경을 자동으로 롤백합니다. 이 작업은 업데이트가 완료된 후 스테이지와 프로덕션 환경이 모두 동일한 AEM 버전에 있는지 확인하기 위해 자동으로 수행됩니다.

AEM 버전 업데이트는 다음 두 가지 유형으로 제공됩니다.

* **AEM 푸시 업데이트**

   * 매일 출시할 수 있습니다.
   * 최신 버그 수정 및 보안 업데이트를 포함한 대부분의 유지 관리.

      변경 사항이 정기적으로 적용되면 점진적 영향을 주므로 서비스에 미치는 영향을 줄일 수 있습니다.

* **새로운 기능 업데이트**

   * 예측 가능한 월별 일정을 통해 릴리스됩니다.

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager는 인스턴스에 대한 모든 업데이트를 제어하므로 AEM as a Cloud Service의 연속 업그레이드 접근 방식에 필수적인 요소입니다. 이는 필수 사항입니다.

새로운 버전의 클라우드 서비스를 사용할 수 있는 경우 Adobe에서 업데이트를 트리거할 수 있습니다. 또는 Cloud Manager에서 제공하는 파이프라인을 사용하여 애플리케이션 업데이트를 트리거할 수 있습니다.

Cloud Manager는

* AEM 프로그램 및 환경을 관리하는 데 사용됩니다.

* AEM as a Cloud Service의 필수 구성 요소 새로운 각 임차인이 먼저 Cloud Manager 액세스 권한을 제공받습니다.

* 운영 및 개발 직원을 위한 단일 엔트리 레벨 솔루션

특히, Cloud Manager에서 만들 수 있는 AEM 프로그램의 수와 유형은 다음 중 하나를 파생시킵니다.

* 고객 사용권 계약에 따르면

* AEM as a Cloud Service이 활성화 또는 교육을 위해 사용될 때 내부 제어 행위자로부터

* Adobe.com에서 시작된 시험과 같은 외부 제어 프로세스에서

Cloud Manager는 AEM as a Cloud Service의 주요 구성 요소를 만들고 구성할 수 있는 셀프 서비스 포털로 발전했습니다.

* 새 프로그램을 만들고 관리합니다. 을(를) 참조하십시오. [프로그램 및 프로그램 유형 이해](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/understand-program-types.md) 자세한 내용

* 이러한 프로그램 내에서 AEM 환경을 만들고 관리합니다. 을(를) 참조하십시오. [환경 관리](/help/implementing/cloud-manager/manage-environments.md) 자세한 내용

* 고객 코드 및 관련 구성을 특정 환경에 배포하기 위한 파이프라인을 만들고 관리합니다. 을(를) 참조하십시오. [CI-CD 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 자세한 내용

* 이러한 구성 요소에 대한 중요한 라이프사이클 이벤트(예: 제품 업데이트)에 대한 알림을 받습니다.

Cloud Manager는 많은 지역 간에 데이터 센터에서 환경을 만들어 글로벌 범위를 제공합니다. CDN Point of Presence(PoPs)는 전 세계 고객을 위해 지연 시간이 짧은 컨텐츠 전달을 보장합니다.


## 온보딩 {#onboarding}

>[!NOTE]
>
>자세한 내용은 [온보딩](/help/onboarding/home.md).

AEM 프로젝트를 시작하고 관리하는 것은 Adobe이 많은 측면을 담당하므로 AEM as a Cloud Service를 사용할 때 간단합니다.

* 기준선 AEM 이미지는 특정 사용 사례에 맞게 최적화되어 있습니다.

* 수동 구성 작업 중 많은 작업이 중복되었습니다.

현재는 크게 다릅니다.

* 모든 전제 조건을 충족하는 평가 단계 다음을 포함합니다. 예:

   * 법적 요구 사항

   * 계약 계약

   * 고객이 지정한 기존 컨텐츠 및/또는 코드에 대한 기술 요구 사항

* 배포 요구 사항:

   * 코드 업데이트 이전 버전의 AEM용으로 개발된 모든 고객 애플리케이션은 검토 및 업데이트해야 합니다.

   * 컨텐츠 마이그레이션

## 개발 {#developing}

>[!NOTE]
>
>자세한 내용은 [개발 지침](/help/implementing/developing/introduction/development-guidelines.md) 및 [개발 - WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

AEM as a Cloud Service을 지원하는 새 아키텍처에는 전체 개발자 경험에 대한 몇 가지 주요 변경 사항이 포함되어 있습니다. AEM as a Cloud Service의 주요 목표 중 하나는 경험 있는 고객(AEM을 온-프레미스 또는 Adobe Managed Services의 컨텍스트에서 사용함)이 사용자 지정된 코드의 대부분을 다시 작성하지 않고도 가능한 한 빨리 AEM as a Cloud Service으로 마이그레이션할 수 있도록 하는 것입니다. 그러나 일부 조정이 여전히 필요할 수 있습니다.

### 클라우드 개발 {#aem-as-a-cloud-service-developing-cloud-development}

AEM as a Cloud Service에서 실행되는 기존 AEM 애플리케이션의 경우 다음 단계가 필요합니다.

* 애플리케이션 코드 및 구성은 연결된 Cloud Manager 프로그램의 Git 코드 리포지토리에 저장해야 합니다.
* 애플리케이션 코드와 구성은 기준 요소 AEM 이미지의 최신 버전과 호환되어야 합니다(매일 변경될 수 있음).
   * 고객 애플리케이션은 Cloud Manager 환경과 연결된 Cloud Manager 파이프라인을 사용하여 작성하고 배포해야 합니다.
* 고객 애플리케이션은 파이프라인에 적용되는 모든 코드 품질, 보안 및 성능 게이트를 전달해야 합니다.
* 고객 애플리케이션용으로 만들어진 이미지는 Cloud Manager 파이프라인에 의해 배포되어야 합니다.

이 프로세스를 일반적으로 클라우드 우선 개발이라고 합니다. 종단 간 지속 시간은 애플리케이션의 복잡성에 따라 20~50분 정도 걸릴 것으로 예상되므로 클라우드에서 보류 중인 코드 및 구성 변경을 시도하기 전에 신속한 개발 방법론을 수용해야 합니다.

OSGI 번들 및 관련 구성이 관리되는 웹 콘솔 및 이전에 AEM QuickStart의 일부로 AEM as a Cloud Service 환경의 사용자가 더 이상 직접 액세스할 수 없습니다. 새 개발자 콘솔을 사용하여 이 인터페이스에 계속 읽기 전용 모드로 액세스할 수 있습니다. 이 콘솔을 사용하여 개발자는 작성자 또는 게시 서비스의 특정 노드를 선택하고 직접 로그인한 다음, 기본적으로 차단된 영역에 액세스할 수 있습니다.

>[!NOTE]
>
>참조 - [OSGi 구성](/help/implementing/deploying/overview.md#osgi-configuration)

개발자에게 공통되는 또 다른 요구 사항은 다양한 환경의 로그 파일에 빠르게 액세스하는 것입니다. AEM as a Cloud Service을 사용하면 작성 및 게시 노드에 있는 다른 노드의 로그 파일을 Cloud Manager를 통해 다운로드하거나 API를 통해 사용할 수 있습니다.

코드와 컨텐츠가 명확히 구분되어 개발자는 배포의 일부로 컨텐츠를 업데이트하는 특정 프로세스를 사용할 수 있습니다. 가변 콘텐츠에 대한 일반적인 사용 사례는 다음과 같습니다.

* 표준 *기본* 고객 프로젝트에 포함된 컨텐츠(예: 폴더, 템플릿, 워크플로우 등)

* 검색 색인 정의

* ACL 및 권한

* 서비스 사용자 및 사용자 그룹

### 로컬 개발 {#aem-as-a-cloud-service-developing-local-development}

신속한 반복 및 개발을 지원하기 위해 AEM as a Cloud Service 컨텍스트 외부에서 AEM 애플리케이션을 개발할 수도 있습니다. 이를 위해 개발자가 다음 가공물을 사용할 수 있습니다.

* AEM as a Cloud Service QuickStart: a `.jar` 동일한 기능 및 API 면을 사용하는 최신 AEM 코드 베이스의 독립형 설치 프로그램.

* AEM as a Cloud Service Dispatcher SDK: 로컬에서 Dispatcher 구성을 테스트 및 확인하는 이미지 기반 프로세스입니다

>[!NOTE]
>
>Cloud QuickStart는 모든 AEM Sites 및 AEM Assets 기능을 허용하지 않습니다. 대부분의 확장을 개발 및 테스트할 수 있는 간단한 작성 환경으로 구성됩니다.

## 작업 및 성능 {#operations-and-performance}

>[!NOTE]
>
>For further details start with [Backup](/help/operations/backup.md), [Indexing](/help/operations/indexing.md), and [other Maintenance Tasks](/help/operations/maintenance.md).

AEM as a Cloud Service을 사용하면 이러한 작업이 자동화되므로 더 이상 서비스를 중단할 필요가 없습니다.

다음 영역에서 다음을 수행합니다.

* 많은 작업이 자동화되었습니다.

* 토폴로지는 최대 복원력과 효율성을 제공하도록 최적화되었습니다. 예를 들어 binaryless 복제가 기본값입니다.

* 큐, 작업 및 대량 처리 작업과 같은 로드가 많은 작업이 공유 및 전용 마이크로 서비스에서 처리할 수 있도록 핵심 AEM 인스턴스에서 이동되었습니다.

AEM as a Cloud Service에 대한 작업도 새로운 모니터링, 보고 및 경고 인프라에서 지원됩니다. 이를 통해 Adobe SRE(Site 신뢰성 엔지니어)는 사전 예방적으로 서비스 상태를 유지할 수 있습니다. 그 건축의 다양한 요소들은 다양한 건강검사를 갖추고 있다. 어떤 이유로 아키텍처의 특정 노드가 적절하지 않다고 판단되면 서비스에서 제거되고 자동으로 새로운 건강한 노드로 대체됩니다.

## ID 관리 {#identity-management}

>[!NOTE]
>
>자세한 내용은 [보안 - IMS 지원](/help/security/ims-support.md).

AEM as a Cloud Service에 대한 주요 변경 사항은 작성 계층에 액세스하기 위해 Adobe ID를 완벽하게 통합한 것입니다.

이를 위해서는 [Adobe 관리 콘솔](https://helpx.adobe.com/kr/enterprise/using/admin-console.html) 사용자 및 사용자 그룹 관리를 위한 것입니다. 사용자 프로필 정보가 모든 클라우드 서비스에서 공유되도록 Adobe Identity Management 시스템(IMS)에서 중앙 집중화되므로 사용자 계정을 사용하면 사용자가 Adobe 제품 및 서비스에 액세스할 수 있습니다. AEM에 대한 액세스 권한이 할당되면 사용자 계정을 AEM as a Cloud Service에서 참조(전과 같이)할 수 있습니다. 예를 들어 AEM 보안 사용자 인터페이스에서 역할 및 권한을 정의하는 데 사용됩니다.

여기에는 다음과 같은 이점이 결합됩니다.

* IMS(Adobe Identity Management System)를 사용하여 모든 Adobe 클라우드 애플리케이션에서 단일 사인온을 제공합니다.

* AEM의 각 특정 인스턴스에 대해 로컬에 남아 있는 사용자 환경 설정 as a Cloud Service.

## 작성 사용자 인터페이스 {#authoring-user-interface}

>[!NOTE]
>
>자세한 내용은 [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) 출발점이 좋군요

사이트 및 자산 둘 다에 대한 작성 UI(사용자 인터페이스)의 기본 원칙은 이전에 AEM을 사용한 모든 사용자에게 매우 익숙할 것입니다.

가장 큰 차이점은 UI가 순전히 터치 방식입니다. 클래식 UI는 더 이상 사용할 수 없습니다. 그렇지 않으면 기본 사항은 변경되지 않고 작은 변경 사항만 표시됩니다.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites as a Cloud Service을 사용하면 AEM 컨텐츠 관리 시스템의 강력한 기능을 AEM 디지털 자산 관리와 결합하여 고객에게 개인화된 컨텐츠 중심의 경험을 제공할 수 있습니다.

자세한 내용은 개요 를 참조하십시오. [사이트 변경 사항](/help/sites-cloud/sites-cloud-changes.md).

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service은 클라우드 기반의 PaaS 솔루션을 제공하여 빠르고 효과적으로 디지털 자산 관리 및 Dynamic Media 작업을 수행할 수 있을 뿐만 아니라 항상 최신, 항상 사용 가능하고 항상 학습되는 시스템 내에서 AI/ML과 같은 차세대 스마트 기능도 사용할 수 있습니다.

자산 서비스에는 클라우드의 차세대 자산 처리 및 고성능 자산 수집 및 검색이 포함됩니다.

자세한 내용은 [자산 개요 및 소개 as a Cloud Service](/help/assets/overview.md).

## Adobe Experience Manager as a Cloud Service 알기 {#getting-to-know-aem-as-cloud-service}

자세한 내용은 다음을 참조하십시오.

* [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)
* Adobe Experience Manager as a Cloud Service [아키텍처](/help/overview/architecture.md)
* [AEM as a Cloud Service에 대한 주목할 만한 변경 사항(릴리스 노트)](/help/release-notes/aem-cloud-changes.md)
* [ AEM Sites as a Cloud Service에 대한 주요 변경 사항](/help/sites-cloud/sites-cloud-changes.md)
* [AEM Assets as a Cloud Service에 대한 주요 변경 사항](/help/assets/assets-cloud-changes.md)
* [AEM Assets as a Cloud Service 소개](/help/assets/overview.md)
* [Adobe Experience Manager as a Cloud Service 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

>[!TIP]
>
>AEM as a Cloud Service에 대한 개요를 보고 를 검토하여 빠르게 온보딩할 수 있습니다. [온보딩 여정.](/help/journey-onboarding/home.md)
>
>이미 온보딩되었거나 AEM 기능 테스트를 시작할 준비가 되었습니까? 설치 [AEM 참조 데모 추가 기능](/help/journey-sites/demos-add-on/overview.md) 풍부한 예를 사용하여 AEM의 강력한 기능을 살펴보십시오.