---
title: Dynamic Media Assets 제공
description: 포함된 비디오 및 이미지를 통해 또는 웹 애플리케이션에 URL을 연결하여 Dynamic Media 자산을 웹 페이지에 전달하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 4557b561-b3c4-4d6f-8044-2069bda41613
source-git-commit: 0e452bd94d75609ecc3c20ab6b56ded968ed0a70
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 7%

---

# Dynamic Media Assets 제공{#delivering-dynamic-media-assets}

Dynamic Media 에셋(비디오와 이미지 모두)을 전달하는 방법은 웹 사이트가 구현되는 방식에 따라 다릅니다.

Dynamic Media에는 다음과 같은 몇 가지 옵션이 있습니다.

* 웹 사이트가 Adobe Experience Manager에서 호스팅되는 경우 Dynamic Media 에셋을 페이지에 바로 추가하려 합니다.
* 웹 사이트가 Experience Manager에 없는 경우 다음 중 하나를 선택할 수 있습니다.

   * 웹 사이트에 비디오 또는 이미지를 포함합니다.
   * 웹 애플리케이션에 URL을 연결합니다. 비디오 플레이어를 팝업 또는 모달 창으로 전달하려면 연결을 사용합니다.
   * 사이트가 응답형인 경우 [최적화된 이미지를 제공](/help/assets/dynamic-media/responsive-site.md)할 수 있습니다.

>[!NOTE]
>
>스마트 이미징은 기존 이미지 사전 설정에서 작동합니다. 전달 마지막 순간에 인텔리전스를 사용하여 브라우저나 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다. 자세한 내용은 [스마트 이미징](/help/assets/dynamic-media/imaging-faq.md)을 참조하세요.

자세한 내용은 다음 항목을 참조하십시오.

* [웹 페이지에 Dynamic Media Assets 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)
* [Dynamic Media의 핫링크 보호 활성화](/help/assets/dynamic-media/hotlink-protection.md)
* [웹 애플리케이션에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [응답형 사이트용으로 최적화된 이미지 제공](/help/assets/dynamic-media/responsive-site.md)
* [컨텐츠의 HTTP2 전달](/help/assets/dynamic-media/http2faq.md)
* [Dynamic Media의 방식으로 CDN 캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
* [Dynamic Media Classic의 방식으로 CDN 캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dm-classic.md)
* [규칙 세트를 사용하여 URL 변환](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)

## Dynamic Media 자산의 HTTP/2 전달 {#http-delivery-of-dynamic-media-assets}

이제 Experience Manager은 HTTP/2를 통해 모든 Dynamic Media 컨텐츠(이미지 및 비디오)의 전달을 지원합니다. 즉, 이미지 또는 비디오에 대한 게시된 URL 또는 포함 코드를 호스팅된 에셋을 허용하는 모든 애플리케이션과 통합할 수 있습니다. 그런 다음 게시된 에셋은 HTTP/2 프로토콜을 통해 전달됩니다. 이 전달 방법은 브라우저와 서버의 통신 방식을 개선하여 모든 Dynamic Media 에셋의 응답 및 로드 시간을 향상시킵니다.

자세한 내용은 [HTTP/2 콘텐츠 배달 FAQ](/help/assets/dynamic-media/http2faq.md)를 참조하세요.
