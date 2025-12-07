---
title: ' [!DNL Assets view]에서 자산을 검색하고 검색하는 방법을 알아보세요.'
description: AEM Assets 보기에서 에셋을 검색하고 검색하는 방법을 알아봅니다. 강력한 검색 기능을 통해 적절한 에셋을 빠르게 찾고 콘텐츠 속도를 높일 수 있습니다.
role: User
exl-id: abfe6a91-1699-436f-8bf4-0d0bf2369f46
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: f83324be68bdab65e5c76ef336eb7e4a2e318dd1
workflow-type: tm+mt
source-wordcount: '1621'
ht-degree: 74%

---

# [!DNL Assets view]에서 자산 검색 {#search-assets}

>[!CONTEXTUALHELP]
>id="assets_search"
>title="자산 검색"
>abstract="검색창에서 키워드를 지정하거나 상태, 파일 유형, MIME 유형, 크기, 생성, 수정 및 만료 일자를 기준으로 필터링하여 자산을 검색하십시오. 표준 필터 외에도 사용자 정의 필터를 적용할 수 있습니다. 필터링된 결과를 “저장된 검색” 또는 “스마트 컬렉션”으로 저장할 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-collections.html?lang=ko#manage-smart-collection" text="스마트 컬렉션 만들기"

[!DNL Assets view]는 기본적으로 작동하는 효과적인 검색 기능을 제공합니다. 검색 기능은 전체 텍스트 검색이므로 포괄적입니다. 강력한 검색 기능을 통해 적절한 자산을 빠르게 찾고 콘텐츠 속도를 높일 수 있습니다. [!DNL Assets view]는 스마트 태그, 제목, 생성 날짜 및 저작권과 같은 메타데이터를 통해 전체 텍스트 검색 및 다중 검색 기능을 제공합니다.

에셋을 검색하려면 다음을 수행하십시오.

* 페이지 상단의 검색 상자를 클릭합니다. 기본적으로 현재 탐색 중인 폴더 내에서 검색됩니다. 다음 중 하나를 수행하십시오.

  ![검색 상자](assets/search-box.png)

   * 키워드를 사용하여 검색하고 필요한 경우 폴더를 변경합니다. Return 키를 누릅니다.

   * 직접 검색하여 최근에 본 자산으로 작업을 시작하십시오. 검색 상자를 클릭하고 제안에서 최근에 본 자산을 선택합니다.

## 검색 결과 필터링 {#refine-search-results}

여러 필터를 적용하여 검색 결과를 구체화하여 관련 에셋을 찾을 수 있습니다. 관리자가 구성한 이러한 필터는 파일, 폴더 및 컬렉션을 기반으로 합니다. [검색 필터 사용자 지정](custom-search-filters.md)을 참조하세요.

![검색 필터](assets/filters-panel.gif)

다음 매개변수를 기반으로 검색 결과를 필터링할 수 있습니다.

