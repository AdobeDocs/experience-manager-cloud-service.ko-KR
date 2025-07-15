---
title: Edge Delivery Services를 사용하여 AEM Forms에 제출 액션 구성
description: Edge Delivery Services를 사용하여 AEM Forms에서 제출 액션을 구성하는 방법을 알아봅니다. 안전하고 효율적으로 양식 데이터를 처리하려면 Forms 제출 서비스와 AEM Publish 제출 액션 중에서 선택합니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 75d8ea4f0913e690e3374d62c6e7dcc44ea74205
workflow-type: tm+mt
source-wordcount: '2166'
ht-degree: 99%

---

# 양식 제출 구성: 데이터는 어디로 이동합니까?

사용자가 양식에서 **제출**&#x200B;을 클릭하면 Edge Delivery Services에서 해당 데이터를 어떻게 처리할지 알려 주어야 합니다. 두 가지 주요 옵션이 있습니다.

## 방법 1: AEM Forms 제출 서비스 사용 (간소화)

이 서비스는 스프레드시트나 이메일로 데이터를 보내는 것과 같은 일반적이고 간단한 액션에 적합합니다.

**무엇이며 어떻게 도움이 될 수 있습니까?**

[Forms 제출 서비스](/help/forms/forms-submission-service.md)는 Adobe에서 호스팅하는 엔드포인트입니다. 양식에서 데이터를 제출하면 이 서비스가 받아 미리 구성된 액션을 수행합니다. 설치가 쉽도록 설계되었습니다. 구성 가능: 스프레드시트 또는 이메일로 제출:

* **스프레드시트에 제출:** 제출된 양식 데이터를 자동으로 Google Sheet나 Microsoft Excel 파일(OneDrive 또는 SharePoint에 저장됨)에 새 행으로 추가합니다.
* **이메일 보내기:** 양식 데이터가 포함된 이메일을 지정한 하나 이상의 이메일 주소로 보냅니다.

#### 중요: 설정 요구 사항

* **스프레드시트 액세스:** OneDrive/SharePoint에 있는 Google Sheet나 Excel 파일로 데이터를 보내려면 Adobe 서비스 계정(종종 `forms@adobe.com`)에 해당 스프레드시트에 대한 **편집 권한**&#x200B;이 있어야 합니다.
* **얼리 액세스 프로그램:** 이 서비스의 일부 기능, 특히 스프레드시트의 경우 얼리 액세스 프로그램의 일부일 수 있습니다. `aem-forms-ea@adobe.com`으로 이메일을 보내거나 프로젝트 세부 정보가 포함된 특정 Adobe 양식을 작성하여 액세스를 요청해야 할 수도 있습니다. 항상 최신 Adobe 문서를 확인하십시오.

**Forms 제출 서비스 사용 순서도**
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

이 순서도는 Forms 제출 서비스가 제출된 데이터를 어떻게 가져와 구성된 스프레드시트나 이메일로 보내는지 보여 줍니다.

## 방법 2: AEM Publish 인스턴스에 제출 (고급)

더 복잡한 상황의 경우 [양식(특히 Universal Editor로 만든 양식)은 AEM as a Cloud Service 게시 인스턴스로 데이터를 직접 전송할 수 있습니다](/help/forms/configure-submit-actions-core-components.md). 이렇게 하면 AEM의 전체 백엔드 기능이 해제됩니다.

**AEM Publish에 제출해야 하는 경우는 언제입니까?**

* 제출 후 사용자 정의 AEM 워크플로를 트리거하는 경우.
* AEM 양식 데이터 모델(FDM)을 사용하여 데이터베이스나 다른 엔터프라이즈 시스템과 통합하는 경우.
* Marketo, Microsoft Power Automate 또는 Adobe Workfront Fusion과 같은 서드파티 서비스와 연결하는 경우.
* Azure Blob Storage나 SharePoint 목록/문서 라이브러리(단순 스프레드시트만이 아님)와 같은 특정 위치에 데이터를 저장하는 경우.
* AEM 내에 복잡한 서버측 검증이나 데이터 처리 논리가 있는 경우.

**사용 가능한 제출 액션 (AEM Publish 제출)**

