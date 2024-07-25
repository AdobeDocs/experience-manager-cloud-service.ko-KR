---
title: 이 문서에서는 핵심 구성 요소를 기반으로 하는 적응형 양식의 규칙 편집기에 대한 다양한 사용 사례를 간략하게 설명합니다.
description: 이 문서에서는 핵심 구성 요소를 기반으로 하는 적응형 양식의 규칙 편집기에 대한 다양한 사용 사례를 간략하게 설명합니다.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 8191e113-f768-4b1e-a191-e3c722f19054
source-git-commit: 34be2ca89433e36a68e7d8eae42c6bd9ad6e623f
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 0%

---

# 규칙 편집기의 다양한 사용 사례

이 문서에서는 핵심 구성 요소를 기반으로 하는 적응형 양식에 대한 규칙 편집기의 자세한 예제를 제공하여 다양한 시나리오에 대한 적절한 구현에 대한 통찰력을 제공합니다. 규칙 편집기를 사용하면 개발자가 양식의 동작을 제어하는 논리를 정의하고 관리할 수 있습니다.
이제 규칙 편집기에 대한 다양한 구현에 대해 살펴보겠습니다.


## 함수를 사용하여 반복 가능한 패널에서 복잡한 계산 간소화

규칙 편집기를 사용하면 반복 가능한 패널 내의 필드에서 Sum, Min, Max 및 Join과 같은 기본 함수를 바로 사용할 수 있습니다. 숫자 배열, 문자열 배열, 부울 배열 등을 허용하는 함수에 반복 가능한 패널 필드 값을 전달할 수도 있습니다. 이렇게 하면 강력한 자동화가 잠금 해제되므로 사용자 지정 코드 없이 복잡한 비즈니스 논리를 구현할 수 있습니다.

각 패널 인스턴스가 자산의 선언된 값에 대한 정보를 수집하는 반복 가능한 패널이 있는 양식을 상상해 보십시오.

![반복 가능한 양식](/help/forms/assets/ootb-function-support-repeatable-panel-form.png)

`Sum` 함수를 사용하여 모든 패널에서 총 에셋 값을 자동으로 계산할 수 있으므로 수동으로 계산할 필요가 없고 오류가 발생할 가능성이 줄어듭니다.

![OOTB 함수에서 반복 가능한 패널 필드 지원](/help/forms/assets/ootb-function-support-repeatable-panel.png)

에셋 값을 선언할 인스턴스를 추가하여 양식을 작성할 때 `Calculate Asset Value` 단추는 선언된 모든 에셋 값의 총 합계를 계산하고 그 결과를 `assetvalue` 텍스트 상자에 표시합니다.

![OOTB 함수에서 반복 가능한 패널 필드 지원](/help/forms/assets/ootb-function-support-repeatable-panel-form-preview.png)

>[!NOTE]
>
> 반복 가능 패널 필드의 값이 배열을 허용하지 않는 함수에 전달되는 경우 반복 가능 패널의 마지막 인스턴스의 필드 값이 함수에 전달됩니다.

