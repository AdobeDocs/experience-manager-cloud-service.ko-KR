---
title: AEM as a Cloud Service 릴리스의 마이그레이션 도구에 대한 릴리스 2021.10.0
description: AEM as a Cloud Service 릴리스의 마이그레이션 도구에 대한 릴리스 2021.11.0
feature: Release Information
exl-id: 6b1caa63-dcb0-4c48-ab2c-fd72617abf13
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 8%

---

# AEM as a Cloud Service 릴리스의 마이그레이션 도구에 대한 릴리스 2021.10.0 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 마이그레이션 도구에 대한 릴리스 노트를 간략하게 설명합니다2021.10.0.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service의 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=ko-kr).

## Cloud Acceleration Manager {#cam-release}

### 릴리스 날짜 {#release-date-cam}

Cloud Acceleration Manager의 출시일은 2021년 10월 25일입니다.

### 새로운 기능 {#what-is-new-cam}

이제 Cloud Acceleration Manager에서는 트렌드 라인 보고서에서 내역 BPA 보고서를 볼 수 있는 기능을 제공합니다. 이 보고서를 사용하면 사용자가 쉽게 그래픽 표현을 사용하여 만들고 있는 진행 상황을 볼 수 있습니다. 을(를) 참조하십시오. [트렌드 라인 보기 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#trendline-view-cam) 자세한 내용

### 릴리스 날짜 {#release-date-october-cam}

Cloud Acceleration Manager 릴리스 날짜는 2021년 10월 4일입니다.

### 새로운 기능 {#what-is-new-cam-oct}

이제 Cloud Acceleration Manager에서 BPA 보고서를 인쇄 가능한 미리 보기로 볼 수 있으므로 인쇄하거나 인쇄하여 PDF에 인쇄하여 공유하기 쉽게 할 수 있습니다. 의 6단계 및 7단계를 참조하십시오 [우수 사례 분석 카드 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).


## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.6.0의 릴리스 날짜는 2021년 10월 4일입니다.

### 새로운 기능 {#what-is-new-ctt-oct}

* 아래 나열된 다음 기능을 포함하여 간소화된 사용자 경험을 통해 사용자 매핑 도구가 개선되었습니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html).
   * 사용자 매핑을 실행하기 전에 사용자 관리 API에 대한 연결을 테스트합니다
   * 오류를 올바르게 건너뛰고 사용자 매핑 활동을 계속 진행합니다
   * 다음의 경우 사용자 매핑이 더 이상 실패하지 않습니다 **액세스 토큰** 는 24시간 후에 만료됩니다. 사용자 매핑은 마지막으로 중지된 위치에서 다시 실행할 수 있습니다.

* 컨텐츠 전송 도구의 견고성을 높이기 위해 컨텐츠를 한 번에 작성자 인스턴스 또는 게시 인스턴스에 수집할 수 있습니다. 자세한 내용은 [컨텐츠 전송 도구 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) 자세한 내용

* 버전이 포함되면 경로는 `/var/audit` 은 감사 이벤트를 마이그레이션하기 위해 자동으로 포함됩니다.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa-latest}

Best Practices Analyzer v2.1.20 릴리스 날짜는 2021년 10월 5일입니다.

### 새로운 기능 {#what-is-new-bpa-oct}

* 노드 이름 길이를 감지하고 보고할 수 있습니다.

* 총 인덱스 크기를 감지하고 보고하는 기능.

* 원래 표현물이 누락된 자산을 검색하고 보고하는 기능.
