---
title: 액세스 가능한 적응형 Forms을 만드는 방법
description: AEM Forms은 액세스 가능한 적응형 Forms을 만들 수 있는 도구를 제공하며 접근성 표준을 준수하도록 도와줍니다.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: 3b5247fa-decb-40eb-a629-6d834976d33c
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '2018'
ht-degree: 0%

---

# 액세스 가능한 적응형 Forms 만들기{#creating-accessible-adaptive-forms}

## 소개 {#introduction}

액세스 가능한 양식은 특별한 요구 사항이 있는 사용자를 포함하여 모든 사용자가 사용할 수 있는 양식입니다. 적응형 Forms에는 다양한 능력을 가진 사용자의 사용성을 향상시키는 몇 가지 기능이 포함되어 있습니다. 적응형 Forms에 접근성을 구축하면 가능한 가장 광범위한 콘텐츠 대상자를 사용할 수 있을 뿐만 아니라, 접근성 표준 준수가 요구되는 지역에서 문서를 제공할 때 반드시 필요합니다. [!DNL AEM Forms] 양식 개발자가 접근성 표준을 준수하도록 지원합니다.

작성자는 적응형 양식을 작성하는 동안 액세스 가능한 적응형 양식을 만들려면 다음 사항을 고려해야 합니다.

* ANDI(Accessible Name and Description Inspector) 접근성 테스트 도구로 양식 확인
* 양식 컨트롤에 적절한 레이블 제공
* 이미지에 해당하는 텍스트 제공
* 충분한 색상 대비 제공
* 양식 컨트롤을 키보드에 액세스할 수 있는지 확인합니다.

## 전제 조건

액세스 가능한 적응형 양식을 만들려면 **ANDI(Accessible Name and Description Inspector)**&#x200B;와(과) **접근성 관련 문제를 해결하기 위해 개발된 적응형 양식 테마**&#x200B;와(과) 같은 접근성 도구가 필요합니다.

### 접근성 테스트 도구 다운로드 및 설치

ANDI(Accessible Name and Description Inspector) 도구를 사용하면 웹 콘텐츠의 접근성 규정 준수 관련 문제를 식별하고 해결할 수 있습니다. 국토안보부의 Trusted Tester v5 지침에 따라 권장되는 도구입니다. 미국 사회보장행정부가 웹 콘텐츠&#x200B;의 Section 508 준수 여부를 확인하기 위해 개발하였다. 도구는 다음과 같습니다.

* 웹 페이지에서 접근성 문제&#x200B;을 감지하는 데 도움이 됩니다.
* 접근성을 개선하기 위한 제안 사항을 제공합니다&#x200B;.
* 키보드 접근성 및 색상 대비 문제 감지
* 표준에 따라 화면 판독기 콘텐츠를 명확하게 식별합니다.

