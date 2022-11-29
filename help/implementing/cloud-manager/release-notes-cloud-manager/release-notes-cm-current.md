---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2022.12.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2022.12.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: aa7f2175e2a43a318a6171e622d292ed3a8e958b
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 38%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2022.12.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2022.12.0 릴리스 정보에 대해 간략히 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2022.12.0은 2022년 11월 29일입니다. 다음 릴리스는 2023년 1월 19일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 알림 대상 [AEM 유지 관리 업데이트](/help/overview/what-is-new-and-different.md#aem-updates) 은 Cloud Manager UI에서 표시됩니다. 이 변경 사항은 2022.12.0 릴리스 후 몇 주 내에 단계적인 방식으로 롤아웃됩니다.
* 를 통해 수집되는 경우 [CTT(컨텐츠 전송 도구)](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md) 가 진행 중인 경우 개발자 콘솔과 Cloud Manager 모두의 환경 상태가 `Ingestion in Progress`.
* 의 가용성 및 신뢰성 향상 [Cloud Manager 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 만들어졌어요

## 버그 수정 {#bug-fixes}

* 다음을 방지하기 위해 변경했습니다. [프런트엔드 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) 동일한 환경에서 파이프라인 실행이 진행 중인 동안 실행되기 때문입니다.
* 을(를) 방지하기 위해 변경했습니다. `PATCH /program//environment//variables` 을 사용하여 환경 요청 `FAILED` 상태.
