---
title: Forms(EDS Forms 블록)용 Edge Delivery Services 유니버설 편집기
description: Forms Edge Delivery Services(EDS Forms 블록)용 범용 편집기를 사용하여 적응형 Forms을 만듭니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: 9d5950793f5b3e3c3d6229b9de9d5c020a164dd7
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 13%

---

# Forms(EDS Forms 블록)용 Edge Delivery Services 유니버설 편집기


범용 편집기는 콘텐츠 작성자와 양식 작성자가 양식을 쉽게 작성, 관리 및 편집할 수 있도록 설계되었습니다. EDS(Edge Delivery Services)에 초점을 맞춘 간단하고, 시각적이며, 효율적인 편집 환경을 제공합니다.

범용 편집기를 사용하면 텍스트 필드, 확인란 및 라디오 버튼과 같은 양식 요소를 사용하여 What You See Is What You Get(WYSIWYG) 인터페이스에서 양식을 만들 수 있습니다. WYSIWYG 접근 방식을 사용하면 기술 전문 지식이 없는 사람도 양식 만들기를 직관적이고 쉽게 수행할 수 있습니다.

유니버설 편집기는 특히 EDS(Edge Delivery Services)에 중점을 둡니다. 유니버설 편집기의 핵심 강점은 고급 양식 작성 기능, 동적 규칙 편집 및 다양한 데이터 소스와의 원활한 통합을 포함하는 강력한 기능 세트에 있습니다. 사용자는 사전 빌드된 구성 요소, 사용자 정의 가능한 템플릿 및 광범위한 양식 요소 라이브러리를 사용하여 응답형 양식을 신속하게 디자인할 수 있습니다.

![유니버설 편집기](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=50%, align-center}

Universal Editor의 기능은 가벼운 클라이언트측 렌더링, 브라우저 간 호환성 및 접근성 표준을 엄격하게 준수하도록 신중하게 설계되었습니다.

## EDS Forms 유니버설 편집기의 주요 기능


<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/generate-forms.svg" alt="WYSIWYG 인터페이스"> 
    <h3>WYSIWYG 인터페이스</h3>
    <p>유니버설 편집기는 사전 설치된 구성 요소 라이브러리, 반응형 디자인, 템플릿 기반 작성 및 실시간 필드 수정이 포함된 양식 디자인을 위한 WYSIWYG 인터페이스를 제공합니다.
 </p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/rule-editor.svg" alt="WYSIWYG 인터페이스" alt="규칙 편집기">
    <h3>규칙 편집기</h3>
    <p>규칙 편집기를 사용하면 이벤트 기반 규칙, 즉각적인 유효성 검사 및 경량 JavaScript 및 JSON을 통한 오류 처리를 사용하여 동적 양식 상호 작용을 만들 수 있습니다.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/responsive.svg" alt="WYSIWYG 인터페이스" alt="반응형 모드">
    <h3>반응형 모드 </h3>
    <p>장치(데스크탑, 태블릿 및 모바일) 간에 원활하게 적용되는 양식을 디자인합니다. 반응형 모드를 사용하여 다양한 화면 크기에 대한 양식을 미리 보고 테스트할 수 있습니다.</p>
  </div>
</div>
<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/personalization.svg" alt="WYSIWYG 인터페이스 alt=" WYSIWYG Interface"> 
    <h3>개인화</h3>
    <p>Personalization은 사용자 데이터를 사용하여 사용자 환경 설정에 따라 콘텐츠, 레이아웃 또는 옵션을 동적으로 조정하면서 맞춤 양식 경험을 제공합니다.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/experimentation-ab-testing.svg" alt="WYSIWYG 인터페이스" alt="규칙 편집기">
    <h3>A/B 테스트</h3>
    <p>A/B 테스트(실험)를 통해 조직에서는 다양한 양식 디자인, 레이아웃 및 기능을 실험하여 가장 성과가 좋은 변형을 식별할 수 있습니다.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/adobe-workfront.svg" alt="WYSIWYG 인터페이스" alt="Adobe Workfront과 통합">
    <h3> 작업 관리 </h3>
    <p>Adobe Workfront과의 통합을 통해 팀이 양식 생성 및 유지 관리를 위한 작업을 관리할 수 있으므로 간소화된 워크플로가 보장됩니다.</p>
  </div>
</div>

