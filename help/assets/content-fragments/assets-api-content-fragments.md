---
title: 자산 HTTP API에서 Cloud Service 컨텐츠 조각 지원으로서의 Adobe Experience Manager
description: 자산 HTTP API의 Cloud Service 컨텐츠 조각 지원으로서 Adobe Experience Manager에 대해 학습합니다.
translation-type: tm+mt
source-git-commit: 8aa2585e85b0ed23d68597857cda09dc301df4f6
workflow-type: tm+mt
source-wordcount: '1891'
ht-degree: 2%

---


# AEM Assets HTTP API의 컨텐츠 조각 지원{#content-fragments-support-in-aem-assets-http-api}

## 개요 {#overview}

>[!NOTE]
>
>자산 [HTTP API는](/help/assets/mac-api-assets.md) 다음을 포함합니다.
>
>* 자산 REST API
>* 컨텐츠 조각 지원 포함

>
>
에셋 HTTP API의 현재 구현은 [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) 아키텍처 스타일을 기반으로 합니다.

Assets REST API를 [](/help/assets/mac-api-assets.md) 사용하면 Cloud Service의 개발자는 CRUD 작업(만들기, 읽기, 업데이트, 삭제)을 통해 HTTP API를 통해 직접 AEM에 저장된 컨텐츠에 액세스할 수 있습니다.

API를 사용하면 JavaScript 프런트 엔드 애플리케이션에 컨텐츠 서비스를 제공하여 Adobe Experience Manager을 헤드리스 CMS(Content Management System)로 Cloud Service으로 운영할 수 있습니다. 또는 HTTP 요청을 실행하고 JSON 응답을 처리할 수 있는 기타 애플리케이션입니다.

예를 들어, 단일 페이지 애플리케이션(SPA), 프레임워크 기반 또는 사용자 정의 등은 HTTP API를 통해 제공되는 컨텐츠가 종종 JSON 형식으로 필요합니다.

AEM [코어 구성](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html) 요소는 이러한 목적으로 필요한 읽기 작업을 제공할 수 있고 JSON 출력을 사용자 정의할 수 있는 매우 포괄적이고 유연하며 사용자 정의 가능한 API를 제공하지만 전용 AEM 템플릿을 기반으로 하는 페이지에서 호스팅되어야 하는 AEM WCM(Web Content Management) 구현에 대한 노하우가 필요합니다. 모든 SPA 개발 조직이 이러한 지식을 직접 이용하고 있는 것은 아닙니다.

이것은 자산 REST API를 사용할 수 있는 때입니다. 이를 통해 개발자는 에셋(예: 이미지 및 컨텐츠 조각)을 페이지에 먼저 임베드하여 JSON 포맷으로 컨텐츠를 전달할 필요 없이 직접 액세스할 수 있습니다.

>[!NOTE]
>
>자산 REST API에서 JSON 출력을 사용자 지정할 수 없습니다.

또한 Assets REST API를 사용하면 개발자는 기존 자산, 컨텐츠 조각 및 폴더를 새로 만들거나, 업데이트하거나, 삭제하여 컨텐츠를 수정할 수 있습니다.

자산 REST API:

* HATEOAS [원칙을 따릅니다.](https://en.wikipedia.org/wiki/HATEOAS)

* 사이렌 [형식 구현](https://github.com/kevinswiber/siren)

## 전제 조건 {#prerequisites}

Assets REST API는 최신 Adobe Experience Manager을 Cloud Service 버전으로 즉시 설치할 때마다 사용할 수 있습니다.

## 주요 개념 {#key-concepts}

자산 REST API는 AEM 인스턴스 [에](https://en.wikipedia.org/wiki/Representational_state_transfer)저장된 자산에 대한 REST 스타일 액세스를 제공합니다.

끝점을 사용하고 `/api/assets` 자산의 경로가 있어야 합니다(맨 앞에 있지 `/content/dam`않음).

* 이것은 다음 위치에서 자산에 액세스하는 것을 의미합니다.
   * `/content/dam/path/to/asset`
* 다음을 요청해야 합니다.
   * `/api/assets/path/to/asset`

예를 들어, 액세스하려면 `/content/dam/wknd/en/adventures/cycling-tuscany`요청 `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>액세스 권한:
>* `/api/assets` **은** 선택기를 사용할 필요가 `.model` 없습니다.
>* `/content/path/to/page` **을** 사용하려면 선택기를 `.model` 사용해야 합니다.


HTTP 메서드는 실행할 작업을 결정합니다.

* **GET** - 자산 또는 폴더의 JSON 표현을 검색하기
* **POST** - 새 자산 또는 폴더를 만들려면
* **PUT** - 자산 또는 폴더의 속성을 업데이트하려면
* **DELETE** - 자산 또는 폴더 삭제

>[!NOTE]
>
>요청 본문 및/또는 URL 매개 변수를 사용하여 이러한 작업 중 일부를 구성할 수 있습니다.예를 들어 폴더 또는 자산을 **POST** 요청에 의해 만들어야 함을 정의합니다.

<!--
The exact format of supported requests is defined in the [API Reference](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference) documentation.
-->

### 트랜잭션 동작 {#transactional-behavior}

모든 요청은 원자이다.

즉, 후속(`write`) 요청은 단일 엔티티로 성공하거나 실패할 수 있는 단일 트랜잭션으로 결합할 수 없습니다.

### AEM(자산) REST API와 AEM 구성 요소 {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>종횡비</td>
   <td>자산 REST API<br/> </td>
   <td>AEM 구성 요소<br/> (슬링 모델을 사용한 구성 요소)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>지원되는 사용 사례</td>
   <td>일반적인 목적</td>
   <td><p>단일 페이지 애플리케이션(SPA) 또는 기타 모든(컨텐츠 소비) 컨텍스트에서의 사용을 위해 최적화되었습니다.</p> <p>레이아웃 정보를 포함할 수도 있습니다.</p> </td>
  </tr>
  <tr>
   <td>지원되는 작업</td>
   <td><p>만들기, 읽기, 업데이트, 삭제</p> <p>엔티티 유형에 따라 추가 작업이 있는 경우.</p> </td>
   <td>읽기 전용.</td>
  </tr>
  <tr>
   <td>액세스</td>
   <td><p>직접 액세스할 수 있습니다.</p> <p>저장소에 매핑된 <code>/api/assets </code>끝점을 <code>/content/dam</code> 사용합니다.</p> 
   <p>예제 경로는 다음과 같습니다. <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>AEM 페이지의 AEM 구성 요소를 통해 참조되어야 합니다.</p> <p>선택기를 <code>.model</code> 사용하여 JSON 표현을 만듭니다.</p> <p>예제 경로는 다음과 같습니다.<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>보안</td>
   <td><p>여러 가지 옵션이 가능합니다.</p> <p>OAuth가 제안됨;표준 설정과 별도로 구성할 수 있습니다.</p> </td>
   <td>AEM 표준 설정을 사용합니다.</td>
  </tr>
  <tr>
   <td>건축주의</td>
   <td><p>쓰기 액세스는 일반적으로 작성자 인스턴스를 처리합니다.</p> <p>또한 읽기가 게시 인스턴스로 연결될 수도 있습니다.</p> </td>
   <td>이 방법은 읽기 전용이므로 일반적으로 게시 인스턴스에 사용됩니다.</td>
  </tr>
  <tr>
   <td>출력</td>
   <td>JSON 기반의 SYNN 출력:장황하지만 강력합니다. 컨텐츠 내에서 탐색할 수 있습니다.</td>
   <td>JSON 기반의 독점 출력;Sling Models를 통해 구성 가능합니다. 콘텐츠 구조를 탐색하는 것은 구현하기가 어렵습니다(하지만 반드시 불가능한 것은 아닙니다).</td>
  </tr>
 </tbody>
</table>

### 보안 {#security}

특정 인증 요구 사항이 없는 환경에서 자산 REST API를 사용하는 경우 AEM CORS 필터를 올바르게 구성해야 합니다.

>[!NOTE]
>
>자세한 내용은 다음을 참조하십시오.
>
>* [CORS/AEM 설명](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
>* [비디오 - AEM에서 CORS를 위한 개발](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

>



특정 인증 요구 사항이 있는 환경에서는 OAuth가 권장됩니다.

## 사용 가능한 기능 {#available-features}

컨텐츠 조각은 자산의 특정 유형입니다. 컨텐츠 조각 [작업을 참조하십시오](/help/assets/content-fragments/content-fragments.md).

API를 통해 사용할 수 있는 기능에 대한 자세한 내용은 다음을 참조하십시오.

* 자산 [REST API](/help/assets/mac-api-assets.md)
* [엔티티 유형](/help/assets/content-fragments/assets-api-content-fragments.md#entity-types). 여기서 지원되는 각 유형별(컨텐츠 조각과 관련) 기능이 설명됩니다.

### 페이징 {#paging}

자산 REST API는 URL 매개 변수를 통해 페이징(GET 요청)을 지원합니다.

* `offset` - 검색할 첫 번째(하위) 엔티티 수
* `limit` - 반환된 최대 개체 수

응답에는 SYNN 출력 섹션의 일부로서 페이징 정보가 `properties` 포함됩니다. 이 `srn:paging` 속성에는 요청에 지정된 총 개체 수(자식)( `total`), 오프셋 및 한도(, `offset`, `limit`)가 포함됩니다.

>[!NOTE]
>
>페이징은 요청된 엔티티의 자식과 관련이 있으므로 일반적으로 컨테이너 엔티티(즉, 폴더 또는 표현물과 자산)에 적용됩니다.

#### 예:페이징 {#example-paging}

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

폴더는 자산 및 기타 폴더의 컨테이너 역할을 합니다. AEM 컨텐츠 저장소의 구조를 반영합니다.

자산 REST API는 폴더의 속성에 대한 액세스 권한을 노출합니다.예를 들어 이름, 제목 등이 있습니다. 자산은 폴더 및 하위 폴더의 하위 엔티티로 표시됩니다.

>[!NOTE]
>
>하위 자산 및 폴더의 자산 유형에 따라 하위 엔티티 목록에는 해당 하위 엔티티를 정의하는 전체 속성 세트가 이미 포함되어 있을 수 있습니다. 또는 이 하위 엔티티 목록의 엔티티에 대해 축소된 속성 세트만 노출될 수 있습니다.

### 자산 {#assets}

자산이 요청되면 응답에서 해당 메타데이터를 반환합니다.제목, 이름 및 해당 자산 스키마에 의해 정의된 기타 정보 등.

자산의 이진 데이터는 유형의 SYNN 링크로 노출됩니다 `content`.

자산에 여러 표현물이 있을 수 있습니다. 이러한 항목은 일반적으로 하위 엔티티로 노출되며, 한 가지 예외는 축소판 변환이며 유형 `thumbnail` ( `rel="thumbnail"`)의 링크로 노출됩니다.

### 콘텐츠 조각 {#content-fragments}

컨텐츠 [조각은](/help/assets/content-fragments/content-fragments.md) 특별한 유형의 자산입니다. 텍스트, 숫자, 날짜 등 구조화된 데이터에 액세스하는 데 사용할 수 있습니다.

이미지 또는 오디오와 같은 *표준* 에셋에는 몇 가지 차이가 있으므로 처리 시 일부 추가 규칙이 적용됩니다.

#### 표현 {#representation}

컨텐츠 조각:

* 이진 데이터를 노출하지 마십시오.
* JSON 출력(속성 내)에 완전히 포함되어 `properties` 있습니다.

* 요소 및 변형이 조각 속성의 일부로, 링크 또는 하위 엔티티로 노출되는 것과 같이 원자로도 간주됩니다. 이렇게 하면 조각의 페이로드에 효율적으로 액세스할 수 있습니다.

#### 컨텐츠 모델 및 컨텐츠 조각 {#content-models-and-content-fragments}

현재 컨텐츠 조각 구조를 정의하는 모델은 HTTP API를 통해 노출되지 않습니다. 따라서 *소비자가* 페이로드에서 대부분의 정보를 유추할 수 있지만 조각(최소)의 모델에 대해 알아야 합니다.데이터 유형 등에 는 정의의 일부입니다.

새 컨텐츠 조각을 만들려면 모델의 (내부 저장소) 경로를 제공해야 합니다.

#### 관련 컨텐츠 {#associated-content}

연결된 컨텐츠는 현재 노출되지 않습니다.

## 사용 {#using}

사용 방법은 AEM 작성자 환경을 사용하는지 게시 환경을 사용하는지에 따라 특정 사용 사례와 함께 다를 수 있습니다.

* 작성은 작성자 인스턴스에 바인딩되어[있으며 현재 이 API를 사용하여 게시할 조각을 복제할 방법이 없습니다](/help/assets/content-fragments/assets-api-content-fragments.md#limitations).
* AEM은 요청된 컨텐츠를 JSON 형식으로만 제공하므로 두 가지 방식 모두에서 전달할 수 있습니다.

   * AEM 작성자 인스턴스의 저장 및 전달에는 방화벽 뒤의 미디어 라이브러리 애플리케이션이 충분합니다.

   * 라이브 웹 전달의 경우 AEM 게시 인스턴스가 권장됩니다.

>[!CAUTION]
>
>AEM 클라우드 인스턴스의 디스패처 구성이 액세스 권한을 차단할 수 `/api`있습니다.

<!--
>[!NOTE]
>
>For further details, see the [API Reference](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference). In particular, [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html). 
-->

### 읽기/전달 {#read-delivery}

사용 방법:

`GET /{cfParentPath}/{cfName}.json`

예:

`http://<host>/api/assets/wknd/en/adventures/cycling-tuscany.json`

응답은 컨텐츠 조각에서와 같이 구조화된 컨텐츠와 함께 JSON에 정리됩니다. 참조는 참조 URL로 제공됩니다.

두 가지 유형의 읽기 작업이 가능합니다.

* 특정 컨텐츠 조각을 경로별로 읽는 경우 컨텐츠 조각의 JSON 표현을 반환합니다.
* 경로별 컨텐츠 조각 폴더 읽기:폴더 내의 모든 컨텐츠 조각에 대한 JSON 표현을 반환합니다.

### 만들기 {#create}

사용 방법:

`POST /{cfParentPath}/{cfName}`

본문에는 컨텐츠 조각 요소에 설정되어야 하는 초기 컨텐츠를 포함하여 작성할 컨텐츠 조각에 대한 JSON 표현이 포함되어야 합니다. 속성을 설정해야 하며 `cq:model` 올바른 컨텐츠 조각 모델을 가리켜야 합니다. 그렇게 하지 않으면 오류가 발생합니다. 다음으로 설정된 헤더 `Content-Type` 를 추가해야 합니다 `application/json`.

### 업데이트 {#update}

사용 방법

`PUT /{cfParentPath}/{cfName}`

본문에는 주어진 컨텐츠 조각에 대해 업데이트될 JSON 표현이 포함되어야 합니다.

컨텐츠 조각, 단일 요소 또는 모든 요소 값 및/또는 메타데이터의 제목 또는 설명일 수 있습니다.

### 삭제 {#delete}

사용 방법:

`DELETE /{cfParentPath}/{cfName}`

## 제한 사항 {#limitations}

몇 가지 제한 사항이 있습니다.

* **변형은 작성하고 업데이트할 수 없습니다.** 이러한 변형을 페이로드에 추가하는 경우(예: 업데이트) 무시됩니다. 그러나 변형은 배달()을 통해 제공됩니다 `GET`.

* **컨텐츠 조각 모델은 현재 지원되지 않습니다**.읽거나 만들 수 없습니다. 개발자는 새 컨텐츠 조각을 만들거나 기존 컨텐츠 조각을 업데이트하려면 컨텐츠 조각 모델의 올바른 경로를 알아야 합니다. 현재 이러한 기능의 개요를 얻는 유일한 방법은 관리 UI를 통한 것입니다.
* **참조는 무시됩니다**. 현재 기존 컨텐츠 조각이 참조되는지 여부를 확인하지 않습니다. 예를 들어 컨텐츠 조각을 삭제하면 삭제된 컨텐츠 조각에 대한 참조가 포함된 페이지에 문제가 발생할 수 있습니다.

## 상태 코드 및 오류 메시지 {#status-codes-and-error-messages}

관련 상황에서 다음 상태 코드를 볼 수 있습니다.

* **200** (확인)

   다음 경우에 반환:

   * 컨텐츠 조각 요청 `GET`

   * 을(를) 사용하여 컨텐츠 조각을 성공적으로 업데이트 `PUT`

* **201** (작성일)

   다음 경우에 반환:

   * 을(를) 사용하여 컨텐츠 조각 만들기 `POST`

* **404** (찾을 수 없음)

   다음 경우에 반환:

   * 요청한 컨텐츠 조각이 없습니다.

* **500** (내부 서버 오류)

   >[!NOTE]
   >
   >이 오류가 반환됩니다.
   >
   >    * 특정 코드로 식별할 수 없는 오류가 발생한 경우
   >    * 지정된 페이로드가 유효하지 않은 시기


   다음은 이 오류 상태가 반환되는 일반적인 시나리오와 생성된 오류 메시지(고정 공간)를 함께 나열합니다.

   * 상위 폴더가 없습니다(다음을 통해 컨텐츠 조각을 만들 때). `POST`
   * 제공된 컨텐츠 조각 모델이 없거나(cq:model이 없습니다), 읽을 수 없거나(잘못된 경로 또는 권한 문제) 올바른 조각 모델이 없습니다.

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`
   * 콘텐츠 조각을 만들 수 없습니다(권한 문제가 있을 수 있음).

      * `Could not create content fragment`
   * 제목 및 설명을 업데이트할 수 없습니다.

      * `Could not set value on content fragment`
   * 메타데이터를 설정할 수 없습니다.

      * `Could not set metadata on content fragment`
   * 콘텐츠 요소를 찾을 수 없거나 업데이트할 수 없습니다.

      * `Could not update content element`
      * `Could not update fragment data of element`

   자세한 오류 메시지는 일반적으로 다음 방법으로 반환됩니다.

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

## API Reference {#api-reference}

자세한 API 참조는 여기를 참조하십시오.
<!--
* [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html)
-->

* [자산 HTTP API](/help/assets/mac-api-assets.md)

   * [사용 가능한 기능](/help/assets/mac-api-assets.md#available-features)

## 추가 리소스 {#additional-resources}

자세한 내용은 다음을 참조하십시오.

* [에셋 HTTP API 설명서](/help/assets/mac-api-assets.md)
* [AEM Gem 세션:OAuth](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html)

