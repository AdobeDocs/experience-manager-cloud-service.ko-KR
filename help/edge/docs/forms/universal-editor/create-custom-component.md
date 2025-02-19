---
title: EDS 양식에 대한 사용자 정의 구성 요소 만들기
description: EDS 양식에 대한 사용자 정의 구성 요소 만들기
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '1725'
ht-degree: 5%

---

# WYSIWYG 작성에서 사용자 지정 구성 요소 만들기

Edge Delivery Services Forms 오퍼 맞춤화 기능을 통해 프론트엔드 개발자는 맞춤화된 양식 구성 요소를 구축할 수 있습니다. 이러한 사용자 지정 구성 요소는 WYSIWYG 작성 환경에 원활하게 통합되므로 양식 작성자가 양식 편집기 내에서 구성 요소를 쉽게 추가, 구성 및 관리할 수 있습니다. 사용자 지정 구성 요소를 사용하면 작성자가 기능을 향상시키는 동시에 부드럽고 직관적인 작성 프로세스를 보장할 수 있습니다.

이 문서에서는 사용자 경험을 개선하고 양식의 시각적 매력을 높이기 위해 기본 HTML 양식 구성 요소의 스타일을 지정하여 사용자 정의 구성 요소를 만드는 절차에 대해 설명합니다.

## 전제 조건

사용자 정의 구성 요소 만들기를 시작하기 전에 다음과 같은 작업을 수행할 수 있습니다.

* [기본 HTML 구성 요소](/help/edge/docs/forms/form-components.md)에 대한 기본 지식이 있어야 합니다.
* [CSS 선택기를 사용하여 필드 유형에 따라 양식 필드의 스타일을 지정하는](/help/edge/docs/forms/style-theme-forms.md) 방법 파악

## 사용자 정의 구성 요소 만들기

범용 편집기에서 사용자 지정 구성 요소를 추가하면 양식을 디자인하는 동안 양식 작성자가 사용할 수 있는 새 구성 요소를 만들 수 있습니다. 여기에는 구성 요소 등록, 속성 정의 및 사용 가능한 위치 구성이 포함됩니다. 사용자 지정 구성 요소를 만드는 단계는 다음과 같습니다.

