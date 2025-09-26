---
title: ' [!DNL Dynamic Media] 템플릿을 관리하는 방법'
description: WYSIWYG 템플릿 편집기를 사용하여  [!DNL Dynamic Media] 템플릿을 만들고 여러 이미지, 텍스트 및 모양 레이어를 포함하여 배너 및 전단을 빠르게 만들고 다운스트림 애플리케이션에서 사용하는 방법에 대해 알아봅니다.
hide: true
role: User
exl-id: 07de648e-4ae2-4524-8e05-3cf10bb6006d
source-git-commit: d82d40ebb5417dfb7ce37c9995c5cadb74a2fe11
workflow-type: tm+mt
source-wordcount: '3780'
ht-degree: 1%

---


# 템플릿 [!DNL Dynamic Media]개{#dynamic-media-templates}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services와의 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 활성화</b></a>
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

WYSIWYG 템플릿 편집기인 [!DNL Dynamic Media] 템플릿을 사용하여 배너 및 전단에 대한 사용자 지정 가능한 실시간 템플릿을 만듭니다. [!DNL Dynamic Media] 템플릿을 게시하고 다운스트림 애플리케이션에서 사용합니다. [!DNL Dynamic Media] 템플릿에는 이미지 및 텍스트 레이어가 포함됩니다. 템플릿의 이미지 및 텍스트 레이어에 매개 변수를 추가하고 [[!DNL Dynamic Media] URL](https://experienceleague.adobe.com/ko/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media)을 사용하여 레이어의 위치를 변경하고 크기를 조정하며 해당 내용을 실시간으로 업데이트합니다.

몇 가지 주요 기능은 다음과 같습니다.

* **[!DNL Dynamic Media]WYSIWYG 템플릿 편집기:** 이미지 및 텍스트 레이어를 사용하여 사용자 지정 배너를 만듭니다.
* **레이어 매개 변수화:** 레이어의 동적 키-값 쌍을 정의하여 실시간 업데이트를 사용하도록 설정합니다.
* **[!DNL Dynamic Media]URL 지원:** 템플릿에 [!DNL Dynamic Media] URL을 사용하여 자사 또는 타사 응용 프로그램의 개인화된 값을 통합합니다.
* **레이어 가시성 컨트롤:** 필요에 따라 레이어를 동적으로 숨기거나 표시합니다.
* **스마트 텍스트 크기 조정:** 지정된 영역에 맞게 텍스트 크기를 자동으로 조정합니다.

[!DNL Dynamic Media] 템플릿의 주요 이점 중 일부는 다음과 같습니다.

* **최적화 1:1 Personalization:** 콘텐츠를 실시간 고객 신호에 맞게 조정합니다.
* **수작업 감소:** 콘텐츠 생성 및 관리를 자동화하고 가속화합니다.
* **일관성 있는 옴니채널 환경을 확인합니다.** 채널 전반에서 브랜드 일관성을 유지합니다.
* **효과적으로 콘텐츠 재사용:** 매개 변수가 있는 동적 템플릿을 사용하여 콘텐츠와 크기를 한 번만 사용하지 않도록 합니다.
* **위험 완화:** 가격, 할인 및 링크를 실시간으로 업데이트합니다.
* **고객 참여 개선:** 상황에 맞는 대화형 경험을 제공합니다.

>[!NOTE]
>
>향상된 보안 SKU를 구독하는 고객은 해당 클라우드 서비스 프로그램에서 [!DNL Dynamic Media] 템플릿을 포함한 [!DNL Dynamic Media] 기능을 사용할 수 없습니다.

이 비디오에서 단계별로 [!DNL Dynamic Media] 템플릿을 만드는 방법을 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/3443281)

## 시작하기에 앞서{#prerequisites-for-dynamic-media-wysiwyg-template}

[!DNL Dynamic Media] 템플릿을 만들고 해당 게재 URL을 생성하려면 다음 요구 사항을 충족하십시오.

