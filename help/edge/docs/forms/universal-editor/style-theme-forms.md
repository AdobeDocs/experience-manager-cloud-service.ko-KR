---
title: AEM Forms용 Edge Delivery Services 양식의 테마 및 스타일 사용자 정의
description: Edge Delivery Services를 통해 제공되는 AEM Forms의 테마와 스타일을 효과적으로 사용자 정의하여 일관되고 브랜드화된 사용자 경험을 보장합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
source-git-commit: bf35f847f6f00d21915dfedb10cf38ea74344988
workflow-type: tm+mt
source-wordcount: '2493'
ht-degree: 55%

---

# 양식 모양 사용자 정의

Edge Delivery Services for AEM Forms의 양식 스타일을 사용하려면 CSS 사용자 지정 속성, 블록 기반 아키텍처 및 구성 요소별 타깃팅 전략을 정교하게 이해해야 합니다. 적응형 Forms 블록은 기존의 양식 스타일링 접근 방식과 달리 Edge Delivery Services의 성능과 접근성 이점을 유지하면서 일관된 태닝을 가능하게 하는 체계적인 디자인 토큰 시스템을 구현합니다.

적응형 Forms 블록 아키텍처는 모든 양식 구성 요소에 대해 표준화된 HTML 구조를 생성하여 CSS 타깃팅 및 사용자 지정에 예측 가능한 패턴을 만듭니다. 이러한 일관성을 통해 개발자는 복잡한 양식 구현에서 확장되는 포괄적인 스타일 시스템을 구현하는 동시에 Edge Delivery Services을 매우 빠르게 만드는 블록 기반 성능 최적화를 유지할 수 있습니다.

이 포괄적인 안내서는 CSS 사용자 지정 속성 시스템, 구성 요소 HTML 구조 패턴, 고급 스타일 지정 기술 등 Edge Delivery Services 에코시스템 내의 양식 스타일링에 대한 기술적 기반을 다룹니다. 이 설명서는 정교한 브랜드 양식 경험을 만들기 위한 이론적 이해와 실용적인 구현 지침을 모두 제공합니다.

## 기본 제공 사항

**CSS 사용자 지정 속성 마스터**: 색 구성표, 타이포그래피 배율, 간격 시스템 및 레이아웃 매개 변수를 포함하여 양식 모양을 제어하는 완전한 변수 시스템을 이해합니다. 이러한 속성을 재정의하고 확장하여 포괄적인 브랜드 테마를 구현하는 방법에 대해 알아봅니다.

**구성 요소 아키텍처 이해**: 각 양식 구성 요소 유형에 사용되는 HTML 구조 패턴에 대한 깊이 있는 지식을 확보하여 기본 기능이나 접근성 기능을 손상시키지 않고 정확한 CSS 타깃팅 및 맞춤화를 가능하게 합니다.

**고급 스타일 지정 기술**: Edge Delivery Services의 빠른 로드 특성을 유지하는 상태 기반 스타일 지정, 반응형 디자인 통합 및 성능 최적화 사용자 지정 전략을 포함한 정교한 스타일 지정 패턴을 구현합니다.

**전문 구현 전략**: 디자인 시스템 통합, 유지 관리 가능한 CSS 아키텍처 및 복잡한 스타일 지정 시나리오에 대한 문제 해결 기법을 포함하여 스타일 지정을 형성하기 위한 업계 표준 접근 방식에 대해 알아봅니다.

## 양식 필드 유형 이해

