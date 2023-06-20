---
title: 액션 센터
description: 액션 센터를 활용하여 인시던트 및 기타 중요한 정보에 대해 편리하게 조치
hidefromtoc: true
hide: true
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: bceec9ea6858b1c4c042ecd96f13ae5cac1bbee5
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 94%

---

# 액션 센터 {#actions-center}

>[!NOTE]
>이 기능은 릴리스되지 않았습니다.

AEM as Cloud Service는 최적화에 즉각적인 조치와 사전 알림 추천이 필요한 중대 인시던트가 발생하면 액션 센터 이메일 알림을 전송합니다. 예로는 차단된 대기열 또는 만료되는 자격 증명 세트가 있습니다. 액션 센터 알림 유형의 전체 세트는 [아래 표](#supported-notification-types)에서 볼 수 있으며 시간이 지남에 따라 확장됩니다.

액션 센터 이메일 알림이 수신되면 클릭하여 AEM as a Cloud Service의 액션 센터를 열 수 있으며, 이때 고객이 취해야 할 조치를 설명하는 추가 컨텍스트를 표시하는 팝업이 함께 열립니다.

방금 클릭한 이메일 알림에 대한 정보를 표시하는 것 외에도 액션 센터는 현재 및 이전 알림 세트를 보고 관리할 수 있는 허브 역할을 합니다. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

액션 센터에 표시되는 두 가지 높은 수준의 알림 범주가 있습니다.

1. 운영 인시던트 - 일반적으로 신속한 해결이 필요한 이벤트가 발생했습니다. 예: 차단된 대기열 해결.
1. 사전 알림 추천 - Adobe는 가까운 미래에 고객이 취해야 할 조치에 대한 추천을 제시합니다. 예: 더 이상 사용되지 않는 UI 참조를 중지합니다.

액션 센터에서 현재 지원되는 알림은 [아래 표](#supported-notification-types)를 참조하십시오.

액션 센터에서 해당 범위에 대한 필터링 효과가 있는 특정 프로그램 및 환경을 선택할 수 있습니다.

## 구성 {#configuration}

액션 센터 이메일 알림 수신을 구성하려면 [이 문서](/help/journey-onboarding/notification-profiles.md)에 설명된 제품 프로필, 즉 인시던트 알림 - Cloud Service 및 사전 알림 - Cloud Service를 만듭니다. 또한 해당 프로필에 조직의 적절한 Adobe ID를 할당합니다. 이를 통해 관리자는 해당 이메일 알림을 수신하려는 사용자를 확인할 수 있습니다.

>[!NOTE]
>액션 센터 이메일 알림은 조직 수준에서 작동하므로 구독자는 해당 프로그램 내의 모든 프로그램 및 환경에 대한 알림을 수신합니다.

## 자세한 사용자 흐름 {#detailed-user-flow}

이메일을 클릭하면 클릭한 알림에 대한 컨텍스트를 표시하는 팝업과 경우에 따라 수정 조치를 취하는 방법을 설명하는 추가 정보 링크가 있는 액션 센터로 이동합니다.

![인시던트 세부 정보](/help/operations/assets/incident-details.png)

사용자는 **자세히 알아보기** 링크를 클릭하여 이 문서로 이동합니다. 아래에서 [지원되는 알림 유형 표](#supported-notification-types)와 같이 알림 유형을 참조할 수 있으며, 이 표는 어떤 조치를 취해야 하는지 지침을 제공합니다.

액션 센터에서 다른 최근 알림 목록을 볼 수 있습니다. [작업] 목록을 사용하면 조직에서 작업을 인식하고 있음을 Adobe에게 알리는 알림을 확인하고 나중에 해결 조치가 취해진 경우 알림을 해결하는 것이 좋습니다.

![알림 목록](/help/operations/assets/notification-list.png)

대부분의 경우 팝업은 문제를 해결하는 데 필요한 모든 컨텍스트를 제공합니다. 단, Adobe 지원에 대한 질문이 있는 경우 팝업에서 **지원에 문의** 링크를 클릭할 수 있습니다. 이렇게 하면 질문을 설명하고 지원 티켓을 만들기 위해 제출할 수 있는 양식이 표시되며, 여기에는 Adobe 지원 엔지니어가 관련 컨텍스트를 확보할 수 있도록 특정 알림에 대한 참조도 포함됩니다.

![지원에 문의 1](/help/operations/assets/contact-support1.png)

![지원에 문의 2](/help/operations/assets/contact-support2.png)

모든 지원 티켓과 마찬가지로 지원 티켓이 [Adobe Admin Console의 지원 사례 탭](https://helpx.adobe.com/kr/enterprise/using/support-for-enterprise.html)에 나타나며, 여기에서 지원 티켓을 추적하고 댓글을 추가할 수 있습니다.

![Admin Console 지원](/help/operations/assets/admin-console-support.png)

## 어떤 알림이 표시됩니까? {#which-notification}

AEM as a Cloud Service에는 여러 유형의 알림이 있지만 아래 그림과 같이 액션 센터에는 하위 집합만 표시됩니다.

| 알림 유형 | 설명 | 구성하는 방법 | 액션 센터에 표시 |
|---|---|---|---|
| 운영 인시던트 | 즉각적인 조치가 필요한 중대 인시던트 | “인시던트 알림 - Cloud Service” 제품 프로필에 할당된 사용자 | X |
| 사전 알림 추천 | 계획을 수립해야 하는 최적화 | “사전 알림 - Cloud Service” 제품 프로필에 할당된 사용자 | X |
| Cloud Manager 파이프라인 상태 | 파이프라인 상태에 대한 정보 | 비즈니스 소유자 역할, 프로그램 관리자 역할 또는 배포 관리자 역할이 주어진 사용자, [Experience Cloud 환경 설정](https://experience.adobe.com/preferences)에서 선택한 “기타” 확인란, [여기에 설명된](/help/implementing/cloud-manager/notifications.md) 바와 같이. |   |

## 지원되는 알림 유형 {#supported-notification-types}

다음 표는 액션 센터에서 현재 지원되는 알림 유형 목록입니다.

| 알림 유형 | 관련 제품 프로필 | 수정 조치 |
|---|---|---|
| 차단된 복제 대기열 | 인시던트 | [복제 문서](/help/operations/replication.md#troubleshooting)의 지침에 따라 대기열 차단을 해제합니다. |
| 만료되는 S2S 인증서 | 사전 알림 | [서버측 API용 액세스 토큰 생성 문서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials)에서 자격 증명을 새로 고치는 방법에 대해 알아보십시오. |

