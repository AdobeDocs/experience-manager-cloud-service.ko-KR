---
title: EDS 양식에 대한 사용자 정의 구성 요소 만들기
description: EDS 양식에 대한 사용자 정의 구성 요소 만들기
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '1789'
ht-degree: 98%

---

# WYSIWYG 작성 사용자 정의 구성 요소 만들기

Edge Delivery Services 양식은 사용자 정의 기능을 제공하여 프론트엔드 개발자가 맞춤형 양식 구성 요소를 구축할 수 있도록 합니다. 이러한 사용자 정의 구성 요소는 WYSIWYG 저작 환경에 완벽하게 통합되어 양식 작성자가 양식 편집기 내에서 쉽게 추가, 구성 및 관리할 수 있습니다. 사용자 정의 구성 요소를 통해 작성자는 기능을 향상시키면서 원활하고 직관적인 작성 과정을 보장할 수 있습니다.

이 문서에서는 사용자 경험을 개선하고 양식의 시각적 매력을 높이기 위해 기본 HTML 양식 구성 요소의 스타일을 지정하여 사용자 정의 구성 요소를 만드는 절차에 대해 설명합니다.

## 사전 요구 사항

사용자 정의 구성 요소 만들기를 시작하기 전에 다음과 같은 작업을 수행할 수 있습니다.

- [기본 HTML 구성 요소](/help/edge/docs/forms/form-components.md)에 대한 기본 지식이 있어야 합니다.
- [CSS 선택기를 사용하여 필드 유형에 따라 양식 필드의 스타일을 지정하는](/help/edge/docs/forms/style-theme-forms.md) 방법 파악

## 사용자 정의 구성 요소 만들기

범용 편집기에 사용자 정의 구성 요소를 추가하면 양식 작성자가 양식을 설계할 때 사용할 수 있는 새로운 구성 요소가 제공됩니다. 이는 구성 요소를 등록하고, 속성을 정의하며, 사용할 수 있는 위치를 구성하는 것을 포함합니다. 사용자 정의 구성 요소를 만드는 절차는 다음과 같습니다.

