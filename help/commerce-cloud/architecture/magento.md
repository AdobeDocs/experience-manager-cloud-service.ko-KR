---
title: 커머스 통합 프레임워크를 사용한 AEM 및 Magento 통합
description: AEM 및 Magento은 CIF(Commerce Integration Framework)를 사용하여 완벽하게 통합됩니다. CIF를 사용하면 AEM에서 Magento 인스턴스에 액세스하고 GraphQL을 통해 Magento과 통신할 수 있습니다. 또한 AEM 작성자는 제품 및 카테고리 선택기 및 제품 콘솔을 사용하여 Magento에서 온디맨드로 가져오는 제품 및 카테고리 데이터를 검색할 수 있습니다. 또한 CIF는 상거래 프로젝트를 가속화할 수 있는 최신 스토어를 제공합니다.
thumbnail: aem-magento-architecture.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 1%

---


# 전자 상거래 통합 프레임워크를 사용한 AEM 및 Magento 통합 {#aem-magento-framework}

AEM 및 Magento은 CIF(Commerce Integration Framework)를 사용하여 완벽하게 통합됩니다. CIF를 사용하면 AEM에서 Magento 인스턴스에 액세스하고 GraphQL을 통해 Magento과 통신할 수 있습니다. 또한 AEM 작성자는 제품 및 카테고리 선택기 및 제품 콘솔을 사용하여 Magento에서 온디맨드로 가져오는 제품 및 카테고리 데이터를 검색할 수 있습니다. 또한 CIF는 상거래 프로젝트를 가속화할 수 있는 최신 스토어를 제공합니다.

## 아키텍처 개요 {#overview}

전체 아키텍처는 다음과 같습니다.

![CIF 아키텍처 개요](../assets/AEM_Magento_Architecture.JPG)

CIF는 GraphQL 지원을 기반으로 구축됩니다. AEM과 Magento 간의 주 통신 채널은 Magento [GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql/) API입니다. AEM 간의 통신을 Cloud Service과 Magento으로 구성하는 방법에는 여러 가지가 있습니다. 자세한 내용은 [시작하기](../getting-started.md) 페이지를 참조하십시오.

CIF에서는 서버측 및 클라이언트측 커뮤니케이션 패턴을 지원합니다.
서버측 API 호출은 Magento GraphQL 스키마에 대해 생성된 데이터 모델](https://github.com/adobe/commerce-cif-magento-graphql)의 [세트와 함께 빌드 인 일반 [GraphQL 클라이언트](https://github.com/adobe/commerce-cif-graphql-client)을 사용하여 구현됩니다. 또한 모든 GraphQL 쿼리 또는 GQL 포맷의 돌연변이를 사용할 수 있습니다.

[Response](https://reactjs.org/)를 사용하여 빌드하는 클라이언트측 구성 요소의 경우 [Apollo Client](https://www.apollographql.com/docs/react/)이 사용됩니다.

## AEM CIF 핵심 구성 요소 아키텍처 {#cif-core-components}

![AEM CIF 핵심 구성 요소 아키텍처](../assets/cif-component-architecture.jpg)

[AEM CIF 코어 ](https://github.com/adobe/aem-core-cif-components) 구성 요소는  [AEM WCM 핵심 구성 요소와 같이 매우 유사한 디자인 패턴과 모범 사례를 따릅니다](https://github.com/adobe/aem-core-wcm-components).

AEM CIF 핵심 구성 요소에 대한 Magento을 통한 비즈니스 논리 및 백엔드 통신은 Sling 모델에 구현됩니다. 프로젝트 특정 요구 사항을 충족하기 위해 이 논리를 사용자 정의해야 하는 경우 Sling 모델에 대한 위임 패턴을 사용할 수 있습니다.

>[!TIP]
>
>[AEM CIF 핵심 구성 요소 사용자 지정](../customizing/customize-cif-components.md) 페이지에는 CIF 핵심 구성 요소를 사용자 지정하는 방법에 대한 자세한 예와 우수 사례가 있습니다.

프로젝트 내에서 AEM CIF 핵심 구성 요소 및 사용자 지정 프로젝트 구성 요소는 Sling 컨텍스트 인식 구성을 통해 AEM 페이지와 연결된 Magento 저장소에 대해 구성된 클라이언트를 쉽게 검색할 수 있습니다.
