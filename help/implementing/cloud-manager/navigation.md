---
title: Cloud Manager UI 탐색
description: Cloud Manager UI가 구성되는 방식과 프로그램 및 환경을 관리하기 위해 탐색하는 방법을 알아봅니다.
exl-id: 3f3d7631-2bc9-440b-9888-50f6529bcd42
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 76%

---


# Cloud Manager UI 탐색 {#navigation}

Cloud Manager UI가 구성되는 방식과 프로그램 및 환경을 관리하기 위해 탐색하는 방법을 알아봅니다.

Cloud Manager UI는 주로 두 가지 그래픽 인터페이스로 구성됩니다.

* [내 프로그램 콘솔](#my-programs-console)에서는 모든 프로그램을 조회하고 관리할 수 있습니다.
* [프로그램 개요 창](#program-overview)에서는 개별 프로그램의 세부 정보를 확인하고 관리할 수 있습니다.

>[!TIP]
>
>또한 Cloud Manager을 사용하여 AEM as a Cloud Service을 시작하고 실행하는 방법에 대한 전체 개요는 [온보딩 설명서 여정](/help/journey-onboarding/overview.md)을 확인하십시오.

## 내 프로그램 콘솔 {#my-programs-console}

[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인하고 적절한 조직을 선택하면 **내 프로그램** 콘솔이 표시됩니다.

![내 프로그램 콘솔](assets/my-programs-console.png)

내 프로그램 콘솔은 선택한 조직에서 액세스할 수 있는 모든 프로그램에 대한 개요를 제공합니다. 여러 부분으로 구성되어 있습니다.

1. [도구 모음](#toolbars-my-programs-toolbars) - 조직 선택, 알림 및 계정 설정
1. 프로그램의 현재 보기를 토글할 수 있는 탭입니다.
   * **홈** 보기(기본값) - 모든 프로그램의 개요가 포함된 **내 프로그램** 보기 선택
   * [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md)에 액세스하는 **라이선스**.
   * 탭은 기본적으로 닫혀 있으며 [Cloud Manager 헤더](#cloud-manager-header)의 햄버거 메뉴를 사용하여 표시할 수 있습니다.
1. [통계 및 콜 투 액션](#statistics) - 최근 활동 개요
1. [**내 프로그램** 섹션](#my-programs-section) - 사용자의 모든 프로그램에 대한 개요 포함
1. [빠른 링크](#quick-links-section) - 관련 리소스에 쉽게 액세스

>[!TIP]
>
>프로그램에 대한 자세한 내용은 [프로그램 및 프로그램 유형](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) 문서를 참조하십시오.

### 도구 모음 {#my-programs-toolbars}

두 개의 도구 모음이 서로 겹쳐져 있습니다.

#### Cloud Manager 헤더 {#cloud-manager-header}

첫 번째는 Cloud Manager를 탐색할 때 유지되는 Cloud Manager 헤더입니다. 이는 Cloud Manager 프로그램 전체에 적용되는 설정 및 정보에 대한 액세스를 제공하는 앵커입니다.

![Experience Cloud 헤더](assets/experience-cloud-header.png)

1. 햄버거 메뉴를 통해 개별 프로그램의 특정 부분으로 이동하거나 상황에 따라 [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md)와 **[내 프로그램](#my-programs-console)** 콘솔 간에 전환할 수 있는 탭에 액세스할 수 있습니다.
1. Cloud Manager 버튼을 사용하면 Cloud Manager의 어느 위치에 있든 Cloud Manager의 내 프로그램 콘솔로 돌아갑니다.
1. Cloud Manager에 대한 피드백을 Adobe에 제공하려면 피드백 버튼을 탭하거나 클릭합니다.
1. 조직 선택기는 현재 로그인되어 있는 조직(이 예에서는 Foundation Internal)을 표시합니다. Adobe ID가 여러 조직과 연결된 경우 탭하거나 클릭하여 다른 조직으로 전환합니다.
1. 솔루션 전환기를 탭하거나 클릭하면 다른 Experience Cloud 솔루션으로 빠르게 이동할 수 있습니다.
1. 도움말 아이콘은 학습 및 지원 리소스에 대한 바로 가기를 제공합니다.
1. 알림 아이콘에 현재 할당된 미완료 [알림](/help/implementing/cloud-manager/notifications.md) 수가 배지로 표시되어 있습니다.
1. 사용자를 나타내는 아이콘을 선택하여 사용자 설정에 액세스합니다. 사용자 사진을 구성하지 않은 경우, 아이콘이 임의로 할당됩니다.

#### 프로그램 도구 모음 {#program-toolbar}

프로그램 도구 모음은 Cloud Manager 프로그램과 상황에 적합한 작업 간을 전환할 수 있는 링크를 제공합니다.

![프로그램 도구 모음](assets/program-toolbar.png)

1. 프로그램 선택기는 다른 프로그램을 빠르게 선택하거나 새 프로그램 만들기와 같이 상황에 맞는 작업을 수행할 수 있는 드롭다운을 엽니다.
1. 시작하기 링크를 통해 [온보딩 설명서 여정](/help/journey-onboarding/overview.md)에 액세스하여 Cloud Manager를 시작하고 실행할 수 있습니다.
1. 액션 버튼으로 새 프로그램 만들기와 같이 상황에 맞는 액션을 수행할 수 있습니다.

### 통계 및 콜 투 액션 {#statistics}

통계 및 콜 투 액션 섹션은 조직에 대한 집계 데이터를 제공합니다. 예를 들어 프로그램을 성공적으로 설정한 경우 지난 90일 동안의 활동 통계가 다음을 포함하여 표시될 수 있습니다.

* [배포](/help/implementing/cloud-manager/deploy-code.md) 수
* 식별된 [코드 품질 문제](/help/implementing/cloud-manager/code-quality-testing.md) 수
* 빌드 수

또는 조직 설정을 이제 막 시작하는 경우 다음 단계 또는 설명서 리소스에 대한 팁이 있을 수 있습니다.

### 내 프로그램 섹션 {#my-programs-section}

**내 프로그램** 콘솔의 기본 콘텐츠는 **내 프로그램** 섹션의 프로그램 목록입니다.

**내 프로그램** 섹션에는 각 프로그램을 나타내는 카드가 나열됩니다. 프로그램에 대한 자세한 내용을 보려면 카드를 탭하거나 클릭하여 프로그램의 **프로그램 개요** 페이지에 액세스합니다.

>[!NOTE]
>
>권한에 따라서는 특정 프로그램을 선택하지 못할 수도 있습니다.

정렬 옵션을 사용하여 필요한 프로그램을 더 효과적으로 찾을 수 있습니다.

![정렬 옵션](/help/implementing/cloud-manager/assets/my-programs-sorting.png)

* 정렬 기준
   * 만든 날짜(기본값)
   * 프로그램 이름
   * 상태
* 오름차순(기본값)/내림차순
* 그리드 보기(기본값)
* 목록 보기

#### 프로그램 카드 {#program-cards}

모든 프로그램은 카드(또는 표의 행)로 표시되어 프로그램 개요, 그리고 조치를 취할 수 있는 빠른 링크를 제공합니다.

![프로그램 카드](assets/program-card.png)

* 프로그램 이미지(구성된 경우)
* 프로그램 이름
* 서비스 유형:
   * AEM as a Cloud Service 프로그램용 **Experience Manager 클라우드**
   * [AMS 프로그램](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/introduction)에 대한 **Experience Manager**
* [프로그램 형식](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md):
   * 샌드박스
   * 프로덕션
* 상태
* 구성된 솔루션
* 생성일

프로그램을 만들 때 선택한 옵션에 따라 프로덕션 프로그램에 배지를 지정하여 추가 기능을 표시할 수 있습니다.

* [HIPAA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

  ![HIPAA 배지](assets/hipaa.png)

* [WAF-DDOS 보호](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security)

  ![WAF-DDOS 배지](assets/waf-ddos-protection.png)

* [99.99% SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)

  ![99.99% SLA 배지](assets/9999-sla.png)

정보 아이콘을 사용하면 프로그램에 대한 추가 정보에 빠르게 액세스할 수 있습니다(목록 보기에서 유용함).

![정보](assets/information-list-view.png)

줄임표 아이콘을 사용하면 프로그램에서 수행할 수 있는 추가 작업에 액세스할 수 있습니다.

![프로그램의 줄임표 버튼](assets/program-ellipsis.png)

* 프로그램의 특정 [환경](/help/implementing/cloud-manager/manage-environments.md)으로 이동
* [프로그램 개요](#program-overview) 열기
* [프로그램 편집](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#editing)
* [샌드박스 프로그램 삭제](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#delete-sandbox-program)

>[!TIP]
>
>프로그램 및 프로그램 만들기 및 관리에 대한 자세한 내용은 다음 문서를 참조하십시오.
>
>* [프로그램 및 프로그램 유형](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
>* [샌드박스 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)
>* [프로덕션 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

### 빠른 링크 섹션 {#quick-links-section}

빠른 링크 섹션을 통해 일반적으로 사용되는 관련 리소스에 액세스할 수 있습니다.

## 프로그램 개요 창 {#program-overview}

**[내 프로그램](#my-programs-console)** 콘솔에서 프로그램을 선택하면 **프로그램 개요** 창으로 이동합니다.

![프로그램 개요](assets/program-overview.png)

프로그램 개요를 통해 Cloud Manager 프로그램의 모든 세부 정보에 액세스할 수 있습니다. **내 프로그램** 콘솔과 마찬가지로 여러 부분으로 구성됩니다.

1. [도구 모음](#program-overview-toolbar) - 내 프로그램 콘솔로 빠르게 돌아가고 프로그램 탐색
1. [탭](#program-tabs) - 프로그램의 다양한 측면 간 전환
1. [콜 투 액션](#cta) - 프로그램의 마지막 작업에 기반
1. [환경 개요](#environments) - 프로그램의 환경 개요
1. [파이프라인 개요](#pipelines) - 프로그램의 파이프라인 개요
1. 프로그램의 [성능 개요](#performance)
1. [유용한 리소스](#useful-resources) - 유용한 리소스 링크

### 도구 모음 {#program-overview-toolbar}

프로그램 개요의 도구 모음은 [내 프로그램 콘솔](#my-programs-toolbars)의 도구 모음과 비슷합니다. 여기서는 차이점만 설명합니다.

#### Cloud Manager 헤더 {#cloud-manager-header-2}

Cloud Manager 헤더에는 프로그램 개요의 탐색 가능한 탭을 표시하기 위해 자동으로 열리는 햄버거 메뉴가 있습니다.

![Cloud Manager 햄버거 메뉴](assets/cloud-manager-hamburger.png)

탭을 숨기려면 햄버거 메뉴 아이콘을 탭하거나 클릭합니다.

#### 프로그램 도구 모음 {#program-toolbar-2}

프로그램 도구 모음을 사용하면 다른 프로그램으로 빠르게 전환할 수 있을 뿐만 아니라 프로그램 추가 및 편집과 같이 상황에 맞는 작업에 액세스할 수도 있습니다.

![프로그램 도구 모음](assets/cloud-manager-program-toolbar.png)

또한 햄버거 메뉴를 사용하여 탭을 숨긴 경우 도구 모음은 항상 현재 있는 탭을 표시합니다.

### 프로그램 탭 {#program-tabs}

각 프로그램에는 이와 관련된 많은 옵션과 데이터가 있습니다. 이러한 데이터는 탭으로 모여 있어 프로그램을 탐색하기가 더 쉽습니다. 탭을 통해 다음 항목에 액세스할 수 있습니다.

* 개요 - 현재 문서에 설명된 프로그램 개요
* [활동](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity) - 프로그램의 파이프라인 실행 기록
* [파이프라인](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines) - 프로그램에 대해 구성된 모든 파이프라인
* [저장소](/help/implementing/cloud-manager/managing-code/managing-repositories.md) - 프로그램에 대해 구성된 모든 저장소
* [보고서](/help/implementing/cloud-manager/sla-reporting.md) - SLA 데이터 등의 지표
* [환경](/help/implementing/cloud-manager/manage-environments.md) - 프로그램에 대해 구성된 모든 환경
* [도메인 설정](/help/implementing/cloud-manager/custom-domain-names/introduction.md) - 프로그램의 사용자 지정 도메인 이름 관리
* [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) - 프로그램에 대한 SSL 인증서 관리
* [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) - 특정 IP 주소에 대한 허용 목록 정의
* [콘텐츠 세트](/help/implementing/developing/tools/content-copy.md) - 복사 목적으로 만들어진 콘텐츠 세트
* [콘텐츠 복사 활동](/help/implementing/developing/tools/content-copy.md) - 콘텐츠 복사 활동
* [네트워크 인프라](/help/security/configuring-advanced-networking.md) - 프로그램의 고급 네트워킹 옵션 관리
* 학습 경로 - Cloud Manager의 추가 학습 리소스

기본적으로 프로그램을 열면 **개요** 탭이 표시됩니다. 현재 탭이 강조 표시됩니다. 세부 정보를 보려면 다른 탭을 선택합니다.

탭을 숨기려면 [Cloud Manager 헤더](#cloud-manager-header-2)의 햄버거 메뉴를 사용합니다.

### 콜 투 액션 {#cta}

콜 투 액션 섹션에서는 프로그램 상태에 따라 유용한 정보를 제공합니다. 새 프로그램의 경우 다음 단계 및 Go-Live 날짜 알림 메시지가 표시될 수 있습니다. [프로그램 생성 중 설정](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).

![새 프로그램에 대한 클릭 유도 문안](/help/implementing/cloud-manager/assets/info-banner-new-program.png)

라이브 상태인 프로그램의 경우, 세부 정보 및 새 배포 시작 링크가 포함된 마지막 배포 상태입니다.

![콜 투 액션](/help/implementing/cloud-manager/assets/info-banner.png)

### 환경 카드 {#environments}

**환경** 카드는 환경에 대한 개요와 빠른 작업을 위한 링크를 제공합니다.

**환경** 카드에는 세 가지 환경만 나열됩니다. 프로그램의 모든 환경을 보려면 **모두 표시**&#x200B;를 클릭합니다.

환경을 관리하는 방법에 대한 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md) 문서를 참조하십시오.

### 파이프라인 카드 {#pipelines}

**파이프라인** 카드는 파이프라인에 대한 개요와 빠른 작업을 위한 링크를 제공합니다.

**파이프라인** 카드에는 세 가지 파이프라인만 나열됩니다. 프로그램의 모든 파이프라인을 보려면 **모두 표시**&#x200B;를 클릭합니다.

파이프라인을 관리하는 방법에 대한 자세한 내용은 [파이프라인 관리](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) 문서를 참조하십시오.

### 성능 카드 {#performance}

**성능** 카드는 **[CDN 대시보드](/help/implementing/cloud-manager/cdn-performance.md)**&#x200B;에 대한 개요를 제공합니다.

![성능 카드](/help/implementing/cloud-manager/assets/cdn-performance-dashboard.png)

### 유용한 리소스 {#useful-resources}

**유용한 리소스** 섹션에서는 Cloud Manager의 추가 학습 리소스에 대한 링크를 제공합니다.
