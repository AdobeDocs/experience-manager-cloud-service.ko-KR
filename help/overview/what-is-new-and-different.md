---
title: Cloud Service의 차이점과 새로운 점
description: 'What is Different and What is New - as a Cloud Service. '
translation-type: tm+mt
source-git-commit: 52e8cf1e3fb503c1d222a9543cfc1ddfe87132b6
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 10%

---


# 새로운 기능 및 차이점 {#what-is-new-and-what-is-different}

수년 동안 AEM은 다음과 같은 기능을 모두 사용할 수 있습니다.

* On-Premise

* 관리 서비스

이러한 이전 접근 방식과 AEM은 Cloud Service으로 본질적으로 차이가 있습니다.

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
>이러한 개요는 철저하지 않지만, 소개를 하기 위한 것입니다.

>[!NOTE]
>
>온-프레미스 및 관리 서비스 버전에 대한 자세한 내용은 [AEM 6.5](https://helpx.adobe.com/kr/support/experience-manager/6-5.html)에 대한 설명서를 참조하십시오.

## 아키텍처 {#architecture}

>[!NOTE]
>
>자세한 내용은 [Architecture](/help/core-concepts/architecture.md)를 참조하십시오.

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

AEM은 이제 Cloud Service으로 연속 통합 및 연속 배달(CI/CD)을 사용하여 프로젝트가 최신 AEM 버전을 사용하고 있는지 확인합니다. 즉, 프로덕션 및 스테이지 인스턴스는 사용자를 위한 서비스 중단 없이 최신 AEM 버전으로 업데이트됩니다.

>[!NOTE]
> 프로덕션 환경에 대한 업데이트가 실패할 경우 Cloud Manager는 스테이지 환경을 자동으로 롤백합니다. 이 작업은 업데이트가 완료되면 스테이지와 프로덕션 환경 모두 동일한 AEM 버전을 사용하도록 자동으로 수행됩니다.

AEM 버전 업데이트는 다음과 같은 두 가지 유형입니다.

* **AEM 푸시 업데이트**

   * 매일 출시됩니다.
   * 최신 버그 수정 및 보안 업데이트를 비롯한 대부분의 유지 관리

      변경 사항이 정기적으로 적용되면 효과가 증가하므로 서비스에 미치는 영향이 줄어듭니다.

* **새로운 기능 업데이트**

   * 예측 가능한 월별 일정을 통해 출시됩니다.

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager는 모든 인스턴스 업데이트를 제어하므로 Cloud Service의 지속적인 업그레이드 접근 방식에 없어서는 안 될 필수 사항입니다.

새로운 버전의 클라우드 서비스를 사용할 수 있는 경우 Adobe에 의해 업데이트를 트리거할 수 있습니다. 또는 Cloud Manager에서 제공하는 파이프라인을 사용하여 애플리케이션 업데이트를 트리거할 수 있습니다.

클라우드 관리자:

* aem 프로그램 및 환경을 관리하는 데 사용됩니다.

* aem의 Cloud Service의 필수 구성 요소각 새 테넌트는 클라우드 관리자 액세스에 대해 먼저 프로비저닝되며

* 운영 및 개발 담당 직원을 위한 단일 시작 지점

특히, Cloud Manager에서 만들 수 있는 AEM 프로그램의 수와 유형은 다음 중 하나를 파생합니다.

* 고객 라이센스 계약,

* cloud service으로 AEM을 활성 또는 트레이닝으로 사용할 때 내부 연기자

* adobe.com에서 시작된 시험버전과 같은 외부 기반 프로세스에서

Cloud Manager는 다음과 같은 Cloud Service의 기본 구성 요소를 만들고 구성할 수 있는 셀프 서비스 포털로 발전했습니다.

* 새로운 프로그램 제작 및 관리 자세한 내용은 [프로그램 및 프로그램 유형 이해](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md)를 참조하십시오.

* 이러한 프로그램 내에서 AEM 환경을 만들고 관리합니다. 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md)를 참조하십시오.

