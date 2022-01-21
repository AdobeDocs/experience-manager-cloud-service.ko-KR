---
title: Forms as a Cloud Service Communications 소개
description: 데이터를 XDP 및 PDF 템플릿과 자동으로 병합하거나 PCL, ZPL 및 PostScript 형식으로 출력을 생성합니다
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: d136062ed0851b89f954e5485c2cfac64afeda2d
workflow-type: tm+mt
source-wordcount: '1869'
ht-degree: 1%

---

# AEM Forms as a Cloud Service 통신 사용 {#frequently-asked-questions}

**AEM Forms as a Cloud Service Communications 기능은 베타에 있습니다.**

커뮤니케이션 기능을 통해 비즈니스 서신, 명세서, 청구 처리 편지, 혜택 공지, 월별 청구서 또는 환영 키트와 같은 브랜드 중심, 개인화된 표준화된 문서를 작성할 수 있습니다.


요청 시 문서를 생성하거나 배치 작업을 생성하여 정의된 간격으로 여러 문서를 생성할 수 있습니다. 통신 API는 다음을 제공합니다.

* 온디맨드 및 배치 문서 생성 기능을 간소화합니다.

* 기존 시스템과 쉽게 통합할 수 있는 HTTP API입니다. 주문형(지연 시간) 및 배치 작업(높은 처리량 작업)에 대한 별도의 API가 포함됩니다. 문서 생성을 효율적으로 합니다.

* 데이터에 대한 보안 액세스. Communications API는 고객이 지정한 데이터 저장소에서만 데이터에 연결 및 액세스하고 로컬 데이터 복사본을 만들지 않으므로 Communications를 매우 안전하게 만듭니다.

![신용 카드 명세서 샘플](assets/statement.png)
Communications API를 사용하여 신용 카드 명세서를 만들 수 있습니다. 이 샘플 문은 동일한 템플릿을 사용하지만 신용 카드 사용에 따라 각 고객에 대해 데이터를 구분합니다.

## 어떻게 작동합니까?

