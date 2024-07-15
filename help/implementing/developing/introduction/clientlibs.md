---
title: AEM as a Cloud Service에서 클라이언트측 라이브러리 사용
description: AEM은 클라이언트측 코드(clientlib)를 저장소에 저장하고, 카테고리로 구성하고, 각 코드 카테고리가 클라이언트에 제공되는 시기와 방법을 정의할 수 있는 클라이언트측 라이브러리 폴더를 제공합니다
exl-id: 370db625-09bf-43fb-919d-4699edaac7c8
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2497'
ht-degree: 1%

---


# AEM as a Cloud Service에서 클라이언트측 라이브러리 사용 {#using-client-side-libraries}

디지털 경험은 복잡한 JavaScript 및 CSS 코드로 구동되는 클라이언트측 처리에 크게 의존합니다. AEM 클라이언트 측 라이브러리(clientlibs)를 사용하면 이러한 클라이언트 측 라이브러리를 구성하고 저장소 내에 중앙에서 저장할 수 있습니다. AEM Project Archetype의 [프론트엔드 빌드 프로세스와 함께 ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html)하면 AEM 프로젝트에 대한 프론트엔드 코드를 간편하게 관리할 수 있습니다.

AEM에서 clientlib을 사용할 때의 장점은 다음과 같습니다.

* 클라이언트측 코드는 다른 모든 애플리케이션 코드 및 콘텐츠와 마찬가지로 저장소에 저장됩니다
* AEM의 Clientlib은 모든 CSS 및 JS를 하나의 파일로 집계할 수 있습니다
* [dispatcher](/help/implementing/dispatcher/disp-overview.md)을(를) 통해 액세스할 수 있는 경로를 통해 clientlib을 노출합니다.
* 참조된 파일 또는 이미지에 대한 경로 재작성을 허용합니다.

Clientlib은 AEM에서 CSS 및 JavaScript을 제공하는 기본 제공 솔루션입니다.

>[!TIP]
>
>AEM 프로젝트용 CSS 및 JavaScript을 만드는 프론트엔드 개발자도 [AEM Project Archetype 및 자동화된 프론트엔드 빌드 프로세스를 숙지해야 합니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html)

## 클라이언트측 라이브러리란 무엇입니까? {#what-are-clientlibs}

사이트에서는 클라이언트측에서 처리할 JavaScript 및 CSS와 아이콘 및 웹 글꼴과 같은 정적 리소스가 필요합니다. clientlib은 AEM에서 참조하고(필요한 경우 카테고리별로) 이러한 리소스를 제공하는 메커니즘입니다.

AEM은 사이트의 CSS와 JavaScript을 중앙 위치에 있는 단일 파일로 수집하여 HTML 출력에 모든 리소스의 복사본을 하나만 포함하도록 합니다. 이를 통해 게재 효율성을 극대화하고 프록시를 통해 이러한 리소스를 저장소 중앙에서 유지 관리할 수 있어 액세스 보안을 유지할 수 있습니다.

## AEM as a Cloud Service용 프론트엔드 개발 {#fed-for-aemaacs}

모든 JavaScript, CSS 및 기타 프론트엔드 자산은 AEM Project Archetype의 [ui.frontend 모듈에서 유지 관리되어야 합니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html) Archetype의 유연성을 통해 원하는 최신 웹 도구를 사용하여 이러한 리소스를 만들고 관리할 수 있습니다.

그런 다음 Archetype은 리소스를 단일 CSS 및 JS 파일로 컴파일하여 리포지토리의 `cq:clientLibraryFolder`에 자동으로 포함할 수 있습니다.

## 클라이언트측 라이브러리 폴더 구조 {#clientlib-folders}

