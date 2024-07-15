---
title: SPA용 동적 모델과 구성 요소 간 매핑
description: 이 문서에서는 AEM용 JavaScript SPA SDK에서 동적 모델과 구성 요소 간 매핑이 발생하는 방법에 대해 설명합니다.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# SPA용 동적 모델과 구성 요소 간 매핑 {#dynamic-model-to-component-mapping-for-spas}

이 문서에서는 AEM용 JavaScript SPA SDK에서 동적 모델과 구성 요소 간 매핑이 발생하는 방식을 설명합니다.

## ComponentMapping 모듈 {#componentmapping-module}

`ComponentMapping` 모듈은 프론트엔드 프로젝트에 NPM 패키지로 제공됩니다. 프론트엔드 구성 요소를 저장하고, 단일 페이지 애플리케이션 이 프론트엔드 구성 요소를 AEM 리소스 유형에 매핑하는 방법을 제공합니다. 모듈은 애플리케이션의 JSON 모델을 구문 분석할 때 구성 요소의 동적 해결을 활성화합니다.

모델에 있는 각 항목에는 AEM 리소스 형식을 노출하는 `:type` 필드가 포함되어 있습니다. 마운트되면 프론트엔드 구성 요소는 기본 라이브러리에서 받은 모델 조각을 사용하여 자신을 렌더링할 수 있습니다.

모델 구문 분석 및 모델에 대한 프런트 엔드 구성 요소 액세스에 대한 자세한 내용은 [SPA 블루프린트](blueprint.md) 문서를 참조하십시오.

npm 패키지 [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)도 참조하십시오.

## 모델 기반 단일 페이지 애플리케이션 {#model-driven-single-page-application}

AEM용 JavaScript SPA SDK를 사용하는 단일 페이지 애플리케이션은 모델 기반의 애플리케이션입니다.

1. 프론트엔드 구성 요소가 [구성 요소 매핑 저장소](#componentmapping-module)에 등록됩니다.
1. [모델 공급자](blueprint.md#the-model-provider)에서 모델을 제공하면 [컨테이너](blueprint.md#container)이(가) 해당 모델 콘텐츠(`:items`)를 반복합니다.

1. 페이지가 있으면 자식(`:children`)이 먼저 [구성 요소 매핑](blueprint.md#componentmapping)에서 구성 요소 클래스를 가져온 다음 인스턴스화합니다.

## 앱 초기화 {#app-initialization}

각 구성 요소는 [`ModelProvider`](blueprint.md#the-model-provider)의 기능을 사용하여 확장됩니다. 따라서 초기화는 다음과 같은 일반적인 형식을 사용합니다.

1. 각 모델 공급자는 자신을 초기화하고 내부 구성 요소에 해당하는 모델 부분에 대한 변경 내용을 수신합니다.
1. [`PageModelManager`](blueprint.md#pagemodelmanager)은(는) [초기화 흐름](blueprint.md)에 표시된 대로 초기화되어야 합니다.

1. 저장되면 페이지 모델 관리자는 앱의 전체 모델을 반환합니다.
1. 그런 다음 이 모델은 응용 프로그램의 프런트 엔드 루트 [컨테이너](blueprint.md#container) 구성 요소로 전달됩니다.
1. 모델 조각이 최종적으로 각 개별 자 컴포넌트로 전파됩니다.

![앱 모델 초기화](assets/app-model-initialization.png)
