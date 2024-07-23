---
title: 이 문서에서는 핵심 구성 요소를 기반으로 하는 적응형 양식의 사용자 지정 기능에 대한 다양한 사용 사례를 간략하게 설명합니다.
description: 이 문서에서는 핵심 구성 요소를 기반으로 하는 적응형 양식의 사용자 지정 기능에 대한 다양한 사용 사례를 간략하게 설명합니다. 사용자 지정 함수는 규칙 편집기에서 양식에 대한 사용자 지정 규칙을 만드는 데 사용됩니다.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
source-git-commit: 580e206427f2205fa8ca537ab4988a90c988171b
workflow-type: tm+mt
source-wordcount: '2108'
ht-degree: 0%

---


# 사용자 지정 함수 개발 및 사용의 예

이 문서에서는 핵심 구성 요소를 기반으로 하는 적응형 양식에 대한 사용자 지정 기능의 세부 예제를 제공하여 다양한 시나리오에서 효과적인 구현에 대한 중요한 통찰력을 제공합니다. 사용자 지정 함수는 AEM Forms의 규칙 편집기에서 사용되며 개발자가 양식 동작을 제어하는 논리를 정의 및 제어할 수 있도록 합니다.
이 문서에서는 다양한 사용자 정의 함수 구현에 대해 알아보고, 특정 요구 사항을 충족하도록 양식을 사용자 정의하고 전반적인 기능을 향상시키는 데 이 함수를 사용할 수 있는 방법을 소개합니다.

## 사용자 정의 함수를 사용하여 드롭다운 목록 옵션 설정

핵심 구성 요소의 규칙 편집기에서 런타임에 드롭다운 목록 옵션을 설정하는 **옵션 설정 of** 속성을 지원하지 않습니다. 그러나 사용자 지정 함수를 사용하여 드롭다운 목록 옵션을 설정할 수 있습니다.

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에서 설명한 대로 사용자 지정 함수에 다음 코드를 추가하여 사용자 지정 함수를 사용하여 드롭다운 목록 옵션을 설정합니다.

```javascript
    /**
    * @name setEnums
    * @returns {string[]}
    **/
    function setEnums() {
    return ["0","1","2","3","4","5","6"];   
    }

    /**
    * @name setEnumNames
    * @returns {string[]}
    **/
    function setEnumNames() {
    return ["Sunday","Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
    }
```

위의 코드에서는 `setEnums`을(를) 사용하여 `enum` 속성을 설정하고 `setEnumNames`을(를) 사용하여 드롭다운의 `enumNames` 속성을 설정합니다.

사용자가 `Next` 단추를 클릭할 때 드롭다운 목록 옵션의 값을 설정하는 `Next` 단추에 대한 규칙을 만들어 보겠습니다.

![드롭다운 목록 옵션](/help/forms/assets/drop-down-list-options.png)

표시 버튼을 클릭할 때 드롭다운 목록의 옵션이 설정되는 위치를 보여 주려면 아래 그림을 참조하십시오.

![규칙 편집기의 드롭다운 옵션](/help/forms/assets/drop-down-option-rule-editor.png)

## `SetProperty` 규칙을 사용하여 패널 표시

사용자 지정 함수에서 `Contact Us` 양식의 도움을 받아 필드 및 전역 개체를 사용하는 방법을 알아보겠습니다.

![연락처 양식](/help/forms/assets/contact-us-form.png)

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 양식 필드를 `Required`(으)로 설정합니다.

```javascript
    
    /**
    * enablePanel
    * @name enablePanel
    * @param {object} field1
    * @param {object} field2
    * @param {scope} globals 
    */

    function enablePanel(field1,field2, globals)
    {
       if(globals.functions.validate(field1).length === 0)
       {
       globals.functions.setProperty(field2, {visible: true});
       }
    }
```

>[!NOTE]
>
> * `[form-path]/jcr:content/guideContainer.model.json`에 있는 사용 가능한 속성을 사용하여 필드 속성을 구성할 수 있습니다.
> * Globals 개체의 `setProperty` 메서드를 사용하여 양식을 수정한 내용은 기본적으로 비동기적이며 사용자 지정 함수를 실행하는 동안 반영되지 않습니다.

