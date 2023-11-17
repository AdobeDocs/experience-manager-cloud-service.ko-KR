---
title: 디지털 자산 컬렉션 관리
description: Adobe Experience Manager Assets의 컬렉션 개념을 이해합니다. 다른 사용자와 컬렉션, 관리, 편집 및 컬렉션을 관리하는 방법에 대해 알아봅니다.
contentOwner: AG
mini-toc-levels: 1
feature: Collections,Asset Management
role: User
exl-id: b0798adc-56a4-4577-b4ee-8d1fca3bff09
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '2400'
ht-degree: 19%

---

# 컬렉션 관리 {#manage-collections}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-collections.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

컬렉션은 Adobe Experience Manager Assets 내의 에셋 세트입니다. 컬렉션을 사용하여 사용자 간에 자산을 공유합니다. 집합은 정적 집합이거나 검색 결과를 기반으로 하는 동적 집합일 수 있습니다.

폴더와 달리 컬렉션에는 서로 다른 위치의 자산이 포함될 수 있습니다. 보기, 편집 등의 다양한 수준의 권한이 할당된 다양한 사용자와 컬렉션을 공유할 수 있습니다.

사용자와 여러 컬렉션을 공유할 수 있습니다. 각 컬렉션에는 자산에 대한 참조가 포함되어 있습니다. 자산의 참조 무결성은 컬렉션에 간에 유지됩니다.

컬렉션은 에셋을 대조하는 방법을 기반으로 다음과 같은 유형을 갖습니다.

* 자산, 폴더 및 기타 컬렉션의 정적 참조 목록을 포함하는 컬렉션입니다.

* 검색 기준에 따라 자산을 동적으로 포함하는 스마트 컬렉션입니다.

## 컬렉션 콘솔 액세스 {#navigate-the-collections-console}

을(를) 열려면 **[!UICONTROL 컬렉션]** 콘솔:

을(를) 열려면 **[!UICONTROL 컬렉션]** Experience Manager 로고를 선택합니다. 탐색 페이지에서 로 이동합니다. **[!UICONTROL 에셋]** > **[!UICONTROL 컬렉션]**.

## 컬렉션 생성 {#create-a-collection}

