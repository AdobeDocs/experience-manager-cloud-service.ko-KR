---
title: AEM에서 범용 편집기 시작하기
description: 범용 편집기에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 100%

---


# AEM에서 범용 편집기 시작하기 {#getting-started}

범용 편집기에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.

>[!TIP]
>
>예를 바로 살펴보고 싶다면 [GitHub의 범용 편집기 샘플 앱](https://github.com/adobe/universal-editor-sample-editable-app)을 검토할 수 있습니다.

범용 편집기는 모든 소스의 콘텐츠를 편집할 수 있지만 이 문서에서는 AEM 앱을 예로 사용합니다. 이 문서에서는 이러한 단계를 안내합니다.

## 페이지 계측 {#instrument-page}

범용 편집기가 편집기에서 페이지를 렌더링하고 편집하려면 JavaScript 라이브러리가 필요합니다.

또한 범용 편집기 서비스에는 편집 중인 앱의 콘텐츠에 대한 올바른 백엔드 시스템을 식별하고 활용하기 위해 [균일 리소스 이름(URN)](https://en.wikipedia.org/wiki/Uniform_Resource_Name)이 필요합니다. 따라서 콘텐츠를 다시 콘텐츠 리소스에 매핑하려면 URN 스키마가 필요합니다.

### 범용 편집기 CORS 라이브러리 포함 {#cors-library}

범용 편집기를 앱에 연결하려면 앱에 범용 편집기 CORS 라이브러리가 포함되어야 합니다. 다음 스크립트를 앱에 추가합니다.

```html
 <script src="https://universal-editor-service.adobe.io/cors.js" async></script>
```

### 연결 만들기 {#connections}

앱에서 사용되는 연결은 페이지의 `<head>`에 `<meta>` 태그로 저장됩니다.

```html
<meta name="urn:adobe:aue:<category>:<referenceName>" content="<protocol>:<url>">
```

* `<category>` - 이는 두 가지 옵션으로 연결을 분류한 것입니다.
   * `system` - 연결 엔드포인트용
   * `config` - [선택적 구성 설정 정의](#configuration-settings)용
* `<referenceName>` - 연결을 식별하기 위해 문서에서 재사용되는 짧은 이름입니다. 예: `aemconnection`
* `<protocol>` - 범용 편집기 지속성 서비스의 어떤 지속성 플러그인을 사용할 것인지 나타냅니다. 예: `aem`
* `<url>` - 변경 사항이 지속되어야 하는 시스템의 URL입니다. 예: `http://localhost:4502`

식별자 `urn:adobe:aue:system`은 Adobe 범용 편집기 연결을 의미합니다.

`data-aue-resource`는 `urn` 접두사를 사용하여 식별자를 줄입니다.

```html
data-aue-resource="urn:<referenceName>:<resource>"
```

* `<referenceName>` - `<meta>` 태그에 언급되는 명명된 참조입니다. 예: `aemconnection`
* `<resource>` - 대상 시스템의 리소스에 대한 포인터입니다. 예: `/content/page/jcr:content`와 같은 AEM 콘텐츠 경로

>[!TIP]
>
>범용 편집기에 필요한 데이터 속성 및 유형에 대한 자세한 내용은 [속성 및 유형](attributes-types.md) 문서를 참조하십시오.

### 예시 연결 {#example}

```html
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

필요한 경우 연결 URN에서 `config` 접두사를 사용하여 서비스 및 확장 기능 엔드포인트를 설정할 수 있습니다.

Adobe에서 호스팅하는 범용 편집기 서비스를 사용하지 않고 자체 호스팅 버전을 사용하려면 메타 태그에서 이 설정을 지정할 수 있습니다. 범용 편집기에서 제공하는 기본 서비스 엔드포인트를 덮어쓰려면 다음을 수행하여 자체 서비스 엔드포인트를 설정합니다.

* 메타 이름 - `urn:adobe:aue:config:service`
* 메타 콘텐츠 - `content="https://adobe.com"` (예)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

특정 확장 기능만 페이지에 대해 활성화하려면 이를 메타 태그에 설정할 수 있습니다. 확장 기능을 가져오려면 다음을 수행하여 확장 기능 엔드포인트를 설정합니다.

* 메타 이름: `urn:adobe:aue:config:extensions`
* 메타 콘텐츠: `content="https://adobe.com,https://anotherone.com,https://onemore.com"` (예)

```html
<meta name="urn:adobe:aue:config:extensions" content="<url>,<url>,<url>">
```

## 범용 편집기를 여는 콘텐츠 경로 또는 `sling:resourceType`을 정의합니다. (선택 사항) {#content-paths}

[페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)를 사용하는 기존 AEM 프로젝트가 있는 경우, 콘텐츠 작성자가 페이지를 편집하면 해당 페이지가 페이지 편집기로 자동 열립니다. 콘텐츠 경로 또는 `sling:resourceType`을 기준으로 AEM이 어떤 편집기를 열지 정의하여, 선택한 콘텐츠에 어떤 편집기가 필요한지에 관계없이 작성자에게 매끄러운 경험을 제공할 수 있습니다.

1. 구성 관리자를 엽니다.

   `http://<host>:<port>/system/console/configMgr`

1. 목록에서 **범용 편집기 URL 서비스**&#x200B;를 찾아 **구성 값 편집**&#x200B;을 클릭합니다.

1. 범용 편집기를 여는 콘텐츠 경로 또는 `sling:resourceType`을 정의합니다.

   * **범용 편집기 열기 매핑** 필드에서 범용 편집기를 여는 경로를 제공합니다.
   * **범용 편집기로 열리는 Sling:resourceTypes** 필드에 리소스 목록을 제공합니다.

1. **저장**&#x200B;을 클릭합니다.

1. [externalizer 구성](/help/implementing/developing/tools/externalizer.md)을 확인하고 최소한 다음 예와 같이 로컬, 작성자 및 게시 환경이 설정되어 있는지 확인합니다.

   ```text
   "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
   "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
   "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]"
   ```

이러한 구성 단계가 완료되면 AEM에서 다음 순서대로 페이지에 대한 범용 편집기가 열립니다.

1. AEM은 `Universal Editor Opening Mapping` 아래의 매핑을 확인하고, 콘텐츠가 해당 매핑에 정의된 경로 아래에 있으면 해당 콘텐츠에 대한 범용 편집기가 열립니다.
1. `Universal Editor Opening Mapping`에 정의된 경로 아래에 없는 콘텐츠의 경우 AEM은 콘텐츠의 `resourceType`이 **범용 편집기로 열리는 Sling:resourceTypes**&#x200B;에 정의된 항목과 일치하는지 확인하고, 콘텐츠가 이러한 유형 중 하나와 일치하면 `${author}${path}.html`에서 범용 편집기가 열립니다.
1. 그렇지 않으면 AEM에서 페이지 편집기가 열립니다.

**범용 편집기 열기 매핑** 필드에서 매핑을 정의하는 데 다음 변수를 사용할 수 있습니다.

* `path`: 열고자 하는 리소스의 콘텐츠 경로
* `localhost`: 스키마가 없는 `localhost`에 대한 외부화 항목(예: `localhost:4502`)
* `author`: 스키마가 없는 작성자에 대한 외부화 항목(예:`localhost:4502`)
* `publish`: 스키마가 없는 게시에 대한 외부화 항목(예:`localhost:4503`)
* `preview`: 스키마가 없는 미리보기에 대한 외부화 항목(예:`localhost:4504`)
* `env`: 정의된 Sling 실행 모드에 기반한 `prod`, `stage`, `dev`
* `token`: `QueryTokenAuthenticationHandler`에 필요한 쿼리 토큰

### 매핑 예 {#example-mappings}

* AEM 작성자에서 `/content/foo` 아래의 모든 페이지를 엽니다.

   * `/content/foo:${author}${path}.html?login-token=${token}`
   * 이렇게 하면 `https://localhost:4502/content/foo/x.html?login-token=<token>`이 열립니다.

* 원격 NextJS 서버에서 `/content/bar` 아래의 모든 페이지를 열고 모든 변수를 정보로 제공합니다.

   * `/content/bar:nextjs.server${path}?env=${env}&author=https://${author}&publish=https://${publish}&login-token=${token}`
   * 이렇게 하면 `https://nextjs.server/content/bar/x?env=prod&author=https://localhost:4502&publish=https://localhost:4503&login-token=<token>`이 열립니다.

## 범용 편집기를 사용할 준비 완료 {#youre-ready}

이제 앱이 범용 편집기를 사용하도록 구성되었습니다.

콘텐츠 작성자가 범용 편집기를 사용하여 콘텐츠를 만드는 것이 얼마나 쉽고 직관적인지 알아보려면 [범용 편집기로 콘텐츠 작성](/help/sites-cloud/authoring/universal-editor/authoring.md)을 참조하십시오.

{{ue-headless-auth}}

## 추가 리소스 {#additional-resources}

범용 편집기에 대해 자세히 알아보려면 다음 문서를 참조하십시오.

* [범용 편집기 소개](introduction.md) - 범용 편집기를 통해 모든 구현에서 콘텐츠의 모든 측면을 편집하여 뛰어난 경험을 제공하고, 콘텐츠 속도를 높이고, 최신 개발자 경험을 제공하는 방법에 대해 알아봅니다.
* [범용 편집기로 콘텐츠 작성](/help/sites-cloud/authoring/universal-editor/authoring.md) - 콘텐츠 작성자가 범용 편집기를 사용하여 콘텐츠를 만드는 것이 얼마나 쉽고 직관적인지 알아봅니다.
* [범용 편집기로 콘텐츠 게시](/help/implementing/universal-editor/publishing.md) - 범용 편집기에서 콘텐츠를 게시하는 방법과 앱에서 게시된 콘텐츠를 처리하는 방법에 대해 알아봅니다.
* [범용 편집기 아키텍처](architecture.md) - 범용 편집기의 아키텍처 및 해당 서비스와 계층 간에 데이터가 흐르는 방식에 대해 알아봅니다.
* [속성 및 유형](attributes-types.md) - 범용 편집기에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [범용 편집기 인증](authentication.md) - 범용 편집기의 인증 방법에 대해 알아봅니다.

