---
title: AEM-CIF 핵심 구성 요소 및 Adobe Experience Platform 통합
description: CIF - Experience Platform Connector를 사용하여 AEM 렌더링 제품 페이지에서 Experience Platform으로 상점 이벤트 데이터를 보내는 방법을 알아봅니다.
sub-product: Commerce
version: Experience Manager as a Cloud Service
activity: setup
feature: Commerce Integration Framework
topic: Commerce
role: Architect, Developer
level: Beginner
kt: 10834
thumbnail: 346811.jpeg
exl-id: 30bb9b2c-5f00-488e-ad5c-9af7cd2c4735
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 1%

---


# AEM-CIF 핵심 구성 요소 및 Adobe Experience Platform 통합 {#aem-cif-aep-integration}

[Commerce integration framework(CIF)](https://github.com/adobe/aem-core-cif-components) 핵심 구성 요소는 [장바구니에 추가](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-overview.html?lang=ko)와 같은 클라이언트측 상호 작용에서 상점 이벤트 및 해당 데이터를 전달하기 위해 __Adobe Experience Platform__&#x200B;과(와) 매끄럽게 통합됩니다.

[AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components) 프로젝트는 Adobe Commerce 상점 첫 화면에서 이벤트 데이터를 수집할 수 있도록 [Commerce용 Adobe Experience Platform 커넥터](https://github.com/adobe/aem-core-cif-components/tree/master/extensions/experience-platform-connector)라는 JavaScript 라이브러리를 제공합니다. 해당 이벤트 데이터는 Experience Platform으로 전송되어 Adobe Analytics 및 Adobe Target과 같은 다른 Adobe Experience Cloud 제품에서 고객 여정을 다루는 360도 프로필을 빌드하는 데 사용됩니다. Commerce 데이터를 Adobe Experience Cloud의 다른 제품에 연결하면 사이트에서 사용자 행동을 분석하고, AB 테스트를 수행하고, 개인화된 캠페인을 만드는 등의 작업을 수행할 수 있습니다.

클라이언트측 소스에서 고객 경험 데이터를 수집할 수 있는 [Experience Platform 데이터 수집](https://experienceleague.adobe.com/docs/experience-platform/collection/home.html?lang=ko) 기술 제품군에 대해 자세히 알아보십시오.

## `addToCart` 이벤트 데이터를 Experience Platform에 보내기 {#send-addtocart-to-aep}

다음 단계에서는 CIF - Experience Platform 커넥터를 사용하여 AEM 렌더링 제품 페이지에서 Experience Platform으로 `addToCart` 이벤트 데이터를 전송하는 방법을 보여 줍니다. Adobe Experience Platform Debugger 브라우저 확장을 사용하면 제출된 데이터를 테스트하고 검토할 수 있습니다.

![Adobe Experience Platform Debugger에서 addToCart 이벤트 데이터 검토](../assets/aep-integration/EventData-AEM-AEP.png)

## 사전 요구 사항 {#prerequisites}

로컬 개발 환경을 사용하여 이 데모를 완료합니다. 여기에는 Adobe Commerce 인스턴스에 구성 및 연결된 AEM의 실행 중인 인스턴스가 포함됩니다. [AEM as a Cloud Service SDK을 사용하여 로컬 개발을 설정하는 데 필요한 요구 사항과 단계를 검토하십시오.](/help/commerce-cloud/cif-storefront/develop.md)

또한 데이터 수집을 위한 스키마, 데이터 세트 및 데이터 스트림을 만들려면 [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-ui/ui-guide.html?lang=ko)에 대한 액세스 권한과 사용 권한이 필요합니다. 자세한 내용은 [권한 관리](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html?lang=ko)를 참조하십시오.

## AEM Commerce as a Cloud Service 설정 {#aem-setup}

필요한 코드 및 구성을 사용하여 __AEM Commerce as a Cloud Service__ 로컬 환경에서 작업하려면 다음 단계를 완료하십시오.

### 로컬 설정

작동하는 AEM Commerce as a Cloud Service 환경을 만들 수 있도록 [로컬 설정](/help/commerce-cloud/cif-storefront/develop.md#local-setup) 단계를 따르십시오.

### 프로젝트 설정

새 AEM Commerce(CIF) 프로젝트를 만들 수 있도록 [AEM 프로젝트 원형](/help/commerce-cloud/cif-storefront/develop.md#project) 단계를 따르십시오.

>[!TIP]
>
>다음 예제에서 AEM Commerce 프로젝트의 이름은 `My Demo Storefront`이지만 고유한 프로젝트 이름을 선택할 수 있습니다.

![AEM Commerce 프로젝트](../assets/aep-integration/aem-project-with-commerce.png)


프로젝트의 루트 디렉터리에서 다음 명령을 실행하여 만든 AEM Commerce 프로젝트를 로컬 AEM SDK에 빌드하고 배포합니다.

```bash
$ mvn clean install -PautoInstallSinglePackage
```

기본 코드와 콘텐츠를 사용하여 로컬로 배포된 `My Demo StoreFront` 상거래 사이트의 모습은 다음과 같습니다.

![기본 AEM Commerce 사이트](../assets/aep-integration/demo-aem-storefront.png)

### Peregrine 및 CIF-AEP 커넥터 종속성 설치

이 AEM Commerce 사이트의 카테고리 및 제품 페이지에서 이벤트 데이터를 수집하고 전송하려면 주요 `npm` 패키지를 AEM Commerce 프로젝트의 `ui.frontend` 모듈에 설치하십시오.

명령줄에서 다음 명령을 실행하여 `ui.frontend` 모듈로 이동하고 필요한 패키지를 설치합니다.

```bash
npm i --save lodash.get@^4.4.2 lodash.set@^4.3.2
npm i --save apollo-cache-persist@^0.1.1
npm i --save redux-thunk@~2.3.0
npm i --save @adobe/apollo-link-mutation-queue@~1.1.0
npm i --save @magento/peregrine@~12.5.0
npm i --save @adobe/aem-core-cif-react-components --force
npm i --save-dev @magento/babel-preset-peregrine@~1.2.1
npm i --save @adobe/aem-core-cif-experience-platform-connector --force
```

>[!IMPORTANT]
>
>`--force`PWA Studio[이(가) 지원되는 피어 종속으로 제한되어 있으므로 ](https://developer.adobe.com/commerce/pwa-studio/) 인수가 필요한 경우가 있습니다. 일반적으로 이로 인해 문제가 발생하지 않습니다.


### `--force` 인수를 사용하도록 Maven 구성

Maven 빌드 프로세스의 일부로 npm 클린 설치(`npm ci` 사용)가 트리거됩니다. `--force` 인수도 필요합니다.

프로젝트의 루트 POM 파일 `pom.xml`(으)로 이동하여 `<id>npm ci</id>` 실행 블록을 찾습니다. 다음과 같이 보이도록 블록을 업데이트합니다.

```xml
<execution>
    <id>npm ci</id>
    <goals>
    <goal>npm</goal>
    </goals>
    <configuration>
    <arguments>ci --force</arguments>
    </configuration>
</execution>
```

### 바벨 구성 형식 변경

기본 `.babelrc` 파일 상대 구성 파일 형식에서 `babel.config.js` 형식으로 전환합니다. 프로젝트 전체 구성 형식이므로 `node_module`에 플러그인 및 사전 설정을 더 세밀하게 제어할 수 있습니다.

1. `ui.frontend` 모듈로 이동하여 기존 `.babelrc` 파일을 삭제합니다.

1. `babel.config.js` 사전 설정을 사용하는 `peregrine` 파일을 만듭니다.

   ```javascript
   const peregrine = require('@magento/babel-preset-peregrine');
   
   module.exports = (api, opts = {}) => {
       const config = {
           ...peregrine(api, opts),
           sourceType: 'unambiguous'
       } 
   
       config.plugins = config.plugins.filter(plugin => plugin !== 'react-refresh/babel');
   
       return config;
   }
   ```

### Babel을 사용하도록 Webpack 구성

Babel 로더(`babel-loader`) 및 Webpack을 사용하여 JavaScript 파일을 전송하려면 `webpack.common.js` 파일을 편집하십시오.

`ui.frontend` 속성 값 내에 다음 규칙을 포함할 수 있도록 `webpack.common.js` 모듈로 이동하고 `module` 파일을 업데이트합니다.

```javascript
{
    test: /\.jsx?$/,
    exclude: /node_modules\/(?!@magento\/)/,
    loader: 'babel-loader'
}
```

### Apollo 클라이언트 구성

[Apollo Client](https://www.apollographql.com/docs/react/)는 GraphQL을 사용하여 로컬 및 원격 데이터를 모두 관리하는 데 사용됩니다. 또한 GraphQL 쿼리의 결과를 정규화된 로컬 메모리 내 캐시에 저장합니다.

[`InMemoryCache`](https://www.apollographql.com/docs/react/caching/cache-configuration/)이(가) 효과적으로 작동하려면 `possibleTypes.js` 파일이 필요합니다. 이 파일을 생성하려면 [자동으로 가능한 형식 생성](https://www.apollographql.com/docs/react/data/fragments/#generating-possibletypes-automatically)을 참조하세요.

[PWA Studio 참조 구현](https://github.com/magento/pwa-studio/blob/1977f38305ff6c0e2b23a9da7beb0b2f69758bed/packages/pwa-buildpack/lib/Utilities/graphQL.js#L106-L120) 및 [`possibleTypes.js`](../assets/aep-integration/possibleTypes.js) 파일의 예제를 참조하십시오.

1. `ui.frontend` 모듈로 이동하여 파일을 `./src/main/possibleTypes.js`(으)로 저장합니다.

1. 빌드 시간 동안 필요한 정적 변수를 바꿀 수 있도록 `webpack.common.js` 파일의 `DefinePlugin` 섹션을 업데이트합니다.

   ```javascript
   const { DefinePlugin } = require('webpack');
   const { POSSIBLE_TYPES } = require('./src/main/possibleTypes');
   
   ...
   
   plugins: [
       ...
       new DefinePlugin({
           'process.env.USE_STORE_CODE_IN_URL': false,
           POSSIBLE_TYPES
       })
   ]
   ```

### Peregrine 및 CIF 핵심 구성 요소 초기화

React 기반 Peregrine 및 CIF 핵심 구성 요소를 초기화하려면 필요한 구성 및 JavaScript 파일을 만듭니다.

1. `ui.frontend` 모듈로 이동하여 다음 폴더를 만듭니다. `src/main/webpack/components/commerce/App`

1. 다음 내용으로 `config.js` 파일을 만듭니다.

   ```javascript
   // get and parse the CIF store configuration from the <head>
   const storeConfigEl = document.querySelector('meta[name="store-config"]');
   const storeConfig = storeConfigEl ? JSON.parse(storeConfigEl.content) : {};
   
   // the following global variables are needed for some of the peregrine features
   window.STORE_VIEW_CODE = storeConfig.storeView || 'default';
   window.AVAILABLE_STORE_VIEWS = [
       {
           code: window.STORE_VIEW_CODE,
           base_currency_code: 'USD',
           default_display_currency_code: 'USD',
           id: 1,
           locale: 'en',
           secure_base_media_url: '',
           store_name: 'My Demo StoreFront'
       }
   ];
   window.STORE_NAME = window.STORE_VIEW_CODE;
   window.DEFAULT_COUNTRY_CODE = 'en';
   
   export default {
       storeView: window.STORE_VIEW_CODE,
       graphqlEndpoint: storeConfig.graphqlEndpoint,
       // Can be GET or POST. When selecting GET, this applies to cache-able GraphQL query requests only.
       // Mutations will always be executed as POST requests.
       graphqlMethod: storeConfig.graphqlMethod,
       headers: storeConfig.headers,
   
       mountingPoints: {
           // TODO: define the application specific mount points as they may be used by <Portal> and <PortalPlacer>
       },
       pagePaths: {
           // TODO: define the application specific paths/urls as they may be used by the components
           baseUrl: storeConfig.storeRootUrl
       },
       eventsCollector: {
           eventForwarding: {
               acds: true,
               aep: false,
           }
       }
   };
   ```

   >[!IMPORTANT]
   >
   >이미 [`config.js`AEM Guides - CIF Venia 프로젝트](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.frontend/src/main/components/App/config.js)의 ____ 파일을 잘 알고 있을 수 있지만 이 파일에 몇 가지 변경 사항이 있습니다. 먼저 __TODO__ 댓글을 검토하십시오. 그런 다음 `eventsCollector` 속성 내에서 `eventsCollector > aep` 개체를 찾고 `orgId` 및 `datastreamId` 속성을 올바른 값으로 업데이트합니다. [자세히 알아보기.](#add-aep-values-to-aem)

1. 다음 내용으로 `App.js` 파일을 만듭니다. 이 파일은 일반적인 React 애플리케이션 시작 지점 파일과 유사하며 Experience Platform 통합을 용이하게 하기 위해 React 및 사용자 정의 후크와 React Context 사용을 포함합니다.

   ```javascript
   import config from './config';
   
   import React, { useEffect } from 'react';
   import ReactDOM from 'react-dom';
   import { IntlProvider } from 'react-intl';
   import { BrowserRouter as Router } from 'react-router-dom';
   import { combineReducers, createStore } from 'redux';
   import { Provider as ReduxProvider } from 'react-redux';
   import { createHttpLink, ApolloProvider } from '@apollo/client';
   import { ConfigContextProvider, useCustomUrlEvent, useReferrerEvent, usePageEvent, useDataLayerEvents, useAddToCartEvent } from '@adobe/aem-core-cif-react-components';
   import { EventCollectorContextProvider, useEventCollectorContext } from '@adobe/aem-core-cif-experience-platform-connector';
   import { useAdapter } from '@magento/peregrine/lib/talons/Adapter/useAdapter';
   import { customFetchToShrinkQuery } from '@magento/peregrine/lib/Apollo/links';
   import { BrowserPersistence } from '@magento/peregrine/lib/util';
   import { default as PeregrineContextProvider } from '@magento/peregrine/lib/PeregrineContextProvider';
   import { enhancer, reducers } from '@magento/peregrine/lib/store';
   
   const storage = new BrowserPersistence();
   const store = createStore(combineReducers(reducers), enhancer);
   
   storage.setItem('store_view_code', config.storeView);
   
   const App = () => {
       const [{ sdk: mse }] = useEventCollectorContext();
   
       // trigger page-level events
       useCustomUrlEvent({ mse });
       useReferrerEvent({ mse });
       usePageEvent({ mse });
       // listen for add-to-cart events and enable forwarding to the magento storefront events sdk
       useAddToCartEvent(({ mse }));
       // enable CIF specific event forwarding to the Adobe Client Data Layer
       useDataLayerEvents();
   
       useEffect(() => {
           // implement a proper marketing opt-in, for demo purpose you hard-set the consent cookie
           if (document.cookie.indexOf('mg_dnt') < 0) {
               document.cookie += '; mg_dnt=track';
           }
       }, []);
   
       // TODO: use the App to create Portals and PortalPlaceholders to mount the CIF / Peregrine components to the server side rendered markup
       return <></>;
   };
   
   const AppContext = ({ children }) => {
       const { storeView, graphqlEndpoint, graphqlMethod = 'POST', headers = {}, eventsCollector } = config;
       const { apolloProps } = useAdapter({
           apiUrl: new URL(graphqlEndpoint, window.location.origin).toString(),
           configureLinks: (links, apiBase) =>
               // reconfigure the HTTP link to use the configured graphqlEndpoint, graphqlMethod and storeView header
   
               links.set('HTTP', createHttpLink({
                   fetch: customFetchToShrinkQuery,
                   useGETForQueries: graphqlMethod !== 'POST',
                   uri: apiBase,
                   headers: { ...headers, 'Store': storeView }
               }))
       });
   
       return (
           <ApolloProvider {...apolloProps}>
               <IntlProvider locale='en' messages={{}}>
                   <ConfigContextProvider config={config}>
                       <ReduxProvider store={store}>
                           <PeregrineContextProvider>
                               <EventCollectorContextProvider {...eventsCollector}>
                                   {children}
                               </EventCollectorContextProvider>
                           </PeregrineContextProvider>
                       </ReduxProvider>
                   </ConfigContextProvider>
               </IntlProvider>
           </ApolloProvider>
       );
   };
   
   window.onload = async () => {
       const root = document.createElement('div');
       document.body.appendChild(root);
   
       ReactDOM.render(
           <Router>
               <AppContext>
                   <App />
               </AppContext>
           </Router>,
           root
       );
   };
   ```

   `EventCollectorContext`은(는) 다음과 같은 React 컨텍스트를 내보냅니다.

   - commerce-events-sdk 및 commerce-events-collector 라이브러리,
   - 는 Experience Platform 및/또는 ACDS에 대한 주어진 구성으로 초기화합니다.
   - Peregrine에서 모든 이벤트를 구독하고 이벤트 SDK으로 전달합니다.

   `EventCollectorContext`의 구현 세부 정보를 검토할 수 있습니다. GitHub에서 [aem-core-cif-components를 참조하십시오.](https://github.com/adobe/aem-core-cif-components/blob/3d4e44d81fff2f398fd2376d24f7b7019f20b31b/extensions/experience-platform-connector/src/events-collector/EventCollectorContext.js)

### 업데이트된 AEM 프로젝트 빌드 및 배포 {#build-and-deploy}

위의 패키지 설치, 코드 및 구성 변경 내용이 올바른지 확인하려면 다음 Maven 명령을 사용하여 업데이트된 AEM Commerce 프로젝트를 다시 빌드하고 배포하십시오. `$ mvn clean install -PautoInstallSinglePackage`.

## Experience Platform 설정 {#aep-setup}

카테고리 및 제품과 같은 AEM Commerce 페이지에서 오는 이벤트 데이터를 수신하고 저장하려면 다음 단계를 완료하십시오.

>[!AVAILABILITY]
>
>__Adobe Experience Platform__ 및 __Adobe Experience Platform 데이터 수집__&#x200B;에서 올바른 __제품 프로필__&#x200B;에 속해 있는지 확인하십시오. 필요한 경우 시스템 관리자와 함께 __Admin Console에서__&#x200B;제품 프로필[을 만들거나 업데이트하거나 할당하십시오.](https://adminconsole.adobe.com/)

### Commerce 필드 그룹으로 스키마 만들기 {#create-schema}

상거래 이벤트 데이터의 구조를 정의하려면 경험 데이터 모델(XDM) 스키마를 만들어야 합니다. 스키마는 데이터의 구조와 형식을 나타내고 유효성을 검사하는 규칙 세트입니다.

1. 브라우저에서 __Adobe Experience Platform__ 제품 홈 페이지로 이동합니다. 예: <https://experience.adobe.com/#/@YOUR-ORG-NAME/sname:prod/platform/home>

1. 왼쪽 탐색 섹션에서 __스키마__ 메뉴를 찾은 다음 오른쪽 상단에서 __스키마 만들기__ 단추를 클릭하고 __XDM ExperienceEvent__&#x200B;을(를) 선택합니다.

   ![AEP 스키마 만들기](../assets/aep-integration/AEP-Schema-EventSchema-1.png)

1. __스키마 속성 > 표시 이름__ 필드를 사용하여 스키마 이름을 지정하고 __구성 > 필드 그룹 > 추가__ 단추를 사용하여 필드 그룹을 추가하십시오.

   ![AEP 스키마 정의](../assets/aep-integration/AEP-Schema-Definition.png)

1. __필드 그룹 추가__ 대화 상자에서 `Commerce`을(를) 검색하고 __Commerce 세부 정보__ 확인란을 선택한 다음 __필드 그룹 추가__&#x200B;를 클릭합니다.

   ![AEP 스키마 정의](../assets/aep-integration/AEP-Schema-Field-Group.png)


>[!TIP]
>
>자세한 내용은 [스키마 컴포지션의 기본 사항](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=ko)을 참조하십시오.

### 데이터 세트 만들기 {#create-dataset}

이벤트 데이터를 저장하려면 스키마 정의를 준수하는 데이터 세트를 만들어야 합니다. 데이터 집합은 스키마(열) 및 필드(행)를 포함하는 데이터 수집을 위한 저장소 및 관리 구성입니다.

1. 브라우저에서 __Adobe Experience Platform__ 제품 홈 페이지로 이동합니다. 예: <https://experience.adobe.com/#/@YOUR-ORG-NAME/sname:prod/platform/home>

1. 왼쪽 탐색 섹션에서 __데이터 세트__ 메뉴를 찾은 다음 오른쪽 상단에서 __데이터 세트 만들기__ 단추를 클릭합니다.

   ![AEP 데이터 세트 만들기](../assets/aep-integration/AEP-Datasets-Create.png)

1. 새 페이지에서 __스키마에서 데이터 집합 만들기__ 카드를 선택합니다.

   ![AEP 데이터 세트 스키마 만들기 옵션](../assets/aep-integration/AEP-Datasets-Schema-Option.png)

   새 페이지에서 이전 단계에서 만든 스키마를 __검색 및 선택__&#x200B;하고 __다음__ 단추를 클릭합니다.

   ![AEP 데이터 세트 만들기 스키마 선택](../assets/aep-integration/AEP-Datasets-Select-Schema.png)

1. __데이터 집합 구성 > 이름__ 필드를 사용하여 데이터 집합 이름을 지정하고 __완료__ 단추를 클릭합니다.

   ![AEP 데이터 세트 이름 만들기](../assets/aep-integration/AEP-Datasets-Name.png)

>[!TIP]
>
>자세한 내용은 [데이터 세트 개요](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=ko)를 참조하십시오.


### 데이터 스트림 만들기 {#create-datastream}

Experience Platform에서 데이터 스트림을 만들 수 있도록 다음 단계를 완료합니다.

1. 브라우저에서 __Adobe Experience Platform__ 제품 홈 페이지로 이동합니다. 예: <https://experience.adobe.com/#/@YOUR-ORG-NAME/sname:prod/platform/home>

1. 왼쪽 탐색 섹션에서 __데이터스트림__ 메뉴를 찾은 다음 오른쪽 상단에서 __새 데이터스트림__ 단추를 클릭합니다.

   ![AEP 데이터 스트림 만들기](../assets/aep-integration/AEP-Datastream-Create.png)

1. __이름__ 필수 필드를 사용하여 데이터스트림의 이름을 지정합니다. __이벤트 스키마__ 필드에서 만든 스키마를 선택하고 __저장__&#x200B;을 클릭합니다.

   ![AEP 데이터 스트림 정의](../assets/aep-integration/AEP-Datastream-Define.png)

1. 만든 데이터 스트림을 열고 __서비스 추가__&#x200B;를 클릭합니다.

   ![AEP 데이터스트림 추가 서비스](../assets/aep-integration/AEP-Datastream-Add-Service.png)

1. __서비스__ 필드에서 __Adobe Experience Platform__ 옵션을 선택합니다. __이벤트 데이터 세트__ 필드에서 이전 단계의 데이터 세트 이름을 선택하고 __저장__&#x200B;을 클릭합니다.

   ![AEP 데이터스트림 추가 서비스 세부 정보](../assets/aep-integration/AEP-Datastream-Add-Service-Define.png)

>[!TIP]
>
>자세한 내용은 [데이터스트림 개요](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=ko)를 참조하세요.

## AEM Commerce 구성에 데이터스트림 값 추가 {#add-aep-values-to-aem}

위의 Experience Platform 설정을 완료한 후에는 데이터 스트림 세부 정보의 왼쪽 레일에 `datastreamId`이(가) 있고 `orgId`프로필 사진 > 계정 정보 > 사용자 정보&#x200B;__모달의 오른쪽 상단 모서리에__&#x200B;이(가) 있어야 합니다.

![AEP 데이터스트림 ID](../assets/aep-integration/AEP-Datastream-ID.png)

1. AEM Commerce 프로젝트의 `ui.frontend` 모듈에서 `config.js` 파일, 특히 `eventsCollector > aep` 개체 속성을 업데이트합니다.

1. 업데이트된 AEM Commerce 프로젝트 빌드 및 배포


## `addToCart` 이벤트 트리거 및 데이터 수집 확인 {#event-trigger-verify}

위의 단계에서 AEM Commerce 및 Experience Platform 설정을 완료합니다. 이제 제품 UI에서 Google Chrome 확장 `addToCart`Snowploy Inspector _및 데이터 세트_&#x200B;지표 및 그래프&#x200B;__토글을 사용하여__ 이벤트를 트리거하고 데이터 수집을 확인할 수 있습니다.

이벤트를 트리거하려면 로컬 설정에서 AEM 작성자 또는 게시 서비스를 사용할 수 있습니다. 이 예에서는 계정에 로그인하여 AEM 작성자를 사용하십시오.

1. 사이트 페이지에서 __내 데모 StoreFront > us > en__ 페이지를 선택하고 상단 작업 표시줄의 __편집__&#x200B;을 클릭합니다.

1. 맨 위 작업 표시줄에서 __게시됨으로 보기__&#x200B;를 클릭한 다음 상점 탐색에서 원하는 범주를 클릭합니다.

1. __제품 페이지__&#x200B;에서 원하는 제품 카드를 클릭한 다음 __색상, 크기__&#x200B;을(를) 선택하여 __장바구니에 추가__ 단추를 사용하도록 설정합니다.

1. 브라우저의 확장 패널에서 __Snowploy Inspector__ 확장을 열고 왼쪽 레일에서 __Experience Platform Wed SDK__&#x200B;를 선택합니다.

1. __제품 페이지__(으)로 돌아가서 __장바구니에 추가__ 단추를 클릭하십시오. 이렇게 하면 Experience Platform으로 데이터가 전송됩니다. __Adobe Experience Platform Debugger__ 확장에 이벤트 세부 정보가 표시됩니다.

   ![AEP Debugger 추가 장바구니 이벤트 데이터](../assets/aep-integration/AEP-Debugger-AddToCart-EventData.png)

1. Experience Platform 제품 UI 내에서 __데이터 세트 활동__ 탭의 __데이터 세트 > 내 데모 StoreFront__(으)로 이동합니다. __지표 및 그래프__&#x200B;가 활성화되면 이벤트 데이터 통계가 표시됩니다.

   ![Experience Platform 데이터 세트 데이터 통계](../assets/aep-integration/AEP-Dataset-AddToCart-EventData.png)

## 구현 세부 사항 {#implementation-details}

[CIF Experience Platform 커넥터](https://github.com/adobe/aem-core-cif-components/tree/master/extensions/experience-platform-connector)는 [PWA Studio](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html) 프로젝트의 일부인 [Adobe Commerce용 데이터 연결](https://developer.adobe.com/commerce/pwa-studio/)의 맨 위에 만들어집니다.

PWA Studio 프로젝트를 사용하면 Adobe Commerce 또는 Magento Open Source에서 제공하는 Progressive Web Application(PWA) 상점 전면을 만들 수 있습니다. 프로젝트에 시각적 구성 요소에 논리를 추가하기 위한 [Peregrin](https://developer.adobe.com/commerce/pwa-studio/api/peregrine/)이라는 구성 요소 라이브러리도 포함되어 있습니다. [Peregrin 라이브러리](https://developer.adobe.com/commerce/pwa-studio/api/peregrine/)는 또한 [CIF Experience Platform 커넥터](https://github.com/adobe/aem-core-cif-components/tree/master/extensions/experience-platform-connector)에서 Experience Platform과 원활하게 통합하기 위해 사용하는 사용자 지정 React 후크를 제공합니다.

## 지원되는 이벤트 {#supported-events}

현재 지원되는 이벤트는 다음과 같습니다.

__Experience XDM 이벤트&#x200B;:__

1. 장바구니에 추가(AEM)
1. 페이지 보기(AEM)
1. 제품 보기(AEM)
1. 검색 요청 전송됨(AEM)
1. 검색 응답 수신됨(AEM)

[Peregrine 구성 요소](https://developer.adobe.com/commerce/pwa-studio/guides/packages/peregrine/)가 AEM Commerce 프로젝트에서 재사용되는 경우:

__Experience XDM 이벤트&#x200B;:__

1. 장바구니에서 제거
1. 장바구니 열기
1. 장바구니 보기
1. 즉시 구매
1. 체크아웃 시작
1. 체크아웃 완료

__프로필 XDM 이벤트&#x200B;:__

1. 로그인
1. 계정 만들기
1. 계정 편집

## 추가 리소스 {#additional-resources}

자세한 내용은 다음 리소스를 참조하십시오.

- [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/)
- [[!DNL Data Connection] 개요](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html?lang=ko)
- [[!DNL Data Connection] 이벤트](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html?lang=ko)
- [Adobe Experience Platform 개요](https://experienceleague.adobe.com/docs/experience-platform/landing/home.html?lang=ko)
