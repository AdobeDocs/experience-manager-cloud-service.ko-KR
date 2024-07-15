---
title: 적응형 양식에서 사용자 정의 함수 만들기 및 추가
description: AEM Forms은 사용자가 규칙 편집기 내에서 자체 함수를 만들고 사용할 수 있도록 하는 사용자 지정 함수를 지원합니다.
keywords: 사용자 지정 함수를 추가하고, 사용자 지정 함수를 사용하고, 사용자 지정 함수를 만들고, 규칙 편집기에서 사용자 지정 함수를 사용합니다.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
role: User, Developer
source-git-commit: 52b87073cad84705b5dc0c6530aff44d1e686609
workflow-type: tm+mt
source-wordcount: '4333'
ht-degree: 1%

---


# 적응형 Forms(핵심 구성 요소)의 사용자 지정 기능

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | 이 문서 |

## 소개

AEM Forms은 사용자 정의 함수를 지원하므로 사용자가 복잡한 비즈니스 규칙을 구현하기 위한 JavaScript 함수를 정의할 수 있습니다. 이러한 사용자 지정 기능은 지정된 요구 사항을 충족하도록 입력된 데이터의 조작 및 처리를 용이하게 하여 양식의 기능을 확장합니다. 또한 사전 정의된 기준에 따라 양식 동작을 동적으로 변경할 수 있습니다.

