---
title: AEM Forms용 Edge Delivery Services 개요
description: 최고 성능을 위해 구축된 AEM Forms용 Edge Delivery Services을 통해 간소화된 데이터 수집 및 사용자 참여의 미래를 구상할 수 있습니다.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: bca160763fdd1e96f1350ac74eb76ff7c26ac00b
workflow-type: tm+mt
source-wordcount: '1874'
ht-degree: 7%

---


# AEM Edge Delivery Services에서 Forms 시작하기

<span class="preview"> 이는 프리릴리스 기능이고 [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features)을 통해 액세스할 수 있습니다. </span>

이 안내서는 Adobe Experience Manager(AEM) Edge Delivery Services(EDS)를 사용하여 양식을 이해하고 구현하는 데 도움이 됩니다. 간단한 연락처 양식을 만들거나 복잡한 데이터 수집 도구를 만드는 경우 이 페이지에서는 선택 사항을 안내합니다.

## Edge Delivery Services의 Forms 이해

Edge Delivery Services은 양식을 비롯한 웹 컨텐츠를 탁월한 성능과 민첩성으로 제공하기 위한 Adobe의 최신 솔루션입니다. 양식에 Edge Delivery Services을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* **더 빠른 환경 제공:** Forms은 사용자와 가까운 CDN(Edge Server)의 글로벌 네트워크에서 제공되므로 매우 빠르게 로드됩니다. 이를 통해 사용자 만족도가 향상되고 양식 완료율이 높아질 수 있다.
* **보다 손쉽게 Forms 업데이트:** Edge Delivery Services 접근 방식을 사용하면 개발 주기와 콘텐츠 업데이트가 빨라져 양식을 빠르게 조정할 수 있습니다.
* **최신 반응형 Forms 빌드:** 멋진 양식을 만들고 모든 장치에서 원활하게 작동합니다.
* **확장성 및 안정성의 이점:** 폼은 기본 에지 인프라만큼 강력하고 확장 가능합니다.

이 안내서는 다음을 수행합니다.

* Edge Delivery 사이트에 대한 양식을 작성(작성)할 수 있는 다양한 방법을 설명합니다.
* 사용자가 양식을 제출한 후 수행할 작업을 구성하는 방법을 보여 줍니다(제출 작업).
* 특정 요구 사항과 팀 기술에 가장 적합한 방법을 선택할 수 있습니다.
* 아키텍처 다이어그램 및 모범 사례를 제공합니다.

## 알아야 할 주요 용어

* **EDS(Edge Delivery Services):** CDN을 통해 AEM 콘텐츠를 게재하기 위한 Adobe의 성능 우선 아키텍처입니다. 프로젝트 프랭클린이라고도 합니다.
* **AEM Forms:** 양식을 만들고, 관리하고, 처리하기 위한 Adobe 솔루션입니다.
* **유니버설 편집기(UE):** 양식을 포함한 AEM 콘텐츠에 대한 시각적 WYSIWYG 편집기입니다.
* **문서 기반 작성:** Microsoft Word 또는 Google Docs/Sheets를 사용하여 양식을 만듭니다.
* **DA(문서 작성):** Edge Delivery Services의 컨텐츠(양식을 호스팅할 수 있는 페이지 포함)를 작성하기 위한 Adobe 호스팅 서비스입니다.
* **Forms 제출 서비스(FSS):** 스프레드시트나 전자 메일로 양식 데이터를 간단하게 전송하는 Adobe 서비스입니다.
* **AEM 게시 인스턴스:** 복잡한 양식 제출을 처리할 수 있는 라이브 AEM 환경입니다.
* **CORS(원본 간 리소스 공유):** 다른 도메인의 양식을 포함할 때 구성해야 하는 브라우저 보안 기능입니다.
* **CDN(Content Delivery Network):** 지리적 위치에 따라 사용자에게 웹 콘텐츠를 빠르게 전달하는 서버 네트워크입니다.


