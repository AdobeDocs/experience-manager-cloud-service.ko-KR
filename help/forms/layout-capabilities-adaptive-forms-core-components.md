---
title: 핵심 구성 요소 기반 적응형 Forms의 레이아웃 기능은 무엇입니까?
description: 다양한 디바이스에서 적응형 Forms의 레이아웃 및 모습은 레이아웃 설정의 적용을 받습니다. 다양한 레이아웃과 적용 방법을 이해합니다.
feature: Adaptive Forms, Core Components
keywords: 핵심 구성 요소를 기반으로 하는 적응형 양식 레이아웃, 양식에 대한 다양한 레이아웃, 동적 양식 레이아웃 AEM, AEM Cloud Service 양식 레이아웃, AEM 핵심 구성 요소의 양식 레이아웃 유형, 적응형 양식 레이아웃
role: User, Developer, Admin
source-git-commit: 31f18027d856cbd161457c4a01d6c7c17d1c2b89
workflow-type: tm+mt
source-wordcount: '2107'
ht-degree: 1%

---


# 핵심 구성 요소 기반 적응형 Forms의 레이아웃 기능


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/layout-capabilities-adaptive-forms.html) |
| AEM as a Cloud Service(Foundation 구성 요소) | [여기 클릭](/help/forms/layout-capabilities-adaptive-forms.md) |
| AEM as a Cloud Service (핵심 구성 요소) | 이 문서 |

적응형 Forms은 양식을 효과적으로 레이아웃 및 디자인할 수 있는 퍼스트 클래스 구성 요소를 제공합니다. 레이아웃은 양식에 구성 요소가 표시되는 방식을 제어합니다. 적응형 Forms은 패널, 마법사, 아코디언, 상단/수평 탭의 탭, 왼쪽/수직 탭의 탭 등 다양한 레이아웃을 지원합니다.

![레이아웃 유형](/help/forms/assets/generic-layout-hero-image.png){align="center"}

## 전제 조건

레이아웃의 다양한 기능을 살펴보기 전에 환경에 대해 핵심 구성 요소가 활성화되었는지 확인하십시오. 환경에 핵심 구성 요소를 사용하도록 설정하는 방법에 대한 자세한 지침을 보려면 [여기를 클릭](/help/forms/enable-adaptive-forms-core-components.md)하세요.

## 적응형 Forms 레이아웃 유형

핵심 구성 요소를 기반으로 하는 적응형 양식은 다음과 같은 유형의 레이아웃을 지원합니다.
* **패널 레이아웃**
* **마법사 레이아웃**
* **세로 레이아웃**
* **가로 레이아웃**
* **아코디언 레이아웃**

>[!BEGINTABS]

>[!TAB 패널 레이아웃]

패널 레이아웃은 해당 컨텐츠를 더 쉽게 탐색하고 찾을 수 있도록 관련 필드를 구성하는 데 유용합니다. 패널 레이아웃은 적응형 양식의 개별, 섹션 또는 패널 내에 양식 구성 요소를 정렬합니다.

![패널 레이아웃](/help/forms/assets/panel-layout.png)

패널 레이아웃

[패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel)를 사용하여 양식에 패널 레이아웃을 추가할 수 있습니다. 패널 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) 문서를 참조하십시오.

>[!TAB 마법사 레이아웃]

마법사 레이아웃은 복잡한 양식을 별도의 단계로 나누어 단순화하는 데 도움이 됩니다. 각 단계는 프로세스의 다른 부분을 나타내며 사용자는 **다음** 및 **이전** 단추를 사용하여 단계를 순차적으로 탐색합니다. 마법사 레이아웃을 사용하여 여러 섹션이나 단계가 포함된 양식을 만들 수 있습니다.

![마법사 레이아웃](/help/forms/assets/wizard-layout-compare.gif)

마법사 레이아웃

[마법사 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard)를 사용하여 양식에 마법사 레이아웃을 추가할 수 있습니다. 마법사 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [마법사 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) 문서를 참조하십시오.

>[!TAB 세로 탭 레이아웃]

