---
title: 작업 센터
description: 문제 및 기타 중요한 정보에 대한 조치를 편리하게 취하려면 조치 센터를 활용하십시오.
hidefromtoc: true
hide: true
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: ca7cad567a5f83cd1edc14def6d961b8ba3b7f1f
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 32%

---

# 작업 센터 {#actions-center}

>[!NOTE]
>이 기능은 릴리스되지 않았습니다.

AEM as Cloud Service은 즉각적인 조치가 필요한 중요한 인시던트가 발생하면 작업 센터 이메일 알림과 최적화를 위한 사전 권장 사항을 보냅니다. 예를 들어 차단된 큐 또는 만료되는 자격 증명 세트가 있습니다. 전체 작업 센터 알림 유형 세트는 다음에서 볼 수 있습니다. [아래 표](#supported-notification-types): 시간이 지남에 따라 확장합니다.

작업 센터 이메일 알림이 수신되면 을 클릭하여 AEM as a Cloud Service의 작업 센터를 열 수 있으며 이 작업 센터에는 고객이 수행할 작업을 설명하는 추가 컨텍스트가 표시되는 팝업이 있습니다.

방금 클릭한 이메일 알림에 대한 정보를 표시하는 것 외에도 작업 센터는 현재 및 이전 알림 세트를 보고 관리할 수 있는 허브 역할을 합니다. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

작업 센터에 표시되는 두 가지 높은 수준의 알림 범주가 있습니다.

1. 운영 인시던트 - 일반적으로 신속한 해결이 필요한 이벤트가 발생했습니다. 예: 차단된 대기열 해결.
1. 사전 알림 추천 - Adobe는 가까운 미래에 고객이 취해야 할 조치에 대한 추천을 제시합니다. 예: 더 이상 사용되지 않는 UI 참조를 중지합니다.

다음을 참조하십시오. [아래 표](#supported-notification-types) ( 작업 센터에서 현재 지원되는 알림).

작업 센터에서 특정 프로그램 및 환경을 선택할 수 있으며 이는 해당 범위에 대한 필터링의 효과가 있습니다.

## 구성 {#configuration}

수신 작업 센터 이메일 알림을 구성하려면 설명된 제품 프로필을 만듭니다 [이 문서에서](/help/journey-onboarding/notification-profiles.md)문제 알림 - Cloud Service 및 사전 알림 - Cloud Service. 또한 조직의 적절한 Adobe ID를 해당 프로필에 할당합니다. 이를 통해 관리자는 이러한 이메일 알림을 받을 자격이 있는 사용자를 결정할 수 있습니다.

>[!NOTE]
>작업 센터 이메일 알림은 조직 수준에서 작동하므로 구독자는 해당 프로그램 내의 모든 프로그램 및 환경에 대한 알림을 받게 됩니다.

## 자세한 사용자 흐름 {#detailed-user-flow}

이메일을 클릭하면 경고 센터로 이동합니다. 이때 클릭한 알림에 대한 컨텍스트와 경우에 따라 수정 조치를 수행하는 방법을 설명하는 추가 정보 링크가 표시됩니다.

![인시던트 세부 정보](/help/operations/assets/incident-details.png)

클릭 **자세히 알아보기** 링크 사용자를 이 문서로 이동합니다. 여기에서 알림 유형을 참조할 수 있습니다. [지원되는 알림 유형 테이블](#supported-notification-types) 아래에서 수행할 작업에 대한 지침을 제공합니다.

작업 센터에서 다른 최근 알림 목록을 볼 수 있습니다. 조직이 작업을 인식하고 있음을 Adobe에 알리고, 나중에 수정 조치가 취해졌을 때 알림을 해결하기 위해 작업 목록을 사용하여 알림을 확인하는 것이 좋습니다.

![알림 목록](/help/operations/assets/notification-list.png)

대부분의 경우 팝업은 문제를 해결하는 데 필요한 모든 컨텍스트를 제공해야 합니다. 하지만 Adobe 지원에 대한 질문이 있는 경우 **지원 문의** 팝업에 연결합니다. 이렇게 하면 질문에 대해 설명하고 지원 티켓을 제출하여 Adobe 지원 엔지니어가 관련 컨텍스트를 갖도록 특정 알림에 대한 참조도 포함하는 양식이 표시됩니다.

![지원에 문의 1](/help/operations/assets/contact-support1.png)

![지원에 문의 2](/help/operations/assets/contact-support2.png)

모든 지원 티켓과 마찬가지로 지원 티켓이 [Adobe Admin Console의 지원 사례 탭](https://helpx.adobe.com/kr/enterprise/using/support-for-enterprise.html)에 나타나며, 여기에서 지원 티켓을 추적하고 추가 설명을 추가할 수 있습니다.

![Admin Console 지원](/help/operations/assets/admin-console-support.png)

## 어떤 알림이 표시됩니까? {#which-notification}

AEM as a Cloud Service에는 여러 유형의 알림이 있지만 아래 표에 표시된 것처럼 작업 센터에 하위 집합만 표시됩니다.

| 알림 유형 | 설명 | 구성하는 방법 | 경고 센터에 나타남 |
|---|---|---|---|
| 운영 인시던트 | 즉각적인 조치가 필요한 중대 인시던트 | &quot;문제 알림 - Cloud Service&quot; 제품 프로필에 할당된 사용자 | X |
| 사전 알림 추천 | 계획을 수립해야 하는 최적화 | &quot;사전 알림 - Cloud Service&quot; 제품 프로필에 할당된 사용자 | X |
| Cloud Manager 파이프라인 상태 | 파이프라인 상태에 대한 정보 | 비즈니스 소유자 역할, 프로그램 관리자 역할 또는 배포 관리자 역할이 주어진 사용자, [Experience Cloud 환경 설정](https://experience.adobe.com/preferences)에서 선택한 “기타” 확인란, 로서의 [여기에 설명됨](/help/implementing/cloud-manager/notifications.md). |  |

## 지원되는 알림 유형 {#supported-notification-types}

다음 표에는 작업 센터에서 현재 지원되는 알림 유형이 나와 있습니다.

| 알림 유형 | 관련 제품 프로필 | 수정 조치 |
|---|---|---|
| 차단된 복제 대기열 | 인시던트 | [복제 문서](/help/operations/replication.md#troubleshooting)의 지침에 따라 대기열 차단을 해제합니다. |
| 만료되는 S2S 인증서 | 사전 알림 | [서버측 API용 액세스 토큰 생성 문서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials)에서 자격 증명을 새로 고치는 방법에 대해 알아보십시오. |

