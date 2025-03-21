---
title: AEM 및 Dynamic Media에 빠른 게시
description: Assets 보기의 빠른 게시를 사용하면 자산을 AEM 및 Dynamic Media에 동시에 또는 별도로 게시할 수 있습니다. 에셋 및 폴더를 선택하고 Dynamic Media 또는 AEM에 게시하도록 선택할 수 있습니다.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, Dynamic Media
role: User
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 2%

---

# AEM 및 Dynamic Media에 자산 게시{#Publish-Assets-to-AEM-and-Dynamic-Media}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
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

Experience Manager Assets을 사용하면 Assets 보기를 사용하여 Experience Manager 및 Dynamic Media에 자산을 빠르게 게시할 수 있습니다. 이렇게 하면 자산을 관리한 다음 관리 보기](/help/assets/overview.md##persona-based-experiences)(으)로 전환하지 않고 [Assets 보기를 사용하여 게시할 수 있습니다.

Experience Manager Assets view에서는 자산을 AEM 또는 Dynamic Media에 게시하거나 두 가지 모두에 동시에 게시할 수 있는 유연성을 제공합니다. 에셋을 업로드하고, 탐색하고, 검색하는 동안 에셋을 게시할 수 있습니다. 자산을 게시하는 이러한 모든 옵션은 이 문서에서 자세히 설명합니다.

## 시작하기에 앞서 {#before-you-begin}

AEM 및 Dynamic Media에 대한 게시 옵션을 보려면 다음 설정을 구성하십시오.

* Dynamic Media에 대한 게시 옵션을 보려면 관리 보기를 사용하여 다음 설정을 구성합니다.

   * [Dynamic Media 클라우드 구성을 만듭니다](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * 폴더 수준에서 Dynamic Media 게시 모드를 설정합니다. Dynamic Media 클라우드 구성을 작성하는 동안 이러한 설정을 구성할 수도 있습니다. 폴더 수준에서 이러한 설정을 덮어쓰려면 [Dynamic Media의 폴더 수준에서 선택적 게시 구성](/help/assets/dynamic-media/selective-publishing.md)을 참조하십시오.

* AEM에 대한 게시 옵션을 보려면 환경에 대한 AEM 게시 끝점을 구성해야 합니다.

## 업로드 중 Assets 게시 {#piblish-assets-during-upload}

폴더에 자산을 업로드하는 동안 AEM 및 Dynamic Media에 자산을 게시할 수 있습니다. 표시되는 게시 옵션은 에셋을 업로드하는 폴더의 Dynamic Media 게시 모드 설정에 따라 다릅니다. Dynamic Media 게시 모드는 다음과 같이 설정할 수 있습니다.

* **활성화 시:** 자산이 이 폴더에 업로드되면 URL/포함 링크가 제공되기 전에 먼저 자산을 명시적으로 게시해야 합니다.

* **즉시:** 자산이 이 폴더에 업로드되면 시스템이 자산을 Experience Manager에 수집하고 URL/임베드를 즉시 제공합니다.
* **선택적 게시:** Assets은 공개 도메인에서 제공하기 위해 Experience Manager 또는 Dynamic Media 중 선택한 항목에 게시됩니다.

### 활성화 시 Dynamic Media 게시 모드가 로 설정됨 {#dynamic-media-publish-mode-set-to-upon-activation}

Dynamic Media 게시 모드가 **활성화 시**(으)로 설정된 폴더에 자산을 업로드하는 동안 자산을 게시하려면:

1. 자산을 업로드할 적절한 폴더로 이동하려면 **Assets 추가** > **찾아보기** > **파일 찾아보기**&#x200B;를 클릭하십시오. **게시 옵션** 섹션에는 **DM 게시 모드**&#x200B;가 **활성화 시**(으)로 표시됩니다.
   ![활성화 시 이미지 업로드](/help/assets/assets/upload-uactivation.svg)
2. **AEM 및 Dynamic Media에 게시**&#x200B;를 선택하고 **업로드**&#x200B;를 클릭합니다. 자산이 AEM 및 Dynamic Media에 동시에 게시됩니다. 이러한 에셋에 대해 업데이트된 게시 상태를 보려면 [게시 상태 확인](#check-publish-status)을 참조하십시오.

### Dynamic Media 게시 모드가 즉시 로 설정됨 {#dynamic-media-publish-mode-set-to-immediate}

Dynamic Media 게시 모드가 **즉시**(으)로 설정된 폴더에 자산을 업로드하는 동안 자산을 게시하려면:

1. 자산을 업로드할 적절한 폴더로 이동하려면 **Assets 추가** > **찾아보기** > **파일 찾아보기**&#x200B;를 클릭하십시오. **게시 옵션** 섹션에는 **DM 게시 모드**&#x200B;가 **즉시**(으)로 표시됩니다.
   ![파일 업로드 이미지 - 즉시 모드](/help/assets/assets/resized-image-pdf-svg-new.svg)


   Dynamic Media 게시 모드가 **즉시**&#x200B;이므로 **업로드**&#x200B;를 클릭하면 업로드된 자산이 Dynamic Media에 자동으로 게시됩니다.

2. 업로드된 자산을 AEM에 게시하려면 **AEM에 게시**&#x200B;를 선택하고 업로드 를 클릭합니다.

   **AEM에 게시**&#x200B;를 선택하면 자산이 AEM 및 Dynamic Media에 게시되고, 그렇지 않으면 자산이 Dynamic Media에 게시됩니다.

   이러한 에셋에 대해 업데이트된 게시 상태를 보려면 [게시 상태 확인](#check-publish-status)을 참조하십시오.

### Dynamic Media 게시 모드가 선택적 게시로 설정됨 {#dynamic-media-publish-mode-set-to-selective-publish}

Dynamic Media 게시 모드가 **선택적 게시**(으)로 설정된 폴더에 업로드하는 동안 자산을 게시하려면:

1. 자산을 업로드할 적절한 폴더로 이동하려면 **Assets 추가** > **찾아보기** > **파일 찾아보기**&#x200B;를 클릭하십시오. **게시 옵션** 섹션에는 **DM 게시 모드**&#x200B;가 **선택적 게시**(으)로 표시됩니다.
   ![이미지 선택적 게시 모드 업로드](/help/assets/assets/upload-selective.svg)

2. 요구 사항에 따라 **AEM에 게시**, **Dynamic Media에 게시** 또는 둘 다를 선택하고 **업로드**&#x200B;를 클릭합니다.

   에셋은 선택한 항목에 따라 AEM 및 Dynamic Media에 게시됩니다.

   이러한 에셋에 대해 업데이트된 게시 상태를 보려면 [게시 상태 확인](#check-publish-status)을 참조하십시오.

## 에셋 검색 페이지를 사용하여 에셋 게시 {#publish-assets-using-asset-browse-page}

에셋 검색 페이지를 사용하여 에셋을 게시하려면 다음 작업을 수행하십시오.

1. 왼쪽 창에 있는 **Assets 관리** 섹션에서 **Assets**&#x200B;을(를) 클릭합니다.
2. 게시해야 하는 에셋 또는 폴더를 하나 이상 선택하고 **게시**&#x200B;를 클릭합니다.
3. 자산을 AEM 및 Dynamic Media에 게시하려면 **AEM**&#x200B;을(를) 선택하고 **게시**를 클릭하십시오.
   ![자산 찾아보기](/help/assets/assets/browse-uactivation-immediate.svg)
Dynamic Media 게시 모드가 **선택적 게시로 설정된 폴더는 게시할 수 없습니다.** AEM을 선택하면 다른 모든 선택한 폴더 또는 자산이 AEM 및 Dynamic Media에 게시됩니다.
   ![자산 찾아보기](/help/assets/assets/browse-selective123.svg)

## 검색 결과 페이지를 사용하여 자산 게시 {#publish-assets-using-search-results-page}

에셋 검색 결과 페이지를 사용하여 에셋을 게시하려면 다음 작업을 수행하십시오.

1. 검색 막대에서 기준을 지정하고 검색 아이콘을 클릭하여 결과를 확인합니다.
2. 게시해야 하는 자산을 선택하고 **게시**&#x200B;를 클릭합니다.
3. 요구 사항에 따라 AEM, Dynamic Media 또는 둘 다 선택하고 **게시**를 클릭합니다.
   ![이미지 검색](/help/assets/assets/search-mode.svg)
검색 결과 페이지의 Dynamic Media에 게시하는 옵션은 저장소에서 에셋을 사용할 수 있는 폴더에 설정된 Dynamic Media 게시 모드에 따라 다릅니다.

   >[!NOTE]
   >
   >폴더를 선택하고 검색 결과 페이지에서 **게시**&#x200B;를 클릭하면 Experience Manager Assets이 폴더에 대한 Dynamic Media 게시 모드 설정에 관계없이 AEM이 아닌 Dynamic Media에 자산을 게시하는 옵션을 표시합니다.

## 게시 상태 확인 {#check-publish-status}

에셋 또는 폴더에 대해 게시된 상태를 확인하려면:

1. 왼쪽 창에 있는 **[!UICONTROL Assets 관리]** 섹션에서 **[!UICONTROL Assets]**&#x200B;을(를) 클릭합니다.
2. 보기 전환기를 사용하여 목록 보기로 전환합니다. AEM 게시, Dynamic Media 게시, 제목, 크기, 차원 등과 같은 에셋 속성을 볼 수 있습니다.\
   에셋 또는 폴더가 게시되지 않은 경우 **AEM 게시** 및 **Dynamic Media 게시** 열의 상태가 **해당 없음**으로 표시됩니다.
   ![게시 상태 확인1](/help/assets/assets/check-publish-status1.png)
목록 보기에서 AEM 게시 및 Dynamic Media 게시 열을 볼 수 없는 경우:
   1. ![설정](/help/assets/assets/settings-icon.svg)을 클릭하고 **구성 가능한 열** 대화 상자에서 **AEM 게시** 및 **Dynamic Media 게시** 열을 선택합니다.
   2. **확인을 클릭합니다.** Experience Manager Assets에서 선택한 열을 목록 보기에 추가합니다.

      ![게시 상태 확인](/help/assets/assets/check-publish-status2.png)

자산을 선택하고 **세부 정보를 클릭하여 자산 게시 상태를 확인할 수도 있습니다.** 세부 정보는 오른쪽 창의 **게시** 섹션에서 사용할 수 있습니다. **게시** 섹션에는 자산이 Dynamic Media 및 AEM에 게시되는 날짜가 나열됩니다. 에셋이 게시되는 시간을 확인해야 하는 경우 목록 보기로 이동하여 해당 세부 정보를 볼 수 있습니다.

![게시 상태 확인](/help/assets/assets/check-publish-status3.png)

## 제한 사항 {#limitations}

AEM 및 Dynamic Media에 자산을 게시하는 동안 현재 다음 기능은 사용할 수 없습니다.

* 자산 세부 사항 페이지에서 AEM 및 Dynamic Media에 자산을 게시합니다.
* 빠른 게시 마법사를 사용하여 자산이 게시되는 끝점을 시각화합니다.
* 빠른 게시 마법사에서 더 많은 에셋을 추가하거나 삭제합니다.
* 게시된 자산을 볼 수 있는 페이지입니다.
* 에셋 수준(에셋이 Dynamic Media에 게시되는 경우)에서 Dynamic Media URL을 복사하거나 붙여넣는 기능입니다.
* AEM에 게시하는 동안 참조(에셋, 태그 등)를 게시하는 기능.
* 폴더 수준에서 Dynamic Media 동기화 상태를 덮어쓰는 기능.
* 폴더 수준에서 Dynamic Media 게시 모드를 덮어쓰는 기능
* 게시 관리는 아직 지원되지 않습니다.