커뮤니케이션 활용 [PDF 및 XFA 템플릿](#supported-document-types) with [XML 데이터](#form-data) 정의된 간격으로 배치 작업을 사용하여 단일 요청 문서 또는 여러 문서를 생성합니다.

통신 API는 템플릿(XFA 또는 PDF)을 고객 데이터([XML 데이터](#form-data)) PS, PCL, DPL, IPL 및 ZPL 포맷과 같은 PDF 및 인쇄 형식으로 문서를 생성할 수 있습니다.

일반적으로 [디자이너](use-forms-designer.md) 및 를 사용하여 데이터를 템플릿과 병합합니다. 애플리케이션이 출력 문서를 네트워크 프린터, 로컬 프린터 또는 스토리지 시스템으로 전송하여 아카이빙할 수 있습니다. 일반적인 기본 제공 및 사용자 지정 워크플로우는 다음과 같습니다.

![통신 워크플로우](assets/communicaions-workflow.png)

사용 사례에 따라 웹 사이트나 스토리지 서버를 통해 이러한 문서를 다운로드할 수 있도록 할 수도 있습니다.

## 통신 API

통신은 주문형 및 배치 문서 생성을 위한 HTTP API를 제공합니다.

* **[동기 API](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/)** 은 온디맨드, 낮은 지연 및 단일 레코드 문서 생성 시나리오에 적합합니다. 이러한 API는 사용자 작업 기반 사용 사례에 더 적합합니다. 예를 들어, 사용자가 양식 작성을 완료한 후 문서를 생성합니다.

* **[배치 API(비동기 API)](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/batch/)** 는 스케줄 지정, 높은 처리량 및 여러 문서 생성 시나리오에 적합합니다. 이러한 API는 문서를 일괄로 생성합니다. 예를 들어, 매월 생성된 전화 요금 청구서, 신용 카드 명세서 및 혜택 명세서 등이 있습니다.

## 온보딩

통신은 Forms as a Cloud Service 사용자를 위한 독립형 및 추가 기능 모듈로 제공됩니다. Adobe 영업 팀이나 Adobe 담당자에게 문의하여 액세스를 요청할 수 있습니다.

Adobe는 조직에 대한 액세스 권한을 활성화하고 조직의 책임자로 지정된 사람에게 필요한 권한을 제공합니다. 관리자는 API를 사용할 수 있도록 조직의 AEM Forms 개발자(사용자)에게 액세스 권한을 부여할 수 있습니다.

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

## 고려 사항 {#considerations-for-communications-apis}

Communication API를 사용하여 문서를 생성하기 전에 다음 고려 사항을 수행하십시오.

### 양식 데이터 {#form-data}

Communications API는 일반적으로 [디자이너](use-forms-designer.md) 및 XML 양식 데이터를 입력으로 추가할 수 있습니다. 문서를 데이터로 채우려면 채울 모든 양식 필드의 XML 양식 데이터에 XML 요소가 있어야 합니다. XML 요소 이름은 필드 이름과 일치해야 합니다. XML 요소가 양식 필드에 해당하지 않거나 XML 요소 이름이 필드 이름과 일치하지 않으면 XML 요소가 무시됩니다. XML 요소가 표시되는 순서와 일치하지 않아도 됩니다. 중요한 요소는 XML 요소가 해당 값과 함께 지정된다는 것입니다.

다음 예제 대출 신청 양식을 고려하십시오.

![대출 신청 양식](assets/loanFormData.png)

데이터를 이 양식 디자인에 병합하려면 양식 계층 구조, 필드 이름 지정 및 데이터 형식에 해당하는 XML 데이터 소스를 만듭니다. 다음 XML은 예제 모기지 응용 프로그램 양식에 해당하는 XML 데이터 원본을 나타냅니다.

```XML
* <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
* <xfa:data>
* <data>
    * <Layer>
        <closeDate>1/26/2007</closeDate>
        <lastName>Johnson</lastName>
        <firstName>Jerry</firstName>
        <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
        <city>New York</city>
        <zipCode>00501</zipCode>
        <state>NY</state>
        <dateBirth>26/08/1973</dateBirth>
        <middleInitials>D</middleInitials>
        <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
        <phoneNumber>5555550000</phoneNumber>
    </Layer>
    * <Mortgage>
        <mortgageAmount>295000.00</mortgageAmount>
        <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
        <purchasePrice>300000</purchasePrice>
        <downPayment>5000</downPayment>
        <term>25</term>
        <interestRate>5.00</interestRate>
    </Mortgage>
</data>
</xfa:data>
</xfa:datasets>
```

### 지원되는 문서 유형 {#supported-document-types}

Communications API의 렌더링 기능에 대한 전체 액세스 권한을 얻으려면 XDP 파일을 입력으로 사용하는 것이 좋습니다. 경우에 따라 PDF 파일을 사용할 수 있습니다. 그러나 PDF 파일을 입력으로 사용하면 다음과 같은 제한 사항이 있습니다.

XFA 스트림이 포함되지 않은 PDF 문서는 PostScript, PCL 또는 ZPL로 렌더링할 수 없습니다. Communications API는 XFA 스트림(즉,에서 만든 양식)으로 PDF 문서를 렌더링할 수 있습니다 [디자이너](use-forms-designer.md))을 레이저나 레이블 형식으로 지정합니다. PDF 문서에 서명, 인증 또는 사용 권한(AEM Forms Reader 확장 서비스를 사용하여 적용)이 있는 경우 이러한 인쇄 형식으로 렌더링할 수 없습니다.

<!-- Run-time options such as PDF version and tagged PDF are not supported for Acrobat forms. They are valid for PDF forms that contain XFA streams; however, these forms cannot be signed or certified. 

### Email support {#email-support}

For email functionality, you can create a process in Experience Manager Workflows that uses the Email Step. A workflow represents a business process that you are automating. -->

### 인쇄 가능 영역 {#printable-areas}

기본 0.25인치 인쇄 불가 여백은 레이블 프린터에는 정확하지 않으며 프린터마다, 레이블 크기에서 레이블 크기로 달라지지만 0.25인치 여백을 유지하거나 줄이는 것이 좋습니다. 그러나 인쇄되지 않는 여백은 증가시키지 않는 것이 좋습니다. 그렇지 않으면 인쇄 가능 영역의 정보가 제대로 인쇄되지 않습니다.

항상 프린터에 올바른 XDC 파일을 사용해야 합니다. 예를 들어, 300dpi 프린터의 XDC 파일을 선택하고 문서를 200dpi 프린터로 보내지 마십시오.

### XFA 양식에 대한 스크립트(XDP/PDF)만 해당 {#scripts}

Communications API와 함께 사용되는 양식 디자인에는 서버에서 실행되는 스크립트가 포함될 수 있습니다. 양식 디자인에는 클라이언트에서 실행되는 스크립트가 포함되어 있지 않아야 합니다. 양식 디자인 스크립트 만들기에 대한 내용은 [디자이너 도움말](use-forms-designer.md).

<!-- #### Working with Fonts
 Document Considerations for Working with Fonts>> -->

### 글꼴 매핑 {#font-mapping}

프린터 상주 글꼴을 사용하는 양식을 디자인하려면 프린터에서 사용할 수 있는 글꼴과 일치하는 서체 이름을 디자이너에서 선택합니다. PCL 또는 PostScript에 대해 지원되는 글꼴 목록은 해당 장치 프로필(XDC 파일)에 있습니다. 또는 다른 서체 이름의 프린터 상주 글꼴에 인쇄자가 아닌 글꼴을 매핑하기 위해 글꼴 매핑을 만들 수 있습니다. 예를 들어, PostScript 시나리오에서 Arial® 글꼴에 대한 참조를 프린터에 상주하는 Helvetica® 서식에 매핑할 수 있습니다.

클라이언트 컴퓨터에 글꼴이 설치되어 있으면 디자이너의 드롭다운 목록에서 사용할 수 있습니다. 글꼴이 설치되어 있지 않으면 글꼴 이름을 수동으로 지정해야 합니다. 디자이너의 &quot;사용할 수 없는 글꼴을 영구적으로 바꾸기&quot; 옵션은 해제할 수 있습니다. 그렇지 않으면 XDP 파일이 디자이너에 저장되면 대체 글꼴 이름이 XDP 파일에 기록됩니다. 프린터 상주 글꼴이 사용되지 않음을 의미합니다.

두 가지 유형의 OpenType® 글꼴이 있습니다. 한 유형은 PCL에서 지원하는 TrueType OpenType® 글꼴입니다. 다른 하나는 CFF OpenType®. PDF 및 PostScript 출력은 포함된 Type-1, TrueType 및 OpenType® 글꼴을 지원합니다. PCL 출력은 포함된 TrueType 글꼴을 지원합니다.

Type-1 및 OpenType® 글꼴은 PCL 출력에 포함되지 않습니다. Type-1 및 OpenType® 글꼴로 서식이 지정된 컨텐츠는 래스터화되어 생성되는 속도가 점점 느려질 수 있는 비트맵 이미지로 생성됩니다.

다운로드되거나 포함된 글꼴은 PostScript, PCL 또는 PDF 출력을 생성할 때 자동으로 대체됩니다. 즉, 생성된 문서를 올바르게 렌더링하는 데 필요한 글꼴 글리프의 하위 집합만 생성된 출력에 포함됩니다.

### 장치 프로필 파일 작업(XDC 파일) {#working-with-xdc-files}

장치 프로필(XDC 파일)은 XML 형식의 프린터 설명 파일입니다. 이 파일을 사용하면 Communications API에서 문서를 레이저 또는 레이블 프린터 형식으로 출력할 수 있습니다. Communications API는 다음을 포함한 XDC 파일을 사용합니다.

* hppcl5c.xdc

* hppcl5e.xdc

* ps_plain_level3.xdc

* ps_plain.xdc

* zpl300.xdc

* zpl600.xdc

* zpl300.xdc

* ipl300.xdc

* ipl400.xdc

* tpcl600.xdc

* dpl300.xdc

* dpl406.xdc

* dpl600.xdc

제공된 XDC 파일을 사용하여 인쇄 문서를 생성하거나 필요에 따라 수정할 수 있습니다.
<!-- It is not necessary to modify these files to create documents. However, you can modify them to meet your business requirements. -->

이러한 파일은 상주 글꼴, 종이 트레이, 스테이플러와 같은 특정 프린터의 기능을 지원하는 XDC 파일을 참조합니다. 이러한 참조의 목적은 장치 프로필을 사용하여 고유한 프린터를 설정하는 방법을 이해하는 데 도움이 됩니다. 또한 참조는 동일한 제품 라인에서 유사한 프린터의 시작점입니다.

### XCI 구성 파일 작업 {#working-with-xci-files}

Communications API는 XCI 구성 파일을 사용하여 출력이 단일 패널인지 페이지 매김인지를 제어하는 등의 작업을 수행합니다. 이 파일에는 설정할 수 있는 설정이 포함되어 있지만 이 값을 수정하는 것은 일반적이지 않습니다. <!-- The default.xci file is located in the svcdata\XMLFormService folder. -->

Communications API를 사용하는 동안 수정된 XCI 파일을 전달할 수 있습니다. 이 작업을 수행할 때 기본 파일의 복사본을 만들고 비즈니스 요구 사항을 충족하도록 수정해야 하는 값만 변경하고 수정된 XCI 파일을 사용하십시오.

통신 API는 기본 XCI 파일(또는 수정된 파일)로 시작합니다. 그런 다음 통신 API를 사용하여 지정된 값을 적용합니다. 이러한 값은 XCI 설정을 덮어씁니다.

다음 표에서는 XCI 옵션을 지정합니다.

| XCI 옵션 | 설명 |
| ------------------------------------| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| config/present/pdf/creator | 문서 정보 사전의 작성자 항목을 사용하여 문서 작성자를 식별합니다. 이 사전에 대한 자세한 내용은 PDF 참조 안내서를 참조하십시오. |
| config/present/pdf/producer | 문서 정보 사전의 생성자 항목을 사용하여 문서 생성자를 식별합니다. 이 사전에 대한 자세한 내용은 PDF 참조 안내서를 참조하십시오. |
| 구성/현재/레이아웃 | 출력이 단일 패널인지 페이지로 매기는지 여부를 제어합니다. |
| config/present/pdf/compression/level | PDF 문서를 생성할 때 사용할 압축 정도를 지정합니다. |
| config/present/pdf/scriptModel | 출력 PDF 문서에 XFA 관련 정보를 포함할지 여부를 제어합니다. |
| config/present/common/data/adjustData | 병합 후 XFA 응용 프로그램이 데이터를 조정하는지 여부를 제어합니다. |
| config/present/pdf/renderPolicy | 페이지 컨텐츠 생성을 서버에서 수행할지 또는 클라이언트에게 연기할지 여부를 제어합니다. |
| config/present/common/locale | 출력 문서에 사용되는 기본 로케일을 지정합니다. |
| config/present/destination | 현재 요소에 포함되는 경우 출력 형식을 지정합니다. openAction 요소에 포함된 경우, 대화형 클라이언트에서 문서를 열 때 수행할 작업을 지정합니다. |
| config/present/output/type | 파일에 적용할 압축 유형 또는 생성할 출력 유형을 지정합니다. |
| config/present/common/temp/uri | 양식 URI를 지정합니다. |
| config/present/common/template/base | 양식 디자인에서 URI의 기본 위치를 제공합니다. 이 요소가 없거나 비어 있으면 양식 디자인의 위치가 기본으로 사용됩니다. |
| config/present/common/log/to | 로그 데이터 또는 출력 데이터가 기록되는 위치를 제어합니다. |
| config/present/output/to | 로그 데이터 또는 출력 데이터가 기록되는 위치를 제어합니다. |
| config/present/script/currentPage | 문서를 열 때의 초기 페이지를 지정합니다. |
| 구성/현재/스크립트/제외 | 무시할 이벤트를 AEM Forms 서버/통신 API에 알려줍니다. |
| config/present/pdf/linear | 출력 PDF 문서의 선형화 여부를 제어합니다. |
| config/present/script/runScripts | AEM Forms이 실행하는 스크립트 집합을 제어합니다. |
| config/present/pdf/tagged | 출력 PDF 문서에 태그 포함을 제어합니다. PDF 컨텍스트에서 태그는 문서의 논리적 구조를 노출하기 위해 문서에 포함된 추가 정보입니다. 태그는 접근성 보조 및 서식 변경을 지원합니다. 예를 들어, 페이지 번호에 아티팩트로 태그를 지정하여 화면 판독기에서 텍스트 중간에 이를 발음하지 않도록 할 수 있습니다. 태그는 문서를 더 유용하게 만들 수 있지만 문서 크기와 문서 작성 시간을 늘립니다. |
| config/present/pdf/version | 생성할 PDF 문서의 버전을 지정합니다. |
