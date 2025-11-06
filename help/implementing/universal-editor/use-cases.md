---
title: 범용 편집기 사용 사례 및 학습 경로
description: 범용 편집기의 주요 사용 사례와 이를 사용하는 가장 좋은 방법을 알아보고, 자신의 프로젝트에 이를 구현하는 방법에 대해 알아봅니다.
exl-id: 398ad0e2-c299-4c49-9784-05c84c67bec2
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 100%

---

# 범용 편집기 사용 사례 및 학습 경로 {#use-cases-learning-paths}

범용 편집기의 주요 사용 사례와 이를 사용하는 가장 좋은 방법을 알아보고, 자신의 프로젝트에 이를 구현하는 방법에 대해 자세히 알아봅니다.

## 개요 {#overview}

범용 편집기는 Adobe Experience Manager Sites의 일부인 다용도 시각적 편집기입니다. 작성자는 모든 헤드리스 또는 헤드풀 경험에 대한 WYSIWYG(what-you-see-is-what-you-get) 편집을 수행할 수 있습니다.

이 문서에서는 두 가지 사용 사례를 자세히 설명하고, 이러한 사례에 대해 알아보는 방법과 자체 프로젝트에서 범용 편집기를 구현하는 방법을 보여 줍니다.

>[!TIP]
>
>아직 검토하지 않았다면 범용 편집기에 대한 전체 개요와 가치에 대한 내용을 담은 [범용 편집기 소개](/help/implementing/universal-editor/introduction.md) 문서를 검토하십시오.

## 사용 사례 {#use-cases}

범용 편집기는 제작하는 콘텐츠 종류에 관계없이 콘텐츠 작성자에게 편리하고 직관적인 시각적 편집기를 제공합니다. 두 가지 주요 사용 사례는 다음과 같습니다.

