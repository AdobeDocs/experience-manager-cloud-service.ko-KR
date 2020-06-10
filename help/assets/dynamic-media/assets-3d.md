---
title: Dynamic Media에서 3D 자산 작업
seo-title: Dynamic Media에서 3D 자산 작업
description: Dynamic Media에서 3D 자산으로 작업하는 방법 살펴보기
seo-description: Dynamic Media에서 3D 자산으로 작업하는 방법 살펴보기
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS and AEM as a Cloud Service
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: 76cd37ae35360e68cca676de8eda53dff4819b41
workflow-type: tm+mt
source-wordcount: '2272'
ht-degree: 3%

---


# Dynamic Media에서 3D 자산 작업 {#working-with-three-d-assets-dm}

Dynamic Media를 사용하면 3D 자산을 매력적인 경험으로 업로드, 관리, 보고 전달할 수 있습니다.

* 3D 자산의 한 번의 클릭(도구 모음에서 **[!UICONTROL 빠른 게시]** 사용)으로 URL을 생성합니다.
* Adobe Dimension 기반의 고품질의 인터랙티브한 차원 뷰어 사전 설정을 사용하여 3D 자산을 볼 수 있도록 최적화된 지원을 제공합니다.
* 3D Media WCM 구성 요소를 사용하면 AEM Sites 페이지에 3D 자산을 쉽게 추가할 수 있습니다.

Dynamic Media에서 3D 자산을 사용하기 위해 추가로 설치할 필요는 없습니다.

![3d 신발](/help/assets/dynamic-media/assets/3d-dimensional-viewer-quickpublish-url-embed2a.png)

<!-- See also [Dynamic Media 3D Release Notes.](/help/release-notes/aem3d-release-notes.md) -->

## Dynamic Media에서 지원되는 3D 파일 포맷 {#supported-three-d-file-formats-in-dm}

Dynamic Media는 다음과 같은 3D 파일 형식을 지원합니다.

| 3D 파일 확장자 | 파일 포맷 | MIME 유형 | 메모 |
|---|---|---|---|
| GLB | 이진 GL 전송 | model/gltf-binary | 재질 및 텍스처를 하나의 에셋으로 포함시킬 수 있습니다. |
| OBJ | WaveFront 3D 개체 파일 | application/x-tgif |  |
| STL | 입체사진 | application/vnd.ms-pki.stl |  |
| USDZ | 범용 장면 설명 Zip 아카이브 | model/vnd.usdz+zip | *섭취 전용 지원; 보기 또는 상호 작용을 사용할 수 없습니다.* USDZ는 Safari 또는 iOS에서 기본적으로 볼 수 있는 독점적인 3D 포맷입니다. |

## 빠른 시작: 다이내믹 미디어의 3D 자산 {#quick-start-three-d}

다음 단계별 워크플로우 설명은 Dynamic Media에서 3D 자산을 빠르게 시작하고 실행하는 데 도움이 되도록 만들어졌습니다.

Dynamic Media에서 3D 자산으로 작업하기 전에 AEM 관리자가 이미 Dynamic Media Cloud 서비스를 활성화하고 구성했는지 확인하십시오.

Dynamic [Media Cloud 서비스 구성을 참조하십시오.](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)

