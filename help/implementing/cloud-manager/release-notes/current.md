---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.12.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.12.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: b3a338f469ea04d2c31204149d619931a55f2b24
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 54%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.12.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.12.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM Cloud Manager 릴리스 2023.12.0의 as a Cloud Service 릴리스 날짜는 2023년 12월 14일입니다. 다음 릴리스는 2024년 1월 18일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* [Cloud Manager 사용자 정의 권한](/help/implementing/cloud-manager/custom-permissions.md)을 사용하여 Cloud Manager 사용자의 프로그램, 파이프라인 및 환경에 대한 액세스를 제한하는 구성 가능한 권한으로 새 사용자 정의 권한 프로필을 생성할 수 있습니다.
   * 이 기능은 2024년 2월 Cloud Manager 릴리스에서 완료될 것으로 예상됨에 따라 단계적으로 출시될 예정입니다.
   * (으)로 이메일을 보내십시오. `Grp-CloudManager-custom-permissions@adobe.com` 더 빨리 활성화하고자 하는 경우 Adobe ID과 연계된 이메일 주소에서.
* 이제 컨테이너 빌드는 Node.js 버전 18 을 지원합니다. [프론트엔드 파이프라인.](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md)
* 새로 생성된 Cloud Manager 프로그램의 경우 [연결된 New Relic 하위 계정](/help/implementing/cloud-manager/user-access-new-relic.md) 은 기본적으로 활성화되지 않습니다.
   * New Relic 하위 계정에 90일 이상 액세스하지 않은 기존 프로그램의 경우 비활성화됩니다.
   * New Relic 하위 계정을 사용하려면 Cloud Manager를 통해 옵트인해야 합니다.
* Java 8 및 11용 부 버전 롤아웃 및 Maven 업데이트 [Cloud Manager의 10월 릴리스에서 발표 및 시작](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) 완료되었습니다.
   * 프론트엔드 및 전체 스택 파이프라인에 대해 노드 18에 대한 지원이 추가되었습니다.
   * Java 8 부 버전이 다음으로 업데이트되었습니다. `jdk1.8.0_371`.
   * Java 11 부 버전이 (으)로 업데이트되었습니다. `jdk-11.0.20`.
   * Maven이 3.8.8로 업데이트되었습니다.
   * 빌드 컨테이너 기본 이미지가 Ubuntu 22.04로 업데이트되었습니다.

## 조기 채택 프로그램 {#early-adoption}

Adobe의 조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### RUM(Real User Monitoring)을 통한 클라이언트측 수집 {#rum}

다음을 활용할 수 있습니다. [RUM(Real User Monitoring) 데이터 서비스](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) 클라이언트측 컬렉션을 AEM as a Cloud Service으로 활성화하려면

RUM(Real User Monitoring) 데이터 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여를 안정적으로 측정합니다. 페이지 성능에 대한 고급 통찰력을 얻을 수 있는 좋은 기회입니다. 이는 Adobe 관리 CDN 또는 Adobe이 아닌 관리 CDN을 사용하는 고객에게 유용합니다. 비 Adobe 관리 CDN을 사용하는 고객의 경우 이제 자동화된 트래픽 보고를 사용할 수 있으므로 트래픽 보고서를 Adobe과 공유할 필요가 없습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 (으)로 이메일을 보내십시오. `aemcs-rum-adopter@adobe.com` 사용 중인 Adobe ID과 연결된 이메일 주소입니다. 이메일에 프로덕션, 스테이징 및 개발 환경의 도메인 이름을 포함하십시오.  이 기능에 대한 얼리 어답터 프로그램의 가용성은 제한적입니다.

### 자체 GitHub 가져오기 {#byo-github}

GitHub를 사용하여 저장소를 관리하는 경우, [이제 Cloud Manager를 통해 GitHub 저장소 내에서 직접 코드의 유효성을 검사할 수 있습니다.](/help/implementing/cloud-manager/managing-code/byo-github.md) 이 통합을 통해 코드를 Adobe 저장소와 지속적으로 동기화할 필요가 없으며, 기본 분기에 병합하기 전에 가져오기 요청을 확인할 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일로 `Grp-CloudManager_BYOG@adobe.com`에 이메일 주소를 보내 주십시오.

### 셀프서비스 콘텐츠 복원 {#content-restore}

[새로운 셀프서비스 콘텐츠 복원 기능](/help/operations/restore.md)에서 이제 최대 7일 동안 백업 복원이 제공되며 얼리 어답터는 평가 목적으로 다음 기능을 사용할 수 있습니다.

* 이전 24시간 동안 특정 시점 백업 복원
* 최대 7일 동안 고정 시간 복원

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일로 `aemcs-restorefrombackup-adopter@adobe.com`에 이메일을 보내 주십시오.

* 얼리 어답터 프로그램은 개발 환경으로만 제한됩니다.
* 이 기능에 대한 얼리 어답터 프로그램의 가용성은 제한적입니다.
* 이 기능은 실수로 삭제된 콘텐츠를 복구하기 위한 것이며 재해 복구용이 아닙니다.

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md)에는 개선에 도움이 되는 인사이트 및 권장 사항과 함께 페이지 성능 점수의 트렌드 보기가 포함됩니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동화 도구인 Google Lighthouse를 사용합니다. 공개 또는 인증이 필요한 모든 웹 페이지에 대해 실행할 수 있습니다. 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사가 있습니다.

새 대시보드를 테스트해 보고 싶으십니까? Adobe ID와 연결된 이메일로 `aem-lighthouse-pilot@adobe.com`에 이메일을 보내 주시면 귀하의 시작을 도와드릴 수 있습니다.
