---
title: AEM에서 Universal Editor 시작하기
description: Universal Editor에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 395cb7b2e37c7358baa7ae07329f42bd5a560cb1
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 68%

---


# AEM에서 Universal Editor 시작하기 {#getting-started}

Universal Editor에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.

>[!TIP]
>
>예를 바로 살펴보고 싶다면 [GitHub의 Universal Editor 샘플 앱](https://github.com/adobe/universal-editor-sample-editable-app)을 검토할 수 있습니다.

## 온보딩 단계 {#onboarding}

Universal Editor는 모든 소스의 콘텐츠를 편집할 수 있지만 이 문서에서는 AEM 앱을 예로 사용합니다.

AEM 앱을 온보딩하고 유니버설 편집기를 사용하도록 계측하는 몇 가지 단계가 있습니다.

1. [Universal Editor 핵심 라이브러리를 포함합니다.](#core-library)
1. [필요한 OSGi 구성을 추가합니다.](#osgi-configurations)
1. [페이지를 계측합니다.](#instrument-page)

이 문서에서는 이러한 단계를 안내합니다.

## Universal Editor 핵심 라이브러리 포함 {#core-library}

범용 편집기에서 사용하기 위해 앱을 계측하려면 먼저 다음 종속성을 포함해야 합니다.

```javascript
@adobe/universal-editor-cors
```

계측을 활성화하려면 다음 가져오기를 `index.js`.

```javascript
import "@adobe/universal-editor-cors";
```

### 비 React 앱의 대안 {#alternative}

React 앱을 구현하지 않거나 서버측 렌더링이 필요한 경우 대체 방법은 문서 본문에 다음 사항을 포함하는 것입니다.

```html
<script src="https://universal-editor-service.experiencecloud.live/corslib/LATEST" async></script>
```

항상 최신 버전을 사용하는 것이 좋지만, 변경 사항이 있을 경우 이전 버전의 서비스를 참조할 수 있습니다.

* `https://universal-editor-service.experiencecloud.live/corslib/LATEST` - 최신 UE CORS 라이브러리
* `https://universal-editor-service.experiencecloud.live/corslib/2/LATEST` - 최신 UE CORS 라이브러리 버전 2.x
* `https://universal-editor-service.experiencecloud.live/corslib/2.1/LATEST` - 최신 UE CORS 라이브러리 버전 2.1.x
* `https://universal-editor-service.experiencecloud.live/corslib/2.1.1`- 정확한 UE CORS 라이브러리 버전 2.1.1

## 필요한 OSGi 구성 추가 {#osgi-configurations}

Universal Editor를 사용하여 앱에서 AEM 콘텐츠를 편집할 수 있으려면 AEM 내에서 CORS 및 쿠키 설정을 수행해야 합니다.

다음 [OSGi 구성을 AEM 작성 인스턴스에서 설정해야 합니다.](/help/implementing/deploying/configuring-osgi.md)

* `SameSite Cookies = None`-`com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`
* X-FRAME-OPTIONS 제거: `org.apache.sling.engine.impl.SlingMainServlet`의 SAMEORIGIN 헤더

### com.day.crx.security.token.impl.impl.TokenAuthenticationHandler {#samesite-cookies}

로그인 토큰 쿠키는 서드파티 도메인으로 AEM에 전송되어야 합니다. 따라서 동일 사이트 쿠키는 명시적으로 `None`으로 설정되어야 합니다.

이 속성은 `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler` OSGi 구성에서 설정해야 합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
          token.samesite.cookie.attr="None" />
```

### org.apache.sling.engine.impl.SlingMainServlet {#sameorigin}

X-Frame-Options: SAMEORIGIN은 iframe 내에서 AEM 페이지 렌더링을 방지합니다. 헤더를 제거하면 페이지를 로드할 수 있습니다.

이 속성은 `org.apache.sling.engine.impl.SlingMainServlet` OSGi 구성에서 설정해야 합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="sling:OsgiConfig"
          sling.additional.response.headers="[X-Content-Type-Options=nosniff]"/>
```

## 페이지 계측 {#instrument-page}

Universal Editor 서비스에는 편집 중인 앱의 콘텐츠에 대한 올바른 백엔드 시스템을 식별하고 활용하기 위해 [균일 리소스 이름(URN)](https://en.wikipedia.org/wiki/Uniform_Resource_Name)이 필요합니다. 따라서 콘텐츠를 다시 콘텐츠 리소스에 매핑하려면 URN 스키마가 필요합니다.

### 연결 만들기 {#connections}

앱에서 사용되는 연결은 페이지의 `<head>`에 `<meta>` 태그로 저장됩니다.

```html
<meta name="urn:adobe:aue:<category>:<referenceName>" content="<protocol>:<url>">
```

* `<category>` - 두 가지 옵션을 가진 연결의 분류입니다.
   * `system` - 연결 끝점의 경우
   * `config` - 대상 [선택적 구성 설정 정의](#configuration-settings)
* `<referenceName>` - 연결을 식별하기 위해 문서에서 재사용되는 짧은 이름입니다. 예: `aemconnection`
* `<protocol>` - Universal Editor 지속성 서비스의 어떤 지속성 플러그인을 사용할 것인지 나타냅니다. 예: `aem`
* `<url>` - 변경 사항이 지속되어야 하는 시스템의 URL입니다. 예: `http://localhost:4502`

식별자 `urn:adobe:aue:system`은 Adobe Universal Editor 연결을 의미합니다.

`data-aue-resource`는 `urn` 접두사를 사용하여 식별자를 줄입니다.

```html
data-aue-resource="urn:<referenceName>:<resource>"
```

* `<referenceName>` - `<meta>` 태그에 언급되는 명명된 참조입니다. 예: `aemconnection`
* `<resource>` - 대상 시스템의 리소스에 대한 포인터입니다. 예: `/content/page/jcr:content`와 같은 AEM 콘텐츠 경로

>[!TIP]
>
>Universal Editor에 필요한 데이터 속성 및 유형에 대한 자세한 내용은 [속성 및 유형](attributes-types.md) 문서를 참조하십시오.

### 예시 연결 {#example}

```html
<meta name="urn:adobe:aue:system:<referenceName>" content="<protocol>:<url>">

<html>
<head>
    <meta name="urn:adobe:aue:system:aemconnection" content="aem:https://localhost:4502">
    <meta name="urn:adobe:aue:system:fcsconnection" content="fcs:https://example.franklin.adobe.com/345fcdd">
</head>
<body>
        <aside>
          <ul data-aue-resource="urn:aemconnection:/content/example/list" data-aue-type="container">
            <li data-aue-resource="urn:aemconnection:/content/example/listitem" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">Jane Doe</p>
              <p data-aue-prop="title" data-aue-type="text">Journalist</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>

...

            <li data-aue-resource="urn:fcsconnection:/documents/mytext" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">John Smith</p>
              <p data-aue-resource="urn:aemconnection:/content/example/another-source" data-aue-prop="title" data-aue-type="text">Photographer</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>
          </ul>
        </aside>
</body>
</html>
```

### 구성 설정 {#configuration-settings}

다음을 사용할 수 있습니다. `config` 필요한 경우 서비스 및 확장 끝점을 설정하려면 연결 URN의 접두사를 사용하십시오.

Adobe이 호스팅하는 유니버설 편집기 서비스를 사용하지 않고 호스팅된 자체 버전을 사용하려면 메타 태그에서 이를 설정할 수 있습니다. 범용 편집기에서 제공하는 기본 서비스 끝점을 덮어쓰려면 고유한 서비스 끝점을 설정합니다.

* 메타 이름 - `urn:adobe:aue:config:service`
* 메타 콘텐츠 - `content="https://adobe.com"` (예)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

페이지에 대해 특정 확장만 활성화하려는 경우 메타 태그에서 설정할 수 있습니다. 확장을 가져오려면 확장 끝점을 설정합니다.

* 메타 이름: `urn:adobe:aue:config:extensions`
* 메타 콘텐츠: `content="https://adobe.com,https://anotherone.com,https://onemore.com"` (예)

```html
<meta name="urn:adobe:aue:config:extensions" content="<url>,<url>,<url>">
```

## Universal Editor를 사용할 준비 완료 {#youre-ready}

이제 앱이 Universal Editor를 사용하도록 구성되었습니다.

콘텐츠 작성자가 Universal Editor를 사용하여 콘텐츠를 만드는 것이 얼마나 쉽고 직관적인지 알아보려면 [Universal Editor로 콘텐츠 작성](/help/sites-cloud/authoring/universal-editor/authoring.md)을 참조하십시오.

## 추가 리소스 {#additional-resources}

Universal Editor에 대해 자세히 알아보려면 다음 문서를 참조하십시오.

* [Universal Editor 소개](introduction.md) - Universal Editor를 통해 모든 구현에서 콘텐츠의 모든 측면을 편집하여 뛰어난 경험을 제공하고, 콘텐츠 속도를 높이고, 최신 개발자 경험을 제공하는 방법에 대해 알아봅니다.
* [Universal Editor로 콘텐츠 작성](/help/sites-cloud/authoring/universal-editor/authoring.md) - 콘텐츠 작성자가 Universal Editor를 사용하여 콘텐츠를 만드는 것이 얼마나 쉽고 직관적인지 알아봅니다.
* [유니버설 편집기로 콘텐츠 게시](/help/sites-cloud/authoring/universal-editor/publishing.md) - 유니버설 편집기에서 콘텐츠를 게시하는 방법과 앱에서 게시된 콘텐츠를 처리하는 방법에 대해 알아봅니다.
* [Universal Editor 아키텍처](architecture.md) - Universal Editor의 아키텍처 및 해당 서비스와 계층 간에 데이터가 흐르는 방식에 대해 알아봅니다.
* [속성 및 유형](attributes-types.md) - Universal Editor에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [Universal Editor 인증](authentication.md) - Universal Editor의 인증 방법에 대해 알아봅니다.

