---
title: 고급 URL 구성
description: 제품 및 카테고리 페이지의 URL을 사용자 지정하는 방법을 알아봅니다. 이를 통해 구현은 검색 엔진에 대한 URL을 최적화하고 검색을 승격할 수 있습니다.
sub-product: 상거래
version: cloud-service
doc-type: technical-video
activity: setup
audience: administrator
feature: 전자 상거래 통합 프레임워크
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7,363cb465-c50a-422f-b149-b3f41c2ebc0f
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 3%

---

# 고급 URL 구성 {#url}

[AEM CIF 핵심 ](https://github.com/adobe/aem-core-cif-components) 구성 요소는 제품 및 카테고리 페이지의 URL을 사용자 지정하는 고급 구성을 제공합니다. 많은 구현이 SEO(검색 엔진 최적화) 목적으로 이러한 URL을 사용자 지정합니다.  다음 비디오에서는 `UrlProvider` 서비스 및 [Sling Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)의 기능을 구성하여 제품 및 카테고리 페이지의 URL을 사용자 지정하는 방법에 대해 자세히 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## 구성 {#configuration}

SEO 요구 사항에 따라 `UrlProvider` 서비스를 구성하려면 프로젝트가 필요합니다. &quot;CIF URL 공급자 구성&quot; 구성에 대한 OSGI 구성을 제공하고 아래에 설명된 대로 서비스를 구성해야 합니다.

>[!NOTE]
>
> [Venia Reference store](https://github.com/adobe/aem-cif-guides-venia) 프로젝트는 아래 참조 자료 구성을 포함하여 제품 및 카테고리 페이지에 대한 사용자 지정 URL의 사용을 보여 줍니다.

### 제품 페이지 URL 템플릿 {#product}

이렇게 하면 다음 속성으로 제품 페이지의 URL이 구성됩니다.

* **제품 URL 템플릿**:자리 표시자 집합을 사용하여 URL의 형식을 정의합니다. 기본값은 `{{page}}.{{url_key}}.html#{{variant_sku}}`이며, 여기서 `/content/venia/us/en/products/product-page.chaz-kangeroo-hoodie.html#MH01-M-Orange` 와 같이 URL이 생성됩니다.
   * `{{page}}` 이(가)  `/content/venia/us/en/products/product-page`
   * `{{url_key}}` 이 제품 `url_key` 의 Magento 속성으로 대체되었습니다.  `chaz-kangeroo-hoodie`
   * `{{variant_sku}}` 이(가) 현재 선택한 변형으로 대체되었습니다.  `MH01-M-Orange`
* **제품 식별자 위치**:제품 데이터를 가져오는 데 사용할 식별자의 위치를 정의합니다. 기본값은 `SELECTOR`이고, 다른 가능한 값은 `SUFFIX`입니다. 이전 예제 URL을 사용하면 ID `chaz-kangeroo-hoodie`이 제품 데이터를 가져오는 데 사용됨을 의미합니다.
* **제품 식별자 유형**:제품 데이터를 가져올 때 사용할 식별자의 유형을 정의합니다. 기본값은 `URL_KEY`이고, 다른 가능한 값은 `SKU`입니다. 이전 예 URL을 사용하면 제품 데이터를 `filter:{url_key:{eq:"chaz-kangeroo-hoodie"}}` 과 같은 Magento GraphQL 필터로 가져오게 됩니다.

### 제품 목록 페이지 URL 템플릿 {#product-list}

이렇게 하면 다음 속성으로 카테고리 또는 제품 목록 페이지의 URL이 구성됩니다.

* **카테고리 URL 템플릿**:자리 표시자 집합을 사용하여 URL의 형식을 정의합니다. 기본값은 `{{page}}.{{id}}.html`이며, 여기서 `/content/venia/us/en/products/category-page.3.html` 와 같이 URL이 생성됩니다.
   * `{{page}}` 이(가)  `/content/venia/us/en/products/category-page`
   * `{{id}}` 이 Magento의  `id` 카테고리 속성으로 대체되었습니다. 여기서는  `3`
* **카테고리 식별자 위치**:제품 데이터를 가져오는 데 사용할 식별자의 위치를 정의합니다. 기본값은 `SELECTOR`이고, 다른 가능한 값은 `SUFFIX`입니다. 이전 예제 URL을 사용하면 ID `3`이 제품 데이터를 가져오는 데 사용됨을 의미합니다.
* **카테고리 식별자 유형**:제품 데이터를 가져올 때 사용할 식별자의 유형을 정의합니다. 기본값과 현재 지원되는 값은 `ID`입니다. 이전 예제 URL을 사용하면 카테고리 데이터를 `category(id:3)` 과 같은 Magento GraphQL 필터로 가져오게 됩니다.

구성 요소에서 `UrlProvider` 을 사용하여 해당 데이터를 설정하고 있는 한 각 템플릿에 대한 사용자 지정 속성을 추가할 수 있습니다. `ProductListItemImpl` 클래스의 코드 예를 확인하여 이 구현이 어떻게 구현되는지 확인하십시오.

또한 `UrlProvider` 서비스를 완전히 사용자 지정 OSGi 서비스로 대체할 수도 있습니다. 이 경우, 기본 구현을 바꾸려면 `UrlProvider` 인터페이스를 구현하고 높은 서비스 등급에 등록해야 합니다.

## Sling 매핑과 결합 {#sling-mapping}

`UrlProvider` 외에 URL을 다시 작성하고 처리하기 위해 [Sling 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)을 구성할 수도 있습니다. AEM Archetype 프로젝트는 포트 4503(게시) 및 80(디스패처)에 대한 일부 Sling 매핑을 구성하기 위한 [예제 구성](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish)도 제공합니다.

## AEM Dispatcher와 결합 {#dispatcher}

`mod_rewrite` 모듈과 함께 AEM Dispatcher HTTP 서버를 사용하여 URL 다시 쓰기를 수행할 수도 있습니다. [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)은 생성된 크기에 대한 기본 [rewrite 규칙](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud)을 이미 포함하는 참조 AEM Dispatcher 구성을 제공합니다.

## 예

[Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) 프로젝트에는 제품 및 카테고리 페이지에 대한 사용자 지정 URL의 사용을 보여 주는 샘플 구성이 포함되어 있습니다. 이렇게 하면 각 프로젝트에서 SEO 요구 사항에 따라 제품 및 카테고리 페이지에 대한 개별 URL 패턴을 설정할 수 있습니다. 위에 설명된 대로 CIF `UrlProvider` 및 Sling 매핑의 조합이 사용됩니다.

>[!NOTE]
>
>이 구성은 프로젝트에서 사용하는 외부 도메인으로 조정해야 합니다. Sling 매핑은 호스트 이름 및 도메인을 기반으로 작동합니다. 따라서 이 구성은 기본적으로 비활성화되어 있으므로 배포 전에 활성화해야 합니다. 이렇게 하려면 사용된 도메인 이름에 따라 `ui.content/src/main/content/jcr_root/etc/map.publish/https`에 있는 Sling 매핑 `hostname.adobeaemcloud.com` 폴더의 이름을 변경하고, `resource.resolver.map.location="/etc/map.publish"` 를 프로젝트의 `JcrResourceResolver` 구성에 추가하여 이 구성을 활성화합니다.

## 추가 리소스

* [Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)
* [AEM 리소스 매핑](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling 매핑](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
