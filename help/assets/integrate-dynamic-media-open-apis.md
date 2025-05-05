---
title: 다운스트림 애플리케이션과 AEM Assets 통합
description: 다운스트림 애플리케이션과 AEM Assets 통합
role: User
exl-id: abd48b5d-2b43-453c-8eb6-31ff509245ca
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 33%

---

# 다운스트림 애플리케이션과 AEM Assets 통합 {#integrate-dynamic-media-open-apis}

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
>OpenAPI 기능이 포함된 Dynamic Media 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE OpenAPI 기능이 포함된 Dynamic Media 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Experience Manager 자산 저장소에서 사용할 수 있는 [승인된 모든 자산](/help/assets/approve-assets.md)을 다운스트림 애플리케이션에 전달할 수 있습니다.

검색 및 게재 API를 사용하여 자체 사용자 지정 사용자 인터페이스를 Experience Manager Assets 저장소와 통합하거나 Adobe의 Micro-Frontend 자산 선택기를 사용할 수 있습니다.

![AEM Assets 리포지토리와 통합](assets/asset-selector-integration.png)

API를 사용하면 AEM Assets 저장소에서 승인된 에셋을 검색한 다음 배달 URL을 사용하여 다운스트림 애플리케이션에 에셋을 게재할 수 있습니다. 자세한 내용은 [검색](/help/assets/search-assets-api.md) 및 [배달](/help/assets/deliver-assets-apis.md) API를 참조하십시오.

Adobe의 Micro-Frontend 자산 선택기는 [!DNL Experience Manager Assets as a Cloud Service] 리포지토리와 쉽게 통합되는 사용자 인터페이스를 제공하므로 리포지토리에서 사용할 수 있는 승인된 디지털 자산을 찾아보거나 검색하고 응용 프로그램 작성 환경에서 사용할 수 있습니다. 자세한 내용은 [Micro-Frontend 자산 선택기](/help/assets/overview-asset-selector.md)를 참조하십시오.

>[!MORELIKETHIS]
>
>* [자산 선택기와 다양한 애플리케이션 통합](/help/assets/integrate-asset-selector.md)
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [자산 선택기 사용자 지정](/help/assets/asset-selector-customization.md)
