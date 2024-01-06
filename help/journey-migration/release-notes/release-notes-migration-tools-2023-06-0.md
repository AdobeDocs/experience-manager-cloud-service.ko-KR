---
title: AEM as a Cloud Service 릴리스 2023.06.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2023.06.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 021b7472-d1e4-4ef6-a040-c612fed8d3c3
source-git-commit: a77e5dc4273736b969e9a4a62fcac75664495ee6
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 3%

---

# AEM as a Cloud Service 릴리스 2023.06.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2023.06.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v2.0.20의 릴리스 날짜는 2023년 6월 8일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 새로운 마이그레이션 도구인 콘텐츠 변환기(CT)가 이번 릴리스와 함께 콘텐츠 전송 도구(CTT)와 통합되었습니다. 콘텐츠 변환기는 가 보고한 콘텐츠 관련 문제를 자동으로 감지하고 해결할 수 있습니다. [Best Practices Analyzer (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=ko-KR) 현재 AEM 구현(온-프레미스 또는 Managed Services AEM)에서 as a Cloud Service으로 콘텐츠를 마이그레이션하기 전에.
콘텐츠 변환기가 제공하는 이점은 다음과 같습니다.
   * 실패 시 안전(Fail-Safe): 문제를 해결하기 위해 저장소를 수정할 때마다 콘텐츠 변환기에 의해 패키지가 생성됩니다. 필요한 경우 패키지를 설치하여 이전 상태로 되돌릴 수 있습니다.
   * 사용하기 쉬움: 콘텐츠 변환기는 콘텐츠 전송 도구와 통합되었으며 직관적인 간단한 사용자 인터페이스가 제공됩니다.
   * 시간 절약: 한 패턴 카테고리에 속하는 콘텐츠 문제가 많으면 콘텐츠 변환기를 사용하여 몇 번의 클릭으로 모두 해결할 수 있으므로 시간과 마이그레이션 복잡성을 크게 줄일 수 있습니다.
