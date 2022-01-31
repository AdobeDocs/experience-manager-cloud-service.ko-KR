---
title: AEM Forms as a Cloud Service - 통신
description: 데이터를 XDP 및 PDF 템플릿과 자동으로 병합하거나 PCL, ZPL 및 PostScript 형식으로 출력을 생성합니다
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: ed46b0be25dabcea69be29e54000a4eab55e2836
workflow-type: tm+mt
source-wordcount: '2250'
ht-degree: 0%

---


# AEM Forms as a Cloud Service Communications API 사용 {#frequently-asked-questions}

**통신 기능은 베타에 있습니다.**

Communications API를 사용하면 XDP 템플릿, XDP 기반 PDF 문서 및 Acrobat Forms(AcroForm)를 XML 데이터와 결합하여 다양한 형식으로 인쇄 문서를 생성하고 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.

- XML 데이터로 템플릿 파일을 채워 문서를 생성합니다.

- 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 양식을 생성합니다.

- XFA 양식 PDF에서 인쇄 PDF를 생성합니다.

- 여러 데이터 세트를 소스 템플릿에 병합하여 PDF, PostScript, PCL 및 ZPL 문서를 일괄적으로 생성합니다.

각 템플릿에 대해 하나 이상의 템플릿과 여러 개의 XML 데이터 레코드가 있는 시나리오를 생각해 보십시오. Communications API를 사용하여 각 레코드에 대한 인쇄 문서를 생성할 수 있습니다. <!-- You can also combine the records into a single document. --> 그 결과는 비대화형 PDF 문서입니다. 비대화형 PDF 문서에서는 사용자가 해당 필드에 데이터를 입력할 수 없습니다.

다음 [API 참조 설명서](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:b1223732-ae0f-4921-bdc0-c31e48b56044) 는 API에서 제공하는 모든 API, 매개 변수, 인증 방법 및 다양한 서비스에 대한 자세한 정보를 제공합니다. API 참조 설명서는 .yaml 형식으로도 사용할 수 있습니다. .yaml을 다운로드할 수 있습니다 [배치 API](assets/batch-api.yaml) 또는 [비 배치 API.yaml](assets/non-batch-api.yaml) 파일을 업로드하고 postman에 업로드하여 API의 기능을 확인합니다.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

Communication API .yaml 파일을 postman에 업로드하여 API의 기능을 확인합니다.

>[!NOTE]
>
>forms-users 그룹의 구성원만 Communications API에 액세스할 수 있습니다.

## 통신 활성화

Forms as a Cloud Service 환경에 대한 통신을 활성화하려면

1. Cloud Manager에 로그인하고 AEM Forms as a Cloud Service 인스턴스를 엽니다.

1. 프로그램 편집 옵션을 열고 솔루션 및 추가 기능 탭으로 이동한 다음 **[!UICONTROL Forms - 통신]** 선택 사항입니다.

   <!-- ![Communications](assets\communications.png)

    If you have already enabled the **[!UICONTROL Forms - Digital Enrollment]** option, then select the **[!UICONTROL Forms - Communications Add-On]** option.  

    <!-- ![Addon](assets\add-on.png) -->

1. 클릭 **[!UICONTROL 업데이트]**.

1. 빌드 파이프라인을 실행합니다.

빌드 파이프라인이 성공하면 환경에 대해 Communication API가 활성화됩니다.

## 통신 API 사용 {#workflows}

일반적으로 [디자이너](use-forms-designer.md) 및 는 통신 API를 사용하여 다음을 수행할 수 있습니다.

- 이러한 템플릿을 PDF, PostScript, ZPL 및 PCL을 포함한 다양한 형식으로 변환합니다.
- XML 양식 데이터를 양식 디자인과 병합하여 문서를 생성합니다.
- XML 양식 데이터를 문서에 병합하지 않고 문서를 생성합니다. 그러나 기본 워크플로우는 데이터를 문서에 병합하는 것입니다.

그러면 출력 문서가 파일에 저장됩니다. 사용자 정의 워크플로우를 설계하여 파일을 네트워크 프린터, 로컬 프린터 또는 보관을 위한 스토리지 시스템으로 보낼 수 있습니다. 일반적인 기본 제공 및 사용자 지정 워크플로우는 다음과 같습니다.

