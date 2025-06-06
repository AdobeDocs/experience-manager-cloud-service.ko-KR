---
title: 구성 요소 및 GraphQL 캐시 지우기
description: AEM CIF에서 캐시 지우기 기능을 활성화하고 확인하는 방법을 알아봅니다.
feature: Commerce Integration Framework
role: Admin
exl-id: f89c07c7-631f-41a4-b5b9-0f629ffc36f0
source-git-commit: 27d8b5f6f358176c828d01f2ff51886d0433017c
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 2%

---

# 구성 요소 및 GraphQL 캐시 지우기 {#clear-cache}

이 문서에서는 AEM CIF의 캐시 지우기 기능 활성화 및 확인에 대한 포괄적인 안내서를 제공합니다.

>[!NOTE]
>
> 이 기능은 실험적입니다.

## CIF 구성에서 캐시 지우기 기능 활성화 {#enable-clear-cache}

CIF 구성에서는 기본적으로 캐시 지우기 기능이 비활성화되어 있습니다. 활성화하려면 해당 프로젝트에 다음을 추가해야 합니다.

* [여기](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config.author/com.adobe.cq.cif.cacheinvalidation.internal.InvalidateCacheNotificationImpl.cfg.json)와 같이 프로젝트에서 `com.adobe.cq.cif.cacheinvalidation.internal.InvalidateCacheNotificationImpl.cfg.json` 구성을 추가하여 해당 요청으로 clear-cache API를 트리거하는 데 도움이 되는 서블릿 `/bin/cif/invalidate-cache`을(를) 활성화합니다.
  >[!NOTE]
  >
  > 작성자 인스턴스에 대해서만 구성을 활성화해야 합니다.

* [여기](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.core.cacheinvalidation.internal.InvalidateCacheSupport.cfg.json)와 같이 프로젝트에서 `com.adobe.cq.commerce.core.cacheinvalidation.internal.InvalidateCacheSupport.cfg.json` 구성을 추가하여 리스너가 AEM의 각 인스턴스(게시 및 작성자)에서 캐시를 지울 수 있도록 합니다.
   * 작성자 및 게시 인스턴스 모두에 대해 구성을 활성화해야 합니다.
   * Dispatcher 캐시 활성화(선택 사항): 위의 구성에서 `enableDispatcherCacheInvalidation` 속성을 true로 설정하여 Dispatcher 캐시 지우기 설정을 활성화할 수 있습니다. 이렇게 하면 Dispatcher에서 캐시를 지우는 기능이 제공됩니다.
     >[!NOTE]
     >
     > 게시 인스턴스에서만 작동합니다.

   * 또한, 제품, 카테고리 및 CMS 페이지에 맞는 해당 패턴을 위의 구성 파일에 추가하여 Dispatcher 캐시에서 제거해야 합니다.

* 제품 및 범주와 관련된 해당 페이지를 찾기 위한 SQL 쿼리 성능을 향상하려면 프로젝트에 해당 인덱스를 추가하십시오(권장). 자세한 내용은 [cifCacheInvalidationSupport/]&#x200B;(링크 https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.apps/src/main/content/jcr_root/_oak_index/cifCacheInvalidationSupport/.content.xml)을 참조하십시오.

## 캐시 지우기 기능 확인 중 {#verify-clear-cache}

모든 것이 올바르게 설정되었는지 확인하려면 다음을 수행하십시오.

