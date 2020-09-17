---
title: 클라우드 서비스로서의  [!DNL Adobe Experience Manager]  2020.9.0 릴리스의 릴리스 노트
description: 클라우드 서비스로서의 [!DNL Adobe Experience Manager] 2020.9.0 릴리스 노트
translation-type: tm+mt
source-git-commit: 529a538948f537fde8b2c50fb1f3acc942a7cb64
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 20%

---


# 클라우드 서비스 2020.9.0으로서의 [!DNL Adobe Experience Manager] 릴리스 노트 {#release-notes}

다음 섹션에서는 클라우드 서비스 2020.9.0으로서의 Experience Manager 일반 릴리스 노트를 간략하게 설명합니다.

## [!DNL Adobe Experience Manager Sites] cloud service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* 단일 페이지 애플리케이션(SPA) 편집기 Javascript SDK [가 이제 오픈 소스입니다.](/help/implementing/developing/spa/reference-materials.md)

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

* 클라우드 준비 분석기(CRA)에는 사용자가 CRA를 실행하기 위해 클릭하는 명시적 &quot;보고서 생성&quot; 단추를 표시하는 시작 상태 콘솔이 있습니다.

* 실행 중인 CRA UI에 진행률이 표시됩니다. 분석 중인 항목과 실행 중에 발견된 결과를 표시합니다.

* CRA 보고서에는 요약 및 결과의 수가 검색 유형 및 중요도 수준별로 구성된 표 형식으로 표시됩니다. 검색 결과 수를 클릭하면 보고서에서 해당 검색 결과의 위치로 자동으로 스크롤됩니다.

### 버그 수정 {#cra-bug-fixes}

* 특정 경우에는 새로 고침을 실행한 후 CRA 보고서가 업데이트되지 않았습니다. 이 버전에서 수정되었습니다.

