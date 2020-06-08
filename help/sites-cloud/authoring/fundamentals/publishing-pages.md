---
title: 페이지 게시
description: AEM을 사용하여 페이지를 게시 및 게시 취소하는 방법
translation-type: tm+mt
source-git-commit: f04dd39a5a22f44f976f2e473689780099f10f9a
workflow-type: tm+mt
source-wordcount: '1694'
ht-degree: 100%

---


# 페이지 게시 {#publishing-pages}

작성 환경에서 컨텐츠를 작성 및 검토한 후에는 [공개 웹 사이트(게시 환경)에서 사용할 수 있도록](/help/sites-cloud/authoring/getting-started/concepts.md) 만들어야 합니다.

이를 페이지 게시라고도 합니다. 게시 환경에서 페이지를 제거하려는 경우 게시 취소라고 합니다. 게시 및 게시 취소할 때 작성 환경에서 페이지를 삭제할 때까지 계속 변경할 수 있습니다.

페이지를 즉시 또는 미래의 미리 정의된 날짜/시간에 게시/게시 취소할 수 있습니다.

## 용어 {#terminology}

AEM에서 작업할 때 게시와 관련된 다양한 용어가 있을 수 있습니다.

* **게시/게시 취소**
   * 이 용어는 컨텐츠를 게시 환경에서 공개적으로 사용할 수 있도록(또는 사용할 수 없도록) 하는 작업을 위한 기본 용어입니다.
   * AEM 설명서에서 사용되는 용어입니다.
* **활성화/비활성화**
   * 게시/게시 취소와 동의어입니다.
   * 이 용어는 이전 AEM 버전에서 사용되었습니다.
* **복제**
   * 페이지를 게시할 때 한 환경에서 다른 환경으로의 데이터(예: 페이지 컨텐츠, 파일, 코드, 사용자 댓글) 이동을 설명하는 기술 용어입니다.
   * 주로 개발자가 사용하는 용어입니다.

## 페이지 게시 {#publishing-pages-1}

다음 위치에 따라 게시할 수 있습니다.

