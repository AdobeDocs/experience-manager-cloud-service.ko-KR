---
title: AEM Headless Developer 여정
description: AEM의 강력하고 유연한 헤드리스 기능 및 첫 번째 개발 프로젝트에서 이러한 기능을 활용하는 방법을 통해 안내식 여정을 살펴보십시오.
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
source-git-commit: 387e75faeccb0671a32a54ff0c12f05219844311
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 1%

---

# AEM Headless Developer 여정 {#aem-headless-developer-journey}

AEM의 강력하고 유연한 헤드리스 기능, 그리고 첫 번째 헤드리스 개발 프로젝트에서 이러한 기능을 활용하는 방법을 통해 안내식 여정을 살펴보십시오.

## 소개 {#introduction}

헤드리스 구현은 전체 스택 솔루션에서 일반적으로 페이지 및 구성 요소 관리를 수행하고 채널 중립적이고 재사용 가능한 컨텐츠 조각 및 채널 간 게재에 중점을 둡니다. 디지털 경험을 구현하기 위한 현대적이고 동적 개발 패턴입니다.

이 안내서는 AEM에서 가장 헤드리스 구현 주제를 안내하여 완료되면 다음을 수행할 수 있습니다.

* 헤드리스 콘텐츠 전달의 정의와 그 이점에 대해 충분히 이해하십시오.
* AEM 헤드리스 기능과 이 기능이 함께 작동하는 방식을 이해하여 헤드리스 경험을 제공합니다.
* 첫 번째 AEM 헤드리스 프로젝트를 구현하는 첫 번째 단계를 수행할 수 있습니다.

## AEM 설명서 여정 {#documentation-journeys}

[설명서 ](/help/journey-documentation/home.md) 여정은 AEM에 대해 새로운 지식을 가진 독자가 처음부터 끝까지 비즈니스 문제를 이해하고 해결하는 데 도움이 되는 스토리를 제공함으로써, 많은 다양한 주제 및 복잡한 주제를 함께 연결합니다. 단, 이전 주제나 AEM 지식이 거의 없습니다.

설명서 여정은 Adobe의 최신 연구, Adobe 컨설턴트의 입증된 구현 경험, 고객 프로젝트의 피드백을 통해 우수 사례 원칙을 중심으로 설계되었습니다.

AEM에서 헤드리스 비즈니스 사례를 해결하는 방법을 Adobe이 권장하는 방법을 알아보려면 [AEM 헤드리스 여정](/help/journey-headless/home.md)이 시작되는 위치입니다.

