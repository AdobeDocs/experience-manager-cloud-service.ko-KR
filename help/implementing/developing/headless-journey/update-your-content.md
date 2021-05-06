---
title: AEM Assets API를 통해 컨텐츠를 업데이트하는 방법
description: AEM 헤드리스 개발자 여정의 이 부분에서 REST API를 사용하여 콘텐츠 조각에 액세스하고 업데이트하는 방법을 알아봅니다.
hide: true
hidefromtoc: true
index: false
exl-id: 8d133b78-ca36-4c3b-815d-392d41841b5c
translation-type: tm+mt
source-git-commit: 0c47dec1e96fc3137d17fc3033f05bf1ae278141
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 3%

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

## 자산 HTTP API {#assets-http-api}

[자산 HTTP API](/help/assets/mac-api-assets.md)은 다음을 포함합니다.

* 자산 REST API
* 컨텐츠 조각 지원 포함

자산 HTTP API의 현재 구현은 **REST** 아키텍처 스타일을 기반으로 합니다.

Assets REST API를 통해 Adobe Experience Manager 개발자는 Cloud Service으로 HTTP API를 통해 **CRUD** 작업(만들기, 읽기, 업데이트, 삭제)을 통해 HTTP API를 통해 직접 컨텐츠(AEM에 저장)에 액세스할 수 있습니다.

API를 사용하면 JavaScript 프런트 엔드 애플리케이션에 컨텐츠 서비스를 제공하여 Adobe Experience Manager을 헤드리스 CMS(Content Management System)로 Cloud Service으로 운영할 수 있습니다. 또는 HTTP 요청을 실행하고 JSON 응답을 처리할 수 있는 다른 애플리케이션입니다.

예를 들어, 단일 페이지 애플리케이션(SPA), 프레임워크 기반 또는 사용자 정의 등은 API를 통해 제공된 컨텐츠가 필요합니다(주로 JSON 형식).

AEM 코어 구성 요소는 이러한 목적으로 필요한 읽기 작업을 제공할 수 있고 JSON 출력을 사용자 정의할 수 있는 매우 포괄적이고 유연하며 사용자 정의 가능한 API를 제공하지만 전용 AEM 템플릿을 기반으로 하는 페이지에서 호스팅되어야 하는 AEM WCM(Web Content Management) 구현에 대한 노하우가 필요합니다. 모든 SPA 개발 조직은 이러한 지식을 직접 이용하고 있지는 않습니다.

이것은 자산 REST API를 사용할 수 있는 때입니다. 이를 통해 개발자는 페이지에 먼저 에셋(예: 이미지 및 컨텐츠 조각)을 임베드하여 컨텐츠를 직렬화된 JSON 포맷으로 제공할 필요 없이 바로 에셋에 액세스할 수 있습니다.

>[!NOTE]
>
>자산 REST API에서 JSON 출력을 사용자 지정할 수 없습니다.

또한 에셋 REST API를 사용하면 개발자는 기존 에셋, 컨텐츠 조각 및 폴더를 새로 만들거나 업데이트하거나 삭제하여 컨텐츠를 수정할 수 있습니다.

자산 REST API:

* HATEOAS 원칙을 따릅니다
* 사이렌 형식을 구현합니다.

## 전제 조건 {#prerequisites}

Assets REST API는 최신 Adobe Experience Manager을 Cloud Service 버전으로 즉시 설치할 때마다 사용할 수 있습니다.

## 주요 개념 {#key-concepts}

자산 REST API는 AEM 인스턴스 내에 저장된 자산에 대한 REST 스타일 액세스를 제공합니다.

`/api/assets` 끝점을 사용하고, 이 끝점에 액세스하려면 자산의 경로가 필요합니다(맨 앞의 `/content/dam` 없이).

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


HTTP 메서드는 실행할 작업을 결정합니다.

* **GET**  - 에셋 또는 폴더의 JSON 표현 가져오기
* **POST**  - 새 에셋 또는 폴더 만들기
* **PUT**  - 자산 또는 폴더의 속성을 업데이트하는 방법
* **DELETE**  - 자산 또는 폴더 삭제

>[!NOTE]
>
>요청 본문 및/또는 URL 매개 변수를 사용하여 이러한 작업 중 일부를 구성할 수 있습니다.예를 들어 **POST** 요청에 의해 폴더 또는 자산을 만들어야 함을 정의합니다.

지원되는 요청의 정확한 형식은 API 참조 설명서에 정의되어 있습니다.

