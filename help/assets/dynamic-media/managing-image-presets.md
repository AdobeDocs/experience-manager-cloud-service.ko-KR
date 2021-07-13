---
title: 이미지 사전 설정 관리
description: 이미지 사전 설정 및 이미지 사전 설정을 만들고, 수정하고, 관리하는 방법에 대해 알아봅니다.
feature: 이미지 사전 설정,뷰어,표현물
role: User
exl-id: a53f40ab-0e27-45f8-9142-781c077a04cc
source-git-commit: aba8896e304619fe7e73d61b52b83da40766477a
workflow-type: tm+mt
source-wordcount: '3634'
ht-degree: 2%

---

# 이미지 사전 설정 관리{#managing-image-presets}

이미지 사전 설정을 사용하면 Adobe Experience Manager Assets에서 동적으로 생성된 다른 크기, 다른 형식 또는 다른 이미지 속성을 사용하여 이미지를 동적으로 전달할 수 있습니다. 각 이미지 사전 설정은 이미지 표시를 위한 크기 및 형식 지정 명령의 사전 정의된 컬렉션을 나타냅니다. 이미지 사전 설정을 만들 때 이미지 제공 크기를 선택합니다. 또한, 이미지를 볼 수 있도록 전달할 때 이미지의 모양을 최적화하도록 서식 명령을 선택할 수도 있습니다.

관리자는 자산을 내보내기 위해 사전 설정을 만들 수 있습니다. 사용자는 이미지를 내보낼 때 사전 설정을 선택할 수 있으며, 이 경우 관리자가 지정하는 사양에 맞게 이미지를 재포맷할 수도 있습니다.

응답형 이미지 사전 설정을 만들 수도 있습니다. 응답형 이미지 사전 설정을 자산에 적용하는 경우, 표시되는 장치나 화면 크기에 따라 달라집니다. RGB 또는 회색 외에 색상 공간에서 CMYK를 사용하도록 이미지 사전 설정을 구성할 수 있습니다.

이 섹션에서는 이미지 사전 설정을 만들고, 수정하고, 일반적으로 관리하는 방법을 설명합니다. 미리 볼 때 언제든지 이미지에 이미지 사전 설정을 적용할 수 있습니다. [이미지 사전 설정 적용](/help/assets/dynamic-media/image-presets.md)을 참조하십시오.

>[!NOTE]
>
>스마트 이미징은 기존 이미지 사전 설정에서 작동하며 마지막 전달 순간에 인텔리전스를 사용하여 브라우저 또는 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다. 자세한 내용은 [스마트 이미징](/help/assets/dynamic-media/imaging-faq.md) 을 참조하십시오.

## 이미지 사전 설정에 대해 알아보기 {#understanding-image-presets}

매크로와 마찬가지로 이미지 사전 설정은 이름 아래에 저장된 크기 및 형식 명령의 사전 정의된 컬렉션입니다. 이미지 사전 설정 작동 방식을 이해하려면 웹 사이트에서 각 제품 이미지를 데스크탑 및 모바일 게재에 대해 서로 다른 크기, 서로 다른 형식 및 압축률을 나타내야 한다고 가정합니다.

두 개의 이미지 사전 설정을 만들 수 있습니다. 데스크탑 버전의 경우 500 x 500 픽셀과 모바일 버전의 경우 150 x 150 픽셀이 포함된 픽셀 이미지를 500x500픽셀로 표시하기 위해 `Enlarge`라는 두 개의 이미지 사전 설정을 만들고, 이미지를 150 x 150픽셀로 표시하기 위해 `Thumbnail`라는 사전 설정을 만듭니다. `Enlarge` 및 `Thumbnail` 크기로 이미지를 전달하려면 Experience Manager이 이미지 사전 설정 확대 및 축소판 이미지 사전 설정의 정의를 찾습니다. 그런 다음 Experience Manager은 각 이미지 사전 설정의 크기 및 형식 지정 사양에 따라 이미지를 동적으로 생성합니다.

동적으로 전달될 때 크기가 줄어든 이미지는 선명도와 세부 사항을 잃을 수 있습니다. 이러한 이유로, 각 이미지 사전 설정에는 특정 크기로 전달될 때 이미지를 최적화하는 형식 지정 컨트롤이 포함되어 있습니다. 이러한 컨트롤을 사용하면 웹 사이트나 애플리케이션에 이미지가 전달될 때 이미지가 선명하고 명확하게 표시됩니다.

관리자는 이미지 사전 설정을 만들 수 있습니다. 이미지 사전 설정을 만들려면 처음부터 시작하거나 기존 이미지 사전 설정에서 시작하여 새 이름으로 저장할 수 있습니다.

## 이미지 사전 설정 관리 {#managing-image-presets-1}

