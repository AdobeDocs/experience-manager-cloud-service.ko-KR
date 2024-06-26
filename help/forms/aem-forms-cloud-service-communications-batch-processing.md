---
title: 간편한 벌크 PDF 생성 - 일괄 처리 기술을 기본으로 제공 - 수백만 개의 PDF 문서 생성에 대한 자체 도움말 안내서!
description: 브랜드 지향적이고 개인화된 커뮤니케이션을 만드는 방법
feature: Adaptive Forms, APIs & Integrations
role: Admin, Developer, User
exl-id: 542c8480-c1a7-492e-9265-11cb0288ce98
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 2%

---

# AEM Forms as a Cloud Service 통신 일괄 처리

커뮤니케이션을 사용하면 비즈니스 서신, 문서, 명세서, 청구 처리 편지, 혜택 공지, 월별 청구서 및 시작 키트와 같은 브랜드 지향적이고 개인화된 커뮤니케이션을 만들고, 조합하고, 제공할 수 있습니다. 커뮤니케이션 API를 사용하여 템플릿(XFA 또는 PDF)을 고객 데이터와 결합하여 PDF, PS, PCL, DPL, IPL 및 ZPL 형식의 문서를 생성할 수 있습니다.

통신은 온디맨드 및 예약된 문서 생성을 위한 API를 제공합니다. 온디맨드 API에는 동기 API를, 예약된 문서 생성에는 배치 API(비동기 API)를 사용할 수 있습니다.

* 동기 API는 온디맨드, 짧은 대기 시간 및 단일 레코드 문서 생성 사용 사례에 적합합니다. 해당 API는 사용자 액션 기반 사용 사례에 보다 적합합니다. 예를 들어 사용자가 양식을 작성한 후 문서를 생성하는 방법이 있습니다.

* 배치 API(비동기 API)는 예약된 높은 처리량의 여러 문서 생성 사용 사례에 적합합니다. 해당 API는 배치 문서를 생성합니다. 예: 매월 생성되는 전화요금 청구서, 신용카드 명세서와 혜택 명세서.

<!-- The following skills are required to create templates and use HTTP APIs: 

* Understanding of Adobe Forms Designer or Acrobat Forms to create templates

* Understanding of HTTP APIs and experience of using HTTP APIs

* Basic understanding of Adobe Experience Manager -->


## 일괄 처리 작업 {#batch-operations}

배치 작업은 예약된 간격으로 레코드 세트에 대해 유사한 유형의 여러 문서를 생성하는 프로세스입니다. 배치 작업에는 구성(정의)과 실행의 두 부분이 있습니다.

* **구성(정의)**: 배치 구성은 생성된 문서에 대해 설정할 다양한 에셋 및 속성에 대한 정보를 저장합니다. 예를 들어 출력 문서에 대한 다양한 속성을 지정할 때 사용할 XDP 또는 PDF 템플릿과 고객 데이터의 위치에 대한 세부 정보를 제공합니다.

* **실행**: 일괄 처리 작업을 시작하려면 일괄 처리 구성 이름을 일괄 처리 실행 API에 전달합니다.

### 배치 작업의 구성 요소 {#components-of-a-batch-operations}

**클라우드 구성**: Experience Manager Cloud 구성은 Experience Manager 인스턴스를 고객이 소유한 Microsoft Azure 스토리지에 연결하는 데 도움이 됩니다. 고객이 소유한 Microsoft Azure 계정에 연결할 자격 증명을 지정할 수 있습니다.

**일괄 데이터 저장소 구성(USC)**: 일괄 데이터 구성은 일괄 처리 API에 대한 Blob 스토리지의 특정 인스턴스를 구성하는 데 도움이 됩니다. 고객이 소유한 Microsoft Azure Blob 저장소에서 입력 및 출력 위치를 지정할 수 있습니다.

**일괄 처리 API**: 배치 구성을 생성하고 이러한 구성을 기반으로 배치 실행을 실행하여 PDF 또는 XDP 템플릿을 데이터와 병합하고 PDF, PS, PCL, DPL, IPL 및 ZPL 형식으로 출력을 생성할 수 있습니다. 통신은 구성 관리 및 배치 실행을 위한 배치 API를 제공합니다.

![데이터 병합 테이블](assets/communications-batch-structure.png)

