---
title: AEM용 적응형 Forms Adaptive Forms에서 사용자 지정 오류 핸들러 추가
seo-title: Error Handlers in Adaptive Forms for AEM Adaptive Forms
description: AEM Forms에서는 외부 서비스를 호출하도록 구성된 REST 엔드포인트를 사용하여 양식에 대한 기본 성공 사례와 오류 핸들러를 제공합니다. AEM 적응형 양식에 기본 오류 처리기와 사용자 지정 오류 처리기를 추가할 수 있습니다.
seo-description: Error handler function and Rule Editor in Adaptive Forms helps you to effectively manage and customize error handling. You can add a default error handler as well as custom error handler in an AEM Adaptive Form.
keywords: 사용자 정의 오류 핸들러 추가, 기본 오류 핸들러 추가, 양식에서 오류 핸들러 추가, 규칙 편집기의 호출 서비스를 사용하여 사용자 정의 오류 핸들러 추가, 규칙 편집기를 구성하여 사용자 정의 오류 핸들러 추가, 규칙 편집기를 사용하여 사용자 정의 오류 핸들러 추가
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms
exl-id: 198a26a9-d6bb-457d-aab8-0a5d15177c48
source-git-commit: defeee2fee42c6274c71438d6f9fde6e49a05081
workflow-type: tm+mt
source-wordcount: '2470'
ht-degree: 91%

---

# AEM Adaptive Forms에서 사용자 지정 오류 핸들러 추가 {#error-handlers-in-adaptive-form}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html) |
| AEM as a Cloud Service | 이 문서 |

AEM Forms에서는 양식 제출에 필요한 기본 성공 사례와 오류 핸들러를 제공합니다. 또한 오류 핸들러 함수를 사용자 정의할 수 있는 기능을 제공합니다. 예를 들어 특정 오류 코드의 백엔드에서 사용자 정의 워크플로를 호출하거나 서비스가 중단되었음을 고객에게 알려 줄 수 있습니다. 핸들러는 서버 응답을 기반으로 실행되는 클라이언트측 함수입니다. API를 통해 외부 서비스를 호출할 때 데이터를 유효성 검사를 위해 서버로 전송하면 서버는 제출의 성공 여부 또는 오류 이벤트에 대한 정보가 포함된 응답을 클라이언트에 반환합니다. 정보가 매개변수로서 관련 핸들러에 전달되면 함수를 실행할 수 있습니다. 오류 핸들러는 발생한 오류 또는 유효성 검사 문제를 관리하고 표시하는 데 도움이 됩니다.

![양식에서 사용자 정의 오류 핸들러를 추가하는 방법을 이해할 수 있는 오류 핸들러 워크플로](/help/forms/assets/error-handler-workflow.png)

적응형 양식에서는 사전 설정된 유효성 검사 기준에 따라 필드에 제공되는 입력의 유효성을 검사하고, 외부 서비스를 호출하도록 구성된 REST 엔드포인트에서 반환된 다양한 오류를 확인합니다. 양식과 함께 사용되는 데이터 소스를 기반으로 유효성 검사 기준을 설정할 수 있습니다. 예: RESTful 웹 서비스를 데이터 소스로 사용하는 경우, Swagger 정의 파일에서 유효성 검사 기준을 정의할 수 있습니다.

입력 값이 유효성 검사 기준을 충족하는 경우, 해당 값을 기타 데이터 소스에 제출하게 되면 적응형 양식은 오류 핸들러를 통해 오류 메시지를 표시합니다. 이 접근 방식과 유사한 적응형 양식은 사용자 정의 오류 핸들러와 통합하여 데이터 유효성 검사를 수행합니다. 입력 값이 유효성 검사 기준을 충족하지 않는 경우, 오류 메시지가 적응형 양식의 필드 수준에 표시됩니다. 이는 서버에서 반환된 유효성 검사 오류 메시지가 표준 메시지 형식인 경우 발생합니다.


## 오류 핸들러 사용 {#uses-of-error-handler}

