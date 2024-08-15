---
title: 액션 센터
description: 문제 및 기타 중요한 정보에 대해 편리하게 조치를 취할 수 있도록 조치 센터 활용
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
feature: Operations
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 54%

---

# 액션 센터 {#actions-center}

AEM as Cloud Service는 최적화에 즉각적인 조치 및 사전 알림 추천이 필요한 중대 인시던트가 발생하면 액션 센터 이메일 알림을 전송합니다. 예로는 차단된 대기열 또는 만료되는 자격 증명 세트가 있습니다. 액션 센터 알림 유형의 전체 세트는 [아래 표](#supported-notification-types)에서 볼 수 있으며 시간이 지남에 따라 확장됩니다.

작업 센터 이메일 알림이 수신되면 을 클릭하여 AEM as a Cloud Service의 작업 센터를 열 수 있습니다. 이 페이지에는 고객이 수행할 작업을 설명하는 추가 컨텍스트가 표시됩니다.

방금 클릭한 이메일 알림에 대한 정보를 표시하는 것 외에도 액션 센터는 현재 및 이전 알림 세트를 보고 관리할 수 있는 허브 역할을 합니다. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers do not find it) -->

액션 센터에 표시되는 두 가지 높은 수준의 알림 범주가 있습니다.

1. 운영 인시던트 - 일반적으로 신속한 해결이 필요한 이벤트가 발생했습니다. 예: 차단된 대기열 해결.
1. 사전 알림 추천 - Adobe는 가까운 미래에 고객이 취해야 할 조치에 대한 추천을 제시합니다. 예: 더 이상 사용되지 않는 UI 참조를 중지합니다.

