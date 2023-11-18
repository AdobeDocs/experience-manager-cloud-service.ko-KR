---
title: 차이점 및 새로운 기능 - Adobe Experience Manager as a Cloud Service
description: 차이점 및 새로운 기능 - Adobe Experience Manager(AEM) as a Cloud Service
exl-id: d1ce126e-960c-4367-b741-af709dd81010
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '1891'
ht-degree: 93%

---

# 새로운 기능 및 차이점 {#what-is-new-and-what-is-different}

수년 동안 AEM은 다음 두 가지로 사용할 수 있었습니다.

* AEM 온프레미스

* AEM as a Managed Service

이러한 이전 방식과 AEM as a Cloud Service 간에는 다음과 같은 항목에서 본질적인 차이점이 있습니다.

* [아키텍처](#architecture)
* [업그레이드](#upgrades)
* [Cloud Manager](#cloud-manager)
* [온보딩](#onboarding)
* [개발](#developing)
* [작업 및 성능](#operations-and-performance)
* [ID 관리](#identity-management)
* [사용자 인터페이스 작성](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>이러한 개요는 완전하지는 않지만 소개를 제공하기 위해 작성되었습니다.

>[!NOTE]
>
>온프레미스 및 Managed Service 버전에 대한 자세한 내용은 [AEM 6.5 설명서](https://experienceleague.adobe.com/docs/experience-manager-65.html) .

## 아키텍처 {#architecture}

>[!NOTE]
>
>자세한 내용은 [아키텍처](/help/overview/architecture.md).

이제 AEM as a Cloud Service에는

* AEM 이미지의 수가 다양한 다이내믹 아키텍처가 있습니다.

![다이내믹 아키텍처](assets/introduction-03.png "다이내믹 아키텍처")

이 아키텍처는

* *실제* 트래픽과 *실제* 활동을 기반으로 크기가 조절됩니다.

* 필요한 경우에만 실행되는 개별 인스턴스를 포함합니다.

* 모듈식 애플리케이션을 사용합니다.

* 작성 클러스터를 기본값으로 포함합니다. 이로 인해 유지 관리 작업의 다운타임이 줄어듭니다.

따라서 다양한 사용 패턴을 자동으로 적용할 수 있습니다.

![다양한 사용 패턴을 위한 자동 크기 조절](assets/introduction-04.png "다양한 사용 패턴을 위한 자동 크기 조절")


## AEM 업데이트 {#aem-updates}

AEM as a Cloud Service는 이제 지속적인 통합 및 연속 게재(CI/CD)를 사용하여 프로젝트를 가장 최신 AEM 버전에서 작업할 수 있도록 해 줍니다. 이는 프러덕션 및 스테이징 인스턴스가 사용자에 대한 서비스 중단 없이 최신 AEM 버전으로 업데이트된다는 것을 뜻합니다.

>[!NOTE]
>
>프로덕션 환경 업데이트에 실패하는 경우 Cloud Manager에서 자동으로 스테이징 환경을 롤백합니다. 이 작업은 업데이트가 완료된 후 스테이지 및 프로덕션 환경이 동일한 AEM 버전에 있도록 자동으로 수행됩니다.

AEM 버전 업데이트에는 다음과 같은 두 가지 유형이 있습니다.

* **AEM 유지 보수 업데이트**

   * 일별로 릴리스될 수 있습니다.
   * 대부분 유지 관리 목적이며, 최신 버그 수정 및 보안 업데이트가 여기에 포함됩니다.
   * 변경 사항이 정기적으로 적용되므로 최소한의 영향만 미치게 됩니다.

* **새로운 기능 업데이트**

   * 예측 가능한 월별 일정을 통해 릴리스됩니다.

>[!TIP]
>
>자세한 내용은 [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md).

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager는 모든 인스턴스 업데이트를 제어하므로 AEM as a Cloud Service의 지속적인 업그레이드 방식에 필수적입니다.

새 버전의 클라우드 서비스를 사용할 수 있을 때 Adobe에 의해 업데이트가 트리거될 수 있습니다. 또는 Cloud Manager에서 제공하는 파이프라인을 사용하여 애플리케이션 업데이트를 트리거할 수 있습니다.

Cloud Manager의 특징은 다음과 같습니다.

* AEM 프로그램 및 환경 관리에 사용됩니다.

* AEM as a Cloud Service의 필수 구성 요소입니다. 각각의 새 테넌트는 Cloud Manager 액세스에 먼저 프로비저닝됩니다.

* 귀사의 작업 및 개발 팀을 위한 단일 진입점입니다.

특히 Cloud Manager에서 생성될 수 있는 AEM 프로그램의 수 및 유형은 다음 중 하나에서 파생됩니다.

* 고객 라이선싱 계약

* 내부 발생 요소 (AEM as a Cloud Service를 강화 또는 교육용으로 사용하는 경우)

* Adobe.com에서 시작된 체험판과 같은 외부 발생 프로세스

Cloud Manager는 다음과 같은 AEM as a Cloud Service의 주요 구성 요소를 생성하고 구성할 수 있는 셀프서비스 포털로 발전해 왔습니다.

* 새 프로그램 생성 및 관리 자세한 내용은 [프로그램 및 프로그램 유형 이해](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)를 참조하십시오.

* 이들 프로그램에서의 AEM 환경 생성 및 관리 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md)를 참조하십시오.

* 고객 코드 및 관련 구성을 특정 환경에 배포하기 위한 파이프라인 생성 및 관리 자세한 내용은 [CI-CD 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 참조하십시오.

* 이들 구성 요소에 대한 중요 라이프사이클 이벤트 알림 (예: 제품 업데이트)

Cloud Manager는 여러 지역 전역에 걸쳐 데이터센터에 환경을 생성합니다. CDN PoPs(Points of Presence)를 통해 전 세계 고객에게 짧은 지연 시간 내에 콘텐츠를 게재할 수 있습니다.


## 온보딩 {#onboarding}

Adobe에서 많은 측면을 담당하므로 AEM as a Cloud service를 사용하면 AEM 프로젝트를 매우 간단하게 시작하고 관리할 수 있습니다.

* 기준선 AEM 이미지가 특정 사용 사례에 최적화되어 있습니다.

* 많은 수동 구성 작업이 중복되었습니다.

이는 현재와도 상당히 다릅니다.

* 다음과 같은 모든 사전 요구 사항이 충족되었는지 확인하기 위한 평가 단계

   * 법적 요구 사항

   * 계약 조건

   * 고객이 맞춤화한 기존 콘텐츠 및/또는 코드에 대한 기술적 요구 사항

* 배포 요구 사항:

   * 코드 업데이트. 이전 버전의 AEM용으로 개발된 고객 애플리케이션은 검토 및 업데이트되어야 합니다.

   * 콘텐츠 마이그레이션

>[!TIP]
>
>온보딩 프로세스에 대한 전체 개요는 [온보딩 여정](/help/journey-onboarding/overview.md)을 참조하십시오.

## 개발 {#developing}

>[!NOTE]
>
>자세한 내용을 보려면 다음으로 시작할 수 있습니다. [개발 지침](/help/implementing/developing/introduction/development-guidelines.md) 및 [개발 - WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

AEM as a Cloud Service를 지원하는 새 아키텍처에는 전반적인 개발자 경험에 대한 몇 가지 주요 변경 내용이 포함됩니다. AEM as a Cloud Service의 주요 목표 중 하나는 숙련된 고객(온프레미스 또는 Adobe Managed Services의 컨텍스트에서 AEM을 사용한 고객)이 맞춤화된 코드 대부분을 다시 작성하지 않고도 AEM as a Cloud Service로 가능한 한 빨리 마이그레이션할 수 있도록 하는 것입니다. 단, 여전히 일부 조정이 필요할 수 있습니다.

### 클라우드 개발 {#aem-as-a-cloud-service-developing-cloud-development}

기존 AEM 애플리케이션을 AEM as a Cloud Service에서 실행하려면 다음 단계를 수행해야 합니다.

* 애플리케이션 코드 및 구성은 관련 Cloud Manager 프로그램의 Git 코드 저장소에 저장되어야 합니다.
* 애플리케이션 코드 및 구성은 최신 버전의 기준선 AEM 이미지(매일 변경될 수 있음)와 호환되어야 합니다.
   * 고객 애플리케이션은 Cloud Manager 환경과 연계된 Cloud Manager 파이프라인을 사용하여 작성 및 배포되어야 합니다.
* 고객 애플리케이션은 해당 파이프라인에 적용되는 모든 코드 품질, 보안 및 성능 게이트를 통과해야 합니다.
* 고객 애플리케이션에 빌드되는 이미지는 Cloud Manager 파이프라인으로 배포되어야 합니다.

일반적으로 이 프로세스를 클라우드 기반 개발이라고 합니다. 애플리케이션의 복잡성에 따라 전반적인 지속 시간이 20분에서 50분까지 소요될 것으로 예상되므로 클라우드에서 보류 중인 코드 및 구성 변경이 수행되기 전에 신속한 개발 방법을 수용해야 합니다.

AEM as a Cloud Service에서는 OSGi 번들 및 관련 구성이 관리되는 웹 콘솔 및 AEM 빠른 시작의 이전 부분에 더 이상 액세스할 수 없습니다. 새 개발자 콘솔에서는 대부분의 런타임 정보를 위한 읽기 전용 인터페이스를 제공합니다. 개발자는 이 콘솔을 통해 작성자 또는 게시 서비스의 특정 노드를 선택하고 바로 로그인할 수 있으며 관련 정보를 확인할 수 있습니다.

>[!NOTE]
>
>[OSGi 구성](/help/implementing/deploying/overview.md#osgi-configuration)도 살펴보십시오.

개발자에 대한 또 다른 일반적인 요구 사항은 다양한 환경의 로그 파일에 대한 바로 가기입니다. AEM as a Cloud Service를 사용하면 작성자 및 게시 노드에 있는 다양한 노드의 로그 파일을 다운로드 가능한 파일 형식에서 또는 API를 통해 Cloud Manager를 통해 사용할 수 있습니다.

코드와 콘텐츠의 명확하게 분리되어 있으므로 개발자는 특정 프로세스를 사용하여 개발의 일부로 콘텐츠를 업데이트할 수 있습니다. 변경 가능한 콘텐츠의 일반적인 사용 사례는 다음과 같습니다.

* 표준 *기본값* 고객 프로젝트의 일부인 콘텐츠(예: 폴더, 템플릿, 워크플로 등)

* 검색 색인 정의

* ACL 및 권한

* 서비스 사용자 및 사용자 그룹

### 로컬 개발 {#aem-as-a-cloud-service-developing-local-development}

신속한 반복 및 개발 지원을 위해 AEM as a Cloud Service 컨텍스트 외부에서 AEM 애플리케이션을 개발할 수도 있습니다. 이러한 목적으로 개발자는 다음과 같은 아티팩트를 사용할 수 있습니다.

* AEM as a Cloud Service 빠른 시작: 동일한 기능 및 API 영역을 갖춘 최신 AEM 코드 베이스의 `.jar` 기반 독립형 설치 관리자

* AEM as a Cloud Service Dispatcher SDK: 로컬에서의 Dispatcher 구성 테스트 및 유효성 검사를 위한 이미지 기반 프로세스

>[!NOTE]
>
>Cloud QuickStart는 일부 AEM Sites 및 AEM Assets 기능만 허용합니다. 대부분의 확장 기능을 개발 및 테스트할 수 있는 간단한 작성자 환경으로 구성되어 있습니다.

## 작업 및 성능 {#operations-and-performance}

>[!NOTE]
>
>자세한 내용을 보려면 다음으로 시작하십시오. [콘텐츠 복원](/help/operations/backup.md), [색인화](/help/operations/indexing.md), 및 [기타 유지 관리 작업](/help/operations/maintenance.md).

AEM as a Cloud Service를 사용하면 이러한 작업이 자동화되므로 더 이상 서비스를 중단할 필요가 없습니다.

이러한 영역에는 다음과 같은 이점이 있습니다.

* 많은 작업이 자동화됩니다.

* 최대 복원력 및 효율성을 위해 구조가 최적화됩니다. 예를 들어 기본적으로 복제에 이중 작업이 필요하지 않습니다.

* 큐, 작업 및 일괄 처리 작업과 같이 많은 로드가 발생하는 작업이 핵심 AEM 인스턴스에서 제외되어 공유 및 전용 마이크로서비스에서 처리됩니다.

새 모니터링, 보고 및 경고 인프라에서 AEM as a Cloud Service 작업도 지원됩니다. 이를 통해 Adobe SRE(Site Reliability Engineers)가 주도적으로 서비스 상태를 확인할 수 있습니다. 아키텍처의 다양한 요소에는 다양한 상태 검사가 갖추어져 있습니다. 어떤 이유로 아키텍처의 특정 노드가 비정상으로 간주될 경우 서비스에서 제거되며 자동으로 정상적인 새 노드로 교체됩니다.

## ID 관리 {#identity-management}

>[!NOTE]
>
>다음을 참조하십시오 [보안 - IMS 지원](/help/security/ims-support.md).

AEM as a Cloud Service의 주요 변경 내용은 작성자 계층 액세스에 대한 Adobe ID 사용이 완전히 통합된다는 것입니다.

이를 위해서는 사용자 및 사용자 그룹 관리에 [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html)을 사용해야 합니다. 사용자 프로필 정보가 Adobe Identity Management System(IMS)에서 중앙 집중식으로 관리되어 모든 클라우드 서비스에 공유되므로 사용자 계정을 사용하면 사용자가 Adobe 제품 및 서비스에 액세스할 수 있습니다. AEM에 액세스 권한을 할당하면 이전과 동일하게 AEM as a Cloud Service에서 사용자 계정을 참조할 수 있습니다(예: AEM 보안 사용자 인터페이스에서 역할 및 권한을 정의하기 위해).

이렇게 하면 다음과 같은 이점이 있습니다.

* Adobe Identity Management System(IMS)을 사용하여 모든 Adobe 클라우드 애플리케이션에 SSO(Single Sign-On)를 제공할 수 있습니다.

* 사용자 환경 설정을 각각의 특정 AEM as a Cloud Service 인스턴스에 대해 로컬로 유지할 수 있습니다.

## 사용자 인터페이스 작성 {#authoring-user-interface}

>[!NOTE]
>
>자세한 내용은 [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) 는 좋은 시작점입니다.

Sites 및 Assets에 대한 사용자 인터페이스(UI) 작성의 기본 원칙은 이전에 AEM을 사용한 적이 있는 누구에게나 매우 익숙할 것입니다.

주요 차이점은 UI에는 터치 기능만 지원되며, 클래식 UI는 더 이상 사용할 수 없다는 것입니다. 그렇지 않은 경우 기본 사항은 변경되지 않으며 작은 변경만 표시됩니다.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites as a Cloud Service를 사용하면 AEM 콘텐츠 관리 시스템의 기능과 AEM 디지털 자산 관리를 통합하여 고객에게 개인화된 콘텐츠 주도 경험을 제공할 수 있습니다.

자세한 내용은 [Sites 변경 내용](/help/sites-cloud/sites-cloud-changes.md) 개요를 참조하십시오.

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service는 클라우드 기반의 비즈니스용 PaaS 솔루션을 제공하여 빠르고 효과적으로 디지털 자산 관리 및 Dynamic Media 작업을 수행할 뿐만 아니라 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습하는 시스템 내에서 AI/ML과 같은 차세대 스마트 기능도 사용합니다.

Assets 제품에는 클라우드에서의 차세대 자산 프로세싱과 고성능 자산 수집 및 검색 기능이 포함됩니다.

자세한 내용은 [Assets as a Cloud Service 개요 및 소개](/help/assets/overview.md)를 참조하십시오.

## Adobe Experience Manager as a Cloud Service 알아보기 {#getting-to-know-aem-as-cloud-service}

자세한 내용은 다음 문서를 참조하십시오.

* [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)
* Adobe Experience Manager as a Cloud Service [아키텍처](/help/overview/architecture.md)
* [AEM as a Cloud Service에 대한 주요 변경 내용 (릴리스 정보)](/help/release-notes/aem-cloud-changes.md)
* [AEM Sites as a Cloud Service의 주요 변경 사항](/help/sites-cloud/sites-cloud-changes.md)
* [AEM Assets as a Cloud Service에 대한 주요 변경 내용](/help/assets/assets-cloud-changes.md)
* [AEM Assets as a Cloud Service 소개](/help/assets/overview.md)
* [Adobe Experience Manager as a Cloud Service 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

>[!TIP]
>
>AEMas a Cloud Service 에 대한 개요가 있을 때 를 검토하여 빠르게 온보딩할 수 있습니다. [온보딩 여정](/help/journey-onboarding/overview.md).
>
>이미 온보딩했거나 AEM의 기능을 테스트할 준비가 되었습니까? [AEM 참조 데모 추가 기능](/help/journey-sites/demos-add-on/overview.md)을 설치하여 풍부한 예제를 통해 AEM의 강력한 기능을 살펴보십시오.
