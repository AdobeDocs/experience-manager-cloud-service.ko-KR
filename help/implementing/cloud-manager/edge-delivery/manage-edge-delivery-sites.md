---
title: Cloud Manager에서 Edge Delivery 사이트 관리
description: Edge Delivery 사이트에 CDN 구성을 추가하거나 Edge Delivery 사이트를 삭제하는 방법에 대해 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Cloud Manager에서 Edge Delivery 사이트 관리 {#manage-edge-delivery-sites}

기존 사이트에 CDN 구성을 추가하여 Cloud Manager에서 Edge Delivery 사이트를 관리하는 방법을 알아봅니다. 또는 Edge Delivery 사이트를 삭제합니다.

## 기존 Edge Delivery 사이트에 CDN 구성 추가 {#add-cdn-to-edge-delivery-site}

[CDN 구성 추가](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)를 참조하십시오.

## Edge Delivery 사이트 삭제 {#delete-edge-delivery-site}

Edge Delivery Services 사이트를 삭제하면 연결된 CDN 구성도 모두 제거됩니다. 이 작업을 수행하면 사용자 지정 도메인과 사이트 간의 연결이 끊어집니다. 자세한 내용은 CDN 구성 을 참조하십시오. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**Edge Delivery 사이트를 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 Edge Delivery 사이트를 추가할 Edge Delivery Services이 구성된 프로그램을 선택합니다.
1. 다음 중 하나를 수행합니다.
   * **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다. Edge Delivery 사이트 테이블에서 제거할 사이트가 있는 행의 끝에 있는 생략 부호를 클릭합니다.
**삭제**&#x200B;를 클릭한 다음 **삭제**&#x200B;를 다시 클릭하여 사이트 제거를 확인합니다.

     ![Edge Delivery 탭에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * 페이지 왼쪽 상단 모서리에서 햄버거 아이콘을 클릭하여 왼쪽 탐색 메뉴를 표시합니다. **서비스** 제목에서 **Edge Delivery 사이트**를 클릭합니다.
Edge Delivery 사이트 테이블에서 제거할 사이트가 있는 행의 끝에 있는 생략 부호를 클릭합니다. **삭제**&#x200B;를 클릭한 다음 **삭제**&#x200B;를 다시 클릭하여 사이트 제거를 확인합니다.


     ![Edge Delivery Sites 단추에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)