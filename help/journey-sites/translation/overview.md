---
title: AEM Sites 번역 여정
description: AEM의 강력한 번역 도구를 사용하여 AEM Sites 컨텐츠를 번역하여 안내식 여정을 살펴보려면 여기에서 시작하십시오.
index: true
hide: false
hidefromtoc: false
exl-id: 3db2ff19-dc24-47b6-aa56-2ee2305fe045
source-git-commit: ada7c256de5d050724781e4cbad6d877c1562c7b
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 2%

---

# AEM Sites 번역 여정 {#aem-sites-translation-journey}

AEM의 강력한 번역 도구를 사용하여 AEM Sites 컨텐츠를 번역하여 안내식 여정을 살펴보려면 여기에서 시작하십시오.

## 소개 {#introduction}

AEM Sites은 디지털 경험을 만들고 관리하기 위한 강력한 도구 세트입니다. 컨텐츠 작성자는 AEM에서 여러 채널을 통해 대상에 전달하는 콘텐츠를 실시간으로 확인할 수 있지만 사이트 편집기를 사용하여 디지털 경험을 쉽게 만들고 사이트 콘솔을 사용하여 컨텐츠를 구성할 수 있습니다.

AEM은 콘텐츠를 번역하는 동일한 강력한 도구를 제공하여 다른 지역 또는 로케일의 대상에게 최대한 빨리 전달할 수 있도록 합니다. 이 설명서 여정은 작성 도구에 대해 소개하여 AEM에서 컨텐츠를 만들고 관리하는 방법을 이해한 다음, 고유한 번역 프로젝트를 관리하기 위해 알아야 하는 사항을 자세히 설명합니다.

