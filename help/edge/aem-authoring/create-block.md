---
title: Universal Editor에 사용하도록 구성된 블록 만들기
description: Edge Delivery Services 프로젝트를 통해 AEM 작성 시 Universal Editor에 사용하도록 구성된 블록을 만드는 방법에 대해 알아봅니다.
exl-id: 65a5600a-8d16-4943-b3cd-fe2eee1b4abf
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: e0b4eafaa9fdc496362f90e6da14b4b198b4ea3e
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 94%

---


# Universal Editor에 사용하도록 구성된 블록 만들기 {#create-block}

Edge Delivery Services 프로젝트를 통해 AEM 작성 시 Universal Editor에 사용하도록 구성된 블록을 만드는 방법에 대해 알아봅니다.

## 사전 요구 사항 {#prerequisites}

이 안내서에서는 Edge Delivery Services 프로젝트를 사용하여 AEM 작성 시 Universal Editor용으로 구성된 블록을 만드는 방법에 대한 단계별 지침이 나와 있습니다. 구성 요소 추가, Universal Editor에서 구성 요소 정의 로드, 페이지 게시, 블록 장식 및 스타일 구현, 변경 사항을 프로덕션에 적용하고 확인하는 방법을 다룹니다. 이 안내서를 완료하면 자체 프로젝트에 대한 새 블록을 만들어 배포할 수 있습니다.

이 안내서에는 Edge Delivery Services 프로젝트 및 Universal Editor를 사용한 AEM 작성에 대한 기존 지식이 필요합니다. 이 안내서를 시작하기 전에 Edge Delivery Services에 액세스하고 다음을 포함한 기본 사항을 숙지해야 합니다.

* [Edge Delivery Service 튜토리얼](/help/edge/developer/tutorial.md)이 완료되었습니다.
* [AEM Cloud Service 샌드박스](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)에 액세스할 수 있습니다.
* [동일한 샌드박스 환경에서 Universal Editor를 활성화](/help/implementing/universal-editor/getting-started.md)했습니다.
* [Edge Delivery Services를 사용한 AEM 작성을 위한 개발자 시작 안내서](/help/edge/aem-authoring/edge-dev-getting-started.md)의 안내서를 완료하셨습니다.

이 안내서는 [Edge Delivery Services를 사용한 AEM 작성을 위한 개발자 시작 안내서](/help/edge/aem-authoring/edge-dev-getting-started.md)의 안내서에서 수행한 작업을 기반으로 합니다.

## 프로젝트에 새로운 블록 추가 {#add-block}

이 안내서에서는 페이지에서 기억에 남는 인용을 렌더링하는 블록을 작성합니다.

