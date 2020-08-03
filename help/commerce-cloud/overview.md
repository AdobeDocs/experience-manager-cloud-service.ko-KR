---
title: Cloud Service으로 AEM Commerce 소개
description: AEM Commerce에서 Cloud Service의 새로운 기능
translation-type: tm+mt
source-git-commit: c5694cf8651cf8ba5331c730fa1b1180310dd35a
workflow-type: tm+mt
source-wordcount: '1331'
ht-degree: 2%

---


# Cloud Service으로 AEM Commerce 소개 {#commerce-intro}

Cloud Service의 Experience Manager 커머스는 Magento 및 기타 타사 상거래 솔루션에서 Experience Cloud과 상거래 서비스를 통합하고 확장하는 Adobe의 권장 패턴인 CIF(Commerce Integration Framework)로 구성되어 있습니다. 이를 통해 Adobe 고객은 첨단 기술을 기반으로 매력적이고 개인화된 옴니채널 쇼핑 경험을 제공할 수 있습니다.

Commerce Integration Framework는 Cloud Service의 추가 기능 모듈이며 일련의 제작 도구, 구성 요소 및 참조 스토어를 제공하여 Cloud Service과 상거래 솔루션으로서의 Experience Manager 간의 통합 개발을 가속화합니다.

## CIF 혜택 {#cif-benefits}

주요 이점은 다음과 같습니다.

* 통합이 추상화 레이어이므로 여러 시스템과 통합되는 것을 표준화하고 캡슐화할 수 있습니다.

* CIF는 헤드리스/옴니채널 경험을 지원합니다.

   * 단일 페이지 애플리케이션 및 다중 페이지 애플리케이션
   * GraphQL 끝점

* CIF는 커머스 서비스의 맞춤화 및 확장을 위해 서버를 사용하지 않는 마이크로서비스 기반 프로세스와 비즈니스 논리 레이어를 제공합니다.

* CIF는 AEM 및 Magento과 같은 Adobe 솔루션과 즉시 통합

## CIF Elements {#cif-elements}

![CIF Elements](/help/commerce-cloud/assets/cif-overview1.jpg)


### 작성 도구용 CIF 추가 기능 {#add-on-authoring-tools}

CIF Add-On은 작성자를 위한 제품 콘솔, 제품 및 카테고리 선택기 또는 제품 검색과 같은 상거래 저작 도구에 액세스하여 마케팅 및 상거래 컨텐츠가 포함된 풍부한 경험을 만들 수 있도록 합니다. 또한 Add-on은 GraphQL을 통해 Magento(또는 대체 커머스 시스템)에 대한 백엔드 연결을 관리합니다. Add-On이 프로비저닝되면 AEM에 Cloud Service 환경으로 자동으로 배포됩니다.

### AEM CIF 핵심 구성 요소 {#aem-cif-core}

AEM CIF 핵심 구성 요소는 Magento GraphQL 지원을 통해 서버측 및 클라이언트측에서 렌더링된 구성 요소입니다. AEM 기술을 기반으로 정적이고 캐시적이며 SEO 기반의 상거래 스토어를 만드는 데 사용됩니다.

기본 구성 요소가 제공되며 제품 세부 사항, 제품 목록, 탐색, 검색 등과 같은 상거래 구현 간에 공통으로 제공됩니다. 그대로 사용하거나 확장할 수 있습니다.

