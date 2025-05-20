---
title: 한 번의 클릭으로 첫 번째 Edge Delivery 사이트 만들기
description: 버튼 클릭만으로 Cloud Manager에서 Edge Delivery 사이트를 빠르게 만드는 방법에 대해 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 292bf0b4-990b-4980-b971-91b8aedde3de
source-git-commit: 0c4ef0eb5bb7caa5cd68dac6c788b37f564e1770
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 95%

---

# 한 번의 클릭으로 첫 번째 Edge Delivery 사이트 만들기{#about-one-click-edge-delivery-site}

한 번의 클릭으로 첫 번째 Edge Delivery 사이트를 만들면 Cloud Manager 내에서 Edge Delivery 사이트의 온보딩 및 배포를 자동화할 수 있습니다. 버튼 하나만 클릭하면 되므로 과정이 크게 간소화됩니다. 클릭 한 번으로 필요한 인프라를 프로비저닝하고, GitHub와 통합하여 버전을 제어하며, Google Drive에서 문서 및 자산 저장소를 구성할 수 있습니다.

이러한 자동화는 초기 사이트를 설정하는 데 필요한 수작업을 줄이는 데 도움이 됩니다. 원활한 워크플로와 확장성을 보장하고 에지에서 콘텐츠를 관리할 때 팀의 성과를 향상시킵니다.

<!-- Check out this quick 2-minute video for a step-by-step walkthrough on creating your first Edge Delivery site—no hassle, just one click.

