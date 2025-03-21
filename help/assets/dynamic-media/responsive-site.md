---
title: 반응형 사이트에 최적화된 이미지 게재
description: 반응형 코드 기능을 사용하여 Dynamic Media에서 최적화된 이미지를 전달하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 62af6f3f-9c86-44ad-870d-140f572f99c5
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 18%

---

# 반응형 사이트에 최적화된 이미지 게재 {#delivering-optimized-images-for-a-responsive-site}

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

반응형 서비스용 코드를 웹 개발자와 공유하려면 반응형 코드 기능을 사용하십시오. 웹 개발자와 공유할 수 있도록 응답형(**[!UICONTROL RESS]**) 코드를 클립보드에 복사합니다.

이 기능은 웹 사이트가 타사 WCM에 있는 경우 사용하는 것이 적절합니다. 그러나 웹 사이트가 대신 Adobe Experience Manager에 있는 경우 오프사이트 이미지 서버가 이미지를 렌더링하여 웹 페이지에 제공합니다.

[웹 페이지에 비디오 뷰어 포함](embed-code.md)도 참조하세요.

[웹 응용 프로그램에 URL 연결](linking-urls-to-yourwebapplication.md)도 참조하세요.

**응답형 사이트에 최적화된 이미지를 전달하려면:**

1. 응답형 코드를 제공할 이미지로 이동한 다음 드롭다운 메뉴에서 **[!UICONTROL 표현물]**&#x200B;을 선택합니다.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Select a responsive image preset. The **[!UICONTROL URL]** and **[!UICONTROL RESS]** buttons appear.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >The selected asset *and* the selected image preset or viewer preset must be published to make the **[!UICONTROL URL]** or **[!UICONTROL RESS]** buttons available.
   >
   >이미지 사전 설정은 자동으로 게시됩니다.

1. **[!UICONTROL RESS]**&#x200B;을(를) 선택합니다.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. **[!UICONTROL 응답형 이미지 포함]** 대화 상자에서 선택한 후 응답형 코드 텍스트를 복사하여 웹 사이트에 붙여넣어 응답형 자산에 액세스합니다.
1. 포함 코드의 기본 중단점을 편집하여 응답형 웹 사이트에 있는 것과 코드 내에서 직접 일치시킵니다. 또한 다양한 페이지 중단점에서 제공되는 다양한 이미지 해상도를 테스트합니다.

## HTTP/2를 사용하여 Dynamic Media 에셋 게재 {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2는 새로운 업데이트된 웹 프로토콜로서 브라우저와 서버의 통신 방식을 개선합니다. 정보 전송 속도를 높이고 필요한 처리 능력을 줄일 수 있습니다. Dynamic Media 에셋의 전달은 더 나은 응답 및 로드 시간을 제공하는 HTTP/2를 사용하여 지원됩니다.

Dynamic Media 계정으로 HTTP/2를 사용하는 방법에 대한 자세한 내용은 [HTTP2 컨텐츠 배달](http2faq.md)을 참조하십시오.
