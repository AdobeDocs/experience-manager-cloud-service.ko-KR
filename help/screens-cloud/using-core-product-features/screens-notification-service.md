---
title: Screens as a Cloud Service의 Screens 알림 서비스
description: 이 페이지에서는 Screens as a Cloud Service으로 알림 서비스를 구성하는 방법에 대해 설명합니다.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
source-git-commit: 69798b1ac3758d37c4e2f480ccc23bae24d6a814
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---

# Screens 알림 서비스 {#notification-service}

## 소개 {#introduction}

### 개요

AEM Screens 알림 서비스를 사용하면 관리자가 이메일에 구성 가능한 기간 동안 ping을 수행하지 않은 모든 AEM Screens 플레이어 목록이 포함된 보고서를 받을 수 있습니다.

### 구성하는 방법

AEM Screens Cloud에서 고객은 다음 정보가 포함된 지원 티켓을 생성하여 장치 비활성 상태에 대한 보고서를 요청할 수 있습니다.

* 고객 이름
* IMS 조직 ID
* 일정 빈도: 이 모니터에서 이메일을 보내야 하는 시간 또는 빈도(예: 1)를 지정합니다.
* Ping Timeout: 디바이스에 연결할 수 없는 것으로 간주되는 간격(분)을 지정합니다.
* 이메일 ID : 보고서를 전송할 이메일 ID

>[!NOTE]
>이메일은 이메일 생성 시 주어진 핑 시간 초과 동안 핑하지 않은 장치가 있을 경우에만 플레이어가 보고됩니다.

### 예제 사용 사례

보고서 시간을 오전 5시로 설정하고 핑 시간 제한을 1시간으로 설정한 경우 Screens 장치가 오전 4시에서 오전 5시 사이에 ping을 수행하지 않으면 장치 비활성화를 확인하는 이메일 알림을 받게 됩니다.
