---
title: Dynamic Media 자산 제공
description: Dynamic Media 에셋을 제공하는 방법을 알아봅니다.
feature: 자산 관리
role: Business Practitioner
exl-id: 4557b561-b3c4-4d6f-8044-2069bda41613
translation-type: tm+mt
source-git-commit: 1ad89be4ebddec0705c6f557fed3d697b9f1f3a7
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 7%

---

# Dynamic Media 자산 제공{#delivering-dynamic-media-assets}

비디오 및 이미지 등 Dynamic Media 자산을 제공하는 방법은 웹 사이트 구현 방법에 따라 다릅니다.

Dynamic Media에는 다음과 같은 몇 가지 옵션이 있습니다.

* 웹 사이트가 Adobe Experience Manager에서 호스팅되는 경우 Dynamic Media 자산을 페이지에 직접 추가할 수 있습니다.
* 웹 사이트가 Experience Manager에 없는 경우 다음 중 하나를 선택합니다.

   * 웹 사이트에 비디오 또는 이미지 임베드
   * 웹 응용 프로그램에 URL을 연결합니다. 비디오 플레이어를 팝업 또는 모달 창으로 제공하려는 경우 링크를 사용합니다.
   * 사이트가 응답형인 경우 [최적화된 이미지](/help/assets/dynamic-media/responsive-site.md)를 제공할 수 있습니다.

>[!NOTE]
>
>스마트 이미징은 기존 이미지 사전 설정과 연동됩니다. 전달 마지막 순간에 지능적인 기능을 사용하여 브라우저 또는 네트워크 연결 속도에 따라 이미지 파일 크기를 추가로 줄일 수 있습니다. 자세한 내용은 [스마트 이미징](/help/assets/dynamic-media/imaging-faq.md)을 참조하십시오.

자세한 내용은 다음 항목을 참조하십시오.

* [웹 페이지에 Dynamic Media 자산 추가](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [웹 페이지에 비디오 또는 이미지 뷰어 포함](/help/assets/dynamic-media/embed-code.md)
* [Dynamic Media에서 핫링크 보호 활성화](/help/assets/dynamic-media/hotlink-protection.md)
* [웹 응용 프로그램에 URL 연결](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [응답형 사이트에 최적화된 이미지 제공](/help/assets/dynamic-media/responsive-site.md)
* [콘텐츠의 HTTP2 전달](/help/assets/dynamic-media/http2faq.md)
* [Dynamic Media을 통해 CDN 캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
* [Dynamic Media Classic을 통해 CDN 캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dm-classic.md)
* [규칙 세트를 사용하여 URL 변형](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)

## Dynamic Media 에셋 {#http-delivery-of-dynamic-media-assets} HTTP/2 전달

이제 Experience Manager은 HTTP/2를 통해 모든 Dynamic Media 컨텐츠(이미지 및 비디오)를 전달할 수 있습니다. 즉, 이미지 또는 비디오에 대해 게시된 URL 또는 포함 코드는 호스팅된 자산을 허용하는 모든 응용 프로그램과 통합할 수 있습니다. 이렇게 게시된 자산은 HTTP/2 프로토콜을 통해 전달됩니다. 이 방식의 전달은 브라우저 및 서버의 통신 방식을 개선하여 모든 Dynamic Media 에셋에 대한 응답 및 로드 시간을 향상시킵니다.

자세한 내용은 [HTTP/2 FAQ 배달](/help/assets/dynamic-media/http2faq.md)을 참조하십시오.
