---
title: IP 허용 목록 관리
description: Cloud Manager에서 IP 허용 목록을 보고, 편집하고, 삭제하고, 상태를 확인하는 방법을 알아봅니다.
exl-id: 6efabe53-3f45-47d4-ac1f-979cae0ab33e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 19%

---

# IP 허용 목록 관리 {#manage-ip-allow-lists}

Cloud Manager에서 IP 허용 목록을 보고, 편집하고, 삭제하고, 상태를 확인하는 방법을 알아봅니다.

## IP 허용 목록 보기 및 업데이트 {#update-ip-allow-lists}

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 보고 업데이트할 수 있습니다.

**IP 허용 목록을 보고 업데이트하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그온한 다음 적절한 조직과 프로그램을 선택합니다.
1. **개요** 페이지의 왼쪽 메뉴에서 **서비스** 아래의 ![작업 목록 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP 허용 목록**&#x200B;을 클릭합니다.
1. 보거나 업데이트할 IP 허용 목록의 행을 식별합니다.
1. 행의 오른쪽 끝에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
1. 드롭다운 메뉴에서 **보기 및 업데이트**를 클릭합니다.
**IP 허용 목록 보기 및 업데이트** 대화 상자에는 규칙이 적용되는 환경 및 서비스와 함께 규칙을 정의하는 이름, IP 주소(또는 범위)가 표시됩니다.
1. 원하는 대로 이름 또는 IP 주소를 변경합니다.

   IP 허용 목록에 새 IP 범위를 추가하거나 제거하면 이전에 적용된 모든 해당 환경/서비스에 자동으로 적용/적용 취소됩니다.

   이전 업데이트가 진행 중이고 완료되지 않은 동안에는 IP 허용 목록을 업데이트할 수 없습니다.

1. **업데이트**&#x200B;를 클릭합니다.

## IP 허용 목록 상태 확인 {#check-allow-list-status}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그온한 다음 적절한 조직과 프로그램을 선택합니다.

1. **개요** 페이지의 왼쪽 메뉴에서 **서비스** 아래의 ![작업 목록 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP 허용 목록**&#x200B;을 클릭합니다.

1. IP 허용 목록 테이블의 **상태** 열에서 사용 중인 녹색 IP 허용 목록 위에 마우스 포인터를 두면 적용된 하나 이상의 서비스를 볼 수 있습니다.

   표에 표시된 상태 값은 다음과 같은 의미를 갖습니다.

   | IP 허용 목록 상태 | 설명 |
   | --- | --- |
   | 적용 여부 | IP 허용 목록이 하나 이상의 환경에 성공적으로 적용되었습니다. |
   | 업데이트 중 | IP 허용 목록에 대한 업데이트가 진행 중이며 목록에서 하나 이상의 적용 또는 적용 취소가 포함될 수 있습니다. 각 적용/적용 취소는 **시작되지 않음**, **진행 중**, **완료** 또는 **실패**&#x200B;라는 자체 상태와 함께 나열됩니다. |
   | 실패 | 하나 이상의 업데이트 적용 또는 적용 취소 프로세스가 실패했습니다.<br>· 각 응용 프로그램 및 응용 프로그램이 상태와 함께 나열됩니다.<br>· 업데이트에서 하나의 적용/적용 취소가 실패하면 상태는 **실패**&#x200B;입니다. 모든 실패가 지워질 때까지 상태는 **실패**&#x200B;로 유지됩니다.<br>· 오류를 지울 수 있도록 상태 옆에 있는 **다시 시도** 아이콘을 클릭합니다.<br>· **실패** 상태의 IP 허용 목록을 업데이트하거나 삭제할 수 없습니다. |
   | 삭제 중 | IP 허용 목록 삭제가 진행 중입니다.<br>· 삭제에는 모든 서비스에서 목록 적용 취소가 포함됩니다.<br>· 각 응용 프로그램이 **시작되지 않음**, **진행 중**, **완료** 또는 **실패**&#x200B;라는 자체 상태와 함께 나열됩니다.<br>· 삭제 작업이 완료되면 IP 허용 목록이 IP 허용 목록 테이블에 나타나지 않습니다. 또한 IP 허용 목록은 Cloud Manager의 프로그램에 있는 서비스에도 적용되지 않습니다. |
   | 삭제 실패 | 삭제 작업 중 하나 이상의 적용 취소가 실패했습니다.<br>· 각 적용 취소는 **완료** 또는 **실패** 상태와 함께 나열됩니다.<br>· 하나의 적용 취소에 실패하면 상태는 **삭제 실패**&#x200B;가 됩니다. 모든 실패가 지워질 때까지 상태는 **삭제 실패**(으)로 유지됩니다. 테이블 행의 맨 오른쪽에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 드롭다운 메뉴에서 **삭제**&#x200B;를 클릭하여 오류를 지웁니다.<br>· 상태가 **실패**&#x200B;인 동안에는 IP 허용 목록을 업데이트할 수 없습니다. |

## IP 허용 목록 삭제 {#delete-allow-list}

IP 허용 목록을 삭제하면 모든 서비스에서 목록이 자동으로 적용 취소되고 IP 허용 목록 테이블에서 삭제됩니다.

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 보고 업데이트할 수 있습니다.

**IP 허용 목록을 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그온한 다음 적절한 조직과 프로그램을 선택합니다.
1. **개요** 페이지의 왼쪽 메뉴에서 **서비스** 아래의 ![작업 목록 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP 허용 목록**&#x200B;을 클릭합니다.
1. 삭제할 IP 허용 목록의 행을 식별한 다음 행 오른쪽 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하고 **삭제**&#x200B;를 클릭합니다.
1. **IP 허용 목록 삭제** 대화 상자에서 **삭제**&#x200B;를 클릭합니다.

## 기존 CDN 구성 {#pre-existing-cdn}

IP 허용 목록에 대한 기존 CDN(Content Delivery Network) 구성이 있는 경우 **IP 허용 목록** 페이지에 정보 메시지가 있습니다. 이 메시지는 Cloud Manager에서 보고 구성할 수 있도록 사용자 인터페이스를 통해 이러한 구성을 추가하도록 권장합니다.

UI를 사용하여 모든 기존 환경 구성이 마이그레이션되면 메시지가 사라집니다. 메시지가 사라지는 데는 영업일 기준 1~2일이 소요될 수 있습니다.

자세한 내용은 [IP 허용 목록 추가](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md)를 참조하십시오.

SSL 인증서 또는 사용자 정의 도메인 이름에 대한 기존 CDN 구성이 있는 환경의 **SSL 인증서** 및 **환경** 페이지에도 유사한 메시지가 제공됩니다.
