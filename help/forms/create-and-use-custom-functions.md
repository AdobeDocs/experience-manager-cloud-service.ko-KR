---
title: 적응형 양식에서 사용자 정의 함수 사용
description: AEM Forms은 사용자가 규칙 편집기 내에서 자체 함수를 만들고 사용할 수 있도록 하는 사용자 지정 함수를 지원합니다.
keywords: 사용자 지정 함수를 추가하고, 사용자 지정 함수를 사용하고, 사용자 지정 함수를 만들고, 규칙 편집기에서 사용자 지정 함수를 사용합니다.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
role: User, Developer
source-git-commit: a35556164ace2245577c3e22da1bc276fc3d98d0
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 1%

---


# 핵심 구성 요소를 기반으로 하는 적응형 Forms을 위한 맞춤형 기능 소개

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | 이 문서 |

AEM Forms은 사용자 정의 함수를 지원하므로 사용자가 복잡한 비즈니스 규칙을 구현하기 위한 JavaScript 함수를 정의할 수 있습니다. 이러한 사용자 지정 기능은 지정된 요구 사항을 충족하도록 입력된 데이터의 조작 및 처리를 용이하게 하여 양식의 기능을 확장합니다. 사전 정의된 기준에 따라 양식 동작을 동적으로 변경할 수 있습니다. 사용자 지정 기능을 사용하면 개발자가 복잡한 유효성 검사 논리를 적용하고, 동적 계산을 수행하고, 사용자 상호 작용이나 사전 정의된 기준에 따라 양식 요소의 표시나 동작을 제어할 수 있습니다.

