---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2022.6.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2022.6.0 릴리스 정보입니다.
feature: Release Information
exl-id: 0a348836-74cd-4fd4-aef4-6ffbd6483c24
source-git-commit: e05c2fa2cfb035ed363e2c80d4aac33b022bd435
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2022.6.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2022.6.0 릴리스 정보에 대해 간략히 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2022.6.0 릴리스 일자는 2022년 6월 9일입니다. 다음 릴리스는 2022년 6월 30일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* Cloud Manager 랜딩 페이지의 새로운 시작 카드를 통해 사용자는 테넌트와 관련된 온보딩 튜토리얼 및 진행률 지표에 빠르게 액세스할 수 있습니다.
   * 이 기능은 2022.06.0 릴리스 다음 주에 단계적으로 출시될 예정입니다.
* 필수 권한이 있는 사용자는 Cloud Manager 랜딩 페이지에서 새 [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md)에 액세스하여 테넌트가 사용할 수 있는 권한의 세부 정보를 볼 수 있습니다.
   * AEM Sites는 클라우드 관리 대시보드를 통해 가용성 및 사용량 소비를 제공하는 최초의 솔루션입니다.
   * 이 기능은 2022.06.0 릴리스 이후 몇 주에 걸쳐 단계적으로 출시될 예정입니다.
* 이제 Cloud Manager UI를 통해 [New Relic 하위 계정 및 셀프서비스 사용자 관리](/help/implementing/cloud-manager/user-access-new-relic.md)를 사용할 수 있습니다.
   * 이 기능은 2022.06.0 릴리스 이후 몇 주에 걸쳐 단계적으로 출시될 예정입니다.
* Cloud Service 프로덕션 프로그램의 홈 페이지에 있는 새로운 Go Live 위젯은 이제 성공적인 Go Live 경험을 준비하기 위한 지침을 제공합니다.
* 이제 git 미러링을 사용할 때 [빌드 아티팩트를 재사용](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse)할 수 있습니다.

## API 변경 사항 {#api-changes}

* [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) API는 더 이상 사용되지 않으며 대신 [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant)를 사용해야 합니다.
   * `List Programs`은 계속 작동하지만 사용 시 로그에 경고 메시지가 생성됩니다.
   * 3개월 후에는 더 이상 지원되지 않습니다.
