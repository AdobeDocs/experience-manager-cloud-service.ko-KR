---
title: Sling Model 내보내기를 통한 ResourceResolver 직렬화 허용 안 함
description: Sling Model 내보내기를 통한 ResourceResolver 직렬화 허용 안 함
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 5%

---

# Sling Model 내보내기를 통한 ResourceResolver 직렬화 허용 안 함 {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

슬링 모델 내보내기 기능을 사용하면 슬링 모델 개체를 JSON 형식으로 serialize할 수 있습니다. 이 기능은 SPA(단일 페이지 애플리케이션)가 AEM의 데이터에 쉽게 액세스할 수 있도록 하므로 널리 사용됩니다. 구현 측면에서는 Jacson Databind 라이브러리를 사용하여 이러한 개체를 serialize합니다.

직렬화는 재귀 연산입니다. &quot;루트 오브젝트&quot;부터 시작하여 모든 적격 오브젝트를 재귀적으로 반복하고 오브젝트 및 해당 하위 오브젝트를 직렬화합니다. [이 문서](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)에서 직렬화된 필드에 대한 설명을 찾을 수 있습니다.

이 접근 방식은 모든 유형의 개체를 JSON으로 serialize하며 serialization 규칙이 적용되는 경우 Sling `ResourceResolver` 개체도 serialize할 수 있습니다. `ResourceResolver` 서비스(및 이를 나타내는 서비스 개체)에는 잠재적으로 중요한 정보가 포함되어 있으므로 공개해서는 안 되므로 문제가 됩니다. 예:

* 사용자 ID
* 상대 경로를 확인하기 위한 검색 경로
* `propertyMap`.

`propertyMap`은(는) 내부 데이터 구조이므로 특히 중요합니다([`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)의 API 설명서 참조). 내부 데이터 구조는 `ResourceResolver`과(와) 동일한 주기를 공유하는 개체를 캐시하는 등 다양한 용도로 사용할 수 있습니다. 이러한 항목을 직렬화하면 최종 사용자가 읽기 및 액세스할 수 없는 데이터가 노출되므로 구현 세부 사항이 누출될 수 있으며 보안 영향을 받을 수 있습니다. 이러한 이유로 `ResourceResolvers`을(를) JSON으로 serialize하면 안 됩니다.

Adobe은 2단계 접근 방식으로 `ResourceResolvers`의 serialization을 비활성화할 계획입니다.

1. AEM as a Cloud Service 릴리스 14697부터 `ResourceResolver`이(가) serialize될 때마다 AEM에 경고 메시지가 기록됩니다. 모든 고객은 애플리케이션 로그에서 이러한 로그 설명을 확인하고 이에 따라 코드베이스를 조정하는 것이 좋습니다.
1. 나중에 Adobe을 수행하면 ResourceResolver가 JSON으로 직렬화되지 않습니다.

## 구현 {#implementation}

WARN 메시지는 AEM as a Cloud Service 및 로컬 AEM SDK 인스턴스에 모두 기록되며 다음과 같습니다.

```
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

이 로그 메시지는 `/content/…/page`을(를) JSON으로 serialize하는 동안 `ResourceResolver`이(가) 이미 serialize되었음을 의미합니다. `/content/../page.model.json`을(를) 요청하면 `ResourceResolver`의 필드가 정확히 어디에 표시되는지 확인하고 이를 사용하여 이 동작을 실제로 트리거하는 Sling Model 클래스를 식별할 수 있습니다.


>[!NOTE]
>
>AEM 핵심 구성 요소는 이 문제의 영향을 받지 않습니다.

## 요청된 작업 {#requested-action}

Adobe은 모든 고객에게 이 문제의 영향을 받는지 애플리케이션 로그와 코드 베이스를 확인하고 필요한 경우 사용자 정의 애플리케이션을 변경하여 이 경고 메시지가 더 이상 표시되지 않도록 할 것을 요청합니다.

`ResourceResolver` 개체는 JSON 출력에 전혀 필요하지 않으며, 해당 개체에 포함된 정보는 일반적으로 프론트엔드 응용 프로그램에 필요하지 않으므로 대부분의 경우 이러한 필수 변경 내용은 정방향이라고 가정합니다. 즉, 대부분의 경우 `ResourceResolver` 개체가 Jackson에서 고려되지 않도록 제외하는 것으로 충분합니다([규칙](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not) 참조).

슬링 모델이 이 문제의 영향을 받지만 변경되지 않는 경우, `ResourceResolver` 개체의 직렬화를 명시적으로 사용하지 않도록 설정(두 번째 단계로 Adobe에서 실행)하면 JSON 출력이 변경됩니다.
