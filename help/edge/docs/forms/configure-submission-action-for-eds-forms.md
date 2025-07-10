---
title: Edge Delivery Services을 사용하여 AEM Forms에 대한 제출 액션 구성
description: Edge Delivery Services을 사용하여 AEM Forms에서 제출 액션을 구성하는 방법에 대해 알아봅니다. 양식 데이터를 안전하고 효율적으로 처리할 수 있도록 Forms 제출 서비스와 AEM 게시 제출 액션 중에서 선택하십시오.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 75d8ea4f0913e690e3374d62c6e7dcc44ea74205
workflow-type: tm+mt
source-wordcount: '2166'
ht-degree: 0%

---

# 양식 제출 구성: 데이터는 어디로 이동합니까?

사용자가 양식에서 **제출**&#x200B;을 클릭하면 해당 데이터로 어떻게 할지 Edge Delivery Services에 알려야 합니다. 다음과 같은 두 가지 주요 옵션이 있습니다.

## 방법 1: AEM Forms 제출 서비스 사용(간소화)

이 서비스는 데이터를 스프레드시트나 이메일로 보내는 것과 같은 일반적이고 간단한 작업에 이상적입니다.

**도움이 되는 내용 및 방법**

[Forms 제출 서비스](/help/forms/forms-submission-service.md)는 Adobe에서 호스팅하는 끝점입니다. 양식에서 데이터를 제출하면 이 서비스가 이를 인계받아 사전 구성된 작업을 수행합니다. 쉽게 설정할 수 있도록 설계되었습니다. 다음을 구성할 수 있습니다. 스프레드시트 또는 이메일로 제출:

* **스프레드시트에 제출:** 제출된 양식 데이터를 Google Sheet 또는 Microsoft Excel 파일(OneDrive 또는 SharePoint에 저장됨)에 새 행으로 자동으로 추가합니다.
* **전자 메일 보내기:** 지정한 하나 이상의 전자 메일 주소로 양식 데이터가 포함된 전자 메일을 보냅니다.

#### 중요: 설정 요구 사항

* **스프레드시트 액세스:** OneDrive/SharePoint에서 Google Sheet 또는 Excel 파일로 데이터를 보내려면 Adobe 서비스 계정(종종 `forms@adobe.com`)에 해당 특정 스프레드시트에 대한 **편집 권한**&#x200B;이 필요합니다.
* **조기 액세스 프로그램:** 이 서비스의 일부 기능(특히 스프레드시트의 경우)이 조기 액세스 프로그램의 일부일 수 있습니다. `aem-forms-ea@adobe.com`에 전자 메일을 보내거나 프로젝트 세부 정보로 특정 Adobe 양식을 작성하여 액세스 권한을 요청해야 할 수 있습니다. 항상 최신 Adobe 설명서를 확인하십시오.

**Forms 제출 서비스 순서도**
<!--
```mermaid
    graph TD
    UserForm[User Submits Form on Your EDS Site] >|Data Sent| FormSubmissionService[AEM Forms Submission Service]
    FormSubmissionService -- "If configured for Google Sheets" > GoogleSheet[Data written to Google Sheet]
    FormSubmissionService -- "If configured for Excel (OneDrive or SharePoint)" > ExcelSheet[Data written to Excel]
    FormSubmissionService -- "If configured for Email" > Email[Email with data is sent]

    style UserForm fill:#ccf,stroke:#333
    style FormSubmissionService fill:#fca,stroke:#333
    style GoogleSheet fill:#90ee90,stroke:#333
    style ExcelSheet fill:#90ee90,stroke:#333
    style Email fill:#add8e6,stroke:#333
```-->
![Forms 제출](/help/forms/assets/eds-fss.png)

이 순서도는 Forms 제출 서비스에서 제출된 데이터를 가져와 구성된 스프레드시트나 이메일로 보내는 방법을 보여줍니다.

## 방법 2: AEM 게시 인스턴스에 제출(고급)

더 복잡한 요구 사항의 경우 [양식(특히 유니버설 편집기로 만든 양식)은 데이터를 AEM as a Cloud Service 게시 인스턴스로 직접 보낼 수 있습니다](/help/forms/configure-submit-actions-core-components.md). 이렇게 하면 AEM의 전체 백엔드 전원이 잠금 해제됩니다.

**언제 AEM 게시로 제출해야 합니까?**

