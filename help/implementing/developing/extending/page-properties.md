---
title: 페이지 속성 보기 사용자 정의
description: 작성자가 페이지 속성을 보고 편집하는 방법에 대해 알아봅니다.
exl-id: 363b3c2d-f965-485f-bdae-2ea5b4cecb83
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 92%

---

# 페이지 속성 보기 사용자 정의{#customizing-views-of-page-properties}

모든 페이지에는 사용자가 보고 편집할 수 있는 [속성](/help/sites-cloud/authoring/sites-console/page-properties.md) 세트가 있습니다. 일부는 페이지를 만들 때 필요하며(만들기 보기), 일부는 나중에 보고 편집할 수 있습니다(편집 보기). 이러한 페이지 속성은 해당 페이지 구성 요소의 대화 상자(`cq:dialog`)를 통해 정의하고 제공합니다.

모든 페이지 속성의 기본 상태는 다음과 같습니다.

* 만들기 보기(예: **페이지 만들기** 마법사)에서는 숨겨짐

* 편집 보기(예: **속성 보기**)에서 사용 가능

변경이 필요한 경우 필드를 구체적으로 구성해야 합니다. 이는 적절한 노드 속성을 사용하여 수행됩니다.

* 만들기 보기(예: **페이지 만들기** 마법사)에서 사용할 수 있는 페이지 속성:

   * 이름: `cq:showOnCreate`
   * 유형: `Boolean`

* **속성** **보기**/**편집** 옵션과 같은 편집 보기에서 사용할 수 있는 페이지 속성:

   * 이름: `cq:hideOnEdit`
   * 유형: `Boolean`

>[!TIP]
>
>페이지 속성을 사용자 정의하는 방법에 대한 안내서는 [페이지 속성 확장 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html?lang=ko-KR)을 참조하십시오.

## 페이지 속성 구성 {#configuring-your-page-properties}

페이지 구성 요소의 대화 상자를 구성하고 적절한 노드 속성을 적용하여 사용 가능한 필드를 구성할 수도 있습니다.

예를 들어 기본적으로 [**페이지 만들기** 마법사](/help/sites-cloud/authoring/sites-console/creating-pages.md#creating-a-new-page)에는 **기타 제목 및 설명** 아래에 그룹화된 필드가 표시됩니다. 이를 숨기려면 다음과 같이 구성하십시오.

1. `/apps` 아래에서 페이지 구성 요소를 만듭니다.
1. 페이지 구성 요소의 `basic` 섹션에 대해 재정의를 만듭니다([Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md)에서 제공되는 *대화 상자 비교* 사용). 예를 들면 다음과 같습니다.

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

1. `basic`의 `path` 속성이 기본 탭의 재정의를 가리키도록 설정합니다(다음 단계도 참조). 예:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. 해당 경로에서 `basic` - `moretitles` 섹션의 재정의를 만듭니다. 예를 들면 다음과 같습니다.

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. 적절한 노드 속성을 적용합니다.

   * **이름**: `cq:showOnCreate`
   * **유형**: `Boolean`
   * **값**: `false`

   **기타 제목 및 설명** 섹션이 더 이상 **페이지 만들기** 마법사에 표시되지 않습니다.

>[!NOTE]
>
>라이브 카피에 사용할 페이지 속성을 구성할 때 자세한 내용은 [다중 사이트 관리자 확장](/help/implementing/developing/extending/msm.md#configuring-msm-locks-on-page-properties)을 참조하십시오.

## 페이지 속성의 샘플 구성 {#sample-configuration-of-page-properties}

이 샘플은 [`sling:orderBefore`](/help/implementing/developing/introduction/sling-resource-merger.md#properties) 사용을 포함하여 [Sling 리소스 병합](/help/implementing/developing/introduction/sling-resource-merger.md)의 대화 상자 비교 기법을 보여 줍니다. 또한 `cq:showOnCreate` 및 `cq:hideOnEdit` 모두의 사용을 보여 줍니다.

[GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)에서 이 페이지의 코드를 찾을 수 있습니다.
