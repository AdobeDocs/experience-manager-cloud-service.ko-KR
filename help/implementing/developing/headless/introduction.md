---
title: Cloud Service의 헤드리스 개발
description: AEM은 컨텐츠 모델, 컨텐츠 조각 및 GraphQL API와 같은 강력한 기능을 Cloud Service으로 사용하여 중앙에서 경험을 관리하고 다양한 채널에 제공할 수 있습니다.
translation-type: tm+mt
source-git-commit: 712a99095494ab333cf0ebb2ac9fffe3f5945f3b
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 5%

---


# AEM Sites {#headless-development}으로 Cloud Service에 대한 헤드리스 개발

AEM은 컨텐츠 모델, 컨텐츠 조각 및 GraphQL API와 같은 강력한 기능을 Cloud Service으로 사용하여 중앙에서 경험을 관리하고 다양한 채널에 제공할 수 있습니다.

## 개요 {#overview}

헤드리스 구현은 채널 유형에 상관없이 어디서나 고객에게 경험을 전달하는 데 중요한 역할을 담당하고 있습니다.

헤드리스 구현은 일반적인 전체 스택 및 하이브리드 솔루션의 전형적인 페이지 및 구성 요소 관리로서 채널 중립적이고 재사용 가능한 컨텐츠 조각 및 크로스 채널 전달의 생성에 중점을 둡니다. 웹 경험을 구현하기 위한 현대적이고 동적인 개발 패턴입니다.

![AEM 구현 모델](assets/aem-implementation-models.png)

## AEM을 Cloud Service으로 사용하고 헤드리스 {#aem-headless}

CLOUD SERVICE의 AEM은 3개의 강력한 서비스를 제공하여 헤드리스 구현 모델을 위한 유연한 툴입니다.

1. 컨텐츠 모델
   * 컨텐츠 모델은 컨텐츠의 구조화된 표현입니다.
   * 이러한 정의는 AEM 컨텐츠 조각 모델 편집기의 정보 설계자에 의해 정의됩니다.
   * 컨텐츠 모델은 컨텐츠 조각의 기반이 됩니다.
1. 컨텐츠 조각
   * 컨텐츠 조각은 컨텐츠 모델의 인스턴스화합니다.
   * AEM 컨텐츠 조각 편집기를 사용하여 컨텐츠 작성자가 작성합니다.
   * AEM Assets에 저장되고 자산 관리 UI에서 관리됩니다.
1. 전달용 콘텐츠 API
   * AEM GraphQL API는 컨텐츠 조각 제공을 지원합니다.
   * AEM Assets REST API는 컨텐츠 조각 CRUD 작업을 지원합니다.
   * 직접 컨텐츠 배달은 [컨텐츠 조각 핵심 구성 요소의 JSON 내보내기를 사용할 수도 있습니다.](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/components/content-fragment-component.html)

## 헤드리스 시작 안내서 {#getting-started}

헤드리스 시작하기 안내서에서는 5단계만으로 AEM을 Cloud Service으로 사용하여 경험을 제작, 관리 및 전달하는 간단한 방법을 설명합니다. 각 안내선은 이전 버전을 기반으로 구축되므로 철저하게 순서대로 탐색하는 것이 좋습니다.

1. [구성 만들기](getting-started/create-configuration.md)
1. [컨텐츠 조각 모델 만들기](getting-started/create-content-model.md)
1. [자산 폴더 만들기](getting-started/create-assets-folder.md)
1. [컨텐츠 조각 만들기](getting-started/create-content-fragment.md)
1. [컨텐츠 조각 액세스 및 제공](getting-started/create-api-request.md)

## 속성을 확인하는 {#audience}

[헤드리스 시작 안내서](#getting-started)에 설명된 작업은 AEM 헤드리스 기능의 기본 엔드 투 엔드 데모를 위해 필요합니다. 관리자가 테스트 AEM 인스턴스에 액세스할 수 있는 사람은 개발자 경험이 있는 사람이면 누구나 이 가이드를 따라 AEM에서의 헤드리스 전달을 이해할 수 있습니다.

그러나 프로덕션 환경에서 작업은 여러 다른 사람에 의해 여러 번 수행됩니다. 예:

* **관리자** 는 컨텐츠의 초기 구성 및 폴더 구조를 일반적으로 한 번만 또는 산발적으로 설정해야 합니다.
* **정보** 아키텍처는 일반적으로 조직의 요구에 따라 새로운 모델을 추가합니다.
* **컨텐츠** 제작자는 설계자가 정의한 모델을 기반으로 컨텐츠 조각으로 새로운 컨텐츠를 지속적으로 제작합니다.

헤드리스 시작 안내서에서는 일반적으로 설명된 작업을 수행하는 사람과 얼마나 자주 수행하는지 알려줍니다.

## 다음 단계 {#next-step}

자세한 내용을 살펴보십시오. 그런 다음 헤드리스 시작 안내서의 첫 번째 부분을 읽고 시작합니다.[구성 만들기.](getting-started/create-configuration.md)
