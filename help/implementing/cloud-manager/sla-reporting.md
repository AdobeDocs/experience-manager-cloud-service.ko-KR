---
title: SLA 보고서
description: 계약된 서비스 수준 계약과 관련하여 프로덕션 AEM 환경의 성능을 확인하는 방법에 대해 알아봅니다.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 13%

---


# SLA 보고서 {#sla-reporting}

계약된 SLA(서비스 수준 계약)와 관련하여 프로덕션 AEM 환경의 성능을 확인하는 방법을 알아봅니다.

## SLA 보고서 보기 {#introduction}

SLA 보고서 데이터는 작성자 계층과 Publish 계층의 두 프로덕션 계층에 대한 성능 지표를 추적합니다.

선택한 연도의 선 그래프에는 1월부터 12월까지 매월 데이터 포인트가 포함됩니다. 다음 지표가 추적됩니다.

| 지표 추적됨 | 선 색상 | 설명 |
| --- | --- | --- |
| 실제 계층 작성 | 연한 녹색 | Adobe 또는 Adobe 공급업체에 의해 발생한 프로덕션 작성자 계층 팩토링 인시던트의 측정된 가동 시간입니다. |
| 작성자 계층 계약서 | 진한 파란색 | 작성자 계층에 대해 Adobe과의 계약에 정의된 SLA. |
| 실제 계층 게시 | 주황색 | Adobe 또는 Adobe 공급업체에 의해 발생한 팩토링 인시던트, 프로덕션 Publish 계층의 측정된 가동 시간입니다. |
| 계층 계약서 게시 | 빨간색 | Publish 계층에 대해 Adobe과의 계약에 정의된 SLA. |

**SLA 보고서를 보려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **프로그램 개요** 페이지의 왼쪽 메뉴에서 **보고서**&#x200B;를 클릭합니다.

1. **SLA 보고서**&#x200B;를 클릭합니다.

   ![SLA 보고서 줄 그래프](/help/implementing/cloud-manager/assets/cm-sla-report.png)

1. SLA 데이터의 선 그래프를 보려면 원하는 연도를 클릭합니다.

1. (선택 사항) 다음 중 하나를 수행합니다.

   * 선 그래프의 데이터 포인트 위에 커서를 놓으면 해당 포인트에 대한 특정 값이 표시됩니다.
   * 선 그래프의 연도 아래에서 다운로드 아이콘을 클릭하여 선 그래프의 PNG 이미지 파일을 저장합니다.
   * 해당 지표의 데이터만 보려면 지표 이름을 클릭합니다. 또는 하나 이상의 지표 이름을 선택하거나 선택 취소하는 동안 키보드에서 `Shift`을(를) 누릅니다.

   ![세부 데이터 표시](/help/implementing/cloud-manager/assets/cm-sla-download.png)

## 이벤트 분석 {#event-analysis}

그래프 아래의 **이벤트 분석** 섹션은 선택된 해 동안 프로그램에 대해 발생한 일련의 인시던트를 보여 줍니다.

각 인시던트에는 시간 범위, 원인 및 댓글 집합이 있습니다.

![이벤트 분석 예](assets/sla-reporting-c.png)

## SLA 보고서의 새로 고침 간격 {#refresh}

SLA 보고를 통해 AEM 프로덕션 환경의 성능에 대한 통찰력을 얻을 수 있으며, 이는 최신 상태이지만 즉각적인 상태는 아닙니다. SLA 보고서 생성은 매월 수행되며 `Production previous month`(으)로 표시된 새 프로그램에 대해 생성됩니다. 인스턴트 아녜요 이러한 지연으로 인해 SLA 보고서를 검토할 때 다음 사항에 유의하십시오.

* 보고된 SLA은 해당 달 동안 SLA이 변경되었더라도 해당 달이 시작되는 시점에 존재했던 것입니다.
* 프로그램이 존재하지 않아 월초에 SLA이 없었던 경우 프로그램이 생성된 날짜에 존재했던 SLA이 적용된다.

## 환경 미리보기 {#preview}

미리보기 환경은 콘텐츠 작성자가 게시하기 전에 콘텐츠의 최종 경험을 확인할 수 있는 도구입니다. 이 기능 때문에 미리보기 환경은 고가용성으로 설계되지 않았으며 관련 SLA이 없습니다.
