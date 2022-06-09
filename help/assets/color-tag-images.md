---
title: 이미지용 색상 태그
description: Experience Manager Assets을 사용하면 이미지에서 색상을 구별하고 자동으로 태그로 적용할 수 있습니다. 그런 다음 이러한 태그를 사용하여 이미지를 검색하고 필터링할 수 있습니다.
source-git-commit: 74c13efe99b50ba08d9dc38c246de71482a536a0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 이미지용 색상 태그 {#color-tag-images}

![색상 태깅 배너](assets/banner-image.png)

Experience Manager Assets은 Adobe Sensei AI 기능을 사용하여 이미지의 색상을 구별하고 수집 시 자동으로 태그로 적용합니다. 이러한 태그는 이미지 색상 구성에 따라 향상된 검색 환경을 제공합니다.

이미지에 태그가 지정된 색상의 수를 1~40개 범위에서 구성할 수 있으므로 나중에 해당 색상을 기준으로 이미지를 검색할 수 있습니다. Experience Manager Assets은 이미지의 색상 범위를 기반으로 태그를 적용합니다. 색상 태그에 대한 표시 형식을 구성할 수도 있습니다.

>[!NOTE]
>
>이 기능은 사전 릴리스 채널에서 사용할 수 있습니다. 자세한 내용은 [사전 릴리스 채널 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#enable-prerelease) 을 참조하십시오.

다음 그림은 Experience Manager Assets에서 이미지에 대한 색상 태깅을 구성하고 관리하기 위해 수행하는 작업 순서를 보여줍니다.

![색상 태그 지정](assets/color-tagging-dfd.gif)

## 지원되는 파일 형식 {#supported-file-formats-color-tags}

| 파일 형식 | 확장 | MIME 유형 | 입력 색상 공간 | 지원되는 최대 소스 파일 크기 | 지원되는 최대 파일 크기 해상도 |
|---|---|---|---|---|---|
| JPEG | .jpg, .jpeg | image/jpeg | sRGB | 15GB | 20000px X 20000px |
| PNG | .png | image/png | sRGB | 15GB | 20000px X 20000px |
| TIFF | .tif, .tiff | image/tiff | sRGB | 4GB(포맷 사양에 따라 제한됨) | 20000px X 20000px |
| PSD | .psd | image/vnd.adobe.photoshop | sRGB | 2GB(포맷 사양에 따라 제한됨) | 20000px X 20000px |
| GIF | .gif | image/gif | sRGB | 15GB | 20000px X 20000px |
| BMP | .bmp | image/bmp | sRGB | 4GB(포맷 사양에 따라 제한됨) | 20000px X 20000px |

## 색상 태깅 속성 관리 {#manage-color-tagging-properties}

이미지의 색상 태깅 속성을 관리하려면:

1. 다음으로 이동 **[!UICONTROL 도구 > 자산 > 색상 태깅]**.

   ![색상 태깅 속성](assets/color-tag-settings.png)

1. 에서 색상 태그의 표시 형식을 지정합니다 **[!UICONTROL 표시 형식]** 필드. 가능한 옵션에는 색상 이름, RGB 또는 HEX 형식이 포함됩니다.

1. 에서 이미지에 태깅할 색상 수를 지정합니다 **[!UICONTROL 제한]** 필드. 이러한 색상은 이미지의 속성을 볼 때 표시됩니다.  이 필드에서 1과 40사이의 숫자를 정의할 수 있습니다. 이 필드의 기본값은 10색입니다.

1. 검색 결과에 색상 태그를 포함하려면 최소 색상 적용 범위 백분율을 **[!UICONTROL 범위/우위 임계값 %]** 필드. 예를 들어, 이미지에서 빨강 색상 범위가 10%이고 이 필드에 9%를 정의하는 경우, 빨간색 색상이 있는 이미지를 검색할 때 이미지가 포함됩니다. 하지만 이미지에서 빨강 색상 범위가 10%이고 이 필드에 11%를 정의하는 경우 빨간색 색상이 있는 이미지를 검색할 때 이미지가 포함되지 않습니다.

   이 필드에 5~00의 숫자를 지정할 수 있습니다. 기본값은 11입니다.

   >[!NOTE]
   >
   >Adobe은 이 필드에서 기본값 가까운 값을 사용할 것을 권장합니다. 이 필드에 대해 높은 숫자 값을 설정하면(예: 25보다 큼) 검색 결과가 거의 반환되지 않을 수 있습니다. 마찬가지로, 낮은 숫자 값(예: 6 미만)을 설정하면 검색 결과가 너무 많이 반환될 수 있으므로 유용하지 않을 수 있습니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.


   >[!VIDEO](https://video.tv.adobe.com/v/340108)


### 색상 태깅 비활성화 {#disable-color-tagging}

이미지에 대한 색상 태깅은 기본적으로 활성화됩니다. 폴더 수준에서 색상 태깅을 비활성화할 수 있습니다. 모든 하위 폴더는 상위 폴더에서 색상 태깅 속성을 상속합니다.

폴더 수준에서 색상 태깅을 비활성화하려면 다음을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager > 자산 > 파일]**.

1. 폴더를 선택하고 을(를) 클릭합니다 **[!UICONTROL 속성]**.

1. 에서 **[!UICONTROL 자산 처리]** 탭으로 이동하여 **[!UICONTROL 이미지용 색상 태그]** 폴더를 입력합니다. 드롭다운 목록에서 다음 값 중 하나를 선택합니다.

   * 상속됨 - 폴더가 상위 폴더에서 활성화 또는 비활성화 옵션을 상속합니다.

   * 활성화 - 선택한 폴더에 대해 색상 태깅을 활성화합니다.

   * 비활성화 - 선택한 폴더에 대한 색상 태깅을 비활성화합니다.

   ![색상 태깅 설정](assets/color-tags-folder.png)

## 스마트 색상 태그 구성 요소를 추가하도록 메타데이터 스키마 구성 {#configure-metadata-schema}

메타데이터 스키마에는 특정 정보를 입력하기 위한 특정 필드가 포함되어 있습니다. 또한 사용자에게 친숙한 방식으로 메타데이터 필드를 표시하는 레이아웃 정보도 포함되어 있습니다. 메타데이터 속성에는 제목, 설명, MIME 유형, 태그 등이 포함됩니다. 를 사용할 수 있습니다 [!UICONTROL 메타데이터 스키마 Forms] 기존 스키마를 수정하거나 사용자 지정 메타데이터 스키마를 추가하려면 편집기를 사용하십시오.

>[!NOTE]
>
>스마트 색상 태그 필드는 기본 메타데이터 스키마에서 사용할 수 있습니다. 사용자 지정된 메타데이터 스키마를 사용하는 경우 스마트 색상 태그 필드를 추가하도록 스키마를 구성합니다.

스마트 색상 태그 구성 요소를 메타데이터 스키마 양식 편집기에 추가하려면 다음을 수행합니다.

1. 다음으로 이동 **[!UICONTROL 도구 > 자산 > 메타데이터 스키마]**.

1. 스키마 이름을 선택하고 를 클릭합니다 **[!UICONTROL 편집]**.

1. 드래그 **[!UICONTROL 스마트 색상 태그]** 에서 **[!UICONTROL 양식 작성]** 탭하여 **[!UICONTROL 메타데이터 스키마 양식 편집기]**.

1. 을(를) 클릭합니다. **[!UICONTROL 스마트 색상 태그 필드]** 에서 **[!UICONTROL 메타데이터 스키마 양식 편집기]**.

1. 에서 적절한 값을 지정합니다. **[!UICONTROL 필드 레이블]** 의 필드 **[!UICONTROL 설정]**  탭.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/340124)


## 이미지용 스마트 색상 태그 보기 {#view-color-tags}

이미지의 스마트 색상 태그를 보려면 다음을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager > 자산 > 파일]**.