* 고객 코드 및 관련 구성을 특정 환경에 배포하기 위한 파이프라인을 생성하고 관리합니다. 자세한 내용은 [CI-CD 파이프라인 구성](/help/implementing/cloud-manager/configure-pipeline.md)을 참조하십시오.

* 이러한 구성 요소에 대한 중요한 라이프사이클 이벤트(예: 제품 업데이트)에 대한 알림을 받습니다.

현재 Cloud Manager는 3개의 지역(다음 지역이 더 많음)에서 환경을 만들 수 있습니다.

* 미국(동부)

* EMEA(네덜란드)

* APAC(오스트레일리아)

>[!NOTE]
>AEM에서 Cloud Service으로 Cloud Manager를 시작하려면 [Experience Manager으로 액세스](/help/onboarding/getting-access-to-aem-in-cloud/navigation.md)를 참조하십시오.

## 온보딩 {#onboarding}

>[!NOTE]
>
>자세한 내용은 [온보딩](/help/onboarding/home.md)을 참조하십시오.

Adobe으로 AEM을 클라우드 서비스로 사용하는 경우 AEM 프로젝트를 시작 및 관리하는 것은 여러 가지 측면에서 매우 간단합니다.

* 기준선 AEM 이미지는 특정 사용 사례에 맞게 최적화됩니다.

* 수동 구성 작업 중 상당수가 중복되었습니다.

그것은 또한 지금 있는 것과 크게 다릅니다.

* 모든 전제 조건이 충족되도록 하는 평가 단계포함을 참조하십시오.

   * 법적 요건

   * 계약

   * 고객이 맞춤화한 기존 컨텐츠 및/또는 코드에 대한 기술 요구 사항

* 배포 요구 사항:

   * 코드 업데이트;이전 버전의 AEM용으로 개발된 모든 고객 애플리케이션을 검토하고 업데이트해야 합니다.

   * 콘텐츠 마이그레이션

## 개발 {#developing}

>[!NOTE]
>
>자세한 내용은 [개발 지침](/help/implementing/developing/introduction/development-guidelines.md) 및 [개발 - WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)로 시작할 수 있습니다.

AEM을 Cloud Service으로 지원하는 새로운 아키텍처에는 전반적인 개발자 경험에 대한 몇 가지 주요 변경 사항이 포함됩니다. AEM의 Cloud Service의 주요 목표 중 하나는 경험 많은 고객(AEM을 온-프레미스 또는 Adobe Managed Services 컨텍스트에서 사용)이 사용자 정의된 코드의 상당 부분을 다시 작성하지 않고도 가능한 한 빨리 AEM으로 마이그레이션할 수 있도록 하는 것입니다. 그러나 일부 조정이 필요할 수 있습니다.

### 클라우드 개발 {#aem-as-a-cloud-service-developing-cloud-development}

기존 AEM 응용 프로그램이 AEM에서 Cloud Service으로 실행되려면 다음 단계가 필요합니다.

* 응용 프로그램 코드와 구성은 관련 Cloud Manager 프로그램의 Git 코드 리포지토리에 저장해야 합니다.
* 애플리케이션 코드와 구성은 기준 AEM 이미지의 최신 버전과 호환되어야 합니다(매일 변경될 수 있음).
   * 고객 애플리케이션은 Cloud Manager 환경과 연결된 Cloud Manager 파이프라인을 사용하여 구축 및 배포해야 합니다.
* 고객 애플리케이션은 파이프라인에 적용되는 모든 코드 품질, 보안 및 성능 게이트를 전달해야 합니다.
* 고객 애플리케이션을 위해 만들어진 이미지는 Cloud Manager 파이프라인에 의해 배포되어야 합니다.

이 프로세스를 클라우드 퍼스트 개발이라고 합니다. 종단 간 지속 시간은 몇 분(애플리케이션의 복잡성에 따라 20~50분)이 소요되기 때문에 클라우드에서 보류 중인 코드 및 구성 변경을 시도하기 전에 신속한 개발 방법을 수용해야 합니다.

