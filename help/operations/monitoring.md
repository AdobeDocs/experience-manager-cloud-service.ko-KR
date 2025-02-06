---
title: AEM as a Cloud Service의 인프라 및 서비스 모니터링
description: AEM as a Cloud Service의 인프라 및 서비스 모니터링
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
feature: Operations
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 5%

---

# AEM as a Cloud Service의 인프라 및 서비스 모니터링 {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service은 인프라, 서비스 및 사용자 경험에 대한 관찰 및 모니터링을 제공합니다. 다양한 솔루션이 사용되고 모니터링의 여러 계층이 있으므로 이 페이지는 다음 세 섹션으로 구성됩니다.

* [외부 가용성](#external-availability)
* [내부 모듈 모니터링](#module-monitoring)
* [고객 가시성](#customer-observability)

AEM as a Cloud Service은 수백 개의 클라우드 기반 모니터를 사용하여 1년 365일 동안 각 환경의 상태(24/7)를 지속적으로 보고합니다. 모니터 정의는 정적이지 않으며, 조기 감지 능력을 개선하기 위해 지속적으로 검토됩니다. 또한, Adobe은 경고에 응답하도록 호출 시 절차를 설정합니다.

Cloud Manager을 통한 로깅 또는 모니터링과 같은 다른 모니터링 유형에 대한 정보가 필요한 경우 [추가 리소스](#resources)를 참조하십시오.

## 외부 가용성 {#external-availability}

외부 가용성은 서비스 Edge 및 사용자 정의 모니터링의 두 부분으로 구성됩니다.

### 서비스 Edge {#service-edge}

AEM as a Cloud Service의 모든 환경은 가용성이 있는지 모니터링됩니다. 그러나 서비스 Edge 모니터링은 프로덕션 환경에 대해서만 설정되고 이 지표는 고객의 SLA을 계산하는 데 사용됩니다. 환경 런타임 및 AEM as a Cloud Service CDN을 고려해야 합니다. 서비스 Edge 모니터링은 선택한 지역에서 가까운 5개의 서로 다른 위치를 사용하며 정기적으로 가용성을 확인합니다. 사이트를 사용할 수 없으면 경고가 트리거되고 Adobe의 On-Call 지원 팀 및 프로세스가 참여합니다.

### 사용자 정의 모니터링 {#custom-monitoring}

사용자 지정 모니터링을 사용하면 고객은 [실행](/help/journey-migration/go-live.md) 전에 선택적으로 최대 5개의 고유한 웹 속성 URL을 제공할 수 있습니다. 이러한 URL은 유효해야 하며 HTTP 200 응답 코드를 반환해야 합니다. 이러한 모니터는 Adobe CDN 앞에 [자신의 CDN을 ](/help/implementing/dispatcher/cdn.md#point-to-point-CDN)가지고 오는 고객과 Adobe이 제어하지 않는 AEM as a Cloud Service 앞에 사용된 모든 외부 트래픽 라우팅을 지원합니다. 사용자 정의 모니터링 검사로 인한 경고는 Adobe의 지원 팀 및 프로세스를 참여시킵니다.

>[!NOTE]
>
> 이 기능은 프로덕션 환경 및 [고급 클라우드 지원](https://experienceleague.adobe.com/docs/support-resources/data-sheets/overview.html#support-add-ons)을 받는 고객에게만 제공됩니다. 질문이 있는 경우 Adobe 계정 팀에 문의하십시오.

## 내부 모듈 모니터링 {#module-monitoring}

외부 가용성은 최종 사용자 모니터링에 중점을 두지만, 내부 모듈 모니터링은 아키텍처 하위 시스템이 기능 또는 성능 저하 없이 명목상 작동하는지 관찰합니다. 문제가 발생하면 경고가 트리거되어 자동으로 또는 운영 팀의 관여를 통해 복구를 수행할 수 있으며, 가용성이 저하되는 것을 방지할 수 있습니다. 모니터에는 다양한 범주가 있으며, 아래에 몇 가지 확인 예가 나와 있습니다.

* CPU iowait 비율은 특정 임계값을 초과하지 않습니다.
* 인스턴스 재배포는 특정 빈도를 초과하지 않습니다.
* 디스크 사용량이 특정 임계값 미만입니다.
* 작성자 저장소 크기가 특정 범위 내에 있습니다.
* 백업 작업이 완료되었습니다.
* 데이터베이스 상태 및 성능이 모니터링됩니다.
* 차단된 복제 큐, 일관된 데이터 및 성능 저하 없는 쿼리를 포함하여 AEM Cloud Services가 예상대로 작동하고 있습니다.

Forms용으로 프로비저닝된 환경에 추가 검사가 추가됩니다. 확인 정의는 정적이 아니며 변경 및 업데이트될 수 있습니다.

## 고객 가시성 {#customer-observability}

고객은 분석 및 문제 해결을 위해 수집 및 차트로 작성된 실시간 성능 데이터를 제공하는 [New Relic 응용 프로그램 성능 모니터링](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html) 제품군을 사용할 수 있습니다. 모니터링 세트를 사용하면 고객이 JVM 성능 지표, Java™에 대한 트랜잭션 시간, 백그라운드 외부 호출 및 데이터베이스 호출과 같은 다양한 지표를 직접 관찰할 수 있습니다.

## 추가 리소스 {#resources}

* [New Relic 응용 프로그램 성능 모니터링](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html)
* [AEM as a Cloud Service에 대한 로깅](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html)
* [환경 모니터링](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html)
