---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.6.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.6.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: deef27dd90be22669b2328f6e394b8d3df99b4b9
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 33%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.6.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.6.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2023.6.0 릴리스 날짜는 2023년 6월 8일입니다. 다음 릴리스는 2023년 7월 6일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 고객은 운영 지역 외에 추가 보조 게시 지역을 구매할 수 있으므로 지연 시간 단축 및 가용성 향상과 관련된 이점이 있습니다. 참고: 특정 제한 사항이 적용될 수 있습니다.
* 새 항목 생성 시 [프로그램 또는 환경,](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) 이제 이름에는 영숫자와 제한된 특수 문자 집합만 사용할 수 있습니다.
* 다시 시작할 때 [프로덕션 파이프라인,](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 이제 승인 단계에서 확인 대화 상자가 표시됩니다.
* 의 경우 **[고객 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)** 및 **[사용자 정의 UI 테스트](/help/implementing/cloud-manager/ui-testing.md)** 파이프라인 단계, 새로운 기능 `INCOMPLETE` 이제 상태가 가능해졌으며, 이는 이러한 테스트가 존재하지 않았으므로 수행되지 않았음을 나타냅니다.
   * 이러한 경우 파이프라인이 실패하지 않고 다음 단계로 진행합니다.

## 버그 수정 {#bug-fixes}

* 다음 [웹 계층 구성 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) 은 더 이상 에셋 전용 프로그램에 대해 잘못 활성화되지 않습니다.
* 환경 프로비저닝 중에 특정 유형의 실패를 방지하기 위해 보다 강력한 유효성 검사가 추가되었습니다.
