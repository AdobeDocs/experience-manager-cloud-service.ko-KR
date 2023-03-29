---
title: AEM 6.5 Forms과 AEM 클라우드 서비스의 차이점
description: Experience Manager Forms 사용자로서 Adobe Experience Manager Forms as a Cloud Service으로 업그레이드하려고 합니까? AEM 6.5 Forms 및 AEM 클라우드 서비스를 비교하고 Cloud Service으로 업그레이드하거나 마이그레이션하기 전에 가장 눈에 띄는 변경 사항을 알아봅니다.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: dea6c266e5c10135a320f923dc77d0fd2050988e
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 2%

---

# 기존 Adobe Experience Manager 6.5 Forms 사용자의 주요 변경 사항  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms은 Adobe Experience Manager Forms 온-프레미스 및 as a Cloud Service과 비교하여 기존 기능에 몇 가지 주목할 만한 변경 사항을 제공합니다 [!DNL Adobe-Managed Service] 환경. 주요 차이점은 아래에 나와 있습니다.

<!-- 
<table>
    <thead>
        <tr>
            <th>AEM Forms Components</th>
            <th>Feature/Capability</th>
            <th>[!DNL AEM Forms] as a Cloud Service</th>
            <th>AEM 6.5 Forms on-premise </th>
            <th>AEM 6.5 Forms Adobe Managed Services </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="6">Cloud native features</td>
            <td>Cloud-native architecture</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Auto-scaling based on load</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Zero downtime for upgrades</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Feature roll-out frequency</td>
            <td>Monthly</td>
            <td>Quarterly</td>
            <td>Quarterly</td>
        </tr>
        <tr>
            <td>CDN (content delivery network) included</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Topologies optimized for maximum resilience and efficiency</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td rowspan="3">Developer environment <sup>6</sup></td>
            <td>Self-Service via Cloud Manager</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Cloud-native development environment</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        <tr>
            <td>Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD)</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td rowspan="8">Third-party and Adobe integrations</td>
            <td>[!DNL Micosoft Power Automate] for business process automation</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL Microsoft Dynamics] and [!DNL Salesforce] for Customer Relationship Management (CRM)</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Integration with [!DNL Microsoft Azure] for data storage</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL DocuSign] for e-signatures</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[!DNL Adobe Sign] for e-signatures</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>[Adobe Launch] to track usage and performance</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>[!DNL Adobe Analytics] to track usage and performance</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Google reCaptcha for adaptive challenges</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="11">Adaptive Forms</td>
            <td>Automated Forms Conversion Service<sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Core Components</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Foundation Components</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Form creation wizard</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Rule Editor<sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Prefill Service <sup>1</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Auto-save an adaptive form</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>XSD-Based adaptive forms <sup>1</sup></td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>In-form signing experience for adaptive forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Submit an adaptive form to AEM Forms on JEE Workflows (Process Management)</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Summary, Verify, and Scribble Signature components for adaptive forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="4">Forms Portal</td>
            <td>Drafts and Submission component <sup>2<sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Search & Lister component</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Link component</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>List forms for non-logged in users <sup>2</sup></td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="13">Data integration (Form Data Model) </td>
            <td>OData services</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Microsoft Dynamics</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>SalesForce</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>Microsoft Azure Blob Storage</td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>RESTful web services - Open API version 3.0 <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>---</td>
            <td>---</td>
        </tr>
        <tr>
            <td>RESTful web services - Open API version 2.0 <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>SOAP-based web services <sup>4</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Microsoft SQL Server</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>MySQL</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>IBM DB2</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
                <tr>
            <td>Oracle RDBMS</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>AEM user profile</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Sybase</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="8">Communication APIs (Document Services)</td>
            <td>Document Generation (Output Service) <sup>3</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Document Manipulation (Assembler Service) <sup>3</sup></td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Signature Service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Encryption service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Reader Extension service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Send to printer service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Convert PDF service</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Barcoded Forms service </td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Document Security</td>
            <td>Document Security Extension for Microsoft Office (Digital Rights Management)</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td rowspan="2">HTML5 Forms <sup>5</sup></td>
            <td>HTML5 Forms</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Forms Workspace</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
        <tr>
            <td>Interactive Communications</td>
            <td>Interactive Communications</td>
            <td>---</td>
            <td>&#x2705;</td>
            <td>&#x2705;</td>
        </tr>
    </tbody>
