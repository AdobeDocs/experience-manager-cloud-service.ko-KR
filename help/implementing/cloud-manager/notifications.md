---
title: 알림
description: Adobe Experience Cloud 알림 시스템을 사용하여 파이프라인 배포에 대한 정보를 받는 방법을 알아봅니다.
exl-id: c1c740b0-c873-45a8-9518-a856db2be75b
source-git-commit: 451b5a089645004c58c2674fd1fb13afbe1201cf
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 9%

---


# 알림 {#notifications}

Cloud Manager가 중요한 이벤트를 알리는 방법에 대해 알아보십시오.

## Cloud Manager의 알림 {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] 프로덕션 배포가 시작될 때 프로덕션 파이프라인이 시작되고 완료(성공 또는 실패)되면 알림을 보냅니다.

이러한 알림은 을 통해 전송됩니다 [!UICONTROL Experience Cloud] 알림 시스템 **비즈니스 소유자**, **프로그램 관리자**, 및 **배포 관리자** 역할.

내의 사이드바에 알림이 나타납니다 [!UICONTROL Cloud Manager] Adobe 전체에서 [!UICONTROL Experience Cloud]. 새 알림이 있을 때 헤더의 벨 아이콘에 배지가 표시됩니다.

![알림 아이콘](assets/notifications-bell-badged.png)

사이드바를 열고 알림을 보려면 벨 아이콘을 클릭합니다. 다음 **알림 을 참조하십시오** 사이드바의 탭에 배포 확인과 같은 최신 알림이 나열됩니다. 알림은 환경에 영향을 줍니다.

![알림 사이드바](assets/notifications-activities.png)

다음 **공지** 탭에는 Adobe 제품 공지가 포함되어 있습니다. 발표 내용은 제품에 관한 것입니다.

![알림 사이드바](assets/notificaitons-announcements.png)

알림 또는 알림을 클릭하여 세부 사항을 확인합니다. 파이프라인 배포와 같은 활동과 연결된 알림을 사용하면 파이프라인 실행 창과 같은 해당 활동의 세부 사항을 볼 수 있습니다.

을(를) 클릭합니다. **모두 보기** 받은 편지함에서 모든 알림을 보려면 패널 하단에 있는 옵션을 선택합니다.

을(를) 클릭합니다. **모두 읽은 상태로 표시** 패널 하단에 있는 옵션을 사용하여 읽지 않은 모든 알림을 읽음으로 표시하고 벨 아이콘 배지 지우기를 선택합니다.

## 알림 구성 {#configuration}

알림을 받는 방법 및 받는 알림을 사용자 지정할 수 있습니다.

알림 사이드바 상단에 있는 톱니바퀴 아이콘을 클릭합니다.

![알림 설정 아이콘](assets/notifications-configuration.png)

이렇게 하면 **Experience Cloud 환경 설정** 창에서 알림 구독을 정의하고 알림을 받는 방법을 정의할 수 있습니다.

### 구독 {#subscriptions}

구독은 알림을 받는 제품과 알림을 정의합니다.

![알림 구독](assets/notifications-subscriptions.png)

기본적으로 모든 제품에 대한 모든 알림을 받게 됩니다. 클릭 **사용자 지정** 제품 옆에 해당 제품에 대해 받은 알림 유형을 정의합니다.

![알림 구독 사용자 지정](assets/notifications-subscriptions-customize.png)

### 우선 순위 {#priority}

우선 순위 경고는 **높음** 태그로서, 경고 전용으로 수신되도록 구성할 수 있습니다. 에서 **우선순위** 섹션에서 우선 순위 알림으로 적합한 카테고리를 정의할 수 있습니다.

![알림 우선 순위](assets/notifications-priority.png)

드롭다운을 사용하여 우선순위로 적합한 카테고리 목록에 추가합니다. 카테고리 이름 옆에 있는 X 를 클릭하여 제거합니다.

### 경고 {#alerts}

경고는 창의 오른쪽 상단 모서리에 몇 초 동안 표시됩니다. 를 사용하십시오 **경고** 섹션을 통해 경고를 받은 알림을 정의합니다.

![알림 경고](assets/notifications-alerts.png)

경고 동작을 정의할 수 있습니다.

* **다음에 대한 경고 표시** - 경고를 트리거하는 알림 유형을 정의합니다
* **경고를 닫을 때까지 화면에 경고가 표시됩니다** - 경고를 무시하지 않으면 경고가 지속되는지 여부를 제어합니다
* **기간** - 경고가 화면에 계속 표시되도록 선택하지 않은 경우 경고가 화면에 남아 있어야 하는 시간을 정의합니다.

### 이메일 {#emails}

Adobe 간 웹 사용자 인터페이스에서 알림을 사용할 수 있습니다 [!UICONTROL Experience Cloud] 솔루션. 또한 이러한 알림이 **이메일** 섹션을 참조하십시오.

![알림 이메일](assets/notifications-emails.png)

기본적으로 이메일은 전송되지 않습니다. 다음과 같이 이메일을 수신하도록 선택할 수 있습니다.

* 즉시
* 일별
* 주별

When **인스턴트 알림** 을(를) 선택하면 모든 알림에 대해 이메일이 즉시 전송됩니다. 대상 **일별 다이제스트** 및 **주간 다이제스트** 일별 다이제스트가 전송되는 시점과 주별 다이제스트 전송 시점을 선택할 수 있습니다.