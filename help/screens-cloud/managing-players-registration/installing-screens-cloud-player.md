---
title: Screens에서 Cloud Service으로 플레이어 설치 및 구성
description: 이 페이지에서는 Screens에서 Cloud Service으로 플레이어를 설치하고 구성하는 방법을 설명합니다.
source-git-commit: d5970e27773433c9e6e7175a103768ae591e87ba
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 1%

---


# Screens에서 Cloud Service으로 플레이어 설치 및 구성 {#installing-players-screens-cloud}

이 섹션에서는 온-프레미스 AEM 인스턴스에 등록된 AEM Screens 플레이어를 설치하는 방법을 설명합니다. 또한 기존 플레이어의 공장 재설정을 수행한 다음, 새 플레이어를 AEM Screens에 Cloud Service으로 등록해야 합니다.

## 목표 {#objective}

이 문서는 플레이어를 등록하기 전에 플레이어를 설정하는 방법을 이해하는 데 도움이 됩니다. 읽기 후에는 다음을 이해할 수 있습니다.

* 플레이어를 설치할 위치
* 플레이어를 클라우드 모드로 업데이트하는 방법

## 플레이어를 클라우드 모드로 설정하는 절차 {#cloud-mode-setup}

[AEM Screens Player 다운로드](https://download.macromedia.com/screens/)에서 최신 플레이어를 다운로드하면 이제 플레이어를 클라우드 모드로 업데이트할 준비가 되었습니다.

아래 단계에 따라 플레이어를 업데이트하십시오.

1. AEM Screens 플레이어를 엽니다.

   >[!NOTE]
   >전용 하드웨어 장치 또는 자체 플레이어에서 웹 확장을 사용하여 테스트할 수 있습니다.

1. **구성** 탭을 클릭하고 **재설정** 옵션 아래에 있는 **출하 시** 단추를 클릭합니다.

   ![이미지](/help/screens-cloud/assets/player/installplayer-2.png)

1. **Confirm**&#x200B;을 클릭하여 플레이어를 재설정합니다.

1. **구성** 탭에서 **실행 모드 전환** 옵션 아래의 **클라우드 모드로 변경** 단추를 다시 클릭합니다.

   ![이미지](/help/screens-cloud/assets/player/installplayer-1.png)

1. 클라우드 모드로 전환할 때 나타나는 **Confirm**&#x200B;을 클릭하면 플레이어 등록이 취소됩니다.

## 기본 재생 모니터링 {#playback-monitoring}

플레이어는 기본값인 각 `ping`이 30초로 설정된 다양한 재생 지표를 보고합니다. 이 지표를 기반으로 중단 경험, 빈 화면 및 예약 문제와 같은 다양한 에지 사례를 감지할 수 있습니다. 이렇게 하면 장치의 문제를 이해하고 해결할 수 있으므로 조사 및 해결 조치를 빠르게 수행할 수 있습니다.

AEM Screens 플레이어의 기본 재생 모니터링을 사용하여 다음을 수행할 수 있습니다.

* 플레이어가 컨텐츠를 제대로 재생하는 경우 원격으로 모니터링합니다.

* 필드의 빈 화면 또는 끊어진 경험에 대한 반응성을 개선합니다.

* 최종 사용자에게 손상된 경험을 표시할 위험을 줄입니다.

### 속성 이해 {#understand-properties}

다음 속성은 각 `ping`에 포함됩니다.

| 속성 | 설명 |
|---|---|
| id {string} | 플레이어 식별자 |
| activeChannel {string} | 현재 재생 중인 채널 경로이거나 예약된 항목이 없으면 null입니다. |
| activeElements {string} | 쉼표로 구분된 문자열, 현재 표시된 모든 재생 시퀀스 채널에 요소(다중 영역 레이아웃의 경우 다중) |
| isDefaultContent {boolean} | 재생 채널이 기본 또는 폴백 채널로 간주되는 경우 true(즉, 우선 순위 1이 있고 예약이 없는 경우) |
| hasContentChanged {boolean} | 지난 5분 동안 내용이 변경된 경우 true이고, 그렇지 않으면 false입니다 |
| lastContentChange {string} | 마지막 콘텐츠 변경 타임스탬프 |

>[!NOTE]
>선택적으로 플레이어 환경 설정(재생 모니터링 활성화)에서 더 많은 고급 속성을 활성화할 수 있으며, 이러한 속성은 다음과 같습니다.
>|속성|설명|
>|—|—|
>|isContentRendering {boolean}|GPU에서 실제 컨텐츠 재생(픽셀 분석 기반)을 확인할 수 있는 경우 true|

### 제한 사항 {#limitations}

다음은 기본 재생 모니터링에 대한 몇 가지 제한 사항입니다.

* 플레이어는 자체 재생 상태를 서버에 보고하므로 활성 연결이 필요합니다.

* GPU를 확인하는 `isContentRendering` 속성은 기본적으로 활성화되도록 현재 리소스 사용량이 많으며 플레이어 환경 설정에서 명시적 옵트인이 필요합니다. 비디오와 함께 사용하지 않는 것이 좋습니다.

* 이 기능은 시퀀스 채널에 대해 지원됩니다.

## 다음은 무엇입니까? {#whats-next}

이제 플레이어를 클라우드 모드로 설치 및 구성했으므로, 다음에 Screens 서비스 제공자에서 [Screens의 플레이어를 Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md)로 등록하여 Cloud Service 여정으로 계속해야 합니다.