1. 해당 폴더를 클릭하고 이미지를 선택합니다.

1. 선택 **[!UICONTROL 속성]** 및에서 태그를 봅니다. **[!UICONTROL 스마트 색상 태그]** 필드.

   ![색상 태그 보기](assets/view-color-tags.png)

   마우스를 색상 태그 위에 놓아 **[!UICONTROL 범위/우위 임계값 %]** 이미지의 색상.

## AEM Assets 색상 설명 구성 {#configure-search-predicate}

이미지에 대한 검색 필터를 구성할 수 있습니다. 그런 다음 특정 색상을 기준으로 검색 기준을 적용하여 결과를 필터링할 수 있습니다.

>[!NOTE]
>
>기본 검색 양식을 사용하지 않는 경우에만 AEM Assets 색상 설명을 구성합니다.

검색 필터를 구성하려면 자산 관리 검색 레일을 사용하여 자산 색상 설명을 만듭니다.

검색 필터를 구성하는 방법:

1. 다음으로 이동 **[!UICONTROL 도구 > 일반 > Forms 검색]**.

1. 선택 **[!UICONTROL Assets 관리 검색 레일]** 을(를) 클릭합니다. **[!UICONTROL 편집]**.

1. 드래그 **[!UICONTROL 자산 색상 설명]** 에서 **[!UICONTROL 설명 선택]** 탭하여 **[!UICONTROL 검색 양식 편집기]**.

1. 에서 적절한 값을 지정합니다. **[!UICONTROL 필드 레이블]** 의 필드 **[!UICONTROL 설정]**  탭.

1. 클릭 **[!UICONTROL 완료]** 설정을 저장하려면 을 클릭합니다.

   >[!VIDEO](https://video.tv.adobe.com/v/340110)

## 색상을 기반으로 이미지 검색 {#search-images-based-on-colors}

>[!VIDEO](https://video.tv.adobe.com/v/340761)

모든 색상 태깅 속성 및 [자산 색상 설명 구성](#search-images-based-on-colors)색상을 기반으로 이미지를 필터로 검색할 수 있습니다.

색상을 기준으로 이미지를 검색하려면 다음을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 자산 > 파일]**.

1. 선택 **[!UICONTROL 필터]** 드롭다운 목록에서 을 선택합니다.
   ![자산 필터링](assets/filter-assets.png)

1. 을(를) 선택합니다 [AEM Assets 색상 설명](#configure-search-predicate).

1. 색상 선택기를 드래그하여 해당 색상을 선택합니다. 선택한 색상이 색상 피커 아래에서 사용할 수 있는 읽기 전용 필드에 표시됩니다. RGB 또는 HEX를 색상의 표시 형식으로 선택할 수 있습니다.

   ![색상 피커](assets/color-picker-color-tags.png)

   한 가지 색상 선택에 따라 이미지를 필터링할 수 있습니다. 선택한 색상을 스마트 색상 태그 중 하나 이상과 [범위/우위 임계값 %](#manage-color-tagging-settings) 오른쪽 창에 를 표시합니다.

1. 검색 막대에서 x 를 클릭하여 필터를 지웁니다.




