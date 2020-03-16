---
title: Adobe Experience Manager에서 디지털 자산 관리
description: 다양한 에셋 관리 및 편집 방법에 대해 알아봅니다.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 6998ee5f3c1c1563427e8739998effe0eba867fc

---


# Manage assets {#manage-assets}

이 문서에서는 AEM(Adobe Experience Manager) 자산에서 자산을 관리하고 편집하는 방법에 대해 설명합니다. 컨텐츠 조각을 관리하려면 컨텐츠 조각 [자산을 참조하십시오](content-fragments/content-fragments.md) .

## 폴더 만들기 {#creating-folders}

모든 이미지와 같은 자산 컬렉션을 구성할 때 폴더를 만들어 함께 유지할 수 있습니다. `Nature` 폴더를 사용하여 자산을 분류하고 구성할 수 있습니다. AEM Assets에서는 더 잘 작동하도록 폴더의 자산을 구성할 필요가 없습니다.

>[!NOTE]
>
>Marketing Cloud에 공유할 때 해당 유형의 자산 폴더 `sling:OrderedFolder`공유가 지원되지 않습니다. 폴더를 공유하려면 폴더를 만들 때 [!UICONTROL 순서가] 지정되지 않습니다.

1. 새 폴더를 만들 디지털 자산 폴더의 위치로 이동합니다. 메뉴에서 만들기를 **[!UICONTROL 클릭합니다]**. [새 **[!UICONTROL 폴더]를 선택합니다]**.
1. 제목 **[!UICONTROL 필드에]** 폴더 이름을 입력합니다. 기본적으로 DAM은 폴더 이름으로 제공한 제목을 사용합니다. 폴더가 만들어지면 기본값을 무시하고 다른 폴더 이름을 지정할 수 있습니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 폴더가 디지털 자산 폴더에 표시됩니다.

다음(공백으로 구분된) 문자는 지원되지 않습니다.

