---
title: 필드 유형
description: 나만의 앱을 계측하는 방법에 대한 예제를 통해 유니버설 편집기가 구성 요소 레일에서 편집할 수 있는 다양한 유형의 필드에 대해 알아봅니다.
exl-id: cb4567b8-ebec-477c-b7b9-53f25b533192
source-git-commit: 7ef3efa6e074778b7b3e3a8159056200b2663b30
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 7%

---


# 필드 유형 {#field-types}

나만의 앱을 계측하는 방법에 대한 예제를 통해 유니버설 편집기가 구성 요소 레일에서 편집할 수 있는 다양한 유형의 필드에 대해 알아봅니다.

{{universal-editor-status}}

## 개요 {#overview}

범용 편집기에서 사용할 앱을 조정할 때 구성 요소를 계측하고 편집기의 구성 요소 레일에서 조작할 수 있는 데이터 유형을 정의해야 합니다.

이 문서에서는 예제 구성과 함께 사용할 수 있는 필드 유형에 대한 개요를 제공합니다.

>[!TIP]
>
>범용 편집기에 사용할 앱을 계측하는 방법에 익숙하지 않은 경우 문서를 참조하십시오 [AEM 개발자를 위한 유니버설 편집기 개요.](/help/implementing/universal-editor/developer-overview.md)

## 부울 {#boolean}

부울 필드는 확인란으로 렌더링된 간단한 true/false 값을 저장합니다.

### 샘플 {#sample-boolean}

```json
{
  "fields": [   
   {
      "component": "boolean",
      "valueType": "boolean",
      "name": "field1",
      "label": "Boolean Field",
      "description": "This is a boolean field.",
      "required": true,
      "placeholder": null,
      "validation": {
        "customErrorMsg": "This is an error."
      }
    }
  ]
}
```

## 확인란 그룹 {#checkbox-group}

부울과 유사하게 확인란 그룹을 사용하여 여러 개의 true/false 항목을 선택할 수 있습니다.

### 샘플 {#sample-checkbox-group}

```json
{
  "fields": [   
   {
      "component": "checkbox-group",
      "valueType": "string-array",
      "name": "field1",
      "label": "Checkbox Group",
      "description": "This is a checkbox group.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "First option", "value": "one" },
        { "name": "Second option", "value": "two" },
        { "name": "Third option", "value": "three" }
      ]
    }
  ]
}
```

## 날짜/시간 {#date-time}

날짜 시간 필드는 날짜, 시간 또는 이들의 조합을 특정할 수 있도록 한다.

### 샘플 {#sample-date-time}

```json
{
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

## 숫자 {#number}

숫자 필드를 사용하면 숫자를 입력할 수 있습니다.

### 샘플 {#sample-number}

```json
{
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
        "numberMin": null,
        "numberMax": null,
        "customErrorMsg": "Please don't do that."
      }
    }
  ]
}
```

## 라디오 그룹 {#radio-group}

라디오 그룹을 사용하면 확인란 그룹과 유사한 그룹으로 렌더링된 여러 옵션에서 상호 배타적으로 선택할 수 있습니다.

### 샘플 {#sample-radio-group}

```json
{
  "fields": [   
   {
      "component": "radio-group",
      "valueType": "string",
      "name": "field1",
      "label": "Radio Group",
      "description": "This is a radio group.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "Option One", "value": "one" },
        { "name": "Option Two", "value": "two" },
        { "name": "Option Three", "value": "three" }
      ]
    }
  ]
}
```

## 참조 {#reference}

참조를 사용하면 현재 개체에서 다른 데이터 개체를 참조로 지정할 수 있습니다.

## 선택 {#select}

선택 을 사용하면 드롭다운 메뉴에서 사전 정의된 옵션을 하나 이상 선택할 수 있습니다.

### 샘플 {#sample-select}

```json
{
  "fields": [   
   {
      "component": "select",
      "valueType": "string",
      "name": "field1",
      "label": "Select",
      "description": "This is a select.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "Option One", "value": "one" },
        { "name": "Option Two", "value": "two" },
        { "name": "Option Three", "value": "three" }
      ],
      "emptyOption": true
    }
  ]
}
```

## 텍스트 영역 {#text-area}

텍스트 영역을 사용하면 여러 줄 텍스트를 입력할 수 있습니다.

### 샘플 {#sample-text-area}

```json
{
  "fields": [   
   {
      "component": "text-area",
      "valueType": "string",
      "name": "field1",
      "label": "Text Area",
      "description": "This is a text area.",
      "required": true,
      "multi": true,
      "placeholder": null,
      "mimeType": "text/x-markdown"
    }
  ]
}
```

## 텍스트 입력 {#text-input}

텍스트 입력을 사용하면 한 줄의 텍스트를 입력할 수 있습니다.

### 샘플 {#sample-text-input}

```json
{
  "fields": [   
   {
      "component": "text-input",
      "valueType": "string",
      "name": "field1",
      "label": "Text Input",
      "description": "This is a text input.",
      "required": true,
      "multi": true,
      "placeholder": null
    },
    {
      "component": "text-input",
      "valueType": "string",
      "name": "field2",
      "label": "Another Text Input",
      "description": "This is a text input with validation.",
      "required": true,
      "multi": true,
      "placeholder": null,
      "validation": {
        "minLength": 5,
        "maxLength": 10,
        "regExp": "^foo:.*",
        "customErrorMsg": "I'm sorry, Dave. I can't do that."
      }
    }
  ]
}
```

## 탭 {#tab}

탭에서는 다른 입력 필드를 여러 탭에서 함께 그룹화하여 작성자의 레이아웃 구성을 개선할 수 있습니다.

A `tab` 정의는 배열의 구분 기호로 생각할 수 있습니다. `fields`. 다음에 오는 모든 것 `tab` 이(가) 새 `tab` 이 발생하면 다음 항목이 새 탭에 배치됩니다.

모든 탭 위에 표시되는 항목을 포함하려면 탭 앞에 항목을 정의해야 합니다.

### 샘플 {#sample-tab}

```json
{
  "id": "title",
  "fields": [
    {
      "component": "tab",
      "label": "Tab",
      "name": "tab1"
    },
    {
      "component": "text-input",
      "name": "tab-response",
      "value": "",
      "placeholder": "Tab? I can't give you a tab unless you order something.",
      "label": "Lou",
      "valueType": "string"
    },
    {
      "component": "tab",
      "label": "Pepsi Free",
      "name": "tab2"
    },
    {
      "component": "text-input",
      "name": "pepsi-free-response",
      "value": "",
      "placeholder": "You want a Pepsi, pal, you're gonna pay for it.",
      "label": "Mr. Carruthers",
      "valueType": "string"
    },
    {
      "component": "select",
      "name": "without-sugar",
      "value": "coffee",
      "label": "Something without sugar",
      "valueType": "string",
      "options": [
        { "name": "Coffee", "value": "coffee" },
        { "name": "Hot Coffee", "value": "hot-coffee" },
        { "name": "Hotter Coffee", "value": "hotter-coffee" }
      ]
    }
  ]
}
```
