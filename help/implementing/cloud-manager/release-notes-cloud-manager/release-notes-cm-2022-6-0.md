---
title: Adobe Experience Manager as a Cloud Service Cloud Manager 2022.6.0의 릴리스 노트
description: 다음은 AEM as a Cloud Service의 Cloud Manager 2022.6.0에 대한 릴리스 노트입니다.
feature: Release Information
exl-id: 0a348836-74cd-4fd4-aef4-6ffbd6483c24
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 1%

---

# Adobe Experience Manager as a Cloud Service Cloud Manager 2022.6.0의 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2022.6.0에 대한 릴리스 노트를 문서화합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2022.6.0의 출시일은 2022년 6월 9일입니다. 다음 릴리스는 2022년 6월 30일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 이제 Cloud Manager UI에서 [셀프 서비스 콘텐츠 복원](/help/operations/backup.md) AEM 클라우드 환경의 알려진 양호한 상태로 전환합니다.
   * 이 기능은 2022.06.0 릴리스 후 몇 주에 걸쳐 단계적인 접근 방식으로 롤아웃됩니다.
* Cloud Manager 랜딩 페이지의 새로운 시작 카드를 통해 사용자는 임차인과 관련된 온보딩 자습서 및 진행 지표에 빠르게 액세스할 수 있습니다.
   * 이 기능은 2022.06.0 릴리스 후 주에 걸쳐 단계적인 접근 방식으로 롤아웃됩니다.
* 필요한 권한이 있는 사용자는 [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md) 임차인이 사용할 수 있는 권한 세부 사항을 보려면 Cloud Manager 랜딩 페이지에서 클릭하십시오.
   * AEM Sites은 클라우드 관리 대시보드를 통해 가용성 및 사용 사용량이 전달되는 첫 번째 솔루션입니다.
   * 이 기능은 2022.06.0 릴리스 후 몇 주에 걸쳐 단계적인 접근 방식으로 롤아웃됩니다.
* [새로운 Relic 하위 계정 및 셀프 서비스 사용자 관리](/help/implementing/cloud-manager/user-access-new-relic.md) 이제 Cloud Manager UI를 통해 을 사용할 수 있습니다.
   * 이 기능은 2022.06.0 릴리스 후 몇 주에 걸쳐 단계적인 접근 방식으로 롤아웃됩니다.
* 이제 Cloud Service 프로덕션 프로그램의 홈 페이지에 있는 새로운 Go Live 위젯에서 성공적인 Go Live 경험을 준비하기 위한 지침을 제공합니다.
* [이제 빌드 아티팩트를 다시 사용할 수 있습니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) git 미러링 사용 시.

## API 변경 사항 {#api-changes}

* 다음 [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) API는 더 이상 사용되지 않으며 [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) 을 대신 사용해야 합니다.
   * `List Programs` 계속 작동하지만 이 사용법은 로그에 경고 메시지를 생성합니다.
   * 3개월 이후에는 더 이상 지원되지 않습니다.
