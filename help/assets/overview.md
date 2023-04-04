---
title: Assets as a [!DNL Cloud Service] 소개
description: Assets as a [!DNL Cloud Service]의 새로운 기능.
contentOwner: AG
feature: Asset Management
role: User,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: efc0f317cf4540db49b6caf7bb9f6fd31b311583
workflow-type: ht
source-wordcount: '457'
ht-degree: 100%

---

# Assets as a[!DNL Cloud Service] 소개 {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a[!DNL Cloud Service]는 클라우드 기반의 비즈니스용 PaaS 솔루션을 제공하여 빠르고 효과적으로 디지털 에셋 관리 및 Dynamic Media 작업을 수행할 뿐만 아니라 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습하는 시스템 내에서 AI/ML과 같은 차세대 스마트 기능도 사용합니다.

여러 에셋 또는 복합 에셋의 동시 수집은 Experience Manager Author 인스턴스에 대한 리소스 집약적인 작업입니다. 기본 인스턴스는 에셋이 추가, 처리나 마이그레이션될 때 상당한 양의 CPU, 메모리 및 I/O 리소스를 사용합니다. 해당 성능 문제는 최종 사용자의 작성 및 탐색 경험에 영향을 미칩니다.

기업은 여러 디바이스, 교차 지역과 다국어 사용 사례의 다양한 파일 형식 및 콘텐츠 해상도에 대한 지원이 필요합니다. 에셋 처리 및 저장 요구 사항에는 기존 솔루션에 과부하를 줄 수 있는 리소스와 기능이 필요합니다. 에셋 처리의 기술적 제한으로 인해 원하는 결과를 얻지 못하는 경우가 있고, 저장 비용이 이윤에 방해가 되는 경우도 있습니다.

우선 [클라우드 기반 제품의 이점](#solution-benefits)을 이해합니다. Experience Manager Assets에도 영향을 미치는 [Experience Manager as a  [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md)에 대한 주요 변경 사항을 확인한 다음 [Assets](/help/assets/assets-cloud-changes.md)에 대한 주요 변경 사항을 확인합니다.

[새 에셋 기능에 대한 세부 정보](#whats-new-assets) 및 [알려진 문제](/help/release-notes/maintenance/latest.md)에 대해 알아봅니다. 이 릴리스에서 제거된 기능을 확인하려면 [더 이상 사용되지 않거나 제거된 기능](/help/release-notes/deprecated-removed-features.md) 목록을 참조하십시오. 마지막으로 이 [용어집](/help/overview/terminology.md)을 참조하여 Experience Manager 용어를 숙지합니다.

## 솔루션 이점 {#solution-benefits}

다음은 Assets as a [!DNL Cloud Service]의 주요 이점입니다. 자세한 내용은 [Experience Manager as a 개요 [!DNL Cloud Service]](/help/overview/introduction.md)를 참조하십시오.

* **에셋 처리를 위한 최신 클라우드 서비스**: 새 에셋 마이크로서비스는 확장 가능하고 안정적이고 간편한 클라우드 기반의 에셋 처리 서비스입니다.
* **뛰어난 확장성**: 확장성이 뛰어난 모든 유형의 배포. 필요한 경우 실제 온디맨드로 제공되는 무제한 리소스입니다. 기존 시스템에 비해 과잉 디자인 비용을 절감합니다.
* **최신 소프트웨어**: 항상 최신 상태이며 업데이트됩니다. 모든 사용자는 모든 패치, 기능, 보안 및 버그 수정이 제공되는 최신 소프트웨어만 사용합니다. 개발자와 통합자는 여러 버전 지원의 문제 없는 최신 API 세트를 사용하여 작업합니다.
* **항상 온라인 상태**: 백업 및 중복이 있는 클러스터에 인스턴스가 배포되어 무중단 상태(0dt). 업그레이드도 0dt입니다.
* **지속적인 모니터링**: 시스템 모니터링은 자동화되어 있고, 기본 제공 검사와 트리거는 성능, 가용성 및 전반적인 견고성을 유지하는 데 도움이 됩니다.
* **간편한 배포**: Experience Manager in the Cloud 작업은 완전히 자동화되어 수동 개입이 필요하지 않습니다. 배포를 자동화하는 경우 Cloud Manager(CM) 구성 요소는 사용자 지정 코드가 포함된 배포 가능한 Docker 이미지의 빌드를 자동화합니다.

## 새 에셋 기능 {#whats-new-assets}

주요한 새 기능은 다음과 같습니다.

* [에셋 마이크로서비스](/help/assets/asset-microservices-overview.md)
* [에셋 업로드 메서드](/help/assets/add-assets.md)
