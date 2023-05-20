---
title: 프로젝트 관리
description: 프로젝트를 사용하면 리소스를 프로젝트 콘솔에서 액세스 및 관리할 수 있는 하나의 엔티티로 그룹화하여 프로젝트를 구성할 수 있습니다.
exl-id: be4616e7-18bc-4b2d-89f6-d04178ac7f3a
source-git-commit: 54a098d8986c8bbd740bed50f8625c1025d2f6f4
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 60%

---

# 프로젝트 관리 {#managing-projects}

프로젝트를 사용하면 리소스를 하나의 엔티티로 그룹화하여 프로젝트를 구성할 수 있습니다.

다음에서 **프로젝트** 콘솔에서 프로젝트에 액세스하고 작업을 수행합니다.

![프로젝트 콘솔](/help/sites-cloud/authoring/assets/projects-console.png)

프로젝트에서 프로젝트를 만들고, 리소스를 프로젝트와 연결하며, 프로젝트나 리소스 링크를 삭제할 수도 있습니다. 타일을 열어 콘텐츠를 보고 타일에 항목을 추가할 수도 있습니다. 이 항목에서는 이러한 절차에 대해 설명합니다.

## 프로젝트 만들기 {#creating-a-project}

AEM에서는 프로젝트를 만들 때 선택할 수 있도록 다음과 같은 템플릿을 기본적으로 제공합니다.

* 간단한 프로젝트
* 미디어 프로젝트
* 번역 프로젝트

<!-- Hiding product photoshoot via cqdoc-18072 as it is not available in Skyline.
* Product Photo Shoot Project 
-->

The procedure of creating a project is the same from project to project. The difference between the types of projects includes available [user roles](/help/sites-cloud/authoring/projects/overview.md) and [workflows](/help/sites-cloud/authoring/projects/workflows.md).  To create a new project:

1. In **Projects**, tap/click **Create** to open the **Create Project** wizard:
1. 템플릿을 선택하고 **다음**&#x200B;을 클릭합니다.

   ![프로젝트 만들기](/help/sites-cloud/authoring/assets/projects-create.png)