전역 탐색 콘솔에 액세스할 Experience Manager 로고를 선택한 다음 도구 아이콘을 선택하고 **[!UICONTROL Assets]** > **[!UICONTROL 이미지 사전 설정]**&#x200B;으로 이동하여 Experience Manager에서 이미지 사전 설정을 관리합니다.

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>자산을 미리 보거나 전달할 때 만들어지는 모든 이미지 사전 설정은 동적 변환으로도 사용할 수 있습니다.
>
>이미지 사전 설정이 자동으로 게시되므로 *이미지 사전 설정을 게시할 필요가 없습니다.*
>
>[이미지 사전 설정 게시](#publishing-image-presets)를 참조하십시오.

>[!NOTE]
>
>자산의 세부 사항 보기에서 **[!UICONTROL 표현물]**&#x200B;을 선택하면 시스템에 다양한 표현물이 표시됩니다. 표시되는 이미지 사전 설정 수를 늘리거나 줄일 수 있습니다. [표시되는 이미지 사전 설정 수를 늘립니다](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Adobe Illustrator(AI), PostScript®(EPS) 및 PDF 파일 형식 {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

이러한 파일 형식의 동적 변환을 생성할 수 있도록 AI, EPS 및 PDF 파일 수집을 지원하려는 경우 이미지 사전 설정을 만들기 전에 다음 정보를 검토하십시오.

Adobe Illustrator의 파일 형식은 PDF의 변형입니다. Experience Manager 자산 컨텍스트에서 주요 차이점은 다음과 같습니다.

* Adobe Illustrator 문서는 여러 레이어가 있는 단일 페이지로 구성됩니다. 각 레이어는 기본 Illustrator 자산 아래에 PNG 하위 자산으로 추출됩니다.
* PDF 문서는 하나 이상의 페이지로 구성됩니다. 각 페이지는 기본 다중 페이지 PDF 문서 아래에 단일 페이지 PDF 하위 자산으로 추출됩니다.

하위 자산은 전체 `DAM Update Asset` 워크플로우 내에서 `Create Sub Asset process` 구성 요소에 의해 만들어집니다. 워크플로우 내에서 이 프로세스 구성 요소를 보려면 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]** > **[!UICONTROL DAM 자산 업데이트]** > **[!UICONTROL 편집]**&#x200B;으로 이동합니다.

<!-- See also [Viewing pages of a multi-page file](/help/assets/manage-linked-subassets.md#view-pages-of-a-multi-page-file). -->

자산을 열 때 하위 자산이나 페이지를 보고, 컨텐츠 메뉴를 선택하고 **[!UICONTROL 하위 자산]** 또는 **[!UICONTROL 페이지]**&#x200B;를 선택할 수 있습니다. 하위 자산은 실제 자산입니다. 즉, PDF 페이지는 `Create Sub Asset` 워크플로우 구성 요소에 의해 추출됩니다. 그런 다음 기본 자산 아래의 `page1.pdf`, `page2.pdf` 등으로 저장됩니다. 저장되면 `DAM Update Asset` 워크플로우가 처리합니다.

Dynamic Media을 사용하여 AI, EPS 또는 PDF 파일에 대한 동적 렌디션을 미리 보고 생성하려면 다음 처리 단계를 수행해야 합니다.

1. `DAM Update Asset` 워크플로우에서 `Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소는 구성된 해상도를 사용하여 원본 자산의 첫 페이지를 `cqdam.preview.png` 표현물로 래스터화합니다.

1. 그런 다음 `cqdam.preview.png` 렌디션은 워크플로우 내의 `Dynamic Media Process Image Assets` 프로세스 구성 요소에 의해 PTIFF에 최적화됩니다.

>[!NOTE]
>
>DAM 자산 업데이트 워크플로우에서 **[!UICONTROL EPS 축소판 그림]** 단계에서는 EPS 파일의 축소판 그림을 생성합니다.

#### PDF/AI/EPS 자산 메타데이터 속성 {#pdf-ai-eps-asset-metadata-properties}

| **메타데이터 속성** | **설명** |
|---|---|
| dam:Physicalwidthinsites | 문서 너비(인치) |
| dam:Physicalheight | 문서 높이(인치) |

`DAM Update Asset` 워크플로우를 통해 `Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소 옵션에 액세스합니다.

왼쪽 위의 Adobe Experience Manager에서 을(를) 선택하고 **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]**&#x200B;로 이동합니다. 워크플로우 모델 페이지에서 **[!UICONTROL DAM 자산 업데이트]**&#x200B;를 선택한 다음 도구 모음에서 **[!UICONTROL 편집]**&#x200B;을 선택합니다. DAM 자산 업데이트 워크플로우 페이지에서 `Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소를 두 번 탭하여 해당 단계 속성 대화 상자를 엽니다.

