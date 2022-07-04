---
title: 적응형 Forms 규칙 편집기를 사용하는 방법
description: 적응형 Forms 규칙 편집기를 사용하면 코딩 또는 스크립팅 없이 다이내믹 동작을 추가하고 복잡한 논리를 양식에 작성할 수 있습니다. 규칙 구성을 선택하기 위한 규칙 및 지침 이해를 시작합니다. 규칙 편집기에서 사용 가능한 연산자 유형 및 이벤트에 대해 자세히 알아보십시오.
feature: Adaptive Forms
role: User
level: Beginner, Intermediate
exl-id: 6fd38e9e-435e-415f-83f6-3be177738c00
source-git-commit: e64e15c9096f837daa7fff5c64b8394736297579
workflow-type: tm+mt
source-wordcount: '6351'
ht-degree: 0%

---

# 적응형 양식에 규칙 추가 {#adaptive-forms-rule-editor}

## 개요 {#overview}

규칙 편집기 기능을 사용하면 forms 비즈니스 사용자와 개발자가 적응형 양식 개체에 규칙을 작성할 수 있습니다. 이러한 규칙은 양식의 사전 설정된 조건, 사용자 입력 및 사용자 작업을 기반으로 양식 개체에 대해 트리거할 작업을 정의합니다. 양식 채우기 환경을 더욱 간소화하여 정확성과 속도를 보장합니다.

규칙 편집기는 규칙을 작성하는 데 사용할 수 있는 직관적이고 간단한 사용자 인터페이스를 제공합니다. 규칙 편집기에서는 모든 사용자를 위한 시각적 편집기를 제공합니다.<!-- In addition, only for forms power users, rule editor provides a code editor to write rules and scripts. --> 규칙을 사용하여 적응형 양식 개체에서 수행할 수 있는 몇 가지 주요 작업은 다음과 같습니다.

* 개체 표시 또는 숨기기
* 개체 활성화 또는 비활성화
* 개체의 값 설정
* 개체 값의 유효성 검사
* 함수를 실행하여 객체 값을 계산합니다
* 양식 데이터 모델 서비스 호출 및 작업 수행
* 개체의 속성 설정

<!-- Rule editor replaces the scripting capabilities in [!DNL Experience Manager 6.1 Forms] and earlier releases. However, your existing scripts are preserved in the new rule editor. For more information about working with existing scripts in the rule editor, see [Impact of rule editor on existing scripts](rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p). -->

forms-power-users 그룹에 추가된 사용자는 스크립트를 만들고 기존 스크립트를 편집할 수 있습니다. 의 사용자 [!DNL forms-users] 그룹은 스크립트를 사용할 수 있지만 스크립트를 만들거나 편집할 수는 없습니다.

## 규칙 이해 {#understanding-a-rule}

규칙은 작업과 조건의 조합입니다. 규칙 편집기에서 작업에는 양식에 있는 개체의 값을 숨기기, 표시, 활성화, 비활성화 또는 계산하는 등의 활동이 포함됩니다. 조건은 양식 객체의 상태, 값 또는 속성에 대해 확인 및 작업을 수행하여 평가되는 부울 표현식입니다. 작업은 값( )을 기반으로 수행됩니다 `True` 또는 `False`)를 반환한 후 조건에 대한 평가를 끝냅니다.

규칙 편집기에서는 규칙을 작성하는 데 도움이 되도록 시기, 표시, 숨기기, 활성화, 비활성화, 값 설정 및 유효성 검사와 같이 사전 정의된 규칙 유형 세트를 제공합니다. 각 규칙 유형을 사용하면 규칙에 조건과 작업을 정의할 수 있습니다. 이 문서에서는 각 규칙 유형에 대해 자세히 설명합니다.

규칙은 일반적으로 다음 구문 중 하나를 따릅니다.

**조건-작업** 이 구성에서는 규칙이 먼저 조건을 정의하고 다음에 트리거할 작업을 정의합니다. 프로그래밍 언어의 if-then 문과 비교할 수 있습니다.

규칙 편집기에서 **When** 규칙 유형은 조건-작업 구성을 적용합니다.

**작업 조건** 이 구성에서는 규칙이 먼저 트리거할 작업을 정의하고 그 다음에 평가 조건을 정의합니다. 이 구문의 또 다른 변형은 작업-조건-대체 작업입니다. 이 작업은 조건이 False를 반환하는 경우 트리거할 대체 작업도 정의합니다.

규칙 편집기의 표시, 숨기기, 활성화, 비활성화, 값 설정 및 유효성 검사 규칙 유형을 작업 조건 규칙 구성을 적용합니다. 기본적으로 [표시]에 대한 대체 작업은 [숨기기]이고, [사용]에 대한 대체 작업은 [사용 안 함]이며, 그 반대입니다. 기본 대체 작업은 변경할 수 없습니다.

>[!NOTE]
>
>규칙 편집기에서 정의하는 조건 및 작업을 포함하여 사용 가능한 규칙 유형은 규칙을 만드는 양식 객체의 유형에도 따라 다릅니다. 규칙 편집기에는 특정 양식 개체 유형에 대한 조건 및 작업 문을 쓰기 위한 유효한 규칙 유형과 옵션만 표시됩니다. 예를 들어, 패널 개체에 대한 유효성 검사, 값 설정, 활성화 및 비활성화 규칙 유형이 표시되지 않습니다.

