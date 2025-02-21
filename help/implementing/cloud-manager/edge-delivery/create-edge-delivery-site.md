---
title: Cloud Manager에서 Edge Delivery 사이트 만들기
description: 버튼을 클릭하여 Cloud Manager에서 Edge Delivery 사이트를 빠르게 만드는 방법을 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0e1248ee8ceb324ee44dce296135d651d28c9f97
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 31%

---


# Cloud Manager에서 Edge Delivery 사이트 만들기 {#about-one-click-edge-delivery-site}

Edge Delivery 사이트 만들기 기능은 Cloud Manager 내에서 Edge Delivery 사이트의 온보딩 및 배포를 자동화하는 데 도움이 되도록 설계되었습니다. 버튼 하나만 클릭하면 되므로 과정이 크게 간소화됩니다. 클릭 한 번으로 필요한 인프라를 프로비저닝하고, GitHub와 통합하여 버전을 제어하며, Google Drive에서 문서 및 자산 저장소를 구성할 수 있습니다.

이러한 자동화는 초기 사이트를 설정하는 데 필요한 수작업을 줄이는 데 도움이 됩니다. 원활한 워크플로와 확장성을 보장하고 에지에서 콘텐츠를 관리할 때 팀의 성과를 향상시킵니다.

## 주요 개념 {#key-concepts}

한 번의 클릭으로 Cloud Manager에서 Edge Delivery 사이트를 만들 때의 주요 개념입니다.

| 주요 개념 | 설명 |
| --- | --- |
| 자동화된 Edge 배포 | <ul><li>사용자는 Edge Delivery 사이트를 즉시 만들고 구성할 수 있습니다.</li><li>Cloud Manager과 CI/CD 워크플로우의 통합을 통해 수동 온보딩 프로세스의 필요성을 줄이거나 없앱니다.</li><li>Cloud Manager와 통합되어 원활한 CI/CD 워크플로를 제공합니다.</li></ul> |
| Cloud Manager와 통합 | <ul><li>Cloud Manager의 사용자 인터페이스를 사용하여 One Click Edge Delivery 프로세스를 트리거합니다.</li><li>자동화된 저장소 생성 및 배포에 대한 액세스를 제공합니다.</li></ul> |
| GitHub 기반 버전 제어 | <ul><li>배포를 표준화하기 위해 미리 정의된 보일러플레이트 템플릿을 사용하여 조직 내에 GitHub 저장소를 만듭니다.</li><li>콘텐츠 업데이트를 위한 AEM Bot 링크.</li></ul> |
| 문서 및 자산 저장 통합 | <ul><li>저장을 위해 Google Drive 폴더를 생성합니다.<li>저장소에 AEM 코드 동기화 애플리케이션을 설치하여 원활한 동기화 및 배포를 보장합니다.</li></li><li>공동 작업자는 문서를 쉽게 관리할 수 있습니다.</li></ul> |
| 보안 및 확장성 | <ul><li>기업 보안 표준 준수를 보장합니다.</li><li>는 다양한 Cloud Manager 테넌트에서 여러 Edge Delivery 사이트를 지원합니다.</li></ul> |

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

한 번의 클릭으로 Adobe Edge 게재 사이트를 만들려면 조직에 사용 가능한 Edge Delivery Services 라이선스가 있어야 합니다. 이 라이선스는 Adobe Experience Manager(AEM)의 일부이며 Cloud Manager 내에서 Edge Delivery Services를 만드는 데 필요합니다.

권한 측면에서 비즈니스 소유자 역할의 멤버이거나 Cloud Manager에서 프로그램을 추가 또는 편집할 수 있는 적절한 권한이 부여되어야 합니다. 이 접근 수준을 통해 프로그램에 Edge Delivery 서비스를 통합하는 것을 관리할 수 있습니다.

[Cloud Manager에서의 Edge Delivery Services 소개](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md)도 참조하십시오.

<!-- PROPER AEM BOT CONFIGURATIONS MUST BE IN PLACE FIRST FOR AUTOMATIC CONTENT UPDATES? TRUE or FALSE? -->

