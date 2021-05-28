---
title: AEM에서 클라이언트측 라이브러리를 Cloud Service으로 사용
description: AEM에서는 클라이언트 측 코드(clientlibs)를 저장소에 저장하고, 카테고리로 구성하고, 각 코드 카테고리를 클라이언트에 제공할 시기와 방법을 정의할 수 있는 클라이언트측 라이브러리 폴더를 제공합니다
exl-id: 370db625-09bf-43fb-919d-4699edaac7c8
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '2561'
ht-degree: 0%

---

# AEM에서 클라이언트측 라이브러리를 Cloud Service {#using-client-side-libraries}(으)로 사용

디지털 경험은 복잡한 JavaScript 및 CSS 코드로 구동되는 클라이언트측 처리에 주로 의존합니다. AEM 클라이언트측 라이브러리(clientlibs)를 사용하면 이러한 클라이언트측 라이브러리를 리포지토리 내에 구성하고 중앙에서 저장할 수 있습니다. AEM Project Archetype에서 [프런트 엔드 빌드 프로세스와 결합되면 AEM 프로젝트에 대한 프런트 엔드 코드를 관리하는 작업이 간단해집니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html)

AEM에서 clientlibs를 사용할 때의 장점은 다음과 같습니다.

* 클라이언트측 코드는 다른 모든 애플리케이션 코드 및 컨텐츠와 마찬가지로 저장소에 저장됩니다
* AEM의 Clientlibs는 모든 CSS 및 JS를 하나의 파일에 집계할 수 있습니다
* [dispatcher](/help/implementing/dispatcher/disp-overview.md)를 통해 액세스할 수 있는 경로를 통해 clientlibs를 노출합니다.
* 참조된 파일 또는 이미지에 대한 경로를 재작성할 수 있습니다

Clientlibs 는 AEM에서 CSS 및 Javascript를 전달하기 위한 내장된 솔루션입니다.

>[!TIP]
>
>AEM 프로젝트용 CSS 및 Javascript를 만드는 프런트 엔드 개발자도 [AEM Project Archetype 및 자동화된 프런트 엔드 빌드 프로세스에 익숙해져야 합니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html)

## 클라이언트측 라이브러리란 무엇입니까? {#what-are-clientlibs}

사이트에서는 클라이언트측에서 처리할 정적 리소스와 JavaScript 및 CSS가 필요합니다. clientlib은 필요한 경우 카테고리별로 을(를) 참조하고 이러한 리소스를 제공하는 AEM 메커니즘입니다.

AEM에서는 사이트의 CSS 및 Javascript를 중앙 위치의 단일 파일로 수집하여 리소스의 한 복사본만 HTML 출력에 포함되도록 합니다. 이렇게 하면 전달 효율성이 극대화되고 이러한 리소스를 프록시를 통해 저장소에서 중앙 집중식으로 유지 관리할 수 있으므로 액세스를 안전하게 유지할 수 있습니다.

## AEM as a Cloud Service용 프런트엔드 개발 {#fed-for-aemaacs}

모든 JavaScript, CSS 및 기타 프런트 엔드 자산은 AEM Project Archetype의 [ui.frontend 모듈에서 유지 관리해야 합니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html) 원형 형의 유연성을 통해 원하는 최신 웹 도구를 사용하여 이러한 리소스를 만들고 관리할 수 있습니다.

그런 다음 원형 은 리소스를 단일 CSS 및 JS 파일로 컴파일하여 저장소의 `cq:clientLibraryFolder`에 자동으로 포함할 수 있습니다.

## 클라이언트 측 라이브러리 폴더 구조 {#clientlib-folders}

