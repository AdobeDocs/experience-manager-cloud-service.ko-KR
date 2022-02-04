---
title: AEM as a Cloud Service 릴리스 2022.2.0의 마이그레이션 도구에 대한 릴리스 노트
description: AEM as a Cloud Service 릴리스 2022.2.0의 마이그레이션 도구에 대한 릴리스 노트
feature: Release Information
source-git-commit: 8876702f1a172282fd1ff46387ade2a45e187fed
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 7%

---


# AEM as a Cloud Service 릴리스 2022.2.0의 마이그레이션 도구에 대한 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.2.0의 마이그레이션 도구에 대한 릴리스 노트를 간략하게 설명합니다.

## 모범 사례 분석기 {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.24 릴리스 날짜는 2022년 2월 1일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 스마트 태그가 있는 자산 및 없는 자산 수를 감지하고 보고하는 기능.
* 사용된 코어 구성 요소 버전을 감지하고 보고할 수 있습니다.
* BPA가 실행된 소스 계층(작성자 또는 게시)의 유형을 감지하고 보고하는 기능.

### 버그 수정 {#bug-fixes-bpa}

* BPA 크기 조정 로직이 더 빠르고 효율적으로 만들어졌습니다.
* 일부 시나리오에서 BPA는 실행 시 분석된 카운트를 증가시키지 않았습니다. 이 문제가 수정되었습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v1.8.6의 릴리스 날짜는 2022년 2월 3일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 컨텐츠 유효성 검사 - 사용자는 컨텐츠 전송 도구에서 추출한 모든 컨텐츠를 대상 인스턴스에 성공적으로 수집했는지 여부를 안정적으로 확인할 수 있습니다. 이 기능을 사용하려면, `System Console` 소스 AEM 환경의 구성 요소 을(를) 참조하십시오. [컨텐츠 전송 확인 - 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=en#getting-started) 자세한 내용

### 버그 수정 {#bug-fixes-ctt}

* 사용자 매핑은 대/소문자를 구분하므로 일부 사용자가 매핑되지 않았습니다. 이 문제가 수정되었습니다. 사용자 매핑은 더 이상 대/소문자를 구분하지 않습니다.

