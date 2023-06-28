---
title: 컬렉션 관리
description: 컬렉션은 Experience Manager Assets 보기 내의 에셋 세트입니다. 컬렉션을 사용하여 사용자 간에 에셋을 공유합니다.
exl-id: 33c889f5-c989-4772-9591-db62f50e5c80
source-git-commit: d198b3f0c7d8469a376ba7a3e95e57c84f835dbb
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 86%

---

# 컬렉션 관리 {#manage-collections}

>[!CONTEXTUALHELP]
>id="assets_collections"
>title="컬렉션 관리"
>abstract="컬렉션은 에셋, 폴더 또는 에셋 보기 내의 다른 컬렉션 세트입니다. 컬렉션을 사용하여 사용자 간에 에셋을 공유합니다. 폴더와 달리 컬렉션에는 서로 다른 위치의 에셋이 포함될 수 있습니다. 사용자와 여러 컬렉션을 공유할 수 있습니다. 각 컬렉션에는 에셋에 대한 참조가 포함되어 있습니다. 에셋의 참조 무결성은 컬렉션에 간에 유지됩니다."

컬렉션은 Adobe Experience Manager Assets 보기 내의 에셋, 폴더 또는 기타 컬렉션 세트입니다. 컬렉션을 사용하여 사용자 간에 에셋을 공유합니다.

폴더와 달리 컬렉션에는 서로 다른 위치의 에셋이 포함될 수 있습니다.

<!--
You can share collections with various users that are assigned different levels of privileges, including viewing, editing, and so on.
-->

사용자와 여러 컬렉션을 공유할 수 있습니다. 각 컬렉션에는 에셋에 대한 참조가 포함되어 있습니다. 에셋의 참조 무결성은 컬렉션에 간에 유지됩니다.

![컬렉션](assets/collections.png)

다음 작업을 수행하여 컬렉션을 관리하고 사용할 수 있습니다.

