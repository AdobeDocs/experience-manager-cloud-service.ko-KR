---
title: CIF 핵심 구성 요소 사용자 정의
description: CIF 핵심 구성 요소 사용자 정의
translation-type: tm+mt
source-git-commit: c3cf472f5e207e7ca0788dc3e42105868d9bdf00
workflow-type: tm+mt
source-wordcount: '2520'
ht-degree: 1%

---


# AEM CIF 핵심 구성 요소 사용자 정의 {#customize-cif-components}

[AEM CIF 핵심 구성 요소는](https://github.com/adobe/aem-core-cif-components) Adobe Experience Manager(AEM)과 Magento 솔루션을 통합하는 프로젝트를 가속화하는 데 사용할 수 있는 표준 상거래 구성 요소 집합을 제공합니다. 이러한 구성 요소는 바로 제작할 수 있으며 CSS로 [쉽게 스타일을 지정할 수 있습니다](style-cif-component.md). 많은 구현은 또한 이러한 구성 요소를 확장하여 비즈니스별 요구 사항을 충족하려고 합니다.

이 자습서에서는 AEM CIF 핵심 구성 요소 및 AEM에서 제공하는 다양한 익스텐션 포인트를 전반적으로 살펴봅니다. 이렇게 하려면 &quot;새로운&quot; 배너를 렌더링하는 기능을 포함하도록 [제품 티저](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) 구성 요소의 기능을 확장합니다. 컨텐츠 작성자는 이 배너를 전환하고 배너를 표시하는 시간을 결정할 수 있습니다. 제품의 &quot;연령&quot;은 Magento 카탈로그의 작성 날짜를 기준으로 합니다. 특정 기간이 경과한 제품은 &quot;새로운&quot; 배너가 자동으로 사라집니다.

![새 배너 확장](/help/commerce-cloud/assets/customize-cif-components/new-banner-productteaser.png)

## 전제 조건 {#prerequisites}

다음 도구 및 기술이 필요합니다.

* [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html)
* [Apache Maven](https://maven.apache.org/) (3.3.9 이상)
* [AEM Cloud SDK(CIF Add-on 포함)](../develop.md)
* CIF 코어 구성 요소와 호환되는 Magento

이 자습서를 진행하기 전에 다음 내용을 검토하는 것이 좋습니다.

* [AEM에서 Cloud Service으로 커머스 통합 프레임워크 소개](/help/commerce-cloud/overview.md)
* [AEM CIF 핵심 구성 요소 스타일 지정 - 자습서](style-cif-component.md)

## 스타터 프로젝트

이 튜토리얼에서 사용할 시작 프로젝트를 제공했습니다. 이 프로젝트는 CIF 프로젝트 원형의 [v0.7.0을](https://github.com/adobe/aem-cif-project-archetype/releases/tag/cif-project-archetype-0.7.0) 사용하여 생성되었습니다. 새로운 프로젝트를 시작할 때 원형의 [최신 릴리스](https://github.com/adobe/aem-cif-project-archetype/releases/latest) 를 항상 사용하는 것이 가장 좋은 방법입니다.

1. 시작 프로젝트 [**acme-store.zip **](/help/commerce-cloud/assets/customize-cif-components/acme-store.zip)파일을 데스크탑에 다운로드합니다.

1. acme-store.zip의 압축을 **해제하면** 다음 폴더 구조가 표시됩니다.

   ```plain
   /acme-store
      /ui.content
      /ui.apps
      /samplecontent
      /core
      /all
      + pom.xml
      + README.md
   ```

1. 새 터미널 창을 열고 프로젝트를 구축하여 AEM의 로컬 인스턴스에 배포합니다.

   ```shell
   $ cd acme-store/
   $ mvn clean install -PautoInstallAll
   ```

1. AEM 인스턴스를 Magento 인스턴스에 연결하거나 구성을 새로 만든 프로젝트에 추가하려면 필요한 OSGi 구성을 추가하십시오.

1. 이때 Magento 인스턴스에 연결된 스토어프런트 작업 버전이 있어야 합니다. 다음 위치에서 `US` > `Home` 페이지로 이동합니다. [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

   당신은 현재 매점이 베니아 테마를 사용하고 있다는 것을 보아야 합니다. 스토어프런트의 기본 메뉴를 확장하면 연결 Magento이 작동하는지 나타내는 다양한 카테고리가 표시됩니다.

   ![Venia 테마를 사용하여 구성된 스토어](/help/commerce-cloud/assets/customize-cif-components/acme-store-configured.png)

## 제품 티저 작성 {#author-product-teaser}

이 자습서 전반에서 제품 티저 구성 요소를 확장합니다. 첫 번째 단계에서는 기준 기능을 이해하기 위해 제품 티저의 새 인스턴스를 홈 페이지에 추가합니다.

1. 사이트의 **홈 페이지로** 이동합니다. [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

1. 페이지의 **주 레이아웃 컨테이너에 새** 제품 티저 구성 요소를 삽입합니다.

   ![제품 티저 삽입](/help/commerce-cloud/assets/customize-cif-components/product-teaser-add-component.png)

1. 사이드 패널(아직 전환되지 않은 경우)을 확장하고 자산 파인더 드롭다운을 **제품으로 전환합니다**. 연결된 Magento 인스턴스의 사용 가능한 제품 목록이 표시됩니다. 제품을 선택하고 페이지의 **제품 티저** **** 구성 요소에 끌어다 놓습니다.

   ![드래그 앤 드롭 제품 티저](/help/commerce-cloud/assets/customize-cif-components/drag-drop-product-teaser.png)

   > 참고, 대화 상자를 사용하여 구성 요소를 구성하여 표시된 제품을 구성할 수도 있습니다( *공구 모양 아이콘 클릭* ).

1. 이제 제품 Teaser가 표시되는 제품이 표시됩니다. 제품의 이름과 가격은 표시되는 기본 속성입니다.

   ![제품 티저 - 기본 스타일](/help/commerce-cloud/assets/customize-cif-components/product-teaser-default-style.png)

## 제품 티저 마크업 사용자 정의 {#customize-markup-product-teaser}

AEM 구성 요소의 일반적인 확장 기능은 구성 요소에서 생성한 마크업을 수정하는 것입니다. 이 작업은 구성 요소가 마크업을 렌더링하는 데 사용하는 [HTL](https://docs.adobe.com/content/help/ko-KR/experience-manager-htl/using/overview.html) 스크립트를 재정의하여 수행됩니다. HTML 템플릿 언어(HTL)는 AEM 구성 요소가 작성한 컨텐츠를 기반으로 마크업을 동적으로 렌더링하는 데 사용하는 경량의 템플릿 언어로서 구성 요소를 다시 사용할 수 있도록 합니다. 예를 들어 제품 티저를 여러 번 다시 사용하여 다른 제품을 표시할 수 있습니다.

Adobe에서는 Teaser 상단에 제품이 &quot;New&quot;이며 최근에 카탈로그에 추가되었음을 나타내는 배너를 렌더링하려고 합니다. 구성 요소의 [마크업을](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) 사용자 지정하기 위한 디자인 패턴은 실제로 AEM CIF 핵심 구성 요소뿐만 아니라 모든 AEM 구성 요소에 대한 표준입니다.

원하는 IDE를 사용하여 자습서 시작 부분에 다운로드한 [시작 프로젝트를](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) 엽니다.

1. ui.apps **모듈을** 탐색 및 확장하고 폴더 계층 구조를 다음으로 확장합니다. `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser` 파일을 `.content.xml` 검사합니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="acme"/>
   ```

   상단은 프로젝트에서 제품 티저 구성 요소에 대한 구성 요소 정의입니다. 속성을 확인합니다 `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"`. 프록시 구성 요소를 만드는 [예입니다](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/using.html#create-proxy-components). AEM CIF 핵심 구성 요소의 모든 제품 Teaser HTL 스크립트를 복사하고 붙여넣는 대신, 이 스크립트를 사용하여 모든 기능을 상속할 수 `sling:resourceSuperType` 있습니다.

1. 새 브라우저를 열고 AEM에서 [CRXDE-Lite로](http://localhost:4502/crx/de/index.jsp#/apps/core/cif/components/commerce/productteaser/v1/productteaser) 이동합니다. 트리를 확장하여 다음 아래에서 구성 요소를 `productteaser` 봅니다. `/apps/core/cif/components/commerce/productteaser/v1/productteaser`:

   ![CRXDE Lite 제품 티저](/help/commerce-cloud/assets/customize-cif-components/crxde-productteaser.png)

   제품 티저 구성 요소의 전체 구성 요소 정의입니다.

1. IDE 및 Acme 스토어 프로젝트로 다시 전환합니다. 아래에 명명된 새 파일 `productteaser.html` 을 만듭니다 `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser`.

1. CRXDE-Lite `productteaser.html` 의 컨텐츠를 [복사하여 새로 만든](http://localhost:4502/crx/de/index.jsp#/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html) `productteaser.html` 파일의 Acme-Store 프로젝트에 붙여넣습니다.

   ![제품 티저 html 덮어쓰기](/help/commerce-cloud/assets/customize-cif-components/productteaser-html-overwrite.png)

1. Acme-Store 프로젝트에서 `productteaser.html` 파일을 수정하고 제품 이미지 마크업 위에 배지를 나타내는 새 div를 삽입합니다.

   ```html
   ...
   <div data-sly-test.isvalid="${product.url}" class="item__root" data-cmp-is="productteaser">
       <!-- Add Badge -->
       <div class="item__badge">
           <span>New</span>
       </div>
       <!-- end add badge -->
       <a class="item__images" href=${product.url}>
           <img class="item__image" width="100%" height="100%"
                   src="${product.image}" alt="${product.image}"/>
       </a>
       <a class="item__name" href=${product.url}><span>${product.name}</span></a>
       <div class="item__price">
           <span> ${product.formattedPrice} </span>
       </div>
       <sly data-sly-call="${actionsTpl.actions @ product=product}"></sly>
   </div>
   ```

1. 전문적인 기술을 사용하거나 IDE의 기능을 사용하여 업데이트된 코드를 AEM의 로컬 인스턴스 [에 배포할 수 있습니다](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment).

   ```shell
   $ cd ui.apps
   $ mvn -PautoInstallPackage clean install
   ```

1. 브라우저에서 AEM의 스토어 앞 [의 홈페이지로 돌아갑니다](http://localhost:4502/editor.html/content/acme/us/en.html) . 새로 고치면 구성 요소의 오른쪽 위 모서리에 &quot;새&quot; 배너가 나타납니다.

   ![새 배너 확장](/help/commerce-cloud/assets/customize-cif-components/new-banner-productteaser.png)

   현재 배너가 표시될 때 뒤에 논리가 없습니다. 다음 몇 번 연습에서는 그것을 고칠 것입니다.

   > 배너를 렌더링할 CSS는 시작 프로젝트의 일부로 제공되었으며 다음 위치에서 찾을 수 있습니다. `ui.apps/../apps/acme/clientlibs/theme/components/productteaser/teaser.css`. 자세한 내용은 [스타일 CIF 핵심 구성 요소 자습서를 참조하십시오](style-cif-component.md).

## 제품 티저 대화 상자 사용자 지정 {#customize-dialog-product-teaser}

다음으로 제품 티저 구성 요소의 대화 상자를 사용자 정의하여 작성자가 제품이 &quot;신규&quot;로 간주되는 날짜 범위를 결정하고 배너를 표시해야 하는지 여부를 결정합니다. Acme 스토어 프로젝트의 [일부로 제품 티저의 대화](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-dialogs) 내용을 사용자 정의하여 이 작업을 수행합니다.

1. 원하는 IDE에서 Acme 스토어 프로젝트를 열고 원하는 위치로 이동합니다 `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser`.

1. 폴더 아래에서 `productteaser` 새 폴더를 추가합니다. 이름이 `_cq_dialog`지정됩니다. 새 파일을 `_cq_dialog` 폴더에 추가합니다 `.content.xml`. 이제 다음 파일 구조가 있어야 합니다.

   ```plain
   ../acme
       /components
           /commerce
               /productteaser
                  /_cq_dialog
                     + .content.xml
                  /_cq_template
                  + .content.xml
                  + productteaser.html
   ```

1. 다음 XML `_cq_dialog/.content.xml` 로 업데이트합니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
       xmlns:cq="http://www.day.com/jcr/cq/1.0" 
       xmlns:jcr="http://www.jcp.org/jcr/1.0" 
       xmlns:nt="http://www.jcp.org/jcr/nt/1.0" 
       jcr:primaryType="nt:unstructured" 
       jcr:title="My Product Teaser" 
       sling:resourceType="cq/gui/components/authoring/dialog" 
       trackingFeature="cif-core-components:productteaser:v1">
       <content jcr:primaryType="nt:unstructured" 
           sling:resourceType="granite/ui/components/coral/foundation/container">
           <items jcr:primaryType="nt:unstructured">
               <tabs jcr:primaryType="nt:unstructured" 
                   sling:resourceType="granite/ui/components/coral/foundation/tabs" 
                   maximized="{Boolean}true">
                   <items jcr:primaryType="nt:unstructured">
                       <badge jcr:primaryType="nt:unstructured" 
                           jcr:title="Badge" 
                           sling:resourceType="granite/ui/components/coral/foundation/container" 
                           margin="{Boolean}true">
                           <items jcr:primaryType="nt:unstructured">
                               <columns jcr:primaryType="nt:unstructured" 
                                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns" 
                                   margin="{Boolean}true">
                                   <items jcr:primaryType="nt:unstructured">
                                       <column jcr:primaryType="nt:unstructured" 
                                           sling:resourceType="granite/ui/components/coral/foundation/container">
                                           <items jcr:primaryType="nt:unstructured">
                                               <badge jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/coral/foundation/form/checkbox" 
                                                   text="Display 'New' badge" 
                                                   value="true" 
                                                   uncheckedValue="false" 
                                                   name="./badge" />
                                               <age jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield" 
                                                   fieldDescription="The maximum age in days the 'new' badge should be shown" 
                                                   fieldLabel="Max Product Age" 
                                                   name="./age"
                                                   min="{Long}0" 
                                                   value="10" />
                                               <ageTypeHint jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/foundation/form/hidden" 
                                                   ignoreData="{Boolean}true" 
                                                   name="./age@TypeHint" 
                                                   value="Long" />
                                           </items>
                                       </column>
                                   </items>
                               </columns>
                           </items>
                       </badge>
                   </items>
               </tabs>
           </items>
       </content>
   </jcr:root>
   ```

   위의 새로운 탭 및 단일 숨김 필드의 일부로 2개의 필드를 추가했습니다.

   1. &#39;새로 만들기&#39; 배지 표시 확인란
   2. 최대 제품 기간을 정의하는 숫자 필드
   3. 최대 제품 사용 기간이 길게 저장되도록 숨김 필드(자세한 내용은 [@TypeHint](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) 참조)

   프록시 구성 요소의 일부로 정의된 대화 상자는 Sling 리소스 합병이라고 하는 기능을 사용하여 모든 기존 대화 상자 필드를 [상속합니다](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/sling-resource-merger.html). 따라서 제품 티저에 포함된 기존 필드를 다시 정의할 필요가 없습니다.

1. 배지 `productteaser.html` 를 업데이트하고 `data-sly-test` 배지 `<div>` 에 추가합니다. 사용자가 &quot;true&quot;를 선택한 경우 배지가 렌더링되도록 하는 간단한 테스트가 됩니다.

   ```html
       ...
       <div data-sly-test.isvalid="${product.url}" class="item__root" data-cmp-is="productteaser">
   
           <!--/* add test to see if properties.badge equals true */-->
           <div data-sly-test="${properties.badge == 'true'}" class="item__badge">
               <span>New</span>
           </div>
   ...
   ```

1. IDE의 기능을 사용하거나 전문적인 기술을 사용하여 업데이트된 코드를 AEM의 로컬 인스턴스에 배포합니다.

   ```shell
   $ cd ui.apps
   $ mvn -PautoInstallPackage clean install
   ```

1. 제품 티저 구성 요소로 돌아가서 *공구 모양* 아이콘을 클릭하여 대화 상자를 엽니다. 이제 두 개의 추가 필드가 있는 **배지** 탭이 표시됩니다. 이러한 필드를 업데이트하면 값이 AEM에 지속됩니다. 확인란을 사용하여 배지 켜기/끄기를 전환할 수 있어야 합니다.

   ![배지 전환](/help/commerce-cloud/assets/customize-cif-components/toggle-badge-checkbox.gif)

   그러면 작성자가 배지가 표시되는 시기를 제어할 수 있습니다. 그러나 **최대 제품 연령**&#x200B;항목에 따라 제품이 하루 중 특정 연령에 도달하면 배지가 자동으로 사라지는 것이 이상적입니다. 이를 위해서는 백엔드 로직을 구현해야 합니다.

## 제품 티저에 대한 Sling 모델 업데이트 {#updating-sling-model-product-teaser}

다음으로 Sling 모델을 구현하여 제품 Teaser의 비즈니스 로직을 확장합니다. [Sling Models](https://sling.apache.org/documentation/bundles/models.html)는 구성 요소에 필요한 비즈니스 로직을 구현하는 주석 기반 &quot;POJOs&quot;(Plain Old Java Objects)입니다. 슬링 모델은 구성 요소의 일부로 HTL 스크립트와 함께 사용됩니다. Sling Models에 대한 [위임](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) 패턴을 따라 기존 제품 Teaser 모델의 일부분을 확장할 수 있습니다.

Sling Models는 Java로 구현되며 생성된 프로젝트의 **핵심** 모듈에서 찾을 수 있습니다.

1. 원하는 IDE에서 Acme Store 프로젝트를 열고 **핵심** 모듈 아래로 이동하여 다음을 수행합니다. `core/src/main/java/com/acme/cif/core/models/MyProductTeaser.java`. **MyProductTeaser.java** 는 CIF ProductTeaser **인터페이스를 확장하는 미리 만들어진 Java 인터페이스입니다** .

1. 다음 위치에 있는 MyProductTeaserImpl. **java** 파일을 엽니다. `core/src/main/java/com/acme/cif/core/models/MyProductTeaserImpl.java`. `MyProductTeaserImpl` 는 인터페이스에 대한 구현 클래스입니다 `MyProductTeaser`.

   Sling Models의 [위임 패턴을 사용하여](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) 속성을 통해 `ProductTeaser` 클래스를 참조할 수 `sling:resourceSuperType` 있습니다.

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   재정의하거나 변경하지 않으려는 모든 방법에 대해, 반환되는 값을 간단히 반환할 수 `ProductTeaser` 있습니다.

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

1. AEM CIF 코어 구성 요소에서 제공하는 추가 확장 지점 중 하나는 특정 제품 속성에 액세스할 수 `AbstractProductRetriever` 있는 것입니다. 다음 메서드를 추가하여 메서드 `AbstractProductRetriever` 에서 해당 메서드를 `init()` 초기화합니다.

   ```java
   import javax.annotation.PostConstruct;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
       ...
       private AbstractProductRetriever productRetriever;
   
       /* add this method to intialize the proudctRetriever */
       @PostConstruct
       public void initModel() {
           productRetriever = productTeaser.getProductRetriever();
   
       }
   ...
   ```

1. 서식이 지정된 가격을 수정하고 다음 로직을 대체하여 이러한 변경 사항을 테스트할 수 있습니다 `getFormattedPrice()`. 다음 업데이트를 하면 독일어 로케일에 따라 가격을 명시적으로 지정할 수 있습니다. (또는 다른 국가를 선택하십시오!)

   ```java
           import java.util.Locale;
           import java.text.NumberFormat;
            ...
   
               @Override
                   public String getFormattedPrice() 
                   {
                   //return productTeaser.getFormattedPrice();
                   NumberFormat germanCurrencyFormat = NumberFormat.getCurrencyInstance(Locale.GERMANY);
                   Double price =  productRetriever.fetchProduct().getPrice().getRegularPrice().getAmount().getValue();
                       if(price != null) 
                       {
                           return germanCurrencyFormat.format(price);
                       }
                   return null;
                   }
   ```

   개체를 통해 `productRetriever` 메서드를 통해 개체에 `ProductInterface` 액세스할 수 있는 방법을 `fetchProduct()` 확인하십시오. 여기에서 [사용 가능한 모든 방법을 볼 수 있습니다](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java).

   > 참고* 로케일을 독일어로 수정하는 것은 재정의를 보여주는 재미있는 예일 뿐입니다. 실제로 ProductTeaser는 [페이지의 로케일을 사용하여 형식을 결정합니다](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/internal/models/v1/productteaser/ProductTeaserImpl.java#L173).

1. 다음으로 **ui.apps** 모듈에서 productteaser.html을 업데이트하여 다음 위치에서 새로운 Sling 모델을 참조해야 **** 합니다. `com.acme.cif.core.models.MyProductTeaser`.

   ```diff
     <!--/* productteaser.html - change the use.product to point to MyProductTeaser */-->
     <sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html"
   -  data-sly-use.product="com.adobe.cq.commerce.core.components.models.productteaser.ProductTeaser"
   +  data-sly-use.product="com.acme.cif.core.models.MyProductTeaser"
      data-sly-use.actionsTpl="actions.html">
      ...
   ```

   변경 내용을 저장합니다 `productteaser.html`.

1. AEM의 로컬 인스턴스에 코드 베이스를 배포합니다. ui.apps **및** 핵심 **** 모듈 모두 변경되었으므로, 루트에서 프로젝트를 빌드하고 배포합니다.

   ```shell
   $ cd acme-store
   $ mvn -PautoInstallPackage clean install
   ```

1. 브라우저를 열고 다음 위치로 이동합니다. [http://localhost:4502/system/console/status-slingmodels](http://localhost:4502/system/console/status-slingmodels). 이 콘솔에는 시스템에 등록된 모든 Sling 모델이 표시됩니다. MyTeaserModelImpl이 배포되고 올바르게 매핑되었는지 다시 확인하십시오. 다음과 같은 것을 볼 수 있습니다.

   ```plain
   com.acme.cif.core.models.MyProductTeaserImpl - acme/components/commerce/productteaser
   ```

1. 마지막으로 제품 티저 구성 요소를 작성한 위치로 이동하고 이제 독일 통화 형식의 가격을 확인합니다.

   ![가격 포맷 업데이트됨](/help/commerce-cloud/assets/customize-cif-components/german-currency-update.png)

## isShowBadge 논리 구현 {#implement-isshowbadge}

이제 Sling Model 메서드를 재정의하는 방법을 실험해 볼 수 있으므로 &quot;new&quot; 배지 표시 시점의 논리를 구현할 수 있습니다.

1. IDE로 돌아가 다음 위치에서 **MyProductTeaser.java** 파일을 엽니다. `core/src/main/java/com/acme/cif/core/models/MyProductTeaser.java`.

1. 인터페이스에 새 메서드 `isShowBadge()` 를 추가합니다.

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   }
   ```

   이 방식은 배지를 표시할지 여부를 나타내는 논리를 캡슐화하기 위해 도입하고자 합니다.

1. 다음 위치에서 **MyProductTeaserImpl.java** 를 다시 엽니다 `core/src/main/java/com/acme/cif/core/models/MyProductTeaserImpl.java`.

1. &quot;새로운&quot; 배지가 표시되는 기간의 논리는 제품의 `created_at` 속성을 기반으로 합니다. 해당 속성에 액세스하려면 ProductTeaser에서 수행하는 **GraphQL** 쿼리를 확장해야 합니다. 이렇게 하려면 MyProductTeaserImpl.java의 `init()` 방법을 **업데이트하면 됩니다**.

   ```java
   //MyProductTeaserImpl.java
   
   @PostConstruct
   public void initModel() {
       productRetriever = productTeaser.getProductRetriever();
   
       if (productRetriever != null) {
           // Pass your custom partial query to the ProductRetriever. This class will
           // automatically take care of executing your query as soon
           // as you try to access any product property.
           productRetriever.extendProductQueryWith(p ->
               p.addCustomSimpleField("created_at")
           );
       }
   }
   ```

   모델에 `extendProductQueryWith` 추가하면 추가 제품 속성을 모델의 나머지 부분에서 사용할 수 있습니다. 또한 실행된 쿼리 수를 최소화합니다.

   >[!NOTE]
   >위의 코드에서 Adobe는`addCustomSimpleField` 속성을 검색하는 데 `created_at` the 속성을 사용합니다. Magento 스키마의 일부인 사용자 지정 속성을 쿼리하는 방법을 보여 줍니다.
   >
   > 하지만 이 `created_at` 속성은 실제로 [제품 인터페이스](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java) 일부로 구현되었으며 다음과 같은 메서드를 다시 사용하는 것이 좋습니다. `productRetriever.extendProductQueryWith(p -> p.createdAt());`. 일반적으로 발견되는 스키마 속성은 대부분 구현되었으므로 실제 사용자 지정 속성에 대해서만 `addCustomSimpleField` 를 사용합니다.

1. 다음 방법을 `isShowBadge()` 구현합니다.

   ```java
   import java.time.format.DateTimeFormatter;
   import java.util.Locale;
   import java.time.temporal.ChronoUnit;
   
   ...
   
   @Override
   public Boolean isShowBadge() {
        final DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
   
        //Look at the checkbox from the dialog to see if we should even attempt to show the badge
        final boolean showBadge = properties.get("badge", false);
        if (showBadge) {
   
            //Look at the numberfield set from the dialog to determine the max "age" in days to compare too
            final int maxAgeProp = properties.get("age", 0);
   
           String createdAtString;
           try {
               //Grab the created_at property from the product
               //Here we show the example of retrieving the attribute as if it was a custom attribute
               // an alternative that would work is productRetriever.fetchProduct().getCreatedAt()
               createdAtString = productRetriever.fetchProduct().getAsString("created_at");
               log.info("***CREATED_AT**** " + createdAtString);
           } catch (SchemaViolationError e) {
               //it is possible that a schema error could be thrown if the attribute is not part of the schema
               log.error("Error determining to showBadge" , e);
               return false;
           }
   
            // Custom code to calc the date difference of the product creation
            // compared to today
           final LocalDate createdAt = LocalDate.parse(createdAtString, formatter);
            if (createdAt != null) {
   
                final long ageInDays = ChronoUnit.DAYS.between(createdAt, LocalDate.now());
                if (ageInDays < maxAgeProp) {
                    return true;
                }
            }
        }
        return false;
    }
   ```

   위의 방식에서는 우선 작성자가 확인란을 사용하여 배지 기능을 활성화했는지 확인합니다. 그런 다음 대화 상자 `age` 의 일부로 설정되는 속성 값을 읽고 배너가 사라질 때까지 제품이 보유한 최대 기간(일)을 나타냅니다. 마지막으로 우리는 그 제품이 `created_at` 날짜를 기준으로 몇 년인지 계산한다. 두 값을 비교한 후 다시 배지 `true` 를 표시하는 경우, 다른 모든 경우에 `false` 는 됩니다.

1. 마지막으로 메서드를 호출하려면 `productteaser.html` 스크립트에 하나 더 추가해야 `isShowBadge()` 합니다. 에서 파일을 엽니다 `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser/productteaser.html`. 다음 업데이트:

   ```diff
   ...
   - <div data-sly-test="${properties.badge == 'true'}" class="item__badge">
   + <div data-sly-test="${product.showBadge}" class="item__badge">
        <span>New</span>
    </div>
   ...
   ```

1. AEM의 로컬 인스턴스에 코드 베이스를 배포합니다. ui.apps **및** 핵심 **** 모듈 모두 변경되었으므로, 루트에서 프로젝트를 빌드하고 배포합니다.

   ```shell
   $ cd acme-store
   $ mvn -PautoInstallPackage clean install
   ```

1. AEM 및 ProductTeaser 구성 요소로 돌아가 여러 숫자를 실험해 보고 제품의 최대 사용 기간을 표시합니다. 제품의 사용 연한에 따라 배지가 표시될 수 있도록 매우 큰 숫자를 입력해야 할 수도 있습니다.

   ![최대 제품 연령 999](/help/commerce-cloud/assets/customize-cif-components/max-age-working.png)

1. 마지막으로 AEM 로그를 검색하여 위의 5단계에서 입력한 로그 문을 확인합니다. Magento에서 가져오는 `created_at` 속성 값을 인쇄해야 합니다. 파일을 열어 AEM 로그를 볼 수 `error.log` 있습니다. 이 파일은 AEM jar가 설치된 `crx-quickstart/logs/error.log` 곳 아래에 있습니다. 다음과 같은 라인 항목이 표시될 수 있습니다.

   ```plain
   com.acme.cif.core.models.MyProductTeaser ***CREATED_AT**** 2019-06-05 06:51:33
   ```

   이제 우리가 구현한 논리가 올바른지 확인할 수 있습니다.

### 축하합니다 {#congratulations}

첫 번째 AEM CIF 구성 요소를 사용자 정의했습니다! 여기서 [완성된 솔루션 패키지를 다운로드합니다](/help/commerce-cloud/assets/customize-cif-components/acme-store-solution.zip).

## 추가 리소스 {#additional-resources}

* [AEM 원형](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)
* [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)
* [AEM CIF 핵심 구성 요소 사용자 정의](https://github.com/adobe/aem-core-cif-components/wiki/Customizing-CIF-Core-Components)
* [핵심 구성 요소 사용자 정의](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html)
