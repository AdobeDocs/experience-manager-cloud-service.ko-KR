---
title: AEM Headless CMS 개발자 여정
description: Adobe Experience Manager(AEM) as a Headless CMS를 사용하여 Headless 개발에 대해 알아봅니다. 콘텐츠 모델, 콘텐츠 조각, GraphQL API와 같은 기능을 사용하여 Headless 콘텐츠 게재를 개선하는 방법에 대해 알아봅니다.
landing-page-description: Headless 콘텐츠 게재 및 구현을 이해합니다. 비즈니스 내부에서 전략을 개발하는 방법에 대해 자세히 알아봅니다.
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
source-git-commit: 94e5d0e84d5c55d0ff61a705e079b4dc8e32a777
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 98%

---

# AEM Headless CMS 개발자 여정 {#aem-headless-developer-journey}

Adobe Experience Manager Headless CMS를 처음 사용하는 개발자용 설명서를 시작합니다.

강력하고 유연한 Headless 기능 및 개별 기능과 첫 번째 Headless 개발 프로젝트에서 기능을 사용하는 방법에 대해 알아봅니다. 이 여정은 첫 번째 Headless 애플리케이션 개발에 필요한 모든 정보를 제공합니다.

{{headless-trials-promotion}}

>[!CONTEXTUALHELP]
>id="aemcloud_headless_developer_resources"
>title="AEM Headless 개발자 리소스 및 고급 설명서"
>abstract="AEM Headless CMS에 대해 알아보고 더 나은 애플리케이션과 더 빠른 경험을 빌드 및 제공하는 데 필요한 모든 것입니다."
>additional-url="https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html" text="AEM Headless 개발자 리소스"

## 소개 {#introduction}

AEM의 Headless 구현은 콘텐츠 조각 모델 및 콘텐츠 조각을 사용하여 구조화되고 채널 중립적이며 재사용 가능한 콘텐츠 조각과 크로스 채널 게재를 만드는 데 중점을 둡니다. 이를 실현하려면 전체 스택 솔루션의 기존 방식과 마찬가지로 페이지 및 구성 요소 관리를 생략합니다. 디지털 경험을 구현하기 위한 현대적이고 동적인 개발 패턴입니다.

이 안내서는 AEM의 Headless 구현 주제를 안내하므로 작업이 완료되면 다음 작업을 수행할 수 있습니다.

* Headless 콘텐츠 게재와 이점을 완전하게 이해할 수 있습니다.
* AEM의 Headless 기능과 Headless 경험 게재를 위해 이 기능이 함께 작동하는 방식을 이해할 수 있습니다.
* 첫 번째 AEM Headless 프로젝트를 구현하는 첫 단계를 수행할 수 있습니다.

>[!TIP]
>
> **직접 해보면서 배우는 것**&#x200B;을 선호하고 기존 AEM을 알고 있다면 API 및 프레임워크로 구성되고 이 문서 끝에 있는 [추가 리소스 섹션](#additional-resources)에 제공되는 AEM Headless 튜토리얼을 참조해 보십시오.

## 대상자 {#audience}

이 여정은 개발자를 위해 설계되어 개발자의 관점에서 AEM Headless 프로젝트에 대한 요구 사항, 단계 및 접근 방식을 제시합니다. 이 여정은 개발자가 프로젝트 성공을 위해 상호 작용해야 하는 추가 담당자를 정의하지만, 이 여정은 개발자의 관점에서 전개됩니다.

다음은 이 여정에서 상호 작용하는 담당자입니다.

| 담당자 | 설명 | 이 여정에서의 역할 |
|---|---|---|
| 개발자 (타깃 대상자) | 다양한 소스의 콘텐츠를 사용하는 Headless 애플리케이션을 개발한 경험 | 이 여정의 타깃 대상자 |
| 콘텐츠 작성자 | Headless 방식으로 사이트에 게재되는 콘텐츠 생성 및 관리 | 콘텐츠 작성자는 개발자가 Headless 방식으로 게재하는 콘텐츠를 만듭니다. |
| 관리자 | AEM의 기본 설정 및 구성 관리 | 개발자는 관리자와 협력하여 개발에 필요한 구성을 변경할 수 있습니다. |
| 콘텐츠 설계자 | Headless 방식으로 사이트에 게재할 데이터에 대한 요구 사항 분석 및 해당 데이터의 구조 정의 | 개발자는 콘텐츠 설계자와 협력하여 데이터 구조와 데이터를 Headless 방식으로 게재하기 위한 요구 사항을 이해할 수 있습니다. |

## Headless 개발자 여정 {#the-journey}

AEM의 Headless에 대한 기본 지식을 제공하는 다양한 주제는 이 여정에서 자세히 다룹니다.

여정의 특정 부분으로 바로 이동할 수 있지만, 많은 개념이 이전 문서의 개념을 기반으로 빌드됩니다. 처음부터 시작하여 순차적으로 진행하는 것이 좋습니다.

