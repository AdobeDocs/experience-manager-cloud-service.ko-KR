---
title: AEM Forms Edge Delivery Services 개요
description: 최고의 성능을 위해 구축된 AEM Forms Edge Delivery Services를 통해 간소화된 데이터 수집 및 사용자 참여라는 미래를 구상할 수 있습니다.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 100%

---

# AEM Forms Edge Delivery Services

AEM Forms Edge Delivery Services는 새 양식을 빠르게 업데이트, 게시 및 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. 이러한 서비스는 참여와 전환을 촉진하는 탁월하고 영향력 있는 양식 경험을 선사합니다. 이러한 양식 환경은 쉽게 작성하고 개발할 수 있습니다.

이러한 서비스를 통해 다음이 가능합니다.

* **원하는 도구를 사용하여 등록 경험 조성**: 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본적으로 문서 기반 작성(Microsoft SharePoint 또는 Google Drive)과 AEM 작성(Adaptive Forms Editor)을 모두 사용할 수 있습니다. 동일한 양식 사이트에서 여러 콘텐츠 소스로 작업하고 Microsoft Excel, Google Sheets 또는 적응형 양식 편집기 등 선호하는 작성 도구를 사용할 수 있습니다.

* **뛰어난 디지털 등록 경험 제공:** 실제 사용자 모니터링(RUM)을 통해 신속하게 로드 및 렌더링하고 양식 성능을 지속적으로 모니터링하는 디지털 등록 경험을 제공합니다. 로드 시간이 빠르고 사용자 경험이 최적화되어 있으면 양식 작성률과 전환율을 향상할 수 있습니다.

* **개발자 친화적인 도구 세트 사용:** AEM Forms Edge Delivery Services는 일반 HTML, 최신 CSS 및 바닐라 JavaScript를 사용하여 특정 프레임워크의 가파른 학습 곡선을 방지하면서 뛰어난 경험을 창출합니다. 기본적인 웹 개발 기술을 갖춘 개발자라면 양식 구성 요소와 경험을 사용자 정의하고 손쉽게 빌드할 수 있습니다. 파이프라인이 실행될 때까지 기다릴 필요 없이 코드를 GitHub에 체크인하면 변경 사항이 적용됩니다.

## AEM Forms Edge Delivery Services 개요 {#edge-overview}

AEM Forms Edge Delivery 서비스를 사용하면 웹 사이트에서 양식을 작성하는 방법과 관련해 높은 수준의 유연성을 누릴 수 있습니다. [AEM 작성](/help/forms/creating-adaptive-form-core-components.md)을 비롯하여 [문서 기반 작성](/help/edge/docs/forms/create-forms.md)을 사용해 콘텐츠 및 양식을 작성할 수 있습니다. AEM Forms Edge Delivery Services에서 제공되는 [적응형 양식 블록](/help/edge/docs/forms/create-forms.md)이라는 양식 블록을 사용하여 Edge Delivery Services 사이트에 양식을 추가할 수 있습니다.

예를 들어 Microsoft Excel 또는 Google Sheets에서 직접 양식을 작성하면 이러한 스프레드시트가 웹 사이트용 양식으로 변환됩니다. 새 양식 필드와 같은 새 양식이나 양식 콘텐츠를 재빌드 프로세스 없이 웹 사이트에서 즉시 사용할 수 있습니다.

다음 다이어그램은 Microsoft Excel 또는 Google Sheets(문서 기반 편집)에서 양식을 편집하고 Edge Delivery Services에 게시하는 방법을 보여 줍니다. 또한 적응형 양식 편집기(AEM 작성)를 사용하는 AEM 게시 방법도 보여 줍니다.

