---
title: AEM에서 디지털 에셋 및 이미지 검색
description: 필터 패널을 사용하여 AEM에서 필요한 에셋을 찾는 방법 및 검색에 표시되는 에셋을 사용하는 방법을 살펴봅니다.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 7673ff492caac0b06e568ffecb43da2f5c6becbc
workflow-type: tm+mt
source-wordcount: '4525'
ht-degree: 0%

---


# AEM에서 자산 검색 {#search-assets-in-aem}

Experience Manager의 사용자에게 친숙한 에셋 검색 옵션을 사용하여 콘텐츠 제작 시간을 단축할 수 있습니다. 팀은 즉시 사용 가능한 기능과 맞춤형 방법을 사용하여 매끄럽고 지능적인 검색 경험을 제공함으로써 출시 시간을 단축할 수 있습니다. 자산 검색은 크리에이티브한 사람들이 더 많이 사용할 수 있도록 하거나, 비즈니스 사용자와 마케터가 자산을 안전하게 관리하거나, DAM 관리자가 관리하는 데 중요한 역할을 하는 디지털 자산 관리 시스템의 용도로만 사용할 수 있습니다. AEM Assets 사용자 인터페이스 또는 기타 앱 및 표면을 통해 수행할 수 있는 단순, 고급 및 사용자 정의 검색을 통해 이러한 사용 사례를 준수할 수 있습니다.

AEM은 다음 사용 사례를 지원하며 이 사용 사례의 사용, 개념, 구성, 제한 사항 및 문제 해결에 대해 설명합니다.

