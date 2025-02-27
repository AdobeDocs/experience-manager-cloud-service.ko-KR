---
title: 범용 편집기 이해 - 반응형 모드
description: 이 문서에서는 작성 중에 모양과 느낌을 시각화하기 위해 유니버설 편집기에서 다양한 에뮬레이터를 사용하여 양식을 미리 보는 방법에 대해 설명합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 8f5b4d863ab469c44b4c221eab1fb128706b45c7
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 2%

---

# WYSIWYG 작성의 반응형 모드

<span class="preview"> 이 기능은 조기 액세스 프로그램을 통해 사용할 수 있습니다. 액세스를 요청하려면 공식 주소에서 GitHub 조직 이름 및 저장소 이름으로 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>(으)로 이메일을 보내십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc이면 조직 이름은 adobe이고 저장소 이름은 abc입니다.</span>


[범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)를 사용하면 작성 중에 양식의 모양과 느낌을 확인할 수 있도록 다양한 에뮬레이터로 Edge Delivery Services Forms을 미리 볼 수 있습니다.

반응형 모드를 통해 개발자는 데스크탑, 태블릿 및 모바일 장치를 포함하여 다양한 화면 크기에 자동으로 적응하는 레이아웃을 디자인할 수 있습니다. 범용 편집기는 데스크탑, 태블릿 및 모바일 장치용 에뮬레이터를 지원합니다. 화면 크기에 따라 높이와 너비를 설정하고 다음 작업을 수행할 수 있습니다.

* 방향 설정
* 너비 및 높이 지정
* 방향 변경

## 다른 디바이스에 대해 응답형 모드로 Forms 미리 보기

유니버설 편집기는 화면 오른쪽 맨 위에 있는 **에뮬레이터** 아이콘을 제공하므로 다양한 장치 크기에서 페이지를 미리 보고 반응형 디자인의 동작을 테스트하여 사용자 환경을 개선할 수 있습니다.

유니버설 편집기에서 다양한 화면 크기에서 양식을 렌더링하는 방법을 보려면 다음 단계를 수행하십시오.