* [REST 엔드포인트에 제출](/help/forms/configure-submit-action-restpoint.md)
* [이메일 보내기 (AEM의 메일 서비스 사용)](/help/forms/configure-submit-action-send-email.md)
* [양식 데이터 모델(FDM)을 사용하여 제출](/help/forms/configure-data-sources.md)
* [AEM 워크플로 호출](/help/forms/aem-forms-workflow-step-reference.md)
* [SharePoint에 제출 (목록 항목 또는 문서)](/help/forms/configure-submit-action-sharepoint.md)
* [OneDrive에 제출 (문서)](/help/forms/configure-submit-action-onedrive.md)
* [Azure Blob Storage에 제출](/help/forms/configure-submit-action-azure-blob-storage.md)
* [Microsoft Power Automate에 제출](/help/forms/forms-microsoft-power-automate-integration.md)
* [Adobe Workfront Fusion에 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Adobe Marketo Engage에 제출](/help/forms/submit-adaptive-form-to-marketo-engage.md)

>[!NOTE]
>
> AEM Publish의 Google Sheet/Excel을 타기팅하더라도 직접적인 Forms 제출 서비스와는 다른 구성 단계가 필요합니다.

**AEM Publish 제출 순서도**

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

![AEM Publish 제출 순서도](/help/forms/assets/eds-aem-publish.png)
이 순서도는 AEM Publish에 양식을 제출하는 과정을 보여 주며, 이후 복잡한 백엔드 작업을 처리합니다.

### Forms 제출 서비스와 AEM Publish 제출 비교

| 기능 | Forms 제출 서비스 | AEM Publish 제출 |
| :- | :- | :-- |
| **적합한 대상** | 스프레드시트, 이메일 알림에 대한 간단한 데이터 캡처 | 복잡한 워크플로, 엔터프라이즈 통합, 사용자 정의 논리 |
| **양식 작성** | 문서 기반에 적합, 간단한 UE 양식에 좋음 | Universal Editor에서 작성한 양식에 가장 적합 |
| **설정 노력** | 낮음 (종종 간단한 구성) | 더 높음 (AEM Publish, Dispatcher, OSGi, CDN 설정 필요) |
| **백엔드 시스템** | Adobe 호스팅 서비스 | AEM as a Cloud Service 게시 인스턴스 |
| **유연성** | 시트/이메일로 제한 | 매우 유연하고 다양한 AEM Forms 액션 범위 |
| **예** | Google Sheet로 연락처 양식 데이터 전송 | AEM 승인 워크플로를 트리거하는 대출 신청 |

## 다양한 사이트 또는 페이지에 양식을 임베드하는 방법

때때로 한 곳(예: 중앙 “양식 사이트”)에서 만들어지고 관리되는 양식을 다른 웹 페이지나 사이트에 표시하고 싶을 때가 있습니다.

### 양식을 임베드하는 이유는 무엇입니까?

* Universal Editor로 작성된 표준 “문의하기” 양식이 문서 기반 작성 기능으로 구축된 여러 랜딩 페이지에 표시되어야 합니다.
* 귀하의 주요 웹 사이트 콘텐츠가 문서 작성(DA)에 있으며, 전문 양식을 포함해야 합니다.
* 여러 EDS 프로젝트에서 잘 관리된 단일 양식을 재사용하고자 합니다.

### 양식 임베드의 기술적 작동 방식

양식을 표시하려는 페이지(이하 “호스트 페이지”)에는 특정 코드(일반적으로 특수 블록 또는 스크립트)가 포함됩니다. 사용자가 호스트 페이지를 방문하면 이 코드는 실제 양식이 호스팅되는 URL에 요청을 합니다(이를 “양식 소스”라고 함). 그러면 양식 소스가 HTML을 다시 보내고, 호스트 페이지가 이를 삽입하여 표시합니다.

**임베드된 양식 아키텍처**

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

![임베드된 양식 아키텍처](/help/forms/assets/eds-embedded-form.png)
이 다이어그램은 호스트 페이지가 양식 소스에서 양식 HTML을 가져와서 표시하는 모습을 보여 줍니다. 제출은 원본 양식의 구성된 엔드포인트를 사용합니다.

## 임베드된 양식에 대해 CORS 설정

[CORS(원본 간 리소스 공유)](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)는 브라우저 보안 기능입니다. 호스트 페이지(예: `site-a.com`)가 다른 도메인(예: `forms-site-b.com`)에서 양식을 가져오려고 하면 `forms-site-b.com`에서 CORS 헤더를 통해 명시적으로 허용하지 않는 한 브라우저가 이를 차단합니다.

