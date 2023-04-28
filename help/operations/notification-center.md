---
title: 알림 센터
description: 알림 센터를 활용하여 인시던트 및 기타 중요한 정보에 대해 편리하게 조치
hidefromtoc: true
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: b72d22e8788c04ab4faa3616a4a0ce5e6d8ce991
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 36%

---

# 알림 센터 {#notification-center}

>[!NOTE]
>이 기능은 릴리스되지 않았습니다.

AEM as Cloud Service은 즉각적인 조치가 필요한 중요한 사고가 발생하면 알림을 보내고 최적화에 대한 사전 권장 사항을 보냅니다. 예를 들어 차단된 큐 또는 만료 자격 증명 세트가 있습니다. 전체 알림 유형 집합은 [아래 표](#supported-notification-types): 시간이 지남에 따라 확장됩니다.

이러한 알림은 이메일 및 알림 위젯을 통해 수신하도록 구성할 수 있으며, 알림 위젯에서는 Adobe Experience Cloud 전체의 오른쪽 상단 모서리에 있는 벨 아이콘을 클릭하여 액세스할 수 있습니다.

알림을 받으면 클릭하여 AEM as a Cloud Service 알림 센터를 열고 고객이 수행할 작업을 설명하는 추가 컨텍스트를 표시하는 팝업으로 알림 센터를 열 수 있습니다.

방금 클릭한 알림에 대한 정보를 표시하는 것 외에도, 알림 센터는 현재 및 이전 알림 세트를 보고 관리할 수 있는 허브 역할을 합니다. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

알림 센터에 표시되는 두 가지 높은 수준의 알림 카테고리가 있습니다.

1. 작동 장애 - 이벤트가 발생했으며 일반적으로 신속한 확인이 필요합니다. 예: 차단된 대기열 해결.
1. 사전 권장 사항 - Adobe에는 고객이 가까운 시일 내에 수행해야 하는 작업에 대한 권장 사항이 있습니다. 예: 더 이상 사용되지 않는 UI 참조를 중지합니다.

현재 지원되는 알림은 [아래 표](#supported-notification-types)를 참조하십시오.

알림 센터에서 특정 프로그램 및 환경을 선택할 수 있으며, 이 경우 해당 범위를 필터링하는 효과가 있습니다.

## 구성 {#configuration}

아래 절차에 따라 수신 알림을 구성하십시오.

1. 설명된 대로 다음 제품 프로필을 만듭니다 [이 문서](/help/journey-onboarding/notification-profiles.md)또한 조직의 적절한 Adobe ID를 해당 프로필에 할당합니다. 이를 통해 관리자는 이러한 알림을 받을 수 있는 사용자를 결정할 수 있습니다.
1. 이전 단계에서 지정된 각 사용자는 알림을 받을 방식을 구성할 수 있습니다. 설정 [Experience Cloud 환경 설정 페이지](https://experience.adobe.com/preferences/notification-section), Experience Manager 구독이 활성화되어 있고, **운영 장애** 및 **사전 권장 사항** 확인란이 선택됩니다. 또한 이메일 섹션을 **인스턴트 알림** 따라서 인시던트가 발생하면 알림이 즉시 수신됩니다.

>[!NOTE]
>알림은 조직 수준에서 작동하므로 구독자는 해당 프로그램 내의 모든 프로그램 및 환경에 대한 알림을 받게 됩니다.

## 자세한 사용자 흐름 {#detailed-user-flow}

이메일을 클릭하면 클릭한 알림에 대한 컨텍스트를 표시하는 팝업과 경우에 따라 수정 조치를 취하는 방법을 설명하는 추가 정보 링크가 있는 알림 센터로 이동합니다.

![인시던트 세부 정보](/help/operations/assets/incident-details.png)

**자세히 알아보기** 링크를 클릭하면 이 문서로 이동합니다. 여기에서 아래 표와 같이 알림을 참조할 수 있으며, 이 표는 어떤 조치를 취해야 하는지 지침을 제공합니다.

알림 센터에서 다른 최근 알림 목록을 볼 수 있습니다. 조직이 작업을 인식하고 있음을 Adobe에 알리고, 나중에 수정 조치가 취해졌을 때 알림을 해결하기 위해 작업 목록을 사용하여 알림을 확인하는 것이 좋습니다.

![알림 목록](/help/operations/assets/notification-list.png)

대부분의 경우 알림은 문제를 해결하는 데 필요한 모든 컨텍스트를 제공합니다. 단, Adobe 지원에 대한 질문이 있는 경우 알림 팝업에서 **지원에 문의** 링크를 클릭할 수 있습니다. 이 경우 질문을 설명하고 제출할 수 있는 양식을 가져와 지원 티켓을 만듭니다. 이 표는 특정 알림에 대한 참조를 포함하므로 Adobe 지원 엔지니어가 관련 컨텍스트를 가질 수 있습니다.

![지원에 문의 1](/help/operations/assets/contact-support1.png)

![지원에 문의 2](/help/operations/assets/contact-support2.png)

모든 지원 티켓과 마찬가지로 지원 티켓이 [Adobe Admin Console의 지원 사례 탭](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html)에 나타나며, 여기에서 지원 티켓을 추적하고 추가 설명을 추가할 수 있습니다.

![Admin Console 지원](/help/operations/assets/admin-console-support.png)

## 어떤 알림이 표시됩니까? {#which-notification}

AEM as a Cloud Service에는 몇 가지 유형의 알림이 있지만 아래 표에 나와 있는 것처럼 알림 센터에 하위 집합만 표시됩니다.

| 알림 유형 | 설명 | 구성 방법 | 알림 센터에 표시 |
|---|---|---|---|
| 운영 장애 | 즉각적인 조치가 필요한 중요한 사고 | 인시던트 알림 - Cloud Service 제품 프로필에 할당된 사용자, 다음에서 선택한 &quot;Operational Insights&quot; 확인란 [Experience Cloud 환경 설정](https://experience.adobe.com/preferences) | X |
| 사전 권장 사항 | 계획해야 하는 최적화 | &quot;사전 알림 - Cloud Service&quot; 제품 프로필에 지정된 사용자, 다음에서 선택한 &quot;사전 권장 사항&quot; 확인란 [Experience Cloud 환경 설정](https://experience.adobe.com/preferences) | X |
| Cloud Manager 파이프라인 상태 | 파이프라인의 상태에 대한 정보 | 비즈니스 소유자, 프로그램 관리자 또는 배포 관리자 역할을 가진 사용자, &quot;기타&quot; 확인란은 [Experience Cloud 환경 설정](https://experience.adobe.com/preferences) |  |

## 지원되는 알림 유형 {#supported-notification-types}

다음 표에는 현재 지원되는 알림 유형이 나열되어 있습니다.

| 알림 유형 | 관련 제품 프로필 | 수정 조치 |
|---|---|---|
| 차단된 복제 대기열 | 인시던트 | [복제 문서](/help/operations/replication.md#troubleshooting)의 지침에 따라 대기열 차단을 해제합니다. |
| 만료되는 S2S 인증서 | 사전 알림 | [서버측 API용 액세스 토큰 생성 문서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials)에서 자격 증명을 새로 고치는 방법에 대해 알아보십시오. |