</table>


<!-- 

## Cloud native features 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native architecture | &#x2705;  | --- |
| Auto-scaling based on load | &#x2705;  | --- |
| Zero downtime for upgrades | &#x2705;  | --- |
| Feature roll-out frequency | Agile*  | Quarterly |
| CDN (content delivery network) included | &#x2705;  | --- | 
| Topologies optimized for maximum resilience and efficiency| &#x2705;  | --- | 

## Integrations 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Integration with [!DNL Micosoft Power Automate] | &#x2705; | --- | 
| Integration with [!DNL DocuSign] | &#x2705; | --- | 
| Integration with [!DNL Microsoft Dynamics] and [!DNL Salesforce] | &#x2705; | --- |  
| Integration with Microsoft Azure data stores | &#x2705; | --- | 
| Integration with [!DNL Adobe Sign] | &#x2705; | &#x2705; | 
| Integration with [!DNL AEM Sites] | &#x2705;| &#x2705; | 
| Integration with [!DNL Adobe Launch] | &#x2705; | &#x2705; | 
| Integration with [!DNL Adobe Analytics] | &#x2705; | &#x2705; |
| Data integration (Form Data Model) | &#x2705; | &#x2705; |
 
## Adaptive forms <sup> 1 </sup>

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Automated Forms Conversion Service  | &#x2705; | &#x2705; |
| Forms Portal Submissions | &#x2705; | &#x2705; | 
| Google Captcha integrations | &#x2705; | &#x2705; |
| Repeatable sections in an adaptive form | &#x2705;| &#x2705; |
| Form fragments | &#x2705; | --- |
| Hardened rule editor | &#x2705; | --- | 
| Form creation wizard | &#x2705; | --- |
| Auto-save an adaptive form | --- | &#x2705; |
| Scribble Signatures | --- | &#x2705; |
| XSD-Based adaptive forms | --- | &#x2705; |
| Using Adobe Sign to add signatures within an Adaptive Form | --- | &#x2705; |
|Submit to AEM Forms on JEE Workflows (Process Management)| --- | &#x2705; | 

## Communication APIs (Document Services <sup> 2 </sup>) and Document Security 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Document Generation (Output Service)| &#x2705; | &#x2705; |
| Document Manipulation (Assembler Service) | &#x2705; | &#x2705; |
| Signature service | --- | &#x2705; |
| Encryption service | --- | &#x2705; |
| Reader Extension service | --- | &#x2705; |
| Send to printer service | --- | &#x2705; |
| Convert PDF service | --- | &#x2705; |
| Barcoded Forms service | --- | &#x2705; |
| Document Security Extension for Microsoft Office (Digital Rights Management) | --- | &#x2705; | 

## Data integration (Form Data Model) <sup> 3 </sup>

| Data Sources | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| OData services | &#x2705; (Version 4.0)|  --- | 
| Microsoft Dynamics| &#x2705;  | --- | 
| SalesForce|  &#x2705; | ---| 
| Microsoft Azure Blob Storage| &#x2705;  | --- | 
| RESTful web services Open API version 3.0| &#x2705; | --- |
| RESTful web services Open API version 2.0| &#x2705; | &#x2705; |
| SOAP-based web services| &#x2705;| &#x2705; |   
| MySQL| &#x2705; | &#x2705; | 
| Microsoft SQL Server| &#x2705; | &#x2705; | 
| IBM DB2| &#x2705; | &#x2705; | 
| Oracle RDBMS| &#x2705; | &#x2705; | 
| Sybase|  ---  | &#x2705; | 
| AEM user profile| --- | &#x2705; | 

## Form-centric workflows

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
|Submit to AEM Forms on JEE Workflows (Process Management)| --- | &#x2705; | 

## HTML5 Forms<sup> 4 </sup> and Interactive Communications 

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| HTML5 Forms | --- | &#x2705; | 
| HTML5 Workspace| --- | &#x2705; | 
| Interactive Communications | --- | &#x2705; | 

## Developer environment <sup> 5 </sup>

| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native development environment | &#x2705;  | --- | 
| Self-Service via Cloud Manager | &#x2705;  | --- | 
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD) | &#x2705;  | --- | 


