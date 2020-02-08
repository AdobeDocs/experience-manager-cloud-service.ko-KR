---
title: 이미지 사전 설정 관리
description: 이미지 사전 설정을 이해하고 이미지 사전 설정을 생성, 수정 및 관리하는 방법을 알아봅니다.
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Managing Image Presets{#managing-image-presets}

이미지 사전 설정을 사용하면 AEM 자산에서 서로 다른 크기, 서로 다른 형식 또는 동적으로 생성된 다른 이미지 속성을 사용하여 이미지를 동적으로 제공할 수 있습니다. 각 이미지 사전 설정은 이미지 표시를 위한 크기 및 형식 지정 명령의 사전 정의된 컬렉션을 나타냅니다. 이미지 사전 설정을 만들 때 이미지 배달을 위한 크기를 선택합니다. 또한 이미지를 볼 수 있도록 전달할 때 이미지 모양이 최적화되도록 서식 명령을 선택합니다.

관리자는 에셋 내보내기를 위한 사전 설정을 만들 수 있습니다. 사용자는 이미지를 내보낼 때 사전 설정을 선택할 수 있으며, 이 사전 설정은 관리자가 지정한 사양에 맞게 이미지를 다시 포맷합니다.

반응형 이미지 사전 설정을 만들 수도 있습니다. 응답형 이미지 사전 설정을 자산에 적용하는 경우 해당 사전 설정은 보는 장치나 화면 크기에 따라 달라집니다. RGB 또는 회색 외에 색상 공간에서 CMYK를 사용하도록 이미지 사전 설정을 구성할 수 있습니다.

이 섹션에서는 이미지 사전 설정을 생성, 수정 및 일반적으로 관리하는 방법에 대해 설명합니다. 미리 볼 때마다 이미지에 이미지 사전 설정을 적용할 수 있습니다. See [Applying Image Presets](/help/assets/dynamic-media/image-presets.md).

>[!NOTE]
>
>스마트 이미징은 기존 이미지 사전 설정과 연동되며 전달 마지막 순간에 지능적인 기능을 사용하여 브라우저 또는 네트워크 연결 속도에 따라 이미지 파일 크기를 더욱 줄일 수 있습니다. 자세한 [내용은 스마트](/help/assets/dynamic-media/imaging-faq.md) 이미징을 참조하십시오.

## 이미지 사전 설정 이해 {#understanding-image-presets}

매크로와 마찬가지로 이미지 사전 설정은 이름 아래에 저장된 크기 및 서식 지정 명령의 사전 정의된 모음입니다. 이미지 사전 설정의 작동 방식을 이해하려면 웹 사이트에서 각 제품 이미지가 서로 다른 크기, 서로 다른 형식 및 데스크탑 및 모바일 전달의 압축 비율로 나타나야 한다고 가정합니다.

두 개의 이미지 사전 설정을 만들 수 있습니다.하나는 데스크탑 버전의 경우 500 x 500 픽셀이고 다른 하나는 모바일 버전의 경우 150 x 150 픽셀입니다. 두 개의 이미지 사전 설정을 만듭니다. 하나는 500x500 픽셀로 이미지를 `Enlarge` 표시하기 위해 호출되고 다른 하나는 150 x 150 픽셀로 이미지를 `Thumbnail` 표시하기 위해 호출됩니다. 이미지를 `Enlarge` 크기와 `Thumbnail` 크기로 제공하기 위해 AEM은 이미지 사전 설정 확대 및 축소판 이미지 사전 설정의 정의를 조회합니다. 그런 다음 AEM에서 각 이미지 사전 설정의 크기와 형식 사양에 따라 이미지를 동적으로 생성합니다.

이미지를 동적으로 전달할 때 크기가 축소되면 선명도와 세부 묘사가 손실될 수 있습니다. 이러한 이유로 각 이미지 사전 설정에는 특정 크기로 제공될 때 이미지를 최적화하기 위한 서식 컨트롤이 포함되어 있습니다. 이러한 컨트롤을 사용하면 웹 사이트 또는 애플리케이션에 이미지를 전달할 때 선명하고 명확하게 이미지를 전달할 수 있습니다.

관리자는 이미지 사전 설정을 만들 수 있습니다. 이미지 사전 설정을 새로 만들거나 기존 사전 설정에서 시작하여 새 이름으로 저장할 수 있습니다.

## Managing Image Presets {#managing-image-presets-1}

AEM 로고를 탭하거나 클릭하여 글로벌 탐색 콘솔에 액세스한 다음 도구 아이콘을 탭하거나 클릭하고 자산 > 이미지 사전 설정으로 이동하여 AEM에서 이미지 사전 **[!UICONTROL 설정을 관리합니다]**.

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>만드는 모든 이미지 사전 설정은 자산을 미리 보거나 전달할 때 동적 표현물로 사용할 수도 있습니다.
>
>이미지 사전 설정이 자동으로 게시되므로 이미지 사전 설정을 게시할 *필요가 없습니다* .
>
>See [Publishing Image Presets.](#publishing-image-presets)

>[!NOTE]
>
>자산의 세부 정보 보기에서 표현물을 선택하면 **[!UICONTROL 다양한]** 표현물이 표시됩니다. 표시되는 이미지 사전 설정의 수를 늘리거나 줄일 수 있습니다. 표시되는 [이미지 사전 설정](#increasing-or-decreasing-the-number-of-image-presets-that-display)수 증가를 참조하십시오.

### Adobe Illustrator(AI), Postscript(EPS) 및 PDF 파일 포맷 {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

AI, EPS 및 PDF 파일의 통합을 지원하여 이러한 파일 포맷의 동적 변환을 생성하려는 경우 이미지 사전 설정을 만들기 전에 다음 정보를 검토할 수 있습니다.

Adobe Illustrator의 파일 포맷은 PDF의 변형입니다. AEM 자산 컨텍스트에서 주요 차이점은 다음과 같습니다.

* Adobe Illustrator 문서는 여러 레이어가 있는 단일 페이지로 구성됩니다. 각 레이어는 기본 Illustrator 에셋 아래에 있는 PNG 하위 자산으로 추출됩니다.
* PDF 문서는 하나 이상의 페이지로 구성됩니다. 각 페이지는 여러 페이지로 구성된 기본 PDF 문서 아래에 단일 페이지 PDF 하위 자산으로 추출됩니다.

하위 자산은 전체 `Create Sub Asset process` `DAM Update Asset` 워크플로우 내의 구성 요소에 의해 만들어집니다. 워크플로우 내에서 이 프로세스 구성 요소를 보려면 도구 > 워크플로우 > **[!UICONTROL 모델 > DAM 자산 업데이트 > 편집을 누릅니다]**.

<!-- See also [Viewing pages of a multi-page file](/help/assets/manage-linked-subassets.md#view-pages-of-a-multi-page-file). -->

자산을 열 때 하위 자산이나 페이지를 보고 콘텐츠 메뉴를 누른 다음 하위 자산이나 페이지를 **[!UICONTROL 선택할]** 수 **[!UICONTROL 있습니다]**. 하위 자산은 실제 자산입니다. 즉, PDF 페이지는 `Create Sub Asset` 워크플로우 구성 요소로 추출됩니다. 그런 다음 기본 `page1.pdf`자산 `page2.pdf`아래에 있는 등의 형식으로 저장됩니다. 저장된 후에는 `DAM Update Asset` 워크플로우가 처리합니다.

Dynamic Media를 사용하여 AI, EPS 또는 PDF 파일에 대한 동적 변환을 미리 보고 생성하려면 다음 처리 단계가 필요합니다.

1. 워크플로우에서 `DAM Update Asset` 프로세스 구성 요소는 구성된 해상도를 사용하여 원본 자산의 첫 페이지를 `Rasterize PDF/AI Image Preview Rendition` `cqdam.preview.png` 변환으로 래스터화합니다.

1. 그런 다음 `cqdam.preview.png` 변환은 워크플로우 내의 `Dynamic Media Process Image Assets` 프로세스 구성 요소에 의해 PTIFF로 최적화됩니다.

>[!NOTE]
>
>DAM 자산 업데이트 워크플로우에서 EPS **[!UICONTROL 축소판]** 단계는 EPS 파일의 축소판을 생성합니다.

#### PDF/AI/EPS 에셋 메타데이터 속성 {#pdf-ai-eps-asset-metadata-properties}

| **메타데이터 속성** | **설명** |
|---|---|
| dam:Physicalwidthin인치 | 문서 너비(인치) |
| dam:Physicalheizinch | 문서 높이(인치) |

워크플로우의 방법으로 `Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소 옵션에 액세스합니다 `DAM Update Asset` .

왼쪽 상단에 있는 Adobe Experience Manager를 누르고 도구 > 워크플로우 **[!UICONTROL > 모델로 이동합니다]**. 워크플로우 모델 페이지에서 DAM 자산 **[!UICONTROL 업데이트를]**&#x200B;선택한 다음 도구 모음에서 편집을 **[!UICONTROL 누릅니다]**. DAM 자산 업데이트 워크플로우 페이지에서 프로세스 구성 요소를 두 번 눌러 단계 속성 대화 상자를 엽니다. `Rasterize PDF/AI Image Preview Rendition`

#### Rasterize PDF/AI Image Preview Rendition options {#rasterize-pdf-ai-image-preview-rendition-options}

![PDF 또는 AI 래스터화를 위한 인수 워크플로우](assets/rasterize_pdf_ai_image_preview.png)

PDF 또는 AI 래스터화를 위한 인수 워크플로우

<table>
 <tbody>
  <tr>
   <td><strong>프로세스 인수</strong></td>
   <td><strong>기본 설정</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>MIME 유형</td>
   <td><p>application/pdf</p> <p>application/postscript</p> <p>응용 프로그램/illustrator<br /> </p> </td>
   <td>PDF 또는 Illustrator 문서로 간주되는 문서 MIME 유형 목록입니다.<br /> </td>
  </tr>
  <tr>
   <td>최대 너비</td>
   <td>2048</td>
   <td>생성된 미리 보기 변환의 최대 너비(픽셀 단위)입니다.<br /> </td>
  </tr>
  <tr>
   <td>최대 높이</td>
   <td>2048</td>
   <td>생성된 미리 보기 변환의 최대 높이(픽셀 단위).<br /> </td>
  </tr>
  <tr>
   <td>해상도</td>
   <td>72</td>
   <td>첫 번째 페이지를 래스터화하는 해상도(ppi(인치당 픽셀).</td>
  </tr>
 </tbody>
</table>

기본 프로세스 인수를 사용하여 PDF/AI 문서의 첫 번째 페이지는 72ppi로 래스터화되며 생성된 미리 보기 이미지의 크기는 2048 x 2048픽셀입니다. 일반적인 배포의 경우 해상도를 최소 150ppi 이상으로 늘릴 수 있습니다. 예를 들어 미국 문자 크기 문서가 300ppi인 경우 각각 최대 너비 및 높이는 2550 x 3300픽셀이어야 합니다.

최대 폭 및 최대 높이는 래스터화할 해상도를 제한합니다. 예를 들어 최대값이 변경되지 않고 해상도가 300ppi로 설정된 경우 미국 문자 문서는 186ppi로 래스터화됩니다. 즉, 문서는 1581 x 2046픽셀입니다.

프로세스 구성 요소에는 메모리에서 지나치게 큰 이미지를 만들지 않도록 정의된 최대값이 `Rasterize PDF/AI Image Preview Rendition` 있습니다. 이러한 큰 이미지는 JVM(Java Virtual Machine)에 제공된 메모리를 오버플로우할 수 있습니다. JVM에 구성된 병렬 워크플로우의 수를 관리할 수 있는 충분한 메모리를 제공하려면 각 JVM이 구성된 최대 크기로 이미지를 생성할 가능성이 있습니다.

### InDesign(INDD) 파일 포맷 {#indesign-indd-file-format}

이 파일 포맷의 동적 변환을 생성할 수 있도록 INDD 파일 섭취를 지원하려는 경우 이미지 사전 설정을 만들기 전에 다음 정보를 검토할 수 있습니다.

InDesign 파일의 경우 Adobe InDesign 서버가 AEM과 통합된 경우에만 하위 자산이 추출됩니다. 참조된 자산은 메타데이터를 기반으로 연결됩니다. InDesign Server는 연결에 필요하지 않습니다. 그러나 참조된 에셋이 InDesign 파일과 참조된 에셋 사이에 생성될 링크를 처리하기 전에 AEM 내에 있어야 합니다.

<!-- See [Integrating AEM Assets with InDesign Server](/help/assets/indesign.md). -->

워크플로우의 미디어 추출 프로세스 구성 요소는 InDesign 파일을 처리하기 위해 미리 구성된 여러 개의 스크립트 확장을 실행합니다. `DAM Update Asset`

![미디어 추출 프로세스의 인수에서 ExtendScript 경로](/help/assets/dynamic-media/assets/6_5_mediaextractionprocess.png)

DAM 자산 업데이트 워크플로우에서 미디어 추출 프로세스 구성 요소의 인수에서 ExtendScript 경로

다음 스크립트는 Dynamic Media 통합에서 사용됩니다.

<table>
 <tbody>
  <tr>
   <td><strong>스크립트 이름 확장</strong></td>
   <td><strong>기본값</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>ThumbnailExport.jsx</td>
   <td>예</td>
   <td>최적화된 300ppi <code>thumbnail.jpg</code> 변환을 <code>Dynamic Media Process Image Assets</code> 프로세스 구성 요소별로 PTIFF 변환으로 생성합니다.<br /> </td>
  </tr>
  <tr>
   <td>JPEGPagesExport.jsx</td>
   <td>예</td>
   <td>각 페이지에 대해 300ppi JPEG 하위 자산을 생성합니다. JPEG 하위 자산은 InDesign 에셋 아래에 저장된 실제 자산입니다. 또한 <code>DAM Update Asset</code> 워크플로우에서 최적화된 PTIFF로 전환됩니다.<br /> </td>
  </tr>
  <tr>
   <td>PDFPagesExport.jsx</td>
   <td>아니오</td>
   <td>각 페이지에 대한 PDF 하위 자산을 생성합니다. PDF 하위 자산은 앞서 설명한 대로 처리됩니다. PDF에는 단일 페이지만 포함되어 있으므로 하위 에셋이 생성되지 않습니다.<br /> </td>
  </tr>
 </tbody>
</table>

### 이미지 축소판 크기 구성 {#configuring-image-thumbnail-size}

DAM 자산 업데이트 워크플로에서 이러한 설정을 구성하여 축소판의 크기를 구성할 **[!UICONTROL 수]** 있습니다. 워크플로우에서는 이미지 자산의 축소판 크기를 구성할 수 있는 두 가지 단계가 있습니다. 정적 축소판&#x200B;**[!UICONTROL 생성을 위한 동적 이미지 자산(Dynamic Media Process Image Assets]**)과&#x200B;**[!UICONTROL 정적 축소판 생성을]**&#x200B;위한 다른 프로세스( *프로세스 축소판* )가 사용되거나 모든 다른 프로세스가 축소판을 생성하지 못할 경우둘모두에 동일한 설정이 있어야 합니다.

Dynamic **[!UICONTROL Media Process Image Assets]** 단계에서는 이미지 서버에서 축소판을 생성하며 이 구성은 [프로세스 축소판] **[!UICONTROL 단계에 적용된 구성과 독립적입니다]** . 축소판 처리 **[!UICONTROL 단계를 통해]** 축소판을 생성하는 것은 축소판을 만드는 가장 느리고 메모리를 많이 사용하는 방법입니다.

축소판 크기 조정은 다음 형식으로 정의됩니다. **[!UICONTROL width:height:center]**(예: *80:80:false*) 너비와 높이는 축소판의 크기(픽셀 단위)를 결정합니다.center 값은 false 또는 true이며 true로 설정된 경우 축소판 이미지의 크기가 구성에 지정된 크기와 정확히 일치함을 나타냅니다. 크기가 조정된 이미지가 더 작은 경우 축소판 내에서 가운데에 표시됩니다.

>[!NOTE]
>
>* EPS 파일의 축소판 크기는 축소판의 인수 **[!UICONTROL 탭에서 EPS 축소판]** 단계에서 **** 구성됩니다.
   >
   >
* 비디오의 축소판 크기는 [인수] 아래의 [ **[!UICONTROL 프로세스]** ] **[!UICONTROL 탭에서]** FFmpeg 축소판 **[!UICONTROL 단계에서]**&#x200B;구성됩니다.
>



**이미지 축소판 크기를 구성하려면**

1. 도구 **[!UICONTROL > 워크플로우 > 모델 > DAM 자산 업데이트 > 편집을 누릅니다]**.
1. Dynamic Media **[!UICONTROL Process Image Assets]** 단계를 누르고 축소판 **[!UICONTROL 탭을]** 누릅니다. 필요한 경우 축소판 크기를 변경한 다음 확인을 **[!UICONTROL 누릅니다]**.

   ![6_5_dynamicmediaprocesseassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. [축소판 **[!UICONTROL 처리]** ] 단계를 누른 다음 [축소판] **[!UICONTROL 탭을]** 누릅니다. 필요한 경우 축소판 크기를 변경한 다음 확인을 **[!UICONTROL 누릅니다]**.

   >[!NOTE]
   >
   >[프로세스 축소판] 단계의 축소판 인수 **[!UICONTROL 값은]** [Dynamic Media 프로세스 이미지 자산 **]** 단계의 축소판 인수와 일치해야합니다.

1. 저장을 **[!UICONTROL 눌러]** 워크플로우에 대한 변경 사항을 저장합니다.

### 표시되는 이미지 사전 설정 수 증가 또는 감소 {#increasing-or-decreasing-the-number-of-image-presets-that-display}

만든 이미지 사전 설정은 자산을 미리 볼 때 동적 표현물로 사용할 수 있습니다. AEM은 세부 사항 보기 > 표현물에서 자산을 볼 때 다양한 동적 **[!UICONTROL 표현물을 보여줍니다]**. 표시되는 표현물의 제한을 늘리거나 줄일 수 있습니다.

**표시된 이미지 사전 설정 수를 늘리거나 줄이려면**

1. CRXDE Lite(https://localhost:4502/crx/de)로[이동합니다](https://localhost:4502/crx/de).
1. Navigate to the image preset listing node at `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![increasethenumberofimagepresets표시](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. limit **[!UICONTROL 속성에서]** 기본적으로 15로 ****&#x200B;설정된 값을 원하는 수로 변경합니다.
1. Navigate to the image preset datasource at `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. limit 속성에서 숫자를 원하는 숫자로 변경합니다(예: `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. 모두 **[!UICONTROL 저장을 누릅니다]**.

### 이미지 사전 설정 만들기 {#creating-image-presets}

이미지 사전 설정을 만들면 미리 보거나 게시할 때 이미지에 이러한 설정을 적용할 수 있습니다.

>[!NOTE]
>
>Internet Explorer 9를 사용하는 경우 사전 설정을 만들면 저장 직후 사전 설정 목록에 나타나지 않습니다. 이 문제를 해결하려면 IE9에 대한 캐시를 비활성화하십시오.

AI, PDF 및 EPS 파일의 통합을 지원하여 이러한 파일 포맷의 동적 변환을 생성하려는 경우 이미지 사전 설정을 만들기 전에 다음 정보를 검토할 수 있습니다.
Adobe [Illustrator(AI), Postscript(EPS) 및 PDF 파일 형식을](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)참조하십시오.

이 파일 포맷의 동적 변환을 생성할 수 있도록 INDD 파일 섭취를 지원하려는 경우 이미지 사전 설정을 만들기 전에 다음 정보를 검토할 수 있습니다.
INDD( [InDesign) 파일 형식을](#indesign-indd-file-format)참조하십시오.

**이미지 사전 설정을 만들려면**

1. AEM에서 AEM 로고를 눌러 글로벌 탐색 콘솔에 액세스한 다음 도구 > 자산 **[!UICONTROL > 이미지 사전 설정을 누릅니다]**.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. 이미지 **[!UICONTROL 사전 설정 편집]** 창이 열립니다.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >이 이미지 사전 설정을 반응형으로 만들려면 **[!UICONTROL 폭]** 및 **[!UICONTROL 높이]** 필드의 값을 지우고 비워 두십시오.

1. 이름을 포함하여 **[!UICONTROL 기본]** 및 고급 **[!UICONTROL 탭에 값을 적절히]** 입력합니다. 옵션은 이미지 사전 설정 [옵션에 요약되어 있습니다](#image-preset-options). 사전 설정은 왼쪽 창에 표시되며 다른 에셋과 함께 즉시 사용할 수 있습니다.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. [!UICONTROL 저장]을 **클릭합니다**.

### 반응형 이미지 사전 설정 만들기 {#creating-a-responsive-image-preset}

반응형 이미지 사전 설정을 만들려면 이미지 사전 설정 [만들기에서 단계를 수행합니다](#creating-image-presets). [이미지 사전 설정 편집] 창에서 높이와 **[!UICONTROL 너비를]** 입력할 때 값을 지운 후 비워 둡니다.

이 사전 설정을 비워 두면 AEM에서 이 이미지 사전 설정이 응답성이 있음을 알 수 있습니다. 다른 값을 적절히 조정할 수 있습니다.

>[!NOTE]
>
>자산에 이미지 **[!UICONTROL 사전 설정을 적용할]** 때 URL 및 **[!UICONTROL RESS]** 단추를 보려면 자산을 게시해야 합니다.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>이미지 사전 설정과 이미지 자산은 자동으로 게시됩니다.

### 이미지 사전 설정 옵션 {#image-preset-options}

이미지 사전 설정을 만들거나 편집할 때 이 섹션에 설명된 옵션이 있습니다. 또한 Adobe에서는 다음과 같은 &quot;우수 사례&quot; 옵션을 선택하여 시작할 것을 권장합니다.

* **[!UICONTROL 형식** (**[!UICONTROL 기본]** 탭) - 요구 사항을 **[!UICONTROL 충족하는 JPEG]** 또는 다른 형식을 선택합니다. 모든 웹 브라우저는 JPEG 이미지 형식을 지원합니다.작은 파일 크기와 이미지 품질 간의 적절한 균형을 제공합니다. 그러나 JPEG 형식 이미지는 압축 설정이 너무 낮으면 원치 않는 이미지 결함을 발생시킬 수 있는 손실 압축 스키마를 사용합니다. 이러한 이유로 Adobe에서는 압축 품질을 75로 설정하는 것이 좋습니다. 이 설정은 이미지 품질과 작은 파일 크기 간의 적절한 균형을 제공합니다.

* **[!UICONTROL 단순 선명]** 활성화 - [ **[!UICONTROL 단순 선명하게 하기 사용]을 선택하지 마십시오]** . 이 선명 효과 필터는 [언샵 마스킹] 설정보다 더 적은 컨트롤을 제공합니다.

* **[!UICONTROL 선명하게 하기:리샘플링 모드]** - **[!UICONTROL Bi-Cubic을 선택합니다]**.

#### 기본 탭 옵션 {#basic-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>필드</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong>이름</strong></td>
   <td>공백 없이 수사적 이름을 입력합니다. 사용자가 이미지 사전 설정을 식별하는 데 도움이 되도록 이름에 이미지 크기 사양을 포함해야 합니다.</td>
  </tr>
  <tr>
   <td><strong>폭과 높이</strong></td>
   <td>이미지가 배달되는 크기를 픽셀 단위로 입력합니다. 너비와 높이는 0픽셀보다 커야 합니다. 값이 0이면 사전 설정이 만들어지지 않습니다. 두 값이 모두 비어 있으면 응답형 이미지 사전 설정이 만들어집니다.</td>
  </tr>
  <tr>
   <td><strong>형식</strong></td>
   <td><p>메뉴에서 형식을 선택합니다.</p> <p>JPEG <strong>를</strong> 선택하면 다음과 같은 추가 옵션이 제공됩니다.</p>
    <ul>
     <li><strong>품질</strong> - JPEG 압축 레벨을 제어합니다. 이 설정은 파일 크기와 이미지 품질 모두에 영향을 줍니다. JPEG 품질 척도는 1-100입니다. 슬라이더를 드래그하면 비율이 표시됩니다.</li>
     <li><strong>JPG Chrominance Downsampling</strong> 활성화 - JPEG 이미지는 고주파수 광도보다 고주파수 색상 정보에 덜 민감하므로 이미지 정보를 광도 및 색상 구성 요소로 나눕니다. JPEG 이미지가 압축되면 광도 구성 요소는 전체 해상도로 유지되며 색상 구성 요소는 픽셀 그룹을 평균화하여 다운샘플링됩니다. 다운샘플링은 인지된 품질에 거의 영향을 주지 않으면서 데이터 볼륨을 1/2 또는 1/3만큼 감소시킵니다. 다운샘플링은 회색 음영 이미지에는 적용되지 않습니다. 이 기술은 대비가 높은 이미지(예: 텍스트가 넘치는 이미지)에 유용합니다.</li>
    </ul>
    <div>
      GIF <strong>또는 GIF</strong> 를 <strong>alpha</strong> 와 함께 선택하면 다음과 같은 추가 <strong>GIF 색상 양자화</strong> 옵션이 제공됩니다.
    </div>
    <ul>
     <li><strong>유형 </strong>- <strong>응용</strong> (기본값) <strong>, 웹</strong>또는 <strong>Macintosh</strong>를선택합니다. If you select <strong>GIF with Alpha</strong>, the Macintosh option is not available.</li>
     <li><strong>디더</strong> - 확산 <strong>또는</strong> 끄기를 <strong>선택합니다</strong>.</li>
     <li><strong>색상 수 </strong>- 2와 256 사이의 숫자를 입력합니다.</li>
     <li><strong>색상 목록</strong> - 쉼표로 구분된 목록을 입력합니다. 예를 들어, 흰색, 회색 및 검정의 경우 00000,88888,ffff를 입력합니다.</li>
    </ul>
    <div>
      PDF <strong></strong>, <strong>TIFF</strong>또는 <strong>알파가</strong> 있는 TIFF를 선택하면 다음 추가 옵션을 사용할 수 있습니다.
    </div>
    <ul>
     <li><strong>압축</strong> - 압축 알고리즘을 선택합니다. PDF에 대한 알고리즘 옵션은 <strong>없음</strong>, <strong>Zip</strong>및 <strong>Jpeg</strong>입니다.tiff의 경우 <strong>없음</strong>, <strong>LZW</strong>, <strong>Jpeg</strong>및 <strong>Zip</strong>이alpha가 있는 TIFF의 경우 <strong>없음</strong>, <strong>LZW</strong>및 <strong>Zip</strong>이있습니다.</li>
    </ul> <p>PNG <strong></strong>, <strong>알파가 있는 PNG</strong> 또는 <strong>EPS를 선택하면</strong> 추가 옵션이제공되지 않습니다.</p> </td>
  </tr>
  <tr>
   <td><strong>선명하게 하기</strong></td>
   <td>Select the <strong>Enable Simple Sharpening</strong> option to apply a basic sharpening filter to the image after all scaling takes place. Sharpening can help compensate for blurriness that can result when you display an image at a different size. </td>
  </tr>
 </tbody>
</table>

#### 고급 탭 옵션 {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>필드</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong>색상 공간</strong></td>
   <td>색상 <strong>공간에 대해 RGB, CMYK</strong> 또는 <strong>회색</strong> 을 선택합니다.</td>
  </tr>
  <tr>
   <td><strong>색상 프로필</strong></td>
   <td>작업 프로필과 다른 경우 에셋을 변환할 출력 색상 공간 프로필을 선택합니다.</td>
  </tr>
  <tr>
   <td><strong>렌더링 의도</strong></td>
   <td>기본 렌더링 의도를 무시할 수 있습니다. 렌더링 의도는 대상 색상 프로파일에서 재현할 수 없는 색상(색상 영역 외)의 상황을 결정합니다. 렌더링 의도가 ICC 프로파일과 호환되지 않으면 무시됩니다.
    <ul>
     <li>원본 <strong>이미지의 하나</strong> 이상의 색상이 대상 색상 공간의 색상 영역을 벗어날 때 전체 색상 영역을 한 색상 공간의 다른 색상 공간으로 압축하려면 [가시 범위]를 선택합니다.</li>
     <li>현재 <strong>색상 공간의 색상이</strong> 대상 색상 공간의 색상 영역을 벗어나는 경우 다른 색상에 영향을 주지 않고 대상 색상 공간의 색상 영역 내에서 가장 가까운 색상으로 매핑하려는 경우 [상대 색상 지표]를 선택합니다. </li>
     <li>대상 <strong>색상</strong> 공간으로 변환할 때 원본 이미지 색상 채도를 재현하려면 채도를 선택합니다. </li>
     <li>이미지의 <strong>밝기를</strong> 변경하는 흰색 점 또는 검은 점을 조정하지 않고 색상을 정확하게 일치시키려면 [절대 색상 지표]를 선택합니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>검은 점 보상</strong></td>
   <td>출력 프로파일이 이 기능을 지원하는 경우 이 옵션을 선택합니다. Blackpoint 보상은 지정된 ICC 프로파일과 호환되지 않으면 무시됩니다.</td>
  </tr>
  <tr>
   <td><strong>디더링</strong></td>
   <td>색상 밴딩 결함을 방지하거나 줄이려면 이 옵션을 선택합니다. </td>
  </tr>
  <tr>
   <td><strong>선명하게 하기 유형</strong></td>
   <td><p>[ <strong>없음</strong>], <strong>[선명</strong>] 또는 [언샵 마스크] <strong>를</strong>선택합니다. </p>
    <ul>
     <li>[없음] <strong>을</strong> 선택하여 선명하게 하기를 비활성화합니다.</li>
     <li>모든 <strong>크기 조정이 </strong>수행된 후 이미지에 기본 선명하게 하기 필터를 적용하려면 선명 효과를 선택합니다. 선명하게 하기는 이미지를 다른 크기로 표시할 때 발생할 수 있는 흐림 효과를 보상하는 데 도움이 됩니다. </li>
     <li>Unsharp<strong> mask</strong> 를 선택하여 최종 다운샘플링된 이미지에서 선명하게 하기 필터 효과를 세밀하게 조정합니다. 효과의 강도, 효과의 반경(픽셀 단위 측정) 및 무시할 대비 임계값을 제어할 수 있습니다. 이 효과는 Photoshop의 "언샵 마스크" 필터와 동일한 옵션을 사용합니다.</li>
    </ul> <p>언샵 <strong>마스크에는</strong>다음 옵션이 있습니다.</p>
    <ul>
     <li><strong>양</strong> - 가장자리 픽셀에 적용되는 대비의 양을 제어합니다. 기본 실수 값은 1.0입니다.고해상도 이미지의 경우 최대 5.0까지 늘릴 수 있습니다.양을 필터 강도를 측정하여 생각해 보십시오.</li>
     <li><strong>반경</strong> - 선명하게 하기에 영향을 주는 가장자리 픽셀 주위의 픽셀 수를 결정합니다. 고해상도 이미지의 경우 1부터 2까지의 실수를 입력합니다. 낮은 값은 가장자리 픽셀만 선명하게 합니다.높은 값은 더 넓은 범위의 픽셀을 선명하게 합니다. 올바른 값은 이미지의 크기에 따라 달라집니다.</li>
     <li><strong>임계값</strong> - 언샵 마스크 필터를 적용할 때 무시할 대비 범위를 결정합니다. 즉, 이 옵션은 선명하게 된 픽셀이 가장자리 픽셀로 간주되어 선명하게 되기 전에 주변 영역과 얼마나 달라야 하는지 결정합니다. 노이즈를 발생하지 않도록 하려면 2~20 사이의 정수 값을 실험해 봅니다. </li>
     <li><strong>적용 대상</strong> - 선명하지 않은 영역이 각 색상에 적용되는지 또는 밝기에 적용되는지 결정합니다.</li>
    </ul>
    <div>
      선명하게 하기는 선명하게 하기 <a href="https://docs.adobe.com/content/help/en/dynamic-media-classic/using/assets/s7_sharpening_images.pdf">이미지에 설명되어 있습니다</a>.
    </div> </td>
  </tr>
  <tr>
   <td><strong>리샘플링 모드</strong></td>
   <td>리샘플링 <strong>모드</strong> 옵션을 선택합니다. 이러한 옵션은 이미지를 다운샘플링할 때 이미지를 선명하게 합니다.
    <ul>
     <li><strong>Bi-Linear</strong> - 가장 빠른 리샘플링 방법입니다.일부 앨리어스 가공물은 눈에 띄게 표시됩니다.</li>
     <li><strong>Bi-Cubic</strong> - CPU 사용량을 증가시키지만 앨리어스 가공물이 덜 나타나면서 이미지를 더 선명하게 만듭니다.</li>
     <li><strong>Sharp2</strong> - Bi-Cubic보다 약간 더 선명하게 결과를 생성할 수 있지만 CPU 비용은 훨씬 더 높습니다.</li>
     <li><strong>Bi-Sharp</strong> - Adobe Photoshop에서 이미지 크기를 줄이기 위한 Photoshop 기본 리샘플러를 <strong>쌍입방(더 선명하게</strong> )이라고 합니다.</li>
     <li><strong>각 색상</strong> 및 <strong>밝기</strong> - 각 방법은 색상 또는 밝기를 기반으로 할 수 있습니다. 기본적으로 <strong>[각 색상</strong> ]이 선택됩니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>인쇄 해상도</strong></td>
   <td>이 이미지 인쇄를 위한 해상도를 선택하십시오.기본값은 72픽셀입니다.</td>
  </tr>
  <tr>
   <td><strong>이미지 수정자</strong></td>
   <td><p>UI에서 사용할 수 있는 일반적인 이미지 설정 외에도 Dynamic Media는 이미지 수정자 <strong>필드에 지정할 수 있는 다양한 고급 이미지 수정을 지원합니다</strong> . 이러한 매개 변수는 이미지 서버 프로토콜 <a href="https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/c_command_reference.html">명령 참조에</a>정의되어 있습니다.</p> <p>중요:API에 나열된 다음 기능은 지원되지 않습니다.</p>
    <ul>
     <li>기본 템플릿 및 텍스트 렌더링 명령: <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> 및 <code>textPs=</code></li>
     <li>현지화 명령: <code>locale=</code> 및 <code>req=xlate</code></li>
     <li><code>req=set</code> 은 일반 용도로 사용할 수 없습니다.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>비코어 Dynamic Media 서비스:SVG, 이미지 렌더링 및 Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### 이미지 수정자를 사용하여 이미지 사전 설정 옵션 정의 {#defining-image-preset-options-with-image-modifiers}

기본 및 고급 탭에서 사용할 수 있는 옵션 외에도 이미지 사전 설정을 정의할 때 더 많은 옵션을 제공하는 이미지 수정자를 정의할 수 있습니다. 이미지 렌더링은 Scene7 이미지 렌더링 API를 사용하며 HTTP 프로토콜 [참조에서 자세히 정의됩니다](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/c_http_protocol_reference.html).

다음은 이미지 수정자로 수행할 수 있는 작업에 대한 몇 가지 기본적인 예입니다.

>[!NOTE]
>
>일부 이미지 수정자는 AEM에서 사용할 [수 없습니다](#advanced-tab-options).

* [op_invert](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_invert.html) - 음수 이미지 효과를 위해 각 색상 구성 요소를 반전합니다.

   ```xml
   &op_invert=1
   ```

   ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_blur](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_blur.html) - 흐림 필터를 이미지에 적용합니다.

   ```xml
   &op_blur=7
   ```

   ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* 결합된 명령 - op_blur 및 op-invert

   ```xml
   &op_invert=1&op_blur=7
   ```

   ![chlimage_1-80](assets/chlimage_1-501.png)

* [op_brightness](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_brightness.html) - 밝기를 줄이거나 늘립니다.

   ```xml
   &op_brightness=58
   ```

   ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_opac.html) - 이미지 불투명도를 조정합니다. 전경 불투명도를 줄일 수 있습니다.

   ```xml
   opac=29
   ```

   ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

### 이미지 사전 설정 편집 {#modifying-image-presets}

1. AEM에서 AEM 로고를 눌러 글로벌 탐색 콘솔에 액세스한 다음 도구 > 자산 **[!UICONTROL > 이미지 사전 설정을 누릅니다]**.

   ![6_5_imagepreset-editpreset](assets/6_5_imagepreset-editpreset.png)

1. 사전 설정을 선택한 다음 편집을 **[!UICONTROL 클릭합니다]**. 이미지 **[!UICONTROL 사전 설정 편집]** 창이 열립니다.
1. 변경한 후 **[!UICONTROL 저장을]** 클릭하여 변경 내용을 저장하거나 취소를 **[!UICONTROL 클릭하여]** 변경 사항을 취소합니다.

### 게시 이미지 사전 설정 {#publishing-image-presets}

이미지 사전 설정은 자동으로 게시됩니다.

### 이미지 사전 설정 삭제 {#deleting-image-presets}

1. AEM에서 AEM 로고를 눌러 글로벌 탐색 콘솔에 액세스하고 도구 아이콘을 탭하거나 클릭하고 자산 > 이미지 사전 **[!UICONTROL 설정으로 이동합니다]**.
1. 사전 설정을 선택한 다음 **[!UICONTROL 삭제]를 클릭합니다**. Dynamic Media에서 삭제를 확인합니다. 삭제를 **[!UICONTROL 눌러]** 삭제하거나 취소를 **[!UICONTROL 눌러]** 중단합니다.
