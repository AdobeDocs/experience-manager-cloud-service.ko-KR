---
title: AEM Sites 번역 여정
description: AEM의 강력한 번역 도구를 사용하여 AEM Sites 콘텐츠 번역을 통한 가이드 여정을 시작해 보십시오.
index: true
hide: false
hidefromtoc: false
exl-id: 3db2ff19-dc24-47b6-aa56-2ee2305fe045
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: ht
source-wordcount: '931'
ht-degree: 100%

---

# AEM Sites 번역 여정 {#aem-sites-translation-journey}

AEM의 강력한 번역 도구를 사용하여 AEM Sites 콘텐츠 번역을 통한 가이드 여정을 시작해 보십시오.

## 소개 {#introduction}

AEM Sites는 디지털 환경 제작 및 관리를 위한 강력한 도구 세트입니다. 콘텐츠 작성자는 사이트 편집기를 사용하여 디지털 환경을 손쉽게 제작하고 Sites 콘솔을 사용하여 콘텐츠를 구성할 수 있으며, 모든 콘텐츠가 AEM을 통해 서로 다른 채널의 대상자에게 전달되므로 콘텐츠를 라이브로 확인할 수 있습니다.

AEM은 콘텐츠 번역을 위한 강력한 도구를 제공하므로 다른 지역 또는 로케일의 대상자에게 번역된 콘텐츠를 최대한 신속하게 전달할 수 있습니다. 이 설명서 여정에서는 AEM에서 콘텐츠를 만들고 관리하는 방법을 이해할 수 있는 작성 도구를 소개하고 나만의 번역 프로젝트를 관리하기 위해 알아야 할 사항을 안내합니다.

