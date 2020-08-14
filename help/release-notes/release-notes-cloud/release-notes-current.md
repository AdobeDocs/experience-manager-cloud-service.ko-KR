---
title: 클라우드 서비스로서의  [!DNL Adobe Experience Manager]  2020.8.0 릴리스의 릴리스 노트
description: 클라우드 서비스로서의 [!DNL Adobe Experience Manager] 2020.8.0 릴리스 노트
translation-type: tm+mt
source-git-commit: bb5bf9527da7ed9039740ef6d0bab27cfd21b84e
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 11%

---


# 클라우드 서비스 2020.8.0으로서의 [!DNL Adobe Experience Manager] 릴리스 노트 {#release-notes}

다음 섹션에서는 클라우드 서비스 2020.8.0으로서의 Experience Manager 일반 릴리스 노트를 간략하게 설명합니다.

## [!DNL Adobe Experience Manager Assets] cloud service {#assets}

* 새로운 [!DNL Experience Manager Assets] 배포는 기본적으로 [!DNL Adobe Developer Console] 통합되어 있습니다. 이 기능은 스마트 태그 기능을 보다 빠르게 구성하는 데 도움이 됩니다. 기존 배포에서 관리자는 스마트 태그 통합을 [전과 같이](/help/assets/smart-tags-configuration.md#aio-integration) 구성합니다.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 이제 제품 콘솔 기능을 사용할 수 있습니다. 이를 통해 AEM의 마케터/작성자는 상거래 백엔드에 저장된 카테고리와 제품을 보고 탐색할 수 있습니다. 제품 콘솔에서 카테고리 및 제품에 대한 속성에 대한 지원도 제공됩니다.

* 제품 및 카테고리 선택 기능이 향상되어 마케터는 SKU를 통해 제품을 선택하거나 카테고리 ID를 통해 카테고리를 선택할 수 있습니다.

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.8.0 is August 06, 2020.

### 새로운 기능 {#what-is-new-cloud-manager}

* 콘텐츠 감사는 Cloud Manager Sites 프로덕션 파이프라인에서 활성화된 기능입니다. 이제 사이트가 있는 프로그램에 대한 프로덕션 파이프라인 구성에는 컨텐츠 감사라는 세 번째 탭이 **포함됩니다**. 프로덕션 파이프라인이 실행될 때마다 사용자 정의 기능 테스트 후 새로운 컨텐츠 감사 단계가 파이프라인에 포함됩니다. 사용자 정의 기능 테스트 후에는 성능, SEO(검색 엔진 최적화), 접근성, 우수 사례 및 PWA(점진적 웹 앱)을 비롯한 다양한 차원과 사이트를 평가합니다.

   Refer to [Content Audit Testing](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) for more details.

* 자산 프로그램에서 새로 만들어진 환경은 이제 스마트 콘텐츠 서비스로 자동 구성됩니다.

* Cloud Manager의 **개요** 페이지에서 최대 절전 모드 해제 환경을 사용할 수 있습니다.

* 이제 인증 바인딩된 개인 마웬 리포지토리가 지원됩니다.

### 버그 수정 {#bug-fixes-cm}

* 불필요하고 불필요한 일부 SonarQube 플러그인이 코드 품질 스캐닝의 일부로 실행되었습니다.

* 파이프라인 실행 페이지에서 분기 이름의 형식이 잘못되었습니다.

* 경우에 따라 파이프라인 집행이 완료되었다고 기록되지 않아 파이프라인의 새로운 처형이 방지되는 경우도 있습니다.

* 가끔 내부 통신 문제로 인해 파이프라인 *실행이* 중단될 수 있습니다.

* 새 조직을 프로비저닝할 때 시스템 관리자 이외의 관리자 역할을 가진 일부 사용자에게 클라우드 관리자에 대한 액세스 권한이 잘못 부여되었습니다.

* 특정 조건에서, 업데이트 인덱스 작업이 여러 번 동시에 시작되어 배포 오류가 발생했습니다.

* 프로그램 카드에 대한 도구 설명이 일관되게 올바르지 않습니다.

* 사용자 인터페이스가 삭제되는 동안 환경에서 작업을 시도하도록 잘못 허용되었습니다.

* Cloud Manager의 **개요** 페이지에 색상이 일치하지 않습니다.

### 알려진 문제 {#known-issues-cm}

* 콘텐츠 감사 평균 점수 이하로 유도하는 잘못된 페이지가 포함됩니다.

* 컨텐츠 감사 탭에 게시 도메인 대신 작성자 도메인을 사용하여 기본 URL이 잘못 표시됩니다.

* 컨텐츠 감사 단계를 활성화하려면 파이프라인을 편집하고 선택적으로 페이지를 추가해야 합니다. 페이지가 추가되지 않으면 홈 페이지가 감사됩니다.

## 컨텐츠 전송 도구 {#content-transfer-tool}

컨텐츠 전송 도구 릴리스 v1.0.4의 새로운 기능과 업데이트에 대해 알아보려면 이 섹션을 따르십시오.

### 새로운 기능 {#what-is-new-ctt}

* 이제 콘텐츠 전송 도구가 공유 S3 DataStore를 지원합니다.

### 버그 수정 {#ctt-bug-fixes}

* 추가 시간 초과가 추가 작업에 추가되었습니다.

* 이전 버전 UI는 로그에 오류가 표시되더라도 성공적인 추출을 표시하기도 했습니다.