이 예제에서는 단추를 클릭하면 `personaldetails` 패널의 유효성 검사가 수행됩니다. 패널에서 오류가 감지되지 않으면 버튼을 클릭할 때 다른 패널인 `feedback` 패널이 표시됩니다.

`Next` 단추에 대한 규칙을 만들어 `personaldetails` 패널의 유효성을 검사하고 사용자가 `Next` 단추를 클릭할 때 `feedback` 패널이 표시되도록 하겠습니다.

![속성 설정](/help/forms/assets/custom-function-set-property.png)

`Next` 단추를 클릭할 때 `personaldetails` 패널의 유효성을 검사한 위치를 보여 주는 아래 그림을 참조하십시오. `personaldetails` 내의 모든 필드의 유효성을 검사하면 `feedback` 패널이 표시됩니다.

![속성 양식 미리 보기 설정](/help/forms/assets/set-property-form-preview.png)

`personaldetails` 패널의 필드에 오류가 있는 경우 `Next` 단추를 클릭하면 필드 수준에서 오류가 표시되고 `feedback` 패널은 표시되지 않습니다.

![속성 양식 미리 보기 설정](/help/forms/assets/set-property-panel.png)

## 필드 유효성 검사

사용자 지정 함수에서 필드 및 전역 개체를 사용하여 `Contact Us` 양식을 통해 필드의 유효성을 검사하는 방법을 알아보겠습니다.

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 필드의 유효성을 검사합니다.

```javascript
    /**
    * validateField
    * @name validateField
    * @param {object} field
    * @param {scope} globals
    */
    function validateField(field,globals)
    {
    
        globals.functions.validate(field);
    
    }   
```

>[!NOTE]
>
> `validate()` 함수에서 인수가 전달되지 않으면 폼의 유효성을 검사합니다.

이 예제에서는 사용자 지정 유효성 검사 패턴이 `contact` 필드에 적용됩니다. 사용자는 전화 번호를 `10`(으)로 시작하여 `8` 자릿수를 입력해야 합니다. 사용자가 `10`(으)로 시작하지 않거나 `8`자리보다 많거나 적은 전화 번호를 입력하면 단추를 클릭할 때 유효성 검사 오류 메시지가 나타납니다.

![전자 메일 주소 유효성 검사 패턴](/help/forms/assets/custom-function-validation-pattern.png)

이제 다음 단계는 단추 클릭에서 `contact` 필드의 유효성을 검사하는 `Next` 단추에 대한 규칙을 만드는 것입니다.

![유효성 검사 패턴](/help/forms/assets/custom-function-validate.png)

사용자가 `10`(으)로 시작하지 않는 전화 번호를 입력하는 경우 필드 수준에 오류 메시지가 표시되는지 확인하려면 아래 그림을 참조하십시오.

![전자 메일 주소 유효성 검사 패턴](/help/forms/assets/custom-function-validate-error-message.png)

사용자가 올바른 전화 번호를 입력하고 `personaldetails` 패널의 모든 필드가 유효성이 확인되면 `feedback` 패널이 화면에 나타납니다.

![전자 메일 주소 유효성 검사 패턴](/help/forms/assets/validate-form-preview-form.png)

## 패널 재설정

사용자 지정 함수에서 필드 및 전역 개체를 사용하여 `Contact Us` 양식을 사용하여 필드를 재설정하는 방법에 대해 알아보겠습니다.

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 패널을 재설정합니다.

```javascript
    /**
    * resetField
    * @name  resetField
    * @param {string} input1
    * @param {object} field
    * @param {scope} globals 
    */
    function  resetField(field,globals)
    {
    
        globals.functions.reset(field);
    
    }
```

>[!NOTE]
>
> `reset()` 함수에서 인수가 전달되지 않으면 폼의 유효성을 검사합니다.

이 예제에서는 `Clear` 단추를 클릭하면 `personaldetails` 패널이 재설정됩니다. 다음 단계는 단추 클릭 시 패널을 재설정하는 `Clear` 단추에 대한 규칙을 만드는 것입니다.

![지우기 단추](/help/forms/assets/custom-function-reset-field.png)

사용자가 `clear` 단추를 클릭하면 `personaldetails` 패널이 재설정됨을 표시하려면 아래 그림을 참조하십시오.

![양식 재설정](/help/forms/assets/custom-function-reset-form.png)

