---
title: IP 허용 목록 적용 및 적용 취소
description: 환경에 IP 허용 목록을 적용 및 적용 취소하는 방법을 알아봅니다.
exl-id: 7158496c-b0c4-4228-a306-71dc51003c57
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 84%

---


# IP 허용 목록 적용 및 적용 취소 {#apply-allow-list}

IP 허용 목록을 적용할 때 목록의 정의에 포함된 모든 IP 범위는 환경 내의 작성자 또는 게시 서비스와 연결됩니다. 목록 적용을 취소하는 것은 이 프로세스의 반대입니다.

## IP 허용 목록 적용 {#applying}

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 적용할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 화면에서 특정 환경 세부 정보 페이지로 이동하고 **IP 허용 목록** 표로 이동합니다.
1. IP 허용 목록과 이를 적용할 작성자 또는 게시 서비스를 선택할 수 있도록 표 상단의 입력 필드를 사용합니다.
   * IP 허용 목록을 적용하려면 Cloud Manager에 해당 목록이 있어야 합니다.
1. **적용**&#x200B;을 클릭하여 제출을 확인합니다.

## 허용 목록 적용 취소 {#un-applying}

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 적용 취소할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 화면에서 특정 환경 세부 정보 페이지로 이동하고 **IP 허용 목록** 표로 이동합니다.
1. 적용을 취소하려는 IP 허용 목록 행을 식별합니다.
1. 행의 오른쪽 끝에 있는 줄임표 버튼을 선택합니다.
1. **적용 취소** 옵션을 선택하여 제출을 확인합니다.
