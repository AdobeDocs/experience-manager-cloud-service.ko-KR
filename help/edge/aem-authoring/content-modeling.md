---
title: Edge Delivery Services 프로젝트를 사용한 AEM 작성을 위한 콘텐츠 모델링
description: Edge Delivery Services 프로젝트를 통한 AEM 작성 시 콘텐츠 모델링의 작동 방식과 자체 콘텐츠의 모델링 방법에 대해 알아보십시오.
exl-id: e68b09c5-4778-4932-8c40-84693db892fd
source-git-commit: 11f721b4a617c99e30329d7196f42d7b48067f1b
workflow-type: tm+mt
source-wordcount: '2233'
ht-degree: 100%

---


# Edge Delivery Services 프로젝트를 사용한 AEM 작성을 위한 콘텐츠 모델링 {#content-modeling}

Edge Delivery Services 프로젝트를 통한 AEM 작성 시 콘텐츠 모델링의 작동 방식과 자체 콘텐츠의 모델링 방법에 대해 알아보십시오.

## 사전 요구 사항 {#prerequisites}

Edge Delivery Services를 통한 AEM 작성을 사용한 프로젝트는 콘텐츠 소스 또는 [작성 방법](/help/edge/aem-authoring/authoring.md)에 관계없이 기타 Edge Delivery Services 프로젝트의 메커니즘 대부분을 상속합니다.

프로젝트의 콘텐츠 모델링을 시작하기 전에 먼저 다음 문서를 읽어보십시오.

* [시작하기 - 개발자 튜토리얼](/help/edge/developer/tutorial.md)
* [마크업, 섹션, 블록 및 자동 차단](/help/edge/developer/markup-sections-blocks.md)
* [컬렉션 차단](/help/edge/developer/block-collection.md)

콘텐츠 소스에 구애받지 않는 방식으로 작동하는 강력한 콘텐츠 모델을 마련하려면 이러한 개념을 이해하는 것이 필수입니다. 이 문서에서는 AEM 작성을 위해 특별히 구현된 메커니즘에 대한 세부 정보를 제공합니다.

## 기본 콘텐츠 {#default-content}

**기본 콘텐츠**&#x200B;는 작성자가 다른 의미 체계를 추가하지 않고 직관적으로 페이지에 넣을 콘텐츠입니다. 여기에는 텍스트, 제목, 링크 및 이미지가 포함됩니다. 이러한 콘텐츠는 기능과 목적 면에서 설명이 따로 필요하지 않습니다.

AEM에서 이 콘텐츠는 Markdown 및 HTML로 직렬화할 수 있는 모든 것을 포함하는 매우 간단하고 사전 정의된 모델이 있는 구성 요소로 구현됩니다.

* **텍스트**: 서식 있는 텍스트(목록 요소 및 강조 텍스트 또는 기울임체 텍스트 포함)
* **제목**: 텍스트, 유형(h1-h6)
* **이미지**: 소스, 설명
* **버튼**: 텍스트, 제목, URL, 유형(기본, 주, 보조)

