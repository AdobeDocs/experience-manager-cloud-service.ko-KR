---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 에셋 선택기를 다양한 Adobe, 비Adobe 및 타사 애플리케이션과 통합합니다.
role: Admin, User
exl-id: a0c030e2-2213-406b-ad92-4761f1e2ee9f
source-git-commit: f9f5b2a25933e059cceacf2ba69e23d528858d4b
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 8%

---

# 에셋 선택기와 Adobe 애플리케이션 통합 {#integrate-asset-selector-with-adobe-app}

에셋 선택기를 사용하면 다양한 Adobe 애플리케이션을 사용하여 를 통합하여 두 애플리케이션이 원활하게 함께 작동할 수 있습니다.

## 사전 요구 사항{#prereqs-adobe-app}

자산 선택기를 [!DNL Adobe] 응용 프로그램과 통합하는 경우 다음 사전 요구 사항을 사용하십시오.

* [커뮤니케이션 방법](/help/assets/overview-asset-selector.md#prereqs)
* imsOrg
* imsToken
* apikey

## 자산 선택기를 [!DNL Adobe] 응용 프로그램과 통합 {#adobe-app-integration-vanilla}

다음 예제에서는 Unified Shell에서 [!DNL Adobe] 응용 프로그램을 실행하거나 인증을 위해 이미 `imsToken`을(를) 생성한 경우 자산 선택기를 사용하는 방법을 보여 줍니다.

아래 예제의 _줄 6-15_&#x200B;에 표시된 대로 `script` 태그를 사용하여 코드에 자산 선택기 패키지를 포함하십시오. 스크립트가 로드되면 `PureJSSelectors` 전역 변수를 사용할 수 있습니다. _행 16~23_&#x200B;에 표시된 대로 자산 선택기 [속성](/help/assets/asset-selector-properties.md)을(를) 정의합니다. Adobe 응용 프로그램에서 인증하려면 `imsOrg` 및 `imsToken` 속성이 모두 필요합니다. `handleSelection` 속성은 선택한 자산을 처리하는 데 사용됩니다. 자산 선택기를 렌더링하려면 _17행_&#x200B;에서 언급한 대로 `renderAssetSelector` 기능을 호출합니다. _21~22행_&#x200B;에 표시된 대로 `<div>` 컨테이너 요소에 자산 선택기가 표시됩니다.

다음 단계를 따라 [!DNL Adobe] 응용 프로그램에서 자산 선택기를 사용할 수 있습니다.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Asset Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>
    <script>
        // get the container element in which we want to render the AssetSelector component
        const container = document.getElementById('asset-selector-container');
        // imsOrg and imsToken are required for authentication in Adobe application
        const assetSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (assets: SelectedAssetType[]) => {},
        };
        // Call the `renderAssetSelector` available in PureJSSelectors globals to render AssetSelector
        PureJSSelectors.renderAssetSelector(container, assetSelectorProps);
    </script>
</head>

<body>
    <div id="asset-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

