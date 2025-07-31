---
title: 적응형 양식에 대한 제출 액션을 구성하는 방법
description: 적응형 양식은 여러 제출 액션을 제공합니다. 제출 액션은 적응형 양식이 제출 후 처리되는 방식을 정의합니다. 기본 제공 제출 액션을 사용하거나 직접 만들 수 있습니다.
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
role: User, Developer
source-git-commit: c0df3c6eaf4e3530cca04157e1a5810ebf5b4055
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 58%

---


# 적응형 Forms에서 지원하는 작업 제출

적응형 양식을 사용하여 멋지고, 반응이 빠르고, 동적이고, 적응력이 뛰어난 양식을 만들 수 있습니다. 직관적인 사용자 인터페이스와 양식을 효율적으로 디자인하고 관리할 수 있는 기본 구성 요소 세트를 제공합니다. 양식 데이터를 OneDrive, SharePoint, Workfront Fusion 등의 서비스로 보내도록 다양한 제출 액션을 구성할 수 있습니다.

사용자가 적응형 양식에서 **[!UICONTROL 제출]** 단추를 클릭하면 제출 액션이 트리거됩니다. Forms as a Cloud Service은 몇 가지 제출 액션을 즉시 제공합니다. 기본 제공 제출 액션을 사용하면 다음 작업을 수행할 수 있습니다.

* 전자 메일을 통해 손쉽게 양식 데이터 보내기
* 데이터를 전송하는 동안 Microsoft® Power Automate 플로우 또는 AEM 워크플로우를 시작합니다.
* 양식 데이터를 Microsoft® SharePoint Server, Microsoft® Azure Blob Storage 또는 Microsoft® OneDrive로 직접 전송합니다.
* 양식 데이터 모델(FDM)을 사용하여 구성된 데이터 소스에 데이터를 원활하게 전송합니다.
* 편리하게 데이터를 REST 엔드포인트에 제출합니다.

## 적응형 Forms에서 지원하는 작업 제출

AEM forms에서는 다음과 같은 기본 제출 액션을 제공합니다.