* 제출 후 사용자 지정 AEM 워크플로우를 트리거합니다.
* AEM 양식 데이터 모델(FDM)을 사용하여 데이터베이스 또는 다른 엔터프라이즈 시스템과 통합하려면 다음을 수행합니다.
* Marketo, Microsoft Power Automate 또는 Adobe Workfront Fusion과 같은 서드파티 서비스와 연결하려면
* Azure Blob Storage 또는 SharePoint 목록/문서 라이브러리(단순 스프레드시트가 아님)와 같은 특정 위치에 데이터를 저장합니다.
* AEM 내에 복잡한 서버측 유효성 검사 또는 데이터 처리 논리가 있는 경우.

**사용 가능한 제출 액션(AEM 게시 제출)**

* [REST 끝점에 제출](/help/forms/configure-submit-action-restpoint.md)
* [이메일 보내기(AEM의 메일 서비스 사용)](/help/forms/configure-submit-action-send-email.md)
* [양식 데이터 모델(FDM)을 사용하여 제출](/help/forms/configure-data-sources.md)
* [AEM Workflow 호출](/help/forms/aem-forms-workflow-step-reference.md)
* [SharePoint에 제출(목록 항목 또는 문서로)](/help/forms/configure-submit-action-sharepoint.md)
* [OneDrive에 제출(문서로)](/help/forms/configure-submit-action-onedrive.md)
* [Azure Blob 스토리지에 제출](/help/forms/configure-submit-action-azure-blob-storage.md)
* [Microsoft Power Automate에 제출](/help/forms/forms-microsoft-power-automate-integration.md)
* [Adobe Workfront Fusion에 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Adobe Marketo Engage에 제출](/help/forms/submit-adaptive-form-to-marketo-engage.md)

>[!NOTE]
>
> AEM Publish에서 Google Sheet/Excel을 대상으로 하는 경우에도 직접 Forms 제출 서비스와 다른 구성 단계가 포함됩니다.

**AEM 게시 제출 순서도**

<!--```mermaid
    graph TD
    UEForm[User Submits Universal Editor Form on EDS Site] >|Data sent to AEM Publish URL - example: /adobe/forms/af/submit/...| AEMPublish[AEM Publish Instance]
    AEMPublish -- Configured to run AEM Workflow > AEMWorkflow[AEM Workflow is Triggered]
    AEMPublish -- Configured to use Form Data Model > FDM[FDM updates Backend System or Database]
    AEMPublish -- Configured for Marketo > Marketo[Data sent to Marketo Engage]
    AEMPublish -- Other configured actions... > OtherIntegrations[...]

    style UEForm fill:#ccf,stroke:#333
    style AEMPublish fill:#fca,stroke:#333
    style AEMWorkflow fill:#add8e6,stroke:#333
    style FDM fill:#add8e6,stroke:#333
    style Marketo fill:#add8e6,stroke:#333
```-->

![AEM 게시 제출 순서도](/help/forms/assets/eds-aem-publish.png)
이 순서도는 복잡한 백엔드 작업을 처리하는 AEM 게시로 제출된 양식을 보여 줍니다.

### Forms 제출 서비스와 AEM Publish 제출 비교

| 기능 | Forms 제출 서비스 | AEM 게시 제출 |
| :- | :- | :-- |
| **적합한 대상** | 스프레드시트, 이메일 알림에 대한 간단한 데이터 캡처 | 복잡한 워크플로우, 엔터프라이즈 통합, 사용자 정의 논리 |
| **양식 작성** | 문서 기반에 적합, 단순 UE 양식에 적합 | 범용 편집기 작성 양식에 최적 |
| **설치 노력** | 낮음(종종 간단한 구성) | 높음(AEM Publish, Dispatcher, OSGi, CDN 설정 필요) |
| **백엔드 시스템** | Adobe 호스팅 서비스 | AEM as a Cloud Service 게시 인스턴스 |
| **유연성** | 시트/이메일로 제한 | 매우 유연하고 광범위한 AEM Forms 작업 |
| **예** | Google 시트에 양식 데이터 연결 | AEM 승인 워크플로를 트리거하는 대출 애플리케이션 |

## 다른 사이트 또는 페이지에 Forms을 임베드하는 방법

다른 웹 페이지나 사이트의 한 위치(예: 중앙 &quot;양식 사이트&quot;)에서 작성 및 관리되는 양식을 표시할 수 있습니다.

### 양식을 임베드하는 이유는 무엇입니까?

