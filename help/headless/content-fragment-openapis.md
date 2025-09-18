---
title: 콘텐츠 조각 및 콘텐츠 조각 모델 OpenAPI
description: 콘텐츠 조각과 콘텐츠 조각 모델 OpenAPI에 대해 알아봅니다.
exl-id: 077eed73-a066-4273-b2f5-da4bf5cd900c
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 1fb1201fa976e4c0e3c87f22bd9327a55828efef
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 37%

---

# 컨텐츠 조각 및 컨텐츠 조각 모델 관리 OpenAPI {#content-fragments-and-content-fragment-models-management-openapis}

콘텐츠 조각 관리 API의 현대화된 OpenAPI 구현을 통해 개발자는 AEM 작성자에서 프로그래밍 방식으로 만들기, 읽기, 업데이트 및 삭제 작업을 수행하여 AEM에 저장된 콘텐츠 조각 모델 및 콘텐츠 조각을 관리할 수 있습니다. 이러한 API는 다양한 사용 사례를 지원합니다.

전체 문서는 [ 콘텐츠 조각 관리 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)를 참조하십시오.

>[!NOTE]
>
>콘텐츠 조각에 대한 [Assets HTTP API](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/assets/admin/mac-api-assets)의 기존 사용을 새 콘텐츠 조각 관리 OpenAPI로 마이그레이션해야 합니다.

>[!NOTE]
>
>AEM에 로그인하지 않은 경우 OpenAPI에 액세스하려면 인증이 필요합니다. 예를 들어 다른 제품에서 OpenAPI를 통합의 일부로 사용하는 경우가 있습니다.
>
>OpenAPI에 대한 액세스 권한 부여에 대한 자세한 내용은 [OpenAPI 기반 API](/help/implementing/developing/open-api-based-apis.md)를 참조하십시오.

>[!CAUTION]
>
>기본적으로 콘텐츠 조각 관리 OpenAPI는 게시할 때 비활성화됩니다. 대신 배달 지향 사용 사례의 경우 [콘텐츠 조각 배달 OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)를 사용하는 것이 좋습니다.

>[!NOTE]
>
>사용 가능한 다양한 API에 대한 개요와 관련된 몇 가지 개념의 비교는 [구조화된 컨텐츠 배달 및 관리를 위한 AEM API](/help/headless/apis-headless-and-content-fragments.md)를 참조하십시오.