이 예를 단순화하기 위해 프로젝트 저장소의 `main` 분기에 모든 변경 사항이 적용됩니다. 물론 실제 프로젝트에서는 `main`으로 병합하기 전 가져오기 요청을 통해 다른 분기에서 개발하고 모든 변경 사항을 검토하여 [개발 모범 사례를 따라야 합니다](https://www.aem.live/docs/dev-collab-and-good-practices).

Adobe는 3단계 방식으로 블록을 개발할 것을 권장합니다.

1. 블록에 대한 정의와 모델을 만들고 검토한 후 이를 프로덕션에 적용합니다.
1. 새 블록으로 콘텐츠를 만듭니다.
1. 새 블록의 장식과 스타일을 구현합니다.

다음 인용 블록 예제는 이 방식을 따릅니다.

### 블록 정의 및 모델 만들기 {#create-block-model}

1. [Edge Delivery Services를 사용한 AEM 작성을 위한 개발자 시작 안내서](/help/edge/aem-authoring/edge-dev-getting-started.md)의 안내서에서 만든 GitHub 프로젝트를 로컬로 복제하고 원하는 편집기에서 엽니다.

   * 여기에서 Microsoft 코드는 설명 목적으로 사용되었습니다.

   ![프로젝트 복제](assets/create-block/clone.png)

1. 프로젝트 루트에 있는 `component-definition.json` 파일을 편집하고 새 인용 블록에 대해 다음 정의를 추가한 후 파일을 저장합니다.

>[!BEGINTABS]

>[!TAB JSON 예]

```json
{
  "title": "Quote",
  "id": "quote",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "Quote",
          "model": "quote",
          "quote": "<p>Think, McFly! Think!</p>",
          "author": "Biff Tannen"
        }
      }
    }
  }
}
```

>[!TAB 스크린샷]

![component-definitions.json 파일을 편집하여 인용 블록 정의](assets/create-block/component-definitions.png)

>[!ENDTABS]

1. 프로젝트 루트에 있는 `component-models.json` 파일을 편집하고 새 인용 블록에 대해 다음 [모델 정의](/help/implementing/universal-editor/field-types.md#model-structure)를 추가한 후 파일을 저장합니다.

   * 콘텐츠 모델을 만들 때 고려해야 할 중요 사항에 대한 자세한 내용은 [Edge Delivery Services 프로젝트를 사용한 AEM 작성을 위한 콘텐츠 모델링](/help/edge/aem-authoring/content-modeling.md) 문서를 참조하십시오.

>[!BEGINTABS]

>[!TAB JSON 예]

```json
{
  "id": "quote",
  "fields": [
     {
       "component": "text-area",
       "name": "quote",
       "value": "",
       "label": "Quote",
       "valueType": "string"
     },
     {
       "component": "text-input",
       "valueType": "string",
       "name": "author",
       "label": "Author",
       "value": ""
     }
   ]
}
```

>[!TAB 스크린샷]

![component-models.json 파일을 편집하여 인용 블록의 모델 정의](assets/create-block/component-models.png)

>[!ENDTABS]

1. 프로젝트 루트에 있는 `component-filters.json` 파일을 편집하고 [필터 정의](/help/implementing/universal-editor/customizing.md#filtering-components)에 인용 블록을 추가하여 해당 블록이 모든 섹션에 추가되도록 허용하고 파일을 저장합니다.

>[!BEGINTABS]

>[!TAB JSON 예]

```json
{
  "id": "section",
  "components": [
    "text",
    "image",
    "button",
    "title",
    "hero",
    "cards",
    "columns",
    "quote"
   ]
}
```

>[!TAB 스크린샷]

![component-filters.json 파일을 편집하여 인용 블록에 대한 필터 정의](assets/create-block/component-filters.png)

>[!ENDTABS]

1. Git을 사용하여 이러한 변경 사항을 `main` 분기에 커밋합니다.

   * `main`에 대한 커밋은 설명 목적으로만 사용됩니다. [모범 사례를 따라](https://www.aem.live/docs/dev-collab-and-good-practices) 실제 프로젝트 작업에 가져오기 요청을 사용합니다.

### 블록으로 콘텐츠 만들기 {#create-content}

이제 기본 인용 블록이 정의되어 샘플 프로젝트에 커밋되었기 때문에 기존 페이지에 인용 블록을 추가할 수 있습니다.

1. 브라우저에서 AEM as a Cloud Service에 로그인합니다. [Sites 콘솔을 사용하여](/help/sites-cloud/authoring/basic-handling.md) [Edge Delivery Services를 사용한 AEM 작성을 위한 개발자 시작 안내서](/help/edge/aem-authoring/edge-dev-getting-started.md)의 안내서에서 만든 사이트로 이동하고 페이지를 선택합니다.

   * 이 경우 `index`는 설명 목적으로 사용됩니다.

   ![Sites 콘솔에서 색인 페이지 선택](assets/create-block/sites-console.png)

1. 콘솔 도구 모음에서 **편집**&#x200B;을 탭하거나 클릭하면 Universal Editor가 열립니다.

   * 페이지를 로드하려면 **Adobe에 로그인**&#x200B;을 탭하거나 클릭하여 Universal Editor에서 AEM에 인증해야 할 수도 있습니다.

1. Universal Editor에서 섹션을 선택합니다. 속성 레일에서 **추가** 아이콘을 탭하거나 클릭한 다음, 메뉴에서 새 **인용** 블록을 선택합니다.

   * **추가** 아이콘은 더하기 기호입니다.
   * 선택한 오브젝트의 파란색 윤곽선에 **섹션**&#x200B;이라는 레이블이 지정된 탭이 있으면 섹션이 선택된 것입니다.
   * 이 예에서는 **Lorem Ipsum** 제목 약간 위를 탭하거나 클릭하면 제목과 lorem ipsum 텍스트가 포함된 섹션이 선택됩니다.

   ![Universal Editor에서 섹션 선택](assets/create-block/add-quote-block.png)

1. 페이지가 다시 로드되고 `component-definitions.json` 파일에 지정된 기본 콘텐츠와 함께 선택한 섹션의 아래쪽에 인용 블록이 추가됩니다.

   * 인용 블록은 내부 또는 속성 레일에서 다른 블록처럼 선택하고 편집할 수 있습니다.
   * 추가 단계에서 스타일링이 적용됩니다.

   ![선택한 섹션에 새 인용 블록이 있는 페이지](assets/create-block/quote-added.png)

1. 인용 콘텐츠가 만족스러우면 Universal Editor 도구 모음의 **게시** 버튼을 탭하거나 클릭하여 페이지를 게시할 수 있습니다.

1. 게시된 페이지로 이동하여 콘텐츠가 게시되었는지 확인합니다. 링크는 `https://<branch>--<repo>--<owner>.hlx.page`와 유사합니다.

   ![게시된 인용](assets/create-block/quote-published.png)

### 블록 스타일 지정 {#style-block}

작동하는 인용 블록이 있으므로 여기에 스타일을 적용할 수 있습니다.

1. 프로젝트 편집기로 돌아갑니다.

1. `blocks` 폴더 아래에 `quote` 폴더를 만듭니다.

   ![인용 폴더 만들기](assets/create-block/new-folder.png)

1. 새 `quote` 폴더에서 다음 JavaScript를 추가하여 `quote.js` 파일을 추가하고 블록 장식을 구현한 다음 파일을 저장합니다.

>[!BEGINTABS]

>[!TAB JavaScript 예]

```javascript
export default function decorate(block) {
  const [quoteWrapper] = block.children;
 
  const blockquote = document.createElement('blockquote');
  blockquote.textContent = quoteWrapper.textContent.trim();
  quoteWrapper.replaceChildren(blockquote);
}
```

>[!TAB 스크린샷]

![JavaScript 추가하여 블록 장식](assets/create-block/quote-js.png)

>[!ENDTABS]

1. `quote` 폴더에서 다음 CSS 코드를 추가하여 `quote.css` 파일을 추가고 블록 스타일링을 정의한 다음 파일을 저장합니다.

>[!BEGINTABS]

>[!TAB CSS 예]

```css
.block.quote {
    background-color: #ccc;
    padding: 0 0 24px;
    display: flex;
    flex-direction: column;
    margin: 1rem 0;
}
 
.block.quote blockquote {
    margin: 16px;
    text-indent: 0;
}
 
.block.quote > div:last-child > div {
    margin: 0 16px;
    font-size: small;
    font-style: italic;
    position: relative;
}
 
.block.quote > div:last-child > div::after {
    content: "";
    display: block;
    position: absolute;
    left: 0;
    bottom: -8px;
    height: 5px;
    width: 30px;
    background-color: darkgray;
}
```

>[!TAB 스크린샷]

![CSS를 추가하여 블록 스타일 정의](assets/create-block/quote-css.png)

>[!ENDTABS]

1. Git을 사용하여 이러한 변경 사항을 `main` 분기에 커밋합니다.

   * `main`에 대한 커밋은 설명 목적으로만 사용됩니다. [모범 사례를 따라](https://www.aem.live/docs/dev-collab-and-good-practices) 실제 프로젝트 작업에 가져오기 요청을 사용합니다.

1. 프로젝트 페이지를 편집하던 Universal Editor의 브라우저 탭으로 돌아가 페이지를 다시 로드하여 스타일이 지정된 블록을 확인합니다.

1. 페이지에서 현재 스타일이 지정된 인용 블록을 확인합니다.

   ![Universal Editor의 스타일이 지정된 인용 블록](assets/create-block/quote-styled.png)

1. 게시된 페이지로 이동하여 변경 사항이 프로덕션에 푸시되었는지 확인합니다. 링크는 `https://<branch>--<repo>--<owner>.hlx.page`와 유사합니다.

   ![게시되고 스타일이 지정된 인용 블록](assets/create-block/quote-styled-published.png)

축하합니다! 이제 완벽하게 작동하고 스타일이 지정된 인용 블록이 있습니다. 이 예를 자신만의 프로젝트별 블록을 설계하기 위한 기초로 사용할 수 있습니다.

### 블록 옵션 {#block-options}

특정 상황에 따라 블록이 약간 다르게 보이거나 동작해야 하지만 그 자체로는 새 블록이 될 만큼 차이가 없다면 작성자가 다음 중 하나를 선택하도록 할 수 있습니다. [차단 옵션을 사용할 수 있습니다.](content-modeling.md#type-inference)

를 추가하여 `classes` 속성을 블록, 단순 블록의 경우 테이블 헤더에서 렌더링된 속성 또는 컨테이너 블록의 항목에 대한 값 목록으로 렌더링됩니다.

```json
{
  "id": "simpleMarquee",
  "fields": [
    {
      "component": "text",
      "valueType": "string",
      "name": "marqueeText",
      "value": "",
      "label": "Marquee text",
      "description": "The text you want shown in your marquee"
    },
    {
      "component": "select",
      "name": "classes",
      "value": "",
      "label": "Background Color",
      "description": "The marquee background color",
      "valueType": "string",
      "options": [
        {
          "name": "Red",
          "value": "bg-red"
        },
        {
          "name": "Green",
          "value": "bg-green"
        },
        {
          "name": "Blue",
          "value": "bg-blue"
        }
      ]
    }
  ]
}
```

## 다른 작업 분기 사용 {#other-branches}

이 안내서에서는 단순성을 위해 `main` 분기에 바로 커밋하도록 하였습니다. 샘플 저장소에서 실험하는 경우 이는 일반적으로 문제가 되지 않습니다. 실제 작업에서는 `main`으로 병합하기 전 가져오기 요청을 통해 다른 분기에서 개발하고 모든 변경 사항을 검토하여 [개발 모범 사례를 따라야 합니다](https://www.aem.live/docs/dev-collab-and-good-practices).

`main` 분기에서 개발하지 않으면 Universal Editor 위치 표시줄에서 `?ref=<branch>`를 추가하여 분기에서 페이지를 로드할 수 있습니다. 프로젝트 미리보기 또는 라이브 URL(예: `https://<branch>--<repo>--<owner>.hlx.page`)에 사용되는 것처럼 `<branch>`는 분기 이름입니다.

새 모델을 사용한 콘텐츠 게시는 모델이 `main` 분기에 병합된 경우에만 지원됩니다.

## 다음 단계 {#next-steps}

블록을 생성하는 방법을 알았으므로 린 개발자 경험을 달성하기 위해 의미론적 방식으로 콘텐츠의 모델링 방법을 이해하는 것이 중요합니다.

Edge Delivery Services 프로젝트를 사용한 AEM 작성을 위한 콘텐츠 모델링의 작동 방식을 알아보려면 [Edge Delivery Services 프로젝트를 사용한 AEM 작성을 위한 컨텐츠 모델링](/help/edge/aem-authoring/content-modeling.md) 문서를 참조하십시오.

>[!TIP]
>
>AEM as a Cloud Service를 콘텐츠 소스로 사용하여 AEM 작성에 활성화된 새로운 Edge Delivery Services 프로젝트를 만드는 방법에 대한 전체 연습을 보려면 [이 AEM GEM 웨비나](https://experienceleague.adobe.com/en/docs/events/experience-manager-gems-recordings/gems2024/aem-authoring-and-edge-delivery)를 시청하십시오.