**양식 소스 서버**&#x200B;에 CORS 헤더가 올바르지 않은 경우 브라우저가 호스트 페이지에서 양식을 로드하지 못하게 하여 임베드된 양식이 나타나지 않습니다.

### 양식을 제공하는 사이트에서 CORS를 구성하는 방법은 무엇입니까?

**양식 소스**&#x200B;를 호스팅하는 서버가 응답에 특정 HTTP 헤더를 보내도록 구성해야 합니다. 정확한 방법은 EDS 설정에 따라 달라집니다(예: Franklin 프로젝트의 경우 CDN 동작이나 에지 작업자 논리를 제어하는 GitHub 저장소의 `helix-config.yaml` 또는 유사한 구성 파일에서 자주 수행됩니다).
양식 소스의 응답에 추가할 주요 헤더:

* `Access-Control-Allow-Origin: <URL_of_Host_Page>` (예: `https://your-site.com`). 테스트를 위해 `*`를 사용할 수 있지만 프로덕션의 경우 정확한 도메인을 지정해야 합니다.
* `Access-Control-Allow-Methods: GET, OPTIONS` (양식 제출 자체가 원본 간인 경우 `POST`가 필요할 수 있지만 일반적으로 제출은 동일한 원본 또는 특별히 구성된 별도의 엔드포인트로 이동합니다).
* `Access-Control-Allow-Headers: Content-Type` (및 양식 가져오기에 사용할 수 있는 기타 사용자 정의 헤더).

**예 (구성 파일에 대한 개념):**

```yaml
        # In the configuration for the site HOSTING THE FORM (Form Source)
        headers:
          # Apply to paths where your forms are served, e.g., /forms/**
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-page-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS
```

## 추가 고려 사항: CDN 및 다중 코드베이스 (Helix 4)

* **CDN 규칙:** CDN에서 요청을 프록시하는 방법을 제공할 수도 있습니다. 예를 들어 `host-page.com/embedded-form`에 대한 요청은 CDN에 의해 내부적으로 라우팅되어 `form-source.com/actual-form`에서 콘텐츠를 가져오게 되어 브라우저에 동일한 원본으로 표시될 수 있습니다. 설정하기 복잡할 수 있습니다.
* **다중 코드베이스(Helix 4):** 호스트 페이지와 양식 소스가 서로 다른 GitHub 저장소에 있는 경우(Helix 4 설정에서는 일반적), 양식을 렌더링하거나 관리하는 데 필요한 JavaScript “양식 블록”이 호스트 페이지의 코드베이스에서 사용 가능한지 또는 양식 소스에서 가져온 양식 HTML이 모든 필수 JavaScript와 자체 포함형인지 확인합니다. 원본 문서에는 “다른 코드베이스를 가진 helix4의 경우, 두 코드베이스 모두에 양식 블록을 추가해야 합니다”고 언급되어 있습니다.

### 일반적인 아키텍처 설정 및 구성 단계

다음은 작성 방법과 제출 전략을 결합하여 양식을 설정하는 몇 가지 일반적인 방법과 주요 구성 사항입니다.

#### 스프레드시트/이메일 제출이 가능한 문서 기반 양식

가장 간단한 설정입니다. Word/Google Docs에서 양식을 작성하면 Forms 제출 서비스를 통해 스프레드시트나 이메일로 데이터를 제출합니다.

1. 지정된 테이블 구조 또는 양식 블록을 사용하여 Word/Google Doc/Sheet에서 양식을 정의합니다.
1. 문서(또는 관련 구성)에서 Forms 제출 서비스의 대상 스프레드시트 URL 또는 이메일 주소를 지정합니다.
1. `forms@adobe.com`(또는 관련 서비스 계정)이 대상 스프레드시트에 대한 편집 권한을 가지고 있는지 확인합니다.
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

#### 스프레드시트/이메일 제출이 가능한 Universal Editor 양식

시각적 Universal Editor를 사용하여 양식을 작성하지만 데이터 캡처를 위해 간단한 Forms 제출 서비스를 여전히 사용합니다.

1. AEM의 Universal Editor를 사용하여 양식을 만듭니다.
1. UE에서 양식 제출 액션을 구성하여 “Forms 제출 서비스에 제출” 옵션을 사용합니다.
1. 대상 스프레드시트 URL이나 이메일 주소를 지정합니다.
1. 스프레드시트를 사용하는 경우 `forms@adobe.com`에 편집 권한이 있는지 확인합니다.
1. AEM에서 Edge Delivery 사이트로 양식이 포함된 페이지를 게시합니다.

   **Universal Editor + Forms 제출 서비스 아키텍처**

   ![Universal Editor + Forms 제출 서비스 아키텍처](/help/forms/assets/eds-ue-fss.png)

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

