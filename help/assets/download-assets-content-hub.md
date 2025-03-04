---
title: Content Hub에서 에셋 다운로드
description: Content Hub 포털에서 에셋을 다운로드하는 방법을 알아봅니다
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 07d533962ae2922c8a467924361fdfefc5c594eb
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 9%

---

# Content Hub에서 에셋 다운로드 {#download-assets}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 포함된 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Download assets](assets/download-asset.jpg) -->
![자산 다운로드](assets/download-asset-genstudio.jpeg)

>[!AVAILABILITY]
>
>Content Hub 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE Content Hub 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Content Hub을 사용하여 에셋을 다운로드하고 공유할 수 있습니다. Content Hub 사용자 인터페이스에는 승인된 에셋만 표시됩니다. 이러한 에셋에는 이미지, 비디오 또는 기타 디지털 콘텐츠가 포함될 수 있습니다. Content Hub은 효과적인 에셋 배포를 위해 접근성과 적응성을 향상합니다.

Content Hub을 사용하여 하나 또는 여러 에셋과 사용 가능한 렌디션을 다운로드할 수 있습니다.

Content Hub에서 사용할 수 있는 [변환 유형](#types-of-renditions)을 참조하세요.

## 에셋 및 해당 렌디션 다운로드 {#download-asset-renditions}

에셋 및 해당 렌디션을 다운로드하려면 다음 단계를 실행합니다.

1. 속성을 보려면 자산을 클릭합니다.

1. 다운로드 프로세스를 시작하려면 ![다운로드](/help/assets/assets/download-icon.svg)를 클릭하십시오. 다운로드 패널에 사용 가능한 모든 에셋 렌디션이 나열됩니다.

   >[!NOTE]
   >
   * 변환은 [구성](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) 사용자 인터페이스를 사용하여 가시성을 사용할 수 있는 경우에만 표시됩니다.
   * 에셋을 다운로드하는 동안 모든 [정적, 동적 및 스마트 자르기 렌디션](#types-of-renditions)을 다운로드할 수 있습니다.

1. 렌디션을 하나 이상 선택하고 **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다.

   ![단일 에셋 렌디션 다운로드](/help/assets/assets/download-single-asset-renditions.png)


사용 허가된 자산을 다운로드하는 경우 **[!UICONTROL 위에 언급된 약관을 읽고 동의함]**&#x200B;을 선택한 다음 **[!UICONTROL 다운로드]**&#x200B;를 클릭하세요. **[!UICONTROL 약관]**&#x200B;을 클릭하여 자산 라이선스를 볼 수도 있습니다. Assets as a Cloud Service 작성 환경을 사용하여 에셋이 승인된 경우에만 라이선스 미리보기가 표시됩니다. 자세한 내용은 [Content Hub의 사용 허가된 자산 관리](/help/assets/manage-licensed-assets-on-content-hub.md)를 참조하십시오.

>[!NOTE]
>
Open API 기능이 있는 [Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md)에 대한 액세스 권한이 있는 사용자는 동적 및 스마트 자르기 변환을 보고 다운로드할 수 있습니다.

## 여러 에셋 및 해당 렌디션 다운로드 {#download-multiple-assets-renditions}

여러 에셋 및 해당 표현물을 다운로드하려면 다음 단계를 수행하십시오.

1. 자산을 선택하고 ![다운로드](/help/assets/assets/download-icon.svg) **[!UICONTROL 다운로드]**&#x200B;를 클릭합니다. [!UICONTROL 에셋 다운로드] 화면에 선택한 에셋을 모두 나열하는 화면이 표시됩니다.
1. 다운로드를 시작하려면 **[!UICONTROL 다운로드]**&#x200B;를 클릭하여 다양한 다운로드 옵션 중에서 선택하십시오.

   * **[!UICONTROL 원본 다운로드]**: 선택한 자산을 원본 양식으로 다운로드하려면 이 옵션을 선택하십시오.
   * **정적 렌디션만 다운로드[!UICONTROL 원본 에셋을 제외한 에셋의 사용 가능한 모든 정적 렌디션을 다운로드하려면 이 옵션을 선택하십시오.]**
   * **원본 및 정적 렌디션 [!UICONTROL 다운로드]**: 선택한 에셋의 원본 및 정적 렌디션을 모두 다운로드하려면 이 옵션을 선택하십시오.

     ![여러 렌디션 다운로드](/help/assets/assets/download-multiple-renditions.png)

     >[!NOTE]
     >
     * 변환은 [구성](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) 사용자 인터페이스를 사용하여 가시성을 사용할 수 있는 경우에만 표시됩니다.
     * 여러 자산을 다운로드하는 동안에는 [정적 렌디션](#types-of-renditions)만 다운로드할 수 있습니다.

   선택한 자산 중 라이센스가 부여된 자산이 있는 경우 왼쪽 창에서 자산의 라이센스를 클릭하여 미리 보기를 확인합니다. 그러면 **[!UICONTROL 위에서 언급한 약관을 읽고 수락했습니다]**. **[!UICONTROL 다운로드]**&#x200B;를 클릭할 수 있습니다. Assets as a Cloud Service 작성 환경을 사용하여 에셋이 승인된 경우에만 라이선스 미리보기가 표시됩니다. 자세한 내용은 [Content Hub의 사용 허가된 자산 관리](/help/assets/manage-licensed-assets-on-content-hub.md)를 참조하십시오.

   <!--![download-multiple-license](/help/assets/assets/download-multiple-license.png)-->

<!--1. On the Content Hub homepage, select the asset and click **Download**. The **Download assets** dialog box displays a license or list of licenses associated with the selected assets in the left pane. 
1. Click a license in the left pane to see its PDF in the middle pane and the associated assets with it in the right pane. The license PDF preview is displayed only if the license is approved in your Assets as a Cloud Service environment. [Approve the license PDFs](/help/assets/approve-assets-content-hub.md) of the selected assets to see their previews.
1. Optional: Click ![remove-icon](/help/assets/assets/remove-icon.svg) to remove a license from the dialog box.
1. Select **I have read and accept all the terms and conditions mentioned above.** 
1. Click **Download** to download the selected assets.-->

<!---This dialog box displays the list of licenses associated with the selected assets in the left pane. Select a license to preview its terms and conditions (in pdf format) in the middle pane and the preview of the associated assets to the license in the right. Reviewed licenses are highlighted in light blue.


The dialog box that displays depends on whether the download list includes expired assets or only non-expired assets. <br/>
**Download expired assets dialog box:** This dialog box displays the expired assets' preview along with their expiry date in the left pane. The expired assets' count out of total selected displays in the right pane. Click **Proceed with all assets** to download expired assets with other assets (if present). The Download assets dialog box displays. See the [Download assets dialog box](#Download-asset-dialog-box) to proceed further.
    
    >[!NOTE]
    >
    >[Enable the download option for expired assets](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub) to download them. Only expired assets that have enabled downloading are available for download.

   <a id="Download-asset-dialog-box"></a> **Download assets dialog box:** This dialog box displays the list of licenses associated with the selected assets in the left pane. Select a license to preview its terms and conditions (in pdf format) in the middle pane and the associated assets' preview and their count in the right pane. Reviewed licenses are highlighted in light blue.

    >[!NOTE]
    >
    > The **Download Asset dialog box** previews licensing terms and conditions only for approved licenses. [Approve the assets' licenses](/help/assets/approve-assets-content-hub.md) before downloading them to preview their licensing terms in the **Download Asset dialog box**.

1. Click  ![remove-icon](/help/assets/assets/remove-icon.svg) to remove a license from the download dialog box. 

1. Accept the terms and conditions and then click **Download** to download assets associated with the available licenses in the left pane.-->
<!--![download-multiple-license](/help/assets/assets/download-multiple-license.png)-->

<!---
### Download non-licensed Assets {#download-non-licensed-assets}

 To download non-licensed assets, select the assets and click ![download](/help/assets/assets/download-icon.svg) from the top rail.-->


## 표현물 유형 {#types-of-renditions}

에셋 렌디션은 에셋의 원본 파일을 다르게 표현한 것입니다. 여기에는 썸네일, 웹 또는 모바일용으로 최적화된 버전, 워터마크가 적용되거나 DRM으로 보호된 파일 또는 스마트 자르기와 같은 동적 요소가 포함될 수 있습니다. 원본 파일 형식과 일치시킬 필요가 없으며, 대신 다양한 사용 사례에서 에셋을 나타내는 역할을 합니다.

[Experience Manager Assets에서 렌디션 보기 및 관리](/help/assets/renditions.md)에 대해 자세히 알아보세요.

[!DNL Experience Manager Assets]은(는) 다음 유형의 변환을 지원합니다.

* [정적 렌디션](/help/assets/renditions.md#static-renditions): 정적 렌디션은 디지털 에셋의 미리 만들어진 버전으로, 일반적으로 에셋 수집 또는 수정 중에 생성됩니다. 웹 썸네일, 응답형 디자인을 위한 모바일 친화적 형식 또는 인쇄용 고해상도 파일과 같은 특정 용도 및 플랫폼에 최적화되어 간소화되고 일관된 환경을 제공합니다.

* [동적 변환](/help/assets/renditions.md#dynamic-renditions): 동적 변환은 다양한 장치 해상도에 대한 이미지 크기 조정 또는 다양한 종횡비에 맞는 자르기 등 다양한 작업을 수행하는 자산의 실시간 사용자 지정 버전입니다. 이러한 렌디션을 사용하면 더 넓은 요구 사항에 맞게 개인화되고 최적화된 경험을 제공할 수 있습니다. 자산의 동적 변환이 [!DNL Adobe Experience Manager Assets] 작성 환경에서 만들어집니다.

* [스마트 자르기](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles): 스마트 자르기 프로세스는 자르기 프로세스 중 에셋의 필수 부분에만 중점을 둡니다. Dynamic media 스마트 자르기 for은 Adobe Sensei에서 제공하는 인공 지능을 활용하여 관심 영역을 추적하므로, 모든 화면 크기에서 에셋이 최고처럼 보이도록 할 수 있습니다. [!DNL Adobe Experience Manager] 스마트 자르기에 제목과 함께 에셋 표현물의 너비와 높이가 표시됩니다. 자세한 내용은 [AEM Assets Dynamic Media와 함께 스마트 자르기 사용](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use)을 참조하세요.

  ![렌디션 유형](/help/assets/assets/renditions-types.png)


>[!NOTE]
> 
* Dynamic Media 계정에 조기 액세스하려면 [Adobe 고객 지원 사례를 만들어 제출](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html)하십시오.
* [Dynamic Media Open API 서비스](/help/assets/dynamic-media-open-apis-overview.md)에서 새로 온보딩된 고객은 승인을 위해 기존 이미지 사전 설정을 수정해야 합니다.



