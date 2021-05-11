---
title: AEM Assets API를 통해 컨텐츠를 업데이트하는 방법
description: AEM 헤드리스 개발자 여정의 이 부분에서 REST API를 사용하여 콘텐츠 조각에 액세스하고 업데이트하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
index: false
exl-id: 8d133b78-ca36-4c3b-815d-392d41841b5c
translation-type: tm+mt
source-git-commit: 4a36cd3206784c0e4e3ed3d7007c83f44f1d5ee0
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 2%

---

# AEM Assets API {#update-your-content}를 통해 컨텐츠를 업데이트하는 방법

>[!CAUTION]
>
>진행 중인 작업 - 이 문서의 작성은 진행 중이며 완전한 또는 최종적인 것으로 해석되거나 제작 목적으로 사용되어서는 안 됩니다.

[AEM 헤드리스 개발자 여정의 이 부분에서](overview.md) REST API를 사용하여 콘텐츠 조각에 액세스하고 업데이트하는 방법을 알아봅니다.

## 지금까지 스토리 {#story-so-far}

AEM 헤드리스 여정의 이전 문서에서 AEM 전달 API를 통해 콘텐츠에 액세스하는 방법](access-your-content.md) AEM GraphQL API를 통해 AEM에서 헤드리스 컨텐츠에 액세스하는 방법을 학습했고 이제 다음을 수행해야 합니다.[

* GraphQL에 대한 높은 수준의 이해를 제공합니다.
* AEM GraphQL API 작동 방식을 이해합니다.
* 몇 가지 실용적인 샘플 쿼리를 파악합니다.

이 문서는 이러한 기본 사항을 기반으로 구축되므로 REST API를 통해 AEM에서 기존 헤드리스 콘텐츠를 업데이트하는 방법을 이해할 수 있습니다.

## 목표 {#objective}

* **대상**:고급
* **목표**:REST API를 사용하여 컨텐츠 조각의 컨텐츠에 액세스하고 업데이트하는 방법을 알아봅니다.
   * AEM Assets HTTP API를 소개합니다.
   * API에서 컨텐츠 조각 지원 소개 및 토론
   * API에 대한 세부 사항을 설명합니다.

<!--
  * Look at sample code to see how things work in practice.
-->

## 컨텐츠 조각 {#why-http-api}에 대한 자산 HTTP API가 필요한 이유는 무엇입니까?

헤드리스 여정의 이전 단계에서는 AEM GraphQL API를 사용하여 쿼리를 사용하여 컨텐츠를 검색하는 방법을 알아보았습니다.

다른 API가 필요한 이유는 무엇입니까?

자산 HTTP API를 사용하면 **Read**&#x200B;컨텐츠를 볼 수 있지만, GraphQL API에서는 사용할 수 없는 작업(**,**&#x200B;업데이트&#x200B;**및**&#x200B;내용 삭제&#x200B;**)도 가능합니다.**

Assets REST API는 최신 Adobe Experience Manager을 Cloud Service 버전으로 즉시 설치할 때마다 사용할 수 있습니다.

## 자산 HTTP API {#assets-http-api}

자산 HTTP API에는 다음이 포함됩니다.

* 자산 REST API
* 컨텐츠 조각 지원 포함

자산 HTTP API의 현재 구현은 **REST** 아키텍처 스타일을 기반으로 하며, **CRUD** 작업(만들기, 읽기, 업데이트, 삭제)을 통해 내용(AEM에 저장됨)에 액세스할 수 있습니다.

이러한 작업을 수행할 때 API를 사용하면 JavaScript 프런트 엔드 애플리케이션에 컨텐츠 서비스를 제공하여 Adobe Experience Manager을 헤드리스 CMS(Content Management System)로 Cloud Service으로 운영할 수 있습니다. 또는 HTTP 요청을 실행하고 JSON 응답을 처리할 수 있는 다른 애플리케이션입니다. 예를 들어, 단일 페이지 애플리케이션(SPA), 프레임워크 기반 또는 사용자 정의 등은 API를 통해 제공된 컨텐츠가 필요합니다(주로 JSON 형식).

<!--
>[!NOTE]
>
>It is not possible to customize JSON output from the Assets REST API. 

The Assets REST API:

* follows the HATEOAS principle
* implements the SIREN format

## Key Concepts {#key-concepts}

The Assets REST API offers REST-style access to assets stored within an AEM instance. 

It uses the `/api/assets` endpoint and requires the path of the asset to access it (without the leading `/content/dam`). 

* This means that to access the asset at:
  * `/content/dam/path/to/asset`
* You need to request:
  * `/api/assets/path/to/asset` 

For example, to access `/content/dam/wknd/en/adventures/cycling-tuscany`, request `/api/assets/wknd/en/adventures/cycling-tuscany.json` 

>[!NOTE]
>Access over:
>
>* `/api/assets` **does not** need the use of the `.model` selector.
>* `/content/path/to/page` **does** require the use of the `.model` selector.

The HTTP method determines the operation to be executed:

* **GET** - to retrieve a JSON representation of an asset or a folder
* **POST** - to create new assets or folders
* **PUT** - to update the properties of an asset or folder
* **DELETE** - to delete an asset or folder

>[!NOTE]
>
>The request body and/or URL parameters can be used to configure some of these operations; for example, define that a folder or an asset should be created by a **POST** request.

The exact format of supported requests is defined in the API Reference documentation. 

### Transactional Behavior {#transactional-behavior}

All requests are atomic.

This means that subsequent (`write`) requests cannot be combined into a single transaction that could succeed or fail as a single entity.

### Security {#security}

If the Assets REST API is used within an environment without specific authentication requirements, AEM's CORS filter needs to be configured correctly.

>[!NOTE]
>
>For further information see:
>
>* CORS/AEM explained
>* Video - Developing for CORS with AEM

In environments with specific authentication requirements, OAuth is recommended.

## Available Features {#available-features}

Content Fragments are a specific type of Asset, see Working with Content Fragments.

For further information about features available through the API see:

* The Assets REST API (Additional Resources) 
* Entity Types, where the features specific to each supported type (as relevant to Content Fragments) are explained 

### Paging {#paging}

The Assets REST API supports paging (for GET requests) via the URL parameters:

* `offset` - the number of the first (child) entity to retrieve
* `limit` - the maximum number of entities returned

The response will contain paging information as part of the `properties` section of the SIREN output. This `srn:paging` property contains the total number of (child) entities ( `total`), the offset and the limit ( `offset`, `limit`) as specified in the request.

>[!NOTE]
>
>Paging is typically applied on container entities (i.e. folders or assets with renditions), as it relates to the children of the requested entity.

#### Example: Paging {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```json
...
"properties": {
    ...
    "srn:paging": {
        "total": 7,
        "offset": 2,
        "limit": 3
    }
    ...
}
...
```

## Entity Types {#entity-types}

### Folders {#folders}

Folders act as containers for assets and other folders. They reflect the structure of the AEM content repository.

The Assets REST API exposes access to the properties of a folder; for example its name, title, etc. Assets are exposed as child entities of folders, and sub-folders.

>[!NOTE]
>
>Depending on the asset type of the child assets and folders the list of child entities may already contain the full set of properties that defines the respective child entity. Alternatively, only a reduced set of properties may be exposed for an entity in this list of child entities.

### Assets {#assets}

If an asset is requested, the response will return its metadata; such as title, name and other information as defined by the respective asset schema.

The binary data of an asset is exposed as a SIREN link of type `content`.

Assets can have multiple renditions. These are typically exposed as child entities, one exception being a thumbnail rendition, which is exposed as a link of type `thumbnail` ( `rel="thumbnail"`).
-->

## 자산 HTTP API 및 콘텐츠 조각 {#assets-http-api-content-fragments}

컨텐츠 조각은 헤드리스 전달에 사용되며 컨텐츠 조각은 특별한 유형의 자산입니다. 텍스트, 숫자, 날짜 등 구조화된 데이터에 액세스하는 데 사용됩니다.

<!--
As there are several differences to *standard* assets (such as images or audio), some additional rules apply to handling them.

### Representation {#representation}

Content fragments:

* Do not expose any binary data.
* Are completely contained in the JSON output (within the `properties` property).

* Are also considered atomic, i.e. the elements and variations are exposed as part of the fragment's properties vs. as links or child entities. This allows for efficient access to the payload of a fragment.

### Content Models and Content Fragments {#content-models-and-content-fragments}

Currently the models that define the structure of a content fragment are not exposed through an HTTP API. Therefore the *consumer* needs to know about the model of a fragment (at least a minimum) - although most information can be inferred from the payload; as data types, etc. are part of the definition.

To create a new content fragment, the (internal repository) path of the model has to be provided.

### Associated Content {#associated-content}

Associated content is currently not exposed.
-->

## 자산 REST API 사용 {#using-aem-assets-rest-api}

### 액세스 {#access}

자산 REST API는 `/api/assets` 끝점을 사용하며, 이 끝점에 액세스하려면 자산의 경로가 필요합니다(맨 앞의 `/content/dam` 없이).

* 즉, 다음 위치에서 자산에 액세스합니다.
   * `/content/dam/path/to/asset`
* 다음을 요청해야 합니다.
   * `/api/assets/path/to/asset`

예를 들어 `/content/dam/wknd/en/adventures/cycling-tuscany`에 액세스하려면 `/api/assets/wknd/en/adventures/cycling-tuscany.json` 요청을 하십시오.

>[!NOTE]
>액세스 권한:
>
>* `/api/assets` **을** 사용하지 않아도  `.model` 됩니다.
>* `/content/path/to/page` **선택기** 를 사용해야  `.model` 합니다.


### 작업 {#operation}

HTTP 메서드는 실행할 작업을 결정합니다.

* **GET**  - 에셋 또는 폴더의 JSON 표현 가져오기
* **POST**  - 새 에셋 또는 폴더 만들기
* **PUT**  - 자산 또는 폴더의 속성을 업데이트하는 방법
* **DELETE**  - 자산 또는 폴더 삭제

>[!NOTE]
>
>요청 본문 및/또는 URL 매개 변수를 사용하여 이러한 작업 중 일부를 구성할 수 있습니다.예를 들어 **POST** 요청에 의해 폴더 또는 자산을 만들어야 함을 정의합니다.

지원되는 요청의 정확한 형식은 API 참조 설명서에 정의되어 있습니다.

AEM 작성자 환경을 사용하는지 게시 환경을 사용하는지에 따라 특정 사용 사례와 함께 사용법이 다를 수 있습니다.

* 만들기는 작성자 인스턴스에 바인딩되는 것이 좋습니다(현재 이 API를 사용하여 게시할 조각을 복제할 방법이 없습니다).
* AEM은 요청된 컨텐츠를 JSON 형식으로만 제공하므로 두 가지 방식 모두에서 전달할 수 있습니다.

   * AEM 작성 인스턴스에서 저장 및 전달하면 방화벽 뒤의 미디어 라이브러리 애플리케이션에 충분해야 합니다.

   * 라이브 웹 전달의 경우 AEM 게시 인스턴스가 권장됩니다.

>[!CAUTION]
>
>AEM 클라우드 인스턴스의 디스패처 구성은 `/api`에 대한 액세스를 차단할 수 있습니다.

>[!NOTE]
>
>자세한 내용은 API 참조를 참조하십시오. 특히 [Adobe Experience Manager Assets API - 콘텐츠 조각](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/assets-api-content-fragments/index.html).

### 읽기/배달 {#read-delivery}

사용 방법:

`GET /{cfParentPath}/{cfName}.json`

예:

`http://<host>/api/assets/wknd/en/adventures/cycling-tuscany.json`

응답은 컨텐츠 조각에서와 같이 구조화된 컨텐츠와 함께 JSON에 직렬화됩니다. 참조는 참조 URL로 제공됩니다.

두 가지 유형의 읽기 작업이 가능합니다.

* 경로별로 특정 컨텐츠 조각을 읽으면 컨텐츠 조각의 JSON 표현을 반환합니다.
* 경로별로 컨텐츠 조각 폴더 읽기:폴더 내의 모든 컨텐츠 조각에 대한 JSON 표현을 반환합니다.

### 만들기 {#create}

사용 방법:

`POST /{cfParentPath}/{cfName}`

본문에는 컨텐츠 조각 요소에 설정되어야 하는 초기 컨텐츠를 포함하여 작성할 컨텐츠 조각에 대한 JSON 표현이 포함되어야 합니다. `cq:model` 속성을 설정해야 하며 올바른 컨텐츠 조각 모델을 가리켜야 합니다. 그렇게 하지 않으면 오류가 발생합니다. 또한 `application/json`으로 설정된 헤더 `Content-Type`을 추가해야 합니다.

### 업데이트 {#update}

사용 방법은

`PUT /{cfParentPath}/{cfName}`

본문에는 주어진 컨텐츠 조각에 대해 업데이트할 JSON 표현을 포함해야 합니다.

컨텐츠 조각 또는 단일 요소 또는 모든 요소 값 및/또는 메타데이터의 제목 또는 설명일 수 있습니다.

### 삭제 {#delete}

사용 방법:

`DELETE /{cfParentPath}/{cfName}`

AEM Assets REST API 사용에 대한 자세한 내용은 다음을 참조할 수 있습니다.

* Adobe Experience Manager Assets HTTP API(추가 리소스)
* AEM Assets HTTP API의 컨텐츠 조각 지원(추가 리소스)

## 다음 {#whats-next} 소개

AEM 헤드리스 개발자 여정의 이 부분을 완료하셨다면 다음을 수행해야 합니다.

* AEM Assets HTTP API의 기본 사항을 이해합니다.
* 이 API에서 컨텐츠 조각이 지원되는 방식을 이해합니다.

<!--
* Have experience with sample code and know how the API works in practice.
-->

AEM 헤드리스 프로젝트를 사용하고 라이브할 준비를 하는 방법을 배울 수 있는 AEM Headless](put-it-all-together.md) 문서의 [모두 함께 놓는 방법 - 앱과 귀하의 컨텐츠를 차례로 검토하여 AEM 헤드리스 여정을 계속 진행해야 합니다.

[AEM을 사용하여 단일 페이지 애플리케이션(SPA)을 만드는 방법](create-spa.md) 은 AEM Editor 프레임워크를 사용하여 편집 가능한 SPA을 만들고 외부 SPA을 통합하여 필요에 따라 편집 기능을 활성화하는 방법을 보여줍니다.

## 추가 리소스 {#additional-resources}

* [자산 HTTP API](/help/assets/mac-api-assets.md)
* [컨텐츠 조각 REST API](/help/assets/content-fragments/assets-api-content-fragments.md)
   * [API 참조](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference)
* [Adobe Experience Manager Assets API - 콘텐츠 조각](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/assets-api-content-fragments/index.html)
* [콘텐츠 조각을 사용한 작업](/help/assets/content-fragments/content-fragments.md)
* [AEM 핵심 구성 요소](https://docs.adobe.com/content/help/ko/experience-manager-core-components/using/introduction.html)
* [CORS/AEM 설명](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [비디오 - AEM을 사용한 CORS 개발](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

