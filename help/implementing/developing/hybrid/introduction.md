---
title: SPA 소개 및 연습
description: 이 문서에서는 SPA의 개념을 소개하고 저작 시 기본 SPA 응용 프로그램을 사용하여 기본 SPA 편집기와 관련된 방법을 설명합니다.
translation-type: tm+mt
source-git-commit: cdd92032c627740c66de7b2f3836fa1dcd2ee2ca
workflow-type: tm+mt
source-wordcount: '1930'
ht-degree: 1%

---


# SPA 소개 및 연습 {#spa-introduction}

단일 페이지 애플리케이션(SPA)을 통해 웹 사이트 사용자에게 매력적인 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크을 사용하여 사이트를 구축하고자 하며, 작성자는 이러한 프레임워크를 사용하여 구축한 사이트에 대해 AEM 내에서 컨텐츠를 완벽하게 편집하고자 합니다.

SPA Editor는 AEM에서 SPA을 지원하는 포괄적인 솔루션을 제공합니다. 이 문서에서는 저작을 위해 기본 SPA 응용 프로그램을 사용하는 과정을 소개하고 기본 AEM SPA 편집기와 관련된 방법을 설명합니다.

## 소개 {#introduction}

### 아티클 목표 {#article-objective}

이 문서에서는 간단한 SPA 애플리케이션을 사용하여 기본적인 컨텐츠 편집을 시연함으로써 SPA 편집기의 연습을 안내하기 전에 SPA의 기본 개념을 소개합니다. 그런 다음 페이지 구성, SPA 응용 프로그램이 AEM SPA 편집기와 관련 및 상호 작용하는 방법을 자세히 다룹니다.

이 소개 및 연습의 목적은 AEM 개발자에게 SPA이 관련이 있는 이유, 일반적으로 작동하는 방식, AEM SPA 편집기로 SPA을 처리하는 방법 및 표준 AEM 애플리케이션과 어떻게 다른지 시연하는 것입니다.

