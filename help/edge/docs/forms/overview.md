---
title: AEM Forms Edge Delivery Services 개요
description: 최고 성능을 위해 구축된 AEM Forms Edge Delivery Services을 통해 간소화된 데이터 수집 및 사용자 참여의 미래를 구상할 수 있습니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 610f9ba3f342b37d0d20a91c337323bffe95d58d
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 19%

---

# AEM Forms Edge Delivery Services

Adobe의 AEM Forms Edge Delivery Services을 통해 양식 생성을 간소화하고 완료율을 높일 수 있습니다. 이러한 강력하고 컴포저블 서비스를 통해 탁월한 성능과 시각적 매력으로 엔터프라이즈급 양식을 구축할 수 있습니다. AEM은 사용자 경험과 비즈니스 목표 모두에 우선 순위를 두므로 빠르게 로드할 수 있고 양식 전환이 증가합니다.

이들 서비스를 통해 다음과 같은 작업을 수행할 수 있습니다.

* **탁월한 등록 경험 구축**: 느린 인터넷 연결에서도 빠르게 로드하고 렌더링하는 등록 경험을 빌드합니다. 로드 시간이 빠르고 사용자 경험이 최적화되어 있으면 양식 작성률을 높이고 전환율을 향상할 수 있습니다.

* **선택한 도구로 등록 경험 만들기**: 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본적으로 두 가지를 모두 사용할 수 있습니다. **문서 기반 작성** (Microsoft SharePoint 또는 Google 드라이브) 및 **AEM 작성** (적응형 Forms 편집기). 따라서 동일한 양식에서 여러 컨텐츠 소스로 작업하고 Microsoft Excel, Google Sheets 또는 적응형 Forms 편집기와 같은 원하는 작성 도구를 사용할 수 있습니다.

* **개발자에게 친숙한 도구 세트 사용:** AEM Forms은 일반 HTML, 최신 CSS 및 바닐라 JavaScript를 사용하여 일반적인 오버헤드 없이 탁월한 경험을 만듭니다. HTML, CSS 및 JS에 대한 기본 지식을 갖춘 개발자는 고유한 구성 요소를 빌드할 수 있어야 하며 특정 언어나 프레임워크를 학습할 필요가 없어야 합니다. 파이프라인이나 대기가 필요하지 않습니다. 코드를 Github에 체크 인하면 변경 사항이 활성화됩니다. 또한 파이프라인이나 기다리지 않고 Github에서 코드를 체크인하면 변경 사항이 활성 상태가 됩니다.


## AEM Forms Edge Delivery Services 개요 {#edge-overview}

다음 다이어그램은 Microsoft Excel 또는 Google Sheets에서 콘텐츠를 편집하고(문서 기반 편집) Edge Delivery Services에 게시하는 방법을 보여 줍니다. 또한 적응형 Forms 편집기를 사용한 AEM 게시 방법을 보여줍니다.