* [이메일 보내기](/help/forms/configure-submit-action-send-email.md)
* [Power Automate 플로우 호출](/help/forms/forms-microsoft-power-automate-integration.md)
* [SharePoint에 제출](/help/forms/configure-submit-action-sharepoint.md)
* [Workfront Fusion 호출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [양식 데이터 모델(FDM)을 사용하여 제출](/help/forms/using-form-data-model.md)
* [Azure Blob 스토리지에 제출](/help/forms/configure-submit-action-azure-blob-storage.md)
* [REST 엔드포인트에 제출](/help/forms/configure-submit-action-restpoint.md)
* [OneDrive에 제출](/help/forms/configure-submit-action-onedrive.md)
* [AEM Workflow 호출](/help/forms/configure-submit-action-workflow.md)
* [Marketo 조직에 제출](/help/forms/submit-adaptive-form-to-marketo-engage.md)
* [Adobe Experience Platform(AEP)에 제출](/help/forms/aem-forms-aep-connector.md)
* [스프레드시트에 제출](/help/forms/forms-submission-service.md)

적응형 양식을 다른 스토리지 구성에 제출할 수도 있습니다.

* [Salesforce 애플리케이션에 적응형 양식 연결](/help/forms/aem-forms-salesforce-integration.md)
* [Microsoft에 적응형 양식 연결](/help/forms/ms-dynamics-odata-configuration.md)

## 작성 유형 간 작업 지원 제출

아래 표는 AEM Forms에서 사용되는 양식 작성 방법을 기반으로 지원되는 제출 액션을 보여 줍니다.

| 제출 동작 | [기초 구성 요소](/help/forms/configuring-submit-actions.md) | [핵심 구성 요소](/help/forms/configure-submit-actions-core-components.md) | [범용 편집기](/help/forms/configure-submit-action-eds-forms.md#submit-actions-supported-by-adaptive-forms-created-in-universal-editor) | [문서 기반 Forms](/help/forms/configure-submit-action-eds-forms.md#supported-submit-actions-for-document-based-forms) |
|----------------------------|------------------------|------------------|------------------|------------------------|
| 이메일 보내기 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| 전원 자동화 플로우 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| SharePoint에 제출 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| Workfront Fusion | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| FDM을 사용하여 제출 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| AEP에 제출 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| Azure Blob 저장소 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| REST 끝점에 제출 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| Marketo Engage에 제출 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| OneDrive에 제출 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| AEM 워크플로 호출 | ✅ 지원됨 | ✅ 지원됨 | ✅ 지원됨 |                        |
| 스프레드시트에 제출 |                        |                  | ✅ 지원됨 | ✅ 지원됨 |


## 적응형 양식에서 서버측 유효성 재검사

일반적으로 온라인 데이터 캡처 시스템에서 개발자는 몇 가지 비즈니스 규칙을 적용하기 위해 클라이언트측에 대해 JavaScript 유효성 검사를 일부 실시합니다. 단, 최신 브라우저에서 최종 사용자는 이러한 유효성 검사를 무시하고 웹 브라우저 DevTools 콘솔과 같은 다양한 기술을 사용하여 수동으로 제출 액션을 수행할 수 있습니다. 이러한 기술은 적응형 양식에도 유효합니다. 양식 개발자는 다양한 유효성 검사 논리를 만들 수 있지만 기술적 측면에서 최종 사용자는 이러한 유효성 검사 논리를 무시하고 잘못된 데이터를 서버에 제출할 수 있습니다. 잘못된 데이터로 인해 양식 작성자가 적용한 비즈니스 규칙이 깨질 수 있습니다.

서버측 유효성 재검사 기능을 통해 서버에서 적응형 양식을 디자인하면서 적응형 양식 작성자가 제공한 유효성 검사를 실행할 수도 있습니다. 양식 유효성 검사에 표시되는 데이터 제출 및 비즈니스 규칙 위반 사항에 발생할 수 있는 잠재적 손상을 방지할 수 있습니다.


### 서버에서의 유효성 검사 대상은 무엇입니까?

서버에서 다시 실행되는 적응형 양식에 대한 즉시 사용할 수 있는(OOTB) 필드 유효성 검사는 다음과 같습니다.

* 필수
* 유효성 검사 픽처 구절
* 유효성 검사 표현식

사이드바의 적응형 양식 컨테이너 아래에 있는 **[!UICONTROL 서버측 유효성 재검사]**&#x200B;를 사용하여 현재 양식에 대해 서버측 유효성 검사를 활성화하거나 비활성화합니다.

![서버측 유효성 검사 활성화](assets/revalidate-on-server.png)

**서버측 유효성 검사 활성화**

최종 사용자가 이러한 유효성 검사를 무시하고 양식을 제출하면 서버에서 다시 유효성 검사를 수행합니다. 유효성 검사가 서버 끝에서 실패하면 제출 트랜잭션이 중지됩니다. 사용자에게 다시 원본 양식이 표시됩니다. 캡처된 데이터와 제출된 데이터는 사용자에게 오류로 표시됩니다.

>[!NOTE]
>
>서버측 유효성 검사는 양식 모델의 유효성을 검사합니다. 별도의 클라이언트 라이브러리를 만들어 유효성을 검사하고 동일한 클라이언트 라이브러리에서 HTML 스타일링과 DOM 조작과 같은 다른 항목과 혼합하지 않는 것이 좋습니다.

<!--### Supporting Custom functions in Validation Expressions {#supporting-custom-functions-in-validation-expressions-br}

At times, if there are **complex validation rules**, the exact validation script reside in custom functions and author calls these custom functions from field validation expression. To make this custom function library known and available while performing server-side validations, the form author can configure the name of AEM client library under the **[!UICONTROL Basic]** tab of Adaptive Form Container properties as shown below.

![Supporting Custom functions in Validation Expressions](assets/clientlib-cat.png)

Supporting Custom functions in Validation Expressions

Author can configure customJavaScript library per Adaptive Form. In the library, only keep the reusable functions, which have dependency on jquery and underscore.js third-party libraries.

Refer to the following articles to learn how to create custom functions for:

* [Adaptive Forms based on Foundation Components](/help/forms/rule-editor.md#custom-functions-in-rule-editor)
* [Adaptive Forms based on Core Components](/help/forms/create-and-use-custom-functions.md)
* [Adaptive Forms authored using Document-Based Authoring](/help/edge/docs/forms/rules-forms.md#create-a-custom-function)
* [Adaptive Forms created using the Universal Editor](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md#create-a-custom-function)

## Error handling on Submit Action {#error-handling-on-submit-action}

As a part of AEM security and hardening guidelines, configure custom error pages such as 400.jsp, 404.jsp, and 500.jsp. These handlers are called, when on submitting a form 400, 404, or 500 errors appear. The handlers are also called when these error codes are triggered on the Publish node. You can also create JSP pages for other HTTP error codes.

When you prefill a form data model (FDM), or schema based Adaptive Form with XML or JSON data complaint to a schema that is data does not contain `<afData>`, `<afBoundData>`, and `</afUnboundData>` tags, then the data of unbounded fields of the Adaptive Form is lost. The schema can be an XML schema, JSON schema, or a Form Data Model (FDM). Unbounded fields are Adaptive Form fields without the `bindref` property.-->

## 추가 참조

{{af-submit-action}}

