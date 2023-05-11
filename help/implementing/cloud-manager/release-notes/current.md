---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.5.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.5.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 4340b957cea86452f916ab615b383aabacc21676
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 41%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.5.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.5.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2023.5.0의 릴리스 날짜는 2023년 5월 11일입니다. 다음 릴리스는 2023년 6월 8일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 제품, 기능 및 UI 테스트 지원이 [비프로덕션 파이프라인 테스트.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
* 업스트림을 테스트할 뿐만 아니라 [UI 테스트 지원이 Cypress 테스트까지 확장되었습니다.](/help/implementing/cloud-manager/ui-testing.md)
* [셀프 서비스 콘텐츠 복사](/help/implementing/developing/tools/content-copy.md) 이제 Cloud Manager UI를 통해 더 높은 환경에서 더 낮은 환경으로 이동할 수 있습니다.
* 실행 프로세스 초기에 복제 큐의 상태를 확인하기 위해 파이프라인 실행 유효성 검사 단계가 개선되었습니다. 이렇게 하면 작성 환경에서 AEM 관리자 사용자가 직접 해결해야 하는 차단된 큐의 영향을 받지 않습니다.

## 버그 수정 {#bug-fixes}

* 환경 이름에 멀티바이트 문자가 사용되는 경우 더 이상 환경 작성에 실패하지 않습니다.