ANDI는 모든 주요 인터넷 브라우저에서 작동합니다. 도구를 구성하고 사용하는 자세한 지침은 [ANDI의 설명서](https://www.ssa.gov/accessibility/andi/help/install.html)를 참조하세요.

### Ultramarine에서 액세스할 수 있는 테마 다운로드 및 설치

Ultramarine-Accessible 테마는 참조 테마입니다. 적응형 양식의 색상 대비 및 기타 접근성 관련 문제를 해결하는 방법을 보여 주는 데 도움이 됩니다. Adobe은 조직에서 승인한 스타일을 기반으로 프로덕션 환경에 대한 사용자 지정 테마를 만들 것을 권장합니다. 테마를 AEM 인스턴스에 업로드하려면 다음 단계를 수행하십시오.

1. 테마 패키지를 다운로드합니다.
1. AEM 인스턴스의 **[!UICONTROL Experience Manager]** > **[!UICONTROL 탐색]** ![탐색](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Forms]**(으)로 이동합니다.
1. **[!UICONTROL 만들기]** > **[!UICONTROL 파일 업로드]**&#x200B;를 선택합니다. x Ultramarine-Accessible-Theme.zip 파일을 선택하여 업로드합니다. 테마를 AEM 인스턴스에 업로드합니다.

## 적응형 양식에 액세스

키보드 탐색, 색상 대비, 이미지에 의미 있는 대체 텍스트 및 적응형 양식에 액세스할 수 있도록 하는 양식 컨트롤에 대한 적절한 레이블의 네 가지 주요 측면에 중점을 두어야 합니다. 다음 단계를 수행하여 기존 적응형 Forms에 액세스할 수 있도록 합니다.

### 1. 액세스 가능한 테마를 적용하고 추가 수정을 수행합니다

Ultramarine에서 액세스할 수 있는 테마를 기존 적응형 양식에 적용합니다. 테마를 적용하려면:

1. 편집할 적응형 양식을 엽니다.
1. 구성 요소를 선택하고 상위 아이콘을 선택합니다. 컨텍스트 메뉴에서 **[!UICONTROL 적응형 양식 컨테이너]**&#x200B;를 선택한 다음 구성 아이콘을 선택합니다.
1. 속성 브라우저에서 Ultramarine에 액세스할 수 있는 테마를 선택하고 **[!UICONTROL 저장]** 아이콘을 선택합니다.
1. 브라우저 창을 새로 고칩니다. 테마는 적응형 양식에 적용됩니다.

액세스 가능한 테마를 적용한 후 아래에 나열된 추가 수정 사항을 수행합니다. 액세스 가능한 테마에서 다루는 접근성 수정 사항과 더불어 수정 사항이 있습니다.

1. 로고 이미지에 대한 의미 있는 대체 텍스트를 적응형 양식에 추가합니다.

   적응형 양식 템플릿의 머리글 및 바닥글 구성 요소에서 이미지에 대한 의미 있는 대체 텍스트를 제공합니다. 템플릿을 수정하고 이 템플릿을 사용하여 적응형 양식을 만들면 적응형 Forms은 템플릿의 머리글 및 바닥글에 적용된 모든 접근성 관련 수정 사항을 상속합니다.  기존 적응형 양식의 경우 적응형 양식 수준에서 변경합니다. 적응형 양식 템플릿에 대한 변경 사항은 기존 적응형 양식으로 자동 전달되지 않습니다.

1. 양식 이름이 포함된 제목 구성 요소를 적응형 양식에 추가합니다. 양식 디자인에서 회사 이름을 지정하는 경우 회사 이름에 대한 별도의 제목 구성 요소도 추가하십시오.

   대부분의 접근성 도구는 웹 페이지의 구조를 이해하는 데 도움이 되도록 콘텐츠의 계층 구조에 대해 사용자에게 알려 줍니다. 적응형 양식의 조직 이름 및 양식 이름 텍스트에 대해 서로 다른 머리글 수준을 설정하여 이러한 텍스트에 계층 구조를 제공합니다. 또한 적절한 제목 수준으로 각 패널 및 섹션 앞에 텍스트 구성 요소를 사용하여 계층을 만듭니다.

   ![헤더 스타일을 적용하는 방법](assets/apply-style.gif)

1. 텍스트의 가시성과 가독성을 높이기 위해 접근성 표준에 따라 적절한 대비를 사용하도록 바닥글 배경색을 변경합니다. ANDI를 사용하여 양식에서 색상 대비 문제를 찾을 수 있습니다. 또한 매우 작은 글꼴을 사용하지 마십시오. 작은 글꼴은 읽기 어렵습니다.

1. 기존 적응형 양식의 스위치 및 이미지 선택 구성 요소를 선택(라디오) 구성 요소로 바꿉니다.

1. 기존 적응형 양식의 숫자 스텝퍼 구성 요소를 숫자 상자 구성 요소로 바꿉니다.

1. 날짜 입력 필드를 날짜 선택 필드로 바꿉니다.

1. 날짜 선택기 구성 요소에 대한 표시, 유효성 검사 및 편집 패턴을 설정합니다. 또한 사용자 지정 유효성 검사 오류 메시지를 설정합니다. 예를 들어 잘못된 날짜를 지정했습니다. 올바른 날짜 형식은 YYYY-MM-DD입니다.

1. 날짜 선택기 구성 요소에 대한 사용자 지정 액세스 가능성 텍스트를 설정합니다. 예를 들어 생년월일을 입력합니다. 화면 판독기는 이러한 사용자 지정 접근성 텍스트를 읽습니다.

1. 적응형 양식 구성 요소에 대해 긴 설명 대신 짧은 설명을 사용하십시오. 자세한 설명은 도움말 단추를 추가합니다. 적응형 양식에 도움말 버튼이 없는지 확인합니다.

1. 표의 모든 읽기 전용 셀에 사용자 지정 접근성 텍스트를 추가합니다. 또한 표의 모든 읽기 전용 셀을 비활성화합니다.

1. 적응형 양식에 스크리블 서명 필드가 있는 경우 제거합니다. 원활한 디지털 서명 환경을 위해 [!DNL Adobe Sign]을(를) 사용하도록 적응형 양식을 구성하십시오.

### 2. 양식 컨트롤에 적절한 레이블 제공 {#provide-proper-labels-for-form-controls}

구성 요소의 레이블이나 제목은 양식 구성 요소가 나타내는 것을 식별합니다. 예를 들어 &quot;이름&quot;이라는 텍스트는 텍스트 필드에 이름을 입력해야 한다고 사용자에게 알려 줍니다. 화면 판독기에서 액세스할 수 있도록 레이블은 양식 구성 요소와 프로그래밍 방식으로 연결됩니다. 또는 추가 접근성 정보를 사용하여 양식 컨트롤을 구성할 수도 있습니다.

화면 판독기에서 인식하는 레이블은 반드시 시각적 캡션과 같을 필요는 없습니다. 경우에 따라 컨트롤의 목적에 대해 보다 구체적으로 설명해야 할 수도 있습니다. 양식의 각 필드 개체에 대해 액세스 가능성 옵션을 사용하여 화면 판독기에서 특정 양식 필드를 식별하기 위해 발표하는 내용을 지정할 수 있습니다.

[액세스 가능성] 옵션을 사용하려면 다음 단계를 수행합니다.

1. 구성 요소를 선택하고 ![cmpr](assets/cmppr.png)을(를) 선택합니다.
1. 사이드바에서 **[!UICONTROL 접근성]**&#x200B;을 클릭하여 원하는 접근성 옵션을 선택합니다.

### 양식 구성 요소의 접근성 옵션 {#accessibility-options-in-form-components}

![양식 구성 요소의 접근성 옵션](assets/accessibility-options.png)

**사용자 지정 텍스트** 양식 작성자가 액세스 가능성 옵션 사용자 지정 텍스트 필드에 내용을 제공합니다. 화면 판독기와 같은 보조 기술은 이 사용자 지정 텍스트를 사용합니다. 제목 설정을 사용하는 것이 대부분의 시나리오에서 가장 좋은 옵션입니다. 제목 또는 간단한 설명이 불가능한 경우에만 사용자 정의 화면 Reader 텍스트를 생성하는 것이 좋습니다.

**간단한 설명** 대부분의 구성 요소에 대해서는 사용자가 포인터를 구성 요소 위에 두면 런타임에 간단한 설명이 나타납니다. 도움말 콘텐츠 옵션 아래의 짧은 설명 필드에서 이 옵션을 설정할 수 있습니다.

**제목** 이 옵션을 사용하여 [!DNL AEM Forms]에서 화면 판독기 텍스트로 양식 필드에 연결된 시각적 레이블을 사용할 수 있도록 합니다.

**이름** 바인딩 탭의 이름 필드에 값을 지정할 수 있습니다. 이름에는 공백을 사용할 수 없습니다.

**없음** 없음을 선택하면 게시된 양식에 양식 개체의 이름이 없습니다. None은 양식 컨트롤에 권장되는 설정이 아닙니다.

>[!NOTE]
>
>* 라디오 단추와 확인란에는 사용자 지정 텍스트와 제목, 즉 두 가지 접근성 옵션만 사용할 수 있습니다.
>* XFA 기반 적응형 Forms의 경우 액세스 가능성 옵션은 XDP에 설정된 액세스 가능성 옵션에서 상속됩니다. XDP의 도구 팁은 간단한 설명에 매핑되고 캡션은 제목에 매핑됩니다. 다른 옵션은 그대로 작동합니다.

### 3. 이미지에 해당하는 텍스트 입력 {#provide-text-equivalents-for-images}

이미지는 일부 사용자의 이해력을 개선하는 데 도움이 될 수 있습니다. 그러나 화면 판독기를 사용하는 사용자의 경우 이미지는 양식의 접근성을 낮춥니다. 이미지를 사용하도록 선택하는 경우 모든 이미지에 대한 텍스트 설명을 입력합니다.

텍스트가 양식에서 개체 및 그 목적을 설명하도록 하십시오. 이미지가 나타나면 화면 판독기가 이 대체 텍스트를 읽습니다. 이미지에는 항상 대체 텍스트를 지정해야 합니다.

이미지 구성 요소를 선택하고 ![cmpr](assets/cmppr.png)을(를) 선택합니다. 사이드바의 속성 아래에서 이미지에 대한 대체 텍스트를 지정합니다.

![이미지의 대체 텍스트](assets/image-properties.png)

### 4. 충분한 색상 대비 제공 {#provide-sufficient-color-contrast}

접근성 디자인에는 색상 사용에 대한 추가 지침이 고려되어야 합니다. 양식 작성자는 다양한 양식 구성 요소를 강조 표시하여 색상을 사용하여 양식의 모양을 향상시킬 수 있습니다. 그러나 색상을 부적절하게 사용하면 다른 능력을 가진 사람이 읽기 어렵거나 불가능한 형태가 될 수 있습니다.

시각 장애가 있는 사용자는 텍스트와 배경 간의 높은 대비를 통해 디지털 콘텐츠를 읽을 수 있습니다. 충분한 대비가 없으면 일부 사용자의 경우 양식이 불가능하지는 않지만 읽기 어려워질 수 있습니다.

기본 글꼴과 배경색(흰색 배경에 검정색 콘텐츠)을 사용하는 것이 좋습니다. 기본 색상을 변경하는 경우 밝은 배경색에서 어두운 전경색을 선택하거나 반대로 선택합니다.

<!-- See [Creating custom themes for Adaptive Forms](creating-custom-adaptive-form-themes.md), for more information about changing the color contrast and theme for the Adaptive Forms. -->

### 5. 양식 컨트롤을 키보드에 액세스할 수 있는지 확인합니다 {#ensure-that-form-controls-are-keyboard-accessible}

키보드나 이와 동등한 입력 장치만 사용하여 액세스 가능한 양식을 완전히 채울 수 있습니다. 거동이 불편하거나 시력이 저하된 사용자는 키보드를 사용할 수 밖에 없으며 마우스를 사용할 수 있는 많은 사용자는 키보드 입력을 선호합니다. 다양한 입력 방법을 허용하면 액세스 가능한 양식을 만들 수 있을 뿐만 아니라 모든 사용자의 기본 설정에 더 적합한 양식을 만들 수 있습니다.

[!DNL AEM Forms]에서 다음 키보드 단축키를 사용할 수 있습니다.

| 작업 | 키보드 단축키 |
|---|---|
| 양식을 통해 커서를 앞으로 이동 | 탭 |
| 양식을 통해 커서를 뒤로 이동 | Shift+Tab |
| 다음 패널로 이동 | Alt+오른쪽 화살표 |
| 이전 패널로 이동 | Alt+왼쪽 화살표 |
| 양식의 채워진 데이터 재설정 | Alt+R |
| 양식 제출 | Alt+S |

또한 응용 Forms의 **[!UICONTROL 날짜 선택기]** 구성 요소에서 사용할 수 있는 다양한 키보드 단축키가 있습니다. 바로 가기 키를 사용하려면 **[!UICONTROL 날짜 선택기]** 구성 요소를 선택하고 ![구성](assets/configure-icon.svg)을 선택하여 속성을 엽니다. **[!UICONTROL 패턴]** 섹션에서 **[!UICONTROL 유형]** 및 **[!UICONTROL 패턴]** 드롭다운 목록을 사용하여 표시 패턴을 선택합니다. 속성을 저장하여 **[!UICONTROL 날짜 선택기]** 구성 요소에 바로 가기 키를 사용할 수 있도록 합니다.

적응형 Forms에서 날짜 선택기 구성 요소에 사용할 수 있는 키보드 단축키는 다음과 같습니다.

| 작업 | 키보드 단축키 |
|---|---|
| <ul><li>탭 포커스에서 달력 아이콘을 강조 표시할 때 날짜 선택기 구성 요소 옵션을 표시합니다</li><li>탭 포커스에서 옵션을 강조 표시할 때 클릭 이벤트를 수행합니다</li> | Space 또는 Enter |
| 날짜 선택기 구성 요소 옵션 숨기기 | Esc |
| <ul><li>날짜 선택기 구성 요소에서 사용할 수 있는 옵션을 통해 커서를 앞으로 이동합니다.</li><li>날짜 입력 필드가 활성 상태일 때 달력 아이콘에 탭 포커스 설정</li> | 탭 |
| 날짜 선택기 구성 요소에서 사용할 수 있는 옵션을 통해 커서를 뒤로 이동합니다. | Shift+Tab |
| <ul><li>탭 포커스에서 날짜 입력 필드를 강조 표시하면 날짜 선택기 구성 요소 옵션을 표시합니다</li><li>날짜 선택기 구성 요소에서 사용할 수 있는 달력에서 커서를 아래로 이동합니다.</li> | 아래쪽 화살표 |
| 날짜 선택기 구성 요소에서 사용할 수 있는 달력에서 커서를 위로 이동합니다. | 위쪽 화살표 |
| 날짜 선택기 구성 요소에서 사용할 수 있는 달력에서 커서를 뒤로 이동합니다. | 왼쪽 화살표 |
| 날짜 선택기 구성 요소에서 사용할 수 있는 달력에서 커서를 앞으로 이동합니다. | 오른쪽 화살표 |
| 달력에서 오른쪽 및 왼쪽 탐색 화살표 사이에 사용할 수 있는 캡션에 대한 작업을 수행합니다 | Shift + 위쪽 화살표 |
| 캘린더에서 사용할 수 있는 오른쪽 탐색 화살표 아이콘 ![오른쪽 화살표](assets/right-navigation-icon.svg)에 대한 작업을 수행합니다. | Shift + 왼쪽 화살표 |
| 캘린더에서 사용할 수 있는 왼쪽 탐색 화살표 아이콘 ![왼쪽 화살표](assets/left-navigation-icon.svg)에 대한 작업을 수행합니다. | Shift + 오른쪽 화살표 |

## 접근성 도구를 사용하여 남아 있는 접근성 문제를 찾아보십시오

ANDI(Accessible Name and Description Inspector)를 사용하면 적응형 양식에서 접근성 규정 준수 관련 문제를 식별하고 해결할 수 있습니다. ANDI 도구를 사용하여 적응형 양식에서 접근성 문제를 찾으려면 다음을 수행하십시오.

1. 미리 보기 모드에서 적응형 양식을 엽니다.
1. 책갈피가 표시된 ANDI 도구 아이콘을 클릭합니다. ANDI 도구는 적응형 양식을 분석하고 접근성 문제를 표시합니다. 도구 사용 방법에 대한 자세한 내용은 [ANDI의 설명서](https://www.ssa.gov/accessibility/andi/help/howtouse.html)를 참조하세요.
1. ANDI에서 보고한 문제를 검토하고 수정합니다.