-->

## 클라우드 기본 기능

* 이 서비스에는 로드, 업그레이드에 대한 다운타임 없이 자동 확장, 새로운 기능과 업데이트를 자주/롤아웃한 후 자주 자동 확장, 복원 및 효율성을 극대화하도록 최적화된 토폴로지를 사용하는 클라우드 기반의 아키텍처가 있습니다.

* 이 서비스는 데이터 외부화 기능을 제공하며(모든 유형의 처리를 위해 서버에 데이터가 유지되지 않음) 데이터를 Adobe Experience Manager Cloud Service 인스턴스에 저장하는 제출 작업이 포함되어 있지 않아 보안이 강화됩니다. 양식을 통해 캡처된 데이터는 구성된 데이터 저장소로 직접 전송됩니다.

* 무료 CDN(콘텐츠 전달 네트워크)도 양식을 신속하게 제공하고 렌더링할 수 있도록 포함되어 있습니다.


## 개발 흐름 업데이트

* 이 서비스는 Cloud Service에 코드를 배포하기 전에 로컬 환경(로컬 컴퓨터)에서 사용자 지정 코드를 개발하고 테스트하는 SDK를 제공합니다. 개발자는 로컬 시스템에서 SDK를 사용하여 사용자 지정 구성 요소, 테마, 워크플로우 애플리케이션, 구성, 템플릿 등을 개발하고 테스트합니다. 로컬 개발 환경에서 사용자 지정 코드를 테스트한 후 사용자 지정 코드를 [Forms CS 환경 개발 또는 스테이지 환경](/help/implementing/cloud-manager/deploy-code.md) 을 프로덕션 환경으로 승격하기 전에 추가 테스트를 수행하십시오.

* 개발자는 공통된 방식으로 Cloud Service 및 로컬 개발 환경을 위한 코드를 유지 관리합니다 [git 리포지토리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/cloud-manager-repositories.html). AEM Archetype을 기반으로 하는 git 리포지토리는 AEM as a Cloud Service 프로그램을 만들 때 자동으로 만들어집니다.

   ![](/help/forms/assets/git-repo-local-and-forms-cs.png)


* 클라우드 기본 환경에는 웹 콘솔(구성 관리자)이 없습니다. 다음을 사용할 수 있습니다 [[!DNL AEM Forms] 구성을 생성할 as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) 및에 대한 CI/CD 파이프라인 [구성 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) Cloud Service 인스턴스에 매핑해야 합니다.

* Adobe Experience Manager Forms은 as a Cloud Service AEM 프로젝트에 많은 새로운 기능과 가능성을 제공합니다. 그러나 AEM Cloud Service과 호환되도록 Adobe Experience Manager Maven 프로젝트에 필요한 몇 가지 변경 사항이 있습니다. 높은 수준에서 AEM은 가변 콘텐츠와 변경할 수 없는 컨텐츠 간의 분할을 준수하기 위해 콘텐츠와 코드를 개별 하위 패키지로 분리해야 합니다. 를 사용하십시오 [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) Adobe Experience Manager as a Cloud Service에 대해 정의된 프로젝트 구조와 호환되도록 컨텐츠 및 코드를 개별 패키지로 분리하여 기존 프로젝트 패키지를 재구성하는 도구입니다.

* Forms as a Cloud Service과 함께 고객 번들을 사용하기 전에 최신 버전의 adobe-aemfd-docmanager를 사용하여 사용자 지정 코드를 다시 컴파일하십시오.

* 사용 [AEM Forms as a Cloud Service 마이그레이션 유틸리티](/help/forms/migrate-to-forms-as-a-cloud-service.md) 적응형 Forms, 테마, 템플릿 및 클라우드 구성을 준비 및 마이그레이션하려면 <!-- AEM 6.3 Forms--> OSGi의 AEM 6.4 Forms 및 OSGi의 AEM 6.5 Forms으로 [!DNL AEM] as a Cloud Service. 사용 [프로그램의 Git 리포지토리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) 기존 적응형 양식 템플릿을 가져오려면 다음을 수행하십시오.

* 이메일은 기본적으로 HTTP 및 HTTP 프로토콜만 지원합니다. [지원 팀에 문의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) 전자 메일 전송을 위한 포트를 활성화하고 환경에 대해 SMTP 프로토콜을 사용하도록 설정합니다.

