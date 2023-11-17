---
title: 디지털 자산 관리
description: 다양한 에셋 관리 및 편집 방법에 대해 알아봅니다
contentOwner: AG
mini-toc-levels: 3
feature: Asset Management,Publishing,Collaboration,Asset Processing
role: User,Architect,Admin
exl-id: 51a26764-ac2b-4225-8d27-42a7fd906183
source-git-commit: e2505c0fec1da8395930f131bfc55e1e2ce05881
workflow-type: tm+mt
source-wordcount: '4344'
ht-degree: 11%

---

# 에셋 관리 {#manage-assets}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html?lang=ko) |
| AEM as a Cloud Service | 이 문서 |

이 문서에서는에서 에셋을 관리하고 편집하는 방법을 설명합니다. [!DNL Adobe Experience Manager Assets]. 관리하려면 [!DNL Content Fragments], 참조 [[!DNL Content Fragments]](content-fragments/content-fragments.md) 에셋.

## 폴더 만들기 {#creating-folders}

에셋 컬렉션(예: 모두)을 구성할 때 `Nature` 이미지를 만들 때 폴더를 만들어 함께 보관할 수 있습니다. 폴더를 사용하여 에셋을 분류하고 구성할 수 있습니다. [!DNL Experience Manager Assets] 는 작업을 향상시키기 위해 폴더에 에셋을 구성할 필요가 없습니다.

>[!NOTE]
>
>* 유형의 에셋 폴더 공유 `sling:OrderedFolder`은(는) Experience Cloud에 공유할 때 지원되지 않습니다. 폴더를 공유하려면 선택하지 마십시오. [!UICONTROL 주문됨] 폴더를 만들 때.
>* Experience Manager에서 사용을 허용하지 않음 `subassets` word를 폴더 이름으로 사용합니다. 조합 자산에 대한 하위 자산을 포함하는 노드용으로 예약된 키워드입니다

1. 디지털 자산 폴더에서 폴더를 만들 위치로 이동합니다. 메뉴에서 다음을 클릭합니다. **[!UICONTROL 만들기]**. 선택 **[!UICONTROL 새 폴더]**.
1. 다음에서 **[!UICONTROL 제목]** 필드에 폴더 이름을 입력합니다. 기본적으로 DAM은 사용자가 제공한 제목을 폴더 이름으로 사용합니다. 폴더가 만들어지면 기본값을 재정의하고 다른 폴더 이름을 지정할 수 있습니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 디지털 에셋 폴더에 폴더가 표시됩니다.

공백으로 구분된 다음 문자는 지원되지 않습니다.

