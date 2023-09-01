---
title: 콘텐츠 조각 분석
description: 콘텐츠 조각의 구조 및 콘텐츠 전달을 이해합니다. 이렇게 하면 Headless 게재 및 페이지 작성에 대해 모두 알 수 있습니다.
feature: Content Fragments
role: User, Developer, Architect
source-git-commit: 3d20f4bca566edcdb5f13eab581c33b7f3cf286d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 2%

---


# 콘텐츠 조각 구조 분석 {#analyzing-content-fragments-structure}

콘텐츠 조각은 다음 용도로 디자인되었습니다. [GraphQL을 사용한 헤드리스 게재](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md). 이는 이들이 다층 구조를 가질 수 있음을 의미한다.

Experience Manager(AEM)에서는 조각 구조를 보고 분석하는 몇 가지 방법을 제공합니다.

## 참조 {#references}

구조는 참조를 사용하여 빌드됩니다.

* [참조에 대한 데이터 유형은 콘텐츠 조각 모델에서 정의됩니다](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#using-references-to-form-nested-content)
* 작성 시 다음과 같은 작업을 수행할 수 있습니다.
   * [이러한 참조 관리](/help/sites-cloud/administering/content-fragments/authoring.md##manage-references)
   * [조각의 상위 참조 찾기](/help/sites-cloud/administering/content-fragments/managing.md#parent-references-fragment)

## 구조 트리 {#structure-tree}

를 엽니다. **구조 트리** 탭으로 이동하여 콘텐츠 조각의 계층 구조 및 참조를 표시합니다. 링크 아이콘을 사용하여 참조를 엽니다.

예:

![콘텐츠 조각 편집기 - 구조 트리](assets/cf-authoring-structure-tree.png)