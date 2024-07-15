---
title: 유니버설 편집기 사용 사례 및 학습 경로
description: 유니버설 편집기의 주요 사용 사례와 그 사용 방법 및 자체 프로젝트에서 구현하는 방법에 대해 알아봅니다.
exl-id: 398ad0e2-c299-4c49-9784-05c84c67bec2
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 유니버설 편집기 사용 사례 및 학습 경로 {#use-cases-learning-paths}

유니버설 편집기의 주요 사용 사례와 그 사용 및 자체 프로젝트에서 구현하는 방법에 대해 자세히 알아보는 방법에 대해 알아봅니다.

## 개요 {#overview}

범용 편집기는 Adobe Experience Manager Sites의 일부인 다목적 비주얼 편집기입니다. 이를 통해 작성자는 Headless 또는 Headful 경험에 대한 WYSIWYG(보이는 그대로) 편집을 수행할 수 있습니다.

이 문서에서는 이 두 가지 사용 사례에 대해 자세히 설명하고 프로젝트에 유니버설 편집기를 구현할 수 있도록 자세히 알아볼 수 있는 방법을 보여 줍니다.

>[!TIP]
>
>아직 사용하지 않았다면 [유니버설 편집기 소개](/help/implementing/universal-editor/introduction.md) 문서를 검토하여 유니버설 편집기의 전체 개요 및 값을 확인하십시오.

## 사용 사례 {#use-cases}

범용 편집기는 콘텐츠 작성자가 만드는 콘텐츠의 종류에 관계없이 편리하고 직관적인 시각적 편집기를 제공합니다. 두 가지 주요 사용 사례는 다음과 같습니다.

* [WYSIWYG 작성](#wysiwyg-authoring) - AEM Sites 콘솔을 사용하여 범용 편집기를 사용하여 AEM 내에서 콘텐츠 및 작성 페이지를 관리합니다.
* [헤드리스 작성](#headless-authoring) - 유니버설 편집기를 사용하여 사용자 지정 헤드리스 응용 프로그램에서 콘텐츠를 작성합니다.

### WYSIWYG 작성 {#wysiwyg-authoring}

이미 AEM에 익숙하다면 사이트 콘솔을 사용하여 페이지를 만들고 관리한 다음 범용 편집기를 사용하여 편집할 수 있습니다.

이러한 방식으로 페이지 관리(복사, 붙여넣기, 이동) 및 워크플로와 같은 사이트 콘솔에서 사용할 수 있는 도구를 활용할 수 있으며 최신 유니버설 편집기에서도 활용할 수 있습니다.

사용 사례인 경우 바로 다음 단계로, AEM의 범용 편집기를 시작하고 실행하는 방법에 대한 전체 개요는 다음 문서를 참조하십시오.

1. [Edge Delivery Services으로 WYSIWYG 작성을 위한 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) - AEM의 첫 번째 범용 편집기 프로젝트 시작
1. [유니버설 편집기에서 사용하기 위해 계측된 블록 만들기](/help/edge/wysiwyg-authoring/create-block.md) - 유니버설 편집기에서 콘텐츠를 편집할 수 있도록 블록을 계측하는 방법에 대해 알아봅니다.
1. [Edge Delivery Services 프로젝트를 사용하여 WYSIWYG 작성을 위한 콘텐츠 모델링](/help/edge/wysiwyg-authoring/content-modeling.md) - 유니버설 편집기에서 사용할 콘텐츠를 효과적으로 모델링하기 위해 블록을 구성하는 방법에 대한 자세한 내용을 알아봅니다.

이러한 문서를 읽고 나면 이 페이지로 돌아가서 Headless 작성 사용 사례와 범용 편집기가 일반적으로 작동하는 방법에 대해 알아볼 수 있습니다.

### Headless 작성 {#headless-authoring}

이미 Headless 앱이 있는 경우 유니버설 편집기를 사용하여 앱에 대한 콘텐츠를 작성하고 해당 콘텐츠를 AEM의 콘텐츠 조각으로 유지할 수 있습니다. 유일한 요구 사항은 범용 편집기를 사용할 수 있도록 앱이 계측되는 것입니다.

사용 사례인 경우 바로 다음 단계로, 범용 편집기를 사용하도록 계측된 Headless 앱의 예를 보려면 다음 문서를 참조하십시오.

* [범용 편집기용 SecurBank 샘플 앱](/help/implementing/universal-editor/securbank.md)

해당 문서를 읽고 나면 이 페이지로 돌아가서 WYSIWYG 작성 사용 사례와 범용 편집기가 일반적으로 작동하는 방식에 대해 알아볼 수 있습니다.

## 유니버설 편집기 작동 방식 {#how-ue-works}

범용 편집기의 기능은 모든 콘텐츠를 바로 작성할 수 있으므로 콘텐츠가 무엇이든 상관없이 콘텐츠 작성자에게 완전히 직관적이고 통합된 UI를 제공할 수 있습니다.

유니버설 편집기는 다음과 같은 방식으로 작동합니다.

1. 개발자는 범용 편집기를 사용하도록 앱 또는 페이지를 계측합니다. 이 계기는 편집기에 편집 가능한 콘텐츠 및 이를 유지하는 방법을 알려 줍니다.
   * WYSIWYG 작성의 경우, 상용구 템플릿을 사용하여 만든 페이지는 자동으로 계측됩니다.
   * Headless 작성의 경우 앱을 쉽게 계측할 수 있습니다.
1. 콘텐츠 작성자는 범용 편집기를 로드하고, 이 편집용 페이지를 로드합니다. 계측된 콘텐츠이므로 편집할 수 있는 콘텐츠와 표시 및 지속되는 방법에 대해 알 수 있습니다.
1. 콘텐츠 작성자는 직관적인 WYSIWYG 인터페이스에서 페이지 콘텐츠를 편집하고 바로 편집합니다.
1. 범용 편집기는 변경 사항을 AEM에 자동으로 다시 유지합니다.

유니버설 편집기의 아키텍처에 대해 자세히 알아보려면 문서 [유니버설 편집기 아키텍처](/help/implementing/universal-editor/architecture.md)를 참조하십시오.

## 유니버설 편집기 개념 {#concepts}

범용 편집기에서 페이지 또는 앱을 편집할 수 있으려면 적절하게 계측되어야 합니다. 계측된 후에는 프로젝트 요구 사항에 맞게 조정할 수 있습니다.

* [특성 및 형식](/help/implementing/universal-editor/attributes-types.md) - 범용 편집기에서 앱 또는 페이지를 편집할 수 있으려면 적절하게 계측되어야 합니다. 여기에는 편집자가 앱의 콘텐츠를 편집할 수 있도록 적절한 메타데이터가 포함됩니다.
* [모델 정의, 필드 및 구성 요소 유형](/help/implementing/universal-editor/field-types.md) - 구성 요소를 편집할 수 있는 메타데이터가 있으면 편집기의 속성 레일에서 조작할 수 있는 필드 및 구성 요소 유형을 정의합니다. 모델을 만든 다음 구성 요소에서 해당 모델에 연결하면 됩니다.
* [범용 편집기 작성 환경 사용자 지정](/help/implementing/universal-editor/customizing.md) - 앱이나 페이지가 완전히 계측되면 사용 가능한 구성 요소를 필터링하거나 편집기의 기능을 확장하여 범용 편집기 환경을 추가로 조정할 수 있습니다.
* [유니버설 편집기 이벤트](/help/implementing/universal-editor/events.md) - 콘텐츠 및 UI 변경 시 유니버설에서 전송하는 표준 이벤트에 반응하여 앱을 추가로 사용자 지정할 수 있습니다.
