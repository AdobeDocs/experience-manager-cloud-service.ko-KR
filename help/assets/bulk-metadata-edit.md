---
title: Assets 보기에서 벌크 메타데이터 편집
description: Assets 보기에서 사용 가능한 여러 에셋의 메타데이터를 동시에 편집하는 방법에 대해 알아봅니다.
source-git-commit: 5778d0dac141174c1b950625057f920af0301a8b
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Assets 보기에서 벌크 메타데이터 편집{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

Assets 보기 UI에서 **일괄 메타데이터 편집**&#x200B;을 사용하면 여러 에셋 파일에 대한 메타데이터를 동시에 수정할 수 있습니다. 각 에셋에 대한 메타데이터를 개별적으로 편집하는 대신, 한 번에 큰 에셋 그룹에 변경 사항을 적용합니다. 이 기능은 대규모 에셋 세트에서 메타데이터 속성의 효율성, 일관성 및 정확성을 향상시켜 에셋 검색 및 구성을 향상시킵니다.

## 자산 메타데이터 벌크 편집 {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

다음 단계를 실행하여 여러 에셋의 메타데이터를 한 번에 일괄 편집합니다.

1. Assets 보기에서 **Assets**&#x200B;를 클릭합니다.
1. 에셋을 찾아보거나 검색 막대에 관련 키워드를 입력하여 특정 에셋을 찾습니다.
1. 여러 자산을 선택하고 상단 메뉴에서 **일괄 메타데이터 편집**을 클릭합니다.
   ![일괄 메타데이터 편집](/help/assets/assets/bulk-metadata-edit.png)
1. 메타데이터 편집 페이지에서 **속성** 패널에서 다음 필드를 편집합니다.
   * **상태:** 선택한 자산의 사용 가능성을 정의할 상태를 선택합니다.
   * **만료 날짜:** 자산이 더 이상 유효하지 않거나 필요하지 않은 날짜를 설정합니다.
   * **작성자:** 작성자 이름을 지정합니다.
   * **키워드:** 검색 기능을 향상시키기 위해 자산에 대한 높은 수준의 정보를 제공하는 용어나 텍스트 문자열을 추가합니다. 키워드를 추가하고 Enter 키를 누르거나 Return 키를 눌러 목록에 다른 키워드를 추가합니다.
     <!-- * **Tags:** Click ![tags icon](/help/assets/assets/tags-icon.svg) to select tags from the available options. Tags provide more specific information about the assets and enhances their discoverability. Tags already applied to the selected assets are only displayed in the **Properties** panel. If you cannot find the relevant tags, create the tags and assign them to the selected assets. See [Manage tags in Assets view](/help/assets/tagging-management-assets-view.md) for details.-->
   * **저장**&#x200B;을 클릭하여 키워드를 추가하고 <!-- Tags while-->은(는) 상태, 만료 날짜 및 작성자에 대한 기존 세부 정보를 재정의합니다.
     ![save-bulk-metadata-edit-properties](/help/assets/assets/save-bulk-metadata-edit-properties1.png)

     >[!NOTE]
     >
     >한 번에 100개의 에셋의 메타데이터를 편집할 수 있습니다.

에셋에 적용된 메타데이터 변경 내용을 보려면 에셋 세부 정보 페이지로 이동하고(에셋을 선택하고 **세부 정보**&#x200B;을 클릭) ![](/help/assets/assets/info-icon-solid-black.svg)을(를) 클릭하여 **정보** 패널에서 에셋의 메타데이터를 확인합니다.

>[!NOTE]
>
>상태, 만료 날짜, 작성자 및 키워드 <!-- and Tags-->은(는) 폴더별 메타데이터와 관계없이 일괄 메타데이터 편집에 사용할 수 있는 표준 메타데이터 속성입니다. 이러한 메타데이터 속성은 에셋의 폴더에 적용된 메타데이터 양식에 포함된 경우에만 에셋 세부 정보 페이지에 표시됩니다.  에셋 세부 정보 페이지에서 이러한 메타데이터 속성이 표시되지 않으면 에셋 폴더의 메타데이터 양식을 편집하여 이러한 속성을 포함하십시오. 메타데이터 양식을 만들거나 편집하고 폴더에 적용하는 방법에 대해 알아보려면 [Assets 보기의 메타데이터](/help/assets/metadata-assets-view.md)를 참조하십시오.


