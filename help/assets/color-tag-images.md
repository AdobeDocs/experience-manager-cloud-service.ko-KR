---
title: 이미지용 색상 태그
description: Experience Manager Assets을 사용하면 이미지의 색상을 구분하고 이를 태그로 자동으로 적용할 수 있습니다. 그런 다음 이러한 태그를 사용하여 이미지를 검색하고 필터링할 수 있습니다.
exl-id: 3afa949b-ea1b-4b8e-ac94-06566e2c7147
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 9%

---

# 이미지용 색상 태그 {#color-tag-images}

![색상 태그 지정 배너](assets/banner-image.png)

Experience Manager Assets은 Adobe Sensei AI 기능을 사용하여 이미지의 색상을 구분하고 수집 시 이들 색상을 자동으로 태그로 적용합니다. 이러한 태그를 통해 이미지 색상 구성에 따라 향상된 검색 환경을 사용할 수 있습니다.

이미지에 태그 지정되는 색상 수를 1~40개 범위에서 구성하여 나중에 해당 색상을 기준으로 이미지를 검색할 수 있습니다. Experience Manager Assets은 이미지의 색상 범위를 기반으로 태그를 적용합니다. 색상 태그의 표시 형식을 구성할 수도 있습니다.

다음 그림은 Experience Manager Assets에서 이미지에 대한 색상 태깅을 구성하고 관리하기 위해 수행하는 작업의 시퀀스를 보여 줍니다.

![색상 태그 지정](assets/color-tagging-dfd.gif)

## 지원되는 파일 형식 {#supported-file-formats-color-tags}

| 파일 형식 | 확장 | MIME 유형 | 입력 색상 공간 | 지원되는 최대 소스 파일 크기 | 지원되는 최대 파일 크기 확인 |
|---|---|---|---|---|---|
| JPEG | .jpg, .jpeg | image/jpeg | sRGB | 15GB | 20000px X 20000px |
| PNG | .png | image/png | sRGB | 15GB | 20000px X 20000px |
| TIFF | .tif, .tiff | image/tiff | sRGB | 4GB(포맷 사양에 따라 제한됨) | 20000px X 20000px |
| PSD | .psd | image/vnd.adobe.photoshop | sRGB | 2GB(포맷 사양에 따라 제한됨) | 20000px X 20000px |
| GIF | .gif | image/gif | sRGB | 15GB | 20000px X 20000px |
| BMP | .bmp | image/bmp | sRGB | 4GB(포맷 사양에 따라 제한됨) | 20000px X 20000px |

## 색상 태깅 속성 관리 {#manage-color-tagging-properties}

이미지에 대한 색상 태깅 속성을 관리하려면 다음 작업을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 도구 > 에셋 > 색상 태그 지정]**.

   ![색상 태깅 속성](assets/color-tag-settings.png)

1. 에서 색상 태그의 표시 형식 지정 **[!UICONTROL 표시 형식]** 필드. 가능한 옵션에는 색상 이름, RGB 또는 HEX 형식이 포함됩니다.

1. 에서 이미지에 대해 태그 지정할 색상 수를 지정합니다. **[!UICONTROL 제한]** 필드. 이러한 색상은 이미지에 대한 속성을 볼 때 표시됩니다.  이 필드에서 1에서 40 사이의 숫자를 정의할 수 있습니다. 이 필드의 기본값은 10색입니다.