1. 편집할 양식을 범용 편집기에서 엽니다.
1. 범용 편집기 도구 모음에서 사용할 수 있는 ![에뮬레이터 아이콘](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%}을 선택하고 에뮬레이터 아이콘을 클릭하여 옵션을 표시합니다.

   ![응답형 모드](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

1. 선택한 장치의 범용 편집기에서 양식을 에뮬레이션하려면 데스크탑, 태블릿, 모바일과 같은 옵션을 선택합니다.

   ![응답형 모드](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png){width=40%,height=40%}

   기본적으로 편집기는 브라우저에 의해 높이 및 너비가 자동으로 결정된 데스크탑 레이아웃으로 열립니다. 또는 모바일 또는 태블릿 디바이스에서 양식을 에뮬레이션할 수 있습니다. 사용자 지정 장치의 화면 너비와 높이를 사용자 지정할 수도 있습니다.

범용 편집기는 다양한 장치에서 양식을 미리 볼 수 있는 다양한 에뮬레이터를 제공합니다. 아래 표에는 사용 가능한 에뮬레이터 유형과 해당 디바이스 표현이 나와 있습니다.

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">에뮬레이터 유형</th>
        <th style="width: 80%">장치 이미지</th>
    </tr>
    <tr>
        <td style="width: 20%">데스크탑</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="데스크톱 에뮬레이터" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">태블릿</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="태블릿 에뮬레이터" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">모바일</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="모바일 에뮬레이터" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">사용자 지정 장치</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="사용자 지정 장치 에뮬레이터" style="width: auto; height: auto"></td>
    </tr>
</table>

다른 장치에서 양식을 미리 볼 때 **화면 회전기** 아이콘을 사용하여 세로 방향과 가로 방향 간을 전환할 수 있습니다. 이는 개발자가 반응형 디자인이 다양한 디바이스에서 화면 회전에 어떻게 적응하는지를 테스트하는 데 도움이 됩니다.

유니버설 편집기는 다양한 양식 레이아웃을 지원합니다. 다른 레이아웃을 살펴보려면 [레이아웃 기능](#layout-capabilities) 섹션을 참조하세요.

## 레이아웃 기능

범용 편집기를 사용하면 최종 사용자에게 동적 경험을 제공하는 사용하기 쉬운 양식을 만들 수 있습니다. 양식 레이아웃은 항목이나 구성 요소가 양식에 표시되는 방식을 제어합니다.

유니버설 편집기는 폼에 대해 다음 유형의 레이아웃을 지원합니다.
* [패널 레이아웃](#panel-layout)
* [마법사 레이아웃](#wizard-layout)
* [어코디언 레이아웃](#accordion-layout)

### 패널 레이아웃

패널 레이아웃은 해당 컨텐츠를 더 쉽게 탐색하고 찾을 수 있도록 관련 필드를 구성하는 데 유용합니다. 패널 레이아웃은 양식의 개별 섹션 또는 패널 내에 양식 구성 요소를 정렬합니다.

![패널 레이아웃](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

[패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel)를 사용하여 양식에 패널 레이아웃을 추가할 수 있습니다. 패널 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) 문서를 참조하십시오.

### 마법사 레이아웃


마법사 레이아웃은 복잡한 양식을 별도의 단계로 나누어 단순화하는 데 도움이 됩니다. 각 단계는 프로세스의 다른 부분을 나타내며 사용자는 **다음** 및 **뒤로** 단추를 사용하여 단계를 순차적으로 탐색합니다. 마법사 레이아웃을 사용하여 여러 섹션이나 단계가 포함된 양식을 만들 수 있습니다.

![마법사 레이아웃](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

[마법사 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard)를 사용하여 양식에 마법사 레이아웃을 추가할 수 있습니다. 마법사 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [마법사 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) 문서를 참조하십시오.

### 어코디언 레이아웃

아코디언 레이아웃은 적응형 양식의 축소 가능한 섹션이나 패널에 콘텐츠를 표시합니다. 섹션을 확장하면 내의 컨텐츠가 표시되고 다른 섹션은 축소된 상태로 유지됩니다. 이 레이아웃은 대량의 정보를 컴팩트한 형식으로 표시하는 데 이상적입니다.

![아코디언 레이아웃](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

[아코디언 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion)를 사용하여 양식에 아코디언 레이아웃을 추가할 수 있습니다. 아코디언 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [아코디언 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) 문서를 참조하십시오.

### 올바른 레이아웃을 선택하는 방법

사용자 경험과 양식 기능을 최적화하려면 올바른 레이아웃을 선택하는 것이 중요합니다. 이 표는 사용 가능한 다양한 레이아웃 옵션을 이해하는 데 도움이 되며 특정 요구 사항 및 사용 사례에 따라 가장 적합한 레이아웃을 선택할 수 있도록 안내합니다.

| 기능 | 패널 레이아웃 | 마법사 레이아웃 | 어코디언 레이아웃 |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **목적** | 관련 콘텐츠를 개별 섹션으로 그룹화 | 여러 단계 프로세스 또는 양식을 안내합니다. | 콘텐츠를 축소 가능한 섹션으로 구성 |
| **구조** | 개별 섹션 | 순차적 단계/페이지 | 축소 가능한 패널/섹션 |
| **탐색** | 탐색할 패널 헤더를 클릭합니다 | - 앞으로: &quot;다음&quot; 단추<br>- 뒤로: &quot;뒤로&quot; 단추<br>- 선택적 건너뛸 단계 | 섹션을 확장/축소하려면 헤더를 클릭하십시오. |
| **사용자 환경** | 대량의 컨텐츠를 관리 가능한 방식으로 구성 | 단계별 지침을 통해 과중한 업무 부담 감소 | 확장/축소된 단면이 있는 컴팩트한 보기 |
| **사용 사례** | 분류된 섹션이 있는 복잡한 양식 | 프로세스 설정, 복잡한 양식 | FAQ, 설정 메뉴, 세부 콘텐츠 섹션 |

## 추가 참조

{{universal-editor-see-also}}
