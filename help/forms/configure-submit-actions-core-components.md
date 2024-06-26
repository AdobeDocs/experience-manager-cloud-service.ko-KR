---
title: 적응형 양식에 대한 제출 액션을 구성하는 방법
description: 적응형 양식은 여러 제출 액션을 제공합니다. 제출 액션은 적응형 양식이 제출 후 처리되는 방식을 정의합니다. 기본 제공 제출 액션을 사용하거나 직접 만들 수 있습니다
keywords: 적응형 양식에 대한 제출 액션을 선택하고, 적응형 양식을 sharepoint 목록에 연결하고, 적응형 양식을 sharepoint 문서 라이브러리에 연결하고, 적응형 양식을 양식 데이터 모델(FDM)에 연결하는 방법
feature: Adaptive Forms, Core Components
exl-id: 495948e8-30a7-4e7c-952f-c71de15520f0
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 49%

---


# 적응형 양식 제출 액션 {#configuring-the-submit-action}

<span class="preview"> 핵심 구성 요소를 사용하여 [AEM Sites 페이지에 적응형 양식을 추가하거나](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) [독립 적응형 양식을 만드는 것](/help/forms/creating-adaptive-form-core-components.md)이 좋습니다. </span>


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service | 이 문서 |

제출 액션을 사용하면 적응형 양식을 통해 캡처되는 데이터의 대상을 선택할 수 있습니다. 사용자가 적응형 양식에서 **[!UICONTROL 제출]** 버튼을 클릭하면 제출 액션이 트리거됩니다. 핵심 구성 요소를 기반으로 하는 적응형 양식의 Forms as a Cloud Service는 다수의 사전 빌드된 제출 액션을 제공합니다. 이러한 기본 제공 제출 액션을 통해 다음과 같은 작업을 수행할 수 있습니다.

* 이메일을 통해 양식 데이터를 손쉽게 전송합니다.
* 데이터를 전송하는 동안 Microsoft® Power Automate 플로우 또는 AEM 워크플로우를 시작합니다.
* 양식 데이터를 Microsoft® SharePoint Server, Microsoft® Azure Blob Storage 또는 Microsoft® OneDrive로 직접 전송합니다.
* 양식 데이터 모델(FDM)을 사용하여 구성된 데이터 소스에 데이터를 원활하게 전송합니다.
* 편리하게 데이터를 REST 엔드포인트에 제출합니다.

다음을 수행할 수 있습니다. [기본 제출 액션 확장](custom-submit-action-form.md). 조직별 요구 사항에 대해 제출 액션을 사용자 지정할 수도 있습니다.

적응형 양식에 대한 제출 액션을 정의하려면 의 구성 대화 상자 를 사용합니다 **적응형 양식 컨테이너** 구성 요소. 의 구성 대화 상자 **적응형 양식 컨테이너** 구성 요소에는 다음이 포함됩니다.
* 기본 탭
* 양식 데이터 모델 탭
* 제출 탭

구성 대화 상자를 사용하여 양식 컨테이너 속성을 정의할 수 있습니다. 양식 컨테이너 구성 요소의 구성 대화 상자에 대해 자세히 알아보려면 다음을 수행하십시오. [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html)

## 적응형 양식의 제출 액션 선택 및 구성 {#select-and-configure-submit-action}

양식의 제출 액션을 선택하고 구성하려면 다음 작업을 수행하십시오.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.

1. **[!UICONTROL 제출]** 탭을 클릭합니다.

   ![제출 액션을 구성하려면 공구 모양 아이콘을 클릭하여 적응형 양식 컨테이너 대화 상자를 엽니다.](/help/forms/assets/adaptive-forms-submit-message.png)

1. 선택 및 구성 **[!UICONTROL 제출 액션]**&#x200B;을 참조하십시오.

적응형 양식 제출을 위해 다양한 작업을 구성할 수도 있습니다.
* **리디렉션 URL/경로** - 이 옵션을 사용하면 적응형 양식을 제출한 후 양식 사용자가 리디렉션되는 각 양식에 대한 페이지를 구성할 수 있습니다.
* **메시지 표시** - 이 옵션을 사용하면 적응형 양식이 정상적으로 제출될 때 표시되는 메시지를 추가할 수 있습니다. 미리 정의된 텍스트는 대화 상자에 포함되어 사용자가 수정할 수 있습니다.

