---
title: AEM Forms용 Edge Delivery Services 개요
description: AEM Forms용 Edge Delivery Services는 최고의 성능을 발휘하도록 구축되어 데이터 수집 및 사용자 참여를 간소화하는 미래를 구상할 수 있도록 지원합니다.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 67fe933807f8a1bca681a6bcee7164f7c117bcac
workflow-type: tm+mt
source-wordcount: '1874'
ht-degree: 100%

---


# AEM Edge Delivery Services의 Forms 시작하기

<span class="preview"> 이는 프리릴리스 기능이고 [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features)을 통해 액세스할 수 있습니다. </span>

이 안내서는 Adobe Experience Manager(AEM) Edge Delivery Services(EDS)를 사용하여 양식을 이해하고 구현하는 데 도움이 됩니다. 간단한 연락처 양식부터 복잡한 데이터 수집 도구까지 이 페이지에서 해당 옵션을 안내합니다.

## Edge Delivery Services의 양식 이해

Edge Delivery Services는 양식을 포함한 웹 콘텐츠를 탁월한 성능과 민첩성으로 제공하는 Adobe의 최신 솔루션입니다. Edge Delivery Services를 양식에 사용하면 다음과 같은 이점이 있습니다.

* **더욱 빠른 경험 제공:** 양식은 사용자와 가까운 글로벌 에지 서버 네트워크(CDN)에서 제공되므로 매우 빠르게 로드됩니다. 이를 통해 사용자 만족도를 향상시키고 양식 완료율을 높일 수 있습니다.
* **더욱 간편한 양식 업데이트:** Edge Delivery Services 접근 방식을 사용하면 개발 주기를 단축하고 콘텐츠를 업데이트할 수 있으므로 양식을 빠르게 조정할 수 있습니다.
* **현대적인 반응형 양식:** 어떤 디바이스에서든 완벽하고 원활하게 작동하는 양식을 만드십시오.
* **확장성과 안정성의 이점:** 양식은 기본 에지 인프라만큼이나 견고하고 확장 가능할 것입니다.

이 안내서는 다음 내용을 다룹니다.

* Edge Delivery Sites에서 양식을 만드는(작성하는) 다양한 방법을 설명합니다.
* 사용자가 양식을 제출한(제출 액션) 후에 발생하는 일을 구성하는 방법을 보여 줍니다.
* 특정 요구 사항과 팀 기술에 가장 적합한 방법을 선택하도록 도와줍니다.
* 아키텍처 다이어그램과 모범 사례를 제공합니다.

## 알아야 할 핵심 용어

* **Edge Delivery Services(EDS):** CDN을 통해 AEM 콘텐츠를 제공하기 위한 Adobe의 성능 우선 아키텍처. Franklin 프로젝트라고도 합니다.
* **AEM Forms:** 양식 만들기, 관리 및 처리를 위한 Adobe의 솔루션.
* **Universal Editor(UE):** 양식을 포함한 AEM 콘텐츠용 시각적 WYSIWYG 편집기.
* **문서 기반 작성:** Microsoft Word 또는 Google Docs/Sheets를 사용하여 양식 만들기.
* **문서 작성(DA):** Edge Delivery Services를 위한 콘텐츠(양식을 호스팅할 수 있는 페이지 포함)를 작성하는 Adobe 호스팅 서비스.
* **Forms 제출 서비스(FSS):** 스프레드시트나 이메일로 양식 데이터를 간편하게 전송할 수 있는 Adobe 서비스.
* **AEM Publish 인스턴스:** 복잡한 양식 제출을 처리할 수 있는 라이브 AEM 환경.
* **CORS(원본 간 리소스 공유):** 다양한 도메인의 양식을 임베드할 때 구성이 필요한 브라우저 보안 기능.
* **CDN(콘텐츠 전송 네트워크):** 지리적 위치를 기반으로 사용자에게 웹 콘텐츠를 신속하게 제공하는 서버 네트워크.


**Edge Delivery Services 양식 상호 작용의 개념 다이어그램**

<!--  
```mermaid
graph LR
    User[User on Device] >|Interacts| EdgeForm[Edge-Delivered Form Page]
    EdgeForm >|Loads Instantly| CDN[CDN Edge Server]
    CDN >|Serves Content| User
    EdgeForm >|Submits Data| Backend[Backend Processing - e.g. Forms Submission Service / AEM Publish]
    style User fill:#f9f,stroke:#333,stroke-width:2px
    style EdgeForm fill:#ccf,stroke:#333,stroke-width:2px
    style CDN fill:#9cf,stroke:#333,stroke-width:2px
    style Backend fill:#fca,stroke:#333,stroke-width:2px
``` -->