>[!NOTE]
>
> 최신 기능을 사용하려면 [핵심 구성 요소](https://github.com/adobe/aem-core-forms-components)가 최신 버전으로 설정되어 있는지 확인하십시오.

## 사용자 정의 함수 사용 {#uses-of-custom-function}

적응형 Forms에서 사용자 정의 함수를 사용할 때의 장점은 다음과 같습니다.
* **데이터 처리**: 사용자 지정 함수를 사용하면 양식 필드에 입력한 데이터를 처리할 수 있습니다.
* **데이터 유효성 검사**: 사용자 지정 기능을 사용하면 양식 입력에 대한 사용자 지정 검사를 수행하고 지정된 오류 메시지를 제공할 수 있습니다.
* **동적 동작**: 사용자 지정 함수를 사용하면 특정 조건에 따라 양식의 동적 동작을 제어할 수 있습니다. 예를 들어 필드를 표시/숨기거나, 필드 값을 수정하거나, 양식 논리를 동적으로 조정할 수 있습니다.
* **통합**: 사용자 지정 함수를 사용하여 외부 API 또는 서비스와 통합할 수 있습니다. 외부 소스에서 데이터를 가져오거나 외부 Rest 끝점으로 데이터를 전송하거나 외부 이벤트를 기반으로 사용자 지정 작업을 수행하는 데 도움이 됩니다.

사용자 지정 함수는 기본적으로 JavaScript 파일에 추가되는 클라이언트 라이브러리입니다. 사용자 지정 함수를 만들면 규칙 편집기에서 적응형 양식에서 사용자가 선택할 수 있게 됩니다. 사용자 지정 함수는 규칙 편집기의 JavaScript 주석으로 식별됩니다.

## 사용자 지정 기능에 대해 지원되는 JavaScript 주석 {#js-annotations}

JavaScript 주석은 JavaScript 코드에 대한 메타데이터를 제공하는 데 사용됩니다. 여기에는 /** 및 @과 같은 특정 기호로 시작하는 주석이 포함됩니다. 주석은 함수, 변수 및 코드의 기타 요소에 대한 중요한 정보를 제공합니다. 적응형 양식은 사용자 정의 기능에 대해 다음 JavaScript 주석을 지원합니다.

### 이름

이 이름은 적응형 양식의 규칙 편집기에서 사용자 지정 기능을 식별하는 데 사용됩니다. 다음 구문을 사용하여 사용자 지정 함수의 이름을 지정합니다.

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`
  `functionName`은(는) 함수 이름입니다. 공백은 허용되지 않습니다.
  `<Function Name>`은(는) 적응형 양식의 규칙 편집기에 있는 함수의 표시 이름입니다.
함수 이름이 함수 자체의 이름과 동일한 경우 구문에서 `[functionName]`을(를) 생략할 수 있습니다.

### 매개변수

매개 변수는 사용자 지정 함수에서 사용하는 인수 목록입니다. 함수는 여러 매개 변수를 지원할 수 있습니다. 다음 구문을 사용하여 사용자 지정 함수에서 매개 변수를 정의할 수 있습니다.

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`.
  `{type}`은(는) 매개 변수 형식을 나타냅니다.  허용되는 매개 변수 유형은 다음과 같습니다.

   * string: 단일 문자열 값을 나타냅니다.
   * number: 단일 숫자 값을 나타냅니다.
   * 부울: 단일 부울 값(true 또는 false)을 나타냅니다.
   * string[]: 문자열 값의 배열을 나타냅니다.
   * number[]: 숫자 값의 배열을 나타냅니다.
   * boolean[]: 부울 값의 배열을 나타냅니다.
   * date: 단일 날짜 값을 나타냅니다.
   * date[]: 날짜 값의 배열을 나타냅니다.
   * array: 다양한 유형의 값을 포함하는 일반 배열을 나타냅니다.
   * object: 값을 직접 전달하는 대신 사용자 지정 함수에 전달되는 양식 개체를 나타냅니다.
   * 범위: 사용자 지정 함수 내에서 양식을 수정하는 방법, 양식 인스턴스, 대상 필드 인스턴스와 같은 읽기 전용 변수를 포함하는 globals 개체를 나타냅니다. 이 매개 변수는 JavaScript 주석의 마지막 매개 변수로 선언되며 적응형 양식의 규칙 편집기에 표시되지 않습니다. 범위 매개 변수는 양식 또는 구성 요소의 개체에 액세스하여 양식 처리에 필요한 규칙이나 이벤트를 트리거합니다. Globals 개체 및 사용 방법에 대한 자세한 정보는 [여기를 클릭](/help/forms/custom-function-core-component-create-function.md#field-and-global-scope-objects-support-in-custom-functions)하십시오.

매개 변수 형식은 대/소문자를 구분하지 않으며 매개 변수 이름에는 공백을 사용할 수 없습니다.

`<Parameter Description>`에 매개 변수의 용도에 대한 세부 정보가 포함되어 있습니다. 여러 단어가 있을 수 있습니다.

#### 옵션 매개 변수

기본적으로 모든 매개 변수는 필수입니다. 매개 변수 형식 뒤에 `=`을(를) 추가하거나 `[]`에서 매개 변수 이름을 둘러싸서 매개 변수를 선택 사항으로 정의할 수 있습니다. JavaScript 주석에서 선택 사항으로 정의된 매개 변수는 규칙 편집기에서 선택 사항으로 표시됩니다.
변수를 선택적 매개 변수로 정의하려면 다음 구문 중 하나를 사용할 수 있습니다.

* `@param {type=} Input1`

위의 코드 행에서 `Input1`은(는) 기본값이 없는 선택적 매개 변수입니다. 선택적 매개 변수를 기본값으로 선언하려면 다음을 수행합니다.
`@param {string=<value>} input1`

`input1`을(를) 선택적 매개 변수로 사용하고 기본값은 `value`(으)로 설정되어 있습니다.

* `@param {type} [Input1]`

위의 코드 행에서 `Input1`은(는) 기본값이 없는 선택적 매개 변수입니다. 선택적 매개 변수를 기본값으로 선언하려면 다음을 수행합니다.
`@param {array} [input1=<value>]`
`input1`은(는) 기본값이 `value`(으)로 설정된 배열 유형의 선택적 매개 변수입니다.
매개 변수 형식이 중괄호 {} 안에 있고 매개 변수 이름이 대괄호 안에 있는지 확인하십시오.

input2가 선택적 매개 변수로 정의된 다음 코드 스니펫을 고려하십시오.

```javascript
        /**
         * optional parameter function
         * @name OptionalParameterFunction
         * @param {string} input1 
         * @param {string=} input2 
         * @return {string}
        */
        function OptionalParameterFunction(input1, input2) {
        let result = "Result: ";
        result += input1;
        if (input2 !== null) {
            result += " " + input2;
        }
        return result;
        }
```

다음 그림은 규칙 편집기에서 `OptionalParameterFunction` 사용자 지정 함수를 사용하여 표시됩니다.

![선택적 매개 변수 또는 필수 매개 변수 ](/help/forms/assets/optional-default-params.png)

필요한 매개 변수에 대한 값을 지정하지 않고 규칙을 저장할 수 있지만, 규칙이 실행되지 않고 다음과 같은 경고 메시지가 표시됩니다.

![불완전한 규칙 경고](/help/forms/assets/incomplete-rule.png)

사용자가 선택적 매개 변수를 비워 두면 &quot;정의되지 않음&quot; 값이 선택적 매개 변수에 대한 사용자 지정 함수에 전달됩니다.

JSDocs에서 선택적 매개 변수를 정의하는 방법에 대해 자세히 알아보려면 [여기를 클릭](https://jsdoc.app/tags-param)하세요.

### 반환 유형

반환 형식은 사용자 지정 함수가 실행 후 반환하는 값의 형식을 지정합니다. 다음 구문을 사용하여 사용자 지정 함수에서 반환 유형을 정의합니다.

* `@return {type}`
* `@returns {type}`
  `{type}`은(는) 함수의 반환 형식을 나타냅니다. 허용되는 반환 유형은 다음과 같습니다.
   * string: 단일 문자열 값을 나타냅니다.
   * number: 단일 숫자 값을 나타냅니다.
   * 부울: 단일 부울 값(true 또는 false)을 나타냅니다.
   * string[]: 문자열 값의 배열을 나타냅니다.
   * number[]: 숫자 값의 배열을 나타냅니다.
   * boolean[]: 부울 값의 배열을 나타냅니다.
   * date: 단일 날짜 값을 나타냅니다.
   * date[]: 날짜 값의 배열을 나타냅니다.
   * array: 다양한 유형의 값을 포함하는 일반 배열을 나타냅니다.
   * object: 값 대신 양식 개체를 직접 나타냅니다.

  반환 형식은 대/소문자를 구분하지 않습니다.

### 비공개

private으로 선언된 사용자 지정 함수는 적응형 양식의 규칙 편집기에서 사용자 지정 함수 목록에 표시되지 않습니다. 기본적으로 사용자 지정 함수는 공개입니다. 사용자 지정 함수를 전용으로 선언하는 구문은 `@private`입니다.


## 사용자 정의 함수를 만드는 동안 지침

규칙 편집기에 사용자 정의 함수를 나열하려면 다음 형식 중 하나를 사용할 수 있습니다.

### jsdoc 주석이 있거나 없는 Function 문

jsdoc 주석을 사용하거나 사용하지 않고 사용자 지정 함수를 만들 수 있습니다.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
사용자가 사용자 지정 함수에 JavaScript 주석을 추가하지 않으면 함수 이름으로 규칙 편집기에 나열됩니다. 그러나 사용자 정의 함수의 가독성을 높이기 위해 JavaScript 주석을 포함하는 것이 좋습니다.

### 필수 JavaScript 주석 또는 댓글이 있는 화살표 기능

화살표 함수 구문을 사용하여 사용자 지정 함수를 만들 수 있습니다.

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} a parameter description
    * @param {string=} b parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
    /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;
    
```

사용자가 JavaScript 주석을 사용자 지정 함수에 추가하지 않으면 사용자 지정 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다.

### 필수 JavaScript 주석 또는 주석이 있는 함수 표현식

적응형 양식의 규칙 편집기에 사용자 정의 함수를 나열하려면 다음 형식으로 사용자 정의 함수를 만듭니다.

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} input1 parameter description
    * @param {string=} input2 parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

사용자가 JavaScript 주석을 사용자 지정 함수에 추가하지 않으면 사용자 지정 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다.

## 다음 단계

적응형 양식에서 사용자 지정 함수를 만들고 사용하려면 [핵심 구성 요소를 기반으로 적응형 양식에 대한 사용자 지정 함수 만들기](/help/forms/custom-function-core-component-create-function.md) 문서를 참조하십시오.

## 추가 참조

{{see-also-rule-editor}}