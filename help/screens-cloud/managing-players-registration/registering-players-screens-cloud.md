---
title: 화면에서 플레이어 등록 as a Cloud Service
description: 이 페이지에서는 Screens에서 as a Cloud Service으로 플레이어를 등록하는 방법에 대해 설명합니다.
exl-id: 1a0d6b22-71b1-4f3c-acaa-82d8d9c0f81a
source-git-commit: fb82970154fa37e3b3d1591a2e25989853ec6b90
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 1%

---

# 화면에서 플레이어 등록 as a Cloud Service {#registering-players-screens-cloud}

Screens as a Cloud Service으로 플레이어를 설치 및 구성한 후에는 플레이어를 등록해야 합니다.

## 목표 {#objective}

이 문서는 Screens Services Provider에 플레이어를 등록하는 데 도움이 됩니다. 문서를 읽고 나면 다음 작업을 수행할 수 있습니다.

* 플레이어 등록 방법 이해
* screens Services Provider에서 등록 프로세스를 완료하는 방법

## Screens 플레이어 등록 단계 {#register-players}

플레이어를 Screens에 as a Cloud Service으로 설치한 후에는 Screens Services Provider에서 플레이어를 등록할 준비가 되었습니다.

플레이어를 등록하려면 아래 단계를 따르십시오.

1. Screens Services Provider에 로그인합니다.

1. 다음으로 이동 **등록 코드** 아래에 **플레이어 관리** 왼쪽 탐색 패널에서 을(를) 클릭하고 **코드 만들기**.

   >[!NOTE]
   >유효/만료되지 않은 코드가 없는 경우 코드 만들기를 클릭하고 코드 이름을 입력한 다음 요구 사항에 따라 만료 설정을 선택합니다.

   ![이미지](/help/screens-cloud/assets/player/register-player1.png)

1. 에서 다음 필드 채우기 **등록 코드 만들기** 대화 상자:

   ![이미지](/help/screens-cloud/assets/player/register-player2.png)

   1. **등록 코드 이름**: 등록 코드 이름
   1. **등록 코드 만료**: 등록 코드 만료일
   1. **사용 제한**: 버튼을 토글하여 등록 코드의 사용 제한을 해제합니다. 사용 제한 옵션은 기본적으로 꺼져 있습니다.
   1. **사용 제한**: 사용 한도 숫자 선택

1. 클릭 **만들기** 을 클릭하여 등록 코드를 만듭니다. 목록에 등록 코드가 있는 플레이어가 표시됩니다.

   ![이미지](/help/screens-cloud/assets/player/register-player3.png)

1. 열 아래의 값을 클릭합니다. **등록 코드**  를 클릭하여 값을 클립보드에 복사합니다.

1. 다음 위치에 이 값 붙여넣기 **코드 입력** 의 필드 **플레이어 등록** AEM Screens 플레이어의 관리 UI에서 탭을 클릭하고 을 클릭합니다. **등록**.

   ![이미지](/help/screens-cloud/assets/player/register-player4.png)


1. 코드를 추가하면 플레이어가 이제 플레이어의 관리 UI에서 등록됩니다.

   ![이미지](/help/screens-cloud/assets/player/register-player5.png)

1. 이제 이 플레이어가 다음에 표시되는 것을 볼 수 있습니다. **플레이어** 왼쪽 탐색 패널에서 가져옵니다. Screens Services Provider에 표시되는 코드는 **시스템 정보** [플레이어 코드] 아래의 [관리 UI]에 있는 패널

   ![이미지](/help/screens-cloud/assets/player/register-player6.png)

   >[!IMPORTANT]
   >**등록 코드를 사용하는 동안 보안 모범 사례 권장 사항**
   >가장 좋은 방법은 등록 코드 사용을 제한하는 것입니다. 등록 코드가 손상되었지만 등록 수가 100개로 제한되어 있는 경우 공격자는 해당 숫자까지만 등록할 수 있지만 그 이상은 등록할 수 없습니다. 등록 코드가 생성되고 고객의 플레이어가 이미 등록된 후 언제든지 사용 제한을 업데이트할 수 있습니다. 고객이 특정 등록 코드에 대해 특이한 등록 활동을 관찰할 경우 조사하는 동안 실시간으로 한도를 낮출 수 있으며 이미 등록된 선수에게 영향을 주지 않고 잘못된 알람인 경우 횟수를 다시 늘릴 수 있다.


## 다음 단계 {#whats-next}

이제 플레이어를 클라우드 모드로 설치 및 구성했으므로 다음 문서를 검토하여 Screens as a Cloud Service 여정을 계속해야 합니다. [Screens의 디스플레이에 as a Cloud Service 플레이어 할당](/help/screens-cloud/managing-players-registration/assigning-player-display.md) Screens Services 공급자에서 가져왔습니다.
