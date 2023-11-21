---
title: 개인화 및 콘텐츠 타겟팅
description: AEM으로 개인화되고 타겟팅된 콘텐츠를 만드는 방법 알아보기
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 91%

---


# 개인화 및 콘텐츠 타겟팅 {#personalization-and-content-targeting}

고객에게 제공하는 웹 콘텐츠의 개인화란 이러한 경험을 고객의 관심사와 필요에 맞게 조정하는 것을 의미합니다. 이때 고객에 대해 가지고 있는 정보, 예를 들어 쇼핑 요약, 연령, 성별, 지역 등을 기반으로 삼을 수 있습니다.

Adobe Experience Manager as a Cloud Service(AEM)를 사용하여 선택 콘텐츠를 만든 다음, 각 개별 경험을 보게 되는 대상(최종 사용자 그룹)을 지정할 수 있습니다. 즉, 특정 대상자를 대상으로 개인화된 경험을 타겟팅할 수 있습니다.

사용자가 온라인 상태일 때 타겟팅 엔진은 최종 사용자에 대해 사용 가능한 정보를 검토하고 이를 경험 정의와 비교합니다. 그런 다음 엔진에서 어떤 개인화된 경험을 표시해야 하는지 *“결정”*&#x200B;합니다.

AEM은 다음을 위한 도구 프레임워크를 제공합니다.

* 사용 가능한 고객 정보에 따라 다양한 대상자에게 적합한 타겟팅된 콘텐츠를 작성합니다.
* 대상자 정의에 대해 알려진 사용자 정보를 확인하는 데 사용되는 규칙을 정의합니다.
* 타겟팅되고 개인화된 경험을 제공하도록, 현재 최종 사용자에게 해당되는 특정 콘텐츠를 렌더링하도록 페이지를 구성합니다.

다음 개요에서는 AEM의 개인화에 사용되는 몇 가지 용어를 as a Cloud Service으로 사용한 다음, 권장되는 작업 순서를 제시합니다.

## 경험 {#experience}

경험은 최종 사용자에게 표시하고자 하는 콘텐츠입니다.

## 개인화된 경험 {#personalized-experience}

개인화된 경험은 제한된 대상자에게 표시되는 경험입니다. 대상자는 직접 정의할 수 있으며, 현재 최종 사용자에 대해 알려진 정보가 해당 대상자 정의에 해당하는 경우에만 콘텐츠가 표시됩니다.

페이지를 만들 때 각 경험이 하나(또는 그 이상)의 대상자로 해결되는 여러 경험을 정의하게 됩니다. 배정된 대상자가 없으면 기본 경험이 표시됩니다.

### 오퍼 {#offer}

오퍼는 흔히 제한된 기간 동안 사용할 수 있는 개인화된 경험입니다.

예를 들어 샘플 웹 사이트의 페이지는 페이지 상단에 표시되는 티저 이미지와 같은 오퍼를 사용할 수 있습니다. 30세 이상인 사람과 30세 미만인 사람은 다양한 오퍼를 경험 티저로 볼 수 있습니다.

## 대상자 {#audience}

대상자는 개인화된 콘텐츠로 타겟팅하려는 최종 사용자 그룹입니다. 방문자가 웹 페이지를 열면 페이지 로직은 알려진 정보를 기반으로 방문자가 속한 대상자를 판단합니다. 해당 평가를 기반으로 AEM은 해당 대상자를 위해 만들어진 콘텐츠를 표시합니다.

대상자는 마케팅 세그먼트를 기반으로 합니다. 마케팅 세그먼트는 AEM 또는 Adobe Target에서 생성됩니다. 대상자 콘솔을 사용하여 AEM에서 직접 Adobe Target 대상자를 만들 수 있습니다.

### 세그먼트 {#segment}

AEM ContextHub 내에서 대상자는 규칙(조건)을 기반으로 세그먼트로 정의됩니다. 그런 다음 필요한 콘텐츠를 렌더링하도록 배정됩니다.

## 활동 {#activity}

활동은 다음 작업을 수행합니다.

