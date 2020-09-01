---
title: AEM용 SPA 개발
description: 이 문서에서는 프런트 엔드 개발자에게 AEM용 SPA를 개발하도록 권유하는 경우 고려해야 할 중요한 사항을 소개하고 있을 뿐만 아니라 AEM에 개발한 SPA를 배포할 때 염두에 두어야 할 SPA와 관련된 AEM 아키텍처에 대한 개요를 제공합니다.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '2078'
ht-degree: 1%

---


# AEM용 SPA 개발 {#developing-spas-for-aem}

단일 페이지 애플리케이션(SPA)을 통해 웹 사이트 사용자에게 매력적인 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크를 사용하여 사이트를 구축할 수 있어야 하며, 작성자는 이러한 프레임워크를 사용하여 구축한 사이트에 AEM의 컨텐츠를 완벽하게 편집하고자 합니다.

이 문서에서는 프런트 엔드 개발자에게 AEM용 SPA를 개발할 때 고려해야 할 중요한 질문을 제시하며 AEM에 SPA를 배포하는 것과 관련하여 AEM의 아키텍처에 대해 간략하게 설명합니다.

## AEM을 위한 SPA 개발 원칙 {#spa-development-principles-for-aem}

AEM에서 단일 페이지 애플리케이션을 개발하는 경우 프런트 엔드 개발자가 SPA를 만들 때 표준 모범 사례를 준수한다고 가정합니다. 프런트 엔드 개발자는 이러한 일반적인 모범 사례와 AEM별 원칙을 거의 따르지 않는 경우, SPA는 [AEM 및의 컨텐츠 제작 기능과 함께 사용할 수 있습니다](introduction.md#content-editing-experience-with-spa).

* **[휴대성](#portability)** - 모든 컴포넌트와 마찬가지로 가능한 한 휴대할 수 있도록 구축되어야 합니다. SPA는 안전하고 재사용 가능한 구성 요소로 구축되어야 합니다.
* **[AEM 드라이브 사이트 구조](#aem-drives-site-structure)** - 프런트 엔드 개발자는 구성 요소를 만들고 내부 구조를 소유하지만 AEM을 사용하여 사이트의 컨텐츠 구조를 정의합니다.
* **[동적 렌더링](#dynamic-rendering)** - 모든 렌더링이 동적입니다.
* **[동적 라우팅](#dynamic-routing)** - SPA는 라우팅을 담당하고 AEM은 이를 듣고 이에 따라 페치를 처리합니다. 모든 라우팅도 동적입니다.

SPA를 개발할 때 이러한 원칙을 염두에 두면 지원되는 모든 AEM 저작 기능을 활성화하면서 가능한 한 유연하고 향후 증거 자료로 활용할 수 있습니다.

AEM 저작 기능을 지원하지 않아도 다른 [SPA 디자인 모델을 고려해야 할 수도 있습니다](#spa-design-models).

### 이식성 {#portability}

구성 요소를 개발할 때처럼 구성 요소를 이식성을 최대화하는 방식으로 설계해야 합니다. 구성 요소의 이식성이나 재사용성에 반하는 모든 패턴은 향후 호환성, 유연성 및 유지 관리 가능성을 보장하려면 피해야 합니다.

그 결과 SPA는 이동이 쉽고 재사용 가능한 구성 요소로 구축되어야 한다.

### AEM 드라이브 사이트 구조 {#aem-drives-site-structure}

프런트 엔드 개발자는 앱을 빌드하는 데 사용되는 SPA 구성 요소 라이브러리를 만든 자신의 책임을 스스로 생각해야 합니다. 프런트 엔드 개발자는 구성 요소의 내부 구조를 완벽하게 제어할 수 있습니다. [그러나 AEM은 항상 사이트의 구조를 소유합니다.](editor-overview.md)

즉, 프런트 엔드 개발자는 구성 요소의 시작 지점 전후 고객 컨텐츠를 추가할 수 있으며 구성 요소 내에서 서드 파티 호출을 수행할 수도 있습니다. 하지만 프런트 엔드 개발자는 구성 요소가 중첩되는 방법을 완전히 제어하지는 않습니다.

### 동적 렌더링 {#dynamic-rendering}

SPA는 동적 컨텐츠 렌더링에만 의존해야 합니다. 이는 AEM이 컨텐츠 구조의 모든 하위 요소를 가져오고 렌더링하는 기본 예측입니다.

특정 컨텐츠를 가리키는 명시적 렌더링은 정적 렌더링으로 간주되며 지원되지만 AEM 컨텐츠 제작 기능과 호환되지 않습니다. 게다가 이식성의 원리에 [어긋난다](#portability).

### 동적 라우팅 {#dynamic-routing}

렌더링과 마찬가지로 모든 라우팅도 동적입니다. AEM [에서 SPA는 항상 라우팅을](routing.md) 소유해야 하며 AEM은 라우팅을 듣고 이를 바탕으로 컨텐츠를 전달해야 합니다.

모든 정적 라우팅은 이식성 [의 원칙에 어긋나고 AEM의 컨텐츠 저작 기능과 호환하지 않아 작성자를](#portability) 제한합니다. 예를 들어 정적 라우팅을 사용하여 컨텐츠 작성자가 경로를 변경하거나 페이지를 변경하려는 경우 프런트 엔드 개발자에게 요청해야 합니다.

## AEM 프로젝트 전형 {#aem-project-archetype}

모든 AEM 프로젝트는 [AEM 프로젝트 원형](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)(React or Angular)을 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 프로젝트 전형(Pretype)을 활용해야 합니다.

## SPA 디자인 모델 {#spa-design-models}

AEM [에서 SPA 개발 원칙을](#spa-development-principles-for-aem) 준수한다면 SPA에서 지원되는 모든 AEM 컨텐츠 제작 기능을 사용할 수 있습니다.

그러나 이것이 완전히 필요하지 않은 경우도 있을 수 있다. 다음 표는 다양한 디자인 모델, 그 장점 및 그 단점에 대한 개요를 제공합니다.

<table>
 <tbody>
  <tr>
   <th><strong>디자인 모델<br /> </strong></th>
   <th><strong>장점</strong></th>
   <th><strong>단점</strong></th>
  </tr>
  <tr>
   <td>AEM은 <a href="/help/implementing/developing/spa/reference-materials.md">SPA Editor SDK 프레임워크를 사용하지 않고도 헤드리스 CMS로 사용됩니다.</a></td>
   <td>프런트 엔드 개발자는 앱을 완벽하게 제어할 수 있습니다.</td>
   <td><p>컨텐츠 작성자는 AEM 컨텐츠 작성 경험을 활용할 수 없습니다.</p> <p>정적 참조나 라우팅이 포함된 코드에서는 이식성이 불가능하거나 다시 사용할 수 없습니다.</p> <p>템플릿 편집기를 사용할 수 없으므로 프런트 엔드 개발자가 JCR을 통해 편집 가능한 템플릿을 유지 관리해야 합니다.</p> </td>
  </tr>
  <tr>
   <td>프런트 엔드 개발자는 SPA Editor SDK 프레임워크를 사용하지만 컨텐츠 작성자에게 일부 영역만 엽니다.</td>
   <td>개발자는 앱의 제한된 영역에서만 저작을 활성화하여 앱을 계속 제어합니다.</td>
   <td><p>컨텐츠 작성자는 제한된 AEM 컨텐츠 작성 경험으로 제한됩니다.</p> <p>정적 참조나 라우팅을 포함하는 경우 코드를 이식하거나 다시 사용할 수 없을 때 위험이 있습니다.</p> <p>템플릿 편집기를 사용할 수 없으므로 프런트 엔드 개발자가 JCR을 통해 편집 가능한 템플릿을 유지 관리해야 합니다.</p> </td>
  </tr>
  <tr>
   <td>이 프로젝트는 SPA Editor SDK를 완벽하게 활용하며 프런트 엔드 구성 요소는 라이브러리로 개발되고 앱의 컨텐츠 구조가 AEM에 위임됩니다.</td>
   <td><p>이 앱은 재사용 및 이식성이 가능합니다.</p> <p>콘텐츠 제작자는 AEM 콘텐츠 제작 환경을 사용하여 앱을 편집할 수 있습니다.<br /> </p> <p>SPA는 템플릿 편집기와 호환됩니다.</p> </td>
   <td><p>개발자는 앱의 구조와 AEM에 위임된 콘텐츠 일부를 제어하지 않습니다.</p> <p>개발자는 AEM을 사용하여 제작할 목적이 아닌 콘텐츠에 대해 앱의 영역을 계속 예약할 수 있습니다.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>모든 모델이 AEM에서 지원되지만 컨텐츠 작성자는 세 번째(AEM의 권장 [SPA 개발 원칙](#spa-development-principles-for-aem))를 구현해야만 익숙하다면 AEM에서 SPA의 컨텐츠를 사용하고 편집할 수 있습니다.

## 기존 SPA를 AEM으로 마이그레이션 {#migrating-existing-spas-to-aem}

일반적으로 SPA가 AEM의 [SPA Development Principles를](#spa-development-principles-for-aem)준수하는 경우 SPA는 AEM에서 작동하며 AEM SPA Editor를 사용하여 편집할 수 있습니다.

다음 단계에 따라 기존 SPA를 AEM과 함께 사용할 수 있습니다.

1. **JS 구성 요소를 모듈식으로 만듭니다.** - 모든 순서, 위치 및 크기로 렌더링할 수 있도록 합니다.
1. **Adobe SDK에서 제공하는 컨테이너를 사용하여 구성 요소를 화면에 배치합니다.** - AEM에서는 사용할 수 있는 페이지 및 단락 시스템 구성 요소를 제공합니다.
1. **각 JS 구성 요소에 대해 AEM 구성 요소를 만듭니다.** - AEM 구성 요소는 대화 상자 및 JSON 출력을 정의합니다.

## 프런트 엔드 개발자를 위한 지침 {#instructions-for-front-end-developers}

AEM용 SPA를 만들기 위해 프런트 엔드 개발자에게 참여하는 주요 작업은 구성 요소와 JSON 모델에 동의해야 합니다.

다음은 AEM용 SPA를 개발할 때 프런트 엔드 개발자가 따라야 하는 단계에 대한 개요입니다.

1. **구성 요소 및 JSON 모델에 동의**

   프런트 엔드 개발자와 백엔드 AEM 개발자는 SPA 구성 요소에서 백엔드 구성 요소와 1:1 일치하기 때문에 어떤 구성 요소가 필요한지 모델 및 필수 구성 요소에 동의해야 합니다.

   AEM 구성 요소는 여전히 편집 대화 상자를 제공하고 구성 요소 모델을 내보내는 데 필요합니다.

1. **응답형 구성 요소에서`this.props.cqModel`**

   구성 요소가 동의되고 JSON 모델이 적용되면 프런트 엔드 개발자는 SPA를 무료로 개발하고 JSON 모델에 간편하게 액세스할 수 있습니다 `this.props.cqModel`.

1. **구성 요소의 메서드`render()`구현**

   프런트 엔드 개발자는 속성 필드를 사용할 수 있고, `render()` 맞출 수 있는 방법을 구현합니다 `cqModel` . 페이지에 삽입할 DOM 및 HTML 조각을 출력합니다. 이것은 React에서 앱을 빌드하는 표준 방법입니다.

1. **구성 요소를`MapTo()`**

   매핑은 구성 요소 클래스를 저장하고 제공된 구성 요소에서 내부적으로 사용하여 지정된 리소스 유형을 기준으로 구성 요소를 검색하고 동적으로 인스턴스화합니다. `Container`

   이 기능은 프런트 엔드와 백 엔드 간의 &quot;접착제&quot; 역할을 하므로 편집자는 반응형 구성 요소가 일치하는 구성 요소를 파악할 수 있습니다.

   그리고 `Page` 는 기본을 확장하는 강의 좋은 예이다 `ResponsiveGrid` `Container`.

1. **구성 요소의 매개 변수`EditConfig`를`MapTo()`**

   이 매개 변수는 렌더링되지 않거나 렌더링할 컨텐츠가 없는 한 구성 요소의 이름을 지정하는 방법을 편집자에게 알려 주어야 합니다.

1. **페이지 및 컨테이너에 대해 제공된`Container`클래스 확장**

   페이지 및 단락 시스템은 내부 구성 요소에 대한 위임이 예상대로 작동하도록 이 클래스를 확장해야 합니다.

1. **HTML5`History`API를 사용하는 라우팅 솔루션을 구현합니다.**

   이 `ModelRouter` 가 활성화되면 `pushState` 및 `replaceState` 함수를 호출하면 모델에 대한 요청 `PageModelManager` 이 트리거되어 누락된 조각 가져오기가 시작됩니다.

   현재 버전의 유일한 `ModelRouter` 는 Sling 모델 진입점의 실제 리소스 경로를 가리키는 URL의 사용을 지원합니다. 별칭 URL 또는 별칭 사용을 지원하지 않습니다.

   일반 표현식 목록을 무시하도록 `ModelRouter` 비활성화하거나 구성할 수 있습니다.

## AEM-Doalstic {#aem-agnostic}

이러한 코드 블록은 Adobe 또는 AEM에만 해당되는 반응 및 각도 구성 요소가 필요 없는 방식을 보여 줍니다.

* JavaScript 구성 요소 내에 있는 모든 것은 AEM에 관계없이 가능합니다.
* 그러나 AEM에서만 적용되는 것은 JS 구성 요소를 MapTo 도우미로 AEM 구성 요소에 매핑해야 한다는 것입니다.

![AEM에 관계없이](assets/aem-agnostic.png)

헬퍼는 `MapTo` 백엔드 구성 요소와 프런트 엔드 구성 요소를 함께 일치시키는 &quot;접착제&quot;입니다.

* JS 컨테이너(또는 JS 단락 시스템)에 JS 구성 요소가 JSON에 있는 각 구성 요소를 렌더링할 책임이 있는지 알려줍니다.
* JS 구성 요소가 렌더링하는 HTML에 HTML 데이터 속성을 추가하여 SPA 편집기가 구성 요소를 편집할 때 작성자에게 표시할 대화 상자를 알 수 있습니다.

AEM용 SPA `MapTo` 를 일반적으로 사용하고 구축하는 방법에 대한 자세한 내용은 선택한 프레임워크에 대한 시작하기 안내서를 참조하십시오.

* [React를 사용하여 AEM에서 SPA 시작하기](getting-started-react.md)
* [AEM에서 Angular를 사용하여 SPA 시작](getting-started-angular.md)

## AEM 아키텍처 및 SPA {#aem-architecture-and-spas}

개발, 저작 및 출판 환경을 포함한 AEM의 일반 아키텍처는 SPA를 사용할 때 변경되지 않습니다. 그러나 SPA 개발이 이 아키텍처에 어떻게 적합한지 파악하는 것이 도움이 됩니다.

![AEM 아키텍처 및 SPA](assets/aem-architecture.png)

* **빌드 환경**

   SPA 애플리케이션 소스 및 구성 요소 소스의 출처가 체크 아웃되는 곳입니다.

   * NPM clientlib 생성기는 SPA 프로젝트에서 클라이언트 라이브러리를 만듭니다.
   * 해당 라이브러리는 Maven에서 가져와 AEM 작성자에 구성 요소와 함께 Maven Build 플러그인에 의해 배포됩니다.

* **AEM Author**

   컨텐츠는 SPA 작성을 비롯하여 AEM 작성자에 의해 작성됩니다.

   작성 환경에서 SPA 편집기를 사용하여 SPA를 편집하는 경우:

   1. SPA가 외부 HTML을 요청합니다.
   1. CSS가 로드됩니다.
   1. SPA 응용 프로그램의 Javascript가 로드됩니다.
   1. SPA 응용 프로그램이 실행되면 JSON이 요청되므로, 앱에서 속성을 포함한 페이지의 DOM을 빌드할 수 `cq-data` 있습니다.
   1. 이 `cq-data` 속성을 사용하면 편집자가 추가 페이지 정보를 로드하여 구성 요소에 사용할 수 있는 편집 구성을 알 수 있습니다.

* **AEM 게시**

   SPA 응용 프로그램 객체, clientlibs 및 구성 요소를 비롯한 제작된 컨텐츠와 컴파일된 라이브러리가 공개 소비에 대해 게시되는 곳입니다.

* **발송자/CDN**

   디스패처는 사이트 방문자에 대해 AEM의 캐싱 레이어 역할을 합니다.
   * 요청은 AEM 작성자의 요청과 유사하게 처리되지만 편집자만 필요하므로 페이지 정보에 대한 요청은 없습니다.
   * Javascript, CSS, JSON 및 HTML이 캐시되므로 페이지를 최적화하여 신속하게 전달할 수 있습니다.

>[!NOTE]
>
>AEM 내부에서는 Javascript 빌드 메커니즘을 실행하거나 Javascript 자체를 실행할 필요가 없습니다. AEM은 SPA 애플리케이션에서 컴파일된 객체만 호스팅합니다.

## 다음 단계 {#next-steps}

* [React를 사용하여 AEM에서 SPA를 시작한다는 것은 React를 사용하여 AEM에서 SPA Editor와 연동되도록 기본 SPA가 어떻게 구축되었는지를 보여줍니다.](getting-started-react.md)
* [AEM에서 Started with SPAs using Angular](getting-started-angular.md) 는 AEM에서 SPA Editor와 함께 작동하도록 기본 SPA가 어떻게 구축되는지를 보여 줍니다.
* [SPA Editor 개요](editor-overview.md) 는 AEM과 SPA 간의 커뮤니케이션 모델에 대해 더 자세히 설명합니다.
* [WKND SPA Project](wknd-tutorial.md) 는 AEM에서 간단한 SPA 프로젝트를 구현하는 단계별 자습서입니다.
* [SPA에 대한 동적 모델-구성 요소 매핑](model-to-component-mapping.md) 기능은 구성 요소 간 동적 모델과 AEM의 SPA 내에서 작동하는 방식을 설명합니다.
* [SPA Blueprint](blueprint.md) 는 AEM에서 Reresponsive 또는 Angular 이외의 프레임워크를 위해 SPA를 구현하려는 경우 AEM용 SPA SDK의 작동 방식을 자세히 살펴볼 수 있습니다.
