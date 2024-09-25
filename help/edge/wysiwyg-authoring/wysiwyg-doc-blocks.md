---
title: WYSIWYG 및 문서 기반 작성용 블록
description: WYSIWYG 작성과 문서 기반 작성 모두에 사용할 수 있는 블록을 만드는 방법을 알아봅니다.
feature: Edge Delivery Services
role: User
source-git-commit: 3419fa943eb865d87467443527ea97fcd64909c2
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# WYSIWYG 및 문서 기반 작성용 블록 {#wysiwyg-and-doc-blocks}

WYSIWYG 작성과 문서 기반 작성 모두에 사용할 수 있는 블록을 만드는 방법을 알아봅니다.

## 개요 {#overview}

특정 프로젝트에서 [범용 편집기를 사용한 WYSIWYG 작성](/help/edge/wysiwyg-authoring/authoring.md)과 [문서 기반 작성을 모두 지원할 수 있습니다.](/help/edge/docs/authoring.md) 개발 시간을 최소화하고 동일한 사이트 환경을 보장하기 위해 두 사용 사례를 모두 지원하는 블록 집합 하나를 만들 수 있습니다.

이렇게 하려면 WYSIWYG 작성 설정과 문서 기반 작성 설정 모두에 동일한 콘텐츠 모델링 접근 방식을 사용해야 합니다.

## 접근 방식 {#approach}

AEM의 WYSIWYG 작성에서 [모델을 선언](/help/edge/wysiwyg-authoring/content-modeling.md)하고 이름 지정 규칙을 제공합니다. 그런 다음 문서 기반 작성을 사용하여 테이블을 수동으로 만든 것처럼 Edge Delivery을 사용하여 데이터가 테이블과 유사한 블록 구조로 렌더링됩니다.

이를 위해 티저와 같은 간단한 블록에 대해 모든 속성 및 속성 그룹이 1로 렌더링되는 등의 특정 가정을 합니다.각 열이 한 개인 n개 행. 1이 있는 블록의 경우..n개 항목(예: 회전 메뉴 및 카드) 항목은 이러한 행 뒤에 추가되며, 각 등록 정보/등록 정보 그룹에는 하나의 행과 열이 있습니다.

문서 기반 작성에 대해 동일한 접근 방식을 따르는 경우 WYSIWYG 블록을 재사용할 수 있습니다.
