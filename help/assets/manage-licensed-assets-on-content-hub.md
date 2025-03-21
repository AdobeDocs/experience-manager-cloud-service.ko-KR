---
title: Content Hub에서 라이선스가 부여된 자산 관리
description: 에셋 메타데이터 양식에 라이선스 필드를 추가하고, 라이선스 메타데이터 속성을 에셋 폴더에 적용하고, 라이선스가 있는 에셋을 사용할 수 있도록 승인하는 방법에 대해 알아봅니다.
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 19%

---

# Content Hub에서 라이선스가 부여된 자산 관리 {#manage-licensed-assets-on-content-hub}

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

>[!AVAILABILITY]
>
>Content Hub 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE Content Hub 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

관리자는 AEM 작성 환경의 에셋 속성에 표시되도록 에셋 라이선스 필드를 포함하도록 메타데이터 양식을 편집합니다. 그런 다음 Content Hub에서 에셋에 대한 라이선스와 라이선스를 부여하고 사용 가능하게 하는 해당 라이선스를 승인할 수 있습니다.

다음 단계를 실행합니다.

1. 라이선스 세부 정보를 포함하는 새 텍스트 필드를 포함하도록 메타데이터 양식을 편집합니다. 텍스트 필드를 `dc:license` 속성에 매핑합니다. 메타데이터 양식에 필드를 추가하고 속성을 정의하는 방법에 대한 자세한 내용은 [메타데이터 Forms 설정](/help/assets/metadata-assets-view.md#metadata-forms)을 참조하십시오.
   ![zip 추출](/help/assets/assets/metadata-form-edit.png)
1. 메타데이터 양식을 에셋 폴더에 적용하여 1단계에서 통합된 설정을 적용합니다. 에셋 폴더에 메타데이터 양식을 할당하는 방법에 대한 자세한 내용은 [폴더에 메타데이터 양식 할당](/help/assets/metadata-assets-view.md#metadata-forms)을 참조하십시오.
1. [라이선스가 있는 PDF 승인](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. 자산을 선택하고 **세부 정보**&#x200B;를 클릭하여 해당 속성을 확인합니다. 1단계에서 추가된 라이선스 필드에서 3단계에서 승인되었거나 이미 이전에 승인된 에셋 라이선스의 절대 경로를 정의합니다. Content Hub 절대 경로는 다음 표준 패턴을 따릅니다. `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. 예: /content/dam/teamA/projects/documents/file1.pdf
   ![절대 경로](/help/assets/assets/absolute-path.png)
1. Content Hub에서 사용할 수 있도록 자산을 승인하고 **저장**&#x200B;을 클릭합니다. 에셋을 승인하는 방법에 대한 자세한 내용은 [에셋 상태 설정](/help/assets/manage-organize-assets-view.md#set-asset-status)을 참조하십시오.
