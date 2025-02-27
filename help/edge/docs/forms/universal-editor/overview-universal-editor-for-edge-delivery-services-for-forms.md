---
title: Forms용 Edge Delivery Services 유니버설 편집기
description: Forms용 Edge Delivery Services 범용 편집기를 사용하여 적응형 Forms을 만듭니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: d711e0d1-a2fc-4aa6-af87-6e77a7bc5d2e
source-git-commit: 744f505c8e97b6ca6947b685ddb1eba41b370cfa
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 72%

---


# Forms용 Edge Delivery Services 유니버설 편집기

<span class="preview"> 이 기능은 조기 액세스 프로그램을 통해 사용할 수 있습니다. 액세스를 요청하려면 공식 주소에서 GitHub 조직 이름 및 저장소 이름으로 <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>(으)로 이메일을 보내십시오. 예를 들어 저장소 URL이 https://github.com/adobe/abc이면 조직 이름은 adobe이고 저장소 이름은 abc입니다.</span>

범용 편집기는 간단하고, 시각적이며, 직관적인 What You See Is What You Get(WYSIWYG) 인터페이스를 제공하여 Adobe Edge Delivery Services에 대한 양식 작성에 혁신을 줍니다. 콘텐츠 제작자와 양식 작성자를 위해 설계되었으며, 기존 양식 작성 프로세스의 복잡성을 제거하여 기술 전문가가 아닌 사용자도 쉽게 액세스할 수 있습니다.

범용 편집기를 사용하면 텍스트 필드, 체크박스, 라디오 버튼과 같은 사전 설치된 구성 요소를 활용하여 반응형 및 대화형 양식을 빠르게 디자인할 수 있습니다. 강력한 기능 세트는 동적 규칙, 원활한 데이터 통합, 고급 개인화를 지원하여 모든 양식을 필요에 맞게 조정할 수 있도록 해 줍니다.

가벼운 클라이언트측 렌더링을 관리하든, 브라우저 간 호환성을 보장하든, 엄격한 접근성 표준을 준수하든, 범용 편집기는 양식을 만들고 관리하기 위한 간소화된 솔루션을 제공합니다.

![범용 편집기](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center} -->

## Forms용 Edge Delivery Services 유니버설 편집기의 주요 기능



다음은 동일한 너비 카드가 있는 레이아웃입니다(고정 너비 열 사용).

| ![WYSIWYG 인터페이스](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg) | ![규칙 편집기](/help/edge/docs/forms/universal-editor/assets/rule-editor.svg) | ![작업 제출](/help/edge/docs/forms/universal-editor/assets/submit-actions.svg) |
|:-------------:|:-------------:|:-------------:|
| [**WYSIWYG 인터페이스**](/help/edge/docs/forms/universal-editor/universal-editor-user-interface.md) | [**규칙 편집기**](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) | [**작업 제출**](/help/edge/docs/forms/universal-editor/submit-action.md) |
| 범용 편집기는 사전 설치된 구성 요소 라이브러리, 반응형 디자인, 템플릿 기반 작성, 실시간 필드 수정 기능을 갖춘 WYSIWYG 인터페이스를 통해 양식 디자인을 제공합니다. | 규칙 편집기를 사용하면 사용자는 이벤트 기반 규칙, 즉각적인 유효성 검사, 간단한 JavaScript 및 JSON을 통한 오류 처리를 사용하여 동적 양식 상호 작용을 만들 수 있습니다. | 제출 액션은 백엔드 통합, 조건부 제출 논리, 보안 엔드포인트 및 전처리기를 지원하여 제출 워크플로를 간소화합니다. |

| ![게시/게시 취소](/help/edge/docs/forms/universal-editor/assets/publish-unpublish.svg) | ![응답형 모드](/help/edge/docs/forms/universal-editor/assets/responsive.svg) | ![사용자 지정 구성 요소](/help/edge/docs/forms/universal-editor/assets/custom-components.svg) |
|:-------------:|:-------------:|:-------------:|
| [**게시/게시 취소**](/help/edge/docs/forms/universal-editor/publish-forms.md) | [**응답형 모드**](/help/edge/docs/forms/universal-editor/responsive-layout.md) | [**사용자 지정 구성 요소**](/help/edge/docs/forms/universal-editor/create-custom-component.md) |
| 몇 번의 클릭만으로 편집기에서 직접 양식을 게시하거나 게시 취소하여 양식의 가시성을 쉽게 제어할 수 있습니다. | 다양한 디바이스(데스크탑, 태블릿 및 모바일)에서 원활하게 적응되는 양식을 디자인합니다. 반응형 모드를 사용하면 다양한 화면 크기에 맞게 양식을 미리 보고 테스트할 수 있습니다. | 사용자 정의 구성 요소를 사용하면 개발자는 특정 조직의 사용 사례에 맞는 고유한 요소를 만들어 양식 기능을 확장할 수 있습니다. |

