---
title: ' [!DNL Assets view]에서 에셋 검색 및 탐색'
description: ' [!DNL Assets view]에서 에셋을 검색하고 탐색합니다.'
role: User
exl-id: be9597a3-056c-436c-a09e-15a03567c85a
source-git-commit: ed7ce8be17ad1445132b9aa38a0efa84ffa70fdf
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 94%

---

# [!DNL Assets view]에서 에셋 검색 {#search-assets}

>[!CONTEXTUALHELP]
>id="assets_search"
>title="에셋 검색"
>abstract="검색창에서 키워드를 지정하거나 상태, 파일 유형, MIME 유형, 크기, 생성, 수정 및 만료 일자를 기준으로 필터링하여 에셋을 검색하십시오. 표준 필터 외에도 사용자 정의 필터를 적용할 수 있습니다. 필터링된 결과를 “저장된 검색” 또는 “스마트 컬렉션”으로 저장할 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-collections.html?lang=ko#manage-smart-collection" text="스마트 컬렉션 만들기"

[!DNL Assets view]는 기본적으로 작동하는 효과적인 검색 기능을 제공합니다. 검색 기능은 전체 텍스트 검색이므로 포괄적입니다. 강력한 검색 기능을 통해 적절한 에셋을 빠르게 찾고 콘텐츠 속도를 높일 수 있습니다. [!DNL Assets view]는 스마트 태그, 제목, 생성 날짜 및 저작권과 같은 메타데이터를 통해 전체 텍스트 검색 및 다중 검색 기능을 제공합니다.

에셋을 검색하려면

* 페이지 상단의 검색 상자를 클릭합니다. 기본적으로 현재 탐색 중인 폴더 내에서 검색됩니다. 다음 중 하나를 수행하십시오.

  ![검색 상자](assets/search-box.png)

   * 키워드를 사용하여 검색하고 필요한 경우 폴더를 변경합니다. Return 키를 누릅니다.

   * 직접 검색하여 최근에 본 에셋으로 작업을 시작하십시오. 검색 상자를 클릭하고 제안에서 최근에 본 에셋을 선택합니다.

## 검색 결과 필터링 {#refine-search-results}

다음 매개변수를 기반으로 검색 결과를 필터링할 수 있습니다.

![검색 필터](assets/filters1.png)

*그림: 다양한 매개변수를 기반으로 검색된 에셋을 필터링합니다.*

* 에셋 상태: `Approved`, `Rejected` 또는 `No Status` 에셋 상태를 사용하여 검색 결과를 필터링합니다.

* 파일 형식: 지원되는 파일 형식(`Images`, `Documents` 및 `Videos`)으로 검색 결과를 필터링합니다.
* MIME 유형: 지원되는 파일 형식 중 하나 이상을 필터링합니다. <!-- TBD:  [supported file formats](/help/assets/supported-file-formats-assets-view.md). -->
* 이미지 크기: 이미지를 필터링할 최소 및 최대 크기 중 하나 이상을 제공합니다. 크기는 픽셀 단위의 치수로 제공되며 이는 이미지의 파일 크기가 아닙니다.
* 생성 날짜: 메타데이터에 입력된 에셋 생성 날짜입니다. 사용되는 표준 날짜 형식은 `yyyy-mm-dd`입니다.
* 수정 날짜: 에셋이 마지막으로 수정된 날짜입니다. 사용되는 표준 날짜 형식은 `yyyy-mm-dd`입니다.

* 만료 날짜: `Expired` 에셋 상태를 기반으로 검색 결과를 필터링합니다. 또한 에셋의 만료 날짜 범위를 지정하여 검색 결과를 추가로 필터링할 수 있습니다.

