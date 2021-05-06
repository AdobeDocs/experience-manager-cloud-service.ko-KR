---
title: 컨텐츠 조각에 대한 원격 AEM GraphQL 쿼리 인증
description: 헤드리스 컨텐츠 전달을 보호하기 위해 원격 AEM GraphQL 쿼리에 필요한 인증을 파악합니다.
feature: 컨텐츠 조각,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
translation-type: tm+mt
source-git-commit: dab4c9393c26f5c3473e96fa96bf7ec51e81c6c5
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 원격 AEM GraphQL 인증에 대한 컨텐츠 조각 {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

컨텐츠 조각 전달용 [Adobe Experience Manager을 Cloud Service(AEM) GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)으로 사용하는 기본 사용 사례는 타사 응용 프로그램 또는 서비스에서 원격 쿼리를 받는 것입니다. 이러한 원격 쿼리는 헤드리스 컨텐츠 전달을 보호하기 위해 인증된 API 액세스가 필요할 수 있습니다.

>[!NOTE]
>
>테스트 및 개발의 경우 [GraphiQL 인터페이스](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) 인터페이스를 사용하여 AEM GraphQL API에 직접 액세스할 수도 있습니다.

인증을 위해 제3자 서비스는 [액세스 토큰](#retrieving-access-token)을 검색해야 합니다. 이 토큰은 GraphQL 요청](#use-access-token-in-graphql-request)에서 [사용될 수 있습니다.

## 액세스 토큰 {#retrieving-access-token} 검색

자세한 내용은 [서버측 API에 대한 액세스 토큰 생성](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)을 참조하십시오.

## GraphQL 요청의 액세스 토큰 사용 {#use-access-token-in-graphql-request}

AEM 인스턴스와 연결하려면 *액세스 토큰*&#x200B;이 있어야 합니다. 그런 다음 서비스는 POST 요청의 `Authorization` 헤더에 이 토큰을 추가해야 합니다.

예: GraphQL 인증 헤더:

```xml
Authorization: Bearer <access_token>
```

## 권한 요구 사항 {#permission-requirements}

액세스 토큰을 사용하여 수행된 모든 요청은 토큰&#x200B;*을 생성한 사용자 계정에서 실제로*&#x200B;합니다.

즉, GraphQL 쿼리를 실행하는 데 필요한 권한이 계정에 있는지 확인해야 합니다.

로컬 인스턴스에서 GraphiQL을 사용하여 이것을 확인할 수 있습니다.
