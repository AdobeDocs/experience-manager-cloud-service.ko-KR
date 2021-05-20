---
title: React를 사용하여 AEM에서 SPA 시작하기
description: 이 문서에서는 샘플 SPA 애플리케이션을 제공하며 이 응용 프로그램을 구성하는 방법을 설명하고 React 프레임워크를 사용하여 신속하게 자체 SPA을 사용하여 실행 및 실행할 수 있도록 해줍니다.
exl-id: 13998526-65e7-4d1b-bd47-452bad3780a2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 3%

---

# React {#getting-started-with-spas-in-aem-using-react}를 사용하여 AEM에서 SPA 시작하기

SPA(단일 페이지 애플리케이션)는 웹 사이트 사용자에게 훌륭한 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크을 사용하여 사이트를 작성하려고 하며 작성자는 SPA 프레임워크을 사용하여 작성된 사이트의 AEM 내에서 컨텐츠를 원활하게 편집하려고 합니다.

SPA 작성 기능은 AEM 내에서 SPA을 지원하는 포괄적인 솔루션을 제공합니다. 이 문서에서는 React 프레임워크에 간소화된 SPA 애플리케이션을 제공하며 이 응용 프로그램을 어떻게 결합하는지 설명하므로 SPA을 빠르게 시작하고 실행할 수 있습니다.

>[!NOTE]
>
>이 문서는 React 프레임워크를 기반으로 합니다. angular 프레임워크에 대한 해당 문서는 [AEM에서 SPA 시작하기 - Angular](getting-started-angular.md)를 참조하십시오.

## 소개 {#introduction}

이 문서에서는 간단한 SPA의 기본 기능과 최소 기능을 사용하여 실행할 수 있도록 합니다.

AEM에서 SPA이 작동하는 방법에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [SPA 소개 및 연습](introduction.md)
* [SPA 편집기 개요](editor-overview.md)
* [SPA 블루프린트](blueprint.md)

>[!NOTE]
>
>SPA 내에서 컨텐츠를 작성할 수 있으려면 컨텐츠를 AEM에 저장하고 컨텐츠 모델에 의해 노출되어야 합니다.
>
>AEM 외부에서 개발된 SPA은 컨텐츠 모델 계약을 준수하지 않으면 승인되지 않습니다.

이 문서는 React 프레임워크를 사용하여 만든 간소화된 SPA의 구조를 살펴보고 이 이해를 SPA에 적용할 수 있도록 작동 방식을 설명합니다.

## 종속성, 구성 및 빌드 {#dependencies-configuration-and-building}

예상되는 React 종속성 외에도, 샘플 SPA은 추가 라이브러리를 활용하여 SPA을 보다 효율적으로 만들 수 있습니다.

### 종속성 {#dependencies}

`package.json` 파일은 전체 SPA 패키지의 요구 사항을 정의합니다. 작업 SPA에 대한 최소 AEM 종속성은 여기에 나열됩니다.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

이 예는 React 프레임워크를 기반으로 하므로 `package.json` 파일에 의무적인 두 개의 React-특정 종속성이 있습니다.

```
 react
 react-dom
```

`aem-clientlib-generator`은 빌드 프로세스의 일부로 클라이언트 라이브러리를 자동으로 만드는 데 사용됩니다.

`"aem-clientlib-generator": "^1.4.1",`

