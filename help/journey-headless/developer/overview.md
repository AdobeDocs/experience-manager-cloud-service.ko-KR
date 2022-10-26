---
title: AEM Headless CMS Developer 여정
description: Adobe Experience Manager (AEM)을 Headless CMS로 사용하여 헤드리스 개발에 대해 알아봅니다. 컨텐츠 모델, 컨텐츠 조각 및 GraphQL API와 같은 기능을 사용하여 헤드리스 컨텐츠 전달을 수행하는 방법을 알아봅니다.
landing-page-description: 헤드리스 컨텐츠 전달 및 구현에 대한 이해를 얻습니다. 비즈니스 내에서 전략을 개발하는 방법에 대해 자세히 알아보십시오.
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
source-git-commit: 06aec2fa43db2393416dd5efab886d9c301ffdb2
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 16%

---

# AEM Headless CMS Developer 여정 {#aem-headless-developer-journey}

Adobe Experience Manager 헤드리스 CMS를 처음 사용하는 개발자를 위한 설명서를 시작합니다.!

강력하고 유연한 헤드리스 기능, 그리고 첫 번째 헤드리스 개발 프로젝트에서 이러한 기능을 활용하는 방법에 대해 알아볼 수 있습니다. 이 여정은 첫 번째 헤드리스 애플리케이션을 개발하는 데 필요한 모든 정보를 제공합니다.

## 소개 {#introduction}

AEM의 헤드리스 구현에서는 컨텐츠 조각 모델 및 컨텐츠 조각을 사용하여 구조화된 채널 중립적이고 재사용 가능한 컨텐츠 조각 및 크로스 채널 게재를 만드는 데 중점을 둡니다. 이를 위해서는 전체 스택 솔루션에서 일반적으로 페이지 및 구성 요소 관리를 수행하는 것이 좋습니다. 디지털 경험을 구현하기 위한 현대적이고 동적 개발 패턴입니다.

이 안내서에서는 AEM의 헤드리스 구현 주제를 안내합니다. 따라서 작업이 완료되면 다음 작업을 수행할 수 있습니다.

* 헤드리스 콘텐츠 전달의 정의와 그 이점에 대해 충분히 이해하십시오.
* AEM 헤드리스 기능과 이 기능이 함께 작동하는 방식을 이해하여 헤드리스 경험을 제공합니다.
* 첫 번째 AEM 헤드리스 프로젝트를 구현하는 첫 번째 단계를 수행할 수 있습니다.

