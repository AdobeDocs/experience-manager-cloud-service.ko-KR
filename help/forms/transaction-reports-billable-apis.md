---
title: 거래 보고서 청구 가능 API
description: 트랜잭션으로 계산되는 모든 API 목록
feature: Adaptive Forms, Foundation Components
hide: true
hidefromtoc: true
source-git-commit: a1a87a27d73d7472ec02de37621123bbdd3876b4
workflow-type: tm+mt
source-wordcount: '1334'
ht-degree: 4%

---

# 거래 보고서 청구 가능 API {#transaction-reports-billable-apis}

AEM Forms은 양식 제출, 문서 처리 및 문서 렌더링에 필요한 여러 API를 제공합니다. 일부 API는 트랜잭션으로 계산되며 다른 API는 무료로 사용할 수 있습니다. 이 문서에서는 거래 보고서에서 거래로 간주되는 모든 API 목록을 제공합니다. 다음은 청구 가능한 API가 사용되는 몇 가지 일반적인 시나리오입니다.

* 적응형 양식 제출
* 한 형식에서 다른 형식으로 문서 변환
* 동적 PDF 문서 펼치기
* 기록 문서 생성(Forms 서비스 또는 출력 서비스 사용)
* 대화형 PDF 문서를 다른 PDF 문서와 병합
* AEM Workflow의 작업 할당 단계 및 통신 API 단계 사용

과금 API는 페이지 수, 문서 또는 양식의 길이 또는 렌더링된 문서의 최종 포맷을 고려하지 않습니다. 트랜잭션 보고서는 트랜잭션을 Forms 제출됨 및 렌더링된 문서, 이렇게 두 가지 범주로 나눕니다.

* **Forms 제출됨:** AEM Forms으로 만든 모든 유형의 양식에서 데이터를 제출하고 데이터를 데이터 저장소 또는 데이터베이스로 제출한 경우 양식 제출로 간주됩니다. 예를 들어 적응형 양식 또는 양식 세트를 제출하면 제출된 양식으로 간주됩니다. 양식 세트에 5개의 양식이 있는 경우 양식 세트가 제출되면 거래 보고 서비스는 5개의 제출로 계산합니다.

* **렌더링된 문서:** 템플릿과 데이터를 결합하여 문서를 생성하거나, 문서에 디지털 서명 또는 인증을 하거나, 문서 서비스를 위해 청구 가능한 문서 서비스 API를 사용하거나, 문서를 한 형식에서 다른 형식으로 변환하면 문서가 렌더링되는 것으로 간주됩니다.

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_submission_graph_en"
>title="양식 제출 추적기"
>abstract="전체 수에 대한 통합 보기를 사용하여 간편하게 양식 제출을 추적하거나 인스턴스별 세부 정보를 살펴볼 수 있습니다. 직관적인 막대 그래프를 사용하여 트렌드를 식별하고 인스턴스를 비교하며 정보에 입각한 결정을 한눈에 내릴 수 있습니다."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_conversions_graph_en"
>title="양식 전환 추적기"
>abstract="총 카운트 요약을 통해 양식 전환을 간편하게 탭하거나 각 AEM Forms 인스턴스에 대한 세부 정보를 살펴볼 수 있습니다. 읽기 쉬운 막대 그래프는 트렌드를 파악하고, 인스턴스를 비교하고, 정보에 기반한 결정을 내리는 데 도움이 됩니다."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formCreationAvgDuration_graph_en"
>title="평균 양식 생성 기간"
>abstract="그래프는 양식을 만드는 데 걸린 평균 시간을 보여 줍니다. 그래프의 각 막대는 특정 양식을 나타내고 막대의 높이는 해당 기간 동안 양식을 만드는 데 걸린 평균 기간을 나타냅니다. 이 그래프를 분석하면 사용자가 다양한 기간 동안 또는 다른 컨텍스트 내에서 양식 작성의 효율성과 속도를 이해함으로써 잠재적인 개선 사항에 대한 통찰력을 얻을 수 있습니다."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formPublishAvgDuration_en"
>title="평균 양식 작성 기간"
>abstract="그래프는 편집하기 위해 양식을 연 첫 날부터 측정한 양식을 만들고 게시하는 데 걸린 평균 시간을 표시합니다. 각 막대는 양식의 특정 기간에 해당하며, 막대 높이는 양식 개발 시작부터 최종 및 게시까지 걸린 평균 시간을 나타냅니다."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_newForms_graph_en"
>title="새로운 Forms 추적기"
>abstract="그래프는 특정 기간 동안 새로 생성된 양식의 수 또는 빈도에 대한 정보를 제공합니다. 그래프의 각 막대는 일, 주 또는 월과 같은 고유한 측정 단위를 나타냅니다. 각 막대의 높이는 해당 특정 간격 동안 새로 만든 양식의 수량이나 빈도를 나타냅니다."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_publishedForms_graph_en"
>title="Forms 추적기 게시됨"
>abstract="그래프는 특정 기간 동안 성공적으로 게시된 양식의 수 또는 빈도에 대한 정보를 제공합니다. 이를 통해 시간에 따른 양식 게시의 트렌드, 패턴 또는 변형을 이해하고, 생산성을 모니터링하거나, 최대 게시 기간을 식별하거나, 양식 게시 프로세스의 변경 성공 여부를 평가할 수 있습니다."

