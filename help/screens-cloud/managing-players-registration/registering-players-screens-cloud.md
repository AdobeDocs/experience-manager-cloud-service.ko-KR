---
title: Screens의 플레이어 등록 as a Cloud Service
description: 이 페이지에서는 Screens에서 플레이어를 as a Cloud Service으로 등록하는 방법을 설명합니다.
exl-id: 1a0d6b22-71b1-4f3c-acaa-82d8d9c0f81a
source-git-commit: fb82970154fa37e3b3d1591a2e25989853ec6b90
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 1%

---

# Screens의 플레이어 등록 as a Cloud Service {#registering-players-screens-cloud}

Screens용 플레이어를 설치하고 as a Cloud Service으로 구성한 후에는 플레이어를 등록해야 합니다.

## 목표 {#objective}

이 문서는 Screens 서비스 공급자의 플레이어 등록을 이해하는 데 도움이 됩니다. 읽고 나면 다음을 수행할 수 있습니다.

* 플레이어를 등록하는 방법 이해
* screens 서비스 제공자에서 등록 프로세스를 완료하는 방법

## Screens 플레이어 등록 단계 {#register-players}

플레이어를 Screens as a Cloud Service에 설치하면 Screens 서비스 공급자에서 플레이어를 등록할 수 있습니다.

아래 절차에 따라 플레이어를 등록하십시오.

1. Screens 서비스 공급자에 로그인합니다.

1. 다음으로 이동 **등록 코드** 아래에 **플레이어 관리** 왼쪽 탐색 패널에서 을(를) 클릭하고 **코드 만들기**.

   >[!NOTE]
   >유효한/만료되지 않은 코드가 없는 경우 코드 만들기를 클릭하고 코드 이름을 입력하고 요구 사항에 따라 만료 설정을 선택합니다.

   ![이미지](/help/screens-cloud/assets/player/register-player1.png)

1. 에서 다음 필드를 채웁니다 **등록 코드 만들기** 대화 상자:

   ![이미지](/help/screens-cloud/assets/player/register-player2.png)

   1. **등록 코드 이름**: 등록 코드의 이름
   1. **등록 코드 만료**: 등록 코드의 만료 날짜
   1. **사용 제한**: 등록 코드의 사용 제한을 해제하려면 버튼을 전환합니다. 기본적으로 사용량 제한 옵션은 꺼져 있습니다.
   1. **사용 제한**: 사용 제한 번호를 선택합니다

1. 클릭 **만들기** 등록 코드를 만들려면 목록에 등록 코드가 있는 플레이어가 표시됩니다.

   ![이미지](/help/screens-cloud/assets/player/register-player3.png)

1. 열 아래에 있는 값을 클릭합니다 **등록 코드**  값을 클립보드에 복사합니다.

1. 이 값을 **코드 입력** 의 필드 **플레이어 등록** AEM Screens 플레이어의 관리 UI에서 탭을 클릭하고 **등록**.

   ![이미지](/help/screens-cloud/assets/player/register-player4.png)


1. 코드를 추가하면 플레이어가 플레이어의 관리 UI에서 등록된 것이 표시됩니다.

   ![이미지](/help/screens-cloud/assets/player/register-player5.png)

1. 이제 이 플레이어가 표시됩니다. **축구 선수** 왼쪽 탐색 패널 Screens 서비스 공급자에 표시되는 코드가 **시스템 정보** 플레이어 코드 아래에 있는 관리 UI의 패널입니다.

   ![이미지](/help/screens-cloud/assets/player/register-player6.png)

   >[!IMPORTANT]
   >**등록 코드를 사용하는 동안 보안 모범 사례 권장 사항**
   >가장 좋은 방법은 등록 코드 사용을 제한할 수 있습니다. 등록 코드가 손상되었지만 100개의 등록 제한이 있는 경우 공격자는 해당 번호까지만 등록할 수 있지만 더 이상 등록할 수 없습니다. 등록 코드가 생성되고 일부 고객의 플레이어가 이미 등록된 후에는 항상 사용 제한을 업데이트할 수 있습니다. 고객이 특정 등록 코드에 대한 비정상적인 등록 활동을 관찰하면 실시간으로 제한 사항을 낮출 수 있고, 잘못된 경보였다면 등록된 플레이어에게 영향을 주지 않고 숫자를 다시 늘릴 수 있습니다.


## 다음 단계 {#whats-next}

이제 플레이어를 클라우드 모드로 설치 및 구성했으므로 다음 번 문서를 검토하여 Screens as a Cloud Service 여정을 계속해야 합니다. [Screens에서 디스플레이에 플레이어 할당 as a Cloud Service](/help/screens-cloud/managing-players-registration/assigning-player-display.md) 스크린 서비스 공급자에서
