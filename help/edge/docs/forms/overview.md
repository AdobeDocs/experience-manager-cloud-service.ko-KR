---
title: AEM Forms Edge Delivery Service 개요
description: 최고의 성능을 위해 구축된 AEM Forms Edge Delivery Service를 통해 간소화된 데이터 수집 및 사용자 참여라는 미래를 구상할 수 있습니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: d0c4f2f880ef7c11b11144502d30430336ac682e
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 30%

---


# AEM Forms Edge Delivery Service

Adobe의 AEM Forms Edge Delivery Service를 통해 양식 생성을 간소화하고 완료율을 높일 수 있습니다. 이 강력하고 컴포저블 서비스는 탁월한 성능과 시각적인 매력으로 엔터프라이즈급 양식을 구축할 수 있도록 해줍니다. AEM은 사용자 경험과 비즈니스 목표 모두에 우선 순위를 두므로 빠르게 로드할 수 있고 양식 완성도를 높일 수 있습니다.

이 서비스를 사용하여 다음을 수행할 수 있습니다.

* **멋진 양식으로 사용자 Captivate**: 사전 빌드된 구성 요소 라이브러리를 사용하여 복잡하고 매력적인 양식을 쉽게 빌드합니다. 쉽게 reCAPTCHA를 통합하고, 양식을 이메일로 직접 제출하고, Sharepoint, Azure Storage 및 Amazon S3와 같은 보안 스토리지 솔루션에 원활한 파일 업로드를 허용합니다. 자신만의 사용자 정의 양식 구성 요소를 만들어 자신만의 고유한 비전을 실현할 수도 있습니다.

* **원하는 도구를 사용하여 디지털 등록 환경 만들기**: 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본적으로 문서 기반 작성(Microsoft 365 및 Google Workspace)과 AEM 작성(AEM 편집기)을 모두 사용할 수 있습니다. 따라서 동일한 웹 사이트에서 여러 컨텐츠 소스로 작업하고 Microsoft Excel, Google Sheets 또는 적응형 Forms 편집기와 같은 원하는 작성 도구를 사용할 수 있습니다.

* **완벽한 Lighthouse 점수로 양식 작성**: 느린 인터넷 연결에서도 빠르게 로드하고 렌더링하는 양식을 빌드합니다. 로드 시간이 빠르고 사용자 경험이 최적화되어 있으면 양식 작성률을 높이고 전환율을 향상할 수 있습니다.

  <div>
    <style>
    .image-container {
    width: 80%;
    text-align: center; 
    }
    .image-container img {
        width: 100%; /* Set image width to 100% of the container */
        border: .5px solid; /* Maintain the border style */
        padding: 15px; /* Maintain the padding */
    }
</style>
    <div class="image-container">
    <img src="/help/edge/assets/eds-forms-key-features.png" alt="EDS Forms 주요 기능">
    </div>


</div>

<!--

    ![Enrollment forms](/help/edge/assets/enrollment-form.png)

* **Build forms with perfect lighthouse score**: Build forms that load and render quickly, even on slow internet connections. Faster loading times and optimized user experience contribute to higher form completion rates and improved conversion rates.

    ![perfect lighthouse score for your forms](/help/edge/assets/lighthouse-forms.png)

* **Create digital enrollment experiences with tools of your choice**: Increase authoring efficiency by decoupling content sources. Out of the box you can use both AEM authoring and document-based authoring. As such, you can work with multiple content sources on the same website and use your preferred authoring tools, such as Microsoft Excel, Google Sheets, or AEM Editors.

    ![Edge Delivery forms authoring tools](/help/edge/assets/edge-delivery-forms-authoring-tools.png)
    
<!--
* **Measure customer impact and deliver effective forms**: Use our RUM dashboards to visualize form performance and identify areas for improvement. Experiment with different versions and continuously optimize your forms for maximum effectiveness, ensuring you capture the data you need and drive better business outcomes.

* **Use Integrated services:** Use integrated services to streamline and empowers your users with a one-stop shop for managing their digital enrollment journeys. Use e-signatures, automated workflows, document of record (DoR), and seamless data integration, simplify the entire digital enrollment process, accelerate approvals, and optimizes your business workflows. 

    
    >[!NOTE]
    >
    >
    > WYSIWYG authoring capability, integrated services, and customer impact measuring features are available under early adopter program. You can write to aem-forms-early-adopter-program@adobe.com from your official email id to join the early adopter program and request access to the capability.

    -->

## 주요 기능

