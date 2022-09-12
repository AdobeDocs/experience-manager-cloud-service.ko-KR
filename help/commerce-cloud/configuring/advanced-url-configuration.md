---
title: 고급 URL 구성
description: 제품 및 카테고리 페이지의 URL을 사용자 지정하는 방법을 알아봅니다. 이를 통해 구현은 검색 엔진에 대한 URL을 최적화하고 검색을 승격할 수 있습니다.
sub-product: Commerce
version: Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7,363cb465-c50a-422f-b149-b3f41c2ebc0f
source-git-commit: f5e465d90477f1b49e4ff1c5ca9dd47cc5d539bb
workflow-type: tm+mt
source-wordcount: '2039'
ht-degree: 3%

---

# 고급 URL 구성 {#url}

>[!NOTE]
>
> SEO(검색 엔진 최적화)는 많은 마케터의 주요 관심사가 되었습니다. 따라서 많은 Adobe Experience Manager (AEM) as a Cloud Service 프로젝트에서 SEO 문제를 해소해야 합니다. 자세한 내용 [SEO 및 URL 관리 우수 사례](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/seo-and-url-management.html) 추가 정보.

[AEM CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components) 제품 및 카테고리 페이지의 URL을 사용자 지정하는 고급 구성을 제공합니다. 많은 구현이 SEO(검색 엔진 최적화) 목적으로 이러한 URL을 사용자 지정합니다. 다음 비디오에서는 을 구성하는 방법을 자세히 설명합니다 `UrlProvider` 의 서비스 및 기능 [Sling 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) 제품 및 카테고리 페이지의 URL을 사용자 지정하는 방법.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## 구성 {#configuration}

를 구성하려면 `UrlProvider` SEO 요구 사항에 따라 서비스를 제공하며 프로젝트가 필요한 경우 _CIF URL 공급자 구성_.

>[!NOTE]
>
> AEM CIF 코어 구성 요소 의 릴리스 2.0.0부터 URL 공급자 구성에서는 1.x 릴리스에서 알려진 자유 텍스트 구성 가능 형식 대신 미리 정의된 URL 형식만 제공합니다. 또한 URL에서 데이터를 전달하는 선택기를 사용하여 접미사로 대체되었습니다.

### 제품 페이지 URL 형식 {#product}

제품 페이지의 URL을 구성하고 다음 옵션을 지원합니다.

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (기본값)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

