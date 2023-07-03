---
title: 에서 PDF 문서 관리 [!DNL Adobe Experience Manager].
description: 에서 PDF 문서 관리 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
feature: Asset Management
role: User,Admin
exl-id: 29660869-6902-4093-845b-cd629be59d4d
source-git-commit: 589ed1e1befa84c0caec0eed986c3e1a717ae602
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 4%

---

# Experience Manager Assets as a Cloud Service으로 PDF 문서 관리 {#add-assets-to-experience-manager}

Experience Manager Assets은 Document Cloud PDF 뷰어와 원활하게 통합되므로 PDF 문서의 여러 페이지를 미리 볼 수 있습니다. 또한 주석, 검색 텍스트, 책갈피 및 썸네일을 사용하여 PDF 문서를 탐색하는 등의 고급 Document Cloud PDF 뷰어 기능을 동일한 지붕 아래에서 사용할 수도 있습니다. Experience Manager Assets을 사용하면 지원되는 다른 형식의 문서를 업로드하고 PDF 형식으로 미리 볼 수도 있습니다.

Document Cloud PDF 뷰어는 다음과 같은 방법으로 AEM Assets에 이점을 제공합니다.
* [PDF Document Cloud 뷰어 구성 요소 지원](#pdf-doc-cloud)
* [PDF 자산에 대한 여러 페이지 미리보기 및 주석 지원](#multi-page)
* [다른 형식의 문서에 대한 여러 페이지 미리보기 지원](#multi-format)

> 팁
> 이전에 업로드한 PDF 문서의 여러 PDF 미리보기를 가져올 수 없는 경우 페이지를 선택하고 을(를) 클릭합니다 **![재처리](/help/assets/assets/Reprocess.svg) 자산 재처리**.
>

## PDF Document Cloud 뷰어 구성 요소 지원 {#pdf-doc-cloud}

AEM Assets의 기본 PDF Doc Cloud 뷰어에는 다음 구성 요소가 있습니다.

* **페이지 썸네일을 사용하는 PDF 뷰어** 축소판 보기는 PDF 문서의 페이지를 미리 보는 작은 보기입니다. 썸네일을 사용하여 원하는 페이지로 바로 이동할 수 있습니다. 다음을 통해 선택한 PDF 문서의 썸네일에 액세스할 수 있습니다. ![축소판](/help/assets/assets/thumbnail.svg) 왼쪽 창에서 을 클릭합니다.

* **책갈피를 사용한 PDF 뷰어** 책갈피는 문서의 콘텐츠로 이동하는 직접 링크입니다. 다음을 통해 선택한 PDF 문서의 책갈피에 액세스할 수 있습니다. ![책갈피](/help/assets/assets/bookmark.svg) 왼쪽 창에서 을 클릭합니다.

* **PDF에서 검색** 검색을 사용할 수 있습니다. ![검색](/help/assets/assets/Search.svg) PDF 문서에서 텍스트를 조회합니다.

* **페이지 위로/페이지 아래로** 페이지 위로 사용 ![페이지 위로](/help/assets/assets/ArrowUp.svg) 또는 페이지 아래로 ![페이지 아래로](/help/assets/assets/ArrowDown.svg) 문서를 스크롤할 수 있습니다.

* **축소/확대** 축소 사용 ![축소](/help/assets/assets/ZoomOut.svg) 또는 확대 ![확대](/help/assets/assets/ZoomIn.svg) 문서를 추적합니다.

* **페이지 맞춤** 너비 또는 높이 차원을 사용하여 화면 크기에 맞게 문서를 맞출 수 있습니다.

* **고정/고정 해제 PDF** 이 옵션을 사용하여 기본 PDF 뷰어의 구성 요소를 고정하거나 고정 해제할 수 있습니다.

## PDF 자산에 대한 여러 페이지 미리보기 및 주석 지원 {#multi-page}

Adobe Experience Manager Assets를 사용하면 여러 페이지로 구성된 PDF 문서를 미리 볼 수 있습니다. PDF 문서의 여러 페이지를 미리 보려면 다음 단계를 고려하십시오.

1. 다음 단계를 수행합니다. [AEM에서 에셋 업로드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en).
1. 업로드하고 미리 보려는 PDF 문서를 찾습니다.
1. 문서를 엽니다.
1. PDF 문서 뷰어는 기본적으로 로드됩니다. 렌디션 패널에서 PDF 렌디션을 선택할 수도 있습니다.
1. 렌디션 드롭다운에서 **모든 표현물**.

또한 신청할 수 있습니다 [주석](#pdf-annotations) 여러 PDF 미리보기의 페이지 문서로 이동합니다.

> 메모
> 미리 볼 수 있는 에셋의 최대 크기는 최대 100MB입니다.
>

>[!VIDEO](https://video.tv.adobe.com/v/3409355)

<!--
![Multi-page Preview](/help/assets/assets/multi-page.png)
-->

**PDF 주석{#pdf-annotations}**

Experience Manager Assets을 사용하면 PDF 문서에 주석을 추가할 수 있습니다. PDF 문서에는 여러 개의 주석이 있을 수 있습니다.

PDF 문서에 주석을 달려면 다음 단계를 수행하십시오.
1. Assets 인터페이스로 이동하여 주석을 달려는 PDF 문서로 이동합니다. 기본 PDF 뷰어가 오른쪽에 열리고 선택한 PDF 문서의 미리보기가 표시됩니다.
1. 클릭 **주석** 을 클릭합니다.
다음은 PDF 문서에 적용할 수 있는 주석입니다.

<table>
        <tr>
             <th> 주석 </th>
            <th> 설명 </th>
        </tr>
        <tr>
           <td> <img src="/help/assets/assets/Comment.svg"> 설명 </td>
            <td> 관찰을 표현하려면 Comment 를 선택합니다. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Text.svg"> 텍스트 상자 </td>
            <td> 텍스트 상자를 선택하여 텍스트를 입력합니다. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Note.svg"> 스티커 메모 </td>
            <td> PDF의 특정 영역에 추가할 수 있는 작은 텍스트나 미리 알림을 추가합니다. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Comment.svg"> 텍스트 형광펜 </td>
            <td> 다른 색상으로 강조 표시할 텍스트를 선택합니다. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextUnderline.svg"> 텍스트 밑줄 </td>
            <td> 밑줄을 표시할 텍스트를 선택합니다. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextStrikethrough.svg"> 취소선 </td>
            <td> 아웃할 텍스트를 선택합니다. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Draw.svg"> 그리기 </td>
            <td> PDF에 시각적 아트를 삽입합니다. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Erase.svg"> 드로잉 지우기 </td>
             <td> 드로잉을 제거하거나 명령취소합니다. </td>
        </tr>
    </table>

>[!NOTE]
>
>PDF 문서에 추가하는 주석은 미리보기 모드에서 사용할 수 있습니다. 그러나 PDF 문서를 다운로드하거나 인쇄할 때는 주석이 표시되지 않습니다.

## 다른 형식의 문서에 대한 여러 페이지 미리보기 지원 {#multi-format}

PDF 문서 외에도 다른 형식 유형의 문서에 대해 여러 페이지를 미리 볼 수도 있습니다. 지원되는 문서 형식 유형은 TXT, RTF, DOC, DOCX, PPT, PPTX, XLS 및 XLSX입니다. Experience Manager Assets은 이러한 문서 형식을 자동으로 PDF 형식으로 변환하여 미리보기에 사용할 수 있도록 합니다.

![다른 형식의 문서에 대한 다중 페이지 미리보기](/help/assets/assets/multi-page-other-formats.png)

지원되는 다른 문서 형식의 여러 페이지를 미리 보려면 다음 단계를 수행하십시오.
1. 다음 단계를 수행합니다. [AEM에서 에셋 업로드](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en).
1. 업로드할 문서를 검색하고 미리 봅니다.
1. 문서를 엽니다.
1. 왼쪽 패널의 정적 섹션 아래에서 PDF 를 선택합니다. 오른쪽 패널에는 에셋의 여러 페이지 미리보기가 표시됩니다. 미리 보려는 페이지를 선택하려면 왼쪽 패널에서 축소판을 선택합니다.

> 메모
> * 미리 볼 수 있는 에셋의 최대 크기는 최대 100MB입니다.
> * 미리 볼 XLS 또는 XLSX 파일의 최대 크기는 20MB입니다.
>

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
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