## 필드 수준에서 사용자 정의 메시지를 표시하고 필드를 유효하지 않은 것으로 표시

사용자 지정 함수에서 필드 및 전역 개체를 사용하여 필드 수준에서 사용자 지정 메시지를 표시하고 필드를 `Contact Us` 양식의 도움으로 잘못된 것으로 표시하는 방법에 대해 알아보겠습니다.

`markFieldAsInvalid()` 함수를 사용하여 필드를 잘못된 필드로 정의하고 필드 수준에서 사용자 지정 오류 메시지를 설정할 수 있습니다. `fieldIdentifier` 값은 `fieldId`, `field qualifiedName` 또는 `field dataRef`일 수 있습니다. 이름이 `option`인 개체의 값은 `{useId: true}`, `{useQualifiedName: true}` 또는 `{useDataRef: true}`일 수 있습니다.
필드를 유효하지 않은 것으로 표시하고 사용자 정의 메시지를 설정하는 데 사용되는 구문은 다음과 같습니다.

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 필드 수준에서 사용자 지정 메시지를 사용하도록 설정합니다.

```javascript
    /**
    * customMessage
    * @name customMessage
    * @param {object} field
    * @param {scope} globals 
    */
    function customMessage(field, globals) {
    const minLength = 15;
    const comments = field.$value.trim();
    if (comments.length < minLength) {
        globals.functions.markFieldAsInvalid(field.$id, "Comments must be at least 15 characters long.", { useId: true });
    }
}
```

이 예제에서 사용자가 주석 입력란에 15자 미만을 입력하면 사용자 정의 메시지가 필드 수준에 나타납니다.

다음 단계는 `comments` 필드에 대한 규칙을 만드는 것입니다.

![잘못된 필드로 표시](/help/forms/assets/custom-function-invalid-field.png)

`comments` 필드에 부정적인 피드백을 입력하면 필드 수준에서 사용자 지정 메시지를 표시하도록 트리거됨을 표시하려면 아래 데모를 참조하십시오.

![필드를 잘못된 미리 보기 양식으로 표시](/help/forms/assets/custom-function-invalidfield-form.png)

사용자가 주석 입력란에 15자 이상을 입력하면 필드의 유효성이 검사되고 양식이 제출됩니다.

![필드를 올바른 미리 보기 양식으로 표시](/help/forms/assets/custom-function-validfield-form.png)

## 변경된 데이터를 서버에 제출

사용자 지정 함수에서 필드 및 전역 개체를 사용하여 `Contact Us` 양식을 통해 조작된 데이터를 서버에 제출하는 방법에 대해 알아보겠습니다.

다음 코드 줄:
`globals.functions.submitForm(globals.functions.exportData(), false);`은(는) 조작 후 양식 데이터를 제출하는 데 사용됩니다.
* 첫 번째 인수는 제출할 데이터입니다.
* 두 번째 인수는 제출 전에 양식의 유효성을 검사할지 여부를 나타냅니다. `optional`이며 기본적으로 `true`(으)로 설정됩니다.
* 세 번째 인수는 제출 서류의 `contentType`이며, 기본값인 `multipart/form-data`과(와) 함께 선택 사항입니다. 다른 값은 `application/json` 및 `application/x-www-form-urlencoded`일 수 있습니다.

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 조작된 데이터를 서버에 제출합니다.

```javascript
    /**
    * submitData
    * @name submitData
    * @param {object} field
    * @param {scope} globals 
    */
    function submitData(globals)
    {
    
    var data = globals.functions.exportData();
    if(!data.comments) {
    data.comments = 'NA';
    }
    console.log('After update:{}',data);
    globals.functions.submitForm(data, false);
    }
```

이 예제에서 사용자가 `comments` 텍스트 상자를 비워 두면 양식 제출 시 `NA`이(가) 서버로 제출됩니다.

이제 데이터를 전송하는 `Submit` 단추에 대한 규칙을 만듭니다.

![데이터 제출](/help/forms/assets/custom-function-submit-data.png)

사용자가 `comments` 텍스트 상자를 비워 두면 `NA` 값이 서버에 제출된다는 것을 증명하려면 아래 `console window` 그림을 참조하십시오.

![콘솔 창에서 데이터 제출](/help/forms/assets/custom-function-submit-data-form.png)

