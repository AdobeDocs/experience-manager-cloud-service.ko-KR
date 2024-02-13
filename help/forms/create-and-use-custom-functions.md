---
title: 적응형 양식에서 사용자 정의 함수 만들기 및 추가
description: AEM Forms은 사용자가 규칙 편집기 내에서 자체 함수를 만들고 사용할 수 있도록 하는 사용자 지정 함수를 지원합니다.
keywords: 사용자 지정 함수를 추가하고, 사용자 지정 함수를 사용하고, 사용자 지정 함수를 만들고, 규칙 편집기에서 사용자 지정 함수를 사용합니다.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
source-git-commit: 28020b05e4aaaa3f066943e0504f05e307c7020b
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 8%

---


# 적응형 Forms(핵심 구성 요소)의 사용자 지정 기능

## 소개

AEM Forms은 사용자 정의 함수를 지원하므로 사용자가 복잡한 비즈니스 규칙을 구현하기 위한 JavaScript 함수를 정의할 수 있습니다. 이러한 사용자 지정 기능은 지정된 요구 사항을 충족하도록 입력된 데이터의 조작 및 처리를 용이하게 하여 양식의 기능을 확장합니다. 또한 사전 정의된 기준에 따라 양식 동작을 동적으로 변경할 수 있습니다.
적응형 Forms에서는 [적응형 양식의 규칙 편집기](/help/forms/rule-editor.md#custom-functions) 을 입력하여 양식 필드에 대한 특정 유효성 검사 규칙을 만듭니다.

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

적응형 Forms에서 사용자 정의 함수를 사용하는 몇 가지 장점은 다음과 같습니다.

* **데이터 조작**: 사용자 정의 함수는 양식 필드에 입력된 데이터를 조작하고 처리합니다.
* **데이터 유효성 검사**: 사용자 정의 기능을 사용하면 양식 입력에 대한 사용자 정의 검사를 수행하고 지정된 오류 메시지를 제공할 수 있습니다.
* **동적 동작**: 사용자 정의 기능을 사용하면 특정 조건에 따라 양식의 동적 동작을 제어할 수 있습니다. 예를 들어 필드를 표시/숨기거나, 필드 값을 수정하거나, 양식 논리를 동적으로 조정할 수 있습니다.
* **통합**: 사용자 지정 함수를 사용하여 외부 API 또는 서비스와 통합할 수 있습니다. 외부 소스에서 데이터를 가져오거나 외부 Rest 끝점으로 데이터를 전송하거나 외부 이벤트를 기반으로 사용자 지정 작업을 수행하는 데 도움이 됩니다.

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

다음 형식의 사용자 지정 함수를 만들어 적응형 양식의 규칙 편집기에 나열합니다. 예:

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
> 다음을 확인할 수 있습니다. `error.log` 사용자 지정 함수와 같은 오류가 발생한 경우 파일이 규칙 편집기에 나열되지 않습니다.

<!--The `error.log` file also displays the methods and parameters that are not supported for custom functions. -->


## 사용자 지정 함수 만들기 {#create-custom-function}

규칙 편집기에서 사용자 지정 함수를 호출할 클라이언트 라이브러리를 만듭니다. 자세한 내용은 [클라이언트측 라이브러리 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).

사용자 정의 함수를 만드는 단계는 다음과 같습니다.
1. [클라이언트 라이브러리 만들기](#create-client-library)
1. [적응형 양식에 클라이언트 라이브러리 추가](#use-custom-function)

### 클라이언트 라이브러리 만들기 {#create-client-library}

클라이언트 라이브러리를 추가하여 사용자 정의 함수를 추가할 수 있습니다. 클라이언트 라이브러리를 만들려면 다음 단계를 수행하십시오.

1. [AEM Forms as a Cloud Service 저장소 복제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#accessing-git).
1. `[AEM Forms as a Cloud Service repository folder]/apps/` 폴더 아래에 폴더를 만듭니다. 예: `experience-league`로 지정된 폴더 만들기
1. `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/`로 이동하고 `es6clientlibs`로서 `ClientLibraryFolder`를 만듭니다.
1. 속성 추가 `categories`문자열 유형 값이 인 `es6customfunctions` (으)로 `es6clientlibs` 폴더를 삭제합니다.

   >[!NOTE]
   >
   >`es6customfunctions`는 예제 범주입니다. 범주의 이름을 선택할 수 있습니다.

1. `js`라는 이름의 폴더를 만듭니다.
1. `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/es6clientlibs/js` 폴더로 이동합니다.
1. JavaScript 파일 추가(예: ) `function.js`. 이 파일은 사용자 지정 함수에 대한 코드로 구성됩니다.

   >[!NOTE]
   >
   >* 사용자 정의 함수에 대한 코드가 포함된 JavaScript 파일에 오류가 있는 경우 사용자 정의 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다. 다음을 확인할 수도 있습니다. `error.log` 파일에 오류가 표시됩니다.

   <!-- 
    >* AEM Adaptive Form supports the caching of custom functions. If the JavaScript is modified, the caching becomes invalidated, and it is parsed. You can see a message as `Fetched following custom functions list from cache` in the `error.log` file.  -->

1. `function.js` 파일을 저장합니다.
1. `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/es6clientlibs/js` 폴더로 이동합니다.
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

파이프라인이 성공적으로 실행되면 클라이언트 라이브러리에 추가된 사용자 지정 함수를에서 사용할 수 있게 됩니다 [적응형 양식 규칙 편집기](/help/forms/rule-editor.md).

### 적응형 양식에 클라이언트 라이브러리 추가{#use-custom-function}

클라이언트 라이브러리를 추가한 후 적응형 양식에서 사용합니다. 을(를) 사용하면 [사용자 정의 함수를 양식의 규칙으로 사용](/help/forms/rule-editor.md#custom-functions). 적응형 양식에 클라이언트 라이브러리를 추가하려면 다음 단계를 수행하십시오.

1. 편집 모드에서 양식을 엽니다.
편집 모드에서 양식을 열려면 양식을 선택하고 을 선택합니다 **[!UICONTROL 열기]**.
1. 편집 모드에서 구성 요소를 선택한 다음 를 선택합니다 ![필드 수준](assets/select_parent_icon.svg) > **[!UICONTROL 적응형 양식 컨테이너]**&#x200B;을 선택한 다음 을 선택합니다 ![cmppr](assets/configure-icon.svg).
1. 사이드바의 클라이언트 라이브러리 이름 아래에서 클라이언트 라이브러리를 추가합니다. ( `es6customfunctions` 예제에서.)

   ![사용자 정의 함수 클라이언트 라이브러리 추가](/help/forms/assets/clientlib-custom-function.png)

규칙 편집기에서 사용자 지정 함수를 사용할 규칙을 만듭니다.

<!--

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





