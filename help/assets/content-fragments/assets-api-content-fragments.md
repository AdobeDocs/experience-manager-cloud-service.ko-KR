---
title: Assets HTTP API의 Adobe Experience Manager as a Cloud Service 컨텐츠 조각 지원
description: AEM 헤드리스 게재 기능의 중요한 부분인 Assets HTTP API의 컨텐츠 조각에 대한 지원에 대해 알아봅니다.
feature: Content Fragments,Assets HTTP API
exl-id: d72cc0c0-0641-4fd6-9f87-745af5f2c232
source-git-commit: cf8c8353d83e4446f52235a2ea1a322a84786b61
workflow-type: tm+mt
source-wordcount: '1761'
ht-degree: 2%

---

# AEM Assets HTTP API의 콘텐츠 조각 지원 {#content-fragments-support-in-aem-assets-http-api}

## 개요 {#overview}

AEM 헤드리스 게재 기능의 중요한 부분인 Assets HTTP API의 컨텐츠 조각에 대한 지원에 대해 알아봅니다.

>[!NOTE]
>
>다음 [자산 HTTP API](/help/assets/mac-api-assets.md) 는 다음을 포함합니다.
>
>* 자산 REST API
>* 컨텐츠 조각에 대한 지원 포함
>
>자산 HTTP API의 현재 구현은 [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) 건축 스타일.

다음 [자산 REST API](/help/assets/mac-api-assets.md) Adobe Experience Manager as a Cloud Service 개발자는 CRUD 작업(만들기, 읽기, 업데이트, 삭제)을 통해 HTTP API를 통해 직접 컨텐츠(AEM에 저장됨)에 액세스할 수 있습니다.

API를 사용하면 JavaScript 프런트 엔드 애플리케이션에 컨텐츠 서비스를 제공하여 Adobe Experience Manager as a Cloud Service을 헤드리스 CMS(Content Management System)로 운영할 수 있습니다. 또는 HTTP 요청을 실행하고 JSON 응답을 처리할 수 있는 다른 애플리케이션입니다.

예, [단일 페이지 애플리케이션(SPA)](/help/implementing/developing/hybrid/introduction.md), 프레임워크 기반 또는 사용자 지정 환경에서는 HTTP API를 통해 제공되는 컨텐츠(일반적으로 JSON 형식)가 필요합니다.