![양식 상호작용](/help/forms/assets/eds-form-interaction.png)
이 다이어그램은 CDN을 통해 신속하게 전달된 양식과 사용자가 상호작용하는 모습을 보여 줍니다. 제출된 데이터는 백엔드 시스템에 의해 처리됩니다.

## Edge에서 양식은 어떻게 작동합니까?

EDS를 사용하면 웹 사이트 콘텐츠(양식 구조 포함)를 AEM as a Cloud Service, SharePoint, Google Drive 또는 문서 작성(DA) 서비스와 같은 다양한 소스에서 가져올 수 있습니다. 이 콘텐츠는 이후 글로벌 CDN에 게시됩니다. 사용자가 사이트를 방문하면 가장 가까운 CDN 에지 서버에서 직접 콘텐츠를 제공해 최대 속도를 보장합니다.

<!--*   **Where AEM Forms Fit In**
    Forms in an EDS architecture are designed to be:
    *   **Fast Loading:** Form structures are often simple HTML rendered client-side.
    *   **Decoupled:** The visual part of the form (frontend) is separate from where the data goes after submission (backend).
    *   **Flexible to Create:** You have different tools to build your forms.
    *   **Configurable for Submission:** You can send data to simple services or powerful AEM backends.-->

**Forms를 통해 간소화된 Edge Delivery Services 아키텍처**

<!--
```mermaid
    graph TD
        UserStart[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User on Device] >|Interacts| EdgeForm[Edge-Delivered Form Page]
        EdgeForm >|Loads Instantly| CDN[CDN Edge Server]
        CDN >|Serves Content| UserEnd[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User on Device]
        EdgeForm >|Submits Data| Backend[Backend Processing - Form Submission Service / AEM Publish]

        style UserStart fill:#f9f,stroke:#333,stroke-width:2px
        style UserEnd fill:#f9f,stroke:#333,stroke-width:2px
        style EdgeForm fill:#ccf,stroke:#333,stroke-width:2px
        style CDN fill:#9cf,stroke:#333,stroke-width:2px
        style Backend fill:#fca,stroke:#333,stroke-width:2px
``` -->

![아키텍처](/help/forms/assets/eds-simplified-architecture.png)
이 다이어그램은 양식이 작성 시스템에서 정의되고, 에지에 게시되어 사용자에게 제공되고, 제출된 데이터는 백엔드에서 처리되는 여정을 보여 줍니다.

## 양식 작성 방법 선택

Edge Delivery Services 사이트에 맞는 양식을 만드는 데는 세 가지 주요 방법이 있습니다. 팀의 기술, 양식의 복잡성, 프로젝트의 필요성에 따라 선택이 달라집니다.

### 어떤 작정 접근 방식이 적합할까요?

다음 의사 결정 트리를 사용하여 선택합니다.

**양식 작성 의사 결정 트리**
<!--    
```mermaid
    graph TD
        A{Start: I need to create a form for an Edge Delivery Services site} > B{What are my team's primary content creation tools & skills?}
        B -- "We mainly use Word / Google Docs / Sheets" > C{How complex is the form and where does the data need to go?}
        B -- "We use AEM and prefer visual tools (Marketers or Designers)" > D[Use Universal Editor - WYSIWYG]
        B -- "Our site content is managed in Document Authoring (DA)" > E[Use Document Authoring - Embed Forms]
        C -- "Simple to moderate form, data to a spreadsheet or email" > F[Use Document-Based Authoring]
        C -- "More complex logic or needs AEM backend integration" > D
        E > G[Create form using Document-Based Authoring or Universal Editor, then embed in your DA page]

        style A fill:#f9f,stroke:#333,stroke-width:2px
        style F fill:#ccf,stroke:#333,stroke-width:2px
        style D fill:#ccf,stroke:#333,stroke-width:2px
        style G fill:#ccf,stroke:#333,stroke-width:2px
``` -->

![올바른 플랫폼 선택](/help/forms/assets/eds-authoring-selection.png)

이 의사 결정 트리는 팀과 양식의 필요에 따라 작성 방법을 선택하는 데 도움이 됩니다.

### 문서를 사용하여 양식 만들기 (Word/Google Docs)

이 방법은 [팀이 Microsoft Word 또는 Google Docs/Sheets에 익숙하다면 신속하게 양식을 작성](/help/edge/docs/forms/create-forms.md)하는 데 매우 유용합니다.

**작동 방식: 문서에서 웹 양식으로**

