---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 에셋 선택기를 다양한 Adobe, 비Adobe 및 타사 애플리케이션과 통합합니다.
role: Admin, User
exl-id: 55848de0-aff2-42a0-b959-c771235d9425
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 6%

---

# Adobe이 아닌 애플리케이션과 통합 {#integrate-asset-selector-non-adobe-app}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Asset Selector를 사용하면 다양한 비 Adobe 또는 타사 애플리케이션을 사용하여 통합하여 이들 애플리케이션을 원활하게 함께 사용할 수 있습니다.

## 사전 요구 사항 {#prereqs-non-adobe-app}

에셋 선택기를 Adobe이 아닌 응용 프로그램과 통합하는 경우 다음 사전 요구 사항을 사용하십시오.

* [커뮤니케이션 방법](/help/assets/overview-asset-selector.md#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Adobe이 아닌 응용 프로그램과 통합할 때 자산 선택기는 `imsScope` 또는 `imsClientID`과(와) 같은 IMS(Identity Management System) 속성을 사용하여 [!DNL Experience Manager Assets] 리포지토리에 대한 인증을 지원합니다.

## Adobe이 아닌 애플리케이션에 대한 에셋 선택기 구성 {#configure-non-adobe-app}

Adobe이 아닌 애플리케이션에 대해 에셋 선택기를 구성하려면 먼저 프로비저닝에 대한 지원 티켓을 기록한 후 통합 단계를 수행해야 합니다.

### 지원 티켓 로깅 {#log-a-support-ticket}

Admin Console을 통해 지원 티켓을 기록하는 단계:

1. 티켓 제목에 **AEM Assets을 사용하여 자산 선택기**&#x200B;를 추가합니다.

1. 설명에서 다음 세부 정보를 입력해 주십시오.

   * [!DNL Experience Manager Assets]을(를) [!DNL Cloud Service] URL(프로그램 ID 및 환경 ID)로 사용했습니다.
   * Adobe이 아닌 웹 응용 프로그램이 호스팅되는 도메인 이름.

## 통합 단계 {#non-adobe-app-integration-steps}

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
        src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>
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

## 게재 저장소에 액세스할 수 없음 {#unable-to-access-delivery-repository}

>[!TIP]
>
>로그인 워크플로우를 사용하여 자산 선택기를 통합했지만 여전히 게재 저장소에 액세스할 수 없는 경우 브라우저 쿠키가 정리되었는지 확인하십시오. 그렇지 않으면 콘솔에 `invalid_credentials All session cookies are empty` 오류가 발생합니다.

>[!MORELIKETHIS]
>
>* [다양한 응용 프로그램과 자산 선택기 통합](/help/assets/integrate-asset-selector.md)
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [OpenAPI 기능을 사용하여 Dynamic Media과 자산 선택기 통합](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [자산 선택기 사용자 지정](/help/assets/asset-selector-customization.md)
