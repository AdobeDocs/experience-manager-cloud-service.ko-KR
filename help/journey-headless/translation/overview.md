---
title: AEM Headless 번역 여정
description: AEM의 강력한 번역 도구를 사용하여 Headless 콘텐츠 번역을 통한 가이드 여정을 시작해 보십시오.
exl-id: b677f691-5257-43c3-a4b9-c34932577b31
source-git-commit: ad47148237fe8a8b7c0b4fc4eb293f1155dae560
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 100%

---

# AEM Headless 번역 여정 {#aem-headless-translation-journey}

AEM의 강력한 번역 도구를 사용하여 Headless 콘텐츠 번역을 통한 가이드 여정을 시작해 보십시오.

## 소개 {#introduction}

Headless 구현은 채널, 지역 또는 로케일에 관계없이 어디서든 경험을 대상자에게 전달하는 데 점점 더 중요해지고 있습니다.

Headless 구현은 전체 스택 솔루션의 기존 방식과 마찬가지로 페이지 및 구성 요소 관리를 생략하고 채널 중립적이고 재사용 가능한 콘텐츠 조각 생성 및 크로스 채널 게재에 중점을 둡니다. AEM의 강력한 번역 도구를 사용하여 재사용 가능한 해당 조각을 쉽게 번역하여 어디서든 대상자에게 전달할 수 있습니다.

이 안내서는 가장 중요한 Headless 주제를 안내하므로 완료 시 다음과 같은 작업을 수행할 수 있습니다.

* Headless 콘텐츠 게재에 대한 개요를 살펴볼 수 있습니다.
* AEM의 Headless 기능에 대한 기본 사항을 이해할 수 있습니다.
* AEM의 번역 기능 및 이들과 Headless 콘텐츠의 관련성에 대해 이해할 수 있습니다.
* 자체 Headless 콘텐츠 번역을 시작할 수 있습니다.

목표는 Headless 기술, AEM에서 Headless 콘텐츠를 제공하는 방법과 콘텐츠를 번역하는 방법에 대한 폭넓은 이해를 제공하는 것입니다. 해당 주제에 익숙하지 않은 경우 이 목표를 시작하는 것이 좋습니다.

