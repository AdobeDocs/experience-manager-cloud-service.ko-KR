---
title: JSON+LD 메타데이터
description: AEM CIF에서 JSON+LD 기능을 활성화하고 확인하는 방법을 알아봅니다.
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 547d3721-e094-4a42-8a7c-27e4ef97ea9c
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 2%

---


# JSON+LD 메타데이터 {#json-ld}

이 안내서에서는 AEM CIF에서 JSON+LD 기능을 활성화하고 확인하는 방법을 설명합니다.

>[!NOTE]
>
> 이 기능은 실험적입니다.

## CIF 구성에서 JSON+LD 활성화 {#enabling}

기본적으로 **JSON+LD 사용** 확인란은 CIF 구성에 표시되지 않습니다. 이 기능을 활성화하려면 프로젝트에 확인란을 표시할 수 있는 필요한 OSGi 구성이 포함되어야 합니다. 이 구성을 통해 사용자는 제품 페이지에서 JSON+LD 스크립트 지원을 전환할 수 있습니다.

CIF 구성에서 **JSON+LD 사용** 확인란을 사용할 수 있도록 하려면 프로젝트에 다음 OSGi 구성을 추가하십시오.

`com.adobe.cq.cif.components.models.JsonLdFeatureEnable`

이 구성 추가에 대한 자세한 내용은 공용 aem-cif-guides-venia 리포지토리의 [Json-Ld에 대한 구성 추가](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.cif.components.models.JsonLdFeatureEnable.cfg.json)를 참조하십시오.

이 구성이 추가되고 배포되면 CIF 구성 설정에 확인란이 표시되며 **JSON+LD**&#x200B;을(를) 활성화하는 단계는 다음과 같습니다.

1. AEM의 CIF 구성으로 이동합니다.
1. 상속을 취소합니다.
1. **JSON+LD 사용** 확인란을 선택합니다.
1. 구성을 저장합니다.

## PDP(Product Detail Page)에서 JSON+LD 확인 {#verify}

JSON+LD를 확인하는 단계를 보여주기 위해 Venia 프로젝트가 예로 사용되며, 여기서 필요한 JSON+LD 구성이 이미 해당 기능을 활성화하기 위해 추가되었습니다. 다음은 따라야 할 단계입니다.

1. 로컬 AEM 인스턴스로 이동하여 PDP(Product Detail Page)를 엽니다. `http://localhost:4502/editor.html/content/venia/us/en/products/product-page.html`
1. PDP(Product Detail Page)에서 제품을 작성합니다.
1. **게시로 보기** 모드로 전환합니다.
1. 브라우저에서 **Source 보기**&#x200B;를 엽니다.
1. 페이지 소스에서 JSON+LD를 검색합니다.

올바르게 구성된 경우 페이지에 삽입된 제품과 관련된 JSON+LD 스크립트를 찾을 수 있습니다.

## 제품에 대한 샘플 JSON+LD 구조 {#sample}

다음은 Venia 프로젝트의 PDP 페이지에서 작성된 Agatha 스커트에 대한 **JSON+LD** 구조의 예입니다.

```html
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "Product",
  "sku": "VSK05",
  "name": "Agatha Skirt",
  "image": "https://mcstaging.catalogservice4commerce.fun/media/catalog/product/cache/926ea6fc2ad48a7202ff4587b6c2768e/v/s/vsk05-pe_main_2.jpg",
  "description": "The Agatha Skirt has a large circumference that lends itself to all sorts of drama...",
  "@id": "product-ef4fa1dc72",
  "offers": [
    {
      "@type": "Offer",
      "sku": "VSK05-KH-S",
      "url": "/content/venia/us/en/products/product-page.html/agatha-skirt.html",
      "priceCurrency": "USD",
      "price": 78.0
    },
    {
      "@type": "Offer",
      "sku": "VSK05-RN-XS",
      "availability": "InStock",
      "priceSpecification": {
        "@type": "UnitPriceSpecification",
        "priceType": "https://schema.org/ListPrice",
        "price": 18.0,
        "priceCurrency": "USD"
      },
      "price": 46.0
    }
  ]
}
</script>
```

## GraphQL에 JSON+LD 속성 매핑 {#mapping}

JSON+LD 속성을 AEM CIF의 GraphQL 쿼리에 매핑하여 구조화된 데이터가 GraphQL을 통해 검색된 제품 정보를 동적으로 반영하도록 할 수 있습니다.

### 제품 매핑 예 {#example}

| JSON+LD 속성 | Magento GraphQL 속성 | 필수(Y/N) |
|---------------------------------|-------------------|---|
| sku | sku | N |
| offers.url | 사용자 지정 논리 | N |
| offers.SpecialPricedate | special_to_date | N |
| offers.sku | sku | N |
| offers.priceSpecification.priceCurrency | 통화 | Y |
| offers.priceSpecification.price | regular_price | N |
| offers.priceCurrency | 통화 | Y |
| offers.price | special_price | Y |
| offers.image | media_gallery.url | N |
| offers.availability | stock_status | N |
| 이름 | 이름 | Y |
| 이미지 | media_gallery.url | Y |
| 설명 | 설명 | N |
| aggregateRating.reviewCount | review_count | N |
| aggregateRating.ratingValue | rating_summary | N |
| @id | id | N |

이 매핑을 통해 GraphQL 쿼리를 통해 검색된 제품 데이터를 기반으로 JSON+LD 스크립트가 동적으로 채워집니다.

JSON+LD 구조를 테스트하려면 [리치 결과 테스트 - Google 검색 콘솔을 사용할 수 있습니다.](https://search.google.com/test/rich-results/result?id=wtU3LVIEM8H7Aaf5qqK9qw) 이 도구는 필요한 특성이 있는지 누락되었는지 등 자세한 피드백을 제공하고 구조화된 데이터가 올바르게 구현되도록 합니다.
