---
title: Content Hub에서 에셋 다운로드
description: Content Hub 포털에서 에셋을 다운로드하는 방법을 알아봅니다
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 96b7b7fe32aefc81a9fde15d79e9089f71cb5d31
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 4%

---

# Content Hub에서 에셋 다운로드 {#download-assets}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능 포함 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Download assets](assets/download-asset.jpg) -->
![자산 다운로드](assets/download-asset-genstudio.jpeg)

Content Hub을 사용하여 에셋을 다운로드하고 공유할 수 있습니다. 이러한 에셋에는 이미지, 비디오 또는 기타 디지털 콘텐츠가 포함될 수 있습니다. Content Hub은 효과적인 에셋 배포를 위해 접근성과 적응성을 향상합니다.

Content Hub을 사용하여 단일 에셋 또는 여러 에셋을 다운로드할 수 있습니다. 에셋의 원본 버전이 다운로드됩니다.

## 사전 요구 사항 {#prerequisites}

[Content Hub 사용자](deploy-content-hub.md#onboard-content-hub-users)는 이 문서에 언급된 작업을 수행할 수 있습니다.

## 에셋 다운로드 {#download-single-asset}

다운로드하기 전에 [자산 라이선스를 승인](/help/assets/approve-assets-content-hub.md)합니다.

### 단일 다운로드 {#single-download-asset}

자산을 선택하고 상단 레일에서 ![다운로드](/help/assets/assets/download-icon.svg)를 클릭합니다. 에셋 다운로드 대화 상자에 에셋의 라이센스가 표시됩니다. 라이선스 사용 약관에 동의하고 **다운로드**를 클릭합니다.
또는 에셋 카드에서 ![다운로드](/help/assets/assets/download-icon.svg)를 클릭하여 에셋을 다운로드합니다.

#### 에셋 대화 상자에서 단일 에셋 다운로드 {#single-download-from-asset-dialog-box}

1. 에셋 썸네일을 클릭합니다. 에셋 대화 상자가 표시됩니다.
1. 맨 오른쪽 도구 모음에서 ![다운로드](/help/assets/assets/download-icon.svg)를 클릭합니다. 다운로드 창에는 에셋 렌디션과 라이선스 사용 약관 수락 확인란이 표시됩니다.
   ![단일 다운로드 대화 상자](/help/assets/assets/asset-dialog-box-for-single-download.png)
   * 사용 약관 링크를 클릭하여 왼쪽 창에서 사용 약관을 확인합니다.

     >[!NOTE]
     >
     >사용 약관 확인란은 사용 허가된 자산에 대해서만 표시됩니다. 또한 에셋 대화 상자에는 승인된 라이센스가 있는 에셋에 대해서만 라이센스 약관 미리보기가 표시됩니다. 자산 대화 상자에서 라이선스 조건을 미리 보려면 다운로드하기 전에 [자산 라이선스를 승인](/help/assets/approve-assets-content-hub.md)하십시오.

   * 왼쪽 창에서 원본 에셋 렌디션으로 돌아가려면 **원본 렌디션 상자**&#x200B;를 클릭하십시오.
1. 라이선스 사용 약관에 동의하고 **다운로드**&#x200B;를 클릭하여 자산을 다운로드합니다.

### 다중 다운로드 {#multi-download}

1. 자산을 선택하고 상단 레일에서 ![다운로드](/help/assets/assets/download-icon.svg)를 클릭합니다. 표시되는 대화 상자는 다운로드 목록에 만료된 에셋이 포함되어 있는지 아니면 만료되지 않은 에셋만 포함되어 있는지에 따라 다릅니다. <br/>
   **만료된 에셋 다운로드 대화 상자:** 이 대화 상자에는 만료된 에셋의 미리 보기가 왼쪽 창에 만료 날짜와 함께 표시됩니다. 선택한 전체 중 만료된 에셋의 카운트가 오른쪽 창에 표시됩니다. 다른 에셋과 함께 만료된 에셋을 다운로드하려면 **모든 에셋으로 진행**&#x200B;을 클릭합니다(있는 경우). 에셋 다운로드 대화 상자가 표시됩니다. 계속 진행하려면 [자산 다운로드 대화 상자](#Download-asset-dialog-box)를 참조하세요.

   >[!NOTE]
   >
   >[만료된 에셋에 대한 다운로드 옵션을 사용하도록 설정](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub)합니다. 다운로드를 활성화한 만료된 에셋만 다운로드할 수 있습니다.

   <a id="Download-asset-dialog-box"></a> **에셋 다운로드 대화 상자:** 이 대화 상자는 왼쪽 창에 선택한 에셋과 관련된 라이선스 목록을 표시합니다. 라이선스를 선택하여 해당 약관(pdf 형식)을 가운데 창에서 미리 보고 관련 에셋의 미리 보기 및 개수를 오른쪽 창에서 미리 봅니다. 검토된 라이센스는 연한 파란색으로 강조 표시됩니다.

   >[!NOTE]
   >
   > **자산 다운로드 대화 상자**&#x200B;에서는 승인된 라이선스에 대한 라이선스 사용 약관만 미리 봅니다. [에셋의 라이선스를 승인](/help/assets/approve-assets-content-hub.md)한 후 다운로드하면 **에셋 다운로드 대화 상자**&#x200B;에서 라이선스 조건을 미리 볼 수 있습니다.

1. 다운로드 대화 상자에서 라이선스를 제거하려면 ![remove-icon](/help/assets/assets/remove-icon.svg)을 클릭하세요.

1. 사용 약관에 동의한 다음 **다운로드**를 클릭하여 왼쪽 창에서 사용 가능한 라이선스와 연결된 에셋을 다운로드합니다.
   ![download-multiple-license](/help/assets/assets/download-multiple-license.png)

### 라이센스가 부여되지 않은 자산 다운로드 {#download-non-licensed-assets}

라이선스가 없는 에셋을 다운로드하려면 에셋을 선택하고 상단 레일에서 ![다운로드](/help/assets/assets/download-icon.svg)를 클릭합니다.







