---
title: 적응형 양식에서 사용자 정의 함수 만들기 및 추가
description: AEM Forms은 사용자가 규칙 편집기 내에서 자체 함수를 만들고 사용할 수 있도록 하는 사용자 지정 함수를 지원합니다.
keywords: 사용자 지정 함수를 추가하고, 사용자 지정 함수를 사용하고, 사용자 지정 함수를 만들고, 규칙 편집기에서 사용자 지정 함수를 사용합니다.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
source-git-commit: b6061690fa278ccb883656cefd065d06ab924499
workflow-type: tm+mt
source-wordcount: '3521'
ht-degree: 3%

---


<span class="preview"> 이 문서에는 다음이 포함됩니다. `Override form submission success and error handlers` 를 프리릴리스 기능으로 사용하십시오. 프리릴리스 기능은 다음을 통해서만 액세스할 수 있습니다. [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features).

# 적응형 Forms(핵심 구성 요소)의 사용자 지정 기능

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | 이 문서 |

## 소개

AEM Forms은 사용자 정의 함수를 지원하므로 사용자가 복잡한 비즈니스 규칙을 구현하기 위한 JavaScript 함수를 정의할 수 있습니다. 이러한 사용자 지정 기능은 지정된 요구 사항을 충족하도록 입력된 데이터의 조작 및 처리를 용이하게 하여 양식의 기능을 확장합니다. 또한 사전 정의된 기준에 따라 양식 동작을 동적으로 변경할 수 있습니다.