* **HTML5 기반 양식 필드 구성 요소**: AEM Forms Edge Delivery Service를 통해 유효한 HTML5를 기반으로 하는 양식 필드를 사용하여 사용자 친화적인 대화형 양식을 만들 수 있습니다 [입력 유형](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">텍스트 영역</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">선택</a>, 및 <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">필드 세트</a>  구성 요소. 이러한 구성 요소는 다양한 유형의 데이터 수집에 적합하며 특정 요구 사항에 맞게 쉽게 사용자 지정할 수 있습니다.

* **접근성**: 양식 블록의 필드에 액세스할 수 있습니다. 각 레이블은 해당 입력 요소와 연결되고 연결을 위해 ID가 자동으로 생성됩니다. 필드와 연결된 설명은 Aria-describedby 속성을 통해 연결됩니다. 표준 Tab/Shift + Tab 키를 사용하는 키보드 탐색이 지원됩니다.

* **양식 규칙**: 사용자 입력 또는 사전 정의된 조건에 따라 필드 가시성, 유효성 검사 및 동작을 조정하는 논리를 만듭니다. 규칙은 양식에 지능을 추가하는 유연하고 직관적인 방법을 제공하여 사용자 입력에 따라 원활하게 조정되도록 합니다.

* **파일 업로드**: 원활한 파일 첨부 기능을 통해 양식을 향상시킬 수 있습니다. 사용자로부터 문서, 이미지 또는 기타 파일을 수집해야 하는 경우 적응형 양식 블록을 사용하면 파일 업로드 기능을 손쉽게 통합할 수 있습니다. 사용자 지정 처리 옵션을 사용하면 특정 요구 사항에 맞게 파일 업로드 프로세스를 조정할 수 있습니다.

* **양식 유효성 검사**: 제출하기 전에 양식의 유효성을 검사하고 유효하지 않은 필드에 오류 메시지가 표시된 상태로 사용자에게 표시됩니다. 이러한 오류를 표시하기 위해 다양한 패턴을 사용할 수 있습니다.

* **Forms 스타일링**: 각 양식 필드에는 사용자 지정 CSS 또는 JavaScript 파일을 사용하여 추가로 데코레이트할 수 있는 고정된 HTML 구조가 있습니다. CSS/JS의 타겟팅 필드에 대한 선택기는 유형 및 이름을 기반으로 제공됩니다.

## 워크플로

![문서 기반 작성 에코시스템](/help/edge/assets/document-based-authoring-workflow.png)

## 양식 만들기 시작

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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="EDS 양식을 사용하여 양식 만들기" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Google Sheets 또는 Microsoft Excel을 사용하여 양식 만들기</b>
        </a>
        <p>모바일 디바이스에서 빠르게 로드 및 렌더링되고 자동으로 재배치되는 양식을 만듭니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="양식 제출" alt="EDS 양식에서 양식 조각 사용" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">스프레드시트에 양식 제출</b>
        </a>
        <p>Microsoft Excel 또는 Google Sheets에 직접 양식을 제출합니다.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="EDS 양식에 스타일 또는 테마 적용" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">테마 사용자 정의</b>
        </a>
        <p>동일한 테마를 여러 양식에 적용하여 일관된 브랜드 이미지를 만듭니다.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="양식 필드에 유효성 검사 추가" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">필드 유효성 검사 적용</b>
        </a>
        <p>올바른 형식으로 양식 내용을 입력했는지 확인하여 오류와 불만을 줄입니다.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="규칙을 사용하여 양식에 동적 동작 추가" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">규칙을 사용하여 양식에 동적 동작 추가</b>
        </a>
        <p>여러 양식에서 사전 구성된 조각을 재사용합니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="EDS 양식 번역" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">양식 번역</b>
        </a>
        <p>비용을 억제하면서 양식의 범위를 확장합니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="EDS 양식에 반복 가능한 섹션 추가" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">반복 가능한 섹션 추가</b>
        </a>
        <p>반복 가능한 섹션을 손쉽게 만들고 양식에 추가합니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="표준 JavaScript 및 CSS를 사용하여 사용자 정의 양식 구성 요소 만들기"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">사용자 정의 구성 요소 만들기</b>
        </a>
        <p>표준 JavaScript 및 CSS를 사용하여 구성 요소와 테마를 만듭니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="EDS 양식에서 reCAPTCHA 사용" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">reCAPTCHA 사용</b>
        </a>
        <p>강력한 스팸 및 봇 방지 기능을 위해 OOTB reCAPTCHA 통합을 사용합니다.</p>
    </div>


</div>


</br>









