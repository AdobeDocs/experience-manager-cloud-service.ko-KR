---
title: 숨기기 조건 사용
description: 숨기기 조건을 사용하여 구성 요소 리소스가 렌더링되었는지 확인할 수 있습니다.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 5%

---


# 숨기기 조건 사용 {#using-hide-conditions}

숨기기 조건을 사용하여 구성 요소 리소스가 렌더링되었는지 확인할 수 있습니다. 템플릿 작성자가 [템플릿 편집기](/help/sites-cloud/authoring/features/templates.md)에 핵심 구성 요소 [목록 구성 요소](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/components/list.html)를 구성하고 하위 페이지를 기준으로 목록을 작성하는 옵션을 비활성화하기로 결정하는 경우가 이에 해당됩니다. 디자인 대화 상자에서 이 옵션을 비활성화하면 목록 구성 요소를 렌더링할 때 숨기기 조건이 평가되고 하위 페이지 표시 옵션이 표시되지 않도록 속성이 설정됩니다.

## 개요 {#overview}

대화 상자는 매우 복잡해질 수 있으며 사용자가 원하는 옵션 중 일부만 사용할 수 있습니다. 이로 인해 사용자에게 사용자 인터페이스 경험이 크게 늘어날 수 있습니다.

숨기기 조건을 사용하면 관리자, 개발자 및 수퍼 사용자는 규칙 세트를 기반으로 리소스를 숨길 수 있습니다. 이 기능을 사용하면 작성자가 컨텐츠를 편집할 때 표시할 리소스를 결정할 수 있습니다.

>[!NOTE]
>
>식을 기반으로 리소스를 숨기면 ACL 권한이 대체되지 않습니다. 컨텐츠는 편집 가능하지만 표시되지는 않습니다.

## 구현 및 사용 세부 정보 {#implementation-and-usage-details}

`com.adobe.granite.ui.components.FilteringResourceWrapper` 는 필터링할 필드에 있는  `granite:hide` 속성의 존재 및 값을 기반으로 리소스를 필터링하는 책임을 집니다. `/libs/cq/gui/components/authoring/dialog/dialog.jsp` 구현에 `FilteringResourceWrapper.` 인스턴스가 포함되어 있습니다.

구현은 Granite [ELResolver API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/docs/server/el.html)를 사용하고 ExpressionCustomizer를 통해 `cqDesign` 사용자 지정 변수를 추가합니다.

다음은 `etc/design` 아래 또는 컨텐트 정책으로 있는 디자인 노드의 숨기기 조건의 몇 가지 예입니다.

```
${cqDesign.myProperty}
${!cqDesign.myProperty}
${cqDesign.myProperty == 'someText'}
${cqDesign.myProperty != 'someText'}
${cqDesign.myProperty == true}
${cqDesign.myProperty == true}
${cqDesign.property1 == 'someText' && cqDesign.property2 || cqDesign.property3 != 1 || header.myHeader}
```

숨기기 표현식을 정의할 때는 다음 사항을 염두에 두십시오.

* 유효하려면 속성이 발견되는 범위(예:`cqDesign.myProperty`).
* 값은 읽기 전용입니다.
* 함수(필요한 경우)는 서비스가 제공하는 특정 세트로 제한되어야 합니다.

## 예 {#example}

숨기기 조건의 예제는 AEM 및 [핵심 구성 요소](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html)에서 찾을 수 있습니다. 예를 들어 [목록 핵심 구성 요소](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/list.html)는 [WKND 자습서에 구현된 것으로 간주합니다.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

[템플릿](/help/sites-cloud/authoring/features/templates.md) 작성자는 템플릿 편집기를 사용하여 페이지 작성자가 사용할 수 있는 목록 구성 요소의 옵션을 디자인 대화 상자에서 정의할 수 있습니다. 목록을 정적 목록으로 허용할지 여부, 하위 페이지 목록, 태그 있는 페이지 목록 등과 같은 옵션. 활성화 또는 비활성화할 수 있습니다.

템플릿 작성자가 하위 페이지 옵션을 비활성화하도록 선택하면 디자인 속성이 설정되고 숨기기 조건이 평가되어 페이지 작성자에 대해 옵션이 렌더링되지 않습니다.

1. 기본적으로 페이지 작성자는 목록 핵심 구성 요소를 사용하여 **하위 페이지** 옵션을 선택하여 하위 페이지를 사용하여 목록을 만들 수 있습니다.

   ![목록 구성 요소 설정](assets/hide-conditions-list-settings.png)

1. 목록 핵심 구성 요소의 디자인 대화 상자에서 템플릿 작성자는 **하위 항목 비활성화** 옵션을 선택하여 하위 페이지를 기준으로 목록을 생성하는 옵션이 페이지 작성자에게 표시되지 않게 할 수 있습니다.

   ![목록 구성 요소 디자인 대화 상자](assets/hide-conditions-list-design.png)

1. 정책 노드는 `/conf/wknd/settings/wcm/policies/wknd/components/list` 아래에 `disableChildren` 속성이 `true`로 설정된 상태로 만들어집니다.

   ![숨기기 조건의 노드 구조](assets/hide-conditions-node-structure.png)

1. 숨기기 조건은 대화 상자 속성 노드 `/libs/core/wcm/components/list/v2/list/cq:dialog/content/items/tabs/items/listSettings/items/columns/items/column/items/listFrom/items/children`에 있는 `granite:hide` 속성의 값으로 정의됩니다.

   ![숨기기 조건 평가](assets/hide-conditions-evaluation.png)

1. `disableChildren`의 값이 디자인 구성에서 가져오며 `${cdDesign.disableChildren}` 식이 `false`로 평가됩니다. 즉, 옵션이 구성 요소의 일부로 렌더링되지 않습니다.

1. 목록 구성 요소를 사용할 때 **하위 페이지** 옵션이 더 이상 페이지 작성자에 대해 렌더링되지 않습니다.

   ![하위 옵션이 비활성화된 목록 구성 요소](assets/hide-conditions-child-disabled.png)
