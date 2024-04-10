---
title: AEM 버전 업데이트
description: Adobe Experience Manager(AEM as a Cloud Service)에서 CI/CD(지속적 통합 및 배포)를 사용하여 프로젝트를 최신 버전으로 유지하는 방법에 대해 알아봅니다.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 72fc611e006f80fdda672f08b0b795432f5899e2
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 1%

---


# AEM 버전 업데이트 {#aem-version-updates}

Adobe Experience Manager(AEM as a Cloud Service)에서 CI/CD(지속적 통합 및 배포)를 사용하여 프로젝트를 최신 버전으로 유지하는 방법에 대해 알아봅니다.

## CI/CD {#ci-cd}

AEM as a Cloud Service은 CI/CD(지속적 통합 및 지속적 배포)를 사용하여 프로젝트가 가장 최신 AEM 버전에 있도록 합니다. 이 프로세스는 사용자에게 영향을 주지 않고 프로덕션, 스테이징 및 개발 인스턴스를 원활하게 업데이트합니다.

>[!NOTE]
> 개발 인스턴스는 이미 자동으로 업데이트되므로 개발 인스턴스에 대한 수동 업데이트는에서 사용할 수 없습니다. _일부_ 을 참조하십시오. 이 기능은 자동 업데이트로 전환됩니다.

인스턴스가 자동으로 업데이트되기 전에 3~5일 전에 새 AEM 유지 관리 릴리스가 게시됩니다. 이 기간 동안 개발 인스턴스가 자동으로 업데이트되거나 사용 가능한 경우 선택적으로 업데이트할 수 있습니다 [개발 인스턴스에 대한 업데이트 트리거](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment). 버전 업데이트는 먼저 개발 환경에 자동으로 적용됩니다. 업데이트가 성공하면 업데이트 프로세스가 스테이징 및 프로덕션 인스턴스로 진행됩니다. 개발 및 스테이징 인스턴스는 업데이트가 프로덕션 환경에 적용되기 전에 사용자 지정 작성 테스트가 실행되는 자동화된 품질 게이트 역할을 합니다.

### NIMU(비간섭 유지 보수 업데이트) {#nimu}

비침해적 유지 보수 업데이트는 고객 파이프라인과 관련이 없이 적용되는 자동 업데이트입니다.
NIMU를 통해 고객은 AEM 버전 업데이트가 예약되거나 진행 중인 경우에도 언제든지 파이프라인을 사용할 수 있으며 유지 관리 업데이트가 더 이상 고객 파이프라인 실행 기록에 표시되지 않으므로 코드 배포 내역을 더 쉽게 추적할 수 있습니다.

#### 활동 업데이트

Cloud Manager UI 환경 패널을 사용하여 이전과 마찬가지로 현재 AEM 버전을 각 환경에 대해 확인할 수 있습니다. 파이프라인에서 사용되는 것과 동일한 품질 게이트를 고객 서면 테스트를 포함한 비침입 유지 관리 업데이트에서 사용합니다.
프로그램 환경에 비간섭 유지 관리 업데이트가 적용될 때마다 Cloud Manager UI 알림이 전송됩니다. 이메일로도 전송되도록 구성할 수 있습니다.

>[!NOTE]
>
> 참고: 비간섭 유지 보수 업데이트는 2024년에 모든 고객에 대해 점진적으로 활성화됩니다.


## 업데이트 유형 {#update-types}

AEM 버전 업데이트에는 다음과 같은 두 가지 유형이 있습니다.

* [**AEM 유지 보수 업데이트**](/help/release-notes/maintenance/latest.md)

   * 대부분 유지 관리 목적이며, 최신 버그 수정 및 보안 업데이트가 여기에 포함됩니다.
   * 변경 사항이 정기적으로 적용되므로 최소한의 영향만 미칩니다.

* [AEM 기능 활성화**](/help/release-notes/release-notes-cloud/release-notes-current.md)

   * 예측 가능한 월별 일정에 따라 릴리스됩니다.

>[!NOTE]
>
> 에서 월별 릴리스의 주요 날짜 확인 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html#aem-as-cloud-service) 달력에 표시하여 릴리스를 준비하기 위한 주요 활동을 준비하십시오.

## 업데이트 실패 {#update-failure}

AEM 업데이트는 여러 단계를 포함하는 강력하고 완전히 자동화된 제품 유효성 검사 파이프라인을 통해 운영상의 모든 시스템에 대한 서비스를 중단하지 않도록 합니다. 상태 검사는 응용 프로그램의 상태를 모니터링하는 데 사용됩니다. AEM as a Cloud Service 업데이트 중에 이러한 검사가 실패하면 릴리스는 진행되지 않고 Adobe에서 업데이트가 예기치 않은 동작을 발생시킨 이유를 확인합니다.