의 경우 [Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` 교체 `/content/venia/us/en/products/product-page`
* `{{sku}}` 은 제품의 sku(예: )로 대체됩니다. `VP09`
* `{{url_key}}` 이 제품의 `url_key` 속성(예: `lenora-crochet-shorts`
* `{{url_path}}` 이 제품의 `url_path`예: `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` 은 현재 선택한 변형으로 대체됩니다(예: ). `VP09-KH-S`

다음 이후 `url_path` 가 더 이상 사용되지 않는 경우, 사전 정의된 제품 URL 형식은 제품의 `url_rewrites` 및 를 선택하는 경우 경로 세그먼트가 가장 큰 세그먼트를 대체 항목으로 선택합니다 `url_path` 을(를) 사용할 수 없습니다.

위의 예제 데이터를 사용하면 기본 URL 형식을 사용하여 형식이 지정된 제품 변형 URL은 다음과 같습니다 `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### 카테고리 페이지 URL 형식 {#product-list}

카테고리 또는 제품 목록 페이지의 URL을 구성하고 다음 옵션을 지원합니다.

* `{{page}}.html/{{url_path}}.html` (기본값)
* `{{page}}.html/{{url_key}}.html`

의 경우 [Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` 교체 `/content/venia/us/en/products/category-page`
* `{{url_key}}` 은(는) 카테고리의 `url_key` 속성
* `{{url_path}}` 은(는) 카테고리의 `url_path`

위의 예제 데이터를 사용하면 기본 URL 형식을 사용하여 형식이 지정된 카테고리 페이지 URL은 다음과 같습니다 `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
> 다음 `url_path` 는 `url_keys` 제품 또는 카테고리의 상위 항목 및 제품 또는 카테고리의 `url_key` 분리 `/` 슬래시. 각 `url_key` 는 주어진 스토어 내에서 고유하게 간주됩니다.

### 특정 구성 저장 {#store-specific-urlformats}

시스템 전체 카테고리 및 제품 페이지 URL 형식은 _CIF URL 공급자 구성_ 각 저장소에 대해 변경할 수 있습니다.

CIF 구성에서 편집기는 대체 제품 또는 카테고리 페이지 URL 형식을 선택할 수 있습니다. 아무 것도 선택하지 않으면 구현은 시스템 전체 구성으로 대체됩니다.

라이브 웹 사이트의 URL 형식을 변경하면 사이트의 유기 트래픽에 부정적인 영향을 줄 수 있습니다. 자세한 내용은 [우수 사례](#best-practices) 아래에서 미리 URL 형식 변경을 신중하게 계획합니다.

![CIF 구성의 URL 형식](assets/store-specific-url-formats.png)

>[!NOTE]
>
> 저장소별 URL 형식 구성은 [CIF 코어 구성 요소 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) 최신 버전의 Adobe Experience Manager Content and Commerce 추가 기능입니다.

## 카테고리 인식 제품 페이지 URL {#context-aware-pdps}

제품 URL에서 카테고리 정보를 인코딩할 수 있으므로 여러 카테고리에 있는 제품은 여러 제품 URL로 주소를 지정할 수도 있습니다.

기본 URL 형식은 다음 스키마를 사용하여 가능한 대체 요소 중 하나를 선택합니다.

* if `url_path` e-commerce 백엔드에서 정의합니다(사용 중단됨).
* 에서 `url_rewrites` 제품의 `url_key` 대체 요소
* 이러한 대체 요소에서는 가장 많은 경로 세그먼트가 있는 세그먼트를 사용합니다
* 여러 개가 있는 경우 전자 상거래 백엔드에서 지정한 순서대로 첫 번째 항목을 가져갑니다

이 구성표는 `url_path` 상위 카테고리가 상위 카테고리보다 하위 카테고리가 더 구체적이라는 가정을 기반으로 하여 가장 많은 상위 카테고리를 사용합니다. 선택한 항목 `url_path` 는 고려됩니다 _정식_ 및 는 항상 제품 페이지 또는 제품 사이트 맵에서 표준 링크로 사용됩니다.

그러나 쇼핑객이 카테고리 페이지에서 제품 페이지로 이동하거나, 한 제품 페이지에서 동일한 카테고리의 다른 관련 제품 페이지로 이동하는 경우 현재 카테고리 컨텍스트를 유지하는 것이 좋습니다. 이 경우 `url_path` 선택 사항에서는 현재 카테고리 컨텍스트 내에 있는 대체 요소를 선호해야 합니다. _정식_ 위에 설명된 선택 사항입니다.

이 기능은 _CIF URL 공급자 구성_. 활성화하면 선택 내용이 대체 요소에 더 높은 점수를 주게 됩니다

* 해당 카테고리의 일부와 일치합니다 `url_path` 시작(퍼지 접두사 일치)
* 또는 지정된 카테고리와 일치하는 `url_key` 장소(정확히 부분 일치)

예를 들어 [제품 쿼리](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) 아래의 제품에서 사용할 수 있습니다. 사용자가 &quot;New Products / New in Summer 2022&quot; 카테고리 페이지에 있고 스토어가 기본 카테고리 페이지 URL 형식을 사용하는 경우, 대체 &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;은(는) 처음부터 컨텍스트의 경로 세그먼트 중 2개와 일치합니다. &quot;new-products&quot; 및 &quot;new-in-summer-2022&quot; 저장소가 카테고리만 포함하는 카테고리 페이지 URL 형식을 사용하는 경우 `url_key`컨텍스트의 와 일치하므로 동일한 대체 요소가 여전히 선택됩니다 `url_key` 어디에나 두 경우 모두 &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;에 대해 제품 페이지 URL이 만들어집니다 `url_path`.

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
> 카테고리 인식 제품 URL에 필요한 [CIF 코어 구성 요소 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) 또는 그 이상

## 특정 카테고리 및 제품 페이지 {#specific-pages}

만들 수 있습니다 [여러 카테고리 및 제품 페이지](../authoring/multi-template-usage.md) 를 참조하십시오.

### 선택 기준 {#specific-pages-selection}

특정 카테고리 페이지의 선택은 카테고리의 `url_path` 또는 `url_key`. 일치하는 하위 카테고리는 전체 카테고리를 포함하는 URL 형식에 대해서만 지원됩니다 `url_path`. 그렇지 않으면 와 정확히 일치하는 `url_key` 가능합니다.

특정 제품 페이지가 제품의 sku 또는 카테고리로 선택됩니다. 나중에 제품 URL에서 일부 카테고리 정보를 인코딩해야 합니다. 일부 기본 URL 형식에만 사용할 수 있습니다. sku 또는 카테고리별로 특정 페이지 선택을 지원하는 URL 형식과 비교하려면 아래 표를 참조하십시오.


| URL 형식 | sku | 카테고리 기준 |
| ----------------------------------------------------- | ------ | ---------------- |
| `{{page}}.html/{{url_key}}.html` | 아니오 | 아니오 |
| `{{page}}.html/{{category}}/{{url_key}}.html` | 아니오 | 정확히 일치만 |
| `{{page}}.html/{{url_path}}.html` | 아니오 | 예 |
| `{{page}}.html/{{sku}}.html` | 예 | 아니오 |
| `{{page}}.html/{{sku}}/{{url_key}}.html` | 예 | 아니오 |
| `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html` | 예 | 정확히 일치만 |
| `{{page}}.html/{{sku}}/{{url_path}}.html` | 예 | 예 |

{style=&quot;table-layout:auto&quot;}

>[!NOTE]
>
> 카테고리별로 특정 제품 페이지를 선택하려면 다음이 필요합니다 [CIF 코어 구성 요소 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) 또는 그 이상

### 심층 연결 {#specific-pages-deep-linking}

다음 `UrlProvider` 는 작성 계층 인스턴스의 특정 카테고리 및 제품 페이지에 대한 딥 링크를 생성하도록 사전 구성되어 있습니다. 이 기능은 미리 보기 모드를 사용하여 사이트를 탐색하고, 특정 제품 또는 카테고리 페이지로 이동한 다음, 편집 모드로 전환하여 페이지를 편집하는 편집자에게 유용합니다.

반면 게시 계층 인스턴스에서는 카탈로그 페이지 URL을 안정적으로 유지하여 검색 엔진 순위가 더 이상 떨어지지 않도록 해야 합니다. 이러한 게시 계층 인스턴스로 인해 기본적으로 특정 카탈로그 페이지에 대한 딥 링크가 렌더링되지 않습니다. 이 동작을 변경하려면 _CIF URL 공급자 특정 페이지 전략_ 항상 특정 페이지 URL을 생성하도록 구성할 수 있습니다.

## 사용자 지정 {#customization}

### 사용자 지정 URL 형식 {#custom-url-format}

사용자 지정 URL 형식을 제공하려면 프로젝트가 다음을 구현할 수 있습니다 [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) 또는 [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) 서비스 인터페이스를 사용하여 구현을 OSGI 서비스로 등록합니다. 이러한 구현은 사용 가능한 경우 구성된 사전 정의된 형식을 대체합니다. 등록된 여러 개의 구현이 있는 경우 서비스 등급이 높은 구현은 해당 구현이 낮은 서비스 등급을 대체합니다.

사용자 지정 URL 형식 구현은 지정된 매개 변수에서 URL을 빌드하고 URL을 구문 분석하여 각각 동일한 매개 변수를 반환하는 한 쌍의 메서드를 구현해야 합니다.

### Sling 매핑과 결합 {#sling-mapping}

추가 `UrlProvider`를 설정하는 것도 가능합니다 [Sling 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) 를 재작성하고 처리하기 위해 입니다. AEM Archetype 프로젝트에서도 사용할 수 있습니다 [구성 예](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) 포트 4503(게시) 및 80(dispatcher)에 대한 일부 Sling 매핑을 구성하려면 다음을 수행하십시오.

### AEM Dispatcher와 결합 {#dispatcher}

URL 다시 쓰기는 AEM Dispatcher HTTP 서버를 `mod_rewrite` 모듈. 다음 [AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype) 에서는 이미 기본 항목이 포함된 참조 AEM Dispatcher 구성을 제공합니다 [rewrite 규칙](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) 생성되었습니다.

## 모범 사례 {#best-practices}

### 최상의 URL 형식 선택 {#choose-url-format}

사용 가능한 기본 형식 중 하나를 선택하거나 사용자 지정 형식을 구현하기 전에 언급했듯이 은 저장소의 요구 사항과 요구 사항에 따라 크게 달라집니다. 다음의 제안은 교육받은 설명을 하는 데 도움이 될 수 있다.

_**sku를 포함하는 제품 페이지 URL 형식을 사용합니다.**_

CIF 코어 구성 요소 는 모든 구성 요소에서 sku를 기본 식별자로 사용합니다. 제품 페이지 URL 형식에 sku가 포함되어 있지 않은 경우 GraphQL 쿼리가 이를 해결해야 합니다. 이 경우 1바이트 시간에 영향을 줄 수 있습니다. 또한 고객이 검색 기호를 사용하여 sku로 제품을 찾을 수 있다는 것이 필요할 수 있습니다.

_**카테고리 컨텍스트를 포함하는 제품 페이지 URL 형식을 사용합니다.**_

CIF Url Provider의 일부 기능은 제품 URL 형식을 사용할 때만 사용할 수 있으며, 카테고리와 같은 카테고리 컨텍스트를 인코딩합니다 `url_key` 또는 카테고리 `url_path`. 새 스토어에 이러한 기능이 필요하지 않을 수도 있지만 처음부터 이러한 URL 형식 중 하나를 사용하면 나중에 마이그레이션 작업을 줄일 수 있습니다.

_**URL 길이와 인코딩된 정보 간의 균형.**_

카탈로그 크기, 특히 카테고리 트리의 크기 및 깊이에 따라 전체 항목을 인코딩하는 것은 적절하지 않을 수 있습니다 `url_path` 카테고리를 URL에 추가합니다. 이 경우 카테고리만 포함하여 URL 길이를 줄일 수 있습니다 `url_key` 을 가리키도록 업데이트하는 것이 좋습니다. 이렇게 하면 카테고리를 사용할 때 사용할 수 있는 대부분의 기능이 지원됩니다 `url_path`.

또한 다음을 사용하십시오 [Sling 매핑](#sling-mapping) sku를 제품과 결합하려면 `url_key`. 대부분의 전자 상거래 시스템에서 sku는 특정 형식을 따르며 sku와 `url_key` 수신 요청의 경우 쉽게 수행할 수 있어야 합니다. 이를 염두에 두고 제품 페이지 URL을 다음으로 다시 작성할 수 있어야 합니다. `/p/{{category}}/{{sku}}-{{url_key}}.html`및 카테고리 URL을 `/c/{{url_key}}.html` 특별하게 다음 `/p` 및 `/c` 제품 및 카테고리 페이지를 다른 컨텐츠 페이지와 구분하려면 접두사가 여전히 필요합니다.

### 새 URL 형식으로 마이그레이션 {#migrate-url-formats}

대부분의 기본 URL 형식은 어떻게든 서로 호환되므로, 한 URL에서 가져온 URL을 다른 URL에서 구문 분석할 수 있습니다. URL 형식 간을 마이그레이션하는 데 도움이 됩니다.

반면 검색 엔진은 새로운 URL 포맷으로 모든 카탈로그 페이지를 다시 크롤링하는 데 시간이 걸릴 것입니다. 이 프로세스를 지원하고 최종 사용자 경험을 향상시키기 위해 이전 URL에서 새 URL로 사용자를 전달하는 리디렉션을 제공하는 것이 좋습니다.

한 가지 접근 방법은 스테이지 환경을 프로덕션 e-commerce 백엔드에 연결하고 새 URL 형식을 사용하도록 구성하는 것입니다. 그런 다음 를 가져옵니다 [CIF 제품 사이트 맵 생성기에서 생성된 제품 사이트 맵](../../overview/seo-and-url-management.md) 스테이지와 프로덕션 환경 모두에 대해 이 두 차원을 사용하여 [Apache httpd 재작성 맵](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). 이 다시 작성 맵은 새 URL 형식의 롤아웃과 함께 디스패처에 배포할 수 없습니다.

## 예 {#example}

다음 [Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia) 프로젝트에는 제품 및 카테고리 페이지에 대한 사용자 지정 URL의 사용을 보여주는 샘플 구성이 포함되어 있습니다. 이렇게 하면 각 프로젝트에서 SEO 요구 사항에 따라 제품 및 카테고리 페이지에 대한 개별 URL 패턴을 설정할 수 있습니다. CIF의 조합 `UrlProvider` 및 위에 설명된 Sling 매핑이 사용됩니다.

>[!NOTE]
>
>이 구성은 프로젝트에서 사용하는 외부 도메인으로 조정해야 합니다. Sling 매핑은 호스트 이름 및 도메인을 기반으로 작동합니다. 따라서 이 구성은 기본적으로 비활성화되어 있으므로 배포 전에 활성화해야 합니다. 이렇게 하려면 Sling 매핑의 이름을 변경합니다 `hostname.adobeaemcloud.com` 폴더 `ui.content/src/main/content/jcr_root/etc/map.publish/https` 사용된 도메인 이름에 따라 다음을 추가하여 이 구성을 활성화하십시오. `resource.resolver.map.location="/etc/map.publish"` 변환 후 `JcrResourceResolver` 구성 을 참조하십시오.

## 추가 리소스 {#additional}

* [Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)
* [AEM 리소스 매핑](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
