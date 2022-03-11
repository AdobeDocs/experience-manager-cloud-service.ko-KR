---
title: 개발자 모드
seo-title: Developer Mode
description: 개발자 모드에서는 개발자에게 현재 페이지에 대한 정보를 제공하는 여러 탭이 있는 사이드 패널을 엽니다
seo-description: Developer mode opens a side panel with several tabs that provide a developer with information about the current page
exl-id: fbf11c0f-dc6e-43f3-bcf2-080eacc6ba99
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 1%

---

# 개발자 모드 {#developer-mode}

AEM에서 페이지를 편집할 때 [모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) 개발자 모드를 포함하여 을 사용할 수 있습니다. 개발자 모드에서는 개발자에게 현재 페이지에 대한 기술 정보를 제공하는 몇 개의 탭이 있는 사이드 패널이 열립니다.

두 개의 탭이 있습니다.

* **[구성 요소](#components)** 구조 및 성능 정보를 볼 수 있습니다.
* **[오류](#errors)** 문제가 발생하는 것을 확인합니다.

개발자는 다음 작업을 수행할 수 있습니다.

* **검색** 페이지를 구성하는 방법
* **디버그:** 어디에서 언제 그리고 언제 무슨 일이 일어나는가 하는 것은 문제를 해결하는 데 도움이 됩니다.

>[!NOTE]
>
>개발자 모드:
>
>* 모바일 장치나 데스크탑의 작은 창에서 사용할 수 없습니다(공간 제한 때문에).
>  * 너비가 1024px 미만인 경우 발생합니다.
>* 의 구성원인 사용자만 사용할 수 있습니다 `administrators` 그룹에 속해 있어야 합니다.


## 개발자 모드 열기 {#opening-developer-mode}

개발자 모드가 페이지 편집기에 사이드 패널로 구현됩니다. 패널을 열려면 **개발자** 페이지 편집기의 도구 모음에 있는 모드 선택기에서 다음을 수행합니다.

![개발자 모드 열기](assets/developer-mode.png)

패널은 다음 두 개의 탭으로 나뉘어 있습니다.

* **[구성 요소](#components)** - 다음과 유사한 구성 요소 트리가 표시됩니다 [컨텐츠 트리](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree) 작성자
* **[오류](#errors)** - 문제가 발생하면 각 구성 요소에 대해 세부 사항이 표시됩니다.

### 구성 요소 탭 {#components}

![구성 요소 탭](assets/developer-mode-components-tab.png)

다음과 같은 구성 요소 트리가 표시됩니다.

* 페이지에서 렌더링되는 구성 요소 및 템플릿의 체인에 대해 설명합니다. 트리를 확장하여 계층 내에 컨텍스트를 표시할 수 있습니다.
* 구성 요소를 렌더링하는 데 필요한 서버측 계산 시간을 표시합니다.
* 트리를 확장하고 트리 내에서 특정 구성 요소를 선택할 수 있습니다. 선택 사항에서는 구성 요소 세부 사항에 액세스할 수 있습니다. 예:
   * 저장소 경로
   * 스크립트에 대한 링크(CRXDE Lite에서 액세스)
   * 에 표시된 구성 요소 세부 사항 [구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md)
* 트리에서 선택한 구성 요소는 편집기에서 파란색 테두리로 표시됩니다.

이 구성 요소 탭은 다음 작업을 수행하는 데 도움이 됩니다.

* 구성 요소당 렌더링 시간을 결정하고 비교합니다.
* 계층 구조를 보고 이해합니다.
* 느린 구성 요소를 찾아 페이지 로드 시간을 파악하고 개선합니다.

각 구성 요소 항목에는 다음 옵션이 있을 수 있습니다.

![개발자 모드 구성 요소 예](assets/developer-mode-component-example.png)

* **세부 사항 보기:** 다음을 보여주는 목록에 대한 링크:
   * 구성 요소를 렌더링하는 데 사용되는 모든 구성 요소 스크립트.
   * 이 특정 구성 요소의 저장소 컨텐츠 경로입니다.

      ![세부 사항 보기](assets/developer-mode-view-details.png)

* **스크립트 편집:** CRXDE Lite에서 구성 요소 스크립트를 여는 링크입니다.

* **구성 요소 세부 사항 보기:** 내에서 구성 요소의 세부 사항을 엽니다 [구성 요소 콘솔.](/help/sites-cloud/authoring/features/components-console.md)

V자형 화살표를 탭하거나 클릭하여 구성 요소 항목을 확장하는 경우에도 다음 내용이 표시될 수 있습니다.

    * 선택한 구성 요소 내의 계층 구조입니다.
    * 격리된 선택한 구성 요소, 해당 구성 요소 내에 중첩된 개별 구성 요소 및 결합된 합계의 렌더링 시간입니다.

### 오류 탭 {#errors}

![오류 탭](assets/developer-mode-errors-tab.png)

바라건대 **오류** 탭은 항상 비어 있지만(위와 같이) 문제가 발생하면 각 구성 요소에 대해 다음 세부 정보가 표시될 수 있습니다.

* 구성 요소가 오류 로그에 항목을 기록하고 오류 세부 정보와 CRXDE Lite 내의 해당 코드에 대한 직접 링크가 있는 경우 경고.
* 구성 요소에서 관리 세션을 여는 경우 경고.

예를 들어 정의되지 않은 메서드가 호출되면 결과 오류가 **오류** 탭의 트리에서 구성 요소 항목 **구성 요소** 오류가 발생하면 탭이 표시기로 표시됩니다.
