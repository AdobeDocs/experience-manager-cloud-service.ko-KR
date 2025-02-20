---
title: 규칙 편집기를 사용해 양식 필드에 규칙을 적용하여 WYSIWYG 작성으로 만든 양식에 대해 동적 비헤이비어와 복잡한 논리를 구현하는 방법
description: 범용 편집기의 규칙 편집기를 사용하면 코딩이나 스크립팅 없이도 양식에 동적 비헤이비어를 추가하고 복잡한 논리를 작성할 수 있습니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: ba42a99e6138616ab6a7564c4bf58400844bdcc4
workflow-type: tm+mt
source-wordcount: '2166'
ht-degree: 76%

---


# WYSIWYG 작성에서 규칙 편집기 소개

규칙 편집기를 사용하여 규칙을 만들면 동적 양식 비헤이비어를 추가할 수 있습니다. 이러한 규칙을 사용하면 조건부 필드 가시성이 높아지고, 사용자 입력을 기반으로 계산이 자동화되며, 전반적인 사용자 경험이 향상됩니다. 규칙 편집기는 양식 작성 프로세스를 간소화하여 정확성과 효율성을 모두 보장하는 데 도움이 됩니다.

규칙 편집기는 규칙을 만들고 관리하기 위한 직관적인 시각적 인터페이스를 제공합니다. 사용자 친화적인 접근 방식을 통해 기술적인 전문 지식이 없는 사용자를 포함한 모든 사용자가 쉽게 액세스하여 양식 내에서 논리를 구현할 수 있습니다.

## 규칙 이해

규칙은 특정 조건에서 사용자가 어떤 작업을 수행해야 하는지 안내하는 지침입니다.

* **조건**: 조건은 무언가가 true인지 false인지 평가하는 검사 또는 규칙입니다. “이것이 요구 사항을 충족시키는가?”라는 질문에 답합니다.

* **액션**: 액션은 조건이 true일 때 발생하는 결과입니다. 이는 조건에 대한 평가에 따라 트리거되는 작업 또는 동작입니다.

규칙은 일반적으로 다음 구성 중 하나를 따릅니다.

* **Condition-Action**: 먼저 조건을 확인한 다음 액션을 수행합니다. 규칙 편집기에서 `When` 규칙 유형은 `condition-action` 구성을 적용합니다.
* **Action-Condition**: 먼저 액션을 수행한 다음 조건을 확인합니다. 규칙 편집기의 `Set Value Of` 및 `Validate` 규칙 유형은 `action-condition` 구성을 적용합니다.
* **Action-Condition-Alternate Action**: 액션을 수행하고 조건을 확인한 다음 조건에 따라 기본 액션 또는 대체 액션을 수행합니다. 예를 들어 기본적으로 `Show`에 대한 대체 액션은 `Hide`이고, `Enable`에 대한 대체 액션은 `Disable`입니다.

한 가지 예로 조건은 사용자가 필드에 특정 값을 입력했는지 확인할 수 있으며 이에 따른 액션은 필드를 표시하거나 숨기는 것일 수 있습니다.
* **조건**: 소득이 50,000달러보다 큰지 확인합니다.
* **액션**: 조건이 true인 경우 `Additional Deduction` 필드를 표시합니다. 그렇지 않은 경우 수행하는 대체 액션으로써 `Additional Deduction` 필드를 숨깁니다.

자세한 단계별 지침은 [조건부 규칙 추가](#2-add-a-conditional-rule)를 참조하십시오.

## 규칙 편집기 확장 기능을 활성화하는 방법

범용 편집기에서 규칙 편집기 확장은 기본적으로 활성화되어 있지 않습니다. 규칙 편집기 확장을 사용하려면 공식 전자 메일 ID에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)에 전자 메일을 보내십시오.

사용자 환경에서 규칙 편집기 확장 기능을 활성화하면 편집기의 오른쪽 상단에 ![edit-rules](/help/forms/assets/edit-rules-icon.svg) 아이콘이 나타납니다.

![범용 편집기 규칙 편집기](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)

규칙을 작성할 양식 구성 요소를 선택하고 ![편집-규칙](/help/forms/assets/edit-rules-icon.svg) 아이콘을 클릭합니다. 규칙 편집기 사용자 인터페이스가 나타납니다.

