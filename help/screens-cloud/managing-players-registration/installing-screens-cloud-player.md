---
title: Screens에서 플레이어 설치 및 구성 as a Cloud Service
description: 이 페이지에서는 Screens에서 as a Cloud Service으로 플레이어를 설치하고 구성하는 방법에 대해 설명합니다.
exl-id: a022738a-c543-4629-a244-f70fa294fe7f
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 1%

---

# Screens에서 플레이어 설치 및 구성 as a Cloud Service {#installing-players-screens-cloud}

이 섹션에서는 온-프레미스 AEM 인스턴스에 등록된 AEM Screens 플레이어를 설치하는 방법을 설명합니다. 또한 기존 플레이어를 출하 시 재설정한 다음 AEM Screens에 새 플레이어를 as a Cloud Service으로 등록해야 합니다.

## 목표 {#objective}

이 문서는 플레이어를 등록하기 전에 플레이어를 설정하는 방법을 이해하는 데 도움이 됩니다. 읽고 나면 다음을 이해할 수 있어야 합니다.

* 플레이어 설치 위치
* 플레이어를 클라우드 모드로 업데이트하는 방법

## 플레이어를 클라우드 모드로 설정하는 단계 {#cloud-mode-setup}

에서 최신 플레이어를 다운로드한 후 [AEM Screens 플레이어 다운로드](https://download.macromedia.com/screens/), 이제 플레이어를 클라우드 모드로 업데이트할 준비가 되었습니다.

플레이어를 업데이트하려면 아래 단계를 따르십시오.

1. AEM Screens 플레이어를 엽니다.

   >[!NOTE]
   >전용 하드웨어 장치로 테스트하거나 자체 플레이어에서 웹 확장을 사용하도록 선택할 수 있습니다.

1. 다음을 클릭합니다. **구성** tab 키를 누른 다음 클릭 **팩터리로** 아래에 있는 단추 **재설정** 옵션을 선택합니다.

   ![이미지](/help/screens-cloud/assets/player/installplayer-2.png)

1. 클릭 **확인** 플레이어를 재설정합니다.

1. 다음에서 다시 **구성** tab 키를 누른 다음 클릭 **클라우드 모드로 변경** 아래에 있는 단추 **실행 모드 전환** 옵션을 선택합니다.

   ![이미지](/help/screens-cloud/assets/player/installplayer-1.png)

1. 클릭 **확인** 클라우드 모드로 전환할 때 플레이어의 등록을 취소할지 묻는 메시지가 표시됩니다.

## 기본 재생 모니터링 {#playback-monitoring}

플레이어는 각 재생 지표에서 다양한 재생 지표를 보고합니다 `ping` 기본값은 30초입니다. 이러한 지표를 기반으로 Adobe은 중단 경험, 빈 화면 및 예약 문제와 같은 다양한 에지 사례를 감지할 수 있습니다. 이 검색을 통해 디바이스의 문제를 이해하고 해결할 수 있으므로 조사 및 수정 조치를 신속하게 진행할 수 있습니다.

AEM Screens 플레이어에서 기본 재생 모니터링을 사용하면 다음을 수행할 수 있습니다.

* 플레이어가 컨텐츠를 제대로 재생하고 있는지 원격으로 모니터링합니다.

* 현장에서의 빈 화면 또는 깨진 경험에 대한 반응성을 개선합니다.

* 최종 사용자에게 손상된 경험이 표시될 위험을 줄입니다.

### 속성 이해 {#understand-properties}

각 속성에는 다음 속성이 포함됩니다 `ping`:

| 속성 | 설명 |
|---|---|
| id {string} | 플레이어 식별자 |
| activeChannel {string} | 현재 재생 중인 채널 경로 또는 일정이 없는 경우 null |
| 활성 요소 {string} | 재생 중인 모든 시퀀스 채널에 현재 표시되는 쉼표로 구분된 문자열(다중 영역 레이아웃이 있는 경우 다중) |
| isDefaultContent {boolean} | 재생 채널이 기본 또는 대체 채널로 간주되는 경우(즉, 우선 순위 1이 있고 일정이 없는 경우) true |
| hasContentChanged {boolean} | 지난 5분 동안 콘텐츠가 변경되면 true이고, 그렇지 않으면 false입니다. |
| lastContentChange {string} | 마지막 콘텐츠 변경 타임스탬프 |

>[!NOTE]
>선택적으로, 플레이어 환경 설정에서 고급 속성을 활성화할 수 있습니다(재생 모니터링 활성화).
>|속성|설명|
>|—|—|
>|isContentRendering {boolean}|true - GPU가 실제 콘텐츠를 재생하고 있는지 확인할 수 있는 경우(픽셀 분석 기반)|

### 제한 사항 {#limitations}

기본 재생 모니터링에 대한 몇 가지 제한 사항이 아래에 나와 있습니다.

* 플레이어는 자체 재생 상태를 서버에 보고하므로 활성 연결이 필요합니다.

* 다음 `isContentRendering` gpu를 확인하는 속성은 기본적으로 사용하도록 설정하기에 너무 많은 리소스를 사용하며 플레이어 환경 설정에서 명시적인 옵트인이 필요합니다. 프로덕션 환경에서는 비디오와 함께 사용하지 않는 것이 좋습니다.

* 이 기능은 시퀀스 채널에만 지원되며 대화형 채널(SPA) 사용 사례는 아직 다루지 않습니다.

* 이 지표는 아직 고객에게 완전히 노출되지 않았습니다. Adobe이 곧 대시보드와 유사한 보고 및 경고 메커니즘을 활성화하는 작업을 진행하고 있습니다.

## 다음 단계 {#whats-next}

이제 플레이어를 클라우드 모드로 설치 및 구성했으므로 Screens as a Cloud Service 여정을 계속하십시오. 문서 검토 [화면에서 플레이어 등록 as a Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) Screens Services 공급자에서 가져왔습니다.
