---
title: 선택 사항 - AEM을 통해 단일 페이지 애플리케이션(SPA)을 제작하는 방법
description: 지속적인 AEM Headless 개발자 여정의 이 선택적인 구성에서는 AEM이 Headless 게재를 기존 전체 스택 CMS 기능과 결합하는 방법과 AEM의 SPA 편집기 프레임워크를 통해 편집 가능한 SPA를 제작하는 방법에 대해 알아봅니다.
exl-id: d74848f2-683e-49e1-9374-32596ca5d7d7
source-git-commit: 6be7cc7678162c355c39bc3000716fdaf421884d
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 100%

---

# AEM을 통해 단일 페이지 애플리케이션(SPA)을 제작하는 방법 {#create-spa}

지속적인 [AEM Headless 개발자 여정](overview.md)의 이 선택적인 구성에서는 AEM이 Headless 게재를 기존 전체 스택 CMS 기능과 결합하는 방법, AEM의 SPA 편집기 프레임워크를 통해 편집 가능한 SPA를 제작하는 방법과 필요에 따라 편집 기능을 사용하여 외부 SPA를 통합하는 방법에 대해 알아봅니다.

## 지금까지의 스토리 {#story-so-far}

이 시점에서 전체 [AEM Headless 개발자 여정](overview.md)을 완료하고 다음에 대한 이해를 비롯해 AEM의 Headless 게재에 대한 기본 사항을 이해해야 합니다.

* Headless 콘텐츠 게재와 Headful 콘텐츠 게재의 차이점.
* AEM의 Headless 기능.
* AEM Headless 프로젝트를 구성하고 방법.
* AEM에서 Headless 콘텐츠를 만드는 방법
* AEM에서 Headless 콘텐츠를 검색하여 업데이트하는 방법.
* AEM Headless 프로젝트를 실행하는 방법.

이제 첫 번째 AEM Headless 프로젝트를 실행했거나 이에 필요한 모든 지식을 갖게 되었습니다. 축하합니다!

