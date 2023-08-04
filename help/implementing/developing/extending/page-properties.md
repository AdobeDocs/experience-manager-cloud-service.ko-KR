---
title: 페이지 속성 보기 사용자 지정
description: 작성자가 페이지 속성을 보고 편집하는 방법을 알아봅니다.
source-git-commit: f159f0ef86c2b82da4e7308a0892b4947b6e43fb
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 4%

---


# 페이지 속성 보기 사용자 지정{#customizing-views-of-page-properties}

모든 페이지에는 [속성](/help/sites-cloud/authoring/fundamentals/page-properties.md) 를 보거나 편집할 수 있습니다. 일부는 페이지를 만들 때 필요하고(보기 만들기), 일부는 나중에 보고 편집할 수 있습니다(보기 편집). 이러한 페이지 속성은 대화 상자에서 정의하고 사용할 수 있습니다. (`cq:dialog`)을 클릭하여 제품에서 사용할 수 있습니다.

모든 페이지 속성의 기본 상태는 다음과 같습니다.

* 만들기 보기에서 숨겨짐(예: **페이지 만들기** wizard)

* 편집 보기에서 사용 가능(예: **속성 보기**)

변경이 필요한 경우 필드를 구체적으로 구성해야 합니다. 이 작업은 적절한 노드 속성을 사용하여 수행됩니다.

* 만들기 보기에서 사용할 수 있는 페이지 속성(예: **페이지 만들기** 마법사):

   * 이름: `cq:showOnCreate`
   * 유형: `Boolean`

* 편집 보기에서 사용할 수 있는 페이지 속성(예: ) **보기**/**편집**  **속성** 옵션:

   * 이름: `cq:hideOnEdit`
   * 유형: `Boolean`

>[!TIP]
>
>다음을 참조하십시오. [페이지 속성 확장 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) 페이지 속성 맞춤화에 대한 안내서입니다.

## 페이지 속성 구성 {#configuring-your-page-properties}

페이지 구성 요소의 대화 상자를 구성하고 적절한 노드 속성을 적용하여 사용 가능한 필드를 구성할 수도 있습니다.

예를 들어 기본적으로 [**페이지 만들기** 마법사](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) 아래에 그룹화된 필드를 표시합니다. **기타 제목 및 설명**. 이를 숨기려면 다음을 구성합니다.

1. 아래에 페이지 구성 요소 만들기 `/apps`.
1. 재정의 만들기(사용) *대화 상자 차이* 에서 제공 [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md))에 사용됩니다. `basic` 섹션(예: 페이지 구성 요소):

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

1. 설정 `path` 속성 `basic` 기본 탭의 재정의를 지정합니다(다음 단계도 참조). 예:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. 재정의 만들기 `basic` - `moretitles` 섹션에 있는 마지막 항목이 될 필요가 없습니다. 예:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. 적절한 노드 속성을 적용합니다.

   * **이름**: `cq:showOnCreate`
   * **유형**: `Boolean`
   * **값**: `false`

   다음 **기타 제목 및 설명** 섹션이 **페이지 만들기** 마법사.

>[!NOTE]
>
>라이브 카피에 사용할 페이지 속성을 구성할 때는 문서를 참조하십시오. [다중 사이트 관리자 확장](/help/implementing/developing/extending/msm.md#configuring-msm-locks-on-page-properties) 을 참조하십시오.

## 페이지 속성의 샘플 구성 {#sample-configuration-of-page-properties}

이 샘플은 대화 상자 비교 기술을 [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md) 의 사용을 포함한다 [`sling:orderBefore`](/help/implementing/developing/introduction/sling-resource-merger.md#properties). 또한 두 가지 사용 방법을 보여 줍니다 `cq:showOnCreate` 및 `cq:hideOnEdit`.

이 페이지의 코드는에서 찾을 수 있습니다. [GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
