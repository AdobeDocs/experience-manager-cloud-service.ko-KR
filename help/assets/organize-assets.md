---
title: 디지털 자산 구성
description: Experience Manager을 사용하여 디지털 자산, 이미지, 파일, 폴더 등을 구성합니다.
contentOwner: AG
feature: Asset Management, Search
role: User
exl-id: 6b3ce076-2dd9-47f6-9b68-4fa52bfedd42
source-git-commit: 80ac947976bab2b0bfedb4ff9d5dd4634de6b4fc
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 5%

---

# 디지털 자산 구성 {#organize-digital-assets}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/organize-assets.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

Microsoft® Office 및 PDF 문서의 모든 디지털 자산, 메타데이터, 콘텐츠를 추출하여 검색할 수 있습니다. 검색을 사용하면 자산에 대해 복잡한 필터링을 수행할 수 있으며 적절한 권한을 완전히 준수할 수 있습니다. 메타데이터는 디지털 자산 관리의 메타데이터에서 자세히 다룹니다.

[!DNL Experience Manager Assets] 에서는 컨텐츠를 구성하는 여러 방법을 지원합니다. 폴더를 사용하여 계층 구조로 구성할 수도 있고, 태그 등의 순서가 없는 임시 방식으로 구성할 수도 있습니다. 사용자는 하위 자산, 표현물 및 메타데이터가 표시되는 DAM 자산 편집기에서 태그를 편집할 수 있습니다.

<!-- Commenting to pull down the existing content before applying changes wrt CQDOC-15930
## Create folders {#create-folders}

When organizing a collection of assets, for example, all *Nature* images, you can create folders to keep them together. You can use folders to categorize and organize your assets. [!DNL Assets] does not require you to organize assets in folders to work better.

>[!NOTE]
>
>Sharing an Assets folder (in Marketing Cloud) of the type `sling:OrderedFolder`, is not supported. If you want to share a folder, do not select Ordered when creating a folder.

1. Navigate to the place in your digital assets folder where you want to create a new folder.
1. In the menu, click **[!UICONTROL Create]**. Select **[!UICONTROL New Folder]**.
1. In the **[!UICONTROL Title]** field, provide a folder name. By default, DAM uses the title that you provided as the folder name. Once the folder is created, you can override the default and specify another folder name.
1. Click **[!UICONTROL Create]**. Your folder is displayed in the digital assets folder.

## Add CUG properties to folders {#add-cug-properties-to-folders}

You can limit who can access certain folders in Assets by making the folder part of a closed user group (CUG). To make a folder part of a CUG:

1. In Assets, right-click the folder you want to add closed user group properties for and select **Properties**.  
1. Click the **CUG** tab.
1. Select the **Enabled** check box to make the folder and its assets available only to a closed user group.  
1. Browse to the login page, if there is one, to add that information. Add admitted groups by clicking **Add item**. If necessary, add the realm. Click **OK** to save your changes.

## Use tags to organize assets {#use-tags-to-organize-assets}

You can use folders or tags or both to organize assets. Adding tags to assets makes them more easy to retrieve during a search. To add tags to an asset, follow these steps:

1. In the Digital Asset Manager, double-click the asset to open it.
1. In the **Tags** area, open the menu to reveal the available tags. Select tags as appropriate. To delete a tag, hover the pointer over the tag and click `X` to delete it.
1. Click **Save** to save any tags you added.

Date24/08/2021
-->

## 폴더에서 자산 구성 {#organize-using-folders}

자산을 구성하는 가장 기본적인 방법은 자산을 폴더에 저장하는 것입니다. 로컬 파일 시스템의 폴더에 파일을 구성하는 것과 유사합니다. 폴더를 만들고 관리하는 방법에 대한 자세한 내용은 [자산 관리](manage-digital-assets.md). 파일 및 폴더의 이름 지정 방법, 하위 폴더를 정렬하는 방법 및 이러한 폴더 내에서 파일을 처리하는 방식은 해당 자산의 처리 방식에 큰 영향을 줄 수 있습니다. 일관된 적절한 파일 및 폴더 이름 지정 전략을 사용하고 좋은 메타데이터 방법을 사용하면 디지털 자산 저장소를 최대한 활용할 수 있습니다.

* 일반적으로 디지털 자산 저장소는 항상 증가하고 있습니다. 따라서 컨텐츠 생성 주기 초기에 메타데이터 사용, 폴더 구조 및 파일 이름을 공식화하는 것이 중요합니다.
* 디지털 자산에 대해 일관된 저장소 구조를 적용하는 경우에만 폴더를 사용하십시오. 이러한 일관성은 프로세스를 지원하고 자산을 더 잘 관리하는 데 도움이 됩니다. 예를 들어, 다음 유형의 폴더에 배치된 자산은 자산을 구분하는 데 도움이 될 수 있습니다.

   * **개발 폴더**: 현재 작업 중인 디지털 자산을 포함합니다.
   * **클라이언트 폴더**: 클라이언트 또는 프로젝트 이름을 기반으로 하는 디지털 자산을 포함합니다.
   * **기본 폴더**: 원본 소스 디지털 자산을 포함합니다.
   * **표현물 폴더**: 원본 소스 디지털 자산의 표현물과 사본을 포함합니다.
   * **파일 크기 폴더**: 작은 파일, 중간 크기 또는 큰 파일 크기를 기반으로 하는 디지털 자산을 포함합니다.
   * **스테이징 폴더**: 웹 사이트에서 라이브로 게시할 준비가 된 디지털 자산을 포함합니다.
   * **MIME 유형 폴더**: 이미지, 문서 및 멀티미디어와 같은 MIME 유형에 맞는 디지털 자산을 포함합니다.
   * **폴더 아카이브**: 에서 사용되지 않는 디지털 자산을 포함합니다.
   * **날짜 기반 폴더**: 는 만든 날짜 또는 마지막으로 수정한 날짜를 기반으로 하는 디지털 자산을 포함합니다.