또한 콘솔 창을 검사하여 서버에 제출된 데이터를 볼 수도 있습니다.

콘솔 창의 ![Inspect 데이터](/help/forms/assets/custom-function-submit-data-console-data.png)

## 양식 제출 성공 및 오류 처리기 재정의

사용자 지정 함수에서 필드 및 전역 개체를 사용하여 `Contact Us` 양식을 사용하여 제출 처리기를 재정의하는 방법을 알아보겠습니다.

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에 설명된 대로 다음 코드 행을 추가하여 양식 제출을 위한 제출 또는 실패 메시지를 사용자 지정하고 양식 제출 메시지를 모달 상자에 표시합니다.

```javascript
/**
 * Handles the success response after a form submission.
 *
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitSuccessHandler(globals) {
    var event = globals.event;
    var submitSuccessResponse = event.payload.body;
    var form = globals.form;

    if (submitSuccessResponse) {
        if (submitSuccessResponse.redirectUrl) {
            window.location.href = encodeURI(submitSuccessResponse.redirectUrl);
        } else if (submitSuccessResponse.thankYouMessage) {
            showModal("success", submitSuccessResponse.thankYouMessage);
        }
    }
}

/**
 * Handles the error response after a form submission.
 *
 * @param {string} customSubmitErrorMessage - The custom error message.
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitErrorHandler(customSubmitErrorMessage, globals) {
    showModal("error", customSubmitErrorMessage);
}
function showModal(type, message) {
    // Remove any existing modals
    var existingModal = document.getElementById("modal");
    if (existingModal) {
        existingModal.remove();
    }

    // Create the modal dialog
    var modal = document.createElement("div");
    modal.setAttribute("id", "modal");
    modal.setAttribute("class", "modal");

    // Create the modal content
    var modalContent = document.createElement("div");
    modalContent.setAttribute("class", "modal-content");

    // Create the modal header
    var modalHeader = document.createElement("div");
    modalHeader.setAttribute("class", "modal-header");
    modalHeader.innerHTML = "<h2>" + (type === "success" ? "Thank You" : "Error") + "</h2>";

    // Create the modal body
    var modalBody = document.createElement("div");
    modalBody.setAttribute("class", "modal-body");
    modalBody.innerHTML = "<p class='" + type + "-message'>" + message + "</p>";

    // Create the modal footer
    var modalFooter = document.createElement("div");
    modalFooter.setAttribute("class", "modal-footer");

    // Create the close button
    var closeButton = document.createElement("button");
    closeButton.setAttribute("class", "close-button");
    closeButton.innerHTML = "Close";
    closeButton.onclick = function() {
        modal.remove();
    };

    // Append the elements to the modal content
    modalFooter.appendChild(closeButton);
    modalContent.appendChild(modalHeader);
    modalContent.appendChild(modalBody);
    modalContent.appendChild(modalFooter);

    // Append the modal content to the modal
    modal.appendChild(modalContent);

    // Append the modal to the document body
    document.body.appendChild(modal);
}
```

이 예에서 사용자가 `customSubmitSuccessHandler` 및 `customSubmitErrorHandler` 사용자 지정 함수를 사용하면 성공 및 실패 메시지가 모달에 표시됩니다. JavaScript 함수 `showModal(type, message)`은(는) 모달 대화 상자를 동적으로 만들어 화면에 표시하는 데 사용됩니다.

이제 성공적인 양식 제출을 위한 규칙을 만듭니다.

![양식 제출 성공](/help/forms/assets/form-submission-success.png)

양식이 성공적으로 제출되면 성공 메시지가 모달에 표시된다는 것을 증명하려면 아래 그림을 참조하십시오.

![양식 제출 성공 메시지](/help/forms/assets/form-submission-success-message.png)

마찬가지로 실패한 양식 제출에 대한 규칙을 만들어 보겠습니다.

![양식 제출 실패](/help/forms/assets/form-submission-fail.png)

양식 제출이 실패할 때 오류 메시지가 모달에 표시되는지 보여 주려면 아래 그림을 참조하십시오.

![양식 제출 실패 메시지](/help/forms/assets/form-submission-fail-message.png)

기본 방식으로 양식 제출 성공 및 실패를 표시하려면 `Default submit Form Success Handler` 및 `Default submit Form Error Handler` 함수를 즉시 사용할 수 있습니다.

