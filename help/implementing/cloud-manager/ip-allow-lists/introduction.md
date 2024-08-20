---
title: IP 허용 목록 소개
description: IP 허용 목록이 사용자가 AEM as a Cloud Service의 도메인에 액세스할 수 있는 주소를 제한하는 방법에 대해 알아봅니다.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f4c6331491bb08e81964476ad58065c1ee022967
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 20%

---


# IP 허용 목록 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP 허용 목록 관리"
>abstract="AEM as a Cloud Service은 인터넷을 통해 액세스할 수 있으며 사용자 인증 및 권한 부여를 통해 보호됩니다. Cloud Manager의 IP 허용 목록을 사용하여 신뢰할 수 있는 IP 주소에 대한 액세스를 제한하고 제어할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 허용 목록을 만들 수 있습니다."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists" text="IP 허용 목록 추가"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists" text="IP 허용 목록 보기 및 업데이트"

AEM as a cloud service는 기본적으로 인터넷을 통해 액세스할 수 있습니다. 보안은 사용자 인증 및 권한 부여를 통해 처리되지만, IP 허용 목록에 추가 기능은 신뢰할 수 있는 IP 주소로만 액세스를 제한하는 방법입니다.

Cloud Manager의 IP 허용 목록을 사용하여 이러한 신뢰할 수 있는 IP 주소에 대한 액세스를 제한하고 제어할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 [IP 허용 목록을 만들기](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md)할 수 있습니다.

추가한 후 [IP 허용 목록을 환경의 작성자 서비스나 게시자 서비스 또는 둘 다에 단위나 엔터티로 여러 번 적용 또는 적용 취소](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)할 수 있습니다.

>[!NOTE]
>
>IP 허용 목록이 적용되지 않으면 기본적으로 모든 IP 주소가 허용됩니다. IP 허용 목록이 적용되면 IP 허용 목록의 주소 외에는 IP 주소가 허용되지 않습니다.

## 제한 사항 {#limitations}

IP 허용 목록에 몇 가지 제한 사항을 염두에 두어야 합니다.

* 프로그램에 최대 50개의 IP 허용 목록을 추가할 수 있습니다.
* 각 IP 허용 목록에 최대 50개의 IP/CIDR 주소를 추가할 수 있습니다.
* IP 허용 목록 이름은 환경의 작성자 서비스용 Cloud Manager 또는 게시 서비스나 둘 다에서 지원됩니다.
