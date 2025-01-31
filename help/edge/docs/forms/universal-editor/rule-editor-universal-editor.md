---
title: 규칙 편집기를 사용하여 양식 필드에 규칙을 적용하여 WYSIWYG 작성으로 만든 양식의 동적 동작과 복잡한 논리를 활성화하는 방법
description: 범용 편집기의 규칙 편집기를 사용하면 코딩 또는 스크립팅 없이 동적 동작을 추가하고 복잡한 논리를 양식에 빌드할 수 있습니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: c27b8e413c060de601a72a669d86c4add2a4167d
workflow-type: tm+mt
source-wordcount: '2111'
ht-degree: 5%

---


# 범용 편집기에서 규칙 편집기 소개

규칙을 만들 수 있는 규칙 편집기를 사용하여 동적 양식 동작을 추가할 수 있습니다. 이러한 규칙을 사용하면 조건부 필드 가시성을 활성화하고 사용자 입력을 기반으로 계산을 자동화하며 전체 사용자 경험을 향상시킬 수 있습니다. 양식 채우기 프로세스를 간소화함으로써 규칙 편집기는 정확성과 효율성을 모두 보장하는 데 도움이 됩니다.

규칙 편집기는 규칙을 만들고 관리하기 위한 직관적인 시각적 인터페이스를 제공합니다. 사용자 친화적인 접근 방식을 통해 광범위한 기술 전문 지식이 없는 사용자도 모든 사용자가 액세스할 수 있으므로 양식 내에서 논리를 손쉽게 구현할 수 있습니다.

## 규칙 이해

규칙은 특정 조건에서 수행할 작업을 사용자에게 안내하는 지침입니다.

* **조건**: 조건은 참 또는 거짓인지를 평가하는 검사 또는 규칙입니다. 이것은 &quot;이것이 요구 사항을 충족합니까?&quot;라는 질문에 대한 답을 제공합니다.

* **작업**: 조건이 true일 때 수행되는 작업입니다. 조건 평가를 기반으로 트리거된 작업 또는 동작입니다.

규칙은 일반적으로 다음 구문 중 하나를 따릅니다.

* **Condition-Action**: 먼저 조건을 확인한 다음 작업을 수행합니다. 규칙 편집기에서 `When` 규칙 형식은 `condition-action` 구문을 적용합니다.
* **Action-Condition**: 먼저 작업을 수행한 다음 조건을 확인합니다. 규칙 편집기의 `Set Value Of` 및 `Validate` 규칙 유형은 `action-condition` 구문을 적용합니다.
* **Action-Condition-Alternate Action**: 작업을 수행하고 조건을 확인한 다음 기본 작업이나 조건에 따라 대체 작업을 수행합니다. 예를 들어 기본적으로 `Show`에 대한 대체 작업은 `Hide`이고 `Enable`에 대한 대체 작업은 `Disable`입니다.

예를 들어, 조건이 사용자가 필드에 특정 값을 입력했는지 확인할 수 있으며, 작업이 필드를 표시하거나 숨길 수 있습니다.
* **조건**: 소득이 $50,000보다 큰지 확인하십시오.
* **작업**: 조건이 true이면 `Additional Deduction` 필드를 표시하고 그렇지 않으면 `Additional Deduction` 필드를 숨기는 대체 작업을 수행합니다.

자세한 단계별 지침은 [조건부 규칙 추가](#2-add-a-conditional-rule)를 참조하십시오.

## 규칙 편집기 확장을 활성화하는 방법

범용 편집기에서 규칙 편집기는 기본적으로 활성화되어 있지 않습니다. 환경에 규칙 편집기 확장을 사용하려면 요청을 포함하여 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)(으)로 전자 메일을 보내십시오.

사용자 환경에 대해 규칙 편집기 확장을 활성화하면 편집기의 오른쪽 상단 모서리에 ![edit-rules](/help/forms/assets/edit-rules-icon.svg) 아이콘이 나타납니다.

![유니버설 편집기 규칙 편집기](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)

