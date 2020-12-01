---
title: 자산 폴더 헤드리스 빠른 시작 안내서 만들기
description: 컨텐츠 조각 모델은 컨텐츠 조각 구조를 정의합니다. 그런 다음 컨텐츠 조각은 자산 폴더에 저장됩니다.
translation-type: tm+mt
source-git-commit: 9c801af38142434a5a0302b73b6fc1469a0eaab2
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# 자산 폴더 헤드리스 빠른 시작 안내서 만들기{#creating-an-assets-folder}

컨텐츠 조각 모델은 컨텐츠 조각 구조를 정의합니다. 그런 다음 컨텐츠 조각은 자산 폴더에 저장됩니다.

##  자산 폴더란?{#what-is-an-assets-folder}

[향후 컨텐츠 조각에 사용할 구조를 정의하는 컨텐츠 조각 ](create-content-model.md) 모델을 만들었으므로 일부 조각을 만드는 것이 매우 흥분될 것입니다.

그러나 먼저 에셋 폴더를 저장할 에셋 폴더를 만들어야 합니다.

자산 폴더는 이미지 및 비디오와 같은 기존 컨텐츠 자산[과(와) 콘텐츠 조각을 구성하는 데 사용됩니다.](/help/assets/manage-digital-assets.md)

## 자산 폴더 {#how-to-create-an-assets-folder}를 만드는 방법

관리자가 컨텐츠를 만들 때 가끔 폴더를 만들어야 합니다. 이 시작 안내서의 경우 하나의 폴더만 만들어야 합니다.

1. AEM에 Cloud Service으로 로그인하고 주 메뉴에서 **탐색 -> 자산 -> 파일**&#x200B;을 선택합니다.
1. **만들기 -> 폴더**&#x200B;를 탭하거나 클릭합니다.
1. 폴더에 **제목**&#x200B;과 **이름**&#x200B;을 제공합니다.
   * **제목**&#x200B;은 설명적이어야 합니다.
   * **이름**&#x200B;은 저장소의 노드 이름이 됩니다.
      * 제목에 따라 자동으로 생성되고 [AEM 명명 규칙에 따라 조정됩니다.](/help/implementing/developing/introduction/naming-conventions.md)
      * 필요한 경우 조정할 수 있습니다.

   ![폴더 만들기](../assets/assets-folder-create.png)
1. 방금 만든 폴더를 선택한 다음 도구 모음에서 **속성**&#x200B;을 선택합니다(또는 `p` [키보드 단축키 사용](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)).
1. **속성** 창에서 **Cloud Services** 탭을 선택합니다.
1. **클라우드 구성**&#x200B;에 대해 이전에 만든 [구성을 선택합니다.](create-configuration.md)

   ![자산 폴더 구성](../assets/assets-folder-configure.png)
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.
1. 확인 창에서 **OK**&#x200B;을 탭하거나 클릭합니다.

   ![확인 창](../assets/assets-folder-confirmation.png)

방금 만든 폴더 내에 하위 폴더를 추가로 만들 수 있습니다. 하위 폴더는 상위 폴더의 **클라우드 구성**&#x200B;을 상속받게 됩니다. 다른 구성의 모델을 사용하려는 경우에는 이 값을 무시할 수 있습니다.

현지화된 사이트 구조를 사용하는 경우 새 폴더 아래에 언어 루트[를 만들 수 있습니다.](/help/assets/translate-assets.md)

## 다음 단계 {#next-steps}

콘텐츠 조각에 대한 폴더를 만들었으므로 이제 시작 안내서의 네 번째 부분으로 이동하고 [콘텐츠 조각 만들기](create-content-fragment.md)

>!![TIP]
컨텐츠 조각 관리에 대한 자세한 내용은 [컨텐츠 조각 설명서](/help/assets/content-fragments/content-fragments.md)를 참조하십시오.
