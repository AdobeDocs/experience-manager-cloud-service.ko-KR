---
title: DNS 레코드 상태 확인
description: Cloud Manager를 사용하여 DNS 설정이 제대로 구성되고 있는지 확인하는 방법을 알아봅니다.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: 2278abcf0c34fd34a7730242ee27814d37b7d4d0
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 100%

---

# DNS 레코드 상태 확인 {#check-dns-record-status}

Cloud Manager 내에서 도메인 이름이 AEM as a Cloud Service 웹 사이트로 올바르게 확인되는지 확인할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **개요** 페이지에서 **환경** 화면으로 이동합니다.

1. 왼쪽 탐색 패널에서 **도메인 설정**&#x200B;을 클릭합니다.

1. 도메인 이름에 대한 **상태** 아이콘을 클릭합니다.

Cloud Manager는 도메인 이름에 대한 DNS 조회를 수행하고 다음 상태 메시지 중 하나를 표시합니다.

* **DNS 상태가 감지되지 않음** - 사용자 정의 도메인 이름이 성공적으로 확인 및 배포될 때까지 DNS 상태가 감지되지 않습니다.

   * 이 상태는 사용자 정의 도메인 이름을 삭제하는 동안에도 관찰됩니다.

* **DNS가 잘못 확인됨** - DNS 레코드 구성이 확인되지 않았거나 잘못되었음을 나타냅니다.

   * 자세한 내용은 [DNS 설정 구성](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) 문서를 참조하십시오.
   * 준비가 되면 상태 옆에 있는 **다시 해결** 아이콘을 선택해야 합니다.

* **DNS 확인 진행 중** - 확인이 진행 중입니다.

   * 이 상태는 일반적으로 상태 옆에 있는 **다시 해결** 아이콘을 선택한 후에 표시됩니다.

* **DNS가 올바르게 확인됨** - DNS 설정이 올바르게 구성되었습니다.

   * 사이트가 방문자에게 서비스를 제공하고 있습니다.

사용자 정의 도메인 이름이 처음으로 확인 및 배포되면 Cloud Manager가 자동으로 DNS 조회를 트리거합니다. 이후 시도 시 상태 옆에 있는 **다시 해결** 아이콘을 선택해야 합니다.