이것은 단지 하나의 예입니다! 사용 가능한 [함수](#b-form-objects-and-functions-br)를 탐색하여 워크플로우를 간소화하고 양식 내에서 데이터 정확도를 향상시킵니다.

## 중첩된 표현식 {#nestedexpressions}

규칙 편집기를 사용하면 여러 AND 및 OR 연산자를 사용하여 중첩된 규칙을 만들 수 있습니다. 규칙에서 여러 AND 및 OR 연산자를 혼합할 수 있습니다.

다음은 필수 조건이 충족될 때 자녀 양육권 자격에 대한 메시지를 사용자에게 표시하는 중첩된 규칙의 예입니다.

![복합 식](assets/complexexpression.png)

규칙 내에서 조건을 드래그 앤 드롭하여 편집할 수도 있습니다. 조건 전에 핸들(![핸들](assets/drag-handle.svg))을 선택하고 마우스로 가리킵니다. 포인터가 아래 표시된 대로 손 기호로 바뀌면 규칙을 규칙 내의 아무 곳에나 드래그하여 놓습니다. 규칙 구조가 변경됩니다.

![드래그 앤 드롭](assets/drag-and-drop.png)

## 날짜 표현식 조건 {#dateexpression}

규칙 편집기를 사용하면 날짜 비교를 사용하여 조건을 만들 수 있습니다.

다음은 주택에 대한 담보대출이 이미 실행된 경우 정적 텍스트 객체를 표시하는 예제 조건입니다. 이 조건은 사용자가 날짜 필드를 채워 나타냅니다.

사용자가 입력한 부동산의 담보대출 일자가 과거인 경우 적응형 양식에 소득 계산에 대한 메모가 표시됩니다. 다음 규칙은 사용자가 입력한 날짜와 현재 날짜를 비교하며 사용자가 입력한 날짜가 현재 날짜보다 이전인 경우 양식에 텍스트 메시지(소득)가 표시됩니다.

![날짜 식 조건](assets/dateexpressioncondition.png)

채워진 일자가 현재 일자보다 이전인 경우 양식에 다음과 같은 텍스트 메시지(수입)가 표시됩니다.

![날짜 식 조건이 충족됨](assets/dateexpressionconditionmet.png)

## 숫자 비교 조건 {#number-comparison-conditions}

규칙 편집기를 사용하면 두 숫자를 비교하는 조건을 만들 수 있습니다.

다음은 지원자가 현재 주소에 있는 개월 수가 36개월 미만인 경우 정적 텍스트 객체를 표시하는 예제 조건입니다.

![숫자 비교 조건](assets/numbercomparisoncondition.png)

사용자가 현재 거주 주소에서 36개월 미만 거주한다고 표시하면 양식에 더 많은 거주 증명을 요청할 수 있다는 알림이 표시됩니다.

![더 많은 증명을 요청함](assets/additionalproofrequested.png)

<!-- ## Impact of rule editor on existing scripts {#impact-of-rule-editor-on-existing-scripts}

In [!DNL Experience Manager Forms] versions prior to [!DNL Experience Manager 6.1 Forms] feature pack 1, form authors and developers used to write expressions in the Scripts tab of the Edit component dialog to add dynamic behavior to Adaptive Forms. The Scripts tab is now replaced by the rule editor.

Any scripts or expressions that you must have written in the Scripts tab are available in the rule editor. While you cannot view or edit them in visual editor, if you are a part of the forms-power-users group you can edit scripts in code editor. -->

### 양식 데이터 모델 서비스 호출 {#invoke}

대출 금액, 재직 기간 및 신청자의 신용 점수를 입력하고 EMI 금액 및 이자율을 포함한 대출 플랜을 반환하는 웹 서비스 `GetInterestRates`을(를) 고려하십시오. 웹 서비스를 데이터 소스로 사용하여 양식 데이터 모델(FDM)을 만듭니다. 양식 모델에 데이터 모델 개체 및 `get` 서비스를 추가합니다. 이 서비스는 양식 데이터 모델(FDM)의 [서비스] 탭에 나타납니다. 그런 다음 데이터 모델 객체의 필드를 포함하는 적응형 양식을 만들어 대출 금액, 근속 기간 및 신용 점수에 대한 사용자 입력을 캡처합니다. 웹 서비스를 트리거하는 단추를 추가하여 계획 세부 정보를 가져옵니다. 해당 필드에 출력이 채워집니다.

다음 규칙은 예제 시나리오를 수행하기 위해 서비스 호출 작업을 구성하는 방법을 보여 줍니다.

![Example-invoke-services](assets/example-invoke-services.png)

>[!NOTE]
>
>입력이 배열 유형인 경우 배열을 지원하는 필드가 출력 드롭다운 섹션에 표시됩니다.

### When 규칙을 사용하여 여러 작업 트리거 {#triggering-multiple-actions-using-the-when-rule}

대출 신청 양식에서 대출 신청자가 기존 고객인지 여부를 캡처하려고 합니다. 사용자가 제공하는 정보에 따라 고객 ID 필드가 표시되거나 숨겨져야 합니다. 또한 사용자가 기존 고객인 경우 고객 ID 필드에 포커스를 설정할 수 있습니다. 대출 신청 양식에는 다음과 같은 구성 요소가 있습니다.

* 라디오 단추, **[!UICONTROL 기존 Geometrixx 고객입니까?]**: [!UICONTROL 예] 및 [!UICONTROL 아니요] 옵션을 제공합니다. 예 값은 **0**&#x200B;이고 아니요 값은 **1**&#x200B;입니다.

* 고객 ID를 지정하는 텍스트 필드 **[!UICONTROL Geometrixx 고객 ID]**&#x200B;입니다.

이 동작을 구현하기 위해 라디오 단추에 When 규칙을 작성할 때 시각적 규칙 편집기에 다음과 같이 규칙이 나타납니다.

![When-rule-example](assets/when-rule-example.png)

예제 규칙에서 When 섹션의 문은 True를 반환하는 경우 Then 섹션에 지정된 작업을 실행하는 조건입니다.

<!-- The rule appears as follows in the code editor.

![when-rule-example-code](assets/when-rule-example-code.png) 

Rule in the code editor -->

### 규칙에서 함수 출력 사용 {#using-a-function-output-in-a-rule}

구매 주문 양식에는 사용자가 주문을 작성하는 다음 표가 있습니다. 이 표에서:

* 첫 번째 행은 반복 가능하므로 사용자는 여러 제품을 주문하고 다른 수량을 지정할 수 있습니다. 요소 이름은 `Row1`입니다.
* 반복 가능 행의 제품 수량 열에 있는 셀의 제목은 수량입니다. 이 셀의 요소 이름은 `productquantity`입니다.
* 테이블의 두 번째 행은 반복될 수 없으며 이 행의 제품 수량 열에 있는 셀 제목은 총 수량입니다.

![Example-function-table](assets/example-function-table.png)

**A.** 행1 **B.** 수량 **C.** 총 수량

이제 모든 제품에 대해 제품 수량 열에 지정된 수량을 추가하고 총 수량 셀에 합계를 표시합니다. 아래와 같이 총 수량 셀에 규칙 값 설정을 작성하면 이 합계를 달성할 수 있습니다.

![Example-function-output](assets/example-function-output.png)

### 표현식을 사용하여 필드 값 확인 {#validating-a-field-value-using-expression}

앞의 예에서 설명한 구매 주문 양식에서는 사용자가 가격이 더 비싼 제품을 두 개 이상 주문하지 못하도록 10000. 이 유효성 검사를 수행하려면 아래와 같이 유효성 검사 규칙을 작성할 수 있습니다.

![Example-validate](assets/example-validate.png)

## 추가 참조

{{see-also-rule-editor}}
