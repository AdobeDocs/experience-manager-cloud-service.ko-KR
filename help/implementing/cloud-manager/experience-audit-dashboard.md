---
title: 경험 감사 대시보드
description: Experience Audit에서 배포 프로세스를 검증하는 방법을 알아보고, 명확하고 유용한 대시보드 인터페이스를 통해 배포된 변경 사항이 성능, 접근성, 모범 사례 및 SEO에 대한 기준 표준을 충족하는지 확인하는 데 도움이 됩니다.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 73%

---

# 경험 감사 대시보드 {#experience-audit-dashboard}


Experience Audit에서 배포 프로세스를 검증하는 방법을 알아보고, 명확하고 유용한 대시보드 인터페이스를 통해 배포된 변경 사항이 성능, 접근성, 모범 사례 및 SEO에 대한 기준 표준을 충족하는지 확인하는 데 도움이 됩니다.

>[!NOTE]
>
>이 기능은 [얼리 어답터 프로그램](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)에만 사용할 수 있습니다.
>
>AEMas a Cloud Service 의 기존 경험 감사 기능에 대한 자세한 내용은 [경험 감사 테스트](/help/implementing/cloud-manager/experience-audit-testing.md).

## 개요 {#overview}

경험 감사는 Cloud Manager Sites 프로덕션 파이프라인에서 사용할 수 있는 기능으로, 배포 프로세스를 검증하고 변경 사항이 배포되었는지 확인합니다.

1. 성능, 접근성, 모범 사례, SEO(검색 엔진 최적화) 및 PWA(점진적 웹 앱)에 대한 기준 표준을 충족합니다.

1. 회귀를 도입하지 마십시오.

Cloud Manager의 경험 감사를 통해 사이트에서 사용자의 경험을 최고 수준으로 유지할 수 있습니다.

감사 결과는 정보 제공용이며 이를 통해 배포 관리자가 점수, 현재 점수와 이전 점수 간의 변화를 확인할 수 있습니다. 이 인사이트는 현재 배포에 도입된 회귀가 있는지 확인하는 데 유용합니다.

