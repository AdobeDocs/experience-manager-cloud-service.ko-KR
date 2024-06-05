---
title: 페이지 속성의 일괄 편집 구성
description: 한 번에 여러 페이지의 속성을 편집할 수 있도록 일괄 편집을 구성하는 방법에 대해 알아봅니다.
exl-id: 0d10c6b9-8643-479d-adc1-4066d227e83d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 94%

---

# 페이지 속성의 일괄 편집 구성 {#configuring-bulk-editing-of-page-properties}

[페이지 속성의 일괄 편집](/help/sites-cloud/authoring/sites-console/page-properties.md#from-the-sites-console-multiple-pages)을 통해 한 번에 여러 페이지의 속성을 편집할 수 있습니다.

## 고려 사항 {#considerations}

페이지 속성은 기본적으로 일괄 편집에 대해 활성화되어 있지 않습니다. 명시적으로 활성화해야 합니다. 일괄 편집에 사용할 수 있는 페이지 속성을 정의할 때 다음과 같은 특정 영향을 고려해야 합니다.

* 특정 필드는 일반적으로 고유합니다. 하나의 값을 적용할 때 일괄 편집을 위해 이러한 필드를 활성화하는 것이 의미가 있는지 여부를 판단해야 합니다.
   * 예를 들어 페이지 제목은 거의 항상 고유합니다.
* 특정 필드에는 렌더링할 때 의미 있는 표시가 필요한 여러 값이 있을 수 있습니다.
   * **게시 준비됨**&#x200B;이라는 상태 드롭다운을 예로 들 수 있습니다. 대량 편집 전에 다음과 같은 몇 가지 값이 있을 수 있습니다. **준비**, **검토 중**, **진행 중**&#x200B;등.

값이 여러 개 있을 수 있으므로 일괄 편집 시에 다음 필드 유형만 활성화하는 것이 좋습니다.

* `/libs/granite/ui/components/foundation/form/textfield`
* `/libs/granite/ui/components/foundation/form/textarea`
* `/libs/granite/ui/components/foundation/form/tagspicker`
* `/libs/granite/ui/components/foundation/form/datepicker`
* `/libs/granite/ui/components/foundation/form/pathbrowser`
* `/libs/granite/ui/components/foundation/form/checkbox`

## 필드 활성화 {#enabling-a-field}

이 단계에서는 [WKND 샘플 콘텐츠](/help/implementing/developing/introduction/develop-wknd-tutorial.md)의 `/apps/core/wcm/components/page/v1/page`를 예로 사용하여 개발 환경의 필드에서 일괄 편집을 활성화합니다.

1. CRXDE를 사용하여 페이지 구성 요소를 엽니다.
1. `cq:dialog` 정의 내에서 필수 필드로 이동합니다.
1. 필드 노드에서 다음 속성을 정의합니다.

   * **이름**: `allowBulkEdit`
   * **유형**: `Boolean`
   * **값**: `true`

1. **모두 저장**&#x200B;을 선택하여 업데이트 내용을 유지합니다.

## 제한 사항 {#limitations}

페이지 속성의 일괄 편집에는 다음과 같은 특징이 있습니다.

* Live Copy 내의 페이지에는 사용할 수 없습니다.
* 리소스 유형이 동일한 페이지에만 사용할 수 있습니다.