AEM Sites 및 번역 요구 사항을 잘 알고 있다면 이 여정에 대한 기초 지식을 이미 알고 있을 것입니다. 그렇다면 [아래 추가 리소스 섹션](#additional-resources)에 연결된 기술 설명서를 참조하는 것이 좋습니다.

## AEM 설명서 여정 {#documentation-journeys}

[설명서 여정](/help/journey-documentation/documentation-journeys.md)은 AEM을 처음 접할 수 있는 독자가 최소한의 사전 주제 또는 AEM 지식을 전제로 비즈니스 문제를 처음부터 끝까지 이해하고 해결하는 데 도움이 되는 묘사를 제공하여 다양하고 복잡한 주제와 기능을 결합합니다.

설명서 여정은 Adobe의 최신 연구, Adobe 컨설턴트의 입증된 구현 경험 및 고객 프로젝트의 피드백을 통해 제공되는 모범 사례 원칙을 중심으로 설계되었습니다.

Adobe가 AEM을 통해 AEM 관련 사이트 비즈니스 사례를 해결하는 방법에 대해 알아보려면 AEM Sites 여정에서 시작해 보십시오.

## 대상자 {#audience}

이 여정은 번역 프로젝트 관리자 또는 TPM이라고도 하는 번역 전문가 사용자를 위해 설계되었습니다. 이 여정은 AEM Sites 콘텐츠를 번역하기 위한 요구 사항, 단계 및 접근 방식을 제시합니다. 이 여정은 번역 전문가가 상호 작용해야 하는 추가 담당자를 정의할 수 있지만, 이 여정은 번역 전문가의 관점에서 전개됩니다.

이 여정은 독자가 대형 CMS 시스템에서 콘텐츠를 번역한 경험은 있지만 AEM에 대한 지식은 없다고 가정합니다.

다음은 이 여정에서 상호 작용하는 담당자입니다.

| 담당자 | 설명 | 여정에서의 역할 |
|---|---|---|
| 번역 전문가 | 번역할 콘텐츠 정의 및 해당 워크플로 관리 | 이 여정의 대상자 |
| 콘텐츠 작성자 | 사이트로 제공되는 콘텐츠 생성 및 관리 | 콘텐츠 작성자는 번역 전문가가 번역해야 하는 콘텐츠를 만듭니다. |
| 관리자 | AEM의 기본 설정 및 구성 관리 | 번역 전문가는 관리자와 함께 작업하여 번역 커넥터 설치와 같은 번역에 필요한 구성 변경을 수행합니다. |
| 콘텐츠 설계자 | 사이트로 제공할 데이터에 대한 요구 사항 분석 및 이러한 데이터의 구조 정의 | 번역 전문가는 콘텐츠 설계자와 함께 작업하여 콘텐츠를 간편하게 번역할 수 있도록 콘텐츠의 구성을 정의합니다. |

이 여정에서 제공하는 정보는 모든 담당자에게 유용하지만 일부 정보는 특정 역할에 불필요할 수 있습니다. [추가 역할을 다루는 다가오는 여정](/help/journey-documentation/documentation-journeys.md#journeys)은 추후에 업데이트될 예정입니다.

## Sites 번역 여정 {#the-journey}

이 여정에서 다양한 주제들을 살펴보게 됩니다. 다음 문서는 AEM에서의 사이트 콘텐츠 번역에 대한 기초 지식을 제공하며 상세 기술 설명서와 연결됩니다.

여정의 특정 부분으로 바로 이동할 수 있지만, 많은 개념이 이전 문서의 개념을 기반으로 합니다. 따라서 AEM에서 번역을 처음 수행하는 경우 처음부터 시작하여 순차적으로 진행하는 것이 좋습니다.

| # | 문서 | 설명 |
|---|---|---|
| 0 | AEM Sites 번역 여정 | 이 문서 |
| 1 | [사이트 콘텐츠 및 AEM에서의 사이트 콘텐츠 번역 방법에 대해 알아보기](learn-about.md) | 사이트 개념 및 AEM 번역 이론에 대해 알아봅니다. |
| 2 | [AEM Sites 번역 시작하기](getting-started.md) | 사이트 콘텐츠를 구성하는 방법 및 AEM의 번역 도구의 작동 방식에 대해 알아봅니다. |
| 3 | [번역 커넥터 구성](configure-connector.md) | AEM을 번역 서비스에 연결하는 방법에 대해 알아봅니다. |
| 4 | [번역 규칙 구성](translation-rules.md) | 번역 규칙을 정의하여 번역할 콘텐츠를 식별하는 방법에 대해 알아봅니다. |
| 5 | [콘텐츠 번역](translate-content.md) | 번역 커넥터 및 규칙을 사용하여 사이트 콘텐츠를 번역합니다. |
| 6 | [번역된 콘텐츠 게시](publish-content.md) | 기본 콘텐츠를 업데이트할 때 번역된 콘텐츠를 게시하고 번역을 업데이트하는 방법에 대해 알아봅니다. |

## 다음 단계 {#what-is-next}

이제 Adobe Sites 번역 여정을 시작할 준비가 되었습니다. 여정의 다음 단계로 넘어가 다음 문서인 [AEM의 사이트 콘텐츠 및 번역 방법 알아보기](learn-about.md)를 읽어보시기 바랍니다.

## 추가 리소스 {#additional-resources}

AEM의 강력한 기능들이 함께 작동하는 방법에 대한 자세한 내용은 이들 추가 리소스를 확인하십시오.

* [Headless 작성 여정](/help/journey-headless/author/overview.md) - AEM의 강력하고 유연한 Headless 기능과 각각의 능력, 그리고 사용자의 첫 Headless 프로젝트에서 콘텐츠를 모델링하는 방법에 대한 가이드 여정을 시작해 보십시오.
* [Headless 설계자 여정](/help/journey-headless/architect/overview.md) - 여기에서 Adobe Experience Manager as a Cloud Service의 강력하고 유연한 Headless 기능을 접해 보고 프로젝트 콘텐츠를 모델링하는 방법을 알아보십시오.
* [AEM Headless 개발자 여정](/help/journey-headless/developer/overview.md) - 여기에서 AEM의 강력하고 유연한 Headless 기능과 각각의 능력, 그리고 사용자의 첫 개발 프로젝트에서 이들 기능을 사용하는 방법에 대한 가이드 여정을 시작해 보십시오.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - AEM 및 Headless 기술에 대해 확실히 이해하고 있다면 바로 심화 기술 문서를 참조할 수 있습니다.
* [AEM Headless 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - 직접 해보면서 배우는 것을 선호하고 기술 관련 소양을 갖추고 있다면 API 및 프레임워크로 구성된 실습형 튜토리얼을 사용하여 AEM Headless에 구축된 애플리케이션을 만들고 사용해 보십시오.