* 맞춤형 필터: [맞춤형 필터 추가](#custom-filters) (자산 보기 사용자 인터페이스 참조) 표준 필터 외에 맞춤형 필터를 적용하여 검색 결과를 구체화합니다.

검색된 에셋을 `Name`, `Relevancy`, `Size`, `Modified` 및 `Created`의 오름차순 또는 내림차순으로 정렬할 수 있습니다.

## 맞춤형 필터 관리 {#custom-filters}

**필요한 권한:**  `Can Edit`, `Owner` 또는 관리자.

에셋 보기를 사용하면 사용자 인터페이스에 사용자 지정 필터를 추가할 수도 있습니다. 그런 다음 [표준 필터](#refine-search-results) 외에 이러한 맞춤형 필터를 적용하여 검색 결과를 구체화할 수 있습니다.

에셋 보기는 다음과 같은 사용자 지정 필터를 제공합니다.

<table>
    <tbody>
     <tr>
      <th><strong>맞춤형 필터 이름</strong></th>
      <th><strong>설명</strong></th>
     </tr>
     <tr>
      <td>제목</td>
      <td>에셋 제목을 사용하여 에셋을 필터링합니다. 대/소문자 구분 검색 기준에 지정하는 제목은 결과에 표시할 에셋의 정확한 제목과 일치해야 합니다.</td>
     </tr>
     <tr>
      <td>이름</td>
      <td>에셋 필터 이름을 사용하여 에셋을 필터링합니다. 대/소문자 구분 검색 기준에 지정하는 이름은 결과에 표시할 에셋의 정확한 파일 이름과 일치해야 합니다.</td>
     </tr>
     <tr>
      <td>에셋 크기</td>
      <td>결과에 표시할 에셋의 검색 기준에서 크기 범위를 바이트 단위로 정의하여 에셋을 필터링합니다.</td>
     </tr>
     <tr>
      <td>예측된 태그</td>
      <td>에셋 스마트 태그를 사용하여 에셋을 필터링합니다. 대/소문자 구분 검색 기준에 지정하는 스마트 태그 이름은 결과에 표시할 에셋의 정확한 스마트 태그 이름과 일치해야 합니다. 검색 기준에 여러 스마트 태그를 지정할 수 없습니다.</td>
     </tr>    
    </tbody>
   </table>

<!--
   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. For example, if you define <b>ma*</b> as the search criteria, Assets view displays assets with title, such as, market, marketing, man, manchester, and so on in the results.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. You can specify multiple smart tags separated by a comma in the search criteria.

   -->

### 맞춤형 필터 추가 {#add-custom-filters}

맞춤형 필터를 추가하려면:

1. **[!UICONTROL 필터]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 맞춤형 필터]** 섹션에서 **[!UICONTROL 편집]** 또는 **[!UICONTROL 필터 추가]**&#x200B;를 클릭합니다.

   ![맞춤형 필터 추가](assets/add-custom-filters.png)

1. **[!UICONTROL 맞춤형 필터 관리]** 대화 상자의 기존 필터 목록에서 추가해야 하는 필터를 선택합니다. **[!UICONTROL 맞춤형 필터]**&#x200B;를 선택하여 모든 필터를 선택합니다.

1. **[!UICONTROL 확인]**&#x200B;을 클릭하여 사용자 인터페이스에 필터를 추가합니다.

### 맞춤형 필터 제거 {#remove-custom-filters}

맞춤형 필터를 제거하려면:

1. **[!UICONTROL 필터]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 맞춤형 필터]** 섹션에서 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 맞춤형 필터 관리]** 대화 상자의 기존 필터 목록에서 제거해야 하는 필터를 선택 취소합니다.

1. **[!UICONTROL 확인]**&#x200B;을 클릭하여 사용자 인터페이스에서 필터를 제거합니다.


## 저장된 검색 {#saved-search}

검색 기능은 [!DNL Assets view]에서 사용하기 매우 간단합니다. 검색 상자 내에서 키워드를 입력하고 Return 키를 눌러 결과를 볼 수 있을 뿐만 아니라 한 번의 클릭으로 최근 검색한 키워드를 빠르게 다시 검색할 수 있습니다.

메타데이터 및 에셋 유형에 대한 특정 기준에 따라 검색 결과를 필터링할 수도 있습니다. 자주 사용하는 필터의 경우 검색 경험을 개선하기 위해 [!DNL Assets view]을 사용하여 검색 매개변수를 저장할 수 있습니다. 그런 다음 저장된 검색을 선택하여 한 번의 클릭으로 필터를 검색하고 적용할 수 있습니다.

저장된 검색을 생성하려면 일부 에셋을 검색하고 하나 이상의 필터를 적용한 다음 [!UICONTROL 필터] 패널에서 **[!UICONTROL 다른 이름으로 저장]** > **[!UICONTROL 저장된 검색]**&#x200B;을 클릭하십시오. **[!UICONTROL 다른 이름으로 저장]**&#x200B;을 클릭하고 **[!UICONTROL 스마트 컬렉션]**&#x200B;을 선택하여 결과를 스마트 컬렉션으로 저장할 수도 있습니다. 자세한 내용은 [스마트 컬렉션 만들기](manage-collections-assets-view.md#create-a-smart-collection)를 참조하십시오.

![스마트 컬렉션 만들기](assets/create-smart-collection.png)

<!-- TBD: Search behavior. Full-text search. Ranking and rank boosts. Hidden assets.
Report poor UX that users can only save a filtered search and not a simple search.
.
Are other supported files fully indexed and support full-text search? Eg. audio/videos files can at best have metadata indexed.
Anything about ranking of assets displayed in search results?

What about temporarily hiding an asset (suspending search on it) from the search results? If an asset is undergoing review collaboration, should it be used by others? Should it be hidden in search?

When userA is searching and userB add an asset that matches search results, will the asset display in search as soon as userA refreshes the page? Assuming indexing is near real-time. May not be so for bulk uploads.
-->

## 다음 단계 {#next-steps}

* [자산 보기에서 자산을 검색하려면 비디오 보기](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/using.html)

* 다음을 사용하여 제품 피드백 제공 [!UICONTROL 피드백] 자산 보기 사용자 인터페이스에서 사용할 수 있는 옵션

* 오른쪽 사이드바에서 사용 가능한 [!UICONTROL 이 페이지 편집], ![페이지 편집](assets/do-not-localize/edit-page.png), [!UICONTROL 문제 기록] 또는 ![GitHub 문제 생성](assets/do-not-localize/github-issue.png)을 사용하여 설명서 피드백 제공

* [고객 지원 센터](https://experienceleague.adobe.com/?support-solution=General#support) 문의
