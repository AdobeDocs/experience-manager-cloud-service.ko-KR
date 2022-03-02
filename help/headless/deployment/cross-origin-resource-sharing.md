---
title: AEM Headless로 CORS(원본 간 리소스 공유) 구성
description: Adobe Experience Manager의 CORS(원본 간 리소스 공유)를 사용하면 Headless 웹 애플리케이션에서 AEM에 대한 클라이언트측 호출을 할 수 있습니다. GraphQL 끝점에 대한 액세스를 활성화하려면 CORS 구성이 필요합니다.
feature: GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: ht
source-wordcount: '208'
ht-degree: 100%

---


# CORS(원본 간 리소스 공유) 구성

>[!NOTE]
>
>AEM의 CORS 리소스 공유 정책에 대한 자세한 개요는 [CORS(원본 간 리소스 공유) 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=ko-KR#understand-cross-origin-resource-sharing-(cors))를 참조하십시오.

GraphQL 끝점에 액세스하려면 CORS 정책을 구성하고 [Cloud Manager를 통해 AEM에 배포된](/help/implementing/cloud-manager/deploy-code.md) AEM 프로젝트에 추가해야 합니다. 원하는 끝점에 대한 적절한 OSGi CORS 구성 파일 추가를 통해 수행됩니다. 여러 CORS 구성을 만들고 다른 환경에 배포할 수 있습니다. 예시는 [WKND 참조 사이트](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig)에서 확인할 수 있습니다.

CORS 구성은 액세스 권한이 부여되어야 하는 신뢰할 수 있는 웹 사이트 출처 `alloworigin` 또는 `alloworiginregexp`를 지정해야 합니다.

구성 파일의 이름은 다음과 같이 지정해야 합니다. `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json` 여기서 `appname`은 애플리케이션 이름을 나타냅니다.

예를 들어 GraphQL 끝점 `/content/cq:graphql/wknd/endpoint` 및 `https://my.domain`의 지속 쿼리 끝점에 대한 액세스 권한을 부여하려면 다음을 사용할 수 있습니다.

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

끝점에 대해 가상 경로를 구성한 경우 `allowedpaths`에서도 사용할 수 있습니다.


