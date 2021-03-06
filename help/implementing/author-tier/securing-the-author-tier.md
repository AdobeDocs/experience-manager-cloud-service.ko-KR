---
title: 작성자 계층 보호
description: 작성자 계층 보호
exl-id: f5be90a4-266a-4d23-8e8b-94156f0264d5
source-git-commit: b2b319cf06bbad07add092059d3f093ce7336d4e
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 66%

---

# 작성자 계층 보호 {#securing-the-author-tier}

AEM as a Cloud Service로 사용하여 새 환경을 만들 때 기본적으로 결과 작성자 계층은 인터넷에서 액세스할 수 있습니다. 작성자 계층에 대한 액세스를 보호하기 위해 네트워크 정책을 추가로 구성할 수 있습니다. 자세한 내용은 [IP 허용 목록 적용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/apply-allow-list.html?lang=en) 자세한 내용 이 절차는 작성자 환경에 대한 네트워크 액세스 권한을 부여해야 하는 IP 범위 인증을 기반으로 합니다.

이러한 규칙을 적용하려면 [Adobe Admin Console](https://adminconsole.adobe.com/) 요청된 정보를 사용하여 다음을 수행하십시오.

* 프로그램 ID
* 환경 ID
* 인증할 IP 주소 범위

