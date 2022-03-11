---
title: 이름 지정 규칙
description: 저장소의 노드는 Java 컨텐츠 저장소의 이름 지정 규칙을 따릅니다
exl-id: 3c5c39dd-b209-488b-a93e-e840786fe224
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 17%

---

# 이름 지정 규칙{#naming-conventions}

저장소의 노드는 Java 컨텐츠 저장소의 이름 지정 규칙을 따릅니다. 그러나 AEM에서는 페이지 노드의 이름에 대한 추가적인 규칙을 적용합니다.

## 페이지에 대한 이름 지정 규칙 {#naming-conventions-for-pages}

이러한 이름 지정 규칙은 다음과 같은 다양한 수준에서 구현됩니다.

* JcrUtil: 의 AEM 구현 [JCR 유틸리티](#jcr-utilities).
* 페이지 관리자: a [페이지 관리자](#page-manager) 페이지 수준 작업에 대한 메서드를 제공합니다.
* AEM UI 내에서 {#ui-behavior}

### JCR 유틸리티 {#jcr-utilities}

[JcrUtil](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/jcr/JcrUtil.html) 는 JCR 유틸리티의 AEM 구현입니다. 이름 유효성 검사에 대한 특정 관심 사항은 이 컨트롤이 제어하는 문자 매핑과 다음 유효성 검사입니다.

* `isValidName`
   * 이름이 비어 있지 않고 올바른 문자만 포함되어 있는지 확인합니다.
   * 제안된 이름이 유효한지 확인하는 데 사용할 수 있습니다.
* `createValidName`
   * 이렇게 하면 임의의 문자열로 유효한 레이블이 만들어집니다.
   * 제목에서 이름을 만드는 데 사용할 수 있습니다.

### 페이지 관리자 {#page-manager}

[PageManager](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) 에서는 다음을 기준으로 페이지 수준 작업에 대한 메서드를 제공합니다 [JCRUtil](#jcr-utilities).

### AEM UI 동작 {#ui-behavior}

컨텐츠를 관리할 때 AEM UI는

* 다음 경우 PageManager에서 지정한 제한에 따라 이름을 확인합니다.
   * 노드 이름으로 전환할 페이지 제목이 제공됩니다
   * 명시적 노드 이름이 제공됩니다.