>[!VIDEO](https://video.tv.adobe.com/v/3458975?quality=12&learn=on) -->



<!-- >
## Practical use cases {#use-cases}

| Use case | Description |
| --- | --- |
| Website and application deployment | <ul><li>Automate the hosting and delivery of static or dynamic sites.</li><li>Ensure fast performance through edge caching. </li></ul> |
| API gateway and content delivery | <ul><li>Optimize API responses by caching data at the edge.</li><li>Reduce backend load and improved response times. </li></ul> |
| Real-time content updates | <ul><li>Instant deployment of new content across edge locations.</li><li>Support integration with automated content pipelines. </li></ul> |
| Edge computing workloads | <ul><li>Support serverless computing to process workloads closer to users.</li><li>Reduce latency and enhance performance. </li></ul> |
| Security and governance | <ul><li>Security is provided with integrated DDoS (Distributed Denial of Service) protection and WAF (Web Application Firewall) integration.</li><li>Ensure that content is delivered securely through TLS (Transport Security Layer) encryption. </li></ul> |
-->





## 클릭 한 번으로 Cloud Manager에서 Edge Delivery 사이트 만들기 {#one-click-edge-delivery-site}

클릭 한 번으로 Adobe Edge Delivery 사이트를 만들려면 조직에 사용 가능한 Edge Delivery Services 라이선스가 있어야 합니다. 이 라이선스는 Adobe Experience Manager(AEM)의 일부이며 Cloud Manager 내에서 Edge Delivery Services를 만드는 데 필요합니다.

권한 측면에서 비즈니스 소유자 역할의 멤버이거나 Cloud Manager에서 프로그램을 추가 또는 편집할 수 있는 적절한 권한이 부여되어야 합니다. 이 접근 수준을 통해 프로그램에 Edge Delivery 서비스를 통합하는 것을 관리할 수 있습니다.

[Cloud Manager에서의 Edge Delivery Services 소개](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md)도 참조하십시오.

<!-- PROPER AEM BOT CONFIGURATIONS MUST BE IN PLACE FIRST FOR AUTOMATIC CONTENT UPDATES? TRUE or FALSE? -->

**클릭 한 번으로 Cloud Manager에서 Edge Delivery 사이트를 만들려면 다음 작업을 수행하십시오.**

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단에서 ![메뉴 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다.
1. 왼쪽 메뉴에서 **프로그램** 제목 아래에 있는 **개요**&#x200B;를 클릭합니다.
1. **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다.
1. Edge Delivery 페이지에서 **Edge Delivery 할 일 목록** 대화 상자 내의 **Edge Delivery 사이트 추가** 그룹 상자에서 **지금 사이트 생성**&#x200B;을 클릭합니다.
1. **Edge Delivery 사이트 생성** 대화 상자에서 **프로젝트 이름** 텍스트 필드에 사이트 이름을 입력한 다음 **지금 사이트 만들기**&#x200B;를 클릭합니다.

   화면 상단 중앙에 알림이 나타나 Edge Delivery 사이트 프로비저닝이 시작되었음을 알려 줍니다.

Cloud Manager에서 사이트 프로비저닝 및 검증이 완료되면 **사이트 이름**(이전에 입력한 프로젝트 이름)이 Edge Delivery 페이지의 **Edge Delivery 사이트** 목록 상자에 표시됩니다. 또한 저장소 URL 왼쪽에 녹색 확인 표시가 표시됩니다.


### 클릭 한 번으로 생성된 Edge Delivery 사이트 탐색 {#explore-one-click-ed-site}

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단에서 ![메뉴 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다.
1. 왼쪽 메뉴에서 **프로그램** 제목 아래에 있는 **개요**&#x200B;를 클릭합니다.
1. **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다.
1. Edge Delivery 페이지에서 다음 중 하나를 수행하십시오.

   | 탐색할 항목 | 단계 |
   | --- | --- |
   | 사이트의 GitHub 저장소 | <ul><li>**Edge Delivery 사이트** 목록 상자에서 **저장소** 열 제목 아래에 있는, 방금 생성한 사이트의 URL을 클릭합니다.<br>사용자 이름 또는 이메일 주소와 암호로 GitHub에 로그인해야 할 수 있습니다.</li> |
   | 사이트 게시 | <ul><li> **Edge Delivery 사이트** 목록 상자에서 사이트 이름의 맨 오른쪽에 있는 ![더 보기 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 드롭다운 메뉴를 엽니다.</li><li>드롭다운 메뉴에서 ![게시 확인 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PublishCheck_18_N.svg)을 클릭하여 **사이트 게시**&#x200B;를 선택합니다.<br>사이트 게시가 성공적으로 시작되었음을 알려 주는 확인 메시지가 표시됩니다.</li></ul> |
   | 게시된 사이트 미리보기 | <ul><li>**Edge Delivery 사이트** 목록 상자에서 **사이트 이름** 열 제목 아래에 있는, 방금 생성 및 게시한 사이트의 URL을 클릭합니다.<br>브라우저의 URL 주소 표시줄에서 사이트 URL이 `.page`로 끝나는 것을 확인하십시오. 이는 사이트 미리보기를 보고 있다는 것을 의미합니다.</li><li>사이트를 라이브로 보려면 URL 주소 표시줄에서 `.page`를 `.live`로 수동으로 변경하십시오.</li></ul> |
   | Google Drive의 콘텐츠 저장소에 대한 사용자 액세스 권한 부여 | <ul><li> **Edge Delivery 사이트** 목록 상자에서 사이트 이름의 맨 오른쪽에 있는 ![더 보기 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 드롭다운 메뉴를 엽니다.</li><li>드롭다운 메뉴에서 ![사용자 추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg)을 클릭하여 **콘텐츠 저장소에 대한 액세스 권한 받기**&#x200B;를 선택합니다.</li><li>**사이트에 공동 작업자 추가** 대화 상자에서 참여자의 이메일 주소를 입력한 후 ![체크 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg)을 클릭합니다.</li><li>필요에 따라 참여자 이메일을 계속 추가합니다.</li><li>작업을 완료하면 **공동 작업자 추가**&#x200B;를 클릭합니다.</li><li>콘텐츠 공동 작업자와 링크를 공유하려면 **공동 작업자가 정상적으로 추가됨** 대화 상자에서 **확인**&#x200B;을 클릭합니다.</li><li>공동 작업자가 정상적으로 추가됨 대화 상자에서 ![복사 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)을 클릭하여 링크를 복사한 후 공동 작업자와 공유합니다.<br>링크를 공유하기 전에 공동 작업자가 IMS 계정과 연결된 이메일 주소로 로그인되어 있는지 확인하십시오. IMS 이메일 계정이 사용 불가능한 경우, 공동 작업자로 추가된 이메일 주소를 사용해야 합니다. 이렇게 하면 공동 작업자가 링크에 액세스하여 Google Drive에서 콘텐츠를 편집하거나 업데이트할 수 있습니다.</li><li>편집이 완료되면 위에서 설명한 대로 Cloud Manager에서 **사이트 게시**&#x200B;를 클릭합니다.<br>또는 위에서 설명한 대로 변경 사항을 미리 봅니다.</li></ul> |
   | GitHub의 기본 저장소에 대한 사용자 액세스 권한 부여 | <ul><li> **Edge Delivery 사이트** 목록 상자에서 사이트 이름의 맨 오른쪽에 있는 ![더 보기 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 드롭다운 메뉴를 엽니다.</li><li>드롭다운 메뉴에서 ![코드 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg)을 클릭하여 **기본 저장소에 대한 액세스 권한 받기**&#x200B;를 선택합니다.</li><li>**사이트의 기본 저장소에 액세스** 대화 상자에서 공동 작업자의 GitHub 사용자 이름을 입력한 후 ![체크 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg)을 클릭합니다.</li><li>필요에 따라 GitHub 사용자 이름을 계속 추가합니다.</li><li>작업을 완료하면 **공동 작업자 추가**&#x200B;를 클릭합니다.</li>사용자는 저장소를 보려면 GitHub 사용자 이름에 대한 액세스를 허용해야 합니다. |
