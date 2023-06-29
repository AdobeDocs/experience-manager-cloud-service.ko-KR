---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.6.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.6.0 릴리스 정보입니다.'
exl-id: 2c72973b-5a51-4744-bf88-50da0013ba31
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1437'
ht-degree: 45%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.6.0은 2021년 6월 28일입니다.
다음 릴리스(2021.7.0) 날짜는 2021년 7월 29일입니다.

## 릴리스 비디오 {#release-video}

다음을 살펴보십시오. [2021년 6월 릴리스 개요](https://video.tv.adobe.com/v/334296) 추가된 기능에 대한 요약을 보려면 비디오 를 사용하십시오.

## XML Documentation for AEM as a cloud Service {#xml-documentation}

### 새로운 기능 {#what-is-new-xml-documentation}

* AEMas a Cloud Service 용 XML Documentation은 이제 GA입니다.
* 이를 통해 기존 AEM Cloud Service 고객은 AEM 사이트를 비롯한 여러 채널에서 기술 콘텐츠를 가져오고, 만들고, 관리하고, 전달할 수 있는 XML Documentation addon을 확보할 수 있습니다

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.6.0 및 2021.5.0의 Cloud Manager 릴리스 정보에 대해 간략히 설명합니다.

### 릴리스 일자 {#release-date-june-cm}

AEM as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 일자는 2021년 6월 10일입니다.
다음 릴리스는 2021년 7월 15일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-junecm}

* 미리보기 서비스가 모든 프로그램에 순차적으로 배포됩니다. 고객은 미리보기 서비스에 대해 프로그램이 활성화될 때 제품 내에서 알림을 받게 됩니다. 다음을 참조하십시오 [미리보기 서비스 액세스](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) 을 참조하십시오.

* 이제 빌드 단계 중 다운로드된 Maven 종속 항목이 파이프라인 실행 사이에 캐시됩니다. 이 기능은 다음 몇 주 이내에 고객에 대해 활성화됩니다.

* 이제 프로그램 편집 대화 상자를 통해 프로그램 이름을 편집할 수 있습니다.

* 프로젝트 생성 중 및 git 워크플로 관리를 통한 기본 푸시 명령에 사용된 기본 분기 이름이 `main`으로 변경되었습니다.

* UI의 프로그램 편집 환경이 새로워졌습니다.

* 품질 규칙 `ImmutableMutableMixCheck`가 `/oak:index` 노드를 변경 불가로 분류하도록 업데이트되었습니다.

* 품질 규칙 `CQBP-84` 및 `CQBP-84--dependencies`가 단일 규칙으로 통합되었습니다. 이 통합의 일부로 종속 항목의 스캐닝이 AEM 런타임에 배포되는 서드파티 종속 항목의 문제를 보다 정확하게 식별할 수 있습니다.

* 혼란을 방지하기 위해 환경 세부 정보 페이지의 Publish AEM 행 및 Publish Dispatcher 세그먼트 행이 통합되었습니다.

  ![Dispatcher 환경](/help/implementing/cloud-manager/release-notes/assets/aem-dispatcher.png)

* `damAssetLucene` 인덱스 구조를 확인하기 위해 새 코드 품질 규칙이 추가되었습니다. 다음을 참조하십시오 [사용자 정의 DAM Asset Lucene Oak 인덱스](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) 을 참조하십시오.

* 이제 해당되는 경우 환경 세부 정보 페이지에 Publish 및 미리보기 서비스에 대한 여러 도메인 이름이 표시됩니다. 다음을 참조하십시오 [환경 세부 정보](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) 추가 세부 정보를 참조하십시오.

### 버그 수정 {#bug-fixes-junecm}

* 루트 요소 이름 뒤에 새 줄이 포함된 JCR 노드 정의가 올바르게 구문 분석되지 않았습니다.

* 목록 저장소 API가 삭제된 저장소를 필터링하지 않았습니다.

* 예약 단계에 잘못된 값이 제공되었을 때 잘못된 오류 메시지가 표시되었습니다.

* 해당 구성이 배포되지 않은 경우에도 IP 허용 목록 옆에 녹색 *활성* 상태가 표시되는 경우가 있었습니다.

* 일부 프로그램 편집 시퀀스로 인해 프로덕션 파이프라인을 만들거나 편집하지 못할 수 있습니다.

* 일부 프로그램 편집 시퀀스로 인해 **개요** 페이지에 프로그램 설정을 다시 실행하라는 잘못된 메시지가 표시될 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#ga-features-assets}

* 콘텐츠 자동화 기능을 통해 다음과 같은 작업을 수행할 수 있습니다 [!DNL Experience Manager Assets] 사용 [!DNL Adobe Creative Cloud] 규모에 맞게 에셋 제작을 자동화하는 API입니다. 동일한 에셋의 변형을 만드는 데 소요되는 시간과 필요한 반복을 크게 줄여 콘텐츠 속도를 향상시킵니다. 이 기능은 코드가 필요하지 않으며 DAM 내에서 작동합니다.
* [!DNL Adobe Asset Link] 용 v3.0 [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], 및 [!DNL Adobe InDesign] 및 [!DNL Adobe Asset Link] 용 v2.0 [!DNL Adobe XD] 이(가) 릴리스되었습니다. 다음을 제공합니다.

   * 지원 대상 [!DNL Assets Essentials].
   * 에 자동 연결 기능 [!DNL Experience Manager] as a [!DNL Cloud Service] 또는 [!DNL Assets Essentials].

<!-- TBD: Checking with PMs if AAE release should be mentioned here.
-->

### 에서 사용할 수 있는 새로운 기능 [!DNL Assets] 프리릴리스 채널 {#beta-features-assets}

