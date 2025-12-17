---
title: ' [!DNL AEM Assets] 을(를)  [!DNL Figma]과(와) 통합합니다.'
description: ' [!DNL AEM Assets] 디자인 워크플로우에서 조직의 자산에 액세스하고 사용하기 위해  [!DNL Figma] 을(를)  [!DNL Figma] 과(와) 통합하는 방법을 알아봅니다.'
hide: false
role: User
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: a9c1f5472092b3b9fa7a5e5570feb92f32e9ef6c
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---


# [!DNL AEM Assets]과(와) [!DNL Figma] 통합{#integrate-aem-assets-with-figma}

[!DNL AEM Assets]은(는) 기본적으로 [!DNL Figma]과(와) 통합되어 디자이너가 [!DNL AEM Assets] 사용자 인터페이스 내에서 [!DNL Figma]에 저장된 자산에 직접 액세스할 수 있습니다. [!DNL AEM Assets]에서 관리되는 콘텐츠를 [!DNL Figma] 캔버스에 배치한 다음 새 콘텐츠 또는 편집된 콘텐츠를 [!DNL AEM Assets] 저장소에 저장할 수 있습니다.

## 시작하기에 앞서{#prerequisites-for-aem-assets-and-figma-integration}

* 필요한 최소 AEM 릴리스 버전은 `19149`입니다.

* [!DNL AEM Assets]을(를) [!DNL Figma]과(와) 통합하려면 유효한 [!DNL AEM Assets] 및 [!DNL Figma] 라이선스가 있어야 합니다.

## 지원되는 파일 형식 {#supported-file-formats-integration-figma}


* [!DNL AEM] 에셋을 Figma로 가져오는 경우 지원되는 형식은 이미지 에셋(JPEG, PNG), 비디오 파일(MP4, MOV, WebM), 애니메이션 파일(GIF) 및 벡터 파일(SVG)입니다.
* [!DNL Figma]에서 [!DNL AEM Assets]&#x200B;(으)로 디자인을 내보내는 경우 지원되는 형식은 **PNG**, **PDF**, **JPG**, **SVG**&#x200B;입니다.

## [!UICONTROL Adobe Experience Manager(AEM) Assets 커넥터 액세스]{#access-aem-assets-connector}

다음 단계를 실행하여 [!UICONTROL Adobe Experience Manager(AEM) Assets 커넥터에 액세스합니다].

1. [!DNL Figma] 홈 페이지의 캔버스 아래쪽에 있는 도구 모음에서 **[!UICONTROL 작업]**&#x200B;을 클릭하고 대화 상자에서 사용할 수 있는 검색 막대에서 [!DNL Adobe Experience Manager (AEM) Assets Connector]을(를) 검색합니다.
1. [!DNL Adobe Experience Manager (AEM) Assets Connector] 패널을 표시하려면 [!DNL Adobe Experience Manager (AEM) Assets Connector]을(를) 선택하십시오. 이 패널을 사용하여 [에셋을  [!DNL AEM] 캔버스 [!DNL Figma] (으)로 가져오기](#import-aem-assets-into-figma-workflow)합니다.
   ![작업](/help/assets/assets/actions-on-figma.png)
또는 [[!DNL Adobe Experience Manager (AEM) Assets Connector] 커뮤니티에서 사용 가능한 ](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector)[!DNL Figma]에 액세스하여 **[!UICONTROL 여는 위치...]**&#x200B;를 클릭하고, 최근 파일을 선택하거나 새 파일을 만든 다음 **[!UICONTROL 실행]**&#x200B;을 클릭하여 [!DNL Adobe Experience Manager (AEM) Assets Connector] 패널에 액세스합니다.
   ![plugin-page-on-figma-community](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [ 환경에 로그인한 후 ](https://helpx.adobe.com/contact.html)네트워크 오류&#x200B;**[!UICONTROL 메시지가 표시되면]** Adobe 지원에 문의[!DNL AEM]하십시오.

## [!DNL AEM]개의 자산을 [!DNL Figma] 캔버스로 가져오기{#import-aem-assets-into-figma-workflow}

[ 디자인 인터페이스에서 [!UICONTROL Adobe Experience Manager(AEM) Assets 커넥터] 패널](#access-aem-assets-connector)에 액세스하고 다음을 수행합니다.[!DNL Figma]

1. [!UICONTROL Adobe Experience Manager(AEM) Assets 커넥터] 패널에서 자산을 검색합니다. 자세한 내용은 [자산 선택기 사용](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector)을 참조하세요.

1. 자산을 캔버스로 드래그 앤 드롭하거나 자산을 선택하고 **[!UICONTROL 선택]**&#x200B;을 클릭하여 자산을 캔버스로 가져옵니다.

1. 폴더 경로에서 ![세 점](/help/assets/assets/three-dots.svg)을 클릭하여 현재 계층의 모든 상위 및 하위 폴더를 표시합니다. 해당 위치로 이동할 폴더를 선택하십시오.
   ![세 점](/help/assets/assets/figma-v2-plugin.png)

1. [선택 사항] **[!UICONTROL 업데이트 확인]**&#x200B;을 클릭합니다. 현재 Figure 문서에 사용된 에셋은 AEM에 있는 에셋과 비교됩니다. 모든 업데이트는 별도의 창에 나열됩니다. 업데이트된 자산을 AEM에서 Figma 문서로 가져오려면 **[!UICONTROL 업데이트]**&#x200B;를 클릭합니다.

Figma 디자인이 준비되면 [자산을 AEM Assets 저장소로 내보내기](#export-figma-design-to-aem-assets-folder)할 수 있습니다.

## 자산을 [!DNL AEM Assets] 리포지토리로 내보내기{#export-figma-design-to-aem-assets-folder}

[ 디자인 인터페이스에서 [!UICONTROL Adobe Experience Manager(AEM) Assets 커넥터] 패널](#access-aem-assets-connector)에 액세스하고 다음 단계를 실행하여 디자인을 [!DNL Figma] 리포지토리로 내보냅니다.[!DNL AEM Assets]

1. [!DNL Figma] 디자인을 저장할 대상 폴더로 이동합니다. 이미 폴더에 있는 경우 폴더 경로에서 추가 옵션(![점 세 개](/help/assets/assets/three-dots.svg))을 클릭하여 다른 대상 폴더를 선택합니다.
1. 선택 사항: 캔버스에서 에셋을 그룹화하여 폴더에서 업로드할 단일 단위로 선택합니다.
1. ![파일 업로드](/help/assets/assets/upload-icon.svg) **[!UICONTROL 업로드]**&#x200B;를 클릭하여 **[!UICONTROL 자산 업로드]** 대화 상자를 표시합니다.
1. 대화 상자에서 **[!UICONTROL 선택한 항목]** 또는 **[!UICONTROL 페이지]**&#x200B;을 선택하고, 파일 또는 페이지 이름을 지정하고, 내보내기 구성을 정의하고, **[!UICONTROL 업로드]**&#x200B;를 클릭하여 선택한 에셋 또는 전체 디자인을 대상 폴더에 업로드합니다.

   내보내기 구성은 파일 형식, 크기 및 품질로 구성됩니다. 예를 들어 JPG을 파일 형식으로 선택하는 경우 이미지 크기 조절과 품질을 정의할 수도 있습니다. 마찬가지로 PNG 를 파일 형식으로 선택하면 이미지 배율을 정의할 수도 있습니다.
   ![그림 디자인 업로드](/help/assets/assets/upload-figma-design.png)