| 자산 검색 | 구성 및 관리 | 검색 결과를 사용한 작업 |
|--- |--- |--- |
| [기본 검색](#searchbasics) | [검색 색인](#searchindex) | [결과 정렬](#sort) |
| [검색 UI 이해](#searchui) |  | [자산의 속성 및 메타데이터 확인](#checkinfo) |
| [검색 제안](#searchsuggestions) | [필수 메타데이터](#mandatorymetadata) | [다운로드](#download) |
| [검색 결과 및 행동 이해](#searchbehavior) | [검색 패싯 수정](#searchfacets) | [일괄 메타데이터 업데이트](#metadataupdates) |
| [검색 순위 및 향상](#searchrank) | [텍스트 추출](#extracttextupload) | [스마트 컬렉션](#collections) |
| [고급 검색:검색 필터링 및 범위](#scope) | [사용자 정의 설명](#custompredicates) | [예기치 않은 결과](#unexpectedresults) 이해 및 문제 [해결](#troubleshoot) |
| [다른 솔루션 및 앱에서 검색](#beyondomnisearch): <br />     [Asset Link](#aal) <br />데스크탑 [앱](#desktopapp) <br />     [Adobe Stock 이미지](#adobestock) <br />     [다이내믹 미디어 자산](#dynamicmedia) |  |  |
| [자산 선택기/선택](#assetselector) |  |  |
| [제한](#tips) 사항 및 [팁](#limitations) |  |  |
| [일러스트레이션 예제](#samples) |  |  |

AEM 웹 인터페이스 상단에 있는 Omnisearch 필드를 사용하여 에셋을 검색합니다. AEM의 **[!UICONTROL 자산]****[!UICONTROL >]** 파일 ![으로 이동하고 상단 막대에서](assets/do-not-localize/search_icon.png) search_icon을 클릭하고 검색 키워드를 입력한 다음 Return 키를 누릅니다. 또는 키워드 단축키 `/` (슬래시)를 사용하여 Omnisearch 필드를 엽니다. `Location:Assets` 는 검색을 DAM 자산으로 제한하도록 미리 선택되어 있습니다. 고급 검색을 수행하여 검색 [범위를 늘리거나 제한할 수 있습니다](#scope).

[ **[!UICONTROL 필터]** ] 패널을 사용하여 에셋, 폴더, 태그 및 메타데이터를 검색할 수 있습니다. 파일 유형, 파일 크기, 마지막 수정 날짜, 자산 상태, 인사이트 데이터, Adobe Stock 라이선스와 같은 다양한 옵션(예측 가능)을 기반으로 검색 결과를 필터링할 수 있습니다. 필터 패널을 사용자 정의하고 [검색 패싯을 사용하여 검색 조건자를 추가/제거할 수 있습니다](/help/assets/search-facets.md).

AEM 검색 기능은 컬렉션 검색 및 컬렉션 내 자산 검색을 지원합니다. 컬렉션 [검색을 참조하십시오](/help/assets/manage-collections.md).

## 검색 인터페이스 이해 {#searchui}

검색 인터페이스와 사용 가능한 작업에 대해 숙지하십시오.

![자산 검색 결과 인터페이스의 일부 이해](assets/aem_search_results.png)*그림:* 자산 검색 결과 인터페이스의 일부 이해

**A.** 검색을 스마트 컬렉션으로 저장합니다. **B.** 검색 결과의 범위를 좁히는 필터(예측). **C.** 검색 결과에 파일, 폴더 또는 둘 다를 표시합니다. **D.** 필터를 클릭하여 왼쪽 레일을 열거나 닫습니다. **E.** 검색 위치는 DAM입니다. **사용자** 제공 검색 키워드 **G.** 확인란을 사용하여 모든 검색 결과 **H.** 총 검색 결과 중 표시되는 검색 결과 수를 선택합니다. **I. 카드 보기와 목록 보기 간 검색** 을 닫습니다. **** Close the search Nisj J. Switch between Card 뷰와 목록 보기 간

### 동적 검색 패싯 {#dynamicfacets}

검색 패싯에서 동적으로 업데이트되는 예상 검색 결과 수를 사용하여 검색 결과 페이지에서 원하는 자산을 더 빠르게 찾을 수 있습니다. 예상 자산 수는 검색 필터를 적용하기 전에도 업데이트됩니다. 필터에 대한 예상 카운트를 보면 검색 결과를 빠르고 효율적으로 탐색할 수 있습니다. 자세한 내용은 AEM에서 [자산 검색을 참조하십시오](/help/assets/search-assets.md).

![검색 패싯에서 검색 결과를 필터링하지 않고 대략적인 자산 수를 참조하십시오.](assets/asset_search_results_in_facets_filters.png)

검색 패싯에서 검색 결과를 필터링하지 않고 대략적인 자산 수를 참조하십시오.

## Search suggestions as you type {#searchsuggestions}

키워드를 입력하기 시작하면 AEM에서 가능한 검색 키워드 또는 구문을 제안합니다. 제안은 AEM의 자산을 기반으로 합니다. AEM은 검색에 도움이 되도록 모든 메타데이터 필드를 인덱싱합니다. 검색 제안을 제공하기 위해 시스템에서는 다음 몇 가지 메타데이터 필드의 값을 사용합니다. 검색 제안을 제공하려면 다음 필드를 적절한 키워드로 채우는 것이 좋습니다.

* 자산 태그. (매핑 대상 `jcr:content/metadata/cq:tags`)
* 자산 제목. (매핑 대상 `jcr:content/metadata/dc:title`)
* 자산 설명입니다. (매핑 대상 `jcr:content/metadata/dc:description`)
* JCR 저장소의 제목입니다. 이 값은 자산 제목에 매핑될 수 있습니다. (매핑 대상 `jcr:content/jcr:title`)
* JCR 저장소의 설명입니다. 이 값은 자산 설명에 매핑될 수 있습니다. (매핑 대상 `jcr:content/jcr:description`)

## 검색 결과 및 행동 이해 {#searchbehavior}

### 기본 검색어 및 결과 {#searchbasics}

OmniSearch 필드에서 키워드 검색을 실행할 수 있습니다. 키워드 검색은 대소문자를 구분하지 않으며 널리 사용되는 메타데이터 필드에서 전체 텍스트 검색입니다. 둘 이상의 키워드를 사용하는 경우 키워드 간의 기본 연산자 `AND` 가 됩니다. 결과는 가장 가까운 일치부터 관련성별로 정렬됩니다. 여러 키워드의 경우 메타데이터에 두 용어가 모두 포함된 자산이 관련성이 더 높습니다. 메타데이터 내에서 스마트 태그로 나타나는 키워드는 다른 메타데이터 필드에 나타나는 키워드보다 등급이 높습니다.

AEM은 특정 검색어를 더 높은 무게를 줄 수 있다. 또한 특정 검색어에 대한 몇 개의 타깃팅된 자산의 등급을 높일 수 있습니다. AEM 관리자는 아래 설명된 대로 이러한 구성을 수행할 수 있습니다.

관련 자산을 신속하게 찾기 위해 리치 인터페이스를 통해 필터링, 정렬 및 선택 메커니즘을 제공합니다. 여러 기준을 기반으로 결과를 필터링하고 다양한 필터에 대해 검색된 자산의 수를 확인할 수 있습니다. 또는 Omnisearch 필드에서 질의를 변경하여 검색을 다시 실행할 수 있습니다. 검색어 또는 필터를 변경하면 다른 필터는 검색 컨텍스트를 유지하기 위해 계속 적용됩니다.

경우에 따라 검색 결과에 예기치 않은 에셋이 표시될 수 있습니다. 자세한 내용은 [예상치 못한 결과를 참조하십시오](#unexpectedresults).

AEM에서 다양한 파일 포맷을 검색할 수 있으며 비즈니스 요구 사항에 맞게 검색 필터를 사용자 정의할 수 있습니다. DAM 저장소에 사용할 수 있는 검색 옵션과 로그인 제한 사항에 대해 알아보려면 관리자에게 문의하십시오.

<!-- 
### Results with and without Enhanced Smart Tags {#withsmarttags}

By default, AEM search combines the search terms with an AND clause. For example, consider searching for keywords woman running. Only the assets with both woman and running keywords in the metadata appear in the search results by default. The same behavior is retained when special characters (periods, underscores, or dashes) are used with the keywords. The following search queries return the same results:

* `woman running`
* `woman.running`
* `woman-running`

However, the query `woman -running` returns assets without `running` in their metadata.
Using smart tags adds an extra `OR` clause to find any of the search terms as the applied smart tags. An asset tagged with either `woman` or `running` using Smart Tags also appear in such a search query. So the search results are a combination of,

* Assets with `woman` and `running` keywords in the metadata (default behavior).

* Assets smart tagged with either of the keywords (Smart Tags behavior).
-->

### 검색 순위 및 향상 {#searchrank}

메타데이터 필드의 모든 검색어와 일치하는 검색 결과가 먼저 표시되고, 그 다음에 스마트 태그의 검색어와 일치하는 검색 결과가 표시됩니다. 위 예에서 검색 결과의 대략적인 표시 순서는 다음과 같습니다.

1. 다양한 메타데이터 필드 `woman running` 에서 일치하는 항목을 찾습니다.
1. 스마트 태그 `woman running` 에 일치합니다.
1. 스마트 태그 `woman` 의 `running` 일치 또는

특정 자산에 대한 키워드의 연관성을 개선하여 키워드를 기반으로 검색을 강화할 수 있습니다. 즉, 특정 키워드를 홍보하는 이미지가 이러한 키워드를 기반으로 검색할 때 검색 결과의 맨 위에 표시됩니다.

1. 자산 사용자 인터페이스에서 자산의 속성 페이지를 엽니다. 고급 **[!UICONTROL 을]** 클릭하고 검색 키워드 **[!UICONTROL 를]** 위한 **[!UICONTROL 격려]**&#x200B;아래에서추가를 클릭/탭합니다.
1. 홍보 **[!UICONTROL 검색]** 상자에서 이미지 검색을 강화할 키워드를 지정한 다음 **[!UICONTROL 추가를 클릭/탭합니다]**. 동일한 방법으로 여러 키워드를 지정할 수 있습니다.
1. **[!UICONTROL 저장 후 닫기]**&#x200B;를 클릭합니다. 이 키워드에 대해 홍보한 자산이 상위 검색 결과 사이에 나타납니다.

타깃팅된 키워드에 대한 검색 결과의 일부 자산의 등급을 강화하여 이 분류를 장점으로 사용할 수 있습니다. 아래 예제 비디오를 참조하십시오. 자세한 내용은 AEM에서 [검색을 참조하십시오](https://helpx.adobe.com/experience-manager/kt/help/assets/search-feature-video-use.html).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*비디오:검색 결과의 등급 지정 방법과 등급에 영향을 주는 방법을 이해합니다.*

## Advanced search {#scope}

AEM에서는 원하는 에셋을 보다 빠르게 찾을 수 있도록 검색된 에셋에 적용되는 필터와 같은 다양한 방법을 제공합니다. 다음은 흔히 사용되는 몇 가지 방법을 설명한 것입니다. 일부 [예제는](#samples) 아래에 공유되어 있습니다.

**파일 또는 폴더**&#x200B;검색:검색 결과에서 파일, 폴더 또는 둘 다를 참조하십시오. 필터 **[!UICONTROL 패널에서]** 적절한 옵션을 선택할 수 있습니다. 검색 [인터페이스를 참조하십시오](#searchui).

**폴더 내의 자산 검색**:검색을 특정 폴더로 제한할 수 있습니다. [ **[!UICONTROL 필터]** ] 패널에서 폴더 경로를 추가합니다. 한 번에 하나의 폴더만 선택할 수 있습니다.

![필터 패널에서 폴더 경로를 추가하여 검색 결과를 폴더로 제한](assets/search_folder_select.gif)

필터 패널에서 폴더 경로를 추가하여 검색 결과를 폴더로 제한

<!--
### Find similar images {#visualsearch}

To find images that are visually similar to a user-selected image, click **[!UICONTROL Find Similar]** option from the card view of an image or from the toolbar. AEM displays the smart tagged images from the DAM repository that are similar to a user-selected image. See [how to configure similarity search](#configvisualsearch).

![Find similar images using the option in the card view](assets/search_find_similar.png)
*Figure: Find similar images using the option in the card view*
-->

### Adobe Stock 이미지 {#adobestock}

AEM 유저 인터페이스 내에서 사용자는 [Adobe Stock 자산을](/help/assets/aem-assets-adobe-stock.md) 검색하고 필요한 자산에 라이선스를 부여할 수 있습니다. Omnisearch 바 `Location: Adobe Stock` 에 추가합니다. 또한 필터 패널을 사용하여 라이선스가 부여되거나 라이선스가 부여되지 않은 모든 에셋을 찾거나 Adobe Stock 파일 번호를 사용하여 특정 에셋을 검색할 수도 있습니다.

### 다이내믹 미디어 자산 {#dmassets}

[필터] 패널에서 [ **[!UICONTROL 다이내믹 미디어] > [세트]** ]를 선택하여 Dynamic Media 이미지를 **[!UICONTROL 필터링할 수]** 있습니다. 이미지 세트, 회전 메뉴, 혼합 미디어 집합 및 스핀 세트와 같은 에셋을 필터링하고 표시합니다.

### 메타데이터 필드에서 특정 값을 사용하여 검색 {#gqlsearch}

제목, 설명 및 작성자와 같은 특정 메타데이터 필드의 정확한 값을 기반으로 자산을 사용할 수 있습니다. GQL 전체 텍스트 검색 기능은 메타데이터 값이 검색 쿼리와 정확히 일치하는 자산만 가져옵니다. 속성 이름(예: 작성자, 제목 등)과 값은 대/소문자를 구분합니다.

| 메타데이터 필드 | 패싯 값 및 사용 |
|---|---|
| 제목 | 제목:John |
| 작성자 | creator:John |
| 위치 | 위치:북미 |
| 설명 | 설명:&quot;샘플 이미지&quot; |
| 작성자 도구 | creatortool:&quot;Adobe Photoshop CC 2015&quot; |
| 저작권 소유자 | copyrightowner:&quot;Adobe Systems&quot; |
| 내용 작성자 | contributor:John |
| 사용 약관 | usagterms:&quot;CopyRights Reserved&quot; |
| 작성일 | created:YYYY-MM-DDTHH |
| 만료 날짜 | explose:YYYY-MM-DDTHH |
| 정시 | ontime:YYYY-MM-DDTHH |
| 해제 시간 | offtime:YYYY-MM-DDTHH |
| 시간 범위(만료일 시간, 시간 해제) | facet 필드:하한...맨 |
| 경로 | /content/dam/&lt;폴더 이름> |
| PDF 제목 | pdftitle:&quot;Adobe 문서&quot; |
| 제목 | 제목:&quot;교육&quot; |
| 태그 | 태그:&quot;위치 및 여행&quot; |
| 유형 | type:&quot;image\png&quot; |
| 이미지 너비 | width:lowbound.맨 |
| 이미지 높이 | height:lower bound.맨 |
| 개인 | 사람:John |

속성 경로, 제한, 크기 및 orderby는 다른 속성과 함께 ORed를 사용할 수 없습니다.

사용자 생성 속성의 키워드는 속성 편집기의 필드 레이블이며 공백이 제거됩니다.

다음은 복잡한 쿼리에 대한 검색 형식의 몇 가지 예입니다.

* 여러 패싯 필드가 있는 모든 자산을 표시하려면(예:title=John Doe 및 creator 도구 = Adobe Photoshop): `title:"John Doe" creatortool : Adobe*`
* 패싯 값이 단일 단어가 아닌 문장(예:title=Scott Reynolds): `title:"Scott Reynolds"`
* 단일 속성의 여러 값이 있는 자산을 표시하려면(예:title=Scott Reynolds or John Doe): `title:"Scott Reynolds" OR "John Doe"`
* 속성 값이 있는 자산을 특정 문자열로 표시하려면(예:제목이 스캇 레이놀즈): `title:Scott*`
* 특정 문자열로 끝나는 속성 값이 있는 자산을 표시하려면(예:제목이 스캇 레이놀즈): `title:*Reynolds`
* 특정 문자열이 포함된 속성 값이 있는 자산을 표시하려면(예:title = Basel 회의실): `title:*Meeting*`
* 특정 문자열이 들어 있고 특정 속성 값이 있는 자산을 표시하려면(예:title=John Doe가 있는 자산에서 문자열 Adobe 검색): `*Adobe* title:"John Doe"`

## 다른 AEM 제품 또는 인터페이스에서 에셋 검색 {#beyondomnisearch}

Adobe Experience Manager(AEM)은 DAM 저장소를 다른 다양한 AEM 솔루션에 연결하여 디지털 에셋에 보다 신속하게 액세스할 수 있도록 하고 크리에이티브 워크플로우를 간소화합니다. 모든 자산 검색은 검색 또는 검색으로 시작합니다. 검색 동작은 다양한 표면과 솔루션에서 동일하게 유지됩니다. 일부 검색 방법은 대상 대상, 사용 사례 및 사용자 인터페이스가 AEM 솔루션에 따라 달라집니다. 아래 링크에서 개별 솔루션에 대한 특정 방법을 문서화합니다. 일반적으로 적용할 수 있는 팁과 행동은 이 문서에 설명되어 있습니다.

### Adobe 에셋 링크 패널에서 에셋 검색 {#aal}

이제 크리에이티브 전문가는 Adobe 에셋 링크를 사용하여 지원되는 Adobe Creative Cloud 앱을 종료하지 않고도 AEM Assets에 저장되어 있는 컨텐츠에 액세스할 수 있습니다. 크리에이티브 전문가는 Creative Cloud 앱에서 인앱 패널을 사용하여 에셋을 원활하게 검색하고 체크 아웃하고 확인할 수 있습니다.Photoshop, Illustrator 및 InDesign 에셋 링크를 사용하면 시각적으로 유사한 결과를 검색할 수도 있습니다. 시각적인 검색 디스플레이 결과는 Adobe Sensei의 머신 러닝 알고리즘을 기반으로 하며 미적으로 유사한 이미지를 찾는 데 도움이 됩니다. Adobe [자산 링크를 사용하여 자산](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) 검색 및 찾아보기를 참조하십시오.

### AEM 데스크탑 앱에서 에셋 검색 {#desktopapp}

크리에이티브 전문가는 데스크탑 앱을 사용하여 로컬 데스크탑(Win 또는 Mac)에서 검색 및 이용할 수 있는 AEM Assets을 손쉽게 만들 수 있습니다. 크리에이티브는 Mac Finder 또는 Windows 탐색기에서 원하는 에셋을 쉽게 표시하고, 데스크탑 애플리케이션에서 열고, 로컬로 변경할 수 있습니다. 변경 내용은 저장소에서 만든 새 버전으로 다시 AEM에 저장됩니다. 이 애플리케이션은 하나 이상의 키워드 * 및 ? 와일드카드 및 AND 연산자로 지정합니다. 데스크탑 앱에서 [에셋](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) 검색 및 미리 보기를 참조하십시오.

### Search assets in Brand Portal {#brandportal}

비즈니스 라인 사용자와 마케터는 브랜드 포털을 사용하여 승인된 디지털 자산을 다양한 내부 팀, 파트너 및 리셀러와 효율적이고 안전하게 공유합니다. See [search assets on Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching.html).

### Adobe Stock 이미지 검색 {#adobestock-1}

AEM 사용자 인터페이스 내에서 사용자는 Adobe Stock 자산을 검색하고 필요한 에셋에 라이선스를 부여할 수 있습니다. Omnisearch 필드 `Location: Adobe Stock` 에 추가합니다. 또한 필터 **** 패널을 사용하여 라이선스가 부여되거나 라이선스가 부여되지 않은 모든 자산을 찾거나 Adobe Stock 파일 번호를 사용하여 특정 자산을 검색할 수도 있습니다. AEM에서 Adobe Stock 이미지 [관리를 참조하십시오](/help/assets/aem-assets-adobe-stock.md#usemanage).

### 다이내믹 미디어 자산 검색 {#dynamicmedia}

[필터] 패널에서 [ **[!UICONTROL 다이내믹 미디어]** ] > [ **[!UICONTROL 세트]** ]를 선택하여 **[!UICONTROL Dynamic Media 이미지를]** 필터링할 수있습니다. 이미지 세트, 회전 메뉴, 혼합 미디어 집합 및 스핀 세트와 같은 에셋을 필터링하고 표시합니다. 웹 페이지를 작성하는 동안 작성자는 컨텐츠 파인더 내에서 세트를 검색할 수 있습니다. 설정 필터는 팝업 메뉴에서 사용할 수 있습니다.

### 웹 페이지를 작성할 때 Content Finder에서 자산 검색 {#contentfinder}

작성자는 컨텐츠 파인더를 사용하여 DAM 리포지토리에서 관련 자산을 검색하고, 만든 웹 페이지에서 자산을 사용할 수 있습니다.

<!-- Authors can also use the Connected Assets functionality to search for assets that are available on a remote AEM deployment. Authors can then use these assets in web pages on a local AEM deployment. See [use remote assets](use-assets-across-connected-assets-instances.md#use-remote-assets).
-->

### 컬렉션 검색 {#collections}

AEM 검색 기능은 컬렉션 검색 및 컬렉션 내 자산 검색을 지원합니다. 컬렉션 [검색을 참조하십시오](/help/assets/manage-collections.md).

## Asset selector {#assetselector}

자산 선택기를 사용하면 DAM 자산을 특별한 방식으로 검색, 필터링 및 검색할 수 있습니다. 자산 선택기는 에서 사용할 수 있습니다 `https://[aem_server]:[port]/aem/assetpicker.html`. 자산 선택기를 사용하여 선택한 자산의 메타데이터를 가져올 수 있습니다. 자산 유형(이미지, 비디오, 텍스트) 및 선택 모드(단일 또는 다중 선택)와 같은 지원되는 요청 매개 변수를 사용하여 시작할 수 있습니다. 이러한 매개 변수는 특정 검색 인스턴스에 대한 자산 선택기의 컨텍스트를 설정하며 선택 영역 전체에서 그대로 유지됩니다.

자산 선택기는 HTML5 `Window.postMessage` 메시지를 사용하여 선택한 자산에 대한 데이터를 수신자에게 보냅니다. 자산 선택기는 Granite의 foundation picker 어휘를 기반으로 합니다. 기본적으로 자산 선택기는 찾아보기 모드에서 작동합니다.

다음 요청 매개 변수를 URL에 전달하여 특정 컨텍스트에서 자산 선택기를 시작할 수 있습니다.

| 이름 | 값 | 예 | 목적 |
|---|---|---|---|
| 리소스 접미어(B) | URL에 있는 리소스 접미어의 폴더 경로:[https://localhost:4502/aem/assetpicker.html/&lt;folder_path>](https://localhost:4502/aem/assetpicker.html) | 폴더 /content/dam/we-retail/en/activities와 같이 선택한 특정 폴더를 사용하여 자산 선택기를 실행하려면, URL이 형식이어야 합니다. [https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images](https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images) | 자산 선택기가 시작될 때 특정 폴더를 선택해야 하는 경우 리소스 접미어로 전달합니다. |
| mode | 단일, 다중 | [https://localhost:4502/aem/assetpicker.html?mode=multiplehttps://localhost:4502/aem/assetpicker.html?mode=single](https://localhost:4502/aem/assetpicker.html?mode=multiplehttps://localhost:4502/aem/assetpicker.html?mode=single) | 여러 모드에서 자산 선택기를 사용하여 여러 자산을 동시에 선택할 수 있습니다. |
| mimetype | 자산의 MIMETYPE(`/jcr:content/metadata/dc:format`와일드카드가 지원됨) | <ul><li>[https://localhost:4502/aem/assetpicker.html?mimetype=image/png](https://localhost:4502/aem/assetpicker.html?mimetype=image/png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&amp;mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&amp;mimetype=*png)</li></ul> | MIME 형식을 기반으로 자산을 필터링하는 데 사용합니다. |
| 문제가 발생합니다 | true, false | [https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | 이러한 매개 변수를 사용하여 자산 선택기를 [화강암 대화 상자]로 엽니다. 이 옵션은 [화강암 경로 필드]를 통해 자산 선택기를 실행하고 pickerSrc URL로 구성하는 경우에만 적용됩니다. |
| 자산 유형(S) | 이미지, 문서, 멀티미디어, 아카이브 | <ul><li>[https://localhost:4502/aem/assetpicker.html?assettype=images](https://localhost:4502/aem/assetpicker.html?assettype=images)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=documents](https://localhost:4502/aem/assetpicker.html?assettype=documents)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=multimedia](https://localhost:4502/aem/assetpicker.html?assettype=multimedia)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=archives](https://localhost:4502/aem/assetpicker.html?assettype=archives)</li></ul> | 전달된 값을 기준으로 자산 유형을 필터링하려면 이 옵션을 사용합니다. |
| 루트 | &lt;folder_path> | [https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities](https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities) | 자산 선택기의 루트 폴더를 지정하려면 이 옵션을 사용합니다. 이 경우 자산 선택기를 사용하면 루트 폴더 아래에서 하위 자산(직접/간접)만 선택할 수 있습니다. |

자산 선택기 인터페이스에 액세스하려면 로 이동합니다 `https://[AEM server]:[port]/aem/assetpicker`. 원하는 폴더로 이동하고 하나 이상의 자산을 선택합니다. 또는 Omnisearch 상자에서 원하는 자산을 검색하고 필요에 따라 필터를 적용한 다음 선택합니다.

![자산 선택기에서 자산 찾아보기 및 선택](assets/assetpicker.png)

*그림:자산 선택기에서 자산을 검색하고 선택합니다.*

## 제한 사항 {#limitations}

AEM Assets의 검색 기능에는 다음과 같은 제한 사항이 있습니다.

* 검색 쿼리에 선행 공백을 입력하지 마십시오. 그렇지 않으면 검색이 작동하지 않습니다.
* 검색된 결과에서 자산의 속성을 선택한 다음 검색을 취소한 후에도 AEM은 검색어를 계속 표시할 수 있습니다(CQ-4273540).
* 폴더 또는 파일 및 폴더를 검색할 때 어떤 매개 변수에서든 검색 결과를 정렬할 수 없습니다.
* Omnisearch 막대에서 아무 것도 입력하지 않고 Return 키를 누르면 AEM은 폴더가 아닌 파일 목록만 반환합니다. 키워드를 사용하지 않고 폴더를 특히 검색하는 경우 AEM에서는 결과를 반환하지 않습니다.

시각적 검색 또는 유사성 검색에는 다음과 같은 제한이 있습니다.

* 시각적 검색은 더 큰 저장소에서 가장 잘 작동합니다. 좋은 결과를 얻기 위해 필요한 최소 이미지 수는 없지만, 몇 개의 이미지가 있는 일치 항목의 품질이 큰 저장소의 일치 항목 만큼 좋지 않을 수 있습니다.
* 모델을 변경하거나 AEM에서 유사한 이미지를 찾을 수 없습니다. 예를 들어 일부 자산에 스마트 태그를 추가하거나 제거해도 모델이 변경되지 않습니다. 에셋은 시각적으로 유사한 검색 결과에서 제외됩니다.

## 검색 팁 {#tips}

* 자산의 검토 상태를 모니터링할 때 적절한 옵션을 사용하여 승인되는 자산이나 승인 대기 중인 자산을 찾습니다.
* 인사이트 술어를 사용하여 다양한 크리에이티브 앱에서 얻은 사용 통계를 기반으로 지원되는 자산을 검색합니다. 사용 데이터는 자산이 카테고리가 표시되는 사용량 점수, 노출 횟수, 클릭 수 및 미디어 채널로 그룹화됩니다.
* 선택 영역에서 사용할 검색 결과 또는 필터링된 검색 결과를 모두 선택하려면 확인란을 선택합니다. 현재 사용자 보기에 표시되는 자산 수에 관계없이 검색된 모든 자산을 선택합니다. 예를 들어 선택한 모든 자산을 다운로드하거나, 선택한 모든 자산에 대해 메타데이터 속성을 일괄 업데이트하거나, 선택한 자산을 컬렉션에 추가할 수 있습니다.
* 필수 메타데이터가 포함되지 않은 자산을 검색하려면 [필수 메타데이터를 참조하십시오](#mandatorymetadata).
* 검색은 모든 메타데이터 필드를 사용합니다. 12를 검색하는 것과 같은 일반 검색은 일반적으로 많은 결과를 반환합니다. 더 나은 결과를 얻으려면 큰 따옴표(작은 따옴표가 아님)를 사용하거나 숫자가 특수 문자 없이 단어에 인접하는지 확인합니다(예: `shoe12`).
* 전체 텍스트 검색은 `-` 및 `^`등의 연산자를 지원합니다. 이러한 문자를 문자열 리터럴으로 검색하려면 검색 표현식을 큰 따옴표로 묶습니다. 예를 들어, 대신 `"Notebook - Beauty"` 를 사용합니다 `Notebook - Beauty`.
* 검색 결과가 너무 많으면 원하는 자산에 대해 검색 [범위를](#scope) 0으로 제한합니다. 특정 파일 유형, 특정 위치, 특정 메타데이터 등 원하는 에셋을 보다 효과적으로 찾는 방법을 알고 있을 때 가장 적합합니다.

* **태그 지정**:태그를 사용하면 보다 효율적으로 검색 및 검색할 수 있는 자산을 분류할 수 있습니다. Tagging을 사용하면 적절한 분류법을 다른 사용자 및 워크플로우에 전파할 수 있습니다. AEM은 사용 및 트레이닝을 통해 자산에 더 잘 태그를 지정할 수 있는 Adobe Sensei의 지능적인 서비스를 사용하여 에셋에 자동으로 태그를 지정하는 방법을 제공합니다. 자산을 검색할 때 계정에서 기능이 활성화되면 스마트 태그가 포함됩니다. 내장된 검색 기능과 함께 작동합니다. 검색 [동작을 참조하십시오](#searchbehavior). 검색 결과가 표시되는 순서를 최적화하기 위해 일부 특정 자산의 검색 순위를 [높일](#searchrank) 수 있습니다.

* **인덱싱**:인덱싱된 메타데이터와 자산만 검색 결과에 반환됩니다. 더 나은 취재와 성과를 위해서는 적절한 색인 작성 및 우수 사례를 따르십시오. 색인 [지정을 참조하십시오](#searchindex).

## 검색을 보여 주는 몇 가지 예 {#samples}

키워드 주위에 이중 인용구를 사용하여 사용자가 지정한 정확한 순서로 구문이 포함된 자산을 찾습니다.

![따옴표가 있는 경우와 없는 경우 검색 동작](assets/search_with_quotes.gif)

*그림:따옴표가 있는 경우와 없는 경우에는 검색 동작을 참조하십시오.*

**별표 와일드카드를 사용하여 검색**:검색을 확장하려면 검색어 앞이나 뒤에 별표를 사용하여 문자 수에 관계없이 검색어를 찾습니다. 예를 들어 별표 없이 실행만 검색해도 변형된 단어(메타데이터에 포함)가 포함된 에셋은 반환되지 않습니다. 별표는 문자 수에 관계없이 쓰인다. 예,

* `run` 정확히 run 키워드로 자산 반환
* `run*` 실행, 실행, 실행 취소 등으로 자산을 반환합니다.
* `*run` learn, rerun 등을 반환합니다.
* `*run*` 가능한 모든 조합을 반환합니다.

![예를 사용하여 자산 검색에서 별표 와일드카드의 사용](assets/search_with_asterisk_run.gif)

*그림:예를 사용하여 자산 검색에서 별표 와일드카드의 사용을 보여 줍니다.*

**물음표 와일드카드로 검색**:검색을 확장하려면 하나 이상의 &#39;?&#39;를 사용하십시오. 문자를 정확하게 개수와 일치시킵니다. 예를 들어 다음 그림에서는

* `run???` 쿼리가 자산이 일치하지 않습니다.

* `run????` query는 그 다음 `running` 4자로 된 단어와 일치합니다 `run`.

* `??run` query는 앞에 두 문자가 있는 단어 `rerun` 와 일치합니다 `run`.

![예를 사용하여 자산 검색에서 물음표 와일드카드 사용](assets/search_with_questionmark_run.gif)

*그림:예를 사용하여 자산 검색에서 물음표 와일드카드의 사용을 보여 줍니다.*

**키워드 제외**:키워드를 포함하지 않는 자산을 검색하려면 대시를 사용합니다. 예를 들어 `running -shoe` 쿼리는 포함되지만 포함되지 않은 자산을 `running`반환합니다 `shoe`. 마찬가지로 쿼리는 포함되지만 포함되지 않은 자산 `camp -night` 을 `camp` `night`반환합니다. 쿼리는 `camp-night` 와 둘 다 포함된 자산을 `camp` 반환합니다 `night`.

![대시를 사용하여 제외된 키워드를 포함하지 않는 자산을 검색합니다](assets/search_dash_exclude_keyword.gif)*그림:제외된 키워드를 포함하지 않는 자산을 검색하기 위해 대시 사용*

<!--
## Configuration and administration tasks related to search functionality {#configadmin}

### Search index configurations {#searchindex}

Asset discovery relies on indexing of DAM contents, including the metadata. Faster and accurate asset discovery relies on optimized indexing and appropriate configurations. See [indexing](/help/operations/indexing.md).
-->

<!--
### Visual or similarity search {#configvisualsearch}

Visual search uses smart tagging and requires AEM 6.5.2.0 or later. After configuring smart tagging functionality, follow these steps.

1. In AEM CRXDE, in `/oak:index/lucene` node, add the following properties and values and save the changes.

    * `costPerEntry` property of type `Double` with the value `10`.

    * `costPerExecution` property of type `Double` with the value `2`.

    * `refresh` property of type `Boolean` with the value `true`.

   This configuration allows searches from the appropriate index.

1. To create Lucene index, in CRXDE, at `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`, create node named `imageFeatures` of type `nt-unstructured`. In `imageFeatures` node,

    * Add `name` property of type `String` with the value `jcr:content/metadata/imageFeatures/haystack0`.

    * Add `nodeScopeIndex` property of type `Boolean` with the value of `true`.

    * Add `propertyIndex` property of type `Boolean` with the value of `true`.

    * Add `useInSimilarity` property of type `Boolean` with the value `true`.

   Save the changes.

1. Access `/oak:index/damAssetLucene/indexRules/dam:Asset/properties/predictedTags` and add `similarityTags` property of type `Boolean` with the value of `true`.
1. Apply Smart Tags to the assets in your AEM repository. See [how to configure smart tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html).
1. In CRXDE, in `/oak-index/damAssetLucene` node, set the `reindex` property to `true`. Save the changes.
1. (Optional) If you have customized search form then copy the `/libs/settings/dam/search/facets/assets/jcr%3Acontent/items/similaritysearch` node to `/conf/global/settings/dam/search/facets/assets/jcr:content/items`. Save all the changes.

For related information, see [understand smart tags in AEM](https://helpx.adobe.com/experience-manager/kt/help/assets/smart-tags-feature-video-understand.html) and [how to manage smart tags](/help/assets/smart-tags.md).
-->

<!--
### Mandatory metadata {#mandatorymetadata}

Business users, administrators, or DAM librarians can define some metadata as mandatory metadata that is a must for the business processes to work. For various reasons, some assets may be missing this metadata, such as legacy assets or assets migrated in bulk. Assets with missing or invalid metadata are detected and reported based on the indexed metadata property. To configure it, see [mandatory metadata](/help/assets/metadata-schemas.md#defining-mandatory-metadata).

### Modify search facets {#searchfacets}

To improve the speed of discovery, AEM Assets offers search facets using which you can filter the search results. The Filters panel includes a few standard facets by default. Administrators can customize the Filters panel to modify the default facets using the in-built predicates. AEM provides a good collection of in-built predicates and an editor to customize the facets. See [search facets](/help/assets/search-facets.md).

### Extract text when uploading assets {#extracttextupload}

You can configure AEM to extract the text from the assets when users upload assets, such as PSD or PDF files. AEM indexes the extracted text and helps users search these assets based on the extracted text. See [upload assets](/help/assets/manage-digital-assets.md#uploading-assets).
-->

<!-- TBD: Check with gklebus and engineering if these customization are possible in CS.

### Custom predicates to filter search results {#custompredicates}

Predicates are used to create facets. Administrators can customize the search facets in the Filters panel using pre-configured predicates. These predicates can be customized using overlays. See [create custom predicates](/help/assets/searchx.md).

You can search for digital assets based on one or more of the following properties. Filters that apply on some of these properties are available by default and some other filters can be custom-created to apply on the other properties.

| Search field | Search property values |
|---|---|
| Approved Status | Approved or Rejected. |
| Audio Bitrate | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Audio Codec | Libvorbis, Lame MP3, AAC Encoding. Value is stored in the metadata of video renditions only. |
| File Size | Small, Medium, or Large. |
| Last Modified | Hour, Day, Week, Month, or Year. |
| MIME Types | Images, Documents, Multimedia, Archives, or Other. |
| Orientation | Horizontal, Vertical, or Square. |
| Publish Status | Published or Unpublished. |
| Style | Color, or Black & White. |
| Video Bitrate | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Video Codec | x264. Value is stored in the metadata of video renditions only. |
| Video Format | DVI, Flash, MPEG4, MPEG, OGG Theora, QuickTime, Windows Media. Value is stored in the metadata of the source video and any renditions. |
| Video Height | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |
| Video Width | Specified as a minimum and maximum value. Value is stored in the metadata of video renditions only. |

-->

## 자산 검색 결과를 사용한 작업 {#aftersearch}

기준과 일치하는 일부 검색 자산이 표시되면 이러한 검색 결과에 대해 다음 일반 작업을 수행하거나 수행할 수 있습니다.

* 메타데이터 속성 및 기타 정보를 봅니다.
* 하나 이상의 자산을 다운로드합니다.
* 데스크톱 작업을 사용하여 이러한 자산을 데스크톱 앱에서 엽니다.
* 스마트 컬렉션 제작

### 검색 결과 정렬 {#sort}

검색 결과를 정렬하면 필요한 자산을 보다 신속하게 찾을 수 있습니다. 검색 결과 정렬은 목록 보기에서 작동하며 필터 **[[!UICONTROL 패널에서]](#searchui)** 파일 **[!UICONTROL 을 선택한 경우에만]** 작동합니다. [!DNL Assets] 서버측 정렬을 사용하여 폴더 또는 검색 쿼리의 결과 내의 모든 자산(wherever)을 빠르게 정렬합니다. 서버측 정렬은 클라이언트측 정렬보다 빠르고 정확한 결과를 제공합니다.

목록 보기에서는 임의의 폴더에서 자산을 정렬할 수 있는 것처럼 검색 결과를 정렬할 수 있습니다. 정렬은 이름, 제목, 상태, Dimension, 크기, 등급, 사용, (날짜) 생성됨, (날짜) 수정됨, (날짜) 게시됨, 워크플로우 및 체크 아웃과 같은 열에서 작동합니다.

정렬 기능에 대한 제한 사항은 [제한 사항을 참조하십시오](#limitations).

### 자산의 세부 정보 확인 {#checkinfo}

검색 결과 페이지에서 검색된 자산의 세부 정보를 확인할 수 있습니다.

자산의 모든 메타데이터를 보려면 자산을 선택하고 도구 모음에서 **[!UICONTROL 속성을]** 클릭합니다.

자산의 자산이나 버전 내역에 대한 주석을 확인하려면 자산을 클릭하여 큰 크기의 미리 보기를 엽니다. 왼쪽 레일에서 타임라인을 열고 **[!UICONTROL 댓글]** 또는 **[!UICONTROL 버전을 선택합니다]**. 댓글 또는 버전과 같은 타임라인 활동을 시간순으로 정렬할 수도 있습니다.

![검색 자산에 대한 타임라인 항목 정렬](assets/sort_timeline_search_results.gif)

검색 자산에 대한 타임라인 항목 정렬

### 검색된 자산 다운로드 {#download}

폴더에서 일반 자산을 다운로드하는 것처럼 검색된 자산과 해당 표현물을 다운로드할 수 있습니다. 검색 결과에서 하나 이상의 자산을 선택하고 도구 모음에서 **[!UICONTROL 다운로드를]** 클릭합니다.

### 메타데이터 속성 일괄 업데이트 {#metadataupdates}

여러 자산의 공통 메타데이터 필드를 일괄 업데이트할 수 있습니다. 검색 결과에서 하나 이상의 자산을 선택합니다. 도구 **[!UICONTROL 모음에서]** 속성을 클릭하고 필요에 따라 메타데이터를 업데이트합니다. 완료되면 **[!UICONTROL 저장 및 닫기를]** 클릭합니다. 업데이트된 필드의 기존 메타데이터를 덮어씁니다.

단일 폴더 또는 컬렉션에서 사용할 수 있는 자산의 경우 메타데이터를 일괄 [업데이트하는 것이 더 쉽습니다](/help/assets/manage-metadata.md#manage-assets-metadata). 여러 폴더에서 사용할 수 있거나 일반적인 기준과 일치하는 자산의 경우 검색을 통해 메타데이터를 일괄 업데이트하는 것이 더 빠릅니다.

### 스마트 컬렉션 {#collections-1}

컬렉션은 컬렉션이 이러한 자산에 대한 참조만 포함되기 때문에 다른 위치의 자산을 포함할 수 있는 순차적 자산 집합입니다. 컬렉션은 다음 두 가지 유형입니다.

* 자산, 폴더 및 기타 컬렉션의 정적 참조 목록입니다.
* 검색 기준을 기반으로 컬렉션의 자산을 채우는 동적 목록(스마트 컬렉션)

검색 조건에 따라 스마트 컬렉션을 만들 수 있습니다. 필터 **[!UICONTROL 패널에서]** **[!UICONTROL 파일]** 을 **[!UICONTROL 선택하고 스마트 컬렉션]**&#x200B;을 클릭합니다. 컬렉션 [관리를 참조하십시오](/help/assets/manage-collections.md).

## 예기치 않은 검색 결과 {#unexpectedresults}

**누락된 메타데이터**&#x200B;검색:필수 메타데이터가 없는 자산을 검색할 때 AEM은 유효한 메타데이터가 있는 일부 자산을 표시할 수 있습니다. 인덱스 메타데이터 속성을 기반으로 누락된 메타데이터가 검색되고 보고됩니다. 자산 메타데이터가 수정되더라도 색인 재설정이 발생할 때까지 누락된 메타데이터로 계속 표시됩니다. 필수 [메타데이터를 참조하십시오](/help/assets/metadata-schemas.md#defining-mandatory-metadata).

**검색 결과가 너무 많습니다**.너무 많은 검색 결과를 얻지 않으려면 검색 결과를 제한하는 것이 좋습니다. 예를 들어 DAM에서 자산을 검색하려면 Omnisearch 막대 `Location:Assets` 에서 선택합니다. 더 많은 검색 필터를 보려면 검색 [범위를 참조하십시오](#scope).

<!-- Another reason to get more than expected search results can be use of smarts tags. See [search behavior with smart tags](#withsmarttags). 
-->

<!--
**Partially related or unrelated search results**: AEM may display seemingly partially related or unrelated assets, alongside the desired assets in the search results. If you enable Enhanced Smart Tags, the search behavior changes slightly. See how it changes [after smart tagging](#withsmarttags).
-->

**새로 업로드한 자산에 대한 자동 완성 제안 없음**:Omnisearch 막대에서 검색 키워드를 입력하기 시작하면 최근 업로드된 자산의 메타데이터(제목, 태그 등)를 추천으로 즉시 사용할 수 없습니다. AEM Assets은 백그라운드 작업을 실행하기 전에 시간 초과 기간(기본적으로 1시간)이 만료될 때까지 기다렸다가 새로 업로드되거나 업데이트된 모든 자산에 대한 메타데이터를 색인화한 다음 메타데이터를 제안 목록에 추가합니다.

**검색 결과 없음**:AEM에서 검색 쿼리에 대해 빈 페이지를 표시하는 경우 다음과 같은 이유가 있을 수 있습니다.

* 쿼리와 일치하는 자산이 없습니다.
* 검색 쿼리 앞에 공백을 추가합니다. 이것은 [알려진 제한이다](#limitations).

* 지원되지 않는 메타데이터 필드에 검색하는 키워드가 포함되어 있습니다. 일부 메타데이터 필드는 검색으로 간주되지 않습니다. 자세한 내용은 [범위를 참조하십시오](#scope).
* 자산 설정 시간 및 해제 시간이 구성되며 자산 해제 시간 동안 검색이 수행되었습니다.

**검색 필터/조건자를 사용할 수 없습니다**.사용자 인터페이스에서 검색 필터에 대한 예상 사용자 지정을 사용할 수 없는 경우 관리자에게 문의하여 사용 중인 모든 작성자 및 프로덕션 서버에 대해 사용자 지정이 구현되었는지 확인하십시오. 구성이 잘못되었을 수 있습니다.

## 검색 관련 문제 해결 {#troubleshoot}

<!-- TBD: Expand this section.
-->

아래의 문제 및 가능한 작업 과정을 참조하십시오.

* 예상 검색 필터/조건자가 표시되지 않으면 관리자에게 문의하십시오.
* 시각적으로 유사한 이미지를 검색할 때 검색 결과에서 예상 이미지가 누락될 수 있습니다. 이러한 자산이 인덱싱되어 있고 스마트 태그가 지정되었는지 확인합니다.
* 시각적으로 유사한 이미지를 검색할 때 겉보기에 부적절한 이미지가 검색 결과에 표시될 수 있습니다. AEM은 가능한 한 많은 관련 자산을 표시합니다. 관련성이 낮은 이미지가 있는 경우 결과에 추가되지만 검색 등급이 낮습니다. 검색 결과를 아래로 스크롤하면 검색 자산의 일치 항목 및 연관성이 줄어듭니다.
