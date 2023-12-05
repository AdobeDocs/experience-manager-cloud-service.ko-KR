---
title: React를 사용하여 AEM에서 SPA 시작하기
description: 이 문서에서는 샘플 SPA 애플리케이션을 제공하고, 구성 방법을 설명하며, React 프레임워크를 사용하여 SPA을 빠르게 시작하고 실행할 수 있도록 해 줍니다.
exl-id: 13998526-65e7-4d1b-bd47-452bad3780a2
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 5%

---

# React를 사용하여 AEM에서 SPA 시작하기 {#getting-started-with-spas-in-aem-using-react}

SPA(단일 페이지 애플리케이션)는 웹 사이트 사용자에게 적합한 멋진 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크를 사용하여 사이트를 작성하려고 하며 작성자는 SPA 프레임워크를 사용하여 빌드된 사이트의 AEM 내 콘텐츠를 원활하게 편집하려고 합니다.

SPA 작성 기능은 AEM 내에서 SPA을 지원하는 포괄적인 솔루션을 제공합니다. 이 문서에서는 React 프레임워크의 간소화된 SPA 애플리케이션을 제공하고, 구성 방법을 설명하여 고유한 SPA을 빠르게 시작하고 실행할 수 있도록 해 줍니다.

>[!NOTE]
>
>이 문서는 React 프레임워크를 기반으로 합니다. angular 프레임워크에 대한 해당 문서는 을 참조하십시오. [AEM에서 SPA 시작하기 - Angular](getting-started-angular.md).

## 소개 {#introduction}

이 문서에서는 간단한 SPA의 기본 기능과 실행하는 데 필요한 최소 사항을 요약합니다.

AEM에서 SPA이 작동하는 방법에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [SPA 소개 및 워크스루](introduction.md)
* [SPA 편집기 개요](editor-overview.md)
* [SPA 블루프린트](blueprint.md)

>[!NOTE]
>
>SPA 내에서 컨텐츠를 작성할 수 있으려면 컨텐츠가 AEM에 저장되고 컨텐츠 모델에 의해 표시되어야 합니다.
>
>AEM 외부에서 개발된 SPA이 콘텐츠 모델 계약을 준수하지 않는 경우 작성할 수 없습니다.

이 문서에서는 React 프레임워크를 사용하여 만든 간소화된 SPA의 구조를 살펴보고 그 작동 방식을 보여 주므로 이러한 이해를 귀하의 SPA에 적용할 수 있습니다.

## 종속성, 구성 및 작성 {#dependencies-configuration-and-building}

샘플 SPA은 예상 React 종속성 외에도 추가 라이브러리를 사용하여 SPA을 보다 효율적으로 만들 수 있습니다.

### 종속성 {#dependencies}

다음 `package.json` 파일은 전체 SPA 패키지의 요구 사항을 정의합니다. 작동 중인 SPA의 최소 AEM 종속성이 여기에 나열됩니다.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

이 예제는 React 프레임워크를 기반으로 하므로 에는 두 가지 React 관련 종속성이 있습니다 `package.json` 파일:

```
 react
 react-dom
```

다음 `aem-clientlib-generator` 빌드 프로세스의 일부로 클라이언트 라이브러리를 자동으로 만드는 데 사용됩니다.

`"aem-clientlib-generator": "^1.4.1",`

