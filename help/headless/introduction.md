---
title: AEM Headless 소개
description: Adobe Experience Manager (AEM) 헤드리스 자습 리소스 및 설명서 링크. 컨텐츠 모델, 컨텐츠 조각 및 GraphQL API와 같은 기능을 사용하여 AEM에서 헤드리스 경험을 향상시키는 방법을 알아봅니다.
landing-page-description: 헤드리스 as a Cloud Service Experience Manager을 사용하고 관리하는 방법을 이해합니다.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: c5d67e0ece40cdf7a9009436ec90305fe81425a2
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 2%

---


# Adobe Experience Manager Headless 소개  {#introduction-aem-headless}

컨텐츠 모델, 컨텐츠 조각 및 GraphQL API와 같은 Adobe Experience Manager(AEM)의 기능을 사용하여 헤드리스 경험을 규모에 맞게 향상시키는 방법을 알아봅니다.

## 개요 {#overview}

AEM 헤드리스는 GraphQL을 사용하여 AEM에서 구조화된 컨텐츠(컨텐츠 조각)를 HTTP를 통해 모든 앱에서 사용할 수 있도록 하는 Experience Manager의 CMS 솔루션입니다. 헤드리스 구현을 통해 다양한 플랫폼과 채널에서 경험을 규모에 맞게 전달할 수 있습니다.

헤드리스 구현은 전체 스택 및 하이브리드 솔루션에서 일반적으로 페이지 및 구성 요소 관리를 수행하고 채널 중립적이고 재사용 가능한 컨텐츠 조각 및 채널 간 전달을 만드는 데 중점을 둡니다. 웹 경험을 구현하기 위한 현대적이고 동적 개발 패턴입니다.

![AEM 구현 모델](assets/aem-implementation-models.png)

## AEM 헤드리스의 기능 {#aem-headless-features}

AEM as a Cloud Service 은 세 가지 강력한 기능을 제공하여 헤드리스 구현 모델을 위한 유연한 도구입니다.

1. **컨텐츠 모델**
   * 컨텐츠 모델은 컨텐츠의 구조화된 표현입니다.
   * 컨텐츠 모델은 AEM 컨텐츠 조각 모델 편집기에서 정보 설계자에 의해 정의됩니다.
   * 컨텐츠 모델은 컨텐츠 조각의 기반이 됩니다.
1. **컨텐츠 조각**
   * 컨텐츠 조각은 컨텐츠 모델을 기반으로 만들어집니다.
   * AEM 컨텐츠 조각 편집기를 사용하여 컨텐츠 작성자가 작성합니다.
   * 컨텐츠 조각은 AEM Assets에 저장되고 Assets 관리 UI에서 관리됩니다.
1. **게재용 컨텐츠 API**
   * AEM GraphQL API는 컨텐츠 조각 전달을 지원합니다.
   * AEM Assets REST API는 컨텐츠 조각 CRUD 작업을 지원합니다.
   * 또한 [컨텐츠 조각 코어 구성 요소의 JSON 내보내기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html).

## AEM 헤드리스를 사용한 첫 번째 단계 {#first-steps}

AEM 헤드리스 기능을 시작하는 데 사용할 수 있는 리소스는 몇 가지가 있습니다. 각 안내서는 다양한 사용 사례 및 대상에 맞게 조정됩니다.

| 리소스 | 설명 | 유형 | 속성을 확인하는 | 설정. 시간 |
|---|---|---|---|---|
| [헤드리스 개발자 여정](/help/journey-headless/developer/overview.md) | **AEM을 처음 사용하는 개발자와 헤드리스** 기술, 첫 번째 헤드리스 프로젝트에서 라이브로 진행하면서 헤드리스 이론에서 AEM과 헤드리스 기능에 대한 포괄적인 소개를 위해 여기서 시작하십시오. | 안내서 | 개발자 **AEM 및 헤드리스** | 1시간 |
| [헤드리스 설정](/help/headless/setup/introduction.md) | **숙련된 AEM 사용자** 주요 AEM 헤드리스 기능에 대한 간단한 요약이 필요한 사람은 이 빠른 시작 개요를 참조하십시오. | 참조 설정 | 개발자, 관리자 **AEM 경험 사용** | 20분 |
| [헤드리스 실습 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | **실습 방법을 선호하며 AEM에 익숙하다면**, 이 자습서에서는 간단한 헤드리스 앱 구현에 직접 대해 자세히 설명합니다. | 튜토리얼 | 개발자 | 2시간 |
| [헤드리스 아키텍트 여정](/help/journey-headless/architect/overview.md) | **AEM을 처음 사용하고 헤드리스를 처음 사용하는 설계자의 경우** technologies에서 Adobe Experience Manager as a Cloud Service의 강력하고 유연한 헤드리스 기능과 프로젝트 컨텐츠를 모델링하는 방법을 소개합니다. | 안내서 | 아키텍트 | 1시간 |
| [헤드리스 작성 여정](/help/journey-headless/author/overview.md) | **AEM을 처음 사용하는 비즈니스 사용자 및 헤드리스** technologies에서 Adobe Experience Manager as a Cloud Service의 강력하고 유연한 헤드리스 기능과 프로젝트 컨텐츠를 모델링하는 방법을 소개합니다. | 안내서 | 콘텐츠 작성자 | 1시간 |
| [헤드리스 번역 여정](/help/journey-headless/translation/overview.md) | 해당 **헤드리스에 대한 AEM 번역 접근 방식에 관심**. 헤드리스 기술과 AEM에서 A에서 Z로 번역 프로젝트를 만들고 업데이트하는 방법에 대해 알아봅니다. | 안내서 | 번역 전문가 | 1시간 |

## 헤드리스 및 헤드리스 비교 {#headful-headless}

이 안내서는 AEM의 헤드리스 전체 구현 모델에 중점을 둡니다. 하지만 headful과 headless는 AEM에서 이진 선택이 될 필요가 없습니다. 헤드리스 기능을 사용하여 컨텐츠를 관리하고 여러 터치 포인트에 전달하는 동시에 컨텐츠 작성자가 단일 페이지 애플리케이션을 편집할 수도 있습니다. 모두 AEM에서

>[!TIP]
>
>문서를 참조하십시오 [AEM의 헤드리스 및 헤드리스](/help/implementing/developing/headful-headless.md) 추가 정보.