* 범용 편집기로 만든 표준 &quot;연락처&quot; 양식은 문서 기반 작성으로 빌드된 여러 랜딩 페이지에 표시되어야 합니다.
* 기본 웹 사이트 콘텐츠는 문서 작성(DA)에 있으며 특수 양식을 포함해야 합니다.
* 여러 EDS 프로젝트에서 잘 유지 관리되는 단일 양식을 재사용하려는 경우

### 양식 포함이 기술적으로 작동하는 방법

양식을 표시할 페이지(&quot;호스트 페이지&quot;라고 함)에는 일부 코드(일반적으로 특수 블록 또는 스크립트)가 포함됩니다. 사용자가 호스트 페이지를 방문하면 이 코드는 실제 양식이 호스팅된 URL에 대한 요청을 수행합니다(&quot;양식 Source&quot;라고 함). 그런 다음 양식 Source은 호스트 페이지가 주입 및 표시하는 HTML을 다시 전송합니다.

**포함된 양식 아키텍처**

<!--```mermaid
   graph LR
    User[User] >|Visits| HostPage[Host Page - for example: your-site.com/landing-page]
    HostPage >|Contains code to embed form| FetchForm{Host Page Requests Form HTML}
    FetchForm >|HTTP GET request to the form URL| FormSource[Form Source - for example: forms-repo.hlx.page/my-form]
    FormSource >|Returns form HTML| FetchForm
    FetchForm >|Injects form HTML into page| HostPage
    HostPage >|Displays full page with embedded form| User

    subgraph Submission ["Form Submission from Host Page"]
        HostPage_Form[Embedded form on the host page] >|User submits| TargetEndpoint[Submission endpoint - FSS or AEM Publish]
    end

    style HostPage fill:#e6f3ff,stroke:#333
    style FormSource fill:#ffe6e6,stroke:#333
    style FetchForm fill:#fff2cc,stroke:#333
    style Submission fill:#f0fff0,stroke:#333
```-->
![포함된 양식 아키텍처](/help/forms/assets/eds-embedded-form.png)
이 다이어그램은 HTML에서 Source을 가져와서 표시하는 호스트 페이지를 보여 줍니다. 제출은 원본 양식의 구성된 끝점을 사용합니다.

## 포함된 Forms에 대한 CORS 설정

[CORS(원본 간 리소스 공유)](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)은(는) 브라우저 보안 기능입니다. 호스트 페이지(예: `site-a.com`)에서 다른 도메인(예: `forms-site-b.com`)에서 양식을 가져오려고 하면 `forms-site-b.com`에서 CORS 헤더를 통해 명시적으로 허용하지 않는 한 브라우저가 해당 양식을 차단합니다.

**양식 Source 서버**&#x200B;에 올바른 CORS 헤더가 없으면 브라우저에서 호스트 페이지가 양식을 로드할 수 없게 되어 포함된 양식이 표시되지 않습니다.

### 양식을 제공하는 사이트에서 CORS를 구성하는 방법

응답에서 특정 HTTP 헤더를 보내도록 **Form Source**&#x200B;을(를) 호스팅하는 서버를 구성해야 합니다. 정확한 방법은 EDS 설정에 따라 다릅니다(예: Franklin 프로젝트의 경우 CDN 동작 또는 Edge Worker 논리를 제어하는 GitHub 저장소의 `helix-config.yaml` 또는 유사한 구성 파일에서 수행되는 경우가 많음).
양식 Source 응답에 추가할 주요 헤더:

* `Access-Control-Allow-Origin: <URL_of_Host_Page>`(예: `https://your-site.com`). 테스트에는 `*`을(를) 사용할 수 있지만 프로덕션에는 정확한 도메인을 지정하십시오.
* `Access-Control-Allow-Methods: GET, OPTIONS`(양식 제출 자체도 원본 간에 있는 경우 `POST`이(가) 필요할 수 있지만 일반적으로 제출은 별도의 원본 또는 특별히 구성된 끝점으로 이동합니다).
* `Access-Control-Allow-Headers: Content-Type`(및 양식을 가져오는 데 사용할 수 있는 다른 모든 사용자 지정 헤더).

**예제(구성 파일의 개념적):**

```yaml
        # In the configuration for the site HOSTING THE FORM (Form Source)
        headers:
          # Apply to paths where your forms are served, e.g., /forms/**
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-page-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS
```

## 추가 고려 사항: CDN 및 다중 코드 베이스(Helix 4)

