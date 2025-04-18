---
title: 오퍼 생성 및 관리(오퍼 콘솔)
description: 오퍼 콘솔을 사용하여 활동 경험에서 사용할 수 있는 오퍼를 생성하십시오.
exl-id: 81d2fda2-06a9-48f6-820a-dd9e11d94fcc
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 82%

---

# 오퍼 생성 및 관리(오퍼 콘솔) {#creating-and-managing-offers}

**오퍼** 콘솔은 향후에 더 이상 사용되지 않습니다. 따라서 앞으로 이 콘솔에는 다음이 적용됩니다.

* *레거시* 오퍼가 이미 정의된(기존) 고객만 사용 가능
* 이러한 레거시 오퍼는 경험 조각 오퍼로 변환하는 것이 좋음
   * 마지막 레거시 오퍼가 변환/제거되는 즉시 **오퍼** 콘솔을 더 이상 사용할 수 없습니다.

![개인화 콘솔](/help/sites-cloud/authoring/assets/offers-consoles.png)

>[!NOTE]
>
>기존 레거시 오퍼가 있는 고객은 **오퍼** 콘솔을 계속 사용하여 기존 오퍼를 확인하고 새 레거시 오퍼를 만들 수 있습니다.
>
>기존 레거시 오퍼가 없는 고객에게는 **오퍼** 콘솔이 표시되지 않습니다.
>
>모든 고객은 **경험 조각 오퍼**&#x200B;를 사용하여 오퍼를 만들고 관리할 수 있습니다.

## 레거시 오퍼를 경험 조각으로 변환 {#convert-legacy-offer-to-experience-fragment}

레거시 제안을 경험 조각으로 변환하는 데 도움이 되도록 **경험 조각 변형으로 변환** 옵션 및 워크플로가 구현되었습니다.

>[!NOTE]
>
>레거시 오퍼를 경험 조각으로 전환하는 데 권장되는 워크플로입니다.

>[!NOTE]
>
>경험 조각을 직접 만들고 레거시 오퍼의 콘텐츠를 조각으로 수동으로 전송한 다음 레거시 오퍼를 삭제할 수도 있습니다.

>[!CAUTION]
>
>**경험 조각 변형으로 변환** 옵션은 모든 핵심 구성 요소에 사용할 수 있습니다.
>
>이 옵션은 사용자 정의 구성 요소에 대해서는 지원되지 않습니다. 이러한 구성 요소의 경우 콘텐츠를 경험 조각으로 수동 변환해야 합니다.

>[!CAUTION]
>
>마지막 레거시 오퍼가 변환/제거되는 즉시 다음이 적용됩니다.
>
>* **오퍼** 콘솔을 더 이상 사용할 수 없습니다.
>* 영향을 받는 다른 구성 요소의 도구 모음에 있는 타겟 아이콘이 더 이상 나타나지 않습니다.

1. 편집할 오퍼가 포함된 페이지를 엽니다.

1. 해당 페이지의 **타겟팅** 모드로 전환합니다.

1. **타겟팅 시작**&#x200B;을 선택합니다.

1. 적절한(타겟팅된) 구성 요소를 선택합니다.

1. 구성 요소 도구 모음을 통해 **경험 조각 변형으로 변환** 옵션을 사용할 수 있습니다.

   ![레거시 오퍼를 경험 조각으로 변환](/help/sites-cloud/authoring/assets/offers-convert-legacy-icon.png)

1. 대화 상자가 표시됩니다. 여기에서 필요한 **작업**&#x200B;을 선택할 수 있습니다.

   * 새로운 경험 조각 만들기
   * 기존 경험 조각에 콘텐츠 추가

   이 시나리오에서는 **새 경험 조각 만들기**&#x200B;를 선택합니다.

   ![경험 조각 변형으로 변환 대화 상자](/help/sites-cloud/authoring/assets/offers-convert-dialog.png)

1. 대화 상자에서 필수 필드를 완료합니다.

   * **상위 경로**
새 경험 조각의 상위 경로 지정
   * **템플릿**
경험 조각을 만드는 데 사용할 템플릿을 선택합니다.
   * **조각 제목**
제목을 지정합니다.
   * **조각 태그**
필요한 경우 태그를 추가합니다.

1. **완료**&#x200B;를 선택하여 확인합니다.

   이제 **경험 조각 오퍼** 콘솔로 이동하면 새 경험 조각과 관련 변형을 볼 수 있습니다.

### 오퍼 템플릿으로 타겟팅 {#targeting-offers-template}

