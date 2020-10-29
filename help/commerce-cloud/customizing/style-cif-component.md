---
title: AEM CIF 핵심 구성 요소 스타일 지정
description: AEM CIF 핵심 구성 요소의 스타일을 지정하는 방법을 알아봅니다. 이 자습서에서는 Client-Side Libraries 또는 clientlibs를 사용하여 Adobe Experience Manager(AEM) 커머스 구현을 위한 CSS 및 Javascript를 배포 및 관리하는 방법에 대해 설명합니다. 이 자습서에서는 ui.frontend 모듈과 웹 팩 프로젝트를 엔드 투 엔드 빌드 프로세스에 통합하는 방법도 다룹니다.
sub-product: 상거래
topics: Development
version: cloud-service
doc-type: tutorial
activity: develop
audience: developer
feature: Commerce Integration Framework
kt: 3456
thumbnail: 3456-style-cif.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '2592'
ht-degree: 2%

---


# AEM CIF 핵심 구성 요소 스타일 지정 {#style-aem-cif-core-components}

CIF [Venia](https://github.com/adobe/aem-cif-guides-venia) 프로젝트는 [CIF 코어 구성 요소를 사용하기 위한 참조 코드 베이스입니다](https://github.com/adobe/aem-core-cif-components). 이 자습서에서는 Venia 참조 프로젝트를 검사하고 AEM CIF Core 구성 요소에서 사용되는 CSS 및 JavaScript를 구성하는 방법을 알아봅니다. 또한 CSS를 사용하여 새 스타일을 만들어 **제품 티저 구성 요소의 기본 스타일을** 업데이트합니다.

>[!TIP]
>
> 직접 상거래 구현을 시작할 때 [AEM 프로젝트](https://github.com/adobe/aem-project-archetype) 원형 유형을 사용하십시오.

## 구축 내용

이 자습서에서는 카드와 유사한 제품 티저 구성 요소에 대해 새 스타일이 구현됩니다. 자습서에서 학습한 교훈을 다른 CIF 핵심 구성 요소에 적용할 수 있습니다.

![구축 내용](../assets/style-cif-component/what-you-will-build.png)

## 전제 조건 {#prerequisites}

이 자습서를 완료하려면 로컬 개발 환경이 필요합니다. 여기에는 Magento 인스턴스에 구성 및 연결된 실행 중인 AEM 인스턴스가 포함됩니다. AEM을 Cloud Service SDK로 사용하여 로컬 개발 [을 설정하는 요구 사항과 단계를 검토하십시오](../develop.md).

## Venia 프로젝트 복제 {#clone-venia-project}

Venia Project를 [복제한](https://github.com/adobe/aem-cif-guides-venia) 다음 기본 스타일을 무시합니다.

>[!NOTE]
>
> **CIF가 포함된 AEM Project Tranype을 기반으로 기존 프로젝트를** 자유롭게 사용하고 이 섹션을 건너뜁니다.

1. 다음 git 명령을 실행하여 프로젝트를 복제합니다.

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. 프로젝트를 빌드하고 AEM의 로컬 인스턴스에 배포합니다.

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. AEM 인스턴스를 Magento 인스턴스에 연결하거나 구성을 새로 만든 프로젝트에 추가하려면 필요한 OSGi 구성을 추가하십시오.

1. 이때 Magento 인스턴스에 연결된 스토어프런트 작업 버전이 있어야 합니다. 다음 위치에서 `US` > `Home` 페이지로 이동합니다. [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

   당신은 현재 매점이 베니아 테마를 사용하고 있다는 것을 보아야 합니다. 스토어프런트의 기본 메뉴를 확장하면 연결 Magento이 작동하는지 나타내는 다양한 카테고리가 표시됩니다.

   ![Venia 테마를 사용하여 구성된 스토어](../assets/style-cif-component/venia-store-configured.png)

## 클라이언트 라이브러리 및 ui.frontend 모듈 {#introduction-to-client-libraries}

스토어프런트 테마와 스타일을 렌더링하는 책임이 있는 CSS 및 JavaScript는 [클라이언트 라이브러리](/help/implementing/developing/introduction/clientlibs.md) 또는 clientlibs에서 간단하게 관리합니다. 클라이언트 라이브러리는 프로젝트 코드에서 CSS 및 Javascript를 구성한 다음 페이지에 전달하는 메커니즘을 제공합니다.

이러한 클라이언트 라이브러리에 의해 관리되는 CSS를 추가하고 대체하여 AEM CIF 핵심 구성 요소에 브랜드 전용 스타일을 적용할 수 있습니다. 클라이언트 라이브러리가 구조화되고 페이지에 포함되는 방법을 이해하는 것이 중요합니다.

ui. [frontend](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/uifrontend.html) 는 프로젝트에 대한 모든 프런트 엔드 에셋을 관리하는 전용 [웹 팩](https://webpack.js.org/) 프로젝트입니다. 이를 통해 프런트 엔드 개발자는 [TypeScript](https://www.typescriptlang.org/), Sass 등과 같은 다양한 언어와 기술을 사용할 [수](https://sass-lang.com/) 있습니다.

또한 이 `ui.frontend` 모듈은 Maven 모듈이며 aem-clientlib-generator의 NPM 모듈 [을 사용하여 더 큰 프로젝트와 통합됩니다](https://github.com/wcm-io-frontend/aem-clientlib-generator). 빌드 중에 컴파일된 CSS 및 JavaScript 파일을 모듈의 클라이언트 라이브러리에 `aem-clientlib-generator` `ui.apps` 복사합니다.

![ui.frontend ui.apps 아키텍처](../assets/style-cif-component/ui-frontend-architecture.png)

*컴파일된 CSS 및 Javascript는 Maven 빌드 동안 `ui.frontend` 모듈에서 클라이언트 라이브러리로 `ui.apps` 모듈로 복사됩니다*

## 티저 스타일 업데이트 {#ui-frontend-module}

다음으로, Teaser 스타일을 변경하여 `ui.frontend` 모듈과 clientlibraries의 작동 방식을 확인합니다. Venia 프로젝트 [를 가져오려면 원하는](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) IDE를 사용하십시오. 사용된 스크린샷은 [Visual Studio 코드 IDE에서 가져온 것입니다](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code).

1. ui. **frontend** 모듈을 탐색 및 확장하고 폴더 계층 구조를 다음으로 확장합니다. `ui.frontend/src/main/styles/commerce`:

   ![ui.frontend 커머스 폴더](../assets/style-cif-component/ui-frontend-commerce-folder.png)

   폴더 아래에 여러 개의 Sass(`.scss`) 파일이 있습니다. 이러한 스타일은 각 상거래 구성 요소에 대한 상거래 특정 스타일입니다.

1. Open the file `_productteaser.scss`.

1. 규칙을 `.item__image` 업데이트하고 테두리 규칙을 수정합니다.

   ```scss
   .item__image {
       border: #ea00ff 8px solid; /* <-- modify this rule */
       display: block;
       grid-area: main;
       height: auto;
       opacity: 1;
       transition-duration: 512ms;
       transition-property: opacity, visibility;
       transition-timing-function: ease-out;
       visibility: visible;
       width: 100%;
   }
   ```

   위의 규칙은 제품 티저 구성 요소에 매우 굵은 분홍색 테두리를 추가해야 합니다.

1. 새 터미널 창을 열고 `ui.frontend` 폴더로 이동합니다.

   ```shell
   $ cd <project-location>/aem-cif-guides-venia/ui.frontend
   ```

1. 다음 마비안 명령을 실행합니다.

   ```shell
   $ mvn clean install
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  29.497 s
   [INFO] Finished at: 2020-08-25T14:30:44-07:00
   [INFO] ------------------------------------------------------------------------
   ```

   Inspect의 최종 출력. Maven 명령이 여러 개의 NPM 스크립트를 실행했음을 확인할 수 `npm run build`있습니다. 이 `npm run build` 명령은 `package.json` 파일에 정의되며 웹 팩 프로젝트를 컴파일하고 클라이언트 라이브러리 생성을 트리거하는 효과가 있습니다.

1. Inspect `ui.frontend/dist/clientlib-site/site.css`:

   ![컴파일된 사이트 CSS](../assets/style-cif-component/comiled-site-css.png)

   파일은 프로젝트에서 모든 Sass 파일의 컴파일되고 축소된 버전입니다.

   >[!NOTE]
   >
   > 이와 같은 파일은 빌드 시간 동안 생성되어야 하므로 소스 컨트롤에서 무시됩니다.

1. 파일을 Inspect으로 `ui.frontend/clientlib.config.js`전송합니다.

   ```js
   /* clientlib.config.js*/
   ...
   // Config for `aem-clientlib-generator`
   module.exports = {
       context: BUILD_DIR,
       clientLibRoot: CLIENTLIB_DIR,
       libs: [
           {
               ...libsBaseConfig,
               name: 'clientlib-site',
               categories: ['venia.site'],
               dependencies: ['venia.dependencies', 'aem-core-cif-react-components'],
               assets: {
   ...
   ```

   이 파일은 aem-clientlib-generator [용](https://github.com/wcm-io-frontend/aem-clientlib-generator) 구성 파일이며, 컴파일된 CSS 및 JavaScript가 AEM 클라이언트 라이브러리로 변형되는 위치와 방법을 결정합니다.

1. 모듈에서 파일을 `ui.apps` 검사합니다. `ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-site/css/site.css`:

   ![ui.apps의 컴파일된 사이트 CSS](../assets/style-cif-component/comiled-css-ui-apps.png)

   이렇게 하면 복사한 `site.css` 파일이 `ui.apps` 프로젝트에 추가됩니다. 이제 카테고리로 명명된 클라이언트 라이브러리 `clientlib-site` 의 일부입니다 `venia.site`. 파일이 모듈의 일부이면 AEM에 배포할 수 `ui.apps` 있습니다.

   >[!NOTE]
   >
   > 이와 같은 파일은 빌드 시간 동안 생성되어야 하므로 소스 컨트롤에서 무시됩니다.

1. 다음으로 프로젝트에서 생성된 다른 클라이언트 라이브러리를 검사합니다.

   ![기타 클라이언트 라이브러리](../assets/style-cif-component/other-clientlibs.png)

   이러한 클라이언트 라이브러리는 `ui.frontend` 모듈에서 관리하지 않습니다. 대신 이러한 클라이언트 라이브러리에는 Adobe에서 제공하는 CSS 및 JavaScript 종속성이 포함됩니다. 이러한 clientlibraries에 대한 정의는 각 폴더 아래의 `.content.xml` 파일에 있습니다.

   **clientlib-base** - [AEM 코어 구성 요소의 필수 종속성을 간단히 제공하는 빈 클라이언트 라이브러리입니다](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html). 카테고리가 `venia.base`있습니다.

   **clientlib-cif** - [AEM CIF 핵심 구성 요소의 필수 종속성을 간단히 제공하는 빈 클라이언트 라이브러리입니다](https://github.com/adobe/aem-core-cif-components). 카테고리가 `venia.cif`있습니다.

   **clientlib-grid** - AEM 응답형 격자 기능을 활성화하는 데 필요한 CSS가 포함됩니다. AEM 그리드를 사용하면 AEM [편집기에서](https://docs.adobe.com/content/help/en/experience-manager-65/administering/operations/configuring-responsive-layout.html#include-the-responsive-css) 레이아웃 모드를 사용할 수 있으며 컨텐츠 작성자에게 구성 요소의 크기를 다시 조정할 수 있는 기능이 제공됩니다. 카테고리는 라이브러리 `venia.grid` 에 `venia.base` 포함되며

1. Inspect `customheaderlibs.html` 와 다음 `customfooterlibs.html` 과 `ui.apps/src/main/content/jcr_root/apps/venia/components/page`같이

   ![사용자 정의 머리글 및 바닥글 스크립트](../assets/style-cif-component/custom-header-footer-script.png)

   이러한 스크립트에는 모든 페이지의 **일부로** venia.base **및** venia.cif라이브러리가 포함됩니다.

   >[!NOTE]
   >
   > 기본 라이브러리만 페이지 스크립트의 일부로 &quot;하드 코딩됨&quot;입니다. `venia.site` 은 이러한 파일에 포함되지 않으며 대신 페이지 템플릿의 일부로 포함되어 있어 유연성을 높일 수 있습니다. 이것은 나중에 검사될 것입니다.

1. 터미널에서 전체 프로젝트를 구축하여 AEM의 로컬 인스턴스에 배포합니다.

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

## 제품 티저 작성 {#author-product-teaser}

이제 코드 업데이트가 배포되었으므로 AEM 제작 도구를 사용하여 제품 티저 구성 요소의 새 인스턴스를 사이트의 홈 페이지에 추가합니다. 그러면 업데이트된 스타일을 볼 수 있습니다.

1. 새 브라우저 탭을 열고 사이트의 **홈 페이지로** 이동합니다. [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. 편집 모드에서 자산 파인더(사이드 레일) **를** 확장합니다. 자산 필터를 **제품으로 전환합니다**.

   ![자산 파인더 확장 및 제품별 필터링](../assets/style-cif-component/drag-drop-product-page.png)

1. 새 제품을 기본 레이아웃 컨테이너의 홈 페이지로 드래그하여 놓습니다.

   ![제품 티저(분홍색 테두리 포함)](../assets/style-cif-component/pink-border-product-teaser.png)

   이제 제품 티저가 이전에 만든 CSS 규칙 변경에 따라 밝은 분홍색 테두리를 표시해야 합니다.

## 페이지에서 클라이언트 라이브러리 확인 {#verify-client-libraries}

다음으로 페이지에 클라이언트 라이브러리 포함을 확인합니다.

1. 사이트의 **홈 페이지로** 이동합니다. [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. 페이지 **정보** 메뉴를 선택하고 **게시됨으로 보기를 클릭합니다**.

   ![게시됨으로 보기](../assets/style-cif-component/view-as-published.png)

   게시된 사이트에 나타나는 AEM 작성자 javascript가 로드되지 않은 페이지가 열립니다. url에 쿼리 매개 변수가 `?wcmmode=disabled` 추가되어 있습니다. CSS 및 Javascript를 개발할 때는 이 매개 변수를 사용하여 AEM 작성자의 어떤 것이든 사용하여 페이지를 단순화하는 것이 좋습니다.

1. 페이지 소스를 보면 몇 개의 클라이언트 라이브러리가 포함되어 있는지 확인할 수 있습니다.

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-site.min.css" type="text/css">
   </head>
   ...
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/core/wcm/components/commons/site/clientlibs/container.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-base.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/common.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-cif.min.js"></script>
   </body>
   </html>
   ```

   페이지로 배달될 때 클라이언트 라이브러리는 사전 `/etc.clientlibs` 고정되어 [프록시를 통해](/help/implementing/developing/introduction/clientlibs.md) 제공되므로 `/apps` 또는 `/libs`에서 민감한 내용이 노출되지 않습니다.

   알림 `venia/clientlibs/clientlib-site.min.css` 및 `venia/clientlibs/clientlib-site.min.js`Adobe 이러한 파일은 `ui.frontend` 모듈에서 파생된 컴파일된 CSS 및 Javascript 파일입니다.

## 페이지 템플릿과 함께 클라이언트 라이브러리 포함 {#client-library-inclusion-pagetemplates}

클라이언트측 라이브러리를 포함하는 방법에는 몇 가지 옵션이 있습니다. 그런 다음 페이지 템플릿을 통해 생성된 프로젝트에 `clientlib-site` 라이브러리가 포함되어 있는지 [확인합니다](https://docs.adobe.com/content/help/en/experience-manager-65/developing/platform/templates/page-templates-editable.html).

1. AEM Editor 내에서 **사이트의 홈 페이지로** 이동합니다. [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. 페이지 **정보** 메뉴를 선택하고 템플릿 **편집을 클릭합니다**.

   ![템플릿 편집](../assets/style-cif-component/edit-template.png)

   그러면 **홈** 페이지가 기반으로 하는 랜딩 페이지 **** 템플릿이열립니다.

   >[!NOTE]
   >
   > AEM 시작 화면에서 사용 가능한 모든 템플릿을 보려면 **도구** > **일반** > **템플릿으로**&#x200B;이동합니다.

1. 왼쪽 위 모서리에서 **페이지 정보** 아이콘을 선택하고 **페이지 정책을 클릭합니다**.

   ![페이지 정책 메뉴 항목](../assets/style-cif-component/page-policy-menu.png)

1. 랜딩 페이지 템플릿에 대한 페이지 정책이 열립니다.

   ![페이지 정책 - 랜딩 페이지](../assets/style-cif-component/page-policy-properties.png)

   오른쪽에는 이 템플릿을 사용하는 모든 페이지에 포함될 클라이언트 라이브러리 **카테고리** 목록이 표시됩니다.

   * `venia.dependencies` - 사용하는 모든 공급업체 라이브러리를 `venia.site` 제공합니다.
   * `venia.site` - 모듈 `clientlib-site` 이 생성하는 `ui.frontend` 카테고리입니다.

   다른 템플릿은 동일한 정책, **컨텐츠 페이지**, **랜딩 페이지**&#x200B;등을 사용합니다.동일한 정책을 다시 사용하면 동일한 클라이언트 라이브러리가 모든 페이지에 포함되도록 할 수 있습니다.

   템플릿 및 페이지 정책을 사용하여 클라이언트 라이브러리 포함을 관리할 수 있는 이점은 템플릿별 정책을 변경할 수 있다는 것입니다. 예를 들어 동일한 AEM 인스턴스 내에서 두 개의 다른 브랜드를 관리하는 경우가 있습니다. 각 브랜드는 고유한 스타일 또는 *테마를* 가지지만 기본 라이브러리와 코드는 동일합니다. 또 다른 예로, 특정 페이지에만 표시하고 싶은 더 큰 클라이언트 라이브러리가 있는 경우 해당 템플릿에 대해서만 고유한 페이지 정책을 만들 수 있습니다.

## 로컬 웹 팩 개발 {#local-webpack-development}

이전 연습에서는 모듈의 Sass 파일에 대한 업데이트를 `ui.frontend` 수행한 다음 Maven 빌드를 수행한 후 변경 사항이 AEM에 배포되었습니다. 다음으로 프런트 엔드 스타일을 신속하게 개발할 수 있는 웹 팩 개발 서버를 활용합니다.

webpack-dev-server는 AEM의 로컬 인스턴스에서 이미지 및 일부 CSS/JavaScript를 프록시하지만 개발자는 모듈에서 스타일과 JavaScript를 수정할 수 `ui.frontend` 있습니다.

1. 브라우저에서 **홈** 페이지 및 게시됨으로 **보기**&#x200B;로 이동합니다. [http://localhost:4502/content/venia/us/en.html?wcmmode=disabled](http://localhost:4502/content/venia/us/en.html?wcmmode=disabled).

1. 페이지의 소스를 보고 페이지의 원시 HTML을 **복사합니다** .

1. 모듈 아래의 원하는 IDE로 돌아가 파일을 `ui.frontend` 엽니다. `ui.frontend/src/main/static/index.html`

   ![정적 HTML 파일](../assets/style-cif-component/static-index-html.png)

1. 컨텐츠를 덮어쓰고 이전 단계 `index.html` 에 복사한 HTML을 **붙여** 넣습니다.

1. 포함을 찾아 `clientlib-site.min.css``clientlib-site.min.js`**제거합니다** .

   ```html
   <head>
       <!-- remove this link -->
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       ...
   </head>
   <body>
       ...
        <!-- remove this link -->
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
   </body>
   ```

   이러한 CSS 및 JavaScript는 `ui.frontend` 모듈에서 생성된 컴파일된 버전을 나타내므로 제거됩니다. 다른 클라이언트 라이브러리는 실행 중인 AEM 인스턴스에서 프록시됩니다.

1. 새 터미널 창을 열고 `ui.frontend` 폴더로 이동합니다. 명령을 실행합니다 `npm start`.

   ```shell
   $ cd ui.frontend
   $ npm start
   ```

   http://localhost:8080/에서 webpack-dev-server가 [시작됩니다.](http://localhost:8080/)

   >[!CAUTION]
   >
   > Sass 관련 오류가 발생하는 경우 서버를 중지하고 명령을 실행하고 위 단계 `npm rebuild node-sass` 를 반복합니다. 이 문제는 다른 버전의 `npm` 가 있는 `node` 후 프로젝트에 지정된 경우에 발생할 수 있습니다 `aem-cif-guides-venia/pom.xml`.

1. 로그인한 AEM의 [인스턴스와 동일한 브라우저가 있는 새 탭의 http://localhost:8080/](http://localhost:8080/) 디렉토리로 이동합니다. webpack-dev-server를 통해 Venia 홈 페이지가 표시됩니다.

   ![포트 80의 Webpack 개발 서버](../assets/style-cif-component/webpack-dev-server-port80.png)

   webpack-dev-server를 실행합니다. 다음 연습에서는 사용할 것입니다.

## 제품 티저에 대한 카드 스타일 구현 {#update-css-product-teaser}

그런 다음 `ui.frontend` 모듈의 Sass 파일을 수정하여 제품 Teaser에 대한 카드 스타일 스타일을 구현합니다. webpack-dev-server는 변경 사항을 신속하게 확인하는 데 사용됩니다.

IDE 및 생성된 프로젝트로 돌아갑니다.

1. ui. **frontend** 모듈에서 파일을 다시 `_productteaser.scss` 엽니다 `ui.frontend/src/main/styles/commerce/_productteaser.scss`.

1. 제품 티저 테두리를 다음과 같이 변경합니다.

   ```diff
       .item__image {
   -       border: #ea00ff 8px solid;
   +       border-bottom: 1px solid #c0c0c0;
           display: block;
           grid-area: main;
           height: auto;
           opacity: 1;
           transition-duration: 512ms;
           transition-property: opacity, visibility;
           transition-timing-function: ease-out;
           visibility: visible;
           width: 100%;
       }
   ```

   변경 내용을 저장하고 webpack-dev-server는 새 스타일을 사용하여 자동으로 새로 고칩니다.

1. 그림자 효과를 추가하고 제품 티저에 둥근 모서리를 포함합니다.

   ```scss
    .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

1. Teaser 하단에 표시되는 제품 이름을 업데이트하고 텍스트 색상을 수정합니다.

   ```css
   .item__name {
       color: #000;
       display: block;
       float: left;
       font-size: 22px;
       font-weight: 900;
       line-height: 1em;
       padding: 0.75em;
       text-transform: uppercase;
       width: 75%;
   }
   ```

1. Teaser 아래쪽에 표시되는 제품 가격을 업데이트하고 텍스트 색상을 수정합니다.

   ```css
   .price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   
       ...
   ```

1. 맨 아래에 있는 미디어 쿼리를 업데이트하여 이름과 가격을 **992px보다 작은 화면으로 스택할 수 있습니다**.

   ```css
   @media (max-width: 992px) {
       .productteaser .item__name {
           font-size: 18px;
           width: 100%;
       }
       .productteaser .item__price {
           font-size: 14px;
           width: 100%;
       }
   }
   ```

   이제 webpack-dev-server에 반영된 카드 스타일이 표시됩니다.

   ![Webpack Dev Server Teaser 변경](../assets/style-cif-component/webpack-dev-server-teaser-changes.png)

   그러나 변경 사항은 아직 AEM에 배포되지 않았습니다. 여기에서 [솔루션 파일을 다운로드할 수 있습니다](../assets/style-cif-component/_productteaser.scss).

1. 명령줄 터미널에서 Maven 기술을 사용하여 AEM에 업데이트를 배포합니다.

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

   >[!NOTE]
   >전체 Maven 빌드를 수행하지 않고도 프로젝트 파일을 로컬 AEM 인스턴스에 직접 동기화할 수 있는 추가 [IDE 설정](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) 및 도구가 있습니다.

## 업데이트된 제품 티저 보기 {#view-updated-product-teaser}

프로젝트의 코드가 AEM에 배포된 후 제품 티저에 대한 변경 사항을 볼 수 있어야 합니다.

1. 브라우저로 돌아가서 홈 페이지를 다시 새로 고칩니다. [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html). 업데이트된 제품 티저 스타일이 적용된 것을 확인할 수 있습니다.

   ![업데이트된 제품 티저 스타일](../assets/style-cif-component/product-teaser-new-style.png)

1. 추가 제품 티저를 추가하여 실험해 보십시오. 여러 티저를 한 행에 표시하려면 레이아웃 모드를 사용하여 구성 요소의 너비와 오프셋을 변경합니다.

   ![여러 제품 티저](../assets/style-cif-component/multiple-teasers-final.png)

## 문제 해결 {#troubleshooting}

CRXDE- [Lite에서](http://localhost:4502/crx/de/index.jsp) 업데이트된 CSS 파일이 배포되었는지 확인할 수 있습니다. [http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css](http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css)

새 CSS 및/또는 JavaScript 파일을 배포할 때는 브라우저가 부실 파일을 제공하지 않는지 확인하는 것도 중요합니다. 브라우저 캐시를 지우거나 새 브라우저 세션을 시작하여 이 과정을 제거할 수 있습니다.

또한 AEM은 성능을 위해 클라이언트 라이브러리를 캐시하려고 합니다. 가끔 코드 배포 후 이전 파일이 제공됩니다. 클라이언트 라이브러리 다시 [작성 도구를 사용하여 AEM 클라이언트 라이브러리 캐시를 수동으로 무효화할 수 있습니다](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html). *Invalidate Caches는 AEM에서 클라이언트 라이브러리의 이전 버전을 캐시했다고 의심하는 경우 선호하는 방법입니다. 라이브러리 재구축은 비효율적이며 시간이 많이 소요됩니다.*

## 축하합니다 {#congratulations}

첫 번째 AEM CIF 코어 구성 요소를 스타일이 적용되었으며 웹팩 개발 서버를 사용했습니다.

## 보너스 챌린지 {#bonus-challenge}

AEM [스타일 시스템을](https://docs.adobe.com/content/help/en/experience-manager-65/developing/components/style-system.html) 사용하여 내용 작성자가 설정/해제할 수 있는 두 가지 스타일을 만들 수 있습니다. [스타일 시스템을](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html) 사용한 개발 과정에는 이를 수행하는 방법에 대한 자세한 단계와 정보가 포함되어 있습니다.

![보너스 챌린지 - 스타일 시스템](../assets/style-cif-component/bonus-challenge.png)

## 추가 리소스 {#additional-resources}

* [AEM 프로젝트 전형](https://github.com/adobe/aem-project-archetype)
* [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)
* [로컬 AEM 개발 환경 설정](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html)
* [클라이언트측 라이브러리](/help/implementing/developing/introduction/clientlibs.md)
* [AEM Sites 시작하기](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
* [스타일 시스템을 사용한 개발](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html)
