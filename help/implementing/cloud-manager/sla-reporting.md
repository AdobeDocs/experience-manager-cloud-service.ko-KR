---
title: SLA 보고
description: 계약된 SLA(Service Level Agreement)와 관련하여 프로덕션 AEM 환경의 성능을 확인하는 방법을 알아봅니다.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
source-git-commit: 6cf164093cc543fe4847859b248e70efd86efbb1
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 2%

---


# SLA 보고 {#sla-reporting}

계약된 SLA(Service Level Agreement)와 관련하여 프로덕션 AEM 환경의 성능을 확인하는 방법을 알아봅니다.

## 소개 {#introduction}

SLA 보고 데이터는 **보고서** 탭. 액세스하려면 다음 단계에 따르십시오.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **보고서** 탭에서 **개요** 페이지.

1. 그래프로 표시된 SLA 데이터를 보려면 원하는 연도를 클릭합니다.

![SLA 그래프 예](assets/sla-reporting-1.png)

커서를 데이터 점 위에 놓으면 해당 점에 대한 특정 값이 표시됩니다.

![자세한 데이터 표시](assets/sla-reporting-b.png)

## SLA 지표 {#sla-metrics}

선택한 연도의 그래프에는 여러 데이터 세트가 포함됩니다.

* **계층 계약 게시** - 게시 계층의 Adobe과 계약에 정의된 SLA입니다.

* **실제 게시 계층** - Adobe 또는 Adobe 공급업체이 일으킨 프로덕션 게시 계층 팩토링 사고의 측정된 가동 시간입니다.

* **작성 계층 계약** - 작성 계층에 대한 Adobe과 계약에 정의된 SLA입니다.

* **실제 작성 계층** - Adobe 또는 Adobe 공급업체이 일으킨 프로덕션 작성 계층 팩토링 사고의 측정된 가동 시간입니다.

## 이벤트 분석 {#event-analysis}

다음 **이벤트 분석** 그래프 아래의 섹션에는 선택한 연도 동안 프로그램에 대해 발생한 인시던트 세트가 표시됩니다.

각 사건에는 시간 범위, 원인 및 설명 세트가 있습니다.

![이벤트 분석 예](assets/sla-reporting-c.png)
