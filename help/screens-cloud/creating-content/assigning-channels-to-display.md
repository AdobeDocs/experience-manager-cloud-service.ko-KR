---
title: 화면 내 디스플레이에 채널 할당 as a Cloud Service
description: 이 페이지에서는 Screens의 디스플레이에 as a Cloud Service으로 채널을 할당하는 방법을 설명합니다.
exl-id: ba001c18-7b05-4ae2-aa7f-9ebb320fedd0
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 2%

---

# 화면 내 디스플레이에 채널 할당 as a Cloud Service {#assign-channel-displays-screens-cloud}

프로젝트 설정이 완료되면 콘텐츠를 보려면 채널을 디스플레이에 할당해야 합니다.

## 목표 {#objective}

이 문서는 디스플레이가 준비되고 채널에 콘텐츠를 추가하고 게시한 후 디스플레이에 채널을 할당하는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면 Screens Services Provider에서 디스플레이에 채널을 할당하는 방법을 이해할 수 있어야 합니다.

## 사전 요구 사항 {#prerequisites}

아래 단계를 수행하여 디스플레이에 채널을 할당하려면 먼저 학습을 완료해야 합니다.

* 디스플레이 만들기 및 관리
* 채널 만들기 및 관리

## 디스플레이에 채널 할당 단계 {#assign-channel-to-display}

채널을 디스플레이에 할당하려면 아래 단계를 따르십시오.

1. Screens Services Provider로 이동하여 **표시** 왼쪽 탐색 패널에서 가져옵니다.

1. 클릭 **채널 할당** 화면에 표시합니다.

   ![이미지](/help/screens-cloud/assets/display/assignchannel-1.png)

1. 에서 다음 필드 채우기 **채널 할당** 대화 상자.

   ![이미지](/help/screens-cloud/assets/display/assignchannel-2.png)

   1. 드롭다운에서 채널 이름을 선택합니다.
   1. 우선 순위를 선택합니다.

      >[!NOTE]
      >여러 할당이 재생 기준과 일치하는 경우 우선 순위를 사용하여 할당을 정렬합니다. 값이 가장 높은 것이 항상 낮은 값보다 우선합니다. 예를 들어, 두 개의 채널 A와 B가 있는 경우. A는 우선 순위가 1이고 B는 우선 순위가 2이므로 A보다 우선 순위가 높은 채널 B가 표시됩니다.

   1. 다음 날짜의 시작 날짜 및 종료 날짜를 선택합니다. **활성화**.

1. 클릭 **+ 자동연장 추가** 채널에 대한 반복 일정을 추가합니다.

   ![이미지](/help/screens-cloud/assets/create-content/recurrence-1.png)

   >[!NOTE]
   >채널에 여러 개의 반복 일정을 추가할 수 있습니다. 반복 일정에는 특정 시간에 여러 채널이 실행되는 글로벌 일정을 설정하고 모든 디스플레이에 대해 설정된 일정을 한 번에 재사용할 수 있는 DayParting이 도입됩니다.

   다음 옵션을 설정할 수 있습니다.

   * **이름**: 반복 일정의 제목입니다.
   * **반복**: 일정이 일별, 주별, 월별 또는 연별로 실행되는지 선택합니다.
   * **시작**: 예약의 시작 시간입니다.
   * **종료**: 일정의 종료 시간입니다. 시간 또는 기간에 따라 설정할 수 있습니다.
   * **시간**: 일정이 지정된 시간에 종료됩니다.
   * **기간**: 일정은 시간 또는 분 단위의 특정 기간 동안 실행됩니다.

1. **만들기**&#x200B;를 클릭합니다. 아래 그림과 같이 해당 디스플레이에 채널이 할당되어 있음을 알 수 있습니다.

   ![이미지](/help/screens-cloud/assets/display/assignchannel-3.png)


## 다음 단계 {#whats-next}

이제 여정에 채널을 할당했으므로 다음 문서를 검토하여 Screens as a Cloud Service 채널을 계속해야 합니다 [Screens Player for AEM as a Cloud Service 설치 및 구성](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md).