![규칙 편집기 사용자 인터페이스](/help/edge/docs/forms/assets/rule-editor-for-field.png)

이 문서에서 `form object`과(와) `form component`은(는) 서로 교환하여 사용됩니다.

이제 [규칙 편집기에서 사용 가능한 규칙 유형](#available-rule-types-in-rule-editor)을 사용하여 선택한 양식 필드에 대한 규칙이나 비즈니스 로직을 작성할 수 있습니다.

## 규칙 편집기 사용자 인터페이스 이해

규칙 편집기 편집기는 ![edit-rules](/help/forms/assets/edit-rules-icon.svg) 아이콘을 클릭하면 열립니다.

![규칙 편집기 사용자 인터페이스](/help/edge/docs/forms/assets/rule-editor-interface.png)

<table border="1">
  <thead>
    <tr>
      <th>규칙 편집기의 구성 요소</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. 제목</td>
      <td>양식 구성 요소의 제목과 선택한 규칙 유형을 표시합니다. 예를 들어 '총 급여 입력'은 '언제' 규칙 유형이 선택된 텍스트 상자 구성 요소입니다. </td>
    </tr>
    <tr>
      <td>2. 양식 오브젝트 및 함수</td>
      <td><b>Forms 개체</b> 탭에는 양식에 포함된 모든 구성 요소의 계층 보기가 표시됩니다. <b>함수</b> 탭에는 규칙 편집기에 기본 제공된 함수 집합이 포함되어 있습니다.</td>
    </tr>
    <tr>
      <td>3. 양식 오브젝트 및 함수 토글</td>
      <td>토글 단추는 양식 개체 및 함수 창을 교대로 표시하거나 숨깁니다. </td>
    </tr>
    <tr>
      <td>4. 시각적 규칙 편집기</td>
      <td>시각적 규칙 편집기 는 양식 구성 요소에 대한 규칙을 만들 수 있는 인터페이스입니다.</td>
    </tr>
    <tr>
      <td>5. 완료 및 취소 버튼</td>
      <td><b>완료</b> 버튼은 규칙을 저장하는 데 사용됩니다. <b>취소</b> 버튼을 클릭하면 규칙에 대한 모든 변경 사항이 삭제되고 규칙 편집기가 닫힙니다.</td>
    </tr>
  </tbody>
</table>

양식 구성 요소에 대한 기존 규칙은 구성 요소를 선택하면 나열됩니다. 규칙 편집기에서 제목을 보고 규칙 요약을 미리 볼 수 있습니다. 또한 규칙의 순서를 변경하고, 규칙을 편집하고, 규칙을 활성화/비활성화하고, 규칙을 삭제할 수도 있습니다.

![사용 가능한 양식 오브젝트 규칙 표시](/help/edge/docs/forms/assets/rule-editor15.png)

## 사용 가능한 규칙 유형

규칙 편집기는 아래 테이블에 표시된 것처럼 규칙을 작성하는 데 사용할 수 있는 사전 정의된 규칙 유형 세트를 제공합니다.

<table border="1">
  <thead>
    <tr>
      <th>규칙 유형</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>값 설정</td>
      <td>지정된 조건의 충족 여부에 따라 양식 구성 요소의 값을 설정합니다.</td>
    </tr>
    <tr>
      <td>값 지우기</td>
      <td>지정된 양식 구성 요소의 값을 지웁니다.</td>
    </tr>
    <tr>
      <td>숨기기/표시</td>
      <td>조건 충족 여부에 따라 양식 구성 요소를 숨기거나 표시합니다.</td>
    </tr>
    <tr>
      <td>활성화/비활성화</td>
      <td>조건의 충족 여부에 따라 양식 구성 요소를 활성화하거나 비활성화합니다.</td>
    </tr>
    <tr>
      <td>유효성 검사</td>
      <td>조건을 기반으로 양식 구성 요소를 확인하고 조건이 충족되지 않으면 오류를 표시합니다. </td>
    </tr>
    <tr>
      <td>When</td>
      <td>평가 조건을 지정하고 조건이 충족되면 트리거할 작업을 지정합니다. <i>condition-action-alternate</i> 작업 규칙 구문 또는 <i>condition-action</i> 규칙 구문을 따릅니다. </td>
    </tr>
    <tr>
      <td>포맷</td>
      <td> 양식 구성 요소의 값이 변경될 때 해당 표현식을 사용하여 양식 구성 요소의 표시 값을 수정합니다.</td>
    </tr>
    <tr>
      <td>서비스 호출</td>
      <td>외부 API, 양식 데이터 모델 또는 RESTful 웹 서비스를 사용하여 구성된 서비스를 호출합니다.</td>
    </tr>
    <tr>
      <td>속성 설정</td>
      <td>조건을 기반으로 지정된 양식 구성 요소의 속성 값을 설정합니다.</td>
    </tr>
    <tr>
      <td>포커스 설정</td>
      <td>지정된 양식 구성 요소에 포커스를 설정합니다.</td>
    </tr>
    <tr>
      <td>양식 저장</td>
      <td>초안 및 제출 Forms 포털 구성 요소를 사용하여 양식을 초안으로 저장할 수 있습니다. </td>
    </tr>
    <tr>
      <td>양식 제출</td>
      <td>양식을 제출합니다.</td>
    </tr>
    <tr>
      <td>양식 재설정</td>
      <td>양식을 재설정합니다.</td>
    </tr>
    <tr>
      <td>인스턴스 추가/제거</td>
      <td>지정된 반복 가능한 패널이나 테이블 행의 인스턴스를 추가하거나 제거합니다.</td>
    </tr>
    <tr>
      <td>다음으로 이동</td>
      <td>다른 적응형 양식, 다른 자산(예: 이미지 또는 문서 조각) 또는 외부 URL로 이동합니다.</td>
    </tr>
    <tr>
      <td>이벤트 발송</td>
      <td>사전 정의된 조건이나 이벤트에 따라 특정 액션을 트리거합니다.</td>
    </tr>
    <tr>
      <td>패널 중에서 탐색</td>
      <td>양식에서 여러 패널 간에 포커스를 이동할 수 있습니다.</td>
    </tr>
  </tbody>
</table>


이제 [규칙 편집기에서 규칙을 작성](#write-rules)하는 방법을 살펴보겠습니다.

## 규칙 작성

시각적 규칙 편집기에서 규칙을 작성하는 방법을 이해하기 위해 세금 계산 양식이라는 간단한 예제를 살펴보겠습니다.

![규칙 편집기 예제](/help/edge/docs/forms/assets/rule-editor-1.png)

위에 설명된 양식에서 사용자는 총 급여를 입력합니다. 이러한 입력을 기준으로 조건부 필드가 표시되고 미지급 세금이 계산됩니다.

**양식 필드:**
* 총 급여 (사용자 입력)
* 추가 공제 (조건부 필드)
* 과세 소득 (계산된 필드)
* 미지급 세금 (계산된 필드)

**조건부 규칙:**
* 조건: 총 급여 > 50,000
* 액션: 추가 공제 필드 표시

**계산 규칙:**

* 과세 소득 = 총 급여 - 추가 공제 (해당되는 경우)
* 미지급 세금 = 과세 소득 * 세율 (단순성을 위해 10% 고정 세율을 가정)

규칙을 작성하려면 다음 단계를 수행합니다.

### 1. 양식 작성

범용 편집기에서 양식을 작성하는 방법은 다음과 같습니다.

1. 편집을 위해 범용 편집기에서 양식을 엽니다.
1. 다음 양식 구성 요소를 추가합니다.
   * 세금 계산 양식 (제목)
   * 총 급여(숫자 입력)
   * 추가 공제(숫자 입력)
   * 과세 소득(숫자 입력)
   * 납부세액(숫자 입력)
   * 제출 (제출 버튼)
1. `Additional Deduction` 양식 필드의 `Properties`를 열어 해당 필드를 숨깁니다.

   ![규칙 편집기 예제](/help/edge/docs/forms/assets/rule-editor2.png)

### 2. 양식 필드에 대한 조건부 규칙 추가

양식을 작성했으면 총 급여가 50,000달러를 초과하는 경우에만 `Additional Deduction` 필드를 표시하도록 첫 번째 규칙을 작성합니다. 조건부 규칙을 추가하려면 다음 작업을 수행합니다.

1. 편집할 양식을 유니버설 편집기에서 열고 콘텐츠 트리에서 **[!UICONTROL 총 급여]** 필드를 선택한 다음 ![편집-규칙](/help/forms/assets/edit-rules-icon.svg)을 선택하십시오. 또는 **[!UICONTROL Forms 개체]** 창에서 직접 **[!UICONTROL 총 급여]** 필드를 선택할 수 있습니다.
   ![규칙 편집기 예제1](/help/edge/docs/forms/assets/rule-editor3.png)
시각적 규칙 편집기 인터페이스가 나타납니다.
1. 규칙을 만들려면 **[!UICONTROL 만들기]**를 클릭하십시오.
   ![규칙 편집기 예제2](/help/edge/docs/forms/assets/rule-editor4.png)
기본적으로 `Set Value Of` 규칙 유형이 선택되어 있습니다. 선택한 오브젝트를 변경하거나 수정할 수는 없지만 규칙 드롭다운을 사용하여 다른 규칙 유형을 선택할 수 있습니다.\
   ![규칙 편집기 예제3](/help/edge/docs/forms/assets/rule-editor5.png)
1. 규칙 유형 드롭다운 목록을 열고 **[!UICONTROL When]** 규칙 유형을 선택합니다.
   ![규칙 편집기 예제4](/help/edge/docs/forms/assets/rule-editor6.png)
1. **[!UICONTROL 상태 선택]** 드롭다운을 선택하고 **[!UICONTROL 다음보다 큼]**&#x200B;을 선택합니다. **[!UICONTROL 숫자 입력]** 필드가 나타납니다.
   ![규칙 편집기 예제5](/help/edge/docs/forms/assets/rule-editor7.png)
1. 규칙의 **[!UICONTROL 숫자 입력]** 필드에서 `50000`을 입력합니다.
   ![규칙 편집기 예제6](/help/edge/docs/forms/assets/rule-editor8.png)
조건을 `When Gross Salary is greater than 50000`으로 정의했습니다. 다음으로 이 조건이 `True`일 경우 수행할 액션을 정의합니다.
1. `Then` 문에서 **[!UICONTROL 액션 선택]** 드롭다운의 **[!UICONTROL 표시]**를 선택합니다.
   ![규칙 편집기 예제7](/help/edge/docs/forms/assets/rule-editor9.png)
1. **[!UICONTROL 오브젝트 드롭 또는 여기에서 선택]** 필드의 양식 오브젝트 탭에서 **[!UICONTROL 추가 공제]** 필드를 드래그 앤 드롭합니다. 또는 **[!UICONTROL 오브젝트를 놓거나 여기에서 선택]** 필드를 선택하고 팝업 메뉴에서 **[!UICONTROL 추가 공제]** 필드를 선택하면 양식의 모든 양식 오브젝트가 나열됩니다.
   ![규칙 편집기 예제8](/help/edge/docs/forms/assets/rule-editor10.png)
1. `50000` 미만의 급여를 입력하는 경우를 위해 **[!UICONTROL 다른 섹션 추가]**&#x200B;를 선택하여 **[!UICONTROL 총 급여]** 필드에 다른 조건을 추가합니다.
   ![규칙 편집기 예제9](/help/edge/docs/forms/assets/rule-editor11.png)
1. `Else` 문에서 **[!UICONTROL 액션 선택]** 드롭다운의 **[!UICONTROL 숨기기]**를 선택합니다.
   ![규칙 편집기 예제10](/help/edge/docs/forms/assets/rule-editor12.png)
1. **[!UICONTROL 오브젝트 드롭 또는 여기에서 선택]** 필드의 양식 오브젝트 탭에서 **[!UICONTROL 추가 공제]** 필드를 드래그 앤 드롭합니다. 또는 **[!UICONTROL 오브젝트를 놓거나 여기에서 선택]** 필드를 선택하고 팝업 메뉴에서 **[!UICONTROL 추가 공제]** 필드를 선택하면 양식의 모든 양식 오브젝트가 나열됩니다.
   ![규칙 편집기 예제11](/help/edge/docs/forms/assets/rule-editor13.png)
1. **[!UICONTROL 완료]**를 선택하여 규칙을 저장합니다.
규칙이 규칙 편집기에 다음과 같이 나타납니다.
   ![규칙 편집기 예제12](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> 또는 총 급여 필드에 When 규칙을 작성하는 대신 추가 공제 필드에 표시 규칙을 작성하여 동일한 동작을 구현할 수도 있습니다.

### 3. 양식 필드에 대한 계산 규칙 추가

다음으로 `Taxable Income`을 계산하는 규칙을 작성합니다. 이는 `Gross Salary`에서 `Additional Deduction`(해당되는 경우)을 뺀 값입니다. **[!UICONTROL 과세 소득]** 필드에 계산 규칙을 추가하려면 다음 단계를 수행합니다.

1. 작성 모드에서 **[!UICONTROL 과세 소득]** 필드를 선택하고 ![edit-rules](/help/forms/assets/edit-rules-icon.svg) 아이콘을 선택합니다. 또는 **[!UICONTROL Forms 개체]** 창에서 직접 **[!UICONTROL 과세 소득]** 필드를 선택할 수 있습니다.
1. 그런 다음 **[!UICONTROL 만들기]**를 선택하여 규칙을 만듭니다.
   ![규칙 편집기 예제13](/help/edge/docs/forms/assets/rule-editor16.png)
1. **[!UICONTROL 옵션 선택]**&#x200B;을 선택하고 **[!UICONTROL 수학 표현식]**을 선택합니다. 수학 표현식을 작성하는 필드가 열립니다.
   ![규칙 편집기 예제14](/help/edge/docs/forms/assets/rule-editor17.png)

1. 수학 표현 필드에서 다음 작업을 수행합니다.

   * 양식 오브젝트 탭의 첫 번째 **[!UICONTROL 오브젝트 드롭 또는 여기에서 선택]** 필드에서 **[!UICONTROL 총 급여]** 필드를 선택하거나 드래그 앤 드롭합니다.

   * **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 빼기]**&#x200B;를 선택합니다.

   * 양식 오브젝트 탭의 기타 **[!UICONTROL 오브젝트 드롭 또는 여기에서 선택]** 필드에서 **[!UICONTROL 추가 공제]** 필드를 선택하거나 드래그 앤 드롭합니다.
     ![규칙 편집기 예제15](/help/edge/docs/forms/assets/rule-editor18.png)

1. **[!UICONTROL 완료]**&#x200B;를 선택하여 규칙을 저장합니다.

   이제 과세 소득에 세율을 곱하여 결정되는 `Tax Payable ` 필드에 대한 규칙을 추가합니다. 단순성을 위해 고정 세율을 `10%`로 가정합니다.

1. 작성 모드에서 **[!UICONTROL 미지급 세금]** 필드를 선택하고 ![edit-rules](/help/forms/assets/edit-rules-icon.svg) 아이콘을 선택합니다. **[!UICONTROL 만들기]**를 선택하여 규칙을 만듭니다.
   ![규칙 편집기 예제16](/help/edge/docs/forms/assets/rule-editor19.png)
1. **[!UICONTROL 옵션 선택]**&#x200B;을 선택하고 **[!UICONTROL 수학 표현식]**을 선택합니다. 수학 표현식을 작성하는 필드가 열립니다.
   ![규칙 편집기 예제17](/help/edge/docs/forms/assets/rule-editor20.png)
1. 수학 표현 필드에서 다음 작업을 수행합니다.

   * 양식 오브젝트 탭의 첫 번째 **[!UICONTROL 오브젝트 드롭 또는 여기에서 선택]** 필드에서 **[!UICONTROL 과세 소득]** 필드를 선택하거나 드래그 앤 드롭합니다.

   * **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 곱하기]**&#x200B;를 선택합니다.

   * **[!UICONTROL 옵션 선택]** 필드에서 **숫자**&#x200B;를 선택하고 **[!UICONTROL 숫자 입력]** 필드에 값을 `10`으로 입력합니다.
     ![규칙 편집기 예제18](/help/edge/docs/forms/assets/rule-editor21.png)
1. 다음으로 표현식 필드 주변의 강조 표시된 영역을 선택하고 **[!UICONTROL 표현식 확장]**을 선택합니다.
   ![규칙 편집기 예제19](/help/edge/docs/forms/assets/rule-editor22.png)
1. 확장된 표현식 필드의 **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 나누기]**&#x200B;를 선택하고 **[!UICONTROL 옵션 선택]** 필드에서 **[!UICONTROL 숫자]**&#x200B;를 선택합니다. 그런 다음 숫자 필드에 `100`을 지정합니다.
   ![규칙 편집기 예제20](/help/edge/docs/forms/assets/rule-editor23.png)
