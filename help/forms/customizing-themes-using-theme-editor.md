---
title: 테마 편집기를 사용하여 적응형 양식 테마 맞춤화
description: 테마 편집기를 사용하여 Adobe Experience Manager의 핵심 구성 요소 기반 적응형 Forms에 대한 시각적 테마를 만들고 맞춤화하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: f1b318803b9b854ec2ce800670f6484799113599
workflow-type: tm+mt
source-wordcount: '1951'
ht-degree: 1%

---


# 양식 테마 맞춤화 {#customizing-form-themes}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/themes.html) |
| AEM as a Cloud Service | 이 문서 |

Adobe Experience Manager(AEM) Forms의 테마 편집기는 수동으로 코드를 작성하지 않고도 적응형 Forms에 대한 테마를 만들고 맞춤화할 수 있는 시각적 인터페이스입니다. 테마는 배경색, 글꼴 스타일, 테두리, 치수 및 간격 등 양식 구성 요소와 패널의 모양과 느낌을 정의합니다. 테마를 적용하면 지정된 스타일이 해당 구성 요소를 반영하므로 여러 적응형 Forms에서 동일한 테마를 다시 사용할 수 있습니다.

테마 편집기를 사용하면 기본 양식 스타일을 위한 전용 개발자 페르소나를 사용할 필요가 없습니다. CSS에 대한 실무 지식을 바탕으로 시각적 사이드바를 사용하여 양식의 스타일을 지정하거나 편집기 내에서 직접 고급 CSS 무시를 작성할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

* Adobe Experience Manager Forms의 작성자 수준 권한.
* CSS 스타일 원칙에 대한 기본 이해입니다. 전체 CSS 참조에 대해서는 [MDN 웹 문서 CSS 참조](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)를 참조하십시오.

## 테마 디렉토리로 이동합니다. {#navigate-to-themes}

1. AEM 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL 테마]**&#x200B;로 이동합니다.

   테마 디렉터리에는 사용자 또는 조직에서 만든 사용자 지정 테마와 함께 AEM 캔버스에서 제공하는 표준 테마를 포함하여 사용 가능한 모든 테마가 표시됩니다.

### 새 테마 만들기 {#create-a-new-theme}

1. 테마 디렉터리에서 새 테마를 저장할 폴더를 선택합니다.
1. **[!UICONTROL 만들기]** > **[!UICONTROL 테마]**&#x200B;를 클릭합니다.

   ![새 테마 만들기](/help/forms/assets/custom-theme-create.png)

1. **[!UICONTROL 테마 만들기]** 대화 상자에서 다음 세부 정보를 지정합니다.
   * **[!UICONTROL 제목]**: 테마를 설명하는 제목입니다.
   * **[!UICONTROL 이름]**: 테마의 노드 이름입니다.
   * **[!UICONTROL 테마를 미리 볼 적응형 양식]**: 핵심 구성 요소 테마의 경우 핵심 구성 요소 기반 적응형 양식을 선택하십시오. **[!UICONTROL 기본 적응형 양식 사용]**&#x200B;은(는) 핵심 구성 요소가 아닌 기초 적응형 양식을 사용합니다. 편집하는 동안 실시간 미리 보기를 위해 선택한 양식이 테마 편집기 캔버스에 표시됩니다.
   * **[!UICONTROL 설명]** *(선택 사항)*: 테마에 대한 간략한 설명입니다.
   * **[!UICONTROL 구성 컨테이너]** *(선택 사항)*: Adobe 글꼴 구성 세부 정보를 포함하는 구성 컨테이너입니다.
   * **[!UICONTROL 태그]** *(선택 사항)*: 식별 및 검색을 위해 테마에 첨부된 태그
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.

   ![사용자 지정 테마 구성](/help/forms/assets/custom-theme-name.png)

   테마가 만들어집니다. 이제 **[!UICONTROL 편집]**&#x200B;을 클릭하여 테마 편집기에서 열 수 있습니다.

### 기존 테마 편집 {#edit-an-existing-theme}

1. **테마** 디렉터리에서 수정할 테마를 선택합니다.
1. 작업 표시줄에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 테마 편집기에서 테마를 엽니다.

   ![테마 편집](/help/forms/assets/custom-theme-edit.png)

### 테마 업로드 {#upload-a-theme}

테마 패키지(예: 다른 환경에서 내보낸 패키지)를 테마 디렉터리로 가져올 수 있습니다.

