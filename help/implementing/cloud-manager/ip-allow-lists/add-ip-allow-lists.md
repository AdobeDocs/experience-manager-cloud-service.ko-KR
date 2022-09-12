---
title: IP 허용 목록 추가
description: Cloud Manager를 사용하여 고유한 IP 허용 목록을 추가하는 방법을 알아봅니다.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 378ff582435f1ab3db431a0c9c3e80a4661cccc4
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 3%

---


# IP 허용 목록 추가 {#add-ip-allow-list}

Cloud Manager를 사용하여 고유한 IP 허용 목록을 추가하는 방법을 알아봅니다.

의 사용자 **비즈니스 소유자** 또는 **배포 관리자** 역할은 다음 단계에 따라 IP 허용 목록을 추가할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 다음으로 이동 **환경** 화면 **개요** 페이지.

1. 다음으로 이동 **IP 허용 목록** 페이지의 **환경** 화면.

   ![사이드 패널의 IP 허용 목록 옵션](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. 클릭 **IP 허용 목록 추가** 열다 **IP 허용 목록 추가** 대화 상자.

   ![IP 허용 목록 추가 대화 상자](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. 에서 허용 목록을 참조하는 데 사용할 이름을 입력합니다. **IP 허용 목록 이름** 필드.

   * 이 정보는 정보 제공용이므로 목록을 식별하는 데 도움이 되도록 설명되어야 합니다.

1. 에 IP 또는 IP CIDR 블록을 입력합니다. **IP 주소/CIDR** 필드.

   * 여러 블록은 쉼표나 탭으로 구분될 수 있습니다.

1. 클릭 **저장** 을 클릭하여 제출을 확인합니다.

저장하면 새로 만든 IP 허용 목록이 의 표에 행으로 표시됩니다 **IP 허용 목록** 페이지.
