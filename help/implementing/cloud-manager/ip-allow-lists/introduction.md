---
title: IP 허용 목록 소개
description: AEM as a Cloud Service 도메인에 액세스할 수 있는 주소에서 IP 허용 목록을 제한하는 방법을 알아봅니다.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 8d1680fa8dbaaefa297cf8c6698097b3c7acc48d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# IP 허용 목록 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP 허용 목록 관리"
>abstract="AEM as a cloud service는 인터넷을 통해 액세스할 수 있으며 사용자 인증 및 인증을 통해 보안됩니다. Cloud Manager의 IP 허용 목록을 사용하여 신뢰할 수 있는 IP 주소에만 대한 액세스를 제한하고 제어할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트의 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 허용 목록을 만들 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="IP 허용 목록 추가"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html" text="IP 허용 목록 보기 및 업데이트"

AEM as a cloud service는 인터넷을 통해 액세스할 수 있으며 사용자 인증 및 인증을 통해 보안됩니다. Cloud Manager의 IP 허용 목록을 사용하여 신뢰할 수 있는 IP 주소에만 대한 액세스를 제한하고 제어할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트의 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 허용 목록을 만들 수 있습니다.

IP 허용 목록은 한 번 추가하고 환경의 작성자 및/또는 게시자 서비스에 단위 또는 엔티티로 여러 번 적용/적용 취소할 수 있습니다.

## 제한 사항 {#limitations}

IP에는 목록을 기억하도록 허용하는 많은 제한 사항이 있습니다.

* 프로그램에 최대 50개의 IP 허용 목록을 추가할 수 있습니다
* 각 IP 허용 목록에 최대 50개의 IP/CIDR 주소를 추가할 수 있습니다.
* IP 허용 목록 이름은 Cloud Manager에서 환경의 작성자 및/또는 게시 서비스에 대해 지원됩니다.
