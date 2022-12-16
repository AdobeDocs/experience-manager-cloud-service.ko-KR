---
title: AEM as a Cloud Service 릴리스 2022.9.0의 마이그레이션 도구에 대한 릴리스 노트
description: AEM as a Cloud Service 릴리스 2022.9.0의 마이그레이션 도구에 대한 릴리스 노트
feature: Release Information
source-git-commit: d6c47c3b8fe4ac994ee9f2db365888f496be12f0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 10%

---

# AEM as a Cloud Service 릴리스 2022.9.0의 마이그레이션 도구에 대한 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.9.0의 마이그레이션 도구에 대한 릴리스 노트를 간략하게 설명합니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.34의 출시일은 2022년 9월 12일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 이제 BPA는 고객이 사용자 지정 로거 구성을 추가했는지 여부를 감지하고 보고할 수 있습니다. AEM as a Cloud Service은 사용자 지정 로그 파일을 지원하지 않습니다. 모든 로그 파일은에 전송해야 합니다. `error.log`
* 이제 BPA는 고객 저장소에 있는 다른 이진 MIME 유형에 대해 보고하고 해당 유형과 관련된 카운트를 보고할 수 있습니다.

### 버그 수정 {#bug-fixes-bpa}

* 단일 패턴으로 많은 수의 검색 결과를 표시할 때 BPA UI에 렌더링 문제가 있었습니다. 이 문제가 해결되었습니다.
* BPA가 일부 결과를 심각한 심각도와 호환되지 않는 변경이라고 잘못 보고했습니다. 이 문제가 해결되었습니다.
