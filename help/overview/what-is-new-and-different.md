---
title: 차이점 및 새로운 기능 - Cloud Service의 Adobe Experience Manager
description: 'Cloud Service의 차이점과 새로운 기능 - Adobe Experience Manager(AEM)입니다. '
translation-type: tm+mt
source-git-commit: b77113ccc55f2063c684d49e2babdd7563b9d6fc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 새로운 기능 및 차이점 {#what-is-new-and-what-is-different}

수년 동안 AEM은 다음 두 가지 모두를 사용할 수 있었습니다.

* On-Premise

* 관리 서비스로

이러한 이전 접근 방식과 Cloud Service의 AEM 간에는 본질적인 차이가 있습니다.

* [아키텍처](#architecture)
* [업그레이드](#upgrades)
* [Cloud Manager](#cloud-manager)
* [온보딩](#onboarding)
* [개발](#developing)
* [운영 및 성능](#operations-and-performance)
* [ID 관리](#identity-management)
* [작성 사용자 인터페이스](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>이러한 개요는 완벽하지는 않지만 소개를 위해 작성되었습니다.

>[!NOTE]
>
>온-프레미스 및 관리 서비스 버전에 대한 자세한 내용은 [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html)에 대한 설명서를 참조하십시오.

## 아키텍처 {#architecture}

>[!NOTE]
>
>자세한 내용은 [아키텍처](/help/core-concepts/architecture.md)를 참조하십시오.

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
>자세한 내용은 [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md)를 참조하십시오.

이제 Cloud Service으로 AEM은 지속적인 통합 및 지속적인 전달(CI/CD)을 사용하여 프로젝트가 최신 AEM 버전에 있는지 확인합니다. 즉, 프로덕션 및 스테이지 인스턴스는 사용자를 위한 서비스 중단 없이 최신 AEM 버전으로 업데이트됩니다.

>[!NOTE]
> 프로덕션 환경에 대한 업데이트가 실패하면 Cloud Manager는 자동으로 스테이지 환경을 롤백합니다. 이 작업은 업데이트가 완료된 후 스테이지와 프로덕션 환경 모두 동일한 AEM 버전을 사용하도록 자동으로 수행됩니다.

AEM 버전 업데이트는 다음 두 가지 유형으로 구성됩니다.

* **AEM 푸시 업데이트**

   * 일일 기준으로 출시될 수 있습니다.
   * 최신 버그 수정 및 보안 업데이트를 비롯한 대부분의 유지 관리.

      변경 사항이 정기적으로 적용되므로 서비스 영향이 점차 증가하고 있습니다.

* **새로운 기능 업데이트**

   * 예측 가능한 월별 일정을 통해 릴리스됩니다.

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager는 인스턴스에 대한 모든 업데이트를 제어하므로 AEM의 지속적인 업그레이드 방식에 있어 없어서는 안 될 필수 사항입니다.

새로운 버전의 클라우드 서비스를 사용할 수 있을 때 업데이트를 Adobe에 의해 트리거할 수 있습니다. 또는 Cloud Manager에서 제공하는 파이프라인을 사용하여 애플리케이션 업데이트를 트리거할 수 있습니다.

클라우드 관리자:

* AEM 프로그램 및 환경을 관리하는 데 사용됩니다.

* Cloud Service의 필수 구성 요소각 새 테넌트가 먼저 클라우드 관리자 액세스를 위해 프로비저닝된 후

* 운영 및 개발 담당 직원을 위한 단일 시작 지점

특히, Cloud Manager에서 만들 수 있는 AEM 프로그램의 수와 유형은 다음 중 하나를 파생합니다.

* 고객 라이센스 계약,

* Cloud Service으로 AEM을 활성 또는 트레이닝에 사용할 때 내부 연기자

* 시험버전과 같은 외부 기반 프로세스에서 Adobe.com에서 시작되었습니다.

Cloud Manager는 Cloud Service의 기본 구성 요소를 만들고 구성할 수 있는 셀프 서비스 포털로 발전했습니다.

* 새 프로그램 만들기 및 관리 자세한 내용은 [프로그램 및 프로그램 유형 이해](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md)를 참조하십시오.

* 이러한 프로그램 내에서 AEM 환경을 만들고 관리합니다. 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md)를 참조하십시오.

* 고객 코드 및 관련 구성을 특정 환경에 배포하기 위한 파이프라인을 만들고 관리합니다. 자세한 내용은 [CI-CD 파이프라인 구성](/help/implementing/cloud-manager/configure-pipeline.md)을 참조하십시오.

* 이러한 구성 요소에 대한 중요한 라이프사이클 이벤트(예: 제품 업데이트)에 대한 알림을 받습니다.

Cloud Manager는 다양한 지역에 걸쳐 데이터 센터에 환경을 생성하여 글로벌 지원 서비스를 제공합니다. PoPs(CDN Points of Presence)는 전 세계 고객을 위해 낮은 지연 시간 컨텐츠 전달을 보장합니다.

>[!NOTE]
>AEM에서 Cloud Manager를 Cloud Service으로 시작하려면 [Cloud Service](/help/onboarding/getting-access-to-aem-in-cloud/navigation.md)으로 Experience Manager 액세스를 참조하십시오.

## 온보딩 {#onboarding}

>[!NOTE]
>
>자세한 내용은 [온보딩](/help/onboarding/home.md)을 참조하십시오.

Adobe으로 AEM을 클라우드 서비스로 사용하는 경우 AEM 프로젝트를 시작 및 관리하는 것은 여러 가지 측면에서 책임집니다.

* 기준선 AEM 이미지는 특정 사용 사례에 맞게 최적화됩니다.

* 수동 구성 작업 중 상당수가 중복되었습니다.

그것은 또한 지금 있는 것과 크게 다르다.

* 모든 전제 조건이 충족되도록 하는 평가 단계포함을 예로 들면 다음과 같습니다.

   * 법적 요건

   * 계약 계약

   * 고객이 맞춤화한 기존 컨텐츠 및/또는 코드에 대한 기술 요구 사항

* 배포 요구 사항:

   * 코드 업데이트;이전 버전의 AEM용으로 개발된 모든 고객 애플리케이션을 검토하고 업데이트해야 합니다.

   * 콘텐츠 마이그레이션

## 개발 {#developing}

>[!NOTE]
>
>자세한 내용은 [개발 지침](/help/implementing/developing/introduction/development-guidelines.md) 및 [개발 - WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)로 시작할 수 있습니다.

AEM을 Cloud Service으로 지원하는 새로운 아키텍처에는 전반적인 개발자 경험에 대한 몇 가지 주요 변경 사항이 포함됩니다. Cloud Service의 주요 목표 중 하나는 경험 있는 고객(AEM을 온-프레미스 또는 Adobe Managed Services 컨텍스트에서 사용)이 사용자 지정된 코드의 대량 쓰기를 수행하지 않고도 가능한 한 빨리 AEM으로 마이그레이션할 수 있도록 허용하는 것입니다. 그러나 일부 조정은 여전히 필요할 수 있습니다.

### 클라우드 개발 {#aem-as-a-cloud-service-developing-cloud-development}

기존 AEM 응용 프로그램이 Cloud Service으로 AEM에서 실행되려면 다음 단계가 필요합니다.

* 응용 프로그램 코드와 구성은 연결된 Cloud Manager 프로그램의 Git 코드 리포지토리에 저장해야 합니다.
* 응용 프로그램 코드와 구성은 기본 AEM 이미지의 최신 버전과 호환되어야 합니다(매일 변경될 수 있음).
   * 고객 애플리케이션은 Cloud Manager 환경과 연결된 Cloud Manager 파이프라인을 사용하여 구축 및 배포해야 합니다.
* 고객 애플리케이션은 파이프라인에 적용되는 모든 코드 품질, 보안 및 성능 게이트를 전달해야 합니다.
* 고객 애플리케이션에 맞게 제작된 이미지는 Cloud Manager 파이프라인에서 배포해야 합니다.

이 프로세스를 클라우드 우선 개발이라고 합니다. 종단 간 지속 시간은 몇 분(애플리케이션의 복잡성에 따라 20~50분)이 소요되므로 대기 중인 코드 및 구성 변경 사항을 클라우드에서 시도하기 전에 신속한 개발 방법론을 채택해야 합니다.

OSGI 번들 및 관련 구성이 관리되고 이전에 AEM QuickStart에 포함되었던 웹 콘솔은 더 이상 Cloud Service 환경으로 AEM 사용자가 직접 액세스할 수 없습니다. 이 인터페이스는 새 개발자 콘솔을 사용하여 읽기 전용 모드에서 액세스할 수 있습니다. 이 콘솔에서 개발자는 작성자 또는 게시 서비스의 특정 노드를 선택하여 직접 로그인한 다음 기본적으로 차단된 영역에 액세스할 수 있습니다.

>[!NOTE]
>
>[OSGi 구성](/help/implementing/deploying/overview.md#osgi-configuration)도 참조하십시오.

개발자에게 가장 일반적으로 요구되는 또 다른 사항은 다양한 환경의 로그 파일에 신속하게 액세스하는 것입니다. AEM을 Cloud Service으로 사용하면 작성자 및 게시 노드의 다른 노드의 로그 파일을 Cloud Manager를 통해 다운로드할 수 있는 파일 형식 또는 API를 통해 사용할 수 있습니다.

코드와 컨텐츠가 명확히 구분되어 있으므로 개발자는 배포의 일부로 컨텐츠를 업데이트하는 특정 프로세스를 사용할 수 있습니다. 변경 가능한 컨텐츠의 일반적인 사용 사례는 다음과 같습니다.

* 고객 프로젝트에 포함된 표준 *기본* 컨텐츠(예: 폴더, 템플릿, 워크플로우 등)

* 색인 정의 검색

* ACL 및 권한

* 서비스 사용자 및 사용자 그룹

### 로컬 개발 {#aem-as-a-cloud-service-developing-local-development}

신속한 반복 및 개발을 지원하기 위해 Cloud Service 컨텍스트에서 AEM 외부에서 AEM 애플리케이션을 개발할 수도 있습니다. 따라서 개발자는 다음 아티팩트를 사용할 수 있습니다.

* Cloud Service QuickStart로 AEM:동일한 기능 및 API 표면을 사용하는 최신 AEM 코드 베이스의 `.jar` 기반 독립 실행형 설치 프로그램.

* Cloud Service Dispatcher SDK로 AEM:로컬에서 Dispatcher 구성을 테스트 및 확인하는 이미지 기반 프로세스

>[!NOTE]
>
>Cloud QuickStart는 모든 AEM Sites 및 AEM Assets 기능을 허용하지 않습니다. 대부분의 익스텐션을 개발 및 테스트할 수 있는 간단한 작성 환경으로 구성됩니다.

## 작업 및 성능 {#operations-and-performance}

>[!NOTE]
>
>자세한 내용은 [백업](/help/operations/backup.md), [인덱싱](/help/operations/indexing.md) 및 [기타 유지 관리 작업](/help/operations/maintenance.md)으로 시작합니다.

Cloud Service으로 AEM을 사용하면 이러한 작업이 자동화되므로 서비스를 더 이상 중단할 필요가 없습니다.

다음 영역에서 다음을 수행합니다.

* 많은 작업이 자동화되었습니다.

* 토폴로지는 최대 복구 및 효율성을 위해 최적화됩니다.예를 들어 바이너리스 복제가 기본값입니다.

* 큐, 작업 및 벌크 처리 작업과 같은 무거운 로드 작업이 핵심 AEM 인스턴스에서 이동하여 공유 및 전용 마이크로 서비스에 의해 처리됩니다.

새로운 모니터링, 보고 및 경고 인프라에서 AEM을 Cloud Service으로 사용할 수도 있습니다. 이를 통해 Adobe SRE(Site 신뢰성 엔지니어)가 서비스를 원활하게 유지할 수 있습니다. 그 건축의 여러 요소에는 다양한 건강검진이 있다. 어떤 이유로 아키텍처의 특정 노드가 건강하지 않다고 판단되는 경우 서비스에서 해당 노드가 제거되고 자동으로 새로운 건강한 노드로 대체됩니다.

## ID 관리 {#identity-management}

>[!NOTE]
>
>자세한 내용은 [보안 - IMS 지원](/help/security/ims-support.md)을 참조하십시오.

Cloud Service로서 AEM의 주요 변경 사항은 작성 계층에 액세스하기 위해 Adobe ID를 완벽하게 통합하는 것입니다.

이렇게 하려면 사용자 및 사용자 그룹을 관리하기 위해 [Adobe 관리 콘솔](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을 사용해야 합니다. 사용자 프로필 정보는 모든 클라우드 서비스에서 공유되도록 Adobe Identity Management System(IMS)에 중앙 집중화되므로 사용자 계정을 통해 Adobe 제품 및 서비스에 액세스할 수 있습니다. AEM에 대한 액세스 권한이 할당되면 사용자 계정을 Cloud Service으로 AEM에서 참조할 수 있습니다(이전과 같이).예를 들어 AEM Security 사용자 인터페이스에서 역할 및 권한을 정의하는 경우

여기에는 다음과 같은 이점이 포함됩니다.

* Adobe Identity Management System(IMS)을 사용하여 모든 Adobe 클라우드 애플리케이션에서 Single Sign-On을 제공합니다.

* AEM의 각 특정 인스턴스에 Cloud Service으로 남아있는 사용자 환경 설정

## 작성 사용자 인터페이스 {#authoring-user-interface}

>[!NOTE]
>
>자세한 내용은 [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md)를 시작하는 것이 좋습니다.

사이트 및 자산 모두에 대한 UI(작성 사용자 인터페이스)의 기본 원칙은 이전에 AEM을 사용한 모든 사용자에게 매우 익숙할 것입니다.

주요 차이점은 UI는 터치 기능만 사용하는 것입니다.클래식 UI는 더 이상 사용할 수 없습니다. 그렇지 않은 경우 기본 사항은 변경되지 않고 약간 변경만 가능합니다.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites은 Cloud Service으로 AEM 콘텐츠 관리 시스템의 강력한 기능과 AEM 디지털 에셋 관리 기능을 결합하여 고객에게 개인화된 콘텐츠 중심의 경험을 제공할 수 있도록 지원합니다.

자세한 내용은 [사이트 변경 사항](/help/sites-cloud/sites-cloud-changes.md)의 개요를 참조하십시오.

## AEM Assets {#aem-assets}

Cloud Service의 Adobe Experience Manager Assets는 클라우드 기반의 PaaS 솔루션을 제공하므로 기업은 디지털 에셋 관리 및 Dynamic Media 작업을 신속하고 효율적으로 수행할 수 있을 뿐만 아니라 항상 최신 방식으로 사용할 수 있고 항상 사용할 수 있는 시스템에서 AI/ML과 같은 차세대 스마트 기능을 사용할 수 있습니다.

자산 서비스에는 클라우드의 차세대 에셋 처리 및 고성능 에셋 수집 및 검색이 포함됩니다.

자세한 내용은 [개요 및 Cloud Service](/help/assets/overview.md)로 에셋 소개를 참조하십시오.

## Adobe Experience Manager as a Cloud Service 알기 {#getting-to-know-aem-as-cloud-service}

자세한 내용은 다음을 참조하십시오.

* [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)
* Adobe Experience Manager as a Cloud Service [아키텍처](/help/core-concepts/architecture.md)
* [AEM as a Cloud Service에 대한 주목할 만한 변경 사항(릴리스 노트)](/help/release-notes/aem-cloud-changes.md)
* [ AEM Sites as a Cloud Service에 대한 주요 변경 사항](/help/sites-cloud/sites-cloud-changes.md)
* [AEM Assets as a Cloud Service에 대한 주요 변경 사항](/help/assets/assets-cloud-changes.md)
* [Cloud Service으로 AEM Assets 소개](/help/assets/overview.md)
* [Adobe Experience Manager as a Cloud Service 자습서](https://docs.adobe.com/content/help/ko-KR/experience-manager-learn/cloud-service/overview.html)
