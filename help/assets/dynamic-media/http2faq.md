---
title: 콘텐츠 FAQ의 HTTP2 게재
description: HTTP2 콘텐츠 전달에 대해 알아보고 브라우저와 서버 간의 통신을 개선하여 정보를 더 빠르게 전송하는 방법에 대해 알아봅니다.
contentOwner: Rick Brough
feature: Dynamic Media,Configuration,FAQ
role: Admin,User
exl-id: 0a8a5fd8-a341-4e7f-84a5-409e2de97efe
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 1%

---

# 콘텐츠 FAQ의 HTTP2 게재{#http-delivery-of-content-faq}

Adobe은 컨텐츠의 HTTP/2 전달 가능성을 발표하게 되어 매우 기쁘게 생각합니다. HTTP/2를 사용할 때 전반적인 성능이 향상됩니다.

>[!NOTE]
>
>이 기능을 사용하려면 Adobe Experience Manager - Dynamic Media와 함께 번들로 제공되는 기본 제공 컨텐츠 전달 네트워크를 사용해야 합니다. 이 기능에서는 다른 모든 사용자 지정 콘텐츠 전달 네트워크가 지원되지 않습니다.

## HTTP/2란? {#what-is-http}

HTTP/2는 브라우저와 서버의 통신 방식을 향상시켜 필요한 처리 능력을 줄이면서 정보를 더 빠르게 전송할 수 있도록 합니다.

웹 사이트 문서 [HTTP/2에 대해 알고 있어야 하는 사항](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html)에서는 HTTP/2와 그 이점을 간단하고 간단하게 설명합니다.

## 컨텐츠 전달을 위해 HTTP/2로 이동하면 얻을 수 있는 주요 이점은 무엇입니까? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

성능 향상은 다양한 요인에 기반하기 때문에 매우 다양합니다. 예를 들어 웹 사이트의 코드, Dynamic Media 사용 방법, 소비자의 장치, 화면 및 위치가 이러한 예입니다.

Adobe 자체 테스트에서 다음과 같은 결과가 도출되었습니다.

* 이미지의 경우 디바이스 및 브라우저에 따라 응답 시간이 7~28% 향상되었습니다. 가장 눈에 띄는 성능 향상은 iOS 장치에서 이루어졌습니다.
* 뷰어의 경우 로드 시간 성능이 15% 향상되었습니다.

다음 데모에서는 HTTP/1과 HTTP/2 로드 간의 차이점을 보여 줍니다.

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## HTTP/2로 전환할 수 있습니까? {#am-i-eligible-to-switch-over-to-http}

HTTP/2를 사용하려면 다음 요구 사항을 충족해야 합니다.

