---
title: 사용자 정의 오류 페이지
description: AEM에는 사용자 지정할 수 있는 HTTP 오류를 처리하기 위한 표준 오류 핸들러가 포함되어 있습니다.
exl-id: b74c65d1-8ef5-4ad4-8255-8187f3b1d84c
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 2%

---

# 오류 페이지 사용자 지정 {#customizing-error-pages}

AEM에는 HTTP 오류를 처리하기 위한 표준 오류 처리기가 함께 제공됩니다. 예를 들면 다음과 같습니다.

![표준 오류 메시지](assets/error-message-standard.png)

오류에 응답하기 위해 AEM에서는 `404.jsp` 아래에 스크립트 `/libs/sling/servlet/errorhandler`.

>[!TIP]
>
>AEM은 Apache Sling을 기반으로 하므로 자세한 정보를 사용할 수 있습니다 [( Apache 오류 처리 설명서)](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html)

>[!NOTE]
>
>작성자 인스턴스에서 [CQ WCM 디버그 필터](/help/implementing/deploying/configuring-osgi.md) 은 기본적으로 활성화되어 있습니다. 따라서 항상 응답 코드 200이 생성됩니다. 기본 오류 처리기는 전체 스택 추적을 응답에 기록하여 응답합니다.
>
>게시 인스턴스에서 CQ WCM 디버그 필터는 **항상** 비활성화됨(활성화됨으로 구성된 경우에도).

## 오류 핸들러로 표시된 페이지를 사용자 지정하는 방법 {#how-to-customize-pages-shown-by-the-error-handler}

자체 스크립트를 개발하여 오류가 발생했을 때 오류 핸들러에서 표시하는 페이지를 사용자 지정할 수 있습니다. 이렇게 하려면 다음을 사용합니다 [AEM 표준 오버레이 메커니즘](/help/implementing/developing/introduction/overlays.md) 따라서 맞춤화된 페이지는에 생성됩니다 `/apps` 아래에 있는 기본 페이지를 오버레이합니다. `/libs`.

1. 저장소에서 기본 스크립트를 복사합니다.

   * 변환 전: `/libs/sling/servlet/errorhandler/`
   * 끝 `/apps/sling/servlet/errorhandler/`

   기본적으로 대상 경로가 존재하지 않으므로 처음 이 작업을 수행할 때 대상 경로를 만들어야 합니다.

1. 다음으로 이동 `/apps/sling/servlet/errorhandler`. 다음 중 하나를 수행할 수 있습니다.

   * 필요한 정보를 제공하도록 적절한 기존 스크립트를 편집합니다. 또는
   * 필요한 코드에 대한 새 스크립트를 만들고 편집합니다.

1. 변경 사항을 저장하고 테스트합니다.

>[!CAUTION]
>
>다음 `404.jsp` 스크립트는 특히 이러한 오류가 발생하는 경우 시스템 로그인을 허용하도록 AEM 인증에 맞게 특별히 설계되었습니다.
>
>따라서 이 대본의 교체는 매우 신중하게 이루어져야 합니다.

### HTTP 500 오류에 대한 응답 사용자 지정 {#customizing-the-response-to-http-errors}

HTTP [500 내부 서버 오류](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) 서버에서 예기치 않은 상태가 발생하여 요청을 수행할 수 없는 것과 같은 서버측 오류를 나타냅니다.

요청 처리로 인해 예외가 발생하는 경우 Apache Sling 프레임워크(AEM이 빌드됨):

* 예외를 기록합니다.
* 응답 본문으로 를 반환합니다.
   * HTTP 응답 코드 500
   * 예외 스택 추적

작성자: [오류 핸들러로 표시된 페이지 사용자 지정](#how-to-customize-pages-shown-by-the-error-handler) a `500.jsp` 스크립트를 만들 수 있습니다. 그러나 다음과 같은 경우에만 사용됩니다 `HttpServletResponse.sendError(500)` 는 명시적으로 실행됩니다. 즉, 예외 캐쳐에서 실행됩니다.

그렇지 않으면 응답 코드가 500으로 설정되지만 `500.jsp` 스크립트가 실행되지 않습니다.

500 오류를 처리하려면 오류 처리기 스크립트의 파일 이름이 예외 클래스(또는 슈퍼클래스)와 같아야 합니다. 이러한 모든 예외를 처리하기 위해 스크립트를 만들 수 있습니다 `/apps/sling/servlet/errorhandler/Throwable.jsp` 또는 `/apps/sling/servlet/errorhandler/Exception.jsp`.

>[!NOTE]
>
>AEM as Cloud Service에서 CDN은 백엔드에서 5XX 오류가 수신될 때 일반 오류 페이지를 제공합니다. 백엔드의 실제 응답을 통과하려면 응답에 다음 헤더를 추가해야 합니다. `x-aem-error-pass: true`.
>이는 AEM 또는 Apache/Dispatcher 계층에서 오는 응답에만 작동합니다. 중간 인프라 계층에서 발생하는 기타 예기치 않은 오류는 일반 오류 페이지를 계속 표시합니다.

>[!CAUTION]
>
>작성자 인스턴스에서 [CQ WCM 디버그 필터](/help/implementing/deploying/configuring-osgi.md) 은 기본적으로 활성화되어 있습니다. 따라서 항상 응답 코드 200이 생성됩니다. 기본 오류 처리기는 전체 스택 추적을 응답에 기록하여 응답합니다.
>
>사용자 지정 오류 처리기의 경우 코드 500이 있는 응답이 필요하므로 [CQ WCM 디버그 필터를 비활성화해야 합니다.](/help/implementing/deploying/configuring-osgi.md). 이는 응답 코드(500)가 반환되는 것을 보장하며, 이는 결국 올바른 Sling 오류-핸들러를 트리거한다.
>
>게시 인스턴스에서 CQ WCM 디버그 필터는 **항상** 비활성화됨(활성화됨으로 구성된 경우에도).
