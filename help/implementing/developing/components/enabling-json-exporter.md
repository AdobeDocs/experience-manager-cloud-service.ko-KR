---
title: 구성 요소에 대해 JSON 내보내기 활성화
description: 구성 요소를 모델러 프레임워크를 기반으로 해당 컨텐츠의 JSON 내보내기를 생성하도록 조정할 수 있습니다.
exl-id: e9be5c0c-618e-4b56-a365-fcdd185ae808
source-git-commit: 6be7cc7678162c355c39bc3000716fdaf421884d
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 11%

---

# 구성 요소에 대해 JSON 내보내기 활성화 {#enabling-json-export-for-a-component}

구성 요소를 모델러 프레임워크를 기반으로 해당 컨텐츠의 JSON 내보내기를 생성하도록 조정할 수 있습니다.

## 개요 {#overview}

JSON 내보내기는 다음을 기반으로 합니다 [Sling 모델](https://sling.apache.org/documentation/bundles/models.html), 및 [Sling 모델 내보내기](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) 프레임워크(자체 [잭슨 주석](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

즉, JSON을 내보내려면 구성 요소에 Sling 모델이 있어야 합니다. 따라서 구성 요소에서 JSON 내보내기를 활성화하려면 이 두 단계를 수행해야 합니다.

* [구성 요소에 대한 Sling 모델 정의](#define-a-sling-model-for-the-component)
* [Sling 모델 인터페이스에 주석 달기](#annotate-the-sling-model-interface)

## 구성 요소에 대한 Sling 모델 정의 {#define-a-sling-model-for-the-component}

먼저 구성 요소에 대해 Sling 모델을 정의해야 합니다.

>[!NOTE]
>
>Sling 모델 사용 예는 문서를 참조하십시오 [AEM에서 Sling 모델 내보내기 개발](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html).

Sling 모델 구현 클래스에 다음과 같은 주석을 달아야 합니다.

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

이렇게 하면 구성 요소를 `.model` 선택기 및 `.json` 확장.

또한 Sling 모델 클래스를 `ComponentExporter` 인터페이스.

>[!NOTE]
>
>Jackson 주석은 일반적으로 Sling 모델 클래스 수준에서 지정되지 않고 모델 인터페이스 수준에서 지정됩니다. JSON 내보내기 가 구성 요소 API의 일부로 간주되도록 하기 위한 것입니다.

>[!NOTE]
>
>다음 `ExporterConstants` 및 `ComponentExporter` 클래스는 `com.adobe.cq.export.json` 번들입니다.

### 여러 선택기 사용 {#multiple-selectors}

표준 사용 사례는 아니지만 `model` 선택기.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

그러나 이러한 경우에는 `model` 선택기는 첫 번째 선택기여야 하며 확장은 다음 형식이어야 합니다. `.json`.

## Sling 모델 인터페이스에 주석 달기 {#annotate-the-sling-model-interface}

JSON Exporter 프레임워크에서 고려하려면 모델 인터페이스가 다음을 구현해야 합니다 `ComponentExporter` 인터페이스(또는 `ContainerExporter`: 컨테이너 구성 요소의 경우)

해당 Sling 모델 인터페이스(`MyComponent`)을 사용하여 주석을 답니다 [잭슨 주석](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) 를 내보내는(직렬화) 방법을 정의합니다.

모델 인터페이스에 serialize해야 하는 메서드를 정의하려면 올바르게 주석을 추가해야 합니다. 기본적으로 getter에 대한 일반적인 이름 지정 규칙을 준수하는 모든 메서드는 직렬화되고 getter 이름에서 JSON 속성 이름을 자연적으로 파생합니다. 이 경우 `@JsonIgnore` 또는 `@JsonProperty` 를 JSON 속성의 이름을 바꾸는 데 사용됩니다.

## 예 {#example}

[핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko) json 내보내기를 지원하고 참조로 사용할 수 있습니다.

예를 들어 이미지 코어 구성 요소의 Sling 모델 구현과 주석으로 구성된 인터페이스를 참조하십시오.

## 관련 설명서 {#related-documentation}

자세한 내용은 다음을 참조하십시오.

* [콘텐츠 조각](/help/sites-cloud/administering/content-fragments/content-fragments.md)
* [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragments-models.md)
* [컨텐츠 조각으로 작성](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 그리고 [컨텐츠 조각 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=ko-KR)
