---
title: AEM as a Cloud Service의 인프라 및 서비스 모니터링
description: AEM as a Cloud Service의 인프라 및 서비스 모니터링
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
source-git-commit: 34fed4e64b49ab32e7025c9654d930e3fa362a52
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 5%

---

# AEM as a Cloud Service의 인프라 및 서비스 모니터링 {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service은 다음 사항에 대한 가시성과 모니터링을 제공합니다. 인프라, 서비스 및 사용자 경험 다양한 솔루션이 사용되고 여러 가지 모니터링 레이어가 있으므로 이 페이지는 다음 세 섹션으로 구성됩니다.

* [외부 가용성](#external-availability)
* [내부 모듈 모니터링](#module-monitoring)
* [고객 가시성](#customer-observability)

AEM as a Cloud Service은 수백 개의 클라우드 기반의 모니터를 사용하여 매년 365일 동안 각 환경(24/7)을 지속적으로 보고합니다. 모니터 정의는 정적이 아니며, 조기 감지 기능을 개선하기 위해 지속적으로 검토됩니다. 또한 Adobe은 경고에 응답하도록 온-콜 절차가 설정되어 있습니다.

Cloud Manager를 통한 로깅 또는 모니터링과 같은 다른 유형의 모니터링에 대한 정보가 필요한 경우 다음을 참조하십시오. [추가 리소스](#resources) 섹션을 참조하십시오.

## 외부 가용성 {#external-availability}

외부 가용성은 다음 두 부분으로 구성됩니다. 서비스 에지 및 사용자 지정 모니터링.

### 서비스 에지 {#service-edge}

모든 AEM as a Cloud Service 환경이 가용성을 모니터링합니다. 그러나 Service Edge Monitoring은 프로덕션 환경에서만 설정되며, 이 지표는 고객의 SLA를 계산하는 데 사용됩니다. 환경 런타임 및 AEM as a Cloud Service CDN이 고려됩니다. Service Edge Monitoring은 선택한 지역에 가까운 5개의 개별 위치를 사용하고 있으며, 주기적으로 가용성을 확인합니다. 사이트의 가용성을 유지하지 않으면 경고가 트리거되며 Adobe의 On-Call 지원 팀 및 프로세스가 포함됩니다.

### 사용자 지정 모니터링 {#custom-monitoring}

사용자 지정 모니터링을 사용하면 고객은 최대 5개의 개별 웹 속성 URL을 제공 전에 제공할 수 있습니다 [live](/help/journey-migration/go-live.md). 이러한 URL은 유효해야 하며 HTTP 200 응답 코드를 반환합니다. 이러한 모니터는 [고유한 CDN 가져오기](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) Adobe의 제어에 있지 않은 AEM as a Cloud Service 앞에 사용되는 모든 외부 트래픽 라우팅 및 CDN Adobe 앞에 있습니다. 사용자 지정 모니터링 확인으로 인한 경고는 Adobe의 지원 팀 및 프로세스를 담당합니다.

>[!NOTE]
>
> 이 기능은 고급 클라우드 지원을 사용하는 고객에게만 제공됩니다. 질문이 있는 경우 Admin Console을 통해 지원 사례를 제기하십시오.

## 내부 모듈 모니터링 {#module-monitoring}

외부 가용성은 최종 사용자 모니터링에 중점을 두는 반면, 내부 모듈 모니터링은 아키텍처 하위 시스템이 기능이나 성능 저하 없이 명목적으로 작동하는지 여부를 관찰합니다. 문제가 발생할 경우 경고가 트리거되므로 자동으로 또는 운영 팀의 참여를 통해 복구를 수행할 수 있으며 가용성 저하 방지 목표를 달성합니다. 다음과 같은 여러 가지 모니터 범주가 있습니다.

* CPU iowait 비율이 특정 임계값을 초과하지 않습니다.
* 인스턴스 재배포는 특정 빈도를 초과하지 않습니다.
* 디스크 사용량이 특정 임계값 미만입니다.
* 작성자 저장소 크기가 특정 범위 내에 있습니다.
* 백업 작업이 완료되었습니다.
* 데이터베이스 상태 및 성능이 모니터링됩니다.
* AEM 클라우드 서비스는 차단된 복제 큐, 일관된 데이터 및 성능 쿼리를 포함하여 예상대로 작동합니다.

Forms에 대해 제공된 환경에 추가 확인이 추가됩니다. 확인 정의는 정적이 아니며, 변경 및 업데이트가 적용된다는 점을 기억하십시오.

## 고객 가시성 {#customer-observability}

고객은 를 사용할 수 있습니다 [New Relic 애플리케이션 성능 모니터링](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html) 분석 및 문제 해결을 위해 수집 및 차트로 표시한 실시간 성능 데이터를 제공하는 Suite. 모니터링 세트를 사용하면 고객이 다음과 같은 다양한 지표를 직접 관찰할 수 있습니다. JVM 성능 지표, Java에 대한 트랜잭션 시간, 백그라운드 외부 호출 및 데이터베이스 호출.

## 추가 리소스 {#resources}

* [New Relic 애플리케이션 성능 모니터링](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html)
* [AEM as a Cloud Service 로깅](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html)
* [환경 모니터링](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html)
