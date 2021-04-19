---
title: 디지털 자산을 관리합니다
description: 다양한 에셋 관리 및 편집 방법에 대해 알아봅니다.
contentOwner: AG
mini-toc-levels: 1
feature: 자산 관리,게시,공동 작업,자산 처리
role: Business Practitioner,Architect,Administrator
exl-id: 51a26764-ac2b-4225-8d27-42a7fd906183
translation-type: tm+mt
source-git-commit: 05c090a198cc241c6e466254416880dd6406900f
workflow-type: tm+mt
source-wordcount: '4505'
ht-degree: 2%

---

# 자산 관리 {#manage-assets}

이 문서에서는 Adobe Experience Manager Assets의 자산을 관리하고 편집하는 방법에 대해 설명합니다. 컨텐츠 조각을 관리하려면 [컨텐츠 조각](content-fragments/content-fragments.md) 자산을 참조하십시오.

## {#creating-folders} 폴더 만들기

자산 컬렉션을 구성할 때(예: 모든 `Nature` 이미지) 함께 유지할 폴더를 만들 수 있습니다. 폴더를 사용하여 자산을 분류하고 구성할 수 있습니다. [!DNL Experience Manager Assets] 를 사용하면 보다 효과적으로 작동하도록 폴더의 에셋을 구성할 필요가 없습니다.

>[!NOTE]
>
>* `sling:OrderedFolder` 유형의 자산 폴더 공유는 Marketing Cloud에 공유할 때 지원되지 않습니다. 폴더를 공유하려면 폴더를 만들 때 [!UICONTROL 주문됨]을 선택하지 마십시오.
>* Experience Manager에서는 `subassets` 단어를 폴더 이름으로 사용할 수 없습니다. 복합 자산에 대한 하위 자산을 포함하는 노드에 예약된 키워드입니다.


1. 새 폴더를 만들 디지털 자산 폴더의 위치로 이동합니다. 메뉴에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. **[!UICONTROL 새 폴더]**&#x200B;를 선택합니다.
1. **[!UICONTROL 제목]** 필드에 폴더 이름을 입력합니다. 기본적으로 DAM은 폴더 이름으로 제공한 제목을 사용합니다. 폴더가 만들어지면 기본값을 무시하고 다른 폴더 이름을 지정할 수 있습니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 폴더가 디지털 자산 폴더에 표시됩니다.

다음(공백으로 구분된 목록) 문자는 지원되지 않습니다.

