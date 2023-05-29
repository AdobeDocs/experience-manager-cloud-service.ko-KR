---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 자산 선택기를 사용하여 애플리케이션 내에서 자산의 메타데이터와 렌디션을 검색하고 찾을 수 있습니다.
contentOwner: Adobe
role: Admin,User
source-git-commit: af36101d8fecd7fab2300f93d40bba4c92f8eafe
workflow-type: ht
source-wordcount: '2378'
ht-degree: 100%

---


# 마이크로 프론트엔드 자산 선택기 {#Overview}

마이크로 프론트엔드 자산 선택기는 [!DNL Experience Manager Assets as a Cloud Service] 저장소와 간편하게 통합하는 사용자 인터페이스를 제공하므로 사용자는 해당 저장소에서 사용 가능한 디지털 자산을 탐색 또는 검색하고 애플리케이션 작성 경험에 사용할 수 있습니다.

자산 선택기 패키지를 사용하여 마이크로 프론트엔드 사용자 인터페이스를 애플리케이션 경험에 사용할 수 있습니다. 이렇게 하면 패키지에 대한 모든 업데이트를 자동으로 가져오고 최근 배포된 자산 선택기가 애플리케이션 내에서 자동으로 로드됩니다.

![개요](assets/overview.png)

자산 선택기는 다음과 같은 많은 이점을 제공합니다.

* Vanilla JavaScript 라이브러리를 사용하여 Adobe 애플리케이션 또는 Adobe 이외의 애플리케이션과 쉽게 통합할 수 있습니다.
* 자산 선택기 패키지에 대한 업데이트가 애플리케이션에서 사용할 수 있는 자산 선택기에 자동으로 배포되므로 유지 관리가 간편합니다. 최신 수정 사항을 로드하기 위해 애플리케이션 내에서 업데이트를 수행하지 않아도 됩니다.
* 애플리케이션 내에서 자산 선택기 표시를 제어하는 속성을 통해 손쉽게 사용자 정의할 수 있습니다.

* 전체 텍스트 검색, 기본 제공 및 사용자 정의 필터를 통해 작성 경험 내에서 사용할 자산을 빠르게 탐색할 수 있습니다.

* IMS 조직 내에서 저장소를 전환하여 자산을 선택할 수 있습니다.

* 자산을 이름, 차원 및 크기별로 정렬하고 목록 보기, 격자 보기, 갤러리 보기 또는 워터폴 보기로 볼 수 있습니다.

이 문서는 통합 셸에서 [!DNL Adobe] 애플리케이션과 함께 자산 선택기를 사용하는 방법과 인증용으로 생성된 imsToken을 이미 보유한 경우에 대해 다룹니다. 이 문서에서는 이러한 워크플로를 SUSI 외 흐름이라고 합니다.

[!DNL Experience Manager Assets as a Cloud Service] 저장소와 자산 선택기를 통합하고 사용하려면 다음 작업을 수행하십시오.

