---
title: AEM CIF 핵심 구성 요소 스타일 지정
description: AEM CIF 핵심 구성 요소 스타일 지정
translation-type: tm+mt
source-git-commit: 48805b21500ff3f2629efd6aecb40bb1cdc38cd6
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 2%

---


# AEM CIF 핵심 구성 요소 스타일 지정 {#style-aem-cif-core-components}

CIF [프로젝트 원형](https://github.com/adobe/aem-cif-project-archetype) 유형은 [AEM CIF 핵심 구성 요소를 사용하는 고객 프로젝트의 시작점으로 최소한의 Adobe Experience Manager(AEM) CIF 프로젝트를 만듭니다](https://github.com/adobe/aem-core-cif-components). Venia 브랜드라고 하는 기본 스타일이 처음에 사이트에 적용됩니다. 이 자습서에서는 원형별로 생성된 새로운 AEM CIF 프로젝트를 검사하고 AEM CIF Core 구성 요소에서 사용되는 CSS 및 JavaScript를 구성하는 방법을 파악합니다. 또한 CSS를 사용하여 제품 티저 구성 요소의 기본 스타일을 대체할 새 스타일을 만듭니다.

![구축 내용](/help/commerce-cloud/assets/style-cif-component/what-you-will-build.png)

>[!NOTE]
> 카드와 유사한 제품 티저 구성 요소에 대해 새 스타일이 구현됩니다.

## 전제 조건 {#prerequisites}

다음 도구 및 기술이 필요합니다.

* [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/index.html) 또는 [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html) (AEM 6.5+만 해당)
* [Apache Maven](https://maven.apache.org/) (3.3.9 이상)
* Adobe Experience Manager(로컬 인스턴스)
   * [AEM 6.5](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/introduction/technical-requirements.html)
   * [AEM 6.4.4+](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/sp-release-notes.html)
* 원형과 호환되는 [버전을 실행하는 Magento](https://github.com/adobe/aem-cif-project-archetype#requirements)

## 프로젝트 생성 {#generate-project}

CIF 프로젝트 원형(CIF Project [Pretype)을 사용하여 새로운 AEM CIF](https://github.com/adobe/aem-cif-project-archetype) 프로젝트를 생성한 다음 기본 스타일을 무시합니다.

**CIF 프로젝트 원형을 기반으로 기존 프로젝트** (CIF Project Tranype)를 자유롭게 사용하고 이 섹션을 건너뜁니다.

1. GitHub에서 최신 릴리스 [를 확인하여 CIF 프로젝트 원형 최신 버전을 결정합니다](https://github.com/adobe/aem-cif-project-archetype/releases/latest). 다음 단계에서 최신 릴리스 `x.y.z` 의 버전으로 대체하십시오.

1. 다음 마비안 명령을 실행하여 [배치 모드에서 새 프로젝트를 생성합니다](https://maven.apache.org/archetype/maven-archetype-plugin/examples/generate-batch.html).

   ```terminal
   mvn archetype:generate -B \
       -DarchetypeGroupId="com.adobe.commerce.cif" \
       -DarchetypeArtifactId="cif-project-archetype" \
       -DarchetypeVersion=x.y.z \
       -DgroupId="com.acme.cif" \
       -DartifactId="acme-store" \
       -Dversion=0.0.1-SNAPSHOT \
       -Dpackage="com.acme.cif" \
       -DappsFolderName="acme" \
       -DartifactName="Acme Store" \
       -DcontentFolderName="acme" \
       -DpackageGroup="acme" \
       -DsiteName="Acme Store" \
       -DoptionAemVersion=6.5.0 \
       -DoptionIncludeExamples=y \
       -DoptionEmbedConnector=y
   ```

1. 프로젝트를 빌드하고 AEM의 로컬 인스턴스에 배포합니다.

   ```shell
   $ cd acme-store/
   $ mvn clean install -PautoInstallAll
   ```

1. AEM 인스턴스를 Magento 인스턴스에 연결하거나 구성을 새로 만든 프로젝트에 추가하려면 필요한 OSGi 구성을 추가하십시오.

1. 이때 Magento 인스턴스에 연결된 스토어프런트 작업 버전이 있어야 합니다. 다음 위치에서 `US` > `Home` 페이지로 이동합니다. [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

   당신은 현재 매점이 베니아 테마를 사용하고 있다는 것을 보아야 합니다. 스토어프런트의 기본 메뉴를 확장하면 연결 Magento이 작동하는지 나타내는 다양한 카테고리가 표시됩니다.

   ![Venia 테마를 사용하여 구성된 스토어](/help/commerce-cloud/assets/style-cif-component/acme-store-configured.png)

## 클라이언트 라이브러리 소개 {#introduction-to-client-libraries}

스토어프런트 테마와 스타일을 렌더링하는 책임이 있는 CSS 및 JavaScript는 [클라이언트 라이브러리](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html) 또는 clientlibs에서 간단하게 관리합니다. 클라이언트 라이브러리는 프로젝트 코드에서 CSS 및 Javascript를 구성한 다음 페이지에 전달하는 메커니즘을 제공합니다.

AEM CIF 핵심 구성 요소에 브랜드 전용 스타일을 적용하는 방법은 이러한 클라이언트 라이브러리에서 관리되는 CSS를 추가하고 재정의하는 것입니다. 클라이언트 라이브러리가 구조화되고 페이지에 포함되는 방법을 이해하는 것이 중요합니다.

### 프로젝트 클라이언트 라이브러리 {#project-client-libraries}

그런 다음 원형에 의해 자동으로 생성된 클라이언트 라이브러리를 검사합니다. 선택한 IDE를 사용하여 이전 연습 [에서 생성된 프로젝트를 가져옵니다](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment).

1. ui.apps **모듈을** 탐색 및 확장하고 폴더 계층 구조를 다음으로 확장합니다. `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs`:

   ![ui.apps clientlibs](/help/commerce-cloud/assets/style-cif-component/ui-apps-clientli-folder.png)

   아래에 clientlib-base **및** 테마 폴더가 두 개 있습니다 ****.

1. **clientlib-base** - [AEM 코어 구성 요소의 필수 종속성을 간단히 제공하는 빈 클라이언트 라이브러리입니다](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html).

   ![Clientlib-base](/help/commerce-cloud/assets/style-cif-component/clientlib-base-folderhierarchy.png)

   다음은 clientlib-base의 XML **정의입니다** ( `.content.xml` 파일).

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:ClientLibraryFolder"
       allowProxy="{Boolean}true"
       categories="[acme.wcm.base]"
       embed="[core.wcm.components.accordion.v1,core.wcm.components.tabs.v1,core.wcm.components.carousel.v1,core.wcm.components.image.v2,core.wcm.components.breadcrumb.v2,core.wcm.components.search.v1,core.wcm.components.form.text.v2]"/>
   ```

   `acme.wcm.base` 은 이 클라이언트 라이브러리의 카테고리입니다. 카테고리를 태그로 생각해 보세요. 페이지에 라이브러리를 포함하거나 포함하는 데 사용됩니다.

   다른 clientlib 카테고리의 `embed` 속성과 배열을 확인합니다. 이러한 각 카테고리는 클라이언트 라이브러리를 나타냅니다. 예를 들어 아코디언 구성 요소 `core.wcm.components.accordion.v1` 가 작동하는 데 필요한 javascript [를](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/accordion.html) 포함합니다.

   관리 `embed` 및 `categories` 속성을 사용하여 다른 프로젝트의 클라이언트 라이브러리를 포함할 수 있습니다.

   `allowProxy=true` 클라이언트 라이브러리 CSS 및 JavaScript가 다음 접두사가 있는 경로에서 제공될 수 있도록 합니다. `/etc.clientlibs`. 이렇게 하면 응용 프로그램 코드가 최종 사용자로부터 보호되지만 웹 사이트가 작동하는 데 필요한 CSS 및 JavaScript는 익명으로 제공할 수 있습니다. `/apps` allowProxy [속성에 대한 자세한 내용은 여기에서 확인할 수 있습니다](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet).

1. **테마** - CIF 프로젝트에 대한 시작 테마와 CSS가 포함된 클라이언트 라이브러리입니다. 이 클라이언트 라이브러리는 각 구현에 의해 사용자 지정되도록 디자인되었으며, 구성 요소가 제대로 작동하도록 일부 기존 스타일로 시작하는 것이 유용합니다.

   ![테마 클라이언트 라이브러리](/help/commerce-cloud/assets/style-cif-component/clientlib-theme-folder-hierarchy.png)

   다음은 **테마** XML 정의입니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:ClientLibraryFolder"
       allowProxy="{Boolean}true"
       categories="[acme.theme]"/>
   ```

   `acme.theme` 는 이 클라이언트 라이브러리의 카테고리이며 클라이언트 라이브러리가 페이지에 포함되는 방법입니다.

1. 테마 **클라이언트 라이브러리 아래에** css.txt라는 파일이 **** 있습니다. `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs/theme/css.txt`:

   ```plain
   #base=.
   common/common.css
   
   components/button/button.css
   
   components/featuredcategorylist/categorylist.css
   
   ...
   ```

   **css.txt** (및 **js.txt**)는 최종 CSS 파일에 개별 파일이 포함되는 순서를 지정하는 매니페스트처럼 작동합니다. CSS와 JavaScript의 순서를 지정하는 것이 중요하며 코드를 보다 효과적으로 관리하기 위해 여러 파일을 만들 수 있는 것이 좋습니다. css.txt **** 파일을 보면 스타일이 적용된 구성 요소에 의해 파일이 정리되어 있음을 알 수 있습니다.

1. CSS 파일을 **테마/구성 요소** 아래에 추가하여 ootb 구성 요소 스타일에 대한 아이디어를 얻을 수 있습니다. 이러한 파일 중 일부는 튜토리얼에서 나중에 업데이트할 예정입니다.

### 기본 페이지 구성 요소를 사용한 클라이언트 라이브러리 포함

다음으로 HTL 및 페이지 구성 요소를 사용하여 클라이언트 라이브러리가 페이지에 어떻게 포함되어 있는지 [](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#using-htl) 검사합니다.

1. ui.apps **모듈에서 다음** 아래의 `page` 구성 요소 정의로 이동합니다. `ui.apps/src/main/content/jcr_root/apps/acme/components/structure/page`. 원형 유형에 의해 생성된 이 **페이지** 구성 요소는 프로젝트의 모든 페이지를 렌더링하는 데 사용되는 시작 지점입니다.

1. 페이지 구성 요소의 정의( **)를** 검사하면`page/.content.xml`가리키는 속성 `sling:resourceSuperType` 이 `core/cif/components/structure/page/v1/page`표시됩니다. 즉, 프로젝트의 (Acme) **페이지** 구성 요소는 [CIF 코어 페이지](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/structure/page/v1/page) 구성 요소의 모든 기능을 상속하므로 더 적은 코드를 관리할 수 있습니다.

1. 페이지 **구성 요소** 아래에서 두 개의 파일을 찾을 수 있습니다. **customerlibs.html** 및 **customfooterlibs.html**.

   ```html
   <!--/* customheaderlibs.html */-->
   <sly data-sly-use.clientLib="/libs/granite/sightly/templates/clientlib.html"
    data-sly-call="${clientlib.css @ categories='acme.wcm.base'}"/>
   ```

   **customerlibs.html** 은 페이지의 헤드에서 렌더링되는 HTL 스크립트입니다. 프로젝트별 로직을 재정의하고 추가하는 일반적인 스크립트입니다. 이 경우 카테고리가 있는 클라이언트 라이브러리를 포함하기 위해 사용합니다 `acme.wcm.base`. 웹 개발 우수 사례를 따르자면 페이지 맨 앞에만 CSS가 포함되어 있습니다.

   ```html
   <!--/* customfooterlibs.html */-->
   <sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
       <sly data-sly-call="${clientlib.js @ categories='acme.wcm.base'}"/>
   </sly>
   ```

   **customfoterlibs.html** 은 닫는 `</body>` 태그 바로 앞에서 페이지 하단에 렌더링되는 HTL 스크립트입니다. 카테고리가 `acme.wcm.base` 다시 사용되지만 이번에는 클라이언트 라이브러리의 JavaScript만 로드됩니다.

페이지 구성 요소의 HTL 스크립트 **수정은 모든 페이지에** `acme.wcm.base` 포함되는 방법입니다. 하지만 어떻게 `acme.theme`하죠? 다음 연습에서는 클라이언트 라이브러리를 포함하는 다른 옵션을 살펴봅니다.

### 페이지 템플릿과 함께 클라이언트 라이브러리 포함 {#client-library-inclusion-pagetemplates}

클라이언트측 라이브러리를 포함하는 방법에는 몇 가지 옵션이 있습니다. 다음으로 생성된 프로젝트에 [페이지 템플릿을 통해 테마 클라이언트측 라이브러리가 포함된 방법을 검사합니다](https://docs.adobe.com/content/help/en/experience-manager-65/developing/platform/templates/page-templates-editable.html).

이 자습서를 시작할 때 새 브라우저를 열고 프로젝트를 배포한 AEM 인스턴스에 로그인합니다.

1. AEM 시작 화면에서 **도구** > **일반** > 템플릿 **으로 이동합니다**.

   ![템플릿 탐색](/help/commerce-cloud/assets/style-cif-component/template-location.png)

1. Acme 스토어 **구성 폴더로** 이동합니다. **연필** 아이콘을 선택하여 카테고리 페이지 템플릿을 ** 엽니다.

   ![범주 페이지 템플릿 카드](/help/commerce-cloud/assets/style-cif-component/category-page-template.png)

1. 왼쪽 위 모서리에서 **페이지 정보** 아이콘을 선택하고 **페이지 정책을 클릭합니다**.

   ![페이지 정책 메뉴 항목](/help/commerce-cloud/assets/style-cif-component/page-policy-menu.png)

1. 카탈로그 페이지 템플릿에 대한 페이지 정책이 열립니다.

   ![페이지 정책 - 카탈로그 페이지](/help/commerce-cloud/assets/style-cif-component/page-policy-properties.png)

   오른쪽에는 이 템플릿을 사용하는 모든 페이지에 포함될 클라이언트 라이브러리 **카테고리** 목록이 표시됩니다.

   * **wcm.foundation.components.page.responsive** - 작성자가 [응답형 레이아웃](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/siteandpage/responsive-layout.html) 컨트롤을 사용하는 데 필요한 CSS를 제공합니다.
   * **acme.theme** - 원형이 자동으로 생성하는 시작 테마입니다. 기본적으로 이 스타일이 샘플 Venia 데모 스토어처럼 지정됩니다. 하지만 이름에서 알 수 있듯이 프로젝트 구현에 의해 사용자 지정되도록 합니다. *다음은 다음 섹션에서 수정할 사항입니다.*
   * **core.cif.components.react** - 장바구니와 같은 동적 기능에 사용되는 여러 React 구성 요소의 컴파일된 클라이언트 라이브러리입니다. 자세한 [내용은 여기를 참조하십시오](https://github.com/adobe/aem-core-cif-components/tree/master/react-components).

   다른 템플릿은 동일한 정책, **컨텐츠 페이지**, **랜딩 페이지**&#x200B;등을 사용합니다. 동일한 정책을 다시 사용하면 동일한 클라이언트 라이브러리가 모든 페이지에 포함되도록 할 수 있습니다.

   템플릿 및 페이지 정책을 사용하여 클라이언트 라이브러리 포함을 관리할 수 있는 이점은 템플릿별 정책을 변경할 수 있다는 것입니다. 예를 들어 동일한 AEM 인스턴스 내에서 두 개의 다른 브랜드를 관리하는 경우가 있습니다. 각 브랜드는 고유한 스타일 또는 *테마를* 가지지만 기본 라이브러리와 코드는 동일합니다. 또 다른 예로, 특정 페이지에만 표시하고 싶은 더 큰 클라이언트 라이브러리가 있는 경우 해당 템플릿에 대해서만 고유한 페이지 정책을 만들 수 있습니다. 다른 이점

### 페이지에서 클라이언트 라이브러리 확인 {#verify-client-libraries}

이 시점에서 HTL을 사용하는 클라이언트 라이브러리를 **customerlibs.html** 및 **customfoterlibs.html** 스크립트와 함께 포함하는 방법과 템플릿의 페이지 정책을 사용하여 추가 클라이언트 라이브러리를 포함할 수 있는 방법을 검토했습니다. 다음으로 사이트에 클라이언트 라이브러리 포함을 확인합니다.

1. AEM Start 화면에서 **Sites** > **Acme Store** > **미국****>** 영어English로 이동하여 편집할 페이지를 엽니다. [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html).

1. 페이지 **정보** 메뉴를 선택하고 **게시됨으로 보기를 클릭합니다**.

   ![게시됨으로 보기](/help/commerce-cloud/assets/style-cif-component/view-as-published.png)

   게시된 사이트에 나타나는 AEM 작성자 javascript가 로드되지 않은 페이지가 열립니다. url에 쿼리 매개 변수가 `?wcmmode=disabled` 추가되어 있습니다. CSS 및 Javascript를 개발할 때는 이 매개 변수를 사용하여 AEM 작성자의 어떤 것이든 사용하여 페이지를 단순화하는 것이 좋습니다.

1. 페이지 소스를 보면 다음 클라이언트 라이브러리가 포함되어 있는지 확인할 수 있습니다. **acme.wcm.base**, **wcm.foundation.components.page.responsive**, **acme.theme**, **core.cif.components.react**

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/acme/clientlibs/clientlib-base.css" type="text/css">
       <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/acme/clientlibs/theme.css" type="text/css">
   </head>
   ...
   
       <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/react-components.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/acme/clientlibs/clientlib-base.js"></script>
   </body>
   </html>
   ```

## 제품 티저 스타일 지정 {#style-product-teaser}

원형에 의해 생성된 클라이언트 라이브러리 구조를 이해하게 되면서 AEM CIF 핵심 구성 요소를 사용자 정의할 수 있게 되었습니다. 제품 Teaser 구성 요소의 스타일을 수정하여 &quot;카드&quot;처럼 보이도록 합니다.

### 제품 티저 작성 {#author-product-teaser}

첫 번째 단계로, AEM 제작 도구를 사용하여 사이트의 홈 페이지에 제품 티저 구성 요소의 새 인스턴스를 추가합니다.

1. 새 브라우저 탭을 열고 사이트의 **홈 페이지로** 이동합니다. [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html).

1. 페이지의 **주 레이아웃 컨테이너에 새** 제품 티저 구성 요소를 삽입합니다.

   ![제품 티저 삽입](/help/commerce-cloud/assets/style-cif-component/product-teaser-add-component.png)

1. 사이드 패널(아직 전환되지 않은 경우)을 확장하고 자산 파인더 드롭다운을 **제품으로 전환합니다**. 연결된 Magento 인스턴스의 사용 가능한 제품 목록이 표시됩니다. 제품을 선택하고 페이지의 **제품 티저** **** 구성 요소에 끌어다 놓습니다.

   ![드래그 앤 드롭 제품 티저](/help/commerce-cloud/assets/style-cif-component/drag-drop-product-teaser.png)

   > 참고, 대화 상자를 사용하여 구성 요소를 구성하여 표시된 제품을 구성할 수도 있습니다( *공구 모양 아이콘 클릭* ).

1. 이제 제품 Teaser가 표시되는 제품이 표시됩니다. 제품의 이름과 가격은 표시되는 기본 속성입니다.

   ![제품 티저 - 기본 스타일](/help/commerce-cloud/assets/style-cif-component/product-teaser-default-style.png)

### 제품 티저에 대한 CSS 업데이트 {#update-css-product-teaser}

다음으로 제품 Teaser에 대한 카드 **스타일의 스타일을 구현하기 위해** 테마 클라이언트 라이브러리의 CSS를 수정합니다.

IDE 및 생성된 프로젝트로 돌아갑니다.

1. ui.apps **** 모듈에서 폴더로 이동합니다. `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs/theme/components/productteaser`. 여기에서 제품 티저에 대한 모든 스타일이 정의됩니다.

1. 파일 **teaser.css** 를 열고 해당 CSS 규칙을 업데이트합니다(또는 [솔루션 teaser.css 파일](/help/commerce-cloud/assets/style-cif-component/solution-teaser.css) 다운로드 및 바꾸기).

   그림자 효과를 추가하고 제품 티저에 둥근 모서리를 포함합니다.

   ```css
    .productteaser .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .productteaser .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

   제품 티저의 이미지 테두리를 변경합니다.

   ```css
   .productteaser .item__image {
       border-bottom: 1px solid #c0c0c0;
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

   Teaser 하단에 표시되는 제품 이름을 업데이트하고 텍스트 색상을 수정합니다.

   ```css
   .productteaser .item__name {
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

   Teaser 아래쪽에 표시되는 제품 가격을 업데이트하고 텍스트 색상을 수정합니다.

   ```css
   .productteaser .item__price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   }
   ```

   맨 아래에 있는 미디어 쿼리를 업데이트하여 992px 보다 작은 화면으로 이름과 가격을 스택할 수 있습니다.

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

   Teaser.css에 변경 내용을 **저장합니다**. 여기에서 [솔루션 teaser.css 파일을 다운로드할 수 있습니다](/help/commerce-cloud/assets/style-cif-component/solution-teaser.css).

1. 명령줄 터미널에서 Maven 기술을 사용하여 **ui.apps** 모듈의 업데이트를 AEM에 배포합니다.

   ```shell
           $ cd acme-store/ui.apps/
           $ mvn -PautoInstallPackage clean install
           ...
           saving approx 0 nodes...
           Package imported.
           Package installed in 61ms.
           [INFO] ------------------------------------------------------------------------
           [INFO] BUILD SUCCESS
           [INFO] ------------------------------------------------------------------------
           [INFO] Total time:  6.903 s
           [INFO] Finished at: 2020-02-06T13:21:36-08:00
            [INFO] ------------------------------------------------------------------------
   ```

   >[!NOTE]
   >전체 Maven 빌드를 수행하지 않고도 프로젝트 파일을 로컬 AEM 인스턴스에 직접 동기화할 수 있는 추가 [IDE 설정](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) 및 도구가 있습니다.

### 업데이트된 제품 티저 보기 {#view-updated-product-teaser}

프로젝트의 코드가 AEM에 배포된 후 제품 티저에 대한 변경 사항을 볼 수 있어야 합니다.

1. 브라우저로 돌아가서 홈 페이지를 다시 새로 고칩니다. [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html). 업데이트된 제품 티저 스타일이 적용된 것을 확인할 수 있습니다.

   ![업데이트된 제품 티저 스타일](/help/commerce-cloud/assets/style-cif-component/product-teaser-new-style.png)

1. 추가 제품 티저를 추가하여 실험해 보십시오. 여러 티저를 한 행에 표시하려면 레이아웃 모드를 사용하여 구성 요소의 너비와 오프셋을 변경합니다.

   ![여러 제품 티저](/help/commerce-cloud/assets/style-cif-component/multiple-teasers-final.png)

   >[!NOTE]
   >각 제품 티저에 동일한 스타일이 포함되어 있습니다.

### 문제 해결 {#troubleshooting}

CRXDE- [Lite에서](http://localhost:4502/crx/de/index.jsp) 업데이트된 CSS 파일이 배포되었는지 확인할 수 있습니다. [http://localhost:4502/crx/de/index.jsp#/apps/acme/clientlibs/theme/components/productteaser/teaser.css](http://localhost:4502/crx/de/index.jsp#/apps/acme/clientlibs/theme/components/productteaser/teaser.css)

새 CSS 및/또는 JavaScript 파일을 배포할 때는 브라우저가 부실 파일을 제공하지 않는지 확인하는 것도 중요합니다. 브라우저 캐시를 지우거나 새 브라우저 세션을 시작하여 이 과정을 제거할 수 있습니다.

또한 AEM은 성능을 위해 클라이언트 라이브러리를 캐시하려고 합니다. 가끔 코드 배포 후 이전 파일이 제공됩니다. 클라이언트 라이브러리 다시 [작성 도구를 사용하여 AEM 클라이언트 라이브러리 캐시를 수동으로 무효화할 수 있습니다](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html). *Invalidate Caches는 AEM에서 클라이언트 라이브러리의 이전 버전을 캐시했다고 의심하는 경우 선호하는 방법입니다. 라이브러리 재구축은 비효율적이며 시간이 많이 소요됩니다.*

### 축하합니다 {#congratulations}

첫 번째 AEM CIF 코어 구성 요소를 스타일이 적용되었습니다.

### 보너스 챌린지 {#bonus-challenge}

AEM [스타일 시스템을](https://docs.adobe.com/content/help/en/experience-manager-65/developing/components/style-system.html) 사용하여 내용 작성자가 설정/해제할 수 있는 두 가지 스타일을 만들 수 있습니다. [스타일 시스템을](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html) 사용한 개발 과정에는 이를 수행하는 방법에 대한 자세한 단계와 정보가 포함되어 있습니다.

![보너스 챌린지 - 스타일 시스템](/help/commerce-cloud/assets/style-cif-component/bonus-challenge.png)

## 추가 리소스 {#additional-resources}

* [AEM CIF Tranype](https://github.com/adobe/aem-cif-project-archetype)

* [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)

* [로컬 AEM 개발 환경 설정](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)

* [클라이언트측 라이브러리](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html)
* [AEM Sites 시작하기](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

* [스타일 시스템을 사용한 개발](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html)
