---
title: 이미지 사전 설정 관리
description: 이미지 사전 설정 및 이미지 사전 설정을 생성, 수정 및 관리하는 방법에 대해 알아봅니다.
contentOwner: Rick Brough
feature: Image Presets,Viewers,Renditions
role: User
exl-id: a53f40ab-0e27-45f8-9142-781c077a04cc
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '3587'
ht-degree: 9%

---

# 이미지 사전 설정 관리{#managing-image-presets}

이미지 사전 설정을 사용하면 Adobe Experience Manager Assets에서 다른 크기, 다른 형식 또는 동적으로 생성되는 다른 이미지 속성으로 이미지를 동적으로 전달할 수 있습니다. 각 이미지 사전 설정은 이미지를 표시하기 위한 미리 정의된 크기 조정 및 서식 지정 명령 컬렉션을 나타냅니다. 이미지 사전 설정을 만들 때 이미지 게재 크기를 선택합니다. 또한 보기 위해 이미지가 전달될 때 이미지의 모양이 최적화되도록 서식 지정 명령을 선택합니다.

관리자는 에셋 내보내기를 위한 사전 설정을 만들 수 있습니다. 사용자는 이미지를 내보낼 때 사전 설정을 선택할 수 있으며, 이 사전 설정은 관리자가 지정하는 사양으로 이미지 형식을 다시 지정할 수도 있습니다.

응답하는 이미지 사전 설정을 만들 수도 있습니다. 반응형 이미지 사전 설정을 에셋에 적용하면 에셋이 표시된 장치 또는 화면 크기에 따라 변경됩니다. RGB 또는 회색 외에 색상 공간에서 CMYK를 사용하도록 이미지 사전 설정을 구성할 수 있습니다.

이 섹션에서는 이미지 사전 설정을 만들고, 수정하고, 일반적으로 관리하는 방법을 설명합니다. 미리 볼 때마다 이미지 사전 설정을 이미지에 적용할 수 있습니다. [이미지 사전 설정 적용](/help/assets/dynamic-media/image-presets.md)을 참조하십시오.

>[!NOTE]
>
>스마트 이미징은 기존 이미지 사전 설정에서 작동하며 마지막 전달 순간에 인텔리전스를 사용하여 브라우저 또는 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다. 자세한 내용은 [스마트 이미징](/help/assets/dynamic-media/imaging-faq.md)을 참조하세요.

## 이미지 사전 설정에 대해 알아보기 {#understanding-image-presets}

매크로와 마찬가지로 이미지 사전 설정은 이름 아래에 저장된 크기 조정 및 서식 지정 명령의 미리 정의된 컬렉션입니다. 이미지 사전 설정의 작동 방식을 이해하려면 웹 사이트에서 각 제품 이미지를 데스크탑 및 모바일 게재에 대해 서로 다른 크기, 다른 형식 및 압축률로 표시해야 한다고 가정해 봅시다.

두 개의 이미지 사전 설정을 만들 수 있습니다. 하나는 데스크탑 버전의 경우 500 x 500픽셀이고 다른 하나는 모바일 버전의 경우 150 x 150픽셀입니다. 두 개의 이미지 사전 설정을 만듭니다. 하나는 500x500픽셀로 이미지를 표시하는 `Enlarge`이고 다른 하나는 150x150픽셀로 이미지를 표시하는 `Thumbnail`입니다. `Enlarge` 및 `Thumbnail` 크기의 이미지를 전달하기 위해 Experience Manager은 확대 이미지 사전 설정 및 썸네일 이미지 사전 설정의 정의를 찾습니다. 그런 다음 Experience Manager은 각 이미지 사전 설정의 크기 및 서식 지정 사양에 따라 이미지를 동적으로 생성합니다.

이미지가 동적으로 전달될 때 크기가 줄어든 이미지는 선명도와 디테일을 잃을 수 있습니다. 이러한 이유로 각 이미지 사전 설정에는 이미지가 특정 크기로 제공될 때 이를 최적화하기 위한 서식 지정 컨트롤이 포함되어 있습니다. 이러한 컨트롤은 이미지가 웹 사이트나 응용 프로그램에 전달될 때 선명하고 선명하게 나타나도록 합니다.

관리자는 이미지 사전 설정을 만들 수 있습니다. 이미지 사전 설정을 만들려면 처음부터 시작하거나 기존 이미지 사전 설정에서 시작하여 새 이름으로 저장할 수 있습니다.

## 이미지 사전 설정 관리 {#managing-image-presets-1}