>[!NOTE]
>
> 최신 기능을 사용하려면 [핵심 구성 요소](https://github.com/adobe/aem-core-forms-components)가 최신 버전으로 설정되어 있는지 확인하십시오.

### 사용자 정의 함수 사용 {#uses-of-custom-function}

적응형 Forms에서 사용자 정의 함수를 사용할 때의 장점은 다음과 같습니다.
* **데이터 처리**: 사용자 지정 함수를 사용하면 양식 필드에 입력한 데이터를 처리할 수 있습니다.
* **데이터 유효성 검사**: 사용자 지정 기능을 사용하면 양식 입력에 대한 사용자 지정 검사를 수행하고 지정된 오류 메시지를 제공할 수 있습니다.
* **동적 동작**: 사용자 지정 함수를 사용하면 특정 조건에 따라 양식의 동적 동작을 제어할 수 있습니다. 예를 들어 필드를 표시/숨기거나, 필드 값을 수정하거나, 양식 논리를 동적으로 조정할 수 있습니다.
* **통합**: 사용자 지정 함수를 사용하여 외부 API 또는 서비스와 통합할 수 있습니다. 외부 소스에서 데이터를 가져오거나 외부 Rest 끝점으로 데이터를 전송하거나 외부 이벤트를 기반으로 사용자 지정 작업을 수행하는 데 도움이 됩니다.

사용자 지정 함수는 기본적으로 JavaScript 파일에 추가되는 클라이언트 라이브러리입니다. 사용자 지정 함수를 만들면 규칙 편집기에서 적응형 양식에서 사용자가 선택할 수 있게 됩니다. 사용자 지정 함수는 규칙 편집기의 JavaScript 주석으로 식별됩니다.

### 사용자 지정 기능에 대해 지원되는 JavaScript 주석 {#js-annotations}

JavaScript 주석은 JavaScript 코드에 대한 메타데이터를 제공하는 데 사용됩니다. 여기에는 /** 및 @과 같은 특정 기호로 시작하는 주석이 포함됩니다. 주석은 함수, 변수 및 코드의 기타 요소에 대한 중요한 정보를 제공합니다. 적응형 양식은 사용자 정의 기능에 대해 다음 JavaScript 주석을 지원합니다.

#### 이름

이 이름은 적응형 양식의 규칙 편집기에서 사용자 지정 기능을 식별하는 데 사용됩니다. 다음 구문을 사용하여 사용자 지정 함수의 이름을 지정합니다.

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`
  `functionName`은(는) 함수 이름입니다. 공백은 허용되지 않습니다.
  `<Function Name>`은(는) 적응형 양식의 규칙 편집기에 있는 함수의 표시 이름입니다.
함수 이름이 함수 자체의 이름과 동일한 경우 구문에서 `[functionName]`을(를) 생략할 수 있습니다.

#### 매개변수

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
   * 범위: 사용자 지정 함수 내에서 양식을 수정하는 방법, 양식 인스턴스, 대상 필드 인스턴스와 같은 읽기 전용 변수를 포함하는 globals 개체를 나타냅니다. 이 매개 변수는 JavaScript 주석의 마지막 매개 변수로 선언되며 적응형 양식의 규칙 편집기에 표시되지 않습니다. 범위 매개 변수는 양식 또는 구성 요소의 개체에 액세스하여 양식 처리에 필요한 규칙이나 이벤트를 트리거합니다. Globals 개체 및 사용 방법에 대한 자세한 정보는 [여기를 클릭](/help/forms/create-and-use-custom-functions.md#support-field-and-global-objects)하십시오.

매개 변수 형식은 대/소문자를 구분하지 않으며 매개 변수 이름에는 공백을 사용할 수 없습니다.

`<Parameter Description>`에 매개 변수의 용도에 대한 세부 정보가 포함되어 있습니다. 여러 단어가 있을 수 있습니다.

**선택적 매개 변수**
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

#### 반환 유형

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

#### 비공개

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

## 사용자 정의 함수 만들기 {#create-custom-function}

규칙 편집기에서 사용자 지정 함수를 호출할 클라이언트 라이브러리를 만듭니다. 자세한 내용은 [클라이언트측 라이브러리 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing)을 참조하십시오.

사용자 정의 함수를 만드는 단계는 다음과 같습니다.
1. [클라이언트 라이브러리 만들기](#create-client-library)
1. [적응형 양식에 클라이언트 라이브러리 추가](#use-custom-function)


### 사용자 지정 함수를 만들기 위한 사전 요구 사항

적응형 Forms에 사용자 지정 기능을 추가하기 전에 다음을 확인하십시오.

**소프트웨어:**

* **IDE(일반 텍스트 편집기)**: 모든 일반 텍스트 편집기가 작동할 수 있지만, Microsoft Visual Studio Code와 같은 IDE(통합 개발 환경)에서는 쉽게 편집할 수 있는 고급 기능을 제공합니다.

* **Git:** 코드 변경 내용을 관리하려면 이 버전 제어 시스템이 필요합니다. 설치되지 않은 경우 https://git-scm.com에서 다운로드하십시오.

### 클라이언트 라이브러리 만들기 {#create-client-library}

클라이언트 라이브러리를 추가하여 사용자 정의 함수를 추가할 수 있습니다. 클라이언트 라이브러리를 만들려면 다음 단계를 수행하십시오.

**리포지토리 복제**

[AEM Forms as a Cloud Service 리포지토리 복제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#accessing-git):

1. 명령줄 또는 터미널 창을 엽니다.

1. 저장소를 저장할 시스템에서 원하는 위치로 이동합니다.

1. 다음 명령을 실행하여 저장소를 복제합니다.

   `git clone [Git Repository URL]`

이 명령은 저장소를 다운로드하고 시스템에 복제된 저장소의 로컬 폴더를 만듭니다. 이 안내서에서는 이 폴더를 [AEMaaCS 프로젝트 디렉터리](으)로 참조합니다.

**클라이언트 라이브러리 폴더 추가**

새 클라이언트 라이브러리 폴더를 [AEMaaCS 프로젝트 디렉터리]에 추가하려면 다음 단계를 수행합니다.

1. 편집기에서 [AEMaaCS 프로젝트 디렉터리]를 엽니다.

   ![사용자 지정 함수 폴더 구조](/help/forms/assets/custom-library-folder-structure.png)

1. `ui.apps` 찾기.
1. 새 폴더를 추가합니다. 예를 들어 `experience-league`(으)로 이름이 지정된 폴더를 추가합니다.
1. `/experience-league/` 폴더로 이동하여 `ClientLibraryFolder`을(를) 추가합니다. 예를 들어 이름이 `customclientlibs`인 클라이언트 라이브러리 폴더를 만듭니다.

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**클라이언트 라이브러리 폴더에 파일 및 폴더 추가**

추가된 클라이언트 라이브러리 폴더에 다음을 추가합니다.

* .content.xml 파일
* js.txt 파일
* js 폴더

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. `.content.xml`에서 다음 코드 행을 추가합니다.

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > `client library folder` 및 `categories` 속성의 이름을 선택할 수 있습니다.

1. `js.txt`에서 다음 코드 행을 추가합니다.

   ```javascript
         #base=js
       function.js
   ```
1. `js` 폴더에서 사용자 지정 함수를 포함하는 `function.js`(으)로 Javascript 파일을 추가합니다.

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
1. 파일을 저장합니다.

![사용자 지정 함수 폴더 구조](/help/forms/assets/custom-function-added-files.png)

**filter.xml에 새 폴더 포함**:

1. [AEMaaCS 프로젝트 디렉터리]에서 `/ui.apps/src/main/content/META-INF/vault/filter.xml` 파일로 이동합니다.

1. 파일을 열고 끝에 다음 줄을 추가합니다.

   `<filter root="/apps/experience-league" />`
1. 파일을 저장합니다.

![사용자 지정 함수 필터 xml](/help/forms/assets/custom-function-filterxml.png)

**새로 만든 클라이언트 라이브러리 폴더를 AEM 환경에 배포합니다**

Cloud Service 환경에 AEM as a Cloud Service [AEMaaCS 프로젝트 디렉터리]를 배포합니다. Cloud Service 환경에 배포하려면 다음을 수행하십시오.

1. 변경 내용 커밋

   1. 아래 명령을 사용하여 저장소의 변경 내용을 추가하고, 커밋하고, 푸시합니다.

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. 업데이트된 코드를 배포합니다.

   1. 기존 전체 스택 파이프라인을 통해 코드 배포를 트리거합니다. 이렇게 하면 업데이트된 코드가 자동으로 빌드 및 배포됩니다.

아직 파이프라인을 설정하지 않았다면 [AEM Formsas a Cloud Service 에 대한 파이프라인 설정 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline)에 대한 안내서를 참조하십시오.

파이프라인이 실행되면 클라이언트 라이브러리에 추가된 사용자 지정 함수를 [적응형 양식 규칙 편집기](/help/forms/rule-editor-core-components.md)에서 사용할 수 있게 됩니다.

### 적응형 양식에 클라이언트 라이브러리 추가{#use-custom-function}

클라이언트 라이브러리를 Forms CS 환경에 배포한 후에는 적응형 양식에서 해당 기능을 사용하십시오. 적응형 양식에 클라이언트 라이브러리를 추가하려면

1. 편집 모드에서 양식을 엽니다. 편집 모드에서 양식을 열려면 양식을 선택하고 **[!UICONTROL 편집]**&#x200B;을 선택합니다.
1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 기본]** 탭을 열고 드롭다운 목록에서 **[!UICONTROL 클라이언트 라이브러리 범주]**&#x200B;의 이름을 선택합니다(이 경우 `customfunctionscategory` 선택).

   ![사용자 지정 함수 클라이언트 라이브러리를 추가](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > **[!UICONTROL 클라이언트 라이브러리 범주]** 필드 내에서 쉼표로 구분된 목록을 지정하여 여러 범주를 추가할 수 있습니다.

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

[JavaScript 주석](##js-annotations)을 사용하여 [적응형 양식의 규칙 편집기](/help/forms/rule-editor-core-components.md)에서 사용자 지정 함수를 사용할 수 있습니다.

## 적응형 양식에서 사용자 정의 함수 사용

적응형 양식에서는 [규칙 편집기 내에서 사용자 지정 함수](/help/forms/rule-editor-core-components.md)를 사용할 수 있습니다. JavaScript 파일(`Function.js` 파일)에 다음 코드를 추가하여 생년월일(YYYY-MM-DD)을 기준으로 연령을 계산합니다. 생년월일을 입력으로 취하여 연령을 반환하는 사용자 지정 함수를 `calculateAge()`(으)로 만듭니다.

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

위의 예에서 사용자가 생년월일을 형식(YYYY-MM-DD)으로 입력하면 사용자 지정 함수 `calculateAge`이(가) 호출되고 연령을 반환합니다.

![규칙 편집기에서 Agae 사용자 지정 함수 계산](/help/forms/assets/custom-function-calculate-age.png)

이제 양식을 미리 보기하여 사용자 정의 함수가 규칙 편집기를 통해 어떻게 구현되는지 살펴보겠습니다.

![규칙 편집기 양식 미리 보기에서 Agae 사용자 지정 함수 계산](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> 다음 [사용자 지정 함수](/help/forms/assets//customfunctions.zip) 폴더를 참조할 수 있습니다. [패키지 관리자](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager)를 사용하여 AEM 인스턴스에 이 폴더를 다운로드하여 설치하십시오.


### 사용자 정의 함수를 사용하여 드롭다운 목록 옵션 설정

핵심 구성 요소의 규칙 편집기에서 런타임에 드롭다운 목록 옵션을 설정하는 **옵션 설정 of** 속성을 지원하지 않습니다. 그러나 사용자 지정 함수를 사용하여 드롭다운 목록 옵션을 설정할 수 있습니다.

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

위의 코드에서는 `setEnums`을(를) 사용하여 `enum` 속성을 설정하고 `setEnumNames`을(를) 사용하여 드롭다운의 `enumNames` 속성을 설정합니다.

사용자가 `Next` 단추를 클릭할 때 드롭다운 목록 옵션의 값을 설정하는 `Next` 단추에 대한 규칙을 만들어 보겠습니다.

![드롭다운 목록 옵션](/help/forms/assets/drop-down-list-options.png)

표시 버튼을 클릭할 때 드롭다운 목록의 옵션이 설정되는 위치를 보여 주려면 아래 그림을 참조하십시오.

![규칙 편집기의 드롭다운 옵션](/help/forms/assets/drop-down-option-rule-editor.png)



### 사용자 지정 함수에서 비동기 함수 지원 {#support-of-async-functions}

비동기 사용자 지정 함수는 규칙 편집기 목록에 표시되지 않습니다. 그러나 동기 함수 표현식을 사용하여 만든 사용자 지정 함수 내에서 비동기 함수를 호출할 수 있습니다.

![동기화 및 비동기 사용자 지정 함수](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

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

위의 예에서 asyncFunction 함수는 `asynchronous function`입니다. `https://petstore.swagger.io/v2/store/inventory`에 `GET`을(를) 요청하여 비동기 작업을 수행합니다. `await`을(를) 사용하여 응답을 기다리고 `response.json()`을(를) 사용하여 응답 본문을 JSON으로 구문 분석한 다음 데이터를 반환합니다. `callAsyncFunction` 함수는 `asyncFunction` 함수를 호출하고 콘솔에 응답 데이터를 표시하는 동기 사용자 지정 함수입니다. `callAsyncFunction` 함수는 동기식이지만 비동기 asyncFunction 함수를 호출하고 그 결과를 `then` 및 `catch` 문으로 처리합니다.

작동 여부를 확인하려면 단추를 추가하고 단추 클릭 시 비동기 함수를 호출하는 단추에 대한 규칙을 만들어 보겠습니다.

![비동기 함수에 대한 규칙을 만드는 중](/help/forms/assets/rule-for-async-funct.png)

사용자가 `Fetch` 단추를 클릭하면 사용자 지정 함수 `callAsyncFunction`이(가) 호출되어 비동기 함수 `asyncFunction`이(가) 호출되는지 보여 주려면 아래 콘솔 창의 그림을 참조하십시오. Inspect 콘솔 창에서 버튼에 대한 응답을 봅니다. 클릭:

![콘솔 창](/help/forms/assets/async-custom-funct-console.png)

사용자 정의 함수의 기능에 대해 자세히 살펴보겠습니다.

## 사용자 정의 기능을 위한 다양한 기능

사용자 지정 함수를 사용하여 양식에 개인화된 기능을 추가할 수 있습니다. 이러한 기능은 특정 필드 작업, 전역 필드 사용 또는 캐싱과 같은 다양한 기능을 지원합니다. 이러한 유연성을 통해 조직의 요구 사항에 따라 양식을 사용자 정의할 수 있습니다.

### 사용자 지정 함수의 필드 및 전역 범위 개체 {#support-field-and-global-objects}

필드 개체는 텍스트 필드, 확인란 등 양식 내의 개별 구성 요소 또는 요소를 나타냅니다. Globals 개체에는 사용자 지정 함수 내에서 양식을 수정하는 방법, 대상 필드 인스턴스 및 양식 인스턴스와 같은 읽기 전용 변수가 포함되어 있습니다.

>[!NOTE]
>
> `param {scope} globals`은(는) 마지막 매개 변수여야 하며 적응형 양식의 규칙 편집기에 표시되지 않습니다.

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

사용자 지정 함수에서 다양한 사용 사례를 사용하여 `Contact Us` 양식의 도움을 받아 필드 및 전역 개체를 사용하는 방법에 대해 알아보겠습니다.

![연락처 양식](/help/forms/assets/contact-us-form.png)

+++ **사용 사례**: `SetProperty` 규칙을 사용하여 패널 표시

[create-custom-function](#create-custom-function) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 양식 필드를 `Required`(으)로 설정합니다.

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

+++

+++ **사용 사례**: 필드의 유효성을 검사합니다.

[create-custom-function](#create-custom-function) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 필드의 유효성을 검사합니다.

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

+++

+++ **사용 사례**: 패널 재설정

[create-custom-function](#create-custom-function) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 패널을 재설정합니다.

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

+++

+++ **사용 사례**: 필드 수준에서 사용자 지정 메시지를 표시하고 필드를 잘못된 것으로 표시하려면

`markFieldAsInvalid()` 함수를 사용하여 필드를 잘못된 필드로 정의하고 필드 수준에서 사용자 지정 오류 메시지를 설정할 수 있습니다. `fieldIdentifier` 값은 `fieldId`, `field qualifiedName` 또는 `field dataRef`일 수 있습니다. 이름이 `option`인 개체의 값은 `{useId: true}`, `{useQualifiedName: true}` 또는 `{useDataRef: true}`일 수 있습니다.
필드를 유효하지 않은 것으로 표시하고 사용자 정의 메시지를 설정하는 데 사용되는 구문은 다음과 같습니다.

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

[create-custom-function](#create-custom-function) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 필드 수준에서 사용자 지정 메시지를 사용하도록 설정합니다.

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

+++

+++ **사용 사례**: 변경된 데이터를 서버에 제출

다음 코드 줄:
`globals.functions.submitForm(globals.functions.exportData(), false);`은(는) 조작 후 양식 데이터를 제출하는 데 사용됩니다.
* 첫 번째 인수는 제출할 데이터입니다.
* 두 번째 인수는 제출 전에 양식의 유효성을 검사할지 여부를 나타냅니다. `optional`이며 기본적으로 `true`(으)로 설정됩니다.
* 세 번째 인수는 제출 서류의 `contentType`이며, 기본값인 `multipart/form-data`과(와) 함께 선택 사항입니다. 다른 값은 `application/json` 및 `application/x-www-form-urlencoded`일 수 있습니다.

[create-custom-function](#create-custom-function) 섹션에 설명된 대로 사용자 지정 함수에 다음 코드를 추가하여 조작된 데이터를 서버에 제출합니다.

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

+++

+++ **사용 사례**: 양식 제출 성공 및 오류 처리기 재정의

[create-custom-function](#create-custom-function) 섹션에 설명된 대로 다음 코드 행을 추가하여 양식 제출을 위한 제출 또는 실패 메시지를 사용자 지정하고 양식 제출 메시지를 모달 상자에 표시합니다.

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

+++

+++ **사용 사례**: 반복 가능한 패널의 특정 인스턴스에서 작업을 수행합니다.

반복 가능 패널에서 시각적 규칙 편집기를 사용하여 만든 규칙은 반복 가능 패널의 마지막 인스턴스에 적용됩니다. 반복 가능 패널의 특정 인스턴스에 대한 규칙을 작성하려면 사용자 지정 함수를 사용합니다.

목적지로 향하는 여행자에 대한 정보를 수집할 다른 양식을 만들어 보겠습니다. 여행자 패널이 반복 가능한 패널로 추가됩니다. 이 패널에서 `Add Traveler` 버튼을 사용하여 5명의 여행자에 대한 세부 정보를 추가할 수 있습니다.

![여행자 정보](/help/forms/assets/traveler-info-form.png)

[create-custom-function](#create-custom-function) 섹션에 설명된 대로 다음 코드 행을 추가하여 마지막 인스턴스가 아닌 반복 가능한 패널의 특정 인스턴스에서 작업을 수행합니다.

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

+++

+++ **사용 사례**: 양식이 로드될 때 값을 사용하여 필드를 미리 채웁니다.

[create-custom-function](#create-custom-function) 섹션에서 설명한 대로 다음 코드 행을 추가하여 양식을 초기화할 때 필드에 미리 채워진 값을 로드합니다.

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

+++

+++ **Usecase**: 특정 필드에 초점을 설정합니다.

[create-custom-function](#create-custom-function) 섹션에서 설명한 대로 다음 코드 행을 추가하여 `Submit` 단추를 클릭할 때 지정된 필드에 포커스를 설정합니다.

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

+++

+++ **Usecase**: `dispatchEvent` 속성을 사용하여 반복 가능한 패널을 추가하거나 삭제합니다.

[create-custom-function](#create-custom-function) 섹션에서 설명한 대로 다음 코드 행을 추가하여 `dispatchEvent` 속성을 사용하여 `Add Traveler` 단추를 클릭할 때 패널을 추가합니다.

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

+++

## 사용자 지정 기능에 대한 캐싱 지원

적응형 Forms은 규칙 편집기에서 사용자 지정 함수 목록을 검색하는 동안 응답 시간을 개선하기 위해 사용자 지정 함수에 대한 캐싱을 구현합니다. `Fetched following custom functions list from cache`(으)로 표시되는 메시지가 `error.log` 파일에 나타납니다.

캐시를 지원하는 ![사용자 지정 함수](/help/forms/assets/custom-function-cache-error.png)

사용자 지정 함수가 수정되면 캐싱이 무효화되고 구문 분석됩니다.

## 문제 해결 {#troubleshooting}

* 사용자 지정 제출 처리기가 기존 AEM 프로젝트 또는 양식에서 예상대로 수행되지 않으면 다음 단계를 수행하십시오.
   * [핵심 구성 요소 버전이 3.0.18 이상](https://github.com/adobe/aem-core-forms-components)(으)로 업데이트되었는지 확인하십시오. 그러나 기존 AEM 프로젝트 및 양식의 경우 따라야 할 추가 단계가 있습니다.

   * AEM 프로젝트의 경우 사용자는 `submitForm('custom:submitSuccess', 'custom:submitError')`의 모든 인스턴스를 `submitForm()`(으)로 바꾸고 Cloud Manager 파이프라인을 통해 프로젝트를 배포해야 합니다.

   * 기존 양식의 경우 사용자 지정 제출 처리기가 제대로 작동하지 않으면 사용자가 규칙 편집기를 사용하여 **제출** 단추에서 `submitForm` 규칙을 열고 저장해야 합니다. 이 작업은 `submitForm('custom:submitSuccess', 'custom:submitError')`의 기존 규칙을 양식의 `submitForm()`(으)로 바꿉니다.


* 사용자 정의 함수에 대한 코드가 들어 있는 JavaScript 파일에 오류가 있는 경우 사용자 정의 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다. 사용자 지정 함수 목록을 확인하려면 `error.log` 파일로 이동하여 오류를 확인할 수 있습니다. 오류가 발생하면 사용자 지정 함수 목록이 비어 있습니다.

  ![오류 로그 파일](/help/forms/assets/custom-function-list-error-file.png)

  오류가 없는 경우 사용자 지정 함수를 가져와서 `error.log` 파일에 나타납니다. `Fetched following custom functions list`(으)로 표시되는 메시지가 `error.log` 파일에 있습니다.

  ![적절한 사용자 지정 함수를 가진 오류 로그 파일](/help/forms/assets/custom-function-list-fetched-in-error.png)

## 고려 사항

* `parameter type` 및 `return type`은(는) `None`을(를) 지원하지 않습니다.

* 사용자 지정 함수 목록에서 지원되지 않는 함수는 다음과 같습니다.
   * 생성기 함수
   * 비동기/대기 함수
   * 메서드 정의
   * 클래스 메서드
   * 기본 매개 변수
   * 나머지 매개 변수

## 추가 참조 {#see-also}

{{see-also}}


