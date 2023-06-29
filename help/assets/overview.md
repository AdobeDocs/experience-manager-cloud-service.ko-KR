---
title: Assets as a [!DNL Cloud Service] 소개
description: Assets as a [!DNL Cloud Service]의 새로운 기능.
contentOwner: AG
feature: Asset Management
role: User,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: 5a7938d5e52388516f8b66bbcf8ffdee332a51a3
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 68%

---

# Assets as a [!DNL Cloud Service] 소개 {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a [!DNL Cloud Service]는 클라우드 기반의 비즈니스용 PaaS 솔루션을 제공하여 빠르고 효과적으로 디지털 에셋 관리 및 Dynamic Media 작업을 수행할 뿐만 아니라 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습하는 시스템 내에서 AI/ML과 같은 차세대 스마트 기능도 사용합니다.

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

## 사용 가능한 사용자 기반 경험 {#persona-based-experiences}

Adobe는 디지털 에셋을 최대한 활용할 수 있는 강력한 DAM(디지털 에셋 관리) 솔루션을 제공합니다. Adobe Experience Manager Assets에는 동일한 Cloud Services 저장소를 사용하는 두 개의 별도 경험이 있습니다.

* **관리자 보기**: 기존 Assets as a Cloud Service 사용자 인터페이스. 통합, 워크플로우, 콘텐츠 자동화, 게시 등을 포함한 모든 고급 에셋 관리 기능에 대해 관리 보기를 사용합니다.

* **자산 보기**: 디지털 에셋을 저장하고, 관리하고, 검색하고, 사용할 수 있는 Adobe의 간단한 에셋 관리 경험입니다. 필수 에셋 관리 기능이 포함된 간소화된 사용자 인터페이스입니다. 업로드, 메타데이터 관리, 검색, 다운로드 및 공유에 중점을 둔 경량 DAM 사용자를 위해 설계되었습니다.

관리자 보기에 대한 액세스 권한이 있는 사용자는 에셋 보기에 액세스할 수도 있습니다. 에셋 보기는 간소화된 사용자 인터페이스를 제공하여 디지털 에셋을 쉽게 관리, 검색 및 배포할 수 있도록 합니다. 크리에이티브, 마케팅 및 사업 부문 팀을 비롯한 다양한 기능의 광범위한 사용자가 에셋에 대해 공동 작업을 수행하고 필요한 시간과 장소에서 올바른 승인된 에셋에 액세스할 수 있습니다. 많은 일반 DAM 사용자는 기능의 하위 집합만 포함하므로 에셋 보기를 선호합니다. 이 경험은 크리에이티브, 읽기 전용 에셋 소비자 및 경량 DAM 사용자를 대상으로 합니다.

DAM 라이브러리 관리자, 개발자 및 슈퍼 사용자는 필요에 따라 관리자 보기를 계속 사용하거나 사용자 인터페이스 간을 전환할 수 있습니다. 역할에 가장 적합한 경험을 선택할 수 있습니다.

![태그 추가](assets/newui-overview.svg)

자산 보기에 액세스하는 방법과 관리자 보기에서 제공하는 몇 가지 간소화에 대한 자세한 내용은 을 참조하십시오. [자산 보기 소개](/help/assets/assets-view-introduction.md).

## 새 에셋 기능 {#whats-new-assets}

주요한 새 기능은 다음과 같습니다.

* [에셋 마이크로서비스](/help/assets/asset-microservices-overview.md)
* [에셋 업로드 메서드](/help/assets/add-assets.md)

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
