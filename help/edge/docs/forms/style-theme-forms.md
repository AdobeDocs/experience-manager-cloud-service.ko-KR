---
title: AEM Forms Edge Delivery Service 양식의 테마 및 스타일 사용자 정의
description: AEM Forms Edge Delivery Service 양식의 테마 및 스타일 사용자 정의
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e8fbe3efae7368c940cc2ed99cc9a352bbafbc22
workflow-type: tm+mt
source-wordcount: '1275'
ht-degree: 1%

---


# 양식 필드 스타일링

Forms은 웹 사이트에서 사용자가 데이터를 입력할 수 있도록 하는 데 중요합니다. 이 안내서에서는 내에서 다양한 양식 필드를 스타일링하는 기본 사항을 다룹니다. [적응형 양식 블록](/help/edge/docs/forms/create-forms.md)를 사용하면 시각적으로 호소력 있고 사용자에게 친숙한 양식을 만들 수 있습니다.

## 양식 필드 유형 이해

스타일링에 들어가기 전에 적응형 양식 블록에서 지원하는 일반적인 양식 필드 유형을 검토해 보겠습니다.

* 입력 필드: 여기에는 텍스트 입력, 이메일 입력, 암호 입력 등이 포함됩니다.
* 확인란 그룹: 여러 옵션을 선택하는 데 사용됩니다.
* 라디오 그룹: 그룹에서 하나의 옵션만 선택하는 데 사용됩니다.
* 드롭다운: 목록에서 하나의 옵션을 선택하는 데 사용되는 선택 박스라고도 합니다.
* 패널/컨테이너: 관련 양식 요소를 함께 그룹화하는 데 사용됩니다.

## 기본 스타일 원칙

특정 양식 필드를 스타일링하기 전에 기본 CSS 개념을 이해하는 것이 중요합니다.

* 선택기: CSS 선택기를 사용하면 스타일을 지정할 특정 HTML 요소를 타깃팅할 수 있습니다. 요소 선택기, 클래스 선택기 또는 ID 선택기를 사용할 수 있습니다.
* 속성: CSS 속성은 요소의 시각적 모양을 정의합니다. 양식 필드 스타일을 위한 일반적인 속성에는 색상, background-color, border, padding, margin 등이 있습니다.
* 상자 모델: CSS 상자 모델은 패딩, 테두리 및 여백으로 둘러싸인 컨텐츠 영역으로 HTML 요소의 구조를 설명합니다.
* Flexbox/Grid: CSS Flexbox 및 Grid 레이아웃은 반응형 및 유연한 디자인을 만들기 위한 강력한 도구입니다.

## 적응형 양식 블록을 위한 양식 스타일링

적응형 양식 블록은 양식 구성 요소를 선택하고 스타일링하는 프로세스를 단순화하는 표준화된 HTML 구조를 제공합니다.

* **기본 스타일 업데이트**: 를 편집하여 양식의 기본 스타일을 수정할 수 있습니다. `/blocks/form/form.css file`. 이 파일은 여러 단계의 마법사 양식을 지원하는 양식에 대한 포괄적인 스타일을 제공합니다. 또한 사용자 정의 CSS 변수를 사용하여 간편하게 맞춤화하고, 유지 관리하고, 양식 간에 통일된 스타일을 만들 수 있다는 점을 강조합니다. 적응형 양식 블록을 프로젝트에 추가하는 방법에 대한 지침은 [양식 만들기](/help/edge/docs/forms/create-forms.md).

* **사용자 지정**: 기본값 사용 `forms.css` 를 기반으로 양식 구성 요소의 모양과 느낌을 수정하여 시각적으로 매력적이고 사용자 친화적으로 만들 수 있습니다. 파일 구조는 구성을 장려하고 양식의 스타일을 유지 관리하여 웹 사이트 전반에 걸쳐 일관된 디자인을 홍보합니다.

## forms.css 구조 분류

* **전역 변수:** 다음에서 정의됨 `:root` level, 이러한 변수(`--variable-name`) 일관성 및 간편한 업데이트를 위해 스타일시트 전체에 사용되는 값을 저장합니다. 이러한 변수는 색상, 글꼴 크기, 패딩 및 기타 속성을 정의합니다. 고유한 Global 변수를 선언하거나 기존 변수를 수정하여 양식의 스타일을 변경할 수 있습니다.

