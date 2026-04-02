---
title: 클릭 한 번으로 첫 Edge Delivery Site 만들기
description: 버튼 클릭만으로 Cloud Manager에서 Edge Delivery Site를 빠르게 만드는 방법에 대해 알아보십시오.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 292bf0b4-990b-4980-b971-91b8aedde3de
source-git-commit: fc9f7f10d1797bda5f31d82005b0afbb6ea1e644
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 64%

---

# 클릭 한 번으로 첫 Edge Delivery Site 만들기{#about-one-click-edge-delivery-site}

원클릭 Edge Delivery Site 만들기 기능은 Cloud Manager 내에서 Edge Delivery Sites의 온보딩 및 배포를 자동화하는 데 도움이 되도록 설계되었습니다. 버튼 하나만 클릭하면 되므로 과정이 크게 간소화됩니다. 클릭 한 번으로 필요한 인프라를 프로비저닝하고, GitHub와 통합하여 버전을 제어하며, Google Drive에서 문서 및 자산 저장소를 구성할 수 있습니다.

이러한 자동화는 초기 사이트를 설정하는 데 필요한 수작업을 줄이는 데 도움이 됩니다. 원활한 워크플로와 확장성을 보장하고 에지에서 콘텐츠를 관리할 때 팀의 성과를 향상시킵니다.

<!-- Check out this quick 2-minute video for a step-by-step walkthrough on creating your first Edge Delivery site—no hassle, just one click.

