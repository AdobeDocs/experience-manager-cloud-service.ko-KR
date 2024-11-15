---
title: AEM에서 Universal Editor 시작하기
description: Universal Editor에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: edef86c67becf3b8094196d39baa9e69d6c81777
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 72%

---


# AEM에서 Universal Editor 시작하기 {#getting-started}

Universal Editor에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.

>[!TIP]
>
>예를 바로 살펴보고 싶다면 [GitHub의 Universal Editor 샘플 앱](https://github.com/adobe/universal-editor-sample-editable-app)을 검토할 수 있습니다.

범용 편집기는 모든 소스에서 콘텐츠를 편집할 수 있지만 이 문서에서는 AEM 앱을 예로 사용합니다. 이 문서에서는 이러한 단계를 안내합니다.

## 페이지 계측 {#instrument-page}

Universal Editor 서비스에는 편집 중인 앱의 콘텐츠에 대한 올바른 백엔드 시스템을 식별하고 활용하기 위해 [균일 리소스 이름(URN)](https://en.wikipedia.org/wiki/Uniform_Resource_Name)이 필요합니다. 따라서 콘텐츠를 다시 콘텐츠 리소스에 매핑하려면 URN 스키마가 필요합니다.

### 연결 만들기 {#connections}

앱에서 사용되는 연결은 페이지의 `<head>`에 `<meta>` 태그로 저장됩니다.

```html
<meta name="urn:adobe:aue:<category>:<referenceName>" content="<protocol>:<url>">
```

* `<category>` - 두 가지 옵션이 있는 연결의 분류입니다.
   * `system` - 연결 끝점의 경우
   * `config` - [선택적 구성 설정 정의](#configuration-settings)에 대해
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

필요한 경우 연결 URN에서 `config` 접두사를 사용하여 서비스 및 확장 끝점을 설정할 수 있습니다.

Adobe이 호스팅하는 유니버설 편집기 서비스를 사용하지 않고 호스팅된 자체 버전을 사용하려면 메타 태그에서 이를 설정할 수 있습니다. 범용 편집기에서 제공하는 기본 서비스 끝점을 덮어쓰려면 고유한 서비스 끝점을 설정합니다.

* 메타 이름 - `urn:adobe:aue:config:service`
* 메타 콘텐츠 - `content="https://adobe.com"`(예)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

페이지에 대해 특정 확장만 활성화하려는 경우 메타 태그에서 설정할 수 있습니다. 확장을 가져오려면 확장 끝점을 설정합니다.

* 메타 이름: `urn:adobe:aue:config:extensions`
* 메타 콘텐츠: `content="https://adobe.com,https://anotherone.com,https://onemore.com"`(예)

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