* 자산 파일 이름에는 다음 문자를 사용할 수 없습니다.`* / : [ \\ ] | # % { } ? &`
* 자산 폴더 이름에는 다음 문자를 사용할 수 없습니다.`* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## 자산 업로드 {#uploading-assets}

[Experience Manager](add-assets.md)에 디지털 자산 추가를 참조하십시오.

## 중복된 자산 {#detect-duplicate-assets} 감지

<!-- TBD: This feature may not work as documented. See CQ-4283718. Get PM review done. -->

DAM 사용자가 저장소에 이미 있는 하나 이상의 자산을 업로드하는 경우, [!DNL Experience Manager]은(는) 중복을 감지하여 사용자에게 알립니다. 중복 감지는 저장소 크기 및 업로드된 자산 수에 따라 성능에 영향을 줄 수 있으므로 기본적으로 비활성화됩니다. 이 기능을 활성화하려면 [!UICONTROL Adobe AEM Cloud Asset Duplicator]를 구성합니다. [OSGi 구성 작업 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html)을 참조하십시오. 복제 감지는 `jcr:content/metadata/dam:sha1`에 저장된 고유한 `dam:sha1` 값을 기반으로 합니다. 파일 이름이 다르더라도 중복 에셋이 검색됨을 의미합니다.

사용자 지정 코드에 구성 파일 `/apps/example/config.author/com.adobe.cq.assetcompute.impl.assetprocessor.AssetDuplicationDetector.cfg.json`을 추가할 수 있으며 파일에는 다음이 포함될 수 있습니다.

```json
{
  "enabled":true,
  "detectMetadataField":"dam:sha1"
}
```

활성화되면 Experience Manager은 중복 에셋의 알림을 Experience Manager 받은 편지함으로 보냅니다. 여러 중복에 대해 집계된 결과입니다. 사용자는 결과에 따라 자산을 제거하도록 선택할 수 있습니다.

![중복 자산에 대한 받은 편지함 알림](assets/duplicate-detect-inbox-notification.png)

## 자산 미리 보기 {#previewing-assets}

자산을 미리 보려면 다음 단계를 수행합니다.

1. 자산 사용자 인터페이스에서 미리 보려는 자산의 위치로 이동합니다.
1. 원하는 자산을 눌러 엽니다.

1. 미리 보기 모드에서 확대/축소 옵션은 [지원되는 이미지 유형](/help/assets/file-format-support.md)(대화형 편집 포함)에 사용할 수 있습니다.

   자산을 확대하려면 `+`을(를) 탭/클릭합니다. 또는 자산에서 돋보기를 탭/클릭합니다.) 축소하려면 `-`을(를) 탭/클릭합니다. 확대하면 패닝하여 이미지의 모든 영역을 자세히 볼 수 있습니다. 확대/축소 재설정 화살표를 사용하면 원래 보기로 돌아갑니다.

   보기를 원래 크기로 재설정하려면 **[!UICONTROL 재설정]**&#x200B;을 누릅니다.

## 속성 편집 {#editing-properties}

1. 편집할 메타데이터가 있는 자산의 위치로 이동합니다.

1. 자산을 선택하고 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 탭/클릭하여 자산 속성을 봅니다. 또는 자산 카드에서 **[!UICONTROL 속성]** 빠른 작업을 선택합니다.

   ![properties_quickaction](assets/properties_quickaction.png)

1. [!UICONTROL 속성] 페이지에서 다양한 탭에서 메타데이터 속성을 편집합니다. 예를 들어 **[!UICONTROL 기본]** 탭에서 제목, 설명 등을 편집합니다.

   >[!NOTE]
   >
   >[!UICONTROL 속성] 페이지의 레이아웃 및 사용 가능한 메타데이터 속성은 기본 메타데이터 스키마에 따라 다릅니다. [!UICONTROL 속성] 페이지의 레이아웃을 수정하는 방법에 대해 알려면 [메타데이터 스키마](/help/assets/metadata-schemas.md)를 참조하십시오.

1. 자산의 활성화를 위한 특정 날짜/시간을 예약하려면 **[!UICONTROL 설정 시간]** 필드 옆에 있는 날짜 선택기를 사용합니다.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. 특정 기간 후에 자산을 비활성화하려면 **[!UICONTROL 해제 시간]** 필드 옆에 있는 날짜 선택기에서 비활성화 날짜/시간을 선택합니다. 비활성화 날짜는 자산의 활성화 날짜보다 이후여야 합니다. [!UICONTROL 해제 시간] 이후에는 자산 웹 인터페이스 또는 HTTP API를 통해 에셋 및 해당 변환을 사용할 수 없습니다.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. **[!UICONTROL 태그]** 필드에서 하나 이상의 태그를 선택합니다. 사용자 지정 태그를 추가하려면 상자에 태그 이름을 입력하고 `Enter` 키를 선택합니다. 새 태그가 [!DNL Experience Manager]에 저장됩니다.

   YouTube를 게시하려면 태그가 필요하며 YouTube에 대한 링크가 있어야 합니다(적절한 링크를 찾을 수 있는 경우).

   >[!NOTE]
   >
   >태그를 만들려면 CRX 저장소의 `/content/cq:tags/default` 경로에 쓰기 권한이 있어야 합니다.

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 탭/클릭합니다.

1. 자산 사용자 인터페이스로 이동합니다. 제목, 설명 및 태그를 비롯한 편집된 메타데이터 속성은 카드 보기의 자산 카드 및 목록 보기의 관련 열 아래에 표시됩니다.

<!-- TBD: Uncomment after verification for Dec release.

## View asset usage and references {#usage-and-references}

[!DNL Experience Manager] lets you track statistics about usage of a digital asset. The usage statistics include the following:

    * Number of times the asset was viewed or downloaded
    * Channels/devices through which the asset was used
    * Creative solutions where the asset was recently used

To view usage statistics for an asset, in the [!UICONTROL Properties] page, click the **[!UICONTROL Insights]** tab. For more details, see [Asset Insights](assets-insights.md).

[!DNL Experience Manager] also lets you check all the incoming references to an asset, that is, the usage of an asset in remote [!DNL Sites] and in compound assets. Authors of webpages on [!DNL Experience Manager Sites] deployment can use an asset on a remote [!DNL Assets] deployment using the Connected Assets functionality. The [!UICONTROL References] tab in an asset's [!UICONTROL Properties] page lists the local and remote references of the asset. That is, the use of assets in compound assets in [!DNL Assets] and its use in remote [!DNL Sites] pages.

-->

## 자산 복사 {#copying-assets}

에셋 또는 폴더를 복사하면 전체 에셋 또는 폴더가 컨텐츠 구조와 함께 복사됩니다. 복사된 자산 또는 폴더는 대상 위치에 복제됩니다. 소스 위치의 자산은 변경되지 않습니다.

자산의 특정 복사본에 고유한 몇 가지 속성은 전달되지 않습니다. 예를 들면 다음과 같습니다.

* 자산 ID, 작성 날짜 및 시간, 버전 및 버전 내역. 이러한 속성 중 일부는 `jcr:uuid`, `jcr:created` 및 `cq:name` 속성으로 표시됩니다.

* 제작 시간 및 참조된 경로는 각 자산과 각 표현물에 대해 고유합니다.

다른 속성 및 메타데이터 정보가 유지됩니다. 자산을 복사할 때 부분 복사본이 만들어지지 않습니다.

1. 자산 UI에서 하나 이상의 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 복사]** 아이콘을 탭/클릭합니다. 또는 자산 카드에서 **[!UICONTROL 복사]** ![복사_아이콘](assets/copy_icon.png) 빠른 작업을 선택합니다.

   >[!NOTE]
   >
   >[!UICONTROL 복사] 빠른 작업을 사용하는 경우 한 번에 하나의 자산만 복사할 수 있습니다.

1. 자산을 복사할 위치로 이동합니다.

   >[!NOTE]
   >
   >동일한 위치에서 자산을 복사하면 [!DNL Experience Manager]은(는) 변형된 이름을 자동으로 생성합니다. 예를 들어 `Square`이라는 제목의 자산을 복사하면 [!DNL Experience Manager]은 자동으로 복사본 제목을 `Square1`로 생성합니다.

1. 도구 모음에서 **[!UICONTROL 붙여넣기]** 자산 아이콘을 클릭합니다. 자산이 이 위치에 복사됩니다.

   ![chlimage_1-219](assets/chlimage_1-219.png)

   >[!NOTE]
   >
   >붙여넣기 작업이 완료될 때까지 도구 모음에서 **[!UICONTROL 붙여넣기]** 아이콘을 사용할 수 있습니다.

### 자산 {#moving-or-renaming-assets} 이동 또는 이름 바꾸기

1. 이동할 자산의 위치로 이동합니다.

1. 자산을 선택하고 도구 모음에서 **[!UICONTROL 이동]** 아이콘 ![move_icon](assets/move_icon.png)을 탭/클릭합니다.

1. 자산 이동 마법사에서 다음 중 하나를 수행합니다.

   * 자산을 이동한 후 자산의 이름을 지정합니다. 그런 다음 **[!UICONTROL 다음]**&#x200B;을 탭/클릭하여 계속 진행합니다.

   * **[!UICONTROL 취소]**&#x200B;를 탭/클릭하여 프로세스를 중지합니다.
   >[!NOTE]
   >
   >* 새 위치에 해당 이름의 자산이 없는 경우 자산에 대해 동일한 이름을 지정할 수 있습니다. 하지만 자산을 같은 이름의 자산이 있는 위치로 이동하는 경우에는 다른 이름을 사용해야 합니다. 동일한 이름을 사용하면 변형된 이름이 자동으로 생성됩니다. 예를 들어, 에셋의 이름이 정사각형인 경우 사본에 대해 Square1 이름이 생성됩니다.
   >* 이름을 변경할 때 파일 이름에 공백을 사용할 수 없습니다.


1. **[!UICONTROL 대상 선택]** 대화 상자에서 다음 중 하나를 수행합니다.

   * 자산을 위한 새 위치로 이동한 다음 **[!UICONTROL 다음]**&#x200B;을 탭/클릭합니다.

   * **[!UICONTROL 뒤로]**&#x200B;를 탭/클릭하여 **[!UICONTROL 이름 바꾸기]** 화면으로 돌아갑니다.

1. 이동되는 자산에 참조 페이지, 자산 또는 컬렉션이 있는 경우 **[!UICONTROL 참조 조정]** 탭이 **[!UICONTROL 대상 선택]** 탭 옆에 나타납니다.

   **[!UICONTROL 참조 조정]** 화면에서 다음 중 하나를 수행합니다.

   * 새 세부 사항에 따라 조정할 참조를 지정한 다음 **[!UICONTROL 이동]**&#x200B;을 탭/클릭합니다.

   * **[!UICONTROL 조정]** 열에서 자산에 대한 참조를 선택/선택 취소합니다.
   * **[!UICONTROL 뒤로]**&#x200B;를 탭/클릭하여 **[!UICONTROL 대상 선택]** 화면으로 돌아갑니다.

   * 이동 작업을 중지하려면 **[!UICONTROL 취소]**&#x200B;를 탭/클릭합니다.

   참조를 업데이트하지 않으면 에셋의 이전 경로를 계속 가리킵니다. 참조를 조정하면 새 자산 경로로 업데이트됩니다.

### 변환 관리 {#managing-renditions}

1. 원본을 제외한 자산에 대한 변환을 추가하거나 제거할 수 있습니다. 표현물을 추가하거나 제거할 자산의 위치로 이동합니다.

1. 자산을 탭/클릭하여 자산 페이지를 엽니다.

   ![chlimage_1-220](assets/chlimage_1-220.png)

1. 글로벌 탐색 아이콘을 탭/클릭하고 목록에서 **[!UICONTROL 표현물]**&#x200B;을 선택합니다.

   ![renditions_menu](assets/renditions_menu.png)

1. **[!UICONTROL 표현물]** 패널에서 자산에 대해 생성된 표현물 목록을 봅니다.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >기본적으로 [!DNL Experience Manager Assets]은(는) 미리 보기 모드에서 자산의 원래 변환을 표시하지 않습니다. 관리자는 오버레이를 사용하여 [!DNL Assets]을 구성하여 미리 보기 모드에서 원본 변환을 표시할 수 있습니다.

1. 변환을 보거나 삭제할 변환을 선택합니다.

   **변환 삭제**

   **[!UICONTROL 변환]** 패널에서 변환을 선택한 다음 도구 모음에서 **[!UICONTROL 변환 삭제]** 아이콘을 탭/클릭합니다. 자산 처리가 완료된 후에는 변환을 일괄적으로 삭제할 수 없습니다. 개별 자산의 경우 사용자 인터페이스에서 수동으로 변환을 제거할 수 있습니다. 여러 자산의 경우 [!DNL Experience Manager]을(를) 사용자 지정하여 특정 표현물을 삭제하거나 자산을 삭제하고 삭제된 자산을 다시 업로드할 수 있습니다.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **새 변환 업로드**

   자산에 대한 자산 세부 사항 페이지로 이동하고 도구 모음에서 **[!UICONTROL 변환 추가]** 아이콘을 탭/클릭하여 자산에 대한 새 변환을 업로드합니다.

   ![chlimage_1-221](assets/chlimage_1-221.png)

   >[!NOTE]
   >
   >**[!UICONTROL 표현물]** 패널에서 변환을 선택하면 도구 모음이 컨텍스트를 변경하고 표현물과 관련된 작업만 표시합니다. [렌디션 업로드] 아이콘과 같은 옵션이 표시되지 않습니다. 도구 모음에서 이러한 옵션을 보려면 자산의 세부 사항 페이지로 이동합니다.

   이미지 또는 비디오 자산의 세부 사항 페이지에 표시할 변환의 크기를 구성할 수 있습니다. 지정한 차원에 따라 Assets는 표현물을 정확하거나 가장 가까운 크기로 표시합니다.

   이미지의 변환 크기를 자산 세부 사항 수준에서 구성하려면 `renditionpicker` 노드(`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`)를 오버레이하고 width 속성의 값을 구성합니다. 이미지 크기에 따라 자산 세부 정보 페이지에서 변환을 사용자 정의하려면 속성 **[!UICONTROL 크기(긴)(KB]**)를 구성합니다. 크기 기반 맞춤화의 경우 일치하는 변환의 크기가 원본보다 큰 경우 속성 `preferOriginal`은 원본에 환경 설정을 할당합니다.

   마찬가지로 `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`을(를) 오버레이하여 주석 페이지 이미지를 사용자 정의할 수 있습니다.

   ![chlimage_1-222](assets/chlimage_1-222.png)

   비디오 자산에 대한 변환 크기를 구성하려면 `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker` 위치의 CRX 저장소의 `videopicker` 노드로 이동하여 노드를 오버레이한 다음 적절한 속성을 편집합니다.

   >[!NOTE]
   >
   >비디오 주석은 HTML5 호환 비디오 포맷이 있는 브라우저에서만 지원됩니다. 또한 브라우저에 따라 다른 비디오 형식이 지원됩니다.

## 자산 {#delete-assets} 삭제

다른 페이지에서 들어오는 참조를 해결하거나 제거하려면 자산을 삭제하기 전에 관련 참조를 업데이트합니다.

또한 오버레이를 사용하여 강제 삭제 단추를 비활성화하여 사용자가 참조된 자산을 삭제하지 않고 끊어진 링크를 남기지 못하도록 합니다.

1. 삭제할 자산의 위치로 이동합니다.

1. 자산을 선택하고 도구 모음에서 **[!UICONTROL 삭제]** 아이콘을 탭/클릭합니다.

   ![delete_icon](assets/delete_icon.png)

1. 확인 대화 상자에서 다음을 클릭합니다.

   * **[!UICONTROL 작업]** 을 중지하려면 취소됨
   * 해당 작업을 승인하려면 **[!UICONTROL 삭제]**

      * 자산에 참조가 없으면 자산이 삭제됩니다.
      * 자산에 참조가 있으면, 오류 메시지가 **하나 이상의 자산이 참조되었다고 표시됩니다.** **[!UICONTROL 강제 삭제]**&#x200B;나 **[!UICONTROL 취소]**&#x200B;를 선택할 수 있습니다.

   >[!NOTE]
   >
   >자산을 삭제할 수 있으려면 dam/asset에 대한 삭제 권한이 필요합니다. 수정 권한만 있는 경우 자산 메타데이터만 편집하고 자산에 주석을 추가할 수 있습니다. 그러나 자산이나 해당 메타데이터는 삭제할 수 없습니다.

   >[!NOTE]
   >
   >다른 페이지에서 들어오는 참조를 해결하거나 제거하려면 자산을 삭제하기 전에 관련 참조를 업데이트합니다.
   >
   >
   >또한 오버레이를 사용하여 강제 삭제 단추를 비활성화하여 사용자가 참조된 자산을 삭제하지 않고 끊어진 링크를 남기지 못하도록 합니다.

## 자산 다운로드 {#download-assets}

[자산 [!DNL Experience Manager]](/help/assets/download-assets-from-aem.md)에서 다운로드를 참조하십시오.

## 자산 {#publish-assets} 게시 또는 게시 취소

1. 게시할 자산 또는 자산 폴더의 위치 또는 게시 환경에서 제거할 자산 폴더(게시 취소)로 이동합니다.

1. 게시 또는 게시 취소할 에셋 또는 폴더를 선택하고 도구 모음에서 **[!UICONTROL 발행물 관리]** ![발행물 관리 옵션](assets/do-not-localize/globe-publication.png) 옵션을 선택합니다. 또는 빠르게 게시하려면 도구 모음에서 **[!UICONTROL 빠른 게시]** 옵션을 선택합니다. 게시할 폴더에 빈 폴더가 포함되어 있으면 빈 폴더가 게시되지 않습니다.

1. 필요에 따라 **[!UICONTROL 게시]** 또는 **[!UICONTROL 게시 취소]** 옵션을 선택합니다.

   ![게시 취소 작업](assets/unpublish_action.png)
   *그림:게시 및 게시 취소 옵션과 예약 옵션을 사용합니다.*

1. **[!UICONTROL 지금]**&#x200B;을 선택하여 에셋에 즉시 작업을 수행하거나 **[!UICONTROL 나중에]**&#x200B;를 선택하여 작업을 예약합니다. **[!UICONTROL 나중에]** 옵션을 선택하는 경우 날짜 및 시간을 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. 자산을 게시할 때 자산이 다른 자산을 참조하는 경우 해당 참조가 마법사에 나열됩니다. 마지막 게시 이후 게시 취소되거나 수정된 참조만 표시됩니다. 게시할 참조를 선택합니다.

1. 게시를 취소할 때 자산이 다른 자산을 참조하는 경우 게시를 취소할 참조를 선택합니다. **[!UICONTROL 게시 취소]**&#x200B;를 클릭합니다. 확인 대화 상자에서 **[!UICONTROL 취소]**&#x200B;를 클릭하여 작업을 중지하거나 **[!UICONTROL 게시 취소]**&#x200B;를 클릭하여 지정된 날짜에 에셋의 게시를 취소할지 확인합니다.

자산 또는 폴더 게시 또는 게시 취소와 관련된 다음 제한 사항과 팁을 이해합니다.

* [!UICONTROL 게시 관리] 옵션은 복제 권한이 있는 사용자 계정에서만 사용할 수 있습니다.
* 복잡한 자산을 게시 취소하는 동안 자산만 게시 취소합니다. 게시된 다른 자산에서 참조될 수 있으므로 참조 자료의 게시를 취소하지 마십시오.
* 빈 폴더가 게시되지 않습니다.
* 처리 중인 자산을 게시하면 원래 컨텐츠만 게시됩니다. 변환이 없습니다. 처리가 완료될 때까지 기다린 다음 처리가 완료되면 자산을 게시하거나 다시 게시하십시오.

## 닫힌 사용자 그룹 {#closed-user-group}

닫힌 사용자 그룹(CUG)을 사용하여 [!DNL Experience Manager]에서 게시된 특정 자산 폴더에 대한 액세스를 제한합니다. 폴더에 대해 CUG를 만드는 경우 폴더(폴더 자산 및 하위 폴더 포함)에 대한 액세스는 할당된 구성원 또는 그룹으로만 제한됩니다. 폴더에 액세스하려면 보안 자격 증명을 사용하여 로그인해야 합니다.

CUG는 자산에 대한 액세스를 제한하는 추가 방법입니다. 폴더에 대한 로그인 페이지를 구성할 수도 있습니다.

1. 자산 UI에서 폴더를 선택하고 도구 모음에서 속성 아이콘을 탭/클릭하여 속성 페이지를 표시합니다.
1. **[!UICONTROL 권한]** 탭에서 **[!UICONTROL 닫힌 사용자 그룹]**&#x200B;에 구성원 또는 그룹을 추가합니다.

   ![add_user](assets/add_user.png)

1. 사용자가 폴더에 액세스할 때 로그인 화면을 표시하려면 **[!UICONTROL 활성화]** 옵션을 선택합니다. 그런 다음 [!DNL Experience Manager]에서 로그인 페이지의 경로를 선택하고 변경 내용을 저장합니다.

   ![login_page](assets/login_page.png)

   >[!NOTE]
   >
   >로그인 페이지의 경로를 지정하지 않으면 게시 인스턴스에 기본 로그인 페이지가 표시됩니다.[!DNL Experience Manager]

1. 폴더를 게시한 다음 게시 인스턴스에서 액세스합니다. 로그인 화면이 표시됩니다.
1. CUG 회원인 경우 보안 자격 증명을 입력합니다. [!DNL Experience Manager] 인증 후 폴더가 표시됩니다.

## 자산 검색 {#search-assets}

자산 검색은 크리에이티브가 추가적으로 사용하거나 비즈니스 사용자 및 마케터가 자산을 안전하게 관리하거나 DAM 관리자의 관리를 위해 디지털 자산 관리 시스템을 사용하는 데 중요합니다.

가장 적절한 자산을 검색하고 사용하기 위한 단순, 고급 및 사용자 지정 검색을 보려면  [!DNL Experience Manager]](/help/assets/search-assets.md)에서 [자산 검색을 참조하십시오.

## 빠른 작업 {#quick-actions}

빠른 작업 아이콘은 한 번에 한 자산에 사용할 수 있습니다. 장치에 따라 다음 작업을 수행하여 빠른 작업 아이콘을 표시합니다.

* 터치 장치:길게 터치하세요. 예를 들어, iPad에서는 빠른 작업이 표시되도록 자산을 길게 탭할 수 있습니다.
* 비접촉 장치:포인터를 가져갑니다. 예를 들어 데스크톱 장치에서는 포인터를 에셋 축소판 위에 두면 빠른 작업 표시줄이 표시됩니다.

## 이미지 편집 {#editing-images}

[!DNL Experience Manager Assets] 인터페이스의 편집 도구를 사용하여 이미지 자산에 대해 작은 편집 작업을 수행할 수 있습니다. 이미지에서 자르기, 회전, 뒤집기 및 기타 편집 작업을 수행할 수 있습니다. 이미지 맵을 자산에 추가할 수도 있습니다.

>[!NOTE]
>
>일부 구성 요소의 경우 [전체 화면] 모드에 사용할 수 있는 추가 옵션이 있습니다.

1. 편집 모드에서 자산을 열려면 다음 중 하나를 수행합니다.

   * 자산을 선택한 다음 도구 모음에서 **[!UICONTROL 편집]** 아이콘을 클릭/탭합니다.
   * 카드 보기의 자산에 나타나는 **[!UICONTROL 편집]** 아이콘을 탭/클릭합니다.
   * 자산 페이지의 도구 모음에서 **[!UICONTROL 편집]** 아이콘을 탭/클릭합니다.

   ![edit_icon](assets/edit_icon.png)

1. 이미지를 자르려면 **자르기** 아이콘을 탭/클릭합니다.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. 목록에서 원하는 옵션을 선택합니다. 선택한 옵션에 따라 자르기 영역이 이미지에 나타납니다. **Free Hand** 옵션을 사용하면 종횡비 제한 없이 이미지를 자를 수 있습니다.

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. 잘라낼 영역을 선택하고 이미지의 크기를 조정하거나 위치를 변경합니다.
1. **완료** 아이콘(오른쪽 상단)을 사용하여 이미지를 자릅니다. **완료** 아이콘을 클릭하면 표현물의 재생도 트리거됩니다.

   ![chlimage_1-228](assets/chlimage_1-228.png)

1. 오른쪽 위에 있는 **실행 취소** 및 **다시 실행** 아이콘을 사용하여 잘리지 않은 이미지로 되돌리거나 잘린 이미지를 각각 유지합니다.

   ![chlimage_1-229](assets/chlimage_1-229.png)

1. 이미지를 시계 방향 또는 반시계 방향으로 회전하려면 해당 회전 아이콘을 탭/클릭합니다.

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. 이미지를 가로 또는 세로로 뒤집으려면 적절한 뒤집기 아이콘을 탭/클릭합니다.

   ![chlimage_1-231](assets/chlimage_1-231.png)

1. **완료** 아이콘을 탭/클릭하여 변경 내용을 저장합니다.

   ![chlimage_1-232](assets/chlimage_1-232.png)

>[!NOTE]
>
>이미지 편집은 BMP, GIF, PNG 및 JPEG 파일 포맷에 대해 지원됩니다.

<!-- You can also add image maps using the image editor. For details, see [Adding Image Maps](/help/assets/image-maps.md). -->

>[!NOTE]
>
>TXT 파일을 편집하려면 Configuration Manager에서 **Day CQ Link Externalizer**&#x200B;를 설정합니다.

## 타임라인 {#timeline}

타임라인을 사용하면 자산에 대한 활성 워크플로우, 댓글/주석, 활동 로그 및 버전과 같이 선택한 항목에 대한 다양한 이벤트를 볼 수 있습니다.

![자산에 대한 타임라인 항목 ](assets/sort_timeline.gif)
*정렬그림:자산에 대한 타임라인 항목 정렬*

>[!NOTE]
>
>[컬렉션 콘솔](/help/assets/manage-collections.md#navigate-the-collections-console)에서 **[!UICONTROL 모두 표시]** 목록은 주석 및 워크플로우만 볼 수 있는 옵션을 제공합니다. 또한 타임라인은 콘솔에 나열된 최상위 수준의 컬렉션에 대해서만 표시됩니다. 컬렉션 내에서 탐색하는 경우에는 표시되지 않습니다.

>[!NOTE]
>
>타임라인에는 컨텐츠 조각](content-fragments/content-fragments.md)에 대한 몇 가지 [옵션이 포함되어 있습니다.

## 주석 달기 {#annotating}

주석은 이미지나 비디오에 추가된 주석 또는 설명 노트입니다. 주석을 통해 마케터는 공동 작업을 수행하고 에셋에 대한 피드백을 남길 수 있습니다.

비디오 주석은 HTML5 호환 비디오 포맷이 있는 브라우저에서만 지원됩니다. 자산 지원 비디오 형식은 브라우저에 따라 다릅니다.

>[!NOTE]
>
>컨텐츠 조각에 대해 [주석은 조각 편집기](content-fragments/content-fragments.md)에 생성됩니다.

1. 주석을 추가할 자산의 위치로 이동합니다.
1. 다음 중 하나에서 **[!UICONTROL 주석]** 아이콘을 탭/클릭합니다.

   * [빠른 작업](#quick-actions)
   * 자산을 선택하거나 자산 페이지로 이동한 후 도구 모음에서

   ![chlimage_1-233](assets/chlimage_1-233.png)

1. 타임라인 아래쪽에 있는 **[!UICONTROL 주석]** 상자에 주석을 추가합니다. 또는 이미지의 영역을 마크업하고 **[!UICONTROL 주석 추가]** 대화 상자에 주석을 추가합니다.

   ![chlimage_1-234](assets/chlimage_1-234.png)

<!--
1. To notify a user about an annotation, specify the email address of the user and add the comment. For example, to notify Aaron MacDonald about an annotation, enter @aa. Hints for all matching users is displayed in a list. Select Aaron's email address from the list to tag her with the comment. Similarly, you can tag more users anywhere within the annotation or before or after it.
-->

>[!NOTE]
>
>관리자가 아닌 사용자의 경우 CRXDE의 `/home`에서 사용자에게 읽기 권한이 있는 경우에만 제안이 표시됩니다.

![chlimage_1-235](assets/chlimage_1-235.png)

1. 주석을 추가한 후 **[!UICONTROL 추가]**&#x200B;를 클릭하여 저장합니다. 주석에 대한 알림이 Aaron에게 전송됩니다.

   ![chlimage_1-236](assets/chlimage_1-236.png)

   >[!NOTE]
   >
   >저장하기 전에 여러 주석을 추가할 수 있습니다.

1. **[!UICONTROL 닫기]**&#x200B;를 탭/클릭하여 주석 모드에서 종료합니다.
1. 알림을 보려면 Aaron MacDonald의 자격 증명으로 자산에 로그인하고 **[!UICONTROL 알림]** 아이콘을 클릭하여 알림을 봅니다.

   >[!NOTE]
   >
   >비디오 자산에 주석을 추가할 수도 있습니다. 비디오에 주석을 달 때 프레임에 주석을 달 수 있도록 플레이어가 일시 중지됩니다. 자세한 내용은 [비디오 자산 관리](manage-video-assets.md)를 참조하십시오.

1. 다른 색상을 선택하여 사용자 간에 구분할 수 있도록 하려면 프로필 아이콘을 클릭/탭하고 **[!UICONTROL 내 환경 설정]**&#x200B;을 클릭/탭합니다.

   ![chlimage_1-237](assets/chlimage_1-237.png)

   **[!UICONTROL 주석 색상]** 상자에 원하는 색상을 지정한 다음 **[!UICONTROL 승인]**&#x200B;을 클릭/탭합니다.

   ![chlimage_1-238](assets/chlimage_1-238.png)

>[!NOTE]
>
>컬렉션에 주석을 추가할 수도 있습니다. 그러나 컬렉션에 하위 컬렉션이 포함되어 있으면 상위 컬렉션에만 주석/주석을 추가할 수 있습니다. [주석] 옵션은 자식 컬렉션에 사용할 수 없습니다.

### 저장된 주석 보기 {#viewing-saved-annotations}

1. 자산에 대해 저장된 주석을 보려면 자산의 위치로 이동하고 자산의 자산 페이지를 엽니다.

1. GlobalNav 아이콘을 탭/클릭하고 목록에서 **[!UICONTROL 타임라인]**&#x200B;을 선택합니다.

   ![chlimage_1-239](assets/chlimage_1-239.png)

1. 타임라인의 **[!UICONTROL 모두 표시]** 목록에서 **[!UICONTROL 주석]**&#x200B;을 선택하여 주석을 기반으로 결과를 필터링합니다.

   ![chlimage_1-240](assets/chlimage_1-240.png)

   **[!UICONTROL 타임라인]** 패널에서 주석을 탭/클릭하여 이미지에 해당하는 주석을 봅니다.

   ![chlimage_1-241](assets/chlimage_1-241.png)

   특정 주석을 삭제하려면 **[!UICONTROL 삭제]**&#x200B;를 탭/클릭합니다.

### 인쇄 주석 {#printing-annotations}

자산에 주석이 있거나 검토 워크플로우가 있는 경우 오프라인 검토를 위해 주석 및 검토 상태와 함께 자산을 PDF 파일로 인쇄할 수 있습니다.

주석만 인쇄하거나 상태를 검토하도록 선택할 수도 있습니다.

주석과 검토 상태를 인쇄하려면 **[!UICONTROL 인쇄]** 아이콘을 탭/클릭하고 마법사의 지침을 따릅니다. **[!UICONTROL 인쇄]** 아이콘은 자산에 하나 이상의 주석 또는 검토 상태가 할당된 경우에만 도구 모음에 표시됩니다.

1. 자산 UI에서 자산에 대한 미리 보기 페이지를 엽니다.
1. 다음 중 하나를 수행하십시오.

   * 모든 주석과 검토 상태를 인쇄하려면 3단계를 건너뛰고 4단계로 바로 이동합니다.
   * 특정 주석을 인쇄하고 상태를 검토하려면 [타임라인](/help/assets/manage-digital-assets.md#timeline)을 연 다음 3단계로 이동합니다.

1. 특정 주석을 인쇄하려면 타임라인에서 주석을 선택합니다.

   ![chlimage_1-242](assets/chlimage_1-242.png)

   검토 상태만 인쇄하려면 타임라인에서 선택합니다.

   ![chlimage_1-243](assets/chlimage_1-243.png)

1. 도구 모음에서 **[!UICONTROL 인쇄]** 아이콘을 탭/클릭합니다.

   ![chlimage_1-244](assets/chlimage_1-244.png)

1. [인쇄] 대화 상자에서 PDF에 주석/검토 상태를 표시할 위치를 선택합니다. 예를 들어 인쇄된 이미지가 포함된 페이지의 오른쪽 상단에 주석/상태를 인쇄하려면 **왼쪽 위** 설정을 사용합니다. 기본적으로 선택되어 있습니다.

   ![chlimage_1-245](assets/chlimage_1-245.png)

   인쇄 PDF에 주석/상태를 표시할 위치에 따라 다른 설정을 선택할 수 있습니다. 인쇄된 자산과 별개의 페이지에 주석/상태를 표시하려면 **[!UICONTROL 다음 페이지]**&#x200B;를 선택합니다.

1. **[!UICONTROL 인쇄]**&#x200B;를 클릭합니다. 2단계에서 선택한 옵션에 따라, 생성된 PDF에 지정된 위치에 주석/상태가 표시됩니다. 예를 들어 **왼쪽 위** 설정을 사용하여 주석과 검토 상태를 모두 인쇄하도록 선택한 경우 생성된 출력이 여기에 설명된 PDF 파일과 유사합니다.

   ![chlimage_1-246](assets/chlimage_1-246.png)

1. 오른쪽 상단의 옵션을 사용하여 PDF를 다운로드하거나 인쇄합니다.

   ![chlimage_1-247](assets/chlimage_1-247.png)

   글꼴 색상, 크기 및 스타일, 주석 및 상태의 배경색 등 렌더링된 PDF 파일의 모양을 수정하려면 Configuration Manager에서 **[!UICONTROL 주석 PDF 구성]**&#x200B;을 열고 원하는 옵션을 수정합니다. 예를 들어, 승인된 상태의 표시 색상을 변경하려면 해당 필드에서 색상 코드를 수정합니다. 주석의 글꼴 색상 변경에 대한 자세한 내용은 [주석 달기](/help/assets/manage-digital-assets.md#annotating)를 참조하십시오.

   ![chlimage_1-248](assets/chlimage_1-248.png)

   렌더링된 PDF 파일로 돌아가 새로 고칩니다. 새로 고친 PDF는 변경한 내용을 반영합니다.

## 에셋 버전 관리 {#asset-versioning}

버전 매기기를 통해 특정 시점의 디지털 자산 스냅샷을 만들 수 있습니다. 버전 관리를 통해 나중에 에셋을 이전 상태로 복원할 수 있습니다. 예를 들어, 자산에 대한 변경 내용을 취소하려는 경우 편집되지 않은 버전의 자산을 복원합니다.

다음은 버전을 만드는 시나리오입니다.

* 다른 응용 프로그램에서 이미지를 수정하고 자산에 업로드합니다. 원본 이미지를 덮어쓰지 않도록 이미지의 버전이 만들어집니다.
* 자산의 메타데이터를 편집합니다.
* [!DNL Experience Manager] 데스크톱 앱을 사용하여 기존 자산을 체크 아웃하고 변경 내용을 저장합니다. 자산이 저장될 때마다 새 버전이 만들어집니다.

워크플로우에서 자동 버전 관리를 활성화할 수도 있습니다. 자산에 대한 버전을 만들면 메타데이터 및 표현물이 버전과 함께 저장됩니다. 변환은 업로드된 JPEG 파일의 PNG 변환과 같은 동일한 이미지의 대체 요소로 렌더링됩니다.

버전 관리 기능을 사용하여 다음을 수행할 수 있습니다.

* 자산의 버전을 만듭니다.
* 자산에 대한 현재 개정판을 봅니다.
* 자산을 이전 버전으로 복원합니다.

1. 버전을 만들 자산의 위치로 이동하고, 자산을 탭/클릭하여 자산 페이지를 엽니다.

1. 전역 탐색 아이콘을 탭/클릭하고 메뉴에서 **[!UICONTROL 타임라인]**&#x200B;을 선택합니다.

   ![타임라인](assets/timeline.png)

1. 하단에 있는 **[!UICONTROL 작업]**(화살표) 아이콘을 탭/클릭하여 자산에 대해 수행할 수 있는 사용 가능한 작업을 봅니다.

   ![chlimage_1-249](assets/chlimage_1-249.png)

1. **[!UICONTROL 다른 버전으로 저장]**&#x200B;을 탭/클릭하여 자산에 대한 버전을 만듭니다.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. 레이블 및 주석을 추가한 다음 **[!UICONTROL 만들기]**&#x200B;를 클릭하여 버전을 만듭니다. 또는 **취소**&#x200B;를 탭/클릭하여 작업을 종료합니다.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. 새 버전을 보려면 자산 세부 사항 페이지 또는 자산 UI에서 타임라인에서 **[!UICONTROL 모두 표시]** 목록을 열고 **[!UICONTROL 버전]**&#x200B;을 선택합니다. 자산에 대해 만들어진 모든 버전은 타임라인 탭 아래에 나열됩니다. 드롭다운 화살표를 클릭하고 목록에서 **[!UICONTROL 버전]**&#x200B;을 선택하여 버전을 표시하도록 목록을 필터링할 수 있습니다.

   ![versions_option](assets/versions_option.png)

1. 자산을 미리 보거나 자산 UI에 표시할 특정 버전을 선택합니다.

   ![select_version](assets/select_version.png)

1. 자산 UI의 특정 버전으로 되돌리려면 버전에 대한 레이블 및 주석을 추가합니다.

   ![save_version](assets/save_version.png)

1. 버전에 대한 미리 보기를 생성하려면 **[!UICONTROL 버전 미리 보기]**&#x200B;를 탭/클릭합니다.
1. 자산 UI에 이 버전을 표시하려면 **[!UICONTROL 이 버전으로 되돌리기]**&#x200B;를 선택합니다.
1. 두 버전 간에 비교하려면 자산의 자산 페이지로 이동하여 현재 버전과 비교할 버전을 탭/클릭합니다.

   ![select_version_tocompare](assets/select_version_tocompare.png)

1. 타임라인에서 비교할 버전을 선택하고 슬라이더를 왼쪽으로 드래그하여 현재 버전 위에 이 버전을 오버레이하고 비교할 수 있습니다.

   ![compare_versions](assets/compare_versions.png)

### 자산 {#starting-a-workflow-on-an-asset}에 대한 워크플로우 시작

1. 워크플로우를 시작할 자산의 위치로 이동하고 자산을 탭/클릭하여 자산 페이지를 엽니다.
1. 전역 탐색 아이콘을 탭/클릭하고 메뉴에서 **[!UICONTROL 타임라인]**&#x200B;을 선택하여 타임라인을 표시합니다.

   ![timeline-1](assets/timeline-1.png)

1. 하단에 있는 **[!UICONTROL 작업]**(화살표) 아이콘을 탭/클릭하여 자산에 사용할 수 있는 작업 목록을 엽니다.

   ![chlimage_1-252](assets/chlimage_1-252.png)

1. 목록에서 **[!UICONTROL 워크플로우 시작]**&#x200B;을 탭/클릭합니다.

   ![chlimage_1-253](assets/chlimage_1-253.png)

1. **[!UICONTROL 워크플로우 시작]** 대화 상자의 목록에서 워크플로우 모델을 선택합니다.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. (선택 사항) 워크플로우 인스턴스를 참조하는 데 사용할 수 있는 워크플로우의 제목을 지정합니다.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. 대화 상자에서 **[!UICONTROL 시작]**&#x200B;을 탭/클릭한 다음 **[!UICONTROL 계속]**&#x200B;을 탭/클릭하여 확인합니다. 각 워크플로우 단계가 이벤트로 타임라인에 표시됩니다.

   ![chlimage_1-256](assets/chlimage_1-256.png)

## 컬렉션 {#collections}

컬렉션은 순차적 자산 세트입니다. 컬렉션을 사용하여 사용자 간에 자산을 공유합니다.

* 컬렉션은 이러한 자산에 대한 참조만 포함되기 때문에 다른 위치의 자산을 포함할 수 있습니다. 각 컬렉션은 자산의 참조 무결성을 유지합니다.
* 편집, 보기 등 다양한 권한 수준을 가진 여러 사용자와 컬렉션을 공유할 수 있습니다.

컬렉션 관리에 대한 자세한 내용은 [컬렉션 관리](/help/assets/manage-collections.md)를 참조하십시오.

## 데스크톱 앱 또는 Adobe 자산 링크 {#hide-expired-assets-via-acp-api}에서 자산을 볼 때 만료된 자산 숨기기

[!DNL Experience Manager] 데스크탑 앱을 사용하면 Windows 또는 Mac 데스크탑에서 DAM 저장소에 액세스할 수 있습니다. Adobe 자산 링크를 사용하면 지원되는 [!DNL Creative Cloud] 데스크톱 응용 프로그램 내에서 자산에 액세스할 수 있습니다.

[!DNL Experience Manager] 사용자 인터페이스 내에서 자산을 검색할 때 만료된 자산이 표시되지 않습니다. 데스크탑 앱 및 에셋 링크에서 에셋을 검색할 때 만료된 에셋을 보고, 검색하고, 가져오는 것을 방지하기 위해 관리자는 다음 구성을 수행할 수 있습니다. 구성은 관리자 권한에 관계없이 모든 사용자에 대해 작동합니다.

다음 CURL 명령을 실행합니다. 자산에 액세스하는 사용자에 대해 `/conf/global/settings/dam/acpapi/`에 대한 읽기 액세스 권한을 확인합니다. `dam-user` 그룹에 속한 사용자는 기본적으로 권한이 있습니다.

```curl
curl -v -u admin:admin --location --request POST 'http://localhost:4502/conf/global/settings/dam/acpapi/configuration/_jcr_content' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'jcr:title=acpapiconfig' \
--data-urlencode 'hideExpiredAssets=true' \
--data-urlencode 'hideExpiredAssets@TypeHint=Boolean' \
--data-urlencode 'jcr:primaryType=nt:unstructured' \
--data-urlencode '../../jcr:primaryType=sling:Folder'
```

자세한 내용은 데스크톱 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) 및 [Adobe 자산 링크 사용 방법](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html)을 사용하여 [DAM 자산을 검색하는 방법을 참조하십시오.
