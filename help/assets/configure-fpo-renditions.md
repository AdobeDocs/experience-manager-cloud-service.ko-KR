---
title: Adobe InDesign에 대한 배치 전용 표현물 생성
description: Experience Manager 자산 워크플로우 및 ImageMagick를 사용하여 신규 및 기존 자산의 FPO 변환을 생성합니다.
contentOwner: Vishabh Gupta
role: Admin
feature: 표현물
exl-id: null
source-git-commit: 69f1ac34dc24f92cae47e1bfcffb39f6f3b03b7b
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Adobe InDesign에 대한 배치 전용 표현물 생성 {#fpo-renditions}

Experience Manager의 큰 자산을 Adobe InDesign 문서에 배치할 때 크리에이티브 전문가가 [자산을 배치한 후 상당한 시간을 기다려야 합니다](https://helpx.adobe.com/indesign/using/placing-graphics.html). 한편 InDesign 사용이 차단되었습니다. 따라서 크리에이티브 플로우가 중단되고 사용자 경험에 부정적인 영향을 줍니다. Adobe을 사용하면 InDesign 문서에 작은 크기의 렌디션을 일시적으로 배치할 수 있습니다. 최종 출력이 필요한 경우(예: 인쇄 및 게시 워크플로우) 원래 전체 해상도 자산은 임시 변환을 백그라운드로 대체합니다. 백그라운드에서 이러한 비동기 업데이트를 통해 디자인 프로세스의 속도를 높여 생산성을 높이고 크리에이티브 프로세스를 방해하지 않습니다.

자산은 배치에만 사용되는 표현물(FPO)을 제공합니다. 이러한 FPO 변환은 파일 크기가 작지만 동일한 종횡비입니다. 자산에 FPO 변환을 사용할 수 없는 경우 Adobe InDesign에서는 대신 원본 자산을 사용합니다. 이 대체 메커니즘을 사용하면 크리에이티브 워크플로우가 중단 없이 진행됩니다.

Experience Manager as a Cloud Service은 FPO 변환을 생성할 수 있는 클라우드 기반의 자산 처리 기능을 제공합니다. 렌디션 생성을 위해 자산 마이크로서비스 사용. 새로 업로드한 자산과 Experience Manager에 있는 자산의 렌디션 생성을 구성할 수 있습니다.

다음은 FPO 변환을 생성하는 단계입니다.
1. [처리 프로필 만들기](#create-processing-profile).
1. 이 프로필을 사용하여 새 자산 처리 [에 사용하도록 Experience Manager을 구성합니다.](#generate-renditions-of-new-assets)
1. 프로필을 사용하여 기존 자산](#generate-renditions-of-existing-assets)을 처리합니다.[

## 처리 프로필 만들기 {#create-processing-profile}

FPO 변환을 생성하려면 **[!UICONTROL 처리 프로필]**&#x200B;을 만듭니다. 프로필은 클라우드 기반의 자산 마이크로서비스를 사용하여 처리합니다. 지침은 자산 마이크로서비스용 처리 프로필 만들기](asset-microservices-configure-and-use.md)를 참조하십시오.[

FPO 변환을 생성하려면 **[!UICONTROL FPO 변환 만들기]**&#x200B;를 선택합니다. 원할 경우 **[!UICONTROL 새로 추가]**&#x200B;를 클릭하여 동일한 프로필에 다른 변환 설정을 추가합니다.

![create-processing-profile-fpo-renditions](assets/create-processing-profile-fpo-renditions.png)

## 새 자산의 표현물 생성 {#generate-renditions-of-new-assets}

새 자산의 FPO 변환을 생성하려면 **[!UICONTROL 처리 프로필]**&#x200B;을 폴더 속성의 폴더에 적용합니다. 폴더의 속성 페이지에서 **[!UICONTROL 자산 처리]** 탭을 클릭하고 **[!UICONTROL FPO 프로필]**&#x200B;을 **[!UICONTROL 처리 프로필]**&#x200B;로 선택한 다음 변경 사항을 저장합니다. 폴더에 업로드된 모든 새 자산은 이 프로필을 사용하여 처리됩니다.

![add-fpo-rendition](assets/add-fpo-rendition.png)


## 기존 자산의 표현물 생성 {#generate-renditions-of-existing-assets}

표현물을 생성하려면 자산을 선택하고 다음 단계를 수행합니다.

![fpo-existing-asset-reprocess](assets/fpo-existing-asset-reprocess.gif)


## FPO 표현물 보기 {#view-fpo-renditions}

워크플로우가 완료된 후 생성된 FPO 표현물을 확인할 수 있습니다. 자산 Experience Manager 사용자 인터페이스에서 자산을 클릭하여 큰 미리 보기를 엽니다. 왼쪽 레일을 열고 **[!UICONTROL 표현물]**&#x200B;을 선택합니다. 또는 미리 보기가 열려 있을 때 키보드 단축키 `Alt + 3` 을 사용합니다.

**[!UICONTROL FPO 표현물]**&#x200B;을 클릭하여 미리 보기를 로드합니다. 선택적으로 변환을 마우스 오른쪽 단추로 클릭하고 파일 시스템에 저장할 수 있습니다. 왼쪽 레일에서 사용 가능한 렌디션을 확인합니다.

![rendition_list](assets/list-renditions.png)
