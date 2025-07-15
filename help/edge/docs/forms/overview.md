---
title: AEM Forms용 Edge Delivery Services 개요
description: 범용 편집기 작성 접근 방식을 강조하여 Adobe Experience Manager Edge Delivery Services에서 고성능 양식을 작성하고 전달합니다.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 48%

---


# AEM Forms용 Edge Delivery Services


AEM Forms용 Edge Delivery Services는 새 양식을 빠르게 업데이트, 게시 및 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. 이러한 서비스는 참여와 전환을 촉진하는 탁월하고 영향력 있는 양식 경험을 선사합니다. 이러한 양식 환경은 쉽게 작성하고 개발할 수 있습니다.

이러한 서비스를 통해 다음이 가능합니다.

* **원하는 도구를 사용하여 등록 경험 조성**: 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본적으로 문서 기반 작성(Microsoft SharePoint 또는 Google Drive)과 WYSIWYG 작성(범용 편집기 또는 적응형 양식 편집기)을 사용할 수 있습니다. 동일한 양식 사이트에서 여러 콘텐츠 소스로 작업하고 Microsoft Excel, Google Sheets, 범용 편집기 또는 적응형 양식 편집기 등 선호하는 작성 도구를 사용할 수 있습니다.

* **뛰어난 디지털 등록 경험 제공:** 운영 원격 측정을 통해 신속하게 로드 및 렌더링하고 양식 성능을 지속적으로 모니터링하는 디지털 등록 경험을 제공합니다. 로드 시간이 빠르고 사용자 경험이 최적화되어 있으면 양식 작성률과 전환율을 향상할 수 있습니다.

* **개발자 친화적인 도구 세트 사용:** AEM Forms용 Edge Delivery Services는 일반 HTML, 최신 CSS 및 바닐라 JavaScript를 사용하여 특정 프레임워크의 가파른 학습 곡선을 방지하면서 뛰어난 경험을 창출합니다. 기본적인 웹 개발 기술을 갖춘 개발자라면 양식 구성 요소와 경험을 사용자 정의하고 손쉽게 빌드할 수 있습니다. 파이프라인이 실행될 때까지 기다릴 필요 없이 코드를 GitHub에 체크인하면 변경 사항이 적용됩니다.

## 작성 방법 선택


Adobe Experience Manager(AEM) EDS(Edge Delivery Services)를 사용하면 엣지에서 매우 빠르고 확장성이 뛰어난 웹 경험을 제공할 수 있습니다. 이 안내서에서는 명확한 권장 계층 구조를 사용하여 **이러한 경험에 대한 양식을 작성하고 게시하는 방법**&#x200B;을 설명합니다.

1. **유니버설 편집기(UE) - 대부분의 팀에 가장 적합한 옵션**
2. **문서 기반 작성(문서/시트) - 빠르고 간단한 양식에 적합**
3. **DA(문서 작성) - DA가 작성된 페이지에 양식을 포함하는 데 사용**

마지막에 올바른 작성 방법을 선택하고 제출 옵션을 이해한 다음, 프로덕션 준비 양식에 대한 다음 단계를 따를 수 있습니다.





| 팀 및 요구 사항 | 권장 메서드 | 이유 |
|--------------------|--------------------|-----|
| 마케터/디자이너는 시각적 제어, 조건부 논리 또는 AEM 통합이 필요합니다 | **Universal Editor** | 드래그 앤 드롭, 고급 규칙, FSS 또는 AEM 게시로 제출 |
| 이미 Word/Google Docs/Sheets에서 작업 중인 콘텐츠 작성자, 스프레드시트/이메일로 간단한 데이터 캡처 | **문서 기반 작성** | 친숙한 도구, 기본 양식을 위한 가장 빠른 경로 |
| **DA(문서 작성)**&#x200B;에 빌드된 웹 사이트 페이지 | DA 페이지에 UE 또는 문서 기반 양식을 **포함** | DA는 양식 자체를 빌드하지 않습니다. |


## 작성 방법 세부 정보

### Universal Editor

<span class="preview"> <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features">시험판 채널</a>을 통해 사용할 수 있는 시험판 기능입니다. </span>

범용 편집기는 속도와 엔터프라이즈급 성능을 결합한 마케터 및 디자이너를 위한 시각적, 드래그 앤 드롭 작성 도구입니다.

* 실시간 WYSIWYG 편집 및 장치 미리 보기.
* AEM 자산, 워크플로우 및 양식 데이터 모델(FDM)과 직접 통합합니다.
* 바닐라 JS/CSS의 사용자 지정 구성 요소에 대해 개발자에게 매끄러운 핸드오프입니다.
* 복잡한 로직을 생성하기 위한 고급 규칙 편집기.
* 사용자 정의 기능을 위한 서버측 확장성.
* 쉬운 양식 만들기 및 시각화를 위한 WYSIWYG 편집 경험.
* 제출된 데이터의 변조 방지 아카이브를 만드는 기록 문서 기능.
* 전자 서명을 위한 Adobe Sign 통합.
* 양식 제출 시 Adobe Workfront Fusion 시나리오를 트리거하기 위한 Adobe Workfront Fusion 통합.
* 양식을 미리 채우고 데이터를 제출하기 위한 다양한 데이터 소스 통합.
* 다양한 데이터 소스와의 데이터 구조 및 상호 작용을 정의하기 위한 양식 데이터 모델(FDM).
* Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, 더 많은 데이터 소스에 데이터를 제출하는 기능을 포함하여 양식 제출을 처리하기 위한 여러 제출 작업 중에서 선택할 수 있는 기능.
* Forms 제출 서비스(FSS) 또는 AEM 게시 제출 액션을 사용하여 제출

