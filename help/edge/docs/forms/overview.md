---
title: AEM Forms Edge Delivery Services 개요
description: 최고 성능을 위해 구축된 AEM Forms Edge Delivery Services을 통해 간소화된 데이터 수집 및 사용자 참여의 미래를 구상할 수 있습니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: f4cf79e2cd71a390741987cfcf034e6eed02432d
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---

# AEM Forms Edge Delivery Services

AEM Forms Edge Delivery Services은 작성자가 새로운 양식을 신속하게 업데이트, 게시 및 실행할 수 있는 신속한 개발 환경을 구현하는 구성 가능한 서비스 세트입니다. 이러한 서비스는 참여 및 전환을 유도하는 효과적이고 영향력이 큰 양식 경험을 제공합니다. 이러한 양식 경험은 작성 및 개발하기 쉽습니다.

이러한 서비스를 통해 다음을 수행할 수 있습니다.

* **원하는 도구를 사용하여 등록 경험을 만들 수 있습니다.** 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본적으로 문서 기반 작성(Microsoft SharePoint 또는 Google 드라이브)과 AEM 작성(적응형 Forms 편집기)을 모두 사용할 수 있습니다. 동일한 양식 사이트에서 여러 컨텐츠 소스로 작업하고 Microsoft Excel, Google Sheets 또는 적응형 Forms 편집기와 같은 원하는 작성 도구를 사용할 수 있습니다.

* **탁월한 디지털 등록 경험을 제공합니다.** 빠르게 로드하고 렌더링하는 디지털 등록 경험을 제공합니다. 더 빠른 로드 시간과 최적화된 사용자 경험은 더 높은 양식 완료 및 전환율에 기여합니다.

* **개발자에게 친숙한 도구 세트 사용:** AEM Forms Edge Delivery Services은 일반 HTML, 최신 CSS 및 바닐라 JavaScript를 사용하여 특정 프레임워크의 가파른 학습 곡선을 피하고 탁월한 경험을 만듭니다. 기본 웹 개발 기술을 보유한 개발자는 양식 구성 요소 및 경험을 사용자 정의하고 쉽게 빌드할 수 있습니다. 파이프라인이 실행될 때까지 기다릴 필요가 없습니다. 코드를 GitHub에 체크 인하기만 하면 변경 사항이 라이브됩니다.

## AEM Forms Edge Delivery Services 개요 {#edge-overview}

AEM Forms Edge Delivery 서비스를 통해 웹 사이트에서 양식을 작성하는 방법을 매우 유연하게 수행할 수 있습니다. 을 사용하여 콘텐츠 및 양식을 작성할 수 있습니다. [AEM 작성](/help/forms/creating-adaptive-form-core-components.md) 뿐만 아니라 [문서 기반 작성](/help/edge/docs/forms/create-forms.md). AEM Forms Edge Delivery Services은 다음과 같은 양식 블록을 제공합니다. [적응형 Forms 블록](/help/edge/docs/forms/create-forms.md) Edge Delivery Services 사이트에 양식을 추가합니다.

예를 들어 양식을 직접 Microsoft Excel 또는 Google Sheets에서 작성하면 이들 스프레드시트는 웹 사이트용 양식으로 변환됩니다. 새 양식 필드와 같은 모든 새 양식 또는 양식 콘텐츠는 재구축 프로세스 없이 웹 사이트에서 즉시 사용할 수 있습니다.

다음 다이어그램은 Microsoft Excel 또는 Google 시트(문서 기반 작성)에서 양식을 편집하고 Edge Delivery Services에 게시하는 방법을 보여 줍니다. 또한 적응형 Forms 편집기(AEM 작성)를 사용한 AEM 게시 방법을 보여 줍니다.

