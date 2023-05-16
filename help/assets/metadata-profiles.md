---
title: 메타데이터 프로필
description: 자산의 메타데이터 프로필에 대해 알아봅니다. 메타데이터 프로필을 만들어 폴더 자산에 적용하는 방법을 알아봅니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: eef90c6a-b354-4342-8b97-21d067ae2979
source-git-commit: 80ac947976bab2b0bfedb4ff9d5dd4634de6b4fc
workflow-type: tm+mt
source-wordcount: '1408'
ht-degree: 20%

---

# 메타데이터 프로필 {#metadata-profiles}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-config.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

메타데이터 프로필을 사용하면 폴더 내의 자산에 기본 메타데이터를 적용할 수 있습니다. 메타데이터 프로필을 만들어 폴더에 적용합니다. 이후에 폴더에 업로드하는 모든 자산은 메타데이터 프로필에서 구성한 기본 메타데이터를 상속합니다.

Experience Manager Assets에서 프로필 사용과 관련된 중요한 개념은 프로필에 폴더가 할당된다는 것입니다. 프로필 내에는 비디오 프로필 또는 이미지 프로필과 함께 메타데이터 프로필 형식의 설정이 있습니다. 이러한 설정은 폴더의 내용과 하위 폴더를 처리합니다. 따라서 파일 및 폴더의 이름 지정 방법, 하위 폴더 정렬 방법 및 이러한 폴더 내에서 파일을 처리하는 방법은 프로필에서 해당 자산을 처리하는 방식에 큰 영향을 줍니다.
일관되고 적절한 파일 및 폴더 이름 지정 전략 및 좋은 메타데이터 방법을 사용하면 디지털 자산 수집을 최대한 활용하고 올바른 프로필에 의해 올바른 파일이 처리되도록 할 수 있습니다.

## 메타데이터 프로필 추가 {#adding-a-metadata-profile}

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 메타데이터 프로필]**&#x200B;를 클릭한 다음 **[!UICONTROL 만들기]**.
1. 메타데이터 프로필의 제목(예: 샘플 메타데이터)을 입력하고 **[!UICONTROL 제출]**. 메타데이터 프로필에 대한 편집 양식이 표시됩니다.
1. 구성 요소를 클릭하고 해당 속성을 **[!UICONTROL 설정]** 탭. 예를 들어 **[!UICONTROL 설명]** 구성 요소를 만들고 해당 속성을 편집합니다.
에 대해 다음 속성을 편집합니다 **[!UICONTROL 설명]** 구성 요소:

   * **[!UICONTROL 필드 레이블]** - 메타데이터 속성의 표시 이름입니다. 사용자 참조용입니다.
   * **[!UICONTROL 속성에 매핑]** - 이 속성의 값은 저장소에 저장된 자산 노드에 대한 상대 경로/이름을 제공합니다. 값은 항상 `./` 경로가 자산의 노드 아래에 있음을 나타냅니다.

      지정한 값 **[!UICONTROL 속성에 매핑]** 는 자산의 메타데이터 노드 아래에 속성으로 저장됩니다. For example, if you specify . `/jcr:content/metadata/dc:desc` 의 이름으로 **[!UICONTROL 속성에 매핑]**, [!DNL Adobe Experience Manager Assets] 값 저장 `dc:desc` at the asset&#39;s metadata node.

   * **[!UICONTROL 기본값]** - 이 속성을 사용하여 메타데이터 구성 요소에 대한 기본값을 추가합니다. 예를 들어 &quot;My description&quot;을 지정하면 이 값이 속성에 할당됩니다 `dc:desc` at the asset&#39;s metadata node.

      >[!NOTE]
      >
      >새 메타데이터 속성에 기본값 추가(에 존재하지 않음) `/jcr:content/metadata` node)가 기본적으로 자산의 속성 페이지에 속성 및 해당 값을 표시하지 않습니다. 에서 새 속성을 보려면 [!UICONTROL 속성] 페이지에서 해당 스키마 양식을 수정합니다.