* [컬렉션 생성](#create-collection)

* [컬렉션에 에셋 추가](#add-assets-to-collection)

* [컬렉션에서 에셋 제거](#remove-assets-from-collection)

* [스마트 컬렉션 만들기](#create-smart-collection)

* [스마트 컬렉션 편집](#edit-smart-collection)

* [컬렉션 메타데이터 보기 및 편집](#view-edit-collection-metadata)

* [컬렉션 링크 공유](#share-collection-links)

* [컬렉션 다운로드](#download-collection)

* [컬렉션 삭제](#delete-collection)

## 컬렉션 생성 {#create-collection}

컬렉션을 생성하려면:

1. 왼쪽 레일에서 **[!UICONTROL 컬렉션]**&#x200B;을 클릭한 다음 **[!UICONTROL 컬렉션 생성]**&#x200B;을 클릭합니다.

1. 컬렉션에 대한 제목 및 설명(선택 사항)을 지정합니다.

1. 개인 컬렉션 또는 공개 컬렉션을 만들어야 하는 경우 선택합니다. 공개 컬렉션은 모든 사용자가 보고 편집할 수 있습니다. 그러나 개인 컬렉션은 작성자와 관리자 권한이 있는 사용자가 사용할 수 있습니다.

1. **[!UICONTROL 만들기]**&#x200B;를 클릭하여 컬렉션을 생성합니다.

![컬렉션 만들기](assets/create-collection.png)

<!--
   
   for viewing and editing only to users with the appropriate [permissions](#manage-collection-access).

-->

## 컬렉션에 에셋 추가 {#add-assets-to-collection}

컬렉션에 에셋을 추가하려면:

1. 왼쪽 레일에서 **[!UICONTROL 에셋]**&#x200B;을 클릭한 다음 컬렉션을 추가해야 하는 에셋을 선택합니다.

1. **[!UICONTROL 컬렉션에 추가]**&#x200B;를 클릭합니다.

1. [!UICONTROL 컬렉션] 대화 상자에서 선택한 에셋을 추가할 컬렉션을 선택합니다.

1. **[!UICONTROL 추가]**&#x200B;를 클릭하여 선택한 컬렉션에 에셋을 추가합니다.

## 컬렉션에서 에셋 제거 {#remove-assets-from-collection}

컬렉션에서 에셋을 제거하려면:

1. 컬렉션 목록을 보려면 왼쪽 레일에서 **[!UICONTROL 컬렉션]**&#x200B;을 클릭합니다.

1. 컬렉션을 클릭하고 컬렉션에서 제거해야 하는 항목을 선택합니다.

1. **[!UICONTROL 제거]**&#x200B;를 클릭합니다.

## 스마트 컬렉션 관리 {#manage-smart-collection}

검색 결과를 스마트 컬렉션으로 저장하여 컬렉션 콘텐츠를 동적으로 업데이트합니다. 스마트 컬렉션을 만드는 동안 정의된 검색 기준에 맞는 에셋 보기 저장소에 추가된 에셋이 있는 경우 스마트 컬렉션을 열면 해당 스마트 컬렉션의 콘텐츠가 자동으로 업데이트됩니다.

### 스마트 컬렉션 만들기 {#create-smart-collection}

스마트 컬렉션을 만들려면 다음 작업을 수행하십시오.

1. **[!UICONTROL 필터]**&#x200B;를 클릭한 다음 [검색 기준을 정의](search-assets-view.md#refine-search-results)합니다.

1. **[!UICONTROL 다른 이름으로 저장]**&#x200B;을 클릭한 다음 **[!UICONTROL 스마트 컬렉션]**&#x200B;을 선택합니다.

   ![스마트 컬렉션 만들기](assets/create-smart-collection.png)

1. [!UICONTROL 스마트 컬렉션 만들기] 대화 상자에서 해당 스마트 컬렉션의 제목과 설명을 지정합니다.

1. 모든 사용자가 컬렉션에 액세스할 수 있도록 하려면 **[!UICONTROL 공개 컬렉션]**&#x200B;을 선택합니다. 제한된 사용자 그룹만 컬렉션에 액세스할 수 있도록 하려면 **[!UICONTROL 개인 컬렉션]**&#x200B;을 선택합니다.

1. **[!UICONTROL 만들기]**&#x200B;를 클릭하여 스마트 컬렉션을 생성합니다.

### 스마트 컬렉션 편집 {#edit-smart-collection}

스마트 컬렉션을 편집하려면 다음 작업을 수행하십시오.

1. 왼쪽 레일에서 **[!UICONTROL 컬렉션]**&#x200B;을 클릭한 다음 편집해야 하는 컬렉션의 이름을 더블 클릭합니다.

1. **[!UICONTROL 스마트 컬렉션 편집]**&#x200B;을 클릭합니다.

1. [!UICONTROL 스마트 컬렉션 필터] 대화 상자에서 스마트 컬렉션에 대한 [검색 기준을 업데이트](search-assets-view.md#refine-search-results)합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

<!--

## Manage access to a Private collection {#manage-collection-access}

The permission management for collections function in the same manner as folders in [!DNL Assets view]. Administrators can manage the access levels for collections available in the repository. As an administrator, you can create user groups and assign permissions to those groups to manage access levels. You can also delegate the permission management privileges to user groups at the collection-level.

For more information, see [Manage permissions for folders and collections](manage-permissions.md).

-->

<!--

## Search a collection {#search-collections}

Click **[!UICONTROL Collections]** in the left rail and use the Search box to specify a text as the criteria to search for a collection. [!DNL Assets view] uses the specified text to search collection names, metadata including tags defined for a collection and returns appropriate results.

>[!NOTE]
>
>Assets view performs search in collections available at the root level. It does not perform search in assets and folders available in collections.

-->

## 컬렉션 메타데이터 보기 및 편집 {#view-edit-collection-metadata}

컬렉션 메타데이터는 제목 및 설명과 같은 컬렉션에 대한 데이터로 구성됩니다.

컬렉션 메타데이터를 보고 편집하려면:

1. 왼쪽 레일에서 **[!UICONTROL 컬렉션]**&#x200B;을 클릭하고 컬렉션을 선택한 다음 **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 기본]** 탭을 사용하여 컬렉션 메타데이터를 봅니다.
1. 필요에 따라 메타데이터 필드를 수정합니다. [!UICONTROL 제목] 및 [!UICONTROL 설명] 필드를 수정할 수 있습니다.

![컬렉션 메타데이터](assets/collection-metadata.png)

## 컬렉션 링크 공유 {#share-collection-links}

[!DNL Assets view]에서 링크를 생성하고 [!DNL Assets view] 애플리케이션에 대한 액세스 권한이 없는 외부 관련자와 컬렉션 내의 컬렉션 및 에셋을 공유할 수 있습니다. 해당 링크에 대한 만료일을 정의한 다음 이메일 또는 메시징 서비스와 같이 선호하는 커뮤니케이션 수단을 사용하여 다른 사용자와 공유할 수 있습니다. 링크 수신자는 자산을 미리 보고 다운로드할 수 있습니다.

![에셋에 대한 링크 공유](assets/share-link-collections.png)

외부 관련자와 컬렉션 링크를 공유하는 방법에 대한 자세한 내용은 [에셋에 대한 링크 공유](/help/assets/share-links-for-assets-view.md).

## 컬렉션 다운로드 {#download-collection}

컬렉션을 다운로드하는 방법:

1. 왼쪽 레일에서 **[!UICONTROL 컬렉션]**&#x200B;을 클릭합니다.

1. 다운로드해야 하는 컬렉션을 선택하고 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

1. [!UICONTROL 에셋 다운로드] 대화 상자에서 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

컬렉션은 로컬 컴퓨터에 .ZIP 파일로 다운로드됩니다.

## 컬렉션 삭제 {#delete-collection}

컬렉션을 삭제하려면:

1. 왼쪽 레일에서 **[!UICONTROL 컬렉션]**&#x200B;을 클릭합니다.

1. 삭제해야 하는 컬렉션을 선택합니다.

1. **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.

## 다음 단계 {#next-steps}

* 다음을 사용하여 제품 피드백 제공 [!UICONTROL 피드백] 자산 보기 사용자 인터페이스에서 사용할 수 있는 옵션

* 오른쪽 사이드바에서 사용 가능한 [!UICONTROL 이 페이지 편집], ![페이지 편집](assets/do-not-localize/edit-page.png), [!UICONTROL 문제 기록] 또는 ![GitHub 문제 생성](assets/do-not-localize/github-issue.png)을 사용하여 설명서 피드백 제공

* [고객 지원 센터](https://experienceleague.adobe.com/?support-solution=General#support) 문의