Experience Manager 로고를 선택하여 전역 탐색 콘솔에 액세스한 다음 도구 아이콘을 선택하고 **[!UICONTROL Assets]** > **[!UICONTROL 이미지 사전 설정]**(으)로 이동하여 Experience Manager에서 이미지 사전 설정을 관리합니다.

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>만든 모든 이미지 사전 설정은 에셋을 미리 보거나 전달할 때 동적 변환으로도 사용할 수 있습니다.
>
>이미지 사전 설정이 자동으로 게시되므로 *not*&#x200B;은(는) 이미지 사전 설정을 게시해야 합니다.
>
>[Publish 이미지 사전 설정](#publishing-image-presets)을 참조하세요.

>[!NOTE]
>
>자산의 세부 정보 보기에서 **[!UICONTROL 렌디션]**&#x200B;을 선택하면 시스템에 다양한 렌디션이 표시됩니다. 표시되는 이미지 사전 설정의 수를 늘리거나 줄일 수 있습니다. [표시되는 이미지 사전 설정 수 늘리기](#increasing-or-decreasing-the-number-of-image-presets-that-display)를 참조하십시오.

### Adobe Illustrator(AI), PostScript®(EPS) 및 PDF 파일 형식 {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

이러한 파일 형식의 동적 변환을 생성할 수 있도록 AI, EPS 및 PDF 파일의 수집을 지원하려면 이미지 사전 설정을 만들기 전에 다음 정보를 검토하십시오.

Adobe Illustrator의 파일 형식은 PDF의 변형입니다. Experience Manager Assets의 컨텍스트에서 주요 차이점은 다음과 같습니다.

* Adobe Illustrator 문서는 여러 레이어가 있는 단일 페이지로 구성됩니다. 각 레이어는 기본 Illustrator 에셋 아래에 PNG 하위 에셋으로 추출됩니다.
* PDF 문서는 하나 이상의 페이지로 구성됩니다. 각 페이지는 기본 다중 페이지 PDF 문서 아래에 있는 단일 페이지 PDF 하위 자산으로 추출됩니다.

전체 `DAM Update Asset` 워크플로 내에서 `Create Sub Asset process` 구성 요소에 의해 하위 자산이 만들어집니다. 워크플로우 내에서 이 프로세스 구성 요소를 보려면 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]** > **[!UICONTROL DAM 자산 업데이트]** > **[!UICONTROL 편집]**&#x200B;으로 이동하십시오.

<!-- See also [Viewing pages of a multi-page file](/help/assets/manage-linked-subassets.md#view-pages-of-a-multi-page-file). -->

에셋을 열고 콘텐츠 메뉴를 선택한 다음 **[!UICONTROL 하위 에셋]** 또는 **[!UICONTROL 페이지]**&#x200B;를 선택하면 하위 에셋 또는 페이지를 볼 수 있습니다. 하위 자산은 실제 자산입니다. 즉, PDF 페이지는 `Create Sub Asset` 워크플로 구성 요소에 의해 추출됩니다. 그런 다음 기본 에셋 아래에 `page1.pdf`, `page2.pdf` 등으로 저장됩니다. 저장되면 `DAM Update Asset` 워크플로에서 처리합니다.

Dynamic Media을 사용하여 AI, EPS 또는 PDF 파일에 대한 동적 변환을 미리 보고 생성하려면 다음 처리 단계가 필요합니다.

1. `DAM Update Asset` 워크플로에서 `Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소는 구성된 해상도를 사용하여 원본 에셋의 첫 번째 페이지를 `cqdam.preview.png` 렌디션으로 래스터화합니다.

1. 그런 다음 워크플로 내의 `Dynamic Media Process Image Assets` 프로세스 구성 요소에 의해 `cqdam.preview.png` 렌디션이 PTIFF로 최적화됩니다.

>[!NOTE]
>
>In the DAM Update Asset workflow, the **[!UICONTROL EPS thumbnails]** step generates thumbnails for EPS files.

#### PDF/AI/EPS 에셋 메타데이터 속성 {#pdf-ai-eps-asset-metadata-properties}

| **메타데이터 속성** | **설명** |
|---|---|
| dam:Physicalwidthininches | 문서 너비(인치). |
| dam:물리적 높이 | 문서 높이(인치). |

`DAM Update Asset` 워크플로를 통해 `Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소 옵션에 액세스합니다.

왼쪽 상단의 Adobe Experience Manager을 선택하고 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로]** > **[!UICONTROL 모델]**&#x200B;로 이동합니다. 워크플로 모델 페이지에서 **[!UICONTROL DAM 자산 업데이트]**&#x200B;를 선택한 다음 도구 모음에서 **[!UICONTROL 편집]**&#x200B;을 선택합니다. DAM 자산 업데이트 워크플로우 페이지에서 `Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소를 두 번 선택하여 해당 단계 속성 대화 상자를 엽니다.

