---
title: 이미지 세트
description: Dynamic Media에서 이미지 세트로 작업하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Image Sets
role: User
exl-id: 2eb71f24-73d9-4b5c-8605-923a0e3d1505
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '2191'
ht-degree: 5%

---

# 이미지 세트 {#image-sets}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

이미지 세트는 사용자에게 썸네일 이미지를 클릭하여 항목의 다양한 보기를 볼 수 있는 통합된 보기 환경을 제공합니다. 이미지 집합을 사용하면 항목의 대체 보기를 표시할 수 있으며 뷰어는 이미지를 면밀하게 검사하는 확대/축소 도구를 제공합니다.

Image Sets are designated by a banner with the word `IMAGESET`. 또한 이미지 세트가 게시되면 **[!UICONTROL World]** 아이콘으로 표시된 게시 날짜가 배너에 있습니다. 또한 **[!UICONTROL 연필]** 아이콘으로 표시된 마지막 수정 날짜가 표시됩니다.

![chlimage_1-133](assets/chlimage_1-339.png)

이미지 세트 내에서 이미지 세트를 만들고 썸네일을 추가하여 견본을 만들 수도 있습니다.

이 응용 프로그램은 다른 색상, 패턴 또는 완료로 항목을 표시하려는 경우에 유용합니다. 색상 견본을 사용하여 이미지 세트를 만들려면 사용자에게 제공할 색상, 패턴 또는 마무리에 대해 각각 하나의 이미지가 필요합니다. 각 색상, 패턴 또는 마무리에 대해 하나의 색상, 패턴 또는 마무리 색상 견본이 필요합니다.

예를 들어 서로 다른 색상 지폐가 있는 캡의 이미지를 표시한다고 가정해 보십시오. 지폐는 빨간색, 녹색 및 파란색입니다. 이 경우에는 같은 캡으로 3타를 맞으셔야 합니다 빨간색으로 한 장, 초록색으로 한 장, 파란 지폐로 한 장이 필요합니다. 빨강, 녹색, 파랑 색상 견본도 필요합니다. 색상 견본은 사용자가 견본 집합 뷰어에서 클릭하여 붉은색 청구됨, 녹색 청구됨 또는 파란색 청구됨 캡을 표시하는 썸네일 역할을 합니다.

>[!NOTE]
>
>Assets 사용자 인터페이스에 대한 자세한 내용은 [Touch UI로 자산 관리](/help/assets/manage-digital-assets.md)를 참조하십시오.

이미지 집합을 생성할 때 Adobe에서는 다음 모범 사례를 권장하며 다음 제한을 적용합니다.

| 제한 유형 | 모범 사례 | 제한 적용됨 |
| --- | --- | --- |
| 세트당 중복 에셋 수 | 중복 항목 없음 | 20 |
| 세트당 최대 이미지 수 | 세트당 5-10개 이미지 | 1000년 |

[Dynamic Media 제한 사항](/help/assets/dynamic-media/limitations.md)도 참조하세요.

## 빠른 시작: 이미지 집합 {#quick-start-image-sets}

빠르게 시작하고 실행하려면:

1. 선택 사항. [일괄처리 집합 사전 설정을 만들고](/help/assets/dynamic-media/batch-set-presets-dm.md) 이를 회전 집합 이미지가 업로드되는 새 폴더에 적용합니다.

   일괄처리 집합 사전 설정을 사용하면 이미지 집합 생성을 자동화할 수 있습니다.

   >[!IMPORTANT]
   >
   >배치 세트는 IPS(이미지 프로덕션 시스템)가 자산 수집의 일부로 만듭니다.