특수 테이블 형식이나 “양식 블록”을 사용하여 Word 문서나 Google Sheet에서 양식의 필드, 레이블 및 유형을 직접 정의합니다. 이 문서를 게시하면 Edge Delivery Services가 자동으로 해당 문서를 사용자가 사이트에서 상호 작용할 수 있는 웹 지원 HTML 양식으로 변환합니다.

**기능 및 특징**

* 익숙한 도구를 사용하여 작성: Word, Google Docs, Google Sheets.
* 필드 정의: 텍스트, 이메일, 드롭다운, 체크박스, 라디오 버튼, 텍스트 영역 입력.
* 레이블, 플레이스홀더, 도움말 메시지 추가.
* 기본적인 유효성 검사 규칙 설정: 필수 필드, 이메일 형식.
* 스팸 방지를 위한 reCAPTCHA 통합.
* 파일 업로드 허용.
* 즉시 게시: 문서의 변경 사항이 라이브 사이트에 빠르게 반영.
* 사용자 정의 코드로 확장: 고급 사용자는 GitHub을 통해 사용자 정의 양식 구성 요소와 스타일 추가.

**고려 사항**

* 팀이 정기적으로 Word 또는 Google Docs/Sheets를 콘텐츠에 사용합니다.
* 간단한 것부터 적당히 복잡한 형태까지 빠르게 만들어야 합니다.
* 최소한의 설정으로 양식 데이터를 스프레드시트나 이메일 주소로 직접 보내고자 합니다.

**제출 방식 (주로 Forms 제출 서비스)**

이렇게 생성된 양식은 일반적으로 [데이터를 AEM Forms 제출 서비스로 전송](/help/forms/forms-submission-service.md)합니다. Google Sheet, OneDrive/SharePoint의 Excel 파일 또는 이메일로 데이터를 전송하도록 (종종 소스 문서 자체에서) 설정할 수 있습니다.

**문서 기반 작성의 개념**
<!--    
```mermaid
    graph LR
        subgraph Authoring["You define your form in a Google Sheet or Word Document"]
        Sheet[Spreadsheet or Document with field definitions:\nField Name - Type - Label\nemail - email - Email Address\nmessage - textarea - Your Message]
    end

        Sheet >|Edge Delivery Services automatically converts it| JSON[Internal Form Definition as JSON]
    JSON >|A 'Form Block' on your page renders it as| HTMLForm[Live HTML Form on Your Website]

        style Sheet fill:#e6ffe6,stroke:#333
        style JSON fill:#e6e6ff,stroke:#333
        style HTMLForm fill:#ffe6e6,stroke:#333
```-->

![문서 기반](/help/forms/assets/eds-doc-based.png)
이 다이어그램은 문서에 정의된 양식이 어떻게 라이브 웹 양식이 되는지 보여 줍니다.

### Universal Editor를 사용한 시각적 양식 작성

[Universal Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)는 웹 브라우저에서 직접 양식을 작성할 수 있는 현대적인 드래그 앤 드롭 인터페이스를 제공합니다.

**작동 방식: 드래그 앤 드롭 양식 작성**

시각적 인터페이스를 사용하여 양식 구성 요소(입력 필드, 버튼, 드롭다운 등)를 페이지로 끌어다 놓습니다. 그런 다음 속성 패널을 통해 각 구성 요소의 속성(레이블, 유효성 검사 등)을 구성할 수 있습니다. Universal Editor는 양식을 실시간으로 미리 보여 줍니다.

**기능 및 특징**

* 사전 설치된 구성 요소 라이브러리를 사용하여 시각적 양식을 만듭니다.
* 실시간 유효성 검사 및 비즈니스 로직을 구성합니다(예: 선택에 따라 필드 표시/숨기기).
* 다양한 디바이스(데스크탑, 모바일)에 대해 실시간 미리보기를 확인합니다.
* 콘텐츠 조각, AEM 워크플로, 사용자 권한과 같은 AEM 기능과 통합할 수 있습니다.
* 프롬프트를 사용하여 양식을 만들거나 편집하기 위한 AI 지원을 받으려면 “경험 빌더”를 사용합니다.

**고려 사항**

* 조건 논리, 다단계 패널 또는 개인화가 포함된 복잡한 양식을 작성해야 합니다.
* 팀(예: 마케터, 비즈니스 사용자)이 시각적 도구를 선호합니다.
* 거버넌스, 워크플로 또는 양식에 AEM 자산을 사용하려면 AEM as a Cloud Service와 강력한 통합이 필요합니다.

**제출 작동 방식 (Forms 제출 서비스 또는 AEM Publish)**

Universal Editor로 작성한 양식은 다음과 같은 기능을 제공합니다.