#### AEM Publish 제출을 포함한 Universal Editor 양식 (고급)

이 설정은 Universal Editor를 사용하여 양식을 생성하고 AEM Publish 인스턴스를 사용하여 강력한 백엔드 처리(워크플로, FDM 등)를 수행합니다. 여기에는 추가 구성이 필요합니다.

1. **UE에 양식 만들기:** Universal Editor에서 양식을 작성합니다. AEM Forms 액션을 가리키도록 제출 액션을 구성합니다(예: “AEM 워크플로 호출”, “양식 데이터 모델을 사용하여 제출”).
1. **AEM Dispatcher 구성(AEM Publish 계층):**
   * **리디렉션 금지**: Dispatcher 규칙이 요청을 `/adobe/forms/af/submit/...` 경로로 *리디렉션하지 않도록 합니다*.
   * **제출 허용:** Dispatcher 필터(예: `filters.any`)를 수정하여 Edge Delivery 사이트의 도메인 또는 IP 주소에서 `/adobe/forms/af/submit/...`에 POST 요청을 명시적으로 허용(`allow`)합니다.
1. **AEM의 OSGi 레퍼러 필터(AEM Publish 계층):**
   * AEM OSGi 콘솔(`/system/console/configMgr`)에서 “Apache Sling 레퍼러 필터”를 찾아 구성합니다.
   * Edge Delivery 사이트의 도메인(예: `https://your-eds-domain.hlx.page`, `https://your-custom-eds-domain.com`)을 “허용 호스트” 또는 “허용 호스트 정규식” 목록에 추가합니다. 이를 통해 AEM은 귀하의 EDS 사이트에서 제출된 자료를 수락하게 됩니다.
1. **CDN 리디렉션 규칙(Edge Delivery CDN):**
   * Edge Delivery 사이트(예: `your-eds-domain.hlx.page`)는 제출 요청을 AEM Publish 인스턴스로 올바르게 라우팅해야 합니다.
   * EDS 페이지의 양식을 제출할 때 `/adobe/forms/af/submit/...`과 같은 상대 경로를 대상으로 할 수 있습니다. Edge Delivery CDN(또는 에지 작업자)에 “요청이 `your-eds-domain.hlx.page/adobe/forms/af/submit/...`에 오면 `your-aem-publish-instance.com/adobe/forms/af/submit/...`으로 전달(프록시 또는 리디렉션)합니다.”와 같은 규칙이 필요합니다.
   * 정확한 구현은 CDN 공급자(예: Fastly VCL, Akamai Property Manager, Cloudflare Workers)에 따라 달라집니다.
1. **(선택 사항) 개발용 `constants.js`(EDS 프로젝트의 코드베이스):**
   * 로컬 개발이나 클라이언트측 양식 스크립트가 전체 AEM Publish URL을 알아야 하는 경우 Edge Delivery 프로젝트의 GitHub 저장소 내의 `constants.js` 또는 유사한 구성 파일에서 이를 구성할 수 있습니다. 예:

   ```javascript
       // in your-eds-project/scripts/constants.js
       export const AEM_PUBLISH_URL = 'https://publish-p123-e456.adobeaemcloud.com';
            // Your form submission script might then construct the submit URL:
           // const submitUrl = `${AEM_PUBLISH_URL}/adobe/forms/af/submit/...`;
   ```

1. **게시:** 양식 페이지를 AEM에서 EDS로 게시하고 모든 AEM 구성이 AEM Publish 인스턴스에서 활성화되어 있는지 확인합니다.

   **Universal Editor + AEM Publish 아키텍처**

![Universal Editor + AEM Publish 아키텍처](/help/forms/assets/eds-aem-publish.png)

다음은 사용자가 EDS 사이트에 제출하고 CDN이 AEM Dispatcher로 라우팅한 다음 AEM Publish가 처리하는 흐름을 보여 줍니다.

#### 문서 작성(DA) 페이지에 양식 임베드

귀하의 주요 웹 사이트 콘텐츠는 문서 작성(DA)에서 생성됩니다. 문서 기반 작성 또는 Universal Editor를 별도로 사용하여 양식을 만든 다음 DA 페이지에 임베드합니다.

