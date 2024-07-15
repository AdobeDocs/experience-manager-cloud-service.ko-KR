---
title: AEM as a Cloud Service 릴리스 2022.2.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2022.2.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: b1cd871d-c71e-4902-a97e-2c859f6a4da4
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 55%

---

# AEM as a Cloud Service 릴리스 2022.2.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.2.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

우수 사례 분석기 v2.1.24의 릴리스 날짜는 2022년 2월 1일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 스마트 태그가 있거나 없는 에셋 수를 감지하고 보고하는 기능.
* 사용된 핵심 구성 요소 버전 감지 및 보고 기능.
* BPA가 실행된 소스 계층 유형(작성자 또는 게시)을 감지하고 보고하는 기능.

### 버그 수정 {#bug-fixes-bpa}

* BPA 크기 조정 논리는 더 빠르고 효율적으로 만들어졌습니다.
* 일부 시나리오에서는 BPA가 실행될 때 분석된 수를 증가시키지 않았습니다. 이 문제가 해결되었습니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

콘텐츠 전송 도구 v1.8.6의 릴리스 날짜는 2022년 2월 3일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 콘텐츠 유효성 검사 - 사용자는 콘텐츠 전송 도구에서 추출한 모든 콘텐츠가 대상 인스턴스에 성공적으로 수집되었는지 확인할 수 있습니다. 이 기능을 사용하려면 원본 AEM 환경의 `System Console`에서 활성화하십시오. 자세한 내용은 [콘텐츠 전송 확인 - 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html#getting-started)를 참조하십시오.

### 버그 수정 {#bug-fixes-ctt}

* 사용자 매핑이 대소문자를 구분하기 때문에 일부 사용자가 매핑되지 않았습니다. 이 문제가 해결되었습니다. 사용자 매핑은 더 이상 대소문자를 구분하지 않습니다.
