---
title: AEM Forms Edge Delivery Services 양식의 테마 및 스타일 사용자 정의
description: AEM Forms Edge Delivery Services 양식의 테마 및 스타일 사용자 정의
feature: Edge Delivery Services
exl-id: c214711c-979b-4833-9541-8e35b2aa8e09
source-git-commit: 5eee563a9a425ef187afed69a8159d8b1298dad7
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 68%

---


# 양식 모양 사용자 지정

Forms는 사용자가 데이터를 입력할 수 있도록 해 주며 웹 사이트에서 사용자 상호 작용에 중요한 역할을 합니다. CSS(Cascading Style Sheet)를 사용하여 양식의 필드에 스타일을 지정하여 양식의 시각적 프레젠테이션을 강화하고 사용자 경험을 향상시킬 수 있습니다.

적응형 Forms 블록은 모든 양식 필드에 대해 일관된 구조를 생성합니다. 일관된 구조를 사용하면 CSS 선택기를 개발하여 필드 유형 및 필드 이름에 따라 양식 필드를 선택하고 스타일을 지정할 수 있습니다.

이 문서에서는 다양한 양식 구성 요소의 HTML 구조에 대해 간략하게 설명합니다. 이 문서는 다양한 양식 필드에 대한 CSS 선택기를 만들어 적응형 Forms 블록의 양식 필드에 스타일을 지정하는 방법에 대한 이해를 돕습니다.

이 문서의 끝까지:

* 적응형 Forms 블록에 포함된 기본 CSS 파일의 구조를 이해할 수 있습니다.
* 일반 구성 요소와 드롭다운, 라디오 그룹, 확인란 그룹과 같은 특정 구성 요소를 포함하여 적응형 Forms 블록에서 제공하는 양식 구성 요소의 HTML 구조를 이해합니다.
* CSS 선택기를 사용하여 필드 유형 및 필드 이름에 따라 양식 필드의 스타일을 지정하여 요구 사항에 따라 일관되거나 고유한 스타일을 지정하는 방법을 배웁니다.


## 양식 필드 유형 이해

스타일링에 들어가기 전에, 일반적인 형태를 검토해 보겠습니다 [필드 유형](/help/edge/docs/forms/form-components.md) 적응형 Forms 블록에서 지원:

* 입력 필드: 여기에는 텍스트 입력, 이메일 입력, 암호 입력 등이 포함됩니다.
* 확인란 그룹: 여러 옵션을 선택하는 데 사용됩니다.
* 라디오 그룹: 그룹에서 하나의 옵션만 선택하는 데 사용됩니다.
* 드롭다운: 선택 상자라고도 하며 목록에서 하나의 옵션을 선택하는 데 사용됩니다.
* 패널/컨테이너: 관련 양식 요소를 그룹화하는 데 사용됩니다.

## 기본 스타일 지정 원칙

