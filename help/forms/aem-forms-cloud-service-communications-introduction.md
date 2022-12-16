---
title: Forms as a Cloud Service Communications 소개
description: 데이터를 XDP 및 PDF 템플릿과 자동으로 병합하거나 PCL, ZPL 및 PostScript 형식으로 출력을 생성합니다
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: 20e54ff697c0dc7ab9faa504d9f9e0e6ee585464
workflow-type: tm+mt
source-wordcount: '1442'
ht-degree: 2%

---

# AEM Forms as a Cloud Service 통신 사용 {#frequently-asked-questions}

커뮤니케이션 기능을 사용하면 비즈니스 서신, 명세서, 청구 처리 편지, 혜택 공지, 월별 청구서 또는 환영 키트와 같은 브랜드 승인, 개인화 및 표준화된 문서를 만들 수 있습니다.

이 기능은 문서를 생성하고 조작하는 API를 제공합니다. 필요에 따라 문서를 생성 또는 조작하거나 배치 작업을 만들어 정의된 간격으로 여러 문서를 생성할 수 있습니다. 통신 API는 다음을 제공합니다.

* 온디맨드 및 배치 문서 생성 기능이 간소화되었습니다.

* PDF 문서를 필요에 따라 결합, 재정렬 및 검증할 수 있습니다.

* 외부 시스템과의 쉬운 통합을 위한 HTTP API. 주문형(지연 시간) 및 배치 작업(높은 처리량 작업)에 대한 별도의 API가 포함됩니다.

* 데이터에 대한 보안 액세스. 통신 API는 고객이 지정한 데이터 저장소에서만 데이터를 연결하고 액세스하므로 커뮤니케이션을 매우 안전하게 만듭니다.

![신용 카드 명세서 샘플](assets/statement.png)
Communications API를 사용하여 신용 카드 명세서를 만들 수 있습니다. 이 샘플 문은 동일한 템플릿을 사용하지만 신용 카드 사용에 따라 각 고객에 대해 별도의 데이터를 사용합니다.

## 문서 생성

