---
title: 핵심 구성 요소를 기반으로 하는 적응형 양식의 규칙 편집기에서 사용할 수 있는 다양한 연산자 유형 및 이벤트는 무엇입니까?
description: 적응형 Forms 규칙 편집기는 다양한 연산자 유형과 이벤트를 지원합니다.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
source-git-commit: 780c68f0c21ef94ff6a73ce991370100b1a88db9
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 1%

---


# 핵심 구성 요소를 기반으로 하는 적응형 양식의 규칙 편집기에서 연산자 유형 및 이벤트

AEM Forms as a Cloud에서 규칙 편집기에는 복잡한 조건 및 작업을 쉽게 정의하고 실행할 수 있는 다양한 연산자 유형 및 이벤트가 포함되어 있습니다.

적응형 양식의 규칙 편집기에서 사용할 수 있는 연산자 유형은 정확한 조건을 구성하는 강력한 프레임워크를 제공합니다. 이를 통해 데이터를 조작하고 계산을 수행하며 논리적이고 일관성 있는 방식으로 여러 조건을 결합할 수 있습니다. 값을 비교하든, 산술 연산을 수행하든, 문자열을 조작하든 상관없이 이러한 연산자는 규칙이 유연하고 강력한지 확인합니다.

규칙 편집기의 이벤트는 규칙을 활성화하는 트리거 역할을 합니다. 특정 조건이 충족될 때 발생하는 특정 작업을 정의합니다. 다양한 유형의 이벤트를 활용함으로써 사용자 상호 작용, 예약 시간, 데이터 변경, 시스템 상태 등 다양한 시나리오에 대한 응답을 자동화할 수 있습니다. 이러한 트리거를 지정하는 기능을 통해 특정 요구 사항에 맞는 동적 및 반응형 규칙을 만들 수 있습니다.

사용 가능한 연산자 유형 및 이벤트를 이해하고 사용하면 규칙 편집기의 잠재력을 최대한 활용하여 고유한 요구 사항에 맞는 효율적이고 효과적인 규칙을 만들고 전반적인 시스템 기능을 개선할 수 있습니다.

## 규칙 편집기에서 사용 가능한 연산자 유형 및 이벤트 {#available-operator-types-and-events-in-rule-editor}

규칙 편집기는 규칙을 만들 수 있는 다음과 같은 논리 연산자 및 이벤트를 제공합니다.

* **이(가)**&#x200B;과(와) 같음
* **이(가)**&#x200B;과(와) 같지 않습니다.
* **다음으로 시작**
* **다음으로 끝남**
* **포함**
* **포함하지 않음**
* **비어 있음**
* **비어 있지 않음**
* **선택함:** 사용자가 확인란, 드롭다운, 라디오 단추에 대한 특정 옵션을 선택하면 true를 반환합니다.
* **초기화됨(이벤트):** 브라우저에서 양식 개체가 렌더링될 때 true를 반환합니다.
* **Is Changed (event):** 사용자가 양식 개체에 대해 입력한 값 또는 선택한 옵션을 변경하면 true를 반환합니다.

<!--
* **Navigation(event):** Returns true when the user clicks a navigation object. Navigation objects are used to move between panels. 
* **Step Completion(event):** Returns true when a step of a rule completes.
* **Successful Submission(event):** Returns true on successful submission of data to a form data model.
* **Error in Submission(event):**  Returns true on unsuccessful submission of data to a form data model. -->

### 규칙 편집기에서 사용 가능한 규칙 유형 {#available-rule-types-in-rule-editor}

