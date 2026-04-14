---
title: Experience 현대화 에이전트 개요
description: Experience 현대화 에이전트가 AI의 도움을 받아 Edge Delivery Services에 새 웹 사이트를 온보딩하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: c23a6f55-2ba8-4290-b7e8-06cad5de0fc8
source-git-commit: 95e3046fca3cc2ede57d9e1e9a4ff01a0ba566c3
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---


# Experience 현대화 에이전트 개요 {#experience-modernization-agent}

Experience 현대화 에이전트가 AI의 도움을 받아 Edge Delivery Services에 웹 사이트를 온보딩하는 방법에 대해 알아봅니다.

## 소개 {#introduction}

[Brand Experience Agent의 일부로 &#x200B;](/help/ai-in-aem/agents/brand-experience/overview.md) Experience Modernation Agent는 웹 사이트 마이그레이션 및 기본 사이트 설정을 자동화하여 Edge Delivery Services에 대한 온보딩을 가속화합니다.

초기 웹 사이트 온보딩을 위한 [사이트 생성 및 마이그레이션 기술](#creation-migration)과 사이트 생성 및 마이그레이션 워크플로를 지원하기 위한 [개발 기능 차단](#block-development)을 결합합니다. 또한 웹 기반 AI 지원 개발 환경으로 [경험 현대화 콘솔](#console)을 직접 사용할 수 있습니다. 사용자는 해당 콘솔을 통해 직접 에이전트를 작동할 수 있지만, 개발자는 어떤 선박에 대한 모든 권한을 유지합니다.

복잡하거나 우선 순위가 높은 마이그레이션의 경우 Adobe은 Experience Modernation Agent를 사용하여 프로덕션 준비가 완료된 Edge Delivery 사이트를 제공하도록 설계된 [AOE(Agentic Result Engineer) 게재 모델](#aoe-delivery)을 제공합니다.

## 이점 {#benefits}

Experience 현대화 에이전트는 [Edge Delivery Services](/help/edge/overview.md) 채택의 가치 창출 시간을 단축하고 브랜드의 웹 경험을 조정할 수 있는 민첩성을 제공합니다.

* **고속**: AI 자동화는 반복적인 마이그레이션 작업(콘텐츠 가져오기, 블록 매핑, 시스템 응용 프로그램 디자인)을 처리하므로 기존 접근 방식과 비교하여 마이그레이션 타임라인이 압축됩니다
* **효율성 중심**: 자동화는 반복 작업을 줄여 팀이 더 높은 가치의 구현 작업에 집중할 수 있도록 합니다.
* **모든 사용자가 액세스할 수 있음**: 자연어 요청을 사용하면 웹 사이트 변경 내용에 액세스할 수 있으며 실시간 미리 보기를 통해 변경 내용의 유효성을 즉시 확인할 수 있습니다
* **엔터프라이즈 거버넌스**: 개발자는 GitHub와 통합된 검토 워크플로를 통해 수행되는 작업에 대한 모든 권한을 유지합니다.
* **마이그레이션 후 유연성**: 팀이 Edge Delivery Services 패턴을 사용하여 마이그레이션된 사이트를 확장하고 세분화할 수 있습니다.

## 사이트 생성 및 마이그레이션 기술 {#creation-migration}

Experience 현대화 에이전트는 새 Edge Delivery Services 사이트를 만들고 기존 웹 사이트를 마이그레이션하는 기술을 제공합니다. 새로운 Edge Delivery Services 사이트 또는 마이그레이션은 이러한 기술을 활용하는 것이 좋습니다.

* 몇 개월에서 몇 주 또는 며칠에 걸쳐 웹 사이트 생성 및 마이그레이션을 가속화하여 Edge Delivery Services 채택에 소요되는 시간을 대폭 단축
* 광범위한 CMS 플랫폼, 레거시 AEM 또는 디자인 시스템(예: Figma)에서 프로덕션 지원 Edge Delivery Services 프로젝트로의 마이그레이션을 지원합니다.
* Edge Delivery Services 지침에 따른 성능, 접근성 및 반응형 디자인에 대한 모범 사례를 지원합니다

자세한 기술에는 페이지 마이그레이션, 대량 가져오기, 디자인 추출, 탐색 설정 및 웹 스크래핑 등이 있습니다.

## 블록 개발 기능 {#block-development}

Experience Modernation Agent는 다양한 개발 작업을 제공하는 일반적인 Edge Delivery Services 개발 기능을 활용하여 초기 사이트 생성 또는 마이그레이션 이상의 지속적인 가치를 제공합니다.

* 작성자에게 친숙한 콘텐츠 모델을 위한 CDD(Content-Driven Development) 방법론을 따릅니다
* [컬렉션 차단](https://www.aem.live/developer/block-collection) 및 [파티 차단](https://www.aem.live/developer/block-party/)을 활용하여 참조 구현 및 모범 사례를 찾습니다.
* 배포 전 변경 내용의 유효성을 검사하기 위한 테스트 및 디버깅 워크플로 지원

세부 기능에는 블록 개발, 콘텐츠 모델링, 참조 블록 검색, 테스트 및 디버깅이 포함됩니다.

## 경험 현대화 콘솔 {#console}

Experience 현대화 에이전트는 [`aemcoder.adobe.io`.](https://aemcoder.adobe.io)에서 웹 인터페이스로 노출된 Edge Delivery Services을 위한 웹 기반 AI 지원 개발 환경을 제공합니다.

* 사용자가 즉시 자연어로 변경 내용을 묻기 시작할 수 있도록 콘솔을 로컬 설정할 필요가 없습니다.
* 라이브 AEM 미리 보기를 통해 미리보는 동안 일상적인 경험 개발 작업을 빠르게 수행하고 콘텐츠를 AEM에 동기화할 수 있습니다.
* 콘솔은 표준 GitHub 검토 워크플로우를 통해 기업 거버넌스를 지원합니다.

셀프 서비스 경험 현대화 콘솔 은 일반적으로 사용할 수 있습니다. 관심이 있는 사용자는 원활한 온보딩 경험을 보장하기 위해 액세스 권한을 요청할 수 있습니다.

Experience Modernation Console을 시작합니다!

* 문서 작성을 타깃팅하여 사이트를 현대화하는 경우 [여기에서 시작하십시오.](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md)
* AEM 작성을 타깃팅하여 사이트를 현대화하는 경우 [여기에서 시작하십시오.](/help/ai-in-aem/agents/brand-experience/modernization/getting-started-aem-authoring.md)

## 프로젝트 설명서 스킬 {#project-documentation}

프로젝트 진행자의 시간이 많이 소요되는 특성을 인식하므로 작성 및 개발 작업이 완료되면 [프로젝트 설명서 기술](/help/ai-in-aem/agents/brand-experience/modernization/project-documentation.md)이 포괄적인 설명서를 자동으로 생성할 수 있습니다.

## AOE(Agentic Outcome Engineer) 게재 {#aoe-delivery}

복잡한 마이그레이션 또는 가속화된 결과를 위해 Adobe은 AOE(Agentic Outcome Engineer) 서비스를 제공합니다. 이는 Adobe 엔지니어가 사용자를 대신하여 Experience Modernation Agent를 운영하는 선택적 서비스로, AI 자동화와 전문가 지침을 결합하여 규모에 맞게 제작 준비가 완료된 결과를 제공합니다. AOE 게재에 대한 자세한 내용은 [경험 현대화 에이전트의 AOE 게재](/help/ai-in-aem/agents/brand-experience/modernization/aoe-delivery.md) 문서를 참조하십시오.

다음 마이그레이션에 대한 AOE 모델에 관심이 있는 경우:

* 범위 지정 및 일정을 시작하려면 Adobe 담당자 또는 계정 팀에 문의하십시오.
* Adobe은 자격 조건을 확인하고 참여를 예측하며 참여 계획을 제안합니다.

## 제한 사항 {#limitations}

다음 사용 사례에서는 경험 현대화 에이전트의 기술 외에 추가적인 구현 노력이 필요합니다.

스크래핑 스킬은 다음 소스를 지원하지 않습니다.

* 인트라넷 또는 액세스 불가능한 인증, VPN 또는 방화벽 뒤의 콘텐츠와 같은 보호된 소스
* 정교한 사용자 상호 작용이 필요한 콘텐츠와 같은 복잡한 동적 콘텐츠가 DOM에 표시됩니다.
   * 특정 URL을 통해 콘텐츠에 액세스할 수 있는 경우 클라이언트측 렌더링된 콘텐츠가 지원됩니다.
   * CSS를 통해 숨겨져 있지만 탭, 아코디언 또는 카루셀과 같은 DOM에 있는 요소도 지원됩니다.

에이전트가 다음 대상을 지원하지 않습니다.

* 사이트에서 HTL 기반 전달을 사용하는 AEM 게시 환경
   * 이 기술은 Edge Delivery Services만 타깃팅합니다.
* API 전용 또는 SPA 기반 게재와 같은 헤드리스 게재 패턴(예: Next.js)

다음 요구 사항은 전용 자동화 기술에서 다루지 않으며 수작업이 필요합니다.

* 엄격한 픽셀 완성도
   * 실용적인 설계 충실도만 자동화됩니다.
* 서버 또는 클라이언트측 타사 데이터/서비스 통합
* 상거래 또는 검색 기능 통합
* MarTech 데이터 레이어 또는 타겟팅/실험
* 컨텐츠/경험 조각 격리
* 다중 사이트 상속(MSM)
* 사용자 정의 기능(예: 계산기, 구성자)
* 사용자 정의 비즈니스 논리

## 다음 단계 {#next-steps}

[Experience Modernation Agent 시작하기](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md) 문서를 사용하여 사이트를 마이그레이션하여 시작하십시오.
