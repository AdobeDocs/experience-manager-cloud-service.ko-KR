---
title: 사용자 지정 오류 페이지
description: AEM에는 사용자 정의할 수 있는 HTTP 오류 처리를 위한 표준 오류 처리기가 포함되어 있습니다.
translation-type: tm+mt
source-git-commit: d7e9bdee83f1b85436185ca57420ee178268cb33
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# 오류 페이지 {#customizing-error-pages} 사용자 지정

AEM에는 HTTP 오류 처리를 위한 표준 오류 처리기가 포함되어 있습니다.예를 들어 다음을 표시합니다.

![표준 오류 메시지](assets/error-message-standard.png)

오류에 응답하기 위해 AEM은 `/libs/sling/servlet/errorhandler` 아래에 `404.jsp` 스크립트를 제공합니다.

>[!TIP]
>
>AEM은 Apache Sling을 기반으로 하므로 Apache 오류 처리 설명서에서 [에 자세한 정보를 볼 수 있습니다.](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html)

>[!NOTE]
>
>작성자 인스턴스에서 [CQ WCM 디버그 필터](/help/implementing/deploying/configuring-osgi.md)는 기본적으로 활성화되어 있습니다. 항상 응답 코드 200이 발생합니다. 기본 오류 핸들러는 전체 스택 추적을 응답에 써서 응답합니다.
>
>게시 인스턴스에서 CQ WCM 디버그 필터는 **항상**&#x200B;이 비활성화되었습니다(활성화된 것으로 구성된 경우에도).

## 오류 처리기 {#how-to-customize-pages-shown-by-the-error-handler}에 표시되는 페이지를 사용자 지정하는 방법

오류가 발생할 때 오류 처리기가 표시하는 페이지를 사용자 지정하는 자체 스크립트를 개발할 수 있습니다. 이렇게 하려면 [AEM 표준 오버레이 메커니즘](/help/implementing/developing/introduction/overlays.md)을 사용하여 사용자 지정된 페이지가 `/apps` 아래에 만들어지고 `/libs` 아래에 있는 기본 페이지를 오버레이합니다.

1. 저장소에서 기본 스크립트를 복사합니다.

   * 변환 전: `/libs/sling/servlet/errorhandler/`
   * 끝 `/apps/sling/servlet/errorhandler/`

   대상 경로가 기본적으로 존재하지 않으므로 이 작업을 처음으로 수행할 때 대상 경로를 만들어야 합니다.

1. 다음으로 이동 `/apps/sling/servlet/errorhandler`. 여기에서 다음 중 하나를 수행할 수 있습니다.

   * 필요한 정보를 제공하기 위해 적절한 기존 스크립트를 편집합니다. 또는
   * 필요한 코드에 대한 새 스크립트를 만들고 편집합니다.

1. 변경 내용을 저장하고 테스트합니다.

>[!CAUTION]
>
>`404.jsp` 스크립트는 AEM 인증을 충족하기 위해 특별히 설계되었습니다.특히 이러한 오류가 발생하는 경우 시스템 로그인을 허용합니다.
>
>따라서 이 스크립트의 대체는 매우 신중하게 해야 합니다.

### HTTP 500 오류에 대한 응답 사용자 지정 {#customizing-the-response-to-http-errors}

HTTP [500 내부 서버 오류](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)는 예기치 않은 조건이 발생한 서버와 같은 서버측 오류를 표시하여 요청을 처리할 수 없습니다.

요청 처리 결과 예외가 발생하면 Apache Sling 프레임워크(AEM이 구축됨):

* 예외를 기록합니다.
* 응답의 본문에 다음을 반환합니다.
   * HTTP 응답 코드 500
   * 예외 스택 추적

[오류 처리기](#how-to-customize-pages-shown-by-the-error-handler)에 의해 표시되는 페이지를 사용자 정의하여 `500.jsp` 스크립트를 만들 수 있습니다. 그러나 `HttpServletResponse.sendError(500)`이(가) 명시적으로 실행되는 경우에만 사용됩니다.예: 예외 캐처

그렇지 않으면 응답 코드가 500으로 설정되지만 `500.jsp` 스크립트가 실행되지 않습니다.

500 오류를 처리하려면 오류 처리기 스크립트의 파일 이름이 예외 클래스(또는 수퍼 클래스)와 같아야 합니다. 이러한 모든 예외를 처리하려면 `/apps/sling/servlet/errorhandler/Throwable.jsp` 또는 `/apps/sling/servlet/errorhandler/Exception.jsp` 스크립트를 만들 수 있습니다.

>[!CAUTION]
>
>작성자 인스턴스에서 [CQ WCM 디버그 필터](/help/implementing/deploying/configuring-osgi.md)는 기본적으로 활성화되어 있습니다. 항상 응답 코드 200이 발생합니다. 기본 오류 핸들러는 전체 스택 추적을 응답에 써서 응답합니다.
>
>사용자 지정 오류 처리기의 경우 코드 500이 있는 응답이 필요하므로 [CQ WCM 디버그 필터를 비활성화해야 합니다.](/help/implementing/deploying/configuring-osgi.md) 이렇게 하면 응답 코드 500이 반환되고, 이 경우 올바른 Sling 오류 핸들러가 트리거됩니다.
>
>게시 인스턴스에서 CQ WCM 디버그 필터는 **항상**&#x200B;이 비활성화되었습니다(활성화된 것으로 구성된 경우에도).