While [AEM 코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 는 이 용도로 필요한 읽기 작업을 제공할 수 있고 사용자 지정할 수 있는 매우 포괄적이고 유연한 API를 제공하며, JSON 출력을 사용자 지정할 수 있습니다. 전용 AEM 템플릿을 기반으로 하는 페이지에서 호스팅해야 하므로 구현을 위한 AEM WCM(Web Content Management) 노하우가 필요합니다. 모든 SPA 개발 조직이 이러한 지식을 직접 액세스하는 것은 아닙니다.

이때 Assets REST API를 사용할 수 있습니다. 이를 통해 개발자는 페이지에 먼저 포함할 필요 없이 자산(예: 이미지 및 컨텐츠 조각)에 직접 액세스하여 직렬화된 JSON 형식으로 콘텐츠를 제공할 수 있습니다.

>[!NOTE]
>
>Assets REST API에서 JSON 출력을 사용자 지정할 수 없습니다.

Assets REST API를 사용하면 기존 자산, 컨텐츠 조각 및 폴더를 새로 만들거나, 업데이트하거나, 삭제하여 컨텐츠를 수정할 수 있습니다.

자산 REST API:

* 다음 [HATEOAS 원칙](https://en.wikipedia.org/wiki/HATEOAS)

* 구현 [사이렌 형식](https://github.com/kevinswiber/siren)

## 사전 요구 사항 {#prerequisites}

Assets REST API는 최신 Adobe Experience Manager as a Cloud Service 버전을 바로 설치할 때마다 사용할 수 있습니다.

## 주요 개념 {#key-concepts}

자산 REST API 오퍼 [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)AEM 인스턴스 내에 저장된 자산에 대한 -style 액세스.

이 템플릿은 를 사용합니다 `/api/assets` 엔드포인트 및에 액세스할 자산의 경로가 필요합니다(선행 없이). `/content/dam`).

* 즉, 다음 위치에서 자산에 액세스합니다.
   * `/content/dam/path/to/asset`
* 다음을 요청해야 합니다.
   * `/api/assets/path/to/asset`

예를 들어, `/content/dam/wknd/en/adventures/cycling-tuscany`, 요청 `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>액세스 권한:
>
>* `/api/assets` **포함하지 않음** 의 사용 필요 `.model` 선택기.
>* `/content/path/to/page` **does** 를 사용하려면 `.model` 선택기.


HTTP 메서드는 실행할 작업을 결정합니다.

* **GET** - 자산 또는 폴더의 JSON 표현을 검색하려면
* **POST** - 새 자산 또는 폴더를 만들려면
* **PUT** - 자산 또는 폴더의 속성을 업데이트하려면
* **DELETE** - 자산 또는 폴더를 삭제하려면

>[!NOTE]
>
>요청 본문 및/또는 URL 매개 변수를 사용하여 이러한 작업 중 일부를 구성할 수 있습니다. 예를 들어, 폴더 또는 자산을 **POST** 요청.

지원되는 요청의 정확한 형식은 [API 참조](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference) 설명서.

### 트랜잭션 동작 {#transactional-behavior}

모든 요청은 원자입니다.

이것은 그 다음(`write`) 요청을 단일 엔티티로 성공하거나 실패할 수 있는 단일 트랜잭션에 결합할 수 없습니다.

### AEM(Assets) REST API와 AEM 구성 요소 {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Aspect</td>
   <td>자산 REST API<br/> </td>
   <td>AEM 구성 요소<br/> (Sling 모델을 사용한 구성 요소)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>지원되는 사용 사례</td>
   <td>일반적인 목적.</td>
   <td><p>단일 페이지 애플리케이션(SPA) 또는 기타(컨텐츠 소비) 컨텍스트에서 소비에 최적화되었습니다.</p> <p>레이아웃 정보를 포함할 수도 있습니다.</p> </td>
  </tr>
  <tr>
   <td>지원되는 작업</td>
   <td><p>작성, 읽기, 업데이트, 삭제</p> <p>엔티티 유형에 따라 추가 작업이 제공됩니다.</p> </td>
   <td>읽기 전용.</td>
  </tr>
  <tr>
   <td>액세스</td>
   <td><p>직접 액세스할 수 있습니다.</p> <p>를 사용합니다 <code>/api/assets </code>엔드포인트, 매핑 <code>/content/dam</code> (저장소에서)</p> 
   <p>예제 경로는 다음과 같습니다. <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>AEM 페이지에서 AEM 구성 요소를 통해 참조되어야 합니다.</p> <p>를 사용합니다 <code>.model</code> 선택기를 사용하여 JSON 표현을 만듭니다.</p> <p>예제 경로는 다음과 같습니다.<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>보안</td>
   <td><p>여러 옵션이 가능합니다.</p> <p>OAuth가 제안됩니다. 표준 설정과 별도로 구성할 수 있습니다.</p> </td>
   <td>AEM 표준 설정을 사용합니다.</td>
  </tr>
  <tr>
   <td>건축주의</td>
   <td><p>쓰기 액세스는 일반적으로 작성자 인스턴스의 주소를 지정합니다.</p> <p>읽기가 게시 인스턴스로 보내질 수도 있습니다.</p> </td>
   <td>이 방법은 읽기 전용이므로 일반적으로 게시 인스턴스에 사용됩니다.</td>
  </tr>
  <tr>
   <td>출력</td>
   <td>JSON 기반 SHANNER 출력: 장황하지만 강력해 컨텐츠 내에서 탐색할 수 있습니다.</td>
   <td>JSON 기반 독점 출력; Sling 모델을 통해 구성할 수 있습니다. 컨텐츠 구조를 탐색하는 것은 구현하기가 어렵습니다(하지만 반드시 불가능한 것은 아님).</td>
  </tr>
 </tbody>
</table>

### 보안 {#security}

특정 인증 요구 사항 없이 환경 내에서 Assets REST API를 사용하는 경우 AEM CORS 필터를 올바르게 구성해야 합니다.

>[!NOTE]
>
>자세한 내용은 다음을 참조하십시오.
>
>* [CORS/AEM 설명](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
>* [비디오 - AEM을 사용한 CORS용 개발](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
>


특정 인증 요구 사항이 있는 환경에서는 OAuth가 권장됩니다.

## 사용 가능한 기능 {#available-features}

컨텐츠 조각은 특정 유형의 자산입니다. 자세한 내용은 [컨텐츠 조각을 사용한 작업](/help/assets/content-fragments/content-fragments.md).

API를 통해 사용할 수 있는 기능에 대한 자세한 내용은 다음을 참조하십시오.

* 다음 [자산 REST API](/help/assets/mac-api-assets.md)
* [엔티티 유형](/help/assets/content-fragments/assets-api-content-fragments.md#entity-types)에서는 지원되는 각 유형에 해당하는 기능(컨텐츠 조각과 관련)이 설명되어 있습니다

### 페이징 {#paging}

Assets REST API는 URL 매개 변수를 통해 페이징(GET 요청)을 지원합니다.

* `offset` - 검색할 첫 번째(하위) 엔티티의 수
* `limit` - 반환된 최대 개체 수

응답에는 페이지의 일부로 페이징 정보가 포함됩니다 `properties` 섹션에 있는 SANNL 출력의 섹션을 참조하십시오. 이 `srn:paging` 속성에는 (자식) 엔티티의 총 수가 포함됩니다. `total`), 오프셋 및 제한( `offset`, `limit`)을 입력합니다.

>[!NOTE]
>
>페이징은 일반적으로 요청된 엔티티의 1차 하위 구성요소와 관련된 컨테이너 엔티티(즉, 폴더 또는 변환이 있는 자산)에 적용됩니다.

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

폴더는 자산 및 기타 폴더에 대한 컨테이너 역할을 합니다. AEM 컨텐츠 저장소의 구조를 반영합니다.

Assets REST API는 폴더의 속성에 대한 액세스 권한을 노출합니다. 예를 들어 해당 이름, 제목 등이 있습니다. 자산은 폴더 및 하위 폴더의 하위 엔티티로 노출됩니다.

>[!NOTE]
>
>하위 자산 및 폴더의 자산 유형에 따라 하위 엔티티 목록에 이미 각 하위 엔티티를 정의하는 전체 속성 세트가 포함될 수 있습니다. 또는 이 자식 엔티티 목록에서 엔티티에 대해 축소된 속성 집합만 노출될 수 있습니다.

### 에셋 {#assets}

자산이 요청되면 응답은 해당 메타데이터를 반환합니다. 제목, 이름 및 각 자산 스키마에 의해 정의된 기타 정보와 같은 정보를 제공합니다.

자산의 이진 데이터는 유형의 SANNER 링크로 노출됩니다 `content`.

자산에는 여러 표현물이 있을 수 있습니다. 이러한 항목은 일반적으로 하위 엔티티로 노출되며, 한 가지 예외는 축소판 표현이며 유형 링크로 표시됩니다 `thumbnail` ( `rel="thumbnail"`).

### 콘텐츠 조각 {#content-fragments}

A [콘텐츠 조각](/help/assets/content-fragments/content-fragments.md) 는 특별한 유형의 자산입니다. 텍스트, 숫자, 날짜 등과 같은 구조화된 데이터에 액세스하는 데 사용할 수 있습니다.

다음과 같은 몇 가지 차이점이 있습니다 *standard* 자산(이미지 또는 오디오 등)을 처리할 때 일부 추가 규칙이 적용됩니다.

#### 표시 {#representation}

컨텐츠 조각:

* 이진 데이터는 노출하지 마십시오.
* JSON 출력(내의)에 완전히 포함되어 있습니다 `properties` Analytics JavaScript용 URL 섹션을 참조하십시오.

* 또한 원자로도 간주됩니다. 즉, 요소 및 변형이 조각의 속성의 일부와 링크 또는 하위 엔티티의 일부로 노출됩니다. 이를 통해 조각의 페이로드에 효율적으로 액세스할 수 있습니다.

#### 컨텐츠 모델 및 컨텐츠 조각 {#content-models-and-content-fragments}

현재 컨텐츠 조각의 구조를 정의하는 모델은 HTTP API를 통해 노출되지 않습니다. 따라서 *소비자* 페이로드에서 대부분의 정보를 추론할 수 있지만 조각의 모델에 대해 알아야 합니다(최소). 데이터 유형 등 는 정의의 일부입니다.

새 컨텐츠 조각을 생성하려면 모델의 (내부 저장소) 경로를 제공해야 합니다.

#### 관련 콘텐츠 {#associated-content}

연관된 컨텐츠는 현재 노출되지 않습니다.

## 사용 {#using}

사용법은 특정 사용 사례와 함께 AEM 작성자 또는 게시 환경을 사용하는지에 따라 다를 수 있습니다.

* 작성은 작성자 인스턴스([현재 이 API를 사용하여 게시할 조각을 복제할 방법이 없습니다](/help/assets/content-fragments/assets-api-content-fragments.md#limitations)).
* AEM은 요청된 컨텐츠를 JSON 형식으로만 제공하므로 두 방법 모두에서 게재가 가능합니다.

   * AEM 작성자 인스턴스에서 저장 및 전달하면 방화벽 뒤에서 미디어 라이브러리 응용 프로그램이 충분해야 합니다.

   * 라이브 웹 전달을 위해 AEM 게시 인스턴스가 권장됩니다.

>[!CAUTION]
>
>AEM 클라우드 인스턴스의 Dispatcher 구성은에 대한 액세스를 차단할 수 있습니다 `/api`.

>[!NOTE]
>
>자세한 내용은 [API 참조](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference). 특히, [Adobe Experience Manager Assets API - 컨텐츠 조각](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html).

## 제한 사항 {#limitations}

다음과 같은 몇 가지 제한 사항이 있습니다.

* **컨텐츠 조각 모델은 현재 지원되지 않습니다**: 읽거나 만들 수 없습니다. 신규 컨텐츠 조각을 생성하거나 기존 컨텐츠 조각을 업데이트하려면 개발자가 컨텐츠 조각 모델에 대한 올바른 경로를 알아야 합니다. 현재 이러한 UI에 대한 개요를 얻는 유일한 방법은 관리 UI를 사용하는 것입니다.
* **참조는 무시됩니다**. 현재 기존 컨텐츠 조각을 참조하는지 여부에 대한 검사가 없습니다. 따라서, 예를 들어 컨텐츠 조각을 삭제하면 삭제된 컨텐츠 조각에 대한 참조가 포함된 페이지에 문제가 발생할 수 있습니다.
* **JSON 데이터 유형** 의 REST API 출력 *JSON 데이터 유형* 은(는) 현재 *문자열 기반 출력*.

## 상태 코드 및 오류 메시지 {#status-codes-and-error-messages}

관련 상황에서는 다음 상태 코드를 볼 수 있습니다.

* **200년** (확인)

   다음 경우에 반환됩니다.

   * 를 통해 컨텐츠 조각 요청 `GET`
   * 를 통해 컨텐츠 조각을 성공적으로 업데이트함 `PUT`

* **201년** (생성됨)

   다음 경우에 반환됩니다.

   * 를 통해 컨텐츠 조각을 성공적으로 만들기 `POST`

* **404년** (찾을 수 없음)

   다음 경우에 반환됩니다.

   * 요청된 컨텐츠 조각이 없습니다.

* **500년** (내부 서버 오류)

   >[!NOTE]
   >
   >이 오류가 반환됩니다.
   >
   >* 특정 코드로 식별할 수 없는 오류가 발생한 경우
   >* 지정된 페이로드가 올바르지 않은 경우


   다음은 이 오류 상태가 반환될 때 발생하는 일반적인 시나리오와 생성된 오류 메시지(모노스페이스)를 나열합니다.

   * 상위 폴더가 없습니다(를 통해 컨텐츠 조각을 만들 때). `POST`)
   * 제공된 컨텐츠 조각 모델이 없습니다(cq:model이 없음). 읽을 수 없거나(잘못된 경로 또는 권한 문제로 인해) 올바른 조각 모델이 없습니다.

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`
   * 컨텐츠 조각을 만들 수 없습니다(권한 문제일 수 있음).

      * `Could not create content fragment`
   * 제목 및 또는 설명을 업데이트할 수 없습니다.

      * `Could not set value on content fragment`
   * 메타데이터를 설정할 수 없습니다.

      * `Could not set metadata on content fragment`
   * 콘텐츠 요소를 찾을 수 없거나 업데이트할 수 없습니다.

      * `Could not update content element`
      * `Could not update fragment data of element`

   자세한 오류 메시지는 일반적으로 다음 방식으로 반환됩니다.

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

자세한 API 참조는 다음을 참조하십시오.

* [Adobe Experience Manager Assets API - 컨텐츠 조각](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html)

* [Assets HTTP API](/help/assets/mac-api-assets.md)

   * [사용 가능한 기능](/help/assets/mac-api-assets.md#available-features)

## 추가 리소스 {#additional-resources}

자세한 내용은 다음을 참조하십시오.

* [자산 HTTP API 설명서](/help/assets/mac-api-assets.md)
* [AEM Gem 세션: OAuth](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html)
