---
title: ' [!DNL AEM Forms] as a Cloud Service 소개'
description: AEM Forms를 살펴보고 업무용 문서 및 양식 콘텐츠를 제작하는 데 어떻게 도움이 되는지 알아봅니다. PaaS(Platform-as-a-Service)에 대해 자세히 알아보고 엔터프라이즈급 디지털 양식 및 비즈니스 프로세스를 관리하는 방법을 포함하여 Forms를 현재 데이터 소스에 연결하는 방법도 알아봅니다.
landing-page-description: AEM as a Cloud Service에서 양식을 사용하는 방법을 이해합니다.
exl-id: aa5ef10c-ba78-4a9d-8b2b-a72a7a306888
source-git-commit: 95e1981faf9532aa56cc8a2e18166d08f35ecf29
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 29%

---

# 소개 {#introduction}

Adobe [!DNL Experience Manager Forms as a Cloud Service] 는 제출된 데이터를 백엔드 프로세스, 비즈니스 규칙 및 외부 데이터 저장소에 통합하는 동시에 복잡한 디지털 양식을 작성, 관리, 게시 및 업데이트하는 클라우드 기반의 PaaS(Platform as a Service) 솔루션을 제공합니다. 이 서비스는 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습합니다.

이 서비스를 사용하여 대화형의 매력적인 디지털 양식을 제작하고 배포할 수 있습니다. 예를 들어, 고객 등록 여정을 디지털화하고자 하는 조직을 생각해 보십시오. 이 조직은 기존 고객 데이터가 포함된 여러 데이터 소스를 보유하고 있습니다. 양식을 미리 채우고, 양식에 전자 서명을 추가하고, 채워진 양식을 PDF 파일로 보관하고자 합니다. 또한 조직에는 여러 인쇄 양식(PDF 양식)이 있으며 모든 인쇄 양식을 디지털 양식으로 변환하고자 합니다.

이 조직은 [!DNL AEM Forms] as a Cloud Service를 사용하여 디지털 양식을 만들고, 양식을 기존 데이터 소스에 연결하고, [!DNL Adobe Sign]과 양식을 통합하여 양식에 전자 서명을 추가하고, DoR(문서 기록)을 생성하여 제출된 양식을 PDF 파일로 보관할 수 있습니다. 서비스를 사용하여 기존 PDF 양식을 디지털 양식으로 변환할 수도 있습니다.

조직은 [!DNL AEM Forms] as a Cloud Service를 사용하여 로컬 인프라 없이도 클라우드에서 이러한 모든 기능을 사용할 수 있습니다. 또한 이 서비스는 항상 최신 기능을 유지하므로 조직은 복잡한 업그레이드 주기를 겪을 필요가 없습니다.

## 주요 기능 {#key-features}

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


>[!ENDTABS] -->


| 적응형 양식 | automated forms conversion 서비스 | 통신 API | 통합 | Forms Workflow |
|---|---|---|---|---|
| 적응형 Forms을 통해 기업은 웹 사이트 및 기타 디지털 채널에 응답하고 모바일에 친숙한 양식을 위한 대화형 데이터 기반의 양식을 만들고 관리할 수 있습니다. | automated forms conversion 서비스를 통해 기업은 기존의 PDF 기반 양식을 대화형 디지털 양식으로 전환하여 온라인으로 쉽게 관리 및 배포할 수 있습니다. | Communications API는 기업이 개인화된 데이터 기반 통신의 작성, 관리 및 전달을 자동화할 수 있는 RESTful API(Application Programming Interface) 세트입니다. | 플랫폼은 Adobe Sign 및 DocuSign과 통합할 수 있으므로 사용자가 적응형 양식에서 직접 디지털 서명 요청을 전송하고 추적할 수 있습니다. </br></br>또한 플랫폼을 Adobe Analytics과 통합하여 조직에서 사용자 행동 및 환경 설정에 대한 중요한 통찰력을 얻을 수 있습니다. </br></br> 마지막으로 AEM Forms Cloud Service을 사용하면 적응형 양식을 AEM Sites 페이지에 직접 포함할 수 있으므로 원활한 사용자 경험을 만들 수 있습니다 | AEM(Adobe Experience Manager) Forms의 Forms 중심 워크플로우는 양식과 관련된 비즈니스 프로세스를 자동화할 수 있도록 설계되었습니다. 이러한 워크플로우는 비즈니스 프로세스의 여러 단계를 거쳐서 양식의 라우팅, 검토 및 승인을 자동화합니다. Forms 중심의 워크플로우는 AEM Forms 워크플로우 디자이너를 사용하여 시각적으로 만들 수 있으며 AEM Forms과 통합하여 양식을 제출할 때 워크플로우를 트리거할 수 있습니다. 워크플로우는 특정 기준에 따라 다양한 사용자 또는 그룹으로 양식을 라우팅하도록 구성할 수 있으며, 자동 알림 및 미리 알림을 포함하여 양식이 적시에 처리되도록 할 수 있습니다. AEM Forms의 양식 중심의 전반적인 워크플로우는 조직의 비즈니스 프로세스를 간소화하고 효율성을 높이며 오류를 줄일 수 있도록 해줍니다. |


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

[헤드리스 적응형 Forms](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) 은 Adobe Experience Manager 플랫폼 내에서 헤드리스 웹 양식을 만들고 관리하는 솔루션입니다. 이 기능을 사용하면 기존 그래픽 사용자 인터페이스를 통해서가 아니라 API를 통해 액세스 및 상호 작용할 수 있는 대화형 양식을 작성, 게시 및 관리할 수 있습니다. AEM Headless Adaptive Forms을 사용하면 양식 개발 및 배포에서 유연성과 확장성을 향상시킬 수 있을 뿐만 아니라, 특정 요구에 맞게 양식 디자인 및 기능을 조정할 수 있는 기능을 통해 사용자 경험을 향상시킬 수 있습니다. 이 솔루션은 AEM 및 헤드리스 기술의 기능을 활용하여 다양한 사용 사례 및 애플리케이션을 위한 웹 양식을 작성, 관리 및 배포할 수 있는 강력한 플랫폼을 제공합니다.


