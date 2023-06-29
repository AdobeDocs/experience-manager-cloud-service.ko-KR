---
title: 콘텐츠 조각의 원격 AEM GraphQL 쿼리 인증
description: Headless 콘텐츠 전송을 보호하기 위해 원격 Adobe Experience Manager GraphQL 쿼리에 필요한 인증을 이해합니다.
feature: Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 31%

---

# 콘텐츠 조각의 원격 AEM GraphQL 쿼리 인증 {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

의 기본 사용 사례 [컨텐츠 조각 전달을 위한 Adobe Experience Manager as a Cloud Service(AEM) GraphQL API](/help/headless/graphql-api/content-fragments.md) 은 타사 응용 프로그램 또는 서비스의 원격 쿼리를 수락하는 것입니다. Headless 콘텐츠 게재를 보호하기 위해 이러한 원격 쿼리에는 인증된 API 액세스가 필요할 수 있습니다.

>[!NOTE]
>
>테스트 및 개발을 위해 다음을 사용하여 AEM GraphQL API에 직접 액세스할 수도 있습니다. [GraphiQL 인터페이스](/help/headless/graphql-api/graphiql-ide.md).

인증을 위해 서드파티 서비스는 [액세스 토큰 검색](#retrieving-access-token) 그런 다음 다음과 같을 수 있습니다. [GraphQL 요청에 사용됨](#use-access-token-in-graphql-request).

## 액세스 토큰 검색 {#retrieving-access-token}

다음을 참조하십시오 [서버측 API용 액세스 토큰 생성](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) 전체 세부 정보.

## GraphQL 요청에서 액세스 토큰 사용 {#use-access-token-in-graphql-request}

서드파티 서비스가 AEM 인스턴스와 연결하려면 *액세스 토큰*. 그런 다음 서비스는 이 토큰을 POST 요청의 `Authorization` 헤더에 추가해야 합니다.

예를 들어 GraphQL 권한 부여 헤더는 다음과 같습니다.

```xml
Authorization: Bearer <access_token>
```

## 권한 요구 사항 {#permission-requirements}

액세스 토큰을 사용하여 이루어진 모든 요청 *토큰을 생성한 사용자 계정별*.

이 사용자 계정은 계정에 GraphQL 쿼리를 실행하는 데 필요한 권한이 있는지 확인해야 함을 의미합니다.

로컬 인스턴스에서 GraphiQL을 사용하여 이러한 권한을 확인할 수 있습니다. 권한에 대한 자세한 내용은 [여기](/help/headless/security/permissions.md)에서 확인하십시오.
