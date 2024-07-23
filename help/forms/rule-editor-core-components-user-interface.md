---
title: 이 문서에서는 핵심 구성 요소를 기반으로 하는 적응형 양식의 규칙 편집기 사용자 인터페이스에 대해 설명합니다.
description: 적응형 Forms 규칙 편집기를 사용하면 조건, 사용자 입력 및 상호 작용에 따라 작업을 트리거하는 규칙을 작성할 수 있습니다.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
source-git-commit: 780c68f0c21ef94ff6a73ce991370100b1a88db9
workflow-type: tm+mt
source-wordcount: '2298'
ht-degree: 0%

---


# 핵심 구성 요소 기반 적응형 Forms을 위한 규칙 편집기 사용자 인터페이스

핵심 구성 요소를 기반으로 하는 적응형 Forms을 위한 규칙 편집기 사용자 인터페이스는 Adobe Experience Manager(AEM) 내의 양식 작성 프로세스를 향상시킵니다. 사전 정의된 조건, 사용자 입력 및 상호 작용에 따라 작업을 트리거하는 규칙을 작성하여 비즈니스 사용자와 개발자 모두 동적 동작과 복잡한 로직을 양식에 구현할 수 있습니다. 이 기능은 ES10 기능을 비롯한 최신 JavaScript 기능을 지원하며, 규칙 작성 프로세스를 단순화하는 직관적인 시각적 편집기를 제공합니다.
규칙 편집기는 양식 채우기 환경을 간소화하여 정확성과 효율성을 모두 보장하는 데 유용합니다. 이를 통해 패널 및 양식의 유효성 검사 또는 재설정과 양식 개체의 값을 계산하는 사용자 지정 함수를 실행할 수 있습니다. 중첩된 조건에 대한 지원과 양식 데이터 모델 서비스를 호출하는 기능을 갖춘 규칙 편집기 사용자 인터페이스는 반응형, 사용자 친화형 및 적응형 양식을 만드는 데 중요한 구성 요소입니다.

## 규칙 편집기 사용자 인터페이스 이해 {#understanding-the-rule-editor-user-interface}

규칙 편집기는 규칙을 작성하고 관리할 수 있는 포괄적이면서도 간단한 사용자 인터페이스를 제공합니다. 작성 모드의 적응형 양식 내에서 규칙 편집기 사용자 인터페이스를 시작할 수 있습니다.

규칙 편집기 사용자 인터페이스를 시작하려면 다음을 수행합니다.