* **CDN 규칙:** CDN에서 요청을 프록시할 수 있는 방법을 제공할 수 있습니다. 예를 들어 CDN이 `host-page.com/embedded-form`에 대한 요청을 내부적으로 라우팅하여 `form-source.com/actual-form`에서 콘텐츠를 가져와 동일한 원본으로 브라우저에서 표시할 수 있습니다. 설정하는 것은 복잡할 수 있습니다.
* **여러 코드 베이스(Helix 4):** 호스트 페이지와 양식 Source이 서로 다른 GitHub 저장소(Helix 4 설정에서 공통됨)에 있는 경우 양식을 렌더링하거나 관리하는 데 필요한 모든 JavaScript &quot;양식 블록&quot;을 호스트 페이지의 코드 베이스에 사용할 수 있는지 확인하거나 양식 Source에서 가져온 양식 HTML이 필요한 모든 JavaScript과 함께 자체 포함되어 있는지 확인하십시오. 원본 문서에서는 &quot;서로 다른 코드 베이스가 있는 helix4의 경우 두 코드 베이스 모두에 양식 블록을 추가해야 합니다.&quot;라고 언급합니다.

### 일반적인 아키텍처 설정 및 구성 단계

다음은 작성 방법을 제출 전략과 결합하여 주요 구성 포인트와 함께 양식을 설정할 수 있는 몇 가지 일반적인 방법입니다.

#### 스프레드시트/이메일 제출이 있는 문서 기반 양식

가장 간단한 설정입니다. Word/Google Docs에서 양식을 만들고 Forms 제출 서비스를 통해 데이터를 스프레드시트나 이메일로 제출합니다.

1. 지정된 표 구조 또는 양식 블록을 사용하여 Word/Google 문서/시트에서 양식을 정의합니다.
1. 문서(또는 관련 구성)에서 Forms 제출 서비스의 대상 스프레드시트 URL 또는 이메일 주소를 지정합니다.
1. `forms@adobe.com`(또는 관련 서비스 계정)에게 대상 스프레드시트에 대한 편집 액세스 권한이 있는지 확인하십시오.
1. Edge Delivery 사이트에 문서를 게시합니다.

**문서 기반 + Forms 제출 서비스 아키텍처**
<!--
```mermaid
    graph TD
        User[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User] >|Fills Out| EDS_Page_DocBased[EDS Page with Document-Based Form]
        EDS_Page_DocBased >|Submits Data| FSS[AEM Forms Submission Service]
        FSS > Target[<img src='https://img.icons8.com/color/48/000000/google-sheets.png' width='30' /> Data to Spreadsheet / <img src='https://img.icons8.com/color/48/000000/filled-sent.png' width='30' /> Email Notification]

        Authoring[Form defined in Google Doc/Sheet] >|EDS Syncs & Renders| EDS_Page_DocBased

        style EDS_Page_DocBased fill:#ccf,stroke:#333
        style FSS fill:#fca,stroke:#333
        style Target fill:#90ee90,stroke:#333
        style Authoring fill:#e6ffe6,stroke:#333
```-->

![문서 기반 + Forms 제출 서비스 아키텍처](/help/forms/assets/eds-doc-fss.png)

#### 스프레드시트/이메일 제출이 있는 유니버설 편집기 양식

시각적 범용 편집기를 사용하여 양식을 작성하지만 데이터 캡처에는 여전히 간단한 Forms 제출 서비스를 사용합니다.

1. AEM의 범용 편집기를 사용하여 양식을 만듭니다.
1. &quot;Forms 제출 서비스에 제출&quot; 옵션을 사용하도록 UE에서 양식의 제출 액션을 구성합니다.
1. 대상 스프레드시트 URL 또는 이메일 주소를 지정합니다.
1. 스프레드시트를 사용하는 경우 `forms@adobe.com`에 편집 액세스 권한이 있는지 확인하십시오.
1. AEM의 양식이 포함된 페이지를 Edge Delivery 사이트에 게시합니다.

   **유니버설 편집기 + Forms 제출 서비스 아키텍처**

   ![유니버설 편집기 + Forms 제출 서비스 아키텍처](/help/forms/assets/eds-ue-fss.png)

   <!--```mermaid
    graph TD
    User[User] >|Fills Out| EDS_Page_UE[EDS Page with Universal Editor Form]
    EDS_Page_UE >|Submits Data| FSS[AEM Forms Submission Service]
    FSS > Target[Data sent to Google Sheet and Email Notification]
    AuthoringUE[Form built in Universal Editor - AEM] >|AEM Publishes to EDS| EDS_Page_UE
    style EDS_Page_UE fill:#ccf,stroke:#333
    style FSS fill:#fca,stroke:#333
    style Target fill:#90ee90,stroke:#333
    style AuthoringUE fill:#e6f3ff,stroke:#333
    ```
    -->

