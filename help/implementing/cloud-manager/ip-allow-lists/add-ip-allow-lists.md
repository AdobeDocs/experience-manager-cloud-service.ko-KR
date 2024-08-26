---
title: IP 허용 목록 추가
description: Cloud Manager을 사용하여 나만의 IP 허용 목록을 추가하는 방법을 알아봅니다.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 12%

---


# IP 허용 목록 추가 {#add-ip-allow-list}

Cloud Manager을 사용하여 나만의 IP 허용 목록을 추가하는 방법을 알아봅니다.

**비즈니스 소유자** 또는 **배포 관리자** 역할의 사용자는 다음 단계에 따라 IP 허용 목록을 추가할 수 있습니다.

{{add-cm-allowlist-frontend-pipeline}}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 왼쪽의 사이드 패널을 사용하여(왼쪽 상단에 있는 햄버거 아이콘을 클릭하여 패널을 표시해야 할 수 있음) **IP 허용 목록**&#x200B;을 클릭합니다.

   ![사이드 패널의 IP 허용 목록 옵션](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. IP 허용 목록 페이지의 오른쪽 상단 모서리에서 **IP 허용 목록 추가**&#x200B;를 클릭합니다.

   ![IP 허용 목록 추가 대화 상자](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. **IP 허용 목록 추가** 대화 상자의 **IP 허용 목록 이름** 필드에 IP 허용 목록 참조에 사용할 이름을 입력합니다. 이 이름은 정보 제공용입니다. 목록을 식별하는 데 도움이 될 만큼 설명적인지 확인하십시오.

1. **IP 주소/CIDR** 필드에 IP 또는 IP CIDR 블록을 입력하십시오. 여러 블록은 쉼표나 탭으로 구분하십시오.

1. **저장**&#x200B;을 클릭합니다.

저장한 후 새로 만든 IP 허용 목록이 **IP 허용 목록** 페이지의 표에 행으로 나타납니다.

## Cloud Manager IP 허용 목록 추가 {#add-cm-allowlist}

프론트엔드 파이프라인을 사용하려면 먼저 다음 Cloud Manager IP 허용 목록을 추가해야 합니다.

**Cloud Manager IP 허용 목록**

`52.254.106.192/28,20.186.185.181,52.254.106.240/28,52.254.107.128/28,52.254.105.192/28,52.254.106.176/28,20.186.185.227,52.254.106.144/28,52.254.107.64/28,20.186.185.239,20.22.83.112,52.254.107.80/28,52.254.107.144/28,52.254.106.224/28,20.14.241.153,52.254.107.0/28,52.254.107.32/28,52.254.106.208/28,40.70.154.136/29,52.254.106.160/28,52.254.107.16/28,52.254.106.0/28,4.152.211.251`

프론트엔드 파이프라인 실행이 중단되지 않도록 하려면 이 Cloud Manager IP 허용 목록이 추가된 다음 *이전* 환경의 작성자 서비스에 적용되는지 확인하십시오.

**Cloud Manager IP 허용 목록을 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 왼쪽의 사이드 패널을 사용하여(왼쪽 상단에 있는 햄버거 아이콘을 클릭하여 패널을 표시해야 할 수 있음) **IP 허용 목록**&#x200B;을 클릭합니다.

1. IP 허용 목록 페이지의 오른쪽 상단 모서리에서 **IP 허용 목록 추가**&#x200B;를 클릭합니다.

1. **IP 허용 목록 추가** 대화 상자의 **IP 허용 목록 이름** 필드에 *`Cloud Manager`*&#x200B;을(를) 입력합니다.

1. 위의 Cloud Manager IP 허용 목록 주소 블록을 복사합니다. 각 주소는 이미 쉼표로 구분되어 있습니다.

1. **IP 허용 목록 추가** 대화 상자에서 블록을 **IP 주소/CIDR** 필드에 붙여 넣습니다.

1. 주소 목록에서 첫 번째 쉼표 바로 뒤에 커서를 놓고 **Enter**&#x200B;를 누릅니다.

1. **저장**&#x200B;을 클릭합니다.

이제 [Cloud Manager IP 허용 목록을 적용](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)하여 프로그램 환경을 개선하세요.



