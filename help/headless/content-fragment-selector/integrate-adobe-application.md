---
title: Adobe 애플리케이션과 콘텐츠 조각 선택기 통합
description: 컨텐츠 조각 선택기를 다양한 Adobe 애플리케이션과 통합합니다.
role: Admin, User, Developer
source-git-commit: a16d9e9fa6483a89283c595372abcc437d1d962e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---

# Adobe 애플리케이션과 콘텐츠 조각 선택기 통합 {#integrate-content-fragment-selector-with-adobe-application}

콘텐츠 조각 선택기를 사용하면 다양한 Adobe 애플리케이션과 통합하여 원활하게 함께 작동할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

콘텐츠 조각 선택기를 Adobe 애플리케이션과 통합하는 경우 다음 사전 요구 사항을 사용하십시오.

* [사전 요구 사항](/help/headless/content-fragment-selector/overview.md#prerequisites)
* imsOrg
* imsToken
* apikey

## Adobe 애플리케이션과 콘텐츠 조각 선택기 통합 {#integrate-content-fragment-selector-with-an-adobe-application}

다음 예제에서는 통합 셸에서 Adobe 응용 프로그램을 실행하거나 인증을 위해 이미 `imsToken`이(가) 생성된 경우 콘텐츠 조각 선택기를 사용하는 방법을 보여 줍니다.

아래 예와 같이 `script` 태그를 사용하여 코드에 콘텐츠 조각 선택기 패키지를 포함합니다.

* 스크립트가 로드되면 `PureJSContentFragmentSelectors` 전역 변수를 사용할 수 있습니다.
* 콘텐츠 조각 선택기 [속성](/help/headless/content-fragment-selector/properties.md)을(를) 정의합니다.

   * Adobe 응용 프로그램에서 인증하려면 `imsOrg` 및 `imsToken` 속성이 모두 필요합니다.
   * `handleSelection` 속성은 선택한 조각을 처리하는 데 사용됩니다.

* 콘텐츠 조각 선택기를 렌더링하려면 `renderFragmentSelector` 함수를 호출하십시오.
* 콘텐츠 조각 선택기가 `<div>` 컨테이너 요소에 표시됩니다.

이러한 단계에 따라 Adobe 애플리케이션에서 콘텐츠 조각 선택기를 사용할 수 있습니다.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Fragment Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-fragmentss-selectors/static-fragments/resources/fragments-selectors.js"></script>
    <script>
        // get the container element in which we want to render the FragmentSelector component
        const container = document.getElementById('fragment-selector-container');
        // imsOrg and imsToken are required for authentication in Adobe application
        const fragmentSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (fragmentss: SelectedFragmentType[]) => {},
        };
        // Call the `renderFragmentSelector` available in PureJSContentFragmentSelectors globals to render FragmenttSelector
        PureJSContentFragmentSelectors.renderFragmentSelector(container, fragmentSelectorProps);
    </script>
</head>

<body>
    <div id="fragment-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

### ImsAuthProps {#imsauthprops}

`ImsAuthProps` 속성은 콘텐츠 조각 선택기에서 `imsToken`을(를) 가져오는 데 사용하는 인증 정보 및 흐름을 정의합니다. 이러한 속성을 설정하여 인증 흐름이 작동하는 방식을 제어하고 다양한 인증 이벤트에 대한 리스너를 등록할 수 있습니다.

속성에 대한 자세한 내용은 [ImsAuthProps 속성](/help/headless/content-fragment-selector/properties.md#imsauthprops-properties)을 참조하세요.

### ImsAuthService {#imsauthservice}

`ImsAuthService` 클래스는 조각 선택기의 인증 흐름을 처리합니다. Adobe IMS 인증 서비스에서 `imsToken`을(를) 가져옵니다. `imsToken`은(는) 사용자를 인증하고 AEM as a Cloud Service 저장소에 대한 액세스 권한을 부여하는 데 사용됩니다. `ImsAuthService`은(는) `ImsAuthProps` 속성을 사용하여 인증 흐름을 제어하고 다양한 인증 이벤트에 대한 수신기를 등록합니다. `registerFragmentsSelectorsAuthService` 함수를 사용하여 `ImsAuthService` 인스턴스를 조각 선택기에 등록할 수 있습니다. 다음 함수는 `ImsAuthService` 클래스에서 사용할 수 있습니다. 그러나 `registerFragmentsSelectorsAuthService` 함수를 사용하는 경우에는 이러한 함수를 직접 호출할 필요가 없습니다.

속성에 대한 자세한 내용은 [ImsAuthService 속성](/help/headless/content-fragment-selector/properties.md#imsauthservice-properties)을 참조하세요.

### 입력한 IMS 토큰으로 유효성 검사 {#validation-with-provided-ims-token}

```javascript
<script>
    const apiToken="<valid IMS token>";
    function handleSelection(selection) {
    console.log("Selected fragment: ", selection);
    };
    function renderFragmentSelectorInline() {
    console.log("initializing Fragment Selector");
    const props = {
    "repositoryId": "delivery-p64502-e544757.adobeaemcloud.com",
    "apiKey": "ngdm_test_client",
    "imsOrg": "<IMS org>",
    "imsToken": apiToken,
    handleSelection,
    hideTreeNav: true
    }
    const container = document.getElementById('fragment-selector-container');
    PureJSContentFragmentSelectors.renderFragmentSelector(container, props);
    }
    $(document).ready(function() {
    renderFragmentSelectorInline();
    });
</script>
```

### IMS 서비스에 콜백 등록 {#register-callbacks-to-ims-service}

```java
// object `imsProps` to be defined as below 
let imsProps = {
    imsClientId: <IMS Client Id>,
        imsScope: "openid",
        redirectUrl: window.location.href,
        modalMode: true,
        adobeImsOptions: {
            modalSettings: {
            allowOrigin: window.location.origin,
},
        useLocalStorage: true,
},
onImsServiceInitialized: (service) => {
            console.log("onImsServiceInitialized", service);
},
onAccessTokenReceived: (token) => {
            console.log("onAccessTokenReceived", token);
},
onAccessTokenExpired: () => {
            console.log("onAccessTokenError");
// re-trigger sign-in flow
},
onErrorReceived: (type, msg) => {
            console.log("onErrorReceived", type, msg);
},
}
```
