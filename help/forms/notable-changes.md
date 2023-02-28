---
title: AEM 6.5 Forms과 AEM 클라우드 서비스 간에 변경된 사항
description: Experience Manager Forms 사용자로서 Adobe Experience Manager Forms as a Cloud Service으로 업그레이드하려고 합니까? Cloud Service으로 업그레이드하거나 마이그레이션하기 전에 가장 눈에 띄는 변경 사항에 대해 알아봅니다.
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
contentOwner: khsingh
source-git-commit: 7c157cbeb530627c1b888379896ddffda3f3efb3
workflow-type: tm+mt
source-wordcount: '1215'
ht-degree: 3%

---

# 기존 Adobe Experience Manager 6.5 Forms 사용자의 주요 변경 사항  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms은 Adobe Experience Manager Forms 온-프레미스 및 as a Cloud Service과 비교하여 기존 기능에 몇 가지 주목할 만한 변경 사항을 제공합니다 [!DNL Adobe-Managed Service] 환경. 주요 차이점은 아래에 나와 있습니다.

| 기능/기능 | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms |
|---|---|---|
| 클라우드 기반의 아키텍처 | ✅ | ⛌ |
| 로드 기반 자동 크기 조절 | ✅ | ⛌ |
| 업그레이드에 대한 다운타임 없음 | ✅ | ⛌ |
| 기능 롤아웃 빈도 | 애자일* | 분기별 |
| CDN(컨텐츠 전달 네트워크) 포함 | ✅ | ⛌ |
| 최고의 복원력과 효율성을 제공하도록 최적화된 토폴로지 | ✅ | ⛌ |
| 클라우드 기반의 개발 환경 | ✅ | ⛌ |
| Cloud Manager를 통한 셀프 서비스 | ✅ | ⛌ |
| CI/CD(Continuous Integration and Continuous Delivery)를 사용한 자동화된 업그레이드 | ✅ | ⛌ |
| [!DNL Micosoft Power Automate]와 통합  | ✅ | ⛌ |
| [!DNL DocuSign]와 통합  | ✅ | ⛌ |
| Microsoft Dynamics 및 Salesforce와의 쉬운 연결 | ✅ | ⛌ |
| Microsoft Azure 데이터 스토어를 통한 편리한 연결 | ✅ | ⛌ |
| 경화된 규칙 편집기 | ✅ | ⛌ |
| 양식 만들기 마법사 | ✅ | ⛌ |
| 기록 문서에 대한 사용자 지정 XCI 지원 | ✅ | ⛌ |
| 응용 Forms <sup>1</sup> | ✅ | ✅ |
| 여러 데이터 소스와 데이터 통합 | ✅ | ✅ |
| 통신 API(문서 서비스) <sup>2,3</sup> | ✅ | ✅ |
| automated forms conversion 서비스 <sup>4</sup> | ✅ | ✅ |
| [!DNL Adobe Sign]와 통합  | ✅ | ✅ |
| [!DNL AEM Sites]와 통합  | ✅ | ✅ |
| [!DNL Adobe Launch]와 통합  | ✅ | ✅ |
| [!DNL Adobe Analytics]와 통합  | ✅ | ✅ |
| Forms 포털 <sup>5개</sup> | ✅ | ✅ |
| AEM 워크플로우 | ✅ | ✅ |
| 기록 문서 | ✅ | ✅ |
| Captcha 숨김 | ✅ | ✅ |
| 재사용 가능한 양식 데이터 모델 구성 | ✅ | ✅ |
| Acroform 기반 레코드 문서 | ✅ | ✅ |
| Adobe Sign에 대한 정부 ID 기반 ID 인증 활성화 응용 Forms | ✅ | ✅ |
| HTML5 <sup>6</sup> | ⛌ | ✅ |
| 문서 보안 | ⛌ | ✅ |

서비스를 계속 진행하기 전에 다음 예외적인 경우를 고려하십시오.

+++ 1. 적응형 Forms