* 작성자 인스턴스 AEM에 해당 서블릿을 트리거합니다(예: [http://localhost:4502/bin/cif/invalidate-cache](http://localhost:4502/bin/cif/invalidate-cache)). 200 HTTP 응답을 가져와야 합니다.
* 작성자 인스턴스의 `/var/cif/cacheinvalidation` 경로에 노드가 만들어졌는지 확인하십시오. 노드 이름은 `cmd_{{timestamp}}` 패턴을 따릅니다.
* 각 게시 인스턴스에 동일한 노드가 생성되었는지 확인합니다.

이제 캐시가 제대로 지워지고 있는지 확인하려면 다음을 수행하십시오.
1. 해당 PLP 및 PDP 페이지로 이동합니다.
2. 상거래 엔진에서 제품 또는 카테고리 이름을 업데이트합니다. 캐시 구성에 따라 변경 사항이 AEM에 즉시 반영되지 않습니다.
3. 다음과 같이 서블릿 API를 트리거합니다.

   ```
   curl --location '{Author AEM Instance Url}/bin/cif/invalidate-cache' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: ••••••' \ // Mandatory
   --header 'Cookie: private_content_version=0299c5e4368a1577a6f454a61370317b' \
   --data '{
       "productSkus": ["Sku1", "Sku2"], // Optional: Pass the corresponding sku which got updated.
       "categoryUids":["CategoryUid"], // Optional : Pass the corresponding category-uid which got updated.
       "storePath": "/content/venia/us/en", // Mandatory : Needs to be given to know for which site we are removing the clear cache.
   }'
   ```
모든 것이 잘 진행되면 새로운 변경 사항이 모든 인스턴스에 반영됩니다. 게시 인스턴스에 대한 변경 사항이 반영되지 않는 경우 전용 창에서 해당 PLP 및 PDP 페이지를 확인하십시오.

>[!NOTE]
>
> 게시 인스턴스는 여러 수준의 캐시 레이어를 가질 수 있습니다. 이 기능은 AEM 내부 메모리 및 Dispatcher의 캐시 지우기만 담당합니다.

## 캐시 무효화 API 지우기 {#clear-cache-api}

AEM에서 상거래 관련 데이터의 캐시를 지우고자 할 때마다 트리거해야 하는 API입니다.

요청 유형: `POST`

### 헤더

| 매개변수 | 값 | 필수/필수 | 댓글 |
|------------------------------|-------------------|---|---|
| `Content-Type` | `application/json` | 필수 |  |
| `Authorization` | 해당 작성자의 사용자 자격 증명(인증 유형: 기본 인증) | 필수 | 해당 사용자 이름과 암호를 추가합니다. |


### 페이로드

다음 표는 기능이 기본 제공하는 기존 속성을 보여 줍니다. 이러한 `InvalidateType` 속성은 필수 특성(예: `storePath`)과 함께 지정해야 합니다.

| `invalidateType` | 값 | 유형(배열/문자열/부울) | 이렇게 하면 Dispatcher 캐시가 지워집니까? | 댓글 |
|------------------------------|-------------------|---|---|---|
| `productSkus` | 캐시에서 무효화해야 하는 제품의 sku. | 배열 | 예 | <br>```"\"sku\":\\s*\""```<br>Dispatcher<br> 패턴을 사용하여 내부 메모리에서 캐시를 지웁니다.<ul><li>해당 SKU의 PDP 페이지 캐시 지우기</li><li>해당 카테고리가 존재하는 카테고리 페이지의 캐시 지우기(상업의 graphql 응답 기반)</li><li>다음 쿼리를 기반으로 캐시를 지웁니다.</li></ul><br>```SELECT content.[jcr:path] FROM [nt:unstructured] AS content<br>WHERE ISDESCENDANTNODE(content, '{storePath}')<br>AND ( (content.[product] IN ('sku1','sku2') AND content.[productType] = 'combinedSku')<br> OR (content.[selection] IN ('sku1','sku2') AND content.[selectionType] IN ('combinedSku', 'sku')))``` |
| `categoryUids` | 범주의 uid - 캐시에서 무효화해야 합니다. | 배열 | 예 | <br>```"\"uid\"\\s*:\\s*\\{\"id\"\\s*:\\s*\""```<br>Dispatcher<br> 패턴을 사용하여 내부 메모리에서 캐시를 지웁니다.<ul><li>해당 데이터(하위 범주 페이지 포함)에 대한 범주 페이지 캐시 지우기</li><li>해당 범주가 있는 모든 PDP 페이지 지우기</li><li>다음 쿼리를 기반으로 캐시를 지웁니다.</li></ul><br>```SELECT content.[jcr:path] FROM [nt:unstructured] AS content<br>WHERE ISDESCENDANTNODE(content,'{storePath}')<br>AND ((content.[categoryId] in ('category1','category2')<br>AND content.[categoryIdType] in ('uid'))<br>OR (content.[category] in ('category1','category2') AND content.[categoryType] in ('uid')))``` |
| `regexPatterns` | 정규 표현식 패턴을 기반으로 GraphQL 응답 데이터를 지워야 하는 경우 이를 사용합니다. | 배열 | 아니요 | |
| `cacheNames` | 이 값은 해당 CIF GraphQL 클라이언트 구성 팩토리 >> 해당 StorePath GraphQL 구성 >> GraphQL 캐시 구성 아래에 정의됩니다 | 배열 | 아니요 | |
| `invalidateAll` | True 또는 False | 부울 | 예 | |

이 표에서는 모든 API 호출에서 전달해야 하는 필수 속성을 보여 줍니다.

| 속성 | 값 | 유형(배열/문자열/부울) | 이렇게 하면 Dispatcher 캐시가 지워집니까? | 댓글 |
|------------------------------|-------------------|---|---|---|
| `storePath` | 캐시를 제거해야 하는 사이트 경로의 해당 값(예: venia 프로젝트 참조: `/content/venia/us/en`). | 문자열 | 예 | 이 값은 `invalidateType.`의 조합과 함께 제공되어야 합니다. |

### 샘플 API 요청

```
curl --location 'https://author-p10603-e145552-cmstg.adobeaemcloud.com/bin/cif/invalidate-cache' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--header 'Cookie: private_content_version=0299c5e4368a1577a6f454a61370317b' \
--data '{
"productSkus": ["VP01", "VT10"], // This will clear cache for the corresponding pages related with mentioned skus.
"categoryUids":["Mjk="], // This will clear cache for the corresponding pages related with mentioned categories.
"regexPatterns":["\"uid\"\\s*:\\s*\\{\"id\"\\s*:\\s*\"(Mjk=)\"", "\"sku\":\\s*\"(VP02|VP03)\""],
"cacheNames": ["venia/components/commerce/product"], // If this been added then it will clear respective caches for the corresponding storepath
"storePath": "/content/venia/us/en"
}'
```

## 확장성 {#clear-cache-extensibility}

이 기능은 핵심 기능을 제공할 뿐만 아니라 확장성을 제공하여 개발자가 필요에 따라 핵심 기능을 구축하고 맞춤화할 수 있도록 합니다.

### 기존 속성 확장 {#existing-attribute}

기존 특성 기반 기능(예: `categoryUids`)에서 현재 다루지 않는 캐시를 지워야 하는 경우 [이 참조 파일](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/ExtendedCategoryUidInvalidation.java)을 참조하여 새 패턴을 추가하고 현재 구현이 처리하는 범위를 넘어 캐시에서 지워야 하는 추가 `invalidatePaths`을(를) 정의할 수 있습니다.

### 새 사용자 지정 속성 추가 {#new-custom-attribute}

예를 들어 캐시를 지우기 위해 기존 속성을 사용하지 않으려면 고유한 속성을 만들고 해당 기능을 정의할 수 있는 유연성을 갖습니다.

* AEM의 내부 메모리(graphql 응답)에서 캐시만 지우면 [이 참조](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/CustomInvalidation.java)를 따라야 합니다.
* 내부 메모리 및 Dispatcher 캐시에서 캐시를 지워야 하는 경우 [이 참조](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/CustomDispatcherInvalidation.java)를 따라야 합니다.
  >[!NOTE]
  >
  > `getPatterns()` 메서드에 대해 `null`을(를) 반환하면 내부 지우기 캐시를 무시할 수 있습니다.
