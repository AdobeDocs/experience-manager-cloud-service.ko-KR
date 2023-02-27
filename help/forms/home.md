---
title: ' [!DNL AEM Forms] as a Cloud Service 소개'
description: AEM Forms를 살펴보고 업무용 문서 및 양식 콘텐츠를 제작하는 데 어떻게 도움이 되는지 알아봅니다. PaaS(Platform-as-a-Service)에 대해 자세히 알아보고 엔터프라이즈급 디지털 양식 및 비즈니스 프로세스를 관리하는 방법을 포함하여 Forms를 현재 데이터 소스에 연결하는 방법도 알아봅니다.
landing-page-description: AEM as a Cloud Service에서 양식을 사용하는 방법을 이해합니다.
exl-id: aa5ef10c-ba78-4a9d-8b2b-a72a7a306888
source-git-commit: 37274b28ab2343fd3cdfb4747c9dee701c699b46
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 31%

---

# 소개 {#introduction}

Adobe [!DNL Experience Manager Forms as a Cloud Service] 는 제출된 데이터를 백엔드 프로세스, 비즈니스 규칙 및 외부 데이터 저장소에 통합하는 동시에 복잡한 디지털 양식을 작성, 관리, 게시 및 업데이트하는 클라우드 기반의 PaaS(Platform as a Service) 솔루션을 제공합니다. 이 서비스는 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습합니다.

이 서비스를 사용하여 대화형의 매력적인 디지털 양식을 제작하고 배포할 수 있습니다. 예를 들어, 고객 등록 여정을 디지털화하고자 하는 조직을 생각해 보십시오. 이 조직은 기존 고객 데이터가 포함된 여러 데이터 소스를 보유하고 있습니다. 양식을 미리 채우고, 양식에 전자 서명을 추가하고, 채워진 양식을 PDF 파일로 보관하고자 합니다. 또한 조직에는 여러 인쇄 양식(PDF 양식)이 있으며 모든 인쇄 양식을 디지털 양식으로 변환하고자 합니다.



이 조직은 [!DNL AEM Forms] as a Cloud Service를 사용하여 디지털 양식을 만들고, 양식을 기존 데이터 소스에 연결하고, [!DNL Adobe Sign]과 양식을 통합하여 양식에 전자 서명을 추가하고, DoR(문서 기록)을 생성하여 제출된 양식을 PDF 파일로 보관할 수 있습니다. 서비스를 사용하여 기존 PDF 양식을 디지털 양식으로 변환할 수도 있습니다.

조직은 [!DNL AEM Forms] as a Cloud Service를 사용하여 로컬 인프라 없이도 클라우드에서 이러한 모든 기능을 사용할 수 있습니다. 또한 이 서비스는 항상 최신 기능을 유지하므로 조직은 복잡한 업그레이드 주기를 겪을 필요가 없습니다.

## 주요 기능 {#key-features}

