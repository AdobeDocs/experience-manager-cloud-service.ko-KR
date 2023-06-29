---
title: AEM Headless으로 Dispatcher 구성
description: Dispatcher는 Adobe Experience Manager Publish 환경 앞에 있는 캐싱 및 보안 계층입니다. Headless 애플리케이션에 대한 GraphQL 엔드포인트를 여는 데 여러 구성이 사용됩니다.
feature: Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 55%

---

# AEM Headless으로 Dispatcher 구성

[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)는 Adobe Experience Manager Publish 환경 앞에 있는 캐싱 및 보안 계층입니다. Headless 애플리케이션에 대한 GraphQL 엔드포인트를 여는 데 여러 구성이 기본적으로 포함되어 있습니다.

>[!NOTE]
>
>Dispatcher에 대한 자세한 문서는 다음을 참조하십시오. [Dispatcher 안내서](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html).

AEM 프로젝트의 일부로 Dispatcher에 대한 구성이 포함된 Dispatcher 모듈이 포함되어 있습니다. 에서 새로 생성된 프로젝트 [AEM Project Archetype](https://github.com/adobe/aem-project-archetype) 자동 포함 [필터](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?#defining-a-filter) GraphQL 종단점을 사용할 수 있도록 합니다.

## GraphQL 엔드포인트

기본 필터의 일부로, [GraphQL 엔드포인트](/help/headless/graphql-api/graphql-endpoint.md)는 다음 규칙에 따라 열립니다.

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

`*` 와일드 카드는 AEM 인스턴스에서 여러 엔드포인트를 엽니다. GraphQL 끝점을 사용한 쿼리는 다음을 사용하여 수행됩니다. `POST` 그리고 응답은 다음과 같습니다. **아님** 캐시됨.

## GraphQL 지속 쿼리

지속 쿼리에 대한 요청은 다른 끝점에 대해 수행됩니다. 기본 필터 구성의 일부로 [지속 쿼리](/help/headless/graphql-api/persisted-queries.md) 는 다음 규칙에 따라 열립니다.

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

지속 쿼리는 다음을 사용하여 요청할 수 있습니다. `GET`: Dispatcher 및 CDN 수준에서 응답을 캐싱합니다. 캐싱 및 캐시 무효화에 대한 자세한 내용은 [여기](/help/implementing/dispatcher/caching.md)에서 확인할 수 있습니다.
