---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2020.9.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2020.9.0용 as a Cloud Service 릴리스 노트"
exl-id: 2332512f-8c52-4569-a006-faa36a7670a1
source-git-commit: bc4da79735ffa99f8c66240bfbfd7fcd69d8bc13
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 13%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 릴리스 노트  {#release-notes}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service 2020.9.0

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0은 2020년 9월 24일입니다.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### [!DNL Sites]의 새로운 기능 {#what-is-new-sites}

* SPA(Single Page Application) Editor JavaScript SDK는 이제 [오픈 소스](/help/implementing/developing/hybrid/reference-materials.md)입니다.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* 워터마크 이미지 파일은 자산 마이크로서비스에서 생성된 변환에 대해 지원됩니다. 처리 프로필로 구성할 수 있으며 PNG 파일을 워터마크로 사용합니다. 자세한 내용은 [자산 워터마크 지정](/help/assets/watermark-assets.md).

* 의 개선 사항 [!DNL Dynamic Media]

   * 선택적 게시 - 이제 마케팅 팀이 액세스할 수 있습니다 [!DNL Dynamic Media] 에 동기화된 스마트 자르기 이미지 및 동적 변환 [!DNL Dynamic Media] 따라서 자산을 게시하지 않고도 홍보 자료를 만들 수 있습니다. [!DNL Dynamic Media] 글로벌 전달을 위한 것입니다. [!DNL Experience Manager] 및 [!DNL Dynamic Media] 게시는 분리되며 이를 위해 별도로 발생할 수 있습니다. 자세한 내용은 [선택적 게시](/help/assets/dynamic-media/selective-publishing.md).
   * 이제 관리자는 재설정할 수 있습니다 [!DNL Dynamic Media] 프로비저닝 시 받은 Cloud Service 암호입니다. 재설정은 [!DNL Experience Manager] 사용자 인터페이스를 사용할 필요가 없습니다 [!DNL Dynamic Media Classic] 데스크탑 앱.

* 다음 개선 사항에 대해 알아보려면 [Brand Portal의 새로운 기능](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Adobe Document Cloud 보기 SDK 통합을 통해 PDF 미리 보기가 개선되었습니다.
   * 한 번의 클릭으로 다운로드 기능을 사용할 수 있습니다.
   * 다운로드 경험에 대한 새 관리 구성입니다.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* CIF 코어 구성 요소 v1.3.0이 출시되었습니다. 자세한 내용은 [CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) 자세한 내용

* 제품 및 카테고리 템플릿을 위한 제품/카테고리가 포함된 미리 보기 기능을 이제 사용할 수 있습니다. 이를 통해 AEM의 비즈니스 사용자/마케터는 실제 데이터로 제품/카테고리 템플릿을 볼 수 있습니다.

* 비즈니스 사용자가 제품 SKU/카테고리 ID와 관련된 세부 사항을 볼 수 있도록 제품 및 카테고리에 추가된 속성 페이지입니다.

* 제품 콘솔에 정렬 기능이 추가되어 이름 또는 가격 특성별로 제품/카테고리를 정렬할 수 있습니다.

* 제품 검색 기능이 제품 콘솔에 추가되었습니다.

### 버그 수정 {#bug-fixes-commerce}

* Commerce Cloud 구성이 상속을 준수하지 않았습니다. 구성이 값을 상속하도록 수정되었습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

에 대한 릴리스 날짜 [!UICONTROL Cloud Manager] 버전 2020.9.0은 2020년 9월 3일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}

* 컨텐츠 감사 기능은 경험 감사로 레이블이 재지정되었습니다.
* 빌드 프로세스는 세 개의 별도 Maven 명령으로 분리되었습니다.
* Git 리포지토리를 복제하지 않으면 최대 3회 다시 시도됩니다.

### 버그 수정 {#bug-fixes-cm}

* 컨텐츠 감사 탭이 게시 도메인 대신 작성 도메인을 사용하여 기본 URL을 잘못 표시합니다.

## 클라우드 준비 분석기 {#cloud-readiness-analyzer}

이 섹션을 통해 Cloud Readiness Analyzer 릴리스 버전 1.1.0에 대한 새로운 기능 및 업데이트를 알아보십시오.

### 새로운 기능 {#what-is-new-cra}

* CRA(Cloud Readiness Analyzer)에는 명시적 **보고서 생성** 버튼을 클릭하여 CRA를 실행할 수 있습니다.

* 실행 중인 CRA UI에 진행률이 표시됩니다. 분석 중인 항목과 실행 중에 발견된 결과를 표시합니다.

* CRA 보고서에는 요약 및 결과의 수가 검색 유형 및 중요도 수준별로 구성된 표 형식으로 표시됩니다. 해당 검색 결과 수를 클릭하면 보고서에서 해당 검색 결과의 위치로 자동 스크롤됩니다.

### 버그 수정 {#cra-bug-fixes}

* 특정 경우, 새로 고침을 실행한 후 CRA 보고서가 업데이트되지 않습니다. 이 문제가 이 버전에서 수정되었습니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

이 섹션을 통해 컨텐츠 전송 도구 릴리스 v1.1.10에 대한 새로운 기능 및 업데이트를 알아보십시오.

### 새로운 기능 {#what-is-new-ctt}

* CTT(컨텐츠 전송 도구)는 Azure Blob Store 데이터 저장소를 지원합니다.

* CTT 사용자 인터페이스에는 30초마다 개요 페이지를 다시 로드하는 자동 재로드 기능이 있습니다.

* 검색할 CTT 사용자 인터페이스에 단추가 추가되었습니다 *액세스 토큰* 쉽게.

* 에 설명 유효성 검사 메시지가 추가되었습니다 *URL* 및 *마이그레이션 세트 이름*.

## 코드 리팩터링 도구 {#code-refactoring}

이 섹션을 통해 새로운 기능 및 코드 리팩터링 도구에 대한 업데이트를 알아보십시오.

### 새로운 기능 {#what-is-new-refactoring}

* AIO-CLI 플러그인은 Repository Modernizer를 지원하며 사용자는 플러그인을 사용하여 도구를 실행할 수 있습니다.

   을(를) 참조하십시오. [Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) 자세한 내용

* Repository Modernizer 유틸리티를 사용하여 기존 프로젝트 패키지를 AEM as a Cloud Service에 대해 정의된 프로젝트 구조와 호환되는 패키지로 재구성할 수 있습니다.

   을(를) 참조하십시오. [Git 리소스: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) 자세한 내용
