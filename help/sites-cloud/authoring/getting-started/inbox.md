---
title: 받은 편지함
description: 받은 편지함에서 작업 관리
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# 받은 편지함 {#your-inbox}

워크플로우 및 프로젝트를 포함하여 AEM의 다양한 영역에서 알림을 받을 수 있습니다. 예를 들어 다음 항목에 대한 알림을 받을 수 있습니다.

* 작업:
   * These can also be created at various points within the AEM UI, for example, under **Projects**.
   * These can be the product of a workflow **Create Task** or **Create Project Task** step.
* 워크플로우:
   * 페이지 컨텐츠에서 수행해야 하는 작업을 나타내는 작업 항목
      * These are the product of workflow **Participant** steps.
   * 실패 항목, 관리자가 실패한 단계를 다시 시도할 수 있도록 허용

사용자의 받은 편지함에서 이러한 알림을 받고 확인하여 작업을 수행할 수 있습니다.

>[!NOTE]
>
>항목 유형에 대한 자세한 정보는 다음을 참조하십시오.
>
>* [프로젝트](/help/sites-cloud/authoring/projects/overview.md)
>* [프로젝트 - 작업 중](/help/sites-cloud/authoring/projects/tasks.md)
>* [워크플로우](/help/sites-cloud/authoring/workflows/overview.md)


## 헤더의 받은 편지함 {#inbox-in-the-header}

어떤 콘솔에서든 헤더에는 받은 편지함의 현재 알림 수가 표시됩니다. 표시기를 열어서 작업이 필요한 페이지에 빨리 액세스하거나 받은 편지함에 액세스할 수도 있습니다.

![헤더의 받은 편지함 개요](/help/sites-cloud/authoring/assets/inbox-header.png)

>[!NOTE]
>
>특정 작업이 [해당 리소스의 카드 보기에도](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view) 표시됩니다.

## 받은 편지함 열기 {#opening-the-inbox}

AEM 알림 받은 편지함 열기

1. 도구 모음에서 표시기를 클릭/탭합니다.