* **XSD 기반 응용 Forms:** 이 서비스는 HTML 5 Forms(Mobile Forms)을 지원하지 않습니다. XDP 기반 양식을 HTML 5 Forms으로 렌더링하는 경우 AEM 6.5 Forms에서 기능을 계속 사용할 수 있습니다. XDP-template을 사용하여 Document for Record에 대한 템플릿을 디자인할 수 있습니다. 이 서비스는 XFA 기반의 적응형 Forms을 지원하지 않습니다
* **적응형 양식 템플릿 가져오기:** 빌드 파이프라인 및 프로그램의 해당 Git 저장소를 사용하여 기존 적응형 양식 템플릿을 가져옵니다.
* **규칙 편집기:** AEM Forms as a Cloud Service [규칙 편집기](rule-editor.md#visual-rule-editor). 코드 편집기는 Forms as a Cloud Service에서 사용할 수 없습니다. 마이그레이션 유틸리티는 코드 편집기에서 만든 사용자 지정 규칙이 있는 양식을 마이그레이션하는 데 도움이 됩니다. 이 유틸리티는 이러한 규칙을 Forms as a Cloud Service에서 지원되는 사용자 지정 함수로 변환합니다. 규칙 편집기와 함께 재사용 가능한 함수를 사용하여 규칙 스크립트로 얻은 결과를 계속 얻을 수 있습니다. `onSubmitError` 또는 `onSubmitSuccess` 이제 함수를 규칙 편집기에서 작업으로 사용할 수 있습니다.
* **초안 및 제출:** 이 서비스는 초안 및 제출된 적응형 Forms에 대한 메타데이터를 유지하지 않습니다.
* **미리 채우기 서비스:** 기본적으로 미리 채우기 서비스는 AEM 6.5 Forms에서 서버의 데이터를 병합하는 대신 클라이언트의 적응형 양식과 데이터를 병합합니다. 이 기능은 적응형 양식을 미리 채우는 데 필요한 시간을 개선하는 데 도움이 됩니다. 항상 Adobe Experience Manager Forms 서버에서 병합 작업을 실행하도록 구성할 수 있습니다.
* **작업 제출:** 다음 **전자 메일을 PDF으로 보내기** 작업을 사용할 수 없습니다. 다음 **이메일** 제출 작업은 첨부 파일을 보내고 전자 메일에 기록 문서(DoR)를 첨부하는 옵션을 제공합니다.
* **구성 요소**: 이 서비스는 양식 서명 경험을 지원하지 않으며, 적응형 Forms용 요약 및 확인 구성 요소를 포함하지 않습니다.



+++


+++ 2. 문서서비스 문서 조작 API(어셈블러 서비스)


서비스는 다른 서비스 또는 응용 프로그램에 종속된 작업을 지원하지 않습니다.

* PDF이 아닌 형식의 문서를 PDF 형식으로 변환할 수 없습니다. 예를 들어 Microsoft Word에서 PDF으로, Microsoft Excel에서 PDF으로, PDF으로 HTML은 지원되지 않습니다. 문서가 PDF 형식이 아닌 경우 Communications Document 조작 API에서 사용하는 문서를 사용하기 전에 이러한 문서를 PDF 형식으로 변환합니다. 예를 들어, 문서가 Microsoft Office, HTML, PostScript(PS), XDP 포맷인 경우, PDF 문서에서 사용하기 전에 이러한 문서를 PDF 형식으로 변환하십시오.
* Adobe Distiller 기반 전환은 지원되지 않습니다. 예를 들어 PostScript(PS)에서 PDF
* Forms 서비스 기반 전환은 지원되지 않습니다. 예를 들어 XDP에서 PDF forms으로 이동합니다.
* 이 서비스는 서명된 PDF 또는 투명 PDF을 다른 PDF 형식으로 변환하는 것을 지원하지 않습니다.
* Reader 확장 서비스를 사용하여 사용 권한을 적용할 수 없습니다.
* 이 서비스는 서명 또는 투명한 PDF 문서를 PDF/A 형식으로 변환하는 기능을 제공하지 않습니다.

+++


+++ 3. 문서서비스 문서 생성 API(출력 서비스)

단일 API 호출 또는 배치에서는 여러 DATA XML 파일이 있는 하나의 템플릿만 사용할 수 있습니다. 단일 API 호출에서 여러 데이터 파일에 여러 템플릿을 사용하는 것은 지원되지 않습니다.

+++

+++ 4. Automated forms conversion 서비스

이 서비스는 Automated forms conversion 서비스에 대한 메타 모델을 제공하지 않습니다. 다음을 수행할 수 있습니다 [automated forms conversion 서비스 설명서에서 다운로드](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model).

+++

+++ 5. Forms 포털

즉시 사용 가능한 Forms 포털(OOTB)에 대한 익명 사용 지원을 사용할 수 없습니다. 로그인하지 않은 사용자에 대해 양식을 표시할 수 있도록 양식 포털을 사용자 지정할 수 있습니다.

+++


+++ 6. HTML5 Forms(모바일 Forms)

* 이 서비스는 HTML 5 Forms(Mobile Forms)을 지원하지 않습니다. XDP 기반 양식을 HTML 5 Forms으로 렌더링하는 경우 AEM 6.5 Forms에서 기능을 계속 사용할 수 있습니다.

* 오프라인으로 데이터를 캡처하고 다음에 온라인으로 돌아올 때 동기화하기 위한 사용 사례가 있을 경우 [AEM Forms 작업 공간](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-aem-forms-workspace/introduction-html-workspace.html) AEM 6.5 Forms의 기능입니다.

+++


+++ 7. 양식 데이터 모델

* Forms 데이터 모델은 데이터를 제출할 HTTP 및 HTTP 끝점만 지원합니다. 이 서비스는 REST 커넥터에 대한 상호 SSL 및 SOAP 데이터 소스에 대한 x509 인증서 기반 인증을 지원하지 않습니다.

* Forms as a Cloud Service에서는 일반 CRUD(만들기, 읽기, 업데이트 및 삭제) 작업을 지원하는 Microsoft Azure Blob, Microsoft Sharepoint, Microsoft OneDrive 및 서비스를 데이터 저장소로 사용할 수 있으며, Open API 사양 2.0 및 Open API 사양이 모두 지원됩니다. 이 서비스는 JDBC 커넥터를 지원합니다.

+++


+++ 8. 개발자 환경

* 클라우드 기본 환경에는 웹 콘솔(구성 관리자)이 없습니다. 다음을 사용할 수 있습니다 [[!DNL AEM Forms] 구성을 생성할 as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) 및에 대한 CI/CD 파이프라인 [구성 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) Cloud Service 인스턴스에 매핑해야 합니다.
* 이메일은 기본적으로 HTTP 및 HTTP 프로토콜만 지원합니다. [지원 팀에 문의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) 전자 메일 전송을 위한 포트를 활성화하고 환경에 대해 SMTP 프로토콜을 사용하도록 설정합니다.
* 이 서비스는 서명된 PDF 또는 투명 PDF을 다른 PDF 형식으로 변환하는 것을 지원하지 않습니다. Forms as a Cloud Service과 함께 고객 번들을 사용하기 전에 현지화된 적응형 Forms의 최신 버전의 adobe-aemfd-docmanager* URL 규칙을 사용하여 사용자 지정 코드를 다시 컴파일하십시오. 에서는 이제 URL에서 로케일을 지정할 수 있습니다. 새 URL 규칙을 사용하면 Dispatcher 또는 CDN에 현지화된 양식을 캐싱할 수 있습니다. Cloud Service 환경에서 URL 형식을 사용합니다 `http://host:port/content/forms/af/<afName>.<locale>.html` 를 입력하여 대신 현지화된 적응형 양식 버전을 요청합니다. `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe은 Dispatcher 또는 CDN 캐싱을 사용하는 것을 권장합니다. 미리 입력된 양식의 렌더링 속도를 개선하는 데 도움이 됩니다
* Adobe Experience Manager Forms은 as a Cloud Service AEM 프로젝트에 많은 새로운 기능과 가능성을 제공합니다. 그러나 AEM Cloud Service과 호환되도록 Adobe Experience Manager Maven 프로젝트에 필요한 몇 가지 변경 사항이 있습니다. 높은 수준에서 AEM은 가변 콘텐츠와 변경할 수 없는 컨텐츠 간의 분할을 준수하기 위해 콘텐츠와 코드를 개별 하위 패키지로 분리해야 합니다. 를 사용하십시오 [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) Adobe Experience Manager as a Cloud Service에 대해 정의된 프로젝트 구조와 호환되도록 컨텐츠 및 코드를 개별 패키지로 분리하여 기존 프로젝트 패키지를 재구성하는 도구입니다.


+++

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




