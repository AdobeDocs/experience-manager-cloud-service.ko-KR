---
title: 관련 컨텐츠(Assets - 컨텐츠 조각)
description: AEM 콘텐츠 조각의 관련 콘텐츠 기능이 연결을 제공하여 조각과 함께 에셋을 선택적으로 사용할 수 있도록 하는 방법을 이해합니다.
exl-id: 8c8ad768-a210-4d34-bb47-2347599bcac9
feature: Content Fragments
role: User
solution: Experience Manager Sites
source-git-commit: 86a2c5f35d82010c84b74b6b5f0da09fd87c2b7a
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 44%

---

# 관련 콘텐츠{#associated-content}

Adobe Experience Manager의 콘텐츠 조각(AEM as a Cloud Service)의 경우 관련 콘텐츠 기능(원본 편집기에서 사용 가능)이 연결을 제공하여 에셋을 조각과 함께 선택적으로 사용할 수 있도록 합니다. 이렇게 하면 [콘텐츠 조각을 사용할 때 액세스할 수 있는 다양한 에셋을 제공](/help/assets/content-fragments/content-fragments.md#using-associated-content)하는 동시에 적절한 에셋을 검색하는 데 필요한 시간을 줄일 수 있으므로 유연성을 높일 수 있습니다. 이 기능은 Headless 콘텐츠 게재 및 페이지 작성 둘 다에 사용할 수 있습니다.

>[!NOTE]
>
>콘텐츠 조각은 Sites 기능이지만 **자산**&#x200B;으로 저장됩니다.
>
>콘텐츠 조각 작성에는 두 개의 편집기가 있습니다. 기본 기능은 동일하지만 몇 가지 차이점이 있습니다. 이 섹션에서는 주로 **Assets** 콘솔에서 액세스하는 원본 편집기에 대해 설명합니다.

## 관련 콘텐츠 추가 {#adding-associated-content}

>[!NOTE]
>
>[시각적 자산(예: 이미지)](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets)을 조각 및/또는 페이지에 추가하는 다양한 방법이 있습니다.

연결하려면 먼저 [미디어 자산을 컬렉션에 추가](/help/assets/manage-collections.md)해야 합니다. 이러한 작업을 마치면 다음과 같은 작업을 수행할 수 있습니다.

1. 조각을 열고 사이드 패널에서 **관련 콘텐츠**&#x200B;를 선택합니다.

   ![관련 콘텐츠](assets/cfm-assoc-content-01.png)

1. 컬렉션이 이미 연결되어 있는지 여부에 따라 다음 중 하나를 선택합니다.

   * **콘텐츠 연결** - 첫 번째 연결된 컬렉션입니다.
   * **컬렉션 연결** - 연결된 컬렉션이 구성되어 있는 경우 이 옵션을 선택합니다.

1. 필요한 컬렉션을 선택합니다.

   원할 경우 선택한 컬렉션에 조각 자체를 추가할 수도 있습니다. 이렇게 하면 추적에 유용합니다.

   ![컬렉션 선택](assets/cfm-assoc-content-02.png)

1. **선택**&#x200B;을 사용하여 확인합니다. 컬렉션이 연결된 것으로 표시됩니다.

   ![확인된 연결](assets/cfm-assoc-content-03.png)

## 관련 콘텐츠 편집 {#editing-associated-content}

컬렉션을 연결하면 다음 작업을 수행할 수 있습니다.

* 연결 **제거**
* 컬렉션에 **자산 추가**
* 추가 작업을 위한 자산 선택
* 자산 편집