**Edge Delivery Services 양식 인터랙션 개념도**

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

![양식 상호 작용](/help/forms/assets/eds-form-interaction.png)
이 다이어그램은 사용자가 CDN을 통해 빠르게 전달되는 양식과 상호 작용하는 모습을 보여 줍니다. 그런 다음 제출하는 데이터는 백엔드 시스템에 의해 처리됩니다.

## Forms은 Edge에서 어떻게 작동합니까?

EDS를 사용하면 웹 사이트 컨텐츠(양식 구조 포함)를 AEM as a Cloud Service, SharePoint, Google 드라이브 또는 DA(Document Authoring) 서비스와 같은 다양한 소스에서 가져올 수 있습니다. 그런 다음 이 콘텐츠는 글로벌 CDN에 게시됩니다. 사용자가 사이트를 방문할 때 가장 가까운 CDN 에지 서버에서 바로 콘텐츠가 제공되어 최대 속도가 보장됩니다.

<!--*   **Where AEM Forms Fit In**
    Forms in an EDS architecture are designed to be:
    *   **Fast Loading:** Form structures are often simple HTML rendered client-side.
    *   **Decoupled:** The visual part of the form (frontend) is separate from where the data goes after submission (backend).
    *   **Flexible to Create:** You have different tools to build your forms.
    *   **Configurable for Submission:** You can send data to simple services or powerful AEM backends.-->

**Forms을 사용한 간소화된 Edge Delivery Services 아키텍처**

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
이 다이어그램은 여정을 보여 줍니다. 양식이 작성 시스템에 정의되어 있고, 에지에 게시되고, 사용자에게 제공되며, 제출된 데이터는 백엔드에 의해 처리됩니다.

## 양식 작성 방법 선택

Edge Delivery Services 사이트에 대한 양식을 만드는 세 가지 주요 방법이 있습니다. 선택은 팀의 기술, 양식의 복잡성 및 프로젝트 요구 사항에 따라 달라집니다.

### 어떤 작성 방식이 귀하에게 적합합니까?

이 진단트리를 사용하여 다음 항목을 선택하십시오.

**양식 작성 결정 트리**
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

이 진단트리는 팀 및 양식 요구 사항에 따라 작성 방법을 선택하는 데 도움이 됩니다.

### 문서를 사용하여 Forms 만들기(Word/Google Docs)

이 방법은 팀이 Microsoft Word 또는 Google Docs/Sheets에 익숙한 경우 [양식을 빠르게 만들기](/help/edge/docs/forms/create-forms.md)하는 데 유용합니다.

**작동 방식: 문서에서 웹 양식으로**

특수한 표 형식 또는 &quot;양식 블록&quot;을 사용하여 Word 문서 또는 Google 시트에서 직접 양식의 필드, 레이블 및 유형을 정의합니다. 이 문서를 게시하면 Edge Delivery Services은 자동으로 문서를 웹에서 바로 사용할 수 있는 HTML 양식으로 변환하여 사용자가 사이트에서 상호 작용할 수 있도록 합니다.

**기능 및 기능**

* 익숙한 도구로 작성: Word, Google Docs, Google Sheets.
* 텍스트 입력, 이메일, 드롭다운, 확인란, 라디오 버튼, 텍스트 영역 등의 필드를 정의합니다.
* 레이블, 자리 표시자 및 도움말 메시지를 추가합니다.
* 기본 유효성 검사 규칙(필수 필드, 이메일 형식)을 설정합니다.
* 스팸 보호를 위해 reCAPTCHA를 통합합니다.
* 파일 업로드를 허용합니다.
* 즉시 게시: 문서의 변경 사항이 라이브 사이트에 빠르게 반영됩니다.
* 사용자 지정 코드로 확장: 고급 사용자는 GitHub를 통해 사용자 지정 양식 구성 요소 및 스타일을 추가할 수 있습니다.

