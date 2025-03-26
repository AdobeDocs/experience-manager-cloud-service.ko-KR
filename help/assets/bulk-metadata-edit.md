---
title: 에서 벌크 메타데이터 편집 Assets 보기
description: '[DNL]에서 사용 가능한 여러 에셋에 대한 사전 정의된 표준 메타데이터 필드 세트를 업데이트하는 방법에 대해 알아봅니다. Assets View] 와 동시에 표시됩니다.'
exl-id: f5fee1b3-2855-4010-ae4a-216beb20920d
source-git-commit: 9b5191bd05bfb06fb4eb1a9b710b98cc132ffeda
workflow-type: tm+mt
source-wordcount: 511
ht-degree: 3%

---

# [!DNL Assets View]에서 일괄 메타데이터 편집{#how-to-edit-the-metadata-of-multiple-assets-simultaneously}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

[!DNL Assets View]의 **[!DNL Bulk Metadata Edit]** 기능을 사용하면 여러 에셋 파일에 대해 미리 정의된 표준 메타데이터 필드 집합을 동시에 편집할 수 있습니다. 각 에셋에 대한 표준 메타데이터를 개별적으로 업데이트하는 대신, 여러 에셋을 선택하고 사전 정의된 표준 메타데이터 세트를 한 번에 일괄 업데이트합니다. 여러 에셋에 대한 표준 메타데이터 속성 세트를 한 번에 일괄 편집할 수 있는 기능은 대규모 에셋 세트에서 이러한 표준 메타데이터 속성의 효율성, 일관성 및 정확성을 유지 관리하여 해당 에셋의 검색 및 구성을 향상합니다.

## 자산 메타데이터 벌크 편집 {#how-to-bulk-edit-the-metadata-of-multiple-assets-on-assets-view}

다음 단계를 실행하여 여러 에셋의 메타데이터를 한 번에 일괄 편집합니다.

1. **[!DNL Assets View]**(으)로 이동한 다음 **[!UICONTROL Assets]**&#x200B;을(를) 클릭합니다.
1. 특정 에셋을 찾아보거나 검색 막대에서 키워드를 사용하여 검색합니다.
1. 자산을 선택하고 상단 메뉴에서 **[!UICONTROL 일괄 메타데이터 편집]**을 클릭합니다.
   ![일괄 메타데이터 편집](/help/assets/assets/bulk-metadata-edit1.png)
1. [!UICONTROL 메타데이터 편집 페이지]에서 **[!UICONTROL 속성]** 패널에서 다음 필드를 편집합니다.
   * **[!UICONTROL 상태]:** 선택한 자산의 상태를 선택합니다.
   * **[!UICONTROL 만료 날짜]:** 자산이 더 이상 유효하지 않거나 필요하지 않은 날짜를 설정합니다.
   * **[!UICONTROL 작성자]:** 작성자 이름을 지정합니다.
   * **[!UICONTROL 키워드]:** 검색 기능을 향상시키기 위해 자산에 대한 높은 수준의 정보를 제공하는 특정 용어나 텍스트 문자열을 추가합니다. 키워드를 추가하고 **Enter** 또는 **return**&#x200B;을 눌러 목록에 다른 키워드를 추가합니다.
   * **[!UICONTROL 태그]:** 사용 가능한 옵션에서 태그를 선택하려면 ![일괄 메타데이터 편집](/help/assets/assets/tags-icon.svg)을 클릭하십시오. 태그는 에셋에 대한 보다 구체적인 정보를 제공하고 검색 기능을 향상시킵니다. 선택한 자산에 이미 적용된 태그가 **[!UICONTROL 속성]** 패널에 표시됩니다. 관련 태그를 찾을 수 없는 경우 해당 태그를 만들어 선택한 에셋에 할당합니다. 에셋에 태그를 만들고 할당하는 방법에 대한 자세한 내용은 [에서 태그 관리 [!DNL Assets view]](/help/assets/tagging-management-assets-view.md)를 참조하십시오.
   * 위의 메타데이터 업데이트를 선택한 자산에 적용하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하십시오. 저장되면 **[!UICONTROL 키워드]** 및 **[!UICONTROL 태그]**&#x200B;이 추가되고, **[!UICONTROL 상태]**, **[!UICONTROL 만료 날짜]** 및 **[!UICONTROL 작성자]**에 대한 업데이트된 세부 정보는 기존 세부 정보를 무시합니다.
     ![save-bulk-metadata-edit-properties](/help/assets/assets/save-bulk-metadata-edit-properties2.png)

     >[!NOTE]
     >
     >한 번에 100개의 에셋의 메타데이터를 편집할 수 있습니다.

자산에 적용된 메타데이터 업데이트를 보려면 [!DNL asset details page]&#x200B;(자산을 선택하고 **[!UICONTROL 세부 정보]**&#x200B;를 클릭)로 이동하고 ![일괄 메타데이터 편집](/help/assets/assets/info-icon-solid-black.svg)을 클릭하여 **[!UICONTROL 정보]** 패널에서 자산의 메타데이터를 확인합니다.

>[!NOTE]
>
>**[!UICONTROL 상태]**, **[!UICONTROL 만료 날짜]**, **[!UICONTROL 작성자]**, **[!UICONTROL 키워드]** 및 **[!UICONTROL 태그]**&#x200B;는 폴더별 메타데이터와 관계없이 일괄 메타데이터 편집에 사용할 수 있는 표준 메타데이터 속성입니다. 이러한 메타데이터 속성은 에셋의 폴더에 적용된 메타데이터 양식에 포함된 경우에만 [!UICONTROL 에셋 세부 정보 페이지]에 표시됩니다. [!UICONTROL 자산 세부 정보 페이지]에서 이러한 표준 메타데이터 속성을 찾을 수 없는 경우 이러한 속성을 포함하도록 자산 폴더의 메타데이터 양식을 편집하십시오. 메타데이터 양식을 만들거나 편집하고 폴더에 적용하는 방법에 대해 알아보려면 [의 메타데이터 [!DNL Assets View]](/help/assets/metadata-assets-view.md)를 참조하세요.
