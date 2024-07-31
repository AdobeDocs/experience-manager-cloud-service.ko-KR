---
title: EDS 양식에 대한 사용자 정의 구성 요소 만들기
description: EDS 양식에 대한 사용자 정의 구성 요소 만들기
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 77e90657-38db-4a49-9aac-3f3774b62624
role: Admin, Architect, Developer
source-git-commit: 4356fcc73a9c33a11365b1eb3f2ebee5c9de24f0
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 4%

---

# 사용자 정의 구성 요소 만들기

AEM Forms Edge Delivery Services을 사용하면 [기본 HTML 양식 구성 요소](/help/edge/docs/forms/form-components.md)를 사용자 지정하고 사용자에게 친숙한 대화형 양식을 만들 수 있습니다. 사용자 지정 CSS(Cascading Style Sheets)와 구성 요소를 장식하기 위한 사용자 지정 코드를 사용하여 [양식 필드 스타일 지정](/help/edge/docs/forms/style-theme-forms.md)에 설명된 대로 미리 정의된 마크업으로 양식 구성 요소를 수정할 수 있으므로 적응형 Forms 블록 내에서 양식 필드의 모양을 향상시킬 수 있습니다.

![사용자 지정 구성 요소](/help/edge/assets/custom-component-image.png)

이 문서에서는 사용자 경험을 개선하고 양식의 시각적 매력을 높이기 위해 기본 HTML 양식 구성 요소의 스타일을 지정하여 사용자 지정 구성 요소를 만드는 단계를 간략하게 설명합니다.

양식에 `Estimated trip cost`을(를) 표시하는 `range` 구성 요소의 예를 들어 보겠습니다. `range` 구성 요소는 최소값, 최대값 또는 선택된 값과 같은 값을 표시하지 않고 직선으로 표시됩니다.

![기본 범위 구성 요소](/help/edge/assets/native-range-component.png)

CSS를 사용하여 스타일을 추가하고 구성 요소를 장식하는 사용자 지정 함수를 추가하여 라인에서 최소, 최대 및 선택된 값을 표시하도록 `range` 필드를 사용자 지정해 보겠습니다.

![사용자 지정 범위 구성 요소](/help/edge/assets/custom-range-component.png)

이 문서가 끝날 때까지 CSS 파일 및 사용자 지정 함수에서 스타일을 추가하여 사용자 지정 구성 요소를 만드는 방법을 배웁니다.

## 전제 조건

사용자 지정 구성 요소를 만들기 전에 다음을 수행해야 합니다.

* [기본 HTML 구성 요소](/help/edge/docs/forms/form-components.md)에 대한 기본 지식을 갖추고 있습니다.
* CSS 선택기를 사용하여 필드 유형에 따라 [양식 필드를 스타일링하는 방법을 알아보세요](/help/edge/docs/forms/style-theme-forms.md)


## 사용자 지정 구성 요소 만들기


사용자 지정 구성 요소를 만드는 ![단계](/help/edge/docs/forms/assets/steps-to-create-custom-component.png)

이제 각 단계를 자세히 살펴보겠습니다.

아래 설명된 단계에 따라 [조회 스프레드시트](/help/edge/docs/forms/assets/enquiry.xlsx)를 참조하여 `range` 구성 요소를 사용자 지정합니다.

### 구성 요소를 장식할 사용자 지정 기능 추가

`[../Form Block/components]`에 추가된 사용자 지정 함수는 다음으로 구성됩니다.

* **함수 선언**: 함수 이름과 매개 변수를 정의합니다.
* **논리 구현**: 구성 요소에 대한 사용자 지정 동작을 추가하는 논리를 작성하십시오.
* **함수 내보내기**: `[Form Block]`에서 함수에 액세스할 수 있도록 합니다.

범위 구성 요소의 스타일을 지정하기 위해 이름이 `range.js`인 JavaScript 파일을 만들어 보겠습니다. 사용자 지정 함수를 추가하려면:

