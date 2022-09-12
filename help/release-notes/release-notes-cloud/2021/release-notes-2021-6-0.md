---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.6.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.6.0 릴리스 정보입니다.'
exl-id: 2c72973b-5a51-4744-bf88-50da0013ba31
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 25%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 이전 버전의 릴리스 정보로 이동할 수 있습니다. 예를 들어, 2020년, 2021년 등의 경우입니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.6.0은 2021년 6월 28일입니다.
다음 릴리스(2021.7.0)는 2021년 7월 29일에 있습니다.

## 릴리스 비디오 {#release-video}

을(를) 보십시오. [2021년 6월 릴리스 개요](https://video.tv.adobe.com/v/334296) 비디오 를 참조하십시오.

## XML Documentation for AEM as a cloud Service {#xml-documentation}

### 새로운 기능 {#what-is-new-xml-documentation}

* XML Documentation for AEM as a Cloud Service은 현재 GA입니다.
* 이를 통해 기존 AEM Cloud Service 고객은 AEM 사이트를 비롯한 여러 채널에서 기술 컨텐츠를 가져오고, 만들고, 관리하고, 전달하는 XML Documentation addon 을 확보할 수 있습니다

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.6.0 및 2021.5.0에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-june-cm}

AEM as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 날짜는 2021년 6월 10일입니다.
다음 릴리스는 2021년 7월 15일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-junecm}

* 미리 보기 서비스는 모든 프로그램에 롤링 기반으로 배포됩니다. 미리 보기 서비스에 대해 프로그램이 활성화되면 고객에게 제품 내 알림을 보냅니다. 을(를) 참조하십시오. [미리 보기 서비스 액세스](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) 자세한 내용

* 이제 빌드 단계 중에 다운로드한 Maven 종속성이 파이프라인 실행 간에 캐시됩니다. 이 기능은 다음 몇 주 동안 고객에 대해 활성화됩니다.

* 이제 프로그램 편집 대화 상자를 통해 프로그램 이름을 편집할 수 있습니다.

* 프로젝트를 만드는 동안 및 git 워크플로우 관리를 통한 기본 푸시 명령에 사용된 기본 분기 이름이 `main`.

* UI에서 프로그램 편집 환경을 새로 고쳤습니다.

* 품질 규칙 `ImmutableMutableMixCheck` 을(를) 분류하도록 업데이트했습니다 `/oak:index` 노드를 변경할 수 없습니다.

* 품질 규칙 `CQBP-84` 및 `CQBP-84--dependencies` 는 단일 규칙으로 통합되었습니다. 이 통합의 일부로, 종속성을 스캔하면 AEM 런타임으로 배포되는 타사 종속성의 문제를 보다 정확하게 식별할 수 있습니다.

* 혼동을 방지하기 위해 환경 세부 사항 페이지의 AEM 게시 및 Dispatcher 세그먼트 행이 통합되었습니다.

   ![](/help/implementing/cloud-manager/release-notes-cloud-manager/assets/aem-dispatcher.png)

* 구조의 유효성을 확인하기 위해 새 코드 품질 규칙이 추가되었습니다 `damAssetLucene` 인덱스. 을(를) 참조하십시오. [사용자 지정 DAM 자산 Lucene Oak 색인](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) 자세한 내용

* 이제 환경 세부 사항 페이지에 게시 및 미리 보기 서비스의 여러 도메인 이름이 표시됩니다(해당하는 경우). 을(를) 참조하십시오. [환경 세부 사항](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) 추가 정보.

### 버그 수정 {#bug-fixes-junecm}

* 루트 요소 이름을 올바르게 구문 분석한 후 새 행을 포함하는 JCR 노드 정의가 있습니다.

* 목록 저장소 API는 삭제된 저장소를 필터링하지 않습니다.

* 예약 단계에 잘못된 값을 제공한 경우 잘못된 오류 메시지가 표시되었습니다.

* 경우에 따라 사용자가 녹색으로 표시될 수 있습니다 *활성* 구성을 배포하지 않은 경우에도 IP 허용 목록 옆에 표시됩니다.

* 일부 프로그램 편집 시퀀스는 프로덕션 파이프라인을 만들거나 편집할 수 없게 될 수 있습니다.