클라이언트측 라이브러리 폴더는 `cq:ClientLibraryFolder` 유형의 저장소 노드입니다. [CND 표기법](https://jackrabbit.apache.org/node-type-notation.html)의 정의는 다음과 같습니다.

```text
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

* `cq:ClientLibraryFolder`개의 노드를 저장소의 `/apps` 하위 트리 내 어디에나 배치할 수 있습니다.
* 노드의 `categories` 속성을 사용하여 노드가 속한 라이브러리 범주를 식별합니다.

각 `cq:ClientLibraryFolder`은(는) 몇 개의 지원 파일과 함께 JS 및/또는 CSS 파일 세트로 채워집니다(아래 참조). `cq:ClientLibraryFolder`의 중요한 속성은 다음과 같이 구성됩니다.

* `allowProxy`: 모든 clientlib은 `apps`에 저장되어야 하므로 이 속성을 사용하면 프록시 서블릿을 통해 클라이언트 라이브러리에 액세스할 수 있습니다. 아래의 [클라이언트 라이브러리 폴더 찾기 및 프록시 클라이언트 라이브러리 서블릿 사용](#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) 섹션을 참조하십시오.
* `categories`: 이 `cq:ClientLibraryFolder` 내의 JS 및/또는 CSS 파일 집합이 속하는 범주를 식별합니다. `categories` 속성은 다중값이므로 라이브러리 폴더가 둘 이상의 범주에 속할 수 있습니다(이 기능이 어떻게 유용할 수 있는지 아래 참조).

클라이언트 라이브러리 폴더에 런타임 시 단일 JS 및/또는 CSS 파일로 병합되는 하나 이상의 소스 파일이 포함되어 있는 경우. 생성된 파일의 이름은 `.js` 또는 `.css` 파일 이름 확장명을 가진 노드 이름입니다. 예를 들어, 이름이 `cq.jquery`인 라이브러리 노드는 `cq.jquery.js` 또는 `cq.jquery.css`인 생성된 파일을 생성합니다.

클라이언트 라이브러리 폴더에는 다음 항목이 포함되어 있습니다.

* JS 및/또는 CSS 소스 파일
* 아이콘, 웹 글꼴 등과 같이 CSS 스타일을 지원하는 정적 리소스입니다.
* 생성된 JS 및/또는 CSS 파일에서 병합할 소스 파일을 식별하는 하나의 `js.txt` 파일 및/또는 하나의 `css.txt` 파일

![Clientlib 아키텍처](assets/clientlib-architecture.drawio.png)

## 클라이언트측 라이브러리 폴더 만들기 {#creating-clientlib-folders}

클라이언트 라이브러리는 `/apps` 아래에 있어야 합니다. 이 규칙은 콘텐츠 및 구성에서 코드를 더 잘 분리하는 데 필요합니다.

`/apps` 아래의 클라이언트 라이브러리에 액세스하려면 프록시 서블릿을 사용하십시오. ACL은 여전히 클라이언트 라이브러리 폴더에 적용되지만 `allowProxy` 속성이 `true`(으)로 설정된 경우 서블릿에서 `/etc.clientlibs/`을(를) 통해 콘텐츠를 읽을 수 있습니다.

1. 웹 브라우저(`https://<host>:<port>/crx/de`)에서 CRXDE Lite을 엽니다.
1. `/apps` 폴더를 선택하고 **만들기 > 노드 만들기**&#x200B;를 클릭합니다.
1. 라이브러리 폴더의 이름을 입력하고 **Type** 목록에서 `cq:ClientLibraryFolder`을(를) 선택하십시오. **확인**&#x200B;을 클릭한 다음 **모두 저장**&#x200B;을 클릭합니다.
1. 라이브러리가 속한 범주를 지정하려면 `cq:ClientLibraryFolder` 노드를 선택하고 다음 속성을 추가한 다음 **모두 저장**&#x200B;을 클릭합니다.
   * 이름: `categories`
   * 유형: 문자열
   * 값: 카테고리 이름
   * 다중: 선택됨
1. `/etc.clientlibs`에서 프록시를 통해 클라이언트 라이브러리에 액세스하려면 `cq:ClientLibraryFolder` 노드를 선택하고 다음 속성을 추가한 다음 **모두 저장**&#x200B;을 클릭하십시오.
   * 이름: `allowProxy`
   * 유형: 부울
   * 값: `true`
1. 정적 리소스를 관리해야 하는 경우 클라이언트 라이브러리 폴더 아래에 `resources`(이)라는 하위 폴더를 만듭니다.
   * `resources` 폴더 아래 이외의 위치에 정적 리소스를 저장하는 경우 게시 인스턴스에서 참조할 수 없습니다.
1. 라이브러리 폴더에 소스 파일을 추가합니다.
   * 이 작업은 일반적으로 [AEM Project Archetype.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html)의 프론트엔드 빌드 프로세스에서 수행됩니다.
   * 원하는 경우 하위 폴더에 소스 파일을 구성할 수 있습니다.
1. 클라이언트 라이브러리 폴더를 선택하고 **만들기 > 파일 만들기**&#x200B;를 클릭합니다.
1. 파일 이름 상자에 다음 파일 이름 중 하나를 입력하고 확인을 클릭합니다.
   * **`js.txt`:** 이 파일 이름을 사용하여 JavaScript 파일을 생성하십시오.
   * **`css.txt`:** 이 파일 이름을 사용하여 계단식 스타일 시트를 생성하십시오.
1. 파일을 열고 다음 텍스트를 입력하여 소스 파일의 경로 루트를 식별합니다.
   * `#base=*[root]*`
   * `[root]`을(를) TXT 파일을 기준으로 소스 파일이 포함된 폴더의 경로로 바꿉니다. 예를 들어 소스 파일이 TXT 파일과 동일한 폴더에 있는 경우 다음 텍스트를 사용합니다.
      * `#base=.`
   * 다음 코드는 루트를 `cq:ClientLibraryFolder` 노드 아래에 mobile이라는 폴더로 설정합니다.
      * `#base=mobile`
1. `#base=[root]` 아래 줄에 루트를 기준으로 소스 파일의 경로를 입력합니다. 각 파일 이름을 별도의 줄에 지정합니다.
1. **모두 저장**&#x200B;을 클릭합니다.

## 클라이언트측 라이브러리 제공 {#serving-clientlibs}

클라이언트 라이브러리 폴더가 [필요에 따라 구성되면](#creating-clientlib-folders) 프록시를 통해 클라이언트 라이브러리를 요청할 수 있습니다. 예:

* `/apps/myproject/clientlibs/foo`에 clientlib이 있습니다.
* `/apps/myprojects/clientlibs/foo/resources/icon.png`에 정적 이미지가 있습니다.

`allowProxy` 속성을 사용하여 다음을 요청할 수 있습니다.

* `/etc.clientlibs/myprojects/clientlibs/foo.js`을(를) 통한 clientlib
* `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`을(를) 통한 정적 이미지

### HTL을 통해 클라이언트 라이브러리 로드 {#loading-via-htl}

Clientlib을 클라이언트 라이브러리 폴더에 저장하고 관리하면 HTL을 통해 액세스할 수 있습니다.

클라이언트 라이브러리는 `data-sly-use`을(를) 통해 액세스할 수 있는 AEM에서 제공하는 도우미 템플릿을 통해 로드됩니다. 도우미 템플릿은 `data-sly-call`을(를) 통해 호출할 수 있는 이 파일에서 사용할 수 있습니다.

각 도우미 템플릿에는 원하는 클라이언트 라이브러리를 참조하기 위한 `categories` 옵션이 필요합니다. 해당 옵션은 문자열 값의 배열이거나 쉼표로 구분된 값 목록을 포함하는 문자열일 수 있습니다.

HTL을 통한 clientlib 로드에 대한 자세한 내용은 [HTL 설명서를 참조하십시오](https://experienceleague.adobe.com/docs/experience-manager-htl/using/getting-started/getting-started.html#loading-client-libraries).

<!--
### Setting Cache Timestamps {#setting-cache-timestamps}

This is possible. Still need detail.
-->

## 작성자의 클라이언트 라이브러리와 Publish 비교 {#clientlibs-author-publish}

대부분의 clientlib은 AEM 게시 인스턴스에 필요합니다. 즉, 대부분의 clientlib의 목적은 컨텐츠의 최종 사용자 경험을 생성하는 것입니다. 게시 인스턴스의 clientlib에 대해 위에서 설명한 대로 [클라이언트 라이브러리 폴더를 통해 [프론트엔드 빌드 도구](#fed-for-aemaacs)를 사용하고 배포할 수 있습니다.](#creating-clientlib-folders)

그러나 작성 환경을 사용자 지정하는 데 클라이언트 라이브러리가 필요한 경우가 있습니다. 예를 들어 대화 상자를 사용자 정의하려면 AEM 작성 인스턴스에 CSS 또는 JS의 작은 비트를 배포해야 할 수 있습니다.

### 작성자의 클라이언트 라이브러리 관리 {#clientlibs-on-author}

작성자에 대해 클라이언트 라이브러리를 사용해야 하는 경우 게시와 동일한 방법을 사용하여 `/apps`에 클라이언트 라이브러리를 만들 수 있지만, 전체 프로젝트를 만드는 대신 `/apps/.../clientlibs/foo`에 직접 작성하여 관리할 수 있습니다.

그런 다음 클라이언트 라이브러리를 기본 제공 클라이언트 라이브러리 카테고리에 추가하여 작성 JS에 &quot;후크&quot;할 수 있습니다.

## 디버깅 도구 {#debugging-tools}

AEM은 클라이언트 라이브러리 폴더를 디버깅하고 테스트하기 위한 몇 가지 도구를 제공합니다.

### 클라이언트 라이브러리 검색 {#discover-client-libraries}

`/libs/cq/granite/components/dumplibs/dumplibs` 구성 요소는 시스템의 모든 클라이언트 라이브러리 폴더에 대한 정보 페이지를 생성합니다. `/libs/granite/ui/content/dumplibs` 노드에 리소스 유형으로 구성 요소가 있습니다. 페이지를 열려면 다음 URL을 사용합니다(필요에 따라 호스트 및 포트 변경).

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

정보에는 라이브러리 경로 및 유형(CSS 또는 JS)과 라이브러리 속성의 값(예: 범주 및 종속성)이 포함됩니다. 페이지의 후속 테이블에는 각 카테고리 및 채널의 라이브러리가 표시됩니다.

### 생성된 출력 보기 {#see-generated-output}

`dumplibs` 구성 요소에는 `ui:includeClientLib` 태그에 대해 생성된 소스 코드를 표시하는 테스트 선택기가 포함되어 있습니다. 이 페이지에는 js, css 및 테마 속성의 다양한 조합에 대한 코드가 포함되어 있습니다.

1. 다음 방법 중 하나를 사용하여 테스트 출력 페이지를 엽니다.
   * `dumplibs.html` 페이지에서 **출력 테스트를 위해 여기를 클릭** 텍스트의 링크를 클릭합니다.
   * 웹 브라우저에서 다음 URL을 엽니다(필요에 따라 다른 호스트 및 포트 사용).
      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`
   * 기본 페이지에는 categories 속성에 대한 값이 없는 태그의 출력이 표시됩니다.
1. 범주에 대한 출력을 보려면 클라이언트 라이브러리의 `categories` 속성 값을 입력하고 **쿼리 제출**&#x200B;을 클릭합니다.

## 추가 클라이언트 라이브러리 폴더 기능 {#additional-features}

AEM의 클라이언트 라이브러리 폴더에서 지원하는 몇 가지 다른 기능이 있습니다. 그러나 AEM as a Cloud Service에서는 이러한 기능이 필요하지 않으므로 사용하지 마십시오. 완성도를 위해 여기에 나열됩니다.

>[!WARNING]
>
>클라이언트 라이브러리 폴더의 이러한 추가 기능은 AEM as a Cloud Service에 필요하지 않으므로 사용하지 마십시오. 완성도를 위해 여기에 나열됩니다.

### Adobe Granite HTML 라이브러리 관리자 {#html-library-manager}

추가 클라이언트 라이브러리 설정은 `https://<host>:<port>/system/console/configMgr`에 있는 시스템 콘솔의 **Adobe Granite HTML 라이브러리 관리자** 패널을 통해 제어할 수 있습니다.

### 추가 폴더 속성 {#additional-folder-properties}

추가 폴더 속성에는 종속성 및 임베드를 제어할 수 있는 기능이 포함되어 있지만 일반적으로 더 이상 필요하지 않으며 사용하지 않습니다.

* `dependencies`: 이 라이브러리 폴더가 종속된 다른 클라이언트 라이브러리 범주의 목록입니다. 예를 들어 두 개의 `cq:ClientLibraryFolder` 노드 `F` 및 `G`이(가) 지정된 경우, `F`의 파일이 제대로 작동하려면 `G`의 다른 파일이 필요한 경우 `G`의 `categories` 중 하나 이상이 `F`의 `dependencies`에 속해야 합니다.
* `embed`: 다른 라이브러리의 코드를 포함하는 데 사용됩니다. `F` 노드가 `G` 및 `H` 노드를 임베드하는 경우 결과 HTML은 `G` 및 `H` 노드의 콘텐츠 연결입니다.

### 종속성에 연결 {#linking-to-dependencies}

클라이언트 라이브러리 폴더의 코드가 다른 라이브러리를 참조하면 다른 라이브러리를 종속성으로 식별합니다. 클라이언트 라이브러리 폴더를 참조하는 `ui:includeClientLib` 태그로 인해 HTML 코드에는 생성된 라이브러리 파일에 대한 링크와 종속성이 포함됩니다.

종속성은 다른 `cq:ClientLibraryFolder`이어야 합니다. 종속성을 식별하려면 다음 특성을 사용하여 `cq:ClientLibraryFolder` 노드에 속성을 추가하십시오.

* **이름:** 종속성
* **유형:** 문자열[]
* **값:** 현재 라이브러리 폴더가 사용하는 cq:ClientLibraryFolder 노드의 categories 속성 값입니다.

예를 들어 `/etc/clientlibs/myclientlibs/publicmain`은(는) `cq.jquery` 라이브러리에 종속되어 있습니다. 기본 클라이언트 라이브러리를 참조하는 페이지는 다음 코드를 포함하는 HTML을 생성합니다.

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### 다른 라이브러리의 코드 포함 {#embedding-code-from-other-libraries}

클라이언트 라이브러리의 코드를 다른 클라이언트 라이브러리에 포함할 수 있습니다. 런타임 시 포함 라이브러리의 생성된 JS 및 CSS 파일은 포함 라이브러리의 코드를 포함합니다.

포함 코드는 저장소의 보안 영역에 저장된 라이브러리에 대한 액세스를 제공하는 데 유용합니다.

#### 앱별 클라이언트 라이브러리 폴더 {#app-specific-client-library-folders}

모든 응용 프로그램 관련 파일을 응용 프로그램 폴더 `/apps` 아래에 보관하는 것이 좋습니다. 또한 `/apps` 폴더에 대한 웹 사이트 방문자의 액세스를 거부하는 것이 좋습니다. 두 모범 사례를 모두 충족하려면 `/apps` 아래의 클라이언트 라이브러리를 임베드하는 `/etc` 폴더 아래에 클라이언트 라이브러리 폴더를 만드십시오.

포함할 클라이언트 라이브러리 폴더를 식별하려면 categories 속성을 사용합니다. 라이브러리를 포함하려면 다음 속성 특성을 사용하여 포함 `cq:ClientLibraryFolder` 노드에 속성을 추가하십시오.

* **이름:** 포함
* **유형:** 문자열[]
* **값:** 포함할 `cq:ClientLibraryFolder` 노드의 categories 속성 값입니다.

#### 포함을 사용하여 요청 최소화 {#using-embedding-to-minimize-requests}

경우에 따라 게시 인스턴스에 의해 일반 페이지에 대해 생성된 최종 HTML에 비교적 많은 `<script>`개의 요소가 포함되어 있을 수 있습니다.

이러한 경우 페이지 로드 시 앞뒤 요청 수가 줄어들도록 필요한 모든 클라이언트 라이브러리 코드를 단일 파일에 결합하는 것이 유용할 수 있습니다. 이렇게 하려면 `cq:ClientLibraryFolder` 노드의 포함 속성을 사용하여 필요한 라이브러리를 앱별 클라이언트 라이브러리에 `embed`할 수 있습니다.

#### CSS 파일의 경로 {#paths-in-css-files}

CSS 파일을 포함할 때 생성된 CSS 코드는 포함 라이브러리에 상대적인 리소스에 대한 경로를 사용합니다. 예를 들어 공개적으로 액세스할 수 있는 라이브러리 `/etc/client/libraries/myclientlibs/publicmain`은(는) `/apps/myapp/clientlib` 클라이언트 라이브러리를 임베드합니다.

`main.css` 파일에 다음 스타일이 포함되어 있습니다.

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

`publicmain` 노드가 생성하는 CSS 파일에 원본 이미지의 URL을 사용하는 다음 스타일이 포함되어 있습니다.

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

#### HTML 출력에 포함된 파일 보기 {#see-embedded-files}

포함된 코드의 원본을 추적하거나 포함된 클라이언트 라이브러리가 예상 결과를 생성하도록 하려면 런타임 시 포함된 파일의 이름을 볼 수 있습니다. 파일 이름을 보려면 `debugClientLibs=true` 매개 변수를 웹 페이지의 URL에 추가하십시오. 생성된 라이브러리에 포함된 코드 대신 `@import` 문이 포함되어 있습니다.

이전 [다른 라이브러리의 코드 포함](#embedding-code-from-other-libraries) 섹션의 예제에서 `/etc/client/libraries/myclientlibs/publicmain` 클라이언트 라이브러리 폴더는 `/apps/myapp/clientlib` 클라이언트 라이브러리 폴더를 임베드합니다. 웹 페이지에 매개 변수를 추가하면 웹 페이지의 소스 코드에 다음과 같은 링크가 만들어집니다.

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

`publicmain.css` 파일을 열면 다음 코드가 표시됩니다.

```javascript
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. 웹 브라우저의 주소 상자에서 HTML URL에 다음 텍스트를 추가합니다.
   * `?debugClientLibs=true`
1. 페이지가 로드되면 페이지 소스를 봅니다.
1. 링크 요소에 대해 href로 제공된 링크를 클릭하여 파일을 열고 소스 코드를 봅니다.

### 전처리기 사용 {#using-preprocessors}

AEM에서는 플러그 가능한 전처리기를 허용하며 CSS 및 JavaScript용 [YUI Compressor](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) 및 AEM의 기본 전처리기로 설정된 JavaScript용 [Google Closure Compiler(GCC)](https://developers.google.com/closure/compiler/)을(를) 지원합니다.

플러그 가능한 프리프로세서는 다음을 포함하여 유연하게 사용할 수 있습니다.

* 스크립트 소스를 처리할 수 있는 스크립트 프로세서 정의
* 옵션으로 프로세서 구성 가능
* 프로세서는 축소되지 않은 경우에도 사용할 수 있습니다.
* clientlib은 사용할 프로세서를 정의할 수 있습니다

>[!NOTE]
>
>기본적으로 AEM은 YUI Compressor를 사용합니다. 알려진 문제 목록은 [YUI 압축기 GitHub 설명서](https://github.com/yui/yuicompressor/issues)를 참조하십시오. 특정 클라이언트 라이브러리에 대해 GCC 압축기로 전환하면 YUI 사용 시 관찰되는 몇 가지 문제를 해결할 수 있습니다.

>[!CAUTION]
>
>축소된 라이브러리를 클라이언트 라이브러리에 배치하지 마십시오. 대신 원시 라이브러리를 제공하고, 축소가 필요한 경우 사전 프로세서의 옵션을 사용합니다.

#### 사용 {#usage}

클라이언트 라이브러리 또는 시스템 전체에 대해 프로세서 구성을 구성할 수 있습니다.

* Clientlibrary 노드에서 다중 값 속성 `cssProcessor` 및 `jsProcessor`을(를) 추가합니다.
* 또는 **HTML 라이브러리 관리자** OSGi 구성을 통해 시스템 기본 구성을 정의하십시오.

clientlib 노드의 전처리기 구성이 OSGI 구성보다 우선합니다.

#### 형식 및 예 {#format-and-examples}

##### 형식 {#format}

```javascript
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

##### CSS용 YUI 압축기 축소 및 JS용 GCC {#yui-compressor-for-css-minification-and-gcc-for-js}

```javascript
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

##### 사전 처리할 Typescript를 입력한 다음 축소 및 난독화할 GCC {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate}

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

#### 시스템 기본 축소기 설정 {#set-system-default-minifier}

AEM에서 YUI가 기본 축소기로 설정됩니다. GCC로 변경하려면 다음 단계를 따르십시오.

1. (`http://<host>:<port/system/console/configMgr`)의 Apache Felix 구성 관리자로 이동합니다.
1. **Adobe Granite HTML 라이브러리 관리자**&#x200B;를 찾아 편집합니다.
1. **축소** 옵션을 활성화합니다(아직 활성화되지 않은 경우).
1. 값 **JS 프로세서 기본 구성**&#x200B;을(를) `min:gcc`(으)로 설정합니다.
   * 옵션을 세미콜론으로 구분하면 전달할 수 있습니다(예: `min:gcc;obfuscate=true`).
1. 변경 내용을 저장하려면 **저장**&#x200B;을 클릭하세요.
