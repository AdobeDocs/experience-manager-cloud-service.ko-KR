---
title: 디지털 자산 컬렉션 관리
description: Adobe Experience Manager Assets의 컬렉션 개념을 이해합니다. 다른 사용자와 컬렉션, 관리, 편집 및 컬렉션을 수행하는 방법을 알아봅니다.
contentOwner: AG
mini-toc-levels: 1
feature: Collections,Asset Management
role: User
exl-id: b0798adc-56a4-4577-b4ee-8d1fca3bff09
source-git-commit: 80ac947976bab2b0bfedb4ff9d5dd4634de6b4fc
workflow-type: tm+mt
source-wordcount: '2447'
ht-degree: 23%

---

# 컬렉션 관리 {#manage-collections}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-collections.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

컬렉션은 Adobe Experience Manager Assets 내의 자산 세트입니다. 컬렉션을 사용하여 사용자 간에 에셋을 공유합니다. 이 집합은 검색 결과를 기반으로 하는 정적 컬렉션 또는 동적 컬렉션일 수 있습니다.

폴더와 달리 컬렉션에는 서로 다른 위치의 에셋이 포함될 수 있습니다. 보기, 편집 등을 포함하여 서로 다른 수준의 권한이 할당된 다양한 사용자와 컬렉션을 공유할 수 있습니다.

사용자와 여러 컬렉션을 공유할 수 있습니다. 각 컬렉션에는 에셋에 대한 참조가 포함되어 있습니다. 에셋의 참조 무결성은 컬렉션에 간에 유지됩니다.

컬렉션은 자산을 수집하는 방식에 따라 다음 유형입니다.

* 자산, 폴더 및 기타 컬렉션의 정적 참조 목록을 포함하는 컬렉션입니다.

* 검색 기준에 따라 자산을 동적으로 포함하는 스마트 컬렉션입니다.

## 컬렉션 콘솔 액세스 {#navigate-the-collections-console}

를 열려면 **[!UICONTROL 컬렉션]** 콘솔:

를 열려면 **[!UICONTROL 컬렉션]**&#x200B;에서 Experience Manager 로고를 탭하거나 클릭합니다. 탐색 페이지에서 로 이동합니다. **[!UICONTROL 자산]** > **[!UICONTROL 컬렉션]**.

## 컬렉션 생성 {#create-a-collection}