경험 감사는 다음을 통해 제공됩니다. [Google 등대](https://developer.chrome.com/docs/lighthouse/overview/): Google의 오픈 소스 도구이며 모든 Cloud Manager 프로덕션 파이프라인에서 활성화됩니다.

>[!TIP]
>
>[파이프라인을 설정](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code)할 때 경험 감사에 포함되는 페이지를 구성합니다.

## 경험 감사 대시보드 {#dashboard}

경험 감사 결과는 다음에 나와 있습니다. **스테이지 테스트** 를 통한 프로덕션 파이프라인 단계 [프로덕션 파이프라인 실행 페이지](/help/implementing/cloud-manager/deploy-code.md).

![파이프라인의 대시보드](assets/dashboard.png)

경험 감사는 4개의 탭에 요약된 종합적이고 상세한 페이지 수준 테스트 결과를 제공합니다.

* **[Insights](#insights)**&#x200B;에는 사이트 성능을 개선하기 위해 실행 가능한 권장 사항에 대한 간략한 설명이 제공됩니다.
* **[Lighthouse 점수](#lighthouse)**&#x200B;는 이 파이프라인 실행에 배포된 코드의 Lighthouse 점수에 대한 요약입니다.
* **[페이지](#pages)**&#x200B;는 특별히 분석하도록 구성된 페이지의 성능에 대한 요약입니다.
* **[문제](#issues)**&#x200B;에는 이 파이프라인 실행 코드에서 감지된 모든 성능 문제가 요약됩니다.

### Insights {#insights}

**Insights** 탭에는 사이트 성능을 개선하기 위해 실행 가능한 권장 사항에 대한 간략한 설명이 제공됩니다.

![Insights](assets/insights.png)

다음 항목 선택 **더 보기** 단추를 클릭하여 전체 대시보드를 엽니다.

**Insights 및 권장 사항** 섹션에서 영향을 받는 페이지 비율 및 성능에서 기대할 수 있는 이득과 관련된 명확한 가치 지표와 함께 실행 가능한 권장 사항의 자세한 목록을 찾을 수 있습니다. 이를 통해 팀에 대한 이러한 권장 사항의 우선 순위를 쉽게 지정할 수 있습니다.

![Insights 및 권장 사항](assets/insights-recommendations.png)

프로덕션 파이프라인 실행 페이지로 돌아가려면 브라우저에서 뒤로 화살표를 선택하기만 하면 됩니다.

### Lighthouse 점수 {#lighthouse}

**Lighthouse 점수** 탭은 이 파이프라인 실행에 배포된 코드의 Lighthouse 점수에 대한 요약입니다.

![Lighthouse 점수](assets/lighthouse.png)

다음 항목 선택 **더 보기** 단추를 클릭하여 전체 대시보드를 엽니다.

**Lighthouse 점수** 섹션에서 다양한 점수의 트렌드 보기를 찾을 수 있습니다. **성능**, **접근성**, **PWA** 또는 **SEO**&#x200B;를 선택하여 해당 값에 대한 월별 트렌드 보기를 확인할 수 있습니다.

![Lighthouse 점수 그래프](assets/lighthouse-scores.png)

그래프의 각 지점은 해당 월의 모든 배포에 대한 평균입니다.

프로덕션 파이프라인 실행 페이지로 돌아가려면 브라우저에서 뒤로 화살표를 선택하기만 하면 됩니다.

### 페이지 {#pages}

**페이지** 탭은 특별히 분석하도록 구성된 페이지의 성능에 대한 요약입니다.

![페이지 탭](assets/pages.png)

다음 항목 선택 **더 보기** 단추를 클릭하여 전체 대시보드를 엽니다.

**페이지** 섹션에는 테스트된 페이지 목록과 최신 Lighthouse 성능 점수 및 분류가 제공됩니다.

![페이지 보기](assets/pages-view.png)

[파이프라인을 설정](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code)할 때 경험 감사에 포함되는 페이지를 구성합니다.

프로덕션 파이프라인 실행 페이지로 돌아가려면 브라우저에서 뒤로 화살표를 선택하기만 하면 됩니다.

### 문제 {#issues}

**문제** 탭에는 이 파이프라인 실행 코드에서 감지된 모든 성능 문제가 요약됩니다.

![문제 탭](assets/issues.png)

다음 항목 선택 **더 보기** 단추를 클릭하여 전체 대시보드를 엽니다.

**Insights 및 권장 사항** 섹션에서 영향을 받는 페이지 비율 및 성능에서 기대할 수 있는 이득과 관련된 명확한 가치 지표와 함께 실행 가능한 권장 사항의 더 자세한 목록을 찾을 수 있습니다. 이를 통해 팀에 대한 이러한 권장 사항의 우선 순위를 쉽게 지정할 수 있습니다.

![Insights 및 권장 사항](assets/insights-recommendations.png)

프로덕션 파이프라인 실행 페이지로 돌아가려면 브라우저에서 뒤로 화살표를 선택하기만 하면 됩니다.

### 페이지 세부 정보 {#page-detail}

의 탭 중 하나에서 페이지 링크를 선택하는 경우 **경험 감사** 파이프라인 실행 페이지 탭의 섹션 또는 **페이지** 전체 경험 감사 대시보드의 섹션에서 특정 페이지의 세부 정보를 볼 수 있습니다.

![페이지 데이터](assets/page-data.png)

이전 테스트 실행에서 변경된 사항과 함께 특정 테스트에 대해 개별 페이지의 점수를 확인할 수 있습니다.

개별 페이지의 세부 정보를 클릭하면 평가된 페이지 요소에 대한 정보와 개선 기회가 감지된 경우 문제를 해결하기 위한 지침이 제공됩니다.

프로덕션 파이프라인 실행 페이지로 돌아가려면 브라우저에서 뒤로 화살표를 선택하기만 하면 됩니다.
