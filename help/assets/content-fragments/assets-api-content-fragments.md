---
title: Assets HTTP API의 Adobe Experience Manager as a Cloud Service 콘텐츠 조각 지원
description: Adobe Experience Manager의 Headless 게재 기능의 중요한 부분인 Assets HTTP API에서의 콘텐츠 조각 지원에 대해 알아봅니다.
feature: Content Fragments, Assets HTTP API
exl-id: d72cc0c0-0641-4fd6-9f87-745af5f2c232
role: User, Admin
source-git-commit: 04d1f4f312c9cd256430a2134b308e45dde2c4d7
workflow-type: tm+mt
source-wordcount: '1859'
ht-degree: 14%

---

# AEM Assets HTTP API의 콘텐츠 조각 지원 {#content-fragments-support-in-aem-assets-http-api}

## 개요 {#overview}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/extending/assets-api-content-fragments.html) |
| AEM as a Cloud Service | 이 문서 |

>[!CAUTION]
>
>Assets HTTP API의 콘텐츠 조각 지원이 이제 [사용되지 않음](/help/release-notes/deprecated-removed-features.md)입니다.
>
>[콘텐츠 조각 및 콘텐츠 조각 모델 관리 OpenAPI](/help/headless/content-fragment-openapis.md)와 함께 [OpenAPI를 통한 콘텐츠 조각 배달](/help/headless/aem-content-fragment-delivery-with-openapi.md)로 대체되었습니다.

Adobe Experience Manager(AEM) Headless 전달 기능의 중요한 부분인 Assets HTTP API의 콘텐츠 조각에 대한 지원에 대해 알아봅니다.

>[!NOTE]
>
>사용 가능한 다양한 API에 대한 개요와 관련된 몇 가지 개념의 비교는 [구조화된 컨텐츠 배달 및 관리를 위한 AEM API](/help/headless/apis-headless-and-content-fragments.md)를 참조하십시오.
>
>[콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)도 사용하실 수 있습니다.

>[!NOTE]
>
>[Assets HTTP API](/help/assets/mac-api-assets.md)는 다음을 포함합니다.
>
>* Assets REST API
>* 콘텐츠 조각의 지원 포함
>
>Assets HTTP API의 현재 구현은 [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) 아키텍처 스타일을 기반으로 합니다.