1. Google 드라이브 또는 SharePoint의 AEM 프로젝트 폴더로 이동합니다.
1. `[../Form Block/components]`(으)로 이동합니다.
1. 이름이 `range.js`인 새 파일을 추가합니다.
1. 다음 코드 행을 추가합니다.

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
   '--total-steps': Math.ceil((max - min) /    step),
   '--current-steps': Math.ceil((value - min) / step),
   };
   const style = Object.entries(steps).map(([varName, varValue]) => `${varName}:${varValue}`).join(';');
   bubble.style.left = `calc(${left})`;
   element.setAttribute('style', style);
   }
   // eslint-disable-next-line no-unused-vars
   export default function decorateRange(fieldDiv, field) {
   loadCSS('/blocks/form/components/range/range.css');
   const input = fieldDiv.querySelector('input');
   // modify the type in case it is not range.
   input.type = 'range';
   input.min = input.min || 1;
   // create a wrapper div to provide the min/max and current value
   const div = document.createElement('div');
   div.className = 'range-widget-wrapper';
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
   // as a best practice add a custom css class to apply custom styling
   fieldDiv.classList.add('decorated');
   return fieldDiv;    
   }
   ```

1. 변경 사항을 저장합니다.

### 양식 블록에 장식기 삽입

`[Form Block]`은(는) 의미 체계 HTML을 사용하여 입력 필드, 레이블 및 도움말 텍스트가 포함된 양식 필드를 접근성을 위한 표준 특성으로 렌더링합니다. `[Form Block]`이(가) 지정된 구성 요소에 대해 사용자 지정 Decorator를 사용하도록 하려면 `mappings.js` 파일에서 이를 정의합니다. `mappings.js` 파일은 특정 구성 요소를 장식하는 모듈을 반환하는 함수를 가져옵니다. 이 함수는 필드 속성을 가져오고 양식 필드에 대한 데코레이터 함수를 반환합니다.

이 경우 함수는 필드의 `fieldType` 속성을 확인하고 `[../Form Block/components]`에 있는 `range.js` 파일에서 사용자 지정 범위 데코레이터를 반환합니다.

양식 블록에 데코레이터를 삽입하려면 다음을 수행합니다.

1. `[../Form Block/]`(으)로 이동하여 `mapping.js`을(를) 엽니다.
1. 다음 코드 행을 추가합니다.

   ```javascript
   export default async function componentDecorator(fd) {
   const { ':type': type = '', fieldType } = fd;
   .... existing code ....
   if (fieldType === 'range') {
   const module = await import('./components/range.js');
   return module.default;
   }
    return null; // null should be returned to use the original markup
   }
   ```

1. 변경 사항을 저장합니다.

### CSS 파일에 구성 요소의 스타일 추가

CSS 선택기를 사용하여 필드 유형 및 필드 이름에 따라 양식 필드의 모양을 변경할 수 있으므로 요구 사항에 따라 일관되거나 고유한 스타일을 지정할 수 있습니다. 구성 요소의 스타일을 지정하려면 `form.css` 파일에 코드를 추가하여 양식 구성 요소의 모양과 느낌을 수정하십시오.

`range` 구성 요소의 스타일을 사용자 지정하려면 `range` 입력 요소와 관련 구성 요소를 양식에 스타일링하는 CSS 코드 조각을 포함하십시오. 이는 `.form` 및 `.range-wrapper`과(와) 같은 클래스가 있는 구조화된 HTML 레이아웃을 가정합니다.

CSS 파일의 구성 요소에 대한 스타일을 추가하려면 다음을 수행합니다.
1. `[../Form Block/]`(으)로 이동하여 `form.css`을(를) 엽니다.
1. 다음 코드 행을 추가합니다.

   ```javascript
       /** styling for range */
   main .form .range-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, var(--button-primary-color) calc(100% * var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% * var(--current-steps)/var(--total-steps)));
   }
   
   main .form .range-wrapper.decorated input[type="range"]:focus {
   outline: none;
   }
   
   .range-wrapper.decorated input[type="range"]::-webkit-slider-thumb {
   appearance: none;
   width: 25px;
   height: 25px;
   border-radius: 50%;
   background: #fff;
   border: 3px solid var(--button-primary-color);
   cursor: pointer;
   outline: 3px solid #fff;
   }
   
   .range-wrapper.decorated input[type="range"]:focus::-webkit-slider-thumb {
   border-color: var(--button-primary-color);
   }
   
   .range-wrapper.decorated .range-bubble {
   color: #17252e;
   font-size: 20px;
   line-height: 28px;
   position: relative;
   display: inline-block;
   padding-bottom: 12px;
   }
   
   .range-wrapper.decorated .range-min,
   .range-wrapper.decorated .range-max {
   font-size: 14px;
   line-height: 22px;
   color: #494f50;
   margin-top: 16px;
   display: inline-block;
   }
   
   .range-wrapper.decorated .range-max {
   float: right;
   }
   ```
1. 변경 사항을 저장합니다.

### 파일 배포 및 프로젝트 빌드

업데이트된 `range.js`, `mapping.css` 및 `form.css` 파일을 GitHub 프로젝트에 배포하고 빌드 성공 여부를 확인합니다.

### AEM 사이드 킥을 사용하여 양식 미리 보기

[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을(를) 사용하여 `range` 구성 요소의 스타일을 지정하는 새로 구현된 함수를 사용하여 양식을 미리 봅니다.

![사용자 지정 구성 요소 양식](/help/edge/assets/custom-componet-form.png)

`range` 구성 요소에 대한 새 스타일은 CSS를 사용한 스타일과 구성 요소에 대한 데코레이터가 포함된 사용자 지정 함수를 사용하여 줄에 최소, 최대 및 선택한 값을 표시합니다.


## 추가 참조

{{see-more-forms-eds}}