* 리치 미디어 요청에 보안 HTTPS를 사용합니다.
* Adobe 번들로 제공되는 CDN(Content Delivery Network)을 Dynamic Media Classic 라이선스의 일부로 사용합니다.
* 일반 Dynamic Media 도메인(`s7d1.scene7.com`, `s7d2.scene7.com` 또는 `s7d13.scene7.com`)이 아닌 전용 도메인(`images.company.com` 또는 `mycompany.scene7.com`)을 사용하십시오.

  도메인을 찾으려면 [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=ko#getting-started)을 연 다음 계정에 로그인하세요.

  **[!UICONTROL 설정]** > **[!UICONTROL 응용 프로그램 설정]** > **[!UICONTROL 일반 설정]**(으)로 이동합니다. 레이블이 **게시된 서버 이름**&#x200B;인 필드를 찾습니다. 현재 일반 Dynamic Media 도메인을 사용 중인 경우 이 전환의 일부로 사용자 정의 도메인으로의 이동을 요청할 수 있습니다.

## 내 Dynamic Media 계정에 대해 HTTP/2를 활성화하는 프로세스는 무엇입니까? {#what-is-the-process-for-enabling-http-for-my-dm-account}

[Admin Console을 사용하여 지원 사례를 만들고](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html) HTTP/2로 전환하도록 요청하세요. 자동으로 수행되지 않습니다.

1. 지원 사례에 다음 정보를 제공하십시오.

   * 기본 담당자 이름, 이메일 및 전화번호.
   * HTTP2로 전환할 모든 도메인. 즉, `images.company.com` 또는 `mycompany.scene7.com`입니다.

   도메인을 찾으려면 [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=ko#getting-started)을 연 다음 계정에 로그인하세요.

   **[!UICONTROL 설정]** > **[!UICONTROL 응용 프로그램 설정]** > **[!UICONTROL 일반 설정]**(으)로 이동합니다. 레이블이 **[!UICONTROL 게시된 서버 이름]**&#x200B;인 필드를 찾습니다.

   * 리치 미디어 요청에 보안 HTTPS를 사용하는지 확인합니다.
   * Adobe을 통해 CDN을 사용 중이며 직접적인 관계로 관리되지 않는지 확인합니다.
   * 전용 도메인을 사용 중인지 확인합니다. 즉, `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`과(와) 같은 일반 Dynamic Media 도메인이 아닌 `images.company.com` 또는 `mycompany.scene7.com`입니다.

   도메인을 찾으려면 [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=ko#getting-started)을 연 다음 계정에 로그인하세요.

   **[!UICONTROL 설정]** > **[!UICONTROL 응용 프로그램 설정]** > **[!UICONTROL 일반 설정]**(으)로 이동합니다. 레이블이 **[!UICONTROL 게시된 서버 이름]**&#x200B;인 필드를 찾습니다. 현재 일반 Dynamic Media 도메인을 사용 중인 경우 이 전환의 일부로 사용자 정의 도메인으로의 이동을 요청할 수 있습니다.

   1. 고객 지원 팀은 요청이 제출된 순서에 따라 사용자를 HTTP/2 고객 대기자 명단에 추가합니다.
   1. Adobe에서 요청을 처리할 준비가 되면 고객 지원 팀에서 연락하여 전환을 조정하고 목표 날짜를 설정합니다.
   1. 완료 후 알림이 전송되며 HTTP2로의 성공적인 전환을 확인할 수 있습니다.

## 언제 HTTP/2로 전환할 수 있습니까? {#when-can-i-expect-to-be-transitioned-over-to-http}

요청은 고객 지원 센터에서 수신한 순서대로 처리됩니다.

>[!NOTE]
>
>HTTP/2로의 전환에는 캐시 지우기가 포함되기 때문에 리드 타임이 깁니다. 따라서 한 번에 몇 개의 고객 전환만 처리할 수 있습니다.

## HTTP/2로 이동할 때 발생하는 위험은 무엇입니까? {#what-are-the-risks-with-moving-to-http}

HTTP/2로 전환하면 새 CDN 구성으로 이동하는 작업이 포함되므로 CDN에서 캐시가 지워집니다.

캐싱되지 않은 콘텐츠는 캐시가 다시 빌드될 때까지 Adobe의 원본 서버에 직접 도달합니다. 이러한 조치 때문에 Adobe은 한 번에 몇 가지 고객 전환을 처리할 계획입니다. 이 방법을 사용하면 원본에서 요청을 가져올 때 수용 가능한 성능이 유지됩니다.

## URL 또는 웹 사이트가 HTTP/2로 활성화되었는지 어떻게 확인할 수 있습니까? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

웹 브라우저에서 사용할 확장을 다운로드합니다. Firefox 및 Chrome의 경우 **[!UICONTROL HTTP/2 및 SPDY 표시기]**&#x200B;라는 확장이 있습니다. 브라우저는 HTTP/2만 안전하게 지원하므로, HTTPS로 URL을 호출하여 확인해야 합니다. HTTP/2가 지원되는 경우 파란색 Flash 기호 및 헤더 &quot;X-Firefox-Spdy&quot; : &quot;h2&quot; 형식으로 확장되어 표시됩니다.