* **유니버설 선택기 스타일:** 다음 `*` 선택기가 양식의 모든 요소와 일치하여 기본적으로 스타일을 모든 구성 요소에 적용할 수 있습니다. `box-sizing` 다음으로 속성: `border-box`.

* **양식 스타일 지정:** 이 섹션에서는 특정 HTML 요소를 타깃팅하기 위해 선택기를 사용하여 양식 구성 요소를 스타일링하는 방법을 중점적으로 다룹니다. 입력 필드, 텍스트 영역, 확인란, 라디오 버튼, 파일 입력, 양식 레이블 및 설명의 스타일을 정의합니다.

* **마법사 스타일(해당하는 경우):** 이 섹션은 각 단계가 한 번에 하나씩 표시되는 여러 단계 양식인 마법사 레이아웃을 스타일링하는 데 사용됩니다. 마법사 컨테이너, 필드 세트, 범례, 탐색 단추 및 응답형 레이아웃의 스타일을 정의합니다.

* **미디어 쿼리:** 레이아웃과 스타일을 적절하게 조정하여 다양한 화면 크기에 맞는 스타일을 제공합니다.

* **기타 스타일:**: 이 섹션에서는 성공 또는 오류 메시지, 파일 업로드 영역 및 양식에 표시될 수 있는 기타 요소에 대한 스타일을 다룹니다.


## 구성 요소 구조

적응형 양식 블록은 다양한 양식 요소에 대해 일관된 HTML 구조를 제공하여 더 쉬운 스타일링 및 관리를 보장합니다. 스타일링 목적으로 CSS를 사용하여 구성 요소를 조작할 수 있습니다.

### 일반 구성 요소(드롭다운, 라디오 그룹 및 확인란 그룹 제외):

드롭다운, 라디오 그룹 및 확인란 그룹을 제외한 모든 양식 필드는 다음과 같은 HTML 구조를 갖습니다.

#### HTML 구조

```HTML
<div class="form-{Type}-wrapper form-{Name} field-wrapper" data-required={Required}>
  <label for="{FieldId}" class="field-label">Field Label</label>
  <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Description of the field.
  </div>
</div>
```

* 클래스: div 요소에는 특정 요소 및 스타일을 타기팅하기 위한 여러 클래스가 있습니다. 다음이 필요합니다. `form-{Type}-wrapper` 또는 `form-{Name}` 클래스를 사용하여 양식 필드 스타일을 지정하는 CSS 선택기 개발:
   * {Type}: 필드 유형별로 구성 요소를 식별합니다. 예: 텍스트(form-text-wrapper), 숫자(form-number-wrapper), 날짜(form-date-wrapper)
   * {Name}: 구성 요소를 이름으로 식별합니다. 필드 이름에는 영숫자만 사용할 수 있으며, 이름에 있는 여러 연속 대시는 단일 대시로 대체됩니다 `(-)`, 필드 이름의 시작 및 종료 대시는 제거됩니다. 예: 이름 (form-first-name field-wrapper)
   * {FieldId}: 자동으로 생성된 필드에 대한 고유 식별자입니다.
   * {Required}: 필드가 필요한지 여부를 나타내는 부울입니다.
* 레이블: `label` 요소는 필드에 대한 설명 텍스트를 제공하고 다음을 사용하여 입력 요소와 연결합니다. `for` 특성.
* 입력: `input` 요소는 입력할 데이터 유형을 정의합니다. 예를 들어 텍스트, 숫자, 이메일이 있습니다.
* 설명(선택 사항): `div` 클래스 `field-description` 는 사용자에 대한 추가 정보 또는 지침을 제공합니다.

**HTML 구조의 예**

```HTML
<div class="form-text-wrapper form-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

**일반 구성 요소용 CSS 선택기**

```CSS
.form-{Type}-wrapper input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}


.form-{Name} input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```

* `.form-{Type}-wrapper`: 외부를 타깃팅합니다 `div` 필드 형식을 기반으로 하는 요소입니다. 예를 들어, `.form-text-wrapper` 는 모든 텍스트 입력 필드를 타깃팅합니다.
* `.form-{Name}`: 특정 필드 이름을 기반으로 요소를 추가로 선택합니다. 예를 들어, `.form-first-name` 는 &quot;이름&quot; 텍스트 필드를 타깃팅합니다.

**일반 구성 요소에 대한 CSS 선택기 예**

```CSS
/*Target all text input fields */

.form-text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/*Target all fields with name first-name*/

