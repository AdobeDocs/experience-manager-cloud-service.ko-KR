---
title: 자산 폴더 헤드리스 빠른 시작 안내서 만들기
description: AEM 컨텐츠 조각 모델을 사용하여 헤드리스 컨텐츠의 기반인 컨텐츠 조각의 구조를 정의합니다.
exl-id: 9a156a17-8403-40fc-9bd0-dd82fb7b2235
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 자산 폴더 헤드리스 빠른 시작 안내서 {#creating-an-assets-folder} 만들기

AEM 컨텐츠 조각 모델을 사용하여 헤드리스 컨텐츠의 기반인 컨텐츠 조각의 구조를 정의합니다. 그런 다음 컨텐츠 조각이 자산 폴더에 저장됩니다.

##  자산 폴더란?{#what-is-an-assets-folder}

[향후 컨텐츠 조각에 ](create-content-model.md) 사용할 구조를 정의하는 컨텐츠 조각 모델을 만들었으므로 이제 일부 조각을 생성하게 되어 매우 기쁘게 생각할 수 있습니다.

하지만 먼저 저장할 자산 폴더를 만들어야 합니다.

자산 폴더는 이미지 및 비디오뿐만 아니라 컨텐츠 조각과 같은 기존 컨텐츠 자산](/help/assets/manage-digital-assets.md)을 구성하는 데 사용됩니다.[

## 자산 폴더를 만드는 방법 {#how-to-create-an-assets-folder}

관리자는 컨텐츠 작성과 동시에 컨텐츠를 구성하기 위해 가끔 폴더를 만들어야 합니다. 이 시작 안내서를 사용하려면 하나의 폴더만 만들면 됩니다.

1. AEM에 Cloud Service으로 로그인하고 기본 메뉴에서 **탐색 -> 자산 -> 파일**&#x200B;을 선택합니다.
1. **만들기 -> 폴더**&#x200B;를 탭하거나 클릭합니다.
1. 폴더에 **제목** 및 **이름**&#x200B;을 입력합니다.
   * **제목**&#x200B;은 설명적이어야 합니다.
   * **이름**&#x200B;은 저장소의 노드 이름이 됩니다.
      * 제목 기준 자동 생성되며 [AEM 이름 지정 규칙에 따라 조정됩니다.](/help/implementing/developing/introduction/naming-conventions.md)
      * 필요하면 조정할 수 있다.

   ![폴더 만들기](../assets/assets-folder-create.png)
1. 방금 만든 폴더를 선택한 다음 도구 모음에서 **속성**&#x200B;을 선택합니다(또는 `p` [키보드 단축키를 사용합니다.](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md))
1. **속성** 창에서 **Cloud Services** 탭을 선택합니다.
1. **클라우드 구성**&#x200B;에 대해 이전에 만든 [구성을 선택합니다.](create-configuration.md)

   ![자산 폴더 구성](../assets/assets-folder-configure.png)
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.
1. 확인 창에서 **확인**&#x200B;을 탭하거나 클릭합니다.

   ![확인 창](../assets/assets-folder-confirmation.png)

방금 만든 폴더 내에서 추가 하위 폴더를 만들 수 있습니다. 하위 폴더는 상위 폴더의 **클라우드 구성**&#x200B;을 상속합니다. 다른 구성에서 모델을 사용하려는 경우에는 이 값을 대체할 수 있습니다.

현지화된 사이트 구조를 사용하는 경우 새 폴더 아래에 [언어 루트](/help/assets/translate-assets.md)를 만들 수 있습니다.

## 다음 단계 {#next-steps}

컨텐츠 조각용 폴더를 만들었으므로 이제 시작 가이드의 네 번째 부분으로 이동하고 컨텐츠 조각을 [만들 수 있습니다.](create-content-fragment.md)

>[!TIP]
>
>컨텐츠 조각 관리에 대한 자세한 내용은 [컨텐츠 조각 설명서](/help/assets/content-fragments/content-fragments.md) 를 참조하십시오.