* 일부 프로그램 편집 시퀀스는 **개요** 프로그램 설정을 다시 실행하는 데 잘못된 메시지가 표시되는 페이지입니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#ga-features-assets}

* 콘텐츠 자동화 기능을 사용하면 [!DNL Experience Manager Assets] 활용 [!DNL Adobe Creative Cloud] 자산 프로덕션을 규모에 맞게 자동화하는 API 동일한 자산의 변형을 만드는 데 필요한 시간과 반복 시간을 크게 줄여 컨텐츠 속도를 향상시킵니다. 기능은 코드가 필요하지 않으며 DAM 내에서 작동합니다.
* [!DNL Adobe Asset Link] v3.0 [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], 및 [!DNL Adobe InDesign] 및 [!DNL Adobe Asset Link] v2.0 [!DNL Adobe XD] 가 출시되었습니다. 다음을 제공합니다.

   * 지원 대상 [!DNL Assets Essentials].
   * 자동 연결 기능 [!DNL Experience Manager] 로서의 [!DNL Cloud Service] 또는 [!DNL Assets Essentials].

<!-- TBD: Checking with PMs if AAE release should be mentioned here.
-->

### 에서 사용할 수 있는 새로운 기능 [!DNL Assets] 사전 릴리스 채널 {#beta-features-assets}

* 보기 설정이 개선되어 사용자가 기본 보기와 기본 정렬 매개 변수를 선택할 수 있습니다.
* Linkshare 다운로드 기능은 다운로드 속도를 높이는 비동기 다운로드를 사용합니다.
* 사용자는 속성 설명을 기반으로 폴더를 검색하고 필터링할 수 있습니다.
* [!DNL Experience Manager Assets] 에서 제공하는 PDF 뷰어 포함 [!DNL Adobe Document Cloud] 지원되는 문서를 미리 보려면 이 기능을 사용하면 복잡한 처리 없이 PDF 및 기타 다중 페이지 파일을 미리 볼 수 있습니다. 이에 따라 기능 패리티가 다음과 개선됩니다 [!DNL Experience Manager] 6.5.

### [!DNL Assets]의 수정된 버그 {#bugs-fixed-assets}

* 하위 폴더에 소유자를 추가하면 [!DNL Assets] 또한 상위 폴더의 소유자와 동일한 사용자를 추가합니다. (CQ-4323737)
* 컬렉션에 자산을 추가할 때 사용자가 컬렉션 검색 시 필터를 적용하면 사용자가 목록 보기에서 컬렉션을 볼 수 없습니다. (CQ-4323181)
* 파일 및 폴더를 검색할 때 사용자가 필터를 적용하고 [!UICONTROL 파일 및 폴더]에는 파일만 표시되지만 폴더는 표시되지 않습니다. (CQ-4319543)

## [!DNL Experience Manager Sites] 로서의 [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#ga-features-sites}

* 이제 미리 보기 계층에 게시 가 Sites 관리 UI에서 페이지 상태로 표시됩니다
* 미리 보기 계층에 게시 를 사용하면 이제 작업 끝에 미리 보기 URL이 표시되고 나중에 참조할 수 있도록 페이지 속성에서 URL이 유지됩니다

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* AEM 받은 편지함에서 맞춤 열을 필터링할 수 있는 기능이 추가되었습니다.
* 테마 편집기를 사용해 적응형 양식 편집기 레이어를 스타일링함으로써 Captcha 구성 요소를 스타일링할 수 있는 기능이 추가되었습니다.
* 소스 PDF 양식의 논리적 섹션을 자동 감지하고 이를 해당 적응형 양식 패널로 변환하는 속도와 정확도를 개선했습니다.
* PDF 또는 XDP 파일을 폴더 간에 이동하는 이동 액션을 추가했습니다.

### [!DNL Forms]의 베타 기능 {#what-is-new-forms-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: 커뮤니케이션 API를 통해 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.
   * XML 데이터로 템플릿 파일을 채워 최종 양식 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
   * XFA 형식 PDF 및 Adobe Acrobat Form(AcroForm)에서 인쇄 PDF를 생성합니다.

* **변수 데이터 외부화**: 조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수 데이터를 저장할 수 있습니다.

