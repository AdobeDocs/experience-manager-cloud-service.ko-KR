---
title: 범용 편집기 2024.12.02 릴리스 정보
description: 다음은 범용 편집기 2024.12.02 릴리스에 대한 릴리스 정보입니다.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 2aae8c63358680758e4f5324f38dea1bc2c47155
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 16%

---


# 범용 편집기 2024.12.02 릴리스 정보 {#release-notes}

다음은 범용 편집기의 2024년 12월 2일 릴리스 정보입니다.

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 새로운 기능 {#what-is-new}

* **콘텐츠 트리의 키보드 탐색**: [측면 패널에서 사용할 수 있는 콘텐츠 트리,](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode)는 이제 키보드를 통해 액세스할 수 있습니다.
   * 작성자는 접근성을 위해 [WCAG 2.1 지침](/help/sites-cloud/authoring/page-editor/accessible-content.md)을 준수하여 표준 키보드 컨트롤을 사용하여 트리 보기 항목을 탐색하고 상호 작용할 수 있습니다.
   * 이러한 향상된 기능은 트리 내의 모든 대화형 요소가 키보드에서 작동 가능하므로 키보드 탐색에 의존하는 사용자의 포괄성이 향상됩니다.
* **편집 가능 요소 선택 해제**: 이제 작성자는 페이지에서 이전에 선택한 편집 가능 요소를 선택 해제할 수 있습니다.
   * 따라서 작성자가 활성 선택 테두리 없이 페이지를 보려고 할 때 주의해야 할 사항이 없습니다.
* **조각 선택기**: AEM as a Cloud Service 인스턴스에서 조각 참조는 이제 조각 선택기를 콘텐츠 선택기로 열어 허용된 콘텐츠 조각 모델 준수, 콘텐츠 조각 검색 및 개선된 전체 경험과 같은 향상된 기능을 제공합니다.
   * 다른 Adobe UI와 일치하고 일관성을 향상시킵니다.
   * [AEM 6.5 환경의 경우](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) 기존 콘텐츠 선택기가 사용 중입니다.
* **컨테이너 설명**: [콘텐츠를 참조하기 위해 [속성 패널](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-panel-properties-rail)에서 사용되는 컨테이너 구성 요소](/help/implementing/universal-editor/field-types.md#container)에서 이제 컨테이너 필드 위에 표시되는 설명 특성을 지원합니다.
   * 이렇게 하면 작성자가 편집하고 있는 그룹화된 필드에 대한 컨텍스트를 제공하여 명확성을 높일 수 있습니다.

## 기타 개선 사항 {#other-improvements}

* **서식 있는 텍스트 필드 동기화**: 속성 패널의 서식 있는 텍스트 필드 내에서 원시 콘텐츠와 렌더링된 콘텐츠의 동기화를 개선하여 서식 있는 텍스트 콘텐츠와 렌더링된 표현이 다를 수 있는 Edge Delivery Services 프로젝트 내의 문제를 해결했습니다.
* **편집 모드 이벤트**: 이제 유니버설 편집기에서 원격 앱을 다시 로드한 후를 포함하여 편집 모드 이벤트를 안정적으로 내보냅니다.
