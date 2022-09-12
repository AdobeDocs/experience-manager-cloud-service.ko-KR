---
title: 화면의 디스플레이에 채널 as a Cloud Service 할당
description: 이 페이지에서는 Screens의 디스플레이에 채널을 할당하는 방법을 as a Cloud Service으로 설명합니다.
exl-id: ba001c18-7b05-4ae2-aa7f-9ebb320fedd0
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 19%

---

# 화면의 디스플레이에 채널 as a Cloud Service 할당 {#assign-channel-displays-screens-cloud}

프로젝트 설정이 완료되면 컨텐츠를 보려면 채널을 디스플레이에 지정해야 합니다.

## 목표 {#objective}

디스플레이가 준비되고 채널에 컨텐츠를 추가하고 게시하면 디스플레이에 채널을 할당하는 방법을 이해하는 데 도움이 됩니다. 읽기 후에는 Screens 서비스 제공업체에서 디스플레이에 채널을 할당하는 방법을 이해할 수 있어야 합니다.

## 사전 요구 사항 {#prerequisites}

디스플레이에 채널을 지정하려면 아래 단계를 수행해야 합니다.

* 디스플레이 생성 및 관리
* 채널 생성 및 관리

## 디스플레이에 채널 지정 단계 {#assign-channel-to-display}

아래 절차에 따라 디스플레이에 채널을 지정하십시오.

1. Screens 서비스 공급자로 이동하고 을 선택합니다 **표시** 왼쪽 탐색 패널

1. 클릭 **채널 지정** 표시합니다.

   ![이미지](/help/screens-cloud/assets/display/assignchannel-1.png)

1. 다음 필드 채우기 **채널 할당** 대화 상자

   ![이미지](/help/screens-cloud/assets/display/assignchannel-2.png)

   1. 드롭다운에서 채널 이름을 선택합니다.
   1. 우선 순위를 선택합니다.

      >[!NOTE]
      >우선 순위는 여러 지정 내용이 재생 기준을 충족하는 경우 지정 내용의 순서를 정하는 데 사용됩니다. 값이 가장 높은 지정은 낮은 값의 지정보다 항상 우선합니다. 예를 들어, 두 개의 채널 A와 B가 있고 A의 우선 순위는 1이고 B의 우선 순위는 2라면, 채널 B의 우선 순위가 A보다 높으므로 채널 B가 표시됩니다.
   1. 시작 날짜 및 종료 날짜부터 선택합니다 **활성화**.

1. 클릭 **+ 되풀이 추가** 채널에 대한 되풀이 일정을 추가하려면 다음을 수행하십시오.

   ![이미지](/help/screens-cloud/assets/create-content/recurrence-1.png)

   >[!NOTE]
   >여러 개의 반복 일정을 채널에 추가할 수 있습니다. 되풀이 일정에서는 DayParting을 도입하여 하루 중 특정 시간에 실행 중인 여러 채널을 사용하여 전역 일정을 설정하고 해당 설정을 모든 디스플레이에 한 번에 다시 사용할 수 있습니다.

   다음 옵션을 설정할 수 있습니다.

   * **이름**: 되풀이 일정의 제목입니다.
   * **반복**: 일정이 일별, 주별, 월별 또는 연간 중 어느 것을 실행할지 선택합니다.
   * **시작**: 예약의 시작 시간입니다.
   * **종료**: 예약의 종료 시간입니다. 시간 또는 기간별로 설정할 수 있습니다.
   * **시간**: 일정이 지정된 시간에 종료됩니다.
   * **기간**: 예약은 특정 시간(시간 또는 분) 동안 실행됩니다.

1. 클릭 **만들기** 이제 아래 그림과 같이 해당 디스플레이에 대해 채널이 할당되었음을 볼 수 있습니다.

   ![이미지](/help/screens-cloud/assets/display/assignchannel-3.png)


## 다음 단계 {#whats-next}

이제 디스플레이에 채널을 지정했으므로, 다음 번에 문서를 검토하여 스크린 as a Cloud Service 여정을 계속해야 합니다 [AEM as a Cloud Service Screens 플레이어 설치 및 구성](/help/screens-cloud/managing-players-registration/installing-screens-cloud-player.md).
