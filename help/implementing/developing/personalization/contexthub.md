---
title: ContextHub
description: ContextHub는 컨텍스트 데이터를 저장, 조작 및 제공하기 위한 프레임워크입니다
exl-id: 604477c6-d96a-441f-b5fc-5def93832478
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---

# ContextHub {#contexthub}

ContextHub는 컨텍스트 데이터를 저장, 조작 및 제공하기 위한 프레임워크입니다. 이 기능은 다양한 가상 사용자 간에 시뮬레이션을 하고 전환하는 동안 [컨텍스트 데이터를 볼 수 있는 기능을 제공하는 주요 기능입니다.](/help/sites-cloud/authoring/personalization/contexthub.md)

ContextHub를 사용하여 다음을 수행할 수 있습니다.

* [컨텍스트 데이터를 사용하여 페이지를 작성하는 동안 가상 사용자](#presentation) 를 표시하고 전환하며 사용자 경험을 시뮬레이션할 수 있습니다.
* [웹 ](#persistence) 사이트에서 컨텍스트 데이터를 데이터 레이어 표현으로 유지합니다.
* [선택한 ](#segmentation) 컨텍스트의 세그먼트를 관리합니다.

클라이언트측 Javascript API를 사용하면 컨텐츠를 개인화하기 위해 데이터에 액세스할 수 있습니다.

## 프레젠테이션 {#presentation}

[ContextHub 도구 모음](/help/sites-cloud/authoring/personalization/contexthub.md)을 사용하면 마케터와 작성자가 페이지를 작성할 때 사용자 경험을 시뮬레이션하기 위해 저장소 데이터를 보고 조작할 수 있습니다. 도구 모음은 [ContextHub 저장소에 액세스할 수 있는 UI 모듈 그룹,](#persistence)은 클라이언트의 ContextHub 데이터를 유지합니다.

각 ContextHub UI 모듈은 사전 정의된 모듈 유형의 인스턴스입니다.

* ContextHub에서는 몇 가지 [샘플 모듈 유형](sample-modules.md)을 제공합니다.
* AEM 콘솔을 사용하여 [UI 모듈](configuring-contexthub.md#adding-a-ui-module)을 추가하고, [UI 모드](configuring-contexthub.md#adding-a-ui-mode)로 그룹화합니다.
* 개발자는 [사용자 지정 모듈 유형](extending-contexthub.md#creating-contexthub-ui-module-types)을 만들 수 있습니다.

개발자는 [ContextHub 구성 요소를 페이지](configuring-contexthub.md)에 추가해야 합니다.

## 지속성 {#persistence}

ContextHub는 클라이언트에서 컨텍스트 데이터를 유지합니다. ContextHub Javascript API를 사용하면 필요에 따라 데이터를 생성, 업데이트 및 삭제하기 위해 저장소에 액세스할 수 있습니다. 이와 같이 ContextHub는 페이지의 데이터 계층을 나타냅니다.

각 ContextHub 저장소는 사전 정의된 저장소 유형의 인스턴스입니다.

* ContextHub에서는 몇 가지 [샘플 저장소 유형](sample-stores.md)을 제공합니다.
* AEM 콘솔을 사용하여 [저장소를 만듭니다](configuring-contexthub.md#creating-a-contexthub-store).
* 개발자는 [사용자 지정 저장소 유형](extending-contexthub.md#creating-custom-store-candidates)을 만들 수 있습니다.
* 개발자는 Javascript를 통해 [스토어 데이터](adding-contexthub.md#interacting-with-contexthub-stores)에 액세스할 수 있습니다.

## 세그멘테이션 {#segmentation}

ContextHub에는 세그먼트를 관리하고 현재 컨텍스트에 대해 해결된 세그먼트를 결정하는 세그멘테이션 엔진이 포함되어 있습니다. 여러 세그먼트가 정의됩니다. Javascript API를 사용하여 [해결된 세그먼트를 결정할 수 있습니다](adding-contexthub.md#determining-resolved-contexthub-segments).
