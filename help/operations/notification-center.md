---
title: 알림 센터
description: 알림 센터를 활용하여 인시던트 및 기타 중요한 정보에 대한 조치를 편리하게 취할 수 있습니다
hidefromtoc: true
source-git-commit: a5977c667d831c47d41cd86b68e9196fbe726899
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# 알림 센터 {#notification-center}

>[!NOTE]
>이 기능은 아직 릴리스되지 않았습니다.

구성이 완료되면 AEM as Cloud Service은 고객이 조치를 취해야 하는 중요한 정보에 대한 알림을 전송합니다. 알림의 예로는 차단된 큐 또는 만료되는 자격 증명 세트가 있습니다. 전체 알림 유형 세트는 다음에서 볼 수 있습니다. [아래 표](#current-notification-types), 및 는 시간이 지남에 따라 확장됩니다. 알림은 이메일을 통해 그리고 Adobe Experience Cloud 전체에서 오른쪽 상단 모서리에 있는 벨 아이콘을 클릭하여 액세스할 수 있는 알림 위젯 아래의 새 항목으로 수신됩니다. 알림 설정을 구성할 수 있습니다.

알림을 받으면, 고객이 취해야 할 권장 조치를 설명하는 추가 컨텍스트를 표시하는 팝업과 함께 AEMas a Cloud Service 의 알림 센터를 열기 위해 클릭할 수 있습니다.

방금 클릭한 알림에 대한 정보를 표시하는 것 외에도 알림 센터는 현재 및 이전 알림 세트를 보고 관리할 수 있는 허브 역할을 합니다. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

알림에는 두 가지 높은 수준 카테고리가 있습니다.

1. 인시던트 - 이벤트가 발생했으며 일반적으로 신속한 해결이 필요합니다. 예를 들어 차단된 큐를 해결하는 경우
1. 사전 예방적 - Adobe은 고객이 가까운 미래에 취해야 하는 작업에 대한 권장 사항이 있습니다. 예를 들어 더 이상 사용되지 않는 UI 참조를 중단하려면 다음을 수행하십시오.

다음을 참조하십시오. [아래 표](#current-notification-types) 현재 지원되는 알림에 대해 설명합니다.

알림 센터 화면에서 특정 프로그램 및 환경을 선택할 수 있으며, 이는 해당 범위에 대한 필터링의 효과가 있습니다.

## 구성 {#configuration}

아래 단계에 따라 수신 알림을 구성할 수 있습니다.

1. 설명된 대로 다음 제품 프로필을 만듭니다 [이 문서에서](/help/journey-onboarding/user-groups.md)를 통해 조직의 적절한 Adobe ID를 해당 프로필에 할당합니다.
1. 알림 구성 설정을 결정합니다. [이 페이지에서](https://experience.adobe.com/preferences/notification-section), Experience Manager 구독이 활성화되어 있고 **기타** 확인란이 선택되어 있습니다. 또한 이메일 섹션을으로 설정하는 것이 좋습니다. **인스턴트 알림** 따라서 인시던트가 발생한 후 즉시 알림을 받게 됩니다.

>[!NOTE]
>구독은 조직 수준에서 작동하므로 구독자는 해당 프로그램 내의 모든 프로그램 및 환경에 대한 알림을 받게 됩니다.

## 자세한 사용자 흐름 {#detailed-user-flow}

이메일을 클릭하면 알림 센터로 이동하며, 클릭한 알림에 대한 컨텍스트와 경우에 따라 수정 조치를 수행하는 방법을 설명하는 추가 정보에 대한 링크를 표시하는 팝업이 있습니다.

![문제 세부 정보](/help/operations/assets/incident-details.png)

클릭 **자세히 알아보기** 링크는 사용자를 아래 표에서 알림을 참조할 수 있는 이 문서로 안내하며, 이는 수행할 작업에 대한 지침을 제공합니다.

알림 센터에서 다른 최근 알림 목록을 볼 수 있습니다. [작업] 목록을 사용하여 조직에서 작업을 인식하고 있음을 Adobe에게 알리기 위해 알림을 승인하고 나중에 해결 조치가 취해진 경우 알림을 해결하는 것이 좋습니다.

![알림 목록](/help/operations/assets/notification-list.png)

대부분의 경우 알림은 문제를 해결하는 데 필요한 모든 컨텍스트를 제공해야 합니다. 하지만 Adobe 지원에 대한 질문이 있는 경우 **지원 문의** 알림 팝업의 링크입니다. 이렇게 하면 질문에 대해 설명하고 지원 티켓을 제출하여 지원 티켓을 만들 수 있는 양식이 표시됩니다. 이 양식에는 Adobe 지원 엔지니어가 관련 컨텍스트를 갖도록 특정 알림에 대한 참조가 포함됩니다.

![지원 문의 1](/help/operations/assets/contact-support1.png)

![지원 문의 2](/help/operations/assets/contact-support2.png)

모든 지원 티켓과 마찬가지로 [Adobe Admin Console의 지원 사례 탭](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html)를 추적하여 주석을 추가할 수 있습니다.

![Admin Console 지원](/help/operations/assets/admin-console-support.png)

## 현재 알림 유형 {#current-notification-types}

아래 표에는 현재 지원되는 알림 유형이 나와 있습니다

| 알림 유형 | 관련 제품 프로필 | 수정 작업 |
|---|---|---|
| 복제 큐 차단 | 문제 | 의 지침에 따라 큐 차단 해제 [복제 설명서](/help/operations/replication.md#troubleshooting) |
| S2S 인증서 만료 | 사전 예방 | 에서 자격 증명을 새로 고치는 방법을 알아봅니다. [서버측 API에 대한 액세스 토큰 생성 설명서](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) |
