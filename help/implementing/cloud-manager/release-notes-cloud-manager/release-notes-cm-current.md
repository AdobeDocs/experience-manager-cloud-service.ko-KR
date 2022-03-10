---
title: Adobe Experience Manager as a Cloud Service Cloud Manager 2022.3.0의 릴리스 노트
description: 다음은 AEM as a Cloud Service의 Cloud Manager 2022.3.0에 대한 릴리스 노트입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 428bba062fcfb44ebfbbf3c1d05ce1a4634fb429
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 2%

---


# Adobe Experience Manager as a Cloud Service Cloud Manager 2022.3.0의 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2022.3.0에 대한 릴리스 노트를 문서화합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 10의 Cloud Manager 릴리스 2022.3.0에 대한 릴리스 날짜(2022년 3월) 다음 릴리스는 2022년 4월 7일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 을 사용하는 사용자 **개발자** 이제 역할이 AEM 환경 로그에 액세스할 수 있습니다.
* [다음 `reliability_rating` 중요 지표](/help/implementing/cloud-manager/code-quality-testing.md) 이 비활성화되었습니다.
* 이제 사용자가 **파이프라인** 페이지를 Cloud Manager에 추가합니다.

## 버그 수정 {#bug-fixes}

* 수동으로 만든 Git 리포지토리의 하위 집합에 영향을 받는 잘못된 이름 값이 있습니다 [빌드 아티팩트 재사용 기능입니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) 이러한 리포지토리의 이름이 변경되었으며 사용자는 Cloud Manager API/UI에서 수정된 이름을 볼 수 있습니다.
* [코드 품질 파이프라인을 추가하거나 편집할 때](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) a **중요한 지표 실패 동작** 옵션이 더 이상 표시되지 않습니다.
* 예기치 않은 파이프라인 변수 구성으로 인해 빌드 단계에서 오류가 발생하지 않습니다.
