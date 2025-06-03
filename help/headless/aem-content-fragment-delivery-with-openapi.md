---
title: OpenAPI와 함께 사용하는 AEM 콘텐츠 조각 게재
description: OpenAPI를 사용한 tAEM 콘텐츠 조각 게재에 대해 알아보기
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: b298db37-1033-4849-bc12-7db29fb77777
source-git-commit: 1995c84bb669fd52ecd53c7e695acc518a5226e8
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 3%

---


# OpenAPI와 함께 사용하는 AEM 콘텐츠 조각 게재 {#aem-content-fragment-delivery-with-openapi}

Adobe Experience Manager(AEM) as a Cloud Service에서 컨텐츠 조각 전달을 위한 AEM OpenAPI는 다음과 같습니다.

* 는 JSON 형식으로 AEM 컨텐츠 조각의 라이브 게재에 최적화된 OpenAPI입니다
* 는 활성 콘텐츠 무효화를 허용하는 최신 CDN 통합을 제공합니다
* 컨텐츠 전달(성능, 확장성, CDN 통합, 최적화된 JSON 제어 및 출력)에 중점을 둡니다.
* 참조된 조각 및 에셋에 대해 JSON을 하이드레이션하는 기능이 포함되어 있습니다

이 API:

* 은(는) AEM Assets HTTP API에서 [콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md)의 후속 항목입니다.

* 콘텐츠 조각 및 콘텐츠 조각 모델(CRUD)을 관리할 수 있도록 [콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI](/help/headless/content-fragment-openapis.md)를 보완합니다.

* 은(는) 콘텐츠 조각과 함께 사용하기 위한 [AEM GraphQL API에 대한 HTTP REST 대안입니다](/help/headless/graphql-api/content-fragments.md)

전체 문서를 보려면 [OpenAPI를 사용한 AEM 콘텐츠 조각 배달](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/contentfragments/delivery/)을 참조하십시오.

>[!NOTE]
>
>사용 가능한 다양한 API에 대한 개요와 관련된 몇 가지 개념의 비교는 [구조화된 컨텐츠 배달 및 관리를 위한 AEM API](/help/headless/apis-headless-and-content-fragments.md)를 참조하십시오.

>[!IMPORTANT]
>
>AEM as a Cloud Service에서 OpenAPI를 사용하여 콘텐츠 조각 배달을 활성화하려면 아직 활성화되지 않았는지 확인한 다음, 제목이 **OpenAPI를 사용하여 콘텐츠 조각 배달 활성화**&#x200B;이고 다음을 지정하는 Adobe 지원 티켓을 제출하십시오.
>
>* Cloud Service 프로그램 및 환경 ID
>* 콘텐츠 조각 배달 OpenAPI로 해결할 사용 사례의 세부 정보
>* Adobe이 응답하고 요청 및 프로젝트에 대해 계속 알려 주어야 하는 모든 연락처에 대한 세부 정보(필요한 경우)

## 캐싱 {#caching}

AEM은 AEM CDN Fastly와 통합됩니다. 즉, 게시 계층에서 제공되는 JSON 응답이 Fastly 수준에서 캐시됩니다.

그러면 사전 정의된 캐싱 헤더를 기반으로 응답이 캐시됩니다(구성할 수 없음).

* 응답은 브라우저/클라이언트 캐시에서 5분 동안 캐시됩니다.
   * `max-age`=`300`
* 응답은 CDN 캐시에서 1시간 동안 캐시됩니다.
   * `s-maxage`=`3600`
* 최대 1시간 동안 새 요청의 유효성을 다시 검사하는 동안 오래된 콘텐츠를 제공할 수 있습니다.
   * `stale-while-revalidate`=`3600`
* 오래된 컨텐츠는 오류별로 최대 1일 동안 제공될 수 있습니다
   * `stale-on-error`=`86400`

OpenAPI를 사용한 콘텐츠 조각 전달은 활성 CDN 캐시 무효화를 지원합니다. 즉, 콘텐츠가 업데이트되거나 게시될 때마다, Fastly에 대한 소프트 삭제 요청을 통해 해당 JSON OpenAPI 응답이 자동으로 무효화됩니다. 이렇게 하면 실제 CDN 캐시 수명(`s-maxage`)에 도달하기 전에 JSON 출력에 반영된 변경 내용을 볼 수 있습니다.

## 사용 가능 {#availability}

OpenAPI를 사용하는 콘텐츠 조각 전달은 미리보기 및 게시 계층에서 사용할 수 있습니다. OpenAPI는 미리보기 및 라이브 게재를 위해 콘텐츠 조각을 JSON 형식으로 전달합니다.

OpenAPI를 사용하여 콘텐츠 조각 게재를 미리 보는 경우 다음을 수행할 수 있습니다.

* 미리보기에 게시
* ip 허용 목록으로 미리 보기에 대한 액세스 활성화
* 미리보기 URL 가져오기

## CORS {#cors}

[CORS 허용 원본](/help/headless/deployment/cross-origin-resource-sharing.md)은(는) API를 호출할 수 있는 원본을 정의합니다.

Dispatcher 구성 측, 특히 GraphQL에 대해 정의된 CORS 허용 출처는 이 API에서 고려되지 않습니다.

<!-- 
## API Rate Limits {#api-rate-limits}
-->

<!-- 
## Limitations {#limitations}
-->
