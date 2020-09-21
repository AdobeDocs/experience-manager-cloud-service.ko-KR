---
title: CIF 핵심 구성 요소 사용자 정의
description: AEM CIF 핵심 구성 요소를 사용자 지정하는 방법을 알아봅니다. 이 자습서에서는 비즈니스 특정 요구 사항을 충족하기 위해 CIF 핵심 구성 요소를 안전하게 확장하는 방법을 설명합니다. GraphQL 쿼리를 확장하여 사용자 지정 속성을 반환하고 CIF 코어 구성 요소에 새 속성을 표시하는 방법을 알아봅니다.
sub-product: 커머스
topics: development
version: cloud-service
doc-type: tutorial
activity: develop
audience: developer
kt: 4279
thumbnail: 4279-customize-cif.jpg
translation-type: tm+mt
source-git-commit: a88595f3fab37f4406e607cb104a27de51cdbef6
workflow-type: tm+mt
source-wordcount: '2550'
ht-degree: 1%

---


# AEM CIF 핵심 구성 요소 사용자 정의 {#customize-cif-components}

CIF [Venia](https://github.com/adobe/aem-cif-guides-venia) 프로젝트는 [CIF 코어 구성 요소를 사용하기 위한 참조 코드 베이스입니다](https://github.com/adobe/aem-core-cif-components). 이 자습서에서는 [제품 티저](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) 구성 요소를 확장하여 Magento의 사용자 지정 속성을 표시합니다. AEM과 Magento의 GraphQL 통합과 CIF 핵심 구성 요소에서 제공하는 확장 호크에 대해 자세히 알아보십시오.

>[!TIP]
>
> 직접 상거래 구현을 시작할 때 [AEM 프로젝트](https://github.com/adobe/aem-project-archetype) 원형 유형을 사용하십시오.

## 구축 내용

베니아 브랜드는 최근 지속 가능한 재료를 사용하여 일부 제품을 제조하기 시작했고, 기업은 **친환경** 배지를 제품 티저의 일부로서 보여주고 싶어한다. Magento에 새 사용자 지정 속성이 생성되어 제품이 **친환경** 자료를 사용하는지 여부를 나타냅니다. 이 사용자 지정 속성은 GraphQL 쿼리의 일부로 추가되고 지정된 제품의 제품 티저에 표시됩니다.

![친환경 배지 최종 구현](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## 전제 조건 {#prerequisites}

이 자습서를 완료하려면 로컬 개발 환경이 필요합니다. 여기에는 Magento 인스턴스에 구성 및 연결된 실행 중인 AEM 인스턴스가 포함됩니다. AEM을 Cloud Service SDK로 사용하여 로컬 개발 [을 설정하는 요구 사항과 단계를 검토하십시오](../develop.md). 튜토리얼을 완전히 따르려면 Magento의 제품에 [속성을 추가할 수 있는 권한이](https://docs.magento.com/user-guide/catalog/product-attributes-add.html) 필요합니다.

또한 코드 샘플과 자습서를 실행하려면 GraphiQL [](https://github.com/graphql/graphiql) 또는 브라우저 익스텐션과 같은 GraphQL IDE가 필요합니다. 브라우저 확장 프로그램을 설치하는 경우 요청 헤더를 설정하는 기능이 있는지 확인합니다. Google Chrome에서 [Alt GraphQL 클라이언트](https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja) 기능은 작업을 수행할 수 있는 하나의 확장 기능입니다.

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

   ![Venia 테마를 사용하여 구성된 스토어](../assets/customize-cif-components/venia-store-configured.png)

## 제품 티저 작성 {#author-product-teaser}

제품 티저 구성 요소는 이 자습서 전반에서 확장됩니다. 첫 번째 단계로, 기본 기능을 이해하기 위해 제품 티저의 새 인스턴스를 홈 페이지에 추가합니다.

1. 사이트의 **홈 페이지로** 이동합니다. [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

2. 페이지의 **주 레이아웃 컨테이너에 새** 제품 티저 구성 요소를 삽입합니다.

   ![제품 티저 삽입](../assets/customize-cif-components/product-teaser-add-component.png)

3. 사이드 패널(아직 전환되지 않은 경우)을 확장하고 자산 파인더 드롭다운을 **제품으로 전환합니다**. 연결된 Magento 인스턴스의 사용 가능한 제품 목록이 표시됩니다. 제품을 선택하고 페이지의 **제품 티저** **** 구성 요소에 끌어다 놓습니다.

   ![드래그 앤 드롭 제품 티저](../assets/customize-cif-components/drag-drop-product-teaser.png)

   >[!NOTE]
   >
   > 참고, 대화 상자를 사용하여 구성 요소를 구성하여 표시된 제품을 구성할 수도 있습니다( *공구 모양 아이콘 클릭* ).

4. 이제 제품 Teaser가 표시되는 제품이 표시됩니다. 제품의 이름과 가격은 표시되는 기본 속성입니다.

   ![제품 티저 - 기본 스타일](../assets/customize-cif-components/product-teaser-default-style.png)

## Magento에 사용자 지정 속성 추가 {#add-custom-attribute}

AEM에 표시되는 제품 및 제품 데이터는 Magento에 저장됩니다. 그런 다음 Magento UI를 사용하여 **제품 속성** 세트의 일부로 환경 친화에 대한 새 속성을 추가합니다.

>[!TIP]
>
> 사용자 지정 **예/아니요** 속성이 이미 제품 속성 세트의 일부로 있습니까? 마음껏 사용하고 이 부분은 건너뛰세요.

1. Magento 인스턴스에 로그인합니다.
1. 카탈로그 **> 제품** 으로 **이동합니다**.
1. 검색 필터를 업데이트하여 이전 연습 **에서 Teaser 구성 요소에** 추가될 때 사용한 구성 가능한 제품을 찾습니다. 제품을 편집 모드로 엽니다.

   ![밸리아 제품 검색](../assets/customize-cif-components/search-valeria-product.png)

1. 제품 보기에서 속성 **추가** > 새 속성 **만들기를 클릭합니다**.
1. 다음 값으로 **새 속성** 양식 채우기(다른 값에 대해서는 기본값 유지)

   | 필드 세트 | 필드 레이블 | 값 |
   |-----------|-------------|---------|
   | 속성 | 속성 레이블 | **친환경** |
   | 속성 | 카탈로그 입력 유형 | **예/아니요** |
   | 고급 속성 속성 | 속성 코드 | **eco_friendly** |

   ![새 속성 양식](../assets/customize-cif-components/attribute-new-form.png)

   완료되면 **속성** 저장을 클릭합니다.

1. 제품 아래쪽으로 스크롤하고 속성 **머리글을** 확장합니다. 새로운 **친환경** 필드를 만나보세요 전환을 예로 **전환합니다**.

   ![yes로 전환](../assets/customize-cif-components/eco-friendly-toggle-yes.png)

   **제품에 대한 변경 사항을 저장합니다** .

   >[!TIP]
   >
   > 제품 속성 관리에 대한 자세한 [내용은 Magento 사용자 안내서를 참조하십시오](https://docs.magento.com/user-guide/catalog/attribute-best-practices.html).

1. 시스템 **> 도구** **** > **캐시**&#x200B;관리로이동합니다. 데이터 스키마를 업데이트했으므로 Magento의 일부 캐시 유형을 무효화해야 합니다.
1. 구성 옆에 있는 상자를 **선택하고** 새로 고침을 위한 캐시 유형을 **제출합니다.**

   ![구성 캐시 유형 새로 고침](../assets/customize-cif-components/refresh-configuration-cache-type.png)

   >[!TIP]
   >
   > 캐시 관리에 대한 자세한 [내용은 Magento 사용자 안내서를 참조하십시오](https://docs.magento.com/user-guide/system/cache-management.html).

## GraphQL IDE를 사용하여 속성 확인 {#use-graphql-ide}

AEM 코드로 이동하기 전에 GraphQL IDE를 사용하여 [Magento GraphQL을](https://devdocs.magento.com/guides/v2.4/graphql/) 탐색하는 것이 유용합니다. AEM과의 Magento 통합은 주로 일련의 GraphQL 쿼리를 통해 수행됩니다. GraphQL 질의 이해 및 수정은 CIF 핵심 구성 요소를 확장할 수 있는 주요 방법 중 하나입니다.

그런 다음 GraphQL IDE를 사용하여 속성이 제품 속성 세트에 추가되었는지 `eco_friendly` 확인합니다. 이 자습서의 스크린샷은 Alt GraphQL [클라이언트를 사용하는 것입니다](https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja).

1. GraphQL IDE를 열고 IDE 또는 확장의 URL 막대 `http://<magento-server>/graphql` 에 URL을 입력합니다.
2. 다음 [제품 쿼리를](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) 추가합니다.여기서 `YOUR_SKU` 는 이전 연습 **에서 사용되는 제품의 SKU입니다** .

   ```json
     {
       products(
       filter: { sku: { eq: "YOUR_SKU" } }
       ) {
           items {
           name
           sku
           eco_friendly
           }
       }
   }
   ```

3. 쿼리를 실행하면 다음과 같은 응답을 받게 됩니다.

   ```json
   {
   "data": {
       "products": {
           "items": [
               {
               "name": "Valeria Two-Layer Tank",
               "sku": "VT11",
               "eco_friendly": 1
               }
           ]
           }
       }
   }
   ```

   ![GraphQL 응답 샘플](../assets/customize-cif-components/sample-graphql-query.png)

   Yes 값은 **1** 의 정수입니다 ****. 이 기능은 Java로 GraphQL 쿼리를 작성할 때 유용합니다.

   >[!TIP]
   >
   > GraphQL [Magento에 대한 자세한 설명은 여기를 참조하십시오](https://devdocs.magento.com/guides/v2.4/graphql/index.html).

## 제품 티저에 대한 Sling 모델 업데이트 {#updating-sling-model-product-teaser}

다음으로 Sling 모델을 구현하여 제품 Teaser의 비즈니스 로직을 확장합니다. [Sling Models](https://sling.apache.org/documentation/bundles/models.html)는 구성 요소에 필요한 비즈니스 로직을 구현하는 주석 기반 &quot;POJOs&quot;(Plain Old Java Objects)입니다. 슬링 모델은 구성 요소의 일부로 HTL 스크립트와 함께 사용됩니다. Sling Models에 대한 [위임](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) 패턴을 따라 기존 제품 Teaser 모델의 일부분을 확장할 수 있습니다.

Sling Models는 Java로 구현되며 생성된 프로젝트의 **핵심** 모듈에서 찾을 수 있습니다.

Venia 프로젝트 [를 가져오려면 원하는](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) IDE를 사용하십시오. 사용된 스크린샷은 [Visual Studio 코드 IDE에서 가져온 것입니다](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code).

1. IDE에서 **핵심** 모듈 아래로 탐색하여 다음을 수행합니다. `core/src/main/java/com/venia/core/models/commerce/MyProductTeaser.java`.

   ![핵심 위치 IDE](../assets/customize-cif-components/core-location-ide.png)

   `MyProductTeaser.java` 는 CIF ProductTeaser [인터페이스를 확장하는 Java 인터페이스입니다](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/models/productteaser/ProductTeaser.java) .

   제품이 &quot;새로 만들기&quot;로 간주되는 경우 배지 `isShowBadge()` 를 표시하기 위해 이미 새로운 방법이 추가되었습니다.

1. 인터페이스에 새 메서드 `isEcoFriendly()` 를 추가합니다.

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   
       public Boolean isEcoFriendly();
   }
   ```

   이 방법은 제품의 속성이 `eco_friendly` 예 **또는** 아니요 **로 설정되어 있는지 여부를 나타내는 논리를 캡슐화하는 새로운 방법입니다**.

1. 다음으로, `MyProductTeaserImpl.java` 에서 검사하십시오 `core/src/main/java/com/venia/core/models/commerce/MyProductTeaserImpl.java`.

   Sling Models의 [위임 패턴을 사용하면](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) 속성을 통해 `MyProductTeaserImpl` 모델을 참조할 수 `ProductTeaser` 있습니다 `sling:resourceSuperType` .

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   재정의하거나 변경하지 않으려는 모든 방법에 대해 반환되는 값을 간단히 반환할 수 `ProductTeaser` 있습니다. 예:

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

   따라서 구현이 작성해야 하는 Java 코드의 양이 최소화됩니다.

1. AEM CIF 코어 구성 요소에서 제공하는 추가 확장 지점 중 하나는 특정 제품 속성에 대한 액세스를 제공하는 `AbstractProductRetriever` 것입니다. Inspect `initModel()` 방법:

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
   
           if (productRetriever != null) {
               productRetriever.extendProductQueryWith(p -> p.createdAt());
           }
   
       }
   ...
   ```

   주석을 `@PostConstruct` 사용하면 Sling 모델이 초기화되는 즉시 이 메서드를 호출할 수 있습니다.

   제품 GraphQL 쿼리는 추가 속성을 검색하는 방법을 사용하여 이미 `extendProductQueryWith` 확장되었습니다 `created_at` . 이 속성은 나중에 메서드의 일부로 `isShowBadge()` 사용됩니다.

1. GraphQL 쿼리를 업데이트하여 속성 `eco_friendly` 을 부분 쿼리에 포함합니다.

   ```java
   //MyProductTeaserImpl.java
   
   private static final String ECO_FRIENDLY_ATTRIBUTE = "eco_friendly";
   
   @PostConstruct
   public void initModel() {
       productRetriever = productTeaser.getProductRetriever();
   
       if (productRetriever != null) {
           productRetriever.extendProductQueryWith(p ->
                productRetriever.extendProductQueryWith(p -> p
                   .createdAt()
                   .addCustomSimpleField(ECO_FRIENDLY_ATTRIBUTE)
               );
           );
       }
   }
   ```

   모델에 `extendProductQueryWith` 추가하면 추가 제품 속성을 모델의 나머지 부분에서 사용할 수 있습니다. 또한 실행된 쿼리 수를 최소화합니다.

   위의 코드에서`addCustomSimpleField` 는 속성을 검색하는 데 `eco_friendly` 사용됩니다. Magento 스키마의 일부인 사용자 지정 속성을 쿼리하는 방법을 보여 줍니다.

   >[!NOTE]
   >
   > 이 `createdAt()` 방법은 실제로 [제품 인터페이스의 일부로 구현되었습니다](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java). 일반적으로 발견되는 스키마 속성은 대부분 구현되었으므로 실제 사용자 지정 속성에 대해서만 `addCustomSimpleField` 를 사용합니다.

1. 로거를 추가하여 Java 코드를 디버깅합니다.

   ```java
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
   
   private static final Logger LOGGER = LoggerFactory.getLogger(MyProductTeaserImpl.class);
   ```

1. 다음으로 다음 방법을 `isEcoFriendly()` 구현합니다.

   ```java
   @Override
   public Boolean isEcoFriendly() {
   
       Integer ecoFriendlyValue;
       try {
           ecoFriendlyValue = productRetriever.fetchProduct().getAsInteger(ECO_FRIENDLY_ATTRIBUTE);
           if(ecoFriendlyValue != null && ecoFriendlyValue.equals(Integer.valueOf(1))) {
               LOGGER.info("*** Product is Eco Friendly**");
               return true;
           }
       } catch (SchemaViolationError e) {
           LOGGER.error("Error retrieving eco friendly attribute");
       }
       LOGGER.info("*** Product is not Eco Friendly**");
       return false;
   }
   ```

   위의 메서드에서 는 제품 `productRetriever` 을 가져오는 데 사용되며 `getAsInteger()` 메서드를 사용하여 `eco_friendly` 속성 값을 가져옵니다. 이전에 실행한 GraphQL 질의를 기준으로 `eco_friendly` 속성이 &quot;**예**&quot;로 설정된 경우 예상된 값이 실제로 **1**&#x200B;의 정수임을 알 수 있습니다.

   슬링 모델이 업데이트되었으므로, 모델 슬링(Sling Model)을 기반으로 환경 친화( **Eco Friendly** ) 표시기를 실제로 표시하려면 컴포넌트 마크업을 업데이트해야 합니다.

## 제품 티저 마크업 사용자 정의 {#customize-markup-product-teaser}

AEM 구성 요소의 일반적인 확장 기능은 구성 요소에서 생성한 마크업을 수정하는 것입니다. 이 작업은 구성 요소가 마크업을 렌더링하는 데 사용하는 [HTL](https://docs.adobe.com/content/help/ko-KR/experience-manager-htl/using/overview.html) 스크립트를 재정의하여 수행됩니다. HTML 템플릿 언어(HTL)는 AEM 구성 요소가 작성한 컨텐츠를 기반으로 마크업을 동적으로 렌더링하는 데 사용하는 경량의 템플릿 언어로서 구성 요소를 다시 사용할 수 있도록 합니다. 예를 들어 제품 티저를 여러 번 다시 사용하여 다른 제품을 표시할 수 있습니다.

Adobe에서는 사용자 지정 속성을 기반으로 제품이 &quot;친환경&quot;임을 나타내는 배너를 Teaser 위에 렌더링하려고 합니다. 구성 요소의 [마크업을](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) 사용자 지정하기 위한 디자인 패턴은 실제로 AEM CIF 핵심 구성 요소뿐만 아니라 모든 AEM 구성 요소에 대한 표준입니다.

1. IDE에서 모듈을 탐색 및 확장하고 폴더 계층 구조를 다음으로 `ui.apps` 확장합니다. `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser` 파일을 `.content.xml` 검사합니다.

   ![제품 티저 ui.apps](../assets/customize-cif-components/product-teaser-ui-apps-ide.png)

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="Venia - Commerce"/>
   ```

   상단은 프로젝트에서 제품 티저 구성 요소에 대한 구성 요소 정의입니다. 속성을 확인합니다 `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"`. 프록시 구성 요소를 만드는 [예입니다](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/using.html#create-proxy-components). AEM CIF 핵심 구성 요소의 모든 제품 Teaser HTL 스크립트를 복사하고 붙여넣는 대신, 이 스크립트를 사용하여 모든 기능을 상속할 수 `sling:resourceSuperType` 있습니다.

1. Open the file `productteaser.html`. CIF 제품 Teaser의 `productteaser.html` 파일 [복사본입니다.](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html)

   ```html
   <!--/* productteaser.html */-->
   <sly data-sly-use.product="com.venia.core.models.commerce.MyProductTeaser"
       data-sly-use.templates="core/wcm/components/commons/v1/templates.html"
       data-sly-use.actionsTpl="actions.html"
       data-sly-test.isConfigured="${properties.selection}"
       data-sly-test.hasProduct="${product.url}">
   ```

   Sling Model for `MyProductTeaser` 이 사용되고 변수에 `product` 할당됩니다.

1. 이전 연습 `productteaser.html` 에서 구현된 `isEcoFriendly` 메서드를 호출하려면 수정합니다.

   ```html
   ...
   <div data-sly-test="${isConfigured && hasProduct}" class="item__root" data-cmp-is="productteaser" data-virtual="${product.virtualProduct}">
       <div data-sly-test="${product.showBadge}" class="item__badge">
           <span>${properties.text || 'New'}</span>
       </div>
       <!--/* Insert call to Eco Friendly here */-->
       <div data-sly-test="${product.ecoFriendly}" class="item__eco">
           <span>Eco Friendly</span>
       </div>
   ...
   ```

   HTL에서 Sling Model 메서드를 호출할 때 메서드의 `get` 및 `is` 부분이 떨어지고 첫 번째 문자가 소문자로 바뀝니다. 이렇게 `isShowBadge()` 되면 `.showBadge` 점점 `isEcoFriendly` 늘어납니다 `.ecoFriendly`. 에서 반환되는 부울 값을 기준으로 `.isEcoFriendly()` 해당 값이 표시되는지 `<span>Eco Friendly</span>` 확인합니다.

   기타 `data-sly-test` HTL 블록 문 [에 대한 자세한 내용은 여기를 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-htl/using/htl/block-statements.html#test).

1. 명령줄 터미널에서 Maven 기술을 사용하여 변경 내용을 저장하고 AEM에 업데이트를 배포합니다.

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. 새 브라우저 창을 열고 AEM 및 **OSGi 콘솔** > **상태** > **모델**&#x200B;으로 이동합니다. [http://localhost:4502/system/console/status-slingmodels](http://localhost:4502/system/console/status-slingmodels)

1. 검색하면 `MyProductTeaserImpl` 다음과 같은 선이 표시됩니다.

   ```plain
   com.venia.core.models.commerce.MyProductTeaserImpl - venia/components/commerce/productteaser
   ```

   이는 Sling 모델이 올바르게 배포되고 올바른 구성 요소에 매핑되었음을 나타냅니다.

1. 제품 Teaser가 추가된 http://localhost:4502/editor.html/content/venia/us/en.html **** 의 Venia 홈 페이지 [](http://localhost:4502/editor.html/content/venia/us/en.html) 로새로 고칩니다.

   ![환경 친화적인 메시지 표시](../assets/customize-cif-components/eco-friendly-text-displayed.png)

   제품에 `eco_friendly` 속성이 **예**&#x200B;로 설정된 경우 페이지에 &quot;Eco Friendly&quot; 텍스트가 표시됩니다. 동작 변경을 확인하려면 다른 제품으로 전환해 보십시오.

1. 다음으로 AEM `error.log` 를 열어 추가한 로그 문을 확인합니다. 그 `error.log` 는 위치 `<AEM SDK Install Location>/crx-quickstart/logs/error.log`에 있다.

   AEM 로그를 검색하여 Sling 모델에 추가된 로그 문을 확인합니다.

   ```plain
   2020-08-28 12:57:03.114 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is Eco Friendly**
   ...
   2020-08-28 13:01:00.271 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is not Eco Friendly**
   ...
   ```

   >[!CAUTION]
   >
   > Teaser에 사용된 제품에 속성 세트의 일부로 속성이 없는 경우 일부 스택 `eco_friendly` 추적이 표시될 수도 있습니다.

## 친환경 배지에 스타일 추가 {#add-styles}

이 시점에서는 **친환경** 배지 표시 시점의 논리가 효과가 있지만 일반 텍스트는 일부 스타일을 사용할 수 있습니다. 그런 다음 `ui.frontend` 모듈에 아이콘과 스타일을 추가하여 구현을 완료합니다.

1. eco_friendly.svg [파일을](../assets/customize-cif-components/eco_friendly.svg) 다운로드합니다. 이 배지는 **친환경** 배지로 사용됩니다.
1. IDE로 돌아가 `ui.frontend` 폴더로 이동합니다.
1. 폴더에 `eco_friendly.svg` 파일을 `ui.frontend/src/main/resources/images` 추가합니다.

   ![친환경 SVG 추가됨](../assets/customize-cif-components/eco-friendly-svg-added.png)

1. 에서 파일 `productteaser.scss` 을 엽니다 `ui.frontend/src/main/styles/commerce/_productteaser.scss`.
1. 다음 Sass 규칙을 `.productteaser` 클래스 내에 추가합니다.

   ```scss
   .productteaser {
       ...
       .item__eco {
           width: 60px;
           height: 60px;
           left: 0px;
           overflow: hidden;
           position: absolute;
           padding: 5px;
   
       span {
           display: block;
           position: absolute;
           width: 45px;
           height: 45px;
           text-indent: -9999px;
           background: no-repeat center center url('../resources/images/eco_friendly.svg'); 
           }
       }
   ...
   }
   ```

   >[!NOTE]
   >
   > 프런트 [엔드 워크플로우에 대한 자세한 내용은 스타일](./style-cif-component.md) CIF 핵심 구성 요소를 참조하십시오.

1. 명령줄 터미널에서 Maven 기술을 사용하여 변경 내용을 저장하고 AEM에 업데이트를 배포합니다.

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. 제품 Teaser가 추가된 http://localhost:4502/editor.html/content/venia/us/en.html **** 의 Venia 홈 페이지 [](http://localhost:4502/editor.html/content/venia/us/en.html) 로새로 고칩니다.

   ![친환경 배지 최종 구현](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## 축하합니다 {#congratulations}

첫 번째 AEM CIF 구성 요소를 사용자 정의했습니다! 여기에서 [완성된 솔루션 파일을 다운로드합니다](../assets/customize-cif-components/customize-cif-component-SOLUTION_FILES.zip).

## 보너스 챌린지 {#bonus-challenge}

제품 Teaser에 이미 구현된 **새** 배지 기능을 검토하십시오. 작성자가 **친환경 배지 표시 시기를 제어할 수 있는 확인란을** 추가해 보십시오. 에서 구성 요소 대화 상자를 업데이트해야 합니다 `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser/_cq_dialog/.content.xml`.

![새로운 배지 구현 당면 과제](../assets/customize-cif-components/new-badge-implementation-challenge.png)

## 추가 리소스 {#additional-resources}

* [AEM 원형](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)
* [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)
* [AEM CIF 핵심 구성 요소 사용자 정의](https://github.com/adobe/aem-core-cif-components/wiki/Customizing-CIF-Core-Components)
* [핵심 구성 요소 사용자 정의](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html)
* [AEM Sites 시작하기](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