![통신 워크플로우](assets/communicaions-workflow.png)

### PDF 문서 만들기 {#create-pdf-documents}

를 사용할 수 있습니다 _generatePDFOutput_ 양식 디자인 및 XML 양식 데이터를 기반으로 하는 PDF 문서를 만들기 위한 API입니다. 출력은 비대화형 PDF 문서입니다. 즉, 사용자는 양식 데이터를 입력하거나 수정할 수 없습니다. 기본 워크플로우는 XML 양식 데이터를 양식 디자인과 병합하여 PDF 문서를 만드는 것입니다. 다음 그림은 양식 디자인과 XML 양식 데이터를 병합하여 PDF 문서를 생성하는 방법을 보여 줍니다.

![PDF 문서 만들기](assets/outPutPDF_popup.png)

### PostScript(PS), 프린터 명령 언어(PCL), Zebra Printing Language(ZPL) 문서 작성 {#create-PS-PCL-ZPL-documents}

Communications API를 사용하여 XDP 양식 디자인 또는 PDF 문서를 기반으로 하는 PS(PostScript), PCL(프린터 명령 언어) 및 ZPL(Zebra Printing Language) 문서를 만들 수 있습니다. 다음 _generatePrintedOutput_ API는 양식 디자인을 양식 데이터와 병합하여 문서를 생성합니다. 문서를 파일에 저장하고 사용자 정의 프로세스를 개발하여 프린터로 보낼 수 있습니다.

<!-- ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that contains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

 -->

### 배치 데이터를 처리하여 여러 문서 작성 {#processing-batch-data-to-create-multiple-documents}

XML 배치 데이터 소스 내에서 각 레코드에 대해 별도의 문서를 만들 수 있습니다. 대량 및 비동기 모드로 문서를 생성할 수 있습니다. 변환에 대한 다양한 매개 변수를 구성한 다음 배치 프로세스를 시작할 수 있습니다. <!-- You can can also create a single document that contains all records (this functionality is the default).  Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents. -->

<!-- The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents. -->

### 대화형 PDF 문서 병합 {#flatten-interactive-pdf-documents}

Communications API를 사용하여 대화형 PDF 문서(예: 양식)를 비대화형 PDF 문서로 변환할 수 있습니다. 대화형 PDF 문서를 사용하면 PDF 문서 필드에 있는 데이터를 입력하거나 수정할 수 있습니다. 대화형 PDF 문서를 비대화형 PDF 문서로 변환하는 프로세스를 병합이라고 합니다. PDF 문서를 평면화하면 사용자는 문서 필드에 있는 데이터를 수정할 수 없습니다. PDF 문서를 평면화하는 한 가지 이유는 데이터를 수정할 수 없도록 하기 위한 것입니다.

다음 유형의 PDF 문서를 평면화할 수 있습니다.

- Designer에서 작성된 대화형 PDF 문서(XFA 스트림을 포함함).

- Acrobat PDF forms

비대화형 PDF 문서를 병합하려고 하면 예외가 발생합니다.

### 양식 상태 유지 {#retain-form-state}

대화형 PDF 문서에는 양식을 구성하는 다양한 요소가 포함되어 있습니다. 이러한 요소에는 필드(데이터를 허용하거나 표시하기 위한), 단추(이벤트를 트리거하기 위한) 및 스크립트(특정 작업을 수행하는 명령)가 포함될 수 있습니다. 버튼을 클릭하면 필드의 상태를 변경하는 이벤트가 트리거될 수 있습니다. 예를 들어, 성별 옵션을 선택하면 필드의 색상 또는 양식의 모양이 변경될 수 있습니다. 양식 상태가 변경되는 수동 이벤트의 예입니다.

그러한 대화형 PDF 문서를 Communications API를 사용하여 병합하면 양식의 상태가 유지되지 않습니다. 양식을 평면화한 후에도 양식의 상태가 유지되도록 하려면 부울 값을 설정합니다 _keepFormState_ 를 입력하여 양식의 상태를 저장하고 유지할 수 있습니다.

### 통신 API에 대한 고려 사항 {#considerations-for-communications-apis}

#### 양식 데이터 {#form-data}

