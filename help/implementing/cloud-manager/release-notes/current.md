---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.1.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.1.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 06f534e6541bd04e005f3acf1edbb3e372c1cd0d
workflow-type: ht
source-wordcount: '673'
ht-degree: 100%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.1.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.1.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2024.1.0의 릴리스 일자는 2024년 1월 18일입니다. 다음 릴리스는 2024년 2월 16일로 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 이제 Cloud Manager는 기본 [인증서뿐만 아니라, ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) 중간 인증서의 만료 날짜도 확인합니다.
* CDN [로그](/help/implementing/cloud-manager/manage-logs.md)가 이제 압축 형식으로 반환됩니다.

## 조기 채택 프로그램 {#early-adoption}

Adobe의 조기 채택 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 실제 사용자 모니터링(RUM)을 통한 클라이언트측 컬렉션 {#rum}

[실제 사용자 모니터링(RUM) 데이터 서비스](/help/implementing/cloud-manager/content-requests.md#cliendside-collection)를 활용하여 AEM as a Cloud Service에 대한 클라이언트측 컬렉션을 활성화할 수 있습니다.

실제 사용자 모니터링(RUM) 데이터 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여에 대한 안정적인 측정을 보장합니다. 이를 통해 페이지 성능에 대한 고급 인사이트를 얻을 수 있습니다. 이는 Adobe에서 관리하는 CDN 또는 Adobe에서 관리하지 않는 CDN을 사용하는 고객에게 유용합니다. Adobe가 관리하지 않는 CDN을 사용하는 고객의 경우 이제 자동화된 트래픽 보고를 활성화할 수 있으므로 트래픽 보고서를 Adobe와 공유할 필요가 없습니다.

이러한 새 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 `aemcs-rum-adopter@adobe.com`에 이메일을 보내주십시오. 이메일에 프로덕션, 단계, 개발 환경의 도메인 이름이 포함되어야 합니다.  이 기능에 대한 얼리 어답터 프로그램의 가용성은 제한적입니다.

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

## 버그 수정 {#bug-fixes}

* 구성 파일의 위치가 제대로 설정되지 않은 경우, 명확하지 않은 오류 메시지와 함께 빌드 단계에서 구성 파이프라인이 실패하는 오류가 수정되었습니다. 이제 오류 메시지가 명확해졌으며, 사용자가 구성 파일의 위치가 올바른지 확인해야 함을 나타냅니다.
* `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR`로 인해 `FAILED` 상태로 빌드 단계가 완료되면 대상 분기와의 병합 충돌로 인해 오류로 올바르게 설명됩니다.