>[!NOTE]
>
>Experience Manager API에 대한 최신 정보는 [Adobe Experience Manager as a Cloud Service API](https://developer.adobe.com/experience-cloud/experience-manager-apis/)를 참조하십시오.

[Assets REST API](/help/assets/mac-api-assets.md)를 사용하면 Adobe Experience Manager as a Cloud Service의 개발자가 CRUD(만들기, 읽기, 업데이트, 삭제) 작업을 통해 HTTP API를 통해 직접 콘텐츠(AEM에 저장됨)에 액세스할 수 있습니다.

API를 사용하면 Adobe Experience Manager as a Cloud Service 프론트엔드 애플리케이션에 컨텐츠 서비스를 제공하여 JavaScript as a headless CMS(컨텐츠 관리 시스템)를 운영할 수 있습니다. 또는 HTTP 요청을 실행하고 JSON 응답을 처리할 수 있는 다른 모든 애플리케이션.

예를 들어 프레임워크 기반 또는 사용자 지정 [SPA(단일 페이지 애플리케이션)](/help/implementing/developing/hybrid/introduction.md)에는 HTTP API를 통해 제공되는 콘텐츠(종종 JSON 형식)가 필요합니다.

[AEM 핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)는 이러한 목적에 필요한 읽기 작업을 수행하고 JSON 출력을 사용자 지정할 수 있는 사용자 지정 가능한 API를 제공하지만, 구현을 위해 AEM WCM(웹 콘텐츠 관리) 노하우가 필요합니다. 전용 AEM 템플릿을 기반으로 하는 페이지에서 호스팅해야 하기 때문입니다. 모든 SPA 개발 조직에서 이러한 지식을 직접 액세스할 수 있는 것은 아닙니다.

이때 Assets REST API를 사용할 수 있습니다. 이를 통해 개발자는 페이지에 에셋을 먼저 임베드할 필요 없이 에셋(예: 이미지 및 콘텐츠 조각)에 직접 액세스하고 콘텐츠를 직렬화된 JSON 형식으로 전달할 수 있습니다.

>[!NOTE]
>
>Assets REST API에서 JSON 출력을 사용자 정의할 수 없습니다.

Assets REST API를 사용하면 개발자가 기존 에셋, 콘텐츠 조각 및 폴더를 새로 만들거나 업데이트하거나 삭제하여 콘텐츠를 수정할 수도 있습니다.

Assets REST API:

* [HATEOAS 원칙](https://en.wikipedia.org/wiki/HATEOAS)을 따릅니다.

* [SIREN 형식](https://github.com/kevinswiber/siren)을 구현합니다.

## 사전 요구 사항 {#prerequisites}

Assets REST API는 기본적으로 제공되는 최신 Adobe Experience Manager as a Cloud Service 버전 설치에서 사용할 수 있습니다.

## 주요 개념 {#key-concepts}

Assets REST API는 AEM 인스턴스 내에 저장된 자산에 대한 [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) 스타일 액세스를 제공합니다.

`/api/assets` 끝점을 사용하며 자산 경로를 사용하여 액세스합니다(선행 `/content/dam` 없음).

* 즉, 다음 위치에서 자산에 액세스할 수 있습니다.
   * `/content/dam/path/to/asset`
* 요청:
   * `/api/assets/path/to/asset`

예를 들어 `/content/dam/wknd/en/adventures/cycling-tuscany`에 액세스하기 위해 `/api/assets/wknd/en/adventures/cycling-tuscany.json`을 요청합니다.

>[!NOTE]
>다음을 통한 액세스:
>
>* `/api/assets`는 `.model` 선택기 사용이 필요하지 **않습니다**.
>* `/content/path/to/page`는 `.model` 선택기 사용이 필요&#x200B;**합니다**.

HTTP 메서드는 실행할 작업을 결정합니다.

* **GET** - 자산 또는 폴더의 JSON 표현식 검색
* **POST** - 에셋 또는 폴더를 만들려면
* **PUT** - 자산 또는 폴더의 속성 업데이트
* **DELETE** - 자산 또는 폴더 삭제

>[!NOTE]
>
>요청 본문 및/또는 URL 매개변수를 사용하여 해당 작업 중 일부를 구성할 수 있습니다(예: **POST** 요청에 의해 폴더 또는 자산이 생성될 수 있도록 정의).

지원되는 요청의 정확한 형식은 [API 참조](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference) 설명서에 정의되어 있습니다.

>[!NOTE]
>
>[콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)도 사용하실 수 있습니다.

### 트랜잭션 동작 {#transactional-behavior}

모든 요청은 원자입니다.

즉, 후속(`write`) 요청은 단일 엔터티로 성공하거나 실패할 수 있는 단일 트랜잭션으로 결합할 수 없습니다.

### AEM(Assets) REST API 및 AEM 구성 요소 {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>측면</td>
   <td>Assets REST API<br/> </td>
   <td>AEM 구성 요소<br/>(Sling 모델을 사용하는 구성 요소)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>지원되는 사용 사례</td>
   <td>일반적인 목적.</td>
   <td><p>SPA(단일 페이지 애플리케이션) 또는 기타(콘텐츠 소비) 컨텍스트에서 사용을 위해 최적화되었습니다.</p> <p>레이아웃 정보를 포함할 수도 있습니다.</p> </td>
  </tr>
  <tr>
   <td>지원되는 작업</td>
   <td><p>만들기, 읽기, 업데이트, 삭제.</p> <p>엔터티 유형에 따라 추가 작업을 사용할 수 있습니다.</p> </td>
   <td>읽기 전용.</td>
  </tr>
  <tr>
   <td>액세스</td>
   <td><p>바로 액세스할 수 있습니다.</p> <p>리포지토리의 <code>/content/dam</code>에 매핑된 <code>/api/assets </code>끝점을 사용합니다.</p> 
   <p>예제 경로는 다음과 같습니다. <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>AEM 페이지에서 AEM 구성 요소를 통해 참조해야 합니다.</p> <p><code>.model</code> 선택기를 사용하여 JSON 표현을 만듭니다.</p> <p>예제 경로는 다음과 같습니다.<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>보안</td>
   <td><p>여러 옵션이 가능합니다.</p> <p>OAuth가 제안되며, 표준 설정과 별도로 구성할 수 있습니다.</p> </td>
   <td>AEM의 표준 설정을 사용합니다.</td>
  </tr>
  <tr>
   <td>아키텍처 설명</td>
   <td><p>쓰기 액세스는 일반적으로 작성자 인스턴스를 해결합니다.</p> <p>읽기는 게시 인스턴스로 진행될 수도 있습니다.</p> </td>
   <td>이 접근 방식은 읽기 전용이므로 일반적으로 게시 인스턴스에 사용됩니다.</td>
  </tr>
  <tr>
   <td>출력</td>
   <td>JSON 기반 SIREN 출력: 자세한 정보지만 강력한. 콘텐츠 내를 탐색할 수 있습니다.</td>
   <td>JSON 기반 소유 출력, Sling 모델을 통해 구성 가능. 콘텐츠 구조를 탐색하는 것은 구현하기 어렵습니다(하지만 반드시 불가능하지는 않음).</td>
  </tr>
 </tbody>
</table>

### 보안 {#security}

Assets REST API를 특정 인증 요구 사항 없이 환경 내에서 사용하는 경우 AEM의 CORS 필터를 올바르게 구성해야 합니다.

>[!NOTE]
>
>자세한 내용은 다음을 참조하십시오.
>
>* [CORS/AEM 설명](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html)
>* [비디오 - AEM을 사용하여 CORS용 개발(04:06)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/develop-for-cross-origin-resource-sharing.html)
>

특정 인증 요구 사항이 있는 환경에서는 OAuth가 권장됩니다.

## 사용 가능한 기능 {#available-features}

콘텐츠 조각은 특정 유형의 자산입니다. [콘텐츠 조각을 사용하여 작업](/help/assets/content-fragments/content-fragments.md)을 참조하세요.

API를 통해 사용할 수 있는 기능에 대한 자세한 내용은 다음을 참조하십시오.

* [Assets REST API](/help/assets/mac-api-assets.md)
* [엔터티 형식](/help/assets/content-fragments/assets-api-content-fragments.md#entity-types)(지원되는 각 형식과 관련된 기능(콘텐츠 조각과 관련된 기능) 설명)

>[!NOTE]
>
>[콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)도 사용하실 수 있습니다.

### 페이징 {#paging}

Assets REST API는 URL 매개 변수를 통해 (GET 요청에 대한) 페이징을 지원합니다.

* `offset` - 검색할 첫 번째(하위) 엔티티 수
* `limit` - 반환되는 최대 엔터티 수

응답에 SIREN 출력의 `properties` 섹션의 일부로 페이징 정보가 포함되어 있습니다. 이 `srn:paging` 속성에는 요청에 지정된 총 (하위) 엔티티 수(`total`), 오프셋 및 제한(`offset`, `limit`)이 포함됩니다.

>[!NOTE]
>
>페이징은 요청된 엔티티의 하위 항목과 관련이 있으므로 일반적으로 컨테이너 엔티티(렌디션이 있는 폴더 또는 에셋)에 적용됩니다.

#### 예: 페이징 {#example-paging}

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

## 엔티티 유형 {#entity-types}

### 폴더 {#folders}

폴더는 에셋 및 기타 폴더의 컨테이너 역할을 합니다. 이는 AEM 콘텐츠 저장소의 구조를 반영합니다.

Assets REST API는 폴더의 속성에 대한 액세스를 노출합니다. (예: 이름 및 제목) Assets은 폴더 및 하위 폴더의 하위 엔티티로 노출됩니다.

>[!NOTE]
>
>하위 에셋 및 폴더의 에셋 유형에 따라 하위 엔티티 목록에는 각 하위 엔티티를 정의하는 전체 속성 세트가 이미 포함되어 있을 수 있습니다. 대안적으로, 이러한 자식 엔티티들의 목록에 있는 엔티티에 대해 감소된 속성 세트만이 노출될 수 있다.

### 자산 {#assets}

에셋이 요청되면 응답은 제목, 이름 및 각 에셋 스키마에서 정의한 기타 정보와 같은 메타데이터를 반환합니다.

자산의 이진 데이터가 `content` 유형의 SIREN 링크로 노출됩니다.

Assets에는 여러 표현물이 있을 수 있습니다. 일반적으로 자식 엔터티로 노출됩니다. 한 가지 예외는 썸네일 렌디션으로, `thumbnail`(`rel="thumbnail"`) 형식의 링크로 노출됩니다.

### 콘텐츠 조각 {#content-fragments}

[콘텐츠 조각](/help/assets/content-fragments/content-fragments.md)은(는) 특별한 유형의 자산입니다. 텍스트, 숫자, 날짜 등 구조화된 데이터에 액세스하는 데 사용할 수 있습니다.

*표준* 자산(예: 이미지 또는 오디오)에 몇 가지 차이점이 있으므로 이를 처리하는 데 일부 추가 규칙이 적용됩니다.

#### 표시 {#representation}

컨텐츠 조각:

* 이진 데이터를 노출하지 마십시오.
* JSON 출력(`properties` 속성 내)에 포함되어 있습니다.

* 그들은 또한 원자로도 간주된다. 즉, 요소 및 변형은 조각의 속성 또는 링크 또는 하위 엔티티의 일부로 노출됩니다. 이를 통해 조각의 페이로드에 효율적으로 액세스할 수 있습니다.

#### 콘텐츠 모델 및 콘텐츠 조각 {#content-models-and-content-fragments}

현재 콘텐츠 조각의 구조를 정의하는 모델은 HTTP API를 통해 노출되지 않습니다. 따라서 *consumer*&#x200B;은(는) 페이로드에서 대부분의 정보를 유추할 수 있지만, 데이터 형식 등은 정의의 일부입니다.

콘텐츠 조각을 만들려면 모델의 (내부 저장소) 경로를 제공해야 합니다.

#### 관련 콘텐츠 {#associated-content}

연결된 콘텐츠가 노출되지 않았습니다.

## 사용 {#using}

특정 사용 사례와 함께 AEM 작성자 또는 게시 환경을 사용하는지에 따라 사용 방식이 다를 수 있습니다.

* 만들기는 작성자 인스턴스([)에 바인딩되는 것이 좋습니다. 현재 이 API를 사용하여 게시할 조각을 복제할 방법이 없습니다](/help/assets/content-fragments/assets-api-content-fragments.md#limitations).
* AEM은 JSON 형식으로만 요청된 콘텐츠를 제공하므로 모두에서 게재할 수 있습니다.

   * AEM 작성자 인스턴스의 저장 및 제공은 방화벽 뒤 미디어 라이브러리 애플리케이션이면 충분합니다.

   * 라이브 웹 게재의 경우 AEM 게시 인스턴스가 권장됩니다.

>[!CAUTION]
>
>AEM 클라우드 인스턴스의 Dispatcher 구성으로 인해 `/api`에 대한 액세스가 차단될 수 있습니다.

>[!NOTE]
>
>[API 참조](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference)를 참조하십시오. 특히, [Adobe Experience Manager Assets API - 콘텐츠 조각](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html).
>
>[콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)도 사용하실 수 있습니다.

## 제한 사항 {#limitations}

몇 가지 제한 사항이 있습니다.

* **콘텐츠 조각 모델은 현재 지원되지 않습니다**: 읽거나 만들 수 없습니다. 기존 콘텐츠 조각을 만들거나 업데이트하려면 개발자는 콘텐츠 조각 모델에 대한 올바른 경로를 알고 있어야 합니다. 현재 이러한 기능에 대한 개요를 얻는 유일한 방법은 관리 UI를 사용하는 것입니다.
* **참조가 무시됩니다**. 현재 기존 콘텐츠 조각이 참조되는지 여부에 대한 검사가 없습니다. 따라서 예를 들어 콘텐츠 조각을 삭제하면 삭제된 콘텐츠 조각에 대한 참조가 포함된 페이지에 문제가 발생할 수 있습니다.
* **JSON 데이터 형식** *JSON 데이터 형식*&#x200B;의 REST API 출력은 *문자열 기반 출력*&#x200B;입니다.

## 상태 코드 및 오류 메시지 {#status-codes-and-error-messages}

관련 상황에서 다음 상태 코드를 볼 수 있습니다.

* **200**(확인)

  다음과 같은 경우에 반환됨:

   * `GET`을(를) 통해 콘텐츠 조각 요청
   * `PUT`을(를) 통해 콘텐츠 조각을 업데이트했습니다.

* **201**(생성됨)

  다음과 같은 경우에 반환됨:

   * `POST`을(를) 통해 콘텐츠 조각을 만들었습니다.

* **404**(찾을 수 없음)

  다음과 같은 경우에 반환됨:

   * 요청한 콘텐츠 조각이 존재하지 않습니다.

* **500**(내부 서버 오류)

  >[!NOTE]
  >
  >이 오류가 반환됩니다.
  >
  >* 특정 코드로 식별할 수 없는 오류가 발생한 경우
  >* 지정된 페이로드가 유효하지 않은 경우

  다음은 생성된 오류 메시지(단공간)와 함께 이 오류 상태가 반환될 때의 일반적인 시나리오를 나열합니다.

   * 상위 폴더가 없습니다(`POST`을(를) 통해 콘텐츠 조각을 만드는 경우).
   * 제공된 콘텐츠 조각 모델이 없거나(cq:model이 누락됨), 잘못된 경로 또는 권한 문제로 인해 읽을 수 없거나, 유효한 조각 모델이 없습니다.

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`

   * 콘텐츠 조각을 만들 수 없습니다(권한 문제일 수 있음).

      * `Could not create content fragment`

   * 제목 및/또는 설명을 업데이트할 수 없습니다.

      * `Could not set value on content fragment`

   * 메타데이터를 설정할 수 없음:

      * `Could not set metadata on content fragment`

   * 콘텐츠 요소를 찾을 수 없거나 업데이트할 수 없습니다.

      * `Could not update content element`
      * `Could not update fragment data of element`

  자세한 오류 메시지는 다음과 같은 방식으로 반환됩니다.

  ```xml
  {
    "class": "core/response",
    "properties": {
      "path": "/api/assets/foo/bar/qux",
      "location": "/api/assets/foo/bar/qux.json",
      "parentLocation": "/api/assets/foo/bar.json",
      "status.code": 500,
      "status.message": "...{error message}.."
    }
  }
  ```

## API 참조 {#api-reference}

자세한 API 참조는 여기를 참조하십시오.

* [Adobe Experience Manager Assets API - 콘텐츠 조각](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html)

* [Assets HTTP API](/help/assets/mac-api-assets.md)

   * [사용 가능한 기능](/help/assets/mac-api-assets.md#available-features)

* [콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)도 사용하실 수 있습니다.

## 추가 리소스 {#additional-resources}

자세한 내용은 다음 문서를 참조하십시오.

* [Assets HTTP API 설명서](/help/assets/mac-api-assets.md)
* [AEM Gem 세션: OAuth](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2014/aem-oauth-server-functionality-in-aem.html)
