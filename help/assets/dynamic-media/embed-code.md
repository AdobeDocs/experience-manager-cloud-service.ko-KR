---
title: 웹 페이지에 Dynamic Media 비디오 또는 이미지 뷰어 포함
description: 웹 페이지에 Dynamic Media 비디오 또는 이미지 자산을 포함하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 76335781-e39f-4aae-967f-5af8634d8f61
source-git-commit: b37ff72dbcf85e5558eb3421b5168dc48e063b47
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 21%

---

# 웹 페이지에 Dynamic Media 비디오, 이미지 뷰어 또는 차원 뷰어 포함 {#embedding-the-video-or-image-viewer-on-a-web-page}

Use the **[!UICONTROL Embed Code]** feature when you want to play the video or view an asset embedded on a web page. You copy the embed code to the clipboard so you can paste it in your web pages. Editing of the code is not permitted in the **[!UICONTROL Embed Code]** dialog box.

Adobe Experience Manager을 WCM으로 사용하여 _not_&#x200B;하는 경우에만 URL을 포함합니다. Experience Manager을 WCM으로 사용하는 경우 [에셋을 페이지에서 바로 추가](adding-dynamic-media-assets-to-pages.md)합니다.

[웹 응용 프로그램에 URL 연결](linking-urls-to-yourwebapplication.md)을 참조하십시오.

[응답형 사이트에 최적화된 이미지 제공](responsive-site.md)을 참조하십시오.

>[!NOTE]
>
>포함 코드는 선택한 자산을 게시하기 전까지 복사할 수 없습니다. 또한 뷰어 사전 설정 또는 이미지 사전 설정도 게시해야 합니다.
>
>[Publish Assets](publishing-dynamicmedia-assets.md)을(를) 참조하십시오.
>
>[Publish 뷰어 사전 설정](managing-viewer-presets.md#publishing-viewer-presets)을 참조하세요.
>
>[Publish 이미지 사전 설정](managing-image-presets.md#publishing-image-presets)을 참조하세요.

**웹 페이지에 Dynamic Media 비디오 또는 이미지 뷰어를 포함하려면:**

1. 포함 코드를 복사할 *게시된* 비디오 또는 이미지 자산으로 이동합니다.

   Remember that the embed code is only available to copy *after* you have first *published* the assets. In addition, the viewer preset or image preset must also be published.

   [Publish Assets](publishing-dynamicmedia-assets.md)을(를) 참조하십시오.

   [Publish 뷰어 사전 설정](managing-viewer-presets.md#publishing-viewer-presets)을 참조하세요.

   [Publish 이미지 사전 설정](managing-image-presets.md#publishing-image-presets)을 참조하세요.

1. 왼쪽 레일에서 드롭다운 목록을 선택하고 **[!UICONTROL 뷰어]**&#x200B;를 선택합니다.
1. 왼쪽 레일에서 뷰어 사전 설정 이름을 선택합니다. 뷰어 사전 설정이 자산에 적용됩니다.
1. **[!UICONTROL 포함]**&#x200B;을 선택하세요.
1. **[!UICONTROL 포함 코드]** 대화 상자에서 전체 코드를 클립보드에 복사한 다음 **[!UICONTROL 닫기]**&#x200B;를 선택합니다.
1. 웹 페이지에 포함 코드를 붙여넣습니다.

## HTTP/2를 사용하여 Dynamic Media 에셋 전달 {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2는 새로운 업데이트된 웹 프로토콜로서 브라우저와 서버의 통신 방식을 개선합니다. 정보 전송 속도를 높이고 필요한 처리 능력을 줄일 수 있습니다. 이제 Dynamic Media 에셋의 전달이 HTTP/2를 통해 가능해져 응답 및 로드 시간이 향상됩니다.

Dynamic Media 계정으로 HTTP/2를 사용하는 방법에 대한 자세한 내용은 [컨텐츠의 HTTP2 전달](http2faq.md)을 참조하십시오.
