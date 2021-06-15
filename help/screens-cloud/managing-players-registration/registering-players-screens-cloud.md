---
title: Screens의 플레이어를 Cloud Service으로 등록
description: 이 페이지에서는 Screens에 플레이어를 Cloud Service으로 등록하는 방법을 설명합니다.
hide: true
hidefromtoc: true
index: false
source-git-commit: f0e005ddc59c575188d15986cabdbe04cb48ad03
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 1%

---


# 스크린의 플레이어를 Cloud Service {#registering-players-screens-cloud} 로 등록

Screens용 플레이어를 Cloud Service으로 설치하고 구성한 후에는 플레이어를 등록해야 합니다.

## 목표 {#objective}

이 문서는 Screens 서비스 공급자의 플레이어 등록을 이해하는 데 도움이 됩니다. 읽고 나면 다음을 수행할 수 있습니다.

* 플레이어를 등록하는 방법 이해
* screens 서비스 제공자에서 등록 프로세스를 완료하는 방법

## 스크린 플레이어 {#register-players} 등록 단계

플레이어를 Cloud Service으로 Screens에 설치하면 Screens 서비스 공급자에서 플레이어를 등록할 수 있습니다.

아래 절차에 따라 플레이어를 등록하십시오.

1. Screens 서비스 공급자에 로그인합니다.

1. 왼쪽 탐색 패널에서 **Players 관리** 아래의 **등록 코드**&#x200B;로 이동하고 **코드 만들기**&#x200B;를 클릭합니다.

   >[!NOTE]
   >유효한/만료되지 않은 코드가 없는 경우 코드 만들기를 클릭하고 코드 이름을 입력하고 요구 사항에 따라 만료 설정을 선택합니다.

   ![이미지](/help/screens-cloud/assets/player/register-player1.png)

1. **등록 코드** 대화 상자에서 다음 필드를 채웁니다.

   ![이미지](/help/screens-cloud/assets/player/register-player2.png)

   1. **등록 코드 이름**:등록 코드의 이름
   1. **등록 코드 만료**:등록 코드의 만료 날짜
   1. **사용 제한**:등록 코드의 사용 제한을 해제하려면 버튼을 전환합니다. 기본적으로 사용량 제한 옵션은 꺼져 있습니다.
   1. **사용 제한**:사용 제한 번호를 선택합니다

1. **만들기**&#x200B;를 클릭하여 등록 코드를 만듭니다. 목록에 등록 코드가 있는 플레이어가 표시됩니다.

   ![이미지](/help/screens-cloud/assets/player/register-player3.png)

1. **REGISTRATION CODE** 열 아래의 값을 클릭하여 값을 클립보드에 복사합니다.

1. AEM Screens 플레이어의 관리자 UI에서 **플레이어 등록** 탭에 있는 **코드** 필드에 이 값을 붙여 넣고 **등록**&#x200B;을 클릭합니다.

   ![이미지](/help/screens-cloud/assets/player/register-player4.png)


1. 코드를 추가하면 플레이어가 플레이어의 관리 UI에서 등록된 것이 표시됩니다.

   ![이미지](/help/screens-cloud/assets/player/register-player5.png)

1. 이제 왼쪽 탐색 패널의 **Players**&#x200B;에 이 플레이어가 표시됩니다. Screens 서비스 공급자에 표시되는 코드는 플레이어 코드 아래의 관리 UI의 **시스템 정보** 패널과 일치합니다.

   ![이미지](/help/screens-cloud/assets/player/register-player6.png)

## 다음 기능 {#whats-next}

이제 플레이어를 클라우드 모드로 설치 및 구성했으므로, 다음에 Screens 서비스 공급자의 Cloud Service으로 [Screens의 디스플레이에 플레이어 할당 문서를 검토하여 Screens 여정으로 계속해야 합니다.](/help/screens-cloud/managing-players-registration/assigning-player-display.md)