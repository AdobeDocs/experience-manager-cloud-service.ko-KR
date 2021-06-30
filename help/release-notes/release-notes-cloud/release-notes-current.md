---
title: Cloud Service [!DNL Adobe Experience Manager] 의 현재 릴리스 노트입니다.
description: Cloud Service [!DNL Adobe Experience Manager] 의 현재 릴리스 노트입니다.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: ed24f9ad81e7686f0a33260c44011628bc7c4cf9
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 3%

---


# [!DNL Adobe Experience Manager] Cloud Service의 현재 릴리스 노트 {#release-notes}

다음 섹션에서는 Cloud Service으로 현재(최신) 버전의 [!DNL Experience Manager]에 대한 일반 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>
>여기에서 이전 버전의 릴리스 정보로 이동할 수 있습니다.예를 들어, 2020년, 2021년 등의 경우입니다.

>[!NOTE]
>
>릴리스와 직접 관련이 없는 설명서 업데이트에 대한 자세한 내용은 [최근 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

[!DNL Adobe Experience Manager] as a 2021.6.0 Cloud Service의 출시일은 2021년 6월 28일입니다.
다음 릴리스(2021.7.0)는 2021년 7월 29일에 있습니다.

## 릴리스 비디오 {#release-video}

추가된 기능 요약에 대한 설명이 필요하면 [2021년 6월 릴리스 개요](https://video.tv.adobe.com/v/334296) 비디오를 보십시오.

## AEM as a cloud Service용 XML Documentation {#xml-documentation}

### 새로운 기능 {#what-is-new-xml-documentation}

* 이제 AEM as a Cloud Service에 대한 XML 설명서가 GA됩니다.
* 이를 통해 기존 AEM Cloud Service 고객은 AEM 사이트를 비롯한 여러 채널에서 기술 컨텐츠를 가져오고 만들고, 관리하고 전달하는 데 필요한 XML 설명서 추가 기능을 확보할 수 있습니다

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.6.0 및 2021.5.0 의 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-june-cm}

AEM as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 날짜는 2021년 6월 10일입니다.
다음 릴리스는 2021년 7월 15일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-junecm}

