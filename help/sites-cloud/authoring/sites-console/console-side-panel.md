---
title: 사이트 콘솔 사이드 패널
description: AEM 사이트 콘솔에서 사이드 패널을 사용하여 콘텐츠를 더 잘 이해하고 탐색하는 방법을 알아봅니다.
exl-id: 7f2571d6-b847-4cce-8e94-94ba0d2e04a5
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 26%

---

# 사이트 콘솔 사이드 패널 {#side-panel}

AEM에서 사이드 패널을 사용하는 방법 알아보기 **사이트** 콘솔을 통해 콘텐츠를 더 잘 이해하고 탐색할 수 있습니다.

## 방향 {#orientation}

를 입력할 때 기본적으로 사이드 패널이 닫힙니다. **사이트** 콘솔. 이러한 방식으로 화면은 전적으로 콘텐츠 전용이 됩니다.

을(를) 탭하거나 클릭합니다 **사이드 패널** 아이콘 **사이트** 사이드 패널을 활성화하고 콘텐츠 보기를 선택하는 콘솔 도구 모음

* [컨텐츠 전용](#content-only)
* [콘텐츠 트리](#content-tree)
* [타임라인](#timeline)
* [참조](#references)
* [Site](#site)
* [필터](#filter)
* [Analytics 설정](#setup-analytics)

![사이트 콘솔의 사이드 패널 보기](assets/sites-console-side-panel-views.png)

선택한 현재 보기는 드롭다운에서 파란색 확인 표시로 표시되며 도구 모음의 사이드 패널 아이콘은 선택한 보기의 이름으로 업데이트됩니다.

## 컨텐츠 전용 {#content-only}

이 사이드 패널 보기는 효과적으로 꺼집니다. 즉, 사이트의 콘텐츠만 표시됩니다.

>[!TIP]
>
>억음 악센트/억음 악센트 사용 `´` 사이드 패널의 컨텐트 전용 보기로 전환하는 키보드 단축키.

## 콘텐츠 트리 {#content-tree}

이 사이드 패널 보기는 콘텐츠를 트리 계층 구조로 표시합니다. 콘텐츠 트리를 사용하여 사이드 패널에서 사이트 계층 구조를 빠르게 탐색하고, 현재 폴더의 페이지에 대한 다양한 정보를 볼 수 있습니다.

![사이드 패널의 콘텐츠 트리 보기](assets/console-side-panel-content-tree.png)

트리의 항목 옆에 있는 오른쪽 방향 V자형 화살표는 하위 항목을 표시하기 위해 확장할 수 있는 노드를 나타냅니다. V자 버튼을 탭하거나 클릭하여 아이들을 표시합니다.

콘솔에는 콘텐츠 트리에 현재 선택한 항목의 콘텐츠가 표시됩니다.

콘텐츠 트리 사이드 패널과 목록 보기 또는 카드 보기를 함께 사용하면 프로젝트의 계층 구조를 쉽게 확인하고, 콘텐츠 트리 사이드 패널을 사용하여 콘텐츠 구조를 쉽게 탐색하고, 목록 보기에서 자세한 페이지 정보를 볼 수 있습니다.

>[!TIP]
>
>* 사용 `Alt+1` 사이드 패널의 콘텐츠 트리 보기로 전환하는 키보드 단축키.
>* 계층 구조 보기에서 항목을 선택한 후에는 화살표 키를 사용하여 계층 구조를 빠르게 탐색할 수 있습니다.
>* 자세한 내용은 [키보드 단축키](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md)를 참조하십시오.

## 타임라인 {#timeline}

타임라인을 사용하여 선택한 리소스에 영향을 준 이벤트를 볼 수 있습니다. 워크플로우 또는 버전과 같은 특정 이벤트를 시작하는 데도 사용할 수 있습니다.

![타임라인 세부 사항](/help/sites-cloud/authoring/assets/timeline-detail.png)

다음 **타임라인** 사이드 패널을 통해 드롭다운 목록에서 유형으로 선택할 수 있는 선택한 항목과 관련된 다양한 이벤트를 볼 수 있습니다.

* 댓글
* [주석](/help/sites-cloud/authoring/page-editor/annotations.md)
* [활동](/help/sites-cloud/authoring/personalization/activities.md)
* [론치](/help/sites-cloud/authoring/launches/overview.md)
* [버전](/help/sites-cloud/authoring/sites-console/page-versions.md)
* [워크플로](/help/sites-cloud/authoring/workflows/overview.md)
   * 내역 정보가 저장되지 않으므로 임시 워크플로우에 대한 정보는 표시되지 않습니다.<!--With the exception of [transient workflows](/help/sites-developing/workflows.md#transient-workflows) as no history information is saved for these-->
* 모두 표시

또한 를 사용하여 선택한 항목에 대한 설명을 추가/볼 수 있습니다. **댓글** 이벤트 목록 맨 아래에 표시되는 상자입니다. 다음에 이어지는 주석 입력 `Return` 이(가) 주석을 등록합니다. It is shown when **Comments** or **Show All** is selected.

다음에서 **사이트** 콘솔 옆에 있는 줄임표 버튼을 통해 추가 기능에 액세스할 수도 있습니다. **댓글** 필드.

* [버전 저장](/help/sites-cloud/authoring/sites-console/page-versions.md)
* [워크플로 시작](/help/sites-cloud/authoring/workflows/applying.md)

![사이트 콘솔 댓글 필드](assets/sites-console-comment-ellipsis.png)

>[!TIP]
>
>* 사용 `Alt+2` 사이드 패널의 타임라인 보기로 전환하는 키보드 단축키.
>* 자세한 내용은 [키보드 단축키](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md)를 참조하십시오.

## 참조 {#references}

다음 **참조** 보기는 콘솔에서 선택한 리소스에 대한 참조 유형 또는 리소스에 대한 참조 유형 목록을 보여 줍니다.

![참조 세부 사항](assets/console-side-panel-references-detail.png)

자세한 내용을 보려면 적절한 참조 유형을 선택합니다. 특정 상황에서 다음을 비롯한 특정 참조를 선택하면 추가 작업을 사용할 수 있습니다.

* **수신 링크**: 페이지를 참조하는 페이지 목록과 함께, 특정 링크를 선택할 때 그러한 페이지 중 하나를 **편집**&#x200B;하기 위해 직접 액세스할 수 있는 권한 제공.
   * 이렇게 하면 목록 구성 요소에서 동적으로 생성된 링크가 아닌 정적 링크만 표시할 수 있습니다.
* [론치](/help/sites-cloud/authoring/launches/overview.md): 관련 론치에 대한 액세스 권한 제공
* [Live Copy](/help/sites-cloud/administering/msm/overview.md): 선택한 리소스를 기반으로 하는 모든 Live Copy의 경로 표시
* [블루프린트](/help/sites-cloud/administering/msm/best-practices.md): 세부 정보 및 여러 작업 제공
* [언어 사본](/help/sites-cloud/administering/translation/managing-projects.md#creating-translation-projects-using-the-references-panel): 세부 정보 및 여러 작업 제공

## Site {#site}

다음 **Site** 사이드 패널 보기에는 사이트의 세부 정보가 표시됩니다. [사이트 템플릿을 사용하여 만듭니다.](/help/sites-cloud/administering/site-creation/create-site.md)

![사이트 패널](assets/console-side-panel-site-paenl.png)

문서 보기 [사이트 패널을 사용하여 사이트 테마 관리](/help/sites-cloud/administering/site-creation/site-rail.md) 패널을 사용하여 를 관리하는 방법에 대한 자세한 내용은 [사이트의 테마.](/help/sites-cloud/administering/site-creation/site-themes.md).

테마 기반 사이트 생성을 활성화하도록 프론트엔드 파이프라인을 아직 설정하지 않은 경우 사이드 패널에서 해당 옵션을 제공합니다.

![사이드 패널에서 프론트엔드 파이프라인 활성화 옵션](assets/sites-console-side-panel-site.png)

>[!TIP]
>
>템플릿으로 사이트를 만들고 테마를 맞춤화하는 프로세스에 대한 전체적인 설명은 [빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md)에서 확인할 수 있습니다.

## 필터 {#filter}

다음 **필터** 패널은 다음과 유사합니다 [검색 기능](/help/sites-cloud/authoring/search.md) 적절한 위치 필터가 이미 설정되어 있는 상태에서 보려는 콘텐츠를 추가로 필터링할 수 있습니다.

![필터 예](assets/console-side-panel-filter.png)

사이드 패널의 다른 보기와 달리 다른 보기로 전환하려면 `X` 을 클릭합니다.

## Analytics 설정 {#setup-analytics}

이 보기를 사용하면 선택한 사이트에 대해 Adobe Analytics을 빠르게 설정할 수 있습니다.

![Analytics 설정](assets/sites-console-side-panel-setup-analytics.png)