이에 대한 자세한 내용은 를 참조하십시오 [GitHub의 여기](https://github.com/wcm-io-frontend/aem-clientlib-generator).

다음 `aem-clientlib-generator` 이(가)에 구성되어 있습니다. `clientlib.config.js` 파일을 다음과 같이 지정합니다.

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

### 빌드 중 {#building}

실제로 앱 사용 빌드 [Webpack](https://webpack.js.org/) 자동 클라이언트 라이브러리 생성을 위해 aem-clientlib-generator와 함께 전송할 수 있습니다. 따라서 빌드 명령은 다음과 비슷합니다.

`"build": "webpack && clientlib --verbose"`

빌드되면 패키지를 AEM 인스턴스에 업로드할 수 있습니다.

### AEM Project Archetype {#aem-project-archetype}

AEM 프로젝트는 React 또는 Angular를 통해 SPA 프로젝트를 지원하고 SPA SDK를 사용하는 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)을 사용해야 합니다.

## 애플리케이션 구조 {#application-structure}

종속성을 포함하고 앞에서 설명한 대로 앱을 빌드하면 AEM 인스턴스에 업로드할 수 있는 작업 SPA 패키지가 제공됩니다.

이 문서의 다음 섹션에서는 AEM의 SPA이 구성되는 방식, 애플리케이션을 구동하는 중요한 파일 및 함께 작동하는 방식에 대해 설명합니다.

간소화된 이미지 구성 요소를 예로 사용하지만, 애플리케이션의 모든 구성 요소는 동일한 개념을 기반으로 한다.

### index.js {#index-js}

SPA의 진입점은 입니다. `index.js` 여기에 표시된 파일은 중요한 콘텐츠에 집중할 수 있도록 단순화되었습니다.

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

의 주요 기능 `index.js` 은(는) 을(를) 사용합니다. `ReactDOM.render` dom에서 응용 프로그램을 삽입할 위치를 결정하는 함수입니다.

이는 이 예제 앱에만 적용되는 것이 아니라 이 기능의 표준 사용입니다.

#### 정적 인스턴스화 {#static-instantiation}

구성 요소가 구성 요소 템플릿(예: JSX)을 사용하여 정적으로 인스턴스화되면 모델에서 구성 요소의 속성으로 값을 전달해야 합니다.

### App.js {#app-js}

앱을 렌더링하면 `index.js` 호출 `App.js`중요 콘텐츠에 집중할 수 있도록 간소화된 버전으로 여기에 표시됩니다.

```
import {Page, withModel } from '@adobe/aem-react-editable-components';

...

class App extends Page {
...
}

export default withModel(App);
```

`App.js` 주로 앱을 구성하는 루트 구성 요소를 래핑하는 역할을 합니다. 앱의 진입점은 페이지입니다.

### Page.js {#page-js}

페이지를 렌더링하여 `App.js` 호출 `Page.js` 다음은 간소화된 버전에 나열되어 있습니다.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

이 예에서는 `AppPage` 클래스 확장 `Page`: 내부 콘텐츠 메서드를 포함하고서 사용할 수 있습니다.

다음 `Page` 페이지 모델의 JSON 표현을 수집하고 콘텐츠를 처리하여 페이지의 각 요소를 래핑/장식합니다. 에 대한 추가 세부 정보 `Page` 문서에서 찾을 수 있음 [SPA 블루프린트입니다.](blueprint.md)

### Image.js {#image-js}

페이지가 렌더링됨에 따라 구성 요소 `Image.js` 여기에 표시된 대로 렌더링할 수 있습니다.

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

AEM에서 SPA의 핵심 아이디어는 SPA 구성 요소를 AEM 구성 요소에 매핑하고 콘텐츠가 수정될 때(그리고 그와 반대되게) 구성 요소를 업데이트하는 아이디어입니다. 문서 보기 [SPA 편집기 개요](editor-overview.md) 이 커뮤니케이션 모델에 대한 요약 정보를 제공합니다.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

다음 `MapTo` 메서드는 SPA 구성 요소를 AEM 구성 요소에 매핑합니다. 단일 문자열 또는 문자열 배열의 사용을 지원합니다.

`ImageEditConfig` 는 편집기가 자리 표시자를 생성하는 데 필요한 메타데이터를 제공하여 구성 요소의 작성 기능을 활성화하는 데 기여하는 구성 개체입니다

콘텐츠가 없는 경우 빈 콘텐츠를 나타내는 자리 표시자로 레이블이 제공됩니다.

#### 동적으로 전달된 속성 {#dynamically-passed-properties}

모델에서 나온 데이터는 구성 요소의 속성으로 동적으로 전달됩니다.

## 편집 가능한 컨텐츠 내보내기 {#exporting-editable-content}

구성 요소를 내보내고 편집 가능한 상태로 유지할 수 있습니다.

```
import React, { Component } from 'react';
import { MapTo } from '@adobe/aem-react-editable-components';

...

const EditConfig = {...}

class PageClass extends Component {...};

...

export default MapTo('my-react-app/react/components/structure/page')(PageClass, EditConfig);
```

다음 `MapTo` 함수는 를 반환합니다. `Component` 제공된 를 확장하는 컴포지션의 결과입니다 `PageClass` 작성을 활성화하는 클래스 이름 및 속성 포함. 이 구성 요소를 내보내어 나중에 응용 프로그램의 마크업에서 인스턴스화할 수 있습니다.

를 사용하여 내보낼 때 `MapTo` 또는 `withModel` 함수, `Page` 구성 요소를 래핑합니다 `ModelProvider` 구성 요소는 표준 구성 요소에 페이지 모델의 최신 버전 또는 해당 페이지 모델의 정확한 위치에 대한 액세스를 제공합니다.

자세한 내용은 [SPA 블루프린트 문서](blueprint.md).

>[!NOTE]
>
>기본적으로 를 사용할 때 구성 요소의 전체 모델을 받습니다. `withModel` 함수.

## SPA 구성 요소 간 정보 공유 {#sharing-information-between-spa-components}

단일 페이지 애플리케이션 내의 구성 요소가 정보를 공유하는 것은 정기적으로 필요합니다. 이 작업을 수행하는 방법에는 다음과 같이 복잡성이 증가하는 순서로 나열되는 몇 가지 방법이 권장됩니다.

* **옵션 1:** 예를 들어 React Context를 사용하여 논리를 중앙 집중화하고 필요한 구성 요소에 브로드캐스트합니다.
* **옵션 2:** Redux와 같은 상태 라이브러리를 사용하여 구성 요소 상태를 공유할 수 있습니다.
* **옵션 3:** 컨테이너 구성 요소를 사용자 정의하고 확장하여 개체 계층 구조를 활용합니다.

## 다음 단계 {#next-steps}

* [angular을 사용하여 AEM에서 SPA 시작하기](getting-started-angular.md) angular을 사용하여 AEM에서 SPA 편집기로 작동하도록 기본 SPA을 빌드한 방법을 보여 줍니다.
* [SPA 편집기 개요](editor-overview.md)는 AEM과 SPA 간의 커뮤니케이션 모델에 대해 자세히 설명합니다.
* [WKND SPA 프로젝트](wknd-tutorial.md) 는 AEM에서 간단한 SPA 프로젝트를 구현하는 단계별 자습서입니다.
* [SPA용 동적 모델과 구성 요소 간 매핑](model-to-component-mapping.md) 구성 요소 매핑에 대한 동적 모델과 AEM의 SPA 내에서 작동하는 방식에 대해 설명합니다.
* [SPA 블루프린트](blueprint.md) 에서는 React 또는 Angular 이외의 프레임워크에 대해 AEM을 구현하거나 간단히 더 깊이 이해하고 싶은 경우 AEMSPA 용 SPA SDK의 작동 방식에 대해 자세히 알아봅니다.