* 사용자 지정 또는 자동화가 계속 작동하도록 변경할 가능성이 없는 폴더 디렉토리를 만듭니다. 예를 들어 지정된 처리 프로필은 계속 작동합니다.
* 자산이 이미 게시된 경우 [!DNL Experience Manager] 자산을 다른 폴더로 이동하고 새 위치에서 다시 게시하려면 다음을 수행하십시오. 게시된 원래 자산 위치는 새로 다시 게시된 자산과 함께 계속 사용할 수 있습니다. 그러나 원래 게시된 자산은 입니다 *분실* to [!DNL Experience Manager] 게시 취소할 수 없습니다. 따라서 가장 좋은 방법은 먼저 자산을 게시 취소한 다음 다른 폴더로 이동하는 것입니다.

## 태그를 사용하여 자산 구성 {#use-tags-to-organize-assets}

자산에 태그를 추가하면 검색 중에 보다 쉽게 검색할 수 있고, 검색 결과를 사용하여 컬렉션을 만들고, 일부 자산에 대한 검색 등급을 높이고, 자산 검색을 위해 Adobe Sensei의 AI 알고리즘을 적용할 수 있습니다.

[!DNL Adobe Experience Manager Assets] 는 자체 학습 알고리즘을 사용하여 몇 번의 클릭만으로 적합한 자산을 찾을 수 있도록 해주는 매우 설명적인 태그를 만듭니다. 스마트 태깅은 Adobe Sensei, 인공 지능 및 머신 러닝 프레임워크를 사용하며, 이 프레임워크는 이미지에 표준 태그와 비즈니스 관련 태그를 모두 인식하고 적용하도록 교육할 수 있습니다. 스마트 태그는 컨텐츠, 개별 단어 또는 구문을 식별하고 자산에 설명 태그를 자동으로 적용할 수도 있습니다.

다음은 자산에 태그를 추가하는 단계입니다.

1. 에 로그인합니다. [!DNL Experience Manager Assets].
1. 클릭 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;를 클릭하고 자산을 선택한 다음 를 클릭합니다 **[!UICONTROL 속성]** 자산 속성을 엽니다.
1. 에서 **[!UICONTROL 기본]** 탭에서 폴더 아이콘을 클릭합니다. **[!UICONTROL 태그]** 메타데이터. 팝업 창이 열립니다.
1. 의 기존 태그에서 적절한 태그를 검색하거나 선택합니다 `cq-tags`. 자산에 여러 태그를 지정할 수 있습니다.

   태그 구조를 **[!UICONTROL 이름]** (알파벳 순서), **[!UICONTROL 생성됨]** 날짜 또는 **[!UICONTROL 수정됨]** 날짜. 다음 그림에서 태그 구조는 **[!UICONTROL 이름]**.

   ![추가 태그](assets/add-tags-to-asset.png)

1. 클릭 **저장** 자산 메타데이터 변경 사항을 업데이트하려면

자세한 내용은 다음 문서를 참조하십시오.

* [자산 메타데이터 편집](meta-edit.md)
* [자산의 스마트 태그](smart-tags.md)
* [검색 패널에 태그 설명 추가](/help/assets/search-facets.md/#adding-a-tags-predicate)

## 컬렉션으로 구성 {#organize-as-collections}

의 자산 컬렉션 사용 [!DNL Experience Manager Assets]를 사용하면 사용자 간에 자산을 생성, 편집 및 공유하는 기능을 간소화할 수 있습니다. 자산, 폴더 및 컬렉션의 정적 참조 목록이 포함된 컬렉션, 검색 기준에 따라 자산을 가져오는 컬렉션을 포함하여, 사용하는 방식에 따라 여러 유형의 컬렉션을 만듭니다. 다른 위치의 자산으로 컬렉션을 만들고 액세스, 보기 및 편집 권한이 다른 여러 사용자와 공유할 수 있습니다.

자세한 내용은 [컬렉션 관리](manage-collections.md)


## 프로필을 사용하여 자산 구성 {#organize-to-use-profiles}

처리 프로필에는 [!DNL Assets] 사전 정의된 폴더에 업로드되는 자산에 적용되는 처리 명령. 프로필은 폴더 또는 새로 업로드한 자산의 컨텐츠 처리를 자동화하는 데 사용됩니다. 프로필을 사용하여 자산을 더 잘 구성할 수 있습니다.

메타데이터 사용, 파일 이름 지정 및 폴더 구조를 표준화하면 디지털 자산 풀이 증가함에 따라 처리 프로필을 보다 정밀하고 일관성 있게 폴더에 적용할 수 있습니다.

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

>[!MORELIKETHIS]
>
>* [자산 마이크로서비스 및 처리 프로필 사용](asset-microservices-configure-and-use.md)
>* [메타데이터 프로필](metadata-profiles.md)
>* [비디오 프로필](/help/assets/dynamic-media/video-profiles.md)
>* [Dynamic Media 이미지 프로필](/help/assets/dynamic-media/image-profiles.md)


