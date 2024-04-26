---
title: IP 허용 목록 추가
description: Cloud Manager를 사용하여 고유한 IP 허용 목록을 추가하는 방법을 알아봅니다.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: fa6d0670a011276facc561f62f52c6e69147a49e
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 87%

---


# IP 허용 목록 추가 {#add-ip-allow-list}

Cloud Manager를 사용하여 고유한 IP 허용 목록을 추가하는 방법을 알아봅니다.

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 추가할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 다음에서 **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔을 누르고 프로그램을 선택합니다.

1. 다음에서 **개요** 페이지, 다음으로 이동 **IP 허용 목록** 측면 탐색 탭을 사용하여 페이지를 표시합니다.

   ![사이드 패널의 IP 허용 목록 옵션](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. **IP 허용 목록**&#x200B;을 추가합니다.

   ![IP 허용 목록 추가 대화 상자](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. **IP 허용 목록 추가** 대화 상자에서 **IP 허용 목록 이름** 필드에 허용 목록을 참조하는 데 사용할 이름을 입력합니다.

   * 이 이름은 정보 제공용으로만 제공되며 목록을 식별하는 데 도움이 되는 설명을 제공해야 합니다.

1. **IP 주소/CIDR** 필드에 IP 또는 IP CIDR 블록을 입력합니다.

   * 여러 블록은 쉼표나 탭으로 구분할 수 있습니다.

1. **저장**&#x200B;을 클릭합니다.

저장하면 새로 만든 IP 허용 목록이 **IP 허용 목록** 페이지의 표에 행으로 표시됩니다.