이러한 구성 요소의 모델은 [Edge Delivery Services를 사용한 AEM 작성을 위한 상용구](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json#L2-L112)의 일부입니다.

## 블록 {#blocks}

블록은 특정 스타일과 기능을 갖춘 더욱 풍부한 콘텐츠를 만드는 데 사용됩니다. 기본 콘텐츠와 달리 블록에는 추가 의미 체계가 필요합니다. 블록은 AEM 페이지 편집기의 [구성 요소에 비유할 수 있습니다.](/help/implementing/developing/components/overview.md)

블록은 기본적으로 JavaScript로 장식되고 스타일시트로 스타일이 지정된 콘텐츠 조각입니다.

### 블록 모델 정의 {#model-definition}

Edge Delivery Services를 통한 AEM 작성을 사용할 때 작성자에게 콘텐츠 생성을 위한 인터페이스를 제공하기 위해 블록 콘텐츠를 명시적으로 모델링해야 합니다. 기본적으로 작성 UI가 블록을 기반으로 작성자에게 제시할 옵션을 알 수 있도록 모델을 만들어야 합니다.

[`component-models.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json) 파일은 블록 모델을 정의합니다. 구성 요소 모델에 정의된 필드는 AEM 속성으로 유지되고 블록을 구성하는 테이블의 셀로 렌더링됩니다.

```json
{
  "id": "hero",
  "fields": [
    {
      "component": "reference",
      "valueType": "string",
      "name": "image",
      "label": "Image",
      "multi": false
    },
    {
      "component": "text-input",
      "valueType": "string",
      "name": "imageAlt",
      "label": "Alt",
      "value": ""
    },
    {
      "component": "text-area",
      "name": "text",
      "value": "",
      "label": "Text",
      "valueType": "string"
    }
  ]
}
```

모든 블록에 모델이 있어야 하는 것은 아닙니다. 일부 블록은 단순히 하위 목록을 위한 [컨테이너](#container)이며, 각 하위 항목에는 자체 모델이 있습니다.

또한 Universal Editor를 사용하여 어떤 블록이 존재하고 페이지에 추가될 수 있는지를 정의해야 합니다. [`component-definitions.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) 파일에는 Universal Editor에서 사용할 수 있는 구성 요소가 나열되어 있습니다.

```json
{
  "title": "Hero",
  "id": "hero",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "Hero",
          "model": "hero"
        }
      }
    }
  }
}
```

여러 블록에 하나의 모델을 사용할 수 있습니다. 예를 들어 일부 블록은 텍스트와 이미지를 정의하는 모델을 공유할 수 있습니다.

각 블록에 대해 개발자는 다음 작업을 수행합니다.

* AEM에서 블록 논리의 일반 구현인 `core/franklin/components/block/v1/block` 리소스 유형을 사용해야 합니다.
* 블록의 테이블 헤더에 렌더링될 블록 이름을 정의해야 합니다.
   * 블록 이름은 블록을 장식하는 데 적합한 스타일과 스크립트를 가져오는 데 사용됩니다.
* [모델 ID](/help/implementing/universal-editor/field-types.md#model-structure)를 정의할 수 있습니다.
   * 모델 ID는 속성 레일에서 작성자가 사용할 수 있는 필드를 정의하는 구성 요소 모델에 대한 참조입니다.
* [필터 ID](/help/implementing/universal-editor/customizing.md#filtering-components)를 정의할 수 있습니다.
   * 필터 ID는 구성 요소 필터에 대한 참조이며, 이를 통해 작성 동작을 변경할 수 있습니다(예: 블록이나 섹션에 추가할 수 있는 하위 요소 또는 활성화되는 RTE 기능 제한).

페이지에 블록이 추가되면 이 모든 정보가 AEM에 저장됩니다. 리소스 유형이나 블록 이름이 누락되면 해당 블록이 페이지에 렌더링되지 않습니다.

>[!WARNING]
>
>사용자 정의 AEM 구성 요소를 구현하는 것이 가능하지만 필수 또는 권장 사항은 아닙니다. AEM에서 제공하는 Edge Delivery Services용 구성 요소는 충분하며, 손쉽게 개발하도록 특정 가드레일을 제공합니다.
>
>AEM에서 제공하는 구성 요소는 마크업을 렌더링하며, 이 마크업은 Edge Delivery Services에 게시할 때 [helix-html2md](https://github.com/adobe/helix-html2md)에서 또는 Universal Editor에서 페이지를 로드할 때 [aem.js](https://github.com/adobe/aem-boilerplate/blob/main/scripts/aem.js)에서 사용할 수 있습니다. 마크업은 AEM과 시스템 내 다른 부분 간의 안정적인 계약이며, 사용자 정의가 허용되지 않습니다. 이러한 이유로 프로젝트에서 구성 요소를 변경해서는 안 되며 사용자 정의 구성 요소를 사용해서도 안 됩니다.

### 블록 구조 {#block-structure}

블록 속성은 [구성 요소 모델에 정의되고](#model-definition) AEM에서도 그대로 유지됩니다. 속성은 블록 테이블과 같은 구조에서 셀로 렌더링됩니다.

#### 단순 블록 {#simple}

가장 간단한 형태의 블록은 속성이 모델에 정의된 순서대로 단일 행/열의 각 속성을 렌더링합니다.

다음 예에서는 모델에서 이미지가 먼저 정의되고 두 번째로 텍스트가 정의됩니다. 따라서 이미지가 먼저 렌더링되고 텍스트가 두 번째로 렌더링됩니다.

>[!BEGINTABS]

>[!TAB 데이터]

```json
{
  "name": "Hero",
  "model": "hero",
  "image": "/content/dam/image.png",
  "imageAlt": "Helix - a shape like a corkscrew",
  "text": "<h1>Welcome to AEM</h1>"
}
```

>[!TAB 마크업]

```html
<div class="hero">
  <div>
    <div>
      <picture>
        <img src="/content/dam/image.png" alt="Helix - a shape like a corkscrew">
      </picture>
    </div>
  </div>
  <div>
    <div>
      <h1>Welcome to AEM</h1>
    </div>
  </div>
</div>
```

>[!TAB 표]

```text
+---------------------------------------------+
| Hero                                        |
+=============================================+
| ![Helix - a shape like a corkscrew][image0] |
+---------------------------------------------+
| # Welcome to AEM                            |
+---------------------------------------------+
```

>[!ENDTABS]

일부 값 유형을 통해 마크업의 의미 체계를 유추할 수 있으며 속성은 단일 셀에 결합된다는 것을 알 수 있습니다. 이 비헤이비어는 [유형 추론](#type-inference) 섹션에 설명되어 있습니다.

#### 키-값 블록 {#key-value}

대부분의 경우 렌더링된 의미 체계 마크업을 장식하고, CSS 클래스 이름을 추가하고, 새 노드를 추가하거나 DOM에서 이동하고, 스타일을 적용하는 것이 좋습니다.

다른 경우에는 블록이 키-값 쌍과 같은 구성으로 읽혀집니다.

이에 대한 예는 [섹션 메타데이터입니다.](/help/edge/developer/markup-sections-blocks.md#sections) 이 사용 사례에서는 블록을 키-값 쌍 테이블로 렌더링하도록 구성할 수 있습니다. 자세한 내용은 [섹션 및 섹션 메타데이터](#sections-metadata) 섹션을 참조하십시오.

>[!BEGINTABS]

>[!TAB 데이터]

```json
{
  "name": "Featured Articles",
  "model": "spreadsheet-input",
  "key-value": true,
  "source": "/content/site/articles.json",
  "keywords": ['Developer','Courses'],
  "limit": 4
}
```

>[!TAB 마크업]

```html
<div class="featured-articles">
  <div>
    <div>source</div>
    <div><a href="/content/site/articles.json">/content/site/articles.json</a></div>
  </div>
  <div>
    <div>keywords</div>
    <div>Developer,Courses</div>
  <div>
  <div>
    <div>limit</div>
    <div>4</div>
  </div>
</div>
```

>[!TAB 표]

```text
+-----------------------------------------------------------------------+
| Featured Articles                                                     |
+=======================================================================+
| source   | [/content/site/articles.json](/content/site/articles.json) |
+-----------------------------------------------------------------------+
| keywords | Developer,Courses                                          |
+-----------------------------------------------------------------------+
| limit    | 4                                                          |
+-----------------------------------------------------------------------+
```

>[!ENDTABS]

#### 컨테이너 블록 {#container}

이전 구조에는 모두 속성 목록이라는 단일 차원이 있습니다. 컨테이너 블록을 사용하면 하위 항목(일반적으로 동일한 유형 또는 모델)를 추가할 수 있으므로 2차원이 됩니다. 이 블록은 먼저 단일 열이 있는 행으로 렌더링되는 자체 속성을 계속 지원합니다. 단, 각 항목이 행으로 렌더링되고 각 속성이 해당 행 내의 열로 렌더링되는 하위 항목 추가도 허용됩니다.

다음 예에서 블록은 연결된 아이콘 목록을 하위 항목으로 허용하며, 연결된 각 아이콘에는 이미지와 링크가 있습니다. 필터 구성을 참조하도록 블록 데이터에 설정된 [필터 ID](/help/implementing/universal-editor/customizing.md#filtering-components)를 확인하십시오.

>[!BEGINTABS]

>[!TAB 데이터]

```json
{
  "name": "Our Partners",
  "model": "text-only",
  "filter": "our-partners",
  "text": "<p>Our community of partners is ...</p>",
  "item_0": {
    "model": "linked-icon",
    "image": "/content/dam/partners/foo.png",
    "imageAlt": "Icon of Foo",
    "link": "https://foo.com/"
  },
  "item_1": {
    "model": "linked-icon"
    "image": "/content/dam/partners/bar.png",
    "imageAlt": "Icon of Bar",
    "link": "https://bar.com"
  }
}
```

>[!TAB 마크업]

```html
<div class="our-partners">
  <div>
    <div>
        Our community of partners is ...
    </div>
  </div>
  <div>
    <div>
      <picture>
         <img src="/content/dam/partners/foo.png" alt="Icon of Foo">
      </picture>
    </div>
    <div>
      <a href="https://foo.com">https://foo.com</a>
    </div>
  </div>
  <div>
    <div>
      <picture>
         <img src="/content/dam/partners/bar.png" alt="Icon of Bar">
      </picture>
    </div>
    <div>
      <a href="https://bar.com">https://bar.com</a>
    </div>
  </div>
</div>
```

>[!TAB 표]

```text
+------------------------------------------------------------ +
| Our Partners                                                |
+=============================================================+
| Our community of partners is ...                            |
+-------------------------------------------------------------+
| ![Icon of Foo][image0] | [https://foo.com](https://foo.com) |
+-------------------------------------------------------------+
| ![Icon of Bar][image1] | [https://bar.com](https://bar.com) |
+-------------------------------------------------------------+
```

>[!ENDTABS]

### 블록의 의미 체계 콘텐츠 모델 만들기 {#creating-content-models}

[블록 구조의 메커니즘을 설명하면](#block-structure) AEM에 유지된 콘텐츠를 일대일로 게재 계층에 매핑하는 콘텐츠 모델을 만들 수 있습니다.

모든 프로젝트 초기에는 모든 블록에 대해 콘텐츠 모델을 신중하게 고려해야 합니다. 작성자가 블록 구현 및 스타일을 재사용하는 동안 콘텐츠 소스 및 작성 경험을 전환하거나 결합할 수 있도록 콘텐츠 소스 및 작성 경험과 독립적이어야 합니다. 자세한 내용 및 일반 지침은 [David&#39;s Model(2번)에서 확인할 수 있습니다.](https://www.aem.live/docs/davidsmodel) 보다 구체적으로 [블록 컬렉션](/help/edge/developer/block-collection.md)에는 일반적인 사용자 인터페이스 패턴의 특정 사용 사례에 대한 광범위한 콘텐츠 모델 세트가 포함되어 있습니다.

Edge Delivery Services를 사용한 AEM 작성의 경우, 서식 있는 텍스트와 같이 컨텍스트 내에서 의미 체계 마크업을 편집하는 대신 여러 필드로 구성된 양식으로 정보를 작성할 때 강력한 의미 체계 콘텐츠 모델을 제공하는 방법에 대해 의문을 제기합니다.

이 문제를 해결하기 위해 매력적인 콘텐츠 모델을 손쉽게 만들 수 있는 세 가지 방법이 있습니다.

* [유형 추론](#type-inference)
* [필드 축소](#field-collapse)
* [요소 그룹화](#element-grouping)

>[!NOTE]
>
>블록 구현은 콘텐츠를 분해하고 블록을 클라이언트측에서 렌더링된 DOM으로 대체할 수 있습니다. 개발자에게는 가능하고 직관적이나 Edge Delivery Services의 모범 사례는 아닙니다.

#### 유형 추론 {#type-inference}

일부 값의 경우, 값 자체에서 의미 체계 의미를 추론할 수 있습니다. 해당 값은 다음과 같습니다.

* **이미지** - AEM의 리소스에 대한 참조가 `image/`로 시작되는 MIME 유형이 있는 자산인 경우, 참조는 `<picture><img src="${reference}"></picture>`로 렌더링됩니다.
* **링크** - 참조가 AEM에 있고 이미지가 아닌 경우나 값이 `https?://` 또는 `#`으로 시작하는 경우, 참조는 `<a href="${reference}">${reference}</a>`로 렌더링됩니다.
* **서식 있는 텍스트** - 트리밍된 값이 단락으로 시작되는 경우(`p`, `ul`, `ol`, `h1`-`h6` 등), 값은 서식 있는 텍스트로 렌더링됩니다.
* **Class Names** - `classes` 속성은 블록 옵션으로 처리되고 [단순 블록](#simple)의 경우 테이블 헤더에 렌더링되거나 [컨테이너 블록의 항목에 대한 값 목록으로 렌더링됩니다.](#container)
* **값 목록** - 값이 다중 값 속성이고 첫 번째 값이 이전 값이 아닌 경우, 모든 값은 쉼표로 구분된 목록으로 연결됩니다.

다른 모든 내용은 일반 텍스트로 렌더링됩니다.

#### 필드 축소 {#field-collapse}

필드 축소는 접미사(`Title`, `Type`, `MimeType`, `Alt` 및 `Text`)(모두 대소문자 구분)를 사용하는 명명 규칙을 기준으로 여러 필드 값을 단일 의미 체계 요소로 결합하는 메커니즘입니다. 해당 접미사로 끝나는 모든 속성은 값으로 간주되지 않고, 오히려 다른 속성의 속성으로 간주됩니다.

##### 이미지 {#image-collapse}

>[!BEGINTABS]

>[!TAB 데이터]

```json
{
  "image": "/content/dam/red-car.png",
  "imageAlt: "A red card on a road"
}
```

>[!TAB 마크업]

```html
<picture>
  <img src="/content/dam/red-car.png" alt="A red car on a road">
</picture>
```

>[!TAB 표]

```text
![A red car on a road][image0]
```

>[!ENDTABS]

##### 링크 및 버튼 {#links-buttons-collapse}

>[!BEGINTABS]

>[!TAB 데이터]

```json
{
  "link": "https://www.adobe.com",
  "linkTitle": "Navigate to adobe.com",
  "linkText": "adobe.com",
  "linkType": "primary"
}
```

>[!TAB 마크업]

`linkType` 또는 `linkType=default` 없음

```html
<a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
```

`linkType=primary`

```html
<strong>
  <a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
</strong>
```

`linkType=secondary`

```html
<em>
  <a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
</em>
```

>[!TAB 표]

```text
[adobe.com](https://www.adobe.com "Navigate to adobe.com")
**[adobe.com](https://www.adobe.com "Navigate to adobe.com")**
_[adobe.com](https://www.adobe.com "Navigate to adobe.com")_
```

>[!ENDTABS]

##### 제목 {#headings-collapse}

>[!BEGINTABS]

>[!TAB 데이터]

```json
{
  "heading": "Getting started",
  "headingType": "h2"
}
```

>[!TAB 마크업]

```html
<h2>Getting started</h2>
```

>[!TAB 표]

```text
## Getting started
```

>[!ENDTABS]

#### 요소 그룹화 {#element-grouping}

[필드 축소](#field-collapse)가 여러 속성을 하나의 의미 체계 요소로 결합하는 것이라면, 요소 그룹화는 여러 의미 체계 요소를 단일 셀로 연결하는 것입니다. 이는 특히 작성자가 만들 수 있는 요소의 유형과 수를 제한해야 하는 사용 사례에 유용합니다.

예를 들어 티저 구성 요소는 작성자는 최대 두 개의 클릭 유도 버튼과 결합된 부제, 제목, 단일 단락 설명만 만들도록 허용할 수 있습니다. 이러한 요소를 함께 그룹화하면 추가 작업 없이 스타일을 지정할 수 있는 의미 체계 마크업이 생성됩니다.

요소 그룹화에서는 그룹 이름이 밑줄로 그룹의 각 속성과 구분되는 명명 규칙을 사용합니다. 그룹 속성의 필드 축소는 앞서 설명한 대로 작동합니다.

>[!BEGINTABS]

>[!TAB 데이터]

```json
{
  "name": "teaser",
  "model": "teaser",
  "image": "/content/dam/teaser-background.png",
  "imageAlt": "A group of people sitting on a stage",
  "teaserText_subtitle": "Adobe Experience Cloud"
  "teaserText_title": "Meet the Experts"
  "teaserText_titleType": "h2"
  "teaserText_description": "<p>Join us in this ask me everything session...</p>"
  "teaserText_cta1": "https://link.to/more-details",
  "teaserText_cta1Text": "More Details"
  "teaserText_cta2": "https://link.to/sign-up",
  "teaserText_cta2Text": "RSVP",
  "teaserText_cta2Type": "primary"
}
```

>[!TAB 마크업]

```html
<div class="teaser">
  <div>
    <div>
      <picture>
        <img src="/content/dam/teaser-background.png" alt="A group of people sitting on a stage">
      </picture>
    </div>
  </div>
  <div>
    <div>
      <p>Adobe Experience Cloud</p>
      <h2>Meet the Experts</h2>
      <p>Join us in this ask me everything session ...</p>
      <p><a href="https://link.to/more-details">More Details</a></p>
      <p><strong><a href="https://link.to/sign-up">RSVP</a></strong></p>
    </div>
  </div>
</div>
```

>[!TAB 표]

```text
+-------------------------------------------------+
| Teaser                                          |
+=================================================+
| ![A group of people sitting on a stage][image0] |
+-------------------------------------------------+
| Adobe Experience Cloud                          |
| ## Welcome to AEM                               |
| Join us in this ask me everything session ...   |
| [More Details](https://link.to/more-details)    |
| [RSVP](https://link.to/sign-up)                 |
+-------------------------------------------------+
```

>[!ENDTABS]

## 섹션 및 섹션 메타데이터 {#sections-metadata}

개발자가 여러 [블록](#blocks)을 정의하고 모델링할 수 있는 것과 동일한 방식으로 서로 다른 섹션을 정의할 수 있습니다.

Edge Delivery Services의 콘텐츠 모델은 섹션에 포함된 기본 콘텐츠 또는 블록인 단일 수준의 중첩만 의도적으로 허용합니다. 즉, 다른 구성 요소를 포함할 수 있는 보다 복잡한 시각적 구성 요소를 가지려면 섹션으로 모델링하고 자동 차단 클라이언트측을 사용하여 함께 결합해야 합니다. 이에 대한 일반적인 예로는 탭과 아코디언과 같이 접을 수 있는 섹션이 있습니다.

섹션은 블록과 동일한 방식으로 정의할 수 있지만, `core/franklin/components/section/v1/section`의 리소스 유형을 사용합니다. 섹션에는 이름과 [Universal Editor](/help/implementing/universal-editor/introduction.md)에서만 사용하는 [필터 ID](/help/implementing/universal-editor/customizing.md#filtering-components) 및 섹션 메타데이터를 렌더링하는 데 사용하는 [모델 ID](/help/implementing/universal-editor/field-types.md#model-structure)가 있습니다. 모델은 이러한 방식으로 섹션 메타데이터 블록의 모델이며, 비어 있지 않은 경우 키-값 블록으로 섹션에 자동 추가됩니다.

기본 섹션의 [모델 ID](/help/implementing/universal-editor/field-types.md#model-structure) 및 [필터 ID](/help/implementing/universal-editor/customizing.md#filtering-components)는 `section`입니다. 기본 섹션의 비헤이비어를 변경하는 데 사용할 수 있습니다. 다음 예에서는 섹션 메타데이터 모델에 일부 스타일과 배경 이미지를 추가합니다.

```json
{
  "id": "section",
  "fields": [
    {
      "component": "multiselect",
      "name": "style",
      "value": "",
      "label": "Style",
      "valueType": "string",
      "options": [
        {
          "name": "Fade in Background",
          "value": "fade-in"
        },
        {
          "name": "Highlight",
          "value": "highlight"
        }
      ]
    },
    {
      "component": "reference",
      "valueType": "string",
      "name": "background",
      "label": "Image",
      "multi": false
    }
  ]
}
```

다음 예에서는 자동 차단 중에 탭 제목 데이터 속성이 있는 연속 섹션을 탭 블록으로 결합하여 탭 블록을 만드는 데 사용할 수 있는 탭 섹션을 정의합니다.

```json
{
  "title": "Tab",
  "id": "tab",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/section/v1/section",
        "template": {
          "name": "Tab",
          "model": "tab",
          "filter": "section"
        }
      }
    }
  }
}
```

## 페이지 메타데이터 {#page-metadata}

문서에는 페이지 [메타데이터 블록이 있는데,](https://www.aem.live/developer/block-collection/metadata) 이를 사용하여 페이지의 `<head>`에서 `<meta>` 렌더링된 요소를 정의합니다. AEM as a Cloud Service 페이지의 페이지 속성은 Edge Delivery Services에 기본 제공되는 페이지 속성에 매핑됩니다(예: `title`, `description`, `keywords` 등).

자체 메타데이터를 정의하는 방법을 자세히 살펴보기 전에 다음 문서를 검토하여 페이지 메타데이터의 개념을 먼저 이해하시기 바랍니다.

* [메타데이터](https://www.aem.live/developer/block-collection/metadata)
* [대량 메타데이터](/help/edge/docs/bulk-metadata.md)

두 가지 방법으로 추가 페이지 메타데이터를 정의할 수도 있습니다.

### 메타데이터 스프레드시트 {#metadata-spreadsheets}

AEM as a Cloud Service에서 테이블과 같은 방식의 경로별 또는 경로 패턴별로 메타데이터를 정의할 수 있습니다. Excel 또는 Google Sheets와 유사한 테이블 형식 데이터에 대한 작성 UI가 있습니다.

이러한 테이블을 만들려면 페이지를 만들고 Sites 콘솔에서 메타데이터 템플릿을 사용합니다.

스프레드시트의 페이지 속성에서 URL과 함께 필요한 메타데이터 필드를 정의합니다. 그런 다음 페이지 경로 또는 페이지 경로 패턴별로 메타데이터를 추가합니다.

게시하기 전에 스프레드시트가 경로 매핑에도 추가되었는지 확인하십시오.

```json
{
  "mappings": [
    "/content/site/:/",
    "/content/site/metadata:/metadata.json"
  ]
}
```

### 페이지 속성 {#page-properties}

AEM에서 사용할 수 있는 기본 페이지 속성 중 다수는 문서의 해당 페이지 메타데이터에 매핑됩니다. 여기에는 예를 들어 `title`, `description`, `robots` `canonical url` 또는 `keywords`가 포함됩니다. 일부 AEM 관련 속성도 사용할 수 있습니다.

* `cq:lastModified` - `modified-time`(ISO8601 형식)
* 문서가 마지막으로 게시된 시간 - `published-time`(ISO8601 형식)
* `cq:tags` - `cq-tags`(태그 ID를 쉼표로 구분한 목록)

작성자에게 AEM Sites 페이지 속성 대화 상자의 탭으로 제공되는 사용자 정의 페이지 메타데이터에 대한 구성 요소 모델을 정의할 수도 있습니다.

이렇게 하려면 ID `page-metadata`를 사용하여 구성 요소 모델을 만듭니다.

```json
{
  "id": "page-metadata",
  "fields": [
    {
      "component": "text",
      "name": "theme",
      "label": "Theme"
    }
  ]
}
```

## 다음 단계 {#next-steps}

이제 컨텐츠를 모델링하는 방법을 알았으므로 AEM 작성 프로젝트를 통해 자체 Edge Delivery Services에 대한 블록을 만들 수 있습니다.

Edge Delivery Services 프로젝트를 통해 AEM 작성 시 Universal Editor에 사용하도록 구성된 블록을 만드는 방법을 알아보려면 [Universal Editor에 사용하도록 구성된 블록 만들기](/help/edge/aem-authoring/create-block.md) 문서를 참조하십시오.

이미 블록을 만드는 데 익숙하다면 콘텐츠 작성을 위한 Edge Delivery Services 및 Universal Editor를 사용하여 새로운 Adobe Experience Manager 사이트를 시작하고 실행하기 위한 정보를 확인하려면 [Edge Delivery Services를 사용한 AEM 작성을 위한 개발자 시작 안내서](/help/edge/aem-authoring/edge-dev-getting-started.md) 문서를 참조하십시오.

>[!TIP]
>
>AEM as a Cloud Service를 콘텐츠 소스로 사용하여 AEM 작성에 활성화된 새로운 Edge Delivery Services 프로젝트를 만드는 방법에 대한 전체 연습을 보려면 [이 AEM GEM 웨비나](https://experienceleague.adobe.com/en/docs/events/experience-manager-gems-recordings/gems2024/aem-authoring-and-edge-delivery)를 시청하십시오.