1. **3D 자산 업로드**

   * [Dynamic Media에서 사용할 3D 자산 업로드](/help/assets/add-assets.md#upload-assets)
   * [Dynamic Media에서 업로드하기 위해 지원되는 3D 파일 포맷](#supported-three-d-file-formats-in-dm)

1. **3D 자산 관리**

   * 3D 에셋 구성 및 검색

      * [디지털 에셋 구성](/help/assets/organize-assets.md)
      * [3D 자산 검색](/help/assets/search-assets.md)
   * 3D 자산 보기

      * [3D 자산 보기 및 상호 작용](#viewing-three-d-assets)
      * [차원 뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md)
   * 3D 에셋 메타데이터를 사용한 작업

      * [디지털 자산에 대한 메타데이터 관리](/help/assets/manage-digital-assets.md#editing-properties)
      * [메타데이터 스키마](/help/assets/metadata-schemas.md)



1. **3D 에셋 게시**

   * [정적 Dynamic Media 3D 자산 게시](#publishing-three-d-assets)
   * [차원 뷰어를 사용하여 Dynamic Media 3D 자산을 게시하는 대체 방법](#alternate-publish-methods)

## 3D 자산 보기 및 상호 작용 정보 {#viewing-three-d-assets}

이 섹션에서는 다음 두 가지 방법으로 3D 자산을 보고 상호 작용하는 방법에 대해 설명합니다. 자산 세부 사항 페이지 및 사이트의 3D 미디어 구성 요소 내에서

인터랙티브한 3D 뷰어에는 3D 에셋을 궤도를 따라 이동하고, 확대/축소하고, 이동시킬 수 있는 인터랙티브한 카메라 컨트롤 컬렉션이 포함되어 있습니다.

자산 세부 사항 페이지 보기에서 3D 자산을 여는 데 걸리는 시간은 여러 가지 요인에 따라 다릅니다. 이러한 요인에는 다음이 포함됩니다.

* 서버에 대한 대역폭입니다.
* 서버 대기 시간
* 이미지의 복잡성.

또한 카메라를 대화형으로 조작할 때 워크스테이션, 노트북 또는 모바일 터치 장치와 같은 클라이언트 컴퓨터의 기능도 고려해야 합니다. 그래픽 성능이 좋은 강력한 시스템에서는 대화형 3D 보기 환경이 좀 더 원활하고 유용할 수 있습니다.

>[!TIP]
>
>Viewer Preset Editor에서 D 뷰어 사전 설정을 열어 3D 파일을 먼저 업로드할 필요 없이 3D 자산을 탐색하는 방법을 실습할 수 있습니다. Dimension 뷰어 사전 설정에는 상호 작용할 수 있는 내장된 3D 자산이 있습니다.
>
>See [Managing viewer presets.](/help/assets/dynamic-media/managing-viewer-presets.md)

## 자산 세부 사항 페이지에서 3D 자산 보기 및 상호 작용 {#viewing-three-d-assets-from-asset-details-page}

소프트웨어 [인터페이스를 사용하여 자산 미리 보기를 참조하십시오.](/help/assets/dynamic-media/previewing-assets.md)

**자산 세부 사항 페이지에서 3D 자산을 보고 상호 작용하려면**

1. 3D 자산을 AEM에 업로드했는지 확인합니다.

   Dynamic [Media에서 사용할 3D 자산 업로드를 참조하십시오.](/help/assets/add-assets.md#upload-assets)

1. AEM의 **[!UICONTROL 탐색]** 페이지에서 **[!UICONTROL 자산 > 파일]**&#x200B;을 탭합니다.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL Card View]**.
1. 보려는 3D 자산으로 이동합니다.
1. 3D 자산의 카드를 탭하여 자산 세부 사항 페이지에서 엽니다.
1. 3D 자산에 대한 세부 사항 보기 페이지에서 다음 중 하나를 수행합니다.

   * **카메라** 회전 - 3D 장면 및 개체 주위를 따라 주위를 선회할 수 있습니다.
      * _마우스_: 마우스 왼쪽 단추를 클릭하고 드래그합니다.
      * _터치 스크린_: 한 손가락으로 누르고 드래그하십시오.
   * **카메라** 이동 - 보기 왼쪽, 오른쪽, 위쪽 또는 아래쪽으로 이동합니다.
      * _마우스_: 마우스 오른쪽 단추를 클릭하고 드래그합니다.
      * _터치 스크린_: 두 손가락을 누른 상태에서 드래그합니다.
   * **카메라** 확대 - 3D 장면 영역 안팎으로 카메라를 확대/축소할 수 있습니다.
      * _마우스_: 스크롤 휠입니다.
      * _터치 스크린_: 두 손가락으로 집어요.
   * **카메라** 다시 입력 - 3D 장면의 개체 지점으로 카메라를 재입력할 수 있습니다.
      * _마우스_: 두 번 클릭합니다.
      * _터치 스크린_: 두 번 누릅니다.
   * **재설정** - 페이지의 오른쪽 아래 모서리 근처에 있는 재설정 아이콘을 눌러 보기 대상 포인트를 3D 자산의 중심으로 복원합니다. 또한 재설정은 카메라를 더 가깝게 또는 멀리 이동하여 에셋을 전체적으로 적절한 보기 크기로 표시합니다.
   * **전체 화면 모드** - 전체 화면 모드로 전환하려면 페이지의 오른쪽 아래에 있는 전체 화면 아이콘을 누릅니다.

1. 페이지 상단 오른쪽에서 **[!UICONTROL 닫기]**&#x200B;를 탭하여 자산 페이지로 돌아갑니다.

## 3D 미디어 구성 요소에서 3D 자산 보기 및 상호 작용 {#interacting-with-asset-inside-three-d-media-component}

웹 페이지가 **[!UICONTROL 편집]** 모드에 있는 경우 3D 자산과 상호 작용할 수 없습니다. 자산을 대화형으로 만들려면 미리 **[!UICONTROL 보기]** 기능을 사용하여 3D 미디어 구성 요소의 기능에 대한 전체 액세스 권한을 제공하는 페이지 편집기에서 웹 페이지를 볼 수 있습니다.

>[!IMPORTANT]
>
>3D 미디어 구성 요소를 웹 페이지에 추가하고 3D 자산을 구성 요소에 할당한 후에만 이 작업을 수행할 수 있습니다. 웹 페이지에 [3D 미디어 구성 요소 추가](#adding-the-three-d-media-component-to-a-web-page) 및 3D 미디어 구성 [요소에 3D 자산 할당을 참조하십시오.](#assigning-a-three-d-asset-to-the-component)

소프트웨어 [인터페이스를 사용하여 자산 미리 보기를 참조하십시오.](/help/assets/dynamic-media/previewing-assets.md)

**3D 미디어 구성 요소 내에서 3D 자산을 보고 상호 작용하려면**

1. 웹 페이지가 **[!UICONTROL 편집]** 모드에 있는 동안 다음 중 하나를 수행합니다.

   * 페이지의 오른쪽 위 근처에 있는 미리 **[!UICONTROL 보기]** 를 클릭하여 미리 **[!UICONTROL 보기]** 모드로 전환합니다.
   * 브라우저의 페이지 URL `/editor.html` 에서 삭제합니다.
   ![
A fully interactive 3D asset as displayed in ](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)****

1. ![3D 미디어 구성 요소 내부에 표시되는 3D 자산](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)미리 보기 **[!UICONTROL 모드에서 표시된 대로 완전히 인터랙티브한 3D 자산]** .

   * 미리 **[!UICONTROL 보기]** 모드에서 다음 중 하나를 수행합니다.**
      * **카메라** 회전 - 3D 장면 및 개체 주위를 따라 주위를 선회할 수 있습니다.
      * _마우스_: 마우스 왼쪽 단추를 클릭하고 드래그합니다.
   * _터치 스크린_: 한 손가락으로 누르고 드래그하십시오.
      * **카메라** 이동 - 보기 왼쪽, 오른쪽, 위쪽 또는 아래쪽으로 이동합니다.
      * _마우스_: 마우스 오른쪽 단추를 클릭하고 드래그합니다.
   * _터치 스크린_: 두 손가락을 누른 상태에서 드래그합니다.
      * **카메라** 확대 - 3D 장면 영역 안팎으로 카메라를 확대/축소할 수 있습니다.
      * _마우스_: 스크롤 휠입니다.
   * _터치 스크린_: 두 손가락으로 집어요.
      * **카메라** 다시 입력 - 3D 장면의 개체 지점으로 카메라를 재입력할 수 있습니다.
      * _마우스_: 두 번 클릭합니다.
   * _터치 스크린_: 두 번 누릅니다.
   * **재설정** - 페이지의 오른쪽 아래 모서리 근처에 있는 재설정 아이콘을 눌러 보기 대상 포인트를 3D 자산의 중심으로 복원합니다. 또한 재설정은 카메라를 더 가깝게 또는 멀리 이동하여 에셋을 전체적으로 적절한 보기 크기로 표시합니다.

## **전체 화면 모드** - 전체 화면 모드로 전환하려면 페이지의 오른쪽 아래에 있는 전체 화면 아이콘을 누릅니다.

3D 미디어 구성 요소 작업 정보 {#working-with-three-d-media-component}

* [Dynamic Media에는 AEM Sites에서 사용할 수 있는 Dynamic Media 3D 미디어 구성 요소가 포함되어 있으므로 웹 페이지에서 3D 모델을 인터랙티브하게 볼 수 있습니다.](#adding-three-d-media-component-to-page-template)
* [페이지 템플릿에 3D 미디어 구성 요소 추가](#adding-three-d-media-component-to-page-template)
   * [웹 페이지에 3D 미디어 구성 요소 추가](#adding-the-three-d-media-component-to-a-web-page)
* [선택 사항 - 3D 미디어 구성 요소 구성](#configuring-the-three-d-component)


## [3D 미디어 구성 요소에 3D 자산 할당](#assigning-a-three-d-asset-to-the-component)

1. 페이지 템플릿에 3D 미디어 구성 요소 추가 {#adding-three-d-media-component-to-page-template}]**
1. 도구 > **[!UICONTROL 일반 > 템플릿으로 이동합니다]**.
1. 에서 3D 구성 요소를 활성화할 페이지 템플릿으로 이동하고 템플릿을 선택합니다.****
1. 편집을 **[!UICONTROL 눌러]** 템플릿을 엽니다.

   페이지의 오른쪽 위 근처에 있는 드롭다운 메뉴에서 구조 **** 모드를 선택합니다(아직 활성화되지 않은 경우).](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)

1. ![3d-media-component-structure](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)]**
1. 레이아웃 컨테이너 **[!UICONTROL 영역에서]** 빈 영역을 눌러 선택하고 관련 도구 모음을 엽니다.****
1. 도구 모음에서 **[!UICONTROL 정책]** 아이콘을 눌러 **[!UICONTROL 정책 편집기를 엽니다]**.********
1. [ **[!UICONTROL 속성]** ] **** 섹션의 [ **[!UICONTROL 허용된 구성 요소]**] 탭에서 **[!UICONTROL 동적 미디어로]**&#x200B;스크롤한 다음 목록을 확장하고3D 미디어를 확인합니다.

   완료를 **[!UICONTROL 눌러]** 변경 사항을 저장하고 **[!UICONTROL 정책 편집기를 닫습니다]**.

## 이제 이 템플릿을 사용하는 모든 페이지에 Dynamic Media 3D 미디어 구성 요소를 배치할 수 있습니다.{#adding-the-three-d-media-component-to-a-web-page}

웹 페이지에 3D 미디어 구성 요소 추가 {#adding-the-three-d-media-component-to-a-web-page}

Adobe Experience Manager를 웹 컨텐츠 관리 시스템으로 사용하는 경우 3D 미디어 구성 요소를 통해 웹 페이지에 3D 자산을 추가할 수 있습니다.[](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)

1. See also [Adding Dynamic Media assets to pages.](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
1. AEM Sites를 열고 Dynamic Media 3D 미디어 구성 요소를 추가할 웹 페이지를 선택합니다.********

   편집 **** (연필) 아이콘을 눌러 페이지를 페이지 편집기로 엽니다. 페이지의 오른쪽 **[!UICONTROL 위]** 근처에 편집 모드가 선택되어 있는지 확인합니다.](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. ![3d-media-component-add](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. 도구 모음에서 사이드 패널 아이콘을 눌러 패널 표시를 켜거나 전환합니다.****

   사이드 패널에서 더하기 기호 아이콘을 눌러 구성 요소 **[!UICONTROL 목록을]** 엽니다.](/help/assets/dynamic-media/assets/3d-assets-filtera.png)

1. ![3d-media-component-drag-drop](/help/assets/dynamic-media/assets/3d-assets-filtera.png)]******

[ **[!UICONTROL 구성 요소]** ] 목록에서 **[!UICONTROL 3D 미디어]** 구성 요소를 3D 뷰어를 표시할 페이지의 위치로 드래그합니다.

이제 구성 요소에 3D 자산을 할당할 준비가 되었습니다.[](#assigning-a-three-d-asset-to-the-component)

### 3D [미디어 구성 요소에 3D 자산 할당을 참조하십시오.](#assigning-a-three-d-asset-to-the-component)

1. 선택 사항 - 3D 미디어 구성 요소 구성 {#configuring-the-three-d-component}]**
1. AEM Sites 페이지 편집기에서 이전에 페이지에 추가한 **[!UICONTROL 3D Media Viewer]** 구성 요소를 선택합니다.

   구성 **[!UICONTROL 아이콘]** (렌치)을 눌러 구성 요소 구성 대화 상자를 엽니다.](/help/assets/dynamic-media/assets/3d-media-component-configa.png)

1. ![3d-media-component-config](/help/assets/dynamic-media/assets/3d-media-component-configa.png)]**

   [3D 미디어] 대화 상자의 [뷰어 사전 설정] 드롭다운 목록에서 **[!UICONTROL 차원을]** 선택하여 Dimensity viewer 사전 설정을 구성 요소에 지정합니다.](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

1. ![3d-media-component-edit-config](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

## 오른쪽 상단 모서리에서 확인 표시를 눌러 변경 사항을 저장합니다.{#assigning-a-three-d-asset-to-the-component}

3D 미디어 구성 요소에 3D 자산 할당 {#assigning-a-three-d-asset-to-the-component}

웹 페이지에 3D 미디어 구성 요소를 추가한 후 3D 자산을 할당할 수 있습니다.[](#adding-the-three-d-media-component-to-a-web-page)

1. 웹 [페이지에 3D 미디어 구성 요소 추가를 참조하십시오.](#adding-the-three-d-media-component-to-a-web-page)]******
1. AEM Sites 페이지 편집기에서 **[!UICONTROL 자산]** 아이콘을 클릭하여 사이드 패널에서 **[!UICONTROL 자산을]** 엽니다.
1. 드롭다운 목록에서 3D를 선택하여 **[!UICONTROL 3D]** 자산 파일 유형만 표시합니다.
1. 사이드 패널에서 편집하는 페이지에서 보려는 3D 자산을 검색하거나 스크롤합니다.****

   자산 사이드 패널에서 3D 자산을 드래그하여 이전에 페이지에 추가한 **[!UICONTROL 3D 미디어]** 구성 요소에 놓습니다.](/help/assets/dynamic-media/assets/3d-asset-adda.png)

>![3d 미디어 구성 요소에 3d 에셋 할당](/help/assets/dynamic-media/assets/3d-asset-adda.png)
>
>[!NOTE]]******

## 웹 페이지가 AEM Sites **[!UICONTROL 편집]** 모드에 있는 동안 3D 미디어 구성 요소는 3D 자산을 표시하지만 자산과의 상호 작용은 불가능합니다. 자산을 대화형으로 만들려면 미리 **[!UICONTROL 보기]** 기능을 사용하여 3D 미디어 구성 요소의 기능에 대한 전체 액세스 권한을 제공하는 페이지 편집기에서 웹 페이지를 볼 수 있습니다.

정적 Dynamic Media 3D 자산 게시 {#publishing-three-d-assets}***

Dynamic Media는 Dynamic Media에서 *정적 컨텐츠로* 지원되는 다양한 3D 파일 포맷을 수용합니다. 정적 컨텐츠는 3D 자산을 업로드 및 게시할 수 있지만, 3D 자산과 관련된 *다이내믹* 이미징 또는 이미지 리핑은 지원되지 않음을 의미합니다. Dynamic Media Imaging Server가 3D 형식을 인식하지 않기 때문입니다. 따라서 Dynamic Media에서 3D 자산을 게시하면 복사할 수 있는 인스턴트 URL이 있습니다. 3D 자산의 URL은 일반적인 다이내믹 미디어 URL 구조를 따릅니다. 하지만 Dynamic Media의 기존 이미지 자산과 달리 자산의 URL에서 매개 변수를 편집할 수는 없습니다.

정적 [자산에 대한 URL 획득을 참조하십시오.](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset)]**********

[ **[!UICONTROL 카드 보기]**]에서 작은 둥근 모양 아이콘이 자산 이름 바로 아래, 해당 날짜 및 시간 왼쪽에 표시되어 게시되었음을 나타냅니다. 목록 보기 **[!UICONTROL 에서]**&#x200B;게시된 **** 열은 게시되었거나 게시되지 않은 자산을 나타냅니다.

AEM을 WCM으로 사용하는 경우 이 게시 방법을 사용하여 웹 페이지에 직접 Dynamic Media 3D 자산을 추가합니다.[](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

다이내믹 [미디어 자산 게시를 참조하십시오.](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

페이지 [게시를 참조하십시오.](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)

1. **정적 Dynamic Media 3D 자산을 게시하려면**
1. 3D 자산(GLB, OBJ 또는 STL 파일 형식)을 열어 자산 세부 사항 페이지에서 볼 수 있습니다.****

   도구 모음에서 **[!UICONTROL 빠른 게시를 누릅니다]**.](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)

1. ![3d-asset-quick-publish](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)]**
1. 닫기 **[!UICONTROL 를]** 눌러 대화 상자를 종료하고 자산 세부 사항 페이지로 돌아갑니다.

   3D 자산 파일 이름의 왼쪽 드롭다운 목록에서 표현물을 **[!UICONTROL 누릅니다]**.](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)

1. ![3d-asset-renditions](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)]******
   * 원본을 **[!UICONTROL 누릅니다]**. 3D 자산을 게시하거나 &quot;활성화&quot;하면 다음 3D 자산 조건이 모두 충족되는 경우 페이지의 왼쪽 아래 모서리 근처에 **[!UICONTROL URL]** 단추가 표시됩니다.
   * 3D 자산은 지원되는 형식(GLB, OBJ, STL 및 USDZ)입니다.
   * 3D 자산이 IPS(Dynamic Media Image Production System)로 수집되었습니다.
   ![3D 자산이 게시됩니다.](/help/assets/dynamic-media/assets/3d-asset-urla.png)

1. ![3d-asset-url](/help/assets/dynamic-media/assets/3d-asset-urla.png)]**

### URL **[!UICONTROL 을]** 눌러 웹 페이지에서 복사하고 사용할 수 있는 3D 자산의 직접 제작 URL을 표시합니다.

차원 뷰어를 사용하여 Dynamic Media 3D 자산을 게시하는 대체 방법 {#alternate-publish-methods}*

* AEM을 WCM으로 사용하지 *않는* 경우 Dynamic Media 3D 자산을 게시하려면 다음 두 가지 방법을 사용하십시오.]******

   **[!UICONTROL URL]** - 타사 웹 컨텐츠 관리 시스템을 사용하고 Dimensity 뷰어를 사용하여 Dynamic Media 3D 자산을 웹 페이지에 연결하려면 **[!UICONTROL URL을]** 사용합니다.](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset)

* See [Linking URLs to your web application.](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset)]**********

   **[!UICONTROL 포함]** - **[!UICONTROL 차원 뷰어를 사용하여 웹 페이지에 임베드된 Dynamic Media 3D 자산을 보려면 임베드]** 기능을 사용합니다. 포함 코드를 클립보드에 복사하여 웹 페이지에 붙여넣을 수 있습니다. 포함 대화 상자에서 코드 편집이 **[!UICONTROL 허용되지]** 않습니다.](/help/assets/dynamic-media/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page)
