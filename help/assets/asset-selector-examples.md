---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 자산 선택기를 사용하여 요구 사항에 따라 사용자 지정하는 예제.
role: Admin, User
exl-id: 7a393a96-f2a2-4a25-922c-577271cafc57
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 46%

---

# 자산 선택기 속성 사용 예 {#usage-examples}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

**index.html** 파일에서 자산 선택기 [속성](/help/assets/asset-selector-properties.md)을(를) 정의하여 응용 프로그램 내의 자산 선택기 표시를 사용자 지정할 수 있습니다.

## 예 1: 레일 보기의 자산 선택기

![레일-보기-예](assets/rail-view-example-vanilla.png)

AssetSelector `rail`의 값이 `false`(으)로 설정되어 있거나 속성에 언급되지 않은 경우 기본적으로 자산 선택기가 모달 보기에 표시됩니다. `acvConfig` 속성은 끌어서 놓기와 같은 일부 심층적인 구성을 허용합니다. `acvConfig` 속성의 사용을 이해하려면 [드래그 앤 드롭을 사용하거나 사용하지 않도록 설정](asset-selector-customization.md#enable-disable-drag-and-drop)하세요.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

## 예 2: 메타데이터 팝오버

다양한 속성을 통해 정보 아이콘을 사용하여 보려는 자산의 메타데이터를 정의합니다. 정보 팝오버는 자산의 제목, 차원, 수정일, 위치 및 설명을 포함하여 자산 또는 폴더에 대한 정보 모음을 제공합니다. 아래 예에서는 자산의 메타데이터를 표시하는 데 다양한 속성이 사용됩니다. 예를 들어 `repo:path` 속성은 자산의 위치를 지정합니다. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![메타데이터-팝오버-예](assets/metadata-popover.png)

## 예 3: 레일 보기의 사용자 정의 필터 속성

패싯된 검색 외에도 Assets Selector를 사용하면 [!DNL Adobe Experience Manager]에서 [!DNL Cloud Service] 애플리케이션으로 검색을 구체화하기 위해 다양한 특성을 사용자 지정할 수 있습니다. 다음 코드를 추가하여 애플리케이션에 사용자 지정된 검색 필터를 추가합니다. 아래 예의 이미지, 문서 또는 비디오 중에서 자산 유형을 필터링하는 `Type Filter` 검색 또는 검색을 위해 추가한 필터 유형

![사용자-정의-필터-예-바닐라](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->


>[!MORELIKETHIS]
>
>* [자산 선택기 사용자 지정](/help/assets/asset-selector-customization.md)
>* [자산 선택기 업로드](/help/assets/asset-selector-upload.md)
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [OpenAPI 기능을 사용하여 Dynamic Media과 자산 선택기 통합](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