|  |  |
|---|---|
| 적응형 양식 | 웹 사이트, 앱, 기타 디지털 및 인쇄 채널을 위한 대화형, 동적, 응답형, 모바일 친화적, 데이터 기반의 양식을 작성하고 관리합니다. 등록 경험을 시작, 이해 및 구현하려면 다음 사항을 검토하십시오. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html"> 적응형 양식 만들기 </a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/themes.html">적응형 양식 스타일 지정</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#enabling-server-side-validation-br"> 데이터 저장소 또는 워크플로우에 데이터 제출</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html"> 장기 보관을 위해 양식의 레코드를 만듭니다</a></li></ul> |
| 통신 API | RESTful API를 온디맨드 또는 월별 명세서 및 계정 알림과 같은 일정 간격으로 개인화된 데이터 기반 커뮤니케이션의 작성, 관리 및 전달을 자동화합니다. 시작하기, 이해 및 만들려면 다음을 검토하십시오. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#document-generation"> 개인화된 커뮤니티 생성 </a> </li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#document-manipulation"> PDF 문서 조합 또는 분해 </a> </li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#convert-to-and-validate-pdf%2Fa-compliant-documents">PDF/A 호환 문서 만들기 </a></li></ul> |
| automated forms conversion 서비스 | 레거시 PDF 기반 양식을 온라인으로 쉽게 관리하고 배포할 수 있는 적응형 Forms으로 변환합니다. 시작하려면 다음을 검토하십시오. <ul><li><a href="https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html">automated forms conversion 서비스 구성</a></li><li><a href="https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html">PDF 양식을 적응형 양식으로 전환</a></li></ul> |
| Forms Workflow | 양식 및 문서 서비스와 관련된 비즈니스 프로세스를 자동화합니다. 다양한 업무 프로세스 단계를 거쳐서 양식 및 문서를 할당, 경로 지정, 검토 및 승인합니다. 시작하려면 다음을 검토하십시오.  <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-reviews-forms.html">검토할 양식 또는 문서 보내기</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#assign-task-step">승인 거부 워크플로우 생성</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#generate-document-of-record-step">레코드 문서 추가 </a> 또는 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#sign-document-step"> eSign </a> 비즈니스 워크플로우 단계</a></li></ul> |
| 전자 서명 | Adobe Sign 및 DocuSign과 통합하여 Forms 및 문서를 사용자에게 손쉽게 전자 서명을 전송할 수 있습니다. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html">Adobe Sign을 사용하여 적응형 양식에 전자 서명 </a></li><li></a> <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-docusign-adaptive-forms.html">DocuSign을 사용하여 적응형 양식 전자 서명 </a></li></ul> |
| Forms Analytics | Adobe Analytics을 사용하여 사용자 행동 및 환경 설정에 대한 중요한 통찰력을 얻을 수 있습니다. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-aem-forms-with-adobe-analytics.html?lang=en">Adobe Analytics으로 적응형 양식 연결</a></li></ul> |
| 데이터 소스 | 양식 및 문서를 외부 데이터 소스와 쉽게 연결하여 데이터를 검색하고 전송할 수 있습니다. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-data-sources.html?lang=en">RDBMS 또는 Rest 끝점에 연결</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics-salesforce.html?lang=en">Microsoft Dynamics 365 또는 Salesforce 클라우드 서비스에 연결</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html?lang=en">Microsoft Azure Blob 저장 공간에 연결</a></li></ul> |


<!-- 
>[!BEGINTABS]

>[!TAB Adaptive Forms]

Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>

>[!TAB Automated Forms Conversion Service]

Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>

>[!TAB Communications API (Document Services)]

Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.

>[!TAB Advanced Analytics]

The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>


>[!ENDTABS] 

| Adaptive Forms | Communications APIs  | Automated Forms Conversion Service | Forms Workflows | E-Sign | Forms Analytics | Data Model | 
|---|---|---|---|---|---| ---|
|Create and manage interactive, dynamic, responsive, mobile-friendly, and data-driven forms for your websites, apps, and other digital and Print channels. | Automate creation, management, and delivery of personalized, data-driven communications with RESTful APIs (Application Programming Interfaces) on-demand or at scheduled intervals. | Convert legacy PDF-based forms into Adaptive Forms that can be easily managed and distributed online. | Automate business processes involving forms and document services. Assign, route, review, and approve forms and document as these move through different stages of a business process.| Integrate with Adobe Sign and DocuSign to easliy send send Forms and documents to users for e-signatures. | Use Adobe Analytics to gain valuable insights into user behavior and preferences. | Easily connect your forms and documents with external data sources to retieve and send data. |
|<ul><li>Create an Adaptive Form</li><li>Style an Adaptive Form</li><li>Submit data to a data store or a workflow</li></ul>|<ul><li>Generate personalized communciations</li><li>Assemble or disassemble PDF documents</li><li>Create PDF/A-compliant documents</li></ul>|<ul><li>Configure Automated Forms Conversion Service</li><li>Convert PDF forms to adaptive forms</li></ul>|<ul><li>Send a form or document for review</li><li>Create an approval rejection Workflow</li><li>Add Document of Record or e-signatures to a business workflow</li></ul>|<ul><li>E-sign an Adaptive Form with Adobe Sign</li><li>E-sign an Adaptive Form with DocuSign</li></ul>|<ul><li>Connect an Adaptive Form with Adobe Analytics</li></ul>|<ul><li>Connect to a RDBMS or Rest endpoint</li><li>Connect to Microsoft Dynamics 365 or Salesforce cloud service</li><li>Connect to Microsoft&reg; Azure Blob Storage</li></ul>|

<!--
| | |
|---|---|
| Adaptive Forms | Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>|
| Automated Forms Conversion Service | Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>|
| Communications API (Document Services) | Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.|
|Advanced Analytics| The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>|