1. 에서 검색 결과에 색상 태그를 포함할 최소 색상 적용 범위 비율을 지정합니다. **[!UICONTROL 적용 범위/우위성 임계값 %]** 필드. 예를 들어, 이미지의 빨강 색상에 대한 적용 범위가 10%이고 이 필드에 9%를 정의하면 빨강 색상에 대한 이미지를 검색할 때 이미지가 포함됩니다. 그러나 이미지의 빨강 색상 적용 범위가 10%이고 이 필드에 11%를 정의하면 빨강 색상이 있는 이미지를 검색할 때 이미지가 포함되지 않습니다.

   이 필드에는 5에서 100 사이의 숫자를 지정할 수 있습니다. 기본값은 11입니다.

   >[!NOTE]
   >
   >Adobe은 이 필드의 기본값에 가까운 값을 사용하는 것을 권장합니다. 이 필드에 설정된 높은 숫자 값(예: 25보다 큼)을 설정하면 검색 결과가 거의 반환되지 않을 수 있습니다. 마찬가지로, 낮은 숫자 값(예: 6보다 작음)을 설정하면 너무 많은 검색 결과가 반환될 수 있으며, 이는 유용하지 않을 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.


   >[!VIDEO](https://video.tv.adobe.com/v/340108)


### 색상 태그 지정 비활성화 {#disable-color-tagging}

이미지에 대한 색상 태깅은 기본적으로 활성화되어 있습니다. 폴더 수준에서 색상 태그 지정을 비활성화할 수 있습니다. 모든 하위 폴더는 상위 폴더에서 색상 태깅 속성을 상속합니다.

폴더 수준에서 색상 태그 지정을 비활성화하려면 다음을 수행합니다.

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager > 에셋 > 파일]**.

1. 폴더를 선택하고 **[!UICONTROL 속성]**.

1. 다음에서 **[!UICONTROL 자산 처리]** 탭에서 다음 위치로 이동 **[!UICONTROL 이미지용 색상 태그]** 폴더를 삭제합니다. 드롭다운 목록에서 다음 값 중 하나를 선택합니다.

   * 상속 - 폴더는 상위 폴더에서 활성화 또는 비활성화 옵션을 상속합니다.

   * 활성화 - 선택한 폴더에 대해 색상 태그 지정을 활성화합니다.

   * 비활성화 - 선택한 폴더에 대한 색상 태그 지정을 비활성화합니다.

   ![색상 태그 지정 설정](assets/color-tags-folder.png)

## 스마트 색상 태그 구성 요소를 추가하도록 메타데이터 스키마 구성 {#configure-metadata-schema}

메타데이터 스키마에는 채울 특정 정보에 대한 특정 필드가 포함되어 있습니다. 또한 사용자에게 친숙한 방식으로 메타데이터 필드를 표시하기 위한 레이아웃 정보가 포함되어 있습니다. 메타데이터 속성에는 제목, 설명, MIME 유형, 태그 등이 포함됩니다. 다음을 사용할 수 있습니다. [!UICONTROL 메타데이터 스키마 Forms] 기존 스키마를 수정하거나 사용자 지정 메타데이터 스키마를 추가하는 편집기.

>[!NOTE]
>
>스마트 색상 태그 필드는 기본 메타데이터 스키마에서 사용할 수 있습니다. 사용자 지정된 메타데이터 스키마를 사용하는 경우 스마트 색상 태그 필드를 추가하도록 스키마를 구성합니다.

메타데이터 스키마 양식 편집기에 스마트 색상 태그 구성 요소를 추가하려면 다음을 수행합니다.

1. 다음으로 이동 **[!UICONTROL 도구 > 에셋 > 메타데이터 스키마]**.

1. 스키마 이름을 선택하고 **[!UICONTROL 편집]**.

1. 드래그 **[!UICONTROL 스마트 색상 태그]** 다음에서 **[!UICONTROL 양식 작성]** 에 대한 탭 **[!UICONTROL 메타데이터 스키마 양식 편집기]**.

1. 다음을 클릭합니다. **[!UICONTROL 스마트 색상 태그 필드]** 다음에서 **[!UICONTROL 메타데이터 스키마 양식 편집기]**.

1. 에 적절한 값을 지정합니다. **[!UICONTROL 필드 레이블]** 의 필드 **[!UICONTROL 설정]**  탭.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/340124)

## DAM의 기존 이미지에 대한 색상 태그 {#color-tags-existing-images}

DAM에 이미 존재하는 이미지는 색상 태그가 자동으로 지정되지 않습니다. 다음을 수행해야 합니다. [!UICONTROL 자산 재처리] 색상 태그를 수동으로 생성합니다.

에셋 저장소에 이미 있는 에셋의 이미지 또는 폴더(하위 폴더 포함)에 색상을 지정하려면 다음 단계를 수행합니다.

1. 다음 항목 선택 [!DNL Adobe Experience Manager] 로고를 만든 다음 [!UICONTROL 탐색] 페이지를 가리키도록 업데이트하는 중입니다.

