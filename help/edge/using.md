---
title: AEM과 함께 Edge Delivery Services 사용
description: AEM as a Cloud Service를 Edge Delivery Services와 함께 사용할 수 있는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
exl-id: 41999302-b4c9-4f5a-b659-6e7398a3c4f4
role: Admin, Architect, Developer
index: false
hide: true
hidefromtoc: true
source-git-commit: e57610e4c5e498ddfdbaa0ba39c9197ecfb5d177
workflow-type: ht
source-wordcount: '338'
ht-degree: 100%

---


# AEM과 함께 Edge Delivery Services 사용 {#using-edge}

Edge Delivery Services는 콘텐츠 소스에서 분리되며 다양한 콘텐츠 소스의 콘텐츠를 수집할 수 있습니다. 즉, 선택한 소스에 관계없이 간소화된 게시 기능으로 동일한 웹 사이트에서 여러 콘텐츠 소스로 작업할 수 있습니다.

Edge Delivery Services를 사용하면 작성자가 콘텐츠를 빠르게 업데이트 및 게시하고 새 사이트를 신속하게 시작할 수 있는 빠른 개발 환경을 제작할 수 있습니다. 인터넷에서 라이브로 콘텐츠를 편집하고 보는 데까지 단 몇 초밖에 걸리지 않습니다.

![Edge Delivery용 콘텐츠 소스](assets/content-sources.png)

여러 콘텐츠 소스에서 수집하면 사용자에게 최대의 유연성이 제공됩니다. Adobe에서는 프로젝트에 가장 적합한 콘텐츠 소스를 선택하는 데 도움이 되는 지침을 제공합니다.

콘텐츠 소스가 미리 정의되어 있거나 유연하지 않은 경우가 있습니다(예: 프로젝트에서 Sharepoint 또는 Google 드라이브를 사용할 수 없음). 그러나 대부분의 경우 도구는 미리 정의되어 있지 않으며 선택할 수 있는 도구 또한 다양합니다.

Adobe의 안내 원칙은 단순성입니다. 문서 기반 작성으로 시작하고 필요할 때 복잡성을 추가해 보십시오. 도구 변경이 필요한 경우 AEM의 Edge Delivery Services 통합에 콘텐츠 마이그레이션이 포함됩니다.

![콘텐츠 소스 유연성](assets/content-source-flexiblity.png)

## 작성 {#authoring-edge}

Edge Delivery Services를 사용하여 쉽고, 빠르고, 유연하게 콘텐츠를 작성할 수 있습니다. 문서 기반 작성 또는 범용 편집기를 사용하는 WYSIWYG 작성 중 선택할 수 있습니다.

자세한 내용은 [Edge Delivery Services용 콘텐츠 작성](/help/edge/wysiwyg-authoring/authoring.md) 문서를 참조하십시오.

## 게시 {#publishing-edge}

Edge Delivery Services를 사용하여 콘텐츠 소스에 관계없이 원활하게 콘텐츠를 게시합니다.

자세한 내용은 [Edge Delivery Services용 콘텐츠 게시](/help/edge/wysiwyg-authoring/publishing.md) 문서를 참조하십시오.

## 개발 {#developing-edge}

Edge Delivery Services는 블록 개념을 기반으로 합니다. AEM에는 프로젝트 요구 사항을 충족하도록 확장할 수 있는 사전 정의된 블록의 포괄적인 라이브러리가 함께 제공됩니다. Edge Delivery Services 프로젝트의 코드는 GitHub에서 관리됩니다.

자세한 내용은 [Edge Delivery Services를 사용한 WYSIWYG 작성용 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) 문서를 참조하십시오.
