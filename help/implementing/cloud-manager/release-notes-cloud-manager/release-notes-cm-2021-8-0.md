---
title: AEM as a Cloud Service 릴리스 2021.8.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.8.0의 Cloud Manager 릴리스 노트
feature: Release Information
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: 07a80076493070cb5e754a4cfbafe51cfcd6442e
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 4%

---

# Adobe Experience Manager as a Cloud Service 2021.8.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2021.8.0 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service에 대한 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR)를 클릭하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.8.0의 Cloud Manager 릴리스 날짜는 2021년 8월 12일입니다.
다음 릴리스는 2021년 9월 9일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new}

* 이제 Cloud Service 고객은 Cloud Manager에서 SLA(서비스 수준 계약) 보고서를 볼 수 있습니다. 이 기능은 다음 몇 달 동안 점진적으로 제공될 예정입니다.
자세한 내용은 [SLA 보고](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html)를 참조하십시오.

* IndexType 및 `IndexDamAssetLucene` 품질 규칙의 유형과 심각도가 변경되었습니다. 이제 Blocker *serverity*&#x200B;의 버그가 둘 다 있습니다.

* 비동기 및 tika 구성을 다루는 새로운 Oak 색인 품질 규칙이 도입되었습니다.

* 프로그램당 최대 SSL 인증서를 50개로 늘립니다.

* 사용자가 Cloud Manager UI를 통해 여러 저장소를 만들고 관리할 수 있는 셀프 서비스 기능입니다.

* SonarQube가 불필요하게 Git 내역 데이터를 읽고 있었습니다. 큰 코드 베이스에서 이로 인해 불필요한 빌드 성능 벌금이 발생할 수 있습니다.

* 이제 파이프라인당 Maven 종속성 캐시를 무효화하는 데 사용할 수 있는 API가 있습니다.

* Cloud Manager에서 사용하는 AEM 프로젝트 원형 버전이 버전 29로 업데이트되었습니다.

### 버그 수정 {#bug-fixes}

* 최신 릴리스가 현재 릴리스보다 작을 경우 사용 가능한 업데이트 상태가 표시되지 않아야 합니다.

* 매우 긴 이름을 가진 새로운 조직에 대해 초기 온보딩이 실패했습니다.

* 경우에 따라 파이프라인이 두 번 트리거되면 *이(가) 파이프라인 실행 상태* 오류로 인해 실행 중 하나가 실패하는 경우가 있습니다.


