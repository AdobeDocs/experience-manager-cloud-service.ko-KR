---
title: Dynamic Media에서 3D 자산 작업
description: Dynamic Media에서 3D 자산으로 작업하는 방법을 알아봅니다.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS and Experience Manager as a Cloud Service
topic-tags: introduction
content-type: reference
feature: 3D Assets
role: User
exl-id: 82084ba7-1302-4cbd-8626-d77b3aaa4ed1
source-git-commit: 251975b825adb5748b6f76c0fdf9d0b7262b2d35
workflow-type: tm+mt
source-wordcount: '2219'
ht-degree: 5%

---

# Dynamic Media에서 3D 자산 작업 {#working-with-three-d-assets-dm}

Dynamic Media을 사용하면 3D 자산을 업로드, 관리, 보고 몰입형 환경으로 제공할 수 있습니다.

* 한 번의 클릭으로 게시( **[!UICONTROL 빠른 게시]** 3D 자산 의 (도구 모음)을 사용하여 URL을 생성합니다.
* Adobe Dimension 기반의 고품질의 대화형 차원 뷰어 사전 설정을 사용하여 3D 자산 보기를 지원하도록 최적화되었습니다.
* 3D Media WCM 구성 요소를 사용하면 3D 자산을 [!DNL Adobe Experience Manager Sites] 페이지.

Dynamic Media에서 3D 자산을 사용하는 데 필요한 추가 설치는 없습니다.

![3d 신발](/help/assets/dynamic-media/assets/3d-dimensional-viewer-quickpublish-url-embed2a.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## Dynamic Media에서 지원되는 3D 형식 {#supported-three-d-file-formats-in-dm}

Dynamic Media은 다음 3D 파일 형식을 지원합니다.

참조 - [Experience Manager Assets에서 지원되는 3D 형식](/help/assets/file-format-support.md#support-3d-formats)

| 3D 파일 확장명 | 파일 형식 | MIME 유형 | 메모 |
|---|---|---|---|
| GLB | 이진 GL 전송 | model/gltf-binary | 재료와 텍스처를 하나의 자산으로 포함합니다. |
| OBJ | WaveFront 3D 개체 파일 | application/x-tgif |  |
| STL | 입체광조형 | application/vnd.ms-pki.stl |  |
| USDZ | 범용 장면 설명 Zip 아카이브 | model/vnd.usdz+zip | *수집만 지원 보거나 상호 작용을 사용할 수 없습니다.* USDZ는 Safari 또는 iOS에서 기본적으로 볼 수 있는 전용 3D 포맷입니다. |

<!-- >[!NOTE]
>
>The 3D Media WCM component and 3D preview on an asset's Details page is not compatible with the latest version of Chrome (97.x). Instead, to work with 3D assets, use Firefox or Safari, or use an earlier version of Chrome (96.x). CQDOC-18921-->

## 빠른 시작: Dynamic Media의 3D 자산 {#quick-start-three-d}

다음 단계별 워크플로우 설명은 Dynamic Media에서 3D 자산을 빠르게 시작하고 실행할 수 있도록 설계되었습니다.

Dynamic Media에서 3D 자산으로 작업하기 전에 [!DNL Experience Manager] 관리자가 이미 Dynamic Media Cloud Services을 활성화하고 구성했습니다.

자세한 내용은 [Dynamic Media Cloud Services 구성](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).

1. **3D 자산 업로드**

   * [Dynamic Media에서 사용할 3D 자산 업로드](/help/assets/add-assets.md#upload-assets)
   * [Dynamic Media에서 업로드할 수 있는 3D 파일 형식 지원](#supported-three-d-file-formats-in-dm)

1. **3D 자산 관리**

   * 3D 자산 구성 및 검색

      * [디지털 자산 구성](/help/assets/organize-assets.md)
      * [3D 자산 검색](/help/assets/search-assets.md)
   * 3D 자산 보기

      * [3D 자산 보기 및 상호 작용](#viewing-three-d-assets)
      * [차원 뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md)
   * 3D 자산 메타데이터 작업

      * [디지털 자산에 대한 메타데이터 관리](/help/assets/manage-digital-assets.md#editing-properties)
      * [메타데이터 스키마](/help/assets/metadata-schemas.md)



1. **3D 자산 게시**

   * [정적 Dynamic Media 3D 자산 게시](#publishing-three-d-assets)
   * [차원 뷰어를 사용하여 Dynamic Media 3D 자산을 게시하는 대체 방법](#alternate-publish-methods)

## 3D 자산 보기 및 상호 작용 정보 {#viewing-three-d-assets}

이 섹션에서는 다음 두 가지 방법으로 3D 자산을 보고 상호 작용하는 방법을 설명합니다. 자산 세부 사항 페이지 내와 사이트의 3D 미디어 구성 요소 내에서 를 참조하십시오.

대화형 3D 뷰어에는 특히 3D 자산을 궤도 회전, 확대/축소 및 이동할 수 있는 대화형 카메라 컨트롤 컬렉션이 포함되어 있습니다.

자산 세부 사항 페이지 보기에서 3D 자산을 여는 데 걸리는 시간은 몇 가지 요인에 따라 다릅니다. 이러한 요인에는 다음이 포함됩니다.

* 서버에 대한 대역폭입니다.
* 서버에 대기 시간
* 이미지의 복잡성입니다.

또한 카메라를 대화식으로 조작할 때는 워크스테이션, 노트북 또는 모바일 터치 장치와 같은 클라이언트 컴퓨터의 기능도 고려해야 합니다. 그래픽 성능이 좋은 강력한 시스템에서는 대화형 3D 보기 환경이 좀 더 원활하고 유용할 수 있습니다.

>[!TIP]
>
>먼저 3D 파일을 업로드할 필요 없이 뷰어 사전 설정 편집기에서 Dimensional viewer 사전 설정을 열어 3D 자산 탐색을 연습할 수 있습니다. 차원 뷰어 사전 설정에는 상호 작용할 수 있는 내장된 3D 자산이 있습니다.
>
>자세한 내용은 [뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md).

## 자산 세부 사항 페이지에서 3D 자산을 보고 상호 작용할 수 있습니다 {#viewing-three-d-assets-from-asset-details-page}

참조 - [소프트웨어 인터페이스를 사용하여 자산 미리 보기](/help/assets/dynamic-media/previewing-assets.md).

**자산 세부 사항 페이지에서 3D 자산을 보고 상호 작용하려면 다음을 수행하십시오.**

1. 에 3D 자산을 업로드했는지 확인합니다. [!DNL Experience Manager].

   자세한 내용은 [Dynamic Media에서 사용할 3D 자산 업로드](/help/assets/add-assets.md#upload-assets).

1. From [!DNL Experience Manager], **[!UICONTROL 탐색]** 페이지를 선택하고 **[!UICONTROL 자산 > 파일]**.
1. 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 보기]** 드롭다운 목록에서 **[!UICONTROL 카드 보기]**.
1. 보려는 3D 자산으로 이동합니다.
1. 세부 사항 페이지에서 자산을 열려면 3D 자산의 카드를 선택합니다.
1. 3D 자산에 대한 세부 사항 페이지에서 다음 중 하나를 수행합니다.

   | 보기 | 설명 | 마우스 동작 | 터치 화면 작업 |
   | --- | --- | --- | --- |
   | **카메라 회전** | 3D 장면 및 개체 주위로 보기를 궤도 회전합니다. | 왼쪽 클릭 + 드래그. | 한 손가락으로 누르기 + 드래그. |
   | **카메라 팬** | 왼쪽, 오른쪽, 위 또는 아래로 뷰를 패닝합니다. | 마우스 오른쪽 단추 클릭 + 드래그. | 두 손가락으로 누르기 + 드래그. |
   | **카메라 확대/축소** | 3D 장면의 영역 내외로 이동합니다. | 스크롤 휠입니다. | 두 손가락에 끼어요 |
   | **카메라 다시 입력** | 3D 장면에서 개체의 한 지점으로 카메라를 다시 입력합니다. | 두 번 클릭. | 두 번 탭하세요. |
   | **재설정** | 페이지의 오른쪽 아래 모서리 근처에 있는 재설정 아이콘을 선택하여 보기 대상 포인트를 3D 자산의 중심으로 복원합니다. 또한 재설정을 수행하면 카메라가 더 가깝거나 더 멀게 이동되어 자산이 전체적으로 적절한 보기 크기로 표시됩니다. |  |  |
   | **전체 화면 모드** | 전체 화면 모드로 전환하려면 페이지의 오른쪽 아래 모서리에서 전체 화면 아이콘을 선택합니다. |  |  |

1. 페이지의 오른쪽 위 모서리에서 을(를) 선택합니다 **[!UICONTROL 닫기]** 자산 페이지로 돌아갑니다.

## 3D Media 구성 요소에서 3D 자산을 보고 상호 작용할 수 있습니다 {#interacting-with-asset-inside-three-d-media-component}

웹 페이지가 **[!UICONTROL 편집]** 모드 에서는 3D 자산과 상호 작용할 수 없습니다. 자산을 대화형으로 만들려면 **[!UICONTROL 미리 보기]** 3D Media 구성 요소의 기능에 대한 전체 액세스 권한을 사용하여 페이지 편집기에서 웹 페이지를 보는 기능.

>[!IMPORTANT]
>
>웹 페이지에 3D Media 구성 요소를 추가하고 구성 요소에 3D 자산을 할당한 후에만 이 작업을 수행할 수 있습니다. 자세한 내용은 [웹 페이지에 3D Media 구성 요소 추가](#adding-the-three-d-media-component-to-a-web-page) 및 [3D 미디어 구성 요소에 3D 자산 할당](#assigning-a-three-d-asset-to-the-component).

참조 - [소프트웨어 인터페이스를 사용하여 자산 미리 보기](/help/assets/dynamic-media/previewing-assets.md).

**3D Media 구성 요소 내에서 3D 자산을 보고 상호 작용하려면 다음을 수행하십시오.**

1. 웹 페이지가 있는 동안 **[!UICONTROL 편집]** 모드에서 다음 중 하나를 수행합니다.

   * 페이지 오른쪽 상단의 **[!UICONTROL 미리 보기]** 을 입력합니다. **[!UICONTROL 미리 보기]** 모드.
   * 삭제 `/editor.html` 를 래핑합니다.

에 표시되는 완전히 대화형 3D 자산    ![3D Media 구성 요소 내부를 보여주는 3D 자산](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)
에 표시되는 완전히 대화형 3D 자산 **[!UICONTROL 미리 보기]** 모드.

1. 에 있는 동안 **[!UICONTROL 미리 보기]** 모드에서 다음 중 하나를 수행합니다.

   | 보기 | 설명 | 마우스 동작 | 터치 화면 작업 |
   | --- | --- | --- | --- |
   | **카메라 회전** | 3D 장면 및 개체 주위로 보기를 궤도 회전합니다. | 왼쪽 클릭 + 드래그. | 한 손가락으로 누르기 + 드래그. |
   | **카메라 팬** | 왼쪽, 오른쪽, 위 또는 아래로 뷰를 패닝합니다. | 마우스 오른쪽 단추 클릭 + 드래그. | 두 손가락으로 누르기 + 드래그. |
   | **카메라 확대/축소** | 3D 장면의 영역 내외로 이동합니다. | 스크롤 휠입니다. | 두 손가락에 끼어요 |
   | **카메라 다시 입력** | 3D 장면에서 개체의 한 지점으로 카메라를 다시 입력합니다. | 두 번 클릭. | 두 번 탭하세요. |
   | **재설정** | 페이지의 오른쪽 아래 모서리 근처에 있는 재설정 아이콘을 선택하여 보기 대상 포인트를 3D 자산의 중심으로 복원합니다. 또한 재설정을 수행하면 카메라가 더 가깝거나 더 멀게 이동되어 자산이 전체적으로 적절한 보기 크기로 표시됩니다. |  |  |
   | **전체 화면 모드** | 전체 화면 모드로 전환하려면 페이지의 오른쪽 아래 모서리에서 전체 화면 아이콘을 선택합니다. |  |  |

## 3D Media 구성 요소 작업 정보 {#working-with-three-d-media-component}

Dynamic Media에는 에서 사용할 수 있는 Dynamic Media 3D Media 구성 요소가 포함되어 있습니다. [!DNL Experience Manager Sites] 를 클릭하여 웹 페이지에서 3D 모델을 대화형 볼 수 있도록 합니다.

* [페이지 템플릿에 3D Media 구성 요소 추가](#adding-three-d-media-component-to-page-template)
* [웹 페이지에 3D Media 구성 요소 추가](#adding-the-three-d-media-component-to-a-web-page)
   * [선택 사항 - 3D Media 구성 요소 구성](#configuring-the-three-d-component)
* [3D 미디어 구성 요소에 3D 자산 할당](#assigning-a-three-d-asset-to-the-component)

## 페이지 템플릿에 3D Media 구성 요소 추가 {#adding-three-d-media-component-to-page-template}

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL 일반]** > **[!UICONTROL 템플릿]**.
1. 에서 3D 구성 요소를 활성화할 페이지 템플릿으로 이동하여 템플릿을 선택합니다.
1. 템플릿을 열려면 **[!UICONTROL 편집]**.
1. 페이지 오른쪽 상단의 드롭다운 메뉴에서 을(를) 선택합니다 **[!UICONTROL 구조]** 모드(아직 활성화되지 않은 경우)

   ![3d-media-component-structure](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)

1. 빈 영역을 선택하고 연결된 도구 모음을 열려면 **[!UICONTROL 레이아웃 컨테이너]** 지역.
1. 도구 모음에서 **[!UICONTROL 정책]** 아이콘을 클릭하여 열기 **[!UICONTROL 정책 편집기]**.
1. 에서 **[!UICONTROL 속성]** 섹션, 아래에 **[!UICONTROL 허용된 구성 요소]** 탭, 아래로 스크롤합니다. **[!UICONTROL Dynamic Media]**&#x200B;그런 다음 목록을 확장하고 다음을 확인합니다 **[!UICONTROL 3D 미디어]**.
1. 탭 **[!UICONTROL 완료]** 변경 내용을 저장하고 **[!UICONTROL 정책 편집기]**.

   이제 이 템플릿을 사용하는 모든 페이지에 Dynamic Media 3D Media 구성 요소를 배치할 수 있습니다.

## 웹 페이지에 3D Media 구성 요소 추가 {#adding-the-three-d-media-component-to-a-web-page}

사용 중인 경우 [!DNL Experience Manager] 웹 컨텐츠 관리 시스템으로 3D Media 구성 요소를 통해 웹 페이지에 3D 자산을 추가할 수 있습니다.

참조 - [페이지에 Dynamic Media 자산 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

1. 열기 [!DNL Experience Manager Sites] Dynamic Media 3D Media 구성 요소를 추가할 웹 페이지를 선택합니다.
1. 페이지를 페이지 편집기로 열려면 **[!UICONTROL 편집]** (연필) 아이콘. 확인 **[!UICONTROL 편집]** 페이지 오른쪽 상단 근처에 모드가 선택됩니다.

   ![3d-media-component-add](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. 도구 모음에서 사이드 패널 아이콘을 선택하여 패널 표시를 전환하거나 &quot;켜기&quot;를 선택합니다.

1. 사이드 패널에서 더하기 기호 아이콘을 선택하여 **[!UICONTROL 구성 요소]** 목록.

   ![3d media-component-drag-drop](/help/assets/dynamic-media/assets/3d-assets-filtera.png)

1. 을(를) 드래그합니다. **[!UICONTROL 3D 미디어]** 구성 요소 **[!UICONTROL 구성 요소]** 3D 뷰어를 표시할 페이지의 위치로 표시합니다.

이제 구성 요소에 3D 자산을 할당할 준비가 되었습니다.

자세한 내용은 [3D 미디어 구성 요소에 3D 자산 할당](#assigning-a-three-d-asset-to-the-component)

### 선택 사항 - 3D Media 구성 요소 구성 {#configuring-the-three-d-component}

1. 에서 [!DNL Experience Manager Sites] 페이지 편집기에서 **[!UICONTROL 3D Media Viewer]** 이전에 페이지에 추가한 구성 요소입니다.
1. 구성 요소 구성 대화 상자를 열려면 **[!UICONTROL 구성]** 아이콘(렌치).

   ![3d-media-component-config](/help/assets/dynamic-media/assets/3d-media-component-configa.png)

1. 3D Media 대화 상자의 뷰어 사전 설정 드롭다운 목록에서 을 선택합니다 **[!UICONTROL 차원]** 구성 요소에 차원 뷰어 사전 설정을 할당하려면

   ![3d-media-component-edit-config](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

1. 오른쪽 상단 모서리에서 확인 표시를 선택하여 변경 사항을 저장합니다.

## 3D 미디어 구성 요소에 3D 자산 할당 {#assigning-a-three-d-asset-to-the-component}

웹 페이지에 3D Media 구성 요소를 추가한 후 3D 자산을 여기에 할당할 수 있습니다.

자세한 내용은 [웹 페이지에 3D Media 구성 요소 추가](#adding-the-three-d-media-component-to-a-web-page).

1. 에서 [!DNL Experience Manager Sites] 페이지 편집기에서 **[!UICONTROL 자산]** 아이콘 열기 **[!UICONTROL 자산]** 를 클릭합니다.
1. 드롭다운 목록에서 을(를) 선택합니다 **[!UICONTROL 3D]** 3D 자산 파일 유형만 표시합니다.
1. 사이드 패널에서 편집 중인 페이지에서 볼 3D 자산을 검색하거나 스크롤합니다.
1. 자산 사이드 패널에서 3D 자산을 드래그하여 **[!UICONTROL 3D 미디어]** 이전에 페이지에 추가한 구성 요소입니다.

   ![3d Media 구성 요소에 3d 자산 할당](/help/assets/dynamic-media/assets/3d-asset-adda.png)

>[!NOTE]
>
>웹 페이지는 [!DNL Experience Manager Sites] **[!UICONTROL 편집]** 모드에서는 3D Media 구성 요소에 3D 자산이 표시되지만 자산과 상호 작용할 수는 없습니다. 자산을 대화형으로 만들려면 **[!UICONTROL 미리 보기]** 3D Media 구성 요소의 기능에 대한 전체 액세스 권한을 사용하여 페이지 편집기에서 웹 페이지를 보는 기능.

## 정적 Dynamic Media 3D 자산 게시 {#publishing-three-d-assets}

Dynamic Media은 다음과 같이 지원되는 다양한 3D 파일 형식을 허용합니다 *정적 콘텐츠* Dynamic Media. 정적 컨텐츠는 3D 자산을 업로드하고 게시할 수 있지만 을 지원하지 않음을 의미합니다 *동적* 3D 자산과 관련된 이미징 또는 이미지 리퍼팅. 이유는 Dynamic Media 이미징 서버에서 3D 형식을 인식하지 못하기 때문입니다. 따라서 Dynamic Media에서 3D 자산을 게시하면 복사할 수 있는 인스턴트 URL이 제공됩니다. 3D 자산의 URL은 일반적인 Dynamic Media URL 구조를 따릅니다. 하지만 Dynamic Media의 기존 이미지 자산과 달리 자산의 URL에서는 매개 변수를 편집할 수 없습니다.

참조 - [정적 자산의 URL 가져오기](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset).

에서 **[!UICONTROL 카드 보기]**&#x200B;를 입력하면 자산 이름 바로 아래에 작은 지구본 아이콘이 표시되고, 그 날짜 및 시간 왼쪽에는 게시되었음을 나타냅니다. In the **[!UICONTROL List View]**, a **[!UICONTROL Published]** column indicates which assets are published or which are not.

사용 중인 경우 [!DNL Experience Manager] wcm의 경우 이 게시 방법을 사용하여 웹 페이지에서 바로 Dynamic Media 3D 자산을 추가합니다.

참조 - [Dynamic Media 자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

참조 - [페이지 게시](/help/sites-cloud/authoring/fundamentals/publishing-pages.md).

**정적 Dynamic Media 3D 자산을 게시하려면 다음을 수행하십시오.**

1. 3D 자산(GLB, OBJ 또는 STL 파일 형식)을 엽니다.
1. 세부 정보 페이지의 도구 모음에서 를 선택합니다 **[!UICONTROL 빠른 게시]**.

   ![3d-asset-quick-publish](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)

1. 탭 **[!UICONTROL 닫기]** 대화 상자를 종료하고 자산 세부 사항 페이지로 돌아갑니다.
1. 3D 자산 파일 이름의 왼쪽에 있는 드롭다운 목록에서 를 선택합니다 **[!UICONTROL 표현물]**.

   ![3d-asset-renditions](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)

1. 탭 **[!UICONTROL 원본]**. 3D 자산이 게시되면(또는 &quot;활성화됨&quot;), **[!UICONTROL URL]** 다음 3D 자산 조건이 모두 충족되는 경우 페이지의 왼쪽 하단 모서리 근처에 버튼이 표시됩니다.
   * 3D 자산은 지원되는 형식(GLB, OBJ, STL 및 USDZ)입니다.
   * 3D 자산을 Dynamic Media IPS(이미지 프로덕션 시스템)에 수집했습니다.
   * 3D 자산이 게시됩니다.

   ![3d-asset-url](/help/assets/dynamic-media/assets/3d-asset-urla.png)

1. 웹 페이지에서 복사하고 사용할 수 있는 3D 자산의 직접 프로덕션 URL을 표시하려면 을(를) 선택합니다 **[!UICONTROL URL]**.

### 차원 뷰어를 사용하여 Dynamic Media 3D 자산을 게시하는 대체 방법 {#alternate-publish-methods}

다음과 같은 경우 Dynamic Media 3D 자산을 게시하는 두 가지 방법을 사용하십시오 *not* 사용 [!DNL Experience Manager] WCM으로 사용할 수 있습니다.

* **[!UICONTROL URL]** - 사용 **[!UICONTROL URL]** 타사 웹 컨텐츠 관리 시스템을 사용하는 경우 차원 뷰어를 사용하여 Dynamic Media 3D 자산을 웹 페이지에 연결하려는 경우.

   자세한 내용은 [웹 애플리케이션에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL 포함]** - 사용 **[!UICONTROL 포함]** 차원 뷰어를 사용하여 웹 페이지에 포함된 Dynamic Media 3D 자산을 보려는 경우. You copy the embed code to the clipboard so you can paste it in your web pages. Editing of the is not permitted in the **[!UICONTROL Embed Code]** dialog box.

   자세한 내용은 [웹 페이지에 Dynamic Media 비디오, 이미지 뷰어 또는 차원 뷰어 포함](/help/assets/dynamic-media/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page).
