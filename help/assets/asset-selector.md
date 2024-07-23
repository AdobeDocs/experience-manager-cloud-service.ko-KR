---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 자산 선택기를 사용하여 애플리케이션 내에서 자산의 메타데이터와 렌디션을 검색하고 찾을 수 있습니다.
contentOwner: KK
role: Admin,User
exl-id: 5f962162-ad6f-4888-8b39-bf5632f4f298
source-git-commit: a2646fa72788cb887066751efb171e92b597f4f5
workflow-type: tm+mt
source-wordcount: '4550'
ht-degree: 36%

---

# 마이크로 프론트엔드 자산 선택기 {#Overview}

마이크로 프론트엔드 자산 선택기는 [!DNL Experience Manager Assets] 저장소와 간편하게 통합하는 사용자 인터페이스를 제공하므로 사용자는 해당 저장소에서 사용 가능한 디지털 자산을 탐색 또는 검색하고 애플리케이션 작성 경험에 사용할 수 있습니다.

자산 선택기 패키지를 사용하여 마이크로 프론트엔드 사용자 인터페이스를 애플리케이션 경험에 사용할 수 있습니다. 이렇게 하면 패키지에 대한 모든 업데이트를 자동으로 가져오고 최근 배포된 자산 선택기가 애플리케이션 내에서 자동으로 로드됩니다.

![개요](assets/overview.png)

자산 선택기는 다음과 같은 많은 이점을 제공합니다.

