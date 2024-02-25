---
title: Assets as a [!DNL Cloud Service] 소개
description: Experience Manager Assets as a Cloud Service를 사용 및 관리하는 방법을 이해합니다.
contentOwner: AK
feature: Asset Management
role: User,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: b3bfc841f0609e1e529c97dd1f11d16de561701c
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 92%

---


# Assets as a [!DNL Cloud Service] 소개 {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a [!DNL Cloud Service]는 클라우드 기반의 비즈니스용 PaaS 솔루션을 제공하여 빠르고 효과적으로 디지털 자산 관리 및 Dynamic Media 작업을 수행할 뿐만 아니라 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습하는 시스템 내에서 AI/ML과 같은 차세대 스마트 기능도 사용합니다.

여러 자산 또는 복합 자산의 동시 수집은 Experience Manager Author 인스턴스에 대한 리소스 집약적인 작업입니다. 기본 인스턴스는 자산이 추가, 처리나 마이그레이션될 때 상당한 양의 CPU, 메모리 및 I/O 리소스를 사용합니다. 해당 성능 문제는 최종 사용자의 작성 및 탐색 경험에 영향을 미칩니다.

기업은 여러 디바이스, 교차 지역과 다국어 사용 사례의 다양한 파일 형식 및 콘텐츠 해상도에 대한 지원이 필요합니다. 자산 처리 및 저장 요구 사항에는 기존 솔루션에 과부하를 줄 수 있는 리소스와 기능이 필요합니다. 자산 처리의 기술적 제한으로 인해 원하는 결과를 얻지 못하는 경우가 있고, 저장 비용이 이윤에 방해가 되는 경우도 있습니다.