Communications API는 일반적으로 디자이너에서 만든 양식 디자인과 XML 양식 데이터를 입력으로 모두 허용합니다. 문서를 데이터로 채우려면 채울 모든 양식 필드의 XML 양식 데이터에 XML 요소가 있어야 합니다. XML 요소 이름은 필드 이름과 일치해야 합니다. XML 요소는 양식 필드에 해당하지 않거나 XML 요소 이름이 필드 이름과 일치하지 않는 경우에는 무시됩니다. XML 요소가 표시되는 순서와 일치하지 않아도 됩니다. 중요한 요소는 XML 요소가 해당 값과 함께 지정된다는 것입니다.

다음 예제 대출 신청 양식을 고려하십시오.

![대출 신청 양식](assets/loanFormData.png)

데이터를 이 양식 디자인에 병합하려면 양식에 해당하는 XML 데이터 소스를 만듭니다. 다음 XML은 예제 모기지 응용 프로그램 양식에 해당하는 XML 데이터 원본을 나타냅니다.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
- <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
- <xfa:data>
- <data>
    - <Layer>
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
    - <Mortgage>
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

#### 지원되는 문서 유형 {#supported-document-types}

Communications API의 렌더링 기능에 대한 전체 액세스 권한을 얻으려면 XDP 파일을 입력으로 사용하는 것이 좋습니다. 경우에 따라 PDF 파일을 사용할 수 있습니다. 그러나 PDF 파일을 입력으로 사용하면 다음과 같은 제한 사항이 있습니다.

- XFA 스트림이 포함되지 않은 PDF 문서는 PostScript, PCL 또는 ZPL로 렌더링할 수 없습니다. Communications API는 XFA 스트림(즉 Designer에서 만든 양식)으로 PDF 문서를 레이저 및 레이블 형식으로 렌더링할 수 있습니다. PDF 문서에 서명, 인증 또는 사용 권한(AEM Forms Reader 확장 서비스를 사용하여 적용)이 있는 경우 이러한 인쇄 형식으로 렌더링할 수 없습니다.

<!-- * Run-time options such as PDF version and tagged PDF are not supported for Acrobat forms. They are valid for PDF forms that contain XFA streams; however, these forms cannot be signed or certified. 

#### Email support {#email-support}

For email functionality, you can create a process in AEM Workflows that uses the Email Step. A workflow represents a business process that you are automating. -->

#### 인쇄 가능 영역 {#printable-areas}

기본 0.25인치 인쇄 불가 여백은 레이블 프린터에는 정확하지 않으며 프린터마다, 레이블 크기에서 레이블 크기에 따라 다릅니다. 0.25인치 여백을 유지하거나 줄이는 것이 좋습니다. 그러나 인쇄되지 않는 여백은 증가시키지 않는 것이 좋습니다. 그렇지 않으면 인쇄 가능 영역의 정보가 제대로 인쇄되지 않습니다.

항상 프린터에 올바른 XDC 파일을 사용해야 합니다. 예를 들어, 300dpi 프린터의 XDC 파일을 선택하고 문서를 200dpi 프린터로 보내지 마십시오.

#### 스크립트 {#scripts}

Communications API와 함께 사용되는 양식 디자인에는 서버에서 실행되는 스크립트가 포함될 수 있습니다. 양식 디자인에는 클라이언트에서 실행되는 스크립트가 포함되어 있지 않아야 합니다. 양식 디자인 스크립트 만들기에 대한 내용은 디자이너 도움말을 참조하십시오.

<!-- #### Working with Fonts
 Document Considerations for Working with Fonts>> -->

#### 글꼴 매핑 {#font-mapping}

클라이언트 컴퓨터에 글꼴이 설치되어 있으면 디자이너의 드롭다운 목록에서 사용할 수 있습니다. 글꼴이 설치되어 있지 않으면 글꼴 이름을 수동으로 지정해야 합니다. 디자이너의 &quot;사용할 수 없는 글꼴을 영구적으로 바꾸기&quot; 옵션은 해제할 수 있습니다. 그렇지 않으면 XDP 파일이 디자이너에 저장되면 대체 글꼴 이름이 XDP 파일에 기록됩니다. 프린터 상주 글꼴이 사용되지 않음을 의미합니다.

