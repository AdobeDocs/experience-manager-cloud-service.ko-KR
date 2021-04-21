---
title: 콘텐츠의 HTTP2 전달 FAQ
description: HTTP2 컨텐츠 전달에 대해 알아봅니다.
role: Administrator,Business Practitioner
exl-id: 0a8a5fd8-a341-4e7f-84a5-409e2de97efe
translation-type: tm+mt
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 1%

---

# 콘텐츠의 HTTP2 전달 FAQ{#http-delivery-of-content-faq}

Adobe은 HTTP/2 컨텐츠 전달 가용성을 발표하게 되어 매우 기쁩니다. HTTP/2를 사용하는 경우 전반적인 성능 증가가 경험됩니다.

>[!NOTE]
>
>이 기능을 사용하려면 Adobe Experience Manager Dynamic Media에 번들로 제공되는 기본 CDN을 사용해야 합니다. 다른 모든 사용자 지정 CDN은 이 기능에서 지원되지 않습니다.

## HTTP/2 소개{#what-is-http}

HTTP/2는 브라우저 및 서버의 통신 방식을 개선하여 정보를 신속하게 전송하고 필요한 처리 능력을 감소시킵니다.

다음 웹 사이트에서는 HTTP/2 및 HTTP의 이점에 대해 간단하고 간단하게 설명합니다.

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## 컨텐츠 전달을 위해 HTTP/2로 전환하면 어떤 이점이 있습니까?{#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

성능 향상은 다양한 요인에 따라 다르므로 다양하게 변화합니다. 예를 들어 웹 사이트 코드, Dynamic Media 사용 방법, 소비자의 디바이스, 화면 및 위치.

Adobe 자체 테스트 결과:

* 이미지의 경우 장치 및 브라우저에 따라 응답 시간이 7%-28% 향상되었습니다. iOS 디바이스에서 가장 주목할 만한 성능 향상
* 뷰어의 경우 로드 시간 성능이 15% 향상되었습니다.

다음 데모에서는 HTTP/1과 HTTP/2 로딩 간의 차이점을 보여 줍니다.

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## HTTP/2로 전환할 수 있습니까?{#am-i-eligible-to-switch-over-to-http}

HTTP/2를 사용하려면 다음 요구 사항을 충족해야 합니다.

* 리치 미디어 요청을 위해 안전한 HTTPS를 사용합니다.
* Dynamic Media Classic 라이선스의 일부로 Adobe 번들 CDN(Content Delivery Network)을 사용합니다.
* 일반 Dynamic Media 도메인(즉, `s7d1.scene7.com`, `s7d2.scene7.com` 또는 `s7d13.scene7.com`)이 아닌 전용 도메인(즉, `images.company.com` 또는 `mycompany.scene7.com`)을 사용합니다.

   도메인을 찾으려면 [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 열고 계정에 로그인합니다.

   **[!UICONTROL 설정 > 응용 프로그램 설정 > 일반 설정]**&#x200B;을 클릭합니다. **게시된 서버 이름**&#x200B;이라는 레이블이 있는 필드를 찾습니다. 현재 일반 Dynamic Media 도메인을 사용하고 있는 경우 이 전환의 일부로 사용자 정의 도메인으로의 이동을 요청할 수 있습니다.

## Dynamic Media 계정에 대해 HTTP/2를 활성화하는 프로세스는 무엇입니까?{#what-is-the-process-for-enabling-http-for-my-dm-account}

[Admin Console을 사용하여 지원 케이스](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 를 만들고 HTTP/2로 전환 요청;자동으로 수행되지 않습니다.

1. 지원 케이스에 다음 정보를 제공합니다.

   * 기본 연락처 이름, 이메일 및 전화 번호
   * HTTP2로 전환할 모든 도메인. 즉, `images.company.com` 또는 `mycompany.scene7.com`입니다.

   도메인을 찾으려면 [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 열고 계정에 로그인합니다.

   **[!UICONTROL 설정 > 응용 프로그램 설정 > 일반 설정]**&#x200B;을 클릭합니다. **[!UICONTROL 게시된 서버 이름]**&#x200B;이라는 레이블이 있는 필드를 찾습니다.

   * 리치 미디어 요청에 보안 HTTPS를 사용하는지 확인합니다.
   * Adobe을 통해 CDN을 사용하고 있고 직접 관계로 관리되지 않는지 확인합니다.
   * 전용 도메인을 사용하고 있는지 확인합니다. 즉, `images.company.com` 또는 `mycompany.scene7.com`은(는) `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`와 같은 일반 Dynamic Media 도메인이 아닙니다.

   도메인을 찾으려면 [Dynamic Media Classic 데스크톱 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 열고 계정에 로그인합니다.

   **[!UICONTROL 설정 > 응용 프로그램 설정 > 일반 설정]**&#x200B;을 클릭합니다. **[!UICONTROL 게시된 서버 이름]**&#x200B;이라는 레이블이 있는 필드를 찾습니다. 현재 일반 Dynamic Media 도메인을 사용하고 있는 경우 이 전환의 일부로 사용자 정의 도메인으로의 이동을 요청할 수 있습니다.

   1. 기술 지원에서는 요청을 제출한 순서에 따라 HTTP/2 고객 대기 목록에 사용자를 추가합니다.
   1. Adobe이 요청을 처리할 준비가 되면 고객 지원 센터는 전환 조정을 위해 사용자에게 연락하여 타겟 날짜를 설정합니다.
   1. 완료 후 알림을 받게 되며 HTTP2로 성공적으로 전환했는지 확인할 수 있습니다.



## 언제 HTTP/2로 전환할 예정입니까?{#when-can-i-expect-to-be-transitioned-over-to-http}

요청은 기술 지원에서 수신한 순서대로 처리됩니다.

>[!NOTE]
>
>HTTP/2로의 전환에는 캐시를 지우는 작업이 포함되므로 리드 타임이 오래 걸립니다. 따라서 한 번에 몇 가지 고객 전환만 처리할 수 있습니다.

## HTTP/2로 이동하는 경우 어떤 위험이 있습니까?{#what-are-the-risks-with-moving-to-http}

HTTP/2로의 전환은 새 CDN 구성으로 이동하는 것을 포함하므로 CDN의 캐시를 지웁니다.

캐시되지 않은 콘텐츠는 캐시가 다시 빌드될 때까지 Adobe의 원본 서버를 직접 히트 시킵니다. 이러한 행동으로 인해 Adobe은 한 번에 몇 가지 고객 전환을 처리할 계획입니다. 이 방법을 사용하면 원래 위치에서 요청을 가져올 때 허용되는 성능이 유지됩니다.

## URL 또는 웹 사이트가 HTTP/2로 활성화되었는지 어떻게 확인할 수 있습니까?{#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

웹 브라우저에 사용할 확장 프로그램을 다운로드합니다. Firefox 및 Chrome의 경우 **[!UICONTROL HTTP/2 및 SPDY 표시기]** 확장명이 있습니다. 브라우저는 HTTP/2만 안전하게 지원하므로 HTTPS를 사용하여 URL을 호출하여 확인해야 합니다. HTTP/2가 지원되는 경우 파란색 Flash 기호 형태로 확장자로 표시되고 헤더 &quot;X-Firefox-Spdy&quot;가 표시됩니다.&quot;h2&quot;.