* (스프레드시트나 이메일로 데이터를 전송하기 위해) 간단한[Forms 제출 서비스](/help/forms/forms-submission-service.md)를 사용합니다.
* AEM Publish 인스턴스에 데이터를 제출하여 (AEM 워크플로 시작, 양식 데이터 모델 사용 또는 다른 엔터프라이즈 시스템과의 통합과 같은) 고급 처리를 수행합니다.

**Universal Editor 개념**

<!--    
```mermaid
    graph TD
    subgraph UE_Interface["Universal Editor Interface in your Browser"]
        Toolbar[Editor Toolbar and Asset Finder]
        Canvas[Your Page with the Form Being Built]
        ComponentPalette[Available Form Components:\nInput / Dropdown / Button\nDrag and drop]
        PropertiesPanel[Configure Selected Component:\nLabel / Validation / Rules]
    end
    ComponentPalette >|Drag & Drop onto| Canvas
    Canvas >|Select a component to edit its| PropertiesPanel
    UE_Interface >|Creates| RenderedForm[Live Form on Your Website]

    style UE_Interface fill:#f0f8ff,stroke:#333
    style RenderedForm fill:#ffe6e6,stroke:#333
```-->

![Universal Editor](/help/forms/assets/eds-ue-based.png)

이 다이어그램은 양식 작성에 사용되는 Universal Editor의 주요 부분을 보여 줍니다.

### 문서 작성(DA)을 통한 양식 사용

