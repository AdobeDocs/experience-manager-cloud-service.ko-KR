---
title: 규칙을 사용하여 양식에 동적 비헤이비어 추가
description: AEM Forms용 Edge Delivery Services는 최고의 성능을 발휘하도록 구축되어 데이터 수집 및 사용자 참여를 간소화하는 미래를 구상할 수 있도록 지원합니다. 규칙을 사용하여 내 양식에 동적 비헤이비어를 추가합니다.
feature: Edge Delivery Services
exl-id: 58042016-e655-446f-a2bf-83f1811525e3
role: Admin, Architect, Developer
source-git-commit: 4a8153ffbdbc4da401089ca0a6ef608dc2c53b22
workflow-type: ht
source-wordcount: '2218'
ht-degree: 100%

---

# 규칙을 사용하여 내 양식에 동적 비헤이비어 추가

스프레드시트를 사용하여 양식을 만드는 강력한 기능 중 하나는 기본 제공 스프레드시트 기능을 사용하여 규칙을 만들 수 있고, 조건부로 양식 필드를 표시하거나 숨길 수 있으며, 사용자 입력을 기반으로 계산을 자동화하고 보다 동적인 사용자 환경을 만들 수 있다는 점입니다.

이 문서에서는 다양한 적응형 양식 블록 속성 중 [`Visible`](#visible-property), [`Visibility Expression`](#visible-expression-property) 및 [`Value Expression`](#value-expression-property) 속성과 [스프레드시트 기능](#spreadsheet-functions-for-rules)을 사용하여 양식에 효과적인 규칙을 만드는 방법을 안내합니다. 이러한 규칙이 실제로 어떻게 구현될 수 있는지 설명하는 몇 가지 예도 살펴봅니다.

## 규칙의 구성 이해

규칙은 다양한 상황에서 무엇을 해야 하는지 알려 주는 지침과 같습니다. 규칙은 일반적으로 다음과 같은 구성됩니다.

* 조건: 규칙이 적용되는 상황을 지정합니다. 대답이 필요한 질문(예 또는 아니요)으로 생각합니다.

* 액션: 조건이 충족되거나(true) 충족되지 않을 때(false) 발생하는 액션을 정의합니다.


예를 들어 확인란을 선택하면 이메일 상자를 표시할 수 있습니다.

* 조건: “잡지 및 활동을 구독하시겠습니까?” 확인란이 선택됩니다. (예 또는 아니요?). 이 조건은 양식의 `Visible` 속성에서 설정됩니다.
* 액션(True): 이메일 상자가 표시됩니다. (예를 선택하면 어떻게 됩니까?). `Visibility Expression`은 `visible` 속성에 대해 정의된 조건을 사용하여 필드를 동적으로 표시합니다.
* 액션(False): 이메일 상자가 숨겨집니다. (아니요를 선택하면 어떻게 됩니까?). `Visibility Expression`은 `Value`에 대해 정의된 조건을 사용하여 필드를 동적으로 숨깁니다.

자세한 단계별 지침은 [조건에 따라 이메일 표시/숨기기](#example-1-conditional-email-field) 필드를 참조하십시오


## 값, 표시, 가시성 표현식 및 값 표현식 속성 이해

### 표시 속성

양식 필드에 대한 조명 스위치를 상상해 보십시오. `Visible` 속성은 스위치와 같아서 필드가 처음 로드될 때 양식에 처음 표시 여부를 제어합니다.

* True(조명 스위치가 “켜진 상태”): 필드가 양식에 표시됩니다.
* False(조명 스위치가 “꺼진 상태”): 필드가 양식에서 숨겨집니다.

스프레드시트 공식(= 태그 포함)을 사용하면 스프레드시트와 같은 논리를 사용하여 공식을 작성하고 필드의 가시성을 결정할 수 있습니다. 이 공식 내에서 양식의 다른 필드 값을 사용할 수 있습니다. 예를 들어 사용자가 등록 유형 필드에서 “개인 사용자”를 선택하면 해당 값을 확인하는 공식을 사용하여 이메일 필드를 숨길 수 있습니다.

### 표시 표현식 속성(필드 표시/숨기기)

`Visible Expression` 속성을 사용하면 `Visible` 속성에 추가된 규칙을 사용하여 사용자 상호 작용을 기반으로 필드를 표시할지 숨길지 결정할 수 있습니다.

`=FORMULATEXT("Address of the corresponding Visible property)`를 사용하여 `Visible` 속성에 언급된 공식을 문자열로 `Visible Expression` 속성 필드에 가져옵니다. 게시된 양식에서 필드를 동적으로 표시/숨기기 위해서는 이 작업이 필요합니다.

![Forumaltext](/help/edge/assets/aem-forms-formulatext.png)

### 값 속성(초기 데이터 설정)

방 조명의 조광기 스위치에 사전 설정된 값이 있다고 상상해 보십시오. `Value` 속성이 유사하여 사용자가 필드에서 보는 데이터의 초기 상태를 결정합니다.  양식 필드 내에 표시되는 현재 데이터를 설정하거나 검색합니다.

양식이 처음 로드되면 `Value` 속성은 사용자가 변경하기 전에 필드에 표시되는 내용을 지정합니다. 가시성을 제어하는 `Visible` 및 `Visible Expression` 속성과 달리 값 속성은 데이터 자체에 직접적인 영향을 미칩니다. 사용자가 옵션(드롭다운 메뉴)을 입력하거나 선택 또는 필드와 상호 작용하여 이 값을 수정할 수 있습니다.

Excel 수식(= 태그 포함)을 사용하면 스프레드시트와 같은 논리를 사용하여 공식을 작성하고 필드에 표시되는 값을 결정할 수 있습니다. 이 공식 내에서 양식의 다른 필드 값을 사용할 수 있습니다. 예를 들어 다른 필드에 입력한 주문 금액을 기반으로 자동으로 할인 금액을 계산할 수 있습니다.


### 값 표현식 속성(필드에 표시할 값 계산)

이 속성을 사용하면 표시 표현식과 같이 공식을 기반으로 필드 내에 표시되는 값을 제어할 수 있습니다. 필드에 계산기가 내장되어 있다고 상상해 보십시오.

`=FORMULATEXT("Address of the corresponding Value property)`를 사용하여 `Value` 속성에 언급된 공식을 문자열로 `Value Expression` 속성 필드에 가져옵니다. 계산된 값을 게시된 양식으로 동적 계산하고 표시하는 데 이 작업이 필요합니다.

![Forumaltext](/help/edge/assets/aem-forms-formulatext-value.png)

다음은 이러한 개념을 강화하기 위한 유사점입니다.

* 표시: 집과 같은 양식을 상상해 보십시오. “표시” 속성은 각 방(필드)의 조명 스위치와 같습니다. 누군가가 집에 들어왔을 때(양식을 열 때) 처음에 방 조명이 켜져 있는지(표시) 꺼져 있는지(숨김) 여부를 결정합니다.
* 표시 표현식: 이것은 동작 센서 조명 스위치와 같습니다. 방(필드)이 처음에는 어두울 수 있지만(숨김) 누군가가 지나가면(다른 필드의 값을 변경하면) 공식(동작 센서)을 방 조명(필드 표시)을 켤 수 있습니다.
* 값: 조명(필드의 초기 데이터)에 대해 미리 설정된 조광기 스위치와 같습니다. 그런 다음 사용자는 명도를 조정(값 수정)할 수 있습니다.
* 값 표현식: 집(양식)에 있는 제품의 가격표에 내장된 고급 계산기와 같습니다. 가격표(필드)에는 기준 가격(다른 필드의 값)처럼 그 밖의 정보를 사용하는 공식(예: 기준 가격에 세금을 추가하는 것)을 기반으로 최종 가격이 표시됩니다.

이러한 속성을 [스프레드시트 기능](#spreadsheet-functions-for-rules)과 결합하면 양식 내에서 다양한 동적 비헤이비어를 달성할 수 있습니다.

## 규칙에 대한 스프레드시트 기능

적응형 양식 블록은 규칙을 만드는 데 사용할 수 있는 다양한 스프레드시트 기능을 지원합니다. 다음은 기본(OOTB)으로 사용할 수 있는 함수입니다.

### 논리 함수

* [NOT()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018452_715980110): 논리 상태를 반전합니다(TRUE는 FALSE가 되고 그 반대도 됩니다).
* [AND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#AND): 지정한 모든 조건이 TRUE인 경우에만 TRUE를 반환합니다.
* [OR()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#OR): 지정한 조건 중 하나 이상이 TRUE이면 TRUE를 반환합니다.

### 조건부 함수

* [IF()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018446_715980110): 조건을 평가하고 TRUE인 경우 특정 값을 반환하고 FALSE인 경우 다른 값을 반환합니다.

### 수학 함수

* [SUM()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#SUM): 지정된 셀 범위의 값을 추가합니다.
* [ROUND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#ROUND): 숫자를 특정 소수 자릿수로 반올림합니다.
* [MIN()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#MIN): 지정된 셀 범위에서 가장 작은 값을 반환합니다.

## 규칙 만들기

규칙을 사용하여 양식을 개선하는 방법을 설명하기 위해 몇 가지 실제 예를 살펴보겠습니다.

## 예 1: 조건부 이메일 필드

이 예에서는 확인란이 조건으로 작동하는 방식을 보여 줍니다. 이 옵션을 선택하면(조건은 true) 이메일 상자가 나타납니다(true에 대한 액션). 선택하지 않은 경우(조건이 false) 이메일 상자가 숨김 상태로 유지됩니다(false에 대한 액션).

아래 이미지에 표시된 것처럼 확인란과 이메일 상자가 있는 양식을 만듭니다.

![조건부 이메일 양식](/help/edge/assets/aem-forms-conditional-email-form.png)


확인란 선택 시 이메일 필드를 표시하는 규칙을 사용하는 방법은 다음과 같습니다.

1. 확인란 필드의 `Value` 속성을 `TRUE`로 설정합니다.
1. 확인란 필드의 `Checked` 속성을 `FALSE`로 설정합니다. 이렇게 하면 기본적으로 확인란이 선택되지 않습니다.
1. 이메일 필드의 `Visible` 속성을 `=[address of Checked property of the checkbox field] = true()`로 설정합니다. 예, `=Q11=TRUE()`. 확인란이 선택되었는지 여부에 따라 공식이 평가됩니다. 확인란이 선택되면 수식이 TRUE로 평가됩니다. 확인란이 선택되지 않으면 공식이 FALSE로 평가됩니다.



   `Checked` 속성을 가리키도록 설정했을 때 `TRUE()` 함수가 논리값을 반환하고 `checked = false`이면 false를 반환합니다. `checked=true`이면 `true`를 반환합니다. 이렇게 하면 기본적으로 이메일 필드가 숨겨집니다.


1. 확인란 필드의 `Visible Expression` 속성을 `=FORMULATEXT ((address of Visible property of the checkbox field))`로 설정합니다. 예, `=FORMULATEXT((G12))`. FORMULATEXT() 함수는 공식을 입력으로 사용하고 공식 자체를 텍스트 문자열로 반환합니다. 양식의 공식을 사용하는 데 도움이 됩니다.

   ![조건부 이메일 필드](/help/edge/assets/aem-forms-visible-expression-formula-text.png)

1. 내 양식을 미리 보고 게시합니다. 이제 확인란을 선택하면 이메일 필드가 표시되고 선택 취소하면 필드가 숨겨져서 동적 사용자 환경이 제공됩니다.

   ![조건부 이메일](/help/edge/assets/aem-forms-coditional-email.gif)


## 예 2: 자동 계산

이 예는 양식에서 여행 날짜를 선택할 때 예상 여행 비용을 자동으로 계산하는 방법을 보여 줍니다.

아래 이미지에 표시된 대로 날짜 필드, 객실 예산, 예상 여행 비용 필드 및 이메일 상자가 있는 양식을 만듭니다.

![조건부 이메일 양식](/help/edge/assets/aem-forms-automatic-calculations-form.png)

자동 계산을 사용하여 예상 여행 비용을 표시하는 방법은 다음과 같습니다.

1. `amount` 필드의 `Value` 속성을 `=F6*DAYS(F3,F2)`로 설정합니다. 이 공식은 `Start Date` 및 `End Date`에서 일수를 계산하고, 객실 예산에 일수를 곱하여 `Estimated Trip Cost` 필드에 결과를 표시합니다.

1. `Estimated Trip Cost` 필드의 `Value Expression` 속성을 `=FORMULATEXT ((address of value property of the amount field))`로 설정합니다. 예, `=FORMULATEXT(F7)`. FORMULATEXT() 함수는 공식을 입력으로 사용하고 공식 자체를 텍스트 문자열로 반환합니다. 양식의 공식을 사용하는 데 도움이 됩니다.

1. 내 양식을 미리 보고 게시합니다. 이제 `Start Date`, `End Date` 및 객실 예산을 지정합니다. `Estimated Trip Cost`는 자동으로 계산됩니다.

## 스프레드시트 함수 예


다음은 일반적으로 사용되는 스프레드시트 함수의 몇 가지 예입니다.

**논리 함수:**

* **NOT():** 논리적 상태를 반전합니다(TRUE는 FALSE가 되고 그 반대도 됩니다).

  예: 이메일 필드가 비어 있으면 “이메일 확인” 필드 숨기기.

   1. “이메일 확인”의 `Visible` 속성을 `=NOT(if('address of email field'=""))`으로 설정합니다.

      ![AEM Forms 이메일 확인 필드 숨기기](/help/edge/assets/aem-forms-not-function-hide-email-field.png)


   1. “이메일 확인” 필드의 보기 표현식을 `=FORMULATEXT ((address of visible property of the Confirm Email field))`로 설정합니다.

      ![AEM Forms 표시 표현식 공식](/help/edge/assets/aem-forms-visible-expression-formula-text.png)


* AND(): 지정한 모든 조건이 TRUE인 경우에만 TRUE를 반환합니다.

   * 예: 모든 필수 필드가 입력된 경우에만 “제출” 버튼 활성화.

   1. “제출” 버튼의 `Visible` 속성을 다음과 같이 설정합니다.



      ```JavaScript
      =AND(NOT(address of `value` property of the `name` field = ""), NOT(address of `value` property of the `email` field = ""), NOT(address of `value` property of the `phone` field))
      ```

      예:

      ```JavaScript
      =AND(NOT(F9=""), NOT(F12=""), NOT(F10=""))
      ```

   1. “이메일 확인” 필드의 보기 표현식을 다음으로 설정합니다.

      ```JavaScript
      =FORMULATEXT ((address of visible property of the Confirm Email field))
      ```

      예:

      ```JavaScript
      =FORMULATEXT(G14)
      ```

      이 공식은 모든 필드(이름, 이메일, 전화번호)가 채워진 경우에만 “제출” 버튼(TRUE)을 표시하고(NOT()은 각 필드에 대해 TRUE를 반환), 그렇지 않으면 버튼(AND(다수 FALSES) = FALSE)을 숨깁니다.

* OR(): 지정한 조건 중 하나 이상이 TRUE이면 TRUE를 반환합니다.

   * 예: 사용자가 해당 할인 쿠폰 코드 중 하나를 입력하면 할인 적용.

   1. “최종 금액” 필드의 `Visible` 속성을 다음과 같이 설정합니다.


  ```JavaScript
     =IF(OR(F14="BlackFridaySale", F14="NewYearDiscount"), (F6*DAYS(F3,F2)* 0.7) , (F6*DAYS(F3,F2)))
  ```

   1. “이메일 확인” 필드의 값 표현식을 다음으로 설정합니다.

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      예:

      ```JavaScript
      =FORMULATEXT(F7)
      ```

      이 공식은 사용자가 쿠폰 코드(couponCode = “NewYearDiscount”) 또는 OR(couponCode = “BlackFridaySale”)를 입력하면 30% 할인을 계산하고, 그렇지 않으면 할인을 0으로 설정합니다.

**텍스트 함수:**

* IF(): 조건을 평가하고 TRUE인 경우 특정 값을 반환하고 FALSE인 경우 다른 값을 반환합니다.

   * 예: 선택한 제품 카테고리에 따라 사용자 정의 메시지 표시.

   1. `message` 필드의 `Value` 속성을 `Only upto 7 kg check-in lagguage is allowed!`로 설정합니다.

   1. `message` 필드의 `Visible` 속성을 다음으로 설정합니다.


      ```JavaScript
      =if(address of value property of chosen product category ="Economy", TRUE(), FALSE())
      ```

      예:

      ```JavaScript
      =if(F5="Economy", TRUE(), FALSE())
      ```

   1. `message` 필드의 값 표현식을 다음과 같이 설정합니다.

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      예:

      ```JavaScript
      =FORMULATEXT(G15)
      ```

      이 공식은 “수하물 위탁은 최대 7kg까지만 허용됩니다!”라는 메시지를 표시합니다. 선택한 클래스가 “이코노미”인 경우이고 그렇지 않으면 메시지 필드를 비워 둡니다.

**수학 함수:**

* SUM(): 지정된 셀 범위의 값을 추가합니다.

  예: 장바구니에 담긴 물품의 총 비용 계산.

  “총 비용” 필드의 값 표현식에서:
SUM(가격 * 수량)

  이 공식은 각 항목의 “가격”과 “수량”에 대한 별도의 필드가 있다고 가정합니다. 이를 곱하고 SUM()을 사용하여 장바구니에 있는 모든 물품의 총 비용을 합산합니다.

* ROUND(): 숫자를 특정 소수 자릿수로 반올림합니다.

  예: 계산된 할인 금액을 소수점 두 자리로 반올림.

  “할인 금액” 필드의 값 표현식에서(할인이 다른 곳에서 계산된 것으로 가정):
ROUND(discount, 2)

  이 공식은 할인 값을 소수점 두 자리로 반올림합니다.

* MIN(): 지정된 셀 범위에서 가장 작은 값을 반환합니다.

  예: 선택한 국가를 기준으로 가입 양식에 필요한 최소 연령 찾기.

  “최소 연령” 필드의 값 표현식에서:
MIN(ageLimits[“US”], ageLimits[“UK”], ageLimits[“France”])

  이 공식에서는 여러 국가의 최소 연령 요구 사항을 저장하는 “ageLimits”라는 테이블이 있다고 가정합니다. MIN()을 사용하여 그 중에서 가장 작은 값을 찾습니다.


또한 적응형 양식 블록을 사용하면 [사용자 정의 함수](#creating-custom-functions)를 만들어 양식을 완전히 관리할 수 있습니다. 사용자 정의 함수를 사용하면 자신만의 규칙과 논리를 정의할 수 있어 양식 작동 방식을 완벽하게 제어할 수 있습니다.


## 사용자 정의 함수 만들기 및 배포

기본(OOTB) 적응형 양식 블록은 다양한 [일반 스프레드시트 함수](#spreadsheet-functions-for-rules)를 구현합니다. 그러나 양식을 보다 세분화하여 제어하기 위해 적응형 양식 블록 내에서 Microsoft® Excel 또는 Google 시트에서 사용할 수 있는 모든 기본(OOTB) 함수를 사용할 수 있습니다. 적응형 양식 블록에는 Microsoft® Excel 또는 Google 시트에서 사용할 수 있는 모든 기본(OOTB) 함수 구현이 포함되어 있지 않습니다. 이러한 함수가 필요한 경우 비슷한 구문으로 사용자 정의 함수를 개발하여 Microsoft® Excel 또는 Google 시트에서 제공하는 기능을 구현할 수 있습니다. 예를 들어 [Microsoft® Excel&#39;s Year() 함수](https://support.microsoft.com/ko/office/calculate-age-113d599f-5fea-448f-a4c3-268927911b37#)를 구현하여 출생일로부터 나이를 계산할 수 있습니다.


### 사용자 정의 함수 만들기

사용자 정의 함수는 `[Adaptive form block]/functions.js` 파일에 있습니다. 만들기 프로세스에는 일반적으로 다음 단계가 포함됩니다.

* 함수 선언: 함수 이름과 함수의 매개변수(허용되는 입력)를 정의합니다.
* 논리 구현: 함수에 의해 수행되는 특정 계산이나 조작을 개략적으로 설명하는 코드를 작성합니다.
* 함수 내보내기: 해당 파일에서 함수를 내보내 규칙에서 액세스할 수 있도록 합니다.

### 예: 연도 함수

이 예는 Microsoft® Excel&#39;s YEAR() 함수를 모방하여 나이를 계산하는 두 가지 사용자 정의 함수를 보여 줍니다.


```JavaScript
/**
 * Get the current date and time
 * @name now
 * @returns {Date} The current date and time as a Date object
 */
function now() {
  const today = new Date();
  return today;
}

/**
 * Get the year from a Date object
 * @name year
 * @param {Date} date The date object
 * @throws {TypeError} If the input is not a Date object
 * @returns {number} The year as a number
 */
function year(date) {
  let inputDate = new Date(date)

  if (!(inputDate instanceof Date)) {
    throw new TypeError("Input must be a Date object");
  }

  const year = inputDate.getFullYear();

  return year;
}

// Make the function accessible for use in rules
export { now, year };
```

### 내 양식의 사용자 정의 함수 사용

내 양식의 사용자 정의 함수를 사용하려면:

1. **함수 추가**: 사용자 정의 함수를 `[Adaptive form block]/functions.js` 파일에 포함시킵니다. 파일 내 내보내기 구문에 추가해야 합니다.
1. **파일 배포**: 업데이트된 `functions.js` 파일을 GitHub 프로젝트에 배포하고 빌드되었는지 확인합니다.
1. **함수 사용**: 기본(OOTB) 지원하는 다른 스프레드시트 기능과 유사하게 `Value`, `Value Expression`, `Visible` 또는 `Visible Expression` 속성을 사용하여 양식 스프레드시트 내의 함수에 액세스합니다.
1. **양식 미리보기**: AEM Sidekick을 사용하여 새로 구현된 함수가 포함된 양식을 미리 봅니다.

