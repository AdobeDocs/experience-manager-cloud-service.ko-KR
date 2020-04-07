---
title: 이미지 세트
description: Dynamic Media에서 이미지 세트로 작업하는 방법 살펴보기
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# 이미지 세트 {#image-sets}

이미지 세트는 사용자가 축소판 이미지를 클릭하여 항목의 다른 보기를 볼 수 있는 통합된 보기 환경을 제공합니다. 이미지 집합을 사용하면 항목의 대체 보기를 표시할 수 있고 뷰어는 이미지를 자세히 검사하는 확대/축소 도구를 제공합니다.

이미지 세트는 단어가 포함된 배너에 의해 `IMAGESET`지정됩니다. 또한 이미지 세트가 게시되면 마지막 수정 **[!UICONTROL 날짜와 함께 배너에 World]** 아이콘으로 표시된 게시 날짜가 **[!UICONTROL 연필]** 아이콘으로표시됩니다.

![chlimage_1-133](assets/chlimage_1-339.png)

이미지 세트 내에서 이미지 세트를 만들고 축소판을 추가하여 견본을 만들 수도 있습니다.

이 응용 프로그램은 항목을 다른 색상, 패턴 또는 마무리로 표시하려는 경우에 특히 유용합니다. 색상 견본을 사용하여 이미지 세트를 만들려면 사용자에게 제공할 각 색상, 패턴 또는 마무리에 대해 하나의 이미지가 필요합니다. 또한 각 색상, 패턴 또는 마무리에 대해 하나의 색상, 패턴 또는 완성 견본이 필요합니다.

예를 들어 서로 다른 색상 BOM을 가진 대문자표 이미지를 제공하려는 경우청구서는 빨강, 녹색, 파랑입니다. 이 경우 동일한 캡의 샷을 세 개 선택해야 합니다. 하나는 빨간색이고 하나는 녹색이고 하나는 파란색이에요 또한 빨간색, 녹색 및 파란색 색상 견본이 필요합니다. 색상 견본은 사용자가 견본 집합 뷰어에서 클릭하여 빨간색 청구, 녹색 청구 또는 파란색의 청구 단락을 보는 축소판으로 사용됩니다.

>[!NOTE]
>
>자산 사용자 인터페이스에 대한 자세한 내용은 터치 UI를 [사용하여 자산 관리를 참조하십시오](/help/assets/manage-digital-assets.md).

## 빠른 시작:이미지 세트 {#quick-start-image-sets}

빠르게 시작하기 위해:

1. [마스터 이미지를 업로드하여 여러 뷰를 볼 수 있습니다.](#uploading-assets-in-image-sets)

   먼저 이미지 세트에 대한 이미지를 업로드합니다. 사용자는 이미지 세트 뷰어에서 이미지를 확대할 수 있으므로 이미지를 선택할 때 확대/축소를 고려합니다. 이미지의 크기가 가장 큰 경우 2000픽셀 이상이어야 합니다. AEM Assets는 많은 이미지 파일 형식을 지원하지만 손실 없는 TIFF, PNG 및 EPS 이미지가 권장됩니다.

1. [이미지 세트 만들기를 참조하십시오.](#creating-image-sets)

   [이미지 세트]에서 사용자는 이미지 세트 뷰어에서 축소판 이미지를 클릭합니다.

   자산에서 이미지 세트를 만들려면 만들기 > 이미지 **[!UICONTROL 세트를 탭하거나 클릭합니다]**. 이미지를 추가하고 저장을 **[!UICONTROL 클릭합니다]**.

   또한 [일괄 처리 집합 사전 설정을](/help/assets/dynamic-media/config-dm.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)통해 자동으로 이미지 집합을 만들 수 있습니다.

   >[!IMPORTANT]
   >
   >일괄 세트는 자산 수집의 일부로 IPS(Image Production System)에 의해 생성됩니다.

   업로드할 [이미지 세트 자산 준비 및 파일](#uploading-assets-in-image-sets)업로드를 참조하십시오.

   See [Working with Selectors.](/help/assets/dynamic-media/working-with-selectors.md)

1. 필요에 [따라 이미지 집합 뷰어 사전 설정을](/help/assets/dynamic-media/managing-viewer-presets.md)추가합니다.

   관리자는 이미지 집합 뷰어 사전 설정을 만들거나 수정할 수 있습니다. 뷰어 사전 설정으로 이미지 세트를 보려면 이미지 세트를 선택하고 왼쪽 레일 드롭다운 메뉴에서 뷰어를 **[!UICONTROL 선택합니다]**.

   뷰어 **[!UICONTROL 사전 설정을 만들거나 편집하려면 도구 > 자산]** > 뷰어 사전 설정을 참조하십시오.

1. (선택 사항) [일괄](/help/assets/dynamic-media/image-sets.md#viewing-image-sets) 세트 사전 설정을 사용하여 만든 이미지 세트 보기
1. [이미지 세트 미리 보기를 참조하십시오.](/help/assets/dynamic-media/previewing-assets.md)

   이미지 세트를 선택하면 미리 볼 수 있습니다. 축소판 아이콘을 클릭하여 선택한 뷰어에서 이미지 세트를 검사합니다. 왼쪽 레일 드롭다운 메뉴에서 **[!UICONTROL [뷰어]** ] 메뉴에서 다른 뷰어를 선택할 수 있습니다.

1. [이미지 세트 게시를 참조하십시오.](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

   이미지 세트 게시를 사용하면 URL 및 포함 문자열이 활성화됩니다. 또한 만든 사용자 정의 뷰어 사전 설정을 [게시해야](/help/assets/dynamic-media/managing-viewer-presets.md) 합니다. 즉시 사용 가능한 뷰어 사전 설정이 이미 게시되었습니다.

1. [웹 응용 프로그램에 URL을 연결하거나 비디오](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 또는 [이미지 뷰어를 포함합니다](/help/assets/dynamic-media/embed-code.md).

   AEM Assets는 이미지 세트에 대한 URL 호출을 만들고 이미지 세트를 게시한 후 활성화합니다. 자산을 미리 볼 때 이러한 URL을 복사할 수 있습니다. 또는 웹 사이트에 포함할 수 있습니다.

   이미지 세트를 선택한 다음 왼쪽 레일 드롭다운 메뉴에서 뷰어를 **[!UICONTROL 선택합니다]**.

   이미지 [세트를 웹 페이지에](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 연결 및 비디오 또는 이미지 [뷰어 포함을 참조하십시오](/help/assets/dynamic-media/embed-code.md).

이미지 세트를 편집하려면 이미지 세트 [편집을 참조하십시오.](#editing-image-sets) 또한 이미지 세트 속성을 보고 편집할 [수](/help/assets/manage-digital-assets.md#editing-properties)있습니다.

세트를 만드는 데 문제가 있는 경우 다이내믹 미디어 문제 해결의 이미지 및 [세트를 참조하십시오](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets).

## 이미지 세트에서 자산 업로드 {#uploading-assets-in-image-sets}

먼저 이미지 세트에 대한 이미지를 업로드합니다. 사용자는 이미지 세트 뷰어에서 이미지를 확대할 수 있으므로 이미지를 선택할 때 확대/축소를 고려합니다. 최적의 확대/축소 세부 사항을 위해 이미지가 가장 큰 차원에서 2000픽셀 이상인지 확인합니다. Dynamic Media는 각 이미지를 최대 25메가픽셀의 이미지로 렌더링할 수 있습니다. 예를 들어 5000 x 5000메가픽셀 이미지 또는 최대 25메가픽셀 크기의 기타 모든 크기 조합을 사용할 수 있습니다.

이미지 세트는 많은 이미지 파일 형식을 지원하지만 손실 없는 TIFF, PNG 및 EPS 이미지가 권장됩니다.

자산에서 다른 자산을 [업로드하듯이 이미지 세트에 대한 이미지를 업로드할 수 있습니다](/help/assets/manage-digital-assets.md#uploading-assets).

### 업로드할 이미지 집합 자산 준비 {#preparing-image-set-assets-for-upload}

이미지 세트를 만들기 전에 이미지의 크기와 형식이 올바른지 확인하십시오.

다중 보기 이미지 세트를 만들려면 다른 보기 지점의 항목을 표시하거나 동일한 항목의 여러 측면을 표시하는 이미지가 필요합니다. 이 프로그램의 목표는 사용자가 항목의 모양과 기능을 완벽하게 파악할 수 있도록 항목의 중요한 기능을 강조하는 것입니다.

사용자가 이미지 세트에서 이미지를 확대/축소할 수 있으므로 이미지 크기가 가장 큰 2,000픽셀 이상인지 확인하십시오. 에셋은 많은 이미지 파일 형식을 지원하지만 손실 없는 TIFF, PNG 및 EPS 이미지가 권장됩니다.

>[!NOTE]
>
>또한 축소판을 사용하여 제품 견본을 나타내는 경우 다음을 수행해야 합니다.
>
>비네팅 또는 동일한 이미지의 다른 샷이 다른 색상, 패턴 또는 마무리로 표시됩니다. 또한 다른 색상, 패턴 또는 마무리에 해당하는 축소판 파일도 필요합니다. 예를 들어, 동일한 자켓을 검정색, 갈색 및 녹색으로 표시하는 이미지 세트와 함께 축소판을 표시하려면 다음을 수행해야 합니다.
>
>* 같은 재킷의 검정색, 갈색, 녹색 샷
>* 검정색, 갈색 및 녹색 색상 축소판


## 이미지 세트 만들기 {#creating-image-sets}

사용자 인터페이스 또는 API를 통해 이미지 세트를 만들 수 있습니다. 이 섹션에서는 UI 파섹

>[!NOTE]
>
>또한 [일괄 처리 집합 사전 설정을](/help/assets/dynamic-media/config-dm.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)통해 자동으로 이미지 집합을 만들 수 있습니다.
>**중요:**일괄 세트는 자산 수집의 일부로 IPS(Image Production System)에 의해 생성됩니다.

세트에 자산을 추가하면 자동으로 영숫자 순서로 추가됩니다. 자산을 추가한 후 수동으로 다시 정렬하거나 정렬할 수 있습니다.

>[!NOTE]
>
>이미지 세트는 파일 이름에 &quot;,&quot;(쉼표)가 있는 자산에 대해 지원되지 않습니다.

**이미지 세트를 만들려면**

1. AEM 파섹 **** 이미지 세트를 만들 위치로 이동한 다음 만들기 > 이미지 **[!UICONTROL 세트를 눌러]** 이미지 세트 편집기 페이지를 엽니다.

   에셋이 포함된 폴더 내에서 세트를 만들 수도 있습니다.

   ![6_5_imagesets-createfulldown](assets/6_5_imagesets-createpulldown.png)

1. 이미지 세트 편집기 페이지의 제목 **[!UICONTROL 필드에]** 이미지 세트의 이름을 입력합니다. 이름이 이미지 세트의 배너에 표시됩니다. 설명을 입력합니다(선택적).

   ![6_5_imageset-creatingnewset](assets/6_5_imageset-creatingnewset.png)

1. 다음 중 하나를 수행합니다.

   * 이미지 세트 편집기 페이지의 왼쪽 위 모서리 근처에 있는 자산 **[!UICONTROL 추가를 누릅니다]**.

   * 이미지 세트 편집기 페이지의 중간에 있는 탭하여 자산 **[!UICONTROL 선택기를 엽니다]**.
   을 눌러 이미지 세트에 포함할 자산을 선택합니다. 선택한 자산에 확인 표시 아이콘이 표시됩니다. 완료되면 페이지의 오른쪽 위 모서리 근처에서 선택을 **[!UICONTROL 누릅니다]**.

   자산 선택기를 사용하면 키워드를 입력하고 재시작을 탭하거나 클릭하여 자산을 검색할 수 **[!UICONTROL 있습니다]**. 필터를 적용하여 검색 결과를 조정할 수도 있습니다. 경로, 컬렉션, 파일 유형 및 태그별로 필터링할 수 있습니다. 필터를 선택한 다음 도구 모음에서 **[!UICONTROL 필터]** 아이콘을 누릅니다. 보기 아이콘을 누르고 열 보기, 카드 보기 **[!UICONTROL 또는 목록 보기를]**&#x200B;선택하여 **[!UICONTROL 보기를]******&#x200B;변경합니다.

   See [Working with Selectors.](/help/assets/dynamic-media/working-with-selectors.md)

   ![6_5_imageset-addingassets](assets/6_5_imageset-addingassets.png)

1. 세트에 자산을 추가하면 자동으로 영숫자 순서로 추가됩니다. 에셋을 추가한 후 수동으로 다시 정렬하거나 정렬할 수 있습니다.

   필요한 경우 자산의 순서 변경 아이콘을 자산의 파일 이름 오른쪽에 드래그하여 이미지 순서를 설정 목록에서 위나 아래로 변경합니다.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   축소판이나 견본을 변경하려면 이미지 옆에 있는 **+** **축소판** 아이콘을 클릭하고 원하는 축소판이나 견본으로 이동합니다. 모든 이미지 선택이 완료되면 저장을 **[!UICONTROL 클릭합니다]**.

1. (선택 사항) 다음 중 하나를 수행합니다.

   * 이미지를 삭제하려면 이미지를 선택하고 자산 **[!UICONTROL 삭제를 누릅니다]**.

   * 사전 설정을 적용하려면 페이지의 오른쪽 위 모서리 근처에 있는 사전 설정을 누른 **[!UICONTROL 다음]**&#x200B;사전 설정을 선택하여 모든 자산에 한 번에 적용할 수 있습니다.
   >[!NOTE]
   >
   >이미지 세트를 만들 때 이미지 세트 축소판을 변경하거나 AEM에서 이미지 세트의 자산을 기반으로 축소판을 자동으로 선택하도록 할 수 있습니다. 축소판을 선택하려면 이미지 **[!UICONTROL 세트 편집기 페이지의 제목 필드 위에 있는 축소판]** 변경을 누른 다음 원하는 이미지를 선택합니다. 다른 폴더로 이동하여 이미지를 찾을 수도 있습니다. 축소판을 선택한 다음 AEM에서 이미지 세트에서 축소판을 생성하도록 결정한 경우 자동 축소판으로 **[!UICONTROL 전환을]** 선택합니다 ****.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 새로 만든 이미지 세트가 만든 폴더에 나타납니다.

## 이미지 세트 보기 {#viewing-image-sets}

사용자 인터페이스에서 또는 [일괄 세트 사전 설정을](/help/assets/dynamic-media/config-dm.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)사용하여 자동으로 이미지 세트를 만들 수 있습니다.

>[!IMPORTANT]
>
>일괄 세트는 자산 수집의 [일부로 IPS] 이미지 제작 시스템에 의해 만들어집니다.

하지만 배치 집합 사전 설정을 사용하여 만든 세트는 사용자 인터페이스에 *나타나지 않습니다* . 이러한 세트는 세 가지 방법으로 볼 수 있습니다. (사용자 인터페이스에서 이미지 세트를 만든 경우에도 이러한 방법을 사용할 수 있습니다.)

* 개별 자산의 속성을 엽니다. 속성은 선택한 자산이 참조되는 세트 또는 의 구성원을 나타냅니다. 세트 이름을 클릭하여 전체 세트를 봅니다.

   ![6_5_imageset-assets 속성](assets/6_5_imageset-assetproperties.png)

* 세트의 멤버 이미지에서 자산이 속하는 세트를 표시하려면 **[!UICONTROL** 세트] 메뉴를 선택합니다.

   ![6_5_imageset-setspulldownmenu](assets/6_5_imageset-setspulldownmenu.png)

* 검색에서 **[!UICONTROL 필터]를 선택한 다음****[!UICONTROL Dynamic Media를 확장하고** 세트를 선택할 수 **[!UICONTROL 있습니다]**.

   검색은 UI에서 수동으로 만들었거나 일괄 세트 사전 설정을 통해 자동으로 생성된 일치 세트를 반환합니다. 자동화된 세트의 경우 &quot;포함&quot; 검색 조건을 사용하는 AEM 검색과는 다른 &quot;다음으로 시작&quot; 검색 조건을 사용하여 검색 쿼리를 수행합니다. 필터를 세트로 설정하는 **[!UICONTROL 것은]** 자동화된 세트를 검색하는 유일한 방법입니다.

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>이미지 세트 편집에 설명된 대로 사용자 인터페이스를 통해 세트를 볼 [수 있습니다](#editing-image-sets).

## 이미지 세트 편집 {#editing-image-sets}

다음과 같이 이미지 세트에서 다양한 편집 작업을 수행할 수 있습니다.

* 이미지 세트에 이미지를 추가합니다.
* 이미지 세트에서 이미지 순서를 변경합니다.
* 이미지 세트에서 자산을 삭제합니다.
* 뷰어 사전 설정을 적용합니다.
* 이미지 세트를 삭제합니다.

**이미지 세트를 편집하려면**

1. 다음 중 하나를 수행합니다.

   * 이미지 세트 자산 위로 마우스를 가져간 다음 편집( **[!UICONTROL 연필]** 아이콘)을 누릅니다.
   * 이미지 세트 자산 위로 마우스를 가져간 다음 **[!UICONTROL 선택]** (확인 표시 아이콘)을 누른 다음 **[!UICONTROL 도구 모음에서 편집을]** 탭합니다.
   * 이미지 세트 자산을 탭한 다음 도구 **[!UICONTROL 모음에서 편집]** (연필 아이콘)을 탭합니다.

1. 이미지 세트에서 이미지를 편집하려면 다음 중 하나를 수행합니다.

   * 자산의 순서를 바꾸려면 이미지를 새 위치로 드래그합니다(항목을 이동하려면 순서 변경 아이콘 선택).
   * 항목을 오름차순이나 내림차순으로 정렬하려면 열 제목을 클릭합니다.
   * 자산을 추가하거나 기존 자산을 업데이트하려면 자산 추가를 **[!UICONTROL 클릭합니다]**. 자산을 탐색하고 선택한 다음 **[!UICONTROL 페이지의]** 오른쪽 위 모서리 근처에 있는 선택을 누릅니다.
      >[!NOTE]
      >
      >AEM에서 축소판에서 사용하는 이미지를 다른 이미지로 대체하여 삭제하는 경우 원본 자산이 계속 표시됩니다.
   * 자산을 삭제하려면 자산을 선택하고 자산 삭제를 탭하거나 **[!UICONTROL 클릭합니다]**.
   * 페이지의 오른쪽 위 모서리 근처에 있는 사전 설정을 적용하려면 사전 설정을 누른 **[!UICONTROL 다음]**&#x200B;뷰어 사전 설정을 선택합니다.
   * 축소판을 추가하거나 변경하려면 자산의 오른쪽 옆에 있는 축소판 아이콘을 선택합니다. 새로운 축소판 또는 견본 자산으로 이동하여 선택한 다음 선택을 **[!UICONTROL 누릅니다]**.
   * 전체 이미지 세트를 삭제하려면 이미지 세트로 이동하여 선택한 다음 삭제를 **[!UICONTROL 누릅니다]**.
   >[!NOTE]
   >
   >세트로 이동하여 이미지 세트에서 이미지를 편집하고 왼쪽 레일에서 **[!UICONTROL 멤버]** 설정을 누른 다음 개별 자산에서 연필 아이콘을 눌러 편집 창을 열 수 있습니다.

1. 편집을 **[!UICONTROL 마치면]** 저장을 누릅니다.

## 이미지 세트 미리 보기 {#previewing-image-sets}

자산 [미리 보기를](/help/assets/dynamic-media/previewing-assets.md)참조하십시오.

## 이미지 세트 게시 {#publishing-image-sets}

자산 [게시를 참조하십시오](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
