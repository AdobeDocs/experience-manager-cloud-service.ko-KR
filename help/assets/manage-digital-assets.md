---
title: 디지털 에셋 관리
description: 다양한 자산 관리 및 편집 방법에 대해 알아봅니다
contentOwner: AG
mini-toc-levels: 3
feature: Asset Management,Publishing,Collaboration,Asset Processing
role: User,Architect,Admin
exl-id: 51a26764-ac2b-4225-8d27-42a7fd906183
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '4356'
ht-degree: 11%

---

# 에셋 관리 {#manage-assets}

이 문서에서는 [!DNL Adobe Experience Manager Assets]. 관리하려면 [!DNL Content Fragments]를 참조하십시오. [[!DNL Content Fragments]](content-fragments/content-fragments.md) 자산.

## 폴더 만들기 {#creating-folders}

자산 컬렉션을 구성할 때(예: 모두) `Nature` 이미지를 만들 수 있습니다. 폴더를 사용하여 자산을 분류하고 구성할 수 있습니다. [!DNL Experience Manager Assets] 가 더 잘 작동하도록 하려면 폴더에서 자산을 구성할 필요가 없습니다.

>[!NOTE]
>
>* 유형의 자산 폴더 공유 `sling:OrderedFolder`은 Experience Cloud에 공유할 때 지원되지 않습니다. 폴더를 공유하려면 선택하지 마십시오 [!UICONTROL 주문] 폴더를 만들 때.
>* Experience Manager이 사용을 허용하지 않음 `subassets` 폴더 이름으로 word를 지정합니다. 복합 자산에 대한 하위 자산을 포함하는 노드에 예약된 키워드입니다


1. 새 폴더를 만들 디지털 자산 폴더의 위치로 이동합니다. 메뉴에서 **[!UICONTROL 만들기]**. 선택 **[!UICONTROL 새 폴더]**.
1. 에서 **[!UICONTROL 제목]** 필드에서 폴더 이름을 입력합니다. 기본적으로 DAM은 폴더 이름으로 제공한 제목을 사용합니다. 폴더를 만들면 기본값을 무시하고 다른 폴더 이름을 지정할 수 있습니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 폴더가 디지털 자산 폴더에 표시됩니다.

다음(공백으로 구분된 목록) 문자는 지원되지 않습니다.