![Edge Delivery Services 및 AEM에 게시](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

AEM Forms Edge Delivery Services는 GitHub를 사용하므로 고객은 GitHub 저장소에서 바로 코드를 관리 및 배포할 수 있습니다. 예를 들어 [Google Sheets](/help/edge/docs/forms/create-forms.md) 또는 [Microsoft Excel](/help/edge/docs/forms/create-forms.md)에서 양식을 작성할 수 있고, GitHub 저장소의 CSS 및 JavaScript를 사용하여 양식의 구성 요소를 작성할 수 있습니다.

양식이 준비되면 Chrome 브라우저 확장 기능인 [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content)을 사용하여 콘텐츠 업데이트를 미리 보고 게시할 수 있습니다.

![AEM SideKick 설치](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

[문서 기반 작성](#document-based-authoring-features)과 [AEM 작성](#aem-authoring-features) 중 무엇을 선택할지는 특정 요구 사항에 따라 다릅니다.

* 몇 가지 필드(연락처 양식, 리드 생성 양식 또는 서비스 요청 양식 등)로 기본 정보를 수집하는 간단한 양식이며 스프레드시트를 사용하여 데이터를 빠르게 연결해야 하는 경우 [문서 기반 작성](#document-based-authoring-features)이 적합합니다. Google Sheets 또는 Microsoft Excel에서 문서를 작성하는 방식과 동일하게 이러한 양식을 작성할 수 있습니다.

* 여러 패널, 복잡한 규칙 및 비즈니스 논리, 데이터 조작, 외부 시스템과의 통합 또는 AEM 기능을 사용한 간소화된 워크플로가 필요한 양식처럼 복잡한 양식의 경우 [AEM 작성](#aem-authoring-features)이 더 나은 옵션입니다.


### 문서 기반 작성 및 AEM 작성의 주요 특징

문서 기반 작성에서는 기본 기능 세트가 제공되며, AEM 작성에서는 문서 기반 작성 이상의 추가 기능을 활용하여 더 복잡한 대화형 양식을 빌드할 수 있습니다. 문서 기반 작성과 AEM 작성의 주요 특징은 다음과 같습니다.

#### 문서 기반 작성 특징

문서 기반 작성에서는 Microsoft Excel 또는 Google Sheets와 같은 친숙한 도구를 사용하여 양식을 만들 수 있습니다. 이러한 양식은 다음 기능을 제공합니다.

* 사용자 친화적인 경험을 위한 접근성 구성 요소.
* 일관된 렌더링을 위한 표준화된 HTML 구조.
* 데이터 정확성을 보장하기 위한 규칙 및 유효성 검사.
* 추가 정보 수집을 위한 파일 첨부 옵션.
* 스팸 방지를 위한 Google reCAPTCHA 통합.
* 특정 요구에 맞는 사용자 정의 양식 구성 요소를 만드는 기능.
* 양식 데이터를 Microsoft Excel 또는 Google Sheets 또는 이메일 주소로 직접 제출.
* 실제 사용자 모니터링(RUM)을 통해 양식 성능 모니터링

#### AEM 작성 특징

AEM 작성에서는 양식 작성에 WYSIWYG 인터페이스(적응형 양식 편집기)가 제공되며, 문서 기반 작성의 모든 기능과 함께 다음과 같은 광범위한 추가 기능이 있습니다.

* 복잡한 로직을 생성하기 위한 고급 규칙 편집기.
* 사용자 정의 기능을 위한 서버측 확장성.
* 쉬운 양식 만들기 및 시각화를 위한 WYSIWYG 편집 경험.
* 제출된 데이터의 변조 방지 아카이브를 만드는 기록 문서 기능.
* 전자 서명을 위한 Adobe Sign 통합.
* 양식 제출 시 Adobe Workfront Fusion 시나리오를 트리거하기 위한 Adobe Workfront Fusion 통합.
* 양식을 미리 채우고 데이터를 제출하기 위한 다양한 데이터 소스 통합.
* 다양한 데이터 소스와의 데이터 구조 및 상호 작용을 정의하기 위한 양식 데이터 모델(FDM).
* Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, 더 많은 데이터 소스에 데이터를 제출하는 기능을 포함하여 양식 제출을 처리하기 위한 여러 제출 작업 중에서 선택할 수 있는 기능.

본질적으로 [AEM 작성](/help/forms/creating-adaptive-form-core-components.md)은 [문서 기반 작성](/help/edge/docs/forms/create-forms.md)을 기반으로 빌드되어 복잡한 양식을 만들고 관리할 수 있는 고급 도구 키트를 제공합니다.

>[!NOTE]
>
>
> AEM 작성 기능은 얼리 어답터 프로그램에서 사용할 수 있습니다. 관심이 있는 경우 회사 주소에서 aem-forms-ea@adobe.com으로 간단한 이메일을 보내 해당 기능에 대한 액세스를 요청하시기 바랍니다.

### AEM Forms Edge Delivery Services: 양식 작성, 게시 및 제출

다음 다이어그램은 문서 기반 작성 및 AEM 작성을 사용하여 양식을 만들고, 게시하고, 제출하는 프로세스를 보여 줍니다.

![문서 기반 작성 ](/help/edge/assets/document-based-authoring-workflow.png)

![AEM 작성](/help/edge/assets/aem-authoring-workflow.png)

## 양식 만들기 시작

* [AEM Forms Edge Delivery Services 시작하기](/help/edge/docs/forms/tutorial.md)
* [Google Sheets 또는 Microsoft Excel을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)
* [Google Sheets 또는 Microsoft Excel 파일을 설정하여 데이터 수신 시작&#x200B;](/help/edge/docs/forms/submit-forms.md)
* [양식 게시 및 데이터 수집 시작](/help/edge/docs/forms/publish-forms.md)
* [양식 모양 사용자 정의&#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [양식에 반복 가능한 섹션 추가&#x200B;](/help/edge/docs/forms/repeatable-forms.md)
* [양식 제출 후 사용자 정의 감사 메시지 표시&#x200B;](/help/edge/docs/forms/thank-you-page-form.md)
* [적응형 양식 블록 구성 요소 및 해당 속성](/help/edge/docs/forms/form-components.md)
* [실시간 사용자 모니터링](https://www.aem.live/developer/rum#authentication)

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