이에 대한 자세한 내용은 여기](https://github.com/wcm-io-frontend/aem-clientlib-generator)GitHub에서 [을 참조하십시오.

`aem-clientlib-generator`은 `clientlib.config.js` 파일에 다음과 같이 구성됩니다.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-react-app/clientlibs",

    libs: {
        name: "my-react-app",
        allowProxy: true,
        categories: ["my-react-app"],
        embed: ["my-react-app.responsivegrid"],
        jsProcessor: ["min:gcc"],
        serializationFormat: "xml",
        assets: {
            js: [
                "dist/**/*.js"
            ],
            css: [
                "dist/**/*.css"
            ]
        }
    }
};
```

### 빌딩 {#building}

실제로 앱을 빌드하면 자동 클라이언트 라이브러리 생성을 위한 aem-clientlib-generator 외에 전달을 위해 [Webpack](https://webpack.js.org/)이 활용됩니다. 따라서 build 명령은 다음과 같습니다.

`"build": "webpack && clientlib --verbose"`

완료되면 패키지를 AEM 인스턴스에 업로드할 수 있습니다.

### AEM 프로젝트 전형 {#aem-project-archetype}

모든 AEM 프로젝트는 React 또는 Angular을 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 [AEM Project Archetype](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)을 활용해야 합니다.

## 응용 프로그램 구조 {#application-structure}

앞에서 설명한 대로 종속성을 포함하고 앱을 빌드하면 AEM 인스턴스에 업로드할 수 있는 작업 SPA 패키지가 표시됩니다.

이 문서의 다음 섹션에서는 AEM에서 SPA을 구성하는 방법, 애플리케이션을 구동하는 중요한 파일 및 이러한 파일이 함께 작동하는 방식을 살펴봅니다.

간소화된 이미지 구성 요소가 예로 사용되지만 애플리케이션의 모든 구성 요소는 동일한 개념을 기반으로 합니다.

### index.js {#index-js}

SPA의 시작 지점은 중요한 컨텐츠에 초점을 맞추기 위해 여기에 표시된 `index.js` 파일입니다.

```
import ReactDOM from 'react-dom';
import App from './App';
import { ModelManager, Constants } from "@adobe/aem-spa-page-model-manager";

...

ModelManager.initialize().then((pageModel) => {
ReactDOM.render(
    <App cqChildren={pageModel[Constants.CHILDREN_PROP]} cqItems={pageModel[Constants.ITEMS_PROP]} cqItemsOrder={pageModel[Constants.ITEMS_ORDER_PROP]} cqPath={ModelManager.rootPath} locationPathname={ window.location.pathname }/>
, document.getElementById('page'));

});
```

`index.js`의 주요 함수는 `ReactDOM.render` 함수를 활용하여 DOM에서 애플리케이션을 삽입할 위치를 결정하는 것입니다.

이 예제 앱에서는 고유하지 않고 이 함수의 표준 사용 방법입니다.

#### 정적 인스턴스화 {#static-instantiation}

구성 요소 템플릿(예: JSX)을 사용하여 구성 요소가 정적으로 인스턴스화될 때, 이 값은 모델에서 구성 요소의 속성으로 전달되어야 합니다.

### App.js {#app-js}

앱을 렌더링하여 `index.js`은(는) `App.js`을 호출합니다. cm.eversttech.net은 중요한 컨텐츠에 초점을 맞추기 위해 여기에 간소화된 버전으로 표시됩니다.

```
import {Page, withModel } from '@adobe/aem-react-editable-components';

...

class App extends Page {
...
}

export default withModel(App);
```

`App.js` 주로 앱을 구성하는 루트 구성 요소를 래핑하는 데 사용됩니다. 앱의 시작 지점은 페이지입니다.

### Page.js {#page-js}

페이지를 렌더링하여 `App.js`은(는) 여기에 나열된 `Page.js`을(를) 간소화된 버전으로 호출합니다.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

이 예제에서 `AppPage` 클래스는 `Page`을 확장합니다. 그러면 사용할 수 있는 내부 컨텐츠 메서드가 포함됩니다.

`Page` 은 페이지 모델의 JSON 표현을 수집하고 컨텐츠를 처리하여 페이지의 각 요소를 래핑/장식합니다. `Page`에 대한 자세한 내용은 [SPA 블루프린트에서 확인할 수 있습니다.](blueprint.md)

### Image.js {#image-js}

페이지를 렌더링하면 여기에 표시된 대로 `Image.js` 등의 구성 요소를 렌더링할 수 있습니다.

```
import React, {Component} from 'react';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Image.css');

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function() {
        return !this.props || !this.props.src || this.props.src.trim().length < 1;
    }
};

class Image extends Component {

    render() {
        return (<img src={this.props.src}>);
    }
}

MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);
```

AEM에서 SPA의 핵심 개념은 SPA 구성 요소를 AEM 구성 요소에 매핑하고 컨텐츠가 수정될 때(또는 그 반대로) 구성 요소를 업데이트하는 것입니다. 이 통신 모델에 대한 요약은 [SPA 편집기 개요](editor-overview.md) 문서를 참조하십시오.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

`MapTo` 메서드는 SPA 구성 요소를 AEM 구성 요소에 매핑합니다. 단일 문자열 또는 문자열 배열을 사용할 수 있습니다.

`ImageEditConfig` 는 편집기에서 자리 표시자를 생성하는 데 필요한 메타데이터를 제공하여 구성 요소의 작성 기능을 활성화하는 데 기여하는 구성 개체입니다

콘텐츠가 없으면 빈 콘텐츠를 나타내는 자리 표시자로 레이블이 제공됩니다.

#### 동적으로 전달된 속성 {#dynamically-passed-properties}

모델에서 나오는 데이터는 구성 요소의 속성으로 동적으로 전달됩니다.

## 편집 가능한 컨텐츠 {#exporting-editable-content} 내보내기

구성 요소를 내보내고 편집 가능하게 유지할 수 있습니다.

```
import React, { Component } from 'react';
import { MapTo } from '@adobe/aem-react-editable-components';

...

const EditConfig = {...}

class PageClass extends Component {...};

...

export default MapTo('my-react-app/react/components/structure/page')(PageClass, EditConfig);
```

`MapTo` 함수는 `Component` 를 반환합니다. 이 결과는 작성을 활성화하는 클래스 이름과 특성을 사용하여 제공된 `PageClass`를 확장하는 작성 결과입니다. 이 구성 요소는 나중에 애플리케이션 마크업에서 인스턴스화하도록 내보낼 수 있습니다.

`MapTo` 또는 `withModel` 함수를 사용하여 내보낼 때 `Page` 구성 요소는 최신 버전의 페이지 모델에 대한 표준 구성 요소 또는 해당 페이지 모델의 정확한 위치에 액세스할 수 있는 `ModelProvider` 구성 요소로 래핑됩니다.

자세한 내용은 [SPA 블루프린트 문서](blueprint.md)를 참조하십시오.

>[!NOTE]
>
>기본적으로 `withModel` 함수를 사용할 때 구성 요소의 전체 모델을 받습니다.

## SPA 구성 요소 간 정보 공유 {#sharing-information-between-spa-components}

단일 페이지 애플리케이션 내의 구성 요소가 정보를 공유하려면 정기적으로 필요합니다. 다음과 같이 복잡도 순서로 나열하는 몇 가지 권장 방법이 있습니다.

* **옵션 1:** React Context를 사용하여 논리 및 브로드캐스트를 필요한 구성 요소로 중앙 집중화합니다.
* **옵션 2:** Redux와 같은 상태 라이브러리를 사용하여 구성 요소 상태를 공유합니다.
* **옵션 3:** 컨테이너 구성 요소를 사용자 지정하고 확장하여 객체 계층 구조를 활용합니다.

## 다음 단계 {#next-steps}

* [Angular를 사용하여 AEM](getting-started-angular.md) 에서 SPA 시작하기 은 Angular을 사용하여 AEM에서 SPA 편집기로 작동하기 위해 기본 SPA을 어떻게 빌드하는지 보여줍니다.
* [SPA ](editor-overview.md) 편집기 개요는 AEM과 SPA 간의 통신 모델에 대해 자세히 설명합니다.
* [WKND SPA ](wknd-tutorial.md) Projectials는 AEM에서 간단한 SPA 프로젝트를 구현하는 단계별 자습서입니다.
* [SPA에 대한 동적 모델과 구성 ](model-to-component-mapping.md) 요소 간 매핑이 AEM에서 SPA 내에서 작동하는 방식에 대해 설명합니다.
* [SPA ](blueprint.md) Blueprint는 React 또는 Angular 이외의 프레임워크를 위해 AEM에서 SPA을 구현하거나 단순히 더 깊이 이해하고 싶은 경우 AEM용 SPA SDK가 작동하는 방식을 자세히 살펴봅니다.