#### PDF/AI 이미지 미리 보기 변환 옵션 래스터화 {#rasterize-pdf-ai-image-preview-rendition-options}

![PDF 또는 AI 워크플로우를 래스터화하는 인수](assets/rasterize_pdf_ai_image_preview.png)

PDF 또는 AI 워크플로우를 래스터화하는 인수

| 프로세스 인수 | 기본 설정 | 설명 |
|---|---|---|
| MIME 유형 | application/pdf<br>application/postscript<br>application/illustrator | PDF 또는 Illustrator 문서로 간주되는 문서 MIME 유형 목록입니다. |
| 최대 너비 | 2048년 | 생성된 미리 보기 표현물의 최대 너비(픽셀 단위)입니다. |
| 최대 높이 | 2048년 | 생성된 미리 보기 표현물의 최대 높이(픽셀 단위)입니다. |
| 해상도 | 72 | 첫 번째 페이지를 ppi(인치당 픽셀 수)로 래스터화하는 해상도. |

기본 프로세스 인수를 사용하면 PDF/AI 문서의 첫 번째 페이지가 72ppi로 래스터화되고 생성된 미리 보기 이미지의 크기가 2048 x 2048픽셀로 지정됩니다. 일반적인 배포의 경우 해상도를 최소 150ppi 이상으로 높일 수 있습니다. 예를 들어, 300ppi의 미국 문자 크기 문서는 각각 최대 너비 및 높이가 2550 x 3300픽셀이어야 합니다.

[최대 너비] 및 [최대 높이]는 래스터화할 해상도를 제한합니다. 예를 들어 최대 값이 변경되지 않고 해상도가 300ppi로 설정되는 경우 미국 편지 문서는 186ppi로 래스터화됩니다. 즉, 문서는 1581 x 2046 픽셀입니다.

`Rasterize PDF/AI Image Preview Rendition` 프로세스 구성 요소에는 메모리에 지나치게 큰 이미지를 만들지 않도록 정의된 최대값이 있습니다. 이러한 큰 이미지는 JVM(Java™ Virtual Machine)에 제공된 메모리를 오버플로할 수 있습니다. 구성된 최대 구성 크기로 이미지를 만들 수 있는 충분한 메모리를 JVM에 제공하여 구성된 병렬 워크플로우 수를 관리할 수 있도록 해야 합니다.

### InDesign(INDD) 파일 형식 {#indesign-indd-file-format}

이 파일 형식의 동적 렌디션을 생성할 수 있도록 INDD 파일 처리를 지원하려는 경우 이미지 사전 설정을 만들기 전에 다음 정보를 검토하십시오.

InDesign 파일의 경우, Adobe InDesign Server이 Experience Manager과 통합된 경우에만 하위 자산이 추출됩니다. 참조된 자산은 메타데이터를 기준으로 연결됩니다. InDesign Server은 연결에 필요하지 않습니다. 그러나 InDesign 파일과 참조된 자산 간에 링크를 만들려면 InDesign 파일이 처리되기 전에 참조된 자산이 Experience Manager 내에 있어야 합니다.

<!-- See [Integrate Experience Manager Assets with InDesign Server](/help/assets/indesign.md). -->

`DAM Update Asset` 워크플로우의 미디어 추출 프로세스 구성 요소는 사전 구성된 스크립트 확장 을 실행하여 InDesign 파일을 처리합니다.

![미디어 추출 프로세스 인수의 ExtendScript 경로](/help/assets/dynamic-media/assets/6_5_mediaextractionprocess.png)

DAM 자산 업데이트 워크플로우에서 미디어 추출 프로세스 구성 요소의 인수에 ExtendScript이 패싱합니다.

다음 스크립트는 Dynamic Media 통합에서 사용됩니다.


| ExtendScript 이름 | 기본값 | 설명 |
|---|---|---|
| ThumbnailExport.jsx | 예 | `Dynamic Media Process Image Assets` 프로세스 구성 요소에 의해 최적화되고 PTIFF 표현물로 전환된 300PPI `thumbnail.jpg` 변환을 생성합니다. |
| JPEGPagesExport.jsx | 예 | 각 페이지에 대해 300PPI JPEG 하위 자산을 생성합니다. JPEG 하위 자산은 InDesign 자산 아래에 저장된 실제 자산입니다. 또한 최적화되어 `DAM Update Asset` 워크플로우에 의해 PTIFF로 전환됩니다. |
| PDFPagesExport.jsx | 아니오 | 각 페이지의 PDF 하위 자산을 생성합니다. PDF 하위 자산은 앞에서 설명한 대로 처리됩니다. PDF에는 단일 페이지만 포함되어 있으므로 하위 자산이 생성되지 않습니다. |