1. [!DNL Dynamic Media]에 액세스.
1. [!DNL Assets View] 홈 페이지의 **[!UICONTROL Dynamic Media Assets]**&#x200B;에 템플릿을 저장할 폴더가 있습니다. [Dynamic Media Assets](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view)에서 해당 폴더를 복제하려면 ![폴더를 ](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets &#x200B;]**&#x200B;Assets&#x200B;**[!UICONTROL &#x200B;에서 만듭니다&#x200B;]**.
1. [ [!DNL AEM Assets] 인스턴스에서 사용할 수 있는 이미지를  [!DNL Dynamic Media] 동기화하여 템플릿을 만드는 데 사용](/help/assets/dynamic-media/config-dm.md)합니다.
1. 템플릿을 만든 후 템플릿의 게재 URL을 생성하는 데 사용할 이미지를 게시합니다. 게재 URL은 다운스트림 애플리케이션에서 사용할 수 있습니다.
1. 템플릿의 텍스트 레이어에서 기본 [!UICONTROL Adobe Sans F2] 글꼴 이외의 글꼴을 사용하려면 [글꼴 파일을 AEM 및 Dynamic Media에 동시에 업로드하고 게시합니다](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation). [지원되는 글꼴 파일 형식은 AFM, OTF, PFB, PFM, PhotoFont, TTC, TTF](https://experienceleague.adobe.com/ko/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats)입니다. 또한 기존 글꼴을 사용하려면 [재처리](/help/assets/reprocessing-assets-view.md)해야 합니다. 자세한 내용은 [글꼴](https://experienceleague.adobe.com/ko/docs/dynamic-media-classic/using/support-files/fonts)을 참조하세요.<!--(On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**)-->
1. touch UI에서 다음을 확인하십시오.
   * **[!UICONTROL 구성 편집 페이지[!DNL Dynamic Media]에서]**&#x200B;기본적으로 비활성화됨&#x200B;**[!UICONTROL [!DNL Dynamic Media] (으)로 설정된]** 동기화 모드&#x200B;**[!UICONTROL 이(가) 모든 AEM 폴더에 적용되지 않습니다(]**&#x200B;모든 콘텐츠 동기화&#x200B;**[!UICONTROL 이(가) 선택되지 않음).]** 자세한 내용은 [Dynamic Media Cloud Service 구성](/help/assets/dynamic-media/config-dm.md)을 참조하십시오.
   * **[!UICONTROL [!DNL Dynamic Media]동기화 모드]**&#x200B;이(가) 생성 후 템플릿을 저장할 대상 폴더 또는 하위 폴더에 대해 **[!UICONTROL 하위 폴더에 대해 사용]**(으)로 설정되어 있습니다. 자세한 내용은 [구성 [!DNL Dynamic Media] Cloud Service](/help/assets/dynamic-media/config-dm.md)을 참조하십시오.

## [!DNL Dynamic Media] 템플릿 만들기{#how-to-create-dynamic-media-template}

[!DNL Dynamic Media] 템플릿을 만들려면 다음 단계를 수행하십시오.

<!--
1. Navigate to your [!DNL Assets View] and [create a folder](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**. The folder tree in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** replicates in **[!UICONTROL Dynamic Media Assets]**. Save your [!DNL Dynamic Media] template in this [!UICONTROL Dynamic Media Assets] folder.
1. Select ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** and [upload and publish your images to [!DNL AEM] and [!DNL Dynamic Media] simultaneously](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm#dynamic-media-publish-mode-set-to-upon-activation) to use them in creating the template. Publishing images is required to generate the template's delivery URL, after creating the template. The delivery URL can be used in downstream applications.
1. [Execute these asset uploading and publishing steps](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation) to upload and publish a font file to AEM and Dynamic Media simultaneously to use it in creating the template. [!UICONTROL Adobe Sans F2] is the only default font available in the text layer. [The supported font file formats are, AFM, OTF, PFB, PFM, PhotoFont, TTC, TTF](https://experienceleague.adobe.com/ko/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Ensure to [reprocess](/help/assets/reprocessing-assets-view.md) the existing fonts to use them in creating the template (On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**). See [Fonts](https://experienceleague.adobe.com/ko/docs/dynamic-media-classic/using/support-files/fonts) to know more about fonts.
-->

1. [빈 캔버스 만들기](#create-a-canvas)
1. [캔버스에 이미지 추가](#add-images-to-the-canvas)
1. [캔버스에 텍스트 레이어 추가](#add-text-to-the-canvas)
1. [캔버스에 모양 추가](#add-shapes-to-the-canvas)
1. [레이어 편집 또는 삭제](#edit-or-delete-a-layer)
1. [매개 변수 레이어](#parameterise-a-layer)

### 빈 캔버스 만들기{#create-a-canvas}

다음 단계를 실행하여 빈 캔버스를 만듭니다.

1. [!DNL Assets View]&#x200B;(으)로 이동하고 왼쪽 패널에서 사용할 수 있는 **[!UICONTROL Dynamic Media Assets]**&#x200B;을(를) 선택한 다음 폴더로 이동하여 해당 폴더에 템플릿을 저장합니다.

   ![Dynamic Media 템플릿](/help/assets/assets/DM-Assets1.png)

1. **[!UICONTROL 템플릿 만들기]**&#x200B;를 선택합니다. **[!UICONTROL 새 템플릿]** 대화 상자가 표시됩니다.

   ![실시간으로 사용자 지정할 수 있는 동적 템플릿을 만드는 방법](/help/assets/assets/new-template.png)

   >[!NOTE]
   >
   >  템플릿은 사용자가 만드는 위치에 저장됩니다. [!DNL Assets View] 홈 페이지에서 **[!UICONTROL Dynamic Media Assets]**&#x200B;을(를) 선택하고 **[!UICONTROL 템플릿 만들기]**&#x200B;를 클릭하여 **[!UICONTROL Dynamic Media Assets]** 루트 폴더에 템플릿을 저장합니다.

1. 템플릿 이름을 지정하고 캔버스 너비 및 높이를 정의한 다음 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 템플릿을 만드는 데 사용할 메뉴 옵션이 양쪽에 있는 빈 캔버스가 표시됩니다. 메뉴 옵션 위로 마우스를 가져가면 해당 도구 설명을 볼 수 있습니다.
   ![실시간 사용자 지정 가능한 템플릿](/help/assets/assets/blank-canvas-page.png)

   >[!NOTE]
   >
   > 허용되는 너비 및 높이 범위는 50~5000입니다.

**오른쪽 창의 메뉴 옵션:** 캔버스에 필요한 이미지 및 텍스트 레이어를 추가하려면 다음 옵션을 사용합니다.

* ![DM 템플릿](/help/assets/assets/add-image.svg): 캔버스에 이미지를 추가하려면 클릭하세요.
* ![사용자 지정 템플릿](/help/assets/assets/add-text.svg): 캔버스에 텍스트를 추가하려면 클릭하세요.
* ![사용자 지정 가능한 템플릿](/help/assets/assets/show-layers-list.svg): 캔버스에 있는 모든 레이어(이미지 및 텍스트) 목록을 보려면 클릭하세요. 캔버스에 추가된 모든 이미지와 텍스트는 별도의 레이어로 표시됩니다.

**왼쪽 창의 메뉴 옵션:** 다음의 일반 편집기 작업에 이 옵션을 사용합니다.

* ![DM 템플릿](/help/assets/assets/layer-selector.svg): ![DM 템플릿](/help/assets/assets/layer-selector.svg)을 선택하고 캔버스에서 레이어를 클릭하여 선택합니다.
* ![사용자 지정을 지원하는 템플릿](/help/assets/assets/bring-forward.svg): ![사용자 지정을 지원하는 템플릿](/help/assets/assets/bring-forward.svg)을 클릭하거나 키보드 단축키, **Ctrl** + **`]`**(Windows) 또는 **Cmd** + **`]`**(Mac)을 사용하여 선택한 레이어를 앞으로 가져옵니다.
* ![쉽게 사용자 지정할 수 있는 템플릿을 만드는 방법](/help/assets/assets/send-backward.svg): ![쉽게 사용자 지정할 수 있는 템플릿을 만드는 방법](/help/assets/assets/send-backward.svg)을 클릭하거나 키보드 단축키, **Ctrl** + **`[`**(Windows) 또는 **Cmd** + **`[`**(Mac)를 사용하여 선택한 레이어를 뒤로 보냅니다.
* ![즉시 사용자 지정할 수 있는 템플릿 만들기](/help/assets/assets/undo.svg): ![즉시 사용자 지정할 수 있는 템플릿 만들기](/help/assets/assets/undo.svg)를 클릭하거나 키보드 단축키, **Ctrl** + **Z**(Windows) 또는 **Cmd** + **Z**(Mac)를 사용하여 마지막 작업을 취소하십시오.
* ![배너를 빠르게 만드는 템플릿](/help/assets/assets/redo.svg): ![배너를 빠르게 만들려면 템플릿을 클릭](/help/assets/assets/redo.svg)하거나, 키보드 단축키, **Ctrl** + **Y**(Windows) 또는 **Cmd** + **Y**(Mac)를 사용하여 마지막 작업을 다시 실행하십시오.
* ![전단을 빠르게 만들려면](/help/assets/assets/zoom-in.svg): ![템플릿을 클릭하여 전단을 빠르게 만들거나](/help/assets/assets/zoom-in.svg) 키보드 단축키를 사용하거나 **Ctrl** + **+**(Windows) 또는 **Cmd** + **+**(Mac)을 사용하여 캔버스를 확대하십시오.
* 배너를 빠르게 만들려면 ![템플릿](/help/assets/assets/Zoom-out.svg): 배너를 빠르게 만들려면 ![템플릿을 클릭](/help/assets/assets/Zoom-out.svg)하거나, 키보드 단축키, **Ctrl** + **-**(Windows) 또는 **Cmd** + **-**(Mac)를 사용하여 캔버스를 축소하십시오.
* 편집 중인 텍스트나 속성이 없으면 **백스페이스** 또는 **삭제**&#x200B;를 눌러 선택한 레이어를 삭제합니다.

템플릿을 만드는 동안 언제든지 캔버스 차원을 편집하려면 ![템플릿을 클릭하여 전단을 빠르게 만들고](/help/assets/assets/show-layers-list.svg) 캔버스 레이어에서 더 많은 옵션(![](/help/assets/assets/three-dots.svg))을 선택하십시오.
![](/help/assets/assets/edit-canvas1.png)

>[!NOTE]
>
> 템플릿은 캔버스를 포함하여 최대 20개의 레이어를 허용합니다.

### 캔버스에 이미지 추가{#add-images-to-the-canvas}

다음 단계를 실행하여 캔버스에 이미지를 추가합니다.

1. ![즉시 배너 만들기](/help/assets/assets/add-image.svg)를 클릭하여 [자산 선택기](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) 패널을 엽니다. 패널에 [!DNL Dynamic Media]에 동기화된 AEM Assets 인스턴스의 이미지가 표시됩니다.
1. 패널을 찾아보거나 검색 막대에서 키워드를 사용하여 특정 이미지를 찾습니다.
1. 캔버스에 이미지를 드래그하여 놓아 사용하십시오. 캔버스에서 레이어 크기 조정 또는 위치 조정은 [**[!UICONTROL 속성 패널]**](#reposition-resize-delete-a-layer)을 참조하세요.
   ![초 내에 배너 만들기](/help/assets/assets/add-image-to-canvas.png)
1. **[!UICONTROL 균일한 반경]** 토글을 활성화하고 **[!UICONTROL 모서리 반경]** 슬라이더를 사용하여 이미지의 네 모퉁이의 원형률을 모두 균일하게 조정합니다. 토글을 비활성화하여 각 모서리에 특정 반지름 값을 지정하여 코너 원형률을 사용자 정의합니다.
   ![이미지의 모퉁이 원형율 조정](/help/assets/assets/enable-uniform-radius-image.png)

### 캔버스에 텍스트 레이어 추가{#add-text-to-the-canvas}

다음 단계를 실행하여 텍스트 레이어를 캔버스에 추가합니다.

1. ![새 배너를 빠르게 만들기](/help/assets/assets/add-text.svg)를 클릭하여 텍스트 레이어를 캔버스에 추가하고 속성 패널을 엽니다.
1. 레이어를 선택하고 텍스트를 클릭하여 업데이트합니다.
1. [속성] 패널에서 **[!UICONTROL 스마트 텍스트 크기 조정]**&#x200B;을 선택하여 지정된 영역에 맞게 텍스트 길이 및 글꼴 크기를 자동으로 조정합니다.
   ![최고의 사용자 지정 배너](/help/assets/assets/add-text-layer.png)

레이어를 위치 변경, 크기 조정, 회전 또는 삭제하려면 [**[!UICONTROL 속성 패널]**](#reposition-resize-delete-a-layer)을 참조하세요. 패널의 **[!UICONTROL 텍스트]** 섹션 아래에 있는 각 필드의 값을 변경하여 텍스트 서식을 필요한 글꼴, 크기, 색상, 스타일, 정렬(레이어)로 지정합니다. **[!UICONTROL 글꼴 모음]** 필드에는 [!UICONTROL Adobe Sans F2] 기본 글꼴, 다시 처리된 기존 글꼴 및 새로 업로드되고 게시된 글꼴이 표시됩니다. 자세한 내용은 위의 [시작하기 전에](#prerequisites-for-dynamic-media-wysiwyg-template) 섹션에서 5점을 참조하십시오.

[특정 텍스트 부분에 서식 지정](#apply-formatting-to-substring) 및 [독립적으로 제어할 수 있도록 매개 변수화](#substring-parameterisation).

#### 선택적 텍스트 서식 지정{#apply-formatting-to-substring}

다음 단계를 실행하여 문자열의 특정 부분에 서식을 지정합니다.

1. 문자열에서 형식을 지정할 문자를 하나 이상 선택합니다.
1. [속성 패널](#properties-panel)을 사용하여 선택 항목의 서식을 지정합니다. 다음 서식 옵션은 하위 문자열 및 해당 부분에 적용할 수 있습니다.
   * **글꼴 스타일**: **[!UICONTROL 글꼴 스타일]** 옵션을 사용하여 굵게, 기울임꼴, 밑줄, 아래 첨자 및 위 첨자.
   * **글꼴 속성**: 각 패널 옵션을 사용하여 글꼴 모음, 색 및 크기를 변경합니다.
     ![format-substring](/help/assets/assets/format-substring.png)

[형식이 지정된 각 문자열 부분은 매개 변수 패널에서 사용할 수 있는 하위 문자열 선택기에 하위 문자열로 표시됩니다. 서식 파일의 게재 URL](#substring-parameterisation)을(를) 사용하여 동적으로 서식을 지정하려면 형식이 지정된 이러한 부분에 매개 변수를 추가하십시오.

### 캔버스에 모양 추가 {#add-shapes-to-the-canvas}

다음 단계를 실행하여 캔버스에 모양을 추가합니다.

1. ![모양 만들기](/help/assets/assets/Shapes.svg)를 클릭하고 모양(사각형 또는 원)을 선택하여 캔버스에 추가합니다. 셰이프의 [[!UICONTROL 속성 패널]](#reposition-resize-delete-a-layer)을 사용하여 레이어의 위치를 변경하거나, 크기를 조정하거나, 회전하거나, 삭제하십시오.
1. 패널의 **[!UICONTROL 스타일]** 섹션으로 스크롤하거나 **[!UICONTROL 셰이프 색상]** 필드에 16진수 코드를 정의하거나 색상 선택기를 사용하여 선택한 셰이프에서 색상을 채웁니다.
1. **[!UICONTROL 균일 반경]** 토글을 활성화하고 **[!UICONTROL 모서리 반경]** 슬라이더를 사용하여 사각형의 네 모퉁이의 원형률을 균일하게 조정합니다. 토글을 비활성화하여 각 모서리에 특정 반지름 값을 지정하여 코너 원형률을 사용자 정의합니다.
   ![셰이프의 모퉁이 원형율 조정](/help/assets/assets/enable-uniform-radius-shape.png)
1. [선택한 레이어에 **[!UICONTROL Hide]** 매개 변수를 추가](#parameterise-a-layer)하여 템플릿 URL을 사용하여 템플릿의 레이어를 실시간으로 표시하거나 숨깁니다.
1. [CTA에 [!UICONTROL 링크]를 추가](#add-CTA-in-dynamic-media-templates)할 계층을 선택하여 사용자가 라이브 템플릿의 하이퍼링크로 모양을 클릭할 수 있도록 합니다.

### 레이어 편집 또는 삭제 {#edit-or-delete-a-layer}

캔버스 레이어를 편집하거나 삭제하려면 다음 단계를 수행하십시오.

1. ![동적 업데이트를 지원하는 템플릿](/help/assets/assets/show-layers-list.svg)을 클릭하고 캔버스 또는 레이어 목록에서 레이어를 선택합니다.
1. 레이어를 편집하거나 삭제하려면 **[!UICONTROL 추가 옵션]**(![실시간 업데이트를 지원하는 템플릿](/help/assets/assets/three-dots.svg))을 클릭하십시오.
1. 레이어를 삭제하려면 **[!UICONTROL 삭제]**&#x200B;를 클릭하십시오.
1. **[!UICONTROL 속성 패널]**&#x200B;을 사용하여 레이어를 편집하려면 [**[!UICONTROL 편집]**](#reposition-resize-delete-a-layer)을 클릭하세요.
   ![빠른 배너 만들기](/help/assets/assets/dm-templates/edit-delete-layer.png)

### 속성 패널{#properties-panel}

[!UICONTROL 속성] 패널에는 레이어의 [위치 변경](#reposition-resize-delete-a-layer), [크기 변경](#reposition-resize-delete-a-layer) 및 [회전](#reposition-resize-delete-a-layer)에 대한 섹션이 포함되어 있습니다.  또한 [모양 레이어](#add-shapes-to-the-canvas)에 대한 색 채우기 옵션, [텍스트 레이어](#text-formatting-options-on-properties-panel)에 대한 [텍스트 서식 옵션](#add-text-to-the-canvas) 및 [선택한 레이어에 [!UICONTROL CTA] 링크를 추가](#add-CTA-in-dynamic-media-templates)하는 옵션을 제공합니다.
레이어의 속성 패널로 이동하려면 ![빠른 콘텐츠 만들기](/help/assets/assets/show-layers-list.svg)를 클릭하고 목록에서 레이어를 선택하여 해당 [!UICONTROL 속성] 패널을 표시합니다.

![빠른 콘텐츠 만들기](/help/assets/assets/properties-panel.png)

레이어의 [!UICONTROL 속성] 패널에서 캔버스에서 다른 레이어를 선택하여 해당 [!UICONTROL 속성] 패널로 이동합니다.

#### 레이어 위치 변경, 크기 조정, 회전 또는 삭제{#reposition-resize-delete-a-layer}

텍스트 또는 이미지 레이어를 편집하려면 다음과 같은 일반적인 레이어 편집 작업을 참조하십시오.

* **레이어 위치 변경:** 레이어를 드래그하여 캔버스에서 원하는 위치로 이동합니다. 이 작업은 속성 패널의 X 및 Y 값을 업데이트합니다. X와 Y는 캔버스 평면에서 레이어의 중심 좌표입니다.
* **레이어 크기 조정:** 레이어를 선택하고 가장자리 핸들을 드래그하여 크기를 조정합니다. 이 작업은 속성 패널의 W(폭) 및 H(높이) 값을 업데이트합니다.
* **레이어 회전:** 레이어 위에 수직으로 배치된 사각형 핸들을 드래그하여 가운데로 회전합니다. 이 작업은 속성 패널의 각도 값을 업데이트합니다.
* **레이어를 삭제합니다.** 선택한 레이어를 삭제하려면 **백스페이스** 또는 **삭제**&#x200B;를 누른 다음 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

#### 텍스트 서식 옵션{#text-formatting-options-on-properties-panel}

패널의 **[!UICONTROL 텍스트]** 섹션 아래에 있는 각 필드의 값을 변경하여 텍스트 서식을 필요한 글꼴, 크기, 색상, 스타일, 맞춤(레이어 내)으로 지정합니다.
**[!UICONTROL 스마트 텍스트 크기 조정]**&#x200B;을 포함해야 합니다. [!UICONTROL 스마트 텍스트 크기 조정]은(는) [자동 맞춤](https://experienceleague.adobe.com/ko/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting) 알고리즘에서 작동하여 텍스트 영역의 텍스트를 최적으로 채우고 텍스트 오버플로를 방지하고 텍스트 아래쪽에 있는 추가 공간을 최소화합니다.

![시간 내에 콘텐츠 만들기](/help/assets/assets/smart-text-resize.png)

### 매개 변수 레이어 {#parameterise-a-layer}

이미지, 텍스트 및 모양의 여러 레이어로 템플릿을 만든 후 선택한 레이어를 매개 변수로 지정합니다. 레이어나 레이어의 속성을 매개 변수로 지정하면 키-값 쌍(매개 변수라고도 함)을 가져옵니다. 이 매개 변수는 템플릿 URL에 포함되어 레이어의 위치, 크기 또는 콘텐츠를 실시간으로 업데이트하여 즉시 템플릿을 사용자 지정할 수 있습니다.

레이어를 매개 변수화하려면 다음을 수행합니다.

1. ![즉시 콘텐츠 만들기](/help/assets/assets/show-layers-list.svg)를 클릭하고 레이어를 선택한 다음 **[!UICONTROL 매개 변수]**&#x200B;를 클릭합니다. **[!UICONTROL 매개 변수]** 패널이 표시됩니다.
1. 속성을 매개 변수화하려면 **[!UICONTROL 매개 변수 포함]**&#x200B;을 전환하십시오. 매개 변수화 후 속성의 동작을 알려면 [매개 변수 패널 옵션](#parameterisation-options-or-allowed-parameters)을 참조하세요.
1. **선택 사항:** 매개 변수 이름을 변경합니다. 매개 변수 이름에는 레이어 이름 뒤에 접미사가 붙습니다. 선택한 레이어의 경우 매개 변수가 있는 모든 속성은 같은 레이어 이름 다음에 다양한 접미사를 공유합니다. 시맨틱 이름 지정 규칙에 따라 레이어 이름의 이름을 바꾸십시오. 그러면 URL에 매개 변수를 포함할 때 매개 변수 이름 자체가 레이어의 콘텐츠 또는 목적에 대해 설명하도록 할 수 있습니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
   ![즉시 콘텐츠 만들기](/help/assets/assets/parameterise-a-layer.png)
이미지의 매개 변수 패널과 텍스트 레이어 사이를 전환하려면 캔버스에서 레이어를 선택하고 **[!UICONTROL 매개 변수]**&#x200B;를 클릭하십시오.

#### 매개 변수 패널 옵션 {#parameterisation-options-or-allowed-parameters}

매개 변수화된 속성은 템플릿 URL에 URL 매개 변수로 포함되어 URL을 사용하여 템플릿을 실시간으로 편집할 수 있습니다.

##### 레이어 매개 변수{#layer-parameters}

다음은 이미지 레이어와 텍스트 레이어 모두에 적용되는 레이어 매개 변수입니다.

**[!UICONTROL X]:** URL에서 매개 변수의 값을 변경하여 레이어를 중앙선을 따라 템플릿 평면의 X축에 평행하게 수평으로 이동하는 것을 포함합니다.
**[!UICONTROL Y]:** URL에서 매개 변수의 값을 변경하여 중심선을 따라 템플릿 평면의 Y축에 평행하게 레이어를 세로로 이동하려면 포함을 포함합니다.
**[!UICONTROL 너비]:** URL에서 매개 변수의 값을 변경하여 레이어의 너비를 조정하려면 포함하십시오.
**[!UICONTROL 높이]:** URL에서 매개 변수의 값을 변경하여 레이어의 높이를 조정하려면 포함하십시오.
**[!UICONTROL 숨기기]:** 0(표시)과 1(숨기기)을 사용하여 템플릿에서 레이어를 숨기거나 표시합니다.

##### 이미지 매개 변수{#image-parameter}

**[!UICONTROL Source]** 매개 변수를 포함하여 URL의 매개 변수 값에서 이미지 경로를 변경하여 레이어의 이미지를 새 이미지로 바꾸십시오.
![이미지 원본 매개 변수](/help/assets/assets/image-parameter.png)

##### 텍스트 서식 매개 변수{#text-formatting-parameters}

다음 매개 변수를 포함하여 URL의 매개 변수 값을 업데이트하여 게재 URL에서 텍스트, 글꼴, 색상 및 크기를 편집합니다.

**[!UICONTROL 텍스트]:** URL에서 텍스트를 업데이트하는 데 포함합니다.
**[!UICONTROL 글꼴 모음]:** URL에서 텍스트 글꼴을 업데이트하는 데 포함합니다.
**[!UICONTROL 글꼴 크기]:** URL에서 텍스트의 글꼴 크기를 업데이트하는 데 포함합니다.
**[!UICONTROL 텍스트 색상]:** URL에서 텍스트의 글꼴 색상을 업데이트하는 데 포함합니다.

##### 하위 문자열 매개 변수화{#substring-parameterisation}

**[!UICONTROL 매개 변수]** 패널에서 **[!UICONTROL 하위 문자열 매개 변수]** 섹션으로 스크롤합니다. 이 섹션에는 형식이 일관되게 지정된 전체 문자열(선택한 텍스트 레이어) 또는 형식이 지정된 부분을 별도의 하위 문자열로 표시하는 **하위 문자열 선택기**&#x200B;가 포함되어 있습니다. [텍스트, 글꼴 모음, 글꼴 크기 및 색을 매개 변수화할 하위 문자열을 선택하십시오](#text-formatting-parameters).
하위 문자열 선택기를 사용하여 [하위 문자열 분할](#split-substring)을 통해 개별 부분을 매개 변수화하거나 [하위 문자열 병합](#merge-substring)을 통해 균일 매개 변수를 적용합니다.

###### 하위 문자열 분할{#split-substring}

하위 문자열의 특정 부분을 매개 변수화하려면 해당 부분을 꺼내 개별 선택 및 매개 변수화를 위한 별도의 하위 문자열로 만듭니다. 다음 단계를 실행하여 하위 문자열을 별도의 하위 문자열로 분할합니다.

1. 하위 문자열 선택기에서 하위 문자열 내의 문자를 선택하여 구분합니다.
1. ![하위 문자열 분할](/help/assets/assets/unmerge.svg)을(를) 클릭하여 선택 항목을 꺼내고 **하위 문자열 선택기** 내에서 별도의 하위 문자열로 만듭니다.
   ![하위 문자열 분할](/help/assets/assets/split-a-substring.png)
필요한 하위 문자열을 선택하여 [텍스트, 글꼴 모음, 글꼴 크기 및 색상을 매개 변수화](#text-formatting-parameters)할 수 있습니다.

###### 하위 문자열 병합{#merge-substring}

하위 문자열 병합을 사용하면 기존의 개별 매개 변수가 제거되고 새로 구성된 하위 문자열에 일관된 매개 변수를 적용할 수 있습니다.
다음 단계를 실행하여 인접한 두 하위 문자열을 병합하여 결과 하위 문자열에 균일 매개 변수를 적용합니다.

1. 하위 문자열 선택기에서 서식이 같은 인접한 두 하위 문자열에 걸쳐 있는 문자를 선택합니다.
1. 하위 문자열을 병합하려면 ![하위 문자열 병합](/help/assets/assets/merge.svg)을 클릭하세요.
   ![동일한 하위 문자열 병합](/help/assets/assets/merge-two-substrings.png)
새로 형성된 하위 문자열에 균일 매개변수를 적용할 수 있습니다.
   >[!NOTE]
   >
   >서식이 동일한 하위 문자열만 병합할 수 있습니다.

### 레이어를 그룹화하여 동시에 가시성 제어{#group-layers}

템플릿을 유연하게 유지하는 또 다른 방법은 단일 매개 변수 이름을 사용하여 여러 레이어를 제어하는 것입니다. 이 전략은 단일 템플릿에서 디자인이나 그래픽을 업데이트하는 가시성(레이어 숨기기 또는 표시) 매개변수에 유용합니다.

다음 단계에 따라 여러 레이어의 [!UICONTROL 숨기기] 매개 변수(![빠른 콘텐츠 만들기](/help/assets/assets/Visibility-icon.svg))에 동일한 이름을 할당하여 동시에 숨기거나 표시할 수 있습니다.

1. 레이어의 [**[!UICONTROL 속성 패널]**](#parameterise-a-layer)(으)로 이동합니다.
1. 이전에 매개 변수를 사용하지 않으면 **[!UICONTROL Hide]** 매개 변수를 전환합니다.
1. **선택 사항:** **[!UICONTROL Hide]** 매개 변수의 이름을 변경합니다.
1. **[!UICONTROL Hide]** 매개 변수 이름을 복사합니다.
1. 캔버스에서 다른 레이어를 선택하여 해당 레이어의 [매개 변수] 패널로 이동하고 매개 변수가 지정되지 않은 경우 해당 **[!UICONTROL 숨기기]** 매개 변수를 전환합니다.
1. **[!UICONTROL 매개 변수 숨기기]** 이름을 복사한 이름으로 바꿉니다.
1. 레이어를 그룹화하려면 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.
1. 변경 내용을 보려면 [**[!UICONTROL 미리 보기 및 게시]**](#preview-and-publish-template-and-copy-template-deliver-url) 섹션에서 3단계와 4단계를 실행하십시오.

## 템플릿을 미리 보고 게시하여 게재 URL 복사{#preview-and-publish-template-and-copy-template-deliver-url}

다음 단계를 실행하여 템플릿을 미리 보고 게시하고 게재 URL을 복사합니다.

1. 캔버스 페이지에서 **[!UICONTROL 미리 보기]**&#x200B;를 클릭합니다. **[!UICONTROL Assets 보기]** **>** **[!UICONTROL Dynamic Media Assets]** **>** 템플릿 찾기 및 선택 **>** 클릭 **[!UICONTROL 템플릿 편집]** **>** 클릭 **[!UICONTROL 미리 보기]**&#x200B;로 이동할 수도 있습니다. 미리 보기 페이지에는 템플릿, 해당 매개 변수(매개 변수가 있는 레이어 및 속성), 게시 상태 및 **[!UICONTROL 게시]** 옵션이 표시됩니다.
1. **[!UICONTROL 템플릿 매개 변수]** 패널에서 매개 변수를 선택하여 해당 값을 편집하고 미리 보기에서 해당 템플릿 레이어의 콘텐츠, 크기, 위치 또는 텍스트 서식을 즉시 업데이트합니다. 예:
   1. 텍스트 레이어를 선택하고 텍스트 또는
   1. 이미지 레이어를 선택하고 ![바로 콘텐츠 만들기](/help/assets/assets/add-image.svg)를 클릭한 다음 자산 선택기에서 이미지를 선택하고 **[!UICONTROL 새로 고침]**&#x200B;을 클릭합니다.

   템플릿이 즉시 업데이트되어 편집된 텍스트가 표시되고 이전 이미지가 새 이미지로 교체됩니다. 또한 이미지 매개 변수 값은 새 이미지 경로를 반영합니다. 마찬가지로 값을 조정하여 레이어의 크기를 조정할 수 있으며 변경 내용은 템플릿에 실시간으로 적용됩니다.
1. 템플릿에서 함께 표시하거나 숨기려면 목록에서 **[!UICONTROL 그룹화된 레이어]**&#x200B;에 대한 [숨기기](#group-layers) 매개 변수를 선택하십시오.
1. **선택 사항:** **[!UICONTROL Hide]** 매개 변수 값을 0과 1 사이에서 변경하고 **[!UICONTROL 새로 고침]**&#x200B;을 클릭하여 변경 사항을 확인합니다. **[!UICONTROL 숨기기]** 매개 변수가 같은 레이어는 숨기거나 함께 표시됩니다. 마찬가지로 URL에서 레이어의 가시성을 제어할 수 있습니다.

   ![즉시 콘텐츠 만들기](/help/assets/assets/dm-templates-publish-status.png)
**[!UICONTROL 모든 매개 변수 포함]**&#x200B;을 전환하여 표시된 모든 매개 변수 값을 편집하고 템플릿 미리 보기에서 업데이트를 볼 수도 있습니다.
   <br>
1. 미리 보기 페이지에서 템플릿을 게시하려면 **[!UICONTROL 게시]**&#x200B;를 클릭하고 게시를 확인합니다. **[!UICONTROL 게시 완료]** 메시지가 표시되고 게시 상태가 **[!UICONTROL 게시됨]**(으)로 업데이트됩니다.

### 게재 URL 복사

**[!UICONTROL 미리 보기]** 페이지에서 선택한 매개 변수가 템플릿 URL의 URL 매개 변수가 됩니다.

템플릿의 이미지가 이미 AEM 및 Dynamic Media에 게시되어 템플릿의 게재 URL을 생성하는지 확인합니다.

다음 단계를 실행하여 템플릿의 게재 URL을 복사합니다.

1. **[!UICONTROL URL 복사]**&#x200B;를 클릭합니다. **[!UICONTROL URL 복사]** 대화 상자가 표시됩니다. 표시된 URL을 선택하고 복사합니다. URL의 첫 번째 매개 변수는 물음표 **([!UICONTROL ) 뒤에 시작됩니다.])** 및 키-값 쌍이 **[!UICONTROL $]**(으)로 시작되고 **[!UICONTROL &amp;]**(으)로 끝납니다. 키와 값이 등호 **([!UICONTROL =])**(으)로 구분됩니다. 왼쪽에는 키가 있고 오른쪽에는 값이 있습니다.
1. 이 URL을 브라우저 탭에 붙여넣고 라이브 템플릿을 확인합니다. [미리 보기 및 게시](#preview-and-publish-template-and-copy-template-deliver-url) 섹션의 **2단계** 및 단계에 표시된 대로 URL에서 필요한 매개 변수의 값(키 값)을 직접 업데이트하여 실시간으로 템플릿을 사용자 지정하십시오.
1. 제품 또는 서비스의 빠른 머천다이징에 이 URL을 사용하십시오. 이 URL을 고객과 공유하거나 웹 사이트 또는 다운스트림 타사 애플리케이션에 통합하여 배너를 표시하고 진행 중인 오퍼를 반영하도록 실시간 업데이트할 수 있습니다.

## URL에서 템플릿을 실시간으로 업데이트합니다.{#update-the-template-from-the-url}

URL에서 직접 매개 변수를 편집하는 것은 지루할 수 있습니다. 단순화하려면 다음을 수행하십시오.

1. URL을 복사하여 메모장에 붙여넣습니다.
1. Cmd+F(Mac) 또는 Ctrl+F(Windows)를 사용하여 매개 변수 값을 찾고 편집합니다. 예:
   * 이미지 레이어의 이미지 경로를 찾아 바꿉니다.
   * 레이어의 [매개 변수화된](#parameterise-a-layer) 좌표, 너비 및 높이를 찾아 값을 조정합니다.
   * 텍스트 레이어의 텍스트, 글꼴, 색상, 크기 또는 정렬을 편집합니다.
   * 가시성 값을 0과 1 사이에서 변경합니다.

업데이트된 이 URL을 브라우저에 붙여넣어 변경 사항을 확인합니다.

## 템플릿 편집{#edit-the-template}

다음 단계에 따라 템플릿을 편집합니다.

1. [!DNL Assets view]에서 **[!UICONTROL Dynamic Media Assets]**&#x200B;을(를) 클릭합니다.
2. 템플릿 위치로 이동합니다.
3. 템플릿을 선택합니다.
4. **[!UICONTROL 템플릿 편집]**&#x200B;을 클릭합니다. 템플릿 캔버스에는 템플릿과 해당 레이어의 모든 목록이 [레이어] 패널에 표시됩니다. 요구 사항에 따라 템플릿 편집을 시작합니다.

## 템플릿 레이어에 Call to action(CTA) 링크 추가{#add-CTA-in-dynamic-media-templates}

사용자를 대상 페이지로 안내하는 CTA 링크를 추가하여 [!DNL Dynamic Media] 템플릿의 이미지, 텍스트 또는 모양 레이어를 하이퍼링크로 전환합니다.

다음 단계를 실행하여 레이어에 CTA 링크를 추가합니다.

1. 템플릿 위치로 이동하여 템플릿을 선택하고 ![편집](/help/assets/assets/edit-pen-icon.svg) **[!UICONTROL 템플릿 편집]**&#x200B;을 클릭합니다. 템플릿이 캔버스에 표시됩니다.
1. 템플릿 레이어를 선택하고 [해당 속성 패널로 이동](#edit-or-delete-a-layer)하여 CTA 링크를 추가합니다.
1. 속성 패널에서 **[!UICONTROL CTA 추가]**&#x200B;를 선택하고 **[!UICONTROL URL]** 필드에 대상 URL을 지정한 다음 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![CTA 추가](/help/assets/assets/add-cta.png)

1. 이전에 게시하지 않은 경우 **[!UICONTROL 미리 보기]**&#x200B;를 클릭하고 **[!UICONTROL 게시]**&#x200B;를 선택하여 템플릿을 게시합니다.
1. 이 템플릿이 저장된 폴더로 이동하여 이 템플릿을 선택하고 ![세부 정보 페이지](/help/assets/assets/details-page-icon.svg) **[!UICONTROL 세부 정보]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 옵션 복사]**&#x200B;를 클릭하고 **[!UICONTROL 포함 코드 복사]**&#x200B;를 선택합니다. 포함 코드를 복사하려면 템플릿 이미지를 [!DNL AEM and Dynamic Media]에 게시해야 합니다.

   ![포함 코드 복사](/help/assets/assets/copy-options1.png)

   다음은 포함 코드의 예입니다.

   ```json
    <div class="adobe-dynamicmedia-template-embed-container">
    <img id="<Image ID>>" src="<Image Source>>" alt="adobe dynamicmedia template" usemap="#adobe-dynamicmedia-template-map" width="800" height="300">
    <map name="adobe-dynamicmedia-template-map">
    <area shape="rect" coords="417,-60,817,340" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    <area shape="rect" coords="6,206.57,129,231.43" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    </map>
    </div>
   ```

1. 복사한 포함 코드를 사이트의 HTML 파일에 추가하고 브라우저에서 실행하여 템플릿을 표시합니다.

템플릿에서 CTA 요소를 클릭하여 대상 페이지로 이동합니다.

이 단계별 비디오를 통해 템플릿 레이어에 CTA 링크를 추가하는 방법에 대해 알아보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3457616)

## 중요 참고 사항 {#important-points-to-note}

* 동적 업데이트를 위해 매개 변수가 있는 이미지 레이어가 있는 템플릿을 만든 후 향후 업데이트하려는 이미지가 매개 변수가 있는 이미지와 동일한 차원을 공유하는지 확인하십시오. 이렇게 하면 이미지가 넘치거나 빈 공간을 남기지 않고 레이어 내에 완벽하게 맞춰집니다. 현재 템플릿에서는 레이어에 이미지를 맞추기 위한 자동 치수 조정을 지원하지 않습니다.
* 텍스트 레이어에는 하위 문자열 지원이 없습니다. 텍스트 레이어의 하위 문자열에 다른 글꼴 속성을 적용할 수 없습니다.
* 현재 [!DNL Dynamic Media] 템플릿에서는 여러 [!DNL Dynamic Media] 회사에 대한 지원을 사용할 수 없습니다.
* 복사 또는 이동의 경우 대상 선택기에 [!DNL Dynamic Media]개가 아닌 동기화된 폴더가 포함된 모든 폴더가 표시됩니다. 또한 현재 [!DNL Dynamic Media] 템플릿 자산은 표시되지 않습니다(두 가지 모두 대상 선택기의 제한 사항입니다).
* Assets 섹션의 폴더에 대한 모든 업데이트 작업(예: 게시 또는 삭제)은 해당 폴더 내에서 사용할 수 있는 [!DNL Dynamic Media] 템플릿에 영향을 줍니다.
* [!DNL Dynamic Media] 템플릿에 대해 휴지통이 작동하지 않습니다. 자산을 휴지통으로 이동한 다음 복원하면 자산이 AEM에서 복원되지만 [!DNL Dynamic Media]에서는 복원되지 않습니다. [!DNL Dynamic Media] 템플릿에 대해서도 동일하게 사용할 수 있습니다.

## 추가 참조

1. [[!DNL Dynamic Media] 및 해당 기능 탐색](/help/assets/dynamic-media/dynamic-media.md)
1. OpenAPI 기능을 사용하여 [[!DNL Dynamic Media] 탐색](/help/assets/dynamic-media-open-apis-overview.md)