클라이언트측 라이브러리 폴더는 `cq:ClientLibraryFolder` 유형의 저장소 노드입니다. [CND 표기법](https://jackrabbit.apache.org/node-type-notation.html)의 정의는 다음과 같습니다

```text
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

* `cq:ClientLibraryFolder` 노드는 저장소의 하위  `/apps` 트리 내의 어디에나 배치할 수 있습니다.
* 노드의 `categories` 속성을 사용하여 해당 노드가 속한 라이브러리 카테고리를 식별합니다.

각 `cq:ClientLibraryFolder` 은 몇 개의 지원 파일과 함께 JS 및/또는 CSS 파일 세트로 채워집니다(아래 참조). `cq:ClientLibraryFolder`의 중요한 속성은 다음과 같이 구성됩니다.

* `allowProxy`:모든 clientlibs는 아래에 저장해야 하므로 이  `apps`속성을 사용하면 프록시 서블릿을 통해 clientlibraries에 액세스할 수 있습니다. 아래의 [클라이언트 라이브러리 폴더 찾기 및 프록시 클라이언트 라이브러리 서블릿 사용](#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet)을 참조하십시오.
* `categories`:이  `cq:ClientLibraryFolder` 가을 내에 JS 및/또는 CSS 파일 세트가 될 카테고리를 식별합니다. 여러 값을 갖는 `categories` 속성을 사용하면 라이브러리 폴더가 두 개 이상의 카테고리에 포함될 수 있습니다(이 기능이 유용한 방법에 대해서는 아래 참조).

클라이언트 라이브러리 폴더에 런타임 시 단일 JS 및/또는 CSS 파일에 병합되는 하나 이상의 소스 파일이 포함된 경우 생성된 파일의 이름은 `.js` 또는 `.css` 파일 이름 확장명을 사용하는 노드 이름입니다. 예를 들어, `cq.jquery` 라이브러리 노드는 `cq.jquery.js` 또는 `cq.jquery.css` 라는 생성된 파일을 생성합니다.

클라이언트 라이브러리 폴더에는 다음 항목이 포함됩니다.

* JS 및/또는 CSS 소스 파일
* 아이콘, 웹 글꼴 등 CSS 스타일을 지원하는 정적 리소스입니다.
* 생성된 JS 및/또는 CSS 파일에 병합할 소스 파일을 식별하는 하나의 `js.txt` 파일 및/또는 하나의 `css.txt` 파일

![Clientlib 아키텍처](assets/clientlib-architecture.drawio.png)

## 클라이언트측 라이브러리 폴더 만들기 {#creating-clientlib-folders}

클라이언트 라이브러리는 `/apps` 아래에 있어야 합니다. 따라서 코드와 컨텐츠를 더 잘 격리할 수 있습니다.

`/apps` 아래의 클라이언트 라이브러리에 액세스하려면 프록시 서버가 사용됩니다. ACL은 여전히 클라이언트 라이브러리 폴더에 적용되지만 `allowProxy` 속성이 `true`로 설정된 경우 서블릿은 `/etc.clientlibs/`을 통해 컨텐츠를 읽을 수 있도록 허용합니다.

1. 웹 브라우저에서 CRXDE Lite(`https://<host>:<port>/crx/de`)를 엽니다.
1. `/apps` 폴더를 선택하고 **만들기 > 노드 만들기**&#x200B;를 클릭합니다.
1. 라이브러리 폴더의 이름을 입력하고 **유형** 목록에서 `cq:ClientLibraryFolder`를 선택합니다. **확인**&#x200B;을 클릭한 다음 **모두 저장**&#x200B;을 클릭합니다.
1. 라이브러리가 속한 카테고리 또는 카테고리를 지정하려면 `cq:ClientLibraryFolder` 노드를 선택하고 다음 속성을 추가한 다음 **모두 저장**&#x200B;을 클릭합니다.
   * 이름: `categories`
   * 유형:문자열
   * 값:카테고리 이름
   * 다중:선택됨
1. `/etc.clientlibs` 아래의 프록시를 통해 클라이언트 라이브러리에 액세스하려면 `cq:ClientLibraryFolder` 노드를 선택하고 다음 속성을 추가한 다음 **모두 저장**&#x200B;을 클릭하십시오.
   * 이름: `allowProxy`
   * Type: Boolean
   * 값: `true`
1. 정적 리소스를 관리해야 하는 경우 클라이언트 라이브러리 폴더 아래에 `resources` 하위 폴더를 만듭니다.
   * 정적 리소스를 폴더 `resources` 아래에 저장하는 경우 게시 인스턴스에서 참조할 수 없습니다.
1. 라이브러리 폴더에 소스 파일을 추가합니다.
   * 이 작업은 일반적으로 [AEM Project Archetype.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html)의 프런트 엔드 빌드 프로세스에서 수행합니다.
   * 원하는 경우 하위 폴더에 소스 파일을 구성할 수 있습니다.
1. 클라이언트 라이브러리 폴더를 선택하고 **만들기 > 파일 만들기**&#x200B;를 클릭합니다.
1. 파일 이름 상자에 다음 파일 이름 중 하나를 입력하고 확인을 클릭합니다.
   * **`js.txt`:** 이 파일 이름을 사용하여 JavaScript 파일을 생성합니다.
   * **`css.txt`:** 이 파일 이름을 사용하여 계단식 스타일 시트를 생성합니다.
1. 파일을 열고 다음 텍스트를 입력하여 소스 파일 경로의 루트를 식별합니다.
   * `#base=*[root]*`
   * `[root]` 을 TXT 파일을 기준으로 소스 파일이 포함된 폴더의 경로로 바꿉니다. 예를 들어 소스 파일이 TXT 파일과 동일한 폴더에 있을 경우 다음 텍스트를 사용합니다.
      * `#base=.`
   * 다음 코드는 루트를 `cq:ClientLibraryFolder` 노드 아래에 mobile 라는 폴더로 설정합니다.
      * `#base=mobile`
1. `#base=[root]` 아래의 줄에 루트와 상대적인 소스 파일의 경로를 입력합니다. 각 파일 이름을 별도의 줄에 배치합니다.
1. **모두 저장**&#x200B;을 클릭합니다.

## 클라이언트 측 라이브러리 제공 {#serving-clientlibs}

클라이언트 라이브러리 폴더가 [필요에 따라 구성되면](#creating-clientlib-folders) 프록시를 통해 clientlibs를 요청할 수 있습니다. 예:

* `/apps/myproject/clientlibs/foo`에 clientlib이 있습니다.
* `/apps/myprojects/clientlibs/foo/resources/icon.png`에 정적 이미지가 있습니다.

`allowProxy` 속성을 사용하여 다음을 요청할 수 있습니다.

* j`/etc.clientlibs/myprojects/clientlibs/foo.js`을 통해 clientlib
* `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`을 통한 정적 이미지

### HTL {#loading-via-htl}을 통해 클라이언트 라이브러리 로드

clientlibs가 클라이언트 라이브러리 폴더에 저장되고 관리되면 HTL을 통해 액세스할 수 있습니다.

클라이언트 라이브러리는 `data-sly-use`을 통해 액세스할 수 있는 AEM에서 제공하는 도우미 템플릿을 통해 로드됩니다. 도우미 템플릿은 이 파일에서 사용할 수 있으며, 이 파일은 `data-sly-call`을 통해 호출할 수 있습니다.

각 도우미 템플릿에는 원하는 클라이언트 라이브러리를 참조하기 위한 `categories` 옵션이 필요합니다. 이 옵션은 문자열 값의 배열 또는 쉼표로 구분된 값 목록을 포함하는 문자열일 수 있습니다.

[HTL을 ](https://experienceleague.adobe.com/docs/experience-manager-htl/using/getting-started/getting-started.html#loading-client-libraries) 통한 clientlibs 로드에 대한 자세한 내용은 HTL 설명서 를 참조하십시오.

<!--
### Setting Cache Timestamps {#setting-cache-timestamps}

This is possible. Still need detail.
-->

## 작성자의 클라이언트 라이브러리 및 게시 {#clientlibs-author-publish}

대부분의 clientlibs는 AEM 게시 인스턴스에 필요합니다. 즉, 대부분의 clientlibs의 목적은 컨텐츠의 최종 사용자 경험을 생성하는 것입니다. 게시 인스턴스의 clientlibs의 경우, [프런트 엔드 빌드 도구](#fed-for-aemaacs)를 사용하고 위에서 설명한 대로 [클라이언트 라이브러리 폴더를 통해 배포할 수 있습니다.](#creating-clientlib-folders)

그러나 작성 환경을 사용자 지정하는 데 클라이언트 라이브러리가 필요한 경우가 있습니다. 예를 들어 대화 상자를 사용자 지정하려면 AEM 작성 인스턴스에 작은 CSS 또는 JS 비트를 배포해야 할 수 있습니다.

### 작성자 {#clientlibs-on-author}에서 클라이언트 라이브러리 관리

작성자에서 클라이언트 라이브러리를 사용해야 하는 경우 게시와 동일한 방법을 사용하여 `/apps` 아래에 클라이언트 라이브러리를 만들 수 있지만, 관리할 전체 프로젝트를 만드는 대신 `/apps/.../clientlibs/foo` 아래에 직접 작성합니다.

그런 다음 클라이언트 라이브러리를 기본 제공 클라이언트 라이브러리 카테고리에 추가하여 작성 JS에 &quot;후크&quot;할 수 있습니다.

## 디버깅 도구 {#debugging-tools}

AEM은 클라이언트 라이브러리 폴더를 디버깅하고 테스트하는 몇 가지 도구를 제공합니다.

### 클라이언트 라이브러리 검색 {#discover-client-libraries}

`/libs/cq/granite/components/dumplibs/dumplibs` 구성 요소는 시스템의 모든 클라이언트 라이브러리 폴더에 대한 정보 페이지를 생성합니다. `/libs/granite/ui/content/dumplibs` 노드에는 리소스 유형으로 구성 요소가 있습니다. 페이지를 열려면 다음 URL을 사용합니다(필요에 따라 호스트 및 포트 변경).

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

이 정보에는 라이브러리 경로 및 유형(CSS 또는 JS)과 카테고리 및 종속성과 같은 라이브러리 속성 값이 포함됩니다. 페이지의 후속 테이블에는 각 카테고리와 채널의 라이브러리가 표시됩니다.

### 생성된 출력 {#see-generated-output} 을 참조하십시오.

`dumplibs` 구성 요소에는 `ui:includeClientLib` 태그에 대해 생성된 소스 코드를 표시하는 테스트 선택기가 포함되어 있습니다. 페이지에는 js, css 및 테마 속성의 다양한 조합을 위한 코드가 포함되어 있습니다.

1. 다음 방법 중 하나를 사용하여 [테스트 출력] 페이지를 엽니다.
   * `dumplibs.html` 페이지에서 **출력 테스트** 텍스트를 보려면 여기를 클릭하십시오.
   * 웹 브라우저에서 다음 URL을 엽니다(필요에 따라 다른 호스트 및 포트 사용).
      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`
   * 기본 페이지에는 카테고리 속성에 대한 값이 없는 태그의 출력이 표시됩니다.
1. 범주에 대한 출력을 보려면 클라이언트 라이브러리의 `categories` 속성 값을 입력하고 **Submit Query**&#x200B;를 클릭합니다.

## 추가 클라이언트 라이브러리 폴더 기능 {#additional-features}

AEM의 클라이언트 라이브러리 폴더에서 지원하는 다른 많은 기능이 있습니다. 하지만, AEM에서 Cloud Service으로 사용할 필요는 없으며, 이러한 사용을 중단할 수도 있습니다. 완결성을 위해 여기에 나와 있습니다

>[!WARNING]
>
>이러한 클라이언트 라이브러리 폴더의 추가 기능은 AEM에서 Cloud Service으로 필요하지 않으며 이러한 추가 기능은 사용할 수 없습니다. 완결성을 위해 여기에 나와 있습니다

### Adobe Granite HTML 라이브러리 관리자 {#html-library-manager}

추가 클라이언트 라이브러리 설정은 `https://<host>:<port>/system/console/configMgr`에서 시스템 콘솔의 **Adobe Granite HTML 라이브러리 관리자** 패널을 통해 제어할 수 있습니다.

### 추가 폴더 속성 {#additional-folder-properties}

추가 폴더 속성에는 종속성 및 포함 제어를 허용하지만 일반적으로 더 이상 필요하지 않으며 사용할 수 없습니다.

* `dependencies`:이 라이브러리 폴더가 종속되는 다른 클라이언트 라이브러리 카테고리 목록입니다. 예를 들어, 두 개의 `cq:ClientLibraryFolder` 노드 `F` 및 `G`가 지정된 경우, `F`에 있는 파일에 제대로 작동하기 위해 `G`에 다른 파일이 필요한 경우 `G`의 `categories` 중 적어도 하나가 `F`의 `dependencies` 중 하나여야 합니다.
* `embed`:다른 라이브러리의 코드를 포함하는 데 사용됩니다. 노드 `F`에 노드 `G` 및 `H`가 포함된 경우 결과 HTML은 노드 `G` 및 `H`의 컨텐츠의 연결이 됩니다.

### 종속성 {#linking-to-dependencies}에 연결

클라이언트 라이브러리 폴더의 코드가 다른 라이브러리를 참조하면 다른 라이브러리를 종속성으로 식별합니다. 클라이언트 라이브러리 폴더를 참조하는 `ui:includeClientLib` 태그로 인해 HTML 코드가 생성된 라이브러리 파일과 종속성에 대한 링크를 포함합니다.

종속성은 다른 `cq:ClientLibraryFolder`여야 합니다. 종속성을 식별하려면 다음 속성을 사용하여 `cq:ClientLibraryFolder` 노드에 속성을 추가하십시오.

* **이름:** 종속성
* **유형:** 문자열[]
* **값:**  현재 라이브러리 폴더가 종속되는 cq:ClientLibraryFolder 노드의 categories 속성 값입니다.

예를 들어 `/etc/clientlibs/myclientlibs/publicmain`은 `cq.jquery` 라이브러리에 대한 종속성을 갖습니다. 기본 클라이언트 라이브러리를 참조하는 페이지는 다음 코드를 포함하는 HTML을 생성합니다.

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### 다른 라이브러리의 코드 포함 {#embedding-code-from-other-libraries}

클라이언트 라이브러리의 코드를 다른 클라이언트 라이브러리에 포함할 수 있습니다. 런타임 시, 포함 라이브러리의 생성된 JS 및 CSS 파일은 포함된 라이브러리의 코드를 포함합니다.

포함 코드는 저장소의 보안 영역에 저장된 라이브러리에 대한 액세스를 제공하는 데 유용합니다.

#### 앱별 클라이언트 라이브러리 폴더 {#app-specific-client-library-folders}

모든 응용 프로그램 관련 파일을 응용 프로그램 폴더에 `/app` 아래에 보관하는 것이 좋습니다. 또한 `/app` 폴더에 대한 웹 사이트 방문자의 액세스를 거부하는 것이 좋습니다. 두 가지 우수 사례를 모두 충족하려면 `/app` 아래에 있는 클라이언트 라이브러리를 포함하는 `/etc` 폴더 아래에 클라이언트 라이브러리 폴더를 만드십시오.

categories 속성을 사용하여 포함할 클라이언트 라이브러리 폴더를 식별합니다. 라이브러리를 포함하려면 다음 속성 속성을 사용하여 포함 `cq:ClientLibraryFolder` 노드에 속성을 추가하십시오.

* **이름:** 포함
* **유형:** 문자열[]
* **값:** 포함할 노드의 카테고리 속성  `cq:ClientLibraryFolder` 값입니다.

#### 포함 을 사용하여 요청 최소화 {#using-embedding-to-minimize-requests}

경우에 따라 게시 인스턴스에서 일반 페이지에 대해 생성한 최종 HTML에 상대적으로 많은 `<script>` 요소가 포함되어 있는 것을 찾을 수 있습니다.

이러한 경우 페이지 로드 시 전후 요청의 수가 감소하도록 필요한 모든 클라이언트 라이브러리 코드를 하나의 파일에 결합하는 것이 유용할 수 있습니다. 이렇게 하려면 `cq:ClientLibraryFolder` 노드의 embed 속성을 사용하여 필요한 라이브러리를 앱별 클라이언트 라이브러리에 `embed` 삽입할 수 있습니다.

#### CSS 파일의 경로 {#paths-in-css-files}

CSS 파일을 포함하면 생성된 CSS 코드는 포함 라이브러리를 기준으로 하는 리소스에 대한 경로를 사용합니다. 예를 들어 공개적으로 액세스할 수 있는 라이브러리 `/etc/client/libraries/myclientlibs/publicmain`에는 `/apps/myapp/clientlib` 클라이언트 라이브러리가 포함됩니다.

`main.css` 파일에는 다음 스타일이 포함되어 있습니다.

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

`publicmain` 노드가 생성하는 CSS 파일에는 원본 이미지의 URL을 사용하여 다음 스타일이 포함되어 있습니다.

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

#### HTML 출력에 포함된 파일 {#see-embedded-files} 을 참조하십시오.

포함된 코드의 출처를 추적하거나 포함된 클라이언트 라이브러리에서 예상 결과를 산출하는지 확인하기 위해 런타임 시 포함 중인 파일의 이름을 볼 수 있습니다. 파일 이름을 보려면 `debugClientLibs=true` 매개 변수를 웹 페이지의 URL에 추가하십시오. 생성된 라이브러리에는 포함된 코드 대신 `@import` 문이 포함되어 있습니다.

이전 [다른 라이브러리에서 코드 포함](#embedding-code-from-other-libraries) 섹션의 예에서 `/etc/client/libraries/myclientlibs/publicmain` 클라이언트 라이브러리 폴더에는 `/apps/myapp/clientlib` 클라이언트 라이브러리 폴더가 포함됩니다. 웹 페이지에 매개 변수를 추가하면 웹 페이지의 소스 코드에 다음 링크가 생성됩니다.

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

`publicmain.css` 파일을 열면 다음 코드가 표시됩니다.

```javascript
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. 웹 브라우저의 주소 상자에서 HTML의 URL에 다음 텍스트를 추가합니다.
   * `?debugClientLibs=true`
1. 페이지가 로드되면 페이지 소스를 봅니다.
1. 링크 요소에 대한 href로 제공되는 링크를 클릭하여 파일을 열고 소스 코드를 확인합니다.

### 전처리기 사용 {#using-preprocessors}

AEM에서는 플러그형 전처리기 및 CSS 및 JavaScript용 [YUI 압축기](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) 및 YUI가 AEM 기본 전처리기로 설정된 JavaScript용 [Google Closure Compiler(GCC)](https://developers.google.com/closure/compiler/)에 대한 지원을 제공합니다.

플러그형 전처리기는 다음과 같은 유연한 사용을 허용합니다.

* 스크립트 소스를 처리할 수 있는 ScriptProcessor 정의
* 프로세서는 옵션을 사용하여 구성할 수 있습니다
* 프로세서는 축소에 사용할 수 있지만 축소되지 않은 경우도 사용할 수 있습니다
* clientlib은 사용할 프로세서를 정의할 수 있습니다

>[!NOTE]
>
>기본적으로 AEM은 YUI 압축기를 사용합니다. 알려진 문제 목록은 [YUI 압축기 GitHub 설명서](https://github.com/yui/yuicompressor/issues)를 참조하십시오. 특정 clientlibs를 위해 GCC 압축기로 전환하면 YUI 사용 시 발생하는 몇 가지 문제를 해결할 수 있습니다.

>[!CAUTION]
>
>축소된 라이브러리를 클라이언트 라이브러리에 배치하지 마십시오. 대신 원시 라이브러리를 제공하고 축소가 필요한 경우 전처리자의 옵션을 사용합니다.

#### 사용량 {#usage}

클라이언트 라이브러리 또는 시스템 전체에 대해 전처리기 구성을 구성할 수 있습니다.

* clientlibrary 노드에 multivalue 속성 `cssProcessor` 및 `jsProcessor` 추가
* 또는 **HTML 라이브러리 관리자** OSGi 구성을 통해 시스템 기본 구성을 정의합니다

clientlib 노드의 사전 프로세서 구성이 OSGI 구성에 우선합니다.

#### 형식 및 예 {#format-and-examples}

##### 형식 {#format}

```javascript
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

##### JS {#yui-compressor-for-css-minification-and-gcc-for-js}의 CSS 축소와 GCC용 YUI 압축기

```javascript
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

##### Typescript에서 Preprocess로 이동한 다음 GCC에서 {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate} 축소 및 난독화를 수행합니다.

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

GCC 옵션에 대한 자세한 내용은 [GCC 설명서](https://developers.google.com/closure/compiler/docs/compilation_levels)를 참조하십시오.

#### 시스템 기본 미니어 설정 {#set-system-default-minifier}

YUI가 AEM에서 기본 축소기로 설정됩니다. GCC로 변경하려면 다음 단계를 수행합니다.

1. (`http://<host>:<portY/system/console/configMgr`)의 Apache Felix 구성 관리자로 이동합니다.
1. **Granite HTML 라이브러리 관리자 Adobe**&#x200B;를 찾고 편집합니다.
1. **Minify** 옵션을 활성화합니다(아직 활성화되지 않은 경우).
1. 값 **JS 프로세서 기본 구성**&#x200B;을 `min:gcc`로 설정합니다.
   * 세미콜론으로 구분하여 선택 사항을 전달할 수 있습니다(예: ).`min:gcc;obfuscate=true`
1. **저장**&#x200B;을 클릭하여 변경 내용을 저장합니다.
