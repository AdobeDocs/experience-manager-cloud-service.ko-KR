---
title: 구성 요소 정의
description: 구성 요소 정의와 유니버설 편집기 간의 JSON 계약에 대해 자세히 알아봅니다.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 7f54d2ee61d2b92e7a0f02c66ce8ee5cdbedd73c
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# 구성 요소 정의 {#component-definition}

구성 요소 정의와 유니버설 편집기 간의 JSON 계약에 대해 자세히 알아봅니다.

## 개요 {#overview}

`component-definition.json` 파일은 콘텐츠 작성자가 프로젝트에 사용할 수 있는 구성 요소를 정의합니다. 이 문서에서는 이 파일의 용도와 유니버설 편집기에서 이 파일을 사용하여 작성자에게 페이지 작성 구성 요소를 제공하는 방법에 대해 자세히 설명합니다.

>[!TIP]
>
>콘텐츠 모델링 프로세스에 대한 개요는 [Edge Delivery Services 프로젝트를 사용하여 WYSIWYG 작성을 위한 콘텐츠 모델링](/help/edge/wysiwyg-authoring/content-modeling.md) 문서를 참조하십시오.

>[!TIP]
>
>`component-definition.json` 파일을 처음부터 직접 만들 필요는 없습니다. [프로젝트를 부트스트랩](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)하는 데 사용하는 프로젝트 빌러플레이트에는 필요에 따라 조정할 수 있는 [정상적으로 작동하는 `component-definition.json` 파일](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json)이 포함되어 있습니다.

## 구성 요소 정의 예 {#example}

다음은 완전하지만 간단한 `component-definition.json`의 예입니다.

```json
{
  "groups": [
    {
      "title": "General Components",
      "id": "general",
      "components": [
        {
          "title": "Text",
          "id": "text",
          "plugins": {
            "aem": {
              "page": {
                "resourceType": "wknd/components/text",
                "template": {
                  "text": "Default Text"
                }
              }
            },
            "aem65": {
              "page": {
                "resourceType": "wknd/components/text",
                "template": {
                  "text": "Default Text"
                }
              }
            }
          }
        },
      }
   ]
}
```

## `groups` {#groups}

`groups`은(는) 편집기의 속성 패널에서 **추가** 아이콘을 클릭하여 [페이지에 새 구성 요소를 추가할 때 작성자가 유니버설 편집기에서 볼 수 있는 구성 요소 그룹을 정의합니다.구성 요소를 구성하는 데 도움이 되는 그룹이 ](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components)개 있습니다. 일반 그룹은 **일반 구성 요소** 및 **고급 구성 요소**&#x200B;일 수 있습니다.

* `title`은(는) 편집기 UI에 표시되는 그룹의 텍스트 설명을 정의합니다.
* `id`은(는) 그룹을 고유하게 식별합니다.

## `components` {#components}

`components`은(는) 그룹에 속한 구성 요소를 정의합니다.

* `title`은(는) UI에 표시되는 구성 요소의 텍스트 설명을 정의합니다.
* `id`은(는) 구성 요소를 고유하게 식별합니다.
   * 같은 `id`의 [구성 요소 모델](/help/implementing/universal-editor/field-types.md#model-structure)은(는) 구성 요소의 필드를 정의합니다.
   * 이는 고유하므로 예를 들어 [필터 정의](/help/implementing/universal-editor/customizing.md#filtering-components)에서 컨테이너에 추가할 수 있는 구성 요소를 결정하는 데 사용할 수 있습니다.

## `plugins` {#plugins}

`plugins`은(는) 구성 요소 유지를 담당하는 플러그인을 정의합니다. 일반적인 플러그인은 다음과 같습니다.

* AEM as a Cloud Service용 `aem`.
* AEM 6.5용 `aem5`.
* AEM as a Cloud Service WYSIWYG 작성용 `xwalk`.

## `page` 또는 `cf` {#page-cf}

`plugin`이(가) 정의되면 페이지 관련 항목인지 조각 관련 항목인지 표시해야 합니다.

* `page`은(는) 구성 요소가 현재 페이지의 콘텐츠임을 나타냅니다.
* `cf`은(는) 구성 요소가 [콘텐츠 조각 내의 콘텐츠와 관련되어 있음을 나타냅니다.](/help/assets/content-fragments/content-fragments.md)

### `page` {#page}

구성 요소가 페이지의 콘텐츠인 경우 다음 정보를 제공할 수 있습니다.

* `name`은(는) 새로 만든 구성 요소에 대해 JCR에 저장된 선택적 이름을 정의합니다.
   * 정보만 제공하며 일반적으로 `title`과(와) 같이 UI에 표시되지 않습니다.
* `resourceType`은(는) 구성 요소를 렌더링하는 데 사용되는 [Sling](/help/implementing/developing/introduction/sling-cheatsheet.md) `resourceType`을(를) 정의합니다.
* `template`은(는) 새로 만든 구성 요소에 자동으로 쓸 선택적 키/값을 정의합니다.
   * 설명, 샘플 또는 자리 표시자 텍스트에 유용합니다.

### `cf` {#cf}

구성 요소가 콘텐츠 조각 내의 콘텐츠와 관련된 경우 다음 정보를 제공할 수 있습니다.

* `name`은(는) 새로 만든 구성 요소에 대해 JCR에 저장된 선택적 이름을 정의합니다.
   * 정보만 제공하며 일반적으로 `title`과(와) 같이 UI에 표시되지 않습니다.
* `cfModel`은(는) 새로 만든 구성 요소에 대해 [콘텐츠 조각](/help/assets/content-fragments/content-fragments-models.md) 모델을 정의합니다.
* `cfFolder`은(는) 콘텐츠 조각을 만들 폴더를 정의합니다.
* `title`은(는) 새 콘텐츠 조각의 제목을 정의합니다.
* `description`은(는) 새 콘텐츠 조각에 대한 설명을 정의합니다.
* `template`은(는) 새로 만든 콘텐츠 조각에 자동으로 쓸 선택적 키/값을 정의합니다.
   * 설명, 샘플 또는 자리 표시자 텍스트에 유용합니다.

### `cf`은(는) 암시될 수 있습니다. {#cf-implied}

참조 필드를 가리키도록 페이지가 [계측됨](/help/implementing/universal-editor/getting-started.md#instrument-page)이면 `cf`이(가) 가정됩니다.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container" data-aue-prop="field"></div>
```

이 경우 `data-aue-prop`이(가) 참조 필드를 가리키므로 `cf`을(를) 가정합니다. `data-aue-prop`이(가) 없으면 구성 요소가 참조 필드를 통해 연결되지 않으므로 유니버설 편집기는 `page`을(를) 가정합니다.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container"></div>
```

구성 요소는 리소스 아래의 하위 노드일 뿐입니다.
