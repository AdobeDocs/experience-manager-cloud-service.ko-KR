---
title: 옵션 - AEM을 사용하여 단일 페이지 애플리케이션(SPA)을 만드는 방법
description: AEM 헤드리스 개발자 여정의 연속(선택 사항)에서는 AEM에서 헤드리스 전달을 일반적인 전체 스택 CMS 기능과 결합하는 방법과 AEM SPA Editor 프레임워크를 사용하여 편집 가능한 SPA을 만드는 방법을 살펴봅니다.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 3fd695cbe77873fa57373d91249b71d8c4be8a08
workflow-type: tm+mt
source-wordcount: '1301'
ht-degree: 1%

---


# AEM {#create-spa}을(를) 사용하여 단일 페이지 애플리케이션(SPA)을 만드는 방법

>[!CAUTION]
>
>진행 중인 작업 - 이 문서의 작성은 진행 중이며 완전한 또는 최종적인 것으로 해석되거나 제작 목적으로 사용되어서는 안 됩니다.

[AEM 헤드리스 개발자 여정의 연속(선택 사항)에서, AEM이 헤드리스 전달을 기존의 전체 스택 CMS 기능과 결합하는 방법, AEM Editor 프레임워크를 사용하여 편집 가능한 SPA을 만드는 방법, 그리고 외부 SPA을 통합하여 편집 기능을 필요한 경우 활성화하는 방법에 대해 알아봅니다.](#overview.md)

## 지금까지 스토리 {#story-so-far}

이 시점에서 전체 [AEM 헤드리스 개발자 여정](overview.md)을 완료하고 다음을 이해하는 것을 포함하여 AEM에서 헤드리스 전달의 기본 사항을 이해해야 합니다.

* 헤드리스 콘텐츠와 헤드리스 콘텐츠 전달 간의 차이점
* AEM 헤드리스 기능
* 헤드리스 프로젝트를 구성하고 AEM 헤드리스 프로젝트를 구성하는 방법
* AEM에서 헤드리스 컨텐츠를 만드는 방법
* AEM에서 헤드리스 컨텐츠를 검색하고 업데이트하는 방법.
* AEM 헤드리스 프로젝트를 라이브하는 방법

이제 첫 AEM 헤드리스 프로젝트를 라이브하거나 그에 필요한 모든 정보를 얻을 수 있습니다. 축하합니다!

왜 여정의 추가적인 선택적 계속을 읽고 있습니까? [시작하기](getting-started.md#integration-levels)에서 AEM이 헤드리스 전달 및 기존의 전체 스택 모델을 지원할 뿐만 아니라 두 가지 장점을 결합하는 하이브리드 모델을 지원할 수 있는 방법을 간략하게 살펴보았습니다. 기존의 헤드리스 모델은 아니지만 이러한 하이브리드 모델은 특정 프로젝트에 탁월한 유연성을 제공할 수 있습니다.

이 문서는 AEM에서 실제로 편집할 수 있는 고유한 단일 페이지 애플리케이션(SPA)을 만드는 방법에 대해 자세히 살펴봄으로써 AEM 헤드리스에 대한 지식을 바탕으로 합니다. 이러한 방식으로 컨텐츠를 제작하여 헤드없이 SPA으로 전달할 수 있지만 SPA은 AEM에서 편집할 수 있습니다.

## 목표 {#objective}

이 문서는 AEM SPA 편집기 프레임워크를 사용하여 단일 페이지 애플리케이션을 개발하는 방법을 이해하는 데 도움이 됩니다. 이 문서를 읽은 후 다음을 수행해야 합니다.

* SPA 편집기의 기본 기능을 파악합니다.
* AEM용 편집 가능한 SPA을 빌드하기 위한 요구 사항에 대해 알아봅니다.
* 외부 SPA을 AEM에 통합하는 방법을 이해합니다.
* 서버측 렌더링을 구현해야 하는지 아니면 구현하지 말아야 하는지 이해합니다.

## 요구 사항 및 필수 조건 {#requirements-prerequisites}

AEM에서 SPA을 사용하기 전에 많은 요구 사항이 있습니다.

### 지식 {#knowledge}

* 반응 또는 Angular 프레임워크을 사용하여 SPA 제작 경험
* 컨텐츠 조각을 만들고 편집기를 사용하는 기본적인 AEM 기술
* 가능한 다양한 수준의 SPA 통합을 이해하려면 AEM](/help/implementing/developing/headful-headless.md)에서 [헤드리스 및 헤드리스 문서를 검토하십시오.

### 도구 {#tools}

* 프로젝트 배포를 테스트하는 샌드박스 액세스
* 데이터 모델링 및 테스트를 위한 로컬 개발 인스턴스
* 기존 외부 SPA(선택한 통합 모델에 따라 선택 사항)
* AEM 프로젝트 전형

## SPA 소개{#what-is-a-spa}

단일 페이지 애플리케이션(SPA)은 클라이언트 측에서 렌더링되고 주로 Javascript를 기반으로 하며 데이터를 로드하고 페이지를 동적으로 업데이트하는 Ajax 호출에 의존한다는 점에서 일반 페이지와 다릅니다. 대부분의 또는 모든 컨텐츠는 페이지와의 사용자 상호 작용에 따라 필요에 따라 비동기적으로 로드된 추가 리소스를 사용하여 단일 페이지를 로드할 때 한 번 검색됩니다.

이를 통해 페이지 새로 고침이 필요하지 않으며, 매끄럽고 빠르며 기본 앱 경험과 같은 경험을 사용자에게 제공합니다.

SPA Editor를 사용하면 프런트 엔드 개발자는 AEM 사이트에 통합할 수 있는 SPA을 제작할 수 있으므로 컨텐츠 작성자는 다른 AEM 컨텐츠처럼 손쉽게 SPA 컨텐츠를 편집할 수 있습니다.

## SPA을 사용해야 하는 이유{#why-spa}

SPA은 기본 애플리케이션과 마찬가지로 빨라지고 유연하며 보다 매력적인 경험을 제공함으로써 웹 페이지 방문자뿐만 아니라 SPA 작업 방식의 특성상 마케터와 개발자에게 매력적인 경험을 제공합니다.

SPA에 대한 자세한 설명과 이를 사용할 이유를 알아보려면 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## SPA 처리 방법

AEM에서 단일 페이지 애플리케이션을 개발하는 경우 프런트 엔드 개발자가 SPA을 만들 때 표준 우수 사례를 관찰한다고 가정합니다. 프런트 엔드 개발자는 이러한 일반적인 모범 사례뿐만 아니라 몇 가지 AEM 전용 원칙을 준수하는 경우 SPA은 AEM 및 컨텐츠 제작 기능을 통해 사용할 수 있습니다.

* **휴대성**  - 모든 컴포넌트와 마찬가지로 가능한 한 휴대할 수 있도록 SPA 컴포넌트를 구축해야 합니다. SPA은 안전하고 재사용 가능한 구성 요소로 구축되어야 합니다.
* **AEM 드라이브 사이트 구조**  - 프런트 엔드 개발자는 구성 요소를 만들고 내부 구조를 소유하지만, AEM을 사용하여 사이트의 컨텐츠 구조를 정의합니다.
* **동적 렌더링**  - 모든 렌더링이 동적이여야 합니다.
* **동적 라우팅**  - SPA은 라우팅을 담당하고 AEM은 이 라우팅을 듣고 이에 따라 페치를 수신합니다. 모든 라우팅도 동적입니다.

AEM에서 SPA을 처리하는 방법에 대한 자세한 설명은 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## AEM SPA 편집기 {#aem-spa-editor}

반응 및 Angular과 같은 일반적인 SPA 프레임워크을 사용하여 구축한 사이트는 동적 JSON을 통해 컨텐츠를 로드하며 AEM 페이지 편집기가 편집 컨트롤을 배치하는 데 필요한 HTML 구조를 제공하지 않습니다.

AEM 내에서 SPA을 편집하려면 컨텐트에 대한 변경 내용을 저장하려면 SPA의 JSON 출력과 AEM 저장소의 컨텐츠 모델 간 매핑이 필요합니다.

AEM의 SPA 지원은 페이지 편집기에서 로드할 때 SPA JS 코드와 상호 작용하는 가상 JS 레이어를 도입하며, 여기서 이벤트를 전송할 수 있고 편집 컨트롤의 위치를 상황에 맞는 편집을 허용할 수 있습니다. 이 기능은 SPA의 컨텐츠를 컨텐츠 서비스를 통해 로드해야 하므로 Content Services API 끝점 개념을 기반으로 구축됩니다.

AEM SPA 편집기에 대한 자세한 설명은 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## 기존 SPA{#existing-spas} 허용

기존 SPA이 있는 경우 AEM은 AEM에 임베드할 수 있으므로 AEM 편집기에서 컨텐츠 작성자가 볼 수 있습니다. 이 기능은 컨텐츠 조각을 통해 작성자가 소비되는 최종 응용 프로그램의 컨텍스트에서 컨텐츠 조각을 통해 작성하는 컨텐츠를 보는 데 매우 유용합니다.

또한 AEM 편집기 내에서 외부 SPA에 대한 특정 편집 기능도 간단히 변경할 수 있습니다.

RemotePage 구성 요소를 사용하면 AEM에서 외부 SPA을 렌더링할 수 있습니다.

외부 SPA을 AEM에서 편집할 수 있게 하는 방법에 대한 자세한 설명은 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## 다음 {#what-is-next} 소개

AEM용 SPA 개발을 시작하려면 다음 문서를 검토하십시오.

* [SPA WKND 자습서](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [반응 사용 시작](/help/implementing/developing/hybrid/getting-started-react.md)
* [angular 사용 시작](/help/implementing/developing/hybrid/getting-started-angular.md)

AEM에서 사용하기 위해 기존 SPA을 수정해야 하는 경우 다음 문서를 검토하십시오.

* [RemotePage 구성 요소](/help/implementing/developing/hybrid/remote-page.md)
* [AEM 내에서 외부 SPA 편집](/help/implementing/developing/hybrid/editing-external-spa.md)

AEM의 SPA 주제에 대해 자세히 알아볼 수 있는 [추가 리소스](#additional-resources)에 대해서는 아래를 참조하십시오.

## 추가 리소스 {#additional-resources}

다음은 이 문서에 언급된 일부 개념에 대한 자세한 설명을 제공하는 추가 리소스입니다.

* [AEM](/help/implementing/developing/headful-headless.md) 의 헤드라인 및 헤드리스 - AEM에서 사용할 수 있는 다양한 전달 모델에 대한 설명입니다.
* [SPA 소개 및 연습.](/help/implementing/developing/hybrid/introduction.md) AEM을 활용한 SPA 소개
* [AEM용 SPA 개발](/help/implementing/developing/hybrid/developing.md)  - AEM용 SPA 개발 방법에 대한 지침
* [SPA 편집기 개요](/help/implementing/developing/hybrid/editor-overview.md)  - SPA 편집기의 작동 방법에 대한 세부 사항
* [서버측 렌더링](/help/implementing/developing/hybrid/ssr.md)  - AEM SPA용 SSR을 구성하는 방법
* [SPA 참조 문서](/help/implementing/developing/hybrid/reference-materials.md)  - JavaScript API 참조 및 오픈 소스 AEM SPA GitHub 프로젝트에 대한 링크
* [컨텐츠 조각](/help/assets/content-fragments/content-fragments.md)  - 컨텐츠 조각을 만드는 방법
* [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)  - 웹 사이트의 시작점으로 모범 사례 기반의 AEM(Adobe Experience Manager) 프로젝트를 최소한으로 생성하는 마비시켜 주는 템플릿