### 이미지 축소판 크기 구성 {#configuring-image-thumbnail-size}

**[!UICONTROL DAM 자산 업데이트]** 워크플로우에서 이러한 설정을 구성하여 축소판의 크기를 구성할 수 있습니다. 워크플로우에서는 이미지 자산의 축소판 크기를 구성할 수 있는 두 가지 단계가 있습니다. 동적 이미지 자산에 하나(**[!UICONTROL Dynamic Media 처리 이미지 자산]**)가 사용됩니다. 다른 프로세스(**[!UICONTROL Process Thumbnail]**)은 정적 축소판 생성에 사용되거나 다른 모든 프로세스가 축소판을 생성하지 못할 때 사용됩니다. 하지만 *모두*&#x200B;의 설정이 같아야 합니다.

**[!UICONTROL Dynamic Media 이미지 자산 처리]** 단계에서는 이미지 서버에서 미리 보기가 생성되며 이 구성은 **[!UICONTROL 축소판 처리]** 단계에 적용되는 구성과 독립적입니다. **[!UICONTROL 축소판 처리]** 단계를 통해 축소판을 생성하는 것은 축소판을 만드는 가장 느리고 메모리 집약적인 방법입니다.

축소판 크기 조절은 다음 형식으로 정의됩니다. **[!UICONTROL width:height:center]**(예: `80:80:false`). 너비와 높이는 축소판의 크기(픽셀 단위)를 결정합니다. 가운데 값은 false 또는 true입니다. true로 설정하면 축소판 이미지의 크기가 구성에 지정된 크기와 정확히 일치함을 나타냅니다. 크기가 조정된 이미지가 더 작으면 축소판 안에 가운데에 표시됩니다.

>[!NOTE]
>
>* EPS 파일의 축소판 크기는 축소판 그림 아래의 **[!UICONTROL 인수]** 탭의 **[!UICONTROL EPS 축소판 그림]** 단계에서 구성됩니다.
   >
   >
* 비디오의 축소판 크기는 **[!UICONTROL FFmpeg 축소판 그림]** 단계의 **[!UICONTROL 인수]** 아래의 **[!UICONTROL 프로세스]** 탭에 구성됩니다.

>



**이미지 축소판 크기를 구성하려면**

