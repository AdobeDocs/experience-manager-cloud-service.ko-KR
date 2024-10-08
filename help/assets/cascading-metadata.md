---
title: 연속 메타데이터
description: 이 문서에서는 에셋의 계단식 메타데이터를 정의하는 방법에 대해 설명합니다.
contentOwner: AG
feature: Metadata
role: Admin, User
exl-id: 1d3ad496-a964-476e-b1da-4aa6d8ad53b7
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 8%

---

# 계단식 메타데이터 {#cascading-metadata}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

에셋의 메타데이터 정보를 캡처할 때, 사용자는 다양한 이용 가능한 필드들의 정보를 제공한다. 특정 메타데이터 필드나 다른 필드에서 선택한 옵션에 따라 달라지는 필드 값을 표시할 수 있습니다. 이러한 메타데이터의 조건부 표시를 계단식 메타데이터라고 합니다. 즉, 특정 메타데이터 필드/값과 하나 이상의 필드 및/또는 해당 값 사이에 종속성을 만들 수 있습니다.

메타데이터 스키마를 사용하여 계단식 메타데이터를 표시하는 규칙을 정의합니다. 예를 들어 메타데이터 스키마에 에셋 유형 필드가 포함된 경우 사용자가 선택하는 에셋 유형에 따라 표시할 관련 필드 세트를 정의할 수 있습니다.

다음은 계단식 메타데이터를 정의할 수 있는 몇 가지 사용 사례입니다.

* 사용자 위치가 필요한 경우 사용자의 국가 및 주 선택에 따라 관련 도시 이름을 표시합니다.
* 사용자가 선택한 제품 범주에 따라 목록에 관련 브랜드 이름을 로드합니다.
* 다른 필드에 지정된 값을 기준으로 특정 필드의 가시성을 전환합니다. 예를 들어 사용자가 다른 주소로 배송을 배송하려는 경우 별도의 배송 주소 필드를 표시합니다.
* 다른 필드에 지정된 값을 기준으로 필드를 필수 항목으로 지정합니다.
* 다른 필드에 지정된 값을 기준으로 특정 필드에 표시되는 옵션을 변경합니다.
* 다른 필드에 지정된 값을 기반으로 특정 필드의 기본 메타데이터 값을 설정합니다.

## [!DNL Experience Manager]에서 계단식 메타데이터 구성 {#configure-cascading-metadata-in-aem}

선택한 에셋 유형에 따라 계단식 메타데이터를 표시할 시나리오를 생각해 보십시오. 몇 가지 예

* 비디오의 경우 형식, 코덱, 지속 시간 등과 같은 적용 가능한 필드를 표시합니다.
* Word 또는 PDF 문서의 경우 페이지 수, 작성자 등과 같은 필드를 표시합니다.

선택한 에셋 유형에 관계없이 저작권 정보를 필수 필드로 표시합니다.

1. [!DNL Experience Manager] 로고를 선택하고 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**(으)로 이동합니다.
1. **[!UICONTROL 스키마 Forms]** 페이지에서 스키마 양식을 선택한 다음 도구 모음에서 **[!UICONTROL 편집]**&#x200B;을 선택하여 스키마를 편집합니다.

   ![select_form](assets/select_form.png)

1. (선택 사항) 메타데이터 스키마 편집기에서 조건화할 필드를 만듭니다. **[!UICONTROL 설정]** 탭에서 이름 및 속성 경로를 지정하십시오.

   탭을 만들려면 `+`을(를) 선택하여 탭을 추가한 다음 메타데이터 필드를 추가합니다.

   ![add_tab](assets/add_tab.png)

1. 에셋 유형에 대한 드롭다운 필드를 추가합니다. **[!UICONTROL 설정]** 탭에서 이름 및 속성 경로를 지정하십시오. 선택적 설명을 추가합니다.

   ![asset_type_field](assets/asset_type_field.png)

