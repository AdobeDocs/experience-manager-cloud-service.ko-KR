---
title: 범용 편집기 이해 - 반응형 모드
description: 이 문서에서는 작성 중에 모양과 느낌을 시각화하기 위해 유니버설 편집기에서 다양한 에뮬레이터를 사용하여 양식을 미리 보는 방법에 대해 설명합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 9127c58a72dc4942312907f9e8f0cdcc8de9aa4b
workflow-type: tm+mt
source-wordcount: '1285'
ht-degree: 1%

---


# WYSIWYG 작성의 반응형 모드

<span class="preview"> 이 기능은 조기 액세스 프로그램을 통해 사용할 수 있습니다. 액세스를 요청하려면 공식 주소에서 GitHub 조직 이름과 저장소 이름이 포함된 이메일을 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>(으)로 보내십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc이면 조직 이름은 adobe이고 저장소 이름은 abc입니다.</span>

## 반응형 Forms 소개

오늘날의 멀티 디바이스 환경에서는 데스크탑 모니터에서 스마트폰에 이르기까지 모든 크기의 화면에서 폼이 멋진 모양과 기능을 발휘해야 합니다. 범용 편집기의 응답형 모드를 사용하면 작성 프로세스 중에 다양한 디바이스 크기에서 양식을 미리 보고 테스트할 수 있으므로 이 작업을 수행할 수 있습니다.

[범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)를 사용하면 다양한 화면 크기에 자동으로 적용되는 양식을 만들 수 있으므로 사용 중인 장치에 관계없이 최적의 사용자 환경을 제공합니다.

## 다른 디바이스에 대해 응답형 모드로 Forms 미리 보기

유니버설 편집기는 화면 오른쪽 맨 위에 있는 **에뮬레이터** 아이콘을 제공하므로 다양한 장치 크기에서 페이지를 미리 보고 반응형 디자인의 동작을 테스트하여 사용자 환경을 개선할 수 있습니다.

반응형 모드에서 양식을 미리 보려면 다음과 같이 하십시오.

1. 편집할 양식을 범용 편집기에서 엽니다.
2. 도구 모음에서 ![장치 미리 보기 기호를 표시하는 에뮬레이터 아이콘](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%}을 클릭합니다.
3. 장치 형식 선택:
   - 데스크탑(기본값)
   - 태블릿
   - 모바일
   - 사용자 지정(너비 및 높이 지정)