### 트랜잭션 동작 {#transactional-behavior}

모든 요청은 원자입니다.

즉, 후속(`write`) 요청은 단일 엔티티로 성공하거나 실패할 수 있는 단일 트랜잭션으로 결합할 수 없습니다.

### AEM(자산) REST API와 AEM 구성 요소 {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Aspect</td>
   <td>자산 REST API<br/> </td>
   <td>AEM 구성 요소<br/>(Sling 모델을 사용하는 구성 요소)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>지원되는 사용 사례</td>
   <td>일반적인 목적.</td>
   <td><p>단일 페이지 애플리케이션(SPA) 또는 기타(컨텐츠 소비) 컨텍스트에서의 소비를 위해 최적화되었습니다.</p> <p>레이아웃 정보를 포함할 수도 있습니다.</p> </td>
  </tr>
  <tr>
   <td>지원되는 작업</td>
   <td><p>만들기, 읽기, 업데이트, 삭제</p> <p>엔티티 유형에 따라 추가 작업이 제공됩니다.</p> </td>
   <td>읽기 전용.</td>
  </tr>
  <tr>
   <td>액세스</td>
   <td><p>직접 액세스할 수 있습니다.</p> <p>저장소에서 <code>/content/dam</code>에 매핑된 <code>/api/assets </code>끝점을 사용합니다.</p> 
   <p>예제 경로는 다음과 같습니다. <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>AEM 페이지의 AEM 구성 요소를 통해 참조되어야 합니다.</p> <p><code>.model</code> 선택기를 사용하여 JSON 표현을 만듭니다.</p> <p>예제 경로는 다음과 같습니다.<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>보안</td>
   <td><p>여러 옵션이 가능합니다.</p> <p>OAuth가 제안됨;표준 설정과 별도로 구성할 수 있습니다.</p> </td>
   <td>AEM 표준 설정을 사용합니다.</td>
  </tr>
  <tr>
   <td>건축주의</td>
   <td><p>쓰기 액세스는 일반적으로 작성자 인스턴스의 주소를 지정합니다.</p> <p>또한 읽기가 게시 인스턴스로 연결될 수도 있습니다.</p> </td>
   <td>이 방법은 읽기 전용이므로 일반적으로 게시 인스턴스에 사용됩니다.</td>
  </tr>
  <tr>
   <td>출력</td>
   <td>JSON 기반 사이렌 출력:자세한 정보를 제공하고 강력합니다. 컨텐츠 내에서 탐색할 수 있습니다.</td>
   <td>JSON 기반의 독점 출력;Sling 모델을 통해 구성할 수 있습니다. 컨텐츠 구조를 탐색하는 것은 구현하기가 어렵지만 꼭 불가능한 것은 아닙니다.</td>
  </tr>
 </tbody>
</table>

### 보안 {#security}

특정 인증 요구 사항이 없는 환경에서 자산 REST API를 사용하는 경우 AEM CORS 필터를 올바르게 구성해야 합니다.

>[!NOTE]
>
>자세한 내용은 다음을 참조하십시오.
>
>* CORS/AEM 설명
>* 비디오 - AEM을 사용한 CORS 개발

>



특정 인증 요구 사항이 있는 환경에서는 OAuth가 권장됩니다.

## 사용 가능한 기능 {#available-features}

컨텐츠 조각은 특정 유형의 자산입니다. 컨텐츠 조각 작업을 참조하십시오.

API를 통해 사용할 수 있는 기능에 대한 자세한 내용은 다음을 참조하십시오.

* 자산 REST API
* 엔티티 유형 - 지원되는 각 유형(컨텐츠 조각과 관련)에 대한 기능이 설명됩니다.

### {#paging} 호출

자산 REST API는 URL 매개 변수를 통해 페이지(GET 요청에 대해)를 지원합니다.

* `offset` - 검색할 첫 번째(자식) 엔티티의 수
* `limit` - 반환된 최대 개체 수

응답에는 SANNES 출력에서 `properties` 섹션의 일부로서 페이징 정보가 포함됩니다. 이 `srn:paging` 속성에는 요청에 지정된 총 개체 수( `total`), 오프셋 및 한도( `offset`, `limit`)가 포함됩니다.

>[!NOTE]
>
>페이징은 요청된 엔티티의 자식과 관련된 컨테이너 엔티티(즉, 표현물과 함께 폴더 또는 자산)에 일반적으로 적용됩니다.

#### 예:{#example-paging} 호출

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