* [WYSIWYG 작성](#wysiwyg-authoring) - AEM Sites 콘솔을 사용하여 콘텐츠를 관리하고 범용 편집기를 사용하여 AEM 내에서 페이지를 작성합니다.
* [Headless 작성](#headless-authoring) - 범용 편집기를 사용하여 자체 사용자 정의 Headless 앱에서 콘텐츠를 작성합니다.

### WYSIWYG 작성 {#wysiwyg-authoring}

이미 AEM에 익숙하다면 Sites 콘솔을 사용하여 페이지를 만들고 관리한 다음 범용 편집기로 편집할 수 있습니다.

이렇게 하면 페이지 관리(복사, 붙여넣기, 이동) 및 워크플로와 같은 Sites 콘솔에서 사용할 수 있는 도구의 이점을 얻을 수 있을 뿐만 아니라 최신 범용 편집기의 이점도 얻을 수 있습니다.

이를 사용해 본 적이 있다면 바로 다음 단계로 건너뛸 수 있습니다. AEM에서 범용 편집기를 시작하고 실행하는 방법에 대한 전체 개요는 다음 문서를 참조하십시오.

1. [Edge Delivery Services를 사용한 WYSIWYG 작성을 위한 개발자 시작 안내서](https://www.aem.live/developer/ue-tutorial) - AEM에서 첫 번째 범용 편집기 프로젝트를 시작합니다.
1. [범용 편집기와 함께 사용할 수 있도록 계측된 블록 만들기](https://www.aem.live/developer/universal-editor-blocks) - 범용 편집기에서 콘텐츠를 편집 가능하게 만들기 위해 블록을 계측하는 방법에 대해 알아봅니다.
1. [Edge Delivery Services 프로젝트를 사용한 WYSIWYG 작성을 위한 콘텐츠 모델링](https://www.aem.live/developer/component-model-definitions) - 범용 편집기에서 사용할 콘텐츠를 효과적으로 모델링하기 위해 블록이 어떻게 구성되는지 자세히 알아봅니다.

이 문서를 읽은 후 이 페이지로 돌아와서 Headless 작성 사용 사례와 범용 편집기가 일반적으로 작동하는 방식에 대해 알아볼 수 있습니다.

### Headless 작성 {#headless-authoring}

이미 Headless 앱이 있다면 범용 편집기를 사용하여 앱용 콘텐츠를 작성하고 해당 콘텐츠를 AEM의 콘텐츠 조각으로 유지할 수 있습니다. 유일한 요구 사항은 앱이 범용 편집기를 사용할 수 있도록 계측되어야 한다는 것입니다.

이를 사용해 본 적이 있다면 바로 다음 단계로 건너뛸 수 있습니다. 범용 편집기를 사용하도록 계측된 헤드리스 앱의 예는 다음 문서를 참조하십시오.

* [범용 편집기용 SecurBank 샘플 앱](/help/implementing/universal-editor/securbank.md)

이 문서를 읽은 후 이 페이지로 돌아와서 WYSIWYG 작성 사용 사례와 범용 편집기가 일반적으로 작동하는 방식에 대해 알아볼 수 있습니다.

{{ue-headless-auth}}

## 범용 편집기 작동 방식 {#how-ue-works}

범용 편집기의 강점은 모든 콘텐츠를 그 자리에서 작성하여 콘텐츠 작성자에게 콘텐츠에 관계없이 완전히 직관적이고 통합된 UI를 제공하는 기능입니다.

범용 편집기는 다음과 같은 방식으로 작동합니다.

1. 개발자가 범용 편집기를 사용하도록 앱 또는 페이지를 계측합니다. 이 계측은 편집 가능한 콘텐츠와 콘텐츠를 유지하는 방법을 편집자에게 알려줍니다.
   * [Edge Delivery Services를 사용한 WYSIWYG 작성을 위한 개발자 시작 안내서](https://www.aem.live/developer/ue-tutorial) 설명서를 따르면 페이지가 자동으로 계측됩니다.
   * Headless 작성을 위해 앱을 쉽게 계측할 수 있습니다.
1. 콘텐츠 작성자는 범용 편집기를 로드하고, 범용 편집기는 편집을 위해 페이지를 로드합니다. 계측되었기 때문에 편집 가능한 콘텐츠와 이를 표현하고 유지하는 방법에 대해 알고 있습니다.
1. 콘텐츠 작성자는 직관적인 WYSIWYG 인터페이스에서 페이지 콘텐츠를 즉각적으로 편집합니다.
1. 범용 편집기는 변경 사항을 데이터 소스에 자동으로 다시 유지합니다.

범용 편집기 아키텍처에 대해 자세히 알아보려면 [범용 편집기 아키텍처](/help/implementing/universal-editor/architecture.md) 문서를 참조하십시오.

## 범용 편집기 개념 {#concepts}

범용 편집기에서 페이지 또는 앱을 편집 가능하게 하려면 적절하게 계측되어야 합니다.

* [속성 및 유형](/help/implementing/universal-editor/attributes-types.md) - 범용 편집기에서 앱 또는 페이지를 편집할 수 있으려면 적절하게 계측되어야 합니다. 여기에는 편집기가 앱의 콘텐츠를 편집하는 데 필요한 적절한 메타데이터가 포함됩니다.
* [모델 정의, 필드 및 구성 요소 유형](/help/implementing/universal-editor/field-types.md) - 구성 요소를 편집할 수 있는 메타데이터가 있으면 편집기의 속성 패널에서 조작할 수 있는 필드 및 구성 요소 유형을 정의합니다.
* [범용 편집기 이벤트](/help/implementing/universal-editor/events.md) - 범용 편집기가 콘텐츠 또는 UI 상호 작용에서 내보내는 이벤트를 사용하여 앱의 편집 경험을 향상시켜 앱을 추가로 사용자 정의할 수 있습니다.

범용 편집기는 프로젝트 요구에 맞게 조정될 수도 있습니다.

* [범용 편집기 사용자 정의](/help/implementing/universal-editor/customizing.md) - 편집기의 다양한 측면을 필터링하거나 편집기 기능을 확장하여 범용 편집기 경험을 조정할 수 있습니다.
* [범용 편집기 확장](/help/implementing/universal-editor/extending.md) - 범용 편집기의 UI는 프로젝트 요구를 충족하도록 기능을 확장할 수 있습니다.