다음 중 한 방법으로 컬렉션을 만들 수 있습니다 [정적 참조](#create-a-collection-with-static-references) 또는 [검색 기준 기반 필터](#create-a-smart-collection). Lightbox에서 컬렉션을 만들 수도 있습니다.

### 정적 참조를 사용하여 컬렉션 만들기 {#create-a-collection-with-static-references}

정적 참조와 함께 컬렉션을 만들 수 있습니다. 예를 들어 자산, 폴더, 컬렉션, 스핀 세트 및 이미지 세트에 대한 참조가 있는 컬렉션입니다.

1. 로 이동합니다 **[!UICONTROL 컬렉션]** 콘솔.
1. 도구 모음에서 탭/클릭 **[!UICONTROL 만들기]**.
1. 에서 **[!UICONTROL 컬렉션 만들기]** 페이지에서 컬렉션에 대한 제목과 선택적 설명을 입력합니다.
1. Add members to the collection and assign appropriate permissions. Alternatively, select **[!UICONTROL Public Collection]** to allow all users to access the collection.

   >[!NOTE]
   >
   >구성원이 다른 사용자와 컬렉션을 공유할 수 있도록 하려면 `dam-users` 경로에서 읽기 권한 그룹 `home/users`. 사용자를에 대한 권한 부여 `/content/dam/collections` 사용자가 팝업 목록에서 컬렉션을 볼 수 있는 위치입니다. 또는 사용자를 `dam-users` 그룹에 속해 있어야 합니다.

1. (선택 사항) 컬렉션에 대한 축소판 이미지를 추가합니다.
1. Tap/click **[!UICONTROL Create]**, and then tap/click **[!UICONTROL OK]** to close the dialog. A collection with the specified title and properties is opened in the Collections console.

   >[!NOTE]
   >
   >Experience Manager Assets을 사용하면 자산 폴더에 대한 검토 작업을 만드는 방법과 유사한 방식으로 컬렉션에 대한 검토 작업을 만들 수 있습니다.

   컬렉션에 자산을 추가하려면 자산 사용자 인터페이스로 이동합니다. 자세한 내용은 [컬렉션에 자산 추가](#add-assets-to-a-collection).

### 드롭존을 사용하여 컬렉션 만들기 {#create-collections-using-dropzone}

자산 UI에서 컬렉션으로 자산을 드래그할 수 있습니다. 컬렉션의 사본을 만들고 자산을 여기에 드래그할 수도 있습니다.

1. Assets 사용자 인터페이스에서 컬렉션에 추가할 자산을 선택합니다.
1. 자산을 로 드래그합니다. **[!UICONTROL 컬렉션에 놓기]** 영역. 또는, **[!UICONTROL 대상 컬렉션]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.
1. In the **[!UICONTROL Add To Collection]** page, tap/click the **[!UICONTROL Create Collection]** icon from the toolbar. If you want to add the assets to an existing collection, select it from the page, and tap/click **[!UICONTROL Add]**. By default, the most recently updated collection is selected.
1. In the **[!UICONTROL Create New Collection]** dialog, specify a name for the collection. If you want the collection to be accessible to all users, select **[!UICONTROL Public Collection]**.
1. 탭/클릭 **[!UICONTROL 계속]** 컬렉션을 만들려면

### 스마트 컬렉션 만들기 {#create-a-smart-collection}

Smart Collection에서는 검색 기준을 사용하여 자산을 동적으로 채웁니다. 폴더나 파일 및 폴더가 아니라 파일만 사용하여 Smart Collection을 만들 수 있습니다.

1. Navigate to the Assets UI, and tap/click the **[!UICONTROL Search]** icon.
1. 옴니 검색 상자에 검색 키워드를 입력하고 을 선택합니다 `Enter`. GlobalNav 아이콘을 탭/클릭하여 필터 패널을 표시하고 검색 패널에서 검색 필터를 적용합니다.
1. 에서 **[!UICONTROL 파일 및 폴더]** 목록, 선택 **[!UICONTROL 파일]**.
1. 탭/클릭 **[!UICONTROL 스마트 컬렉션 저장]**.
1. 컬렉션 이름을 지정합니다. 선택 **[!UICONTROL 공용]** 뷰어 역할을 가진 DAM 사용자 그룹을 스마트 컬렉션에 추가

   >[!NOTE]
   >
   >선택하는 경우 **[!UICONTROL 공용]**&#x200B;을 만들면 스마트 컬렉션을 만든 후 소유자 역할을 가진 모든 사람이 스마트 컬렉션을 사용할 수 있습니다. 취소 **[!UICONTROL 공용]** 옵션을 선택하면 DAM 사용자 그룹이 더 이상 스마트 컬렉션과 연결되지 않습니다.

1. Tap/click **[!UICONTROL Save]** to create the smart collection, and then close the message box to complete the process. The new smart collection is also added to the **[!UICONTROL Saved Searches]** list.
The label of the **[!UICONTROL Create Smart Selection]** button changes to **[!UICONTROL Edit Smart Selection]**. To edit the settings of the smart collection, select **[!UICONTROL Files]** from the **[!UICONTROL Files &amp; Folders]** list. Then, tap/click the **[!UICONTROL Edit Smart Selection]** button.

## 컬렉션에 에셋 추가 {#add-assets-to-a-collection}

참조된 자산 또는 폴더 목록을 포함하는 컬렉션에 자산을 추가할 수 있습니다.

>[!NOTE]
>
>스마트 컬렉션은 검색 쿼리를 사용하여 자산을 채웁니다. 따라서 자산 및 폴더에 대한 정적 참조는 적용할 수 없습니다.

1. Assets UI에서 컬렉션에 추가할 자산의 위치로 이동합니다.
1. 자산을 선택하고 을(를) 탭/클릭합니다. **[!UICONTROL 대상 컬렉션]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다. 또는 자산을 로 드래그할 수 있습니다 **[!UICONTROL 컬렉션에 놓기]** 영역. 드롭 영역이 활성화되고 레이블이 로 변경되면 마우스 단추를 놓습니다 **[!UICONTROL 추가할 드롭]**.
1. 에서 **[!UICONTROL 컬렉션에 추가]** 페이지에서 자산을 추가할 컬렉션을 선택합니다.
1. 탭/클릭 **[!UICONTROL 추가]**&#x200B;를 클릭한 다음 확인 메시지를 닫습니다. 자산이 컬렉션에 추가됩니다.

## 스마트 컬렉션 편집 {#edit-a-smart-collection}

스마트 컬렉션은 검색을 저장하여 작성되므로, [저장된 검색](#saved-searches).

1. Assets 사용자 인터페이스에서 를 탭/클릭합니다. **[!UICONTROL 검색]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.
1. Omnisearch 상자에 커서를 놓고 `Enter` 키.
1. [전역 탐색] 아이콘을 탭/클릭하여 [필터] 패널을 표시합니다.
1. From the **[!UICONTROL Saved Searches]** list, select the smart collection you want to modify. The Search panel displays the filters configured for the saved search.
1. 에서 **[!UICONTROL 파일 및 폴더]** 목록, 선택 **[!UICONTROL 파일]**.
1. 필요에 따라 하나 이상의 필터를 수정합니다. 탭/클릭 **[!UICONTROL 스마트 컬렉션 편집]**. 스마트 컬렉션의 이름을 편집할 수도 있습니다.
1. 탭/클릭 **[!UICONTROL 저장]**. 다음 **[!UICONTROL 스마트 컬렉션 편집]** 대화 상자가 나타납니다.
1. 탭/클릭 **[!UICONTROL 덮어쓰기]** 원본 스마트 컬렉션을 편집된 컬렉션으로 대체하려면 또는 을 선택합니다 **[!UICONTROL 다른 이름으로 저장]** 편집한 컬렉션을 별도로 저장하려면
1. 확인 대화 상자에서 를 탭/클릭합니다 **[!UICONTROL 저장]** 프로세스를 완료합니다.

## 컬렉션 메타데이터 보기 및 편집 {#view-and-edit-collection-metadata}

컬렉션 메타데이터는 추가된 태그를 포함하여 컬렉션에 대한 데이터를 포함합니다.

1. 컬렉션 콘솔에서 컬렉션을 선택하고 **[!UICONTROL 속성]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.
1. In the **[!UICONTROL Collection Metadata]** page, view the collection metadata from the **[!UICONTROL Basic]** and **Advanced** tabs.
1. 필요에 따라 메타데이터를 수정한 후 탭/클릭합니다 **[!UICONTROL 저장 및 닫기]** 도구 모음에서 변경 사항을 저장합니다.

### 컬렉션 메타데이터 일괄 편집 {#edit-collection-metadata-in-bulk}

여러 컬렉션의 메타데이터를 동시에 편집할 수 있습니다. 이 기능을 사용하면 여러 컬렉션에서 공통 메타데이터를 빠르게 복제할 수 있습니다.

1. 컬렉션 콘솔에서 메타데이터를 편집할 컬렉션을 두 개 이상 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]** 아이콘.
1. In the **[!UICONTROL Collection Metadata]** page, edit the metadata under the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs, as necessary.
1. 탭/클릭 **[!UICONTROL 저장 및 닫기]** 도구 모음에서 확인 대화 상자를 닫고 프로세스를 완료합니다.
1. To append the new metadata with the existing metadata, select **[!UICONTROL Apend mode]**. If you do not select this option, the new metadata replaces the existing metadata in the fields. Tap/click **[!UICONTROL Submit]**.

   >[!NOTE]
   >
   >The Append mode works only for fields that can contain multiple values. For fields that can contain only a single value, the new metadata is not appended to the existing value in the field even if you select **[!UICONTROL Append mode]**.

## 검색 {#searching}

컬렉션 내의 검색 기능은 두 기능을 모두 지원합니다 [컬렉션 검색](#search-collections) 및 [컬렉션 내에서 자산 검색](#search-within-collections).

### 컬렉션 검색 {#search-collections}

컬렉션 콘솔에서 컬렉션을 검색할 수 있습니다. Omnisearch 상자에서 키워드로 검색할 경우, [!DNL Experience Manager Assets] 컬렉션 이름, 메타데이터 및 컬렉션에 추가된 태그를 검색합니다.

최상위 수준에서 컬렉션을 검색하는 경우 개별 컬렉션만 검색 결과에 반환됩니다. 컬렉션 내의 자산 또는 폴더는 제외됩니다. 다른 모든 경우(예: 개별 컬렉션 내 또는 폴더 계층 구조) 모든 관련 자산, 폴더 및 컬렉션이 반환됩니다.

### 컬렉션 내에서 검색 {#search-within-collections}

컬렉션 콘솔에서 컬렉션을 탭/클릭하여 엽니다.

컬렉션 내에서, [!DNL Experience Manager] 검색 기능은 보고 있는 컬렉션 내의 자산(및 해당 태그 및 메타데이터)으로 제한됩니다. 폴더 내에서 검색하면 현재 폴더 내에서 일치하는 모든 자산 및 하위 폴더가 반환됩니다. 컬렉션 내에서 검색할 때 컬렉션의 직접 멤버인 일치하는 자산, 폴더 및 기타 컬렉션만 반환됩니다.

## 컬렉션 설정 편집 {#edit-collection-settings}

제목 및 설명과 같은 컬렉션 설정을 편집하거나 컬렉션에 구성원을 추가할 수 있습니다.

1. 컬렉션을 선택하고 **[!UICONTROL 설정]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다. 또는 **[!UICONTROL 설정]** 컬렉션 축소판에서의 빠른 작업.
1. Modify the collection settings in the **[!UICONTROL Collection Settings]** page. For example, modify the collection title, descriptions, members, and permissions as discussed in [Add collections](#create-a-collection).
1. 탭/클릭 **[!UICONTROL 저장]** 변경 사항을 저장하려면 을 클릭합니다.

## 컬렉션 삭제 {#delete-a-collection}

1. 컬렉션 콘솔에서 하나 이상의 컬렉션을 선택하고 도구 모음에서 삭제 아이콘을 탭/클릭합니다.
1. 대화 상자에서 을 탭/클릭합니다. **[!UICONTROL 삭제]** 를 클릭하여 삭제 작업을 확인합니다.

   >[!NOTE]
   >
   >다음 방법으로 스마트 컬렉션을 삭제할 수도 있습니다 [저장된 검색 삭제](#saved-searches).

## 컬렉션 다운로드 {#download-a-collection}

컬렉션을 다운로드하면 폴더 및 하위 컬렉션을 포함하여 컬렉션 내의 자산의 전체 계층 구조가 다운로드됩니다.

1. 컬렉션 콘솔에서 다운로드할 컬렉션을 하나 이상 선택합니다.
1. 도구 모음에서 다운로드 아이콘을 탭/클릭합니다.
1. 에서 **[!UICONTROL 다운로드]** 대화 상자, 탭/클릭 **[!UICONTROL 다운로드]**. 컬렉션 내에서 자산의 표현물을 다운로드하려면 를 선택합니다 **[!UICONTROL 표현물]**. <!-- Select the **[!UICONTROL Email]** option to send an email notification to the owner of the collection. -->

   다운로드할 컬렉션을 선택하면 컬렉션 아래의 전체 폴더 계층 구조가 다운로드됩니다. 개별 폴더에 다운로드한 각 컬렉션(상위 컬렉션 아래에 중첩된 하위 컬렉션의 자산 포함)을 포함하려면 를 선택합니다 **[!UICONTROL 각 자산에 대해 별도의 폴더를 만듭니다]**.

## 여러 컬렉션의 메타데이터 속성 편집 {#editing-metadata-properties-of-multiple-collections}

Adobe Enterprise Manager Assets를 사용하면 많은 컬렉션의 메타데이터를 일괄적으로 편집할 수 있습니다. 를 사용하십시오 [!UICONTROL 속성] 여러 컬렉션에서 메타데이터 변경 작업을 수행할 수 있습니다. 예를 들어 메타데이터 속성을 공통 값으로 변경하거나 태그를 추가 또는 수정합니다.

메타데이터를 사용자 지정하는 방법 [!UICONTROL 속성] 페이지에서 메타데이터 속성 추가, 수정, 삭제를 비롯한 스키마 편집기를 사용합니다.

>[!NOTE]
>
>벌크 편집 방법은 컬렉션에서 사용할 수 있는 자산에 대해 작동합니다. 여러 폴더 간에 사용할 수 있거나 공통 기준과 일치하는 자산의 경우 다음을 수행할 수 있습니다 [검색 후 메타데이터 대량 업데이트](/help/assets/search-assets.md#metadata-updates).

1. 컬렉션 콘솔에서 편집할 컬렉션을 선택합니다.
1. 도구 모음에서 탭/클릭 **[!UICONTROL 속성]** 열다 [!UICONTROL 속성] 선택한 컬렉션에 대한 페이지입니다.
1. 다양한 탭에서 선택한 컬렉션의 메타데이터 속성을 수정합니다.

   >[!NOTE]
   >
   >선택한 컬렉션에 대해 추가하는 메타데이터는 태그를 제외하고 이러한 컬렉션에 대한 이전 메타데이터를 덮어씁니다. 에 추가하는 모든 태그 **[!UICONTROL 태그]** 필드가 메타데이터의 기존 태그 목록에 추가됩니다.

1. 특정 컬렉션에 대한 메타데이터 속성을 보려면 컬렉션 목록에서 나머지 컬렉션 선택을 취소합니다. 메타데이터 편집기 필드는 특정 컬렉션의 메타데이터로 채워집니다.

   >[!NOTE]
   >
   >* 컬렉션 속성 페이지에서 선택을 취소하여 컬렉션 목록에서 컬렉션을 제거할 수 있습니다. 컬렉션 목록에는 기본적으로 선택된 모든 컬렉션이 있습니다. 제거하는 컬렉션의 메타데이터는 업데이트되지 않습니다.
   >* 목록의 맨 위에서 가까운 확인란을 선택합니다 **[!UICONTROL 제목]** 컬렉션 선택 및 목록 지우기 간을 전환하려면.


1. 변경 사항을 저장합니다.

## 중첩된 컬렉션 만들기 {#create-nested-collections}

다른 컬렉션에 컬렉션을 추가하여 중첩된 컬렉션을 만들 수 있습니다.

1. 컬렉션 콘솔에서 원하는 컬렉션이나 컬렉션 그룹을 선택하고 탭하거나 클릭합니다 **[!UICONTROL 대상 컬렉션]** 클릭합니다.
1. 에서 **[!UICONTROL 컬렉션에 추가]** 페이지에서 컬렉션을 추가할 컬렉션을 선택합니다.

   >[!NOTE]
   >
   >가장 최근에 업데이트된 컬렉션은 기본적으로 **[!UICONTROL 컬렉션에 추가]** 페이지.

1. 탭/클릭 **[!UICONTROL 추가]**. 컬렉션이 **[!UICONTROL 대상 선택]** 페이지. 메시지를 닫고 프로세스를 완료합니다.

>[!NOTE]
>
>스마트 컬렉션은 중첩할 수 없습니다. 즉, 스마트 컬렉션에는 다른 컬렉션이 포함될 수 없습니다.

## 저장된 검색 {#saved-searches}

In the Assets user interface, you can search or filter assets based on certain rules, search criteria, or custom search facets. If you save these as **[!UICONTROL Saved Searches]**, you can access them later from the **[!UICONTROL Saved Searches]** list in the Filter panel. Creating a saved search also creates a smart collection.

Saved searches are created when you create a smart collection. Smart collections are automatically added to the **[!UICONTROL Saved Searches]** list. The Saved Searches query for the collection is saved in the `dam:query` property in CRXDE at the relative location `/content/dam/collections/`. 저장 및 목록에 표시된 저장된 검색에서 저장할 수 있는 검색에는 제한이 없습니다.

>[!NOTE]
>
>정적 컬렉션을 공유하는 것과 동일한 방법으로 스마트 컬렉션을 공유할 수 있습니다.

저장된 검색을 편집하는 것은 스마트 컬렉션을 편집하는 것과 같습니다. 자세한 내용은 [스마트 컬렉션 편집](#edit-a-smart-collection).

저장된 검색을 삭제하려면 다음 단계를 수행합니다.

1. Assets 사용자 인터페이스의 도구 모음에서 검색 아이콘을 탭/클릭합니다.

1. Omnisearch 필드에 커서를 두고 `Enter` 키.
1. [전역 탐색] 아이콘을 클릭하거나 탭하여 [필터] 패널을 표시합니다.
1. From the **[!UICONTROL Saved Searches]** list, tap/click **[!UICONTROL Delete]** next to the smart collection you want to delete.
1. 대화 상자에서 을 탭/클릭합니다. **[!UICONTROL 삭제]** 저장된 검색을 삭제합니다.

## 컬렉션에서 워크플로우 실행 {#run-a-workflow-on-a-collection}

컬렉션 내의 자산에 대한 워크플로우를 실행할 수 있습니다. 컬렉션에 중첩된 컬렉션이 포함되어 있으면 중첩된 컬렉션 내의 자산에서도 워크플로우가 실행됩니다. 그러나 컬렉션과 중첩된 컬렉션에 중복 자산이 포함되어 있는 경우 워크플로우는 해당 자산에 대해 한 번만 실행됩니다.

1. 컬렉션 콘솔에서 워크플로우를 실행할 컬렉션을 선택합니다.
1. GlobalNav 아이콘을 탭/클릭하고 **[!UICONTROL 타임라인]** 참조하십시오.
1. 타임라인에서 맨 아래에 있는 캐럿 아이콘을 선택하거나 탭한 다음, 탭/클릭합니다 **[!UICONTROL 워크플로우 시작]**.
1. In the **[!UICONTROL Start Workflow]** section, select a workflow model from the list. For example, select the **[!UICONTROL DAM Update Asset]** model.
1. 워크플로우의 제목을 입력하고 탭/클릭합니다 **[!UICONTROL 시작]**.
1. 대화 상자에서 을 탭/클릭합니다. **[!UICONTROL 계속]**. 워크플로우는 컬렉션의 모든 자산에서 실행됩니다.

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
* [일괄 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [컬렉션에 대한 검토 작업 만들기](/help/assets/bulk-approval.md)

