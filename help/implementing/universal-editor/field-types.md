---
title: 모델 정의, 필드 및 구성 요소 유형
description: 예제와 함께 범용 편집기가 속성 패널에서 편집할 수 있는 필드와 구성 요소 유형에 대해 알아봅니다. 모델 정의를 생성하고 구성 요소에 연결하여 자체 앱을 계측하는 방법에 대해 알아봅니다.
exl-id: cb4567b8-ebec-477c-b7b9-53f25b533192
feature: Developing
role: Admin, Architect, Developer
source-git-commit: efd96f179482dfe1f00bdce35e2824ac5cdf9813
workflow-type: tm+mt
source-wordcount: '1592'
ht-degree: 98%

---


# 모델 정의, 필드 및 구성 요소 유형 {#field-types}

예제와 함께 범용 편집기가 속성 패널에서 편집할 수 있는 필드와 구성 요소 유형에 대해 알아봅니다. 모델 정의를 생성하고 구성 요소에 연결하여 자체 앱을 계측하는 방법에 대해 알아봅니다.

## 개요 {#overview}

범용 편집기에서 사용할 자체 애플리케이션을 적용할 때 구성 요소를 계측하고 편집기의 속성 패널에서 조작할 수 있는 필드 및 구성 요소 유형을 정의해야 합니다. 이 작업은 모델을 생성하고 구성 요소에서 모델에 연결하여 수행합니다.

이 문서에서는 모델 정의와 필드, 사용 가능한 구성 요소 유형에 대한 개요와 함께 구성 예시를 제공합니다.

>[!TIP]
>
>범용 편집기용 애플리케이션을 계측하는 방법에 대해 익숙하지 않은 경우 [AEM 개발자용 범용 편집기 개요](/help/implementing/universal-editor/developer-overview.md) 문서를 참조합니다.

## 모델 정의 구조 {#model-structure}

범용 편집기의 속성 패널을 통해 구성 요소를 구성하려면 모델 정의가 존재하고 구성 요소에 연결되어야 합니다.

모델 정의는 모델의 배열로 시작하는 JSON 구조입니다.

```json
[
  {
    "id": "model-id",        // must be unique
    "fields": []             // array of fields which shall be rendered in the properties panel
  }
]
```

