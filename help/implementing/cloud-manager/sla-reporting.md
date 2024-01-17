---
title: SLA 보고
description: 계약된 SLA(서비스 수준 계약)와 관련하여 프로덕션 AEM 환경의 성능을 확인하는 방법을 알아봅니다.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
source-git-commit: 90250c13c5074422e24186baf78f84c56c9e3c4f
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 88%

---


# SLA 보고 {#sla-reporting}

계약된 SLA(서비스 수준 계약)와 관련하여 프로덕션 AEM 환경의 성능을 확인하는 방법을 알아봅니다.

## 소개 {#introduction}

SLA 보고 데이터는 **보고서** 탭을 통해 모든 프로덕션 프로그램에 사용할 수 있습니다. 액세스하려면 다음 단계를 따르십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 다음에서 **[내 프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** 화면 프로그램 선택.

1. **개요** 페이지에서 **보고서** 탭으로 이동합니다.

1. SLA 데이터를 그래프로 보려면 원하는 연도를 클릭합니다.

![SLA 그래프 예](assets/sla-reporting-1.png)

데이터 포인트 위에 커서를 놓으면 해당 포인트에 대한 특정 값이 표시됩니다.

![세부 데이터 표시](assets/sla-reporting-b.png)

## SLA 지표 {#sla-metrics}

선택한 연도의 그래프에는 여러 데이터 세트가 포함됩니다.

* **게시 계층 약정** - 게시 계층에 대해 Adobe와의 약정에 정의된 SLA입니다.

* **게시 계층 실제** - Adobe 또는 Adobe 공급업체에 의해 발생한 프로덕션 게시 계층 팩토링 인시던트의 측정된 가동 시간입니다.

* **작성자 계층 약정**: 이는 작성자 계층에 대해 Adobe Managed Services와의 약정에 정의된 SLA입니다.

* **작성자 계층 실제** - Adobe 또는 Adobe 공급업체에 의해 발생한 프로덕션 작성자 계층 팩토링 인시던트의 측정된 가동 시간입니다.

## 이벤트 분석 {#event-analysis}

이 그래프 아래의 **이벤트 분석** 섹션은 선택된 해 동안 프로그램에 대해 발생한 일련의 인시던트를 보여 줍니다.

각 인시던트에는 시간 범위, 원인 및 댓글 집합이 있습니다.

![이벤트 분석 예](assets/sla-reporting-c.png)