규칙 편집기에서 사용할 수 있는 규칙 유형에 대한 자세한 내용은 다음을 참조하십시오 [규칙 편집기에서 사용할 수 있는 규칙 유형](rule-editor.md#p-available-rule-types-in-rule-editor-p).

### 규칙 구성 선택 지침 {#guidelines-for-choosing-a-rule-construct}

규칙 구성을 사용하여 대부분의 사용 사례를 달성할 수 있지만, 다음 몇 가지 지침에 따라 한 개의 구성을 다른 도메인으로 선택할 수 있습니다. 규칙 편집기에서 사용할 수 있는 규칙에 대한 자세한 내용은 다음을 참조하십시오 [규칙 편집기에서 사용할 수 있는 규칙 유형](rule-editor.md#p-available-rule-types-in-rule-editor-p).

* 규칙을 만들 때 일반적인 경험의 규칙은 규칙을 작성하는 개체의 컨텍스트에서 규칙을 고려하는 것입니다. 사용자가 필드 A에서 지정하는 값을 기반으로 필드 B를 숨기거나 표시할 수 있습니다. 이 경우 필드 A에서 조건을 평가하고, 반환되는 값을 기반으로 필드 B에서 작업을 트리거합니다.

   따라서 필드 B(조건을 평가하는 개체)에 규칙을 작성하는 경우 조건-작업 구문 또는 When 규칙 유형을 사용합니다. 마찬가지로 필드 A에 작업 조건 구성 또는 표시 또는 숨기기 규칙 유형을 사용합니다.

* 한 조건을 기준으로 여러 작업을 수행해야 하는 경우가 있습니다. 이러한 경우 조건-작업 구성을 사용하는 것이 좋습니다. 이 구성에서는 조건을 한 번 평가하고 여러 작업 문을 지정할 수 있습니다.

   예를 들어, 사용자가 필드 A에서 지정하는 값을 확인하는 조건을 기반으로 필드 B, C 및 D를 숨기려면 조건-작업 구성 또는 필드 A에 규칙 유형을 지정하고 필드 B, C 및 D의 가시성을 제어하는 작업을 지정하는 규칙을 하나씩 작성합니다. 그렇지 않으면 B, C 및 D 필드에 세 개의 별도의 규칙이 필요합니다. 여기서 각 규칙은 조건을 확인하고 각 필드를 표시하거나 숨깁니다. 이 예제에서 세 개체에 대해 Show 또는 Hide 규칙 형식이 아닌 한 개체에 When 규칙 유형을 쓰는 것이 더 효율적입니다.

* 여러 조건을 기반으로 작업을 트리거하려면 작업 조건 구성을 사용하는 것이 좋습니다. 예를 들어, 필드 B, C 및 D에 대한 조건을 평가하여 필드 A를 표시하고 숨기려면 필드 A에 표시 또는 숨기기 규칙 유형을 사용합니다.
* 규칙에 하나의 조건에 대한 작업이 포함된 경우 조건-작업 또는 작업 조건 구성을 사용합니다.
* 규칙이 조건을 확인하고 필드에 값을 제공하거나 필드를 종료할 때 즉시 작업을 수행하는 경우 조건이 평가되는 필드에 조건-작업 구성 또는 When 규칙 유형을 사용하여 규칙을 작성하는 것이 좋습니다.
* When 규칙의 조건은 사용자가 When 규칙이 적용되는 객체의 값을 변경할 때 평가됩니다. 그러나 값 미리 채우기와 같이 서버 측에서 값이 변경될 때 작업이 트리거되도록 하려면 필드가 초기화될 때 작업을 트리거하는 When 규칙을 작성하는 것이 좋습니다.
* 드롭다운, 라디오 단추 또는 확인란 개체에 대한 규칙을 작성할 때 양식에 있는 이러한 양식 개체의 옵션 또는 값이 규칙 편집기에서 미리 채워집니다.

## 규칙 편집기에서 사용할 수 있는 연산자 유형 및 이벤트 {#available-operator-types-and-events-in-rule-editor}

규칙 편집기에서는 규칙을 만들 수 있는 다음과 같은 논리 연산자와 이벤트를 제공합니다.

* **다음과 같음**
* **다음과 같지 않음**
* **다음으로 시작**
* **종료 문자**
* **포함하는 항목**
* **비어 있음**
* **비어 있지 않음**
* **선택 항목:** 사용자가 확인란, 드롭다운, 라디오 단추에 대한 특정 옵션을 선택하면 true를 반환합니다.
* **초기화됨(이벤트):** 브라우저에서 양식 개체가 렌더링될 때 true를 반환합니다.
* **변경됨(이벤트):** 사용자가 양식 개체에 대해 입력한 값 또는 선택한 옵션을 변경하면 true를 반환합니다.
* **탐색(이벤트):** 사용자가 탐색 개체를 클릭하면 true를 반환합니다. 탐색 개체는 패널 간을 이동하는 데 사용됩니다.
* **단계 완료(이벤트):** 규칙 단계가 완료되면 true를 반환합니다.
* **전송 성공(이벤트):** 양식 데이터 모델에 데이터를 성공적으로 제출하면 true를 반환합니다.
* **제출 오류(이벤트):**  양식 데이터 모델에 데이터를 제출하지 못한 경우 true를 반환합니다.

## 규칙 편집기에서 사용할 수 있는 규칙 유형 {#available-rule-types-in-rule-editor}

규칙 편집기에서는 규칙을 작성하는 데 사용할 수 있는 사전 정의된 규칙 유형 세트를 제공합니다. 각 규칙 유형을 자세히 살펴보겠습니다. 규칙 편집기에서 규칙 작성에 대한 자세한 내용은 [규칙 쓰기](rule-editor.md#p-write-rules-p).

### [!UICONTROL http 화이트보드] {#whenruletype}

다음 **[!UICONTROL When]** 규칙 유형은 **condition-action-alternate action** 규칙 구성 또는 경우에 따라 **condition-action** 구성합니다. 이 규칙 유형에서는 먼저 평가를 위한 조건을 지정하고 조건이 충족되면 트리거할 작업을 지정합니다( `True`). When 규칙 유형을 사용하는 동안 여러 AND 및 OR 연산자를 사용하여 만들 수 있습니다 [중첩 표현식](#nestedexpressions).

When 규칙 유형을 사용하면 양식 개체에 대한 조건을 평가하고 하나 이상의 개체에 대해 작업을 수행할 수 있습니다.

일반적인 말로, 일반적인 When 규칙이 다음과 같이 구조됩니다.

`When on Object A:`

`(Condition 1 AND Condition 2 OR Condition 3) is TRUE;`

`Then, do the following:`

객체 B에 대한 작업 2 객체 C의 작업 3

_

라디오 단추 또는 목록과 같은 다중 값 구성 요소가 있는 경우 해당 구성 요소에 대한 규칙을 만들면 옵션이 자동으로 검색되어 규칙 작성자가 사용할 수 있습니다. 옵션 값을 다시 입력할 필요는 없습니다.

예를 들어, 목록에는 네 가지 선택 사항이 있습니다. 빨강, 파랑, 녹색, 노랑. 규칙을 만드는 동안 옵션(라디오 단추)이 자동으로 검색되고 규칙 작성자가 다음과 같이 사용할 수 있게 됩니다.

![다중 값에 옵션이 표시됩니다](assets/multivaluefcdisplaysoptions.png)

When 규칙을 작성하는 동안 Clear Value Of 작업을 트리거할 수 있습니다. 값 지우기 작업은 지정된 객체의 값을 지웁니다. When 문에 선택 사항으로 값 지우기 를 사용하면 여러 필드가 있는 복잡한 조건을 만들 수 있습니다.

![값 지우기](assets/clearvalueof.png)

**[!UICONTROL 숨기기]** 지정된 개체를 숨깁니다.

**[!UICONTROL 표시]** 지정된 개체를 표시합니다.

**[!UICONTROL 활성화]** 지정된 개체를 활성화합니다.

**[!UICONTROL 비활성화]** 지정한 개체를 사용하지 않도록 설정합니다.

**[!UICONTROL 서비스 호출]** 양식 데이터 모델로 구성된 서비스를 호출합니다. 서비스 호출 작업을 선택하면 필드가 나타납니다. 필드를 탭하면 페이지의 모든 양식 데이터 모델에 구성된 모든 서비스가 표시됩니다 [!DNL Experience Manager] 인스턴스. 양식 데이터 모델 서비스를 선택할 때 지정된 서비스의 입력 및 출력 매개 변수와 함께 양식 객체를 매핑할 수 있는 필드가 더 나타납니다. 양식 데이터 모델 서비스 호출에 대한 예제 규칙을 참조하십시오.

양식 데이터 모델 서비스 외에도 웹 서비스를 호출하는 직접적인 WSDL URL을 지정할 수 있습니다. 그러나 양식 데이터 모델 서비스에는 많은 이점이 있으며 서비스를 호출하는 데 권장되는 방법이 있습니다.

양식 데이터 모델에서 서비스 구성에 대한 자세한 내용은 다음을 참조하십시오 [[!DNL Experience Manager Forms] 데이터 통합](data-integration.md).

**[!UICONTROL 값 설정]** 지정된 객체의 값을 계산하고 설정합니다. 객체 값을 문자열, 다른 객체의 값, 수학 식 또는 함수를 사용하여 계산된 값, 객체의 속성 값 또는 구성된 양식 데이터 모델 서비스의 출력 값으로 설정할 수 있습니다. 웹 서비스 옵션을 선택하면 웹 서비스의 모든 양식 데이터 모델에 구성된 모든 서비스가 표시됩니다 [!DNL Experience Manager] 인스턴스. 양식 데이터 모델 서비스를 선택할 때 지정된 서비스의 입력 및 출력 매개 변수와 함께 양식 객체를 매핑할 수 있는 필드가 더 나타납니다.

양식 데이터 모델에서 서비스 구성에 대한 자세한 내용은 다음을 참조하십시오 [[!DNL Experience Manager Forms] 데이터 통합](data-integration.md).

다음 **[!UICONTROL 속성 설정]** 규칙 유형을 사용하면 조건 작업을 기반으로 지정된 객체의 속성 값을 설정할 수 있습니다.

규칙을 정의하여 확인란을 적응형 양식에 동적으로 추가할 수 있습니다. 사용자 지정 함수, 양식 개체 또는 개체 속성을 사용하여 규칙을 정의할 수 있습니다.

![속성 설정](assets/set_property_rule_new.png)

사용자 지정 함수를 기반으로 규칙을 정의하려면 **[!UICONTROL 함수 출력]** 드롭다운 목록에서 사용자 지정 함수를 드래그하여 **[!UICONTROL 함수]** 탭. 조건 작업이 충족되면 사용자 지정 함수에 정의된 확인란 수가 적응형 양식에 추가됩니다.

양식 개체를 기반으로 규칙을 정의하려면 **[!UICONTROL 양식 개체]** 드롭다운 목록에서 양식 객체를 드래그하여 놓습니다 **[!UICONTROL 양식 개체]** 탭. 조건 작업이 충족되면 양식 개체에 정의된 확인란 수가 적응형 양식에 추가됩니다.

개체 속성을 기반으로 한 속성 설정 규칙을 사용하면 적응형 양식에 포함된 다른 개체 속성을 기반으로 적응형 양식의 확인란 수를 추가할 수 있습니다.

다음 그림은 적응형 양식의 드롭다운 목록 수에 따라 확인란을 동적으로 추가하는 예를 보여 줍니다.

![개체 속성](assets/object_property_set_property_new.png)

**[!UICONTROL 값 지우기]** 지정된 개체의 값을 지웁니다.

**[!UICONTROL 포커스 설정]** 지정된 개체에 초점을 설정합니다.

**[!UICONTROL 양식 저장]** 양식을 저장합니다.

**[!UICONTROL Forms 제출]** 양식을 제출합니다.

**[!UICONTROL 양식 재설정]** 양식을 재설정합니다.

**[!UICONTROL 양식 유효성 검사]** 양식의 유효성을 검사합니다.

**[!UICONTROL 인스턴스 추가]** 지정된 반복 가능한 패널 또는 테이블 행의 인스턴스를 추가합니다.

**[!UICONTROL 인스턴스 제거]** 지정된 반복 가능한 패널 또는 테이블 행의 인스턴스를 제거합니다.

**[!UICONTROL 다음으로 이동]** 다른 페이지로 이동합니다. <!--Interactive Communications,--> 응용 Forms, 이미지 또는 문서 조각과 같은 기타 자산 또는 외부 URL입니다. <!-- For more information, see [Add button to the Interactive Communication](create-interactive-communication.md#addbuttontothewebchannel). -->

### [!UICONTROL 값 설정 - ] {#set-value-of}

다음 **[!UICONTROL 값 설정]** 규칙 유형을 사용하면 지정된 조건이 충족되는지 여부에 따라 양식 객체의 값을 설정할 수 있습니다. 이 값은 다른 개체의 값, 리터럴 문자열, 수학 식 또는 함수에서 파생된 값, 다른 개체의 속성 값 또는 양식 데이터 모델 서비스의 출력으로 설정할 수 있습니다. 마찬가지로 함수 또는 수학 표현식에서 파생된 구성 요소, 문자열, 속성 또는 값에 대한 조건을 확인할 수 있습니다.

다음 **값 설정** 패널 및 도구 모음 단추와 같은 모든 양식 개체에는 규칙 유형을 사용할 수 없습니다. 규칙의 표준 세트 값은 다음 구조를 갖습니다.

개체 A 값을 다음으로 설정:

(문자열 ABC) OR (개체 속성 X of Object C) OR (함수의 값) OR (수학 표현식의 값) OR (데이터 모델 서비스 또는 웹 서비스의 출력 값);

시기(선택 사항):

(조건 1, 조건 2 및 조건 3)은 참인 경우

다음 예제에서는 값을 `dependentid` 필드를 입력으로 지정하고 `Relation` 결과 필드 `Relation` 그 주장 `getDependent` 양식 데이터 모델 서비스입니다.

![Set-value-web-service](assets/set-value-web-service.png)

양식 데이터 모델 서비스를 사용한 값 설정 규칙의 예

>[!NOTE]
>
>또한 규칙 값 설정 을 사용하여 양식 데이터 모델 서비스 또는 웹 서비스의 출력에서 드롭다운 목록 구성 요소의 모든 값을 채울 수 있습니다. 그러나 선택한 출력 인수가 배열 형식인지 확인합니다. 배열에 반환되는 모든 값은 지정된 드롭다운 목록에서 사용할 수 있게 됩니다.

### [!UICONTROL 표시] {#show}

사용 **[!UICONTROL 표시]** 규칙 유형에서는 조건을 만족하는지 여부에 따라 양식 개체를 표시하거나 숨기는 규칙을 작성할 수 있습니다. 또한 규칙 표시 유형은 조건이 충족되지 않거나 반환되는 경우 숨기기 작업을 트리거합니다 `False`.

일반적인 Show 규칙은 다음과 같이 구성됩니다.

`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`

### [!UICONTROL 숨기기] {#hide}

규칙 표시 유형과 유사하게, **[!UICONTROL 숨기기]** 조건을 충족하는지 여부에 따라 양식 개체를 표시하거나 숨길 규칙 유형입니다. 또한 숨기기 규칙 유형은 조건이 충족되지 않거나 반환되는 경우 표시 작업을 트리거합니다 `False`.

일반적인 숨기기 규칙은 다음과 같이 구성됩니다.

`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`

### [!UICONTROL 사용] {#enable}

다음 **[!UICONTROL 활성화]** 규칙 유형을 사용하면 조건이 충족되는지 여부에 따라 양식 개체를 활성화하거나 비활성화할 수 있습니다. 또한 규칙 활성화 유형은 조건이 충족되지 않거나 반환되는 경우 비활성화 작업을 트리거합니다 `False`.

일반적인 사용 규칙은 다음과 같이 구조화됩니다.

`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`

### [!UICONTROL 사용 안함] {#disable}

규칙 사용 유형과 유사하며, **[!UICONTROL 비활성화]** 규칙 유형을 사용하면 조건이 충족되는지 여부에 따라 양식 개체를 활성화하거나 비활성화할 수 있습니다. 또한 Disable 규칙 유형은 조건이 충족되지 않거나 반환되는 경우 Enable 작업을 트리거합니다 `False`.

일반적인 비활성화 규칙은 다음과 같이 구조화됩니다.

`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

### [!UICONTROL 유효성 검사] {#validate}

다음 **[!UICONTROL 유효성 검사]** 규칙 유형은 표현식을 사용하여 필드의 값의 유효성을 검사합니다. 예를 들어, 이름을 지정하는 텍스트 상자에 특수 문자나 숫자가 포함되어 있지 않은지 확인할 표현식을 작성할 수 있습니다.

일반적인 유효성 검사 규칙은 다음과 같이 구성됩니다.

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>지정한 값이 유효성 검사 규칙을 준수하지 않으면 사용자에게 유효성 검사 메시지를 표시할 수 있습니다. 에서 메시지를 지정할 수 있습니다. **[!UICONTROL 스크립트 유효성 검사 메시지]** 사이드바의 구성 요소 속성에 있는 필드입니다.

![스크립트 유효성 검사](assets/script-validation.png)

### [!UICONTROL 옵션 설정] {#setoptionsof}

다음 **[!UICONTROL 옵션 설정]** 규칙 유형을 사용하면 확인란을 적응형 양식에 동적으로 추가할 규칙을 정의할 수 있습니다. 양식 데이터 모델 또는 사용자 지정 함수를 사용하여 규칙을 정의할 수 있습니다.

사용자 지정 함수를 기반으로 규칙을 정의하려면 **[!UICONTROL 함수 출력]** 드롭다운 목록에서 사용자 지정 함수를 드래그하여 **[!UICONTROL 함수]** 탭. 사용자 지정 함수에 정의된 확인란 수가 적응형 양식에 추가됩니다.

![사용자 지정 함수](assets/custom_functions_set_options_new.png)

사용자 지정 함수를 만들려면 다음을 참조하십시오 [규칙 편집기의 사용자 지정 함수](#custom-functions).

양식 데이터 모델을 기반으로 규칙을 정의하려면

1. 선택 **[!UICONTROL 서비스 출력]** 드롭다운 목록에서 을 선택합니다.
1. 데이터 모델 개체를 선택합니다.
1. 데이터 모델 개체 속성을 **[!UICONTROL 표시 값]** 드롭다운 목록. 적응형 양식의 확인란 수는 데이터베이스의 해당 속성에 대해 정의된 인스턴스 수에서 파생됩니다.
1. 데이터 모델 개체 속성을 **[!UICONTROL 값 저장]** 드롭다운 목록.

![FDM 설정 옵션](assets/fdm_set_options_new.png)

## 규칙 편집기 사용자 인터페이스 이해 {#understanding-the-rule-editor-user-interface}

규칙 편집기는 규칙을 작성하고 관리할 수 있는 포괄적이고 간단한 사용자 인터페이스를 제공합니다. 작성 모드의 적응형 양식 내에서 규칙 편집기 사용자 인터페이스를 시작할 수 있습니다.

규칙 편집기 사용자 인터페이스를 시작하려면 다음을 수행하십시오.

1. 작성 모드에서 적응형 양식을 엽니다.
1. 규칙을 작성할 양식 개체를 탭하고 구성 요소 도구 모음에서 탭하기 ![편집 규칙](assets/edit-rules-icon.svg). 규칙 편집기 사용자 인터페이스가 표시됩니다.

   ![create-rules](assets/create-rules.png)

   선택한 양식 객체의 모든 기존 규칙이 이 보기에 나열됩니다. 기존 규칙 관리에 대한 자세한 내용은 [규칙 관리](rule-editor.md#p-manage-rules-p).

1. 탭 **[!UICONTROL 만들기]** 새 규칙을 작성하는 방법 규칙 편집기 사용자 인터페이스의 시각적 편집기는 규칙 편집기를 처음 시작할 때 기본적으로 열립니다.

   ![규칙 편집기 UI](assets/rule-editor-ui.png)

규칙 편집기 UI의 각 구성 요소를 자세히 살펴보겠습니다.

### A. 구성 요소 규칙 표시 {#a-component-rule-display}

규칙 편집기를 시작한 적응형 양식 개체의 제목과 현재 선택한 규칙 유형을 표시합니다. 위의 예에서 규칙 편집기는 봉급이라는 적응형 양식 객체에서 시작되며 선택된 규칙 유형은 When입니다.

### B. 양식 객체 및 함수 {#b-form-objects-and-functions-br}

규칙 편집기 사용자 인터페이스의 왼쪽 창에는 두 개의 탭이 있습니다. **[!UICONTROL Forms 개체]** 및 **[!UICONTROL 함수]**.

양식 객체 탭에는 적응형 양식에 포함된 모든 객체의 계층 뷰가 표시됩니다. 객체의 제목과 유형을 표시합니다. 규칙을 작성할 때 양식 개체를 규칙 편집기에 끌어 놓을 수 있습니다. 개체나 함수를 자리 표시자로 끌어다 놓을 때 규칙을 만들거나 편집하는 동안 자리 표시자는 자동으로 적절한 값 유형을 사용합니다.

하나 이상의 유효한 규칙이 적용된 양식 개체는 녹색 점으로 표시됩니다. 양식 개체에 적용된 규칙이 올바르지 않으면 양식 개체가 노란색 점으로 표시됩니다.

함수 탭에는 Sum Of, Min Of, Max Of, Average Of, Number And Validate Form과 같은 기본 함수 세트가 포함되어 있습니다. 이 함수를 사용하여 반복 가능한 패널 및 테이블 행의 값을 계산하고 규칙을 작성할 때 작업 및 조건 문에서 사용할 수 있습니다. 그러나 다음을 만들 수 있습니다 [사용자 지정 함수](#custom-functions) 그것도.

![함수 탭](assets/functions.png)

>[!NOTE]
>
>Forms 개체 및 함수 탭에서 개체 및 함수 이름 및 제목에 대한 텍스트 검색을 수행할 수 있습니다.

양식 개체의 왼쪽 트리에서 양식 개체를 탭하여 각 개체에 적용된 규칙을 표시할 수 있습니다. 다양한 양식 객체의 규칙을 탐색할 수 있을 뿐만 아니라 양식 객체 간에 규칙을 복사하여 붙여넣을 수도 있습니다. 자세한 내용은 [규칙 복사-붙여넣기](rule-editor.md#p-copy-paste-rules-p).

### C. 양식 개체 및 함수 전환 {#c-form-objects-and-functions-toggle-br}

토글 버튼을 탭하면 양식 객체 및 함수 창을 토글합니다.

### D. 시각적 규칙 편집기 {#visual-rule-editor}

시각적 규칙 편집기는 규칙을 작성하는 규칙 편집기 사용자 인터페이스의 시각적 편집기 모드에 있는 영역입니다. 규칙 유형을 선택하고 그에 따라 조건 및 작업을 정의할 수 있습니다. 규칙에서 조건 및 작업을 정의할 때 [양식 객체 및 함수] 창에서 양식 객체 및 함수를 드래그하여 놓을 수 있습니다.

시각적 규칙 편집기 사용에 대한 자세한 내용은 [규칙 쓰기](rule-editor.md#p-write-rules-p).
<!-- 
### E. Visual-code editors switcher {#e-visual-code-editors-switcher}

Users in the forms-power-users group can access code editor. For other users, code editor is not available. If you have the rights, you can switch from visual editor mode to code editor mode of the rule editor, and vice versa, using the switcher right above the rule editor. When you launch rule editor the first time, it opens in the visual editor mode. You can write rules in the visual editor mode or switch to the code editor mode to write a rule script. However, note that if you modify a rule or write a rule in code editor, you cannot switch back to the visual editor for that rule unless you clear the code editor.

[!DNL Experience Manager Forms] tracks the rule editor mode you used last to write a rule. When you launch the rule editor next time, it opens in that mode. However, you can also configure a default mode to open the rule editor in the specified mode. To do so:

1. Go to [!DNL Experience Manager] web console at `https://[host]:[port]/system/console/configMgr`.
1. Click to edit **[!UICONTROL Adaptive Form Configuration Service]**.
1. choose **[!UICONTROL Visual Editor]** or **[!UICONTROL Code Editor]** from the **[!UICONTROL Default Mode for Rule Editor]** drop-down

1. Click **[!UICONTROL Save]**.
-->

### E. 완료 및 취소 단추 {#done-and-cancel-buttons}

다음 **[!UICONTROL 완료]** 버튼을 사용하여 규칙을 저장할 수 있습니다. 불완전한 규칙을 저장할 수 있습니다. 그러나 불완전함은 유효하지 않으며 실행되지 않습니다. 양식 개체에 저장된 규칙은 다음에 동일한 양식 개체에서 규칙 편집기를 시작할 때 나열됩니다. 해당 보기에서 기존 규칙을 관리할 수 있습니다. 자세한 내용은 [규칙 관리](rule-editor.md#p-manage-rules-p).

다음 **[!UICONTROL 취소]** 버튼은 규칙에 대한 모든 변경 사항을 무시하고 규칙 편집기를 닫습니다.

## 규칙 쓰기 {#write-rules}

시각적 규칙 편집기를 사용하여 규칙을 작성할 수 있습니다 &lt;!>— 또는 코드 편집기>를 선택합니다. 규칙 편집기를 처음 실행하면 시각적 편집기 모드에서 열립니다. 코드 편집기 모드 및 쓰기 규칙으로 전환할 수 있습니다. 그러나 코드 편집기에서 규칙을 작성하거나 수정하는 경우 코드 편집기를 지우지 않으면 해당 규칙에 대한 시각적 편집기로 전환할 수 없습니다. 다음에 규칙 편집기를 실행하면 마지막으로 규칙을 만드는 데 사용한 모드로 열립니다.

먼저 시각적 편집기를 사용하여 규칙을 작성하는 방법을 살펴보겠습니다.

### 시각적 편집기 사용 {#using-visual-editor}

다음 예제 양식을 사용하여 시각적 편집기에서 규칙을 만드는 방법을 이해하겠습니다.

![Create-rule-example](assets/create-rule-example.png)

대출 신청 양식의 대출 요건 섹션은 지원자가 혼인 상태, 임금 및 결혼한 경우 배우자의 급여를 지정해야 합니다. 사용자 입력을 기반으로, 규칙은 대출 자격 금액을 계산하고 대출 자격 필드에 표시됩니다. 다음 규칙을 적용하여 시나리오를 구현합니다.

* 배우자 임금 필드는 혼인상태만 표시됩니다.
* 대출 자격 금액은 전체 봉급의 50%입니다.

규칙을 작성하려면 다음 단계를 수행하십시오.

1. 먼저, 혼인 상태 라디오 버튼에 대해 선택한 옵션 사용자에 따라 배우자 임금 필드의 가시성을 제어하는 규칙을 작성합니다.

   작성 모드에서 대출 신청 양식을 엽니다. 탭하기 **[!UICONTROL 혼인 상태]** 구성 요소 및 탭 ![편집 규칙](assets/edit-rules-icon.svg). 다음 을 누릅니다 **[!UICONTROL 만들기]** 규칙 편집기를 실행하려면 를 클릭합니다.

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1.png)

   규칙 편집기를 실행하면 기본적으로 When 규칙이 선택됩니다. 또한 규칙 편집기를 시작한 양식 객체(이 경우 혼인 상태)는 When 문에 지정됩니다.

   선택한 개체를 변경하거나 수정할 수는 없지만, 아래와 같이 규칙 드롭다운을 사용하여 다른 규칙 유형을 선택할 수 있습니다. 다른 개체에 규칙을 만들려면 [취소]를 탭하여 규칙 편집기를 종료하고 원하는 양식 개체에서 다시 실행하십시오.

1. 탭 **[!UICONTROL 상태 선택]** 드롭다운 및 선택 **[!UICONTROL 다음과 같음]**. 다음 **[!UICONTROL 문자열 입력]** 필드가 나타납니다.

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2.png)

   결혼 상태 라디오 버튼에서 **[!UICONTROL 기혼]** 및 **[!UICONTROL 단일]** 옵션이 할당됨 **0** 및 **1** 값을 반환합니다. 아래와 같이 편집 라디오 단추 대화 상자의 제목 탭에서 지정된 값을 확인할 수 있습니다.

   ![규칙 편집기의 라디오 단추 값](assets/radio-button-values.png)

1. 에서 **[!UICONTROL 문자열 입력]** 규칙의 필드에서 다음을 지정합니다. **0**.

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4.png)

   조건을 로 정의했습니다. `When Marital Status is equal to Married`. 다음으로, 이 조건이 True인 경우 수행할 작업을 정의합니다.

1. Then 문에서 **[!UICONTROL 표시]** 에서 **[!UICONTROL 작업 선택]** 드롭다운.

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5.png)

1. 을(를) 끌어서 놓습니다 **[!UICONTROL 배우자 임금]** 필드 **[!UICONTROL 개체를 끌어 놓거나 여기를 선택하십시오.]** 필드. 또는 **[!UICONTROL 개체를 끌어 놓거나 여기를 선택하십시오.]** 필드를 선택하고 **[!UICONTROL 배우자 임금]** 폼의 모든 양식 개체를 나열하는 팝업 메뉴의 필드

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6.png)

   규칙이 규칙 편집기에 다음과 같이 나타납니다.

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7.png)