| ![스타일링](/help/edge/docs/forms/universal-editor/assets/personalization.svg) | ![미리 채우기 서비스](/help/edge/docs/forms/universal-editor/assets/prefill-services.svg) | ![A/B 테스트](/help/edge/docs/forms/universal-editor/assets/experimentation-ab-testing.svg) |
|:-------------:|:-------------:|:-------------:|
| [**스타일링**](/help/edge/docs/forms/universal-editor/style-theme-forms.md) | **미리 채우기 서비스**(준비 중) | [**A/B 테스트**](https://github.com/adobe/aem-experimentation/blob/main/documentation/experiments.md) |
| CSS를 사용한 스타일링을 통해 개발자는 양식 요소의 모양을 사용자 정의하고 웹 사이트 미학에 맞는 시각적으로 매력적인 디자인을 만들 수 있습니다. | 미리 채우기 서비스를 사용하면 다양한 소스에서 얻은 관련 사용자 데이터로 양식 필드가 자동으로 채워지므로 수동 입력을 줄이고 사용자 경험을 개선할 수 있습니다. | A/B 테스트를 통해 조직은 다양한 양식 디자인, 레이아웃 및 기능을 실험하여 가장 성과가 좋은 변형을 식별할 수 있습니다. |

| ![분석 및 추적](/help/edge/docs/forms/universal-editor/assets/analyticsandtracking.svg) | ![작업 관리](/help/edge/docs/forms/universal-editor/assets/adobe-workfront.svg) | ![데이터 바인딩](/help/edge/docs/forms/universal-editor/assets/data-binding.svg) |
|:-------------:|:-------------:|:-------------:|
| [**분석 및 추적**](https://www.aem.live/developer/martech-integration) | **작업 관리**(준비 중) | **데이터 바인딩**(준비 중) |
| 기본 제공 분석 및 추적 기능을 통해 사용자 행동, 양식 상호 작용 및 제출률에 대한 인사이트를 얻고 데이터 기반 양식 최적화를 실현할 수 있습니다. | Adobe Workfront와 통합하면 팀에서 양식 작성 및 유지 관리 작업을 관리하여 워크플로를 간소화할 수 있습니다. | 데이터 바인딩을 사용하면 양식 필드와 백엔드 데이터 소스 간에 직접 연결할 수 있으므로 실시간 업데이트와 고급 데이터 매핑을 지원합니다. |

| ![CAPTCHA](/help/edge/docs/forms/universal-editor/assets/captcha.svg) | ![Forms 포함](/help/edge/docs/forms/universal-editor/assets/embedding-forms.svg) | ![감사 인사 구성](/help/edge/docs/forms/universal-editor/assets/thank-you.svg) |
|:-------------:|:-------------:|:-------------:|
| [**CAPTCHA**](/help/edge/docs/forms/universal-editor/recaptcha-forms.md) | **Forms 포함** | [**감사 인사 구성**](/help/edge/docs/forms/universal-editor/submit-action.md#show-a-custom-thank-you-message-on-adaptive-form-submission-submit-action-message-ue) |
| reCAPTCHA를 사용하여 자동화된 봇으로부터 양식을 보호하여 안전하고 신뢰할 수 있는 데이터 수집을 보장합니다. | 범용 편집기의 내장된 임베디드 구성 요소를 사용하여 Edge Delivery Services Sites 페이지에 양식을 직접 임베드합니다. | 양식을 성공적으로 제출한 후 사용자에게 표시되는 승인 메시지 또는 페이지를 간편하게 사용자 정의합니다. |


<!-- ![Universal Editor](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg)  **WYSIWYG interface for Form creation**: Universal Editor provides a WYSIWYG interface for form design. It provides pre-built component library, responsive design support, and template-based form creation. You can instantly add or remove form fields and modify field properties (like label, data binding, validation). You can also plugin custom form components to Universal Editor.


* **Rule editor**: The rule editor stands out as a powerful mechanism for creating sophisticated form interactions. It supports event-driven rules, instant validation, and error handling through lightweight JavaScript and JSON-based definitions. This allows developers to implement complex form logic, such as conditional field visibility, automatic calculations, and dynamic form behaviour without extensive coding.

* **Submit actions**: Submit Actions enable form submission workflows. These actions provide comprehensive backend integration options, supporting protocols like REST API. The system allows you configure data pre-processors for automatic data transformation, conditional submission logic based on form field values, and secure endpoint connections. Organizations can define complex submission rules that validate data, and manage form responses with granular control.

* **Pre-fill services:** Pre-fill Services enhance user experience by intelligently populating form fields with relevant data. These services connect to various data sources, including user profiles, browser local storage, and external databases. The mechanism supports dynamic data population, enabling automatic completion of form fields based on contextual information. Users benefit from reduced manual data entry, while administrators gain flexibility in configuring pre-fill rules across different form types and scenarios. The pre-fill functionality adapts to different authentication methods, including session-based approaches and token-based systems, ensuring both convenience and security.

* **Data binding capabilities**: Data binding in the Universal Editor enables direct, dynamic connections between form fields and backend data sources. This feature allows real-time synchronization of form data, supporting complex data mapping scenarios. The system supports transforming form inputs into structured database records with minimal configuration. Advanced mapping supports nested data structures, allowing complex form designs to interact seamlessly with intricate data models.

* **Internationalization/localization capabilities**: Internationalization support ensures global accessibility, with multi-language rendering, right-to-left language compatibility, and locale-specific formatting.

* **Analytics and tracking mechanisms**: The built-in analytics and tracking mechanisms provide comprehensive insights into form interactions, submission rates, and user behavior, enabling continuous optimization of form design and performance. 

* **Experimentation (A/B Testing)**: The Universal Editor supports experimentation by allowing organizations to run A/B tests on form designs to identify the best-performing layouts or features.

* **Task Management via Adobe Workfront**: Integration with Adobe Workfront allows teams to manage tasks related to form creation and maintenance, ensuring streamlined collaboration and efficient workflows.

* **Editor Customization via UI Extension**: Developers can extend the functionality of the Universal Editor through UI extensions, enabling tailored solutions that fit specific organizational needs. -->

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

<!-- * Footer: Adds a footer section for consistent design or additional information.
* Form Container: Wraps all form elements and manages overall form properties.
* Header: Adds a header section for form titles, branding, or instructions.-->
<!-- * 
* Prefillable Fields: Automatically populates form fields with data from predefined sources such as user profiles or APIs. 

* Switches/Toggle Buttons: Provides binary on/off choices for user input.


* Title: Adds a text-based heading or label to improve form clarity and organization.


In-addtion to pre-built form components, the Universal editor also provides support for:

* **Embedding Forms in Another Webpage**: The Universal Editor supports embedding forms directly into Edge Deliver Services Sites pages. This can be done using the embed component provided out of the box.

* **Validation Messages**: Validation messages provide real-time feedback to users when they enter incorrect or incomplete data. Features include:
    * Dynamic Error Display: Instantly alerts users to errors, such as invalid email addresses or missing required fields.
    * Customizable Messages: Allows form authors to define user-friendly error texts.
    * Rule-Based Validation: Supports advanced validation logic, such as checking dependencies between fields or implementing conditional rules.

* **Hidden Fields**: Hidden fields store data invisibly within the form, often for backend processing or prefilled values. Use cases include:
    * Passing contextual information (e.g., user ID or session data) to the backend without displaying it to users.
    * Capturing metadata like timestamps or tracking IDs.
    * Hidden fields are not visible to end-users but can be prefilled, updated dynamically, or used in workflows.

* **Custom Components**: Custom components allow developers to extend the functionality of forms by creating specialized or third-party integrations. Features include:
    * Flexibility: Developers can design unique form elements tailored to specific use cases.
    * Third-Party Integration: Embed widgets or tools like payment gateways, analytics trackers, or AI-driven input fields.
    * Seamless Compatibility: Custom components can integrate with the Universal Editor's drag-and-drop interface and existing features like data binding or validation.

* **Thank you Configuration**: Customize the acknowledgment message or page shown after form submission.
-->


## 온보딩

범용 편집기와 규칙 편집기 같은 고급 기능을 활성화하려면 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 문의하십시오. Adobe 팀은 귀하가 양식 작성 경험을 혁신하도록 지원하고 있습니다.

## 자주 묻는 질문 (FAQ)

**Q. 누가 범용 편집기를 사용할 수 있습니까?**
범용 편집기는 다음을 포함한 광범위한 대상자를 위해 설계되었습니다.

* 시각적으로 매력적인 양식을 작성하고자 하는 콘텐츠 제작자
* 고급 사용자 정의 및 통합 기능이 필요한 개발자
* 확장 가능하고 안전하며 규정을 준수하는 양식 솔루션을 원하는 조직

**Q: 범용 편집기로 만든 양식을 기존 시스템에 통합할 수 있습니까?**
예. 범용 편집기는 백엔드 시스템과의 원활한 데이터 바인딩을 지원하여 실시간 업데이트와 고급 데이터 매핑을 가능하게 합니다. 작업 관리를 위한 Adobe Workfront와 같은 도구와도 통합되며 데이터 제출 워크플로를 위한 안전한 엔드포인트를 지원합니다.

**Q: 양식 구성요소를 사용자 정의할 수 있습니까?**
예. 범용 편집기를 사용하면 개발자가 조직의 특정 요구 사항에 맞는 사용자 정의 구성 요소를 만들 수 있습니다. 또한 UI 확장 기능 및 사용자 정의 워크플로를 통해 편집기의 기능을 확장할 수도 있습니다.

**Q: 범용 편집기는 접근성을 어떻게 처리합니까?**
범용 편집기는 WCAG(웹 콘텐츠 접근성 지침)를 포함한 접근성 표준을 엄격히 준수하여 설계되었습니다. 이를 통해 장애가 있는 사용자도 양식을 사용할 수 있어 포괄적인 경험이 가능합니다.

**Q: 양식에서 어떤 종류의 분석을 얻을 수 있습니까?**
범용 편집기에는 사용자 상호 작용, 양식 제출률, 전환 지표를 모니터링하는 기본 제공 분석 및 추적 도구가 포함되어 있습니다. 이러한 인사이트는 양식을 최적화하여 더 나은 성과를 얻는 데 도움이 됩니다.


## 양식 만들기 시작

{{universal-editor-see-also}}

