---
title: 범용 편집기 작성 경험 사용자 지정
description: 콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 UI를 사용자 지정할 수 있는 다양한 확장 지점 및 기타 기능에 대해 알아봅니다.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: f04ab32093371ff425c4e196872738867d9ed528
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# 범용 편집기 작성 경험 사용자 지정 {#customizing-ue}

콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 작성 환경을 사용자 정의할 수 있는 다양한 확장 지점 및 기타 기능에 대해 알아봅니다.

## 게시 비활성화 {#disable-publish}

특정 작성 워크플로에서는 콘텐츠를 게시하기 전에 검토해야 합니다. 이러한 경우 작성자는 게시 옵션을 사용할 수 없습니다.

다음 **게시** 따라서 다음 메타데이터를 추가하여 앱에서 버튼을 완전히 억제할 수 있습니다.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## 구성 요소 필터링 {#filtering-components}

유니버설 편집기를 사용하는 경우 컨테이너 구성 요소별로 허용된 구성 요소를 제한할 수 있습니다. 이렇게 하려면 필터 정의를 가리키는 추가 스크립트 태그를 도입해야 합니다.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

필터 정의는 다음과 같을 수 있으며, 이렇게 하면 텍스트 및 이미지 추가만 허용하도록 컨테이너가 제한됩니다.

```json
[
  {
    "id": "container-filter",
     "components": ["text", "image"]
   }
]
```

그런 다음 속성을 추가하여 컨테이너 구성 요소에서 필터 정의를 참조할 수 있습니다 `data-aue-filter`를 통해 이전에 정의한 필터의 ID를 전달합니다.

```html
data-aue-filter="container-filter"
```

설정 `components` 필터 정의의 속성 `null` 필터가 없는 것처럼 모든 구성 요소를 허용합니다.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

## 속성 레일에서 조건부로 구성 요소 표시 및 숨기기 {#conditionally-hide}

일반적으로 작성자가 구성 요소를 사용할 수 있지만 의미가 없는 상황이 있을 수 있습니다. 이러한 경우 를 추가하여 속성 레일에서 구성 요소를 숨길 수 있습니다 `condition` 속성 [구성 요소 모델의 필드.](/help/implementing/universal-editor/field-types.md#fields)

다음을 사용하여 조건을 정의할 수 있습니다. [JsonLogic 스키마.](https://jsonlogic.com/) 조건이 true이면 필드가 표시됩니다. 조건이 false이면 필드가 숨겨집니다.

### 샘플 모델 {#sample-model}

```json
 {
    "id": "conditionally-revealed-component",
    "fields": [
      {
        "component": "boolean",
        "label": "Shall the text field be revealed?",
        "name": "reveal",
        "valueType": "boolean"
      },
      {
        "component": "text-input",
        "label": "Hidden text field",
        "name": "hidden-text",
        "valueType": "string",
        "condition": { "===": [{"var" : "reveal"}, true] }
      }
    ]
 }
```

#### 조건 False {#false}

![숨겨진 텍스트 필드](assets/hidden.png)

#### 조건 True {#true}

![표시된 텍스트 필드](assets/shown.png)
