---
title: ' [!DNL Admin View] 에서  [!DNL Assets View](으)로 메타데이터 양식 가져오기'
description: 이 문서에서는  [!DNL Admin View] 부터 [!DNL Assets View]까지 메타데이터 양식을 가져오는 방법에 대해 설명합니다.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 5fb4fe97-486a-4a91-af60-a7182efcc2f9
source-git-commit: fdd74e4d9b74600fd462e951046abfb1bb8e203b
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 8%

---

# [!DNL Admin View]에서 [!DNL Assets View]&#x200B;(으)로 메타데이터 양식 가져오기 {#import-metadata-forms-from-admin-view-to-assets-view}

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

[!DNL Adobe Experience Manager Assets]을(를) 사용하면 메타데이터 양식과 해당 폴더 연결을 [!DNL Admin View]에서 [!DNL Assets View]&#x200B;(으)로 가져올 수 있습니다.

## 시작하기에 앞서{#prerequisites-for-importing-metadata-forms-to-assets-view}

[!DNL Admin View]에서 [!DNL Assets View]&#x200B;(으)로 메타데이터 양식 및 해당 폴더 연결을 가져올 수 있는 관리자 권한이 있는지 확인하십시오.

## 메타데이터 양식을 [!DNL Assets View]&#x200B;(으)로 가져오기{#import-metadata-forms-to-assets-view}

관리자는 [!DNL Admin View]에서 사용 가능한 메타데이터 양식을 [!DNL Assets View]&#x200B;(으)로 가져오려면 다음 단계를 수행하십시오.

1. [!DNL Assets View] 홈 페이지로 이동하고 **[!UICONTROL 설정]**&#x200B;에서 **[!UICONTROL 메타데이터 Forms]**&#x200B;을(를) 클릭하여 [!DNL Assets View]에서 사용할 수 있는 메타데이터 양식 목록을 표시하는 **[!UICONTROL 메타데이터 Forms]** 페이지를 엽니다.

   ![메타데이터 양식 페이지](/help/assets/assets/metadata-forms-page.png)

1. **[!UICONTROL 가져오기]**&#x200B;를 선택하면 처리 메시지가 표시됩니다(예: *2개 메타데이터 양식 처리 중...). 잠시 기다려 주십시오.*) 가져오기를 진행하는 동안. 처리가 완료되면 [!DNL Admin View]에서 사용할 수 있는 메타데이터 양식 목록이 포함된 **[!UICONTROL 메타데이터 양식 가져오기]** 테이블이 표시됩니다. 테이블 행에는 메타데이터 양식 이름(**[!UICONTROL 이름]** 아래), 해당 양식과 연결된 폴더(**[!UICONTROL 폴더 연결]** 아래) 및 양식을 가져오기 전에 ![미리 보기](/help/assets/assets/Preview.svg) 옵션을 포함합니다.

   ![메타데이터 Forms 페이지 가져오기](/help/assets/assets/import-metadata-forms-page.png)

   >[!NOTE]
   > 
   > **[!UICONTROL 메타데이터 가져오기 Forms]**&#x200B;에서 양식 이름 옆에 있는 **[!UICONTROL 복제]** 레이블을 표로 표시하면 양식이 [!DNL Assets View]의 폴더에 이미 적용되었음을 나타냅니다. 해당 중복 양식을 가져오면 폴더에 적용된 기존 양식이 무시됩니다. 이러한 재정의를 방지하려면 양식을 가져오기 전에 이름을 바꾸십시오. 이름을 변경하려면 양식 이름을 클릭합니다.

1. [!UICONTROL 폴더 연결] 아래의 폴더 이름 옆에 있는 ![폴더 선택](/help/assets/assets/x.svg)을 클릭하여 양식과 연결된 폴더를 제거합니다.
1. 해당 메타데이터 양식을 할당할 폴더를 선택하려면 ![폴더 선택](/help/assets/assets/add-to-folder.svg)을 클릭하십시오.
1. 가져오기에서 제외된 양식에서 지원되지 않는 메타데이터 구성 요소 또는 매핑에 대한 세부 정보를 보려면 빨간색 원을 클릭하십시오.

   ![메타데이터 Forms 페이지 가져오기](/help/assets/assets/unsupported-import-elements.png)

1. 테이블에서 하나 이상의 양식을 선택하고 **[!UICONTROL 가져오기 시작]**&#x200B;을 클릭하여 메타데이터 양식 및 관련 폴더를 [!DNL Assets View]&#x200B;(으)로 가져옵니다. 처리 메시지가 표시됩니다(예: *3개의 메타데이터 양식을 가져오는 중). 기다려 주십시오!*). 가져오기가 완료되면 양식을 성공적으로 가져왔음을 확인하는 메시지가 나타나고 [!DNL Assets View]의 **[!UICONTROL 메타데이터 Forms]** 페이지에 [!DNL Assets View]에서 사용 가능한 최근에 가져온 양식과 기존 양식이 모두 표시됩니다. 이 페이지에서 다음 작업을 수행할 수 있습니다.

   * [!UICONTROL 이름], [!UICONTROL 수정됨] 또는 [!UICONTROL 작성자]별로 테이블을 정렬하려면 열 헤더를 클릭하십시오.
   * 가져온 양식을 선택하고 **[!UICONTROL 폴더에서 제거]**를 클릭한 다음 폴더 경로에서 폴더 이름을 확인하여 폴더가 올바르게 포팅되었는지 확인하십시오.
     ![메타데이터 양식 페이지 확인](/help/assets/assets/confirm-ported-folder.png)
   * 가져온 양식을 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭하여 메타데이터 양식의 지원되는 모든 구성을 봅니다. 메타데이터 양식, 구성 요소 및 필드에 대한 자세한 내용은 [메타데이터 Forms 설정](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/metadata#metadata-forms)을 참조하십시오.

   ![메타데이터 양식 페이지 확인](/help/assets/assets/verify-metadata-forms-page.png)

## 가져온 메타데이터 양식 확인{#Verify-the-imported-metadata-forms}

[!DNL Admin View]에서 [!DNL Assets View]&#x200B;(으)로 메타데이터 양식을 가져온 후 다음 단계에 따라 가져오기를 확인하십시오.

1. 가져온 메타데이터 양식의 관련 폴더로 이동합니다.
1. [자산의 세부 정보 페이지](/help/assets/navigate-assets-view.md#preview-assets)(으)로 이동하여 지원되는 메타데이터 구성 요소, 구성 요소 필드 및 필드 값이 [!DNL Admin View]에서 동기화되었는지 확인하십시오. 메타데이터 구성 요소, 구성 요소 필드 및 필드 값에 대한 자세한 내용은 [Assets Essentials의 메타데이터](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/metadata) 문서를 참조하십시오.

   >[!NOTE]
   >
   > [[!DNL Assets View] 세부 정보 페이지](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/metadata-assets-view#metadata-forms) 또는 [[!DNL Admin View] 속성 페이지](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/metadata-schemas)에서 메타데이터 속성 값에 대한 변경 내용은 두 인터페이스 간에 자동으로 동기화됩니다. 그러나 필드를 추가 또는 제거하거나 기타 수정 사항과 같은 양식의 구조적 변경 사항은 동기화되지 않습니다.
