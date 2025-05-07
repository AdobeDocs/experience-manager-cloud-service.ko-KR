---
title: 라이선스 대시보드
description: Cloud Manager는 조직 또는 테넌트가 사용할 수 있는 AEMaaCS 제품 권한을 쉽게 볼 수 있도록 대시보드를 제공합니다.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: e25e337e4b71ed6c0d15bddcb306be243d970501
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 23%

---


# 라이선스 대시보드 {#license-dashboard}

Cloud Manager는 조직 또는 테넌트가 사용할 수 있는 AEMaaCS 제품 권한을 쉽게 볼 수 있도록 대시보드를 제공합니다.

>[!IMPORTANT]
>
>라이선스 대시보드는 AEM as a Cloud Service 프로그램에만 적용됩니다. [AMS 프로그램](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-manager/content/introduction)이 라이선스 대시보드에 포함되어 있지 않습니다.
>
>프로그램에 있는 서비스 유형(AMS 또는 AEMaaCS)을 확인하려면 [Cloud Manager UI 탐색](/help/implementing/cloud-manager/navigation.md#program-cards)을 참조하십시오.

## 개요 {#overview}

Cloud Manager 라이선스 대시보드를 사용하면 사용 가능한 항목 및 사용 가능한 항목을 포함하여 모든 프로그램에서 사용할 수 있는 솔루션 권한에 쉽게 액세스할 수 있습니다. Sites 솔루션에 대한 월별 트렌드가 있는 콘텐츠 요청 사용량 지표.

## 라이선스 대시보드 액세스 {#using-dashboard}

>[!NOTE]
>
>라이선스 대시보드를 보려면 **비즈니스 소유자** 역할의 사용자가 로그인해야 합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 [Cloud Manager 헤더](/help/implementing/cloud-manager/navigation.md#cloud-manager-header)의 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭합니다. 이 작업을 수행하면 탭이 표시됩니다.
1. 탭에서 **라이선스** 옵션을 클릭합니다.

![라이선스 대시보드](assets/license-dashboard.png)

대시보드는 다음을 표시하는 세 섹션으로 나뉩니다.

* **솔루션** - 라이선스가 부여된 솔루션.
* **추가 기능** - 사용 허가된 솔루션에 대한 추가 기능.
* **기타 권한** - 테넌트 내에서 사용할 수 있는 샌드박스 및 개발 환경 및 기타 권한.

각 섹션에는 사용 가능한 항목과 사용 방법이 요약되어 있습니다. 현재 테넌트에 다른 솔루션이 있는 경우에도 Sites 및 Assets 솔루션만 표시됩니다.

* **상태** 열에는 사용되지 않은 권한 수와 테넌트가 사용할 수 있는 총 권한 수가 표시됩니다.
* **구성** 열은 솔루션 권한이 적용된 프로그램을 나타냅니다.
   * 권한은 프로덕션 환경이 생성된 경우에만 사용된 것으로 간주됩니다. 또는 업데이트 파이프라인이 있는 경우 해당 파이프라인에서 실행된 것입니다.
   * 제한된 수의 프로그램만 열에 개별적으로 나열되며 나머지는 `+x` 항목으로 표시됩니다.
   * `+x` 항목 위로 마우스를 가져가면 모든 프로그램에 대한 세부 정보가 포함된 팝업이 표시됩니다.
* **사용량** 열에는 솔루션에 대한 사용량 통계를 표시하는 **[사용량 세부 정보 보기](#view-usage-details)** 단추가 표시됩니다.

>[!TIP]
>
>Admin Console에서 전체 조직의 Adobe 권한을 관리하는 방법을 알아보려면 [Admin Console 개요](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)를 참조하십시오.

## 사용 세부 정보 보기 {#view-usage-details}

<!--
The **View usage details** button gives access to the chosen solution's **Usage Details** window. This window gives a detailed breakdown including charts to show your solution's usage. How that usage is measured depends on the chosen solution. -->

Cloud Manager의 라이선스 영역에 있는 **사용 세부 정보 보기** 단추는 현재 리소스 사용에 대한 자세한 분석을 제공합니다. 클릭하면 라이선스와 관련된 중요한 지표를 보여 주는 보고서나 대시보드가 열립니다. <!-- ADD THIS SENTENCE IF ASSETS USAGE DETAILS GETS REINSTATED ", such as the number of users, storage consumption, or bandwidth usage, depending on the type of services you're using." --> 이 기능을 사용하면 더 나은 리소스 계획 및 최적화를 위한 통찰력을 제공하는 동시에 계약 한도 내에서 모니터링하고 유지할 수 있습니다.

### Sites 사용량 세부 정보 {#sites-usage-details}

**사이트 사용 세부 정보** 창에는 [콘텐츠 요청](#what-is-a-content-request)을 기반으로 사이트 라이선스 사용에 대한 개요를 보여주는 그래프가 표시됩니다.

![사이트 사용 세부 정보 창](assets/sites-usage-details.png)

창 왼쪽에는 **계약 연도 보기** 드롭다운에서 선택한 계약 연도의 계약 분석을 보여주는 파이 차트가 표시됩니다.

창의 오른쪽에는 선택한 계약 연도의 시간 경과에 따라 프로그램별로 분류된 사용량을 보여주는 영역 차트가 표시됩니다. 마우스로 가리키면 선택한 시점의 프로그램당 세부 정보가 포함된 팝업이 표시됩니다.

<!-- REMOVED AS PER CQDOC-21983
### Assets usage details {#assets-usage-details}

The **Assets usage details** window, presents graphs giving an overview of the usage of your Assets licenses based on [storage](#storage) and [standard users](#standard-users). Select the appropriate tab to toggle between the views.

For both storage and standard users views, you can use the **Environment Type** dropdown to toggle the view between production, stage, and development environments.

#### Storage {#storage}

![Assets usage details window for storage](assets/assets-usage-details-storage.png)

The left side of the window presents a pie chart showing the contract breakdown for the contract year selected in the **View contract year** dropdown.

The right side of the window presents an area chart showing the usage broken down by program over time for the selected contract year. A hover reveals a popup with details per program for the selected point in time.

#### Standard Users {#standard-users}

![Assets usage details window for standard-users](assets/assets-usage-details-standard-users.png)

The left side of the window presents a pie chart showing the contract breakdown for the contract year selected in the **View contract year** dropdown.

The right side of the window presents an area chart showing the usage broken down by program over time for the selected contract year. A hover reveals a popup with details per program for the selected point in time. -->

## 자주 묻는 질문 {#faq}

+++**콘텐츠 요청이란?**{#what-is-a-content-request}

콘텐츠 요청은 AEM Sites 또는 콘텐츠 전달 네트워크와 같은 고객 제공 캐싱 시스템으로 전달되는 모든 요청입니다. 페이지 조회수를 위해 HTML 형식의 콘텐츠나 데이터를 검색합니다. 또는 API 호출을 위해 JSON 형식으로 표시.

콘텐츠 요청은 각 페이지 보기 또는 5개의 API 호출마다 계산되며, 콘텐츠 요청을 수신하기 위한 첫 번째 캐싱 시스템의 인그레스에서 측정됩니다. 콘텐츠 요청은 프로덕션 환경에 대해서만 계산됩니다.

콘텐츠 요청은 제품 및 서비스 제공의 유일한 목적으로 Adobe에 의해 또는 이를 대신하여 시작된 요청 또는 활동을 제외합니다. 일반 검색 엔진 및 소셜 미디어 서비스와 관련된 봇, 크롤러 및 스파이더의 Adobe 식별 사용자 에이전트 트래픽도 제외됩니다.

[Cloud Service 콘텐츠 요청 이해](/help/implementing/cloud-manager/content-requests.md)도 참조하세요.
+++

+++**Adobe Experience Manager은 콘텐츠 요청을 어떻게 측정합니까?**{#how-are-content-requests-measured}

콘텐츠 요청은 AEM as a Cloud Service의 에지 서버에서 추적됩니다. 원본 트래픽은 콘텐츠 요청에 포함되지 않습니다. AEM as a Cloud Service에 내장된 CDN은 유효한 HTML 및 JSON 요청을 추적합니다.

또한 AEM에는 검색 인덱스나 서비스를 새로 고치기 위해 사이트를 정기적으로 방문하는 잘 알려진 서비스를 포함하여 잘 알려진 봇을 제외하는 규칙이 있습니다.

[Cloud Service 콘텐츠 요청 이해](/help/implementing/cloud-manager/content-requests.md)도 참조하세요.
+++

+++**Analytics 보고서에 AEM 콘텐츠 요청과 다른 결과가 표시되는 이유는 무엇입니까?**{#why-are-reports-different}

콘텐츠 요청은 조직의 Analytics 보고 도구와 차이가 있을 수 있습니다. 자세한 내용은 [Cloud Service 콘텐츠 요청 이해](/help/implementing/cloud-manager/content-requests.md)를 참조하십시오.
+++

+++**콘텐츠 요청 볼륨에 대해 자세히 알아보려면 어떻게 해야 합니까?**{#current-request-volumes}

라이선스 대시보드에 표시된 콘텐츠 요청 볼륨에 대한 추가 통찰력을 원하는 경우 Adobe 팀이 콘텐츠 요청의 상위 볼륨 드라이버를 보여주는 보고서를 제공할 수 있습니다. 최상위 사용 보고서를 요청하려면 Adobe 팀 또는 Adobe 고객 지원 센터에 문의하십시오.
+++

+++**내 CDN을 사용하는 경우 어떻게 합니까?**{#using-own-cdn}

라이선스 대시보드에는 Cloud Service CDN에서 추적한 데이터만 표시됩니다. 자체 CDN(BYOCDN)을 가져오기로 선택한 경우 계약에 명시된 대로 연간 기준으로 컨텐츠 요청 볼륨을 Adobe에 다시 보고합니다.
+++