>[!VIDEO](https://video.tv.adobe.com/v/3458975?quality=12&learn=on) -->



<!--
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

1. [experience.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
   1. **바로 가기** 섹션에서 **Experience Manager**&#x200B;를 클릭합니다.
   1. 왼쪽 사이드 패널에서 **Cloud Manager**&#x200B;를 클릭합니다.
   1. 원하는 조직을 선택합니다.
1. **내 프로그램** 콘솔에서 프로그램을 클릭합니다.
1. 페이지의 왼쪽 상단에서 ![메뉴 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다.
1. 왼쪽 메뉴에서 **프로그램** 제목 아래에 있는 **개요**&#x200B;를 클릭합니다.
1. **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다.
1. Edge Delivery 페이지의 **Edge Delivery 할 일 목록** 대화 상자, **Edge Delivery 사이트 추가** 그룹 상자에서 **지금 사이트 만들기**&#x200B;를 클릭합니다.
1. **Edge Delivery 사이트 만들기** 대화 상자의 **프로젝트 이름** 텍스트 필드에 사이트 이름을 입력합니다.
1. **작성 옵션**&#x200B;에서 다음 중 하나를 선택합니다.
   * **문서 작성** - Google 드라이브 또는 SharePoint에서 콘텐츠를 작성합니다. 이 옵션은 기본값이며 AEM 환경이 필요하지 않습니다.
   * **AEM 작성(Beta)** - 범용 편집기를 사용하여 AEM에서 콘텐츠를 작성합니다. 이 옵션을 선택하는 경우 **템플릿 선택**&#x200B;에서 Edge Delivery 사이트의 초기 템플릿을 선택합니다.

   ![AEM 작성을 선택한 Edge Delivery 사이트 만들기 대화 상자](/help/implementing/cloud-manager/edge-delivery/assets/eds-create-aem-authoring.png)

1. **작성 환경** 드롭다운 목록에서 작성에 사용할 AEM 환경을 선택합니다. 프로그램에 이 환경이 이미 있어야 합니다. 작성 계층만 필요합니다. Edge Delivery이 게재를 처리할 때에는 게시 계층이 필요하지 않습니다. [유연한 게시 계층(Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier)을 참조하십시오.

1. **지금 사이트 만들기**&#x200B;를 클릭합니다.

   화면 상단 중앙에 알림이 나타나 Edge Delivery 사이트 프로비저닝이 시작되었음을 알려 줍니다.

Cloud Manager에서 사이트 프로비저닝 및 검증이 완료되면 **사이트 이름**(이전에 입력한 프로젝트 이름)이 Edge Delivery 페이지의 **Edge Delivery 사이트** 목록 상자에 표시됩니다. 또한 Verified status 열 왼쪽에 녹색 점이 나타납니다.

[AEM 작성자의 콘텐츠를 Edge Delivery에 게시](#publish-from-aem-author)도 참조하십시오.

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
   | Google Drive의 콘텐츠 저장소에 대한 사용자 액세스 권한 부여 | <ul><li> **Edge Delivery 사이트** 목록 상자에서 사이트 이름의 맨 오른쪽에 있는 ![더 보기 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 드롭다운 메뉴를 엽니다.</li><li>드롭다운 메뉴에서 ![사용자 추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_UsersAdd_18_N.svg)을 클릭하여 **콘텐츠 저장소에 대한 액세스 권한 받기**&#x200B;를 선택합니다.</li><li>**`Add collaborators to your site`** 대화 상자에서 기여자의 전자 메일 주소를 입력한 다음 ![확인 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg)을 클릭합니다.</li><li>필요에 따라 참여자 이메일을 계속 추가합니다.</li><li>작업을 완료하면 **공동 작업자 추가**&#x200B;를 클릭합니다.</li><li>콘텐츠 공동 작업자와 링크를 공유하려면 **공동 작업자가 정상적으로 추가됨** 대화 상자에서 **확인**&#x200B;을 클릭합니다.</li><li>공동 작업자가 정상적으로 추가됨 대화 상자에서 ![복사 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)을 클릭하여 링크를 복사한 후 공동 작업자와 공유합니다.<br>링크를 공유하기 전에 공동 작업자가 IMS 계정과 연결된 이메일 주소로 로그인되어 있는지 확인하십시오. IMS 이메일 계정이 사용 불가능한 경우, 공동 작업자로 추가된 이메일 주소를 사용해야 합니다. 이렇게 하면 공동 작업자가 링크에 액세스하여 Google Drive에서 콘텐츠를 편집하거나 업데이트할 수 있습니다.</li><li>편집이 완료되면 위에서 설명한 대로 Cloud Manager에서 **사이트 게시**&#x200B;를 클릭합니다.<br>또는 위에서 설명한 대로 변경 사항을 미리 봅니다.</li></ul> |
   | GitHub의 기본 저장소에 대한 사용자 액세스 권한 부여 | <ul><li> **Edge Delivery 사이트** 목록 상자에서 사이트 이름의 맨 오른쪽에 있는 ![더 보기 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭하여 드롭다운 메뉴를 엽니다.</li><li>드롭다운 메뉴에서 ![코드 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg)을 클릭하여 **기본 저장소에 대한 액세스 권한 받기**&#x200B;를 선택합니다.</li><li>**사이트의 기본 저장소에 액세스** 대화 상자에서 공동 작업자의 GitHub 사용자 이름을 입력한 후 ![체크 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg)을 클릭합니다.</li><li>필요에 따라 GitHub 사용자 이름을 계속 추가합니다.</li><li>작업을 완료하면 **공동 작업자 추가**&#x200B;를 클릭합니다.</li>사용자는 저장소를 보려면 GitHub 사용자 이름에 대한 액세스를 허용해야 합니다. |

## AEM 작성자의 콘텐츠를 Edge Delivery(Beta)에 게시 {#publish-from-aem-author}

>[!NOTE]
>
>여기에 설명된 게시 기능은 Beta에 있습니다. Beta에 가입하려면 Adobe 조직 ID와 프로그램 ID로 [grp-beta_xwalk-publish_config@adobe.com](mailto:grp-beta_xwalk-publish_config@adobe.com)에 전자 메일을 보내십시오.

이 기능은 AEM 작성 옵션으로 만든 Edge Delivery 사이트에만 사용할 수 있습니다.

Edge Delivery 사이트가 만들어지고 Cloud Manager에서 **확인**&#x200B;되면 AEM 유니버설 편집기를 사용하여 콘텐츠를 작성하고 게시할 수 있습니다.

**Cloud Manager에서 유니버설 편집기에 액세스하려면:**

1. Edge Delivery 탭의 Edge Delivery 사이트 목록에서 사이트를 찾습니다.

   ![AEM 작성자의 콘텐츠를 Edge Delivery에 게시](/help/implementing/cloud-manager/edge-delivery/assets/eds-content-source-link.png)

1. 사이트 행에서 **컨텐츠 Source** 링크를 클릭합니다. 이 링크를 클릭하면 AEM 범용 편집기 페이지가 열리고 여기서 사이트의 콘텐츠를 만들고 편집할 수 있습니다.

**콘텐츠를 게시하려면:**

* **Cloud Manager에서** -

   1. **개요** 페이지의 **게재** 탭의 **환경** 카드에서 강조 표시된 ![정보 또는 정보 아이콘](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg)을 클릭합니다.

   1. 정보 팝업에서 **활성화하려면 클릭**&#x200B;을 선택하여 Cloud Manager 사용자 인터페이스에서 게시 계층 프로비저닝을 활성화합니다.

      ![게시 계층 프로비저닝을 활성화하려면 클릭](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/click-to-activate-publish-tier-capabilities.png)

   1. 게시 계층 활성화 대화 상자에서 **활성화**&#x200B;를 클릭합니다.

      ![게시 계층 활성화 대화 상자](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/activate-publish-tier.png)

      활성화되면 게시 계층이 자동으로 프로비저닝됩니다. 또는 작성자가 AEM 사용자 인터페이스에서 직접 콘텐츠를 게시하려고 하는 경우 게시 계층을 자동으로 프로비저닝할 수 있습니다.

      게시 계층이 정상적으로 활성화되고 프로비저닝되면 **활성화하려면 클릭** 링크가 흐리게 표시되거나 사용할 수 없게 됩니다.

* **AEM 작성자로부터** — AEM 작성 인터페이스에서 **빠른 게시**&#x200B;를 클릭하여 콘텐츠를 Edge Delivery 사이트에 직접 게시합니다. Edge Delivery이 게재를 처리할 때 이 작업에는 게시 계층이 필요하지 않습니다.

게시 후 사이트의 `.page` URL에서 콘텐츠를 미리 보거나 `.live` URL에서 실시간으로 볼 수 있습니다.

