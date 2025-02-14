---
title: WYSIWYG 및 문서 기반 작성을 위한 블록
description: WYSIWYG 작성과 문서 기반 작성에 모두 사용할 수 있는 블록을 만드는 방법을 알아봅니다.
feature: Edge Delivery Services
role: User
exl-id: f039c70a-e1a0-4fcc-8f42-dfa0f8bb3764
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '235'
ht-degree: 100%

---

# WYSIWYG 및 문서 기반 작성을 위한 블록 {#wysiwyg-and-doc-blocks}

WYSIWYG 작성과 문서 기반 작성에 모두 사용할 수 있는 블록을 만드는 방법을 알아봅니다.

## 개요 {#overview}

특정 프로젝트에서는 [범용 편집기를 사용한 WYSIWYG 작성](/help/edge/wysiwyg-authoring/authoring.md) 및 [문서 기반 작성](/help/edge/docs/authoring.md)을 모두 지원할 수 있습니다. 개발 시간을 최소화하고 동일한 사이트 경험을 보장하기 위해 두 가지 사용 사례를 모두 지원하는 하나의 블록 세트를 만들 수 있습니다.

이를 위해서는 WYSIWYG 작성 설정과 문서 기반 작성 설정에 모두 동일한 콘텐츠 모델링 접근 방식을 사용해야 합니다.

## 접근법 {#approach}

AEM의 WYSIWYG 작성에서 [모델을 선언](/help/edge/wysiwyg-authoring/content-modeling.md)하고 명명 규칙을 입력합니다. 그런 다음 문서 기반 작성을 사용하여 테이블을 수동으로 생성한 것과 동일한 방식으로 Edge Delivery를 사용하여 테이블과 같은 블록 구조로 데이터를 렌더링합니다.

이를 달성하기 위해 티저와 같은 간단한 블록의 경우 모든 속성과 속성 그룹이 각각 하나의 열로 구성된 1~n개의 행에 렌더링된다고 가정합니다. 1~n개의 항목(예: 슬라이드 및 카드)을 포함하는 블록의 경우, 항목이 이러한 행 뒤에 추가되며 각 항목은 하나의 행과 각각의 속성/속성 그룹에 해당하는 열로 구성됩니다.

문서 기반 작성에 대해 동일한 접근법을 따르는 경우 WYSIWYG 블록을 재사용할 수 있습니다.