-->

## 최신 혁신 내용 {#latest-innovations}

>[!BEGINTABS]

>[!TAB 헤드리스 적응형 Forms]

|| |—|—| |![](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/assets/how-headless-adaprive-forms-work.png?)| 만들기 및 관리 [헤드리스 적응형 Forms](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) Adobe Experience Manager 플랫폼 내에서 사용할 수 있습니다. 개발자는 기존의 그래픽 사용자 인터페이스를 통해서가 아니라 API를 통해 액세스 및 상호 작용할 수 있는 대화형 양식을 작성, 게시 및 관리할 수 있습니다. <br/> <br/> 이러한 양식은 기존 HTML 양식 인터페이스 없이도 제출할 수 있도록 설계되었습니다. 즉, 프런트 엔드에 표시되는 양식 요소를 필요로 하지 않고 API 또는 백엔드 코드를 통해 양식 데이터를 프로그래밍 방식으로 제출할 수 있습니다. <br/> <br/> 헤드리스 양식은 단일 페이지 애플리케이션, 점진적 웹 앱 또는 모바일 애플리케이션을 작성할 때와 같이 기존 HTML 양식 인터페이스가 필요하지 않거나 실용적이지 않을 수 있는 다양한 시나리오에서 유용합니다. 개발자가 API 또는 백엔드 코드를 통해 직접 양식 데이터를 제출할 수 있도록 함으로써, 헤드리스 양식을 통해 워크플로우를 간소화하고 웹 애플리케이션의 전반적인 성능을 향상시킬 수 있습니다.|




>[!TAB 코어 구성 요소]

|||
|--|--|
|![](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/assets/sample-core-components-based-adaptive-form.png?) | 적응형 양식 핵심 구성 요소는 Adobe Experience Manager WCM 핵심 구성 요소를 기반으로 구축된 24개의 오픈 소스 BEM 호환 구성 요소 세트입니다. [](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) 사용자의 디바이스, 브라우저 및 화면 크기에 맞춰 조정되는 양식인 적응형 양식을 만드는 데 사용하도록 특별히 설계되었습니다. <br/> <br/> 이러한 구성 요소를 사용하면 텍스트 필드, 확인란, 드롭다운 메뉴 등을 포함한 다양한 양식 필드 옵션을 제공하여 탁월한 데이터 캡처 및 등록 경험을 만들 수 있습니다. 또한 여기에는 사용자 친화적이고 사용하기 쉬운 양식을 만드는 데 사용할 수 있는 유효성 검사, 조건부 논리 및 반응형 디자인과 같은 기능이 포함되어 있습니다. <br/> <br/>  이와 더불어 이러한 구성 요소는 오픈 소스이므로 개발자가 조직의 특정 요구 사항에 맞게 구성 요소를 쉽게 사용자 정의하고 확장할 수 있습니다. 그리고 이러한 구성 요소는 BEM 방법론을 기반으로 구축되어 있으므로 확장 및 유지 관리가 가능합니다.|



