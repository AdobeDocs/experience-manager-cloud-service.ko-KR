---
title: 사용자 지정 함수의 범위 개체 소개
description: Form은 규칙을 실행할 때 함수에 마지막 인수로 전달되는 사용자 지정 함수의 범위 개체를 지원합니다.
keywords: 사용자 지정 함수, 전역 개체, 필드 개체의 범위 개체를 참조하십시오.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: af211649a4f22d06f4e8669335a8267ee948a408
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# 사용자 지정 함수의 범위 개체

적응형 Forms에서, 규칙이 실행될 때 범위 개체가 함수에 대한 마지막 인수로 전달됩니다. 함수 내에서 양식/필드 속성을 읽고 양식을 수정하는 데 사용할 수 있습니다. 범위 개체에는 폼에 대한 읽기 전용 프록시 개체, 트리거된 이벤트 및 대상 필드가 포함되어 있습니다. `$`(예: `scope.form.$id` 및 `scope.field.$id`)을(를) 추가하여 범위 개체를 사용하여 양식 및 필드 속성에 액세스할 수 있습니다.

## 범위 개체를 사용한 양식 수정 함수

범위 객체에는 양식 수정을 위한 다음과 같은 함수가 있습니다.

| 함수 | 구문 | 설명 | 코드 샘플 |
|-----------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------|
| **setProperty** | `setProperty(any $element, any $payload)` | `$payload`을(를) 사용하여 `$element`의 속성을 설정합니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule). |
| **유효성 검사** | `validate([any $element])` | `$element`에서 유효성 검사를 실행합니다. 요소가 제공되지 않으면 전체 양식의 유효성을 검사합니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#validate-the-field). |
| **재설정** | `reset([any $element])` | `$element`을(를) 재설정합니다. 제공된 요소가 없으면 전체 양식이 재설정됩니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel). |
| **importData** | `importData(any $payload)` | 데이터를 양식으로 가져와 기존 양식 데이터를 바꿉니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads). |
| **exportData** | `exportData()` | 양식의 데이터를 반환합니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server). |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | 양식 제출을 트리거합니다. `$data` 매개 변수는 전송할 항목을 지정하고 `$submit_as`은(는) 콘텐츠 형식을 정의합니다(기본값은 &#39;multipart/form-data&#39;임). 선택적 `$validate_form`은(는) 양식의 유효성 검사 여부를 결정합니다(기본값: true). 성공하면 `submitSuccess`이(가) 실행되고, 실패하면 `submitError`이(가) 실행됩니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server). |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | 포커스를 `$element`(패널 또는 필드)로 설정합니다. 요소가 제공되지 않으면 규칙을 트리거한 필드로 포커스가 설정됩니다. 선택적 `$focusOption` 매개 변수(열거형 형식 `FocusOption`의)는 `$element`을(를) 기준으로 &#39;nextItem&#39; 또는 &#39;previousItem&#39;에 집중할지 여부를 지정합니다. 패널을 지정하면 탐색이 해당 패널로 제한됩니다. 필드가 있으면 상위 패널에서 탐색이 수행됩니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field). |
| **dispatchEvent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | `$element`에서 지정한 요소에 `$eventName` 형식의 이벤트를 전달합니다. 요소를 제공하지 않으면 폼에서 이벤트가 발송됩니다. 선택적 `$payload`은(는) 이벤트를 처리하는 식에 사용할 수 있습니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property). |
| **잘못된 필드로 표시** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | `$fieldIdentifier`에 의해 식별된 필드를 잘못된 것으로 표시하고 유효성 검사 메시지를 `$validationMessage`(으)로 설정합니다. 선택적 `$option` 매개 변수는 `$fieldIdentifier`이(가) `id`, `name` 또는 `dataRef`(으)로 해석되는지 여부를 지정합니다. 기본값은 `{useId: true}`이며 지원되는 값은 `{useId: true}`, `{useDataRef: true}` 및 `{useQualifiedName: true}`입니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid). |

## 추가 참조

{{see-also-rule-editor}}