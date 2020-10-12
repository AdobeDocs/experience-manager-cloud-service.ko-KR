---
title: AEM에서 Cloud Service으로 클라이언트측 라이브러리 사용
description: AEM은 클라이언트측 라이브러리 폴더를 제공합니다. 이 폴더를 통해 저장소에 클라이언트측 코드(clientlibs)를 저장하고, 카테고리로 구성하고, 각 코드 카테고리가 클라이언트에게 제공되는 시기와 방법을 정의할 수 있습니다
translation-type: tm+mt
source-git-commit: d4c031e17c0c83e44b687474502252c89ed37922
workflow-type: tm+mt
source-wordcount: '2571'
ht-degree: 1%

---


# AEM에서 Cloud Service으로 클라이언트측 라이브러리 사용 {#using-client-side-libraries}

디지털 경험은 복잡한 JavaScript 및 CSS 코드를 기반으로 하는 클라이언트 측 처리에 크게 의존합니다. AEM Client-Side Libraries(clientlibs)를 사용하면 이러한 클라이언트측 라이브러리를 저장소 내에 구성하고 중앙에서 저장할 수 있습니다. AEM 프로젝트 원형의 [프런트 엔드 구축 프로세스와 결합하여](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/uifrontend.html) AEM 프로젝트의 프런트 엔드 코드를 관리하는 것은 간단해집니다.

AEM에서 clientlibs를 사용하는 경우의 이점은 다음과 같습니다.

* 클라이언트측 코드는 다른 모든 애플리케이션 코드와 같은 저장소에 저장됩니다
* AEM의 Clientlibs는 모든 CSS 및 JS를 하나의 파일로 취합할 수 있습니다
* 디스패처를 통해 액세스할 수 있는 경로를 통해 clientlibs [노출](/help/implementing/dispatcher/disp-overview.md)
* 참조된 파일 또는 이미지에 대한 경로 재작성 허용

Clientlibs는 AEM에서 CSS 및 Javascript를 전달하기 위한 내장된 솔루션입니다.

>[!TIP]
>
>AEM 프로젝트용 CSS 및 Javascript를 제작하는 프런트 엔드 개발자는 [AEM Project Pretype 및 자동화된 프런트 엔드 빌드 프로세스에 익숙해져야 합니다.](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/uifrontend.html)

## 클라이언트측 라이브러리란? {#what-are-clientlibs}

사이트에는 JavaScript와 CSS뿐만 아니라 아이콘 및 웹 글꼴과 같은 정적 리소스를 클라이언트측에서 처리해야 합니다. clientlib은 필요한 경우 범주별로 참조하고 이러한 리소스를 제공하는 AEM 메커니즘입니다.

AEM은 사이트의 CSS 및 Javascript를 중앙 위치의 단일 파일로 수집하여 모든 리소스의 한 복사본만 HTML 출력에 포함되도록 합니다. 이렇게 하면 전달 효율성이 극대화되고 이러한 리소스를 프록시를 통해 저장소에 중앙에서 유지 관리할 수 있으므로 액세스를 안전하게 유지할 수 있습니다.

## Cloud Service으로 AEM용 프런트 엔드 개발 {#fed-for-aemaacs}

모든 JavaScript, CSS 및 기타 프런트 엔드 에셋은 AEM Project Tranype의 [ui.frontend 모듈에서 유지 관리되어야 합니다.](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/uifrontend.html) 원형의 유연성은 이러한 리소스를 제작하고 관리할 수 있는 최신 웹 툴을 제공합니다.

그런 다음 원형을 통해 리소스를 단일 CSS 및 JS 파일에 컴파일하여 저장소의 리소스 `cq:clientLibraryFolder` 에 자동으로 포함시킬 수 있습니다.

## 클라이언트측 라이브러리 폴더 구조 {#clientlib-folders}

