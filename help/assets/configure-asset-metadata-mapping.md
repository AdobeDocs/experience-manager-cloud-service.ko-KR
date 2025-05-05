---
title: Workfront과 Experience Manager Assets 간의 에셋 메타데이터 매핑 구성
description: Adobe Workfront 및 Experience Manager as a Cloud Service 애플리케이션 간에 에셋 메타데이터 필드를 매핑합니다. 메타데이터 필드를 매핑한 결과, Workfront에서 Experience Manager Assets으로 에셋을 전송하면 Experience Manager Assets에서 매핑된 에셋 메타데이터를 볼 수 있습니다.
exl-id: 71400769-b2bc-4f5d-8b6b-a73598e837b4
feature: Metadata, Workfront Integrations and Apps
role: User, Admin
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1058'
ht-degree: 6%

---

# Adobe Workfront과 Experience Manager Assets 간의 에셋 메타데이터 매핑 구성 {#asset-metadata-mapping-workfront-aem-assets}

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

Adobe Workfront 및 Experience Manager as a Cloud Service 애플리케이션 간에 에셋 메타데이터 필드를 매핑할 수 있습니다. 메타데이터 필드를 매핑한 결과, Workfront에서 Experience Manager Assets으로 에셋을 전송하면 Experience Manager Assets에서 매핑된 에셋 메타데이터를 볼 수 있습니다.

예를 들어 이미지를 Workfront으로 보낼 때 Experience Manager Assets에서 이름, 설명 및 이미지가 속한 프로젝트와 같은 이미지에 대한 메타데이터 필드를 유지해야 하는 경우 이러한 필드를 구성하고 Experience Manager Assets 속성에 매핑합니다.

**사용 사례**

Adobe Workfront 응용 프로그램의 `Metadata Syncs` 프로젝트에 `add-users-workfront.png` 이미지가 있습니다. 다음 메타데이터와 함께 해당 이미지를 Experience Manager Assets as a Cloud Service으로 보내야 합니다.

* 프로젝트 이름

* 문서 이름

* 문서 설명

## 사전 요구 사항 {#prerequisites}

* Workfront 및 Experience Manager Assets as a Cloud Service 애플리케이션에 대한 관리자 액세스 권한.

* [Workfront 및 Experience Manager Assets as a Cloud Service 응용 프로그램](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FDocuments%2FAdobe_Workfront_for_Experience_Manager_Assets_Essentials%2Fsetup-asset-essentials.htm&amp;_LANG=enus) 간의 통합.

## Workfront에서 메타데이터 매핑 설정 {#set-up-metadata-mapping}

Workfront의 프로젝트 이름, 문서 이름 및 문서 설명 필드에 대한 메타데이터 매핑을 설정하려면 다음을 수행하십시오.

1. Adobe Workfront 응용 프로그램의 오른쪽 상단에 있는 기본 메뉴 아이콘 ![메뉴 표시](assets/show-menu.svg)를 클릭한 다음 **[!UICONTROL 설정]**&#x200B;을 클릭합니다.

1. 왼쪽 패널에서 **[!UICONTROL 문서]**&#x200B;를 선택한 다음 **[!UICONTROL Experience Manager Assets]**&#x200B;을 선택합니다.

1. Experience Manager Assets 통합을 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 메타데이터]**&#x200B;를 클릭합니다. **[!UICONTROL Assets]** 탭에서 [!UICONTROL 프로젝트] > [!UICONTROL 이름] Workfront 필드를 `wm:projectName` Experience Manager Assets 필드에 매핑합니다. 정확한 일치 항목을 찾지 못한 경우 Adobe에서는 Workfront 및 Experience Manager Assets 필드를 매핑할 수 있는 가장 적합한 항목을 찾을 것을 권장합니다. 서로 다른 데이터 유형의 필드를 매핑하지 않아도 됩니다. 예를 들어 날짜 Workfront 필드를 설명 Assets 필드에 매핑합니다.
1. [!UICONTROL Document] > [!UICONTROL Name] Workfront 필드를 `wm:documentName` Experience Manager Assets 필드에 매핑합니다.

   ![Workfront에서 매핑](assets/workfront-metadata-mapping.png)

1. [!UICONTROL Document] > [!UICONTROL Description] Workfront 필드를 `dc:description` Experience Manager Assets 필드에 매핑합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/344255)

## Workfront에서 Experience Manager Assets으로 이미지 보내기 {#send-image-workfront-assets}

Workfront에서 Experience Manager Assets으로 이미지를 전송하려면 다음을 수행하십시오.

1. Adobe Workfront 응용 프로그램의 오른쪽 상단에 있는 기본 메뉴 아이콘 ![메뉴 표시](assets/show-menu.svg)를 클릭한 다음 **[!UICONTROL 프로젝트]**&#x200B;를 클릭합니다.

1. 프로젝트를 만들려면 **[!UICONTROL 새 프로젝트]**&#x200B;를 클릭하십시오.

1. 왼쪽 창에서 사용할 수 있는 **[!UICONTROL 문서]** 옵션을 클릭하고 드래그한 다음 Experience Manager Assets으로 보내야 하는 이미지를 선택합니다.

1. **[!UICONTROL 보내기]**&#x200B;를 클릭한 다음 Experience Manager Assets Essentials 통합 이름을 선택합니다.

   ![AEM으로 보내기](assets/send-to-aem.png)

1. 에셋의 대상 폴더를 선택한 다음 **[!UICONTROL 폴더 선택]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## Experience Manager as a Cloud Service에서 에셋 메타데이터 매핑 구성 {#metadata-mapping-aem}

