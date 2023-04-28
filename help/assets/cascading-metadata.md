---
title: 연속 메타데이터
description: 이 문서에서는 자산에 대한 계단식 메타데이터를 정의하는 방법을 설명합니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 1d3ad496-a964-476e-b1da-4aa6d8ad53b7
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 14%

---

# 계단식 메타데이터 {#cascading-metadata}

자산의 메타데이터 정보를 캡처할 때 사용자는 사용 가능한 다양한 필드에 정보를 제공합니다. 다른 필드에서 선택한 옵션에 따라 특정 메타데이터 필드 또는 필드 값을 표시할 수 있습니다. 이러한 메타데이터 조건부 표시를 계단식 메타데이터라고 합니다. 즉, 특정 메타데이터 필드/값과 하나 이상의 필드 및/또는 해당 값 간에 종속성을 만들 수 있습니다.

메타데이터 스키마를 사용하여 계단식 메타데이터를 표시하는 규칙을 정의합니다. 예를 들어 메타데이터 스키마에 자산 유형 필드가 포함된 경우, 사용자가 선택하는 자산 유형에 따라 표시할 관련 필드 세트를 정의할 수 있습니다.

다음은 계단식 메타데이터를 정의할 수 있는 몇 가지 사용 사례입니다.

* 사용자 위치가 필요한 경우 사용자의 국가 및 상태 선택에 따라 관련 도시 이름을 표시합니다.
* 사용자의 제품 카테고리 선택 사항을 기반으로 하여 목록에서 관련 브랜드 이름을 로드합니다.
* 다른 필드에 지정된 값을 기반으로 특정 필드의 표시 여부를 전환합니다. 예를 들어, 사용자가 다른 주소로 선적이 배달되도록 하려면 별도의 운송 주소 필드를 표시합니다.
* 다른 필드에 지정된 값을 기준으로 필드를 필수로 지정합니다.
* 다른 필드에 지정된 값을 기준으로 특정 필드에 대해 표시되는 선택 사항을 변경합니다.
* 다른 필드에 지정된 값을 기반으로 특정 필드에 기본 메타데이터 값을 설정합니다.

## 에서 계단식 메타데이터 구성 [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

선택한 자산 유형에 따라 계단식 메타데이터를 표시하려는 시나리오를 생각해 보십시오. 몇 가지 예

* 비디오의 경우 형식, 코덱이나 지속 시간 등의 적용 가능한 필드를 표시합니다.
* Word 또는 PDF 문서의 경우 페이지 수, 작성자 등의 필드를 표시합니다.

선택한 자산 유형에 관계없이 저작권 정보를 필수 필드로 표시합니다.

1. 을 탭/클릭합니다. [!DNL Experience Manager] 로고로 이동하여 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 스키마]**.
1. In the **[!UICONTROL Schema Forms]** page, select a schema form and then tap/click **[!UICONTROL Edit]** from the toolbar to edit the schema.

   ![select_form](assets/select_form.png)

1. (선택 사항) 메타데이터 스키마 편집기에서 조건부 적용할 새 필드를 만듭니다. 에서 이름 및 속성 경로를 지정합니다. **[!UICONTROL 설정]** 탭.

   새 탭을 만들려면 탭하거나 클릭합니다 `+` 탭을 추가하고 메타데이터 필드를 추가합니다.

   ![add_tab](assets/add_tab.png)

1. 자산 유형에 대한 드롭다운 필드를 추가합니다. 에서 이름 및 속성 경로를 지정합니다. **[!UICONTROL 설정]** 탭. 선택적 설명을 추가합니다.

   ![asset_type_field](assets/asset_type_field.png)

