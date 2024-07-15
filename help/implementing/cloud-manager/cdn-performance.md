---
title: CDN 성능 대시보드
description: Cloud Manager이 컨텐츠 전달 네트워크(CDN) 성능을 평가하는 방법과 대시보드에서 학습할 수 있는 내용을 이해합니다.
exl-id: ecd8c1ca-873f-4e73-ad73-b5f7561eb109
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 4%

---

# CDN 성능 대시보드 {#cdn-performance}

Cloud Manager이 컨텐츠 전달 네트워크(CDN) 성능을 평가하는 방법과 대시보드에서 학습할 수 있는 내용을 이해합니다.

## 개요 {#overview}

모든 Cloud Manager 프로그램에는 CDN 성능 대시보드가 있습니다. 이 대시보드에는 CDN 성능에 대한 전체 점수와 함께 필요한 경우 개선 사항에 대한 트렌드, 경고 및 제안이 표시됩니다.

![CDN 성능 대시보드](assets/cdn-performance-dashboard.png)

## 대시보드 액세스 {#accessing}

CDN 대시보드는 모든 프로그램의 개요 페이지에서 사용할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 보려는 CDN 대시보드의 프로그램을 탭하거나 클릭합니다.

   ![내 프로그램 페이지](assets/my-programs.png)

1. 프로그램의 **프로그램 개요** 페이지에서 **환경** 및 **파이프라인** 카드 아래로 스크롤하여 **성능** 카드를 확인합니다.

   ![성능](assets/cdn-performance-overview.png)

## 대시보드 사용 {#using}

대시보드에는 CDN 성능에 대한 전반적인 점수와 함께 필요한 경우 개선 사항에 대한 트렌드, 경고 및 제안이 표시됩니다.

![CDN 성능 대시보드](assets/cdn-performance-dashboard.png)

CDN 성능에 대한 세부 정보와 개선 방법에 대한 제안을 보려면 **트렌드 보기**&#x200B;를 탭하거나 클릭합니다.

![성능 트렌드](assets/cdn-performance-trend.png)

차트 아래의 **보기**&#x200B;를 탭하거나 클릭하여 차트의 시간 범위를 변경합니다.

CDN 성능을 향상시키는 방법에 대한 제안 사항은 **Recommendations** 탭을 선택하십시오.

![CDN 권장 사항](assets/cdn-performance-recommendations.png)

개선해야 할 단계 및 문제의 원인에 대한 세부 정보를 보려면 목록에서 권장 사항 옆에 있는 V자형 화살표를 탭하거나 클릭합니다.

## 캐시 적중 정의 {#cache-hit}

캐시 적중률은 캐시가 수신하는 요청 수와 비교하여 캐시가 성공적으로 채울 수 있는 콘텐츠 요청 수를 측정한 것입니다. 캐시 적중률이 높을수록 CDN 성능이 향상됩니다.

>[!TIP]
>
>Adobe은 사용자가 99%의 캐시 적중률을 목표로 할 것을 권장합니다.

```text
Cache Hit Ratio = Cache Hits / (Hits + Misses + Passes + Other)
```

* **히트** - 캐시에서 데이터가 요청되었으며 검색되었습니다.
* **Miss** - 캐시에서 데이터를 요청했지만 찾을 수 없습니다.
* **통과** - 캐시에서 데이터가 요청되며 어떤 경우에도 이 데이터를 캐싱하지 않도록 설정됩니다.
* **기타** - 캐시의 모든 데이터 요청이 다른 사례와 일치하지 않습니다.

캐시 지표는 24시간마다 업데이트됩니다.

>[!TIP]
>
>Cloud Manager 및 CDN이 Dispatcher과 상호 작용하는 방법에 대한 자세한 내용은 [AEM as a Cloud Service의 캐싱](/help/implementing/dispatcher/caching.md) 문서를 참조하십시오.
