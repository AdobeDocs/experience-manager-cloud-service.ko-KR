---
title: AEM Forms as a Cloud Service 통신 API
description: 클라우드에서 AEM Forms Communication API를 사용하여 문서 생성, 조작 및 보안
Keywords: document generation, PDF manipulation, document security, batch processing, document conversion, PDF/A compliance
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, Developer, User
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '2720'
ht-degree: 28%

---


# AEM Forms as a Cloud Service 통신 API {#communications-apis-overview}

> **버전 가용성**
>
> * **AEM 6.5**: [AEM 문서 서비스 개요](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/overview-aem-document-services.html)
> * **AEM as a Cloud Service**: 이 문서

## 소개

AEM Forms as a Cloud Service의 커뮤니케이션 API를 통해 비즈니스 요구 사항에 맞게 브랜드에서 승인하고 개인화된 표준화된 문서를 만들 수 있습니다. 이러한 강력한 API를 사용하면 온디맨드 프로세스이든, 대용량 배치 프로세스에서든 프로그래밍 방식으로 문서를 생성하고, 조작하고, 보호할 수 있습니다.

### 주요 이점

* **문서 생성 간소화** - 템플릿을 고객 데이터와 병합하여 개인화된 문서를 만듭니다.
* **강력한 문서 조작** - PDF 문서를 프로그래밍 방식으로 결합, 재배열 및 유효성 검사
* **유연한 배포 옵션** - 대기 시간이 짧은 요구 시 온디맨드 API를 사용하거나 처리량이 많은 작업을 위한 일괄 처리 API를 사용합니다.
* **향상된 보안** - 디지털 서명, 인증 및 암호화를 적용하여 중요한 문서를 보호합니다.
* **클라우드 기반 아키텍처** - 유지 관리 부담 없이 확장 가능하고 안전한 클라우드 인프라 활용

## API 기능 개요

커뮤니케이션 API는 다음 기능 영역으로 구성된 포괄적인 문서 처리 기능 세트를 제공합니다.

| 문서 생성 | 문서 조작 | 문서 추출 | 문서 변환 | 문서 Assurance |
|---------------------|----------------------|---------------------|---------------------|-------------------|
| 템플릿을 PDF 및 인쇄 형식을 비롯한 다양한 형식의 데이터와 병합하여 개인화된 문서를 생성합니다. | PDF 문서를 프로그래밍 방식으로 결합, 재배열 및 확인하여 새 문서 패키지를 만듭니다. | 추가 처리를 위해 PDF 문서에서 속성, 메타데이터 및 컨텐츠를 추출합니다. | 아카이브 요구 사항에 대한 PDF/A 규정 준수 검증을 포함하여 문서를 형식 간에 변환할 수 있습니다. | 디지털 서명, 인증 및 암호화를 적용하여 문서를 보호하고 보호합니다. |

[API 참조 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)에서는 API에서 제공하는 모든 매개 변수, 인증 방법 및 다양한 서비스에 대한 자세한 정보를 제공합니다. API 참조 설명서는 .yaml 형식으로도 사용할 수 있습니다. .yaml 를 다운로드하고 Postman에 업로드하여 API의 기능을 확인할 수 있습니다.

## 적용 가능성 및 사용 사례

### 보험

## AEM Forms에서 보험 증서 문서를 생성할 수 있습니까?

예. AEM Forms은 양식을 통해 캡처한 템플릿 및 구조화된 데이터를 사용하여 정책 관련 문서를 생성할 수 있습니다.

## AEM Forms이 규모에 맞게 보험 업무를 처리할 수 있습니까?

예. Adobe Managed Services 또는 프라이빗 클라우드에서 권장 아키텍처를 사용하여 배포하면 AEM Forms에서 대량 양식 제출 및 엔터프라이즈급 워크로드를 지원합니다.

## 문서 생성

