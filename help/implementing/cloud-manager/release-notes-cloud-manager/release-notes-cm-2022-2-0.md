---
title: AEM as a Cloud Service 릴리스 2022.02.0의 Cloud Manager 릴리스 노트
description: 다음은 AEM as a Cloud Service 릴리스의 Cloud Manager에 대한 릴리스 2022.02.0.
feature: Release Information
exl-id: da0643a0-78f8-4e9d-9cc9-a1a17067a08c
source-git-commit: 0c4a42595800f7f1d0869bf647c3ec99023b12c5
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 67%

---

# Adobe Experience Manager as a Cloud Service 2022.02.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2022.02.0의 Cloud Manager 릴리스 날짜는 2022년 2월 10일입니다. 다음 릴리스는 2022년 3월 10일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 가속화된 [웹 계층 구성 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines)이 새로 도입되어 HTTPD/dispatcher 구성을 독점적으로 배포할 수 있습니다.
   * 이 기능을 사용하려면 AEM 버전 `2021.12.6151.20211217T120950Z` 이상을 사용하고 [유연한 Dispatcher 도구 모드를 옵트인](/help/implementing/dispatcher/disp-overview.md#validation-debug)해야 합니다.
   * 이 기능은 2022.02.0 출시 후 2 주에 걸쳐 주 단계별 접근 방식으로 제공될 예정입니다.
* Cloud Manage 랜딩 페이지 경험이 새로워져 탐색 기능이 개선되고, 간단하게 그리드/타일 보기로 전환되고, 빠른 프로그램 요약을 위한 팝업이 제공됩니다.
* 새 실패 임계값(`< D`)이 [안정성 평가 지표](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)에 추가되었습니다.
   * 주로 잘못된 인덱스 및 워크플로 프로세스와 관련하여, 시스템 안정성에 영향을 미치는 심각한 품질 문제가 발생하면 고객은 해당 문제가 해결될 때까지 배포할 수 없습니다.
* `BannedPath` [품질 규칙](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)의 심각도가 차단에서 심각으로 변경되었습니다.
* 파이프라인 마법사는 관련 [웹 계층 구성 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines)을 구성하기 전에 AEM 환경 업데이트가 필요한 시기를 사용자에게 알려줍니다.

## 버그 수정 {#bug-fixes}

* 새 암호가 생성되면 이제 기존 Git 저장소 암호는 항상 무효화됩니다.
* API를 통해 환경 변수를 업데이트하면 특수한 환경에서는 파이프라인이 더 이상 실행되지 않습니다.
