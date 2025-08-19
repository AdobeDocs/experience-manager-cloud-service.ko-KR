---
title: 소개 및 개요
description: 다양한 상점 옵션을 이해하십시오.
thumbnail: introducing-aem-commerce.jpg
exl-id: 29410f76-a63f-4b0a-b817-2ed724ad1a3c
feature: Commerce Integration Framework
role: Admin
source-git-commit: 80f1c9548b8b87dc6280e0e95988d84a8376f7ab
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 1%

---


# Content 및 Commerce {#content-commerce}

인텐트 기반 및 고성능 상거래 경험에 대한 고객의 기대치가 높아지면서 브랜드는 품질을 그대로 유지하면서 더 많은 콘텐츠를 더 빠르게 제공해야 하는 압박을 받고 있습니다. Adobe Experience Manager을 사용하면 브랜드가 더 빠르게 확장 및 혁신하여 몰입형 상거래 경험을 만들고 더 많은 트래픽과 증가하는 온라인 지출을 캡처할 수 있습니다.

Adobe Experience Manager은 콘텐츠가 풍부하고 개인화된 고객 경험을 만들고 관리할 수 있는 강력한 도구를 제공합니다. AEM을 Adobe Commerce, Salesforce Commerce, SAP Commerce Cloud 또는 기타 솔루션과 같은 상거래 솔루션과 통합하면 브랜드가 콘텐츠와 상거래를 통합하여 채널 간에 원활한 쇼핑 여정을 제공할 수 있습니다.

## 상점 소개 개요 {#overview}

AEM은 상황과 환경 설정에 따라 지원을 제공할 수 있습니다. 다음 지침을 사용하여 자신에게 적합한 접근 방식을 선택하십시오.

* [Edge Delivery Services 사용(권장)](#edge)
* [고유한 상점 사용(헤드리스 AEM 통합)](#own-storefront)
* [AEM CIF 상점 사용](#cif)

### Edge Delivery Services 사용(권장) {#edge}

귀사에서 웹에서 가장 빠르고 AI에 친화적인 매장을 원하며 개발자가 최첨단 개발자 경험을 원하는 경우 [Edge Delivery Services을 사용하십시오.](../edge/overview.md) Edge Delivery Services은 현재와 미래의 모든 요구 사항을 충족합니다. 백엔드 및 솔루션에 따라 다른 옵션이 있습니다.

#### &#x200B;1. Adobe Commerce as a Cloud Service과의 통합 {#acaacs}

Adobe에서는 Edge Delivery 및 [Adobe Commerce 상점](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=ko)을 시작점으로 사용하는 것이 좋습니다. Storefront에는 Adobe Commerce 서비스, API와 사전 통합된 보일러판이 포함되어 있으며 Commerce 드롭인 구성 요소를 다양하게 제공하여 매장을 신속하게 구축할 수 있습니다.

적합: Adobe Commerce as a Cloud Service의 일반적인 상점 환경

#### &#x200B;2. Adobe Commerce Optimizer과의 통합(타사 솔루션의 경우) {#aco}

기존 상거래 솔루션을 통합하고 카탈로그 성능을 높이려면 [Adobe Commerce Optimizer](https://experienceleague.adobe.com/ko/docs/commerce-learn/tutorials/adobe-commerce-optimizer/overview)을(를) 최신 통합 레이어로 사용하는 것이 Adobe의 좋습니다. Commerce Optimizer은 카탈로그 및 머천다이징을 위한 고성능 SaaS 서비스로 상거래 솔루션을 개선합니다. Adobe Commerce as a Cloud Service과 마찬가지로 [Adobe Commerce 상점](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=ko)도 즉시 사용할 수 있습니다.

Salesforce Commerce과 같은 상거래 솔루션에 대한 통합을 사용할 수 있습니다. Adobe 담당자에게 문의하십시오.

적합: 기존 상거래 솔루션으로 일반적인 상점 환경

#### &#x200B;3. 사용자 정의 통합 {#custom}

Adobe 사용자 지정 통합을 빌드하려면 Edge Delivery Services을 사용하는 것이 좋습니다. 처음부터 새로 시작하거나 Edge Delivery 상점 첫 화면에서 기존 JS 프레임워크 상거래 구성 요소(예: 트랜잭션 부품)를 다시 사용할 수 있습니다. 이를 통해 고객은 무아지경 친화적인 매우 빠른 쇼핑 경험을 얻을 수 있을 뿐만 아니라 기존 투자를 다시 사용하여 TTV를 향상시킬 수 있습니다. 시작 지점은 기본 [Edge Delivery Boilerplate](https://www.aem.live/developer/tutorial)입니다.

적합: Edge Deliery 상점 첫 화면의 낮은 가격

### 고유한 상점 사용(헤드리스 AEM 통합) {#own-storefront}

기존 상점(예: React JS로 작성)이 있고 콘텐츠 관리 및 전달(콘텐츠 조각), 에셋, 컨텍스트 내 편집(범용 편집기)에 Adobe Experience Manager을 사용하려고 합니다. 통합의 시작 지점은 [Adobe Experience Manager as a Headless CMS 소개](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/headless/introduction) 및 [CIF 추가 기능](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/content-and-commerce/storefront/authoring/enrich-product-associated-content)입니다. CIF 추가 기능을 사용하면 제품 데이터를 AEM에 원활하게 통합(AEM UI에서 제품 검색, 탐색 및 찾기)할 수 있습니다. 이러한 기능을 사용하여 상거래별 경험을 구축할 수 있습니다.

### AEM CIF 상점 {#cif}

Adobe의 권장 사항 및 참조 아키텍처는 Edge Delivery Services을 사용하는 것입니다. AEM CIF 핵심 구성 요소가 포함된 CIF 스토어프론트는 이제 유지 관리 모드에 있으므로 새 프로젝트에서 사용해서는 안 됩니다. 참조용으로 [CIF 설명서를 참조하십시오.](/help/commerce-cloud/cif-storefront/introduction.md)

>[!NOTE]
>
>새로운 AEM/Commerce 기능을 활용하려는 기존 고객은 웹 사이트를 Edge Delivery으로 이동해야 합니다. 일반적인 패턴은 페이지의 하위 집합만 Edge Delivery으로 이동하고 Edge Deliery 및 CIF 페이지를 나란히 실행하는 것입니다. 또한 AEM CIF 구성 요소를 새 [Commerce 드롭인 구성 요소](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/?lang=ko)&#x200B;(으)로 교체하여 새로운 Commerce 기능을 활용할 수 있습니다.