[문서 작성(DA)](https://www.aem.live/developer/da-tutorial)은 Edge Delivery Services를 통해 제공되는 주요 웹 사이트 콘텐츠(페이지, 문서)를 만들고 관리하기 위한 Adobe 호스팅 서비스입니다. Edge Delivery Services 소스 콘텐츠에 SharePoint 또는 Google Drive를 사용하는 대신 사용할 수 있습니다.

**Edge Delivery Services 콘텐츠를 위한 문서 작성(DA) 이해**

문서 저작은 Adobe의 디자인 시스템(Spectrum)과 AEM의 문서 모델(블록, 섹션)을 사용하여 엔터프라이즈급 작성 환경을 제공합니다. EDS의 구조화된 콘텐츠 관리를 위해 설계되었습니다.

**DA가 양식 처리 방식(직접 작성이 아닌 임베드)**

DA 자체는 **양식을 처음부터 구축하는 도구가 아닙니다**. 대신 DA를 사용하여 웹 페이지를 만든 다음 (문서 기반 작성 또는 Universal Editor를 사용하여 만든) 양식을 해당 DA 작성 페이지에 *임베드*&#x200B;합니다.

**DA 페이지에 양식을 임베드하는 단계**

1. **양식 만들기:** 다음 중 하나를 사용하여 양식을 작성합니다.
   * 문서 기반 작성 (Word/Google Docs)
   * Universal Editor

1. **양식 게시:** 이 양식이 게시되고 자체 Edge Delivery URL(예: `https://your-eds-project.hlx.page/forms/contact-us`)을 통해 액세스할 수 있는지 확인합니다.
1. **DA에서 페이지 작성:** 문서 작성에서 양식을 표시할 페이지를 만들거나 편집합니다.
1. **양식 임베드:** DA 페이지 내의 특정 “블록” 또는 구성 요소를 사용하여 URL에서 양식을 참조하고 임베드합니다. 그러면 DA 페이지가 외부에서 생성된 양식을 가져와서 표시합니다.

**임베드된 양식을 사용한 문서 작성**
<!--
```mermaid
    graph TD
    subgraph FormCreation["1. Create Form using other methods"]
        UE_Form[Universal Editor Form] >|Published to| FormLocation[Form lives at its own Edge Delivery Services URL:\nfor example: /forms/my-contact-form]
        DocBased_Form[Document-Based Form] >|Published to| FormLocation
    end

    subgraph DA_Content["2. Author Page in Document Authoring"]
        DAPage[Your Web Page Authored in DA\nExample: /main-site/landing-page]
        EmbedBlock[On DA Page, add 'Embed Form' Block\nPoints to /forms/my-contact-form]
    end

    DAPage > EmbedBlock
    User[User visits your DA Page] > DAPage
    EmbedBlock >|DA Page fetches and displays| FormLocation[The Form appears on your DA Page]

    style FormCreation fill:#e6ffe6,stroke:#333
    style DA_Content fill:#ffe6cc,stroke:#333
    style FormLocation fill:#ccf,stroke:#333
```-->

![문서 작성](/help/forms/assets/eds-da-based.png)

이 다이어그램은 먼저 UE 또는 Docs를 사용하여 양식을 만든 다음 문서 작성에서 작성한 페이지에 임베드하는 방식을 보여 줍니다.


### 작성 옵션 비교

| 기준 | 문서 기반 작성 | Universal Editor (WYSIWYG) | 문서 작성(DA)의 양식 |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **기본 작성 도구** | Word/Google Docs/Sheets | 브라우저 (AEM Universal Editor) | N/A (양식이 *임베드됨*) |
| **팀 기술 수준** | 문서 편집기에 익숙함 | 시각적 웹 도구에 익숙함 | 페이지 콘텐츠에 DA 사용 |
| **일반적인 양식 복잡성** | 단순부터 중간 | 중간부터 복잡, 엔터프라이즈급 | 임베드된 양식에 따라 다름 |
| **제출 옵션 1 (단순)** | Forms 제출 서비스 (시트/이메일) | Forms 제출 서비스 (시트/이메일) | 임베드된 양식의 설정을 따름 |
| **제출 옵션 2 (고급)** | 해당 사항 없음 | AEM Publish (워크플로, FDM 등) | 임베드된 양식의 설정을 따름 |
| **AEM 백엔드 통합** | 최소 | 높음 (AEM Publish 제출 포함) | 간접적, 임베드된 Universal Editor 양식을 통해 |
| **적합한 대상...** | 콘텐츠 팀이 간단한 양식의 신속한 생성, 빠른 데이터 캡처. | 마케터, 시각적 제어, 복잡한 양식 또는 긴밀한 AEM 통합이 필요한 비즈니스 사용자. | DA에서 주요 콘텐츠를 관리하고 다른 소스의 양식이 필요한 Sites. |

**향상된 의사 결정 트리**
<!--
```mermaid
    graph TD
    A{Start Here: I need a form on my Edge Delivery Services Site} > B{What's my team's main authoring tool & skill for form content?};
    B -- "Word/Google Docs" > C{How complex is the form & data destination?};
    C -- "Simple form, data to Sheet/Email" > Sol1[CHOOSE: Document-Based Authoring + Forms Submission Service];
    C -- "Needs more logic OR AEM backend\nlike Workflow or FDM" > Sol2[CONSIDER: Can Universal Editor meet this need better?];

    B -- "AEM User / Visual Editor needed\nMarketer or Designer" > D{Where does the form data need to go?};
    D -- "Simple - to Sheet/Email" > Sol3[CHOOSE: Universal Editor + Forms Submission Service];
    D -- "Advanced - AEM Workflow, FDM,\n3rd Party via AEM" > Sol4[CHOOSE: Universal Editor + AEM Publish Submissions\nRequires additional setup];

    B -- "Our main site content is in Document Authoring (DA)" > Sol5[STRATEGY: Author form using Sol1, Sol2, Sol3 or Sol4 first\nTHEN embed that form into your DA page];

    A > F{Will this form be embedded or fetched from another site or domain?};
    F -- "Yes" > G[IMPORTANT: Configure CORS on the site hosting the form.\nEnsure any form JavaScript blocks are available where the form is displayed];

    style Sol1 fill:#90ee90,stroke:#333
    style Sol2 fill:#fffacd,stroke:#333
    style Sol3 fill:#90ee90,stroke:#333
    style Sol4 fill:#90ee90,stroke:#333
    style Sol5 fill:#add8e6,stroke:#333
    style G fill:#ffb6c1,stroke:#333
```-->

![의사 결정 트리](/help/forms/assets/eds-enhanced-decision.png)

## 작성 방법의 기능 비교

다음 표는 다양한 AEM 양식 작성 방법의 주요 기능을 자세히 비교하여 요구 사항에 가장 적합한 방법을 선택하는 데 도움을 줍니다.&#x200B;

| **기능** | **Universal Editor (WYSIWYG)** | **문서 기반 작성** | **문서 작성 (DA)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Sites를 통한 통합 컴포지션** | ✅ |                              | ✅ (임베드된 양식 포함) |
| **양식 임베드 지원** | ✅ | ✅ | ✅ (Universal Editor 또는 Docs에서 임베드) |
| **규칙 (동적 동작)** | 사용자 정의 함수가 포함된 고급 규칙 편집기 | 제한적: 표시/숨기기, 값 계산, 사용자 정의 함수 | 임베드된 양식에 따라 다름 |
| **첨부 파일 지원** | ✅ | ℹ️ (얼리 액세스) | 임베드된 양식에 따라 다름 |
| **CAPTCHA 지원** | reCAPTCHA Enterprise | reCAPTCHA Enterprise | 임베드된 양식에 따라 다름 |
| **제출 기능** | REST, 이메일, FDM, 워크플로, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion(EA) | 스프레드시트만 | 임베드된 양식의 설정을 따름 |
| **데이터 스키마** | FDM, 사용자 정의 | 사용자 정의 | 임베드된 양식 기준 |
| **미리 채우기** | 💡 (마법사 사용) | ✅ | 임베드된 양식에 따라 다름 |
| **조각** | ✅ | ✅ | 임베드된 양식에 따라 다름 |
| **시각적 규칙 편집기** | ✅ |                              |                              |
| **현지화** | 💡 (Sites 사용) | ℹ️ (Excel/Sheets 매뉴얼) | 임베드된 양식에 따라 다름 |
| **데이터 스키마 (데이터 트리)** | 💡 (UI 확장 기능 사용) |                              |                              |
| **템플릿 지원** | 초기 콘텐츠 전용 |                              |                              |
| **포털** |                               |                              |                              |
| **테마** | ℹ️ (프로젝트 수준에서) | ℹ️ (프로젝트 수준에서) | ℹ️ (호스팅 사이트 기준) |
| **사용자 정의 구성 요소** | ✅ | ✅ | ✅ (임베드된 구성 요소가 지원하는 경우) |
| **OOTB 및 사용자 정의 함수** | ✅ | ✅ | ✅ (임베드된 양식) |
| **조각 참조** |                               |                              |                              |
| **Sign 통합** |                               |                              |                              |
| **실험** | ✅ | ✅ | 임베드된 컨텍스트에 따라 다름 |
| **Workfront를 통한 작업 관리** | ✅ |                              |                              |
| **개인화 확장 기능** | 💡 |                              |                              |
| **편집기 사용자 정의** | ✅ (UI 확장 기능 사용) |                              |                              |
| **제출 액션** | ✅ | 스프레드시트만 | 임베드된 양식 기준 |

<!--

## Best Practices for Creating Forms

Building great forms goes beyond just the technology. Here's how to ensure your forms are user-friendly and achieve their goals:

* **Designing User-Friendly and Accessible Forms**

  *   **Use Clear, Visible Labels:** Every form field needs a `<label>`. Don't rely only on placeholder text (text inside the input field), as it disappears when users type and is bad for accessibility.
        *   *Good:* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
        *   *Bad:* `<input type="email" placeholder="Email Address">`
  *   **Keep it Simple:** Use standard HTML input types (`<input type="date">`, `<input type="tel">`) where possible. They often have better mobile support and accessibility than complex custom widgets.
  *   **Logical Order and Grouping:** Arrange fields in a way that makes sense to the user. Group related fields together using `<fieldset>` and `<legend>`.
  *   **Provide Clear Instructions:** For any fields that might be confusing, offer concise help text or tooltips.
  *   **Keyboard Navigation:** Ensure users can navigate through your entire form using only the keyboard (Tab, Shift+Tab, Enter, Spacebar).
  *   **Error Handling:** Make errors obvious and easy to correct. Display error messages next to the relevant field and explain what needs to be fixed.

* **Ensuring Your Forms Load Quickly and Are Visible**

  *   **Place Forms Prominently:** If a form is important, make sure users can see it easily without too much scrolling ("above the fold" if possible). Adobe's research shows many forms get low interaction because they are hidden.
  *   **Optimize Assets:** Keep any custom JavaScript or CSS for your forms as small as possible to ensure fast load times. Edge Delivery Services helps with the base page load, but heavy form scripts can still slow things down.

* **Handling User Data Responsibly**
  *   **Ask Only What You Need:** The less Personal Identifiable Information (PII) you ask for, the better. Every field is a potential reason for a user to abandon the form.
  *   **Be Transparent:** Clearly explain *why* you need certain information and *how it will be used*. Link to your privacy policy. This builds trust.

* **Improving User Experience: Captcha Alternatives**

  * **Rethink Visible Captchas:** Those "type the wavy text" or "click all the traffic lights" tests can be very frustrating for users, especially those with disabilities, and often lead to high drop-off rates.

*   **Consider Alternatives:**
    *   **Honeypot Fields:** Add a hidden field that only bots would fill out. If it has data, the submission is likely spam.
    *   **Time-Based Checks:** Measure how quickly a form is submitted. Submissions that are too fast are often bots.
    *   **Invisible reCAPTCHA (v3):** This Google service analyzes user behavior in the background and only presents a challenge if the user seems suspicious. This is often a much better user experience.

**Form Design Do's and Don'ts**

```mermaid
    graph LR
subgraph GoodFormUX [Do ✅ - For Better Forms]
    direction LR
    ClearLabels[Use Visible <label> Tags for All Fields]
    SimpleInputs[Prefer Standard HTML Input Types]
    KeyboardNav[Ensure Full Keyboard Navigation]
    ClearErrors[Show Clear, Actionable Error Messages]
    MinimalPII[Ask Only for Necessary Information]
    TransparentUse[Explain How Data is Used - Privacy Info]
    InvisibleCaptcha[Use Invisible or Behavioral CAPTCHA]
    ProminentPlacement[Make Form Easy to Find on Page]
end

subgraph BadFormUX [Don't ❌ - Avoid These]
    direction LR
    PlaceholderOnly[Only Use Placeholder Text for Labels]
    ComplexWidgets[Use Overly Complex Custom Widgets]
    PoorErrors[Vague or Missing Error Messages]
    ExcessivePII[Request Excessive Personal Data]
    VisibleHardCaptcha[Use Hard-to-Solve Visible CAPTCHAs]
    HiddenForm[Hide the Form Deep in the Page]
end

style GoodFormUX fill:#e6ffe6,stroke:#333
style BadFormUX fill:#ffe6e6,stroke:#333
```

## Quick Decision Guide: Choosing the Right Form Strategy

Let's bring it all together to help you decide on the best approach for your forms.

*   **Matching Form Features to Your Project Goals**
    *   **For speed and simplicity with basic data capture (to spreadsheets/email):** Document-Based Authoring with the Forms Submission Service is often your fastest route.
    *   **For visually rich forms with potential for AEM backend integration:** Universal Editor is your tool. You can start with the Forms Submission Service for simple needs and scale to full AEM Publish submissions for complex workflows.
    *   **If your site content is managed in Document Authoring (DA):** You'll create forms using one of the above methods and then embed them into your DA pages. The submission logic will be tied to how the original embedded form was configured.-->

배운 내용을 바탕으로 앞으로 나아갈 수 있는 방법은 다음과 같습니다.

[제출 전략 선택](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) 프로젝트에 스프레드시트/이메일 출력에 적합한 Forms 제출 서비스의 간편함이 필요한지, 아니면 AEM Publish 제출 액션이 제공하는 유연성과 백엔드 통합이 필요한지 결정합니다.

효과적이고 접근성이 뛰어나며 사용자 친화적인 양식을 디자인하는 방법은 [양식 만들기 모범 사례](/help/edge/docs/forms/universal-editor/best-pratices-eds-forms.md) 문서를 참조하십시오.

## 다음 단계

이 안내서는 AEM Edge Delivery Services에서 양식 사용에 대한 개요를 제공합니다. 특정 구성에 대한 자세한 단계별 지침은 공식 Adobe Experience Manager 설명서를 참조하십시오.

* [Edge Delivery Services Forms가 포함된 문서 기반 작성](/help/edge/docs/forms/tutorial.md)
* [Edge Delivery Services Forms가 포함된 Universal Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [문서 작성(DA) 및 콘텐츠 임베드](https://www.aem.live/developer/da-tutorial)
* [AEM Forms 제출 서비스](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)


<!-- 
# Edge Delivery Services for AEM Forms
 

Edge Delivery Services for AEM Forms is a composable set of services that enables a rapid development environment where authors can update, publish, and launch new forms rapidly. These services deliver exceptional and high impact forms experiences that drive engagement and conversions. These forms experiences are easy to author and develop.

These services enable you to:

* **Create enrolment experiences with tools of your choice:** Increase authoring efficiency by decoupling content sources. Out of the box you can use Document-based Authoring (Microsoft SharePoint or Google Drive), WYSIWYG Authoring (Universal Editor or Adaptive Forms Editor). You can work with multiple content sources on the same forms site and use your preferred authoring tools, such as Microsoft Excel, Google Sheets, Universal Editor, or Adaptive Forms Editor.

* **Deliver exceptional Digital Enrolment experiences:** Deliver Digital Enrolment experiences that load and render quickly and continuously monitor your forms performance through Operational Telemetry. Faster loading times and optimized user experience contribute to higher form completion and conversion rates. 

* **Use developer friendly toolset:** Edge Delivery Services for AEM Forms
 uses plain HTML, modern CSS, and vanilla JavaScript to create exceptional experiences, avoiding the steep learning curve of a specific framework. A developer with basic web development skills can customize and easily build form components and experiences. There is no need to wait for a pipeline to run, just check-in your code into GitHub and your changes are live.

## Edge Delivery Services for AEM Forms Overview {#edge-overview}

Edge Delivery Services for AEM Forms allows for a high degree of flexibility in how you author forms on your website. You can author content and forms with [WYSIWYG Authoring](/help/forms/creating-adaptive-form-core-components.md) as well as [Document-based Authoring](/help/edge/docs/forms/create-forms.md). Edge Delivery Services for AEM Forms
 provide a forms block, known as [Adaptive Forms Block](/help/edge/docs/forms/create-forms.md) to add a form to your Edge Delivery Services site.

For example, you author forms directly in Microsoft Excel or Google Sheets and these spreadsheets are transformed into forms for your website. Any new form or form content, such as a new form field, is instantly available on your website without requiring a rebuild process.

The following diagram illustrates how you can edit forms in Microsoft Excel or Google Sheets (Document-based Authoring) and publish to Edge Delivery Services. It also shows the AEM publishing method using the WYSIWYG Authoring (Universal Editor or Adaptive Forms Editor).

![Publish to Edge Delivery Services and AEM](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)

Edge Delivery Services for AEM Forms uses GitHub so customers can manage and deploy code directly from their GitHub repository. For example, you can write forms in either [Google Sheets](/help/edge/docs/forms/create-forms.md) or [Microsoft Excel](/help/edge/docs/forms/create-forms.md) and the components of your forms can be developed by using CSS and JavaScript in a GitHub repository.

When your forms are ready, you can use the [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), a chrome browser extension, to preview and publish content updates.

![Install AEM SideKick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

The choice between the [Document-based Authoring ](#document-based-authoring-features) and [WYSIWYG Authoring](#wysiwyg-authoring-features) depends on your specific requirements:

* For simple forms that just collect basic information with a few fields (think contact us forms, lead generation forms, or service request forms), and where you need quick data connectivity using a spreadsheet, the [Document-based Authoring](#document-based-authoring-features) is a good fit. You can build these forms like you would build a document in Google Sheets or Microsoft Excel. 

* For complex forms, like forms requiring multiple panels, complex rules and business logic, data manipulation, integration with external systems, or streamlined workflows using AEM features, then [WYSIWYG Authoring](#wysiwyg-authoring-features) is a better option. 


### Key Features of Document-based Authoring and WYSIWYG Authoring

Document-based Authoring offers a basic set of features and WYSIWYG Authoring unlocks additional capabilities beyond the Document-based Authoring, empowering you to build more complex and interactive forms. The key features of both Document-based Authoring and WYSIWYG Authoring are:

#### Document-based Authoring features

Document-based Authoring  allows you to create forms using familiar tools like Microsoft Excel or Google Sheets. These forms offer the following functionalities:

* Accessible components for a user-friendly experience.
* Standardized HTML structure for consistent rendering.
* Rules and validations to ensure data accuracy.
* File attachment options for collecting additional information.
* Google reCAPTCHA integration for spam protection.
* Ability to create custom form components for specific needs.
* Submit form data directly to Microsoft Excel or Google Sheets or email addresses.
* Monitor your forms performance through Operational Telemetry

#### WYSIWYG Authoring features

WYSIWYG Authoring provides WYSIWYG interfaces (Universal Editor and Adaptive Forms Editor) for building forms and offers all the capabilities of Document-based Authoring, plus a wide range of additional features:

* Advanced rules editor for creating complex logic.
* Server-side extensibility for custom functionalities.
* WYSIWYG editing experience for easy form creation and visualization.
* Document of record functionality to create tamper-proof archives of submitted data.
* Integration with Adobe Sign for electronic signatures.
* Integration with Adobe Workfront Fusion to triggering Adobe Workfront Fusion scenarios upon form submission.
* Integration with various data sources for pre-populating forms and submitting data.
* Form Data Model (FDM) for defining data structure and interactions with various data sources.
* Ability to choose from multiple submit actions for handling form submissions, including submitting data to Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, many more data sources.

The all above features are also available via Adaptive Forms Editor. 

In essence, WYSIWYG Authoring (Universal Editor and [Adaptive Forms Editor](/help/forms/creating-adaptive-form-core-components.md)) builds upon the foundation of [Document-based Authoring](/help/edge/docs/forms/create-forms.md), providing a more advanced toolkit for creating and managing complex forms. 

>[!NOTE]
>
>
> The WYSIWYG Authoring capability is available under the early-adopter program. If you are interested, send a quick email from your work address to aem-forms-ea@adobe.com to request access to the capability.

### Edge Delivery Services for AEM Forms

: Authoring, Publishing, and Submission of Forms  

The following diagrams illustrate the process of creating, publishing, and submitting forms using Document-based Authoring and WYSIWYG Authoring.

![Document-based Authoring](/help/edge/assets/document-based-authoring-workflow.png)

![WYSIWYG Authoring](/help/edge/assets/wysiwyg-authoring-workflow.png)

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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using Edge Delivery Services forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an Edge Delivery Services form" style="border-radius: 5px;"> </b>
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
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
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
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->