오류 핸들러는 다양한 용도로 사용됩니다. 오류 핸들러 함수의 일부 용도는 다음과 같습니다.
* **유효성 검사 수행**: 오류 처리는 미리 정의된 규칙 또는 기준에 따른 사용자 입력의 유효성 검사로 시작됩니다. 사용자가 적응형 양식을 작성하고 나면 오류 핸들러는 입력의 유효성을 검사하여 적응형 양식이 필요한 포맷, 길이 또는 다른 모든 제약을 충족하는지 확인합니다.

* **실시간 피드백 제공**: 오류가 감지되면 오류 핸들러는 사용자에게 해당 양식 필드 아래의 인라인 오류 메시지와 같은 즉각적인 피드백을 표시합니다. 이 피드백을 통해 사용자는 양식을 제출하고 응답을 기다리지 않고도 오류를 식별하고 수정할 수 있습니다.


* **오류 메시지 표시**: 적응형 양식 제출 시 유효성 검사 오류가 발생하면 오류 핸들러는 적절한 오류 메시지를 표시합니다. 오류 메시지는 명확하고 간결하며, 주의가 필요한 특정 필드를 강조 표시해야 합니다.

* **오류 필드 강조 표시**: 사용자가 잘못된 특정 필드에 주의를 집중하도록 오류 핸들러는 해당 필드를 강조 표시하거나 시각적으로 구별합니다. 배경색을 바꾸고, 사용자가 오류를 빠르게 찾고 해결할 수 있도록 아이콘 또는 테두리나 다른 시각적인 단서를 추가하면서 작업을 수행합니다.


## 실패/오류 응답 형식 {#failure-response-format}

적응형 양식은 서버 유효성 검사 오류 메시지가 다음 표준 포맷인 경우 필드 수준의 오류를 표시합니다.
아래 코드는 기존 실패 응답 구조를 보여 줍니다.

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]
        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
    }
```


위치:

* `errorCausedBy`에서는 실패 이유에 대해 설명합니다.
* `errors` 유효성 검사 오류 메시지와 함께 유효성 검사 기준에 실패한 필드의 SOM 식을 언급하십시오.
* AEM을 통해 추가된 `originCode` 필드는 외부 서비스에서 반환된 http 상태 코드를 포함합니다.
* AEM을 통해 추가된 `originMessage`필드는 외부 서비스에서 반환된 원시 오류 데이터를 포함합니다.

AEM Forms 버전의 기능 개선과 후속 업데이트를 통해서 기존 실패 응답 구조는 기존 실패 응답 구조와 역으로 호환되는 RFC7807 기반의 새 포맷으로 변경되었습니다.

```javascript
    {
        "type": "SERVER_SIDE_VALIDATION/FORM_SUBMISSION/SERVICE_INVOCATION/FAILURE/VALIDATION_ERROR", (required)
        "title": "Server side validation failed/Third party service invocation failed", (optional)
        "detail": "", (optional)
        "instance": "", (optional)
        "validationErrors" : [ (required)
            {
                "fieldName":"<SOM expression of the field whose data sent is invalid>",
                "dataRef":<JSONPath (or XPath) of the data element which is invalid>
                "details": ["Error Message(s) for the field"] (required)
    
            }
        ],
        "originCode": <Origin http status code>, (optional - in case of SERVER_SIDE_VALIDATION)
        "originMessage" : "<unstructured error message returned by service>" (optional - in case of SERVER_SIDE_VALIDATION)
    }