1. **[!UICONTROL 완료]**&#x200B;를 선택하여 규칙을 저장합니다.

### 4. 양식 미리보기

이제 양식을 미리 보고 **총 급여**&#x200B;를 `60,000`으로 입력하면 **추가 공제** 필드가 나타나고 **과세 소득**&#x200B;과 **미지급 세금**&#x200B;이 이에 따라 계산됩니다.

![양식 미리보기](/help/edge/docs/forms/assets/rule-editor-form.png)

함수 출력에 나열된 합계, 평균과 같은 기본 제공 함수 외에도 [사용자 정의 함수를 작성](#create-a-custom-function)하여 복잡한 비즈니스 로직을 구현할 수 있습니다.

## 규칙 편집기의 사용자 정의 함수

Edge Delivery Services 양식은 사용자가 복잡한 비즈니스 규칙을 구현하기 위한 JavaScript 함수를 정의할 수 있는 사용자 정의 함수를 지원합니다. 사용자 정의 함수는 입력된 데이터의 조작과 처리를 용이하게 하여 지정된 요구 사항을 충족하게 함으로써 양식의 기능을 확장합니다.

### 사용자 정의 함수 만들기

사용자 정의 함수를 만들려면 `../[blocks]/form/functions.js` 파일을 편집합니다. 만들기 프로세스에는 일반적으로 다음 단계가 포함됩니다.

* **함수 선언**: 함수 이름과 함수의 매개변수(허용되는 입력)를 정의합니다.
* **논리 구현**: 함수에 의해 수행되는 특정 계산이나 조작을 개략적으로 설명하는 코드를 작성합니다.
* **함수 내보내기**: 해당 파일에서 함수를 내보내 규칙에서 액세스할 수 있도록 합니다.


이 예제에서는 두 개의 사용자 정의 함수인 `getFullName`과 `days`를 설명합니다.

```JavaScript
/**
 * Get Full Name
 * @name getFullName Concats first name and last name
 * @param {string} firstname in Stringformat
 * @param {string} lastname in Stringformat
 * @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

/**
 * Calculate the number of days between two dates.
 * @param {*} endDate
 * @param {*} startDate
 * @name days Calculates the numebr of days between two dates
 * @returns {number} returns the number of days between two dates
 */
function days(endDate, startDate) {
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // return zero if dates are valid
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// eslint-disable-next-line import/prefer-default-export
export { getFullName, days };
```
![사용자 정의 함수 추가](/help/edge/docs/forms/assets/create-custom-function.png)

### 규칙 편집기의 사용자 정의 함수 사용

규칙 편집기에서 사용자 정의 함수를 사용하는 방법은 다음과 같습니다.

1. **함수 추가**: 사용자 정의 함수를 `../[blocks]/form/functions.js` 파일에 포함시킵니다. 파일 내 `export` 구문에 추가해야 합니다.
1. **파일 배포**: 업데이트된 `functions.js` 파일을 GitHub 프로젝트에 배포하고 빌드되었는지 확인합니다.
1. **함수 사용**: 양식의 규칙 편집기에서 함수에 액세스하려면 **[!UICONTROL 액션 선택]** 필드에서 `Function Output` 옵션을 선택합니다.

   ![규칙 편집기의 사용자 정의 함수](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

1. **양식 미리 보기**: 새로 구현된 함수를 사용하여 양식을 미리 봅니다.

## 추가 정보

>[!NOTE]
>
> 범용 편집기에서 정적 및 동적 가져오기는 사용자 지정 함수 스크립트에서 지원되지 않습니다. `../[blocks]/form/functions.js` 파일에 전체 코드를 추가해야 합니다.

이 문서에서는 범용 편집기에서 사용할 수 있는 규칙 편집기에 대한 제한된 정보를 제공합니다. 규칙 편집기 및 사용자 지정 함수에 대한 자세한 내용은 다음 문서를 참조하십시오.

{{see-also-rule-editor}}

## 추가 참조

{{universal-editor-see-also}}