1. 탭 **[!UICONTROL 완료]** 규칙을 저장하려면 을 클릭합니다.

1. 1단계부터 5단계까지 반복하여 배우자 상태가 단일 상태인 경우 배우자 임금 필드를 숨길 수 있습니다. 규칙이 규칙 편집기에 다음과 같이 나타납니다.

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8.png)

   >[!NOTE]
   >
   >또는, 부부직 상태 필드에 두 개의 &quot;When rules on the Dimensional Status&quot; 필드 대신 배우자 임금 필드에 하나의 Show 규칙을 작성하여 동일한 행동을 구현할 수 있습니다.

   ![write-rules-visual-editor-9](assets/write-rules-visual-editor-9.png)

1. 다음으로, 전체 임금의 50%인 대출 자격 금액을 계산하는 규칙을 작성하여 대출 자격 필드에 표시합니다. 이러한 결과를 얻으려면 **[!UICONTROL 값 설정]** 대출 자격 필드에 대한 규칙.

   작성 모드에서 **[!UICONTROL 대출 자격]** 필드 및 탭 ![편집 규칙](assets/edit-rules-icon.svg). 다음 을 누릅니다 **[!UICONTROL 만들기]** 규칙 편집기를 실행하려면 를 클릭합니다.

1. 선택 **[!UICONTROL 값 설정]** 규칙 드롭다운에서 규칙을 만듭니다.

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10.png)

