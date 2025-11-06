---
title: IP 허용 목록 추가
description: Cloud Manager을 사용하여 나만의 IP 허용 목록을 추가하는 방법을 알아봅니다.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 7%

---


# IP 허용 목록 추가 {#add-ip-allow-list}

Cloud Manager을 사용하여 나만의 IP 허용 목록을 추가하는 방법을 알아봅니다.

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 추가할 수 있습니다.

{{add-cm-allowlist-frontend-pipeline}}
{{ip-allow-lists-ue}}

**IP 허용 목록 추가:**

1. [experience.adobe.com](https://experience.adobe.com/experiencemanager/)에서 Cloud Manager에 로그인합니다.

1. 왼쪽 메뉴에서 Cloud Manager을 클릭한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 왼쪽 메뉴를 사용하여(![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭해야 메뉴를 볼 수 있음) ![작업 목록 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP 허용 목록**&#x200B;을 클릭합니다.

   왼쪽 메뉴에 있는 ![IP 허용 목록 옵션](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. IP 허용 목록 페이지의 오른쪽 상단 모서리에서 **IP 허용 목록 추가**&#x200B;를 클릭합니다.

   ![IP 허용 목록 추가 대화 상자](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. **IP 허용 목록 추가** 대화 상자의 **IP 허용 목록 이름** 필드에 IP 허용 목록 참조에 사용할 이름을 입력합니다. 이 이름은 정보 제공용입니다. 목록을 식별하는 데 도움이 될 만큼 설명적인지 확인하십시오.

1. **IP 주소/CIDR** 필드에 최대 50개의 IP 주소 또는 CIDR 블록을 입력합니다. 다음 방법 중 하나로 추가할 수 있습니다.

   * 한 번에 하나씩: 주소를 입력한 다음 `Enter`을 누릅니다. 각 추가 주소에 대해 이 작업을 반복합니다.
   * 한 번에 여러 개 입력: 쉼표(,) 또는 탭으로 구분된 주소를 입력한 다음 각 주소를 개별적으로 인식하도록 `Enter`을(를) 누르십시오.

1. 마지막 IP 주소 또는 CIDR 블록 입력을 마치면 `Enter`을(를) 눌러 입력을 확인합니다. `Enter`을(를) 누르고 **저장** 단추가 활성화된 후에만 항목이 확인됩니다.

1. **저장**&#x200B;을 클릭합니다.

저장한 후 새로 만든 IP 허용 목록이 **IP 허용 목록** 페이지의 표에 행으로 나타납니다.