1. (Optional) Add more components to the Edit Form from the **[!UICONTROL Build Form]** tab, and configure their properties in the **[!UICONTROL Settings]** tab. The following properties are available from the **[!UICONTROL Build Form]** tab:

| 구성 요소 | 속성 |
|------------------|----------------------------------------------------|
| 섹션 머리글 | 필드 레이블, 설명 |
| 한 줄 텍스트 | 필드 레이블, 속성에 매핑, 기본값 |
| 다중 값 텍스트 | 필드 레이블, 속성에 매핑, 기본값 |
| 숫자 | 필드 레이블, 속성에 매핑, 기본값 |
| 날짜 | 필드 레이블, 속성에 매핑, 기본값 |
| 표준 태그 | 필드 레이블, 속성에 매핑, 기본값, 설명 |

1. 클릭 **[!UICONTROL 완료]**. 메타데이터 프로필이 **[!UICONTROL 메타데이터 프로필]** 페이지.

## 메타데이터 프로필 복사 {#copying-a-metadata-profile}

1. 에서 **[!UICONTROL 메타데이터 프로필]** 페이지에서 메타데이터 프로필을 선택하여 복사본을 만듭니다.
1. 클릭 **[!UICONTROL 복사]** 를 클릭합니다.
1. 에서 **[!UICONTROL 메타데이터 프로필 복사]** 대화 상자에서 메타데이터 프로필의 새 사본의 제목을 입력합니다.
1. 클릭 **[!UICONTROL 복사]**. The copy of the Metadata Profile appears in the list of profiles in the **[!UICONTROL Metadata Profiles]** page.

## 메타데이터 프로필 삭제 {#deleting-a-metadata-profile}

1. 에서 **[!UICONTROL 메타데이터 프로필]** 페이지에서 삭제할 프로필을 선택합니다.
1. 클릭 **[!UICONTROL 메타데이터 프로필 삭제]** 클릭합니다.
1. 대화 상자에서 **[!UICONTROL 삭제]** 삭제 작업을 확인합니다. 메타데이터 프로필이 목록에서 삭제됩니다.

## 폴더에 메타데이터 프로필 적용 {#applying-a-metadata-profile-to-folders}

메타데이터 프로필을 폴더에 할당하면 모든 하위 폴더는 해당 상위 폴더에서 프로필을 자동으로 상속합니다. 다른 프로파일이 하위 폴더에 적용되면 상속이 중지됩니다. 하나의 메타데이터 프로필만 폴더에 할당할 수 있습니다. 따라서 자산을 업로드, 저장, 사용 및 보관하는 폴더 구조를 신중하게 고려하십시오.

폴더에 다른 메타데이터 프로필을 할당한 경우 새 프로필이 이전 프로필을 무시합니다. 이전에 기존 폴더 자산은 변경되지 않은 상태로 유지됩니다. 변경 후 폴더에 추가된 자산에 새 프로필이 적용됩니다. 특정 폴더에 메타데이터 프로필을 적용하거나 모든 자산에 전체적으로 적용할 수 있습니다.

프로필이 할당된 폴더는 카드 이름에 표시되는 프로필의 이름으로 사용자 인터페이스에 표시됩니다.

나중에 변경한 기존 메타데이터 프로필이 이미 있는 폴더에서 자산을 재처리할 수 있습니다. <!-- See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

### 특정 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-specific-folders}

You can apply a metadata profile to a folder from within the **[!UICONTROL Tools]** menu or if you are in the folder, from **[!UICONTROL Properties]**. This section describes how to apply metadata profiles to folders both ways.

Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

나중에 변경한 기존 비디오 프로필이 이미 있는 폴더에서 자산을 재처리할 수 있습니다. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

#### 프로필 사용자 인터페이스의 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