1. 탭 **[!UICONTROL 선택 옵션]** 을(를) 선택합니다. **[!UICONTROL 수식]**. 수학 표현식을 작성하는 필드가 열립니다.

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11.png)

1. 표현식 필드에서 다음을 수행합니다.

   * Forms 개체 탭에서 을(를) 선택하거나 드래그하여 놓습니다. **[!UICONTROL 급여]** 첫 번째 필드의 필드 **[!UICONTROL 개체를 끌어 놓거나 여기를 선택하십시오.]** 필드.

   * 선택 **[!UICONTROL 플러스]** 에서 **[!UICONTROL 연산자 선택]** 필드.

   * Forms 개체 탭에서 을(를) 선택하거나 드래그하여 놓습니다. **[!UICONTROL 배우자 임금]** 다른 필드의 필드 **[!UICONTROL 개체를 끌어 놓거나 여기를 선택하십시오.]** 필드.

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. 다음으로 표현식 필드 주위에 강조 표시된 영역을 탭하고 탭합니다 **[!UICONTROL 표현식 확장]**.

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13.png)

   확장 표현식 필드에서 **[!UICONTROL 나누기]** 에서 **[!UICONTROL 연산자 선택]** 필드 및 **[!UICONTROL 숫자]** 에서 **[!UICONTROL 선택 옵션]** 필드. 그런 다음 **[!UICONTROL 2개]** 숫자 필드에서 을 클릭합니다.

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14.png)

   >[!NOTE]
   >
   >옵션 선택 필드에서 구성 요소, 함수, 수학 표현식 및 속성 값을 사용하여 복잡한 표현식을 만들 수 있습니다.

   다음으로, True를 반환하면 표현식이 실행되는 조건을 만듭니다.