1. 작성 모드에서 적응형 양식을 엽니다.
1. 규칙을 작성할 양식 개체를 선택하고 구성 요소 도구 모음에서 ![edit-rules](assets/edit-rules-icon.svg)을(를) 선택합니다. 규칙 편집기 사용자 인터페이스가 나타납니다.

   ![create-rules](assets/create-rules.png)

   선택한 양식 객체에 대한 기존 규칙이 이 뷰에 나열됩니다. 기존 규칙 관리에 대한 자세한 내용은 [규칙 관리](rule-editor.md#p-manage-rules-p)를 참조하십시오.

1. 새 규칙을 작성하려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오. 규칙 편집기 사용자 인터페이스의 시각적 편집기는 규칙 편집기를 처음 실행할 때 기본적으로 열립니다.

   ![규칙 편집기 UI](assets/rule-editor-ui.png)

규칙 편집기 UI의 각 구성 요소를 자세히 살펴보겠습니다.

### A. 구성 요소 규칙 표시 {#a-component-rule-display}

규칙 편집기를 시작한 적응형 양식 개체의 제목과 현재 선택된 규칙 유형을 표시합니다. 위의 예에서 규칙 편집기는 질문 1이라는 적응형 양식 객체에서 시작되며 선택한 규칙 유형은 때입니다.

### B. 양식 개체 및 함수 {#b-form-objects-and-functions-br}

규칙 편집기 사용자 인터페이스의 왼쪽 창에는 두 개의 탭, 즉 **[!UICONTROL Forms 개체]** 및 **[!UICONTROL 함수]**&#x200B;가 있습니다.

양식 개체 탭은 적응형 양식에 포함된 모든 개체의 계층 구조 보기를 표시합니다. 객체의 제목과 유형이 표시됩니다. 규칙을 작성할 때 양식 개체를 규칙 편집기로 드래그 앤 드롭할 수 있습니다. 개체 또는 함수를 자리 표시자로 드래그 앤 드롭할 때 규칙을 만들거나 편집할 때 자리 표시자는 자동으로 적절한 값 유형을 사용합니다.

하나 이상의 유효한 규칙이 적용된 양식 개체는 녹색 점으로 표시됩니다. 양식 객체에 적용된 규칙 중 하나라도 유효하지 않으면 양식 객체가 노란색 점으로 표시됩니다.

함수 탭에는 Sum Of, Min Of, Max Of, Average Of, Number 및 Validate Form과 같은 기본 함수 집합이 포함되어 있습니다. 이러한 함수를 사용하여 반복 가능한 패널 및 테이블 행에서 값을 계산하고 규칙을 작성할 때 작업 및 조건 문에서 사용할 수 있습니다. 그러나 사용자 정의 함수를 만들 수도 있습니다.

일부 함수 목록이 그림에 표시됩니다.

![함수 탭](assets/functions.png)

>[!NOTE]
>
>Forms 개체 및 함수 탭에서 개체 및 함수 이름과 제목에 대해 텍스트 검색을 수행할 수 있습니다.

양식 객체의 왼쪽 트리에서 양식 객체를 선택하여 각 객체에 적용된 규칙을 표시할 수 있습니다. 다양한 양식 객체의 규칙을 탐색할 수 있을 뿐만 아니라 양식 객체 간에 규칙을 복사하여 붙여넣을 수도 있습니다. 자세한 내용은 [규칙 복사-붙여넣기](rule-editor.md#p-copy-paste-rules-p)를 참조하십시오.

### C. 양식 개체 및 함수 전환 {#c-form-objects-and-functions-toggle-br}

전환 단추를 누르면 양식 개체 및 함수 창이 전환됩니다.

### D. 시각적 규칙 편집기 {#visual-rule-editor}

시각적 규칙 편집기는 규칙 편집기 사용자 인터페이스의 시각적 편집기 모드에서 규칙을 작성하는 영역입니다. 규칙 유형을 선택하고 그에 따라 조건 및 작업을 정의할 수 있습니다. 규칙에서 조건 및 작업을 정의할 때 양식 개체 및 함수 창에서 양식 개체 및 함수를 드래그 앤 드롭할 수 있습니다.

시각적 규칙 편집기 사용에 대한 자세한 내용은 [규칙 쓰기](rule-editor.md#p-write-rules-p)를 참조하십시오.
<!-- 
### E. Visual-code editors switcher {#e-visual-code-editors-switcher}

Users in the forms-power-users group can access code editor. For other users, code editor is not available. If you have the rights, you can switch from visual editor mode to code editor mode of the rule editor, and conversely, using the switcher right above the rule editor. When you launch rule editor the first time, it opens in the visual editor mode. You can write rules in the visual editor mode or switch to the code editor mode to write a rule script. However, note that if you modify a rule or write a rule in code editor, you cannot switch back to the visual editor for that rule unless you clear the code editor.

[!DNL Experience Manager Forms] tracks the rule editor mode you used last to write a rule. When you launch the rule editor next time, it opens in that mode. However, you can also configure a default mode to open the rule editor in the specified mode. To do so:

1. Go to [!DNL Experience Manager] web console at `https://[host]:[port]/system/console/configMgr`.
1. Click to edit **[!UICONTROL Adaptive Form Configuration Service]**.
1. choose **[!UICONTROL Visual Editor]** or **[!UICONTROL Code Editor]** from the **[!UICONTROL Default Mode for Rule Editor]** drop-down

1. Click **[!UICONTROL Save]**.
-->

### E. 완료 및 취소 단추 {#done-and-cancel-buttons}

**[!UICONTROL 완료]** 단추를 사용하여 규칙을 저장합니다. 불완전한 규칙을 저장할 수 있습니다. 그러나 미완료는 유효하지 않으며 실행되지 않습니다. 다음에 동일한 양식 객체에서 규칙 편집기를 실행하면 양식 객체에 저장된 규칙이 나열됩니다. 해당 보기에서 기존 규칙을 관리할 수 있습니다. 자세한 내용은 [규칙 관리](rule-editor.md#p-manage-rules-p)를 참조하십시오.

**[!UICONTROL 취소]** 단추를 사용하면 규칙에 대한 모든 변경 내용이 취소되고 규칙 편집기가 닫힙니다.

## 규칙 작성 {#write-rules}

시각적 규칙 편집기 <!-- or the code editor. When you launch the rule editor the first time, it opens in the visual editor mode. You can switch to the code editor mode and write rules. However, if you write or modify a rule in code editor, you cannot switch to the visual editor for that rule unless you clear the code editor. When you launch the rule editor next time, it opens in the mode that you used last to create rule. -->을(를) 사용하여 규칙을 작성할 수 있습니다.

먼저 시각적 편집기를 사용하여 규칙을 작성하는 방법을 살펴보겠습니다.

+++

+++ 비주얼 편집기 {#using-visual-editor} 사용

다음 예제 양식을 사용하여 시각적 편집기에서 규칙을 만드는 방법을 살펴보겠습니다.

![Create-rule-example](assets/create-rule-example.png)

예제 대출 신청서의 대출 요건 섹션에서는 신청자가 결혼 여부, 급여 및 기혼인 경우 배우자의 급여를 지정해야 합니다. 사용자 입력을 기반으로 규칙이 대출 자격 금액을 계산하고 대출 자격 필드에 표시합니다. 다음 규칙을 적용하여 시나리오를 구현합니다.

* [배우자 임금] 필드는 [결혼 상태]가 [기혼]인 경우에만 표시됩니다.
* 대출 가능 금액은 총 급여의 50%입니다.

규칙을 작성하려면 다음 단계를 수행하십시오.

1. 먼저 혼인 상태 라디오 단추에 대해 사용자가 선택한 옵션을 기준으로 배우자 임금 필드의 가시성을 제어하는 규칙을 작성합니다.

   작성 모드에서 대출 신청 양식을 엽니다. **[!UICONTROL 결혼 상태]** 구성 요소를 선택하고 ![편집 규칙](assets/edit-rules-icon.svg)을 선택합니다. 그런 다음 **[!UICONTROL 만들기]**&#x200B;를 선택하여 규칙 편집기를 시작합니다.

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1-cc.png)

   규칙 편집기를 실행하면 기본적으로 시기 규칙이 선택됩니다. 또한 규칙 편집기를 시작한 양식 개체(이 경우 결혼 상태)는 When 문에 지정됩니다.

   선택한 객체를 변경하거나 수정할 수 없지만 아래 표시된 대로 규칙 드롭다운을 사용하여 다른 규칙 유형을 선택할 수 있습니다. 다른 객체에 규칙을 작성하려면 취소를 선택하여 규칙 편집기를 종료하고 원하는 양식 객체에서 규칙을 다시 시작합니다.

1. **[!UICONTROL 상태 선택]** 드롭다운을 선택하고 **[!UICONTROL 이(가) 다음과 같음]**&#x200B;을(를) 선택합니다. **[!UICONTROL 문자열 입력]** 필드가 나타납니다.

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2-cc.png)

1. 규칙의 **[!UICONTROL 문자열 입력]** 필드에서 드롭다운 메뉴에서 **기혼**&#x200B;을(를) 선택합니다.

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4-cc.png)

   조건을 `When Marital Status is equal to Married`(으)로 정의했습니다. 그런 다음 이 조건이 True인 경우 수행할 작업을 정의합니다.

1. Then 문의 **[!UICONTROL 작업 선택]** 드롭다운에서 **[!UICONTROL 표시]**&#x200B;를 선택합니다.

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5-cc.png)

1. **[!UICONTROL 개체 놓기 또는 여기를 선택]** 필드의 양식 개체 탭에서 **[!UICONTROL 배우자 급여]** 필드를 드래그 앤 드롭하십시오. 또는 **[!UICONTROL 드롭 개체 또는 여기를 선택]** 필드를 선택하고 양식의 모든 양식 개체가 나열된 팝업 메뉴에서 **[!UICONTROL 배우자 급여]** 필드를 선택합니다.

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6-cc.png)

   그런 다음 이 조건이 False인 경우 수행할 작업을 정의합니다.
