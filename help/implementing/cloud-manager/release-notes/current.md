---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.9.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.9.0 릴리스 정보입니다.
feature: Release Information
source-git-commit: dd52aef2f88cf64e8d9a32b1c8cafe4fcfbcb812
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 81%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.9.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.9.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2023.9.0 릴리스 일자는 2023년 9월 7일입니다. 다음 릴리스는 2023년 10월 5일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

이 릴리스는 버그 수정에 중점을 둡니다.

## 조기 채택 프로그램 {#early-adoption}

조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 셀프서비스 콘텐츠 복원 {#content-restore}

[새로운 셀프서비스 콘텐츠 복원 기능](/help/operations/restore.md)에서 이제 최대 7일 동안 백업 복원이 제공되며 얼리 어답터는 평가 목적으로 다음 기능을 사용할 수 있습니다.

* 이전 24시간 동안 특정 시점 백업 복원
* 최대 7일 동안 고정 시간 복원

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일로 `aemcs-restorefrombackup-adopter@adobe.com`에 이메일을 보내주십시오. 참고:

* 얼리 어답터 프로그램은 개발 환경으로만 제한됩니다.
* 이 기능에 대한 얼리 어답터 프로그램의 가용성은 제한적입니다.
* 이 기능은 실수로 삭제된 콘텐츠를 복구하기 위한 것이며 재해 복구용이 아닙니다.

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)에는 개선에 도움이 되는 인사이트 및 권장 사항과 함께 페이지 성능 점수의 트렌드 보기가 포함됩니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동화 도구인 Google Lighthouse를 활용합니다. 공개 또는 인증이 필요한 모든 웹 페이지에 대해 실행할 수 있습니다. 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사가 있습니다.

새 대시보드를 테스트해 보고 싶으십니까? Adobe ID와 연결된 이메일로 `aem-lighthouse-pilot@adobe.com`에 이메일을 보내주시면 귀하의 시작을 도와드릴 수 있습니다.

## 버그 수정 {#bug-fixes}

* 프로그램이 삭제되면 연결된 실행 중인 파이프라인도 모두 삭제되어 파이프라인이 실패 상태로 잘못 지정되지 않도록 합니다.
* 경우에 따라 파이프라인 실행의 모든 단계가 &#39;완료&#39;되면 파이프라인의 상태가 &#39;실행 중&#39;으로 표시되어 중단 상태로 보일 수 있습니다. 이제 &#39;완료&#39;로 표시됩니다.
* 코드 생성기 Archetype을 사용하여 생성된 저장소 분기의 경우 CI/CD 파이프라인이 실패합니다.
