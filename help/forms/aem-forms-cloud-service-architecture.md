---
title: Experience Manager [!DNL AEM Forms] as a Cloud Service 아키텍처
description: 의 아키텍처 이해 [!DNL AEM Forms] 플랫폼의 확장성, 탄력성 및 성능 측면에 대해 as a Cloud Service을 이용할 수 있습니다.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 6%

---


# [!DNL AEM] as a Cloud Service 아키텍처 {#architecture}

[!DNL AEM Forms] as a Cloud Service은 모든 고객을 위한 배포 아키텍처를 표준화하므로 고객이 아키텍처 고려 사항에서 완전히 벗어날 수 있도록 합니다. 예를 들어, 새로운 AEM as a Cloud Service 아키텍처는 지속성을 위해 마이크로 커널의 개념에 의존하지만 고객은 어떤 마이크로 커널을 선택할지에 대해 걱정할 필요가 없습니다. 작성자와 게시 측에서 모두 사용되는 마이크로 커널은 다음과 같습니다 [!DNL AEM Cloud Service] 그리고 그렇지 않으면 고객이 온-프레미스 설치에 사용할 수 없습니다.

AEM as a Cloud Service에는 AEM 인스턴스 수가 다양한 동적 아키텍처가 있습니다. 개발, 스테이지, 프로덕션 및 데모 환경을 제공합니다. AEM 인스턴스(Cloud Manager)를 관리하고, 사용자 및 인증(Admin Console 및 IMS(Adobe Identity Management) 시스템)을 유지 관리하고, 캐싱(CDN)을 구성하고, 클라우드 기반의 개발 환경을 관리하는 도구를 제공합니다. 아키텍처에 대한 자세한 내용은 다음을 참조하십시오. [건축의 소개 [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=en).

## Cloud Manager{#cloud-manager}

Cloud Manager는 [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en). 의 각 새 테넌트 [!DNL AEM Forms] as a Cloud Service은 Cloud Manager 액세스를 위해 먼저 제공됩니다. Cloud Manager는 고객의 운영 및 개발자 모습을 위한 단일 시작점입니다. AEM 프로그램과 환경을 관리할 수 있는 곳입니다. Cloud Manager는 AEM as a Cloud Service의 주요 구성 요소를 만들고 구성할 수 있는 셀프 서비스 포털로 발전했습니다.

* 프로그램 만들기 및 관리
* 프로그램 내에서 AEM 환경 만들기 및 관리
* 고객 코드 및 구성을 특정 환경에 배포하기 위한 파이프라인 만들기 및 관리
* 이러한 구성 요소에 대한 중요한 라이프사이클 이벤트에 대한 알림 받기(예: 제품 업데이트) Cloud Manager에 대한 자세한 내용은 [Cloud Manager Adobe 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html) 및 [Cloud Manager 소개](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=ko-KR).

## 사용자 및 인증 {#users-and-authentication}

AEM as a Cloud Service에는 AEM 인스턴스 및 IMS(Adobe Identity Management 시스템) 기반 인증에 대한 Admin Console 지원이 포함되어 있습니다. 관리자는 Admin Console을 사용하여 모든 Experience Cloud 사용자를 중앙에서 관리할 수 있습니다. 사용자 및 그룹을 AEM as a Cloud Service 인스턴스와 연결된 제품 프로필에 지정하여 해당 인스턴스에 로그인할 수 있도록 할 수 있습니다. 사용자, 인증 및 AEM as a Cloud Service 인스턴스에 액세스하는 방법에 대한 자세한 내용은 [에 대한 IMS 지원 [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#introduction).

다양한 사람들이 일반적인 [!DNL AEM Forms] 프로젝트. 에 로그인한 후 [!DNL AEM Forms] as a Cloud Service 인스턴스: [admin console에서 사용자 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html) 조직 또는 프로젝트에 적용할 수 있는 [사용자를 기본 제공 그룹에 할당](forms-groups-privileges-tasks.md) 필요한 권한을 제공합니다.

다양한 내장 학습 [!DNL AEM Forms] 사용 가능한 특정 사용자 그룹 및 권한 [!DNL AEM Forms] Cloud Services 인스턴스에서는 [구성, 사용자, 역할 및 그룹](forms-groups-privileges-tasks.md).

## 개발자 경험 {#developer-experience}

AEM as a Cloud Service을 지원하는 새로운 아키텍처는 전체 개발자 경험에 몇 가지 주요 변경 사항을 제공합니다. 개발자 경험 변경에 대한 주요 목표 중 하나는 기존 사용자 지정 코드를 거의 수정하지 않고 가능한 한 빨리 AEM as a Cloud Service으로 마이그레이션할 수 있도록 허용하는 것입니다.

## 클라우드 개발 {#cloud-development}

다음은 AEM as a Cloud Service 환경에서 기존 코드를 원활하게 실행하는 지침입니다.

* 코드 및 구성을 관련 Cloud Manager 프로그램의 Git 저장소에 저장합니다. 코드를 손쉽게 관리하고 CI/CD와 통합할 수 있습니다.
* 기준선과 호환되는 애플리케이션 코드 및 구성 만들기 [!DNL AEM Forms] 이미지. 최신 API를 사용하면 빠르고 안전한 애플리케이션을 빌드할 수 있습니다.
* Cloud Manager 환경과 연결된 Cloud Manager 파이프라인을 사용하여 애플리케이션을 빌드하고 배포합니다. Adobe Campaign은에 대한 최신 기능과 버그를 수정하도록 도와줍니다 [!DNL AEM Forms] 환경에 as a Cloud Service
* 사용자 지정 애플리케이션이 파이프라인에 적용되는 모든 코드 품질, 보안 및 성능 게이트를 통과하도록 하십시오. Labs를 사용하면 안전하고 더 나은 성능 애플리케이션을 구축함으로써 고객 경험을 향상시킬 수 있습니다. 항상 Cloud Manager UI를 사용하여 일부 검사를 건너뛸 수 있습니다.
이 프로세스를 일반적으로 클라우드 우선 개발이라고 합니다. [!DNL AEM Forms] 또한 as a Cloud Service은 클라우드에서 보류 중인 코드 및 구성 변경을 시도하기 전에 신속한 개발을 지원하는 SDK를 제공합니다.
이전에 AEM QuickStart에 포함되었던 일부 인터페이스는 AEM as a Cloud Service 환경의 사용자가 더 이상 사용할 수 없습니다. 예를 들어 OSGI 번들 및 관련 구성이 관리되는 웹 콘솔입니다. CRXDE Lite 컨텐츠 저장소 브라우저는 비프로덕션 환경 유형에서만 액세스할 수 있게 됩니다. 개발자가 진단 및 상태 목적으로 사용하는 경우 특히 필요한 웹 콘솔 기능의 하위 집합은 새로운 개발자 콘솔을 통해 사용할 수 있습니다.
또한 개발자에게 가장 일반적인 요구 사항 중 하나는 다양한 환경의 로그 파일에 빠르게 액세스하는 것입니다. 사용 [!DNL AEM Cloud Service]로 지정하는 경우 작성자, 게시에 있는 다른 노드의 로그 파일은 Cloud Manager를 통해 다운로드할 수 있는 파일 형식 또는 로그를 추적하기 위한 API를 통해 사용할 수 있습니다. 코드와 컨텐츠가 명확히 구분되어 개발자는 배포의 일부로 컨텐츠를 업데이트하는 특정 프로세스를 활용할 수 있습니다. 변경 가능한 콘텐츠의 일반적인 사용 사례는 다음과 같습니다.
* 고객 프로젝트에 포함된 표준 &quot;기본&quot; 컨텐츠(예: 폴더, 템플릿, 워크플로우..)
* 검색 색인 정의
* ACL 및 권한
* 서비스 사용자 및 사용자 그룹
개발 환경 설정, [CI/CD 파이프라인 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html), 및 학습 [코드 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) 환경.

## 로컬 개발 {#local-development}

을 설정하고 구성할 때 [!DNL AEM Forms] as a Cloud Service 환경에서는 개발, 스테이징 및 프로덕션 환경을 설정합니다. 또한 빠른 반복 및 개발을 위한 로컬 개발 환경을 설정하고 구성합니다. AEM SDK를 다운로드하여 설정하고 [!DNL AEM Forms] 로컬 설정을 위한 추가 기능 아카이브 [!DNL Forms] as a Cloud Service 개발 환경.  자세한 지침은 [로컬 개발 환경 설정](setup-local-development-environment.md).

## 디버깅 {#debugging}

AEM as a Cloud Service 은 셀프 서비스, 확장 가능한 클라우드 인프라에서 실행됩니다. AEM 개발자는 빌드 및 배포에서 AEM 애플리케이션 실행에 대한 세부 사항을 획득하기 위해 AEM의 다양한 패싯을 이해하고 디버깅해야 합니다. 자세한 내용은 [AEM as a Cloud Service 디버깅](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en).
