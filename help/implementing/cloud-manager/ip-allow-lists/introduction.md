---
title: IP 허용 목록 소개
description: IP 허용 목록을 통해 사용자가 AEM as a Cloud Service의 도메인에 액세스할 수 있는 주소를 제한하는 방법에 대해 알아봅니다.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 100%

---


# IP 허용 목록 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP 허용 목록 관리"
>abstract="AEM as a Cloud Service는 인터넷을 통해 액세스할 수 있으며 사용자 인증 및 권한 부여를 통해 보호됩니다. Cloud Manager의 IP 허용 목록은 신뢰할 수 있는 IP 주소에 대한 액세스를 제한하고 제어하는 데만 사용할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 허용 목록을 만들 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="IP 허용 목록 추가"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists.html" text="IP 허용 목록 보기 및 업데이트"

기본적으로 AEM as a Cloud Service는 인터넷을 통해 액세스할 수 있습니다. 보안은 사용자 인증 및 권한 부여를 통해 처리되지만, IP 허용 목록에 추가 기능은 신뢰할 수 있는 IP 주소로만 액세스를 제한하는 방법입니다.

Cloud Manager의 IP 허용 목록은 신뢰할 수 있는 IP 주소에 대한 액세스를 제한하고 제어하는 데에만 사용할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 [허용 목록을 만들 수 있습니다](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).

IP 허용 목록은 추가한 후에 환경의 작성자 및/또는 게시자 서비스에 하나의 단위 또는 엔티티로 여러 번 [적용/적용 해제](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)할 수 있습니다.

>[!NOTE]
>
>IP 허용 목록이 적용되지 않으면 기본적으로 모든 IP 주소가 허용됩니다. IP 허용 목록이 적용되면 IP 허용 목록에 있는 주소를 제외하고 IP 주소가 허용되지 않습니다.

## 제한 사항 {#limitations}

IP 허용 목록에는 여러 제한 사항이 있습니다.

* 프로그램에 최대 50개의 IP 허용 목록을 추가할 수 있습니다.
* 각 IP 허용 목록에 최대 50개의 IP/CIDR 주소를 추가할 수 있습니다.
* IP 허용 목록 이름은 Cloud Manager에서 환경의 작성자나 게시 서비스 또는 둘 다를 위해 지원됩니다.
