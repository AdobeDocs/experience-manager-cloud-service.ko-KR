---
title: AEM Sites as a Cloud Service을 위한 헤드리스 개발
description: 컨텐츠 모델, 컨텐츠 조각 및 GraphQL API와 같은 Cloud Service의 강력한 헤드리스 기능으로서 AEM을 사용하여 경험을 중앙에서 관리하고 여러 채널에서 제공하는 방법을 살펴볼 수 있습니다.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 2%

---


# AEM Sites as a Cloud Service {#headless-development} 헤드리스 개발

컨텐츠 모델, 컨텐츠 조각 및 GraphQL API와 같은 Cloud Service의 강력한 헤드리스 기능으로서 AEM을 사용하여 경험을 중앙에서 관리하고 여러 채널에서 제공하는 방법을 살펴볼 수 있습니다.

## 개요 {#overview}

헤드리스 구현은 어디에 있든 채널에 관계없이 고객에게 경험을 전달하는 데 점점 중요해지고 있습니다.

헤드리스 구현은 전체 스택 및 하이브리드 솔루션에서 일반적으로 페이지 및 구성 요소 관리를 수행하고 채널 중립적이고 재사용 가능한 컨텐츠 조각 및 채널 간 전달을 만드는 데 중점을 둡니다. 웹 경험을 구현하기 위한 현대적이고 동적 개발 패턴입니다.

![AEM 구현 모델](assets/aem-implementation-models.png)

## 헤드리스와 헤드리스 비교 {#headful-headless}

이 문서는 AEM의 헤드리스 전체 구현 모델에 중점을 둡니다. 하지만 headful과 headless는 AEM에서 이진 선택이 될 필요가 없습니다. 헤드리스 기능을 사용하여 콘텐츠를 관리하고 다양한 종단점으로 전달하면서 콘텐츠 작성자가 단일 페이지 애플리케이션을 편집할 수도 있습니다. 모두 AEM에서

>[!TIP]
>
>자세한 내용은 AEM](/help/implementing/developing/headful-headless.md)의 [제목 및 제목 없음 문서를 참조하십시오.

## AEM as a Cloud Service 및 헤드리스 {#aem-headless}

AEM as a Cloud Service은 세 가지 강력한 서비스를 제공하여 헤드리스 구현 모델을 위한 유연한 도구입니다.

1. 컨텐츠 모델
   * 컨텐츠 모델은 컨텐츠의 구조화된 표현입니다.
   * 이는 AEM 컨텐츠 조각 모델 편집기의 정보 설계자에 의해 정의됩니다.
   * 컨텐츠 모델은 컨텐츠 조각의 기반이 됩니다.
1. 콘텐츠 조각
   * 컨텐츠 조각은 컨텐츠 모델을 인스턴스화합니다.
   * 이러한 템플릿은 AEM 컨텐츠 조각 편집기를 사용하여 컨텐츠 작성자가 만듭니다.
   * AEM Assets에 저장되고 Assets 관리 UI에서 관리됩니다.
1. 게재용 컨텐츠 API
   * AEM GraphQL API는 컨텐츠 조각 전달을 지원합니다.
   * AEM Assets REST API는 컨텐츠 조각 CRUD 작업을 지원합니다.
   * 직접 컨텐츠 전달은 [컨텐츠 조각 코어 구성 요소의 JSON 내보내기도 사용할 수 있습니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)

## AEM Headless {#first-steps}를 사용하는 첫 번째 단계

AEM 헤드리스 기능을 시작할 수 있는 리소스는 많습니다. 이 기능은 서로 다른 사용 사례를 위해 작성되었지만, 모두 AEM 헤드리스 기능에 대한 구체적인 개요를 제공합니다.

| 리소스 | 설명 | 유형 | 속성을 확인하는 | 설정. 시간 |
|---|---|---|---|---|
| [헤드리스 개발자 여정](/help/journey-headless/developer/overview.md) | 첫 번째 헤드리스 프로젝트에서 라이브로 전환하여 헤드리스 이론에서 AEM 헤드리스 기능에 대한 포괄적인 개요를 살펴보려면 여기에서 시작하십시오. | 안내서 | 개발자 | 1시간 |
| [헤드리스 시작 안내서](/help/implementing/developing/headless/getting-started/introduction.md) | 주요 AEM 헤드리스 기능에 대한 간단한 요약을 보려면 이 빠른 시작 개요를 확인하십시오. | 빠른 시작 | 개발자, 관리자 | 20분 |
| [AEM Headless 실습 자습서 시작하기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | 실습 방법을 선호하는 경우 이 자습서에서는 간단한 헤드리스 프로젝트를 만들기 위해 직접 자세히 설명합니다. | 자습서 | 개발자 | 2시간 |