1. 탭 **[!UICONTROL 조건 추가]** When 문을 추가하려면

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15.png)

   When 문에서:

   * Forms 개체 탭에서 을(를) 선택하거나 드래그하여 놓습니다. **[!UICONTROL 혼인 상태]** 첫 번째 필드의 필드 **[!UICONTROL 개체를 끌어 놓거나 여기를 선택하십시오.]** 필드.

   * 선택 **[!UICONTROL 다음과 같음]** 에서 **[!UICONTROL 연산자 선택]** 필드.

   * 다른 문자열에서 문자열 선택 **[!UICONTROL 개체를 끌어 놓거나 여기를 선택하십시오.]** 필드 및 지정 **[!UICONTROL 기혼]** 에서 **[!UICONTROL 문자열 입력]** 필드.

   규칙이 마지막으로 규칙 편집기에 다음과 같이 나타납니다.  ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16.png)

1. **[!UICONTROL Done]**&#x200B;을 누릅니다. 규칙을 저장합니다.

1. 7~14단계를 반복하여 혼인 상태가 단일(Single)인 경우 대출 자격을 계산할 다른 규칙을 정의합니다. 규칙이 규칙 편집기에 다음과 같이 나타납니다.

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17.png)

>[!NOTE]
>
>또는, 배우자 임금 필드를 표시하거나 숨기도록 생성한 When 규칙에서 대출 자격을 계산하기 위해 값 설정 규칙을 사용할 수 있습니다. 혼인 상태가 단일(Single)이면 결과 결합된 규칙은 규칙 편집기에서 다음과 같이 나타납니다.
>
>마찬가지로 혼인 상태가 기혼인 경우 배우자 임금 필드의 가시성을 제어하고 대출 자격을 계산하는 결합 규칙을 작성할 수 있습니다.

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18.png)