클라이언트측 라이브러리 폴더는 유형의 저장소 노드입니다 `cq:ClientLibraryFolder`. CND 표기법의 [정의](https://jackrabbit.apache.org/node-type-notation.html) :

```text
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

* `cq:ClientLibraryFolder` 노드는 저장소의 하위 트리 내의 어느 곳에나 배치할 수 `/apps` 있습니다.
* 노드의 `categories` 속성을 사용하여 해당 노드가 속하는 라이브러리 범주를 식별합니다.

각 `cq:ClientLibraryFolder` 은 몇 개의 지원 파일과 함께 JS 및/또는 CSS 파일 세트로 채워집니다(아래 참조). 의 중요한 속성은 다음과 같이 `cq:ClientLibraryFolder` 구성됩니다.

* `allowProxy`:모든 clientlibs는 아래에 저장되어야 하므로 이 등록 정보는 clientlibraries `apps`프록시 서블릿에 액세스할 수 있습니다. 클라이언트 [라이브러리 폴더 찾기 및 아래의 프록시 클라이언트 라이브러리 서블릿 사용을](#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) 참조하십시오.
* `categories`:이 안에 있는 JS 및/또는 CSS 파일 세트가 속하는 카테고리를 `cq:ClientLibraryFolder` 식별합니다. 다중 값을 갖는 `categories` 속성은 라이브러리 폴더를 두 개 이상의 카테고리에 포함할 수 있도록 합니다(유용할 수 있는 방법은 아래 참조).

클라이언트 라이브러리 폴더에 런타임에 단일 JS 및/또는 CSS 파일로 병합되는 소스 파일이 하나 이상 포함되어 있는 경우 생성된 파일의 이름은 확장명이 `.js` 또는 파일 이름인 노드 `.css` 이름입니다. 예를 들어, 라이브러리 노드 이름 `cq.jquery` 은 생성된 파일 이름 `cq.jquery.js` 또는 `cq.jquery.css`결과

클라이언트 라이브러리 폴더에는 다음 항목이 포함됩니다.

* JS 및/또는 CSS 소스 파일
* 아이콘, 웹 글꼴 등 CSS 스타일을 지원하는 정적 리소스
* 생성된 JS 및/또는 CSS 파일에 병합할 소스 파일을 식별하는 파일 및/또는 하나의 `js.txt` `css.txt` 파일

![Clientlib 아키텍처](assets/clientlib-architecture.drawio.png)

## 클라이언트측 라이브러리 폴더 만들기 {#creating-clientlib-folders}

클라이언트 라이브러리는 아래에 있어야 합니다 `/apps`. 이 방법은 코드를 컨텐츠 및 구성에서 보다 잘 격리하기 위한 것입니다.

클라이언트 라이브러리에 액세스할 수 있도록 `/apps` 프록시 서버가 사용됩니다. ACL은 클라이언트 라이브러리 폴더에 계속 적용되지만 서블릿은 속성이 로 설정된 `/etc.clientlibs/` 경우 컨텐츠를 읽을 수 있도록 `allowProxy` 허용합니다 `true`.

1. Open CRXDE Lite in a web browser (`https://<host>:<port>/crx/de`).
1. 폴더를 `/apps` 선택하고 **만들기 > 노드 만들기를 클릭합니다**.
1. 라이브러리 폴더 이름을 입력하고 **유형** 목록에서 선택합니다 `cq:ClientLibraryFolder`. 확인 **을** 클릭한 다음 **모두 저장을 클릭합니다**.
1. 라이브러리가 속한 카테고리 또는 범주를 지정하려면 노드를 선택하고 다음 속성을 추가한 `cq:ClientLibraryFolder` 다음 [모두 **저장]을 클릭합니다**.
   * 이름: `categories`
   * 유형:문자열
   * 값:범주 이름
   * 다중:선택됨
1. 아래에서 프록시를 통해 클라이언트 라이브러리에 액세스할 수 있도록 하려면 `/etc.clientlibs`노드를 선택하고 다음 속성을 추가한 다음 [모두 `cq:ClientLibraryFolder` 저장]을 클릭합니다 ****.
   * 이름: `allowProxy`
   * Type: Boolean
   * 값: `true`
1. 정적 리소스를 관리해야 하는 경우 클라이언트 라이브러리 폴더 `resources` 아래에 명명된 하위 폴더를 만듭니다.
   * 폴더 아래에 정적 리소스를 저장하는 경우 `resources`게시 인스턴스에서 참조할 수 없습니다.
1. 라이브러리 폴더에 소스 파일을 추가합니다.
   * 이는 일반적으로 [AEM Project Tranype의 프런트 엔드 빌드 프로세스를 통해 수행됩니다.](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/uifrontend.html)
   * 원하는 경우 하위 폴더에서 소스 파일을 구성할 수 있습니다.
1. 클라이언트 라이브러리 폴더를 선택하고 **만들기 > 파일 만들기를 클릭합니다**.
1. 파일 이름 상자에 다음 파일 이름 중 하나를 입력하고 확인을 클릭합니다.
   * **`js.txt`:** 이 파일 이름을 사용하여 JavaScript 파일을 생성합니다.
   * **`css.txt`:** 이 파일 이름을 사용하여 계단식 스타일 시트를 생성합니다.
1. 파일을 열고 다음 텍스트를 입력하여 소스 파일 경로의 루트를 확인합니다.
   * `#base=*[root]*`
   * 소스 파일 `[root]` 이 들어 있는 폴더의 경로로 TXT 파일을 기준으로 대체합니다. 예를 들어 소스 파일이 TXT 파일과 동일한 폴더에 있는 경우 다음 텍스트를 사용합니다.
      * `#base=.`
   * 다음 코드는 루트를 노드 아래에 mobile이라는 폴더로 `cq:ClientLibraryFolder` 설정합니다.
      * `#base=mobile`
1. 아래 줄에 루트 `#base=[root]`를 기준으로 소스 파일의 경로를 입력합니다. 각 파일 이름을 별도의 줄에 배치합니다.
1. 모두 **저장을 클릭합니다**.

## 클라이언트측 라이브러리 제공 {#serving-clientlibs}

클라이언트 라이브러리 폴더가 [필요에 따라 구성되면](#creating-clientlib-folders) 프록시를 통해 clientlibs를 요청할 수 있습니다. 예:

* clientlib이 `/apps/myproject/clientlibs/foo`
* 정적 이미지가 `/apps/myprojects/clientlibs/foo/resources/icon.png`

이 `allowProxy` 속성을 사용하여 다음을 요청할 수 있습니다.

* j를 통한 clientlib`/etc.clientlibs/myprojects/clientlibs/foo.js`
* 정적 이미지는 `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

### HTL을 통해 클라이언트 라이브러리 로드 {#loading-via-htl}

클라이언트 라이브러리 폴더에 저장되고 관리되면 HTL을 통해 액세스할 수 있습니다.

클라이언트 라이브러리는 AEM에서 제공하는 도우미 템플릿을 통해 로드되며, 이 템플릿은 이를 통해 액세스할 수 있습니다 `data-sly-use`. 헬퍼 템플릿은 이 파일에서 사용할 수 있으며, 이를 통해 호출할 수 있습니다 `data-sly-call`.

각 헬퍼 템플릿에는 원하는 클라이언트 라이브러리를 참조하는 `categories` 옵션이 필요합니다. 이 옵션은 문자열 값의 배열 또는 쉼표로 구분된 값 목록을 포함하는 문자열일 수 있습니다.

[HTL을 통해 clientlibs를 로드하는 방법에 대한 자세한 내용은 HTL 설명서를](https://docs.adobe.com/content/help/en/experience-manager-htl/using/getting-started/getting-started.html#loading-client-libraries) 참조하십시오.

<!--
### Setting Cache Timestamps {#setting-cache-timestamps}

This is possible. Still need detail.
-->

## 작성자와 게시 시의 클라이언트 라이브러리 {#clientlibs-author-publish}

AEM 게시 인스턴스에 대부분의 clientlibs가 필요합니다. 즉, 대부분의 clientlibs는 컨텐츠에 대한 최종 사용자 경험을 제작하는 것입니다. 게시 인스턴스의 clientlibs의 경우 위에 설명된 대로 [프런트 엔드 빌드 도구를](#fed-for-aemaacs) 사용하고 [클라이언트 라이브러리 폴더를 통해 배포할 수 있습니다.](#creating-clientlib-folders)

그러나 클라이언트 라이브러리가 작성 환경을 사용자 정의하는 데 필요할 수 있는 경우가 있습니다. 예를 들어 대화 상자를 사용자 정의하려면 AEM 제작 인스턴스에 작은 CSS 또는 JS를 배포해야 할 수 있습니다.

### 작성자의 클라이언트 라이브러리 관리 {#clientlibs-on-author}

작성자에서 클라이언트 라이브러리를 사용해야 하는 경우 게시와 동일한 방법으로 클라이언트 라이브러리를 `/apps` 만들 수 있지만 전체 프로젝트를 관리하는 대신 바로 아래에 `/apps/.../clientlibs/foo` 클라이언트 라이브러리를 작성할 수 있습니다.

그런 다음 기본 클라이언트 라이브러리 범주에 클라이언트 라이브러리를 추가하여 제작 JS에 &quot;연결&quot;할 수 있습니다.

## 디버깅 도구 {#debugging-tools}

AEM은 클라이언트 라이브러리 폴더를 디버깅하고 테스트하는 몇 가지 도구를 제공합니다.

### 클라이언트 라이브러리 검색 {#discover-client-libraries}

구성 요소는 시스템의 모든 클라이언트 라이브러리 폴더에 대한 정보 페이지를 생성합니다 `/libs/cq/granite/components/dumplibs/dumplibs` . 노드에는 `/libs/granite/ui/content/dumplibs` 리소스 유형으로 구성 요소가 있습니다. 페이지를 열려면 다음 URL을 사용합니다(필요에 따라 호스트 및 포트 변경).

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

이 정보에는 라이브러리 경로 및 유형(CSS 또는 JS)과 범주 및 종속성 등의 라이브러리 속성 값이 포함됩니다. 페이지의 다음 표는 각 카테고리와 채널의 라이브러리를 보여줍니다.

### 생성된 출력 참조 {#see-generated-output}

구성 요소 `dumplibs` 에는 태그에 대해 생성된 소스 코드를 표시하는 테스트 선택기가 `ui:includeClientLib` 포함되어 있습니다. 이 페이지에는 js, css 및 테마 속성의 다양한 조합을 위한 코드가 포함되어 있습니다.

1. 다음 방법 중 하나를 사용하여 [테스트 출력] 페이지를 엽니다.
   * 페이지에서 출력 테스트 `dumplibs.html` 텍스트를 보려면 여기를 **클릭하십시오** .
   * 웹 브라우저에서 다음 URL을 엽니다(필요에 따라 다른 호스트 및 포트 사용).
      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`
   * 기본 페이지에는 categories 속성에 대한 값이 없는 태그에 대한 출력이 표시됩니다.
1. 카테고리에 대한 출력을 보려면 클라이언트 라이브러리 속성 값을 입력하고 쿼리 제출 `categories` 을 클릭합니다 ****.

## 추가 클라이언트 라이브러리 폴더 기능 {#additional-features}

AEM의 클라이언트 라이브러리 폴더에서 지원하는 기타 많은 기능이 있습니다. 그러나 AEM에서는 Cloud Service으로 사용할 필요가 없고 그러한 사용은 좌절됩니다. 그들은 완전성을 위해 여기에 열거되어 있다.

>[!WARNING]
>
>이러한 클라이언트 라이브러리 폴더의 추가 기능은 Cloud Service으로 AEM에서 필요하지 않으며 이러한 기능은 사용하지 않습니다. 그들은 완전성을 위해 여기에 열거되어 있다.

### Adobe Granite HTML 라이브러리 관리자 {#html-library-manager}

추가 클라이언트 라이브러리 설정은 시스템 콘솔()의 [ **Adobe [HTML 라이브러리 관리자** ] 패널을 통해 제어할 수 `https://<host>:<port>/system/console/configMgr`있습니다.

### 추가 폴더 속성 {#additional-folder-properties}

추가 폴더 속성에는 종속성 및 포함 제어 기능이 포함되지만, 일반적으로 더 이상 필요하지 않으며 사용이 권장되지 않습니다.

* `dependencies`:이 라이브러리 폴더가 종속된 다른 클라이언트 라이브러리 카테고리 목록입니다. 예를 들어, 주어진 두 개의 `cq:ClientLibraryFolder` 노드 `F` 와 주어진 파일이 제대로 기능하기 위해 다른 파일이 필요한 경우, 그 `G`에 있는 파일 중 적어도 하나 `F` 가 `G` Coverity의 `categories` 한 개 이상 `G` `dependencies` `F`에 있어야 합니다.
* `embed`:다른 라이브러리의 코드를 임베드하는 데 사용됩니다. 노드 `F` 가 노드 `G` 를 포함하고 `H`있는 경우, 결과 HTML은 노드 `G` 및 `H`컨텐츠의 연결입니다.

### 종속성 연결 {#linking-to-dependencies}

클라이언트 라이브러리 폴더의 코드가 다른 라이브러리를 참조하면 다른 라이브러리를 종속성으로 식별합니다. 클라이언트 라이브러리 폴더를 참조하는 `ui:includeClientLib` 태그로 인해 HTML 코드에 생성된 라이브러리 파일에 대한 링크 및 종속성이 포함됩니다.

종속성은 다른 것이어야 합니다 `cq:ClientLibraryFolder`. 종속성을 식별하려면 다음 속성을 사용하여 `cq:ClientLibraryFolder` 노드에 속성을 추가하십시오.

* **이름:** 종속성
* **유형:** 문자열[]
* **값:** 현재 라이브러리 폴더가 종속된 cq:ClientLibraryFolder 노드의 categories 속성 값.

예를 들어, 라이브러리 `/etc/clientlibs/myclientlibs/publicmain` 에 대한 종속성이 `cq.jquery` 있습니다. 기본 클라이언트 라이브러리를 참조하는 페이지는 다음 코드를 포함하는 HTML을 생성합니다.

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### 다른 라이브러리의 코드 포함 {#embedding-code-from-other-libraries}

클라이언트 라이브러리의 코드를 다른 클라이언트 라이브러리에 포함할 수 있습니다. 런타임 시 임베드 라이브러리의 생성된 JS 및 CSS 파일에는 임베드 라이브러리의 코드가 포함되어 있습니다.

포함 코드는 저장소의 보안 영역에 저장된 라이브러리에 대한 액세스를 제공하는 데 유용합니다.

#### 앱별 클라이언트 라이브러리 폴더 {#app-specific-client-library-folders}

응용 프로그램 관련 파일을 아래 응용 프로그램 폴더에 보관하는 것이 좋습니다 `/app`. 또한 웹 사이트 방문자가 `/app` 폴더에 액세스할 수 없도록 하는 것이 좋습니다. 두 가지 모범 사례를 모두 충족하려면 아래에 있는 클라이언트 라이브러리를 포함하는 `/etc` 폴더 아래에 클라이언트 라이브러리 폴더를 만드십시오 `/app`.

categories 속성을 사용하여 포함할 클라이언트 라이브러리 폴더를 식별합니다. 라이브러리를 포함하려면 다음 속성 속성을 사용하여 포함 `cq:ClientLibraryFolder` 노드에 속성을 추가합니다.

* **이름:** 포함
* **유형:** 문자열[]
* **값:** 포함할 노드의 categories 속성 값 `cq:ClientLibraryFolder` 입니다.

#### 포함 기능을 사용하여 요청 최소화 {#using-embedding-to-minimize-requests}

일부 경우에는 게시 인스턴스별로 일반적인 페이지에 대해 생성된 최종 HTML에 비교적 많은 `<script>` 요소가 포함되어 있는 것을 확인할 수 있습니다.

이러한 경우 필요한 모든 클라이언트 라이브러리 코드를 하나의 파일로 결합하여 페이지 로드 시 요청이 오고 나가는 횟수를 줄이는 것이 유용할 수 있습니다. 이렇게 하려면 노드의 embed 속성 `embed` 을 사용하여 필요한 라이브러리를 앱별 클라이언트 라이브러리에 포함할 수 `cq:ClientLibraryFolder` 있습니다.

#### CSS 파일의 경로 {#paths-in-css-files}

CSS 파일을 포함할 때 생성된 CSS 코드는 포함 라이브러리에 상대적인 리소스에 대한 경로를 사용합니다. 예를 들어 공개적으로 액세스할 수 있는 라이브러리에는 클라이언트 라이브러리 `/etc/client/libraries/myclientlibs/publicmain` 가 `/apps/myapp/clientlib` 포함됩니다.

파일에 `main.css` 다음 스타일이 포함되어 있습니다.

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

노드가 생성하는 CSS 파일은 원래 이미지의 URL을 사용하여 다음 스타일을 `publicmain` 포함합니다.

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

#### HTML 출력에 포함된 파일 참조 {#see-embedded-files}

포함된 코드의 원본을 추적하거나 포함된 클라이언트 라이브러리가 예상 결과를 생성하는지 확인하기 위해 런타임 시 포함 중인 파일의 이름을 볼 수 있습니다. 파일 이름을 보려면 웹 페이지의 URL에 매개 `debugClientLibs=true` 변수를 추가합니다. 생성된 라이브러리에는 포함된 코드 대신 `@import` 문이 포함되어 있습니다.

이전 [다른 라이브러리의 코드 포함](#embedding-code-from-other-libraries) 섹션의 예에서 `/etc/client/libraries/myclientlibs/publicmain` 클라이언트 라이브러리 폴더에 `/apps/myapp/clientlib` 클라이언트 라이브러리 폴더가 포함됩니다. 웹 페이지에 매개 변수를 추가하면 웹 페이지의 소스 코드에 다음 링크가 만들어집니다.

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

파일을 열면 다음 코드가 `publicmain.css` 표시됩니다.

```javascript
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. 웹 브라우저의 주소 상자에서 HTML의 URL에 다음 텍스트를 추가합니다.
   * `?debugClientLibs=true`
1. 페이지가 로드되면 페이지 소스를 봅니다.
1. 파일을 열고 소스 코드를 보기 위해 링크 요소의 href로 제공되는 링크를 클릭합니다.

### 프리프로세서 사용 {#using-preprocessors}

AEM에서는 플러그형 프리프로세서를 지원하고 YUI가 AEM 기본 프리프로세서로 설정된 JavaScript용 [YUI Compressor](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) 및 [Google Closure Compiler(GCC)](https://developers.google.com/closure/compiler/) 지원을 제공합니다.

플러그형 프리프로세서를 통해 다음을 비롯한 유연한 사용 가능

* 스크립트 소스를 처리할 수 있는 스크립트 프로세서 정의
* 프로세서는 옵션을 사용하여 구성할 수 있습니다.
* 프로세서는 소정에 사용할 수 있지만, 축소 가능한 경우도 사용할 수 있습니다
* clientlib은 사용할 프로세서를 정의할 수 있습니다.

>[!NOTE]
>
>기본적으로 AEM은 YUI 압축기를 사용합니다. 알려진 문제 목록은 [YUI Compressor GitHub 설명서를](https://github.com/yui/yuicompressor/issues) 참조하십시오. 특정 클라이언트용 GCC 압축기로 전환하면 YUI를 사용할 때 발생하는 몇 가지 문제를 해결할 수 있습니다.

>[!CAUTION]
>
>클라이언트 라이브러리에 축소 라이브러리를 배치하지 마십시오. 대신 원시 라이브러리를 제공하고, 인증이 필요한 경우 프리프로세서의 옵션을 사용하십시오.

#### 사용량 {#usage}

클라이언트 라이브러리 또는 시스템 전체에 대해 프리프로세서 구성을 구성할 수 있습니다.

* Add the multivalue properties `cssProcessor` and `jsProcessor` on the clientlibrary node
* 또는 **HTML Library Manager** OSGi 구성을 통해 시스템 기본 구성 정의

clientlib 노드의 프리프로세서 구성이 OSGI 구성에 우선합니다.

#### 형식 및 예 {#format-and-examples}

##### 형식 {#format}

```javascript
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

##### CSS용 YUI 압축기 및 JS용 GCC {#yui-compressor-for-css-minification-and-gcc-for-js}

```javascript
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

##### Typescript를 Preprocess로 변환한 다음 GCC에서 Minify 및 Obfuskate로 변환 {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate}

```javascript
jsProcessor: [
   "default:typescript",
   "min:typescript",
   "min:gcc;obfuscate=true"
]
```

##### 추가 GCC 옵션 {#additional-gcc-options}

```javascript
failOnWarning (defaults to "false")
languageIn (defaults to "ECMASCRIPT5")
languageOut (defaults to "ECMASCRIPT5")
compilationLevel (defaults to "simple") (can be "whitespace", "simple", "advanced")
```

GCC 옵션에 대한 자세한 내용은 [GCC 설명서를 참조하십시오](https://developers.google.com/closure/compiler/docs/compilation_levels).

#### 시스템 기본 미니표시자 설정 {#set-system-default-minifier}

AEM에서 YUI가 기본 미니피자로 설정됩니다. GCC로 변경하려면 다음 단계를 따르십시오.

1. (`http://<host>:<portY/system/console/configMgr`)의 Apache Felix Config Manager로 이동
1. [ **Adobe [화강암 HTML 라이브러리 관리자]를 찾아 편집합니다**.
1. 축소 **옵션을** 활성화합니다(아직 활성화되지 않은 경우).
1. 값 **JS 프로세서 기본 구성을** 로 `min:gcc`설정합니다.
   * 세미콜론(예:)으로 구분하면 옵션을 전달할 수 있습니다. `min:gcc;obfuscate=true`.
1. Click **Save** to save the changes.
