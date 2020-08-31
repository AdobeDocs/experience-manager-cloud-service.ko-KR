---
title: SPA 블루프린트
description: 본 문서에서는 AEM 내에서 편집 가능한 SPA 구성 요소를 구현하기 위해 모든 SPA 프레임워크가 이행해야 하는 일반적인 프레임워크 독립적인 계약에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: f7d90d9cb41077a3a510f97a9f9f89f4b2b13cd9
workflow-type: tm+mt
source-wordcount: '2058'
ht-degree: 0%

---


# SPA 블루프린트 {#spa-blueprint}

저자가 AEM SPA Editor를 사용하여 SPA의 컨텐츠를 편집할 수 있도록 하려면 SPA가 반드시 충족해야 하는 요구 사항이 있습니다.

## 소개 {#introdcution}

본 문서에서는 AEM 내에서 편집 가능한 SPA 구성 요소를 구현하기 위해 모든 SPA 프레임워크가 충족해야 하는(즉, AEM 지원 계층) 일반적인 계약에 대해 설명합니다.

작성자가 AEM 페이지 편집기를 사용하여 단일 페이지 애플리케이션 프레임워크에 의해 노출된 데이터를 편집할 수 있도록 하려면, 프로젝트는 AEM 리포지토리 내 응용 프로그램에 대해 저장된 데이터의 의미론적 구조를 나타내는 모델의 구조를 해석할 수 있어야 합니다. 이러한 목표를 달성하기 위해 프레임워크에 관계없이 다음 두 개의 라이브러리가 제공됩니다.Adobe `PageModelManager` 와 `ComponentMapping`Creative Cloud

>[!NOTE]
>
>다음 요구 사항은 프레임워크에 영향을 받지 않습니다. 이러한 요구 사항이 충족되면 모듈, 구성 요소 및 서비스로 구성된 프레임워크별 레이어를 제공할 수 있습니다.
>
>**이러한 요구 사항은 AEM의 반응 및 각 프레임워크에 대해 이미 충족됩니다.** 이 블루프린트의 요구 사항은 AEM에서 사용할 다른 프레임워크를 구현하려는 경우에만 관련이 있습니다.

>[!CAUTION]
>
>AEM의 SPA 기능은 프레임워크에 영향을 받지 않지만 현재 Reimate 및 Angular 프레임워크만 지원됩니다.

## PageModelManager {#pagemodelmanager}

라이브러리는 SPA 프로젝트에서 사용할 NPM 패키지로 제공됩니다. `PageModelManager` SPA와 함께 제공되며 데이터 모델 관리자 역할을 합니다.

SPA를 대신하여 실제 컨텐츠 구조를 나타내는 JSON 구조의 검색 및 관리를 추상화합니다. 또한 구성 요소를 다시 렌더링해야 하는 시기를 알려주는 SPA와 동기화해야 합니다.

