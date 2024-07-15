---
title: 이미지 편집
description: ' [!DNL Adobe Express] 기반 옵션을 사용하여 이미지를 편집하고 업데이트된 이미지를 버전으로 저장합니다.'
role: User
exl-id: cfc4c7b7-da8c-4902-9935-0e3d4388b975
feature: Best Practices, Interactive Images, Smart Crop, Smart Imaging
source-git-commit: 23b43f22b62451c9d0a5460999fcd43479438d7e
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 79%

---

# [!DNL Assets view]에서 이미지 편집 {#edit-images-in-assets-view}

Assets 보기를 사용하면 크기 조정, 배경 제거, 자르기 및 JPEG 및 PNG 형식 간 변환 등 기본 이미지 편집을 사용할 수 있습니다. 또한 Adobe Express와의 통합을 통해 고급 편집을 사용할 수도 있습니다. 이미지를 편집한 후 새 이미지를 새 버전으로 저장할 수 있습니다. 필요한 경우 버전 관리를 통해 나중에 원본 자산으로 되돌릴 수 있습니다. 이미지를 편집하려면 [미리보기를 열고](https://experienceleague.adobe.com/ko/docs/experience-manager-assets-essentials/help/navigate-view#preview-assets) **이미지 편집**&#x200B;을 클릭합니다.

>[!NOTE]
>
>[!DNL Adobe Express]을 사용하여 PNG 및 JPEG 파일 형식의 이미지를 편집할 수 있습니다.

<!--The editing actions that are available are Spot healing, Crop and straighten, Resize image, and Adjust image.-->

## 이미지 편집 {#edit-image}

[Assets 보기](https://experience.adobe.com/#/assets) 링크를 사용하고 올바른 저장소를 선택하여 Assets 보기에 도달합니다. 액세스 권한을 받으려면 귀사의 관리자에게 문의하십시오.
추가 참조 정보는 [Adobe Experience Manager Assets 보기 사용 시작](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view), [Assets 보기 사용자 인터페이스 이해](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/navigate-assets-view#understand-interface-navigation) 및 [Assets 보기 사용 사례](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view#use-cases)를 참조하세요.
<!--
>[!CONTEXTUALHELP]
>id="assets_express_integration"
>title="Adobe Express Integration"
>abstract="Easy and intuitive image-editing tools powered by Adobe Express available directly within AEM Assets to increase content reuse and accelerate content velocity."-->

### Adobe Express을 사용하여 Assets 보기에서 이미지 편집 {#edit-image-on-assets-view-using-adobe-express}

Assets 보기에 도착한 후 **Assets**&#x200B;을(를) 클릭하고 이미지를 선택한 다음 상단 레일에서 **편집**&#x200B;을(를) 클릭합니다. 새 화면에 크기 조정, 배경 제거, 자르기, JPEG와 PNG 포맷 간 변환 등 사용 가능한 편집 옵션이 표시됩니다.

#### 이미지 크기 조정 {#resize-image-using-express}

이미지 크기를 특정 크기로 조정하는 것이 일반적인 사용 사례입니다. Assets 보기를 사용하면 특정 사진 크기에 대해 미리 계산된 새로운 해상도를 제공하여 일반적인 사진 크기에 맞게 빠르게 이미지 크기를 조정할 수 있습니다. Assets 보기를 사용하여 이미지 크기를 조정하려면 아래 단계를 따르십시오.

1. 왼쪽 창에서 **이미지 크기 조정**&#x200B;을 클릭합니다.
1. [크기 조정] 드롭다운 목록에서 적절한 소셜 미디어 플랫폼을 선택하고 표시되는 옵션에서 이미지 크기 조정을 선택합니다.
1. 필요한 경우 **이미지 크기 조정** 필드를 사용하여 이미지 크기를 조정합니다.
1. **[!UICONTROL 적용]**을 클릭하여 변경 내용을 적용합니다.
   ![Adobe Express를 사용하여 이미지 편집](assets/adobe-express-resize-image.png)

   편집한 이미지를 다운로드할 수 있습니다. 편집한 자산을 동일한 자산의 새 버전으로 저장하거나 새 자산으로 저장할 수 있습니다.
   ![Adobe Express로 이미지 저장](assets/adobe-express-resize-save.png)

#### 배경 제거 {#remove-background-using-express}

아래 설명된 몇 번의 간단한 단계를 따라 이미지에서 배경을 제거할 수 있습니다.

1. 왼쪽 창에서 **배경 제거**&#x200B;를 클릭합니다. Experience Manager Assets에 배경이 없는 이미지가 표시됩니다.
1. **[!UICONTROL 적용]**을 클릭하여 변경 내용을 적용합니다.
   ![Adobe Express로 이미지 저장](assets/adobe-express-remove-background.png)

   편집한 이미지를 다운로드할 수 있습니다. 편집한 자산을 동일한 자산의 새 버전으로 저장하거나 새 자산으로 저장할 수 있습니다.

#### 이미지 자르기 {#crop-image-using-express}

임베드된 [!DNL Adobe Express] 빠른 작업을 사용하여 이미지를 완벽한 크기로 간단하게 변환할 수 있습니다.

1. 왼쪽 창에서 **[!UICONTROL 이미지 자르기]**&#x200B;를 클릭합니다.
2. 이미지 모퉁이의 핸들을 드래그하여 원하는 자르기를 만듭니다.
3. **[!UICONTROL 적용]**을 클릭합니다.
   ![Adobe Express로 이미지 저장](assets/adobe-express-crop-image.png)
잘린 이미지를 다운로드할 수 있습니다. 편집한 자산을 동일한 자산의 새 버전으로 저장하거나 새 자산으로 저장할 수 있습니다.

#### 이미지 파일 포맷 간 변환 {#convert-image-types-using-express}

Adobe Express를 사용하여 JPEG 및 PNG 이미지 포맷 간 빠르게 변환할 수 있습니다. 다음 단계를 실행합니다.

1. 왼쪽 창에서 **JPEG를 PNG로** 또는 **PNG를 JPEG로**를 클릭합니다.
   <!--![Convert to PNG with Adobe Express](/help/using/assets/adobe-express-convert-image.png)-->
1. **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

#### 제한 사항 {#limitations-adobe-express}

* 지원되는 이미지 해상도: 차원당 최소 50픽셀, 최대 6000픽셀.

* 지원되는 최대 파일 크기: 17MB.

### 임베드된 Adobe Express 편집기에서 이미지 편집 {#edit-images-in-adobe-express-embedded-editor}

Express 권한이 있는 사용자는 Assets 보기 내에서 임베드된 Express 편집기를 사용하여 컨텐츠를 쉽게 편집하고 Adobe Firefly의 GenAI로 새 컨텐츠를 만들 수 있습니다. 이를 통해 콘텐츠 재사용이 향상되고 콘텐츠 속도가 빨라집니다. 또한 사전 정의된 요소를 사용하여 자산을 멋지게 보이게 하거나 몇 번의 클릭만으로 빠른 작업을 수행하여 이미지를 편집할 수 있습니다.
![essentials UI의 Express](/help/assets/assets/express-in-essentials-ui.jpg)
[!DNL Adobe Express] 포함된 편집기를 사용하여 이미지를 편집하려면 아래 단계를 따르십시오.

1. [AEM Assets 보기](https://experience.adobe.com/#/assets) 링크를 사용하여 AEM Assets 보기에 도달하고 올바른 리포지토리를 선택합니다.
1. **자산**&#x200B;을 클릭하고 폴더를 입력한 다음 이미지를 선택합니다.
1. **Adobe Express에서 열기**&#x200B;를 클릭합니다. Express 캔버스에서 이미지가 열립니다.
1. 이미지에 필요한 편집을 수행합니다.
1. 프로젝트에 페이지를 더 추가해야 하는 경우 **추가**&#x200B;를 클릭하고, 자산을 선택한 다음 폴더를 입력하고, 캔버스 페이지로 가져올 이미지를 선택한 다음 이미지에 필요한 편집을 수행합니다.
1. 이미지를 저장하려면 **저장**&#x200B;을 클릭합니다. 저장 대화 상자가 표시됩니다.

   >[!NOTE]
   >
   > **1. 단일 페이지의 경우**
   >
   > **버전으로 저장:** 이 기능은 단일 자산 저장만 지원합니다. 이미지를 원본 포맷을 유지한 채로 새 버전으로 내보내고 동일한 폴더에 저장하려면 이 옵션을 선택합니다.
   > **새 자산으로 저장:** 자산을 원본과 다른 포맷으로 내보내고 폴더에 새 자산으로 저장하려면 이 옵션을 선택합니다.
   >  
   > **2. 여러 페이지의 경우**
   >
   > **버전으로 저장:** 이 기능은 단일 자산 저장만 지원합니다. 여러 페이지에서 단일 페이지를 저장하려면 이 옵션을 선택하여 자산을 원래 포맷으로 원래 위치에 저장합니다.\
   > **새 자산으로 저장:** 이 옵션을 사용하면 여러 자산 또는 단일 자산을 임의의 폴더로 내보낸 후 원본 파일 포맷이나 다른 파일 포맷의 새 자산으로 저장할 수 있습니다.

1. [저장] 대화 상자에서 다음 작업을 수행합니다.
   1. **다른 이름으로 저장** 필드에 파일 이름을 입력합니다.
   1. 대상 폴더를 선택합니다.
   1. 선택 사항: 프로젝트 또는 캠페인 이름, 키워드, 채널, 시간대 및 지역과 같은 세부 정보를 입력합니다.
1. 자산을 저장하려면 **버전으로 저장** 또는 **새 자산으로 저장**&#x200B;을 클릭합니다.

#### Express Editor에서의 이미지 편집 제한 사항 {#limitations-of-editing-images-in-the-express-editor}

* 지원되는 파일 포맷: JPEG 또는 PNG.
* 지원되는 최대 파일 크기: 40 MB.
* 지원되는 폭 및 높이 범위: 50~8000픽셀.
* 소스 폴더에 최근 저장된 새 자산을 보려면 페이지를 다시 로드합니다.

### Adobe Express를 사용하여 새 자산 만들기 {#create-new-embedded-editor}

[!DNL Assets view]를 사용하여 [!DNL Adobe Express] 임베드된 편집기로 처음부터 새 템플릿을 만들 수 있습니다. [!DNL Adobe Express]를 사용하여 새 자산을 만들려면 아래 단계를 실행하십시오.

1. **[!UICONTROL 내 Workspace]**(으)로 이동한 다음 맨 위에 표시되는 Adobe Express 배너에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다. [!DNL Adobe Express] 빈 캔버스는 [!DNL Assets view] 사용자 인터페이스 내에 표시됩니다.
1. [템플릿](https://helpx.adobe.com/kr/express/using/work-with-templates.html)을 사용하여 콘텐츠를 만듭니다. 그렇지 않은 경우 **[!UICONTROL 내 항목]**&#x200B;으로 이동하여 기존의 콘텐츠를 수정합니다.
1. 편집이 완료되면 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 만든 에셋의 대상 경로를 지정하고 **[!UICONTROL 새 에셋으로 저장]**&#x200B;을 클릭합니다.

#### 제한 사항 {#limitations}

* `JPEG` 및 `PNG` 포맷 유형의 이미지만 수정할 수 있습니다.
* 자산 크기는 40MB보다 작아야 합니다.
* `PDF`, `JPEG` 또는 `PNG` 포맷에 이미지를 저장할 수 있습니다.

<!--
## Edit images using [!DNL Adobe Photoshop Express] {#edit-using-photoshop-express}

<!--
After editing an image, you can save the new image as a new version. Versioning helps you to revert to the original asset later, if needed. To edit an image, [open its preview](navigate-assets-view.md#preview-assets) and click **[!UICONTROL Edit Image]** ![edit icon](assets/do-not-localize/edit-icon.png) from the rail on the right.

![Options to edit an image](assets/edit-image2.png)

*Figure: The options to edit images are powered by [!DNL Adobe Photoshop Express].*
-->
<!--
### Touch up images {#spot-heal-images-using-photoshop-express}

If there are minor spots or small objects on an image, you can edit and remove the spots using the spot healing feature provided by Adobe Photoshop.

The brush samples the retouched area and makes the repaired pixels blend seamlessly into the rest of the image. Use a brush size that is only slightly larger than the spot you want to fix.

![Spot healing edit option](assets/edit-spot-healing.png)

<!-- 
TBD: See if we should give backlinks to PS docs for these concepts.
For more information about how Spot Healing works in Photoshop, see [retouching and repairing photos](https://helpx.adobe.com/photoshop/using/retouching-repairing-images.html). 
-->
<!-- 
### Crop and straighten images {#crop-straighten-images-using-photoshop-express}

Using the crop and straighten option that you can do basic cropping, rotate image, flip it horizontally or vertically, and crop it to dimensions suitable for popular social media websites.

To save your edits, click **[!UICONTROL Crop Image]**. After editing, you can save the new image as a version.

![Option to crop and straighten](assets/edit-crop-straighten.png)

Many default options let you crop your image to the best proportions that fit various social media profiles and posts.

### Resize image {#resize-image-using-photoshop-express}

You can view the common photo sizes in centimeters or inches to know the dimensions. By default, the resizing method retains the aspect ratio. To manually override the aspect ratio, click ![](assets/do-not-localize/lock-closed-icon.png).

Enter the dimensions and click **[!UICONTROL Resize Image]** to resize the image. Before you save the changes as a version, you can either undo all the changes done before saving by clicking [!UICONTROL Undo] or you can change the specific step in the editing process by clicking [!UICONTROL Revert].

![Options when resizing an image](assets/resize-image.png)

### Adjust image {#adjust-image-using-photoshop-express}

[!DNL Assets view] lets you adjust the color, tone, contrast, and more, with just a few clicks. Click **[!UICONTROL Adjust image]** in the edit window. The following options are available in the right sidebar:

* **Popular**: [!UICONTROL High Contrast & Detail], [!UICONTROL Desaturated Contrast], [!UICONTROL Aged Photo], [!UICONTROL B&W Soft], and [!UICONTROL B&W Sepia Tone].
* **Color**: [!UICONTROL Natural], [!UICONTROL Bright], [!UICONTROL High Contrast], [!UICONTROL High Contrast & Detail], [!UICONTROL Vivid], and [!UICONTROL Matte].
* **Creative**: [!UICONTROL Desaturated Contrast], [!UICONTROL Cool Light], [!UICONTROL Turquoise & Red], [!UICONTROL Soft Mist], [!UICONTROL Vintage Instant], [!UICONTROL Warm Contrast], [!UICONTROL Flat & Green], [!UICONTROL Red Lift Matte], [!UICONTROL Warm Shadows], and [!UICONTROL Aged Photo].
* **B&W**: [!UICONTROL B&W Landscape], [!UICONTROL B&W High Contrast], [!UICONTROL B&W Punch], [!UICONTROL B&W Low Contrast], [!UICONTROL B&W Flat], [!UICONTROL B&W Soft], [!UICONTROL B&W Infrared], [!UICONTROL B&W Selenium Tone], [!UICONTROL B&W Sepia Tone], and [!UICONTROL B&W Split Tone].
* **Vignetting**: [!UICONTROL None], [!UICONTROL Light], [!UICONTROL Medium], and [!UICONTROL Heavy].

![Adjust image by editing](assets/adjust-image.png)

<!--
TBD: Insert a video of the available social media options.
-->

### 다음 단계 {#next-steps}

* Assets 보기 사용자 인터페이스에서 사용할 수 있는 [!UICONTROL 피드백] 옵션을 사용하여 제품 피드백을 제공하십시오.

* 오른쪽 사이드바에서 사용 가능한 [!UICONTROL 이 페이지 편집], ![페이지 편집](assets/do-not-localize/edit-page.png), [!UICONTROL 문제 기록] 또는 ![GitHub 문제 생성](assets/do-not-localize/github-issue.png)을 사용하여 설명서 피드백을 제공합니다.

* [고객 지원 센터](https://experienceleague.adobe.com/?support-solution=General#support) 문의

>[!MORELIKETHIS]
>
>* [Adobe Express의 빠른 작업](https://helpx.adobe.com/kr/express/using/resize-image.html)
>* [자산의 버전 기록 보기](navigate-assets-view.md)
