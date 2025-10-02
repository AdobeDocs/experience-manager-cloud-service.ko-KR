---
title: 적응형 양식 블록 필드 속성 마스터하기
description: 스프레드시트 및 적응형 양식 블록 필드 속성을 사용하여 강력한 양식을 더 빠르게 작성할 수 있습니다. 이 안내서에는 EDS Forms Block에서 지원하는 속성이 모두 나열됩니다.
feature: Edge Delivery Services
exl-id: e86ccc36-bda0-4e9d-8d65-ae7cb3fa79b7
source-git-commit: 41dd61425ce3b7536ee805580f3841e32e40ee99
workflow-type: ht
source-wordcount: '930'
ht-degree: 100%

---

# 적응형 양식 블록 필드 속성

이 문서는 JSON 스키마가 `blocks/form/form.js`에서 렌더링된 HTML로 매핑되는 방식을 요약하며, 필드가 식별되고 렌더링되는 방식, 일반적인 패턴 및 필드별 차이점에 중점을 둡니다.

## 필드(`fieldType`)를 식별하는 방법

JSON 스키마의 각 필드에는 렌더링 방식을 결정하는 `fieldType` 속성이 있습니다. `fieldType`는 다음과 같습니다.

- **특수 유형**\
  예: `drop-down`, `radio-group`, `checkbox-group`, `panel`, `plain-text`, `image`, `heading` 등
- **올바른 HTML 입력 유형**\
  예: `text`, `number`, `email`, `date`, `password`, `tel`, `range`, `file` 등
- **`-input` 접미사가 있는 유형**\
  예: `text-input`, `number-input` 등 (이는 `text`, `number`와 같은 기본 유형으로 표준화됩니다.)

`fieldType`가 특수 유형과 일치하는 경우 **사용자 정의 렌더러**&#x200B;가 사용됩니다. 그렇지 않으면 **기본 입력 유형**&#x200B;으로 처리됩니다.