규칙을 작성할 양식 개체를 선택하고 ![edit-rules](/help/forms/assets/edit-rules-icon.svg) 아이콘을 클릭합니다. 규칙 편집기 사용자 인터페이스가 나타납니다.

![규칙 편집기 사용자 인터페이스](/help/edge/docs/forms/assets/rule-editor-for-field.png)

이제 규칙 편집기에서 [사용 가능한 규칙 유형](#available-rule-types-in-rule-editor)을 사용하여 선택한 양식 필드에 대한 규칙 또는 비즈니스 논리를 쓸 수 있습니다.

## 규칙 편집기 사용자 인터페이스 이해

규칙 편집기의 시각적 편집기는 ![edit-rules](/help/forms/assets/edit-rules-icon.svg) 아이콘을 클릭하면 열립니다.

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
      <td>1. 구성 요소 규칙 표시</td>
      <td>규칙 편집기를 실행한 양식 객체의 제목과 현재 선택한 규칙 유형을 표시합니다.</td>
    </tr>
    <tr>
      <td>2. 양식 개체 및 함수</td>
      <td><b>Forms 개체</b> 탭에는 양식에 포함된 모든 개체의 계층 보기가 표시됩니다. <b>함수</b> 탭에는 기본 제공 함수 집합이 포함되어 있습니다.</td>
    </tr>
    <tr>
      <td>3. 양식 개체 및 함수 전환</td>
      <td>전환 단추를 누르면 양식 개체 및 함수 창이 전환됩니다.</td>
    </tr>
    <tr>
      <td>4. 시각적 규칙 편집기</td>
      <td>시각적 규칙 편집기 는 규칙 편집기 사용자 인터페이스의 시각적 편집기 모드에서 규칙을 작성하는 영역입니다.</td>
    </tr>
    <tr>
      <td>5. 완료 및 취소 단추</td>
      <td><b>완료</b> 단추를 사용하여 규칙을 저장합니다. <b>취소</b> 단추를 사용하면 규칙에 대한 모든 변경 내용이 취소되고 규칙 편집기가 닫힙니다.</td>
    </tr>
  </tbody>
</table>

양식 객체에 대한 기존 규칙은 객체를 선택할 때 나열됩니다. 시각적 규칙 편집기에서 제목 및 규칙 요약을 미리 볼 수 있습니다. 또한 규칙 순서를 변경하거나, 규칙을 편집하거나, 규칙을 활성화/비활성화하거나, 규칙을 삭제할 수 있습니다.

![양식 개체의 사용 가능한 규칙을 표시합니다](/help/edge/docs/forms/assets/rule-editor15.png)

## 사용 가능한 규칙 유형

규칙 편집기는 아래 표에 표시된 대로 규칙을 작성하는 데 사용할 수 있는 사전 정의된 규칙 유형 집합을 제공합니다.

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
      <td>지정된 조건을 충족하는지 여부에 따라 양식 개체의 값을 설정합니다.</td>
    </tr>
    <tr>
      <td>값 지우기</td>
      <td>지정된 객체의 값을 지웁니다.</td>
    </tr>
    <tr>
      <td>숨기기/표시</td>
      <td>조건 충족 여부에 따라 양식 개체를 숨기거나 표시합니다.</td>
    </tr>
    <tr>
      <td>활성화/비활성화</td>
      <td>조건의 충족 여부에 따라 양식 개체를 활성화하거나 비활성화합니다.</td>
    </tr>
    <tr>
      <td>유효성 검사</td>
      <td>양식 또는 지정된 개체의 유효성을 검사합니다.</td>
    </tr>
    <tr>
      <td>http 화이트보드</td>
      <td><i>condition-action-alternate</i> 작업 규칙 구문 또는 <i>condition-action</i> 규칙 구문을 따릅니다. 평가 조건을 지정하고 조건이 충족되면 트리거할 작업을 지정합니다.</td>
    </tr>
    <tr>
      <td>형식</td>
      <td>함수 또는 정규 표현식을 기반으로 양식 개체의 형식을 지정합니다.</td>
    </tr>
    <tr>
      <td>서비스 호출</td>
      <td>양식 데이터 모델(FDM)로 구성된 서비스를 호출합니다.</td>
    </tr>
    <tr>
      <td>속성 설정</td>
      <td>조건을 기반으로 지정된 개체의 속성 값을 설정합니다.</td>
    </tr>
    <tr>
      <td>포커스 설정</td>
      <td>지정한 개체에 포커스를 설정합니다.</td>
    </tr>
    <tr>
      <td>양식 저장</td>
      <td>양식을 저장합니다.</td>
    </tr>
    <tr>
      <td>양식 제출/재설정</td>
      <td>양식을 제출하거나 재설정합니다.</td>
    </tr>
    <tr>
      <td>인스턴스 추가/제거</td>
      <td>지정된 반복 가능한 패널 또는 테이블 행의 인스턴스를 추가하거나 제거합니다.</td>
    </tr>
    <tr>
      <td>다음으로 이동</td>
      <td>다른 적응형 Forms, 이미지 또는 문서 조각과 같은 기타 에셋 또는 외부 URL로 이동합니다.</td>
    </tr>
    <tr>
      <td>이벤트 발송</td>
      <td>사전 정의된 조건 또는 이벤트를 기반으로 특정 작업을 트리거합니다.</td>
    </tr>
    <tr>
      <td>패널 간 탐색</td>
      <td>양식의 서로 다른 패널 간에 포커스를 이동할 수 있습니다.</td>
    </tr>
  </tbody>
</table>


이제 [규칙 편집기에서 규칙을 작성](#write-rules)하는 방법에 대해 알아보겠습니다.

## 규칙 작성

시각적 규칙 편집기에서 규칙을 작성하는 방법을 이해하기 위해 세금 계산 양식의 간단한 예를 살펴보겠습니다.

![규칙 편집기 예](/help/edge/docs/forms/assets/rule-editor-1.png)

사용자가 전술한 형태로 총 급여를 기재하게 된다. 이 입력을 기반으로 조건부 필드가 표시되고 납부할 세금이 계산됩니다.

**양식 필드:**
* 총 급여(사용자 입력)
* 추가 공제(조건부 필드)
* 과세 소득(계산된 필드)
* 납부할 세금(계산된 필드)

**조건부 규칙:**
* 조건: 총 임금 > 50,000
* 조치: 추가 공제 필드 표시

**계산 규칙:**

* 과세 소득 = 총 급여 - 추가 공제(해당하는 경우)
* 지급 세금 = 과세 소득 * 세율(단순화를 위해 고정 세율을 10%로 가정)

규칙을 작성하려면 다음 단계를 수행하십시오.

### 1. 양식 작성

범용 편집기에서 양식을 작성하려면 다음 작업을 수행하십시오.

1. 편집할 양식을 유니버설 편집기에서 엽니다.
1. 다음 양식 구성 요소를 추가합니다.
   * 세금 계산 양식(제목)
   * 총 급여(텍스트 입력)
   * 추가 공제(텍스트 입력)
   * 과세 소득(텍스트 입력)
   * 납부세액(텍스트 입력)
   * 제출(제출 단추)
1. `Properties`을(를) 열어 `Additional Deduction` 양식 필드를 숨깁니다.

   ![규칙 편집기 예](/help/edge/docs/forms/assets/rule-editor2.png)

### 2. 양식 필드에 대한 조건부 규칙 추가

양식을 작성한 후 총 급여가 50,000달러를 초과하는 경우에만 `Additional Deduction` 필드를 표시하도록 첫 번째 규칙을 작성하십시오. 조건부 규칙을 추가하려면 다음 작업을 수행하십시오.

1. 편집할 양식을 유니버설 편집기에서 엽니다.
1. 콘텐츠 트리에서 **[!UICONTROL 총 급여]** 구성 요소를 선택하고 ![편집-규칙](/help/forms/assets/edit-rules-icon.svg)을(를) 선택하십시오.
   ![규칙 편집기 예1](/help/edge/docs/forms/assets/rule-editor3.png)
시각적 규칙 편집기 인터페이스가 나타납니다.
1. **[!UICONTROL 만들기]**를 클릭하여 규칙 편집기를 시작합니다.
   ![규칙 편집기 예2](/help/edge/docs/forms/assets/rule-editor4.png)
기본적으로 `Set Value Of` 규칙 유형이 선택됩니다. 선택한 객체를 변경하거나 수정할 수 없지만 규칙 드롭다운을 사용하여 다른 규칙 유형을 선택할 수 있습니다.\
   ![규칙 편집기 예3](/help/edge/docs/forms/assets/rule-editor5.png)
1. 규칙 유형 드롭다운 목록을 열고 **[!UICONTROL When]** 규칙 유형을 선택합니다.
   ![규칙 편집기 예4](/help/edge/docs/forms/assets/rule-editor6.png)
1. **[!UICONTROL 상태 선택]** 드롭다운을 선택하고 **[!UICONTROL 이(가)]**&#x200B;보다 큼을(를) 선택합니다. **[!UICONTROL 숫자 입력]** 필드가 나타납니다.
   ![규칙 편집기 예5](/help/edge/docs/forms/assets/rule-editor7.png)
1. 규칙의 **[!UICONTROL 숫자 입력]** 필드에 `50000`을(를) 입력합니다.
   ![규칙 편집기 예6](/help/edge/docs/forms/assets/rule-editor8.png)
조건을 `When Gross Salary is greater than 50000`(으)로 정의했습니다. 그런 다음 이 조건이 `True`인 경우 수행할 작업을 정의합니다.
1. `Then` 문의 **[!UICONTROL 작업 선택]** 드롭다운에서 **[!UICONTROL 표시]**를 선택합니다.
   ![규칙 편집기 예7](/help/edge/docs/forms/assets/rule-editor9.png)
1. **[!UICONTROL 개체 놓기 또는 여기를 선택]** 필드의 양식 개체 탭에서 **[!UICONTROL 추가 공제]** 필드를 끌어서 놓습니다. 또는 **[!UICONTROL 개체 놓기 또는 여기를 선택]** 필드를 선택하고 양식의 모든 양식 개체를 나열하는 팝업 메뉴에서 **[!UICONTROL 추가 공제]** 필드를 선택합니다.
   ![규칙 편집기 예8](/help/edge/docs/forms/assets/rule-editor10.png)
1. `50000`보다 적은 급여를 입력하는 경우 **[!UICONTROL 기타 섹션 추가]**&#x200B;를 클릭하여 **[!UICONTROL 총 급여]** 필드에 다른 조건을 추가합니다.
   ![규칙 편집기 예9](/help/edge/docs/forms/assets/rule-editor11.png)
1. `Else` 문의 **[!UICONTROL 작업 선택]** 드롭다운에서 **[!UICONTROL 숨기기]**를 선택합니다.
   ![규칙 편집기 예10](/help/edge/docs/forms/assets/rule-editor12.png)
1. **[!UICONTROL 개체 놓기 또는 여기를 선택]** 필드의 양식 개체 탭에서 **[!UICONTROL 추가 공제]** 필드를 끌어서 놓습니다. 또는 **[!UICONTROL 개체 놓기 또는 여기를 선택]** 필드를 선택하고 양식의 모든 양식 개체를 나열하는 팝업 메뉴에서 **[!UICONTROL 추가 공제]** 필드를 선택합니다.
   ![규칙 편집기 예11](/help/edge/docs/forms/assets/rule-editor13.png)
1. **[!UICONTROL 완료]**를 선택하여 규칙을 저장합니다.
규칙은 규칙 편집기에 다음과 같이 표시됩니다.
   ![규칙 편집기 예12](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> 또는 총 임금 필드의 When 규칙 대신 추가 공제 필드에 표시 규칙을 작성하여 동일한 동작을 구현할 수 있습니다.

### 3. 양식 필드에 계산 규칙 추가

그런 다음 `Gross Salary`과(와) `Additional Deduction`의 차이인 `Taxable Income`을(를) 계산하는 규칙을 작성합니다(해당하는 경우). **[!UICONTROL 과세 소득]** 필드에 계산 규칙을 추가하려면 다음 단계를 수행하십시오.

1. 작성 모드에서 **[!UICONTROL 과세 소득]** 필드를 선택하고 ![편집-규칙](/help/forms/assets/edit-rules-icon.svg) 아이콘을 선택합니다. 그런 다음 **[!UICONTROL 만들기]**를 선택하여 규칙 편집기를 시작합니다.
   ![규칙 편집기 예13](/help/edge/docs/forms/assets/rule-editor16.png)
1. **[!UICONTROL 옵션 선택]**&#x200B;을 선택하고 **[!UICONTROL 수학 식]**을 선택합니다. 수학 표현식을 작성할 필드가 열립니다.
   ![규칙 편집기 예14](/help/edge/docs/forms/assets/rule-editor17.png)

1. 수학 표현식 필드에서 다음을 수행합니다.

   * Forms 개체 탭에서 첫 번째 **[!UICONTROL 개체 놓기 또는 여기]** 필드를 선택하여 **[!UICONTROL 총 급여]** 필드를 선택하거나 끌어서 놓습니다.

   * **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 빼기]**&#x200B;을(를) 선택합니다.

   * Forms 개체 탭에서 다른 **[!UICONTROL 개체 놓기 또는 여기를 선택]** 필드의 **[!UICONTROL 추가 공제]** 필드를 선택하거나 끌어서 놓습니다.
     ![규칙 편집기 예15](/help/edge/docs/forms/assets/rule-editor18.png)

1. **[!UICONTROL 완료]**&#x200B;를 선택하여 규칙을 저장합니다.

   이제 `Tax Payable ` 필드에 대한 규칙을 추가하고, 이 규칙은 과세 소득에 세율을 곱하여 결정됩니다. 간결성을 위해 고정 세율 `10%`을(를) 가정해 보십시오.

1. 작성 모드에서 **[!UICONTROL TAX PAYABLE]** 필드를 선택하고 ![편집 규칙](/help/forms/assets/edit-rules-icon.svg) 아이콘을 선택합니다. 그런 다음 **[!UICONTROL 만들기]**를 선택하여 규칙 편집기를 시작합니다.
   ![규칙 편집기 예16](/help/edge/docs/forms/assets/rule-editor19.png)
1. **[!UICONTROL 옵션 선택]**&#x200B;을 선택하고 **[!UICONTROL 수학 식]**을 선택합니다. 수학 표현식을 작성할 필드가 열립니다.
   ![규칙 편집기 예17](/help/edge/docs/forms/assets/rule-editor20.png)
1. 수학 표현식 필드에서 다음을 수행합니다.

   * Forms 개체 탭에서 첫 번째 **[!UICONTROL 놓기 개체에 있는**[!UICONTROL &#x200B;과세 소득&#x200B;]**필드를 선택하거나 끌어서 놓거나 여기]** 필드를 선택합니다.

   * **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 곱하기]**&#x200B;를 선택합니다.

   * **[!UICONTROL 옵션 선택]** 필드에서 **숫자**&#x200B;을(를) 선택하고 **[!UICONTROL 숫자 입력]** 필드에 값을 `10`로 입력하십시오.
     ![규칙 편집기 예18](/help/edge/docs/forms/assets/rule-editor21.png)
1. 그런 다음 식 필드 주위의 강조 표시된 영역에서 을 선택하고 **[!UICONTROL 식 확장]**을 선택합니다.
   ![규칙 편집기 예19](/help/edge/docs/forms/assets/rule-editor22.png)
1. 확장 식 필드의 **[!UICONTROL 연산자 선택]** 필드에서 **[!UICONTROL 나누기]**&#x200B;를 선택하고 **[!UICONTROL 옵션 선택]** 필드에서 **[!UICONTROL 숫자]**&#x200B;를 선택합니다. 그런 다음 숫자 필드에 `100`을(를) 지정합니다.
   ![규칙 편집기 예20](/help/edge/docs/forms/assets/rule-editor23.png)
1. **[!UICONTROL 완료]**&#x200B;를 선택하여 규칙을 저장합니다.

### 4. 양식 미리 보기

이제 양식을 미리 보고 **총 급여**&#x200B;을(를) `60,000`(으)로 입력하면 **추가 공제** 필드가 나타나고 **과세 소득** 및 **납부세액**&#x200B;이(가) 그에 따라 계산됩니다.

![양식 미리 보기](/help/edge/docs/forms/assets/rule-editor-form.png)

함수 출력 아래에 나열된 Sum, Average와 같은 기본 함수 외에도 [사용자 지정 함수를 작성](#create-a-custom-function)하여 복잡한 비즈니스 논리를 구현할 수 있습니다.

## 규칙 편집기의 사용자 지정 함수

Edge Delivery Services Forms은 사용자가 복잡한 비즈니스 규칙을 구현하기 위해 JavaScript 함수를 정의할 수 있는 사용자 지정 함수를 지원합니다. 사용자 지정 함수는 지정된 요구 사항을 충족하도록 입력된 데이터의 조작 및 처리를 용이하게 하여 양식의 기능을 확장합니다.

### 사용자 정의 함수 만들기

사용자 지정 함수를 만들려면 `../[blocks]/form/functions.js` 파일을 편집하세요. 만들기 프로세스에는 일반적으로 다음 단계가 포함됩니다.

* **함수 선언**: 함수 이름 및 해당 매개 변수(함수 이름이 허용하는 입력)를 정의합니다.
* **논리 구현**: 함수에서 수행하는 특정 계산 또는 조작에 대해 대략적으로 설명하는 코드를 작성합니다.
* **함수 내보내기**: 관련 파일에서 함수를 내보내어 규칙 내에서 액세스할 수 있도록 합니다.


이 예에서는 `getFullName` 및 `days`(으)로 두 가지 사용자 지정 함수를 보여 줍니다.

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
![사용자 지정 함수 추가](/help/edge/docs/forms/assets/create-custom-function.png)

### 규칙 편집기에서 사용자 지정 함수 사용

규칙 편집기에서 사용자 지정 함수를 사용하려면 다음을 수행하십시오.

1. **함수 추가**: `../[blocks]/form/functions.js` 파일에 사용자 지정 함수를 포함합니다. 파일 내의 `export` 문에 추가해야 합니다.
1. **파일 배포**: 업데이트된 `functions.js` 파일을 GitHub 프로젝트에 배포하고 빌드되었는지 확인합니다.
1. **함수 사용**: **[!UICONTROL 작업 선택]** 필드에서 `Function Output` 옵션을 선택하여 양식의 규칙 편집기 내에서 함수에 액세스합니다.

   ![규칙 편집기의 사용자 지정 함수](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

1. **양식 미리 보기**: 새로 구현된 함수를 사용하여 양식을 미리 봅니다.

## 관련 문서

{{see-also-rule-editor}}

## 추가 참조

* [AEM Forms용 Edge Delivery Services 시작하기](/help/edge/docs/forms/tutorial.md)
* [Google Sheets 또는 Microsoft Excel을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)
* [Google Sheets 또는 Microsoft Excel 파일을 설정하여 데이터 수신 시작&#x200B;](/help/edge/docs/forms/submit-forms.md)
* [양식 게시 및 데이터 수집 시작](/help/edge/docs/forms/publish-forms.md)
* [양식 모양 사용자 정의&#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [양식에 반복 가능한 섹션 추가&#x200B;](/help/edge/docs/forms/repeatable-forms.md)
* [양식 제출 후 사용자 정의 감사 메시지 표시&#x200B;](/help/edge/docs/forms/thank-you-page-form.md)
* [적응형 양식 블록 구성 요소 및 해당 속성](/help/edge/docs/forms/form-components.md)
* [실제 사용 모니터링](https://www.aem.live/developer/rum#authentication)