1. 혼인 상태를 싱글로 선택하는 경우 **[!UICONTROL 기타 섹션 추가]**&#x200B;를 클릭하여 **[!UICONTROL 배우자 급여]** 필드에 다른 조건을 추가합니다.

   ![when-else](assets/when-else.png)


1. Else 문의 **[!UICONTROL 작업 선택]** 드롭다운에서 **[!UICONTROL 숨기기]**를 선택합니다.
   ![when-else](assets/when-else-1.png)

1. **[!UICONTROL 개체 놓기 또는 여기를 선택]** 필드의 양식 개체 탭에서 **[!UICONTROL 배우자 급여]** 필드를 드래그 앤 드롭하십시오. 또는 **[!UICONTROL 드롭 개체 또는 여기를 선택]** 필드를 선택하고 양식의 모든 양식 개체가 나열된 팝업 메뉴에서 **[!UICONTROL 배우자 급여]** 필드를 선택합니다.
   ![when-else](assets/when-else-2.png)

   규칙은 규칙 편집기에 다음과 같이 표시됩니다.

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7-cc.png)

1. **[!UICONTROL 완료]**&#x200B;를 선택하여 규칙을 저장합니다.

<!--
1. Repeat steps 1 through 5 to define another rule to hide the Spouse Salary field if the marital Status is Single. The rule appears as follows in the rule editor.

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8-cc.png) -->

