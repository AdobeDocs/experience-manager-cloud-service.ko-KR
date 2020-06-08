---
title: 클라우드 서비스로서의 자산 소개
description: 클라우드 서비스로 제공되는 에셋의 새로운 기능
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 3%

---


# 클라우드 서비스로서의 Assets 소개 {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a Cloud Service는 기업이 디지털 에셋 관리 및 다이내믹 미디어 작업을 신속하고 효율적으로 수행할 수 있을 뿐만 아니라 항상 최신, 항상 사용 가능하고 항상 사용 가능한, 항상 학습 방식으로 AI/ML과 같은 차세대 스마트 기능을 사용할 수 있도록 클라우드 기반의 PaaS 솔루션을 제공합니다.

많은 자산 또는 복잡한 자산에 대한 동시 인제스트는 AEM 작성자 인스턴스에 대한 리소스 중심 작업입니다. 자산을 추가, 처리 또는 마이그레이션하면 기본 인스턴스는 상당한 CPU, 메모리 및 I/O 리소스를 사용합니다. 이러한 성능 문제는 최종 사용자의 작성 및 탐색 경험에 영향을 줍니다.

기업은 다양한 파일 포맷과 다양한 디바이스, 지역 간 및 다국어 사용 사례를 위한 컨텐츠 해상도를 지원해야 합니다. 자산 처리 및 스토리지 요구 사항은 기존 솔루션의 부담을 가중시킬 수 있는 리소스와 기능을 필요로 합니다. 경우에 따라, 자산 처리의 기술적 제한이 원하는 결과를 낳지 않고, 다른 경우에는 저장 비용이 이익 수익에 장애가 됩니다.

먼저 클라우드 기본 솔루션의 [이점을 파악하십시오](#solution-benefits). Adobe Experience Manager Assets에 영향을 주는 클라우드 서비스로 [AEM에 대한 주목할 만한](/help/release-notes/aem-cloud-changes.md) 변경 사항 [](/help/assets/assets-cloud-changes.md)을 확인하십시오.

새로운 자산 기능 [및](#whats-new-assets) 알려진 문제에 대한 [자세한 내용을 살펴보십시오](/help/release-notes/known-issues.md). 이 릴리스에서 제거되는 기능을 [확인하려면 더 이상 사용되지 않거나 제거된 기능](/help/release-notes/deprecated-removed-features.md) 목록을 [보고 향후 기능](/help/release-notes/known-issues.md#upcoming-assets-capabilities) 목록을 참조하여 향후기능중 무엇이 곧 제공될 지 알 수 있습니다. 마지막으로, 이 [용어집](/help/overview/terminology.md)도움말로 AEM 용어를 이해합니다.

## 솔루션 이점 {#solution-benefits}

다음은 Assets as a Cloud Service의 주요 이점입니다. 자세한 내용은 Experience Manager as a Cloud Service [개요를 참조하십시오](/help/overview/introduction.md).

* **에셋 처리를 위한 최신 클라우드 서비스**: 새로운 에셋 마이크로서비스는 클라우드 기반의 확장 가능하고 안정적이며 간편한 에셋 처리 서비스입니다.
* **높은 확장성**: 모든 배포 유형에 대한 탄력적인 확장성 필요할 때마다 언제든지 On-Demand 방식으로 사용할 수 있는 무한한 리소스를 활용할 수 있습니다. 기존 시스템에 비해 지나치게 많은 디자인 비용을 절감할 수 있습니다.
* **최신 소프트웨어**: 항상 최신 상태로 항상 업데이트 모든 사용자에게는 모든 패치, 기능, 보안 및 버그 수정이 포함된 최신 소프트웨어만 제공됩니다. 개발자와 통합자는 다중 버전 지원 문제 없이 최신 API 세트를 사용하여 작업합니다.
* **항상 온라인**: 백업 및 중복을 갖춘 클러스터에 배포된 인스턴스 덕분에 가동 중지 시간(0dt)이 전혀 발생하지 않습니다. 업그레이드도 0dt입니다.
* **지속적인 모니터링**: 시스템의 모니터링은 자동화 및 내장된 체크아웃으로, 성능, 가용성 및 전반적인 안정성을 유지하는 데 도움이 됩니다.
* **간편한 배포**: 클라우드 작업의 AEM은 수동 개입이 필요 없는 완전히 자동화됩니다. 자동화된 배포를 위해 CM(클라우드 관리자) 구성 요소는 사용자 정의 코드를 포함하는 배포 가능한 Docker 이미지 작성을 자동화합니다.

## 새로운 자산 기능 {#whats-new-assets}

중요한 새로운 기능은 다음과 같습니다.

* [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)
* [자산 업로드 방법](/help/assets/add-assets.md)
