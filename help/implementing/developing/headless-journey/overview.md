---
title: AEM Headless Developer 여정
description: AEM의 강력하고 유연한 헤드리스 기능 및 첫 번째 개발 프로젝트에서 이러한 기능을 활용하는 방법을 통해 안내식 여정을 살펴보십시오.
hide: true
hidefromtoc: true
index: false
exl-id: 4524c92a-8f19-497a-b4f2-c3e23f555d37
source-git-commit: 9e06419f25800199dea92b161bc393e6e9670697
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 1%

---

# AEM Headless 개발자 여정 {#aem-headless-developer-journey}

>[!CAUTION]
>
>오래된 내용 - 이 초안 내용이 새 [헤드리스 개발자 여정 설명서로 대체되었습니다.](/help/journey-headless/developer/overview.md)

AEM의 강력하고 유연한 헤드리스 기능, 그리고 첫 번째 헤드리스 개발 프로젝트에서 이러한 기능을 활용하는 방법을 통해 안내식 여정을 살펴보십시오.

## 소개 {#introduction}

헤드리스 구현은 어디에 있든 채널에 관계없이 고객에게 경험을 전달하는 데 점점 중요해지고 있습니다.

헤드리스 구현은 전체 스택 솔루션에서 일반적으로 페이지 및 구성 요소 관리를 수행하고 채널 중립적이고 재사용 가능한 컨텐츠 조각 및 채널 간 게재에 중점을 둡니다. 웹 경험을 구현하기 위한 현대적이고 동적 개발 패턴입니다.

이 안내서는 가장 중요한 주제를 안내합니다. 따라서 완료 시 다음과 같은 작업을 수행할 수 있습니다.

* 헤드리스 콘텐츠 전달의 정의와 그 이점에 대해 충분히 이해하십시오.
* AEM 헤드리스 기능과 이 기능이 함께 작동하는 방식을 이해하여 헤드리스 경험을 제공합니다.
* 첫 번째 AEM 헤드리스 프로젝트를 구현하는 첫 번째 단계를 수행할 수 있습니다.

## 속성을 확인하는 {#audience}

이 여정은 개발자 관점에서 AEM Headless 프로젝트의 요구 사항, 단계 및 접근 방식을 레이아웃하며 개발자 성향용으로 설계되었습니다. 여정은 성공적인 프로젝트를 위해 개발자가 상호 작용해야 하는 추가 가상 사용자를 정의하지만 여정의 관점은 개발자의 것입니다.

이 여정의 정보는 물론 다른 사용자에게 유용할 수 있지만, 일부 정보는 특정 역할에 유용할 것입니다. 추가적인 역할을 다루는 향후의 여정에 대해 채널을 고정하십시오.

## 헤드리스 개발자 여정 {#the-journey}

이 여정에서 많은 주제를 살펴봅니다. 다음 문서는 AEM의 헤드리스에 대한 기본 지식을 제공하고 자세한 기술 설명서에 연결합니다.

여정의 특정 부분으로 직접 이동할 수 있지만 많은 개념이 이전 문서의 개념에 구축됩니다. 따라서 AEM에서 헤드리스를 처음 사용하는 경우 시작 및 진행 순서로 시작하는 것이 좋습니다.

| # | 기사 | 설명 |
|---|---|---|
| 0 | AEM Headless Developer 여정 | 이 문서 |
| 1 | [CMS Headless 개발에 대해 알아보기](learn-about.md) | 헤드리스 기술 및 사용 시기를 알아봅니다. |
| 2 | [Cloud Service으로 AEM Headless 시작하기](getting-started.md) | AEM Headless 사전 요구 사항에 대해 알아보기 |
| 3 | [AEM Headless를 사용하여 첫 번째 경험의 경로](path-to-first-experience.md) | 개발 환경을 설정하고 간단한 앱을 AEM Headless와 통합하는 방법을 알아봅니다 |
| 4 | [컨텐츠를 모델링하는 방법](model-your-content.md) | 컨텐츠 구조를 모델링하는 방법을 알아봅니다. 그런 다음 컨텐츠 조각 모델 및 컨텐츠 조각을 사용하여 AEM(Adobe Experience Manager)의 구조를 사용하여 여러 채널에서 재사용할 수 있습니다. |
| 5 | [AEM 배달 API를 통해 콘텐츠에 액세스하는 방법](access-your-content.md) | GraphQL 쿼리를 사용하여 컨텐츠 조각 컨텐츠에 액세스하는 방법을 알아봅니다. |
| 6 | [AEM 자산 API를 통해 컨텐츠를 업데이트하는 방법](update-your-content.md) | REST API를 사용하여 컨텐츠 조각 컨텐츠에 액세스하고 업데이트하는 방법을 알아봅니다. |
| 7 | [AEM Headless에서 앱과 컨텐츠를 모두 통합하는 방법](put-it-all-together.md) | 컨텐츠 조각, GraphQL 호출, REST API 호출 및 애플리케이션을 포함하여 AEM 프로젝트를 가져와 라이브로 전환하는 방법을 알아봅니다. |
| 8 | [헤드리스 애플리케이션을 사용하여 라이브로 전환하는 방법](go-live.md) | 애플리케이션을 라이브로 배포하고 Git에서 로컬 코드를 가져와 CI/CD용 Cloud Manager Git 파이프라인으로 이동하는 방법을 알아봅니다. |
| 9 | [선택 사항 - AEM을 사용하여 단일 페이지 애플리케이션(SPA)을 만드는 방법](create-spa.md) | AEM 헤드리스 기능을 이해하면 헤드리스 게재 기능과 헤드리스 게재를 결합하는 방법을 탐색하고 AEM SPA Editor 프레임워크를 사용하여 편집 가능한 SPA을 만드는 방법을 알아봅니다. |

## 다음 기능 {#what-is-next}

이제 Adobe 헤드리스 여정을 시작할 준비가 되었습니다. 여정의 다음 부분으로 계속 이동하여 [CMS Headless Development에 대해 알아봅니다.](learn-about.md)

### 자신만의 모험 선택 {#choose-your-path}

그러나 Adobe은 학습 스타일에 상관없이 AEM Headless 프로젝트를 시작할 때 성공하기를 원합니다. 따라서 이 두 가지 옵션을 고려해 보십시오.

* **헤드리스 개념 및 AEM 헤드리스 기술에 대해 배우려면** 문서를 참조하여 AEM 헤드리스 여정을 계속 진행해야 합니다. [컨텐츠를 AEM 컨텐츠 모델로 모델링하는 방법](model-your-content.md) 문서를 참조하여 AEM에서 컨텐츠 구조를 모델링하는 방법을 배웁니다.
* **을(를) 수행하여 학습하려는 경우 [AEM 헤드리스 실습 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html)로 건너뛸 수 있습니다. 여기서 간단한 프로젝트를 구현하여 AEM 헤드리스 콘텐츠를 노출하도록 AEM Headless 개발에 직접 참여합니다.**
