---
title: AEM Headless를 사용한 레퍼러 필터 구성
description: Adobe Experience Manager의 레퍼러 필터를 사용하면 타사 호스트에서 액세스할 수 있습니다. 헤드리스 애플리케이션의 GraphQL 종단점에 액세스할 수 있으려면 레퍼러 필터에 대한 OSGi 구성이 필요합니다.
feature: GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# 레퍼러 필터 {#referrer-filter}

Adobe Experience Manager의 레퍼러 필터를 사용하면 타사 호스트에서 액세스할 수 있습니다. 헤드리스 애플리케이션의 GraphQL 종단점에 액세스할 수 있으려면 레퍼러 필터에 대한 OSGi 구성이 필요합니다.

이 작업은 레퍼러 필터에 적절한 OSGi 구성을 추가하여 수행합니다.

* 신뢰할 수 있는 웹 사이트 호스트 이름을 지정합니다. 둘 중 하나 `allow.hosts` 또는 `allow.hosts.regexp`,
* 이 호스트 이름에 대한 액세스 권한을 부여합니다.

파일 이름은 다음과 같아야 합니다. `org.apache.sling.security.impl.ReferrerFilter.cfg.json`.

예를 들어 레퍼러가 있는 요청에 대한 액세스 권한을 부여하려면 `my.domain` 다음을 수행할 수 있습니다.

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
>고객이 다음 작업을 수행할 책임이 있습니다.
>
>* 신뢰할 수 있는 도메인에 대한 액세스 권한만 부여
>* 중요한 정보가 노출되지 않도록 합니다.
>* 와일드카드 사용 안 함 [*] 구문; 이렇게 하면 GraphQL 종단점에 대한 인증된 액세스를 비활성화하고 전체 세계에 노출됩니다.


>[!CAUTION]
>
>모든 GraphQL [스키마](#schema-generation) (컨텐츠 조각 모델에서 파생됨 **활성화됨**)은 GraphQL 종단점을 통해 읽을 수 있습니다.
>
>이는 민감한 데이터가 이러한 방식으로 유출될 수 있으므로 사용할 수 없도록 해야 함을 의미합니다. 예를 들어 모델 정의에서 필드 이름으로 존재할 수 있는 정보가 포함됩니다.
