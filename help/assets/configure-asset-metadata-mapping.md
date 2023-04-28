---
title: Workfront과 Experience Manager Assets 간 자산 메타데이터 매핑 구성
description: Adobe Workfront과 Experience Manager as a Cloud Service 애플리케이션 간에 자산 메타데이터 필드를 매핑합니다. 메타데이터 필드를 매핑한 결과, Workfront에서 Experience Manager Assets으로 자산을 전송하면 Experience Manager Assets에서 매핑된 자산 메타데이터를 볼 수 있습니다.
exl-id: 71400769-b2bc-4f5d-8b6b-a73598e837b4
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 3%

---

# Adobe Workfront과 Experience Manager Assets 간 자산 메타데이터 매핑 구성 {#asset-metadata-mapping-workfront-aem-assets}

Adobe Workfront과 Experience Manager as a Cloud Service 애플리케이션 간에 자산 메타데이터 필드를 매핑할 수 있습니다. 메타데이터 필드를 매핑한 결과, Workfront에서 Experience Manager Assets으로 자산을 전송하면 Experience Manager Assets에서 매핑된 자산 메타데이터를 볼 수 있습니다.

예를 들어, 이미지를 Experience Manager Assets에 보낼 때 이미지, 이름, 설명, 해당 이미지가 Workfront에 속한 프로젝트 등의 이미지에 대한 메타데이터 필드를 유지해야 하는 경우 이러한 필드를 구성하고 Experience Manager Assets 속성에 매핑합니다.

**사용 사례**

이미지 `add-users-workfront.png` 에 있음 `Metadata Syncs` Adobe Workfront 응용 프로그램의 프로젝트. 다음 메타데이터를 사용하여 해당 이미지를 Experience Manager Assets as a Cloud Service으로 보내야 합니다.

* 프로젝트 이름

* 문서 이름

* 문서 설명

## 사전 요구 사항 {#prerequisites}

* Workfront 및 Experience Manager Assets as a Cloud Service 애플리케이션에 대한 관리자 액세스 권한.

* 통합 [Workfront 및 Experience Manager Assets as a Cloud Service 애플리케이션](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FDocuments%2FAdobe_Workfront_for_Experience_Manager_Assets_Essentials%2Fsetup-asset-essentials.htm&amp;_LANG=enus).

## Workfront에서 메타데이터 매핑 설정 {#set-up-metadata-mapping}

Workfront의 프로젝트 이름, 문서 이름 및 문서 설명 필드에 대한 메타데이터 매핑을 설정하려면 다음을 수행하십시오.

1. Main Menu 아이콘을 클릭합니다. ![메뉴 표시](assets/show-menu.svg) Adobe Workfront 애플리케이션의 오른쪽 상단 모서리에서 을(를) 클릭하고 **[!UICONTROL 설정]**.

1. 선택 **[!UICONTROL 문서]** 왼쪽 패널에서 를 선택하고 **[!UICONTROL Experience Manager Assets]**.

1. Experience Manager Assets 통합을 선택하고 을(를) 클릭합니다 **[!UICONTROL 편집]**.

1. 클릭 **[!UICONTROL 메타데이터]**. 에서 **[!UICONTROL 자산]** 탭, 맵 [!UICONTROL 프로젝트] > [!UICONTROL 이름] Workfront 필드 `wm:projectName` Experience Manager Assets 필드. 정확히 일치하는 항목을 찾지 못할 경우 Workfront 및 Experience Manager Assets 필드를 매핑하기 위해 가장 적합한 일치 항목을 찾는 것이 좋습니다. 서로 다른 데이터 유형의 필드를 매핑하지 않도록 할 수 있습니다. 예를 들어 날짜 Workfront 필드를 설명 자산 필드에 매핑합니다.
1. 맵 [!UICONTROL 문서] > [!UICONTROL 이름] Workfront 필드 `wm:documentName` Experience Manager Assets 필드.

   ![Workfront의 매핑](assets/workfront-metadata-mapping.png)

