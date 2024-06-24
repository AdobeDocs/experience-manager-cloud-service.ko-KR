---
title: AEM Headless로 CORS(원본 간 리소스 공유) 구성
description: Adobe Experience Manager의 CORS(원본 간 리소스 공유)를 사용하면 Headless 웹 애플리케이션에서 AEM에 대한 클라이언트측 호출을 할 수 있습니다. GraphQL 엔드포인트에 대한 액세스를 활성화하려면 CORS 구성이 필요합니다.
feature: Headless, GraphQL API
exl-id: 426be9f9-f44a-4744-ac08-e64bb97308a0
solution: Experience Manager
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 100%

---

# CORS(원본 간 리소스 공유) 구성

>[!CAUTION]
>
>[Dispatcher에서 캐싱이 활성화된](/help/headless/deployment/dispatcher-caching.md) 경우 CORS 필터가 필요하지 않으므로 이 섹션을 무시해도 됩니다.

>[!NOTE]
>
>AEM의 CORS 리소스 공유 정책에 대한 자세한 개요는 [CORS(원본 간 리소스 공유) 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=ko-KR#understand-cross-origin-resource-sharing-(cors))를 참조하십시오.

GraphQL 엔드포인트에 액세스하려면 CORS 정책을 구성하고 [Cloud Manager를 통해 AEM에 배포된](/help/implementing/cloud-manager/deploy-code.md) AEM 프로젝트에 추가해야 합니다. 원하는 엔드포인트에 대한 적절한 OSGi CORS 구성 파일 추가를 통해 수행됩니다. 여러 CORS 구성을 만들고 다른 환경에 배포할 수 있습니다. 예시는 [WKND 참조 사이트](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig)에서 확인할 수 있습니다.

CORS 구성은 액세스 권한이 부여되어야 하는 신뢰할 수 있는 웹 사이트 출처 `alloworigin` 또는 `alloworiginregexp`를 지정해야 합니다.

구성 파일의 이름은 다음과 같이 지정해야 합니다. `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json` 여기서 `appname`은 애플리케이션 이름을 나타냅니다.

예를 들어 GraphQL 엔드포인트 `/content/cq:graphql/wknd/endpoint` 및 `https://my.domain`의 지속 쿼리 엔드포인트에 대한 액세스 권한을 부여하려면 다음을 사용할 수 있습니다.

```json
{
  "supportscredentials":false,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/cq:graphql/wknd/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

엔드포인트에 대해 가상 경로를 구성한 경우 `allowedpaths`에서도 사용할 수 있습니다.
