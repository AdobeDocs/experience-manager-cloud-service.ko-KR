---
title: AEM Headless로 레퍼러 필터 구성
description: Adobe Experience Manager의 레퍼러 필터를 사용하면 서드파티 호스트에서 액세스할 수 있습니다. Headless 애플리케이션용 GraphQL 엔드포인트 액세스를 활성화하려면 레퍼러 필터에 대한 OSGi 구성이 필요합니다.
feature: Headless, GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
solution: Experience Manager
role: Admin, Developer
source-git-commit: 3096436f8057833419249d51cb6c15e6c28e9e13
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 55%

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

## 예제 구성 {#example-configuration}

예를 들어 레퍼러 `my.domain`이 있는 요청에 대한 액세스 권한을 부여하려면 다음과 같은 작업을 수행할 수 있습니다.

>[!CAUTION]
>
>이는 표준 구성을 덮어쓸 수 있는 기본 예입니다. 제품 업데이트가 모든 사용자 정의에 항상 적용되도록 해야 합니다.

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

## 데이터 보안 {#data-security}

>[!CAUTION]
>
>다음 사항을 완전히 해결하는 것은 귀하의 책임입니다.

데이터를 안전하게 유지하려면 다음을 확인해야 합니다.

* **만** 액세스가 트러스트된 도메인에 부여됨

* **not**&#x200B;의 와일드카드 [`*`] 구문이 사용되었습니다. 두 구문 모두 GraphQL 끝점에 대한 인증된 액세스를 비활성화하고 전 세계에 노출합니다.

* 중요한 정보가 **절대** 노출되지 않았습니다. 직접 또는 간접적으로 노출되지 않습니다.

   * 예를 들어 모든 [GraphQL 스키마](/help/headless/graphql-api/content-fragments.md#schema-generation)는 다음과 같습니다.

      * **사용**&#x200B;된 콘텐츠 조각 모델에서 파생됨

     **및**

      * GraphQL 엔드포인트를 통해 읽을 수 있습니다.

     즉, 모델 정의에서 필드 이름으로 표시되는 정보를 사용할 수 있습니다.

어떤 방법으로도 민감한 데이터를 사용할 수 없도록 해야 하므로 이러한 세부 사항을 신중하게 고려해야 합니다.
