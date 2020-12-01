---
title: 컨텐츠 조각 만들기 헤드리스 빠른 시작 안내서
description: 컨텐츠 조각을 사용하면 AEM에서 헤드없이 전달할 수 있는 페이지 독립적인 컨텐츠를 디자인, 제작, 조정 및 사용할 수 있습니다.
translation-type: tm+mt
source-git-commit: 712a99095494ab333cf0ebb2ac9fffe3f5945f3b
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 2%

---


# 콘텐츠 조각 만들기 헤드리스 빠른 시작 안내서 {#creating-content-fragments}

컨텐츠 조각을 사용하면 AEM에서 헤드없이 전달할 수 있는 페이지 독립적인 컨텐츠를 디자인, 제작, 조정 및 사용할 수 있습니다.

## 컨텐츠 조각이란?{#what-are-content-fragments}

[콘텐츠 조각을 저장할 수 있는 ](create-assets-folder.md) 자산 폴더를 만들었으므로 이제 조각을 만들 수 있습니다.

컨텐츠 조각을 사용하면 페이지에 영향을 받지 않는 컨텐츠를 디자인, 제작, 조정 및 게시할 수 있습니다. 여러 위치 및 여러 채널에서 사용할 수 있는 컨텐츠를 준비할 수 있습니다.

콘텐츠 조각에는 구조화된 콘텐츠가 포함되어 있으며 JSON 형식으로 전달할 수 있습니다.

## 컨텐츠 조각 생성 방법 {#how-to-create-a-content-fragment}

컨텐츠 작성자는 제작한 컨텐츠를 나타내는 컨텐츠 조각을 수에 관계없이 만듭니다. 이것이 AEM에서 그들의 주된 업무가 될 것입니다. 이 시작 가이드의 목적을 위해 Adobe는 가이드를 제작하기만 하면 됩니다.

1. AEM에 Cloud Service으로 로그인하고 주 메뉴에서 **탐색 -> 자산**&#x200B;을 선택합니다.
1. 이전에 만든 [폴더를 탭하거나 클릭합니다.](create-assets-folder.md)
1. **만들기 -> 컨텐츠 조각**&#x200B;을 탭하거나 클릭합니다.
1. 컨텐츠 조각 생성은 두 가지 단계에서 마법사로 표시됩니다. 먼저 컨텐츠 조각을 만드는 데 사용할 모델을 선택하고 **다음**&#x200B;을 탭하거나 클릭합니다.
   * 사용 가능한 모델은 컨텐츠 조각을 만드는 자산 폴더](create-assets-folder.md)에 대해 정의한 [**클라우드 구성**&#x200B;에 따라 다릅니다.
   * `We could not find any models` 메시지가 표시되면 자산 폴더의 구성을 확인하십시오.

   ![컨텐츠 조각 모델 선택](../assets/content-fragment-model-select.png)
1. 필요한 경우 **제목**, **설명** 및 **태그**&#x200B;를 입력하고 **만들기**&#x200B;를 탭하거나 클릭합니다.

   ![컨텐츠 조각 만들기](../assets/content-fragment-create.png)
1. 확인 창에서 **열기**&#x200B;를 탭하거나 클릭합니다.

   ![컨텐츠 조각 생성 확인](../assets/content-fragment-confirmation.png)
1. 컨텐츠 조각 편집기에서 컨텐츠 조각 세부 정보를 제공합니다.

   ![컨텐츠 조각 편집기](../assets/content-fragment-edit.png)
1. **저장**&#x200B;을 탭하거나 클릭합니다.

컨텐츠 조각은 다른 컨텐츠 조각을 참조할 수 있으므로 필요한 경우 중첩된 컨텐츠 구조를 사용할 수 있습니다.

컨텐츠 조각은 AEM의 다른 에셋을 참조할 수도 있습니다. [참조하는 컨텐츠 조각을 만들기 전에 이러한 자산을 ](/help/assets/manage-digital-assets.md) AEM에 저장해야 합니다.

## 다음 단계 {#next-steps}

콘텐츠 조각을 만들었으므로 이제 시작 가이드의 마지막 부분으로 이동하고 [API 요청을 만들어 콘텐츠 조각에 액세스하고 전달할 수 있습니다.](create-api-request.md)

>!![TIP]
컨텐츠 조각 관리에 대한 자세한 내용은 [컨텐츠 조각 설명서](/help/assets/content-fragments/content-fragments.md)를 참조하십시오.
