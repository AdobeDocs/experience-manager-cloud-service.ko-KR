---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.10.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.10.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: b760b3a65d89b0b4f924379fc460015a58e2ed3e
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 63%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.10.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.10.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2023.10.0 릴리스 일자는 2023년 10월 5일입니다. 다음 릴리스는 2023년 11월 2일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 개선 사항 [색인화](/help/operations/indexing.md) 새 인덱스를 배포할 때 파이프라인 지속 시간이 단축되었습니다.
   * 개선 사항은 콘텐츠 프로필에 따라 다릅니다.
* 자동 [개발 환경에 대한 업데이트](/help/implementing/cloud-manager/manage-environments.md#updating-environments) 새 프로그램에 대해 기본적으로 활성화되어 업데이트를 수동으로 실행해야 하는 시간을 절약할 수 있습니다.
   * 이 업데이트는 단계적으로 배포됩니다.
* Cloud Manager의 2023년 10월 릴리스부터 단계적 롤아웃을 통해 Java 버전이 업데이트됩니다.
   * Java 8 및 11과 Maven의 부 버전이 업데이트되었으며 향후 2개월에 걸쳐 단계적으로 출시될 예정입니다. 새 버전에는 여러 보안 수정 사항 및 버그 수정이 있습니다. 새 버전은 다음과 같습니다.
   * *Maven: 3.8.8*
   * *Java 8 버전: /usr/lib/jvm/jdk1.8.0_371*
   * *Java 11 버전: /usr/lib/jvm/jdk-11.0.20*
   * [OpenJDK 설명서를 참조하십시오](https://openjdk.org/groups/vulnerability/advisories/) 이러한 JDK 업데이트의 보안 및 버그 수정에 대한 자세한 내용을 확인하십시오.

## 조기 채택 프로그램 {#early-adoption}

조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 사용자 지정 권한 {#custom-permissions}

[Cloud Manager 사용자 지정 권한](/help/implementing/cloud-manager/custom-permissions.md) 에서는 구성 가능한 권한으로 새 사용자 정의 권한 프로필을 만들어 Cloud Manager 사용자의 프로그램, 파이프라인 및 환경에 대한 액세스를 제한할 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 전자 메일을 보내십시오 `Grp-CloudManager-custom-permissions@adobe.com` (Adobe ID과 연계된 이메일 주소).

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
