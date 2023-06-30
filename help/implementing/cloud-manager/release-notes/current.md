---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 1b46f763903a1b103837ed7e8cc498ad08ce64f1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 35%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>다음을 참조하십시오 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2023.7.0 릴리스 일자는 2023년 6월 29일입니다. 다음 릴리스는 2023년 8월 10일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 이제 Cloud Manager 랜딩 페이지의 카드에 [향상된 보안](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) 이 해당 프로그램에 대해 활성화되어 있습니다.
* 개발인 경우 [파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 에는 테스트 단계가 포함되어 있지 않습니다. 이제 사용자는 테스트 단계를 포함할 수 있습니다. [파이프라인을 시작합니다.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines)
   * 이 기능은 단계적으로 출시될 예정입니다.
* 날짜 [실행 취소,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) 이제 파이프라인 실행 승인 단계에서 사용자에게 취소 이유를 입력하도록 요청합니다.
   * 이 기능은 단계적으로 출시될 예정입니다.

## 버그 수정 {#bug-fixes}

* Cloud Manager에서 작성 UI로 이동하는 경우 로그인 후 더 이상 통합 셸로 리디렉션되지 않습니다.
* Go-Live 위젯을 통해 Go-Live 날짜를 편집하면 이제 로 이동합니다. **실행** 대신 tab 키를 누릅니다. **향상된 보안** 탭.
* 복사 작업을 시작할 때 사용자는 복사 작업이 이미 호출된 환경을 더 이상 선택할 수 없습니다.
