---
title: AEM as a Cloud Service 릴리스 2024.05.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2024.05.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
role: Admin
exl-id: f50a74fa-ad7d-4837-b0a1-9945c32af02f
source-git-commit: 3b2ed44b438fe8587a9b9603ddfacc41111fb903
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 6%

---

# AEM as a Cloud Service 릴리스 2024.05.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2024.05.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 v2.1.50의 릴리스 날짜는 2024년 5월입니다.

### 새로운 기능 {#what-is-new-bpa}

* 이제 BPA(모범 사례 분석기)는 BPA에서 생성된 보고서를 CAM(Cloud Acceleration Manager)에 직접 자동 업로드하도록 지원합니다. 사용자는 더 이상 보고서를 수동으로 다운로드하여 CAM에 업로드할 필요가 없습니다. 자세한 내용은 [모범 사례 분석기 사용](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md)을 참조하세요.

### 버그 수정 {#bug-fixes-bpa}

* 이제 Best Practices Analyzer 가 16MB 이상의 모든 노드를 감지합니다
* NCC 발견의 산발적 발생을 야기하는 경합 상태가 수정되었습니다.

## Cloud Acceleration Manager {#cam-release}

### 새로운 기능 {#what-is-new-cam}

* CAM(Cloud Acceleration Manager)은 이제 BPA에서 생성된 보고서를 CAM에 직접 자동 업로드할 수 있습니다. 자세한 내용은 [Cloud Acceleration Manager의 준비 단계 - 모범 사례 분석 카드 사용](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis)을 참조하세요.

* 이제 Cloud Acceleration Manager은 노드 수, 데이터 저장소 크기 등과 같은 요소를 고려하여 수집에 소요되는 예상 시간을 제공합니다. [Cloud Service에 콘텐츠 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)을 통해 자세히 알아보기