1. **양식 만들기 및 게시:**
   * 문서 기반 작성 또는 Universal Editor를 사용하여 양식을 만듭니다.
   * 제출 방법을 구성합니다(설정 1, 2 또는 3에 따라 Forms 제출 서비스 또는 AEM Publish).
   * 이 양식을 자체 Edge Delivery URL(예: `.../forms/my-special-form`)에 실시간으로 게시합니다.
1. **CORS 구성:** 이 독립 실행형 양식을 호스팅하는 Edge Delivery 사이트/프로젝트에서 문서 작성 사이트의 도메인을 가져올 수 있도록 CORS 헤더가 설정되어 있는지 확인합니다.
1. **DA의 작성자 페이지:** 문서 작성에서 페이지를 만들거나 편집합니다.
1. **양식 블록 임베드:** DA에서 적절한 블록을 사용하여 외부 URL을 임베드합니다. 이 블록을 독립 실행형 게시 양식의 URL로 지정합니다.
1. **DA 페이지 게시:** DA 페이지를 게시합니다. 이제 양식을 가져와서 표시합니다.

   **DA 아키텍처에 임베드된 양식**

   ![DA 아키텍처에 임베드된 양식](/help/forms/assets/eds-forms-embedd-da.png)

   다른 EDS 위치에서 양식을 가져오는 DA 페이지를 보여 줍니다. 임베드된 양식은 스스로 제출을 처리합니다.

## 문제 해결

* **내 양식 제출이 작동하지 않습니다.**
   * **콘솔 오류 확인:** 브라우저의 개발자 콘솔(일반적으로 F12)을 열고 제출할 때 네트워크 탭이나 콘솔 탭에서 오류를 확인합니다.
   * **제출 URL 확인:** 양식이 올바른 엔드포인트(Forms 제출 서비스 URL 또는 AEM Publish 경로)에 제출하려고 합니까?
   * **Forms 제출 서비스:** 스프레드시트로 전송하는 경우 `forms@adobe.com`에 편집 권한이 부여됩니까? 스프레드시트 URL이 정확합니까?
   * **AEM Publish 제출:**
      * Dispatcher가 POST를 `/adobe/forms/af/submit/...`에 허용하고 있습니까?
      * AEM Publish의 Sling 레퍼러 필터가 EDS 도메인을 허용하도록 구성되어 있습니까?
      * `/adobe/forms/af/submit/...`에 대한 CDN 리디렉션 규칙이 올바르게 작동하고 있습니까?

* **임베드된 양식이 나타나지 않습니다.**

   * **CORS!** 이것이 가장 흔한 이유입니다. CORS 오류가 있는지 브라우저 콘솔을 확인합니다. 양식을 *호스팅*&#x200B;하는 사이트에 올바른 `Access-Control-Allow-Origin` 헤더가 있는지 확인합니다.
   * **양식 URL이 올바릅니까?** 호스트 페이지의 임베드 코드가 양식의 올바른 실시간 URL을 가리키고 있습니까?
   * **JavaScript 블록:** 양식이 렌더링을 위해 특정 JavaScript “양식 블록”에 의존하는 경우, 해당 블록의 코드를 호스트 페이지에서 사용할 수 있습니까?

* **AEM Publish에 제출하면 “403 금지됨” 또는 “401 인증되지 않음”이라는 메시지가 나타납니다.**

   * 이는 AEM Publish의 Sling 레퍼러 필터가 EDS 도메인에서 요청을 허용하지 않는다는 것을 의미합니다. 구성을 다시 한번 확인합니다.
   * 표준 양식 제출물은 일반적으로 익명으로 처리되지만 AEM 제출 엔드포인트에 필요한 경우 인증/허가 문제일 수도 있습니다.

## 다음 단계

이 안내서는 AEM Edge Delivery Services에서 양식 사용에 대한 개요를 제공합니다. 특정 구성에 대한 자세한 단계별 지침은 공식 Adobe Experience Manager 설명서를 참조하십시오.

* [Edge Delivery Services Forms가 포함된 문서 기반 작성](/help/edge/docs/forms/tutorial.md)
* [Edge Delivery Services Forms가 포함된 Universal Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [문서 작성(DA) 및 콘텐츠 임베드](https://www.aem.live/developer/da-tutorial)
* [AEM Forms 제출 서비스](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