* [Vanilla JS를 사용하여 자산 선택기 통합](#integration-with-vanilla-js)
* [자산 선택기 표시 속성 정의](#asset-selector-properties)
* [자산 선택기 사용](#using-asset-selector)

## Vanilla JS를 사용하여 자산 선택기 통합 {#integration-with-vanilla-js}

모든 [!DNL Adobe] 또는 Adobe 이외의 애플리케이션을 [!DNL Experience Manager Assets] as a [!DNL Cloud Service] 저장소와 통합하고 애플리케이션 내에서 자산을 선택할 수 있습니다.

이러한 통합은 자산 선택기 패키지를 가져온 다음 Vanilla JavaScript 라이브러리를 사용하여 Assets as a Cloud Service에 연결하여 수행할 수 있습니다. `index.html` 또는 애플리케이션 내의 적절한 파일을 편집하여 다음 작업을 수행해야 합니다.
* 인증 세부 정보 정의
* Assets as a Cloud Service 저장소 액세스
* 자산 선택기 표시 속성 구성

<!--
Asset Selector supports authentication to the [!DNL Experience Manager Assets] as a [!DNL Cloud Service] repository using Identity Management System (IMS) properties such as `imsScope` or `imsClientID`. Authentication using these IMS properties is referred to as SUSI (Sign Up Sign In) flow in this article.

You can perform authentication without defining some of the IMS properties, such as `imsScope` or `imsClientID`, if:

*   You are integrating an [!DNL Adobe] application on [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=en).
*   You already have an IMS token generated for authentication.

Accessing [!DNL Experience Manager Assets] as a [!DNL Cloud Service] repository without defining `imsScope` or `imsClientID` IMS properties is referred to as a non-SUSI flow in this article.
-->

다음과 같은 경우 일부 IMS 속성을 정의하지 않고 인증을 수행할 수 있습니다.

* [통합 셸](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=ko)에서 [!DNL Adobe] 애플리케이션을 통합하는 경우
* 인증용으로 생성된 IMS 토큰을 이미 보유하고 있는 경우

## 사전 요구 사항 {#prerequisites}

<!--
If your application requires user based authentication, out-of-the-box Asset Selector also supports a flow for authentication to the [!DNL Experience Manager Assets] as a [!DNL Cloud Service] repository using Identity Management System (IMS.)

You can use properties such as `imsScope` or `imsClientID` to retrieve `imsToken` automatically. You can use SUSI (Sign Up Sign In) flow and IMS properties. Also, you can obtain your own imsToken and pass it to Asset Selector by integrating within [!DNL Adobe] application on Unified Shell or if you already have an imsToken obtained via other methods (for example, using technical account). Accessing [!DNL Experience Manager Assets] as a [!DNL Cloud Service] repository without defining IMS properties (For example, `imsScope` and `imsClientID`) is referred to as a non-SUSI flow.
-->

`index.html` 파일 또는 애플리케이션 구현 내에 있는 유사한 파일의 사전 요구 사항을 정의하여 [!DNL Experience Manager Assets] as a [!DNL Cloud Service] 저장소에 액세스하기 위한 인증 세부 정보를 정의합니다. 사전 요구 사항에는 다음이 포함됩니다.
* imsOrg
* imsToken
* apikey

<!--
The prerequisites vary if you are authenticating using a SUSI flow or a non-SUSI flow.

**Non-SUSI flow**

*   imsOrg
*   imsToken
*   apikey

For more information on these properties, refer to [Asset Selector Properties](#asset-selector-properties).

**SUSI flow**

*   imsClientId
*   imsScope
*   redirectUrl
*   imsOrg
*   apikey

For more information on these properties, refer to [Example for the SUSI flow](#susi-vanilla) and [Asset Selector Properties](#asset-selector-properties).
-->

## 설치 {#installation}

자산 선택기는 ESM CDN(예: [esm.sh](https://esm.sh/)/[Skypack](https://www.skypack.dev/)) 및 [UMD](https://github.com/umdjs/umd) 버전을 통해 사용할 수 있습니다.

**UMD 버전**&#x200B;을 사용하는 브라우저의 경우(권장됨):

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

**ESM CDN 버전**&#x200B;을 사용하며 `import maps`가 지원되는 브라우저의 경우:

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/@assets/selectors/index.js'
</script>
```

**ESM CDN 버전**&#x200B;을 사용하는 Deno/Webpack Module Federation의 경우:

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/@assets/selectors/index.js'
```

### 선택된 자산 유형 {#selected-asset-type}

선택된 자산 유형은 `handleSelection`, `handleAssetSelection` 및 `onDrop` 기능을 사용할 때 자산 정보를 포함하는 오브젝트의 배열입니다.

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
        'http://ns.adobe.com/adobecloud/rel/rendition': Array<{
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
| *repo:state* | 문자열 | 저장소에 있는 자산의 현재 상태입니다(예: 활성, 삭제됨 등). |
| *repo:createdBy* | 문자열 | 자산을 생성한 사용자 또는 시스템입니다. |
| *repo:createDate* | 문자열 | 자산이 생성된 날짜 및 시간입니다. |
| *repo:modifiedBy* | 문자열 | 마지막으로 자산을 수정한 사용자 또는 시스템입니다. |
| *repo:modifyDate* | 문자열 | 자산이 마지막으로 수정된 날짜 및 시간입니다. |
| *dc:format* | 문자열 | 파일 유형과 같은 자산의 형식입니다(예: JPEG, PNG 등). |
| *tiff:imageWidth* | 숫자 | 자산의 폭입니다. |
| *tiff:imageLength* | 숫자 | 자산의 높이입니다. |
| *computedMetadata* | `Record<string, any>` | 모든 종류의 모든 자산 메타데이터(저장소, 애플리케이션 또는 임베드된 메타데이터)에 대한 버킷을 나타내는 오브젝트입니다. |
| *_links* | `Record<string, any>` | 관련 자산에 대한 하이퍼미디어 링크입니다. 메타데이터 및 렌디션과 같은 리소스에 대한 링크가 포함됩니다. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition* | `Array<Object>` | 자산의 렌디션에 대한 정보가 포함된 오브젝트 배열입니다. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].href* | 문자열 | 렌디션에 대한 URI입니다. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].type* | 문자열 | 렌디션의 MIME 유형입니다. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].&#39;repo:size&#39;* | 숫자 | 렌디션의 크기입니다(바이트). |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].width* | 숫자 | 렌디션의 폭입니다. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].height* | 숫자 | 렌디션의 높이입니다. |

전체 속성 목록과 자세한 예를 보려면 [자산 선택기 코드 예](https://github.com/adobe/aem-assets-selectors-mfe-examples)를 방문하십시오.

<!--
### ImsAuthProps {#ims-auth-props}

The `ImsAuthProps` properties define the authentication information and flow that the Asset Selector uses to obtain an `imsToken`. By setting these properties, you can control how the authentication flow should behave and register listeners for various authentication events.

| Property Name | Description|
|---|---|
| `imsClientId`| A string value representing the IMS client ID used for authentication purposes. This value is provided by Adobe and is specific to your Adobe AEM CS organization.|
| `imsScope`| Describes the scopes used in authentication. The scopes determine the level of access that the application has to your organization resources. Multiple scopes can be separated by commas.|
| `redirectUrl` | Represents the URL where the user is redirected after authentication. This value is typically set to the current URL of the application. If a `redirectUrl` is not supplied, `ImsAuthService` will use the redirectUrl used to register the `imsClientId`|
| `modalMode`| A boolean indicating whether the authentication flow should be displayed in a modal (pop-up) or not. If set to `true`, the authentication flow is displayed in a pop-up. If set to `false`, the authentication flow is displayed in a full page reload. _Note:_ for better UX, you can dynamically control this value if the user has browser pop-up disabled. |
| `onImsServiceInitialized`| A callback function that is called when the Adobe IMS authentication service is initialized. This function takes one parameter, `service`, which is an object representing the Adobe IMS service. See [`ImsAuthService`](#imsauthservice-ims-auth-service) for more details.|
| `onAccessTokenReceived`| A callback function that is called when an `imsToken` is received from the Adobe IMS authentication service. This function takes one parameter, `imsToken`, which is a string representing the access token. |
| `onAccessTokenExpired`| A callback function that is called when an access token has expired. This function is typically used to trigger a new authentication flow to obtain a new access token. |
| `onErrorReceived`| A callback function that is called when an error occurs during authentication. This function takes two parameters: the error type and error message. The error type is a string representing the type of error and the error message is a string representing the error message. |

### ImsAuthService {#ims-auth-service}

`ImsAuthService` class handles the authentication flow for the Asset Selector. It is responsible for obtaining an `imsToken` from the Adobe IMS authentication service. The `imsToken` is used to authenticate the user and authorize access to the Adobe Experience Manager (AEM) CS Assets repository. ImsAuthService uses the `ImsAuthProps` properties to control the authentication flow and register listeners for various authentication events. You can use the convenient [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) function to register the _ImsAuthService_ instance with the Asset Selector. The following functions are available on the `ImsAuthService` class. However, if you're using the _registerAssetsSelectorsAuthService_ function, you do not need to call these functions directly.

| Function Name | Description |
|---|---|
| `isSignedInUser` | Determines whether the user is currently signed in to the service and returns a boolean value accordingly.|
| `getImsToken`    | Retrieves the authentication `imsToken` for the currently signed-in user, which can be used to authenticate requests to other services such as generating asset _rendition.|
| `signIn`| Initiates the sign-in process for the user. This function uses the `ImsAuthProps` to show authentication in either a pop-up or a full page reload |
| `signOut`| Signs the user out of the service, invalidating their authentication token and requiring them to sign in again to access protected resources. Invoking this function will reload the current page.|
| `refreshToken`| Refreshes the authentication token for the currently signed-in user, preventing it from expiring and ensuring uninterrupted access to protected resources. Returns a new authentication token that can be used for subsequent requests. |
-->

### SUSI 외 흐름 예 {#non-susi-vanilla}

이 예는 통합 셸에서 [!DNL Adobe] 애플리케이션을 실행할 때 SUSI 외 흐름을 통해 자산 선택기를 사용하는 방법과 인증용으로 생성된 `imsToken`을 이미 보유한 경우에 대해 설명합니다.

아래 예의 _6~15행_&#x200B;에 표시된 대로 `script` 태그를 사용하여 코드에 자산 선택기 패키지를 포함합니다. 스크립트가 로드되면 `PureJSSelectors` 전역 변수를 사용할 수 있습니다. _16~23행_&#x200B;에 표시된 대로 자산 선택기 [속성](#asset-selector-properties)을 정의합니다. SUSI 외 흐름 인증에는 `imsOrg` 및 `imsToken` 속성이 모두 필요합니다. `handleSelection` 속성은 선택한 자산을 처리하는 데 사용됩니다. 자산 선택기를 렌더링하려면 _17행_&#x200B;에서 언급한 대로 `renderAssetSelector` 기능을 호출합니다. _21~22행_&#x200B;에 표시된 대로 `<div>` 컨테이너 요소에 자산 선택기가 표시됩니다.

다음 단계를 따르면 [!DNL Adobe] 애플리케이션에서 SUSI 외 흐름과 함께 자산 선택기를 사용할 수 있습니다.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Asset Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>
    <script>
        // get the container element in which we want to render the AssetSelector component
        const container = document.getElementById('asset-selector-container');
        // imsOrg and imsToken are required for authentication in non-SUSI flow
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

자세한 예를 보려면 [자산 선택기 코드 예](https://github.com/adobe/aem-assets-selectors-mfe-examples)를 방문하십시오.

<!--
### Example for the SUSI flow {#susi-vanilla}

Use this example `index.html` file for authentication if you are integrating your application using SUSI flow.

Access the Asset Selector package using the `Script` Tag, as shown in *line 9* to *line 11* of the example `index.html` file.

*Line 14* to *line 38* of the example describes the IMS flow properties, such as `imsClientId`, `imsScope`, and `redirectURL`. The function requires that you define at least one of the `imsClientId` and `imsScope` properties. If you do not define a value for `redirectURL`, the registered redirect URL for the client ID is used.

As you do not have an `imsToken` generated, use the `registerAssetsSelectorsAuthService` and `renderAssetSelectorWithAuthFlow` functions, as shown in line 40 to line 50 of the example `index.html` file. Use the `registerAssetsSelectorsAuthService` function before `renderAssetSelectorWithAuthFlow` to register the `imsToken` with the Asset Selector. [!DNL Adobe] recommends to call `registerAssetsSelectorsAuthService` when you instantiate the component.

Define the authentication and other Assets as a Cloud Service access-related properties in the `const props` section, as shown in *line 54* to *line 60* of the example `index.html` file.

The `PureJSSelectors` global variable, mentioned in *line 65*, is used to render the Asset Selector in the web browser.

Asset Selector is rendered on the `<div>` container element, as mentioned in *line 74* to *line 81*. The example uses a dialog to display the Asset Selector.

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
-->

## 자산 선택기 속성 사용 {#asset-selector-properties}

자산 선택기 속성을 사용하여 자산 선택기가 렌더링되는 방식을 사용자 정의할 수 있습니다. 다음 표에는 자산 선택기를 사용자 정의하고 사용하는 데 사용할 수 있는 속성이 나열되어 있습니다.

| 속성 | 유형 | 필수 | 기본값 | 설명 |
|---|---|---|---|---|
| *레일* | 부울 | 아니요 | false | `true`가 확인 표시되어 있는 경우 자산 선택기가 왼쪽 레일 보기에서 렌더링됩니다. `false`가 확인 표시되어 있는 경우에는 자산 선택기가 모달 보기에서 렌더링됩니다. |
| *imsOrg* | 문자열 | 예 |  | 조직에 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]를 프로비저닝하는 중에 할당된 Adobe IMS(Identity Management System)입니다. 액세스하려는 조직이 Adobe IMS에 속해 있는지 여부를 인증하려면 `imsOrg` 키가 필요합니다. |
| *imsToken* | 문자열 | 아니요 |  | 인증에 사용되는 IMS 전달자 토큰입니다. SUSI 외 흐름을 사용하는 경우 `imsToken`이 필요합니다. |
| *apiKey* | 문자열 | 아니요 |  | AEM Discovery 서비스에 액세스하는 데 사용되는 API 키입니다. SUSI 외 흐름을 사용하는 경우 `apiKey`가 필요합니다. |
| *rootPath* | 문자열 | 아니요 | /content/dam/ | 자산 선택기에 자산이 표시되는 폴더 경로입니다. 캡슐화된 형태로도 `rootPath`를 사용할 수 있습니다. 예를 들어 `/content/dam/marketing/subfolder/`라는 경로가 주어지면 자산 선택기에서는 상위 폴더로 이동할 수 없으며 하위 폴더만 표시됩니다. |
| *path* | 문자열 | 아니요 |  | 자산 선택기가 렌더링될 때 자산의 특정 디렉터리로 이동하는 데 사용되는 경로입니다. |
| *filterSchema* | 배열 | 아니요 |  | 필터 속성을 구성하는 데 사용되는 모델입니다. 자산 선택기에서 특정 필터 옵션을 제한하려는 경우에 유용합니다. |
| *filterFormProps* | 오브젝트 | 아니요 |  | 검색을 세분화하는 데 사용해야 하는 필터 속성을 지정합니다. 예를 들어 MIME 유형을 JPG, PNG, GIF로 지정할 수 있습니다. |
| *selectedAssets* | 배열 `<Object>` | 아니요 |  | 자산 선택기가 렌더링될 때 선택된 자산을 지정합니다. 자산의 ID 속성을 포함하는 오브젝트 배열이 필요합니다. 그 예로는 `[{id: 'urn:234}, {id: 'urn:555'}]` 등이 있습니다. 또한 현재 디렉터리에서 자산을 사용할 수 있어야 합니다. 다른 디렉터리를 사용해야 하는 경우 `path` 속성 값도 제공하십시오. |
| *acvConfig* | 오브젝트 | 아니요 |  | 기본값을 재정의하기 위한 사용자 지정 구성을 포함하는 오브젝트가 포함된 자산 컬렉션 보기 속성입니다. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | 아니요 |  | OOTB 번역이 애플리케이션 요구 사항을 제대로 충족하지 않는 경우 `i18nSymbols` 속성을 통해 현지화된 사용자 지정 값을 전달할 수 있는 인터페이스를 노출할 수 있습니다. 이 인터페이스를 통해 값을 전달하면 제공된 기본 번역이 재정의되며 사용자 고유의 번역이 대신 사용됩니다.  재정의를 수행하려면 유효한 재정의하려는 `i18nSymbols`의 키에 [메시지 설명자](https://formatjs.io/docs/react-intl/api/#message-descriptor) 오브젝트를 전달해야 합니다. |
| *intl* | 오브젝트 | 아니요 |  | 자산 선택기는 기본 OOTB 번역을 제공합니다. `intl.locale` 속성을 통해 유효한 로케일 문자열을 제공하여 번역 언어를 선택할 수 있습니다. 예를 들어 `intl={{ locale: "es-es" }}`의 경우 </br></br> 지원되는 로케일 문자열은 언어 표준의 이름을 표현하기 위해 [ISO 639 - 코드](https://www.iso.org/iso-639-language-codes.html)를 따릅니다. </br></br> 지원되는 로케일 목록: 영어 - “en-us”(기본값) 스페인어 - “es-es” 독일어 - “de-de” 프랑스어 - “fr-fr” 이탈리아어 - “it-it” 일본어 - “ja-jp” 한국어 - “ko-kr” 포르투갈어 - “pt-br” 중국어(번체) - “zh-cn” 중국어(대만) - “zh-tw” |
| *repositoryId* | 문자열 | 아니요 | &#39;&#39; | 자산 선택기가 콘텐츠를 로드하는 저장소입니다. |
| *additionalAemSolutions* | `Array<string>` | 아니요 | [ ] | AEM 저장소 목록을 추가할 수 있습니다. 이 속성에 정보를 제공하지 않으면 미디어 라이브러리 또는 AEM Assets 저장소만 고려됩니다. |
| *hideTreeNav* | 부울 | 아니요 |  | 자산 트리 탐색 사이드바를 표시할지 또는 숨길지 지정합니다. 모달 보기에서만 사용되므로 레일 보기에서는 이 속성이 영향을 미치지 않습니다. |
| *onDrop* | 함수 | 아니요 |  | 이 속성은 자산의 드롭 기능을 허용합니다. |
| *dropOptions* | `{allowList?: Object}` | 아니요 |  | “allowList”를 사용하여 드롭 옵션을 구성합니다. |
| *colorScheme* | 문자열 | 아니요 |  | 자산 선택기에 대한 테마를 구성합니다(`light` 또는 `dark`). |
| *handleSelection* | 함수 | 아니요 |  | 자산을 선택하고 모달의 `Select` 버튼을 클릭하면 자산 항목 배열과 함께 호출됩니다. 이 함수는 모달 보기에서만 호출됩니다. 레일 보기의 경우 `handleAssetSelection` 또는 `onDrop` 함수를 사용하십시오. 예: <pre>handleSelection=(assets: Asset[])=> {...}</pre> 자세한 내용은 [선택된 자산 유형](#selected-asset-type)을 참조하십시오. |
| *handleAssetSelection* | 함수 | 아니요 |  | 자산을 선택하거나 선택 취소할 때 항목 배열과 함께 호출됩니다. 이 속성은 사용자가 자산을 선택할 때 자산을 수신하려는 경우에 유용합니다. 예: <pre>handleSelection=(assets: Asset[])=> {...}</pre> 자세한 내용은 [선택된 자산 유형](#selected-asset-type)을 참조하십시오. |
| *onClose* | 함수 | 아니요 |  | 모달 보기에서 `Close` 버튼을 누르면 호출됩니다. 이 속성은 `modal` 보기에서만 호출되며 `rail` 보기에서는 무시됩니다. |
| *onFilterSubmit* | 함수 | 아니요 |  | 사용자가 다른 필터 조건을 변경할 때 필터 항목과 함께 호출됩니다. |
| *selectionType* | 문자열 | 아니요 | 단일 | 한 번에 `single` 자산을 선택할지 또는 `multiple` 자산을 선택할지에 대한 구성입니다. |

## 자산 선택기 속성 사용 예 {#usage-examples}

`index.html` 파일에서 자산 선택기 [속성](#asset-selector-properties)을 정의하여 애플리케이션 내 자산 선택기 표시를 사용자 정의할 수 있습니다.

### 예 1: 레일 보기의 자산 선택기

![레일-보기-예](assets/rail-view-example-vanilla.png)

AssetSelector `rail` 값이 `false`로 설정되어 있거나 속성에 언급되어 있지 않는 경우 자산 선택기는 기본적으로 모달 보기에 표시됩니다.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

### 예 2: 메타데이터 팝오버

다양한 속성을 통해 정보 아이콘을 사용하여 보려는 자산의 메타데이터를 정의합니다. 정보 팝오버는 자산의 제목, 차원, 수정일, 위치 및 설명을 포함하여 자산 또는 폴더에 대한 정보 모음을 제공합니다. 아래 예에서는 자산의 메타데이터를 표시하는 데 다양한 속성이 사용됩니다. 예를 들어 `repo:path` 속성은 자산의 위치를 지정합니다. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![메타데이터-팝오버-예](assets/metadata-popover.png)


### 예 3: 레일 보기의 사용자 정의 필터 속성

세분화된 검색 외에도 자산 선택기를 사용하면 다양한 속성을 사용자 정의하여 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 애플리케이션에서의 검색을 세분화할 수 있습니다. 애플리케이션에 사용자 정의된 검색 필터를 추가하려면 다음 코드를 추가해야 합니다. 아래 예의 이미지, 문서 또는 비디오 중에서 자산 유형을 필터링하는 `Type Filter` 검색 또는 검색을 위해 추가한 필터 유형

![사용자-정의-필터-예-바닐라](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->

<!-- Property details to be added here. Referred the ticket https://jira.corp.adobe.com/browse/ASSETS-19023-->

<!--
## Asset Selector Object Schema {#object-schema}

Schema describes the object properties associated with an asset selected using Asset Selector. It uses the combination of data types and their values to validate the object describing the selected Asset using an Asset Selector.

**Schema Syntax**
````
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
        'http://ns.adobe.com/adobecloud/rel/rendition': Array<{
            href: string;
            type: string;
            'repo:size': number;
            width: number;
            height: number;
            [others: string]: any;
        }>;
    };
}
````

**Query Parameters**

| Parameter | Type | Description |
|---|---|---|
| repo:id | string | ID of an Asset |
| repo:name | string | The name of an Asset |
| repo:path | string | The path of an Asset |
| repo:size | number | Size of an Asset (in bytes) |
| repo:createdBy | string | ID of a user who created an Asset |
| repo: createdDate | string | The timestamp when an asset was created |
| repo:modifiedBy | string | ID of a user who modified the asset recently |
| repo:modifyDate | string | The timestamp when the asset was last modified |
| dc:format | string | MIME type of an Asset |
| tiff:imageWidth | number | The width of an image type of Asset |
| tiff:imageLength | number | The height of an image type of Asset |
| repo:state | string | The `Approved`, `Rejected`, or `Expired`state of an Asset |
| computedMetadata | string | It is an object that represents a bucket for all the Asset's metadata of all kinds (repository, application or embedded metadata) |
| _links | string | It represents the collection of links used in the Asset Selector. The links are represented in the form of an array. The parameters of an array include: `href`, `type`, `repo:size`, `width`, `height`, etc.  |

For the detailed example of Object Schema, click 
-->

## 오브젝트 스키마를 사용한 자산 선택 처리 {#handling-selection}

`handleSelection` 속성은 자산 선택기에서 단일 또는 다중 자산 선택을 처리하는 데 사용됩니다. 아래 예는 `handleSelection`의 사용 구문을 나타냅니다.

![선택-처리](assets/handling-selection.png)

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

자산 선택기를 사용하면 자산 선택을 위해 저장소를 전환할 수도 있습니다. 왼쪽 패널에 있는 드롭다운에서 원하는 저장소를 선택할 수 있습니다. 드롭다운 목록에서 사용할 수 있는 저장소 옵션은 `index.html` 파일에 정의된 `repositoryId` 속성을 기반으로 하며, 이 속성은 로그인한 사용자가 액세스하는 선택된 IMS 조직의 환경을 기반으로 합니다. 소비자는 기본 `repositoryID`를 전달할 수 있으며 이 경우 자산 선택기는 저장소 전환기 렌더링을 중지하고 주어진 저장소의 자산만 렌더링합니다.
<!--
It is based on the `imsOrg` that is provided in the application. If you want to see the list of repositories, then `repositoryId` is required to view those specific repositories in your application.
-->

### 자산 저장소

작업을 수행하는 데 사용할 수 있는 자산 폴더 모음입니다.

### 기본 제공 필터 {#filters}

자산 선택기에는 검색 결과를 세분화할 수 있는 기본 필터 옵션도 제공됩니다. 사용 가능한 필터는 다음과 같습니다.

* `File type`: 폴더, 파일, 이미지, 문서 또는 비디오 포함
* `MIME type`: JPG, GIF, PPTX, PNG, MP4, DOCX, TIFF, PDF, XLSX 포함
* `Image Size`: 이미지 최소/최대 폭, 최소/최대 높이 포함

![레일-보기-예](assets/filters-asset-selector.png)

### 사용자 정의 검색

전체 텍스트 검색 외에도 자산 선택기를 사용하면 사용자 정의 검색을 사용하여 파일 내의 자산을 검색할 수 있습니다. 모달 보기 및 레일 보기 모드 모두에서 사용자 정의 검색 필터를 사용할 수 있습니다.

![사용자 정의-검색](assets/custom-search.png)

자주 검색하는 필드를 저장하고 나중에 사용할 수 있도록 기본 검색 필터를 생성할 수도 있습니다. 자산에 대한 사용자 정의 검색을 만들기 위해 `filterSchema` 속성을 사용할 수 있습니다.

### 검색 창 {#search-bar}

자산 선택기를 사용하면 선택한 저장소 내에서 자산의 전체 텍스트 검색을 수행할 수 있습니다. 예를 들어 검색 창에 `wave` 키워드를 입력하면 메타데이터 속성에 언급된 것 중 `wave` 키워드가 있는 모든 자산이 표시됩니다.

### 정렬 {#sorting}

자산 선택기에서 자산의 이름, 차원 또는 크기별로 자산을 정렬할 수 있습니다. 자산을 오름차순 또는 내림차순으로 정렬할 수도 있습니다.

### 보기 유형 {#types-of-view}

자산 선택기를 사용하면 네 가지 다른 보기에서 자산을 볼 수 있습니다.

* **![목록 보기](assets/do-not-localize/list-view.png) [!UICONTROL 목록 보기]**: 목록 보기에는 스크롤 가능한 파일과 폴더가 단일 열에 표시됩니다.
* **![격자 보기](assets/do-not-localize/grid-view.png) [!UICONTROL 격자 보기]**: 격자 보기에는 스크롤 가능한 파일과 폴더가 행과 열의 격자로 표시됩니다.
* **![갤러리 보기](assets/do-not-localize/gallery-view.png) [!UICONTROL 갤러리 보기]**: 갤러리 보기에는 파일 또는 폴더가 중앙이 잠긴 가로 목록으로 표시됩니다.
* **![워터폴 보기](assets/do-not-localize/waterfall-view.png) [!UICONTROL 워터폴 보기]**: 워터폴 보기에는 파일 또는 폴더가 Bridge 형태로 표시됩니다.

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
*   **Configure** You can configure the files/folders that you want to show at the upfront. The assets that are chosen to view can be of any supported formats, for example, JPEG. It allows you to control the display of various text or symbols as per your choice.
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
*   **Open in media library** Allows you to open the asset in media library.
*   **Upload** Allows you to upload an asset directly.
*   **Download** Downloads the asset in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
-->
<!--

### Status of an asset

Asset Selector allows you to know the status of your uploaded assets. The status can be `Approved`, `Rejected`, or `Expired` of the asset. 
-->
<!--

### Localization

The integration of Asset Selector with [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] allows localized content appear in your application.
-->