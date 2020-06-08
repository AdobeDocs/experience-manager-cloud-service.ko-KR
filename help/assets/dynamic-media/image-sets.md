---
title: 이미지 세트
description: Dynamic Media에서 이미지 세트로 작업하는 방법 살펴보기
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14
workflow-type: tm+mt
source-wordcount: '2049'
ht-degree: 0%

---


# 이미지 세트 {#image-sets}

이미지 세트는 사용자가 축소판 이미지를 클릭하여 항목의 다양한 보기를 볼 수 있는 통합 보기 환경을 제공합니다. 이미지 세트를 사용하면 항목의 대체 보기를 표시할 수 있으며 뷰어에서는 이미지를 면밀하게 검사할 수 있는 확대/축소 도구를 제공합니다.

이미지 세트는 단어가 포함된 배너에 의해 지정됩니다 `IMAGESET`. 또한 이미지 세트가 게시되는 경우 **[!UICONTROL 월드]** 아이콘으로 표시된 게시 날짜가 마지막 수정 날짜와 함께 배너에 **[!UICONTROL 연필]** 아이콘으로 표시됩니다.

![chlimage_1-133](assets/chlimage_1-339.png)

이미지 세트 내에서 이미지 세트를 만들고 축소판을 추가하여 견본을 만들 수도 있습니다.

이 응용 프로그램은 항목을 다른 색상, 패턴 또는 마무리로 표시하려는 경우에 특히 유용합니다. 색상 견본을 사용하여 이미지 세트를 만들려면 사용자에게 보여줄 각 색상, 패턴 또는 마무리에 대해 하나의 이미지가 필요합니다. 또한 각 색상, 패턴 또는 마무리에 대해 하나의 색상, 패턴 또는 마무리 견본이 필요합니다.

예를 들어 서로 다른 색상 BOM을 가진 대문자용 이미지를 제공하려는 경우 지폐는 빨강, 녹색 그리고 파란색입니다. 이 경우 동일한 캡의 샷이 3개 필요합니다. 빨간색, 녹색, 파란색 계산서가 필요합니다. 또한 빨강, 녹색 및 파랑 색상 견본이 필요합니다. 색상 견본은 색상 견본 집합 뷰어에서 사용자가 빨간색으로 청구되거나 녹색 청구되거나 파란색으로 청구되는 캡을 보기 위해 클릭하는 축소판으로 사용됩니다.

>[!NOTE]
>
>자산 사용자 인터페이스에 대한 자세한 내용은 터치 UI를 사용하여 [자산 관리를 참조하십시오](/help/assets/manage-digital-assets.md).

## 빠른 시작: 이미지 세트 {#quick-start-image-sets}

빠르게 시작하기