이미 AEM Sites 및 번역 요구 사항을 잘 알고 있는 경우, 이 여정에 대한 기본 지식이 이미 있을 수 있습니다. 이 경우 아래에 연결된 기술 문서를 참조하여 Adobe에 문의하십시오 [아래의 추가 리소스 섹션.](#additional-resources)

## AEM 설명서 여정 {#documentation-journeys}

[설명서 여정](/help/journey-documentation/documentation-journeys.md) AEM에 대해 새로운 지식을 가진 독자들이, 이전의 주제와 AEM 지식을 최소한으로 가정하는 동시에, 처음부터 끝까지 비즈니스 문제를 이해하고 해결하는 데 도움이 되는 이야기를 제공함으로써, 많은 다양한 그리고 아마도 복잡한 주제와 특징들을 함께 결합합니다.

설명서 여정은 Adobe의 최신 연구, Adobe 컨설턴트의 입증된 구현 경험, 고객 프로젝트의 피드백을 통해 우수 사례 원칙을 중심으로 설계되었습니다.

Adobe이 AEM을 사용하여 사이트 비즈니스 사례를 해결하는 방법을 권장하는 방법을 알아보려면 AEM Sites 여정이 시작되는 곳입니다.

## 속성을 확인하는 {#audience}

이 여정은 번역 전문가 사용자를 위해 설계되었으며 종종 번역 프로젝트 관리자 또는 TPM이라고도 합니다. 이 여정은 AEM Sites 컨텐츠를 번역하는 요구 사항, 단계 및 접근 방식을 설명합니다. 여정은 번역 전문가가 상호 작용해야 하는 추가 가상 사용자를 정의할 수 있지만, 여정의 관점은 번역 전문가의 것입니다.

이 여정은 독자가 대규모 CMS 시스템에서 컨텐츠를 번역할 경험이 있다고 가정하지만 AEM에 대한 지식이 없다고 가정합니다.

다음은 이 여정에서 상호 작용하는 가상 정보입니다.

| 모습 | 설명 | 여정의 역할 |
|---|---|---|
| 번역 전문가 | 번역해야 하는 컨텐츠를 정의하고 이러한 워크플로우를 관리합니다 | 이 여정 대상 |
| 컨텐츠 작성자 | 사이트로 전달되는 컨텐츠를 만들고 관리합니다 | 컨텐츠 작성자는 번역 전문가가 번역해야 하는 컨텐츠를 만듭니다. |
| 관리자 | AEM의 기본 설정 및 구성을 관리합니다 | 번역 전문가는 관리자와 함께 번역 커넥터 설치처럼 번역에 필요한 구성을 변경합니다. |
| 컨텐츠 설계자 | 사이트로 전달되어야 하는 데이터에 대한 요구 사항을 분석하고 이 데이터의 구조를 정의합니다 | 번역 전문가들은 콘텐츠 설계자와 협력하여 쉽게 변환할 수 있도록 컨텐츠 구성을 정의합니다. |

이 여정의 정보는 물론 모든 사용자에게 유용할 수 있지만, 일부 정보는 특정 역할에 유용할 수 있습니다. 채널을 고정하세요 [추가 역할을 다루는 제공 여정](/help/journey-documentation/documentation-journeys.md#journeys)

## 사이트 번역 여정 {#the-journey}

이 여정에서 많은 주제를 살펴봅니다. 다음 문서는 AEM에서 사이트 컨텐츠를 번역하고 세부 기술 설명서에 연결되는 기본 지식을 제공합니다.

여정의 특정 부분으로 직접 이동할 수 있지만 많은 개념이 이전 문서의 개념에 구축됩니다. 따라서 AEM에서 번역을 처음 사용하는 경우 처음부터 시작하여 순차적으로 진행하는 것이 좋습니다.

| # | 문서 | 설명 |
|---|---|---|
| 0 | AEM Sites 번역 여정 | 이 문서 |
| 1 | [사이트 컨텐츠와 AEM에서 번역하는 방법에 대해 알아봅니다](learn-about.md) | 사이트 개념과 AEM 번역 이론에 대해 알아봅니다. |
| 2 | [AEM Sites 번역 시작](getting-started.md) | 사이트 콘텐츠를 구성하는 방법과 AEM 번역 도구가 작동하는 방식을 알아봅니다. |
| 3 | [번역 커넥터 구성](configure-connector.md) | AEM을 번역 서비스에 연결하는 방법을 알아봅니다. |
| 4 | [번역 규칙 구성](translation-rules.md) | 번역 규칙을 정의하여 번역 콘텐츠를 식별하는 방법을 알아봅니다. |
| 5 | [컨텐츠 번역](translate-content.md) | 번역 커넥터와 규칙을 사용하여 사이트 콘텐츠를 번역합니다. |
| 6 | [번역된 컨텐츠 게시](publish-content.md) | 기본 컨텐츠가 업데이트될 때 번역된 컨텐츠를 게시하고 번역을 업데이트하는 방법을 알아봅니다. |

## 다음은 무엇입니까? {#what-is-next}

이제 Adobe 사이트 번역 여정을 시작할 준비가 되었습니다. 여정의 다음 부분으로 계속 이동하여 문서를 읽어 보십시오 [사이트 컨텐츠와 AEM에서 번역하는 방법에 대해 알아봅니다](learn-about.md)

## 추가 리소스 {#additional-resources}

AEM의 강력한 기능이 함께 작동하는 방식에 대한 자세한 내용은 이러한 추가 리소스를 참조하십시오.

* [헤드리스 작성 여정](/help/journey-headless/author/overview.md) - AEM의 강력하고 유연한 헤드리스 기능, 첫 번째 헤드리스 프로젝트에서 컨텐츠를 모델링하는 방법을 통해 안내식 여정을 살펴보려면 여기에서 시작하십시오.
* [헤드리스 아키텍트 여정](/help/journey-headless/architect/overview.md) - Adobe Experience Manager as a Cloud Service의 강력하고 유연한 헤드리스 기능과 프로젝트 컨텐츠를 모델링하는 방법을 소개합니다.
* [AEM Headless Developer 여정](/help/journey-headless/developer/overview.md) - AEM의 강력하고 유연한 헤드리스 기능, 첫 번째 개발 프로젝트에서 이러한 기능을 활용하는 방법을 통해 안내식 여정을 살펴보려면 여기에서 시작하십시오.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - AEM 및 헤드리스 기술에 대한 확고한 이해가 있는 경우에는 심층적인 기술 문서를 직접 문의할 수 있습니다.
* [AEM Headless 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - 자습서를 통해 학습하고 기술적으로 경사진 경우 AEM Headless에서 빌드된 애플리케이션을 제작 및 사용하는 API 및 프레임워크로 구성된 실습 자습서를 살펴보십시오.