* 미리 보기 서비스는 모든 프로그램에 롤링 기반으로 배포됩니다. 미리 보기 서비스에 대해 프로그램이 활성화되면 고객에게 제품 내 알림을 보냅니다. 자세한 내용은 [미리 보기 서비스 액세스](/help/implementing/cloud-manager/manage-environments.md#access-preview-service)를 참조하십시오.

* 이제 빌드 단계 중에 다운로드한 Maven 종속성이 파이프라인 실행 간에 캐시됩니다. 이 기능은 다음 몇 주 동안 고객에 대해 활성화됩니다.

* 이제 프로그램 편집 대화 상자를 통해 프로그램 이름을 편집할 수 있습니다.

* 프로젝트를 만드는 동안 및 git 워크플로우 관리를 통한 기본 푸시 명령에 사용된 기본 분기 이름이 `main`(으)로 변경되었습니다.

* UI에서 프로그램 편집 환경을 새로 고쳤습니다.

* `/oak:index` 노드를 변경할 수 없는 것으로 분류하도록 품질 규칙 `ImmutableMutableMixCheck`이 업데이트되었습니다.

* 품질 규칙 `CQBP-84` 및 `CQBP-84--dependencies`이(가) 단일 규칙으로 통합되었습니다. 이 통합의 일부로, 종속성을 스캔하면 AEM 런타임으로 배포되는 타사 종속성의 문제를 보다 정확하게 식별할 수 있습니다.

* 혼동을 방지하기 위해 환경 세부 사항 페이지의 AEM 게시 및 Dispatcher 세그먼트 행이 통합되었습니다.

   ![](/help/onboarding/release-notes-cloud-manager/assets/aem-dispatcher.png)

* `damAssetLucene` 인덱스 구조의 유효성을 확인하기 위해 새 코드 품질 규칙이 추가되었습니다. 자세한 내용은 [사용자 지정 DAM Asset Lucene Oak 색인](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check)을 참조하십시오.

* 이제 환경 세부 사항 페이지에 게시 및 미리 보기 서비스의 여러 도메인 이름이 표시됩니다(해당하는 경우). 자세한 내용은 [환경 세부 정보](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) 를 참조하십시오.

### 버그 수정 {#bug-fixes-junecm}

* 루트 요소 이름을 올바르게 구문 분석한 후 새 행을 포함하는 JCR 노드 정의가 있습니다.

* 목록 저장소 API는 삭제된 저장소를 필터링하지 않습니다.

* 예약 단계에 잘못된 값을 제공한 경우 잘못된 오류 메시지가 표시되었습니다.

* 구성이 배포되지 않은 경우에도 IP 허용 목록 옆에 녹색 *활성* 상태가 표시될 수 있습니다.

* 일부 프로그램 편집 시퀀스는 프로덕션 파이프라인을 만들거나 편집할 수 없게 될 수 있습니다.

* 일부 프로그램 편집 시퀀스는 **개요** 페이지에 프로그램 설정을 다시 실행하기 위한 잘못된 메시지가 표시될 수 있습니다.

## [!DNL Experience Manager Assets]로서의 [!DNL Cloud Service]  {#assets}

### [!DNL Assets]의 새로운 기능 {#ga-features-assets}

* 컨텐츠 자동화 기능을 사용하여 [!DNL Experience Manager Assets] API를 활용하여 자산 프로덕션을 규모에 맞게 자동화할 수 있습니다. [!DNL Adobe Creative Cloud] 동일한 자산의 변형을 만드는 데 필요한 시간과 반복 시간을 크게 줄여 컨텐츠 속도를 향상시킵니다. 이 기능은 DAM 내에서 프로그래밍과 작업할 필요가 없습니다. [Creative Cloud 통합을 사용하여 자산의 변형 생성](/help/assets/cc-api-integration.md)을 참조하십시오.

* [[!DNL Adobe Asset Link] v3.0](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html)  [!DNL Adobe Photoshop],  [!DNL Adobe Illustrator],  [!DNL Adobe InDesign] 및  [[!DNL Adobe Asset Link] v2.0](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link-for-xd.html) 을  [!DNL Adobe XD] 사용할 수 있습니다. 다음을 제공합니다.

   * [!DNL Assets Essentials]을 지원합니다.
   * [!DNL Experience Manager]에 [!DNL Cloud Service] 또는 [!DNL Assets Essentials]로 자동 연결할 수 있습니다.

* [자산 일괄 수집 도구](/help/assets/add-assets.md#asset-bulk-ingestor)를 사용하면 일괄 수집 중에 메타데이터를 추가할 수 있습니다.

### [!DNL Assets] 사전 릴리스 채널에서 사용할 수 있는 새로운 기능 {#beta-features-assets}

* 보기 설정이 개선되어 사용자가 기본 보기와 기본 정렬 매개 변수를 선택할 수 있습니다.

   ![보기 설정에서 기본 보기 설정](/help/assets/assets/view-settings-for-defaults.png)

* Linkshare 다운로드 기능은 다운로드 속도를 높이는 비동기 다운로드를 사용합니다.

* 사용자는 속성 설명을 기반으로 폴더를 검색하고 필터링할 수 있습니다.

   ![검색 조건을 사용하여 검색 폴더 필터링](/help/assets/assets/search-folders-via-predicates.png)

* [!DNL Experience Manager Assets] 지원되는 문서 형식을 미리 보기 위해 PDF 뷰어를 포함합니다. [!DNL Adobe Document Cloud] 전원이 켜져 있습니다. 이 기능을 사용하면 복잡한 처리 없이 PDF 및 기타 다중 페이지 파일을 미리 볼 수 있습니다. 따라서 [!DNL Experience Manager] 6.5의 기능 패리티가 개선됩니다.

   ![PDF 뷰어를  [!DNL Experience Manager] 사용하여 PDF 파일 미리 보기](/help/assets/assets/preview-pdf-file-viewer.png)

* 사용자 경험 개선 사항은 폴더에 있는 자산 수를 표시합니다. 폴더에 있는 자산이 1000개 이상인 경우 [!DNL Assets]에 1000 이상이 표시됩니다.

   ![인터페이스에 폴더의 자산 수가 표시됩니다](/help/assets/assets/browse-folder-number-of-assets.png)

* 메타데이터 스키마를 [!UICONTROL 속성]의 폴더에 직접 적용할 수 있습니다.

   ![폴더 속성에서 메타데이터 스키마 추가](/help/assets/assets/metadata-schema-folder-properties.png)

### [!DNL Assets]에 수정된 버그 {#bugs-fixed-assets}

* 하위 폴더에 소유자를 추가할 때 [!DNL Assets] 은 상위 폴더의 소유자와 동일한 사용자를 추가합니다. (CQ-4323737)
* 컬렉션에 자산을 추가할 때 사용자가 컬렉션 검색 시 필터를 적용하면 사용자가 목록 보기에서 컬렉션을 볼 수 없습니다. (CQ-4323181)
* 파일 및 폴더를 검색할 때 사용자가 필터를 적용하고 [!UICONTROL 파일 및 폴더]를 선택하면 폴더만 표시되지만 폴더에는 표시되지 않습니다. (CQ-4319543)

## [!DNL Experience Manager Sites]로서의 [!DNL Cloud Service]  {#sites}

### [!DNL Sites]의 새로운 기능 {#ga-features-sites}

* 이제 미리 보기 계층에 게시 가 Sites 관리 UI에서 페이지 상태로 표시됩니다
* 미리 보기 계층에 게시 를 사용하면 이제 작업 끝에 미리 보기 URL이 표시되고 나중에 참조할 수 있도록 페이지 속성에서 URL이 유지됩니다

## [!DNL Adobe Experience Manager Forms]로서의 [!DNL Cloud Service]  {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* AEM 받은 편지함에서 사용자 지정 열을 필터링하는 기능이 추가되었습니다.
* 적응형 양식 편집기의 테마 편집기와 스타일 레이어를 사용하여 Captcha 구성 요소의 스타일을 지정하는 기능이 추가되었습니다.
* 소스 PDF forms에서 논리 섹션을 자동으로 감지하여 해당 적응형 양식 패널로 변환하는 속도와 정확도를 개선했습니다.
* PDF 또는 XDP 파일을 한 폴더에서 다른 폴더로 이동하는 이동 작업을 추가했습니다.

### [!DNL Forms] 베타 기능 {#what-is-new-forms-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**:Communication API를 사용하면 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성할 수 있습니다. 이 서비스를 통해 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.
   * XML 데이터로 템플릿 파일을 채워서 최종 양식 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
   * XFA 양식 PDF 및 Adobe Acrobat 양식(AcroForm)에서 인쇄 PDF를 생성합니다.

* **Variable Data Externalizer**:조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수의 데이터를 저장할 수 있습니다.

[!DNL formscsbeta@adobe.com]에 작성하여 베타 프로그램에 등록할 수 있습니다.

### [!DNL Forms]에 수정된 버그 {#forms-bugs-fixed}

* FDM(양식 데이터 모델)을 통해 백엔드 서비스에 데이터를 제출하기 전에 필드의 유효성을 검사하면 유효성 검사가 성공하지만 양식 데이터 모델 서비스가 사후 유효성 검사를 호출하지 못합니다.
* Apple iOS 장치에서 표준 HTML 업로드 필드가 포함된 양식을 제출하면 파일 컨텐츠가 전송되지 않고 다른 쪽에서 0바이트 파일이 수신되는 경우가 있습니다. Apple iOS에서 알려진 문제입니다. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Adobe Experience Manager Screens]로서의 [!DNL Cloud Service]  {#screens}

이 섹션에서는 AEM Screens as a Cloud Service에 대한 릴리스 노트를 간략하게 설명합니다.

### 릴리스 날짜 {#release-date-june-screens}

AEM Screens as a Cloud Service의 출시일은 2021년 6월 24일입니다.

### 새로운 기능 {#what-is-new-screens-june}

>[!NOTE]
>Screens를 Cloud Service으로 설치, 구성 및 실행하고 세부 개념 기술 설명서에 대한 링크와 함께 실행하는 데 필요한 기본 지식은 [AEM Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html?lang=en) 안내서를 참조하십시오.

* 대량 장치 등록 관리는 대량의 플레이어 장치를 제공하는 것이 더 빠르고 효율적이라는 것을 의미합니다.

* 각 장치, 표시 및 채널 인벤토리 보기에 대한 검색 및 필터 옵션이 개선되었습니다.

* 디바이스 상태 스냅샷은 중요한 상태를 한 눈에 제공하여 시간을 절약합니다.

* 객체 세부 정보 페이지에는 프로젝트의 각 객체에 대한 가장 관련성이 높은 정보가 요약되어 있습니다.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 컨텐츠 조각에 대한 새 CIF 제품 및 카테고리 참조 데이터 유형(Incl) 제품/카테고리 선택기 UI 지원)
* 새 상거래 컨텐츠 조각 코어 구성 요소
* AEM 백엔드에서 지원되는 전체 텍스트 상거래 검색
* 상거래 핵심 구성 요소 지원 Adobe Commerce Sensei Recs 데이터 수집
* 카테고리 페이지의 SEO 기반 URL이 개선되었습니다
* 사이트/구성당 사용자 지정 HTTP 헤더 지원

## 컨텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.5.4의 릴리스 날짜는 2021년 6월 28일입니다.

### 새로운 기능 {#what-is-new-ctt-latest}

* CTT에 사용할 선택적 [사전 복사](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) 단계에 대한 지원이 추가되었습니다. 사전 복사 단계는 소스 AEM 인스턴스가 Amazon S3 또는 Azure Blob 저장 공간 데이터 저장소를 사용하도록 구성된 경우 컨텐츠 전송 활동의 추출 및 수집 단계를 크게 가속화하는 데 사용할 수 있습니다.

* 사용자가 수집을 중지하지 않고 수집 단계 중 중요한 시점에 도달하면 데이터가 손상될 수 있도록 CTT에 보호 기능이 추가되었습니다.

* 추출 로그가 문제 해결에 도움이 되도록 더 설명했습니다.

* UI에 보다 설명적인 수집 상태 메시지를 추가했습니다.

### 버그 수정 {#bug-fixes-ctt-latest}

* 작성자 인스턴스에서 처리를 중지하는 동안 UI는 이전에 완료된 수집 항목을 게시 인스턴스에서 `FINISHED`의 `STOPPED`에 덮어씁니다. 이 문제가 수정되었습니다.