1. **모두 보기**&#x200B;를 선택합니다. **AEM 받은 편지함**&#x200B;이 열립니다. 받은 편지함은 워크플로우, 프로젝트 및 작업의 항목을 보여줍니다.
1. 기본 보기는 [목록 보기](#inbox-list-view)이지만 [달력 보기](#inbox-calendar-view)로 전환할 수도 있습니다. 이는 [보기 선택기](도구 모음, 오른쪽 상단)로 수행할 수 있습니다.

   For both views you can also define [View Settings](#inbox-view-settings). The options available are dependent on the current view.

   ![받은 편지함 보기 설정](/help/sites-cloud/authoring/assets/inbox-view-settings.png)

>[!NOTE]
>
>The Inbox operates as a console, so use [Global Navigation](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) or [Search](/help/sites-cloud/authoring/getting-started/search.md) to navigate to another location when you are finished.

### 받은 편지함 - 목록 보기 {#inbox-list-view}

이 보기에서는 관련 정보와 함께 모든 항목이 나열됩니다.

![받은 편지함 목록 보기](/help/sites-cloud/authoring/assets/inbox-list-view.png)

### 받은 편지함 - 달력 보기 {#inbox-calendar-view}

이 보기는 달력에서 해당 위치에 따라 항목을 표시합니다.

![받은 편지함 달력 보기](/help/sites-cloud/authoring/assets/inbox-calendar-view.png)

다음을 작업을 수행할 수 있습니다.

* Select a specific view: **Timeline**, **Column**, **List**
* Specify the tasks to display according to **Schedule**: **All**, **Planned**, **In Progress**, **Due Soon**, **Past Due**
* 드릴다운하여 항목에 대한 자세한 정보
* 보기에 초점을 맞출 날짜 범위를 선택합니다.

![받은 편지함 달력 보기 날짜 범위](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### 받은 편지함 - 설정 보기 {#inbox-view-settings}

두 가지 보기(목록 및 달력)에 대해 다음과 같이 설정을 정의할 수 있습니다.

* **달력 보기**

   **달력 보기**&#x200B;의 경우 다음을 구성할 수 있습니다.

   * **그룹화 기준**
   * **예약** 또는 **없음**
   * **카드 크기**
   ![받은 편지함 달력 보기 설정](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **목록 보기**

   **목록 보기**&#x200B;의 경우 정렬 메커니즘을 구성할 수 있습니다.

   * **정렬 기준**
   * **정렬 순서**
   ![받은 편지함 목록 보기 설정](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

   다른 사용자에게 달력을 위임할 수 있을 뿐만 아니라 다른 사용자로부터 위임을 요청하고 위임을 관리할 수도 있습니다.

   ![받은 편지함 목록 보기 위임 설정](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## 항목에 대한 작업 수행 {#taking-action-on-an-item}

1. 항목에 대해 작업을 수행하기 위해서는 해당 항목 옆에 있는 썸네일을 선택합니다. 해당 항목에 적용할 수 있는 작업에 대한 아이콘이 도구 모음에 표시됩니다.

   ![받은 편지함 항목 선택](/help/sites-cloud/authoring/assets/inbox-select-item.png)

   항목에 해당하는 작업은 다음과 같습니다.

   * **전체** 작업
   * **항목 위임**
   * **항목 유형에 따라 다음 작업을 수행할 수 있는 항목을 엽니다** .

      * 항목 속성 표시
      * 추가 작업을 위해 적절한 대시보드 또는 마법사 열기
      * 관련 문서 열기
   * 이전 단계로 **돌아갑니다**
   * 워크플로우에 대한 페이로드를 확인합니다
   * 항목에서 프로젝트를 생성합니다
   >[!NOTE]
   >
   >자세한 내용은 다음을 참조하십시오.
   >
   >* 워크플로우 항목 - ](/help/sites-cloud/authoring/workflows/participating.md)워크플로우에 참여[


1. 선택한 항목에 따라 작업이 시작됩니다. 예:

   * 작업에 해당하는 대화 상자가 열립니다
   * 동작 마법사가 시작됩니다.
   * 설명서 페이지가 열립니다.
   For example, **Delegate** will open a dialog:

   ![받은 편지함 작업 위임](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   대화 상자, 마법사, 문서 페이지가 열렸는지 여부에 따라 다음을 수행할 수 있습니다.

   * 적절한 작업(예: 재할당)을 확인합니다.
   * 작업을 취소합니다
   * 뒤로 화살표를 선택하여 받은 편지함으로 돌아갑니다. 예를 들어 작업 마법사나 문서 페이지가 열려 있으면 받은 편지함으로 돌아갈 수 있습니다.


## 작업 만들기 {#creating-a-task}

받은 편지함에서 작업을 만들 수 있습니다.

1. **만들기**&#x200B;와 **작업**&#x200B;을 차례대로 선택합니다.
1. Complete the necessary fields in the **Basic** and **Advanced** tabs (only the **Title** is mandatory, all others are optional):

   * **기본**:

      * **제목**
      * **프로젝트**
      * **할당자**
      * **컨텐츠**(페이로드)와 유사하며, 보관소의 위치에 대한 작업의 참조입니다
      * **설명**
      * **작업 우선순위**
      * **시작 날짜**
      * **기한**
   ![받은 편지함 추가 작업](/help/sites-cloud/authoring/assets/inbox-create-task.png)

   * **고급**

      * **이름**: URL을 구성하는 데 사용되며 비어 있는 경우 제목을 기반으로 **합니다**.
   ![받은 편지함 추가 작업 고급 옵션](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png)

1. **제출**&#x200B;을 선택합니다.

## 프로젝트 만들기 {#creating-a-project}

특정 작업의 경우, 다음과 같이 해당 작업에 따라 [프로젝트](/help/sites-cloud/authoring/projects/overview.md)를 만들 수 있습니다.

1. 썸네일에서 적절한 작업을 탭/클릭하여 선택합니다.

   >[!NOTE]
   >
   >Only tasks created using the **Create** option of the **Inbox** can be used to create a project.
   >
   >워크플로우의 작업 항목은 프로젝트를 만드는 데 사용할 수 없습니다.

1. 도구 막대에서 **프로젝트 만들기**&#x200B;를 선택하여 마법사를 엽니다.
1. 해당 템플릿을 선택한 뒤 **다음**&#x200B;을 선택합니다.
1. 필수 속성을 지정합니다.

   * **기본**

      * **제목**
      * **설명**
      * **시작 날짜**
      * **기한**
      * **사용자** 및 역할
   * **고급**

      * **이름**
   >[!NOTE]
   >
   >자세한 내용은 [프로젝트 만들기](/help/sites-cloud/authoring/projects/managing.md#creating-a-project)를 참조하십시오.

1. **만들기**&#x200B;를 선택하여 작업을 확인합니다.

## AEM 받은 편지함에서 항목 필터링 {#filtering-items-in-the-aem-inbox}

나열된 항목을 필터링할 수 있습니다.

1. **AEM 받은 편지함**&#x200B;을 엽니다.

1. [필터 선택기]를 엽니다.

   ![받은 편지함 검색](/help/sites-cloud/authoring/assets/inbox-search.png)

1. 기준 범위에 따라 나열된 항목을 필터링할 수 있으며 이러한 항목 중 일부를 수정할 수 있습니다.예:

   ![받은 편지함 검색 필터](/help/sites-cloud/authoring/assets/inbox-search-filter.png)

   >[!NOTE]
   >
   >또한 [보기 설정](#inbox-view-settings)에서 [목록 보기](#inbox-list-view)를 사용할 때 정렬 순서를 구성할 수 있습니다.