| # | 문서 | 설명 |
|---|---|---|
| 0 | AEM Headless 개발자 여정 | 이 문서 |
| 1 | [CMS Headless 개발에 대해 알아보기](learn-about.md) | Headless 기술과 사용 시기에 대해 알아봅니다. |
| 2 | [AEM Headless as a Cloud Service 시작하기](getting-started.md) | AEM Headless 사전 요구 사항에 대해 알아보기 |
| 3 | [AEM Headless를 사용한 첫 번째 경험으로의 경로](path-to-first-experience.md) | 개발 환경을 설정하고 간단한 앱을 AEM Headless와 통합하는 방법에 대해 알아보기 |
| 4 | [콘텐츠를 모델링하는 방법](model-your-content.md) | 콘텐츠 구조를 모델링하는 방법에 대해 알아봅니다. |
| 5 | [AEM 게재 API를 통해 콘텐츠에 액세스하는 방법](access-your-content.md) | GraphQL 쿼리를 사용하여 콘텐츠 조각의 콘텐츠에 액세스하는 방법에 대해 알아봅니다. |
| 6 | [AEM Assets API를 통해 콘텐츠를 업데이트하는 방법](update-your-content.md) | REST API를 사용하여 콘텐츠 조각의 콘텐츠에 액세스하고 업데이트하는 방법에 대해 알아봅니다. |
| 7 | [결합 방법 - AEM Headless의 앱과 콘텐츠](put-it-all-together.md) | AEM 프로젝트를 가져와 AEM Headless SDK 실행을 준비하는 방법에 대해 알아봅니다. |
| 8 | [Headless 애플리케이션 실행 방법](go-live.md) | 실행 중인 애플리케이션을 배포하고 Git의 로컬 코드를 사용하여 CI/CD 파이프라인용 Cloud Manager Git으로 이동하는 방법에 대해 알아봅니다. |
| 9 | [옵션 - AEM을 통해 단일 페이지 애플리케이션(SPA)을 제작하는 방법](create-spa.md) | Headful 및 Headless 게재를 결합하는 방법을 살펴보고 AEM의 SPA 편집기 프레임워크를 사용하여 편집 가능한 SPA를 제작하는 방법에 대해 알아봅니다. |

{style="table-layout:auto"}

## 다음 단계 {#what-is-next}

다음 문서 확인으로 시작: [CMS Headless 개발에 대해 알아보기.](learn-about.md)

### 나만의 어드벤처 선택 {#choose-your-path}

원하는 속도로 학습하시겠습니까? 다음 옵션 확인:

* **Headless 개념 및 AEM의 Headless 기술**&#x200B;에 대해 계속 알아보려면 다음 문서인 [콘텐츠를 AEM 콘텐츠 모델로 모델링하는 방법](model-your-content.md)을 검토하여 권장하는 AEM Headless 여정을 계속하는 것이 좋습니다(AEM의 콘텐츠 구조를 모델링하는 방법에 대해 알아보는 경우).
* **직접 해보면서 배우는 것**&#x200B;을 선호하면 [AEM Headless 실습 튜토리얼 시작하기](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html)로 이동할 수 있습니다(AEM Headless 콘텐츠를 노출하는 간단한 프로젝트를 구현하여 AEM Headless 개발로 직접 이동하는 경우).

## 추가 리소스 {#additional-resources}

설명서 여정에서는 관련 프로세스 및 기능을 안내하는 내러티브를 제공하여 AEM을 통해 비즈니스 문제를 해결하는 방법을 보여 줍니다. 여정은 한 가지 비즈니스 요구 사항을 충족시키기 위해 여러 기능이 함께 작동하는 방식을 보여 줍니다.

AEM의 강력한 기능들이 함께 작동하는 방법에 대한 자세한 내용은 이들 추가 여정을 확인하십시오.

* 다음 [AEM 개발자 포털](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [AEM Headless 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - 직접 해 보면서 배우는 것을 선호하고 기존 AEM을 알고 있다면 API 및 프레임워크로 구성된 실습형 튜토리얼을 사용하여 AEM Headless에 빌드된 애플리케이션을 만들고 사용해 보십시오.
* [AEM Headless 번역 여정](/help/journey-headless/translation/overview.md) - 이 설명서 여정을 통해 Headless 기술, AEM에서 Headless 콘텐츠를 제공하는 방법과 콘텐츠를 번역하는 방법을 폭넓게 이해할 수 있습니다.
* [Headless 작성 여정](/help/journey-headless/author/overview.md) - AEM의 강력하고 유연한 Headless 기능과 각각의 능력, 그리고 사용자의 첫 Headless 프로젝트에서 콘텐츠를 모델링하는 방법에 대한 가이드 여정을 시작해 보십시오.
* [Headless 설계자 여정](/help/journey-headless/architect/overview.md) - 여기에서 Adobe Experience Manager as a Cloud Service의 강력하고 유연한 Headless 기능을 접해 보고 프로젝트 콘텐츠를 모델링하는 방법을 알아보십시오.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - AEM 및 Headless 기술에 대해 확실히 이해하고 있다면 바로 심화 기술 문서를 확인합니다.
   * [AEM as a Headless CMS 소개](/help/headless/introduction.md)
