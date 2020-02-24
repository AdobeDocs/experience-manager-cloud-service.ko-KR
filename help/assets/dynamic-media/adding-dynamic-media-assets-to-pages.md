---
title: 페이지에 Dynamic Media 자산 추가
description: AEM의 페이지에 Dynamic Media 구성 요소를 추가하는 방법
translation-type: tm+mt
source-git-commit: 454f4c9585b575ae0d904292ddd659148393db0b

---


# 페이지에 Dynamic Media 자산 추가{#adding-dynamic-media-assets-to-pages}

To add the Dynamic Media functionality to assets you use on your websites, you can add the **Dynamic Media**, **Interactive Media**, **Panoramic Media**, or **Video 360 Media** component directly on the page. 이렇게 하려면 레이아웃 모드로 전환하고 다이내믹 미디어 구성 요소를 활성화합니다. 그런 다음이 구성 요소를 페이지에 추가하고 자산을 구성 요소에 추가할 수 있습니다. Dynamic Media 구성 요소는 스마트하며, 사용자는 이미지 또는 비디오를 추가하는지 여부와 그에 따라 사용 가능한 구성 옵션이 변경됩니다.

AEM 파섹 WCM에 대해 서드 파티를 사용하는 경우 자산을 [링크하거나](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)[포함합니다](/help/assets/dynamic-media/embed-code.md) . 반응형 타사 웹 사이트의 경우 반응형 사이트에 [최적화된 이미지](/help/assets/dynamic-media/responsive-site.md)제공을 참조하십시오.

