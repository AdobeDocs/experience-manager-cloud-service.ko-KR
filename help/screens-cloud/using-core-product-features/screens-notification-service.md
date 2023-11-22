---
title: Screens as a Cloud Service의 Screens 알림 서비스
description: 이 페이지에서는 Screens as a Cloud Service으로 알림 서비스를 구성하는 방법에 대해 설명합니다.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
source-git-commit: 237b4a8e01af74dbaac0ba1715b5fa95c931be7c
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 6%

---

# Screens 알림 서비스 {#notification-service}

## 소개 {#introduction}

### 개요

AEM Screens 알림 서비스를 사용하면 AEM screens 플레이어가 구성 가능한 기간 동안 ping을 수행하지 않는 경우 관리자가 이메일을 받을 수 있습니다.

### 구성하는 방법

AEM Screens Cloud에서 고객은 다음 정보로 지원 티켓을 생성하여 장치 비활성 상태에 대한 경고를 요청할 수 있습니다.

* 고객 이름
* IMS 조직 ID
* 일정 빈도: 이 모니터에서 이메일을 보내야 하는 시간 또는 빈도(예: 1)를 지정합니다.
* Ping Timeout: 디바이스에 연결할 수 없는 것으로 간주되는 간격(분)을 지정합니다.
* 이메일 ID : 보고서를 전송할 이메일 ID
