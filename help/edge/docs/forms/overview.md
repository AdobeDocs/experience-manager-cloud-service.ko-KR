---
title: AEM Forms Edge Delivery Services 개요
description: 최고 성능을 위해 구축된 AEM Forms Edge Delivery Services을 통해 간소화된 데이터 수집 및 사용자 참여의 미래를 구상할 수 있습니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 53a66eac5ca49183221a1d61b825401d4645859e
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 17%

---

# AEM Forms Edge Delivery Services

Adobe의 AEM Forms Edge Delivery Services을 통해 양식 생성을 간소화하고 완료율을 높일 수 있습니다. 이러한 강력하고 컴포저블 서비스를 통해 탁월한 성능과 시각적 매력으로 엔터프라이즈급 양식을 구축할 수 있습니다. AEM은 사용자 경험과 비즈니스 목표 모두에 우선 순위를 두므로 빠르게 로드할 수 있고 양식 전환이 증가합니다.

이들 서비스를 통해 다음과 같은 작업을 수행할 수 있습니다.

* **탁월한 등록 경험 구축**: 느린 인터넷 연결에서도 빠르게 로드하고 렌더링하는 등록 경험을 빌드합니다. 로드 시간이 빠르고 사용자 경험이 최적화되어 있으면 양식 작성률을 높이고 전환율을 향상할 수 있습니다.

* **선택한 도구로 등록 경험 만들기**: 콘텐츠 소스를 분리하여 작성 효율성을 높입니다. 기본적으로 두 가지를 모두 사용할 수 있습니다. **문서 기반 작성** (Microsoft SharePoint 또는 Google 드라이브) 및 **AEM 작성** (AEM 편집기). 따라서 동일한 양식에서 여러 컨텐츠 소스로 작업하고 Microsoft Excel, Google Sheets 또는 적응형 Forms 편집기와 같은 원하는 작성 도구를 사용할 수 있습니다.

* **개발자에게 친숙한 도구 세트 사용:** AEM Forms은 일반 HTML, 최신 CSS 및 바닐라 JavaScript를 사용하여 일반적인 오버헤드 없이 탁월한 경험을 만듭니다. HTML, CSS 및 JS에 대한 기본 지식을 갖춘 개발자는 고유한 구성 요소를 빌드할 수 있어야 하며 특정 언어나 프레임워크를 학습할 필요가 없어야 합니다. 파이프라인이나 대기가 필요하지 않습니다. 코드를 Github에 체크 인하면 변경 사항이 활성화됩니다. 또한 파이프라인이나 기다리지 않고 Github에서 코드를 체크인하면 변경 사항이 활성 상태가 됩니다.


## 디지털 등록 환경 만들기

AEM Forms은 두 가지 오퍼를 모두 제공합니다. **문서 기반 작성** (Microsoft SharePoint 또는 Google 드라이브) 및 **AEM 작성** (AEM 편집기). 다음을 사용할 수 있습니다. [적응형 Forms 블록](/help/edge/docs/forms/create-forms.md) Edge Delivery Services 사이트에 양식을 추가합니다.


>[!BEGINTABS]

>[!TAB 문서 기반 작성]

문서 기반 작성은 필수 기능을 갖춘 간단한 양식을 작성하는 데 적합한 다양한 옵션입니다. 텍스트 필드, 드롭다운 메뉴 및 라디오 버튼과 같은 다양한 입력 유형을 통합할 수 있으므로 사용자 데이터를 효과적으로 수집할 수 있습니다. 양식에 동적 동작을 추가하는 기본 버전의 규칙을 제공합니다. 문서 기반 작성의 주요 기능은 다음과 같습니다.

