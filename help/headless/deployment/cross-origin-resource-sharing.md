---
title: AEM Headless를 사용한 CORS(원본 간 리소스 공유) 구성
description: Adobe Experience Manager의 CORS(Cross-Origin Resource Sharing)를 사용하면 헤드리스 웹 애플리케이션에서 AEM에 클라이언트측 호출을 수행할 수 있습니다. GraphQL 종단점에 액세스할 수 있도록 하려면 CORS 구성이 필요합니다.
feature: GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# CORS(원본 간 리소스 공유) 구성

>[!NOTE]
>
>AEM에서 CORS 리소스 공유 정책에 대한 자세한 개요는 다음을 참조하십시오 [CORS(원본 간 리소스 공유) 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html#understand-cross-origin-resource-sharing-(cors)).

GraphQL 종단점에 액세스하려면 CORS 정책을 구성하여 AEM Project에 추가해야 합니다 [Cloud Manager를 통해 AEM에 배포](/help/implementing/cloud-manager/deploy-code.md). 이 작업은 원하는 엔드포인트에 대한 적절한 OSGi CORS 구성 파일을 추가하여 수행합니다. 여러 CORS 구성을 만들어 다른 환경에 배포할 수 있습니다. 예제는 [WKND 참조 사이트](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig)

CORS 구성은 신뢰할 수 있는 웹 사이트 원본을 지정해야 합니다 `alloworigin` 또는 `alloworiginregexp` 액세스 권한을 부여해야 하는 대상.

구성 파일의 이름은 다음과 같습니다. `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json` 여기서 `appname` 은 응용 프로그램의 이름을 반영합니다.

예를 들어 GraphQL 종단점에 대한 액세스 권한을 부여하려면 `/content/cq:graphql/wknd/endpoint` 및 지속된 쿼리 끝점에 대해 `https://my.domain` 다음을 사용할 수 있습니다.

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

엔드포인트에 대한 별칭 경로를 구성한 경우, 이를 에서도 사용할 수 있습니다. `allowedpaths`.


