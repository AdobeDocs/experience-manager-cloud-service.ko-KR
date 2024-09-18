---
title: Cloud Manager에 Edge Delivery 사이트 추가
description: 프로덕션 프로그램 또는 샌드박스 프로그램에 Edge Delivery 사이트를 추가하는 방법과 이점을 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 68f05c49ebc3d46aa44b3998e6142ab8547e5455
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 2%

---


# Cloud Manager에 Edge Delivery 사이트 추가 {#eds-add-site}

프로덕션 프로그램 또는 샌드박스 프로그램에 Edge Delivery 사이트를 추가하는 방법과 이점을 알아봅니다.

## 소개 {#introduction}

AEM as a Cloud Service을 사용하는 Edge Delivery Services 프로젝트의 일부로 Edge Delivery 사이트를 Cloud Manager에 추가하는 것이 좋습니다. Edge Delivery 웹 사이트를 Cloud Manager에 추가하면 다음과 같은 이점이 있습니다.

* [Adobe 관리 CDN에 대한 액세스](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)
* [SLA 보고서에 대한 액세스](/help/implementing/cloud-manager/sla-reporting.md)
* [라이선스 사용 현황 보고서 액세스](/help/implementing/cloud-manager/license-dashboard.md)

[Edge Delivery 프로젝트에 대한 지원 티켓을 등록하려면 Edge Delivery 사이트를 Cloud Manager에 추가해야 합니다.](/help/edge/overview.md##support-ticket)

## Cloud Manager에 및 Edge Delivery 사이트 추가 {#adding}

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. 다음 중 하나를 수행하십시오.
   * **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다. 그런 다음 페이지의 오른쪽 아래 모서리에서 **Edge Delivery 사이트 추가**&#x200B;를 클릭합니다.

     ![Edge Delivery 탭에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * 페이지 왼쪽 상단 모서리에서 햄버거 아이콘을 클릭하여 왼쪽 탐색 메뉴를 표시합니다. **서비스** 제목에서 **Edge Delivery 사이트**&#x200B;를 클릭합니다. 페이지의 오른쪽 상단 근처에 있는 **사이트 추가**&#x200B;를 클릭합니다.

     ![Edge Delivery Sites 단추에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. **Edge Delivery 사이트 추가** 대화 상자에서 필수 필드에 다음 정보를 제공합니다.

   | 텍스트 필드 | 제공할 데이터 |
   | --- | --- |
   | 사이트 이름 | 추가하려는 Edge Delivery 사이트의 이름을 입력합니다. 이 이름은 Cloud Manager 내에서 사이트의 고유 식별자 역할을 합니다. |
   | 저장소 URL | 이 필드는 웹 사이트의 코드가 저장된 Git 저장소를 나타냅니다. 이 필드를 사용하면 Cloud Manager이 배포 프로세스 중에 해당 저장소에서 코드를 가져올 수 있습니다. |
   | 사이트 설명 (선택 사항) | 추가하려는 Edge Delivery 사이트에 대한 간략한 설명을 입력합니다. 이 설명은 사이트를 식별하고 구분하는 데 도움이 되므로 추가한 다른 사이트 간에 보다 쉽게 관리하고 인식할 수 있습니다. |

1. 대화 상자의 오른쪽 아래 모서리에서 **추가**&#x200B;를 클릭합니다.

1. **저장소 소유권 확인** 대화 상자가 열립니다. 이 창을 연 상태에서 다음 단계를 수행하십시오.

   1. **저장소 URL** 필드에 나열된 Git 저장소의 `main` 분기에 경로와 이름이 `well-known/adobe/cloudmanager-challenge.txt`인 파일을 추가하십시오.
      * 필요한 경우 **복사** 아이콘을 클릭하여 클립보드에 경로를 복사합니다.
      * 위치 경로의 시작 부분에 마침표를 *추가하지 마십시오*.
   1. **Step &amp;num; 1** 필드의 코드를 이전 단계에서 만든 파일에 추가합니다.
      * 필요한 경우 **복사** 아이콘을 클릭하여 코드를 클립보드에 복사합니다.
   1. Git 리포지토리에서 방금 만든 변경 내용에 대한 끌어오기 요청을 만든 다음 `main`에 병합합니다.

1. **확인**&#x200B;을 클릭합니다.

저장소가 확인되면 Edge Deliver Sites 테이블의 상태가 내부에 흰색 확인 표시가 있는 녹색 원으로 변경됩니다.

프로덕션 프로그램에 Edge Delivery Services을 추가하면 Edge Delivery Services 라이선스가 적용됩니다.

각 Edge Delivery 사이트에는 Edge Delivery 사이트를 만드는 과정을 안내하는 **Edge Delivery 할 일 목록**&#x200B;이 있습니다.

![Edge Delivery 할 일 앱](/help/implementing/cloud-manager/assets/edge-delivery-to-do-ist.png)

이 단계에 대한 자세한 내용은 [Cloud Manager에서 Edge Delivery Services 소개](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list) 문서를 참조하십시오.
