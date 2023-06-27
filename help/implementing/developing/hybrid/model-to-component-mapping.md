---
title: SPA에 대한 동적 모델과 구성 요소 간 매핑
description: 이 문서에서는 AEM용 JavaScript SPA SDK에서 동적 모델과 구성 요소 간 매핑이 발생하는 방법을 설명합니다.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 4%

---

# SPA에 대한 동적 모델과 구성 요소 간 매핑 {#dynamic-model-to-component-mapping-for-spas}

이 문서에서는 AEM용 JavaScript SPA SDK에서 동적 모델과 구성 요소 간 매핑이 발생하는 방법을 설명합니다.

## ComponentMapping 모듈 {#componentmapping-module}

다음 `ComponentMapping` 모듈은 프론트엔드 프로젝트에 NPM 패키지로 제공됩니다. 프론트엔드 구성 요소를 저장하고, 단일 페이지 애플리케이션 이 프론트엔드 구성 요소를 AEM 리소스 유형에 매핑하는 방법을 제공합니다. 모듈은 애플리케이션의 JSON 모델을 구문 분석할 때 구성 요소의 동적 해결을 활성화합니다.

모델에 있는 각 항목에는 `:type` AEM 리소스 유형을 표시하는 필드입니다. 마운트되면 프론트엔드 구성 요소는 기본 라이브러리에서 받은 모델 조각을 사용하여 자신을 렌더링할 수 있습니다.

다음을 참조하십시오 [SPA 블루프린트](blueprint.md) 모델 구문 분석 및 모델에 대한 프론트엔드 구성 요소 액세스에 대한 자세한 내용을 보려면 문서를 참조하십시오.

또한 npm 패키지 를 참조하십시오. [@adobe/aem-spa-component-매핑](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## 모델 기반 단일 페이지 애플리케이션 {#model-driven-single-page-application}

AEM용 JavaScript SPA SDK를 사용하는 단일 페이지 애플리케이션은 모델 기반의 애플리케이션입니다.

1. 프론트엔드 구성 요소는에 등록됩니다. [구성 요소 매핑 저장소](#componentmapping-module).
1. 그런 다음 [컨테이너](blueprint.md#container), 를 통해 모델이 제공되면 [모델 공급자](blueprint.md#the-model-provider), 모델 컨텐츠(`:items`).

1. 페이지가 있으면 그 하위 페이지(`:children`)에서 먼저 구성 요소 클래스를 가져옵니다. [구성 요소 매핑](blueprint.md#componentmapping) 그런 다음 인스턴스화합니다.

## 앱 초기화 {#app-initialization}

각 구성 요소는 의 기능으로 확장됩니다. [`ModelProvider`](blueprint.md#the-model-provider). 따라서 초기화는 다음과 같은 일반적인 형식을 사용합니다.

1. 각 모델 공급자는 자신을 초기화하고 내부 구성 요소에 해당하는 모델 부분에 대한 변경 내용을 수신합니다.
1. 다음 [`PageModelManager`](blueprint.md#pagemodelmanager) 은(는) 로 표시된 대로 초기화해야 합니다. [초기화 흐름](blueprint.md).

1. 저장되면 페이지 모델 관리자는 앱의 전체 모델을 반환합니다.
1. 그런 다음 이 모델은 프론트엔드 루트로 전달됩니다 [컨테이너](blueprint.md#container) 응용 프로그램의 구성 요소입니다.
1. 모델 조각이 최종적으로 각 개별 자 컴포넌트로 전파됩니다.

![앱 모델 초기화](assets/app-model-initialization.png)
