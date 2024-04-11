---
title: 기존 AEM 프로젝트와 함께 Edge Delivery Services 사용
description: 기존 AEM 프로젝트에서 Edge Delivery Services의 이점을 활용하는 방법 알아보기
feature: Edge Delivery Services
exl-id: f54aac3a-1d0c-4be0-9aa6-616217e0e458
source-git-commit: 11f721b4a617c99e30329d7196f42d7b48067f1b
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 100%

---


# 기존 AEM 프로젝트와 함께 Edge Delivery Services 사용 {#existing-projects}

새로운 AEM 프로젝트가 Edge Delivery Services의 이점을 얻을 수 있을 때까지 기다릴 필요가 없습니다. Edge Delivery Services를 기존 AEM 프로젝트에 통합하여 성능 향상을 즉시 활용할 수 있습니다.

## AEM 페이지 편집기 제한 사항 {#page-editor}

Edge Delivery Services가 등장하기 전에는 AEM 페이지 편집기를 사용하여 AEM에서 관리되는 콘텐츠를 편집했습니다. Edge Delivery Services가 도입되기 전에 프로젝트가 시작된 경우, 페이지 편집기를 사용하고 있었을 것입니다.

AEM 페이지 편집기는 [핵심 구성 요소와 같은 [AEM 구성 요소](/help/implementing/developing/components/overview.md)에서만 작동합니다.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 이러한 구성 요소는 Edge Delivery Services와 호환되지 않습니다. 이로 인해 기존 AEM 프로젝트에 Edge Delivery Services를 도입하려면 두 가지 단계가 필요합니다.

* [1단계 - 프론트엔드 바꾸기](#replace-front-end)
* [2단계 - Universal Editor로 전환](#switch-ue)

## 1단계 - 프론트엔드 바꾸기 {#replace-front-end}

1단계에서는 기존 AEM 사이트 구조, 구성 요소 및 작성 도구를 계속 사용할 수 있습니다. 웹 사이트 렌더링은 JavaScript 및 CSS를 사용하는 블록을 사용하여 재구축되며, Edge Delivery Services를 통해 제공됩니다.

Edge Delivery Services용 블록 및 개발 방법에 대한 자세한 내용은 Edge Delivery Services 설명서의 [빌드 섹션](/help/edge/developer/block-collection.md) 을 참조하십시오.

AEM 렌더링된 HTML 출력을 전환하여 Edge Delivery Services로 보내려면 애플리케이션 빌더의 전환기가 필요합니다.

![게시 흐름의 콘텐츠 전환기](assets/content-converter.png)

2단계에서는 AEM 작성자의 HTL 및 Java가 포함된 AEM 핵심 구성 요소, Edge Delivery의 JS 기반 블록 및 nodeJS 기반 전환기와 같은 기술 중복을 제거하여 프로세스를 완료합니다.

## 2단계 - Universal Editor로 전환 {#switch-ue}

이 단계에서는 AEM 페이지 편집기가 Universal Editor로 대체됩니다. Universal Editor는 블록에서 직접 작업할 수 있으므로, AEM 핵심 구성 요소 및 전환기가 더 이상 필요하지 않습니다.

