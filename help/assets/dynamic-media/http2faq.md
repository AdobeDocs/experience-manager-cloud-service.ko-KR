---
title: 콘텐츠 FAQ의 HTTP2 전송
description: HTTP2 콘텐츠 전달에 대해 알아봅니다.
role: Admin,User
exl-id: 0a8a5fd8-a341-4e7f-84a5-409e2de97efe
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 1%

---

# 콘텐츠 FAQ의 HTTP2 전송{#http-delivery-of-content-faq}

Adobe은 컨텐츠의 HTTP/2 게재 가용성을 발표하게 되어 매우 기쁘게 생각합니다. HTTP/2를 사용하는 경우 전반적인 성능 증가가 발생합니다.

>[!NOTE]
>
>이 기능을 사용하려면 Adobe Experience Manager - Dynamic Media과 번들로 제공되는 기본 컨텐츠 전달 네트워크를 사용해야 합니다. 다른 모든 사용자 지정 콘텐츠 전달 네트워크는 이 기능에서 지원되지 않습니다.

## HTTP/2란? {#what-is-http}

HTTP/2는 브라우저 및 서버의 통신 방식을 개선하여 정보를 더 빨리 전송하면서도 필요한 처리 능력을 줄일 수 있습니다.

웹 사이트 문서 [HTTP/2에 대해 알고 있어야 하는 사항](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html) 에서는 HTTP/2 및 그 이점에 대해 간단하고 간단하게 설명합니다.

## 컨텐츠 전달을 위해 HTTP/2로 이동하여 얻을 수 있는 주요 이점은 무엇입니까? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

성능 향상은 다양한 요인에 따라 다르므로 광범위하게 다릅니다. 예를 들어, 웹 사이트의 코드, Dynamic Media 사용 방법, 소비자의 장치, 화면 및 위치.

Adobe의 자체 테스트에서는 다음 결과가 도출되었습니다.

* 이미지의 경우 응답 시간이 장치 및 브라우저에 따라 7%~28% 개선되었습니다. 가장 주목할 만한 성능 향상은 iOS 장치였습니다.
* 뷰어의 경우 로드 시간 성능이 15% 향상되었습니다.

다음 데모에서는 HTTP/1과 HTTP/2 로드 간의 차이점을 보여 줍니다.

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## HTTP/2로 전환할 수 있습니까? {#am-i-eligible-to-switch-over-to-http}

HTTP/2를 사용하려면 다음 요구 사항을 충족해야 합니다.

* 리치 미디어 요청에 보안 HTTPS를 사용합니다.
* Dynamic Media Classic 라이센스의 일부로 Adobe 번들 CDN(Content Delivery Network)을 사용합니다.
* 전용 도메인 사용(즉, `images.company.com` 또는 `mycompany.scene7.com`), 일반 Dynamic Media 도메인이 아닌, `s7d1.scene7.com`, `s7d2.scene7.com`, 또는 `s7d13.scene7.com`).

   도메인을 찾으려면 [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)그런 다음 계정에 로그인합니다.

   이동 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 일반 설정]**. 레이블이 지정된 필드를 찾습니다 **게시된 서버 이름**. 현재 일반 Dynamic Media 도메인을 사용 중인 경우, 이 전환의 일부로 고유한 사용자 지정 도메인으로 이동을 요청할 수 있습니다.

## Dynamic Media 계정에 대해 HTTP/2를 활성화하는 프로세스는 무엇입니까? {#what-is-the-process-for-enabling-http-for-my-dm-account}

[Admin Console을 사용하여 지원 사례를 만듭니다](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html) 및 HTTP/2로 전환할 것을 요청합니다. 자동으로 수행되지 않습니다.

1. 지원 사례에 다음 정보를 제공하십시오.

   * 기본 연락처 이름, 전자 메일 및 전화 번호입니다.
   * HTTP2로 전환할 모든 도메인. 그건, `images.company.com` 또는 `mycompany.scene7.com`.

   도메인을 찾으려면 [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)그런 다음 계정에 로그인합니다.

   이동 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 일반 설정]**. 레이블이 지정된 필드를 찾습니다 **[!UICONTROL 게시된 서버 이름]**.

   * 리치 미디어 요청에 보안 HTTPS를 사용하는지 확인합니다.
   * Adobe을 통해 CDN을 사용하고 있으며 직접 관계로 관리되지 않는지 확인합니다.
   * 전용 도메인을 사용하고 있는지 확인합니다. 그건, `images.company.com` 또는 `mycompany.scene7.com`과 같은 일반 Dynamic Media 도메인이 아님 `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

   도메인을 찾으려면 [Dynamic Media Classic 데스크탑 애플리케이션](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)그런 다음 계정에 로그인합니다.

   이동 **[!UICONTROL 설정]** > **[!UICONTROL 애플리케이션 설정]** > **[!UICONTROL 일반 설정]**. 레이블이 지정된 필드를 찾습니다 **[!UICONTROL 게시된 서버 이름]**. 현재 일반 Dynamic Media 도메인을 사용 중인 경우, 이 전환의 일부로 고유한 사용자 지정 도메인으로 이동을 요청할 수 있습니다.

   1. 고객 지원 팀은 요청이 제출된 순서에 따라 HTTP/2 고객 대기 목록에 사용자를 추가합니다.
   1. Adobe이 요청을 처리할 준비가 되면 고객 지원 센터에서 전환을 조정하고 대상 날짜를 설정하도록 알려줍니다.
   1. 완료 후 알림을 받게 되며 HTTP2로 성공적으로 전환되었는지 확인할 수 있습니다.



## 언제 HTTP/2로 전환할 수 있습니까? {#when-can-i-expect-to-be-transitioned-over-to-http}

요청은 고객 지원에서 수신하는 순서로 처리됩니다.

>[!NOTE]
>
>HTTP/2로 전환하면 캐시를 지워야 하므로 리드 타임이 오래 걸립니다. 따라서 한 번에 몇 개의 고객 전환만 처리할 수 있습니다.

## HTTP/2로 이동할 때 어떤 위험이 있습니까? {#what-are-the-risks-with-moving-to-http}

HTTP/2로 전환하면 새 CDN 구성으로 이동해야 하므로 CDN에서 캐시를 지웁니다.

캐싱되지 않은 컨텐츠는 캐시가 다시 빌드될 때까지 Adobe의 원본 서버에 직접 연결됩니다. 이러한 작업으로 인해 Adobe은 한 번에 몇 개의 고객 전환을 처리할 계획입니다. 이 방법은 원본에서 요청을 가져올 때 허용 가능한 성능이 유지되도록 합니다.

## URL 또는 웹 사이트가 HTTP/2로 활성화되었는지 어떻게 확인할 수 있습니까? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

웹 브라우저에서 사용할 확장을 다운로드합니다. Firefox 및 Chrome의 경우 **[!UICONTROL HTTP/2 및 SPDY 표시기]**. 브라우저는 HTTP/2만 안전하게 지원하므로 확인하려면 HTTPS를 사용하여 URL을 호출해야 합니다. HTTP/2가 지원되는 경우 확장이 파란색 Flash 기호 형태로 표시되고 헤더 &quot;X-Firefox-Spdy&quot; 가 표시됩니다. &quot;h2&quot;.
