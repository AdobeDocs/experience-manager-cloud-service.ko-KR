---
title: 스핀 세트
description: Dynamic Media에서 스핀 세트를 사용하는 방법을 알아봅니다.
feature: Spin Sets
role: User
exl-id: ed470472-62d9-4684-971b-30df3919c180
source-git-commit: a2bbc64051214efa83d74d414e2e5f1407433127
workflow-type: tm+mt
source-wordcount: '1927'
ht-degree: 10%

---

# 스핀 세트{#spin-sets}

스핀 세트는 개체를 돌려 검사하는 실제 동작을 시뮬레이션합니다. 스핀 세트를 사용하면 모든 각도에서 주요 시각적 세부 사항을 획득하여 항목을 볼 수 있습니다.

스핀 세트는 360° 보기 경험을 시뮬레이션합니다. Dynamic Media에서는 뷰어가 항목을 회전할 수 있는 단일 축 스핀 세트를 제공합니다. 또한 사용자는 몇 번의 간단한 마우스 클릭으로 모든 보기를 &quot;자유 형식&quot;으로 확대/축소하고 이동할 수 있습니다. 이렇게 하면 특정 시점에서 항목을 더 자세히 검사할 수 있습니다.

스핀 세트는 단어가 포함된 배너에 의해 지정됩니다 **[!UICONTROL SPINSET]**. 또한 스핀 세트가 게시되면 게시 날짜가 **[!UICONTROL World]** 아이콘은 마지막 수정 날짜와 함께 배너에 있으며, **[!UICONTROL 연필]** 아이콘이 표시됩니다.

![chlimage_1-](assets/chlimage_1-380.png)

>[!NOTE]
>
>Assets 사용자 인터페이스에 대한 자세한 내용은 [Touch UI를 사용하여 자산 관리](/help/assets/manage-digital-assets.md) 이미지 세트 자산이 업로드된 새 폴더에 적용합니다.

스핀 세트를 만들 때, Adobe은 다음 모범 사례를 권장하고 다음 제한을 적용합니다.

| 제한 유형 | 우수 사례 | 제한 적용 |
| --- | --- | --- |
| 2D 세트당 최대 행/열 수 | 세트당 12-18개 이미지 | 1000 |

참조 - [Dynamic Media 제한 사항](/help/assets/dynamic-media/limitations.md).

## 빠른 시작: 스핀 세트 {#quick-start-spin-sets}

스핀 세트를 사용하여 빠르게 시작하고 실행하려면 다음 단계를 수행합니다.

1. 선택 사항입니다. [배치 집합 사전 설정 만들기](/help/assets/dynamic-media/batch-set-presets-dm.md) 새 자산 폴더에 적용합니다.

   배치 세트 사전 설정을 사용하면 스핀 세트 생성을 자동화할 수 있습니다.

   >[!IMPORTANT]
   >
   >Batch sets are created by the IPS (Image Production System) as part of asset ingestion.