`fields` 배열을 정의하는 방법에 대한 자세한 내용은 이 문서의 **[필드](#fields)** 섹션을 참조하십시오.

[구성 요소 정의](#component-definition)를 사용하거나 [계측](#instrumentation)을 통해 두 가지 방법으로 모델을 구성 요소에 연결할 수 있습니다.

### 구성 요소 정의를 사용하여 연결 {#component-definition}

이는 모델을 구성 요소에 연결하는 기본 방법입니다. 이렇게 하면 구성 요소 정의에서 링크를 중앙에서 유지하고 구성 요소를 컨테이너 간에 드래그할 수 있습니다.

`component-definition.json` 파일의 `components` 배열에 있는 구성 요소 오브젝트에 `model` 속성을 포함하기만 하면 됩니다.

자세한 내용은 [구성 요소 정의](/help/implementing/universal-editor/component-definition.md) 문서를 참조하십시오.

### 계측을 사용하여 연결 {#instrumentation}

구성 요소와 함께 모델 정의를 사용하려면 `data-aue-model` 속성을 사용할 수 있습니다.

```html
<div data-aue-resource="urn:datasource:/content/path" data-aue-type="component"  data-aue-model="model-id">Click me</div>
```

>[!NOTE]
>
>범용 편집기는 먼저 계측을 통해 모델이 연결되었는지 확인하고, 구성 요소 정의를 확인하기 전에 해당 모델을 사용합니다. 이것은 다음을 의미합니다.
>
>* 모델에 대한 링크를 계측을 통해 구현한 프로젝트는 변경할 필요 없이 그대로 계속 작동합니다.
>* [구성 요소 정의](#component-definition) 및 계측에 모델을 정의하는 경우 항상 계측이 사용됩니다.

## 모델 정의 로드 {#loading-model}

모델을 생성하면 외부 파일로 참조할 수 있습니다.

```html
<script type="application/vnd.adobe.aue.model+json" src="<url-of-model-definition>"></script>
```

또는 인라인으로 모델을 정의할 수도 있습니다.

```html
<script type="application/vnd.adobe.aue.model+json">
  { ... model definition ... }
</script>
```

## 필드 {#fields}

필드 오브젝트에는 다음 유형 정의가 있습니다.

| 구성 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `component` | `ComponentType` | 구성 요소의 렌더러 | 예 |
| `name` | `string` | 데이터가 유지되어야 하는 속성 [또는 경로](#nesting) | 예 |
| `label` | `FieldLabel` | 필드의 레이블 | 예 |
| `description` | `FieldDescription` | 필드 설명 | 아니요 |
| `placeholder` | `string` | 필드에 대한 플레이스홀더 | 아니요 |
| `value` | `FieldValue` | 자리 표시자 역할을 하는 기본값입니다. 이 값에 따라 변경되는 콘텐츠 업데이트가 없습니다. 이는 UI의 표시일 뿐입니다. | 아니요 |
| `valueType` | `ValueType` | 표준 유효성 검사이며, `string`, `string[]`, `number`, `date`, `boolean`이 될 수 있습니다. | 아니요 |
| `required` | `boolean` | 필드가 필수입니까? | 아니요 |
| `readOnly` | `boolean` | 필드가 읽기 전용입니까? | 아니요 |
| `hidden` | `boolean` | 필드가 기본적으로 숨겨져 있습니까? | 아니요 |
| `condition` | `RulesLogic` | [조건](/help/implementing/universal-editor/customizing.md#conditionally-hide)에 따라 필드를 표시하거나 숨기는 규칙 | 아니요 |
| `multi` | `boolean` | 필드가 다중 필드입니까?<br/>속성 패널의 다중 필드에 컨테이너 중첩이 허용되지 않습니다. | 아니요 |
| `validation` | `ValidationType` | 필드에 대한 유효성 검사 규칙 | 아니요 |
| `raw` | `unknown` | 구성 요소가 사용할 수 있는 원시 데이터 | 아니요 |

### 이름 필드 및 중첩 {#nesting}

`name` 필드는 현재 리소스의 속성을 직접 가리킬 수 있으며, `cq:Pages`의 구성 요소인 경우 중첩된 속성에 대한 경로를 사용할 수도 있습니다. 예:

```json
"name": "teaser/image/fileReference"
```

### 구성 요소 유형 {#component-types}

다음은 필드 렌더링에 사용할 수 있는 구성 요소 유형입니다.

| 설명 | 구성 요소 유형 |
|---|---|
| [AEM 태그](#aem-tag) | `aem-tag` |
| [AEM 콘텐츠](#aem-content) | `aem-content` |
| [부울](#boolean) | `boolean` |
| [체크박스 그룹](#checkbox-group) | `checkbox-group` |
| [컨테이너](#container) | `container` |
| [콘텐츠 조각](#content-fragment) | `aem-content-fragment` |
| [Date Time](#date-time) | `date-time` |
| [경험 조각](#experience-fragment) | `aem-experience-fragment` |
| [다중 선택](#multiselect) | `multiselect` |
| [숫자](#number) | `number` |
| [라디오 그룹](#radio-group) | `radio-group` |
| [참조](#reference) | `reference` |
| [리치 텍스트](#rich-text) | `richtext` |
| [선택](#select) | `select` |
| [탭](#tab) | `tab` |
| [텍스트](#text) | `text` |

#### AEM 태그 {#aem-tag}

AEM 태그 구성 요소 유형은 AEM 태그 선택기를 활성화하여 구성 요소에 태그를 첨부하는 데 사용할 수 있습니다.

>[!BEGINTABS]

>[!TAB 샘플]

```json
{
  "id": "aem-tag-picker",
  "fields": [
    {
      "component": "aem-tag",
      "label": "AEM Tag Picker",
      "name": "cq:tags",
      "valueType": "string"
    }
  ]
}
```

>[!TAB 스크린샷]

![AEM 태그 구성 요소 유형의 스크린샷](assets/component-types/aem-tag-picker.png)

>[!ENDTABS]

>[!TIP]
>
>스프레드시트를 사용하여 Edge Delivery Services 프로젝트의 분류 데이터를 관리하는 방법에 대한 자세한 내용은 [분류 체계 데이터 관리](https://www.aem.live/docs/authoring-taxonomy) 문서를 참조하십시오.

#### AEM 콘텐츠 {#aem-content}

AEM 콘텐츠 구성 요소 유형은 AEM 콘텐츠 선택기를 활성화하여 모든 AEM 리소스를 선택하는 데 사용할 수 있습니다. 자산만 선택할 수 있는 [참조 구성 요소](#reference)와 달리 AEM 콘텐츠 구성 요소는 모든 AEM 콘텐츠를 참조할 수 있습니다. 추가 유효성 검사 유형을 제공합니다.

| 유효성 검사 유형 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `rootPath` | `string` | 사용자가 AEM 콘텐츠를 선택하기 위해 콘텐츠 선택기를 여는 경로이며, 해당 디렉터리 및 하위 디렉터리로 선택이 제한됩니다. | 아니요 |

>[!BEGINTABS]

>[!TAB 샘플]

```json
{
  "id": "aem-content-picker",
  "fields": [
    {
      "component": "aem-content",
      "name": "reference",
      "value": "",
      "label": "AEM Content Picker",
      "valueType": "string",
      "validation": {
            "rootPath": "/content/refresh"
        }
    }
  ]
}
```

>[!TAB 스크린샷]

![AEM 콘텐츠 구성 요소 유형의 스크린샷](assets/component-types/aem-content-picker.png)

>[!ENDTABS]

#### 부울 {#boolean}

부울 구성 요소 유형은 토글로 렌더링되는 간단한 true/false 값을 저장합니다. 추가 유효성 검사 유형을 제공합니다.

| 유효성 검사 유형 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `customErrorMsg` | `string` | 입력된 값이 부울 값이 아닌 경우 표시되는 메시지 | 아니요 |

>[!BEGINTABS]

>[!TAB 샘플 1]

```json
{
  "id": "boolean",
  "fields": [
    {
      "component": "boolean",
      "label": "Boolean",
      "name": "boolean",
      "valueType": "boolean"
    }
  ]
}
```

>[!TAB 샘플 2]

```json
{
  "id": "another-boolean",
  "fields": [
    {
      "component": "boolean",
      "label": "Boolean",
      "name": "boolean",
      "valueType": "boolean",
      "validation": {
        "customErrorMsg": "Think, McFly. Think!"
      }
    }
  ]
}
```

>[!TAB 스크린샷]

![부울 구성 요소 유형의 스크린샷](assets/component-types/boolean.png)

>[!ENDTABS]

#### 체크박스 그룹 {#checkbox-group}

부울과 마찬가지로 체크박스 그룹 구성 요소 유형을 사용하면 여러 체크박스로 렌더링되는 여러 true/false 항목을 선택할 수 있습니다.

>[!BEGINTABS]

>[!TAB 샘플]

```json
{
  "id": "checkbox-group",
  "fields": [
    {
      "component": "checkbox-group",
      "label": "Checkbox Group",
      "name": "checkbox",
      "valueType": "string[]",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB 스크린샷]

![그룹 구성 요소 유형의 스크린샷](assets/component-types/checkbox-group.png)

>[!ENDTABS]

#### 컨테이너 {#container}

컨테이너 구성 요소 유형을 사용하면 다중 필드 지원을 포함하여 구성 요소를 그룹화할 수 있습니다. 추가 구성을 제공합니다. 속성 패널의 다중 필드에 컨테이너 중첩이 허용되지 않습니다.

| 구성 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `collapsible` | `boolean` | 컨테이너를 축소할 수 있습니까? | 아니요 |

>[!BEGINTABS]

>[!TAB 샘플]

```json
 {
  "id": "container",
  "fields": [
    {
      "component": "container",
      "label": "Container",
      "name": "container",
      "valueType": "string",
      "collapsible": true,
      "fields": [
        {
          "component": "text-input",
          "label": "Simple Text 1",
          "name": "text",
          "valueType": "string"
        },
        {
          "component": "text-input",
          "label": "Simple Text 2",
          "name": "text2",
          "valueType": "string"
        }
      ]
    }
  ]
}
```

>[!TAB 스크린샷]

![컨테이너 구성 요소 유형의 스크린샷](assets/component-types/container.png)

>[!TAB 다중 필드 지원]

```json
{
  "component": "container",
  "name": "test",
  "label": "Multi Text",
  "multi": true,
  "fields": [
    {
      "component": "reference",
      "name": "image",
      "value": "",
      "label": "Sample Image",
      "valueType": "string"
    },
    {
      "component": "text",
      "name": "alt",
      "value": "",
      "label": "Alt Text",
      "valueType": "string"
    }
  ]
}
```

>[!ENDTABS]



#### 콘텐츠 조각 {#content-fragment}

콘텐츠 조각 선택기는 [콘텐츠 조각](/help/sites-cloud/authoring/fragments/content-fragments.md) 및 해당 변형(필요한 경우)을 선택하는 데 사용할 수 있습니다. 추가 구성을 제공합니다.

| 구성 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `variationName` | `string` | 선택한 변형을 저장할 변수 이름입니다. 정의되지 않은 경우 변형 선택기가 표시되지 않습니다. | 아니요 |

추가 유효성 검사 유형도 제공합니다.

| 유효성 검사 유형 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `rootPath` | `string` | 사용자가 콘텐츠 조각을 선택하기 위해 콘텐츠 선택기를 여는 경로이며, 해당 디렉터리 및 하위 디렉터리로 선택이 제한됩니다. | 아니요 |

>[!NOTE]
>
>범용 편집기는 [모델을 기반으로 콘텐츠 조각 필드의 유효성을 검사](/help/assets/content-fragments/content-fragments-models.md#validation)하여 정규식 패턴 및 고유성 제약 조건과 같은 데이터 무결성 규칙을 적용할 수 있습니다.
>
>이렇게 하면 콘텐츠가 게시되기 전에 특정 비즈니스 요구 사항을 충족할 수 있습니다.

>[!BEGINTABS]

>[!TAB 샘플 1]

```json
[
  {
    "id": "aem-content-fragment",
    "fields": [
      {
        "component": "aem-content-fragment",
        "name": "picker",
        "label": "Content Fragment Picker",
        "valueType": "string",
        "variationName": "contentFragmentVariation",
        "validation": {
            "rootPath": "/content/refresh"
        }
      }
    ]
  }
]
```

>[!TAB 스크린샷]

![콘텐츠 조각 선택기의 스크린샷](assets/component-types/aem-content-fragment.png)

>[!ENDTABS]

#### Date Time {#date-time}

날짜 시간 구성 요소 유형을 사용하면 날짜, 시간 또는 둘의 조합을 지정할 수 있습니다. 추가 구성을 제공합니다.

| 구성 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `displayFormat` | `string` | 날짜 문자열을 표시하는 형식 | 예 |
| `valueFormat` | `string` | 날짜 문자열을 저장할 형식 | 예 |

추가 유효성 검사 유형도 제공합니다.

| 유효성 검사 유형 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `customErrorMsg` | `string` | `valueFormat`이 충족되지 않을 경우 표시될 메시지 | 아니요 |

>[!BEGINTABS]

>[!TAB 샘플 1]

```json
{
  "id": "date-time",
  "fields": [
    {
      "component": "date-time",
      "label": "Date & Time",
      "name": "date",
      "valueType": "date"
    }
  ]
}
```

>[!TAB 샘플 2]

```json
{
  "id": "another-date-time",
  "fields": [
    {
      "component": "date-time",
       "valueType": "date-time",
      "name": "field1",
      "label": "Date Time",
      "description": "This is a date time field that stores both date and time.",
      "required": true,
      "placeholder": "YYYY-MM-DD HH:mm:ss",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Marty! You have to come back with me!"
      }
    },
    {
      "component": "date-time",
      "valueType": "date",
      "name": "field2",
      "label": "Another Date Time",
      "description": "This is another date time field that only stores the date.",
      "required": true,
      "placeholder": "YYYY-MM-DD",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Back to the future!"
      }
    },
    {
      "component": "date-time",
      "valueType": "time",
      "name": "field3",
      "label": "Yet Another Date Time",
      "description": "This is another date time field that only stores the time.",
      "required": true,
      "placeholder": "HH:mm:ss",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Great Scott!"
      }
    }
  ]
}
```

>[!TAB 스크린샷]

![날짜 시간 구성 요소 유형의 스크린샷](assets/component-types/date-time.png)

>[!ENDTABS]

#### 경험 조각 {#experience-fragment}

경험 조각 선택기를 사용하여 [경험 조각](/help/sites-cloud/authoring/fragments/experience-fragments.md) 및 해당 변형(필요한 경우)을 선택할 수 있습니다. 추가 구성을 제공합니다.

| 구성 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `variationName` | `string` | 선택한 변형을 저장할 변수 이름입니다. 정의되지 않은 경우 변형 선택기가 표시되지 않습니다. | 아니요 |

추가 유효성 검사 유형도 제공합니다.

| 유효성 검사 유형 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `rootPath` | `string` | 사용자가 경험 조각을 선택하기 위해 콘텐츠 선택기를 여는 경로이며, 해당 디렉터리 및 하위 디렉터리로 선택이 제한됩니다. | 아니요 |

>[!BEGINTABS]

>[!TAB 샘플 1]

```json
[
  {
    "id": "experience-fragment",
    "fields": [
      {
        "component": "aem-experience-fragment",
        "valueType": "string",
        "name": "experience-fragment",
        "label": "experience-fragment",
        "variationName": "experienceFragmentVariation",
        "validation": {
            "rootPath": "/content/refresh"
        }
      }
    ]
  }
]
```

>[!TAB 스크린샷]

![경험 조각 선택기의 스크린샷](assets/component-types/aem-experience-fragment.png)

>[!ENDTABS]


#### 다중 선택 {#multiselect}

다중 선택 구성 요소 유형은 선택 가능한 요소를 그룹화하는 기능을 포함하여 드롭다운에서 선택할 수 있는 여러 항목을 제공합니다.

>[!BEGINTABS]

>[!TAB 샘플 1]

```json
{
  "id": "multiselect",
  "fields": [
    {
      "component": "multiselect",
      "name": "multiselect",
      "label": "Multi Select",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB 샘플 2]

```json
{
  "id": "multiselect-grouped",
  "fields": [
    {
      "component": "multiselect",
      "name": "property",
      "label": "Multiselect field",
      "valueType": "string",
      "required": true,
      "maxSize": 2,
      "options": [
        {
          "name": "Theme",
          "children": [
            { "name": "Light", "value": "light" },
            { "name": "Dark",  "value": "dark" }
          ]
        },
        {
          "name": "Type",
          "children": [
            { "name": "Alpha", "value": "alpha" },
            { "name": "Beta", "value": "beta" },
            { "name": "Gamma", "value": "gamma" }
          ]
        }
      ]
    }
  ]
}
```

>[!TAB 스크린샷]

![다중 선택 구성 요소 유형의 스크린샷](assets/component-types/multiselect.png)
![그룹화가 적용된 다중 선택 구성 요소 유형의 스크린샷](assets/component-types/multiselect-group.png)

>[!ENDTABS]

#### 숫자 {#number}

숫자 구성 요소 유형을 사용하면 숫자를 입력할 수 있습니다. 추가 유효성 검사 유형을 제공합니다.

| 유효성 검사 유형 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `numberMin` | `number` | 허용되는 최소 수 | 아니요 |
| `numberMax` | `number` | 허용되는 최대 수 | 아니요 |
| `customErrorMsg` | `string` | `numberMin` 또는 `numberMax`가 충족되지 않을 경우 표시되는 메시지 | 아니요 |

>[!BEGINTABS]

>[!TAB 샘플 1]

```json
{
  "id": "number",
  "fields": [
    {
      "component": "number",
      "name": "number",
      "label": "Number",
      "valueType": "number",
      "value": 0
    }
  ]
}
```

>[!TAB 샘플 2]

```json
{
  "id": "another-number",
  "fields": [
   {
      "component": "number",
      "valueType": "number",
      "name": "field1",
      "label": "Number Field",
      "description": "This is a number field.",
      "required": true,
      "placeholder": null,
      "validation": {
        "numberMin": 0,
        "numberMax": 88,
        "customErrorMsg": "You also need 1.21 gigawatts."
      }
    }
  ]
}
```

>[!TAB 스크린샷]

![숫자 구성 요소 유형의 스크린샷](assets/component-types/number.png)

>[!ENDTABS]

#### 라디오 그룹 {#radio-group}

라디오 그룹 구성 요소 유형을 사용하면 체크박스 그룹과 유사하게 그룹으로 렌더링되는 여러 옵션에서 상호 배타적인 선택을 할 수 있습니다.

>[!BEGINTABS]

>[!TAB 샘플]

```json
{
  "id": "radio-group",
  "fields": [
    {
      "component": "radio-group",
      "label": "Radio Group",
      "name": "radio",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB 스크린샷]

![라디오 그룹 구성 요소 유형의 스크린샷](assets/component-types/radio.png)

>[!ENDTABS]

#### 참조 {#reference}

참조 구성 요소 유형은 AEM 자산 선택기를 활성화하여 참조할 AEM 자산을 선택하는 데 사용할 수 있습니다. 모든 AEM 리소스를 선택할 수 있는 [AEM 콘텐츠 구성 요소](#aem-content)와 달리 참조 구성 요소는 자산만 참조할 수 있습니다. 추가 유효성 검사 유형을 제공합니다.

참조 구성 요소 유형을 사용하면 현재 오브젝트에서 다른 데이터 오브젝트로 참조할 수 있습니다.

>[!BEGINTABS]

>[!TAB 샘플]

```json
{
  "id": "reference",
  "fields": [
    {
      "component": "reference",
      "label": "Reference",
      "name": "reference",
      "valueType": "string"
    }
  ]
}
```

>[!TAB 스크린샷]

![참조 구성 요소 유형의 스크린샷](assets/component-types/reference.png)

>[!ENDTABS]

#### 리치 텍스트 {#rich-text}

리치 텍스트를 사용하면 여러 줄의 리치 텍스트를 입력할 수 있습니다.

>[!BEGINTABS]

>[!TAB 샘플 1]

```json
{
  "id": "richtext",
  "fields": [
    {
      "component": "richtext",
      "name": "rte",
      "label": "Rich Text",
      "valueType": "string"
    }
  ]
}
```

>[!TAB 스크린샷]

![텍스트 영역 구성 요소 유형의 스크린샷](assets/component-types/richtext.png)

>[!ENDTABS]

#### 선택 {#select}

선택 구성 요소 유형을 사용하면 드롭다운 메뉴의 미리 정의된 옵션 목록에서 단일 옵션을 선택할 수 있습니다.

>[!BEGINTABS]

>[!TAB 샘플]

```json
{
  "id": "select",
  "fields": [
    {
      "component": "select",
      "label": "Select",
      "name": "select",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB 스크린샷]

![선택 구성 요소 유형의 스크린샷](assets/component-types/select.png)

>[!ENDTABS]

#### 탭 {#tab}

탭 구성 요소 유형을 사용하면 여러 탭에 다른 입력 필드를 함께 그룹화하여 작성자의 레이아웃 구성을 개선할 수 있습니다.

`tab` 정의는 `fields` 배열의 구분자로 생각할 수 있습니다. `tab` 뒤에 오는 모든 항목은 새 `tab`이 나타날 때까지 해당 탭에 배치되며, 이후 항목은 새 탭에 배치됩니다.

모든 탭 위에 항목이 표시되게 하려면, 모든 탭보다 먼저 항목을 정의해야 합니다.

>[!BEGINTABS]

>[!TAB 샘플]

```json
{
  "id": "tab",
  "fields": [
    {
      "component": "tab",
      "label": "Tab 1",
      "name": "tab1"
    },
    {
      "component": "text-input",
      "label": "Text 1",
      "name": "text1",
      "valueType": "string"
    },
    {
      "component": "tab",
      "label": "Tab 2",
      "name": "tab2"
    },
    {
      "component": "text-input",
      "label": "Text 2",
      "name": "text2",
      "valueType": "string"
    }
  ]
}
```

>[!TAB 스크린샷]

![탭 구성 요소 유형의 스크린샷](assets/component-types/tab.png)

>[!ENDTABS]

#### 텍스트 {#text}

텍스트를 사용하면 한 줄의 텍스트를 입력할 수 있습니다. 여기에는 추가 유효성 검사 유형이 포함됩니다.

| 유효성 검사 유형 | 값 유형 | 설명 | 필수 |
|---|---|---|---|
| `minLength` | `number` | 허용되는 최소 문자 수 | 아니요 |
| `maxLength` | `number` | 허용되는 최대 문자 수 | 아니요 |
| `regExp` | `string` | 입력 텍스트와 일치해야 하는 정규 표현식 | 아니요 |
| `customErrorMsg` | `string` | `minLength`, `maxLength`, `regExp` 중 하나 이상이 위반될 경우 표시될 메시지 | 아니요 |

>[!BEGINTABS]

>[!TAB 샘플 1]

```json
{
  "id": "simpletext",
  "fields": [
    {
      "component": "text",
      "name": "text",
      "label": "Simple Text",
      "valueType": "string"
    }
  ]
}
```

>[!TAB 샘플 2]

```json
{
  "id": "another simpletext",
  "fields": [
    {
      "component": "text",
      "name": "text",
      "label": "Simple Text",
      "valueType": "string",
      "valueFormat": "regexp",
      "description": "This is a text input with validation.",
      "required": true,
      "validation": {
        "minLength": 1955,
        "maxLength": 1985,
        "regExp": "^foo:.*",
        "customErrorMsg": "Why don't you make like a tree and get outta here?"
      }
    }
  ]
}
```

>[!TAB 스크린샷]

![텍스트 구성 요소 유형의 스크린샷](assets/component-types/simpletext.png)

>[!ENDTABS]