자산 REST API는 폴더의 속성에 대한 액세스 권한을 표시합니다.예를 들어 이름, 제목 등이 있습니다. 자산은 폴더 하위 엔티티 및 하위 폴더로 표시됩니다.

>[!NOTE]
>
>하위 자산 및 폴더의 자산 유형에 따라 하위 엔티티 목록에 해당 하위 엔티티를 정의하는 전체 속성 세트가 이미 포함되어 있을 수 있습니다. 또는 이 자식 엔티티 목록의 엔티티에 대해 축소된 속성 세트만 노출될 수 있습니다.

### 에셋 {#assets}

자산이 요청되면 응답에서 해당 메타데이터를 반환합니다.제목, 이름 및 해당 자산 스키마에 의해 정의된 기타 정보 등.

에셋의 이진 데이터는 `content` 유형의 SYNN 링크로 노출됩니다.

자산에 여러 표현물이 있을 수 있습니다. 이러한 항목은 일반적으로 하위 엔티티로 노출되며, 한 가지 예외는 축소판 변환이며 이 변환은 `thumbnail` 유형의 링크로 표시됩니다( `rel="thumbnail"`).

### 콘텐츠 조각 {#content-fragments}

컨텐츠 조각은 특별한 유형의 자산입니다. 텍스트, 숫자, 날짜 등 구조화된 데이터에 액세스하는 데 사용할 수 있습니다.

*standard* 자산(예: 이미지 또는 오디오)에 차이가 여러 개 있으므로 처리 시 일부 추가 규칙이 적용됩니다.

#### 표현 {#representation}

컨텐츠 조각:

* 이진 데이터를 노출하지 마십시오.
* JSON 출력(`properties` 속성 내)에 완전히 포함됩니다.

* 요소 및 변형을 원자성으로 간주합니다. 즉, 요소 및 변형을 링크 또는 하위 엔티티보다 조각 속성의 일부로 노출됩니다. 이렇게 하면 조각의 페이로드에 대한 효율적인 액세스를 할 수 있습니다.

#### 컨텐트 모델 및 컨텐츠 조각 {#content-models-and-content-fragments}

현재 컨텐츠 조각 구조를 정의하는 모델은 HTTP API를 통해 노출되지 않습니다. 따라서 대부분의 정보를 페이로드에서 유추할 수 있지만, *consumer*&#x200B;는 조각 모델에 대해 알아야 합니다(최소 최소).데이터 유형 등에 는 정의의 일부입니다.

새 컨텐츠 조각을 만들려면 모델의 (내부 저장소) 경로를 제공해야 합니다.

#### 관련 컨텐츠 {#associated-content}

연관된 컨텐츠는 현재 노출되지 않습니다.

## 자산 REST API 사용 {#using-aem-assets-rest-api}

AEM Assets REST API 사용에 대한 자세한 내용은 다음을 참조할 수 있습니다.

* Adobe Experience Manager Assets HTTP API
* AEM Assets HTTP API의 컨텐츠 조각 지원

## 다음 {#whats-next} 소개

AEM 헤드리스 개발자 여정의 이 부분을 완료하셨다면 다음을 수행해야 합니다.

* AEM Assets HTTP API를 이해합니다.
* 이 API에서 컨텐츠 조각이 지원되는 방식을 이해합니다.

<!--
* Have experience with sample code and know how the API works in practice.
-->

AEM 헤드리스 프로젝트를 사용하고 라이브할 준비를 하는 방법을 배울 수 있는 AEM Headless](put-it-all-together.md) 문서의 [모두 함께 놓는 방법 - 앱과 귀하의 컨텐츠를 차례로 검토하여 AEM 헤드리스 여정을 계속 진행해야 합니다.

## 추가 리소스 {#additional-resources}

* [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)
* [HATEOAS 원칙](https://en.wikipedia.org/wiki/HATEOAS)
* [사이렌 형식](https://github.com/kevinswiber/siren)
* [자산 HTTP API](/help/assets/mac-api-assets.md)
* [컨텐츠 조각 REST API](/help/assets/content-fragments/assets-api-content-fragments.md)
   * [API 참조](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference)
* [콘텐츠 조각을 사용한 작업](/help/assets/content-fragments/content-fragments.md)
* [AEM 핵심 구성 요소](https://docs.adobe.com/content/help/ko/experience-manager-core-components/using/introduction.html)
* [CORS/AEM 설명](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [비디오 - AEM을 사용한 CORS 개발](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

