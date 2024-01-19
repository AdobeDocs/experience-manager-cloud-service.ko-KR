---
title: Sling 모델 내보내기를 통한 ResourceResolver 직렬화 허용 안 함
description: Sling 모델 내보내기를 통한 ResourceResolver 직렬화 허용 안 함
source-git-commit: 4543a4646719f8433df7589b21344433c43ab432
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Sling 모델 내보내기를 통한 ResourceResolver 직렬화 허용 안 함 {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

슬링 모델 내보내기 기능을 사용하면 슬링 모델 개체를 JSON 형식으로 serialize할 수 있습니다. 이 기능은 SPA(단일 페이지 애플리케이션)가 AEM의 데이터에 쉽게 액세스할 수 있도록 하므로 널리 사용됩니다. 구현 측면에서는 Jacson Databind 라이브러리를 사용하여 이러한 개체를 serialize합니다.

직렬화는 재귀 연산입니다. &quot;루트 오브젝트&quot;부터 시작하여 모든 적격 오브젝트를 재귀적으로 반복하고 오브젝트 및 해당 하위 오브젝트를 직렬화합니다. 직렬화된 필드에 대한 설명을 찾을 수 있습니다 [이 문서](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).

이 접근 방식은 모든 유형의 개체를 JSON으로 직렬화하고, 자연스럽게 Sling도 직렬화할 수 있습니다 `ResourceResolver` object(직렬화 규칙이 적용되는 경우). 이는 다음과 같이 문제가 있습니다. `ResourceResolver` 서비스(따라서 이를 나타내는 서비스 개체)에는 잠재적으로 중요한 정보가 포함되어 있으므로 공개해서는 안 됩니다. 예:

* 사용자 ID
* 상대 경로를 확인하기 위한 검색 경로
* 다음 `propertyMap`.

특히 민감한 사항은 다음과 같습니다. `propertyMap` ( 의 API 설명서 참조) [`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--))는 내부 데이터 구조로서, 여러 용도로 사용할 수 있습니다(예: 와 동일한 주기를 공유하는 객체 캐싱). `ResourceResolver`. 이러한 항목을 직렬화하면 최종 사용자가 읽기 및 액세스할 수 없는 데이터가 노출되므로 구현 세부 사항이 누출될 수 있으며 보안 영향을 받을 수 있습니다. 그 이유로 `ResourceResolvers` 는 JSON으로 직렬화하면 안 됩니다.

Adobe은 의 직렬화를 비활성화할 계획입니다. `ResourceResolvers` 2단계 접근 방식:

1. AEM as a Cloud Service 릴리스 14697으로 시작하여 `ResourceResolver` 가 직렬화되면 AEM에 경고 메시지가 기록됩니다. 모든 고객은 애플리케이션 로그에서 이러한 로그 설명을 확인하고 이에 따라 코드베이스를 조정하는 것이 좋습니다.
1. 나중에 Adobe을 수행하면 ResourceResolver가 JSON으로 직렬화되지 않습니다.

## 구현 {#implementation}

WARN 메시지는 AEM as a Cloud Service 및 로컬 AEM SDK 인스턴스에 모두 기록되며 다음과 같습니다.

```
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

이 로그 메시지는 을(를) 직렬화하는 동안 `/content/…/page` json a에 `ResourceResolver` 은(는) 이미 직렬화되었습니다. 요청별 `/content/../page.model.json` 필드의 정확한 위치를 확인할 수 있습니다. `ResourceResolver` 가 표시되는 경우 이를 사용하여 실제로 이 동작을 트리거하는 슬링 모델 클래스를 식별합니다.


>[!NOTE]
>
>AEM 핵심 구성 요소는 이 문제의 영향을 받지 않습니다.

## 요청된 작업 {#requested-action}

Adobe은 모든 고객에게 이 문제의 영향을 받는지 애플리케이션 로그와 코드 베이스를 확인하고 필요한 경우 사용자 정의 애플리케이션을 변경하여 이 경고 메시지가 더 이상 표시되지 않도록 할 것을 요청합니다.

대부분의 경우 다음과 같이 필요한 이러한 변경 사항은 정면으로 진행된다고 가정합니다. `ResourceResolver` 포함된 정보는 일반적으로 프론트엔드 애플리케이션에 필요하지 않으므로 개체는 JSON 출력에 전혀 필요하지 않습니다. 즉, 대부분의 경우 다음을 제외하는 것으로 충분합니다. `ResourceResolver` 오브젝트가 Jackson에 의해 고려되지 않음(참조: [규칙](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)).

슬링 모델이 이 문제의 영향을 받지만 변경되지 않는 경우, 의 정규화를 명시적으로 비활성화합니다. `ResourceResolver` 개체(두 번째 단계로 Adobe에서 실행됨)는 JSON 출력의 변경 내용을 적용합니다.



