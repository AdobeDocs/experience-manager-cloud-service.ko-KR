---
title: IP 허용 목록 적용 및 적용 취소
description: Cloud Manager 환경에 IP 허용 목록을 적용 및 적용 취소하는 방법을 알아봅니다.
exl-id: 7158496c-b0c4-4228-a306-71dc51003c57
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 18%

---


# IP 허용 목록 적용 및 적용 취소 {#apply-allow-list}

IP 허용 목록을 적용할 때 목록의 정의에 포함된 모든 IP 범위는 환경 내의 작성자 또는 게시 서비스와 연결됩니다. 목록 적용을 취소하는 것은 이 프로세스의 반대입니다.

{{add-cm-allowlist-frontend-pipeline}}

## IP 허용 목록 적용 {#applying}

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 적용할 수 있습니다.

**IP 허용 목록을 적용하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인합니다.
1. 적절한 조직을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 화면에서 특정 환경 세부 정보 페이지로 이동합니다.
1. **IP 허용 목록** 테이블로 이동합니다.
1. IP 허용 목록 및 이를 적용할 작성자 또는 게시 서비스를 선택할 수 있도록 표 상단의 입력 필드를 사용합니다.
IP 허용 목록을 적용하려면 Cloud Manager에 IP 도메인이 이미 있어야 합니다. [IP 허용 목록 추가](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md)를 참조하십시오.
1. **적용**&#x200B;을 클릭하여 제출을 확인합니다.

## IP 허용 목록 적용 취소 {#un-applying}

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 적용 취소할 수 있습니다.

**IP 허용 목록 적용을 취소하려면**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인합니다.
1. 적절한 조직을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 화면에서 특정 환경 세부 정보 페이지로 이동합니다.1. **IP 허용 목록** 테이블로 이동합니다.
1. 적용을 취소하려는 IP 허용 목록 행을 식별합니다.
1. 식별된 행의 오른쪽에서 줄임표 버튼을 클릭한 다음 **적용 취소**&#x200B;를 선택합니다.
1. 제출을 확인합니다.
