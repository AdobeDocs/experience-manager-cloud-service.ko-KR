---
title: 사용자 지정 함수의 범위 개체 소개
description: Form은 규칙을 실행할 때 함수에 마지막 인수로 전달되는 사용자 지정 함수의 범위 개체를 지원합니다.
keywords: 사용자 지정 함수, 전역 개체, 필드 개체의 범위 개체를 참조하십시오.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 248c75a5-6335-41d2-aa0a-28a20a710f88
source-git-commit: e2bc958104bd9b75845ad2c213eec18d2560a3a4
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 1%

---

# 사용자 정의 함수의 범위 오브젝트

적응형 Forms에서, 규칙이 실행될 때 범위 개체가 함수에 대한 마지막 인수로 전달됩니다. 함수 내에서 양식/필드 속성을 읽고 양식을 수정하는 데 사용할 수 있습니다. 범위 개체에는 폼에 대한 읽기 전용 프록시 개체, 트리거된 이벤트 및 대상 필드가 포함되어 있습니다. `$`(예: `scope.form.$id` 및 `scope.field.$id`)을(를) 추가하여 범위 개체를 사용하여 양식 및 필드 속성에 액세스할 수 있습니다.

## 범위 개체를 사용한 양식 수정 함수

범위 객체에는 양식 수정을 위한 다음과 같은 함수가 있습니다.

| 함수 | 구문 | 설명 | 코드 샘플 |
|-----------------|--------|-------------|-------------|
| **setProperty** | `setProperty(any $element, any $payload)` | `$payload`을(를) 사용하여 대상 필드의 속성을 설정합니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule). |
| **유효성 검사** | `validate([any $element])` | 대상 필드에서 유효성 검사를 실행합니다. 대상이 제공되지 않은 경우 전체 양식에서 유효성 검사를 실행하고 일련의 유효성 검사 오류를 반환합니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#validate-the-field). |
| **재설정** *(더 이상 사용되지 않음)* | `reset([any $element])` | 사용하지 않음. 대신 `dispatchEvent($target, 'reset')`을(를) 사용합니다. 대상 필드를 재설정하거나 대상을 제공하지 않은 경우 전체 양식을 재설정합니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel). |
| **importData** | `importData(any $payload)` | 데이터를 양식으로 가져와 기존 양식 데이터를 바꿉니다. `qualifiedName`을(를) 지정하면 해당 컨테이너 필드로만 데이터를 가져옵니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads). |
| **exportData** | `exportData()` | 양식의 데이터를 반환합니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server). |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | 양식 제출을 트리거합니다. `$payload` 매개 변수를 통해 제출할 내용을 지정하고 `$contentType` 매개 변수를 통해 콘텐츠 형식을 설정할 수 있습니다. 데이터는 기본적으로 `multipart/form-data`(으)로 제출됩니다. 선택적 `$validateForm` 매개 변수는 제출 전에 양식을 유효성 검사할지 여부를 지정합니다(기본값: true). 성공하면 `submitSuccess`이(가) 실행되고, 실패하면 `submitError`이(가) 실행됩니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server). |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | 포커스를 패널이나 양식 필드가 될 수 있는 대상 필드로 설정합니다. 타겟이 제공되지 않으면 규칙을 트리거한 필드로 포커스가 설정됩니다. 선택적 `$focusOption` 매개 변수는 대상에 상대적인 다음 또는 이전 항목에 포커스를 두어야 하는지 여부를 지정합니다. 지원되는 값: `'nextItem'`, `'previousItem'`. 패널과 함께 사용할 경우 해당 패널로 탐색이 제한됩니다. 필드와 함께 사용할 경우 해당 필드의 상위 패널 내에서 탐색이 수행됩니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field). |
| **dispatchEvent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | `$eventName`에 의해 결정된 요소에 `$target` 유형의 이벤트를 전달합니다. 타겟이 제공되지 않으면 양식에서 이벤트를 발송합니다. 선택적 `$payload`은(는) 이벤트를 처리하는 식에 사용할 수 있습니다. 선택적 `$dispatch` 매개 변수는 이벤트 전파 동작을 제어합니다. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property). |
| **잘못된 필드로 표시** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | `$fieldIdentifier`에 의해 식별된 필드를 잘못된 것으로 표시하고 `$validationMessage`을(를) 표시합니다. 선택적 `$option` 매개 변수는 `$fieldIdentifier`을(를) `id`, `dataRef` 또는 `qualifiedName`(으)로 해석할지 여부를 지정합니다. 기본값은 `{useId: true}`입니다. 지원되는 값: `{useId: true}`, `{useDataRef: true}`, `{useQualifiedName: true}`. | 예제를 보려면 [여기를 클릭하세요](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid). |

## 추가 참조

{{see-also-rule-editor}}

