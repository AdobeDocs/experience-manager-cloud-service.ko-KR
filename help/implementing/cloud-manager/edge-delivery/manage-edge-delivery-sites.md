---
title: Cloud Manager에서 Edge Delivery Sites 관리
description: Edge Delivery 사이트에 CDN 구성을 추가하거나 Edge Delivery 사이트를 삭제하는 방법을 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: a078d45f81fc7081012ebf24fa8f46dc1a218cd7
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 91%

---

# Cloud Manager에서 Edge Delivery 사이트 관리 {#manage-edge-delivery-sites}

기존 사이트에 CDN 구성을 추가하여 Cloud Manager에서 Edge Delivery 사이트를 관리하는 방법을 알아봅니다. 또는 Edge Delivery 사이트를 삭제합니다.

## 기존 Edge Delivery 사이트에 CDN 구성 추가 {#add-cdn-to-edge-delivery-site}

[CDN 구성 추가](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)를 참조하십시오.

## Edge Delivery 사이트 이름 변경(#rename-edge-delivery-site)

Adobe Cloud Manager에서 다음의 이유로 Edge Delivery 사이트 이름을 바꾸고자 할 수 있습니다.

* **명확성과 조직성**: 사이트의 목적이나 관련 환경(예: 프로덕션, 스테이징)을 더 잘 설명할 수 있습니다.
* **혼란 방지**: 여러 사이트를 사용 중인 경우 이름을 변경해 두 사이트를 쉽게 구분할 수 있으면 잘못된 사이트에 구성이나 업데이트를 적용할 가능성을 줄일 수 있습니다.
* **표준화**: 조직의 지침에 부합하는 일관된 명명 규칙을 따라 관리 및 감사를 더 쉽게 진행할 수 있습니다.

**Edge Delivery 사이트의 이름을 바꾸려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 Edge Delivery Services가 포함된 프로그램을 선택하고, 여기에 Edge Delivery 사이트를 추가합니다.
1. 다음 중 하나를 수행합니다.

   * **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다. Edge Delivery 사이트 테이블에서 이름을 바꾸려는 사이트의 행 끝의 줄임표를 클릭합니다.
**이름 변경**&#x200B;을 클릭합니다.
   * 페이지의 왼쪽 상단에서 ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다. **서비스** 제목 아래 ![Web pages icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**를 클릭합니다.
Edge Delivery 사이트 테이블에서 이름을 바꾸려는 사이트의 행 끝의 ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다. **이름 변경**&#x200B;을 클릭합니다.

1. **Edge Delivery 사이트 편집** 대화 상자에서 **사이트 이름** 텍스트 필드에 사이트의 새 이름을 입력합니다.

1. **편집**&#x200B;을 클릭합니다.

## Edge Delivery 사이트를 삭제 {#delete-edge-delivery-site}

Edge Delivery Services 사이트를 삭제하면 관련 CDN 구성도 모두 제거됩니다. 이 작업은 사용자 정의 도메인과 사이트 간의 연결을 끊습니다. 자세한 내용은 CDN 구성을 참조하십시오. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**Edge Delivery 사이트를 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 Edge Delivery Services가 포함된 프로그램을 선택하고, 여기에 Edge Delivery 사이트를 추가합니다.
1. 다음 중 하나를 수행합니다.

   * **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다. Edge Delivery 사이트 테이블에서 삭제하려는 사이트의 행 끝의 ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
![Edge Delivery 사이트 삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **삭제**&#x200B;을 클릭한 다음 **삭제**&#x200B;를 다시 클릭하여 사이트 제거를 확인합니다.

     ![Edge Delivery 탭에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * 페이지의 왼쪽 상단에서 ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 왼쪽 사이드 메뉴를 표시합니다. **서비스** 제목에서 ![Edge Delivery 사이트 웹 페이지 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery 사이트**를 클릭합니다.
Edge Delivery 사이트 테이블에서 삭제하려는 사이트의 행 끝의 ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다. ![Edge Delivery 사이트 삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **삭제**&#x200B;을 클릭한 다음 **삭제**&#x200B;를 다시 클릭하여 사이트 제거를 확인합니다.

     ![Edge Delivery Sites 버튼에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## 지원 티켓 기록 {#eds-support-ticket}

{{support-ticket}}