이 연습은 표준 AEM 기능 및 샘플 WKND SPA Project 앱을 기반으로 합니다. 팔로우하려면 GitHub에서 [샘플 WKND SPA 프로젝트 앱을 다운로드하여 설치하십시오.](https://github.com/adobe/aem-guides-wknd-spa)

>[!CAUTION]
>
>이 문서에서는 데모용으로만 [WKND SPA Project 앱](https://github.com/adobe/aem-guides-wknd-spa)을 사용합니다. 어떤 프로젝트 작업에도 사용해서는 안 됩니다.

>[!TIP]
>
>모든 AEM 프로젝트는 React 또는 Angular를 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 [AEM Project Tranype](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)을 활용해야 합니다.

### SPA 소개{#what-is-a-spa}

단일 페이지 애플리케이션(SPA)은 클라이언트 측에서 렌더링되고 주로 Javascript가 사용된다는 점에서 일반적인 페이지와 다릅니다. Ajax 호출에서 데이터를 로드하고 페이지를 동적으로 업데이트하는 것입니다. 대부분의 또는 모든 컨텐츠는 페이지와의 사용자 상호 작용에 따라 필요에 따라 비동기적으로 로드된 추가 리소스를 포함한 단일 페이지 로드에서 한 번 검색됩니다.

이를 통해 페이지 새로 고침이 필요하지 않으며, 사용자에게 매끄럽고 빠르며 기본 앱 경험과 같은 경험을 제공합니다.

AEM SPA Editor를 사용하면 프런트 엔드 개발자는 AEM 사이트에 통합할 수 있는 SPA을 제작할 수 있으므로 컨텐츠 작성자는 다른 AEM 컨텐츠과 같이 SPA 컨텐츠를 손쉽게 편집할 수 있습니다.

### SPA을 사용해야 하는 이유{#why-a-spa}

SPA은 기본 애플리케이션과 유사하게 더욱 빨라지고 유연해졌으며 웹 페이지 방문자뿐만 아니라 SPA 작업 방식의 특성상 마케터 및 개발자에게도 매력적인 경험을 제공합니다.

![SPA 혜택](assets/spa-benefits.png)

#### 방문자 수 {#visitors}

* 방문자는 컨텐츠와 상호 작용할 때 방문자와 유사한 경험을 원합니다.
* 페이지를 빠르게 할수록 더 많은 전환이 발생한다는 명확한 데이터가 있습니다.

#### 마케터 {#marketers}

* 마케터는 방문자가 컨텐츠와 완벽하게 교류하도록 유도할 수 있는 풍부한 네이티브 경험을 제공하고자 합니다.
* 개인화를 통해 이러한 경험을 보다 매력적인 경험으로 만들 수 있습니다.

#### 개발자 {#developers}

* 개발자는 컨텐츠와 프레젠테이션에 대한 우려 사항을 명확하게 구분하길 원합니다.
* 시스템을 깔끔하게 분리하면 독립적인 프런트 엔드 개발을 허용할 뿐만 아니라 확장 가능해집니다.

### SPA 작동 방식{#how-does-a-spa-work}

SPA의 주요 아이디어는 서버 지연으로 인한 지연을 최소화하기 위해 서버에 대한 호출과 의존도를 줄여 SPA이 기본 애플리케이션의 응답성에 접근한다는 것입니다.

기존의 순차적 웹 페이지에서는 바로 페이지에 필요한 데이터만 로드됩니다. 즉, 방문자가 다른 페이지로 이동할 때 추가 리소스를 위해 서버가 호출됩니다. 방문자가 페이지의 요소와 상호 작용하므로 추가 호출이 필요할 수 있습니다. 이 여러 호출은 페이지가 방문자의 요청을 따라잡아야 하므로 지연이나 지연을 일으킬 수 있습니다.

![순차적 경험과 유연한 경험](assets/spa-sequential-vs-fluid.png)

방문자가 모바일, 기본 앱에서 기대하는 것에 접근하는 보다 유동적인 경험을 위해 SPA은 첫 번째 로드 시 방문자에 필요한 모든 데이터를 로드합니다. 처음에는 시간이 조금 더 걸릴 수 있지만 이 경우 추가 서버 호출이 필요하지 않습니다.

클라이언트 쪽에서 렌더링하면 페이지 요소가 더 빠르게 반응하고 방문자가 페이지와의 상호 작용은 즉시 발생합니다. 필요한 추가 데이터는 페이지 속도를 최대화하기 위해 비동기식으로 호출됩니다.

>[!TIP]
>
>AEM에서 SPA이 작동하는 방법에 대한 자세한 내용은 다음 문서를 참조하십시오.
>* [AEM에서 반응 사용 시작](getting-started-react.md)
>* [AEM에서 Angular를 사용하여 시작](getting-started-angular.md)

>
>
SPA Editor의 디자인, 아키텍처 및 기술 워크플로우에 대한 자세한 내용은 다음 문서를 참조하십시오.
>* [SPA 편집기 개요](editor-overview.md).


## SPA {#content-editing-experience-with-spa}의 컨텐츠 편집 경험

SPA SPA Editor를 활용하도록 AEM이 구축되면 컨텐츠 작성자는 컨텐츠를 편집하고 만들 때 아무런 차이도 느끼지 않습니다. 공통 AEM 기능을 사용할 수 있으며 작성자의 워크플로우를 변경할 필요가 없습니다.

1. AEM에서 WKND SPA Project 앱을 편집합니다.

   `http://localhost:4502/editor.html/content/wknd-spa-react/us/en/home.html`

   ![WKND SPA Project 홈](assets/wknd-home.png)

1. 텍스트 구성 요소를 선택하면 도구 모음이 다른 구성 요소와 같이 나타납니다. **편집**&#x200B;을 선택하십시오.

   ![텍스트 구성 요소 선택](assets/wknd-text.png)

1. AEM 내에서 컨텐츠를 정상적으로 편집하고 변경 사항이 지속된다는 점을 참고하십시오.

   ![텍스트 편집](assets/wknd-edit-text.png)

1. 자산 브라우저를 사용하여 새 이미지를 이미지 구성 요소로 드래그하여 놓습니다.

   ![이미지 자산 삭제](assets/wkdn-drop-image.png)

1. 변경 사항이 유지됩니다.

   ![지속된 이미지](assets/wknd-change-persisted.png)

페이지에서 추가 구성 요소를 드래그 앤 드롭하거나 구성 요소를 재배치하고 레이아웃을 수정하는 등 SPA이 아닌 다른 애플리케이션에서처럼 추가 작성 도구가 지원됩니다.

>[!NOTE]
>
>SPA 편집기는 응용 프로그램의 DOM을 수정하지 않습니다. SPA 자체도 DOM을 책임집니다.
>
>이 문서의 작동 방식을 확인하려면 [SPA Apps 및 AEM SPA 편집기](#spa-apps-and-the-aem-spa-editor)의 다음 섹션으로 계속하십시오.

## SPA 앱 및 AEM SPA 편집기 {#spa-apps-and-the-aem-spa-editor}

SPA이 최종 사용자에 대해 동작하고 SPA 페이지를 검사하는 방법을 경험하면 AEM에서 SPA 편집기와 SAP 앱이 작동하는 방식을 더 잘 이해할 수 있습니다.

### SPA 응용 프로그램 사용 {#using-an-spa-application}

1. WKND SPA Project 응용 프로그램을 게시 서버에 로드하거나 페이지 편집기의 **페이지 정보** 메뉴에서 **게시됨으로 보기** 옵션을 사용하여 로드합니다.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![WKND SPA 프로젝트 미리 보기 홈](assets/wknd-preview.png)

   하위 페이지, 메뉴 및 아티클 카드로의 탐색을 비롯한 페이지 구조를 확인합니다.

1. 메뉴를 사용하여 하위 페이지로 이동하고 새로 고칠 필요 없이 페이지가 즉시 로드되는지 확인합니다.

   ![WKND SPA 프로젝트 페이지 1](assets/wknd-page1.png)

1. 브라우저에 내장된 개발자 도구를 열고 하위 페이지를 탐색할 때 네트워크 활동을 모니터링합니다.

   ![네트워크 활동](assets/wknd-network-activity.png)

   앱에서 페이지로 이동할 때 트래픽이 거의 없습니다. 페이지가 다시 로드되지 않고 새 이미지만 요청됩니다.

   SPA은 클라이언트 쪽에서 컨텐츠와 라우팅을 완전히 관리합니다.

하위 페이지를 탐색할 때 페이지가 다시 로드되지 않으면 어떻게 로드됩니까?

다음 섹션인 [SPA 응용 프로그램 로드](#loading-a-spa-application)에서는 SPA을 로드하는 역학 및 컨텐트를 동기적으로 그리고 비동기적으로 로드하는 방법에 대해 자세히 알아봅니다.

### SPA 응용 프로그램 로드 중 {#loading-a-spa-application}

1. 아직 로드되지 않은 경우 We.Retail 저널 애플리케이션을 게시 서버에 로드하거나 페이지 편집기의 **페이지 정보** 메뉴에서 **게시됨으로 보기** 옵션을 사용하여 로드합니다.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![WKND SPA 프로젝트 미리 보기](assets/wknd-preview.png)

1. 브라우저의 기본 제공 도구를 사용하여 페이지의 소스를 봅니다.
1. 소스의 내용은 제한됩니다.

   ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8"/>
        <title>WKND SPA React Home Page</title>
   
        <meta name="template" content="spa-page-template"/>
        <meta name="viewport" content="width=device-width, initial-scale=1"/>
   
    <link rel="stylesheet" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-base.min.css" type="text/css">
   
    <meta name="theme-color" content="#000000"/>
    <link rel="icon" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react/resources/favicon.ico"/>
    <link rel="apple-touch-icon" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react/resources/logo192.png"/>
    <link rel="manifest" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react/resources/manifest.json"/>
   
    <!-- AEM page model -->
    <meta property="cq:pagemodel_root_url" content="/content/wknd-spa-react/us/en.model.json"/>
    <link href="//fonts.googleapis.com/css?family=Source+Sans+Pro:400,600|Asar&display=swap" rel="stylesheet"/>
    <meta property="cq:datatype" content="JSON"/>
    <meta property="cq:wcmmode" content="edit"/>
   
    <link rel="stylesheet" href="/libs/cq/gui/components/authoring/editors/clientlibs/internal/page.min.css" type="text/css">
    <link rel="stylesheet" href="/etc.clientlibs/wcm/foundation/clientlibs/main.min.css" type="text/css">
    <script type="text/javascript" src="/libs/cq/gui/components/authoring/editors/clientlibs/internal/messaging.min.js"></script>
    <script type="text/javascript" src="/libs/cq/gui/components/authoring/editors/clientlibs/utils.min.js"></script>
    <script type="text/javascript" src="/libs/granite/author/deviceemulator/clientlibs.min.js"></script>
    <script type="text/javascript" src="/libs/cq/gui/components/authoring/editors/clientlibs/internal/page.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/wcm/foundation/clientlibs/main.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/clientlibs/granite/jquery.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/clientlibs/granite/utils.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/clientlibs/granite/jquery/granite.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/foundation/clientlibs/jquery.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/foundation/clientlibs/shared.min.js"></script>
   
    <!--cq{"decorated":false,"type":"cq/cloudconfig/components/scripttags/header","path":"/content/wknd-spa-react/us/en/home/jcr:content/cloudconfig-header","structurePath":"/content/wknd-spa-react/us/en/home/jcr:content/cloudconfig-header","selectors":null,"servlet":"Script /libs/cq/cloudconfig/components/scripttags/header/header.html","totalTime":2,"selfTime":2}-->
   
    <link rel="stylesheet" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react.min.css" type="text/css">
   
    </head>
   
    <body class="page basicpage">
        <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="spa-root"></div>
   
    <script type="text/javascript" src="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-react.min.js"></script>
   
    <script type="text/javascript" src="/etc.clientlibs/core/wcm/components/commons/site/clientlibs/container.min.js"></script>
    <script type="text/javascript" src="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-base.min.js"></script>
   
    <script type="text/javascript" src="/libs/cq/gui/components/authoring/editors/clientlibs/internal/pagemodel/messaging.min.js"></script>
   
    <link rel="stylesheet" href="/etc.clientlibs/wknd-spa-react/clientlibs/clientlib-author.min.css" type="text/css">
   
    <!--cq{"decorated":true,"type":"cq/cloudserviceconfigs/components/servicecomponents","path":"/content/wknd-spa-react/us/en/home/jcr:content/cloudservices","selectors":null,"servlet":"Script /libs/cq/cloudserviceconfigs/components/servicecomponents/servicecomponents.jsp","totalTime":2,"selfTime":2}-->
   
    <!--cq{"decorated":false,"type":"cq/cloudconfig/components/scripttags/footer","path":"/content/wknd-spa-react/us/en/home/jcr:content/cloudconfig-footer","structurePath":"/content/wknd-spa-react/us/en/home/jcr:content/cloudconfig-footer","selectors":null,"servlet":"Script /libs/cq/cloudconfig/components/scripttags/footer/footer.html","totalTime":2,"selfTime":2}-->
   
    </body>
    </html>
    <!--cq{"decorated":false,"type":"wknd-spa-react/components/page","path":"/content/wknd-spa-react/us/en/home/jcr:content","selectors":null,"servlet":"Script /apps/spa-project-core/components/page/page.html","totalTime":39,"selfTime":33}-->
   ```

   페이지의 본문 내에 콘텐츠가 없습니다. 주로 스타일 시트 및 `clientlib-react.min.js`와 같은 다양한 스크립트에 대한 호출로 구성됩니다.

   이러한 스크립트는 이 애플리케이션의 기본 드라이버이며 모든 컨텐츠를 렌더링할 책임이 있습니다.

1. 브라우저에 내장된 툴을 사용하여 페이지를 검사할 수 있습니다. 완전히 로드된 DOM의 컨텐츠를 참조하십시오.

   ![WKND SPA 프로젝트](assets/wknd-dom.png)

1. 검사기의 네트워크 탭으로 전환하고 페이지를 다시 로드합니다.

   이미지 요청을 무시하고 페이지에 대해 로드되는 기본 리소스는 페이지 자체, CSS, 반응형 Javascript, 해당 종속성 및 페이지의 JSON 데이터입니다.

   ![WKND SPA 프로젝트 네트워크 활동](assets/wknd-network.png)

1. 새 탭에서 `home.model.json`을 로드합니다.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.model.json`

   ![WKND SPA 프로젝트 홈 페이지의 JSON](assets/wknd-json.png)

   AEM SPA 편집기는 [AEM 컨텐츠 서비스](/help/assets/content-fragments/content-fragments.md)를 활용하여 페이지의 전체 컨텐츠를 JSON 모델로 전달합니다.

   Sling Models는 특정 인터페이스를 구현하여 SPA에 필요한 정보를 제공합니다. JSON 데이터의 배달은 각 구성 요소(페이지, 단락, 구성 요소 등)에 하향 위임됩니다.

   각 구성 요소는 표시되는 요소와 렌더링하는 방법을 선택합니다(HTL을 사용하는 서버측 또는 [반응] 또는 [각진]을 사용하는 클라이언트측). 이 문서에서는 React를 사용한 클라이언트측 렌더링에 중점을 둡니다.

1. 또한 모델은 동기적으로 로드되도록 페이지를 함께 그룹화하여 필요한 페이지 다시 로드 횟수를 줄일 수 있습니다.

   We.Retail 저널의 예에서 방문자가 일반적으로 모든 페이지를 방문하기 때문에 `home`, `page-1`, `page-2` 및 `page-3` 페이지가 동기식으로 로드됩니다.

   이 동작은 필수 사항이 아니며 완전히 정의할 수 있습니다.

   ![WKND SPA 프로젝트 항목 그룹화](assets/wknd-pages.png)

1. 동작의 이러한 차이를 보려면 `home` 페이지를 다시 로드하고 검사기의 네트워크 활동을 지웁니다. 페이지 메뉴에서 `page-1`으로 이동하여 네트워크 활동만이 `page-1`의 이미지에 대한 요청임을 확인하십시오. `page-1` 자체도 로드할 필요가 없습니다.

   ![WKND SPA 프로젝트 페이지-1 네트워크 활동](assets/wknd-page1-network.png)

### SPA 편집기와의 상호 작용 {#interaction-with-the-spa-editor}

샘플 WKND SPA Project 응용 프로그램을 사용하면 앱이 어떻게 동작하고 제작될 수 있는지, 게시 시 로드되는지를 알 수 있으며, JSON 컨텐츠 전달과 리소스 비동기 로딩에 대한 컨텐츠 서비스를 활용할 수 있습니다.

또한 컨텐츠 작성자의 경우 SPA 편집기를 사용한 컨텐츠 제작은 AEM 내에서 매끄럽게 이루어집니다.

다음 섹션에서는 SPA Editor가 SPA 구성 요소 내의 구성 요소를 AEM 구성 요소와 연계하여 이러한 매끄러운 편집 환경을 구현할 수 있는 계약을 살펴봅니다.

1. 편집기에서 WKND SPA Project 응용 프로그램을 로드하고 **Preview** 모드로 전환합니다.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

1. 브라우저의 내장된 개발자 도구를 사용하여 페이지의 컨텐츠를 검사합니다. 선택 도구를 사용하여 페이지에서 편집 가능한 구성 요소를 선택하고 요소 세부 사항을 봅니다.

   구성 요소에 새 데이터 속성 `data-cq-data-path`이(가) 있습니다.

   ![WKND SPA 프로젝트 요소 검사](assets/wknd-inspector.png)

   예

   `data-cq-data-path="/content/wknd-spa-react/us/en/home/jcr:content/root/responsivegrid/text`

   이 경로를 사용하면 각 구성 요소의 편집 컨텍스트 구성 개체를 검색하고 연결할 수 있습니다.

   이것은 편집자가 이것을 SPA 내에서 편집 가능한 구성 요소로 인식하기 위해 필요한 유일한 마크업 속성입니다. 이 속성을 기반으로 SPA 편집기는 구성 요소와 연관된 편집 가능한 구성을 판단하여 올바른 프레임, 도구 모음 등을 확인합니다. 가 로드되었습니다.

   자리 표시자를 표시하거나 자산을 드래그하여 놓는 기능을 위해 일부 특정 클래스 이름도 추가되었습니다.

   >[!NOTE]
   >
   >이 동작은 편집 가능한 각 구성 요소에 대해 삽입된 `cq` 요소가 있는 AEM의 서버측 렌더링된 페이지와 다릅니다.
   >
   >SPA Editor에서 이 방법을 사용하면 사용자 지정 요소를 주입할 필요가 없으며 추가 데이터 속성만 의존하므로 프런트 엔드 개발자는 마크업을 보다 간단하게 할 수 있습니다.

## 다음 단계 {#next-steps}

이제 AEM의 SPA 편집 경험과 SPA과 SPA 편집기의 상관관계를 이해하면 SPA의 제작 방식을 보다 심층적으로 이해할 수 있습니다.

* [AEM에서 SPA 시작하기 - ](getting-started-react.md) 리액티트를 사용하여 기본 SPA이 AEM에서 SPA 편집기로 작동되도록 구축된 방법을 설명합니다. 반응
* [AEM에서 SPA 시작하기(](getting-started-angular.md) Angulareusing) - AEM에서 SPA Editor와 함께 작동하도록 기본 SPA을 어떻게 구축하는지 Angular
* [SPA 편집기 ](editor-overview.md) 오버뷰에서는 AEM과 SPA 간의 통신 모델에 대해 더 자세히 살펴봅니다.
* [AEM용 SPA 개발](developing.md) 에서는 프런트 엔드 개발자가 AEM용 SPA을 개발하는 방법뿐만 아니라 SPA과 AEM 아키텍처와 상호 작용하는 방법을 설명합니다.
