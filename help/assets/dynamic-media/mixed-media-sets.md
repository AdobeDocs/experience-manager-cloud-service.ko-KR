---
title: 혼합 미디어 세트
description: Dynamic Media에서 혼합 미디어 세트를 사용하는 방법을 알아봅니다.
feature: 혼합 미디어 세트
role: User
exl-id: 7ccde741-38d2-44c9-9378-f2721384aab7
source-git-commit: a11529886d4b158c19a97ccbcb7d004cf814178d
workflow-type: tm+mt
source-wordcount: '1470'
ht-degree: 1%

---

# 혼합 미디어 세트{#mixed-media-sets}

혼합 미디어 세트를 사용하면 이미지, 이미지 세트, 스핀 세트 및 비디오를 하나의 프레젠테이션에 혼합할 수 있습니다.

혼합 미디어 집합은 배너에 의해 **[!UICONTROL MixedMediaSet]**&#x200B;라는 단어가 지정됩니다. 또한 혼합 미디어 세트가 게시되면 **[!UICONTROL World]** 아이콘에 표시된 게시 날짜가 **[!UICONTROL Pencil]** 아이콘으로 표시된 마지막 수정 날짜와 함께 배너에 표시됩니다.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Assets 사용자 인터페이스에 대한 자세한 내용은 [Touch UI를 사용하여 자산 관리](/help/assets/manage-digital-assets.md)를 참조하십시오.

## 빠른 시작: 혼합 미디어 집합 {#quick-start-mixed-media-sets}

혼합 미디어 세트를 사용하여 빠르게 시작하고 실행하려면 다음 단계를 수행합니다.

