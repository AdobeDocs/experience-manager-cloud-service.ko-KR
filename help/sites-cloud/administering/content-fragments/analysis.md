---
title: 콘텐츠 조각 분석
description: 콘텐츠 전달에 사용되는 콘텐츠 조각의 구조를 이해합니다. Headless 게재 및 페이지 작성과 관련된 정보를 제공합니다.
feature: Content Fragments
role: User, Developer, Architect
exl-id: d9268c1a-bfe6-4df7-bad9-6007dd79e0aa
source-git-commit: 19685cb952a890731bd7d75a2adf3cfd841a465f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 콘텐츠 조각 구조 분석 {#analyzing-content-fragments-structure}

콘텐츠 조각은 [GraphQL을 사용하는 Headless 게재](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md)용으로 디자인되었습니다. 이로써 다층 구조를 가질 수 있습니다.

Experience Manager(AEM)은 조각의 구조를 보고 분석할 수 있는 몇 가지 방법을 제공합니다.

## 참조 {#references}

다중 레이어 구조는 참조를 사용하여 빌드됩니다.

* [참조용 데이터 유형은 콘텐츠 조각 모델에 정의되어 있습니다.](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#using-references-to-form-nested-content)
* 작성 시 다음 작업을 수행할 수 있습니다.
   * [해당 참조 관리](/help/sites-cloud/administering/content-fragments/authoring.md##manage-references)
   * [조각의 상위 참조 찾기](/help/sites-cloud/administering/content-fragments/managing.md#parent-references-fragment)

## 구조 트리 {#structure-tree}

편집기 도구 모음에서 **구조 트리** 탭을 열어 콘텐츠 조각의 계층 구조와 해당 참조를 표시합니다. 링크 아이콘을 사용하여 참조를 엽니다.

예:

![콘텐츠 조각 편집기 - 구조 트리](assets/cf-authoring-structure-tree.png)