다음 제출 작업에 대한 자세한 내용은 다음을 참조하십시오.

* [이메일 보내기](/help/forms/configure-submit-action-send-email.md)
* [Power Automate 플로우 호출](/help/forms/forms-microsoft-power-automate-integration.md)
* [SharePoint에 제출](/help/forms/configure-submit-action-sharepoint.md)
* [Workfront Fusion 호출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [양식 데이터 모델(FDM)을 사용하여 제출](/help/forms/using-form-data-model.md)
* [Azure Blob 스토리지에 제출](/help/forms/configure-submit-action-azure-blob-storage.md)
* [REST 엔드포인트에 제출](/help/forms/configure-submit-action-restpoint.md)
* [OneDrive에 제출](/help/forms/configure-submit-action-onedrive.md)
* [AEM Workflow 호출](/help/forms/configure-submit-action-workflow.md)

적응형 양식을 다른 스토리지 구성에 제출할 수도 있습니다.

* [Salesforce 애플리케이션에 적응형 양식 연결](/help/forms/aem-forms-salesforce-integration.md)
* [Microsoft® Dynamics OData에 적응형 양식 연결](/help/forms/ms-dynamics-odata-configuration.md)

다음을 수행할 수 있습니다. [기본 제출 액션 사용자 정의](custom-submit-action-form.md). 또한 특정 조직 요구 사항에 맞게 제출 액션을 사용자 지정할 수 있습니다.


<!--
## Send Email {#send-email}

To send an email to one or more recipients upon successful submission of the form, you can use the **[!UICONTROL Send Email]** Submit Action. 

Refer to [configure the send email submit action for an Adaptive Form](/help/forms/configure-submit-action-send-email.md) to learn how to set up an Adaptive Form to send an email upon successful submission.
[!NOTE]
>
>Send PDF via Email Submit Action is applicable only to Adaptive Forms that use XFA template as form model. 

>[!NOTE]
>
>Ensure that the [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>exists. The directory is required to temporarily store attachments. If the directory does not exist, create it.


>[!CAUTION]
>
>If you  [prefill](prepopulate-adaptive-form-fields.md) a form template,  a Form Data Model (FDM) or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema , form template, or form data model (FDM)) that is data does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost. 

>[!CAUTION]
>
>If you [prefill](prepopulate-adaptive-form-fields.md) a form template, a Form Data Model (FDM) or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema, or form data model(FDM)) that does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost.

## Submit to Microsoft® SharePoint {#submit-to-sharedrive}

The **[!UICONTROL Submit to SharePoint]** Submit Action connects an Adaptive Form with a Microsoft&reg; SharePoint Storage. You can submit the form data files, attachments, or Document of Record to the connected Microsoft&reg; Sharepoint Storage. 

Integration of AEM Adaptive Form with Microsoft® SharePoint enables the submission, retrieval, or storage of data, files, and other relevant information within the SharePoint storage. To learn how to configure submit to SharePoint submit action for an Adaptive Form, [click here.](/help/forms/configure-submit-action-sharepoint.md) 

## Submit using Form Data Model (FDM) {#submit-using-form-data-model}

The **[!UICONTROL Submit using Form Data Model (FDM)]** Submit Action writes submitted Adaptive Form data for the specified data model object in a Form Data Model (FDM) to its data source. When configuring the Submit Action, you can choose a data model object whose submitted data you want to write back to its data source.

