---
title: 변형 생성
description: AEM as a Cloud Service 내 다양한 편집기에서 접근 가능한 변형 생성에 대해 알아보기
feature: Generate Variations
role: Admin, Architect, Developer, User
exl-id: d380ddd6-43f9-4bbf-8167-a6a472b9fc01
source-git-commit: 85489b9d2c774af2f82efe4cde406d6d33057d4e
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 97%

---

# 변형 생성 - AEM 편집기에 통합 {#generate-variations-integrated-in-aem-editors}

디지털 채널을 최적화하고 콘텐츠 제작을 가속화하는 방법을 찾고 있다면 AEM 편집기에 통합된 변형 생성을 사용할 수 있습니다.

변형 생성은 생성형 AI를 활용하여 사용자의 입력을 기반으로 콘텐츠 변형을 생성합니다. 변형을 만든 후 웹 사이트에서 콘텐츠를 사용할 수 있으며, [Edge Delivery Services](/help/edge/overview.md)의 [실험](https://www.aem.live/docs/experimentation) 기능을 사용하여 성공 여부를 측정할 수도 있습니다.

이를 통해 브랜드에 부합하는 콘텐츠를 몇 분 만에 신속하게 생성하여 콘텐츠 생산 속도를 가속화할 수 있습니다. 이로 인해 새로운 복사 변형을 통해 전환율을 향상시킬 수 있습니다.

[다음 편집기를 구성한 후](#access-generate-variations)에는 편집기에서 [변형 생성에 액세스](#access-generate-variations)할 수 있습니다.

* [AEM Edge Delivery Services의 Sidekick 내 문서 기반 작성용 편집기](#access-aem-sidekick)
* [범용 편집기 내](#access-aem-universal-editor)
* [콘텐츠 조각 편집기 내](#access-aem-content-fragment-editor)

>[!IMPORTANT]
>
>이 페이지는 예시의 기본으로 문서 기반 작성을 사용하지만 원칙은 다른 편집기에도 적용됩니다.

>[!NOTE]
>
>모든 경우에 변형 생성을 사용하려면 [액세스 사전 요구 사항](#access-prerequisites)이 충족되었는지 확인해야 합니다.

>[!NOTE]
>
>이 버전을 사용하는 것이 좋습니다. 독립 실행형 버전 [변형 생성](/help/generative-ai/generate-variations.md)에 계속 직접 액세스할 수 있지만 앞으로 더 이상 사용되지 않습니다.

그런 다음 아래와 같은 작업을 수행할 수 있습니다.

* 기존 콘텐츠 블록에서 [작업하려는 콘텐츠 선택](#select-the-content)
   * 선택된 블록은 표시되는 내용과 사용 가능한 작업을 결정합니다.
* [원하는 변경 사항 설명](#describe-the-changes-you-want)
* [콘텐츠의 변형을 생성](#generate-copy)한 다음 [원하는 경우 추가 작업 수행](#take-further-action-on-a-variation)
* [변형을 선택하고 사용](#use-a-generated-variation)
* [기록](#history) 검토
* [즐겨찾기](#favorites) 보기

## 법률 및 사용 참고 사항 {#legal-usage-note}

<!--
Generative AI and Generate Variations for AEM are powerful tools – but **you** are responsible for use of the output.

Your inputs to the service should be tied to a context. This context can be your branding materials, website content, data, schemas for such data, templates, or other trusted documents.

You must evaluate the accuracy of any output as appropriate to your use case.

Before using Generate Variations you are recommended to read the [Adobe Experience Cloud Generative AI User Guidelines](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).
-->

[변형 생성의 사용](#generative-action-usage)은 생성형 액션의 소비와 관련이 있습니다.

## 개요 {#overview}

편집기에 통합된 변형 생성을 열면 세 개의 탭이 있는 부동 패널로 확장 기능이 표시됩니다.

![변형 생성 - 문서 기반 작성 개요](assets/generate-variations-doc-based-overview.png)

* 편집기:
   * 편집기 내 콘텐츠 흐름을 보여 줍니다.
   * 여기에서 **변형 생성**&#x200B;에 사용할 콘텐츠 블록을 선택할 수 있습니다.
* **변형 생성**:
   * 세 개의 탭이 있는 부동 패널로, 원하는 위치로 이동할 수 있습니다.
   * [생성](#get-started-with-generate-variations):
      * [선택한 콘텐츠](#select-the-content)를 표시합니다.
      * 변경에 대한 샘플 **제안**&#x200B;을 제공합니다.
      * [원하는 변경 사항을 설명](#describe-the-changes-you-want)할 수 있습니다.
      * 새로운 변형을 [생성](#generate-copy)할 수 있습니다.
      * 생성된 변형을 보여 줍니다. <!--, together with their [brand score](#the-brand-score).-->
      * [변형에 대한 추가 작업을 수행](#take-further-action-on-a-variation)합니다.
      * [생성된 변형을 사용](#use-a-generated-variation)합니다.
   * [기록](#history):
      * 최근 생성 기록을 표시합니다.
   * [즐겨찾기](#favorites):
      * 즐겨찾기로 표시한 이전 세대의 결과를 표시합니다.
   * **Adobe Generative AI 용어**: [Adobe Experience Cloud Generative AI 사용자 지침](https://www.adobe.com/kr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)에 대한 링크입니다.

## 변형 생성 시작하기 {#get-started-with-generate-variations}

인터페이스는 콘텐츠 생성 과정을 안내합니다. 인터페이스를 연 후 첫 번째 단계는 사용할 콘텐츠 블록을 선택하는 것입니다.

### 콘텐츠 선택 {#select-the-content}

편집기의 주요 콘텐츠 흐름에서 변형을 생성할 콘텐츠를 선택합니다. 이 **선택**&#x200B;은 **생성** 탭에 표시됩니다.

### 원하는 변경 사항 설명 {#describe-the-changes-you-want}

콘텐츠의 변형을 생성하려면 원하는 변경 사항을 설명해야 합니다. 제공된 **제안** 중 하나를 선택하거나 직접 설명을 제공할 수 있습니다.

추가적인 컨텍스트를 제공하기 위해 **수정자**&#x200B;를 지정할 수도 있습니다.

* **웹 페이지 참조**
더 많은 컨텍스트를 위해 URL을 제공합니다.
* **콘텐츠 브리프 업로드**
콘텐츠 브리프의 세부 정보를 담은 `.docx` 파일(10MB 이하)을 업데이트합니다.

### 사본 생성 {#generate-copy}

원하는 변경 사항을 설명한 후 **생성**&#x200B;을 선택하여 생성형 AI의 응답을 확인합니다.

![변형 생성 - 문서 기반 사본 생성](assets/generate-variations-doc-based-generate-copy.png)

<!--
### The Brand Score {#the-brand-score}

The brand score shows you how on-brand the generated variation is.
-->

### 변형에 대한 추가 작업 수행 {#take-further-action-on-a-variation}

단일 변형을 선택하면 다음과 같은 작업을 사용할 수 있습니다.

* **편집**
   * 생성된 변형의 텍스트를 편집할 수 있습니다.

      * 업데이트 내용을 웹 페이지에서 미리 볼 수 있습니다.

   * 변경 사항을 저장하여 나중에 사용할 수 있습니다.
* **즐겨찾기**
   * 이 변형을 나중에 참고할 수 있도록 플래그로 표시합니다.
   * 플래그가 지정되면 [즐겨찾기](#favorites) 탭에 표시됩니다.
* **AI 이론적 근거**
   * 투명성을 높이기 위해 생성형 AI가 해당 변형을 생성한 이유에 대한 간략한 설명을 제공합니다.

### 생성된 변형 사용 {#use-a-generated-variation}

생성형 AI로 생성된 콘텐츠를 사용하려면 먼저 선택한 후 **CSV로 내보내기**&#x200B;를 선택해야 합니다.

내보낸 후에는 다른 곳에서 콘텐츠를 사용할 수 있습니다. 예를 들어, 웹 사이트의 콘텐츠를 작성할 때 사용할 수 있습니다. [실험](https://www.aem.live/docs/experimentation)을 실행할 수도 있습니다.

>[!NOTE]
>
>Generate Variations에 [AEM 범용 편집기](#access-aem-universal-editor) 또는 [AEM 콘텐츠 조각 편집기](#access-aem-content-fragment-editor)에서 접근하면 선택된 생성 콘텐츠가 자동으로 AEM에 저장됩니다.

## 기록 {#history}

이 탭은 **생성**&#x200B;을 선택한 후의 과거 활동을 보여 줍니다. 하나의 **기록** 항목이 추가됩니다.

나중에 메인 흐름에서 동일한 콘텐츠를 선택하고 **기록** 탭을 열면 해당 블록에 대해 생성된 모든 변형을 확인할 수 있습니다.

## 즐겨찾기 {#favorites}

콘텐츠를 검토한 후 선택한 변형을 즐겨찾기에 저장할 수 있습니다.

저장되면 **즐겨찾기** 아래에 표시됩니다. 즐겨찾기는 계속 유지됩니다(**즐겨찾기에서 제거**&#x200B;하거나 브라우저 캐시를 지울 때까지).

* 해당 항목에 대해 **편집**, **즐겨찾기에서 제거** 또는 **AI 이론적 근거** 보기를 수행할 수 있습니다.
* 변형이 선택되면 **CSV로 내보내기** 기능도 사용할 수 있습니다.

## 생성형 액션 사용량 {#generative-action-usage}

사용량 관리는 수행된 액션에 따라 달라집니다.

* 변형 생성

  하나의 카피 변형 생성은 하나의 생성형 액션과 동일합니다. 고객은 AEM 라이선스와 함께 제공되는 일정 수의 생성형 액션을 보유하고 있습니다. 기본 할당량을 모두 사용하면 추가 액션을 구매할 수 있습니다.

  >[!NOTE]
  >
  >기본 할당량에 대한 자세한 내용은 [Adobe Experience Manager: Cloud Service | 제품 설명](https://helpx.adobe.com/kr/legal/product-descriptions/aem-cloud-service.html)에서 확인할 수 있으며, 더 많은 생성형 액션을 구매하려면 계정 팀에 문의하십시오.

## 변형 생성 액세스 {#access-generate-variations}

사전 요구 사항을 충족하면 AEM as a Cloud Service 또는 Edge Delivery Services의 Sidekick에서 변형 생성에 액세스할 수 있습니다.

### 액세스 사전 요구 사항 {#access-prerequisites}

변형 생성을 사용하려면 다음 사전 요구 사항이 충족되었는지 확인해야 합니다.

* [Edge Delivery Services가 포함된 Experience Manager as a Cloud Service 액세스](#access-to-aemaacs-with-edge-delivery-services)

#### Edge Delivery Services가 포함된 Experience Manager as a Cloud Service 액세스{#access-to-aemaacs-with-edge-delivery-services}

변형 생성에 액세스해야 하는 사용자는 Edge Delivery Services가 포함된 Experience Manager as a Cloud Service 환경에 권한이 있어야 합니다.

>[!NOTE]
>
>AEM Sites as a Cloud Service에 대한 계약에 Edge Delivery Services가 포함되어 있지 않은 경우, 액세스 권한을 얻으려면 새 계약에 서명해야 합니다.
>
>Edge Delivery Services가 포함된 AEM Sites as a Cloud Service로 전환하는 방법에 대해 논의하려면 계정 팀에 문의하십시오.

특정 사용자에게 액세스 권한을 부여하려면 해당 사용자 계정을 제품 프로필에 할당합니다. [자세한 내용은 AEM 제품 프로필 할당](/help/journey-onboarding/assign-profiles-cloud-manager.md)을 참조하십시오.

### 문서 기반 작성을 위해 AEM Sidekick에서 액세스 {#access-aem-sidekick}

AEM Sidekick에서의 액세스는 [문서 기반 작성](/help/edge/wysiwyg-authoring/authoring.md)에 사용됩니다.

Edge Delivery Services의 Sidekick에서 변형 생성에 액세스하려면 몇 가지 구성이 필요합니다.

>[!NOTE]
>
>Sidekick을 설치하고 구성하는 방법은 [AEM Sidekick 설치](https://www.aem.live/docs/sidekick-extension) 문서를 참조하십시오.

(Edge Delivery Services의) Sidekick에서 변형 생성을 사용하려면 Edge Delivery Services 프로젝트에 다음 구성을 포함시킵니다.

1. 다음에서 앱을 활성화:

   * `tools/sidekick/config.json`

   이를 기존 구성에 병합한 다음 배포해야 합니다.

   예:

   ```prompt
   {
     "plugins": [
       {
         "id": "aem-genai-variations",
         "titleI18n": {
           "en": "Generate with AI"
         },
         "environments": [
           "preview"
         ],
         "includePaths": [
           "**.docx**"
         ],
         "event": "aem-genai-variations-sidekick"
       }
     ]
   }
   ```

1. 만들기:

   * `/tools/sidekick/aem-genai-variations.js`

   다음 내용을 포함한 파일을 생성해야 합니다.

   ```prompt
   (function () {
     let isAEMGenAIVariationsAppLoaded = false;
     function loadAEMGenAIVariationsApp() {
       const script = document.createElement('script');
       script.src = 'https://experience.adobe.com/solutions/aem-sites-genai-aem-genai-variations-mfe/static-assets/resources/sidekick/client.js?source=plugin';
       script.onload = function () {
         isAEMGenAIVariationsAppLoaded = true;
       };
       script.onerror = function () {
         console.error('Error loading AEMGenAIVariationsApp.');
       };
       document.head.appendChild(script);
     }
   
     function handlePluginButtonClick() {
       if (!isAEMGenAIVariationsAppLoaded) {
         loadAEMGenAIVariationsApp();
       }
     }
   
     // The code snippet for the Sidekick V1 extension, https://chromewebstore.google.com/detail/aem-sidekick/ccfggkjabjahcjoljmgmklhpaccedipo?hl=en
     const sidekick = document.querySelector('helix-sidekick');
     if (sidekick) {
       // sidekick already loaded
       sidekick.addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
     } else {
       // wait for sidekick to be loaded
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('helix-sidekick')
           .addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
       }, { once: true });
     }
   
     // The code snippet for the Sidekick V2 extension, https://chromewebstore.google.com/detail/aem-sidekick/igkmdomcgoebiipaifhmpfjhbjccggml?hl=en
     const sidekickV2 = document.querySelector('aem-sidekick');
     if (sidekickV2) {
       // sidekick already loaded
       sidekickV2.addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
     } else {
       // wait for sidekick to be loaded
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('aem-sidekick')
           .addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
       }, { once: true });
     }
   }());
   ```

1. 업데이트:

   * `/scripts/scripts.js`

   `loadLazy()` 함수에 다음 명령문을 포함하도록 업데이트해야 합니다.

   ```prompt
     import('../tools/sidekick/aem-genai-variations.js');
   ```

   이렇게 하면 `/tools/sidekick/aem-genai-variations.js`가 지연 로딩 프로세스의 일부로 로드됩니다.

   ![변형 생성 - 느린 로더](assets/generate-variations-sidekick-lazyloader.png)

1. 그런 다음 사용자가 [Edge Delivery Services가 포함된 Experience Manager as a Cloud Service에 액세스](#access-to-aemaacs-with-edge-delivery-services)할 수 있는지 확인해야 할 수도 있습니다.

1. 그런 다음 Sidekick 도구 모음에서 **AI를 사용하여 생성**&#x200B;을 선택하여 이 기능에 액세스할 수 있습니다.

   ![변형 생성 - AEM Sidekick에서 액세스](assets/generate-variations-doc-based-sidekick.png)

### AEM 범용 편집기에서 액세스 {#access-aem-universal-editor}

[AEM 범용 편집기](/help/sites-cloud/authoring/universal-editor/authoring.md)에서의 액세스는 확장 기능으로 구현되었습니다. 자세한 내용은 [AEM Experience Manager의 Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/)를 참조하십시오.

### AEM 콘텐츠 조각 편집기에서 액세스 {#access-aem-content-fragment-editor}

[AEM 콘텐츠 조각 편집기](/help/sites-cloud/administering/content-fragments/authoring.md#generate-variations-ai)에서의 액세스는 확장 기능으로 구현되었습니다. 자세한 내용은 [AEM Experience Manager의 Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/)를 참조하십시오.

## 추가 정보 {#further-information}

자세한 내용은 다음에서 확인할 수 있습니다.

* [GitHub에서 생성형 AI 변형 생성](https://github.com/adobe/aem-genai-assistant#setting-up-aem-genai-assistant)
* [Edge Delivery Services 실험](https://www.aem.live/docs/experimentation)

## 릴리스 기록 {#release-history}

현재 및 이전 릴리스에 대한 자세한 내용은 [변형 생성에 대한 릴리스 정보](/help/generative-ai/release-notes-generate-variations.md)를 참조하십시오.