```


>[!NOTE]
>
> * 오류 응답 구조에 **fieldName** 또는 **dataRef** 중 하나가 포함되어 있는지 확인합니다.
> * **ContentType** 헤더가 **애플리케이션/문제+json**&#x200B;인지 확인합니다.

위치:
* `type (required)`에서 실패 유형을 지정합니다. 다음 값 중 하나일 수 있습니다.
   * `SERVER_SIDE_VALIDATION`는 서버측 유효성 검사로 인한 실패를 표시합니다.
   * `FORM_SUBMISSION`은 양식 제출 시 실패를 표시합니다.
   * `SERVICE_INVOCATION`은 서드파티 서비스 호출 시 실패를 표시합니다.
   * `FAILURE`는 일반적인 오류를 표시합니다.
   * `VALIDATION_ERROR`는 유효성 검사 오류로 인한 실패를 표시합니다.

* `title (optional)`은 실패에 대한 제목 또는 간단한 설명을 제공합니다.
* `detail (optional)`는 필요한 경우 실패에 대한 추가 세부 정보를 제공합니다.
* `instance (optional)`는 실패와 연결된 인스턴스 또는 식별자를 나타내고 특정 실패 발생을 추적하거나 식별하는 데 도움을 줍니다.
* `validationErrors (required)`에는 유효성 검사 오류에 대한 정보가 포함됩니다. 다음 필드가 포함됩니다.
   * `fieldname` 은 유효성 검사 기준에 실패한 필드의 SOM 식을 언급합니다.
   * `dataRef`는 유효성 검사에 실패한 필드의 JSON 경로 또는 XPath를 나타냅니다.
   * `details`에는 잘못된 필드와 함께 유효성 검사 오류 메시지가 포함됩니다.
* AEM을 통해 추가된 `originCode (optional)` 필드는 외부 서비스에서 반환된 http 상태 코드를 포함합니다.
* AEM을 통해 추가된 `originMessage (optional)`필드는 외부 서비스에서 반환된 원시 오류 데이터를 포함합니다.

### 샘플 오류 응답 형식 {#sample-error-response-format}

오류 응답을 표시하는 일부 옵션은 다음과 같습니다.

+++  적응형 양식 fieldName 속성을 기반으로 합니다.


* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
          {
              "type": "VALIDATION_ERROR",
              "validationErrors": [
              {
              "fieldName": "guide[0].guide1[0].guideRootPanel[0].textbox1686647736683[0]",
              "dataRef": "",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
          ]
          }
          ]}
  ```

  필드를 탭하고 을(를) 선택하여 적응형 양식에 있는 모든 필드의 SOM 표현식을 볼 수 있습니다. **[!UICONTROL SOM 표현식 보기]**.

  ![사용자 지정 오류 처리기의 오류 응답을 표시하는 적응형 양식 필드의 일부 표현식](/help/forms/assets/custom-error-handler-somexpression.png)

+++


+++ 적응형 양식 dataRef 속성 기반

* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
      {
          "type": "VALIDATION_ERROR",
          "validationErrors": [
          {
              "fieldName": "",
              "dataRef": "/Pet/id",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
              ]
              }
      ]}
  ```

  ![사용자 지정 오류 처리기에서 오류 응답을 표시하는 적응형 양식 필드의 데이터 참조](/help/forms/assets/custom-errorhandler-dataref.png)

양식 구성 요소의 **[!UICONTROL 속성]** 창에서 dataRef 값을 볼 수 있습니다.

+++


## 규칙 편집기를 통해 오류 핸들러 추가 {#add-error-handler-using-rule-editor}

[규칙 편집기의 호출 서비스](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) 작업을 통해 적응형 양식과 함께 사용되는 데이터 소스를 기반으로 유효성 검사 기준을 정의합니다. RESTful 웹 서비스를 데이터 소스로 사용하는 경우, Swagger 정의 파일에서 유효성 검사 기준을 정의할 수 있습니다. 적응형 양식에서 오류 핸들러 함수와 규칙 편집기를 사용하여 오류 처리를 효과적으로 관리하고 사용자 정의할 수 있습니다. 규칙이 트리거되면 규칙 편집기를 통해 조건을 정의하고 원하는 작업을 구성하여 수행할 수 있습니다. 적응형 양식에서는 사전 설정된 유효성 검사 기준에 따라 필드에 제공되는 입력의 유효성을 검사합니다. 입력 값이 유효성 검사 기준을 충족하지 않는 경우, 오류 메시지가 적응형 양식의 필드 수준에 표시됩니다.

>[!NOTE]
>
> * 규칙 편집기의 호출 서비스 작업과 함께 오류 핸들러를 사용하려면 양식 데이터 모델로 적응형 양식을 구성합니다.
> * 오류 응답이 표준 스키마에 있는 경우, 기본 오류 핸들러를 제공하여 오류 메시지를 필드에 표시합니다. 사용자 정의 오류 핸들러 함수에서 기본 오류 핸들러를 호출할 수도 있습니다.

규칙 편집기를 사용하여 다음 작업을 수행할 수 있습니다.
* [기본 오류 핸들러 함수 추가](#add-default-errror-handler)
* [사용자 정의 오류 핸들러 함수 추가](#add-custom-errror-handler)


### 기본 오류 핸들러 함수 추가 {#add-default-errror-handler}

오류 응답이 표준 스키마나 서버측 유효성 검사 실패에 있는 경우, 기본 오류 핸들러를 지원하여 오류 응답을 필드에 표시합니다.
[규칙 편집기의 호출 서비스](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) 작업을 통해 기본 오류 핸들러를 사용하는 방법을 이해하려면 두 필드, **펫 ID** 및 **펫 이름**&#x200B;을 사용하여 간단한 적응형 양식의 예를 살펴본 다음 **펫 ID** 필드의 기본 오류 핸들러를 사용하여 외부 서비스를 호출하도록 구성된 REST 엔드포인트에서 반환된 다양한 오류를 확인합니다(예: `200 - OK`,`404 - Not Found`, `400 - Bad Request`). 규칙 편집기의 서비스 호출 작업을 통해 기본 오류 핸들러를 추가하려면 다음 단계를 실행합니다.

1. 작성 모드에서 적응형 양식을 열고 양식 구성 요소를 선택한 다음 **[!UICONTROL 규칙 편집기]**&#x200B;를 탭하여 규칙 편집기를 엽니다.
1. **[!UICONTROL 만들기]**&#x200B;를 탭합니다.
1. 규칙의 **날짜** 섹션에서 조건을 만듭니다. 예: **펫 ID 필드의 날짜[ 이름]**&#x200B;이 변경되었습니다. 선택이 **상태 선택** 드롭다운 목록에서 변경되었습니다.
1. **Then** 섹션의 **작업 선택** 드롭다운 목록에서 **[!UICONTROL 호출 서비스]**&#x200B;를 선택합니다.
1. **입력** 섹션에서 **사후 서비스**&#x200B;와 해당 데이터 바인딩을 선택합니다. 예: **펫 ID**&#x200B;의 유효성을 검사하려면 **사후 서비스**&#x200B;를 **GET/pet/{petId}**&#x200B;으로 선택하고 **입력** 섹션에서 **펫 ID**&#x200B;를 선택합니다.
1. **출력** 섹션에서 데이터 바인딩을 선택합니다. **출력** 섹션에서 **펫 이름**&#x200B;을 선택합니다.
1. **오류 핸들러** 섹션에서 **[!UICONTROL 기본 오류 핸들러]**&#x200B;를 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

![기본 오류 핸들러 추가하여 양식의 필드 유효성 검사](/help/forms/assets/default-error-handler.png)

이 규칙의 결과로 얻은 **펫 ID**&#x200B;에 대한 입력 값을 사용하여 REST 엔드포인트에서 호출한 외부 서비스를 통해 **펫 이름**&#x200B;의 유효성 검사를 확인합니다. 데이터 소스 기반의 유효성 검사 기준이 실패할 경우, 오류 메시지가 필드 수준에 표시됩니다.

![양식에서 기본 오류 핸들러를 추가하여 오류 응답을 처리할 때 기본 오류 메시지 표시](/help/forms/assets/default-error-message.png)

### 사용자 정의 오류 핸들러 함수 추가 {#add-custom-errror-handler}

사용자 정의 오류 핸들러 함수를 추가하여 다음의 일부 작업을 수행할 수 있습니다.

* 비표준이나 표준 오류 응답을 사용하는 오류 응답을 처리합니다. 이 비표준 오류 응답이 [오류 응답의 표준 스키마](#failure-response-format)를 준수하지 않는다는 점에 유의해야 합니다
* 분석 이벤트를 모든 분석 플랫폼으로 보냅니다. (예: Adobe Analytics).
* 오류 메시지와 함께 모달 대화 상자를 표시합니다.

언급된 작업 외에도, 사용자 정의 오류 핸들러를 사용하여 특정 사용자 요구 사항을 충족하는 사용자 정의 함수를 실행할 수 있습니다.

사용자 정의 오류 핸들러는 외부 서비스에서 반환된 오류에 응답하고, 최종 사용자에게 사용자 정의된 응답을 게재하도록 설계된 함수(클라이언트 라이브러리)입니다. 주석 `@errorHandler`가 포함된 모든 클라이언트 라이브러리는 사용자 정의 오류 핸들러 함수로 간주됩니다. 이 주석은 `.js` 파일에 지정된 오류 핸들러 함수를 식별하는 데 도움이 됩니다.
[규칙 편집기의 호출 서비스](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) 작업을 통해 사용자 정의 오류 핸들러를 만들고 사용하는 방법을 이해하려면 두 필드, **펫 ID** 및 **펫 이름**&#x200B;을 사용하여 간단한 적응형 양식의 예를 살펴본 다음 **펫 ID** 필드의 사용자 정의 오류 핸들러를 사용하여 외부 서비스를 호출하도록 구성된 REST 엔드포인트에서 반환된 다양한 오류를 확인하십시오(예: `200 - OK`,`404 - Not Found`, `400 - Bad Request`).

적응형 양식에서 사용자 정의 오류 핸들러를 추가하고 사용하려면 다음 단계를 수행합니다.
1. [사용자 정의 오류 핸들러 만들기](#create-custom-error-message)
1. [규칙 편집기를 사용하여 사용자 정의 오류 핸들러 구성](#use-custom-error-handler)

#### 1. 사용자 정의 오류 핸들러 만들기 {#create-custom-error-message}

사용자 정의 오류 함수를 만들려면 다음 단계를 수행합니다.

1. [AEM Forms as a Cloud Service 저장소 복제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#accessing-git).
1. `[AEM Forms as a Cloud Service repository folder]/apps/` 폴더 아래에 폴더를 만듭니다. 예: `experience-league`로 지정된 폴더 만들기
1. `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/`로 이동하고 `clientlibs`로서 `ClientLibraryFolder`를 만듭니다.
1. `js`라는 이름의 폴더를 만듭니다.
1. `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` 폴더로 이동합니다.
1. 예: JavaScript 파일을 추가합니다`function.js`. 파일은 사용자 정의 오류 핸들러의 코드로 구성됩니다.
다음 코드를 JavaScript 파일에 추가하여 REST 서비스 엔드포인트가 수신한 응답과 헤더를 브라우저 콘솔에 표시해 보겠습니다.

   ```javascript
       /**
       * Custom Error handler
       * @name customErrorHandler Custom Error Handler Function
       * @errorHandler
       */
       function customErrorHandler(response, headers)
       {
           console.log("Custom Error Handler processing start...");
           console.log("response:"+JSON.stringify(response));
           console.log("headers:"+JSON.stringify(headers));
           guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers);
           console.log("Custom Error Handler processing end...");
       }
   ```

   사용자 정의 오류 핸들러에서 기본 오류 핸들러를 호출하려면 샘플 코드의 다음 라인을 사용합니다.
   `guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers) `

   >[!NOTE]
   >
   > 다음에서 `.content.xml` 파일, 추가 `allowProxy` 및 `categories` 속성.
   >
   > * `allowProxy = [Boolean]true`
   > * `categories= customfunctionsdemo`
   >예: 이 경우에 [custom-errorhandler-name]이 `customfunctionsdemo`로 제공됩니다.

1. `function.js` 파일을 저장합니다.
1. `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` 폴더로 이동합니다.
1. `js.txt`로 텍스트 파일을 추가합니다. 파일에는 다음이 포함됩니다.

   ```javascript
       #base=js
       functions.js
   ```

1. `js.txt` 파일을 저장합니다.\
   생성된 폴더 구조 형태는 다음과 같습니다.

   ![클라이언트 라이브러리 폴더 구조가 생성됨](/help/forms/assets/customclientlibrary_folderstructure.png)

   >[!NOTE]
   >
   > 사용자 정의 함수를 생성하는 방법에 대해 자세히 알아보려면 [규칙 편집기의 사용자 정의 함수](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=ko-KR#write-rules)를 클릭합니다.

1. 아래 명령을 사용하여 저장소의 변경 내용을 추가하고, 커밋하고, 푸시합니다.

   ```javascript
       git add .
       git commit -a -m "Adding error handling files"
       git push
   ```

1. [파이프라인 실행.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline)

파이프라인이 정상적으로 실행되면 사용자 정의 오류 핸들러를 적응형 양식 규칙 편집기에 사용할 수 있게 됩니다. 이제 AEM Forms에서 규칙 편집기의 호출 서비스를 통해 사용자 정의 오류 핸들러를 구성하고 사용하는 방법을 살펴보겠습니다.

#### 2. 규칙 편집기를 사용하여 사용자 정의 오류 핸들러 구성 {#use-custom-error-handler}

적응형 양식에서 사용자 정의 오류 핸들러를 구현하기 전에 **[!UICONTROL 클라이언트 라이브러리 카테고리]**&#x200B;의 클라이언트 라이브러리 이름이 `.content.xml` 파일의 카테고리 옵션에 지정된 이름과 일치하는지 확인합니다.

![적응형 양식 컨테이너 구성에서 클라이언트 라이브러리의 이름 추가](/help/forms/assets/client-library-category-name.png)

이 경우 클라이언트 라이브러리 이름은 다음과 같이 제공됩니다. `customfunctionsdemo` 다음에서 `.content.xml` 파일.

**[!UICONTROL 규칙 편집기의 호출 서비스]** 작업을 통해 사용자 정의 오류 핸들러를 사용하려면

1. 작성 모드에서 적응형 양식을 열고 양식 구성 요소를 선택한 다음 **[!UICONTROL 규칙 편집기]**&#x200B;를 탭하여 규칙 편집기를 엽니다.
1. **[!UICONTROL 만들기]**&#x200B;를 탭합니다.
1. 규칙의 **날짜** 섹션에서 조건을 만듭니다. 예: **[펫 ID 필드 이름]**&#x200B;이 변경되면 **상태 선택** 드롭다운 목록에서 선택이 **변경됩니다**.
1. **Then** 섹션의 **작업 선택** 드롭다운 목록에서 **[!UICONTROL 호출 서비스]**&#x200B;를 선택합니다.
1. **입력** 섹션에서 **사후 서비스**&#x200B;와 해당 데이터 바인딩을 선택합니다. 예: **펫 ID**&#x200B;의 유효성을 검사하려면 **사후 서비스**&#x200B;를 **GET/pet/{petId}**&#x200B;으로 선택하고 **입력** 섹션에서 **펫 ID**&#x200B;를 선택합니다.
1. **출력** 섹션에서 데이터 바인딩을 선택합니다. 예: **출력** 섹션에서 **펫 이름**&#x200B;을 선택합니다.
1. **[!UICONTROL 오류 핸들러]** 섹션에서 **[!UICONTROL 사용자 정의 오류 핸들러]**&#x200B;를 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

![오류 응답을 처리하기 위해 양식에 사용자 지정 오류 처리기 추가](/help/forms/assets/custom-error-handler.png)

이 규칙의 결과로 얻은 **펫 ID**&#x200B;에 대한 입력 값을 사용하여 REST 엔드포인트에서 호출한 외부 서비스를 통해 **펫 이름**&#x200B;의 유효성 검사를 확인합니다. 데이터 소스 기반의 유효성 검사 기준이 실패할 경우, 오류 메시지가 필드 수준에 표시됩니다.

![양식에서 사용자 정의 오류 핸들러를 추가하여 오류 응답 처리](/help/forms/assets/custom-error-handler-message.png)

브라우저 콘솔을 열고 REST 서비스 엔드포인트가 수신한 응답과 헤더에서 유효성 검사 오류 메시지를 확인합니다.


사용자 정의 오류 핸들러 함수는 오류 응답을 기반으로 모달 대화 상자 표시하기 또는 분석 이벤트 보내기 등 추가 작업 실행을 담당합니다. 사용자 정의 오류 핸들러 기능은 특정 사용자 요구 사항에 맞게 오류 처리를 맞춤화하는 유연성을 제공합니다.

<!-- 

## Configure Adaptive Form submission to add custom handlers {#configure-adaptive-form-submission}

If the server validation error message does not display in the standard format, you can enable asynchronous submission and add a custom error handler on Adaptive Form submission to convert the message into a standard format.

### Configure asynchronous Adaptive Form submission {#configure-asynchronous-adaptive-form-submission}

Before adding custom handler, you must configure the adaptive form for asynchronous submission. Execute the following steps:

1. In adaptive form authoring mode, select the Form Container object and tap ![adaptive form properties](assets/configure_icon.png) to open its properties.
1. In the **[!UICONTROL Submission]** properties section, enable **[!UICONTROL Use asynchronous submission]**.
1. Select **[!UICONTROL Revalidate on server]** to validate the input field values on server before submission.
1. Select the Submit Action:

    * Select **[!UICONTROL Submit using Form Data Model]** and select the appropriate data model, if you are using RESTful web service based [form data model](work-with-form-data-model.md) as the data source.
    * Select **[!UICONTROL Submit to REST Service endpoint]** and specify the **[!UICONTROL Redirect URL/Path]**, if you are using RESTful web services as the data source.

    ![adaptive form submission properties](assets/af_submission_properties.png)

1. Tap ![Save](assets/save_icon.png) to save the properties.

### Add custom error handler on Adaptive Form submission {#add-custom-error-handler-af-submission}

AEM Forms provides out-of-the-box success and error handlers for form submissions. Handlers are client-side functions that execute based on the server response. When an Adaptive Form is submitted, the data is transmitted to the server for validation, which returns a response to the client with information about the success or error event for the submission. The information is passed as parameters to the relevant handler to execute the function.

Execute the following steps to add custom error handler on Adaptive Form submission:

1. Open an Adaptive Form in authoring mode, select any form object, and tap  to open the rule editor.
1. Select **[!UICONTROL Form]** in the Form Objects tree and tap **[!UICONTROL Create]**.
1. Select **[!UICONTROL Error in Submission]** from the Event drop-down list.
1. Write a rule to convert custom error structure to the standard error structure and tap **[!UICONTROL Done]** to save the rule.

The following is a sample code to convert a custom error structure to the standard error structure:

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys(errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

The `var som_map` lists the SOM expression of the Adaptive Form fields that you want to transform into the standard format. You can view the SOM expression of any field in an adaptive form by tapping the field and selecting **[!UICONTROL View SOM Expression]**.

Using this custom error handler, the adaptive form converts the fields listed in `var som_map` to standard error message format. As a result, the validation error messages display at field-level in the adaptive form.

 -->


## 참고 항목 {#see-also}

* [적응형 Forms(핵심 구성 요소)에서 사용자 지정 오류 핸들러 만들기 및 사용](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)
* [적응형 양식 기반의 독립 실행형 코어 구성 요소 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [양식에 맞는 스타일 또는 테마 만들기](/help/forms/using-themes-in-core-components.md)
* [적응형 양식을 만들거나 AEM Sites 페이지에 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