사용자 지정 제출 처리기가 기존 AEM 프로젝트 또는 양식에서 예상대로 실행되지 않는 경우 [문제 해결](#troubleshooting) 섹션을 참조하십시오.

## 반복 가능 패널의 특정 인스턴스에서 작업 수행

반복 가능 패널에서 시각적 규칙 편집기를 사용하여 만든 규칙은 반복 가능 패널의 마지막 인스턴스에 적용됩니다. 반복 가능 패널의 특정 인스턴스에 대한 규칙을 작성하려면 사용자 지정 함수를 사용합니다.

다른 양식을 `Booking Form`(으)로 만들어 목적지로 향하는 여행자에 대한 정보를 수집하겠습니다. 여행자 패널이 반복 가능한 패널로 추가됩니다. 이 패널에서 `Add Traveler` 버튼을 사용하여 5명의 여행자에 대한 세부 정보를 추가할 수 있습니다.

![여행자 정보](/help/forms/assets/traveler-info-form.png)

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에 설명된 대로 다음 코드 행을 추가하여 마지막 인스턴스가 아닌 반복 가능한 패널의 특정 인스턴스에서 작업을 수행합니다.

```javascript
/**
* @name hidePanelInRepeatablePanel
* @param {scope} globals
*/
function hidePanelInRepeatablePanel(globals)
{    
    var repeatablePanel = globals.form.travelerinfo;
    // hides a panel inside second instance of repeatable panel
    globals.functions.setProperty(repeatablePanel[1].traveler, {visible : false});
}  
```

이 예제에서 `hidePanelInRepeatablePanel` 사용자 지정 함수는 반복 가능 패널의 특정 인스턴스에서 작업을 수행합니다. 위의 코드에서 `travelerinfo`은(는) 반복 가능한 패널을 나타냅니다. `repeatablePanel[1].traveler, {visible: false}` 코드는 반복 가능한 패널의 두 번째 인스턴스에서 패널을 숨깁니다.

레이블이 `Hide`인 단추를 추가하고 반복 가능한 패널의 두 번째 인스턴스를 숨기는 규칙을 추가합니다.

![패널 규칙 숨기기](/help/forms/assets/custom-function-hidepanel-rule.png)

`Hide`을(를) 클릭할 때 두 번째 반복 가능한 인스턴스의 패널이 숨겨짐을 보여 주는 아래 비디오를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3429554?quality=12&learn=on)

## 양식 로드 시 값으로 필드를 미리 채웁니다.

사용자 지정 함수에서 필드 및 전역 개체를 사용하여 `Booking Form`의 도움을 받아 필드를 미리 채우는 방법에 대해 알아보겠습니다.

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에서 설명한 대로 다음 코드 행을 추가하여 양식을 초기화할 때 필드에 미리 채워진 값을 로드합니다.

```javascript
/**
 * Tests import data
 * @name testImportData
 * @param {scope} globals
 */
function testImportData(globals)
{
    globals.functions.importData(Object.fromEntries([['amount','10000']]));
} 
```

앞서 설명한 코드에서는 양식을 로드할 때 `testImportData` 함수가 `Booking Amount` 텍스트 상자 필드를 미리 채웁니다. 예약 양식을 사용하려면 최소 예약 금액이 `10,000`이어야 합니다.

양식 초기화 시 규칙을 만들어 `Booking Amount` 텍스트 상자 필드의 값이 양식을 로드할 때 지정된 값으로 미리 채워지는 방법을 살펴보겠습니다.

![데이터 규칙 가져오기](/help/forms/assets/custom-function-import-data.png)

양식을 로드할 때 `Booking Amount` 텍스트 상자의 값이 지정된 값으로 미리 채워져 있음을 보여 주는 아래 스크린샷을 참조하십시오.

![데이터 규칙 양식 가져오기](/help/forms/assets/custom-function-prefill-form.png)

## 특정 필드에 포커스 설정

사용자 지정 함수에서 필드 및 전역 개체를 사용하여 `Booking Form`을(를) 통해 특정 필드에 대한 포커스를 설정하는 방법에 대해 알아보겠습니다.

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에서 설명한 대로 다음 코드 행을 추가하여 `Submit` 단추를 클릭할 때 지정된 필드에 포커스를 설정합니다.

