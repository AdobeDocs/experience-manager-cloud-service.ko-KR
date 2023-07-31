---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 2721cb20083eeda7546513817f1ddfe12e9cb43a
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 89%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 일자는 2023년 6월 29일입니다. 다음 릴리스는 2023년 8월 10일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 이제 Cloud Manager 랜딩 페이지의 카드에 해당 프로그램에 대한 [향상된 보안](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) 기능이 활성화되어 있는지 여부가 표시됩니다.
* 개발 [파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)에 테스트 단계가 포함되어 있지 않은 경우 사용자는 이제 [파이프라인을 시작할 때](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) 테스트 단계를 포함할 수 있습니다.
   * 이 기능은 단계적으로 출시될 예정입니다.
* 이제 [실행을 취소할 때](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) 파이프라인 실행 승인 단계에서 사용자에게 취소 이유를 입력하도록 요청됩니다.
   * 이 기능은 단계적으로 출시될 예정입니다.
* 이제 사용자가 액세스할 수 있음 [콘텐츠 복사 프로세스에서 로그인합니다.](/help/implementing/developing/tools/content-copy.md#accessing-logs)
   * 이 옵션은 소스 및 대상 환경이 모두 AEM 버전인 경우에만 사용할 수 있습니다 `2023.7.12549` 또는 그 이상

## 버그 수정 {#bug-fixes}

* 로그인 후 Cloud Manager에서 작성 UI로 이동해도 더 이상 통합 셸로 리디렉션되지 않습니다.
* Go-Live인 위젯을 통해 Go-Live 날짜를 편집하면 이제 **향상된 보안** 탭 대신 **Go-Live** 탭으로 이동합니다.
* 복사 작업을 시작할 때 사용자는 더 이상 복사 작업이 호출되어 있는 환경을 선택할 수 없습니다.
