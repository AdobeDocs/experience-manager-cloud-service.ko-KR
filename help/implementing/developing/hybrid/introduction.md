---
title: SPA 소개 및 연습
description: 이 문서에서는 SPA의 개념을 소개하고 기본적인 SPA 응용 프로그램을 저작하기 위해 사용하며 기본 AEM SPA Editor와 관련된 방식을 설명합니다.
translation-type: tm+mt
source-git-commit: cdd92032c627740c66de7b2f3836fa1dcd2ee2ca
workflow-type: tm+mt
source-wordcount: '1930'
ht-degree: 1%

---


# SPA 소개 및 연습 {#spa-introduction}

단일 페이지 애플리케이션(SPA)을 통해 웹 사이트 사용자에게 매력적인 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크을 사용하여 사이트를 구축하고자 하며, 작성자는 이러한 프레임워크를 사용하여 구축된 사이트에서 AEM의 컨텐츠를 매끄럽게 편집하고자 합니다.

SPA Editor는 AEM 내에서 SPA을 지원하는 포괄적인 솔루션을 제공합니다. 이 문서에서는 저작에 기본 SPA 응용 프로그램을 사용하는 과정을 소개하고 기본 AEM SPA 편집기와 관련된 방법을 설명합니다.

## 소개 {#introduction}

### 아티클 목표 {#article-objective}

이 문서에서는 간단한 SPA 애플리케이션을 사용하여 기본적인 컨텐츠 편집을 시연함으로써 SPA 편집기의 연습을 통해 독자를 안내하기 전에 SPA의 기본 개념을 설명합니다. 그런 다음 페이지 구성과 SPA 응용 프로그램이 AEM SPA Editor와 관련되고 상호 작용하는 방법을 자세히 다룹니다.

이 소개 및 연습의 목적은 AEM 개발자에게 SPA이 연관성 있는 이유,가 일반적으로 작동하는 방식, AEM SPA 편집기에서 SPA을 처리하는 방법 및 표준 AEM 애플리케이션과 어떻게 다른지 시연하는 것입니다.

