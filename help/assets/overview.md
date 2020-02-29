---
title: 클라우드 서비스로서의 자산 소개
description: 클라우드 서비스로서의 에셋의 새로운 기능
contentOwner: AG
translation-type: tm+mt
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Introducing Assets as a Cloud Service {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a Cloud Service는 클라우드 기반의 PaaS 솔루션을 제공하므로 기업은 신속하고 효과적으로 디지털 자산 관리 및 다이내믹 미디어 작업을 수행할 수 있을 뿐만 아니라 항상 최신 방식으로 이용할 수 있고 항상 학습 가능한 차세대 스마트 기능을 시스템 내에서 사용할 수 있습니다.

많은 수의 자산이나 복잡한 자산에 대한 동시 인제스트는 AEM 작성자 인스턴스에 대해 리소스를 많이 사용합니다. 기본 인스턴스는 에셋을 추가, 처리 또는 마이그레이션할 때 상당한 CPU, 메모리 및 I/O 리소스를 사용합니다. 이러한 성능 문제는 최종 사용자의 작성 및 탐색 경험에 영향을 줍니다.

기업은 다양한 파일 포맷과 다중 장치, 지리 및 다국어 사용 사례를 위한 컨텐츠 해상도를 지원해야 합니다. 자산 처리 및 스토리지 요구 사항에는 기존 솔루션의 부담을 가중시킬 수 있는 리소스와 기능이 필요합니다. 경우에 따라, 자산 처리의 기술적 제한으로 원하는 결과를 얻지 못할 수도 있고, 다른 경우에는 저장 비용이 이익 수익에 장애가 될 수도 있습니다.

먼저 클라우드 기본 솔루션의 [이점을](#solution-benefits)파악하십시오. Adobe Experience Manager Assets에 영향을 미치는 클라우드 서비스로서 AEM의 주목할 만한 [변경](/help/release-notes/aem-cloud-changes.md) 사항을 확인하고 [변경 사항을 자산에 적용합니다](/help/assets/assets-cloud-changes.md).

새로운 자산 기능과 [](#whats-new-assets) 알려진 문제에 [](/help/release-notes/known-issues.md)대한 자세한 내용을 살펴보십시오. 이 릴리스에서 제거되는 기능을 [확인하려면](/help/release-notes/deprecated-removed-features.md) 더 이상 사용되지 않거나 제거된 기능 [목록을 참조하십시오. 그리고 향후 출시될 기능에](/help/release-notes/known-issues.md#upcoming-assets-capabilities) 대한목록을 참조하십시오. 마지막으로, 이 [용어 해설을](/help/overview/terminology.md)통해 AEM 용어를 이해합니다.

## 솔루션 이점 {#solution-benefits}

다음은 클라우드 서비스로 제공되는 자산의 주요 이점입니다. 자세한 내용은 Experience Manager as a Cloud Service [개요를 참조하십시오](/help/overview/introduction.md).

* **에셋 처리를**&#x200B;위한 최신 클라우드 서비스:새로운 에셋 마이크로서비스는 클라우드 기반의 확장 가능하고 안정적이며 간편한 에셋 처리 서비스입니다.
* **높은 확장성**:모든 유형의 배포에 대한 탄력적인 확장성 필요할 때마다 언제든지 On-Demand 방식으로 이용할 수 있는 리소스를 사실상 무제한으로 이용할 수 있습니다. 기존 시스템에 비해 디자인 비용이 많이 절감됩니다.
* **최신 소프트웨어**:항상 최신 상태로 항상 업데이트됩니다. 모든 사용자는 모든 패치, 기능, 보안 및 버그 수정이 가능한 최신 소프트웨어만 사용할 수 있습니다. 개발자와 통합자는 다중 버전 지원 문제 없이 최신 API 세트를 사용하여 작업할 수 있습니다.
* **항상 온라인**:백업 및 중복을 통해 클러스터에 배포된 인스턴스 덕분에 가동 중지 시간(0dt)이 전혀 발생하지 않습니다. 업그레이드도 0dt입니다.
* **지속적인 모니터링**:시스템 모니터링은 자동화 및 내장된 체크와 트리거를 통해 성능, 가용성 및 전반적인 견고성을 유지할 수 있습니다.
* **간편한 배포**:클라우드 작업의 AEM은 수동 개입이 필요 없는 완전히 자동화되도록 설계되었습니다. 이를 위해 CM(클라우드 관리자) 구성 요소는 사용자 정의 코드가 들어 있는 배포 가능한 Docker 이미지 작성을 자동화합니다.

## 새로운 자산 기능 {#whats-new-assets}

중요한 새로운 기능은 다음과 같습니다.

* [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)
* [자산 업로드 방법](/help/assets/add-assets.md)