>[!TIP]
>
> **을 수행하여 학습하고 싶고, 기술적으로 경도가 높은 경우에는 API 및 프레임워크로 구성되어 있고 이 문서의 끝에 있는 [추가 리소스 섹션](#additional-resources)에서 사용할 수 있는 AEM Headless 자습서를 방문하십시오.**

## 속성을 확인하는 {#audience}

이 여정은 개발자 관점에서 AEM Headless 프로젝트의 요구 사항, 단계 및 접근 방식을 레이아웃하며 개발자 성향용으로 설계되었습니다. 여정은 성공적인 프로젝트를 위해 개발자가 상호 작용해야 하는 추가 가상 사용자를 정의하지만 여정의 관점은 개발자의 것입니다.

다음은 이 여정에서 상호 작용하는 가상 정보입니다.

| 모습 | 설명 | 이 여정의 역할 |
|---|---|---|
| 개발자(타겟 대상) | 다양한 소스의 컨텐츠를 소비하는 헤드리스 애플리케이션을 개발하는 경험이 있습니다 | 이 여정의 Target 대상 |
| 컨텐츠 작성자 | 헤더없이 전달되는 컨텐츠를 만들고 관리합니다 | 컨텐츠 작성자는 개발자가 헤드리도록 컨텐츠를 만듭니다. |
| 관리자 | AEM의 기본 설정 및 구성을 관리합니다 | 개발자는 관리자와 함께 개발에 필요한 구성을 변경합니다. |
| 컨텐츠 설계자 | 헤드리스 없이 전달해야 하는 데이터에 대한 요구 사항을 분석하고 이 데이터의 구조를 정의합니다 | 개발자는 컨텐츠 설계자와 협력하여 데이터 구조 및 요구 사항을 헤딩 없이 파악합니다. |

이 여정의 정보는 물론 모든 사용자에게 유용할 수 있지만, 일부 정보는 특정 역할에 유용할 수 있습니다. 추가 역할을 다루는 [예정된 여정에 대해 채널을 고정하십시오.](/help/journey-documentation/home.md#journeys)

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
| 6 | [AEM Assets API를 통해 콘텐츠를 업데이트하는 방법](update-your-content.md) | REST API를 사용하여 컨텐츠 조각 컨텐츠에 액세스하고 업데이트하는 방법을 알아봅니다. |
| 7 | [AEM Headless에서 앱과 컨텐츠를 모두 통합하는 방법](put-it-all-together.md) | AEM Headless SDK를 사용하여 AEM 프로젝트를 라이브로 전환하는 방법을 알아봅니다. |
| 8 | [헤드리스 애플리케이션을 사용하여 라이브로 전환하는 방법](go-live.md) | 애플리케이션을 라이브로 배포하고 Git에서 로컬 코드를 가져와 CI/CD용 Cloud Manager Git 파이프라인으로 이동하는 방법을 알아봅니다. |
| 9 | [선택 사항 - AEM을 사용하여 단일 페이지 애플리케이션(SPA)을 만드는 방법](create-spa.md) | AEM 헤드리스 기능을 이해하면 헤드리스 게재 기능과 헤드리스 게재를 결합하는 방법을 탐색하고 AEM SPA Editor 프레임워크를 사용하여 편집 가능한 SPA을 만드는 방법을 알아봅니다. |

## 다음은 무엇입니까? {#what-is-next}

이제 Adobe 헤드리스 여정을 시작할 준비가 되었습니다. 여정의 다음 부분으로 계속 이동하여 [CMS Headless Development에 대해 알아봅니다.](learn-about.md)

### 자신만의 모험 선택 {#choose-your-path}

그러나 Adobe은 학습 스타일에 상관없이 AEM Headless 프로젝트를 시작할 때 성공하기를 원합니다. 따라서 이 두 가지 옵션을 고려해 보십시오.

* **헤드리스 개념 및 AEM 헤드리스 기술에 대해 배우려면** 문서를 참조하여 AEM 헤드리스 여정을 계속 진행해야 합니다. [컨텐츠를 AEM 컨텐츠 모델로 모델링하는 방법](model-your-content.md) 문서를 참조하여 AEM에서 컨텐츠 구조를 모델링하는 방법을 배웁니다.
* **을(를) 수행하여 학습하려는 경우 [AEM 헤드리스 실습 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html)로 건너뛸 수 있습니다. 여기서 간단한 프로젝트를 구현하여 AEM 헤드리스 콘텐츠를 노출하도록 AEM Headless 개발에 직접 참여합니다.**

## 추가 리소스 {#additional-resources}

설명서 여정은 복잡하고 관련된 프로세스와 기능을 안내하는 설명을 제공하여 AEM에서 비즈니스 문제를 해결하는 방법을 보여줍니다. 여정은 단일 비즈니스 요구 사항을 충족하기 위해 여러 기능이 함께 작동하는 방식을 보여줍니다.

이러한 여정은 스스로 설 수 있도록 고안되었습니다. 하지만 그들 중 많은 수가 서로 관련될 수 있습니다. AEM의 강력한 기능이 함께 작동하는 방식에 대한 자세한 내용은 이러한 추가 여정을 참조하십시오.

* [AEM Headless 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)  - 원하는 방식으로 학습하고 기술적인 지식이 있는 경우 AEM Headless에서 구축된 애플리케이션의 제작 및 사용을 탐색하는 API 및 프레임워크로 구성된 실습 위주의 자습서를 받으십시오.
* [AEM 헤드리스 번역 여정](/help/journey-headless/translation/overview.md)  - 이 설명서 여정은 헤드리스 기술, AEM에서 헤드리스 콘텐츠를 제공하는 방법 및 이를 번역할 수 있는 방법에 대한 광범위한 이해를 제공합니다.
* [헤드리스 작성 여정](/help/journey-headless/author/overview.md)  - AEM의 강력하고 유연한 헤드리스 기능 및 첫 번째 헤드리스 프로젝트에서 컨텐츠를 모델링하는 방법을 통해 안내식 여정을 살펴보려면 여기에서 시작하십시오.
* [헤드리스 아키텍트 여정](/help/journey-headless/architect/overview.md)  - Cloud Service 로서의 Adobe Experience Manager의 강력하고 유연하며, 헤드리스 기능을 소개합니다. 또한 프로젝트용 컨텐츠를 모델링하는 방법을 소개합니다.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html)  - AEM 및 헤드리스 기술에 대한 확고한 이해가 있는 경우에는 심층적인 기술 문서를 직접 문의할 수 있습니다.