이 연습은 표준 AEM 기능과 샘플 WKND SPA Project 앱을 기반으로 합니다. 팔로우하려면 GitHub에서 샘플 WKND SPA 프로젝트 앱을 다운로드하여 설치하십시오.[](https://github.com/adobe/aem-guides-wknd-spa)

>[!CAUTION]
>
>이 문서에서는 데모용으로만 [WKND SPA 프로젝트 앱](https://github.com/adobe/aem-guides-wknd-spa)을 사용합니다. 어떤 프로젝트 작업에도 사용되어서는 안 됩니다.

>[!TIP]
>
>모든 AEM 프로젝트는 React 또는 Angular를 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 [AEM Project Tranype](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)을 활용해야 합니다.

### SPA 소개{#what-is-a-spa}

단일 페이지 애플리케이션(SPA)은 클라이언트 측에서 렌더링되고 주로 Javascript를 기반으로 하며 데이터를 로드하고 페이지를 동적으로 업데이트하는 Ajax 호출에 의존한다는 점에서 일반 페이지와 다릅니다. 대부분의 또는 모든 컨텐츠는 페이지와의 사용자 상호 작용에 따라 필요에 따라 비동기적으로 로드된 추가 리소스를 사용하여 단일 페이지를 로드할 때 한 번 검색됩니다.

이를 통해 페이지 새로 고침이 필요하지 않으며, 매끄럽고 빠르며 기본 앱 경험과 같은 경험을 사용자에게 제공합니다.

SPA Editor를 사용하면 프런트 엔드 개발자는 AEM 사이트에 통합할 수 있는 SPA을 제작할 수 있으므로 컨텐츠 작성자는 다른 AEM 컨텐츠처럼 손쉽게 SPA 컨텐츠를 편집할 수 있습니다.

### SPA을 사용해야 하는 이유{#why-a-spa}

SPA은 기본 애플리케이션과 마찬가지로 빨라지고 유연하며 보다 매력적인 경험을 제공함으로써 웹 페이지 방문자뿐만 아니라 SPA 작업 방식의 특성상 마케터와 개발자에게 매력적인 경험을 제공합니다.

![SPA 혜택](assets/spa-benefits.png)

#### 방문자 수 {#visitors}

* 방문자는 컨텐츠와 상호 작용할 때 원초적인 경험을 원합니다.
* 페이지가 빠르게 전환할수록 더 많은 전환이 발생한다는 명확한 데이터가 있습니다.

#### 마케터 {#marketers}

* 마케터는 방문자가 컨텐츠에 완전히 매료되도록 유도할 수 있는 토착적이고 풍부한 경험을 제공하고자 합니다.
* 개인화를 통해 이러한 경험을 보다 매력적으로 만들 수 있습니다.

#### 개발자 {#developers}

* 개발자는 컨텐츠와 프레젠테이션에 대한 우려 사항을 명확하게 구분해야 합니다.
* 깔끔한 분리를 통해 시스템은 확장 가능하고 독립적인 프런트 엔드 개발을 할 수 있습니다.

### SPA 작동 방식{#how-does-a-spa-work}

SPA의 주요 아이디어는 SPA이 기본 애플리케이션의 응답성에 접근하도록 서버 지연으로 인한 지연을 최소화하기 위해 서버에 대한 호출과 의존도를 줄이는 것입니다.

기존의 순차적 웹 페이지에서는 바로 페이지에 필요한 데이터만 로드됩니다. 즉, 방문자가 다른 페이지로 이동할 때 추가 리소스를 위해 서버가 호출됩니다. 방문자가 페이지의 요소와 상호 작용하므로 추가 호출이 필요할 수 있습니다. 페이지가 방문자의 요청을 따라잡아야 하므로 이러한 여러 개의 호출로 인해 지연이나 지연이 생길 수 있습니다.

![순차적 경험과 유동적인 경험](assets/spa-sequential-vs-fluid.png)

방문자가 모바일, 기본 앱에서 기대하는 것을 접근하는 보다 유동적인 경험을 위해 SPA은 첫 번째 로드 시 방문자에 필요한 모든 데이터를 로드합니다. 처음에는 시간이 조금 더 걸릴 수 있지만 이 경우 추가 서버 호출을 수행할 필요가 없습니다.

클라이언트 쪽에서 렌더링하면 페이지 요소가 빠르게 반응하며 방문자가 페이지와의 상호 작용은 즉시 발생합니다. 필요한 추가 데이터는 페이지 속도를 최대화하기 위해 비동기식으로 호출됩니다.

>[!TIP]
>
>AEM에서 SPA이 작동하는 방법에 대한 자세한 내용은 다음 문서를 참조하십시오.
>* [반응을 사용하여 AEM에서 SPA 시작하기](getting-started-react.md)
>* [Angular를 사용하여 AEM에서 SPA 시작하기](getting-started-angular.md)

>
>
SPA Editor의 디자인, 아키텍처 및 기술 워크플로우에 대한 자세한 내용은 다음 문서를 참조하십시오.
>* [SPA 편집기 개요](editor-overview.md).


## SPA {#content-editing-experience-with-spa}의 컨텐츠 편집 경험

AEM SPA Editor를 활용할 수 있도록 SPA을 구축하면 컨텐츠 작성자는 컨텐츠를 편집하고 제작할 때 아무런 차이도 표시되지 않습니다. 일반적인 AEM 기능을 사용할 수 있으며 작성자의 워크플로우를 변경할 필요가 없습니다.

1. AEM에서 WKND SPA Project 앱을 편집합니다.

   `http://localhost:4502/editor.html/content/wknd-spa-react/us/en/home.html`

   ![WKND SPA 프로젝트 홈](assets/wknd-home.png)

1. 텍스트 구성 요소를 선택하면 다른 구성 요소에 대해 도구 모음이 표시됩니다. **편집**&#x200B;을 선택하십시오.

   ![텍스트 구성 요소 선택](assets/wknd-text.png)

1. AEM 내에서 컨텐츠를 정상적으로 편집하고 변경 사항이 지속됨을 확인합니다.

   ![텍스트 편집](assets/wknd-edit-text.png)

1. 자산 브라우저를 사용하여 새 이미지를 이미지 구성 요소로 드래그하여 놓습니다.

   ![이미지 자산 삭제](assets/wkdn-drop-image.png)

1. 변경 사항이 지속됩니다.

   ![지속되는 이미지](assets/wknd-change-persisted.png)

페이지에서 추가 구성 요소를 드래그 앤 드롭하거나, 구성 요소를 다시 정렬하고, 레이아웃을 수정하는 것과 같은 추가 제작 도구는 SPA이 아닌 다른 응용 프로그램에서처럼 지원됩니다.

>[!NOTE]
>
>SPA 편집기는 응용 프로그램의 DOM을 수정하지 않습니다. SPA 자체도 DOM을 책임집니다.
>
>이 작동 방식을 보려면 이 문서 [SPA Apps 및 AEM SPA Editor](#spa-apps-and-the-aem-spa-editor)의 다음 섹션으로 계속하십시오.

## SPA 앱 및 AEM SPA 편집기 {#spa-apps-and-the-aem-spa-editor}

SPA이 최종 사용자를 위해 동작하고 SPA 페이지를 검사하는 방식을 통해 SAP 앱이 AEM에서 SPA 편집기와 작동하는 방식을 더 잘 이해할 수 있습니다.

### SPA 응용 프로그램 사용 {#using-an-spa-application}

1. WKND SPA Project 응용 프로그램을 게시 서버에 로드하거나 페이지 편집기의 **페이지 정보** 메뉴에서 **게시됨으로 보기** 옵션을 사용하여 로드합니다.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![WKND SPA 프로젝트 미리 보기 홈](assets/wknd-preview.png)

   하위 페이지, 메뉴 및 아티클 카드로 이동하는 등 페이지 구조를 확인합니다.

1. 메뉴를 사용하여 하위 페이지로 이동하고 새로 고칠 필요 없이 페이지가 즉시 로드되는지 확인합니다.

   ![WKND SPA 프로젝트 페이지 1](assets/wknd-page1.png)

1. 브라우저에서 내장된 개발자 도구를 열고 하위 페이지를 탐색할 때 네트워크 활동을 모니터링할 수 있습니다.

   ![네트워크 활동](assets/wknd-network-activity.png)

   앱에서 페이지로 이동할 때 트래픽이 거의 없습니다. 페이지가 다시 로드되지 않고 새 이미지만 요청됩니다.

   SPA은 클라이언트 측에서 완전히 컨텐츠와 라우팅을 관리합니다.

하위 페이지를 탐색할 때 페이지가 다시 로드되지 않으면 어떻게 로드됩니까?

다음 섹션인 [SPA 응용 프로그램 로드](#loading-a-spa-application)에서는 SPA을 로드하는 역학 및 컨텐츠를 동기적으로 및 비동기적으로 로드하는 방법을 자세히 살펴봅니다.

### SPA 응용 프로그램 로드 중 {#loading-a-spa-application}

1. 아직 로드되지 않은 경우, We.Retail 저널 애플리케이션을 게시 서버에 로드하거나 페이지 편집기의 **페이지 정보** 메뉴에서 **게시됨으로 보기** 옵션을 사용하여 로드합니다.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![WKND SPA 프로젝트 미리 보기](assets/wknd-preview.png)

1. 브라우저의 내장된 도구를 사용하여 페이지의 소스를 봅니다.
1. 소스의 컨텐츠는 제한되어 있습니다.

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

   페이지에 본문 내에 내용이 없습니다. 주로 스타일 시트 및 `clientlib-react.min.js`와 같은 다양한 스크립트에 대한 호출로 구성됩니다.

   이러한 스크립트는 이 애플리케이션의 기본 드라이버이며 모든 컨텐츠를 렌더링하는 작업을 수행합니다.

1. 브라우저에 내장된 툴을 사용하여 페이지를 검사할 수 있습니다. 완전히 로드된 DOM의 컨텐츠를 확인합니다.

   ![WKND SPA 프로젝트](assets/wknd-dom.png)

1. 관리자의 네트워크 탭으로 전환하고 페이지를 다시 로드합니다.

   이미지 요청을 무시하고 페이지에 대해 로드된 기본 리소스는 페이지 자체, CSS, React Javascript, 해당 종속성 및 페이지에 대한 JSON 데이터입니다.

   ![WKND SPA 프로젝트 네트워크 활동](assets/wknd-network.png)

1. 새 탭에서 `home.model.json`을 로드합니다.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.model.json`

   ![WKND SPA 프로젝트 홈 페이지의 JSON](assets/wknd-json.png)

   AEM SPA 편집기는 [AEM Content Services](/help/assets/content-fragments/content-fragments.md)를 활용하여 페이지의 전체 컨텐츠를 JSON 모델로 전달합니다.

   Sling Models는 특정 인터페이스를 구현하여 SPA에 필요한 정보를 제공합니다. JSON 데이터 배달은 각 구성 요소(페이지, 단락, 구성 요소 등)에 아래쪽으로 위임됩니다.

   각 구성 요소는 표시되는 요소와 렌더링하는 방법을 선택합니다(HTL과 서버측 또는 [반응] 또는 [각도]와 함께 클라이언트측). 이 문서는 React를 사용한 클라이언트측 렌더링에 중점을 둡니다.

1. 또한 모델은 동기적으로 로드되도록 페이지를 그룹화하여 필요한 페이지 다시 로드 수를 줄일 수도 있습니다.

   We.Retail 저널의 예에서 방문자는 일반적으로 모든 페이지를 방문하므로 `home`, `page-1`, `page-2` 및 `page-3` 페이지가 동기식으로 로드됩니다.

   이 동작은 필수가 아니며 완전히 정의할 수 있습니다.

   ![WKND SPA 프로젝트 항목 그룹화](assets/wknd-pages.png)

1. 동작의 이러한 차이를 보려면 `home` 페이지를 다시 로드하고 관리자의 네트워크 활동을 지웁니다. 페이지 메뉴에서 `page-1`으로 이동하여 네트워크 활동만 `page-1` 이미지에 대한 요청임을 확인하십시오. `page-1` 자체적으로 로드할 필요가 없습니다.

   ![WKND SPA 프로젝트 페이지-1 네트워크 활동](assets/wknd-page1-network.png)

### SPA 편집기와의 상호 작용 {#interaction-with-the-spa-editor}

샘플 WKND SPA Project 애플리케이션을 사용하면 앱이 어떻게 동작하고 제작되는지 명확히 알 수 있고, 게시할 때 로드됩니다. JSON 컨텐츠 전달을 위한 컨텐츠 서비스 및 리소스의 비동기 로딩을 활용합니다.

또한 컨텐츠 작성자의 경우 SPA 편집기를 사용하여 컨텐츠를 만드는 것은 AEM 내에서 매끄럽게 이루어집니다.

다음 섹션에서는 SPA Editor가 SPA 구성 요소 내의 구성 요소를 AEM 구성 요소와 연계하여 이러한 매끄러운 편집 환경을 제공할 수 있도록 하는 계약을 살펴봅니다.

1. 편집기에서 WKND SPA 프로젝트 응용 프로그램을 로드하고 **미리 보기** 모드로 전환합니다.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

1. 브라우저의 내장된 개발자 도구를 사용하여 페이지의 컨텐츠를 검사합니다. 선택 도구를 사용하여 페이지에서 편집 가능한 구성 요소를 선택하고 요소 세부 사항을 봅니다.

   구성 요소에는 새 데이터 속성 `data-cq-data-path`이 있습니다.

   ![WKND SPA 프로젝트 요소 검사](assets/wknd-inspector.png)

   예

   `data-cq-data-path="/content/wknd-spa-react/us/en/home/jcr:content/root/responsivegrid/text`

   이 경로를 사용하면 각 구성 요소의 편집 컨텍스트 구성 객체를 검색하고 연결할 수 있습니다.

   편집자가 SPA 내에서 이 구성 요소를 편집 가능한 구성 요소로 인식하는 데 필요한 유일한 마크업 속성입니다. 이 속성을 기반으로 SPA 편집기는 구성 요소와 연결된 편집 가능한 구성을 판단하여 올바른 프레임, 도구 모음 등을 확인합니다. 가 로드되었습니다.

   자리 표시자를 표시하거나 자산 드래그하여 놓기 기능을 위해 일부 특정 클래스 이름도 추가되었습니다.

   >[!NOTE]
   >
   >이 동작은 편집 가능한 각 구성 요소에 대해 `cq` 요소가 삽입된 AEM의 서버측 렌더링된 페이지와 다릅니다.
   >
   >SPA Editor에서 이 방법을 사용하면 사용자 정의 요소를 주입할 필요가 없고 추가 데이터 속성만 의존하므로 마크업이 프런트 엔드 개발자에게 더 간편해집니다.

## 다음 단계 {#next-steps}

이제 AEM의 SPA 편집 경험과 SPA이 SPA 편집기와 어떻게 관련이 있는지 이해했다면 SPA의 구축 방법을 보다 심도 있게 살펴볼 수 있습니다.

* [Reactact를 사용하여 AEM에서 SPA으로 시작하는 방법](getting-started-react.md) 은 React를 사용하여 AEM에서 SPA Editor에서 작동하는 기본 SPA을 어떻게 구축하는지 보여줍니다
* [Angularageusing AEM에서 SPA 시작하기](getting-started-angular.md) 는 Angular를 사용하여 AEM에서 SPA 편집기로 작업할 기본 SPA을 빌드하는 방법을 보여줍니다
* [SPA ](editor-overview.md) Editor Overview를 통해 AEM과 SPA 간의 통신 모델에 대해 더 자세히 살펴봅니다.
* [AEM용 SPA 개발](developing.md) 은 AEM용 SPA을 개발하기 위해 프런트 엔드 개발자의 참여를 유도하는 방법뿐만 아니라 SPA과 AEM 아키텍처가 어떻게 상호 작용하는지 설명합니다.