* 자산 파일 이름에는 다음 문자를 사용할 수 없습니다. `* / : [ \\ ] | # % { } ? &`
* 자산 폴더 이름에는 다음 문자를 사용할 수 없습니다. `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Upload assets {#uploading-assets}

자세한 내용은 [Adobe Experience Manager에](add-assets.md)디지털 자산 추가를 참조하십시오.

## 에셋 미리 보기 {#previewing-assets}

자산을 미리 보려면 다음 단계를 따르십시오.

1. 자산 사용자 인터페이스에서 미리 보려는 자산의 위치로 이동합니다.
1. 원하는 자산을 눌러 엽니다.

1. 미리 보기 모드에서는 [지원되는 이미지 유형](/help/assets/file-format-support.md) (대화형 편집 포함)에 대해 확대/축소 옵션을 사용할 수 있습니다.

   자산을 확대하려면 자산을 탭/클릭( `+` 또는 자산에서 확대경을 탭/클릭)합니다. 축소하려면 탭/클릭합니다 `-`. 확대하면 패닝하여 이미지의 모든 영역을 자세히 볼 수 있습니다. 확대/축소 재설정 화살표를 클릭하면 원래 보기로 돌아갑니다.

   재설정을 **[!UICONTROL 눌러]** 보기를 원래 크기로 재설정합니다.

## 속성 편집 {#editing-properties}

1. 편집할 메타데이터가 있는 자산의 위치로 이동합니다.

1. 자산을 선택하고 도구 모음에서 **[!UICONTROL 속성을]** 탭/클릭하여 자산 속성을 봅니다. 또는 자산 **[!UICONTROL 카드에서 속성]** 빠른 작업을 선택합니다.

   ![properties_quickaction](assets/properties_quickaction.png)

1. 속성 [!UICONTROL 페이지에서] 다양한 탭에서 메타데이터 속성을 편집합니다. 예를 들어 기본 **[!UICONTROL 탭에서]** 제목, 설명 등을 편집합니다.

   >[!NOTE]
   >
   >속성 페이지의 레이아웃 [!UICONTROL 및] 사용 가능한 메타데이터 속성은 기본 메타데이터 스키마에 따라 다릅니다. 속성 페이지의 레이아웃을 수정하는 방법에 대해 [!UICONTROL 알아보려면] 메타데이터 스키마를 [참조하십시오](/help/assets/metadata-schemas.md).

1. 자산의 활성화를 위한 특정 날짜/시간을 예약하려면 [설정 시간] 필드 옆에 있는 날짜 **[!UICONTROL 선택기를 사용합니다]** .

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. 특정 기간 후에 자산을 비활성화하려면 해제 시간 필드 옆에 있는 날짜 선택기에서 비활성화 날짜/시간을 **[!UICONTROL 선택합니다]** . 비활성화 날짜는 자산의 활성화 날짜보다 이후여야 합니다. 해제 [!UICONTROL 시간]후에는 자산 웹 인터페이스 또는 HTTP API를 통해 자산 및 표현물을 사용할 수 없습니다.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. 태그 **[!UICONTROL 필드에서]** 하나 이상의 태그를 선택합니다. 사용자 지정 태그를 추가하려면 상자에 태그 이름을 입력하고 Enter 키를 누릅니다. 새 태그가 AEM에 저장됩니다.

   YouTube를 게시하려면 태그가 필요하며 YouTube에 대한 링크가 있어야 합니다(적절한 링크를 찾을 수 있는 경우).

   >[!NOTE]
   >
   >태그를 만들려면 CRX 저장소의 `/content/cq:tags/default` 경로에 쓰기 권한이 있어야 합니다.

1. 자산에 대한 사용량 통계를 보려면 인사이트 **[!UICONTROL 탭을 클릭/탭합니다]** .

   사용 통계에는 다음이 포함됩니다.

   * 자산을 보거나 다운로드한 횟수
   * 자산이 사용된 채널/장치
   * 자산이 최근에 사용된 크리에이티브 솔루션
   자세한 내용은 자산 통찰력을 [참조하십시오](assets-insights.md).

1. 저장 및 **[!UICONTROL 닫기를 탭/클릭합니다]**.

1. 자산 사용자 인터페이스로 이동합니다. 제목, 설명 및 태그를 비롯한 편집된 메타데이터 속성은 카드 보기의 자산 카드 및 목록 보기의 관련 열 아래에 표시됩니다.

## 자산 복사 {#copying-assets}

자산 또는 폴더를 복사하면 전체 자산이나 폴더가 컨텐츠 구조와 함께 복사됩니다. 복사된 자산 또는 폴더는 대상 위치에 복제됩니다. 소스 위치의 자산은 변경되지 않습니다.

자산의 특정 사본에 고유한 몇 가지 특성은 전달되지 않습니다. 몇 가지 예는 다음과 같습니다.

* 자산 ID, 작성 날짜 및 시간, 버전 및 버전 내역. 이러한 속성 중 일부는 속성 `jcr:uuid``jcr:created`및 `cq:name`로 표시됩니다.

* 작성 시간 및 참조된 경로는 각 자산과 각 변환에 대해 고유합니다.

다른 속성과 메타데이터 정보는 그대로 유지됩니다. 자산을 복사할 때 부분 복사본이 만들어지지 않습니다.

1. 자산 UI에서 하나 이상의 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 복사]** 아이콘을 탭/클릭합니다. 또는 자산 **[!UICONTROL 카드에서 복사]** _ ![copy_icon](assets/copy_icon.png) 빠른 작업을 선택합니다.

   >[!NOTE]
   >
   >빠른 복사 [!UICONTROL 작업을] 사용하는 경우 한 번에 하나의 자산만 복사할 수 있습니다.

1. 자산을 복사할 위치로 이동합니다.

   >[!NOTE]
   >
   >동일한 위치에서 자산을 복사하면 AEM에서 변형된 이름을 자동으로 생성합니다. 예를 들어 제목이 지정된 자산을 복사하면 AEM에서 `Square`해당 사본의 제목을 자동으로 생성합니다 `Square1`.

1. 도구 모음에서 **[!UICONTROL 자산]** 붙여넣기 아이콘을 클릭합니다. 자산이 이 위치에 복사됩니다.

   ![chlimage_1-219](assets/chlimage_1-219.png)

   >[!NOTE]
   >
   >붙여넣기 **[!UICONTROL 아이콘은]** 붙여넣기 작업이 완료될 때까지 도구 모음에서 사용할 수 있습니다.

### 자산 이동 또는 이름 바꾸기 {#moving-or-renaming-assets}

1. 이동할 자산의 위치로 이동합니다.

1. 자산을 선택하고 도구 모음에서 **[!UICONTROL 이동]** 아이콘 ![move_icon](assets/move_icon.png) 을탭/클릭합니다.

1. 자산 이동 마법사에서 다음 중 하나를 수행합니다.

   * 자산을 이동한 후 자산의 이름을 지정합니다. 그런 다음 다음을 탭/ **[!UICONTROL 클릭하여]** 진행합니다.

   * 취소를 탭/클릭하여 **[!UICONTROL 프로세스를]** 중지합니다.
   >[!NOTE]
   >
   >* 새 위치에 해당 이름의 자산이 없을 경우 자산에 대해 동일한 이름을 지정할 수 있습니다. 하지만 자산을 같은 이름의 자산이 있는 위치로 이동하는 경우 다른 이름을 사용해야 합니다. 동일한 이름을 사용하면 변형된 이름이 자동으로 생성됩니다. 예를 들어 자산의 이름이 Square인 경우 시스템에서는 해당 사본에 대해 Square1이라는 이름을 생성합니다.
   >* 이름을 변경할 때 파일 이름에 공백을 사용할 수 없습니다.


1. 대상 **[!UICONTROL 선택]** 대화 상자에서 다음 중 하나를 수행합니다.

   * 자산의 새 위치로 이동한 다음 다음을 탭/클릭하여 **[!UICONTROL 계속 진행합니다]** .

   * 뒤로를 탭/ **[!UICONTROL 클릭하여]** 이름 변경 **[!UICONTROL 화면으로 돌아갑니다]** .

1. 이동되는 자산에 참조 페이지, 자산 또는 컬렉션이 있으면 대상 **[!UICONTROL 선택]** 탭 옆에 참조 조정 **[!UICONTROL 탭이]** 나타납니다.

   참조 조정 **[!UICONTROL 화면에서 다음 중 하나를 수행합니다]** .

   * 새 세부 정보에 따라 조정할 참조를 지정한 다음 이동을 탭/ **[!UICONTROL 클릭하여]** 진행합니다.

   * 조정 **[!UICONTROL 열에서]** 자산에 대한 참조를 선택/선택 취소합니다.
   * 뒤로 를 탭/ **[!UICONTROL 클릭하여]** 대상 **[!UICONTROL 선택]** 화면으로 돌아갑니다.

   * 취소를 탭/클릭하여 **[!UICONTROL 이동]** 작업을 중지합니다.
   참조를 업데이트하지 않으면 해당 참조는 자산의 이전 경로를 계속 가리킵니다. 참조를 조정하면 새 자산 경로로 업데이트됩니다.

### 변환 관리 {#managing-renditions}

1. 원본을 제외하고 자산에 대한 변환을 추가하거나 제거할 수 있습니다. 표현물을 추가하거나 제거할 자산의 위치로 이동합니다.

1. 자산을 탭/클릭하여 자산 페이지를 엽니다.

   ![chlimage_1-220](assets/chlimage_1-220.png)

1. GlobalNav 아이콘을 탭/클릭하고 목록에서 **[!UICONTROL 표현물을]** 선택합니다.

   ![renditions_menu](assets/renditions_menu.png)

1. 표현물 **[!UICONTROL 패널에서]** 자산에 대해 생성된 표현물 목록을 봅니다.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >기본적으로 AEM 자산은 미리 보기 모드에서 자산의 원본 변환을 표시하지 않습니다. 관리자의 경우 오버레이를 사용하여 AEM 자산을 구성하여 미리 보기 모드에서 원본 변환을 표시할 수 있습니다.

1. 변환을 보거나 삭제할 변환을 선택합니다.

   **변환 삭제**

   [표현물] 패널에서 **[!UICONTROL 표현물을]** 선택한 다음 도구 모음에서 **[!UICONTROL 표현물 삭제]** 아이콘을 탭/클릭합니다.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **새 변환 업로드**

   자산에 대한 자산 세부 사항 페이지로 이동하고 도구 모음에서 **[!UICONTROL 변환 추가]** 아이콘을 탭/클릭하여 자산에 대한 새 변환을 업로드합니다.

   ![chlimage_1-221](assets/chlimage_1-221.png)

   >[!NOTE]
   >
   >[표현물] 패널에서 표현물을 **[!UICONTROL 선택하면]** 도구 모음이 컨텍스트를 변경하고 표현물과 관련된 작업만 표시합니다. 변환 업로드 아이콘과 같은 옵션은 표시되지 않습니다. 도구 모음에서 이러한 옵션을 보려면 자산의 세부 정보 페이지로 이동합니다.

   이미지 또는 비디오 자산의 세부 정보 페이지에 표시할 변환의 크기를 구성할 수 있습니다. 지정한 차원에 따라 AEM 자산에 정확히 또는 가장 가까운 차원이 있는 변환이 표시됩니다.

   이미지의 변환 크기를 자산 세부 사항 수준에서 구성하려면 `renditionpicker` 노드(`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`)를 오버레이하고 폭 속성 값을 구성합니다. 이미지 크기에 따라 자산 세부 정보 페이지에서 변환을 사용자 **** 지정할 수 있도록 속성 크기(길이)를 너비 대신 KB로 구성합니다. 크기 기반 맞춤화의 경우, 일치된 표현물의 크기가 원본보다 큰 경우 속성은 원본에 기본 설정을 `preferOriginal` 할당합니다.

   마찬가지로 오버레이하여 주석 페이지 이미지를 사용자 정의할 수 `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`있습니다.

   ![chlimage_1-222](assets/chlimage_1-222.png)

   비디오 자산에 대한 변환 크기를 구성하려면 CRX 저장소의 `videopicker` 노드로 이동한 `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`후 해당 속성을 편집합니다.

   >[!NOTE]
   >
   >비디오 주석은 HTML5 호환 비디오 포맷이 있는 브라우저에서만 지원됩니다. 또한 브라우저에 따라 다른 비디오 형식이 지원됩니다.

## Delete assets {#delete-assets}

다른 페이지에서 들어오는 참조를 해결하거나 제거하려면 자산을 삭제하기 전에 관련 참조를 업데이트하십시오.

또한 오버레이를 사용하여 강제 삭제 단추를 비활성화하여 사용자가 참조된 자산을 삭제하고 끊어진 링크를 떠나지 않도록 합니다.

1. 삭제할 자산의 위치로 이동합니다.

1. 자산을 선택하고 도구 모음에서 **[!UICONTROL 삭제]** 아이콘을 탭/클릭합니다.

   ![delete_icon](assets/delete_icon.png)

1. 확인 대화 상자에서 다음을 클릭합니다.

   * **[!UICONTROL 작업을 중지하려면]** 취소
   * 해당 작업을 승인하려면 **[!UICONTROL 삭제]**

      * 자산에 참조가 없으면 자산이 삭제됩니다.
      * 자산에 참조가 있으면, 하나 이상의 자산이 **참조되었다고 오류 메시지가 표시됩니다.** **[!UICONTROL 강제 삭제]**&#x200B;나 **[!UICONTROL 취소]**&#x200B;를 선택할 수 있습니다.
   >[!NOTE]
   >
   >자산을 삭제하려면 dam/자산에 대한 삭제 권한이 필요합니다. 수정 권한만 있는 경우 자산 메타데이터를 편집하고 자산에 주석만 추가할 수 있습니다. 하지만 자산이나 해당 메타데이터는 삭제할 수 없습니다.

   >[!NOTE]
   >
   >다른 페이지에서 들어오는 참조를 해결하거나 제거하려면 자산을 삭제하기 전에 관련 참조를 업데이트하십시오.
   >
   >
   >또한 오버레이를 사용하여 강제 삭제 단추를 비활성화하여 사용자가 참조된 자산을 삭제하고 끊어진 링크를 떠나지 않도록 합니다.

## 자산 다운로드 {#download-assets}

See [Download assets from AEM](/help/assets/download-assets-from-aem.md).

## Publish assets {#publish-assets}

<!--
>[!NOTE]
>
>For more information specific to Dynamic Media, see [Publishing Dynamic Media Assets.](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
-->

1. 게시할 자산/폴더의 위치로 이동합니다.

1. 자산 **[!UICONTROL 카드에서 빠른 게시]** 작업을 선택하거나 자산을 선택하고 도구 모음에서 **[!UICONTROL 빠른 게시]** 아이콘을 탭/클릭합니다.
1. 자산이 다른 자산을 참조하는 경우 해당 참조가 마법사에 나열됩니다. 마지막으로 게시되었거나 게시 취소된 후 게시 취소되거나 수정된 참조만 표시됩니다. 게시할 참조를 선택합니다.

   ![chlimage_1-225](assets/chlimage_1-225.png)

   >[!NOTE]
   >
   >게시할 폴더에 빈 폴더가 포함되어 있으면 빈 폴더가 게시되지 않습니다.

1. 게시를 탭/ **[!UICONTROL 클릭하여]** 자산에 대한 활성화를 확인합니다.

>[!CAUTION]
>
>처리 중인 자산을 게시하면 원래 컨텐츠만 게시됩니다. 변환이 없습니다. 처리가 완료될 때까지 기다렸다가 게시 또는 처리가 완료되면 자산을 다시 게시하십시오.

## 자산 게시 취소 {#unpublishing-assets}

1. 게시 환경(게시 취소)에서 제거할 자산/자산 폴더의 위치로 이동합니다.

1. 게시를 취소할 자산/폴더를 선택하고 도구 모음에서 게시 **[!UICONTROL 관리]** 아이콘을 탭/클릭합니다.

   ![manage_publication](assets/manage_publication.png)

1. 목록에서 **[!UICONTROL 게시]** 취소 작업을 선택합니다.

   ![unpublish_action](assets/unpublish_action.png)

1. 나중에 자산을 게시 취소하려면 [나중에 게시 **[!UICONTROL 취소]를]**&#x200B;선택한 다음 자산의 게시 취소 날짜를 선택합니다.
1. 게시 환경에서 자산을 사용할 수 없는 날짜를 예약합니다.
1. 자산이 다른 자산을 참조하는 경우 게시 취소할 참조를 선택합니다. 게시 취소를 탭/ **[!UICONTROL 클릭합니다]**.
1. 확인 대화 상자에서 다음을 탭/클릭합니다.

   * **[!UICONTROL 작업을 중지하려면]** 취소
   * **[!UICONTROL 게시]** 취소를 클릭하여 지정된 날짜에 자산 게시 취소(더 이상 게시 환경에서 사용할 수 없음)가 되었는지 확인합니다.
   >[!NOTE]
   >
   >복잡한 자산을 게시 취소할 때는 자산만 게시 취소합니다. 다른 게시된 자산에서 참조될 수 있으므로 참조를 게시 취소하지 마십시오.

## Closed user group {#closed-user-group}

CUG(폐쇄된 사용자 그룹)는 AEM에서 게시한 특정 자산 폴더에 대한 액세스를 제한하는 데 사용됩니다. 폴더에 대한 CUG를 만드는 경우 폴더(폴더 자산 및 하위 폴더 포함)에 대한 액세스 권한은 지정된 구성원 또는 그룹으로만 제한됩니다. 폴더에 액세스하려면 보안 자격 증명을 사용하여 로그인해야 합니다.

CUG 파섹 폴더에 대한 로그인 페이지를 구성할 수도 있습니다.

1. 자산 UI에서 폴더를 선택하고 도구 모음에서 속성 아이콘을 탭/클릭하여 속성 페이지를 표시합니다.
1. 권한 **[!UICONTROL 탭에서]** 닫힌 사용자 그룹 아래에 구성원 또는 그룹을 **[!UICONTROL 추가합니다]**.

   ![add_user](assets/add_user.png)

1. 사용자가 폴더에 액세스할 때 로그인 화면을 표시하려면 활성화 **[!UICONTROL 옵션을 선택합니다]** . 그런 다음 AEM에서 로그인 페이지의 경로를 선택하고 변경 내용을 저장합니다.

   ![login_page](assets/login_page.png)

   >[!NOTE]
   >
   >로그인 페이지의 경로를 지정하지 않으면 게시 인스턴스에 기본 로그인 페이지가 표시됩니다.

1. 폴더를 게시한 다음 게시 인스턴스에서 액세스합니다. 로그인 화면이 표시됩니다.
1. CUG 회원인 경우 보안 자격 증명을 입력합니다. AEM에서 사용자를 인증한 후 폴더가 표시됩니다.

## 자산 검색 {#search-assets}

자산 검색은 크리에이티브 전문가가 추가적으로 사용하거나 비즈니스 사용자 및 마케터가 자산을 안전하게 관리하거나 DAM 관리자의 관리를 위해 디지털 자산 관리 시스템을 사용하는 데 중요합니다.

간단한, 고급 및 사용자 지정 검색을 통해 가장 적절한 자산을 검색하고 사용하려면 AEM에서 [검색 자산을 참조하십시오](/help/assets/search-assets.md).

## 빠른 작업 {#quick-actions}

빠른 작업 아이콘은 한 번에 한 자산에 사용할 수 있습니다. 장치에 따라 다음 작업을 수행하여 빠른 작업 아이콘을 표시합니다.

* 터치 장치:길게 터치하세요. 예를 들어, iPad에서는 빠른 작업이 표시되도록 자산을 길게 탭할 수 있습니다.
* 비터치 장치:포인터를 가져갑니다. 예를 들어, 데스크톱 장치에서는 포인터를 에셋 축소판 위에 두면 빠른 작업 막대가 표시됩니다.

## 이미지 편집 {#editing-images}

AEM 자산 인터페이스의 편집 도구를 사용하여 이미지 자산에 대해 작은 편집 작업을 수행할 수 있습니다. 이미지에서 자르기, 회전, 뒤집기 및 기타 편집 작업을 수행할 수 있습니다. 이미지 맵을 자산에 추가할 수도 있습니다.

>[!NOTE]
>
>일부 구성 요소의 경우 전체 화면 모드에는 추가 옵션을 사용할 수 있습니다.

1. 편집 모드에서 자산을 열려면 다음 중 하나를 수행합니다.

   * 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 편집]** 아이콘을 클릭/탭합니다.
   * 카드 보기에서 자산에 **[!UICONTROL 표시되는]** 편집 아이콘을 탭/클릭합니다.
   * 자산 페이지의 도구 모음에서 편집 **[!UICONTROL 아이콘을 탭]** /클릭합니다.
   ![edit_icon](assets/edit_icon.png)

1. 이미지를 자르려면 자르기 아이콘을 탭/ **클릭합니다** .

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. 목록에서 원하는 옵션을 선택합니다. 자르기 영역은 선택한 옵션에 따라 이미지에 나타납니다. [ **무료 손** ] 옵션을 사용하면 종횡비 제한 없이 이미지를 자를 수 있습니다.

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. 잘라낼 영역을 선택하고 이미지에서 크기를 조정하거나 위치를 변경합니다.
1. 마침 **아이콘** (오른쪽 상단)을 사용하여 이미지를 자릅니다. 마침 **아이콘을** 클릭하면 표현물의 재재생도 트리거됩니다.

   ![chlimage_1-228](assets/chlimage_1-228.png)

1. 오른쪽 **위에 있는** [실행 취소 **] 및 [다시 실행** ] 아이콘을 사용하여 잘리지 않은 이미지로 되돌리거나 잘린 이미지를 각각 유지합니다.

   ![chlimage_1-229](assets/chlimage_1-229.png)

1. 이미지를 시계 방향 또는 반시계 방향으로 회전하려면 해당 회전 아이콘을 탭/클릭합니다.

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. 해당 대칭 이동 아이콘을 탭/클릭하여 이미지를 가로 또는 세로로 뒤집습니다.

   ![chlimage_1-231](assets/chlimage_1-231.png)

1. 마침 아이콘을 탭/클릭하여 **변경** 사항을 저장합니다.

   ![chlimage_1-232](assets/chlimage_1-232.png)

>[!NOTE]
>
>BMP, GIF, PNG 및 JPEG 파일 포맷에 대한 이미지 편집 기능이 지원됩니다.

<!-- You can also add image maps using the image editor. For details, see [Adding Image Maps](/help/assets/image-maps.md). -->

>[!NOTE]
>
>TXT 파일을 편집하려면 Configuration Manager **에서 Day CQ Link** Externalizer를 설정합니다.

## 타임라인 {#timeline}

타임라인을 사용하면 자산, 주석/주석, 활동 로그 및 버전에 대한 활성 워크플로우 등 선택한 항목에 대한 다양한 이벤트를 볼 수 있습니다.

![자산에 대한 타임라인 항목 정렬그림](assets/sort_timeline.gif)*:자산에 대한 타임라인 항목 정렬*

>[!NOTE]
>
>컬렉션 [콘솔에서](/help/assets/manage-collections.md#navigate-the-collections-console)모두 **[!UICONTROL 표시]** 목록은 댓글 및 워크플로우만 볼 수 있는 옵션을 제공합니다. 또한 타임라인은 콘솔에 나열된 최상위 수준의 컬렉션에 대해서만 표시됩니다. 컬렉션 내에서 탐색하는 경우에는 표시되지 않습니다.

>[!NOTE]
>
>타임라인에는 컨텐츠 조각에 [](content-fragments/content-fragments.md)관련된 몇 가지 옵션이 있습니다.

## 주석 달기 {#annotating}

주석은 이미지나 비디오에 추가된 설명 또는 설명서입니다. 주석을 통해 마케터는 공동 작업을 수행하고 에셋에 대한 피드백을 남길 수 있습니다.

비디오 주석은 HTML5 호환 비디오 포맷이 있는 브라우저에서만 지원됩니다. AEM 자산에서 지원하는 비디오 형식은 브라우저에 따라 다릅니다.

>[!NOTE]
>
>컨텐츠 조각의 경우 [주석이 조각 편집기에서](content-fragments/content-fragments.md)생성됩니다.

1. 주석을 추가할 자산의 위치로 이동합니다.
1. 다음 중 하나에서 **[!UICONTROL 주석]** 아이콘을 탭/클릭합니다.

   * [빠른 작업](#quick-actions)
   * 자산을 선택하거나 자산 페이지로 이동한 후 도구 모음에서
   ![chlimage_1-233](assets/chlimage_1-233.png)

1. 타임라인 아래쪽에 있는 **[!UICONTROL [주석]** ] 상자에 주석을 추가합니다. 또는 이미지의 영역을 마크업하고 주석 추가 **[!UICONTROL 대화 상자에서 주석을]** 추가합니다.

   ![chlimage_1-234](assets/chlimage_1-234.png)

<!--
1. To notify a user about an annotation, specify the email address of the user and add the comment. For example, to notify Aaron MacDonald about an annotation, enter @aa. Hints for all matching users is displayed in a list. Select Aaron's email address from the list to tag her with the comment. Similarly, you can tag more users anywhere within the annotation or before or after it.

   >[!NOTE]
   >
   >For a non-administrator user, suggestions appear only if the user has Read permissions at `/home` in CRXDE.

   ![chlimage_1-235](assets/chlimage_1-235.png)

1. After adding the annotation, click **[!UICONTROL Add]** to save it. A notification for the annotation is sent to Aaron.

   ![chlimage_1-236](assets/chlimage_1-236.png)

   >[!NOTE]
   >
   >You can add multiple annotations, before you save them.

1. Tap/click **[!UICONTROL Close]** to exit from the Annotation mode.
1. To view the notification, log in to AEM Assets with Aaron MacDonald's credentials and click the **[!UICONTROL Notifications]** icon to view the notification.

   >[!NOTE]
   >
   >Annotations can also be added to video assets. While annotating videos, the player pauses to let you annotate on a frame. For details, see [managing video assets](manage-video-assets.md).

1. To choose a different color so you can differentiate between users, click/tap the Profile icon and click/tap **[!UICONTROL My Preferences]**.

   ![chlimage_1-237](assets/chlimage_1-237.png)

   Specify the desired color in the **[!UICONTROL Annotation Color]** box and then click/tap **[!UICONTROL Accept]**.

   ![chlimage_1-238](assets/chlimage_1-238.png)

>[!NOTE]
>
>You can also add annotations to a collection. However, if a collection contains child collections, you can add annotations/comments to the parent collection only. The Annotate option is not available for child collections.

### View saved annotations {#viewing-saved-annotations}

1. To view saved annotations for an asset, navigate to the location of the asset and open the asset page for the asset.

1. Tap/click the GlobalNav icon, and choose **[!UICONTROL Timeline]** from the list.

   ![chlimage_1-239](assets/chlimage_1-239.png)

1. From the **[!UICONTROL Show All]** list in the timeline, select **[!UICONTROL Comments]** to filter the results based on annotations.

   ![chlimage_1-240](assets/chlimage_1-240.png)

   Tap/click a comment in the **[!UICONTROL Timeline]** panel to view the corresponding annotation on the image.

   ![chlimage_1-241](assets/chlimage_1-241.png)

   Tap/click **[!UICONTROL Delete]**, to delete a particular comment.

### Print annotations {#printing-annotations}

If an asset has annotations or it has been subjected to a review workflow, you can print the asset along with annotations and review status as a PDF file for offline review.

You can also choose to print only the annotations or review status.

To print the annotations and review status, tap/click the **[!UICONTROL Print]** icon and follow the instructions in the wizard. The **[!UICONTROL Print]** icon appears in the toolbar only when the asset has at least one annotation or review status assigned to it.

1. From the Assets UI, open the preview page for an asset.
1. Do one of the following:

    * To print all the annotations and the review status, skip step 3 and directly go to step 4.
    * To print specific annotations and review status, open the [timeline](/help/assets/manage-digital-assets.md#timeline) and then go to step 3.

1. To print specific annotations, select the annotations from the timeline.

   ![chlimage_1-242](assets/chlimage_1-242.png)

   To print the review status only, select it from the timeline.

   ![chlimage_1-243](assets/chlimage_1-243.png)

1. Tap/click the **[!UICONTROL Print]** icon from the toolbar.

   ![chlimage_1-244](assets/chlimage_1-244.png)

1. From the Print dialog, choose the position you want the annotations/review status to be displayed on the PDF. For example, if you want the annotations/status to be printed at the top-right of the page that contains the printed image, use the **Top-Left** setting. It is selected by default.

   ![chlimage_1-245](assets/chlimage_1-245.png)

   You can choose other settings depending on the position where you want the annotations/status to appear in the printed PDF. If you want the annotations/status to appear in a page that is separate from the printed asset, choose **[!UICONTROL Next Page]**.

   >[!NOTE]
   >
   >Lengthy annotations may not render properly in the PDF file. For optimal rendering, Adobe recommends that you limit annotations to 50 words.

1. Tap/click **[!UICONTROL Print]**. Depending upon the option you choose in step 2, the generated PDF displays the annotations/status at the specified position. For example, if you choose to print both annotations and the review status using the **Top-Left** setting, the generated output resembles the PDF file depicted here.

   ![chlimage_1-246](assets/chlimage_1-246.png)

1. Download or print the PDF using the options at the top-right.

   ![chlimage_1-247](assets/chlimage_1-247.png)

   To modify the appearance of the rendered PDF file, for example the font color, size, and style, background color of the comments and statuses, open the **[!UICONTROL Annotation PDF configuration]** from Configuration Manager, and modify the desired options. For example, to change the display color of the approved status, modify the color code in the corresponding field. For information around changing the font color of annotations, see [Annotating](/help/assets/manage-digital-assets.md#annotating).

   ![chlimage_1-248](assets/chlimage_1-248.png)

   Return to the rendered PDF file and refresh it. The refreshed PDF reflects the changes you made.

## Asset versioning {#asset-versioning}

Versioning creates a snapshot of digital assets at a specific point in time. Versioning helps restore assets to a previous state at a later time. For example, if you want to undo a change that you made to an asset, restore the unedited version of the asset.

The following are scenarios where you create versions:

* You modify an image in a different application and upload to AEM Assets. A version of the image is created so your original image is not overwritten.
* You edit the metadata of an asset.
* You use AEM desktop app to checkout an existing asset and save your changes. A new version is created everytime the asset is saved.

You can also enable automatic versioning through a workflow. When you create a version for an asset, the metadata and renditions are saved along with the version. Renditions are rendered alternatives of the same images, for example, a PNG rendition of an uploaded JPEG file.

The versioning functionality lets you do the following:

* Create a version of an asset.
* View the current revision for an asset.
* Restore the asset to a previous version.

1. Navigate to the location of the asset for which you want to create a version, and tap/click it to open its asset page.

1. Tap/click the GlobalNav icon, and the choose **[!UICONTROL Timeline]** from the menu.

   ![timeline](assets/timeline.png)

1. Tap/click the **[!UICONTROL Actions]** (arrow) icon at the bottom to view the available actions you can perform on the asset.

   ![chlimage_1-249](assets/chlimage_1-249.png)

1. Tap/click **[!UICONTROL Save as Version]** to create a version for the asset.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Add a label and comment, and then click **[!UICONTROL Create]** to create a version. Alternatively, tap/click **Cancel** to exit the operation.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. To view the new version, open the **[!UICONTROL Show All]** list in the timeline from the asset details page or the Assets UI, and choose **[!UICONTROL Versions]**. All versions created for an asset are listed under the timeline tab. You can filter the list to show Versions, by clicking the drop arrow and selecting **[!UICONTROL Versions]** from the list.

   ![versions_option](assets/versions_option.png)

1. Select a specific version for the asset to preview it or enable it to appear in the Assets UI.

   ![select_version](assets/select_version.png)

1. Add a label and comment for the version to revert to the particular version in the Assets UI.

   ![save_version](assets/save_version.png)

1. To generate a preview for the version, tap/click **[!UICONTROL Preview Version]**.
1. To display this version in the Assets UI, select **[!UICONTROL Revert to this Version]**.
1. To compare between two versions, go to asset page of the asset and tap/click the version to be compared with the current version.

   ![select_version_tocompare](assets/select_version_tocompare.png)

1. From the timeline, select the version you want to compare and drag the slider to the left to superimpose this version over the current version and compare.

   ![compare_versions](assets/compare_versions.png)

### Starte a workflow on an asset {#starting-a-workflow-on-an-asset}

1. Navigate to the location of the asset for which you want to start a workflow, and tap/click the asset to open the asset page.
1. Tap/click the GlobalNav icon, and the choose **[!UICONTROL Timeline]** from the menu to display the timeline.

   ![timeline-1](assets/timeline-1.png)

1. Tap/click the **[!UICONTROL Actions]** (arrow) icon at the bottom to open the list of actions available for the asset.

   ![chlimage_1-252](assets/chlimage_1-252.png)

1. Tap/click **[!UICONTROL Start Workflow]** from the list.

   ![chlimage_1-253](assets/chlimage_1-253.png)

1. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. (Optional) Specify a title for the workflow, which can be used to reference the workflow instance.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Tap/click **[!UICONTROL Start]** and then tap/click **[!UICONTROL Proceed]** in the dialog to confirm. Each step of workflow is displayed in the timeline as an event.

   ![chlimage_1-256](assets/chlimage_1-256.png)

## Collections {#collections}

A collection is an ordered set of assets. Use collections to share assets between users.

* A collection can include assets from different locations because they only contain references to these assets. Each collection maintains the referential integrity of assets.
* You can share collections with multiple users with different privilege levels, including editing, viewing, and so on.

See [Managing Collections](/help/assets/manage-collections.md) for details on collection management.
