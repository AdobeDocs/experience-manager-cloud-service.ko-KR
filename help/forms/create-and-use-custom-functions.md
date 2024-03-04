---
title: 적응형 양식에서 사용자 정의 함수 만들기 및 추가
description: AEM Forms은 사용자가 규칙 편집기 내에서 자체 함수를 만들고 사용할 수 있도록 하는 사용자 지정 함수를 지원합니다.
keywords: 사용자 지정 함수를 추가하고, 사용자 지정 함수를 사용하고, 사용자 지정 함수를 만들고, 규칙 편집기에서 사용자 지정 함수를 사용합니다.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
source-git-commit: 46fbed98a806f62dd1882eb0085d4338c5cd51a7
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 8%

---


# 적응형 Forms(핵심 구성 요소)의 사용자 지정 기능

## 소개

AEM Forms은 사용자 정의 함수를 지원하므로 사용자가 복잡한 비즈니스 규칙을 구현하기 위한 JavaScript 함수를 정의할 수 있습니다. 이러한 사용자 지정 기능은 지정된 요구 사항을 충족하도록 입력된 데이터의 조작 및 처리를 용이하게 하여 양식의 기능을 확장합니다. 또한 사전 정의된 기준에 따라 양식 동작을 동적으로 변경할 수 있습니다.
적응형 Forms에서는 [적응형 양식의 규칙 편집기](/help/forms/rule-editor-core-components.md) 을 입력하여 양식 필드에 대한 특정 유효성 검사 규칙을 만듭니다.

사용자가 이메일 주소를 입력하는 사용자 정의 함수의 사용을 이해하고 입력된 이메일 주소가 특정 형식(&quot;@&quot; 기호 및 도메인 이름 포함)을 따르는지 확인하겠습니다. 이메일 주소를 입력으로 사용하고 유효한 경우 true를 반환하고 그렇지 않은 경우 false를 반환하는 사용자 지정 함수를 &quot;ValidateEmail&quot;로 만듭니다.

```javascript
function ValidateEmail(inputText)
{
    var email = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
    if(inputText.value.match(email))
        {
            alert("Valid email address!");
            return true;
        }
    else
    {
        alert("Invalid email address!");
        return false;
    }
}
```

위의 예에서 사용자가 양식을 제출하려고 하면 사용자 지정 함수 &quot;ValidateEmail&quot;이 호출되어 입력한 이메일 주소가 유효한지 확인합니다.

### 사용자 정의 함수 사용 {#uses-of-custom-function}

적응형 Forms에서 사용자 정의 함수를 사용할 때의 장점은 다음과 같습니다.

* **데이터 조작**: 사용자 정의 함수는 양식 필드에 입력된 데이터를 조작하고 처리합니다.
* **데이터 유효성 검사**: 사용자 정의 기능을 사용하면 양식 입력에 대한 사용자 정의 검사를 수행하고 지정된 오류 메시지를 제공할 수 있습니다.
* **동적 동작**: 사용자 정의 기능을 사용하면 특정 조건에 따라 양식의 동적 동작을 제어할 수 있습니다. 예를 들어 필드를 표시/숨기거나, 필드 값을 수정하거나, 양식 논리를 동적으로 조정할 수 있습니다.
* **통합**: 사용자 지정 함수를 사용하여 외부 API 또는 서비스와 통합할 수 있습니다. 외부 소스에서 데이터를 가져오거나 외부 Rest 끝점으로 데이터를 전송하거나 외부 이벤트를 기반으로 사용자 지정 작업을 수행하는 데 도움이 됩니다.

## 지원되는 JS 주석

작성한 사용자 지정 함수에 `jsdoc` 위에.

지원됨 `jsdoc` 태그:

* **비공개**
구문: `@private`
비공개 함수는 사용자 지정 함수로 포함되지 않습니다.

* **이름**
구문: `@name funcName <Function Name>`
또는 `,` 다음을 사용할 수 있습니다. `@function funcName <Function Name>` **또는** `@func` `funcName <Function Name>`.
  `funcName` 는 함수 이름입니다(공백은 허용되지 않음).
  `<Function Name>` 는 함수의 표시 이름입니다.

