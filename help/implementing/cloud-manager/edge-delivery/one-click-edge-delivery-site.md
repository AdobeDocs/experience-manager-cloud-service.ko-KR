---
title: Cloud Manager에서 Edge Delivery 사이트 프로비저닝
description: 단추 클릭으로 Cloud Manager에서 Edge Delivery 사이트를 빠르게 만드는 방법에 대해 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ac110fb006ed377403bce52c961712e6e449be88
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 8%

---


# Cloud Manager에서 Edge Delivery 사이트 프로비저닝 기본 정보 {#about-provision-edge-delivery-site}

EDS(One Click Edge Delivery Service)는 Cloud Manager 내에서 Edge Delivery 사이트의 온보딩 및 배포를 자동화하도록 설계되었습니다. 버튼 한 개를 클릭할 수 있어 프로세스가 크게 간소화됩니다. 한 번의 클릭으로 필요한 인프라를 프로비저닝하고, 버전 제어를 위해 GitHub와 통합하며, Google 드라이브에서 문서 및 에셋 스토리지를 구성합니다.

이러한 자동화는 초기 사이트를 설정하는 데 필요한 수작업을 줄이는 데 도움이 됩니다. 따라서 엣지에서 컨텐츠를 관리할 때 원활한 워크플로와 확장성을 보장하고 팀의 성능을 향상시킬 수 있습니다.

## 주요 개념 {#key-concepts}

Edge Delivery 사이트 프로비저닝을 한 번 클릭하는 경우의 주요 개념입니다.

| 주요 개념 | 설명 |
| --- | --- |
| 자동화된 Edge 배포 | <ul><li>사용자는 Edge Delivery 사이트를 즉시 프로비저닝하고 구성할 수 있습니다.</li><li>Cloud Manager과 CI/CD 워크플로우의 통합을 통해 수동 온보딩 프로세스의 필요성을 줄이거나 제거합니다.</li><li>원활한 CI/CD 워크플로우를 위해 Cloud Manager과 통합됩니다.</li></ul> |
| Cloud Manager과 통합 | <ul><li>Cloud Manager의 사용자 인터페이스를 사용하여 One Click Edge Delivery 프로세스를 트리거합니다.</li><li>자동화된 저장소 생성 및 배포에 대한 액세스를 제공합니다.</li></ul> |
| GitHub 기반 버전 제어 | <ul><li>미리 정의된 표준 서식 파일을 사용하여 조직 내에 GitHub 저장소를 생성하여 배포를 표준화합니다.</li><li>콘텐츠 업데이트를 위한 AEM 봇과의 링크.</li></ul> |
| 문서 및 에셋 스토리지 통합 | <ul><li>스토리지용 Google 드라이브 폴더를 생성합니다.<li>저장소에 AEM 코드 동기화 응용 프로그램을 설치하여 원활한 동기화 및 배포를 보장합니다.</li></li><li>여러 공동 작업자가 문서를 쉽게 관리할 수 있습니다.</li></ul> |
| 보안 및 확장성 | <ul><li>엔터프라이즈 보안 표준을 준수하도록 보장합니다.</li><li>는 다양한 Edge Delivery 테넌트에서 여러 Cloud Manager 사이트를 지원합니다.</li></ul> |



## Cloud Manager에서 Edge Delivery 사이트 프로비저닝 {#provision-edge-delivery-site}

한 번의 클릭으로 Adobe Edge 게재 사이트를 프로비저닝하려면 조직에 사용 가능한 Edge Delivery Services 라이선스가 있어야 합니다. 이 라이선스는 Adobe Experience Manager(AEM)의 일부이며 Cloud Manager 내에서 Edge Delivery Services을 프로비저닝하는 데 필요합니다.

권한 측면에서 비즈니스 소유자 역할의 멤버이거나 Cloud Manager에서 프로그램을 추가하거나 편집할 수 있는 적절한 권한이 부여되어야 합니다. 이 액세스 수준을 사용하면 프로그램에 대한 Edge Delivery Services 통합을 관리할 수 있습니다.

[Cloud Manager에서의 Edge Delivery Services 소개](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md)도 참조하십시오.

자동 콘텐츠 업데이트를 위해 먼저 적절한 AEM 보트 구성을 사용해야 합니까? 사실이에요? FALSE?

**Cloud Manager에서 Edge Delivery 사이트를 프로비전하려면:**

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단 모서리에서 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 왼쪽 메뉴를 표시합니다.
1. 왼쪽 메뉴에서 **서비스** 제목 아래의 ![웹 페이지 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery 사이트**&#x200B;를 클릭합니다.
1. Edge Delivery 페이지의 **Edge Delivery 할 일 목록** 대화 상자, **필수 구성 요소 완료** 그룹 상자에서 **프로비저닝**&#x200B;을 클릭합니다.
1. **Edge Delivery 사이트 프로비저닝** 대화 상자의 **프로젝트 이름** 텍스트 필드에 사이트 이름을 입력한 다음 **프로비저닝**을 클릭합니다.
화면 상단 중앙에 Edge Delivery 사이트 프로비저닝이 시작되었음을 알리는 알림이 표시됩니다.
프로비저닝이 완료되고 사이트의 유효성을 검사하면 사이트 이름이 Edge Delivery 페이지의 **Edge Delivery 사이트** 영역에 표시됩니다.

### 새로 제공된 Edge Delivery 사이트 탐색




1. 사이트 이름 오른쪽에 있는 Git 저장소 링크를 클릭합니다.

Publish. 사이트 이름을 클릭하고 일부 변경한 다음 게시합니다

미리보기에서 페이지를 본 다음 라이브 버전을 보려면 URL을 변경하십시오.

공동 작업자를 추가합니다.




## Publish 및 Edge Delivery 사이트



## Edge Delivery 사이트에 공동 작업자 추가


































이러한 개선 사항은 자동화를 개선하고 설정 프로세스를 간소화하며 Edge Delivery Services 사용자의 공동 작업을 강화하는 것을 목표로 합니다. <!-- CMGR-59362 -->

![Edge Delivery 사이트 프로비저닝](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

![Edge Delivery 사이트 대화 상자 프로비저닝](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)