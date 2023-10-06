---
title: AEM as a Cloud Service 릴리스 2023.09.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2022.09.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
source-git-commit: 08e9f21022a3dcf0edfbc0ebbf76c9253b730fac
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# AEM as a Cloud Service 릴리스 2023.09.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2022.09.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v3.0.0의 릴리스 날짜는 2023년 9월 7일입니다.

### 새로운 기능 {#what-is-new-ctt}

컨텐츠 전송 도구 가 크게 향상되어 다음과 같은 이점이 있습니다.
* AzCopy를 활용하여 모든 Blob ID를 복사하는 대신 필요한 Blob ID만 복사함으로써 컨텐츠 리포지토리의 하위 집합을 마이그레이션할 때 전송 시간이 단축되었습니다
* Oak 업그레이드를 사용한 더 빠른 차등 컨텐츠 추가
* 콘텐츠 수집 프로세스에서 색인화 프로세스를 분리하여 견고성을 개선했습니다. 색인화에 실패한 경우 콘텐츠를 다시 수집할 필요가 없습니다. 인덱싱만 자동으로 다시 시작되므로 상당한 시간과 노력이 절약됩니다.
