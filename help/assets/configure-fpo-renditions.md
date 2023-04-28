---
title: Adobe InDesign에 대한 배치 전용 표현물 생성
description: Experience Manager Assets 워크플로우 및 ImageMagick를 사용하여 신규 및 기존 자산의 FPO 변환을 생성합니다.
contentOwner: Vishabh Gupta
role: Admin
feature: Renditions
exl-id: 869c1c34-6287-4d62-bb7a-aa4df580ac0e
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 4%

---

# Adobe InDesign에 대한 배치 전용 표현물 생성 {#fpo-renditions}

Experience Manager에서 Adobe InDesign 문서로 대규모 자산을 배치하는 경우 크리에이티브 전문가가 해당 자산이 끝나면 상당한 시간을 기다려야 합니다 [자산 배치](https://helpx.adobe.com/indesign/using/placing-graphics.html). 한편 InDesign 사용이 차단되었습니다. 따라서 크리에이티브 플로우가 중단되고 사용자 경험에 부정적인 영향을 줍니다. Adobe을 사용하면 InDesign 문서에 작은 크기의 렌디션을 일시적으로 배치할 수 있습니다. 최종 출력이 필요한 경우(예: 인쇄 및 게시 워크플로우) 원래 전체 해상도 자산은 임시 변환을 백그라운드로 대체합니다. 백그라운드에서 이러한 비동기 업데이트를 통해 디자인 프로세스의 속도를 높여 생산성을 높이고 크리에이티브 프로세스를 방해하지 않습니다.

자산은 배치에만 사용되는 표현물(FPO)을 제공합니다. 이러한 FPO 변환은 파일 크기가 작지만 동일한 종횡비입니다. 자산에 FPO 변환을 사용할 수 없는 경우 Adobe InDesign에서는 대신 원본 자산을 사용합니다. 이 대체 메커니즘을 사용하면 크리에이티브 워크플로우가 중단 없이 진행됩니다.

Experience Manager은 as a Cloud Service 클라우드 기반의 자산 처리 기능을 제공하여 FPO 변환을 생성합니다. 렌디션 생성을 위해 자산 마이크로서비스 사용. 새로 업로드한 자산과 Experience Manager에 있는 자산의 렌디션 생성을 구성할 수 있습니다.

다음은 FPO 변환을 생성하는 단계입니다.

1. [처리 프로필 만들기](#create-processing-profile).

1. 이 프로필을 사용할 Experience Manager 구성 [새 자산 처리](#generate-renditions-of-new-assets).
1. 프로필을 사용하여 다음 작업을 수행합니다 [기존 자산 처리](#generate-renditions-of-existing-assets).

## 처리 프로필 만들기 {#create-processing-profile}

FPO 변환을 생성하려면 다음을 생성합니다 **[!UICONTROL 처리 프로필]**. 프로필은 클라우드 기반의 자산 마이크로서비스를 사용하여 처리합니다. 자세한 내용은 [자산 마이크로서비스용 처리 프로필 만들기](asset-microservices-configure-and-use.md).

선택 **[!UICONTROL FPO 표현물 만들기]** FPO 변환을 생성합니다. 원할 경우 **[!UICONTROL 새로 추가]** 다른 변환 설정을 동일한 프로필에 추가하려면

![create-processing-profile-fpo-renditions](assets/create-processing-profile-fpo-renditions.png)

## 새 자산의 표현물 생성 {#generate-renditions-of-new-assets}

새 자산의 FPO 표현물을 생성하려면 **[!UICONTROL 처리 프로필]** 폴더 속성의 폴더로 이동합니다. 폴더의 속성 페이지에서 **[!UICONTROL 자산 처리]** 탭에서 을 선택합니다 **[!UICONTROL FPO 프로필]** 로서의 **[!UICONTROL 처리 프로필]**, 그리고 변경 사항을 저장합니다. 폴더에 업로드된 모든 새 자산은 이 프로필을 사용하여 처리됩니다.

![add-fpo-rendition](assets/add-fpo-rendition.png)


## 기존 자산의 표현물 생성 {#generate-renditions-of-existing-assets}

표현물을 생성하려면 자산을 선택하고 다음 단계를 수행합니다.

![fpo-existing-asset-reprocess](assets/fpo-existing-asset-reprocess.gif)


## FPO 표현물 보기 {#view-fpo-renditions}

워크플로우가 완료된 후 생성된 FPO 표현물을 확인할 수 있습니다. Experience Manager Assets 사용자 인터페이스에서 자산을 클릭하여 큰 미리 보기를 엽니다. 왼쪽 레일을 열고 을 선택합니다. **[!UICONTROL 표현물]**. 또는 키보드 단축키를 사용합니다 `Alt + 3` 미리 보기가 열려 있을 때.

클릭 **[!UICONTROL FPO 표현물]** 미리 보기를 로드하려면 다음을 수행하십시오. 선택적으로 변환을 마우스 오른쪽 단추로 클릭하고 파일 시스템에 저장할 수 있습니다. 왼쪽 레일에서 사용 가능한 렌디션을 확인합니다.

![rendition_list](assets/list-renditions.png)

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)