AEM, Headless 및 번역에 대해 잘 알고 있다면 이 여정에 대한 기초 지식을 이미 알고 있을 것입니다. [아래 추가 리소스 섹션](#additional-resources)에 연결된 기술 설명서를 참조하는 것이 좋습니다.

## AEM 설명서 여정 {#documentation-journeys}

[설명서 여정](/help/journey-documentation/documentation-journeys.md)은 AEM을 처음 접할 수 있는 독자가 최소한의 사전 주제 또는 AEM 지식을 전제로 비즈니스 문제를 처음부터 끝까지 이해하고 해결하는 데 도움이 되는 묘사를 제공하여 다양하고 복잡한 주제와 기능을 결합합니다.

설명서 여정은 Adobe의 최신 연구, Adobe 컨설턴트의 입증된 구현 경험 및 고객 프로젝트의 피드백을 통해 제공되는 모범 사례 원칙을 중심으로 설계되었습니다.

Adobe가 AEM을 통해 AEM 관련 Headless 비즈니스 사례를 해결하는 방법에 대해 알아보려면 [AEM Headless 여정](/help/journey-documentation/documentation-journeys.md)에서 시작해 보십시오.

## 대상자 {#audience}

이 여정은 번역 프로젝트 관리자 또는 TPM이라고도 하는 번역 전문가 사용자를 위해 설계되었습니다. 이 여정은 AEM의 Headless 콘텐츠를 번역하기 위한 요구 사항, 단계 및 접근 방식을 제시합니다. 이 여정은 번역 전문가가 상호 작용해야 하는 추가 담당자를 정의할 수 있지만, 이 여정은 번역 전문가의 관점에서 전개됩니다.

이 여정은 독자가 대형 CMS 시스템에서 콘텐츠를 번역한 경험은 있지만 Headless 기술 또는 AEM에 대한 지식은 없다고 가정합니다.

다음은 이 여정에서 상호 작용하는 담당자입니다.

| 담당자 | 설명 | 여정에서의 역할 |
|---|---|---|
| 번역 전문가 | 번역할 콘텐츠 정의 및 해당 워크플로 관리 | 이 여정의 대상자 |
| 콘텐츠 작성자 | Headless 방식으로 사이트에 게재되는 콘텐츠 생성 및 관리 | 콘텐츠 작성자는 번역 전문가가 번역해야 하는 콘텐츠를 만듭니다. |
| 관리자 | AEM의 기본 설정 및 구성 관리 | 번역 전문가는 관리자와 함께 작업하여 번역 커넥터 설치와 같은 번역에 필요한 구성 변경을 수행합니다. |
| 콘텐츠 설계자 | Headless 방식으로 사이트에 게재할 데이터에 대한 요구 사항 분석 및 해당 데이터의 구조 정의 | 번역 전문가는 콘텐츠 설계자와 함께 작업하여 콘텐츠를 간편하게 번역할 수 있도록 콘텐츠의 구성을 정의합니다. |

이 여정에서 제공하는 정보는 모든 담당자에게 유용하지만 일부 정보는 특정 역할에 불필요할 수 있습니다. [추가 역할을 다루는 다가오는 여정](/help/journey-documentation/documentation-journeys.md#journeys)은 추후에 업데이트될 예정입니다.

## Headless 번역 여정 {#the-journey}

이 여정에서 다양한 주제들을 살펴보게 됩니다. 다음 문서는 AEM에서의 Headless 콘텐츠 번역에 대한 기초 지식을 제공하며 상세 기술 설명서와 연결됩니다.

여정의 특정 부분으로 바로 이동할 수 있지만 많은 개념이 이전 문서의 개념을 기반으로 합니다. 따라서 AEM에서 Headless 번역을 처음 수행하는 경우 처음부터 시작하여 순차적으로 진행하는 것이 좋습니다.

| # | 문서 | 설명 |
|---|---|---|
| 0 | AEM Headless 번역 여정 | 이 문서 |
| 1 | [Headless 콘텐츠 및 AEM에서의 번역 방법에 대해 알아보기](learn-about.md) | Headless 개념, AEM에 매핑하는 방법 및 AEM 번역 이론에 대해 알아봅니다. |
| 2 | [AEM Headless 번역 시작하기](getting-started.md) | Headless 콘텐츠를 구성하는 방법 및 AEM의 번역 도구의 작동 방식에 대해 알아봅니다. |
| 3 | [번역 커넥터 구성](configure-connector.md) | AEM을 번역 서비스에 연결하는 방법에 대해 알아봅니다. |
| 4 | [콘텐츠 번역](translate-content.md) | 번역 커넥터 및 규칙을 사용하여 Headless 콘텐츠를 번역합니다. |
| 5 | [번역된 콘텐츠 게시](publish-content.md) | 기본 콘텐츠를 업데이트할 때 번역된 콘텐츠를 게시하고 번역을 업데이트하는 방법에 대해 알아봅니다. |

## 다음 단계 {#what-is-next}

이제 Adobe Headless 번역 여정을 시작할 준비가 되었습니다. 여정의 다음 단계로 넘어가 다음 문서인 [AEM의 Headless 콘텐츠 및 번역 방법 알아보기](learn-about.md)를 읽어보시기 바랍니다.

## 추가 리소스 {#additional-resources}

설명서 여정에서는 복잡하고 상호 연관된 프로세스 및 기능을 안내하는 내러티브를 제공하여 AEM을 통해 비즈니스 문제를 해결하는 방법을 보여 줍니다. 여정은 한 가지 비즈니스 요구 사항을 충족시키기 위해 여러 기능이 함께 작동하는 방식을 보여 줍니다.

따라서 여정은 독자적으로 설계되었습니다. 하지만 여러 여정이 서로 관련될 수 있습니다. AEM의 강력한 기능들이 함께 작동하는 방법에 대한 자세한 내용은 이들 추가 여정을 확인하십시오.

* [Headless 작성 여정](/help/journey-headless/author/overview.md) - AEM의 강력하고 유연한 Headless 기능과 각각의 능력, 그리고 사용자의 첫 Headless 프로젝트에서 콘텐츠를 모델링하는 방법에 대한 가이드 여정을 시작해 보십시오.
* [Headless 설계자 여정](/help/journey-headless/architect/overview.md) - 여기에서 Adobe Experience Manager as a Cloud Service의 강력하고 유연한 Headless 기능을 접해 보고 프로젝트 콘텐츠를 모델링하는 방법을 알아보십시오.
* [AEM Headless 개발자 여정](/help/journey-headless/developer/overview.md) - 여기에서 AEM의 강력하고 유연한 Headless 기능과 각각의 능력, 그리고 사용자의 첫 개발 프로젝트에서 이들 기능을 활용하는 방법에 대한 가이드 여정을 시작해 보십시오.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - AEM 및 Headless 기술에 대해 확실히 이해하고 있다면 바로 심화 기술 문서를 참조할 수 있습니다.
* [AEM Headless 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - 직접 해보면서 배우는 것을 선호하고 기술 관련 소양을 갖추고 있다면 API 및 프레임워크로 구성된 실습형 튜토리얼을 사용하여 AEM Headless에 구축된 애플리케이션을 만들고 사용해 보십시오.
