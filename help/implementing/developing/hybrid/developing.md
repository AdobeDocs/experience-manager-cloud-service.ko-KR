---
title: AEM용 SPA 개발
description: 이 문서에서는 프론트엔드 개발자에게 AEM용 SPA을 개발하도록 요청할 때 고려해야 할 중요한 질문을 제시하고 AEM에서 개발된 SPA을 배포할 때 AEM과 관련된 SPA의 아키텍처에 대한 개요를 제공합니다.
exl-id: f6c6f31a-69ad-48f6-b995-e6d0930074df
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '2072'
ht-degree: 12%

---

# AEM용 SPA 개발 {#developing-spas-for-aem}

SPA(단일 페이지 애플리케이션)는 웹 사이트 사용자에게 적합한 멋진 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크를 사용하여 사이트를 작성하려고 하며 작성자는 해당 프레임워크를 통해 빌드된 사이트의 AEM 내에서 콘텐츠를 원활하게 편집하려고 합니다.

이 문서에서는 프론트엔드 개발자에게 AEM용 SPA을 개발하도록 요청할 때 고려해야 할 중요한 질문을 제시하고 AEM에서의 SPA 배포와 관련된 AEM의 아키텍처에 대한 개요를 제공합니다.

## AEM용 SPA 개발 원칙 {#spa-development-principles-for-aem}

