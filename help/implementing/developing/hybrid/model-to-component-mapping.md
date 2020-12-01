---
title: SPA에 대한 동적 모델과 구성 요소 간 매핑
description: 이 문서에서는 AEM용 Javascript SPA SDK에서 구성 요소에 대한 동적 모델이 발생하는 방법에 대해 설명합니다.
translation-type: tm+mt
source-git-commit: cdd92032c627740c66de7b2f3836fa1dcd2ee2ca
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 4%

---


# SPA에 대한 동적 모델과 구성 요소 간 매핑 {#dynamic-model-to-component-mapping-for-spas}

이 문서에서는 AEM용 Javascript SPA SDK에서 구성 요소에 대한 동적 모델 매핑이 발생하는 방법에 대해 설명합니다.

## ComponentMapping 모듈 {#componentmapping-module}

`ComponentMapping` 모듈은 프런트 엔드 프로젝트에 NPM 패키지로 제공됩니다. 프런트 엔드 구성 요소를 저장하고 단일 페이지 애플리케이션에서 프런트 엔드 구성 요소를 AEM 리소스 유형에 매핑할 수 있는 방법을 제공합니다. 이렇게 하면 응용 프로그램의 JSON 모델을 구문 분석할 때 구성 요소의 동적 확인이 가능합니다.

모델에 있는 각 항목에는 AEM 리소스 유형을 표시하는 `:type` 필드가 포함되어 있습니다. 마운트되면 프런트 엔드 구성 요소는 기본 라이브러리에서 받은 모델 조각을 사용하여 자체 렌더링할 수 있습니다.

모델 구문 분석 및 모델에 대한 프런트 엔드 구성 요소 액세스에 대한 자세한 내용은 [SPA Blueprint](blueprint.md) 문서를 참조하십시오.

npm 패키지를 참조하십시오.[@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## 모델 기반 단일 페이지 응용 프로그램 {#model-driven-single-page-application}

AEM용 Javascript SPA SDK를 활용하는 단일 페이지 애플리케이션은 모델 기반입니다.

1. 프런트 엔드 구성 요소는 [구성 요소 매핑 스토어](#componentmapping-module)에 자신을 등록합니다.
1. 그런 다음 [Container](blueprint.md#container)이(가) [Model Provider](blueprint.md#the-model-provider)에서 모델과 함께 제공되면 해당 모델 컨텐트(`:items`)에 대해 반복합니다.

1. 페이지의 경우, 해당 하위(`:children`)는 먼저 [Component Mapping](blueprint.md#componentmapping)에서 구성 요소 클래스를 가져온 다음 인스턴스화합니다.

## 앱 초기화 {#app-initialization}

각 구성 요소는 [`ModelProvider`](blueprint.md#the-model-provider)의 기능으로 확장됩니다. 따라서 초기화는 다음과 같은 일반 양식을 사용합니다.

1. 각 모델 공급자는 자체적으로 초기화하고 내부 구성 요소에 해당하는 모델 부분의 변경 사항을 수신합니다.
1. [`PageModelManager`](blueprint.md#pagemodelmanager)은 [초기화 흐름](blueprint.md)으로 표현되어야 합니다.

1. 저장 후 페이지 모델 관리자는 앱의 전체 모델을 반환합니다.
1. 그런 다음 이 모델은 응용 프로그램의 프런트 엔드 루트 [Container](blueprint.md#container) 구성 요소로 전달됩니다.
1. 모델의 일부가 결국 개별 하위 구성 요소에 전파됩니다.

![앱 모델 초기화](assets/app-model-initialization.png)