[1. 새 사용자 지정 구성 요소 ](#1-adding-structure-for-new-custom-component)에 대한 구조를 추가하는 중
[2. ](#2-defining-the-properties-of-your-custom-component-for-authoring) 작성을 위한 사용자 지정 구성 요소의 속성을 정의하는 중
[3.  사용자 지정 구성 요소를 WYSIWYG 구성 요소 목록](#3-making-your-custom-component-visible-in-the-wysiwyg-component-list)에 표시
[4. 사용자 지정 구성 요소 등록](#4-registering-your-custom-component)
[5. 사용자 지정 구성 요소에 대한 런타임 동작을 추가하는 중](#5-adding-the-runtime-behaviour-for-your-custom-component)

**range**&#x200B;이라는 새 사용자 지정 구성 요소를 만드는 예를 살펴보겠습니다. 범위 구성 요소는 직선으로 나타나고 최소값, 최대값 또는 선택된 값과 같은 값을 표시합니다.

![범위 구성 요소 스타일](/help/edge/docs/forms/universal-editor/assets/custom-component-range-style.png)

이 문서가 끝날 때까지 처음부터 사용자 지정 구성 요소를 만드는 방법을 배우게 됩니다.

### 1. 새 사용자 지정 구성 요소에 대한 구조 추가

사용자 지정 구성 요소를 사용하려면 먼저 유니버설 편집기에서 사용 가능한 옵션으로 인식하도록 등록해야 합니다. 이 작업은 고유 식별자, 기본 속성 및 구성 요소 구조를 포함하는 구성 요소 정의를 통해 수행됩니다.사용자 지정 구성 요소를 양식 작성에 사용하려면 다음 단계를 수행하십시오.

1. **새 폴더 및 파일 추가**
AEM 프로젝트에서 새 사용자 지정 구성 요소에 대한 새 폴더 및 파일을 추가합니다.
   1. AEM 프로젝트를 열고 `../blocks/form/components/`(으)로 이동합니다.
   1. `../blocks/form/components/<component_name>`에서 사용자 지정 구성 요소에 대한 새 폴더를 추가합니다. 이 예제에서는 `range` 폴더를 만듭니다.
   1. `../blocks/form/components/<component_name>`에 새로 만든 폴더로 이동합니다. 예를 들어 `../blocks/form/components/range`(으)로 이동하여 다음 파일을 추가합니다.
      * `/blocks/form/components/range/_range.json`: 사용자 지정 구성 요소의 정의를 포함합니다.
      * `../blocks/form/components/range/range.css`: 사용자 지정 구성 요소의 스타일을 정의합니다.
      * `../blocks/form/components/range/range.js`: 런타임에 사용자 지정 구성 요소를 사용자 지정합니다.

        ![작성을 위한 사용자 지정 구성 요소 추가](/help/edge/docs/forms/universal-editor/assets/adding-custom-component.png)

        >[!NOTE]
        >
        > JSON 파일의 파일 이름에 접두사로 밑줄(_)이 포함되어 있는지 확인합니다.

1. `/blocks/form/components/range/_range.json` 파일로 이동하여 사용자 지정 구성 요소에 대한 구성 요소 정의를 추가하십시오.

1. **구성 요소 정의 추가**

   정의를 추가하려면 `_range.json` 파일에 추가해야 하는 필드는 다음과 같습니다.

   * **title**: 유니버설 편집기에 표시되는 구성 요소의 제목입니다.
   * **id**: 구성 요소의 고유 식별자입니다.
   * **fieldType**: Forms에서는 특정 유형의 사용자 입력을 캡처하기 위해 다양한 **fieldType**&#x200B;을(를) 지원합니다. 추가 바이트 섹션](#supported-fieldtypes)에서 [지원되는 fieldType을 찾을 수 있습니다.
   * **resourceType**: 각 사용자 지정 구성 요소에는 fieldType을 기반으로 연결된 리소스 유형이 있습니다. 추가 바이트 섹션](#supported-resourcetype)에서 [지원되는 resourceType을 찾을 수 있습니다.
   * **jcr:title**: 제목과 유사하지만 구성 요소의 구조 내에 저장됩니다.
   * **fd:viewType**: 사용자 지정 구성 요소의 이름을 나타냅니다. 구성 요소에 대한 고유 식별자입니다. 구성 요소에 대한 사용자 지정 보기를 만드는 데 필요합니다.

구성 요소 정의를 추가한 후 `_range.json` 파일은 다음과 같습니다.

```javascript
{
  "definitions": [
    {
      "title": "Range",
      "id": "range",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/numberinput/v1/numberinput",
            "template": {
              "jcr:title": "Range",
              "fieldType": "number-input",
              "fd:viewType": "range",
              "enabled": true,
              "visible": true
            }
          }
        }
      }
    }
  ]
}
```

>[!NOTE]
>
> 모든 양식 관련 구성 요소는 범용 편집기에 블록을 추가할 때 Sites와 동일한 접근 방식을 따릅니다. 자세한 내용은 [범용 편집기에서 사용하기 위해 계측된 블록 만들기](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/create-block) 문서를 참조하십시오.

### 2. 작성을 위한 사용자 지정 구성 요소의 속성 정의

사용자 지정 구성 요소에는 양식 작성자가 구성할 수 있는 속성을 지정하는 구성 요소 모델이 포함됩니다. 이러한 속성은 유니버설 편집기의 **속성** 대화 상자에 나타나며 작성자는 레이블, 유효성 검사 규칙, 스타일 및 기타 특성과 같은 설정을 조정할 수 있습니다. 등록 정보를 정의하려면

1. `/blocks/form/components/range/_range.json` 파일로 이동하여 사용자 지정 구성 요소에 대한 구성 요소 모델을 추가합니다.

1. **구성 요소 모델 추가**

   사용자 지정 구성 요소의 구성 요소 모델을 정의하려면 `_range.json` 파일에 관련 필드를 추가해야 합니다.

   1. **새 모델 만들기**

      * 모델 배열에서 새 개체를 추가하고 구성 요소 모델의 `id`을(를) 구성 요소 정의에서 이전에 구성된 `fd:viewType` 속성과 일치하도록 설정합니다.
      * 이 개체 내에 필드 배열을 포함합니다.

   2. **속성 대화 상자의 필드 정의**

      * 필드 배열의 각 개체는 **속성** 대화 상자에 탭으로 나타날 수 있는 컨테이너 형식 구성 요소여야 합니다.
      * 일부 필드는 `models/form-common`에서 사용 가능한 재사용 가능한 속성을 참조할 수 있습니다.

   3. **기존 구성 요소 모델을 참조로 사용**

      * 선택한 `fieldType`에 해당하는 기존 구성 요소 모델의 내용을 복사하고 필요에 따라 수정할 수 있습니다. 예를 들어 `number-input` 구성 요소가 확장되어 **range** 구성 요소가 생성되므로 `models/form-components/_number-input.json`의 모델 배열을 참조로 사용할 수 있습니다.

   구성 요소 모델을 추가한 후 `_range.json` 파일은 다음과 같습니다.

   ```javascript
   "models": [
   {
     "id": "range",
     "fields": [
       {
         "component": "container",
         "name": "basic",
         "label": "Basic",
         "collapsible": false,
         "...": "../../../../models/form-common/_basic-input-fields.json"
       },
       {
         "...": "../../../../models/form-common/_help-container.json"
       },
       {
         "component": "container",
         "name": "validation",
         "label": "Validation",
         "collapsible": true,
         "...": "../../../../models/form-common/_number-validation-fields.json"
       }
     ]
   }
   ]
   ```

   >[!NOTE]
   >
   > 사용자 지정 구성 요소의 **속성** 대화 상자에 새 필드를 추가하려면 [정의된 스키마](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/field-types#loading-model)를 준수하십시오.

   사용자 지정 구성 요소에 [사용자 지정 속성을 추가](#adding-custom-properties-for-your-custom-component)하여 기능을 확장할 수도 있습니다.

#### 사용자 지정 구성 요소에 대한 사용자 지정 속성 추가

사용자 지정 속성을 사용하면 구성 요소의 속성 대화 상자에 설정된 값에 따라 특정 동작을 정의할 수 있습니다. 이렇게 하면 구성 요소의 기능 및 사용자 지정 옵션을 확장할 수 있습니다.

이 예제에서는 단계 값을 범위 구성 요소에 사용자 지정 속성으로 추가합니다.

![단계 값 사용자 지정 속성](/help/edge/docs/forms/universal-editor/assets/customcomponent-stepvalue.png)

단계 값 사용자 지정 속성을 추가하려면 구성 요소 모델을 ` _<component>.json` 파일에 다음 코드 줄로 추가합니다.

```javascript
      {
      "component": "number",
      "name": "stepValue",
      "label": "Step Value",
      "valueType": "number"
      }
```

JSON 코드 조각은 **범위** 구성 요소에 대해 **단계 값**&#x200B;이라는 사용자 지정 속성을 정의합니다. 다음은 각 필드에 대한 분류입니다.

* **component**: 속성 대화 상자에 사용되는 입력 필드 형식을 지정합니다. 이 경우 `number`은(는) 필드가 숫자 값을 허용함을 나타냅니다.
* **name**: 구성 요소의 논리에서 해당 속성을 참조하는 데 사용되는 속성의 식별자입니다. 여기서 `stepValue`은(는) 범위에 대한 단계 값 설정을 나타냅니다.
* **label**: 속성 대화 상자에 표시되는 속성의 표시 이름입니다.
* **valueType**: 속성에 필요한 데이터 형식을 정의합니다. `number`을(를) 사용하면 숫자 입력만 허용됩니다.

이제 `stepValue`을(를) `range.js`의 JSON 속성에서 사용자 지정 속성으로 사용하고 런타임 시 해당 값을 기반으로 동적 동작을 구현할 수 있습니다.

따라서 구성 요소 정의, 구성 요소 모델 및 사용자 지정 속성을 추가한 후 최종 `_range.json` 파일은 다음과 같습니다.

```javascript
 {
  "definitions": [
    {
      "title": "Range",
      "id": "range",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/numberinput/v1/numberinput",
            "template": {
              "jcr:title": "Range",
              "fieldType": "number-input",
              "fd:viewType": "range",
              "enabled": true,
              "visible": true
            }
          }
        }
      }
    }
  ],
  "models": [
    {
      "id": "range",
      "fields": [
        {
          "component": "container",
          "name": "basic",
          "label": "Basic",
          "collapsible": false,
          "...": "../../../../models/form-common/_basic-input-fields.json"
         {
           "component": "number",
           "name": "stepValue",
            "label": "Step Value",
             "valueType": "number"
}
        },
        {
          "...": "../../../../models/form-common/_help-container.json"
        },
        {
          "component": "container",
          "name": "validation",
          "label": "Validation",
          "collapsible": true,
          "...": "../../../../models/form-common/_number-validation-fields.json"
        }
      ]
    }
  ]
}
```

![구성 요소 정의 및 모델](/help/edge/docs/forms/universal-editor/assets/custom-component-json-file.png)


### 3. 사용자 지정 구성 요소를 WYSIWYG 구성 요소 목록에 표시

필터는 범용 편집기에서 사용자 지정 구성 요소를 사용할 수 있는 섹션을 정의합니다. 이렇게 하면 구성 요소를 적절한 섹션에서만 사용할 수 있으므로 구조와 사용성을 유지할 수 있습니다.

WYSIWYG에서 양식을 작성하는 동안 사용자 지정 구성 요소가 사용 가능한 구성 요소 목록에 표시되도록 하려면 다음을 수행하십시오.

1. `/blocks/form/_form.json` 파일로 이동합니다.
1. `id="form"`이(가) 있는 개체 내에서 구성 요소 배열을 찾습니다.
1. `id="form"`을(를) 사용하여 `definitions[]`의 `fd:viewType` 값을 개체의 구성 요소 배열에 추가합니다.

```javascript
 "filters": [
    {
      "id": "form",
      "components": [
        "captcha",
        "checkbox",
        "checkbox-group",
        "date-input",
        "drop-down",
        "email",
        "file-input",
        "form-accordion",
        "form-button",
        "form-fragment",
        "form-image",
        "form-modal",
        "form-reset-button",
        "form-submit-button",
        "number-input",
        "panel",
        "plain-text",
        "radio-group",
        "rating",
        "telephone-input",
        "text-input",
        "tnc",
        "wizard",
        "range"
      ]
    }
  ]
```

![구성 요소 필터](/help/edge/docs/forms/universal-editor/assets/custom-component-form-file.png)

### 4. 사용자 지정 구성 요소 등록

양식 블록이 사용자 지정 구성 요소를 인식하고 양식을 작성하는 동안 구성 요소 모델에 정의된 속성을 로드하도록 하려면 구성 요소 정의의 `fd:viewType` 값을 `mappings.js` 파일에 추가하십시오.
구성 요소를 등록하려면 다음을 수행하십시오.
1. `/blocks/form/mappings.js` 파일로 이동합니다.
1. `customComponents[]` 배열을 찾습니다.
1. `definitions[]` 배열의 `fd:viewType` 값을 `customComponents[]` 배열에 추가합니다.

```javascript
let customComponents = ["range"];
const OOTBComponentDecorators = ['file-input',
                                 'wizard', 
                                 'modal', 'tnc',
                                'toggleable-link',
                                'rating',
                                'datetime',
                                'list',
                                'location',
                                'accordion'];
```

![구성 요소 매핑](/help/edge/docs/forms/universal-editor/assets/custom-component-mapping-file.png)

위의 단계를 완료하면 사용자 지정 구성 요소가 유니버설 편집기 내의 양식 구성 요소 목록에 나타납니다. 그런 다음 양식 섹션으로 끌어다 놓을 수 있습니다.

![범위 구성 요소](/help/edge/docs/forms/universal-editor/assets/custom-component-range.png)

아래 스크린샷에는 양식 작성자가 구성할 수 있는 속성을 지정하는 구성 요소 모델에 추가된 `range` 구성 요소의 속성이 표시됩니다.

![범위 구성 요소의 속성](/help/edge/docs/forms/universal-editor/assets/range-properties.png)

이제 스타일 및 기능을 추가하여 사용자 지정 구성 요소의 런타임 동작을 정의할 수 있습니다.

### 5. 사용자 지정 구성 요소에 대한 런타임 동작 추가

[양식 필드 스타일 지정](/help/edge/docs/forms/style-theme-forms.md)에 설명된 대로 미리 정의된 태그를 사용하여 사용자 지정 구성 요소를 수정할 수 있습니다. 맞춤형 CSS(Cascading Style Sheets) 및 맞춤형 코드를 사용하여 구성 요소의 모양을 향상시킬 수 있습니다. 구성 요소에 런타임 동작을 추가하려면 다음을 수행합니다.

1. 스타일을 추가하려면 `/blocks/form/components/range/range.css` 파일로 이동하여 다음 코드 행을 추가합니다.

   ```javascript
   /** Styling for range */
   main .form .range-widget-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, #ADD8E6 calc(100% * var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% * var(--current-steps)/var(--total-steps)));
   }
   
   main .form .range-widget-wrapper.decorated input[type="range"]:focus {
   outline: none;
   }
   
   .range-widget-wrapper.decorated input[type="range"]::-webkit-slider-thumb {
   appearance: none;
   width: 25px;
   height: 25px;
   border-radius: 50%;
   background: #00008B; /* Dark Blue */
   border: 3px solid #00008B; /* Dark Blue */
   cursor: pointer;
   outline: 3px solid #fff;
   }
   
   .range-widget-wrapper.decorated input[type="range"]:focus::-webkit-slider-thumb {
   border-color: #00008B; /* Dark Blue */
   }
   
   .range-widget-wrapper.decorated .range-bubble {
   color: #00008B; /* Dark Blue */
   font-size: 20px;
   line-height: 28px;
   position: relative;
   display: inline-block;
   padding-bottom: 12px;
   font-weight: bold;
   }
   
   .range-widget-wrapper.decorated .range-min,
   .range-widget-wrapper.decorated .range-max {
   font-size: 14px;
   line-height: 22px;
   color: #494f50;
   margin-top: 16px;
   display: inline-block;
   }
   
   .range-widget-wrapper.decorated .range-max {
   float: right;
   }
   ```
   코드는 사용자 지정 구성 요소의 스타일 및 시각적 모양을 정의하는 데 도움이 됩니다.

1. 기능을 추가하려면 `/blocks/form/components/range/range.js` 파일로 이동하여 다음 코드 행을 추가합니다.

   ```javascript
   function updateBubble(input, element) {
   const step = input.step || 1;
   const max = input.max || 0;
   const min = input.min || 1;
   const value = input.value || 1;
   const current = Math.ceil((value - min) / step);
   const total = Math.ceil((max - min) / step);
   const bubble = element.querySelector('.range-bubble');
   // during initial render the width is 0. Hence using a default here.
   const bubbleWidth = bubble.getBoundingClientRect().width || 31;
   const left = `${(current / total) * 100}% - ${(current / total) * bubbleWidth}px`;
   bubble.innerText = `${value}`;
   const steps = {
       '--total-steps': Math.ceil((max - min) / step),
       '--current-steps': Math.ceil((value - min) / step),
   };
   const style = Object.entries(steps).map(([varName, varValue]) => `${varName}:${varValue}`).join(';');
   bubble.style.left = `calc(${left})`;
   element.setAttribute('style', style);
   }
   
   export default async function decorate(fieldDiv, fieldJson) {
   console.log('RANGE DIV: ', fieldDiv);
   console.log('RANGE JSON: fieldJson', fieldJson);
    const input = fieldDiv.querySelector('input');
   // modify the type in case it is not range.
   input.type = 'range';
   input.min = input.min || 10;
   input.max = input.max || 1000;
   // create a wrapper div to provide the min/max and current value
   const div = document.createElement('div');
   div.className = 'range-widget-wrapper decorated';
   input.after(div);
   const hover = document.createElement('span');
   hover.className = 'range-bubble';
   const rangeMinEl = document.createElement('span');
   rangeMinEl.className = 'range-min';
   const rangeMaxEl = document.createElement('span');
   rangeMaxEl.className = 'range-max';
   rangeMinEl.innerText = `${input.min || 1}`;
   rangeMaxEl.innerText = `${input.max}`;
   div.appendChild(hover);
   // move the input element within the wrapper div
   div.appendChild(input);
   div.appendChild(rangeMinEl);
   div.appendChild(rangeMaxEl);
   input.addEventListener('input', (e) => {
   updateBubble(e.target, div);
   });
   updateBubble(input, div);
   return fieldDiv;
   }
   ```

   사용자 지정 구성 요소가 사용자 입력과 상호 작용하고 데이터를 처리하며 유니버설 편집기의 양식 블록과 통합하는 방법을 제어합니다.

   사용자 지정 스타일 및 기능을 통합하면 범위 구성 요소의 모양과 동작이 향상됩니다. 업데이트된 디자인은 적용된 스타일을 반영하는 반면 추가된 기능은 보다 역동적이고 대화형 사용자 경험을 보장합니다.
아래 스크린샷은 업데이트된 범위 구성 요소를 보여 줍니다.

![범위 구성 요소 스타일](/help/edge/docs/forms/universal-editor/assets/custom-component-range-1.png)

## 자주 묻는 질문

* **component.css와 forms.css에서 스타일을 모두 추가하는 경우 우선 순위가 어느 것입니까?**
`component.css`과(와) **forms.css** 모두에 스타일이 정의된 경우 `component.css`이(가) 우선 순위를 갖습니다. 구성 요소 수준 스타일이 보다 구체적이고 `forms.css`의 전역 스타일에 우선하기 때문입니다.

* **사용자 지정 구성 요소가 유니버설 편집기의 사용 가능한 구성 요소 목록에 표시되지 않습니다. 이 문제를 해결하려면 어떻게 합니까?**
사용자 지정 구성 요소가 표시되지 않으면 다음 파일을 확인하여 구성 요소가 올바르게 등록되었는지 확인하십시오.
   * **component-definition.json**: 구성 요소가 올바르게 정의되었는지 확인하십시오.
   * **component-filters.json**: 구성 요소가 적절한 섹션에서 허용되는지 확인하십시오.
   * **component-models.json**: 구성 요소 모델이 올바르게 구성되었는지 확인하십시오.

## 모범 사례

* 로컬에서 사용자 지정 스타일 및 구성 요소를 개발하려면 [로컬 AEM 개발 환경을 설정](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#set-up-local-aem-development-environment)하는 것이 좋습니다.


## 추가 바이트

### 지원되는 resourceType

| 필드 유형 | 리소스 유형 |
|--------------|------------------------------------------------------------------|
| 텍스트 입력 | core/fd/components/form/textinput/v1/textinput |
| 숫자 입력 | core/fd/components/form/numberinput/v1/numberinput |
| 날짜 입력 | core/fd/components/form/datepicker/v1/datepicker |
| 패널 | core/fd/components/form/panelcontainer/v1/panelcontainer |
| 확인란 | core/fd/components/form/checkbox/v1/checkbox |
| 드롭다운 | core/fd/components/form/dropdown/v1/dropdown |
| 라디오 그룹 | core/fd/components/form/radiobutton/v1/radiobutton |
| 일반 텍스트 | core/fd/components/form/text/v1/text |
| 파일 입력 | core/fd/components/form/fileinput/v2/fileinput |
| 이메일 | core/fd/components/form/emailinput/v1/emailinput |
| 이미지 | core/fd/components/form/image/v1/image |
| 단추 | core/fd/components/form/button/v1/button |

### 지원되는 필드 유형

양식에 지원되는 필드 유형은 다음과 같습니다.
* 텍스트 입력
* 숫자 입력
* 날짜 입력
* 패널
* 확인란
* 드롭다운
* 라디오 그룹
* 일반 텍스트
* 파일 입력
* 이메일
* 이미지
* 단추

## 추가 참조

{{see-more-forms-eds}}