세로 탭 레이아웃은 왼쪽 레이아웃의 탭이라고도 합니다. 세로 탭 레이아웃은 폼의 왼쪽을 따라 패널이나 섹션을 구성합니다. 읽기 및 탐색이 쉽도록 패널/섹션이 세로로 스택된 양식에 대한 일반적인 레이아웃입니다.

![세로 레이아웃](/help/forms/assets/vertical-tab.gif)

세로 탭 레이아웃

[세로 탭 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs)를 사용하여 양식에 세로 탭 레이아웃을 추가할 수 있습니다. 세로 탭 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [세로 탭 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) 문서를 참조하십시오.


>[!TAB 가로 탭 레이아웃]

수평 탭 레이아웃은 상단 레이아웃의 탭이라고도 합니다. 가로 탭 레이아웃은 한 행에 패널이나 섹션을 나란히 정렬합니다. 이 레이아웃은 양식 또는 패널의 너비에 걸쳐 양식 섹션을 선형 방식으로 표시합니다.


![가로 레이아웃](/help/forms/assets/horizontal-layout.gif)

가로 탭 레이아웃

[가로 탭 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs)를 사용하여 양식에 가로 탭 레이아웃을 추가할 수 있습니다. 수평 탭 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [수평 탭 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) 문서를 참조하십시오.


>[!TAB 아코디언 레이아웃]

아코디언 레이아웃은 적응형 양식의 축소 가능한 섹션이나 패널에 콘텐츠를 표시합니다. 섹션을 확장하면 내의 컨텐츠가 표시되고 다른 섹션은 축소된 상태로 유지됩니다. 이 레이아웃은 대량의 정보를 컴팩트한 형식으로 표시하는 데 이상적입니다.

![아코디언 레이아웃](/help/forms/assets/accordion-layout-compare.gif)

어코디언 레이아웃

[아코디언 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion)를 사용하여 양식에 아코디언 레이아웃을 추가할 수 있습니다. 아코디언 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [아코디언 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) 문서를 참조하십시오.

>[!ENDTABS]

