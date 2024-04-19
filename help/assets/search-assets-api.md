---
title: 자산 검색 API
description: Search Assets API를 사용하는 방법을 알아봅니다.
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 자산 검색 API {#search-assets-api}

모두 [승인된 에셋](approved-assets.md) Experience Manager 에셋 저장소에서 사용할 수 있으며, 검색 후 배달 URL을 사용하여 통합 다운스트림 애플리케이션에 전달할 수 있습니다.

Experience Manager 저장소에서 올바른 승인된 에셋을 검색하는 것은 게재 URL을 사용하여 에셋을 게재하는 첫 번째 단계입니다. 검색 요청에 대한 응답은 검색 기준을 충족하는 에셋에 해당하는 JSON 문서 배열로 구성됩니다. 각 JSON 문서는 `id` 필드: 에셋 게재 요청을 구성하는 데 사용됩니다.

![다이렉트 이진 업로드 프로토콜 개요](assets/search-assets-api-overview.png)

Search Assets API 요청 내에서 속성을 정의하여 다음 기능을 활성화할 수 있습니다.

* **전체 텍스트 검색**: 사용 `match` 검색할 텍스트를 정의하려면 질의합니다.  다음 내에서 연산자를 사용할 수도 있습니다. `match` 쿼리 를 클릭하여 결과를 필터링합니다.

* **필터 적용**: 사용 `term` 쿼리 를 클릭하여 다음을 정의하여 결과를 추가로 필터링합니다. `key` 및 하나 또는 여러 값을 포함할 수 있습니다. `key` 은 값이 일치해야 하는 필드를 식별하며, `value` 는 일치시킬 항목을 나타냅니다. 마찬가지로 `range` 다음보다 큼(gt), 다음보다 크거나 같음(gte), 다음보다 작음(lt) 및 다음보다 작거나 같음(lte) 속성을 사용하여 필드의 범위를 정의하는 쿼리입니다.

* **결과 정렬**: 사용 `OrderBy` 속성을 사용하여 하나 이상의 필드를 기준으로 검색 결과를 정렬할 수 있습니다. 결과를 오름차순 또는 내림차순으로 정렬할 수 있습니다.

* **쪽 매기기**: 사용 `limit` 및 `cursor` 속성을 사용하여 검색 API 요청 내에서 페이지 매김 속성을 정의할 수 있습니다. `limit` 속성은 API 응답에서 검색할 최대 항목을 정의합니다. `cursor` 속성은에 정의된 다음 에셋 세트의 시작점을 쉽게 검색할 수 있습니다. `limit` 속성. 예를 들어 다음을 `50` api 요청의 제한으로, `cursor` 다음 API 요청을 사용하여 다음 50개 항목을 시작 및 검색하는 속성입니다.

## 자산 검색 API 엔드포인트 {#search-assets-api-endpoint}

Search Assets API 요청의 끝점은 다음 형식이어야 합니다.
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

게재 도메인은 Experience Manager 작성자 환경의 도메인과 구조가 유사합니다. 유일한 차이점은 용어를 대체하는 것입니다 `author` 포함 `delivery`.

`pXXXX` 는 프로그램 ID를 나타냅니다.

`eYYYY` 환경 ID를 참조합니다.

## 자산 검색 API 요청 메서드 {#search-assets-api-request-method}

POST

## 자산 검색 API 헤더 {#search-assets-api-header}

Search Assets API에서 헤더를 정의하는 동안 다음 세부 정보를 제공해야 합니다.

```java
headers: {
      'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    },
```

Search API를 호출하려면 IMS 토큰이에서 을 정의해야 합니다. `Authorization` 세부 정보. IMS 토큰을 기술 계정에서 가져옵니다. 다음을 참조하십시오 [AEM as a Cloud Service 자격 증명 가져오기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) 새 기술 계정을 만듭니다. 다음을 참조하십시오 [액세스 토큰 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) ims 토큰을 생성하고 자산 검색 API 요청 헤더에서 적절하게 사용합니다.

요청 샘플, 응답 샘플 및 응답 코드를 보려면 [자산 검색 API](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).