* 자산 상태: `Approved`, `Rejected` 또는 `No Status` 자산 상태를 사용하여 검색 결과를 필터링합니다.
* 파일 형식: 지원되는 파일 형식(`Images`, `Documents` 및 `Videos`)으로 검색 결과를 필터링합니다.
* MIME 유형: 지원되는 파일 형식 중 하나 이상을 필터링합니다. <!-- TBD:  [supported file formats](/help/using/supported-file-formats.md). -->
* 이미지 크기: 이미지를 필터링할 최소 및 최대 크기 중 하나 이상을 제공합니다. 크기는 픽셀 단위의 치수로 제공되며 이는 이미지의 파일 크기가 아닙니다.
* 생성 날짜: 메타데이터에 입력된 자산 생성 날짜입니다. 사용되는 표준 날짜 형식은 `yyyy-mm-dd`입니다.
* 수정 날짜: 자산이 마지막으로 수정된 날짜입니다. 사용되는 표준 날짜 형식은 `yyyy-mm-dd`입니다.
* 만료 날짜: `Expired` 자산 상태를 기반으로 검색 결과를 필터링합니다. 또한 자산의 만료 날짜 범위를 지정하여 검색 결과를 추가로 필터링할 수 있습니다.
* 사용자 지정 필터: [Assets 보기 사용자 인터페이스에 사용자 지정 필터를 추가](#custom-filters)합니다. 표준 필터 외에 사용자 정의 필터를 적용하여 검색 결과를 구체화합니다.

검색된 자산을 `Name`, `Relevance`, `Size`, `Modified` 및 `Created`의 오름차순 또는 내림차순으로 정렬할 수 있습니다. 기본적으로 검색된 자산은 `Relevance`를 기준으로 정렬됩니다.

<!--
  
## Manage custom filters {#custom-filters}

**Permissions required:**  `Can Edit`, `Owner`, or Administrator.

Assets view also enable you to add custom filters to the user interface. You can then apply those custom filters in addition to the [standard filters](#refine-search-results) to refine your search results.

Assets view provides the following custom filters:

<table>
    <tbody>
     <tr>
      <th><strong>Custom filter name</strong></th>
      <th><strong>Description</strong></th>
     </tr>
     <tr>
      <td>Title</td>
      <td>Filter assets using the asset title. The title that you specify in the case-sensitive search criteria must match the exact title of the asset to display in the results.</td>
     </tr>
     <tr>
      <td>Name</td>
      <td>Filter assets using the asset file name. The name that you specify in the case-sensitive search criteria must match the exact file name of the asset to display in the results.</td>
     </tr>
     <tr>
      <td>Asset Size</td>
      <td>Filter assets by defining a size range, in bytes, in the search criteria for an asset to display in the results.</td>
     </tr>
     <tr>
      <td>Predicted Tags</td>
      <td>Filter assets using the asset smart tag. The smart tag name that you specify in the case-sensitive search criteria must match the exact smart tag name of the asset to display in the results. You cannot specify multiple smart tags in search criteria.</td>
     </tr>    
    </tbody>
   </table>

   <!--
   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. For example, if you define <b>ma*</b> as the search criteria, Assets view displays assets with title, such as, market, marketing, man, manchester, and so on in the results.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. You can specify multiple smart tags separated by a comma in the search criteria.

   

### Add custom filters {#add-custom-filters}

To add custom filters:

1. Click **[!UICONTROL Filters]**. 

1. In the **[!UICONTROL Custom Filters]** section, click **[!UICONTROL Edit]** or **[!UICONTROL Add Filters]**.

   ![Add custom filters](assets/add-custom-filters.png)

1. On the **[!UICONTROL Custom filters management]** dialog box, select the filters that you need to add to the existing list of filters. Select **[!UICONTROL Custom Filters]** to select all filters.

1. Click **[!UICONTROL Confirm]** to add the filters to the user interface.

### Remove custom filters {#remove-custom-filters}

To remove custom filters:

1. Click **[!UICONTROL Filters]**. 

1. In the **[!UICONTROL Custom Filters]** section, click **[!UICONTROL Edit]**.

1. On the **[!UICONTROL Custom filters management]** dialog box, deselect the filters that you need to remove from the existing list of filters.

1. Click **[!UICONTROL Confirm]** to remove the filters from the user interface.

-->

## AI 검색 {#ai-search}

AI 검색은 정확한 키워드 일치 여부에 의존하지 않고 사용자 쿼리 뒤에 있는 의미와 의도를 이해하는 고급 검색 기능입니다. 인공지능(AI)과 머신러닝을 활용해 보다 정확하고 상황에 맞는 결과를 전달한다.

정확한 용어를 찾는 기존 키워드 기반 검색과 달리 AI 검색은 단어, 개념, 사용자 의도 간 관계를 해석한다. 이렇게 하면 쿼리가 다르게 표현되거나, 오타가 있거나, 다른 언어로 되어 있더라도 사용자가 찾고 있는 항목을 찾을 수 있습니다.

몇 가지 주요 이점은 다음과 같습니다.

* **다국어 지원**: 정확한 번역이 필요 없이 여러 언어를 검색합니다. 사용자는 쿼리 언어에 관계없이 관련 콘텐츠를 찾을 수 있습니다.

* **철자 오류를 처리합니다**: 오타 및 맞춤법 오류를 해석하여 입력이 불완전한 경우에도 정확한 결과를 보장합니다.

* **동의어 이해**: 관련 용어와 구에 대한 결과를 제공하므로 사용자가 올바른 키워드를 추측할 필요가 없습니다.

* **컨텍스트 인식 검색**: 정확한 단어뿐만 아니라 쿼리 뒤에 있는 의도를 인식합니다.

### AI 검색 예 {#examples-ai-search}

**메시지 예제**: *커피를 마시는 여성*

기존 키워드 기반 검색은 `Woman`, `drinking`, `Coffee`과(와) 같은 자산 메타데이터의 정확한 일치 항목을 찾고 메타데이터에 이러한 모든 용어를 포함하는 자산을 반환합니다.

그러나 AI 검색은 `Girl`의 경우 `Lady`, `Woman`, `Cappuccino`의 경우 `Latte` 및 `Coffee`과(와) 같은 유사한 단어와 일치합니다.

마찬가지로 이 프롬프트를 스페인어로 지정하거나 `Woman`을(를) `Wman`(으)로 잘못 입력해도 동일한 결과를 얻을 수 있습니다.

![Assets 보기에서 의미 체계 검색](assets/semantic-search.png)

### Assets 보기에서 AI 검색 활성화 또는 비활성화 {#enable-disable-ai-search}

다음 단계를 실행하여 AI 검색을 활성화하거나 비활성화합니다.

1. **[!UICONTROL 설정]** >> **[!UICONTROL 일반 설정]**(으)로 이동한 다음 **[!UICONTROL 검색]** 탭을 선택합니다.

1. **[!UICONTROL 검색]** 섹션에서 **[!UICONTROL AI 검색]**&#x200B;을 선택하여 AI 검색을 활성화하거나 **[!UICONTROL 키워드]**&#x200B;를 선택하여 비활성화합니다.

   ![Assets 보기에서 의미 체계 검색](/help/assets/assets/enable-disable-ai-search.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.


## [!DNL Adobe Firefly]를 사용하여 자산 검색 {#search-firefly}

[!DNL Experience Manager Assets] 내에서 [!DNL Adobe Firefly] 자산 검색 기능을 활용하면 어떤 자산 폴더에서도 사용할 수 없는 자산을 검색할 수 있습니다. 이를 통해 자산 폴더에 저장되지 않은 자산을 실시간으로 효율적으로 생성할 수 있습니다.

### 시작하기에 앞서 {#search-assets-firefly-prereqs}

활성 [!DNL Adobe Express] 구독이 있어야 합니다.

### 자산 생성 {#generate-assets-firefly}

[!DNL Adobe Firefly]를 사용하여 새 자산을 생성하려면:

1. [!DNL AEM Assets] 작업 영역으로 이동합니다.

1. 검색 창에 자산 이름을 입력합니다. 예를 들어 `Bugatti Type 57` 키워드를 사용하여 자산을 검색할 수 있습니다. 자산을 검색할 때 자산이 자산 폴더에 없기 때문에 결과를 찾을 수 없습니다. AI를 사용하여 자산을 생성하려면 **[!UICONTROL Firefly로 생성]**&#x200B;을 클릭합니다. [!DNL Adobe Firefly] 화면이 나타납니다.

   ![Firefly 통합](assets/firefly-integration.png)

   새 자산이 정상적으로 생성되었습니다. 또한 설명 상자에 새 텍스트 프롬프트를 입력하여 이미지 설명을 변경할 수도 있습니다. [특수 콘텐츠 및 관련 콘텐츠를 생성하기 위해 좋은 AI 프롬프트를 작성하는 방법에 대해 알아봅니다](https://helpx.adobe.com/kr/firefly/using/tips-and-tricks.html). 또는 스타일, 이미지 크기 변경 등 다양한 기능을 사용하여 [이미지를 편집할 수 있습니다](https://helpx.adobe.com/kr/firefly/using/text-to-image.html).

   ![Firefly 통합](assets/bugatti-type-57.png)

1. 저장하려는 이미지를 선택합니다. **[!UICONTROL 저장]**&#x200B;을 클릭하여 원하는 폴더에 자산을 저장한 다음 간편하게 액세스하도록 합니다.

1. 자산 저장 양식이 나타납니다. 다음 필드를 지정합니다.

   * **다른 이름으로 저장** 필드에 파일 이름을 입력합니다.
   * 대상 폴더를 선택합니다.
   * 프로젝트 또는 캠페인 이름, 키워드, 채널, 시간대 및 지역과 같은 세부 정보를 입력합니다.

   ![Firefly 통합](assets/save-generated-asset.png)

1. **새 자산으로 저장**&#x200B;을 클릭하여 자산을 저장합니다.

<!--

### Upload assets {#upload-assets-firefly}

To upload the generated asset to the assets repository:

1. Click **[!UICONTROL Upload]**.
1. Select the asset folder to which you need to upload the asset and click **[!UICONTROL Select Folder]**.
 ![Upload asset](assets/upload-asset-firefly.jpg)

 -->

## 저장된 검색 {#saved-search}

검색 기능은 [!DNL Assets view]에서 사용하기 매우 간단합니다. 검색 상자 내에서 키워드를 입력하고 Return 키를 눌러 결과를 볼 수 있을 뿐만 아니라, 한 번의 클릭으로 최근 검색한 키워드를 빠르게 다시 검색할 수 있습니다.

메타데이터 및 자산 유형에 대한 특정 기준에 따라 검색 결과를 필터링할 수도 있습니다. 자주 사용하는 필터의 경우 검색 경험을 개선하기 위해 [!DNL Assets view]을 사용하여 검색 매개변수를 저장할 수 있습니다. 그런 다음 저장된 검색을 선택하여 한 번의 클릭으로 필터를 검색하고 적용할 수 있습니다.

저장된 검색을 생성하려면 일부 자산을 검색하고 하나 이상의 필터를 적용한 다음 [!UICONTROL 필터] 패널에서 **[!UICONTROL 다른 이름으로 저장]** > **[!UICONTROL 저장된 검색]**&#x200B;을 클릭하십시오. **[!UICONTROL 다른 이름으로 저장]**&#x200B;을 클릭하고 **[!UICONTROL 스마트 컬렉션]**&#x200B;을 선택하여 결과를 스마트 컬렉션으로 저장할 수도 있습니다. 자세한 내용은 [스마트 컬렉션 만들기](manage-collections.md#create-a-smart-collection)를 참조하십시오.

![스마트 컬렉션 만들기](assets/create-smart-collection.png)

<!-- TBD: Search behavior. Full-text search. Ranking and rank boosts. Hidden assets.
Report poor UX that users can only save a filtered search and not a simple search.
.
Are other supported files fully indexed and support full-text search? Eg. audio/videos files can at best have metadata indexed.
Anything about ranking of assets displayed in search results?

What about temporarily hiding an asset (suspending search on it) from the search results? If an asset is undergoing review collaboration, should it be used by others? Should it be hidden in search?

When userA is searching and userB add an asset that matches search results, will the asset display in search as soon as userA refreshes the page? Assuming indexing is near real-time. May not be so for bulk uploads.
-->

## 검색 결과를 사용하여 작업 {#work-with-search-results}

검색 결과에 표시되는 자산을 선택하고 다음 작업을 수행할 수 있습니다.

* **유사 이미지 찾기**: 메타데이터 및 스마트 태그를 기반으로 Assets UI에서 유사한 이미지 자산을 찾습니다.

* **세부 정보**: 자산 속성을 보고 편집합니다.

* **다운로드**: 자산을 다운로드합니다.

* **컬렉션에 추가**: 선택한 자산을 컬렉션에 추가합니다.

* **바로 가기에 고정**: 나중에 필요할 때 더 빠르게 액세스할 수 있도록 [자산을 고정](my-workspace-assets-view.md)합니다. 고정된 모든 항목은 내 작업 영역의 **바로 가기** 섹션에 표시됩니다.

* **Adobe Express에서 열기**: Adobe Experience Manager Assets 화면에서 통합된 Adobe Express 이미지를 편집합니다.

* **편집**: Adobe Express를 사용하여 이미지를 편집합니다.

* **링크 공유**: 자산에 대한 [링크 공유](share-links-for-assets-view.md)를 통해 다른 사용자가 액세스하고 다운로드할 수 있도록 합니다.

* **삭제**: 자산을 삭제합니다.

* **복사**: 자산을 다른 폴더 위치에 복사합니다.

* **이동**: 자산을 다른 폴더 위치로 이동합니다.

* **이름 바꾸기**: 자산의 이름을 바꿉니다.

* **라이브러리에 복사**: 라이브러리에 자산을 추가합니다.

* **작업 할당**: 사용자에게 자산에 대한 작업을 할당합니다.

* **보기**: 자산에서 수행된 [작업을 모니터링](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/manage/search-assets)합니다.

## 검색 우선 홈 페이지 구성 {#configuring-search-first-homepage}

Assets 보기를 사용하면 조직의 기본 랜딩 페이지를 선택할 수 있습니다. 검색 우선을 홈 페이지로 사용하는 경우, 브랜딩에 맞게 배경 및 로고 이미지를 구성하여 페이지 브랜딩을 맞춤화할 수 있는 옵션도 있습니다.

검색 우선 홈 페이지를 구성하려면 아래 단계를 실행하십시오.

1. **[!UICONTROL 설정]** > **[!UICONTROL 일반 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 검색 우선]**&#x200B;을 선택합니다. 검색 우선 관련된 구성이 열립니다. 홈 페이지의 [정렬](#setting-alignment-search-bar) 또는 [배경 및 로고 이미지 설정](#setting-background-image-and-logo)을 설정할 수 있습니다.

### 검색 창 정렬 설정 {#setting-alignment-search-bar}

[!DNL Assets view]를 사용하면 검색 창 정렬을 변경할 수 있습니다. 검색 창을 중앙이나 상단에 표시할 수 있습니다. 적절한 정렬을 선택하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

![검색 우선 홈 페이지 정렬](assets/search-first-alignment.png)

### 홈 페이지 배경 및 로고 이미지 설정 {#setting-background-image-and-logo}

검색 우선 홈 페이지에 브랜드 로고와 배경 이미지를 추가할 수 있습니다. 다음 단계를 실행합니다.

1. **[!UICONTROL 홈 페이지]** 아래의 **[!UICONTROL 배경 및 로고 이미지]** 섹션으로 이동합니다.
1. 기존의 자산 저장소에서 이미지를 찾아보려면 **[!UICONTROL 바꾸기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 수정 사항을 검토하려면 변경 사항을 [미리 봅니다](#preview-configured-homepage).

### 구성된 홈 페이지 미리보기 {#preview-configured-homepage}

검색 우선 홈 페이지의 레이아웃과 서식을 미리보기로 확인할 수 있습니다. **[!UICONTROL 미리보기]**&#x200B;를 사용하면 레이아웃을 수정하거나 요구 사항에 따라 수정할 수 있습니다. 구성된 홈 페이지를 미리 보려면 아래 단계를 수행하십시오.

1. **[!UICONTROL 일반 설정]**&#x200B;을 클릭하고 **[!UICONTROL 검색 우선]**&#x200B;을 선택합니다.
1. **[!UICONTROL 검색 우선 홈 페이지 사용자 정의]**&#x200B;로 이동하고 **[!UICONTROL 미리보기]**&#x200B;를 클릭합니다. 홈 페이지를 어둡거나 밝은 테마로 미리 보려면 **[!UICONTROL 어두운 테마]** 버튼을 토글합니다.
1. 미리보기 화면을 닫으려면 **[!UICONTROL 닫기]**&#x200B;를 클릭합니다.

   ![검색 우선 홈 페이지 미리보기](/help/assets/assets/search-first-preview.gif)


<!--

## Contextual Search {#contextual-search}

You can also search assets available in the repository by defining text prompts. Experience Manager Assets automatically transforms those text prompts to search filters and displays the search results. You can view and modify automatic filters using the Filters Pane to further narrow down the search results.

### Access Contextual Search {#access-contextual-search}

To access Contextual Search in Experience Manager Assets:

1. Click **[!UICONTROL Search]** in the left pane.

   ![Contextual Search](assets/access-contextual-search.png)

1. Define the text prompt in the Search text box and click **[!UICONTROL Contextual Search]**.

   ![Contextual Search text prompt](/help/assets/assets/wknd-contextual-search.png)

   [!DNL Experience Manager Assets] displays the search results.

### Supported filters {#supported-filters}

Contextual Search supports the following filters out-of-the-box. Base your text prompts on these filters to view appropriate search results.

* Image height

* Image width

* File type: image, document, video, or folder.

* MIME type: JPG, PNG, TIFF, GIF, MP4, PDF, PPTX, DOCX or XLSX

* Created date

* Modified date

* Expiration date

* Asset status: Approved, Rejected, or all

* Expired assets

### Examples for the text prompts {#text-prompts-examples}

**Example 1**

**Text Prompt**: Images created this month.

[!DNL Experience Manager Assets] applies the following filters automatically and displays the search results:

![Contextual Search Example 1](assets/contextual-search-example1.png)

**Example 2**

**Text prompt**: Images at least 200px tall and 100px wide with beach and clear sky.

[!DNL Experience Manager Assets] applies the following filters automatically and displays the search results:

![Contextual Search Example 2](assets/contextual-search-example2.png)

**Example 3**

**Text prompt**: I need images of blue sky that are 1500 and 2500 pixel height and created in the past month that is not expired and approved.

[!DNL Experience Manager Assets] applies the following filters automatically and displays the search results:

![Contextual Search Example 3](assets/contextual-search-example3.png)

The following video illustrates the end-to-end process from accessing the Contextual Search User Interface to defining text prompts, and viewing the search results.

>[!VIDEO](https://video.tv.adobe.com/v/3428407)

### Disable Contextual Search {#disable-contextual-search}

Administrators also have the option to disable Contextual Search for users in your organization. To do so, execute the following steps:

1. Navigate to **[!UICONTROL Settings]** > **[!UICONTROL General Settings]**.

1. In the [!UICONTROL Contextual Search] section, turn off the **[!UICONTROL Enable Contextual Search for your organization]** toggle to disable the Contextual Search feature for all users in your organization.  

### Contextual Search feedback {#contextual-search-feedback}

If you need to provide feedback on the Contextual Search feature, click ![Contextual Search icon](assets/do-not-localize/Smock_Help_18_N.svg)  and click the Feedback icon. Select the feedback type, specify the subject and description, and click **[!UICONTROL Submit]**.

![Contextual Search feedback](assets/contextual-search-feedback.png)

-->

## 다음 단계 {#next-steps}

* [Assets 보기에서 에셋을 검색하는 비디오를 시청하십시오](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/using.html?lang=ko)

* Assets 보기 사용자 인터페이스에서 사용 가능한 [!UICONTROL 피드백] 옵션을 사용하여 제품 피드백 제공

* 오른쪽 사이드바에서 사용 가능한 [!UICONTROL 이 페이지 편집], ![페이지 편집](assets/do-not-localize/edit-page.png), [!UICONTROL 문제 기록] 또는 ![GitHub 문제 생성](assets/do-not-localize/github-issue.png)을 사용하여 설명서 피드백을 제공합니다.

* [고객 지원 센터](https://experienceleague.adobe.com/ko?support-solution=General#support) 문의



