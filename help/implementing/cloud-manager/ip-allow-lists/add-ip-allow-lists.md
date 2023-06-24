---
title: IP 허용 목록 추가
description: 허용 목록에 추가하다 Cloud Manager를 사용하여 자체 IP를 추가하는 방법을 알아봅니다.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 40%

---


# IP 허용 목록 추가 {#add-ip-allow-list}

허용 목록에 추가하다 Cloud Manager를 사용하여 자체 IP를 추가하는 방법을 알아봅니다.

의 사용자 **비즈니스 소유자** 또는 **배포 관리자** 역할은 다음 단계에 따라 IP 허용 목록을 추가할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **개요** 페이지에서 **환경** 화면으로 이동합니다.

1. **환경** 화면에서 **IP 허용 목록** 페이지로 이동합니다.

   ![사이드 패널의 IP 허용 목록 옵션](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. 클릭 **IP 허용 목록 추가** 을(를) 열려면 **IP 허용 목록 추가** 대화 상자.

   ![IP 허용 목록 추가 대화 상자](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. 에서 허용 목록에 추가하다를 참조하는 데 사용할 이름을 입력하십시오. **IP 허용 목록 이름** 필드.

   * 이 이름은 정보 제공용으로만 제공되며 목록을 식별하는 데 도움이 되는 설명을 제공해야 합니다.

1. **IP 주소/CIDR** 필드에 IP 또는 IP CIDR 블록을 입력합니다.

   * 여러 블록은 쉼표나 탭으로 구분할 수 있습니다.

1. **저장**&#x200B;을 클릭하여 제출을 확인합니다.

새로 만든 IP 테이블을 저장한 후 의 행에 허용 목록에 추가하다 테이블이 나타납니다. **IP 허용 목록** 페이지를 가리키도록 업데이트하는 중입니다.
