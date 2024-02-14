---
title: Edge Delivery Services 프로젝트를 사용한 AEM 작성을 위한 콘텐츠 모델링
description: Edge Delivery Services 프로젝트를 사용하여 AEM 작성에 콘텐츠 모델링이 작동하는 방식과 자체 콘텐츠를 모델링하는 방법에 대해 알아봅니다.
source-git-commit: e9c882926baee001170bad2265a1085e03cdbedf
workflow-type: tm+mt
source-wordcount: '2097'
ht-degree: 1%

---


# Edge Delivery Services 프로젝트를 사용한 AEM 작성을 위한 콘텐츠 모델링 {#content-modeling}

Edge Delivery Services 프로젝트를 사용하여 AEM 작성에 콘텐츠 모델링이 작동하는 방식과 자체 콘텐츠를 모델링하는 방법에 대해 알아봅니다.

{{aem-authoring-edge-early-access}}

## 사전 요구 사항 {#prerequisites}

Edge Delivery ServicesEdge Delivery Services 와 함께 AEM 작성을 사용하는 프로젝트는 컨텐츠 소스나 [작성 방법.](/help/edge/authoring.md)

프로젝트에 대한 콘텐츠 모델링을 시작하기 전에 먼저 다음 설명서를 읽어야 합니다.

* [시작하기 - 개발자 튜토리얼](/help/edge/developer/tutorial.md)
* [마크업, 섹션, 블록 및 자동 차단](/help/edge/developer/markup-sections-blocks.md)
* [컬렉션 차단](/help/edge/developer/block-collection.md)

콘텐츠 소스와 관계없는 방식으로 작동하는 매력적인 콘텐츠 모델을 마련하기 위해서는 이러한 개념을 이해하는 것이 필수적입니다. 이 문서에서는 AEM 작성을 위해 특별히 구현된 메커니즘에 대한 세부 사항을 제공합니다.

## 기본 컨텐츠 {#default-content}

**기본 콘텐츠** 는 작성자가 추가 의미 체계를 추가하지 않고 직관적으로 페이지에 넣을 수 있는 콘텐츠입니다. 여기에는 텍스트, 제목, 링크 및 이미지가 포함됩니다. 이와 같은 내용은 그 기능과 목적에 있어 자명한 것이다.

AEM에서 이 콘텐츠는 Markdown 및 HTML으로 일련화할 수 있는 모든 것을 포함하여 매우 간단하고 사전 정의된 모델을 사용하는 구성 요소로 구현됩니다.

* **텍스트**: 리치 텍스트(목록 요소 및 강한 텍스트 또는 기울임꼴 텍스트 포함)
* **제목**: 텍스트, 유형(h1-h6)
* **이미지**: 소스, 설명
* **단추**: 텍스트, 제목, url, 유형 (기본값, 기본, 보조)