* **매개 변수**
구문: `@param {type} name <Parameter Description>`
또는 다음을 사용할 수 있습니다. `@argument` `{type} name <Parameter Description>` **또는** `@arg` `{type}` `name <Parameter Description>`.
함수에서 사용하는 매개 변수를 표시합니다. 함수는 여러 매개 변수 태그를 가질 수 있으며, 발생 순서로 각 매개 변수에 대해 하나의 태그가 있습니다.
  `{type}` 매개 변수 유형을 나타냅니다. 허용되는 매개 변수 유형은 다음과 같습니다.

   1. 문자열
   2. 숫자
   3. 부울
   4. 범위
   5. 문자열[]
   6. 숫자[]
   7. 부울[]
   8. 날짜
   9. 날짜[]
   10. 배열
   11. 개체

  `scope` 는 forms 런타임에서 제공하는 특수 globals 개체를 참조합니다. 이 매개 변수는 마지막 매개 변수여야 하며 규칙 편집기에서 사용자에게 표시되지 않습니다. 범위를 사용하여 읽을 수 있는 양식에 액세스하고 필드 프록시 개체를 사용하여 속성, 규칙을 트리거한 이벤트 및 양식을 조작하는 함수 집합을 읽을 수 있습니다.

  `object` type은 매개 변수의 읽기 가능한 필드 개체를 값을 전달하는 대신 사용자 지정 함수에 전달하는 데 사용됩니다.

  모든 매개변수 유형은 위의 유형 중 하나에 분류됩니다. 지원되지 않습니다. 위의 유형 중 하나를 선택해야 합니다. 유형은 대/소문자를 구분하지 않습니다. 매개 변수 이름에는 공백을 사용할 수 없습니다.  매개 변수 설명에는 여러 단어가 포함될 수 있습니다.

* **선택적 매개 변수**
구문: `@param {type=} name <Parameter Description>`
또는 다음을 사용할 수 있습니다. `@param {type} [name] <Parameter Description>`
기본적으로 모든 매개 변수는 필수입니다. 를 추가하여 매개 변수를 선택 사항으로 표시할 수 있습니다 `=` 매개 변수 형식이나 매개 변수 이름을 대괄호로 묶어 입력합니다.
예를 들어 다음을 선언하겠습니다. `Input1` 선택적 매개 변수로:
   * `@param {type=} Input1`
   * `@param {type} [Input1]`

* **반환 유형**
구문: `@return {type}`
또는 다음을 사용할 수 있습니다 `@returns {type}`.
함수 목적 등 함수에 대한 정보를 추가합니다.
{type} 함수의 반환 형식을 나타냅니다. 허용되는 반환 유형은 다음과 같습니다.

   1. 문자열
   2. 숫자
   3. 부울
   4. 문자열[]
   5. 숫자[]
   6. 부울[]
   7. 날짜
   8. 날짜[]
   9. 배열
   10. 개체

다른 모든 반환 유형은 위의 한 가지 유형에 따라 분류됩니다. 지원되지 않습니다. 위의 유형 중 하나를 선택해야 합니다. 반환 유형은 대/소문자를 구분하지 않습니다.

## 사용자 지정 함수를 만드는 동안 고려 사항 {#considerations}

규칙 편집기에 사용자 정의 함수를 나열하려면 다음 형식 중 하나로 선언하면 됩니다.

* **jsdoc 주석이 있거나 없는 Function 문**

jsdoc 주석을 사용하거나 사용하지 않고 사용자 지정 함수를 만들 수 있습니다.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
<!--

* **Arrow function with mandatory jsdoc comment**

Some of the examples to create Arrow functions are:
```javascript
    /**
    * test function
    * @name testFunction test function
    * @param {string} a some parameter description
    * @param {string} b another parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
```

    * @param {string=} b another parameter description
      /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;-->

* **필수 jsdoc 주석이 있는 함수 표현식**

적응형 양식의 규칙 편집기에 사용자 정의 함수를 나열하려면 다음 형식으로 사용자 정의 함수를 만듭니다.

