---
title: AEM용 SPA 개발
description: 이 문서에서는 프런트 엔드 개발자에게 AEM for AEM을 개발하도록 권유할 때 고려해야 할 중요한 질문을 제시하며, SPA에 개발한 SPA을 배포할 때 염두에 둘 수 있도록 SPA과 관련된 AEM 아키텍처에 대한 개요를 제공합니다.
exl-id: f6c6f31a-69ad-48f6-b995-e6d0930074df
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '2076'
ht-degree: 1%

---

# AEM용 SPA 개발 {#developing-spas-for-aem}

SPA(단일 페이지 애플리케이션)는 웹 사이트 사용자에게 훌륭한 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크을 사용하여 사이트를 작성하려고 하며 작성자는 이러한 프레임워크를 사용하여 작성된 사이트의 AEM 내에서 컨텐츠를 원활하게 편집하려고 합니다.

이 문서에서는 프런트엔드 개발자에게 AEM for SPA을 개발하도록 권유할 때 고려해야 할 중요한 질문을 제시하며 AEM에서 SPA 배포과 관련된 AEM 아키텍처에 대한 개요를 제공합니다.

## AEM {#spa-development-principles-for-aem}에 대한 SPA 개발 원칙

AEM에서 단일 페이지 애플리케이션을 개발하는 경우 프런트 엔드 개발자는 SPA을 만들 때 표준 우수 사례를 관찰한다고 가정합니다. 프런트 엔드 개발자로서 이러한 일반 모범 사례와 몇 가지 AEM 관련 원칙을 따르는 경우 SPA은 [AEM 및 해당 컨텐츠 작성 기능](introduction.md#content-editing-experience-with-spa)에서 사용할 수 있습니다.

* **[휴대성](#portability)**  - 모든 구성 요소와 마찬가지로 구성 요소를 최대한 휴대할 수 있도록 제작해야 합니다. SPA은 휴대용 및 재사용 가능한 구성 요소로 구축되어야 합니다.
* **[AEM 드라이브 사이트 구조](#aem-drives-site-structure)**  - 프런트 엔드 개발자는 구성 요소를 만들고 내부 구조를 소유하지만, AEM을 사용하여 사이트의 컨텐츠 구조를 정의합니다.
* **[동적 렌더링](#dynamic-rendering)**  - 모든 렌더링은 동적이여야 합니다.
* **[동적 라우팅](#dynamic-routing)**  - SPA은 공정순서를 담당하고 AEM은 공정순서를 수신하여 그에 따라 가져옵니다. 모든 라우팅도 동적이여야 합니다.

SPA을 개발할 때 이러한 원칙을 염두에 두는 경우 지원되는 모든 AEM 작성 기능을 활성화하면서 가능한 한 유연하고 향후 증거입니다.

AEM 작성 기능을 지원하지 않아도 되는 경우 다른 [SPA 디자인 모델](#spa-design-models)을 고려해야 할 수 있습니다.

### 휴대성 {#portability}

구성 요소를 개발할 때와 같이 구성 요소는 휴대성을 극대화하도록 설계되어야 합니다. 구성 요소의 휴대성 또는 재사용성에 역행하는 모든 패턴은 향후 호환성, 유연성 및 유지 관리 기능을 보장하기 위해 피해야 합니다.

결과 SPA은 휴대성과 재사용 가능한 구성 요소로 구축되어야 합니다.

### AEM 드라이브 사이트 구조 {#aem-drives-site-structure}

프런트 엔드 개발자는 자신을 앱을 빌드하는 데 사용되는 SPA 구성 요소 라이브러리를 만들 책임이 있다고 생각해야 합니다. 프런트엔드 개발자는 구성 요소의 내부 구조를 완벽하게 제어할 수 있습니다. [하지만 항상 AEM이 사이트의 구조를 소유합니다.](editor-overview.md)

즉, 프런트엔드 개발자는 구성 요소의 시작 지점 전이나 후에 고객 컨텐츠를 추가할 수 있고, 구성 요소 내에서 타사 호출을 수행할 수도 있습니다. 그러나 프런트 엔드 개발자는 예를 들어 구성 요소가 중첩되는 방식을 완전히 제어하지 않습니다.

### 동적 렌더링 {#dynamic-rendering}

SPA은 컨텐츠의 동적 렌더링만 사용해야 합니다. 이는 AEM이 컨텐츠 구조의 모든 하위 항목을 가져오고 렌더링하는 기본 예측입니다.

특정 컨텐츠를 가리키는 명시적 렌더링은 정적 렌더링으로 간주되지만 지원되는 것은 AEM 컨텐츠 작성 기능과 호환되지 않습니다. 이는 [이식성](#portability)의 원칙과도 어긋납니다.

### 동적 라우팅 {#dynamic-routing}

렌더링과 마찬가지로 모든 라우팅도 동적이여야 합니다. AEM에서 [SPA은 항상 라우팅](routing.md)을 소유해야 하며 AEM이 이 라우트를 수신하고 이를 기반으로 컨텐츠를 가져옵니다.

모든 정적 라우팅은 [휴대성](#portability)의 원칙에 따라 작동하며 AEM의 컨텐츠 작성 기능과 호환되지 않아 작성자를 제한합니다. 예를 들어 정적 라우팅을 사용하여 컨텐츠 작성자가 경로를 변경하거나 페이지를 변경하려면 프런트 엔드 개발자에게 경로 지정을 요청해야 합니다.

## AEM 프로젝트 전형 {#aem-project-archetype}

모든 AEM 프로젝트는 React 또는 Angular을 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)을 활용해야 합니다.

## SPA 디자인 모델 {#spa-design-models}

AEM](#spa-development-principles-for-aem)에서 SPA을 개발하는 [의 원칙을 따를 경우 SPA은 지원되는 모든 AEM 컨텐츠 작성 기능과 함께 작동합니다.

그러나 이것이 완전히 필요하지 않은 경우도 있을 수 있습니다. 다음 표에서는 다양한 디자인 모델, 그 이점 및 그 단점에 대해 간략하게 설명합니다.

<table>
 <tbody>
  <tr>
   <th><strong>디자인 모델<br /> </strong></th>
   <th><strong>장점</strong></th>
   <th><strong>단점</strong></th>
  </tr>
  <tr>
   <td>AEM은 <a href="/help/implementing/developing/hybrid/reference-materials.md">SPA Editor SDK 프레임워크를 사용하지 않고 헤드리스 CMS로 사용됩니다.</a></td>
   <td>프런트 엔드 개발자는 앱을 완벽하게 제어할 수 있습니다.</td>
   <td><p>컨텐츠 작성자는 AEM 컨텐츠 작성 환경을 활용할 수 없습니다.</p> <p>이 코드가 정적 참조나 라우팅이 포함된 경우 휴대형 또는 재사용할 수 없습니다.</p> <p>템플릿 편집기를 사용할 수 없으므로 프런트 엔드 개발자는 JCR을 통해 편집 가능한 템플릿을 유지 관리해야 합니다.</p> </td>
  </tr>
  <tr>
   <td>프런트 엔드 개발자는 SPA Editor SDK 프레임워크를 사용하지만 컨텐츠 작성자에게 일부 영역만 엽니다.</td>
   <td>개발자는 앱의 제한된 영역에서만 작성을 활성화하여 앱을 제어합니다.</td>
   <td><p>컨텐츠 작성자는 제한된 AEM 컨텐츠 작성 환경으로 제한됩니다.</p> <p>코드가 정적 참조나 라우팅이 포함되어 있는 경우 휴대가 불가능하거나 다시 사용할 수 없을 수 있습니다.</p> <p>템플릿 편집기를 사용할 수 없으므로 프런트 엔드 개발자는 JCR을 통해 편집 가능한 템플릿을 유지 관리해야 합니다.</p> </td>
  </tr>
  <tr>
   <td>이 프로젝트는 SPA Editor SDK를 완전히 활용하고 프런트 엔드 구성 요소는 라이브러리로 개발되며, 앱의 컨텐츠 구조가 AEM에 위임됩니다.</td>
   <td><p>이 앱은 재사용이 가능하고 휴대할 수 있습니다.</p> <p>컨텐츠 작성자는 AEM 컨텐츠 작성 환경을 사용하여 앱을 편집할 수 있습니다.<br /> </p> <p>SPA은 템플릿 편집기와 호환됩니다.</p> </td>
   <td><p>개발자는 앱의 구조 및 AEM에 위임된 컨텐츠 부분을 제어하지 않습니다.</p> <p>개발자는 AEM을 사용하여 작성되지 않도록 되어 있는 컨텐츠에 대해 앱의 영역을 계속 예약할 수 있습니다.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>모든 모델은 AEM에서 지원되지만, 세 번째(및 이에 따라 AEM](#spa-development-principles-for-aem)에서 권장되는 [SPA 개발 원칙을 따르는 경우에만 컨텐츠 작성자는 익숙해진 대로 AEM에서 SPA의 컨텐츠와 상호 작용하고 편집할 수 있습니다.

## 기존 SPA을 AEM {#migrating-existing-spas-to-aem}으로 마이그레이션

일반적으로 SPA이 AEM](#spa-development-principles-for-aem)SPA 개발 원칙을 따르는 경우, SPA은 AEM에서 작동하며 AEM SPA 편집기를 사용하여 편집할 수 있습니다.[

다음 단계에 따라 기존 SPA에서 AEM을 사용할 수 있습니다.

1. **JS 구성 요소를 모듈식으로 만듭니다.** - 원하는 순서, 위치 및 크기로 렌더링할 수 있도록 합니다.
1. **SDK에서 제공하는 컨테이너를 사용하여 구성 요소를 화면에 표시합니다.** - AEM에서는 사용할 페이지 및 단락 시스템 구성 요소를 제공합니다.
1. **각 JS 구성 요소에 대해 AEM 구성 요소를 만듭니다.** - AEM 구성 요소는 대화 상자 및 JSON 출력을 정의합니다.

## 프런트 엔드 개발자를 위한 지침 {#instructions-for-front-end-developers}

프런트엔드 개발자에게 AEM용 SPA을 만드는 데 필요한 주요 작업은 구성 요소 및 JSON 모델에 동의하는 것입니다.

다음은 SPA for AEM을 개발할 때 프런트 엔드 개발자가 따라야 하는 단계에 대한 개요입니다.

1. **구성 요소 및 해당 JSON 모델에 대해 동의합니다**

   프런트엔드 개발자와 백엔드 AEM 개발자는 필요한 구성 요소 및 모델에 동의해야 SPA 구성 요소에서 백엔드 구성 요소로의 일대일 비교가 가능합니다.

   AEM 구성 요소는 편집 대화 상자를 제공하고 구성 요소 모델을 내보내는 데 주로 필요합니다.

1. **React 구성 요소에서`this.props.cqModel`**

   구성 요소가 동의하고 JSON 모델이 배치되면 프런트 엔드 개발자는 SPA을 개발할 수 있으며 `this.props.cqModel` 을 통해 JSON 모델에 간편하게 액세스할 수 있습니다.

1. **구성 요소의  `render()` 메서드 구현**

   프런트 엔드 개발자는 `render()` 메서드를 적절히 구현하고 `cqModel` 속성의 필드를 사용할 수 있습니다. 이렇게 하면 페이지에 삽입할 DOM 및 HTML 조각이 출력됩니다. React에서 앱을 빌드하는 표준 방법입니다.

1. **을 통해 구성 요소를 AEM 리소스 유형에 매핑합니다`MapTo()`**

   매핑은 구성 요소 클래스를 저장하고 제공된 `Container` 구성 요소에서 내부적으로 사용하여 주어진 리소스 유형에 따라 구성 요소를 검색하고 동적으로 인스턴스화합니다.

   이 기능은 프런트 엔드와 백 엔드 간에 &quot;풀&quot; 역할을 하므로 편집기에서 React 구성 요소가 해당하는 구성 요소를 파악할 수 있습니다.

   `Page` 및 `ResponsiveGrid` 는 기본 `Container`을 확장하는 클래스의 좋은 예입니다.

1. **구성 요소의 매개 변수 `EditConfig` 를 (으)로 정의합니다`MapTo()`**

   이 매개 변수는 이 아직 렌더링되지 않았거나 렌더링할 콘텐츠가 없는 경우 구성 요소의 이름을 지정하는 방법을 편집기에 알려야 합니다.

1. **페이지 및 컨테이너 `Container` 에 대해 제공된 클래스를 확장합니다.**

   페이지 및 단락 시스템은 내부 구성 요소에 위임이 예상대로 작동되도록 이 클래스를 확장해야 합니다.

1. **HTML5  `History` API를 사용하는 라우팅 솔루션을 구현합니다.**

   `ModelRouter`이 활성화되어 있으면 `pushState` 및 `replaceState` 함수를 호출하면 `PageModelManager`에 대한 요청을 트리거하여 누락된 모델 조각을 가져옵니다.

   현재 버전의 `ModelRouter`은(는) Sling 모델 시작 지점의 실제 리소스 경로를 가리키는 URL의 사용만 지원합니다. 별칭 URL 또는 별칭 사용을 지원하지 않습니다.

   정규 표현식 목록을 무시하도록 `ModelRouter` 을 비활성화하거나 구성할 수 있습니다.

## AEM-Agnostic {#aem-agnostic}

이러한 코드 블록은 React 및 Angular 구성 요소에 Adobe 또는 AEM에만 해당하는 것이 필요하지 않음을 보여줍니다.

* JavaScript 구성 요소 내에 있는 모든 것은 AEM에 관계 없습니다.
* 그러나 AEM에만 해당하는 것은 JS 구성 요소를 MapTo 도우미가 있는 AEM 구성 요소에 매핑해야 한다는 것입니다.

![AEM 불가지식 접근 방식](assets/aem-agnostic.png)

`MapTo` 도우미는 백 엔드와 프런트 엔드 구성 요소를 함께 일치시킬 수 있는 &quot;풀&quot;입니다.

* JSON에 있는 각 구성 요소 렌더링을 위해 JS 컨테이너(또는 JS 단락 시스템)에 어떤 JS 구성 요소가 담당하는지 알려줍니다.
* JS 구성 요소가 렌더링하는 HTML에 HTML 데이터 속성을 추가하므로 SPA 편집기는 구성 요소를 편집할 때 작성자에게 표시할 대화 상자를 알 수 있습니다.

일반적으로 `MapTo` 사용 및 SPA for AEM 작성에 대한 자세한 내용은 선택한 프레임워크에 대한 시작 안내서를 참조하십시오.

* [React를 사용하여 AEM에서 SPA 시작하기](getting-started-react.md)
* [angular을 사용하여 AEM에서 SPA 시작하기](getting-started-angular.md)

## AEM 아키텍처 및 SPA {#aem-architecture-and-spas}

SPA 사용 시 개발, 작성 및 게시 환경을 포함한 AEM의 일반 아키텍처는 변경되지 않습니다. 하지만 SPA 개발이 이 아키텍처에 어떻게 적합한지 이해하는 데 도움이 됩니다.

![AEM 아키텍처 및 SPA](assets/aem-architecture.png)

* **빌드 환경**

   여기서 SPA 애플리케이션 소스 및 구성 요소 소스의 소스가 체크 아웃됩니다.

   * NPM clientlib 생성기가 SPA 프로젝트에서 클라이언트 라이브러리를 만듭니다.
   * 해당 라이브러리는 Maven에서 가져온 후 AEM 작성자에 대한 구성 요소와 함께 Maven Build 플러그인에 의해 배포됩니다.

* **AEM Author**

   컨텐츠는 SPA 작성을 포함하여 AEM 작성자에 의해 만들어집니다.

   작성 환경에서 SPA 편집기를 사용하여 SPA을 편집하는 경우:

   1. SPA이 외부 HTML을 요청합니다.
   1. CSS가 로드됩니다.
   1. SPA 애플리케이션의 Javascript가 로드됩니다.
   1. SPA 애플리케이션이 실행되면 JSON이 요청되어 앱이 `cq-data` 속성을 포함하는 페이지의 DOM을 작성할 수 있습니다.
   1. 이 `cq-data` 속성을 사용하면 편집기에서 구성 요소에 사용할 수 있는 편집 구성을 알 수 있도록 추가 페이지 정보를 로드할 수 있습니다.

* **AEM 게시**

   여기서 SPA 애플리케이션 객체, clientlibs 및 구성 요소를 포함한 작성된 컨텐츠 및 컴파일된 라이브러리가 공개 소비에 대해 게시됩니다.

* **Dispatcher/CDN**

   디스패처는 사이트 방문자를 위한 AEM의 캐싱 레이어 역할을 합니다.
   * 요청은 AEM 작성자에 있는 방식과 유사하게 처리되지만 편집기에만 필요하므로 페이지 정보에 대한 요청이 없습니다.
   * Javascript, CSS, JSON 및 HTML이 캐시되므로 빠른 배달을 위해 페이지가 최적화됩니다.

>[!NOTE]
>
>AEM 내부에서는 Javascript 빌드 메커니즘을 실행하거나 Javascript 자체를 실행할 필요가 없습니다. AEM은 SPA 애플리케이션에서 컴파일된 객체만 호스팅합니다.

## 다음 단계 {#next-steps}

* [React를 사용하여 AEM에서 SPA](getting-started-react.md) 로 시작하기 는 React를 사용하여 AEM에서 SPA Editor와 작동하도록 기본 SPA을 빌드하는 방법을 보여줍니다.
* [Angular를 사용하여 AEM](getting-started-angular.md) 에서 SPA 시작하기 은 Angular을 사용하여 AEM에서 SPA 편집기로 작동하기 위해 기본 SPA을 어떻게 빌드하는지 보여줍니다.
* [SPA ](editor-overview.md) 편집기 개요는 AEM과 SPA 간의 통신 모델에 대해 자세히 설명합니다.
* [WKND SPA ](wknd-tutorial.md) Projectials는 AEM에서 간단한 SPA 프로젝트를 구현하는 단계별 자습서입니다.
* [SPA에 대한 동적 모델과 구성 ](model-to-component-mapping.md) 요소 간 매핑이 AEM에서 SPA 내에서 작동하는 방식에 대해 설명합니다.
* [SPA ](blueprint.md) Blueprint는 React 또는 Angular 이외의 프레임워크를 위해 AEM에서 SPA을 구현하거나 단순히 더 깊이 이해하고 싶은 경우 AEM용 SPA SDK가 작동하는 방식을 자세히 살펴봅니다.