* [페이지 편집기에서](#publishing-from-the-editor)
* [사이트 콘솔에서](#publishing-from-the-console)

>[!NOTE]
>
>특정 페이지 게시에 필요한 권한이 없는 경우:
>
>* 게시할 요청을 적절한 사람에게 알리도록 워크플로우가 트리거됩니다.
>* 이 워크플로우는 개발 팀에서 사용자 지정했을 수 있습니다.
>* 워크플로우가 트리거되었음을 알리는 메시지가 짧게 표시됩니다.


<!--
>* This [workflow may have been customized](/help/sites-developing/workflows-models.md#main-pars-procedure-6fe6) by your development team.
>* A message will be displayed briefly to notify you that the workflow was triggered.
-->

### 편집기에서 게시 {#publishing-from-the-editor}

페이지를 편집하는 경우 편집기에서 직접 게시할 수 있습니다.

1. **페이지 정보** 아이콘을 선택하여 메뉴를 열고 **페이지 게시** 옵션을 엽니다.

   ![페이지 옵션을 통해 페이지 게시](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. 페이지에 게시해야 하는 참조가 있는지에 따라 다음과 같이 달라집니다.

   * 게시할 참조가 없으면 페이지가 직접 게시됩니다.
   * 페이지에 게시해야 하는 참조가 있을 경우 **게시 마법사**&#x200B;에 나열되며 여기서 다음을 수행할 수 있습니다.
      * 페이지와 함께 게시할 자산, 태그 등 하나를 지정한 다음 **게시**&#x200B;를 사용하여 프로세스를 완료합니다.
      * **취소**&#x200B;를 사용하여 작업을 중단합니다.
   ![페이지를 사용하여 참조 게시](/help/sites-cloud/authoring/assets/publishing-references.png)

1. **게시**&#x200B;를 선택하면 페이지가 게시 환경에 복제됩니다. 페이지 편집기에 게시 작업을 확인하는 정보 배너가 표시됩니다.

   ![게시 상태 정보 배너](/help/sites-cloud/authoring/assets/publishing-info.png)

   콘솔에서 동일한 페이지를 볼 때 업데이트된 게시 상태가 표시됩니다.

   ![Sites 콘솔 열 보기의 페이지 게시 상태](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>편집기에서 게시하면 약식 공개가 아닙니다. 즉, 선택한 페이지만 게시되며 하위 페이지는 게시되지 않습니다.

### 콘솔에서 게시 {#publishing-from-the-console}

사이트 콘솔에는 게시에 대한 두 가지 옵션이 있습니다.

* [빠른 게시](#quick-publish)
* [게시 관리](#manage-publication)

#### 빠른 게시 {#quick-publish}

**빠른 게시**&#x200B;는 간단한 사례에 해당하며 추가적인 상호 작용 없이 선택한 페이지를 즉시 게시합니다. 이로 인해 게시되지 않은 참조도 자동으로 게시됩니다.

빠른 게시로 페이지를 게시하려면 다음을 수행하십시오.

1. Sites 콘솔에서 페이지를 선택하고 **빠른 게시** 단추를 누릅니다.

   ![게시할 페이지 선택](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. 빠른 게시 대화 상자에서 **게시**&#x200B;를 클릭하여 게시를 확인하거나 **취소**&#x200B;를 클릭하여 취소를 확인합니다. 게시되지 않은 참조도 자동으로 게시됩니다.

   ![빠른 게시 확인](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. 페이지가 게시되면 게시를 확인하는 알림이 표시됩니다.

>[!NOTE]
>
>빠른 게시는 약식 공개가 아닙니다. 즉, 선택한 페이지만 게시되며 하위 페이지는 게시되지 않습니다.

#### 게시 관리 {#manage-publication}

**게시 관리**&#x200B;는 빠른 게시보다 많은 옵션을 제공하여 하위 페이지, 참조의 사용자 지정, 적용 가능한 워크플로우 시작뿐 아니라 나중에 게시할 수 있는 옵션이 포함되어 있습니다.

게시 관리를 사용하여 페이지를 게시 또는 게시 취소하려면 다음을 수행하십시오.

1. Sites  콘솔에서 페이지를 선택하고 **게시 관리** 단추를 누릅니다.

   ![게시할 페이지 선택](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. **게시 관리** 마법사가 시작됩니다. 첫 번째 단계인 **옵션**&#x200B;에서 다음 작업을 수행할 수 있습니다.

   * 선택한 페이지를 게시하거나 게시 취소하도록 선택합니다.
   * 지금 또는 나중에 해당 작업을 수행하도록 선택합니다.
   나중에 게시하면 지정된 시간에 선택한 페이지를 게시하기 위한 워크플로우를 시작합니다. 반대로 나중에 게시 취소하면 지정된 시간에 선택한 페이지를 게시 취소하기 위한 워크플로우를 시작합니다.

   나중에 게시/게시 취소를 취소하려면 워크플로우 콘솔로 가서 해당 워크플로우를 종료합니다. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

   ![게시 관리 옵션](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

   계속하려면 **다음**&#x200B;을 클릭하십시오.

1. 게시 관리 마법사의 다음 단계인 **범위**&#x200B;에서 하위 페이지 포함 여부, 참조 포함 등과 같이 게시/게시 취소 범위를 정의할 수 있습니다.

   ![게시 범위 관리](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   게시 관리 마법사를 시작하기 전에 선택하지 않은 경우 **컨텐츠 추가** 단추를 사용하여 게시할 페이지 목록에 페이지를 추가할 수 있습니다.

   컨텐츠 추가 단추를 클릭하면 [경로 브라우저](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser)가 시작되어 컨텐츠를 선택할 수 있습니다.

   필요한 페이지를 선택한 후 **선택**&#x200B;을 클릭하여 컨텐츠를 마법사에 추가하거나 **취소**를 클릭하여 선택 사항을 취소하고 마법사로 돌아갈 수 있습니다.

   마법사로 돌아가 목록에서 항목을 선택한 뒤 다음과 같은 추가 옵션을 구성할 수 있습니다.

   * 하위 항목을 포함합니다.
   * 선택 사항에서 제거합니다.
   * 게시된 참조를 관리합니다.
   ![게시 관리 페이지 선택](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **하위 포함**&#x200B;을 클릭하면 대화 상자가 열려 다음 작업을 수행할 수 있습니다.

   * 바로 아래 하위만 포함.
   * 수정된 페이지만 포함.
   * 이미 게시된 페이지만 포함.
   **추가**&#x200B;를 클릭하여 선택 옵션에 따라 게시하거나 게시 취소할 페이지 목록에 하위 페이지를 추가합니다. **취소**&#x200B;를 클릭하여 선택 항목을 취소하고 마법사로 돌아갑니다.

   ![하위 항목을 포함한 게시 관리](/help/sites-cloud/authoring/assets/publishing-include-children.png)

   마법사로 돌아가면 하위 포함 대화 상자의 옵션 선택에 따라 추가된 페이지가 표시됩니다.

   페이지를 선택한 다음 **게시된 참조** 단추를 클릭하여 게시되거나 게시 취소된 참조를 보고 수정할 수 있습니다.

   ![게시 관리 옵션](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   **게시된 참조** 대화 상자는 선택한 컨텐츠에 대한 참조를 표시합니다. 기본적으로 모든 항목이 선택되어 있고 게시/게시 취소되지만 선택을 해제하여 취소하면 작업에 포함되지 않습니다.

   **완료**&#x200B;를 클릭하여 변경 사항을 저장하거나 **취소**&#x200B;를 클릭하여 선택 항목을 취소하고 마법사로 돌아갑니다.

   마법사로 돌아가면 **참조** 열이 업데이트되어 게시되거나 게시되지 않을 참조에 대한 선택을 반영합니다.

   ![게시 관리 페이지 선택](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. **게시**&#x200B;를 클릭하여 완료합니다.

   사이트 콘솔로 돌아가면 알림 메시지가 표시되어 게시를 확인합니다.

1. 게시된 페이지가 워크플로우와 연관되어 있으면 게시 마법사의 마지막 **워크플로우** 단계에 표시될 수 있습니다.

   >[!NOTE]
   >
   >**워크플로우** 단계는 사용자가 보유하거나 보유하지 않을 수 있는 권한에 따라 표시됩니다. 자세한 내용은 게시 권한에 관한 이 페이지의 이전 메모, 워크플로우에 대한 액세스 권한 관리 및 [워크플로우를 페이지에 적용](/help/sites-cloud/authoring/workflows/applying.md)을 참조하십시오.
   <!--
   >The **Workflows** step will be shown based on what rights your user may or may not have. See the previous note on this page regarding publishing privileges as well as [Managing Access to Workflows](/help/sites-administering/workflows-managing.md) and [Applying Workflows to Pages](/help/sites-cloud/authoring/workflows/applying.md) for details.
   -->

   참조는 트리거된 워크플로우 및 지정된 옵션별로 그룹화되어 다음 작업을 수행할 수 있습니다.

   * 워크플로우의 제목을 정의합니다.
   * 워크플로우가 다중 참조 지원을 제공한다면 워크플로우 패키지를 유지합니다.
   <!--Keep the workflow package, provided that the workflow has [multi-resource support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support).
    -->

   * 워크플로우 패키지를 유지하는 옵션이 선택된 경우 워크플로우 패키지의 제목을 정의합니다.
   **게시** 또는 **나중에 게시**&#x200B;를 클릭하여 게시를 완료할 수 있습니다.

## 페이지 게시 취소 {#unpublishing-pages}

페이지 게시를 취소하면 더 이상 읽을 수 없도록 페이지가 게시 환경에서 제거됩니다.

[게시와 유사한 방식으로](#publishing-pages) 하나 이상의 페이지에 대한 게시를 취소할 수 있습니다.

* [페이지 편집기에서](#unpublishing-from-the-editor)
* [사이트 콘솔에서](#unpublishing-from-the-console)

### 편집기에서 게시 취소 {#unpublishing-from-the-editor}

페이지를 편집할 때 해당 페이지의 게시를 취소하려는 경우 [페이지를 게시](#publishing-from-the-editor)한 만큼 **페이지 정보** 메뉴에서 **페이지 게시 취소**&#x200B;를 선택합니다.

### 콘솔에서 게시 취소 {#unpublishing-from-the-console}

[게시하기 위해 게시 관리를 사용](#manage-publication)하는 것과 같은 방식으로 게시 취소할 수 있습니다.

1. Sites 콘솔에서 페이지를 선택하고 **게시 관리** 단추를 누릅니다.
1. **게시 관리** 마법사가 시작됩니다. 첫 번째 단계인 **옵션**&#x200B;에서 기본 옵션인 **게시**&#x200B;를 선택하는 대신 **게시 취소**&#x200B;를 선택합니다.

   ![게시 취소](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   나중에 게시를 사용하면 지정된 시간에 이 페이지 버전을 게시하는 워크플로우가 시작됩니다. 나중에 비활성화를 사용하면 특정 시간에 선택한 페이지를 게시 취소하는 워크플로우가 시작됩니다.

   나중에 게시/게시 취소를 취소하려면 워크플로우 콘솔로 가서 해당 워크플로우를 종료합니다. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

1. 게시 취소를 완료하려면 [페이지를 게시](#manage-publication)하는 것처럼 마법사를 계속 사용하십시오.

## 트리 게시 및 게시 취소 {#publishing-and-unpublishing-a-tree}

동일한 루트 페이지 아래에서 수많은 컨텐츠 페이지를 입력하거나 업데이트한 경우 전체 트리를 한 번에 게시하면 더욱 편리할 수 있습니다.

사이트 콘솔에서 [게시 관리](#manage-publication) 옵션을 사용하여 이 작업을 수행할 수 있습니다.

1. 사이트 콘솔에서 게시 또는 게시 취소하려는 트리의 루트 페이지를 선택하고 **게시 관리**&#x200B;를 선택합니다.
1. **게시 관리** 마법사가 시작됩니다. 게시 또는 게시 취소하도록 선택하고 해당 작업이 수행되면 **다음**&#x200B;을 클릭하여 계속 진행합니다.
1. **범위** 단계에서 루트 페이지를 선택하고 **하위 포함**&#x200B;을 선택합니다.

   ![게시 관리 페이지 선택](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. **하위 포함** 대화 상자에서 다음과 같은 옵션을 선택 취소합니다.

   * 바로 아래 하위만 포함
   * 이미 게시된 페이지만 포함
   이러한 옵션이 기본적으로 선택되므로 선택 취소해야 합니다. **추가**&#x200B;를 클릭하여 게시/게시 취소할 컨텐츠를 확인하고 추가합니다.

   ![게시 취소 시 하위 포함](/help/sites-cloud/authoring/assets/publishing-tree-children.png)

1. **게시 관리** 마법사에 검토할 트리 컨텐츠가 나열됩니다. 페이지를 추가하거나 선택한 페이지를 제거하여 선택 사항을 추가로 사용자 지정할 수 있습니다.

   ![게시 관리 옵션](/help/sites-cloud/authoring/assets/publishing-tree-select.png)

   **게시된 참조** 옵션을 통해 게시되는 참조 자료도 검토할 수 있습니다.

1. [게시 관리 마법사를 정상적으로 계속 진행](#manage-publication)하여 트리 게시 또는 게시 취소를 완료합니다.

## 게시 상태 확인 {#determining-publication-status}

페이지의 게시 상태를 확인할 수 있습니다.

* ](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)사이트 콘솔의 리소스 개요 정보[에서

   ![카드 보기의 게시 상태](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

   게시 상태는 사이트 콘솔에 [카드](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view), [열](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view), [목록](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) 보기로 표시됩니다.

* [타임라인](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)에서

   ![타임라인 보기의 게시 상태](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* 페이지를 편집할 때 [페이지 정보 메뉴](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information)에서

   ![페이지 정보 메뉴의 게시 상태](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
