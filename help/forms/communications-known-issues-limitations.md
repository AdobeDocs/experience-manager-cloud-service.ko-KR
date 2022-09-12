---
title: 알려진 문제 및 우수 사례를 고려 사항
description: 통신 우수 사례, 알려진 문제 및 제한 사항
exl-id: e95615dd-e494-40cd-9cdf-6e9761ca3b3e
source-git-commit: 4b76fbbb1b58324065b39d6928027759b0897246
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 0%

---

# 알려진 문제 및 우수 사례를 고려 사항 {#best-practices-known-issues-and-limitations}

Communication API를 사용하기 전에 다음 고려 사항, 알려진 문제 및 FAQ를 검토하십시오.

## 고려 사항  {#considerations-for-communications-apis}

### 양식 데이터 {#form-data}

Communications API는 일반적으로 디자이너에서 만들어지는 양식 디자인과 XML 양식 데이터를 모두 입력으로 허용합니다. 문서를 데이터로 채우려면 채울 모든 양식 필드의 XML 양식 데이터에 XML 요소가 있어야 합니다. XML 요소 이름은 필드 이름과 일치해야 합니다. XML 요소는 양식 필드에 해당하지 않거나 XML 요소 이름이 필드 이름과 일치하지 않는 경우에는 무시됩니다. XML 요소가 표시되는 순서와 일치하지 않아도 됩니다. 중요한 요소는 XML 요소가 해당 값과 함께 지정된다는 것입니다.

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

### 지원되는 문서 유형 {#supported-document-types}

Communications API의 렌더링 기능에 대한 전체 액세스 권한을 얻으려면 XDP 파일을 입력으로 사용하는 것이 좋습니다. 경우에 따라 PDF 파일을 사용할 수 있습니다. 그러나 PDF 파일을 입력으로 사용하면 다음과 같은 제한이 있습니다.

XFA 스트림이 포함되지 않은 PDF 문서는 PostScript, PCL 또는 ZPL로 렌더링할 수 없습니다. Communications API는 XFA 스트림(즉 Designer에서 만든 양식)으로 PDF 문서를 레이저 및 레이블 형식으로 렌더링할 수 있습니다. PDF 문서에 서명, 인증 또는 사용 권한(AEM Forms Reader 확장 서비스를 사용하여 적용)이 있는 경우 이러한 인쇄 형식으로 렌더링할 수 없습니다.


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


## 알려진 문제

* 특정 렌더링 유형(PDF, PRINT)은 인쇄 옵션 목록에서 한 번만 사용할 수 있습니다. 예를 들어 PCL 렌더링 유형을 지정하는 PRINT 옵션은 각각 두 개 가질 수 없습니다.

* 일괄 처리 구성의 경우 OutputType(PDF, PRINT) 및 RenderType(PostScript, PCL, IPL, ZPL 등)의 값 조합 인스턴스 하나만 가 허용됩니다.

* 비동기 API(배치 처리)의 경우 기본 레코드 수준이 2로 설정됩니다. 사용자 지정 XCI를 사용하여 레코드 수준을 1로 변경할 수 있습니다.

* 기본 XCI가 구성되면 원본 렌디션까지 경로가 포함됩니다. 예 `/content/dam/formsanddocuments/default.xci/jcr:content/renditions/original`



## 모범 사례

* Adobe은 AEM Cloud Service에서 사용하는 클라우드 영역에서 데이터 파일 blob 컨테이너 저장소를 호스팅하도록 권장합니다.

## 자주 묻는 질문 {#faq}

**감시 폴더나 다른 스토리지 메커니즘을 사용하여 입출력 작업을 저장할 수 있습니까?**

현재 Microsoft Azure 저장 공간을 사용하여 입력 데이터와 생성된 문서를 저장할 수 있습니다. Microsoft Azure 저장소는 [데이터 이동 작업 자동화](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10).

**Microsoft Azure 저장 공간 계정이 Experience Manager Forms Cloud Service 라이선스에 포함되어 있습니까?**

Microsoft Azure 저장 공간 계정은 Experience Manager Forms Cloud Service 라이선스와 독립적입니다.

**Communication API는 Experience Manager Forms Cloud Service 서버에 데이터를 저장합니까?**

입력 및 출력 데이터는 Microsoft Azure 저장소에만 저장됩니다.

**Communication API는 Experience Manager Forms Cloud Service에만 사용할 수 있습니까? 온-프레미스 환경에서 유사한 기능을 사용할 수 있습니까?**

AEM Forms 출력 서비스를 사용하여 템플릿(XFA 또는 PDF)을 고객 데이터와 결합하여 PDF, PS, PCL 및 ZPL 형식으로 문서를 생성할 수 있습니다.

온-프레미스 환경과 비교하여 Cloud Service은 자동 확장 및 비용 효율성의 추가적인 이점을 제공합니다.

<!--**Where is data processed?**

**Who has access to data?**

**Is data encrypted?**

**Where is data hosted?** -->

**여러 배치 작업을 동시에 실행할 수 있습니까?**
예, 여러 배치 작업을 함께 실행할 수 있습니다. 충돌을 방지하려면 모든 작업에 항상 서로 다른 소스 및 대상 폴더를 사용하십시오.
