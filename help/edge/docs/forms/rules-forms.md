---
title: 규칙을 사용하여 양식에 동적 동작 추가
description: 최고 성능을 위해 구축된 AEM Forms Edge Delivery Services을 통해 간소화된 데이터 수집 및 사용자 참여의 미래를 구상할 수 있습니다. 규칙을 사용하여 양식에 동적 동작을 추가하십시오.
feature: Edge Delivery Services
exl-id: 58042016-e655-446f-a2bf-83f1811525e3
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '2216'
ht-degree: 0%

---

# 규칙을 사용하여 양식에 동적 동작 추가

스프레드시트를 사용하여 양식을 작성할 때의 강력한 기능 중 하나는 기본 제공 스프레드시트 기능을 사용하여 규칙을 작성할 수 있으므로 양식 필드를 조건부로 표시하거나 숨기고, 사용자 입력을 기반으로 계산을 자동화하고, 보다 역동적인 사용자 경험을 작성할 수 있습니다.

이 문서에서는 주로 다양한 적응형 양식 블록 속성을 사용하는 방법을 안내합니다 [`Visible`](#visible-property), [`Visibility Expression`](#visible-expression-property) 및 [`Value Expression`](#value-expression-property) 속성과 함께 [스프레드시트 함수](#spreadsheet-functions-for-rules) 을 사용하여 양식에 대한 효과적인 규칙을 만들 수 있습니다. 이러한 규칙을 실제로 구현하는 방법을 보여 주는 몇 가지 예도 살펴봅니다.

## 규칙의 구성 이해

규칙은 우리에게 다른 상황에서 무엇을 해야 하는지를 알려주는 지시와 같다. 규칙에는 일반적으로 다음 구문이 있습니다.

* 조건 : 규칙이 적용되는 상황을 지정합니다. 답변이 필요한 질문으로 생각하십시오(예 또는 아니요).

* 작업: 조건이 충족되거나(true) 충족되지 않을 때(false) 발생하는 작업을 정의합니다.


예를 들어 확인란을 선택한 경우 이메일 상자를 표시하려면 다음을 수행합니다.

* 조건: &quot;Magazine &amp; Activities에 구독하시겠습니까?&quot; 확인란이 선택되어 있습니다. (예, 아니요). 이 조건은 다음에 설정됩니다. `Visible` 폼의 속성입니다.
* 작업(True): 전자 메일 상자가 표시됩니다. (해당되는 경우 어떻게 됩니까). 다음 `Visibility Expression`  다음에 대해 정의된 조건 사용 `visible` 필드를 동적으로 표시하는 속성입니다.
* 작업(False): 전자 메일 상자가 숨겨집니다. (없는 경우 어떻게 됩니까). 다음 `Visibility Expression`  다음에 대해 정의된 조건 사용 `Value` 필드를 동적으로 숨깁니다.

자세한 단계별 지침은 [조건에 따라 이메일 필드 표시/숨기기](#example-1-conditional-email-field)


## 값, 표시, 가시성 표현식 및 값 표현식 속성 이해

### 표시 속성

양식 필드에 대한 조명 스위치를 상상해 보십시오. 다음 `Visible` 속성은 해당 스위치와 유사하며, 필드가 처음 로드될 때 폼에 표시되는지 여부를 제어합니다.

* True(조명 스위치가 &quot;켜짐&quot;인 것처럼): 필드가 양식에 표시됩니다.
* False(예: 조명 스위치가 &quot;꺼짐&quot;인 경우): 양식에서 필드가 숨겨집니다.

SpreadSheet 공식( = 태그 포함)을 사용하여 스프레드시트와 유사한 논리를 사용하여 공식을 작성하여 필드의 가시성을 결정할 수 있습니다. 이 수식 내에서 양식의 다른 필드 값을 사용할 수 있습니다. 예를 들어 사용자가 등록 유형 필드에서 &quot;개인&quot;을 선택하는 경우 해당 값을 확인하는 공식을 사용하여 이메일 필드를 숨길 수 있습니다.

### 표시 표현식 속성(필드 표시/숨기기)

다음 `Visible Expression` 속성은에 추가된 규칙을 사용할 수 있도록 합니다. `Visible` 속성을 사용하여 사용자 상호 작용에 따라 필드를 표시할지 또는 숨길지 여부를 결정합니다.

사용 `=FORMULATEXT("Address of the corresponding Visible property)` 에 언급된 공식을 가져오려면 `Visible` 속성을 문자열로 사용 `Visible Expression` 속성 필드. 게시된 양식에서 필드를 동적으로 표시/숨기는 데 필요합니다.

![Forumaltext](/help/edge/assets/aem-forms-formulatext.png)

### 값 속성(초기 데이터 설정)

방 조명의 조광기 스위치에 미리 설정된 값을 상상해 보세요. 다음 `Value` 속성은 필드에 표시되는 데이터의 초기 상태를 결정하는 것과 유사합니다.  양식 필드 내에 표시된 현재 데이터를 설정하거나 검색합니다.

양식이 처음 로드될 때 `Value` 속성은 변경하기 전에 필드에 표시되는 내용을 나타냅니다. 좋아하지 않음 `Visible` 및 `Visible Expression` 가시성을 제어하는 속성에서는 Value 속성이 데이터 자체에 직접 영향을 줍니다. 사용자는 입력, 옵션 선택(드롭다운 메뉴) 또는 필드와 상호 작용하여 이 값을 수정할 수 있습니다.

Excel 공식( = 태그 포함)을 사용하여 스프레드시트와 유사한 논리를 사용하여 공식을 작성하여 필드에 표시되는 값을 결정할 수 있습니다. 이 수식 내에서 양식의 다른 필드 값을 사용할 수 있습니다. 예를 들어 다른 필드에 입력한 주문 금액을 기준으로 자동으로 할인을 계산할 수 있습니다.


### 값 표현식 속성(필드에 표시될 값 계산)

이 속성을 사용하면 표시 표현식과 유사하게 수식을 기반으로 필드 내에 표시되는 값을 제어할 수 있습니다. 계산기가 현장에 내장되어 있다고 상상해 보세요.

사용 `=FORMULATEXT("Address of the corresponding Value property)` 에 언급된 공식을 가져오려면 `Value` 속성을 문자열로 사용 `Value Expression` 속성 필드. 게시된 양식에서 계산된 값을 동적으로 계산하고 표시하는 데 필요합니다.

![Forumaltext](/help/edge/assets/aem-forms-formulatext-value.png)

이러한 개념을 확고히 하기 위한 비유는 다음과 같습니다.

* 보이는 것: 집 같은 형태를 상상해 보세요. &quot;보이는&quot; 속성은 각 룸(필드)의 조명 스위치와 같습니다. 누군가 집 안으로 들어왔을 때(양식을 열었을 때) 방이 처음에 켜져 있는지(표시되는지) 아니면 어둡게(숨겨지는지) 결정합니다.
* 표시 표현식: 모션 센서 조명 스위치와 같습니다. 룸(필드)은 처음에 어둡게(숨겨짐) 보일 수 있지만, 누군가 지나가면(다른 필드의 값을 변경하면) 수식(모션 센서)이 이를 설정(필드 표시)할 수 있습니다.
* 값: 이것은 조명에 대해 미리 설정된 조광기 스위치와 같습니다(필드의 초기 데이터). 그런 다음 사용자가 밝기를 조정(값 수정)할 수 있습니다.
* 값 표현식: 주택(양식)의 가격표에 내장된 고급 계산기와 같습니다. 가격 태그(필드)는 기본 가격(다른 필드의 값)과 같은 다른 정보를 사용하는 공식(예: 기본 가격에 세금 추가)을 기반으로 최종 가격을 표시합니다.

이러한 속성을 와 결합하여 [스프레드시트 함수](#spreadsheet-functions-for-rules), 양식 내에서 광범위한 동적 동작을 수행할 수 있습니다.

## 규칙용 스프레드시트 함수

적응형 Forms 블록은 규칙을 만드는 데 사용할 수 있는 다양한 스프레드시트 기능을 지원합니다. 기본 제공(OOTB)으로 사용할 수 있는 함수는 다음과 같습니다.

### 논리 함수

* [NOT()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018452_715980110): 논리 상태를 반대로 바꿉니다(TRUE는 FALSE가 되고 그 반대).
* [AND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#AND): 지정된 모든 조건이 TRUE인 경우에만 TRUE를 반환합니다.
* [OR()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#OR): 지정된 조건 중 하나 이상이 TRUE이면 TRUE를 반환합니다.

### 조건부 함수

* [IF()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018446_715980110): 조건을 평가하고 TRUE인 경우 특정 값을 반환하고 FALSE인 경우 다른 값을 반환합니다.

### 수학 함수

* [SUM()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#SUM): 지정된 셀 범위에서 값을 추가합니다.
* [ROUND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#ROUND): 숫자를 지정된 소수 자릿수로 반올림합니다.
* [MIN()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#MIN): 지정된 셀 범위에서 가장 작은 값을 반환합니다.

## 규칙 만들기

규칙을 사용하여 양식을 향상시키는 방법을 설명하기 위한 몇 가지 실제 예를 살펴보겠습니다.

## 예제 1: 조건부 이메일 필드

이 예에서는 확인란이 조건으로 작동하는 방식을 보여 줍니다. 이 옵션을 선택하면(조건이 true인 경우) 이메일 상자가 나타납니다(true인 경우 작업). 선택하지 않으면(조건이 false임) 이메일 상자가 숨겨진 상태로 유지됩니다(false에 대한 작업).

아래 이미지에 표시된 대로 확인란과 전자 메일 상자를 사용하여 양식을 만듭니다.

![조건부 전자 메일 양식](/help/edge/assets/aem-forms-conditional-email-form.png)


규칙을 사용하여 확인란 선택에 대한 이메일 필드를 표시하는 방법은 다음과 같습니다.

1. 설정 `Value` 확인란 필드의 속성 `TRUE`.
1. 설정 `Checked` 확인란 필드의 속성 `FALSE`. 이렇게 하면 기본적으로 확인란이 선택되지 않습니다.
1. 설정 `Visible` 다음으로 전자 메일 필드의 속성: `=[address of Checked property of the checkbox field] = true()`. 예 `=Q11=TRUE()`. 공식은 확인란이 선택되었는지 여부에 따라 평가됩니다. 확인란을 선택하면 공식이 TRUE로 평가됩니다. 확인란을 선택하지 않으면 공식이 FALSE로 평가됩니다.



   다음 `TRUE()` 함수는 논리적 값을 가리키도록 설정할 때 반환합니다. `Checked` 속성입니다. `checked = false` false를 반환합니다. If `checked=true`를 반환합니다. `true`. 이렇게 하면 기본적으로 이메일 필드가 숨겨집니다.


1. 설정 `Visible Expression` 확인란 필드의 속성 `=FORMULATEXT ((address of Visible property of the checkbox field))`. 예, `=FORMULATEXT((G12))`. FORMULATEXT() 함수는 수식을 입력으로 취하여 수식 자체를 텍스트 문자열로 반환합니다. 이것은 형식에서 공식을 사용하는 데 도움이 됩니다.

   ![조건부 이메일 필드](/help/edge/assets/aem-forms-visible-expression-formula-text.png)

1. 양식을 미리 보고 게시합니다. 이제 확인란을 선택하면 이메일 필드가 표시되는 반면 선택을 해제하면 필드가 숨겨져 동적 사용자 경험이 제공됩니다.

   ![조건부 이메일](/help/edge/assets/aem-forms-coditional-email.gif)


## 예제 2: 자동 계산

다음 예에서는 양식에서 이동 일자를 선택할 때 양식이 추정 이동 비용을 자동으로 계산하는 방법을 보여 줍니다.

아래 그림과 같이 날짜 필드, 회의실 예산, 예상 출장 비용 필드 및 전자 메일 상자가 있는 양식을 만듭니다.

![조건부 전자 메일 양식](/help/edge/assets/aem-forms-automatic-calculations-form.png)

다음은 자동 계산을 수행하여 예상 이동 비용을 표시하는 방법입니다.

1. 설정 `Value` 의 속성 `amount` 필드 대상 `=F6*DAYS(F3,F2)`. 이 수식은 다음 날짜로부터 일 수를 계산합니다. `Start Date`  및 `End Date`, 룸 예산이 있는 일 수의 배수이며 결과를 다음과 같이 표시합니다. `Estimated Trip Cost` 필드.

1. 설정 `Value Expression` 의 속성 `Estimated Trip Cost` 필드 대상 `=FORMULATEXT ((address of value property of the amount field))`. 예, `=FORMULATEXT(F7)`. FORMULATEXT() 함수는 수식을 입력으로 취하여 수식 자체를 텍스트 문자열로 반환합니다. 이것은 형식에서 공식을 사용하는 데 도움이 됩니다.

1. 양식을 미리 보고 게시합니다. 이제, 을(를) 지정할 때 `Start Date`, `End Date`, 룸 예산. 다음 `Estimated Trip Cost` 는 자동으로 계산됩니다.

## 스프레드시트 함수 예


다음은 일반적으로 사용되는 스프레드시트 함수에 대한 몇 가지 예입니다.

**논리 함수:**

* **NOT():** 논리 상태를 반대로 바꿉니다(TRUE는 FALSE가 되고 그 반대).

  예: 이메일 필드가 비어 있는 경우 &quot;이메일 확인&quot; 필드를 숨깁니다.

   1. 설정 `Visible` 다음에 대한 &quot;이메일 확인&quot; 필드의 속성 `=NOT(if('address of email field'=""))`.

      ![AEM Forms 확인 이메일 필드 숨기기](/help/edge/assets/aem-forms-not-function-hide-email-field.png)


   1. &quot;이메일 확인&quot; 필드의 보이는 표현식을 다음으로 설정 `=FORMULATEXT ((address of visible property of the Confirm Email field))`

      ![AEM Forms 표시 표현식 공식](/help/edge/assets/aem-forms-visible-expression-formula-text.png)


* AND(): 지정된 모든 조건이 TRUE인 경우에만 TRUE를 반환합니다.

   * 예: 모든 필수 필드가 채워지는 경우에만 &quot;제출&quot; 버튼을 활성화합니다.

   1. 설정 `Visible` &quot;제출&quot; 단추의 속성을 사용하여 다음을 수행할 수 있습니다.



      ```JavaScript
      =AND(NOT(address of `value` property of the `name` field = ""), NOT(address of `value` property of the `email` field = ""), NOT(address of `value` property of the `phone` field))
      ```

      예:

      ```JavaScript
      =AND(NOT(F9=""), NOT(F12=""), NOT(F10=""))
      ```

   1. &quot;이메일 확인&quot; 필드의 보이는 표현식을 다음으로 설정

      ```JavaScript
      =FORMULATEXT ((address of visible property of the Confirm Email field))
      ```

      예:

      ```JavaScript
      =FORMULATEXT(G14)
      ```

      이 수식은 모든 필드(이름, 이메일, 전화)가 채워져 있고(NOT()) 각각에 대해 TRUE를 반환하는 경우에만 &quot;제출&quot; 단추(TRUE)를 표시하고, 그렇지 않으면 단추(AND(다중 FALSES) = FALSE)를 숨깁니다.

* OR(): 지정된 조건 중 하나 이상이 TRUE이면 TRUE를 반환합니다.

   * 예: 사용자가 적용 가능한 할인 쿠폰 코드를 입력하는 경우 할인 적용.

   1. 설정 `Visible` &quot;final amount&quot; 필드의 속성:


  ```JavaScript
     =IF(OR(F14="BlackFridaySale", F14="NewYearDiscount"), (F6*DAYS(F3,F2)* 0.7) , (F6*DAYS(F3,F2)))
  ```

   1. &quot;이메일 확인&quot; 필드의 값 표현식을 다음으로 설정

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      예:

      ```JavaScript
      =FORMULATEXT(F7)
      ```

      이 공식은 사용자가 쿠폰 코드(couponCode = &quot;NewYearDiscount&quot;) 또는 (couponCode = &quot;BlackFridaySale&quot;)를 입력하면 30% 할인을 계산하며, 그렇지 않으면 할인을 0으로 설정합니다.

**텍스트 함수:**

* IF(): 조건을 평가하고 TRUE이면 특정 값을 반환하고 FALSE이면 다른 값을 반환합니다.

   * 예: 선택한 제품 카테고리를 기반으로 한 사용자 지정 메시지 표시

   1. 설정 `Value` 의 속성 `message` 필드 대상 `Only upto 7 kg check-in lagguage is allowed!`:

   1. 설정 `Visible` 의 속성 `message` 필드:


      ```JavaScript
      =if(address of value property of chosen product category ="Economy", TRUE(), FALSE())
      ```

      예:

      ```JavaScript
      =if(F5="Economy", TRUE(), FALSE())
      ```

   1. 의 값 표현식 설정 `message` 필드 대상

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      예:

      ```JavaScript
      =FORMULATEXT(G15)
      ```

      이 공식은 &quot;최대 7kg의 체크인 수하물만 허용됩니다!&quot;라는 메시지를 표시합니다. 선택한 클래스가 &quot;경제&quot;이면 메시지 필드를 비워 둡니다.

**수학 함수:**

* SUM(): 지정된 셀 범위에서 값을 추가합니다.

  예: 장바구니에 있는 항목의 총 비용 계산

  &quot;총 비용&quot; 필드의 값 표현식: SUM(가격 * 수량)

  이 공식은 각 품목의 &quot;가격&quot;과 &quot;수량&quot;에 대해 별도의 필드가 있다고 가정합니다. 곱하고 SUM() 을 사용하여 장바구니에 있는 모든 항목에 대한 총 비용을 합산합니다.

* ROUND(): 숫자를 지정된 소수 자릿수로 반올림합니다.

  예: 계산된 할인 금액을 소수점 두 자리로 반올림합니다.

  &quot;할인 금액&quot; 필드의 값 표현식(다른 곳에서 할인이 계산된다고 가정): ROUND(discount, 2)

  이 공식은 할인 값을 소수점 두 자리로 반올림합니다.

* MIN(): 지정된 셀 범위에서 가장 작은 값을 반환합니다.

  예: 선택한 국가를 기준으로 등록 양식에 필요한 최소 연령 찾기

  최소 기간 필드의 값 표현식: MIN(ageLimits[&quot;US&quot;], ageLimits[&quot;UK&quot;], ageLimits[&quot;프랑스&quot;])

  이 공식은 서로 다른 국가에 대한 최소 연령 요구 사항을 저장하는 &quot;ageLimits&quot;라는 테이블이 있다고 가정합니다. 이 메서드는 MIN()을 사용하여 이 중 가장 작은 값을 찾습니다.


또한 적응형 Forms 블록을 사용하면 다음을 만들어 양식을 완전히 수행할 수 있습니다. [사용자 정의 함수](#creating-custom-functions). 사용자 정의 함수를 사용하면 고유한 규칙과 논리를 정의할 수 있으므로 양식의 동작 방식을 완벽하게 제어할 수 있습니다.


## 사용자 지정 함수 만들기 및 배포

기본 제공(OOTB) 적응형 Forms 블록은 많은 사용자에게 구현을 제공합니다 [공통 스프레드시트 함수](#spreadsheet-functions-for-rules). 그러나 양식에 대한 보다 세분화된 제어를 위해 적응형 Forms 블록 내의 Microsoft® Excel 또는 Google Sheets에서 사용할 수 있는 OOTB 함수를 사용할 수 있습니다. 적응형 Forms 블록에는 Microsoft® Excel 또는 Google Sheets에서 사용할 수 있는 모든 OOTB 함수에 대한 구현이 포함되어 있지 않습니다. 이러한 함수가 필요한 경우 유사한 구문을 사용하는 사용자 지정 함수를 개발하여 Microsoft® Excel 또는 Google Sheets에서 제공하는 기능을 사용할 수 있습니다. 예를 들어 다음을 구현할 수 있습니다 [Microsoft® Excel의 Year() 함수](https://support.microsoft.com/en-us/office/calculate-age-113d599f-5fea-448f-a4c3-268927911b37#) 출생 날짜로부터 연령을 계산하기 위해.


### 사용자 지정 함수 만들기

사용자 정의 함수는 `[Adaptive form block]/functions.js` 파일. 작성 프로세스에는 일반적으로 다음 단계가 포함됩니다.

* 함수 선언: 함수 이름과 해당 매개 변수(함수 이름이 허용하는 입력)를 정의합니다.
* 논리 구현: 함수에서 수행하는 특정 계산 또는 조작을 대략적으로 설명하는 코드를 작성합니다.
* 함수 내보내기: 관련 파일에서 함수를 내보내어 규칙 내에서 액세스할 수 있도록 합니다.

### 예: Year 함수

이 예에서는 Microsoft® Excel의 YEAR() 함수를 모방하여 연령을 계산하는 두 가지 사용자 정의 함수를 보여 줍니다.


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

### 양식에서 사용자 정의 함수 사용

양식에서 사용자 지정 함수를 사용하려면 다음을 수행하십시오.

1. **함수 추가**: 사용자 지정 함수를 `[Adaptive form block]/functions.js` 파일. 파일 내의 export 문에 추가해야 합니다.
1. **파일 배포**: 업데이트된 배포 `functions.js` 파일을 GitHub 프로젝트에 저장하고 성공적인 빌드를 확인합니다.
1. **기능 사용**: 를 사용하여 양식의 스프레드시트 내에 있는 함수에 액세스합니다 `Value`, `Value Expression`, `Visible`, 또는 `Visible Expression` OOTB에서 지원되는 다른 스프레드시트 함수와 유사한 등록 정보입니다.
1. **양식 미리 보기**: AEM Sidekick을 사용하여 새로 구현된 함수를 사용하여 양식을 미리 봅니다.

