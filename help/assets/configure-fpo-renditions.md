---
title: Adobe InDesign에 대한 배치 전용 렌디션 생성
description: Experience Manager Assets 워크플로 및 ImageMagick을 사용하여 새 에셋과 기존 에셋의 FPO 렌디션을 생성합니다.
contentOwner: Vishabh Gupta
role: Admin
feature: Renditions
exl-id: 869c1c34-6287-4d62-bb7a-aa4df580ac0e
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 10%

---

# Adobe InDesign에 대한 배치 전용 렌디션 생성 {#fpo-renditions}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/configure-fpo-renditions.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

Experience Manager에서 Adobe InDesign 문서로 대형 에셋을 배치할 때 크리에이티브 전문가는 [에셋을 배치](https://helpx.adobe.com/indesign/using/placing-graphics.html)한 후 상당한 시간을 기다려야 합니다. 한편, 사용자는 InDesign 사용이 차단된다. 이는 크리에이티브 흐름을 방해하고 사용자 경험에 부정적인 영향을 미칩니다. Adobe을 사용하면 InDesign 문서에 작은 크기의 렌디션을 임시로 배치할 수 있습니다. 인쇄 및 게시 워크플로와 같이 최종 출력이 필요한 경우 원본 전체 해상도 에셋이 배경의 임시 렌디션을 대체합니다. 백그라운드에서 이 비동기식 업데이트는 디자인 프로세스를 가속화하여 생산성을 높이고 크리에이티브 프로세스를 방해하지 않습니다.

Assets은 배치에만 사용되는 렌디션(FPO)을 제공합니다. 이러한 FPO 렌디션은 파일 크기는 작지만 종횡비가 동일합니다. 에셋에 FPO 렌디션을 사용할 수 없는 경우 Adobe InDesign은 원본 에셋을 대신 사용합니다. 이 대체 메커니즘을 사용하면 크리에이티브 워크플로우가 중단 없이 진행될 수 있습니다.

Experience Manager as a Cloud Service은 클라우드 기반 에셋 처리 기능을 제공하여 FFRENDITIONS를 생성합니다. 렌디션 생성에 자산 마이크로서비스 사용. 새로 업로드한 에셋과 Experience Manager에 있는 에셋의 렌디션 생성을 구성할 수 있습니다.

다음은 FPO 렌디션을 생성하는 단계입니다.

1. [처리 프로필을 만듭니다](#create-processing-profile).

1. 이 프로필을 사용하여 [새 자산을 처리](#generate-renditions-of-new-assets)하도록 Experience Manager을 구성하십시오.
1. 프로필을 사용하여 [기존 자산을 처리](#generate-renditions-of-existing-assets)합니다.

## 처리 프로필 만들기 {#create-processing-profile}

FPO 렌디션을 생성하려면 **[!UICONTROL 처리 프로필]**&#x200B;을 만드십시오. 프로필은 처리를 위해 클라우드 기반 에셋 마이크로서비스를 사용합니다. 지침은 [자산 마이크로서비스에 대한 처리 프로필 만들기](asset-microservices-configure-and-use.md)를 참조하십시오.

FPO 렌디션을 생성하려면 **[!UICONTROL FPO 렌디션 만들기]**&#x200B;를 선택하십시오. 필요한 경우 **[!UICONTROL 새로 추가]**&#x200B;를 클릭하여 동일한 프로필에 다른 렌디션 설정을 추가합니다.

![create-processing-profile-fpo-renditions](assets/create-processing-profile-fpo-renditions.png)

## 새 자산의 렌디션 생성 {#generate-renditions-of-new-assets}

새 자산의 FPO 변환을 생성하려면 폴더 속성의 폴더에 **[!UICONTROL 처리 프로필]**&#x200B;을 적용하십시오. 폴더의 속성 페이지에서 **[!UICONTROL 자산 처리]** 탭을 클릭하고 **[!UICONTROL FPO 프로필]**&#x200B;을(를) **[!UICONTROL 처리 프로필]**(으)로 선택한 다음 변경 사항을 저장합니다. 폴더에 업로드된 모든 새 에셋은 이 프로필을 사용하여 처리됩니다.

![fpo-rendition 추가](assets/add-fpo-rendition.png)


## 기존 에셋의 렌디션 생성 {#generate-renditions-of-existing-assets}

렌디션을 생성하려면 에셋을 선택하고 다음 단계를 수행합니다.

![fpo-existing-asset-reprocess](assets/fpo-existing-asset-reprocess.gif)


## FPO 표현물 보기 {#view-fpo-renditions}

워크플로우가 완료된 후 생성된 FPO 렌디션을 확인할 수 있습니다. Experience Manager Assets 사용자 인터페이스에서 에셋을 클릭하여 큰 미리 보기를 엽니다. 왼쪽 레일을 열고 **[!UICONTROL 렌디션]**&#x200B;을 선택합니다. 또는 미리 보기가 열려 있을 때 키보드 단축키 `Alt + 3`을(를) 사용합니다.

미리 보기를 로드하려면 **[!UICONTROL FPO 렌디션]**&#x200B;을 클릭합니다. 필요한 경우 렌디션을 마우스 오른쪽 버튼으로 클릭하고 파일 시스템에 저장할 수 있습니다. 왼쪽 레일에서 사용 가능한 렌디션을 확인합니다.

![rendition_list](assets/list-renditions.png)

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)