1. [여러 뷰에 대한 마스터 이미지를 업로드합니다.](#uploading-assets-in-image-sets)

   먼저 이미지 세트에 대한 이미지를 업로드합니다. 이미지 세트 뷰어에서 이미지를 확대/축소할 수 있으므로 이미지를 선택할 때 확대/축소를 고려합니다. 이미지의 크기가 가장 큰 경우 2000픽셀 이상이어야 합니다. AEM Assets는 많은 이미지 파일 포맷을 지원하지만 손실 없는 TIFF, PNG 및 EPS 이미지가 권장됩니다.

1. [이미지 세트 만들기를 참조하십시오.](#creating-image-sets)

   이미지 세트에서 사용자는 이미지 세트 뷰어에서 축소판 이미지를 클릭합니다.

   자산에 이미지 세트를 만들려면 만들기 > 이미지 세트 **[!UICONTROL 를 탭하거나 클릭합니다]**. 이미지를 추가하고 저장을 **[!UICONTROL 클릭합니다]**.

   또한 [일괄 세트 사전 설정을 통해 자동으로 이미지 세트를 만들 수도 있습니다](/help/assets/dynamic-media/config-dm.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

   >[!IMPORTANT]
   >
   >배치 세트는 자산 수정의 일부로 IPS(Image Production System)에 의해 만들어집니다.

   파일 [업로드 및 업로드를 위한 이미지 세트 자산 준비를 참조하십시오](#uploading-assets-in-image-sets).

   See [Working with Selectors.](/help/assets/dynamic-media/working-with-selectors.md)

1. 필요에 따라 [이미지 세트 뷰어 사전](/help/assets/dynamic-media/managing-viewer-presets.md)설정을 추가합니다.

   관리자는 이미지 세트 뷰어 사전 설정을 만들거나 수정할 수 있습니다. 뷰어 사전 설정으로 이미지 세트를 보려면 이미지 세트를 선택하고 왼쪽 레일 드롭다운 메뉴에서 **[!UICONTROL 뷰어를 선택합니다]**.

   뷰어 **[!UICONTROL 사전 설정을 만들거나 편집하려면 도구 > 자산 > 뷰어 사전]** 설정을 참조하십시오.

1. (선택 사항) [일괄 세트 사전 설정을 사용하여 만든](/help/assets/dynamic-media/image-sets.md#viewing-image-sets) 이미지 세트 보기
1. [이미지 세트 미리 보기를 참조하십시오.](/help/assets/dynamic-media/previewing-assets.md)

   이미지 세트를 선택하면 미리 볼 수 있습니다. 축소판 아이콘을 클릭하여 선택한 뷰어에서 이미지 세트를 검사합니다. 왼쪽 레일 드롭다운 메뉴에서 **[!UICONTROL 뷰어]** 메뉴에서 다른 뷰어를 선택할 수 있습니다.

1. [이미지 세트 게시를 참조하십시오.](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

   이미지 세트를 게시하면 URL 및 포함 문자열이 활성화됩니다. 또한 만든 사용자 정의 뷰어 사전 [설정을](/help/assets/dynamic-media/managing-viewer-presets.md) 게시해야 합니다. 최신 뷰어 사전 설정이 이미 게시되었습니다.

1. [웹 응용 프로그램에 URL을 연결하거나 비디오 또는 이미지 뷰어](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)[를 포함합니다](/help/assets/dynamic-media/embed-code.md).

   AEM Assets는 이미지 세트에 대한 URL 호출을 만들고 이미지 세트를 게시한 후 활성화합니다. 자산을 미리 볼 때 이러한 URL을 복사할 수 있습니다. 또는 웹 사이트에 포함할 수 있습니다.

   이미지 세트를 선택한 다음 왼쪽 레일 드롭다운 메뉴에서 뷰어를 **[!UICONTROL 선택합니다]**.

   이미지 [세트를 웹 페이지에 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 및 [비디오 또는 이미지 뷰어 포함을 참조하십시오](/help/assets/dynamic-media/embed-code.md).

이미지 세트를 편집하려면 이미지 세트 [편집을 참조하십시오.](#editing-image-sets) 또한 [이미지 세트 속성을 보고 편집할 수도 있습니다](/help/assets/manage-digital-assets.md#editing-properties).

세트를 만드는 데 문제가 있으면 다이내믹 미디어 문제 해결에서 이미지 및 [세트를 참조하십시오](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets).

## 이미지 세트에 자산 업로드 {#uploading-assets-in-image-sets}

먼저 이미지 세트에 대한 이미지를 업로드합니다. 이미지 세트 뷰어에서 이미지를 확대/축소할 수 있으므로 이미지를 선택할 때 확대/축소를 고려합니다. 확대/축소 세부 사항을 최적화하려면 이미지가 가장 큰 차원에서 2000픽셀 이상이어야 합니다. Dynamic Media는 각 이미지를 최대 25메가픽셀까지 렌더링할 수 있습니다. 예를 들어 5000 x 5000메가픽셀 이미지 또는 최대 25메가픽셀의 기타 크기 조합을 사용할 수 있습니다.

이미지 세트는 많은 이미지 파일 포맷을 지원하지만 손실 없는 TIFF, PNG 및 EPS 이미지가 권장됩니다.

Assets의 다른 자산을 [업로드하듯이 이미지 세트에 대한 이미지를 업로드할 수 있습니다](/help/assets/manage-digital-assets.md#uploading-assets).

### 업로드할 이미지 세트 자산 준비 {#preparing-image-set-assets-for-upload}

이미지 세트를 만들기 전에 이미지의 크기와 형식이 올바른지 확인하십시오.

다중 보기 이미지 세트를 만들려면 다른 보기 지점에서 항목을 표시하거나 동일한 항목의 다른 측면을 표시하는 이미지가 필요합니다. 이 제품의 주요 기능을 강조 표시하여 사용자가 실제로 어떤 모습인지 완벽하게 파악할 수 있도록 합니다.

사용자가 이미지 세트에서 이미지를 확대/축소할 수 있으므로 이미지 크기가 가장 큰 2,000픽셀 이상인지 확인하십시오. 에셋은 많은 이미지 파일 포맷을 지원하지만 손실 없는 TIFF, PNG 및 EPS 이미지가 권장됩니다.

>[!NOTE]
>
>제품 견본을 나타내기 위해 축소판을 사용하는 경우에도 다음을 수행해야 합니다.
>
>비네팅 또는 동일한 이미지의 다른 샷이 서로 다른 색상, 패턴 또는 마무리로 표시되어야 합니다. 또한 다른 색상, 패턴 또는 마무리에 해당하는 축소판 파일도 필요합니다. 예를 들어, 동일한 자켓을 검정색, 갈색 및 녹색으로 표시하는 이미지 세트로 축소판을 표시하려면 다음을 수행해야 합니다.
>
>* 같은 재킷의 검정색, 갈색, 그린 샷.
>* 검정, 갈색 및 녹색 색상 축소판


## 이미지 세트 만들기 {#creating-image-sets}

사용자 인터페이스 또는 API를 통해 이미지 세트를 만들 수 있습니다. 이 섹션에서는 UI에서 이미지 세트를 만드는 방법에 대해 설명합니다.

>[!NOTE]
>
>또한 [일괄 세트 사전 설정을 통해 자동으로 이미지 세트를 만들 수도 있습니다](/help/assets/dynamic-media/config-dm.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).
>**중요:**배치 세트는 자산 수정의 일부로 IPS(Image Production System)에 의해 만들어집니다.

세트에 자산을 추가하면 자동으로 영숫자 순서로 추가됩니다. 자산을 추가한 후에 수동으로 다시 정렬하거나 정렬할 수 있습니다.

>[!NOTE]
>
>이미지 세트는 파일 이름에 &quot;,&quot;(쉼표)가 있는 자산에 대해 지원되지 않습니다.

**이미지 세트를 만들려면**

1. AEM에서 AEM 로고를 눌러 글로벌 탐색 콘솔에 액세스한 다음 **[!UICONTROL 탐색 > 자산을 탭합니다]**. 이미지 세트를 만들 위치로 이동한 다음 **[!UICONTROL 만들기 > 이미지 세트를]** 눌러 이미지 세트 편집기 페이지를 엽니다.

   에셋이 포함된 폴더 내에서 세트를 만들 수도 있습니다.

   ![6_5_imagesets-createplldown](assets/6_5_imagesets-createpulldown.png)

1. 이미지 세트 편집기 페이지의 **[!UICONTROL 제목]** 필드에 이미지 세트의 이름을 입력합니다. 이미지 세트의 배너에 이름이 나타납니다. 설명을 입력합니다(선택적).

   ![6_5_imageset-creatingnewset](assets/6_5_imageset-creatingnewset.png)

1. 다음 중 하나를 수행합니다.

   * 이미지 세트 편집기 페이지의 왼쪽 위 모서리 근처에 있는 자산 **[!UICONTROL 추가를 누릅니다]**.

   * 이미지 세트 편집기 페이지의 중간 근처에 있는 탭 **[!UICONTROL 을 눌러 자산 선택기를 엽니다]**.
   이미지 세트에 포함할 자산을 선택하려면 을 누릅니다. 선택한 자산에 확인 표시 아이콘이 표시됩니다. 완료되면 페이지의 오른쪽 위 모서리 근처에 있는 선택을 **[!UICONTROL 누릅니다]**.

   자산 선택기를 사용하여 키워드를 입력하고 재시작을 탭하거나 클릭하여 자산을 검색할 수 **[!UICONTROL 있습니다]**. 필터를 적용하여 검색 결과를 조정할 수도 있습니다. 경로, 컬렉션, 파일 유형 및 태그별로 필터링할 수 있습니다. 필터를 선택한 다음 도구 모음에서 **[!UICONTROL 필터]** 아이콘을 누릅니다. 보기 아이콘을 누르고 열 보기, 카드 보기 **[!UICONTROL 또는 목록 보기]**&#x200B;를 선택하여 보기 **[!UICONTROL 를]**&#x200B;변경합니다 ****.

   See [Working with Selectors.](/help/assets/dynamic-media/working-with-selectors.md)

   ![6_5_imageset-addingassets](assets/6_5_imageset-addingassets.png)

1. 세트에 자산을 추가하면 자동으로 영숫자 순서로 추가됩니다. 자산을 추가한 후 자산을 수동으로 다시 정렬하거나 정렬할 수 있습니다.

   필요한 경우 자산의 순서 변경 아이콘을 자산 파일 이름의 오른쪽으로 드래그하여 이미지 순서를 설정 목록의 위나 아래로 변경합니다.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   축소판 또는 견본을 변경하려면 이미지 옆에 있는 **+** **축소판** 아이콘을 클릭하고 원하는 축소판 또는 견본을 탐색합니다. 모든 이미지 선택이 완료되면 [저장]을 **[!UICONTROL 클릭합니다]**.

1. (선택 사항) 다음 중 하나를 수행합니다.

   * 이미지를 삭제하려면 이미지를 선택하고 자산 **[!UICONTROL 삭제를 누릅니다]**.

   * 사전 설정을 적용하려면 페이지의 오른쪽 위 모서리 근처에 있는 사전 **[!UICONTROL 설정을]**&#x200B;누른 다음 사전 설정을 선택하여 모든 자산에 한 번에 적용할 수 있습니다.
   >[!NOTE]
   >
   >이미지 세트를 만들 때 이미지 세트 축소판을 변경하거나 AEM에서 이미지 세트의 자산을 기반으로 축소판을 자동으로 선택하도록 허용할 수 있습니다. 축소판을 선택하려면 이미지 세트 편집기 **[!UICONTROL 페이지의 제목 필드]** 위에 있는 축소판 변경을 누른 다음 이미지를 선택합니다. 다른 폴더로 이동하여 이미지를 찾을 수도 있습니다. 축소판을 선택한 다음 AEM에서 이미지 세트에서 축소판을 생성하도록 선택한 경우 **[!UICONTROL 자동 축소판으로]** **[!UICONTROL 전환을 선택합니다]**.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 새로 만든 이미지 세트가 만든 폴더에 나타납니다.

## 이미지 세트 보기 {#viewing-image-sets}

사용자 인터페이스에서 또는 [일괄 세트 사전 설정을 사용하여 자동으로 이미지 세트를 만들 수 있습니다](/help/assets/dynamic-media/config-dm.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

>[!IMPORTANT]
>
>배치 세트는 자산 수정의 일부로 IPS [Image Production] System에 의해 만들어집니다.

하지만 배치 집합 사전 설정을 사용하여 만든 세트는 사용자 인터페이스에 *나타나지 않습니다* . 이러한 세트는 세 가지 방법으로 볼 수 있습니다. (사용자 인터페이스에서 이미지 세트를 만든 경우에도 이러한 방법을 사용할 수 있습니다.)

* 개별 자산의 속성을 엽니다. 속성은 선택한 자산이 참조되는 세트 또는 그 구성원을 나타냅니다. 전체 세트를 보려면 세트 이름을 클릭합니다.

   ![6_5_imageset-assets 속성](assets/6_5_imageset-assetproperties.png)

* 모든 세트의 멤버 이미지에서 자산이 속하는 세트를 표시하려면 **[!UICONTROL** 세트 메뉴]를 선택합니다.

   ![6_5_imageset-setspulldownmenu](assets/6_5_imageset-setspulldownmenu.png)

* 검색에서 **[!UICONTROL 필터**]를 선택한 다음 **[!UICONTROL Dynamic Media** 를 확장하고 **[!UICONTROL 세트를 선택할 수 있습니다]**.

   검색은 UI에서 수동으로 만들거나 배치 집합 사전 설정을 통해 자동으로 생성된 일치 집합을 반환합니다. 자동화된 세트의 경우 &quot;포함&quot; 검색 기준을 사용하는 AEM 검색과는 다른 &quot;다음으로 시작&quot; 검색 조건을 사용하여 검색 쿼리를 수행합니다. 필터를 **[!UICONTROL 세트로]** 설정하면 자동화된 세트를 검색할 수 있습니다.

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>이미지 세트 [편집에 설명된 대로 사용자 인터페이스를 통해 세트를 볼 수 있습니다](#editing-image-sets).

## 이미지 세트 편집 {#editing-image-sets}

다음과 같이 이미지 세트에서 다양한 편집 작업을 수행할 수 있습니다.

* 이미지 세트에 이미지를 추가합니다.
* 이미지 세트에서 이미지 순서를 변경합니다.
* 이미지 세트에서 자산을 삭제합니다.
* 뷰어 사전 설정을 적용합니다.
* 이미지 세트를 삭제합니다.

**이미지 세트를 편집하려면**

1. 다음 중 하나를 수행합니다.

   * 이미지 세트 에셋을 마우스로 가리킨 다음 **[!UICONTROL 편집]** (연필 아이콘)을 누릅니다.
   * 이미지 세트 자산 위로 마우스를 가져간 다음 **[!UICONTROL 선택]** (확인 표시 아이콘)을 누른 다음 도구 모음에서 **[!UICONTROL 편집을]** 탭합니다.
   * 이미지 세트 자산을 누른 다음 도구 모음에서 **[!UICONTROL 편집]** (연필 아이콘)을 누릅니다.

1. 이미지 세트에서 이미지를 편집하려면 다음 중 하나를 수행합니다.

   * 자산의 순서를 바꾸려면 이미지를 새 위치로 드래그합니다(항목을 이동하려면 순서 변경 아이콘 선택).
   * 항목을 오름차순 또는 내림차순으로 정렬하려면 열 제목을 클릭합니다.
   * 자산을 추가하거나 기존 자산을 업데이트하려면 자산 **[!UICONTROL 추가를 클릭합니다]**. 자산으로 이동하여 선택한 다음 페이지의 오른쪽 위 모서리 **[!UICONTROL 근처에 있는 선택을]** 누릅니다.

      >[!NOTE]
      >
      >AEM에서 축소판에서 사용하는 이미지를 다른 이미지로 대체하여 삭제하면 원래 자산이 계속 표시됩니다.
   * 자산을 삭제하려면 해당 자산을 선택하고 자산 **[!UICONTROL 삭제를 탭하거나 클릭합니다]**.
   * 사전 설정을 적용하려면 페이지의 오른쪽 위 모서리 근처에 있는 사전 설정을 **[!UICONTROL 누른]**&#x200B;다음 뷰어 사전 설정을 선택합니다.
   * 축소판을 추가하거나 변경하려면 자산의 오른쪽 옆에 있는 축소판 아이콘을 선택합니다. 새로운 축소판 또는 견본 에셋으로 이동하여 선택한 다음 선택을 **[!UICONTROL 누릅니다]**.
   * 전체 이미지 세트를 삭제하려면 이미지 세트로 이동하고 선택한 다음 **[!UICONTROL 삭제를 누릅니다]**.

   >[!NOTE]
   >
   >세트로 이동하여 왼쪽 레일에서 멤버 **** 설정을 누른 다음 개별 자산의 연필 아이콘을 눌러 편집 창을 열면 이미지 세트의 이미지를 편집할 수 있습니다.

1. 편집을 **[!UICONTROL 마치면 저장을]** 누릅니다.

## 이미지 세트 미리 보기 {#previewing-image-sets}

자산 [미리 보기를 참조하십시오](/help/assets/dynamic-media/previewing-assets.md).

## 이미지 세트 게시 {#publishing-image-sets}

자산 [게시를 참조하십시오](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