AEM을 통해 단일 페이지 애플리케이션을 개발하면 프론트엔드 개발자가 SPA를 제작하는 도중 표준 모범 사례를 준수하는 것으로 간주됩니다. 프론트엔드 개발자가 이러한 일반적인 모범 사례와 몇 가지 AEM 관련 원칙을 따르는 경우 SPA은 [AEM 및 컨텐츠 작성 기능](introduction.md#content-editing-experience-with-spa).

* **[이동성](#portability)** - 모든 구성 요소와 마찬가지로 구성 요소는 최대한 이동할 수 있도록 빌드해야 합니다. SPA는 이동 및 재사용할 수 있는 구성 요소로 빌드해야 합니다.
* **[AEM 실행 사이트 구조](#aem-drives-site-structure)** - 프론트엔드 개발자는 구성 요소를 만들고 내부 구조를 가지고 있지만 AEM을 사용하여 사이트의 콘텐츠 구조를 정의할 수 있습니다.
* **[동적 렌더링](#dynamic-rendering)** - 모든 렌더링은 동적이어야 합니다.
* **[동적 라우팅](#dynamic-routing)** - SPA는 라우팅을 담당하고 이에 따라 AEM은 라우팅을 수신하고 가져옵니다. 모든 라우팅 또한 동적이어야 합니다.

SPA을 개발할 때 이러한 원칙을 염두에 두면 지원되는 모든 AEM 작성 기능을 활성화하면서 가능한 한 유연하고 향후 증명이 됩니다.

AEM 작성 기능을 지원하지 않아도 되는 경우에는 다른 사항을 고려해야 할 수도 있습니다 [SPA 디자인 모델](#spa-design-models).

### 이동성 {#portability}

구성 요소를 개발할 때와 마찬가지로 구성 요소는 휴대성을 극대화하는 방식으로 설계해야 합니다. 향후 호환성, 유연성 및 유지 관리를 위해 구성 요소의 이동성 또는 재사용 가능성에 대해 작동하는 모든 패턴을 피해야 합니다.

결과 SPA은 휴대성이 높고 재사용 가능한 구성 요소로 빌드해야 합니다.

### AEM 드라이브 사이트 구조 {#aem-drives-site-structure}

프론트엔드 개발자는 앱을 빌드하는 데 사용되는 SPA 구성 요소 라이브러리를 만들어야 합니다. 프론트엔드 개발자는 구성 요소의 내부 구조를 완벽하게 제어합니다. [그러나 AEM은 항상 사이트의 구조를 소유합니다.](editor-overview.md)

즉, 프론트엔드 개발자는 구성 요소의 진입점 앞이나 뒤에 고객 콘텐츠를 추가할 수 있고, 구성 요소 내에서 서드파티 호출을 수행할 수도 있습니다. 그러나 프론트엔드 개발자는 예를 들어 구성 요소가 중첩할 수 있는 방법을 완벽하게 제어하지 못합니다.

### 동적 렌더링 {#dynamic-rendering}

SPA은 컨텐츠의 동적 렌더링에만 의존해야 합니다. AEM이 콘텐츠 구조의 모든 하위 항목을 가져와서 렌더링하는 기본 예상입니다.

특정 콘텐츠를 가리키는 명시적 렌더링은 정적 렌더링으로 간주되며 지원되지만 AEM 콘텐츠 작성 기능과 호환되지 않습니다. 이것은 또한 의 원칙에 위배된다 [이식성](#portability).

### 동적 라우팅 {#dynamic-routing}

렌더링과 마찬가지로 모든 라우팅도 동적이어야 합니다. AEM에서 [SPA은 항상 라우팅을 소유해야 합니다.](routing.md) 그리고 AEM은 이를 수신하고 이를 기반으로 콘텐츠를 가져옵니다.

모든 정적 라우팅은 [휴대성의 원리](#portability) 및 은 AEM의 콘텐츠 작성 기능과 호환되지 않도록 작성자를 제한합니다. 예를 들어, 정적 라우팅의 경우, 콘텐츠 작성자가 경로를 변경하거나 페이지를 변경하려면 프론트엔드 개발자에게 요청해야 합니다.

## AEM Project Archetype {#aem-project-archetype}

모든 AEM 프로젝트는 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=ko-KR)React 또는 Angular을 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 사용하는 입니다.

## SPA 디자인 모델 {#spa-design-models}

다음과 같은 경우 [AEM에서 SPA 개발의 원칙](#spa-development-principles-for-aem) 그러면 SPA이 지원되는 모든 AEM 콘텐츠 작성 기능을 사용할 수 있습니다.

그러나 완전히 필요하지 않은 경우도 있을 수 있습니다. 다음 표는 다양한 디자인 모델의 개요와 장점 및 단점을 제공합니다.

<table>
 <tbody>
  <tr>
   <th><strong>디자인 모델<br /> </strong></th>
   <th><strong>장점</strong></th>
   <th><strong>단점</strong></th>
  </tr>
  <tr>
   <td>AEM은 를 사용하지 않고 Headless CMS로 사용됩니다. <a href="/help/implementing/developing/hybrid/reference-materials.md">SPA Editor SDK 프레임워크.</a></td>
   <td>프론트엔드 개발자가 앱을 완벽하게 제어합니다.</td>
   <td><p>콘텐츠 작성자는 AEM 콘텐츠 작성 환경을 사용할 수 없습니다.</p> <p>정적 참조 또는 라우팅이 포함된 코드는 이식 가능하거나 재사용할 수 없습니다.</p> <p>템플릿 편집기의 사용을 허용하지 않으므로 프론트엔드 개발자는 JCR을 통해 편집 가능한 템플릿을 유지 관리해야 합니다.</p> </td>
  </tr>
  <tr>
   <td>프론트엔드 개발자는 SPA Editor SDK 프레임워크를 사용하지만 콘텐츠 작성자에게 일부 영역만 엽니다.</td>
   <td>개발자는 제한된 앱 영역에서만 작성을 활성화하여 앱을 계속 제어합니다.</td>
   <td><p>콘텐츠 작성자는 제한된 AEM 콘텐츠 작성 경험 세트로 제한됩니다.</p> <p>이 코드에 정적 참조 또는 라우팅이 포함되어 있으면 코드를 이동할 수 없거나 다시 사용할 수 없습니다.</p> <p>템플릿 편집기의 사용을 허용하지 않으므로 프론트엔드 개발자는 JCR을 통해 편집 가능한 템플릿을 유지 관리해야 합니다.</p> </td>
  </tr>
  <tr>
   <td>프로젝트는 SPA Editor SDK를 완전히 사용하며 프론트엔드 구성 요소는 라이브러리로 개발되고 앱의 콘텐츠 구조는 AEM에 위임됩니다.</td>
   <td><p>이 앱은 재사용이 가능하며 휴대가 가능합니다.</p> <p>콘텐츠 작성자는 AEM 콘텐츠 작성 경험을 사용하여 앱을 편집할 수 있습니다.<br /> </p> <p>SPA은 템플릿 편집기와 호환됩니다.</p> </td>
   <td><p>개발자가 앱의 구조 및 AEM에 위임된 콘텐츠 부분을 제어할 수 없습니다.</p> <p>개발자는 AEM을 사용하여 작성되지 않은 콘텐츠에 대해 앱 영역을 계속 예약할 수 있습니다.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>모든 모델은 AEM에서 지원되지만 세 번째 모델을 구현(및 권장 사항에 따라 구현)해야만 합니다 [AEM의 SPA 개발 원칙](#spa-development-principles-for-aem)) 콘텐츠 작성자는 SPA의 콘텐츠가 익숙해질 때 AEM에서 이 콘텐츠와 상호 작용하고 편집할 수 있게 됩니다.

## 기존 SPA에서 AEM으로 마이그레이션 {#migrating-existing-spas-to-aem}

일반적으로 SPA이 [AEM용 SPA 개발 원칙](#spa-development-principles-for-aem)를 클릭하면 SPA이 AEM에서 작동하며 AEM SPA 편집기를 사용하여 편집할 수 있습니다.

다음 단계에 따라 기존 SPA을 AEM에서 사용할 수 있도록 준비하십시오.

1. **JS 구성 요소를 모듈식으로 만듭니다.** - 모든 순서, 위치 및 크기로 렌더링할 수 있도록 합니다.
1. **SDK에서 제공하는 컨테이너를 사용하여 구성 요소를 화면에 배치합니다.** - AEM은 사용할 페이지 및 단락 시스템 구성 요소를 제공합니다.
1. **각 JS 구성 요소에 대한 AEM 구성 요소를 만듭니다.** - AEM 구성 요소는 대화 상자와 JSON 출력을 정의합니다.

## 프론트엔드 개발자를 위한 지침 {#instructions-for-front-end-developers}

프론트엔드 개발자가 AEM용 SPA을 만들도록 유도하는 주요 작업은 구성 요소 및 JSON 모델에 동의하는 것입니다.

다음은 SPA for AEM을 개발할 때 프론트엔드 개발자가 따라야 할 단계에 대한 개요입니다.

1. **구성 요소 및 JSON 모델에 동의**

   프론트엔드 개발자와 백엔드 AEM 개발자는 필요한 구성 요소와 모델에 대해 동의해야 SPA 구성 요소에서 백엔드 구성 요소로의 일대일 매칭이 가능합니다.

   AEM 구성 요소는 여전히 대부분 편집 대화 상자를 제공하고 구성 요소 모델을 내보내는 데 필요합니다.

1. **React 구성 요소에서 를 통해 모델에 액세스합니다.`this.props.cqModel`**

   구성 요소가 동의되고 JSON 모델이 준비되면 프론트엔드 개발자는 SPA을 무료로 개발할 수 있으며 를 통해 JSON 모델에 간단히 액세스할 수 있습니다. `this.props.cqModel`.

1. **구성 요소 구현 `render()` 방법**

   프론트엔드 개발자는 `render()` 메서드를 사용하여 조건에 맞는 `cqModel` 속성. 이렇게 하면 페이지에 삽입된 DOM과 HTML 조각이 출력됩니다. React에서 앱을 빌드하는 표준 방법입니다.

1. **다음을 통해 구성 요소를 AEM 리소스 유형에 매핑`MapTo()`**

   매핑은 구성 요소 클래스를 저장하고 제공된 이 내부적으로 사용합니다 `Container` 지정된 리소스 유형에 따라 구성 요소를 검색하고 동적으로 인스턴스화할 구성 요소입니다.

   이는 프론트엔드와 백엔드 사이의 &quot;접착제&quot; 역할을 하므로 편집기는 반응 구성 요소가 해당하는 구성 요소를 알 수 있습니다.

   다음 `Page` 및 `ResponsiveGrid` 기본 클래스를 확장하는 좋은 예입니다. `Container`.

1. **구성 요소 정의 `EditConfig` 에 매개 변수로`MapTo()`**

   이 매개 변수는 가 아직 렌더링되지 않았거나 렌더링할 콘텐츠가 없는 한 구성 요소의 이름을 어떻게 지정해야 하는지를 편집기에 알려 주는 데 필요합니다.

1. **제공된 을 확장합니다. `Container` 페이지 및 컨테이너 클래스**

   페이지 및 단락 시스템은 내부 구성 요소에 대한 위임이 예상대로 작동하도록 이 클래스를 확장해야 합니다.

1. **HTML5를 사용하는 라우팅 솔루션 구현 `History` API.**

   다음의 경우 `ModelRouter` 이(가) 활성화됨, 호출 `pushState` 및 `replaceState` 함수는 `PageModelManager` 모델의 누락된 조각을 가져올 수 있습니다.

   의 현재 버전 `ModelRouter` 슬링 모델 진입점의 실제 리소스 경로를 가리키는 URL만 사용할 수 있습니다. vanity URL 또는 별칭의 사용을 지원하지 않습니다.

   다음 `ModelRouter` 를 비활성화하거나 정규 표현식 목록을 무시하도록 구성할 수 있습니다.

## AEM-Agnostic {#aem-agnostic}

이러한 코드 블록은 React 및 Angular 구성 요소에 Adobe 또는 AEM에만 해당하는 항목이 필요하지 않은 방법을 보여 줍니다.

* JavaScript 구성 요소 내에 있는 모든 것은 AEM과 관계없습니다.
* 그러나 AEM에 고유한 것은 JS 구성 요소를 MapTo 도우미와 함께 AEM 구성 요소에 매핑해야 한다는 것입니다.

![AEM 불가지론적 접근 방식](assets/aem-agnostic.png)

다음 `MapTo` helper는 백엔드 및 프론트엔드 구성 요소를 함께 찾을 수 있는 &quot;접착제&quot;입니다.

* JS 컨테이너 (또는 JS 단락 시스템)에 JSON에 있는 각 구성 요소를 렌더링하기 위해 JS 구성 요소가 무엇인지를 알려줍니다.
* JS 구성 요소가 렌더링하는 HTML에 HTML 데이터 속성을 추가하므로 SPA 편집기는 구성 요소를 편집할 때 작성자에게 표시할 대화 상자를 알 수 있습니다.

사용에 대한 자세한 내용 `MapTo` SPA for AEM을 일반적으로 빌드하려면 선택한 프레임워크에 대한 시작 안내서를 참조하십시오.

* [React를 사용하여 AEM에서 SPA 시작하기](getting-started-react.md)
* [Angular를 사용하여 AEM에서 SPA 시작하기](getting-started-angular.md)

## AEM 아키텍처 및 SPA {#aem-architecture-and-spas}

개발, 작성 및 게시 환경을 포함한 AEM의 일반 아키텍처는 SPA을 사용할 때 변경되지 않습니다. 그러나 SPA 개발이 이 아키텍처에 어떻게 적합한지 이해하는 것이 유용합니다.

![AEM 아키텍처 및 SPA](assets/aem-architecture.png)

* **빌드 환경**

  SPA 애플리케이션 소스 및 구성 요소 소스의 소스가 체크아웃되는 위치입니다.

   * NPM clientlib 생성기는 SPA 프로젝트에서 클라이언트 라이브러리를 생성합니다.
   * 해당 라이브러리는 Maven에서 가져오고 구성 요소와 함께 Maven Build 플러그인에 의해 AEM 작성자에게 배포됩니다.

* **AEM Author**

  SPA 작성을 포함하여 AEM 작성자에 콘텐츠가 작성됩니다.

  작성 환경에서 SPA 편집기를 사용하여 SPA을 편집하는 경우:

   1. SPA이 외부 HTML을 요청합니다.
   1. CSS가 로드되었습니다.
   1. SPA 애플리케이션의 Javascript가 로드되었습니다.
   1. SPA 애플리케이션이 실행되면 JSON이 요청되어 앱이 다음을 포함한 페이지의 DOM을 빌드할 수 있습니다. `cq-data` 속성.
   1. 이 `cq-data` 속성을 사용하면 편집기에서 구성 요소에 사용할 수 있는 편집 구성이 무엇인지 알 수 있도록 추가 페이지 정보를 로드할 수 있습니다.

* **AEM 게시**

  여기에서 SPA 애플리케이션 아티팩트, clientlib 및 구성 요소를 비롯한 작성된 컨텐츠 및 컴파일된 라이브러리가 공용으로 게시됩니다.

* **Dispatcher / CDN**

  Dispatcher는 사이트 방문자를 위한 AEM의 캐싱 레이어 역할을 합니다.
   * 요청은 AEM 작성자에 있는 것과 유사하게 처리되지만 편집기에만 필요하므로 페이지 정보에 대한 요청은 없습니다.
   * Javascript, CSS, JSON 및 HTML이 캐시되어 빠른 전송을 위해 페이지가 최적화됩니다.

>[!NOTE]
>
>AEM 내에서는 Javascript 빌드 메커니즘을 실행하거나 Javascript 자체를 실행할 필요가 없습니다. AEM은 SPA 애플리케이션에서 컴파일된 아티팩트만 호스팅합니다.

## 다음 단계 {#next-steps}

* [React를 사용하여 AEM에서 SPA 시작하기](getting-started-react.md) React를 통해 AEM에서 기본 SPA를 빌드하여 SPA 편집기에서 작업하는 방법을 표시함.
* [Angular를 사용하여 AEM에서 SPA 시작하기](getting-started-angular.md) Angular를 통해 AEM에서 기본 SPA를 빌드하여 SPA 편집기에서 작업하는 방법을 표시함.
* [SPA 편집기 개요](editor-overview.md)는 AEM과 SPA 간의 커뮤니케이션 모델에 대해 자세히 설명합니다.
* [WKND SPA 프로젝트](wknd-tutorial.md) 는 AEM에서 간단한 SPA 프로젝트를 구현하는 단계별 자습서입니다.
* [SPA용 동적 모델과 구성 요소 간 매핑](model-to-component-mapping.md) 구성 요소 매핑에 대한 동적 모델과 AEM의 SPA 내에서 작동하는 방식에 대해 설명합니다.
* [SPA 블루프린트](blueprint.md) 는 React 또는 Angular 이외의 프레임워크에 대해 AEM에서 SPA을 구현하거나 더 깊이 이해하고 싶은 경우 AEM용 SPA SDK의 작동 방식에 대해 자세히 알아봅니다.
