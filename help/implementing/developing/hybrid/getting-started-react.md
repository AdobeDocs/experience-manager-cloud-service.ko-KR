---
title: React를 사용하여 AEM에서 SPA 시작하기
description: 이 문서에서는 샘플 SPA 애플리케이션을 제공하며 이 응용 프로그램을 구성하는 방법을 설명하고 React 프레임워크를 사용하여 신속하게 자체 SPA을 사용하여 실행 및 실행할 수 있도록 해줍니다.
exl-id: 13998526-65e7-4d1b-bd47-452bad3780a2
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 3%

---

# React를 사용하여 AEM에서 SPA 시작하기 {#getting-started-with-spas-in-aem-using-react}

SPA(단일 페이지 애플리케이션)는 웹 사이트 사용자에게 훌륭한 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크을 사용하여 사이트를 작성하려고 하며 작성자는 SPA 프레임워크을 사용하여 작성된 사이트의 AEM 내에서 컨텐츠를 원활하게 편집하려고 합니다.

SPA 작성 기능은 AEM 내에서 SPA을 지원하는 포괄적인 솔루션을 제공합니다. 이 문서에서는 React 프레임워크에 간소화된 SPA 애플리케이션을 제공하며 이 응용 프로그램을 어떻게 결합하는지 설명하므로 SPA을 빠르게 시작하고 실행할 수 있습니다.

>[!NOTE]
>
>이 문서는 React 프레임워크를 기반으로 합니다. angular 프레임워크에 대한 해당 문서는 [AEM에서 SPA 시작하기 - Angular](getting-started-angular.md).

## 소개 {#introduction}

이 문서에서는 간단한 SPA의 기본 기능과 최소 기능을 사용하여 실행할 수 있도록 합니다.

AEM에서 SPA이 작동하는 방법에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [SPA 소개 및 워크스루](introduction.md)
* [SPA 편집기 개요](editor-overview.md)
* [SPA 블루프린트](blueprint.md)

>[!NOTE]
>
>SPA 내에서 컨텐츠를 작성할 수 있으려면 컨텐츠를 AEM에 저장하고 컨텐츠 모델에 의해 노출되어야 합니다.
>
>AEM 외부에서 개발된 SPA은 컨텐츠 모델 계약을 준수하지 않으면 승인되지 않습니다.

이 문서는 React 프레임워크를 사용하여 만든 간소화된 SPA의 구조를 살펴보고 이 이해를 SPA에 적용할 수 있도록 작동 방식을 설명합니다.

## 종속성, 구성 및 작성 {#dependencies-configuration-and-building}

예상되는 React 종속성 외에도, 샘플 SPA은 추가 라이브러리를 활용하여 SPA을 보다 효율적으로 만들 수 있습니다.

### 종속성 {#dependencies}

다음 `package.json` 파일은 전체 SPA 패키지의 요구 사항을 정의합니다. 작업 SPA에 대한 최소 AEM 종속성은 여기에 나열됩니다.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

이 예는 React 프레임워크를 기반으로 하므로, 에는 두 개의 React-specific 종속성이 있으며, 이 종속성은 `package.json` 파일:

```
 react
 react-dom
```

다음 `aem-clientlib-generator` 는 빌드 프로세스의 일부로 클라이언트 라이브러리를 자동으로 만드는 데 사용됩니다.

`"aem-clientlib-generator": "^1.4.1",`

