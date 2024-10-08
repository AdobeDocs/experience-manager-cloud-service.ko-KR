---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 에셋 선택기를 사용하여 애플리케이션 내에서 에셋의 메타데이터와 렌디션을 검색, 찾기 및 검색할 수 있습니다.
role: Admin, User
exl-id: 62b0b857-068f-45b7-9018-9c59fde01dc3
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1332'
ht-degree: 34%

---

# 마이크로 프론트엔드 자산 선택기 {#Overview}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

마이크로 프론트엔드 자산 선택기는 [!DNL Experience Manager Assets] 저장소와 간편하게 통합하는 사용자 인터페이스를 제공하므로 사용자는 해당 저장소에서 사용 가능한 디지털 자산을 탐색 또는 검색하고 애플리케이션 작성 경험에 사용할 수 있습니다.

자산 선택기 패키지를 사용하여 마이크로 프론트엔드 사용자 인터페이스를 애플리케이션 경험에 사용할 수 있습니다. 이렇게 하면 패키지에 대한 모든 업데이트를 자동으로 가져오고 최근 배포된 자산 선택기가 애플리케이션 내에서 자동으로 로드됩니다.

![개요](assets/overview.png)

자산 선택기는 다음과 같은 많은 이점을 제공합니다.

* 바닐라 JavaScript 라이브러리를 사용하여 [Adobe](/help/assets/integrate-asset-selector-adobe-app.md) 또는 [Adobe 이외](/help/assets/integrate-asset-selector-non-adobe-app.md) 응용 프로그램과 쉽게 통합할 수 있습니다.
* 자산 선택기 패키지에 대한 업데이트가 애플리케이션에서 사용할 수 있는 자산 선택기에 자동으로 배포되므로 유지 관리가 간편합니다. 최신 수정 사항을 로드하기 위해 애플리케이션 내에서 업데이트를 수행하지 않아도 됩니다.
* 애플리케이션 내에서 자산 선택기 표시를 제어하는 속성을 통해 손쉽게 사용자 정의할 수 있습니다.
* 전체 텍스트 검색, 기본 제공 및 사용자 정의 필터를 통해 작성 경험 내에서 사용할 자산을 빠르게 탐색할 수 있습니다.
* IMS 조직 내에서 저장소를 전환하여 자산을 선택할 수 있습니다.
* 이름, 차원 및 크기별로 에셋을 정렬하고 목록, 그리드, 갤러리 또는 폭포 보기에서 보는 기능.

<!--Perform the following tasks to integrate and use Asset Selector with your [!DNL Experience Manager Assets] repository:

1. [Install Asset Selector](#installation)
2. [Integrate Asset Selector using Vanilla JS](#integration-using-vanilla-js)
3. [Use Asset Selector](#using-asset-selector)
-->

<!--
## Setting up Asset Selector {#asset-selector-setup}

![Asset Selector set up](assets/asset-selector-prereqs.png)
-->

## 사전 요구 사항{#prereqs}

다음 통신 방법을 확인해야 합니다.

* 응용 프로그램이 HTTPS에서 실행 중입니다.
* 애플리케이션의 URL은 IMS 클라이언트의 리디렉션 URL 허용 목록에 있습니다.
* 웹 브라우저에서 팝업을 사용하여 IMS 로그인 흐름을 구성하고 렌더링합니다. 따라서 대상 브라우저에서 팝업을 활성화하거나 허용해야 합니다.

자산 선택기의 IMS 인증 워크플로우가 필요한 경우 위의 사전 요구 사항을 사용하십시오. 또는 IMS 워크플로우로 이미 인증한 경우 대신 IMS 정보를 추가할 수 있습니다.

**자세히 보기**

* [에셋 선택기를 Adobe 앱과 통합](/help/assets/integrate-asset-selector-adobe-app.md)
* [에셋 선택기를 Adobe이 아닌 앱과 통합](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [자산 선택기 Dynamic Media Open API 통합](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!IMPORTANT]
>
> 이 저장소는 Asset Selector를 통합하기 위해 사용 가능한 API 및 사용 예를 설명하는 보조 설명서로서 사용되도록 설계되었습니다. 에셋 선택기를 설치하거나 사용하기 전에 조직에 Experience Manager Assets as a Cloud Service 프로필의 일부로 에셋 선택기에 대한 액세스 권한이 제공되었는지 확인하십시오. 제공되지 않은 경우 이러한 구성 요소를 통합하거나 사용할 수 없습니다. 프로비저닝을 요청하려면 프로그램 관리자가 Admin Console에서 P2로 표시된 지원 티켓을 가져와 다음 정보를 포함해야 합니다.
>
>* 통합 애플리케이션이 호스팅되는 도메인 이름.
>* 프로비저닝 후 조직에 자산 선택기 구성에 필요한 요청된 환경에 해당하는 `imsClientId`, `imsScope` 및 `redirectUrl`이(가) 제공됩니다. 이러한 유효한 속성이 없으면 설치 단계를 실행할 수 없습니다.

## 설치 {#installation}

자산 선택기는 ESM CDN(예: [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/))과 [UMD](https://github.com/umdjs/umd) 버전을 통해 사용할 수 있습니다.

**UMD 버전**&#x200B;을 사용하는 브라우저의 경우(권장됨):

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

**ESM CDN 버전**&#x200B;을 사용하며 `import maps`가 지원되는 브라우저의 경우:

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
</script>
```

**ESM CDN 버전**&#x200B;을 사용하는 Deno/Webpack Module Federation의 경우:

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
```

## 자산 선택기 사용하기 {#using-asset-selector}

자산 선택기를 설정하고 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]와 자산 선택기를 사용하도록 인증되면 자산을 선택하거나 다른 다양한 작업을 수행하여 저장소 내에 있는 자산을 검색할 수 있습니다.

![자산-선택기-사용](assets/using-asset-selector.png)

* **A**: [패널 숨기기/표시](#hide-show-panel)
* **B**: [저장소 전환기](#repository-switcher)
* **C**: [자산](#repository)
* **D**: [필터](#filters)
* **E**: [검색 창](#search-bar)
* **F**: [정렬](#sorting)
* **G**: [오름차순 또는 내림차순으로 정렬](#sorting)
* **H**: [보기](#types-of-view)

### 패널 숨기기/표시 {#hide-show-panel}

왼쪽 탐색에서 폴더를 숨기려면 **[!UICONTROL 폴더 숨기기]** 아이콘을 클릭합니다. 변경 내용을 실행 취소하려면 **[!UICONTROL 폴더 숨기기]** 아이콘을 다시 클릭합니다.

### 저장소 전환기 {#repository-switcher}

또한 에셋 선택기를 사용하여 에셋 선택을 위한 저장소를 전환할 수 있습니다. 왼쪽 패널에 있는 드롭다운에서 원하는 저장소를 선택할 수 있습니다. 드롭다운 목록에서 사용할 수 있는 저장소 옵션은 `index.html` 파일에 정의된 `repositoryId` 속성을 기반으로 하며, 로그인한 사용자가 액세스하는 선택한 IMS 조직의 환경을 기반으로 합니다. 소비자는 기본 `repositoryID`를 전달할 수 있으며 이 경우 자산 선택기는 저장소 전환기 렌더링을 중지하고 주어진 저장소의 자산만 렌더링합니다.

### 자산 저장소

작업을 수행하는 데 사용할 수 있는 자산 폴더 모음입니다.

### 기본 제공 필터 {#filters}

자산 선택기에는 검색 결과를 세분화할 수 있는 기본 필터 옵션도 제공됩니다. 사용 가능한 필터는 다음과 같습니다.

* **[!UICONTROL Status]:**&#x200B;에는 `all`, `approved`, `rejected` 또는 `no status` 중 에셋의 현재 상태가 포함됩니다.
* **[!UICONTROL 파일 형식]:**&#x200B;에 `folder`, `file`, `images`, `documents` 또는 `video`이(가) 포함되어 있습니다.
* **[!UICONTROL 만료 상태]:**&#x200B;에서 만료 기간을 기준으로 자산을 언급합니다. `[!UICONTROL Expired]` 확인란을 선택하여 만료된 에셋을 필터링하거나, 에셋의 `[!UICONTROL Expiration Duration]`을(를) 설정하여 만료 기간에 따라 에셋을 표시할 수 있습니다. 에셋이 이미 만료되었거나 만료될 위기에 처하면 동일한 정보를 나타내는 배지가 나타납니다. 또한 만료된 에셋을 사용(또는 드래그 앤 드롭)할지 여부를 제어할 수 있습니다. [만료된 에셋 사용자 지정](/help/assets/asset-selector-customization.md#customize-expired-assets)에 대해 자세히 알아보세요. 기본적으로 향후 30일 이내에 만료되는 자산에 대해 **곧 만료** 배지가 표시됩니다. 그러나 `expirationDate` 속성을 사용하여 만료를 구성할 수 있습니다.

  >[!TIP]
  >
  > 향후 만료 날짜를 기준으로 자산을 보거나 필터링하려면 `[!UICONTROL Expiration Duration]` 필드에 미래 날짜 범위를 언급하십시오. **곧 만료** 배지가 있는 자산이 표시됩니다.

* **[!UICONTROL MIME 형식]:**&#x200B;에 `JPG`, `GIF`, `PPTX`, `PNG`, `MP4`, `DOCX`, `TIFF`, `PDF`, `XLSX`이(가) 포함되어 있습니다.
* **[!UICONTROL 이미지 크기]:**&#x200B;에는 이미지의 최소/최대 너비, 최소/최대 높이가 포함됩니다.

  ![레일-보기-예](assets/filters-asset-selector.png)

### 사용자 정의 검색

전체 텍스트 검색 외에도 에셋 선택기를 사용하여 사용자 지정된 검색을 사용하여 파일 내에서 에셋을 검색할 수 있습니다. 모달 보기 및 레일 보기 모드 모두에서 사용자 정의 검색 필터를 사용할 수 있습니다.

![사용자 정의-검색](assets/custom-search1.png)

기본 검색 필터를 만들어 자주 검색하고 나중에 사용하는 필드를 저장할 수도 있습니다. 자산에 대한 사용자 정의 검색을 만들기 위해 `filterSchema` 속성을 사용할 수 있습니다.

### 검색 창 {#search-bar}

에셋 선택기를 사용하여 선택한 저장소 내의 에셋에 대한 전체 텍스트 검색을 수행할 수 있습니다. 예를 들어 검색 창에 `wave` 키워드를 입력하면 메타데이터 속성에 언급된 것 중 `wave` 키워드가 있는 모든 자산이 표시됩니다.

### 정렬 {#sorting}

자산 선택기에서 자산의 이름, 차원 또는 크기별로 자산을 정렬할 수 있습니다. 자산을 오름차순 또는 내림차순으로 정렬할 수도 있습니다.

### 보기 유형 {#types-of-view}

에셋 선택기를 사용하여 에셋을 다음 네 가지 보기로 볼 수 있습니다.

* **![목록 보기](assets/do-not-localize/list-view.png) [!UICONTROL 목록 보기]** 목록 보기에는 스크롤할 수 있는 파일과 폴더가 한 열에 표시됩니다.
* **![눈금 보기](assets/do-not-localize/grid-view.png) [!UICONTROL 눈금 보기]** 눈금 보기에는 스크롤할 수 있는 파일과 폴더가 행 및 열 눈금에 표시됩니다.
* **![갤러리 보기](assets/do-not-localize/gallery-view.png) [!UICONTROL 갤러리 보기]** 갤러리 보기에는 파일 또는 폴더가 가운데로 잠긴 가로 목록에 표시됩니다.
* **![폭포 보기](assets/do-not-localize/waterfall-view.png) [!UICONTROL 폭포 보기]** 폭포 보기에는 파일 또는 폴더가 Bridge 형태로 표시됩니다.

**개요 그래픽**


## 주요 기능에 대해 자세히 알아보기 {#key-capabilities-asset-selector}

<table>
<tr>
    <td>
        <img src="assets/integrate-asset-selector.gif" width="70px" height="70px" alt="자산 선택기 통합 그래픽"><br/>
        <a href="integrate-asset-selector.md">자산 선택기 통합</a>
        <p>
        <em>자산 선택기를 여러 응용 프로그램과 통합하는 다양한 기능에 대해 알아봅니다.
        </p>
     </td>
    <td>
        <img src="assets/with-adobe-app.gif" width="70px" height="70px" alt="에셋 선택기와 Adobe 애플리케이션 통합 그래픽"><br/>
        <a href="integrate-asset-selector.md">Adobe 응용 프로그램과 자산 선택기 통합</a>
        <p>
        <em>에셋 선택기를 다양한 Adobe 응용 프로그램과 통합하는 방법을 알아봅니다.</em>
        </p>
    </td>
    <td>
        <img src="assets/third-party-app.gif" width="70px" height="70px" alt="자산 선택기 통합 그래픽"><br/>
        <a href="integrate-asset-selector.md">자산 선택기와 타사 응용 프로그램 통합</a>
        <p>
        <em>자산 선택기를 Adobe이 아닌 응용 프로그램과 통합하는 기능을 살펴봅니다.</em>
        </p>
    </td>
    <td>
        <img src="assets/with-dynamic-media-open-api.gif" width="70px" height="70px" alt="자산 선택기 통합 그래픽"><br/>
        <a href="integrate-asset-selector.md">Dynamic Media Open API와 자산 선택기 통합</a>
        <p>
        <em>자산 선택기를 Dynamic Media Open API와 통합하는 방법을 이해합니다.</em>
        </p>
     </td>
     <td>
        <img src="assets/asset-selector-examples.gif" width="70px" height="70px" alt="자산 선택기 속성 그래픽"><br/>
        <a href="asset-selector-customization.md">자산 선택기 속성</a>
        <p>
        <em>필터, 에셋 선택, 만료된 에셋 등과 같은 에셋 선택기의 다양한 구성 요소를 사용자 지정하는 기본 사항에 대해 알아봅니다. </em>
        </p>
    </td>
</tr>
<tr>
    <td>
        <img src="assets/asset-selector-properties.gif" width="70px" height="70px" alt="자산 선택기 예 그래픽"><br/>
        <a href="asset-selector-customization.md">자산 선택기 예</a>
        <p>
        <em>실제 사용 방법을 이해합니다. </em>
        </p>
    </td>
    <td>
        <img src="assets/customize-asset-selector.gif" width="70px" height="70px" alt="자산 선택기 사용자 지정 그래픽"><br/>
        <a href="asset-selector-customization.md">자산 선택기 사용자 지정</a>
        <p>
        <em>사용 편이성에 따라 에셋 선택기의 다양한 구성 요소를 구성하고 사용자 지정합니다. </em>
        </p>
    </td>
    <td>
        <img src="assets/asset-selector-upload.gif" width="70px" height="70px" alt="자산 선택기 업로드 그래픽"><br/>
        <a href="asset-selector-upload.md">자산 선택기 업로드</a>
        <p>
        <em>로컬 또는 타사 파일 시스템에서 자산 선택기에 파일이나 폴더를 업로드하는 방법을 알아봅니다. </em>
        </p>
    </td>
     <td>
        <img src="assets/asset-selector-collections.gif" width="70px" height="70px" alt="에셋 선택기 컬렉션 그래픽"><br/>
        <a href="asset-selector-collections.md">자산 선택기 컬렉션</a>
        <p>
        <em>Experience Manager 저장소를 사용하여 에셋 선택기 내에서 컬렉션을 사용하는 방법에 대해 알아봅니다. </em>
        </p>
    </td>
    <td>
    </td>
</tr>
</table>

>[!MORELIKETHIS]
>
>* [자산 선택기 사용자 지정](/help/assets/asset-selector-customization.md)
>* [다양한 응용 프로그램과 자산 선택기 통합](/help/assets/integrate-asset-selector.md)
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [OpenAPI 기능을 사용하여 Dynamic Media과 자산 선택기 통합](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
