---
title: Content Hub에서 자산 검색
description: ' [!DNL Content Hub]에서 자산을 검색하는 방법 알아보기'
role: User
source-git-commit: 5a968440c8841abe7af2c81c4af12258b7e4547f
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---


# [!DNL Content Hub]에서 Assets 검색 {#search-assets}

![자산 배너 이미지 공유](assets/search.png)

저장소에 에셋이 많으면 적절한 에셋을 검색하는 데 시간이 오래 걸립니다. [!DNL The Content Hub] 검색에서는 승인된 에셋을 찾아 컬렉션 다운로드, 공유 또는 만들기와 같은 추가 작업을 수행할 수 있는 기능을 제공합니다. 텍스트 기반 검색 수행, 필터 사용, 태그 또는 스마트 태그별 검색 수행, 특정 파일 형식 검색 등과 같은 다양한 기능을 사용하여 검색 결과 범위를 좁힐 수 있습니다.

## 사전 요구 사항 {#prerequisites}

[Content Hub 사용자](deploy-content-hub.md#onboard-content-hub-users)는 이 문서에 언급된 작업을 수행할 수 있습니다.

## 검색할 수 있는 항목  {#what-you-can-search}

[!DNL Content Hub] 검색은 다음을 기반으로 결과를 제공합니다.

* **일치하는 텍스트:** [!DNL Content Hub] 검색을 사용하면 이름 또는 설명을 사용하여 에셋을 검색할 수 있습니다. 키워드를 에셋의 속성에서 사용할 수 있는 텍스트와 비교하는 키워드 기반 검색을 수행할 수 있습니다.

* **일치하는 컨텍스트:** [!DNL Content Hub] 검색 결과 목록에 일치하는 컨텍스트를 기반으로 얻은 자산의 대략적인 결과가 포함되어 있습니다. 예를 들어 검색 창에 `cool`을(를) 입력하면 `winter`, `snow`, `cold surroundings`과(와) 관련된 자산이 검색 목록에 표시됩니다.

* **자산 정보(제목, 태그 또는 스마트 태그):** [!DNL Content Hub]은(는) 스마트 검색 알고리즘을 사용하여 검색 결과의 등급을 가능한 한 정확하고 적절하게 지정합니다. [메타데이터](#asset-properties.md)은(는) 에셋에 사용할 수 있는 모든 데이터의 컬렉션이지만 해당 에셋에 반드시 포함되지는 않을 수 있습니다. [자산을 분류하는 데 도움이 되며 디지털 정보의 양이 증가할 때 유용합니다](/help/assets/configure-content-hub-ui-options.md##configure-metadata-search-content-hub).

* **마지막으로 수정한 날짜:** 최근에 수정한 자산이 검색 결과 목록의 맨 위에 나타납니다. 요구 사항에 따라 날짜 범위를 필터링할 수도 있습니다.

* **사용량:** 일반적으로 사용되는 자산이 검색 목록의 맨 위에 나타납니다.

* **검색 기록:** 문자를 입력하지 않고 검색 상자 안을 클릭하여 검색 기록을 가져옵니다. 기록에서 특정 키워드를 제거할 수도 있습니다. 검색 기록은 웹 브라우저의 캐시 메모리에 저장됩니다. 즉, 다른 브라우저에서 [!DNL Content Hub] 검색에 액세스하거나 브라우저의 캐시 메모리를 지우면 더 이상 검색 기록을 볼 수 없습니다.

* **입력하는 동안 검색:** [!DNL Content Hub] 검색은 입력을 시작할 때 자동 완성 제안을 제공하여 검색 환경을 향상시킵니다.

## 기본 검색 {#basic-search}

[!DNL the Content Hub]에서 기본 검색을 수행하려면 검색 창으로 이동하여 검색해야 하는 키워드를 지정하십시오. 왼쪽 창에서 사용할 수 있는 필터로 이동하여 적용한 다음 검색 결과의 범위를 좁힙니다.

예를 들어 지난 해 내에 수정된 `architect` 키워드가 포함된 모든 **[!UICONTROL JPEG]** 이미지를 검색합니다. 이 시나리오를 실행하려면 다음 단계를 수행하십시오.

1. `architect`을(를) 검색 키워드로 지정하십시오.

1. 필터 패널 > **[!UICONTROL 서식]** > **[!UICONTROL JPEG]** 선택으로 이동합니다.

1. **[!UICONTROL 수정됨]**(으)로 이동하고 날짜 범위를 지정하십시오.

   ![기본 검색](assets/basic-search.png)

## 필터를 사용하여 검색 결과 좁히기 {#narrow-down-search-results}

필터 패널을 사용하여 메타데이터를 기반으로 에셋을 검색합니다. 다양한 검색 술어에 따라 검색 결과를 필터링할 수 있습니다. 적절한 모든 술어를 선택하여 검색 결과를 최소화하거나 좁힐 수 있습니다. 필터 내에서 여러 옵션을 선택하면 Content Hub에 필터 내에서 선택한 옵션과 일치하는 에셋이 표시됩니다. 그러나 필터 간에 여러 옵션을 선택하면 Content Hub은 검색 결과의 범위를 좁히기 위해 필터 간에 선택한 모든 옵션과 일치하는 에셋만 표시합니다.

기본 필터에는 파일 형식, 승인자, 승인 날짜, 만료 날짜 및 만료되지 않은 에셋, 만료 날짜가 포함됩니다. 관리자는 필터 목록에 표시되는 필터를 구성할 수도 있습니다. 자세한 내용은 [Content Hub 사용자 인터페이스 구성](configure-content-hub-ui-options.md#configure-filters-content-hub)을 참조하십시오.

<!--

<table>
    <tbody>
     <tr>
      <th><strong>Search Predicate</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Properties</strong></th>
     </tr>
     <tr>
      <td> Campaigns </td>
      <td> Allows you to search using planned activity performed to take any particular action. For example, advertisement campaign run on Ferrari to know the understand the interests of people using number of clicks people perform.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Channels </td>
      <td> Helps you to understand the path from where the asset is coming from. For example, web, social media, books, catalog, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Region </td>
      <td> Helps you to understand the location where the asset is created. For example, Japan, EMEA, Worldwide, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Keywords </td>
      <td> Keyword helps you search using terms or the words that you enter based on the topic. For example, images, low-resolution, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Timeframe </td>
      <td> Helps you search assets using timeline. For example, search by year 2024, Q3 2023, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td>File format</td>
      <td>Composition of an asset. The supported assets include image, document, video, printable media, and so on.</td>
      <td>
        <ul>
            <li>[!UICONTROL JPEG]</li> 
            <li>[!UICONTROL Quicktime]</li> 
            <li>[!UICONTROL PNG]</li> 
            <li>[!UICONTROL WebP]</li> 
            <li>[!UICONTROL MP4]</li> 
            <li>[!UICONTROL Plain]</li> 
            <li>[!UICONTROL PDF]</li>
            <li>[!UICONTROL SVG + XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Tags</td>
      <td>Tags help you categorize assets that can be browsed and searched more efficiently based on hierarchical taxonomies.</td>
      <td>
        <ul>
            <li>Field label</li>
            <li>Property name</li>
            <li>Path</li>
            <li>Description</li>
        </ul>
      </td>
     </tr>
     <!--<tr>
      <td>Subject</td>
      <td>Classification of assets based on their theme. For example, colorful, hiking, outdoors.</td>
      <td>NA</td>
     </tr>
          <tr>
      <td>Last modified</td>
      <td>Search assets based on their last modification. Specify the date range using the Start date and End date fields.</td>
      <td>
        <ul>
            <li>Range text (From)</li> 
            <li>Range text (To) </li>
        </ul>
      </td>
     </tr>    
     <!--<tr>
      <td>Asset ID</td>
      <td>Unique number that identifies the asset.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Colors </td>
      <td> Helps you search assets using colors that are automatically identified in an asset using Adobe's Sensei AI capabilities.</td>
      <td>NA</td>
     </tr>  
    </tbody>
   </table>

-->

## 검색으로 더 많은 작업 {#do-more-with-search}

[!DNL The Content Hub]은(는) 검색으로 제한되지 않으며, 검색 또는 미리 보기 인터페이스에서 바로 [다운로드](download-assets-content-hub.md), [공유](share-assets-content-hub.md) 및 [컬렉션에 에셋 추가](collections-content-hub.md)와 같은 추가 작업을 수행할 수 있습니다. 검색 결과 페이지에서 자산을 선택하여 이러한 옵션을 확인합니다.
