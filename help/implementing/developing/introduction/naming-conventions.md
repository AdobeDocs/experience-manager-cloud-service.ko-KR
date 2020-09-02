---
title: 이름 지정 규칙
description: 저장소의 노드는 Java 컨텐츠 저장소의 이름 지정 규칙을 따릅니다
translation-type: tm+mt
source-git-commit: fee73b5f5ba69422494efe554ac5aa62c046ad86
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 16%

---


# 이름 지정 규칙{#naming-conventions}

저장소의 노드는 Java 컨텐츠 저장소의 이름 지정 규칙을 따릅니다. 그러나 AEM에서는 페이지 노드의 이름에 대한 추가적인 규칙을 적용합니다.

## 페이지에 대한 이름 지정 규칙 {#naming-conventions-for-pages}

이러한 이름 지정 규칙은 다양한 수준에서 구현됩니다.

* JcrUtil:JCR 유틸리티의 AEM [구현](#jcr-utilities).
* 페이지 관리자:페이지 관리자 [는](#page-manager) 페이지 수준 작업에 대한 메서드를 제공합니다.
* AEM UI 내에서 {#ui-behavior}

### JCR 유틸리티 {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) 은 JCR 유틸리티의 AEM 구현입니다. 이름 유효성 검사에 대한 특정 관심 사항은 이름이 제어하는 문자 매핑과 다음 유효성 검사입니다.

* `isValidName`
   * 이름이 비어 있지 않고 유효한 차만 포함되어 있는지 확인합니다.
   * 제안된 이름이 유효한지 확인하는 데 사용할 수 있습니다.
* `createValidName`
   * 임의의 문자열에서 유효한 레이블을 만듭니다.
   * 제목에서 이름을 만드는 데 사용할 수 있습니다.

### 페이지 관리자 {#page-manager}

[PageManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) 는 JCRUtil을 기반으로 페이지 수준 작업 방식을 [제공합니다](#jcr-utilities).

### AEM UI 동작 {#ui-behavior}

컨텐츠 관리 시 AEM UI:

* 다음 경우 PageManager에서 지정한 제한에 따라 이름을 확인합니다.
   * 노드 이름으로 변환할 페이지 제목이 제공됩니다.
   * 명시적 노드 이름이 제공됩니다.