우선 [클라우드 기반 제품의 이점](#solution-benefits)을 이해합니다. Experience Manager Assets에도 영향을 미치는 [Experience Manager as a  [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md)에 대한 주요 변경 사항을 확인한 다음 [Assets](/help/assets/assets-cloud-changes.md)에 대한 주요 변경 사항을 확인합니다.

[새 자산 기능에 대한 세부 정보](#whats-new-assets) 및 [알려진 문제](/help/release-notes/maintenance/latest.md)에 대해 알아봅니다. 이 릴리스에서 제거된 기능을 확인하려면 [더 이상 사용되지 않거나 제거된 기능](/help/release-notes/deprecated-removed-features.md) 목록을 참조하십시오. 마지막으로 이 [용어집](/help/overview/terminology.md)을 참조하여 Experience Manager 용어를 숙지합니다.

## 솔루션 이점 {#solution-benefits}

다음은 Assets as a [!DNL Cloud Service]의 주요 이점입니다. 자세한 내용은 [Experience Manager as a 개요 [!DNL Cloud Service]](/help/overview/introduction.md)를 참조하십시오.

* **자산 처리를 위한 최신 클라우드 서비스**: 새 자산 마이크로서비스는 확장 가능하고 안정적이고 간편한 클라우드 기반의 자산 처리 서비스입니다.
* **뛰어난 확장성**: 확장성이 뛰어난 모든 유형의 배포. 필요한 경우 실제 온디맨드로 제공되는 무제한 리소스입니다. 기존 시스템에 비해 과잉 디자인 비용을 절감합니다.
* **최신 소프트웨어**: 항상 최신 상태이며 업데이트됩니다. 모든 사용자는 모든 패치, 기능, 보안 및 버그 수정이 제공되는 최신 소프트웨어만 사용합니다. 개발자와 통합자는 여러 버전 지원의 문제 없는 최신 API 세트를 사용하여 작업합니다.
* **항상 온라인 상태**: 백업 및 중복이 있는 클러스터에 인스턴스가 배포되어 무중단 상태(0dt). 업그레이드도 0dt입니다.
* **지속적인 모니터링**: 시스템 모니터링은 자동화되어 있고, 기본 제공 검사와 트리거는 성능, 가용성 및 전반적인 견고성을 유지하는 데 도움이 됩니다.
* **간편한 배포**: Experience Manager in the Cloud 작업은 완전히 자동화되어 수동 개입이 필요하지 않습니다. 배포를 자동화하는 경우 Cloud Manager(CM) 구성 요소는 사용자 정의 코드가 포함된 배포 가능한 Docker 이미지의 빌드를 자동화합니다.

## 사용 가능한 개인 기반의 경험 {#persona-based-experiences}

Adobe는 디지털 자산을 최대한 활용할 수 있는 강력한 DAM(디지털 자산 관리) 솔루션을 제공합니다. Adobe Experience Manager Assets에는 동일한 클라우드 서비스 저장소를 사용하는 서로 다른 두 가지 환경이 있습니다.

* **관리자 보기**: 기존의 Assets as a Cloud Service 사용자 인터페이스입니다. 통합, 워크플로, 콘텐츠 자동화, 게시 등을 포함한 모든 고급 자산 관리 기능에 관리자 보기를 사용합니다.

* **Assets 보기**: 디지털 자산을 저장, 관리, 검색 및 사용할 수 있는 가벼운 버전의 Adobe 자산 관리 환경입니다. 필수 자산 관리 기능이 포함된 간소화된 사용자 인터페이스입니다. 업로드, 메타데이터 관리, 검색, 다운로드 및 공유에 중점을 둔 가벼운 버전의 DAM 사용자를 위해 설계되었습니다.

관리자 보기에 대한 액세스 권한이 있는 사용자는 Assets 보기에도 액세스할 수 있습니다. Assets 보기는 간소화된 사용자 인터페이스를 통해 디지털 자산을 쉽게 관리, 검색 및 배포할 수 있습니다. 크리에이티브, 마케팅 및 사업 부문 팀 등 다양한 직무의 광범위한 사용자가 자산에 대해 공동 작업하고 필요한 시간과 장소에서 올바른 승인된 자산에 액세스할 수 있습니다. 많은 일반 DAM 사용자는 기능의 하위 집합만 포함하는 Assets 보기를 선호합니다. 이 경험은 크리에이티브, 읽기 전용 자산 소비자 및 더 가벼운 DAM 사용자를 대상으로 합니다.

DAM 라이브러리 관리자, 개발자 및 상위 사용자는 계속해서 관리자 보기를 사용하거나 필요에 따라 사용자 인터페이스 간에 전환할 수 있습니다. 역할에 가장 적합한 환경을 선택할 수 있습니다.

![add-tags](assets/newui-overview.svg)

Assets 보기에 액세스하는 방법 및 관리자 보기에서 제공하는 일부 간소화에 대한 자세한 내용은 [Assets 보기 소개](/help/assets/assets-view-introduction.md)를 참조하십시오.

## Edge Delivery Services용 문서 기반 작성과의 통합 {#integrate-doc-authoring-edge-and-assets}

Edge Delivery를 사용하면 작성자가 콘텐츠를 빠르게 업데이트 및 게시하고 새 사이트를 신속하게 시작할 수 있는 빠르고 매력적인 웹 사이트를 제작할 수 있습니다.

AEM Assets를 Edge Delivery Services용 문서 기반 작성과 통합하면 웹 사이트 작성자가 Microsoft Word 또는 Google Docs에서 문서를 작성하는 동안 AEM Assets 저장소에서 사용 가능한 이미지를 사용할 수 있습니다. 자세한 내용은 [AEM Assets를 문서 기반 작성과 통합](/help/edge/using.md#integrate-assets-edge)을 참조하십시오.

## Adobe Journey Optimizer과 통합 {#integration-with-ajo}

[Adobe Journey Optimizer](https://business.adobe.com/products/journey-optimizer/adobe-journey-optimizer.html) 는 고객에게 지능적인 의사 결정과 통찰력을 통해 옴니채널 캠페인을 제공할 수 있도록 여정 관리를 간소화합니다. Journey Optimizer을 사용하여 메시지를 디자인할 때 Journey Optimizer 인터페이스 내에서 자산 as a Cloud Service 저장소에 직접 액세스할 수 있습니다. 사용자는 Experience Manager Assets의 임베드된 사용자 인터페이스를 사용하여 에셋에 액세스할 수 있습니다. 자세한 내용은 [Experience Manager Assets을 사용하여 에셋 만들기 및 관리](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/assets-images/assets.html).

## 새 자산 기능 {#whats-new-assets}

주요한 새 기능은 다음과 같습니다.

* [자산 마이크로서비스](/help/assets/asset-microservices-overview.md)
* [자산 업로드 메서드](/help/assets/add-assets.md)

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