통신 문서 생성 API는 템플릿(XFA 또는 PDF)을 고객 데이터(XML)와 결합하여 PS, PCL, DPL, IPL 및 ZPL 포맷과 같은 PDF 및 인쇄 형식으로 문서를 생성하는 데 도움이 됩니다. 이러한 API는 [XML 데이터](communications-known-issues-limitations.md#form-data) 배치 작업을 사용하여 단일 요청 문서 또는 여러 문서를 생성할 수 있습니다.

일반적으로 [디자이너](use-forms-designer.md) 및 를 사용하여 데이터를 템플릿과 병합합니다. 애플리케이션이 출력 문서를 네트워크 프린터, 로컬 프린터 또는 스토리지 시스템으로 전송하여 아카이빙할 수 있습니다. 일반적인 기본 제공 및 사용자 지정 워크플로우는 다음과 같습니다.

![통신 문서 생성 워크플로우](assets/communicaions-workflow.png)

사용 사례에 따라 웹 사이트나 스토리지 서버를 통해 이러한 문서를 다운로드할 수 있도록 할 수도 있습니다.

문서 생성 API의 몇 가지 예는 다음과 같습니다.

### PDF 문서 만들기 {#create-pdf-documents}

문서 생성 API를 사용하여 양식 디자인 및 XML 양식 데이터를 기반으로 하는 PDF 문서를 만들 수 있습니다. 출력은 비대화형 PDF 문서입니다. 즉, 사용자는 양식 데이터를 입력하거나 수정할 수 없습니다. 기본 워크플로우는 XML 양식 데이터를 양식 디자인과 병합하여 PDF 문서를 만드는 것입니다. 다음 그림은 양식 디자인과 XML 양식 데이터를 병합하여 PDF 문서를 생성하는 방법을 보여 줍니다.

![PDF 문서 만들기](assets/outPutPDF_popup.png)
그림: PDF 문서를 만드는 일반적인 워크플로우

### PostScript(PS), 프린터 명령 언어(PCL), Zebra Printing Language(ZPL) 문서 작성 {#create-PS-PCL-ZPL-documents}

문서 생성 API를 사용하여 XDP 양식 디자인 또는 PDF 문서를 기반으로 하는 PS(PostScript), PCL(Printer Command Language) 및 ZPL(Zebra Printing Language) 문서를 만들 수 있습니다. 이러한 API는 양식 디자인을 양식 데이터와 병합하여 문서를 생성하는 데 도움이 됩니다. 문서를 파일에 저장하고 사용자 정의 프로세스를 개발하여 프린터로 보낼 수 있습니다.

<!-- ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that con tains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

 -->

### 배치 데이터를 처리하여 여러 문서 작성 {#processing-batch-data-to-create-multiple-documents}

문서 생성 API를 사용하여 XML 배치 데이터 소스 내의 각 레코드에 대해 별도의 문서를 만들 수 있습니다. 대량 및 비동기 모드로 문서를 생성할 수 있습니다. 변환에 대한 다양한 매개 변수를 구성한 다음 배치 프로세스를 시작할 수 있습니다.

![PDF 문서 만들기](assets/ou_OutputBatchMany_popup.png)

<!-- You can can also create a single document that contains all records (this functionality is the default).  Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents. -->

<!-- The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents. 

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use document generation APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document’s fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form. -->

## 문서 조작

통신 문서 조작 API를 사용하여 PDF 문서를 결합, 재정렬 및 확인할 수 있습니다. 일반적으로 DDX를 만들어 문서 조작 API에 제출하여 문서를 어셈블하거나 다시 배치합니다. 다음 [DDX 문서](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) 소스 문서를 사용하여 필수 문서 세트를 생성하는 방법에 대한 지침을 제공합니다. DDX 참조 설명서는 지원되는 모든 작업에 대한 자세한 정보를 제공합니다. 문서 조작의 몇 가지 예는 다음과 같습니다.

### PDF 문서를 어셈블합니다

문서 조작 API를 사용하여 두 개 이상의 PDF 또는 XDP 문서를 하나의 PDF 문서 또는 PDF Portfolio으로 어셈블할 수 있습니다. PDF 문서를 취합할 수 있는 몇 가지 방법은 다음과 같습니다.

* 간단한 PDF 문서 조합
* PDF Portfolio 만들기
* 암호화된 문서 조합
* Bates 번호를 사용하여 문서 조합
* 문서 평면화 및 조합

![여러 PDF 문서에서 간단한 PDF 문서 조립](assets/as_document_assembly.png)
그림: 여러 PDF 문서에서 간단한 PDF 문서 조립

### PDF 문서를 디스어셈블합니다

문서 조작 API를 사용하여 PDF 문서를 분해할 수 있습니다. API는 소스 문서에서 페이지를 추출하거나 책갈피를 기반으로 소스 문서를 나눌 수 있습니다. 일반적으로 이 작업은 PDF 문서가 원래 문 컬렉션과 같은 여러 개별 문서에서 만들어진 경우에 유용합니다.

* 소스 문서에서 페이지 추출
* 책갈피를 기준으로 소스 문서 나누기

![책갈피를 기반으로 하는 소스 문서를 여러 문서로 분할](assets/as_intro_pdfsfrombookmarks.png)
그림: 책갈피를 기반으로 하는 소스 문서를 여러 문서로 분할

### PDF/A호환 문서로 변환하고 확인합니다

문서 조작 API를 사용하여 PDF 문서를 PDF/A 호환 문서로 변환하고 PDF 문서가 PDF/A 규격 문서인지 확인할 수 있습니다. PDF/A는 문서 컨텐츠를 장기 보존하기 위한 보관 형식입니다. 글꼴은 문서 내에 포함되고 파일의 압축이 해제됩니다. 따라서 PDF/A 문서는 일반적으로 표준 PDF 문서보다 큽니다. 또한 PDF/문서에 오디오 및 비디오 컨텐츠가 포함되어 있지 않습니다.

## 문서 유틸리티

문서 유틸리티 동기 API는 PDF과 XDP 파일 형식 간에 문서를 변환하고 PDF 문서에 대한 정보를 쿼리하는 데 도움이 됩니다. 예를 들어 PDF 문서에 주석이나 첨부 파일이 포함되어 있는지 확인할 수 있습니다.

### PDF 문서 속성 검색

다음을 수행할 수 있습니다 [PDF 문서 쿼리](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/pdf-utility-sync/#tag/Document-Extraction/) 을 참조하십시오.

* PDF 문서입니다. 소스 문서가 PDF 문서인지 확인합니다.
* 입력 가능한 양식입니다. 소스 PDF 문서가 입력 가능한 양식인지 확인합니다.
* 양식 유형: 문서의 양식 유형을 검색합니다.
* 첨부 파일 확인: 소스 PDF 문서에 첨부 파일이 있는지 확인합니다.
* 주석 확인: 소스 PDF 문서에 검토 주석이 있는지 확인합니다.
* PDF 패키지입니다. 문서가 PDF 패키지인지 확인합니다.
* PDF 버전 가져오기: 검색 [PDF 문서 버전](https://en.wikipedia.org/wiki/History_of_PDF).
* 권장 Acrobat 버전: 필요한 버전의 Acrobat(Reader)을 검색하여 PDF 문서를 엽니다.
* XFA 문서입니다. 소스 PDF 문서가 XFA 기반 PDF 문서인지 확인합니다.
* 셸 PDF: 소스 PDF 문서가 셸 PDF인지 확인합니다. 셸 PDF은 XFA 스트림, 글꼴 및 이미지 리소스만 포함하고, 비어 있거나 Acrobat 또는 Adobe Reader을 사용하여 문서를 열어야 한다는 경고가 포함된 페이지를 하나 포함합니다. 셸 PDF은 PDFForm 변환의 전달만 최적화하기 위해 PDF 변환에 사용됩니다.
* XFA 버전 가져오기: 검색 [XFA 기반 PDF 문서에 대한 XFA 버전](https://en.wikipedia.org/wiki/XFA#XFA_versions).

### PDF 문서를 XDP 문서로 변환

다음 [XDP API에 PDF](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/pdf-utility-sync/#tag/Document-Conversion) PDF 문서를 XDP 파일로 변환합니다. PDF 문서를 XDP 파일로 성공적으로 변환하려면 사전에서 PDF 문서에 XFA 스트림을 포함해야 합니다.

## 통신 API 유형

통신은 주문형 및 배치 문서 생성을 위한 HTTP API를 제공합니다.

* **[동기 API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)** 은 온디맨드, 낮은 지연 및 단일 레코드 문서 생성 시나리오에 적합합니다. 이러한 API는 사용자 작업 기반 사용 사례에 더 적합합니다. 예를 들어, 사용자가 양식 작성을 완료한 후 문서를 생성합니다.

* **[배치 API(비동기 API)](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)** 는 스케줄 지정, 높은 처리량 및 여러 문서 생성 시나리오에 적합합니다. 이러한 API는 문서를 일괄로 생성합니다. 예를 들어, 매월 생성된 전화 요금 청구서, 신용 카드 명세서 및 혜택 명세서 등이 있습니다.

## 온보딩

통신 기능은 Forms as a Cloud Service 사용자를 위한 독립형 및 추가 기능 모듈로 제공됩니다. Adobe 영업 팀이나 Adobe 담당자에게 문의하여 액세스를 요청할 수 있습니다. Adobe는 조직에 대한 액세스 권한을 활성화하고 조직의 책임자로 지정된 사람에게 필요한 권한을 제공합니다. 관리자는 조직의 Forms as a Cloud Service 개발자(사용자)에게 API를 사용할 수 있는 액세스 권한을 부여할 수 있습니다.

온보딩 후 Forms as a Cloud Service 환경에 대한 통신 기능을 활성화하려면

1. Cloud Manager에 로그인하고 AEM Forms as a Cloud Service 인스턴스를 엽니다.

1. 프로그램 편집 옵션을 열고 솔루션 및 추가 기능 탭으로 이동한 다음 **[!UICONTROL Forms - 통신]** 선택 사항입니다.

   ![통신](assets/communications.png)

   이미 을(를) 활성화한 경우 **[!UICONTROL Forms - 디지털 등록]** 옵션을 선택한 다음 **[!UICONTROL Forms - 통신 추가 기능]** 선택 사항입니다.

   ![Addon](assets/add-on.png)

1. 클릭 **[!UICONTROL 업데이트]**.

1. 빌드 파이프라인을 실행합니다. 빌드 파이프라인이 성공하면 환경에 대해 Communications API가 활성화됩니다.

>[!NOTE]
>
> 문서 조작 API를 활성화하고 구성하려면 다음 규칙을 [Dispatcher 구성](setup-local-development-environment.md#forms-specific-rules-to-dispatcher):
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

<!--

Communication help you combine a template and XML data to generate print documents in various formats. The service allows you to generate documents in synchronous and batch modes. The APIs enables you to create applications that let you:

  * Generate documents by populating template files (PDF and XDP) with XML data.
  * Generate output forms in various formats, including non-interactive PDF print streams.

Consider a scenario where you have one or more templates and multiple records of XML data for each template. You can use Communications APIs to generate a print document for each record.  You can also combine the records into a single document.  The result is a non-interactive PDF document. A non-interactive PDF document does not let users enter data into its fields.

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as REST endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example ExpenseClaim.xdp). You can specify a fully qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document.  

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

You can use Communications APIs to create PostScript (PS), Printer Command Language (PCL), and Zebra Printing Language (ZPL) document that are based on a XDP form design or PDF document. The _generatePrintedOutput_ API merges a form design with form data to generate a document. You can save the document to a file and develop a custom process to send it to a printer.

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

You can use the Communications APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document’s fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form.  -->