1. **테마** 디렉터리에서 **[!UICONTROL 만들기]** > **[!UICONTROL 파일 업로드]**&#x200B;를 클릭합니다.
1. 컴퓨터에서 테마 패키지(ZIP 파일)를 찾아 선택한 다음 **[!UICONTROL 업로드]**&#x200B;를 클릭합니다.

   ![테마 업로드 - 파일 업로드 옵션으로 메뉴 만들기](/help/forms/assets/custom-theme-upload.png)

업로드한 테마는 테마 디렉터리에 표시되며 다른 테마와 같이 편집할 수 있습니다.

### 테마 다운로드 {#download-a-theme}

테마를 패키지(ZIP 파일)로 내보내 다른 AEM Forms 환경에서 재사용하거나 백업할 수 있습니다.

1. **테마** 디렉터리에서 테마를 하나 이상 선택합니다(테마 카드의 확인란 사용).
1. 작업 표시줄에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다. 선택한 테마의 세부 정보가 포함된 대화 상자가 나타날 수 있습니다.
1. 확인하거나 대화 상자에서 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다. 테마 패키지가 ZIP 파일로 컴퓨터에 다운로드됩니다.

   ![테마 다운로드 - 테마를 선택하고 다운로드 클릭](/help/forms/assets/custom-theme-download.png)