>[!TIP]
>
> 원하는 경우 **다음을 통해 학습** AEM에 대한 기존 지식을 가지고 있는 경우 API 및 프레임워크로 구성되어 있고 [추가 리소스 섹션](#additional-resources) 이 문서의 끝 부분.

## 대상자 {#audience}

이 여정은 개발자 관점에서 AEM Headless 프로젝트의 요구 사항, 단계 및 접근 방식을 레이아웃하며 개발자 성향용으로 설계되었습니다. 여정은 성공적인 프로젝트를 위해 개발자가 상호 작용해야 하는 추가 가상 사용자를 정의하지만 여정의 관점은 개발자의 것입니다.

다음은 이 여정에서 상호 작용하는 담당자입니다.

| 담당자 | 설명 | 이 여정의 역할 |
|---|---|---|
| 개발자(타겟 대상) | 다양한 소스의 컨텐츠를 소비하는 헤드리스 애플리케이션을 개발하는 경험이 있습니다 | 이 여정의 Target 대상 |
| 콘텐츠 작성자 | 헤더없이 전달되는 컨텐츠를 만들고 관리합니다 | 컨텐츠 작성자는 개발자가 헤드리도록 컨텐츠를 만듭니다. |
| 관리자 | AEM의 기본 설정 및 구성 관리 | 개발자는 관리자와 함께 개발에 필요한 구성을 변경합니다. |
| 콘텐츠 설계자 | 헤드리스 없이 전달해야 하는 데이터에 대한 요구 사항을 분석하고 이 데이터의 구조를 정의합니다 | 개발자는 컨텐츠 설계자와 협력하여 데이터 구조 및 요구 사항을 헤딩 없이 파악합니다. |

## 헤드리스 개발자 여정 {#the-journey}

AEM에서 헤드리스에 대한 기본 지식을 제공하는 이 여정의 많은 주제를 다룹니다.

여정의 특정 부분으로 바로 이동할 수 있지만 이전 문서의 개념을 기반으로 하는 많은 개념이 있습니다. 처음부터 시작하여 순차적으로 진행하는 것이 좋습니다.

| # | 문서 | 설명 |
|---|---|---|
| 0 | AEM Headless Developer 여정 | 이 문서 |
| 1 | [CMS Headless 개발에 대해 알아보기](learn-about.md) | 헤드리스 기술 및 사용 시기를 알아봅니다. |
| 2 | [AEM Headless as a Cloud Service 시작하기](getting-started.md) | AEM Headless 사전 요구 사항에 대해 알아보기 |
| 3 | [AEM Headless를 사용한 첫 번째 경험으로의 경로](path-to-first-experience.md) | 개발 환경을 설정하고 간단한 앱을 AEM Headless와 통합하는 방법을 알아봅니다 |
| 4 | [컨텐츠를 모델링하는 방법](model-your-content.md) | 컨텐츠 구조를 모델링하는 방법을 알아봅니다. |
| 5 | [AEM 배달 API를 통해 콘텐츠에 액세스하는 방법](access-your-content.md) | GraphQL 쿼리를 사용하여 컨텐츠 조각 컨텐츠에 액세스하는 방법을 알아봅니다. |
| 6 | [AEM Assets API를 통해 콘텐츠를 업데이트하는 방법](update-your-content.md) | REST API를 사용하여 컨텐츠 조각 컨텐츠에 액세스하고 업데이트하는 방법을 알아봅니다. |
| 7 | [AEM Headless에서 앱과 컨텐츠를 모두 통합하는 방법](put-it-all-together.md) | AEM Headless SDK를 사용하여 AEM 프로젝트를 라이브로 전환하는 방법을 알아봅니다. |
| 8 | [Headless 애플리케이션 실행 방법](go-live.md) | 애플리케이션을 라이브로 배포하고 Git에서 로컬 코드를 가져와 CI/CD용 Cloud Manager Git 파이프라인으로 이동하는 방법을 알아봅니다. |
| 9 | [선택 사항 - AEM을 사용하여 단일 페이지 애플리케이션(SPA)을 만드는 방법](create-spa.md) | 헤드리스 및 헤드리스 게재를 결합하는 방법을 살펴보고 AEM SPA 편집기 프레임워크를 사용하여 편집 가능한 SPA을 만드는 방법을 알아봅니다. |

## 다음 단계 {#what-is-next}

다음 문서를 체크아웃하여 시작합니다. [CMS 헤드리스 개발에 대해 알아봅니다.](learn-about.md)

### 자신만의 모험 선택 {#choose-your-path}

당신 자신의 진도에 따라 배우는 것이 더 좋으세요? 다음 옵션을 확인하십시오.

* 계속 **headless 개념 및 AEM headless 기술에 대해 알아보기**&#x200B;을 지정하는 경우, 다음 번에 문서를 검토하여 권장하는 대로 AEM 헤드리스 여정을 계속해야 합니다 [컨텐츠를 AEM 컨텐츠 모델로 모델링하는 방법](model-your-content.md) AEM에서 컨텐츠 구조를 모델링하는 방법을 알아봅니다.
* 원하는 경우 **다음을 통해 학습**&#x200B;로 이동하면 [AEM Headless 실습 자습서 시작하기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=ko-KR) 에서는 간단한 프로젝트를 구현하여 AEM 헤드리스 콘텐츠를 노출하여 AEM 헤드리스 개발에 직접 참여합니다.

## 추가 리소스 {#additional-resources}

설명서 여정은 관련 프로세스와 기능을 안내하는 설명을 제공하여 AEM에서 비즈니스 문제를 해결하는 방법을 보여줍니다. 여정은 단일 비즈니스 요구 사항을 충족하기 위해 여러 기능이 함께 작동하는 방식을 보여줍니다.

AEM의 강력한 기능이 함께 작동하는 방식에 대한 자세한 내용은 이러한 추가 여정을 참조하십시오.

* [AEM Headless 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - AEM을 학습하고 기존 지식을 습득하는 것을 선호하는 경우 AEM Headless에서 빌드된 애플리케이션을 만들고 사용하는 API 및 프레임워크로 구성된 실습 자습서를 살펴보십시오.
* [AEM 헤드리스 번역 여정](/help/journey-headless/translation/overview.md) - 이 설명서 여정은 헤드리스 기술, AEM에서 헤드리스 콘텐츠를 제공하는 방법 및 이를 번역할 수 있는 방법에 대한 광범위한 이해를 제공합니다.
* [헤드리스 작성 여정](/help/journey-headless/author/overview.md) - AEM의 강력하고 유연한 헤드리스 기능과 각각의 능력, 그리고 귀하의 첫 헤드리스 프로젝트에서 콘텐츠를 모델링하는 방법에 대한 가이드 여정을 시작해 보십시오.
* [헤드리스 설계 여정](/help/journey-headless/architect/overview.md) - 여기에서 Adobe Experience Manager as a Cloud Service의 강력하고 유연한 헤드리스 기능을 접해 보고 프로젝트 콘텐츠를 모델링하는 방법을 알아보십시오.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - AEM 및 헤드리스 기술에 대해 잘 알고 있는 경우에는 심층적인 기술 문서를 참조하십시오.
