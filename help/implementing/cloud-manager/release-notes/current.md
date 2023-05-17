---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.5.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.5.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 4340b957cea86452f916ab615b383aabacc21676
workflow-type: ht
source-wordcount: '206'
ht-degree: 100%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.5.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.5.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2023.5.0 릴리스 일자는 2023년 5월 11일입니다. 다음 릴리스는 2023년 6월 8일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 제품, 기능 및 UI 테스트 지원이 [비프로덕션 파이프라인 테스트](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)로 확장되었습니다.
* 업스트림 테스트를 활성화하는 것 외에도 [UI 테스트 지원이 Cypress 테스트로 확장되었습니다.](/help/implementing/cloud-manager/ui-testing.md)
* 이제 [셀프서비스 콘텐츠 복사](/help/implementing/developing/tools/content-copy.md)를 Cloud Manager UI를 통해 상위 환경에서 하위 환경으로 이동할 수 있습니다.
* 파이프라인 실행 유효성 검사 단계가 개선되어 실행 프로세스 초기에 복제 대기열의 상태를 검증할 수 있습니다. 이렇게 하면 작성 환경에서 AEM 관리자가 직접 해결해야 하는 차단된 대기열의 영향을 받지 않고 배포 단계를 수행할 수 있습니다.

## 버그 수정 {#bug-fixes}

* 환경 이름에 멀티바이트 문자가 사용되면 환경 생성이 더 이상 실패하지 않습니다.
