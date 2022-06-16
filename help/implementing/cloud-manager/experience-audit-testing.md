---
title: 경험 감사 테스트
description: Experience Auditor는 배포 프로세스를 확인하고 배포된 변경 사항이 성능, 액세스 가능성, 모범 사례 및 SEO에 대한 기본 표준을 충족하는지 확인하는 데 도움이 됩니다.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
source-git-commit: 1a7a9ee78d09a9360922a63dfa315ef9d106209e
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 1%

---


# 경험 감사 테스트 {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="경험 감사 테스트"
>abstract="Experience Auditor는 배포 프로세스를 확인하고 배포된 변경 사항이 성능, 액세스 가능성, 모범 사례 및 SEO에 대한 기본 표준을 충족하는지 확인하는 데 도움이 됩니다."

Experience Auditor는 배포 프로세스를 확인하고 배포된 변경 사항이 성능, 액세스 가능성, 모범 사례 및 SEO에 대한 기본 표준을 충족하는지 확인하는 데 도움이 됩니다.

## 개요 {#overview}

Experience Audit는 배포 프로세스를 확인하고 변경 사항이 배포되었는지 확인하는 데 도움이 되는 Cloud Manager Sites 프로덕션 파이프라인에서 사용할 수 있는 기능입니다.

1. 성능, 접근성, 우수 사례, SEO(검색 엔진 최적화) 및 PWA(점진적 웹 앱)에 대한 기본 표준을 충족합니다.

1. 회귀를 사용하지 마십시오.

Cloud Manager의 Experience Audit를 사용하면 사이트에서 최종 사용자의 경험이 가장 높은 표준이 되도록 할 수 있습니다.

감사 결과는 정보 제공용이며 배포 관리자가 현재 점수와 이전 점수 간의 점수 및 변경 사항을 확인할 수 있도록 합니다. 이 통찰력은 현재 배포와 함께 도입될 회귀 여부를 판별하는 데 유용합니다.

Experience Auditor는 Google의 오픈 소스 도구인 Google Lighthouse에서 제공하며 모든 Cloud Manager 프로덕션 파이프라인에서 활성화됩니다.

## 경험 감사 결과 이해 {#understanding-experience-audit-results}

Experience Auditor는 다음을 통해 집계 및 자세한 페이지 수준 테스트 결과를 제공합니다 [프로덕션 파이프라인 실행 페이지.](/help/implementing/cloud-manager/deploy-code.md)

* 집계 지표는 성능, 접근성, 우수 사례, SEO(검색 엔진 최적화)를 위해 감사된 페이지의 평균 점수를 측정합니다.
* 드릴다운 을 통해 개별 페이지 수준 점수를 사용할 수도 있습니다.
* 점수의 세부 사항은 식별된 문제를 해결하는 방법에 대한 지침과 함께 개별 테스트의 결과를 보는 데 사용할 수 있습니다.
* 테스트 결과 내역은 Cloud Manager 내에 유지되어 파이프라인에 도입되는 변경 사항에 이전 실행의 회귀를 포함하는지 확인합니다.

### 합계 점수 {#aggregate-scores}

합계 수준 점수는 실행에 포함된 페이지의 평균 점수를 사용합니다. 집계 수준의 변경은 실행 사이에 포함하여 구성된 페이지 컬렉션이 변경된 경우에도 현재 실행 중인 페이지의 평균 점수를 이전 실행의 점수 평균과 비교하여 나타냅니다.

성능, 접근성, SEO 및 우수 사례와 같은 각 테스트 유형에 대한 집계 수준 점수가 있습니다.

변경 지표에는 다음 값 중 하나가 있을 수 있습니다.

* **양수 값** - 마지막 프로덕션 파이프라인 실행 이후 선택한 테스트에서 페이지가 개선되었습니다.

* **음수 값** - 마지막 프로덕션 파이프라인이 실행된 이후 선택한 테스트에서 페이지가 회귀되었습니다.

* **변경 없음** - 페이지가 마지막 프로덕션 파이프라인 실행 이후 동일한 점수를 받았습니다.

* **해당 없음** - 비교할 수 있는 이전 점수가 없습니다.

![경험 감사 결과](/help/implementing/cloud-manager/assets/exp-audit-1.png)


### 페이지 수준 점수 {#page-level-scores}

테스트로 드릴다운하면 보다 자세한 페이지 수준 점수를 사용할 수 있습니다. 이전 테스트 실행의 변경 사항과 함께 특정 테스트에 대해 개별 페이지의 점수가 산정되는 방식을 확인할 수 있습니다.

개별 페이지의 세부 사항을 클릭하면 평가된 페이지의 요소에 대한 정보와 개선 기회가 감지되면 문제를 수정하는 지침을 제공합니다.

![페이지 수준 점수](/help/implementing/cloud-manager/assets/exp-audit-2.png)
