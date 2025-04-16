---
title: IP 허용 목록 추가
description: Cloud Manager을 사용하여 나만의 IP 허용 목록을 추가하는 방법을 알아봅니다.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 328ae6d1866a7089fb291d4872d27dc5fa1d4caa
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 14%

---


# IP 허용 목록 추가 {#add-ip-allow-list}

Cloud Manager을 사용하여 나만의 IP 허용 목록을 추가하는 방법을 알아봅니다.

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 추가할 수 있습니다.

{{add-cm-allowlist-frontend-pipeline}}

**IP 허용 목록 추가:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 왼쪽 메뉴를 사용하여(![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭해야 메뉴를 볼 수 있음) ![작업 목록 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP 허용 목록**&#x200B;을 클릭합니다.

   왼쪽 메뉴에 있는 ![IP 허용 목록 옵션](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. IP 허용 목록 페이지의 오른쪽 상단 모서리에서 **IP 허용 목록 추가**&#x200B;를 클릭합니다.

   ![IP 허용 목록 추가 대화 상자](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. **IP 허용 목록 추가** 대화 상자의 **IP 허용 목록 이름** 필드에 IP 허용 목록 참조에 사용할 이름을 입력합니다. 이 이름은 정보 제공용입니다. 목록을 식별하는 데 도움이 될 만큼 설명적인지 확인하십시오.

1. **IP 주소/CIDR** 필드에 IP 또는 IP CIDR 블록을 입력하십시오. 여러 블록은 쉼표나 탭으로 구분하십시오.

1. **저장**&#x200B;을 클릭합니다.

저장한 후 새로 만든 IP 허용 목록이 **IP 허용 목록** 페이지의 표에 행으로 나타납니다.

