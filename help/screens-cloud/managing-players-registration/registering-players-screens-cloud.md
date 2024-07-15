---
title: Screensas a Cloud Service 에 플레이어 등록
description: 이 페이지에서는 Screensas a Cloud Service 에서 플레이어를 등록하는 방법에 대해 설명합니다.
exl-id: 1a0d6b22-71b1-4f3c-acaa-82d8d9c0f81a
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 13%

---

# Screensas a Cloud Service 에 플레이어 등록 {#registering-players-screens-cloud}

Screensas a Cloud Service 용 플레이어를 설치하고 구성한 후에는 플레이어를 등록해야 합니다.

## 목표 {#objective}

이 문서는 Screens 서비스 공급자의 플레이어 등록을 이해하는 데 도움이 됩니다. 문서를 읽고 나면 다음 작업을 수행할 수 있습니다.

* 플레이어 등록 방법 이해
* Screens 서비스 공급자로부터 등록 프로세스를 완료하는 방법

## Screens 플레이어 등록 단계 {#register-players}

Screensas a Cloud Service 에 플레이어를 설치하면 Screens 서비스 공급자로부터 플레이어를 등록할 준비가 된 것입니다.

플레이어를 등록하려면 아래 단계를 따르십시오.

1. Screens 서비스 공급자에 로그인합니다.

1. 왼쪽 탐색 패널에서 **플레이어 관리** 아래의 **등록 코드**(으)로 이동한 다음 **코드 만들기**&#x200B;를 클릭합니다.

   >[!NOTE]
   >유효/만료되지 않은 코드가 없는 경우 코드 만들기를 클릭하고 코드 이름을 입력한 다음 요구 사항에 따라 만료 설정을 선택합니다.

   ![이미지](/help/screens-cloud/assets/player/register-player1.png)

1. **등록 코드 만들기** 대화 상자에서 다음 필드를 채웁니다.

   ![이미지](/help/screens-cloud/assets/player/register-player2.png)

   1. **등록 코드 이름**: 등록 코드 이름
   1. **등록 코드 만료**: 등록 코드 만료일
   1. **사용 제한**: 등록 코드의 사용 제한을 끄려면 단추를 전환합니다. 사용 제한 옵션은 기본적으로 꺼져 있습니다.
   1. **사용 제한**: 사용 제한 번호를 선택하세요.

1. 등록 코드를 만들려면 **만들기**&#x200B;를 클릭합니다. 목록에 등록 코드가 있는 플레이어를 볼 수 있습니다.

   ![이미지](/help/screens-cloud/assets/player/register-player3.png)

1. **등록 코드** 열 아래의 값을 클릭하여 값을 클립보드에 복사합니다.

1. AEM Screens 플레이어의 관리 UI에서 **플레이어 등록** 탭의 **코드 입력** 필드에 이 값을 붙여 넣고 **등록**&#x200B;을 클릭합니다.

   ![이미지](/help/screens-cloud/assets/player/register-player4.png)


1. 코드를 추가하면 이제 플레이어가 플레이어의 관리 UI에서 등록되었음을 확인할 수 있습니다.

   ![이미지](/help/screens-cloud/assets/player/register-player5.png)

1. 이제 왼쪽 탐색 패널에서 이 플레이어가 **플레이어**&#x200B;에 표시되는 것을 볼 수 있습니다. Screens 서비스 공급자에 표시되는 코드는 플레이어 코드 아래의 관리 UI에 있는 **시스템 정보** 패널과 일치합니다.

   ![이미지](/help/screens-cloud/assets/player/register-player6.png)

   >[!IMPORTANT]
   >등록 코드를 사용하는 동안 **보안 모범 사례 권장 사항**
   >모범 사례로서 등록 코드 사용을 제한할 수 있습니다. 등록 코드가 침해되더라도 등록이 100개로 제한되어 있는 경우 공격자는 해당 수까지만 등록할 수 있고 이를 초과해서는 등록할 수 없습니다. 등록 코드가 생성되고 고객의 플레이어 중 일부가 이미 등록된 후 언제든지 사용 제한을 업데이트할 수 있습니다. 고객이 특정 등록 코드에 대해 특이한 등록 활동을 관찰할 경우 조사하는 동안 실시간으로 한도를 낮출 수 있으며 이미 등록된 선수에게 영향을 주지 않고 잘못된 알람인 경우 횟수를 다시 늘릴 수 있다.


## 다음 단계 {#whats-next}

이제 플레이어를 클라우드 모드로 설치 및 구성했으므로 다음 문서인 Screens as a Cloud Service 여정을 계속 검토하여 Screens 서비스 공급자의 [Screens에 as a Cloud Service 지정](/help/screens-cloud/managing-players-registration/assigning-player-display.md)을(를) 검토해야 합니다.