이러한 구성 요소의 모델은 [Edge Delivery Services을 사용한 AEM 작성용 표준 템플릿입니다.](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json#L2-L112)

## 블록 {#blocks}

블록은 특정 스타일과 기능으로 더 풍부한 콘텐츠를 만드는 데 사용됩니다. 기본 컨텐츠와 달리 블록은 추가적인 의미 체계를 필요로 하지 않습니다. 블록은 다음과 비유할 수 있습니다. [AEM 구성 요소 를 참조하십시오.](/help/implementing/developing/components/overview.md)

블록은 기본적으로 JavaScript로 데코레이트되고 스타일시트로 스타일링된 콘텐츠 조각입니다.

### 블록 모델 정의 {#model-definition}

Edge Delivery Services에 AEM 작성을 사용하는 경우 작성자에게 컨텐츠를 만들 인터페이스를 제공하기 위해 블록의 컨텐츠를 명시적으로 모델링해야 합니다. 기본적으로 모델을 생성해야 하므로 작성 UI는 블록을 기반으로 작성자에게 제공할 옵션을 알고 있습니다.

다음 [`component-models.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json) 파일은 블록의 모델을 정의합니다. 구성 요소 모델에 정의된 필드는 AEM에서 속성으로 유지되고 블록을 구성하는 테이블에서 셀로 렌더링됩니다.

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

모든 블록에 모델이 있어야 하는 것은 아닙니다. 일부 블록은 [컨테이너](#container) 각 하위 항목에 고유한 모델이 있는 하위 목록의 경우

또한 유니버설 편집기를 사용하여 페이지에 추가할 수 있고 존재하는 블록을 정의해야 합니다. 다음 [`component-definitions.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) 파일은 유니버설 편집기에서 사용할 수 있는 구성 요소를 나열합니다.

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

많은 블록에 대해 하나의 모델을 사용하는 것이 가능하다. 예를 들어, 일부 블록들은 텍스트 및 이미지를 정의하는 모델을 공유할 수 있다.

각 블록에 대해 개발자는

* 다음을 사용해야 합니다. `core/franklin/components/block/v1/block` 리소스 유형(AEM에서 블록 논리의 일반 구현)입니다.
* 블록의 테이블 헤더에 렌더링될 블록 이름을 정의해야 합니다.
   * 블록 이름은 블록을 장식할 적절한 스타일과 스크립트를 가져오는 데 사용됩니다.
* 다음을 정의할 수 있습니다. [모델 ID.](/help/implementing/universal-editor/field-types.md#model-structure)
   * 모델 ID는 구성 요소의 모델에 대한 참조로, 속성 레일에서 작성자가 사용할 수 있는 필드를 정의합니다.
* 다음을 정의할 수 있습니다. [필터 ID.](/help/implementing/universal-editor/customizing.md#filtering-components)
   * 필터 ID는 구성 요소의 필터에 대한 참조로, 블록 또는 섹션에 추가할 수 있는 하위 항목 또는 사용할 수 있는 RTE 기능을 제한하는 방식으로 작성 동작을 변경할 수 있습니다.

이 모든 정보는 블록이 페이지에 추가될 때 AEM에 저장됩니다. 리소스 유형 또는 블록 이름이 누락된 경우 블록이 페이지에서 렌더링되지 않습니다.

>[!WARNING]
>
>가능한 한 사용자 지정 AEM 구성 요소를 구현할 필요가 없거나 구현이 권장되지 않습니다. AEM에서 제공하는 Edge Delivery Services의 구성 요소만으로도 충분하고 특정 가드 레일을 제공하여 개발을 용이하게 합니다.
>
>AEM에서 제공하는 구성 요소는에서 사용할 수 있는 마크업을 렌더링합니다. [helix-html2md](https://github.com/adobe/helix-html2md) Edge Delivery Services에 게시 및 게시하는 사람 [aem.js](https://github.com/adobe/aem-boilerplate/blob/main/scripts/aem.js) 범용 편집기에서 페이지를 로드할 때. 마크업은 AEM과 시스템의 다른 부분 간의 안정적인 계약이며 사용자 정의를 허용하지 않습니다. 따라서 프로젝트는 구성 요소를 변경하지 말아야 하며 사용자 지정 구성 요소를 사용하지 말아야 합니다.

### 블록 구조 {#block-structure}

블록의 속성은 다음과 같습니다 [구성 요소 모델에 정의됨](#model-definition) AEM에서 지속됩니다. 속성은 블록의 표 형식 구조에서 셀로 렌더링됩니다.

#### 단순 블록 {#simple}

가장 간단한 형식에서 블록은 모델에 속성이 정의된 순서대로 각 속성을 단일 행/열로 렌더링합니다.

다음 예제에서는 이미지가 먼저 모델에서 정의되고 텍스트가 두 번째로 정의됩니다. 따라서 이미지가 먼저 렌더링되고 텍스트가 두 번째로 렌더링됩니다.

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

일부 유형의 값을 사용하면 마크업에서 의미 체계를 유추할 수 있으며 속성이 단일 셀에 결합됩니다. 이 동작은 섹션에 설명되어 있습니다 [형식 유추.](#type-inference)

#### 키-값 블록 {#key-value}

대부분의 경우 렌더링된 의미 체계 마크업을 꾸미고, CSS 클래스 이름을 추가하고, 새 노드를 추가하거나 DOM에서 이리저리 이동하고, 스타일을 적용하는 것이 좋습니다.

그러나 다른 경우에는 블록이 키-값 쌍과 같은 구성으로 읽히기도 합니다.

예를 들면 다음과 같습니다. [섹션 메타데이터.](/help/edge/developer/markup-sections-blocks.md#sections) 이 사용 사례에서 블록은 키-값 쌍 테이블로 렌더링하도록 구성될 수 있다. 섹션을 참조하십시오. [섹션 및 섹션 메타데이터](#sections-metadata) 추가 정보.

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

앞의 두 구조는 모두 단일 차원인 등록 정보 목록을 가집니다. 컨테이너 블록은 자식 항목(일반적으로 동일한 유형 또는 모델)을 추가할 수 있으므로 2차원입니다. 이러한 블록은 여전히 단일 열이 있는 행으로 렌더링된 자체 속성을 먼저 지원합니다. 그러나 각 항목이 행으로 렌더링되고 각 속성이 해당 행 내에서 열로 렌더링되는 하위 항목도 추가할 수 있습니다.

다음 예에서 블록은 연결된 아이콘 목록을 하위 항목으로 허용하며, 이때 각 연결된 아이콘에는 이미지와 링크가 있습니다. 다음 사항에 주목합니다. [필터 ID](/help/implementing/universal-editor/customizing.md#filtering-components) 필터 구성을 참조하려면 블록의 데이터를 설정합니다.

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

### 블록에 대한 의미 체계 콘텐츠 모델 만들기 {#creating-content-models}

포함 [블록 구조의 역학 설명,](#block-structure) AEM에서 지속되는 콘텐츠를 게재 계층에 일대일로 매핑하는 콘텐츠 모델을 만들 수 있습니다.

모든 프로젝트의 초기에는 모든 블록에 대해 콘텐츠 모델을 신중하게 고려해야 합니다. 작성자가 블록 구현 및 스타일을 재사용하는 동안 콘텐츠 소스 및 작성 경험을 전환하거나 결합할 수 있도록 하려면 불가지론자여야 합니다. 자세한 내용 및 일반적인 지침은 다음에서 확인할 수 있습니다. [David의 모델 (테이크 2).](https://www.aem.live/docs/davidsmodel) 특히, [블록 컬렉션](/help/edge/developer/block-collection.md) 에는 일반적인 사용자 인터페이스 패턴의 특정 사용 사례에 대한 광범위한 콘텐츠 모델 세트가 포함되어 있습니다.

Edge Delivery Services을 사용하여 AEM을 작성하는 경우 리치 텍스트와 같이 컨텍스트에 맞는 의미 마크업을 편집하지 않고 여러 필드로 구성된 양식으로 정보를 작성할 때 매력적인 의미 콘텐츠 모델을 제공하는 방법에 대한 질문이 제기됩니다.

이 문제를 해결하기 위해 매력적인 콘텐츠 모델을 만드는 데 도움이 되는 세 가지 방법이 있습니다.

* [형식 유추](#type-inference)
* [필드 접기](#field-collapse)
* [요소 그룹화](#element-grouping)

>[!NOTE]
>
>블록 구현은 콘텐츠를 해체하고 블록을 클라이언트측 렌더링 DOM으로 대체할 수 있습니다. 개발자에게 이 작업이 가능하고 직관적이지만 Edge Delivery Services에게 모범 사례는 아닙니다.

#### 형식 유추 {#type-inference}

어떤 가치들에 대해 우리는 가치 그 자체로부터 의미론적 의미를 추론할 수 있다. 이러한 값은 다음과 같습니다.

* **이미지** - AEM의 리소스에 대한 참조가 다음으로 시작하는 MIME 유형의 자산인 경우 `image/`, 참조가 다음과 같이 렌더링됩니다. `<picture><img src="${reference}"></picture>`.
* **링크** - AEM에 참조가 있고 이미지가 아니거나 값이 로 시작하는 경우 `https?://`  또는 `#`, 참조가 다음과 같이 렌더링됩니다. `<a href="${reference}">${reference}</a>` .
* **리치 텍스트** - 트림된 값이 단락으로 시작하는 경우(`p`, `ul`, `ol`, `h1`-`h6`, 등)으로 설정하면 값이 리치 텍스트로 렌더링됩니다.
* **클래스 이름** - `classes` 속성은 블록 옵션으로 처리되고 의 테이블 헤더에 렌더링됩니다. [단순 블록,](#simple) 또는 의 항목에 대한 값 목록으로 [컨테이너 블록.](#container)
* **값 목록** - 값이 다중 값 속성이고 첫 번째 값이 이전 값 중 어느 것도 아닌 경우 모든 값이 쉼표로 구분된 목록으로 연결됩니다.

다른 모든 항목은 일반 텍스트로 렌더링됩니다.

#### 필드 접기 {#field-collapse}

필드 축소란 접미사를 사용하는 명명 규칙을 기반으로 여러 필드 값을 하나의 의미 요소로 결합하는 메커니즘입니다 `Title`, `Type`, `Alt`, 및 `Text` (모든 대/소문자 구분). 이러한 접미사로 끝나는 모든 속성은 값으로 간주되지 않고 다른 속성의 속성으로 간주됩니다.

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

##### 링크 및 단추 {#links-buttons-collapse}

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

아니요 `linkType`, 또는 `linkType=default`

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

While [필드 접기](#field-collapse) 는 여러 속성을 하나의 의미 요소로 결합하는 것이고, 요소 그룹화는 여러 의미 요소를 하나의 셀로 연결하는 것입니다. 이 기능은 작성자가 만들 수 있는 요소의 유형 및 수를 제한해야 하는 사용 사례에 특히 유용합니다.

예를 들어, 티저 구성 요소를 통해 작성자는 최대 2개의 콜 투 액션 버튼과 결합된 자막, 제목 및 단일 단락 설명만 만들 수 있습니다. 이러한 요소를 함께 그룹화하면 추가 작업 없이 스타일을 지정할 수 있는 시맨틱 마크업이 생성됩니다.

요소 그룹화에서는 이름 지정 규칙을 사용합니다. 여기서 그룹 이름은 그룹의 각 속성과 밑줄로 구분됩니다. 그룹 속성의 필드 축소는 이전에 설명한 대로 작동합니다.

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

개발자가 여러 을 정의하고 모델링할 수 있는 것과 동일한 방식입니다 [블록,](#blocks) 서로 다른 섹션을 정의할 수 있습니다.

Edge Delivery Services의 콘텐츠 모델은 섹션에 포함된 기본 콘텐츠 또는 블록인 단일 수준의 중첩만 의도적으로 허용합니다. 즉, 다른 구성 요소를 포함할 수 있는 보다 복잡한 시각적 구성 요소를 포함하려면 섹션으로 모델링하고 자동 차단 클라이언트측을 사용하여 함께 결합해야 합니다. 이것의 대표적인 예는 아코디언과 같이 탭과 접을 수 있는 단면이다.

섹션은 블록과 동일한 방식으로 정의할 수 있지만 리소스 유형은 다음과 같습니다. `core/franklin/components/section/v1/section`. 섹션에는 이름과 [필터 ID,](/help/implementing/universal-editor/customizing.md#filtering-components) 다음에서 사용됨: [유니버설 편집기](/help/implementing/universal-editor/introduction.md) 뿐만 아니라 [모델 ID,](/help/implementing/universal-editor/field-types.md#model-structure) 섹션 메타데이터를 렌더링하는 데 사용됩니다. 이 모델은 이러한 방식으로 섹션 메타데이터 블록의 모델을 만듭니다. 이 모델은 비어 있지 않을 경우 키-값 블록으로 섹션에 자동으로 추가됩니다.

다음 [모델 ID](/help/implementing/universal-editor/field-types.md#model-structure) 및 [필터 ID](/help/implementing/universal-editor/customizing.md#filtering-components) 기본 섹션의 값은 입니다. `section`. 기본 섹션의 동작을 변경하는 데 사용할 수 있습니다. 다음 예제에서는 일부 스타일과 배경 이미지를 섹션 메타데이터 모델에 추가합니다.

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

다음 예제에서는 탭 섹션을 정의합니다. 이 섹션은 자동 차단 중에 탭 제목 데이터 속성과 함께 연속된 섹션을 탭 블록으로 결합하여 탭 블록을 만드는 데 사용할 수 있습니다.

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

문서에 페이지가 있을 수 있음 [메타데이터 블록,](/help/edge/authoring.md#metadata--seo) 다음 항목을 정의하는 데 사용됨 `<meta>` 요소가 다음에 렌더링됩니다. `<head>` 페이지의 . AEM에 있는 페이지의 페이지 속성은 다음과 같이 Edge Delivery Services에게 즉시 사용할 수 있는 속성으로 as a Cloud Service 매핑됩니다. `title`, `description`, `keywords`등

고유한 메타데이터를 정의하는 방법을 자세히 살펴보기 전에 다음 문서를 검토하여 페이지 메타데이터의 개념을 먼저 이해하십시오.

* [메타데이터](https://www.aem.live/developer/block-collection/metadata)
* [대량 메타데이터](/help/edge/docs/bulk-metadata.md)

두 가지 방법으로 추가 페이지 메타데이터를 정의할 수도 있습니다.

### 메타데이터 스프레드시트 {#metadata-spreadsheets}

경로당 또는 경로 패턴당 메타데이터를 AEM as a Cloud Service으로 테이블처럼 정의할 수 있습니다. Excel 또는 Google Sheets와 유사한 테이블 형식 데이터를 위한 작성 UI가 있습니다.

이러한 테이블을 만들려면 페이지를 만들고 사이트 콘솔에서 메타데이터 템플릿을 사용하십시오.

스프레드시트의 페이지 속성에서 URL과 함께 필요한 메타데이터 필드를 정의합니다. 그런 다음 페이지 경로 또는 페이지 경로 패턴당 메타데이터를 추가합니다.

스프레드시트를 게시하기 전에 경로 매핑에도 스프레드시트가 추가되었는지 확인하십시오.

```json
{
  "mappings": [
    "/content/site/:/",
    "/content/site/metadata:/metadata.json"
  ]
}
```

### 페이지 속성 {#page-properties}

작성자가 AEM Sites 페이지 속성 대화 상자의 탭으로 사용할 수 있게 되는 페이지 메타데이터에 대한 구성 요소 모델을 정의할 수도 있습니다.

이렇게 하려면 ID를 사용하여 구성 요소 모델을 만듭니다 `page-metadata`.

```json
{
  "id": "page-metadata",
  "fields": [
    {
      "component": "text-input",
      "name": "theme",
      "label": "Theme"
    }
  ]
}
```

작성 대화 상자 UI를 제공할 때 건너뛰게 되는 특별한 의미를 갖는 몇 가지 필드 이름이 있습니다.

* **`cq:tags`** - 기본적으로, `cq:tags` 가 메타데이터에 추가되지 않았습니다. 에 추가 `page-metadata` 모델은 태그 ID를 쉼표로 구분된 목록으로 추가합니다. `tags` 헤드에 메타 태그를 추가합니다.
* **`cq:lastModified`** - `cq:lastModified` 은(는) 데이터를 다음으로 추가합니다. `last-modified` 머리까지.
