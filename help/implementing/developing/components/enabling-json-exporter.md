---
title: 구성 요소에 대해 JSON 내보내기 활성화
description: 구성 요소는 모델러 프레임워크를 기반으로 컨텐츠의 JSON 내보내기를 생성하기 위해 채택할 수 있습니다.
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 8%

---


# 구성 요소에 대해 JSON 내보내기 활성화 {#enabling-json-export-for-a-component}

구성 요소는 모델러 프레임워크를 기반으로 컨텐츠의 JSON 내보내기를 생성하기 위해 채택할 수 있습니다.

## 개요 {#overview}

JSON 내보내기는 [Sling Models](https://sling.apache.org/documentation/bundles/models.html) 및 [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) 프레임워크를 기반으로 합니다. 이 프레임워크는 [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)에 의존합니다.

즉, JSON을 내보내야 하는 경우 구성 요소에 Sling 모델이 있어야 합니다. 따라서 이 두 단계를 따라 모든 구성 요소에서 JSON 내보내기를 활성화해야 합니다.

* [구성 요소에 대한 슬링 모델 정의](#define-a-sling-model-for-the-component)
* [슬링 모델 인터페이스에 주석 달기](#annotate-the-sling-model-interface)

## 구성 요소 {#define-a-sling-model-for-the-component}에 대한 슬링 모델 정의

먼저 구성 요소에 대해 슬링 모델을 정의해야 합니다.

>[!NOTE]
>
>Sling Models를 사용하는 예를 보려면 [AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/develop-sling-model-exporter.html)에서 Sling Model Proporters 개발 문서를 참조하십시오.

Sling Model 구현 클래스에 다음과 같은 주석을 추가해야 합니다.

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

이렇게 하면 `.model` 선택기 및 `.json` 확장을 사용하여 구성 요소를 직접 내보낼 수 있습니다.

또한 Sling Model 클래스를 `ComponentExporter` 인터페이스에 적용할 수 있음을 지정합니다.

>[!NOTE]
>
>잭슨 주석은 보통 슬링 모델 클래스 수준에서 지정되지 않고 모델 인터페이스 수준에서 지정됩니다. 이는 JSON 내보내기가 구성 요소 API의 일부로 간주되도록 하기 위한 것입니다.

>[!NOTE]
>
>`ExporterConstants` 및 `ComponentExporter` 클래스는 `com.adobe.cq.export.json` 번들에서 제공됩니다.

### 여러 선택기 사용 {#multiple-selectors}

표준 사용 사례는 아니지만 `model` 선택기 외에 여러 선택기를 구성할 수 있습니다.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

그러나 이러한 경우 `model` 선택기는 첫 번째 선택기여야 하며 확장자는 `.json`이어야 합니다.

## Sling 모델 인터페이스에 주석 달기 {#annotate-the-sling-model-interface}

JSON Exporter 프레임워크에서 고려하려면 모델 인터페이스가 `ComponentExporter` 인터페이스(또는 컨테이너 구성 요소의 경우 `ContainerExporter`)를 구현해야 합니다.

그런 다음 해당 Sling 모델 인터페이스(`MyComponent`)에 [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)를 사용하여 주석을 달아서 내보내기(직렬화)할 방법을 정의합니다.

모델 인터페이스에 일련화할 메서드를 정의하려면 제대로 주석을 달아야 합니다. 기본적으로 getter에 대한 일반적인 명명 규칙을 준수하는 모든 메서드는 serialize되고 getter 이름에서 JSON 속성 이름을 자연스럽게 파생하게 됩니다. JSON 속성 이름을 바꾸기 위해 `@JsonIgnore` 또는 `@JsonProperty`을 사용하여 이를 방지하거나 재정의할 수 있습니다.

## 예 {#example}

[핵심 구성 ](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html) 요소는 JSON 내보내기를 지원하며 참조로 사용할 수 있습니다.

예를 들어, 이미지 코어 구성 요소의 Sling 모델 구현과 주석 있는 인터페이스를 참조하십시오.

## 관련 설명서 {#related-documentation}

자세한 내용은 다음을 참조하십시오.

* [자산 사용 안내서의 컨텐츠 조각](/help/assets/content-fragments/content-fragments.md)
* [콘텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md)
* [컨텐츠 조각으로 작성](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [핵심 ](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) 구성 요소 및  [컨텐츠 조각 구성 요소](https://docs.adobe.com/content/help/kr/experience-manager-core-components/using/components/content-fragment-component.html)