1. 키-값 쌍은 양식 사용자에게 제공되는 옵션입니다. 수동으로 또는 JSON 파일에서 키-값 쌍을 제공할 수 있습니다.

   * 값을 수동으로 지정하려면 **[!UICONTROL 수동으로 추가]**, 탭/클릭 **[!UICONTROL 선택 추가]** 텍스트 및 값 옵션을 지정합니다. 예를 들어, 비디오, PDF, Word 및 이미지 자산 유형을 지정합니다.

   * JSON 파일에서 값을 동적으로 가져오려면 를 선택합니다 **[!UICONTROL JSON 경로를 통해 추가]** 및 는 JSON 파일의 경로를 제공합니다. [!DNL Experience Manager] 사용자에게 양식이 표시될 때 실시간으로 키-값 쌍을 가져옵니다.

   두 옵션 모두 함께 사용할 수 없습니다. JSON 파일에서 옵션을 가져오고 수동으로 편집할 수 없습니다.

   ![add_choice](assets/add_choice.png)

   >[!NOTE]
   >
   >JSON 파일을 추가할 때 키-값 쌍이 메타데이터 스키마 편집기에 표시되지 않지만 게시된 양식으로 사용할 수 있습니다.

   >[!NOTE]
   >
   >선택 사항을 추가할 때 팝업 필드를 클릭하면 인터페이스가 왜곡되고 선택 사항에 대한 삭제 아이콘이 작동하지 않습니다. 변경 사항을 저장할 때까지 드롭다운을 클릭하지 마십시오. 이 문제가 발생하면 스키마를 저장하고 다시 열어 편집을 계속합니다.

1. (선택 사항) 다른 필수 필드를 추가합니다. 예를 들어 자산 유형 비디오의 형식, 코덱과 지속 시간이 있습니다.

   마찬가지로, 다른 자산 유형에 대한 종속 필드를 추가합니다. 예를 들어 PDF 및 Word 파일과 같은 문서 자산에 대한 필드 페이지 카운트와 작성자를 추가합니다.

   ![video_dependent_fields](assets/video_dependent_fields.png)

1. 자산 유형 필드와 다른 필드 간에 종속성을 만들려면 종속 필드를 선택하고 을(를) 엽니다. **[!UICONTROL 규칙]** 탭.

   ![select_dependentfield](assets/select_dependentfield.png)

1. 아래 **[!UICONTROL 요구 사항]**&#x200B;을(를) 선택하고 을(를) 선택합니다. **[!UICONTROL 필수, 새 규칙 기반]** 선택 사항입니다.
1. Tap/click **[!UICONTROL Add Rule]** and choose the **[!UICONTROL Asset Type]** field to create a dependency. Also choose the field value upon which to create the dependency. In this case, choose **[!UICONTROL Video]**. Tap/click **[!UICONTROL Done]** to save the changes.

   ![define_rule](assets/define_rule.png)

   >[!NOTE]
   >
   >수동으로 사전 정의된 값이 있는 드롭다운을 규칙과 함께 사용할 수 있습니다. 구성된 JSON 경로가 있는 드롭다운 메뉴는 사전 정의된 값을 사용하여 조건을 적용하는 규칙과 함께 사용할 수 없습니다. 런타임 시 JSON에서 값이 로드되는 경우 사전 정의된 규칙을 적용할 수 없습니다.

1. Under **[!UICONTROL Visibility]**, choose the **[!UICONTROL Visible, based on new rule]** option.

1. Tap/click **[!UICONTROL Add Rule]** and choose the **[!UICONTROL Asset Type]** field to create a dependency. Also choose the field value upon which to create the dependency. In this case, choose **[!UICONTROL Video]**. Tap/click **[!UICONTROL Done]** to save the changes.

   ![define_visityrule](assets/define_visibilityrule.png)

   >[!CAUTION]
   >
   >값을 재설정하려면 공백 또는 값이 아닌 인터페이스의 아무 곳이나 클릭하거나 탭합니다. 값이 재설정되면 값을 다시 선택합니다.

   >[!NOTE]
   >
   >You can apply **[!UICONTROL Requirement]** condition and **[!UICONTROL Visibility]** condition independent of each other.

1. 마찬가지로 자산 유형 필드의 값 비디오와 코덱과 지속 시간 등의 다른 필드 간에 종속성을 만듭니다.
1. 다음 단계를 반복하여 문서 자산(PDF 및 Word) 간에 종속성을 만듭니다 [!UICONTROL 자산 유형] 필드 및 필드(예: ) [!UICONTROL 페이지 수] 및 [!UICONTROL 작성자].
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 폴더에 메타데이터 스키마를 적용합니다.

1. 메타데이터 스키마를 적용한 폴더로 이동하고 자산의 속성 페이지를 엽니다. 자산 유형 필드에서 선택한 내용에 따라 관련 계단식 메타데이터 필드가 표시됩니다.

   ![비디오 자산에 대한 계단식 메타데이터](assets/video_asset.png)
   *그림: 비디오 자산에 대한 계단식 메타데이터*

   ![문서 자산에 대한 계단식 메타데이터](assets/doc_type_fields.png)
   *그림: 문서 자산에 대한 계단식 메타데이터*

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)
