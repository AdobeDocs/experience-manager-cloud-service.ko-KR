---
title: 페이지에 워크플로 적용
description: 작성 시 페이지에서 수행할 워크플로를 불러올 수 있습니다. 하나 이상의 워크플로를 적용할 수도 있습니다.
exl-id: 86e71f0e-e53e-40bc-901d-2a1ab347bd0a
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 100%

---

# 페이지에 워크플로 적용 {#applying-workflows-to-pages}

작성 시 페이지에서 수행할 워크플로를 불러올 수 있습니다. 하나 이상의 워크플로를 적용할 수도 있습니다.

워크플로를 적용할 때에는 다음 정보를 지정합니다.

* 적용할 워크플로.
   * AEM 관리자가 할당한 대로 액세스할 수 있는 워크플로를 적용할 수 있습니다.
* 원할 경우, 사용자의 받은 편지함에서 워크플로 인스턴스를 식별하는 데 도움이 되는 제목.
* 워크플로 페이로드. 하나 이상의 페이지일 수 있습니다.

워크플로는 다음 위치에서 시작될 수 있습니다.

* [Sites 콘솔](#starting-a-workflow-from-the-sites-console)
* [페이지 편집 시 페이지 정보](#starting-a-workflow-from-the-page-editor)

>[!NOTE]
>
>추가 참조:
>
>* 워크플로를 DAM 자산에 적용하는 방법
>* [프로젝트 워크플로를 사용하여 작업](/help/sites-cloud/authoring/projects/workflows.md)

<!-- 
>* [How to apply workflows to DAM assets](/help/assets/assets-workflow.md).
>* [Working with Project Workflows](/help/sites-cloud/authoring/projects/workflows.md).
-->

>[!NOTE]
>
>AEM 관리자는 몇 가지 다른 방법을 사용하여 워크플로를 시작할 수 있습니다.

<!-- 
>AEM administrators can [start workflows using several other methods](/help/sites-administering/workflows-starting.md).
-->

## Sites 콘솔에서 워크플로 시작 {#starting-a-workflow-from-the-sites-console}

다음 중 하나에서 워크플로를 시작할 수 있습니다.

* [사이트 도구 모음의 [만들기] 옵션](#starting-a-workflow-from-the-sites-toolbar)
* [Sites 콘솔의 타임라인 레일](#starting-a-workflow-from-the-timeline)

두 경우 모두 다음 작업을 수행해야 합니다.

* [워크플로 만들기 마법사에서 워크플로 세부 사항 지정](#specifying-workflow-details-in-the-create-workflow-wizard)

### 사이트 도구 모음에서 워크플로 시작 {#starting-a-workflow-from-the-sites-toolbar}

**사이트** 콘솔의 도구 모음에서 워크플로를 시작할 수 있습니다.

1. 필요한 페이지로 이동하여 선택합니다.

1. 이제 도구 모음의 **만들기** 옵션에서 **워크플로**&#x200B;를 선택할 수 있습니다.

   ![도구 모음에서 워크플로 만들기](/help/sites-cloud/authoring/assets/workflows-create-from-toolbar.png)

1. **워크플로 만들기** 마법사는 [워크플로 세부 사항을 지정](#specifying-workflow-details-in-the-create-workflow-wizard)하는 데 도움이 됩니다.

### 타임라인에서 워크플로 시작 {#starting-a-workflow-from-the-timeline}

**타임라인**&#x200B;에서는 선택한 리소스에 적용할 워크플로를 시작할 수 있습니다.

1. [리소스를 선택](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)한 다음 [타임라인](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)을 엽니다(또는 타임라인을 연 다음 리소스 선택).
1. 설명 필드 옆에 있는 화살표를 사용하여 **워크플로 시작**&#x200B;을 표시할 수 있습니다.

   ![타임라인에서 워크플로 만들기](/help/sites-cloud/authoring/assets/workflows-create-from-timeline.png)

1. **워크플로 만들기** 마법사는 [워크플로 세부 사항을 지정](#specifying-workflow-details-in-the-create-workflow-wizard)하는 데 도움이 됩니다.

### 워크플로 만들기 마법사에서 워크플로 세부 사항 지정 {#specifying-workflow-details-in-the-create-workflow-wizard}

**워크플로 만들기** 마법사는 워크플로를 선택하고 필요한 세부 사항을 지정하는 데 도움이 됩니다.

다음 중 하나에서 **워크플로 만들기** 마법사를 여십시오.

* [사이트 도구 모음의 [만들기] 옵션](#starting-a-workflow-from-the-sites-toolbar)
* [Sites 콘솔의 타임라인 레일](#starting-a-workflow-from-the-timeline)

세부 사항을 지정할 수 있습니다.

1. **속성** 단계에서는 워크플로의 기본 옵션이 정의됩니다.

   * **워크플로 모델**
   * **워크플로 제목**

      * 나중 단계에서 식별할 수 있도록 이 인스턴스의 제목을 지정할 수 있습니다.

   워크플로 모델에 따라 다음 옵션도 사용할 수 있습니다. 이 옵션을 사용하면 워크플로가 완료된 후에도 페이로드로 만들어진 패키지를 유지할 수 있습니다.

   * **워크플로 패키지 유지**
   * **패키지 제목**

      * 식별할 수 있도록 패키지의 제목을 지정할 수 있습니다.

   >[!NOTE]
   >
   >**워크플로 패키지 유지** 옵션은 여러 리소스 지원에 대해 워크플로를 구성했으며 여러 리소스를 선택한 경우에 사용할 수 있습니다.

   <!--
   >The **Keep workflow package** option is available when the workflow has been configured for [Multi Resource Support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) and multiple resources have been selected.
   -->

   완료되면 **다음**&#x200B;을 사용하여 계속 진행하십시오.

   ![워크플로 속성 지정](/help/sites-cloud/authoring/assets/workflows-properties.png)

1. **범위** 단계에서 다음을 선택할 수 있습니다.

   * **콘텐츠 추가**: [경로 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser)를 열고 추가 리소스를 선택합니다. 브라우저에서 **선택**&#x200B;을 클릭/탭하여 워크플로 인스턴스에 콘텐츠를 추가합니다.

   * 추가 작업을 보기 위한 기존 리소스:

      * **하위 포함** - 해당 리소스의 하위 항목이 워크플로에 포함되도록 지정합니다.
대화 상자가 열리고 다음 내용에 따라 선택 내용을 개선할 수 있습니다.

         * 바로 아래 하위 항목만 포함
         * 수정된 페이지만 포함.
         * 이미 게시된 페이지만 포함.

        지정된 모든 하위 항목이 워크플로가 적용될 리소스 목록에 추가됩니다.

      * **선택 제거** - 워크플로에서 해당 리소스를 제거합니다.

   ![워크플로 범위 정의](/help/sites-cloud/authoring/assets/workflows-scope.png)

   >[!NOTE]
   >
   >추가 리소스를 추가하면 **뒤로**&#x200B;를 사용하여 **속성** 단계의 **워크플로 패키지 유지** 설정을 조정할 수 있습니다.

1. **만들기**&#x200B;를 사용하여 마법사를 닫고 워크플로 인스턴스를 만듭니다. 알림은 Sites 콘솔에 표시됩니다.

## 페이지 편집기에서 워크플로 시작 {#starting-a-workflow-from-the-page-editor}

페이지를 편집할 때 도구 모음에서 **페이지 정보**&#x200B;를 선택할 수 있습니다. 드롭다운 메뉴에는 **워크플로에서 시작** 옵션이 있습니다. 이 옵션을 선택하면 필요한 경우 제목과 함께 필요한 워크플로를 지정할 수 있는 대화 상자가 열립니다.

![페이지 편집기에서 워크플로 시작](/help/sites-cloud/authoring/assets/workflows-create-page-editor.png)