Beta 프로그램에 등록하려면 [!DNL formscsbeta@adobe.com]에 문의하십시오.

### [!DNL Forms]의 수정된 버그 {#forms-bugs-fixed}

* When a field is validated before submitting data to backend service via 양식 데이터 모델(FDM)을 통해 백엔드 서비스로 데이터를 제출하기 전에 필드를 유효성 검사하는 경우, 유효성 검사는 성공하지만 양식 데이터 모델 서비스가 사후 유효성 검사를 불러오지 못합니다.
* Apple iOS 디바이스에서 표준 HTML 업로드 필드가 포함된 양식을 제출할 경우, 때때로 파일의 콘텐츠가 전송되지 않고 반대편에서 0바이트 파일이 수신됩니다. Apple iOS에서 알려진 문제입니다. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Experience Manager Screens] 로서의 [!DNL Cloud Service] {#screens}

이 섹션에서는 AEM Screens as a Cloud Service 릴리스 노트를 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-june-screens}

AEM Screens as a Cloud Service 릴리스 날짜는 2021년 6월 24일입니다.

### 새로운 기능 {#what-is-new-screens-june}

>[!NOTE]
>자세한 내용은 [AEM Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html?lang=en) Screens를 성공적으로 설치, 구성 및 실행하는 데 필요한 기본 지식을 소개하고 자세한 개념 기술 설명서에 연결합니다.

* 대량 장치 등록 관리는 대량의 플레이어 장치를 제공하는 것이 더 빠르고 효율적이라는 것을 의미합니다.

* 각 장치, 표시 및 채널 인벤토리 보기에 대한 검색 및 필터 옵션이 개선되었습니다.

* 디바이스 상태 스냅샷은 중요한 상태를 한 눈에 제공하여 시간을 절약합니다.

* 객체 세부 정보 페이지에는 프로젝트의 각 객체에 대한 가장 관련성이 높은 정보가 요약되어 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 컨텐츠 조각에 대한 새 CIF 제품 및 카테고리 참조 데이터 유형(Incl) 제품/카테고리 선택기 UI 지원)
* 새 상거래 컨텐츠 조각 코어 구성 요소
* AEM 백엔드에서 지원되는 전체 텍스트 상거래 검색
* 상거래 핵심 구성 요소 는 Adobe Commerce Sensei Recs 데이터 수집을 지원합니다
* 카테고리 페이지의 SEO 기반 URL이 개선되었습니다
* 사이트/구성당 사용자 지정 HTTP 헤더 지원

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.5.4의 릴리스 날짜는 2021년 6월 28일입니다.

### 새로운 기능 {#what-is-new-ctt-latest}

* 옵션 지원 [사전 복사](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) ctt에 사용할 단계가 추가되었습니다. 사전 복사 단계는 소스 AEM 인스턴스가 Amazon S3 또는 Azure Blob 저장 공간 데이터 저장소를 사용하도록 구성된 경우 컨텐츠 전송 활동의 추출 및 수집 단계를 크게 가속화하는 데 사용할 수 있습니다.

* 사용자가 수집을 중지하지 않고 수집 단계 중 중요한 시점에 도달하면 데이터가 손상될 수 있도록 CTT에 보호 기능이 추가되었습니다.

* 추출 로그가 문제 해결에 도움이 되도록 더 설명했습니다.

* UI에 보다 설명적인 수집 상태 메시지를 추가했습니다.

### 버그 수정 {#bug-fixes-ctt-latest}

* 작성자 인스턴스에서 수집을 정지하는 동안 UI는 이전에 완료된 수집 항목을 게시 인스턴스에서에 오버라이드했습니다. `STOPPED` 변환 전: `FINISHED`. 이 문제가 해결되었습니다.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.16 릴리스 날짜는 2021년 6월 30일입니다.

### 새로운 기능 {#what-is-new-bpa-latest}

* 아래의 폴더에서 누락된 하위 노드를 검색하고 보고하는 기능 `/content/dam`.

* 사용된 모범 사례 분석기 버전을 감지하고 보고하는 기능.

### 버그 수정 {#bug-fixes-bpa-latest}

* 지원되지 않는 URS(저장소 구조)와 관련된 로깅 오류가 수정되었습니다.