<!-- 
>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formFragments_graph_en"
>title="Form Fragments Tracker"
>abstract="This graph helps you see how many form fragments people use in their forms. It gives you a sense of how popular or common these reusable parts are in form building."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_avgFormPerFragments_graph_en"
>title="Average Duration for Form Fragments Creation"
>abstract= "The graph displays the average time taken to create a form fragment, measured from the initial day the form fragment was opened for editing. Each bar corresponds to a specific time frame for a form fragment, with the bar height indicating the average time taken from the start of form fragment development to its finalization and publication."


<!-- 

>[!NOTE]
>
>Transaction Reports UI displays three categories: Forms Submitted, Documents Rendered, and Documents Processed. Both Documents Rendered and Documents Processed are accounted as Documents Rendered.
-->


<!--

## Billable Document Services APIs {#billable-document-services-apis}

### Generate PDF Service {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Creates PDF from HTML pages.</p> </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimizes PDF to reduce file size by stripping unnecessary metadata without affecting the quality.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->


<!--
### Distiller Service {#distiller-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

## 청구 가능 문서 서비스 API {#billable-document-services-apis}

### PDF 서비스 생성 {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>설명</td>
   <td>거래 보고서 범주</td>
   <td>추가 정보</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#section/Before-you-start" target="_blank">createPDF</a></td>
   <td>템플릿에서 PDF 문서를 생성하고 데이터를 템플릿으로 병합합니다.</td>
   <td>처리된 문서</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePrintedOutput/post" target="_blank">exportPDF</a></td>
   <td>XDP 파일 또는 PDF 문서를 지원되는 파일 형식으로 변환합니다.</td>
   <td>처리된 문서</td>
   <td> </td>
  </tr>
  <!--<tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Creates PDF from HTML pages.</p> </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimizes PDF to reduce file size by stripping unnecessary metadata without affecting the quality.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>-->
 </tbody>
</table>

### 출력 서비스 {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>설명</td>
   <td>거래 보고서 범주</td>
   <td>추가 정보</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PDFOutput" target="_blank">generatePDFOutput</a></td>
   <td>데이터와 템플릿을 병합하여 PDF 문서를 만듭니다.</td>
   <td>처리된 문서</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PDFOutputOptions" target="_blank">generatePDFOutput(PDFOutputOptions)</a></td>
   <td>데이터와 템플릿을 병합하여 PDF 문서를 만듭니다.</td>
   <td>처리된 문서</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig" target="_blank">generatePDFOutputBatch</a></td>
   <td>데이터와 템플릿을 병합하여 PDF 문서 세트를 만듭니다.</td>
   <td>처리된 문서</td>
   <td> <!-- The generatePDFOutputBatch API combines a form template with a record and generates a PDF. When you process a batch of records, the transaction reporting service counts each record as a separate PDF rendition. <br> You can use the <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> flag to combine multiple renditions to single PDF file. Irrespective of the status of flag, the service counts each record as a separate PDF rendition. --> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutput" target="_blank">generatePrintedOutput</a></td>
   <td>XDP 및 PDF 문서를 PS(PostScript), PCL(Printer Command Language) 및 ZPL 파일 형식으로 변환합니다. </td>
   <td>처리된 문서</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutputOptions" target="_blank">generatePrintedOutput(PrintedOutputOptions)</a></td>
   <td>XDP 및 PDF 문서를 PS(PostScript), PCL(Printer Command Language) 및 ZPL 파일 형식으로 변환합니다. </td>
   <td>처리된 문서</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig" target="_blank">generatePrintedOutputBatch</a></td>
   <td>XDP 및 PDF 문서 집합을 PostScript(PS), 프린터 명령 언어(PCL) 및 ZPL 파일 형식 집합으로 변환합니다. </td>
   <td>처리된 문서</td>
   <td> <!-- The generatePDFOutputBatch API combines a form template with a record and generates a PDF. When you process a batch of records, the transaction reporting service counts each record as a separate PDF rendition. <br> You can use the <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> flag to combine multiple renditions to single PDF file. Irrespective of the status of flag, the service counts each record as a separate PDF rendition. --> </td>
  </tr>
 </tbody>