![Edge Delivery Services 및 AEM에 게시](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

AEM Forms Edge Delivery Services은 GitHub를 사용하므로 고객은 GitHub 저장소에서 직접 코드를 관리하고 배포할 수 있습니다. 예를 들어 다음 중 하나로 양식을 작성할 수 있습니다. [Google Sheets](/help/edge/docs/forms/create-forms.md) 또는 [Microsoft Excel](/help/edge/docs/forms/create-forms.md) GitHub 저장소에서 CSS 및 JavaScript를 사용하여 양식의 구성 요소를 개발할 수 있습니다.

양식이 준비되면 [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), 콘텐츠 업데이트를 미리 보고 게시하기 위한 chrome 브라우저 확장 프로그램.

![설치 AEM Sidekick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

다음 중에서 선택 [문서 기반 작성](#document-based-authoring-features) 및 [AEM 작성](#aem-authoring-features) 은 특정 요구 사항에 따라 다릅니다.

* 몇 가지 필드(예: 양식, 리드 생성 양식 또는 서비스 요청 양식)가 있는 기본 정보를 수집하는 간단한 양식과 스프레드시트를 사용하여 빠른 데이터 연결이 필요한 경우 [문서 기반 작성](#document-based-authoring-features) 잘 맞네요. Google Sheets 또는 Microsoft Excel에서 문서를 작성하는 것처럼 이러한 양식을 작성할 수 있습니다.

* 여러 패널이 필요한 양식, 복잡한 규칙 및 비즈니스 로직, 데이터 조작, 외부 시스템과의 통합 또는 AEM 기능을 사용한 간소화된 워크플로와 같은 복잡한 양식의 경우 다음을 수행합니다 [AEM 작성](#aem-authoring-features) 더 나은 선택입니다.


### 문서 기반 작성 및 AEM 작성의 주요 기능

문서 기반 작성은 기본 기능 세트를 제공하며 AEM 작성은 문서 기반 작성 이외의 추가 기능을 잠금 해제하고 보다 복잡하고 대화형 양식을 작성할 수 있도록 해 줍니다. 문서 기반 작성 및 AEM 작성의 주요 기능은 다음과 같습니다.

#### 문서 기반 작성 기능

문서 기반 작성을 사용하면 Microsoft Excel 또는 Google Sheets와 같은 익숙한 도구를 사용하여 양식을 만들 수 있습니다. 이러한 양식은 다음과 같은 기능을 제공합니다.

* 액세스 가능한 구성 요소로 사용자 친화적 인 환경을 제공합니다.
* 일관된 렌더링을 위해 표준화된 HTML 구조.
* 데이터 정확성을 보장하는 규칙 및 유효성 검사.
* 추가 정보 수집을 위한 첨부 파일 옵션.
* 스팸 보호를 위한 Google reCAPTCHA 통합.
* 특정 요구 사항에 맞게 사용자 정의 양식 구성 요소를 만들 수 있습니다.
* 양식 데이터를 Microsoft Excel 또는 Google Sheets 또는 이메일 주소로 직접 제출합니다.

#### AEM 작성 기능

AEM 작성은 양식 작성을 위한 WYSIWYG 인터페이스(적응형 Forms 편집기)를 제공하며 문서 기반 작성의 모든 기능과 광범위한 추가 기능을 제공합니다.

* 복잡한 논리를 만들기 위한 고급 규칙 편집기.
* 사용자 정의 기능을 위한 서버측 확장성.
* 간편한 양식 생성 및 시각화를 위한 WYSIWYG 편집 환경.
* 제출된 데이터의 변조 불가능한 아카이브를 만드는 기록 문서 기능.
* 전자 서명을 위해 Adobe Sign과 통합.
* Adobe Workfront Fusion과 통합하여 양식 제출 시 Adobe Workfront Fusion 시나리오를 트리거합니다.
* 양식을 미리 채우고 데이터를 제출하기 위해 다양한 데이터 소스와 통합됩니다.
* 데이터 구조 및 다양한 데이터 소스와의 상호 작용을 정의하기 위한 양식 데이터 모델
* Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics 등 다양한 데이터 소스에 데이터를 제출하는 작업을 포함하여 양식 제출을 처리하기 위해 여러 제출 작업 중에서 선택할 수 있습니다.

본질적으로, [AEM 작성](/help/forms/creating-adaptive-form-core-components.md) 을 기반으로 구축 [문서 기반 작성](/help/edge/docs/forms/create-forms.md)복잡한 양식을 만들고 관리하기 위한 고급 툴킷을 제공합니다.

>[!NOTE]
>
>
> AEM 작성 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 관심이 있는 경우, 기능에 대한 액세스를 요청하려면 회사 주소에서 aem-forms-ea@adobe.com으로 빠른 이메일을 보내십시오.

### AEM Forms Edge Delivery Services: Forms 작성, 게시 및 제출

다음 다이어그램은 문서 기반 작성 및 AEM 작성을 사용하여 양식을 작성, 게시 및 제출하는 프로세스를 보여 줍니다.

![문서 기반 작성 ](/help/edge/assets/document-based-authoring-workflow.png)

![AEM 작성](/help/edge/assets/aem-authoring-workflow.png)




## 양식 만들기 시작

* [AEM Forms Edge Delivery Services 시작](/help/edge/docs/forms/tutorial.md)
* [Google Sheets 또는 Microsoft Excel을 사용하여 양식 만들기](/help/edge/docs/forms/create-forms.md)
* [Google Sheets 또는 Microsoft Excel 파일을 설정하여 데이터 &#x200B; 수락 시작](/help/edge/docs/forms/submit-forms.md)
* [양식을 게시하고 데이터 수집 시작](/help/edge/docs/forms/publish-forms.md)
* [양식의 모양 사용자 지정&#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [양식에 반복 가능한 섹션 추가&#x200B;](/help/edge/docs/forms/repeatable-forms.md)
* [양식 제출 후 사용자 정의 감사 메시지 &#x200B; 표시](/help/edge/docs/forms/thank-you-page-form.md)
* [적응형 양식 블록 구성 요소 및 속성](/help/edge/docs/forms/form-components.md)















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