>[!TAB 코어 구성 요소]

다음 [응용 Forms 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) 는 Adobe Experience Manager WCM 코어 구성 요소의 기초 위에 구축된 24개의 오픈 소스 BEM 준수 구성 요소 세트입니다. 사용자의 디바이스, 브라우저 및 화면 크기에 맞춰 조정되는 양식인 적응형 양식을 만드는 데 사용하도록 특별히 설계되었습니다.

이러한 구성 요소를 사용하면 텍스트 필드, 확인란, 드롭다운 메뉴 등을 포함한 다양한 양식 필드 옵션을 제공하여 탁월한 데이터 캡처 및 등록 경험을 만들 수 있습니다. 또한 여기에는 사용자 친화적이고 사용하기 쉬운 양식을 만드는 데 사용할 수 있는 유효성 검사, 조건부 논리 및 반응형 디자인과 같은 기능이 포함되어 있습니다.

이와 더불어 이러한 구성 요소는 오픈 소스이므로 개발자가 조직의 특정 요구 사항에 맞게 구성 요소를 쉽게 사용자 정의하고 확장할 수 있습니다. 그리고 이러한 구성 요소는 BEM 방법론을 기반으로 구축되어 있으므로 확장 및 유지 관리가 가능합니다.


>[!TAB Microsoft PowerAutomate &#x200B; 커넥터]

Microsoft Power Automate Connector for AEM Forms은 AEM(Adobe Experience Manager) Forms을 Microsoft Power Automate(이전에 Microsoft Flow)와 통합할 수 있는 커넥터입니다. Power Automate 는 클라우드 기반 서비스로, 다양한 애플리케이션과 서비스 간에 자동화된 워크플로우를 만들 수 있습니다.

Power Automate Connector for AEM Form을 사용하면 적응형 양식 제출을 기반으로 자동으로 트리거되는 워크플로우를 만들 수 있습니다. 예를 들어, 사용자가 양식을 제출하거나 사용자가 양식을 완료할 때 Microsoft Planner에서 작업을 만들 때 특정 사용자에게 전자 메일 알림을 자동으로 보내는 워크플로우를 만들 수 있습니다.

AEM Forms용 Power Automate Connector를 사용하면 다음과 같은 많은 이점이 있습니다.

* **자동화**: 일상적인 작업을 자동화하고 프로세스를 간소화하여 시간을 절약하고 오류를 줄일 수 있습니다.

* **통합**: 커넥터를 사용하면 Adobe Experience Manager Forms을 다른 애플리케이션 및 서비스와 통합하여 다양한 도구를 사용하여 작업할 수 있습니다.

* **사용자 지정**: 사용자 지정 작업, 조건 및 트리거를 추가하는 기능을 사용하여 특정 요구에 맞는 워크플로우를 만들 수 있습니다.

* **Analytics**: Power Automate는 상세 분석 및 보고를 제공하여 시간에 따라 워크플로우를 모니터링하고 최적화할 수 있습니다.

전반적으로 AEM Forms용 Power Automate Connector는 AEM Forms을 다른 애플리케이션 및 서비스와 자동화 및 통합하여 효율성 및 생산성을 향상시킬 수 있는 강력한 도구입니다.

>[!TAB Microsoft Storage Connectors: OneDrive 및 Sharepoint]

OneDrive 및 SharePoint용 AEM Forms Microsoft Storage Connectors 는 AEM(Adobe Experience Manager) Forms을 Microsoft OneDrive 및 SharePoint과 통합할 수 있는 커넥터입니다. 이러한 커넥터를 사용하면 Microsoft의 클라우드 기반 스토리지 솔루션 내에 AEM Forms 데이터 및 문서를 저장하고 관리할 수 있습니다.

이러한 커넥터를 사용하면 Microsoft OneDrive 내에 AEM Forms 데이터 및 문서를 저장하고 관리할 수 있습니다. 이 커넥터를 사용하여 AEM Forms에서 직접 OneDrive 및 SharePoint에 데이터 파일과 첨부 파일을 업로드할 수 있습니다.

OneDrive 및 SharePoint용 AEM Forms Microsoft Storage Connectors를 사용하면 다음과 같은 몇 가지 이점이 있습니다.

* **통합**: 이러한 커넥터를 사용하면 AEM Forms을 Microsoft의 클라우드 기반 스토리지 솔루션과 통합하여 이러한 플랫폼의 기능을 활용할 수 있습니다.

* **공동 작업**: OneDrive와 SharePoint은 팀 구성원이 파일과 문서에서 함께 작업할 수 있도록 하는 공동 작업 플랫폼입니다. 이러한 플랫폼과 AEM Forms을 통합함으로써 공동 작업 및 팀워크를 향상시킬 수 있습니다.

* **보안**: OneDrive 및 SharePoint은 강력한 보안 기능을 제공하여 데이터와 문서를 안전하게 저장하고 액세스할 수 있도록 합니다.

전반적으로 OneDrive 및 SharePoint용 AEM Forms Microsoft Storage Connectors는 Microsoft의 클라우드 기반 스토리지 솔루션 내에서 AEM Forms 데이터 및 문서를 저장 및 관리하고 공동 작업 및 보안을 향상시킬 수 있는 강력한 도구입니다.

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