* 에셋 파일 이름에는 다음 문자를 사용할 수 없습니다. `* / : [ \\ ] | # % { } ? &`
* 에셋 폴더 이름에는 다음 문자를 사용할 수 없습니다. `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## 에셋 업로드 {#uploading-assets}

다음을 참조하십시오 [Experience Manager에 디지털 에셋 추가](add-assets.md).

## ZIP 아카이브 추출 {#extract-zip-archives}

Experience Manager에서 관리되는 ZIP 아카이브를 선택하고 다운로드하지 않고 파일을 Experience Manager에 직접 추출하십시오.

ZIP 파일을 추출하려면 다음 단계를 수행하십시오.

1. ZIP 파일 유형을 선택합니다.
1. 다음을 클릭합니다. **[!UICONTROL 아카이브 추출]** 작업 모음에서 사용할 수 있는 옵션입니다.
1. 압축된 폴더에서 사용할 수 있는 추출된 에셋을 저장해야 하는 폴더를 선택합니다.
1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 추출하는 동안 파일 이름 충돌을 처리할 적절한 동작을 선택하십시오. 기존 에셋의 버전을 만들거나, 에셋을 교체하거나, 두 에셋을 모두 대상 폴더에 유지하거나, 새 에셋의 추출을 건너뛰도록 선택할 수 있습니다.
1. 클릭 **[!UICONTROL Extract]**. Zip 추출 프로세스가 시작됩니다. 프로세스가 완료되면 대상 폴더에서 추출된 에셋을 볼 수 있습니다.

   ![zip 추출](assets/zip-extraction.png)

>[!NOTE]
>
>* 지원되는 최대 ZIP 파일 크기는 15GB입니다.
>* 한 번에 최대 3개의 ZIP 파일을 추출할 수 있습니다.

## 자산 미리보기 {#previewing-assets}

에셋을 미리 보려면 다음 단계를 수행합니다.

1. 에셋 사용자 인터페이스에서 미리 보려는 에셋의 위치로 이동합니다.
1. 원하는 에셋을 탭하여 엽니다.

1. 미리보기 모드에서 다음에 대한 확대/축소 옵션을 사용할 수 있습니다. [지원되는 이미지 유형](/help/assets/file-format-support.md) (대화형 편집 사용).

   자산을 확대하려면 탭/클릭합니다 `+` (또는 에셋에서 돋보기를 탭/클릭합니다.) 축소하려면 탭/클릭 `-`. 확대하면 패닝으로 이미지의 모든 영역을 자세히 볼 수 있습니다. 확대/축소 재설정 화살표를 사용하면 원래 보기로 돌아갑니다.

   누르기 **[!UICONTROL 재설정]** 뷰를 원래 크기로 재설정합니다.

## 속성 편집 {#editing-properties}

1. 편집할 메타데이터가 있는 에셋의 위치로 이동합니다.

1. 에셋을 선택하고 탭/클릭합니다 **[!UICONTROL 속성]** 을 클릭하여 자산 속성을 확인합니다. 또는 **[!UICONTROL 속성]** 에셋 카드에 대한 빠른 작업

   ![properties_quickaction](assets/properties_quickaction.png)

1. 다음에서 [!UICONTROL 속성] 페이지를 만들고 다양한 탭에서 메타데이터 속성을 편집합니다. 예를 들어 **[!UICONTROL 기본]** 탭, 제목, 설명 등을 편집합니다.

   >[!NOTE]
   >
   >의 레이아웃 [!UICONTROL 속성] 페이지 및 사용 가능한 메타데이터 속성은 기본 메타데이터 스키마에 따라 다릅니다. 의 레이아웃을 수정하는 방법을 알아보려면 [!UICONTROL 속성] 페이지, 참조 [메타데이터 스키마](/help/assets/metadata-schemas.md).

1. To schedule a particular date/time for the activation of the asset, use the date picker beside the **[!UICONTROL On Time]** field.

   ![날짜 선택기](assets/date-picker.png)

1. 특정 기간 후에 에셋을 비활성화하려면 옆에 있는 날짜 선택기에서 비활성화 날짜/시간을 선택합니다. **[!UICONTROL 해제 시간]** 필드. 비활성화 날짜는 에셋의 활성화 날짜 이후여야 합니다. 다음 이후 [!UICONTROL 해제 시간], 에셋 및 해당 렌디션은 에셋 웹 인터페이스 또는 HTTP API를 통해 사용할 수 없습니다.

   <!--![chlimage_1-218](assets/chlimage_1-218.png)
1. 다음에서 **[!UICONTROL 태그]** 필드에서 태그를 하나 이상 선택합니다. 사용자 지정 태그를 추가하려면 상자에 태그 이름을 입력하고 `Enter` 키. 새 태그는에 저장됩니다. [!DNL Experience Manager].

   YouTube을 게시하려면 태그가 필요하고 YouTube에 대한 링크가 있어야 합니다(적절한 링크가 있는 경우).

   >[!NOTE]
   >
   > 태그를 만들려면 다음 위치에 쓰기 권한이 있어야 합니다. `/content/cq:tags/default` crx 저장소의 경로입니다.

1. 탭/클릭 **[!UICONTROL 저장 및 닫기]**.

1. Assets 사용자 인터페이스로 이동합니다. 제목, 설명 및 태그를 포함한 편집된 메타데이터 속성은 카드 보기의 자산 카드 및 목록 보기의 관련 열 아래에 표시됩니다.

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

에셋 또는 폴더를 복사하면 전체 에셋 또는 폴더가 콘텐츠 구조와 함께 복사됩니다. 복사한 에셋 또는 폴더가 대상 위치에 복제됩니다. 소스 위치의 자산은 변경되지 않습니다.

에셋의 특정 사본에 고유한 몇 가지 속성은 이월되지 않습니다. 몇 가지 예는 다음과 같습니다.

* 에셋 ID, 생성 날짜 및 시간, 버전 및 버전 내역. 이러한 속성 중 일부는 속성으로 표시됩니다. `jcr:uuid`, `jcr:created`, 및 `cq:name`.

* 작성 시간 및 참조된 경로는 각 에셋과 각 에셋의 렌디션에 대해 고유합니다.

다른 속성 및 메타데이터 정보는 유지됩니다. 에셋을 복사할 때에는 부분 복사본이 만들어지지 않습니다.

1. 에셋 UI에서 하나 이상의 에셋을 선택한 다음 **[!UICONTROL 복사]** 아이콘을 클릭합니다. 또는 **[!UICONTROL 복사]** ![copy_icon](assets/copy_icon.png) 자산 카드의 빠른 작업

   >[!NOTE]
   >
   >를 사용하는 경우 [!UICONTROL 복사] 빠른 작업: 한 번에 하나의 에셋만 복사할 수 있습니다.

1. 에셋을 복사할 위치로 이동합니다.

   >[!NOTE]
   >
   >동일한 위치에서 에셋을 복사하는 경우 [!DNL Experience Manager] 는 이름의 변형을 자동으로 생성합니다. 예를 들어 이라는 에셋을 복사하는 경우 `Square`, [!DNL Experience Manager] 는 사본에 대한 제목을 다음과 같이 자동 생성합니다. `Square1`.

1. 다음을 클릭합니다. **[!UICONTROL 붙여넣기]** 도구 모음의 에셋 아이콘 자산이 이 위치에 복사됩니다.

   <!--![chlimage_1-219](assets/chlimage_1-219.png)-->

   >[!NOTE]
   >
   >다음 **[!UICONTROL 붙여넣기]** 붙여넣기 작업이 완료될 때까지 도구 모음에서 아이콘을 사용할 수 있습니다.

### 에셋 이동 또는 이름 바꾸기 {#moving-or-renaming-assets}

1. 이동할 자산의 위치로 이동합니다.

1. 에셋을 선택하고 **[!UICONTROL 이동]** 아이콘 ![move_icon](assets/move_icon.png) 을 클릭합니다.

1. 자산 이동 마법사에서 다음 중 하나를 수행합니다.

   * 에셋을 이동한 후 에셋의 이름을 지정합니다. 그런 다음 탭/클릭 **[!UICONTROL 다음]** 계속합니다.

   * 탭/클릭 **[!UICONTROL 취소]** 프로세스를 중지합니다.

   >[!NOTE]
   >
   >* 새 위치에 해당 이름을 가진 에셋이 없는 경우 에셋에 동일한 이름을 지정할 수 있습니다. 그러나 에셋을 같은 이름의 에셋이 있는 위치로 이동하는 경우에는 다른 이름을 사용해야 합니다. 동일한 이름을 사용하는 경우 이름 변형이 자동으로 생성됩니다. 예를 들어 에셋의 이름이 Square인 경우 시스템에서는 해당 복사본에 대한 이름 Square1을 생성합니다.
   >* 이름을 바꿀 때 파일 이름에 공백이 허용되지 않습니다.

1. 다음에서 **[!UICONTROL 대상 선택]** 대화 상자에서 다음 중 하나를 수행합니다.

   * 에셋의 새 위치로 이동한 다음 탭/클릭합니다 **[!UICONTROL 다음]** 계속합니다.

   * 탭/클릭 **[!UICONTROL 뒤로]** (으)로 돌아가기 **[!UICONTROL 이름 바꾸기]** 화면.

1. 이동하는 에셋에 참조하는 페이지, 에셋 또는 컬렉션이 있는 경우 **[!UICONTROL 참조 조정]** 탭 옆에 표시 **[!UICONTROL 대상 선택]** 탭.

   다음 중 하나를 수행합니다. **[!UICONTROL 참조 조정]** 화면:

   * 새 세부 사항을 기반으로 조정할 참조를 지정한 다음 탭/클릭합니다 **[!UICONTROL 이동]** 계속합니다.

   * 다음에서 **[!UICONTROL 조정]** 열에서 에셋에 대한 참조를 선택/선택 취소합니다.
   * 탭/클릭 **[!UICONTROL 뒤로]** (으)로 돌아가기 **[!UICONTROL 대상 선택]** 화면.

   * 탭/클릭 **[!UICONTROL 취소]** 이동 작업을 중지합니다.

   참조를 업데이트하지 않으면 계속해서 자산의 이전 경로를 가리킵니다. 참조를 조정하면 새 에셋 경로로 업데이트됩니다.

### 렌디션 관리 {#managing-renditions}

1. 원본을 제외한 에셋에 대한 렌디션을 추가하거나 제거할 수 있습니다. 렌디션을 추가하거나 제거할 에셋의 위치로 이동합니다.

1. 에셋을 탭/클릭하여 에셋 페이지를 엽니다.

   <!--![chlimage_1-220](assets/chlimage_1-220.png)-->

1. GlobalNav 아이콘을 탭/클릭한 다음 **[!UICONTROL 표현물]** 목록에서 삭제할 수 있습니다.

   ![renditions_menu](assets/renditions_menu.png)

1. 다음에서 **[!UICONTROL 표현물]** 패널, 에셋에 대해 생성된 렌디션 목록을 봅니다.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >기본적으로, [!DNL Experience Manager Assets] 미리 보기 모드에서 에셋의 원본 렌디션을 표시하지 않습니다. 관리자는 오버레이를 사용하여 를 구성할 수 있습니다 [!DNL Assets] 미리보기 모드에서 원본 렌디션을 표시하려면

1. 렌디션을 보거나 삭제하려면 렌디션을 선택합니다.

   **렌디션 삭제**

   에서 렌디션 선택 **[!UICONTROL 표현물]** 패널을 클릭한 다음 **[!UICONTROL 렌디션 삭제]** 아이콘을 클릭합니다. 에셋 처리가 완료된 후에는 렌디션을 일괄적으로 삭제할 수 없습니다. 개별 에셋의 경우 사용자 인터페이스에서 렌디션을 수동으로 제거할 수 있습니다. 여러 에셋의 경우 사용자 지정할 수 있습니다 [!DNL Experience Manager] 특정 렌디션을 삭제하거나 에셋을 삭제하고 삭제된 에셋을 다시 업로드하려면

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **새 렌디션 업로드**

   Navigate to the asset details page for the asset, and tap/click the **[!UICONTROL Add Rendition]** icon in the toolbar to upload a new rendition for the asset.

   <!--![chlimage_1-221](assets/chlimage_1-221.png)-->

   >[!NOTE]
   >
   >If you select a rendition from the **[!UICONTROL Renditions]** panel, the toolbar changes context and displays only those actions that are relevant to the rendition. Options, such as the Upload Rendition icon is not displayed. To view these options in the toolbar, navigate to the details page for the asset.

   이미지 또는 비디오 에셋의 세부 사항 페이지에 표시할 렌디션의 차원을 구성할 수 있습니다. 지정한 차원에 따라 Assets는 정확한 차원이나 가장 가까운 차원을 사용하여 렌디션을 표시합니다.

   다음 접두사는 Adobe 내부에 있으므로 렌디션을 만들 수 없습니다.

   * cq5

   * cqdam

   * cq5dam

   To configure rendition dimensions of an image at the asset detail level, overlay the `renditionpicker` node (`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`) and configure the value of the width property. Configure the property **[!UICONTROL size (Long) in KB]** in place of width to customize rendition on asset detail page based on image size. For size-based customization, the property `preferOriginal` assigns preference to the original if the size of the matched rendition is greater than the original.

   마찬가지로 오버레이하여 주석 페이지 이미지를 사용자 정의할 수 있습니다 `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`.

   <!--![chlimage_1-222](assets/chlimage_1-222.png)-->

   비디오 에셋에 대한 렌디션 차원을 구성하려면 다음 위치로 이동합니다. `videopicker` 위치에 있는 CRX 저장소의 노드 `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`를 클릭하고 노드를 오버레이한 다음 적절한 속성을 편집합니다.

   >[!NOTE]
   >
   >비디오 주석은 HTML 5와 호환되는 비디오 형식이 있는 브라우저에서만 지원됩니다. 또한 브라우저에 따라 서로 다른 비디오 형식이 지원됩니다. 그러나 MXF 비디오 포맷은 비디오 주석에서 아직 지원되지 않습니다.

## 에셋 삭제 {#delete-assets}

다른 페이지에서 들어오는 참조를 확인하거나 제거하려면 에셋을 삭제하기 전에 관련 참조를 업데이트하십시오.

또한, 오버레이를 사용하여 강제 삭제 버튼을 비활성화하여, 사용자가 참조된 자산을 삭제하고 끊어진 링크를 남기지 못하도록 할 수 있습니다.

1. 삭제할 자산의 위치로 이동합니다.

1. 에셋을 선택하고 **[!UICONTROL 삭제]** ![delete_icon](assets/do-not-localize/delete-icon.png) 을 클릭합니다.

1. 확인 대화 상자에서 다음을 클릭합니다.

   * **[!UICONTROL 취소]** 작업을 중지하려면
   * **[!UICONTROL 삭제]**&#x200B;를 사용하여 작업을 확인합니다.

      * 에셋에 참조가 없으면 에셋이 삭제됩니다.
      * 에셋에 참조가 있을 경우 오류 메시지에 **[!UICONTROL 하나 이상의 에셋이 참조됨]**. 다음을 선택할 수 있습니다. **[!UICONTROL 강제 삭제]** 또는 **[!UICONTROL 취소]**.

   >[!NOTE]
   >
   >에셋을 삭제하려면 dam/asset에 대한 삭제 권한이 필요합니다. 수정 권한만 있는 경우 에셋 메타데이터를 편집하고 에셋에 주석을 추가할 수 있습니다. 그러나 에셋 또는 에셋의 메타데이터는 삭제할 수 없습니다.

   >[!NOTE]
   >
   >다른 페이지에서 들어오는 참조를 확인하거나 제거하려면 에셋을 삭제하기 전에 관련 참조를 업데이트하십시오. 링크가 끊어지기 때문에 참조된 에셋을 삭제하는 것을 허용하지 않을 수 있습니다. 오버레이를 사용하여 강제 삭제 단추를 비활성화합니다.

## 자산 다운로드 {#download-assets}

다음을 참조하십시오 [에서 에셋 다운로드 [!DNL Experience Manager]](/help/assets/download-assets-from-aem.md).

## 자산 게시 또는 게시 취소 {#publish-assets}

1. 게시하거나 게시 환경에서 제거하려는(게시 취소) 에셋 또는 에셋 폴더의 위치로 이동합니다.

1. 게시 또는 게시 취소할 에셋 또는 폴더를 선택하고 **[!UICONTROL 게시 관리]** ![게시 관리 옵션](assets/do-not-localize/globe-publication.png) 도구 모음의 옵션입니다. 또는 빠르게 게시하려면 **[!UICONTROL 빠른 게시]** 도구 모음의 옵션입니다. 게시하려는 폴더에 빈 폴더가 포함되어 있으면 빈 폴더는 게시되지 않습니다.

1. 다음 항목 선택 **[!UICONTROL 게시]** 또는 **[!UICONTROL 게시 취소]** 필요에 따라 옵션을 선택합니다.

   ![게시 취소 작업](assets/unpublish_action.png)
   *그림: 게시 및 게시 취소 옵션과 예약 옵션*

1. 선택 **[!UICONTROL 지금]** 자산을 즉시 처리하거나 **[!UICONTROL 나중에]** 을 클릭하여 작업을 예약합니다. 다음을 선택하는 경우 날짜 및 시간 선택 **[!UICONTROL 나중에]** 옵션을 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. 게시할 때 에셋이 다른 에셋을 참조하는 경우 해당 참조가 마법사에 나열됩니다. 마지막 게시 이후 게시가 취소되거나 수정된 참조만 표시됩니다. 게시하려는 참조를 선택합니다.

1. 게시를 취소할 때 에셋이 다른 에셋을 참조하는 경우 게시를 취소할 참조를 선택합니다. **[!UICONTROL 게시 취소]**&#x200B;를 클릭합니다. 확인 대화 상자에서 **[!UICONTROL 취소]** 작업을 중지하려면 **[!UICONTROL 게시 취소]** 지정된 날짜에 에셋의 게시가 취소되는지 확인합니다.

에셋 또는 폴더 게시 또는 게시 취소와 관련된 다음 제한 사항 및 팁을 이해합니다.

* 다음에 대한 옵션: [!UICONTROL 게시 관리] 복제 권한이 있는 사용자 계정만 사용할 수 있습니다.
* 복잡한 에셋의 게시를 취소하는 동안 에셋만 게시 취소합니다. 게시된 다른 에셋에서 참조하므로 참조를 게시 취소하지 마십시오.
* 빈 폴더는 게시되지 않습니다.
* 처리 중인 에셋을 게시하는 경우 원래 콘텐츠만 게시됩니다. 렌디션이 누락되었습니다. 처리가 완료될 때까지 기다린 다음 처리가 완료되면 자산을 게시하거나 다시 게시합니다.

## 폐쇄된 사용자 그룹 {#closed-user-group}

CUG(폐쇄형 사용자 그룹)는에서 게시된 특정 에셋 폴더에 대한 액세스를 제한하는 데 사용됩니다 [!DNL Experience Manager]. 폴더에 대한 CUG를 생성하는 경우 폴더(폴더 에셋 및 하위 폴더 포함)에 대한 액세스는 할당된 구성원 또는 그룹으로만 제한됩니다. 폴더에 액세스하려면 보안 자격 증명을 사용하여 로그인해야 합니다.

CUG는 자산에 대한 액세스를 제한하는 추가 방법입니다. 폴더의 로그인 페이지를 구성할 수도 있습니다.

1. Assets UI에서 폴더를 선택하고 도구 모음에서 속성 아이콘을 탭/클릭하여 속성 페이지를 표시합니다.
1. 다음에서 **[!UICONTROL 권한]** 탭, 아래에 구성원 또는 그룹 추가 **[!UICONTROL 폐쇄된 사용자 그룹]**.

   ![add_user](assets/add_user.png)

1. 사용자가 폴더에 액세스할 때 로그인 화면을 표시하려면 **[!UICONTROL 사용]** 옵션을 선택합니다. 그런 다음 의 로그인 페이지 경로를 선택합니다 [!DNL Experience Manager]을 클릭하고 변경 내용을 저장합니다.

   ![login_page](assets/login_page.png)

   >[!NOTE]
   >
   >로그인 페이지 경로를 지정하지 않으면 [!DNL Experience Manager] 게시 인스턴스에 기본 로그인 페이지를 표시합니다.

1. 폴더를 게시한 다음 게시 인스턴스에서 액세스해 보십시오. 로그인 화면이 표시됩니다.
1. CUG 멤버인 경우 보안 인증서를 입력합니다. 다음 뒤에 폴더가 표시됩니다. [!DNL Experience Manager] 인증.

## 자산 검색 {#search-assets}

자산 검색은 디지털 자산 관리 시스템 사용의 핵심입니다. 이를 통해 크리에이티브에서 더 많이 사용하거나, 비즈니스 사용자 및 마케터가 자산을 탄탄하게 관리하거나, DAM 관리자가 관리할 수 있습니다.

가장 적절한 에셋을 검색하고 사용하기 위한 간단한 고급 사용자 지정 검색에 대해서는 [에서 에셋 검색 [!DNL Experience Manager]](/help/assets/search-assets.md).

## 빠른 작업 {#quick-actions}

빠른 작업 아이콘은 한 번에 하나의 에셋에 사용할 수 있습니다. 장치에 따라 다음 작업을 수행하여 빠른 작업 아이콘을 표시합니다.

* 터치 장치: 터치 및 홀드. 예를 들어 iPad에서 빠른 작업이 표시되도록 에셋을 길게 탭할 수 있습니다.
* 비-터치 장치: 마우스 포인터. 예를 들어 데스크탑 디바이스에서 포인터를 자산 썸네일 위에 두면 빠른 작업 표시줄이 표시됩니다.

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

타임라인을 사용하면 에셋에 대한 활성 워크플로우, 댓글/주석, 활동 로그 및 버전과 같은 선택한 항목에 대한 다양한 이벤트를 볼 수 있습니다.

![자산에 대한 타임라인 항목 정렬](assets/sort_timeline.gif)
*그림: 에셋의 타임라인 항목 정렬*

>[!NOTE]
>
>다음에서 [컬렉션 콘솔](/help/assets/manage-collections.md#navigate-the-collections-console), **[!UICONTROL 모두 표시]** 목록은 댓글 및 워크플로만 볼 수 있는 옵션을 제공합니다. 또한 콘솔에 나열된 최상위 수준 컬렉션에만 타임라인이 표시됩니다. 컬렉션 내부를 탐색하는 경우에는 표시되지 않습니다.

>[!NOTE]
>
>타임라인에 여러 개 포함 [컨텐츠 조각과 관련된 옵션](content-fragments/content-fragments.md).

## 에셋에 주석 달기 {#annotating}

주석은 이미지 또는 비디오에 추가된 댓글 또는 설명 주석입니다. 주석은 마케터에게 자산에 대한 공동 작업을 수행하고 피드백을 남길 수 있는 기능을 제공합니다.

비디오 주석은 HTML5와 호환되는 비디오 형식이 있는 브라우저에서만 지원됩니다. Assets가 지원하는 비디오 형식은 브라우저에 따라 다릅니다. 그러나 MXF 비디오 포맷은 비디오 주석에서 아직 지원되지 않습니다.

>[!NOTE]
>
>컨텐츠 조각의 경우 [주석은 조각 편집기에서 생성됩니다](content-fragments/content-fragments.md).

1. 주석을 추가할 자산의 위치로 이동합니다.
1. 탭/클릭 **[!UICONTROL 주석]** 아이콘은 다음 중 하나입니다.

   * [빠른 작업](#quick-actions)
   * 에셋을 선택하거나 에셋 페이지로 이동한 후 도구 모음에서

   <!--![chlimage_1-233](assets/chlimage_1-233.png)-->

1. Add a comment in the **[!UICONTROL Comment]** box at the bottom of the timeline. Alternatively, mark up an area on the image and add an annotation in the **[!UICONTROL Add Annotation]** dialog.

<!-- ![chlimage_1-234](assets/chlimage_1-234.png)-->

<!--
1. To notify a user about an annotation, specify the email address of the user and add the comment. For example, to notify Aaron MacDonald about an annotation, enter @aa. Hints for all matching users is displayed in a list. Select Aaron's email address from the list to tag her with the comment. Similarly, you can tag more users anywhere within the annotation or before or after it.
-->

>[!NOTE]
>
>관리자가 아닌 사용자의 경우 다음에 대한 읽기 권한이 있는 경우에만 제안이 표시됩니다. `/home` CRXDE.

<!--![chlimage_1-235](assets/chlimage_1-235.png)-->

1. 주석을 추가한 후 **[!UICONTROL 추가]** 저장하려고. 주석에 대한 알림이 Aaron에게 전송됩니다.

   <!--![chlimage_1-236](assets/chlimage_1-236.png)-->

   >[!NOTE]
   >
   >저장하기 전에 여러 주석을 추가할 수 있습니다.

1. 탭/클릭 **[!UICONTROL 닫기]** 주석 모드를 종료합니다.
1. 알림을 보려면 Aaron MacDonald의 자격 증명으로 Assets에 로그인하고 **[!UICONTROL 알림]** 알림을 보는 아이콘.

   >[!NOTE]
   >
   >비디오 에셋에 주석을 추가할 수도 있습니다. 비디오에 주석을 달 때 플레이어는 일시 중지하여 프레임에 주석을 달 수 있도록 합니다. 자세한 내용은 [비디오 자산 관리](manage-video-assets.md). 그러나 MXF 비디오 포맷은 비디오 주석에서 아직 지원되지 않습니다.

1. 사용자를 구분할 수 있도록 다른 색상을 선택하려면 프로필 아이콘을 클릭/탭한 다음 클릭/탭합니다 **[!UICONTROL 내 환경 설정]**.

   <!--![chlimage_1-237](assets/chlimage_1-237.png)-->

   Specify the desired color in the **[!UICONTROL Annotation Color]** box and then click/tap **[!UICONTROL Accept]**.

<!-- ![chlimage_1-238](assets/chlimage_1-238.png)-->

>[!NOTE]
>
>컬렉션에 주석을 추가할 수도 있습니다. 그러나 컬렉션에 하위 컬렉션이 포함되어 있으면 상위 컬렉션에만 주석/설명을 추가할 수 있습니다. 하위 컬렉션에는 주석 달기 옵션을 사용할 수 없습니다.

### 저장된 주석 보기 {#viewing-saved-annotations}

한 번에 하나의 주석만 볼 수 있습니다.

>[!NOTE]
>
>여러 주석을 선택하는 경우 최신 주석이 사용자 인터페이스에 표시됩니다.
>
>다중 선택은 주석이 있는 에셋을 PDF으로 인쇄하는 경우에만 지원됩니다.

1. 자산에 대해 저장된 주석을 보려면 자산의 위치로 이동하여 자산에 대한 자산 페이지를 엽니다.

1. GlobalNav 아이콘을 탭/클릭하고 **[!UICONTROL 타임라인]** 목록에서 삭제할 수 있습니다.

   <!--![chlimage_1-239](assets/chlimage_1-239.png)-->

1. From the **[!UICONTROL Show All]** list in the timeline, select **[!UICONTROL Comments]** to filter the results based on annotations.

   <!--![chlimage_1-240](assets/chlimage_1-240.png)-->

   에서 주석 탭/클릭 **[!UICONTROL 타임라인]** 패널에서 이미지에 있는 해당 주석을 볼 수 있습니다.

   <!--![chlimage_1-241](assets/chlimage_1-241.png)-->

   탭/클릭 **[!UICONTROL 삭제]**&#x200B;을 클릭하여 특정 주석을 삭제합니다.

### 주석 인쇄 {#printing-annotations}

자산에 주석이 있거나 검토 워크플로우가 적용된 경우, 오프라인 검토를 위한 PDF 파일로 자산 및 검토 상태를 주석과 함께 인쇄할 수 있습니다.

주석만 인쇄하도록 선택하거나 상태를 검토할 수도 있습니다.

>[!NOTE]
>
>주석이 있는 에셋을 PDF으로 인쇄하는 동안 여러 주석을 선택할 수 있습니다.

주석을 인쇄하고 상태를 검토하려면 다음을 탭/클릭합니다 **[!UICONTROL 인쇄]** 아이콘을 클릭하고 마법사의 지시를 따릅니다. 다음 **[!UICONTROL 인쇄]** 아이콘은 자산에 하나 이상의 주석 또는 검토 상태가 할당된 경우에만 도구 모음에 표시됩니다.

1. 에셋 UI에서 에셋에 대한 미리보기 페이지를 엽니다.
1. 다음 중 하나를 수행하십시오.

   * 모든 주석과 검토 상태를 인쇄하려면 3단계를 건너뛰고 바로 4단계로 이동합니다.
   * 특정 주석을 인쇄하고 상태를 검토하려면 [타임라인](/help/assets/manage-digital-assets.md#timeline) 그런 다음 3단계로 이동합니다.

1. 특정 주석을 인쇄하려면 타임라인에서 주석을 선택합니다.

   <!--![chlimage_1-242](assets/chlimage_1-242.png)-->

   검토 상태만 인쇄하려면 타임라인에서 선택합니다.

   <!--![chlimage_1-243](assets/chlimage_1-243.png)-->

1. 탭/클릭 **[!UICONTROL 인쇄]** 아이콘을 클릭합니다.

   <!--![chlimage_1-244](assets/chlimage_1-244.png)-->

1. 인쇄 대화 상자에서 주석/검토 상태를 PDF에 표시할 위치를 선택합니다. 예를 들어 인쇄된 이미지가 포함된 페이지의 오른쪽 상단에 주석/상태를 인쇄하려면 **왼쪽 위** 설정. 기본적으로 선택되어 있습니다.

   <!--![chlimage_1-245](assets/chlimage_1-245.png)-->

   You can choose other settings depending on the position where you want the annotations/status to appear in the printed PDF. If you want the annotations/status to appear in a page that is separate from the printed asset, choose **[!UICONTROL Next Page]**.

1. 클릭 **[!UICONTROL 인쇄]**. Depending upon the option you choose in step 2, the generated PDF displays the annotations/status at the specified position. For example, if you choose to print both annotations and the review status using the **Top-Left** setting, the generated output resembles the PDF file depicted here.

   <!--![chlimage_1-246](assets/chlimage_1-246.png)-->

1. 오른쪽 상단의 옵션을 사용하여 PDF을 다운로드하거나 인쇄합니다.

   <!--![chlimage_1-247](assets/chlimage_1-247.png)-->

   렌더링된 PDF 파일의 모양(예: 주석 및 상태의 글꼴 색상, 크기 및 스타일, 배경색)을 수정하려면 **[!UICONTROL 주석 PDF 구성]** 을 누르고 원하는 옵션을 수정합니다. 예를 들어 승인됨 상태의 표시 색상을 변경하려면 해당 필드의 색상 코드를 수정합니다. 주석의 글꼴 색상 변경에 대한 자세한 내용은 [주석 달기](/help/assets/manage-digital-assets.md#annotating).

   렌더링된 PDF 파일로 돌아가서 새로 고칩니다. 새로 고친 PDF은 변경 사항을 반영합니다.

## 에셋 버전 관리 {#asset-versioning}

버전 관리는 특정 시점에 디지털 에셋의 스냅샷을 만듭니다. 버전 관리를 통해 에셋을 나중에 이전 상태로 복원할 수 있습니다. 예를 들어 에셋에 대한 변경 내용을 실행 취소하려면 편집되지 않은 버전의 에셋을 복원합니다.

다음은 버전을 만드는 시나리오입니다.

* 다른 애플리케이션에서 이미지를 수정하고 에셋에 업로드합니다. 원본 이미지를 덮어쓰지 않도록 이미지 버전이 만들어집니다.
* 에셋의 메타데이터를 편집합니다.
* 다음을 사용합니다. [!DNL Experience Manager] 기존 에셋을 체크아웃하고 변경 사항을 저장하는 데스크탑 앱입니다. 에셋이 저장될 때마다 새 버전이 만들어집니다.

워크플로우를 통해 자동 버전 관리를 활성화할 수도 있습니다. 에셋에 대한 버전을 만들면 버전과 함께 메타데이터 및 렌디션이 저장됩니다. 변환은 업로드된 JPEG 파일의 PNG 변환과 같이 동일한 이미지의 대체 표현물입니다.

버전 관리 기능을 사용하여 다음을 수행할 수 있습니다.

* 에셋의 버전을 만듭니다.
* 에셋의 현재 개정을 봅니다.
* 자산을 이전 버전으로 복원합니다.

1. 버전을 만들 에셋의 위치로 이동한 다음 해당 에셋 페이지를 열려면 해당 에셋을 탭/클릭하십시오.

1. GlobalNav 아이콘을 탭/클릭하고 **[!UICONTROL 타임라인]** 메뉴에서 삭제할 수 있습니다.

   ![타임라인](assets/timeline.png)

1. 탭/클릭 **[!UICONTROL 작업]** (화살표) 아이콘을 클릭하면 에셋에서 수행할 수 있는 작업을 확인할 수 있습니다.

   <!--![chlimage_1-249](assets/chlimage_1-249.png)-->

1. 탭/클릭 **[!UICONTROL 다른 버전으로 저장]** 에셋의 버전을 생성하려면 다음을 수행하십시오.

<!--![chlimage_1-250](assets/chlimage_1-250.png)-->

1. 레이블과 댓글을 추가한 다음 **[!UICONTROL 만들기]** 을 클릭하여 버전을 만듭니다. 또는 을 탭/클릭합니다 **취소** 을 눌러 작업을 종료합니다.

   <!--![chlimage_1-251](assets/chlimage_1-251.png)-->

1. To view the new version, open the **[!UICONTROL Show All]** list in the timeline from the asset details page or the Assets UI, and choose **[!UICONTROL Versions]**. All versions created for an asset are listed under the timeline tab. You can filter the list to show Versions, by clicking the drop arrow and selecting **[!UICONTROL Versions]** from the list.

   ![versions_option](assets/versions_option.png)

1. 에셋을 미리 보거나 에셋 UI에 표시되도록 활성화하려면 에셋의 특정 버전을 선택합니다.

   ![select_version](assets/select_version.png)

1. Assets UI에서 특정 버전으로 되돌리려면 버전에 대한 레이블과 주석을 추가하십시오.

   ![save_version](assets/save_version.png)

1. To generate a preview for the version, tap/click **[!UICONTROL Preview Version]**.
1. 자산 UI에 이 버전을 표시하려면 을 선택합니다. **[!UICONTROL 이 버전으로 되돌리기]**.
1. 두 버전을 비교하려면 에셋의 에셋 페이지로 이동하여 현재 버전과 비교할 버전을 탭/클릭합니다.

   ![select_version_tocompare](assets/select_version_tocompare.png)

1. 타임라인에서 비교할 버전을 선택하고 슬라이더를 왼쪽으로 드래그하여 이 버전을 현재 버전에 중첩한 다음 비교합니다.

   ![compare_versions](assets/compare_versions.png)

### 자산에 대한 워크플로우 시작 {#starting-a-workflow-on-an-asset}

1. 워크플로우를 시작할 자산의 위치로 이동한 다음 자산을 탭/클릭하여 자산 페이지를 엽니다.
1. GlobalNav 아이콘을 탭/클릭하고 **[!UICONTROL 타임라인]** 을 클릭하여 타임라인을 표시합니다.

   ![timeline-1](assets/timeline-1.png)

1. 탭/클릭 **[!UICONTROL 작업]** (화살표) 아래에 있는 아이콘을 클릭하여 자산에 사용할 수 있는 작업 목록을 엽니다.

   <!--![chlimage_1-252](assets/chlimage_1-252.png)-->

1. 탭/클릭 **[!UICONTROL 워크플로우 시작]** 목록에서 삭제할 수 있습니다.

   <!--![chlimage_1-253](assets/chlimage_1-253.png)-->

1. 다음에서 **[!UICONTROL 워크플로우 시작]** 대화 상자에서 목록에서 워크플로 모델을 선택합니다.

   <!--![chlimage_1-254](assets/chlimage_1-254.png)-->

1. (선택 사항) 워크플로 인스턴스를 참조하는 데 사용할 수 있는 워크플로의 제목을 지정합니다.

   <!--![chlimage_1-255](assets/chlimage_1-255.png)-->

1. Tap/click **[!UICONTROL Start]** and then tap/click **[!UICONTROL Proceed]** in the dialog to confirm. Each step of workflow is displayed in the timeline as an event.

   <!--![chlimage_1-256](assets/chlimage_1-256.png)-->

## 컬렉션 {#collections}

컬렉션은 순서가 지정된 에셋 세트입니다. 컬렉션을 사용하여 사용자 간에 에셋을 공유합니다.

* 이러한 에셋에 대한 참조만 포함하므로 컬렉션에는 서로 다른 위치의 에셋이 포함될 수 있습니다. 각 컬렉션은 자산의 참조 무결성을 유지합니다.
* 편집, 보기 등을 포함하여 다양한 권한 수준을 가진 여러 사용자와 컬렉션을 공유할 수 있습니다.

컬렉션 관리에 대한 자세한 내용은 [컬렉션 관리](/help/assets/manage-collections.md).

## 데스크탑 앱 또는 Adobe 자산 링크에서 자산을 볼 때 만료된 자산 숨기기 {#hide-expired-assets-via-acp-api}

[!DNL Experience Manager] 데스크탑 앱을 사용하면 Windows 또는 Mac 데스크탑에서 DAM 저장소에 액세스할 수 있습니다. Adobe 에셋 링크를 사용하면 지원되는 내에서 에셋에 액세스할 수 있습니다. [!DNL Creative Cloud] 데스크탑 애플리케이션.

내에서 에셋을 검색할 때 [!DNL Experience Manager] 사용자 인터페이스에서는 만료된 에셋이 표시되지 않습니다. 관리자는 데스크탑 앱 및 Asset Link에서 자산을 검색할 때 만료된 자산을 보고 검색하고 가져오지 않도록 다음 구성을 수행할 수 있습니다. 이 구성은 관리자 권한과 관계없이 모든 사용자에 대해 작동합니다.

다음 CURL 명령을 실행합니다. 에 대한 읽기 액세스 권한 확인 `/conf/global/settings/dam/acpapi/` 에셋에 액세스하는 사용자용입니다. 에 속한 사용자 `dam-user` 기본적으로 그룹에 권한이 있습니다.

```curl
curl -v -u admin:admin --location --request POST 'http://localhost:4502/conf/global/settings/dam/acpapi/configuration/_jcr_content' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'jcr:title=acpapiconfig' \
--data-urlencode 'hideExpiredAssets=true' \
--data-urlencode 'hideExpiredAssets@TypeHint=Boolean' \
--data-urlencode 'jcr:primaryType=nt:unstructured' \
--data-urlencode '../../jcr:primaryType=sling:Folder'
```

자세한 내용은 방법 을 참조하십시오 [데스크탑 앱을 사용하여 DAM 자산 찾아보기](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) 및 [Adobe 에셋 링크를 사용하는 방법](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html).

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
