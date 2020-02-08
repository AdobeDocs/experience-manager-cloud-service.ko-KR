---
title: 구성 요소 콘솔
description: 구성 요소 콘솔을 사용하면 인스턴스에 대해 정의된 모든 구성 요소를 검색할 수 있습니다
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# 구성 요소 콘솔 {#components-console}

구성 요소 콘솔을 사용하면 인스턴스에 대해 정의된 모든 구성 요소를 검색하고 각 구성 요소에 대한 주요 정보를 볼 수 있습니다.

It can be accessed from **Tools ->** **General ->** **Components**. 구성 요소에 대한 트리 구조가 없으므로 목록 보기만 사용할 수 있습니다.

![구성 요소 콘솔](/help/sites-cloud/authoring/assets/components-console.png)

>[!NOTE]
>
>구성 요소 콘솔은 시스템의 모든 구성 요소를 표시합니다. The [Component Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) shows components that are available to authors and hides any component groups that begin with a period ( `.`).

## 검색 {#search-field}

**컨텐츠 전용** 아이콘(왼쪽 상단)을 사용하여 구성 요소를 검색 및/또는 필터링할 **검색** 패널을 열 수 있습니다.

![구성 요소 콘솔에서 검색](/help/sites-cloud/authoring/assets/components-console-search.png)

### 구성 요소 세부 사항 {#component-details}

특정 구성 요소에 대한 세부 사항을 보려면 필수 리소스를 탭하거나 클릭합니다. 세 탭에서 다음 정보를 제공합니다.

* **속성**

   ![구성 요소 콘솔 속성](/help/sites-cloud/authoring/assets/components-console-properties.png)

   [속성] 탭에서 다음 작업을 수행할 수 있습니다.

   * 구성 요소의 일반 속성 확인
      * 구성 요소에 대해 아이콘이나 약어를 정의한 방법을 확인합니다. <!-- View how the [icon or abbreviation has been defined](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) for the component.-->
      * 아이콘의 소스를 클릭하면 해당 구성 요소로 이동합니다.
   * 구성 요소에 대한 **리소스 유형** 및 **리소스 슈퍼 유형**(정의된 경우) 확인
      * [리소스 슈퍼 유형]을 클릭하면 해당 구성 요소로 이동합니다.
   >[!NOTE]
   >
   >Because `/apps` is not editable at runtime, the Components Console is read-only.

* **정책**

   ![구성 요소 콘솔 정책](/help/sites-cloud/authoring/assets/components-console-policies.png)

* **라이브 사용량**

   ![구성 요소의 실시간 사용](/help/sites-cloud/authoring/assets/components-console-live-usage.png)

   >[!CAUTION]
   >
   >이 보기에 대해 수집 중인 정보의 특성으로 인해 순서대로 구성하거나 표시하는 데 시간이 걸릴 수 있습니다.

* **설명서**

   개발자가 구성 요소에 대한 설명서를 제공한 경우 **설명서** 탭에 표시됩니다. 사용 가능한 설명서가 없으면 **설명서** 탭이 표시되지 않습니다. <!-- If the developer has provided [documentation for the component](/help/sites-developing/developing-components.md#documenting-your-component), it will appear on the **Documentation** tab. If there is no documentation available, the **Documentation** tab will not be shown.-->

   ![구성 요소 설명서](/help/sites-cloud/authoring/assets/components-console-documentation.png)