<!--For detailed example, visit [Asset Selector Code Example](https://github.com/adobe/aem-assets-selectors-mfe-examples).-->

### ImsAuthProps {#ims-auth-props}

`ImsAuthProps` 속성은 자산 선택기에서 `imsToken`을(를) 가져오는 데 사용하는 인증 정보 및 흐름을 정의합니다. 이러한 속성을 설정하여 인증 플로우의 동작 방법을 제어하고 다양한 인증 이벤트에 대한 리스너를 등록할 수 있습니다.

| 속성 이름 | 설명 |
|---|---|
| `imsClientId` | 인증 용도로 사용되는 IMS 클라이언트 ID를 나타내는 문자열 값입니다. 이 값은 Adobe에서 제공하며 Adobe AEM CS 조직에만 해당됩니다. |
| `imsScope` | 인증에 사용되는 범위를 설명합니다. 범위는 응용 프로그램이 조직 리소스에 대해 갖는 액세스 수준을 결정합니다. 여러 범위는 쉼표로 구분할 수 있습니다. |
| `redirectUrl` | 인증 후 사용자가 리디렉션되는 URL을 나타냅니다. 이 값은 일반적으로 애플리케이션의 현재 URL로 설정됩니다. `redirectUrl`이(가) 제공되지 않으면 `ImsAuthService`에서 `imsClientId`을(를) 등록하는 데 사용되는 redirectUrl을 사용합니다. |
| `modalMode` | 인증 흐름을 모달(팝업)로 표시할지 여부를 나타내는 부울. `true`(으)로 설정하면 인증 흐름이 팝업에 표시됩니다. `false`(으)로 설정하면 전체 페이지를 다시 로드할 때 인증 흐름이 표시됩니다. _참고:_ 더 나은 UX를 위해 사용자에게 브라우저 팝업이 비활성화된 경우 이 값을 동적으로 제어할 수 있습니다. |
| `onImsServiceInitialized` | Adobe IMS 인증 서비스가 초기화될 때 호출되는 콜백 함수입니다. 이 함수는 Adobe IMS 서비스를 나타내는 개체인 `service` 매개 변수 하나를 사용합니다. 자세한 내용은 [`ImsAuthService`](#imsauthservice-ims-auth-service)을(를) 참조하십시오. |
| `onAccessTokenReceived` | Adobe IMS 인증 서비스에서 `imsToken`을(를) 받을 때 호출되는 콜백 함수입니다. 이 함수는 액세스 토큰을 나타내는 문자열인 `imsToken` 매개 변수 하나를 사용합니다. |
| `onAccessTokenExpired` | 액세스 토큰이 만료된 경우 호출되는 콜백 함수입니다. 이 함수는 일반적으로 새 액세스 토큰을 얻기 위해 새 인증 흐름을 트리거하는 데 사용됩니다. |
| `onErrorReceived` | 인증 중에 오류가 발생할 때 호출되는 콜백 함수입니다. 이 함수는 오류 유형과 오류 메시지의 두 매개 변수를 사용합니다. 오류 유형은 오류의 유형을 나타내는 문자열이고, 오류 메시지는 오류 메시지를 나타내는 문자열이다. |

### ImsAuthService {#ims-auth-service}

`ImsAuthService` 클래스는 자산 선택기의 인증 흐름을 처리합니다. Adobe IMS 인증 서비스에서 `imsToken`을(를) 가져옵니다. `imsToken`은(는) 사용자를 인증하고 [!DNL Adobe Experience Manager]에 대한 액세스를 [!DNL Cloud Service] Assets 저장소로 승인하는 데 사용됩니다. ImsAuthService는 `ImsAuthProps` 속성을 사용하여 인증 흐름을 제어하고 다양한 인증 이벤트에 대한 수신기를 등록합니다. 편리한 [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) 함수를 사용하여 자산 선택기에 _ImsAuthService_ 인스턴스를 등록할 수 있습니다. 다음 함수는 `ImsAuthService` 클래스에서 사용할 수 있습니다. 그러나 _registerAssetsSelectorsAuthService_ 함수를 사용하는 경우에는 이러한 함수를 직접 호출할 필요가 없습니다.

| 함수 이름 | 설명 |
|---|---|
| `isSignedInUser` | 사용자가 현재 서비스에 로그인되어 있는지 여부를 확인하고 그에 따라 부울 값을 반환합니다. |
| `getImsToken` | 자산 렌디션 생성과 같은 다른 서비스에 대한 요청을 인증하는 데 사용할 수 있는 현재 로그인한 사용자에 대한 인증 `imsToken`을(를) 검색합니다. |
| `signIn` | 사용자의 로그인 프로세스를 시작합니다. 이 함수는 `ImsAuthProps`을(를) 사용하여 팝업 또는 전체 페이지 다시 로드 시 인증을 표시합니다. |
| `signOut` | 사용자를 서비스에서 로그아웃하고 인증 토큰을 무효화하며 보호된 리소스에 액세스하려면 다시 로그인해야 합니다. 이 함수를 호출하면 현재 페이지가 다시 로드됩니다. |
| `refreshToken` | 현재 로그인한 사용자에 대한 인증 토큰을 새로 고침하여 만료되지 않도록 하고 보호된 리소스에 대한 액세스를 중단하지 않도록 합니다. 후속 요청에 사용할 수 있는 새 인증 토큰을 반환합니다. |

### 입력한 IMS 토큰으로 유효성 검사 {#validation-ims-token}

```
<script>
    const apiToken="<valid IMS token>";
    function handleSelection(selection) {
    console.log("Selected asset: ", selection);
    };
    function renderAssetSelectorInline() {
    console.log("initializing Asset Selector");
    const props = {
    "repositoryId": "delivery-p64502-e544757.adobeaemcloud.com",
    "apiKey": "ngdm_test_client",
    "imsOrg": "<IMS org>",
    "imsToken": apiToken,
    handleSelection,
    hideTreeNav: true
    }
    const container = document.getElementById('asset-selector-container');
    PureJSSelectors.renderAssetSelector(container, props);
    }
    $(document).ready(function() {
    renderAssetSelectorInline();
    });
</script>
```

### IMS 서비스에 콜백 등록 {#register-callback-ims-service}

```
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

>[!MORELIKETHIS]
>
>* [다양한 응용 프로그램과 자산 선택기 통합](/help/assets/integrate-asset-selector.md)
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [자산 선택기 Dynamic Media Open API 통합](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [자산 선택기 사용자 지정](/help/assets/asset-selector-customization.md)
