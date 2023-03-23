---
title: AEM에서 범용 편집기 시작하기
description: 범용 편집기에 액세스하는 방법과 첫 번째 AEM 앱 계측을 시작하여 이를 사용하는 방법을 알아봅니다.
source-git-commit: 0e66c379e10d275610d85a699da272dc0c32a9a8
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---


# AEM에서 범용 편집기 시작하기 {#getting-started}

범용 편집기에 액세스하는 방법과 첫 번째 AEM 앱 계측을 시작하여 이를 사용하는 방법을 알아봅니다.

>[!TIP]
>
>예를 보려면 다음을 검토할 수 있습니다 [GitHub의 범용 편집기 샘플 앱.](https://github.com/adobe/universal-editor-sample-editable-app)

## 온보딩 단계 {#onboarding}

범용 편집기에서 컨텐츠를 편집할 수 있지만 이 문서는 AEM 앱을 예로 사용합니다.

AEM 앱을 온보딩하고 범용 편집기를 사용하도록 이를 계측하는 여러 단계가 있습니다.

1. [범용 편집기에 대한 액세스 권한을 요청합니다.](#request-access)
1. [범용 편집기 핵심 라이브러리를 포함합니다.](#core-library)
1. [필요한 OSGi 구성을 추가합니다.](#osgi-configurations)
1. [페이지를 계측합니다.](#instrument-page)

이 문서는 다음 단계를 안내합니다.

## 범용 편집기에 대한 액세스 요청 {#request-access}

먼저 범용 편집기에 대한 액세스를 요청해야 합니다. 다음 위치로 이동하십시오. [https://experience.adobe.com/#/aem/editor](https://experience.adobe.com/#/aem/editor) 범용 편집기에 액세스할 수 있는지 확인하고 확인합니다.

액세스 권한이 없는 경우 동일한 페이지에 연결된 양식을 통해 요청할 수 있습니다.

## 범용 편집기 핵심 라이브러리 포함 {#core-library}

범용 편집기에서 사용하기 위해 앱을 계측하려면 먼저 다음 종속성을 포함해야 합니다.

```javascript
@adobe/universal-editor-cors
```

계측을 활성화하려면 다음 가져오기를 `index.js`.

```javascript
import "@adobe/universal-editor-cors";
```

### 비반응 앱에 대한 대체 요소 {#alternative}

React 앱을 구현하지 않거나, 서버측 렌더링이 필요한 경우, 대체 방법은 문서 본문에 다음 내용을 포함하는 것입니다.

```html
<script src="https://cdn.jsdelivr.net/gh/adobe/universal-editor-cors/dist/universal-editor-embedded.js" async></script>
```

## 필요한 OSGi 구성 추가 {#osgi-configurations}

범용 편집기를 사용하여 앱에서 AEM 컨텐츠를 편집하려면 AEM 내에서 CORS 및 쿠키 설정을 수행해야 합니다.

다음 [OSGi 구성은 AEM 작성 인스턴스에서 설정해야 합니다.](/help/implementing/deploying/configuring-osgi.md)

* `SameSite Cookies = None`-`com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`
* X-FRAME-OPTIONS 제거: 의 SAMEORIGIN 헤더 `org.apache.sling.engine.impl.SlingMainServlet`

### com.day.crx.security.token.impl.impl.TokenAuthenticationHandler {#samesite-cookies}

로그인 토큰 쿠키를 타사 도메인으로 AEM에 보내야 합니다. 따라서 동일한 사이트 쿠키를 `None`.

이 속성은 `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler` OSGi 구성.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
          token.samesite.cookie.attr="None" />
```

### org.apache.sling.engine.impl.SlingMainServlet {#sameorigin}

X-Frame-Options: SAMEORIGIN을 사용하면 iframe 내에서 AEM 페이지가 렌더링되지 않습니다. 헤더를 제거하면 페이지를 로드할 수 있습니다.

이 속성은 `org.apache.sling.engine.impl.SlingMainServlet` OSGi 구성.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="sling:OsgiConfig"
          sling.additional.response.headers="[X-Content-Type-Options=nosniff]"/>
```

## 페이지 인스트루먼트 {#instrument-page}

범용 편집기 서비스에는 [URN(Uniform Resource Name)](https://en.wikipedia.org/wiki/Uniform_Resource_Name) 편집 중인 앱의 컨텐츠에 대한 올바른 백엔드 시스템을 식별하고 활용합니다. 따라서 컨텐츠를 다시 컨텐츠 리소스에 매핑하려면 URN 스키마가 필요합니다.

페이지에 추가된 계측 속성은 대부분 [HTML 마이크로데이터,](https://developer.mozilla.org/en-US/docs/Web/HTML/Microdata) HTML을 보다 의미적이고 HTML 문서를 색인화할 수 있도록 하는 데 사용할 수 있는 업계 표준입니다.

### 연결 만들기 {#connections}

앱에서 사용되는 연결은 `<meta>` 페이지의 `<head>`.

```html
<meta name="urn:auecon:<referenceName>" content="<protocol>:<url>">
```

* `<referenceName>` - 연결을 식별하기 위해 문서에서 재사용되는 짧은 이름입니다. 예: `aemconnection`
* `<protocol>` - 사용할 범용 편집기 지속성 서비스의 지속성 플러그인을 나타냅니다. 예: `aem`
* `<url>` - 변경 사항을 유지할 시스템의 URL입니다. 예: `http://localhost:4502`

짧은 식별자 `auecon` Adobe 범용 편집기 연결을 의미합니다.

`itemid`은 `urn` 접두사를 사용하여 식별자를 줄입니다.

```html
itemid="urn:<referenceName>:<resource>"
```

* `<referenceName>` - 다음에서 언급된 명명된 참조입니다. `<meta>` 태그에 가깝게 포함했습니다. 예: `aemconnection`
* `<resource>` - 대상 시스템의 리소스에 대한 포인터입니다. 예: 다음과 같은 AEM 컨텐츠 경로 `/content/page/jcr:content`

>[!TIP]
>
>문서를 참조하십시오 [속성 및 유형](attributes-types.md) 범용 편집기에 필요한 데이터 속성 및 유형에 대한 자세한 내용은

### 연결 예 {#example}

```html
<html>
<head>
    <meta name="urn:auecon:aemconnection" content="aem:https://localhost:4502">
    <meta name="urn:auecon:fcsconnection" content="fcs:https://example.franklin.adobe.com/345fcdd">
</head>
<body>
        <aside>
          <ul itemscope itemid="urn:aemconnection:/content/example/list" itemtype="container">
            <li itemscope itemid="urn:aemconnection/content/example/listitem" itemtype="component">
              <p itemprop="name" itemtype="text">Jane Doe</p>
              <p itemprop="title" itemtype="text">Journalist</p>
              <img itemprop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" itemtype="image" alt="avatar"/>
            </li>
 
...
 
            <li itemscope itemid="urn:fcsconnection:/documents/mytext" itemtype="component">
              <p itemprop="name" itemtype="text">John Smith</p>
              <p itemid="urn:aemconnection/content/example/another-source" itemprop="title" itemtype="text">Photographer</p>
              <img itemprop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" itemtype="image" alt="avatar"/>
            </li>
          </ul>
        </aside>
</body>
</html>
```

## 범용 편집기를 사용할 준비가 되었습니다. {#youre-ready}

이제 앱이 범용 편집기를 사용하도록 구현되었습니다!

문서를 참조하십시오 [범용 편집기를 사용하여 컨텐츠 작성](authoring.md) 컨텐츠 작성자가 범용 편집기를 사용하여 컨텐츠를 만드는 것이 얼마나 쉽고 직관적인지 알아보십시오.

## 추가 리소스 {#additional-resources}

범용 편집기에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [범용 편집기 소개](introduction.md) - 범용 편집기를 사용하면 모든 구현에서 컨텐츠의 모든 측면을 편집할 수 있어 뛰어난 경험을 제공하고 컨텐츠 속도를 높이며 최신 개발자 경험을 제공할 수 있습니다.
* [범용 편집기를 사용하여 컨텐츠 작성](authoring.md) - 컨텐츠 작성자가 범용 편집기를 사용하여 컨텐츠를 만드는 것이 얼마나 쉽고 직관적인지를 알아봅니다.
* [범용 편집기를 사용하여 컨텐츠 게시](publishing.md) - 유니버설 시각적 편집기에서 콘텐츠를 게시하는 방법과 앱이 게시된 콘텐츠를 처리하는 방법을 알아봅니다.
* [범용 편집기 아키텍처](architecture.md) - 범용 편집기의 아키텍처와 서비스 및 레이어 간에 데이터가 어떻게 이동되는지 알아봅니다.
* [속성 및 유형](attributes-types.md) - 범용 편집기에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [범용 편집기 인증](authentication.md) - 유니버설 편집기가 인증되는 방법을 알아봅니다.