```javascript
    /**
    * test function
    * @name testFunction test function
    * @param {string} input1 parameter description
    * @param {string} input2 another parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

<!--
* @param {string=} input2 another parameter description
The functions that are not supported in the custom function list are:
* Generator functions
* Async/Await functions 
* Method definitions
* Class methods
* Default parameters
* Rest parameters -->

>[!NOTE]
>
> 다음을 확인할 수 있습니다. `error.log` 사용자 지정 함수가 규칙 편집기에 나열되지 않는 등의 오류에 대한 파일입니다.

<!--The `error.log` file also displays the methods and parameters that are not supported for custom functions. -->


## 사용자 지정 함수 만들기 {#create-custom-function}

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

   >[!NOTE]
   >
   > 사용자 정의 함수에 대한 코드가 포함된 JavaScript 파일에 오류가 있는 경우 사용자 정의 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다. 다음을 확인할 수도 있습니다. `error.log` 파일에 오류가 표시됩니다.

   <!-- 
    >* AEM Adaptive Form supports the caching of custom functions. If the JavaScript is modified, the caching becomes invalidated, and it is parsed. You can see a message as `Fetched following custom functions list from cache` in the `error.log` file.  -->

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

1. [파이프라인 실행.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline)

파이프라인이 성공적으로 실행되면 클라이언트 라이브러리에 추가된 사용자 지정 함수를에서 사용할 수 있게 됩니다 [적응형 양식 규칙 편집기](/help/forms/rule-editor-core-components.md).

### 적응형 양식에 클라이언트 라이브러리 추가{#use-custom-function}

클라이언트 라이브러리를 Forms CS 환경에 배포한 후에는 적응형 양식에서 해당 기능을 사용하십시오. 적응형 양식에 클라이언트 라이브러리를 추가하려면

1. 편집 모드에서 양식을 엽니다. 편집 모드에서 양식을 열려면 양식을 선택하고 을 선택합니다 **[!UICONTROL 편집]**.
1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. 를 엽니다. **[!UICONTROL 기본]** 탭을 클릭하고 이름 선택 **[!UICONTROL 클라이언트 라이브러리 범주]** 드롭다운 목록에서(이 경우 `customfunctionscategory`).

   ![사용자 정의 함수 클라이언트 라이브러리 추가](/help/forms/assets/clientlib-custom-function.png)

1. 클릭 **[!UICONTROL 완료]** .

이제 규칙 편집기에서 사용자 정의 함수를 사용하는 규칙을 만들 수 있습니다.

<!--

Create a rule to use custom function in the rule editor. 

### Support for the optional parameters in custom functions{#support-for-optional-parameter}

AEM supports including optional parameters in JSDocs. These parameters are displayed as optional in the rule editor. There are two ways to add optional parameters in JSDocs:
*  `@param {string=abc} b -- some description for b which is optional`

    In the above line of code, `b` is an optional parameter with the default value set to `abc`. 
    Alternatively, you can define `b` as an optional parameter without assigning any default value as `@param {string=} b -- some description for b which is optional`

* `@param {array} [z=[def,xyz]] - - some description for z which is optional`

    In the above line of code, `z` is an optional parameter of array type with the default value set to `[def , xyz]`. 
    Alternatively, you can define `z` as an optional parameter without assigning any default value as `@param {array} [z=] - - some description for z which is optional`

>[!NOTE]
>
> Ensure that the parameter name is enclosed in square brackets [] and the parameter type is enclosed in curly brackets {}. 

To learn more about how to define optional parameters in JSDocs, [click here](https://jsdoc.app/tags-param).

In the rule editor of an Adaptive Form, the parameters are displayed as `required`. By default the parameters are `required`, if not defined as optional in JSDocs.

  ![Optional or required parameters](/help/forms/assets/optional-default-params.png) 

  You can save the rule without specifying a value for required parameters, but the rule is not executed and displays a warning message as:

  ![incomplete rule warning message](/help/forms/assets/incomplete-rule.png) 
  
  The rule is executed even if you do not specify a value for optional parameters. Undefined values are passed for optional parameters on executing the rule.

  ### Support for field and globals objects in custom functions {#support-field-and-global-objects}

  needs to be discussed

  -->

## 추가 참조 {#see-also}

{{see-also}}