**고려 사항**

* 팀에서는 컨텐츠에 대해 Word 또는 Google Docs/Sheets를 정기적으로 사용합니다.
* 간단하거나 적당히 복잡한 양식을 빨리 만들어야 합니다.
* 최소한의 설정으로 양식 데이터를 스프레드시트나 이메일 주소로 직접 전송하려는 경우

**제출 작동 방식(주로 Forms 제출 서비스)**

Forms은 일반적으로 이러한 방식으로 [데이터를 AEM Forms 제출 서비스로 전송](/help/forms/forms-submission-service.md)합니다. 데이터를 Google Sheet, OneDrive/SharePoint의 Excel 파일 또는 이메일로 보내도록 소스 문서 자체에서 구성할 수 있습니다.

**문서 기반 작성 개념**
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
이 다이어그램은 문서에 정의된 양식이 라이브 웹 양식이 되는 방식을 보여 줍니다.

### 범용 편집기를 사용한 Forms 시각적

[유니버설 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)는 웹 브라우저에서 직접 양식을 작성할 수 있는 최신 드래그 앤 드롭 인터페이스를 제공합니다.

**작동 방법: 양식 드래그 앤 드롭**

시각적 인터페이스를 사용하여 양식 구성 요소(예: 입력 필드, 단추, 드롭다운)를 페이지로 드래그합니다. 그런 다음 속성 패널을 통해 각 구성 요소의 속성(레이블, 유효성 검사 등)을 구성할 수 있습니다. 유니버설 편집기는 폼의 실시간 미리 보기를 표시합니다.

**기능 및 기능**

* 사전 빌드된 구성 요소의 라이브러리로 시각적 양식 만들기.
* 실시간 유효성 검사 및 비즈니스 논리 구성(예: 선택 항목에 따라 필드 표시/숨기기).
* 다른 장치(데스크탑, 모바일)에 대한 라이브 미리보기 를 참조하십시오.
* 컨텐츠 조각, AEM 워크플로 및 사용자 권한과 같은 AEM 기능과 통합됩니다.
* 프롬프트를 사용하여 양식을 만들거나 편집하는 데 AI 지원을 받으려면 &quot;Experience Builder&quot;를 사용하십시오.

**고려 사항**

* 조건부 논리, 여러 단계 패널 또는 개인화를 사용하여 복잡한 양식을 작성해야 합니다.
* 팀(예: 마케터, 비즈니스 사용자)은 시각적 도구를 선호합니다.
* 거버넌스, 워크플로 또는 양식에서 AEM 에셋을 사용하려면 AEM as a Cloud Service과의 강력한 통합이 필요합니다.

**제출 작동 방식(Forms 제출 서비스 또는 AEM 게시)**

범용 편집기로 빌드된 Forms은 다음 작업을 수행할 수 있습니다.

* 간단한 [Forms 제출 서비스](/help/forms/forms-submission-service.md)(스프레드시트나 전자 메일로 데이터 보내기)를 사용합니다.
* 보다 고급 처리(예: AEM 워크플로 시작, 양식 데이터 모델 사용 또는 다른 엔터프라이즈 시스템과의 통합)를 위해 AEM 게시 인스턴스에 데이터를 제출합니다.

**유니버설 편집기 개념**

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

![범용 편집기](/help/forms/assets/eds-ue-based.png)

이 다이어그램은 양식 작성에 사용되는 유니버설 편집기의 주요 부분을 보여 줍니다.

### DA(문서 작성)와 함께 Forms 사용

