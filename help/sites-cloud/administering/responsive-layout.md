---
title: 레이아웃 컨테이너 및 레이아웃 모드 구성
description: 콘텐츠 작성자가 반응형 레이아웃을 사용할 수 있도록 레이아웃 컨테이너 및 레이아웃 모드를 구성하는 방법을 알아봅니다.
exl-id: 469e8151-8231-4ccc-b7f6-855545f87440
solution: Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 3%

---

# 레이아웃 컨테이너 및 레이아웃 모드 구성 {#configuring-layout-container-and-layout-mode}

[응답형 레이아웃](/help/sites-cloud/authoring/page-editor/responsive-layout.md)은(는) [응답형 웹 디자인을 구현하기 위한 메커니즘입니다.](https://en.wikipedia.org/wiki/Responsive_web_design) 이를 통해 콘텐츠 작성자는 사용자가 사용하는 장치에 따라 레이아웃과 차원이 다른 웹 페이지를 만들 수 있습니다.

AEM에서는 메커니즘을 조합하여 페이지에 대한 반응형 레이아웃을 실현합니다.

* **[레이아웃 컨테이너](/help/sites-cloud/authoring/page-editor/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)** - 이 구성 요소는 응답형 그리드 내에 구성 요소를 추가 및 배치할 수 있도록 해주는 그리드 단락 시스템을 제공합니다.
   * 페이지의 기본 parsys로 사용하거나 구성 요소 브라우저에서 작성자가 사용할 수 있습니다.
   * 기본 **레이아웃 컨테이너** 구성 요소는 `/libs/wcm/foundation/components/responsivegrid`에 정의되어 있습니다.
   * 레이아웃 컨테이너를 정의할 수 있습니다.
      * 사용자가 페이지에 추가할 수 있는 구성 요소입니다.
      * 를 페이지의 기본 parsys로 사용합니다.
      * 구성 요소와 기본 parsys 모두로.
         * 레이아웃 컨테이너를 페이지의 표준으로 사용할 수 있으며, 사용자가 이 내에 레이아웃 컨테이너를 더 추가할 수 있습니다(예: 열 제어 달성).
* **[레이아웃 모드](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)** - 레이아웃 컨테이너를 페이지에 배치하면 **레이아웃** 모드를 사용하여 콘텐츠를 응답형 그리드 내에 배치할 수 있습니다.
* **[에뮬레이터](/help/sites-cloud/authoring/page-editor/responsive-layout.md#selecting-a-device-to-emulate)** - 구성 요소의 크기를 대화 방식으로 변경하여 장치/창 크기에 따라 레이아웃을 다시 정렬하는 응답형 웹 사이트를 만들고 편집할 수 있습니다. 그러면 사용자는 콘텐츠가 에뮬레이터를 사용하여 어떻게 렌더링될지 알 수 있습니다.

이러한 응답형 격자 메커니즘을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 장치 레이아웃을 기반으로 달라지는 콘텐츠 동작을 정의하려면 중단점 (장치 그룹화를 나타냄)을 사용하십시오.
* 장치 그룹에 따라 구성 요소를 숨깁니다(구성 요소를 숨길 중단점을 정의하십시오).
* 수평 격자에 맞춤(구성 요소를 격자에 배치하고, 필요에 따라 크기를 변경하고, 언제 구성 요소가 나란히 또는 위/아래에 있도록 축소되거나 리플로우되어야 하는지 정의합니다.)
* 열 컨트롤을 구현할 수 있습니다.

>[!NOTE]
>
>[Project Archetype](#addlink) 또는 [표준 사이트 템플릿](#addlink)에서 사이트를 만드는 경우 일반적으로 응답형 레이아웃이 구성됩니다. 그렇지 않으면 페이지에 대해 [레이아웃 컨테이너 구성 요소를 활성화](#enable-the-layout-container-component-for-page)해야 합니다.

## 에뮬레이터 활성화 {#enabling-emulator}

[Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 및 [표준 사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md#standard-site-template)이(가) 이미 에뮬레이터를 사용할 수 있도록 설정되었습니다. 핵심 구성 요소 또는 Archetype을 기반으로 하지 않는 자체 콘텐츠를 개발한 경우, 이러한 기능을 활용하면서 구성 요소를 개발하는 방법에 대한 자세한 내용은 [반응형 디자인](/help/implementing/developing/introduction/responsive-design.md) 문서를 참조하십시오.

## 사이트에 대한 레이아웃 모드 활성화 {#activate-layout-mode-for-your-site}

**레이아웃** 모드를 사용하면 에뮬레이터를 사용하여 여러 장치의 콘텐츠 레이아웃을 조정할 수 있습니다. WKND 샘플 사이트가 이미 **레이아웃** 모드에 대해 활성화되어 있습니다. 다음 단계에 따라 사이트를 활성화하십시오.

### 중단점 구성 {#configure-breakpoints}

중단점은 반응형 디자인에 중요하며 콘텐츠를 타겟 디바이스에 조정하는 방법 및 시기를 정의합니다. 하지만 소개하는 각 중단점은 콘텐츠를 수용할 수 있도록 작성자에게 추가 작업을 생성하므로 주의하십시오. 기본 중단점이 항상 있는 경우를 포함하여 두 개의 중단점으로 충분할 수 있습니다. Adobe은 기본값을 포함하여 세 개 이상의 중단점을 만들지 말 것을 권장합니다(예: `cq:responsive/breakpoint` 아래의 두 개 이하의 노드).

* 중단점에는 제목과 너비가 있습니다.
   * 제목은 필요한 경우 방향을 사용하여 일반 장치 그룹화를 설명합니다.
      * 예: `phone`, `tablet`
   * 너비는 일반 장치 그룹화에 대한 최대 너비(픽셀 단위)를 정의합니다.
      * 예를 들어, 중단점 전화기의 너비가 768이라면 전화 디바이스에 사용되는 레이아웃의 최대 너비입니다.
* 중단점을 정의할 수 있습니다.
   * 페이지 템플릿에서 해당 템플릿으로 만든 페이지에 설정이 복사됩니다.
   * 페이지 노드에서 설정이 하위 페이지에 상속됩니다.
* 중단점은 에뮬레이터를 사용할 때 페이지 편집기 맨 위에 마커로 표시됩니다.
* 중단점은 상위 노드 계층에서 상속되며 언제든지 재정의할 수 있습니다.
* 마지막으로 구성된 중단점 위의 모든 항목을 포함하는 기본(기본) 중단점이 있습니다.
* 중단점은 CRXDE Lite 또는 XML을 사용하여 정의할 수 있습니다.

중단점은 새 프로젝트와 기존 프로젝트 모두에 대해 고려되어야 합니다.

* 새 프로젝트를 설정하는 경우 템플릿에 중단점을 추가해야 합니다.
* 기존 콘텐츠를 사용하여 기존 프로젝트를 마이그레이션하는 경우 다음을 수행해야 합니다.
   * 템플릿에 중단점을 추가합니다.
   * 기존 페이지에 동일한 중단점을 추가합니다.

상속으로 인해 콘텐츠의 루트 페이지에 대해서만 이 작업을 수행하면 됩니다.

#### CRXDE Lite을 사용하여 중단점 구성 {#configuring-breakpoints-using-crxde-lite}

1. CRXDE Lite을 사용하여 다음 중 하나로 이동합니다.

   * 템플릿 정의.
   * 페이지의 `jcr:content` 노드입니다.

1. `jcr:content`에서 노드를 만듭니다.

   * 이름: `cq:responsive`
   * 유형: `nt:unstructured`

1. 이 아래에서 노드를 만듭니다.

   * 이름: `breakpoints`
   * 유형: `nt:unstructured`

1. 중단점 노드 아래에서 중단점을 원하는 수만큼 만들 수 있습니다. 각 정의는 다음 속성을 갖는 단일 노드입니다.

   * 이름: `<descriptive name>`
   * 유형: `nt:unstructured`
   * 제목: `String <descriptive title seen in Emulator>`
   * 너비: `Decimal <value of breakpoint>`

#### XML을 사용하여 중단점 구성 {#configuring-breakpoints-using-xml}

중단점은 적절한 템플릿(또는 콘텐츠) 폴더 아래의 `.context.html`의 `<jcr:content>` 섹션 내에 있습니다.

예제 정의:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

## 페이지에 대한 구성 요소 크기 조정 활성화 {#enable-component-resizing-for-the-page}

**레이아웃** 모드에서 구성 요소의 크기를 조정하는 것은 WKND 샘플 사이트에서 사용할 수 있는 응답형 디자인의 중요한 부분입니다. 다음 단계에 따라 사이트를 활성화하십시오.

### 레이아웃 컨테이너를 기본 Parsys로 설정 {#set-layout-container-as-main-parsys}

페이지의 기본 parsys를 레이아웃 컨테이너로 설정하려면 parsys를 다음과 같이 정의합니다.

`wcm/foundation/components/responsivegrid`

다음 중 하나에서:

* 페이지 구성 요소
* 페이지 템플릿(나중에 사용)

다음 두 예는 정의를 보여 줍니다.

* **HTL:**

  ```xml
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP:**

  ```xml
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### 반응형 CSS 포함 {#include-the-responsive-css}

#### LESS를 사용하는 중단점용 CSS {#css-for-breakpoints-using-less}

AEM에서는 LESS를 사용하여 필요한 CSS의 일부를 생성하지만 이를 프로젝트에 포함해야 합니다.

추가 구성 및 함수 호출을 제공하려면 [클라이언트 라이브러리](/help/implementing/developing/introduction/clientlibs.md)를 만들어야 합니다. 다음 LESS 추출은 프로젝트에 추가해야 하는 최소값의 예입니다.

```java
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

기본 격자선 정의는 다음 위치에 있습니다.

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### 스타일 고려 사항 {#styling-considerations}

응답형 컨테이너 내에 있는 구성 요소의 크기는 응답형 격자 크기에 따라 해당 HTML DOM 요소와 함께 조정됩니다. 따라서 이러한 상황에서는 고정 너비(포함된) DOM 요소의 정의를 피하거나 업데이트하는 것이 좋습니다.

예:

* 전:

   * `width=100px`

* 이후:

   * `max-width=100px`

#### 크기 조정 및 적응형 이미지 규정 준수 {#resizing-and-adaptive-image-compliance}

그리드 내의 구성 요소 크기를 조정하면 다음 리스너가 적절하게 트리거됩니다.

* `beforeedit`
* `beforechildedit`
* `afteredit`
* `afterchildedit`

응답형 격자에 포함된 응용 이미지의 내용을 올바르게 크기 조정하고 업데이트하려면 `REFRESH_PAGE` 수신자로 설정된 `afterEdit`을(를) 포함된 모든 구성 요소의 `EditConfig` 파일에 추가해야 합니다.

예:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

적응형 이미지 메커니즘은 윈도우의 현재 크기에 대한 정확한 이미지의 선택을 제어하는 스크립트를 통해 이용 가능하게 된다. DOM이 준비된 후 또는 전용 이벤트를 수신할 때 활성화됩니다. 현재 사용자의 작업 결과를 제대로 반영하려면 페이지를 새로 고쳐야 합니다.

>[!CAUTION]
>
>사용자 지정 스타일시트 clientlib을 머리말의 일부로 로드해야 작성자와 게시에서 제대로 작동할 수 있습니다.

## 페이지에 대한 레이아웃 컨테이너 구성 요소 활성화 {#enable-the-layout-container-component-for-page}

효과적인 반응형 레이아웃을 위해 콘텐츠 작성자는 레이아웃 컨테이너 구성 요소의 인스턴스를 페이지로 드래그할 수 있어야 합니다. WKND 샘플 사이트에 대해 이미 활성화되어 있습니다. 다음 단계에 따라 사이트를 활성화하십시오.

### 페이지 편집을 위해 레이아웃 컨테이너 구성 요소 활성화 {#enable-the-layout-container-component-for-page-editing}

작성자가 컨텐츠 페이지에 응답형 그리드를 더 추가할 수 있도록 하려면 페이지에 대해 레이아웃 컨테이너 구성 요소를 활성화해야 합니다. 다음 중 하나를 사용하여 이 작업을 수행할 수 있습니다.

* **작성자 환경을 통해** - [페이지 템플릿을 편집](/help/sites-cloud/authoring/sites-console/templates.md)하여 페이지에 대한 레이아웃 컨테이너를 사용하도록 설정합니다.
* **구성 요소 정의** - 구성 요소를 정의할 때 `allowedComponent` 또는 정적 포함을 사용합니다.

### 레이아웃 컨테이너의 그리드 구성 {#configure-the-grid-of-the-layout-container}

페이지 템플릿을 편집하여 레이아웃 컨테이너 [의 각 특정 인스턴스에 사용할 수 있는 열 수를 구성할 수 있습니다.](/help/sites-cloud/authoring/sites-console/templates.md)
