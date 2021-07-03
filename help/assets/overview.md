---
title: Assets as a [!DNL Cloud Service] 소개
description: Assets as a [!DNL Cloud Service]의 새로운 기능.
contentOwner: AG
feature: 자산 관리
role: Business Practitioner,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: 7256300afd83434839c21a32682919f80097f376
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# 자산을 [!DNL Cloud Service](으)로 소개 {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a [!DNL Cloud Service]은(는) 빠르고 효과적으로 디지털 자산 관리 및 Dynamic Media 작업을 수행할 수 있을 뿐만 아니라 항상 최신, 항상 사용 가능하고 항상 학습할 수 있는 시스템 내에서 AI/ML과 같은 차세대 스마트 기능도 사용할 수 있는 클라우드 기반의 PaaS 솔루션을 제공합니다.

많은 자산 또는 복잡한 자산을 동시에 처리하는 것은 AEM 작성자 인스턴스에 대해 리소스를 많이 사용하는 작업입니다. 기본 인스턴스는 자산을 추가, 처리 또는 마이그레이션할 때 상당한 CPU, 메모리 및 I/O 리소스를 사용합니다. 이러한 성능 문제는 최종 사용자의 작성 및 탐색 환경에 영향을 줍니다.

기업은 여러 장치, 지리적 지역 및 다국어 사용 사례에 대해 광범위한 파일 형식 및 컨텐츠 해상도를 지원해야 합니다. 자산 처리 및 스토리지 요구 사항에 따라 기존 솔루션에 부담을 줄 수 있는 리소스와 기능이 필요합니다. 경우에 따라, 자산 처리의 기술적 제한이 원하는 결과를 산출하지 않으며, 다른 경우에 저장 비용이 수익 마진을 위한 장애입니다.

시작하려면 클라우드 기반의 제공 [의 이점을 이해합니다. ](#solution-benefits) 주목할 만한 [Assets](/help/assets/assets-cloud-changes.md)의 변경 사항에 따라 Experience Manager 자산에도 영향을 주는 주목할 만한 [AEM에 대한 변경 사항을 확인하십시오. [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md)

새 Assets 기능](#whats-new-assets) 및 [알려진 문제](/help/release-notes/known-issues.md)에 대한 세부 사항을 알려면 계속 읽도록 하십시오. [ 이 릴리스에서 제거된 기능을 확인하려면 [더 이상 사용되지 않거나 제거된 기능](/help/release-notes/deprecated-removed-features.md) 목록을 보고 다음 [예정된 기능 목록](/help/release-notes/known-issues.md#upcoming-assets-capabilities)을 참조하여 곧 제공되는 내용을 알아보십시오. 마지막으로 이 [용어](/help/overview/terminology.md)의 도움을 받아 AEM 용어를 이해합니다.

## 솔루션의 이점 {#solution-benefits}

다음은 Assets as a [!DNL Cloud Service] 의 주요 이점입니다. 자세한 내용은 [Experience Manager 개요 a [!DNL Cloud Service]](/help/overview/introduction.md)를 참조하십시오.

* **자산 처리를 위한 최신 클라우드 서비스**:새로운 자산 마이크로서비스는 클라우드 기반의 확장 가능하고 안정적이며 간편한 자산 처리 서비스입니다.
* **확장성이 뛰어난**:모든 유형의 배포에서 탄력적인 확장성 필요한 경우 온디맨드로 이용할 수 있는 사실상 무제한 리소스입니다. 기존 시스템에 비해 설계 비용이 많이 절감됩니다.
* **최신 소프트웨어**:항상 최신 상태이고 항상 업데이트됩니다. 모든 사용자는 모든 패치, 기능, 보안 및 버그 수정이 포함된 최신 소프트웨어만 사용할 수 있습니다. 개발자 및 통합자는 다중 버전 지원 문제 없이 최신 API 세트를 사용합니다.
* **항상 온라인**:백업 및 중복이 있는 클러스터에 배포되는 인스턴스 덕분에 다운타임이 전혀 발생하지 않습니다(0dt). 업그레이드 또한 0dt입니다.
* **지속적인 모니터링**:시스템 모니터링은 자동화되고 내장된 체크와 트리거를 통해 성능, 가용성 및 전반적인 견고성을 유지할 수 있습니다.
* **간편한 배포**:클라우드 작업의 AEM은 수동 개입이 필요 없는 완전히 자동화되어 있습니다. 자동화된 배포를 위해 CM(Cloud Manager) 구성 요소는 사용자 지정 코드를 포함하는 배포 가능한 Docker 이미지의 빌드를 자동화합니다.

## 새 자산 기능 {#whats-new-assets}

중요한 새로운 기능은 다음과 같습니다.

* [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)
* [자산 업로드 방법](/help/assets/add-assets.md)