[DA(문서 작성)](https://www.aem.live/developer/da-tutorial)은(는) Edge Delivery Services을 통해 제공되는 기본 웹 사이트 콘텐츠(페이지, 문서)를 만들고 관리하기 위한 Adobe 호스팅 서비스입니다. Edge Delivery Services 소스 콘텐츠에 SharePoint 또는 Google 드라이브를 사용하는 대신 사용할 수 있습니다.

**Edge Delivery Services 콘텐츠에 대한 DA(문서 작성) 이해**

문서 작성은 Adobe의 Spectrum(디자인 시스템) 및 AEM의 문서 모델(블록, 섹션)을 사용하여 엔터프라이즈급 작성 환경을 제공합니다. EDS를 위한 구조화된 컨텐츠 관리를 위해 설계되었습니다.

**DA에서 Forms을 처리하는 방법(직접 작성이 아닌 포함)**

DA 자체는 **처음부터 양식을 작성하는 도구가 아닙니다**. 대신 DA를 사용하여 웹 페이지를 만든 다음 문서 기반 작성 또는 유니버설 편집기를 사용하여 만든 *embed* 양식을 DA가 작성한 페이지에 추가합니다.

**DA 페이지에 Forms을 포함하는 단계**

1. **다음 중 하나를 사용하여 양식을 만듭니다.**
   * 문서 기반 작성(Word/Google Docs)
   * 범용 편집기

1. **양식 게시:** 이 양식이 게시되고 자체 Edge Delivery URL(예: `https://your-eds-project.hlx.page/forms/contact-us`)을 통해 액세스할 수 있는지 확인하십시오.
1. **DA에서 사용자 페이지 작성:** 양식을 표시할 문서 작성에서 페이지를 만들거나 편집합니다.
1. **양식 포함:** DA 페이지 내의 특정 &quot;블록&quot; 또는 구성 요소를 사용하여 해당 URL에서 양식을 참조하고 포함하십시오. 그런 다음 DA 페이지는 외부에서 만든 이 양식을 가져와 표시합니다.

**포함된 양식으로 문서 작성**
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

이 다이어그램은 먼저 UE 또는 문서를 사용하여 양식을 만든 다음 문서 작성에서 빌드하는 페이지에 포함한다는 것을 보여 줍니다.


### 작성 옵션 비교

| 기준 | 문서 기반 작성 | 유니버설 편집기(WYSIWYG) | DA(문서 작성)의 Forms |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **기본 제작 도구** | Word/Google Docs/Sheets | 브라우저(AEM 유니버설 편집기) | 해당 없음(Forms은 *포함*&#x200B;됨) |
| **팀 스킬 레벨** | 문서 편집기에 익숙함 | 시각적 웹 도구에 익숙함 | 페이지 콘텐츠에 DA 사용 |
| **일반적인 양식 복잡성** | 단순-중재 | 중간에서 복잡으로, 엔터프라이즈급 | 포함된 양식에 따라 다름 |
| **제출 옵션 1(단순)** | Forms 제출 서비스(시트/이메일로) | Forms 제출 서비스(시트/이메일로) | 임베드된 양식의 설정을 따릅니다. |
| **제출 옵션 2(고급)** | 해당 사항 없음 | AEM 게시(워크플로, FDM 등) | 임베드된 양식의 설정을 따릅니다. |
| **AEM 백엔드 통합** | 최소 | 높음(AEM Publish 제출 시) | 임베드된 범용 편집기 양식을 통해 간접적으로 |
| **가장 적합한 대상...** | 콘텐츠 팀이 간단한 양식을 신속하게 작성하고 데이터를 빠르게 캡처합니다. | 시각적 제어, 복잡한 양식 또는 심층 AEM 통합이 필요한 마케터, 비즈니스 사용자. | DA에서 기본 콘텐츠가 관리되고 다른 소스의 양식이 필요한 사이트. |

**향상된 결정 트리**
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

![결정 트리](/help/forms/assets/eds-enhanced-decision.png)

## 작성 방법의 기능 비교

다음 표는 다양한 AEM 양식 작성 방법의 주요 기능을 자세히 비교하여 요구 사항에 가장 적합한 방법을 선택하는 데 도움을 줍니다.&#x200B;

| **기능** | **범용 편집기 (WYSIWYG)** | **문서 기반 작성** | **DA(문서 작성)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Sites를 통한 통합 컴포지션** | ✅ |                              | ✅(임베드된 양식 포함) |
| **양식 임베드 지원** | ✅ | ✅ | ✅(유니버설 편집기 또는 문서에서 포함) |
| **규칙 (동적 동작)** | 사용자 정의 함수가 포함된 고급 규칙 편집기 | 제한적: 표시/숨기기, 값 계산, 사용자 정의 함수 | 포함된 양식에 따라 다름 |
| **첨부 파일 지원** | ✅ | ℹ️ (얼리 액세스) | 포함된 양식에 따라 다름 |
| **CAPTCHA 지원** | reCAPTCHA Enterprise | reCAPTCHA Enterprise | 포함된 양식에 따라 다름 |
| **제출 기능** | REST, 이메일, FDM, 워크플로우, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion(EA) | 스프레드시트만 | 임베드된 양식의 설정을 따릅니다. |
| **데이터 스키마** | FDM, 사용자 정의 | 사용자 정의 | 임베드된 양식 기반 |
| **미리 채우기** | 💡(마법사를 통해) | ✅ | 포함된 양식에 따라 다름 |
| **조각** | ✅ | ✅ | 포함된 양식에 따라 다름 |
| **시각적 규칙 편집기** | ✅ |                              |                              |
| **현지화** | 💡(사이트를 통해) | ℹ️ (Excel/Sheets 설명서) | 포함된 양식에 따라 다름 |
| **데이터 스키마 (데이터 트리)** | 💡(UI 확장 사용) |                              |                              |
| **템플릿 지원** | 초기 콘텐츠만 |                              |                              |
| **포털** |                               |                              |                              |
| **테마** | ℹ️ (프로젝트 수준에서) | ℹ️ (프로젝트 수준에서) | ℹ️(호스팅 사이트 기준) |
| **사용자 정의 구성 요소** | ✅ | ✅ | ✅(포함된 구성 요소가 지원하는 경우) |
| **OOTB 및 사용자 정의 함수** | ✅ | ✅ | ✅(임베드된 양식) |
| **조각 참조** |                               |                              |                              |
| **Sign 통합** |                               |                              |                              |
| **실험** | ✅ | ✅ | 포함 컨텍스트에 따라 다름 |
| **Workfront를 통한 작업 관리** | ✅ |                              |                              |
| **개인화 확장 기능** | 💡 |                              |                              |
| **편집기 사용자 정의** | ✅(UI 확장 사용) |                              |                              |
| **제출 액션** | ✅ | 스프레드시트만 | 임베드된 양식 기반 |

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

학습한 내용을 토대로 다음 단계를 진행할 수 있습니다.

[제출 전략을 선택하십시오](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) 프로젝트에 Forms 제출 서비스의 단순성(스프레드시트/이메일 출력에 적합)이 필요한지 또는 AEM 게시 제출 액션에서 제공하는 유연성과 백엔드 통합이 필요한지 여부를 결정합니다.

효과적이고 접근 가능하며 사용자 친화적인 양식을 디자인하는 방법에 대해 알아보려면 [Forms 만들기 모범 사례](/help/edge/docs/forms/universal-editor/best-pratices-eds-forms.md) 문서를 참조하십시오.

## 다음 단계

이 안내서에서는 AEM Edge Delivery Services에서 양식 사용에 대한 개요를 제공합니다. 특정 구성에 대한 자세한 단계별 지침은 공식 Adobe Experience Manager 설명서를 참조하십시오.

* [Edge Delivery Services Forms을 사용하여 문서 기반 작성](/help/edge/docs/forms/tutorial.md)
* [Edge Delivery Services Forms을 사용한 유니버설 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [DA(문서 작성) 및 콘텐츠 포함](https://www.aem.live/developer/da-tutorial)
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
