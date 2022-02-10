---
title: AEM as a Cloud Service 릴리스 2022.02.0의 Cloud Manager 릴리스 노트
description: 다음은 AEM as a Cloud Service 릴리스의 Cloud Manager에 대한 릴리스 2022.02.0.
feature: Release Information
source-git-commit: d1fe713f0c35a96cf6ba3172ea11986fd9d42fd6
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 2%

---


# Adobe Experience Manager as a Cloud Service 2022.02.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2022.02.0의 Cloud Manager 릴리스 날짜는 2022년 2월 10일입니다. 다음 릴리스는 2022년 3월 10일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 새로운 가속 [웹 계층 구성 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) 은 HTTPD/dispatcher 구성을 독점적으로 배포하기 위해 도입되었습니다.
   * AEM 버전을 사용해야 합니다. `2021.12.6151.20211217T120950Z` 또는 이상 [dispatcher 도구의 유연한 모드로 옵트인합니다.](/help/implementing/dispatcher/disp-overview.md#validation-debug) 을 클릭하여 이 기능을 사용할 수 있습니다.
   * 이 기능은 2022.02.0 릴리스 후 2주에 걸쳐 단계적인 접근 방식으로 롤아웃됩니다.
* Cloud Manager 랜딩 페이지 환경을 새로 고쳐 향상된 탐색, 그리드/타일 보기 및 팝업 오버를 제공하여 빠른 프로그램 요약을 제공합니다.
* 실패한 새 임계값(`< D`)이 에 추가되었습니다. [신뢰성 등급 지표.](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)
   * 시스템 안정성에 영향을 주는 심각한 품질 문제가 있는 고객(주로 잘못된 인덱스 및 워크플로우 프로세스와 관련이 있음)은 이러한 문제가 해결될 때까지 배포할 수 없습니다.
* 의 심각도 `BannedPath` [품질 규칙](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) 이 차단기에서 위험으로 변경되었습니다.
* 파이프라인 마법사는 를 구성하기 전에 AEM 환경 업데이트가 필요할 수 있음을 사용자에게 알려줍니다 [웹 계층 구성 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) 관련 항목.

## 버그 수정 {#bug-fixes}

* 새 암호가 생성되면 이전 Git 리포지토리 암호가 항상 무효화됩니다.
* API를 통해 환경 변수를 업데이트해도 드물게 발생하는 경우 파이프라인 실행이 더 이상 방해되지 않습니다.
