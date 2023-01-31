---
title: 반응형 사이트에 최적화된 이미지 제공
description: 반응형 코드 기능을 사용하여 Dynamic Media에서 최적화된 이미지를 전달하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 62af6f3f-9c86-44ad-870d-140f572f99c5
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 15%

---

# 반응형 사이트에 최적화된 이미지 제공 {#delivering-optimized-images-for-a-responsive-site}

웹 개발자와 응답형 서비스를 위한 코드를 공유하려면 응답형 코드 기능을 사용하십시오. 응답형(**[!UICONTROL RESS]**) 코드를 클립보드에 복사하여 웹 개발자와 공유할 수 있습니다.

웹 사이트가 타사 WCM에 있는 경우 이 기능을 사용하는 것이 적절합니다. 그러나 웹 사이트가 대신 Adobe Experience Manager에 있는 경우 오프사이트 이미지 서버가 이미지를 렌더링하여 웹 페이지에 제공합니다.

참조 - [웹 페이지에 비디오 뷰어 포함](embed-code.md).

참조 - [웹 애플리케이션에 URL 연결](linking-urls-to-yourwebapplication.md).

**응답형 사이트용으로 최적화된 이미지를 전달하려면:**

1. 및 의 응답형 코드를 제공할 이미지로 이동하여 드롭다운 메뉴에서 을 선택합니다 **[!UICONTROL 표현물]**.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Select a responsive image preset. The **[!UICONTROL URL]** and **[!UICONTROL RESS]** buttons appear.

   ![chlimage_1-409](assets/chlimage_1-409.png)

   >[!NOTE]
   >
   >The selected asset *and* the selected image preset or viewer preset must be published to make the **[!UICONTROL URL]** or **[!UICONTROL RESS]** buttons available.
   >
   >이미지 사전 설정이 자동으로 게시됩니다.

1. 선택 **[!UICONTROL RESS]**.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. 에서 **[!UICONTROL 응답형 이미지 포함]** 대화 상자를 선택하고, 응답형 코드 텍스트를 복사하여 웹 사이트에 붙여넣어 응답형 자산에 액세스합니다.
1. 포함 코드의 기본 중단점을 편집하여 코드에서 직접 응답형 웹 사이트에 있는 중단점과 일치합니다. 또한 다른 페이지 중단점에서 제공되는 다양한 이미지 해상도를 테스트합니다.

## HTTP/2를 사용하여 Dynamic Media 자산 전달 {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2는 브라우저 및 서버의 통신 방식을 향상시키는 업데이트된 새로운 웹 프로토콜입니다. 보다 신속하게 정보를 전송할 수 있고 필요한 처리 능력을 줄일 수 있습니다. Dynamic Media 자산의 배달은 HTTP/2를 사용하여 지원되며, 이 경우 더 나은 응답 및 로드 시간이 제공됩니다.

자세한 내용은 [컨텐츠의 HTTP2 전달](http2faq.md) Dynamic Media 계정으로 HTTP/2 사용을 시작하는 방법에 대한 전체 세부 사항을 살펴보십시오.
