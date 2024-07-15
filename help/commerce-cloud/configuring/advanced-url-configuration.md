---
title: 고급 URL 구성
description: 제품 및 카테고리 페이지의 URL을 사용자 지정하는 방법을 알아봅니다. 구현을 통해 검색 엔진의 URL을 최적화하고 검색을 홍보할 수 있습니다.
sub-product: Commerce
version: Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '2059'
ht-degree: 2%

---

# 고급 URL 구성 {#url}

>[!NOTE]
>
> SEO(검색 엔진 최적화)는 많은 마케터의 주요 관심사가 되었습니다. 그 결과, Adobe Experience Manager(AEM as a Cloud Service)의 많은 프로젝트에서 SEO 문제를 해결해야 합니다. 자세한 내용은 [SEO 및 URL 관리 모범 사례](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/seo-and-url-management.html)를 참조하세요.

[AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)는 제품 및 범주 페이지의 URL을 사용자 지정하는 고급 구성을 제공합니다. 많은 구현이 SEO(검색 엔진 최적화) 목적으로 이러한 URL을 사용자 지정합니다. 다음 비디오에서는 `UrlProvider` 서비스 및 [Sling 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)의 기능을 구성하여 제품 및 범주 페이지의 URL을 사용자 지정하는 방법에 대해 자세히 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## 구성 {#configuration}

SEO 요구 사항 및 요구 사항에 따라 `UrlProvider` 서비스를 구성하려면 프로젝트에서 _CIF URL 공급자 구성_&#x200B;에 대한 OSGI 구성을 제공해야 합니다.

>[!NOTE]
>
> AEM CIF 핵심 구성 요소 릴리스 2.0.0부터 URL 공급자 구성은 1.x 릴리스에 알려진 자유 텍스트 구성 가능 형식 대신 사전 정의된 URL 형식만 제공합니다. 또한 선택기를 사용하여 URL에 데이터를 전달하던 방식이 접미사로 대체되었습니다.

### 제품 페이지 URL 형식 {#product}

제품 페이지의 URL을 구성하고 다음 옵션을 지원합니다.

* `{{page}}.html/{{sku}}.html#{{variant_sku}}`(기본값)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

[Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)가 있는 경우:

* `{{page}}`이(가) `/content/venia/us/en/products/product-page`(으)로 대체되었습니다.
* `{{sku}}`은(는) 제품의 SKU로 대체됩니다(예: `VP09`).
* `{{url_key}}`은(는) 제품의 `url_key` 속성(예: `lenora-crochet-shorts`)으로 대체됩니다.
* `{{url_path}}`은(는) 제품의 `url_path`(예: `venia-bottoms/venia-pants/lenora-crochet-shorts`)로 대체됩니다.
* `{{variant_sku}}`은(는) 현재 선택한 변형(예: `VP09-KH-S`)으로 대체됩니다.

`url_path`이(가) 더 이상 사용되지 않으므로 미리 정의된 제품 URL 형식은 제품 `url_rewrites`을(를) 사용하고 `url_path`을(를) 사용할 수 없는 경우 대체 요소로 경로 세그먼트가 가장 많은 URL 형식을 선택합니다.

위의 예제 데이터를 사용하면 기본 URL 형식을 사용하여 형식이 지정된 제품 변형 URL은 `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`과(와) 같습니다.

### 카테고리 페이지 URL 형식 {#product-list}

카테고리 또는 제품 목록 페이지의 URL을 구성하고 다음 옵션을 지원합니다.

* `{{page}}.html/{{url_path}}.html`(기본값)
* `{{page}}.html/{{url_key}}.html`

[Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)가 있는 경우:

* `{{page}}`이(가) `/content/venia/us/en/products/category-page`(으)로 대체되었습니다.
* `{{url_key}}`이(가) 범주의 `url_key` 속성으로 대체되었습니다.
* `{{url_path}}`이(가) 범주의 `url_path`(으)로 대체되었습니다.

위의 예제 데이터를 사용하면 기본 URL 형식을 사용하여 형식이 지정된 카테고리 페이지 URL이 `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`처럼 보입니다.