레이아웃을 삽입하고 양식 구성 요소를 추가하는 방법에 대한 자세한 내용은 [레이아웃을 삽입하고 양식 구성 요소를 추가하는 방법](#how-to-insert-a-layout-and-add-form-components-to-it)이라는 섹션을 참조하십시오.

### 올바른 적응형 양식 레이아웃을 선택하는 방법

사용자 경험과 양식 기능을 최적화하려면 올바른 적응형 양식 레이아웃을 선택하는 것이 중요합니다. 이 표는 사용 가능한 다양한 레이아웃 옵션을 이해하는 데 도움이 되며 특정 요구 사항 및 사용 사례에 따라 가장 적합한 레이아웃을 선택할 수 있도록 안내합니다.

| 기능 | 패널 레이아웃 | 마법사 레이아웃 | 상단/수직 탭 레이아웃의 탭 | 왼쪽/가로 탭 레이아웃의 탭 | 어코디언 레이아웃 |
|--------------------------|-----------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------|--------|
| **목적** | 관련 콘텐츠를 개별 섹션으로 그룹화 | 여러 단계 프로세스 또는 양식을 안내합니다. | 동일한 페이지에서 섹션/보기 간 전환 허용 | 상단 탭과 유사하지만 왼쪽에 세로로 정렬됨 | 콘텐츠를 축소 가능한 섹션으로 구성 |
| **구조** | 개별 섹션 | 순차적 단계/페이지 | 상단의 가로 탭 | 왼쪽의 세로 탭 | 축소 가능한 패널/섹션 |
| **탐색** | 탐색할 패널 헤더를 클릭합니다 | - 앞으로: &quot;다음&quot; 단추<br>- 뒤로: &quot;뒤로&quot; 단추<br>- 선택적 건너뛸 단계 | 탭을 클릭하여 섹션 전환 | 탭을 클릭하여 섹션 전환 | 섹션을 확장/축소하려면 헤더를 클릭하십시오. |
| **사용자 환경** | 대량의 컨텐츠를 관리 가능한 방식으로 구성 | 단계별 지침을 통해 과중한 업무 부담 감소 | 보기 간 액세스 가능한 지우기 전환 | 세로 공간을 효율적으로 사용하고 항상 표시되는 탭 | 확장/축소된 단면이 있는 컴팩트한 보기 |
| **사용 사례** | 분류된 섹션이 있는 복잡한 양식 | 프로세스 설정, 복잡한 양식 | 설정 또는 콘텐츠 범주 구성 | 대시보드, 복잡한 데이터 보기 | FAQ, 설정 메뉴, 세부 콘텐츠 섹션 |


## 레이아웃을 삽입하고 양식 구성 요소를 추가하는 방법

아래 다이어그램은 양식에 레이아웃을 삽입하고 양식 구성 요소를 추가하는 단계를 보여 줍니다.

![레이아웃 및 양식 구성 요소를 추가하는 워크플로](/help/forms/assets/workflow-to-add-component-to-a-layout.png)

[적응형 Forms 레이아웃 유형](#adaptive-forms-layout-types) 섹션에 표시된 **IT 요청 양식**&#x200B;을 고려하십시오. 이 양식은 네트워크 또는 노트북과 관련된 기술 문제를 경험하는 직원으로부터 정보를 수집합니다. 여기에는 세 개의 패널이 포함됩니다.

* **직원 세부 정보**: 패널에서는 직원에 대한 정보를 수집하고 이름, 전자 메일 ID 및 부서라는 텍스트 상자 세 개를 포함합니다.

* **문제 세부 정보**: 패널은 문제에 대한 세부 정보를 캡처합니다. 여기에는 세 가지 옵션(네트워크, 컴퓨터 또는 기타)이 있는 문제 범주에 대한 확인란이 포함됩니다. 또한 Please Specify 및 Comments 라는 두 개의 텍스트 상자가 있습니다.

* **첨부 파일**: 사용자가 문제와 관련된 지원 문서를 업로드할 수 있습니다.

레이아웃을 삽입하고 여기에 구성 요소를 추가하는 단계별 프로세스를 살펴보겠습니다. 이 예제에서 가로 탭 레이아웃은 폼에 삽입됩니다.

### 1. 양식에 레이아웃 구성 요소 삽입

1. [!DNL Experience Manager Forms] 인스턴스에 로그인합니다.
1. 왼쪽 상단 모서리에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;를 선택합니다.
1. 기존 적응형 양식이 이미 생성된 경우 편집 모드로 엽니다.

   ![적응형 양식 열기](/help/forms/assets/insert-layout.png)

   또는 [새 적응형 양식을 만들](/help/forms/creating-adaptive-form-core-components.md)수도 있습니다.

1. 양식 편집기 내에서 레이아웃을 추가할 수 있는 섹션을 찾습니다.

   ![양식 편집기](/help/forms/assets/form-editor.png){width="200" align="center"}
1. **추가** 아이콘을 클릭합니다. 아이콘은 새 구성 요소를 추가하는 옵션을 나타내는 더하기 기호(+)입니다.

   ![레이아웃 삽입](/help/forms/assets/insert-layout-add-icon.png){width="200" align="center"}

   **추가** 아이콘을 클릭하면 삽입할 다양한 구성 요소를 표시하는 **새 구성 요소 삽입** 대화 상자가 표시됩니다.

   >[!NOTE]
   >
   > 또는 [레이아웃 구성 요소를 드래그 앤 드롭할 수](#extra-bytes)도 있습니다.

1. 대화 상자에서 사용 가능한 구성 요소를 탐색하고 목록에서 원하는 레이아웃을 선택합니다. 여기서는 수평 탭 레이아웃을 삽입할 수평 탭 구성 요소를 선택합니다.

   ![가로 탭 선택](/help/forms/assets/select-horizontal-tab.png){width="200" align="center"}

   양식에 가로 탭 구성 요소를 추가하면 처음에는 기본적으로 Item1과 Item2라는 두 개의 빈 패널로 구성됩니다. 이러한 패널에 양식 구성 요소를 수동으로 추가해야 합니다.

   ![가로 탭](/help/forms/assets/insert-tabs-on-top.png){width="200" align="center"}

1. 수평 탭 구성 요소의 속성을 열고 구성 요소의 이름을 지정합니다.
예를 들어 이 경우 가로 탭 구성 요소의 이름을 IT 요청 양식으로 추가합니다.

   ![가로 탭의 이름 추가](/help/forms/assets/change-name-of-horizontal-tabs.png){width="200" align="center"}

1. **완료**&#x200B;를 클릭합니다.

   ![가로 탭](/help/forms/assets/tabs-on-top-rename-component.png){width="200" align="center"}

레이아웃 구성 요소가 양식에 추가되면 요구 사항에 따라 패널 수를 수정합니다.

### 2. 레이아웃에 패널 추가

가로 탭 구성 요소에 새 패널 추가:

1. 가로 탭 구성 요소 속성을 열고 **항목** 탭을 클릭합니다.

   ![가로 탭의 항목 탭](/help/forms/assets/tabs-on-top-items-tab.png){width="200" align="center"}

1. 새 패널을 추가하려면 **추가** 아이콘을 클릭하십시오.

   ![새 패널 추가](/help/forms/assets/tabs-on-top-add-panel.png){width="200" align="center"}

   **추가** 아이콘을 클릭하면 **새 구성 요소 삽입** 대화 상자가 나타납니다.

1. 패널 구성 요소를 선택합니다.

   ![새 패널 추가](/help/forms/assets/tabs-on-top-new-panel.png){width="200" align="center"}

   패널 구성 요소를 선택하면 새 패널이 가로 레이아웃에 추가됩니다.

   ![새 패널 추가](/help/forms/assets/tabs-on-top-add-new-panel.png){width="200" align="center"}

   새 패널의 이름을 입력합니다. 그렇지 않으면 가로 탭 구성 요소의 속성을 저장할 수 없습니다.

1. 아래 그림과 같이 패널 이름을 지정합니다.

   ![패널 이름](/help/forms/assets/tabs-on-tops-panel-name.png){width="200" align="center"}

1. **완료**&#x200B;를 클릭합니다.

   **완료**&#x200B;를 클릭하면 세 개의 패널이 나란히 표시됩니다. 패널 이름은 각 패널의 제목으로 표시되며 양식 구성 요소를 각 패널에 추가할 수 있습니다.

   ![패널 이름](/help/forms/assets/tabs-on-top-initial-view.png){width="200" align="center"}

   패널 구성 요소의 속성을 구성할 수 있습니다. 예를 들어 IT 요청 양식에 패널 제목이 포함되지 않은 경우 패널 구성 요소의 속성을 구성하는 단계입니다.

1. 첫 번째 패널의 속성을 엽니다.

   ![패널 1 속성](/help/forms/assets/tabs-on-tops-panel1-properties.png){width="200" align="center"}

1. **기본** 탭에서 **제목 숨기기** 확인란을 선택합니다.

   ![제목 숨기기](/help/forms/assets/tabs-on-top-hide-panel.png){width="200" align="center"}

1. **완료**&#x200B;를 클릭합니다.

마찬가지로 다른 두 패널의 제목도 숨길 수 있습니다. 완료되면 각 패널에 양식 구성 요소를 추가할 수 있습니다.

### 3. 패널에 양식 구성 요소 추가

<!-- You can employ one of the following method to add form components to the panel:
* [Add components to a layout's panel using the Add icon](#add-components-to-a-layouts-panel-using-the-add-icon)
* [Drag and drop components into a layout's panel](#drag-and-drop-components-into-a-layouts-panel) -->

1. 패널 내에서 구성 요소를 추가할 수 있는 섹션을 찾습니다.
1. **추가** 아이콘을 클릭합니다. 아이콘은 새 구성 요소를 추가하는 옵션을 나타내는 더하기 기호(+)입니다.
   ![레이아웃 삽입](/help/forms/assets/tabs-on-top-add-component.png){width="200" align="center"}

   **추가** 아이콘을 클릭하면 삽입할 다양한 구성 요소를 표시하는 **새 구성 요소 삽입** 대화 상자가 표시됩니다.

   ![새 구성 요소 삽입 대화 상자](/help/forms/assets/insert-new-component.png){width="200" align="center"}

1. 표시되는 대화 상자에서 사용 가능한 구성 요소를 탐색하고 원하는 구성 요소를 선택합니다. 여기서는 텍스트 상자 구성 요소를 선택합니다.
1. 추가된 구성 요소의 속성을 열고 이름을 지정합니다. 추가된 텍스트 상자 구성 요소의 속성을 편집하고 이름을 지정합니다.
   ![레이아웃 삽입](/help/forms/assets/tabs-on-top-textbox-component.png){width="200" align="center"}
1. 마찬가지로 텍스트 상자 구성 요소와 이름을 두 개 더 추가하고 구성 요소를 이메일 ID 및 부서로 추가했습니다.\
   ![첫 번째 패널](/help/forms/assets/tabs-on-tops-first-panel.png){width="200" align="center"}

   이제 첫 번째 패널의 구성 요소가 추가되었으므로 두 번째 패널에 구성 요소를 추가할 수 있습니다.

1. 패널을 전환하려면 도구 모음에서 **패널 선택**&#x200B;을 클릭합니다.

   ![패널 전환](/help/forms/assets/tabs-on-top-select-panel.png){width="200" align="center"}

   **패널 선택**&#x200B;을 클릭하면 [가로 탭] 구성 요소에 추가된 패널 목록이 나타납니다.

   ![패널 전환](/help/forms/assets/tabs-on-tops-panel2.png){width="200" align="center"}

1. 패널 목록에서 **2개 패널**&#x200B;을 선택하면 첫 번째 패널에서 두 번째 패널로 보기가 변경됩니다.

   ![두 번째 패널](/help/forms/assets/tabs-on-top-panel2-component.png){width="200" align="center"}

1. 아래 그림과 같이 패널 2에 원하는 구성 요소를 추가하려면 단계 2에서 단계 4까지 설명된 단계를 반복합니다.

   ![두 번째 패널 구성 요소](/help/forms/assets/panel-2-components.png){width="200" align="center"}

1. 6단계 및 7단계에 설명된 단계를 수행하여 **3 패널**(으)로 전환합니다.

1. 패널 3에 원하는 구성 요소를 추가하려면 단계 2에서 단계 4까지 설명된 단계를 반복합니다.

   ![세 번째 패널 구성 요소](/help/forms/assets/panel-3-component.png){width="200" align="center"}

1. 작성 환경의 오른쪽 상단 모서리에서 **[!UICONTROL 미리 보기]**&#x200B;를 클릭합니다.

   ![가로 레이아웃](/help/forms/assets/horizontal-layout.gif)

[구성 요소를 드래그 앤 드롭하여](#extra-bytes)하여 각 패널에 양식 구성 요소를 추가할 수도 있습니다.


<!-- #### Drag and drop components into a layout's panel 

1. Locate the section within the panel that allows you to add components. 
2. Navigate to the left panel within your authoring environment and click **Components**.

    ![Component Panel](/help/forms/assets/add-new-component.png){width="200" align="center"}

    When you click the **Components** option, the list of the available components appears.   

    ![Component Panel](/help/forms/assets/add-new-component2.png){width="200" align="center"}

3. Browse the available components and select the Text Box component.

4. Drag the component by clicking and holding the selected component, then drag it over to the panel area to place it.

5. Drop the component into the panel by releasing the mouse. 

6. Open the properties of the added Text Box component and specify its name as Name.
    ![Insert layout](/help/forms/assets/tabs-on-top-textbox-component.png){width="200" align="center"}
7. Similarly, add two more Text Box components and name added the components as Email ID and Department.   
    ![First Panel](/help/forms/assets/tabs-on-tops-first-panel.png){width="200" align="center"}

    Now that the components in the first panel have been added, you can proceed with adding the components to the second panel. 

8. To switch the panel, click **Select Panel** from the toolbar. 

    ![Switch Panel](/help/forms/assets/tabs-on-top-select-panel.png){width="200" align="center"}

    When you click the **Select Panel**, the list of the added panels in the Horizontal Tabs component appears.

    ![Switch Panel](/help/forms/assets/tabs-on-tops-panel2.png){width="200" align="center"}

9. Select **2 Panel** from the panel list and the view changes from the first panel to the second panel.

    ![Second Panel](/help/forms/assets/tabs-on-top-panel2-component.png){width="200" align="center"}

10. Repeat the steps outlined from Step 2 to Step 6 for adding the desired components in panel 2 as shown in the below figure:   

     ![Second Panel components](/help/forms/assets/panel-2-components.png){width="200" align="center"}

11. Switch to the **3 Panel** by following the steps outlined in Step 8 and Step 9.

12. Repeat the steps outlined from Step 2 to Step 6 for adding the desired component in panel 3:

    ![Third Panel components](/help/forms/assets/panel-3-component.png){width="200" align="center"} 

    -->



![삭제 아이콘](/help/forms/assets/Smock_Delete_18_N.svg) 아이콘을 사용하여 패널에서 양식 구성 요소를 삭제할 수도 있습니다.

![구성 요소 삭제](/help/forms/assets/delete-component.png){width="200" align="center"}

필요에 따라 구성 요소에 대한 필수 검증을 추가할 수도 있습니다.

## 기존 레이아웃을 새 레이아웃으로 바꾸는 방법

양식의 레이아웃을 새 레이아웃으로 바꿀 수 있습니다. 이 레이아웃에는 양식 내에서 구성 요소가 정렬되고 표시되는 방식이 수정됩니다.



양식의 기존 레이아웃을 바꾸려면 다음 단계를 수행하십시오.

1. 레이아웃 구성 요소의 도구 모음에서 바꾸기 아이콘을 클릭하면 **[!UICONTROL 구성 요소 바꾸기]** 대화 상자가 나타납니다.

   ![레이아웃 바꾸기](/help/forms/assets/replace-layout.png){width="200" align="center"}

1. **[!UICONTROL 구성 요소 바꾸기]** 대화 상자에서 원하는 레이아웃을 선택합니다.

   ![구성 요소 바꾸기 대화 상자](/help/forms/assets/replace-component.png){width="200" align="center"}

   레이아웃을 선택하면 그에 따라 레이아웃 내의 구성 요소 배열이 변경됩니다. 예를 들어, **[!UICONTROL 구성 요소 바꾸기]** 대화 상자에서 세로 탭 구성 요소를 선택합니다. 패널 배열이 왼쪽의 탭으로 변경됩니다.

   ![세로 레이아웃](/help/forms/assets/vertical-tab.gif)

## 추가 바이트

구성 요소를 양식 편집기로 드래그 앤 드롭하려면 다음 단계를 수행하십시오.

1. 구성 요소를 추가할 수 있는 섹션을 찾습니다.
1. 작성 환경의 왼쪽 패널로 이동하여 **구성 요소**&#x200B;를 클릭합니다.

   ![구성 요소 패널](/help/forms/assets/add-new-component.png){width="200" align="center"}

   **구성 요소** 옵션을 클릭하면 사용 가능한 구성 요소 목록이 나타납니다.

   ![구성 요소 패널](/help/forms/assets/add-new-component2.png){width="200" align="center"}

1. 사용 가능한 구성 요소를 탐색하고 원하는 구성 요소를 선택합니다.

1. 선택한 구성 요소를 클릭하고 누른 채로 구성 요소를 드래그하여 패널 영역에 놓습니다.

1. 마우스를 놓아 구성 요소를 패널에 놓습니다.

## 다음 단계

핵심 구성 요소를 기반으로 하는 적응형 양식의 다양한 레이아웃 기능에 익숙해지면 다음 단계로 이동할 수 있습니다.

* [핵심 구성 요소를 기반으로 첫 번째 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [적응형 양식 테마 만들기 및 사용](/help/forms/using-themes-in-core-components.md)



## 추가 참조

{{see-also}}