```javascript
/**
 * @name testSetFocus
 * @param {object} emailField
 * @param {scope} globals
 */
    function testSetFocus(field, globals)
    {
        globals.functions.setFocus(field);
    }
```

`Email ID` 텍스트 상자 필드를 클릭할 때 포커스를 설정하기 위해 `Submit` 단추에 규칙을 추가하겠습니다.

![포커스 규칙 설정](/help/forms/assets/custom-function-set-focus.png)

`Submit` 단추를 클릭하면 `Email ID` 필드에 포커스가 설정되었음을 보여 주는 아래 스크린샷을 참조하십시오.

![포커스 규칙 설정](/help/forms/assets/custom-function-set-focus-form.png)

>[!NOTE]
>
> `email` 필드를 기준으로 다음 또는 이전 필드에 초점을 맞추려면 선택적 `$focusOption` 매개 변수를 사용할 수 있습니다.

## `dispatchEvent` 속성을 사용하여 반복 가능한 패널 추가 또는 삭제

사용자 지정 함수에서 필드 및 전역 개체를 사용하여 `Booking Form`의 도움을 받아 `dispatchEvent` 속성을 사용하여 반복 가능한 패널을 추가하거나 삭제하는 방법에 대해 알아보겠습니다.

[create-custom-function](/help/forms/custom-function-core-component-create-function.md) 섹션에서 설명한 대로 다음 코드 행을 추가하여 `dispatchEvent` 속성을 사용하여 `Add Traveler` 단추를 클릭할 때 패널을 추가합니다.

```javascript
/**
 * Tests add instance with dispatchEvent
 * @name testAddInstance
 * @param {scope} globals
 */
function testAddInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel,'addInstance');
}
```

`Add Traveler` 단추를 클릭할 때 반복 가능한 패널을 추가하는 규칙을 추가하겠습니다.

![패널 규칙 추가](/help/forms/assets/custom-function-add-panel.png)

`Add Traveler` 단추를 클릭하면 `dispatchEvent` 속성을 사용하여 패널이 추가됨을 보여 주는 아래 gif를 참조하십시오.

![패널 추가](/help/forms/assets/custom-function-add-panel.gif)

마찬가지로 [create-custom-function](#create-custom-function) 섹션에서 설명한 대로 다음 코드 행을 추가하여 `dispatchEvent` 속성을 사용하여 `Delete Traveler` 단추를 클릭할 때 패널을 삭제합니다.

```javascript
/**
 
 * @name testRemoveInstance
 * @param {scope} globals
 */
function testRemoveInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel, 'removeInstance');
} 
```

`Delete Traveler` 단추를 클릭할 때 반복 가능한 패널을 삭제하는 규칙을 추가하겠습니다.

![패널 규칙 삭제](/help/forms/assets/custom-function-delete-panel.png)

`Delete Traveler` 단추를 클릭하면 `dispatchEvent` 속성을 사용하여 여행자 패널이 삭제됨을 보여 주는 아래 gif를 참조하십시오.

![패널 삭제](/help/forms/assets/custom-function-delete-panel.gif)


## 문제 해결

* 사용자 지정 제출 처리기가 기존 AEM 프로젝트 또는 양식에서 예상대로 수행되지 않으면 다음 단계를 수행하십시오.
   * [핵심 구성 요소 버전이 3.0.18 이상](https://github.com/adobe/aem-core-forms-components)(으)로 업데이트되었는지 확인하십시오. 그러나 기존 AEM 프로젝트 및 양식의 경우 따라야 할 추가 단계가 있습니다.

   * AEM 프로젝트의 경우 사용자는 `submitForm('custom:submitSuccess', 'custom:submitError')`의 모든 인스턴스를 `submitForm()`(으)로 바꾸고 Cloud Manager 파이프라인을 통해 프로젝트를 배포해야 합니다.

   * 기존 양식의 경우 사용자 지정 제출 처리기가 제대로 작동하지 않으면 사용자가 규칙 편집기를 사용하여 **제출** 단추에서 `submitForm` 규칙을 열고 저장해야 합니다. 이 작업은 `submitForm('custom:submitSuccess', 'custom:submitError')`의 기존 규칙을 양식의 `submitForm()`(으)로 바꿉니다.

## 추가 참조

{{see-also-rule-editor}}