각 필드 유형에 대한 [전체 HTML 구조 및 속성](#common-html-structure)에 대한 아래 섹션을 참조하십시오.

## 필드에 사용되는 공통 속성

다음은 대부분의 필드에서 사용되는 속성입니다.

- `id`: 요소 ID를 지정하고 접근성을 지원합니다.
- `name`: 입력, 선택 또는 필드 세트 요소의 `name` 속성을 정의합니다.
- `label.value`, `label.richText`, `label.visible`: 레이블/범례 텍스트, HTML 콘텐츠 및 가시성을 지정합니다.
- `value`: 필드의 현재 값을 나타냅니다.
- `required`: `required` 속성 또는 유효성 검사 데이터를 추가합니다.
- `readOnly`, `enabled`: 필드를 편집 또는 비활성화할 수 있는지 여부를 제어합니다.
- `description`: 필드 아래에 도움말 텍스트를 표시합니다.
- `tooltip`: 입력에 대한 `title` 속성을 설정합니다.
- `constraintMessages`: 데이터 속성으로 사용자 정의 오류 메시지를 제공합니다.

## 일반적인 HTML 구조

대부분의 필드는 레이블 및 선택적 도움말 텍스트를 포함하는 래퍼 내에서 렌더링됩니다. 다음 코드 조각은 구조를 보여 줍니다.

```html
<div class="<fieldType>-wrapper field-wrapper field-<name>" data-id="<id>">
<label for="<id>" class="field-label">Label</label>
<!-- Field-specific input/element here -->
<div class="field-description" id="<id>-description">Description or error
message</div>
</div>
```

그룹(라디오/확인란) 및 패널의 경우, `<div>/<label>` 대신 `<legend>`가 있는 `<fieldset>`이 사용됩니다. 도움말 텍스트 <div> 설명이 설정된 경우에만 표시됩니다.

## 오류 메시지 표시

오류 메시지는 도움말 텍스트에 사용되는 것과 동일한 `.field-description` 요소에 표시되며, 동적으로 업데이트됩니다.

**필드가 유효하지 않은 경우**:

- 래퍼(예: `.field-wrapper`)에 클래스 `.field-invalid`가 할당됩니다.
- `.field-description` 콘텐츠가 해당 오류 메시지로 대체됩니다.

**필드가 유효해지는 경우**:

- `.field-invalid` 클래스가 제거됩니다.
- `.field-description`은 원래 도움말 텍스트(사용 가능한 경우)로 복원되거나 존재하지 않으면 제거됩니다.

JSON의 `constraintMessages` 속성을 사용하여 사용자 정의 오류 메시지를 정의할 수 있습니다.\
이러한 메시지는 래퍼에 `data-<constraint>ErrorMessage` 속성(예: `data-requiredErrorMessage`)으로 추가됩니다.

## 기본 입력 유형(HTML 입력 또는 `*-input`)

`fieldType`이 특수 유형이 아닌 경우 표준 HTML 입력 형식 또는 `<type>-input`(예: `text`, `number`, `email`, `date`, `text-input`, `number-input`)으로 처리됩니다.

- 접미사 `-input`은 제거되고, 기본 유형은 입력의 `type` 속성으로 사용됩니다.
- 이러한 유형은 `renderField()`에서 기본적으로 처리됩니다.
일반적인 기본 입력 유형은 `text`, `number`, `email`, `date`, `password`, `tel`, `range`, `file` 등입니다. 또한 `text-input`, `number-input` 등과 같이 기본 유형으로 표준화된 유형도 허용됩니다.

## 기본 입력 유형에 대한 제한

제한은 JSON 속성을 기반으로 입력 요소에 속성으로 추가됩니다.

| JSON 속성 | HTML 속성 | 적용 대상 |
|--------------|---------------|------------|
| maxLength | maxLength | 텍스트, 이메일, 암호, 전화 |
| minLength | minLength | 텍스트, 이메일, 암호, 전화 |
| 패턴 | 패턴 | 텍스트, 이메일, 암호, 전화 |
| 최대 | 최대 | 숫자, 범위, 날짜 |
| 최소 | 분 | 숫자, 범위, 날짜 |
| 단계 | 단계 | 숫자, 범위, 날짜 |
| 동의 | 동의 | 파일 |
| 다중 | 다중 | 파일 |
| maxOccur | data-max | 패널 |
| minOccur | data-min | 패널 |

>[!NOTE]
>
> `multiple`은 부울 속성입니다. 참인 경우 `multiple` 속성이 추가됩니다.

이러한 속성은 필드의 JSON 정의를 기반으로 양식 렌더러에 의해 자동으로 설정됩니다.

## 예: 제약 조건이 있는 HTML 구조

다음 예는 유효성 검사 제약 조건 및 오류 처리 속성을 사용하여 숫자 필드가 렌더링되는 방식을 보여 줍니다.

```html
<div class="number-wrapper field-wrapper field-age" data-id="age"
data-required="true"
data-minimumErrorMessage="Too small" data-maximumErrorMessage="Too large">
<label for="age" class="field-label">Age</label>
<input type="number"
id="age" name="age"
value="30" required min="18"
max="99" step="1"
placeholder="Enter your age" />
<div class="field-description" id="age-description"> Description or error message
</div>
</div>
```

HTML 구조의 각 부분은 데이터 바인딩, 유효성 검사, 도움말 또는 오류 메시지 표시에 역할을 합니다.

## 필드별 속성 및 해당 HTML 구조

### 드롭다운

**추가 속성:**

- `enum` / `enumNames`: 드롭다운의 옵션 값과 표시 레이블을 정의합니다.
- `type`: `array`로 설정된 경우 다중 선택을 활성화합니다.
- `placeholder`: 선택 전에 사용자를 안내하는 비활성화된 플레이스홀더 옵션을 추가합니다.

예:

```html
<div class="drop-down-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true"
data-requiredErrorMessage="This field is required">
<label for="<id>" class="field-label">Label</label>
<select id="<id>" name="<name>" required title="Tooltip" multiple>
<option disabled selected value="">Placeholder</option>
<option value="opt1">Option 1</option>
<option value="opt2">Option 2</option>
</select>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### 일반 텍스트

**추가 속성**:

- `richText`: 참인 경우 단락에 HTML을 렌더링합니다.

예:

```html
<div class="plain-text-wrapper field-wrapper field-<name>" data-id="<id>">
<label for="<id>" class="field-label">Label</label>
<p>Text or <a href="..." target="_blank">link</a></p>
</div>
```

### 확인란

**추가 속성**:

- `enum`: 확인란의 선택 및 선택 해제 상태에 대한 값을 정의합니다.
- `properties.variant / properties.alignment`: 스위치 스타일 확인란의 시각적 스타일 및 정렬을 지정합니다.

예:

```html
<div class="checkbox-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true"
data-requiredErrorMessage="Please check this box">
<label for="<id>" class="field-label">Label</label>
<input type="checkbox"
id="<id>"
name="<name>" value="on"
required
data-unchecked-value="off" />
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### 버튼

**추가 속성**:

- `buttonType`: 유형(버튼, 제출, 또는 재설정)을 설정하여 버튼의 비헤이비어를 지정합니다.

예:

```html
<div class="button-wrapper field-wrapper field-<name>" data-id="<id>">
<button id="<id>" name="<name>" type="submit" class="button"> Label
</button>
</div>
```

### 여러 줄 입력

**추가 속성**:

- `minLength`: 텍스트 또는 텍스트 영역 입력에 허용되는 최소 문자 수를 지정합니다.
- `maxLength`: 텍스트 또는 텍스트 영역 입력에 허용되는 최대 문자 수를 지정합니다.
- `pattern`: 입력 값이 유효한 것으로 간주되려면 일치해야 하는 정규 표현식을 정의합니다.
- `placeholder`: 값이 입력될 때까지 입력 또는 텍스트 영역 내에 플레이스홀더 텍스트를 표시합니다.

예:

```html
<div class="multiline-wrapper field-wrapper field-<name>" data-id="<id>"
data-minLengthErrorMessage="Too short" data-maxLengthErrorMessage="Too long">
<label for="<id>" class="field-label">Label</label>
<textarea id="<id>"
name="<name>" required
minlength="2"
maxlength="100"
pattern="[A-Za-z]+"
placeholder="Type here..."></textarea>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### 패널

**추가 속성**:

- `repeatable`: 패널을 동적으로 반복할 수 있는지 여부를 지정합니다.
- `minOccur`: 필요한 최소 패널 인스턴스 수를 설정합니다. maxOccur: 허용되는 최대 패널 인스턴스 수를 설정합니다.
- `properties.variant`: 패널의 시각적 스타일 또는 변형을 정의합니다.
- `properties.colspan`: 격자 레이아웃에서 패널이 차지하는 열 수를 지정합니다.
- `index`: 상위 컨테이너 내에서 패널의 위치를 나타냅니다.
- `fieldset`: 범례 또는 레이블이 있는 `<fieldset>` 요소 아래에 관련 필드를 그룹화합니다.

예:

```html
<fieldset class="panel-wrapper field-wrapper field-<name>" data-id="<id>"
name="<name>"
data-repeatable="true" data-index="0">
<legend class="field-label">Label</legend>
<!-- Nested fields here -->
<button type="button" class="add">Add</button>
<button type="button" class="remove">Remove</button>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### 라디오

**추가 속성**:

- `enum`: 라디오 필드에 허용되는 값 세트를 정의하며, 각 라디오 버튼 옵션의 값 속성으로 사용됩니다.

예:

```html
<div class="radio-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true">
<label for="<id>" class="field-label">Label</label>
<input type="radio" id="<id>" name="<name>" value="opt1" required />
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### 라디오 그룹

**추가 속성**:

- `enum`: 라디오 그룹의 옵션 값 목록을 정의하며, 각 라디오 버튼의 값으로 사용됩니다.
- `enumNames`: enum의 순서와 일치하는 라디오 버튼의 표시 레이블을 제공합니다.

예:

```html
<fieldset class="radio-group-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true">
<legend class="field-label">Label</legend>
<div>
<input type="radio" id="<id>-0" name="<name>" value="opt1" required />
<label for="<id>-0">Option 1</label>
</div>
<div>
<input type="radio" id="<id>-1" name="<name>" value="opt2" />
<label for="<id>-1">Option 2</label>
</div>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### **체크박스 그룹**

**추가 속성**:

- `enum`: 확인란 그룹의 옵션 값 목록을 정의하며, 각 확인란의 값으로 사용됩니다.
- `enumNames`: enum의 순서와 일치하는 확인란의 표시 레이블을 제공합니다.
- `minItems`: 유효성을 위해 선택해야 하는 최소 확인란 수를 설정합니다.
- `maxItems`: 오류가 트리거되기 전에 선택할 수 있는 최대 확인란 수를 설정합니다.

예:

```html
<fieldset class="checkbox-group-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true" data-minItems="1"
data-maxItems="3">
<legend class="field-label">Label</legend>
<div>
<input type="checkbox" id="<id>-0" name="<name>" value="opt1" required />
<label for="<id>-0">Option 1</label>
</div>
<div>
<input type="checkbox" id="<id>-1" name="<name>" value="opt2" />
<label for="<id>-1">Option 2</label>
</div>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### 이미지

**추가 속성**:

- `value / properties['fd:repoPath']`: 이미지를 렌더링하기 위한 이미지 소스 경로 또는 저장소 경로를 정의합니다.
- `altText`: 이미지의 대체 텍스트(대체 속성)를 제공하여 접근성을 개선합니다.

예:

```html
<div class="image-wrapper field-wrapper field-<name>" data-id="<id>">
<picture>
<img src="..." alt="..." />
<!-- Optimized sources -->
</picture>
</div>
```

### 제목

**추가 속성**:

- `value`: 제목 요소(예: `<h2>`) 내에 표시할 텍스트 콘텐츠를 지정합니다.

예:

```html
<div class="heading-wrapper field-wrapper field-<name>" data-id="<id>">
<h2 id="<id>">Heading Text</h2>
</div>
```

자세한 내용은 `blocks/form/form.js` 및 `blocks/form/util.js`의 구현을 참조하십시오.


<!--Each form field is represented as a dedicated row in the spreadsheet, analogous to fields in a database table. The column headers act as labels for the various properties supported by the form field block.

Think of your form as a table in a spreadsheet, where each line represents a different question or piece of information you want to collect. The table headings tell you what kind of answers you can expect for each section.

The below table lists all the properties that are supported by the Adaptive Forms Block.

**Master Your Forms with These Adaptive Forms Block Field Properties:**

This table details all the properties you can use to customize your Adaptive Forms Block fields:

| Property | Description | Example |
|---|---|---|
| **Type** | [HTML input type](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) (text, email, number, etc.), [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), [select](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select), [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) | `text`, `email`, `radio`, `select` |
| **Name** | This defines the unique identifier for submitted data (e.g., 'email' for an email address field).  Choose a clear and unique name for each field, as the name serves as internal field identifier used for data mapping during submission. | `user_name`, `email_address` |
| **Label** | User-friendly field label | `"Full Name"`, `"Choose your country"` |
| **Value** | Default value displayed | `"John Doe"`, `"United States"` |
| **Placeholder** | Hint text within the field | `"Enter your email address"` |
| **Description** | Help text for users | `"Please enter a valid email address"` |
| **Visible** | Show/hide the field initially | `true`, `false` |
| **Mandatory** | Require a value from the user | `true`, `false` |
| **Min/Max** | Set minimum/maximum values (number, date, text length) | `18` (age), `2025-12-31` (date) |
| **Accept** | Allowed file types for file upload | `"image/jpeg,image/png"` |
| **Multiple** | Allow multiple file selections | `true`, `false` |
| **Options** | Comma-separated list for dropdown menus | `"Option 1, Option 2, Option 3"` |
| **Checked** | Default-selected radio button/checkbox | `true`, `false` |
| **Fieldset** | Group fields together | Fieldset name (e.g., `"Personal Information"`) |-->
