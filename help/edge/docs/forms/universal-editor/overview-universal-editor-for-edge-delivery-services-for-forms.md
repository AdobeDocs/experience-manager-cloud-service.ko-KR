---
title: Forms용 Edge Delivery Services용 범용 편집기
description: Forms용 Edge Delivery Services용 범용 편집기를 사용하여 적응형 양식을 만듭니다.
feature: Edge Delivery Services
role: Admin, Developer
exl-id: d711e0d1-a2fc-4aa6-af87-6e77a7bc5d2e
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 100%

---


# Forms용 Edge Delivery Services용 범용 편집기

범용 편집기는 간단하고, 시각적이며, 직관적인 WYSIWYG(What You See Is What You Get) 인터페이스를 제공함으로써 Adobe Edge Delivery Services용 양식 만들기에 혁신을 일으켰습니다. 콘텐츠 제작자와 양식 작성자를 위해 설계되었으며, 기존 양식 작성 프로세스의 복잡성을 제거하여 기술 전문가가 아닌 사용자도 쉽게 액세스할 수 있습니다.

범용 편집기를 사용하면 텍스트 필드, 체크박스, 라디오 버튼과 같은 사전 설치된 구성 요소를 활용하여 반응형 및 대화형 양식을 빠르게 디자인할 수 있습니다. 강력한 기능 세트는 동적 규칙, 원활한 데이터 통합, 고급 개인화를 지원하여 모든 양식을 필요에 맞게 조정할 수 있도록 해 줍니다.

가벼운 클라이언트측 렌더링을 관리하든, 브라우저 간 호환성을 보장하든, 엄격한 접근성 표준을 준수하든, 범용 편집기는 양식을 만들고 관리하기 위한 간소화된 솔루션을 제공합니다.

![범용 편집기](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center}

## Forms용 Edge Delivery Services용 범용 편집기의 주요 기능



| ![WYSIWYG 인터페이스](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg) | ![규칙 편집기](/help/edge/docs/forms/universal-editor/assets/rule-editor.svg) | ![제출 액션](/help/edge/docs/forms/universal-editor/assets/submit-actions.svg) |
|:-------------:|:-------------:|:-------------:|
| [**WYSIWYG 인터페이스**](/help/edge/docs/forms/universal-editor/universal-editor-user-interface.md) | [**규칙 편집기**](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) | [**제출 액션**](/help/edge/docs/forms/universal-editor/submit-action.md) |
| 범용 편집기는 사전 설치된 구성 요소 라이브러리, 반응형 디자인, 템플릿 기반 작성, 실시간 필드 수정 기능을 갖춘 WYSIWYG 인터페이스를 통해 양식 디자인을 제공합니다. | 규칙 편집기를 사용하면 사용자는 이벤트 기반 규칙, 즉각적인 유효성 검사, 간단한 JavaScript 및 JSON을 통한 오류 처리를 사용하여 동적 양식 상호 작용을 만들 수 있습니다. | 제출 액션은 백엔드 통합, 조건부 제출 논리, 보안 엔드포인트 및 전처리기를 지원하여 제출 워크플로를 간소화합니다. |

| ![게시/게시 취소](/help/edge/docs/forms/universal-editor/assets/publish-unpublish.svg) | ![반응형 모드](/help/edge/docs/forms/universal-editor/assets/responsive.svg) | ![사용자 정의 구성 요소](/help/edge/docs/forms/universal-editor/assets/custom-components.svg) |
|:-------------:|:-------------:|:-------------:|
| [**게시/게시 취소**](/help/edge/docs/forms/universal-editor/publish-forms.md) | [**반응형 모드**](/help/edge/docs/forms/universal-editor/responsive-layout.md) | [**사용자 정의 구성 요소**](/help/edge/docs/forms/universal-editor/create-custom-component.md) |
| 양식의 가시성을 쉽게 제어해 보십시오. 몇 번의 클릭만으로 편집기에서 직접 양식을 게시하거나 게시 취소할 수 있습니다. | 다양한 디바이스(데스크탑, 태블릿 및 모바일)에서 원활하게 적응되는 양식을 디자인합니다. 반응형 모드를 사용하면 다양한 화면 크기에 맞게 양식을 미리 보고 테스트할 수 있습니다. | 사용자 정의 구성 요소를 사용하면 개발자는 특정 조직의 사용 사례에 맞는 고유한 요소를 만들어 양식 기능을 확장할 수 있습니다. |