</table>

### DocAssurance 서비스 {#DocAssurance-Service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>설명</td>
   <td>거래 보고서 범주</td>
   <td>추가 정보</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/docassurance/#tag/DocAssurance" target="_blank">secureDocument</a><br /> </td>
   <td>이 API를 사용하면 문서의 보안을 유지할 수 있습니다. API를 사용하여 PDF 문서에 서명, 인증, 리더 확장 또는 암호화할 수 있습니다.</td>
   <td>처리된 문서</td>
   <td>secureDocument의 서명 및 인증 작업만 청구됩니다.</td>
  </tr>
 </tbody>
</table>

### 기록 문서(DOR) 서비스 {#document-of-record-dor-forms-service-and-output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>설명</td>
   <td>거래 보고서 범주</td>
   <td>추가 정보</td>
  </tr>
  <tr>
   <td><a href="https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Generate-DoR/operation/generateDoR" target="_blank">렌더링</a></td>
   <td>지정된 렌더링 메서드를 호출하여 제공된 매개 변수를 사용하여 기록 문서를 생성합니다.</td>
   <td>Forms 서비스를 사용하여 처리된 문서</td>
   <td> </td>
  </tr>
  <!--<tr>
   <td><a href="" target="_blank">render</a></td>
   <td>Invokes the specified render method to generate a document of record using provided parameters.</td>
   <td>Documents Processed using Output Service</td>
   <td> </td>
  </tr>-->
 </tbody>
</table>

<!--

### Forms Service {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Renders PDF Form from XDP templates. The XP templates are created in Forms Designer.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Extracts data from a PDF Form or XDP templates</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

<!--
### Convert PDF Service {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td>
   <td>Converts a PDF document to a list of image documents. Supported image formats are JPEG, JPEG2K, PNG, and TIFF.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toPS</a></td>
   <td>Converts a Flat PDF file to PostScript format using the options specified in the option spec.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

<!--
### Barcoded Forms Service {#barcoded-forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td>
   <td>Decodes all the barcodes in a Document object and returns an org.w3c.dom.Document object that contains data that was retrieved from the barcode.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

### 어셈블러 서비스 {#assembler-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>설명</td>
   <td>거래 보고서 범주</td>
   <td>추가 정보</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/DDX-execution/operation/InvokeDDX">호출</a></td>
   <td>지정된 입력 문서에 대해 DDX를 실행하고 결과 문서가 포함된 개체를 반환합니다.</td>
   <td>처리된 문서</td>
   <td>다음 작업은 트랜잭션으로 계상되지 않습니다.
    <ul>
     <li>패키지 또는 포트폴리오 만들기</li>
     <li>여러 XDP 결합 </li>
    </ul> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/DDX-execution/operation/InvokeDDX" target="_blank">호출</a></td>
   <td>지정된 입력 문서에 대해 DDX를 실행하고 결과 문서가 포함된 개체를 반환합니다.</td>
   <td>처리된 문서</td>
   <td>PDF Generator, Forms 및 출력 서비스에서 지원하는 모든 입력 파일 형식이며 어셈블러 서비스에서는 이러한 모든 형식을 출력 파일 형식으로 지원합니다. </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA">toPDFA</a></td>
   <td>지정된 옵션을 사용하여 지정된 문서를 PDF/A로 변환합니다.</td>
   <td>처리된 문서</td>
   <td> </td>
  </tr>
 </tbody>
</table>

다음 작업 중 하나 이상을 수행하면 API 호출의 사용이 트랜잭션으로 계산됩니다.

1. PDF 형식이 아닌 형식에서 PDF 형식으로 변환. <!--For instance, the conversion from XDP format to PDF format, catering to both interactive and non-interactive forms of communication, and the conversion from Word to PDF.-->
1. PDF 형식에서 PDF/A 형식으로 변환.
1. PDF 형식에서 PDF 형식이 아닌 형식으로 변환. 예제에서는 PDF 형식에서 이미지 형식으로 변환하거나 PDF 형식에서 텍스트 형식으로 변환할 수 있습니다.


>[!NOTE]
>
>* 어셈블러 서비스의 호출 API는 입력에 따라 다른 서비스의 과금 가능한 API를 내부적으로 호출할 수 있습니다. 따라서 호출 API는 없음, 단일 또는 여러 트랜잭션으로 간주할 수 있습니다. 계산되는 트랜잭션 수는 입력 및 호출된 내부 API에 따라 다릅니다.
>* 어셈블러 서비스를 사용하여 생성된 단일 PDF 문서는 없음, 단일 또는 다중 트랜잭션으로 계상될 수 있습니다. 계산되는 거래 수는 제공된 코드에 따라 다릅니다.
>