1. **제목** 및 **설명**&#x200B;을 정의한 다음 필요한 경우 **썸네일** 이미지를 추가합니다. 사용자와 사용자가 속한 그룹을 추가하거나 삭제할 수도 있습니다. 또한 다음을 클릭합니다. **고급** URL에 사용된 이름을 추가합니다.

   ![프로젝트 세부 정보 추가](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. **만들기**&#x200B;를 탭/클릭합니다. 새 프로젝트를 열지 또는 콘솔로 돌아갈지 묻는 메시지가 표시됩니다.

### 리소스를 프로젝트와 연결 {#associating-resources-with-your-project}

프로젝트를 통해 리소스를 하나의 엔티티로 그룹화할 수 있으므로 리소스를 프로젝트에 연관시킬 수 있습니다. 이러한 리소스를 라고 합니다. **타일**. 추가할 수 있는 리소스 유형이에 설명되어 있습니다 [프로젝트 타일](/help/sites-cloud/authoring/projects/overview.md#project-tiles).

리소스를 프로젝트와 연결하려면 다음 작업을 수행하십시오.

1. 에서 프로젝트를 엽니다. **프로젝트** 콘솔.
1. 탭/클릭 **타일 추가** 프로젝트에 연결할 타일을 선택합니다. 여러 유형의 타일을 선택할 수 있습니다.

   ![프로젝트에 타일 추가](/help/sites-cloud/authoring/assets/projects-add-tile.png)

   >[!NOTE]
   >
   >프로젝트와 연결할 수 있는 프로젝트 타일은 [프로젝트 타일](/help/sites-cloud/authoring/projects/overview.md#project-tiles)에 자세히 설명되어 있습니다.

1. **만들기**&#x200B;를 탭/클릭합니다. 리소스는 프로젝트에 연결되며, 이제부터 프로젝트에서 이 리소스에 액세스할 수 있습니다.

### 프로젝트 또는 리소스 링크 삭제 {#deleting-a-project-or-resource-link}

콘솔에서 프로젝트를 삭제하거나 프로젝트에서 연결된 리소스를 삭제하는 데에는 동일한 방법이 사용됩니다.

1. 적절한 위치로 이동합니다.

   * 프로젝트를 삭제하려면 의 최상위 수준으로 이동합니다. **프로젝트** 콘솔.
   * 프로젝트 내의 리소스 링크를 삭제하려면 **프로젝트** 콘솔에서 프로젝트를 여십시오.

1. **선택**&#x200B;을 클릭하고 프로젝트나 리소스 링크를 선택하여 선택 모드에 들어갑니다.
1. **삭제**&#x200B;를 탭/클릭합니다.

1. 대화 상자에서 삭제를 확인해야 합니다. 확정하면 프로젝트 또는 리소스 링크가 삭제됩니다. 선택 모드를 종료하려면 **선택 취소**&#x200B;를 탭/클릭하십시오.

>[!NOTE]
>
>When you create the project and add users to the various roles, groups associated with the project are automatically created to manage associated permissions. For example, a project called Myproject would have three groups **Myproject Owners**, **Myproject Editors**, **Myproject Observers**. However, if the project is deleted, those groups are not automatically deleted. An administrator needs to manually delete the groups in **Tools** > **Security** > **Groups**.

### 타일에 항목 추가 {#adding-items-to-a-tile}

일부 타일에서는 두 개 이상의 항목을 추가할 수 있습니다. 예를 들어 한 번에 두 개 이상의 워크플로가 실행되거나 두 개 이상의 경험이 있을 수 있습니다.

타일에 항목을 추가하려면 다음 작업을 수행하십시오.

1. **프로젝트**&#x200B;에서 프로젝트로 이동한 다음 항목을 추가하려는 타일에 있는 아래쪽 V자 버튼을 클릭합니다.

   ![타일에 항목 추가](/help/sites-cloud/authoring/assets/project-workflows.png)

1. 새 타일을 만들 때처럼 타일에 항목을 추가합니다. 프로젝트 타일에 대해 설명합니다. [여기](/help/sites-cloud/authoring/projects/overview.md#project-tiles). 이 예제에서는 워크플로가 더 추가되었습니다.

### 타일 열기 {#opening-a-tile}

현재 타일에 포함된 항목을 보거나 타일의 항목을 수정하거나 삭제할 수 있습니다.

항목을 보거나 수정할 수 있도록 타일을 열려면 다음 작업을 수행하십시오.

1. 프로젝트 콘솔에서 카드 하단의 생략 부호(...) 아이콘을 탭/클릭합니다.

   ![타일 열기](/help/sites-cloud/authoring/assets/project-links.png)

1. AEM은 해당 타일의 항목을 나열합니다. 선택 모드에 들어가 항목을 수정하거나 삭제할 수 있습니다.

   ![타일 열림](/help/sites-cloud/authoring/assets/projects-add-link.png)

## 프로젝트 통계 보기 {#viewing-project-statistics}

**프로젝트** 콘솔에서 프로젝트 통계를 볼 수 있습니다.

### 프로젝트 타임라인 보기 {#viewing-a-project-timeline}

프로젝트 타임라인에서는 프로젝트의 에셋이 마지막으로 사용된 시기에 대한 정보를 제공합니다. 프로젝트 타임라인을 보려면 **타임라인**&#x200B;을 클릭/탭한 다음 선택 모드에 들어가 프로젝트를 선택합니다. 에셋은 왼쪽 창에 표시됩니다. **프로젝트** 콘솔로 돌아가려면 **타임라인**&#x200B;을 클릭/탭하십시오.

![프로젝트 타임라인](/help/sites-cloud/authoring/assets/projects-timeline.png)

### 활성/비활성 프로젝트 보기 {#viewing-active-inactive-projects}

활성 및 비활성 프로젝트 간 전환하려면 **프로젝트** 콘솔에서 **활성 프로젝트 전환**&#x200B;을 클릭합니다. 아이콘 옆에 확인 표시가 있으면 활성 프로젝트를 표시 중입니다.

![활성 프로젝트 전환 버튼](/help/sites-cloud/authoring/assets/projects-active.png)

아이콘 옆에 확인 x가 있으면 비활성 프로젝트를 표시 중입니다.

![비활성 프로젝트 전환 버튼](/help/sites-cloud/authoring/assets/projects-inactive.png)

## 프로젝트를 비활성 또는 활성 상태로 만들기 {#making-projects-inactive-or-active}

프로젝트를 완료했지만 프로젝트에 대한 정보를 유지하려는 경우 프로젝트를 비활성 상태로 만들 수 있습니다.

프로젝트를 비활성(또는 활성) 상태로 만들려면 다음 작업을 수행하십시오.

1. 다음에서 **프로젝트** 콘솔에서 프로젝트를 연 다음 **프로젝트 정보** 타일.

   >[!NOTE]
   이 타일이 프로젝트에 없는 경우 추가해야 할 수 있습니다. 다음을 참조하십시오 [타일 추가](#adding-items-to-a-tile).

1. **편집**&#x200B;을 탭/클릭합니다.
1. 선택기를 **활성**&#x200B;에서 **비활성**(또는 그 반대)으로 변경합니다.

   ![프로젝트 활성화](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. **완료**&#x200B;를 탭/클릭하여 변경 내용을 저장합니다.
