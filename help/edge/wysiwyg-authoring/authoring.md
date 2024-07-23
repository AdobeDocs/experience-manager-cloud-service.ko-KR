---
title: Edge Delivery Services을 위한 WYSIWYG 컨텐츠 작성
description: Edge Delivery Services를 통한 콘텐츠 작성 방법과 Edge Delivery Services를 사용한 AEM 콘텐츠 작성 방법을 알아보십시오.
feature: Edge Delivery Services
exl-id: 963ff71a-8176-4d9d-8240-dc429405d139
role: User
source-git-commit: f0cb108c620a31c4f8a48f1d2530860ca01b06c3
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 69%

---


# Edge Delivery Services을 위한 WYSIWYG 컨텐츠 작성 {#authoring-edge}

Edge Delivery Services를 사용하여 쉽고, 빠르고, 유연하게 콘텐츠를 작성할 수 있습니다. Edge Delivery Services용 콘텐츠를 작성하기 위한 두 가지 옵션이 있습니다.

* [유니버설 편집기](#universal-editor) - AEM에서 콘텐츠를 작성할 수 있는 최신 WYSIWYG(보이는 그대로) UI
* [문서 기반 작성](#document-based) - Microsoft Word 또는 Google Docs 등

## Universal Editor 작성 {#universal-editor}

AEM as a Cloud Service와 함께 Edge Delivery Services를 사용할 때 이해해야 할 가장 기본적인 사실은 작성한 콘텐츠가 AEM as a Cloud Service로 유지된다는 것입니다.

![Edge Delivery Services에서 WYSIWYG 작성이 작동하는 방식](assets/how-aem-edge-works.png)

1. [AEM Sites 환경](/help/sites-cloud/authoring/quick-start.md)은(는) 새 페이지, 경험 조각, 콘텐츠 조각 등을 만드는 등 콘텐츠 관리에 사용됩니다.
   * 워크플로, MSM, 번역, 실행 등의 모든 AEM 기능을 사용할 수 있습니다.
1. [Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md)는 AEM에서 관리되는 콘텐츠를 작성하는 데 사용됩니다.
   * Universal Editor는 콘텐츠 작성을 위한 새로운 최신 UI를 제공합니다.
   * AEM은 작성을 위해 HTML을 렌더링하지만, Edge Delivery Services의 스크립트, 스타일, 아이콘 및 기타 리소스를 포함합니다.
   * Universal Editor가 사용되지만, 모든 변경 사항은 AEM에 유지됩니다.
   * Universal Editor는 아직 AEM 페이지 편집기가 있는 기능 패리티에 없으며, 일부 AEM 기능은 Universal Editor에서 사용하지 못할 수도 있습니다.
1. Universal Editor로 작성하고 AEM에 유지하는 콘텐츠는 Edge Delivery Services에 게시됩니다.
   * 콘텐츠는 AEM에 계속 저장됩니다.
   * AEM은 수집에 필요한 유의미한 HTML을 렌더링합니다.
   * 콘텐츠는 Edge Delivery Services에 게시됩니다.
1. [Edge Delivery Services](/help/edge/developer/keeping-it-100.md)는 100%의 Lighthouse 점수를 보장합니다.

블록은 Edge Delivery Services에서 제공하는 페이지의 기본 구성 요소입니다. 작성자는 Adobe에서 표준으로 제공하는 기본 블록 또는 개발자가 프로젝트에 맞게 사용자 정의한 블록 중에서 선택할 수 있습니다.

Universal Editor는 블록을 드래그 앤 드롭하여 콘텐츠를 작성할 수 있는 직관적인 최신 GUI를 제공합니다.

![Universal Editor에서 블록 드래그 앤 드롭](assets/blocks.png)

그런 다음 속성 레일에서 블록의 세부 정보를 구성할 수 있습니다.

![블록 속성 구성](assets/block-properties.png)

Universal Editor를 사용하여 작성하는 방법에 대한 자세한 내용은 [Universal Editor를 사용하여 콘텐츠 작성](/help/sites-cloud/authoring/universal-editor/authoring.md)을 참조하십시오.

AEM 및 Edge Delivery Services을 사용하여 프로젝트를 직접 작성하는 방법에 대해 알아보려면 [Edge Delivery Services을 사용하여 WYSIWYG 작성을 위한 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)를 참조하십시오.

## 추가 작성 방법  {#authoring-methods}

WYSIWYG 작성은 콘텐츠 작성자를 위한 강력하고 직관적인 도구입니다. 하지만 작성 사용 사례는 매우 다양하므로 AEM에서 추가 작성 솔루션을 제공합니다.

문서 기반 작성 및 Headless를 포함하여 AEM에서 제공하는 작성 솔루션에 대한 자세한 내용은 [작성 방법 선택](/help/edge/authoring-methods.md) 문서를 참조하십시오.