* **[HTML5 기반 양식 필드 구성 요소](/help/edge/docs/forms/form-components.md)**: AEM Forms Edge Delivery Services을 사용하면 HTML5를 기반으로 양식 구성 요소를 사용하여 사용자 친화적이고 대화형 양식을 만들 수 있습니다 [입력 유형](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">텍스트 영역</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">선택</a>, 및 <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">필드 세트</a>  요소. 이러한 구성 요소는 다양한 유형의 데이터 수집에 적합하며 특정 요구 사항에 맞게 쉽게 사용자 지정할 수 있습니다.

* **접근성**: 양식 블록의 필드에 액세스할 수 있습니다. 각 레이블은 해당 입력 요소와 연결되고 연결을 위해 ID가 자동으로 생성됩니다. 필드와 연결된 설명은 Aria-describedby 속성을 통해 연결됩니다. 표준 Tab/Shift + Tab 키를 사용하는 키보드 탐색이 지원됩니다.

* **[스타일링](/help/edge/docs/forms/style-theme-forms.md)**: 각 양식 필드에는 사용자 지정 CSS 또는 JavaScript 파일을 사용하여 쉽게 데코레이트할 수 있는 고정된 HTML 구조가 있습니다. CSS 및 JS의 타겟팅 필드에 대한 선택기는 유형 및 이름을 기반으로 제공됩니다. 표준화된 구조로 인해 새 선택기를 쉽게 만들고 양식의 스타일을 지정할 수 있습니다.

* **기본 규칙**: 사용자 입력 또는 사전 정의된 조건에 따라 필드 가시성, 유효성 검사 및 동작을 조정하는 논리를 쉽게 만들 수 있습니다. 규칙은 양식에 지능을 추가하는 유연하고 직관적인 방법을 제공하여 사용자 입력에 따라 원활하게 조정되도록 합니다.

* **유효성 검사**: 제출하기 전에 양식의 유효성을 검사하고 유효하지 않은 필드에 오류 메시지가 표시된 상태로 사용자에게 표시됩니다. 적응형 Forms 블록은 최신 브라우저에서 지원하는 모든 HTML 양식 유효성 검사를 지원하고 유효성 검사 스크립트, 파일 크기, 파일 유형, 전체 파일 크기 등과 같은 추가 유효성 검사 메커니즘을 제공합니다.

* **파일 업로드**: 양식에 파일 첨부 기능을 추가할 수 있습니다. 사용자의 문서, 이미지 또는 기타 파일을 수집해야 하는 경우에도 파일 업로드 기능을 사용하면 편리합니다. 사용자 지정 처리 옵션을 사용하면 특정 요구 사항에 맞게 파일 업로드 프로세스를 조정할 수 있습니다.

* **reCAPT차**: 기본 제공(OOTB) 지원을 통해 Google reCAPTCHA를 양식에 원활하게 통합할 수 있습니다. 원활하고 중단 없는 사용자 경험을 유지하면서 사기 활동, 스팸 및 남용으로부터 양식을 보호합니다. 적응형 Forms 블록은 reCaptcha V3 및 reCaptcha Enterprise를 지원합니다.

* **양식 제출 시 이메일 알림 보내기**: 번거로운 수동 후속 조치를 제거하고 양식 제출을 위한 내장된 이메일 자동화를 통해 적시에 통신할 수 있습니다. 이 통합 솔루션을 사용하면 웹 사이트에서 누군가 양식을 작성할 때마다 양식 데이터 전송을 포함하여 관련 당사자에게 쉽게 알릴 수 있습니다. 복잡한 구성이나 추가 도구가 필요 없으며 즉시 사용할 수 있습니다.

>[!TAB AEM 작성]

AEM 작성은 문서 기반 작성 이상의 추가 기능을 잠금 해제하여 보다 복잡하고 대화형 양식을 작성할 수 있도록 해 줍니다. 문서 기반 작성 기능 외에도 AEM 작성에서는 다음과 같은 추가 기능을 제공합니다.

* 고급 규칙: 양식 내에서 논리 기반 작업을 정의합니다. 규칙을 사용하여 양식 섹션을 조건부로 표시하거나 숨기고, 사용자 입력을 기반으로 필드를 미리 채우고, 다양한 유효성 검사를 수행하여 데이터 무결성을 보장할 수 있습니다.

* 서버측 확장성: 양식을 서버측 논리와 통합하여 양식의 기능을 확장합니다. 이를 통해 복잡한 계산을 수행하고, 외부 시스템과 상호 작용하고, 양식 내에서 사용자 작업을 기반으로 특정 작업을 자동화할 수 있습니다.
* 워크플로우 및 데이터 관리 간소화: AEM의 강력한 기능을 활용하여 다음과 같은 작업을 수행할 수 있습니다.
   * AEM 편집기를 사용하여 사용자에게 친숙한 양식을 디자인할 수 있습니다.
   * 제출된 데이터의 안전하고 변조가 불가능한 보관을 위해 &quot;기록 문서&quot;를 생성합니다.
   * 원활하고 안전한 서명 환경을 위해 Adobe Sign을 사용한 전자 서명을 용이하게 합니다.
   * AEM 워크플로우를 통해 비즈니스 프로세스를 자동화하여 양식 제출을 기반으로 작업을 트리거합니다.
   * 다양한 데이터 소스와 손쉽게 통합되므로 원활한 데이터 흐름 및 교환이 가능합니다.

>[!ENDTABS]








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
            <br><b style="margin-top: 5px;">Google 시트 또는 Microsoft Excel을 사용하여 양식 만들기</b>
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
