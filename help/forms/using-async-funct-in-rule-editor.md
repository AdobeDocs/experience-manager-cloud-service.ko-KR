---
title: Visual Rule Editor에서 비동기 함수 호출을 사용하는 방법
description: Visual Rule Editor의 비동기 함수 호출
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
source-git-commit: f6e1de0c2cc2c056b3bfcea6ce5d7aaed041f6f8
workflow-type: tm+mt
source-wordcount: '1437'
ht-degree: 1%

---


# 핵심 구성 요소 기반 적응형 양식에서 비동기 기능 사용

적응형 Forms](/help/forms/rule-editor-core-components.md)의 [규칙 편집기는 비동기 기능을 지원하므로, 양식과의 사용자 상호 작용을 방해하지 않고 외부 프로세스나 데이터 검색을 기다리는 작업을 통합 및 관리할 수 있습니다.

## 비동기 또는 동기 함수의 사용을 결정하는 요소는 무엇입니까?

원활한 경험을 만들려면 사용자 상호 작용을 효과적으로 관리하는 것이 중요합니다. 작업을 처리하기 위한 두 가지 일반적인 접근 방식은 동기식 및 비동기식 기능입니다.

**동기 함수**&#x200B;는 작업을 차례로 실행하여 응용 프로그램이 각 작업이 완료될 때까지 기다린 후 계속 진행합니다. 이로 인해 특히 작업이 파일 업로드 또는 데이터 가져오기와 같은 외부 리소스를 기다리는 경우 지연되고 사용자 경험이 줄어들 수 있습니다.

예를 들어 사용자가 이미지를 업로드하면 전체 양식이 중지되어 업로드가 완료될 때까지 기다리는 시나리오를 생각해 보겠습니다. 이러한 일시 중지로 인해 사용자가 다른 필드와 상호 작용할 수 없어 좌절감과 지연이 발생합니다. 이미지가 처리되기를 기다리는 동안 다른 곳으로 이동하거나 인내심을 잃으면 입력된 정보가 손실되어 경험이 번거롭고 비효율적일 수 있습니다.

반면 **비동기 함수**&#x200B;를 사용하면 작업을 동시에 실행할 수 있습니다. 즉, 백그라운드 프로세스가 실행되는 동안 사용자는 애플리케이션과 계속 상호 작용할 수 있습니다. 비동기 작업을 수행하면 응답성이 향상되므로 사용자가 중단 없이 즉각적인 피드백을 받고 참여를 유지할 수 있습니다.

반대로 비동기 접근 방식을 사용하면 나머지 양식을 원활하게 작성하는 동시에 백그라운드에서 이미지를 업로드할 수 있습니다. 인터페이스는 응답형으로 유지되므로 업로드가 진행될 때 실시간 업데이트와 즉각적인 피드백을 제공할 수 있습니다. 사용자 참여를 강화하여 중단 없이 원활한 경험을 제공합니다.

![비동기 및 동기 함수](/help/forms/assets/sync-async.png){align=center}

## 적응형 Forms을 위한 비동기 기능 구현

규칙 편집기에서 다음 규칙 유형을 사용하여 적응형 Forms에 대한 비동기 기능을 구현할 수 있습니다.

* [비동기 함수 호출](#using-asynchronous-function-calls-in-the-visual-rule-editor)
* [함수 출력](#how-to-use-function-output-rule-type)

## 비동기 함수 호출 규칙 유형을 사용하는 방법

<span class="preview"> 이는 프리릴리스 기능이고 [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features)을 통해 액세스할 수 있습니다. </span>

비동기 작업을 위해 [사용자 지정 함수](/help/forms/custom-function-core-component-create-function.md)를 작성하고 규칙 편집기의 **[!UICONTROL 비동기 함수 호출]** 규칙 형식을 사용하여 비동기 함수를 구성할 수 있습니다.

### 사용 사례를 통해 비동기 함수 호출 규칙 유형 살펴보기

사용자가 일회용 암호(OTP)를 입력하는 웹 사이트의 등록 양식을 고려하십시오. 사용자 세부 정보를 추가하는 패널은 올바른 OTP를 입력한 후에만 나타납니다. OTP가 올바르지 않으면 패널이 숨겨지고 화면에 오류 메시지가 나타납니다.

![로그인 양식](/help/forms/assets/rule-editor-login-form.png) {width-50%}

등록 양식에서 사용자가 **확인** 단추를 클릭하면 입력한 OTP를 확인하기 위해 `matchOTP()` 함수가 비동기적으로 호출됩니다. `matchOTP()` 함수가 [사용자 지정 함수](/help/forms/custom-function-core-component-create-function.md)(으)로 구현되었습니다. 규칙 편집기의 **[!UICONTROL 비동기 함수 호출]** 규칙 유형을 사용하여 적응형 양식의 규칙 편집기에서 `matchOTP()` 함수를 구성할 수 있습니다. 규칙 편집기에서 성공 및 실패 콜백을 구현할 수도 있습니다.

다음 그림은 **[!UICONTROL 비동기 함수 호출]** 규칙 유형을 사용하여 적응형 Forms에 대한 비동기 함수를 호출하는 단계를 보여 줍니다.

![비동기 함수를 추가하는 워크플로우](/help/forms/assets/workflow-to-add-async-func.png){width=50%, align=center}

### 1. JS 파일의 비동기 작업에 대한 사용자 지정 함수 작성

>[!NOTE]
>
> * **비동기 함수 호출** 규칙 유형을 선택하면 양식의 규칙 편집기에 반환 형식이 `Promise`인 함수만 표시됩니다.
> * 사용자 지정 기능을 만드는 방법에 대해 알아보려면 [핵심 구성 요소를 기반으로 하는 적응형 양식에 대한 사용자 지정 기능 만들기](/help/forms/custom-function-core-component-create-function.md) 문서를 참조하십시오.

`matchOTP()` 함수는 사용자 지정 함수로 구현됩니다. 사용자 지정 함수의 JS 파일에 아래 코드가 추가됩니다.

```JavaScript
/**
 * generates the otp for success use case
 * @param {string} otp
 * @return {PROMISE}
 */
function matchOTP(otp) {
     return new Promise((resolve, reject) => {
        // Perform some asynchronous operation here
         asyncOperationForOTPMatch(otp, (error, result) => {
            if (error) {
                // On failure, call reject(error)
                reject(error);
            } else {
                // On success, call resolve(result)
                resolve(result);
            }
        });
    });
}

/**
 * generates the otp
 */
function asyncOperationForOTPMatch(otp, callback) {
    setTimeout(() => {
        if(otp === '111') {
            callback( null, {'valid':'true'});    
        } else {
            callback( {'valid':'false'}, null);
        }
    }, 1000);
}
```

이 코드는 OTP(일회용 암호)의 유효성을 비동기적으로 확인하는 약속을 생성하는 함수 `matchOTP()`을(를) 정의합니다. 함수 `asyncOperationForOTPMatch()`을(를) 사용하여 OTP 일치 프로세스를 시뮬레이션합니다. 함수는 제공된 OTP가 `111`과(와) 같은지 확인합니다. 입력한 OTP가 올바르면 오류에 대해 null이 있는 콜백을 호출하고 OTP가 유효함을 나타내는 개체는 `({'valid':'true'})`입니다. OTP가 유효하지 않으면 오류 개체가 `({'valid':'false'})`이고 결과에 대해 null이 있는 콜백을 호출합니다.

### 2. 규칙 편집기에서 비동기 기능 구성

규칙 편집기에서 비동기 기능을 구성하려면 다음 단계를 수행하십시오.

1. [비동기 함수 호출 규칙 유형을 사용하여 비동기 함수를 사용하는 규칙 만들기](#21-create-a-rule-to-use-asynchronous-function-using-the-async-function-call-rule-type)
1. [비동기 함수에 대한 콜백 구현](#22-implement-the-callbacks-for-asynchronous-function)

#### 2.1 비동기 함수 호출 규칙 유형을 사용하여 비동기 함수를 사용할 규칙을 만듭니다.

비동기 작업을 사용할 규칙을 만들려면 **[!UICONTROL 비동기 함수 호출]** 규칙 유형을 사용하십시오. 다음 단계를 수행하십시오.

1. 작성 모드에서 적응형 양식을 열고 양식 구성 요소를 선택한 다음 **[!UICONTROL 규칙 편집기]**&#x200B;를 선택하여 규칙 편집기를 엽니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. 단추 클릭에 대한 규칙의 **When** 섹션에 조건을 만듭니다. 예를 들어 **When[Confirm]**&#x200B;을 클릭합니다.
1. **Then** 섹션의 **작업 선택** 드롭다운 목록에서 **[!UICONTROL 비동기 함수 호출]**을 선택합니다.
**[!UICONTROL 비동기 함수 호출]**&#x200B;을(를) 선택하면 `Promise` 반환 형식의 함수가 나타납니다.
1. 목록에서 비동기 함수를 선택합니다. 예를 들어 `Add success callback` 및 `add failure callback`이(가) 나타나므로 `matchOTP()` 함수와 해당 콜백을 선택하십시오.
1. 이제 **[!UICONTROL 입력]** 바인딩을 선택하십시오. 예를 들어 **[!UICONTROL 입력]**&#x200B;을(를) `Form Object`(으)로 선택하고 `OTP` 필드와 비교합니다.

아래 스크린샷에는 규칙이 표시됩니다.

![규칙 유형](/help/forms/assets/asyn-function-rule-type.png)

이제 `matchOTP` 함수에 대한 콜백 `Success` 및 `Failure`의 구현을 계속할 수 있습니다.

#### 2.2 비동기 함수에 대한 콜백을 구현합니다

시각적 규칙 편집기를 사용하여 비동기 함수에 대한 성공 및 실패 콜백 메서드를 구현합니다.

**`Add Success callback` 메서드에 대한 규칙을 만듭니다**

OTP가 값 `111`과(와) 일치하는 경우 `userdetails` 패널을 표시하는 규칙을 만들어 보겠습니다.

1. **[!UICONTROL 성공 콜백 추가]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 문 추가]**&#x200B;를 클릭하여 규칙을 만듭니다.
1. 규칙의 **When** 섹션에 조건을 만듭니다.
1. **[!UICONTROL 함수 출력]** > **[!UICONTROL 이벤트 페이로드 가져오기]**&#x200B;를 선택합니다.

   >[!NOTE]
   >
   > **[!UICONTROL 이벤트 페이로드 가져오기]** 함수는 사용자 상호 작용을 동적으로 관리하기 위해 특정 이벤트와 관련된 데이터를 검색합니다.

1. **입력** 섹션에서 해당 바인딩을 선택합니다. 예를 들어 **[!UICONTROL 문자열]**&#x200B;을(를) 선택하고 `valid`을(를) 입력합니다. 입력한 문자열을 `true`과(와) 비교합니다.
1. **Then** 섹션의 **작업 선택** 드롭다운 목록에서 **[!UICONTROL 표시]**&#x200B;를 선택합니다. 예를 들어 `userdetails` 패널을 표시합니다.
1. **[!UICONTROL 문 추가]**&#x200B;를 클릭합니다.
1. **작업 선택** 드롭다운 목록에서 **[!UICONTROL 숨기기]**&#x200B;를 선택합니다. 예를들어 `error message` 텍스트 상자를 숨깁니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

![성공 호출](/help/forms/assets/rule-editor-success-callback.png){width=50%, height=50%}

사용자가 OTP를 `111`(으)로 입력하고 `Confirm` 단추를 클릭하면 `User Details` 패널이 표시되는 아래 스크린샷을 참조하십시오.

![성공](/help/forms/assets/success.gif)

**`Add Failure callback` 메서드에 대한 규칙을 만듭니다**

OTP가 값 `111`과(와) 일치하지 않는 경우 오류 메시지를 표시하는 규칙을 만들어 보겠습니다.

1. **[!UICONTROL 실패 콜백 추가]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 문 추가]**&#x200B;를 클릭하여 규칙을 만듭니다.
1. 규칙의 **When** 섹션에 조건을 만듭니다.
1. **[!UICONTROL 함수 출력]** > **[!UICONTROL 이벤트 페이로드 가져오기]**&#x200B;를 선택합니다.
1. **입력** 섹션에서 해당 바인딩을 선택합니다. 예를 들어 **[!UICONTROL 문자열]**&#x200B;을(를) 선택하고 `valid`을(를) 입력합니다. 입력한 문자열을 `false`과(와) 비교합니다.
1. **Then** 섹션의 **작업 선택** 드롭다운 목록에서 **[!UICONTROL 표시]**&#x200B;를 선택합니다. 예를들어 `error message` 텍스트 상자를 표시합니다.
1. **[!UICONTROL 문 추가]**&#x200B;를 클릭합니다.
1. **작업 선택** 드롭다운 목록에서 **[!UICONTROL 숨기기]**&#x200B;를 선택합니다. 예를 들어 `userdetails` 패널을 숨깁니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

![실패 콜백 메서드](/help/forms/assets/rule-editor-failure-callback.png){width=50%, height=50%}

사용자가 OTP를 `123`(으)로 입력하고 `Confirm` 단추를 클릭하면 오류 메시지가 표시되는 아래 스크린샷을 참조하십시오.

![실패](/help/forms/assets/failure.gif)

아래 스크린샷에는 **[!UICONTROL 비동기 함수 호출]**&#x200B;을 사용하여 비동기 함수를 구현하기 위한 전체 규칙이 표시됩니다.

비동기 함수 호출에 대한 ![규칙](/help/forms/assets/rule-editor-async-callbacks.png)

**[!UICONTROL 성공 콜백 편집]** 및 **[!UICONTROL 실패 콜백 편집]**&#x200B;을 클릭하여 콜백을 편집할 수도 있습니다.

## 함수 출력 규칙 유형을 사용하는 방법

동기 함수를 사용하여 비동기 함수를 간접적으로 호출할 수도 있습니다. 동기 함수는 적응형 양식의 규칙 편집기에서 **[!UICONTROL 함수 출력]** 규칙 유형을 사용하여 실행됩니다.

**[!UICONTROL 함수 출력]** 규칙 유형을 사용하여 비동기 함수를 호출하는 방법을 보려면 아래 코드를 참조하십시오.

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

작동 여부를 확인하기 위해 단추를 추가하고 단추 클릭 시 비동기 함수를 호출하는 단추에 대한 규칙을 만들어 보겠습니다.

![비동기 함수에 대한 규칙을 만드는 중](/help/forms/assets/rule-for-async-funct.png){width=50%}

사용자가 `Fetch` 단추를 클릭할 때 사용자 지정 함수 `callAsyncFunction`이(가) 호출되어 비동기 함수 `asyncFunction`이(가) 호출되는지 보여 주려면 아래 콘솔 창의 스크린샷을 참조하십시오. Inspect 콘솔 창에서 버튼에 대한 응답을 봅니다. 클릭:

![콘솔 창](/help/forms/assets/async-custom-funct-console.png)

## 추가 참조

{{see-also-rule-editor}}