커뮤니케이션 문서 생성 API를 사용하면 템플릿(XFA 또는 PDF)과 고객 데이터(XML)를 결합하여 PDF, AFP(고급 함수 프레젠테이션) 및 PS, PCL, DPL, IPL, ZPL 등의 인쇄 형식으로 문서를 생성할 수 있습니다. 이러한 API는 [XML 데이터](communications-known-issues-limitations.md#form-data)와 함께 PDF 및 XFA 템플릿을 사용하여 요청 시 단일 문서를 생성하거나 일괄 작업을 사용하여 여러 문서를 생성합니다.

일반적으로 [디자이너](use-forms-designer.md)를 사용하여 템플릿을 만들고 통신 API를 사용하여 데이터를 템플릿과 병합합니다. 애플리케이션은 출력 문서를 네트워크 프린터, 로컬 프린터 또는 스토리지 시스템에 전송하여 보관합니다. 일반적인 기본 제공 및 사용자 지정 워크플로는 다음과 같습니다.

![통신 문서 생성 워크플로](assets/communicaions-workflow.png)

사용 사례에 따라 웹 사이트나 스토리지 서버를 통해 해당 문서를 다운로드할 수도 있습니다.

### 주요 문서 생성 기능

#### PDF/AFP 전자 형식으로 문서 만들기

문서 생성 API를 사용하여 양식 디자인 및 XML 양식 데이터를 기반으로 하는 PDF 또는 AFP 형식의 문서를 만들 수 있습니다. 출력은 비대화형 문서입니다. 즉, 사용자는 양식 데이터를 입력하거나 수정할 수 없습니다. 기본 워크플로는 XML 양식 데이터를 양식 디자인과 병합하여 문서를 만드는 것입니다. 다음 일러스트레이션은 양식 디자인과 XML 양식 데이터를 병합하여 PDF 문서를 생성하는 모습을 보여 줍니다.

![PDF 문서 만들기](assets/outPutPDF_popup.png)
그림: 문서를 만드는 일반적인 워크플로

아래 표에는 AFP 및 PDF 형식의 차이가 표시됩니다.

| **기능** | **AFP(고급 함수 표시)** | **PDF(휴대용 문서 형식)** |
|---------------------------|--------------------------------------------------------------------|-------------------------------------------------------------|
| **용도** | 트랜잭션 문서의 대량 인쇄 및 제작 | 범용 문서 공유 및 보기 |
| **사용 사례** | 은행 거래 명세서, 청구서, 송장, 보험 서류 | 전자 책, 양식, 보고서, 이력서, 매뉴얼 |
| **플랫폼 원본** | IBM에서 개발 | Adobe에서 개발 |
| **구조** | 구조화된 필드 및 개체가 있는 페이지 지향 형식 | 페이지 지향적이지만 고정된 레이아웃 |
| **편집 가능성** | 프로덕션 인쇄용으로 설계되었으며 거의 편집되지 않음 | 다양한 도구(예: Adobe Acrobat)로 편집할 수 있습니다 |
| **파일 크기 및 성능** | 고속 인쇄 환경의 성능에 최적화 | 크기가 더 크고 벌크 출력에 덜 최적화될 수 있음 |
| **상호 작용** | 최소 - 없음, 정적 페이지 | 양식, 링크, JavaScript과 같은 대화형 요소 지원 |
| **출력 제어** | 프린터의 레이아웃을 세밀하게 제어합니다. | 화면 및 인쇄에 최적화된 시각적 레이아웃 |
| **글꼴 및 그래픽** | 글꼴 및 리소스 참조를 사용합니다. 렌더러가 해석해야 합니다. | 글꼴 및 이미지를 파일에 직접 임베드 |

문서 생성 API는 생성된 PDF 문서 또는 AFP 문서를 반환합니다. 선택적으로 생성된 PDF를 Azure Blob Storage에 업로드할 수도 있습니다.

<span class="preview"> 문서 생성 API를 사용하여 생성된 PDF를 Azure Blob Storage 기능에 업로드하는 작업은 [얼리 어답터 프로그램](/help/forms/early-access-ea-features.md)에 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

#### PS(PostScript), PCL(Printer Command Language), ZPL(Zebra Printing Language) 문서 만들기 {#create-PS-PCL-ZPL-documents}

문서 생성 API를 사용하여 XDP 양식 디자인 또는 PDF 문서를 기반으로 하는 PostScript(PS), 프린터 명령 언어(PCL) 및 Zebra 인쇄 언어(ZPL) 문서를 만들 수 있습니다. 해당 API는 양식 디자인을 양식 데이터와 병합하여 문서를 생성하는 데 도움이 됩니다. 문서를 파일에 저장하고, 사용자 지정 프로세스를 개발하여 프린터에 전송할 수 있습니다.

#### 배치 데이터를 처리하여 여러 문서 만들기 {#processing-batch-data-to-create-multiple-documents}

문서 생성 API를 사용하여 XML 배치 데이터 소스 내의 각 기록에 별도의 문서를 만들 수 있습니다. 비동기화 모드에서 문서를 일괄 생성할 수 있습니다. 다양한 매개변수를 구성하여 변환한 다음 배치 프로세스를 시작할 수 있습니다.

![PDF 문서 만들기](assets/ou_OutputBatchMany_popup.png)

## 문서 조작

Communications document manipulation(Document Transformation) API 를 통해 PDF 문서를 결합하고 재배열할 수 있습니다. 일반적으로 DDX를 만들어 문서 조작 API에 제출하여 문서를 조합하거나 재정렬합니다. [DDX 문서](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf)에서는 소스 문서를 사용하여 필요한 문서 세트를 생성하는 방법에 대한 지침을 제공합니다. DDX 참조 설명서는 지원되는 모든 작업에 대한 자세한 정보를 제공합니다.

### 주요 문서 조작 기능

#### PDF 문서 어셈블

문서 조작 API를 사용하여 두 개 이상의 PDF 또는 XDP 문서를 단일 PDF 문서 또는 PDF 포트폴리오로 어셈블할 수 있습니다. 다음은 PDF 문서를 조합할 수 있는 몇 가지 방법입니다.

* 간단한 PDF 문서 어셈블
* PDF 포트폴리오 만들기
* 암호화된 문서 어셈블
* Bates 번호 매기기를 사용하여 문서 어셈블
* 문서 변환 및 어셈블

![여러 PDF 문서에서 간단한 PDF 어셈블하기](assets/as_document_assembly.png)
그림: 여러 PDF 문서에서 간단한 PDF 문서 어셈블하기

#### PDF 문서 디스어셈블

문서 조작 API를 사용하여 PDF 문서를 디스어셈블할 수 있습니다. API는 소스 문서에서 페이지를 추출하거나 책갈피를 기준으로 소스 문서를 나눌 수 있습니다. 일반적으로 이 작업은 명령문 컬렉션 등 여러 개별 문서에서 PDF 문서가 만들어진 경우에 유용합니다.

* 소스 문서에서 페이지 추출
* 책갈피를 기준으로 소스 문서 나누기

![책갈피를 기준으로 소스 문서를 여러 문서로 나누기](assets/as_intro_pdfsfrombookmarks.png)
그림: 책갈피를 기준으로 소스 문서를 여러 문서로 나누기

>[!NOTE]
>
> AEM Forms은 PDF 파일과 원활하게 통합되는 다양한 기본 제공 글꼴을 제공합니다. 지원되는 글꼴 목록을 보려면 [여기를 클릭](/help/forms/supported-out-of-the-box-fonts.md)하세요.

## 문서 추출

<span class="preview"> 문서 추출 기능이 얼리어답터 프로그램에 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

문서 추출 서비스는 사용 권한, PDF 속성 및 메타데이터와 같은 PDF 문서의 속성을 가져오는 기능을 제공합니다. 문서 추출 기능:

* PDF에 첨부 파일, 댓글, Acrobat 버전 등이 있는 경우와 같은 PDF 문서의 속성을 가져옵니다.
* PDF 문서에서 활성화된 사용 권한을 추출하면 사용자가 Adobe Acrobat Reader 확장성을 위해 PDF 문서에 대해 활성화되거나 비활성화된 사용 권한을 검색합니다.
* PDF 문서에 있는 메타데이터 정보를 가져옵니다. 메타데이터는 문서에 대한 정보이며 텍스트 및 그래픽과 같은 문서의 컨텐츠와 구분됩니다. Adobe 확장 메타데이터 플랫폼(XMP)은 문서 메타데이터를 처리하는 표준입니다. XMP 유틸리티 서비스는 PDF 문서에서 XMP 메타데이터를 검색하고 XMP 메타데이터를 PDF 문서로 내보낼 수 있습니다.

[API 참조 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)에서는 모든 매개 변수, 인증 방법 및 API에서 제공하는 서비스에 대한 자세한 정보를 제공합니다. API 참조 설명서는 .yaml 형식으로도 사용할 수 있습니다. .yaml 를 다운로드하고 Postman에 업로드하여 API의 기능을 확인할 수 있습니다.

## 문서 변환

### PDF/A호환 문서로 변환하고 확인합니다.

커뮤니케이션 문서 변환 API 는 PDF 문서를 PDF/A로 변환하는 데 도움이 됩니다. API를 사용하여 PDF 문서를 PDF/A 호환 문서로 변환하고 PDF 문서가 PDF/A 호환되는지 확인할 수 있습니다. PDF/A는 문서 내용을 장기간 보존하기 위한 보관 형식입니다. 글꼴이 문서 내에 임베드되어 있고 파일이 압축 해제되어 있습니다. 따라서 PDF/A 문서는 일반적으로 표준 PDF 문서보다 큽니다. 또한 PDF/A 문서에는 오디오 및 비디오 콘텐츠가 포함되어 있지 않습니다. 지원되는 PDF/A 준수 표준에는 PDF/A-1a, 1b, 2a, 2b, 3a 및 3b가 포함됩니다.

### PDF을 XDP로 변환 {#convert-pdf-to-xdp}

<span class="preview"> PDF을 XDP로 변환 기능은 얼리어답터 프로그램에 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

PDF 문서를 XDP 파일로 변환합니다. PDF 문서를 XDP 파일로 성공적으로 변환하려면 PDF 문서에 사전에 XFA 스트림이 있어야 합니다.

## 문서 Assurance {#doc-assurance}

DocAssurance 서비스에는 서명 및 암호화 API가 포함되어 있습니다.

### 서명 API

서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. <!--This service uses digital signatures and certification to ensure that only intended recipients can alter documents. --> 문서 자체에 보안 기능이 적용되어 문서는 전체 수명 주기에 대해 안전하게 제어됩니다. 문서는 오프라인으로 다운로드할 때와 조직에 다시 제출될 때 방화벽 이후에도 안전하게 유지됩니다. 서명 API를 사용하여 다음 작업을 수행할 수 있습니다.

* PDF 문서에 보이는 서명 필드를 추가합니다.
* PDF 문서에 보이지 않는 서명 필드를 추가합니다.
* PDF 문서에서 지정된 서명 필드에 서명합니다.
* PDF 문서 인증
* PDF 문서의 지정된 서명 필드에서 서명 제거
* PDF 문서에서 지정된 서명 필드 삭제

<span class="preview"> 얼리어답터 프로그램에서 사용 가능한 PDF 문서에서 지정된 서명 필드에서 서명을 제거하고 지정된 서명 필드를 삭제합니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

### 암호화 API

암호화 API를 사용하면 문서를 암호화하고 해독할 수 있습니다. 문서가 암호화되면 해당 콘텐츠를 읽을 수 없게 됩니다. 권한이 있는 사용자는 문서의 암호를 해독하여 해당 콘텐츠에 액세스할 수 있습니다. PDF 문서가 암호로 암호화되어 있는 경우 Adobe Reader 또는 Adobe Acrobat에서 문서를 보려면 먼저 사용자가 열기 암호를 지정해야 합니다. <!-- Likewise, if a PDF document is encrypted with a certificate, the user must decrypt the PDF document with the public key that corresponds to the certificate (private key) that was used to encrypt the PDF document.-->

암호화 API를 사용하여 다음 작업을 수행할 수 있습니다.

* 암호로 PDF 문서를 암호화합니다.
* PDF 문서에서 암호 기반 암호화를 제거합니다.
* PDF 문서에 적용된 보안 유형을 검색합니다.
* PDF 문서에 적용된 보안 유형을 반환합니다.

서명 API와 암호화 API는 모두 [동기 API](#types-of-communications-apis-types)입니다.

### 문서 유틸리티 {#doc-utility}

동기 API를 사용하는 문서 유틸리티를 사용하면 PDF 및 XDP 파일 형식 간에 문서를 변환할 수 있습니다. 문서에 사용 권한을 적용하고 문서에서 활성화된 사용 권한을 추출합니다. PDF 문서에 대한 정보를 쿼리합니다. 사용 권한 API의 <!-- determines whether a PDF document contains comments or attachments and more, and use document transformation services for XMP utilities--> 세부 정보는 아래에 나와 있습니다.

#### 사용 권한 API(Reader 확장)

<span class="preview"> 사용 권한(Reader 확장) 기능이 얼리어답터 프로그램에 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

사용 권한 기능을 사용하면 추가 사용 권한으로 Adobe Reader의 기능을 확장하여 조직에서 대화형 PDF 문서를 쉽게 공유할 수 있습니다. 이 서비스는 Adobe Reader 7.0 이상에서 작동하며 PDF 문서에 사용 권한을 추가합니다. 이 작업은 문서에 주석 추가, 양식 채우기, 문서 저장 등과 같이 Adobe Reader를 사용하여 PDF 문서를 열 때 일반적으로 사용할 수 없는 기능을 활성화합니다.

PDF 문서에 적절한 사용 권한이 추가되면 수신자는 Adobe Reader에서 다음 활동을 수행할 수 있습니다.

* 온라인 또는 오프라인에서 PDF 문서 및 양식을 완성하여 수신자가 레코드를 위해 사본을 로컬에 저장하고 추가된 정보를 그대로 유지할 수 있습니다.
* PDF 문서를 로컬 하드 드라이브에 저장하여 원본 문서와 추가 설명, 데이터 또는 첨부 파일을 유지합니다.
* PDF 문서에 파일 및 미디어 클립 첨부
* 업계 표준 공개 키 인프라(PKI) 기술을 사용하여 디지털 서명을 적용하여 PDF 문서에 서명, 인증 및 인증합니다.
* 완료되거나 주석이 있는 PDF 문서를 전자적으로 제출합니다.
* PDF 문서 및 양식을 내부 데이터베이스 및 웹 서비스에 대한 직관적인 개발 프런트 엔드로 사용합니다.
* 검토자가 직관적인 마크업 도구를 사용하여 주석을 추가할 수 있도록 다른 사용자와 PDF 문서를 공유합니다. 이러한 도구에는 전자 스티커 메모, 스탬프, 하이라이트 및 텍스트 취소선이 포함됩니다. Acrobat에서도 동일한 기능을 사용할 수 있습니다.
* Barcoded Forms 디코딩을 지원합니다.

이러한 특수 사용 권한 기능은 권한이 활성화된 PDF 문서가 Adobe Reader에서 열리면 자동으로 활성화됩니다. 사용자가 권한이 활성화된 문서 작업을 완료하면 Adobe Reader에서 해당 기능이 다시 비활성화됩니다. 사용자가 다른 권한이 활성화된 PDF 문서를 받을 때까지 비활성화됩니다.

#### 사용 권한 활성화 또는 비활성화

PDF Reader 서비스를 확장하기 위한 다양한 사용 권한 기능은 다음과 같습니다.

* **바코드 디코딩**: PDF 문서 내의 바코드를 디코딩합니다.

* **댓글**: PDF 문서에서 오프라인으로 댓글을 달려면

* **온라인 댓글**: PDF 문서에 온라인으로 댓글을 달려면

* **디지털 서명**: PDF 문서에 디지털 서명을 추가합니다.

* **동적 양식 필드**: 양식 필드를 PDF 문서에 추가합니다.

* **동적 양식 페이지**: 양식 페이지를 PDF 문서에 추가합니다.

* **포함된 파일**: PDF 문서 내에 파일을 포함합니다.

* **양식 데이터 가져오기**: 양식 데이터를 PDF 문서로 가져옵니다.

* **양식 데이터 내보내기**: 양식 데이터를 PDF 문서로 가져옵니다.

* **양식 채우기**: PDF 문서의 양식 필드를 채우려면

* **온라인 Forms**: PDF 문서에서 웹 서비스 또는 데이터베이스에 액세스합니다.

* **독립 실행형 제출**: PDF 문서에서 오프라인으로 양식 데이터를 제출합니다.

#### 기타 기능

* **메시지**: 하나 이상의 사용 권한이 적용된 PDF 문서를 열 때 Adobe Acrobat Reader 내에 표시되는 메시지입니다.
* **암호 잠금 해제**: 암호화된 PDF 문서를 여는 데 필요한 암호입니다. 일반적으로 문서 열기 암호이지만 PDF 문서가 권한 암호로 추가로 보호되는 경우 중 하나를 사용하여 열 수 있습니다.

## 통신 API 유형 {#types}

커뮤니케이션은 주문형 및 배치 문서 생성에 HTTP API를 제공합니다.

* **[동기식 API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)**&#x200B;는 주문형, 대기 시간이 낮은 단일 기록 문서 생성 시나리오에 적합합니다. 해당 API는 사용자 액션 기반 사용 사례에 보다 적합합니다. 예: 사용자 양식 작성 완료 후 문서 생성.

* **[배치 API(비동기 API)](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)**&#x200B;는 처리량이 높은 예약된 문서 생성 시나리오에 적합합니다. 해당 API는 배치 문서를 생성합니다. 예를 들어, 전화 요금 청구서, 신용카드 명세서 및 혜택 명세서는 매월 생성됩니다.

## 온보딩

커뮤니케이션 기능은 Forms as a Cloud Service 사용자용 독립 실행형 모듈과 추가 기능 모듈로 제공됩니다. Adobe 영업팀 또는 Adobe 담당자에게 문의하여 액세스 권한을 요청할 수 있습니다. Adobe는 조직에 대한 액세스 권한을 활성화하고 조직의 책임자로 지정된 사람에게 필요한 권한을 제공합니다. 관리자는 API를 사용하도록 조직의 Forms as a Cloud Service 개발자(사용자)에게 액세스 권한을 부여할 수 있습니다.

온보딩 후 Forms as a Cloud Service 환경에 대한 통신 기능을 활성화하려면 다음을 수행하십시오.

1. Cloud Manager에 로그인하고 AEM Forms as a Cloud Service 인스턴스를 엽니다.

1. 프로그램 편집 옵션을 열고 솔루션 및 추가 기능 탭으로 이동하여 **[!UICONTROL 양식 - 커뮤니케이션]** 옵션을 선택합니다.

   ![커뮤니케이션](assets/communications.png)

   **[!UICONTROL 양식 - 디지털 등록]** 옵션이 이미 활성화된 경우 **[!UICONTROL 양식 - 커뮤니케이션 추가 기능]** 옵션을 선택합니다.

   ![추가 기능](assets/add-on.png)

1. **[!UICONTROL 업데이트]**&#x200B;를 클릭합니다.

1. 빌드 파이프라인을 실행합니다. 빌드 파이프라인이 성공하면 환경에 통신 API가 활성화됩니다.

>[!NOTE]
>
> 문서 조작 API를 활성화하고 구성하려면 [Dispatcher 구성](setup-local-development-environment.md#forms-specific-rules-to-dispatcher)에 다음 규칙을 추가하십시오.
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## 추가 리소스 {#see-also}

* [통신 처리 - 동기 API](/help/forms/aem-forms-cloud-service-communications.md)
* [통신 처리 - 일괄 처리 API](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
* [AEM Forms as a Cloud Service 아키텍처](/help/forms/aem-forms-cloud-service-architecture.md)
* [API 참조 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)
* [얼리 어답터 프로그램 기능](/help/forms/early-access-ea-features.md)
