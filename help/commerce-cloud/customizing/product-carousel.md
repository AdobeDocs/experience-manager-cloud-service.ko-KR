---
title: CIF 제품 슬라이드에 대한 사용자 정의 속성
description: Sling 모델을 업데이트하고 마크업을 사용자 지정하여 AEM CIF 제품 슬라이드 구성 요소를 확장하는 방법을 알아봅니다.
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 594f0e6ec88851c86134be8d5d7f1719f74ddf4f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 4%

---

# CIF 제품 슬라이드에 대한 사용자 정의 속성 {#product-carousel}

## 소개 {#intro}

제품 슬라이드 구성 요소는 이 자습서 전체에서 확장됩니다. 첫 번째 단계로, 제품 캐러셀의 인스턴스를 홈 페이지에 추가하여 기본 기능을 이해합니다.

1. 사이트의 홈 페이지로 이동합니다(예: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)).
1. 새 제품 슬라이드 구성 요소를 페이지의 기본 레이아웃 컨테이너에 삽입합니다.
   ![제품 회전 메뉴 구성 요소](/help/commerce-cloud/assets/product-carousel-component.png)
1. 사이드 패널을 확장하고(아직 전환되지 않은 경우) 자산 파인더 드롭다운을 **제품**(으)로 전환합니다.
     ![회전 메뉴 제품](/help/commerce-cloud/assets/carousel-products.png)    
1. 연결된 Adobe Commerce 인스턴스에서 사용 가능한 제품 목록이 표시됩니다.
   ![연결된 인스턴스](/help/commerce-cloud/assets/connected-instance.png)
1. 제품은 기본 속성으로 아래와 같이 표시됩니다.
   ![속성이 표시된 제품](/help/commerce-cloud/assets/discount.png)

## Sling 모델 업데이트 {#update-sling-model}

Sling 모델을 구현하여 제품 캐러셀의 비즈니스 논리를 확장할 수 있습니다.

1. IDE에서 핵심 모듈 아래에서 `core/src/main/java/com/venia/core/models/commerce`(으)로 이동하고 CIF ProductCarousel 인터페이스를 확장하는 CustomCarousel 인터페이스를 만듭니다.

   ```
   package com.venia.core.models.commerce;
   import com.adobe.cq.commerce.core.components.models.productcarousel.ProductCarousel;
   public interface CustomCarousel extends ProductCarousel {
   }
   ```
1. 그런 다음 `core/src/main/java/com/venia/core/models/commerce/CustomCarouselImpl.java`에 구현 클래스 `CustomCarouselImpl.java`을(를) 만듭니다.
Sling 모델에 대한 전달 패턴을 통해 `CustomCarouselImpl`은(는) `sling:resourceSuperType` 속성을 통해 `ProductCarousel` 모델을 참조할 수 있습니다.

   ```
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductCarousel productCarousel;
   ```

1. @PostConstruct 주석은 Sling 모델이 초기화될 때 이 메서드가 호출되도록 합니다. 제품 GraphQL 쿼리는 특성을 검색하기 위해 extendProductQueryWith 메서드를 사용하여 이미 확장되었습니다. 다음을 포함하도록 GraphQL 쿼리 업데이트  partial 쿼리의 속성:

   ```
   @PostConstruct
   private void initModel() {
   productsRetriever = productCarousel.getProductsRetriever();
   
   if(productCarousel.getProductsRetriever() != null)
   productCarousel.getProductsRetriever().extendProductQueryWith(p -> p
   .createdAt()
   .addCustomSimpleField("accessory_gemstone_addon")
   );
   }
   ```

   위의 코드에서는 `addCustomSimpleField`을(를) 사용하여 `accessory_gemstone_addon` 특성을 검색합니다.

## 마크업 사용자 정의 {#customize-markup}

마크업을 추가로 사용자 정의하려면

1. `/apps/core/cif/components/commerce/productcarousel/v1/productcarousel`(핵심 구성 요소 자격 증명 경로)에서 ui.apps 모듈 `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productcarousel/productcard.html`(으)로 `productcard.html`의 복사본을 만듭니다.

1. 구현 클래스에 언급된 사용자 지정 특성을 호출하려면 `productcard.html`을(를) 편집하십시오.

   ```xml
   ..
   <div
       data-product-sku="${product.commerceIdentifier.value}"
       data-product-base-sku="${product.combinedSku.baseSku}"
       id="${product.id}"
       data-cmp-data-layer="${product.data.json}"
       class="card product__card">
       <span>${product.product.responseData['accessory_gemstone_addon']}</span>
       <a href="${product.URL}"
           target="${productCarousel.linkTarget}"
   ..
   ```

1. 명령줄 터미널에서 Maven 명령을 사용하여 변경 사항을 저장하고 업데이트를 AEM에 배포합니다. 페이지에서 선택한 제품에 대한 사용자 지정 특성 `accessory_gemstone_addon` 값을 볼 수 있습니다.
