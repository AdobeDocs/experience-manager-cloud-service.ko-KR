---
title: AEM Forms as a Cloud Service 커뮤니케이션 소개
description: 통신 API를 사용하여 문서에 서명, 인증 또는 보호하고, PDF 생성 프로세스를 자동화하고, PDF 문서를 다른 형식으로 변환합니다.
Keywords: How to generate document?, Generate PDF document, Manipulation PDF documents, Assembling PDF documents, Validating PDF document, APIs used in encrypting or decrypting PDFs
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '1433'
ht-degree: 80%

---


# AEM Forms as a Cloud Service 커뮤니케이션 소개 {#frequently-asked-questions}


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/overview-aem-document-services.html) |
| AEM as a Cloud Service | 이 문서 |

커뮤니케이션 기능은 비즈니스 서신, 명세서, 요청 처리 레터, 혜택 공지, 월별 청구서 또는 시작 키트 등 개인화 및 표준화된 브랜드 승인 문서를 만드는 데 도움이 됩니다.

이 기능은 문서를 생성하고 조작하는 API를 제공합니다. 주문형 문서를 생성 또는 조작하거나 배치 작업을 생성하여 정의된 간격으로 여러 문서를 생성할 수 있습니다. 통신 API는 다음 사항을 제공합니다.

* 간소화된 온디맨드 및 배치 문서 생성 기능.

* 주문형 PDF 문서를 결합하고, 재배열하고 확인하는 기능.

* 더 쉽게 외부 시스템과 통합할 수 있는 HTTP API. 온디맨드(낮은 대기 시간) 및 배치 작업(처리량이 많은 작업)용 별도 API가 포함됩니다.

* 데이터에 대한 보안 액세스. 통신 API는 고객이 지정한 데이터 저장소의 데이터에만 연결하고 액세스하여 커뮤니케이션의 보안 수준을 높입니다.

![샘플 신용카드 명세서](assets/statement.png)
신용카드 명세서는 통신 API를 통해 생성될 수 있습니다. 이 샘플 명세서는 동일한 템플릿을 사용하지만 신용카드 사용량에 따라 각 고객별로 별도의 데이터를 사용합니다.

## 문서 생성

