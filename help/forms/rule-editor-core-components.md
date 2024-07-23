---
title: 규칙 편집기를 사용하여 양식 필드에 규칙을 추가하여 동적 동작을 추가하고 핵심 구성 요소를 기반으로 적응형 양식에 복잡한 논리를 작성하는 방법
description: 적응형 Forms 규칙 편집기를 사용하면 코딩 또는 스크립팅 없이 다이내믹 동작을 추가하고 복잡한 논리를 양식에 빌드할 수 있습니다.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 1292f729-c6eb-4e1b-b84c-c66c89dc53ae
source-git-commit: 780c68f0c21ef94ff6a73ce991370100b1a88db9
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 4%

---


# 핵심 구성 요소를 기반으로 하는 적응형 양식용 규칙 편집기 소개

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM as a Cloud Service (핵심 구성 요소) | 이 문서 |
| AEM as a Cloud Service(Foundation 구성 요소) | [여기 클릭](/help/forms/rule-editor.md) |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html) |

핵심 구성 요소를 기반으로 하는 적응형 양식에서 규칙 편집기 기능은 비즈니스 사용자와 개발자가 적응형 양식 개체에 대한 규칙을 작성할 수 있도록 해줍니다. 이러한 규칙은 양식에 대한 사전 설정 조건, 사용자 입력 및 사용자 작업을 기반으로 양식 개체에서 트리거하는 작업을 정의합니다. 이 기능을 사용하면 양식 작성 환경을 더욱 간소화하여 정확성과 속도를 모두 보장할 수 있습니다.

규칙 편집기는 규칙을 작성할 수 있는 직관적이고 단순한 사용자 인터페이스를 제공합니다. 모든 사용자에게 맞는 시각적 편집기를 제공하므로 광범위한 기술 지식 없이도 규칙을 만들고 관리할 수 있습니다. 이 시각적 접근 방식을 사용하면 사용자가 양식 내에서 원하는 논리를 더 쉽게 이해하고 구현할 수 있습니다.

규칙을 사용하여 적응형 양식 개체에 대해 수행할 수 있는 몇 가지 주요 작업은 다음과 같습니다.

* 개체 표시 또는 숨기기
* 오브젝트 활성화 또는 비활성화
* 오브젝트의 값 설정
* 오브젝트 값의 유효성 검사
* 오브젝트의 값을 계산하는 함수 실행
* 양식 데이터 모델(FDM) 서비스 호출 및 작업 수행
* 오브젝트의 속성 설정

<!-- Rule editor replaces the scripting capabilities in [!DNL Experience Manager 6.1 Forms] and earlier releases. However, your existing scripts are preserved in the new rule editor. For more information about working with existing scripts in the rule editor, see [Impact of rule editor on existing scripts](rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p). -->

`forms-power-users` 그룹에 추가된 사용자는 스크립트를 만들고 기존 스크립트를 편집할 수 있습니다. [!DNL forms-users] 그룹의 사용자는 스크립트를 사용할 수 있지만 스크립트를 만들거나 편집할 수는 없습니다.

자세한 비교는 [기초 규칙 편집기와 핵심 구성 요소 규칙 편집기의 차이점](/help/forms/rule-editor-core-components-difference-tables.md) 문서를 참조하십시오.

<!--
## Difference between Rule editor in Core Components and Rule Editor in Foundation Components

{{rule-editor-diff}}

>[!NOTE]
>
> To see how to create and use custom functions in detail, refer to [Custom functions in Adaptive Forms (Core Components)](/help/forms/create-and-use-custom-functions.md) article.

-->

## 규칙 이해 {#understanding-a-rule}

규칙은 작업과 조건의 조합입니다. 규칙 편집기에서 작업에는 폼의 개체 값 숨기기, 표시, 활성화, 비활성화 또는 계산과 같은 활동이 포함됩니다. 조건은 양식 객체의 상태, 값 또는 속성에 대한 검사 및 작업을 수행하여 평가되는 부울 표현식입니다. 조건을 평가하여 반환된 값(`True` 또는 `False`)을 기반으로 작업이 수행됩니다.

규칙 편집기는 규칙을 작성하는 데 도움이 되는 시기, 표시, 숨기기, 활성화, 비활성화, 값 설정 및 유효성 검사와 같은 사전 정의된 규칙 유형 집합을 제공합니다. 각 규칙 유형을 사용하면 규칙에서 조건 및 작업을 정의할 수 있습니다. 이 문서에서는 각 규칙 유형에 대해 자세히 설명합니다.

규칙은 일반적으로 다음 구문 중 하나를 따릅니다.

**Condition-Action** 이 구문에서는 규칙이 먼저 조건을 정의한 다음 트리거할 작업을 정의합니다. 이 구문은 프로그래밍 언어의 if-then 문과 비슷합니다.

규칙 편집기에서 **When** 규칙 유형은 조건-작업 구문을 적용합니다.

**Action-Condition** 이 구문에서는 규칙이 먼저 트리거할 작업을 정의한 다음 평가 조건을 정의합니다. 이 구문의 또 다른 변형은 action-condition-alternate 매크로 함수이며, 이 매크로 함수는 조건이 False를 반환하는 경우 트리거할 대체 매크로 함수도 정의합니다.

