---
title: AEM Forms Edge Delivery Service 개요
description: 최고의 성능을 위해 구축된 AEM Forms Edge Delivery Service를 통해 간소화된 데이터 수집 및 사용자 참여라는 미래를 구상할 수 있습니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 78d40574e6fea8dde22414e43fd77215b9e7d2a1
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 69%

---


# AEM Forms Edge Delivery Service {#aem-forms-edge-delivery-service-overview}

AEM Forms Edge Delivery Service는 효과가 뛰어나고 성능이 빠른 웹 양식을 만들고 게재할 수 있도록 Adobe에서 제공하는 구성 가능한 서비스입니다. 이 서비스를 사용하여 다음을 수행할 수 있습니다.

* **멋진 양식으로 사용자 Captivate**: 사전 빌드된 구성 요소 라이브러리를 사용하여 복잡하고 매력적인 양식을 쉽게 빌드합니다. 쉽게 reCAPTCHA를 통합하고, 양식을 이메일로 직접 제출하고, Sharepoint, Azure Storage 및 Amazon S3와 같은 보안 스토리지 솔루션에 원활한 파일 업로드를 허용합니다. 자신만의 사용자 정의 양식 구성 요소를 만들어 자신만의 고유한 비전을 실현할 수도 있습니다.

  ![등록 양식](/help/edge/assets/enrollment-form.png)

* **Lighthouse 점수가 만점인 양식 작성**: 느린 인터넷 연결에서도 빠르게 로드되고 렌더링되는 양식을 작성합니다. 로드 시간이 빠르고 사용자 경험이 최적화되어 있으면 양식 작성률을 높이고 전환율을 향상할 수 있습니다.

  ![귀하의 양식에 대한 완벽한 lighthouse 점수](/help/edge/assets/lighthouse-forms.png)

* **원하는 도구를 사용하여 디지털 등록 환경 만들기**: 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본 제공되는 AEM 작성과 문서 기반 작성을 모두 사용할 수 있습니다. 따라서 동일한 웹 사이트에서 여러 컨텐츠 소스로 작업하고 Microsoft Excel, Google Sheets 또는 AEM Editors와 같은 원하는 작성 도구를 사용할 수 있습니다.

  ![Edge 게재 양식 작성 도구](/help/edge/assets/edge-delivery-forms-authoring-tools.png)

<!--
* **Measure customer impact and deliver effective forms**: Use our RUM dashboards to visualize form performance and identify areas for improvement. Experiment with different versions and continuously optimize your forms for maximum effectiveness, ensuring you capture the data you need and drive better business outcomes.

* **Use Integrated services:** Use integrated services to streamline and empowers your users with a one-stop shop for managing their digital enrollment journeys. Use e-signatures, automated workflows, document of record (DoR), and seamless data integration, simplify the entire digital enrollment process, accelerate approvals, and optimizes your business workflows. 

    
>[!NOTE]
    >
    >
    > WYSIWYG authoring capability, integrated services, and customer impact measuring features are available under early adopter program. You can write to aem-forms-early-adopter-program@adobe.com from your official email id to join the early adopter program and request access to the capability.

    -->

## 기본 사항부터 시작

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
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="EDS 양식 번역" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">양식 번역</b>
        </a>
        <p>비용을 억제하면서 양식의 범위를 확장합니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/form-fragments.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="EDS 양식에서 양식 조각 사용" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">양식 조각 만들기</b>
        </a>
        <p>여러 양식에서 사전 구성된 조각을 재사용합니다.</p>
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









