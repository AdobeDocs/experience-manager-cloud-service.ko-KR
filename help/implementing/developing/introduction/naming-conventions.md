---
title: 이름 지정 규칙
description: 저장소의 노드는 Java Content Repository의 이름 지정 규칙에 따릅니다
exl-id: 3c5c39dd-b209-488b-a93e-e840786fe224
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 1%

---

# 이름 지정 규칙{#naming-conventions}

저장소의 노드는 Java Content Repository의 이름 지정 규칙에 따릅니다. 그러나 AEM은 페이지 노드 이름에 대한 추가 규칙을 지정합니다.

## 페이지 이름 지정 규칙 {#naming-conventions-for-pages}

이러한 이름 지정 규칙은 다양한 수준에서 구현됩니다.

* JcrUtil: 의 AEM 구현 [JCR 유틸리티](#jcr-utilities).
* PageManager: [페이지 관리자](#page-manager) 페이지 수준 작업을 위한 메서드를 제공합니다.
* AEM UI 내 {#ui-behavior}

### JCR 유틸리티 {#jcr-utilities}

[JcrUtil](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/jcr/JcrUtil.html) 는 JCR 유틸리티의 AEM 구현입니다. 이름 확인에 특히 중요한 것은 이 변수가 제어하는 문자 매핑과 다음 유효성 검사입니다.

* `isValidName`
   * 이름이 비어 있지 않고 유효한 문자만 포함되어 있는지 확인합니다.
   * 제안된 이름이 유효한지 여부를 확인하는 데 사용할 수 있습니다.
* `createValidName`
   * 이렇게 하면 임의의 문자열에서 유효한 레이블이 만들어집니다.
   * 제목에서 이름을 만드는 데 사용할 수 있습니다.

### 페이지 관리자 {#page-manager}

[PageManager](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) 은 다음을 기반으로 페이지 수준 작업을 위한 메서드를 제공합니다. [JCRUtil](#jcr-utilities).

### AEM UI 동작 {#ui-behavior}

컨텐츠를 관리할 때 AEM UI는

* 다음 경우 PageManager에서 지정한 제한에 따라 이름의 유효성을 검사합니다.
   * 노드 이름으로 변환하기 위한 페이지 제목이 제공됩니다.
   * 명시적인 노드 이름이 입력되었습니다.
