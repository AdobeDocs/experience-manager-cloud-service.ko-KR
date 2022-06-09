---
title: 라이선스 대시보드
description: Cloud Manager는 조직 또는 임차인이 사용할 수 있는 AEMaaCS 제품 권한을 쉽게 볼 수 있는 대시보드를 제공합니다.
source-git-commit: 82b4a4c8da9f42de08c19eb3caf25ff3a1bad4d4
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 1%

---


# 라이선스 대시보드 {#license-dashboard}

Cloud Manager는 조직 또는 임차인이 사용할 수 있는 AEMaaCS 제품 권한을 쉽게 볼 수 있는 대시보드를 제공합니다.

## 개요 {#overview}

Cloud Manager 라이선스 대시보드는 다음 정보에 쉽게 액세스할 수 있습니다.

1. 사용 항목 및 사용 가능한 항목을 포함하여 모든 프로그램에서 사용할 수 있는 솔루션 권한
1. 사이트 솔루션에 대한 월별 트렌드 컨텐츠 요청 사용량 지표

## 라이선스 대시보드 사용 {#using-dashboard}

라이선스 대시보드에 액세스하려면 다음 단계를 따르십시오.

>[!NOTE]
>
>의 사용자 **비즈니스 소유자** 라이선스 대시보드를 보려면 역할을 로그인해야 합니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직을 선택합니다.

1. 제품 개요 페이지에서 **라이선스** 탭.

![라이선스 대시보드](assets/license-dashboard.png)

대시보드는 다음과 같은 세 개의 섹션으로 나누어져 있습니다.

* **솔루션** - 이 섹션에서는 사이트 또는 자산과 같이 라이선스를 부여한 솔루션을 요약합니다.
* **추가 기능** - 이 섹션에서는 사용 가능한 라이센스 솔루션에 대한 추가 기능을 요약합니다.
* **샌드박스 및 개발 환경** - 이 섹션에서는 사용 가능한 환경을 요약합니다.

각 섹션에는 사용 가능한 내용과 사용 가능한 방법이 요약되어 있습니다(있는 경우). 현재 다른 솔루션이 테넌트에 있는 경우에도 사이트 솔루션만 표시됩니다.

* 다음 **상태** 열에는 임차인에 대해 사용할 수 있는 총 이용 권한과 사용하지 않은 권한 수가 표시됩니다.
* 다음 **구성됨** 열은 솔루션 권한이 적용된 프로그램을 나타냅니다.
   * 자격 부여는 프로덕션 환경이 생성된 경우에만 사용되거나, 업데이트 파이프라인이 실행된 경우 이미 있는 것으로 간주됩니다.
* 다음 **사용** 열에는 지난 12개월 동안 소비한 컨텐츠 요청이 클릭 시 그래프로 표시됩니다.

>[!TIP]
>
>을(를) 참조하십시오. [Admin Console 개요](https://helpx.adobe.com/enterprise/using/admin-console.html) Admin Console에서 전체 조직에서 Adobe 자격을 관리하는 방법을 알아봅니다.

## FAQ {#faq}

### 콘텐츠 요청이란 무엇입니까? {#what-is-a-content-request}

콘텐츠 요청은 AEM Sites 또는 콘텐츠 전달 네트워크와 같이 고객이 제공하는 캐싱 시스템에 오는 요청이며, 콘텐츠 또는 데이터를 HTML 형식으로 페이지 보기 또는 API 호출로 JSON 형식으로 게재하도록 합니다.

하나의 콘텐츠 요청은 각 페이지 보기 또는 5개의 API 호출마다 계산되며, 첫 번째 캐싱 시스템의 수신에서 측정됩니다.

컨텐츠 요청은 제품 및 서비스를 제공하는 유일한 목적으로 Adobe을 대신하여 또는 가 시작한 요청이나 활동을 제외합니다. 일반적인 검색 엔진 및 소셜 미디어 서비스와 관련된 보트, 크롤러 및 스파이더에서 Adobe 식별된 사용자 에이전트 트래픽도 제외됩니다.

### Adobe Experience Manager은 콘텐츠 요청을 어떻게 측정합니까? {#how-are-content-requests-measured}

컨텐츠 요청은 Cloud Service 내에서 서버측에서 추적됩니다. AEM에 내장된 CDN은 유효한 HTML 및 JSON 요청을 as a Cloud Service으로 추적합니다. AEM에는 검색 색인 또는 서비스를 새로 고치기 위해 정기적으로 사이트를 방문하는 알려진 서비스를 포함하여 잘 알려진 보트가 제외되는 규칙도 있습니다.

다음은 제외된 잘 알려진 서비스의 비완전한 예입니다.

* AddSearchBot
* ArefsBot
* Applebot
* Jeeves Corporate Spider에게 묻기
* 빙보트
* BingPreview
* BLEXBot
* BuildWith
* Bytepider
* 크롤러켄고
* Facebook Externalhit
* Google AdsBot
* Google AdsBot Mobile

### Analytics 보고서에 AEM 컨텐츠 요청과 다른 결과가 표시되는 이유는 무엇입니까? {#why-are-reports-different}

컨텐츠 요청에는 이 표에 요약된 대로 조직의 Analytics 보고 도구와 차이가 있습니다.

| 분산 이유 | 설명 |
|---|---|
| 태깅 | AEM 컨텐츠 요청으로 추적되는 모든 페이지는 Analytics 추적으로 태그가 지정되거나 지정되지 않을 수 있습니다.<br>AEM 컨텐츠 요청으로 추적되는 모든 API 호출은 조직의 Analytics 도구에서 태깅하지 않습니다.<br>페이지 또는 API 호출에 태그를 지정하여 보기 대신 작업을 추적할 수 있습니다. |
| Tag Management 규칙 | 태그 관리 규칙 설정으로 인해 페이지에 다양한 데이터 수집 구성이 생성되어 컨텐츠 요청 추적과 불일치가 일부 조합될 수 있습니다. |
| 보트 수 | AEM에서 미리 식별하거나 제거하지 않은 알 수 없는 보트는 추적 불일치를 초래할 수 있습니다. |
| 보고서 세트 | 동일한 AEM 인스턴스 및 도메인에 속하는 페이지는 데이터를 다른 Analytics 보고서 세트에 보낼 수 있습니다. |
| 타사 모니터링 및 보안 도구 | 모니터링 및 보안 검색 도구는 Analytics 보고서에서 추적되지 않은 AEM에 대한 컨텐츠 요청을 생성할 수 있습니다. |
| 요청 미리 가져오기 | 미리 가져오기 서비스를 사용하여 페이지를 미리 로드하여 속도를 높이면 콘텐츠 요청 트래픽이 크게 증가할 수 있습니다. |
| DDOS | Adobe은 DDOS 공격에서 트래픽을 자동으로 감지하고 필터링하기 위해 모든 노력을 하지만 가능한 모든 DDOS 공격이 탐지된다는 보장은 없습니다. |

### 내 CDN을 사용하는 경우 어떻게 합니까? {#using-own-cdn}

Cloud Manager의 컨텐츠 요청 대시보드는 자신의 CDN에 대한 추적을 표시하지 않습니다.