AEM [CIF 핵심 구성](https://github.com/adobe/aem-core-cif-components) 요소는 [AEM Sites 핵심 구성 요소와](https://github.com/adobe/aem-core-wcm-components) 같이 작동하지만 상거래 특정 사용 사례에만 사용됩니다.

이러한 구성 요소의 주요 이점은 다음과 같습니다.

* 프로젝트에 손쉽게 사용할 수 있습니다.
* 이 변수들은 있는 그대로 사용하거나 매우 최소한의 수정으로 사용할 수 있습니다.
* GraphQL API 또는 REST API를 통해 Magento과 연결하는 모범 사례를 제공합니다

제품 티저 및 제품 회전판과 같은 구성 요소는 AEM Author이 AEM에서 경험 페이지를 만들고 마케팅과 상거래 컨텐츠를 결합할 수 있도록 합니다. 이러한 구성 요소는 AEM에서 만든 컨텐츠 페이지로 쉽게 드래그하여 놓을 수 있으며 Cloud Service의 제품 또는 카테고리 선택기와 같은 CIF 작성 도구를 사용하여 특정 제품 또는 카테고리에 연결할 수 있습니다.

모든 구성 요소는 [GitHub에서 오픈 소스로 제공됩니다](https://github.com/adobe/aem-core-cif-components). 이는 진행 중인 변경 사항에 대한 완전한 투명도를 보여주며 최신 버전을 매우 쉽게 얻을 수 있도록 해줍니다. 또한 통합될 수 있는 개선 및 버그 수정을 위한 풀 요청을 제공할 수 있습니다.

### AEM Venia Storefront {#aem-venia-storefront}

AEM [Venia Storefront](https://github.com/adobe/aem-cif-guides-venia) 는 기본적인 B2C 커머스 여정을 소개하는 최신 프로덕션 지원 참조 스토어프런트입니다. AEM, CIF 및 Magento을 사용하여 상거래 프로젝트를 시작하고 프로젝트를 가속화하는 데 사용할 수 있습니다. AEM 및 Magento 통합에 대한 우수 사례를 보여 주고 [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components) 및 [AEM Sites 핵심 구성 요소를 사용하는 방법을 보여 주며 Adobe 상거래 그래프QL 끝점을](https://github.com/adobe/aem-core-wcm-components) 지원합니다. 또한 AEM과 Magento 간의 통합을 시연할 수 있는 참조 사이트가 포함된 사전 판매 사이트도 제공합니다.

AEM Venia Storefront는 AEM이 유리를 소유하고 있고 Magento이 헤드리스 방식으로 상거래 백엔드를 작동시키는 혼합 페이지 애플리케이션입니다. 서버측 렌더링과 클라이언트측 렌더링을 모두 스토어프런트에서 사용합니다. 서버측 렌더링을 사용하여 정적 컨텐츠를 전달하고 클라이언트측 렌더링을 사용하여 동적 컨텐츠를 전달할 수 있습니다.

제품 및 카탈로그 페이지는 비교적 정적이며 AEM에서 만든 일반 템플릿의 제품 세부 정보 및 제품 목록과 같은 AEM CIF 핵심 구성 요소를 사용하여 서버측에서 렌더링됩니다. 이러한 구성 요소는 GraphQL API를 통해 Magento에서 데이터를 가져옵니다.
이러한 페이지는 동적으로 만들어져 서버에서 렌더링되고 AEM 디스패처에 캐시되어 브라우저에 전달됩니다.
재고 또는 가격과 같은 동적 속성의 경우 클라이언트측 구성 요소가 사용됩니다. 클라이언트측 구성 요소 또는 웹 구성 요소는 GraphQL API를 통해 Magento에서 직접 데이터를 반입한 다음 컨텐츠를 브라우저에서 렌더링합니다.

#### 체크아웃 {#checkout}

이 참조 스토어프런트는 장바구니와 체크아웃 양식을 렌더링하는 클라이언트측 장바구니 구성 요소를 사용하여 완전히 헤드리스 방식으로 실행되는 Magento과 유리를 소유하는 AEM이 포함된 상거래 경험을 전달할 수 있는 완벽한 경험 통합 패턴을 보여줍니다. 제공된 추상적 지불 방법을 사용하는 것이 좋습니다. 이렇게 하면 브라우저 클라이언트가 결제 게이트웨이 공급자와 직접 통신하므로 Adobe 및 Magento 클라우드가 PCI 중요 데이터를 저장하거나 전달하지 않습니다.

#### 계정 관리 {#account-management}

계정 관리는 Magento에 의해 처리되며 참조 스토어프런트는 클라이언트측 반응 기반 구성 요소를 활용하여 AEM이 다음 기능에 대한 경험을 렌더링할 수 있도록 합니다. 계정 만들기, 로그인 및 암호 분실

AEM Venia Storefront 프로젝트는 오픈 소스이며 자세한 내용은 [AEM Storefront를 참조하십시오](https://github.com/adobe/aem-cif-guides-venia).

### AEM 프로젝트 전형 {#aem-project-archtype}

The [AEM Project Archetype](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html) can be used to create a minimal, best-practices-based Adobe Experience Manager project as a starting point for your own AEM projects. 선택적으로 [AEM CIF 핵심 구성 요소를](https://github.com/adobe/aem-core-cif-components) 새로 생성된 프로젝트에 포함시킬 수 있습니다.

### CIF 익스텐션 레이어 {#cif-extension}

CIF 확장 레이어는 복잡한 비즈니스 로직을 호스팅하기 위한 중간 레이어입니다. 그것은 Adobe의 서버리스 플랫폼인 Adobe I/O Runtime 플랫폼에서 실행됩니다. 마이크로 서비스 수준에서 비즈니스 및 프로세스 로직을 삽입하여 엔드 투 엔드 서비스 호출을 확장할 수 있습니다. 예를 들어 위치 및 채널을 사용하여 인벤토리 전략을 결정하는 비즈니스 논리가 필요합니다. 프로세스 로직은 예를 들어 개인화된 정보를 검색할 수 있습니다.

### CIF 통합 레이어 {#cif-integration-layer}

CIF 통합 레이어는 다른 상거래 솔루션과의 통합을 표준화하는 데 사용됩니다. Adobe의 서버를 사용하지 않는 플랫폼인 Adobe I/O Runtime 플랫폼에서 실행되며 Adobe 커머스 API에 대해 타사 API를 매핑하여 마이크로서비스 수준에서 통합을 활성화합니다. AEM와의 타사 통합 구축을 시작하기 위해 Adobe는 Magento이 아닌 상거래 백엔드를 Adobe 상거래 API(Magento GraphQL API)를 통해 통합하는 방법을 보여주는 [참조 구현을](https://github.com/adobe/commerce-cif-graphql-integration-reference) 만들었습니다.

## AEM Commerce 통합 패턴 {#aem-commerce-integration}

일반적으로 구현되는 AEM Commerce 통합 패턴 중 일부가 아래에 나와 있습니다.

![AEM CIF 통합 패턴](/help/commerce-cloud/assets/aem-cif-integration-patterns-updated.JPG)


### 통합 패턴 1 {#integration-pattern-one}

이는 AEM이 전체 유리를 소유하고 Adobe Commerce GraphQL API를 통해 상거래 서비스를 통합하는 권장 통합 패턴입니다. 이 패턴은 다양한 디바이스에서 리치 미디어 사이트 디자인을 맞춤화하는 AEM의 완벽한 유연성을 보장합니다. 이 통합 패턴은 기본적으로 제공되는 솔루션으로 CIF에서 지원합니다.


### 통합 패턴 2 {#integration-pattern-two}

이 패턴은 컨텐츠와 커머스를 전달하는 헤드리스 방식을 나타냅니다. 배달은 완전히 클라이언트측에서 제공됩니다. 이 패턴 콘텐츠는 API를 통해 제공되며 HTML 및 상거래 데이터는 GraphQL을 통해 배달됩니다. 이 패턴은 현재 CIF에서 기본적으로 지원되지 않습니다.


### 통합 패턴 3 {#integration-pattern-three}

이 패턴에서 Magento은 유리를 소유하고 AEM이 제작한 컨텐츠를 임베드합니다. AEM에서 제작한 컨텐츠는 경험 조각 또는 컨텐츠 조각을 통해 전달할 수 있습니다. 이 통합 패턴은 프로젝트별 작업이 필요하며 CIF를 통해 즉시 구현할 수 없습니다.


### 통합 패턴 4 {#integration-pattern-four}

이것은 유리 또는 프레젠테이션 레이어가 AEM과 상거래 솔루션 간에 분할되는 일반적인 통합 패턴입니다. 일반적으로, 상거래 솔루션은 체크아웃, 내 계정, AEM과 같은 비마케팅 페이지를 전달하며 마케팅 페이지와 스토어프런트 카탈로그 환경을 제공합니다. 이 패턴에서는 장바구니 및 사용자 세션이 두 시스템 간에 제대로 처리되어 사용자 환경이 단절되지 않도록 해야 합니다. 예를 들어 Magento은 장바구니 및 사용자 세션을 쿠키에 저장하며 AEM 및 Magento 간에 공유할 수 있습니다. 이 패턴은 프로젝트별 작업이 필요하며 CIF를 통해 즉시 구현할 수 없습니다.
