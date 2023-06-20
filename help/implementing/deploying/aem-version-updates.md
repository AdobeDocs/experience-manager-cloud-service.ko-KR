---
title: AEM 버전 업데이트
description: AEM에서 as a Cloud Service으로 CI/CD(지속적 통합 및 배포)를 사용하여 프로젝트를 최신 버전으로 유지하는 방법을 알아봅니다.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: bceec9ea6858b1c4c042ecd96f13ae5cac1bbee5
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 23%

---


# AEM 버전 업데이트 {#aem-version-updates}

AEM에서 as a Cloud Service으로 CI/CD(지속적 통합 및 배포)를 사용하여 프로젝트를 최신 버전으로 유지하는 방법을 알아봅니다.

## CI/CD {#ci-cd}

AEM as a Cloud Service은 CI/CD(지속적 통합 및 지속적 배포)를 사용하여 프로젝트가 가장 최신 AEM 버전에 있도록 합니다. 이는 프러덕션 및 스테이징 인스턴스가 사용자에 대한 서비스 중단 없이 최신 AEM 버전으로 업데이트된다는 것을 뜻합니다.

버전 업데이트는 프로덕션 및 스테이징 인스턴스에만 자동으로 적용됩니다. [AEM 업데이트는 다른 모든 인스턴스에 수동으로 적용해야 합니다.](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment)

## 업데이트 유형 {#update-types}

AEM 버전 업데이트에는 다음과 같은 두 가지 유형이 있습니다.

* **AEM 유지 보수 업데이트**

   * 일별로 릴리스될 수 있습니다.
   * 대부분 유지 관리 목적이며, 최신 버그 수정 및 보안 업데이트가 여기에 포함됩니다.
   * 변경 사항이 정기적으로 적용되므로 최소한의 영향만 미치게 됩니다.

* **새로운 기능 업데이트**

   * 다음에서 릴리스됨: [예측 가능한 월별 일정.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR)

## 업데이트 실패 {#update-failure}

AEM 업데이트는 여러 단계를 포함하는 강력하고 완전히 자동화된 제품 유효성 검사 파이프라인을 통해 운영상의 모든 시스템에 대한 서비스를 중단하지 않도록 합니다. 상태 검사는 응용 프로그램의 상태를 모니터링하는 데 사용됩니다. AEM as a Cloud Service 업데이트 중에 이러한 확인이 실패하면 릴리스는 진행되지 않고 Adobe에서 업데이트가 예기치 않은 동작을 발생시킨 이유를 조사합니다.

[제품 테스트 및 고객 기능 테스트,](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) 제품 업그레이드 및 고객 코드 푸시로 인해 프로덕션 시스템이 중단되는 것을 방지하는 기능은 AEM 버전 업데이트 중에도 유효합니다.

프로덕션 환경 업데이트에 실패하는 경우 Cloud Manager에서 자동으로 스테이징 환경을 롤백합니다. 이 작업은 업데이트가 완료된 후 스테이징 및 프로덕션 환경이 동일한 AEM 버전에 있도록 자동으로 수행됩니다.

>[!NOTE]
>
>사용자 지정 코드가 프로덕션이 아닌 스테이징으로 푸시된 경우 다음 AEM 업데이트에서는 이러한 변경 사항을 제거하여 프로덕션에 마지막으로 성공한 고객 릴리스의 git 태그를 반영합니다. 따라서 스테이징에서만 사용할 수 있었던 사용자 지정 코드를 다시 배포해야 합니다.

## 복합 노드 저장소 {#composite-node-store}

대부분의 경우 업데이트는 노드 클러스터인 작성 인스턴스를 포함하여 중단 없이 이루어집니다. 다음 이유로 인해 롤링 업데이트가 가능합니다. [oak의 복합 노드 저장소 기능입니다.](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

이 기능을 사용하면 AEM에서 여러 저장소를 동시에 참조할 수 있습니다. 다음 기간 [순환 배포,](/help/implementing/deploying/overview.md#how-rolling-deployments-work) 새 AEM 버전에는 자체 버전이 포함됩니다 `/libs` (TarMK 기반 변경 불가능한 저장소), 이전 AEM 버전과 구별되지만 둘 다 와 같은 영역을 포함하는 공유 DocumentMK 기반 변경 가능한 저장소를 참조합니다. `/content` , `/conf` , `/etc` 외.

이전 버전과 새 버전 모두 의 자체 버전이 있으므로 `/libs`, 두 기능은 모두 롤링 업데이트 중에 활성화될 수 있으며, 이전 기능이 새 기능으로 완전히 대체될 때까지 둘 다 트래픽을 처리할 수 있습니다.