>[!NOTE]
>
> 또는 혼인 상태 필드의 [시기] 규칙 대신 [배우자 임금] 필드에 표시 규칙을 작성하여 동일한 동작을 구현할 수 있습니다.

![write-rules-visual-editor-9](assets/write-rules-visual-editor-9-cc.png)

1. 다음으로, 총 급여의 50%인 대출 자격 금액을 계산하는 규칙을 작성하여 대출 자격 필드에 표시합니다. 이 결과를 얻으려면 대출 자격 필드에 **[!UICONTROL 값 설정]** 규칙을 만드십시오.

   작성 모드에서 **[!UICONTROL 대출 자격]** 필드를 선택하고 ![편집 규칙](assets/edit-rules-icon.svg)을 선택합니다. 그런 다음 **[!UICONTROL 만들기]**&#x200B;를 선택하여 규칙 편집기를 시작합니다.

1. 규칙 드롭다운에서 **[!UICONTROL 값 설정]** 규칙을 선택합니다.

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10-cc.png)

1. **[!UICONTROL 옵션 선택]**&#x200B;을 선택하고 **[!UICONTROL 수학 식]**&#x200B;을 선택합니다. 수학 표현식을 작성할 필드가 열립니다.

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11-cc.png)

1. 표현식 필드에서:

   * Forms 개체 탭에서 첫 번째 **[!UICONTROL 놓기 개체에 있는**[!UICONTROL &#x200B;급여&#x200B;]**필드를 선택하거나 끌어서 놓거나 여기]** 필드를 선택합니다.

   * **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 더하기]**&#x200B;을(를) 선택합니다.

   * Forms 개체 탭에서 다른 **[!UICONTROL 개체 놓기 또는 여기를 선택]** 필드의 **[!UICONTROL 배우자 급여]** 필드를 선택하거나 끌어서 놓습니다.

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. 그런 다음 식 필드 주위의 강조 표시된 영역에서 을 선택하고 **[!UICONTROL 식 확장]**&#x200B;을 선택합니다.

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13-cc.png)

   확장 식 필드의 **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 나누기]**&#x200B;를 선택하고 **[!UICONTROL 옵션 선택]** 필드에서 **[!UICONTROL 숫자]**&#x200B;를 선택합니다. 그런 다음 숫자 필드에 **[!UICONTROL 2]**&#x200B;을(를) 지정합니다.

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14-cc.png)

   >[!NOTE]
   >
   >옵션 선택 필드에서 구성 요소, 함수, 수학 표현식 및 등록 정보 값을 사용하여 복잡한 표현식을 생성할 수 있습니다.

   그런 다음 조건을 만들어 True를 반환하면 표현식이 실행됩니다.