**스토리지**: 커뮤니케이션 API는 고객이 소유한 Microsoft Azure 클라우드 스토리지를 사용하여 고객 레코드를 가져오고 생성된 문서를 저장합니다. Experience Manager Cloud Service 구성에서 Microsoft Azure 스토리지를 구성합니다.

**앱**: 일괄 처리 API를 사용하여 문서를 생성하고 사용하는 사용자 정의 애플리케이션.

## 일괄 처리 작업을 사용하여 여러 문서 생성 {#generate-multiple-documents-using-batch-operations}

배치 작업을 사용하여 예약된 간격으로 여러 문서를 생성할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/338349)

비디오를 보거나 아래 지침을 수행하여 일괄 작업을 사용하여 문서를 생성하는 방법을 배울 수 있습니다. 비디오에 사용되는 API 참조 설명서는 .yaml 형식으로 제공됩니다. 다음을 다운로드할 수 있습니다. [일괄 처리 API](assets/batch-api.yaml) 파일을 만들어 Postman에 업로드하여 API의 기능을 확인하고 비디오를 따라 수행합니다.

### 전제 조건 {#pre-requisites}

배치 API를 사용하려면 다음 조건을 충족해야 합니다.

* [Microsoft Azure 스토리지 계정](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create)
* PDF 또는 XDP 템플릿
* [템플릿과 병합할 데이터](#form-data)
* Experience Manager 관리자 권한이 있는 사용자

### 환경 설정 {#setup-your-environment}

배치 작업을 사용하기 전에:

* 고객 데이터(XML 파일)를 Microsoft Azure Blob 스토리지에 업로드
* 클라우드 구성 만들기
* 일괄 처리 데이터 저장소 구성 만들기
* Experience Manager Forms Cloud Service 인스턴스에 템플릿 및 기타 에셋 업로드

### 고객 데이터(XML 파일)를 Azure Storage에 업로드 {#upload-customer-data-to-Azure-Storage}

Microsoft Azure 스토리지에서 다음을 만듭니다. [컨테이너](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-blobs) 및 [고객 데이터 업로드 (XML)](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-blobs#managing-blobs-in-a-blob-container) (으)로 [폴더](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal) 컨테이너 안쪽에.
>[!NOTE]
>
>입력 폴더를 자동으로 정리하거나 출력 폴더의 컨텐츠를 예약된 간격으로 다른 위치로 이동하도록 Microsoft Azure 저장소를 구성할 수 있습니다. 그러나 폴더를 참조하는 일괄 처리 작업이 계속 실행 중일 때는 폴더가 정리되지 않도록 하십시오.

### 클라우드 구성 만들기 {#create-a-cloud-configuration}

클라우드 구성은 Experience Manager 인스턴스를 Microsoft Azure Storage에 연결합니다. 클라우드 구성을 만들려면 다음 작업을 수행하십시오.

1. 도구 > Cloud Service > Azure 스토리지로 이동합니다.
1. 구성을 호스팅할 폴더를 열고 [만들기]를 클릭합니다. 전역 폴더를 사용하거나 폴더를 만듭니다.
1. 서비스에 연결할 구성 및 자격 증명의 이름을 지정합니다. 다음을 수행할 수 있습니다. [Microsoft Azure 스토리지 포털에서 이러한 자격 증명을 검색합니다.](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal#view-account-access-keys).
1. 만들기 를 클릭합니다.

이제 Experience Manager 인스턴스를 Microsoft Azure Storage에 연결하고 필요한 경우 이 인스턴스를 사용하여 콘텐츠를 저장하고 읽을 수 있습니다.

### 일괄 처리 데이터 저장소 구성 만들기 {#create-batch-data-store-configuration}

배치 데이터 구성은 입력 및 출력을 위한 컨테이너 및 폴더를 구성하는 데 도움이 됩니다. 고객 레코드를 Source 폴더에 보관하고 생성된 문서는 대상 폴더에 배치합니다.

구성을 만들려면 다음 작업을 수행하십시오.

1. 도구 > Forms > 통합 스토리지 커넥터로 이동합니다.
1. 구성을 호스팅할 폴더를 열고 [만들기]를 클릭합니다. 전역 폴더를 사용하거나 폴더를 만듭니다.
1. 구성의 제목 및 이름 을 지정합니다. 스토리지에서 Microsoft Azure 스토리지를 선택합니다.
1. 스토리지 구성 경로에서 고객 소유 Azure 스토리지 계정의 자격 증명이 포함된 클라우드 구성을 검색하여 선택합니다.
1. Source 폴더에서 Azure 저장소 컨테이너의 이름과 레코드가 포함된 폴더를 지정합니다.
1. 대상 폴더에서 생성된 문서를 저장할 Azure 스토리지 컨테이너 및 폴더의 경로를 지정합니다.
1. 만들기 를 클릭합니다.

이제 Experience Manager 인스턴스가 Microsoft Azure Storage에 연결되고 데이터를 검색하여 Microsoft Azure Storage의 특정 위치로 보내도록 구성되었습니다.

### Experience Manager 인스턴스에 템플릿 및 기타 에셋 업로드 {#upload-templates-and-other-assets-to-your-AEM-instance}

조직에는 일반적으로 여러 템플릿이 있습니다. 예를 들어 신용 카드 명세서, 복리후생 명세서 및 청구 신청에 대해 각각 하나의 템플리트가 있습니다. 이러한 모든 XDP 및 PDF 템플릿을 Experience Manager 인스턴스에 업로드합니다. 템플릿을 업로드하려면 다음 작업을 수행하십시오.

1. Experience Manager 인스턴스를 엽니다.
1. Forms > Forms 및 문서로 이동합니다.
1. 만들기 > 폴더 를 클릭하고 폴더를 만듭니다. 폴더를 엽니다.
1. 만들기 > 파일 업로드 를 클릭하고 템플릿을 업로드합니다.

## 일괄 처리 API를 사용하여 문서 생성 {#use-batch-API-to-generate-documents}

일괄 처리 API를 사용하려면 일괄 처리 구성을 만들고 해당 구성을 기반으로 실행을 실행합니다. API 설명서는 일괄 처리를 만들고 실행하기 위한 API, 해당 매개 변수 및 가능한 오류에 대한 정보를 제공합니다. 다음을 다운로드할 수 있습니다. [API 정의 파일](assets/batch-api.yaml) 파일 및 업로드 [Postman](https://go.postman.co/home) 또는 API를 테스트하여 일괄 처리 작업을 만들고 실행하는 유사한 소프트웨어입니다.

### 일괄 처리 만들기 {#create-a-batch}

일괄 처리를 생성하려면 다음을 사용합니다. `POST /config` API. HTTP 요청 본문에 다음 필수 속성을 포함합니다.

* **configName**: 배치의 고유 이름을 지정합니다. 예, `wknd-job`
* **dataSourceConfigUri**: 배치 데이터 저장소 구성의 위치를 지정합니다. 구성의 상대 경로이거나 절대 경로일 수 있습니다. 예를 들어`/conf/global/settings/forms/usc/batch/wknd-batch`
* **출력 유형**: 출력 형식 지정: PDF 및 인쇄. PRINT 출력 유형을 사용하는 경우 `printedOutputOptionsList` 속성을 사용하려면 인쇄 옵션을 하나 이상 지정하십시오. 인쇄 옵션은 해당 렌더링 유형으로 식별되므로, 현재 동일한 렌더링 유형의 여러 인쇄 옵션은 허용되지 않습니다. 지원되는 형식은 PS, PCL, DPL, IPL 및 ZPL입니다.

* **템플릿**: 템플릿의 절대 또는 상대 경로를 지정합니다. 예, `crx:///content/dam/formsanddocuments/wknd/statements.xdp`

상대 경로를 지정하는 경우 컨텐츠 루트도 제공합니다. 콘텐츠 루트에 대한 자세한 내용은 API 설명서 를 참조하십시오.

<!-- For example, you include the following JSON in the body of HTTP APIs to create a batch named wknd-job: -->

다음을 사용할 수 있습니다. `GET /config /[configName]` 을 눌러 배치 구성의 세부 정보를 확인합니다.

### 일괄 처리 실행 {#run-a-batch}

배치를 실행(실행)하려면 `POST /config /[configName]/execution`. 예를 들어 wknd-demo라는 배치를 실행하려면 /config/wknd-demo/execution을 사용합니다. 서버는 요청을 수락하면 HTTP 응답 코드 202를 반환합니다. API는 서버에서 실행 중인 일괄 처리 작업에 대한 HTTP 응답 헤더의 고유 코드(실행 식별자)를 제외하고 페이로드를 반환하지 않습니다. 실행 식별자를 사용하여 배치의 상태를 검색할 수 있습니다.

>[!NOTE]
>
>일괄 처리가 실행되는 동안에는 해당 소스 및 대상 폴더, 데이터 소스 구성 및 Microsoft Azure 클라우드 구성을 변경하지 마십시오.

### 배치 상태 확인 {#status-of-a-batch}

배치 상태를 검색하려면 `GET /config /[configName]/execution/[execution-identifier]`. 실행 식별자는 일괄 실행 요청에 대한 HTTP 응답의 헤더에 포함됩니다.

상태 요청의 응답에는 상태 섹션이 포함됩니다. 배치 작업의 상태, 파이프라인에 이미 있는 레코드 수(이미 읽고 처리 중) 및 각 outputType/renderType(진행 중, 성공 및 실패한 항목 수)의 상태에 대한 세부 정보를 제공합니다. 상태에는 오류에 대한 정보와 함께 배치 작업의 시작 및 종료 시간(있는 경우)도 포함됩니다. 배치 실행이 실제로 완료될 때까지 종료 시간은 -1입니다.

>[!NOTE]
>
>* 여러 PRINT 형식을 요청할 때 상태에는 여러 항목이 포함됩니다. 예: PRINT/ZPL, PRINT/IPL.
>* 일괄 처리 작업은 모든 레코드를 동시에 읽지 않고 레코드 수를 계속 읽고 증가시킵니다. 따라서 모든 레코드를 읽을 때까지 상태는 -1을 반환합니다.

### 생성된 문서 보기 {#view-generated-documents}

작업이 완료되면 생성된 문서가 `success` 배치 데이터 저장소 구성에 지정된 대상 위치에 있는 폴더입니다. 오류가 있으면 서비스에서 `failure` 폴더를 삭제합니다. 오류 유형 및 원인에 대한 정보를 제공합니다.

입력 데이터 파일이 있다고 가정할 때 예제를 통해 이해하겠습니다. `record1.xml` 및 두 가지 출력 유형: `PDF` 및 `PCL`. 그러면 대상 위치에 두 개의 하위 폴더가 포함됩니다 `pdf` 및 `pcl`, 각 출력 유형에 대해 1개. PDF 생성이 성공했다고 가정하고 `pdf` 하위 폴더에는 `success` 실제로 생성된 PDF 문서를 포함하는 하위 폴더 `record1.pdf`. PCL 생성이 실패했다고 가정하고 `pcl` 하위 폴더에 `failure` 하위 폴더에 오류 파일이 포함됨 `record1.error.txt` - 오류에 대한 세부 정보가 포함됩니다. 또한 대상 위치에는 라는 임시 폴더가 있습니다. `__tmp__` 일괄 처리 실행 중에 필요한 특정 파일을 보관할 수 있습니다. 대상 폴더를 참조하는 활성 배치 실행이 없는 경우 이 폴더를 삭제할 수 있습니다.

>[!NOTE]
>
>입력 레코드 수와 템플릿의 복잡성에 따라 배치를 처리하는 데 시간이 걸릴 수 있습니다. 몇 분 정도 기다린 후 대상 폴더에서 출력 파일을 확인하십시오.

## API 참조 설명서

API 참조 설명서는 API에서 제공하는 모든 매개 변수, 인증 방법 및 다양한 서비스에 대한 자세한 정보를 제공합니다. API 참조 설명서는 .yaml 형식으로 사용할 수 있습니다. 다음을 다운로드할 수 있습니다. [일괄 처리 API](assets/batch-api.yaml) 파일을 만든 다음 Postman에 업로드하여 API 기능을 확인합니다.

>[!MORELIKETHIS]
>
>* [AEM Forms as a Cloud Service 커뮤니케이션 소개](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [AEM Forms as a Cloud Service 적응형 Forms 및 커뮤니케이션 아키텍처](/help/forms/aem-forms-cloud-service-architecture.md)
>* [통신 처리 - 동기 API](/help/forms/aem-forms-cloud-service-communications.md)
>* [통신 처리 - 일괄 처리 API](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)