[1. 새로운 사용자 정의 구성 요소에 대한 구조 추가](#1-adding-structure-for-new-custom-component)
[2. 작성을 위한 사용자 정의 구성 요소의 속성 정의](#2-defining-the-properties-of-your-custom-component-for-authoring)
[3.  WYSIWYG 구성 요소 목록에 사용자 정의 구성 요소 표시](#3-making-your-custom-component-visible-in-the-wysiwyg-component-list)
[4. 사용자 정의 구성 요소 등록](#4-registering-your-custom-component)
[5. 사용자 정의 구성 요소에 대한 런타임 동작 추가](#5-adding-the-runtime-behaviour-for-your-custom-component)

**범위**&#x200B;라는 새로운 사용자 정의 구성 요소를 만드는 예를 들어보겠습니다. 범위 구성 요소는 최소값, 최대값 또는 선택한 값 등의 값으로 표시되고 직선으로 나타납니다.

![최소값과 최대값을 포함하는 슬라이더와 선택된 가치 지표를 보여 주는 범위 구성 요소의 시각적 표현](/help/edge/docs/forms/universal-editor/assets/custom-component-range-style.png)

이 문서를 끝까지 읽으면 사용자 정의 구성 요소를 처음부터 만드는 방법을 배울 수 있습니다.

### &#x200B;1. 새로운 사용자 정의 구성 요소에 대한 구조 추가

사용자 정의 구성 요소를 사용하기 전에 범용 편집기가 이를 사용 가능한 옵션으로 인식할 수 있도록 등록해야 합니다. 이는 고유 식별자, 기본 속성 및 구성 요소의 구조를 포함하는 구성 요소 정의를 통해 이루어집니다. 다음 단계를 수행하여 사용자 정의 구성 요소를 양식 작성에 사용할 수 있도록 합니다.

1. **새 폴더 및 파일 추가**

   AEM 프로젝트에서 새 사용자 지정 구성 요소에 대한 새 폴더 및 파일을 추가합니다.

   1. AEM 프로젝트를 열고 `../blocks/form/components/`로 이동합니다.
   1. 사용자 정의 구성 요소를 위한 새 폴더를 `../blocks/form/components/<component_name>`에 추가합니다. 이 예에서는 이름이 `range`인 폴더를 생성합니다.
   1. `../blocks/form/components/<component_name>`에 새로 만든 폴더로 이동합니다. 예를 들어 `../blocks/form/components/range`로 이동하여 다음 파일을 추가합니다.

      - `/blocks/form/components/range/_range.json`: 사용자 정의 구성 요소의 정의를 포함합니다.
      - `../blocks/form/components/range/range.css`: 사용자 정의 구성 요소에 대한 스타일을 정의합니다.
      - `../blocks/form/components/range/range.js`: 런타임에 사용자 정의 구성 요소를 사용자 정의합니다.

        ![작성을 위한 사용자 정의 구성 요소 추가](/help/edge/docs/forms/universal-editor/assets/adding-custom-component.png)

        >[!NOTE]
        >
        > json 파일의 파일 이름에 밑줄(_)이 접두사로 포함되어 있는지 확인합니다.

1. `/blocks/form/components/range/_range.json` 파일로 이동하여 사용자 정의 구성 요소에 대한 구성 요소 정의를 추가합니다.

1. **구성 요소 정의 추가**

   정의를 추가하기 위해 `_range.json` 파일에 추가해야 하는 필드는 다음과 같습니다.

   - **title**: 범용 편집기에 표시되는 구성 요소의 제목입니다.
   - **id**: 구성 요소의 고유 식별자.
   - **fieldType**: 양식은 특정 유형의 사용자 입력을 캡처하기 위해 다양한 **fieldType**&#x200B;을 지원합니다. [지원되는 fieldType은 추가 바이트 섹션](#supported-fieldtypes)에서 찾을 수 있습니다.
   - **resourceType**: 각 사용자 정의 구성 요소는 해당 fieldType에 따라 연결된 리소스 유형을 갖습니다. [지원되는 resourceType은 추가 바이트 섹션](#supported-resourcetype)에서 찾을 수 있습니다.
   - **jcr:title**: 제목과 유사하지만 구성 요소의 구조 내에 저장됩니다.
   - **fd:viewType**: 사용자 정의 구성 요소의 이름을 나타냅니다. 이는 구성 요소의 고유 식별자입니다. 구성 요소에 대한 사용자 정의 보기를 만들어야 합니다.

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
> 모든 양식 관련 구성 요소는 범용 편집기에 블록을 추가할 때 Sites와 동일한 접근 방식을 따릅니다. 자세한 내용은 [범용 편집기에 사용하도록 구성된 블록 만들기](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/create-block) 문서를 참조하십시오.

### &#x200B;2. 작성을 위한 사용자 정의 구성 요소의 속성 정의

사용자 정의 구성 요소에는 양식 작성자가 구성할 수 있는 속성을 지정하는 구성 요소 모델이 포함되어 있습니다. 이러한 속성은 범용 편집기의 **속성** 대화 상자에 표시되므로 작성자가 레이블, 유효성 검사 규칙, 스타일 및 기타 속성과 같은 설정을 조정할 수 있습니다. 속성을 정의하려면 다음 작업을 수행하십시오.

1. `/blocks/form/components/range/_range.json` 파일로 이동하여 사용자 정의 구성 요소에 대한 구성 요소 모델을 추가합니다.

1. **구성 요소 모델 추가**

   사용자 정의 구성 요소의 구성 요소 모델을 정의하려면 관련 필드를 `_range.json` 파일에 추가해야 합니다.

   1. **새 모델 만들기**

      - 모델 배열에서 새 오브젝트를 추가하고 구성 요소 정의에서 이전에 구성된 `fd:viewType`속성과 일치하도록 구성 요소 모델의 `id`를 설정합니다.
      - 이 오브젝트 내에 필드 배열을 포함합니다.

   2. **속성 대화 상자의 필드 정의**

      - 필드 배열의 각 오브젝트는 컨테이너 유형의 구성 요소여야 하며, 이를 통해 **속성** 대화 상자에 탭으로 표시될 수 있습니다.
      - 일부 필드는 `models/form-common`에서 재사용 가능한 속성을 참조할 수 있습니다.

   3. **기존 구성 요소 모델을 참조로 사용**

      - 선택한 `fieldType`에 해당하는 기존 구성 요소 모델의 내용을 복사하고 필요에 따라 수정할 수 있습니다. 예를 들어 `number-input` 구성 요소는 확장되어 **범위** 구성 요소를 생성하므로 `models/form-components/_number-input.json`의 모델 배열을 참조로 사용할 수 있습니다.

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
   > 사용자 정의 구성 요소의 **속성** 대화 상자에 새 필드를 추가하려면 [정의 스키마](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/field-types#loading-model)를 준수해야 합니다.

   사용자 정의 구성 요소에 [사용자 정의 속성을 추가](#adding-custom-properties-for-your-custom-component)하여 기능을 확장할 수도 있습니다.

#### 사용자 정의 구성 요소에 대한 사용자 정의 속성 추가

사용자 정의 속성을 사용하면 구성 요소의 속성 대화 상자에 설정된 값을 기반으로 특정 동작을 정의할 수 있습니다. 이는 구성 요소의 기능과 사용자 정의 옵션을 확장하는 데 도움이 됩니다.

이 예제에서는 Range 구성 요소에 Step Value를 사용자 정의 속성으로 추가합니다.

![단계 값 사용자 정의 속성](/help/edge/docs/forms/universal-editor/assets/customcomponent-stepvalue.png)

단계 값 사용자 정의 속성을 추가하려면 구성 요소 모델에 ` _<component>.json` 파일의 다음 코드 줄을 추가합니다.

```javascript
      {
      "component": "number",
      "name": "stepValue",
      "label": "Step Value",
      "valueType": "number"
      }
```

JSON 스니펫은 **범위** 구성 요소에 대해 **Step Value**&#x200B;라는 사용자 정의 속성을 정의합니다. 각 필드의 세부 내용은 다음과 같습니다.

- **component**: 속성 대화 상자에서 사용되는 입력 필드의 유형을 지정합니다. 이 경우 `number`는 해당 필드가 숫자 값을 허용함을 나타냅니다.
- **name**: 구성 요소의 논리에서 해당 속성을 참조하는 데 사용되는 식별자입니다. 여기에서 `stepValue`는 범위에 대한 단계 값 설정을 나타냅니다.
- **label**: 속성 대화 상자에 표시되는 속성의 표시 이름입니다.
- **valueType**: 속성에 필요한 데이터 유형을 정의합니다. `number`는 숫자 입력만 허용됨을 나타냅니다.

이제 `range.js`의 JSON 속성에서 사용자 정의 속성으로 `stepValue`를 사용하여 런타임에 해당 값에 따라 동적 동작을 구현할 수 있습니다.

따라서 구성 요소 정의, 구성 요소 모델 및 사용자 정의 속성을 추가한 후의 최종 `_range.json` 파일은 다음과 같습니다.

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


### &#x200B;3. WYSIWYG 구성 요소 목록에 사용자 정의 구성 요소 표시

필터는 범용 편집기에서 사용자 정의 구성 요소를 사용할 수 있는 섹션을 정의합니다. 이를 통해 구성 요소는 구조와 사용성을 유지하면서 적절한 섹션에서만 사용할 수 있습니다.

WYSIWYG에서 양식 작성 중 사용 가능한 구성 요소 목록에 사용자 정의 구성 요소가 표시되도록 하려면:

1. `/blocks/form/_form.json` 파일로 이동합니다.
1. `id="form"`이 있는 오브젝트 내에서 구성 요소 배열을 찾습니다.
1. `id="form"`을 사용하여 `definitions[]`의 `fd:viewType` 값을 오브젝트의 구성 요소 배열에 추가합니다.

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

### &#x200B;4. 사용자 정의 구성 요소 등록

양식 블록이 양식 작성 중에 사용자 정의 구성 요소를 인식하고 구성 요소 모델에 정의된 속성을 로드할 수 있도록 하려면 구성 요소 정의의 `fd:viewType` 값을 `mappings.js` 파일에 추가합니다.

구성 요소를 등록하려면 다음 작업을 수행하십시오.

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

위의 단계를 완료하면 사용자 정의 구성 요소가 범용 편집기 내의 양식 구성 요소 목록에 나타납니다. 그런 다음 양식 섹션으로 끌어다 놓을 수 있습니다.

![드래그 앤 드롭으로 양식에 사용할 수 있는 사용자 정의 범위 구성 요소를 보여 주는 범용 편집기 구성 요소 팔레트의 스크린샷](/help/edge/docs/forms/universal-editor/assets/custom-component-range.png)

아래 스크린샷은 구성 요소 모델에 추가된 `range` 구성 요소의 속성을 보여 줍니다. 이 속성은 양식 작성자가 구성할 수 있는 속성을 지정합니다.

![기본 속성, 유효성 검사 규칙 및 스타일 옵션을 포함한 범위 구성 요소에 대한 구성 가능한 설정을 보여 주는 범용 편집기 속성 패널의 스크린샷](/help/edge/docs/forms/universal-editor/assets/range-properties.png)

이제 스타일링과 기능을 추가하여 사용자 정의 구성 요소의 런타임 동작을 정의할 수 있습니다.

### &#x200B;5. 사용자 정의 구성 요소에 대한 런타임 동작 추가

[양식 필드의 스타일링](/help/edge/docs/forms/style-theme-forms.md)에 설명된 대로 미리 정의된 마크업을 사용하여 사용자 정의 구성 요소를 수정할 수 있습니다. 이는 구성 요소의 모양을 향상시키기 위해 사용자 정의 CSS(Cascading Style Sheets)와 사용자 정의 코드를 사용하여 달성할 수 있습니다. 구성 요소에 런타임 동작을 추가하려면 다음 작업을 수행하십시오.

1. 스타일링을 추가하려면 `/blocks/form/components/range/range.css` 파일로 이동하여 다음 코드 라인을 추가합니다.

   ```javascript
   /** Styling for range */
   main .form .range-widget-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, #ADD8E6 calc(100% - var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% - var(--current-steps)/var(--total-steps)));
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

   이 코드는 사용자 정의 구성 요소의 스타일링과 시각적 모양을 정의하는 데 도움이 됩니다.

1. 기능을 추가하려면 `/blocks/form/components/range/range.js` 파일로 이동하여 다음 코드 라인을 추가합니다.

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

   사용자 정의 구성 요소가 사용자 입력과 상호 작용하는 방식, 데이터를 처리하는 방식, 범용 편집기의 양식 블록과 통합되는 방식을 제어합니다.

   사용자 정의 스타일링과 기능을 통합한 후 범위 구성 요소의 모양과 동작이 향상되었습니다. 업데이트된 디자인은 적용된 스타일을 반영하며, 추가된 기능은 보다 역동적이면서 인터랙티브한 사용자 경험을 보장합니다.
아래 스크린샷은 업데이트된 범위 구성 요소를 보여 줍니다.

![스타일이 지정된 슬라이더와 범용 편집기의 값 버블 표시 및 대화형 기능을 보여 주는 최종 범위 구성 요소](/help/edge/docs/forms/universal-editor/assets/custom-component-range-1.png)

## 자주 묻는 질문

- **component.css와 form.css 모두에 스타일링을 추가하면 어떤 것이 우선시됩니까?**
스타일이 `component.css`와 **forms.css** 모두에서 정의될 때, `component.css`가 우선됩니다. 이는 구성 요소 수준의 스타일이 더 구체적이고 `forms.css`의 글로벌 스타일을 재정의하기 때문입니다.

- **내 사용자 정의 구성 요소가 범용 편집기의 사용 가능한 구성 요소 목록에 표시되지 않습니다. 이를 어떻게 수정할 수 있습니까?**
사용자 정의 구성 요소가 나타나지 않는 경우 다음 파일을 확인하여 구성 요소가 올바르게 등록되었는지 확인합니다.
   - **component-definition.json**: 구성 요소가 올바르게 정의되었는지 확인합니다.
   - **component-filters.json**: 해당 섹션에서 구성 요소가 허용되는지 확인합니다.
   - **component-models.json**: 구성 요소 모델이 올바르게 구성되었는지 확인합니다.

## 모범 사례

- 사용자 정의 스타일과 구성 요소를 로컬에서 개발하기 위한 [로컬 AEM 개발 환경을 설정](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#set-up-local-aem-development-environment)하는 것이 좋습니다.


## 추가 바이트

### 지원되는 resourceType

| 필드 유형 | 리소스 유형 |
|--------------|------------------------------------------------------------------|
| text-input | core/fd/components/form/textinput/v1/textinput |
| number-input | core/fd/components/form/numberinput/v1/numberinput |
| date-input | core/fd/components/form/datepicker/v1/datepicker |
| 패널 | core/fd/components/form/panelcontainer/v1/panelcontainer |
| 확인란 | core/fd/components/form/checkbox/v1/checkbox |
| drop-down | core/fd/components/form/dropdown/v1/dropdown |
| radio-group | core/fd/components/form/radiobutton/v1/radiobutton |
| plain-text | core/fd/components/form/text/v1/text |
| file-input | core/fd/components/form/fileinput/v2/fileinput |
| 이메일 | core/fd/components/form/emailinput/v1/emailinput |
| 이미지 | core/fd/components/form/image/v1/image |
| 버튼 | core/fd/components/form/button/v1/button |

### 지원되는 fieldTypes

양식에 지원되는 fieldTypes는 다음과 같습니다.

- text-input
- number-input
- date-input
- 패널
- plain-text
- file-input
- 이메일
- 이미지
- 버튼
- 확인란
- drop-down
- radio-group