* 바닐라 JavaScript 라이브러리를 사용하여 [Adobe](#asset-selector-ims) 또는 [Adobe 이외](#asset-selector-non-ims) 응용 프로그램과 쉽게 통합할 수 있습니다.
* 자산 선택기 패키지에 대한 업데이트가 애플리케이션에서 사용할 수 있는 자산 선택기에 자동으로 배포되므로 유지 관리가 간편합니다. 최신 수정 사항을 로드하기 위해 애플리케이션 내에서 업데이트를 수행하지 않아도 됩니다.
* 애플리케이션 내에서 자산 선택기 표시를 제어하는 속성을 통해 손쉽게 사용자 정의할 수 있습니다.
* 전체 텍스트 검색, 기본 제공 및 사용자 정의 필터를 통해 작성 경험 내에서 사용할 자산을 빠르게 탐색할 수 있습니다.
* IMS 조직 내에서 저장소를 전환하여 자산을 선택할 수 있습니다.
* 자산을 이름, 차원 및 크기별로 정렬하고 목록 보기, 격자 보기, 갤러리 보기 또는 워터폴 보기로 볼 수 있습니다.

<!--Perform the following tasks to integrate and use Asset Selector with your [!DNL Experience Manager Assets] repository:

1. [Install Asset Selector](#installation)
2. [Integrate Asset Selector using Vanilla JS](#integration-using-vanilla-js)
3. [Use Asset Selector](#using-asset-selector)
-->

<!--
## Setting up Asset Selector {#asset-selector-setup}

![Asset Selector set up](assets/asset-selector-prereqs.png)
-->

## 사전 요구 사항{#prereqs}

다음 통신 방법을 확인해야 합니다.

* 응용 프로그램이 HTTPS에서 실행 중입니다.
* 애플리케이션의 URL은 IMS 클라이언트의 리디렉션 URL 허용 목록에 있습니다.
* 웹 브라우저에서 팝업을 사용하여 IMS 로그인 흐름을 구성하고 렌더링합니다. 따라서 대상 브라우저에서 팝업을 활성화하거나 허용해야 합니다.

자산 선택기의 IMS 인증 워크플로우가 필요한 경우 위의 사전 요구 사항을 사용하십시오. 또는 IMS 워크플로우로 이미 인증한 경우 대신 IMS 정보를 추가할 수 있습니다.

>[!IMPORTANT]
>
> 이 저장소는 Asset Selector를 통합하기 위해 사용 가능한 API 및 사용 예를 설명하는 보조 설명서로서 사용되도록 설계되었습니다. 에셋 선택기를 설치하거나 사용하기 전에 조직에 Experience Manager Assets as a Cloud Service 프로필의 일부로 에셋 선택기에 대한 액세스 권한이 제공되었는지 확인하십시오. 제공되지 않은 경우 이러한 구성 요소를 통합하거나 사용할 수 없습니다. 프로비저닝을 요청하려면 프로그램 관리자가 Admin Console에서 P2로 표시된 지원 티켓을 가져와 다음 정보를 포함해야 합니다.
>
>* 통합 애플리케이션이 호스팅되는 도메인 이름.
>* 프로비저닝 후 조직에 자산 선택기 구성에 필요한 요청된 환경에 해당하는 `imsClientId`, `imsScope` 및 `redirectUrl`이(가) 제공됩니다. 이러한 유효한 속성이 없으면 설치 단계를 실행할 수 없습니다.

## 설치 {#installation}

자산 선택기는 ESM CDN(예: [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/))과 [UMD](https://github.com/umdjs/umd) 버전을 통해 사용할 수 있습니다.

**UMD 버전**&#x200B;을 사용하는 브라우저의 경우(권장됨):

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

**ESM CDN 버전**&#x200B;을 사용하며 `import maps`가 지원되는 브라우저의 경우:

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
</script>
```

**ESM CDN 버전**&#x200B;을 사용하는 Deno/Webpack Module Federation의 경우:

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
```

## Vanilla JS를 사용하여 자산 선택기 통합 {#integration-using-vanilla-js}

[!DNL Adobe] 또는 Adobe이 아닌 응용 프로그램을 [!DNL Experience Manager Assets] 리포지토리와 통합하고 응용 프로그램 내에서 에셋을 선택할 수 있습니다. [다양한 응용 프로그램과 자산 선택기 통합](#asset-selector-integration-with-apps)을 참조하십시오.

이러한 통합은 자산 선택기 패키지를 가져온 다음 Vanilla JavaScript 라이브러리를 사용하여 Assets as a Cloud Service에 연결하여 수행할 수 있습니다. `index.html` 또는 응용 프로그램 내의 적절한 파일을 편집하여 다음 작업을 수행합니다.

* 인증 세부 정보 정의
* Assets as a Cloud Service 저장소 액세스
* 자산 선택기 표시 속성 구성

다음과 같은 경우 일부 IMS 속성을 정의하지 않고 인증을 수행할 수 있습니다.

* [통합 셸](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=ko)에서 [!DNL Adobe] 애플리케이션을 통합하는 경우
* 인증용으로 생성된 IMS 토큰을 이미 보유하고 있는 경우

## 에셋 선택기를 다양한 애플리케이션과 통합 {#asset-selector-integration-with-apps}

에셋 선택기를 다음과 같은 다양한 애플리케이션과 통합할 수 있습니다.

* [자산 선택기를  [!DNL Adobe] 응용 프로그램과 통합](#adobe-app-integration-vanilla)
* [에셋 선택기를 Adobe이 아닌 애플리케이션과 통합](#adobe-non-app-integration)

>[!BEGINTABS]

<!--Integration with an Adobe application content starts here-->

>[!TAB Adobe 응용 프로그램과 통합]

### 사전 요구 사항{#prereqs-adobe-app}

자산 선택기를 [!DNL Adobe] 응용 프로그램과 통합하는 경우 다음 사전 요구 사항을 사용하십시오.

* [커뮤니케이션 방법](#prereqs)
* imsOrg
* imsToken
* apikey

### 자산 선택기를 [!DNL Adobe] 응용 프로그램과 통합 {#adobe-app-integration-vanilla}

다음 예제에서는 Unified Shell에서 [!DNL Adobe] 응용 프로그램을 실행하거나 인증을 위해 이미 `imsToken`을(를) 생성한 경우 자산 선택기를 사용하는 방법을 보여 줍니다.

아래 예제의 _줄 6-15_&#x200B;에 표시된 대로 `script` 태그를 사용하여 코드에 자산 선택기 패키지를 포함하십시오. 스크립트가 로드되면 `PureJSSelectors` 전역 변수를 사용할 수 있습니다. _행 16~23_&#x200B;에 표시된 대로 자산 선택기 [속성](#asset-selector-properties)을(를) 정의합니다. Adobe 응용 프로그램에서 인증하려면 `imsOrg` 및 `imsToken` 속성이 모두 필요합니다. `handleSelection` 속성은 선택한 자산을 처리하는 데 사용됩니다. 자산 선택기를 렌더링하려면 _17행_&#x200B;에서 언급한 대로 `renderAssetSelector` 기능을 호출합니다. _21~22행_&#x200B;에 표시된 대로 `<div>` 컨테이너 요소에 자산 선택기가 표시됩니다.

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

+++**ImsAuthProps**
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

+++

+++**ImsAuthService**
`ImsAuthService` 클래스는 자산 선택기의 인증 흐름을 처리합니다. Adobe IMS 인증 서비스에서 `imsToken`을(를) 가져옵니다. `imsToken`은(는) 사용자를 인증하고 [!DNL Adobe Experience Manager]에 대한 액세스를 [!DNL Cloud Service] Assets 저장소로 승인하는 데 사용됩니다. ImsAuthService는 `ImsAuthProps` 속성을 사용하여 인증 흐름을 제어하고 다양한 인증 이벤트에 대한 수신기를 등록합니다. 편리한 [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) 함수를 사용하여 자산 선택기에 _ImsAuthService_ 인스턴스를 등록할 수 있습니다. 다음 함수는 `ImsAuthService` 클래스에서 사용할 수 있습니다. 그러나 _registerAssetsSelectorsAuthService_ 함수를 사용하는 경우에는 이러한 함수를 직접 호출할 필요가 없습니다.

| 함수 이름 | 설명 |
|---|---|
| `isSignedInUser` | 사용자가 현재 서비스에 로그인되어 있는지 여부를 확인하고 그에 따라 부울 값을 반환합니다. |
| `getImsToken` | 자산 렌디션 생성과 같은 다른 서비스에 대한 요청을 인증하는 데 사용할 수 있는 현재 로그인한 사용자에 대한 인증 `imsToken`을(를) 검색합니다. |
| `signIn` | 사용자의 로그인 프로세스를 시작합니다. 이 함수는 `ImsAuthProps`을(를) 사용하여 팝업 또는 전체 페이지 다시 로드 시 인증을 표시합니다. |
| `signOut` | 사용자를 서비스에서 로그아웃하고 인증 토큰을 무효화하며 보호된 리소스에 액세스하려면 다시 로그인해야 합니다. 이 함수를 호출하면 현재 페이지가 다시 로드됩니다. |
| `refreshToken` | 현재 로그인한 사용자에 대한 인증 토큰을 새로 고침하여 만료되지 않도록 하고 보호된 리소스에 대한 액세스를 중단하지 않도록 합니다. 후속 요청에 사용할 수 있는 새 인증 토큰을 반환합니다. |

+++

+++**제공된 IMS 토큰으로 유효성 검사**

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

+++

+++**IMS 서비스에 콜백 등록**

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

+++

<!--Integration with non-Adobe application content starts here-->

>[!TAB Adobe이 아닌 응용 프로그램과 통합]

<!--### Integrate Asset Selector with a [!DNL non-Adobe] application {#adobe-non-app-integration}-->

### 사전 요구 사항 {#prereqs-non-adobe-app}

에셋 선택기를 Adobe이 아닌 응용 프로그램과 통합하는 경우 다음 사전 요구 사항을 사용하십시오.

* [커뮤니케이션 방법](#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Adobe이 아닌 응용 프로그램과 통합할 때 자산 선택기는 `imsScope` 또는 `imsClientID`과(와) 같은 IMS(Identity Management System) 속성을 사용하여 [!DNL Experience Manager Assets] 리포지토리에 대한 인증을 지원합니다.

+++**Adobe이 아닌 응용 프로그램에 대한 자산 선택기 구성**
Adobe이 아닌 애플리케이션에 대해 에셋 선택기를 구성하려면 먼저 프로비저닝에 대한 지원 티켓을 기록한 후 통합 단계를 수행해야 합니다.

**지원 티켓 로깅**
Admin Console을 통해 지원 티켓을 기록하는 절차:

1. 티켓 제목에 **AEM Assets을 사용하여 자산 선택기**&#x200B;를 추가합니다.

1. 설명에서 다음 세부 정보를 입력해 주십시오.

   * [!DNL Experience Manager Assets]을(를) [!DNL Cloud Service] URL(프로그램 ID 및 환경 ID)로 사용했습니다.
   * Adobe이 아닌 웹 응용 프로그램이 호스팅되는 도메인 이름.
+++

+++**통합 단계**
자산 선택기를 Adobe이 아닌 응용 프로그램과 통합하는 동안 인증에 이 예제 `index.html` 파일을 사용하십시오.

예제 `index.html` 파일의 *행 9*&#x200B;부터 *행 11*&#x200B;까지와 같이 `Script` 태그를 사용하여 자산 선택기 패키지에 액세스합니다.

이 예제의 *줄 14*&#x200B;부터 *줄 38*&#x200B;까지는 `imsClientId`, `imsScope`, `redirectURL`과(와) 같은 IMS 흐름 속성을 설명합니다. 함수에는 `imsClientId` 및 `imsScope` 속성 중 하나 이상을 정의해야 합니다. `redirectURL`에 대한 값을 정의하지 않으면 클라이언트 ID에 대해 등록된 리디렉션 URL이 사용됩니다.

생성된 `imsToken`이(가) 없으므로 예제 `index.html` 파일의 40행~50행에 표시된 대로 `registerAssetsSelectorsAuthService` 및 `renderAssetSelectorWithAuthFlow` 함수를 사용합니다. `renderAssetSelectorWithAuthFlow` 앞에 `registerAssetsSelectorsAuthService` 함수를 사용하여 자산 선택기에 `imsToken`을(를) 등록하십시오. [!DNL Adobe]에서는 구성 요소를 인스턴스화할 때 `registerAssetsSelectorsAuthService`을(를) 호출하는 것이 좋습니다.

예제 `index.html` 파일의 *행 54*&#x200B;부터 *행 60*&#x200B;까지 표시된 대로 `const props` 섹션에서 인증 및 기타 Assets as a Cloud Service 액세스 관련 속성을 정의합니다.

*줄 65*&#x200B;에 언급된 `PureJSSelectors` 전역 변수는 웹 브라우저에서 자산 선택기를 렌더링하는 데 사용됩니다.

*줄 74*&#x200B;부터 *줄 81*&#x200B;까지 언급된 대로 자산 선택기가 `<div>` 컨테이너 요소에 렌더링됩니다. 이 예제에서는 대화 상자를 사용하여 에셋 선택기를 표시합니다.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta charset="utf-8">
    <title>Asset Selectors</title>
    <link rel="stylesheet" href="index.css">
    <script id="asset-selector"
        src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/asset-selectors.js"></script>
    <script>

        const imsProps = {
            imsClientId: "<obtained from IMS team>",
            imsScope: "openid, <other scopes>",
            redirectUrl: window.location.href,
            modalMode: true, // false to open in a full page reload flow
            onImsServiceInitialized: (service) => {
                // invoked when the ims service is initialized and is ready
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

        function load() {
            const registeredTokenService = PureJSSelectors.registerAssetsSelectorsAuthService(imsProps);
            imsInstance = registeredTokenService;
        };

        // initialize the IMS flow before attempting to render the asset selector
        load();
        

        //function that will render the asset selector
            const otherProps = {
            // any other props supported by asset selector
            }
            const assetSelectorProps = {
                "imsOrg": "imsorg",
                ...otherProps
            }
             // container element on which you want to render the AssetSelector/DestinationSelector component
            const container = document.getElementById('asset-selector');

            /// Use the PureJSSelectors in globals to render the AssetSelector/DestinationSelector component
            PureJSSelectors.renderAssetSelectorWithAuthFlow(container, assetSelectorProps, () => {
                const assetSelectorDialog = document.getElementById('asset-selector-dialog');
                assetSelectorDialog.showModal();
            });
        }
    </script>

</head>
<body class="asset-selectors">
    <div>
        <button onclick="renderAssetSelectorWithAuthFlowFlow()">Asset Selector - Select Assets with Ims Flow</button>
    </div>
        <dialog id="asset-selector-dialog">
            <div id="asset-selector" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
            </div>
        </dialog>
    </div>
</body>

</html>
```

+++

+++**게재 리포지토리에 액세스할 수 없음**

>[!TIP]
>
>로그인 워크플로우를 사용하여 자산 선택기를 통합했지만 여전히 게재 저장소에 액세스할 수 없는 경우 브라우저 쿠키가 정리되었는지 확인하십시오. 그렇지 않으면 콘솔에 `invalid_credentials All session cookies are empty` 오류가 발생합니다.

>[!ENDTABS]

## 자산 선택기 속성 {#asset-selector-properties}

자산 선택기 속성을 사용하여 자산 선택기가 렌더링되는 방식을 사용자 정의할 수 있습니다. 다음 표에는 자산 선택기를 사용자 정의하고 사용하는 데 사용할 수 있는 속성이 나열되어 있습니다.

| 속성 | 유형 | 필수 | 기본값 | 설명 |
|---|---|---|---|---|
| *레일* | 부울 | 아니요 | 거짓 | `true`(으)로 표시된 경우 자산 선택기가 왼쪽 레일 보기에서 렌더링됩니다. `false`(으)로 표시되어 있으면 자산 선택기가 모달 보기에서 렌더링됩니다. |
| *imsOrg* | 문자열 | 예 | | 조직에 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]를 프로비저닝하는 중에 할당된 Adobe IMS(Identity Management System)입니다. 액세스 중인 조직이 Adobe IMS에 속해 있는지 여부를 인증하려면 `imsOrg` 키가 필요합니다. |
| *imsToken* | 문자열 | 아니요 | | 인증에 사용되는 IMS 전달자 토큰입니다. 통합을 위해 [!DNL Adobe] 응용 프로그램을 사용하는 경우 `imsToken`이(가) 필요합니다. |
| *apiKey* | 문자열 | 아니요 | | AEM Discovery 서비스에 액세스하는 데 사용되는 API 키입니다. [!DNL Adobe] 응용 프로그램 통합을 사용하는 경우 `apiKey`이(가) 필요합니다. |
| *rootPath* | 문자열 | 아니요 | /content/dam/ | 자산 선택기에 자산이 표시되는 폴더 경로입니다. 캡슐화된 형태로도 `rootPath`를 사용할 수 있습니다. 예를 들어 다음 경로 `/content/dam/marketing/subfolder/`이(가) 주어지면 자산 선택기에서 상위 폴더를 통과할 수 없지만 하위 폴더만 표시합니다. |
| *path* | 문자열 | 아니요 | | 자산 선택기가 렌더링될 때 자산의 특정 디렉터리로 이동하는 데 사용되는 경로입니다. |
| *filterSchema* | 배열 | 아니요 | | 필터 속성을 구성하는 데 사용되는 모델입니다. 자산 선택기에서 특정 필터 옵션을 제한하려는 경우에 유용합니다. |
| *filterFormProps* | 오브젝트 | 아니요 | | 검색을 세분화하는 데 사용해야 하는 필터 속성을 지정합니다. 대상! 예: MIME 유형 JPG, PNG, GIF. |
| *selectedAssets* | 배열 `<Object>` | 아니요 |                 | 자산 선택기가 렌더링될 때 선택된 자산을 지정합니다. 자산의 ID 속성을 포함하는 오브젝트 배열이 필요합니다. 그 예로는 `[{id: 'urn:234}, {id: 'urn:555'}]` 등이 있습니다. 또한 현재 디렉터리에서 자산을 사용할 수 있어야 합니다. 다른 디렉터리를 사용해야 하는 경우 `path` 속성 값도 제공하십시오. |
| *acvConfig* | 오브젝트 | 아니요 | | 기본값을 재정의하기 위한 사용자 지정 구성이 포함된 개체를 포함하는 자산 컬렉션 보기 속성입니다. 또한 이 속성은 `rail` 속성과 함께 사용되어 자산 뷰어의 레일 보기를 사용할 수 있습니다. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | 아니요 |                 | OOTB 번역이 응용 프로그램의 요구 사항에 충분하지 않은 경우 `i18nSymbols` prop을 통해 사용자 지정 지역화된 값을 전달할 수 있는 인터페이스를 표시할 수 있습니다. 이 인터페이스를 통해 값을 전달하면 제공된 기본 번역이 무시되고 대신 자체 번역이 사용됩니다. 재정의를 수행하려면 유효한 재정의하려는 `i18nSymbols`의 키에 [메시지 설명자](https://formatjs.io/docs/react-intl/api/#message-descriptor) 오브젝트를 전달해야 합니다. |
| *intl* | 오브젝트 | 아니요 | | 자산 선택기는 기본 OOTB 번역을 제공합니다. `intl.locale` 속성을 통해 유효한 로케일 문자열을 제공하여 번역 언어를 선택할 수 있습니다. 예를 들어 `intl={{ locale: "es-es" }}`의 경우 </br></br> 지원되는 로케일 문자열은 언어 표준의 이름을 표현하기 위해 [ISO 639 - 코드](https://www.iso.org/iso-639-language-codes.html)를 따릅니다. </br></br> 지원되는 로케일 목록: 영어 - “en-us”(기본값) 스페인어 - “es-es” 독일어 - “de-de” 프랑스어 - “fr-fr” 이탈리아어 - “it-it” 일본어 - “ja-jp” 한국어 - “ko-kr” 포르투갈어 - “pt-br” 중국어(번체) - “zh-cn” 중국어(대만) - “zh-tw” |
| *repositoryId* | 문자열 | 아니요 | &#39;&#39; | 자산 선택기가 콘텐츠를 로드하는 저장소입니다. |
| *additionalAemSolutions* | `Array<string>` | 아니요 | [ ] | 추가 AEM 저장소 목록을 추가할 수 있습니다. 이 속성에 정보를 제공하지 않으면 미디어 라이브러리 또는 AEM Assets 저장소만 고려됩니다. |
| *hideTreeNav* | 부울 | 아니요 |  | 자산 트리 탐색 사이드바를 표시할지 또는 숨길지 지정합니다. 모달 보기에서만 사용되므로 레일 보기에서는 이 속성이 영향을 미치지 않습니다. |
| *onDrop* | 함수 | 아니요 | | 이 속성은 자산의 드롭 기능을 허용합니다. |
| *dropOptions* | `{allowList?: Object}` | 아니요 | | “allowList”를 사용하여 드롭 옵션을 구성합니다. |
| *colorScheme* | 문자열 | 아니요 | | 자산 선택기에 대한 테마를 구성합니다(`light` 또는 `dark`). |
| *handleSelection* | 함수 | 아니요 | | 자산을 선택하고 모달의 `Select` 버튼을 클릭하면 자산 항목 배열과 함께 호출됩니다. 이 함수는 모달 보기에서만 호출됩니다. 레일 보기의 경우 `handleAssetSelection` 또는 `onDrop` 함수를 사용하십시오. 예: <pre>handleSelection=(assets: Asset[])=> {...}</pre> 자세한 내용은 [선택된 자산 유형](#selected-asset-type)을 참조하십시오. |
| *handleAssetSelection* | 함수 | 아니요 | | 자산을 선택하거나 선택 취소할 때 항목 배열과 함께 호출됩니다. 이 속성은 사용자가 자산을 선택할 때 자산을 수신하려는 경우에 유용합니다. 예: <pre>handleSelection=(assets: Asset[])=> {...}</pre> 자세한 내용은 [선택된 자산 유형](#selected-asset-type)을 참조하십시오. |
| *onClose* | 함수 | 아니요 | | 모달 보기에서 `Close` 버튼을 누르면 호출됩니다. 이 속성은 `modal` 보기에서만 호출되며 `rail` 보기에서는 무시됩니다. |
| *onFilterSubmit* | 함수 | 아니요 | | 사용자가 다른 필터 조건을 변경할 때 필터 항목과 함께 호출됩니다. |
| *selectionType* | 문자열 | 아니요 | 미혼 | 한 번에 `single` 자산을 선택할지 또는 `multiple` 자산을 선택할지에 대한 구성입니다. |
| 허용 목록에 추가하다 *dragOptions.drag* | 부울 | 아니요 | | 속성은 선택할 수 없는 에셋의 드래그를 허용하거나 거부하는 데 사용됩니다. |
| *aemTierType* | 문자열 | 아니요 |  | 게재 계층, 작성자 계층 또는 둘 다의 자산을 표시할지 여부를 선택할 수 있습니다. <br><br> 구문: `aemTierType:[0]: "author" 1: "delivery"` <br><br> 예를 들어 `["author","delivery"]`을(를) 모두 사용하는 경우 저장소 전환기에 작성자와 게재 모두에 대한 옵션이 표시됩니다. |
| *handleNavigateToAsset* | 함수 | 아니요 | | 에셋 선택을 처리하는 콜백 함수입니다. |
| *noWrap* | 부울 | 아니요 | | *noWrap* 속성은 측면 레일 패널에서 자산 선택기를 렌더링하는 데 도움이 됩니다. 이 속성이 언급되지 않으면 기본적으로 *대화 상자 보기*&#x200B;가 렌더링됩니다. |
| *dialogSize* | 소형, 중형, 대형, 전체 화면 또는 전체 화면 인계 | 문자열 | 옵션 | 제공된 옵션을 사용하여 크기를 지정하여 레이아웃을 제어할 수 있습니다. |
| *colorScheme* | 밝은 색 또는 어두운 색 | 아니요 | | 이 속성은 자산 선택기 응용 프로그램의 테마를 설정하는 데 사용됩니다. 밝은 테마 또는 어두운 테마 중에서 선택할 수 있습니다. |
| *filterRepoList* | 함수 | 아니요 |  | Experience Manager 저장소를 호출하고 필터링된 저장소 목록을 반환하는 `filterRepoList` 콜백 함수를 사용할 수 있습니다. |
| *getExpiryStatus* | 함수 | 아니요 | | 만료된 에셋의 상태를 제공합니다. 함수는 제공한 에셋의 만료 날짜에 따라 `EXPIRED`, `EXPIRING_SOON` 또는 `NOT_EXPIRED`을(를) 반환합니다. [만료된 에셋 사용자 지정](#customize-expired-assets)을 참조하십시오. |
| *allowSelectionAndDrag* | 부울 | 아니요 | 거짓 | 함수 값은 `true` 또는 `false`일 수 있습니다. 값을 `false`(으)로 설정하면 만료된 에셋을 캔버스에서 선택하거나 드래그할 수 없습니다. |
| *showToast* | | 아니요 | | 이를 통해 에셋 선택기에서 만료된 에셋에 대한 사용자 지정 Toast 메시지를 표시할 수 있습니다. |
<!--
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](#customize-expired-assets). |
-->

## 자산 선택기 속성 사용 예 {#usage-examples}

`index.html` 파일에서 자산 선택기 [속성](#asset-selector-properties)을 정의하여 애플리케이션 내 자산 선택기 표시를 사용자 정의할 수 있습니다.

### 예 1: 레일 보기의 자산 선택기

![레일-보기-예](assets/rail-view-example-vanilla.png)

AssetSelector `rail`의 값이 `false`(으)로 설정되어 있거나 속성에 언급되지 않은 경우 기본적으로 자산 선택기가 모달 보기에 표시됩니다. `acvConfig` 속성은 끌어서 놓기와 같은 일부 심층적인 구성을 허용합니다. `acvConfig` 속성의 사용을 이해하려면 [드래그 앤 드롭을 사용하거나 사용하지 않도록 설정](#enable-disable-drag-and-drop)하세요.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

### 예 2: 메타데이터 팝오버

다양한 속성을 통해 정보 아이콘을 사용하여 보려는 자산의 메타데이터를 정의합니다. 정보 팝오버는 자산의 제목, 차원, 수정일, 위치 및 설명을 포함하여 자산 또는 폴더에 대한 정보 모음을 제공합니다. 아래 예에서는 자산의 메타데이터를 표시하는 데 다양한 속성이 사용됩니다. 예를 들어 `repo:path` 속성은 자산의 위치를 지정합니다. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![메타데이터-팝오버-예](assets/metadata-popover.png)

### 예 3: 레일 보기의 사용자 정의 필터 속성

패싯된 검색 외에도 Assets Selector를 사용하면 [!DNL Adobe Experience Manager]에서 [!DNL Cloud Service] 애플리케이션으로 검색을 구체화하기 위해 다양한 특성을 사용자 지정할 수 있습니다. 다음 코드를 추가하여 애플리케이션에 사용자 지정된 검색 필터를 추가합니다. 아래 예의 이미지, 문서 또는 비디오 중에서 자산 유형을 필터링하는 `Type Filter` 검색 또는 검색을 위해 추가한 필터 유형

![사용자-정의-필터-예-바닐라](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->

## 기능 설정 코드 조각{#code-snippets}

`index.html` 파일 또는 응용 프로그램 구현 내의 유사한 파일에서 필수 구성 요소를 정의하여 [!DNL Experience Manager Assets] 저장소에 액세스하기 위한 인증 세부 정보를 정의합니다. 완료되면 요구 사항에 따라 코드 조각을 추가할 수 있습니다.

### 필터 패널 사용자 지정 {#customize-filter-panel}

`assetSelectorProps` 개체에 다음 코드 조각을 추가하여 필터 패널을 사용자 지정할 수 있습니다.

```
filterSchema: [
    {
    header: 'File Type',
    groupKey: 'TopGroup',
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    {
    label: 'Images',
    value: '<comma separated mimetypes, without space, that denote all images, for e.g., image/>',
    },
    {
    label: 'Videos',
    value: '<comma separated mimetypes, without space, that denote all videos for e.g., video/,model/vnd.mts,application/mxf>'
    }
    ]
    }
    ]
    },
    {
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    { label: 'JPG', value: 'image/jpeg' },
    { label: 'PNG', value: 'image/png' },
    { label: 'TIFF', value: 'image/tiff' },
    { label: 'GIF', value: 'image/gif' },
    { label: 'MP4', value: 'video/mp4' }
    ],
    columns: 3,
    },
    ],
    header: 'Mime Types',
    groupKey: 'MimeTypeGroup',
    }},
    {
    fields: [
    {
    element: 'checkbox',
    name: 'property=metadata.application.xcm:keywords.value',
    options: [
    { label: 'Fruits', value: 'fruits' },
    { label: 'Vegetables', value: 'vegetables'}
    ],
    columns: 3,
    },
    ],
    header: 'Food Category',
    groupKey: 'FoodCategoryGroup',
    }
],
```

### 모달 보기에서 정보 사용자 지정 {#customize-info-in-modal-view}

![정보 아이콘](assets/info-icon.svg) 아이콘을 클릭하면 자산의 세부 정보 보기를 사용자 지정할 수 있습니다. 아래 코드를 실행합니다.

```
// Create an object infoPopoverMap and set the property `infoPopoverMap` with it in assetSelectorProps
const infoPopoverMap = (map) => {
// for example, to skip `path` from the info popover view
let defaultPopoverData = PureJSSelectors.getDefaultInfoPopoverData(map);
return defaultPopoverData.filter((i) => i.label !== 'Path'
};
assetSelectorProps.infoPopoverMap = infoPopoverMap;
```

### 드래그 앤 드롭 모드 활성화 또는 비활성화 {#enable-disable-drag-and-drop}

끌어서 놓기 모드를 사용하려면 `assetSelectorProp`에 다음 속성을 추가하십시오. 끌어서 놓기를 비활성화하려면 `true` 매개 변수를 `false`(으)로 바꾸십시오.

```
rail: true,
acvConfig: {
dragOptions: {
allowList: {
'*': true,
},
},
selectionType: 'multiple'
}

// the drop handler to be implemented
function drop(e) {
e.preventDefault();
// following helps you get the selected assets – an array of objects.
const data = JSON.parse(e.dataTransfer.getData('collectionviewdata'));
}
```

### Assets 선택 {#selection-of-assets}

선택된 자산 유형은 `handleSelection`, `handleAssetSelection` 및 `onDrop` 기능을 사용할 때 자산 정보를 포함하는 오브젝트의 배열입니다.

다음 단계를 실행하여 단일 또는 다중 에셋 선택을 구성합니다.

```
acvConfig: {
selectionType: 'multiple' // 'single' for single selection
}
// the `handleSelection` callback, always gets you the array of selected assets
```

**스키마 구문**

```
interface SelectedAsset {
    'repo:id': string;
    'repo:name': string;
    'repo:path': string;
    'repo:size': number;
    'repo:createdBy': string;
    'repo:createDate': string;
    'repo:modifiedBy': string; 
    'repo:modifyDate': string; 
    'dc:format': string; 
    'tiff:imageWidth': number;
    'tiff:imageLength': number;
    'repo:state': string;
    computedMetadata: Record<string, any>;
    _links: {
        'https://ns.adobe.com/adobecloud/rel/rendition': Array<{
            href: string;
            type: string;
            'repo:size': number;
            width: number;
            height: number;
            [others: string]: any;
        }>;
    };
}
```

다음 표에서는 선택한 자산 오브젝트의 몇 가지 중요한 속성에 대해 설명합니다.

| 속성 | 유형 | 설명 |
|---|---|---|
| *repo:repositoryId* | 문자열 | 자산이 저장된 저장소의 고유 식별자입니다. |
| *repo:id* | 문자열 | 자산의 고유 식별자입니다. |
| *repo:assetClass* | 문자열 | 자산의 분류입니다(예: 이미지 또는 비디오, 문서). |
| *repo:name* | 문자열 | 파일 확장명을 포함한 자산의 이름입니다. |
| *repo:size* | 숫자 | 자산의 크기입니다(바이트). |
| *repo:path* | 문자열 | 저장소 내 자산의 위치입니다. |
| *repo:ancestors* | `Array<string>` | 저장소에 있는 자산의 상위 항목 배열입니다. |
| *repo:state* | 문자열 | 저장소에 있는 에셋의 현재 상태(예: 활성, 삭제됨 등)입니다. |
| *repo:createdBy* | 문자열 | 자산을 생성한 사용자 또는 시스템입니다. |
| *repo:createDate* | 문자열 | 자산이 생성된 날짜 및 시간입니다. |
| *repo:modifiedBy* | 문자열 | 마지막으로 자산을 수정한 사용자 또는 시스템입니다. |
| *repo:modifyDate* | 문자열 | 자산이 마지막으로 수정된 날짜 및 시간입니다. |
| *dc:format* | 문자열 | 파일 유형(예: JPEG, PNG 등)과 같은 에셋의 형식입니다. |
| *tiff:imageWidth* | 숫자 | 자산의 폭입니다. |
| *tiff:imageLength* | 숫자 | 자산의 높이입니다. |
| *computedMetadata* | `Record<string, any>` | 모든 종류의 모든 자산 메타데이터(저장소, 애플리케이션 또는 임베드된 메타데이터)에 대한 버킷을 나타내는 오브젝트입니다. |
| *_links* | `Record<string, any>` | 관련 자산에 대한 하이퍼미디어 링크입니다. 메타데이터 및 렌디션과 같은 리소스에 대한 링크가 포함됩니다. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition>* | `Array<Object>` | 자산의 렌디션에 대한 정보가 포함된 오브젝트 배열입니다. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].href>* | 문자열 | 렌디션에 대한 URI입니다. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].type>* | 문자열 | 렌디션의 MIME 유형입니다. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].repo:size>&#39;* | 숫자 | 렌디션의 크기입니다(바이트). |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].width>* | 숫자 | 렌디션의 폭입니다. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].height>* | 숫자 | 렌디션의 높이입니다. |

<!--For a complete list of properties and detailed example, visit [Asset Selector Code Example](https://github.com/adobe/aem-assets-selectors-mfe-examples).-->

### 만료된 에셋 사용자 지정 {#customize-expired-assets}

에셋 선택기를 사용하여 만료된 에셋의 사용을 제어할 수 있습니다. 현재 날짜로부터 30일 이내에 만료되는 에셋에 대해 미리 알 수 있도록 **곧 만료** 배지로 만료된 에셋을 사용자 지정할 수 있습니다. 또한 이는 요구 사항에 따라 사용자 정의할 수 있습니다. 캔버스에서 만료된 에셋을 선택하거나 그 반대로 할 수도 있습니다. 만료된 에셋의 사용자 지정은 다양한 방법으로 일부 코드 조각을 사용하여 수행할 수 있습니다.

<!--{
    getExpiryStatus: function, // to control Expired/Expiring soon badges of the asset
    allowSelectionAndDrag: boolean, // set true to allow the selection of expired assets on canvas, set false, otherwise.
}-->

```
expiryOptions: {
    getExpiryStatus: getExpiryStatus;
}
```

#### 만료된 에셋 선택 {#selection-of-expired-asset}

만료된 에셋의 사용을 선택 또는 선택 취소하도록 사용자 정의할 수 있습니다. 에셋 선택기 캔버스에서 만료된 에셋을 드래그하여 놓을 것인지 여부를 사용자 정의할 수 있습니다. 이렇게 하려면 다음 매개 변수를 사용하여 캔버스에서 에셋을 선택할 수 없도록 합니다.

```
expiryOptions:{
    allowSelectionAndDrop: false;
}
```
<!--
Additionally, To do this, navigate to **[!UICONTROL Disable default expiry behavior]** under the [!UICONTROL Controls] tab and set the boolean value to `true` or `false` as per the requirement. If `true` is selected, you can see the select box over the expired asset, otherwise it remains unselected. You can hover to the info icon of an asset to know the details of an expired asset. 

![Disable default expiry behavior](assets/disable-default-expiry-behavior.png)-->

#### 만료된 에셋의 기간 설정 중 {#set-duration-of-expired-asset}

다음 코드 스니펫은 다음 5일 이내에 만료되는 자산에 대해 **곧 만료** 배지를 설정하는 데 도움이 됩니다. <!--The `expirationDate` property is used to set the expiration duration of an asset. Refer to the code snippet below:-->

```
/**
  const getExpiryStatus = async (asset) => {
  if (!asset.expirationDate) {
    return null;
  }
  const currentDate = new Date();
  const millisecondsInDay = 1000 * 60 * 60 * 24;
  const fiveDaysFromNow = new Date(value: currentDate.getTime() + 5 * millisecondsInDay);
  const expirationDate = new Date(asset.expirationDate);
  if (expirationDate.getTime() < currentDate.getTime()) {
    return 'EXPIRED';
  } else if (expirationDate.getTime() < fiveDaysFromNow.getTime()) {
    return 'EXPIRING_SOON';
  } else {
    return 'NOT_EXPIRED';
  }
};
```

<!--In the above code snippet, the `getExpiryStatus` function is used to show the **Expiring soon** badge that have expiration date stored in `customExpirationDate`. Additionally, it sets the expiration date of an asset to five days from the current date. The `millisecondsInDay` helps you set expiry of an asset by specifying the time range in milliseconds. You can replace milliseconds with hours directly or customize function as per the requirement. Whereas, the `getTime()` function returns the number of milliseconds for the mentioned date. See [properties](#asset-selector-properties) to know about `expirationDate` property.-->

속성이 현재 날짜 및 시간을 가져오는 데 작동하는 방식을 이해하려면 다음 예를 참조하십시오.

```
const currentData = new Date();
currentData.getTime(),
```

날짜 형식 2024-06-19T06:36:53.959Z에 따른 `1718779013959`을(를) 반환합니다.

#### 만료된 에셋의 Toast 메시지 사용자 지정 {#customize-toast-message}

`showToast` 속성은 만료된 에셋에 표시할 Toast 메시지를 사용자 지정하는 데 사용됩니다.

구문:

```
{
    type: 'ERROR', 'NEUTRAL', 'INFO', 'SUCCESS',
    message: '<message to be shown>',
    timeout: optional,
}
```

기본 시간 제한은 500밀리초입니다. 반면 요구 사항에 따라 수정할 수 있습니다. 또한 값 `timeout: 0`을(를) 전달하면 교차 단추를 클릭할 때까지 toast가 열려 있습니다.

다음은 폴더 선택을 허용하지 않고 해당 메시지를 표시하는 데 필요한 경우 알림 메시지를 표시하는 예제입니다.

```
const showToast = {
    type: 'ERROR',
    message: 'Folder cannot be selected',
    timeout: 5000,
}
```

만료된 에셋 사용에 대한 toast 메시지를 표시하려면 다음 코드 조각을 사용하십시오.

![알림 메시지](assets/toast-message.png)

### 상황별 호출 필터{#contextual-invocation-filter}

자산 선택기를 사용하여 태그 선택기 필터를 추가할 수 있습니다. 모든 관련 태그를 특정 태그 그룹에 결합하는 태그 그룹을 지원합니다. 또한 찾고 있는 자산에 해당하는 추가 태그를 선택할 수 있습니다. 또한 사용자가 주로 사용하는 상황별 호출 필터 아래에 기본 태그 그룹을 설정하여 이동 중에 액세스할 수도 있습니다.

>
>
> * 검색에서 태그 지정 필터를 활성화하려면 상황별 호출 코드 조각을 추가해야 합니다.
> * 태그 그룹 형식 `(property=xcm:keywords.id=)`에 해당하는 이름 속성을 사용해야 합니다.

구문:

```
const filterSchema=useMemo(() => {
    return: [
        {
            element: 'taggroup',
            name: 'property=xcm:keywords.id='
        },
    ];
}, []);
```

필터 패널에서 태그 그룹을 추가하려면 기본적으로 하나 이상의 태그 그룹을 추가해야 합니다. 또한 아래 코드 조각을 사용하여 태그 그룹에서 미리 선택된 기본 태그를 추가하십시오.

```
export const WithAssetTags = (props) = {
const [selectedTags, setSelectedTags] = useState (
new Set(['orientation', 'color', 'facebook', 'experience-fragments:', 'dam', 'monochrome'])
const handleSelectTags = (selected) => {
setSelectedTags (new Set (selected)) ;
};
const filterSchema = useMemo ((); => {
    return {
        schema: [
            ｛
                fields: [
                    {
                    element: 'checkbox', 
                    name: 'property=xcm:keywords=', 
                    defaultValue: Array. from(selectedTags), 
                    options: assetTags, 
                    orientation: 'vertical',
                    },
                ],
    header: 'Asset Tags', 
    groupkey: 'AssetTagsGroup',
        ],
    },
｝；
}, [selectedTags]);
```

![태그 그룹 필터](assets/tag-group.gif)

## 오브젝트 스키마를 사용한 자산 선택 처리 {#handling-selection}

`handleSelection` 속성은 자산 선택기에서 단일 또는 다중 자산 선택을 처리하는 데 사용됩니다. 아래 예는 `handleSelection`의 사용 구문을 나타냅니다.

![선택-처리](assets/handling-selection.png)

## Assets 선택 비활성화 {#disable-selection}

선택 해제 는 에셋 또는 폴더를 선택 가능하도록 숨기거나 비활성화하는 데 사용됩니다. 이 확인란을 선택하면 선택되지 않는 카드나 자산에 선택 확인란이 숨겨집니다. 이 기능을 사용하려면 배열에서 비활성화할 에셋 또는 폴더의 위치를 선언할 수 있습니다. 예를 들어 첫 번째 위치에 나타나는 폴더 선택을 비활성화하려면 다음 코드를 추가할 수 있습니다.
`disableSelection: [0]:folder`

이미지, 폴더, 파일 등의 MIME 형식이나 image/jpeg 등의 기타 MIME 형식 목록이 배열에 제공됩니다. 선언한 MIME 형식은 자산의 `data-card-type` 및 `data-card-mimetype` 특성에 매핑됩니다.

또한 선택 사항이 비활성화된 Assets은 드래그할 수 있습니다. 특정 에셋 유형의 끌어서 놓기를 비활성화하려면 `dragOptions.allowList` 속성을 사용합니다.

선택 사항 비활성화 구문은 다음과 같습니다.

```
(args)=> {
    return(
        <ASDialogWrapper
            {...args}
            disableSelection={args.disableSelection}
            handleAssetSelection={action('handleAssetSelection')}
            handleSelection={action('handleSelection')}
            selectionType={args.selectionType}
        />
    );
}
```

>[!NOTE]
>
> 에셋의 경우 선택 확인란이 숨겨지지만 폴더의 경우 폴더를 선택할 수 없지만 언급된 폴더의 탐색이 여전히 나타납니다.

## 자산 선택기 사용하기 {#using-asset-selector}

자산 선택기를 설정하고 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]와 자산 선택기를 사용하도록 인증되면 자산을 선택하거나 다른 다양한 작업을 수행하여 저장소 내에 있는 자산을 검색할 수 있습니다.

![자산-선택기-사용](assets/using-asset-selector.png)

* **A**: [패널 숨기기/표시](#hide-show-panel)
* **B**: [저장소 전환기](#repository-switcher)
* **C**: [자산](#repository)
* **D**: [필터](#filters)
* **E**: [검색 창](#search-bar)
* **F**: [정렬](#sorting)
* **G**: [오름차순 또는 내림차순으로 정렬](#sorting)
* **H**: [보기](#types-of-view)

### 패널 숨기기/표시 {#hide-show-panel}

왼쪽 탐색 영역에서 폴더를 숨기려면 **[!UICONTROL 폴더 숨기기]** 아이콘을 클릭합니다. 변경 내용을 실행 취소하려면 **[!UICONTROL 폴더 숨기기]** 아이콘을 다시 클릭합니다.

### 저장소 전환기 {#repository-switcher}

또한 에셋 선택기를 사용하여 에셋 선택을 위한 저장소를 전환할 수 있습니다. 왼쪽 패널에 있는 드롭다운에서 원하는 저장소를 선택할 수 있습니다. 드롭다운 목록에서 사용할 수 있는 저장소 옵션은 `index.html` 파일에 정의된 `repositoryId` 속성을 기반으로 하며, 로그인한 사용자가 액세스하는 선택한 IMS 조직의 환경을 기반으로 합니다. 소비자는 기본 `repositoryID`를 전달할 수 있으며 이 경우 자산 선택기는 저장소 전환기 렌더링을 중지하고 주어진 저장소의 자산만 렌더링합니다.

### 자산 저장소

작업을 수행하는 데 사용할 수 있는 자산 폴더 모음입니다.

### 기본 제공 필터 {#filters}

자산 선택기에는 검색 결과를 세분화할 수 있는 기본 필터 옵션도 제공됩니다. 사용 가능한 필터는 다음과 같습니다.

* **[!UICONTROL Status]:**&#x200B;에는 `all`, `approved`, `rejected` 또는 `no status` 중 에셋의 현재 상태가 포함됩니다.
* **[!UICONTROL 파일 형식]:**&#x200B;에 `folder`, `file`, `images`, `documents` 또는 `video`이(가) 포함되어 있습니다.
* **[!UICONTROL 만료 상태]:**&#x200B;에서 만료 기간을 기준으로 자산을 언급합니다. `[!UICONTROL Expired]` 확인란을 선택하여 만료된 에셋을 필터링하거나, 에셋의 `[!UICONTROL Expiration Duration]`을(를) 설정하여 만료 기간에 따라 에셋을 표시할 수 있습니다. 에셋이 이미 만료되었거나 만료될 위기에 처하면 동일한 에셋을 나타내는 배지가 나타납니다. 또한 만료된 에셋을 사용(또는 드래그 앤 드롭)할지 여부를 제어할 수 있습니다. [만료된 에셋 사용자 지정](#customize-expired-assets)에 대해 자세히 알아보세요. 기본적으로 다음 30일 후에 만료되는 자산에 대해 **곧 만료** 배지가 표시됩니다. 그러나 `expirationDate` 속성을 사용하여 만료를 구성할 수 있습니다.

  >[!TIP]
  >
  > 향후 만료 날짜를 기준으로 자산을 보거나 필터링하려면 `[!UICONTROL Expiration Duration]` 필드에 미래 날짜 범위를 언급하십시오. **곧 만료** 배지가 있는 자산이 표시됩니다.

* **[!UICONTROL MIME 형식]:**&#x200B;에 `JPG`, `GIF`, `PPTX`, `PNG`, `MP4`, `DOCX`, `TIFF`, `PDF`, `XLSX`이(가) 포함되어 있습니다.
* **[!UICONTROL 이미지 크기]:**&#x200B;에는 이미지의 최소/최대 너비, 최소/최대 높이가 포함됩니다.

  ![레일-보기-예](assets/filters-asset-selector.png)

### 사용자 정의 검색

전체 텍스트 검색 외에도 에셋 선택기를 사용하여 사용자 지정된 검색을 사용하여 파일 내에서 에셋을 검색할 수 있습니다. 모달 보기 및 레일 보기 모드 모두에서 사용자 정의 검색 필터를 사용할 수 있습니다.

![사용자 정의-검색](assets/custom-search1.png)

자주 검색하는 필드를 저장하고 나중에 사용할 수 있도록 기본 검색 필터를 생성할 수도 있습니다. 자산에 대한 사용자 정의 검색을 만들기 위해 `filterSchema` 속성을 사용할 수 있습니다.

### 검색 창 {#search-bar}

에셋 선택기를 사용하여 선택한 저장소 내의 에셋에 대한 전체 텍스트 검색을 수행할 수 있습니다. 예를 들어 검색 창에 `wave` 키워드를 입력하면 메타데이터 속성에 언급된 것 중 `wave` 키워드가 있는 모든 자산이 표시됩니다.

### 정렬 {#sorting}

자산 선택기에서 자산의 이름, 차원 또는 크기별로 자산을 정렬할 수 있습니다. 자산을 오름차순 또는 내림차순으로 정렬할 수도 있습니다.

### 보기 유형 {#types-of-view}

에셋 선택기를 사용하여 에셋을 다음 네 가지 보기로 볼 수 있습니다.

* **![목록 보기](assets/do-not-localize/list-view.png) [!UICONTROL 목록 보기]** 목록 보기에는 스크롤할 수 있는 파일과 폴더가 한 열에 표시됩니다.
* **![눈금 보기](assets/do-not-localize/grid-view.png) [!UICONTROL 눈금 보기]** 눈금 보기에는 스크롤할 수 있는 파일과 폴더가 행 및 열 눈금에 표시됩니다.
* **![갤러리 보기](assets/do-not-localize/gallery-view.png) [!UICONTROL 갤러리 보기]** 갤러리 보기에는 파일 또는 폴더가 가운데로 잠긴 가로 목록에 표시됩니다.
* **![폭포 보기](assets/do-not-localize/waterfall-view.png) [!UICONTROL 폭포 보기]** 폭포 보기에는 파일 또는 폴더가 Bridge 형태로 표시됩니다.

<!--
### Modes to view Asset Selector

Asset Selector supports two types of out of the box views:

**  Modal view or Inline view:** The modal view or inline view is the default view of Asset Selector that represents Assets folders in the front area. The modal view allows users to view assets in a full screen to ease the selection of multiple assets for import. Use `<AssetSelector rail={false}>` to enable modal view.

    ![modal-view](assets/modal-view.png)

**  Rail view:** The rail view represents Assets folders in a left panel. The drag and drop of assets can be performed in this view. Use `<AssetSelector rail={true}>` to enable rail view.

    ![rail-view](assets/rail-view.png)
-->
<!--

### Application Integration

Asset Selector is flexible and can be integrated within your existing [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application. It is accessible and localized to add, search, and select assets in your application. With Asset Selector you can:
*   **Configure** You can configure the files/folders that you want to show at the upfront. The assets that are chosen to view can be of any supported formats, for example, JPEG. It lets you control the display of various text or symbols as per your choice.
*   **Perfect fit** Asset selector easily fits in your existing [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application and choose the way you want to view. The mode of view can be inline, rail, or modal view.
*   **Accessible** With Asset Selector, you can reach the desired asset in an easy manner.
*   **Localize** Assets can be availed for the various locales available as per Adobe's localization standards.
-->
<!--

### Support for multiple instances

The micro front-end design supports the display of multiple instances of Asset Selector on a single screen.

![multiple-instance](assets/multiple-instance.png)
-->

<!--

### Controlled selection with multi-select

You can make default multi-selection of assets by specifying the assets to the component using `selectedAssets` property. You should specify an array of asset IDs. For example, `[{id: 'urn:234}, {id: 'urn:555'}].`
-->
<!--

### Action buttons

When you customize your application with Asset Selector based on ReactJS, you are provided with the following action buttons to perform various actions:
*   **Open in media library** Lets you open the asset in media library.
*   **Upload** Lets you upload an asset directly.
*   **Download** Downloads the asset in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
-->
<!--

### Status of an asset

Asset Selector lets you know the status of your uploaded assets. The status can be `Approved`, `Rejected`, or `Expired` of the asset. 
-->
<!--

### Localization

The integration of Asset Selector with [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] allows localized content appear in your application.
-->



<!--Best Practice-->
<!--
+++**Control default selection of the filter**
You can make the selection of filter default by implementing the following code snippet:

```
"defaultValue": [
    "image/*",
    "application/*"
],

{
    "label": "Documents",
    "value": "application/*"
}
```

+++
-->
