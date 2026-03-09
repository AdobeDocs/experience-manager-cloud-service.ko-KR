---
title: 컨텐츠 조각 선택기를 Adobe 이외 또는 타사 애플리케이션과 통합
description: 컨텐츠 조각 선택기를 다양한 Adobe, 비 Adobe 및 타사 애플리케이션과 통합합니다.
role: Admin, User, Developer
source-git-commit: 3af1a89489af96bf9c9908aea7fb20883956517b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 5%

---

# Adobe 이외 애플리케이션과 통합 {#integration-with-non-adobe-application}

콘텐츠 조각 선택기를 사용하면 Adobe이 아닌 다양한 애플리케이션이나 타사 애플리케이션과 통합하여 원활하게 함께 작동할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

컨텐츠 조각 선택기를 Adobe이 아닌 애플리케이션과 통합하는 경우 다음 사전 요구 사항을 사용하십시오.

* [사전 요구 사항](/help/headless/content-fragment-selector/overview.md#prerequisites)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Adobe이 아닌 애플리케이션과 통합하는 경우 콘텐츠 조각 선택기는 `imsScope` 또는 `imsClientID`과 같은 IMS(Identity Management System) 속성을 사용하여 Adobe Experience Manager(AEM) as a Cloud Service 저장소에 대한 인증을 지원합니다.

## 비 Adobe 애플리케이션에 대한 콘텐츠 조각 선택기 구성 {#configure-content-fragment-selector-for-a-non-adobe-application}

Adobe이 아닌 애플리케이션에 대해 콘텐츠 조각 선택기를 구성하려면 통합 단계를 진행하기 전에 먼저 프로비저닝에 대한 지원 티켓을 기록해야 합니다.

### 지원 티켓 로깅 {#logging-a-support-ticket}

Admin Console을 통해 지원 티켓을 기록하는 단계:

1. 티켓 제목에 **AEM 조각이 있는 콘텐츠 조각 선택기**&#x200B;를 추가합니다.

1. 설명에서 다음 세부 정보를 입력해 주십시오.

   * Experience Manager as a Cloud Service URL(프로그램 ID 및 환경 ID).
   * Adobe 이외의 웹 애플리케이션이 호스팅되는 도메인 이름.

## 통합 단계 {#integration-steps}

다음 예제 `index.html` 파일을 사용하여 콘텐츠 조각 선택기를 Adobe 이외의 애플리케이션과 통합할 때 인증합니다.

* `Script` 태그를 사용하여 콘텐츠 조각 선택기 패키지에 액세스합니다.

* `imsClientId`, `imsScope` 및 `redirectURL`과(와) 같은 IMS 흐름 속성을 정의합니다.

   * 함수에는 `imsClientId` 및 `imsScope` 속성 중 하나 이상을 정의해야 합니다.
   * `redirectURL`에 대한 값을 정의하지 않으면 클라이언트 ID에 대해 등록된 리디렉션 URL이 사용됩니다.

* 예제에 생성된 `imsToken`이(가) 없으므로 `registerFragmentsSelectorsAuthService` 및 `renderFragmentSelectorWithAuthFlow` 함수를 사용하십시오.

   * `registerFragmentsSelectorsAuthService` 앞에 `renderFragmentSelectorWithAuthFlow` 함수를 사용하여 `imsToken`을(를) 콘텐츠 조각 선택기에 등록하십시오.
   * Adobe에서는 구성 요소를 인스턴스화할 때 `registerFragmentsSelectorsAuthService`을(를) 호출하는 것이 좋습니다.

* `const props` 섹션에서 인증 및 기타 조각 as a Cloud Service 액세스 관련 속성을 정의합니다.
* `PureJSContentFragmentSelectors` 전역 변수는 웹 브라우저에서 콘텐츠 조각 선택기를 렌더링하는 데 사용됩니다.
* 콘텐츠 조각 선택기가 `<div>` 컨테이너 요소에 렌더링됩니다. 이 예제에서는 대화 상자를 사용하여 콘텐츠 조각 선택기를 표시합니다.

**예`ìndex.html`**

```html {line-numbers="true"}
<!doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <link rel="icon" type="image/svg+xml" href="/vite.svg" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>testing-cf-mfe-integration-with-3rd-party-app</title>
        <script
            id="content-fragments-selector"
            src="https://experience.adobe.com/solutions/CQ-sites-content-fragment-selector/static-assets/resources/content-fragment-selector.js"
        ></script>
        <script>
            const imsProps = {
                imsClientId: '<IMS_CLIENT_ID>',
                imsScope:
                    'additional_info.projectedProductContext, AdobeID, openid, read_organizations',
                redirectUrl: window.location.href,
                onImsServiceInitialized: (service) => {
                    // invoked when the ims service is initialized and is ready
                    console.log('onImsServiceInitialized', service);
                },
                onAccessTokenReceived: (token) => {
                    console.log('onAccessTokenReceived', token);
                },
                onAccessTokenExpired: () => {
                    console.log('onAccessTokenError');
                    // re-trigger sign-in flow
                },
                onErrorReceived: (type, msg) => {
                    console.log('onErrorReceived', type, msg);
                },
            };

            function load() {
                const registeredTokenService =
                    PureJSContentFragmentSelectors.registerContentFragmentSelectorAuthService(
                        imsProps
                    );
                imsInstance = registeredTokenService;
            }

            // initialize the IMS flow before attempting to render the content fragment selector
            load();

            // function that will render the content fragment selector
            function renderContentFragmentSelectorWithAuthFlow() {
                const contentFragmentSelectorDialog = document.getElementById(
                    'content-fragment-selector-dialog'
                );

                const contentFragmentSelectorProps = {
                    inventoryViewToggleEnabled: true,
                    isOpen: true,
                    noWrap: false,
                    orgId: 'YOUR_ORG_ID@AdobeOrg',
                    // repoId: "author-p12345-e67890.adobeaemcloud.com", // if wanted to restrict to a specific repo
                    runningInUnifiedShell: false,
                    onDismiss: () => contentFragmentSelectorDialog.close(),
                    onSubmit: ({ contentFragments }) => {
                        const selectedContentFragment = contentFragments[0];
                        alert(selectedContentFragment.path);
                    },
                };
                // container element on which you want to render the ContentFragmentSelector component
                const container = document.getElementById('content-fragment-selector');

                /// Use the PureJSContentFragmentSelectors in globals to render the ContentFragmentSelector component
                PureJSContentFragmentSelectors.renderContentFragmentSelectorWithAuthFlow(
                    container,
                    contentFragmentSelectorProps,
                    () => contentFragmentSelectorDialog.showModal()
                );
            }
        </script>
    </head>
    <body>
        <div>
            <button onclick="renderContentFragmentSelectorWithAuthFlow()">
                Content Fragment Selector - Select Content Fragments with Ims Flow
            </button>
        </div>
        <dialog id="content-fragment-selector-dialog">
            <div
                id="content-fragment-selector"
                style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px"
            ></div>
        </dialog>
    </body>
</html>
```

## 게재 저장소에 액세스할 수 없음 {#unable-to-access-delivery-repository}

로그인 워크플로를 사용하여 콘텐츠 조각 선택기를 통합했지만 게재 저장소에 액세스할 수 없는 경우 브라우저 쿠키가 정리되었는지 확인하십시오.

그렇지 않으면 콘솔에 `invalid_credentials All session cookies are empty` 오류가 표시될 수 있습니다.