**클릭 한 번으로 Cloud Manager에서 Edge Delivery 사이트를 만들려면 다음 작업을 수행합니다.**

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단에서 ![메뉴 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다.
1. 왼쪽 메뉴에서 **프로그램** 제목 아래의 **개요**&#x200B;를 클릭합니다.
1. **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다.
1. Edge Delivery 페이지의 **Edge Delivery 할 일 목록** 대화 상자, **Edge Delivery 사이트 추가** 그룹 상자에서 **지금 사이트 만들기**&#x200B;를 클릭합니다.
1. **Edge Delivery 사이트 만들기** 대화 상자의 **프로젝트 이름** 텍스트 필드에 사이트 이름을 입력한 다음 **지금 사이트 만들기**&#x200B;를 클릭합니다.

   화면 상단 중앙에 Edge Delivery 사이트 프로비저닝이 시작되었음을 알리는 알림이 표시됩니다.

Cloud Manager에서 사이트 프로비저닝 및 유효성 검사를 완료하면 Edge Delivery 페이지의 **Edge Delivery sites** 목록 상자에 **사이트 이름**(이전에 입력한 프로젝트 이름)이 나타납니다. 또한 저장소 URL 왼쪽에 녹색 확인 표시가 나타납니다.


### 한 번의 클릭으로 생성된 Edge Delivery 사이트 탐색 {#explore-one-click-ed-site}

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단에서 ![메뉴 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다.
1. 왼쪽 메뉴에서 **프로그램** 제목 아래의 **개요**&#x200B;를 클릭합니다.
1. **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다.
1. Edge Delivery 페이지에서 다음 중 하나를 수행합니다.

   | 탐색 항목 | 단계 |
   | --- | --- |
   | 사이트의 GitHub 저장소 | <ul><li>**Edge Delivery 사이트** 목록 상자의 **저장소** 열 머리글 아래에서 방금 만든 사이트의 URL을 클릭합니다.<br>사용자 이름 또는 전자 메일 주소와 암호를 사용하여 GitHub에 로그인해야 할 수 있습니다.</li> |
   | 사이트 게시 | <ul><li> **Edge Delivery 사이트** 목록 상자에서 사이트 이름의 맨 오른쪽에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 드롭다운 메뉴를 엽니다.</li><li>드롭다운 메뉴에서 ![사이트 게시 확인 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PublishCheck_18_N.svg) **사이트 게시**&#x200B;을 클릭합니다.<br>사이트 게시가 성공적으로 시작되었음을 알리는 알림 메시지가 나타납니다.</li></ul> |
   | 게시된 사이트 미리보기 | <ul><li>**Edge Delivery 사이트** 목록 상자의 **사이트 이름** 열 머리글 아래에서 방금 만들고 게시한 사이트의 URL을 클릭합니다.<br>브라우저의 URL 주소 표시줄에서 사이트 URL이 `.page`(으)로 끝나므로 사이트 미리 보기가 표시됩니다.</li><li>사이트를 실시간으로 보려면 URL 주소 표시줄에서 `.page`을(를) `.live`(으)로 수동으로 변경하십시오.</li></ul> |
   | 사용자에게 Google 드라이브의 컨텐츠 저장소에 대한 액세스 권한 부여 | <ul><li> **Edge Delivery 사이트** 목록 상자에서 사이트 이름의 맨 오른쪽에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 드롭다운 메뉴를 엽니다.</li><li>드롭다운 메뉴에서 ![사용자 추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg) **콘텐츠 저장소에 대한 액세스 권한 얻기**&#x200B;를 클릭합니다.</li><li>**사이트에 공동 작업자 추가** 대화 상자에서 기여자의 전자 메일 주소를 입력한 다음 ![확인 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg)을 클릭합니다.</li><li>필요한 경우 기여자 이메일을 계속 추가합니다.</li><li>완료되면 **공동 작업자 추가**&#x200B;를 클릭하세요.</li><li>콘텐츠 공동 작업자와 링크를 공유하려면 **Collaboration이 추가됨** 대화 상자에서 **확인**&#x200B;을 클릭합니다.<br>공동 작업자는 전자 메일에서 **열기**&#x200B;를 클릭하여 공유 Google 드라이브 폴더에 기여하기 위한 전자 메일 초대를 받습니다. 로그인할 필요가 없습니다. 위에서 설명한 대로 공유 폴더의 파일을 편집하고 업데이트한 다음 Cloud Manager에서 **사이트 게시**&#x200B;를 클릭할 수 있습니다. 위에서 설명한 대로 변경 사항을 미리 볼 수도 있습니다.</li></ul> |
   | 사용자에게 GitHub의 기본 저장소에 대한 액세스 권한 부여 | <ul><li> **Edge Delivery 사이트** 목록 상자에서 사이트 이름의 맨 오른쪽에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 드롭다운 메뉴를 엽니다.</li><li>드롭다운 메뉴에서 ![코드 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) **기본 저장소에 대한 액세스 권한을 얻음**&#x200B;을 클릭합니다.</li><li>**사이트의 기본 저장소에 액세스** 대화 상자에서 공동 작업자의 GitHub 사용자 이름을 입력한 다음 ![확인 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg)을 클릭합니다.</li><li>필요에 따라 GitHub 사용자 이름을 계속 추가합니다.</li><li>완료되면 **공동 작업자 추가**&#x200B;를 클릭하세요.</li> |


