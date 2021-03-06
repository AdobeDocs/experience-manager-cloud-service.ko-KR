---
title: AEM 버전 업데이트
description: 'AEM 버전 업데이트 '
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 36%

---

# AEM 버전 업데이트 {#aem-version-updates}

## 소개 {#introduction}

AEM as a Cloud Service는 이제 지속적인 통합 및 연속 제공(CI/CD)을 사용하여 프로젝트를 가장 최신 AEM 버전에서 작업할 수 있습니다. 이는 사용자에 대한 서비스 중단 없이 프로덕션 및 스테이지 인스턴스가 최신 AEM 버전으로 업데이트됨을 의미합니다.

>[!NOTE]
>프로덕션 환경 업데이트에 실패하는 경우 Cloud Manager에서 자동으로 스테이징 환경을 롤백합니다. 이 작업은 업데이트가 완료된 후 스테이징 및 프로덕션 환경이 동일한 AEM 버전에 있도록 자동으로 수행됩니다.

AEM 버전 업데이트에는 두 가지 유형이 있습니다.

* **AEM 푸시 업데이트**

   * 일별로 릴리스될 수 있습니다.

   * 대부분 유지 관리이며, 최신 버그 수정 및 보안 업데이트가 여기에 포함됩니다.

      변경 내용이 정기적으로 적용됨에 따라 그 영향이 증분되어 서비스에 미치는 영향은 줄어듭니다.

* **새로운 기능 업데이트**

   * 예측 가능한 월별 일정을 통해 릴리스됩니다.

AEM 업데이트는 프로덕션 시스템에서 서비스를 중단하지 않도록 여러 단계를 포함하는 강력하고 완전히 자동화된 제품 유효성 검사 파이프라인을 따릅니다. 상태 검사는 응용 프로그램의 상태를 모니터링하는 데 사용됩니다. AEM as a Cloud Service 업데이트 중에 이러한 확인이 실패하면 릴리스가 진행되지 않으며 Adobe에서 업데이트로 인해 이 예기치 않은 동작이 발생한 이유를 조사합니다.

[제품 테스트 및 고객 기능 테스트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/understand-test-results.html#functional-testing) 또한 AEM 버전 업데이트 중에 제품 업그레이드 및 고객 코드 푸시가 프로덕션을 중단하지 않도록 하는 유효성 검사 방법을 사용할 수 있습니다.

>[!NOTE]
>
>사용자 지정 코드가 스테이징에 푸시된 다음 사용자가 거부하는 경우, 다음 AEM 업데이트는 이러한 변경 사항을 제거하여 마지막으로 성공한 고객 릴리스의 git 태그를 프로덕션에 반영합니다.

## 복합 노드 저장소 {#composite-node-store}

위에서 언급했듯이 대부분의 경우 업데이트는 노드 클러스터인 작성자에 대해 시작하여 다운타임 없이 수행됩니다. 다음 이유로 인해 롤링 업데이트가 가능합니다 *복합 노드 저장소* Oak의 기능입니다.

이 기능을 사용하면 AEM에서 여러 저장소를 동시에 참조할 수 있습니다. 롤링 배포에서 새 녹색 AEM 버전에는 자체 버전이 포함되어 있습니다 `/libs` (TarMK 기반 가변 저장소), 이전 Blue AEM 버전과 구별되는 저장소이지만, 두 리포지토리는 다음과 같은 영역을 포함하는 공유 DocumentMK 기반 가변 저장소를 참조합니다 `/content` , `/conf` , `/etc` 기타 왜냐하면 파란색과 녹색이 모두 그들만의 버전을 가지고 있기 때문이죠 `/libs`를 채울 수 있습니다. 둘 다 롤링 업데이트 중에 활성화될 수 있으며, 파란색이 완전히 녹색으로 대체될 때까지 트래픽을 사용합니다.
