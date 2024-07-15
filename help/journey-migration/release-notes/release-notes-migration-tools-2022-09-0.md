---
title: AEM as a Cloud Service 릴리스 2022.9.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2022.9.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 581370ba-e3e8-487e-af83-a1eacbda2763
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 10%

---

# AEM as a Cloud Service 릴리스 2022.9.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.9.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.34의 릴리스 날짜는 2022년 9월 12일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 이제 BPA는 고객이 사용자 정의 로거 구성을 추가했는지 여부를 감지하고 보고할 수 있습니다. AEM as a Cloud Service은 사용자 지정 로그 파일을 지원하지 않습니다. 모든 로그 파일을 `error.log`에 피핑해야 합니다.
* 이제 BPA는 고객의 저장소에 있는 다양한 바이너리 MIME 유형 및 이와 관련된 카운트에 대해 보고할 수 있습니다.

### 버그 수정 {#bug-fixes-bpa}

* 단일 패턴 아래에 많은 검색 결과를 표시할 때 BPA UI에 렌더링 문제가 있습니다. 이 문제가 해결되었습니다.
* BPA가 일부 결과를 심각한 심각도를 가진 호환되지 않는 변경 내용으로 잘못 보고했습니다. 이 문제가 해결되었습니다.
