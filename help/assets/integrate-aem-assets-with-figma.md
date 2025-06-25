---
title: ' [!DNL AEM Assets] 을(를)  [!DNL Figma]과(와) 통합합니다.'
description: ' [!DNL Figma] 디자인 워크플로우에서 조직의 자산에 액세스하고 사용하기 위해  [!DNL AEM Assets] 을(를)  [!DNL Figma] 과(와) 통합하는 방법을 알아봅니다.'
hide: false
role: User
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: 41fc6cc1c852c25215a804c2d1f9c5872a46e0a4
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 10%

---

# [!DNL AEM Assets]과(와) [!DNL Figma] 통합{#integrate-aem-assets-with-figma}

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

[!DNL AEM Assets]은(는) 기본적으로 [!DNL Figma]과(와) 통합되어 디자이너가 [!DNL Figma] 사용자 인터페이스 내에서 [!DNL AEM Assets]에 저장된 자산에 직접 액세스할 수 있습니다. [!DNL AEM Assets]에서 관리되는 콘텐츠를 [!DNL Figma] 캔버스에 배치한 다음 새 콘텐츠 또는 편집된 콘텐츠를 [!DNL AEM Assets] 저장소에 저장할 수 있습니다.

## 시작하기에 앞서{#prerequisites-for-aem-assets-and-figma-integration}

* 필요한 최소 AEM 릴리스 버전은 `19149`입니다.

* [!DNL AEM Assets]을(를) [!DNL Figma]과(와) 통합하려면 유효한 [!DNL AEM Assets] 및 [!DNL Figma] 라이선스가 있어야 합니다.

## [!UICONTROL Adobe Experience Manager(AEM) Assets 커넥터 액세스]{#access-aem-assets-connector}

다음 단계를 실행하여 [!UICONTROL Adobe Experience Manager(AEM) Assets 커넥터에 액세스합니다].

1. [!DNL Figma] 홈 페이지의 캔버스 아래쪽에 있는 도구 모음에서 **[!UICONTROL 작업]**&#x200B;을 클릭하고 대화 상자에서 사용할 수 있는 검색 막대에서 [!DNL Adobe Experience Manager (AEM) Assets Connector]을(를) 검색합니다.
1. [!DNL Adobe Experience Manager (AEM) Assets Connector] 패널을 표시하려면 [!DNL Adobe Experience Manager (AEM) Assets Connector]을(를) 선택하십시오. 이 패널을 사용하여 [에셋을  [!DNL Figma] 캔버스](#import-aem-assets-into-figma-workflow)(으)로 가져오기 [!DNL AEM] 합니다.
   ![작업](/help/assets/assets/actions-on-figma.png)
또는 [!DNL Figma] 커뮤니티에서 사용 가능한 [[!DNL Adobe Experience Manager (AEM) Assets Connector]](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector)에 액세스하여 **[!UICONTROL 여는 위치...]**&#x200B;를 클릭하고, 최근 파일을 선택하거나 새 파일을 만든 다음 **[!UICONTROL 실행]**&#x200B;을 클릭하여 [!DNL Adobe Experience Manager (AEM) Assets Connector] 패널에 액세스합니다.
   ![plugin-page-on-figma-community](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [!DNL AEM] 환경에 로그인한 후 **[!UICONTROL 네트워크 오류]** 메시지가 표시되면 [Adobe 지원에 문의](https://helpx.adobe.com/kr/contact.html)하십시오.

## [!DNL AEM]개의 자산을 [!DNL Figma] 캔버스로 가져오기{#import-aem-assets-into-figma-workflow}

[!DNL Figma] 디자인 인터페이스에서 [Adobe Experience Manager(AEM) Assets 커넥터] 패널(#access-aem-assets-connector)에 액세스하고 다음을 수행합니다.

1. [!UICONTROL Adobe Experience Manager(AEM) Assets 커넥터] 패널에서 자산을 검색합니다. 자세한 내용은 [자산 선택기 사용](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector)을 참조하세요.

1. 자산을 캔버스로 드래그 앤 드롭하거나 자산을 선택하고 **[!UICONTROL 선택]**&#x200B;을 클릭하여 자산을 캔버스로 가져옵니다.

1. 폴더 경로에서 ![세 점](/help/assets/assets/three-dots.svg)을 클릭하여 현재 계층의 모든 상위 및 하위 폴더를 표시합니다. 해당 위치로 이동할 폴더를 선택하십시오.
   ![세 점](/help/assets/assets/assets-folder-structure.png)

Figma 디자인이 준비되면 [자산을 AEM Assets 저장소로 내보내기](#export-figma-design-to-aem-assets-folder)할 수 있습니다.

## 자산을 [!DNL AEM Assets] 리포지토리로 내보내기{#export-figma-design-to-aem-assets-folder}

[!DNL Figma] 디자인 인터페이스에서 [Adobe Experience Manager(AEM) Assets 커넥터] 패널(#access-aem-assets-connector)에 액세스하고 다음 단계를 실행하여 디자인을 [!DNL AEM Assets] 리포지토리로 내보냅니다.

1. [!DNL Figma] 디자인을 저장할 대상 폴더로 이동합니다. 이미 폴더에 있는 경우 폴더 경로에서 추가 옵션(![점 세 개](/help/assets/assets/three-dots.svg))을 클릭하여 다른 대상 폴더를 선택합니다.
1. 선택 사항: 캔버스에서 에셋을 그룹화하여 폴더에서 업로드할 단일 단위로 선택합니다.
1. ![파일 업로드](/help/assets/assets/upload-icon.svg) **[!UICONTROL 업로드]**&#x200B;를 클릭하여 **[!UICONTROL 자산 업로드]** 대화 상자를 표시합니다.
1. 대화 상자에서 파일 이름을 지정하고 파일 형식을 선택한 다음 **[!UICONTROL 선택한 항목]** 또는 **[!UICONTROL 페이지]**&#x200B;를 선택하고 **[!UICONTROL 업로드]**&#x200B;를 클릭하여 선택한 에셋 또는 전체 디자인을 대상 폴더에 업로드합니다.
   ![그림 디자인 업로드](/help/assets/assets/upload-figma-design.png)

## 중요 참고 사항{#Limitations-of-using-aem-assets-into-figma}

이 통합에는 현재 다음과 같은 제한 사항이 있습니다.

* [!DNL AEM] 자산을 Figma로 가져오는 경우 지원되는 형식은 **JPEG**, **PNG**&#x200B;입니다.
* [!DNL Figma]에서 [!DNL AEM Assets]&#x200B;(으)로 디자인을 내보내는 경우 지원되는 형식은 **PNG**, **PDF**, **JPG**, **SVG**&#x200B;입니다.

