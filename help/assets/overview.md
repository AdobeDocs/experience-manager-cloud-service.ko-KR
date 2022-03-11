---
title: Assets as a 소개 [!DNL Cloud Service]
description: Assets as a [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management
role: User,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Assets as a [!DNL Cloud Service] {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a [!DNL Cloud Service] 는 빠르고 강력한 디지털 자산 관리 및 Dynamic Media 작업을 수행할 수 있을 뿐만 아니라 항상 최신, 항상 사용 가능하고 항상 학습할 수 있는 시스템 내에서 AI/ML과 같은 차세대 스마트 기능도 사용할 수 있는 클라우드 기반의 PaaS 솔루션을 제공합니다.

많은 자산 또는 복잡한 자산을 동시에 처리하는 것은 Experience Manager 작성자 인스턴스에 대해 리소스를 많이 사용하는 작업입니다. 기본 인스턴스는 자산을 추가, 처리 또는 마이그레이션할 때 상당한 CPU, 메모리 및 I/O 리소스를 사용합니다. 이러한 성능 문제는 최종 사용자의 작성 및 탐색 환경에 영향을 줍니다.

기업은 여러 장치, 지리적 지역 및 다국어 사용 사례에 대해 광범위한 파일 형식 및 컨텐츠 해상도를 지원해야 합니다. 자산 처리 및 스토리지 요구 사항에 따라 기존 솔루션에 부담을 줄 수 있는 리소스와 기능이 필요합니다. 경우에 따라, 자산 처리의 기술적 제한이 원하는 결과를 산출하지 않으며, 다른 경우에 저장 비용이 수익 마진을 위한 장애입니다.

먼저 다음을 이해합니다 [클라우드 기반의 서비스의 이점](#solution-benefits). 주목할 만한 [Experience Manager으로 변경 [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md) Experience Manager Assets에 영향을 미치기 때문에 [자산 변경 사항](/help/assets/assets-cloud-changes.md).

를 계속 읽어 보십시오. [새 Assets 기능에 대한 세부 사항](#whats-new-assets) 그리고 [알려진 문제](/help/release-notes/known-issues.md). 목록 보기 [더 이상 사용되지 않거나 제거된 기능](/help/release-notes/deprecated-removed-features.md) 이 릴리스에서 제거된 내용을 확인하고 다음을 확인하십시오 [예정된 기능 목록](/help/release-notes/known-issues.md#upcoming-assets-capabilities) 곧 무슨 일이 일어날지 알기 위해서. 마지막으로, Experience Manager 용어를 이것의 도움으로 이해합니다 [용어 설명](/help/overview/terminology.md).

## 솔루션의 이점 {#solution-benefits}

Assets as a의 주요 이점은 다음과 같습니다 [!DNL Cloud Service]. 자세한 내용은 [로서의 Experience Manager 개요 [!DNL Cloud Service]](/help/overview/introduction.md).

* **자산 처리를 위한 최신 클라우드 서비스**: 새로운 자산 마이크로서비스는 클라우드 기반의 확장 가능하고 안정적이며 간편한 자산 처리 서비스입니다.
* **확장성이 뛰어난**: 모든 유형의 배포에서 탄력적인 확장성 필요한 경우 온디맨드로 이용할 수 있는 사실상 무제한 리소스입니다. 기존 시스템에 비해 설계 비용이 많이 절감됩니다.
* **최신 소프트웨어**: 항상 최신 상태이고 항상 업데이트됩니다. 모든 사용자는 모든 패치, 기능, 보안 및 버그 수정이 포함된 최신 소프트웨어만 사용할 수 있습니다. 개발자 및 통합자는 다중 버전 지원 문제 없이 최신 API 세트를 사용합니다.
* **항상 온라인**: 백업 및 중복이 있는 클러스터에 배포되는 인스턴스 덕분에 다운타임이 전혀 발생하지 않습니다(0dt). 업그레이드 또한 0dt입니다.
* **상수 모니터링**: 시스템 모니터링은 자동화되고 내장된 체크와 트리거를 통해 성능, 가용성 및 전반적인 견고성을 유지할 수 있습니다.
* **간편한 배포**: 클라우드 작업의 Experience Manager은 수동 개입이 필요 없는 완전히 자동화됩니다. 자동화된 배포를 위해 CM(Cloud Manager) 구성 요소는 사용자 지정 코드를 포함하는 배포 가능한 Docker 이미지의 빌드를 자동화합니다.

## 새 자산 기능 {#whats-new-assets}

중요한 새로운 기능은 다음과 같습니다.

* [에셋 마이크로서비스](/help/assets/asset-microservices-overview.md)
* [자산 업로드 방법](/help/assets/add-assets.md)