1. 선택 [!UICONTROL 파일] 자산 인터페이스를 표시합니다.

1. 색상 태그를 적용할 폴더로 이동합니다.

1. 전체 폴더 또는 특정 이미지를 선택합니다.

1. 선택 ![에셋 재처리 아이콘](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL 자산 재처리] 아이콘을 클릭하고 [!UICONTROL 전체 프로세스] 옵션을 선택합니다.

프로세스가 완료되면 다음 위치로 이동합니다. [!UICONTROL 속성] 폴더에 있는 모든 이미지의 페이지입니다. 자동으로 추가된 태그는에 표시됩니다. [!UICONTROL 스마트 색상 태그] 의 섹션 [!UICONTROL 기본] 탭.


## 이미지에 대한 스마트 색상 태그 보기 {#view-color-tags}

이미지에 대한 스마트 색상 태그를 보려면 다음과 같이 하십시오.

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager > 에셋 > 파일]**.

1. 해당 폴더를 클릭하고 이미지를 선택합니다.

1. 선택 **[!UICONTROL 속성]** 및 의 태그 보기 **[!UICONTROL 스마트 색상 태그]** 필드.

   ![색상 태그 보기](assets/view-color-tags.png)

   마우스를 색상 태그 위로 가져가면 **[!UICONTROL 적용 범위/우위성 임계값 %]** 이미지의 색상입니다.

## AEM Assets 색상 술어 구성 {#configure-search-predicate}

이미지에 대한 검색 필터를 구성할 수 있습니다. 그런 다음 특정 색상을 기준으로 검색 기준을 지정하여 결과를 필터링할 수 있습니다.

>[!NOTE]
>
>기본 검색 양식을 사용하지 않는 경우에만 AEM Assets 색상 술어를 구성합니다.

검색 필터를 구성하려면 에셋 관리자 검색 레일을 사용하여 에셋 색상 술어를 만듭니다.

검색 필터를 구성하려면:

1. 다음으로 이동 **[!UICONTROL 도구 > 일반 > Forms 검색]**.

1. 선택 **[!UICONTROL 에셋 관리자 검색 레일]** 및 클릭 **[!UICONTROL 편집]**.

1. 드래그 **[!UICONTROL 에셋 색상 술어]** 다음에서 **[!UICONTROL 조건자 선택]** 에 대한 탭 **[!UICONTROL 검색 양식 편집기]**.

1. 에 적절한 값을 지정합니다. **[!UICONTROL 필드 레이블]** 의 필드 **[!UICONTROL 설정]**  탭.

1. 클릭 **[!UICONTROL 완료]** 설정을 저장합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/340110)

## 색상 기반 이미지 검색 {#search-images-based-on-colors}

>[!VIDEO](https://video.tv.adobe.com/v/340761)

모든 색상 태그 지정 속성 및 [에셋 색상 술어 구성](#search-images-based-on-colors)를 클릭하고 색상을 필터로 사용하여 이미지를 검색할 수 있습니다.

색상을 기준으로 이미지를 검색하려면 다음을 수행합니다.

1. 다음으로 이동 **[!UICONTROL 에셋 > 파일]**.

1. 선택 **[!UICONTROL 필터]** 드롭다운 목록에서 클릭합니다.
   ![자산 필터링](assets/filter-assets.png)

1. 다음 항목 선택 [AEM Assets 색상 술어](#configure-search-predicate).

1. 색상 선택기를 드래그하여 적절한 색상을 선택합니다. 선택한 색상은 색상 선택기 아래에 있는 읽기 전용 필드에 표시됩니다. 색상의 표시 형식으로 RGB 또는 HEX를 선택할 수 있습니다.

   ![색상 피커](assets/color-picker-color-tags.png)

   선택한 색상을 기준으로 이미지를 필터링할 수 있습니다. 선택한 색상이 스마트 색상 태그 중 하나이며 그 위에 있는 이미지 [적용 범위/우위성 임계값 %](#manage-color-tagging-settings) 오른쪽 창에 을 표시합니다.

1. 검색 창에서 x 를 클릭하여 필터를 지웁니다.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [에셋이 지원되는 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 에셋](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