#### PDF/AI 이미지 미리 보기 렌디션 옵션 래스터화 {#rasterize-pdf-ai-image-preview-rendition-options}

![PDF 또는 AI 워크플로를 래스터화하는 인수](assets/rasterize_pdf_ai_image_preview.png)

PDF 또는 AI 워크플로 래스터화 인수

| 프로세스 인수 | 기본 설정 | 설명 |
|---|---|---|
| MIME 유형 | application/pdf<br>application/postscript<br>application/illustrator | PDF 또는 Illustrator 문서로 간주되는 문서 MIME 유형 목록입니다. |
| 최대 폭 | 2048 | 생성된 미리 보기 렌디션의 최대 너비(픽셀 단위)입니다. |
| 최대 높이 | 2048 | 생성된 미리 보기 렌디션의 최대 높이(픽셀 단위)입니다. |
| 해결 방법 | 72 | 첫 번째 페이지를 래스터화하는 해상도(ppi)(인치당 픽셀 수)입니다. |

기본 프로세스 인수를 사용하면 PDF/AI 문서의 첫 번째 페이지가 72ppi로 래스터화되고 생성된 미리보기 이미지의 크기가 2048 x 2048픽셀로 조정됩니다. 일반 배포의 경우 해상도를 최소 150ppi 이상으로 높일 수 있습니다. 예를 들어, 300ppi의 미국 문자 크기 문서에는 각각 최대 너비와 높이가 2550 x 3300픽셀이 필요합니다.

[최대 폭] 및 [최대 높이]는 래스터화할 해상도를 제한합니다. 예를 들어 최대값이 변경되지 않고 해상도가 300ppi로 설정된 경우 US Letter 문서는 186ppi로 래스터화됩니다. 즉, 문서는 1581 x 2046픽셀입니다.

`Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소는 메모리에서 너무 큰 이미지를 만들지 않도록 최대값을 정의했습니다. 이렇게 큰 이미지는 JVM(Java™ Virtual Machine)에 제공된 메모리를 오버플로할 수 있습니다. 구성된 수의 병렬 워크플로우를 관리할 만큼 충분한 메모리를 JVM에 제공하고 각 워크플로우가 구성된 최대 크기로 이미지를 생성할 수 있도록 주의해야 합니다.

### InDesign(INDD) 파일 형식 {#indesign-indd-file-format}

이 파일 형식의 동적 변환을 생성할 수 있도록 INDD 파일 수집을 지원하려면 이미지 사전 설정을 만들기 전에 다음 정보를 검토하십시오.

InDesign 파일의 경우, Adobe InDesign Server이 Experience Manager과 통합된 경우에만 하위 자산이 추출됩니다. 참조된 자산은 메타데이터를 기반으로 연결됩니다. InDesign Server은 연결에 필요하지 않습니다. 그러나 InDesign 파일과 참조된 에셋 사이에 연결되는 링크가 만들어지려면 InDesign 파일이 처리되기 전에 참조된 에셋이 Experience Manager 내에 있어야 합니다.

<!-- See [Integrate Experience Manager Assets with InDesign Server](/help/assets/indesign.md). -->

`DAM Update Asset` 워크플로의 미디어 추출 프로세스 구성 요소는 사전 구성된 여러 확장 스크립트를 실행하여 InDesign 파일을 처리합니다.

![미디어 추출 프로세스의 인수에 있는 ExtendScript 경로](/help/assets/dynamic-media/assets/6_5_mediaextractionprocess.png)

DAM 자산 업데이트 워크플로우에서 미디어 추출 프로세스 구성 요소 인수의 ExtendScript 경로.

Dynamic Media 통합에서 사용하는 스크립트는 다음과 같습니다.


| ExtendScript 이름 | 기본값 | 설명 |
|---|---|---|
| ThumbnailExport.jsx | 예 | `Dynamic Media Process Image Assets` 프로세스 구성 요소에 의해 최적화되고 PTIFF 렌디션으로 변환되는 300PPI `thumbnail.jpg` 렌디션을 생성합니다. |
| JPEGPagesExport.jsx | 예 | 각 페이지에 대해 300PPI JPEG 하위 자산을 생성합니다. JPEG 하위 에셋은 InDesign 에셋 아래에 저장된 실제 에셋입니다. 또한 `DAM Update Asset` 워크플로우에서 최적화되고 PTIFF로 변환됩니다. |
| PDFPagesExport.jsx | 아니요 | 각 페이지에 대한 PDF 하위 자산을 생성합니다. PDF 하위 자산이 앞에서 설명한 대로 처리됩니다. PDF은 단일 페이지만 포함하므로 하위 자산이 생성되지 않습니다. |

### 이미지 썸네일 크기 구성 {#configuring-image-thumbnail-size}

**[!UICONTROL DAM 자산 업데이트]** 워크플로우에서 이러한 설정을 구성하여 썸네일 크기를 구성할 수 있습니다. 이 워크플로에서는 이미지 에셋의 썸네일 크기를 구성할 수 있는 두 가지 단계가 있습니다. 하나(**[!UICONTROL Dynamic Media 프로세스 이미지 Assets]**)가 동적 이미지 자산에 사용됩니다. 다른 (**[!UICONTROL 프로세스 썸네일]**)은 정적 썸네일 생성에 사용되거나 다른 모든 프로세스에서 썸네일을 생성하지 못할 때 사용됩니다. *둘 다*&#x200B;의 설정이 동일해야 합니다.

With the **[!UICONTROL Dynamic Media Process Image Assets]** step, thumbnails are generated by the image server, and this configuration is independent of the configuration applied to the **[!UICONTROL Process Thumbnails]** step. Generating thumbnails through the **[!UICONTROL Process Thumbnails]** step is the slowest and most memory intensive way to create thumbnails.

썸네일 크기가 **[!UICONTROL width:height:center]**(예: `80:80:false`) 형식으로 정의되었습니다. 폭과 높이는 축소판의 크기를 픽셀 단위로 결정합니다. 중심 값은 false 또는 true입니다. true로 설정하면 썸네일 이미지의 크기가 구성에 지정된 것과 정확히 일치함을 나타냅니다. 크기가 조정된 이미지가 더 작으면 축소판 내에서 가운데에 표시됩니다.

>[!NOTE]
>
>* EPS 파일의 썸네일 크기는 썸네일 아래의 **[!UICONTROL 인수]** 탭의 **[!UICONTROL EPS 썸네일]** 단계에서 구성됩니다.
>
>* 비디오의 썸네일 크기는 **[!UICONTROL 인수]** 아래의 **[!UICONTROL 프로세스]** 탭의 **[!UICONTROL FFmpeg 썸네일]** 단계에서 구성됩니다.
>

**이미지 썸네일 크기를 구성하려면:**

1. **[!UICONTROL 도구]** > **[!UICONTROL 워크플로]** > **[!UICONTROL 모델]** > **[!UICONTROL DAM 자산 업데이트]** > **[!UICONTROL 편집]**&#x200B;으로 이동합니다.
1. **[!UICONTROL Dynamic Media 프로세스 이미지 Assets]** 단계를 선택하고 **[!UICONTROL 썸네일]** 탭을 선택합니다. 필요에 따라 썸네일 크기를 변경한 다음 **[!UICONTROL 확인]**&#x200B;을 선택합니다.

   ![6_5_dynamicmediaprocessimageassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. **[!UICONTROL 축소판 처리]** 단계를 선택한 다음 **[!UICONTROL 축소판]** 탭을 선택합니다. 필요에 따라 썸네일 크기를 변경한 다음 **[!UICONTROL 확인]**&#x200B;을 선택합니다.

   >[!NOTE]
   >
   >The values in the thumbnails argument in the **[!UICONTROL Process Thumbnails]** step must match the thumbnails argument in the **[!UICONTROL Dynamic Media Process Image Assets]** step.

1. 변경 내용을 워크플로우에 저장하려면 **[!UICONTROL 저장]**&#x200B;을(를) 선택하십시오.

### 표시되는 이미지 사전 설정 수 증가 또는 감소 {#increasing-or-decreasing-the-number-of-image-presets-that-display}

만든 이미지 사전 설정은 에셋을 미리 볼 때 동적 변환으로 사용할 수 있습니다. Experience Manager은 **[!UICONTROL 자세히 보기 > 렌디션]**&#x200B;에서 에셋을 볼 때 다양한 동적 렌디션을 표시합니다. 표시되는 표현물의 한도를 늘리거나 줄일 수 있습니다.

**표시되는 이미지 사전 설정 수를 늘리거나 줄이려면**

1. CRXDE Lite([https://localhost:4502/crx/de](https://localhost:4502/crx/de))로 이동합니다.
1. `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`의 이미지 사전 설정 나열 노드로 이동합니다.

   ![increase_decreasethenumberofimagepresetssetdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. In the **[!UICONTROL limit]** property, change the **[!UICONTROL Value]**, which is set to 15 by default, to the desired number.
1. `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`의 이미지 사전 설정 데이터 원본으로 이동합니다.

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. limit 속성에서 숫자를 원하는 숫자(예: `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`)로 변경합니다.
1. **[!UICONTROL 모두 저장]**&#x200B;을 선택합니다.

### 이미지 사전 설정 만들기 {#creating-image-presets}

미리 보거나 게시할 때 이미지 간에 설정을 일관되게 적용할 수 있도록 이미지 사전 설정을 만듭니다.

>[!NOTE]
>
>Internet Explorer 9를 사용하는 경우 사전 설정을 작성한 후 바로 사전 설정 목록에 표시되지 않습니다. 이 문제를 해결하려면 IE9에 대한 캐시를 비활성화하십시오.

이러한 파일 형식의 동적 렌디션을 생성할 수 있도록 AI, PDF 및 EPS 파일 수집을 지원하려면 이미지 사전 설정을 만들기 전에 다음 정보를 검토하십시오.

[Adobe Illustrator(AI), PostScript®(EPS) 및 PDF 파일 형식](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)을 참조하세요.

이 파일 형식의 동적 변환을 생성할 수 있도록 INDD 파일 수집을 지원하려면 이미지 사전 설정을 만들기 전에 다음 정보를 검토하십시오.

[INDD(InDesign) 파일 형식](#indesign-indd-file-format)을 참조하세요.

**이미지 사전 설정을 만들려면:**

1. Experience Manager에서 Experience Manager 로고를 선택하여 전역 탐색 콘솔에 액세스한 다음 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 이미지 사전 설정]**(으)로 이동합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >To make this image preset responsive, erase the values in the **[!UICONTROL width]** and **[!UICONTROL height]** fields and leave them blank.

1. **[!UICONTROL 이미지 사전 설정 편집]** 창에서 이름을 포함하여 **[!UICONTROL 기본]** 및 **[!UICONTROL 고급]** 탭에 값을 적절하게 입력합니다. The options are outlined in [Image Preset Options](#image-preset-options). Presets appear in the left pane and can be used on-the-fly with other assets.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

### 응답형 이미지 사전 설정 만들기 {#creating-a-responsive-image-preset}

응답형 이미지 사전 설정을 만들려면 [이미지 사전 설정 만들기](#creating-image-presets)의 단계를 수행하십시오. **[!UICONTROL 이미지 사전 설정 편집]** 창에 높이와 너비를 입력할 때 값을 지우고 비워 둡니다.

이 필드를 비워 두면 Experience Manager에게 이 이미지 사전 설정이 응답함을 알려줍니다. 다른 값은 적절하게 조정할 수 있습니다.

>[!NOTE]
>
>To see the **[!UICONTROL URL]** and **[!UICONTROL RESS]** buttons when applying an image preset to an asset, the asset must be published.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>이미지 사전 설정 및 이미지 에셋은 자동으로 게시됩니다.

### 이미지 사전 설정 옵션 {#image-preset-options}

이미지 사전 설정을 만들거나 편집할 때 이 섹션에 설명된 옵션이 있습니다. 또한 Adobe은 다음과 같은 &quot;모범 사례&quot; 옵션 선택 사항을 시작할 것을 권장합니다.

* **[!UICONTROL 형식]**(**[!UICONTROL 기본]** 탭) - **[!UICONTROL JPEG]** 또는 요구 사항에 맞는 다른 형식을 선택하십시오. All web browsers support the JPEG image format; it offers a good balance between small files sizes and image quality. However, JPEG format images use a lossy compression scheme that can introduce unwanted image artifacts if the compression setting is too low. For that reason, Adobe recommends setting the compression quality to 75. This setting offers a good balance between image quality and small file size.

* **[!UICONTROL Enable Simple Sharpening]** - Do not select **[!UICONTROL Enable Simple Sharpening]** (this sharpening filter offers less control than Unsharp Masking settings).

* **[!UICONTROL 선명하게 하기: 리샘플링 모드]** - **[!UICONTROL Sharp2]**&#x200B;을(를) 선택합니다.

#### 기본 탭 옵션 {#basic-tab-options}

| 필드 | 설명 |
| --- | --- |
| **이름** | 공백 없이 수사적 이름을 입력합니다. 사용자가 이 이미지 사전 설정을 식별하는 데 도움이 되도록 이름에 이미지 크기 사양을 포함하십시오. |
| **너비 및 높이** | 이미지가 표시될 크기를 픽셀로 입력합니다. 폭과 높이는 0픽셀보다 커야 합니다. 값이 0이면 사전 설정이 만들어지지 않습니다. 두 값이 모두 비어 있으면 반응형 이미지 사전 설정이 만들어집니다. |
| **형식** | 메뉴에서 형식을 선택합니다.<br>JPEG **선택**&#x200B;은(는) 다음과 같은 기타 옵션을 제공합니다.<br>· **품질** - JPEG 품질 기준은 1-100입니다. 슬라이더를 드래그하면 배율이 표시됩니다.<br>· **JPG 색차 다운샘플링 사용** - 눈은 고주파 광도보다 고주파 색상 정보에 덜 민감하므로 JPEG 이미지는 이미지 정보를 광도와 색상 구성 요소로 나눕니다. JPEG 이미지가 압축되면 광도 구성 요소는 최대 해상도로 유지되는 반면, 색상 구성 요소는 픽셀 그룹의 평균에 의해 다운샘플링됩니다. 다운샘플링은 체감 품질에 거의 영향을 미치지 않으면서 데이터 양을 1/2 또는 1/3 줄입니다. 회색 음영 이미지에는 다운샘플링을 적용할 수 없습니다. 이 기법은 대비가 높은 이미지(예: 오버레이된 텍스트가 있는 이미지)에 유용한 압축의 양을 줄입니다.<br><br>알파 포함 **GIF** 또는 **GIF을 선택하면 다음과 같은 추가** GIF 색상 양자화&#x200B;**옵션이 제공됩니다.<br>·**&#x200B;유형&#x200B;**-**&#x200B;적응형&#x200B;**(기본값),**&#x200B;웹&#x200B;**또는** Macintosh **선택.** **Alpha GIF**&#x200B;을(를) 선택하면 Macintosh 옵션을 사용할 수 없습니다.<br>· **디더** - **분산** 또는 **해제**&#x200B;를 선택합니다.<br>· **색상 수** - 숫자 2 - 256을 입력하십시오.<br>· **색상 목록** - 쉼표로 구분된 목록을 입력하십시오. 예를 들어 흰색, 회색 및 검은색은 `000000,888888,ffffff`을(를) 입력합니다.<br><br>알파 포함 **PDF**, **TIFF** 또는 **TIFF**&#x200B;을 선택하면 다음과 같은 추가 옵션이 제공됩니다.<br>· **압축** - 압축 알고리즘을 선택하십시오. PDF의 알고리즘 옵션은 **없음**, **Zip** 및 **Jpeg**&#x200B;이고, TIFFTIFF 의 경우 **없음**, **LZW**, **Jpeg** 및 **Zip**&#x200B;이며, Alpha의 경우 **없음**, **LZW** 및 **Zip**&#x200B;입니다.<br><br>Alpha이 있는 **PNG**, **PNG** 또는 **EPS**&#x200B;을(를) 선택하면 추가 옵션이 없습니다. |
| **선명하게 하기** | 모든 크기 조절 후 이미지에 기본 선명하게 하기 필터를 적용하려면 **단순 선명하게 하기 사용**&#x200B;을 선택하십시오. 선명하게 하기는 다른 크기의 이미지를 표시할 때 발생하는 흐릿함을 보상하는 데 도움이 될 수 있습니다. |

#### 고급 탭 옵션 {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>필드</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong>색상 공간</strong></td>
   <td>색상 공간으로 <strong>RGB, CMYK,</strong> 또는 <strong>회색 음영</strong>을 선택하십시오.</td>
  </tr>
  <tr>
   <td><strong>색상 프로필</strong></td>
   <td>작동하는 프로필과 다른 경우 에셋을 변환할 출력 색상 공간 프로필을 선택합니다.</td>
  </tr>
  <tr>
   <td><strong>렌더링 의도</strong></td>
   <td>기본 렌더링 의도를 재정의할 수 있습니다. 렌더링 의도는 대상 색상 프로파일에서 재현할 수 없는 색상(색상 영역 밖)에 발생하는 현상을 결정합니다. ICC 프로파일과 호환되지 않으면 렌더링 의도가 무시됩니다.
    <ul>
     <li>원본 이미지에서 하나 이상의 색상이 대상 색상 공간의 색상 영역을 벗어나는 경우 한 색상 공간의 전체 색상 영역을 다른 색상 공간으로 압축하려면 <strong>Perceptual</strong>을 선택합니다.</li>
     <li>현재 색상 공간의 색상이 대상 색상 공간에서 색상 영역을 벗어난 경우 <strong>상대 색상 지표</strong>을 선택합니다. 또한 다른 색상에 영향을 주지 않고 대상 색상 공간의 색상 영역 내에서 가장 가까운 가능한 색상에 매핑할 수 있습니다. </li>
     <li>대상 색상 공간으로 변환할 때 원본 이미지 색상 채도를 재현하려면 <strong>채도</strong>를 선택합니다. </li>
     <li>이미지의 밝기를 변경하는 흰점이나 검정점을 조정하지 않고 색상을 정확하게 일치시키려면 <strong>절대 색도계</strong>를 선택하십시오.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>검은 점 보상</strong></td>
   <td>출력 프로파일이 이 기능을 지원하는 경우 이 옵션을 선택합니다. 지정된 ICC 프로파일과 호환되지 않으면 검은 점 보상이 무시됩니다.</td>
  </tr>
  <tr>
   <td><strong>디더링</strong></td>
   <td>색상 밴딩 아티팩트를 방지하거나 줄이려면 이 옵션을 선택합니다. </td>
  </tr>
  <tr>
   <td><strong>선명하게 하기 유형</strong></td>
   <td><p><strong>없음</strong>, <strong>선명 효과</strong> 또는 <strong>선명하지 않은 마스크</strong>를 선택하십시오. </p>
    <ul>
     <li>선명하게 하기를 비활성화하려면 <strong>없음</strong>을 선택하세요.</li>
     <li>모든 크기 조절 후 이미지에 기본 선명하게 하기 필터를 적용하려면 <strong>선명하게 </strong>을(를) 선택합니다. 선명하게 하기는 다른 크기의 이미지를 표시할 때 발생하는 흐릿함을 보상하는 데 도움이 될 수 있습니다. </li>
     <li>다운샘플링된 최종 이미지에서 선명하게 하기 필터 효과를 미세 조정하려면 <strong> 언샵 마스크</strong>를 선택합니다. 효과의 강도, 효과의 반경(픽셀 단위) 및 무시되는 대비 임계값을 제어할 수 있습니다. 이 효과는 Photoshop의 "언샵 마스크" 필터와 동일한 옵션을 사용합니다.</li>
    </ul> <p><strong>언샵 마스크</strong>에는 다음 옵션이 있습니다.</p>
    <ul>
     <li><strong>양</strong> - 가장자리 픽셀에 적용된 대비의 양을 제어합니다. 기본 실수 값은 1.0입니다. 고해상도 이미지의 경우 최대 5.0까지 늘릴 수 있습니다. 양을 필터 강도를 나타내는 척도로 간주합니다.</li>
     <li><strong>반경</strong> - 선명하게 하기가 적용되는 가장자리 픽셀 주위의 픽셀 수를 결정합니다. 고해상도 이미지의 경우 1~2의 실제 숫자를 입력합니다. 낮은 값은 가장자리 픽셀만 선명하게 하고 높은 값은 넓은 폭의 픽셀을 선명하게 합니다. 올바른 값은 이미지의 크기에 따라 다릅니다.</li>
     <li><strong>임계값</strong> - 언샵 마스크 필터가 적용될 때 무시할 대비 범위를 결정합니다. 즉, 이 옵션은 가장자리 픽셀로 간주하여 선명하게 되기 전에 선명해진 픽셀이 주변 영역과 얼마나 달라야 하는지 결정합니다. 잡음이 생기는 것을 피하기 위해 2에서 20 사이의 정수 값으로 실험하세요. </li>
     <li><strong>적용 대상</strong> - 각 색상 또는 밝기에 선명하게 하기 취소를 적용할지 여부를 결정합니다.</li>
    </ul>
    <div>
      선명하게 하기는에 설명되어 있습니다.
     <a href="https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html#dynamic-media">Experience Manager Dynamic Media에서 이미지 선명하게 하기 사용</a> 비디오, <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/using/master-files/sharpening-image.html#master-files">이미지 선명하게 하기</a> 온라인 도움말 항목 및 <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/assets/s7_sharpening_images.pdf">Dynamic Media Classic에서 이미지 선명하게 하기 모범 사례</a> 다운로드 가능한 PDF.
    </div> </td>
  </tr>
  <tr>
   <td><strong>리샘플링 모드</strong></td>
   <td><strong>리샘플링 모드</strong> 옵션을 선택하십시오. 다음 옵션을 사용하면 이미지가 다운샘플링될 때 이미지가 선명해집니다.
    <ul>
     <li><strong>이중선형</strong> - 가장 빠른 리샘플링 방법입니다. 일부 앨리어싱 아티팩트가 눈에 띕니다.</li>
     <li><strong>쌍입방</strong> - CPU 사용량이 증가하지만 덜 눈에 띄는 앨리어싱 아티팩트로 더 선명한 이미지를 만듭니다.</li>
     <li><strong>Sharp2</strong> - 쌍입방보다 약간 더 선명한 결과를 만들 수 있지만 CPU 비용이 더 많이 듭니다.</li>
     <li><strong>Bi-Sharp</strong> - 이미지 크기를 줄이기 위한 Photoshop 기본 리샘플러를 선택합니다. 이 리샘플러는 Adobe Photoshop에서 <strong>bicubic sharper</strong>입니다.</li>
     <li><strong>각 색상</strong> 및 <strong>밝기</strong> - 각 메서드는 색상 또는 밝기를 기반으로 할 수 있습니다. 기본적으로 <strong>각 색상</strong>이 선택됩니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>인쇄 해상도</strong></td>
   <td>이 이미지를 인쇄할 해상도를 선택합니다. 기본값은 72픽셀입니다.</td>
  </tr>
  <tr>
   <td><strong>이미지 수정자</strong></td>
   <td><p>UI에서 사용할 수 있는 일반적인 이미지 설정 외에 Dynamic Media에서는 <strong>이미지 수정자</strong> 필드에서 지정할 수 있는 다양한 고급 이미지 수정 사항을 지원합니다. 이러한 매개 변수는 <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/syntax-and-features/image-serving-http/c-command-overview.html">이미지 서버 프로토콜 명령 참조</a>에 정의되어 있습니다.</p> <p>중요: API에 나열된 다음 기능은 지원되지 않습니다.</p>
    <ul>
     <li>기본 템플릿 및 텍스트 렌더링 명령: <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> 및 <code>textPs=</code></li>
     <li>지역화 명령: <code>locale=</code> 및 <code>req=xlate</code></li>
     <li><code>req=set</code> 는 일반 용도로 사용할 수 없습니다.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>비핵심 Dynamic Media 서비스: SVG, 이미지 렌더링 및 Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### 이미지 수정자를 사용하여 이미지 사전 설정 옵션 정의 {#defining-image-preset-options-with-image-modifiers}

기본 및 고급 탭에서 사용할 수 있는 옵션 외에도 이미지 사전 설정을 정의할 때 더 많은 옵션을 제공하도록 이미지 수정자를 정의할 수 있습니다. 이미지 렌더링은 Dynamic Media 이미지 렌더링 API를 사용하며 [HTTP 프로토콜 참조](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-rendering-api/http-protocol-reference/c-ir-introduction.html#image-rendering-api)에서 자세히 정의됩니다.

다음은 이미지 수정자로 수행할 수 있는 작업의 몇 가지 기본 예입니다.

>[!NOTE]
>
>일부 이미지 수정자 [을(를) Experience Manager](#advanced-tab-options)에서 사용할 수 없습니다.

* [op_invert](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert.html) - 부정적인 이미지 효과에 대한 각 색상 구성 요소를 반전시킵니다.

  ```xml {.line-numbers}
  &op_invert=1
  ```

  ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_blur](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur.html) - 이미지에 흐림 효과 필터를 적용합니다.

  ```xml {.line-numbers}
  &op_blur=7
  ```

  ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* 결합된 명령 - op_blur 및 op-invert

  ```xml {.line-numbers}
  &op_invert=1&op_blur=7
  ```

  ![chlimage_1-80](assets/chlimage_1-501.png)

* [op_brightness](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness.html) - 밝기를 줄이거나 늘립니다.

  ```xml {.line-numbers}
  &op_brightness=58
  ```

  ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac.html) - 이미지 불투명도를 조정합니다. 전경 불투명도를 줄일 수 있습니다.

  ```xml {.line-numbers}
  opac=29
  ```

  ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

### 이미지 사전 설정 편집 {#modifying-image-presets}

1. Experience Manager에서 Experience Manager 로고를 선택하여 전역 탐색 콘솔에 액세스한 다음 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 이미지 사전 설정]**(으)로 이동합니다.

   ![6_5_imagepreset-editpreset](assets/6_5_imagepreset-editpreset.png)

1. 사전 설정을 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 선택합니다. **[!UICONTROL 이미지 사전 설정 편집]** 창이 열립니다.
1. 변경 내용을 적용하고 **[!UICONTROL 저장]**&#x200B;을 선택하여 변경 내용을 저장하거나 **[!UICONTROL 취소]**&#x200B;을 선택하여 변경 내용을 취소합니다.

### Publish 이미지 사전 설정 {#publishing-image-presets}

이미지 사전 설정은 자동으로 게시됩니다.

### 이미지 사전 설정 삭제 {#deleting-image-presets}

1. Experience Manager에서 Experience Manager 로고를 선택하여 전역 탐색 콘솔에 액세스하고 도구 아이콘을 선택합니다.
1. **[!UICONTROL Assets]** > **[!UICONTROL 이미지 사전 설정]**(으)로 이동합니다.
1. 사전 설정을 선택한 다음 **[!UICONTROL 삭제]**&#x200B;를 선택합니다. Dynamic Media에서 삭제할 것임을 확인합니다. **[!UICONTROL 삭제]**&#x200B;를 선택하여 제거하거나 **[!UICONTROL 취소]**&#x200B;를 선택하여 이미지 사전 설정으로 돌아갑니다.