When a user submits a form based on a form data model (FDM), you can [configure the form to write the submitted data to the data sources associated with the data model object.](/help/forms/using-form-data-model.md#write-submitted-adaptive-form-data-into-data-sources-write-af)

## Submit to REST endpoint {#submit-to-rest-endpoint}

The **[!UICONTROL Submit to REST Endpoint]** submit action sends the submitted data to a REST URL. This URL can be either an internal server (the server where the form is displayed) or an external server. The data of an Adaptive Form is submitted to a REST URL using the **[!UICONTROL Submit to REST endpoint]** Submit Action.

For a comprehensive guide on the detailed steps to post or submit data to a REST URL, refer to [configure submit to REST Endpoint submit action for Adaptive Forms.](/help/forms/configure-submit-action-restpoint.md)

## Invoke an AEM Workflow {#invoke-an-aem-workflow}

The **[!UICONTROL Invoke an AEM Workflow]** Submit Action integrates an Adaptive Form with an [AEM Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem). When a form is submitted, the selected workflow starts automatically. 

 [Integrate AEM Adaptive Form with AEM Workflow: Streamlining Business Processes](/help/forms/configure-submit-action-workflow.md) provides step-by-step instructions to seamlessly integrate AEM Workflow with Adaptive Forms, optimizing business processes and enhancing workflow automation.

## Submit to OneDrive {#submit-to-onedrive}

The **[!UICONTROL Submit to OneDrive]** Submit Action connects an Adaptive Form with a Microsoft&reg; OneDrive. You can submit the form data, files, attachments, or Document of Record to the connected Microsoft&reg; OneDrive Storage. 

AEM Forms Cloud Service with Microsoft® OneDrive helps in optimize data submission. Explore the steps of [integrating OneDrive with AEM Forms](/help/forms/configure-submit-action-onedrive.md) for streamlined and secure storage.

## Submit to Azure Blob Storage {#submit-to-azure-blob-storage}

The **[!UICONTROL Submit to Azure Blob Storage]** Submit Action connects an Adaptive Form with a Microsoft® Azure portal and allows you to submit various elements such as form data, files, attachments, or Document of Record to the associated Azure Storage containers.

AEM as a Cloud Service allows submitting data to Azure Storage from AEM Adaptive Forms. Learn how to [create and use Azure Blob Storage configuration in AEM Forms](/help/forms/configure-submit-action-azure-blob-storage.md) for efficient data storage. 

To set values of a configuration, [Generate OSGi Configurations using the AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), and [deploy the configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) to your Cloud Service instance.

## Submit to Power Automate {#microsoft-power-automate}

You can configure an Adaptive Form to run a Microsoft&reg; Power Automate Cloud Flow on submission. The configured Adaptive Form sends captured data, attachments, and Document Of Record to Power Automate Cloud Flow for processing. It helps you build custom data capture experience while harnessing the power of Microsoft&reg; Power Automate to build business logics around captured data and automate customer workflows. 
Adaptive Forms editor provides the **Invoke a Microsoft&reg; Power Automate flow** submit action to send adaptive forms data, attachments, and Document Of Record to Power Automate Cloud Flow. To use the Submit action to send captured data to Microsoft&reg; Power Automate, [Connect your Forms as a Cloud Service instance with Microsoft&reg; Power Automate](forms-microsoft-power-automate-integration.md)  

After a successful configuration, use the [Invoke a Microsoft&reg; Power Automate flow](forms-microsoft-power-automate-integration.md#use-the-invoke-a-microsoft&reg;-power-automate-flow-submit-action-to-send-data-to-a-power-automate-flow-use-the-invoke-microsoft-power-automate-flow-submit-action) submit action to send data to a Power Automate Flow.  

## Submit to Workfront Fusion {#workfront-fusion}

You can configure an Adaptive Form to submit data to Workfront Fusion on submission. Workfront Fusion allows automation of processes so that user can concentrate on new tasks rather than repeating the same tasks again and again. It automates both simple and complex tasks, saving time and ensuring consistent process execution.

The Adaptive Forms editor provides the **Invoke a WorkFront Fusion Scenario** submit action to send Adaptive Forms data or attachments to a Workfront Fusion scenario. To use the submit action for sending captured data to a Workfront Fusion scenario, refer to [Submit an Adaptive Form to Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md).

## Send PDF via Email {#send-pdf-via-email}

The **Send PDF via Email** Submit Action sends an email with a PDF containing form data, to one or more recipients on successful submission of the form.

>[!NOTE]
>
>This Submit Action is available for XFA-based Adaptive Forms and XSD-based adaption forms that have the Document of Record template. 
## Invoke a forms workflow {#invoke-a-forms-workflow}

The **Submit to Forms workflow** submit option sends a data xml and file attachments (if any) to an existing Adobe LiveCycle or [!DNL AEM Forms] on JEE process.

For information about how to configure the Submit to forms workflow Submit Action, see [Submitting and processing your form data using forms workflows](submit-form-data-livecycle-process.md). 
## Forms Portal Submit Action {#forms-portal-submit-action}

The **Forms Portal Submit Action** option makes form data available through an [!DNL AEM Forms] portal.

For more information about the Forms Portal and Submit Action, see [Drafts and submissions component](draft-submission-component.md). 

## Use synchronous or asynchronous submission {#use-synchronous-or-asynchronous-submission}

A Submit Action can use synchronous or asynchronous submission.

**Synchronous submission**: Traditionally, web forms are configured to submit synchronously. In a synchronous submission, when users submit a form, they are redirected to an acknowledgment page, a thank you page, or if there is submission failure, an error page. You can select the **[!UICONTROL Use asynchronous submission]** option to redirect the users to a webpage or show a message on submission.  

![Configure Submit Action](assets/thank-you-setting.png)

**Asynchronous submission**: Modern web experiences like single page applications are gaining popularity where the web page remains static while client-server interaction happens in the background. You can now provide this experience with Adaptive Forms by [configuring asynchronous submission](asynchronous-submissions-adaptive-forms.md).

## Server-Side Revalidation in Adaptive Form {#server-side-revalidation-in-adaptive-form}

Typically, in any online data capture system, developers place someJavaScript validations on client side to enforce a few business rules. But in modern browsers, end users have way to bypass those validations and manually do submissions using various techniques, Such as Web Browser DevTools Console. Such techniques are also valid for Adaptive Forms. A forms developer can create various validation logics, but technically, end users can bypass those validation logics and submit invalid data to the server. Invalid data would break the business rules that a form author has enforced.

The server-side revalidation feature provides the ability to run the validations that an Adaptive Forms author has provided while designing an Adaptive Form on the server. It prevents any possible compromise of data submissions and business rules violations represented in terms of form validations.

### What to validate on Server? {#what-to-validate-on-server-br}

All out of the box (OOTB) field validations of an Adaptive Form that are rerun at the server are:

* Required
* Validation Picture Clause
* Validation Expression

### Enabling Server-side Validation {#enabling-server-side-validation-br}

Use the **[!UICONTROL Revalidate on server]** under Adaptive Form Container in the sidebar to enable or disable server-side validation for the current form.

![Enabling Server-Side Validation](assets/revalidate-on-server.png)

Enabling Server-Side Validation

If end-user bypass those validations and submit the forms, the server again performs the validation. If the validation fails at server end, then the submit transaction is stopped. The user is presented with the original form again. The captured data and submitted data are presented to the user as an error.

>[!NOTE]
>
>Server-side validation validates the form model. You are recommended to create a separate client library for validations and not mix it with other things like HTML styling and DOM manipulation in the same client library.
-->

## 제출 액션의 오류 처리 {#error-handling-on-submit-action}

AEM 보안 및 강화 지침의 일부로, 400.jsp, 404.jsp 및 500.jsp와 같은 사용자 정의 오류 페이지를 구성합니다. 이러한 핸들러는 양식 제출 시 400, 404 또는 500 오류가 나타나면 호출됩니다. 게시 노드에서 이러한 오류 코드가 트리거되면 핸들러가 호출되기도 합니다. 또한 다른 HTTP 오류 코드에 대한 JSP 페이지를 만들 수 있습니다.

양식 데이터 모델(FDM) 또는 스키마 기반 적응형 양식에 데이터가 포함되지 않은 스키마에 대한 XML 또는 JSON 데이터 컴플레인을 미리 채우는 경우 `<afData>`, `<afBoundData>`, 및 `</afUnboundData>` 태그를 지정하면 적응형 양식의 제한되지 않은 필드 데이터가 손실됩니다. 스키마는 XML 스키마, JSON 스키마 또는 양식 데이터 모델(FDM)일 수 있습니다. 무제한 필드는 `bindref` 속성이 없는 적응형 양식 필드입니다.

<!-- For more information, see [Customizing Pages shown by the Error Handler](/help/sites-developing/customizing-errorhandler-pages.md). -->


<!--
## See next

* [Create style or themes for your forms](using-themes-in-core-components.md)
* [Create an Adaptive Form (core components)](/help/forms/creating-adaptive-form-core-components.md)
* [Create a custom Submit Action for Adaptive Forms](/help/forms/custom-submit-action-form.md)

-->

## 추가 참조 {#see-also}

{{see-also}}