1. 키-값 쌍은 양식 사용자에게 제공되는 옵션입니다. 키-값 쌍을 수동으로 또는 JSON 파일에서 제공할 수 있습니다.

   * 값을 수동으로 지정하려면 **[!UICONTROL 수동으로 추가]**&#x200B;를 선택하고 **[!UICONTROL 선택 항목 추가]**&#x200B;를 선택한 다음 옵션 텍스트와 값을 지정하십시오. 예를 들어 비디오, PDF, Word 및 Image 에셋 유형을 지정합니다.

   * JSON 파일에서 값을 동적으로 가져오려면 **[!UICONTROL JSON 경로를 통해 추가]**&#x200B;를 선택하고 JSON 파일의 경로를 제공하십시오. [!DNL Experience Manager]은(는) 양식이 사용자에게 표시될 때 실시간으로 키-값 쌍을 가져옵니다.

   두 옵션은 함께 사용할 수 없습니다. JSON 파일에서 옵션을 가져와 수동으로 편집할 수 없습니다.

   ![add_choice](assets/add_choice.png)

   >[!NOTE]
   >
   >JSON 파일을 추가하면 키-값 쌍이 메타데이터 스키마 편집기에 표시되지 않지만 게시된 양식에서 사용할 수 있습니다.

   >[!NOTE]
   >
   >선택 항목을 추가할 때 팝업 필드를 클릭하면 인터페이스가 왜곡되고 선택 항목에 대한 삭제 아이콘이 작동하지 않습니다. 변경 사항을 저장할 때까지 드롭다운을 클릭하지 마십시오. 이 문제가 발생하면 스키마를 저장하고 다시 열어 편집을 계속합니다.

1. (선택 사항) 다른 필수 필드를 추가합니다. 예: 에셋 유형 비디오의 형식, 코덱 및 기간.

   마찬가지로 다른 에셋 유형에 종속 필드를 추가합니다. 예를 들어 PDF 및 Word 파일과 같은 문서 에셋에 대한 필드 페이지 수 및 작성자를 추가합니다.

   ![video_dependent_fields](assets/video_dependent_fields.png)

1. 자산 유형 필드와 다른 필드 사이에 종속성을 만들려면 종속 필드를 선택하고 **[!UICONTROL 규칙]** 탭을 엽니다.

   ![select_dependentfield](assets/select_dependentfield.png)

1. **[!UICONTROL 요구 사항]**&#x200B;에서 **[!UICONTROL 새 규칙을 기반으로 하는 필수]** 옵션을 선택하십시오.
1. **[!UICONTROL 규칙 추가]**&#x200B;를 선택하고 **[!UICONTROL 자산 유형]** 필드를 선택하여 종속성을 만드십시오. 종속성을 생성할 필드 값도 선택합니다. In this case, choose **[!UICONTROL Video]**. **[!UICONTROL 완료]**&#x200B;를 선택하여 변경 내용을 저장합니다.

   ![define_rule](assets/define_rule.png)

   >[!NOTE]
   >
   >수동으로 사전 정의된 값이 있는 드롭다운을 규칙과 함께 사용할 수 있습니다. 사전 정의된 값을 사용하여 조건을 적용하는 규칙에는 JSON 경로가 구성된 드롭다운 메뉴를 사용할 수 없습니다. 런타임 시 JSON에서 값이 로드되는 경우 사전 정의된 규칙을 적용할 수 없습니다.

1. Under **[!UICONTROL Visibility]**, choose the **[!UICONTROL Visible, based on new rule]** option.

1. **[!UICONTROL 규칙 추가]**&#x200B;를 선택하고 **[!UICONTROL 자산 유형]** 필드를 선택하여 종속성을 만드십시오. Also choose the field value upon which to create the dependency. In this case, choose **[!UICONTROL Video]**. **[!UICONTROL 완료]**&#x200B;를 선택하여 변경 내용을 저장합니다.

   ![define_visibilityrule](assets/define_visibilityrule.png)

   >[!CAUTION]
   >
   >값을 재설정하려면 값이 아닌 인터페이스의 아무 곳이나 선택합니다. 값이 재설정된 경우 값을 다시 선택합니다.

   >[!NOTE]
   >
   >You can apply **[!UICONTROL Requirement]** condition and **[!UICONTROL Visibility]** condition independent of each other.

1. 마찬가지로 에셋 유형 필드의 값 Video와 코덱 및 지속 시간과 같은 다른 필드 간에 종속성을 만듭니다.
1. [!UICONTROL 자산 유형] 필드의 문서 자산(PDF 및 Word)과 [!UICONTROL 페이지 수] 및 [!UICONTROL 작성자] 등의 필드 간에 종속성을 만드는 단계를 반복합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 폴더에 메타데이터 스키마를 적용합니다.

1. 메타데이터 스키마를 적용한 폴더로 이동하고 자산의 속성 페이지를 엽니다. 에셋 유형 필드에서 선택한 사항에 따라 관련 계단식 메타데이터 필드가 표시됩니다.

   ![비디오 자산에 대한 계단식 메타데이터](assets/video_asset.png)
   *그림: 비디오 자산에 대한 계단식 메타데이터*

   ![문서 에셋에 대한 계단식 메타데이터](assets/doc_type_fields.png)
   *그림: 문서 에셋에 대한 계단식 메타데이터*

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)