1. [자산을 업로드합니다](#uploading-assets).

   먼저 혼합 미디어 세트에 대한 이미지 및 비디오를 업로드하십시오. 필요한 경우 [이미지 세트](/help/assets/dynamic-media/image-sets.md) 및 [스핀 세트](/help/assets/dynamic-media/spin-sets.md)를 만듭니다. 사용자는 혼합 미디어 세트 뷰어에서 이미지를 확대/축소할 수 있으므로 이미지를 선택할 때 확대/축소를 고려해야 합니다. 이미지의 크기가 가장 큰 2000픽셀 이상인지 확인하십시오.

1. [혼합 미디어 세트를 만듭니다](#creating-mixed-media-sets).

   혼합 미디어 세트를 만들려면 자산 페이지에서 **[!UICONTROL 만들기]** > **[!UICONTROL 혼합 미디어 세트]**&#x200B;로 이동한 다음 세트의 이름을 지정하고, 자산을 선택하고 이미지가 나타나는 순서를 선택합니다.

   [선택기를 사용한 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하십시오.

1. 필요에 따라 [혼합 미디어 뷰어 사전 설정](/help/assets/dynamic-media/managing-viewer-presets.md)을 설정합니다.

   관리자는 혼합 미디어 세트 뷰어 사전 설정을 만들거나 수정할 수 있습니다. 뷰어 사전 설정이 있는 혼합 미디어를 보려면 혼합 미디어 세트를 선택하고 왼쪽 레일 드롭다운 메뉴에서 **[!UICONTROL 뷰어]**&#x200B;를 선택합니다.

   뷰어 사전 설정을 만들거나 편집하려면 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 뷰어 사전 설정]**&#x200B;으로 이동합니다.

   [뷰어 사전 설정 추가 및 편집](/help/assets/dynamic-media/managing-viewer-presets.md)을 참조하십시오.

1. [혼합 미디어 세트를 미리 봅니다](#previewing-mixed-media-sets).

   혼합 미디어 세트를 선택하면 미리 볼 수 있습니다. 선택한 뷰어에서 혼합 미디어 세트를 검사하려면 축소판 아이콘을 선택합니다. 왼쪽 레일 드롭다운 메뉴에서 사용할 수 있는 **[!UICONTROL 뷰어]** 메뉴에서 다른 뷰어를 선택할 수 있습니다.

1. [혼합 미디어 세트를 게시합니다](#publishing-mixed-media-sets).

   혼합 미디어 세트를 게시하면 URL 및 포함 문자열이 활성화됩니다. 또한 [뷰어 사전 설정을 게시](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets)해야 합니다.

1. [웹 애플리케이션에 URL을 ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 연결하거나  [비디오 또는 이미지 뷰어를 포함합니다](/help/assets/dynamic-media/embed-code.md).

   Adobe Experience Manager Assets는 혼합 미디어 세트에 대한 URL 호출을 만들고 혼합 미디어 세트를 게시한 후 활성화합니다. 자산을 미리 볼 때 이러한 URL을 복사할 수 있습니다. 또는 웹 사이트에 포함할 수 있습니다.

   혼합 미디어 세트를 선택한 다음 왼쪽 레일 드롭다운 메뉴에서 **[!UICONTROL 뷰어]**&#x200B;를 선택합니다.

   [혼합 미디어 세트를 웹 페이지에 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) 및 [비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)을 참조하십시오.

필요한 경우 [혼합 미디어 세트](#editing-mixed-media-sets)를 편집할 수 있습니다. 또한 [혼합 미디어 세트 속성](/help/assets/manage-digital-assets.md#editing-properties)을 보고 수정할 수 있습니다.

>[!NOTE]
>
>세트를 만드는 데 문제가 있는 경우 [Dynamic Media 문제 해결](/help/assets/dynamic-media/troubleshoot-dm.md)을 참조하십시오.

## 자산 업로드 {#uploading-assets}

먼저 혼합 미디어 세트에 대한 이미지 및 비디오를 업로드하십시오. 사용자는 혼합 미디어 세트 뷰어에서 이미지를 확대할 수 있습니다. 따라서 확대/축소 기능을 염두에 두고 이미지를 선택합니다. 이미지의 크기가 가장 큰 2000픽셀 이상인지 확인하십시오.

또한 혼합 미디어 세트에 스핀 세트 또는 이미지 세트를 추가하려면 해당 세트도 만듭니다.

## 혼합 미디어 집합 만들기 {#creating-mixed-media-sets}

이미지, 이미지 세트, 스핀 세트 및 비디오를 혼합 미디어 세트에 추가할 수 있습니다. 혼합 미디어 세트에 추가하기 전에 파일, 이미지 세트 및 스핀 세트를 게시할 준비가 되었는지 확인합니다.

세트에 자산을 추가하면 자동으로 영숫자 순서로 추가됩니다. 자산이 추가된 후 자산을 수동으로 재정렬하거나 정렬할 수 있습니다.

**혼합 미디어 세트를 만들려면:**

1. 자산에서 혼합 미디어 세트를 만들 위치로 이동하여 **[!UICONTROL 만들기]**&#x200B;를 선택하고 **[!UICONTROL 혼합 미디어 세트]**&#x200B;를 선택합니다. 자산을 포함하는 폴더 내에서 세트를 만들 수도 있습니다. 혼합 미디어 세트 편집기가 표시됩니다.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. 혼합 미디어 세트 편집기의 **[!UICONTROL 제목]**&#x200B;에 혼합 미디어 세트의 이름을 입력합니다. 이 이름은 혼합 미디어 집합 전체의 배너에 표시됩니다. 설명을 입력합니다(선택적).

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >혼합 미디어 세트를 생성할 때 혼합 미디어 세트 축소판을 변경하거나 혼합 미디어 세트의 자산을 기반으로 Experience Manager이 자동으로 축소판을 선택할 수 있습니다. 축소판을 선택하려면 **[!UICONTROL 축소판 변경]**&#x200B;을 선택하고 이미지를 선택합니다. 이미지를 찾으려면 다른 폴더로 이동하여 찾을 수도 있습니다. 축소판을 선택한 다음 혼합 미디어 세트에서 생성할 Experience Manager을 결정하려면 **[!UICONTROL 자동 축소판으로 전환]**&#x200B;을 선택합니다.

1. 혼합 미디어 세트에 포함할 자산을 선택하려면 자산 선택기를 선택합니다. 선택 후 **[!UICONTROL 선택]**&#x200B;을 선택합니다.

   자산 선택기를 사용하여 키워드를 입력하고 **[!UICONTROL Return]**&#x200B;을 선택하여 자산을 검색할 수 있습니다. 필터를 적용하여 검색 결과를 세분화할 수도 있습니다. 경로, 컬렉션, 파일 유형 및 태그별로 필터링할 수 있습니다. 필터를 선택한 다음 도구 모음에서 **[!UICONTROL 필터]** 아이콘을 선택합니다. **[!UICONTROL 보기]** 아이콘을 선택하고 **[!UICONTROL 목록 보기]**, **[!UICONTROL 열 보기]** 또는 **[!UICONTROL 카드 보기]**&#x200B;를 선택하여 보기를 변경합니다.

   [선택기를 사용한 작업](/help/assets/dynamic-media/working-with-selectors.md)을 참조하십시오.

   ![chlimage_1-140](assets/chlimage_1-351.png)

1. 자산을 목록의 위나 아래로 드래그하여 순서를 변경합니다(필요한 경우 **[!UICONTROL Reorder]** 아이콘을 선택해야 함).

   ![chlimage_1-141](assets/chlimage_1-352.png)

   축소판을 추가하려면 이미지 옆에 있는 **+** **[!UICONTROL 축소판]** 아이콘을 선택하고 원하는 축소판으로 이동합니다. 모든 축소판 이미지를 선택하면 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

   >[!NOTE]
   >
   >자산을 추가하려면 **[!UICONTROL 자산 추가]**&#x200B;를 선택합니다.

1. 자산을 삭제하려면 해당 확인란을 선택하고 **[!UICONTROL 자산 삭제]**&#x200B;를 선택합니다.
1. 사전 설정을 적용하려면 오른쪽 위 모서리에서 **[!UICONTROL 사전 설정]** 을 선택하고 사전 설정을 선택하여 자산에 적용합니다.
1. **[!UICONTROL 저장]**&#x200B;을 선택합니다. 새로 만든 혼합 미디어 세트가 만든 폴더에 나타납니다.

## 혼합 미디어 집합 편집 {#editing-mixed-media-sets}

Assets](/help/assets/manage-digital-assets.md)의 자산처럼 사용자 인터페이스에서 직접 혼합 미디어 세트의 자산에 대한 다양한 편집 작업을 수행할 수 있습니다. [ 혼합 미디어 세트에서 다음 작업을 수행할 수도 있습니다.

* 혼합 미디어 세트에 자산을 추가합니다.
* 혼합 미디어 집합에서 자산 재정렬입니다.
* 혼합 미디어 집합에서 자산을 삭제합니다.
* 뷰어 사전 설정을 적용합니다.
* 기본 축소판을 변경합니다.

**혼합 미디어 세트를 편집하려면 다음을 수행하십시오.**

1. 다음 중 하나를 수행합니다.

   * 혼합 미디어 세트 자산 위로 마우스를 가져간 다음 **[!UICONTROL 편집]** (연필 아이콘)을 선택합니다.
   * 혼합 미디어 세트 자산 위로 마우스를 가져간 후 **[!UICONTROL 선택]**(확인 표시 아이콘)을 선택한 다음, 도구 모음에서 **[!UICONTROL 편집]**&#x200B;을 선택합니다.

   * 혼합 미디어 세트 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 편집]** (연필 아이콘)을 선택합니다.

1. 혼합 미디어 세트 편집기에서 다음 중 하나를 수행합니다.

   * 자산 순서를 조정하려면 - 왼쪽 패널에서 **[!UICONTROL 자산]**(그림 아이콘)을 선택하고 자산을 새 위치로 드래그합니다.
   * 자산을 추가하려면 - 도구 모음에서 **[!UICONTROL 자산 추가]**&#x200B;를 선택합니다. 자산으로 이동합니다. 추가하려는 각 자산에 대해, 자산의 이미지(자산 이름이 아님)를 마우스로 가리킨 다음, 확인 표시 아이콘을 선택합니다. 오른쪽 위 모서리에서 **[!UICONTROL 선택]**&#x200B;을 선택합니다.

   * 자산을 삭제하려면 - 왼쪽 패널에서 **[!UICONTROL 자산]**(그림 아이콘)을 선택한 다음 자산을 선택합니다. 도구 모음 모음에서 **[!UICONTROL 자산 삭제]**&#x200B;를 선택합니다.

   * 자산을 오름차순이나 내림차순으로 정렬하려면 왼쪽 패널에서 **[!UICONTROL 자산]** (그림 아이콘)을 선택합니다. **[!UICONTROL Assets]** 제목 오른쪽에서 위쪽 또는 아래쪽 캐럿 아이콘을 선택합니다.

      >[!NOTE]
      >
      >* 전체 혼합 미디어 세트를 삭제하려면, 임의의 보기 모드(예: **[!UICONTROL 카드 보기]** 또는 **[!UICONTROL 열 보기]**)에서 혼합 미디어 세트로 이동합니다. 자산을 마우스로 가리킨 다음, 선택하도록 확인 표시 아이콘을 선택합니다. 키보드에서 **[!UICONTROL 백스페이스]**&#x200B;를 누르거나 도구 모음에서 **[!UICONTROL 더 보기]**(세 점)를 선택한 다음 **[!UICONTROL 삭제]**&#x200B;를 선택합니다.
         >
         >
      * 세트로 이동하여 혼합 미디어 세트에서 자산을 편집할 수 있습니다. 왼쪽 레일에서 **[!UICONTROL 멤버 설정]**&#x200B;을 선택한 다음 개별 자산에서 **[!UICONTROL 연필]** 아이콘을 선택하여 편집 창을 엽니다.


1. 편집을 완료하면 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

   >[!NOTE]
   >
   >* 혼합 미디어 세트에서 자산을 편집하려면 - 혼합 미디어 세트로 이동합니다. Experience Manager 세트 미리 보기 페이지에서 세트를 열 수 있도록 세트를 탭(선택하지 않음)합니다. 왼쪽 레일에서 드롭다운 캐럿을 선택하여 드롭다운 목록을 연 다음 **[!UICONTROL 멤버 설정]**&#x200B;을 선택합니다. 구성원 설정 페이지에서 자산을 마우스로 가리킨 다음 **[!UICONTROL 편집]**(연필 아이콘)을 선택하여 편집 페이지를 엽니다.
      >
      >
   * 전체 혼합 미디어 세트를 삭제하려면 - 모든 보기 모드(카드 보기 또는 열 보기 등)에서 혼합 미디어 세트로 이동합니다. 세트를 마우스로 가리킨 다음 **[!UICONTROL 선택]**(확인 표시 아이콘)을 선택합니다. 키보드에서 **[!UICONTROL 백스페이스]**&#x200B;를 누르거나 **[!UICONTROL 더 보기]**(세 점 행)를 선택한 다음 **[!UICONTROL 삭제]**&#x200B;를 선택합니다.


## 혼합 미디어 집합 미리 보기 {#previewing-mixed-media-sets}

혼합 미디어 세트를 미리 보는 방법에 대한 자세한 내용은 [자산 미리 보기](/help/assets/dynamic-media/previewing-assets.md) 를 참조하십시오.

## 혼합 미디어 집합 게시 {#publishing-mixed-media-sets}

혼합 미디어 세트를 게시하는 방법에 대한 자세한 내용은 [자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) 를 참조하십시오.

>[!NOTE]
>
>처음 게시할 때 혼합 미디어 세트가 게재 서비스에서 완전히 종료되지 않은 경우 혼합 미디어 세트를 두 번째로 게시합니다.