스타일 지정을 시작하기 전에 양식 블록에서 지원하는 일반적인 적응형 양식 [필드 유형](/help/edge/docs/forms/universal-editor/create-custom-component.md#supported-fieldtypes)을 검토해 보겠습니다.

- 입력 필드: 여기에는 텍스트 입력, 이메일 입력, 암호 입력 등이 포함됩니다.
- 확인란 그룹: 여러 옵션을 선택하는 데 사용됩니다.
- 라디오 그룹: 그룹에서 하나의 옵션만 선택하는 데 사용됩니다.
- 드롭다운: 선택 상자라고도 하며 목록에서 하나의 옵션을 선택하는 데 사용됩니다.
- 패널/컨테이너: 관련 양식 요소를 그룹화하는 데 사용됩니다.

## 기본 스타일 지정 원칙

특정 양식 필드의 스타일을 지정하기 전에 [기본적인 CSS 개념](https://www.w3schools.com/css/css_intro.asp)을 이해하는 것이 중요합니다.

- [선택기](https://www.w3schools.com/css/css_selectors.asp): CSS 선택기를 사용하면 스타일 지정을 위해 특정 HTML 요소를 타기팅할 수 있습니다. 요소 선택기, 클래스 선택기 또는 ID 선택기를 사용할 수 있습니다.
- [속성](https://www.w3schools.com/css/css_syntax.asp): CSS 속성은 요소의 시각적 모양을 정의합니다. 스타일 양식 필드의 일반적인 속성에는 색상, 배경색, 테두리, 패딩, 여백 등이 포함됩니다.
- [상자 모델](https://www.w3schools.com/css/css_boxmodel.asp): CSS 상자 모델은 HTML 요소의 구조를 패딩, 테두리 및 여백으로 둘러싸인 콘텐츠 영역으로 기술합니다.
- Flexbox/격자: CSS [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp) 및 [격자 레이아웃](https://www.w3schools.com/css/css_grid.asp)은 반응성이 뛰어나고 유연한 디자인을 만들기 위한 강력한 도구입니다.




## CSS 사용자 지정 속성을 사용한 포괄적인 양식 스타일 지정

적응형 Forms 블록은 사용자 지정 속성(CSS 변수)을 기반으로 구축된 정교한 CSS 아키텍처를 활용하여 모든 양식 구성 요소에서 체계적인 맞춤화와 일관된 스타일을 가능하게 합니다. 효과적인 양식 사용자 정의 및 브랜딩을 위해서는 이 구조를 이해하는 것이 필수적입니다.

### forms.css 아키텍처 이해

기본 양식 스타일은 프로젝트 리포지토리(`/blocks/form/form.css`)에 있으며 유지 관리 가능성, 일관성 및 사용자 지정 유연성을 우선하는 구조화된 접근 방식을 따릅니다. 아키텍처는 다음과 같은 몇 가지 주요 구성 요소로 구성됩니다.

**CSS 사용자 지정 속성 기초**: 스타일 지정 시스템은 `:root` 수준에서 정의된 CSS 사용자 지정 속성을 기반으로 하며, 모든 양식 구성 요소에 걸쳐 캐스케이드되는 중앙 집중식 테마 지정 시스템을 제공합니다. 이러한 변수는 색상, 타이포그래피, 간격 및 레이아웃 속성에 대한 디자인 토큰을 설정합니다.

**블록 기반 CSS 구조**: Edge Delivery Services에서는 `.form` 클래스가 모든 양식 관련 스타일에 대한 기본 네임스페이스로 사용되는 블록 기반 아키텍처를 사용하여 적절한 범위 격리를 보장하고 CSS가 다른 페이지 구성 요소와 충돌하지 않도록 합니다.

**구성 요소별 스타일 지정**: 개별 양식 구성 요소는 전체 디자인 시스템의 무결성을 유지하면서 다른 필드 형식에 대해 예측 가능한 타깃팅을 제공하는 일관된 래퍼 패턴(`.{Type}-wrapper`)을 사용하여 스타일을 지정합니다.

### CSS 사용자 지정 속성 참조 및 사용자 지정

양식 스타일 지정 시스템에는 양식 모양 및 동작의 모든 측면을 제어하는 50개 이상의 CSS 사용자 지정 속성이 포함되어 있습니다. 이러한 속성을 이해하면 디자인 일관성을 유지하면서 포괄적인 맞춤화를 구현할 수 있습니다.

+++ 색상 및 테마 변수

색상 시스템은 신중하게 구성된 사용자 지정 속성을 통해 양식의 완전한 시각적 기반을 구축합니다.

```css
:root {
    /* Primary color system */
    --background-color-primary: #fff;
    --label-color: #666;
    --border-color: #818a91;
    --form-error-color: #ff5f3f;
    
    /* Button color system */
    --button-primary-color: #5F8DDA;
    --button-secondary-color: #666;
    --button-primary-hover-color: #035fe6;
    
    /* Form-specific color applications */
    --form-background-color: var(--background-color-primary);
    --form-input-border-color: var(--border-color);
    --form-invalid-border-color: #ff5f3f;
    --form-label-color: var(--label-color);
}
```

**실제 사용자 지정 예제**: 폼에 어두운 테마를 구현하려면 기본 색상 변수를 재정의하십시오.

```css
:root {
    --background-color-primary: #1a1a1a;
    --label-color: #e0e0e0;
    --border-color: #404040;
    --form-error-color: #ff6b6b;
    --button-primary-color: #4a9eff;
}
```

시스템이 하드코딩된 값이 아닌 변수 참조를 사용하므로 이 단일 변경 사항은 모든 양식 구성 요소를 통해 전파됩니다.

+++

+++ 타이포그래피 및 간격 변수

타이포그래피 및 간격 변수는 텍스트 표시 및 레이아웃 간격을 포괄적으로 제어합니다.

```css
:root {
    /* Font size system */
    --form-font-size-m: 22px;
    --form-font-size-s: 18px;
    --form-font-size-xs: 16px;
    
    /* Component-specific typography */
    --form-label-font-size: var(--form-font-size-s);
    --form-label-font-weight: 400;
    --form-title-font-weight: 600;
    --form-input-font-size: 1rem;
    
    /* Spacing system */
    --form-field-horz-gap: 40px;
    --form-field-vert-gap: 20px;
    --form-input-padding: 0.75rem 0.6rem;
    --form-padding: 0 10px;
}
```

**실제 사용자 지정 예제**: 더 작은 타이포그래피를 사용하여 더 작은 양식 레이아웃을 만들려면:

```css
:root {
    --form-font-size-m: 18px;
    --form-font-size-s: 14px;
    --form-font-size-xs: 12px;
    --form-field-horz-gap: 20px;
    --form-field-vert-gap: 15px;
    --form-input-padding: 0.5rem 0.4rem;
}
```

+++

+++ 레이아웃 및 구조 변수

레이아웃 변수는 양식 차원, 그리드 동작 및 구성 요소 배열을 제어합니다.

```css
:root {
    /* Form layout */
    --form-width: 100%;
    --form-columns: 12;
    --form-submit-width: 100%;
    
    /* Card-based components */
    --form-card-border-radius: 4px;
    --form-card-padding: 0.6rem 0.8rem;
    --form-card-shadow: 0 1px 2px rgb(0 0 0 / 3%);
    --form-card-hover-shadow: 0 2px 4px rgb(0 0 0 / 6%);
    
    /* Wizard-specific layout */
    --form-wizard-padding: 0px;
    --form-wizard-padding-bottom: 160px;
    --form-wizard-step-legend-padding: 10px;
}
```

**실제 사용자 지정 예제**: 시각적 깊이가 향상된 카드 스타일 양식을 만들려면:

```css
:root {
    --form-card-border-radius: 12px;
    --form-card-padding: 1.5rem 2rem;
    --form-card-shadow: 0 4px 12px rgb(0 0 0 / 8%);
    --form-card-hover-shadow: 0 8px 24px rgb(0 0 0 / 12%);
    --form-background-color: #f8f9fa;
}

.form {
    background: var(--form-background-color);
    border-radius: var(--form-card-border-radius);
    box-shadow: var(--form-card-shadow);
    padding: var(--form-card-padding);
    max-width: 600px;
    margin: 2rem auto;
}
```

+++

### CSS 스타일 패턴 및 모범 사례

적응형 Forms 블록은 모든 구성 요소에서 유지 관리 가능하고 성능이 뛰어나며 일관된 스타일을 보장하는 특정 CSS 패턴을 따릅니다.

+++ 기본 스타일 패턴

**블록 수준 양식 컨테이너**: 전체 레이아웃 및 백그라운드 스타일을 위해 기본 양식 컨테이너를 타깃팅합니다.

```css
.form {
    /* Form-wide styles */
    max-width: 800px;
    margin: 0 auto;
    background-color: var(--form-background-color);
    padding: var(--form-padding);
    border-radius: var(--form-card-border-radius);
}
```

**구성 요소 래퍼 패턴**: 일관된 래퍼 클래스를 사용하여 특정 필드 형식을 타깃팅합니다.

```css
/* Text input fields */
.form .text-wrapper input {
    padding: var(--form-input-padding);
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    font-size: var(--form-input-font-size);
    border-radius: 4px;
    width: 100%;
}

/* Email input fields */
.form .email-wrapper input {
    padding: var(--form-input-padding);
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    font-size: var(--form-input-font-size);
}

/* Button styling */
.form .button-wrapper button {
    background-color: var(--form-button-background-color);
    color: var(--form-button-color);
    padding: var(--form-button-padding);
    border: var(--form-button-border);
    font-size: var(--form-button-font-size);
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.2s ease;
}

.form .button-wrapper button:hover {
    background-color: var(--form-button-background-hover-color);
}
```

+++

+++ 고급 사용자 정의 패턴

**필드별 타깃팅**: 고유한 스타일 요구 사항을 위해 이름별로 개별 필드를 타깃팅합니다.

```css
/* Style specific fields */
.form .field-email input {
    background-image: url('data:image/svg+xml;...'); /* Email icon */
    background-repeat: no-repeat;
    background-position: right 12px center;
    padding-right: 40px;
}

.form .field-phone input {
    text-align: center;
    letter-spacing: 1px;
    font-family: monospace;
}
```

**상태 기반 스타일**: 유효성 검사 및 상호 작용 상태 구현:

```css
/* Validation states */
.form .field-wrapper[data-valid="false"] input {
    border-color: var(--form-error-color);
    box-shadow: 0 0 0 2px rgba(255, 95, 63, 0.1);
}

.form .field-wrapper[data-valid="true"] input {
    border-color: #28a745;
    box-shadow: 0 0 0 2px rgba(40, 167, 69, 0.1);
}

/* Focus states */
.form .text-wrapper input:focus,
.form .email-wrapper input:focus {
    outline: none;
    border-color: var(--button-primary-color);
    box-shadow: 0 0 0 2px rgba(95, 141, 218, 0.2);
}
```

+++


## 구성 요소 구조

적응형 양식 블록은 다양한 양식 요소에 대해 일관된 HTML 구조를 제공하므로 스타일 지정과 관리를 더 용이하게 해 줍니다. 스타일 지정을 위해 CSS를 사용하여 구성 요소를 조작할 수 있습니다.

+++ 일반 구성 요소(드롭다운, 라디오 그룹 및 확인란 그룹 제외):

드롭다운, 라디오 그룹 및 확인란 그룹을 제외한 모든 양식 필드에는 다음과 같은 HTML 구조가 있습니다.

### 일반 구성 요소의 HTML 구조

```HTML
  <div class="{Type}-wrapper field-{Name}   field-wrapper" data-required={Required}>
     <label for="{FieldId}" class="field-label">First   Name</label>
     <input type="{Type}" placeholder="{Placeholder}"   maxlength="{Max}" id={FieldId}" name="{Name}"   aria-describedby="{FieldId}-description">
     <div class="field-description" aria-live="polite"  id="{FieldId}-description">
      Hint - First name should be minimum 3 characters  and a maximum of 10 characters.
     </div>
  </div>
```

- 클래스: div 요소에는 특정 요소 및 스타일을 타기팅하기 위한 여러 클래스가 있습니다. CSS 선택기가 양식 필드의 스타일을 지정하려면 `{Type}-wrapper` 또는 `field-{Name}`이 필요합니다.
- {Type}: 필드 유형으로 구성 요소를 식별합니다. 그 예로는 텍스트(text-wrapper), 숫자(number-wrapper), 날짜(date-wrapper)가 있습니다.
- {Name}: 이름으로 구성 요소를 식별합니다. 필드 이름에는 영숫자 문자만 사용할 수 있으며 이름에 있는 여러 개의 연속 대시는 하나의 대시`(-)`로 대체됩니다. 필드 이름의 시작 및 끝에 있는 대시는 제거됩니다. 그 예로는 이름(field-first-name field-wrapper)이 있습니다.
- {FieldId}: 자동으로 생성된 필드의 고유 식별자입니다.
- {Required}: 필드가 필수인지 여부를 나타내는 부울입니다.
- 레이블: `label` 요소는 필드에 대한 설명 텍스트를 제공하고 `for` 속성을 사용하여 이를 입력 요소와 연결합니다.
- 입력: `input` 요소는 입력할 데이터 유형을 정의합니다. 예를 들어 문자, 숫자, 이메일 등이 있습니다.
- 설명(선택 사항): `field-description` 클래스가 있는 `div`는 사용자에게 추가 정보 또는 지침을 제공합니다.

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

#### 일반 구성 요소용 CSS 선택기

```css
/* Primary Pattern: Target field wrapper by type */
.form .{Type}-wrapper {
    /* Container styling for specific field types */
    margin-bottom: 1rem;
    border-radius: 4px;
}

/* Primary Pattern: Target input fields within wrapper */
.form .{Type}-wrapper input {
    /* Input field styling using CSS custom properties */
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    width: 100%;
    font-size: var(--form-input-font-size);
}

/* Context-specific: Target element by field name when higher specificity needed */
.form .field-{Name} input {
    /* Field-specific customizations */
    /* Use this pattern for unique styling requirements */
}
```

- `.form .{Type}-wrapper`: 필드 유형에 따라 필드 래퍼 요소를 타깃팅합니다. 예를 들어 `.form .text-wrapper`은(는) 모든 텍스트 필드 컨테이너를 대상으로 합니다.
- `.form .{Type}-wrapper input`: 래퍼 내의 실제 입력 요소를 타깃팅합니다. 양식 입력 스타일링에 권장되는 패턴입니다.
- `.form .field-{Name}`: 특정 필드 이름을 기반으로 요소를 타깃팅합니다. 예를 들어 `.form .field-first-name`은(는) &quot;이름&quot; 필드 컨테이너를 대상으로 합니다. `.form .field-{Name} input`을(를) 사용하여 특별히 입력 요소를 대상으로 지정합니다.
- **피하십시오**: `main .form form .{Type}-wrapper` - 불필요한 CSS 특수성이 생성되므로 유지 관리가 더 어렵습니다.

**일반 구성 요소용 CSS 선택기의 예**

```css
/* Primary Pattern: Target all text input fields */
.form .text-wrapper input {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    width: 100%;
    font-size: var(--form-input-font-size);
    background-color: var(--form-input-background-color);
}

/* Context-specific: Target field by name when higher specificity needed */
.form .field-first-name input {
    text-transform: capitalize;
    border-color: var(--button-primary-color);
}

/* Alternative with main context if needed */
main .form .text-wrapper input {
    /* Use only when you need higher specificity */
    color: var(--form-label-color);
}
```

+++

+++ 드롭다운 구성 요소

드롭다운 메뉴의 경우 `input` 요소 대신 `select` 요소가 사용됩니다.

#### 드롭다운 구성 요소의 HTML 구조

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

#### 드롭다운 구성 요소용 CSS 선택기

다음 CSS에는 드롭다운 구성 요소에 대한 몇 가지 CSS 선택기 예가 나열되어 있습니다.

```css
/* Primary Pattern: Target the dropdown wrapper */
.form .drop-down-wrapper {
    /* Container layout using flexbox */
    display: flex;
    flex-direction: column;
    margin-bottom: var(--form-field-vert-gap);
}

/* Target the select element */
.form .drop-down-wrapper select {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    background-color: var(--form-input-background-color);
    font-size: var(--form-input-font-size);
    color: var(--form-label-color);
}

/* Style the label */
.form .drop-down-wrapper .field-label {
    margin-bottom: 5px;
    font-weight: var(--form-label-font-weight);
    color: var(--form-label-color);
    font-size: var(--form-label-font-size);
}
```

- 래퍼 타기팅: 첫 번째 선택기(`.drop-down-wrapper`)는 외부 래퍼 요소를 타기팅하여 스타일이 전체 드롭다운 구성 요소에 적용되도록 합니다.
- Flexbox 레이아웃: Flexbox는 깔끔한 레이아웃을 위해 레이블, 드롭다운 및 설명을 수직으로 정렬합니다.
- 레이블 스타일: 더 굵은 글꼴 두께와 약간의 여백으로 레이블을 돋보이게 합니다.
- 드롭다운 스타일링: 테두리, 패딩 및 둥근 모퉁이로 `select` 요소를 세련되게 합니다.
- 배경색: 시각적인 조화를 위해 일관된 배경색을 설정합니다.
- 화살표 맞춤화: 선택적 스타일로 기본 드롭다운 화살표를 숨기고 유니코드 문자와 위치 지정을 사용하여 사용자 정의 화살표를 만듭니다.

+++

+++ 라디오 그룹

드롭다운 구성 요소와 유사하게 라디오 그룹에는 고유한 HTML 구조 및 CSS 구조가 있습니다.

#### 라디오 그룹의 HTML 구조

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

**HTML 구조의 예**

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

#### 라디오 그룹용 CSS 선택기

- Fieldset 타기팅

```css
/* Target radio group container */
.form .radio-group-wrapper {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    margin-bottom: var(--form-field-vert-gap);
}
```

이 선택기는 radio-group-wrapper 클래스가 있는 모든 필드 세트를 대상으로 합니다. 전체 라디오 그룹에 일반 스타일을 적용하는 데 유용합니다.

- 라디오 버튼 레이블 타기팅

```css
/* Target radio button labels */
.form .radio-wrapper label {
    font-weight: var(--form-label-font-weight);
    margin-right: 10px;
    color: var(--form-label-color);
    font-size: var(--form-label-font-size);
    cursor: pointer;
}
```

- 이름을 기준으로 특정 Fieldset 내의 모든 라디오 버튼 레이블을 타기팅합니다.

```css
/* Target all radio button labels within a specific fieldset based on its name */
.form .field-color .radio-wrapper label {
    /* Field-specific radio label customizations */
    /* Add your custom styles here */
}
```

+++

+++ 확인란 그룹

#### 확인란 그룹의 HTML 구조

```HTML
<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="checkbox-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

**HTML 구조의 예**

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

#### 확인란 그룹용 CSS 선택기

- 외부 래퍼 타기팅: 이들 선택기는 라디오 및 확인란 그룹의 가장 바깥쪽 컨테이너를 타기팅하여 전체 그룹 구조에 일반 스타일을 적용할 수 있습니다. 이는 간격, 정렬 또는 기타 레이아웃 관련 속성을 설정하는 데 유용합니다.

```css
/* Primary Pattern: Targets radio group wrappers */
.form .radio-group-wrapper {
    margin-bottom: var(--form-field-vert-gap); /* Adds space between radio groups */
    display: flex;
    flex-direction: column;
    border: var(--form-fieldset-border);
    padding: var(--form-input-padding);
}

/* Primary Pattern: Targets checkbox group wrappers */
.form .checkbox-group-wrapper {
    margin-bottom: var(--form-field-vert-gap); /* Adds space between checkbox groups */
    display: flex;
    flex-direction: column;
    border: var(--form-fieldset-border);
    padding: var(--form-input-padding);
}
```

- 타기팅 그룹 레이블: 이 선택기는 라디오 및 확인란 그룹 래퍼 내의 `.field-label` 요소를 타기팅합니다. 이를 통해 해당 그룹에 맞게 레이블 스타일을 지정할 수 있으며 잠재적으로 더 돋보이게 만들 수 있습니다.

```css
/* Primary Pattern: Target group labels */
.form .radio-group-wrapper legend,
.form .checkbox-group-wrapper legend {
    font-weight: var(--form-title-font-weight); /* Makes the group label bold */
    margin-bottom: 0.5rem;
    font-size: var(--form-fieldset-legend-font-size);
    color: var(--form-fieldset-legend-color);
    padding: var(--form-fieldset-legend-padding);
    border: var(--form-fieldset-legend-border);
}
```

- 개별 입력 및 레이블 타기팅: 이들 선택기는 개별 라디오 버튼, 확인란 및 관련 레이블에 대한 보다 세부적인 제어를 제공합니다. 이를 사용하여 크기나 간격을 조정하거나 보다 뚜렷한 시각적 스타일을 적용할 수 있습니다.

```css
/* Primary Pattern: Styling radio buttons */
.form .radio-group-wrapper input[type="radio"] {
    margin-right: 8px; /* Adds space between the input and its label */
    margin-bottom: 4px;
    cursor: pointer;
}

/* Primary Pattern: Styling radio button labels */
.form .radio-group-wrapper label {
    font-size: var(--form-label-font-size); /* Changes the label font size */
    color: var(--form-label-color);
    font-weight: var(--form-label-font-weight);
    display: flex;
    align-items: center;
    cursor: pointer;
}

/* Primary Pattern: Styling checkboxes */
.form .checkbox-group-wrapper input[type="checkbox"] {
    margin-right: 8px; /* Adds space between the input and its label */
    margin-bottom: 4px;
    cursor: pointer;
}

/* Primary Pattern: Styling checkbox labels */
.form .checkbox-group-wrapper label {
    font-size: var(--form-label-font-size); /* Changes the label font size */
    color: var(--form-label-color);
    font-weight: var(--form-label-font-weight);
    display: flex;
    align-items: center;
    cursor: pointer;
}
```

- 라디오 버튼 및 확인란 모양 맞춤화: 이 기술을 통해 기본 입력을 숨기고 `:before` 및 `:after` 의사 요소를 사용하여 ‘선택됨’ 상태에 따라 모양을 변경하는 맞춤형 시각적 요소를 생성할 수 있습니다.

```css
/* Hide the default radio button or checkbox */
.form .radio-group-wrapper input[type="radio"],
.form .checkbox-group-wrapper input[type="checkbox"] {
    opacity: 0;
    position: absolute;
    width: 1px;
    height: 1px;
}

/* Create a custom radio button */
.form .radio-group-wrapper input[type="radio"] + label::before {
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid var(--form-input-border-color);
    border-radius: 50%;
    margin-right: 8px;
    background-color: var(--form-input-background-color);
    transition: all 0.2s ease;
}

.form .radio-group-wrapper input[type="radio"]:checked + label::before {
    background-color: var(--button-primary-color);
    border-color: var(--button-primary-color);
    box-shadow: inset 0 0 0 3px var(--form-input-background-color);
}

/* Create a custom checkbox */
.form .checkbox-group-wrapper input[type="checkbox"] + label::before {
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid var(--form-input-border-color);
    border-radius: 2px;
    margin-right: 8px;
    background-color: var(--form-input-background-color);
    transition: all 0.2s ease;
}

.form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
    background-color: var(--button-primary-color);
    border-color: var(--button-primary-color);
    background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16"><path fill="white" d="M13.854 3.646a.5.5 0 0 1 0 .708l-7 7a.5.5 0 0 1-.708 0l-3.5-3.5a.5.5 0 1 1 .708-.708L6.5 10.293l6.646-6.647a.5.5 0 0 1 .708 0z"/></svg>');
    background-repeat: no-repeat;
    background-position: center;
}
```

+++

+++ 패널/컨테이너 구성 요소

#### 패널/컨테이너 구성 요소의 HTML 구조

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

- Fieldset 요소는 패널 이름(field-login)을 기반으로 스타일을 지정하기 위한 panel-wrapper 클래스와 추가 클래스가 있는 패널 컨테이너 역할을 합니다.
- 범례 요소(`<legend>`)는 &quot;로그인 정보&quot; 텍스트와 클래스 필드 레이블을 사용하여 패널 제목 역할을 합니다. data-visible=&quot;false&quot; 속성을 JavaScript와 함께 사용하여 제목의 가시성을 제어할 수 있습니다.
- Fieldset 내부에서 여러 개의.{Type}-wrapper 요소(이 경우 .text-wrapper 및 .password-wrapper)가 패널 내의 개별 양식 필드를 나타냅니다.
- 각 래퍼에는 이전 예시와 유사한 레이블, 입력 필드 및 설명이 포함되어 있습니다.


#### 패널/컨테이너 구성 요소용 CSS 선택기 예

1. 패널 타기팅:

```CSS
  /- Target the entire panel container */
  main .form form .panel-wrapper {
    /- Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

- `.panel-wrapper` 선택기는 panel-wrapper 클래스를 사용하여 모든 요소의 스타일을 지정하여 모든 패널에 대해 일관된 모양을 만듭니다.

1. 패널 제목 타기팅:

```CSS
  /- Target the legend element (panel title) */
  .panel-wrapper legend {
    /- Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /- Optional: create a separation line */
  }
```

- `.panel-wrapper legend` 선택기는 패널 내의 범례 요소 스타일을 지정하여 제목을 시각적으로 돋보이게 만듭니다.


1. 패널 내 개별 필드 타기팅:

```CSS
/- Target all form field wrappers within a panel */
main .form form .panel-wrapper .{Type}-wrapper {
  /- Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

- `.panel-wrapper .{Type}-wrapper` 선택기는 패널 내의 `.{Type}-wrapper` 클래스가 있는 모든 래퍼를 대상으로 하여 양식 필드 사이의 간격 스타일을 지정할 수 있습니다.

1. 특정 필드 타기팅(선택 사항):

```CSS
  /- Target the username field wrapper */
  main .form form .panel-wrapper .text-wrapper.field-username {
    /- Add your styles here (specific to username field) */
  }

  /- Target the password field wrapper */
  main .form form .panel-wrapper .password-wrapper.field-password {
    /- Add your styles here (specific to password field) */
  }
```

- 선택 사항에 해당하는 이러한 선택기의 경우 사용자 이름 필드 강조 표시와 같은 고유한 스타일 지정을 위해 패널 내의 특정 필드 래퍼를 대상으로 지정할 수 있습니다.


+++

+++ 반복 가능 패널

#### 반복 가능 패널의 HTML 구조

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

- data-repeatable=&quot;true&quot;: 이 속성은 패널이 JavaScript 또는 프레임워크를 사용하여 동적으로 반복될 수 있음을 나타냅니다.

- 고유 ID 및 이름: 패널 내의 각 요소에는 고유 ID(예: name-1, email-1)와 패널 색인을 기반으로 하는 이름 속성(예: name=&quot;contacts[0].name&quot;)이 있습니다. 이를 통해 여러 패널이 제출될 때 적절한 데이터 수집이 가능합니다.


#### 반복 가능 패널용 CSS 선택기

- 모든 반복 가능 패널 타기팅:

```CSS
  /- Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] {
    /- Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

이 선택기는 모든 반복 가능 패널의 스타일을 지정하여 디자인을 일관되게 유지합니다.


- 패널 내 개별 필드 타기팅:

```CSS
/- Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /- Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

이 선택기는 반복 가능 패널 내의 모든 필드 래퍼 스타일을 지정하여 필드 사이의 간격을 일관되게 유지합니다.

- 특정 필드 타기팅(패널 내):

```CSS
/- Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /- Add your styles here (specific to first name field) */
}

/- Target all
```


+++


+++ 첨부 파일

#### 첨부 파일의 HTML 구조

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

- 클래스 속성은 첨부 파일에 제공된 이름(claim_form)을 사용합니다.
- 입력 요소의 id 및 name 속성은 첨부 파일 이름(claim_form)과 일치합니다.
- files-list 섹션은 처음에는 비어 있습니다. 파일이 업로드되면 JavaScript로 동적으로 채워집니다.


#### 첨부 파일 구성 요소용 CSS 선택기

- 전체 첨부 파일 구성 요소 타기팅:

```CSS
/- Target the entire file attachment component */
main .form form .file-wrapper {
  /- Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

이 선택기는 범례, 드래그 영역, 입력 필드 및 목록을 포함한 전체 첨부 파일 구성 요소의 스타일을 지정합니다.

- 특정 요소 타기팅:

```CSS
/- Target the drag and drop area */
main .form form .file-wrapper .file-drag-area {
  /- Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/- Target the file input element */
main .form form .file-wrapper input[type="file"] {
  /- Add your styles here (e.g., hide the default input) */
  display: none;
}

/- Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description {
  /- Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/- Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name {
  /- Add your styles here (e.g., font-weight) */
  font-weight: bold;
}
```

이러한 선택기를 사용하면 첨부 파일 구성 요소의 다양한 부분에 개별적으로 스타일을 지정할 수 있습니다. 디자인 환경 설정에 맞게 스타일을 조정할 수 있습니다.

+++



## 구성 요소 스타일 지정

특정 유형(`{Type}-wrapper`)이나 개별 이름(`field-{Name}`)을 기준으로 양식 필드의 스타일을 지정할 수도 있습니다. 이를 통해 양식 모양을 보다 세밀하게 제어하고 맞춤화할 수 있습니다.

+++ 필드 유형에 따른 스타일 지정

CSS 선택기를 사용하여 특정 필드 유형을 타기팅하고 스타일을 일관되게 적용할 수 있습니다.

### HTML 구조

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

- 각 필드는 여러 클래스가 있는 `div` 요소로 래핑됩니다.
   - `{Type}-wrapper`: 필드 유형을 식별합니다. (예: `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`)
   - `field-{Name}`: 이름으로 필드를 식별합니다. (예: `form-name`, `form-age`, `form-email`)
   - `field-wrapper`: 모든 필드 래퍼에 대한 일반 클래스입니다.
- `data-required` 속성은 필드가 필수인지 선택 사항인지를 나타냅니다.
- 각 필드에는 해당 레이블, 입력 요소 및 플레이스홀더 및 설명과 같은 잠재적인 추가 요소가 포함되어 있습니다.




### CSS 선택기의 예

```CSS
/- Primary Pattern: Target all text input fields */
.form .text-wrapper input {
  /- Add your styles here */
  width: 100%;
  padding: var(--form-input-padding);
}

/- Primary Pattern: Target all number input fields */
.form .number-wrapper input {
  /- Add your styles here */
  letter-spacing: 2px; /- Example for adding letter spacing to all number fields */
  text-align: center;
}
```

+++

+++ 필드 이름에 따른 스타일 지정

이름별로 개별 필드를 타기팅하여 고유한 스타일을 적용할 수도 있습니다.

#### HTML 구조

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


#### CSS 선택기의 예

```CSS
/- Primary Pattern: Target specific field by name */
.form .field-otp input {
   letter-spacing: 2px;
   text-align: center;
   font-family: monospace;
}

/- Context-specific: Use higher specificity when needed */
main .form .field-otp input {
   /- Use only when you need to override other styles */
   font-weight: bold;
}
```

이 CSS는 `field-otp` 클래스가 있는 요소 내에 위치한 모든 입력 요소를 타기팅합니다. Edge Delivery Services 양식 구조는 적응형 Forms 블록 규칙을 따르며, 이 규칙에서 컨테이너는 이름이 &quot;otp&quot;인 필드에 대한 &quot;field-otp&quot;와 같은 필드별 클래스로 표시됩니다.


## CSS 파일 구조 및 구현

### **참조 구현**

전체 양식 스타일 참조는 AEM Forms Boilerplate 저장소에서 사용할 수 있습니다.

```
https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/blocks/form/form.css
```

이 파일은 CSS 사용자 지정 속성 시스템의 표준 구현 역할을 하며 모든 양식 스타일을 위한 기반을 제공합니다. 여기에는 모든 CSS 변수, 구성 요소 스타일 패턴 및 반응형 디자인 구현에 대한 포괄적인 정의가 포함됩니다.

+++

+++ 프로젝트 통합

Edge Delivery Services 프로젝트에서 이러한 구조화된 접근 방식을 통해 양식 스타일을 구현합니다.

```
/blocks/form/form.css          // Core form block styles (copied from boilerplate)
/styles/styles.css             // Global site styles and CSS variable overrides
/styles/lazy-styles.css        // Additional component enhancements
```

+++

+++ 구현 전략

**CSS 사용자 지정 속성 무시**: 전역 스타일에서 양식 변수를 재정의하여 브랜드별 스타일을 구현합니다.

```css
/* In /styles/styles.css */
:root {
    /* Brand-specific overrides */
    --button-primary-color: #your-brand-color;
    --form-background-color: #your-background;
    --label-color: #your-text-color;
}
```

**구성 요소별 사용자 지정**:
CSS 변수 시스템을 유지하면서 구성 요소별 스타일을 추가합니다.

```css
/* Enhanced component styling */
.form .text-wrapper input {
    border-radius: var(--form-card-border-radius);
    transition: all 0.2s ease;
}

.form .text-wrapper input:focus {
    transform: translateY(-1px);
    box-shadow: 0 0 0 3px rgba(var(--button-primary-color), 0.1);
}
```

**반응형 디자인 통합**: 일관된 반응형 동작을 위해 미디어 쿼리 내에서 CSS 사용자 지정 속성을 사용합니다.

```css
@media (max-width: 768px) {
    :root {
        --form-input-padding: 0.875rem;
        --form-field-vert-gap: 1rem;
        --form-padding: 1rem;
    }
}
```

+++

### 전체 스타일 구현 예

이 섹션에서는 CSS 사용자 지정 속성을 사용하여 최신 브랜드 양식을 만드는 방법을 보여줍니다. 구현은 쉽게 이해하고 탐색할 수 있도록 명확한 하위 섹션으로 분류됩니다.



+++ &#x200B;1. 브랜드 테마 변수

CSS 사용자 지정 속성을 사용하여 브랜드의 색상 팔레트, 간격 및 타이포그래피를 정의합니다.

```css
/* Custom brand theme */
:root {
  /* Brand color system */
  --brand-primary: #2563eb;
  --brand-secondary: #64748b;
  --brand-success: #059669;
  --brand-error: #dc2626;
  --brand-background: #f8fafc;
  
  /* Override form variables */
  --background-color-primary: #ffffff;
  --button-primary-color: var(--brand-primary);
  --button-primary-hover-color: #1d4ed8;
  --form-error-color: var(--brand-error);
  --form-background-color: var(--brand-background);
  --label-color: var(--brand-secondary);
  --border-color: #d1d5db;
  
  /* Enhanced spacing */
  --form-input-padding: 1rem;
  --form-field-vert-gap: 1.5rem;
  --form-padding: 2rem;
  
  /* Modern typography */
  --form-font-size-s: 16px;
  --form-label-font-weight: 500;
}
```


+++

+++ &#x200B;2. 양식 컨테이너 스타일 지정

시각적으로 매력적인 레이아웃을 만들기 위해 양식 컨테이너에 최신 배경, 테두리 반경 및 그림자를 적용합니다.


```css
/* Enhanced form container */
.form {
    background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
    max-width: 600px;
    margin: 2rem auto;
    overflow: hidden;
}
```




+++

+++ &#x200B;3. 필드 스타일 입력

깔끔하고 현대적인 디자인을 위해 텍스트, 이메일 및 숫자 입력 필드를 스타일링합니다.


```css
/* Modern input styling */
.form .text-wrapper input,
.form .email-wrapper input,
.form .number-wrapper input {
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    padding: var(--form-input-padding);
    font-size: 16px;
    transition: all 0.2s ease;
    width: 100%;
}
```


+++

+++ &#x200B;4. 추가 사용자 정의

필요에 따라 특정 필드, 상태 또는 구성 요소를 타겟팅하여 양식 스타일을 추가로 확장할 수 있습니다. 고급 패턴은 이전 섹션을 참조하십시오.

```css
/* Custom brand theme */
:root {
    /* Brand color system */
    --brand-primary: #2563eb;
    --brand-secondary: #64748b;
    --brand-success: #059669;
    --brand-error: #dc2626;
    --brand-background: #f8fafc;
    
    /* Override form variables */
    --background-color-primary: #ffffff;
    --button-primary-color: var(--brand-primary);
    --button-primary-hover-color: #1d4ed8;
    --form-error-color: var(--brand-error);
    --form-background-color: var(--brand-background);
    --label-color: var(--brand-secondary);
    --border-color: #d1d5db;
    
    /* Enhanced spacing */
    --form-input-padding: 1rem;
    --form-field-vert-gap: 1.5rem;
    --form-padding: 2rem;
    
    /* Modern typography */
    --form-font-size-s: 16px;
    --form-label-font-weight: 500;
}

/* Enhanced form container */
.form {
    background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
    max-width: 600px;
    margin: 2rem auto;
    overflow: hidden;
}

/* Modern input styling */
.form .text-wrapper input,
.form .email-wrapper input,
.form .number-wrapper input {
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    padding: var(--form-input-padding);
    font-size: 16px;
    transition: all 0.2s ease;
    width: 100%;
}

.form .text-wrapper input:focus,
.form .email-wrapper input:focus,
.form .number-wrapper input:focus {
    border-color: var(--brand-primary);
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
    transform: translateY(-1px);
}

/* Enhanced button styling */
.form .button-wrapper button[type="submit"] {
    background: linear-gradient(135deg, var(--brand-primary) 0%, #1d4ed8 100%);
    color: white;
    border: none;
    border-radius: 8px;
    padding: 1rem 2rem;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease;
    width: 100%;
    box-shadow: 0 4px 12px rgba(37, 99, 235, 0.3);
}

.form .button-wrapper button[type="submit"]:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(37, 99, 235, 0.4);
}
```

이 포괄적인 접근 방식은 CSS 사용자 지정 속성을 사용하여 적응형 Forms 블록 시스템의 구조적 무결성과 접근성 기능을 유지하면서 정교한 맞춤화를 구현하는 방법을 보여 줍니다.

+++

## CSS 문제 해결

+++ CSS 특이성 문제

```css
/- ❌ Problem: Styles not applying */
.text-wrapper input {
  color: red;
}

/- ✅ Solution: Match or exceed existing specificity */
.form .text-wrapper input {
  color: red;
}

/- ✅ Alternative: Use higher specificity when needed */
main .form .text-wrapper input {
  color: red;
}
```

+++

+++ CSS 변수 재정의 문제

```css
/- ❌ Problem: Variables not working */
.form {
  --form-border-color: blue; /- Local scope only */
}

/- ✅ Solution: Define in root scope */
:root {
  --form-border-color: blue; /- Global scope */
}
```

+++

+++ 양식 상태 스타일링

```css
/- Validation states */
.form .field-wrapper.error input {
  border-color: var(--form-error-color);
}

.form .field-wrapper.success input {
  border-color: var(--form-success-color);
}

/- Loading state */
.form[data-submitting="true"] {
  opacity: 0.7;
  pointer-events: none;
}

/- Disabled state */
.form input:disabled {
  background-color: var(--form-input-disabled-background);
  cursor: not-allowed;
}
```

+++

+++ 일반적인 선택기 실수

```css
/- ❌ Incorrect: Assumes direct nesting */
.form form input {
  /- This might miss inputs in wrappers */
}

/- ✅ Correct: Target actual structure */
.form .text-wrapper input {
  /- Targets actual HTML structure */
}

/- ❌ Avoid: Unnecessary specificity */
main .form form .text-wrapper input {
  /- Too specific, harder to override */
}

/- ✅ Preferred: Balanced specificity */
.form .text-wrapper input {
  /- Easier to maintain and override */
}
```

+++



### **구성 요소별 모범 사례**


+++ 단추 스타일 지정

```css
/- Primary buttons */
.form .button-wrapper button[type="submit"] {
  background-color: var(--form-focus-color);
  color: white;
  border: none;
  padding: var(--form-input-padding);
  border-radius: var(--form-border-radius);
}

/- Secondary buttons */
.form .button-wrapper button[type="reset"] {
  background-color: transparent;
  color: var(--form-text-color);
  border: 1px solid var(--form-border-color);
}
```

+++

+++ 반응형 양식 디자인

```css
/- Mobile-first approach */
.form {
  width: 100%;
  padding: 1rem;
}

/- Tablet and up */
@media (min-width: 768px) {
  .form {
    max-width: var(--form-max-width);
    padding: var(--form-padding);
  }
}
```

+++

## 모범 사례 요약

1. **CSS 사용자 지정 속성 사용**: 일관된 설정을 위해 변수 활용
2. **블록 기반 아키텍처 준수**: `.form`을(를) 기본 블록 선택기로 사용
3. **특이성 과다 사용 방지**: 필요한 경우가 아니면 `main .form form`을(를) 사용하지 마십시오
4. **래퍼 타깃팅**: 구성 요소 타깃팅에 `.{Type}-wrapper` 패턴을 사용합니다.
5. **일관성 유지**: 프로젝트 전체에서 동일한 선택기 패턴을 사용합니다.
6. **여러 장치에서 테스트**: 모바일, 태블릿 및 데스크톱에서 양식이 제대로 작동하는지 확인
7. **접근성 확인**: 스타일이 화면 판독기나 키보드 탐색에 방해가 되지 않도록 합니다.