규칙 편집기의 Show, Hide, Enable, Disable, Set Value Of 및 Validate 규칙 유형은 작업 조건 규칙 구성을 적용합니다. 기본적으로 표시에 대한 대체 작업은 숨기기이고 활성화에 대한 대체 작업은 비활성화이며 그 반대입니다. 기본 대체 작업은 변경할 수 없습니다.

>[!NOTE]
>
>규칙 편집기에서 정의하는 조건 및 작업을 포함한 사용 가능한 규칙 유형은 규칙을 만드는 양식 객체의 유형에 따라 다릅니다. 규칙 편집기에는 특정 양식 객체 유형에 대한 조건 및 작업 문을 작성하기 위한 유효한 규칙 유형 및 옵션만 표시됩니다. 예를 들어 패널 객체에 대한 유형의 유효성 검사 및 값 설정 은 표시되지 않습니다.

규칙 편집기에서 사용할 수 있는 규칙 유형에 대한 자세한 내용은 [규칙 편집기에서 사용 가능한 규칙 유형](rule-editor.md#p-available-rule-types-in-rule-editor-p)을 참조하십시오.

### 규칙 구성 선택 지침 {#guidelines-for-choosing-a-rule-construct}

모든 규칙 구문을 사용하여 대부분의 사용 사례를 달성할 수 있지만, 다음은 한 구문을 다른 구문보다 선택하는 몇 가지 지침입니다. 규칙 편집기에서 사용 가능한 규칙에 대한 자세한 내용은 [규칙 편집기에서 사용 가능한 규칙 유형](rule-editor.md#p-available-rule-types-in-rule-editor-p)을 참조하십시오.

* 규칙을 작성할 때 일반적으로 경험하는 규칙은 규칙을 작성하는 객체의 컨텍스트에서 생각하는 것입니다. 필드 A에서 사용자가 지정하는 값에 따라 필드 B를 숨기거나 표시하려고 한다고 가정합니다. 이 경우 필드 A에서 조건을 평가하고 반환되는 값을 기반으로 필드 B에서 작업을 트리거합니다.

  따라서 필드 B(조건을 평가하는 객체)에 규칙을 작성하는 경우 조건-작업 구문 또는 시기 규칙 유형을 사용합니다. 마찬가지로 필드 A에서 작업 조건 구문 또는 표시 또는 숨기기 규칙 유형을 사용합니다.

* 한 가지 조건을 기반으로 여러 작업을 수행해야 하는 경우가 있습니다. 이러한 경우 조건-작업 구문을 사용하는 것이 좋습니다. 이 구문에서는 한 번 조건을 평가하고 여러 작업 문을 지정할 수 있습니다.

  예를 들어, 사용자가 필드 A에 지정한 값을 확인하는 조건에 따라 필드 B, C 및 D를 숨기려면 조건-작업 구문 또는 필드 A에 규칙 유형을 입력할 때 하나의 규칙을 작성하고 필드 B, C 및 D의 가시성을 제어하는 작업을 지정합니다. 그렇지 않으면 필드 B, C 및 D에 세 개의 별도 규칙이 필요합니다. 여기서 각 규칙은 조건을 확인하고 해당 필드를 표시하거나 숨깁니다. 이 예제에서는 세 개의 객체에 대한 표시 또는 숨기기 규칙 유형보다 When 규칙 유형을 한 객체에 작성하는 것이 더 효율적입니다.

* 여러 조건을 기반으로 작업을 트리거하려면 작업 조건 구문을 사용하는 것이 좋습니다. 예를 들어 필드 B, C 및 D의 조건을 평가하여 필드 A를 표시하거나 숨기려면 필드 A에서 표시 또는 숨기기 규칙 유형을 사용합니다.
* 규칙에 한 조건에 대한 한 가지 작업이 포함된 경우 조건-작업 또는 작업 조건 구문을 사용합니다.
* 규칙이 조건을 확인하고 필드에 값을 제공하거나 필드를 종료할 때 즉시 작업을 수행하는 경우 조건이 평가되는 필드에 조건-작업 구문 또는 When 규칙 유형이 있는 규칙을 작성하는 것이 좋습니다.
* 사용자가 When 규칙이 적용되는 객체의 값을 변경할 때 When 규칙의 조건이 평가됩니다. 그러나 값을 미리 채우는 경우처럼 값이 서버측에서 변경될 때 작업을 트리거하려면 필드가 초기화될 때 작업을 트리거하는 When 규칙을 작성하는 것이 좋습니다.
* 드롭다운, 라디오 단추 또는 확인란 개체에 대한 규칙을 작성할 때 양식에 있는 이러한 양식 개체의 옵션 또는 값이 규칙 편집기에 미리 채워집니다.

## 다음 단계

규칙 편집기에서 규칙을 작성 및 관리하기 위해 사용자 인터페이스를 사용하는 방법에 대한 자세한 내용은 [핵심 구성 요소를 기반으로 하는 적응형 Forms용 규칙 편집기 사용자 인터페이스](/help/forms/rule-editor-core-components-user-interface.md) 문서를 참조하십시오.

## 추가 참조

{{see-also-rule-editor}}