자세한 내용은 [설정](https://github.com/wcm-io-frontend/aem-clientlib-generator).

다음 `aem-clientlib-generator` 는 `clientlib.config.js` 다음과 같이 파일을 지정합니다.

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

실제로 앱을 빌드하면 활용됩니다 [웹 팩](https://webpack.js.org/) 자동 클라이언트 라이브러리 생성을 위한 aem-clientlib-generator 외에 전달을 위한 것입니다. 따라서 build 명령은 다음과 같습니다.

`"build": "webpack && clientlib --verbose"`

완료되면 패키지를 AEM 인스턴스에 업로드할 수 있습니다.

### AEM Project Archetype {#aem-project-archetype}

모든 AEM 프로젝트는 [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html): React 또는 Angular을 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용합니다.

## 응용 프로그램 구조 {#application-structure}

앞에서 설명한 대로 종속성을 포함하고 앱을 빌드하면 AEM 인스턴스에 업로드할 수 있는 작업 SPA 패키지가 표시됩니다.

이 문서의 다음 섹션에서는 AEM에서 SPA을 구성하는 방법, 애플리케이션을 구동하는 중요한 파일 및 이러한 파일이 함께 작동하는 방식을 살펴봅니다.

간소화된 이미지 구성 요소가 예로 사용되지만 애플리케이션의 모든 구성 요소는 동일한 개념을 기반으로 합니다.

### index.js {#index-js}

SPA의 진입점은 물론 `index.js` 여기에 표시된 파일은 중요한 컨텐츠에 집중할 수 있도록 간소화되었습니다.

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

의 기본 함수 `index.js` 그것은 `ReactDOM.render` DOM에서 애플리케이션을 삽입할 위치를 결정하는 함수입니다.

이 예제 앱에서는 고유하지 않고 이 함수의 표준 사용 방법입니다.

#### 정적 인스턴스화 {#static-instantiation}

구성 요소가 구성 요소 템플릿(예: JSX)을 사용하여 정적으로 인스턴스화될 때, 이 값은 모델에서 구성 요소의 속성으로 전달되어야 합니다.

### App.js {#app-js}

앱을 렌더링하여, `index.js` 호출 `App.js`- 중요한 컨텐츠에 집중할 수 있도록 간소화된 버전으로 여기에 표시됩니다.

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

페이지를 렌더링하여, `App.js` 호출 `Page.js` 여기에 간소화된 버전으로 나열됩니다.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

이 예에서 `AppPage` 클래스 확장 `Page`에는 사용할 수 있는 내부 컨텐츠 메서드가 포함되어 있습니다.

다음 `Page` 페이지 모델의 JSON 표현을 설정하고 컨텐츠를 처리하여 페이지의 각 요소를 래핑/장식합니다. 에 대한 자세한 내용 `Page` 문서에서 찾을 수 있습니다. [SPA 블루프린트.](blueprint.md)

### Image.js {#image-js}

페이지가 렌더링되면 다음과 같은 구성 요소가 제공됩니다. `Image.js` 여기에 표시된 대로 렌더링할 수 있습니다.

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

AEM에서 SPA의 핵심 개념은 SPA 구성 요소를 AEM 구성 요소에 매핑하고 컨텐츠가 수정될 때(또는 그 반대로) 구성 요소를 업데이트하는 것입니다. 문서를 참조하십시오 [SPA 편집기 개요](editor-overview.md) 이 통신 모델에 대한 요약입니다.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

다음 `MapTo` 메서드는 SPA 구성 요소를 AEM 구성 요소에 매핑합니다. 단일 문자열 또는 문자열 배열을 사용할 수 있습니다.

`ImageEditConfig` 는 편집기에서 자리 표시자를 생성하는 데 필요한 메타데이터를 제공하여 구성 요소의 작성 기능을 활성화하는 데 기여하는 구성 개체입니다

콘텐츠가 없으면 빈 콘텐츠를 나타내는 자리 표시자로 레이블이 제공됩니다.

#### 동적으로 전달된 속성 {#dynamically-passed-properties}

모델에서 나오는 데이터는 구성 요소의 속성으로 동적으로 전달됩니다.

## 편집 가능한 컨텐츠 내보내기 {#exporting-editable-content}

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

다음 `MapTo` 함수 반환 `Component` 상기 제공된 상기 조성물을 확장하는 조성물의 결과인 `PageClass` 작성할 클래스 이름과 속성을 사용합니다. 이 구성 요소는 나중에 애플리케이션 마크업에서 인스턴스화하도록 내보낼 수 있습니다.

를 사용하여 내보낼 때 `MapTo` 또는 `withModel` 함수, `Page` 구성 요소, 로 래핑됨 `ModelProvider` 구성 요소로서 최신 버전의 페이지 모델 또는 해당 페이지 모델의 정확한 위치에 대한 표준 구성 요소에 액세스할 수 있습니다.

자세한 내용은 [SPA 블루프린트 문서](blueprint.md).

>[!NOTE]
>
>기본적으로 를 사용할 때 구성 요소의 전체 모델을 받습니다 `withModel` 함수 위에 있어야 합니다.

## SPA 구성 요소 간 정보 공유 {#sharing-information-between-spa-components}

단일 페이지 애플리케이션 내의 구성 요소가 정보를 공유하려면 정기적으로 필요합니다. 다음과 같이 복잡도 순서로 나열하는 몇 가지 권장 방법이 있습니다.

* **옵션 1:** React Context를 사용하여 논리 및 브로드캐스트를 필요한 구성 요소로 중앙 집중화합니다.
* **옵션 2:** Redux와 같은 상태 라이브러리를 사용하여 구성 요소 상태를 공유합니다.
* **옵션 3:** 컨테이너 구성 요소를 사용자 지정하고 확장하여 객체 계층 구조를 활용합니다.

## 다음 단계 {#next-steps}

* [angular을 사용하여 AEM에서 SPA 시작하기](getting-started-angular.md) angular을 사용하여 AEM에서 SPA 편집기로 작동하도록 기본 SPA을 빌드하는 방법을 표시합니다.
* [SPA 편집기 개요](editor-overview.md) AEM과 SPA 간의 통신 모델에 대해 자세히 알아봅니다.
* [WKND SPA 프로젝트](wknd-tutorial.md) 는 AEM에서 간단한 SPA 프로젝트를 구현하는 단계별 자습서입니다.
* [SPA용 동적 모델과 구성 요소 간 매핑](model-to-component-mapping.md) 동적 모델과 구성 요소 간 매핑 및 AEM에서 이 모델이 작동하는 방식을 설명합니다.
* [SPA 블루프린트](blueprint.md) 는 React 또는 Angular 이외의 프레임워크를 위해 AEM에서 SPA을 구현하거나 단순히 더 깊이 이해하고 싶은 경우 AEM용 SPA SDK의 작동 방식을 자세히 살펴봅니다.