1. When 문을 추가하려면 **[!UICONTROL 조건 추가]**&#x200B;를 선택하십시오.

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15-cc.png)

   When 문에서:

   * Forms 개체 탭에서 첫 번째 **[!UICONTROL 개체를 놓거나 여기를 선택]** 필드의 **[!UICONTROL 결혼 상태]** 필드를 선택하거나 끌어서 놓습니다.

   * **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 이(가)]**&#x200B;과(와) 같습니다.

   * 다른 **[!UICONTROL 개체 삭제에서 String을 선택하거나 여기를 선택]** 필드를 선택하고 **[!UICONTROL 문자열 입력]** 필드에 **[!UICONTROL 결혼됨]**&#x200B;을(를) 지정합니다.

   규칙이 최종적으로 규칙 편집기에 다음과 같이 표시됩니다.  ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16-cc.png)

1. **[!UICONTROL 완료]**&#x200B;를 선택합니다. 규칙을 저장합니다.

1. 혼인 상태가 싱글인 경우 대출 자격을 계산하는 다른 규칙을 정의하려면 단계 7 - 14를 반복합니다. 규칙은 규칙 편집기에 다음과 같이 표시됩니다.

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17-cc.png)

또는, 값 설정 규칙을 사용하여 배우자 임금 필드를 표시-숨기기 위해 생성한 시기 규칙에서 대출 자격을 계산할 수 있습니다. 혼인 상태가 싱글인 경우 결합된 결과 규칙은 규칙 편집기에 다음과 같이 표시됩니다.

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18-cc.png)

혼합 규칙을 작성하여 배우자 임금 필드의 가시성을 통제하고 결혼 상태가 기혼인 경우 기타 조건을 사용하여 대출 자격을 계산할 수 있습니다.

![write-rules-visual-editor-19](assets/write-rules-visual-editor-19-cc.png)

+++


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

#### 규칙 편집기의 사용자 정의 함수 {#custom-functions}

**함수 출력**&#x200B;에 나열된 *합계*&#x200B;와 같은 기본 함수 외에 규칙 편집기에서 사용자 지정 함수를 사용할 수도 있습니다. 규칙 편집기는 스크립트 및 사용자 지정 함수에 대한 JavaScript ECMAScript 2019 구문을 지원합니다. 사용자 지정 함수 만들기에 대한 지침은 [적응형 Forms의 사용자 지정 함수](/help/forms/create-and-use-custom-functions.md) 문서를 참조하십시오.

<!--

