---
title: 소개 - Cloud Manager의 IP 허용 목록
description: 소개 - Cloud Manager의 IP 허용 목록
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 1875920ae5180074dcad98fb5c10242b6baa76c7
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 3%

---

# 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP 허용 목록 관리"
>abstract="AEM as a cloud service는 인터넷에 연결되며 보안은 사용자 인증 및 승인을 통해 처리됩니다. IP 허용 목록은 신뢰할 수 있는 사용자에게만 대한 액세스를 제한하고 제어하는 데 사용되는 Cloud Manager의 기능입니다. 이 기능을 사용하면 권한이 있는 사용자가 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 허용 목록을 만들 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="IP 허용 목록 추가"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html" text="IP 허용 목록 보기 및 업데이트"

AEM as a cloud service는 인터넷에 연결되며 보안은 사용자 인증 및 승인을 통해 처리됩니다. IP 허용 목록은 신뢰할 수 있는 사용자에게만 대한 액세스를 제한하고 제어하는 데 사용되는 Cloud Manager의 기능입니다. 이 기능을 사용하면 권한이 있는 사용자가 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 허용 목록을 만들 수 있습니다.

>[!NOTE]
>프로그램에 최대 50개의 IP 허용 목록을 추가할 수 있으며 각 IP 허용 목록에 최대 50개의 IP/CIDR 주소를 추가할 수 있습니다.

IP 허용 목록은 한 번 추가하고 환경의 작성자 및/또는 게시자 서비스에 단위 또는 엔티티로 여러 번 적용/적용할 수 있습니다.

>[!NOTE]
>IP 허용 목록 이름은 환경의 작성자 및/또는 게시 서비스용 Cloud Manager에서 지원됩니다.

권한이 있는 사용자는 Cloud Manager UI IP 허용 목록 페이지나 환경 세부 정보 페이지를 사용하여 다음을 포함하여 환경에 대한 IP 허용 목록을 관리하기 위해 여러 작업을 수행할 수 있습니다.

* [IP 허용 목록 추가](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md)
   >[!NOTE]
   > 한 번 추가하고 프로그램의 환경 서비스에서 여러 번 규칙을 다시 사용하거나 적용할 수 있습니다.
* [IP 허용 목록 보기 또는 업데이트](/help/implementing/cloud-manager/ip-allow-lists/view-update-ip-allow-list.md)
* [IP 허용 목록 적용 또는 적용 취소](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)
* [IP 허용 목록 삭제](/help/implementing/cloud-manager/ip-allow-lists/delete-ip-allow-list.md)