<!-- ### Using code editor {#using-code-editor}

Users added to the forms-power-users group can use code editor. The rule editor auto generates the JavaScript code for any rule you create using visual editor. You can switch from visual editor to the code editor to view the generated code. However, if you modify the rule code in the code editor, you cannot switch back to the visual editor. If you prefer writing rules in code editor rather than visual editor, you can write rules afresh in the code editor. The visual-code editors switcher helps you switch between the two modes.

The code editor JavaScript is the expression language of Adaptive Forms. All the expressions are valid JavaScript expressions and use Adaptive Forms scripting model APIs. These expressions return values of certain types. For the complete list of Adaptive Forms classes, events, objects, and public APIs, see [JavaScript Library API reference for Adaptive Forms](https://helpx.adobe.com/experience-manager/6-5/forms/javascript-api/index.html).

For more information about guidelines to write rules in the code editor, see [Adaptive Form Expressions](adaptive-form-expressions.md).

While writing JavaScript code in the rule editor, the following visual cues help you with the structure and syntax:

* Syntax highlights

* Auto Indentation

* Hints and suggestions for Form objects, functions, and their properties

* Auto completion of form component names and common JavaScript functions

![javascriptruleeditor](assets/javascriptruleeditor.png)
-->

#### 규칙 편집기의 사용자 지정 함수 {#custom-functions}

기본 기능과는 별도로 *합계* 함수 출력 아래에 나열되는 사용자 정의 함수를 자주 필요한 작성할 수 있습니다. 작성한 함수에 `jsdoc` 위에 있는 것입니다.

함께 `jsdoc` 필수 여부:

* 사용자 지정 구성 및 설명을 원하는 경우
* 함수를 선언할 방법에는 여러 가지가 있으므로 `JavaScript,` 및 주석을 사용하면 함수를 계속 추적할 수 있습니다.

규칙 편집기는 스크립트 및 사용자 지정 함수에 대한 JavaScript ES2015 구문을 지원합니다.
자세한 내용은 [jsdoc.app](https://jsdoc.app/).

지원됨 `jsdoc` 태그:

* **비공개**
구문: 개인 함수는 사용자 지정 함수로 포함되지 않습니다.`@private`
개인 함수는 사용자 지정 함수로 포함되지 않습니다.

* **이름**
구문: 또는 `@name funcName <Function Name>`
또는 `,` 다음을 사용할 수 있습니다. `@function funcName <Function Name>` **또는** `@func` `funcName <Function Name>`.
   `funcName` 는 함수의 이름입니다(공백은 허용되지 않음).
   `<Function Name>` 는 함수의 표시 이름입니다.

* **멤버**
구문: 함수에 네임스페이스를 연결합니다.`@memberof namespace`
함수에 네임스페이스를 연결합니다.

* **매개 변수**
구문: 또는 다음을 사용할 수 있습니다. `@param {type} name <Parameter Description>`
또는 다음을 사용할 수 있습니다. `@argument` `{type} name <Parameter Description>` **또는** `@arg` `{type}` `name <Parameter Description>`.
함수에서 사용하는 매개 변수를 표시합니다. 함수에는 여러 매개 변수 태그와 발생 순서로 각 매개 변수에 대해 하나의 태그가 있을 수 있습니다.
   `{type}` 매개 변수 유형을 나타냅니다. 허용되는 매개 변수 유형은 다음과 같습니다.

   1. 문자열
   1. 개수
   1. 부울
   1. 범위

   범위는 적응형 양식의 필드를 나타냅니다. 양식에서 레이지 로드를 사용하는 경우 `scope` 을 눌러 해당 필드에 액세스합니다. 필드가 로드되거나 필드가 전역 것으로 표시된 경우 필드에 액세스할 수 있습니다.

   모든 매개 변수 유형은 위의 항목 중 하나에 따라 분류됩니다. 어떤 것도 지원되지 않습니다. 위의 유형 중 하나를 선택해야 합니다. 유형은 대/소문자를 구분하지 않습니다. 매개 변수에는 공백을 사용할 수 없습니다 `name`. `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* **반환 유형**
구문: 또는, `@return {type}`
또는, `@returns {type}`.
함수(예: 목표)에 대한 정보를 추가합니다.
{type}은(는) 함수의 반환 형식을 나타냅니다. 허용되는 반환 유형은 다음과 같습니다.

   1. 문자열
   1. 개수
   1. 부울

   다른 모든 반환 유형은 위의 중 하나에 분류됩니다. 어떤 것도 지원되지 않습니다. 위의 유형 중 하나를 선택해야 합니다. 반환 유형은 대/소문자를 구분하지 않습니다.

   * **이**
구문: 
`@this currentComponent`
   @this을 사용하여 규칙이 작성된 적응형 양식 구성 요소를 참조합니다.

   다음 예는 필드 값을 기반으로 합니다. 다음 예제에서는 규칙이 양식의 필드를 숨깁니다. 다음 `this` 부분 `this.value` 는 규칙이 작성된 기본 적응형 양식 구성 요소를 나타냅니다.

   ```
      /**
      * @function myTestFunction
      * @this currentComponent
      * @param {scope} scope in which code inside function will be executed.
      */
      myTestFunction = function (scope) {
         if(this.value == "O"){
               scope.age.visible = true;
         } else {
            scope.age.visible = false;
         }
      }
   ```

   >[!NOTE]
   >
   >사용자 지정 함수가 요약에 사용되기 전의 설명. 요약은 태그가 나타날 때까지 여러 줄로 확장할 수 있습니다. 규칙 빌더에서 간결한 설명을 위해 크기를 단일 로 제한합니다.

**사용자 지정 함수 추가**

예를 들어 정사각형의 영역을 계산하는 사용자 지정 함수를 추가하려고 합니다. 사이드 길이는 사용자 지정 함수에 대한 사용자 입력이며, 양식에서 숫자 상자를 사용하여 수락됩니다. 계산된 출력은 양식의 다른 숫자 상자에 표시됩니다. 사용자 지정 함수를 추가하려면 먼저 클라이언트 라이브러리를 만든 다음 CRX 저장소에 추가해야 합니다.

클라이언트 라이브러리를 만들고 CRX 저장소에 추가하려면 다음 단계를 수행합니다.

1. 클라이언트 만들기라이브러리에 다음 단계를 수행하십시오. 자세한 내용은 [클라이언트측 라이브러리 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).
1. CRXDE에서 속성을 추가합니다 `categories`문자열 유형 값이 `customfunction` 변환 후 `clientlib` 폴더를 입력합니다.

   >[!NOTE]
   >
   >`customfunction`는 예제 카테고리입니다. 에서 만드는 카테고리의 이름을 선택할 수 있습니다 `clientlib`폴더를 입력합니다.

클라이언트 라이브러리를 CRX 저장소에 추가한 후 적응형 양식에 사용합니다. 사용자 지정 기능을 양식에서 규칙으로 사용할 수 있습니다. 적응형 양식에 클라이언트 라이브러리를 추가하려면 다음 단계를 수행하십시오.

1. 편집 모드에서 양식을 엽니다.
편집 모드에서 양식을 열려면 양식을 선택하고 **[!UICONTROL 열기]**.
1. 편집 모드에서 구성 요소를 선택한 다음 ![필드 수준](assets/select_parent_icon.svg) > **[!UICONTROL 적응형 양식 컨테이너]**&#x200B;를 누른 다음 탭합니다. ![cmppr](assets/configure-icon.svg).
1. 사이드바의 클라이언트 라이브러리 이름에서 클라이언트 라이브러리를 추가합니다. ( `customfunction` 예)

   ![사용자 지정 함수 클라이언트 라이브러리 추가](assets/clientlib.png)

1. 입력 숫자 상자를 선택하고 를 누릅니다 ![편집 규칙](assets/edit-rules-icon.svg) 규칙 편집기를 엽니다.
1. 탭 **[!UICONTROL 규칙 만들기]**. 아래 표시된 옵션을 사용하여 양식의 출력 필드에 입력의 사각형 값을 저장하는 규칙을 만듭니다.

[![사용자 지정 함수를 사용하여 규칙 만들기](assets/add_custom_rule_new.png)](assets/add-custom-rule.png)

1. **[!UICONTROL Done]**&#x200B;을 누릅니다. 사용자 지정 함수가 추가되었습니다.

#### 함수 선언 지원 형식 {#function-declaration-supported-types}

**함수 문**

```javascript
function area(len) {
    return len*len;
}
```

이 함수는 `jsdoc` 댓글.

**함수 표현식**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**함수 표현식 및 문**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**변수로서의 함수 선언**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

제한 사항: 사용자 지정 함수는 함께 있을 경우 변수 목록에서 첫 번째 함수 선언만 선택합니다. 선언된 모든 함수에 함수 표현식을 사용할 수 있습니다.

**Function 선언 as Object**

```javascript
var c = {
    b : {
        /** */
        area : function(len) {
            return len*len;
        }
    }
};
```

>[!NOTE]
>
>를 사용해야 합니다 `jsdoc` 를 반환합니다. 하지만 `jsdoc`댓글이 권장되며 빈 댓글을 포함합니다. `jsdoc`함수를 사용자 지정 함수로 표시하는 주석. 사용자 지정 기능을 기본적으로 처리할 수 있습니다.

## 규칙 관리 {#manage-rules}

양식 개체의 기존 규칙은 개체를 탭하고 탭하면 나열됩니다 ![edit-rules1](assets/edit-rules-icon.svg). 제목과 규칙 요약을 미리 볼 수 있습니다. 또한 UI를 사용하여 전체 규칙 요약을 확장 및 보고, 규칙 순서를 변경하고, 규칙을 편집하고, 규칙을 삭제할 수 있습니다.

![목록 규칙](assets/list-rules.png)

규칙에 대해 다음 작업을 수행할 수 있습니다.

* **확장/축소**: 규칙 목록의 콘텐츠 열에는 규칙 콘텐츠가 표시됩니다. 전체 규칙 컨텐츠가 기본 보기에 표시되지 않으면 ![expand-rule-content](assets/Smock_ChevronDown.svg) 를 확장하려면 다음을 수행하십시오.

* **재정렬**: 새로 만드는 모든 규칙이 규칙 목록 하단에 스택됩니다. 규칙은 위에서 아래로 실행됩니다. 맨 위에 있는 규칙은 먼저 실행되며, 그 뒤에는 같은 유형의 다른 규칙이 실행됩니다. 예를 들어, When, Show, Enable 및 When 규칙이 각각 상단의 첫 번째, 두 번째, 세 번째 및 네 번째 위치에 있는 경우, 맨 위의 When 규칙이 먼저 실행되고 네 번째 위치에 When 규칙이 실행됩니다. 그런 다음 표시 및 활성화 규칙이 실행됩니다.
을 탭하여 규칙 순서를 변경할 수 있습니다 ![sort-rules](assets/sort-rules.svg) 드래그하여 목록에서 원하는 순서로 놓습니다.

* **편집**: 규칙을 편집하려면 규칙 제목 옆에 있는 확인란을 선택합니다. 규칙을 편집하고 삭제하는 옵션이 나타납니다. 탭 **[!UICONTROL 편집]** 규칙 편집기에서 선택한 규칙을 열려면 <!-- in visual  or code editor mode depending on the mode used to create the rule -->.

* **삭제**: 규칙을 삭제하려면 규칙을 선택하고 **[!UICONTROL 삭제]**.

* **활성화/비활성화**: 규칙 사용을 일시적으로 중단해야 하는 경우 하나 이상의 규칙을 선택하고 탭할 수 있습니다 **[!UICONTROL 비활성화]** 작업 도구 모음에서 를 클릭하여 비활성화합니다. 규칙이 비활성화되면 런타임 시 실행되지 않습니다. 비활성화된 규칙을 활성화하려면 선택하고 작업 도구 모음에서 활성화 를 탭할 수 있습니다. 규칙의 상태 열에는 규칙이 활성화되었는지 아니면 비활성화되었는지 표시됩니다.

![규칙 비활성화](assets/disablerule.png)

## 규칙 복사-붙여넣기 {#copy-paste-rules}

한 필드에서 다른 유사한 필드에 규칙을 복사하여 붙여넣으면 시간을 절약할 수 있습니다.

규칙을 복사-붙여넣으려면 다음을 수행합니다.

1. 규칙을 복사할 양식 개체를 탭하고 구성 요소 도구 모음에서 ![규칙 편집](assets/edit-rules-icon.svg). 양식 개체가 선택된 상태로 규칙 편집기 사용자 인터페이스가 나타나고 기존 규칙이 나타납니다.

   ![규칙 복사](assets/copyrule.png)

   기존 규칙 관리에 대한 자세한 내용은 [규칙 관리](rule-editor.md#p-manage-rules-p).

1. 규칙 제목 옆에 있는 확인란을 선택하면 규칙을 관리하는 옵션이 표시됩니다. Tap **[!UICONTROL Copy]**.

   ![copyrule2](assets/copyrule2.png)

1. 규칙을 붙여넣을 다른 양식 개체를 선택하고 탭합니다 **[!UICONTROL 붙여넣기]**. 또한 규칙을 편집하여 규칙을 변경할 수 있습니다.

   >[!NOTE]
   >
   >양식 개체가 복사된 규칙의 이벤트를 지원하는 경우에만 다른 양식 개체에 규칙을 붙여넣을 수 있습니다. 예를 들어, 버튼은 클릭 이벤트를 지원합니다. 클릭 이벤트가 있는 규칙을 단추에는 붙여넣을 수 있지만 확인상자에는 붙여 넣을 수 없습니다.

1. 탭 **[!UICONTROL 완료]** 규칙을 저장하려면 을 클릭합니다.

## 중첩 표현식 {#nestedexpressions}

규칙 편집기를 사용하면 여러 AND 및 OR 연산자를 사용하여 중첩된 규칙을 만들 수 있습니다. 규칙에서 여러 AND 및 OR 연산자를 혼합할 수 있습니다.

다음은 필요한 조건이 충족될 때 하위 보호 대상의 자격에 대한 메시지를 사용자에게 표시하는 중첩 규칙의 예입니다.

![복잡한 표현식](assets/complexexpression.png)

규칙 내에서 조건을 드래그 앤 드롭하여 편집할 수도 있습니다. 핸들을 탭하고 마우스로 가리키기( ![핸들](assets/drag-handle.svg))를 클릭하여 제품에서 사용할 수 있습니다. 포인터가 아래 표시된 대로 손 기호로 바뀌면 규칙 내의 아무 곳에나 조건을 드래그하여 놓습니다. 규칙 구조가 변경됩니다.

![드래그 앤 드롭](assets/drag-and-drop.png)

## 날짜 표현식 조건 {#dateexpression}

규칙 편집기를 사용하면 날짜 비교를 사용하여 조건을 만들 수 있습니다.

다음은 주택에 대한 저당권이 이미 설정된 경우 정적 텍스트 객체를 표시하는 예제 조건이며, 사용자는 날짜 필드를 채워 나타냅니다.

사용자가 입력한 속성의 저당권 날짜가 지난 경우 적응형 양식에 소득 계산에 대한 메모가 표시됩니다. 다음 규칙은 사용자가 입력한 날짜를 현재 날짜와 비교하고 사용자가 입력한 날짜가 현재 날짜보다 빠른 경우 양식에 텍스트 메시지(소득)가 표시됩니다.

![날짜 표현식 조건](assets/dateexpressioncondition.png)

채워진 날짜가 현재 날짜보다 이전이면 양식에 텍스트 메시지(소득)가 다음과 같이 표시됩니다.

![날짜 표현식 조건이 충족됨](assets/dateexpressionconditionmet.png)

## 숫자 비교 조건 {#number-comparison-conditions}

규칙 편집기를 사용하면 두 숫자를 비교하는 조건을 만들 수 있습니다.

다음은 지원자가 현재 주소에 남아 있는 개월 수가 36개월 미만인 경우 정적 텍스트 개체를 표시하는 예제 조건입니다.

![숫자 비교 조건](assets/numbercomparisoncondition.png)

36개월 미만의 거주자임을 나타내는 양식에는 더 많은 거주지를 요청할 수 있다는 알림이 표시됩니다.

![추가 증명 요청](assets/additionalproofrequested.png)

<!-- ## Impact of rule editor on existing scripts {#impact-of-rule-editor-on-existing-scripts}

In [!DNL Experience Manager Forms] versions prior to [!DNL Experience Manager 6.1 Forms] feature pack 1, form authors and developers used to write expressions in the Scripts tab of the Edit component dialog to add dynamic behavior to Adaptive Forms. The Scripts tab is now replaced by the rule editor.

Any scripts or expressions that you must have written in the Scripts tab are available in the rule editor. While you cannot view or edit them in visual editor, if you are a part of the forms-power-users group you can edit scripts in code editor. -->

## 규칙 예 {#example}

### 양식 데이터 모델 서비스 호출 {#invoke}

웹 서비스를 고려해 보십시오 `GetInterestRates` EMI와 이율을 포함한 대출 계획을 반환하는 데 대출 금액, 종신 재직권, 신용도 등이 포함되어 있습니다. 웹 서비스를 데이터 소스로 사용하여 양식 데이터 모델을 만듭니다. 데이터 모델 개체 및 `get` 양식 모델에 대한 서비스입니다. 이 서비스는 양식 데이터 모델의 서비스 탭에 나타납니다. 그런 다음 데이터 모델 개체의 필드를 포함하는 적응형 양식을 만들어 대출 금액, 종신 및 신용 점수에 대한 사용자 입력을 캡처합니다. 계획 세부 정보를 가져오기 위해 웹 서비스를 트리거하는 단추를 추가합니다. 출력은 적절한 필드에 입력됩니다.

다음 규칙은 예제 시나리오를 수행하기 위해 서비스 호출 작업을 구성하는 방법을 보여줍니다.

![Example-invoke-services](assets/example-invoke-services.png)

적응형 양식 규칙을 사용하여 양식 데이터 모델 서비스 호출

### When 규칙을 사용하여 여러 작업 트리거 {#triggering-multiple-actions-using-the-when-rule}

대출 신청 양식에서 대출 지원자가 기존 고객인지 여부를 수집할 수 있습니다. 사용자가 제공하는 정보를 기반으로 고객 ID 필드를 표시하거나 숨겨야 합니다. 또한 사용자가 기존 고객인 경우 고객 ID 필드에 포커스를 설정하려고 합니다. 대출 신청 양식에는 다음과 같은 구성요소가 있습니다.

* 라디오 버튼 **[!UICONTROL 기존 Geometrixx 고객입니까?]**&#x200B;를 채울 수 있습니다 [!UICONTROL 예] 및 [!UICONTROL 아니요] 옵션. Yes의 값은 **0** 그리고 아니요 **1**.

* 텍스트 필드, **[!UICONTROL Geometrixx 고객 ID]**&#x200B;를 눌러 고객 ID를 지정합니다.

라디오 단추에 When 규칙을 작성하여 이 동작을 구현하면 규칙은 시각적 규칙 편집기에 다음과 같이 나타납니다.

![When-rule-example](assets/when-rule-example.png)

시각적 편집기의 규칙

예제 규칙에서 When 섹션의 문은 조건이 됩니다. 이 조건은 True를 반환하면 Then 섹션에 지정된 작업을 실행합니다.

<!-- The rule appears as follows in the code editor.

![when-rule-example-code](assets/when-rule-example-code.png) 

Rule in the code editor -->

### 규칙에서 함수 출력 사용 {#using-a-function-output-in-a-rule}

구매 발주 양식에는 사용자가 자신의 주문을 채우는 다음 테이블이 있습니다. 다음 표에서 확인하십시오.

* 첫 번째 행은 반복 가능하므로 사용자가 여러 제품을 주문하고 다른 수량을 지정할 수 있습니다. 요소 이름은 입니다. `Row1`.
* 반복 가능한 행의 제품 수량 열에 있는 셀의 제목은 수량입니다. 이 셀의 요소 이름은 `productquantity`.
* 테이블의 두 번째 행은 반복 불가능하며 이 행의 제품 수량 열에 있는 셀의 제목은 총 수량입니다.

![예제-function-table](assets/example-function-table.png)

**A.** 행1 **B.** 수량 **C.** 총 수량

이제 모든 제품에 대한 제품 수량 열에 지정된 수량을 추가하고 합계 수량 셀에 합계를 표시하려는 경우 아래 표시된 대로 총 수량 셀에 값 설정 규칙을 작성하여 이 합계를 얻을 수 있습니다.

![예제-function-output](assets/example-function-output.png)

시각적 편집기의 규칙

<!-- he rule appears as follows in the code editor.

![example-function-output-code](assets/example-function-output-code.png)

Rule in the code editor -->

### 표현식을 사용하여 필드 값의 유효성 검사 {#validating-a-field-value-using-expression}

이전 예제에 설명된 구매 발주 양식에서는 10000 이상의 가격이 책정된 제품에 대해 사용자가 두 개 이상의 수량을 주문하지 못하도록 제한하려고 합니다. 이 유효성 검사를 수행하려면 아래 표시된 대로 유효성 검사 규칙을 작성할 수 있습니다.

![예제-유효성 검사](assets/example-validate.png)

시각적 편집기의 규칙

<!-- The rule appears as follows in the code editor.

![example-validate-code](assets/example-validate-code.png)

Rule in the code editor -->
