---
title: AEM as a Cloud Service 릴리스 2021.10.0의 마이그레이션 도구 릴리스 정보
description: AEM as a Cloud Service 릴리스 2021.11.0의 마이그레이션 도구 릴리스 정보
feature: Release Information
exl-id: 6b1caa63-dcb0-4c48-ab2c-fd72617abf13
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 7%

---

# AEM as a Cloud Service 릴리스 2021.10.0의 마이그레이션 도구 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2021.10.0의 마이그레이션 도구 릴리스 정보에 대해 간략히 설명합니다.

>[!NOTE]
>
>최신 릴리스 노트는 [Adobe Experience Manager as a Cloud Service 최신 릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## Cloud Acceleration Manager {#cam-release}

### 릴리스 일자 {#release-date-cam}

Cloud Acceleration Manager의 릴리스 날짜는 2021년 10월 25일입니다.

### 새로운 기능 {#what-is-new-cam}

이제 Cloud Acceleration Manager에서는 트렌드 라인 보고서에서 내역 BPA 보고서를 볼 수 있는 기능을 사용자에게 제공합니다. 이 보고서를 통해 사용자는 진행 상황을 사용하기 쉬운 그래픽 표현으로 볼 수 있습니다. 자세한 내용은 [추세선 보기 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#trendline-view-cam)을 참조하십시오.

### 릴리스 일자 {#release-date-october-cam}

Cloud Acceleration Manager의 릴리스 날짜는 2021년 10월 4일입니다.

### 새로운 기능 {#what-is-new-cam-oct}

이제 Cloud Acceleration Manager은 인쇄 가능한 미리 보기에서 BPA 보고서를 볼 수 있는 기능을 사용자에게 제공하므로 간단한 인쇄 또는 인쇄를 PDF에 제공하여 쉽게 공유할 수 있습니다. [모범 사례 분석 카드 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#best-practices-analysis)의 6단계 및 7단계를 참조하세요.


## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.6.0의 릴리스 날짜는 2021년 10월 4일입니다.

### 새로운 기능 {#what-is-new-ctt-oct}

* 아래 나열된 기능을 포함하여 간소화된 사용자 경험으로 사용자 매핑 도구가 개선되었습니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html)을 참조하세요.
   * 사용자 매핑을 실행하기 전에 사용자 관리 API에 대한 연결 테스트
   * 오류를 정상적으로 건너뛰고 사용자 매핑 활동을 계속합니다.
   * **액세스 토큰**&#x200B;이(가) 24시간 후에 만료되면 사용자 매핑이 더 이상 실패하지 않습니다. 사용자 매핑은 마지막으로 중지된 위치에서 다시 실행할 수 있습니다.

* 컨텐츠 전송 도구의 견고성을 높이기 위해 컨텐츠를 작성자 인스턴스 또는 Publish 인스턴스로 한 번에 수집할 수 있습니다. 자세한 내용은 [콘텐츠 전송 도구 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html)를 참조하십시오.

* 버전이 포함되면 감사 이벤트를 마이그레이션할 수 있도록 `/var/audit` 경로가 자동으로 포함됩니다.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa-latest}

모범 사례 분석기 v2.1.20의 릴리스 날짜는 2021년 10월 5일입니다.

### 새로운 기능 {#what-is-new-bpa-oct}

* 노드 이름 길이를 감지하고 보고하는 기능.

* 총 색인 크기를 감지하고 보고하는 기능.

* 원본 렌디션이 누락된 에셋을 감지하고 보고하는 기능.
