---
title: DNS 레코드 상태 확인
description: DNS 레코드 상태 확인
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: 17dffaae3beac678ce89b5fde7abea3b2dff86a8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# DNS 레코드 상태 확인 {#check-dns-record-status}

도메인 설정 페이지의 Environments 테이블에서 DNS 레코드에 대한 Status 아이콘을 클릭하여 도메인 이름이 AEM as a Cloud Service 웹 사이트로 제대로 확인되는지 여부를 확인할 수 있습니다.

사용자 지정 도메인 이름이 처음 확인되고 배포되면 Cloud Manager가 DNS 조회를 자동으로 트리거합니다. 후속 시도에 대해서는 상태 옆에 있는 **다시 해결** 아이콘을 선택해야 합니다.

Cloud Manager는 도메인 이름에 대한 DNS 조회를 수행하고 다음 상태 메시지 중 하나를 표시합니다.

* **DNS 상태가**
검색되지 않음 사용자 지정 도메인 이름을 확인하고 배포할 때까지 DNS 상태가 검색되지 않습니다. 사용자 지정 도메인 이름이 삭제 프로세스 중일 때도 이 상태가 관찰됩니다.

* **DNS가**
잘못 확인됨DNS 레코드 구성이 아직 확인/검토되지 않았거나 잘못된 것임을 나타냅니다.

   >[!NOTE]
   >해당 지침에 따라 `CNAME` 또는 `A-record`을 구성해야 합니다. 자세한 내용은 DNS 설정 구성을 참조하십시오. 준비가 완료된 경우 상태 옆에 있는 **다시 해결** 아이콘을 선택해야 합니다.

* **ProgressResolution의 DNS**
확인이 진행 중입니다. 이 상태는 일반적으로 상태 옆에 있는 &#39;다시 해결&#39; 아이콘을 선택하면 표시됩니다.

* **DNS가**
올바르게 확인됩니다. DNS 설정이 올바르게 구성되어 있습니다. 사이트가 방문자를 제공하고 있습니다.
