---
title: 외부 웹 페이지에 적응형 양식을 임베드하는 방법
description: 웹 사이트에 적응형 Forms을 임베드하는 방법에 대해 알아봅니다.
topic-tags: author
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 00b8cd79-bf2d-4001-b2d6-1b020c868008
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 50%

---

# 외부 웹 페이지에 적응형 양식 임베드{#embed-adaptive-form-in-external-web-page}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-external-web-page.html?lang=ko) |
| AEM as a Cloud Service | 이 문서 |

[AEM Sites 페이지에서 적응형 양식을 임베드](/help/forms/embed-adaptive-form-aem-sites.md)하거나 AEM 외부에 호스트된 웹 페이지를 임베드할 수 있습니다. 임베드된 적응형 양식은 완전한 기능을 갖추고 있으며 사용자는 페이지를 떠나지 않고 양식을 작성하고 제출할 수 있습니다. 이로써 사용자는 웹 페이지의 다른 요소 컨텍스트에 남아 있는 동시에 양식과 상호 작용할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

먼저 다음 단계를 수행한 다음 외부 웹 사이트에 적응형 양식을 임베드합니다.

* Publish은 AEM Forms 서버의 Publish 인스턴스에 임베드할 적응형 양식입니다.
* 웹 사이트에서 적응형 양식을 호스팅할 수 있는 웹 페이지를 만들거나 식별합니다. 웹 페이지에서 CDN의 [jQuery 파일을 읽을 수 있는지](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) 또는 jQuery의 로컬 복사본이 포함되어 있는지 확인하십시오. 적응형 양식을 렌더링하는 데 jQuery가 필요합니다.
* AEM 서버와 웹 페이지가 다른 도메인에 있는 경우 섹션에 나열된 단계를 수행합니다. [AEM Forms에서 도메인 간 사이트에 적응형 양식을 제공하도록 설정](#cross-site).

## 임베드된 적응형 양식 {#embed-adaptive-form}

웹 페이지에서 몇 줄의 JavaScript를 삽입하여 적응형 양식을 임베드할 수 있습니다. 코드의 API는 적응형 양식 리소스에 대한 HTTP 요청을 AEM 서버에 보내고 지정된 양식 컨테이너에 적응형 양식을 주입합니다.

적응형 양식을 임베드하려면

1. 다음 코드를 사용하여 웹 사이트에서 웹 페이지를 만듭니다.

   ```html
   <!doctype html>
   <html>
     <head>
       <title>This is the title of the webpage!</title>
       <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
     </head>
     <body>
     <div class="customafsection"/>
       <p>This section is replaced with the adaptive form.</p>
   
    <script>
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
       if(options.path) {
           // options.path refers to the path of the adaptive form
           // For Example: /content/forms/af/ABC, where ABC is the adaptive form
           // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path
           var path = options.path;
           path += "/jcr:content/guideContainer.html";
           $.ajax({
               url  : path ,
               type : "GET",
               data : {
                   // Set the wcmmode to be disabled
                   wcmmode : "disabled"
                   // Set the data reference, if any
                  // "dataRef": options.dataRef
                   // Specify a different theme for the form object
                 //  "themeOverride" : options.themepath
               },
               async: false,
               success: function (data) {
                   // If jquery is loaded, set the inner html of the container
                   // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                   // For example: document.getElementById().innerHTML
                   if(window.$ && options.CSS_Selector){
                       // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
                       $(options.CSS_Selector).html(data);
                   }
               },
               error: function (data) {
                   // any error handler
               }
           });
       } else {
           if (typeof(console) !== "undefined") {
               console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
           }
       }
    }(options);
   
    </script>
     </body>
   </html>
   ```

1. 임베드된 코드에서

   * *options.path* 변수의 값을 적응형 양식의 게시 URL 경로로 변경합니다. AEM 서버가 컨텍스트 경로에서 실행 중인 경우, URL에 컨텍스트 경로가 포함되어 있는지 확인합니다. 확장을 포함한 적응형 양식의 전체 이름을 항상 언급하십시오. 예를 들어 위의 코드와 적응형 양식은 동일한 AEM Forms 서버에 있으므로 이 예제에서는 적응형 양식 `/content/forms/af/locbasic.html`의 컨텍스트 경로를 사용합니다.
   * *options.dataRef*&#x200B;을(를) URL로 전달할 특성으로 바꾸십시오. dataref 변수를 사용하여 [적응형 양식을 미리 채우기](/help/forms/prepopulate-adaptive-form-fields.md)할 수 있습니다.
   * *options.themePath*&#x200B;을(를) 적응형 양식에서 구성한 테마가 아닌 다른 테마에 대한 경로로 바꾸십시오. 또는 요청 속성을 사용하여 테마 경로를 지정할 수 있습니다.
   * CSS 선택기는 적응형 양식이 임베드된 양식 컨테이너의 CSS 선택기입니다. 예: 위 예에서 .customafsection css 클래스는 CSS 선택기입니다.

적응형 양식은 웹 페이지에 임베드되어 있습니다. 임베드된 적응형 양식에서 다음 규칙을 준수합니다.

* 원래 적응형 양식의 머리글 및 바닥글은 임베드된 양식에 포함되지 않습니다.
* 초안과 제출된 양식은 양식 포털의 초안 및 제출 탭에서 확인할 수 있습니다.
* 원래 적응형 양식에 구성된 제출 액션은 임베드된 양식에 유지됩니다.
* 적응형 양식 규칙은 임베드된 양식에 유지되고 완전한 기능을 갖추고 있습니다.
* 원래 적응형 양식에 구성된 경험 타깃팅 및 A/B 테스트는 임베드된 양식에서 작동하지 않습니다.
* Adobe Analytics이 원래 양식에 구성된 경우, 분석 데이터가 Adobe Analytics 서버에 의해 캡처됩니다. 단, 양식 분석 보고서에서 사용할 수 없습니다.

## 샘플 토폴로지 {#sample-topology}

적응형 양식을 임베드하는 외부 웹 페이지에서는 일반적으로 비공개 네트워크 방화벽 뒤에 있는 AEM 서버로 요청을 보냅니다. 요청이 AEM 서버로 안전하게 이동되도록 하려면 역방향 프록시 서버를 설정하는 것이 좋습니다.

Dispatcher 없이 Apache 2.4 역방향 프록시 서버를 설정하는 방법의 예를 살펴보겠습니다. 이 예에서는 역방향 프록시에 대해 `/forms` 컨텍스트 경로와 맵 `/forms`을(를) 사용하여 AEM 서버를 호스팅합니다. Apache 서버의 `/forms`에 대한 모든 요청이 AEM 인스턴스로 이동되도록 합니다. 이 토폴로지를 사용하면 모든 요청에 AEM 서버로 가는 `/forms` 경로가 접두사로 추가되므로 Dispatcher 계층의 규칙 수를 줄이는 데 도움이 됩니다.

1. `httpd.conf`구성 파일을 열고 다음 코드 라인의 주석 해제합니다. 또는 파일에서 이 코드 라인을 추가할 수 있습니다.

   ```text
   LoadModule proxy_html_module modules/mod_proxy_html.so
   LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. `httpd-proxy.conf` 구성 파일의 다음 코드 라인을 추가하여 프록시 규칙을 설정합니다.

   ```text
   ProxyPass /forms https://[AEM_Instance]/forms
   ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   규칙에서 `[AEM_Instance]`를 AEM 서버 게시 URL로 바꿉니다.

컨텍스트 경로에 AEM 서버를 마운트하지 않는 경우 Apache 계층의 프록시 규칙은 다음과 같습니다.

```text
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json

ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>다른 토폴로지를 설정하는 경우 제출, 미리 채우기 및 기타 URL을 Dispatcher 레이어의 허용 목록에 추가하다에 추가해야 합니다.

## 모범 사례 {#best-practices}

웹 페이지의 적응형 양식을 임베드할 때 다음 모범 사례를 고려하십시오.

* 웹 페이지 CSS에 정의된 스타일 규칙이 양식 오브젝트 CSS와 충돌하지 않는지 확인합니다. 충돌을 방지하기 위해 AEM 클라이언트 라이브러리를 사용하여 적응형 양식 테마의 웹 페이지 CSS를 재사용할 수 있습니다. 적응형 양식 테마에서 클라이언트 라이브러리를 사용하는 방법에 대한 자세한 내용은 [AEM Forms의 테마](/help/forms/themes.md)를 참조하십시오.
* 웹 페이지의 양식 컨테이너에서 전체 창 너비를 사용할 수 있습니다. 모바일 디바이스용으로 구성된 CSS 규칙이 변경 사항 없이 작동하고 있는지 확인합니다. 양식 컨테이너가 전체 창 너비를 차지하지 않는 경우 양식이 다른 모바일 장치에 맞게 조정되도록 사용자 지정 CSS를 작성해야 합니다.
* `[getData](https://helpx.adobe.com/kr/experience-manager/6-5/forms/javascript-api/GuideBridge.html)` API를 사용하여 클라이언트에서 양식 데이터의 XML 또는 JSON 표현식을 가져옵니다.
* `[unloadAdaptiveForm](https://helpx.adobe.com/kr/experience-manager/6-5/forms/javascript-api/GuideBridge.html)` API를 사용하여 HTML DOM에서 적응형 양식을 언로드합니다.
* AEM 서버에서 응답을 보낼 때 access-control-origin 헤더를 설정합니다.

## AEM Forms에서 도메인 간 사이트에 적응형 양식을 제공할 수 있도록 활성화 {#cross-site}

1. AEM 게시 인스턴스에서 `https://'[server]:[port]'/system/console/configMgr`의 AEM 웹 콘솔 구성 관리자로 이동합니다.
1. **Apache Sling 레퍼러 필터** 구성을 찾아 엽니다.
1. 허용된 호스트 필드에서 웹 페이지가 있는 도메인을 지정합니다. 이를 통해 호스트는 AEM 서버에 POST를 요청할 수 있습니다. 정규 표현식을 사용하여 일련의 외부 애플리케이션 도메인을 지정할 수도 있습니다.

>[!MORELIKETHIS]
>
>* [외부 웹 페이지에 핵심 구성 요소를 기반으로 하는 적응형 양식 포함](/help/forms/embed-adaptive-form-core-components-external-web-page.md)