>[!NOTE]
> 
> `url_path`은(는) `/` 슬래시로 구분된 제품이나 범주의 상위 항목 `url_keys`과(와) 제품이나 범주의 `url_key`의 연결입니다. 각 `url_key`은(는) 지정된 저장소 내에서 고유한 것으로 간주됩니다.

### 저장소별 구성 {#store-specific-urlformats}

_CIF URL 공급자 구성_&#x200B;에서 설정한 시스템 전체 범주 및 제품 페이지 URL 형식은 각 스토어에 대해 변경할 수 있습니다.

CIF 구성에서 편집기는 대체 제품 또는 카테고리 페이지 URL 형식을 선택할 수 있습니다. 아무 것도 선택하지 않으면 시스템 전체 구성으로 돌아갑니다.

라이브 웹 사이트의 URL 형식을 변경하면 사이트의 유기 트래픽에 부정적인 영향을 줄 수 있습니다. 아래의 [모범 사례](#best-practices)를 보고 URL 형식 변경을 미리 신중하게 계획하십시오.

![CIF 구성의 URL 형식](assets/store-specific-url-formats.png)

>[!NOTE]
>
> URL 형식의 저장소별 구성에는 [CIF 핵심 구성 요소 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0)과(와) 최신 버전의 Adobe Experience Manager 콘텐츠 및 Commerce 추가 기능이 필요합니다.

## 카테고리 인식 제품 페이지 URL {#context-aware-pdps}

제품 URL에 카테고리 정보를 인코딩할 수 있으므로, 여러 카테고리에 있는 제품도 여러 제품 URL로 해결될 수 있습니다.

기본 URL 형식은 다음 체계를 사용하여 가능한 대체 요소 중 하나를 선택합니다.

* `url_path`이(가) 전자 상거래 백엔드에 의해 정의된 경우 이를 사용합니다(더 이상 사용되지 않음).
* `url_rewrites`에서 제품의 `url_key`(으)로 끝나는 URL을 대체 URL로 사용합니다.
* 이러한 대체 형식에서는 경로 세그먼트가 가장 많은 대체 형식을 사용합니다
* 여러 개가 있는 경우 전자 상거래 백엔드에서 지정한 순서대로 첫 번째 항목을 사용합니다

이 구성표는 하위 범주가 상위 범주보다 더 구체적이라는 가정에 따라 상위 범주가 가장 많은 `url_path`을(를) 선택합니다. 선택한 `url_path`은(는) _표준_(으)로 간주되며 항상 제품 페이지 또는 제품 사이트 맵에서 표준 링크로 사용됩니다.

그러나 쇼핑객이 카테고리 페이지에서 제품 페이지로 이동하거나 한 제품 페이지에서 동일한 카테고리의 다른 관련 제품 페이지로 이동할 때는 현재 카테고리 컨텍스트를 유지하는 것이 좋습니다. 이 경우 `url_path` 선택은 위에서 설명한 _표준_ 선택보다 현재 범주 컨텍스트 내에 있는 대안을 선호해야 합니다.

이 기능은 _CIF URL 공급자 구성_&#x200B;에서 사용하도록 설정해야 합니다. 활성화한 경우 다음과 같은 상황에서 선택 점수가 더 높습니다.

* 지정된 범주의 `url_path` 일부를 처음부터 일치시킵니다(유사 접두사 일치).
* 또는 지정된 범주의 `url_key`과(와) 어디서나 일치합니다(완전 부분 일치).

예를 들어 아래의 [제품 쿼리](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html)에 대한 응답을 고려해 보십시오. 다음과 같은 경우

* 사용자가 &quot;New Products / New in Summer 2022&quot; 카테고리 페이지에 있습니다.
* 스토어는 기본 카테고리 페이지 URL 형식을 사용합니다

대체 &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;은 처음부터 컨텍스트의 경로 세그먼트 중 두 개와 일치합니다. 즉, &quot;신제품&quot;과 &quot;2022년 여름 신제품&quot;입니다. 스토어에서 `url_key` 범주만 포함하는 범주 페이지 URL 형식을 사용하는 경우, 어디에서나 컨텍스트의 `url_key`과(와) 일치하므로 동일한 대체 항목이 계속 선택됩니다. 두 경우 모두 &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot; `url_path`에 대해 제품 페이지 URL이 만들어집니다.

```
{
  "data": {
    "products": {
      "items": [
        {
          "sku": "VA18-GO-NA",
          "url_key": "gold-cirque-earrings",
          "url_rewrites": [
            {
              "url": "gold-cirque-earrings.html"
            },
            {
              "url": "venia-accessories/gold-cirque-earrings.html"
            },
            {
              "url": "venia-accessories/venia-jewelry/gold-cirque-earrings.html"
            },
            {
              "url": "new-products/gold-cirque-earrings.html"
            },
            {
              "url": "new-products/new-in-summer-2022/gold-cirque-earrings.html"
            }
          ]
        }
      ]
    }
  }
}
```

>[!NOTE]
>
> 범주 인식 제품 URL에는 [CIF 핵심 구성 요소 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) 이상이 필요합니다.

## 특정 범주 및 제품 페이지 {#specific-pages}

카탈로그의 특정 하위 집합 또는 제품에 대해서만 [다중 범주 및 제품 페이지](../authoring/multi-template-usage.md)를 만들 수 있습니다.

### 선택 기준 {#specific-pages-selection}

범주의 `url_path` 또는 `url_key`을(를) 기준으로 특정 범주 페이지를 직접 선택합니다. 전체 범주 `url_path`이(가) 포함된 URL 형식에 대해서만 일치하는 하위 범주가 지원됩니다. 그렇지 않으면 `url_key`과(와) 정확히 일치만 가능합니다.

특정 제품 페이지는 제품의 SKU 또는 카테고리에 의해 선택됩니다. 후자는 제품 URL에 일부 카테고리 정보를 인코딩해야 합니다. 이 기능은 일부 기본 URL 형식에만 사용할 수 있습니다. SKU 또는 카테고리별로 특정 페이지 선택을 지원하는 URL 포맷을 비교하려면 다음 표를 참조하십시오.


| URL 형식 | SKU별 | 범주별 |
| ----------------------------------------------------- | ------ | ---------------- |
| `{{page}}.html/{{url_key}}.html` | 아니오 | 아니오 |
| `{{page}}.html/{{category}}/{{url_key}}.html` | 아니오 | 정확한 일치만 |
| `{{page}}.html/{{url_path}}.html` | 아니오 | 예 |
| `{{page}}.html/{{sku}}.html` | 예 | 아니오 |
| `{{page}}.html/{{sku}}/{{url_key}}.html` | 예 | 아니오 |
| `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html` | 예 | 정확한 일치만 |
| `{{page}}.html/{{sku}}/{{url_path}}.html` | 예 | 예 |

{style="table-layout:auto"}

>[!NOTE]
>
> 카테고리별로 특정 제품 페이지를 선택하려면 [CIF 핵심 구성 요소 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) 이상이 필요합니다.

### 심층 연결 {#specific-pages-deep-linking}

작성자 계층 인스턴스의 특정 범주 및 제품 페이지에 대한 딥링크를 생성하도록 `UrlProvider`이(가) 미리 구성되어 있습니다. 이 기능은 미리보기 모드를 사용하여 사이트를 탐색하고 특정 제품 또는 카테고리 페이지로 이동한 다음 편집 모드로 다시 전환하여 페이지를 편집하는 편집자에게 유용합니다.

반면에 게시 계층 인스턴스에서는 카탈로그 페이지 URL이 안정적으로 유지되어야 검색 엔진 순위에서 이득을 잃지 않습니다. 해당 게시 계층 때문에 인스턴스는 기본적으로 특정 카탈로그 페이지에 대한 딥링크를 렌더링하지 않습니다. 이 동작을 변경하려면 항상 특정 페이지 URL을 생성하도록 _CIF URL 공급자별 페이지 전략_&#x200B;을 구성할 수 있습니다.

### 여러 카탈로그 페이지 {#multiple-product-pages}

편집자가 사이트의 최상위 수준 탐색을 완전히 제어하려는 경우 단일 카탈로그 페이지를 사용하여 카탈로그의 최상위 수준 카테고리를 렌더링하는 것은 필요하지 않을 수 있습니다. 대신 편집자는 최상위 탐색에 포함할 카탈로그의 각 카테고리에 대해 하나씩 여러 카탈로그 페이지를 만들 수 있습니다.

해당 사용 사례의 경우, 각 카탈로그 페이지에는 카탈로그 페이지에 대해 구성된 카테고리와 관련된 제품 및 카테고리 페이지에 대한 참조가 있을 수 있습니다. `UrlProvider`은(는) 이러한 연결을 사용하여 구성된 범주의 페이지 및 범주에 대한 링크를 만듭니다. 그러나 성능상의 이유로 사이트 탐색 루트/랜딩 페이지의 직접 카탈로그 페이지 하위 항목만 고려됩니다.

카탈로그 페이지의 제품 및 카테고리 페이지는 해당 카탈로그 페이지의 하위 페이지인 것이 좋습니다. 그렇지 않으면 탐색 또는 탐색 표시와 같은 구성 요소가 제대로 작동하지 않을 수 있습니다.

>[!NOTE]
>
> 여러 카탈로그 페이지를 모두 지원하려면 [CIF 핵심 구성 요소 2.10.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0) 이상이 필요합니다.

## 사용자 정의 {#customization}

### 사용자 정의 URL 형식 {#custom-url-format}

사용자 지정 URL 형식을 제공하기 위해 프로젝트는 [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) 또는 [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) 서비스 인터페이스를 구현하고 구현을 OSGI 서비스로 등록할 수 있습니다. 이러한 구현은 사용 가능한 경우 구성된 사전 정의된 형식을 대체합니다. 등록된 구현이 여러 개일 경우 서비스 순위가 높은 구현이 서비스 순위가 낮은 구현을 대체합니다.

사용자 지정 URL 형식 구현은 주어진 매개 변수에서 URL을 작성하고 URL을 구문 분석하여 동일한 매개 변수를 각각 반환하기 위한 메서드 쌍을 구현해야 합니다.

### Sling 매핑과 결합 {#sling-mapping}

`UrlProvider` 외에도 URL을 다시 작성하고 처리하도록 [Sling 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)을 구성할 수 있습니다. AEM Archetype 프로젝트에서는 포트 4503(게시) 및 80(Dispatcher)에 대한 일부 Sling 매핑을 구성할 수 있도록 [예제 구성](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish)도 제공합니다.

### AEM Dispatcher과 결합 {#dispatcher}

`mod_rewrite` 모듈과 함께 AEM Dispatcher HTTP 서버를 사용하여 URL 재쓰기를 수행할 수도 있습니다. [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)은(는) 생성된 크기에 대한 기본 [다시 작성 규칙](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud)이 이미 포함된 참조 AEM Dispatcher 구성을 제공합니다.

## 모범 사례 {#best-practices}

### 최상의 URL 형식 선택 {#choose-url-format}

사용 가능한 기본 형식 중 하나를 선택하거나 사용자 지정 형식을 구현하기 전에 언급했듯이 는 저장소의 요구 사항과 요구 사항에 따라 크게 달라집니다. 다음과 같은 제안은 교육적인 결정을 내리는 데 도움이 될 수 있습니다.

_**SKU가 포함된 제품 페이지 URL 형식을 사용합니다.**_

CIF 핵심 구성 요소는 모든 구성 요소에서 SKU를 기본 식별자로 사용합니다. 제품 페이지 URL 형식에 SKU가 포함되어 있지 않은 경우 이 문제를 해결하려면 GraphQL 쿼리가 필요합니다. 이 해상도는 첫 번째 바이트까지의 시간에 영향을 줄 수 있습니다. 또한, 쇼핑객이 검색 엔진을 사용하여 SKU별로 제품을 찾을 수 있는 것이 필요할 수 있습니다.

_**범주 컨텍스트가 포함된 제품 페이지 URL 형식을 사용하십시오.**_

CIF URL 공급자의 일부 기능은 `url_key` 범주 또는 `url_path` 범주와 같은 범주 컨텍스트를 인코딩하는 제품 URL 형식을 사용하는 경우에만 사용할 수 있습니다. 새 스토어에 이러한 기능이 필요하지 않더라도 맨 앞에 이러한 URL 형식 중 하나를 사용하면 향후 마이그레이션 작업을 줄일 수 있습니다.

_**URL 길이와 인코딩된 정보 간의 균형.**_

카탈로그 크기, 특히 범주 트리의 크기 및 깊이에 따라 전체 `url_path` 범주의 URL을 인코딩하는 것은 적절하지 않을 수 있습니다. 이 경우 대신 범주의 `url_key`만 포함하면 URL 길이를 줄일 수 있습니다. 이 메서드는 범주 `url_path`을(를) 사용할 때 사용할 수 있는 대부분의 기능을 지원합니다.

또한 [Sling 매핑](#sling-mapping)을(를) 사용하여 SKU를 `url_key` 제품과 결합하십시오. 대부분의 전자 상거래 시스템에서 SKU는 특정 형식을 따르며 수신 요청에 대해 SKU를 `url_key`과(와) 구분하는 것이 용이해야 합니다. 이를 고려하여 제품 페이지 URL을 `/p/{{category}}/{{sku}}-{{url_key}}.html`에, 범주 URL을 `/c/{{url_key}}.html`에 각각 다시 작성할 수 있어야 합니다. `/p` 및 `/c` 접두사는 제품 및 범주 페이지를 다른 콘텐츠 페이지와 구분하는 데 계속 필요합니다.

### 새 URL 형식으로 마이그레이션 {#migrate-url-formats}

대부분의 기본 URL 형식은 서로 호환됩니다. 즉, 형식이 다른 URL이 다른 URL에 의해 구문 분석될 수 있습니다. URL 형식 간에 마이그레이션하는 데 도움이 됩니다.

반면 검색 엔진은 새 URL 형식으로 모든 카탈로그 페이지를 다시 캡처하는 데 시간이 필요합니다. 이 프로세스를 지원하고 최종 사용자 경험을 개선하기 위해 사용자를 이전 URL에서 새 URL로 전달하는 리디렉션을 제공하는 것이 좋습니다.

이에 대한 한 가지 접근 방식은 프로덕션 전자 상거래 백엔드에 단계 환경을 연결하고 새 URL 형식을 사용하도록 구성하는 것입니다. 이후 단계 및 프로덕션 환경 모두에 대해 CIF 제품 사이트 맵 생성기](../../overview/seo-and-url-management.md)에서 생성된 [제품 사이트 맵을 얻은 다음 이를 사용하여 [Apache httpd 다시 작성 맵](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html)을(를) 만듭니다. 그런 다음 이 재작성 맵을 새 URL 형식의 롤아웃과 함께 Dispatcher에 배포할 수 있습니다.

## 예 {#example}

[Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia) 프로젝트에는 제품 및 범주 페이지에 대한 사용자 지정 URL의 사용을 보여 주는 샘플 구성이 포함되어 있습니다. 이 구성을 통해 각 프로젝트는 SEO 요구 사항에 따라 제품 및 카테고리 페이지에 대한 개별 URL 패턴을 설정할 수 있습니다. 위에서 설명한 대로 CIF `UrlProvider`과(와) Sling 매핑의 조합이 사용됩니다.

>[!NOTE]
>
>프로젝트에서 사용하는 외부 도메인을 사용하여 이 구성을 조정해야 합니다. Sling 매핑은 호스트 이름과 도메인을 기반으로 작동합니다. 따라서 이 구성은 기본적으로 비활성화되며 배포 전에 활성화해야 합니다. 이렇게 하려면 사용된 도메인 이름에 따라 `ui.content/src/main/content/jcr_root/etc/map.publish/https`에서 Sling 매핑 `hostname.adobeaemcloud.com` 폴더의 이름을 바꾸고 프로젝트의 `JcrResourceResolver` 구성에 `resource.resolver.map.location="/etc/map.publish"`을(를) 추가하여 이 구성을 사용하도록 설정하십시오.

## 추가 리소스 {#additional}

* [Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)
* [AEM 리소스 매핑](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
