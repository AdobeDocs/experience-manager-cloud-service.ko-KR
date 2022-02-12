---
title: AEM Headless를 사용한 Dispatcher 구성
description: Dispatcher는 Adobe Experience Manager 게시 환경 앞에 있는 캐싱 및 보안 레이어입니다. 여러 구성은 헤드리스 응용 프로그램으로 GraphQL 끝점을 여는 데 사용됩니다.
feature: Dispatcher, GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 6%

---


# AEM Headless를 사용한 Dispatcher 구성

다음 [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) Adobe Experience Manager 게시 환경 앞에 있는 캐싱 및 보안 레이어입니다. 헤드리스 애플리케이션으로 GraphQL 종단점을 열 수 있도록 기본적으로 여러 구성이 포함됩니다.

>[!NOTE]
>
>Dispatcher에 대한 자세한 설명서는 를 참조하십시오. [Dispatcher 안내서](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)

AEM Project의 일부로서 Dispatcher 모듈에 디스패처에 대한 구성이 포함됩니다. 에서 새로 생성된 프로젝트 [AEM 프로젝트 원형](https://github.com/adobe/aem-project-archetype) 자동 포함 [필터](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?#defining-a-filter) GraphQL 종단점을 활성화합니다.

## GraphQL 끝점

기본 필터의 일부로서, [GraphQL 끝점](/help/headless/graphql-api/graphql-endpoint.md) 는 다음 규칙으로 열립니다.

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

다음 `*` 와일드카드가 AEM 인스턴스에서 여러 끝점을 엽니다. GraphQL 종단점을 사용하여 쿼리를 수행하면 `POST` 그러면 응답이 **not** 캐시됩니다.

## GraphQL 지속적인 쿼리

다른 종단점에 대해 지속적인 쿼리에 대한 요청이 수행됩니다. 기본 필터 구성의 일부로, [지속되는 쿼리](/help/headless/graphql-api/persisted-queries.md) 는 다음 규칙으로 열립니다.

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

영구 쿼리는 `GET`로 설정되면 Dispatcher 및 CDN 수준에서 응답을 캐시할 수 있습니다. 캐싱 및 캐시 무효화에 대한 자세한 내용을 찾을 수 있습니다. [여기](/help/implementing/dispatcher/caching.md).