이 ZIP은 나중에 [동일한 환경 또는 다른 환경에서 테마 업로드](#upload-a-theme)를 사용하여 업로드할 수 있습니다.

## 테마 편집기 인터페이스 이해 {#understand-the-theme-editor}

테마 편집기에서 테마를 열면 다음 두 가지 기본 영역이 표시됩니다.

![테마 편집기](/help/forms/assets/custom-theme-editor.png)

* **캔버스**(오른쪽): 테마에 연결된 적응형 양식의 미리 보기를 표시합니다. 모든 스타일 변경 사항은 즉시 여기에 반영되므로 편집 사항의 영향을 실시간으로 확인할 수 있습니다.
* **사이드바**(왼쪽): Page, Form, Field, Button, Panel, Image, hCaptcha 및 reCaptcha와 같은 트리 구조에서 스타일링 가능한 모든 양식 구성 요소를 나열하는 **선택기** 패널을 포함합니다.

### 캔버스 도구 모음 {#canvas-toolbar}

![사이드 패널 전환, 실행 취소, 다시 실행, 에뮬레이터, 편집/미리 보기 및 테마 옵션이 있는 테마 편집기 캔버스 도구 모음](/help/forms/assets/custom-theme-toolbar-utilities.png)

도구 모음은 왼쪽에서 오른쪽으로 다음을 제공합니다.
* **A: 사이드 패널 전환**: 선택기 사이드바를 표시하거나 숨깁니다. 캔버스에 초점을 맞추려는 경우 양식 미리 보기 영역을 최대화하거나 구성 요소를 선택하거나 스타일을 지정해야 하는 경우 사이드바를 다시 표시하려면 이 옵션을 사용합니다.
* **B: 테마 옵션**(드롭다운): 네 가지 옵션이 있는 메뉴를 엽니다. 미리 보기 양식을 변경하거나, CSS를 보거나, 저장된 스타일을 관리하거나, 편집기 내 도움말을 보려면 클릭하십시오. 테마 옵션 드롭다운을 열면 다음과 같이 표시됩니다.

  ![구성, 테마 CSS 보기, 스타일 관리 및 도움말을 표시하는 테마 옵션 드롭다운](/help/forms/assets/custom-theme-configure.png)

   * **[!UICONTROL 구성]**: 캔버스에 표시된 양식을 다른 적응형 양식으로 전환합니다. 편집기를 종료하지 않고 다른 양식에서 테마가 어떻게 보이는지 확인할 수 있습니다.
     ![테마 미리 보기를 위한 적응형 양식 구성](/help/forms/assets/custom-theme-switch-af.png)
   * **[!UICONTROL 테마 CSS 보기]**: 테마의 전체 컴파일된 CSS로 대화 상자를 엽니다. 현재 선택한 구성 요소의 CSS만 보려면 사이드바에서 **[!UICONTROL CSS 보기]**를 대신 사용하십시오(규칙 디버깅 또는 복사에 편리함).
     ![최종 CSS 보기](/help/forms/assets/custom-theme-view-css.png)
   * **[!UICONTROL 스타일 관리]**: 텍스트 및 이미지 스타일을 저장하고, 이름을 지정하고, 다시 사용하려면 대화 상자를 엽니다. 저장된 스타일을 다른 구성 요소에 적용할 수 있습니다. 최근에 사용한 스타일도 빠르게 재사용할 수 있도록 나타날 수 있습니다.
   * **[!UICONTROL 도움말]**: 테마 편집기의 이미지 둘러보기를 시작합니다.
* **C: 실행 취소/다시 실행**: 마지막 스타일 변경 내용을 되돌리거나 다시 적용합니다. 스타일을 시도해 보고 다른 편집 내용을 잃지 않고 뒤로 물러나려는 경우에 유용합니다.
* **D: 에뮬레이터**: 화면 크기로 양식을 미리 볼 장치 또는 중단점(예: 데스크톱, 태블릿 또는 모바일)을 선택하십시오. 양식 미리 보기는 선택한 중단점과 일치하도록 크기가 조정됩니다. 중단점을 선택한 동안 설정한 모든 스타일은 해당 중단점에만 적용되므로 응답형 스타일을 정의할 수 있습니다. 자세한 내용은 [다양한 화면 크기를 위한 스타일 지정](#styling-for-different-screen-sizes)을 참조하십시오.
* **E: 편집/미리 보기**: 두 모드 간에 전환합니다. **편집**&#x200B;이 기본값입니다. 캔버스에서 구성 요소를 클릭하여 선택하고 사이드바에서 스타일을 변경할 수 있습니다. **미리 보기**&#x200B;에서는 선택 테두리, 구성 요소 레이블 또는 스타일 사이드바 없이 최종 사용자에게 표시되는 양식이 표시되므로 게시하기 전에 테마 양식의 모양과 동작을 확인할 수 있습니다.

<!--**3. Bottom of the sidebar: Simulate Error and Simulate Success**

When you style components by state (for example, Error or Success), you can preview that look without submitting the form. In AEM Forms as a Cloud Service, **Simulate Error** and **Simulate Success** are available at the **bottom of the left sidebar**. Scroll down in the sidebar if you don’t see them; they appear when you have a component selected and let you toggle the preview to match the Error or Success state.

* **Simulate Error**: Show the form as if a field failed validation, so you can see your **[!UICONTROL Error]** state styling.
* **Simulate Success**: Show the form as if validation passed, so you can see your **[!UICONTROL Success]** state styling.

Toggle these on or off as you adjust styles for each state. For more on styling by state, see [Style by component state](#style-by-state).-->

### 구성 요소 스타일 지정

다음 두 가지 방법으로 스타일을 지정할 구성 요소를 선택할 수 있습니다.
* **캔버스에서**: 양식의 구성 요소(예: 텍스트 필드, 단추 또는 드롭다운)를 직접 클릭합니다. 선택한 요소는 테두리로 강조 표시되고 구성 요소 레이블(예: &quot;텍스트 입력 위젯&quot;)이 그 위에 나타납니다. 사이드바에 해당 구성 요소의 스타일 옵션이 나타납니다.

  ![캔버스에서 테마 편집](/help/forms/assets/custom-theme-field-level.png)

* **선택기 패널에서**: 왼쪽 사이드바의 트리 구조를 사용하여 특정 구성 요소로 드릴다운합니다. 예를 들어 **[!UICONTROL 필드]** > **[!UICONTROL 위젯]** > **[!UICONTROL 텍스트 입력]**&#x200B;을 확장하여 텍스트 상자 위젯을 특별히 타겟팅합니다.

  ![선택기 패널에서 테마 편집](/help/forms/assets/custom-theme-selector.png)

#### 구성 요소에 스타일 적용 {#apply-styles-to-a-component}

구성 요소를 선택하면 사이드바에 사용 가능한 스타일 속성이 다음 카테고리로 구성됩니다.

* **[!UICONTROL 차원 및 위치]**: 정렬, 크기, 패딩, 여백, 너비, 높이 및 Z 인덱스를 제어합니다.
* **[!UICONTROL 텍스트]**: 글꼴 모음, 두께, 색상, 크기, 줄 높이, 맞춤, 문자 간격, 텍스트 장식 및 변형을 구성합니다. 지원되는 CSS 텍스트 속성의 전체 목록을 보려면 [MDN CSS 텍스트 설명서](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_text)를 참조하십시오.
* **[!UICONTROL 배경]**: 배경색, 이미지 또는 그라데이션을 설정합니다. [MDN CSS 배경 설명서](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_backgrounds_and_borders)를 참조하세요.
* **[!UICONTROL 테두리]**: 테두리 너비, 스타일, 반경 및 색을 정의합니다.
* **[!UICONTROL 효과]**: 불투명도, 혼합 모드 및 그림자를 추가합니다.

스타일을 적용하려면:

1. 캔버스 또는 선택기 패널에서 구성 요소를 선택합니다.
1. 사이드바에서 원하는 시각적 속성을 설정합니다. 예를 들어 **[!UICONTROL 배경색]**&#x200B;을 선택하고 **[!UICONTROL 글꼴 색]**&#x200B;을 조정합니다.
1. 확인 표시 아이콘 **[!UICONTROL 확인]**&#x200B;을 클릭하여 속성 변경을 확인합니다.

   ![스타일 적용](/help/forms/assets/custom-theme-applying-style.png)

<!--#### Style by component state {#style-by-state}

Components can have different visual states (for example, default, focus, hover, disabled, error, success). You can style each state separately so the form looks correct during user interaction and validation.

1. Select the component from the canvas or the Selectors panel.
1. In the sidebar, use the **[!UICONTROL State]** dropdown to choose the state you want to style (for example, **[!UICONTROL Default]**, **[!UICONTROL Focus]**, **[!UICONTROL Hover]**, **[!UICONTROL Disabled]**, **[!UICONTROL Error]**, or **[!UICONTROL Success]**).
1. Set the styling properties (Background, Border, Text, and so on) for that state.
1. Click **[!UICONTROL OK]** to confirm.

   ![State dropdown in sidebar for styling Default, Focus, Error, Success, and other states](/help/forms/assets/custom-theme-state-dropdown.png)

The styles you define apply only when the component is in the selected state. For example, if you set a red border and red background for the **[!UICONTROL Error]** state, the field shows that styling when validation fails. If your environment supports it, use **Simulate Error** or **Simulate Success** at the bottom of the sidebar to preview how the component looks in those states without submitting the form.-->

### 양식 수준 스타일 지정 {#form-level-styling}

양식 수준 스타일링은 동일한 유형의 모든 구성 요소에 스타일을 광범위하게 적용합니다. 예를 들어 **[!UICONTROL 선택기]** 패널에서 **필드**&#x200B;를 선택하고 배경색을 파란색으로 설정하면 양식의 모든 필드(텍스트 상자, 숫자 상자, 날짜 선택기 및 드롭다운)가 해당 파란색 배경을 상속합니다.

**예:** 양식의 모든 필드에 균일한 배경색을 설정하려면:

1. **선택기** 패널에서 **[!UICONTROL 필드]**&#x200B;을(를) 선택합니다.
1. 사이드바에서 **[!UICONTROL 배경색]**&#x200B;을 파란색으로 설정합니다.
1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

   ![양식 수준 스타일 지정](/help/forms/assets/custom-theme-form-level-styling.png)

이제 양식의 모든 필드 구성 요소에 파란색 배경이 표시됩니다.

### 구성 요소 수준 스타일 지정 {#component-level-styling}

구성 요소 수준 스타일링은 특정 구성 요소 유형을 타깃팅하여 더 광범위한 양식 수준 스타일을 재정의합니다. 예를 들어 다른 모든 필드는 파란색으로 유지하면서 텍스트 상자 위젯만 다른 배경색을 갖도록 하려면 텍스트 상자 위젯을 특별히 타겟팅합니다.

**예:** 텍스트 상자 위젯에만 녹색 배경과 자주색 글꼴을 설정하려면 다음을 수행합니다.

1. 선택기 패널에서 **[!UICONTROL 필드]** > **[!UICONTROL 위젯]** > **[!UICONTROL 텍스트 입력]**&#x200B;을 확장합니다.
1. **[!UICONTROL 글꼴 색상]**을 자주색으로 설정합니다.
   ![필드 수준 스타일](/help/forms/assets/custom-theme-field-level-styling1.png)
1. **[!UICONTROL 배경색]**을(를) 녹색으로 설정합니다.
   ![필드 수준 스타일](/help/forms/assets/custom-theme-field-level-styling2.png)
1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

이제 텍스트 상자 위젯에 자주색 텍스트가 있는 녹색 배경이 표시되지만 다른 모든 필드는 양식 수준 스타일에서 파란색으로 유지됩니다.

>[!NOTE]
>
> **구성 요소 수준의 스타일이 항상 양식 수준의 스타일링보다 우선합니다.** 스타일이 두 수준에서 정의된 경우 더 구체적인 구성 요소 수준 선택기가 더 광범위한 양식 수준 선택기를 재정의합니다. 표준 [CSS 특정 규칙](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)을 따릅니다. 예를 들어 모든 필드(양식 수준)에 파란색 배경을 설정하고 텍스트 상자 위젯(구성 요소 수준)에 녹색 배경을 설정하면 텍스트 상자에 녹색 배경이 표시됩니다.

## 다양한 화면 크기에 맞는 스타일링 {#styling-for-different-screen-sizes}

테마가 반응할 수 있도록 다양한 장치 크기에 대해 다양한 스타일을 정의할 수 있습니다. 테마 편집기 도구 모음에는 해당 화면 크기로 양식을 미리 보고 스타일링할 수 있는 **장치 옵션**(예: iPhone 5, iPad, 데스크톱, 태블릿, 작은 화면)이 표시됩니다.

1. 캔버스 도구 모음에서 **장치 에뮬레이터** 사용: 장치 레이블 중 하나를 클릭합니다(예: **[!UICONTROL 데스크톱]**, **[!UICONTROL 태블릿]**, **[!UICONTROL iPad]**, **[!UICONTROL 작은 화면]**). 양식 위에 있는 눈금자는 선택한 장치의 픽셀 너비를 보여 줍니다.
1. 해당 장치를 선택한 상태에서 사이드바를 사용하여 스타일을 설정하거나 조정합니다. 스타일은 선택한 장치 보기에만 적용됩니다.
1. 다른 장치로 전환하고 필요에 따라 장치 스타일을 정의합니다.
1. **[!UICONTROL 확인]**&#x200B;을 클릭하고 완료되면 테마를 저장합니다.

   ![테마 편집기의 장치 에뮬레이터 - 눈금자 및 장치 옵션(데스크톱, 태블릿, iPad, 작은 화면)](/help/forms/assets/custom-theme-emulator.png)

따라서 동일한 테마는 장치마다 다른 간격, 글꼴 크기 또는 레이아웃 관련 스타일을 가질 수 있으며, 이는 응답형 스타일에 대한 [AEM 6.5 테마 편집기 동작](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/themes.html)과(와) 일치합니다.

## 고급 CSS 무시 사용 {#use-advanced-css-overrides}

시각적 사이드바를 통해 사용할 수 없는 스타일의 경우 편집기에서 직접 사용자 지정 CSS를 작성할 수 있습니다.

1. 구성 요소를 선택합니다.
1. 사이드바에서 **[!UICONTROL 고급]** 섹션을 확장합니다.
1. **[!UICONTROL CSS Override]** 영역에 사용자 지정 CSS 규칙을 씁니다. 이러한 규칙은 충돌이 있는 경우 시각적 컨트롤을 통해 설정된 모든 속성을 재정의합니다.

전체 CSS 속성 참조에 대해서는 [MDN 웹 문서 CSS 참조](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)를 참조하십시오.

### CSS 의사 요소 추가 {#add-css-pseudo-elements}

**[!UICONTROL 고급]** 섹션도 `::before` 및 `::after`과(와) 같은 CSS 의사 요소를 지원합니다. 이를 통해 양식 구조를 수정하지 않고 구성 요소 주위에 콘텐츠 또는 장식용 스타일을 삽입할 수 있습니다. 예를 들어 textbox 구성 요소 앞에 시각적 표시기를 추가하려면 다음을 수행합니다.

1. 구성 요소를 선택합니다(예: `CMP Textbox`).
1. **[!UICONTROL 고급]** 섹션을 확장합니다.
1. `::before` 의사 요소 필드에 다음과 같은 CSS 속성을 추가합니다.

   ```css
   color: #B10DC9;
   ```

   ![CSS 이전](/help/forms/assets/custom-theme-before-css.png)

1. `::after` 의사 요소 필드에 다음과 같은 CSS 속성을 추가합니다.

   ```css
   color: #006400;
   ```

   ![CSS 이후](/help/forms/assets/custom-theme-after-css.png)


이러한 의사 요소는 표준 CSS 동작을 따릅니다. 전체 참조에 대해서는 [MDN CSS 의사 요소](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)를 참조하십시오.

## 모범 사례 {#best-practices}

* **정확한 타겟팅을 위해 선택기 패널 사용**: 필드 레이블이나 긴 설명과 같은 중첩된 요소의 스타일을 지정할 때 캔버스를 클릭하지 않고 왼쪽의 선택기 패널을 사용하십시오. 이렇게 하면 적절한 특수성을 가진 올바른 CSS 선택기가 생성됩니다.
* **다른 테마의 자산을 사용하지 마십시오**: 테마를 편집할 때 다른 테마의 자산(예: 이미지)을 찾아보고 추가하지 마십시오. 소스 테마를 이동하거나 삭제하면 현재 테마가 중단됩니다.
* **컨테이너 패널 레이아웃 너비를 변경하지 마십시오**: 컨테이너 패널에 고정 너비를 지정하면 컨테이너 패널이 정적이며 다른 화면 크기에 적응하지 못합니다.

## 추가 참조 {#see-also}

{{see-also}}