이해 [기본 CSS 개념](https://www.w3schools.com/css/css_intro.asp) 은 특정 양식 필드를 스타일링하기 전에 매우 중요합니다.

* [선택기](https://www.w3schools.com/css/css_selectors.asp): CSS 선택기를 사용하여 스타일을 지정할 특정 HTML 요소를 타깃팅할 수 있습니다. 요소 선택기, 클래스 선택기 또는 ID 선택기를 사용할 수 있습니다.
* [속성](https://www.w3schools.com/css/css_syntax.asp): CSS 속성은 요소의 시각적 모양을 정의합니다. 스타일 양식 필드의 일반적인 속성에는 색상, 배경색, 테두리, 패딩, 여백 등이 포함됩니다.
* [상자 모델](https://www.w3schools.com/css/css_boxmodel.asp): CSS 상자 모델은 HTML 요소의 구조를 패딩, 테두리 및 여백으로 둘러싸인 콘텐츠 영역으로 설명합니다.
* Flexbox/Grid: CSS [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp) 및 [격자 레이아웃](https://www.w3schools.com/css/css_grid.asp) 는 반응형 및 유연한 설계를 위한 강력한 도구입니다.

## 적응형 양식 블록의 양식 스타일 지정

적응형 양식 블록은 표준화된 HTML 구조를 제공하여 양식 구성 요소 선택 및 스타일 지정 프로세스를 단순화합니다.

* **기본 스타일 업데이트**: `/blocks/form/form.css file`을 편집하여 양식의 기본 스타일을 수정할 수 있습니다. 이 파일은 다단계 마법사 양식을 지원하여 양식에 대한 포괄적인 스타일을 제공합니다. 양식 전반에 걸쳐 손쉬운 사용자 정의, 유지 관리 및 균일한 스타일 지정을 위해 사용자 정의 CSS 변수 사용을 강조합니다. 프로젝트에 적응형 양식 블록을 추가하는 방법에 대한 지침은 [양식 만들기](/help/edge/docs/forms/create-forms.md)를 참조하십시오.

* **사용자 정의**: 기본 `forms.css`를 베이스로 사용하고 이를 사용자 정의하여 구성 요소의 모양과 느낌을 수정하면 시각적으로 매력적이고 사용자 친화적인 구성 요소를 만들 수 있습니다. 파일 구조를 조직하고 양식 스타일을 유지하여 웹 사이트 전체에서 디자인의 일관성을 유지합니다.

## forms.css 구조 분류

* **전역 변수:** 다음에서 정의됨 `:root` level, 이러한 변수(`--variable-name`) 일관성과 간편한 업데이트를 위해 스타일시트 전체에 사용된 값을 저장합니다. 이러한 변수는 색상, 글꼴 크기, 패딩 및 기타 속성을 정의합니다. 나만의 전역 변수를 선언하거나 기존 변수를 수정하여 양식 스타일을 변경할 수 있습니다.

* **범용 선택기 스타일:** `*` 선택기는 양식의 모든 요소와 일치하여 `box-sizing` 속성을 `border-box`로 설정하는 등 기본적으로 구성 요소에 스타일을 적용할 수 있도록 합니다.

* **양식 스타일 지정:** 이 섹션에서는 선택기를 사용하여 양식 구성 요소의 스타일을 지정해 특정 HTML 요소를 타겟팅하는 데 중점을 둡니다. 입력 필드, 텍스트 영역, 확인란, 라디오 버튼, 파일 입력, 양식 레이블 및 설명에 대한 스타일을 정의합니다.

* **마법사 스타일 지정(해당하는 경우):** 이 섹션에서는 각 단계가 한 번에 하나씩 표시되는 다단계 형식인 마법사 레이아웃의 스타일을 지정하는 데 중점을 둡니다. 마법사 컨테이너, Fieldset, 범례, 탐색 버튼 및 반응형 레이아웃에 대한 스타일을 정의합니다.

* **미디어 쿼리:** 다양한 화면 크기를 위한 스타일을 제공하여 그에 따라 레이아웃과 스타일을 조정할 수 있습니다.

* **기타 스타일 지정:** 이 섹션에서는 성공 또는 오류 메시지 스타일, 파일 업로드 영역 및 양식에서 접할 수 있는 기타 요소 등을 다룹니다.


## 구성 요소 구조

적응형 양식 블록은 다양한 양식 요소에 대해 일관된 HTML 구조를 제공하므로 스타일 지정과 관리를 더 용이하게 해 줍니다. 스타일 지정을 위해 CSS를 사용하여 구성 요소를 조작할 수 있습니다.

### 일반 구성 요소(드롭다운, 라디오 그룹 및 확인란 그룹 제외):

드롭다운, 라디오 그룹 및 확인란 그룹을 제외한 모든 양식 필드에는 다음과 같은 HTML 구조가 있습니다.

+++ 일반 구성 요소의 HTML 구조

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

* 클래스: div 요소에는 특정 요소 및 스타일을 타겟팅하기 위한 여러 클래스가 있습니다. 다음이 필요합니다. `{Type}-wrapper` 또는 `field-{Name}` 클래스를 사용하여 CSS 선택기를 개발하여 양식 필드를 스타일링할 수 있습니다.
   * {Type}: 필드 유형으로 구성 요소를 식별합니다. 그 예로는 텍스트(text-wrapper), 숫자(number-wrapper), 날짜(date-wrapper)가 있습니다.
   * {Name}: 이름으로 구성 요소를 식별합니다. 필드 이름에는 영숫자 문자만 사용할 수 있으며 이름에 있는 여러 개의 연속 대시는 하나의 대시`(-)`로 대체됩니다. 필드 이름의 시작 및 끝에 있는 대시는 제거됩니다. 그 예로는 이름(field-first-name field-wrapper)이 있습니다.
   * {FieldId}: 자동으로 생성된 필드의 고유 식별자입니다.
   * {Required}: 필드가 필수인지 여부를 나타내는 부울입니다.
* 레이블: `label` 요소는 필드에 대한 설명 텍스트를 제공하고 `for` 속성을 사용하여 이를 입력 요소와 연결합니다.
* 입력: `input` 요소는 입력할 데이터 유형을 정의합니다. 예를 들어 문자, 숫자, 이메일 등이 있습니다.
* 설명(선택 사항): `field-description` 클래스가 있는 `div`는 사용자에게 추가 정보 또는 지침을 제공합니다.

**HTML 구조의 예**

```HTML
<div class="text-wrapper field-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

+++

+++ 일반 구성 요소용 CSS 선택기

```CSS
  
  /* Target all input fields within any .{Type}-wrapper  */
  .{Type}-wrapper  {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  }
  
  /* Target all input fields within any .{Type}-wrapper  */
  .{Type}-wrapper input {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  }
  
  /* Target any element with the class field-{Name}  */
  .field-{Name} {
    /* Add your styles here */
    /* This could be used for styles specific to all elements with   field-{Name} class, not just inputs */
  }
  
  
```

* `.{Type}-wrapper`: 외부를 타깃팅합니다 `div` 필드 형식을 기반으로 하는 요소입니다. 예를 들어, `.text-wrapper` 는 모든 텍스트 필드를 타깃팅합니다.
* `.field-{Name}`: 특정 필드 이름을 기반으로 요소를 추가로 선택합니다. 예를 들어, `.field-first-name` 는 &quot;이름&quot; 텍스트 필드를 타깃팅합니다. 반면에 이 선택기는 필드가 있는 요소를 타겟팅하는 데 사용할 수 있습니다.{Name} 수업, 조심하는 것이 중요하다. 이 경우 입력 자체뿐만 아니라 레이블 및 설명 요소도 타겟팅하므로 입력 필드의 스타일을 지정하는 데 유용하지 않습니다. 텍스트 입력 필드(.text-wrapper input) 타깃팅에 사용하는 선택기와 같이 보다 구체적인 선택기를 사용하는 것이 좋습니다.



**일반 구성 요소에 대한 CSS 선택기 예**

```CSS
/*Target all text input fields */

text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/*Target all fields with name first-name*/

first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```
+++

### 드롭다운 구성 요소

드롭다운 메뉴의 경우 `input` 요소 대신 `select` 요소가 사용됩니다.



+++ 드롭다운 구성 요소의 HTML 구조

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**HTML 구조의 예**

```HTML
<div class="drop-down-wrapper field-country field-wrapper" data-required="true">
  <label for="country" class="field-label">Country</label>
  <select id="country" name="country">
    <option value="">Select Country</option>
    <option value="US">United States</option>
    <option value="CA">Canada</option>
  </select>
  <div class="field-description" aria-live="polite" id="country-description">
    Please select your country of residence.
  </div>
</div>
```

+++

+++ 드롭다운 구성 요소용 CSS 선택기

다음 CSS에는 드롭다운 구성 요소에 대한 몇 가지 예제 CSS 선택기가 나와 있습니다.

```CSS
/* Target the outer wrapper */
.drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
.drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style the dropdown itself */
.drop-down-wrapper select {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  background-color: white; /* Ensure a consistent background */
  /* Adjust arrow appearance as needed */
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

/* Optional: Style the dropdown arrow */
.drop-down-wrapper select::-ms-expand {
  display: none; /* Hide the default arrow for IE11 */
}

.drop-down-wrapper select::after {
  content: "\25BC";
  font-size: 12px;
  color: #ccc;
  /* Adjust positioning as needed */
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
}
```

* 래퍼 타겟팅: 첫 번째 선택기(`.drop-down-wrapper`)는 외부 래퍼 요소를 타겟팅하여 스타일이 전체 드롭다운 구성 요소에 적용되도록 합니다.
* Flexbox 레이아웃: Flexbox는 깔끔한 레이아웃을 위해 레이블, 드롭다운 및 설명을 수직으로 정렬합니다.
* 레이블 스타일: 더 굵은 글꼴 두께와 약간의 여백으로 레이블을 돋보이게 합니다.
* 드롭다운 스타일: `select` 요소는 광택있는 모양의 테두리, 패딩 및 둥근 모서리를 받습니다.
* 배경색: 시각적인 조화를 위해 일관된 배경색을 설정합니다.
* 화살표 맞춤화: 선택적 스타일로 기본 드롭다운 화살표를 숨기고 유니코드 문자와 위치 지정을 사용하여 사용자 정의 화살표를 만듭니다.

+++

### 라디오 그룹

드롭다운 구성 요소와 유사하게 라디오 그룹에는 고유한 HTML 구조 및 CSS 구조가 있습니다.

+++ 라디오 그룹의 HTML 구조

```HTML
<fieldset class="radio-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="radio" value="" id="{UniqueId}" data-field-type="radio-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

#### HTML 구조 예

```HTML
<fieldset class="radio-group-wrapper field-color field-wrapper" id="color_preference" name="color_preference" data-required="true">
  <legend for="color_preference" class="field-label">Favorite Color:</legend>
  <% for each radio in Group %>
    <div class="radio-wrapper field-color">
      <input type="radio" value="red" id="color_red" data-field-type="radio-group" name="color_preference">
      <label for="color_red" class="field-label">Red</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="green" id="color_green" data-field-type="radio-group" name="color_preference">
      <label for="color_green" class="field-label">Green</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="blue" id="color_blue" data-field-type="radio-group" name="color_preference">
      <label for="color_blue" class="field-label">Blue</label>
    </div>
  <% end for %>
</fieldset>
```

+++

+++ 라디오 그룹용 CSS 선택기

* Fieldset 타겟팅

```CSS
  .radio-group-wrapper {
    border: 1px solid #ccc;
    padding: 10px;
  }
```

이 선택기는 radio-group-wrapper 클래스가 있는 모든 필드 세트를 대상으로 합니다. 전체 라디오 그룹에 일반 스타일을 적용하는 데 유용합니다.

* 라디오 버튼 레이블 타겟팅

```CSS
.radio-wrapper label {
    font-weight: normal;
    margin-right: 10px;
  }
```

* 이름을 기준으로 특정 Fieldset 내의 모든 라디오 버튼 레이블을 타겟팅합니다.

```CSS
.field-color .radio-wrapper label {
  /* Your styles here */
}
```

+++

### 확인란 그룹

+++ 확인란 그룹의 HTML 구조

```HTML
<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

#### HTML 구조 예

```HTML
<fieldset class="checkbox-group-wrapper field-topping field-wrapper" id="topping_preference" name="topping_preference" data-required="false">
  <legend for="topping_preference" class="field-label">Pizza Toppings:</legend>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="pepperoni" id="topping_pepperoni" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_pepperoni" class="field-label">Pepperoni</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="mushrooms" id="topping_mushrooms" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_mushrooms" class="field-label">Mushrooms</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="onions" id="topping_onions" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_onions" class="field-label">Onions</label>
  </div>
</fieldset>
```

+++

+++ 확인란 그룹용 CSS 선택기

* 외부 래퍼 타겟팅: 이들 선택기는 라디오 및 확인란 그룹의 가장 바깥쪽 컨테이너를 타겟팅하여 전체 그룹 구조에 일반 스타일을 적용할 수 있습니다. 이는 간격, 정렬 또는 기타 레이아웃 관련 속성을 설정하는 데 유용합니다.


  ```CSS
     /* Targets radio group wrappers */
       .radio-group-wrapper {
       margin-bottom: 20px; /* Adds space between radio groups */  
     }
  
     /* Targets checkbox group wrappers */
     .checkbox-group-wrapper {
     margin-bottom: 20px; /* Adds space between checkbox groups */
     }
  ```


* 타겟팅 그룹 레이블: 이 선택기는 라디오 및 확인란 그룹 래퍼 내의 `.field-label` 요소를 타겟팅합니다. 이를 통해 해당 그룹에 맞게 레이블 스타일을 지정할 수 있으며 잠재적으로 더 돋보이게 만들 수 있습니다.

  ```CSS
   .radio-group-wrapper legend,
   .checkbox-group-wrapper legend {
     font-weight: bold; /* Makes the group label bold */
   }
  ```



* 개별 입력 및 레이블 타겟팅: 이들 선택기는 개별 라디오 버튼, 확인란 및 관련 레이블에 대한 보다 세부적인 제어를 제공합니다. 이를 사용하여 크기나 간격을 조정하거나 보다 뚜렷한 시각적 스타일을 적용할 수 있습니다.

  ```CSS
  /* Styling radio buttons */
   .radio-group-wrapper input[type="radio"] {
     margin-right: 5px; /* Adds space between the input and its label */
   }
  
   /* Styling radio button labels */
   .radio-group-wrapper label {
     font-size: 15px; /* Changes the label font size */
   }
  
  /* Styling checkboxes */
   .checkbox-group-wrapper input[type="checkbox"] {
     margin-right: 5px; /* Adds space between the input and its label */
   }
  
   /* Styling checkbox labels */
   .checkbox-group-wrapper label {
     font-size: 15px; /* Changes the label font size */
   }
  ```




* 라디오 단추 및 확인란 모양 사용자 지정: 이 기법은 기본 입력을 숨기고 를 사용합니다 `:before` 및 `:after` 의사 요소 를 사용하여 &#39;검사됨&#39; 상태에 따라 모양을 변경하는 사용자 지정 시각적 개체를 만듭니다.

  ```CSS
  /* Hide the default radio button or checkbox */
     .radio-group-wrapper input[type="radio"],
     .checkbox-group-wrapper input[type="checkbox"] {
       opacity: 0;
       position: absolute;
     }
  
     /* Create a custom radio button */
     .radio-group-wrapper input[type="radio"] + label::before {
       /* ... styles for custom radio button ... */
     }
  
     .radio-group-wrapper input[type="radio"]:checked + label::before {
       /* ... styles for checked radio button ... */
     }
  
     /* Create a custom checkbox */
     /* Similar styling as above, with adjustments for a square shape  */
     .checkbox-group-wrapper input[type="checkbox"] + label::before {
       /* ... styles for custom checkbox ... */
     }
  
     .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
       /* ... styles for checked checkbox ... */
     }
  ```

+++

### 패널/컨테이너 구성 요소

+++ 패널/컨테이너 구성 요소의 HTML 구조

```HTML
<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
  </div>
</fieldset>
```

**HTML 구조의 예**

```HTML
<fieldset class="panel-wrapper field-login field-wrapper">
  <legend for="login" class="field-label" data-visible="false">Login Information</legend>
  <div class="text-wrapper field-username field-wrapper">
    <label for="username" class="field-label">Username</label>
    <input type="text" placeholder="Enter your username" maxlength="50" id="username" name="username">
    <div class="field-description" aria-live="polite" id="username-description">
      Please enter your username or email address.
    </div>
  </div>
  <div class="password-wrapper field-password field-wrapper">
    <label for="password" class="field-label">Password</label>
    <input type="password" placeholder="Enter your password" maxlength="20" id="password" name="password">
    <div class="field-description" aria-live="polite" id="password-description">
      Your password must be at least 8 characters long.
    </div>
  </div>
</fieldset>
```

* Fieldset 요소는 패널 이름(field-login)을 기반으로 스타일을 지정하기 위한 panel-wrapper 클래스와 추가 클래스가 있는 패널 컨테이너 역할을 합니다.
* 범례 요소 (<legend>)는 “로그인 정보”라는 텍스트와 field-label 클래스가 포함된 패널 제목 역할을 합니다. data-visible=&quot;false&quot; 속성을 JavaScript와 함께 사용하여 제목의 가시성을 제어할 수 있습니다.
* Fieldset 내부에서 여러 개의 .{Type}-wrapper 요소(이 경우 .text-wrapper 및 .password-wrapper)가 패널 내의 개별 양식 필드를 나타냅니다.
* 각 래퍼에는 이전 예시와 유사한 레이블, 입력 필드 및 설명이 포함되어 있습니다.

+++

+++ 패널/컨테이너 구성 요소용 CSS 선택기 예

1. 패널 타겟팅:

```CSS
  /* Target the entire panel container */
  .panel-wrapper {
    /* Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

* `.panel-wrapper` 선택기는 panel-wrapper 클래스를 사용하여 모든 요소의 스타일을 지정하여 모든 패널에 대해 일관된 모양을 만듭니다.

1. 패널 제목 타겟팅:

```CSS
  /* Target the legend element (panel title) */
  .panel-wrapper legend {
    /* Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /* Optional: create a separation line */
  }
```

* `.panel-wrapper legend` 선택기는 패널 내의 범례 요소 스타일을 지정하여 제목을 시각적으로 돋보이게 만듭니다.


1. 패널 내 개별 필드 타겟팅:

```CSS
/* Target all form field wrappers within a panel */
.panel-wrapper .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

* `.panel-wrapper .{Type}-wrapper` 선택기는 패널 내의 `.{Type}-wrapper` 클래스가 있는 모든 래퍼를 대상으로 하여 양식 필드 사이의 간격 스타일을 지정할 수 있습니다.

1. 특정 필드 타겟팅(선택 사항):

```CSS
  /* Target the username field wrapper */
  .panel-wrapper .text-wrapper.field-username {
    /* Add your styles here (specific to username field) */
  }

  /* Target the password field wrapper */
  .panel-wrapper .password-wrapper.field-password {
    /* Add your styles here (specific to password field) */
  }
```

* 선택 사항에 해당하는 이러한 선택기의 경우 사용자 이름 필드 강조 표시와 같은 고유한 스타일 지정을 위해 패널 내의 특정 필드 래퍼를 대상으로 지정할 수 있습니다.

+++

### 반복 가능 패널

+++ 반복 가능한 패널의 HTML 구조

```HTML
<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
</fieldset>
```

**HTML 구조의 예**

```HTML
<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-1" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-1" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-1" name="contacts[0].name">
    <div class="field-description" aria-live="polite" id="name-1-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-1" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-1" name="contacts[0].email">
    <div class="field-description" aria-live="polite" id="email-1-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>

<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-2" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-2" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-2" name="contacts[1].name">
    <div class="field-description" aria-live="polite" id="name-2-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-2" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-2" name="contacts[1].email">
    <div class="field-description" aria-live="polite" id="email-2-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>
```

각 패널은 추가 속성을 포함하여 단일 패널 예와 구조가 동일합니다.

* data-repeatable=&quot;true&quot;: 이 속성은 패널이 JavaScript 또는 프레임워크를 사용하여 동적으로 반복될 수 있음을 나타냅니다.

* 고유 ID 및 이름: 패널 내의 각 요소에는 패널의 색인을 기반으로 하는 고유 ID(예: name-1, email-1)와 이름 속성(예: name=&quot;contacts)이 있습니다[0].name&quot;) 형식으로 프로필 스크립트에서 참조할 수 있었습니다. 이를 통해 여러 패널이 제출될 때 적절한 데이터 수집이 가능합니다.

+++

+++ 반복 가능한 패널용 CSS 선택기

* 모든 반복 가능 패널 타겟팅:

```CSS
  /* Target all panels with the repeatable attribute */
  .panel-wrapper[data-repeatable="true"] {
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

이 선택기는 모든 반복 가능 패널의 스타일을 지정하여 디자인을 일관되게 유지합니다.


* 패널 내 개별 필드 타겟팅:

```CSS
/* Target all form field wrappers within a repeatable panel */
.panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```
이 선택기는 반복 가능 패널 내의 모든 필드 래퍼 스타일을 지정하여 필드 사이의 간격을 일관되게 유지합니다.

* 특정 필드 타겟팅(패널 내):

```CSS
/* Target the name field wrapper within the first panel */
.panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /* Add your styles here (specific to first name field) */
}

/* Target all
```

+++

### 파일 첨부

+++ 파일 첨부를 위한 HTML 구조

```HTML
<div class="file-wrapper field-{FileName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false"> File Attachment </legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
    <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="{id}" name="{FileName}" autocomplete="off" multiple="" required="required">
  </div>
  <div class="files-list">
    <div data-index="0" class="file-description">
      <span class="file-description-name">ClaimForm.pdf</span>
      <span class="file-description-size">26 kb</span>
      <button class="file-description-remove" type="button"></button>
    </div>
  </div>
</div>
```

**HTML 구조의 예**


```HTML
<div class="file-wrapper field-claim_form field-wrapper">
  <legend for="claim_form" class="field-label" data-visible="false">File Attachment</legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
  </div>
  <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="claim_form"
         name="claim_form" autocomplete="off" multiple="" required="required" data-max-file-size="2MB">
  <div class="files-list">
    </div>
</div>
```

* 클래스 속성은 첨부 파일에 제공된 이름(claim_form)을 사용합니다.
* 입력 요소의 id 및 name 속성은 첨부 파일 이름(claim_form)과 일치합니다.
* files-list 섹션은 처음에는 비어 있습니다. 파일이 업로드되면 JavaScript로 동적으로 채워집니다.

+++

+++ 파일 첨부 구성 요소용 CSS 선택기

* 전체 파일 첨부 구성 요소 타겟팅:

```CSS
/* Target the entire file attachment component */
.file-wrapper {
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

이 선택기는 범례, 끌기 영역, 입력 필드 및 목록을 포함한 전체 파일 첨부 구성 요소의 스타일을 지정합니다.

* 특정 요소 타겟팅:

```CSS
/* Target the drag and drop area */
.file-wrapper .file-drag-area {
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/* Target the file input element */
.file-wrapper input[type="file"] {
  /* Add your styles here (e.g., hide the default input) */
  display: none;
}

/* Target individual file descriptions within the list (populated dynamically) */
.file-wrapper .files-list .file-description {
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/* Target the file name within the description */
.file-wrapper .files-list .file-description .file-description-name {
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
}

/* Target the file size within the description */
.file-wrapper .files-list .file-description .file-description-size {
  /* Add your styles here (e.g., font-size) */
  font-size: 0.8em;
}

/* Target the remove button within the description */
.file-wrapper .files-list .file-description .file-description-remove {
  /* Add your styles here (e.g., background color, hover effect) */
  background-color: transparent;
  border: none;
  cursor: pointer;
}
```

이러한 선택기를 사용하면 파일 첨부 구성 요소의 다양한 부분에 개별적으로 스타일을 지정할 수 있습니다. 디자인 환경 설정에 맞게 스타일을 조정할 수 있습니다.

+++


## 구성 요소 스타일 지정

특정 유형에 따라 양식 필드의 스타일을 지정할 수 있습니다(`{Type}-wrapper`) 또는 개별 이름(`field-{Name}`). 이를 통해 양식 모양을 보다 세밀하게 제어하고 맞춤화할 수 있습니다.

### 필드 유형에 따른 스타일 지정

CSS 선택기를 사용하여 특정 필드 유형을 대상으로 하고 스타일을 일관되게 적용할 수 있습니다.

+++ HTML 구조

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**HTML 구조의 예**

```HTML
<div class="text-wrapper field-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="number-wrapper field-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="email-wrapper field-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>
```

* 각 필드는 여러 클래스가 있는 `div` 요소로 래핑됩니다.
   * `{Type}-wrapper`: 필드 유형을 식별합니다. (예: `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`)
   * `field-{Name}`: 이름으로 필드를 식별합니다. (예: `form-name`, `form-age`, `form-email`)
   * `field-wrapper`: 모든 필드 래퍼에 대한 일반 클래스입니다.
* `data-required` 속성은 필드가 필수인지 선택 사항인지를 나타냅니다.
* 각 필드에는 해당 레이블, 입력 요소 및 플레이스홀더 및 설명과 같은 잠재적인 추가 요소가 포함되어 있습니다.


+++


+++ 예제 CSS 선택기

```CSS
/* Target all text input fields */
.text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
.number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}
```

+++

### 필드 이름에 따른 스타일 지정

이름별로 개별 필드를 타겟팅하여 고유한 스타일을 적용할 수도 있습니다.

+++ HTML 구조

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>
```

**HTML 구조의 예**

```HTML
<div class="number-wrapper field-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp" aria-describedby="otp-description">
  <div class="field-description" aria-live="polite" id="otp-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>
```

+++

+++ CSS 선택기 예

```CSS
.field-otp input {
   letter-spacing: 2px
}
```



이 CSS는 `field-otp` 클래스가 있는 요소 내에 위치한 모든 입력 요소를 타겟팅합니다. 양식의 HTML 구조는 적응형 양식 블록의 규칙을 따릅니다. 이는 “field-otp” 클래스로 표시된 컨테이너에 “otp”라는 이름의 필드가 있음을 의미합니다.

+++

## 추가 참조

{{see-more-forms-eds}}