1. 맵 [!UICONTROL 문서] > [!UICONTROL 설명] Workfront 필드 `dc:description` Experience Manager Assets 필드.

   >[!VIDEO](https://video.tv.adobe.com/v/344255)

## Workfront에서 Experience Manager Assets으로 이미지 보내기 {#send-image-workfront-assets}

Workfront에서 Experience Manager Assets으로 이미지를 보내려면

1. Main Menu 아이콘을 클릭합니다. ![메뉴 표시](assets/show-menu.svg) Adobe Workfront 애플리케이션의 오른쪽 상단 모서리에서 을(를) 클릭하고 **[!UICONTROL 프로젝트]**.

1. 클릭 **[!UICONTROL 새 프로젝트]** 새 프로젝트를 만들려면

1. 클릭 **[!UICONTROL 문서]** 왼쪽 창에서 옵션을 선택한 다음 Experience Manager Assets에 보내야 하는 이미지를 선택합니다.

1. 클릭 **[!UICONTROL 보내기]**&#x200B;그런 다음 Experience Manager Assets Essentials 통합 이름을 선택합니다.

   ![AEM으로 전송](assets/send-to-aem.png)

1. 자산의 대상 폴더를 선택한 다음 를 클릭합니다 **[!UICONTROL 폴더 선택]**.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## Experience Manager as a Cloud Service에서 자산 메타데이터 매핑 구성 {#metadata-mapping-aem}

후 [Adobe Workfront에서 자산 메타데이터 매핑 구성](#set-up-metadata-mapping)를 채울 때는 Experience Manager Assets as a Cloud Service 애플리케이션에서 동일한 매핑을 사용하여 이미지에 적절한 메타데이터 결과를 표시해야 합니다.

메타데이터 매핑은 Experience Manager Assets의 메타데이터 스키마를 사용하여 수행됩니다. 새로 추가되거나 기존 메타데이터 스키마 양식을 편집할 수 있습니다. 메타데이터 스키마 양식은 탭 내의 탭 및 양식 항목을 포함합니다. 이러한 양식 항목을 CRX 저장소의 메타데이터 노드 내의 필드에 매핑/구성할 수 있습니다. 탭 또는 양식 항목을 메타데이터 스키마 양식에 추가할 수 있습니다. 자세한 내용은 [메타데이터 스키마](metadata-schemas.md).

Experience Manager Assets as a Cloud Service에서 새 메타데이터 양식을 사용하여 메타데이터 매핑을 구성하려면 다음을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 스키마]**.

1. 클릭 **[!UICONTROL 만들기]** 를 클릭합니다. 대화 상자에서 스키마 양식의 제목을 제공하고 **[!UICONTROL 만들기]** 을 눌러 양식 작성 프로세스를 완료합니다.

1. 스키마 양식을 선택하고 을(를) 클릭합니다. **[!UICONTROL 편집]**.

1. (선택 사항) 메타데이터 스키마 양식 편집기에서 `+` Workfront 필드에 대한 새 탭을 만들려면

1. 을(를) 클릭합니다. **[!UICONTROL 양식 작성]** 탭을 선택하고 **[!UICONTROL 단일 행 텍스트]** 구성 요소를 생성하지 않습니다. 양식에서 구성 요소를 클릭합니다. 에서 **[!UICONTROL 양식 작성]** 탭:

   1. 지정 `Project Name` 에서 **[!UICONTROL 필드 레이블]** 필드.

   1. 지정 `./jcr:content/metadata/wm:projectName` 에서 **[!UICONTROL 속성에 매핑]** 필드. 지침으로서, 다음 템플릿을 사용하여 Experience Manager Assets에서 필드 매핑을 정의합니다.
      `./jcr:content/metadata/<mapping defined for the field in workfront>`.

      Workfront에서 매핑을 구성하는 동안 매핑했습니다 `wm:projectName` Experience Manager Assets 필드 - 프로젝트 > 이름 Workfront 필드

      `wm` 는 네임스페이스 이름 및 `projectName` 는 속성 제목을 나타냅니다. 를 사용하십시오 `namespace:propertyTitle` 메타데이터 필드 매핑을 정의하는 형식입니다.

      ![AEM으로 전송](assets/metadata-schema-mapping.png)

1. 을(를) 클릭합니다. **[!UICONTROL 양식 작성]** 탭을 선택하고 **[!UICONTROL 단일 행 텍스트]** 구성 요소를 생성하지 않습니다. 양식에서 구성 요소를 클릭합니다. 에서 **[!UICONTROL 양식 작성]** 탭:

   1. 지정 `Document Name` 에서 **[!UICONTROL 필드 레이블]** 필드.

   1. 지정 `./jcr:content/metadata/wm:documentName` 에서 **[!UICONTROL 속성에 매핑]** 필드.
Workfront에서 매핑을 구성하는 동안 매핑했습니다 `wm:documentName` Experience Manager Assets 필드에서 문서 > 이름 Workfront 필드로 이동합니다.

1. 을(를) 클릭합니다. **[!UICONTROL 양식 작성]** 탭을 선택하고 **[!UICONTROL 여러 줄 텍스트]** 구성 요소를 생성하지 않습니다. 양식에서 구성 요소를 클릭합니다. 에서 **[!UICONTROL 양식 작성]** 탭:

   1. 지정 `Document Description` 에서 **[!UICONTROL 필드 레이블]** 필드.

   1. 지정 `./jcr:content/metadata/dc:description` 에서 **[!UICONTROL 속성에 매핑]** 필드.
Workfront에서 매핑을 구성하는 동안 매핑했습니다 `dc:description` Experience Manager Assets 필드 - 문서 > 설명 Workfront 필드

1. 클릭 **[!UICONTROL 저장]** 변경 사항을 저장하려면 을 클릭합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/344314)

## 이미지 폴더에 메타데이터 설정 적용 {#apply-metadata-settings-image-folder}

Experience Manager as a Cloud Service 애플리케이션에서 메타데이터 설정을 구성한 후 해당 설정을 [Workfront 애플리케이션에서 전송된 이미지가 포함된 폴더](#send-image-workfront-assets).

이미지 폴더에 메타데이터 설정을 적용하려면:

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 스키마]**.

1. 사용 가능한 목록에서 메타데이터 스키마를 선택하고 을 클릭합니다 **[!UICONTROL 폴더에 적용]**.

1. 대상 폴더를 선택합니다 [Adobe Workfront 애플리케이션에서 이미지가 전송됩니다](#send-image-workfront-assets) 을(를) 클릭합니다. **[!UICONTROL 적용]**.

Experience Manager Assets에서 이미지로 이동하고 이미지와 연관된 메타데이터를 볼 수 있습니다. 이미지를 선택하고 을(를) 클릭합니다 **[!UICONTROL 속성]** 이미지 메타데이터를 보려면

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