>[!CAUTION]
>
>이 옵션은 기존 레거시 오퍼가 있는 고객만 사용할 수 있습니다.
>
>**오퍼** 콘솔은 다음 경우에 더 이상 사용할 수 없습니다.
>
>* 마지막 레거시 오퍼가 경험 조각으로 변환된 후
>* 레거시 오퍼가 (향후) 더 이상 사용되지 않는 경우
>
>따라서 권장 옵션은 이 옵션이 아닌 경험 조각을 사용하는 것입니다.

기존 레거시 오퍼가 있는 고객의 경우, 경험 조각이 **아닌** 구성 요소를 타겟팅할 때 **오퍼 템플릿 사용** 옵션이 표시됩니다.

![경험 조각 변형으로 변환 대화 상자](/help/sites-cloud/authoring/assets/offers-legacy-target-non-experience-fragment.png)

## 오퍼 콘솔 {#offers-console}

>[!CAUTION]
>
>이 콘솔은 콘텐츠를 개인화하는 레거시 방식을 제공하므로 향후 사용되지 않습니다.
>
>이와 관련해 대비할 시간이 있습니다. [기존 레거시 오퍼를 경험 조각 오퍼로 변환](#convert-legacy-offer-to-experience-fragment)하는 방법을 참조하십시오.

오퍼 콘솔을 사용하여 [활동 경험에서 사용](/help/sites-cloud/authoring/personalization/targeted-content.md)할 수 있는 오퍼를 생성하십시오. 여러 경험에 동일한 오퍼가 필요할 때 오퍼 콘솔에서 오퍼를 생성하면 시간이 절약됩니다.

* 라이브러리에서 오퍼를 한 번 만든 다음 브랜드 활동의 여러 가지 경험에 활용할 수 있습니다.
* 라이브러리에서 오퍼를 변경하고 변경 사항은 오퍼를 사용하는 모든 경험에 영향을 줍니다.

오퍼 콘솔은 브랜드별로 오퍼를 체계적으로 구성합니다. 각 브랜드에는 브랜드의 경험에서 사용할 수 있는 오퍼 라이브러리가 포함되어 있습니다. 폴더를 사용하여 각 라이브러리에 오퍼를 구성하기 위한 계층 구조를 정의합니다. 논리 폴더 구조를 사용하면 찾아보기를 통해 오퍼를 쉽게 찾을 수 있습니다. 또한 태그 지정 및 검색 도구를 사용해도 오퍼를 찾을 수 있습니다.

### 오퍼 콘솔을 사용한 브랜드 추가 {#add-a-brand-using-the-offers-console}

오퍼가 연결된 브랜드를 만드십시오. 폴더 및 오퍼를 만들 수 있는 오퍼 라이브러리에 액세스하려면 오퍼 콘솔에서 브랜드를 여십시오.

오퍼 콘솔을 사용하여 브랜드를 만들면 브랜드를 위한 활동을 추가하고 관리할 수 있는 [활동 콘솔](/help/sites-cloud/authoring/personalization/activities.md)에도 표시됩니다.

1. 탐색 콘솔에서 **Personalization** > **오퍼**&#x200B;를 선택합니다.

   ![오퍼 콘솔로 이동](/help/sites-cloud/authoring/assets/offers-navigation.png)

1. **만들기**&#x200B;를 선택한 다음 **만들기** **브랜드**&#x200B;를 선택하십시오.
1. 브랜드 템플릿을 선택하고 **다음**&#x200B;을(를) 선택합니다.
1. 오퍼 콘솔과 활동 콘솔에 표시할 브랜드의 제목을 입력합니다. 원할 경우, 브랜드와 연결할 태그를 하나 이상 입력하거나 선택합니다.
1. **만들기**&#x200B;를 선택합니다.

### 오퍼 라이브러리에 폴더 추가 {#add-a-folder-to-an-offer-library}

브랜드의 오퍼 라이브러리에 오퍼를 체계적으로 구성하고 저장할 폴더를 추가하십시오. 브랜드나 다른 폴더 아래에 폴더를 만들 수 있습니다.

1. 오퍼 콘솔에서 폴더를 만들 위치를 엽니다. 예를 들어 브랜드를 열어 최상위 수준 폴더를 만들거나, 라이브러리에서 다른 폴더를 여십시오.
1. **만들기** > **폴더 또는 오퍼 만들기**&#x200B;를 선택합니다.

   ![오퍼 폴더 만들기](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. **폴더**&#x200B;를 선택하고 **다음**&#x200B;을 클릭합니다.
1. 오퍼 라이브러리에 표시할 폴더의 제목을 입력하고 태그를 입력하거나 선택합니다.

   ![폴더 속성 정의](/help/sites-cloud/authoring/assets/offers-folder-properties.png)

1. **만들기**&#x200B;를 선택합니다.

### 오퍼 라이브러리에 오퍼 추가 {#add-an-offer-to-an-offer-library}

브랜드의 경험에 추가할 수 있도록 브랜드의 오퍼 라이브러리에 오퍼를 추가하십시오. 오퍼를 추가할 때 제목을 입력합니다. 더 잘 검색할 수 있도록 오퍼를 하나 이상의 태그와 연결할 수도 있습니다.

오퍼를 만든 후에는 열어서 콘텐츠를 작성할 수 있습니다.

1. 오퍼 콘솔에서 오퍼를 만들 위치를 엽니다. 예를 들어 브랜드를 열어 최상위 수준 오퍼를 만들거나, 라이브러리에서 폴더를 여십시오.
1. **만들기** > **폴더 또는 오퍼 만들기**&#x200B;를 선택합니다.

   ![오퍼 폴더 만들기](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. **오퍼 페이지** 템플릿을 선택한 후 **다음**&#x200B;을 선택합니다.
1. 오퍼의 제목을 입력하고 선택적으로 오퍼와 연결할 태그를 하나 이상 선택하거나 입력한 다음 **만들기**&#x200B;를 선택합니다.
1. 확인 대화 상자에서 편집할 오퍼를 열려면 **페이지 열기**&#x200B;를 선택합니다.

### 오퍼 편집 {#editing-an-offer}

오퍼를 열고 오퍼를 사용하는 경험에 표시할 콘텐츠를 편집하십시오. 경험에 사용되는 오퍼를 편집하면 변경 내용이 경험에 표시됩니다.

오퍼 라이브러리의 폴더 또는 검색 결과에서 오퍼를 열 수 있습니다. 오퍼를 사용하는 경험에서 오퍼를 열 수도 있습니다.

1. 오퍼 콘솔에서 오퍼 옆에 있는 아이콘을 선택하고 **편집**&#x200B;을 선택합니다.
1. 오퍼에 구성 요소를 추가하고 구성 요소 콘텐츠를 평소대로 편집합니다.

### 오퍼 삭제 {#deleting-an-offer}

더 이상 필요하지 않은 오퍼는 삭제하십시오. 경험에 사용된 오퍼에 대해 삭제를 시도하면 삭제할 것인지 확인하는 메시지가 표시됩니다. 확인하면 오퍼가 삭제되고 경험에서도 제거됩니다.

오퍼 라이브러리의 폴더 콘텐츠나 검색 결과를 볼 때 오퍼를 삭제할 수 있습니다.

1. 오퍼 콘솔에서 오퍼 옆에 있는 아이콘을 선택하고 **삭제**&#x200B;를 선택합니다.

   오퍼를 선택하고 **삭제**&#x200B;를 선택합니다.

1. 대화 상자가 나타나면 **삭제**&#x200B;를 선택하여 삭제를 확인합니다.
1. 오퍼가 하나 이상의 경험에서 사용되는 경우 오퍼가 참조되고 있음을 나타내는 대화 상자가 표시됩니다.

   * 오퍼를 삭제하고 경험에서 제거하려면 **강제 삭제**&#x200B;를 선택하세요.
   * 오퍼를 유지하려면 **취소**&#x200B;를 선택하세요.

### 오퍼 검색 {#searching-for-offers}

제목과 일치하는 키워드를 사용하여 임의 브랜드의 오퍼를 검색하십시오.

![오퍼 검색](/help/sites-cloud/authoring/assets/offers-search.png)

현재 검색 기준은 검색 결과 옆에 표시됩니다. 결과를 열을 사용하여 오름차순 또는 내림차순으로 정렬할 수도 있습니다. 오퍼 라이브러리의 어떤 폴더에서든 검색을 수행할 수 있습니다. 검색 결과는 현재 폴더에 상관없이 동일합니다.

오퍼를 검색하려면 다음 작업을 수행하십시오.

1. 오퍼 콘솔의 맨 위에서 확대경 아이콘을 선택합니다. 기본적으로 검색은 오퍼로 제한됩니다.
1. 오퍼를 검색할 키워드를 입력합니다. 결과에서 선택하십시오.