.form-first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```


### 드롭다운 구성 요소

드롭다운 메뉴의 경우 `select` 요소 대신 `input` 요소:


#### HTML 구조

```HTML
<div class="form-drop-down-wrapper form-{Name} field-wrapper" data-required={required}>
  <label for="{FieldId}" class="field-label">First Name</label>
  <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
  </div>
</div>
```

**예제 HTML 구조**

```HTML
    <div class="form-drop-down-wrapper form-country field-wrapper" data-required="true">
      <label for="country" class="field-label">Country</label>
      <select id="country" name="country">
         <option value="">Select Country</option>
         <option value="US">United States</option>
         <option value="CA">Canada</option>
    </select>
   <div class="field-description" aria-live="polite" id="country-description">Please select your country of residence.</div>
   </div>
```

#### 드롭다운 구성 요소에 대한 CSS 선택기 예

```CSS
/* Target the outer wrapper */
.form-drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
.form-drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style the dropdown itself */
.form-drop-down-wrapper select {
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
.form-drop-down-wrapper select::-ms-expand {
  display: none; /* Hide the default arrow for IE11 */
}

.form-drop-down-wrapper select::after {
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

* 래퍼를 대상으로 지정: 첫 번째 선택기 (`.form-drop-down-wrapper`) 외부 래퍼 요소를 타겟팅하여 스타일이 전체 드롭다운 구성 요소에 적용되도록 합니다.
* Flexbox 레이아웃: Flexbox가 깔끔한 레이아웃을 위해 레이블, 드롭다운 및 설명을 세로로 정렬합니다.
* 레이블 스타일: 레이블은 더 굵게 글꼴 두께 및 약간의 여백이 눈에 띕니다.
* 드롭다운 스타일: 선택 요소는 광택이 나는 룩에 대해 테두리, 패딩 및 둥근 모서리를 받습니다.
* 배경색: 시각적 조화를 위해 일관된 배경색이 설정됩니다.
* 화살표 사용자 지정: 선택 스타일은 기본 드롭다운 화살표를 숨기고 유니코드 문자와 위치를 사용하여 사용자 지정 화살표를 만듭니다.

### 라디오 및 확인란 그룹

드롭다운 구성 요소와 마찬가지로 라디오 및 확인란 그룹에는 고유한 HTML 구조 및 CSS 고려 사항이 있습니다.

#### 라디오 그룹 HTML 구조

```HTML
<div class="form-checkbox-group-wrapper form-{Name} field-wrapper" data-required={required}>
  <label class="field-label">{Label Text}</label>
  <div class="checkbox-group">
    <input type="checkbox" id="{FieldId}-1" name="{Name}" value="{Value1}">
    <label for="{FieldId}-1">{Option 1 Text}</label>
    <input type="checkbox" id="{FieldId}-2" name="{Name}" value="{Value2}">
    <label for="{FieldId}-2">{Option 2 Text}</label>
    </div>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Select multiple options (if applicable).
  </div>
</div>
```


#### 확인란 그룹 HTML 구조

```HTML
<div class="form-checkbox-group-wrapper form-{Name} field-wrapper" data-required={required}>
  <label class="field-label">{Label Text}</label>
  <div class="checkbox-group">
    <input type="checkbox" id="{FieldId}-1" name="{Name}" value="{Value1}">
    <label for="{FieldId}-1">{Option 1 Text}</label>
    <input type="checkbox" id="{FieldId}-2" name="{Name}" value="{Value2}">
    <label for="{FieldId}-2">{Option 2 Text}</label>
    </div>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Select multiple options (if applicable).
  </div>
</div>
```

**라디오 및 확인란 그룹에 대한 CSS 선택기 예**

* 외부 래퍼 타깃팅: 이 선택기는 라디오 및 확인란 그룹의 가장 바깥쪽 컨테이너를 타깃팅하여 전체 그룹 구조에 일반 스타일을 적용할 수 있습니다. 이 기능은 간격, 정렬 또는 기타 레이아웃 관련 속성을 설정하는 데 유용합니다.


  ```CSS
     /* Targets all radio group wrappers */
  .form-radio-group-wrapper {
    margin-bottom: 20px; /* Adds space between radio groups */
  }
  
  /* Targets all checkbox group wrappers */
  .form-checkbox-group-wrapper {
    margin-bottom: 20px; /* Adds space between checkbox groups */
  }
  ```


* 타겟팅 그룹 레이블: 이 선택기는 `.field-label` 라디오 및 확인란 그룹 래퍼 모두에 포함된 요소입니다. 이렇게 하면 이러한 그룹에 대해 특별히 레이블을 스타일링할 수 있으므로 더 눈에 띌 수 있습니다.

  ```CSS
  .form-radio-group-wrapper .field-label,
  .form-checkbox-group-wrapper .field-label {
   font-weight: bold; /* Makes the group label bold */
  }
  ```



* 개별 입력 및 레이블 타깃팅: 이러한 선택기는 개별 라디오 버튼, 확인란 및 관련 레이블을 더욱 세밀하게 제어할 수 있습니다. 이를 사용하여 크기 조정, 간격 조정 또는 보다 뚜렷한 시각적 스타일을 적용할 수 있습니다.

  ```CSS
  /* Styling radio buttons */
  .form-radio-group-wrapper input[type="radio"] {
    margin-right: 5px; /* Adds space between the input and its   label */
  } 
  
  /* Styling radio button labels */
  .form-radio-group-wrapper label {
    font-size: 15px; /* Changes the label font size */
  }
  
  /* Styling checkboxes */
  .form-checkbox-group-wrapper input[type="checkbox"] {
    margin-right: 5px;  /* Adds space between the input and its  label */ 
  }
  
  /* Styling checkbox labels */
  .form-checkbox-group-wrapper label {
    font-size: 15px; /* Changes the label font size */
  }
  ```




* 라디오 단추 및 확인란 모양 사용자 지정: 이 기법은 기본 입력을 숨기고 :before 및 :after 의사 요소를 사용하여 &#39;선택됨&#39; 상태에 따라 모양을 변경하는 사용자 지정 시각적 개체를 만듭니다.

  ```CSS
  /* Hide the default radio button or checkbox */
  .form-radio-group-wrapper input[type="radio"],
  .form-checkbox-group-wrapper input[type="checkbox"] {
    opacity: 0; 
    position: absolute; 
  }
  
  /* Create a custom radio button */
  .form-radio-group-wrapper input[type="radio"] + label::before { 
    content: "";
    display: inline-block;
    width: 16px; 
    height: 16px; 
    border: 2px solid #ccc; 
    border-radius: 50%;
    margin-right: 5px;
  }
  
  .form-radio-group-wrapper input[type="radio"]:checked +  label::before {
    background-color: #007bff; 
  }
  
  /* Create a custom checkbox */
  /* Similar styling as above, with adjustments for a square shape  */
  ```


## 구성 요소 스타일링

특정 유형 또는 개별 이름을 기준으로 양식 필드의 스타일을 지정할 수도 있습니다. 이렇게 하면 양식 모양을 보다 세밀하게 제어하고 사용자 지정할 수 있습니다.

### 필드 유형에 따른 스타일 지정

CSS 선택기를 사용하여 특정 필드 유형을 대상으로 하고 스타일을 일관되게 적용할 수 있습니다.

**예제 HTML 구조**

```HTML
<div class="form-text-wrapper form-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="form-number-wrapper form-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="form-email-wrapper form-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>
```

* 각 필드는 `div` 여러 클래스가 있는 요소:
   * `form-{Type}-wrapper`: 필드의 유형을 식별합니다. 예를 들어, `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `form-{Name}`: 필드별로 필드를 식별합니다. 예 `form-name`, `form-age`, `form-email`.
   * `field-wrapper`: 모든 필드 래퍼에 대한 일반 클래스입니다.
* 다음 `data-required` 속성은 필드가 필수인지 아니면 선택 사항인지를 나타냅니다.
* 각 필드에는 해당 레이블, 입력 요소 및 자리 표시자 및 설명과 같은 잠재적인 추가 요소가 있습니다.

**예제 CSS 선택기**

```CSS
/* Target all text input fields */
.form-text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
.form-number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}
```

### 필드 이름을 기반으로 스타일링

이름별로 개별 필드를 타겟팅하여 고유한 스타일을 적용할 수도 있습니다.

**예제 HTML 구조**

```HTML
<div class="form-number-wrapper form-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp">
</div>
```

**CSS 선택기 예**

```CSS
.form-otp input {
   letter-spacing: 2px
}
```

이 CSS는 클래스를 갖는 요소 내에 있는 모든 입력 요소를 타겟팅합니다 `form-otp`. 양식의 HTML 구조는 적응형 양식 블록의 규칙을 따르며, &quot;form-otp&quot; 클래스로 표시된 컨테이너가 &quot;otp&quot; 이름의 필드를 보유하고 있음을 의미합니다.


