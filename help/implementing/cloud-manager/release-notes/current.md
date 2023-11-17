---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.11.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.11.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 60%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.11.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.11.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2023.11.0 릴리스 일자는 2023년 11월 14일입니다. 다음 릴리스는 2023년 12월 7일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* AEM 이제 WAF-DDOS(Web Application Firewall-DDOS protection)를 as a Cloud Service 권한 및 [셀프서비스 방식으로 구성할 수 있습니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* 특화 [파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 이제 몇 분 내에 WAF 규칙을 포함한 트래픽 필터 규칙을 구성하고 배포할 수 있습니다.
* [콘텐츠 복사 시](/help/implementing/developing/tools/content-copy.md) 이제 더 높은 환경에서 개발 환경으로 개발 환경은 용량이 제한되어 있으므로 대용량 콘텐츠 세트를 복사할 때에는 주의해야 한다는 메시지가 표시됩니다.
* [파이프라인 실행 세부 정보 페이지](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details)에는 이제 아직 시작되지 않은 단계는 회색으로 바뀌어 모든 파이프라인 실행 단계가 표시됩니다.
* 이제 **[활동](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity)** 및 **[파이프라인](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines)** 페이지에서 실행 상태의 파이프라인을 클릭하면 파이프라인 실행 요약을 사용할 수 있습니다.
* 새 **기간** 섹션이 해당 프로그램의 과거 트렌드를 기반으로 한 파이프라인 단계의 평균 기간을 포함하는 [파이프라인 세부 정보 페이지](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details)에 추가되었습니다.
* 다음에서 [파이프라인 실행 페이지,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity-window) 이제 완료된 단계에 기간이 표시됩니다.
* 실행 [빌드 아티팩트 재사용](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) 이제 해당 아티팩트를 처음 빌드한 실행에 대한 링크가 표시됩니다.
* 선택할 옵션 **중요한 지표 실패** 이제 을(를) 구성할 수 있습니다. [코드 품질 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) 또한.


## 조기 채택 프로그램 {#early-adoption}

조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 자체 GitHub 가져오기 {#byo-github}

GitHub를 사용하여 저장소를 관리하는 경우, [이제 Cloud Manager를 통해 GitHub 저장소 내에서 직접 코드의 유효성을 검사할 수 있습니다.](/help/implementing/cloud-manager/managing-code/byo-github.md) 이 통합을 통해 코드를 Adobe 저장소와 지속적으로 동기화할 필요가 없으며, 기본 분기에 병합하기 전에 가져오기 요청을 확인할 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 다음으로 이메일을 보내십시오. `Grp-CloudManager_BYOG@adobe.com` (Adobe ID과 연계된 이메일 주소).

### 사용자 정의 권한 {#custom-permissions}

[Cloud Manager 사용자 정의 권한](/help/implementing/cloud-manager/custom-permissions.md)을 사용하여 Cloud Manager 사용자의 프로그램, 파이프라인 및 환경에 대한 액세스를 제한하는 구성 가능한 권한으로 새 사용자 정의 권한 프로필을 생성할 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 다음으로 이메일을 보내십시오. `Grp-CloudManager-custom-permissions@adobe.com` (Adobe ID과 연계된 이메일 주소).

### 셀프서비스 콘텐츠 복원 {#content-restore}

[새로운 셀프서비스 콘텐츠 복원 기능](/help/operations/restore.md)에서 이제 최대 7일 동안 백업 복원이 제공되며 얼리 어답터는 평가 목적으로 다음 기능을 사용할 수 있습니다.

* 이전 24시간 동안 특정 시점 백업 복원
* 최대 7일 동안 고정 시간 복원

이 새로운 기능을 테스트하고 피드백을 공유하려면 다음으로 이메일을 보내십시오. `aemcs-restorefrombackup-adopter@adobe.com` Adobe ID과 연계된 이메일.

* 얼리 어답터 프로그램은 개발 환경으로만 제한됩니다.
* 이 기능에 대한 얼리 어답터 프로그램의 가용성은 제한적입니다.
* 이 기능은 실수로 삭제된 콘텐츠를 복구하기 위한 것이며 재해 복구용이 아닙니다.

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)에는 개선에 도움이 되는 인사이트 및 권장 사항과 함께 페이지 성능 점수의 트렌드 보기가 포함됩니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동화 도구인 Google Lighthouse를 활용합니다. 공개 또는 인증이 필요한 모든 웹 페이지에 대해 실행할 수 있습니다. 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사가 있습니다.

새 대시보드를 테스트해 보고 싶으십니까? 다음으로 이메일 보내기 `aem-lighthouse-pilot@adobe.com` Adobe ID과 연결된 이메일을 통해 시작할 수 있습니다.

## 알려진 문제 {#known-issues}

알려진 버그 방지 기능이 있습니다. [파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md##config-deployment-pipeline) 프로덕션으로 푸시할 수 없습니다.

다음과 같은 경우 **프로덕션에 배포 전 일시 중단** 구성 파이프라인에 옵션이 필요합니다. 버그가 해결될 때까지 다음 사항을 제안하는 해결 방법입니다.

1. 파이프라인 실행.
1. 스테이징 환경에서 코드를 테스트합니다.
1. 배포 및 승인을 사용할 수 있게 되면 **거부**.
1. 파이프라인을 편집하여 **프로덕션에 배포 전 일시 중단** 옵션을 선택합니다.
1. 파이프라인을 다시 실행합니다. 스테이징에서 다시 실행된 다음 프로덕션에서 다시 실행됩니다.