통신 문서 생성 API는 템플릿(XFA 또는 PDF)을 고객 데이터(XML)와 결합하여 PS, PCL, DPL, IPL, ZPL 등 PDF 및 인쇄 형식으로 문서를 생성하는 데 도움이 됩니다. 해당 API는 [XML 데이터](communications-known-issues-limitations.md#form-data)가 포함된 PDF 및 XFA 템플릿을 활용하여 배치 작업을 통해 주문형 단일 문서이나 여러 문서를 생성합니다.

일반적으로 [디자이너](use-forms-designer.md)를 사용하여 템플릿을 만들고 통신 API를 사용하여 데이터를 템플릿과 병합합니다. 애플리케이션은 출력 문서를 네트워크 프린터, 로컬 프린터 또는 스토리지 시스템에 전송하여 보관합니다. 일반적인 기본 제공 및 사용자 지정 워크플로는 다음과 같습니다.

![통신 문서 생성 워크플로](assets/communicaions-workflow.png)

사용 사례에 따라 웹 사이트나 스토리지 서버를 통해 해당 문서를 다운로드할 수도 있습니다.

문서 생성 API의 몇 가지 예는 다음과 같습니다.

### PDF 문서 만들기 {#create-pdf-documents}

문서 생성 API를 사용하여 양식 디자인과 XML 양식 데이터를 기반으로 하는 PDF 문서를 만들 수 있습니다. 출력은 비대화형 PDF 문서입니다. 즉, 사용자는 양식 데이터를 입력하거나 수정할 수 없습니다. 기본 워크플로는 XML 양식 데이터를 양식 디자인과 병합하여 PDF 문서를 만드는 것입니다. 다음 일러스트레이션은 양식 디자인과 XML 양식 데이터를 병합하여 PDF 문서를 생성하는 모습을 보여 줍니다.

![PDF 문서 만들기](assets/outPutPDF_popup.png)
그림: PDF 문서를 만드는 일반적인 워크플로

### PS(PostScript), PCL(Printer Command Language), ZPL(Zebra Printing Language) 문서 만들기 {#create-PS-PCL-ZPL-documents}

문서 생성 API를 사용하여 XDP 양식 디자인 또는 PDF 문서를 기반으로 하는 PS(PostScript), PCL(Printer Command Language), ZPL(Zebra Printing Language) 문서를 만들 수 있습니다. 해당 API는 양식 디자인을 양식 데이터와 병합하여 문서를 생성하는 데 도움이 됩니다. 문서를 파일에 저장하고, 사용자 지정 프로세스를 개발하여 프린터에 전송할 수 있습니다.

<!-- ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that con tains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

 -->

### 배치 데이터를 처리하여 여러 문서 만들기 {#processing-batch-data-to-create-multiple-documents}

문서 생성 API를 사용하여 XML 배치 데이터 소스 내의 각 기록에 별도의 문서를 만들 수 있습니다. 비동기화 모드에서 문서를 일괄 생성할 수 있습니다. 다양한 매개변수를 구성하여 변환한 다음 배치 프로세스를 시작할 수 있습니다.

![PDF 문서 만들기](assets/ou_OutputBatchMany_popup.png)

<!-- You can can also create a single document that contains all records (this functionality is the default).  Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents. -->

<!-- The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents. 

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use document generation APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document's fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form. -->

## 문서 조작

통신 문서 조작 API를 통해 PDF 문서를 결합하고, 재배열하고 확인할 수 있습니다. 일반적으로 DDX를 만들어 문서 조작 API에 제출하여 문서를 조합하거나 재정렬합니다. [DDX 문서](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf)에서는 소스 문서를 사용하여 필요한 문서 세트를 생성하는 방법에 대한 지침을 제공합니다. DDX 참조 문서에서는 지원되는 모든 작업에 대한 자세한 정보를 제공합니다. 문서 조작 API의 몇 가지 예는 다음과 같습니다.

### PDF 문서 어셈블

문서 조작 API를 사용하여 두 개 이상의 PDF 또는 XDP 문서를 단일 PDF 문서 또는 PDF 포트폴리오로 어셈블할 수 있습니다. 다음은 PDF 문서를 어셈블할 수 있는 몇 가지 방법입니다.

* 간단한 PDF 문서 어셈블
* PDF 포트폴리오 만들기
* 암호화된 문서 어셈블
* Bates 번호 매기기를 사용하여 문서 어셈블
* 문서 변환 및 어셈블

![여러 PDF 문서에서 간단한 PDF 어셈블하기](assets/as_document_assembly.png)
그림: 여러 PDF 문서에서 간단한 PDF 문서 어셈블하기

### PDF 문서 디스어셈블

문서 조작 API를 사용하여 PDF 문서를 디스어셈블할 수 있습니다. API는 소스 문서에서 페이지를 추출하거나 책갈피를 기준으로 소스 문서를 나눌 수 있습니다. 일반적으로 이 작업은 명령문 컬렉션 등 여러 개별 문서에서 PDF 문서가 만들어진 경우에 유용합니다.

* 소스 문서에서 페이지 추출
* 책갈피를 기준으로 소스 문서 나누기

![책갈피를 기준으로 소스 문서를 여러 문서로 나누기](assets/as_intro_pdfsfrombookmarks.png)
그림: 책갈피를 기준으로 소스 문서를 여러 문서로 나누기

### PDF/A호환 문서로 변환하고 확인합니다.

문서 조작 API를 사용하여 PDF 문서를 PDF/A 호환 문서로 변환하고 PDF 문서가 PDF/A 호환인지 여부를 확인할 수 있습니다. PDF/A는 문서 내용을 장기간 보존하기 위한 보관 형식입니다. 글꼴이 문서 내에 임베드되어 있고 파일이 압축 해제되어 있습니다. 따라서 PDF/A 문서는 일반적으로 표준 PDF 문서보다 큽니다. 또한 PDF/A 문서에는 오디오 및 비디오 콘텐츠가 포함되지 않습니다.

<!-- 

## Document utilities

Document utilities synchronous APIs helps you convert documents between PDF and XDP file formats, and query information about a PDF document. For example, you can determine whether a PDF document contains comments or attachments. 

### Retrieve PDF document properties

You can [query a PDF document](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/pdf-utility-sync/#tag/Document-Extraction/) for the following information:

* Is a PDF Document: Check whether the source document is a PDF document.
* Is a fillable form: Check whether the source PDF document is a fillable form.
* Form Type: Retrieve the form type of the document.
* Check for Attachments: Check whether the source PDF document has any attachments.
* Check for Comments: Check whether the source PDF document has any review comments.
* Is a PDF Package: Check whether the document is a PDF package.
* Get the PDF Version: Retrieve the [version of the PDF document](https://en.wikipedia.org/wiki/History_of_PDF).
* Recommended Acrobat Version: Retrieve the required version of Acrobat (Reader) to open the PDF document.
* Is an XFA Document: Check whether the source PDF document is an XFA-based PDF document.
* Is Shell PDF: Check whether the source PDF document is shell PDF. A shell PDF contains only an XFA stream, font and image resources, and one page that is either blank or contains a warning that the document must be opened using Acrobat or Adobe Reader. The shell PDF is used with PDF transformation to optimize delivery of PDFForm transformations only.
* Get the XFA Version: Retrieve the [XFA Version for an XFA-based PDF document](https://en.wikipedia.org/wiki/XFA#XFA_versions).

### Convert PDF Documents into XDP Documents

The [PDF to XDP API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/pdf-utility-sync/#tag/Document-Conversion) converts a PDF document to an XDP file. For a PDF document to be successfully converted to an XDP file, the PDF document must contain an XFA stream in the dictionary. -->

## 문서 보증 {#doc-assurance}

DocAssurance 서비스에는 서명 및 암호화 API가 포함되어 있습니다.

### 서명 API

서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다. 보안 기능은 문서 자체에 적용되므로, 문서는 전체 라이프 사이클에 대해 안전하게 제어됩니다. 문서는 오프라인으로 다운로드할 때와 조직에 다시 제출될 때 방화벽 이후에도 안전하게 보호됩니다. 서명 API를 사용하여 다음 작업을 수행할 수 있습니다.

* PDF 문서에 서명 필드를 추가합니다.
* PDF 문서에서 지정된 서명 필드에 서명합니다.
* PDF 문서 인증

### 암호화 API

암호화 API를 사용하면 문서를 암호화하고 해독할 수 있습니다. 문서가 암호화되면 해당 내용을 읽을 수 없게 됩니다. 인가된 사용자는 문서의 암호를 해독하여 콘텐츠에 액세스할 수 있습니다. PDF 문서가 암호로 암호화된 경우 Adobe Reader 또는 Adobe Acrobat에서 문서를 보려면 열기 암호를 지정해야 합니다. 마찬가지로, PDF 문서가 인증서로 암호화되어 있는 경우, 사용자는 PDF 문서를 암호화하는 데 사용된 인증서(개인 키)에 해당하는 공개 키로 PDF 문서의 암호를 해독해야 합니다.

암호화 API를 사용하여 다음 작업을 수행할 수 있습니다.

* 암호로 PDF 문서를 암호화합니다.
* PDF 문서에서 암호 기반 암호화를 제거합니다.
* PDF 문서에 적용된 보안 유형을 검색합니다.

서명 API 및 암호화 API는 모두 [동기 API](#types-of-communications-apis-types).


## 통신 API 유형 {#types}

커뮤니케이션은 주문형 및 배치 문서 생성에 HTTP API를 제공합니다.

* **[동기식 API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)**&#x200B;는 주문형, 대기 시간이 낮은 단일 기록 문서 생성 시나리오에 적합합니다. 해당 API는 사용자 액션 기반 사용 사례에 보다 적합합니다. 예: 사용자 양식 작성 완료 후 문서 생성.

* **[배치 API(비동기 API)](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)**&#x200B;는 처리량이 높은 예약된 문서 생성 시나리오에 적합합니다. 해당 API는 배치 문서를 생성합니다. 예: 매월 생성되는 전화요금 청구서, 신용카드 명세서와 혜택 명세서.

## 온보딩

커뮤니케이션 기능은 Forms as a Cloud Service 사용자용 독립 실행형 모듈과 추가 기능 모듈로 제공됩니다. Adobe 영업팀 또는 Adobe 담당자에게 문의하여 액세스 권한을 요청할 수 있습니다. Adobe는 조직에 대한 액세스 권한을 활성화하고 조직의 책임자로 지정된 사람에게 필요한 권한을 제공합니다. 관리자는 조직의 Forms as a Cloud Service 개발자(사용자)에 대한 액세스 권한을 부여하여 API를 사용할 수 있습니다.

온보딩 후 Forms as a Cloud Service 환경의 커뮤니케이션 기능을 활성화하려면

1. Cloud Manager에 로그인하고 AEM Forms as a Cloud Service 인스턴스를 엽니다.

1. 프로그램 편집 옵션을 열고 솔루션 및 추가 기능 탭으로 이동하여 **[!UICONTROL 양식 - 커뮤니케이션]** 옵션을 선택합니다.

   ![커뮤니케이션](assets/communications.png)

   **[!UICONTROL 양식 - 디지털 등록]** 옵션이 이미 활성화된 경우 **[!UICONTROL 양식 - 커뮤니케이션 추가 기능]** 옵션을 선택합니다.

   ![추가 기능](assets/add-on.png)

1. **[!UICONTROL 업데이트]**&#x200B;를 클릭합니다.

1. 빌드 파이프라인을 실행합니다. 빌드 파이프라인이 성공하면 환경에 통신 API가 활성화됩니다.

>[!NOTE]
>
> 문서 조작 API를 활성화하고 구성하려면 다음 규칙을 [Dispatcher 구성](setup-local-development-environment.md#forms-specific-rules-to-dispatcher)에 추가합니다.
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

<!--

Communication help you combine a template and XML data to generate print documents in various formats. The service lets you generate documents in synchronous and batch modes. The APIs enables you to create applications that let you:

  * Generate documents by populating template files (PDF and XDP) with XML data.
  * Generate output forms in various formats, including non-interactive PDF print streams.

Consider a scenario where you have one or more templates and multiple records of XML data for each template. You can use Communications APIs to generate a print document for each record.  You can also combine the records into a single document.  The result is a non-interactive PDF document. A non-interactive PDF document does not let users enter data into its fields.

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as REST endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example ExpenseClaim.xdp). You can specify a fully-qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document.  

The [API reference documentation](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:b1223732-ae0f-4921-bdc0-c31e48b56044) provides detailed information about all the parameters, authentication methods, and various services provided by APIs. The API reference documentation is also available in the .yaml format. You can download the .yaml for [Batch APIs](assets/batch-api.yaml) or [non-Batch API.yaml](assets/non-batch-api.yaml) file and upload it to postman to check functionality of APIs.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

Uploading Communication APIs .yaml file to postman to check functionality of APIs.

## Using the Communications APIs {#workflows}

Typically, you create a template using [Designer](use-forms-designer.md) and use communications APIs ( generatePDFOutput and generatePrintedOutput) to:

* Convert these templates to various formats, including PDF, PostScript, ZPL, and PCL.
* Merge XML form data with a form design to generate a document.
* Generate a document without merging XML form data into the document. However, the primary workflow is merging data into the document.

Then, the output document is stored to a file. You can design custom workflows to send the file to a network printer, a local printer, or to a storage system for archival. A typical out of the box and custom workflows look like the following:

![Communications Workflow](assets/communicaions-workflow.png)

### Create PDF documents {#create-pdf-documents}

You can use the _generatePDFOutput_ API to create PDF document that is based on a form design and XML form data. The output is a non-interactive PDF document. That is, users cannot enter or modify form data. A basic workflow is to merge XML form data with a form design to create a PDF document. The following illustration shows the merging of a form design and XML form data to produce a PDF document.

![Create PDF Documents](assets/outPutPDF_popup.png)

### Create PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) document {#create-PS-PCL-ZPL-documents}

You can use Communications APIs to create PostScript (PS), Printer Command Language (PCL), and Zebra Printing Language (ZPL) document that are based on an XDP form design or PDF document. The _generatePrintedOutput_ API merges a form design with form data to generate a document. You can save the document to a file and develop a custom process to send it to a printer.

 ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that contains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

### Processing batch data to create multiple documents {#processing-batch-data-to-create-multiple-documents}

You create separate documents for each record within an XML batch data source. You can can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents.

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents.

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use the Communications APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document's fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form.  -->

## 추가 참조 {#see-also}


* [통신 처리 - 동기 API](/help/forms/aem-forms-cloud-service-communications.md)
* [통신 처리 - 일괄 처리 API](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