[Adobe Workfront에서 에셋 메타데이터 매핑을 구성](#set-up-metadata-mapping)한 후에는 Experience Manager Assets as a Cloud Service 응용 프로그램에서 동일한 매핑을 사용하여 이미지에 대한 적절한 메타데이터 결과를 표시해야 합니다.

메타데이터 매핑은 Experience Manager Assets의 메타데이터 스키마를 사용하여 수행됩니다. 새로 추가된 메타데이터 스키마 양식 또는 기존 메타데이터 스키마 양식을 편집할 수 있습니다. 메타데이터 스키마 양식에는 탭과 탭 내의 양식 항목이 포함됩니다. 이러한 양식 항목을 CRX 저장소의 메타데이터 노드 내에 있는 필드에 매핑/구성할 수 있습니다. 메타데이터 스키마 양식에 탭이나 양식 항목을 추가할 수 있습니다. 자세한 내용은 [메타데이터 스키마](metadata-schemas.md)를 참조하십시오.

Experience Manager Assets as a Cloud Service에서 새 메타데이터 양식을 사용하여 메타데이터 매핑을 구성하려면 다음 작업을 수행하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.

1. 도구 모음에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 대화 상자에서 스키마 양식의 제목을 입력하고 **[!UICONTROL 만들기]**&#x200B;를 클릭하여 양식 만들기 프로세스를 완료합니다.

1. 스키마 양식을 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.

1. (선택 사항) 메타데이터 스키마 양식 편집기에서 `+`을(를) 클릭하여 Workfront 필드에 대한 탭을 만듭니다.

1. **[!UICONTROL 양식 작성]** 탭을 클릭하고 **[!UICONTROL 한 줄 텍스트]** 구성 요소를 양식으로 끌어 옵니다. 양식에서 구성 요소를 클릭합니다. **[!UICONTROL 양식 작성]** 탭에서:

   1. **[!UICONTROL 필드 레이블]** 필드에 `Project Name`을(를) 지정하십시오.

   1. **[!UICONTROL 속성에 매핑]** 필드에 `./jcr:content/metadata/wm:projectName`을(를) 지정합니다. 지침으로, 다음 템플릿을 사용하여 Experience Manager Assets에서 필드 매핑을 정의합니다.

      `./jcr:content/metadata/<mapping defined for the field in workfront>`

      Workfront에서 매핑을 구성하는 동안 `wm:projectName` Experience Manager Assets 필드를 프로젝트 > 이름 Workfront 필드에 매핑했습니다.

      `wm`은(는) 네임스페이스 이름을 참조하고 `projectName`은(는) 속성 제목을 참조합니다. 메타데이터 필드 매핑을 정의하려면 `namespace:propertyTitle` 형식을 사용하십시오.

      ![AEM으로 보내기](assets/metadata-schema-mapping.png)

1. **[!UICONTROL 양식 작성]** 탭을 클릭하고 **[!UICONTROL 한 줄 텍스트]** 구성 요소를 양식으로 끌어 옵니다. 양식에서 구성 요소를 클릭합니다. **[!UICONTROL 양식 작성]** 탭에서:

   1. **[!UICONTROL 필드 레이블]** 필드에 `Document Name`을(를) 지정하십시오.

   1. **[!UICONTROL 속성에 매핑]** 필드에 `./jcr:content/metadata/wm:documentName`을(를) 지정합니다.
Workfront에서 매핑을 구성하는 동안 `wm:documentName` Experience Manager Assets 필드를 Document > Name Workfront 필드에 매핑했습니다.

1. **[!UICONTROL 양식 작성]** 탭을 클릭하고 **[!UICONTROL 여러 줄 텍스트]** 구성 요소를 양식으로 끌어 옵니다. 양식에서 구성 요소를 클릭합니다. **[!UICONTROL 양식 작성]** 탭에서:

   1. **[!UICONTROL 필드 레이블]** 필드에 `Document Description`을(를) 지정하십시오.

   1. **[!UICONTROL 속성에 매핑]** 필드에 `./jcr:content/metadata/dc:description`을(를) 지정합니다.
Workfront에서 매핑을 구성하는 동안 `dc:description` Experience Manager Assets 필드를 문서 > 설명 Workfront 필드에 매핑했습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 변경 내용을 저장합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/344314)

## 이미지 폴더에 메타데이터 설정 적용 {#apply-metadata-settings-image-folder}

Experience Manager as a Cloud Service 응용 프로그램에서 메타데이터 설정을 구성한 후 해당 설정을 Workfront 응용 프로그램에서 보낸 이미지가 포함된 [폴더에 적용](#send-image-workfront-assets)합니다.

이미지 폴더에 메타데이터 설정을 적용하려면 다음을 수행합니다.

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.

1. 사용 가능한 목록에서 메타데이터 스키마를 선택하고 **[!UICONTROL 폴더에 적용]**&#x200B;을 클릭합니다.

1. [Adobe Workfront 응용 프로그램에서 이미지를 보낼 대상 폴더](#send-image-workfront-assets)를 선택하고 **[!UICONTROL 적용]**&#x200B;을 클릭합니다.

Experience Manager Assets에서 이미지로 이동하여 이미지와 관련된 메타데이터를 볼 수 있습니다. 이미지를 선택하고 **[!UICONTROL 속성]**&#x200B;을 클릭하여 이미지 메타데이터를 봅니다.

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
