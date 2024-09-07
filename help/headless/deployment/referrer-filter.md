---
title: AEM Headless로 레퍼러 필터 구성
description: Adobe Experience Manager의 레퍼러 필터를 사용하면 서드파티 호스트에서 액세스할 수 있습니다. Headless 애플리케이션용 GraphQL 엔드포인트 액세스를 활성화하려면 레퍼러 필터에 대한 OSGi 구성이 필요합니다.
feature: Headless, GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
solution: Experience Manager
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: ht
source-wordcount: '275'
ht-degree: 100%

---

# 레퍼러 필터 {#referrer-filter}

Adobe Experience Manager의 레퍼러 필터를 사용하면 서드파티 호스트에서 액세스할 수 있습니다.

HTTP POST를 통해 Headless 애플리케이션용 GraphQL 엔드포인트 액세스를 활성화하려면 레퍼러 필터에 대한 OSGi 구성이 필요합니다. HTTP GET을 통해 AEM에 액세스하는 AEM Headless 지속 쿼리를 사용하는 경우 레퍼러 필터 구성이 필요하지 않습니다.

>[!WARNING]
> AEM의 레퍼러 필터는 OSGi 구성 팩토리가 아니므로 한 번에 하나의 구성만 AEM 서비스에서 활성화됩니다. 가능한 경우 사용자 정의 레퍼러 필터 구성을 추가하지 마십시오. AEM의 기본 구성을 덮어쓰고 제품 기능을 손상시킬 수 있습니다.

다음과 같은 레퍼러 필터에 대한 적절한 OSGi 구성 추가를 통해 수행됩니다.

* 신뢰할 수 있는 웹 사이트 호스트 이름(`allow.hosts` 또는 `allow.hosts.regexp`)을 지정합니다.
* 이 호스트 이름에 대한 액세스 권한을 부여합니다.

파일 이름은 `org.apache.sling.security.impl.ReferrerFilter.cfg.json`이어야 합니다.

예를 들어 레퍼러 `my.domain`이 있는 요청에 대한 액세스 권한을 부여하려면 다음과 같은 작업을 수행할 수 있습니다.

```xml
{
    "allow.empty": false,
    "allow.hosts": [
      "my.domain"
    ],
    "allow.hosts.regexp": [
      ""
    ],
    "filter.methods": [
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp": [
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
>* 와일드카드 [*] 구문을 사용하지 않는 것. 사용하면 GraphQL 엔드포인트에 대한 인증된 액세스가 비활성화되고 전 세계에 노출됩니다.

>[!CAUTION]
>
>모든 GraphQL [스키마](#schema-generation)(**활성화됨** 상태인 콘텐츠 조각 모델에서 파생)는 GraphQL 엔드포인트를 통해 읽을 수 있습니다.
>
>즉, 이런 식으로 유출될 수 있기 때문에 민감한 데이터가 없는지 확인해야 합니다. 예를 들어 모델 정의에서 필드 이름으로 나타날 수 있는 정보가 여기에 포함됩니다.
