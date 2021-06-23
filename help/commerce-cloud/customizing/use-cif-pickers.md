---
title: CIF 제품 및 카테고리 선택기 사용
description: 고객 상거래 구성 요소에서 CIF 제품 및 카테고리 선택기를 사용하여 작성자와 마케터가 상거래 제품 및 카탈로그 데이터를 효율적으로 사용할 수 있도록 지원하는 방법을 알아봅니다.
sub-product: 상거래
topics: Development
version: cloud-service
activity: develop
audience: developer
feature: 전자 상거래 통합 프레임워크
exl-id: 30f1f263-1b78-46ae-99ed-61861c488b2a
source-git-commit: 35137687e51d54454d3a4b7aed247a28d98dc291
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# AEM Content &amp; Commerce Authoring Picker {#cif-pickers}

AEM Content &amp; Commerce Authoring은 AEM 작성자와 마케터가 상거래 제품 데이터 및 카탈로그를 효율적으로 작업할 수 있도록 하는 작성 도구 세트를 제공합니다. 제품 선택기 및 카테고리 선택기는 CIF 추가 기능의 일부이며 CIF 코어 구성 요소에서 사용됩니다. 프로젝트는 구성 요소 대화 상자에서 이러한 선택기를 사용하여 제품 또는 카테고리를 선택할 수 있습니다.

## 제품 선택기 {#product-picker}

프로젝트 구성 요소에서 제품 선택기를 사용하려면 개발자가 `commerce/gui/components/common/cifproductfield`을 구성 요소 대화 상자에 추가해야 합니다. 예를 들어 cq:dialog:에 다음 내용을 사용하십시오

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

제품 필드를 사용하면 사용자가 다른 보기를 통해 선택할 제품을 탐색할 수 있습니다. 기본적으로 제품 필드는 제품의 ID를 반환하지만 `selectionId` 속성을 사용하여 구성할 수 있습니다.

제품 선택기 필드는 다음과 같은 선택적 속성을 지원합니다.

- selectionId (id, uid, sku, slug, combinedSlug, combinedSku) - 선택기에서 반환할 제품 속성을 선택할 수 있습니다(기본값 = id). sku를 사용하면 결합된 Sku를 사용하는 동안 선택한 제품의 sku를 반환하고 기본 제품 및 선택한 변형의 sku가 있는 base#variant와 같은 문자열 또는 기본 제품이 선택된 경우 단일 sku를 반환합니다.
- filter(folderOrProduct, folderOrProductOrVariant) - 제품 트리를 탐색하는 동안 선택기에서 렌더링할 컨텐츠를 필터링합니다. folderOrProduct - 폴더와 제품을 렌더링합니다. folderOrProductOrVariant - 폴더, 제품 및 제품 변형을 렌더링합니다. 제품 또는 제품 변형을 렌더링하면 선택기에서 선택할 수도 있습니다. (기본값 = folderOrProduct)
- multiple (true, false) - 하나 이상의 제품을 선택할 수 있도록 설정(기본값 = false)
- emptyText - 선택기 필드의 빈 텍스트 값을 구성하려면

또한 `name`, `fieldLabel` 또는 `fieldDescription`와 같은 표준 진단 필드 속성도 지원됩니다.

>[!CAUTION]
>
>`cifproductfield` 구성 요소에는 `cif.shell.picker` clientlib이 필요합니다. clientlib을 대화 상자에 추가하려면 extraClientlibs 속성을 사용할 수 있습니다.
>[!CAUTION]
>
>CIF 코어 구성 요소 버전 2.0.0부터 `id`에 대한 지원이 제거되고 `uid` 로 대체되었습니다. 제품 식별자로 `sku` 또는 `slug` 을 사용하는 것이 좋습니다. CIF 코어 구성 요소 버전 1.x를 사용하는 프로젝트에만 `id`을 계속 지원합니다.

`cifproductfield` 의 전체 작업 예는 [CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml) 프로젝트에서 찾을 수 있습니다. AEM 코어 구성 요소 설명서의 [대화 상자 사용자 지정](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs)을 참조하십시오.

## 카테고리 선택기 {#category-picker}

카테고리 선택기는 제품 선택기와 유사한 방식으로 구성 요소 대화 상자에서도 사용할 수 있습니다.

cq:dialog 구성에서 다음 코드 조각을 사용할 수 있습니다.

```xml
<category jcr:primaryType="nt:unstructured" 
    sling:resourceType="commerce/gui/components/common/cifcategoryfield" 
    fieldLabel="Category" 
    name="./categoryId" 
    selectionId="uid" />
```

카테고리 선택기 필드는 다음과 같은 선택적 속성을 지원합니다.

- selectionId(id, uid, slug, idAndUrlPath, uidAndUrlPath) - 선택기에서 반환할 카테고리 속성을 선택할 수 있습니다(기본값 = id). idAndUrlPath 및 uidAndUrlPath는 카테고리 id/uid 및 url_path를 로 구분하여 저장하는 특수 옵션입니다 | 문자(예: 1|men/top)
- multiple (true, false) - 하나 이상의 카테고리를 선택할 수 있도록 설정(기본값 = false)

또한 `name`, `fieldLabel` 또는 `fieldDescription`와 같은 표준 진단 필드 속성도 지원됩니다.

>[!CAUTION]
>
>`cifproductfield` 구성 요소와 동일한 `cifcategoryfield` 구성 요소에도 `cif.shell.picker` clientlib이 필요합니다. clientlib을 대화 상자에 추가하려면 `extraClientlibs` 속성을 사용할 수 있습니다. AEM 코어 구성 요소 설명서의 [대화 상자 사용자 지정](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs)을 참조하십시오.
>[!CAUTION]
>
>CIF 코어 구성 요소 버전 2.0.0부터 `id`에 대한 지원이 제거되고 `uid` 로 대체되었습니다. 카테고리 식별자로 `uid` 또는 `slug` 을 사용하는 것이 좋습니다. CIF 코어 구성 요소 버전 1.x를 사용하는 프로젝트에만 `id` 및 `idAndUrlPath`을 계속 지원합니다.

`cifcategoryfield` 의 전체 작업 예는 [CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml) 프로젝트에서 찾을 수 있습니다.