>[!NOTE]
>
>자산을 AEM의 페이지에 추가하기 전에 게시해야 합니다. See [Publishing Dynamic Media Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Adding a Dynamic Media component to a page {#adding-a-dynamic-media-component-to-a-page}

다이내믹 미디어, 인터랙티브 미디어, 파노라마 미디어 또는 비디오 360 미디어 구성 요소를 페이지에 추가하는 것은 구성 요소를 페이지에 추가하는 것과 같습니다. Dynamic Media 구성 요소는 다음 섹션에 설명되어 있습니다.

**페이지에 Dynamic Media 구성 요소 추가**

1. AEM에서 Dynamic Media 구성 요소를 추가할 페이지를 엽니다.
1. 왼쪽 창에서 구성 요소 **[!UICONTROL 아이콘을 누른]** 다음 다이내믹 미디어용으로 필터링합니다.

   사용할 수 있는 Dynamic Media 구성 요소가 없는 경우 Dynamic Media 구성 요소를 활성화하거나 켜야 합니다. 자세한 [내용은 템플릿 편집 - 템플릿](/help/sites-cloud/authoring/features/templates.md) 작성자를 참조하십시오.

   ![6_5_360video_wcmcomponent](assets/6_5_360video_wcmcomponent.png)

1. Dynamic **[!UICONTROL Media]** 구성 요소를 페이지에서 원하는 위치에 드래그합니다.

   아래 예에서 비디오 360 **[!UICONTROL 미디어]** 구성 요소가 사용되고 있습니다.

   ![6_5_360video_wcmcomponents드래그](assets/6_5_360video_wcmcomponentdrag.png)

1. 마우스 포인터를 구성 요소 바로 위에 놓습니다. 구성 요소 주위에 파란색 상자가 표시되면 한 번 눌러 구성 요소의 도구 모음을 표시합니다. 구성( **[!UICONTROL 스패너)]** 아이콘을 누릅니다.

   ![6_5_360video_wcmcomponents구성](assets/6_5_360video_wcmcomponentconfigure.png)

1. 페이지에 드롭한 Dynamic Media 구성 요소에 따라 구성 대화 상자가 열립니다. [필요에 따라 구성 요소의 옵션을](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) 설정합니다.

   아래 예제는 Dynamic Media **[!UICONTROL Video 360]** 미디어 구성 요소 대화 상자와 뷰어 사전 설정 드롭다운 목록에서 사용할 수 있는 옵션을 보여줍니다.

   ![비디오 360 미디어 구성 요소](assets/6_5_360video_wcmcomponentviewerpreset.png)

   Dynamic Media Video 360 미디어 구성 요소입니다.

1. 완료되면 대화 상자의 오른쪽 위 모서리 근처에 있는 확인 표시를 눌러 변경 내용을 저장합니다.

## Dynamic Media 구성 요소 현지화 {#localizing-dynamic-media-components}

다음 두 가지 방법 중 하나로 Dynamic Media 구성 요소를 현지화할 수 있습니다.

* 사이트의 웹 페이지에서 속성을 열고 **[!UICONTROL 고급]** **[!UICONTROL 탭을]** 선택합니다. 현지화를 위해 원하는 언어를 선택합니다.

   ![chlimage_1-172](assets/chlimage_1-538.png)

* 사이트 선택기에서 원하는 페이지 또는 페이지 그룹을 선택합니다. 속성을 **[!UICONTROL 누르고]** 고급 **[!UICONTROL 탭을]** 선택합니다. 현지화를 위해 원하는 언어를 선택합니다.

   >[!NOTE]
   >
   >언어 메뉴에서 사용할 수 있는 일부 언어에는 현재 **[!UICONTROL 토큰이]** 할당되어 있지 않습니다.

## 사용 가능한 다이내믹 미디어 구성 요소 {#dynamic-media-components}

Dynamic Media 구성 요소는 구성 요소 아이콘을 누른 **[!UICONTROL 다음]** Dynamic Media에서 필터링할 때 **[!UICONTROL 사용할 수 있습니다]**.

사용할 수 있는 Dynamic Media 구성 요소에는 다음이 포함됩니다.

* **[!UICONTROL 다이내믹 미디어]** - 이미지, 비디오, e카탈로그 및 스핀 세트와 같은 에셋에 사용합니다.
* **[!UICONTROL 인터랙티브한 미디어]** - 인터랙티브한 비디오, 인터랙티브한 이미지 또는 회전 메뉴 세트와 같은 인터랙티브한 에셋에 사용할 수 있습니다.
* **[!UICONTROL 파노라마 미디어]** - 파노라마 이미지 또는 파노라마 VR 이미지 에셋에 사용합니다.
* **[!UICONTROL 비디오 360 미디어]** - 360 비디오 및 360 VR 파섹 비디오 에셋에 사용합니다.

>[!NOTE]
>
>이러한 구성 요소는 기본적으로 사용할 수 없으며 사용하기 전에 템플릿 편집기를 통해 사용할 수 있어야 합니다. 템플릿 편집기에서 사용할 수 있게 되면 다른 AEM 구성 요소처럼 페이지에 구성 요소를 추가할 수 있습니다.

![6_5_dynamicmediawcmcomponents](assets/6_5_dynamicmediawcmcomponents.png)

### 구성 요소:다이내믹 미디어 {#dynamic-media-component}

Dynamic Media 구성 요소는 스마트합니다.이미지 추가 또는 비디오 추가 여부에 따라 다양한 옵션이 제공됩니다. 이 구성 요소는 이미지 사전 설정, 이미지 세트와 같은 이미지 기반 뷰어, 스핀 세트, 혼합 미디어 집합 및 비디오를 지원합니다. 또한 뷰어는 반응형으로 작동하므로 화면 크기가 화면 크기에 따라 자동으로 변경됩니다. 모든 뷰어는 HTML5 뷰어입니다.

>[!NOTE]
>
>웹 페이지에 다음이 있는 경우:
>
>* 동일한 페이지에서 사용되는 Dynamic Media 구성 요소의 여러 인스턴스.
>* 각 인스턴스는 동일한 자산 유형을 사용합니다.
>
>
해당 페이지의 각 Dynamic Media 구성 요소에 다른 뷰어 사전 설정을 할당할 수는 없습니다.
>
>그러나 페이지 내에서 동일한 유형의 자산을 사용하는 모든 Dynamic Media 구성 요소에 대해 동일한 뷰어 사전 설정을 사용할 수 있습니다.

Dynamic Media 구성 요소를 추가하고 **[!UICONTROL Dynamic Media 설정]**&#x200B;이 비어 있거나 자산을 제대로 추가할 수 없는 경우, 다음을 확인하십시오.

* 이미지에 피라미드형 tiff 파일이 있습니다. 다이내믹 미디어를 활성화하기 전에 가져온 이미지에는 피라미드형 tiff 파일이 없습니다.

#### 이미지 작업 시 {#when-working-with-images}

Dynamic Media 구성 요소를 사용하면 이미지 세트, 스핀 세트 및 혼합 미디어 집합을 포함한 다이내믹 이미지를 추가할 수 있습니다. 확대하거나 축소할 수 있고, 해당하는 경우 스핀 세트 내의 이미지를 회전하거나 다른 유형의 세트에서 이미지를 선택할 수 있습니다.

구성 요소에서 바로 뷰어 사전 설정, 이미지 사전 설정 또는 이미지 형식을 구성할 수도 있습니다. 이미지가 응답하도록 하기 위해 중단점을 설정하거나 응답형 이미지 사전 설정을 적용할 수 있습니다.

You can edit the following Dynamic Media Settings by tapping the **[!UICONTROL Edit]** icon in the component and then **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>기본적으로 Dynamic Media 이미지 구성 요소는 적응형입니다. 고정 크기로 설정하려면 **[!UICONTROL 고급]** 탭의 구성 요소에서 **[!UICONTROL 폭]** 및 **[!UICONTROL 높이]**&#x200B;를 설정하십시오.

* **[!UICONTROL 뷰어 사전 설정]**- 드롭다운 메뉴에서 기존 뷰어 사전 설정을 선택합니다. 보려는 뷰어 사전 설정이 표시되지 않을 경우 표시되도록 설정해야 할 수 있습니다. 뷰어 사전 설정 관리를 참조하십시오. 이미지 사전 설정을 사용 중일 때는 뷰어 사전 설정을 선택할 수 없고 그 반대의 경우도 마찬가지입니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우 사용할 수 있는 유일한 선택 사항입니다. 표시되는 뷰어 사전 설정은 편리하게도 적절한 뷰어 사전 설정만 표시됩니다.

* **[!UICONTROL 뷰어 수정자]**- 뷰어 수정자는 이름=값 쌍의 형식을 &amp; 구분 기호로 사용하고 뷰어 참조 안내서에 설명된 대로 뷰어를 변경할 수 있도록 합니다. 뷰어 수정자의 예는 비디오 축소판의 다른 이미지를 `posterimage=img.jpg&caption=text.vtt,1` 설정하고 자막/자막 파일을 비디오와 연결하는 것입니다.

* **[!UICONTROL 이미지 사전 설정]**- 드롭다운 메뉴에서 기존 이미지 사전 설정을 선택합니다. 보려는 이미지 사전 설정이 표시되지 않을 경우 표시되도록 설정해야 할 수 있습니다. 이미지 사전 설정 관리를 참조하십시오. 이미지 사전 설정을 사용 중일 때는 뷰어 사전 설정을 선택할 수 없고 그 반대의 경우도 마찬가지입니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL 이미지 수정자]**- 추가 이미지 명령을 제공하여 이미지 효과를 적용할 수 있습니다. 이미지 사전 설정 및 이미지 제공 명령 참조에 설명되어 있습니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL 중단점]**—응답형 사이트에서 이 자산을 사용하는 경우 이미지 중단점을 추가해야 합니다. 이미지 중단점은 쉼표(,)로 구분해야 합니다. 이 선택 사항은 이미지 사전 설정에 정의된 높이나 폭이 없는 경우에 작동합니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

   You can edit the following Advanced Settings by tapping **[!UICONTROL Edit]** in the component.

