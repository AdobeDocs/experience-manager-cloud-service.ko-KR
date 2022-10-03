---
title: 개인화 및 콘텐츠 타겟팅
description: AEM을 사용하여 개인화된 타깃팅된 컨텐츠를 만드는 방법을 알아봅니다
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
source-git-commit: 635a9e577f03c865cdb31f539598fb8fe034d7b7
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 12%

---


# 개인화 및 콘텐츠 타겟팅 {#personalization-and-content-targeting}

고객에게 제공하는 웹 컨텐츠의 개인화는 해당 경험을 자신의 관심사와 요구 사항에 맞게 재단하는 것을 의미합니다. 그들에 대한 정보를 기반으로 이 작업을 수행할 수 있습니다. 예를 들어, 쇼핑 요약, 연령, 성별, 지리 등

AEM(Adobe Experience Manager as a Cloud Service)을 사용하면 컨텐츠 선택 사항을 만든 다음, 각 개별 경험을 보게 되는 대상(최종 사용자 그룹)을 지정할 수 있습니다. 즉, 특정 대상에서 개인화된 경험을 타깃팅합니다.

리더기가 온라인 상태이면 타깃팅 엔진은 최종 사용자에 대해 사용할 수 있는 정보를 검토하고 경험 정의와 비교합니다. 그러면 엔진 *&quot;finds&quot;* 개인화된 경험을 표시해야 합니다.

AEM은 다음 작업을 위한 도구 프레임워크를 제공합니다.

* 사용 가능한 고객 정보에 따라 다양한 대상에 적합한 타깃팅된 컨텐츠를 작성합니다.
* 대상 정의에 대해 알려진 사용자 정보를 확인하는 데 사용되는 규칙을 정의합니다.
* 타깃팅된 개인화된 경험을 제공하기 위해 페이지 구성 현재 최종 사용자에게 적용할 수 있는 특정 콘텐츠를 렌더링하기 위해.

다음 개요에서는 AEM as a Cloud Service에서 개인화에 사용되는 몇 가지 용어와 그 뒤에 권장되는 작업 순서를 보여 줍니다.

## 경험 {#experience}

경험은 최종 사용자에게 표시할 콘텐츠입니다.

## 개인화된 경험 {#personalized-experience}

개인화된 경험은 제한된 대상에게 표시되는 경험입니다. 대상이 사용자에 의해 정의되며, 컨텐츠는 현재 최종 사용자에 대해 알려진 정보가 해당 대상 정의에 해당하는 경우에만 표시됩니다.

페이지를 만들 때에는 여러 경험을 정의하고 각 경험은 하나 이상의 대상으로 확인됩니다. 대상이 해결되지 않으면 기본 경험이 표시됩니다.

### 오퍼 {#offer}

<!-- not clear - needs clarification -->
<!-- is an offer a personalized experience, or an activity? -->

오퍼는 개인화된 경험으로서, 종종 제한된 기간 동안 사용할 수 있습니다.

예를 들어 샘플 웹 사이트의 페이지는 오퍼를 페이지 맨 위에 나타나는 티저 이미지로 사용할 수 있습니다. 30세 이상인 사람과 30세 미만의 사람은 다른 오퍼를 경험 티저로 보게 됩니다.

## 대상자 {#audience}

대상은 개인화된 컨텐츠로 타깃팅하려는 최종 사용자 그룹입니다. 방문자가 웹 페이지를 열면 페이지 로직은 알려진 정보를 기반으로 방문자가 속한 대상을 결정합니다. 해당 평가를 기반으로 AEM에 해당 대상을 위해 만든 콘텐츠가 표시됩니다.

대상은 마케팅 세그먼트를 기반으로 합니다. 이러한 파일은 AEM 또는 Adobe Target에서 만들어집니다. 대상자 콘솔을 사용하여 AEM에서 직접 Adobe Target 대상을 만들 수 있습니다.

### 세그먼트 {#segment}

AEM ContextHub 내에서 대상은 규칙(조건)을 기반으로 하여 세그먼트로 정의됩니다. 그런 다음 필요한 컨텐츠를 렌더링하도록 확인됩니다.

## 활동 {#activity}

활동:

