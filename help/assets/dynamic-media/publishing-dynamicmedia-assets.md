---
title: Dynamic Media 자산 게시
description: URL 또는 웹 페이지의 포함 코드를 통해 웹 페이지에 포함할 수 있도록 Dynamic Media 비디오 및 이미지 에셋을 게시하는 방법에 대해 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 8ee759dc-cb8f-4e80-8175-2c3ba06da862
source-git-commit: 0e452bd94d75609ecc3c20ab6b56ded968ed0a70
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 4%

---

# Dynamic Media 자산 게시 {#publishing-dynamic-media-assets}

이미 업로드한 자산을 선택하고 을 선택하여 Dynamic Media 자산을 게시합니다 **[!UICONTROL 게시]** 또는 **[!UICONTROL 빠른 게시]**. Dynamic Media 자산이 게시된 후 URL을 통해 또는 페이지에 코드를 포함하여 웹 페이지에 포함할 수 있습니다.

또한 업로드한 에셋을 사용자의 개입 없이 즉시 게시할 수 있습니다. 또는 이러한 에셋을 선택적으로 게시할 수 있습니다. 다음을 참조하십시오 [Dynamic Media 구성](config-dm.md). 또는 를 사용하여 상호 배타적으로 Dynamic Media 또는 Adobe Experience Manager에 자산을 선택적으로 게시할 수 있습니다 **[!UICONTROL 선택적 게시]** 폴더 수준에서. 다음을 참조하십시오 [Dynamic Media에서 선택적 게시 작업](/help/assets/dynamic-media/selective-publishing.md).

다음에서 **[!UICONTROL 카드 보기]**, 작은 지구본 아이콘이 에셋의 이름 바로 아래에 나타나며 날짜 및 시간 왼쪽에 게시되었음을 나타냅니다. In the **[!UICONTROL List View]**, a **[!UICONTROL Published]** column indicates which assets are published or which are not.

>[!NOTE]
>
>에셋이 이미 게시된 경우 에셋을 다른 폴더로 이동하고 새 위치에서 다시 게시하면 새로 다시 게시된 에셋과 함께 원래 게시된 에셋 위치를 계속 사용할 수 있습니다. 그러나 원래 게시된 에셋은 Experience Manager에게 &quot;유실&quot;되며 게시를 취소할 수 없습니다. 따라서 자산을 다른 폴더로 이동하기 전에 먼저 게시를 취소하는 것이 좋습니다.

비디오 에셋을 인코딩한 후 바로 게시하려면 인코딩이 수행되었는지 확인하십시오. 비디오가 인코딩되고 있으면 시스템에서 비디오 처리 워크플로우가 진행 중임을 알려줍니다. 비디오 인코딩이 완료되면 비디오 렌디션을 미리 볼 수 있습니다. 이때 게시 오류가 발생하지 않고 비디오를 게시해도 안전합니다.

참조: [웹 애플리케이션에 URL 연결](linking-urls-to-yourwebapplication.md).

참조: [웹 페이지에 Dynamic Media 비디오 뷰어 또는 이미지 뷰어 포함](embed-code.md).

>[!NOTE]
>
>* URL을 사용하려면 자산을 게시해야 합니다. 에셋이 게시되지 않은 경우 URL을 복사하고 웹 브라우저에 붙여넣을 수 없습니다.
>* 라이브 게재를 위해서는 이미지 사전 설정 및 뷰어 사전 설정을 활성화하고 게시해야 합니다.
>

집합 또는 에셋 게시에 대한 자세한 내용은 [자산 게시](/help/assets/manage-digital-assets.md).

## Dynamic Media 자산의 HTTP/2 전달 {#http-delivery-of-dynamic-media-assets}

이제 Experience Manager은 HTTP/2를 통해 모든 Dynamic Media 컨텐츠(이미지 및 비디오)의 전달을 지원합니다. 즉, 이미지 또는 비디오에 대한 게시된 URL 또는 포함 코드를 호스팅된 에셋을 허용하는 모든 애플리케이션과 통합할 수 있습니다. 그런 다음 게시된 에셋은 HTTP/2 프로토콜을 통해 전달됩니다. 이 전달 방법은 브라우저와 서버의 통신 방식을 개선하여 모든 Dynamic Media 에셋의 응답 및 로드 시간을 향상시킵니다.

다음을 참조하십시오 [콘텐츠의 HTTP/2 전달 FAQ](/help/assets/dynamic-media/http2faq.md).

<!--this md file used to reside under sites-administering-->
