---
title: ContextHub
description: ContextHub는 컨텍스트 데이터를 저장, 조작 및 표시하기 위한 프레임워크입니다
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---

# ContextHub {#contexthub}

ContextHub는 컨텍스트 데이터를 저장, 조작 및 표시하기 위한 프레임워크입니다. 주요 기능은 다음과 같은 기능을 제공하는 것입니다. [다양한 가상 사용자 간 시뮬레이션 및 전환 시 컨텍스트 데이터 보기](/help/sites-cloud/authoring/personalization/contexthub.md).

ContextHub를 사용하여 다음을 수행할 수 있습니다.

* [사용자 경험 프레젠테이션, 보기, 전환 및 시뮬레이션](#presentation) 컨텍스트 데이터를 사용하여 페이지를 작성하는 동안
* [컨텍스트 데이터 유지](#persistence) 를 데이터 레이어 표현으로 웹 사이트에 추가합니다.
* [세그먼트 관리](#segmentation) 선택한 컨텍스트에 사용됩니다.

클라이언트측 JavaScript API를 사용하면 콘텐츠를 개인화하기 위한 데이터에 액세스할 수 있습니다.

## 프레젠테이션 {#presentation}

다음 [ContextHub 도구 모음](/help/sites-cloud/authoring/personalization/contexthub.md) 마케터와 작성자가 페이지를 작성할 때 사용자 경험을 시뮬레이션하기 위해 스토어 데이터를 보고 조작할 수 있습니다. 도구 모음은 다음에 대한 액세스를 제공하는 UI 모듈 그룹으로 구성됩니다 [ContextHub 저장소,](#persistence) 클라이언트에서 ContextHub 데이터를 유지합니다.

각 ContextHub UI 모듈은 사전 정의된 모듈 유형의 인스턴스입니다.

* ContextHub는 몇 가지 기능을 제공합니다. [샘플 모듈 유형](sample-modules.md).
* AEM 콘솔을 사용하여 [ui 모듈 추가](configuring-contexthub.md#adding-a-ui-module), 및 까지 [ui 모드로 그룹화합니다.](configuring-contexthub.md#adding-a-ui-mode).
* 개발자는 [사용자 정의 모듈 유형 만들기](extending-contexthub.md#creating-contexthub-ui-module-types).

개발자는 [페이지에 ContextHub 구성 요소 추가](configuring-contexthub.md).

## 지속성 {#persistence}

ContextHub 저장소는 클라이언트에 컨텍스트 데이터를 유지합니다. ContextHub JavaScript API를 사용하면 저장소에 액세스하여 필요에 따라 데이터를 작성, 업데이트 및 삭제할 수 있습니다. 따라서 ContextHub는 페이지의 데이터 계층을 나타냅니다.

각 ContextHub 저장소는 사전 정의된 저장소 유형의 인스턴스입니다.

* ContextHub는 몇 가지 기능을 제공합니다. [샘플 저장소 유형](sample-stores.md).
* AEM 콘솔을 사용하여 [스토어 만들기](configuring-contexthub.md#creating-a-contexthub-store).
* 개발자는 [사용자 지정 저장소 유형 만들기](extending-contexthub.md#creating-custom-store-candidates).
* 개발자는 [저장소 데이터 액세스](adding-contexthub.md#interacting-with-contexthub-stores) 을 참조하십시오.

## 세분화 {#segmentation}

ContextHub에는 세그먼트를 관리하고 현재 컨텍스트에 대해 해결할 세그먼트를 결정하는 세그먼테이션 엔진이 포함되어 있습니다. 여러 개의 세그먼트가 정의됩니다. JavaScript API를 사용하여 다음과 같은 작업을 수행할 수 있습니다 [해결된 세그먼트 결정](adding-contexthub.md#determining-resolved-contexthub-segments).