#### AEM 게시 제출이 있는 유니버설 편집기 양식(고급)

이 설정에서는 강력한 백엔드 처리(워크플로우, FDM 등)를 위해 양식 작성에 범용 편집기 및 AEM 게시 인스턴스를 사용합니다. 이를 위해서는 추가 구성이 필요합니다.

1. **UE에서 양식 만들기:** 유니버설 편집기에서 양식을 빌드합니다. AEM Forms 작업(예: &quot;AEM 워크플로우 호출&quot;, &quot;양식 데이터 모델을 사용하여 제출&quot;)을 가리키도록 제출 작업을 구성합니다.
1. **AEM Dispatcher 구성(AEM 게시 계층):**
   * **리디렉션 없음:** Dispatcher 규칙이 *경로에 대해 리디렉션 요청을*&#x200B;하지`/adobe/forms/af/submit/...`하는지 확인하십시오.
   * **제출 허용:** Edge Delivery 사이트의 도메인 또는 IP 주소에서 `filters.any`에 대한 POST 요청을 명시적으로 `allow`하도록 Dispatcher 필터(예: `/adobe/forms/af/submit/...`에서)를 수정합니다.
1. AEM(AEM 게시 계층)의 **OSGi 레퍼러 필터:**
   * AEM OSGi 콘솔(`/system/console/configMgr`)에서 &quot;Apache Sling Referrer Filter&quot;를 찾아 구성합니다.
   * Edge Delivery 사이트의 도메인(예: `https://your-eds-domain.hlx.page`, `https://your-custom-eds-domain.com`)을 &quot;호스트 허용&quot; 또는 &quot;호스트 허용 RegExp&quot; 목록에 추가합니다. 이를 통해 AEM은 EDS 사이트에서 시작된 제출을 수락할 수 있습니다.
1. **CDN 리디렉션 규칙(Edge Delivery CDN에서):**
   * Edge Delivery 사이트(예: `your-eds-domain.hlx.page`)에서 제출 요청을 AEM 게시 인스턴스로 올바르게 라우팅해야 합니다.
   * EDS 페이지의 양식이 제출되면 `/adobe/forms/af/submit/...`과(와) 같은 상대 경로를 대상으로 할 수 있습니다. Edge Delivery CDN(또는 에지 작업자)에 &quot;요청이 `your-eds-domain.hlx.page/adobe/forms/af/submit/...`에 도달하면 `your-aem-publish-instance.com/adobe/forms/af/submit/...`(으)로 전달(프록시 또는 리디렉션)합니다.&quot;라는 규칙이 필요합니다.
   * 정확한 구현은 CDN 공급자(예: Fastly VCL, Akamai Property Manager, Cloudflare Workers)에 따라 다릅니다.
1. **(선택 사항) EDS 프로젝트의 코드베이스에 있는 개발용 `constants.js`:**
   * 로컬 개발의 경우 또는 클라이언트측 양식 스크립트가 전체 AEM 게시 URL을 알아야 하는 경우, Edge Delivery 프로젝트의 GitHub 저장소 내에 있는 `constants.js` 또는 유사한 구성 파일에서 구성할 수 있습니다. 예:

   ```javascript
       // in your-eds-project/scripts/constants.js
       export const AEM_PUBLISH_URL = 'https://publish-p123-e456.adobeaemcloud.com';
            // Your form submission script might then construct the submit URL:
           // const submitUrl = `${AEM_PUBLISH_URL}/adobe/forms/af/submit/...`;
   ```

1. **게시:** AEM에서 EDS로 양식 페이지를 게시하고 모든 AEM 구성이 AEM 게시 인스턴스에서 활성화되어 있는지 확인합니다.

   **유니버설 편집기 + AEM 게시 아키텍처**

![유니버설 편집기 + AEM 게시 아키텍처](/help/forms/assets/eds-aem-publish.png)

이는 흐름을 보여줍니다. 사용자가 EDS 사이트에서 제출하고 CDN이 AEM Dispatcher으로 라우팅된 다음 AEM Publish가 이를 처리합니다.

#### DA(문서 작성) 페이지에 양식 포함

