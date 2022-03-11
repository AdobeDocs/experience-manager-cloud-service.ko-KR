---
title: AEM Headless로 레퍼러 필터 구성
description: Adobe Experience Manager의 레퍼러 필터를 사용하면 서드파티 호스트에서 액세스할 수 있습니다. Headless 애플리케이션용 GraphQL 끝점 액세스를 활성화하려면 레퍼러 필터에 대한 OSGi 구성이 필요합니다.
feature: GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 100%

---

# 레퍼러 필터 {#referrer-filter}

Adobe Experience Manager의 레퍼러 필터를 사용하면 서드파티 호스트에서 액세스할 수 있습니다. Headless 애플리케이션용 GraphQL 끝점 액세스를 활성화하려면 레퍼러 필터에 대한 OSGi 구성이 필요합니다.

다음과 같은 레퍼러 필터에 대한 적절한 OSGi 구성 추가를 통해 수행됩니다.

* 신뢰할 수 있는 웹 사이트 호스트 이름(`allow.hosts` 또는 `allow.hosts.regexp`)을 지정합니다.
* 이 호스트 이름에 대한 액세스 권한을 부여합니다.

파일 이름은 `org.apache.sling.security.impl.ReferrerFilter.cfg.json`이어야 합니다.

예를 들어 레퍼러 `my.domain`이 있는 요청에 대한 액세스 권한을 부여하려면 다음을 수행할 수 있습니다.

```xml
{
    "allow.empty":false,
    "allow.hosts":[
      "my.domain"
    ],
    "allow.hosts.regexp":[
      ""
    ],
    "filter.methods":[
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp":[
      ""
    ]
}
```

>[!CAUTION]
>
>다음에 대한 책임은 고객에게 있습니다.
>
>* 신뢰할 수 있는 도메인에만 액세스 권한을 부여하는 것
>* 민감한 정보가 노출되지 않도록 하는 것
>* 와일드카드 [*] 구문을 사용하지 않는 것. 사용하면 GraphQL 끝점에 대한 인증된 액세스가 비활성화되고 전 세계에 노출됩니다.


>[!CAUTION]
>
>모든 GraphQL [스키마](#schema-generation)(**활성화됨** 상태인 콘텐츠 조각 모델에서 파생)는 GraphQL 끝점을 통해 읽을 수 있습니다.
>
>즉, 이런 식으로 유출될 수 있기 때문에 민감한 데이터가 없는지 확인해야 합니다. 예를 들어 모델 정의에서 필드 이름으로 나타날 수 있는 정보가 여기에 포함됩니다.
