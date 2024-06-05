---
title: 작업
description: 작업은 콘텐츠에 대해 수행할 일의 항목들을 나타내며 프로젝트에서 현재 작업의 완료 수준을 판별하는 데 사용됩니다
exl-id: 66f95a1f-34d0-4e2e-aa8c-addc2029a1d9
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 95%

---

# 작업 {#working-with-tasks}

작업은 콘텐츠에 수행할 작업 항목을 나타냅니다. 작업이 할당되면 할당된 작업은 Workflow 받은 편지함에 나타납니다. 작업 항목의 작업 값은 [유형] 열에 있습니다.

작업은 워크플로 작업을 포함하여 현재 작업의 완료 수준을 판별하는 데에도 사용됩니다.

## 프로젝트 진행 상태 추적 {#tracking-project-progress}

**작업** 타일로 표시되는 프로젝트 내의 활성/완료 작업을 보고 프로젝트 진행 상태를 추적할 수 있습니다. 프로젝트 진행 상태는 다음 항목을 통해 판별할 수 있습니다.

* **작업 타일:** 프로젝트의 전반적인 진행 상황은 프로젝트 세부 정보 페이지에서 사용할 수 있는 작업 타일에 표시됩니다.

* **작업 목록:** 작업 타일을 클릭하면 작업 목록이 표시됩니다. 이 목록에는 프로젝트와 관련된 모든 작업에 대한 상세 정보가 있습니다.

두 목록에는 모두 **작업** 타일에서 직접 생성하는 작업뿐만 아니라 워크플로 작업도 표시합니다.

### 작업 타일 {#task-tile}

프로젝트에 관련 작업이 있다면 작업 타일이 프로젝트 내에 표시됩니다. 작업 타일은 프로젝트의 현재 상태를 보여 줍니다. 이 타일은 워크플로 내의 기존 작업을 기반으로 하며 이후에 워크플로가 진행될 때 생성되는 작업은 포함하지 않습니다. 작업 타일에는 다음 정보가 표시됩니다.

* 완료된 작업의 비율
* 활성 작업의 비율
* 기한이 초과된 작업의 비율

![작업 타일](/help/sites-cloud/authoring/assets/projects-tasks-breakdown.png)

### 프로젝트에서 작업 보기 또는 수정 {#viewing-or-modifying-the-tasks-in-a-project}

진행률 추적 외에 프로젝트에 대한 자세한 정보를 보거나 수정할 수도 있습니다.

#### 작업 목록 {#task-list}

프로젝트와 관련된 작업 목록을 표시하려면 작업 타일에서 줄임표(...)를 클릭하십시오. 작업은 상위 워크플로로 나눠집니다. 기한, 할당자, 우선 순위 및 상태와 같은 메타데이터와 함께 작업 세부 사항이 표시됩니다.

![작업 목록](/help/sites-cloud/authoring/assets/projects-task-list.png)

#### 작업 세부 정보 {#task-details}

특정 작업에 대한 자세한 내용은 작업 목록에서 작업을 선택하고 **열기**.

![작업 세부 정보](/help/sites-cloud/authoring/assets/projects-task-details.png)

### 작업 댓글 보기 및 수정 {#viewing-and-modifying-task-comments}

작업 세부 사항에서는 댓글을 편집하거나 추가할 수 있습니다. 또한 프로젝트의 모든 댓글이 댓글 영역에 표시됩니다.

![작업에 달린 주석](/help/sites-cloud/authoring/assets/projects-tasks-comments.png)

### 작업 추가 {#adding-tasks}

프로젝트에 새 작업을 추가할 수 있습니다. 추가된 작업은 [작업] 타일에 나타나고 [알림] 받은 편지함에서 사용 가능하므로 적절한 작업을 수행할 수 있습니다.

작업을 추가하려면 다음 작업을 수행하십시오.

1. 프로젝트에서 **작업** 타일에서 + 아이콘을 선택합니다. **작업 추가** 창이 열립니다.
1. 작업에 대한 정보를 입력합니다. 작업 제목과 할당 대상 그룹은 필수입니다. 콘텐츠 경로, 설명, 작업 우선 순위 및 기한과 같은 추가 정보는 옵션입니다. 추가로 **고급** 탭을 선택하여 URL의 이름을 지정하는 데 사용되는 작업 이름을 입력할 수 있습니다.

   ![작업 추가](/help/sites-cloud/authoring/assets/projects-add-task.png)

1. **만들기**&#x200B;를 선택합니다.

## 받은 편지함에서 작업 {#working-with-tasks-in-the-inbox}

작업에 액세스하는 다른 방법은 받은 편지함을 사용하는 것입니다. 받은 편지함에서 콘텐츠를 열어 필요한 변경 사항을 구현할 수 있습니다. 작업이 완료되면 작업 상태를 [완료]로 설정합니다. 작업은 사용자가 속한 사용자 그룹에 할당되면 사용자의 받은 편지함에도 나타납니다. 이 경우, 그룹의 아무 구성원이나 작업을 수행하고 작업을 완료할 수 있습니다.

![받은 편지함의 작업](/help/sites-cloud/authoring/assets/projects-task-inbox.png)

작업을 완료하려면 작업을 선택하고 **완료**&#x200B;를 클릭하십시오. 작업에 정보를 추가한 다음 **완료**&#x200B;를 클릭합니다. 자세한 내용은 [받은 편지함](/help/sites-cloud/authoring/inbox.md)을 참조하십시오.

![작업 알림](/help/sites-cloud/authoring/assets/projects-task-notifications.png)