![다양한 장치에 대한 응답형 모드 옵션을 보여 주는 유니버설 편집기의 스크린샷](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

태블릿이나 모바일 장치에서 미리 볼 때 **화면 회전기** 아이콘을 사용하여 세로 방향과 가로 방향 간을 전환할 수도 있습니다.

범용 편집기는 다양한 장치에서 양식을 미리 볼 수 있는 다양한 에뮬레이터를 제공합니다. 아래 표에는 사용 가능한 에뮬레이터 유형과 해당 디바이스 표현이 나와 있습니다.

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">에뮬레이터 유형</th>
        <th style="width: 80%">장치 이미지</th>
    </tr>
    <tr>
        <td style="width: 20%">데스크탑</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="전체 너비 레이아웃을 보여 주는 양식의 데스크탑 보기" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">태블릿</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="조정된 구성 요소가 있는 중간 너비 레이아웃을 표시하는 양식의 태블릿 보기" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">모바일</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="스택 구성 요소가 있는 좁은 레이아웃을 표시하는 양식의 모바일 보기" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">사용자 지정 장치</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="사용자 지정 차원이 있는 양식의 사용자 지정 장치 보기" style="width: auto; height: auto"></td>
    </tr>
</table>

## 레이아웃 기능

범용 편집기를 사용하면 최종 사용자에게 동적 경험을 제공하는 사용하기 쉬운 양식을 만들 수 있습니다. 양식 레이아웃은 항목이나 구성 요소가 양식에 표시되는 방식을 제어합니다.

유니버설 편집기는 폼에 대해 다음 유형의 레이아웃을 지원합니다.

- [패널 레이아웃](#panel-layout)
- [마법사 레이아웃](#wizard-layout)
- [어코디언 레이아웃](#accordion-layout)

### 패널 레이아웃

패널 레이아웃은 해당 컨텐츠를 더 쉽게 탐색하고 찾을 수 있도록 관련 필드를 구성하는 데 유용합니다. 패널 레이아웃은 양식의 개별 섹션 또는 패널 내에 양식 구성 요소를 정렬합니다.

![양식 내에 여러 개의 개별 섹션을 표시하는 패널 레이아웃](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**예:** 작업 응용 프로그램 양식은 패널을 사용하여 &quot;개인 정보&quot;, &quot;교육&quot;, &quot;작업 경험&quot; 및 &quot;참조&quot;를 개별 섹션으로 구분할 수 있습니다.

**응답형 동작:** 더 작은 화면에서 패널은 일반적으로 세로로 스택되어 서로 다른 그룹화는 유지하면서 더 좁은 폭으로 조정됩니다.

[패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel)를 사용하여 양식에 패널 레이아웃을 추가할 수 있습니다. 패널 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) 문서를 참조하십시오.

### 마법사 레이아웃

마법사 레이아웃은 복잡한 양식을 서로 다른 단계로 나누어 단순화하는 데 도움이 됩니다. 각 단계는 프로세스의 다른 부분을 나타내며 사용자는 **다음** 및 **뒤로** 단추를 사용하여 단계를 순차적으로 탐색합니다. 마법사 레이아웃을 사용하여 여러 섹션이나 단계가 포함된 양식을 만들 수 있습니다.

![탐색 컨트롤이 있는 여러 단계 양식을 표시하는 마법사 레이아웃](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**예:** 보험 청구 양식에서는 마법사를 사용하여 문제 세부 정보를 제공하고, 증거를 업로드하고, 개인 정보를 입력하고, 제출 내용을 검토하는 과정을 안내할 수 있습니다.

**응답형 동작:** 모바일 장치에서 마법사는 단계별 접근 방식을 유지하지만 더 좁은 화면에 맞게 각 단계 내의 내용을 조정하며 더 큰 화면에 나란히 표시되는 요소를 스택합니다.

[마법사 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard)를 사용하여 양식에 마법사 레이아웃을 추가할 수 있습니다. 마법사 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [마법사 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) 문서를 참조하십시오.

### 어코디언 레이아웃

아코디언 레이아웃은 적응형 양식의 축소 가능한 섹션이나 패널에 콘텐츠를 표시합니다. 섹션을 확장하면 내의 컨텐츠가 표시되고 다른 섹션은 축소된 상태로 유지됩니다. 이 레이아웃은 대량의 정보를 컴팩트한 형식으로 표시하는 데 이상적입니다.

![양식의 확장 가능한 섹션을 표시하는 아코디언 레이아웃](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**예:** 제품 구성 양식에서는 &quot;기본 옵션&quot;, &quot;고급 기능&quot;, &quot;액세서리&quot; 및 &quot;결제 플랜&quot;에 대해 아코디언 섹션을 사용하여 한 번에 한 측면에 집중할 수 있습니다.

**반응형 동작:** 아코디언은 확장된 콘텐츠 섹션만 표시하여 자연스럽게 세로 공간을 절약하므로 작은 화면에 이상적입니다.

[아코디언 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion)를 사용하여 양식에 아코디언 레이아웃을 추가할 수 있습니다. 아코디언 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [아코디언 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) 문서를 참조하십시오.

### 올바른 레이아웃을 선택하는 방법

사용자 경험과 양식 기능을 최적화하려면 올바른 레이아웃을 선택하는 것이 중요합니다. 이 표는 사용 가능한 다양한 레이아웃 옵션을 이해하는 데 도움이 되며 특정 요구 사항 및 사용 사례에 따라 가장 적합한 레이아웃을 선택할 수 있도록 안내합니다.

| 기능 | 패널 레이아웃 | 마법사 레이아웃 | 어코디언 레이아웃 |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **목적** | 관련 콘텐츠를 개별 섹션으로 그룹화 | 여러 단계 프로세스 또는 양식을 안내합니다. | 콘텐츠를 축소 가능한 섹션으로 구성 |
| **구조** | 개별 섹션 | 순차적 단계/페이지 | 축소 가능한 패널/섹션 |
| **탐색** | 탐색할 패널 헤더를 클릭합니다 | - 앞으로: &quot;다음&quot; 단추<br>- 뒤로: &quot;뒤로&quot; 단추<br>- 선택적 건너뛸 단계 | 섹션을 확장/축소하려면 헤더를 클릭하십시오. |
| **사용자 환경** | 대량의 컨텐츠를 관리 가능한 방식으로 구성 | 단계별 지침을 통해 과중한 업무 부담 감소 | 확장/축소된 단면이 있는 컴팩트한 보기 |
| **사용 사례** | 분류된 섹션이 있는 복잡한 양식 | 프로세스 설정, 복잡한 양식 | FAQ, 설정 메뉴, 세부 콘텐츠 섹션 |
| **모바일에 최적** | 중재 - 패널이 세로로 스택 | 좋음 - 현재 단계에만 초점을 둡니다. | 우수 - 축소 가능한 섹션으로 공간 절약 |

## 반응형 Forms에 대한 우수 사례

양식이 모든 장치에서 최상의 경험을 제공하도록 하려면 다음 모범 사례를 따르십시오.

1. **먼저 모바일용 디자인:** 모바일 장치용 양식을 디자인한 다음 더 큰 화면을 위해 품질을 개선합니다. 이 접근 방식을 사용하면 가장 작은 화면에서 핵심 기능이 작동합니다.

2. **적절한 필드 형식 사용:** 터치 장치에서 잘 작동하는 필드 형식을 선택하십시오.
   - 옵션이 많을 때 라디오 버튼 대신 드롭다운을 사용합니다.
   - 터치 입력을 위해 설계된 날짜 선택기 사용
   - 버튼 및 터치 대상이 최소 44px x 44px 인지 확인합니다.

3. **작은 화면의 단순화:**
   - 모바일 장치에서 행당 더 적은 필드 표시
   - 옵션 필드를 &quot;자세히 표시&quot; 옵션 뒤에 숨기는 것이 좋습니다.
   - 복잡한 양식을 모바일에서 더 많은 단계로 나누기

4. **철저하게 테스트:** 양식을 항상 실제 장치에서 테스트하거나 유니버설 편집기의 에뮬레이터 모드를 사용하여 화면 크기에서 제대로 작동하는지 확인하십시오.

5. **로드 시간을 고려합니다.** 특히 연결 속도가 느린 모바일 사용자의 경우 이미지 크기를 최적화하고 필요한 리소스를 최소화하십시오.

## 응답형 Forms 문제 해결

| 문제 | 가능한 원인 | 솔루션 |
|-------|---------------|----------|
| 모바일 장치에서 양식이 잘린 상태로 표시됨 | 폭 설정 또는 오버플로 문제가 해결되었습니다. | 픽셀 대신 상대 단위(%, rem)를 사용하고 overflow:hidden 속성을 확인합니다. |
| 상호 작용이 어려운 터치 요소 | 터치 대상이 너무 작거나 서로 너무 가까움 | 단추/입력 크기를 최소 44px x 44px로 늘리고 대화형 요소 사이에 더 많은 공간을 추가합니다. |
| 작은 화면에서 컨텐츠 오버플로 | 작은 뷰포트에 대한 반응형 규칙 없음 | 미디어 쿼리 또는 반응형 클래스를 추가하여 다양한 화면 크기에 맞게 레이아웃 조정 |
| 모바일 장치에서 양식 너무 느림 | 큰 이미지 또는 과도한 스크립트 | 이미지를 최적화하고 JavaScript을 최소화하며 중요하지 않은 요소에 대한 지연 로드를 고려합니다 |
| 에뮬레이터와 실제 장치 간의 다른 모양 | 브라우저별 렌더링 또는 장치 변형 | 에뮬레이터뿐만 아니라 가능한 한 실제 디바이스에서 테스트합니다. |

## 추가 참조

{#see-more-eds-forms}