> **권장 사항**: 팀이 100% 문서 중심이고 양식이 매우 기본이 아닌 경우 유니버설 편집기로 모든 새 양식 프로젝트를 시작하십시오.


### 문서 기반 작성(Microsoft 문서 또는 Google Sheets 사용)

문서 기반 작성은 Microsoft Word, Google Docs 또는 Google Sheets와 같은 친숙한 도구를 사용하여 단순하고 복잡하지 않은 양식을 작성하는 데 가장 적합합니다. 이 방법은 양식을 빠르고 간단하게 작성하는 방법이 필요한 콘텐츠 팀에 이상적입니다.

* 사용자 친화적인 경험을 위한 접근성 구성 요소.
* 일관된 렌더링을 위한 표준화된 HTML 구조.
* 데이터 정확성을 보장하기 위한 규칙 및 유효성 검사.
* 추가 정보 수집을 위한 파일 첨부 옵션.
* 스팸 방지를 위한 Google reCAPTCHA 통합.
* 특정 요구에 맞는 사용자 정의 양식 구성 요소를 만드는 기능.
* 양식 데이터를 Microsoft Excel 또는 Google Sheets 또는 이메일 주소로 직접 제출.
* 운영 원격 측정을 통해 양식 성능 모니터링


### DA(문서 작성)에 Forms 포함

DA(Document Authoring)는 구조화된 페이지 콘텐츠를 만들기 위해 설계되었으며 기본 양식 만들기를 지원하지 않습니다. DA 작성 페이지에 양식을 추가하려면 **유니버설 편집기**(권장) 또는 문서 기반 작성을 사용하여 양식을 만들고 해당 양식을 문서 작성 페이지에 포함할 수 있습니다.

## Edge Delivery Services Forms 게시 {#edge-overview}

다음 다이어그램은 Microsoft Excel 또는 Google Sheets(문서 기반 편집)에서 양식을 편집하고 Edge Delivery Services에 게시하는 방법을 보여 줍니다. 또한 WYSIWYG 작성(범용 편집기)을 사용하는 AEM 게시 방법을 보여 줍니다.

![Edge Delivery Services 및 AEM에 게시](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)


<!-- 
## Feature Comparison

| Capability | Universal Editor | Document-Based | Document Authoring |
|------------|-----------------|----------------|--------------------|
| Visual drag-and-drop | ✅ | – | – |
| Advanced rules editor | ✅ | Limited | – |
| Attachments | ✅ | EA | – |
| reCAPTCHA Enterprise | ✅ | ✅ | Depends on embed |
| Submit to spreadsheet/email | ✅ (FSS) | ✅ (FSS) | Via embed |
| Submit to AEM workflows/FDM | ✅ | – | Via UE embed |
| Custom components (JS/CSS) | ✅ | ✅ | Via embed |
| Localization via Sites | ✅ | Manual | Via embed |

-->

## 다음 단계

1. **유니버설 편집기로 시작:** 양식 작성을 시작하려면 [유니버설 편집기 시작 안내서](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)를 참조하세요.
1. **문서 기반 작성 사용:** Microsoft Excel 또는 Google Sheets로 양식을 만들려면 [문서 기반 작성 자습서](/help/edge/docs/forms/tutorial.md)를 따르십시오.
1. **문서 작성에 Forms 포함:** 문서 작성에서 페이지를 작성하는 경우 **유니버설 편집기**(권장) 또는 문서 기반 작성을 사용하여 양식을 만들고 [DA 페이지](https://www.aem.live/developer/da-tutorial)에 양식을 포함하십시오.

이제 AEM Edge Delivery Services을 사용하여 첫 번째 고성능 양식을 만들 준비가 되었습니다.


<!-- 

## Start creating forms

* [Get started with Edge Delivery Services for AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Create a form using Google Sheets or Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Set up your Google Sheets or Microsoft Excel files to start accepting data​](/help/edge/docs/forms/submit-forms.md)
* [Publish your form and start collecting data](/help/edge/docs/forms/publish-forms.md)
* [Customize the look of your forms​](/help/edge/docs/forms/style-theme-forms.md)
* [Add repeatable sections to a form​](/help/edge/docs/forms/repeatable-forms.md)
* [Show a custom thank you message after form submission​](/help/edge/docs/forms/thank-you-page-form.md)
* [Adaptive Form Block components and their properties](/help/edge/docs/forms/form-components.md)
* [Real Use Monitoring](https://www.aem.live/developer/rum#authentication)

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