* **[!UICONTROL 제목]**- 이미지의 제목을 변경합니다.

* **[!UICONTROL 대체 텍스트]**- 그래픽을 해제한 사용자의 이미지에 제목을 추가합니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL URL, 열기]**- 링크를 열도록 자산을 설정할 수 있습니다. URL을 설정하고 여는 위치에 같은 창에서 열지 또는 새 창에서 열지를 지정합니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL 너비]**- 이미지를 고정 크기로 설정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.

* **[!UICONTROL 높이]**- 이미지의 크기를 고정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.


#### 비디오 작업 시 {#when-working-with-video}

다이내믹 미디어 구성 요소를 사용하여 웹 페이지에 동적 비디오를 추가합니다. 구성 요소를 편집할 때 페이지에서 비디오를 재생하기 위해 사전 설정된 비디오 뷰어 사전 설정을 사용하도록 선택할 수 있습니다.

![chlimage_1-173](assets/chlimage_1-540.png)

You can edit the following Dynamic Media Settings by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>기본적으로 Dynamic Media 비디오 구성 요소는 적응형입니다. If you want to make it a fixed size, set it in the component with the **[!UICONTROL Width]** and **[!UICONTROL Height]** in the **[!UICONTROL Advanced]** tab.

* **[!UICONCONTROL 뷰어 사전 설정**- 드롭다운 메뉴에서 기존 비디오 뷰어 사전 설정을 선택합니다. 보려는 뷰어 사전 설정이 표시되지 않을 경우 표시되도록 설정해야 할 수 있습니다. 뷰어 사전 설정 관리를 참조하십시오.

* **[!UICONTROL 뷰어 수정자**- 뷰어 수정자는 이름=값 쌍의 형식을 &amp; 구분 기호와 함께 사용하며 Adobe 뷰어 참조 안내서에 설명된 대로 뷰어를 변경할 수 있습니다. 뷰어 수정자의 예는 다음과 같습니다. `posterimage=img.jpg&caption=text.vtt,1`

   예를 들어 뷰어 수정자를 사용하면 다음을 수행할 수 있습니다.

   * 캡션 파일을 비디오와 연결: [캡션](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * 탐색 파일을 비디오와 연결: [탐색](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)
   You can edit the following Advanced Settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL 제목**- 비디오 제목을 변경합니다.

* **[!UICONTROL 너비]**- 이미지를 고정 크기로 설정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.

* **[!UICONTROL 높이]**- 이미지의 크기를 고정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.

#### 스마트 자르기 작업 {#when-working-with-smart-crop}

Dynamic Media 구성 요소를 사용하여 웹 페이지에 스마트 자르기 이미지 자산을 추가합니다. 구성 요소를 편집할 때 페이지에서 비디오를 재생하기 위해 사전 설정된 비디오 뷰어 사전 설정을 사용하도록 선택할 수 있습니다.

AEM [자산과 함께 스마트 자르기 사용 다이내믹 미디어 참조](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/smart-crop-feature-video-use.html)

이미지 [프로필을 참조하십시오](/help/assets/dynamic-media/image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

You can edit the following Dynamic Media Setting by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>기본적으로 Dynamic Media 이미지 구성 요소는 적응형입니다. 고정 크기로 설정하려면 **[!UICONTROL 고급]** 탭의 구성 요소에서 **[!UICONTROL 폭]** 및 **[!UICONTROL 높이]**&#x200B;를 설정하십시오.

* **[!UICONTROL 이미지 수정자]**- 추가 이미지 명령을 제공하여 이미지 효과를 적용할 수 있습니다. 이미지 사전 설정 및 이미지 제공 명령 참조에 설명되어 있습니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

   You can edit the following Advanced Settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL 종횡비 일치]**&#x200B;활성화 - 스마트 자르기 변환을 선택할 때 원본 이미지의 종횡비와 일치합니다.

* **[!UICONTROL 제목]**- 스마트 자르기 이미지의 제목을 변경합니다.

* **[!UICONTROL 대체 텍스트]**- 그래픽을 해제한 사용자를 위해 스마트 자르기 이미지에 제목을 추가합니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL URL, 열기]**- 링크를 열도록 자산을 설정할 수 있습니다. URL을 설정하고 여는 위치에 같은 창에서 열지 또는 새 창에서 열지를 지정합니다.

   이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 보는 경우에는 이 선택 사항을 사용할 수 없습니다.

* **[!UICONTROL 너비]**- 이미지를 고정 크기로 설정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.

* **[!UICONTROL 높이]**- 이미지의 크기를 고정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.

### 구성 요소:인터랙티브 미디어 {#interactive-media-component}

대화형 미디어 구성 요소는 핫스팟이나 이미지 맵과 같은 상호 작용이 있는 자산을 위한 것입니다. 대화형 이미지, 대화형 비디오 또는 회전 배너가 있는 경우 **[!UICONTROL 대화형 미디어]** 구성 요소를 사용하십시오.

Interactive Media 구성 요소는 스마트합니다.이미지 추가 또는 비디오 추가 여부에 따라 다양한 옵션이 제공됩니다. 또한 뷰어는 반응형으로 작동하므로 화면 크기가 화면 크기에 따라 자동으로 변경됩니다. 모든 뷰어는 HTML5 뷰어입니다.

>[!NOTE]
>
>웹 페이지에 다음이 있는 경우:
>
>* 동일한 페이지에서 사용되는 대화형 미디어 구성 요소의 여러 인스턴스.
>* 각 인스턴스는 동일한 자산 유형을 사용합니다.
>
>
해당 페이지의 각 Interactive Media 구성 요소에 다른 뷰어 사전 설정을 할당하는 것은 지원되지 않습니다.
>
>그러나 페이지 내에서 동일한 유형의 에셋을 사용하는 모든 Interactive Media 구성 요소에 대해 동일한 뷰어 사전 설정을 사용할 수 있습니다.

![chlimage_1-174](assets/chlimage_1-541.png)

You can edit the following **[!UICONTROL General]** settings by tapping **[!UICONTROL Edit]** in the component.

* **[!UICONTROL 뷰어 사전 설정]**- 드롭다운 메뉴에서 기존 뷰어 사전 설정을 선택합니다. 보려는 뷰어 사전 설정이 표시되지 않을 경우 표시되도록 설정해야 할 수 있습니다. 뷰어 사전 설정을 사용하려면 먼저 게시해야 합니다. 뷰어 사전 설정 관리를 참조하십시오.

* **[!UICONTROL 제목]**- 비디오 제목을 변경합니다.

* **[!UICONTROL 너비]**- 이미지를 고정 크기로 설정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.

* **[!UICONTROL 높이]**- 이미지의 크기를 고정하려면 값을 픽셀 단위로 입력합니다. 이 값을 공백으로 두면 자산이 적응형으로 설정됩니다.

   구성 요소에서 **[!UICONTROL 편집]**&#x200B;을 클릭하여 다음 **[!UICONTROL 장바구니에 추가]** 설정을 편집할 수 있습니다.

* **[!UICONTROL 제품 자산]**&#x200B;표시 - 기본적으로 이 값이 선택됩니다. 제품 자산은 상거래 모듈에 정의된 제품의 이미지를 보여줍니다. 제품 자산을 표시하지 않도록 하려면 확인 표시를 지우십시오.

* **[!UICONTROL 제품 가격]**&#x200B;표시 - 기본적으로 이 값이 선택됩니다. 제품 가격은 상거래 모듈에 정의된 항목 가격을 보여줍니다. 제품 가격을 표시하지 않도록 하려면 확인 표시를 지우십시오.

* **[!UICONTROL 제품 양식]**&#x200B;표시 - 기본적으로 이 값은 선택되어 있지 않습니다. 제품 양식에는 크기 및 색상과 같은 모든 제품 변형이 포함됩니다. 제품 변형을 표시하지 않도록 하려면 확인 표시를 지우십시오.

### 구성 요소:파노라마 미디어 {#panoramic-media-component}

파노라마 미디어 구성 요소는 구형 파노라마 이미지인 자산을 위한 것입니다. 이러한 이미지는 회의실, 속성, 위치 또는 가로에서 360° 보기 환경을 제공합니다. 이미지가 구형 파노라마를 적용하려면 다음 중 하나 또는 둘 다를 가져야 합니다.

* 2:1 종횡비.
* 키워드 `equirectangular` 또는 (`spherical` + `panorama`) 또는 (`spherical` + `panoramic`) 태그가 지정되어 있습니다. 태그 [사용을 참조하십시오](/help/sites-cloud/authoring/features/tags.md).

종횡비와 키워드 기준은 모두 자산 세부 사항 페이지 및 파노라마 미디어 WCM 구성 요소에 대한 파노라마 **[!UICONTROL 자산에]** 적용됩니다.

>[!NOTE]
>
>웹 페이지에 다음이 있는 경우:
>
>* 동일한 페이지에서 사용되는 **[!UICONTROL 파노라마 미디어]** 구성 요소의 여러 인스턴스.
>* 각 인스턴스는 동일한 자산 유형을 사용합니다.
>
>
해당 페이지의 각 파노라마 미디어 **[!UICONTROL 구성 요소에 다른 뷰어]** 사전 설정을 할당하는 것은 지원되지 않습니다.
>
>그러나 페이지 내에서 동일한 유형의 에셋을 사용하는 모든 파노라마 미디어 구성 요소에 대해 동일한 뷰어 사전 설정을 사용할 수 있습니다.

![panoric-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

구성 요소에서 구성을 탭하여 다음 설정을 편집할 **[!UICONTROL 수]** 있습니다.

* **[!UICONTROL 뷰어 사전]**&#x200B;설정 - 뷰어 사전 설정 드롭다운 메뉴에서 기존 뷰어를 선택합니다.

찾고 있는 뷰어 사전 설정이 표시되지 않는 경우 게시되었는지 확인하십시오. 뷰어 사전 설정을 사용하려면 먼저 게시해야 합니다. [뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md)를 참조하십시오. 

### 구성 요소:비디오 360 미디어 {#video-media-component}

비디오 360 **[!UICONTROL 미디어]** 구성 요소를 사용하여 웹 페이지에 등장방형 비디오를 렌더링하여 회의실, 속성, 위치, 가로 또는 의료 절차의 매력적인 시청 경험을 제공할 수 있습니다.

평면 디스플레이에서 재생하는 동안 사용자는 보기 각도를 제어할 수 있습니다.모바일 디바이스에서 재생하면 일반적으로 내장된 자이로스코프 컨트롤을 활용할 수 있습니다.

뷰어에는 360개의 비디오 에셋 전달에 대한 기본 지원이 포함되어 있습니다. 기본적으로 보거나 재생하는 데 추가 구성이 필요하지 않습니다. .mp4, .mkv 및 .mov와 같은 표준 비디오 익스텐션을 사용하여 360개의 비디오를 제공할 수 있습니다. 가장 일반적인 코덱은 H.264입니다.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

구성 요소에서 구성을 탭하여 다음 설정을 편집할 **[!UICONTROL 수]** 있습니다.

* **[!UICONTROL 뷰어 사전]**&#x200B;설정 - 뷰어 사전 설정 드롭다운 메뉴에서 기존 뷰어를 선택합니다. 가상 현실 안경을 사용하는 최종 사용자를 위해 Video360VR을 사용합니다. 기본 비디오 재생 컨트롤과 소셜 미디어 기능이 포함되어 있습니다. 기본 비디오 재생 컨트롤을 포함하는 Video360_social을 사용합니다. 비디오 렌더링은 스테레오 모드로 수행됩니다. 수동 관점 제어는 꺼져 있지만, 점경적 제어는 켜졌습니다. 소셜 미디어 기능이 없습니다.

찾고 있는 뷰어 사전 설정이 표시되지 않는 경우 게시되었는지 확인하십시오. 뷰어 사전 설정을 사용하려면 먼저 게시해야 합니다. [뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md)를 참조하십시오. 

### HTTP/2를 사용하여 Dynamic Media 에셋 전달 {#using-http-to-delivery-dynamic-media-assets}

HTTP/2는 브라우저와 서버의 통신 방식을 향상시키는 업데이트된 새로운 웹 프로토콜입니다. 보다 신속하게 정보를 전송할 수 있고 필요한 처리 능력을 줄일 수 있습니다. 이제 Dynamic Media 에셋 배달을 HTTP/2를 통해 보다 나은 응답 및 로드 시간을 제공할 수 있습니다.

Dynamic [Media 계정으로](/help/assets/dynamic-media/http2faq.md) HTTP/2 사용을 시작하는 방법에 대한 자세한 내용은 HTTP2 컨텐츠 제공을 참조하십시오.

>[!MORELIKETHIS]
>
>* [AEM Dynamic Media에서 비디오 플레이어 사용](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-player-feature-video-use.html)
>* [AEM Dynamic Media에서 대화형 비디오 사용](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html)
>* [AEM Dynamic Media를 사용한 자산 뷰어 이해](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-viewer-feature-video-understand.html)
>* [AEM Dynamic Media에서 사용자 지정 비디오 축소판 사용](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-thumbnails-feature-video-use.html)
>* [AEM Dynamic Media를 사용한 색상 관리 이해](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-color-management-technical-video-setup.html)
>* [AEM Dynamic Media에서 이미지 선명하게 하기 사용](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html)