* 사용자가 기본 보기와 기본 정렬 매개 변수를 선택할 수 있도록 보기 설정이 개선되었습니다.
* Linkshare 다운로드 기능은 다운로드 속도를 향상시키는 비동기 다운로드를 사용합니다.
* 사용자는 속성 술어에 따라 폴더를 검색하고 필터링할 수 있습니다.
* [!DNL Experience Manager Assets] 에서 제공하는 PDF 뷰어를 임베드합니다. [!DNL Adobe Document Cloud] 을 클릭하여 지원되는 문서를 미리 봅니다. 이 기능을 사용하면 복잡한 처리 없이 PDF 및 기타 다중 페이지 파일을 미리 볼 수 있습니다. 따라서 기능 패리티가 다음과 같이 향상됩니다. [!DNL Experience Manager] 6.5.

### [!DNL Assets]의 수정된 버그 {#bugs-fixed-assets}

* 하위 폴더에 소유자를 추가하면 [!DNL Assets] 또한 동일한 사용자를 상위 폴더의 소유자로 추가합니다. (CQ-4323737)
* 컬렉션에 에셋을 추가할 때 사용자가 컬렉션 검색에 필터를 적용하면 목록 보기에서 컬렉션을 볼 수 없습니다. (CQ-4323181)
* 파일 및 폴더를 검색할 때 사용자가 필터를 적용하고 [!UICONTROL 파일 및 폴더]에서는 파일만 표시되고 폴더는 표시되지 않습니다. (CQ-4319543)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#ga-features-sites}

* 이제 미리보기 계층에 게시 가 사이트 관리자 UI의 페이지 상태로 표시됩니다.
* 이제 [미리보기 계층에 게시]가 작업이 끝날 때 미리보기 URL을 표시하며 해당 URL을 나중에 참조할 수 있도록 페이지 속성에 유지합니다

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

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
* Apple iOS 디바이스에서 표준 HTML 업로드 필드가 포함된 양식을 제출할 경우, 때때로 파일의 콘텐츠가 전송되지 않고 반대편에서 0바이트 파일이 수신됩니다. 이 문제는 Apple iOS에서 알려진 문제입니다. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

이 섹션에서는 AEM Screens as a Cloud Service 릴리스 정보에 대해 간략히 소개합니다.

### 릴리스 일자 {#release-date-june-screens}

AEM Screens as a Cloud Service 릴리스 날짜는 2021년 6월 24일입니다.

### 새로운 기능 {#what-is-new-screens-june}

>[!NOTE]
>다음을 참조하십시오 [AEM Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html?lang=en) Screens의 성공적인 설치, 구성 및 실행에 필요한 기본 지식에 대한 설명서를 as a Cloud Service으로 제공하고 세부 개념 기술 설명서에 연결합니다.

* Bulk Device Registration Management는 대량의 플레이어 디바이스를 프로비저닝하는 것이 더 빠르고 효율적이라는 것을 의미합니다.

* 장치, 디스플레이 및 채널 인벤토리 보기 각각에 대한 검색 및 필터 옵션이 개선되었습니다.

* 디바이스 상태 스냅샷은 중요 상태를 한눈에 표시하여 시간을 절약할 수 있습니다.

* 객체 세부 정보 페이지에서는 프로젝트의 각 객체에 대해 가장 관련성이 높은 정보에 대한 요약을 제공합니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 콘텐츠 조각에 대한 새로운 CIF 제품 및 카테고리 참조 데이터 유형(포함) 제품/카테고리 선택기 UI 지원)
* 새 Commerce 콘텐츠 조각 핵심 구성 요소
* AEM 백엔드에서 전체 텍스트 상거래 검색 지원
* 상거래 핵심 구성 요소는 Adobe Commerce Sensei Recs 데이터 수집
* 범주 페이지에 대한 SEO 친화적인 URL이 개선되었습니다
* 사이트/구성당 사용자 지정 HTTP 헤더 지원

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

콘텐츠 전송 도구 v1.5.4의 릴리스 날짜는 2021년 6월 28일입니다.

### 새로운 기능 {#what-is-new-ctt-latest}

* 옵션 지원 [사전 복사](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) ctt에서 사용할 단계가 추가되었습니다. 사전 복사 단계는 소스 AEM 인스턴스가 Amazon S3 또는 Azure Blob Storage 데이터 저장소를 사용하도록 구성된 경우 컨텐츠 전송 활동의 추출 및 수집 단계를 크게 가속화하는 데 사용할 수 있습니다.

* 사용자가 수집 단계 중 위험 시점에 도달하면 수집을 중지하고 데이터를 손상시킬 수 있는 문제를 방지하기 위해 CTT에 보호 기능이 추가되었습니다.

* 추출 로그가 문제 해결에 도움이 되도록 설명했습니다.

* UI에 보다 설명적인 수집 상태 메시지가 추가되었습니다.

### 버그 수정 {#bug-fixes-ctt-latest}

* 작성자 인스턴스에서 수집을 중지하는 동안 UI가 게시 인스턴스에서 이전에 완료된 수집을 덮어쓰기하여 다음으로 전환했습니다. `STOPPED` 출처: `FINISHED`. 이 문제가 해결되었습니다.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 v2.1.16의 릴리스 날짜는 2021년 6월 30일입니다.

### 새로운 기능 {#what-is-new-bpa-latest}

* 아래 폴더에서 누락된 하위 노드 감지 및 보고 기능 `/content/dam`.

* 사용된 모범 사례 분석기 버전을 감지하고 보고하는 기능.

### 버그 수정 {#bug-fixes-bpa-latest}

* 지원되지 않는 저장소 구조(URS)와 관련된 로깅 오류가 수정되었습니다.
