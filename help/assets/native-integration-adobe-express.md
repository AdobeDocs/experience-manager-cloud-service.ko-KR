---
title: Adobe Express과 AEM Assets 기본 통합
description: Adobe Express과 AEM Assets 기본 통합을 사용하면 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 직접 액세스할 수 있습니다.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: 3046da6d16b2494f6a3f18c60df7a4600afcd7ba
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 14%

---

# Adobe Express와의 네이티브 통합 {#native-integration-adobe-express}

AEM Assets는 Adobe Express에 기본적으로 통합되므로 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 직접 액세스할 수 있습니다. AEM Assets에서 관리되는 콘텐츠를 Express 캔버스에 배치한 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다. 통합은 다음과 같은 주요 이점을 제공합니다.

* AEM에서 새 자산을 편집하고 저장하여 콘텐츠 재사용을 개선했습니다.

* 새 에셋을 만들거나 기존 에셋의 새 버전을 만드는 데 드는 전반적인 시간과 노력이 감소했습니다.

## 사전 요구 사항 {#prerequisites}

Adobe Express 및 AEM Assets 내 하나 이상의 환경에 액세스할 수 있는 권한. 환경은 Assets as a Cloud Service 또는 Assets Essentials 내에 있는 저장소 중 하나일 수 있습니다.

## Adobe Express 편집기 내 AEM Assets 사용 {#use-aem-assets-in-express}

Adobe Express 편집기에서 AEM Assets을 사용하려면 다음 단계를 수행하십시오.

1. Adobe Express 웹 애플리케이션을 엽니다.

2. 새 템플릿 또는 프로젝트를 로드하거나 에셋을 만들어 새 빈 캔버스를 엽니다.

3. 왼쪽 탐색 창에서 사용할 수 있는 **[!UICONTROL Assets]**&#x200B;을(를) 클릭합니다. Adobe Express은 루트 수준에서 사용할 수 있는 에셋 및 폴더 목록과 함께 액세스할 수 있는 저장소 목록을 표시합니다.

4. 저장소에서 에셋을 찾아보거나 검색한 다음 캔버스로 드래그하여 놓습니다. 또는 에셋을 클릭하여 캔버스에 배치합니다. 파일 유형, MIME 유형 및 차원과 같은 다양한 기준으로 자산을 필터링할 수도 있습니다.

   >[!NOTE]
   >
   >차원으로 필터링은 비디오에 적용되지 않습니다.

   ![Assets 추가 기능에서 자산 포함](assets/adobe-express-native-integration.png)

### AEM 업로드를 사용하여 이미지 바꾸기 {#replace-image-using-aem-upload}

또한 **[!UICONTROL AEM 업로드]**&#x200B;를 사용하여 추가된 이미지를 바꿀 수 있습니다. 이렇게 하려면 다음 단계를 실행합니다.

1. 에셋을 찾아보거나 검색하고 캔버스로 드래그 앤 드롭합니다.

1. 바꿀 이미지를 선택합니다. **[!UICONTROL 바꾸기]**&#x200B;를 클릭하고 다양한 옵션 중 **[!UICONTROL AEM Assets]**&#x200B;을(를) 선택합니다.

   ![AEM 바꾸기](assets/aem-replace.png)

1. 왼쪽 탐색 창에서 **[!UICONTROL AEM 업로드]** 패널이 열립니다. Adobe Express은 루트 수준에서 사용할 수 있는 에셋 및 폴더 목록과 함께 액세스할 수 있는 저장소 목록을 표시합니다. 캔버스에서 대체 항목을 미리 보려면 에셋을 선택한 다음 **[!UICONTROL 바꾸기]**&#x200B;를 클릭하여 확인합니다.

   >[!NOTE]
   >
   > SVG 파일 유형은 지원되지 않습니다.

## AEM Assets에 Adobe Express 프로젝트 저장 {#save-express-projects-in-assets}

빠른 캔버스에서 적절한 수정 사항을 통합한 후 AEM Assets 저장소에 저장할 수 있습니다.

1. **[!UICONTROL 공유]**&#x200B;를 클릭하여 **[!UICONTROL 공유]** 대화 상자를 엽니다.

   ![AEM에 자산 저장](assets/adobe-express-share.png)

