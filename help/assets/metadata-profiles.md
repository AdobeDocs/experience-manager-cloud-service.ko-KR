---
title: 메타데이터 프로필
description: 에셋의 메타데이터 프로필에 대해 알아봅니다. 메타데이터 프로필을 만들고 폴더 에셋에 적용하는 방법에 대해 알아봅니다.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: eef90c6a-b354-4342-8b97-21d067ae2979
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 21%

---

# 메타데이터 프로필 {#metadata-profiles}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-config.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

메타데이터 프로필을 사용하면 폴더 내의 에셋에 기본 메타데이터를 적용할 수 있습니다. 메타데이터 프로필을 만들어 폴더에 적용합니다. 이후에 폴더에 업로드하는 모든 에셋은 메타데이터 프로필에서 구성한 기본 메타데이터를 상속합니다.

Experience Manager Assets의 프로필 사용과 관련된 중요한 개념은 폴더에 할당된다는 것입니다. 프로필 내에는 비디오 프로필 또는 이미지 프로필과 함께 메타데이터 프로필 형식의 설정이 있습니다. 이러한 설정은 하위 폴더와 함께 폴더의 내용을 처리합니다. 따라서 파일 및 폴더의 이름 지정 방법, 하위 폴더를 정렬하는 방법 및 이러한 폴더 내의 파일을 처리하는 방법은 해당 에셋이 프로필에서 처리되는 방식에 상당한 영향을 줍니다.
일관되고 적절한 파일 및 폴더 이름 지정 전략 및 양호한 메타데이터 사례를 사용하여 디지털 에셋 컬렉션을 최대한 활용하고 올바른 프로필에서 올바른 파일이 처리되도록 합니다.

## 메타데이터 프로필 추가 {#adding-a-metadata-profile}

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 프로필]**(으)로 이동한 다음 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
1. 메타데이터 프로필의 제목(예: 샘플 메타데이터)을 입력하고 **[!UICONTROL 제출]**&#x200B;을 선택합니다. 메타데이터 프로필에 대한 편집 양식이 표시됩니다.
1. 구성 요소를 클릭하고 **[!UICONTROL 설정]** 탭에서 해당 속성을 구성합니다. 예를 들어 **[!UICONTROL 설명]** 구성 요소를 클릭하고 속성을 편집합니다.
**[!UICONTROL 설명]** 구성 요소에 대한 다음 속성을 편집합니다.

   * **[!UICONTROL 필드 레이블]** - 메타데이터 속성의 표시 이름입니다. 사용자 참조용으로만 사용됩니다.
   * **[!UICONTROL 속성에 매핑]** - 이 속성의 값은 저장소에 저장된 에셋 노드에 대한 상대 경로/이름을 제공합니다. 경로는 자산의 노드 아래에 있으므로 값은 항상 `./`로 시작해야 합니다.

     **[!UICONTROL 속성에 매핑]**&#x200B;에 지정한 값이 자산의 메타데이터 노드 아래에 속성으로 저장됩니다. For example, if you specify . `/jcr:content/metadata/dc:desc`을(를) **[!UICONTROL 속성에 매핑]**&#x200B;의 이름으로 [!DNL Adobe Experience Manager Assets]에서 자산의 메타데이터 노드에 값 `dc:desc`을(를) 저장합니다.

   * **[!UICONTROL 기본값]** - 이 속성을 사용하여 메타데이터 구성 요소의 기본값을 추가합니다. 예를 들어 &quot;My description&quot;을 지정하면 이 값은 자산의 메타데이터 노드에서 `dc:desc` 속성에 할당됩니다.

     >[!NOTE]
     >
     >`/jcr:content/metadata` 노드에 없는 새 메타데이터 속성에 기본값을 추가해도 자산의 속성 페이지에 기본적으로 속성과 해당 값이 표시되지 않습니다. [!UICONTROL 속성] 페이지에서 새 속성을 보려면 해당 스키마 양식을 수정하십시오.

1. (Optional) Add more components to the Edit Form from the **[!UICONTROL Build Form]** tab, and configure their properties in the **[!UICONTROL Settings]** tab. The following properties are available from the **[!UICONTROL Build Form]** tab:

| 구성 요소 | 속성 |
|------------------|----------------------------------------------------|
| 섹션 머리글 | 필드 레이블, 설명 |
| 한 줄 텍스트 | 필드 레이블, 속성에 매핑, 기본값 |
| 다중 값 텍스트 | 필드 레이블, 속성에 매핑, 기본값 |
| 숫자 | 필드 레이블, 속성에 매핑, 기본값 |
| 날짜 | 필드 레이블, 속성에 매핑, 기본값 |
| 표준 태그 | 필드 레이블, 속성에 매핑, 기본값, 설명 |

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다. 메타데이터 프로필이 **[!UICONTROL 메타데이터 프로필]** 페이지의 프로필 목록에 추가됩니다.

## 메타데이터 프로필 복사 {#copying-a-metadata-profile}

1. **[!UICONTROL 메타데이터 프로필]** 페이지에서 복사본을 만들 메타데이터 프로필을 선택하십시오.
1. 도구 모음에서 **[!UICONTROL 복사]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 메타데이터 프로필 복사]** 대화 상자에서 메타데이터 프로필의 새 복사본 제목을 입력합니다.
1. **[!UICONTROL 복사]**&#x200B;를 클릭합니다. The copy of the Metadata Profile appears in the list of profiles in the **[!UICONTROL Metadata Profiles]** page.

## 메타데이터 프로필 삭제 {#deleting-a-metadata-profile}