기본 웹 사이트 컨텐츠는 문서 작성(DA)에서 만들어집니다. 문서 기반 작성 또는 범용 편집기를 별도로 사용하여 양식을 만든 다음 DA 페이지에 임베드합니다.

1. **양식 만들기 및 게시:**
   * 문서 기반 작성 또는 범용 편집기를 사용하여 양식을 만듭니다.
   * 제출 방법을 구성합니다(설정 1, 2 또는 3에 따라 Forms 제출 서비스 또는 AEM 게시로).
   * 이 양식을 자체 Edge Delivery URL(예: `.../forms/my-special-form`)로 라이브로 게시하십시오.
1. **CORS 구성:** 이 독립 실행형 양식을 호스팅하는 Edge Delivery 사이트/프로젝트에서 문서 작성 사이트의 도메인이 가져올 수 있도록 CORS 헤더가 설정되어 있는지 확인하십시오.
1. **DA의 작성자 페이지:** 문서 작성에서 페이지를 만들거나 편집합니다.
1. **양식 블록 포함:** DA에서 적절한 블록을 사용하여 외부 URL을 포함합니다. 이 블록을 독립 실행형 게시 양식의 URL을 가리킵니다.
1. **DA 페이지 게시:** DA 페이지를 게시합니다. 이제 양식을 가져와서 표시합니다.

   **DA 아키텍처에 포함된 Forms**

   ![DA 아키텍처에 포함된 Forms](/help/forms/assets/eds-forms-embedd-da.png)

   다른 EDS 위치에서 형식으로 가져오는 DA 페이지를 보여 줍니다. 포함된 양식은 자체 제출을 처리합니다.

## 문제 해결

* **양식 제출이 작동하지 않습니다.**
   * **콘솔 오류 확인:** 브라우저의 개발자 콘솔(일반적으로 F12)을 열고 제출할 때 네트워크 탭이나 콘솔 탭에서 오류를 찾습니다.
   * **제출 URL 확인:** 양식이 올바른 엔드포인트(Forms 제출 서비스 URL 또는 AEM 게시 경로)에 제출하려고 합니까?
   * **Forms 제출 서비스:** 스프레드시트로 보내는 경우 `forms@adobe.com`에게 편집 액세스 권한이 부여되었습니까? 스프레드시트 URL이 올바릅니까?
   * **AEM 게시 제출:**
      * Dispatcher에서 `/adobe/forms/af/submit/...`에 대한 POST를 허용하고 있습니까?
      * AEM 게시의 Sling Referrer 필터가 EDS 도메인을 허용하도록 구성되어 있습니까?
      * `/adobe/forms/af/submit/...`에 대한 CDN 리디렉션 규칙이 올바르게 작동하고 있습니까?

* **포함된 양식이 표시되지 않습니다.**

   * **CORS!** 가장 일반적인 이유입니다. 브라우저 콘솔에서 CORS 오류를 확인합니다. 사이트 *호스팅* 양식에 올바른 `Access-Control-Allow-Origin` 헤더가 있는지 확인하십시오.
   * **양식 URL이 올바릅니까?** 호스트 페이지의 포함 코드가 올바른 형식의 라이브 URL을 가리키고 있습니까?
   * **JavaScript 블록:** 양식이 렌더링에 특정 JavaScript &quot;양식 블록&quot;을 사용하는 경우 해당 블록의 코드를 호스트 페이지에서 사용할 수 있습니까?

* **AEM 게시로 제출할 때 &quot;403 금지됨&quot; 또는 &quot;401 인증되지 않음&quot;이 표시됩니다.**

   * 이는 종종 AEM 게시의 Sling 레퍼러 필터가 EDS 도메인의 요청을 허용하지 않음을 가리킵니다. 구성을 다시 확인합니다.
   * 또한 표준 양식 제출은 일반적으로 익명으로 처리되지만 AEM 제출 엔드포인트가 필요한 경우 인증/권한 부여 문제일 수 있습니다.

## 다음 단계

이 안내서에서는 AEM Edge Delivery Services에서 양식 사용에 대한 개요를 제공합니다. 특정 구성에 대한 자세한 단계별 지침은 공식 Adobe Experience Manager 설명서를 참조하십시오.

* [Edge Delivery Services Forms을 사용하여 문서 기반 작성](/help/edge/docs/forms/tutorial.md)
* [Edge Delivery Services Forms을 사용한 유니버설 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [DA(문서 작성) 및 콘텐츠 포함](https://www.aem.live/developer/da-tutorial)
* [AEM Forms 제출 서비스](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
