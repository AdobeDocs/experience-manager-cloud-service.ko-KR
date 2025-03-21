---
title: Dynamic Media의 핫링크 보호 활성화
description: Dynamic Media에서 핫링크 보호를 활성화하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 0198b3a3-173e-46ca-a845-3f58f8eab769
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 13%

---

# Dynamic Media의 핫링크 보호 활성화 {#activating-hotlink-protection-in-dynamic-media}

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

핫 연결은 서드파티 웹 사이트가 HTML 코드를 사용하여 웹 사이트의 이미지를 표시하는 것입니다. 방문자의 브라우저가 서버에서 바로 액세스하고 있으므로 그림이 요청될 때마다 대역폭을 사용합니다. 핫링크 *보호*&#x200B;는 다른 웹 사이트가 웹 페이지의 사진, CSS 또는 JavaScript에 직접 연결되는 것을 방지하는 방법입니다. 이러한 종류의 실드는 Dynamic Media 계정에서 불필요한 대역폭 사용을 줄이는 데 도움이 됩니다.

[Adobe 고객 지원 센터](https://experienceleague.adobe.com/?support-solution=Experience+Manager#home)는 CDN 수준에서 레퍼러 필터를 구성할 수 있습니다. 이렇게 하면 도메인에 대해 허용된 웹 사이트 목록의 웹 사이트에만 Dynamic Media 콘텐츠가 제공됩니다.

>[!NOTE]
>
>이 기능을 사용하려면 Adobe Experience Manager Dynamic Media와 번들로 제공되는 기본 CDN을 사용해야 합니다. 다른 모든 사용자 지정 CDN은 이 기능에서 지원되지 않습니다. 핫 링크 보호를 활성화하려면 관리자가 Dynamic Media 계정에 대한 구성 변경을 요청할 수 있도록 지원 티켓을 만들어야 합니다. 핫 링크 보호를 활성화하는 데 드는 추가 비용은 없습니다.