>[!NOTE]
>
> 다음을 확인합니다. [핵심 구성 요소](https://github.com/adobe/aem-core-forms-components) 최신 기능을 사용하려면 를 최신 버전으로 설정하십시오.

### 사용자 정의 함수 사용 {#uses-of-custom-function}

적응형 Forms에서 사용자 정의 함수를 사용할 때의 장점은 다음과 같습니다.
* **데이터 처리**: 사용자 정의 기능은 양식 필드에 입력된 데이터를 처리하는 데 도움이 됩니다.
* **데이터 유효성 검사**: 사용자 정의 기능을 사용하면 양식 입력에 대한 사용자 정의 검사를 수행하고 지정된 오류 메시지를 제공할 수 있습니다.
* **동적 동작**: 사용자 정의 기능을 사용하면 특정 조건에 따라 양식의 동적 동작을 제어할 수 있습니다. 예를 들어 필드를 표시/숨기거나, 필드 값을 수정하거나, 양식 논리를 동적으로 조정할 수 있습니다.
* **통합**: 사용자 지정 함수를 사용하여 외부 API 또는 서비스와 통합할 수 있습니다. 외부 소스에서 데이터를 가져오거나 외부 Rest 끝점으로 데이터를 전송하거나 외부 이벤트를 기반으로 사용자 지정 작업을 수행하는 데 도움이 됩니다.

사용자 지정 함수는 기본적으로 JavaScript 파일에 추가되는 클라이언트 라이브러리입니다. 사용자 지정 함수를 만들면 규칙 편집기에서 적응형 양식에서 사용자가 선택할 수 있게 됩니다. 사용자 지정 함수는 규칙 편집기의 JavaScript 주석으로 식별됩니다.

### 사용자 지정 함수에 대해 지원되는 JavaScript 주석 {#js-annotations}

JavaScript 주석은 JavaScript 코드에 대한 메타데이터를 제공하는 데 사용됩니다. 여기에는 /** 및 @과 같은 특정 기호로 시작하는 주석이 포함됩니다. 주석은 함수, 변수 및 코드의 기타 요소에 대한 중요한 정보를 제공합니다. 적응형 양식은 사용자 정의 기능에 대한 다음 JavaScript 주석을 지원합니다.

#### 이름

이 이름은 적응형 양식의 규칙 편집기에서 사용자 지정 기능을 식별하는 데 사용됩니다. 다음 구문을 사용하여 사용자 지정 함수의 이름을 지정합니다.

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`
  `functionName` 는 함수의 이름입니다. 공백은 허용되지 않습니다.
  `<Function Name>` 는 적응형 양식의 규칙 편집기에 있는 함수의 표시 이름입니다.
함수 이름이 함수 자체의 이름과 동일한 경우 를 생략할 수 있습니다 `[functionName]` 구문을 통해 알 수 있습니다.

#### 매개변수

매개 변수는 사용자 지정 함수에서 사용하는 인수 목록입니다. 함수는 여러 매개 변수를 지원할 수 있습니다. 다음 구문을 사용하여 사용자 지정 함수에서 매개 변수를 정의할 수 있습니다.

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`.
  `{type}` 매개 변수 유형을 나타냅니다.  허용되는 매개 변수 유형은 다음과 같습니다.

   * string: 단일 문자열 값을 나타냅니다.
   * number: 단일 숫자 값을 나타냅니다.
   * 부울: 단일 부울 값(true 또는 false)을 나타냅니다.
   * 문자열[]: 문자열 값의 배열을 나타냅니다.
   * 숫자[]: 숫자 값의 배열을 나타냅니다.
   * 부울[]: 부울 값의 배열을 나타냅니다.
   * date: 단일 날짜 값을 나타냅니다.
   * 날짜[]: 날짜 값의 배열을 나타냅니다.
   * array: 다양한 유형의 값을 포함하는 일반 배열을 나타냅니다.
   * object: 값을 직접 전달하는 대신 사용자 지정 함수에 전달되는 양식 개체를 나타냅니다.
   * 범위: 사용자 지정 함수 내에서 양식을 수정하는 방법, 양식 인스턴스, 대상 필드 인스턴스와 같은 읽기 전용 변수를 포함하는 globals 개체를 나타냅니다. 이 매개 변수는 JavaScript 주석에서 마지막 매개 변수로 선언되며 적응형 양식의 규칙 편집기에 표시되지 않습니다. 범위 매개 변수는 양식 또는 구성 요소의 개체에 액세스하여 양식 처리에 필요한 규칙이나 이벤트를 트리거합니다. Globals 개체 및 사용 방법에 대한 자세한 내용은 [여기를 클릭하십시오](/help/forms/create-and-use-custom-functions.md#support-field-and-global-objects).

매개 변수 형식은 대/소문자를 구분하지 않으며 매개 변수 이름에는 공백을 사용할 수 없습니다.

`<Parameter Description>` 에는 매개 변수의 용도에 대한 세부 사항이 포함되어 있습니다. 여러 단어가 있을 수 있습니다.

**선택적 매개 변수**
기본적으로 모든 매개 변수는 필수입니다. 다음을 추가하여 매개 변수를 선택 사항으로 정의할 수 있습니다 `=` 매개 변수 형식 뒤에 또는 매개 변수 이름을 바깥쪽으로  `[]`. JavaScript 주석에서 선택 사항으로 정의된 매개 변수는 규칙 편집기에서 선택 사항으로 표시됩니다.
변수를 선택적 매개 변수로 정의하려면 다음 구문 중 하나를 사용할 수 있습니다.

* `@param {type=} Input1`

위의 코드 행에서 `Input1` 는 기본값이 없는 선택적 매개 변수입니다. 선택적 매개 변수를 기본값으로 선언하려면 다음을 수행합니다.
`@param {string=<value>} input1`

`input1` 기본값이 로 설정된 선택적 매개 변수로 `value`.

* `@param {type} [Input1]`

위의 코드 행에서 `Input1` 는 기본값이 없는 선택적 매개 변수입니다. 선택적 매개 변수를 기본값으로 선언하려면 다음을 수행합니다.
`@param {array} [input1=<value>]`
`input1` 는 기본값이 로 설정된 배열 유형의 선택적 매개 변수입니다. `value`.
매개 변수 형식이 중괄호로 묶여 있는지 확인합니다. {} 매개 변수 이름은 대괄호로 묶습니다 [].

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

다음 그림은 를 사용하여 표시됩니다. `OptionalParameterFunction` 규칙 편집기의 사용자 지정 함수:

![선택적 또는 필수 매개 변수 ](/help/forms/assets/optional-default-params.png)

필요한 매개 변수에 대한 값을 지정하지 않고 규칙을 저장할 수 있지만, 규칙이 실행되지 않고 다음과 같은 경고 메시지가 표시됩니다.

![불완전한 규칙 경고](/help/forms/assets/incomplete-rule.png)

사용자가 선택적 매개 변수를 비워 두면 &quot;정의되지 않음&quot; 값이 선택적 매개 변수에 대한 사용자 지정 함수에 전달됩니다.

JSDocs에서 선택적 매개 변수를 정의하는 방법에 대해 자세히 알아보려면 [여기를 클릭하십시오](https://jsdoc.app/tags-param).

#### 반환 유형

반환 형식은 사용자 지정 함수가 실행 후 반환하는 값의 형식을 지정합니다. 다음 구문을 사용하여 사용자 지정 함수에서 반환 유형을 정의합니다.

* `@return {type}`
* `@returns {type}`
  `{type}` 함수의 반환 형식을 나타냅니다. 허용되는 반환 유형은 다음과 같습니다.
   * string: 단일 문자열 값을 나타냅니다.
   * number: 단일 숫자 값을 나타냅니다.
   * 부울: 단일 부울 값(true 또는 false)을 나타냅니다.
   * 문자열[]: 문자열 값의 배열을 나타냅니다.
   * 숫자[]: 숫자 값의 배열을 나타냅니다.
   * 부울[]: 부울 값의 배열을 나타냅니다.
   * date: 단일 날짜 값을 나타냅니다.
   * 날짜[]: 날짜 값의 배열을 나타냅니다.
   * array: 다양한 유형의 값을 포함하는 일반 배열을 나타냅니다.
   * object: 값 대신 양식 개체를 직접 나타냅니다.

  반환 형식은 대/소문자를 구분하지 않습니다.

#### 비공개

private으로 선언된 사용자 지정 함수는 적응형 양식의 규칙 편집기에서 사용자 지정 함수 목록에 표시되지 않습니다. 기본적으로 사용자 지정 함수는 공개입니다. 사용자 지정 함수를 private으로 선언하는 구문은 다음과 같습니다. `@private`.


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
사용자가 사용자 정의 함수에 JavaScript 주석을 추가하지 않으면 함수 이름으로 규칙 편집기에 나열됩니다. 그러나 사용자 정의 함수의 가독성을 높이기 위해 JavaScript 주석을 포함하는 것이 좋습니다.

### 필수 JavaScript 주석 또는 주석이 있는 화살표 함수

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

사용자가 사용자 정의 함수에 JavaScript 주석을 추가하지 않으면 사용자 정의 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다.

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

사용자가 사용자 정의 함수에 JavaScript 주석을 추가하지 않으면 사용자 정의 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다.

## 사용자 정의 함수 만들기 {#create-custom-function}

규칙 편집기에서 사용자 지정 함수를 호출할 클라이언트 라이브러리를 만듭니다. 자세한 내용은 [클라이언트측 라이브러리 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).

사용자 정의 함수를 만드는 단계는 다음과 같습니다.
1. [클라이언트 라이브러리 만들기](#create-client-library)
1. [적응형 양식에 클라이언트 라이브러리 추가](#use-custom-function)

### 클라이언트 라이브러리 만들기 {#create-client-library}

클라이언트 라이브러리를 추가하여 사용자 정의 함수를 추가할 수 있습니다. 클라이언트 라이브러리를 만들려면 다음 단계를 수행하십시오.

1. [AEM Forms as a Cloud Service 저장소 복제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#accessing-git).
1. `[AEM Forms as a Cloud Service repository folder]/apps/` 폴더 아래에 폴더를 만듭니다. 예를 들어 이라는 폴더를 만듭니다. `experience-league`.
1. 다음으로 이동 `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` 및 만들기 `ClientLibraryFolder`. 예를 들어 클라이언트 라이브러리 폴더를 다음과 같이 만듭니다. `customclientlibs`.
1. 속성 추가 `categories` 문자열 유형 값 포함. 예를 들어 값을 할당합니다 `customfunctionscategory` (으)로 `categories` 속성 `customclientlibs` 폴더를 삭제합니다.

   >[!NOTE]
   >
   > 다음에 대한 모든 이름을 선택할 수 있습니다. `client library folder` 및 `categories` 속성.

1. `js`라는 이름의 폴더를 만듭니다.
1. `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js` 폴더로 이동합니다.
1. JavaScript 파일 추가(예: ) `function.js`. 이 파일은 사용자 지정 함수에 대한 코드로 구성됩니다.
1. `function.js` 파일을 저장합니다.
1. `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js` 폴더로 이동합니다.
1. `js.txt`로 텍스트 파일을 추가합니다. 파일에는 다음이 포함됩니다.

   ```javascript
       #base=js
       functions.js
   ```

1. `js.txt` 파일을 저장합니다.
1. 아래 명령을 사용하여 저장소의 변경 내용을 추가하고, 커밋하고, 푸시합니다.

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. [파이프라인 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline) 사용자 지정 함수를 배포합니다.

파이프라인이 성공적으로 실행되면 클라이언트 라이브러리에 추가된 사용자 지정 함수를에서 사용할 수 있게 됩니다 [적응형 양식 규칙 편집기](/help/forms/rule-editor-core-components.md).

### 적응형 양식에 클라이언트 라이브러리 추가{#use-custom-function}

클라이언트 라이브러리를 Forms CS 환경에 배포한 후에는 적응형 양식에서 해당 기능을 사용하십시오. 적응형 양식에 클라이언트 라이브러리를 추가하려면

1. 편집 모드에서 양식을 엽니다. 편집 모드에서 양식을 열려면 양식을 선택하고 을 선택합니다 **[!UICONTROL 편집]**.
1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. 를 엽니다. **[!UICONTROL 기본]** 탭을 클릭하고 이름 선택 **[!UICONTROL 클라이언트 라이브러리 범주]** 드롭다운 목록에서(이 경우 `customfunctionscategory`).

   ![사용자 정의 함수 클라이언트 라이브러리 추가](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > 내에서 쉼표로 구분된 목록을 지정하여 여러 범주를 추가할 수 있습니다. **[!UICONTROL 클라이언트 라이브러리 범주]** 필드.

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

에서 사용자 지정 함수를 사용할 수 있습니다. [적응형 양식의 규칙 편집기](/help/forms/rule-editor-core-components.md) 사용 [JavaScript 주석](##js-annotations).

## 적응형 양식에서 사용자 정의 함수 사용

적응형 양식에서 다음을 사용할 수 있습니다 [규칙 편집기 내의 사용자 지정 함수](/help/forms/rule-editor-core-components.md). JavaScript 파일에 다음 코드를 추가하겠습니다(`Function.js` file)을 추가하여 생년월일(YYYY-MM-DD)을 기준으로 연령을 계산합니다. 사용자 정의 함수 만들기 `calculateAge()` 입력 시 생년월일을 사용하고 연령을 반환합니다.

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

위의 예에서 사용자가 생년월일을 형식(YYYY-MM-DD)으로 입력하면 사용자 지정 함수가 `calculateAge` 가 호출되고 월령을 반환합니다.

![규칙 편집기의 Agae 사용자 지정 함수 계산](/help/forms/assets/custom-function-calculate-age.png)

이제 양식을 미리 보기하여 사용자 정의 함수가 규칙 편집기를 통해 어떻게 구현되는지 살펴보겠습니다.

![규칙 편집기 양식 미리 보기에서 Agae 사용자 정의 함수 계산](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> 다음을 참조하십시오 [사용자 정의 함수](/help/forms/assets//customfunctions.zip) 폴더를 삭제합니다. 를 사용하여 AEM 인스턴스에 이 폴더를 다운로드하고 설치합니다. [패키지 관리자](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).


### 사용자 정의 함수를 사용하여 드롭다운 목록 옵션 설정

핵심 구성 요소의 규칙 편집기는 **옵션 설정** 속성을 사용하여 런타임 시 드롭다운 목록 옵션을 설정할 수 있습니다. 그러나 사용자 지정 함수를 사용하여 드롭다운 목록 옵션을 설정할 수 있습니다.

사용자 지정 함수를 사용하여 드롭다운 목록 옵션을 설정하는 방법을 보려면 아래 코드를 살펴보십시오.

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

위의 코드에서 `setEnums` 를 설정하는 데 사용됩니다. `enum` 속성 및 `setEnumNames` 를 설정하는 데 사용됩니다. `enumNames` 드롭다운 속성.

다음에 대한 규칙을 만들겠습니다. `Next` 버튼 - 사용자가 를 클릭할 때 드롭다운 목록 옵션의 값을 설정합니다. `Next` 단추:

![드롭다운 목록 옵션](/help/forms/assets/drop-down-list-options.png)

표시 버튼을 클릭할 때 드롭다운 목록의 옵션이 설정되는 위치를 보여 주려면 아래 그림을 참조하십시오.

![규칙 편집기의 드롭다운 옵션](/help/forms/assets/drop-down-option-rule-editor.png)



### 사용자 지정 함수에서 비동기 함수 지원 {#support-of-async-functions}

비동기 사용자 지정 함수는 규칙 편집기 목록에 표시되지 않습니다. 그러나 동기 함수 표현식을 사용하여 만든 사용자 지정 함수 내에서 비동기 함수를 호출할 수 있습니다.

![동기화 및 비동기 사용자 지정 기능](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

>[!NOTE]
>
> 사용자 지정 함수에서 비동기 함수를 호출하는 경우 비동기 함수를 사용하면 사용자 지정 함수 내에서 각 함수가 사용된 결과를 사용하여 여러 작업을 동시에 실행할 수 있다는 이점이 있습니다.

사용자 지정 함수를 사용하여 비동기 함수를 호출하는 방법은 아래 코드를 참조하십시오.

```javascript
    
    async function asyncFunction() {
    const response = await fetch('https://petstore.swagger.io/v2/store/inventory');
    const data = await response.json();
    return data;
    }

    /**
    * callAsyncFunction
    * @name callAsyncFunction callAsyncFunction
    */
    function callAsyncFunction() {
    asyncFunction()
        .then(responseData => {
        console.log('Response data:', responseData);
        })
        .catch(error => {
         console.error('Error:', error);
    });
}
```

위의 예에서 asyncFunction 함수는 `asynchronous function`. 비동기 작업은 다음을 만들어 수행합니다. `GET` 요청 대상 `https://petstore.swagger.io/v2/store/inventory`. 다음을 사용하여 응답을 기다립니다. `await`는 다음을 사용하여 응답 본문을 JSON으로 구문 분석합니다. `response.json()`를 클릭한 다음 데이터를 반환합니다. 다음 `callAsyncFunction` 함수는 를 호출하는 동기 사용자 지정 함수입니다. `asyncFunction` 콘솔에서 응답 데이터를 표시합니다. 하지만 `callAsyncFunction` 이 함수는 synchronous이고, 비동기 asyncFunction 함수를 호출하고, 결과를 `then` 및 `catch` 명령문입니다.

작동 여부를 확인하려면 단추를 추가하고 단추 클릭 시 비동기 함수를 호출하는 단추에 대한 규칙을 만들어 보겠습니다.

![비동기 함수에 대한 규칙 만들기](/help/forms/assets/rule-for-async-funct.png)

사용자가 를 클릭할 때 표시되는 콘솔 창의 그림을 참조하십시오. `Fetch` 단추, 사용자 지정 함수 `callAsyncFunction` 가 호출되어 비동기 함수를 호출합니다. `asyncFunction`. Inspect 콘솔 창에서 버튼에 대한 응답을 봅니다. 클릭:

![콘솔 창](/help/forms/assets/async-custom-funct-console.png)

사용자 정의 함수의 기능에 대해 자세히 살펴보겠습니다.

## 사용자 정의 기능을 위한 다양한 기능

사용자 지정 함수를 사용하여 양식에 개인화된 기능을 추가할 수 있습니다. 이러한 기능은 특정 필드 작업, 전역 필드 사용 또는 캐싱과 같은 다양한 기능을 지원합니다. 이러한 유연성을 통해 조직의 요구 사항에 따라 양식을 사용자 정의할 수 있습니다.

### 사용자 지정 함수의 필드 및 전역 범위 개체 {#support-field-and-global-objects}

필드 개체는 텍스트 필드, 확인란 등 양식 내의 개별 구성 요소 또는 요소를 나타냅니다. Globals 개체에는 사용자 지정 함수 내에서 양식을 수정하는 방법, 대상 필드 인스턴스 및 양식 인스턴스와 같은 읽기 전용 변수가 포함되어 있습니다.

>[!NOTE]
>
> 다음 `param {scope} globals` 은 마지막 매개 변수여야 하며 적응형 양식의 규칙 편집기에 표시되지 않습니다.

<!-- Let us look at the following code snippet:

```JavaScript
   
    /**
    * updateDateTime
    * @name updateDateTime
    * @param {object} field
    * @param {scope} globals
    */
    function updateDateTime(field, globals) {
    // Accessing the Date object from the global scope
    var currentDate = new Date();
    // Formatting the date and time
    var formattedDateTime = currentDate.toLocaleString();
    // Updating the field value with the formatted date and time using setProperty.
    globals.functions.setProperty(field, {value: formattedDateTime});
    }
```

In the above code snippet, a custom function named `updateDateTime` takes parameters such as a field object and a global object. The field represents the textbox object where the formatted date and time value is displayed within the form. -->

사용자 지정 함수에서 필드를 사용하고 전역 개체를 사용하는 방법에 대해 알아보겠습니다. `Contact Us` 다양한 사용 사례를 사용하는 양식입니다.

![연락처 양식](/help/forms/assets/contact-us-form.png)

+++ 사용 사례: `SetProperty` 규칙

에 설명된 대로 사용자 지정 함수에 다음 코드를 추가합니다. [create-custom-function](#create-custom-function) 섹션, 양식 필드를 다음으로 설정 `Required`.

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
> * 에 있는 사용 가능한 속성을 사용하여 필드 속성을 구성할 수 있습니다. `[form-path]/jcr:content/guideContainer.model.json`.
> * 을 사용하여 양식에 수정한 사항 `setProperty` Globals 개체의 메서드는 기본적으로 비동기이며 사용자 지정 함수를 실행하는 동안에는 반영되지 않습니다.

이 예에서 의 유효성 검사 `personaldetails` 단추를 클릭하면 패널이 표시됩니다. 패널에서 오류가 감지되지 않으면 다른 패널에서 `feedback` 단추 클릭 시 패널이 표시됩니다.

다음에 대한 규칙을 만들겠습니다. `Next` 단추, 유효성 검사 `personaldetails` 패널 및 만들기 `feedback`  사용자가 패널을 클릭하면 표시되는 `Next` 단추를 클릭합니다.

![속성 설정](/help/forms/assets/custom-function-set-property.png)

다음 그림을 참조하여 의 위치를 확인하십시오. `personaldetails` 패널을 클릭하면 유효성이 검사됩니다. `Next` 단추를 클릭합니다. 대소문자 구분 안 함 내의 모든 필드 `personaldetails` 유효성 검사됨, `feedback` 패널이 표시됩니다.

![속성 양식 미리 보기 설정](/help/forms/assets/set-property-form-preview.png)

의 필드에 오류가 있는 경우 `personaldetails` 패널 - 다음을 클릭하면 필드 수준에서 표시됩니다. `Next` 단추 및 `feedback` 패널은 계속 표시되지 않습니다.

![속성 양식 미리 보기 설정](/help/forms/assets/set-property-panel.png)


#### 사용 사례: 필드의 유효성 검사

에 설명된 대로 사용자 지정 함수에 다음 코드를 추가합니다. [create-custom-function](#create-custom-function) 섹션의 유효성 검사를 참조하십시오.

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
> 에 인수가 전달되지 않으면 `validate()` 함수, 양식의 유효성을 검사합니다.

이 예에서는 사용자 정의 유효성 검사 패턴이 `contact` 필드. 사용자는 다음으로 시작하는 전화 번호를 입력해야 합니다. `10` 뒤에 오는 `8` 숫자. 사용자가 다음으로 시작하지 않는 전화 번호를 입력하는 경우 `10` 또는 보다 많거나 적은 포함 `8` 숫자로 표시된 경우 단추를 클릭하면 유효성 검사 오류 메시지가 나타납니다.

![이메일 주소 유효성 검사 패턴](/help/forms/assets/custom-function-validation-pattern.png)

이제 다음 단계에서는 다음에 대한 규칙을 만듭니다. `Next` 의 유효성을 검사하는 버튼 `contact` 단추 클릭 시 필드.

![유효성 검사 패턴](/help/forms/assets/custom-function-validate.png)

사용자가 다음으로 시작하지 않는 전화 번호를 입력하는 경우 아래 그림을 참조하십시오. `10`필드 수준에 다음과 같은 오류 메시지가 나타납니다.

![이메일 주소 유효성 검사 패턴](/help/forms/assets/custom-function-validate-error-message.png)

사용자가 유효한 전화 번호와 `personaldetails` 패널의 유효성이 검사됩니다. `feedback` 패널이 화면에 표시됩니다.

![이메일 주소 유효성 검사 패턴](/help/forms/assets/validate-form-preview-form.png)



#### 사용 사례: 패널 재설정

에 설명된 대로 사용자 지정 함수에 다음 코드를 추가합니다. [create-custom-function](#create-custom-function) 섹션, 패널을 재설정합니다.

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
> 에 인수가 전달되지 않으면 `reset()` 함수, 양식의 유효성을 검사합니다.

이 예에서는 `personaldetails` 패널을 클릭하면 재설정됩니다. `Clear` 단추를 클릭합니다. 다음 단계는 다음에 대한 규칙을 만드는 것입니다. `Clear` 단추를 클릭하면 패널이 재설정됩니다.

![지우기 단추](/help/forms/assets/custom-function-reset-field.png)

사용자가 를 클릭할 경우 이를 표시하려면 아래 그림을 참조하십시오. `clear` 단추, `personaldetails` 패널 재설정:

![양식 재설정](/help/forms/assets/custom-function-reset-form.png)



#### 사용 사례: 필드 수준에서 사용자 정의 메시지를 표시하고 필드를 유효하지 않은 것으로 표시

다음을 사용할 수 있습니다. `markFieldAsInvalid()` 필드를 유효하지 않은 것으로 정의하고 필드 수준에서 사용자 지정 오류 메시지를 설정하는 함수입니다. 다음 `fieldIdentifier` 값은 다음과 같을 수 있습니다. `fieldId`, 또는 `field qualifiedName`, 또는 `field dataRef`. 이름이 인 개체의 값 `option` 다음이 될 수 있음: `{useId: true}`, `{useQualifiedName: true}`, 또는 `{useDataRef: true}`.
필드를 유효하지 않은 것으로 표시하고 사용자 정의 메시지를 설정하는 데 사용되는 구문은 다음과 같습니다.

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

에 설명된 대로 사용자 지정 함수에 다음 코드를 추가합니다. [create-custom-function](#create-custom-function) 섹션에 있는 마지막 항목이 될 필요가 없습니다.

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

다음 단계는 다음에 대한 규칙을 만드는 것입니다. `comments` 필드:

![필드를 유효하지 않은 것으로 표시](/help/forms/assets/custom-function-invalid-field.png)

에 부정적인 피드백을 입력했음을 표시하려면 아래 데모를 참조하십시오. `comments` 필드는 필드 수준에서 사용자 지정 메시지 표시를 트리거합니다.

![필드를 잘못된 미리보기 양식으로 표시](/help/forms/assets/custom-function-invalidfield-form.png)

사용자가 주석 입력란에 15자 이상을 입력하면 필드의 유효성이 검사되고 양식이 제출됩니다.

![필드를 유효한 미리 보기 양식으로 표시](/help/forms/assets/custom-function-validfield-form.png)



#### 사용 사례: 변경된 데이터를 서버에 제출

다음 코드 줄:
`globals.functions.submitForm(globals.functions.exportData(), false);` 은 조작 후 양식 데이터를 제출하는 데 사용됩니다.
* 첫 번째 인수는 제출할 데이터입니다.
* 두 번째 인수는 제출 전에 양식의 유효성을 검사할지 여부를 나타냅니다. 다음과 같습니다. `optional` 및 로 설정 `true` 기본적으로.
* 세 번째 인수는 `contentType` 제출 서류 - 기본값과 함께 선택 사항입니다. `multipart/form-data`. 다른 값은 다음과 같습니다. `application/json` 및 `application/x-www-form-urlencoded`.

에 설명된 대로 사용자 지정 함수에 다음 코드를 추가합니다. [create-custom-function](#create-custom-function) 섹션에서 조작된 데이터를 서버에 제출하려면 다음을 수행합니다.

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

이 예에서 사용자가 `comments` 텍스트 상자가 비어 있음, `NA` 양식 제출 시 서버에 제출됩니다.

이제 다음에 대한 규칙을 만듭니다. `Submit` 데이터를 전송하는 단추:

![데이터 제출](/help/forms/assets/custom-function-submit-data.png)

의 그림을 참조하십시오 `console window` 사용자가 `comments` textbox가 비어 있는 경우 값이 `NA` 은(는) 서버에서 제출됩니다.

![콘솔 창에서 데이터 제출](/help/forms/assets/custom-function-submit-data-form.png)

또한 콘솔 창을 검사하여 서버에 제출된 데이터를 볼 수도 있습니다.

![콘솔 창의 Inspect 데이터](/help/forms/assets/custom-function-submit-data-console-data.png)



#### 사용 사례: 양식 제출 성공 및 오류 처리기 재정의

에 설명된 대로 다음 코드 행을 추가합니다. [create-custom-function](#create-custom-function) 섹션에서 양식 제출을 위해 제출 또는 실패 메시지를 사용자 정의하고 양식 제출 메시지를 모달 상자에 표시하려면 다음을 수행합니다.

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

이 예에서 사용자가 `customSubmitSuccessHandler` 및 `customSubmitErrorHandler` 사용자 정의 함수, 성공 및 실패 메시지는 모달에 표시됩니다. JavaScript 함수 `showModal(type, message)` 를 사용하여 모달 대화 상자를 동적으로 만들고 화면에 표시합니다.

이제 성공적인 양식 제출을 위한 규칙을 만듭니다.

![양식 제출 성공](/help/forms/assets/form-submission-success.png)

양식이 성공적으로 제출되면 성공 메시지가 모달에 표시된다는 것을 증명하려면 아래 그림을 참조하십시오.

![양식 제출 성공 메시지](/help/forms/assets/form-submission-success-message.png)

마찬가지로 실패한 양식 제출에 대한 규칙을 만들어 보겠습니다.

![양식 제출 실패](/help/forms/assets/form-submission-fail.png)

양식 제출이 실패할 때 오류 메시지가 모달에 표시되는지 보여 주려면 아래 그림을 참조하십시오.

![양식 제출 실패 메시지](/help/forms/assets/form-submission-fail-message.png)

기본 방식으로 양식 제출 성공 및 실패를 표시하려면 `Default submit Form Success Handler` 및 `Default submit Form Error Handler` 함수는 즉시 사용할 수 있습니다.

사용자 지정 제출 처리기가 기존 AEM 프로젝트 또는 양식에서 예상대로 수행되지 않는 경우 [문제 해결](#troubleshooting) 섹션.

<!--


#### Use Case:  Perform actions in a specific instance of the repeatable panel 

Rules created using the visual rule editor on a repeatable panel apply to the last instance of the repeatable panel. To write a rule for a specific instance of the repeatable panel, we can use a custom function.

Let's create a form to collect information about travelers heading to a destination. A traveler panel is added as a repeatable panel, where the user can add details for 5 travelers using the Add button.

Add the following line of code as explained in the [create-custom-function](#create-custom-function) section, to perform actions in a specific instance of the repeatable panel, other than the last one:

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
 
In this example, the `hidePanelInRepeatablePanel` custom function performs action in a specific instance of the repeatable panel. In the above code, `travelerinfo` represents the repeatable panel. The `repeatablePanel[1].traveler, {visible: false}` code hides the panel in the second instance of the repeatable panel. 
Let us add a button labeled `Hide` to add a rule to hide a specific panel.

![Hide Panel rule](/help/forms/assets/custom-function-hidepanel-rule.png)

Refer to the video below to demonstrate that when the `Hide` is clicked, the panel in the second repeatable instance hides:




#### **Usecase**: Pre-fill the field with a value when the form loads

Add the following line of code, as explained in the [create-custom-function](#create-custom-function) section, to load the pre-filled value in a field when the form is initialized:

```javascript
/**
 * @name importData
 * @param {scope} globals
 */
function importData(globals)
{
    globals.functions.importData(Object.fromEntries([['amount',200000]]));
} 
```

In the aforementioned code, the `importData` function updates the value in the `amount` textbox field when the form loads.

Let us create a rule for the `Submit` button, where the value in the `amount` textbox field changes to specified value when the form loads:

![Import Data Rule](/help/forms/assets/custom-function-import-data.png)

Refer to the screenshot below, which demonstrates that when the form loads, the value in the amount textbox is pre-filled with a specified value:

![Import Data Rule](/help/forms/assets/cg)



#### **Usecase**: Set focus on the specific field

Add the following line of code, as explained in the [create-custom-function](#create-custom-function) section, to set focus on the specified field when the `Submit` button is clicked.:

```javascript
/**
 * @name setFocus
 * @param {object} field
 * @param {scope} globals
 */
function setFocus(field, globals)
{
    globals.functions.setFocus(field);
}
```

Let us add a rule to the `Submit` button to set focus on the `email` field when it is clicked:

![Set Focus Rule](/help/forms/assets/custom-function-set-focus.png)

Refer to the screenshot below, which demonstrates that when the `Submit` button is clicked, the focus is set on the `email` field:

![Set Focus Rule](/help/forms/assets/custom-function-set-focus-form.png)

>[!NOTE]
>
> You can use the optional `$focusOption` parameter, if you want to focus on the next or previous field relative to the `email` field.

+++

+++ **Usecase**: Add or delete repeatable panel using the `dispatchEvent` property

Add the following line of code, as explained in the [create-custom-function](#create-custom-function) section, to add a panel when the `Add Traveler` button is clicked using the `dispatchEvent` property:

```javascript
/**
 
 * @name addInstance
 * @param {scope} globals
 */
function addInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel, 'addInstance');
} 

```

Let us add a rule to the `Add Traveler` button to add the repeatable panel when it is clicked:

![Add Panel Rule](/help/forms/assets/custom-function-add-panel.png)

Refer to the screenshot below, which demonstrates that when the `Add Traveler` button is clicked, the traveler panel is added using the `dispatchEvent` property:

![Add Panel](/help/forms/assets/customg)

Similarly, add a button labeled `Delete Traveler` to delete a panel. Add the following line of code, as explained in the [create-custom-function](#create-custom-function) section, to delete a panel when the `Delete Traveler` button is clicked using the `dispatchEvent` property:

```javascript

/**
 
 * @name removeInstance
 * @param {scope} globals
 */
function removeInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel, 'removeInstance');
} 

```
Let us add a rule to the `Delete Traveler` button to delete the repeatable panel when it is clicked:

![Delete Panel Rule](/help/forms/assets/custom-function-delete-panel.png)

Refer to the screenshot below, which demonstrates that when the `Delete Traveler` button is clicked, the traveler panel is deleted using the `dispatchEvent` property:

![Delete Panel](/help/forms/assets/customg)
-->

## 사용자 지정 기능에 대한 캐싱 지원

적응형 Forms은 규칙 편집기에서 사용자 지정 함수 목록을 검색하는 동안 응답 시간을 개선하기 위해 사용자 지정 함수에 대한 캐싱을 구현합니다. 다음으로 메시지: `Fetched following custom functions list from cache` 에 표시 `error.log` 파일.

![캐시 지원을 통한 사용자 정의 기능](/help/forms/assets/custom-function-cache-error.png)

사용자 지정 함수가 수정되면 캐싱이 무효화되고 구문 분석됩니다.

## 문제 해결 {#troubleshooting}

* 사용자 지정 제출 처리기가 기존 AEM 프로젝트 또는 양식에서 예상대로 수행되지 않으면 다음 단계를 수행하십시오.
   * 다음을 확인합니다. [코어 구성 요소 버전이 3.0.18 이상으로 업데이트되었습니다.](https://github.com/adobe/aem-core-forms-components). 그러나 기존 AEM 프로젝트 및 양식의 경우 따라야 할 추가 단계가 있습니다.

   * AEM 프로젝트의 경우 사용자는 의 모든 인스턴스를 `submitForm('custom:submitSuccess', 'custom:submitError')` 포함 `submitForm()` Cloud Manager 파이프라인을 통해 프로젝트를 배포할 수 있습니다.

   * 기존 양식의 경우 사용자 정의 제출 핸들러가 제대로 작동하지 않으면 를 열고 저장해야 합니다 `submitForm` 에 대한 규칙 **제출** 규칙 편집기를 사용하는 단추입니다. 이 작업은 의 기존 규칙을 대체합니다. `submitForm('custom:submitSuccess', 'custom:submitError')` 포함 `submitForm()` 폼에서.


* 사용자 지정 함수에 대한 코드가 포함된 JavaScript 파일에 오류가 있는 경우 사용자 지정 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다. 사용자 지정 함수 목록을 확인하려면 `error.log` 파일에 오류가 표시됩니다. 오류가 발생하면 사용자 지정 함수 목록이 비어 있습니다.

  ![오류 로그 파일](/help/forms/assets/custom-function-list-error-file.png)

  오류가 없는 경우 사용자 지정 함수를 가져와서 `error.log` 파일. 다음으로 메시지: `Fetched following custom functions list` 에 표시 `error.log` 파일:

  ![적절한 사용자 정의 기능이 있는 오류 로그 파일](/help/forms/assets/custom-function-list-fetched-in-error.png)

## 고려 사항

* 다음 `parameter type` 및 `return type` 지원 안 함 `None`.

* 사용자 지정 함수 목록에서 지원되지 않는 함수는 다음과 같습니다.
   * 생성기 함수
   * 비동기/대기 함수
   * 메서드 정의
   * 클래스 메서드
   * 기본 매개 변수
   * 나머지 매개 변수

## 추가 참조 {#see-also}

{{see-also}}