OSGI 번들 및 관련 구성이 관리되고 이전에 AEM QuickStart의 일부였던 웹 콘솔은 더 이상 AEM 사용자가 Cloud Service 환경으로 직접 액세스할 수 없습니다. 이 인터페이스는 새 개발자 콘솔을 사용하여 읽기 전용 모드로 여전히 액세스할 수 있습니다. 개발자는 이 콘솔을 사용하여 작성자 또는 게시 서비스의 특정 노드를 선택하여 직접 로그인한 다음 기본적으로 차단된 영역에 액세스할 수 있습니다.

>[!NOTE]
>
>[OSGi 구성](/help/implementing/deploying/overview.md#osgi-configuration)도 참조하십시오.

개발자는 다양한 환경의 로그 파일에 신속하게 액세스할 수 있어야 합니다. AEM을 Cloud Service으로 사용할 경우 작성자 및 게시 노드에 있는 다른 노드의 로그 파일은 클라우드 관리자를 통해 다운로드할 수 있는 파일 형식이나 API를 통해 사용할 수 있습니다.

코드와 컨텐츠가 명확히 구분되어 있으므로 개발자는 특정 프로세스를 사용하여 컨텐츠를 배포의 일부로 업데이트할 수 있습니다. 변경 가능한 컨텐츠에 대한 일반적인 사용 사례는 다음과 같습니다.

* 고객 프로젝트의 일부인 표준 *기본* 컨텐츠(예: 폴더, 템플릿, 워크플로우 등)

* 색인 정의 검색

* ACL 및 권한

* 서비스 사용자 및 사용자 그룹

### 로컬 개발 {#aem-as-a-cloud-service-developing-local-development}

신속한 반복 및 개발을 지원하기 위해 AEM 외부 AEM 애플리케이션을 Cloud Service 컨텍스트으로 개발할 수도 있습니다. 따라서 개발자는 다음 객체를 사용할 수 있습니다.

* AEM은 Cloud Service QuickStart로,동일한 기능 및 API 표면을 사용하는 최신 AEM 코드 베이스의 `.jar` 기반 독립형 설치 프로그램.

* Cloud Service Dispatcher SDK로서 AEM:로컬에서 Dispatcher 구성을 테스트 및 검증하기 위한 이미지 기반 프로세스

>[!NOTE]
>
>클라우드 QuickStart는 모든 AEM Sites 및 AEM Assets 기능을 허용하지 않습니다. 대부분의 익스텐션을 개발 및 테스트할 수 있는 간단한 작성 환경으로 구성됩니다.

## 작업 및 성능 {#operations-and-performance}

>[!NOTE]
>
>자세한 내용은 [백업](/help/operations/backup.md), [인덱싱](/help/operations/indexing.md) 및 [기타 유지 관리 작업](/help/operations/maintenance.md)으로 시작합니다.

AEM을 Cloud Service으로 사용하는 경우 이러한 작업이 자동화되므로 더 이상 서비스를 중단할 필요가 없습니다.

다음 영역에서 다음을 수행합니다.

* 많은 작업이 자동화되었습니다.

* 토폴로지는 최대한의 복원력과 효율성을 위해 최적화되어 있습니다.예를 들어 바이너리스 복제가 기본값입니다.

* 큐, 작업 및 벌크 처리 작업과 같은 무거운 로드 작업은 공유 및 전용 마이크로 서비스에 의해 처리되도록 핵심 AEM 인스턴스에서 옮겨졌습니다.

새로운 모니터링, 보고 및 경고 인프라에서는 AEM의 Cloud Service 작업도 지원됩니다. Adobe SRE(Site 신뢰성 엔지니어)가 서비스를 원활하게 유지할 수 있습니다. 그 건축의 다양한 요소에는 다양한 건강검진이 있다. 어떤 이유로 아키텍처의 특정 노드가 건강하지 않다고 여겨지면 서비스에서 제거되고 자동으로 새로운 건강한 노드로 대체됩니다.

## ID 관리 {#identity-management}

>[!NOTE]
>
>자세한 내용은 [보안 - IMS 지원](/help/security/ims-support.md)을 참조하십시오.

Cloud Service의 큰 변화는 작성 계층에 액세스하기 위해 Adobe ID를 완전히 통합된 것입니다.

이렇게 하려면 사용자 및 사용자 그룹을 관리하기 위해 [Adobe 관리 콘솔](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을 사용해야 합니다. 사용자 계정은 사용자 프로필 정보가 모든 클라우드 서비스에서 공유되도록 Adobe Identity Management 시스템(IMS)에서 중앙 집중화되므로 사용자가 Adobe 제품 및 서비스에 액세스할 수 있도록 합니다. AEM에 대한 액세스 권한이 할당되면 사용자 계정을 이전 버전처럼 AEM에서 Cloud Service으로 참조할 수 있습니다.예를 들어 AEM Security 사용자 인터페이스에서 역할 및 권한을 정의하는 경우

여기에는 다음과 같은 이점이 포함됩니다.

* Adobe Identity Management 시스템(IMS)을 사용하여 모든 Adobe 클라우드 애플리케이션에서 Single Sign-On을 제공합니다.

* 사용자 환경 설정은 AEM의 각 특정 인스턴스에 Cloud Service으로 남아 있습니다.

## 작성 사용자 인터페이스 {#authoring-user-interface}

>[!NOTE]
>
>자세한 내용은 [기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md)를 시작하는 것이 좋습니다.

사이트 및 자산 모두에 대해 UI(작성 사용자 인터페이스)의 기본 원칙은 이전에 AEM을 사용한 모든 사용자에게 매우 익숙할 것입니다.

주요 차이점은 UI가 터치를 사용하는 것입니다.클래식 UI는 더 이상 사용할 수 없습니다. 그렇지 않으면 기본 사항은 변경되지 않고 작은 변경 사항만 표시됩니다.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites은 Cloud Service의 강력한 AEM 콘텐츠 관리 시스템과 AEM 디지털 에셋 관리를 결합하여 개인화된 콘텐츠 중심의 경험을 고객에게 제공할 수 있도록 지원합니다.

자세한 내용은 [사이트 변경 사항](/help/sites-cloud/sites-cloud-changes.md)의 개요를 참조하십시오.

## AEM Assets {#aem-assets}

Cloud Service의 Adobe Experience Manager 에셋은 기업이 디지털 에셋 관리 및 다이내믹한 미디어 작업을 신속하고 효율적으로 수행할 수 있을 뿐만 아니라 항상 최신, 항상 사용 가능하고 항상 사용 가능한 시스템에서 AI/ML과 같은 차세대 스마트 기능을 사용할 수 있도록 클라우드 기반의 SaaS 솔루션을 제공합니다.

자산 서비스에는 클라우드의 차세대 에셋 처리 및 고성능 에셋 수집 및 검색이 포함됩니다.

자세한 내용은 [개요 및 Cloud Service으로 자산 소개](/help/assets/overview.md)를 참조하십시오.

## Adobe Experience Manager as a Cloud Service 알기 {#getting-to-know-aem-as-cloud-service}

자세한 내용은 다음을 참조하십시오.

* [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)
* Adobe Experience Manager as a Cloud Service [아키텍처](/help/core-concepts/architecture.md)
* [AEM as a Cloud Service에 대한 주목할 만한 변경 사항(릴리스 노트)](/help/release-notes/aem-cloud-changes.md)
* [ AEM Sites as a Cloud Service에 대한 주요 변경 사항](/help/sites-cloud/sites-cloud-changes.md)
* [AEM Assets as a Cloud Service에 대한 주요 변경 사항](/help/assets/assets-cloud-changes.md)
* [Cloud Service으로 AEM Assets 소개](/help/assets/overview.md)
* [Adobe Experience Manager as a Cloud Service 자습서](https://docs.adobe.com/content/help/ko-KR/experience-manager-learn/cloud-service/overview.html)