이 규칙 편집기는 규칙을 작성하는 데 사용할 수 있는 사전 정의된 규칙 유형 집합을 제공합니다. 각 규칙 유형에 대해 자세히 살펴보겠습니다. 규칙 편집기에서 규칙을 작성하는 방법에 대한 자세한 내용은 규칙](/help/forms/rule-editor-core-components-user-interface.md#write-rules) 쓰기를 참조하세요[.

#### [!UICONTROL When] {#whenruletype}

**[!UICONTROL When]** 규칙 형식은 **condition-action-alternate action** 규칙 구문을 따르거나 경우에 따라 **condition-action** 구문을 따릅니다. 이 규칙 유형에서는 먼저 평가할 조건을 지정한 다음 조건이 충족되면 트리거할 작업(`True`)을 지정합니다. When 규칙 유형을 사용하는 동안 여러 AND 및 OR 연산자를 사용하여 [중첩 식](/help/forms/rule-editor-core-components-usecases.md#nested-expressions)을 만들 수 있습니다.

When 규칙 유형을 사용하여 양식 객체의 조건을 평가하고 하나 이상의 객체에 작업을 수행할 수 있습니다.

쉽게 말해, 일반적인 When 규칙은 다음과 같이 구성됩니다.

`When on Object A:`

`(Condition 1 AND Condition 2 OR Condition 3) is TRUE;`

`Then, do the following:`

`Action 2 on Object B;`
`AND`
`개체 C에 대한 작업 3;

`Else, do the following:`

`Action 2 on Object C;`
_

라디오 버튼이나 목록과 같은 다중 값 구성 요소가 있는 경우 해당 구성 요소에 대한 규칙을 만드는 동안 해당 옵션이 자동으로 검색되어 규칙 작성자에게 제공됩니다. 옵션 값을 다시 입력할 필요는 없습니다.

예를 들어, 목록에는 빨강, 파랑, 녹색 및 노랑의 네 가지 옵션이 있습니다. 규칙을 만드는 동안 옵션(라디오 버튼)이 자동으로 검색되어 규칙 작성자는 다음과 같이 사용할 수 있습니다.

![다중 값에 옵션 표시](assets/multivaluefcdisplaysoptions.png)

When 규칙 작성 중에 값 지우기 작업을 트리거할 수 있습니다. 작업의 값 지우기 지정된 개체의 값을 지웁니다. When 문에서 Clear 값 를 옵션으로 사용하면 여러 필드가 있는 복잡한 조건을 만들 수 있습니다. Else 문을 추가하여 조건을 더 추가할 수 있습니다

![값 지우기](assets/clearvalueof.png)

>[!NOTE]
>
> 규칙 유형이 단일 레벨 then-else 문만 지원하는 경우.

##### [!UICONTROL When]에 여러 필드가 허용됨 {#allowed-multiple-fields}

**When** 조건에서는 규칙이 적용되는 필드 외에 다른 필드를 추가할 수 있습니다.

예를 들어 When 규칙 유형을 사용하여 서로 다른 양식 객체에 대한 조건을 평가하고 작업을 수행할 수 있습니다.

시기:

(객체 A 조건 1)

및/또는

(오브젝트 B 조건 2)

그런 다음 다음을 수행합니다.

개체 A에 대한 작업 1

_

![When](/help/forms/assets/allowed-multiple-field-when.png)에서 여러 필드 허용됨

**조건 기능에서 허용된 여러 필드를 사용하는 동안 고려 사항**

* 규칙 편집기에서 이 기능을 사용하려면 핵심 구성 요소가 버전 3.0.14 이상으로](https://github.com/adobe/aem-core-forms-components) 설정되어 있는지 [확인하십시오.
* When 조건 내의 다른 필드에 규칙이 적용되는 경우 해당 필드 중 하나만 변경되면 규칙이 균일 트리거됩니다.


<!--
* It is not possible to add multiple fields in the When condition while applying rules to a button.

##### To enable Allowed Multiple fields in When condition feature

Allowed Multiple fields in When condition feature is disabled by default. To enable this feature, add a custom property at the template policy:

1. Open the corresponding template associated with an Adaptive Form in the template editor.
1. Select the existing policy as **formcontainer-policy**.
1. Navigate to the **[!UICONTROL Structure]**  view and, from the **[!UICONTROL Allowed Components]** list, open the **[!UICONTROL Adaptive Forms Container]** policy.
1. Go to the **[!UICONTROL Custom Properties]** tab and to add a custom property, click **[!UICONTROL Add]**.
1. Specify the **Group Name** of your choice. For example, in our case, we added the group name as **allowedfeature**.
1. Add the **key** and **value** pair as follows:
   * key: fd:changeEventBehaviour
   * value: deps
1. Click **[!UICONTROL Done]**. -->

조건 기능에서 허용되는 여러 필드에 문제가 발생하면 다음과 같이 문제 해결 단계를 팔로우 합니다.

1. 양식을 편집 모드에서 엽니다.
1. 컨텐츠 브라우저 를 열고 적응형 양식의 안내서 컨테이너&#x200B;]**구성 요소를 선택합니다**[!UICONTROL .
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. 완료 를 클릭하고 대화 상자를 다시 저장합니다.

**[!UICONTROL 숨기기]** 지정한 개체를 숨깁니다.

**[!UICONTROL 표시]** 지정한 개체를 표시합니다.

**[!UICONTROL 사용]** 지정한 개체를 사용합니다.

**[!UICONTROL 사용 안 함]** 지정한 개체를 사용하지 않습니다.

**[!UICONTROL 서비스 호출]** 양식 데이터 모델(FDM)에 구성된 서비스를 호출합니다. 서비스 호출 작업을 선택하면 필드가 나타납니다. 필드를 탭하면 [!DNL Experience Manager] 인스턴스의 모든 양식 데이터 모델(FDM)에 구성된 모든 서비스가 표시됩니다. 양식 데이터 모델 서비스를 선택하면 양식 개체를 지정된 서비스에 대한 입력 및 출력 매개 변수와 매핑할 수 있는 필드가 더 많이 나타납니다. 양식 데이터 모델(FDM) 서비스를 호출하는 예제 규칙을 참조하십시오.

양식 데이터 모델 서비스 외에 웹 서비스를 호출할 직접 WSDL URL을 지정할 수 있습니다. 그러나 양식 데이터 모델 서비스에는 많은 이점이 있으며 서비스를 호출하는 데 권장되는 방법이 있습니다.

FDM(양식 데이터 모델)에서 서비스를 구성하는 방법에 대한 자세한 내용은 [[!DNL Experience Manager Forms] 데이터 통합](data-integration.md)을 참조하십시오.

**[!UICONTROL 값 설정]** 지정한 개체의 값을 계산하고 설정합니다. 개체 값을 문자열, 다른 개체의 값, 수학 식이나 함수를 사용하여 계산된 값, 개체의 속성 값 또는 구성된 양식 데이터 모델 서비스의 출력 값으로 설정할 수 있습니다. 웹 서비스 옵션을 선택하면 [!DNL Experience Manager] 인스턴스의 모든 양식 데이터 모델(FDM)에 구성된 모든 서비스가 표시됩니다. 양식 데이터 모델 서비스를 선택하면 양식 개체를 지정된 서비스에 대한 입력 및 출력 매개 변수와 매핑할 수 있는 필드가 더 많이 나타납니다.

FDM(양식 데이터 모델)에서 서비스를 구성하는 방법에 대한 자세한 내용은 [[!DNL Experience Manager Forms] 데이터 통합](data-integration.md)을 참조하십시오.

**[!UICONTROL 속성 설정]** 규칙 유형을 사용하면 조건 작업을 기반으로 지정된 개체의 속성 값을 설정할 수 있습니다. 속성을 다음 중 하나로 설정할 수 있습니다.
* 표시(부울)
* label.value (문자열)
* label.visible (부울)
* 설명(문자열)
* 활성화됨(부울)
* readOnly(부울)
* 필수(부울)
* screenReaderText(문자열)
* valid(부울)
* errorMessage(문자열)
* 기본값(숫자, 문자열, 날짜)
* enumNames(String[])
* chartType (String)

예를 들어, 버튼을 클릭할 때 텍스트 상자를 표시하는 규칙을 정의할 수 있습니다. 사용자 지정 함수, 양식 개체, 개체 속성 또는 서비스 출력을 사용하여 규칙을 정의할 수 있습니다.

![속성 설정](assets/set_property_rule_new.png)

사용자 지정 함수를 기반으로 규칙을 정의하려면 드롭다운 목록에서 **[!UICONTROL 함수 출력]**&#x200B;을(를) 선택한 다음 **[!UICONTROL 함수]** 탭에서 사용자 지정 함수를 드래그 앤 드롭합니다. 조건 작업이 충족되면 텍스트 입력 상자가 표시됩니다.

양식 개체를 기반으로 규칙을 정의하려면 드롭다운 목록에서 **[!UICONTROL 양식 개체]**&#x200B;를 선택하고 **[!UICONTROL 양식 개체]** 탭에서 양식 개체를 끌어서 놓습니다. 조건 작업이 충족되면 텍스트 입력 상자가 적응형 양식에 표시됩니다.

개체 속성을 기반으로 속성 설정 규칙을 사용하면 적응형 양식에 포함된 다른 개체 속성을 기반으로 적응형 양식에 텍스트 입력 상자를 표시할 수 있습니다.

다음 그림은 적응형 양식에서 텍스트 상자의 숨김이나 표시를 기반으로 확인란을 동적으로 활성화하는 예를 보여 줍니다.

![개체 속성](assets/object_property_set_property_new.png)

**[!UICONTROL 값 지우기]** 지정한 개체의 값을 지웁니다.

**[!UICONTROL 초점]** 설정 지정된 개체에 포커스 설정.

**[!UICONTROL 양식 제출]** 양식을 제출합니다.

**** 재설정 양식 또는 지정된 개체를 재설정합니다.

**[!UICONTROL 유효성 검사]** 폼이나 지정된 개체의 유효성을 검사합니다.

**[!UICONTROL 인스턴스]** 추가: 지정된 반복 가능 패널 또는 테이블 행의 인스턴스 를 추가합니다.

**[!UICONTROL 인스턴스]** 제거 지정된 반복 가능 패널 또는 테이블 행의 인스턴스를 제거합니다.

**[!UICONTROL 함수 출력]** 미리 정의된 함수 또는 사용자 지정 함수를 기반으로 규칙을 정의합니다.

**[!UICONTROL 이동]** 다른 적응형 Forms, 이미지 또는 문서 조각과 같은 기타 에셋 또는 외부 URL로 이동합니다. <!-- For more information, see [Add button to the Interactive Communication](create-interactive-communication.md#addbuttontothewebchannel). -->

**[!UICONTROL 이벤트 발송]** 미리 정의된 조건이나 이벤트를 기반으로 특정 작업이나 동작을 트리거합니다.

#### [!UICONTROL 값 설정] {#set-value-of}

**[!UICONTROL Set Value of]** 규칙 형식을 사용하면 지정된 조건을 충족하는지 여부에 따라 양식 개체의 값을 설정할 수 있습니다. 값은 다른 개체의 값, 리터럴 문자열, 수학적 식이나 함수에서 파생된 값, 다른 개체의 속성 값 또는 양식 데이터 모델 서비스의 출력으로 설정할 수 있습니다. 마찬가지로 구성 요소, 문자열, 속성 또는 함수나 수학 표현식에서 파생된 값에 대한 조건을 확인할 수 있습니다.

**Set Value Of** 규칙 형식은 패널 및 도구 모음 단추와 같은 모든 양식 개체에 사용할 수 없습니다. 표준 규칙 값 설정(Set Value Of rule)의 구조는 다음과 같습니다.

개체 A의 값을 다음으로 설정:

(문자열 ABC) 또는
(객체 C의 객체 등록 정보 X) 또는
(함수의 값) 또는
(수학 표현식의 값) OR
(데이터모델 서비스의 출력값)

다음과 같은 경우(선택 사항):

(조건 1 및 조건 2 및 조건 3)은 TRUE입니다.

다음 예제에서는 as `True` 의 `Question2` 값을 선택하고 as`correct`의 `Result` 값을 설정합니다.

![값 웹 서비스 설정](assets/set-value-web-service.png)

양식 데이터 모델 서비스를 사용한 집합 값 규칙의 예.

#### [!UICONTROL 표시] {#show}

**[!UICONTROL Show]** 규칙 유형을 사용하면 조건 충족 여부에 따라 양식 개체를 표시하거나 숨기는 규칙을 작성할 수 있습니다. 또한 Show 규칙 유형은 조건이 충족되지 않거나 `False`을(를) 반환하는 경우 Hide 작업을 트리거합니다.

일반적인 표시 규칙은 다음과 같이 구성됩니다.

`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`

#### [!UICONTROL 숨기기] {#hide}

Show 규칙 형식과 마찬가지로 **[!UICONTROL Hide]** 규칙 형식을 사용하여 조건 충족 여부에 따라 양식 개체를 표시하거나 숨길 수 있습니다. 조건이 충족되지 않거나 `False`을(를) 반환하는 경우 Hide 규칙 유형도 Show 작업을 트리거합니다.

일반적인 숨기기 규칙은 다음과 같이 구성됩니다.

`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`

#### [!UICONTROL 사용] {#enable}

**[!UICONTROL Enable]** 규칙 유형을 사용하면 조건 충족 여부에 따라 양식 개체를 활성화하거나 비활성화할 수 있습니다. 또한 Enable 규칙 유형은 조건이 충족되지 않거나 `False`을 반환하는 경우 Disable 작업을 트리거합니다.

일반적인 Enable 규칙은 다음과 같이 구성됩니다.

`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`

#### [!UICONTROL 사용 안 함] {#disable}

Enable 규칙 유형과 유사한 **[!UICONTROL Disable]** 규칙 유형을 사용하면 조건 충족 여부에 따라 양식 개체를 활성화하거나 비활성화할 수 있습니다. 또한 Disable 규칙 유형은 조건이 충족되지 않거나 `False`을(를) 반환하는 경우 Enable 작업을 트리거합니다.

일반적인 비활성화 규칙은 다음과 같이 구성됩니다.

`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

#### [!UICONTROL 유효성 검사] {#validate}

**[!UICONTROL Validate]** 규칙 형식은 식을 사용하여 필드의 값을 확인합니다. 예를들어, 이름을 지정하는 텍스트 상자에 특수 문자나 숫자가 들어 있지 않은지 확인하는 식을 작성할 수 있습니다.

일반적인 유효성 검사 규칙은 다음과 같이 구성됩니다.

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>지정된 값이 유효성 검사 규칙을 준수하지 않으면 사용자에게 유효성 검사 메시지를 표시할 수 있습니다. 사이드바의 구성 요소 속성에서 **[!UICONTROL 스크립트 유효성 검사 메시지]** 필드에 메시지를 지정할 수 있습니다.

![스크립트 유효성 검사](assets/script-validation.png)

<!--
### [!UICONTROL Set Options Of] {#setoptionsof}

The **[!UICONTROL Set Options Of]** rule type enables you to define rules to add check boxes dynamically to the Adaptive Form. You can use a Form Data Model or a custom function to define the rule.

To define a rule based on a custom function, select **[!UICONTROL Function Output]** from the drop-down list, and drag-and-drop a custom function from the **[!UICONTROL Functions]** tab. The number of checkboxes defined in the custom function are added to the Adaptive Form.

![Custom Functions](assets/custom_functions_set_options_new.png)

To create a custom function, see [custom functions in rule editor](#custom-functions).

To define a rule based on a form data model:

1. Select **[!UICONTROL Service Output]** from the drop-down list.
1. Select the data model object.
1. Select a data model object property from the **[!UICONTROL Display Value]** drop-down list. The number of checkboxes in the Adaptive Form is derived from the number of instances defined for that property in the database.
1. Select a data model object property from the **[!UICONTROL Save Value]** drop-down list.

![FDM set options](assets/fdm_set_options_new.png) -->

## 다음 단계

이제 핵심 구성 요소를 기반으로 하는 적응형 양식에 대한 규칙 편집기의 다양한 [예제를 살펴보겠습니다](/help/forms/rule-editor-core-components-usecases.md).

## 추가 참조

{{see-also-rule-editor}}