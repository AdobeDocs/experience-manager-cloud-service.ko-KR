---
title: 범용 편집기 - 반응형 모드 이해
description: 이 문서에서는 범용 편집기에서 다양한 에뮬레이터를 사용하여 양식을 미리 보고, 작성 중에 양식이 어떻게 보이는지 시각적으로 확인하는 방법을 설명합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 99%

---


# WYSIWYG 작성 환경에서의 반응형 모드

<span class="preview"> <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features">시험판 채널</a>을 통해 사용할 수 있는 시험판 기능입니다. </span>

## 반응형 양식 소개

오늘날의 다중 디바이스 환경에서 양식은 데스크탑 모니터부터 스마트폰까지 모든 화면 크기에서 잘 보이고 원활하게 작동해야 합니다. 범용 편집기의 반응형 모드를 사용하면 다양한 디바이스 크기에서 양식을 미리 보고 테스트하여 최적의 사용자 경험을 제공할 수 있습니다.

[범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)를 사용하면 다양한 화면 크기에 자동으로 맞춰지는 양식을 만들어 사용하는 디바이스에 관계없이 최적의 사용자 경험을 제공할 수 있습니다.

## 다양한 디바이스에 대한 반응형 모드에서 양식 미리보기

범용 편집기는 화면 오른쪽 상단에 **에뮬레이터** 아이콘을 제공하며, 이 아이콘을 통해 다양한 디바이스 크기에서 페이지를 미리 보고 반응형 디자인의 동작을 테스트하여 더 나은 사용자 경험을 제공할 수 있습니다.

반응형 모드에서 양식을 미리 보는 방법은 다음과 같습니다.

1. 편집을 위해 범용 편집기에서 양식을 엽니다.
2. 도구 모음에서 ![디바이스 미리보기 기호](/help/edge/docs/forms/universal-editor/assets/emulator.png){높이=2%, 폭=2%} 아이콘을 표시하는 에뮬레이터 아이콘을 클릭합니다.
3. 디바이스 형식을 선택합니다.
   - 데스크탑 (기본값)
   - 태블릿
   - 모바일
   - 사용자 정의 (폭과 높이 지정)