>[!TAB Microsoft PowerAutomate &#x200B; 커넥터]

|| |—|—| |![](https://powerusers.microsoft.com/t5/image/serverpage/image-id/182924i17C4BEA1C045D731/image-size/large/is-moderation-mode/true?v=1.0&amp;px=999)| AEM Forms Power Automate Connector를 사용하면 Adobe Experience Manager(AEM) Forms을 Microsoft Power Automate(이전에 Microsoft Flow)와 통합할 수 있습니다. Power Automate 는 클라우드 기반 서비스로, 다양한 애플리케이션과 서비스 간에 자동화된 워크플로우를 만들 수 있습니다.  <br/> <br/> AEM Form Power 자동 커넥터를 사용하면 적응형 양식 제출을 기반으로 자동으로 트리거되는 워크플로우를 만들 수 있습니다. 예를 들어, 사용자가 양식을 제출하거나 사용자가 양식을 완료할 때 Microsoft Planner에서 작업을 만들 때 특정 사용자에게 전자 메일 알림을 자동으로 보내는 워크플로우를 만들 수 있습니다.  <br/> <br/> AEM Forms Power Automate Connector는 Microsoft Power Automate와 연결된 다른 애플리케이션 및 서비스와 Adaptive Forms을 자동화하고 통합할 수 있는 강력한 도구로서, 더 다양한 도구를 사용하여 작업할 수 있습니다. 사용자 지정 작업, 조건 및 트리거를 추가하는 기능을 사용하여 특정 요구에 맞는 워크플로우를 만들 수 있습니다. 또한 Power Automate는 세부 분석 및 보고를 제공하여 시간에 따라 워크플로우를 모니터링하고 최적화할 수 있습니다.|


>[!TAB Microsoft Storage Connectors: OneDrive 및 Sharepoint]

|| |—|—| |![](/help/forms/assets/onedrive-and-sharepoint.jpg)|OneDrive 및 SharePoint용 AEM Forms Microsoft Storage Connectors는 Adobe Experience Manager(AEM) Forms을 Microsoft OneDrive 및 SharePoint과 통합할 수 있는 커넥터입니다. 이 커넥터를 사용하여 적응형 Forms에서 직접 OneDrive 및 SharePoint에 데이터 파일과 첨부 파일을 업로드할 수 있습니다. |


>[!ENDTABS]

<!--

| | |
|---|---|
| Adaptive Forms | Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>|
| Automated Forms Conversion Service | Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>|
| Communications API (Document Services) | Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.|
|Advanced Analytics| The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>|

Adaptive Forms enable organizations to quickly design and deploy responsive, mobile-friendly forms without the need for extensive coding or development. With Adaptive Forms, businesses can create complex, multi-step forms with conditional logic, validations, and integrations with back-end systems such as CRMs and databases.

Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development.

In addition, AEM Adaptive Forms offer several other features, including:

Advanced workflows for routing, approval, and submission of form data
Real-time validation and error checking to ensure data accuracy
Integration with third-party data sources and APIs for pre-filling form fields or validating data
Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics
Overall, AEM Adaptive Forms provide businesses with a powerful tool for creating and managing complex, interactive forms that can be easily integrated into their digital experiences. |




| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native architecture | &#x2611;  | &#x2612; |
| Auto-scaling based on load | &#x2611;  | &#x2612; |
| Zero downtime for upgrades | &#x2611;  | &#x2612; |
| Feature roll-out frequency | Agile*  | Quarterly |
| CDN (content delivery network) included | &#x2611;  | &#x2612; | 
| Topologies optimized for maximum resilience and efficiency| &#x2611;  | &#x2612; | 
| Cloud-native development environment | &#x2611;  | &#x2612; | 
| Self-Service via Cloud Manager | &#x2611;  | &#x2612; | 
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD) | &#x2611;  | &#x2612; | 
| Adaptive Forms | &#x2611; | &#x2611; | 
| Data Integration with multiple data sources| &#x2611; | &#x2611; | 
| Communications APIs (Document Services) | &#x2611;* | &#x2611; | 
| Automated Forms Conversion Service | &#x2611; | &#x2611; | 
| Integration with [!DNL Micosoft Power Automate] | &#x2611; | &#x2612; | 
| Integration with [!DNL Adobe Sign] | &#x2611; | &#x2611; | 
| Integration with [!DNL AEM Sites] | &#x2611; | &#x2611; | 
| Integration with [!DNL Adobe Launch] | &#x2611; | &#x2611; | 
| Integration with [!DNL Adobe Analytics] | &#x2611; | &#x2611; | 
| Easy connectivity with Microsoft Dynamics and Salesforce | &#x2611; | &#x2612; |
| Custom submit action for with [!DNL DocuSign] | &#x2611; | &#x2612; | 
| Microsoft Azure data store connector | &#x2611; | &#x2612; |
| Hardened Rule editor | &#x2611; | &#x2612; | 
| Forms Portal | &#x2611; | &#x2611; | 
| AEM Workflows | &#x2611; | &#x2611; | 
| Document of Record | &#x2611; | &#x2611; | 
| Adaptive Forms Wizard | &#x2611; | &#x2612; | 
| Custom XCI for Document of Record| &#x2611; | &#x2612; |
| Invisible Captcha | &#x2611; | &#x2611; |
| Reusable Form Data Model configurations | &#x2611; | &#x2611; |
| Acroform-based Document of Record | &#x2611; | &#x2611; | 
| Government ID based identity authentication for Adobe Sign enabled Adaptive Forms | &#x2611; | &#x2611; | 
| Document Security | &#x2612; | &#x2611; |


* [Notable changes in comparison to AEM 6.5 Forms](notable-changes.md)
* [Frequently asked questions](faq.md)

-->