---
title: AEM as a Cloud Service 릴리스 2023.09.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2023.09.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 484a60d4-a439-43d6-a23e-4a3b45ef4160
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 4%

---

# AEM as a Cloud Service 릴리스 2023.09.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2023.09.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v3.0.0의 릴리스 날짜는 2023년 9월 7일입니다.

### 새로운 기능 {#what-is-new-ctt}

다음과 같은 이점을 제공하기 위해 콘텐츠 전송 도구가 개선되었습니다.

* AzCopy를 사용하여 모든 Blob ID를 복사하는 대신 필요한 Blob ID만 복사하여 콘텐츠 저장소의 하위 집합을 마이그레이션할 때 전송 시간이 단축되었습니다.
* Oak 업그레이드를 사용하여 더 빠른 차등 콘텐츠 추가.
* 콘텐츠 수집 프로세스에서 색인화 프로세스를 분리하여 견고성을 개선했습니다. 색인화에 실패한 경우 콘텐츠를 다시 수집할 필요가 없습니다. 인덱싱만 자동으로 다시 시작되므로 상당한 시간과 노력을 절약할 수 있습니다.