* 특정 대상(세그먼트)과 특정 경험의 매핑을 정의합니다
* 타깃팅이 적용되는 기간을 정의합니다
* 는 [타깃팅 엔진](#targeting-engine) 페이지에서

<!-- an example for each of the two types would be good -->

활동은 개인화 활동 또는 A/B 테스트 활동(AEM 및 Adobe Target 개인화 워크플로우의 경우)일 수 있습니다.

예를 들어, 활동은 두 개의 개별 대상에 대한 경험을 정의할 수 있습니다. 30세 이상 및 30세 미만. 그러면 웹 사이트의 페이지에 각 대상에 대해 서로 다른 제품이 표시될 수 있습니다.

또는, 다른 예처럼 제품 카탈로그에는 계절별 제품에 중점을 두는 티저가 포함될 수 있습니다. 따라서 여름 스포츠 활동은 여름 동안 티저가 타깃팅하는 대상을 정의할 수 있습니다.

를 사용하십시오 [활동 콘솔](/help/sites-cloud/authoring/personalization/activities.md) 을 위한 활동을 만들고 관리하려면 [브랜드](#brand). 활동을 작성할 때 [타깃팅된 콘텐츠](/help/sites-cloud/authoring/personalization/targeted-content.md) with [타깃팅 모드](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode).

### 브랜드 {#brand}

브랜드에는 마케팅 활동 및 영역이 선택되어 있습니다.

활동 콘솔을 사용하여 브랜드를 만들면 오퍼 콘솔에도 표시됩니다.

### 영역 {#area}

지역은 브랜드의 구획이다.

## 타깃팅 모드 {#targeting-mode}

작성 시 개인화를 위한 구성 요소를 활성화 및 구성하는 데 사용되는 편집 모드입니다.

다음을 수행할 수 있습니다 [타깃팅된 컨텐츠 작성](/help/sites-cloud/authoring/personalization/targeted-content.md) AEM의 타깃팅 모드 사용. 타겟팅 모드 및 타겟 구성 요소는 마케팅 활동의 경험을 위한 콘텐츠를 만드는 도구를 제공합니다.

## 경험 조각 {#experience-fragments}

경험을 구성하는 그룹화된 구성 요소 세트입니다.

[경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment) 경험을 만들기 위해 콘텐츠 및 정보(스타일링 등)로 구성됩니다. 페이지를 작성할 때 직접 사용할 수 있습니다. AEM 페이지의 하위 집합으로 생각할 수 있습니다. 이를 통해 컨텐츠 작성자는 사이트 페이지 및 타사 시스템을 포함하여 채널 간에 컨텐츠를 재사용할 수 있습니다.

개인화 예제의 경우 제목, 이미지, 설명 및 클릭유도문안 단추를 결합하여 티저 경험을 형성할 수 있습니다. 경험 조각 사용은 Adobe Target 개인화 사용의 주요 부분입니다.

## 타겟팅 엔진 {#targeting-engine}

타깃팅 엔진은 타깃팅된 컨텐츠에 대한 논리를 해결하는 메커니즘입니다. [활동](/help/sites-cloud/authoring/personalization/activities.md)은 사용 가능한 두 개의 타겟팅 엔진인 AEM과 Adobe Target 중 하나를 사용하도록 구성되어 있습니다.

타깃팅 엔진은 사용할 개인화 시스템을 결정하는 플랫폼 또는 메커니즘입니다.

현재 AEM에서는 다음을 사용할 수 있습니다.

* [AEM ContextHub](#aem-contexthub) (표준 AEM)
* a [Adobe Target](#adobe-target) 개인화 엔진

>[!CAUTION]
>
>단일 AEM 페이지에서는 두 엔진을 동시에 사용할 수 없습니다.
>
>동일한 사이트 내에서 두 엔진을 별도의 페이지에서 사용할 수 있습니다.

### AEM ContextHub {#aem-contexthub}

AEM은 페이지 요청을 처리하고 표시할 콘텐츠를 결정하는 내장 타깃팅 엔진 ContextHub를 제공합니다. AEM 타겟팅 엔진을 사용하는 경우 경험의 대상을 정의하기 위해 AEM에서 만들어진 세그먼트를 사용해야 하는 제한이 있습니다.

### Adobe Target {#adobe-target}

Adobe Target 타겟팅 엔진을 사용하면 페이지 방문에서 수집된 정보가 Adobe Target에서 추적됩니다.

* 이 타겟팅 엔진을 사용하는 경우, Adobe Target에서 가져오는 세그먼트를 사용하여 경험의 대상을 정의합니다.
* Adobe Target 엔진을 사용하는 활동은 [Target에 동기화](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target)됩니다.

이 엔진을 사용하면 [Adobe Target 통합](/help/sites-cloud/integrating/integration-adobe-target-ims.md).

## 개인화된 콘텐츠를 설정하는 방법 {#how-to-setup-personalized-content}

개인화된 콘텐츠를 전달하는 데 필요한 다양한 단계 및 정의가 있습니다.

1. 타깃팅 엔진과 AEM 통합.

1. 대상자를 구성합니다.

   1. 타깃팅 엔진에 따라 규칙과 함께 대상 또는 세그먼트를 정의합니다.

1. 브랜드 및 활동을 만듭니다.

1. 다양한 대상에게 표시할 경험의 선택을 작성하십시오.

1. 특정 대상(세그먼트)에 타깃팅하여 이러한 경험을 개인화합니다.