![Edge Delivery 아키텍처](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

Edge Delivery Services는 웹 사이트에서 콘텐츠를 작성하는 방법을 보다 유연하게 제공하는 구성 가능한 서비스 세트입니다. AEM 컨텐츠 관리를 사용할 수 있는 대상: [AEM 작성](/help/forms/creating-adaptive-form-core-components.md) 뿐만 아니라 [문서 기반 작성](/help/edge/docs/forms/create-forms.md)

예를 들어 Microsoft Excel 또는 Google Sheets에서 직접 콘텐츠를 사용할 수 있습니다. 즉, 이러한 소스의 콘텐츠가 웹 사이트의 양식이 될 수 있습니다. 새 콘텐츠는 리빌드 프로세스 없이 즉시 추가됩니다.

Edge Delivery Services는 GitHub를 사용하므로 고객은 GitHub 저장소에서 바로 코드를 관리 및 배포할 수 있습니다. 예를 들어 Google Sheets 또는 Microsoft Excel에서 양식을 작성할 수 있으며 GitHub에서 CSS와 JavaScript를 사용하여 양식의 구성 요소를 개발할 수 있습니다. 준비가 되면 Sidekick 브라우저 확장 기능을 사용하여 콘텐츠 업데이트를 미리 보고 게시할 수 있습니다.

AEM Forms Edge Delivery Services은 다음과 같은 양식 블록을 제공합니다. [적응형 Forms 블록](/help/edge/docs/forms/create-forms.md) Edge Delivery Services 사이트에 양식을 추가합니다.

### AEM Forms Edge Delivery Services의 주요 기능

문서 기반 작성 기본 기능 세트와 AEM 작성은 문서 기반 작성 이상의 추가 기능을 잠금 해제하여 보다 복잡하고 대화형 양식을 작성할 수 있도록 합니다. 다음 표에는 두 기능의 주요 사항이 나와 있습니다.

<!-- 

>[!BEGINTABS]

>[!TAB Document-based authoring]

Document-based authoring is a versatile option suitable for creating simple forms with essential functionalities. It allows you to integrate various input types like text fields, dropdown menus, and radio buttons, enabling you to collect user data effectively. It offers a basic version of rules to add dynamic behaviour to forms. Key features of Document-based authoring are: 

* **[HTML5-based Form Field components](/help/edge/docs/forms/form-components.md)**: AEM Forms Edge Delivery Services allow you to create user-friendly and interactive forms using form components based on HTML5 [input types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, and <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a>  elements. These components cater to different types of data collection and can be easily customized to fit your specific needs.  

* **Accessibility**: The fields in the form block are accessible. Each label is linked with its respective input element, and IDs are auto-generated for linking. Descriptions associated with fields are linked via the aria-describedby attribute. Keyboard navigation using the standard Tab/Shift + Tab keys is supported.

* **[Styling](/help/edge/docs/forms/style-theme-forms.md)**: Each form field has a fixed HTML structure that can be easily decorated using custom CSS or JavaScript files. Selectors for targeting fields in CSS and JS are provided based on type and name. You can easily create new selectors due to the standradized structure and style your form. 

* **Basic Rules**: Easily create logic that adjusts field visibility, validation, and behavior based on user input or predefined conditions. Rules offer a flexible and intuitive way to add intelligence to your forms, ensuring they adapt seamlessly based on user inputs.

* **Validations**: Before submission, the form is validated, and invalid fields are appropriately marked with error messages displayed to the user. Adaptive Forms Block support all the HTML form validation, supported by modern browsers, and provide additional validation mechanism like validation script, file size, file type, overall file size, and more. 

* **File Uploads**: You can add file attachment capabilities to your forms. Whether you need to gather documents, images, or other files from your users, file upload functionality serves you effortlessly. With custom handling options available, you can tailor the file upload process to suit your specific requirements.

* **reCAPTCHA**: Benefit from seamless integration of Google reCAPTCHA into your forms with our out-of-the-box (OOTB) support. Safeguard your forms against fraudulent activities, spam, and abuse, while maintaining a smooth and uninterrupted user experience. Adaptive Forms Block supports reCaptcha V3 and reCaptcha Enterprise. 

* **Send email notification on form submission**: Eliminate the hassle of manual follow-ups and ensure timely communication with our built-in email automation for form submissions. This integrated solution lets you effortlessly notify relevant parties, including sending form data, whenever someone fills out a form on your website. No need for complex configurations or additional tools – it's ready to use out of the box.

>[!TAB AEM Authoring]

AEM Authoring unlocks additional capabilities beyond the document-based authoring, empowering you to build more complex and interactive forms. In additon to the features of Document-based authoring, AEM authoring offers the following additional features:  

* Advanced Rules: Define logic-based actions within your forms. You can use rules to conditionally show or hide form sections, pre-populate fields based on user input, and perform various validations to ensure data integrity.

* Server-side extensibility: Extend the functionalities of your forms by integrating them with server-side logic. This allows you to perform complex calculations, interact with external systems, and automate specific tasks based on user actions within the form.
* Streamline workflows and data management: Leverage the power of AEM to:
    * Design user-friendly forms using AEM editors.
    * Generate a "Document of Record" for secure and tamper-proof archiving of submitted data.
    * Facilitate e-signing with Adobe Sign for a smooth and secure signing experience.
    * Automate business processes through AEM workflows, triggering actions based on form submissions.
    * Effortlessly integrate with various data sources, enabling seamless data flow and exchange.

>[!ENDTABS]



## Start creating forms

-->

|                                           | 문서 기반 작성 | AEM 작성(적응형 Forms 편집기) |
| ----------------------------------------- | ------------------------ | ------------------------------------ |
| **양식 기능** |                          |                                      |
| 액세스 가능한 구성 요소 | ✓ | ✓ |
| 표준화된 HTML 구조 | ✓ | ✓ |
| 규칙 및 유효성 검사 | ✓ | ✓ |
| 첨부 파일(파일 업로드) | ✓ | ✓ |
| Google recaptcha | ✓ | ✓ |
| 사용자 지정 구성 요소 | ✓ | ✓ |
| 전자 메일로 제출 | ✓ | ✓ |
| **고급 기능** |                          |                                      |
| 시각적 규칙 편집기를 사용하는 고급 규칙 |                          | ✓ |
| 서버측 확장성 |                          | ✓ |
| 여러 제출 액션 |                          | ✓ |
| **양식 디자인 및 관리** |                          |                                      |
| WYSIWYG 편집용 적응형 Forms 편집기 |                          | ✓ |
| **통합** |                          |                                      |
| 기록 문서 |                          | ✓ |
| Adobe Sign과 통합 |                          | ✓ |
| Adobe Analytics과의 통합 |                          | ✓ |
| Marketo과 통합 |                          | ✓ |
| 여러 데이터 소스와 통합 |                          | ✓ |
| 여러 제출 액션 |                          | ✓ |


## 양식 만들기 시작

* [시작하기 - 개발자 자습서](/help/edge/docs/forms/tutorial.md)
* [Google Sheets 또는 Microsoft Excel을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)
* [양식을 Microsoft Excel 또는 Google Sheets에 직접 제출](/help/edge/docs/forms/submit-forms.md)
* [양식 보기 변경](/help/edge/docs/forms/style-theme-forms.md)


<!-- 

## Start creating forms

<div>

  <style>
    .card-container {
        width: calc(33.33% - 10px);;
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