액션 센터에서 현재 지원되는 알림은 [아래 표](#supported-notification-types)를 참조하십시오.

액션 센터에서 해당 범위에 대한 필터링 효과가 있는 특정 프로그램 및 환경을 선택할 수 있습니다.

## 구성 {#configuration}

수신 관리 센터 전자 메일 알림을 구성하려면 [알림 프로필](/help/journey-onboarding/notification-profiles.md)에 설명된 대로 제품 프로필을 만듭니다. 즉, 문제 알림 - Cloud Service 및 사전 알림 - Cloud Service. 또한 해당 프로필에 조직의 적절한 Adobe ID를 할당합니다. 이를 통해 관리자는 해당 이메일 알림을 수신하려는 사용자를 확인할 수 있습니다.

>[!NOTE]
>액션 센터 이메일 알림은 조직 수준에서 작동하므로 구독자는 해당 프로그램 내의 모든 프로그램 및 환경에 대한 알림을 수신합니다.

## 자세한 사용자 흐름 {#detailed-user-flow}

이메일을 클릭하면 작업 센터로 이동합니다. 이 센터에는 클릭한 알림에 대한 컨텍스트 및 경우에 따라 수정 조치를 수행하는 방법을 설명하는 추가 정보 링크가 표시됩니다. [https://experience.adobe.com/aem/actions-center](https://experience.adobe.com/aem/actions-center/)에서 액션 센터에 직접 액세스하여 관련 프로그램 및 환경을 선택할 수도 있습니다.

![인시던트 세부 정보](/help/operations/assets/incident-details.png)

사용자는 **자세히 알아보기** 링크를 클릭하여 이 문서로 이동합니다. 아래에서 [지원되는 알림 유형 표](#supported-notification-types)와 같이 알림 유형을 참조할 수 있으며, 이 표는 어떤 조치를 취해야 하는지 지침을 제공합니다.

액션 센터에서 다른 최근 알림 목록을 볼 수 있습니다. 조직이 작업을 인식하고 있음을 Adobe에 알리고 나중에 수정 조치가 취해졌을 때 알림을 해결하기 위해 작업 목록을 사용하여 알림을 확인하는 것이 좋습니다.

![알림 목록](/help/operations/assets/notification-list.png)

대부분의 경우 팝업은 문제를 해결하는 데 필요한 모든 컨텍스트를 제공해야 합니다. 그러나 Adobe 지원에 대한 질문이 있는 경우 팝업에서 **지원 문의** 링크를 클릭할 수 있습니다. 이렇게 하면 질문을 설명하고 지원 티켓을 만들기 위해 제출할 수 있는 양식이 표시되며, 여기에는 Adobe 지원 엔지니어가 관련 컨텍스트를 확보할 수 있도록 특정 알림에 대한 참조도 포함됩니다.

![지원에 문의 1](/help/operations/assets/contact-support1.png)

![지원에 문의 2](/help/operations/assets/contact-support2.png)

모든 지원 티켓과 마찬가지로 지원 티켓이 [Adobe Admin Console의 지원 사례 탭](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html)에 나타나며, 여기에서 지원 티켓을 추적하고 댓글을 추가할 수 있습니다.

![Admin Console 지원](/help/operations/assets/admin-console-support.png)

## 어떤 알림이 표시됩니까? {#which-notification}

AEM as a Cloud Service에는 여러 유형의 알림이 있지만 아래 그림과 같이 액션 센터에는 하위 집합만 표시됩니다.

| 알림 유형 | 설명 | 구성하는 방법 | 액션 센터에 표시 |
|---------------------------------|-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| 운영 인시던트 | 즉각적인 조치가 필요한 중대 인시던트 | “인시던트 알림 - Cloud Service” 제품 프로필에 할당된 사용자 | X |
| 사전 알림 추천 | 계획을 수립해야 하는 최적화 | “사전 알림 - Cloud Service” 제품 프로필에 할당된 사용자 | X |
| Cloud Manager 파이프라인 상태 | 파이프라인 상태에 대한 정보 | 비즈니스 소유자, 프로그램 관리자 또는 배포 관리자 역할의 사용자, &quot;기타&quot; 확인란이 [Experience Cloud 환경 설정](https://experience.adobe.com/preferences)에서 선택되었습니다. [알림](/help/implementing/cloud-manager/notifications.md)을 참조하세요. |                           |

## 지원되는 알림 유형 {#supported-notification-types}

다음 표는 액션 센터에서 현재 지원되는 알림 유형 목록입니다. 알림은 현재 프로덕션 환경으로 제한됩니다.

| 알림 유형 | 관련 제품 프로필 | 수정 조치 |
|---------------------------------|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 차단된 복제 대기열 | 인시던트 | [복제 문서](/help/operations/replication.md#troubleshooting)의 지침에 따라 대기열 차단을 해제합니다. |
| 잘못된 지속 GraphQL 쿼리 | 인시던트 | [지속된 GraphQL 쿼리 문제 해결 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/headless/graphql-api/persisted-queries-troubleshoot.html)를 참조하여 잘못된 GraphQL 쿼리를 수정하십시오. |
| 원본 트래픽 스파이크 | 인시던트 | 원본 경고의 기본 트래픽 스파이크보다 낮은 임계값에서 트리거하는 비율 제한 트래픽 필터 규칙을 구성하여 원본을 Protect 합니다.  자습서를 참조하는 트래픽 필터 규칙 설명서의 [트래픽 규칙을 사용하여 DoS 및 DDoS 공격 차단](/help/security/traffic-filter-rules-including-waf.md#blocking-dos-and-ddos-attacks-using-traffic-filter-rules) 섹션을 참조하십시오. |
| CDN 트래픽 필터 규칙 트리거됨 | 인시던트 | 일치하는 트래픽 필터 규칙이 공격을 반영하지만 사이트에서 해당 트래픽을 차단하지 않는 경우 차단 모드에서 트래픽 필터 규칙을 구성하여 사이트를 보호하십시오. 자습서를 참조하는 트래픽 필터 규칙 설명서의 [트래픽 필터 규칙으로 웹 사이트 보호(WAF 규칙 포함)](/help/security/traffic-filter-rules-including-waf.md#tutorial-protecting-websites) 섹션을 참조하십시오. |
| 페이지에 많은 수의 노드가 포함되어 있습니다. | 사전 알림 | 페이지 내 총 노드 수를 줄입니다. [페이지 복잡성 설명서](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/pcx)를 참조하세요. | |
| 실행 중인 많은 워크플로 인스턴스 | 사전 알림 | 더 이상 필요하지 않은 실행 중인 워크플로우를 종료합니다. [제거 작업을 구성하는 방법](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/operations/maintenance) 알아보기 |               |
| 만료되는 S2S 인증서 | 사전 알림 | [서버측 API용 액세스 토큰 생성 문서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials)에서 자격 증명을 새로 고치는 방법에 대해 알아보십시오. | 높은 연결 수 | 사전 알림 | [고급 네트워킹 설명서와 함께 연결 풀링에 대해 알아봅니다](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
| 더 이상 사용되지 않는 서비스 사용자 매핑 | 사전 알림 | [Sling 서비스 사용자 매핑 및 서비스 사용자 정의에 대한 우수 사례](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/best-practices-for-sling-service-user-mapping-and-service-user-definition)에 나와 있는 대로 최신 Sling 서비스 사용자 매핑 형식을 사용하는 방법에 대해 알아봅니다. |
| 높은 연결 수 | 사전 알림 | [고급 네트워킹 설명서](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking)에서 연결 풀링에 대해 알아봅니다. |  |
| 사용자 정의 그룹에 직접 추가된 사용자 | 사전 알림 | 사용자를 관련 IMS 그룹에 추가하고 이러한 IMS 그룹을 AEM 그룹의 멤버로 추가해야 합니다. [IMS 모범 사례](/help/security/ims-support.md)에 맞추기 | |
| JCR 콘텐츠 누락 | 사전 알림 | 누락된 JCR 콘텐츠 노드를 추가합니다. [Assets Content Validator 설명서](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/acv)를 참조하세요. | |
| 완료된 워크플로가 삭제되지 않음 | 사전 알림 | 90일 이상 된 워크플로 인스턴스를 삭제하여 워크플로 인스턴스 수를 최소화하고 성능을 향상시킵니다. [유지 관리 작업을 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/operations/maintenance)하는 방법 알아보기 | |
| 페이지에 Sling 리소스 유형 누락 | 사전 알림 | 누락된 Sling 리소스 유형 노드를 추가합니다. [Assets Content Validator 설명서](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/acv)를 참조하세요. |
