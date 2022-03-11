---
title: SPA에 대한 동적 모델과 구성 요소 간 매핑
description: 이 문서에서는 AEM용 Javascript SPA SDK에서 다이내믹 모델과 구성 요소 간 매핑이 발생하는 방법을 설명합니다.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 4%

---

# SPA에 대한 동적 모델과 구성 요소 간 매핑 {#dynamic-model-to-component-mapping-for-spas}

이 문서에서는 AEM용 Javascript SPA SDK에서 다이내믹 모델과 구성 요소 간 매핑이 발생하는 방법을 설명합니다.

## 구성 요소 매핑 모듈 {#componentmapping-module}

다음 `ComponentMapping` 모듈은 프런트 엔드 프로젝트에 NPM 패키지로 제공됩니다. 프런트엔드 구성 요소를 저장하고, 단일 페이지 애플리케이션에서 프런트엔드 구성 요소를 AEM 리소스 유형에 매핑할 수 있는 방법을 제공합니다. 이렇게 하면 애플리케이션의 JSON 모델을 구문 분석할 때 구성 요소를 동적으로 확인할 수 있습니다.

모델에 있는 각 항목에는 `:type` AEM 리소스 유형을 표시하는 필드입니다. 마운트되면 프런트 엔드 구성 요소는 기본 라이브러리에서 받은 모델 조각을 사용하여 자체 렌더링할 수 있습니다.

자세한 내용은 [SPA 블루프린트](blueprint.md) 모델 구문 분석 및 모델에 대한 프런트 엔드 구성 요소 액세스에 대한 자세한 내용은 문서를 참조하십시오.

npm 패키지도 참조하십시오. [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## 모델 기반의 단일 페이지 애플리케이션 {#model-driven-single-page-application}

AEM용 Javascript SPA SDK를 활용하는 단일 페이지 애플리케이션은 모델 기반입니다.

1. 프런트엔드 구성 요소는 [구성 요소 매핑 저장소](#componentmapping-module).
1. 그런 다음 [컨테이너](blueprint.md#container)에 의해 모델이 제공된 경우 [모델 공급자](blueprint.md#the-model-provider)는 해당 모델 컨텐츠(`:items`).

1. 페이지의 경우 해당 하위(`:children`)에서 먼저 구성 요소 클래스를 가져옵니다. [구성 요소 매핑](blueprint.md#componentmapping) 그런 다음 인스턴스화합니다.

## 앱 초기화 {#app-initialization}

각 구성 요소는 [`ModelProvider`](blueprint.md#the-model-provider). 따라서 초기화는 다음과 같은 일반 양식을 사용합니다.

1. 각 모델 공급자는 자신을 초기화하고 내부 구성 요소에 해당하는 모델 조각에 대한 변경 사항을 수신합니다.
1. 다음 [`PageModelManager`](blueprint.md#pagemodelmanager) 는 [초기화 흐름](blueprint.md).

1. 저장되면 페이지 모델 관리자는 앱의 전체 모델을 반환합니다.
1. 그런 다음 이 모델이 프런트 엔드 루트로 전달됩니다 [컨테이너](blueprint.md#container) 응용 프로그램의 구성 요소입니다.
1. 모델의 조각이 마침내 각 개별 하위 구성 요소에 전파됩니다.

![앱 모델 초기화](assets/app-model-initialization.png)
