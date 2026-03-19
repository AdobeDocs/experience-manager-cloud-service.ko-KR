---
title: 필터
description: 사용 가능한 구성 요소, RTE 옵션, 에셋 선택 등 편집기에서 사용할 수 있는 옵션을 제한하는 필터를 정의하는 방법에 대해 알아봅니다.
feature: Developing
role: Admin, Developer
exl-id: eeae8d7c-c563-4d9b-8c54-1098a4e98c18
source-git-commit: 8d9d162ec5bba99afb1ae86252a49a9880be4e68
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 15%

---


# 필터 {#filters}

사용 가능한 구성 요소, RTE 옵션, 에셋 선택 등 편집기에서 사용할 수 있는 옵션을 제한하는 필터를 정의하는 방법에 대해 알아봅니다.

## 필터 구성 {#configuring-filters}

범용 편집기를 사용하는 경우 필터를 정의하여 특정 기능에 허용된 옵션을 제한할 수 있습니다. 필터는 특정 컨텍스트에서 사용할 수 있는 항목 또는 작업 목록입니다. 예를 들어 컨테이너에 삽입할 수 있는 구성 요소를 필터링할 수 있고, [RTE에서 사용 가능한 옵션을 필터링](/help/implementing/universal-editor/configure-rte.md)할 수 있으며, 자산 선택기에서 [사용 가능한 자산을 필터링](/help/implementing/universal-editor/configure-assets-selector.md)할 수 있습니다.

필터는 모두 유사하게 정의해야 합니다.

1. [필터 정의를 가리키도록 스크립트 태그 추가](#add-tag)
1. [필터 정의](#define-filter)
1. [필터 참조](#reference-filter)

컨테이너 구성 요소당 구성 요소 필터링의 예를 살펴보겠습니다.

## 참조 필터 정의 {#add-tag}

먼저 필터 정의를 가리키는 추가 스크립트 태그를 도입합니다.

이 예에서는 허용된 컨테이너당 구성 요소를 필터링하는 방법을 설명합니다. 태그는 다음과 비슷합니다.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

## 필터 정의 {#define-filter}

필터 정의에는 필터 및 필터 기준에 고유한 ID가 있는 JSON이 포함되어 있습니다.

이 예제에서는 허용된 구성 요소를 컨테이너별로 필터링합니다. 이렇게 하면 컨테이너가 텍스트 및 이미지 추가만 허용하도록 제한됩니다.

```json
[
  {
    "id": "container-filter",
    "components": ["text", "image"]
   }
]
```

필터 정의의 `components` 속성을 `null`로 설정하면 필터가 없는 것처럼 모든 구성 요소를 허용합니다.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

## 필터 참조 {#reference-filter}

필터를 사용하려면 필터 정의를 참조해야 합니다. 다음을 통해 이 작업을 수행할 수 있습니다.

* 속성 `data-aue-filter`을(를) 추가하고 필터 ID를 전달하여 컨테이너 구성 요소에서 필터를 참조합니다.

  ```html
  data-aue-filter="container-filter"
  ```

* [구성 요소 정의의 필터를 참조하고,](/help/implementing/universal-editor/component-definition.md)에서 필터의 ID를 전달합니다.

  ```json
  {
     "title":"My Container",
     "id":"my-container",
     "model": "my-model",
     "filter": "container-filter",
     ...
  }
  ```

## 추가 리소스 {#additional-resources}

문서에서 범용 편집기에 사용할 수 있는 다른 사용자 정의 및 확장 옵션에 대해 알아봅니다.

* [범용 편집기에 대한 RTE 구성](/help/implementing/universal-editor/configure-rte.md)
* [Assets 선택기에 대한 필터 구성](/help/implementing/universal-editor/configure-assets-selector.md)
* [범용 편집기 사용자 정의](/help/implementing/universal-editor/customizing.md)
* [범용 편집기 확장](/help/implementing/universal-editor/extending.md)