## 로컬라이제이션

* 현지화된 적응형 Forms의 URL 규칙은 이제 URL에서 로케일 지정을 지원합니다. 새 URL 규칙을 사용하면 Dispatcher 또는 CDN에 현지화된 양식을 캐싱할 수 있습니다. Cloud Service 환경에서 URL 형식을 사용합니다 `http://host:port/content/forms/af/<afName>.<locale>.html` 를 입력하여 대신 현지화된 적응형 양식 버전을 요청합니다. `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`.

* Adobe은 Dispatcher 또는 CDN 캐싱을 사용하는 것을 권장합니다. 미리 입력된 양식의 렌더링 속도를 개선하는 데 도움이 됩니다.


## 적응형 양식

* **규칙 편집기:** AEM Forms as a Cloud Service [규칙 편집기](rule-editor.md#visual-rule-editor). 코드 편집기는 Forms as a Cloud Service에서 사용할 수 없습니다.

   다음 [마이그레이션 유틸리티](/help/forms/migrate-to-forms-as-a-cloud-service.md) 은 사용자 지정 규칙(코드 편집기에서 만든)이 있는 양식을 마이그레이션하는 데 도움이 됩니다. 이 유틸리티는 이러한 규칙을 Forms as a Cloud Service에서 지원되는 사용자 지정 함수로 변환합니다. 규칙 편집기와 함께 재사용 가능한 함수를 사용하여 규칙 스크립트로 얻은 결과를 계속 얻을 수 있습니다. 다음 `onSubmitError` 또는 `onSubmitSuccess` 이제 함수 를 규칙 편집기에서 작업으로 사용할 수 있습니다.

* **미리 채우기 서비스:** 기본적으로 미리 채우기 서비스는 AEM 6.5 Forms에서 서버의 데이터를 병합하는 대신 클라이언트의 적응형 양식과 데이터를 병합합니다. 이 기능은 적응형 양식을 미리 채우는 데 필요한 시간을 개선하는 데 도움이 됩니다. 항상 Adobe Experience Manager Forms 서버에서 병합 작업을 실행하도록 구성할 수 있습니다.

* **작업 제출:** 다음 **이메일** 제출 작업은 첨부 파일을 보내고 전자 메일에 기록 문서(DoR)를 첨부하는 옵션을 제공합니다. 대신 사용할 수 있습니다 **전자 메일을 PDF으로 보내기** 작업을 AEM 6.5 Forms에서 사용할 수 있습니다.

* **automated forms conversion 서비스**: 이 서비스는 Automated forms conversion 서비스에 대한 메타 모델을 제공하지 않습니다. 다음을 수행할 수 있습니다 [automated forms conversion 서비스 설명서에서 다운로드](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

* **XSD 기반 응용 Forms:** XDP-template을 사용하여 Document for Record에 대한 템플릿을 디자인할 수 있습니다. 이 서비스는 XFA 기반의 적응형 Forms을 지원하지 않습니다

* **구성 요소**: 이 서비스는 양식 서명 경험을 지원하지 않으며, 적응형 Forms용 요약 및 확인 구성 요소를 포함하지 않습니다.

## Forms 포털

* Forms Portal의 검색 및 목록, 초안 및 제출, 링크 구성 요소를 사용하여 로그인한 사용자를 위한 양식을 나열할 수 있습니다. 즉시 사용 가능한 Forms Portal(OOTB)에 대한 익명 사용 지원을 사용할 수 없습니다. Forms Portal 을 사용자 지정하여 로그인하지 않은 사용자의 양식을 표시할 수 있습니다.

* 이 서비스는 초안 및 제출된 적응형 Forms에 대한 메타데이터를 유지하지 않습니다.

## 문서 서비스:

Forms as a Cloud Service은 문서 생성 및 문서 조작 RESTful API를 제공합니다. 필요에 따라 이러한 API를 사용하여 요청 시 또는 일괄적으로 문서를 생성하거나 조작할 수 있습니다.

* **문서 서비스: 문서 생성 API(출력 서비스)**: 단일 API 호출 또는 배치에서는 여러 DATA XML 파일이 있는 하나의 템플릿만 사용할 수 있습니다. 단일 API 호출에서 여러 데이터 파일에 여러 템플릿을 사용하는 것은 지원되지 않습니다.

* **문서 조작 API(어셈블러 서비스)**:

   * 문서 서비스나 응용 프로그램을 사용하는 작업은 사용할 수 없습니다. 예를 들어 Microsoft Word에서 PDF으로, Microsoft Excel에서 PDF으로, PDF에 HTML, PostScript(PS)에서 PDF으로, XDP에서 PDF forms으로 지원되지 않습니다. 이러한 작업은 각각 Microsoft Office, Adobe Acrobat, Adobe Distiller, Forms 문서 서비스에 의존합니다.

   * Communications Document Manipulation API와 함께 사용하기 전에 PDF 형식이 아닌 문서를 PDF 형식으로 변환합니다. 예를 들어, 문서가 Microsoft Office, HTML, PostScript(PS), XDP 포맷인 경우, PDF 문서에서 사용하기 전에 이러한 문서를 PDF 형식으로 변환하십시오. 를 사용할 수 있습니다 [ConvertPDF](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/using-convertpdf-service.html) 이러한 전환을 위한 서비스입니다.

* 디지털 서명, 암호화, Reader 확장, 프린터로 보내기, PDF 변환 및 Barcoded Forms 서비스에 AEM 6.5 Forms 환경을 사용할 수 있습니다.


## 데이터 통합(양식 데이터 모델)

* Forms as a Cloud Service에서는 일반 CRUD(만들기, 읽기, 업데이트 및 삭제) 작업을 지원하는 Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive 및 서비스를 데이터 저장소로 사용할 수 있으며, Open API 사양 2.0 및 Open API 3.0 사양이 모두 지원됩니다.

* 또한 이 서비스는 JDBC 커넥터, Microsoft Dynamics, SalesForce, SOAP 기반 웹 서비스 및 OData를 지원하는 서비스를 지원합니다.

* AEM 사용자 프로필을 연결하여 사용자 정보를 검색하고 업데이트할 수도 있습니다.

* Forms 데이터 모델은 데이터를 제출할 HTTP 및 HTTPS 끝점만 지원합니다. 이 서비스는 REST 커넥터에 대한 상호 SSL 및 SOAP 데이터 소스에 대한 x509 인증서 기반 인증을 지원하지 않습니다.


## E-Sign

* 이 서비스는 Adobe Sign와의 OOTB 통합을 제공하며 전자 서명을 위해 DocuSign을 지원합니다.


## HTML5 양식

* AEM 6.5 Forms 환경을 사용하여 다음을 수행할 수 있습니다.

   * xdp 기반 양식을 HTML 5 Forms으로 렌더링합니다. 이 서비스는 HTML 5 Forms(Mobile Forms)을 지원하지 않습니다.

   * 오프라인으로 데이터를 캡처하고 다음에 온라인으로 돌아올 때 동기화합니다. [AEM Forms 작업 공간](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) 앱.

## 대화형 통신

* Communications API를 사용하여 요청 시 또는 일괄적으로 개인화된 문서를 생성할 수 있습니다. 웹 채널 및 에이전트 UI에 AEM 6.5 Forms 환경을 사용할 수 있습니다.

## Microsoft Office용 문서 보안 확장

* Microsoft Office(Digital Rights Management)용 문서 보안 확장은 AEM 6.5 Forms을 지원합니다. 확장은 Forms as a Cloud Service에 사용할 수 없습니다.








<!-- 

### HTML5 Forms (Mobile Forms)

The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms.

### Adaptive Forms 

* **XSD-Based Adaptive Forms:** The service does not support HTML5 Forms (Mobile Forms). If you render your XDP-based forms as HTML5 Forms, you can continue using the feature on AEM 6.5 Forms. You can use XDP-template to design a template for Document for Record. The service does not support XFA based Adaptive Forms  
* **Importing Adaptive Form templates:** Use build pipeline and corresponding Git repository of your program to import existing Adaptive Form templates. 
*  **Rule editor:** AEM Forms as a Cloud Service provides a hardened [Rule editor](rule-editor.md#visual-rule-editor). The code editor is not available on Forms as a Cloud Service. The migration utility helps you migrate your forms that have custom rules (created in code editor). The utility converts such rules into custom functions supported on Forms as a Cloud Service. You can use the reusable functions with Rule editor to continue obtaining results obtained with rule scripts  The `onSubmitError` or `onSubmitSuccess` functions are now available as actions the Rule Editor.  
* **Drafts and submissions:** The service does not retain metadata for drafts and submitted Adaptive Forms.  
* **Prefill Service:** By default, the prefill service merges data with an Adaptive Form at client as opposed to merging data on Server in AEM 6.5 Forms. The feature helps improve the time required to prefill an Adaptive Form. You can always configure to run the merge action on the Adobe Experience Manager Forms Server. 
* **Submit actions:** The **Email as PDF** action is not available. The **Email** submit action provide options to send attachments and attach Document of Record (DoR) with email. 
* **Components**:  The service does not support in-form signing experience and does not include the Summary and Verify components for Adaptive Forms.  
* **Forms portal**: Support for anonymous use of Forms portal is not available out of the box (OOTB). You can customize the forms portal to enable displaying forms for non-logged in users.

### Form Data Model

* Forms data model supports only HTTP and HTTPs endpoints to submit data. The service does not support Mutual SSL for REST connector and x509 certificate-based authentication for SOAP data sources. * Forms as a Cloud Service allows to use Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive, and services supporting general CRUD (Create, Read, Update, and Delete) operations as data stores, both Open API specification 2.0 and Open API specification are supported. The service also provides support for JDBC connector.


### Automated Forms Conversion Service     

The service does not provide meta-model for Automated Forms Conversion Service. You can [download it from Automated Forms Conversion Service documentation](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).


### Configurations

* Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment.  
* If you use custom bundles, recompile your code with latest version of adobe-aemfd-docmanager before using these bundles with Forms as a Cloud Service. 


### Document Services: Document Manipulation APIs (Assembler Service)

The service does not support operations dependent on other services or applications:  

* Conversion of documents in a non-PDF format to a PDF format is not supported. For example, Microsoft Word to PDF, Microsoft Excel to PDF, and HTML to PDF are not supported. If your documents are in a non-PDF format. Convert such documents to PDF format before using those with Communications Document Manipulation APIs. For example, if your documents are in Microsoft Office, HTML, PostScript (PS), XDP format, convert these documents to PDF format before using those with PDF documents. 
* Adobe Distiller-based conversions are not supported. For example, PostScript(PS) to PDF
* Forms Service-based conversions are not supported. For example, XDP to PDF Forms.
* The service does not support converting a Signed PDF or Transparent PDF to another PDF format.
* Applying usage rights using Reader Extensions Service is not available. 
* The service does not provide the ability to convert signed or transparent PDF Documents to PDF/A format. 

### Document Services: Document Generation APIs (Output Service)

* In a single API call or batch, you can use one template with multiple DATA XML files. Using mutiple templates with multiple data files in a single API call is not supported. 

### Other differences

* A cloud-native environment does not have web console (configuration manager). You can use [[!DNL AEM Forms] as a Cloud Service SDK to generate configurations](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) and CI/CD pipeline to [deploy the configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) to your Cloud Service instance.
* Email support only HTTP and HTTPs protocols, by default. [Contact the support team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) to enable ports for sending emails and to enable SMTP protocol for your environment.
* The service does not support converting a Signed PDF or Transparent PDF to another PDF format.* Before using your customer bundles with Forms as a Cloud Service, recompile your custom code with the latest version of adobe-aemfd-docmanager* URL convention of localized Adaptive Forms now supports specifying a locale in the URL. New URL convention enables caching localized forms on a Dispatcher or CDN. On Cloud Service environment, use the URL format `http://host:port/content/forms/af/<afName>.<locale>.html` to request a localized version of an Adaptive Form instead of `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe recommends using Dispatcher or CDN caching. It helps improve rendering speed of prefilled forms 
* Adobe Experience Manager Forms as a Cloud Service brings many new features and possibilities into your AEM Projects. However, there are some changes required to Adobe Experience Manager Maven projects to be compatible with AEM Cloud Service. At a high-level, AEM requires a separation of content and code into discrete subpackages to respect the split between mutable and immutable content. Use the [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) tool to restructure existing project packages by separating content and code into discrete packages to be compatible with the project structure defined for Adobe Experience Manager as a Cloud Service.
-->




