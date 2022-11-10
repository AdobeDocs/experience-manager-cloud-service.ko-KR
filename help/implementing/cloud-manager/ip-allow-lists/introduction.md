---
title: IP 허용 목록 소개
description: IP 허용 목록을 통해 사용자가 AEM as a Cloud Service 도메인에 액세스할 수 있는 주소를 제한하는 방법에 대해 알아봅니다.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 18ecf3394ff575213756fced84a3b08795188240
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 56%

---


# IP 허용 목록 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP 허용 목록 관리"
>abstract="AEM as a Cloud Service는 인터넷을 통해 액세스할 수 있으며 사용자 인증 및 권한 부여를 통해 보호됩니다. Cloud Manager의 IP 허용 목록은 신뢰할 수 있는 IP 주소에 대한 액세스를 제한하고 제어하는 데만 사용할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 허용 목록을 만들 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="IP 허용 목록 추가"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html" text="IP 허용 목록 보기 및 업데이트"

AEM as a cloud service는 기본적으로 인터넷을 통해 액세스할 수 있습니다. 사용자 인증 및 권한 부여를 통해 보안을 처리하는 동안 IP 허용 목록은 신뢰할 수 있는 IP 주소에만 대한 액세스를 제한하는 방법입니다.

Cloud Manager의 IP 허용 목록을 사용하여 그러한 신뢰할 수 있는 IP 주소에만 대한 액세스를 제한하고 제어할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 [허용 목록 만들기](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) 신뢰할 수 있는 IP 주소 중에서 사이트 사용자가 자신의 AEM 도메인에 액세스할 수 있습니다.

추가되면, [IP 허용 목록을 적용/적용할 수 없음](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) 환경의 작성자 및/또는 게시자 서비스에 단위 또는 엔티티로서 여러 번.

>[!NOTE]
>
>IP 허용 목록이 적용되지 않으면 기본적으로 모든 IP 주소가 허용됩니다. IP 허용 목록이 적용되는 즉시 IP 허용 목록에 있는 주소 이외의 IP 주소는 허용되지 않습니다.

## 제한 사항 {#limitations}

IP 허용 목록에는 여러 가지 제한 사항이 있습니다.

* 프로그램에 최대 50개의 IP 허용 목록을 추가할 수 있습니다.
* 각 IP 허용 목록에 최대 50개의 IP/CIDR 주소를 추가할 수 있습니다.
* IP 허용 목록 이름은 Cloud Manager에서 환경의 작성자 및/또는 게시 서비스를 위해 지원됩니다.