1. [다중 보기를 위해 기본 소스 이미지를 업로드합니다](#uploading-assets-in-image-sets).

   이미지 세트의 이미지를 업로드합니다. 사용자는 이미지 세트 뷰어에서 이미지를 확대할 수 있습니다. 따라서 이미지를 신중하게 선택하십시오. 이미지의 크기가 가장 큰 것이 2000픽셀 이상인지 확인하십시오.

   이미지 집합에서 지원하는 형식 목록은 [Dynamic Media - 지원되는 래스터 이미지 형식](/help/assets/file-format-support.md#image-support-dynamic-media)을 참조하십시오.

1. [이미지 집합을 만듭니다](#creating-image-sets).

   이미지 세트에서 사용자는 이미지 세트 뷰어에서 썸네일 이미지를 클릭합니다.

   Assets에서 이미지 집합을 만들려면 **[!UICONTROL 만들기]** > **[!UICONTROL 이미지 집합]**&#x200B;을 선택합니다. 그런 다음 이미지를 추가하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   [파일 업로드 및 업로드를 위한 이미지 집합 자산 준비](#uploading-assets-in-image-sets)를 참조하십시오.

   [선택기를 사용하여 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하세요.

1. 필요에 따라 [이미지 집합 뷰어 사전 설정](/help/assets/dynamic-media/managing-viewer-presets.md)을 추가하십시오.

   관리자는 이미지 세트 뷰어 사전 설정을 만들거나 수정할 수 있습니다. 뷰어 사전 설정으로 이미지 집합을 보려면 이미지 집합을 선택하고 왼쪽 레일 드롭다운 목록에서 **[!UICONTROL 뷰어]**&#x200B;를 선택합니다.

   뷰어 사전 설정을 만들거나 편집하려면 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 뷰어 사전 설정]**&#x200B;을 참조하세요.

1. (선택 사항) 일괄처리 집합 사전 설정을 사용하여 만든 [이미지 집합 보기](/help/assets/dynamic-media/image-sets.md#viewing-image-sets).
1. [이미지 집합 미리 보기](/help/assets/dynamic-media/previewing-assets.md).

   이미지 세트를 선택하면 미리 볼 수 있습니다. 선택한 뷰어에서 이미지 세트를 검사하려면 축소판 아이콘을 선택합니다. 왼쪽 레일 드롭다운 목록에서 사용할 수 있는 **[!UICONTROL 뷰어]** 메뉴에서 다른 뷰어를 선택할 수 있습니다.

1. [이미지 집합 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   이미지 집합을 게시하면 URL 및 포함 문자열이 활성화됩니다. 또한 만든 사용자 지정 뷰어 사전 설정을 [게시](/help/assets/dynamic-media/managing-viewer-presets.md)해야 합니다. 즉시 사용 가능한 뷰어 사전 설정이 이미 게시되었습니다.

1. [웹 응용 프로그램에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 또는 [비디오 또는 이미지 뷰어를 포함](/help/assets/dynamic-media/embed-code.md).

   Experience Manager Assets은 이미지 세트에 대한 URL 호출을 생성하고 이미지 세트를 게시한 후 활성화합니다. 에셋을 미리 볼 때 이러한 URL을 복사할 수 있습니다. 또는 웹 사이트에 포함할 수 있습니다.

   이미지 집합을 선택한 다음 왼쪽 레일 드롭다운 목록에서 **[!UICONTROL 뷰어]**&#x200B;을(를) 선택합니다.

   [웹 페이지에 이미지 집합 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 및 [비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)을 참조하세요.

이미지 집합을 편집하려면 [이미지 집합 편집](#editing-image-sets)을 참조하세요. 또한 [이미지 집합 속성](/help/assets/manage-digital-assets.md#editing-properties)을 보고 편집할 수 있습니다.

집합을 만드는 데 문제가 있는 경우 [Dynamic Media 문제 해결](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets)에서 이미지 및 집합을 참조하십시오.

## 이미지 세트에 대한 자산 업로드 {#uploading-assets-in-image-sets}

이미지 세트에 대한 이미지 자산을 업로드하여 시작합니다. 사용자는 이미지 세트 뷰어에서 이미지를 확대할 수 있습니다. 따라서 이미지를 신중하게 선택하십시오. 최적의 확대/축소 세부 사항을 위해 이미지가 가장 큰 크기로 2000픽셀 이상인지 확인하십시오. Dynamic Media는 이미지를 각각 최대 2,500만 픽셀까지 렌더링할 수 있습니다. 예를 들어 5000x5000메가픽셀 이미지나 다른 모든 크기의 조합을 최대 2500메가픽셀까지 사용할 수 있습니다.

<!-- Image Sets supports many image file formats, but lossless TIFF, PNG, and EPS images are recommended. -->

이미지 집합에서 지원하는 형식 목록은 [Dynamic Media - 지원되는 래스터 이미지 형식](/help/assets/file-format-support.md#image-support-dynamic-media)을 참조하십시오.

[Assets의 다른 에셋을 업로드](/help/assets/manage-digital-assets.md#uploading-assets)하는 것처럼 이미지 집합에 대한 이미지를 업로드할 수 있습니다.

### 업로드할 이미지 세트 자산 준비 {#preparing-image-set-assets-for-upload}

이미지 세트를 만들기 전에 이미지의 크기와 형식이 올바른지 확인하십시오.

다중 뷰 이미지 집합을 만들려면 다른 POV의 항목을 표시하거나 동일한 항목의 다른 측면을 표시하는 이미지가 필요합니다. 목표는 항목의 중요한 기능을 강조 표시하여 뷰어가 항목의 모양 또는 기능에 대한 전체 그림을 볼 수 있도록 하는 것입니다.

사용자는 이미지 세트에서 이미지를 확대/축소할 수 있으므로 이미지의 크기가 가장 큰 것이 2000픽셀 이상인지 확인하십시오. Experience Manager Assets은 다양한 이미지 파일 형식을 지원하지만 손실 없는 TIFF, PNG 및 EPS 이미지가 권장됩니다.

>[!NOTE]
>
>썸네일을 사용하여 제품 견본을 나타내는 경우 다음을 수행합니다.
>
>동일한 이미지에 대해 서로 다른 색상, 패턴 또는 마무리로 비네팅 또는 다른 샷을 만듭니다. 다른 색상, 패턴 또는 마무리에 해당하는 축소판 파일도 필요합니다. 예를 들어 동일한 자켓을 검은색, 갈색 및 녹색으로 표시하는 이미지 세트와 함께 썸네일을 표시하려면 다음이 필요합니다.
>
>* 같은 재킷의 검정색, 갈색, 그리고 초록색 샷입니다.
>* 검정색, 갈색 및 녹색 썸네일.

## 이미지 집합 만들기 {#creating-image-sets}

사용자 인터페이스 또는 API를 통해 이미지 세트를 만들 수 있습니다.

>[!NOTE]
>
>[일괄처리 집합 사전 설정](/help/assets/dynamic-media/batch-set-presets-dm.md)을 통해 이미지 집합을 자동으로 만들 수도 있습니다.
>**중요:** 일괄 처리 집합은 자산 수집의 일부로 IPS(이미지 프로덕션 시스템)에 의해 만들어집니다.

세트에 자산을 추가하면 영숫자 순서로 자산이 자동으로 추가됩니다. 자산이 추가된 후 수동으로 순서를 변경하거나 정렬할 수 있습니다.

>[!NOTE]
>
>파일 이름에 &quot;,&quot;(쉼표)가 있는 자산은 이미지 세트가 지원되지 않습니다.

이미지 집합을 생성할 때 Adobe에서는 다음 모범 사례를 권장하며 다음 제한을 적용합니다.

| 제한 유형 | 모범 사례 | 제한 적용됨 |
| --- | --- | --- |
| 세트당 중복 에셋 수 | 중복 항목 없음 | 20 |
| 세트당 최대 이미지 수 | 세트당 5-10개 이미지 | 1000 |

[Dynamic Media 제한 사항](/help/assets/dynamic-media/limitations.md)도 참조하세요.

**이미지 집합을 만들려면:**

1. Adobe Experience Manager에서 Experience Manager 로고를 선택하여 전역 탐색 콘솔에 액세스합니다.
1. **[!UICONTROL 탐색]** > **[!UICONTROL Assets]**&#x200B;을 선택합니다. 이미지 집합을 만들 위치로 이동한 다음 **[!UICONTROL 만들기]** > **[!UICONTROL 이미지 집합]**(으)로 이동하여 이미지 집합 편집기 페이지를 엽니다.

   에셋이 포함된 폴더 내에서 세트를 만들 수도 있습니다.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. 이미지 집합 편집기 페이지의 **[!UICONTROL 제목]** 필드에 이미지 집합의 이름을 입력합니다. 이미지 세트의 배너에 이름이 표시됩니다. 설명을 입력합니다(선택적).

   ![6_5_imageset-creatingnewset](assets/6_5_imageset-creatingnewset.png)

1. 다음 중 하나를 수행합니다.

   * 이미지 집합 편집기 페이지의 왼쪽 상단 모서리 근처에서 **[!UICONTROL 자산 추가]**&#x200B;를 선택합니다.

   * 이미지 집합 편집기 페이지의 중간 부근에서 **[!UICONTROL 탭하여 자산 선택기를 엽니다]**.

   이미지 세트에 포함할 자산을 선택하려면 를 선택합니다. 선택한 에셋에는 확인 표시 아이콘이 있습니다. 완료되면 페이지의 오른쪽 상단 근처에서 **[!UICONTROL 선택]**&#x200B;을 선택합니다.

   자산 선택기를 사용하여 키워드를 입력하고 **[!UICONTROL 반환]**&#x200B;을 선택하여 자산을 검색할 수 있습니다. You can also apply filters to refine your search results. You can filter by path, collection, file type, and tag. 필터를 선택한 다음 도구 모음에서 **[!UICONTROL 필터]** 아이콘을 선택합니다. 보기 아이콘을 선택하고 **[!UICONTROL 열 보기]**, **[!UICONTROL 카드 보기]** 또는 **[!UICONTROL 목록 보기]**&#x200B;를 선택하여 보기를 변경합니다.

   [선택기를 사용하여 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하세요.

   ![6_5_imageset-addingassets](assets/6_5_imageset-addingassets.png)

1. 세트에 자산을 추가하면 영숫자 순서로 자산이 자동으로 추가됩니다. 에셋을 추가한 후 수동으로 에셋을 재정렬하거나 정렬할 수 있습니다.

   필요한 경우 에셋의 파일 이름 오른쪽에 에셋의 순서 변경 아이콘을 드래그하여 세트 목록의 위 또는 아래에 이미지 순서를 변경합니다.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   If you want to change a thumbnail or swatch, click the **+** **thumbnail** icon next to the image and navigate to the thumbnail or swatch you want. When done selecting all the images click **[!UICONTROL Save]**.

1. (선택 사항) 다음 중 하나를 수행합니다.

   * 이미지를 삭제하려면 이미지를 선택하고 **[!UICONTROL 자산 삭제]**&#x200B;를 선택합니다.

   * 페이지의 오른쪽 상단 모서리에서 사전 설정을 적용하려면 **[!UICONTROL 사전 설정]**&#x200B;을 선택한 다음 모든 에셋에 한 번에 적용할 사전 설정을 선택합니다.

   >[!NOTE]
   >
   >이미지 세트를 만들 때 이미지 세트 썸네일을 변경할 수 있습니다. 또는 Experience Manager에서 이미지 세트의 에셋에 따라 썸네일을 자동으로 선택하도록 할 수 있습니다. 썸네일을 선택하려면 이미지 집합 편집기 페이지의 제목 필드 위에서 **[!UICONTROL 썸네일 변경]**&#x200B;을 선택하십시오. 그런 다음 이미지를 선택합니다(다른 폴더로 이동하여 이미지를 찾을 수도 있음). 썸네일을 선택한 경우 Experience Manager에서 이미지 집합에서 썸네일을 생성하도록 결정한 다음 **[!UICONTROL 다음으로 전환]** **[!UICONTROL 자동 썸네일]**&#x200B;을 선택합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 이미지 세트를 만든 폴더에 이미지 세트가 나타납니다.

## 이미지 집합 보기 {#viewing-image-sets}

사용자 인터페이스에서 또는 [일괄처리 집합 사전 설정](/help/assets/dynamic-media/batch-set-presets-dm.md)을 사용하여 자동으로 이미지 집합을 만들 수 있습니다.

>[!IMPORTANT]
>
>자산 수집의 일부로 IPS [이미지 프로덕션 시스템]에서 일괄처리 집합을 만듭니다.

그러나 일괄처리 집합 사전 설정을 사용하여 만든 집합은 사용자 인터페이스에 나타나지 않습니다 *not*. 세 가지 방법으로 이러한 세트를 볼 수 있습니다. (이러한 메서드는 사용자 인터페이스에서 이미지 세트를 만든 경우에도 사용할 수 있습니다.)

* 에셋의 속성을 엽니다. 속성은 선택한 에셋이 참조되거나 의 멤버를 설정하는 항목을 나타냅니다. 전체 세트를 보려면 세트 이름을 선택합니다.

  ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties.png)

* From a member image of any set. **[!UICONTROL 집합]** 메뉴를 선택하여 자산이 구성원인 집합을 표시합니다.

  ![6_5_imageset-setspulldownmenu](assets/6_5_imageset-setspulldownmenu.png)

* 검색에서 **[!UICONTROL 필터]**&#x200B;를 선택한 다음 **[!UICONTROL Dynamic Media]**&#x200B;를 확장하고 **[!UICONTROL 설정]**&#x200B;을 선택할 수 있습니다.

  UI에서 수동으로 만들었거나 일괄처리 집합 사전 설정을 통해 자동으로 만든 일치 세트가 검색 결과에 반환됩니다. 자동화된 세트의 경우 &quot;다음으로 시작&quot;을 사용하여 검색 쿼리가 수행됩니다. 이 검색 기준은 &quot;포함&quot;을 사용하는 Experience Manager과 다릅니다. 필터를 **[!UICONTROL 집합]**(으)로 설정하는 것만이 자동화된 집합을 검색하는 유일한 방법입니다.

  ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>[이미지 집합 편집](#editing-image-sets)에 설명된 대로 사용자 인터페이스를 통해 집합을 볼 수 있습니다.

## 이미지 집합 편집 {#editing-image-sets}

이미지 세트에서 다음과 같은 다양한 편집 작업을 수행할 수 있습니다.

* 이미지 집합에 이미지를 추가합니다.
* 이미지 세트에서 이미지 순서를 변경합니다.
* 이미지 집합에서 자산을 삭제합니다.
* 뷰어 사전 설정을 적용합니다.
* 이미지 집합을 삭제합니다.

**이미지 집합을 편집하려면:**

1. 다음 중 하나를 수행합니다.

   * 이미지 집합 자산을 마우스로 가리킨 다음 **[!UICONTROL 편집]**(연필 아이콘)을 선택합니다.
   * 이미지 집합 자산을 마우스로 가리키고 **[!UICONTROL 선택]**(확인 표시 아이콘)을 선택한 다음 도구 모음에서 **[!UICONTROL 편집]**&#x200B;을 선택합니다.
   * 이미지 집합 에셋에서 을(를) 선택한 다음 도구 모음에서 **[!UICONTROL 편집]**(연필 아이콘)을 선택합니다.

1. 이미지 세트의 이미지를 편집하려면 다음 중 하나를 수행하십시오.

   * 에셋 순서를 변경하려면 이미지를 새 위치로 드래그합니다(항목을 이동하려면 순서 변경 아이콘을 선택합니다.).
   * 항목을 오름차순 또는 내림차순으로 정렬하려면 열 머리글을 클릭합니다.
   * 자산을 추가하거나 기존 자산을 업데이트하려면 **[!UICONTROL 자산 추가]**&#x200B;를 클릭하십시오. 자산으로 이동하여 선택한 다음 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 선택]**&#x200B;을 선택합니다.
     >[!NOTE]
     >
     >Experience Manager이 썸네일에 사용하는 이미지를 다른 이미지로 교체하여 삭제하면 원본 에셋이 계속 표시됩니다.
   * 자산을 삭제하려면 자산을 선택하고 **[!UICONTROL 자산 삭제]**&#x200B;를 선택합니다.
   * 사전 설정을 적용하려면 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 사전 설정]**&#x200B;을 선택한 다음 뷰어 사전 설정을 선택합니다.
   * 썸네일을 추가하거나 변경하려면 에셋 오른쪽 옆에 있는 썸네일 아이콘을 선택합니다. 새 썸네일 또는 견본 자산으로 이동하여 선택한 다음 **[!UICONTROL 선택]**&#x200B;을 선택합니다.
   * 전체 이미지 집합을 삭제하려면 이미지 집합으로 이동하여 선택한 다음 **[!UICONTROL 삭제]**&#x200B;를 선택합니다.

   >[!NOTE]
   >
   >이미지 세트에서 이미지를 편집할 수 있습니다. 집합으로 이동하고 왼쪽 레일에서 **[!UICONTROL 구성원 설정]**&#x200B;을 선택합니다. 편집 창을 열려면 에셋에서 연필 아이콘을 선택합니다.

1. 편집을 마치면 **[!UICONTROL 저장]**&#x200B;을(를) 선택합니다.

## 이미지 집합 미리 보기 {#previewing-image-sets}

[자산 미리 보기](/help/assets/dynamic-media/previewing-assets.md)를 참조하세요.

## 이미지 집합 게시 {#publishing-image-sets}

[Assets 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)를 참조하십시오.
