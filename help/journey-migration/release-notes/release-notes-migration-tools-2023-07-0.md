---
title: AEM as a Cloud Service 릴리스 2023.07.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2023.07.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: 3e5c35136c00f6050dda56c318104a7eb04fa271
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 7%

---

# AEM as a Cloud Service 릴리스 2023.07.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2023.07.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

모범 사례 분석기 v2.1.42의 릴리스 날짜는 2023년 7월 6일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 이 릴리스의 모범 사례 분석기에 여러 모범 사례 패턴이 추가되었습니다. 여기에는 다음이 포함됩니다.
   * 최소 유지 관리 작업 구성 확인
   * 장기 실행/대량 쿼리 감지
   * 실행 중 또는 부실 상태에서 많은 작성자 워크플로 감지
   * OSGI Apache Sling 작업 구성 감지
   * 사용자 지정 Guava 캐시 감지

### 버그 수정 {#bug-fixes-bpa}

* BPA를 개선하여 결과 수가 많은 보고서의 메모리 부족 보고서 생성 오류를 방지했습니다.
* BPA가 개선되어 경로에서 이스케이프 문자를 감지하여 콘텐츠를 AEM으로 as a Cloud Service으로 마이그레이션할 때 콘텐츠 수집 오류가 발생하지 않습니다.
