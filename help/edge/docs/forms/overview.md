---
title: AEM Forms Edge Delivery Service 개요
description: 최고 성능을 위해 구축된 AEM Forms Edge Delivery Service를 통해 향후 간소화된 데이터 수집 및 사용자 참여를 구상할 수 있습니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: b94bd6cd70af541444fda1d03f502b4588fd879b
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# AEM Forms Edge 게재 서비스 {#aem-forms-edge-delivery-service-overview}

AEM Forms Edge Delivery Service는 Adobe에서 제공하는 구성 가능한 서비스로, 효과가 크고 성능이 빠른 웹 양식을 제작하여 제공할 수 있습니다. 이 컴포저블 서비스는 Adobe Experience Manager(AEM)와 원활하게 통합되어 직관적이고 효율적인 워크플로우를 통해 영향력이 크고 번개처럼 빠른 웹 양식을 디자인, 빌드 및 배포할 수 있도록 해 줍니다.

AEM Forms Edge Delivery Service는 다음과 같은 이점을 제공합니다.

* **시각적으로 놀라운 형태 제작**: 깔끔하고 자그마한 디자인을 버리고 브랜드 정체성을 반영하는 다이내믹하고 현대적인 양식으로 사용자를 사로잡습니다. 사전 제작된 구성 요소를 활용하거나 사용자 지정 구성 요소를 만들어 비전을 빠르고 쉽게 실현할 수 있습니다.

* **완벽한 등대 점수로 양식 작성**: 느린 인터넷 연결에서도 빠르게 로드하고 렌더링하는 양식을 빌드합니다. 로드 시간이 빨라지고 사용자 경험이 최적화되면 양식 완료율이 높아지고 전환율이 향상됩니다.

* **작성 및 제출 간소화**: 기존의 작성 환경 대신 Microsoft Excel 또는 Google Sheets와 같은 친숙한 도구를 사용하여 양식을 만듭니다. 양식을 Microsoft Excel 또는 Google 시트에 직접 제출하고 에코시스템을 사용하여 제출된 데이터를 쉽게 처리할 수 있습니다.

## AEM Forms Edge Delivery Service 시작

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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="eds 양식을 사용하여 양식 만들기" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">양식 만들기</b>
        </a>
        <p>모바일 장치에서 빠르고 자동으로 리플로우되는 양식을 만듭니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="양식 필드에 유효성 검사 추가" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">필드 유효성 검사 적용</b>
        </a>
        <p>양식 입력에서 적절한 형식을 확인함으로써 오류와 어려움을 줄일 수 있습니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/form-fragments.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="EDS 양식에서 양식 단편 사용" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">양식 단편 만들기</b>
        </a>
        <p>여러 양식에서 사전 구성된 조각을 재사용합니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="EDS 양식 번역" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">양식 번역</b>
        </a>
        <p>비용을 억제하면서 양식의 범위를 확장하십시오.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Eds 양식에 스타일 또는 테마 적용" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">테마 맞춤화</b>
        </a>
        <p>여러 양식에 동일한 테마를 적용하여 일관된 브랜드 이미지를 만듭니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="EDS 양식에 반복 가능한 섹션 추가" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">반복 가능한 섹션 추가</b>
        </a>
        <p>반복 가능한 섹션을 간편하게 만들어 양식에 추가합니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="표준 JavaScript 및 CSS를 사용하여 사용자 정의 양식 구성 요소 만들기"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">사용자 지정 구성 요소 만들기</b>
        </a>
        <p>표준 JavaScript 및 CSS를 사용하여 구성 요소 및 테마를 만들 수 있습니다.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="EDS 양식에서 reCAPTCHA 사용" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">reCAPTCHA 사용</b>
        </a>
        <p>강력한 스팸 및 보트 보호를 위해 OOTB reCAPTCHA 통합을 사용하십시오.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="양식 제출" alt="EDS 양식에서 양식 단편 사용" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">스프레드시트에 양식 제출</b>
        </a>
        <p>양식을 Microsoft Excel 또는 Google Sheets에 직접 제출합니다.</p>
    </div>
</div>


</br>









