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

ContextHub는 컨텍스트 데이터를 저장, 조작 및 표시하기 위한 프레임워크입니다. 기본 기능은 [다양한 가상 사용자를 시뮬레이션하고 전환하는 동안 컨텍스트 데이터를 보는 기능](/help/sites-cloud/authoring/personalization/contexthub.md)을 제공합니다.

ContextHub를 사용하여 다음을 수행할 수 있습니다.

* 컨텍스트 데이터를 사용하여 페이지를 작성하는 동안 [가상 사용자를 보고, 전환하고, 사용자 환경을 시뮬레이션](#presentation)합니다.
* 웹 사이트에서 컨텍스트 데이터를 데이터 레이어 표현으로 [유지](#persistence).
* 선택한 컨텍스트의 [세그먼트 관리](#segmentation).

클라이언트측 JavaScript API를 사용하면 콘텐츠를 개인화하기 위한 데이터에 액세스할 수 있습니다.

## 프레젠테이션 {#presentation}

[ContextHub 도구 모음](/help/sites-cloud/authoring/personalization/contexthub.md)을(를) 사용하면 마케터와 작성자가 페이지를 작성할 때 사용자 환경을 시뮬레이션하기 위해 저장소 데이터를 보고 조작할 수 있습니다. 도구 모음은 클라이언트에서 ContextHub 데이터를 유지하는 [ContextHub 저장소,](#persistence)에 대한 액세스를 제공하는 UI 모듈 그룹으로 구성됩니다.

각 ContextHub UI 모듈은 사전 정의된 모듈 유형의 인스턴스입니다.

* ContextHub는 여러 [샘플 모듈 유형](sample-modules.md)을 제공합니다.
* AEM 콘솔을 사용하여 [UI 모듈을 추가](configuring-contexthub.md#adding-a-ui-module)하고 [UI 모드에서 해당 모듈을 그룹화](configuring-contexthub.md#adding-a-ui-mode)하십시오.
* 개발자는 [사용자 지정 모듈 유형을 만들 수 있습니다](extending-contexthub.md#creating-contexthub-ui-module-types).

개발자는 [ContextHub 구성 요소를 페이지에 추가](configuring-contexthub.md)해야 합니다.

## 지속성 {#persistence}

ContextHub 저장소는 클라이언트에 컨텍스트 데이터를 유지합니다. ContextHub JavaScript API를 사용하면 저장소에 액세스하여 데이터를 필요에 따라 작성, 업데이트 및 삭제할 수 있습니다. 따라서 ContextHub는 페이지의 데이터 계층을 나타냅니다.

각 ContextHub 저장소는 사전 정의된 저장소 유형의 인스턴스입니다.

* ContextHub는 여러 [샘플 저장소 형식](sample-stores.md)을 제공합니다.
* AEM 콘솔을 사용하여 [스토어를 만듭니다](configuring-contexthub.md#creating-a-contexthub-store).
* 개발자는 [사용자 지정 저장소 유형을 만들 수 있습니다](extending-contexthub.md#creating-custom-store-candidates).
* 개발자는 JavaScript을 통해 [저장소 데이터에 액세스](adding-contexthub.md#interacting-with-contexthub-stores)할 수 있습니다.

## 세분화 {#segmentation}

ContextHub에는 세그먼트를 관리하고 현재 컨텍스트에 대해 해결할 세그먼트를 결정하는 세그먼테이션 엔진이 포함되어 있습니다. 여러 개의 세그먼트가 정의됩니다. JavaScript API를 사용하여 [해결된 세그먼트를 결정](adding-contexthub.md#determining-resolved-contexthub-segments)할 수 있습니다.
