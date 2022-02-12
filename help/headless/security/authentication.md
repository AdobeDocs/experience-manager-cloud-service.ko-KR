---
title: 콘텐츠 조각의 원격 AEM GraphQL 구문 인증
description: 헤드리스 콘텐츠 전달을 보호하기 위해 Remote AEM GraphQL 쿼리에 필요한 인증을 이해합니다.
feature: Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
source-git-commit: 4e37db128aa31d6e8e950be0d077eae921a27468
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 7%

---

# 콘텐츠 조각의 원격 AEM GraphQL 구문 인증 {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

에 대한 기본 사용 사례 [Adobe Experience Manager as a Cloud Service(AEM) GraphQL API for Content Fragment Delivery](/help/headless/graphql-api/content-fragments.md) 는 타사 응용 프로그램 또는 서비스의 원격 쿼리를 수락하는 것입니다. 이러한 원격 쿼리는 헤드리스 콘텐츠 전달을 보호하기 위해 인증된 API 액세스가 필요할 수 있습니다.

>[!NOTE]
>
>테스트 및 개발을 위해 [GraphiQL 인터페이스](/help/headless/graphql-api/graphiql-ide.md) 인터페이스.

인증을 위해 타사 서비스는 다음을 수행해야 합니다 [액세스 토큰 검색](#retrieving-access-token), 그런 다음 [GraphQL 요청에 사용됨](#use-access-token-in-graphql-request).

## 액세스 토큰 검색 {#retrieving-access-token}

자세한 내용은 [서버 측 API에 대한 액세스 토큰 생성](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) 자세한 내용

## GraphQL 요청에서 액세스 토큰 사용 {#use-access-token-in-graphql-request}

타사 서비스가 AEM 인스턴스와 연결하려면 다음이 있어야 합니다 *액세스 토큰*. 그런 다음 서비스는 이 토큰을 `Authorization` 헤더 를 채우는 방법을 설명합니다.

예를 들어 GraphQL 인증 헤더:

```xml
Authorization: Bearer <access_token>
```

## 권한 요구 사항 {#permission-requirements}

액세스 토큰을 사용하여 수행한 모든 요청은 실제로 수행됩니다 *토큰을 생성한 사용자 계정에 의해*.

즉, GraphQL 쿼리를 실행하는 데 필요한 권한이 계정에 있는지 확인해야 합니다.

로컬 인스턴스에서 GraphiQL을 사용하여 이를 확인할 수 있습니다. 에 대한 자세한 내용 [권한은 여기에 있습니다.](/help/headless/security/permissions.md).