다음 중 하나를 사용하여 컬렉션을 만들 수 있습니다. [정적 참조](#create-a-collection-with-static-references) 또는 [검색 기준 기반 필터](#create-a-smart-collection). Lightbox에서 컬렉션을 만들 수도 있습니다.

### 정적 참조를 사용하여 컬렉션 만들기 {#create-a-collection-with-static-references}

정적 참조(예: 에셋, 폴더, 컬렉션, 스핀 세트 및 이미지 세트에 대한 참조가 있는 컬렉션)를 만들 수 있습니다.

1. 다음 위치로 이동 **[!UICONTROL 컬렉션]** 콘솔.
1. 도구 모음에서 를 선택합니다. **[!UICONTROL 만들기]**.
1. 다음에서 **[!UICONTROL 컬렉션 만들기]** 페이지에서 컬렉션에 대한 제목 및 설명(선택 사항)을 입력합니다.
1. Add members to the collection and assign appropriate permissions. Alternatively, select **[!UICONTROL Public Collection]** to allow all users to access the collection.

   >[!NOTE]
   >
   >구성원이 다른 사용자와 컬렉션을 공유할 수 있도록 하려면 다음을 제공합니다. `dam-users` 경로에서 그룹 읽기 권한 `home/users`. 다음 위치에서 사용자에게 권한 부여: `/content/dam/collections` 사용자가 팝업 목록에서 컬렉션을 볼 수 있는 위치입니다. 또는 사용자를 의 일부로 만들 수 있습니다 `dam-users` 그룹입니다.

1. (선택 사항) 컬렉션에 대한 썸네일 이미지를 추가합니다.
1. 선택 **[!UICONTROL 만들기]**&#x200B;을 선택한 다음 을 선택합니다 **[!UICONTROL 확인]** 대화 상자를 닫습니다. A collection with the specified title and properties is opened in the Collections console.

   >[!NOTE]
   >
   >Experience Manager Assets을 사용하면 에셋 폴더에 대한 검토 작업을 만드는 방법과 유사한 컬렉션에 대한 검토 작업을 만들 수 있습니다.

   컬렉션에 에셋을 추가하려면 에셋 사용자 인터페이스로 이동합니다. 자세한 내용은 [컬렉션에 에셋 추가](#add-assets-to-a-collection).

### 드롭 영역을 사용하여 컬렉션 만들기 {#create-collections-using-dropzone}

에셋 UI에서 컬렉션으로 에셋을 드래그할 수 있습니다. 컬렉션의 사본을 만들고 에셋을 드래그할 수도 있습니다.

1. 에셋 사용자 인터페이스에서 컬렉션에 추가할 에셋을 선택합니다.
1. 에셋을 (으)로 드래그 **[!UICONTROL 컬렉션에 놓기]** 영역. 또는 **[!UICONTROL 대상 컬렉션]** 아이콘을 클릭합니다.
1. 다음에서 **[!UICONTROL 컬렉션에 추가]** 페이지에서 **[!UICONTROL 컬렉션 만들기]** 아이콘을 클릭합니다. 기존 컬렉션에 에셋을 추가하려면 페이지에서 해당 에셋을 선택하고 을 선택합니다 **[!UICONTROL 추가]**. By default, the most recently updated collection is selected.
1. In the **[!UICONTROL Create New Collection]** dialog, specify a name for the collection. If you want the collection to be accessible to all users, select **[!UICONTROL Public Collection]**.
1. 선택 **[!UICONTROL 계속]** 컬렉션을 만들려면

### 스마트 컬렉션 만들기 {#create-a-smart-collection}

스마트 컬렉션은 검색 기준을 사용하여 자산을 동적으로 채웁니다. 폴더나 파일 및 폴더가 아닌 파일만 사용하여 스마트 컬렉션을 만들 수 있습니다.

1. 에셋 UI로 이동하여 **[!UICONTROL 검색]** 아이콘.
1. Omni Search 상자에 검색 키워드를 입력하고 다음을 선택합니다. `Enter`. [필터] 패널을 표시하고 [검색] 패널에서 검색 필터를 적용하려면 [전역 탐색] 아이콘을 선택합니다.
1. 다음에서 **[!UICONTROL 파일 및 폴더]** 목록, 선택 **[!UICONTROL 파일]**.
1. 선택 **[!UICONTROL 스마트 컬렉션 저장]**.
1. 컬렉션 이름을 지정합니다. 선택 **[!UICONTROL 공용]** 뷰어 역할이 있는 DAM 사용자 그룹을 스마트 컬렉션에 추가합니다.

   >[!NOTE]
   >
   >다음을 선택하는 경우 **[!UICONTROL 공용]**, 스마트 컬렉션을 만든 후에는 소유자 역할이 있는 모든 사용자가 스마트 컬렉션을 사용할 수 있습니다. 을(를) 취소하면 **[!UICONTROL 공용]** 옵션을 사용하면 DAM 사용자 그룹이 더 이상 스마트 컬렉션과 연결되지 않습니다.

1. 선택 **[!UICONTROL 저장]** 스마트 컬렉션을 만든 다음 메시지 상자를 닫아 프로세스를 완료합니다. The new smart collection is also added to the **[!UICONTROL Saved Searches]** list.
The label of the **[!UICONTROL Create Smart Selection]** button changes to **[!UICONTROL Edit Smart Selection]**. To edit the settings of the smart collection, select **[!UICONTROL Files]** from the **[!UICONTROL Files &amp; Folders]** list. 그런 다음 **[!UICONTROL 스마트 선택 항목 편집]** 단추를 클릭합니다.

## 컬렉션에 에셋 추가 {#add-assets-to-a-collection}

참조된 에셋 또는 폴더 목록이 포함된 컬렉션에 에셋을 추가할 수 있습니다.

>[!NOTE]
>
>스마트 컬렉션은 검색 쿼리를 사용하여 자산을 채웁니다. 따라서 에셋 및 폴더에 대한 정적 참조를 에셋 및 폴더에 적용할 수 없습니다.

1. 에셋 UI에서 컬렉션에 추가하려는 에셋의 위치로 이동합니다.
1. 에셋을 선택하고 **[!UICONTROL 대상 컬렉션]** 아이콘을 클릭합니다. 또는 에셋을 **[!UICONTROL 컬렉션에 놓기]** 영역. 놓기 영역이 활성화되고 해당 레이블이 로 변경되면 마우스 단추를 놓습니다. **[!UICONTROL 추가하려면 놓기]**.
1. 다음에서 **[!UICONTROL 컬렉션에 추가]** 페이지에서 에셋을 추가할 컬렉션을 선택합니다.
1. 선택 **[!UICONTROL 추가]**&#x200B;을 클릭한 다음 확인 메시지를 닫습니다. 자산이 컬렉션에 추가됩니다.

## 스마트 컬렉션 편집 {#edit-a-smart-collection}

스마트 컬렉션은 검색을 저장하여 빌드되므로 의 검색 매개 변수를 수정하여 콘텐츠를 변경할 수 있습니다. [저장된 검색](#saved-searches).

1. Assets 사용자 인터페이스에서 다음을 선택합니다. **[!UICONTROL 검색]** 아이콘을 클릭합니다.
1. Omnisearch 상자에 커서를 놓고 `Enter` 키.
1. GlobalNav 아이콘을 선택하여 필터 패널을 표시합니다.
1. From the **[!UICONTROL Saved Searches]** list, select the smart collection you want to modify. The Search panel displays the filters configured for the saved search.
1. 다음에서 **[!UICONTROL 파일 및 폴더]** 목록, 선택 **[!UICONTROL 파일]**.
1. 필요에 따라 하나 이상의 필터를 수정합니다. 선택 **[!UICONTROL 스마트 컬렉션 편집]**. 스마트 컬렉션의 이름을 편집할 수도 있습니다.
1. **[!UICONTROL 저장]**&#x200B;을 선택합니다. 다음 **[!UICONTROL 스마트 컬렉션 편집]** 대화 상자가 나타납니다.
1. 선택 **[!UICONTROL 덮어쓰기]** 원본 스마트 컬렉션을 편집된 컬렉션으로 바꿉니다. 또는 을 선택합니다. **[!UICONTROL 다른 이름으로 저장]** 편집한 컬렉션을 별도로 저장합니다.
1. 확인 대화 상자에서 다음을 선택합니다 **[!UICONTROL 저장]** 을 클릭하여 프로세스를 완료합니다.

## 컬렉션 메타데이터 보기 및 편집 {#view-and-edit-collection-metadata}

컬렉션 메타데이터는 추가된 태그를 포함하여 컬렉션에 대한 데이터로 구성됩니다.

1. 컬렉션 콘솔에서 컬렉션을 선택하고 **[!UICONTROL 속성]** 아이콘을 클릭합니다.
1. In the **[!UICONTROL Collection Metadata]** page, view the collection metadata from the **[!UICONTROL Basic]** and **Advanced** tabs.
1. 필요에 따라 메타데이터를 수정한 다음 를 선택합니다 **[!UICONTROL 저장 및 닫기]** 을 클릭하여 변경 내용을 저장합니다.

### 컬렉션 메타데이터 일괄 편집 {#edit-collection-metadata-in-bulk}

여러 컬렉션의 메타데이터를 동시에 편집할 수 있습니다. 이 기능을 사용하면 여러 컬렉션의 공통 메타데이터를 빠르게 복제할 수 있습니다.

1. 컬렉션 콘솔에서 메타데이터를 편집할 컬렉션을 두 개 이상 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]** 아이콘.
1. In the **[!UICONTROL Collection Metadata]** page, edit the metadata under the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs, as necessary.
1. 선택 **[!UICONTROL 저장 및 닫기]** 을 클릭하고 확인 대화 상자를 닫아 프로세스를 완료합니다.
1. To append the new metadata with the existing metadata, select **[!UICONTROL Apend mode]**. If you do not select this option, the new metadata replaces the existing metadata in the fields. **[!UICONTROL 제출]**&#x200B;을 선택합니다.

   >[!NOTE]
   >
   >The Append mode works only for fields that can contain multiple values. For fields that can contain only a single value, the new metadata is not appended to the existing value in the field even if you select **[!UICONTROL Append mode]**.

## 검색 {#searching}

컬렉션 내의 검색 기능은 두 가지를 모두 지원합니다 [컬렉션 검색](#search-collections) 및 [컬렉션 내에서 에셋 검색](#search-within-collections).

### 컬렉션 검색 {#search-collections}

컬렉션 콘솔에서 컬렉션을 검색할 수 있습니다. Omnisearch 상자에서 키워드로 검색할 때, [!DNL Experience Manager Assets] 컬렉션 이름, 메타데이터 및 컬렉션에 추가된 태그를 검색합니다.

최상위 수준에서 컬렉션을 검색하는 경우 검색 결과에 개별 컬렉션만 반환됩니다. 컬렉션 내의 자산 또는 폴더는 제외됩니다. 기타 모든 경우(예: 개별 컬렉션 또는 폴더 계층 구조 내)에는 모든 관련 에셋, 폴더 및 컬렉션이 반환됩니다.

### 컬렉션 내 검색 {#search-within-collections}

컬렉션 콘솔에서 컬렉션을 선택하여 엽니다.

컬렉션 내에서 [!DNL Experience Manager] 검색은 현재 보고 있는 컬렉션 내의 자산(및 해당 태그와 메타데이터)으로 제한됩니다. 폴더 내에서 검색하면 현재 폴더 내에서 일치하는 모든 에셋 및 하위 폴더가 반환됩니다. 컬렉션 내에서 검색할 때 일치하는 에셋, 폴더 및 컬렉션의 직접 구성원인 다른 컬렉션만 반환됩니다.

## 컬렉션 설정 편집 {#edit-collection-settings}

제목 및 설명과 같은 컬렉션 설정을 편집하거나 멤버를 컬렉션에 추가할 수 있습니다.

1. 컬렉션을 선택하고 **[!UICONTROL 설정]** 아이콘을 클릭합니다. 또는 **[!UICONTROL 설정]** 컬렉션 썸네일의 빠른 작업
1. Modify the collection settings in the **[!UICONTROL Collection Settings]** page. For example, modify the collection title, descriptions, members, and permissions as discussed in [Add collections](#create-a-collection).
1. 선택 **[!UICONTROL 저장]** 변경 내용을 저장합니다.

## 컬렉션 삭제 {#delete-a-collection}

1. 컬렉션 콘솔에서 컬렉션을 한 개 이상 선택하고 도구 모음에서 삭제 아이콘을 선택합니다.
1. 대화 상자에서 다음을 선택합니다. **[!UICONTROL 삭제]** 삭제 작업을 확인합니다.

   >[!NOTE]
   >
   >다음 방법으로 스마트 컬렉션을 삭제할 수도 있습니다. [저장된 검색 삭제](#saved-searches).

## 컬렉션 다운로드 {#download-a-collection}

컬렉션을 다운로드하면 폴더 및 하위 컬렉션을 포함하여 컬렉션 내의 전체 자산 계층이 다운로드됩니다.

1. 컬렉션 콘솔에서 다운로드할 컬렉션을 한 개 이상 선택합니다.
1. 도구 모음에서 다운로드 아이콘을 선택합니다.
1. 다음에서 **[!UICONTROL 다운로드]** 대화 상자, 선택 **[!UICONTROL 다운로드]**. 컬렉션 내의 에셋 렌디션을 다운로드하려면 다음을 선택합니다 **[!UICONTROL 표현물]**. <!-- Select the **[!UICONTROL Email]** option to send an email notification to the owner of the collection. -->

   다운로드할 컬렉션을 선택하면 컬렉션 아래의 전체 폴더 계층 구조가 다운로드됩니다. 다운로드한 각 컬렉션(상위 컬렉션 아래에 중첩된 하위 컬렉션의 자산 포함)을 개별 폴더에 포함하려면 다음을 선택합니다. **[!UICONTROL 각 자산에 대해 별도의 폴더 만들기]**.

## 여러 컬렉션의 메타데이터 속성 편집 {#editing-metadata-properties-of-multiple-collections}

Enterprise Manager Assets Adobe을 사용하면 많은 컬렉션의 메타데이터를 일괄적으로 편집할 수 있습니다. 사용 [!UICONTROL 속성] 여러 컬렉션에서 메타데이터 변경을 수행할 페이지(예: 메타데이터 속성을 공통 값으로 변경하거나 태그를 추가 또는 수정).

메타데이터 사용자 정의하기 [!UICONTROL 속성] 메타데이터 속성 추가, 수정, 삭제를 포함한 페이지는 스키마 편집기를 사용합니다.

>[!NOTE]
>
>벌크 편집 메서드는 컬렉션에서 사용할 수 있는 에셋에 대해 작동합니다. 여러 폴더에서 사용하거나 공통 기준과 일치하는 에셋의 경우 다음 작업을 수행할 수 있습니다. [검색 후 메타데이터 벌크 업데이트](/help/assets/search-assets.md#metadata-updates).

1. 컬렉션 콘솔에서 편집할 컬렉션을 선택합니다.
1. 도구 모음에서 를 선택합니다. **[!UICONTROL 속성]** 을(를) 열려면 [!UICONTROL 속성] 선택한 컬렉션에 대한 페이지입니다.
1. 다양한 탭에서 선택한 컬렉션의 메타데이터 속성을 수정합니다.

   >[!NOTE]
   >
   >선택한 컬렉션에 대해 추가하는 메타데이터는 태그를 제외한 이러한 컬렉션의 이전 메타데이터를 덮어씁니다. 에 추가하는 모든 태그 **[!UICONTROL 태그]** 필드는 메타데이터의 기존 태그 목록에 추가됩니다.

1. 특정 컬렉션에 대한 메타데이터 속성을 보려면 컬렉션 목록의 나머지 컬렉션 선택을 취소하십시오. 메타데이터 편집기 필드는 특정 컬렉션의 메타데이터로 채워집니다.

   >[!NOTE]
   >
   >* 컬렉션 등록 정보 페이지에서 선택을 취소하여 컬렉션 목록에서 컬렉션을 제거할 수 있습니다. 컬렉션 목록에는 기본적으로 모든 컬렉션이 선택되어 있습니다. 제거한 컬렉션에 대한 메타데이터가 업데이트되지 않습니다.
   >* 목록의 맨 위에서 옆의 확인란을 선택합니다 **[!UICONTROL 제목]** 컬렉션 선택과 목록 지우기 간을 전환합니다.

1. 변경 사항을 저장합니다.

## 중첩 컬렉션 만들기 {#create-nested-collections}

컬렉션을 다른 컬렉션에 추가하여 중첩된 컬렉션을 만들 수 있습니다.

1. 컬렉션 콘솔에서 원하는 컬렉션이나 컬렉션 그룹을 선택하고 을 선택합니다 **[!UICONTROL 대상 컬렉션]** 을 클릭합니다.
1. 다음에서 **[!UICONTROL 컬렉션에 추가]** 페이지에서 컬렉션을 추가할 컬렉션을 선택합니다.

   >[!NOTE]
   >
   >최근에 업데이트된 컬렉션은 기본적으로 **[!UICONTROL 컬렉션에 추가]** 페이지를 가리키도록 업데이트하는 중입니다.

1. 선택 **[!UICONTROL 추가]**. 컬렉션이 의 대상 컬렉션에 추가되었음을 확인하는 메시지가 표시됩니다. **[!UICONTROL 대상 선택]** 페이지를 가리키도록 업데이트하는 중입니다. 메시지를 닫아 프로세스를 완료합니다.

>[!NOTE]
>
>스마트 컬렉션은 중첩될 수 없습니다. 즉, 스마트 컬렉션은 다른 컬렉션을 포함할 수 없습니다.

## 저장된 검색 {#saved-searches}

In the Assets user interface, you can search or filter assets based on certain rules, search criteria, or custom search facets. If you save these as **[!UICONTROL Saved Searches]**, you can access them later from the **[!UICONTROL Saved Searches]** list in the Filter panel. Creating a saved search also creates a smart collection.

Saved searches are created when you create a smart collection. Smart collections are automatically added to the **[!UICONTROL Saved Searches]** list. The Saved Searches query for the collection is saved in the `dam:query` property in CRXDE at the relative location `/content/dam/collections/`. 목록에 표시된 저장된 검색에서 및 저장할 수 있는 검색에는 제한이 없습니다.

>[!NOTE]
>
>정적 컬렉션을 공유하는 것과 동일한 방식으로 스마트 컬렉션을 공유할 수 있습니다.

저장된 검색을 편집하는 것은 스마트 컬렉션을 편집하는 것과 같습니다. 자세한 내용은 [스마트 컬렉션 편집](#edit-a-smart-collection).

저장된 검색을 삭제하려면 다음 단계를 따르십시오.

1. Assets 사용자 인터페이스의 도구 모음에서 검색 아이콘을 선택합니다.

1. Omnisearch 필드에 커서를 놓고 `Enter` 키.
1. GlobalNav 아이콘을 선택하여 필터 패널을 표시합니다.
1. 다음에서 **[!UICONTROL 저장한 검색 결과]** 목록, 선택 **[!UICONTROL 삭제]** 삭제할 스마트 컬렉션 옆에 있습니다.
1. 대화 상자에서 다음을 선택합니다. **[!UICONTROL 삭제]** 저장된 검색을 삭제합니다.

## 컬렉션에서 워크플로우 실행 {#run-a-workflow-on-a-collection}

컬렉션 내의 자산에 대해 워크플로우를 실행할 수 있습니다. 컬렉션에 중첩된 컬렉션이 포함된 경우 워크플로는 중첩된 컬렉션 내의 에셋에서도 실행됩니다. 그러나 컬렉션과 중첩된 컬렉션에 중복 에셋이 포함된 경우 워크플로우는 이러한 에셋에 대해 한 번만 실행됩니다.

1. 컬렉션 콘솔에서 워크플로우를 실행할 컬렉션을 선택합니다.
1. GlobalNav 아이콘을 선택하고 **[!UICONTROL 타임라인]** 목록에서 삭제할 수 있습니다.
1. 타임라인에서 하단의 캐럿 아이콘을 선택하거나 탭한 다음 을 선택합니다 **[!UICONTROL 워크플로우 시작]**.
1. In the **[!UICONTROL Start Workflow]** section, select a workflow model from the list. For example, select the **[!UICONTROL DAM Update Asset]** model.
1. 워크플로우의 제목을 입력하고 선택 **[!UICONTROL 시작]**.
1. 대화 상자에서 다음을 선택합니다. **[!UICONTROL 진행]**. 워크플로우는 컬렉션의 모든 에셋에서 실행됩니다.

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
* [일괄 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [컬렉션에 대한 검토 작업 만들기](/help/assets/bulk-approval.md)
