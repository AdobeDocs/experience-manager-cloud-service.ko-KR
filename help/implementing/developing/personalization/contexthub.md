---
title: ContextHub
description: ContextHub는 컨텍스트 데이터를 저장, 조작 및 표시하기 위한 프레임워크입니다
translation-type: tm+mt
source-git-commit: b8bc27b51eefcfcfa1c23407a4ac0e7ff068081e
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# ContextHub {#contexthub}

ContextHub는 컨텍스트 데이터를 저장, 조작 및 표시하기 위한 프레임워크입니다. 이 기능의 기본 기능은 다양한 페르소나를 시뮬레이션하고 전환하는 동안 컨텍스트 데이터를 [보는 기능을 제공합니다.](/help/sites-cloud/authoring/personalization/contexthub.md)

다음을 수행할 수 있는 ContextHub

* [컨텍스트 데이터를 사용하여 페이지를 작성할 때 사용자 ](#presentation) 경험을 제공, 확인, 전환 및 시뮬레이션할 수 있습니다.
* [웹 ](#persistence) 사이트의 컨텍스트 데이터를 데이터 레이어 표현으로 유지합니다.
* [선택한 ](#segmentation) 컨텍스트에 대한 세그먼트를 관리합니다.

클라이언트측 Javascript API를 사용하면 컨텐츠를 개인화하기 위해 데이터에 액세스할 수 있습니다.

## 프레젠테이션 {#presentation}

[ContextHub 도구 모음](/help/sites-cloud/authoring/personalization/contexthub.md)을 사용하면 마케터와 작성자는 페이지를 작성할 때 사용자 경험을 시뮬레이션하기 위해 저장소 데이터를 보고 조작할 수 있습니다. 도구 모음은 클라이언트에서 ContextHub 데이터를 유지하는 [ContextHub 저장소,](#persistence)에 대한 액세스를 제공하는 UI 모듈 그룹으로 구성됩니다.

각 ContextHub UI 모듈은 사전 정의된 모듈 유형의 인스턴스입니다.

* ContextHub에서는 몇 가지 [샘플 모듈 유형](sample-modules.md)을 제공합니다.
* AEM 콘솔을 사용하여 [UI 모듈](configuring-contexthub.md#adding-a-ui-module)을 추가하고 UI 모드](configuring-contexthub.md#adding-a-ui-mode)에서 그룹화합니다.[
* 개발자는 [사용자 정의 모듈 유형](extending-contexthub.md#creating-contexthub-ui-module-types)을 만들 수 있습니다.

개발자는 [페이지](configuring-contexthub.md)에 ContextHub 구성 요소를 추가해야 합니다.

## 지속성 {#persistence}

ContextHub 저장소는 클라이언트에 컨텍스트 데이터를 저장합니다. ContextHub Javascript API를 사용하면 필요에 따라 데이터를 생성, 업데이트 및 삭제할 수 있는 저장소에 액세스할 수 있습니다. 따라서 ContextHub은 페이지의 데이터 레이어를 나타냅니다.

각 ContextHub 저장소는 사전 정의된 저장소 유형의 인스턴스입니다.

* ContextHub에서는 몇 가지 [샘플 저장소 유형](sample-stores.md)을 제공합니다.
* AEM 콘솔을 사용하여 [스토어](configuring-contexthub.md#creating-a-contexthub-store)를 만듭니다.
* 개발자는 [사용자 정의 스토어 유형](extending-contexthub.md#creating-custom-store-candidates)을 만들 수 있습니다.
* 개발자는 Javascript를 통해 [스토어 데이터](adding-contexthub.md#interacting-with-contexthub-stores)에 액세스할 수 있습니다.

## 세그멘테이션 {#segmentation}

ContextHub에는 세그먼트를 관리하고 현재 컨텍스트에 대해 해결된 세그먼트를 결정하는 세그멘테이션 엔진이 포함되어 있습니다. 여러 세그먼트가 정의됩니다. Javascript API를 사용하여 [해결된 세그먼트](adding-contexthub.md#determining-resolved-contexthub-segments)를 결정할 수 있습니다.