* 특정 대상자(세그먼트)와 특정 경험의 매핑 정의
* 타겟팅이 적용되는 기간 정의
* 페이지에서 사용하는 [타겟팅 엔진](#targeting-engine) 식별

활동은 개인화 활동이거나 A/B 테스트 활동(AEM 및 Adobe Target 개인화 워크플로의 경우)일 수 있습니다.

예를 들어 활동은 30세 이상의 사람과 30세 미만의 사람, 이렇게 두 명의 서로 다른 대상자를 위한 경험을 정의할 수 있습니다. 그런 다음 웹 사이트의 페이지에 각 대상자에 대해 서로 다른 제품을 표시할 수 있습니다.

또는 예를 들어 제품 카탈로그에 계절 상품에 집중하는 티저가 포함될 수 있습니다. 즉, 여름 스포츠 활동은 여름 기간 동안 티저가 타겟팅하는 대상자를 정의할 수 있습니다.

[활동 콘솔](/help/sites-cloud/authoring/personalization/activities.md)을 사용하여 [브랜드](#brand)를 위한 활동을 만들고 관리할 수 있습니다. [타겟팅된 콘텐츠](/help/sites-cloud/authoring/personalization/targeted-content.md)를 작성할 때 [타겟팅 모드](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode)로 활동을 만들 수도 있습니다.

### 브랜드 {#brand}

브랜드는 다양한 마케팅 활동 및 영역을 보유하고 있습니다.

활동 콘솔을 사용하여 브랜드를 생성하면 오퍼 콘솔에도 나타납니다.

### 영역 {#area}

영역은 브랜드의 하위 구분입니다.

## 타겟팅 모드 {#targeting-mode}

작성 시 개인화를 위한 구성 요소를 활성화하고 구성하는 데 사용되는 편집 모드입니다.

AEM의 타겟팅 모드를 사용하여 [타겟팅된 콘텐츠를 작성](/help/sites-cloud/authoring/personalization/targeted-content.md)할 수 있습니다. 타겟팅 모드 및 타겟 구성 요소는 마케팅 활동의 경험을 위한 콘텐츠를 만드는 도구를 제공합니다.

## 경험 조각 {#experience-fragments}

경험을 구성하는 그룹화된 구성 요소 세트입니다.

[경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment)은 콘텐츠와 정보(스타일링 등)로 구성되어 경험을 만듭니다. 페이지 작성 시 직접 사용할 수 있습니다. AEM 페이지의 하위 집합으로 생각할 수 있습니다. 이를 통해 콘텐츠 작성자가 Sites 페이지와 서드파티 시스템을 비롯한 여러 채널에서 콘텐츠를 재사용할 수 있습니다.

개인화의 예로 제목, 이미지, 설명 및 콜 투 액션 버튼을 결합하여 티저 경험을 형성할 수 있습니다. 경험 조각 사용은 Adobe Target 개인화 사용의 핵심 부분입니다.

## 타겟팅 엔진 {#targeting-engine}

타겟팅 엔진은 타겟팅된 콘텐츠에 대한 논리를 배정하는 메커니즘입니다. [활동](/help/sites-cloud/authoring/personalization/activities.md)은 사용 가능한 두 개의 타겟팅 엔진인 AEM과 Adobe Target 중 하나를 사용하도록 구성되어 있습니다.

타겟팅 엔진은 사용할 개인화 시스템을 결정하는 플랫폼 또는 메커니즘입니다.

현재 AEM에서는 다음을 사용할 수 있습니다.

* [AEM ContextHub](#aem-contexthub) (표준 AEM)
* [Adobe Target](#adobe-target) 개인화 엔진

>[!CAUTION]
>
>단일 AEM 페이지는 두 엔진을 동시에 사용할 수 없습니다.
>
>동일한 사이트 내의 별도 페이지에서 두 엔진을 모두 사용할 수 있습니다.

### AEM ContextHub {#aem-contexthub}

AEM에서는 페이지 요청을 처리하고 표시할 콘텐츠를 결정하는 내장 타겟팅 엔진 [ContextHub](/help/implementing/developing/personalization/contexthub.md)를 제공합니다. AEM 타겟팅 엔진을 사용하는 경우 경험의 대상자를 정의하기 위해 AEM에서 만들어진 세그먼트를 사용해야 하는 제한이 있습니다.

### Adobe Target {#adobe-target}

[Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md) 타겟팅 엔진을 사용하면 페이지 방문에서 수집된 정보가 Adobe Target에서 추적됩니다.

* 이 타겟팅 엔진을 사용하는 경우, Adobe Target에서 가져오는 세그먼트를 사용하여 경험의 대상자를 정의합니다.
* Adobe Target 엔진을 사용하는 활동은 [Target에 동기화](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target)됩니다.

[Adobe Target과 통합](/help/sites-cloud/integrating/integrating-adobe-target.md)한 경우 이 엔진을 사용할 수 있습니다.

## 개인화된 콘텐츠를 설정하는 방법 {#how-to-setup-personalized-content}

개인화된 콘텐츠를 제공하는 데 필요한 단계와 정의는 다양합니다.

1. 다음 중 하나를 통해 타겟팅 엔진을 설정합니다.

   1. [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md) 구성
   1. [Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)과 통합

1. 대상자를 구성합니다.

   1. 타겟팅 엔진에 따라 [타깃 대상자](https://experienceleague.adobe.com/docs/target/using/audiences/target.html) 또는 [ContextHub 세그먼트](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)와 함께 규칙을 정의합니다.

1. [브랜드 및 활동](/help/sites-cloud/authoring/personalization/activities.md)을 만듭니다.

1. 다양한 대상자에게 표시하고자 하는 각종 경험을 작성합니다.

1. 특정 대상자(세그먼트)에 대해 [타겟팅](/help/sites-cloud/authoring/personalization/targeted-content.md)하여 이러한 경험을 개인화합니다.