1. **[!UICONTROL 메타데이터 프로필]** 페이지에서 삭제할 프로필을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 메타데이터 프로필 삭제]**&#x200B;를 클릭합니다.
1. 대화 상자에서 **[!UICONTROL 삭제]**&#x200B;를 클릭하여 삭제 작업을 확인합니다. 메타데이터 프로필이 목록에서 삭제됩니다.

## 폴더에 메타데이터 프로필 적용 {#applying-a-metadata-profile-to-folders}

폴더에 메타데이터 프로필을 할당하면 하위 폴더는 자동으로 상위 폴더에서 프로필을 상속합니다. 다른 프로필이 하위 폴더에 적용되면 상속이 중지됩니다. 폴더에 하나의 메타데이터 프로필만 할당할 수 있습니다. 따라서 에셋을 업로드, 저장, 사용 및 보관하는 폴더 구조를 신중하게 고려하십시오.

폴더에 다른 메타데이터 프로필을 할당하면 새 프로필이 이전 프로필을 재정의합니다. 이전의 기존 폴더 자산은 변경되지 않습니다. 새 프로필은 변경 후 폴더에 추가된 에셋에 적용됩니다. 메타데이터 프로필을 특정 폴더에 적용하거나 모든 에셋에 전역적으로 적용할 수 있습니다.

프로필이 할당된 폴더는 카드 이름에 나타나는 프로필 이름으로 사용자 인터페이스에 표시됩니다.

나중에 변경한 기존 메타데이터 프로필이 이미 있는 폴더에서 에셋을 재처리할 수 있습니다. <!-- See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

### 특정 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-specific-folders}

You can apply a metadata profile to a folder from within the **[!UICONTROL Tools]** menu or if you are in the folder, from **[!UICONTROL Properties]**. This section describes how to apply metadata profiles to folders both ways.

Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

나중에 변경한 기존 비디오 프로필이 이미 있는 폴더에서 에셋을 재처리할 수 있습니다. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

#### 프로필 사용자 인터페이스에서 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. **[!UICONTROL 도구 > Assets > 메타데이터 프로필]**(으)로 이동합니다.
1. 폴더 또는 여러 폴더에 적용할 메타데이터 프로필을 선택합니다.
1. **[!UICONTROL 폴더에 메타데이터 프로필 적용]**&#x200B;을 클릭하고 새로 업로드한 자산을 받는 데 사용할 폴더 또는 여러 폴더를 선택한 다음 **[!UICONTROL 완료]**&#x200B;를 클릭합니다. Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

#### 속성에서 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-folders-from-properties}

1. 왼쪽 레일에서 **[!UICONTROL Assets]**&#x200B;을 클릭한 다음 메타데이터 프로필을 적용할 폴더로 이동합니다.
1. 폴더에서 확인 표시를 선택하여 선택한 다음 **속성**&#x200B;을 선택합니다.
1. **[!UICONTROL 메타데이터 프로필]** 탭을 선택하고 드롭다운 메뉴에서 프로필을 선택한 다음 **[!UICONTROL 저장]**&#x200B;을 클릭합니다. Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

### 메타데이터 프로필을 전체적으로 적용 {#applying-a-metadata-profile-globally}

폴더에 프로필을 적용하는 것 외에도, 모든 폴더의 [!DNL Experience Manager Assets]에 업로드된 모든 콘텐츠에 선택한 프로필이 적용되도록 전체적으로 적용할 수도 있습니다.

나중에 변경한 기존 메타데이터 프로필이 이미 있는 폴더에서 에셋을 재처리할 수 있습니다. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**메타데이터 프로필을 전역적으로 적용하려면 다음 중 하나를 실행하십시오**

* `https://[aem_server]/mnt/overlay/dam/gui/content/assets/v2/foldersharewizard.html/content/dam`(으)로 이동하여 적절한 프로필을 적용하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

* `/content/dam/jcr:content` CRXDE Lite으로 이동합니다. 속성 `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>`을(를) 추가합니다. **모두 저장**&#x200B;을 클릭합니다.

## 폴더에서 메타데이터 프로필 제거 {#removing-a-metadata-profile-from-folders}

폴더에서 메타데이터 프로필을 제거하면 모든 하위 폴더는 상위 폴더에서 프로필 제거를 자동으로 상속합니다. 그러나 폴더 내에서 발생한 모든 파일 처리는 그대로 유지됩니다.

You can remove a metadata profile from a folder from within the **Tools** menu or if you are in the folder, from the **Properties**. This section describes how to remove metadata profiles from folders both ways.

### 프로필 사용자 인터페이스를 통해 폴더에서 메타데이터 프로필 제거 {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Experience Manager 로고를 클릭하고 **[!UICONTROL 도구 > Assets > 메타데이터 프로필]**(으)로 이동합니다.
1. 폴더 또는 여러 폴더에서 제거할 메타데이터 프로필을 선택합니다.
1. **[!UICONTROL 폴더에서 메타데이터 프로필 제거]**&#x200B;를 클릭하고 프로필을 제거하는 데 사용할 폴더 또는 여러 폴더를 선택한 다음 **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

   이름이 더 이상 폴더 이름 아래에 표시되지 않으므로 메타데이터 프로필이 더 이상 폴더에 적용되지 않는지 확인할 수 있습니다.

### 속성을 통해 폴더에서 메타데이터 프로필 제거 {#removing-metadata-profiles-from-folders-via-properties}

1. Experience Manager 로고를 클릭하고 **[!UICONTROL Assets]**&#x200B;을(를) 탐색한 다음 메타데이터 프로필을 제거할 폴더로 이동합니다.
1. 폴더에서 확인 표시를 클릭하여 선택한 다음 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.
1. Select the **[!UICONTROL Metadata Profiles]** tab and select **[!UICONTROL None]** from the drop-down menu and click **[!UICONTROL Save]**. Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

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