그러면 이 지속적인 여정의 선택적인 추가 구성을 읽는 이유는 무엇입니까? [시작하기](getting-started.md#integration-levels)에서 AEM이 Headless 게재와 기존 전체 스택 모델뿐만 아니라 두 가지 장점을 결합한 하이브리드 모델을 지원하는 방법에 대해 간략하게 논의했던 것으로 기억할 것입니다. 기존 Headless 모델은 아니지만 해당 하이브리드 모델은 특정 프로젝트에 탁월한 유연성을 제공할 수 있습니다.

이 문서는 AEM Headless에 대한 지식을 기본으로 하며, 이를 통해 AEM에서 실제로 편집할 수 있는 자체 단일 페이지 애플리케이션(SPA)을 제작하는 방법에 대해 자세히 살펴볼 수 있습니다. 이렇게 콘텐츠를 만들어 SPA에 Headless 방식으로 게재할 수 있지만 해당 SPA는 AEM에 편집 가능한 상태로 유지됩니다.

## 목표 {#objective}

이 문서는 AEM SPA 편집기 프레임워크를 통해 단일 페이지 애플리케이션을 개발하는 방법을 이해하는 데 도움이 됩니다. 이 문서를 읽고 나면

* SPA 편집기의 기본 기능을 이해할 수 있습니다.
* 완전히 편집 가능한 AEM용 SPA를 빌드하기 위한 요구 사항을 파악할 수 있습니다.
* 외부 SPA를 AEM에 통합할 수 있는 방법을 이해할 수 있습니다.
* 서버측 렌더링을 구현하거나 구현하지 않는 방법을 이해할 수 있습니다.

## 요구 사항 및 사전 요구 사항 {#requirements-prerequisites}

AEM에서 SPA로 작업을 시작하기 전에 알아 두어야 할 몇 가지 요구 사항이 있습니다.

### 지식 {#knowledge}

* React 또는 Angular 프레임워크를 통해 SPA를 만드는 개발 경험
* 콘텐츠 조각을 만들고 편집기를 사용하는 기본 AEM 기술
* 다양한 SPA 통합 수준을 이해하려면 [AEM Headful 및 Headless](/help/implementing/developing/headful-headless.md) 문서를 검토해야 합니다.

### 도구 {#tools}

* 콘텐츠 배포 테스트를 위한 샌드박스 액세스
* 데이터 모델링 및 테스트에 대한 로컬 개발 인스턴스
* 기존 외부 SPA (선택한 통합 모델에 따라 선택할 수 있음)
* AEM Project Archetype

## SPA란 무엇입니까? {#what-is-a-spa}

단일 페이지 애플리케이션(SPA)은 데이터를 로드하여 페이지를 동적으로 업데이트하는 Ajax 호출을 통해 클라이언트측에서 렌더링되고 주로 JavaScript를 기반으로 하는 기존 페이지와 다릅니다. 페이지와의 사용자 상호 작용을 기반으로 필요에 따라 대부분의 콘텐츠 또는 모든 콘텐츠를 추가 리소스가 비동기적으로 로드된 단일 페이지 로드에서 한 번 검색합니다.

이렇게 하면 페이지 새로 고침의 필요성이 줄어들고 사용자에게 원활하고 빠르며 기본 앱 환경과 같은 경험을 제공할 수 있습니다.

AEM SPA 편집기를 통해 프론트엔드 개발자가 AEM 사이트에 통합할 수 있는 SPA를 만들게 되면 콘텐츠 작성자는 다른 AEM 콘텐츠와 같이 SPA 콘텐츠를 손쉽게 편집할 수 있습니다.

## 왜 SPA입니까? {#why-spa}

더 빠르고 유동적이며 기본 애플리케이션과 매우 유사한 SPA는 작동 방법의 특성으로 인해 웹 페이지 방문자뿐만 아니라 마케터와 개발자에게도 매우 매력적인 경험입니다.

SPA와 SPA를 사용하는 이유에 대한 전체 내용은 보다 심층적인 설명서 링크를 위한 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## AEM을 통해 SPA를 처리하는 방법

AEM을 통해 단일 페이지 애플리케이션을 개발하면 프론트엔드 개발자가 SPA를 제작하는 도중 표준 모범 사례를 준수하는 것으로 간주됩니다. 프론트엔드 개발자가 해당 일반 모범 사례와 몇 가지 AEM 특정 원칙을 준수하면 SPA는 AEM과 콘텐츠 작성 기능과 함께 작동합니다.

* **이동성** - 모든 구성 요소와 마찬가지로 SPA 구성 요소는 최대한 이동할 수 있도록 빌드해야 합니다. SPA는 이동 및 재사용할 수 있는 구성 요소로 빌드해야 합니다.
* **AEM 실행 사이트 구조** - 프론트엔드 개발자는 구성 요소를 만들고 내부 구조를 가지고 있지만 AEM을 사용하여 사이트의 콘텐츠 구조를 정의할 수 있습니다.
* **동적 렌더링** - 모든 렌더링은 동적이어야 합니다.
* **동적 라우팅** - SPA는 라우팅을 담당하고 이에 따라 AEM은 라우팅을 수신하고 가져옵니다. 모든 라우팅 또한 동적이어야 합니다.

AEM을 통해 SPA를 처리하는 방법에 대한 전체 내용은 보다 심층적인 설명서 링크를 위한 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## AEM SPA 편집기 {#aem-spa-editor}

React, Angular와 같은 일반적인 SPA 프레임워크를 사용하여 빌드한 사이트는 동적 JSON을 통해 콘텐츠를 로드하고 AEM 페이지 편집기에서 편집 컨트롤을 배치하는 데 필요한 HTML 구조를 제공하지 않습니다.

AEM 내에서 SPA 편집 기능을 활성화하려면 SPA의 JSON 출력과 AEM 저장소의 콘텐츠 모델 간에 매핑을 사용하여 콘텐츠에 대한 변경 사항을 저장해야 합니다.

AEM의 SPA 지원을 통해 페이지 편집기에 로드하는 경우 SPA JS 코드와 상호 작용하는 얇은 JS 레이어를 도입하여 이벤트를 전송할 수 있고 편집 컨트롤 위치를 활성화하여 상황에 맞게 편집할 수 있습니다. 콘텐츠 서비스를 통해 SPA의 콘텐츠를 로드해야 하므로 이 기능이 콘텐츠 서비스 API 엔드포인트 개념에 빌드됩니다.

AEM SPA 편집기에 대한 전체 내용은 보다 심층적인 설명서 링크를 위한 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## 기존 SPA 수용 {#existing-spas}

기존 SPA가 있는 경우 AEM 편집기의 콘텐츠 작성자에게 표시되도록 AEM은 SPA를 AEM에 임베드하는 것을 지원합니다. 사용할 수 있는 최종 애플리케이션의 컨텍스트에서 콘텐츠 조각을 통해 제작되는 콘텐츠를 확인하는 데 매우 유용합니다.

또한 약간의 변경만으로도 AEM 편집기에서 외부 SPA에 대한 특정 편집 기능을 활성화할 수 있습니다.

RemotePage 구성 요소를 사용하여 AEM에서 외부 SPA를 렌더링할 수 있습니다.

AEM에서 편집 가능한 외부 SPA를 만드는 방법에 대한 전체 내용은 보다 심층적인 설명서 링크를 위한 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## 다음 단계 {#what-is-next}

AEM용 SPA 개발을 시작하려면 다음 문서를 검토합니다.

* [SPA WKND 튜토리얼](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [React를 사용하여 시작하기](/help/implementing/developing/hybrid/getting-started-react.md)
* [Angular를 사용하여 시작하기](/help/implementing/developing/hybrid/getting-started-angular.md)

AEM에 사용할 기존 SPA를 조정해야 하는 경우 다음 문서를 검토합니다.

* [RemotePage 구성 요소](/help/implementing/developing/hybrid/remote-page.md)
* [AEM에서 외부 SPA 편집](/help/implementing/developing/hybrid/editing-external-spa.md)

AEM에서 SPA 주제에 대해 자세히 살펴볼 수 있는 [추가 리소스](#additional-resources)는 아래를 참조하십시오.

## 추가 리소스 {#additional-resources}

다음은 이 문서에서 언급한 몇 가지 개념에 대해 자세히 설명하는 몇 가지 추가 리소스입니다.

* [AEM Headful 및 Headless](/help/implementing/developing/headful-headless.md) - AEM에 제공되는 다른 게재 모델에 대한 설명
* [SPA 소개 및 워크스루.](/help/implementing/developing/hybrid/introduction.md) - AEM의 SPA에 대한 소개
* [AEM용 SPA 개발](/help/implementing/developing/hybrid/developing.md) - AEM용 SPA를 개발하는 방법에 대한 지침
* [SPA 편집기 개요](/help/implementing/developing/hybrid/editor-overview.md) - SPA 편집기의 작동 방식에 대한 세부 정보
* [서버측 렌더링](/help/implementing/developing/hybrid/ssr.md) - AEM SPA용 SSR을 구성하는 방법
* [SPA 참조 문서](/help/implementing/developing/hybrid/reference-materials.md) - 오픈 소스 AEM SPA GitHub 프로젝트에 대한 JavaScript API 참조 및 링크
* [콘텐츠 조각](/help/sites-cloud/administering/content-fragments/content-fragments.md) - 콘텐츠 조각을 만드는 방법
* [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) - Adobe Experience Manager(AEM) 프로젝트를 웹 사이트 시작 지점으로 만드는 최소한의 모범 사례 기반 Maven 템플릿