1. [여러 보기를 위해 이미지 업로드](#uploading-assets-for-spin-sets).

   최소한 1차원 스핀 세트의 경우 항목의 8-12샷과 2차원 스핀 세트의 경우 16-24샷이 필요합니다. 정기적으로 샷을 진행해야 항목이 회전하고 뒤집히는 느낌을 줄 수 있습니다. 예를 들어 1차원 스핀 세트에 12개의 샷이 포함되어 있는 경우 각 샷에 대해 30° (360/12) 항목을 회전합니다.

   자세한 내용은 [Dynamic Media - 지원되는 래스터 이미지 형식](/help/assets/file-format-support.md#image-support-dynamic-media) 를 클릭합니다.

1. [스핀 세트 만들기](#creating-spin-sets).

   스핀 세트를 생성하려면 다음을 선택합니다 **[!UICONTROL 만들기]** > **[!UICONTROL 스핀 세트]** 그런 다음 세트의 이름을 지정하고, 자산을 선택하고, 이미지가 나타나는 순서를 선택합니다.

   자세한 내용은 [선택기를 사용한 작업](/help/assets/dynamic-media/working-with-selectors.md).

1. 설정 [스핀 세트 뷰어 사전 설정](/help/assets/dynamic-media/managing-viewer-presets.md)필요한 경우 ).

   Administrators can create or modify Spin Set Viewer Presets. To see your spin set with a viewer preset, select the spin set, and in the left-rail drop-down menu, select **Viewers**.

   뷰어 사전 설정을 만들거나 편집하려면 다음을 참조하십시오 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 뷰어 사전 설정]**.

   자세한 내용은 [뷰어 사전 설정 추가 및 편집](/help/assets/dynamic-media/managing-viewer-presets.md).

   일괄처리 집합 사전 설정을 통해 만들어진 세트는 3가지 방법으로 보고 액세스할 수 있습니다. (일괄처리 집합 사전 설정을 사용하여 만든 집합입니다. *not* 가 사용자 인터페이스에 표시됩니다.)

1. [스핀 세트 미리 보기](/help/assets/dynamic-media/previewing-assets.md).

   스핀 세트를 선택하고 미리 볼 수 있습니다. 회전 세트를 회전합니다. 에서 다른 뷰어를 선택할 수 있습니다 **[!UICONTROL 뷰어]** 메뉴 아래의 왼쪽 레일 드롭다운 메뉴에서 사용할 수 있습니다.

1. [스핀 세트 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   스핀 세트를 게시하면 URL 및 포함 문자열이 활성화됩니다. 또한 다음을 수행해야 합니다 [뷰어 사전 설정 게시](/help/assets/dynamic-media/managing-viewer-presets.md).

1. [웹 응용 프로그램에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 또는 [비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md).

   Adobe Experience Manager Assets는 스핀 세트에 대한 URL 호출을 만들고 스핀 세트를 게시한 후 활성화합니다. 자산을 미리 볼 때 이러한 URL을 복사할 수 있습니다. 또는 웹 사이트에 포함할 수 있습니다.

   Select the Spin Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   자세한 내용은 [웹 페이지에 스핀 세트 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 및 [비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md).

필요한 경우 다음을 수행할 수 있습니다 [스핀 세트 편집](#editing-spin-sets). 또한 를 보고 수정할 수 있습니다 [스핀 세트 속성](/help/assets/manage-digital-assets.md#editing-properties).

## 스핀 세트에 대한 자산 업로드 {#uploading-assets-for-spin-sets}

최소한 1차원 스핀 세트에 대해 항목의 8-12발이 필요합니다. 정기적으로 샷을 진행해야 항목이 회전하고 뒤집히는 느낌을 줄 수 있습니다. 예를 들어 1차원 스핀 세트에 12개의 샷이 포함되어 있는 경우 각 샷에 대해 30° (360/12) 항목을 회전합니다.

자세한 내용은 [Dynamic Media - 지원되는 래스터 이미지 형식](/help/assets/file-format-support.md#image-support-dynamic-media) 를 클릭합니다.

스핀 세트에 대한 이미지를 업로드하는 것처럼 할 수 있습니다 [Experience Manager Assets에서 다른 자산 업로드](/help/assets/manage-digital-assets.md).

### 스핀 세트에 대한 이미지 캡처 지침 {#guidelines-for-shooting-spin-set-images}

다음은 스핀 세트 이미지에 대한 몇 가지 우수 사례입니다. 일반적으로 스핀 세트에 있는 이미지가 많을수록 이미지 회전 효과가 더 좋습니다. 그러나 집합에 많은 이미지를 포함하면 이미지가 로드되는 데 걸리는 시간도 늘어납니다. Experience Manager은 스핀 세트에서 사용할 이미지를 촬영하기 위해 다음 지침을 권장합니다.

* 적어도, 1차원 스핀 세트에 8-12개의 이미지와 2차원 스핀 세트에 있는 16-24개의 이미지를 사용합니다. 360°을 회전하려면 최소 8개의 이미지가 필요합니다. 2차원 스핀 세트를 만드는 것은 노동 집약이므로 1차원 스핀 세트가 더 일반적입니다.
* 무손실 형식 사용; TIFF 및 PNG가 권장됩니다.
* 항목이 흰색이나 다른 고대비 백그라운드에 나타나도록 모든 이미지를 마스크합니다. 선택적으로 그림자를 추가합니다.
* 제품 세부 사항이 잘 조명되고 초점이 맞춰졌는지 확인하십시오.
* 패션 의류를 위한 스핀 이미지를 마네킹이나 모델로 가져가세요. 마네킹은 종종 마스킹되거나(유리 마네킹을 사용), 스티처리된 마네킹/드레싱이 이미지에 표시됩니다. 각도 수를 정의하여 모델 회전 세트를 생성할 수 있습니다. 모델을 단계별로 안내하고 각 샷의 방향을 확인할 수 있도록 바닥에 있는 테이프로 각 각도를 표시합니다.

## 스핀 세트 만들기 {#creating-spin-sets}

이 섹션에서는 스핀 세트를 만드는 방법을 설명합니다.

>[!NOTE]
>
>You can also create spin sets automatically through [batch set presets](/help/assets/dynamic-media/config-dm.md). **Important:** Batch sets are created by the IPS (Image Production System) as part of asset ingestion.
>
>의 &quot;이미지 세트 및 스핀 세트를 자동으로 생성하기 위한 일괄처리 집합 사전 설정 만들기&quot;를 참조하십시오. [Dynamic Media 구성](/help/assets/dynamic-media/config-dm.md).

>[!NOTE]
>
>스핀 세트 물질에 이미지가 표시되는 순서입니다. 회전 방향이 매끄러운 360° 보기라면 반드시 주문하십시오.

스핀 세트를 만들 때, Adobe은 다음 모범 사례를 권장하고 다음 제한을 적용합니다.

| 제한 유형 | 우수 사례 | 제한 적용 |
| --- | --- | --- |
| 2D 세트당 최대 행/열 수 | 세트당 12-18개 이미지 | 1000년 |

참조 - [Dynamic Media 제한 사항](/help/assets/dynamic-media/limitations.md).

**스핀 세트를 생성하려면**

1. 자산에서 스핀 세트를 만들 위치로 이동하여 을 선택합니다 **[!UICONTROL 만들기]**&#x200B;를 선택한 다음 을 선택합니다. **[!UICONTROL 스핀 세트]**. You can also create the set from inside a folder that contains your assets.

   ![6_5_spinset-createpulldownmenu](assets/6_5_spinset-createpulldownmenu.png)

1. 스핀 세트 편집기에서 **[!UICONTROL 제목]** 필드에 스핀 세트의 이름을 입력합니다. 스핀 세트 위의 배너에 이름이 표시됩니다. 설명을 입력합니다(선택적).

   ![6_5_spinset-spinseteditortitle](assets/6_5_spinset-spinseteditortitle.png)

   >[!NOTE]
   >
   >스핀 세트를 만들 때 스핀 세트 축소판을 변경하거나 스핀 세트의 자산을 기준으로 Experience Manager이 축소판을 자동으로 선택하도록 허용할 수 있습니다. 축소판을 선택하려면 **[!UICONTROL 축소판 변경]** 이미지를 선택합니다(다른 폴더로 이동하여 이미지를 찾을 수도 있습니다.). 축소판을 선택한 다음 스핀 세트에서 생성할 Experience Manager을 결정하려면 **[!UICONTROL 자동 축소판으로 전환]**.

1. 다음 중 하나를 수행합니다.

   * 스핀 세트 편집기 페이지의 왼쪽 위 모서리 근처에 있는 를 선택합니다. **[!UICONTROL 자산 추가]**.

   * [스핀 세트 편집기] 페이지의 중간 근처에 있는 를 선택합니다 **[!UICONTROL 탭하여 자산 선택기 열기]**.
   스핀 세트에 포함할 자산을 선택합니다. Selected assets have a checkmark icon over them. 완료되면 페이지의 오른쪽 위 모서리 근처에 있는 를 선택합니다. **[!UICONTROL 선택]**.

   With the Asset Selector, you can search for assets by typing in a keyword and tapping **[!UICONTROL Return]**. You can also apply filters to refine your search results. You can filter by path, collection, file type, and tag. 필터를 선택한 다음 **[!UICONTROL 필터]** 아이콘을 클릭합니다. Change the view by tapping the View icon and selecting **[!UICONTROL Column View]**, **[!UICONTROL Card View]**, or **[!UICONTROL List View]**.

   자세한 내용은 [선택기를 사용한 작업](/help/assets/dynamic-media/working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. 세트에 자산을 추가하면 자동으로 영숫자 순서로 추가됩니다. 자산을 추가한 후 수동으로 자산 순서를 변경하거나 정렬할 수 있습니다.

   필요한 경우 자산의 재정렬 아이콘을 자산의 파일 이름 오른쪽에 드래그하여 이미지 순서를 세트 목록의 위나 아래로 지정합니다.

   ![스핀 세트에서 프레임 11을 새 위치로 드래그하여 재정렬합니다](assets/6_5_spinset-reorderassets.png)

   스핀 세트에서 프레임 11을 새 위치로 드래그하여 순서를 변경합니다.

1. (선택 사항) 다음 중 하나를 수행합니다.

   * 이미지를 삭제하려면 이미지를 선택하고 을(를) 선택합니다 **[!UICONTROL 자산 삭제]**.

   * 페이지의 오른쪽 위 모서리 근처에 있는 사전 설정을 적용하려면 을(를) 선택합니다 **[!UICONTROL 사전 설정]**&#x200B;를 선택한 다음 사전 설정을 선택하여 모든 자산에 한 번에 적용합니다.

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다. 새로 만든 스핀 세트가 생성한 폴더에 나타납니다.

## 스핀 세트 보기 {#viewing-spin-sets}

사용자 인터페이스에서 또는 를 사용하여 자동으로 스핀 세트를 만들 수 있습니다 [일괄처리 집합 사전 설정](/help/assets/dynamic-media/config-dm.md). 그러나 일괄처리 집합 사전 설정을 사용하여 만든 집합에서는 다음을 수행합니다 *not* 사용자 인터페이스에 표시됩니다. 세 가지 방법으로 일괄처리 집합 사전 설정을 통해 만든 세트에 액세스할 수 있습니다. (이러한 메서드는 사용자 인터페이스에서 스핀 세트를 만든 경우에도 사용할 수 있습니다.)

>[!NOTE]
>
>에 설명된 대로 사용자 인터페이스를 통해 세트를 볼 수도 있습니다. [스핀 세트 편집](#editing-spin-sets).

**스핀 세트를 보려면**

1. 개별 자산의 속성을 열 때. 속성은 선택한 자산이 (아래에) 멤버인 세트를 나타냅니다 **[!UICONTROL 집합 멤버]**). 전체 세트를 보려면 세트의 이름을 선택합니다.

   ![chlimage_1-156](assets/chlimage_1-384.png)

1. From a member image of any set. 을(를) 선택합니다 **[!UICONTROL 세트]** 메뉴 아래의 제품에서 자산이 속하는 세트를 표시합니다.

   ![chlimage_1-157](assets/chlimage_1-385.png)

1. From search, you can Select **[!UICONTROL Filters]**, then expand **[!UICONTROL Dynamic Media]** and select **[!UICONTROL Sets]**.

   검색은 UI에서 수동으로 만들거나 일괄처리 집합 사전 설정을 통해 자동으로 생성된 일치 세트를 반환합니다. 자동화된 세트의 경우 검색 쿼리는 `Starts with` 사용 기준으로 하는 Experience Manager 검색과 다른 검색 기준 `Contains` 검색 기준. 필터를 로 설정 **[!UICONTROL 세트]** 는 자동화된 세트를 검색하는 유일한 방법입니다.

   ![chlimage_1-158](assets/chlimage_1-386.png)

## 스핀 세트 편집 {#editing-spin-sets}

스핀 세트에서 다음과 같은 다양한 편집 작업을 수행할 수 있습니다.

* 스핀 세트에 이미지를 추가합니다.
* 스핀 세트에서 이미지 재정렬.
* 스핀 세트에서 자산을 삭제합니다.
* 뷰어 사전 설정을 적용합니다.
* 스핀 세트를 삭제합니다.

**스핀 세트를 편집하려면**

1. 다음 중 하나를 수행합니다.

   * 스핀 세트 자산을 마우스로 가리킨 다음, 을 선택합니다 **[!UICONTROL 편집]** (연필 아이콘).
   * 스핀 세트 자산을 마우스로 가리킨 다음, 을 선택합니다 **[!UICONTROL 선택]** (확인 표시 아이콘)을 선택한 다음 **[!UICONTROL 편집]** 클릭합니다.

   * 스핀 세트 자산을 선택한 다음 을 선택합니다 **[!UICONTROL 편집]** (연필 아이콘)을 클릭하여 제품에서 사용할 수 있습니다.

1. 스핀 세트를 편집하려면 다음 중 하나를 수행합니다.

   * 이미지를 재정렬하려면 이미지를 새 위치로 드래그합니다(항목을 이동하려면 재정렬 아이콘을 선택합니다.).
   * 항목을 오름차순이나 내림차순으로 정렬하려면 열 머리글을 선택합니다.
   * 자산을 추가하거나 기존 자산을 업데이트하려면 **[!UICONTROL 자산 추가]**. 자산으로 이동하여 선택한 다음 선택합니다 **[!UICONTROL 선택]** 오른쪽 상단 근처에 있습니다.
Experience Manager이 축소판에 사용하는 이미지를 다른 이미지로 대체하여 삭제하면 원본 자산이 계속 표시됩니다.
   * 자산을 삭제하려면 해당 자산을 선택하고 을(를) 선택합니다 **[!UICONTROL 자산 삭제]**.
   * 사전 설정을 적용하려면 사전 설정 아이콘을 선택하고 사전 설정을 선택합니다.
   * 전체 스핀 세트를 삭제하려면 스핀 세트로 이동하여 선택한 다음 선택합니다 **[!UICONTROL 삭제]**

   >[!NOTE]
   >
   >세트로 이동하여 스핀 세트에서 이미지를 편집할 수 있습니다. **[!UICONTROL 구성원 설정]** 왼쪽 레일에서 개별 자산에 대한 연필 아이콘을 선택하여 편집 창을 엽니다.

1. 선택 **[!UICONTROL 저장]** 편집을 완료하면 됩니다.

## 스핀 세트 미리 보기 {#previewing-spin-sets}

자세한 내용은 [자산 미리 보기](/help/assets/dynamic-media/previewing-assets.md).

## 스핀 세트 게시 {#publishing-spin-sets}

자세한 내용은 [자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
