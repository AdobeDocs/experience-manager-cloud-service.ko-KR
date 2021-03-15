---
title: SSL 인증서 상태 확인 - SSL 인증서 관리
description: SSL 인증서 상태 확인 - SSL 인증서 관리
translation-type: tm+mt
source-git-commit: ddee11fdfa8cadfcd63472fd3c94cd8af555c856
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---


# SSL 인증서 상태 확인 중 {#checking-status-an-ssl-certificate}

SSL 인증서 페이지의 SSL 인증서 상태를 한 눈에 파악할 수 있습니다.

다음 색상 구성표에서 SSL 인증서의 상태를 식별할 수 있습니다.

* **녹색**
인증서가 향후 60일 동안 유효함을 나타냅니다.

* **주황색**
인증서가 60일 이내에 만료됨을 나타냅니다. 사이트 액세스나 정전이 발생하지 않도록 Cloud Manager UI를 통해 인증서를 갱신하고 대체할 계획이 있는지 확인해야 합니다. Cloud Manager는 UI에 정기적인 알림을 전송하여 인증서 만료 예정임을 알립니다.

* **빨간색**
여러 알림을 받았더라도 SSL 인증서가 만료되었음을 나타냅니다.

## IP 허용 목록 {#pre-existing-cdn}에 대한 기존 CDN 구성

IP 허용 목록, SSL 인증서 또는 사용자 정의 도메인 이름에 대한 기존 CDN 구성을 포함하는 환경을 보유한 고객은 **IP 허용 목록** 및 **환경** 세부 정보 페이지에 다음 메시지를 보게 됩니다.

![](/help/implementing/cloud-manager/assets/ip-allow-list-1.png)

>[!NOTE]
>기존 구성을 보고 관리하려면 아래 그림과 같이 UI를 통해 해당 구성을 추가해야 합니다.

![](/help/implementing/cloud-manager/assets/ip-allow-list-2.png)