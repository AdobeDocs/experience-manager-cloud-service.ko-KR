---
title: 고급 URL 구성
description: 제품 및 카테고리 페이지의 URL을 사용자 지정하는 방법을 알아봅니다. 이를 통해 구현은 검색 엔진에 대한 URL을 최적화하고 검색을 촉진할 수 있습니다.
sub-product: 상거래
version: cloud-service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 3%

---


# 고급 URL 구성 {#url}

[AEM CIF 핵심 구성](https://github.com/adobe/aem-core-cif-components) 요소는 제품 및 카테고리 페이지의 URL을 사용자 지정하는 고급 구성을 제공합니다. 많은 구현에서 SEO(검색 엔진 최적화)를 위해 이러한 URL을 사용자 정의합니다.  다음 비디오에서는 제품 및 카테고리 페이지의 URL을 사용자 `UrlProvider` 지정하도록 Sling [](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) Mapping의 서비스 및 기능을 구성하는 방법에 대해 자세히 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## 구성 {#configuration}

SEO 요구 사항에 따라 `UrlProvider` 서비스를 구성하고 프로젝트가 필요한 경우 &quot;CIF URL 공급자 구성&quot; 구성에 대한 OSGI 구성을 제공해야 하며 아래에 설명된 대로 서비스를 구성해야 합니다.

>[!NOTE]
>
> Venia [Reference 스토어](https://github.com/adobe/aem-cif-guides-venia) 프로젝트에는 제품 및 카테고리 페이지에 대한 사용자 정의 URL의 사용을 시연하기 위한 샘플 구성이 포함되어 있습니다.

### 제품 페이지 URL 템플릿 {#product}

제품 페이지의 URL을 다음 속성으로 구성합니다.

* **제품 URL 템플릿**:자리표시자 집합을 가진 URL의 형식을 정의합니다. 기본값은 다음과 `{{page}}.{{url_key}}.html#{{variant_sku}}`같이 URL을 생성하는 `/content/venia/us/en/products/product-page.chaz-kangeroo-hoodie.html#MH01-M-Orange` 것입니다.
   * `{{page}}` 다음으로 대체됨 `/content/venia/us/en/products/product-page`
   * `{{url_key}}` magento의 `url_key` 소유물로 대체되었습니다. `chaz-kangeroo-hoodie`
   * `{{variant_sku}}` 이(가) 현재 선택한 변형으로 대체되었습니다. `MH01-M-Orange`
* **제품 식별자 위치**:제품 데이터를 가져오는 데 사용할 식별자의 위치를 정의합니다. 기본값은 `SELECTOR`이며, 가능한 다른 값은 입니다 `SUFFIX`. 이전 예제 URL을 사용하면 식별자가 제품 데이터를 가져오는 데 사용됩니다. `chaz-kangeroo-hoodie`
* **제품 식별자 유형**:제품 데이터를 가져올 때 사용할 식별자 유형을 정의합니다. 기본값은 `URL_KEY`이며, 가능한 다른 값은 입니다 `SKU`. 이전 예제 URL을 사용하면 제품 데이터가 Magento GraphQL 필터와 함께 반입됩니다 `filter:{url_key:{eq:"chaz-kangeroo-hoodie"}}`.

### 제품 목록 페이지 URL 템플릿 {#product-list}

이렇게 하면 카테고리 또는 제품 목록 페이지의 URL이 다음 속성으로 구성됩니다.

* **범주 URL 템플릿**:자리표시자 집합을 가진 URL의 형식을 정의합니다. 기본값은 다음과 `{{page}}.{{id}}.html`같이 URL을 생성하는 `/content/venia/us/en/products/category-page.3.html` 것입니다.
   * `{{page}}` 다음으로 대체됨 `/content/venia/us/en/products/category-page`
   * `{{id}}` 카테고리의 Magento `id` 자산으로 대체되었습니다. `3`
* **카테고리 식별자 위치**:제품 데이터를 가져오는 데 사용할 식별자의 위치를 정의합니다. 기본값은 `SELECTOR`이며, 가능한 다른 값은 입니다 `SUFFIX`. 이전 예제 URL을 사용하면 식별자가 제품 데이터를 가져오는 데 사용됩니다. `3`
* **카테고리 식별자 유형**:제품 데이터를 가져올 때 사용할 식별자 유형을 정의합니다. 기본값과 현재 지원되는 값만 입니다 `ID`. 이전 예제 URL을 사용하면 카테고리 데이터를 Magento GraphQL 필터와 함께 가져오는 것을 의미합니다 `category(id:3)`.

구성 요소에서 해당 데이터를 사용하여 설정하는 한 각 템플릿에 대한 사용자 지정 속성을 추가할 수 `UrlProvider`있습니다. 클래스 코드의 예를 확인하여 `ProductListItemImpl` 이것이 구현되는 방법을 알아냅니다.

또한 서비스를 완전히 사용자 정의 OSGi 서비스로 `UrlProvider` 대체할 수도 있습니다. 이 경우, 기본 구현을 대체하려면 `UrlProvider` 인터페이스를 구현하고 높은 서비스 등급으로 등록해야 합니다.

## 슬링 매핑과 결합 {#sling-mapping}

또한 URL `UrlProvider`을 다시 작성하고 처리하기 [위해](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) Sling 매핑을 구성할 수도 있습니다. AEM Tranype 프로젝트 [는 포트 4503(게시) 및 80(발송자)에 대한 일부 Sling 매핑을 구성하는 예제 구성](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) 기능도 제공합니다.

## AEM Dispatcher와 결합 {#dispatcher}

또한 `mod_rewrite` 모듈과 함께 AEM Dispatcher HTTP 서버를 사용하여 URL 재쓰기를 수행할 수 있습니다. AEM [Project Tranype은 생성된 크기에 대한 기본](https://github.com/adobe/aem-project-archetype) 다시 작성 규칙을 [](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) 이미 포함하는 참조 AEM Dispatcher 구성을 제공합니다.

## 예

Venia [Reference 스토어](https://github.com/adobe/aem-cif-guides-venia) 프로젝트에는 제품 및 카테고리 페이지에 대한 사용자 지정 URL의 사용을 보여주는 샘플 구성이 포함되어 있습니다. 이를 통해 각 프로젝트는 SEO 요구 사항에 따라 제품 및 카테고리 페이지에 대한 개별 URL 패턴을 설정할 수 있습니다. 위에 설명된 CIF `UrlProvider` 및 Sling 매핑의 조합이 사용됩니다.

>[!NOTE]
>
>이 구성은 프로젝트에서 사용하는 외부 도메인에 맞게 조정되어야 합니다. 슬링 매핑은 호스트 이름 및 도메인을 기반으로 작동합니다. 따라서 이 구성은 기본적으로 비활성화되며 배포하기 전에 활성화해야 합니다. 이렇게 하려면 사용된 도메인 이름에 `hostname.adobeaemcloud.com` 따라 Sling Mapping `ui.content/src/main/content/jcr_root/etc/map.publish/https` 폴더 `resource.resolver.map.location="/etc/map.publish"` 의 이름을 변경하고 프로젝트의 구성 `JcrResourceResolver` 에 추가하여 이 구성을 활성화합니다.

## 추가 리소스

* [Venia Reference store](https://github.com/adobe/aem-cif-guides-venia)
* [AEM 리소스 매핑](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/resource-mapping.html)
* [슬링 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
