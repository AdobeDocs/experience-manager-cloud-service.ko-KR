---
title: AEM Headless으로 Dispatcher 구성
description: Dispatcher는 Adobe Experience Manager Publish 환경 앞에 있는 캐싱 및 보안 계층입니다. Headless 애플리케이션에 대한 GraphQL 끝점을 여는 데 여러 구성이 사용됩니다.
feature: Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 100%

---

# AEM Headless으로 Dispatcher 구성

[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=ko-KR)는 Adobe Experience Manager Publish 환경 앞에 있는 캐싱 및 보안 계층입니다. Headless 애플리케이션에 대한 GraphQL 끝점을 여는 데 여러 구성이 기본적으로 포함되어 있습니다.

>[!NOTE]
>
>Dispatcher에 대한 자세한 문서는 [Dispatcher 안내서](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) 를 참조하십시오.

AEM Project의 일부로 Dispatcher에 대한 구성이 포함된 Dispatcher 모듈이 포함되어 있습니다. [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)에서 새로 생성된 프로젝트에는 GraphQL 끝점을 활성화하는 [필터](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=ko-KR?#defining-a-filter)가 자동으로 포함됩니다.

## GraphQL 끝점

기본 필터의 일부로, [GraphQL 끝점](/help/headless/graphql-api/graphql-endpoint.md)은 다음 규칙에 따라 열립니다.

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

`*` 와일드 카드는 AEM 인스턴스에서 여러 끝점을 엽니다. GraphQL 끝점을 사용한 쿼리는 `POST`를 사용하여 이루어지고 응답은 캐시되지 **않습니다**.

## GraphQL 지속 쿼리

지속 쿼리에 대한 요청은 다른 끝점에 대해 수행됩니다. 기본 필터 구성의 일부로, [지속 쿼리](/help/headless/graphql-api/persisted-queries.md)의 URL은 다음 규칙에 따라 열립니다.

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

지속 쿼리는 `GET`를 사용하여 요청할 수 있으므로 Dispatcher 및 CDN 수준에서 응답을 캐싱합니다. 캐싱 및 캐시 무효화에 대한 자세한 내용은 [여기](/help/implementing/dispatcher/caching.md)에서 확인할 수 있습니다.