2. 오른쪽 창의 **[!UICONTROL 권장]** 섹션에서 **AEM Assets**&#x200B;을(를) 선택합니다. Adobe Express에 업로드 대화 상자가 표시됩니다.

   ![AEM에 자산 저장](assets/adobe-express-aem.png)

3. **현재 페이지** 또는 **모든 페이지**를 선택하십시오. 내보낼 자산의 이름과 형식을 지정합니다. 캔버스 컨텐츠를 PNG, JPEG, PDF, MP4, MP4+PNG 또는 MP4+JPEG 형식으로 내보낼 수 있습니다. 캔버스 페이지의 자산에 따라 형식이 자동으로 조정됩니다.
**현재 페이지**&#x200B;을(를) 선택하면 현재 페이지의 자산이 대상 폴더에 저장됩니다. **모든 페이지**&#x200B;를 선택했는데 내보내기 형식이 PDF이 아닌 경우, 모든 캔버스 페이지는 대상 폴더 내의 새 폴더에 별도의 파일로 저장됩니다. 내보내기 형식이 PDF인 경우, 모든 캔버스 페이지는 대상 폴더에 단일 PDF 파일로 저장됩니다.

4. **대상 폴더** 아래의 폴더 아이콘을 클릭하여 위치를 선택하고 에셋을 저장합니다.

   ![AEM에 자산 저장](/help/assets/assets/page-selection-and-destination-folder.svg)

5. 선택 사항: **프로젝트 또는 캠페인 이름** 필드를 사용하여 업로드할 캠페인 메타데이터를 추가할 수 있습니다. 기존 이름을 사용하거나 새 이름을 만들 수 있습니다. 업로드할 여러 프로젝트 또는 캠페인 이름을 정의할 수 있습니다. 이름을 등록하려면 이름을 입력하고 enter 키를 누릅니다.
Adobe에서는 업로드한 에셋에 대해 향상된 검색 환경을 만들 뿐만 아니라 나머지 필드에 값을 지정하는 것을 가장 좋습니다.

6. 마찬가지로 **[!UICONTROL 키워드]** 및 **[!UICONTROL 채널]** 필드에 대한 값을 정의하십시오.

7. 자산을 AEM Assets에 업로드하려면 **[!UICONTROL 업로드]**&#x200B;를 클릭하십시오.

<table> 
    <tbody>
     <tr>
      <th><strong>지원되는 형식</strong></th>
      <th><strong>크기</strong></th>
     </tr>
    </tr>
    <tr>
        <td>[!UICONTROL JPEG]</td>
        <td> 65MP(예: 8K x 8K 또는 16K x 4K) </td>
    </tr>
    <tr>
        <td>[!UICONTROL PNG]</td>
        <td> 65MP(예: 8K x 8K 또는 16K x 4K) </td>
    </tr>
    <tr>
        <td>[!UICONTROL SVG]</td>
        <td> 최대 250KB</td>
    </tr>
    <tr>
        <td>[!UICONTROL MP4]</td>
        <td> 3840 X 3840픽셀, 최대 200MB</td>
    </tr>
    <tr>
      <td colspan="2"> <i> 자산 크기는 데스크톱 장치의 경우 80MB 미만이어야 하며 모바일 장치의 경우 40MB여야 합니다. </i></td>
   </tr>
    </tbody>
</table>

## 제한 사항 {#limitations}

1. 가져오기 및 내보내기의 경우 지원되는 비디오 파일 유형은 MP4입니다.

2. **MP4 비디오 가져오기**&#x200B;의 경우 배경이 투명한 비디오(알파 채널)가 지원되지 않습니다.
   <!--
   1. The maximum file size supported is 200 MB. If this limit exceeds, an alert message displays.
   2. The maximum supported resolution is 3840 X 3840 pixels.
   3. Videos with transparent backgrounds (alpha channel) are not supported.
   -->

3. **MP4 비디오 내보내기**&#x200B;의 경우 지원되는 최대 파일 크기는 200MB입니다. 이 제한이 초과되면 경고에 따라 비디오를 200MB 이하로 자르거나, 다운로드한 후 AEM Assets 대상 폴더에 수동으로 업로드해야 합니다.