NPM 패키지 [@adobe/aem-spa-model-manager 참조](https://www.npmjs.com/package/@adobe/aem-spa-model-manager)

라이브러리를 초기화할 때 라이브러리 `PageModelManager`는 먼저 매개 변수, 메타 속성 또는 현재 URL을 통해 앱의 제공된 루트 모델을 로드합니다. 라이브러리가 현재 페이지의 모델이 루트 모델의 일부가 아니라고 식별하면 해당 모델이 하위 페이지의 모델로 포함됩니다.

![페이지 모델 통합](assets/page-model-consolidation.png)

### ComponentMapping {#componentmapping}

이 `ComponentMapping` 모듈은 프런트 엔드 프로젝트에 NPM 패키지로 제공됩니다. 프런트 엔드 구성 요소를 저장하고 SPA에서 프런트 엔드 구성 요소를 AEM 리소스 유형에 매핑할 수 있는 방법을 제공합니다. 이렇게 하면 응용 프로그램의 JSON 모델을 구문 분석할 때 구성 요소의 동적 확인이 가능합니다.

모델에 있는 각 항목에는 AEM 리소스 유형을 표시하는 `:type` 필드가 포함되어 있습니다. 마운트되면 프런트 엔드 구성 요소는 기본 라이브러리에서 받은 모델 조각을 사용하여 자체 렌더링할 수 있습니다.

#### 동적 모델을 구성 요소 매핑으로 {#dynamic-model-to-component-mapping}

AEM용 Javascript SPA SDK에서 구성 요소에 대한 동적 모델 매핑이 발생하는 방법에 대한 자세한 내용은 SPA에 대한 구성 요소 매핑 [으로 동적 모델을 참조하십시오](model-to-component-mapping.md).

### 프레임워크별 레이어 {#framework-specific-layer}

각 프런트 엔드 프레임워크에 대해 세 번째 레이어를 구현해야 합니다. 이 세 번째 라이브러리는 기본 라이브러리와 상호 작용하는 작업을 담당하고 있으며 데이터 모델과 상호 작용하기 위한 일련의 잘 통합되어 있고 사용하기 쉬운 진입점을 제공합니다.

이 문서의 나머지 부분에서는 이 중간 프레임워크 특정 레이어의 요구 사항을 설명하고 프레임워크에 의존할 수 있도록 합니다. 다음 요구 사항을 준수하여 프로젝트 구성 요소가 데이터 모델을 관리하는 기본 라이브러리와 상호 작용하도록 프레임워크별 레이어를 제공할 수 있습니다.

## 일반 개념 {#general-concepts}

### 페이지 모델 {#page-model}

페이지의 컨텐츠 구조는 AEM에 저장됩니다. 페이지의 모델은 SPA 구성 요소를 매핑하고 인스턴스화하는 데 사용됩니다. SPA 개발자들은 AEM 구성 요소에 매핑되는 SPA 구성 요소를 만듭니다. 이렇게 하려면 리소스 유형(또는 AEM 구성 요소의 경로)을 고유한 키로 사용합니다.

SPA 구성 요소는 페이지 모델과 동기화되어야 하며 그에 따라 컨텐츠의 변경 사항과 함께 업데이트해야 합니다. 동적 구성 요소를 활용하는 패턴을 사용하여 제공된 페이지 모델 구조를 따라 즉시 구성 요소를 인스턴스화해야 합니다.

### 메타 필드 {#meta-fields}

페이지 모델은 Sling Model API를 기반으로 하는 JSON Model Exporter [를](https://sling.apache.org/documentation/bundles/models.html) 활용합니다. 내보낼 수 있는 슬링 모델은 기본 라이브러리가 데이터 모델을 해석할 수 있도록 다음 필드 목록을 표시합니다.

* `:type`:AEM 리소스 유형(기본값 = 리소스 유형)
* `:children`:현재 리소스의 계층 하위 항목입니다. 하위는 현재 리소스의 내부 컨텐트에 속하지 않습니다(페이지를 나타내는 항목에서 찾을 수 있음).
* `:hierarchyType`:리소스의 계층적 유형입니다. 현재 페이지 유형을 `PageModelManager` 지원합니다.

* `:items`:현재 리소스의 하위 콘텐츠 리소스(중첩된 구조만 컨테이너에 있음)
* `:itemsOrder`:하위 목록 JSON 지도 개체는 해당 필드의 순서를 보증하지 않습니다. 맵과 현재 배열을 모두 갖음으로써 API의 소비자는 두 구조를 모두 활용할 수 있습니다
* `:path`:항목의 컨텐츠 경로(페이지를 나타내는 항목에 있음)

AEM [콘텐츠 서비스 시작도 참조하십시오.](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-with-aem-headless/overview.html)

### 프레임워크별 모듈 {#framework-specific-module}

우려 사항을 구분하면 프로젝트 구현이 용이합니다. 따라서 npm별 패키지를 제공해야 합니다. 이 패키지는 기본 모듈, 서비스 및 구성 요소를 집계 및 노출할 책임이 있습니다. 이러한 구성 요소는 데이터 모델 관리 논리를 캡슐화하고 프로젝트의 구성 요소에서 기대하는 데이터에 대한 액세스를 제공해야 합니다. 또한 이 모듈은 기본 라이브러리의 유용한 진입점을 일시적으로 노출할 책임이 있습니다.

Adobe은 라이브러리의 상호 운용성을 돕기 위해 프레임워크별 모듈에 다음 라이브러리를 번들로 묶도록 권장합니다. 필요한 경우 레이어는 기본 API를 캡슐화하여 프로젝트에 적용하기 전에 적용할 수 있습니다.

* [@adobe/aem-spa-model-manager](https://www.npmjs.com/package/@adobe/aem-spa-model-manager)
* [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

#### 구현 {#implementations}

#### 반응 {#react}

npm 모듈: [@adobe/aem-responsive-editable-components](https://www.npmjs.com/package/@adobe/aem-react-editable-components)

#### 각진 {#angular}

npm 모듈: [@adobe/cq-angular-editable-components](https://www.npmjs.com/package/@adobe/cq-angular-editable-components)

## 기본 서비스 및 구성 요소 {#main-services-and-components}

다음 개체는 각 프레임워크에 적용되는 지침에 따라 구현해야 합니다. 프레임워크 아키텍처를 기반으로 구현은 크게 다를 수 있지만 설명된 기능을 제공해야 합니다.

### 모델 공급자 {#the-model-provider}

프로젝트 구성 요소는 모델의 조각에 대한 액세스를 모델 공급자에 위임해야 합니다. 그러면 모델 공급자가 모델의 지정된 조각에 대한 변경 사항을 수신하고 업데이트된 모델을 위임 구성 요소에 반환해야 합니다.

이렇게 하려면 모델 공급자가 에 등록해야 합니다 [`PageModelManager`](#pagemodelmanager). 그런 다음 변경 사항이 발생하면 업데이트된 데이터를 수신하여 위임 구성 요소에 전달합니다. 규칙으로 모델의 조각을 전달하는 위임 구성 요소에 사용할 수 있는 속성의 이름이 지정됩니다 `cqModel`. 구현은 구성 요소에 이 속성을 제공하는 데 무료이지만 프레임워크 아키텍처와의 통합, 발견 가능성 및 사용 편이성 등의 측면을 고려해야 합니다.

### 구성 요소 HTML Decorator {#the-component-html-decorator}

구성 요소 데코레이터는 페이지 편집기에서 기대하는 일련의 데이터 속성과 클래스 이름으로 각 구성 요소 인스턴스의 외부 HTML을 장식할 책임이 있습니다.

#### 구성 요소 선언 {#component-declaration}

다음 메타 데이터를 프로젝트의 구성 요소에서 만든 외부 HTML 요소에 추가해야 합니다. 페이지 편집기에서 해당 편집 구성을 검색할 수 있습니다.

* `data-cq-data-path`:리소스를 기준으로 하는 경로 `jcr:content`

#### 기능 선언 및 자리 표시자 편집 {#editing-capability-declaration-and-placeholder}

다음 메타 데이터 및 클래스 이름은 프로젝트의 구성 요소에서 만든 외부 HTML 요소에 추가해야 합니다. 페이지 편집기에서 관련 기능을 제공할 수 있습니다.

* `cq-placeholder`:빈 구성 요소의 자리 표시자를 식별하는 클래스 이름
* `data-emptytext`:구성 요소 인스턴스가 비어 있을 때 오버레이에서 표시할 레이블

**빈 구성 요소에 대한 자리 표시자**

각 구성 요소는 비어 있는 것으로 식별될 때 자리 표시자 및 관련 오버레이에 관련된 데이터 특성 및 클래스 이름으로 외부 HTML 요소를 장식하는 기능으로 확장되어야 합니다.

**구성 요소의 공허함**

* 구성 요소가 논리적으로 비어 있습니까?
* 구성 요소가 비어 있을 때 오버레이에서 표시하는 레이블은 무엇입니까?

### 컨테이너 {#container}

컨테이너는 하위 구성 요소를 포함하고 렌더링하기 위한 구성 요소입니다. 이렇게 하려면 컨테이너가 모델의 `:itemsOrder`및 속성 `:items` `:children` 을 반복합니다.

컨테이너는 라이브러리의 저장소에서 자식 구성 요소를 동적으로 [`ComponentMapping`](#componentmapping) 가져옵니다. 그런 다음 컨테이너는 모델 공급자 기능으로 하위 구성 요소를 확장하고 마지막으로 인스턴스화합니다.

### 페이지 {#page}

구성 요소 `Page` 는 구성 요소를 `Container` 확장합니다. 컨테이너는 하위 페이지를 포함한 하위 구성 요소를 포함하고 렌더링하기 위한 구성 요소입니다. 이렇게 하려면 컨테이너가 해당 모델의 `:itemsOrder`속성, `:items`및 `:children` 속성을 반복합니다. 구성 요소 `Page` 는 라이브러리의 저장소에서 하위 구성 요소를 동적으로 [`ComponentMapping`](#componentmapping) 가져옵니다. 하위 구성 요소 `Page` 를 인스턴스화할 책임이 있습니다.

### 응답형 격자 {#responsive-grid}

응답형 격자 구성 요소는 컨테이너입니다. 여기에는 해당 열을 나타내는 모델 공급자의 특정 변형이 포함되어 있습니다. 응답형 격자 및 해당 열은 프로젝트 구성 요소의 외부 HTML 요소를 모델에 포함된 특정 클래스 이름으로 장식해야 합니다.

이 구성 요소는 복잡하고 거의 사용자 지정되지 않으므로 응답형 격자 구성 요소는 AEM에 미리 매핑되어야 합니다.

#### 특정 모델 필드 {#specific-model-fields}

* `gridClassNames:` 응답형 그리드에 대한 클래스 이름을 제공했습니다.
* `columnClassNames:` 응답형 열에 대한 클래스 이름을 제공했습니다.

npm resource [@adobe/aem-response-editable-components를 참조하십시오.](https://www.npmjs.com/package/@adobe/aem-react-editable-components)

#### 응답형 격자의 자리 표시자 {#placeholder-of-the-responsive-grid}

SPA 구성 요소는 응답형 격자와 같은 그래픽 컨테이너에 매핑되며, 컨텐츠가 작성될 때 가상 하위 자리 표시자를 추가해야 합니다. 페이지 편집기에 의해 SPA의 컨텐츠가 작성되면 해당 컨텐츠는 iframe을 사용하여 편집기에 임베드되고 속성은 해당 컨텐츠의 문서 노드에 추가됩니다. `data-cq-editor` 속성이 `data-cq-editor` 있는 경우, 컨테이너에는 새 구성 요소를 페이지에 삽입할 때 작성자가 상호 작용하는 영역을 나타내는 HTMLElement가 포함되어야 합니다.

예:

```
<div data-cq-data-path={"path/to/the/responsivegrid/*"} className="new section aem-Grid-newComponent"/>
```

>[!NOTE]
>
>이 예제에서 사용되는 클래스 이름은 현재 페이지 편집기에 필요합니다.
>
>* `"new section"`:현재 요소가 컨테이너의 자리 표시자임을 나타냅니다.
>* `"aem-Grid-newComponent"`:레이아웃 작성을 위한 구성 요소 정규화

>



#### Component Mapping {#component-mapping}

기본 [`Component Mapping`](#componentmapping) 라이브러리와 그 `MapTo` 기능은 캡슐화되고 확장되어 현재 구성 요소 클래스와 함께 제공된 편집 구성에 관련된 기능을 제공할 수 있습니다.

```
const EditConfig = {

    emptyLabel: 'My Component',

    isEmpty: function() {
        return !this.props || !this.props.cqModel || this.props.cqModel.isEmpty;
    }
};

class MyComponent extends Component {

    render() {
        return <div className={'my-component'}></div>;
    }
}

MapTo('component/resource/path')(MyComponent, EditConfig);
```

위의 구현에서 프로젝트 구성 요소는 [구성 요소 매핑](#componentmapping) 저장소에 실제로 등록되기 전에 비어 있는 기능으로 확장됩니다. 이렇게 하려면 라이브러리를 캡슐화하고 확장하여 구성 개체에 대한 지원을 [`ComponentMapping`](#componentmapping) `EditConfig` 도입합니다.

```
/**
 * Configuration object in charge of providing the necessary data expected by the page editor to initiate the authoring. The provided data will be decorating the associated component
 *
 * @typedef {{}} EditConfig
 * @property {String} [dragDropName]       If defined, adds a specific class name enabling the drag and drop functionality
 * @property {String} emptyLabel           Label to be displayed by the placeholder when the component is empty. Optionally returns an empty text value
 * @property {function} isEmpty            Should the component be considered empty. The function is called using the context of the wrapper component giving you access to the component model
 */

/**
 * Map a React component with the given resource types. If an {@link EditConfig} is provided the <i>clazz</i> is wrapped to provide edition capabilities on the AEM Page Editor
 *
 * @param {string[]} resourceTypes                      - List of resource types for which to use the given <i>clazz</i>
 * @param {class} clazz                                 - Class to be instantiated for the given resource types
 * @param {EditConfig} [editConfig]                     - Configuration object for enabling the edition capabilities
 * @returns {class}                                     - The resulting decorated Class
 */
ComponentMapping.map = function map (resourceTypes, clazz, editConfig) {};
```

## 페이지 편집기와 계약 {#contract-with-the-page-editor}

프로젝트 구성 요소는 편집자가 이러한 데이터 속성과 상호 작용할 수 있도록 다음과 같은 데이터 속성을 최소한 생성해야 합니다.

* `data-cq-data-path`:구성 요소의 상대 경로 `PageModel` (예: `"root/responsivegrid/image"`). 이 속성은 페이지에 추가할 수 없습니다.

요약하면 페이지 편집기로 해석하려면 프로젝트 구성 요소는 다음 계약을 존중해야 합니다.

* 프런트 엔드 구성 요소 인스턴스를 AEM 리소스에 연결할 예상 특성을 제공합니다.
* 빈 자리 표시자를 만들 수 있도록 필요한 일련의 특성과 클래스 이름을 제공합니다.
* 필요한 클래스 이름을 지정하여 자산을 드래그하여 놓을 수 있습니다.

### 일반 HTML 요소 구조 {#typical-html-element-structure}

다음 조각은 페이지 컨텐츠 구조의 일반적인 HTML 표현을 보여 줍니다. 다음은 몇 가지 중요한 사항입니다.

* 응답형 격자 요소에는 `aem-Grid--`
* 응답형 열 요소에는 `aem-GridColumn--`
* 이전 두 개의 접두사가 동일한 요소에 나타나지 않는 것처럼 부모 격자의 열이기도 한 응답형 격자
* 편집 가능한 리소스에 해당하는 요소에는 속성이 `data-cq-data-path` 적용됩니다. 이 [문서의 페이지 편집기로](#contract-wtih-the-page-editor) 계약 섹션을 참조하십시오.

```
<div data-cq-data-path="/content/page">
    <div class="aem-Grid aem-Grid--12 aem-Grid--default--12">
        <div class="aem-container aem-GridColumn aem-GridColumn--default--12" data-cq-data-path="/content/page/jcr:content/root/responsivegrid">
            <div class="aem-Grid aem-Grid--12 aem-Grid--default--12">
                <div class="cmp-image cq-dd-image aem-GridColumn aem-GridColumn--default--12" data-cq-data-path="/root/responsivegrid/image">
                    <img src="/content/we-retail-spa-sample/react/jcr%3acontent/root/responsivegrid/image.img.jpeg/1512113734019.jpeg">
                </div>
            </div>
        </div>
    </div>
</div>
```

## 탐색 및 라우팅 {#navigation-and-routing}

앱이 라우팅을 소유합니다. 프런트 엔드 개발자는 먼저 내비게이션 구성 요소를 구현해야 합니다(AEM 탐색 구성 요소에 매핑됨). 이 구성 요소는 컨텐츠 조각을 표시하거나 숨길 일련의 경로와 함께 사용할 URL 링크를 렌더링합니다.

기본 [`PageModelManager`](#pagemodelmanager) 라이브러리와 해당 [`ModelRouter`](routing.md) 모듈(기본적으로 활성화됨)은 주어진 리소스 경로와 연관된 모델에 대한 사전 반입과 액세스 권한을 제공합니다.

두 개체는 라우팅 개념과 관련되지만, [`ModelRouter`](routing.md) 는 현재 응용 프로그램 상태와 동기화되어 있는 데이터 모델 [`PageModelManager`](#pagemodelmanager) 과 데이터를 로드해야 합니다.

자세한 내용은 [SPA 모델 라우팅](routing.md) 아티클을 참조하십시오.

## SPA in Action {#spa-in-action}

다음과 같은 문서를 계속 진행하여 간단한 SPA가 작동하는 방식을 살펴보고 SPA를 직접 경험해 보십시오.

* [React를 사용하여 AEM에서 SPA 시작하기](getting-started-react.md).
* [AEM에서 Angular를 사용하여 SPA 시작](getting-started-angular.md).

## Further Reading {#further-reading}

AEM의 SPA에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [SPA 편집기](editor-overview.md) 개요 - AEM의 SPA 및 커뮤니케이션 모델 개요

