---
title: 개인화 및 콘텐츠 타겟팅
description: AEM이 개인화된 콘텐츠를 만드는 방법
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
source-git-commit: 8b741b64db43369bf0ca3bfbe947fb58ef5ec05a
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 97%

---

# 개인화 및 콘텐츠 타겟팅 {#personalization}

## 개인화 및 콘텐츠 타겟팅 {#personalization-and-content-targeting}

AEM은 타겟팅된 콘텐츠를 작성하고 개인화된 환경을 제공하기 위한 도구 프레임워크를 제공합니다.

## 타겟팅 모드 {#targeting-mode}

AEM의 타겟팅 모드를 사용하여 [타겟팅된 콘텐츠를 작성](/help/sites-cloud/authoring/personalization/targeted-content.md)할 수 있습니다. 타겟팅 모드 및 타겟 구성 요소는 마케팅 활동의 경험을 위한 콘텐츠를 만드는 도구를 제공합니다.

## 활동 {#activities}

활동은 마케팅 노력을 정의하고 구성합니다. 활동은 타겟팅하는 대상과 타겟팅이 적용되는 기간으로 구성됩니다.

예를 들어 제품 카탈로그에 계절 상품에 집중하는 티저가 포함될 수 있습니다. 여름 스포츠 활동은 여름 기간 동안 티저가 타겟팅하는 마케팅 세그먼트를 정의합니다.

활동은 또한 페이지에서 사용하는 [타겟팅 엔진](#targeting-engine)을 식별합니다.

[활동 콘솔](/help/sites-cloud/authoring/personalization/activities.md)을 사용하여 브랜드를 위한 활동을 만들고 관리할 수 있습니다. [타겟팅된 콘텐츠를 작성](/help/sites-cloud/authoring/personalization/targeted-content.md)할 때 활동을 만들 수도 있습니다.

## 경험 {#experiences}

각 활동에 대해 타겟팅하는 대상자를 식별하는 경험을 하나 이상 정의합니다. AEM에서는 각 경험을 구성하는 콘텐츠를 제어할 수 있습니다.

대상은 AEM이나 Adobe Target에서 만들어진 마케팅 세그먼트를 기반으로 합니다. 방문자가 웹 페이지를 열면 페이지의 논리 시스템은 방문자가 속한 대상을 판별하고 해당 대상을 위해 만든 콘텐츠를 표시합니다.

예를 들어 한 활동은 30세 이상의 여성과 30세 미만의 여성, 이렇게 두 개의 서로 다른 대상자를 위한 경험들을 정의하며, 웹 사이트의 여성용 페이지에 각 경험에 대해 서로 다른 제품을 표시할 수 있습니다.

활동을 위한 경험을 정의합니다. [활동 콘솔](/help/sites-cloud/authoring/personalization/activities.md#adding-editing-an-activity-using-the-activities-console)이나 [타겟팅 모드](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode)를 사용하여 활동에 경험을 추가할 수 있습니다.

## 오퍼 {#offers}

오퍼는 경험을 위한 페이지에서 위치에 나타나는 콘텐츠입니다. 서로 다른 경험에 대해 서로 다른 오퍼를 사용하여 대상을 위한 콘텐츠의 효과를 극대화하십시오.

예를 들어 샘플 웹 페이지의 여성용 페이지는 페이지 상단에 표시되는 티저 이미지와 같은 오퍼를 사용할 수 있습니다. 다른 오퍼가 30 이상 여성 경험과 30 미만 여성 경험을 위한 티저로 사용될 수 있습니다.

사용 [경험 조각](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment) 여러 경험에서 사용할 수 있는 오퍼를 만들려면 [타겟팅된 콘텐츠를 작성](/help/sites-cloud/authoring/personalization/targeted-content.md)할 때 단일 사용 오퍼를 만들거나 오퍼 라이브러리의 오퍼를 추가하십시오.

<!--
Use the [Offers console](/help/sites-cloud/authoring/personalization/offers.md) to create offers that you can use in multiple experiences. Create single-use offers or add offers from an offer library when [authoring targeted content](/help/sites-cloud/authoring/personalization/targeted-content.md).
-->

## 타겟팅 엔진 {#targeting-engine}

타겟팅 엔진은 타겟팅된 콘텐츠에 대한 논리를 실행하는 메커니즘입니다. [활동](/help/sites-cloud/authoring/personalization/activities.md)은 사용 가능한 두 개의 타겟팅 엔진인 AEM과 Adobe Target 중 하나를 사용하도록 구성되어 있습니다.

### AEM {#aem}

AEM에서는 페이지 요청을 처리하고 표시할 콘텐츠를 결정하는 내장 타겟팅 엔진을 제공합니다. AEM 타겟팅 엔진을 사용하는 경우 경험의 대상을 정의하기 위해 AEM에서 만들어진 세그먼트를 사용해야 하는 제한이 있습니다.

### Adobe Target {#adobe-target}

Adobe Target 타겟팅 엔진을 사용하면 페이지 방문에서 수집된 정보가 Adobe Target에서 추적됩니다.

* 이 타겟팅 엔진을 사용하는 경우, Adobe Target에서 가져오는 세그먼트를 사용하여 경험의 대상을 정의합니다.
* Adobe Target 엔진을 사용하는 활동은 [Target에 동기화](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target)됩니다.

Adobe Target과 통합한 경우 이 엔진을 사용할 수 있습니다. <!--You can use this engine when you have [integrated with Adobe Target](/help/sites-administering/opt-in.md).-->
