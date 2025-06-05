---
title: ' [!DNL the Content Hub]에서 Assets 공유'
description: ' [!DNL the Content Hub]에서 Assets 공유'
role: User
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 0e66b355d09e2fd2c4c8a5ddacc9b2d033b41bf2
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 17%

---

# Content Hub에서 자산 공유 {#search-assets-as-a-link}

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

![자산 배너 이미지 공유](assets/share-assets-banner.png)

>[!AVAILABILITY]
>
>Content Hub 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE Content Hub 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

선택한 에셋에 대한 링크를 만들어 다른 사용자와 쉽게 공유할 수 있습니다. 승인된 [!DNL Content Hub] 사용자로서 [!DNL Content Hub] 환경에서 사용 가능한 자산을 하나 이상 선택하고 링크를 생성한 후 다른 개인 또는 공용 사용자에게 보냅니다.

## 사전 요구 사항 {#prerequisites}

[Content Hub 사용자](deploy-content-hub.md#onboard-content-hub-users)는 선택한 에셋에 대한 링크를 만들어 다른 사용자와 공유할 수 있습니다.

## 자산 공유 {#share-assets}

하나 이상의 에셋을 개인 또는 공용 사용자와 공유하려면 다음 단계를 수행하십시오.
1. [!DNL Content Hub] 홈 페이지로 이동하여 자산을 하나 이상 선택하고 ![공유](/help/assets/assets/share.svg) **[!UICONTROL 공유]**&#x200B;를 클릭하여 **[!UICONTROL 자산 공유]** 대화 상자에 선택한 단일 자산 또는 여러 자산 목록을 표시합니다.
![컬렉션](/help/assets/assets/Smock_Collection_18_N.svg) **[!UICONTROL 컬렉션]**&#x200B;에서 사용할 수 있는 자산을 선택하고 공유할 수도 있습니다.
1. 자산을 보거나 **[!UICONTROL 자산 공유]** 대화 상자에서 사용할 수 있는 자산 목록을 검토하십시오. 목록에서 자산 선택을 취소하려면 자산 옆에 있는 ![선택 취소](/help/assets/assets/Close.svg)를 클릭합니다.
1. **[!UICONTROL 만료 기간]**&#x200B;을 선택하고 **[!UICONTROL 개인 링크 생성]**&#x200B;을 클릭하여 개인 사용자와 공유할 링크를 생성합니다. 개인 사용자가 [!DNL Content Hub] 환경에 로그인하여 공유 에셋 페이지에 액세스합니다.
   ![비공개 및 공개 링크](/help/assets/assets/private-and-public-link.png)
**[!UICONTROL 공개 링크]** 토글을 활성화하고 **[!UICONTROL 만료 기간]**&#x200B;을 선택한 다음 **[!UICONTROL 공개 링크 생성]**&#x200B;을 클릭하여 공개 사용자와 공유할 링크를 생성합니다. 게스트로 공용 사용자는 [!DNL Content Hub]에 로그인하지 않고 공유 에셋 페이지에 액세스합니다.
   ![비공개 및 공개 링크](/help/assets/assets/public-and-private-link.png)

   >[!NOTE]
   > 
   > [구성 페이지에서 공개 링크 공유를 사용하도록 설정](/help/assets/configure-content-hub-ui-options.md#enable-public-link-sharing)하여 **[!UICONTROL 자산 공유]** 대화 상자에서 **[!UICONTROL 공개 링크]** 토글을 표시합니다.

## 미리보기 페이지에서 에셋 공유 {#share-asset-from-preview-page}

에셋을 미리 보는 동안 공유하려면 다음 단계를 수행하십시오.

1. [!DNL Content Hub] 홈 페이지로 이동하고 자산 미리 보기를 클릭하여 자산을 미리 보고 대화 상자의 오른쪽 창에 메뉴 옵션을 표시합니다.
1. ![공유](/help/assets/assets/share.svg)를 선택하여 **[!UICONTROL 공유]** 패널을 표시합니다.
   자산을 미리 보는 동안 ![자산 공유](/help/assets/assets/share-assets-from-share-panel.png)
1. [에셋 공유](#share-assets) 섹션의 3단계를 수행하여 이 **[!UICONTROL 공유]** 패널에서 에셋 링크(비공개 또는 공개)를 생성하고 공유하십시오.

## 공유 자산에 액세스 {#access-shared-assets}

링크를 통해 공유 에셋 페이지에 액세스하고 다음을 수행합니다.

* 하나 이상의 에셋을 선택하고 ![다운로드](/help/assets/assets/download-icon.svg) **[!UICONTROL 다운로드]**&#x200B;를 클릭하여 사용 가능한 다운로드 옵션에서 **[!UICONTROL 원본]**, **[!UICONTROL 정적]** 또는 두 표현물을 모두 선택합니다.
  ![](/help/assets/assets/download-shared-assets.png)
* 에셋의 메타데이터를 보려면 에셋 썸네일을 클릭합니다.
* 공유 에셋 페이지([개인 링크를 통해 액세스](#share-assets))에서 에셋 썸네일을 클릭하고 ![다운로드](/help/assets/assets/download-icon.svg)를 선택하여 **[!UICONTROL 다운로드]** 패널에서 에셋의 사용 가능한 동적 렌디션을 선택하고 확인합니다.
  ![](/help/assets/assets/download-renditions-shared-assets-page.png)