* 자산 파일 이름에는 다음 문자를 사용할 수 없습니다. `* / : [ \\ ] | # % { } ? &`
* 자산 폴더 이름에는 다음 문자를 사용할 수 없습니다. `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## 에셋 업로드 {#uploading-assets}

자세한 내용은 [Experience Manager에 디지털 자산 추가](add-assets.md).

## 중복 자산 검색 {#detect-duplicate-assets}

<!-- TBD: This feature may not work as documented. See CQ-4283718. Get PM review done. -->

DAM 사용자가 저장소에 이미 있는 자산을 한 개 이상 업로드하는 경우, [!DNL Experience Manager] 중복을 감지하고 사용자에게 알립니다. 중복 감지는 저장소 크기 및 업로드된 자산 수에 따라 성능에 영향을 줄 수 있으므로 기본적으로 비활성화됩니다.

기능을 활성화하려면

1. 다음으로 이동 **[!UICONTROL 도구 > 자산 > 자산 구성]**.

1. 클릭 **[!UICONTROL 자산 중복 감지 장치]**.

1. 설정 [!UICONTROL 자산 중복 감지 페이지]를 클릭합니다. **[!UICONTROL 활성화됨]**.

   `dam:sha1` 메타데이터 검색 필드의 값은 파일 이름이 다르더라도 중복 자산을 검색하도록 합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![에셋 중복 감지기](assets/asset-duplication-detector.png)

>[!NOTE]
>
>복제 탐지기를 `/apps/example/config.author/com.adobe.cq.assetcompute.impl.assetprocessor.AssetDuplicationDetector.cfg.json` 구성 파일(OSGi 구성)은 계속 사용할 수 있지만 Adobe은 새 메서드를 사용하는 것이 좋습니다.


활성화되면 Experience Manager이 중복 자산의 알림을 Experience Manager 받은 편지함에 보냅니다. 여러 중복에 대해 집계된 결과입니다. 사용자는 결과를 기반으로 자산을 제거하도록 선택할 수 있습니다.

![중복 자산에 대한 받은 편지함 알림](assets/duplicate-detect-inbox-notification.png)

>[!NOTE]
>
>자산을 저장소에 업로드하면 Experience Manager이 중복을 감지하고 처음 100개의 중복 자산에 대해 알려줍니다.

## 에셋 미리보기 {#previewing-assets}

자산을 미리 보려면 다음 단계를 수행합니다.

1. 자산 사용자 인터페이스에서 미리 보려는 자산의 위치로 이동합니다.
1. 원하는 자산을 탭하여 엽니다.

1. 미리 보기 모드에서 확대/축소 옵션을 사용할 수 있습니다 [지원되는 이미지 유형](/help/assets/file-format-support.md) (대화형 편집 사용).

   자산을 확대하려면 탭/클릭합니다 `+` (또는 자산에서 돋보기를 탭/클릭합니다.) 축소하려면 탭/클릭합니다 `-`. 확대하면 패닝하여 이미지의 모든 영역을 자세히 볼 수 있습니다. 확대/축소 재설정 화살표는 원래 보기로 돌아갑니다.

   탭 **[!UICONTROL 재설정]** 보기를 원래 크기로 재설정하려면 다음을 수행하십시오.

## 속성 편집 {#editing-properties}

1. 메타데이터를 편집할 자산의 위치로 이동합니다.

1. 자산을 선택하고 탭/클릭합니다 **[!UICONTROL 속성]** 도구 모음에서 자산 속성 보기 또는 을(를) 선택합니다 **[!UICONTROL 속성]** 자산 카드의 빠른 작업.

   ![properties_quickaction](assets/properties_quickaction.png)

1. 에서 [!UICONTROL 속성] 페이지에서 다양한 탭에서 메타데이터 속성을 편집합니다. 예를 들어 **[!UICONTROL 기본]** 탭에서 제목, 설명 등을 편집합니다.

   >[!NOTE]
   >
   >의 레이아웃 [!UICONTROL 속성] 페이지 및 사용 가능한 메타데이터 속성은 기본 메타데이터 스키마에 따라 다릅니다. 레이아웃을 수정하는 방법을 배우려면 [!UICONTROL 속성] 페이지를 참조하십시오. [메타데이터 스키마](/help/assets/metadata-schemas.md).

1. To schedule a particular date/time for the activation of the asset, use the date picker beside the **[!UICONTROL On Time]** field.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. 특정 기간 후에 자산을 비활성화하려면 다음 항목 옆의 날짜 선택기에서 비활성화 날짜/시간을 선택합니다 **[!UICONTROL 해제 시간]** 필드. 비활성화 날짜는 자산의 활성화 날짜보다 이후여야 합니다. 다음 이후 [!UICONTROL 해제 시간], 자산 및 해당 표현물은 Assets 웹 인터페이스 또는 HTTP API를 통해 사용할 수 없습니다.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. 에서 **[!UICONTROL 태그]** 필드에서 하나 이상의 태그를 선택합니다. 사용자 지정 태그를 추가하려면 상자에 태그 이름을 입력하고 `Enter` 키. 새 태그가에 저장됩니다. [!DNL Experience Manager].

   YouTube을 게시하려면 태그가 필요하며 YouTube에 대한 링크가 있어야 합니다(적절한 링크를 찾을 수 있는 경우).

   >[!NOTE]
   >
   >태그를 만들려면 다음에 쓰기 권한이 있어야 합니다. `/content/cq:tags/default` CRX 저장소의 경로입니다.

1. 탭/클릭 **[!UICONTROL 저장 및 닫기]**.

1. 자산 사용자 인터페이스로 이동합니다. 제목, 설명 및 태그를 포함한 편집된 메타데이터 속성은 카드 보기의 자산 카드 및 목록 보기의 관련 열 아래에 표시됩니다.

<!-- TBD: Uncomment after verification for Dec release.

## View asset usage and references {#usage-and-references}

[!DNL Experience Manager] lets you track statistics about usage of a digital asset. The usage statistics include the following:

    * Number of times the asset was viewed or downloaded
    * Channels/devices through which the asset was used
    * Creative solutions where the asset was recently used

To view usage statistics for an asset, in the [!UICONTROL Properties] page, click the **[!UICONTROL Insights]** tab. For more details, see [Assets Insights](assets-insights.md).

[!DNL Experience Manager] also lets you check all the incoming references to an asset, that is, the usage of an asset in remote [!DNL Sites] and in compound assets. Authors of webpages on [!DNL Experience Manager Sites] deployment can use an asset on a remote [!DNL Assets] deployment using the Connected Assets functionality. The [!UICONTROL References] tab in an asset's [!UICONTROL Properties] page lists the local and remote references of the asset. That is, the use of assets in compound assets in [!DNL Assets] and its use in remote [!DNL Sites] pages.

-->

## 에셋 복사 {#copying-assets}

자산 또는 폴더를 복사하면 전체 자산 또는 폴더가 해당 컨텐츠 구조와 함께 복사됩니다. 복사된 자산 또는 폴더는 대상 위치에 복제됩니다. 소스 위치의 자산은 변경되지 않습니다.

특정 자산 사본에 고유한 몇 가지 속성은 전달되지 않습니다. 예를 들면 다음과 같습니다.

* 자산 ID, 생성 날짜 및 시간, 버전 및 버전 내역. 이러한 속성 중 일부는 속성으로 표시됩니다 `jcr:uuid`, `jcr:created`, 및 `cq:name`.

* 작성 시간 및 참조된 경로는 각 자산 및 해당 표현물에 대해 고유합니다.

다른 속성 및 메타데이터 정보는 유지됩니다. 자산을 복사할 때 부분 복사본이 만들어지지 않습니다.

1. Assets UI에서 자산을 한 개 이상 선택한 다음, **[!UICONTROL 복사]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다. 또는 을(를) 선택합니다 **[!UICONTROL 복사]** ![copy_icon](assets/copy_icon.png) 자산 카드에서 빠른 작업 을 참조하십시오.

   >[!NOTE]
   >
   >를 사용하는 경우 [!UICONTROL 복사] 빠른 작업, 한 번에 하나의 자산만 복사할 수 있습니다.

1. 자산을 복사할 위치로 이동합니다.

   >[!NOTE]
   >
   >자산을 같은 위치에 복사하는 경우 [!DNL Experience Manager] 변형된 이름을 자동으로 생성합니다. 예를 들어, 라는 이름의 자산을 복사하는 경우 `Square`, [!DNL Experience Manager] 복사본 제목을 자동으로 생성 `Square1`.

1. 을(를) 클릭합니다. **[!UICONTROL 붙여넣기]** 도구 모음의 자산 아이콘. 자산이 이 위치에 복사됩니다.

   ![chlimage_1-219](assets/chlimage_1-219.png)

   >[!NOTE]
   >
   >다음 **[!UICONTROL 붙여넣기]** 아이콘은 붙여넣기 작업이 완료될 때까지 도구 모음에서 사용할 수 있습니다.

### 자산 이동 또는 이름 변경 {#moving-or-renaming-assets}

1. 이동할 자산의 위치로 이동합니다.

1. 자산을 선택하고 자산을 탭/클릭합니다. **[!UICONTROL 이동]** 아이콘 ![move_icon](assets/move_icon.png) 를 클릭합니다.

1. 자산 이동 마법사에서 다음 중 하나를 수행합니다.

   * 자산을 이동한 후 자산의 이름을 지정합니다. 그런 다음 탭/클릭합니다 **[!UICONTROL 다음]** 계속 진행합니다.

   * 탭/클릭 **[!UICONTROL 취소]** 프로세스를 중지합니다.
   >[!NOTE]
   >
   >* 새 위치에 해당 이름의 자산이 없는 경우 자산에 대해 동일한 이름을 지정할 수 있습니다. 하지만 자산을 동일한 이름의 자산이 있는 위치로 이동하는 경우 다른 이름을 사용해야 합니다. 동일한 이름을 사용하는 경우 변형된 이름이 자동으로 생성됩니다. 예를 들어, 자산의 이름이 Square인 경우, 시스템은 해당 사본의 이름 Square1을 생성합니다.
   >* 이름을 바꿀 때 파일 이름에 공백을 사용할 수 없습니다.


1. 설정 **[!UICONTROL 대상 선택]** 대화 상자에서 다음 중 하나를 수행합니다.

   * 자산의 새 위치로 이동한 후 탭/클릭합니다 **[!UICONTROL 다음]** 계속 진행합니다.

   * 탭/클릭 **[!UICONTROL 뒤로]** 로 돌아가기 **[!UICONTROL 이름 변경]** 화면.

1. 이동되는 자산에 참조 페이지, 자산 또는 컬렉션이 있는 경우, **[!UICONTROL 참조 조정]** 탭 옆에 표시됩니다 **[!UICONTROL 대상 선택]** 탭.

   에서 다음 중 하나를 수행합니다 **[!UICONTROL 참조 조정]** 화면:

   * 새 세부 사항을 기반으로 조정할 참조를 지정한 다음 탭/클릭합니다 **[!UICONTROL 이동]** 계속 진행합니다.

   * 에서 **[!UICONTROL 조정]** 열에서 자산에 대한 참조를 선택/선택 취소합니다.
   * 탭/클릭 **[!UICONTROL 뒤로]** 로 돌아가기 **[!UICONTROL 대상 선택]** 화면.

   * 탭/클릭 **[!UICONTROL 취소]** 이동 작업을 중지하려면 다음을 수행하십시오.

   참조를 업데이트하지 않으면 이 참조는 자산의 이전 경로를 계속 가리킵니다. 참조를 조정하면 새 자산 경로로 업데이트됩니다.

### 표현물 관리 {#managing-renditions}

1. 원본을 제외하고 자산에 대한 표현물을 추가하거나 제거할 수 있습니다. 표현물을 추가하거나 제거할 자산의 위치로 이동합니다.

1. 자산을 탭/클릭하여 자산 페이지를 엽니다.

   ![chlimage_1-220](assets/chlimage_1-220.png)

1. GlobalNav 아이콘을 탭/클릭하고 을 선택합니다 **[!UICONTROL 표현물]** 참조하십시오.

   ![renditions_menu](assets/renditions_menu.png)

1. 에서 **[!UICONTROL 표현물]** 패널에서 자산에 대해 생성된 표현물 목록을 확인합니다.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >기본적으로 [!DNL Experience Manager Assets] 미리 보기 모드에서는 자산의 원래 표현물이 표시되지 않습니다. 관리자는 오버레이를 사용하여 다음을 구성할 수 있습니다 [!DNL Assets] 를 클릭하여 미리 보기 모드에서 원래 렌디션을 표시합니다.

1. 변환을 보거나 삭제할 변환을 선택합니다.

   **표현물 삭제**

   에서 렌디션을 선택합니다 **[!UICONTROL 표현물]** 패널, 탭/클릭 **[!UICONTROL 표현물 삭제]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다. 자산 처리가 완료된 후에는 렌디션을 일괄적으로 삭제할 수 없습니다. 개별 자산의 경우 사용자 인터페이스에서 렌디션을 수동으로 제거할 수 있습니다. 여러 자산의 경우 사용자 지정할 수 있습니다 [!DNL Experience Manager] 특정 표현물을 삭제하거나 자산을 삭제하고 삭제된 자산을 다시 업로드하려면 다음을 수행하십시오.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **새 변환 업로드**

   Navigate to the asset details page for the asset, and tap/click the **[!UICONTROL Add Rendition]** icon in the toolbar to upload a new rendition for the asset.

   ![chlimage_1-221](assets/chlimage_1-221.png)

   >[!NOTE]
   >
   >If you select a rendition from the **[!UICONTROL Renditions]** panel, the toolbar changes context and displays only those actions that are relevant to the rendition. Options, such as the Upload Rendition icon is not displayed. To view these options in the toolbar, navigate to the details page for the asset.

   이미지 또는 비디오 자산의 세부 사항 페이지에 표시할 표현물에 대한 차원을 구성할 수 있습니다. 지정하는 차원에 따라 Assets에 정확히 일치하거나 가장 가까운 차원이 있는 표현물이 표시됩니다.

   To configure rendition dimensions of an image at the asset detail level, overlay the `renditionpicker` node (`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`) and configure the value of the width property. Configure the property **[!UICONTROL size (Long) in KB]** in place of width to customize rendition on asset detail page based on image size. For size-based customization, the property `preferOriginal` assigns preference to the original if the size of the matched rendition is greater than the original.

   마찬가지로 오버레이하여 주석 페이지 이미지를 사용자 지정할 수 있습니다 `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`.

   ![chlimage_1-222](assets/chlimage_1-222.png)

   비디오 자산에 대한 표현물 차원을 구성하려면 다음 위치로 이동합니다 `videopicker` 노드 아래의 CRX 저장소에 있는 `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`를 오버레이한 다음 해당 속성을 편집합니다.

   >[!NOTE]
   >
   >비디오 주석은 HTML5 호환 비디오 형식이 있는 브라우저에서만 지원됩니다. 또한 브라우저에 따라 다른 비디오 형식이 지원됩니다. 그러나 MXF 비디오 형식은 아직 비디오 주석에서 지원되지 않습니다.

## 자산 삭제 {#delete-assets}

다른 페이지에서 들어오는 참조를 해결하거나 제거하려면 자산을 삭제하기 전에 관련 참조를 업데이트하십시오.

또한 오버레이를 사용하여 강제 삭제 단추를 비활성화하여 사용자가 참조된 자산을 삭제하고 끊어진 링크를 떠나지 못하도록 합니다.

1. 삭제할 자산의 위치로 이동합니다.

1. 자산을 선택하고 을(를) 클릭합니다 **[!UICONTROL 삭제]** ![delete_icon](assets/do-not-localize/delete-icon.png) 를 클릭합니다.

1. 확인 대화 상자에서 다음을 클릭합니다.

   * **[!UICONTROL 취소]** 작업을 중지하려면
   * **[!UICONTROL 삭제]** 작업을 확인하려면:

      * 자산에 참조가 없으면, 자산이 삭제됩니다.
      * 자산에 참조가 있으면, 오류 메시지에 다음 내용이 표시됩니다 **[!UICONTROL 하나 이상의 자산을 참조했습니다.]**. 선택할 수 있습니다 **[!UICONTROL 강제 삭제]** 또는 **[!UICONTROL 취소]**.

   >[!NOTE]
   >
   >자산을 삭제할 수 있으려면 dam/asset에 대한 삭제 권한이 필요합니다. 수정 권한만 있는 경우 자산 메타데이터를 편집하고 자산에 주석을 추가할 수 있습니다. 하지만 자산이나 해당 메타데이터는 삭제할 수 없습니다.

   >[!NOTE]
   >
   >다른 페이지에서 들어오는 참조를 해결하거나 제거하려면 자산을 삭제하기 전에 관련 참조를 업데이트하십시오. 참조된 자산을 삭제하면 링크가 끊어지기 때문에 삭제를 취소할 수 없습니다. 오버레이를 사용하여 강제 삭제 단추를 비활성화합니다.

## 에셋 다운로드 {#download-assets}

자세한 내용은 [자산 다운로드 [!DNL Experience Manager]](/help/assets/download-assets-from-aem.md).

## 자산 게시 또는 게시 취소 {#publish-assets}

1. 게시하려는 자산 또는 게시 환경에서 제거하려는 자산 폴더의 위치(게시 취소)로 이동합니다.

1. 게시 또는 게시 취소할 자산 또는 폴더를 선택하고 을 선택합니다 **[!UICONTROL 게시 관리]** ![게시 관리 옵션](assets/do-not-localize/globe-publication.png) 옵션 을 클릭합니다. 또는 빠르게 게시하려면 **[!UICONTROL 빠른 게시]** 옵션 을 클릭합니다. 게시하려는 폴더에 빈 폴더가 포함되어 있으면 빈 폴더가 게시되지 않습니다.

1. 을(를) 선택합니다 **[!UICONTROL 게시]** 또는 **[!UICONTROL 게시 취소]** 선택 사항.

   ![게시 취소 작업](assets/unpublish_action.png)
   *그림: 게시 및 게시 취소 옵션 및 예약 옵션.*

1. 선택 **[!UICONTROL 지금]** 자산을 바로 사용하거나 **[!UICONTROL 나중에]** 를 눌러 작업을 예약합니다. 을(를) 선택하는 경우 날짜 및 시간을 선택합니다 **[!UICONTROL 나중에]** 선택 사항입니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. 게시할 때 자산이 다른 자산을 참조하는 경우 해당 참조가 마법사에 나열됩니다. 마지막 게시 이후 게시 취소되거나 수정된 참조만 표시됩니다. 게시할 참조를 선택합니다.

1. 게시를 취소할 때 자산이 다른 자산을 참조하는 경우 게시를 취소하려는 참조를 선택합니다. **[!UICONTROL 게시 취소]**&#x200B;를 클릭합니다. 확인 대화 상자에서 **[!UICONTROL 취소]** 작업을 중지하려면 를 클릭하거나 **[!UICONTROL 게시 취소]** 지정된 날짜에 자산의 게시를 취소할지 확인합니다.

자산 또는 폴더의 게시 또는 게시 취소와 관련된 다음 제한 사항과 팁을 이해합니다.

* 다음 옵션 [!UICONTROL 게시 관리] 복제 권한이 있는 사용자 계정에만 이 기능을 사용할 수 있습니다.
* 복잡한 자산의 게시를 취소하는 동안 자산만 게시 취소합니다. 게시된 다른 자산에서 참조될 수 있으므로 참조 게시를 취소하지 마십시오.
* 빈 폴더가 게시되지 않습니다.
* 처리 중인 자산을 게시하면 원래 컨텐츠만 게시됩니다. 표현물이 없습니다. 처리가 완료될 때까지 기다렸다가 처리가 완료되면 자산을 게시하거나 다시 게시하십시오.

## 폐쇄된 사용자 그룹 {#closed-user-group}

CUG(폐쇄된 사용자 그룹)를 사용하여 [!DNL Experience Manager]. 폴더에 대한 CUG를 만드는 경우 폴더(폴더 자산 및 하위 폴더 포함)에 대한 액세스가 할당된 구성원 또는 그룹으로만 제한됩니다. 폴더에 액세스하려면 보안 자격 증명을 사용하여 로그인해야 합니다.

CUG는 자산에 대한 액세스를 제한하는 추가 방법입니다. 폴더에 대한 로그인 페이지를 구성할 수도 있습니다.

1. 자산 UI에서 폴더를 선택하고 도구 모음에서 속성 아이콘을 탭/클릭하여 속성 페이지를 표시합니다.
1. 에서 **[!UICONTROL 권한]** 탭에서 **[!UICONTROL 폐쇄된 사용자 그룹]**.

   ![add_user](assets/add_user.png)

1. 사용자가 폴더에 액세스할 때 로그인 화면을 표시하려면 **[!UICONTROL 활성화]** 선택 사항입니다. 그런 다음 의 로그인 페이지 경로를 선택합니다 [!DNL Experience Manager], 그리고 변경 사항을 저장합니다.

   ![login_page](assets/login_page.png)

   >[!NOTE]
   >
   >로그인 페이지의 경로를 지정하지 않으면 [!DNL Experience Manager] 게시 인스턴스에 기본 로그인 페이지를 표시합니다.

1. 폴더를 게시한 다음 게시 인스턴스에서 해당 폴더에 액세스해 보십시오. 로그인 화면이 표시됩니다.
1. CUG 멤버인 경우 보안 자격 증명을 입력합니다. 폴더는 다음에 표시됩니다 [!DNL Experience Manager] 인증을 받습니다.

## 에셋 검색 {#search-assets}

자산을 검색하는 것은 디지털 자산 관리 시스템의 용도의 핵심입니다. 이를 통해 크리에이티브, 비즈니스 사용자 및 마케터의 강력한 자산 관리 또는 DAM 관리자의 관리를 수행할 수 있습니다.

가장 적절한 자산을 검색하고 사용하기 위한 간단한 고급 및 사용자 지정 검색에 대해서는 를 참조하십시오. [의 자산 검색 [!DNL Experience Manager]](/help/assets/search-assets.md).

## 빠른 작업 {#quick-actions}

빠른 작업 아이콘은 한 번에 단일 자산에 사용할 수 있습니다. 장치에 따라 다음 작업을 수행하여 빠른 작업 아이콘을 표시합니다.

* 터치 장치: 길게 터치하세요. 예를 들어 iPad에서 자산을 길게 탭하여 빠른 작업이 표시됩니다.
* 비터치 장치: 포인터를 가져갑니다. 예를 들어, 데스크탑 장치에서 포인터를 자산 축소판 위에 두면 빠른 작업 모음이 표시됩니다.

<!-- Hiding this topic via cqdoc-18707

## Edit images {#editing-images}

The editing tools in the [!DNL Experience Manager Assets] interface let you perform small editing jobs on image assets. You can crop, rotate, flip, and perform other editing jobs on images. You can also add image maps to assets.

>[!NOTE]
>
>For some components, the Full Screen mode has additional options available.

1. Do one of the following to open an asset in edit mode:

    * Select the asset and then click/tap the **[!UICONTROL Edit]** icon in the toolbar.
    * Tap/click the **[!UICONTROL Edit]** icon that appears on an asset in the Card view.
    * In the asset page, tap/click the **[!UICONTROL Edit]** icon in the toolbar.

   ![edit_icon](assets/edit_icon.png)

1. To crop the image, tap/click the **Crop** icon.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. Select the desired option from the list. The crop area appears on the image based on the option you choose. The **Free Hand** option lets you crop the image without any aspect ratio restrictions.

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. Select the area to be cropped, and resize or reposition it on the image.
1. Use the **Finish** icon (top right corner) to crop the image. Clicking the **Finish** icon also triggers the regeneration of renditions.

   ![chlimage_1-228](assets/chlimage_1-228.png)

1. Use the **Undo** and **Redo** icons on the top right to revert to the uncropped image or retain the cropped image, respectively.

   ![chlimage_1-229](assets/chlimage_1-229.png)

1. Tap/click the appropriate Rotate icon to rotate the image clockwise or anti-clockwise.

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. Tap/click the appropriate Flip icon to flip the image horizontally or vertically.

   ![chlimage_1-231](assets/chlimage_1-231.png)

1. Tap/click the **Finish** icon to save the changes.

   ![chlimage_1-232](assets/chlimage_1-232.png)

>[!NOTE]
>
>Image editing is supported for BMP, GIF, PNG, and JPEG files formats.

>[!NOTE]
>
>To edit a TXT file, set **Day CQ Link Externalizer** from Configuration Manager.
-->

## 타임라인 {#timeline}

타임라인을 사용하면 자산에 대한 활성 워크플로우, 댓글/주석, 활동 로그 및 버전과 같은 선택한 항목에 대한 다양한 이벤트를 볼 수 있습니다.

![자산에 대한 타임라인 항목 정렬](assets/sort_timeline.gif)
*그림: 자산에 대한 타임라인 항목 정렬*

>[!NOTE]
>
>에서 [컬렉션 콘솔](/help/assets/manage-collections.md#navigate-the-collections-console), **[!UICONTROL 모두 표시]** 목록에는 댓글 및 워크플로우만 볼 수 있는 옵션이 있습니다. 또한 타임라인은 콘솔에 나열된 최상위 수준의 컬렉션에만 표시됩니다. 컬렉션 내부를 탐색하는 경우에는 표시되지 않습니다.

>[!NOTE]
>
>타임라인에 여러 항목이 포함되어 있습니다 [컨텐츠 조각별 옵션](content-fragments/content-fragments.md).

## 자산에 주석 달기 {#annotating}

주석은 이미지나 비디오에 추가된 주석 또는 설명 노트입니다. 주석은 마케터가 자산에 대한 공동 작업을 수행하고 피드백을 남길 수 있는 기능을 제공합니다.

비디오 주석은 HTML5 호환 비디오 형식이 있는 브라우저에서만 지원됩니다. Assets에서 지원하는 비디오 형식은 브라우저에 따라 다릅니다. 그러나 MXF 비디오 형식은 아직 비디오 주석에서 지원되지 않습니다.

>[!NOTE]
>
>컨텐츠 조각의 경우, [주석은 조각 편집기에서 작성됩니다](content-fragments/content-fragments.md).

1. 주석을 추가할 자산의 위치로 이동합니다.
1. 을 탭/클릭합니다. **[!UICONTROL 주석 달기]** 아이콘 사용:

   * [빠른 작업](#quick-actions)
   * 자산을 선택하거나 자산 페이지로 이동한 후 도구 모음에서

   ![chlimage_1-233](assets/chlimage_1-233.png)

1. Add a comment in the **[!UICONTROL Comment]** box at the bottom of the timeline. Alternatively, mark up an area on the image and add an annotation in the **[!UICONTROL Add Annotation]** dialog.

   ![chlimage_1-234](assets/chlimage_1-234.png)

<!--
1. To notify a user about an annotation, specify the email address of the user and add the comment. For example, to notify Aaron MacDonald about an annotation, enter @aa. Hints for all matching users is displayed in a list. Select Aaron's email address from the list to tag her with the comment. Similarly, you can tag more users anywhere within the annotation or before or after it.
-->

>[!NOTE]
>
>관리자가 아닌 사용자의 경우 사용자에게 읽기 권한이 있는 경우에만 제안이 표시됩니다. `/home` 입니다.

![chlimage_1-235](assets/chlimage_1-235.png)

1. 주석을 추가한 후 **[!UICONTROL 추가]** 저장하려고 노트에 대한 알림이 Aaron에게 전송됩니다.

   ![chlimage_1-236](assets/chlimage_1-236.png)

   >[!NOTE]
   >
   >주석을 저장하기 전에 여러 주석을 추가할 수 있습니다.

1. 탭/클릭 **[!UICONTROL 닫기]** 주석 모드를 종료하려면 다음을 수행하십시오.
1. 알림을 보려면 Aaron MacDonald의 자격 증명으로 Assets에 로그인하고 을 클릭합니다. **[!UICONTROL 알림 을 참조하십시오]** 아이콘을 클릭하여 알림을 볼 수 있습니다.

   >[!NOTE]
   >
   >비디오 자산에 주석을 추가할 수도 있습니다. 비디오에 주석을 추가하는 동안 플레이어는 프레임에 주석을 달 수 있도록 일시 중지합니다. 자세한 내용은 [비디오 자산 관리](manage-video-assets.md). 그러나 MXF 비디오 형식은 아직 비디오 주석에서 지원되지 않습니다.

1. 사용자를 구분하기 위해 다른 색상을 선택하려면 프로필 아이콘을 클릭/탭하고 클릭/탭합니다 **[!UICONTROL 내 환경 설정]**.

   ![chlimage_1-237](assets/chlimage_1-237.png)

   Specify the desired color in the **[!UICONTROL Annotation Color]** box and then click/tap **[!UICONTROL Accept]**.

   ![chlimage_1-238](assets/chlimage_1-238.png)

>[!NOTE]
>
>컬렉션에 주석을 추가할 수도 있습니다. 그러나 컬렉션에 하위 컬렉션이 포함되어 있으면 상위 컬렉션에만 주석/주석을 추가할 수 있습니다. 하위 컬렉션에는 주석 옵션을 사용할 수 없습니다.

### 저장된 주석 보기 {#viewing-saved-annotations}

주석을 한 번에 하나씩만 볼 수 있습니다.

>[!NOTE]
>
>여러 주석을 선택하는 경우 사용자 인터페이스에 최신 주석이 표시됩니다.
>
>다중 선택은 주석 처리된 자산을 PDF으로 인쇄하기 위해서만 지원됩니다.

1. 자산에 대해 저장된 주석을 보려면 자산의 위치로 이동하고 자산의 자산 페이지를 엽니다.

1. GlobalNav 아이콘을 탭/클릭하고 **[!UICONTROL 타임라인]** 참조하십시오.

   ![chlimage_1-239](assets/chlimage_1-239.png)

1. From the **[!UICONTROL Show All]** list in the timeline, select **[!UICONTROL Comments]** to filter the results based on annotations.

   ![chlimage_1-240](assets/chlimage_1-240.png)

   에서 댓글 탭/클릭 **[!UICONTROL 타임라인]** 패널에서 이미지에 해당하는 주석을 볼 수 있습니다.

   ![chlimage_1-241](assets/chlimage_1-241.png)

   탭/클릭 **[!UICONTROL 삭제]**&#x200B;를 눌러 특정 설명을 삭제합니다.

### 주석 인쇄 {#printing-annotations}

자산에 주석이 있거나 검토 워크플로우가 있었던 경우, 오프라인 검토를 위해 PDF 파일로 주석 및 검토 상태와 함께 자산을 인쇄할 수 있습니다.

주석이나 검토 상태만 인쇄하도록 선택할 수도 있습니다.

>[!NOTE]
>
>주석 처리된 자산을 PDF으로 인쇄하는 동안 여러 주석을 선택할 수 있습니다.

주석 및 검토 상태를 인쇄하려면 **[!UICONTROL 인쇄]** 아이콘을 클릭하고 마법사의 지침을 따릅니다. 다음 **[!UICONTROL 인쇄]** 아이콘이 자산에 하나 이상의 주석 또는 검토 상태가 지정된 경우에만 도구 모음에 표시됩니다.

1. 자산 UI에서 자산에 대한 미리 보기 페이지를 엽니다.
1. 다음 중 하나를 수행하십시오.

   * 모든 주석 및 검토 상태를 인쇄하려면 3단계를 건너뛰고 4단계로 바로 이동합니다.
   * 특정 주석을 인쇄하고 상태를 검토하려면 [타임라인](/help/assets/manage-digital-assets.md#timeline) 그리고 3단계로 가십시오.

1. 특정 주석을 인쇄하려면 타임라인에서 주석을 선택합니다.

   ![chlimage_1-242](assets/chlimage_1-242.png)

   검토 상태만 인쇄하려면 타임라인에서 선택합니다.

   ![chlimage_1-243](assets/chlimage_1-243.png)

1. 을 탭/클릭합니다. **[!UICONTROL 인쇄]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.

   ![chlimage_1-244](assets/chlimage_1-244.png)

1. 인쇄 대화 상자에서 PDF에 주석/검토 상태를 표시할 위치를 선택합니다. 예를 들어, 인쇄된 이미지가 포함된 페이지의 오른쪽 상단에 주석/상태를 인쇄하려면 **왼쪽 위** 설정 기본적으로 선택됩니다.

   ![chlimage_1-245](assets/chlimage_1-245.png)

   You can choose other settings depending on the position where you want the annotations/status to appear in the printed PDF. If you want the annotations/status to appear in a page that is separate from the printed asset, choose **[!UICONTROL Next Page]**.

1. 클릭 **[!UICONTROL 인쇄]**. Depending upon the option you choose in step 2, the generated PDF displays the annotations/status at the specified position. For example, if you choose to print both annotations and the review status using the **Top-Left** setting, the generated output resembles the PDF file depicted here.

   ![chlimage_1-246](assets/chlimage_1-246.png)

1. 오른쪽 상단의 옵션을 사용하여 PDF을 다운로드하거나 인쇄합니다.

   ![chlimage_1-247](assets/chlimage_1-247.png)

   렌더링된 PDF 파일의 모양(예: 글꼴 색상, 크기 및 스타일, 주석 및 상태의 배경색)을 수정하려면 **[!UICONTROL 주석 PDF 구성]** 구성 관리자에서 원하는 옵션을 수정합니다. 예를 들어, 승인됨 상태의 표시 색상을 변경하려면 해당 필드에서 색상 코드를 수정합니다. 주석의 글꼴 색상 변경에 대한 자세한 내용은 [주석 달기](/help/assets/manage-digital-assets.md#annotating).

   렌더링된 PDF 파일로 돌아가서 새로 고칩니다. 새로 고친 PDF은 사용자가 변경한 내용을 반영합니다.

## 에셋 버전 관리 {#asset-versioning}

버전 매기기를 통해 특정 시점의 디지털 자산 스냅샷을 만들 수 있습니다. 버전 관리를 사용하면 나중에 자산을 이전 상태로 복원할 수 있습니다. 예를 들어, 자산에 대한 변경 사항을 실행 취소하려면, 편집되지 않은 버전의 자산을 복원합니다.

다음은 버전을 만드는 시나리오입니다.

* 다른 애플리케이션에서 이미지를 수정하고 자산에 업로드합니다. 이미지의 버전이 만들어지므로 원본 이미지를 덮어쓰지 않습니다.
* 자산의 메타데이터를 편집합니다.
* 사용 [!DNL Experience Manager] 기존 자산을 체크아웃하고 변경 사항을 저장하는 데스크탑 앱. 자산이 저장될 때마다 새 버전이 만들어집니다.

워크플로우를 통해 자동 버전 지정을 활성화할 수도 있습니다. 자산에 대한 버전을 만들면 메타데이터 및 표현물이 버전과 함께 저장됩니다. 표현물은 동일한 이미지의 대체 요소(예: 업로드된 JPEG 파일의 PNG 표현물)로 렌더링됩니다.

버전 관리 기능을 사용하면 다음을 수행할 수 있습니다.

* 자산의 버전을 만듭니다.
* 자산에 대한 현재 개정을 확인합니다.
* 자산을 이전 버전으로 복원합니다.

1. 버전을 만들 자산의 위치로 이동하고, 해당 자산 페이지를 열려면 해당 자산을 탭/클릭합니다.

1. GlobalNav 아이콘을 탭/클릭하고 **[!UICONTROL 타임라인]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![타임라인](assets/timeline.png)

1. 을 탭/클릭합니다. **[!UICONTROL 작업]** 맨 아래에 있는 (화살표) 아이콘을 클릭하여 자산에서 수행할 수 있는 사용 가능한 작업을 확인합니다.

   ![chlimage_1-249](assets/chlimage_1-249.png)

1. 탭/클릭 **[!UICONTROL 다른 버전으로 저장]** 를 입력하여 자산의 버전을 만들 수 있습니다.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. 레이블과 주석을 추가한 다음 **[!UICONTROL 만들기]** 버전을 만들려면 또는 탭/클릭합니다 **취소** 를 눌러 작업을 종료합니다.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. To view the new version, open the **[!UICONTROL Show All]** list in the timeline from the asset details page or the Assets UI, and choose **[!UICONTROL Versions]**. All versions created for an asset are listed under the timeline tab. You can filter the list to show Versions, by clicking the drop arrow and selecting **[!UICONTROL Versions]** from the list.

   ![version_option](assets/versions_option.png)

1. 자산을 미리 볼 특정 버전을 선택하거나 자산 UI에 표시되도록 설정합니다.

   ![select_version](assets/select_version.png)

1. 버전에 대한 레이블과 설명을 추가하여 Assets UI의 특정 버전으로 되돌립니다.

   ![save_version](assets/save_version.png)

1. To generate a preview for the version, tap/click **[!UICONTROL Preview Version]**.
1. 자산 UI에 이 버전을 표시하려면 **[!UICONTROL 이 버전으로 되돌리기]**.
1. 두 버전 간에 비교하려면 자산의 자산 페이지로 이동한 후 현재 버전과 비교할 버전을 탭/클릭합니다.

   ![select_version_tocompare](assets/select_version_tocompare.png)

1. 타임라인에서 비교할 버전을 선택하고 슬라이더를 왼쪽으로 드래그하여 현재 버전 위에 이 버전을 겹쳐놓고 비교합니다.

   ![compare_versions](assets/compare_versions.png)

### 자산에서 워크플로우 시작 {#starting-a-workflow-on-an-asset}

1. 워크플로우를 시작할 자산의 위치로 이동하고 자산을 탭/클릭하여 자산 페이지를 엽니다.
1. GlobalNav 아이콘을 탭/클릭하고 **[!UICONTROL 타임라인]** 메뉴에서 타임라인을 표시합니다.

   ![타임라인-1](assets/timeline-1.png)

1. 을 탭/클릭합니다. **[!UICONTROL 작업]** 맨 아래에 있는 (화살표) 아이콘을 사용하여 자산에 사용할 수 있는 작업 목록을 엽니다.

   ![chlimage_1-252](assets/chlimage_1-252.png)

1. 탭/클릭 **[!UICONTROL 워크플로우 시작]** 참조하십시오.

   ![chlimage_1-253](assets/chlimage_1-253.png)

1. 에서 **[!UICONTROL 워크플로우 시작]** 대화 상자의 목록에서 워크플로우 모델을 선택합니다.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. (선택 사항) 워크플로우 인스턴스를 참조하는 데 사용할 수 있는 워크플로우의 제목을 지정합니다.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Tap/click **[!UICONTROL Start]** and then tap/click **[!UICONTROL Proceed]** in the dialog to confirm. Each step of workflow is displayed in the timeline as an event.

   ![chlimage_1-256](assets/chlimage_1-256.png)

## 컬렉션 {#collections}

컬렉션은 순서가 지정된 자산 세트입니다. 컬렉션을 사용하여 사용자 간에 에셋을 공유합니다.

* 컬렉션에는 이러한 자산에 대한 참조만 포함되므로 다른 위치의 자산이 포함될 수 있습니다. 각 컬렉션은 자산의 참조 무결성을 유지합니다.
* 편집, 보기 등을 포함하여 권한 수준이 다른 여러 사용자와 컬렉션을 공유할 수 있습니다.

컬렉션 관리에 대한 자세한 내용은 [컬렉션 관리](/help/assets/manage-collections.md).

## 데스크탑 앱 또는 Adobe 자산 링크에서 자산을 볼 때 만료된 자산 숨기기 {#hide-expired-assets-via-acp-api}

[!DNL Experience Manager] 데스크탑 앱을 사용하면 Windows 또는 Mac 데스크탑에서 DAM 저장소에 액세스할 수 있습니다. Adobe 자산 링크를 사용하면 지원되는 내에서 자산에 액세스할 수 있습니다 [!DNL Creative Cloud] 데스크탑 응용 프로그램.

내에서 자산을 검색할 때 [!DNL Experience Manager] 사용자 인터페이스에서는 만료된 자산이 표시되지 않습니다. 데스크탑 앱 및 자산 링크에서 자산을 검색할 때 만료된 자산을 보고, 검색하고, 가져올 수 없도록 관리자는 다음 구성을 수행할 수 있습니다. 구성은 관리자 권한에 관계없이 모든 사용자에 대해 작동합니다.

다음 CURL 명령을 실행합니다. 읽기 액세스 설정 `/conf/global/settings/dam/acpapi/` 자산에 액세스하는 사용자용. 에 속하는 사용자 `dam-user` 그룹에는 기본적으로 권한이 있습니다.

```curl
curl -v -u admin:admin --location --request POST 'http://localhost:4502/conf/global/settings/dam/acpapi/configuration/_jcr_content' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'jcr:title=acpapiconfig' \
--data-urlencode 'hideExpiredAssets=true' \
--data-urlencode 'hideExpiredAssets@TypeHint=Boolean' \
--data-urlencode 'jcr:primaryType=nt:unstructured' \
--data-urlencode '../../jcr:primaryType=sling:Folder'
```

자세한 내용은 방법 을 참조하십시오. [데스크탑 앱을 사용하여 DAM 자산 찾아보기](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) 및 [Adobe 자산 링크 사용 방법](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html).

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)