| ![스타일링](/help/edge/docs/forms/universal-editor/assets/personalization.svg) | ![미리 채우기 서비스](/help/edge/docs/forms/universal-editor/assets/prefill-services.svg) | ![A/B 테스트](/help/edge/docs/forms/universal-editor/assets/experimentation-ab-testing.svg) |
|:-------------:|:-------------:|:-------------:|
| [**스타일링**](/help/edge/docs/forms/universal-editor/style-theme-forms.md) | **[사전 작성 양식](/help/edge/docs/forms/universal-editor/prefill-form.md)** | [**A/B 테스트**](https://github.com/adobe/aem-experimentation/blob/main/documentation/experiments.md) |
| CSS를 사용하여 스타일링하면 개발자는 양식 요소의 외관을 사용자 정의하고 웹 사이트의 미적 기준에 맞는 시각적으로 매력적인 디자인을 만들 수 있습니다. | 미리 채우기 서비스를 사용하면 다양한 소스에서 얻은 관련 사용자 데이터로 양식 필드가 자동으로 채워지므로 수동 입력을 줄이고 사용자 경험을 개선할 수 있습니다. | A/B 테스트를 통해 조직은 다양한 양식 디자인, 레이아웃 및 기능을 실험하여 가장 효과적인 변형을 파악할 수 있습니다. |

| ![분석 및 추적](/help/edge/docs/forms/universal-editor/assets/analyticsandtracking.svg) | ![양식 조각](/help/edge/docs/forms/universal-editor/assets/form-fragments.svg) | ![데이터 바인딩](/help/edge/docs/forms/universal-editor/assets/data-binding.svg) |
|:-------------:|:-------------:|:-------------:|
| [**분석 및 추적**](https://www.aem.live/developer/martech-integration) | **양식 조각** (곧 제공 예정) | [**데이터 바인딩**](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) |
| 기본 제공 분석 및 추적 기능을 통해 사용자 행동, 양식 상호 작용 및 제출률에 대한 인사이트를 얻고 데이터 기반 양식 최적화를 실현할 수 있습니다. | 양식 조각을 사용하면 자주 사용하는 섹션을 한 번만 생성하고 여러 양식에서 재사용할 수 있어 일관성을 유지하고 유지 관리 작업을 줄일 수 있습니다. | 데이터 바인딩을 통해 양식 필드와 백엔드 데이터 소스를 직접 연결할 수 있으며, 이를 통해 실시간 업데이트와 고급 데이터 매핑이 지원됩니다. |

| ![CAPTCHA](/help/edge/docs/forms/universal-editor/assets/captcha.svg) | ![양식 임베드](/help/edge/docs/forms/universal-editor/assets/embedding-forms.svg) | ![감사 구성](/help/edge/docs/forms/universal-editor/assets/thank-you.svg) |
|:-------------:|:-------------:|:-------------:|
| [**CAPTCHA**](/help/edge/docs/forms/universal-editor/recaptcha-forms.md) | **양식 임베드** (곧 제공 예정) | [**감사 구성**](/help/edge/docs/forms/universal-editor/submit-action.md#show-a-custom-thank-you-message-on-adaptive-form-submission-submit-action-message-ue) |
| reCAPTCHA를 사용하여 자동화된 봇으로부터 양식을 보호하고, 안전하고 신뢰할 수 있는 데이터 수집을 보장합니다. | 범용 편집기의 기본 제공 임베드 구성 요소를 사용하여 Edge Delivery Services Sites 페이지에 양식을 직접 임베드할 수 있습니다. | 양식을 성공적으로 제출한 후 사용자에게 표시되는 승인 메시지 또는 페이지를 간편하게 사용자 정의합니다. |



## 사전 설치된 양식 구성 요소

범용 편집기는 기본적으로 다음과 같은 양식 구성 요소를 제공합니다.

<table>
  <thead>
    <tr>
      <th></th> 
      <th>양식 구성 요소</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="22"><img src="/help/edge/docs/forms/universal-editor/assets/adaptive-forms-components.png" alt="양식 구성 요소" style="width: 100%;"></td> 
      <td><b>아코디언</b></td>
      <td>콘텐츠 구성을 위한 축소 가능한 패널 구조</td>
    </tr>
    <tr>
      <td><b>버튼</b></td>
      <td>탐색 또는 사용자 정의 논리와 같은 액션에 대한 대화형 요소를 추가합니다.</td>
    </tr>
    <tr>
      <td><b>Captcha</b></td>
      <td>Google reCaptcha 또는 HCaptcha를 사용하여 사용자가 사람임을 확인하는 작업을 완료하도록 요구함으로써 스팸을 방지할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>확인란</b></td>
      <td>사용자가 체크박스를 구성할 수 있도록 허용합니다.</td>
    </tr>
    <tr>
      <td><b>체크박스 그룹</b></td>
      <td>사용자가 그룹에서 여러 옵션을 선택할 수 있도록 허용합니다.</td>
    </tr>
    <tr>
      <td><b>날짜 선택기</b></td>
      <td>사용자가 캘린더 인터페이스를 사용하여 날짜를 선택할 수 있도록 허용합니다.</td>
    </tr>
    <tr>
      <td><b>드롭다운 목록</b></td>
      <td>미리 정의된 목록에서 단일 또는 다중 선택 옵션을 제공합니다.</td>
    </tr>
    <tr>
      <td><b>이메일</b></td>
      <td>기본 포맷 유효성 검사를 통해 이메일 주소를 캡처합니다.</td>
    </tr>
    <tr>
      <td><b>첨부 파일</b></td>
      <td>문서, 이미지 또는 기타 파일 유형을 업로드할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>양식 조각</b></td>
      <td>주소 필드나 연락처 세부 정보와 같은 섹션을 위한 재사용 가능한 양식 구성 요소입니다.</td>
    </tr>
    <tr>
      <td><b>이미지</b></td>
      <td>양식 내 이미지 업로드 및 표시를 지원합니다.</td>
    </tr>
    <tr>
      <td><b>양식</b></td>
      <td>경고, 추가 정보 또는 확인에 자주 사용되는 팝업 대화 상자를 표시합니다.</td>
    </tr>
    <tr>
      <td><b>숫자 필드</b></td>
      <td>숫자 입력을 캡처하여 숫자나 범위의 유효성을 검사할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>패널</b></td>
      <td>확장/축소 가능한 패널로 양식 섹션을 구성합니다.</td>
    </tr>
    <tr>
      <td><b>라디오 버튼</b></td>
      <td>옵션 그룹에서 단일 선택이 가능하도록 합니다.</td>
    </tr>
    <tr>
      <td><b>등급</b></td>
      <td>사용자가 별점을 매길 수 있도록 허용합니다.</td>
    </tr>
    <tr>
      <td><b>재설정 버튼</b></td>
      <td>양식 필드를 기본 상태로 재설정합니다.</td>
    </tr>
    <tr>
      <td><b>제출 버튼</b></td>
      <td>양식 제출을 트리거하고 정의된 워크플로를 시작합니다.</td>
    </tr>
    <tr>
      <td><b>전화번호 필드</b></td>
      <td>국가별 서식으로 전화번호를 캡처합니다.</td>
    </tr>
    <tr>
      <td><b>텍스트</b></td>
      <td>체크박스를 통해 법적 약관을 표시하고 사용자 동의를 수집하는 전용 섹션을 제공합니다.</td>
    </tr>
    <tr>
      <td><b>텍스트 필드</b></td>
      <td>이름이나 이메일 주소와 같은 한 줄 입력을 캡처합니다.</td>
    </tr>
    <tr>
      <td><b>마법사</b></td>
      <td>여러 부분으로 구성된 양식 작성 과정을 단계별로 안내합니다.</td>
    </tr>
  </tbody>
</table>

## 자주 묻는 질문 (FAQ)

**Q. 누가 범용 편집기를 사용할 수 있습니까?**
범용 편집기는 다음을 포함한 광범위한 대상자를 위해 설계되었습니다.

- 시각적으로 매력적인 양식을 작성하고자 하는 콘텐츠 제작자
- 고급 사용자 정의 및 통합 기능이 필요한 개발자
- 확장 가능하고 안전하며 규정을 준수하는 양식 솔루션을 원하는 조직

**Q: 범용 편집기로 만든 양식을 기존 시스템에 통합할 수 있습니까?**
예. 범용 편집기는 백엔드 시스템과의 원활한 데이터 바인딩을 지원하여 실시간 업데이트와 고급 데이터 매핑을 가능하게 합니다. 작업 관리를 위한 Adobe Workfront와 같은 도구와도 통합되며 데이터 제출 워크플로를 위한 안전한 엔드포인트를 지원합니다.

**Q: 양식 구성요소를 사용자 정의할 수 있습니까?**
예. 범용 편집기를 사용하면 개발자가 조직의 특정 요구 사항에 맞는 사용자 정의 구성 요소를 만들 수 있습니다. 또한 UI 확장 기능 및 사용자 정의 워크플로를 통해 편집기의 기능을 확장할 수도 있습니다.

**Q: 양식에서 어떤 종류의 분석을 얻을 수 있습니까?**
범용 편집기에는 사용자 상호 작용, 양식 제출률, 전환 지표를 모니터링하는 기본 제공 분석 및 추적 도구가 포함되어 있습니다. 이러한 인사이트는 양식을 최적화하여 더 나은 성과를 얻는 데 도움이 됩니다.

**Q: 범용 편집기는 접근성을 어떻게 처리합니까?**
범용 편집기는 WCAG(웹 콘텐츠 접근성 지침)를 포함한 접근성 표준을 엄격히 준수하여 설계되었습니다. 이를 통해 장애가 있는 사용자도 양식을 사용할 수 있어 포괄적인 경험이 가능합니다.