<!--
### PDF Utility Service  {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td>
   <td>Converts a PDF document into an XDP file. In order for a PDF document to be successfully converted to an XDP file, the PDF document must contain an XFA stream in the AcroForm dictionary.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

## 청구 가능 데이터 캡처 API {#billable-data-capture-apis}

적응형 양식의 모든 제출 이벤트는 거래로 계산됩니다. 기본적으로 PDF 양식 제출은 거래로 간주되지 않습니다. 제공된 를 사용하십시오 [트랜잭션 레코더 API](record-transaction-custom-implementation.md) PDF forms 제출을 거래로 기록하려면 다음과 같이 하십시오.

### 적응형 양식 {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>사용 사례</p> </td>
   <td>설명</td>
   <td>거래 보고서 범주</td>
   <td>추가 정보</td>
  </tr>
  <tr>
   <td>적응형 양식 제출</td>
   <td>구성된 제출 액션에 적응형 양식을 제출합니다. </td>
   <td>제출된 양식</td>
   <td>
    <ul>
     <li>성공한 제출은 단일 또는 두 개의 트랜잭션을 처리합니다. 계산되는 거래 수는 실행에 사용되는 실행 작업 유형에 따라 달라집니다. 예를 들어 이메일 제출 액션을 통해 PDF을 전송하는 것은 두 가지 트랜잭션 수에 해당합니다. 양식 제출을 위한 트랜잭션과 DOR(기록 문서) 서비스를 사용하여 생성된 PDF을 위한 트랜잭션. </li>
     <li>적응형 양식(적응형 양식 세트) 내에서 적응형 양식을 사용하면 단일 트랜잭션만 계산됩니다. 적응형 양식 내에 여러 적응형 양식을 보유할 수 있습니다.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

<!--

### HTML5 Forms {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Use Case</p> </td>
   <td>Description </td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an HTML5 Form</td>
   <td>Submits an HTML5 Form to submit URL configured in the form.</td>
   <td>Forms Submitted</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Form set {#form-set}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting a form set</td>
   <td>Submits form set to the submit URL configured in the form set.</td>
   <td>Forms Submitted</td>
   <td>
    <ul>
     <li>Using the adaptive form within an adaptive form (Adaptive form formset) accounts only single transaction. You can have any number of adaptive forms within an adaptive form.</li>
     <li>Every form in an HTML5 Forms form set accounts as a separate transaction. </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

-->

## 청구 가능 양식 중심 AEM 워크플로 {#billable--form-centric-aem-workflows}

양식 중심 AEM 워크플로의 작업 및 문서 서비스 단계는 트랜잭션으로 계상됩니다. 워크플로우 단계에서 트랜잭션을 처리하지만 워크플로우가 완료되지 않으면 트랜잭션 수가 취소되지 않습니다.

<!--
Assign task and document services steps of Form-centric AEM Workflows on OSGi and all the renditions of interactive communication and are accounted as transactions. Previewing an interactive communication on the author instance and previewing on the publish instance using Agent UI are not accounted as transactions. If a workflow step accounts a transaction and the workflow fails to complete, the transaction count is not reversed.
-->


<!--

### Interactive Communication - Web Channel {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Rendering a web channel</td>
   <td>Opens the web version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interactive Communication - Print Channel {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (convert to PDF)</td>
   <td>Generates the PDF version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

-->

### 양식 중심의 AEM 워크플로 {#form-centric-aem-workflows}

<table>
 <tbody>
  <tr>
   <td><p>사용 사례</p> </td>
   <td>거래 보고서 범주</td>
   <td>추가 정보</td>
  </tr>
  <tr>
   <td>작업 할당 단계 제출</td>
   <td>제출된 양식</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>워크플로우 응용 프로그램 시작 지점 제출 </td>
   <td>제출된 양식</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## 사용자 지정 코드에 대한 트랜잭션으로 청구 가능 API 기록 {#recording-billable-apis-as-transactions-for-custom-code}

PDF 양식 제출, 에이전트 UI를 사용하여 대화형 통신 미리 보기, 비표준 양식 제출 및 사용자 지정 구현과 같은 작업은 트랜잭션으로 계산되지 않습니다. AEM Forms은 트랜잭션과 같은 작업을 기록하는 API를 제공합니다. 사용자 지정 구현에서 API를 호출하여 [거래 기록](/help/forms/record-transaction-custom-implementation.md).

## 관련 문서 {#related-articles}

* [사용자 지정 구현에 대한 트랜잭션 기록](/help/forms/record-transaction-custom-implementation.md)
