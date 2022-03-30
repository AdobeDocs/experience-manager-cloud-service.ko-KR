---
title: DNS 레코드 상태 확인
description: Cloud Manager를 사용하여 DNS 설정이 제대로 해결되는지 여부를 확인하는 방법을 알아봅니다.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: 2278abcf0c34fd34a7730242ee27814d37b7d4d0
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 3%

---

# DNS 레코드 상태 확인 {#check-dns-record-status}

Cloud Manager 내에서 도메인 이름이 AEM as a Cloud Service 웹 사이트로 제대로 확인되고 있는지 여부를 확인할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **환경** 화면 **개요** 페이지.

1. 클릭 **도메인 설정** 왼쪽 탐색 패널

1. 을(를) 클릭합니다. **상태** 아이콘 을 클릭하여 도메인 이름을 지정합니다.

Cloud Manager는 도메인 이름에 대한 DNS 조회를 수행하고 다음 상태 메시지 중 하나를 표시합니다.

* **DNS 상태가 검색되지 않음** - 사용자 지정 도메인 이름을 확인하고 배포할 때까지 DNS 상태가 검색되지 않습니다.

   * 사용자 지정 도메인 이름이 삭제 프로세스 중일 때도 이 상태가 관찰됩니다.

* **DNS가 잘못 확인됨** - DNS 레코드 구성이 확인되지 않았거나 잘못된 것임을 나타냅니다.

   * 문서를 참조하십시오 [DNS 설정 구성](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) 추가 정보
   * When ready, you must select the **Resolve Again** icon next to the status.

* **DNS Resolution In Progress** - The resolution is in progress.

   * This status is typically seen after you select the **Resolve Again** icon next to the status.

* **DNS Resolves Correctly** - Your DNS settings are properly configured.

   * 사이트가 방문자를 제공하고 있습니다.

Cloud Manager will automatically trigger a DNS lookup when your custom domain name is first successfully verified and deployed. For subsequent attempts, you must actively select the **Resolve Again** icon next to the status.