환경에 새 버전의 사용자 지정 코드를 배포하는 경우 [제품 및 사용자 정의 기능 테스트](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) 중요한 역할을 수행하세요. 변경 사항이 적용된 후에도 프로덕션 시스템이 안정적이고 작동합니다. 이러한 테스트는 AEM 버전 업데이트 프로세스에도 적용됩니다.

프로덕션 환경 업데이트에 실패하는 경우 Cloud Manager가 자동으로 스테이징 환경을 롤백합니다. 이 작업은 업데이트가 완료된 후 스테이징 및 프로덕션 환경이 동일한 AEM 버전에 있도록 자동으로 수행됩니다.
마찬가지로 개발 환경의 자동 업데이트에 실패하는 경우 스테이징 및 프로덕션 환경은 업데이트되지 않습니다.

>[!NOTE]
>
>사용자 지정 코드가 프로덕션이 아닌 스테이징으로 푸시된 경우 다음 AEM 업데이트는 이러한 변경 사항을 제거하여 프로덕션에 마지막으로 성공한 고객 릴리스의 git 태그를 반영합니다. 따라서 스테이징에서만 사용할 수 있었던 사용자 지정 코드를 다시 배포해야 합니다.

## 모범 사례 {#best-practices}

* **스테이징 환경 사용**
   * 긴 QA/UAT 주기를 위해 스테이징이 아닌 다른 환경을 사용합니다.
   * 스테이지에서 온전성 테스트가 완료되면 프로덕션에서 로 이동하여 확인합니다.

* **프로덕션 파이프라인**
   * 프로덕션에 배포하기 전에 일시 중단합니다.
   * 스테이징 배포 후 파이프라인을 취소하면 코드가 &quot;통과 중&quot;이며 올바른 프로덕션 후보가 아님을 나타냅니다. 다음을 참조하십시오. [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* **비프로덕션 파이프라인**
   * 구성 [비프로덕션 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
   * 프로덕션 파이프라인 실패에 대한 전달 속도/빈도를 가속화합니다. 제품 기능 테스트, 사용자 정의 기능 테스트 및 사용자 정의 UI 테스트를 활성화하여 비프로덕션 파이프라인의 문제를 식별합니다.

* **콘텐츠 복사**
   * 사용 [콘텐츠 복사](/help/implementing/developing/tools/content-copy.md) 를 클릭하여 유사한 컨텐트 세트를 비프로덕션 환경으로 이동합니다.

* **자동화된 기능 테스트**
   * 파이프라인에 자동화된 테스트를 포함하여 중요한 기능을 테스트할 수 있습니다.
   * [고객 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) 및 [사용자 정의 UI 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) 가 차단됩니다. 실패하면 AEM 릴리스가 롤아웃되지 않습니다.

## 회귀 {#regression}

회귀 관련 문제가 발생하면 Admin Console을 통해 지원 사례를 제출합니다. 문제가 차단제이고 프로덕션에 영향을 주는 경우 P1이 제기되어야 합니다. 회귀 문제를 재현하는 데 필요한 모든 세부 정보를 제공합니다.

## 복합 노드 저장소 {#composite-node-store}

일반적으로 업데이트는 노드 클러스터인 작성 인스턴스를 포함하여 가동 중지 시간 없이 발생합니다. 다음 이유로 인해 롤링 업데이트가 가능합니다. [oak의 복합 노드 저장소 기능입니다.](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

이 기능을 사용하면 AEM에서 여러 저장소를 동시에 참조할 수 있습니다. 다음 기간 [순환 배포](/help/implementing/deploying/overview.md#how-rolling-deployments-work), 새 AEM 버전에는 자체 버전이 포함되어 있습니다 `/libs` (TarMK 기반 변경 불가능한 저장소). 두 버전 모두 와 같은 영역이 포함된 공유 DocumentMK 기반 변경 가능한 저장소를 참조하지만, 이전 AEM 버전과 구별됩니다 `/content` , `/conf` , `/etc` 외.

이전 버전과 새 버전 모두 의 자체 버전이 있으므로 `/libs`, 두 가지 모두 롤링 업데이트 중에 활성화될 수 있습니다. 그리고, 둘 다 옛 것이 새 것으로 완전히 대체될 때까지 트래픽을 맡을 수 있습니다.
