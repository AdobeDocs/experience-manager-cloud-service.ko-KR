---
title: 상거래 통합 프레임워크를 사용한 AEM 및 제3자 상거래 통합
description: 기업 기업은 스토어를 가동하기 위해 제3자 상거래 솔루션을 추가로 요구할 수 있습니다. 이러한 통합 시나리오에서 CIF(Commerce Integration Framework)를 사용하여 I/O 런타임을 사용하여 제3자 상거래 솔루션을 Adobe Experience Manager에 연결할 수 있습니다.
thumbnail: cif-third-party-architecture.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 1%

---


# 상거래 통합 프레임워크를 사용한 AEM 및 제3자 상거래 통합 {#aem-third-party}

기업 기업은 스토어를 가동하기 위해 제3자 상거래 솔루션을 추가로 요구할 수 있습니다. CIF(Commerce Integration Framework)는 이러한 통합 시나리오에서 사용할 수 있으며, Magento 외에도 제3자 상거래 솔루션을 AEM과 통합해야 합니다. CIF는 액셀러레이터 참조 스토어프론트, AEM CIF 핵심 구성 요소 및 즉시 사용 가능한 Magento과 연동되는 제작 도구와 같은 요소를 제공합니다. AEM 및 제3자 상거래 솔루션을 통합하고 이러한 CIF 요소를 다시 사용하려면 몇 가지 추가 개발이 필요합니다.

## 아키텍처 {#architecture}

전체 아키텍처는 다음과 같습니다.

![AEM 비 Magento/타사 아키텍처 개요](/help/commerce-cloud/assets/AEM_nonMagento_Architecture.JPG)

AEM(Magento)과 AEM(3rd party) 커머스에 대한 통합 아키텍처의 주요 차이점은 위 이미지에 표시된 대로 통합 및 데이터 변형 레이어가 추가되는 것입니다. 통합 레이어는 Adobe의 서버리스 플랫폼인 Adobe I/O Runtime 플랫폼에서 호스팅되어야 합니다. Adobe I/O Runtime [여기에서 ](https://www.adobe.io/apis/experienceplatform/runtime.html)에 대해 자세히 알아볼 수 있습니다.

이 통합 레이어의 목적은 Magento이 아닌 API 또는 타사 API를 Adobe 상거래 API(Magento GraphQL API)에 매핑하는 것입니다. 이 매핑을 사용하면 [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components) 및 CIF 작성 도구를 사용하여 Magento이 아닌 솔루션에서 데이터를 검색할 수 있습니다. 이러한 접근 방식을 통해 통합 레이어는 통합 로직을 캡슐화하고 AEM과 타사 솔루션 간의 관심사를 분리시켜 줍니다. 이를 통해 다양한 타사 솔루션과 함께 CIF 요소를 독립적인 방식으로 사용할 수 있습니다. 프로젝트에서 CIF 요소를 사용할 때의 이점은 [소개](/help/commerce-cloud/overview.md)에 설명되어 있습니다.

## 통합 {#develop-integration} 개발

Magento/타사 솔루션을 AEM과 통합하기 위해 필요한 통합 레이어를 구축하는 데 도움이 되도록 [참조 구현](https://github.com/adobe/commerce-cif-graphql-integration-reference)을(를) 만들어 이를 입증했습니다. 이 참조를 프로젝트에서 시작점으로 사용할 수 있습니다.