1. **[!UICONTROL 도구]** > **[!UICONTROL 워크플로우]** > **[!UICONTROL 모델]** > **[!UICONTROL DAM 자산 업데이트]** > **[!UICONTROL 편집]**&#x200B;으로 이동합니다.
1. **[!UICONTROL Dynamic Media 이미지 자산 처리]** 단계를 선택하고 **[!UICONTROL 축소판]** 탭을 선택합니다. 필요에 따라 축소판 크기를 변경한 다음 **[!UICONTROL 확인]**&#x200B;을 선택합니다.

   ![6_5_dynamicmediaprocesseassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. **[!UICONTROL 축소판 처리]** 단계를 선택한 다음 **[!UICONTROL 축소판]** 탭을 선택합니다. 필요에 따라 축소판 크기를 변경한 다음 **[!UICONTROL 확인]**&#x200B;을 선택합니다.

   >[!NOTE]
   >
   >**[!UICONTROL 축소판 처리]** 단계의 축소판 인수 값은 **[!UICONTROL Dynamic Media 이미지 자산 처리]** 단계의 축소판 인수와 일치해야 합니다.

1. **[!UICONTROL 저장]**&#x200B;을 선택하여 워크플로우에 대한 변경 사항을 저장합니다.

### 표시되는 이미지 사전 설정 수를 늘리거나 줄입니다 {#increasing-or-decreasing-the-number-of-image-presets-that-display}

만드는 이미지 사전 설정은 자산을 미리 볼 때 동적 변환으로 사용할 수 있습니다. Experience Manager은 **[!UICONTROL 세부 사항 보기 > 표현물]**&#x200B;에서 자산을 볼 때 다양한 동적 표현물을 보여줍니다. 표시되는 표현물의 제한을 늘리거나 줄일 수 있습니다.

**표시되는 이미지 사전 설정 수를 늘리거나 줄이려면:**

1. CRXDE Lite([https://localhost:4502/crx/de](https://localhost:4502/crx/de))로 이동합니다.
1. `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`에서 이미지 사전 설정 목록 노드로 이동합니다.

   ![display_decreasenumberofimageprestedisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. **[!UICONTROL limit]** 속성에서 기본적으로 15로 설정된 **[!UICONTROL 값]**&#x200B;을 원하는 숫자로 변경합니다.
1. `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`의 이미지 사전 설정 데이터 소스로 이동합니다.

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. limit 속성에서 숫자를 원하는 숫자(예: `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`)로 변경합니다.
1. **[!UICONTROL 모두 저장]**&#x200B;을 선택합니다.

### 이미지 사전 설정 만들기 {#creating-image-presets}

미리 보거나 게시할 때 이미지에 설정을 일관되게 적용할 수 있도록 이미지 사전 설정을 만듭니다.

>[!NOTE]
>
>Internet Explorer 9를 사용하는 경우 사전 설정을 만들면 저장 후 바로 사전 설정 목록에 표시되지 않습니다. 이 문제를 해결하려면 IE9용 캐시를 비활성화합니다.

이러한 파일 형식의 동적 렌디션을 생성할 수 있도록 AI, PDF 및 EPS 파일 수집을 지원하려는 경우 이미지 사전 설정을 만들기 전에 다음 정보를 검토하십시오.

[Adobe Illustrator(AI), PostScript®(EPS) 및 PDF 파일 형식](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)을 참조하십시오.

이 파일 형식의 동적 렌디션을 생성할 수 있도록 INDD 파일 처리를 지원하려는 경우 이미지 사전 설정을 만들기 전에 다음 정보를 검토하십시오.

[InDesign(INDD) 파일 형식](#indesign-indd-file-format)을 참조하십시오.

**이미지 사전 설정을 만들려면:**

1. Experience Manager에서 Experience Manager 로고를 선택하여 전역 탐색 콘솔에 액세스한 다음 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 이미지 사전 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >이 이미지 사전 설정을 응답형으로 만들려면 **[!UICONTROL width]** 및 **[!UICONTROL height]** 필드의 값을 지우고 비워 둡니다.

1. **[!UICONTROL 이미지 사전 설정 편집]** 창에서 이름을 포함하여 **[!UICONTROL 기본]** 및 **[!UICONTROL 고급]** 탭에 값을 적절하게 입력합니다. 옵션은 [이미지 사전 설정 옵션](#image-preset-options)에 요약되어 있습니다. 사전 설정은 왼쪽 창에 나타나며 다른 자산과 함께 즉시 사용할 수 있습니다.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

### 응답형 이미지 사전 설정 만들기 {#creating-a-responsive-image-preset}

응답형 이미지 사전 설정을 만들려면 [이미지 사전 설정 만들기](#creating-image-presets)의 단계를 수행하십시오. **[!UICONTROL 이미지 사전 설정 편집]** 창에서 높이 및 너비를 입력할 때 값을 지우고 비워 둡니다.

이 필드를 비워 두면 Experience Manager이 이 이미지 사전 설정이 응답형임을 알려줍니다. 다른 값을 적절하게 조정할 수 있습니다.

>[!NOTE]
>
>자산에 이미지 사전 설정을 적용할 때 **[!UICONTROL URL]** 및 **[!UICONTROL RESS]** 단추를 보려면 자산을 게시해야 합니다.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>이미지 사전 설정 및 이미지 자산은 자동으로 게시됩니다.

### 이미지 사전 설정 옵션 {#image-preset-options}

이미지 사전 설정을 만들거나 편집할 때 이 섹션에 설명된 옵션이 있습니다. 또한 Adobe은 다음과 같은 &quot;우수 사례&quot; 선택 사항을 시작할 것을 권장합니다.

* **[!UICONTROL 형식]** (**** 기본 탭) - 요구  **** 사항에 맞는 JPEG 또는 다른 형식을 선택합니다. 모든 웹 브라우저는 JPEG 이미지 형식을 지원합니다. 작은 파일 크기와 이미지 품질 간의 균형이 잘 유지됩니다. 그러나 JPEG 형식 이미지는 압축 설정이 너무 낮으면 원하지 않는 이미지 아티팩트를 가져올 수 있는 손실 압축 체계를 사용합니다. 이러한 이유로 Adobe은 압축 품질을 75로 설정할 것을 권장합니다. 이 설정은 이미지 품질과 작은 파일 크기 간의 균형을 잘 맞춥니다.

* **[!UICONTROL 단순 선명도 사용]**  - [단순 선명도 사용]을 선택하지  **[!UICONTROL 마십시오]** (이 선명도 필터는 [언샵 마스킹 설정]보다 덜 제어함).

* **[!UICONTROL 선명하게 하기: 재샘플링 모드]**  -  **[!UICONTROL Bi-Cubic을 선택합니다]**.

#### 기본 탭 옵션 {#basic-tab-options}

| 필드 | 설명 |
| --- | --- |
| **이름** | 공백 없이 수사적 이름을 입력합니다. 사용자가 이 이미지 사전 설정을 식별하는 데 도움이 되도록 이름에 이미지 크기 사양을 포함하십시오. |
| **폭과 높이** | 이미지가 전달되는 크기를 픽셀 단위로 입력하십시오. 너비와 높이는 0픽셀보다 커야 합니다. 두 값 중 하나가 0이면 사전 설정이 만들어지지 않습니다. 두 값이 모두 비어 있으면 응답형 이미지 사전 설정이 만들어집니다. |
| **형식** | 메뉴에서 형식을 선택합니다.<br>JPEG **** 를 선택하면 다음 다른 옵션이 제공됩니다. <br> **품질**  - JPEG 품질 크기가 1-100입니다. 슬라이더를 드래그하면 배율이 표시됩니다.<br>・  **JPG 색차 다운샘플링 활성화**  - 눈은 고주파 휘도보다 고주파 색상 정보에 덜 민감하므로 JPEG 이미지는 이미지 정보를 휘도 및 색상 구성 요소로 나눕니다. JPEG 이미지를 압축하면, 휘도 구성 요소를 전체 해상도로 두고, 색상 구성 요소는 픽셀 그룹을 평균화하여 다운샘플링됩니다. 다운샘플링을 수행하면 데이터 볼륨이 1/3 또는 1/3까지 감소하며 파악된 품질에 거의 영향을 주지 않습니다. 다운샘플링은 회색 음영 이미지에는 적용할 수 없습니다. 이 기술은 대비가 높은 이미지(예: 텍스트가 오버레이된 이미지)에 유용한 압축 양을 줄입니다.<br><br>알파 **** 가 있는 GIF 또는  **GIF를** 선택하면 다음과 같은 추가  **GIF 색상 양자화 옵션이 제공됩니다.** <br>유형 **-** 적응형 **(기본값),** 웹 **또는** Macintosh **** 선택. **알파**&#x200B;가 있는 GIF를 선택하면 Macintosh 옵션을 사용할 수 없습니다.<br>・  **Dither**  -  **** Diffuseor  **Off**&#x200B;를 선택합니다.<br>・  **색상 수**  - 2-256을 입력합니다.<br>・  **색상 목록**  - 쉼표로 구분된 목록을 입력합니다. 예를 들어, 흰색, 회색 및 검정인 경우 `000000,888888,ffffff`을 입력합니다.<br><br>알파 **로 PDF**,  **TIFF** 또는  **TIFF를** 선택하면 <br> **압축**  - 압축 알고리즘을 선택할 수 있습니다. PDF에 대한 알고리즘 옵션은 **None**, **Zip** 및 **Jpeg**&#x200B;입니다. TIFF의 경우 **없음**, **LZW**, **Jpeg** 및 **Zip**&#x200B;입니다. 및 알파의 TIFF는 **없음**, **LZW** 및 **Zip**&#x200B;입니다.<br><br>추가  **옵션을 제공하지 않는 PNG**,  **알파가 있는 PNG** 또는  **** EPS를 선택합니다. |
| **선명하게 하기** | 모든 크기 조절이 수행된 후 이미지에 기본 선명도 필터를 적용하려면 **단순 선명도 사용**&#x200B;을 선택합니다. 선명하게 하면 이미지를 다른 크기로 표시할 때 나타날 수 있는 흐림 효과를 보상하는 데 도움이 됩니다. |

#### 고급 탭 옵션 {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>필드</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td><strong>색상 공간</strong></td>
   <td>색상 공간의 경우 <strong>RGB, CMYK,</strong> 또는 <strong>회색 음영</strong>을 선택합니다.</td>
  </tr>
  <tr>
   <td><strong>색상 프로필</strong></td>
   <td>작업 프로필과 다른 경우 자산으로 변환할 출력 색상 공간 프로필을 선택합니다.</td>
  </tr>
  <tr>
   <td><strong>렌더링 의도</strong></td>
   <td>기본 렌더링 의도를 무시할 수 있습니다. 렌더링 의자는 대상 색상 프로필(색상 영역 외)에서 재현할 수 없는 색상에 대해 발생하는 결과를 결정합니다. Render Intent가 ICC 프로파일과 호환되지 않으면 무시됩니다.
    <ul>
     <li>원본 이미지의 하나 이상의 색상이 대상 색상 공간의 색상 영역을 벗어나는 경우 <strong>Perceptual</strong>을 선택하여 한 색상 공간의 전체 색상 영역을 다른 색상 공간으로 압축합니다.</li>
     <li>현재 색상 공간의 색상이 대상 색상 공간의 색상 영역을 벗어나는 경우 <strong>상대적 색상 지표</strong>를 선택합니다. 또한 다른 색상에 영향을 주지 않고 대상 색상 공간의 색상 영역 내에서 가장 가까운 색상으로 매핑하려고 합니다. </li>
     <li>대상 색상 공간으로 변환할 때 원본 이미지 색상 채도를 재현하려면 <strong>채도</strong>를 선택합니다. </li>
     <li>이미지의 밝기를 변경하는 흰색 점 또는 검정색 점을 조정하지 않고 색상을 정확히 일치시키려면 <strong>절대 색상 지표</strong>를 선택합니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>검은 점 보상</strong></td>
   <td>출력 프로파일이 이 기능을 지원하는 경우 이 옵션을 선택합니다. 지정한 ICC 프로필과 호환되지 않는 경우에는 Blackpoint 보상이 무시됩니다.</td>
  </tr>
  <tr>
   <td><strong>디더링</strong></td>
   <td>색상 밴딩 아티팩트를 방지하거나 줄이려면 이 옵션을 선택합니다. </td>
  </tr>
  <tr>
   <td><strong>선명하게 하기 유형</strong></td>
   <td><p><strong>없음</strong>, <strong>선명</strong> 또는 <strong>언샵 마스크</strong>를 선택합니다. </p>
    <ul>
     <li>선명하게 하기를 비활성화하려면 <strong>없음</strong>을 선택하십시오.</li>
     <li>모든 크기 조절이 수행된 후 이미지에 기본 선명도 필터를 적용하려면 <strong>선명 </strong>을 선택합니다. 선명하게 하면 이미지를 다른 크기로 표시할 때 나타날 수 있는 흐림 효과를 보상하는 데 도움이 됩니다. </li>
     <li>최종 다운샘플링된 이미지에 선명도 필터 효과를 세밀하게 조정하려면 <strong> 언샵 마스크</strong>를 선택합니다. 효과의 강도, 효과의 반경(픽셀 단위 측정) 및 무시되는 조명의 임계값을 제어할 수 있습니다. 이 효과는 Photoshop의 "언샵 마스크" 필터와 동일한 옵션을 사용합니다.</li>
    </ul> <p><strong>언샵 마스크</strong>에는 다음 옵션이 있습니다.</p>
    <ul>
     <li><strong>금액</strong>  - 가장자리 픽셀에 적용되는 대비의 양을 제어합니다. 기본 실수 값은 1.0입니다. 고해상도 이미지의 경우 최대 5.0까지 늘릴 수 있습니다. [금액]을 필터 강도 측정에 대해 생각해 보십시오.</li>
     <li><strong>반경</strong>  - 선명하게 하기에 영향을 주는 가장자리 픽셀을 둘러싸는 픽셀 수를 결정합니다. 고해상도 이미지의 경우 1부터 2까지의 실수를 입력합니다. 낮은 값은 가장자리 픽셀만 선명하게 합니다. 값이 높을수록 더 넓은 범위의 픽셀이 선명해집니다. 올바른 값은 이미지의 크기에 따라 다릅니다.</li>
     <li><strong>임계값</strong>  - 언샵 마스크 필터가 적용될 때 무시할 대비 범위를 결정합니다. 즉, 이 옵션은 가장자리 픽셀로 간주되고 선명하게 되기 전에 선명하게 된 픽셀이 주변 영역과 얼마나 다른지를 결정합니다. 노이즈가 발생하지 않도록 하려면 2~20의 정수 값을 사용해 보십시오. </li>
     <li><strong>적용 대상</strong>  - 선명하게 하기 취소가 각 색상이나 밝기에 적용되는지 여부를 결정합니다.</li>
    </ul>
    <div>
      선명하게 하기는
     <a href="https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html#dynamic-media">Experience Manager Dynamic Media에 이미지 선명하게 하기 사용</a> 비디오, <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/using/master-files/sharpening-image.html#master-files">이미지 선명하게 하기 온라인 도움말 항목 및 <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/assets/s7_sharpening_images.pdf">Dynamic Media Classic에서 이미지 선명하게 하기 위한 우수 사례</a> 다운로드 가능한 PDF입니다.</a>
    </div> </td>
  </tr>
  <tr>
   <td><strong>리샘플링 모드</strong></td>
   <td><strong>재샘플링 모드</strong> 옵션을 선택합니다. 이러한 옵션은 이미지를 다운샘플링할 때 이미지를 선명하게 합니다.
    <ul>
     <li><strong>Bi-Linear</strong>  - 가장 빠른 재샘플링 방법입니다. 일부 앨리어싱 가공물들은 눈에 띄습니다.</li>
     <li><strong>Bi-Cubic</strong>  - CPU 사용을 증가시키지만 앨리어싱 가공물이 덜 눈에 띄도록 더 선명한 이미지를 생성합니다.</li>
     <li><strong>Sharp2</strong>  - Bi-Cubic보다 약간 더 선명한 결과를 생성할 수 있지만 CPU 비용이 훨씬 더 높습니다.</li>
     <li><strong>Bi-Sharp</strong>  - 이미지 크기를 줄이기 위해 Photoshop 기본 반응기를  <strong>선택합니다. 이 분석기는 쌍입방 </strong> 공유인 Adobe Photoshop입니다.</li>
     <li><strong>각 </strong> 색상 및  <strong>밝기</strong>  - 각 방법은 색상 또는 밝기를 기반으로 할 수 있습니다. 기본적으로 각 색상</strong>이 선택됩니다.<strong></strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>인쇄 해상도</strong></td>
   <td>이 이미지를 인쇄할 해상도를 선택하십시오. 기본값은 72픽셀입니다.</td>
  </tr>
  <tr>
   <td><strong>이미지 수정자</strong></td>
   <td><p>UI에서 사용할 수 있는 일반적인 이미지 설정 외에 Dynamic Media에서는 <strong>이미지 수정자</strong> 필드에서 지정할 수 있는 다양한 고급 이미지 수정 사항을 지원합니다. 이러한 매개 변수는 <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/syntax-and-features/image-serving-http/c-command-overview.html">이미지 서버 프로토콜 명령 참조</a>에 정의되어 있습니다.</p> <p>중요 사항: API에 나열된 다음 기능은 지원되지 않습니다.</p>
    <ul>
     <li>기본 템플릿 및 텍스트 렌더링 명령: <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> 및 <code>textPs=</code></li>
     <li>로컬라이제이션 명령: <code>locale=</code> 및 <code>req=xlate</code></li>
     <li><code>req=set</code> 는 일반적인 용도로 사용할 수 없습니다.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>비핵심 Dynamic Media 서비스: SVG, 이미지 렌더링 및 Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### 이미지 수정자를 사용하여 이미지 사전 설정 옵션을 정의합니다 {#defining-image-preset-options-with-image-modifiers}

기본 및 고급 탭에서 사용할 수 있는 옵션 외에도 이미지 사전 설정을 정의할 때 더 많은 옵션을 제공하는 이미지 수정자를 정의할 수 있습니다. 이미지 렌더링은 Dynamic Media 이미지 렌더링 API를 사용하며, [HTTP 프로토콜 참조](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-rendering-api/http-protocol-reference/c-ir-introduction.html#image-rendering-api)에 자세히 정의되어 있습니다.

다음은 이미지 수정자로 수행할 수 있는 작업의 몇 가지 기본 예입니다.

>[!NOTE]
>
>일부 이미지 수정자 [는 Experience Manager](#advanced-tab-options)에 사용할 수 없습니다.

* [op_invert](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert.html)  - 음수 이미지 효과를 위해 각 색상 구성 요소를 반전합니다.

   ```xml
   &op_invert=1
   ```

   ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_blur](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur.html)  - 이미지에 흐림 필터를 적용합니다.

   ```xml
   &op_blur=7
   ```

   ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* 결합된 명령 - op_blur 및 op-invert

   ```xml
   &op_invert=1&op_blur=7
   ```

   ![chlimage_1-80](assets/chlimage_1-501.png)

* [op_brightness](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness.html)  - 밝기를 줄이거나 늘립니다.

   ```xml
   &op_brightness=58
   ```

   ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac.html)  - 이미지 불투명도를 조정합니다. 전경 불투명도를 줄일 수 있습니다.

   ```xml
   opac=29
   ```

   ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

### 이미지 사전 설정 편집 {#modifying-image-presets}

1. Experience Manager에서 Experience Manager 로고를 선택하여 전역 탐색 콘솔에 액세스한 다음 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 이미지 사전 설정]**&#x200B;으로 이동합니다.

   ![6_5_image사전 설정-편집 사전 설정](assets/6_5_imagepreset-editpreset.png)

1. 사전 설정을 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 선택합니다. **[!UICONTROL 이미지 사전 설정 편집]** 창이 열립니다.
1. 변경 작업을 수행하고 **[!UICONTROL 저장]**&#x200B;을 선택하여 변경 내용을 저장하거나 **[!UICONTROL 취소]**&#x200B;를 선택하여 변경 내용을 취소합니다.

### 이미지 사전 설정 게시 {#publishing-image-presets}

이미지 사전 설정이 자동으로 게시됩니다.

### 이미지 사전 설정 삭제 {#deleting-image-presets}

1. Experience Manager에서 Experience Manager 로고를 선택하여 전역 탐색 콘솔에 액세스하고 도구 아이콘을 선택합니다.
1. **[!UICONTROL 자산]** > **[!UICONTROL 이미지 사전 설정]**&#x200B;으로 이동합니다.
1. 사전 설정을 선택한 다음 **[!UICONTROL 삭제]**&#x200B;를 선택합니다. Dynamic Media에서 삭제를 확인합니다. **[!UICONTROL 삭제]**&#x200B;를 선택하여 **[!UICONTROL 취소]**&#x200B;를 선택하거나 이미지 사전 설정으로 돌아갑니다.
