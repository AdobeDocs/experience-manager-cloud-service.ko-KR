---
title: 구성 요소 정의
description: 구성 요소 정의와 범용 편집기 간의 JSON 계약에 대해 자세히 알아봅니다.
feature: Developing
role: Admin, Architect, Developer
exl-id: e1bb1a54-50c0-412a-a8fd-8167c6f47d2b
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: ht
source-wordcount: '602'
ht-degree: 100%

---

# 구성 요소 정의 {#component-definition}

구성 요소 정의와 범용 편집기 간의 JSON 계약에 대해 자세히 알아봅니다.

## 개요 {#overview}

`component-definition.json` 파일은 프로젝트에 대해 콘텐츠 작성자가 사용할 수 있는 구성 요소를 정의합니다. 이 문서는 이 파일의 목적과 범용 편집기가 이 파일을 사용하여 작성자에게 페이지 작성 구성 요소를 제공하는 방법을 자세히 설명합니다.

>[!TIP]
>
>콘텐츠 모델링 프로세스에 대한 개요는 [Edge Delivery Services 프로젝트에서 WYSIWYG 작성을 위한 콘텐츠 모델링](https://www.aem.live/developer/component-model-definitions) 문서를 참조하십시오.

>[!TIP]
>
>처음부터 직접 `component-definition.json` 파일을 만들 필요는 없습니다. [프로젝트 부트스트랩](https://www.aem.live/developer/ue-tutorial)에 사용하는 프로젝트 상용구에는 요구 사항에 맞게 조정할 수 있는 [완전히 작동하는 `component-definition.json` 파일](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json)이 포함되어 있습니다.

## 구성 요소 정의 예 {#example}

다음은 완전하지만 간단한 `component-definition.json` 예입니다.

```json
{
  "groups":[
    {
      "title":"General Components",
      "id":"general",
      "components":[
        {
          "title":"Text",
          "id":"text",
          "model": "text",
          "filter": "texts",
          "plugins":{
            "aem":{
              "page":{
                "resourceType":"wknd/components/text",
                "template":{
                  "text":"Default Text",
                  "name":"Text"
                }
              }
            },
            "aem65":{
              "page":{
                "resourceType":"wknd/components/text",
                "template":{
                  "text":"Default Text",
                  "name":"Text"
                }
              }
            }
          }
        }
      ]
    }
  ]
}
```

## `groups` {#groups}

`groups`는 [새 구성 요소를 페이지에 추가](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components)하기 위해 편집기의 속성 패널에서 **추가** 아이콘을 클릭할 때 작성자에게 범용 편집기에 표시되는 구성 요소 그룹을 정의합니다. 그룹은 구성 요소를 구성하는 데 도움이 됩니다. 일반적인 그룹으로는 **일반 구성 요소** 와 **고급 구성 요소**&#x200B;가 있습니다.

* `title`은 편집기 UI에 표시되는 그룹의 텍스트 설명을 정의합니다.
* `id`는 그룹을 고유하게 식별합니다.

## `components` {#components}

`components`는 그룹에 속하는 구성 요소를 정의합니다.

* `title`은 UI에 표시되는 구성 요소의 텍스트 설명을 정의합니다.
* `id`는 구성 요소를 고유하게 식별합니다.
   * 동일한 `id`의 [구성 요소 모델](/help/implementing/universal-editor/field-types.md#model-structure)은 구성 요소의 필드를 정의합니다.
   * 고유하기 때문에 컨테이너에 추가할 수 있는 구성 요소를 결정하기 위한 [필터 정의](/help/implementing/universal-editor/filtering.md) 등에 사용할 수 있습니다.
* `model`은 구성 요소와 함께 사용되는 [모델](/help/implementing/universal-editor/field-types.md#model-structure)을 정의합니다.
   * 따라서 모델은 구성 요소 정의에서 중앙 집중식으로 관리할 수 있으며, [계측에서 지정](/help/implementing/universal-editor/field-types.md#instrumentation)할 필요가 없습니다.
   * 이를 통해 구성 요소를 컨테이너 간에 자유롭게 이동할 수 있습니다.
* `filter`는 구성 요소와 함께 사용해야 하는 [필터](/help/implementing/universal-editor/filtering.md)를 정의합니다.

## `plugins` {#plugins}

`plugins`는 구성 요소를 유지하는 역할을 하는 플러그인을 정의합니다. 일반적인 플러그인은 다음과 같습니다.

* AEM as a Cloud Service용 `aem`
* AEM 6.5용 `aem5`
* AEM as a Cloud Service WYSIWYG 작성용 `xwalk`

## `page` 또는 `cf` {#page-cf}

`plugin`이 정의되면 페이지 관련인지 또는 조각 관련인지 여부를 표시해야 합니다.

* `page`는 구성 요소가 현재 페이지의 콘텐츠임을 나타냅니다.
* `cf`는 구성 요소가 [콘텐츠 조각](/help/assets/content-fragments/content-fragments.md) 내 콘텐츠와 관련이 있음을 나타냅니다.

### `page` {#page}

구성 요소가 페이지의 콘텐츠인 경우, 다음 정보를 제공할 수 있습니다.

* `resourceType`은 구성 요소를 렌더링하는 데 사용되는 [Sling](/help/implementing/developing/introduction/sling-cheatsheet.md) `resourceType`을 정의합니다.
* `template`은 새로 생성된 구성 요소에 자동으로 기록될 선택적 키/값을 정의하고 구성 요소에 적용되어야 하는 필터 및/또는 모델을 정의합니다.
   * 설명, 샘플 또는 플레이스홀더 텍스트에 유용합니다.

#### `template` {#template}

선택적 키/값 쌍을 제공하면 `template`이 이러한 쌍을 새 구성 요소에 자동으로 기록할 수 있습니다. 또한 다음과 같은 선택 값도 지정할 수 있습니다.

### `cf` {#cf}

구성 요소가 콘텐츠 조각 내 콘텐츠와 관련이 있는 경우 다음 정보를 제공할 수 있습니다.

* `name`은 새로 생성된 구성 요소에 대해 JCR에 저장되는 선택적 이름을 정의합니다.
   * 정보 제공만을 목적으로 하며 `title`처럼 일반적으로 UI에 표시되지 않습니다.
* `cfModel`은 새로 생성된 구성 요소에 대한 [콘텐츠 조각](/help/assets/content-fragments/content-fragments-models.md) 모델을 정의합니다.
* `cfFolder`는 콘텐츠 조각이 생성될 폴더를 정의합니다.
* `title`은 새 콘텐츠 조각의 제목을 정의합니다.
* `description`은 새 콘텐츠 조각의 설명을 정의합니다.
* `template`은 새로 생성된 콘텐츠 조각에 자동으로 기록될 선택적 키/값을 정의합니다.
   * 설명, 샘플 또는 플레이스홀더 텍스트에 유용합니다.

### `cf`는 암시될 수 있습니다. {#cf-implied}

페이지가 참조 필드를 가리키도록 [계측된](/help/implementing/universal-editor/getting-started.md#instrument-page) 경우 `cf`가 가정됩니다.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container" data-aue-prop="field"></div>
```

이러한 경우 `data-aue-prop`이 참조 필드를 가리키므로 `cf`가 가정됩니다. `data-aue-prop`이 없으면 구성 요소가 참조 필드를 통해 연결되지 않으므로 범용 편집기는 `page`로 가정합니다.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container"></div>
```

구성 요소는 리소스 아래의 하위 노드입니다.