![다양한 디바이스에 대한 반응형 모드 옵션을 보여 주는 범용 편집기의 스크린샷](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

태블릿이나 모바일 디바이스에서 미리 볼 때 **화면 회전** 아이콘을 사용하여 세로 방향과 가로 방향을 전환할 수도 있습니다.

범용 편집기는 다양한 디바이스에서 양식을 미리 볼 수 있도록 다양한 에뮬레이터를 제공합니다. 아래 표는 사용 가능한 에뮬레이터 유형과 해당하는 디바이스 표현을 나열한 것입니다.

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">에뮬레이터 유형</th>
        <th style="width: 80%">디바이스 이미지</th>
    </tr>
    <tr>
        <td style="width: 20%">데스크탑</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="전체 폭 레이아웃을 표시하는 양식의 데스크탑 보기" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">태블릿</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="중간 폭 레이아웃으로 조정된 구성 요소를 포함한 양식의 태블릿 보기" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">모바일</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="좁은 레이아웃으로 구성 요소가 쌓인 형태의 양식의 모바일 보기" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">사용자 정의 디바이스</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="사용자가 지정한 크기로 양식을 표시하는 사용자 정의 디바이스 보기" style="width: auto; height: auto"></td>
    </tr>
</table>

## 레이아웃 기능

범용 편집기를 사용하면 최종 사용자에게 동적인 경험을 제공하는 사용하기 쉬운 양식을 만들 수 있습니다. 양식 레이아웃은 양식 내에서 항목이나 구성 요소가 표시되는 방식을 결정합니다.

범용 편집기는 다음과 같은 양식 레이아웃을 지원합니다.

- [패널 레이아웃](#panel-layout)
- [마법사 레이아웃](#wizard-layout)
- [아코디언 레이아웃](#accordion-layout)

### 패널 레이아웃

패널 레이아웃을 사용하면 관련 필드를 함께 그룹화하여 쉽게 탐색하고 원하는 콘텐츠를 빠르게 찾을 수 있습니다. 패널 레이아웃은 양식 내 구성 요소를 개별 섹션 또는 패널 내에 배치하여 정리된 형태로 표시합니다.

![양식 내 여러 개의 구분된 섹션을 표시하는 패널 레이아웃](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**예:** 입사지원서 양식에는 “개인 정보”, “학력”, “경력”, “참조”를 구분된 패널로 구분하여 사용할 수 있습니다.

**반응형 동작:** 작은 화면에서는 패널이 일반적으로 세로로 배열되어, 구분된 그룹을 유지하면서도 좁은 폭에 맞게 조정됩니다.

[패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel)를 사용하여 양식에 패널 레이아웃을 추가할 수 있습니다. 패널 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) 설명서를 참조하십시오.

### 마법사 레이아웃

마법사 레이아웃은 복잡한 양식을 여러 개의 구분된 단계로 나누어 단순화하는 데 도움이 됩니다. 각 단계는 프로세스의 다른 부분을 나타내며, 사용자는 보통 **다음** 및 **이전** 버튼을 사용하여 순차적으로 단계를 이동합니다. 여러 섹션이나 단계를 포함하는 양식을 만들기 위해 마법사 레이아웃을 사용할 수 있습니다.

![탐색 컨트롤이 있는 다단계 양식을 보여 주는 마법사 레이아웃](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**예:** 보험 청구 양식은 사고 세부 정보 제공, 증거 업로드, 개인 정보 입력, 제출 검토 단계를 안내하는 마법사를 사용할 수 있습니다.

**반응형 동작:** 모바일 디바이스에서는 마법사가 단계별 접근 방식을 유지하되 각 단계 내의 콘텐츠를 좁은 화면에 맞게 조정하며, 큰 화면에서 나란히 배치되던 스태킹 요소들이 세로로 배열됩니다.

양식에 마법사 레이아웃을 추가하려면 [마법사 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard)를 사용하십시오. 마법사 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [마법사 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) 설명서를 참조하십시오.

### 아코디언 레이아웃

아코디언 레이아웃은 적응형 양식에서 접을 수 있는 섹션이나 패널 형식으로 콘텐츠를 표시합니다. 섹션이 확장되면 그 안의 콘텐츠가 표시되고, 다른 섹션은 축소된 상태를 유지합니다. 이 레이아웃은 많은 양의 정보를 압축된 양식으로 표시하는 데 이상적입니다.

![양식에서 확장 가능한 섹션을 보여 주는 아코디언 레이아웃](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**예:** 제품 구성 양식은 “기본 옵션”, “고급 기능”, “액세서리”, “결제 계획” 등의 아코디언 섹션을 사용하여 사용자가 한 번에 한 가지 측면에 집중할 수 있도록 합니다.

**반응형 동작:** 아코디언은 모바일 디바이스에서 특히 효과적입니다. 확장된 섹션만 표시되어 세로 공간을 절약하므로 작은 화면에 이상적입니다.

양식에 아코디언 레이아웃을 추가하려면 [아코디언 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion)를 사용하십시오. 아코디언 구성 요소의 다양한 속성을 구성하는 방법에 대한 자세한 지침은 [아코디언 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) 설명서를 참조하십시오.

### 올바른 레이아웃을 선택하려면 어떻게 해야 합니까?

사용자 경험과 양식 기능을 최적화하기 위해 올바른 레이아웃을 선택하는 것이 중요합니다. 아래 표는 사용 가능한 다양한 레이아웃 옵션을 이해하고, 특정 요구 사항과 사용 사례에 따라 가장 적합한 레이아웃을 선택하는 데 도움이 됩니다.

| 기능 | 패널 레이아웃 | 마법사 레이아웃 | 아코디언 레이아웃 |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **용도** | 관련 콘텐츠를 구분된 섹션으로 그룹화 | 다단계 프로세스 또는 양식을 안내 | 콘텐츠를 접을 수 있는 섹션으로 구성 |
| **구조** | 구분된 섹션 | 순차적 단계/페이지 | 접을 수 있는 패널/섹션 |
| **탐색** | 패널 헤더를 클릭하여 탐색 | - 앞으로: “다음” 버튼<br>- 뒤로: “뒤로” 버튼<br>- 선택적으로 단계를 건너뛸 수 있음 | 헤더를 클릭하여 섹션을 확장하거나 축소 |
| **사용자 경험** | 관리 가능한 방식으로 많은 콘텐츠를 정리 | 단계별 안내로 부담감 감소 | 확장/축소 가능한 섹션을 활용한 압축 보기 |
| **사용 사례** | 복잡한 양식의 분류된 섹션 | 설정 프로세스, 복잡한 양식 | FAQ, 설정 메뉴, 상세 콘텐츠 섹션 |
| **모바일에 가장 적합** | 중간 - 패널이 세로로 배열됨 | 우수함 - 현재 단계에 집중할 수 있도록 유지 | 매우 우수함 - 확장/축소 가능한 섹션을 활용하여 공간을 절약 |

## 반응형 양식에 대한 모범 사례

양식이 모든 디바이스에서 최적의 사용자 경험을 제공하도록 다음 모범 사례를 따르십시오.

1. **모바일을 먼저 고려한 디자인:** 먼저 모바일 디바이스에 맞춰 양식을 디자인한 다음 더 큰 화면에 맞게 개선하십시오. 이 접근 방식은 핵심 기능이 가장 작은 화면에서도 작동하도록 보장합니다.

2. **적절한 필드 유형 사용:** 터치 디바이스에서 잘 작동하는 필드 유형을 선택하십시오.
   - 옵션이 많은 경우 라디오 버튼 대신 드롭다운 사용
   - 터치 입력에 적합한 날짜 선택기 사용
   - 버튼과 터치 대상 크기를 최소 44px x 44px로 유지

3. **더 작은 화면을 위해 간소화:**
   - 모바일 디바이스에서 한 행에 표시할 필드 수를 줄이기
   - 선택 항목을 “더 보기” 옵션 뒤에 숨기는 방안 고려
   - 모바일에서 복잡한 양식을 여러 단계로 분할

4. **철저히 테스트:** 항상 실제 디바이스에서 양식을 테스트하거나 범용 편집기의 에뮬레이터 모드를 사용하여 양식이 화면 크기에 상관없이 제대로 작동하는지 확인하십시오.

5. **로딩 시간 고려:** 특히 연결 속도가 느린 모바일 사용자를 위해 이미지 크기를 최적화하고 필요한 리소스를 최소화합니다.

## 반응형 양식 문제 해결

| 문제 | 가능한 원인 | 솔루션 |
|-------|---------------|----------|
| 양식이 모바일 디바이스에서 잘려 보임 | 고정 폭 설정 또는 오버플로 문제 발생 | 픽셀 대신 상대 단위(%, rem)를 사용하고 overflow:hidden 속성 확인 |
| 터치 요소와의 상호작용이 어려움 | 터치 대상이 너무 작거나 너무 가까이 배치됨 | 버튼 및 입력 필드 크기를 최소 44px x 44px로 설정하고 대화형 요소 간 간격 추가 |
| 소형 화면에서 콘텐츠가 넘쳐 보임 | 작은 화면에 대한 반응형 규칙이 없음 | 미디어 쿼리 또는 반응형 클래스를 추가하여 다양한 화면 크기를 위해 레이아웃 조정 |
| 모바일 디바이스에서 양식이 느림 | 이미지 크기가 크거나 스크립트가 과도하게 사용됨 | 이미지를 최적화하고 JavaScript를 최소화하며 비필수 요소에 대해 지연 로딩을 적용 |
| 에뮬레이터와 실제 디바이스에서 다르게 표시됨 | 브라우저별 렌더링 차이 또는 디바이스별 변형 발생 | 가능한 경우 에뮬레이터뿐만 아니라 실제 디바이스에서 테스트 |

## 추가 참조

{#see-more-eds-forms}
