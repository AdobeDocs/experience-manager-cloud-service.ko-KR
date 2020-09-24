---
title: 클라우드 서비스로서의  [!DNL Adobe Experience Manager]  2020.9.0 릴리스의 릴리스 노트
description: 클라우드 서비스로서의 [!DNL Adobe Experience Manager] 2020.9.0 릴리스 노트
translation-type: tm+mt
source-git-commit: 9d73b8339a327643be9f2ea674857b401346087a
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 14%

---


# 클라우드 서비스 2020.9.0으로서의 [!DNL Adobe Experience Manager] 릴리스 노트 {#release-notes}

다음 섹션에서는 클라우드 서비스 2020.9.0으로서의 Experience Manager 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

The Release Date for [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 is September 24, 2020.

## [!DNL Adobe Experience Manager Sites] cloud service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* 이제 단일 페이지 애플리케이션(SPA) 편집기 JavaScript SDK [가 오픈 소스입니다.](/help/implementing/developing/spa/reference-materials.md)

## [!DNL Adobe Experience Manager Assets] cloud service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* 자산 마이크로 서비스로 생성된 변환에 대해 PNG 이미지 워터마크가 지원됩니다. 처리 프로필로 구성할 수 있습니다.

* 향상된 기능 [!DNL Dynamic Media]

   * 선택적 게시 - 이제 마케팅 팀이 글로벌 전달을 위해 이러한 자산을 게시하지 않아도 홍보 자료를 만들 수 있도록 동기화된 [!DNL Dynamic Media] 스마트 자르기 이미지 및 동적 표현물에 액세스할 [!DNL Dynamic Media] 수 [!DNL Dynamic Media] 있습니다. AEM 및 [!DNL Dynamic Media] 퍼블리싱은 분리되어 별도로 수행되므로 이를 실현할 수 있습니다.
   * 관리자는 데스크탑 앱을 사용하지 않고도 AEM UI에서 직접 프로비저닝할 때 받은 [!DNL Dynamic Media] Cloud Service 암호를 재설정할 수 [!DNL Dynamic Media Classic] 있습니다.

* 다음 개선 사항에 대해 알아보려면 브랜드 포털의 새로운 [기능을 참조하십시오](https://docs.adobe.com/content/help/ko-KR/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Adobe Document Cloud 뷰 SDK 통합을 통해 향상된 PDF 미리 보기
   * 한 번의 클릭으로 다운로드 기능을 사용할 수 있습니다.
   * 다운로드 경험에 대한 새 관리 구성

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* CIF 코어 구성 요소 v1.3.0이 출시되었습니다. 자세한 내용은 [CIF 코어 구성](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) 요소를 참조하십시오.

* 제품 및 카테고리 템플릿을 위한 제품/카테고리가 포함된 미리 보기 기능을 사용할 수 있습니다. 이를 통해 AEM의 비즈니스 사용자/마케터는 실제 데이터로 제품/카테고리 템플릿을 볼 수 있습니다.

* 비즈니스 사용자가 제품 SKU/카테고리 ID와 관련된 세부 사항을 볼 수 있도록 제품 및 카테고리에 추가된 속성 페이지입니다.

* 제품 콘솔에 정렬 기능이 추가되어 이름 또는 가격 특성별로 제품/카테고리를 정렬할 수 있습니다.

* 제품 검색 기능이 제품 콘솔에 추가되었습니다.

### 버그 수정 {#bug-fixes-commerce}

* Commerce Cloud 구성이 상속을 고려하지 않았습니다. 구성이 값을 상속하도록 수정되었습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.9.0 is September 03, 2020.

### 새로운 기능 {#what-is-new-cloud-manager}

* 콘텐츠 감사가 경험 감사로 출시되었습니다.
* 빌드 프로세스는 세 개의 개별 Maven 명령으로 분리되었습니다.
* Git 리포지토리를 복제하지 않으면 최대 3회 다시 시도됩니다.

### 버그 수정 {#bug-fixes-cm}

* 컨텐츠 감사 탭이 게시 도메인 대신 작성자 도메인을 사용하여 기본 URL을 잘못 표시했습니다.

## 클라우드 준비 분석기 {#cloud-readiness-analyzer}

이 섹션을 통해 Cloud Readiness Analyzer 릴리스 버전 1.1.0에 대한 새로운 기능 및 업데이트를 알아보십시오.

### 새로운 기능 {#what-is-new-cra}

* 클라우드 준비 분석기(CRA)에는 사용자가 CRA를 실행하기 위해 클릭하는 명시적 **보고서** 생성 단추를 표시하는 시작 상태 콘솔이 있습니다.

* 실행 중인 CRA UI에 진행률이 표시됩니다. 분석 중인 항목과 실행 중에 발견된 결과를 표시합니다.

* CRA 보고서에는 요약 및 결과의 수가 검색 유형 및 중요도 수준별로 구성된 표 형식으로 표시됩니다. 검색 결과 수를 클릭하면 보고서에서 해당 검색 결과의 위치로 자동으로 스크롤됩니다.

### 버그 수정 {#cra-bug-fixes}

* 특정 경우 새로 고침을 실행한 후 CRA 보고서가 업데이트되지 않았습니다. 이 버전에서 수정되었습니다.

## 컨텐츠 전송 도구 {#content-transfer-tool}

컨텐츠 전송 도구 릴리스 v1.1.10의 새로운 기능과 업데이트에 대해 알려면 이 섹션을 따르십시오.

### 새로운 기능 {#what-is-new-ctt}

* CTT(콘텐츠 전송 도구)는 Azure Blob 저장소 데이터 저장소를 지원합니다.

* CTT 사용자 인터페이스에는 30초마다 개요 페이지를 다시 로드하는 자동 다시 로드 기능이 있습니다.

* 액세스 토큰을 쉽게 검색하기 위해 CTT 사용자 인터페이스에 *단추를* 추가했습니다.

* URL 및 *마이그레이션 세트 이름에 대해* 설명 유효성 *검사 메시지가 추가되었습니다*.

## 코드 리팩터링 도구 {#code-refactoring}

이 섹션을 따라 새로운 기능 및 코드 리팩토링 도구에 대한 업데이트에 대해 알아보십시오.

### 새로운 기능 {#what-is-new-refactoring}

* AIO-CLI 플러그인은 Repository Modernizer를 지원하며 사용자는 플러그인을 사용하여 도구를 실행할 수 있습니다.

   Git 리소스 [를 참조하십시오.자세한 내용은 aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) 을 참조하십시오.

* Repository Modernizer 유틸리티를 사용하여 기존 프로젝트 패키지를 AEM에 대해 정의된 프로젝트 구조와 호환되는 패키지로 재구성할 수 있습니다.

   Git 리소스 [를 참조하십시오.Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) 를 참조하십시오.

