---
title: AEM 참조 데모 추가 기능 여정
description: 최소한의 AEM 구성으로 AEM 참조 데모 추가 기능을 샌드박스 환경에 손쉽게 추가하는 방법에 대한 가이드 여정을 시작해 보십시오. 모범 사례를 기반으로 한 풍부한 예제를 통해 AEM의 강력한 기능을 테스트합니다.
exl-id: 8a6d4abf-0832-40e8-9ba6-1ad4ba794ffa
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 100%

---

# AEM 참조 데모 추가 기능 여정 {#reference-demos-add-on-journey}

최소한의 AEM 구성으로 AEM 참조 데모 추가 기능을 샌드박스 환경에 손쉽게 추가하는 방법에 대한 가이드 여정을 시작해 보십시오. 모범 사례를 기반으로 한 풍부한 예제를 통해 AEM Sites 및 AEM Screens의 강력한 기능을 테스트합니다.

## 소개 {#introduction}

AEM은 디지털 환경 제작 및 관리를 위한 강력한 도구 세트입니다. 콘텐츠 작성자는 사이트 편집기를 사용하여 디지털 경험을 손쉽게 만들 수 있습니다. 사이트 콘솔을 사용하여 콘텐츠를 구성할 수 있으며, 동시에 AEM에서 채널을 통해 대상자에게 전달하는 라이브 콘텐츠를 볼 수 있습니다.

샘플 콘텐츠와 구성이 없으면 신규 클라이언트와 숙련된 클라이언트 모두에게 AEM의 강력한 기능을 테스트하는 데 어려움을 겪을 수 있습니다. AEM 참조 데모 추가 기능을 사용하면 샘플 콘텐츠로 사전 로드되고, 최신 Adobe 모범 사례 지침을 사용하여 사전 구성된 샌드박스 환경을 손쉽게 제작할 수 있습니다. 추가 기능을 사용하면 거의 모든 구성 없이 컨텍스트 내에서 AEM Sites 및 AEM Screens 기능을 간편하게 평가할 수 있습니다.

* **AEM을 처음 사용하는 경우**, 이 여정을 따라 완전히 기능하는 실제 AEM 환경에서 실제 콘텐츠를 손쉽게 시작하고 운영해 보십시오. 이를 통해 기능을 테스트하고 AEM 기능을 알 수 있습니다.
* **숙련된 AEM 사용자의 경우** 이 여정을 따라 가장 간편하게 테스트용 개별 데모 환경을 설정하거나 새로운 기능을 사용하여 POC를 만들어 보십시오.

귀하에게 특별히 필요한 사항이 무엇이든 실제적이며 완전히 기능하는 샘플 콘텐츠로 채워진 AEM 환경이 필요하다면 AEM 참조 데모 추가 기능을 사용하여 샌드박스를 설정하는 것이 좋습니다. 계속해서 읽어 보십시오.

## AEM 설명서 여정 {#documentation-journeys}

[설명서 여정](/help/journey-documentation/documentation-journeys.md)에는 독자가 최소한의 사전 주제 또는 AEM 지식을 전제로 비즈니스 문제를 처음부터 끝까지 이해하고 해결하는 데 도움이 되는 묘사를 제공하여 다양하고 복잡한 주제와 기능이 결합되어 있습니다.

설명서 여정은 Adobe의 최신 연구, Adobe 컨설턴트의 입증된 구현 경험 및 고객 프로젝트의 피드백을 통해 제공되는 모범 사례 원칙을 중심으로 설계되었습니다.

Adobe가 AEM을 통해 AEM 관련 사이트 비즈니스 사례를 해결하는 방법에 대해 알아보려면 AEM Sites 여정에서 시작해 보십시오.

## 대상자 {#audience}

이 여정에서는 Sites나 Screens 또는 둘 다의 데모 콘텐츠 등 AEM 참조 데모 추가 기능을 사용하여 프로그램을 제작하고 AEM 샌드박스를 설정하기 위한 요구 사항, 단계 및 접근 방식에 대해 설명합니다. 이에 대한 주요 대상자는 Cloud Manager에서 **비즈니스 소유자** 역할이 할당된 **시스템 관리자**&#x200B;입니다. 일반적으로 비즈니스 소유자는 환경 관리 담당자와 동일한 사람입니다. 단, 참조 데모 추가 기능이 설치되고 나면 해당 관리자는 다른 사용자에게 추가 기능에 의해 활성화된 기능을 테스트하도록 AEM 환경에 대한 액세스 권한을 부여할 수 있습니다.

## AEM 참조 데모 추가 기능 여정 {#the-journey}

이 여정에서 몇 가지 주제들을 살펴봅니다. 다음 문서는 프로그램을 제작하고 AEM 참조 데모 추가 기능을 설정하고 사용하는 데 필요한 기초 지식을 제공합니다. 이 문서는 순서대로 읽어야 합니다. 필요에 따라 상세 기술 설명서와 연결됩니다.

| # | 문서 | 설명 |
|---|---|---|
| 0 | AEM 참조 데모 추가 기능 여정 | 이 문서 |
| 1 | [참조 데모 추가 기능 설치 이해](installation.md) | Cloud Manager 및 이를 사용하여 추가 기능을 설치하는 방법에 대해 알아봅니다. |
| 2 | [프로그램 및 파이프라인 제작](create-program.md) | 새 프로그램 및 파이프라인을 설정하여 추가 기능을 배포하는 방법에 대해 알아봅니다. |
| 3 | [데모 사이트 만들기](create-site.md) | 사전 구성된 템플릿 라이브러리를 기반으로 AEM에서 데모 사이트를 제작합니다. |
| 4 | [(옵션) 데모 사이트에 대해 AEM Screens 활성화](screens.md) | 옵션 - 제작한 데모 사이트에서 전체 AEM Screens as a Cloud Service 환경을 활성화하기 위한 추가 단계에 대해 알아봅니다. |
| 5 | [데모 사이트 관리](manage.md) | 내 데모 사이트를 관리하는 데 도움이 되는 도구 및 이를 제거하는 방법에 대해 알아봅니다. |

## 다음 단계 {#what-is-next}

이제 AEM 참조 데모 추가 기능 여정을 시작할 준비가 되었습니다.

* Cloud Manager와 AEM을 함께 사용하여 데모 환경을 제작하는 방법 및 나만의 데모 환경을 설정하고 사용하는 방법에 대해 자세히 알아보려면 [참조 데모 추가 기능 설치 이해](installation.md)를 참조하십시오. 이 문서를 순서대로 진행하십시오.
* 숙련된 Cloud Manager 사용자이거나 추가 기능 구성 및 사용으로 바로 이동하고자 하는 경우, [프로그램 및 파이프라인 제작](create-program.md)으로 건너뛰고 그 다음 단계에서 여정을 시작할 수 있습니다.

## 추가 리소스 {#additional-resources}

AEM의 강력한 기능들이 함께 작동하는 방법에 대한 자세한 내용은 이들 추가 리소스를 확인하십시오.

* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager.html?lang=ko) - Cloud Manager의 기능에 대해 자세히 알아보려면 바로 심화 기술 문서를 참조할 수 있습니다.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=ko) - AEM에 대해 확실히 이해하고 있다면 바로 심화 기술 문서를 참조할 수 있습니다.