프린터 상주 글꼴을 사용하는 양식을 디자인하려면 프린터에서 사용할 수 있는 글꼴과 일치하는 서체 이름을 디자이너에서 선택합니다. PCL 또는 PostScript에 대해 지원되는 글꼴 목록은 해당 장치 프로필(XDC 파일)에 있습니다. 또는 다른 서체 이름의 프린터 상주 글꼴에 인쇄자가 아닌 글꼴을 매핑하기 위해 글꼴 매핑을 만들 수 있습니다. 예를 들어, PostScript 시나리오에서 Arial® 글꼴에 대한 참조를 프린터에 상주하는 Helvetica® 서식에 매핑할 수 있습니다.

두 가지 유형의 OpenType® 글꼴이 있습니다. 한 유형은 PCL에서 지원하는 TrueType OpenType® 글꼴입니다. 다른 하나는 CFF OpenType®. PDF 및 PostScript 출력은 포함된 Type-1, TrueType 및 OpenType® 글꼴을 지원합니다. PCL 출력은 포함된 TrueType 글꼴을 지원합니다.

Type-1 및 OpenType® 글꼴은 PCL 출력에 포함되지 않습니다. Type-1 및 OpenType® 글꼴로 서식이 지정된 컨텐츠는 래스터화되어 생성되는 속도가 점점 느려질 수 있는 비트맵 이미지로 생성됩니다.

다운로드되거나 포함된 글꼴은 PostScript, PCL 또는 PDF 출력을 생성할 때 자동으로 대체됩니다. 즉, 생성된 문서를 올바르게 렌더링하는 데 필요한 글꼴 글리프의 하위 집합만 생성된 출력에 포함됩니다.

#### 장치 프로필 파일 작업(XDC 파일) {#working-with-xdc-files}

장치 프로필(XDC 파일)은 XML 형식의 프린터 설명 파일입니다. 이 파일을 사용하면 Communications API에서 문서를 레이저 또는 레이블 프린터 형식으로 출력할 수 있습니다. Communications API는 다음을 포함한 XDC 파일을 사용합니다.

- hppcl5c.xdc

- hppcl5e.xdc

- ps_plain_level3.xdc

- ps_plain.xdc

- zpl300.xdc

- zpl600.xdc

- zpl300.xdc

- ipl300.xdc

- ipl400.xdc

- tpcl600.xdc

- dpl300.xdc

- dpl406.xdc

- dpl600.xdc

문서를 만들기 위해 이러한 파일을 수정할 필요가 없습니다. 하지만 비즈니스 요구 사항을 충족하도록 수정할 수 있습니다.

이러한 파일은 상주 글꼴, 종이 트레이, 스테이플러와 같은 특정 프린터의 기능을 지원하는 샘플 XDC 파일입니다. 이 샘플의 목적은 장치 프로필을 사용하여 자체 프린터를 설정하는 방법을 이해하는 데 도움이 됩니다. 이 샘플은 또한 동일한 제품 라인에서 유사한 프린터의 시작점입니다.

#### XCI 구성 파일 작업 {#working-with-xci-files}

Communications API는 XCI 구성 파일을 사용하여 출력이 단일 패널인지 페이지 매김인지를 제어하는 등의 작업을 수행합니다. 이 파일에는 설정할 수 있는 설정이 포함되어 있지만 이 값을 수정하는 것은 일반적이지 않습니다. <!-- The default.xci file is located in the svcdata\XMLFormService folder. -->

Communications API를 사용하는 동안 수정된 XCI 파일을 전달할 수 있습니다. 이 작업을 수행할 때 기본 파일의 복사본을 만들고 비즈니스 요구 사항을 충족하도록 수정해야 하는 값만 변경하고 수정된 XCI 파일을 사용하십시오.

통신 API는 기본 XCI 파일(또는 수정된 파일)로 시작합니다. 그런 다음 통신 API를 사용하여 지정된 값을 적용합니다. 이러한 값은 XCI 설정을 덮어씁니다.

다음 표에서는 XCI 옵션을 지정합니다.

| XCI 옵션 | 설명 |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
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

<!-- Using API

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as HTTP endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example ExpenseClaim.xdp). You can specify a fully qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document. -->