1. 다음으로 이동 **[!UICONTROL 도구 > 자산 > 메타데이터 프로필]**.
1. 폴더 또는 여러 폴더에 적용할 메타데이터 프로필을 선택합니다.
1. 클릭 **[!UICONTROL 폴더에 메타데이터 프로필 적용]** 새로 업로드한 자산을 받는 데 사용할 폴더 또는 여러 폴더를 선택하고 클릭 **[!UICONTROL 완료]**. Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

#### 속성의 폴더에 메타데이터 프로필 적용 {#applying-metadata-profiles-to-folders-from-properties}

1. 왼쪽 레일에서 를 클릭합니다. **[!UICONTROL 자산]** 그런 다음 메타데이터 프로필을 적용할 폴더로 이동합니다.
1. 폴더에서 을 클릭하거나 확인 표시를 클릭하여 선택한 다음 클릭하거나 클릭합니다 **속성**.
1. 을(를) 선택합니다 **[!UICONTROL 메타데이터 프로필]** 탭을 클릭하고 드롭다운 메뉴에서 프로필을 선택한 다음 를 클릭합니다 **[!UICONTROL 저장]**. Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

### 메타데이터 프로필을 전체적으로 적용 {#applying-a-metadata-profile-globally}

폴더에 프로필을 적용하는 것 외에도 폴더에 업로드된 모든 컨텐츠가 전역적으로 적용되도록 프로필을 적용할 수 있습니다 [!DNL Experience Manager Assets] 어떤 폴더에서든 선택된 프로필이 적용되어 있습니다.

나중에 변경한 기존 메타데이터 프로필이 이미 있는 폴더에서 자산을 재처리할 수 있습니다. <!--See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets-in-a-folder-after-you-have-edited-its-processing-profile). -->

**메타데이터 프로필을 전체적으로 적용하려면 다음 중 하나를 수행합니다**

* 다음으로 이동 `https://[aem_server]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` 해당 프로필을 적용하고 **[!UICONTROL 저장]**.

* 다음 노드로 CRXDE Lite으로 이동합니다. `/content/dam/jcr:content`. 속성 추가 `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>`. 클릭 **모두 저장**.

## 폴더에서 메타데이터 프로필 제거 {#removing-a-metadata-profile-from-folders}

폴더에서 메타데이터 프로필을 제거하면 모든 하위 폴더는 해당 상위 폴더에서 프로필을 자동으로 상속받게 됩니다. 그러나 폴더 내에서 발생한 파일의 모든 처리가 그대로 유지됩니다.

You can remove a metadata profile from a folder from within the **Tools** menu or if you are in the folder, from the **Properties**. This section describes how to remove metadata profiles from folders both ways.

### 프로필 사용자 인터페이스를 통해 폴더에서 메타데이터 프로필 제거 {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Experience Manager 로고를 클릭하고 **[!UICONTROL 도구 > 자산 > 메타데이터 프로필]**.
1. 폴더 또는 여러 폴더에서 제거할 메타데이터 프로필을 선택합니다.
1. 클릭 **[!UICONTROL 폴더에서 메타데이터 프로필 제거]** 프로파일을 제거할 폴더 또는 폴더를 여러 개 선택하고 **[!UICONTROL 완료]**.

   이름이 더 이상 폴더 이름 아래에 표시되지 않으므로 메타데이터 프로필이 더 이상 폴더에 적용되지 않았는지 확인할 수 있습니다.

### 속성을 통해 폴더에서 메타데이터 프로필 제거 {#removing-metadata-profiles-from-folders-via-properties}

1. Experience Manager 로고를 클릭하고 탐색합니다 **[!UICONTROL 자산]** 을 클릭하여 메타데이터 프로필을 제거할 폴더로 이동합니다.
1. 폴더에서 확인 표시를 클릭하여 선택한 다음 를 클릭합니다 **[!UICONTROL 속성]**.
1. Select the **[!UICONTROL Metadata Profiles]** tab and select **[!UICONTROL None]** from the drop-down menu and click **[!UICONTROL Save]**. Folders that have a profile already assigned to it are indicated by the display of the profile&#39;s name directly below the folder name.

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
