---
title: 페이지 속성의 벌크 편집 구성
description: 여러 페이지의 속성을 한 번에 편집할 수 있도록 벌크 편집을 구성하는 방법을 알아봅니다.
source-git-commit: 9563c24c2794f8209494891da1a4a5a3360781db
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 1%

---


# 페이지 속성의 벌크 편집 구성 {#configuring-bulk-editing-of-page-properties}

[페이지 속성의 벌크 편집](/help/sites-cloud/authoring/fundamentals/page-properties.md#from-the-sites-console-multiple-pages) 여러 페이지의 속성을 한 번에 편집할 수 있습니다.

## 고려 사항 {#considerations}

페이지 속성은 기본값으로 벌크 편집을 활성화하지 않습니다. 명시적으로 활성화해야 합니다. 벌크 편집에 사용할 수 있는 페이지 속성을 정의할 때는 다음과 같은 특정 의미를 고려해야 합니다.

* 특정 필드는 일반적으로 고유합니다. 하나의 값이 적용될 때 일괄 편집에 이러한 필드를 활성화하는 것이 의미가 있는지 여부를 결정해야 합니다.
   * 예를 들어 페이지 제목은 거의 항상 고유합니다.
* 특정 필드에는 렌더링할 때 의미 있는 표현이 필요한 값이 여러 개 있을 수 있습니다.
   * 예를 들어 상태 드롭다운에 레이블이 지정됨 **게시 준비**. 대량 편집 전에 다음과 같은 몇 가지 값이 있을 수 있습니다. **준비**, **검토 중**, **진행 중**&#x200B;등

값이 여러 개 있을 수 있으므로 벌크 편집에는 다음 필드 유형만 활성화하는 것이 좋습니다.

* `/libs/granite/ui/components/foundation/form/textfield`
* `/libs/granite/ui/components/foundation/form/textarea`
* `/libs/granite/ui/components/foundation/form/tagspicker`
* `/libs/granite/ui/components/foundation/form/datepicker`
* `/libs/granite/ui/components/foundation/form/pathbrowser`
* `/libs/granite/ui/components/foundation/form/checkbox`

## 필드 활성화 {#enabling-a-field}

다음 단계는 `/apps/core/wcm/components/page/v1/page` 다음에서 [WKND 샘플 콘텐츠](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 예를 들어 개발 환경의 필드에서 벌크 편집을 활성화할 수 있습니다.

1. CRXDE를 사용하여 페이지 구성 요소를 엽니다.
1. 내에서 필요한 필드로 이동합니다. `cq:dialog` 정의.
1. 필드 노드에서 다음 속성을 정의합니다.

   * **이름**: `allowBulkEdit`
   * **유형**: `Boolean`
   * **값**: `true`

1. 선택 **모두 저장** 을 클릭하여 업데이트를 유지합니다.

## 제한 사항 {#limitations}

페이지 속성의 벌크 편집:

* 라이브 카피 내의 페이지에는 사용할 수 없습니다.
* 리소스 유형이 동일한 페이지에만 사용할 수 있습니다.