Ensure that the function you write is accompanied by the `jsdoc` above it. Adaptive Form supports the various [JavaScript annotations for custom functions](/help/forms/create-and-use-custom-functions.md#js-annotations).

For more information, see [jsdoc.app](https://jsdoc.app/).

Accompanying `jsdoc` is required:

* If you want custom configuration and description
* Because there are multiple ways to declare a function in `JavaScript,` and comments let you keep a track of the functions.

Supported `jsdoc` tags:

* **Private**
  Syntax: `@private`
  A private function is not included as a custom function.

* **Name**
  Syntax: `@name funcName <Function Name>`
  Alternatively `,` you can use: `@function funcName <Function Name>` **or** `@func` `funcName <Function Name>`.
  `funcName` is the name of the function (no spaces allowed).
  `<Function Name>` is the display name of the function.

* **Parameter**
  Syntax: `@param {type} name <Parameter Description>`
  Alternatively, you can use: `@argument` `{type} name <Parameter Description>` **or** `@arg` `{type}` `name <Parameter Description>`.
  Shows parameters used by the function. A function can have multiple parameter tags, one tag for each parameter in the order of occurrence.
  `{type}` represents parameter type. Allowed parameter types are:

    1. string
    2. number
    3. boolean
    4. scope
    5. string[]
    6. number[]
    7. boolean[]
    8. date
    9. date[]
    10. array
    11. object

   `scope` refers to a special globals object which is provided by forms runtime. It must be the last parameter and is not be visible to the user in the rule editor. You can use scope to access readable form and field proxy object to read properties, event which triggered the rule and a set of functions to manipulate the form.

   `object` type is used to pass readable field object in parameter to a custom function instead of passing the value.

   All parameter types are categorized under one of the above. None is not supported. Ensure that you select one of the types above. Types are not case-sensitive. Spaces are not allowed in the parameter name.  Parameter description can have multiple words.

* **Optional Parameter**
Syntax: `@param {type=} name <Parameter Description>` 
Alternatively, you can use: `@param {type} [name] <Parameter Description>`
By default all parameters are mandatory. You can mark a parameter optional by adding `=` in type of the parameter or by putting param name in square brackets.
   
   For example, let us declare `Input1` as optional parameter:
    * `@param {type=} Input1`
    * `@param {type} [Input1]`

* **Return Type**
  Syntax: `@return {type}`
  Alternatively, you can use `@returns {type}`.
  Adds information about the function, such as its objective.
  {type} represents the return type of the function. Allowed return types are:

    1. string
    2. number
    3. boolean
    4. string[]
    5. number[]
    6. boolean[]
    7. date
    8. date[]
    9. array
    10. object

  All other return types are categorized under one of the above. None is not supported. Ensure that you select one of the types above. Return types are not case-sensitive.

**Adding a custom function**

For example, you want to add a custom function which calculates area of a square. Side length is the user input to the custom function, which is accepted using a numeric box in your form. The calculated output is displayed in another numeric box in your form. To add a custom function, you have to first create a client library, and then add it to the CRX repository.

To create a client library and add it in the CRX repository, perform the following steps:

1. Create a client library. For more information, see [Using Client-Side Libraries](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).
2. In CRXDE, add a property `categories`with string type value as `customfunction` to the `clientlib` folder.

   >[!NOTE]
   >
   >`customfunction`is an example category. You can choose any name for the category you create in the `clientlib`folder.

After you have added your client library in the CRX repository, use it in your Adaptive Form. It lets you use your custom function as a rule in your form. To add the client library in your Adaptive Form, perform the following steps:

1. Open your form in edit mode.
   To open a form in edit mode, select a form and select **[!UICONTROL Open]**.
1. In the edit mode, select a component, then select ![field-level](assets/select_parent_icon.svg) &gt; **[!UICONTROL Adaptive Form Container]**, and then select ![cmppr](assets/configure-icon.svg).
1. In the sidebar, under Name of Client Library, add your client library. ( `customfunction` in the example.)

   ![Adding the custom function client library](assets/clientlib.png)

1. Select the input numeric box, and select ![edit-rules](assets/edit-rules-icon.svg) to open the rule editor.
1. Select **[!UICONTROL Create Rule]**. Using options shown below, create a rule to save the squared value of the input in the Output field of your form.

   [![Using custom functions to create a rule](assets/add_custom_rule_new.png)](assets/add-custom-rule.png)
  
1. Select **[!UICONTROL Done]**. Your custom function is added.

   >[!NOTE]
   >
   > To invoke a form data model from rule editor using custom functions, [see here](/help/forms/using-form-data-model.md#invoke-services-in-adaptive-forms-using-rules-invoke-services). 

#### Function declaration supported types {#function-declaration-supported-types}

**Function Statement**

```javascript
function area(len) {
    return len*len;
}
```

This function is included without `jsdoc` comments.

**Function Expression**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Function Expression and Statement**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Function Declaration as Variable**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Limitation: custom function picks only the first function declaration from the variable list, if together. You can use function expression for every function declared.

**Function Declaration as Object**

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
>Ensure that you use `jsdoc` for every custom function. Although `jsdoc`comments are encouraged, include an empty `jsdoc`comment to mark your function as custom function. It enables default handling of your custom function.
-->

## 규칙 관리 {#manage-rules}

양식 개체에 대한 기존 규칙은 개체를 선택하고 ![edit-rules1](assets/edit-rules-icon.svg)을(를) 선택하면 나열됩니다. 제목을 보고 규칙 요약을 미리 볼 수 있습니다. 또한 UI를 사용하여 전체 규칙 요약을 확장 및 보고, 규칙 순서를 변경하고, 규칙을 편집하고, 규칙을 삭제할 수 있습니다.

![목록 규칙](assets/list-rules-cc.png)

규칙에 대해 다음 작업을 수행할 수 있습니다.

* **확장/축소**: 규칙 목록의 콘텐츠 열에 규칙 콘텐츠가 표시됩니다. 전체 규칙 콘텐츠가 기본 보기에 표시되지 않으면 ![expand-rule-content](assets/Smock_ChevronDown.svg)을(를) 선택하여 확장하십시오.

* **순서 바꾸기**: 만든 새 규칙이 규칙 목록의 맨 아래에 스택되어 있습니다. 규칙은 위에서 아래로 실행됩니다. 맨 위에 있는 규칙이 먼저 실행되고 같은 유형의 다른 규칙이 실행됩니다. 예를 들어, 맨 위에서 첫 번째, 두 번째, 세 번째 및 네 번째 위치에 각각 When, Show, Enable 및 When 규칙이 있는 경우 맨 위에 있는 When 규칙이 먼저 실행되고 네 번째 위치에 있는 When 규칙이 실행됩니다. 그런 다음 표시 및 활성화 규칙이 실행됩니다.
![정렬 규칙](assets/sort-rules.svg)을(를) 탭하여 규칙의 순서를 변경하거나 목록에서 원하는 순서로 드래그 앤 드롭할 수 있습니다.

* **편집**: 규칙을 편집하려면 규칙 제목 옆에 있는 확인란을 선택하십시오. 규칙을 편집하고 삭제하는 옵션이 나타납니다. **[!UICONTROL 편집]**&#x200B;을 선택하여 규칙 편집기에서 선택한 규칙을 엽니다.

* **삭제**: 규칙을 삭제하려면 규칙을 선택하고 **[!UICONTROL 삭제]**&#x200B;를 선택합니다.

* **활성화/비활성화**: 규칙 사용을 일시 중지해야 하는 경우 하나 이상의 규칙을 선택하고 [작업] 도구 모음에서 **[!UICONTROL 비활성화]**&#x200B;를 선택하여 비활성화할 수 있습니다. 규칙이 비활성화되어 있으면 런타임에 실행되지 않습니다. 비활성화된 규칙을 활성화하려면 해당 규칙을 선택하고 작업 도구 모음에서 활성화 를 선택할 수 있습니다. 규칙의 상태 열에는 규칙의 활성화 여부가 표시됩니다.

![규칙 사용 안 함](assets/disablerule-cc.png)

## 규칙 복사/붙여넣기 {#copy-paste-rules}

한 필드에서 유사한 다른 필드로 규칙을 복사하여 붙여넣으면 시간을 절약할 수 있습니다.

규칙을 복사하여 붙여넣으려면 다음을 수행합니다.

1. 규칙을 복사할 양식 개체를 선택하고 구성 요소 도구 모음에서 ![규칙 편집](assets/edit-rules-icon.svg)을 선택합니다. 양식 객체가 선택되고 기존 규칙이 나타나는 규칙 편집기 사용자 인터페이스가 나타납니다.

   ![규칙 복사](assets/copyrule.png)

   기존 규칙 관리에 대한 자세한 내용은 [규칙 관리](rule-editor.md#p-manage-rules-p)를 참조하십시오.

1. 규칙 제목 옆에 있는 확인란을 선택하면 규칙을 관리하는 옵션이 나타납니다. **[!UICONTROL 복사]**&#x200B;를 선택합니다.

   ![copyrule2](assets/copyrule2.png)

1. 규칙을 붙여넣을 다른 양식 개체를 선택하고 **[!UICONTROL 붙여넣기]**&#x200B;를 선택합니다. 또한 규칙을 편집하여 변경할 수 있습니다.

   >[!NOTE]
   >
   >해당 양식 객체가 복사된 규칙의 이벤트를 지원하는 경우에만 다른 양식 객체에 규칙을 붙여넣을 수 있습니다. 예를 들어 버튼은 클릭 이벤트를 지원합니다. 클릭 이벤트가 있는 규칙을 단추에는 붙여넣을 수 있지만 확인란에는 붙여넣을 수 없습니다.

1. **[!UICONTROL 완료]**&#x200B;를 선택하여 규칙을 저장합니다.

## 다음 단계

적응형 양식의 규칙 편집기에서 다양한 연산자 유형 및 이벤트를 이해하려면 적응형 양식의 규칙 편집기에서 [사용 가능한 연산자 유형 및 이벤트](/help/forms/rule-editor-core-components-events-operators.md) 문서를 참조하십시오.


## 추가 참조

{{see-also-rule-editor}}