---
title: 반응형 사이트에 최적화된 이미지 제공
description: 반응형 코드 기능을 사용하여 Dynamic Media에서 최적화된 이미지를 전달하는 방법을 살펴볼 수 있습니다.
translation-type: tm+mt
source-git-commit: fd75af0bf0c16e20c3b98703af14f329ea6c6371
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 3%

---


# 응답형 사이트용으로 최적화된 이미지 제공 {#delivering-optimized-images-for-a-responsive-site}

웹 개발자와 응답형 서비스를 위해 코드를 공유하려는 경우 응답형 코드 기능을 사용합니다. 응답형(**[!UICONTROL RESS]**) 코드를 클립보드에 복사하여 웹 개발자와 공유할 수 있습니다.

이 기능은 웹 사이트가 타사 WCM에 있는 경우에 사용하는 것이 적절합니다. 그러나 웹 사이트가 AEM에 있는 경우 오프사이트 이미지 서버는 이미지를 렌더링하여 웹 페이지에 제공합니다.

웹 페이지에 비디오 뷰어 포함을 참조하십시오.[](embed-code.md)

[웹 응용 프로그램에 URL 연결을 참조하십시오.](linking-urls-to-yourwebapplication.md)

**반응형 사이트에 최적화된 이미지를 제공하려면 다음을 수행하십시오**.

1. 응답형 코드를 제공할 이미지로 이동하고 드롭다운 메뉴에서 **[!UICONTROL 표현물]**&#x200B;을 누릅니다.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. 반응형 이미지 사전 설정을 선택합니다. **[!UICONTROL URL]** 및 **[!UICONTROL RESS]** 단추가 나타납니다.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >**[!UICONTROL URL]** 또는 **[!UICONTROL RESS]** 단추를 사용할 수 있도록 선택한 자산 *과*&#x200B;선택한 이미지 사전 설정 또는 뷰어 사전 설정을 게시해야 합니다.
   >
   >이미지 사전 설정은 자동으로 게시됩니다.

1. **[!UICONTROL RESS]**&#x200B;를 누릅니다.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. **[!UICONTROL 응답형 이미지 포함]** 대화 상자에서 응답형 코드 텍스트를 선택하고 복사하여 웹 사이트에 붙여 넣어 응답형 자산에 액세스합니다.
1. 포함 코드의 기본 중단점을 코드에서 직접 응답형 웹 사이트의 중단점과 일치하도록 편집합니다. 또한 다양한 페이지 중단점에서 제공되는 다양한 이미지 해상도를 테스트할 수 있습니다.

## HTTP/2를 사용하여 Dynamic Media 에셋 {#using-http-to-delivery-your-dynamic-media-assets} 전달

HTTP/2는 브라우저와 서버의 통신 방식을 향상시키는 업데이트된 새로운 웹 프로토콜입니다. 정보를 빠르게 전송할 수 있고 필요한 처리 능력을 줄일 수 있습니다. 더 나은 응답 및 로드 시간을 제공하는 HTTP/2를 사용하여 Dynamic Media 에셋 배달을 지원합니다.

Dynamic Media 계정에서 HTTP/2 사용을 시작하는 방법에 대한 자세한 내용은 [HTTP2 콘텐츠 배달](http2faq.md)을 참조하십시오.