<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/prefill-services.svg" alt="WYSIWYG 인터페이스" alt="사전 채우기 서비스">
    <h3>사전 채우기 서비스</h3>
    <p>미리 채우기 서비스는 자동으로 양식 필드를 다양한 소스의 관련 사용자 데이터로 채워 수동 입력을 줄이고 사용자 경험을 향상시킵니다.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/data-binding.svg" alt="WYSIWYG 인터페이스" alt="데이터 바인딩">
    <h3>데이터 바인딩</h3>
    <p>데이터 바인딩을 사용하면 양식 필드와 백엔드 데이터 소스 간에 직접 연결할 수 있으므로 구조화된 컴플레인 데이터 스토리지에 대한 실시간 업데이트와 고급 데이터 매핑을 지원합니다.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/publish-unpublish.svg" alt="WYSIWYG 인터페이스" alt="다국어화/로컬라이제이션">
    <h3>게시/게시 취소</h3>
    <p>몇 번의 클릭만으로 양식을 게시 또는 게시 취소하여 가용성과 컨텐츠 업데이트를 동적으로 관리할 수 있으므로 양식의 가시성을 쉽게 제어할 수 있습니다.</p>
  </div>
</div>

<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/analyticsandtracking.svg" alt="WYSIWYG 인터페이스" alt="분석 및 추적">
    <h3>분석 및 추적</h3>
    <p>데이터 기반의 양식 최적화를 가능하게 하는 내장된 분석 및 추적을 통해 사용자 동작, 양식 상호 작용 및 제출률에 대한 통찰력을 얻으십시오.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/submit-actions.svg" alt="WYSIWYG 인터페이스" alt="동작 제출">
    <h3>동작 제출</h3>
    <p>제출 액션은 백엔드 통합, 조건부 제출 논리, 보안 끝점 및 사전 프로세서를 지원하여 제출 워크플로우를 간소화합니다.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/custom-components.svg" alt="WYSIWYG 인터페이스" alt="작업 관리">
    <h3>사용자 정의 구성 요소</h3>
    <p>사용자 지정 구성 요소를 사용하여 개발자는 특정 조직의 사용 사례에 맞게 조정된 고유한 요소를 만들어 양식 기능을 확장할 수 있습니다.</p>
  </div>
</div>

<div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/editor-customization.svg" alt="WYSIWYG 인터페이스" alt="편집기 사용자 지정">
    <h3>편집기 사용자 지정</h3>
    <p>개발자는 UI 확장을 통해 유니버설 편집기의 기능을 확장하여 특정 조직의 요구 사항에 맞는 맞춤형 솔루션을 제공할 수 있습니다.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/embedding-forms.svg" alt="WYSIWYG 인터페이스" alt="Forms 포함">
    <h3>Forms 포함</h3>
    <p>원활한 사용자 경험을 위해 유니버설 편집기의 내장 포함 구성 요소를 사용하여 양식을 Edge Delivery Services 사이트 페이지에 직접 임베드할 수 있습니다.</p>
  </div>
  <div class="card" style="display: inline-block; width: calc(30% - 20px); margin: 10px; border: 1px solid #ccc; padding: 10px; text-align: center;">
    <img src="/help/edge/docs/forms/universal-editor/assets/thank-you.svg" alt="WYSIWYG 인터페이스" alt="사용자 정의 구성 요소">
    <h3>감사 인사 구성</h3>
    <p>양식 제출 후 사용자에게 표시되는 승인 메시지 또는 페이지를 쉽게 사용자 지정할 수 있습니다.
    </p>
  </div>
</div>
</div>


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

## 사전 빌드된 양식 구성 요소

유니버설 편집기는 다음과 같은 양식 구성 요소를 즉시 제공합니다.

