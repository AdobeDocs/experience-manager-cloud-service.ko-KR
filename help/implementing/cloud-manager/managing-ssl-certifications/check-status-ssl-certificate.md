---
title: SSL 인증서 상태 확인 - SSL 인증서 관리
description: SSL 인증서 상태 확인 - SSL 인증서 관리
exl-id: 59d81356-2fa9-43db-bfa5-c2896c530eaa
source-git-commit: 828490e12d99bc8f4aefa0b41a886f86fee920b4
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# SSL 인증서 상태 확인 {#checking-status-an-ssl-certificate}

SSL 인증서 상태는 SSL 인증서 페이지에서 한 눈에 알 수 있습니다.

다음 색상 구성표에서 SSL 인증서 상태를 식별할 수 있습니다.

* **녹색**
인증서가 향후 60일 이상 유효함을 나타냅니다.

* **주황**
인증서가 60일 이내에 만료됨을 나타냅니다. 가능한 사이트 액세스 또는 정전을 방지하기 위해 인증서를 갱신하고 Cloud Manager UI를 통해 교체할 계획이 있는지 확인해야 합니다. Cloud Manager는 UI에서 정기적인 알림을 전송하여 임박한 인증서 만료를 알려줍니다.

* **빨간색**
여러 개의 알림에도 불구하고 SSL 인증서가 만료되었음을 나타냅니다.

## 기존 CDN 구성 {#pre-existing-cdn}

IP 허용 목록, SSL 인증서 또는 사용자 지정 도메인 이름에 대한 기존 CDN 구성을 포함하는 환경을 사용하는 고객은 **IP 허용 목록** 그리고 **환경** 세부 사항 페이지. 고객이 UI를 통해 기존 환경 구성을 모두 마이그레이션한 후 UI에 표시되는 메시지는 사라지며, 메시지가 사라지려면 영업일 기준으로 1~2일이 걸릴 수 있습니다.

>[!NOTE]
>기존 구성을 보고 관리하려면 UI를 통해 구성을 추가해야 합니다. 을(를) 참조하십시오. [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) 자세한 내용

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
