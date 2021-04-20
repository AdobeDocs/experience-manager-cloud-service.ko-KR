---
title: AEM 버전 업데이트
description: 'AEM 버전 업데이트 '
feature: Deploying
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---


# AEM 버전 업데이트 {#aem-version-updates}

## 소개 {#introduction}

이제 Cloud Service으로 AEM은 지속적인 통합 및 지속적인 전달(CI/CD)을 사용하여 프로젝트가 최신 AEM 버전에 있는지 확인합니다. 즉, 프로덕션 및 스테이지 인스턴스는 사용자를 위한 서비스 중단 없이 최신 AEM 버전으로 업데이트됩니다.

>[!NOTE]
>프로덕션 환경에 대한 업데이트가 실패하면 Cloud Manager는 자동으로 스테이지 환경을 롤백합니다. 이 작업은 업데이트가 완료된 후 스테이지와 프로덕션 환경 모두 동일한 AEM 버전을 사용하도록 자동으로 수행됩니다.

AEM 버전 업데이트는 다음 두 가지 유형으로 구성됩니다.

* **AEM 푸시 업데이트**

   * 일일 기준으로 출시될 수 있습니다.

   * 최신 버그 수정 및 보안 업데이트를 비롯한 대부분의 유지 관리.

      변경 사항이 정기적으로 적용되므로 서비스 영향이 점차 증가하고 있습니다.

* **새로운 기능 업데이트**

   * 예측 가능한 월별 일정을 통해 릴리스됩니다.

AEM 업데이트는 프로덕션 중인 모든 시스템에 서비스를 중단 없이 진행하는 여러 단계를 포함하는 강력하고 완벽하게 자동화된 제품 유효성 검사 파이프라인을 거칩니다. 상태 검사는 응용 프로그램의 상태를 모니터링하는 데 사용됩니다. AEM에서 Cloud Service 업데이트으로 이러한 검사가 실패하는 경우 릴리스가 진행되지 않으며 Adobe에서 업데이트가 이 예기치 않은 동작을 일으킨 이유를 조사합니다.

[제품 업그레이드 및 고객 기능 테스트](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#functional-testing) 를 방지하고, 제품 업그레이드 및 고객 코드 푸시가 생산을 중단시키지 않도록 하는 경우에도 AEM 버전 업데이트 동안 유효성이 검사됩니다.

>[!NOTE]
>
>사용자 지정 코드가 스테이징으로 푸시되고 사용자가 거부한 경우 다음 AEM 업데이트는 해당 변경 사항을 제거하여 마지막으로 성공한 고객 릴리스의 git 태그를 프로덕션에 반영합니다.

## 복합 노드 저장소 {#composite-node-store}

위에 언급했듯이 대부분의 경우 업데이트는 노드 클러스터인 작성자를 포함하여 다운타임이 0으로 발생합니다. Oak의 *합성 노드 저장소* 기능으로 인해 롤링 업데이트가 가능합니다.

이 기능을 사용하면 AEM에서 여러 저장소를 동시에 참조할 수 있습니다. 롤링 배포에서 새 Green AEM 버전은 고유한 `/libs`(TarMK 기반 변경 가능 저장소)을 포함하며, 이전 Blue AEM 버전과 구별됩니다. 두 버전은 `/content`, `/conf`, `/etc` 등과 같은 영역을 포함하는 공유 DocumentMK 기반 변경 가능 저장소를 참조합니다. 파란색과 녹색 둘 다 자체 버전의 `/libs`을 가지고 있으므로 롤링 업데이트 동안 둘 다 활성화할 수 있습니다. 둘 다 파란색이 녹색으로 완전히 바뀔 때까지 트래픽을 받습니다.