<table>
  <thead>
    <tr>
      <th>러블리</th> 
      <th>양식 구성 요소</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="22"><img src="/help/edge/docs/forms/universal-editor/assets/adaptive-forms-components.png" alt="양식 구성 요소" style="width: 100%;"></td> 
      <td><b>아코디언</b></td>
      <td>컨텐츠 구성을 위한 축소 가능한 패널 구조</td>
    </tr>
    <tr>
      <td><b>버튼</b></td>
      <td>탐색 또는 사용자 지정 논리와 같은 작업에 대화형 요소를 추가합니다.</td>
    </tr>
    <tr>
      <td><b>Captcha</b></td>
      <td>사용자가 Google reCaptcha 또는 HCaptcha를 사용하여 사람 확인 작업을 완료하도록 하여 스팸을 방지합니다.</td>
    </tr>
    <tr>
      <td><b>확인란</b></td>
      <td>사용자가 확인란을 구성할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>확인란 그룹</b></td>
      <td>사용자가 그룹에서 여러 옵션을 선택할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>날짜 선택기</b></td>
      <td>사용자가 달력 인터페이스를 사용하여 날짜를 선택할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>드롭다운 목록</b></td>
      <td>사전 정의된 목록에서 단일 또는 다중 선택 옵션을 제공합니다.</td>
    </tr>
    <tr>
      <td><b>이메일</b></td>
      <td>기본 형식 유효성 검사로 이메일 주소를 캡처합니다.</td>
    </tr>
    <tr>
      <td><b>첨부 파일</b></td>
      <td>문서, 이미지 또는 기타 파일 형식을 업로드할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>양식 조각</b></td>
      <td>주소 필드 또는 연락처 세부 정보와 같은 섹션에 재사용 가능한 양식 구성 요소.</td>
    </tr>
    <tr>
      <td><b>이미지</b></td>
      <td>양식 내에서 이미지 업로드 및 표시를 지원합니다.</td>
    </tr>
    <tr>
      <td><b>양식</b></td>
      <td>경고, 추가 정보 또는 확인에 자주 사용되는 팝업 대화 상자를 표시합니다.</td>
    </tr>
    <tr>
      <td><b>숫자 필드</b></td>
      <td>숫자 입력을 캡처하여 숫자 또는 범위의 유효성 검사를 허용합니다.</td>
    </tr>
    <tr>
      <td><b>패널</b></td>
      <td>확장/축소 가능한 패널로 양식 섹션을 구성합니다.</td>
    </tr>
    <tr>
      <td><b>라디오 단추</b></td>
      <td>옵션 그룹에서 한 항목을 선택할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>등급</b></td>
      <td>사용자가 별 기반 등급을 제공할 수 있습니다.</td>
    </tr>
    <tr>
      <td><b>재설정 버튼</b></td>
      <td>양식 필드를 기본 상태로 재설정합니다.</td>
    </tr>
    <tr>
      <td><b>제출 버튼</b></td>
      <td>양식 제출을 트리거하고 정의된 워크플로우를 시작합니다.</td>
    </tr>
    <tr>
      <td><b>전화 번호 필드</b></td>
      <td>국가를 기반으로 한 포맷으로 전화번호를 캡처합니다.</td>
    </tr>
    <tr>
      <td><b>텍스트</b></td>
      <td>확인란을 통해 약관을 표시하고 사용자 계약을 수집하는 전용 섹션을 제공합니다.</td>
    </tr>
    <tr>
      <td><b>텍스트 필드</b></td>
      <td>DCapps 한 줄 입력 (예: 이름 또는 이메일 주소).</td>
    </tr>
    <tr>
      <td><b>마법사</b></td>
      <td>여러 부분으로 구성된 양식 프로세스를 단계별로 안내합니다.</td>
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

사용자 환경에 범용 편집기 및 규칙 편집기를 사용하거나 Forms 포털, 기록 문서, Adobe Sign 통합 또는 오른쪽에서 왼쪽 쓰기 언어 지원과 같은 추가 기능을 요청하려면 공식 주소로 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)에 전자 메일을 보내 요청하면 됩니다.



## 양식 만들기 시작

* [AEM Forms용 Edge Delivery Services 시작하기](/help/edge/docs/forms/tutorial.md)
* [Google Sheets 또는 Microsoft Excel을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)
* [Google Sheets 또는 Microsoft Excel 파일을 설정하여 데이터 수신 시작&#x200B;](/help/edge/docs/forms/submit-forms.md)
* [양식 게시 및 데이터 수집 시작](/help/edge/docs/forms/publish-forms.md)
* [양식 모양 사용자 정의&#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [양식에 반복 가능한 섹션 추가&#x200B;](/help/edge/docs/forms/repeatable-forms.md)
* [양식 제출 후 사용자 정의 감사 메시지 표시&#x200B;](/help/edge/docs/forms/thank-you-page-form.md)
* [적응형 양식 블록 구성 요소 및 해당 속성](/help/edge/docs/forms/form-components.md)
* [실제 사용 모니터링](https://www.aem.live/developer/rum#authentication)

<!-- 

## Start creating forms

<div>

  <style>
    .card-container {
        width: calc(30% - 10px);;
        margin: 5px;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 5px;
        box-sizing: border-box;
        transition: background-color 0.3s ease; /* Adding transition effect */
    }
    .card-container:hover {
        background-color: #f0f0f0; /* Changing background color on hover */
    }
</style>

<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: -5px;">
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md">
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using eds forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an eds form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Customize a theme</b>
        </a>
        <p>Create a consistent brand image by applying the same theme across forms.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Add validations to form fields" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Apply field validations</b>
        </a>
        <p>Reduce errors and frustration by checking form inputs for proper formatting.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Use rules to add dynamic behaviour to a form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use rules to add dynamic behaviour to a form</b>
        </a>
        <p>Reuse preconfigured fragments across multiple forms.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Add repeatable sections</b>
        </a>
        <p>Effortlessly create and add repeatable sections to a form.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Create custom forms components using standard JavaScript and CSS"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create custom components</b>
        </a>
        <p>Use standard JavaScript and CSS to create components and themes.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->
