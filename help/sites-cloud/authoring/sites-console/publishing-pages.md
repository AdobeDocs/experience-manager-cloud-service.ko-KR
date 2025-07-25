---
title: 사이트 콘솔에서 페이지 게시
description: 사이트 콘솔을 사용하여 페이지를 게시 및 게시 취소하는 방법에 대해 알아봅니다.
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 5ad91a32d705ef61e8b9799bf7fb1e136bb8bfa0
workflow-type: tm+mt
source-wordcount: '1635'
ht-degree: 74%

---


# 사이트 콘솔에서 페이지 게시 {#publishing-pages}

작성 환경에서 콘텐츠를 작성 및 검토한 다음, 목표는 [콘텐츠를 공개 웹 사이트(게시 환경)에서 사용할 수 있도록](/help/sites-cloud/authoring/author-publish.md) 만드는 것입니다.

이를 페이지 게시라고도 합니다. 게시 환경에서 페이지를 제거하려는 경우 게시 취소라고 합니다. 게시 및 게시 취소 시 페이지는 삭제될 때까지 추가 변경 사항에 대해 작성자 환경에서 사용할 수 있습니다.

[**사이트** 콘솔](/help/sites-cloud/authoring/sites-console/introduction.md)을 사용하여 페이지를 즉시 또는 미래의 미리 정의된 날짜/시간에 게시/게시 취소할 수 있습니다.

>[!TIP]
>
>사이트 콘솔이 아닌 다른 위치에서 게시할 수 있습니다.
>
>* [페이지 편집기에서](/help/sites-cloud/authoring/page-editor/publishing.md)
>* [유니버설 편집기에서](/help/sites-cloud/authoring/universal-editor/publishing.md)
>* [경험 조각](/help/sites-cloud/authoring/fragments/experience-fragments.md) 콘솔 또는 편집기에서
>
>이러한 위치에서 게시하는 것은 다양한 옵션을 제공하지만 여기에 설명된 유사한 절차와 일반적인 아이디어를 따릅니다.

## 용어 {#terminology}

Adobe Experience Manager(AEM) as a Cloud Service를 사용하여 작업할 때 게시와 관련된 다양한 용어를 접할 수 있습니다.

* **게시/게시 취소**
   * 이 용어는 콘텐츠를 게시 및/또는 미리보기 환경에서 공개적으로 사용할 수 있도록(또는 사용할 수 없도록) 하는 작업을 위한 기본 용어입니다.
   * AEM 설명서에서 사용되는 용어입니다.
* **활성화/비활성화**
   * 게시/게시 취소와 동의어입니다.
   * 이 용어는 이전 AEM 버전에서 사용되었습니다.
* **복제하기 / 복제**
   * 페이지를 게시할 때(예: 작성자에서 미리보기) 한 서비스에서 다른 서비스로의 데이터(예: 페이지 콘텐츠, 파일, 코드, 사용자 댓글) 이동을 설명하는 기술 용어입니다.
   * 주로 개발자가 사용하는 용어입니다.

>[!NOTE]
>
>특정 페이지 게시에 필요한 권한이 없는 경우:
>
>* 게시할 요청을 적절한 사람에게 알리도록 워크플로가 트리거됩니다.
>* 이 워크플로는 개발 팀에서 사용자 정의했을 수 있습니다.
>* 워크플로가 트리거되었음을 알리는 메시지가 짧게 표시됩니다.

>[!NOTE]
>
>페이지 순서를 유지하려면 [게시 관리](#manage-publication)를 사용하여 상위 페이지를 하위 페이지와 함께 단일 작업으로 게시해야 합니다.
>
>페이지 순서는 보장되지 않습니다.
>
>* 하위 페이지만 게시하도록 선택한 경우(상위 페이지에 주문 정보가 있기 때문)
>* 상위 및 하위 페이지가 별도의 작업으로 게시되는 경우

## 사이트 콘솔에서 페이지 게시 {#publishing-from-the-sites-console}

**사이트** 콘솔에는 두 가지 게시 옵션이 있습니다.

* [빠른 게시](#quick-publish)
* [게시 관리](#manage-publication)

### 빠른 게시 {#quick-publish}

**빠른 게시**&#x200B;는 간단한 사례에 해당하며 추가적인 상호 작용 없이 선택한 페이지를 즉시 게시합니다. 이로 인해 게시되지 않은 참조도 자동으로 게시됩니다.

빠른 게시로 페이지를 게시하려면 다음 작업을 수행하십시오.

1. Sites 콘솔에서 페이지를 선택하고 **빠른 게시** 단추를 클릭합니다.

   ![게시할 페이지 선택](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. 빠른 게시 대화 상자에서 **게시**&#x200B;를 클릭하여 게시를 확인하거나 **취소**&#x200B;를 클릭하여 취소를 확인합니다. 게시되지 않은 참조도 자동으로 게시됩니다.

   ![빠른 게시 확인](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. 페이지가 게시되면 게시를 확인하는 알림이 표시됩니다.

>[!NOTE]
>
>빠른 게시는 약식 공개가 아닙니다. 즉, 선택한 페이지만 게시되며 하위 페이지는 게시되지 않습니다.

### 게시 관리 {#manage-publication}

**게시 관리**&#x200B;는 **빠른 게시**&#x200B;보다 더 많은 옵션을 제공하여 하위 페이지 포함, 참조 사용자 지정, 미리보기 서비스(가능한 경우)에 게시 및 적용 가능한 워크플로 시작 등의 작업을 허용하며 나중에 게시할 수 있는 옵션을 제공합니다.

게시 관리를 사용하여 페이지를 게시 또는 게시 취소하려면 다음 작업을 수행하십시오.

1. Sites 콘솔에서 페이지를 선택하고 **게시 관리** 단추를 클릭합니다.

   ![게시할 페이지 선택](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. **게시 관리** 마법사가 시작됩니다. 첫 번째 단계인 **옵션**&#x200B;에서는 다음을 수행할 수 있습니다.

   * **작업**

     선택한 페이지를 게시하거나 게시 취소하도록 선택합니다.

   * **대상**

     게시 서비스(기본값) 또는 미리보기 서비스에 게시할지 선택합니다. [미리 보기 서비스를 구성한 경우에만 사용할 수 있습니다.](/help/sites-cloud/authoring/sites-console/previewing-content.md)

   * **예약**

     지금 또는 나중에 해당 작업을 수행하도록 선택합니다.

     나중에 게시하면 지정된 시간에 선택한 페이지를 게시하기 위한 워크플로를 시작합니다. 반대로 나중에 게시 취소하면 지정된 시간에 선택한 페이지를 게시 취소하기 위한 워크플로를 시작합니다.

     >[!TIP]
     >
     >나중에 게시/게시 취소를 취소하려면 [워크플로 콘솔](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance)로 이동하여 해당 워크플로를 종료합니다.

     >[!TIP]
     >
     >게시를 위한 컨텐츠 예약은 컨텐츠를 복제하고 게시 워크플로를 준수합니다. 게시를 취소하지 않고 이미 게시된 콘텐츠를 일시적으로 숨기려면 페이지 속성에서 사용할 수 있는 [**설정 시간** 및 **해제 시간**&#x200B;을 고려하십시오.](/help/sites-cloud/authoring/sites-console/page-properties.md#basic)

   ![게시 관리 옵션](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

1. 계속하려면 **다음**&#x200B;을 클릭하십시오.

1. 게시 관리 마법사의 다음 단계인 **범위**&#x200B;에서 하위 페이지 포함 여부, 참조 포함 등과 같이 게시/게시 취소 범위를 정의할 수 있습니다.

   ![게시 범위 관리](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   **콘텐츠 추가**

   게시 관리 마법사를 시작하기 전에 선택하지 않은 경우 **콘텐츠 추가** 버튼을 사용하여 게시할 페이지 목록에 페이지를 추가할 수 있습니다.

   **콘텐츠 추가** 버튼을 선택하면 콘텐츠를 선택할 수 있는 [경로 브라우저](/help/sites-cloud/authoring/path-selection.md)가 실행됩니다.

   필요한 페이지를 선택한 다음 **선택**&#x200B;을 클릭하여 마법사에 콘텐츠를 추가하거나 **취소**&#x200B;를 클릭하여 선택을 취소하고 마법사로 돌아갈 수 있습니다.

   **선택 제거**

   마법사로 돌아가 목록에서 항목을 선택하여 선택에서 제거할 수 있습니다.

   ![게시 관리 페이지 선택](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **게시된 참조**

   페이지를 선택한 다음 **게시된 참조** 버튼을 클릭하여 게시되거나 게시 취소된 참조를 보고 수정할 수 있습니다.

   ![게시 관리 옵션](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   **게시된 참조** 대화 상자는 선택한 콘텐츠에 대한 참조를 표시합니다. 기본적으로 모든 항목이 선택되어 있고 게시/게시 취소되지만 선택을 해제하여 취소하면 작업에 포함되지 않습니다.

   **완료**&#x200B;를 클릭하여 변경 사항을 저장하거나 **취소**&#x200B;를 클릭하여 선택 항목을 취소하고 마법사로 돌아갑니다.

   마법사로 돌아가면 **참조** 열이 업데이트되어 게시되거나 게시되지 않을 참조에 대한 선택을 반영합니다.

   ![게시 관리 페이지 선택](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **하위 항목 포함**

   >[!NOTE]
   >
   >[트리 게시 및 게시 취소](#publishing-and-unpublishing-a-tree) 참조

   **하위 항목 포함**&#x200B;을 클릭하면 대화 상자가 열리며 다음과 같은 작업을 수행할 수 있습니다.

   * **하위 항목 포함**
   * **바로 아래 하위 항목만 포함**
   * **수정된 페이지만 포함**
   * **이미 게시된 페이지만 포함**

   필요한 옵션을 활성화하고 **확인**&#x200B;을 사용하여 확인하면 선택 옵션에 따라 게시하거나 게시를 취소할 페이지 목록에 하위 페이지가 추가됩니다. **취소**&#x200B;를 클릭하여 선택 항목을 취소하고 마법사로 돌아갑니다.

   ![하위 항목을 포함한 게시 관리](/help/sites-cloud/authoring/assets/publishing-include-children.png)

1. **게시**&#x200B;를 클릭하여 완료합니다.

   Sites 콘솔로 돌아가면 알림 메시지가 표시되어 게시를 확인합니다.

1. 게시된 페이지가 워크플로와 연관되어 있으면 게시 마법사의 마지막 **워크플로** 단계에 표시될 수 있습니다.

   ![게시 관리 페이지 선택](/help/sites-cloud/authoring/assets/publishing-manage-publication-workflow.png)

   >[!NOTE]
   >
   >**워크플로** 단계는 사용자가 보유하거나 보유하지 않을 수 있는 권한에 따라 표시됩니다. 자세한 내용은 게시 권한에 관한 이 페이지의 이전 메모, 워크플로에 대한 액세스 권한 관리 및 [워크플로를 페이지에 적용](/help/sites-cloud/authoring/workflows/applying.md)을 참조하십시오.

   참조는 트리거된 워크플로 및 지정된 옵션별로 그룹화되어 다음 작업을 수행할 수 있습니다.

   * 워크플로의 제목을 정의합니다.
   * 워크플로가 다중 참조 지원을 제공한다면 워크플로 패키지를 유지합니다.
   * 워크플로 패키지를 유지하는 옵션이 선택된 경우 워크플로 패키지의 제목을 정의합니다.

1. **게시** 또는 **나중에 게시**&#x200B;를 클릭하여 게시를 완료할 수 있습니다.

## 페이지 게시 취소 {#unpublishing-pages}

페이지 게시를 취소하면 더 이상 읽을 수 없도록 페이지가 게시 또는 [미리보기](/help/sites-cloud/authoring/sites-console/previewing-content.md) 환경에서 제거됩니다.

[게시하기 위해 게시 관리를 사용](#manage-publication)하는 것과 같은 방식으로 게시 취소할 수 있습니다.

1. Sites 콘솔에서 페이지를 선택하고 **게시 관리** 단추를 클릭합니다.
1. **게시 관리** 마법사가 시작됩니다. 첫 번째 단계인 **옵션**&#x200B;에서 기본 옵션인 **게시**&#x200B;를 선택하는 대신 **게시 취소**&#x200B;를 선택합니다.

   ![게시 취소 - 옵션](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   나중에 게시를 사용하면 지정된 시간에 이 페이지 버전을 게시하는 워크플로가 시작됩니다. 나중에 비활성화를 사용하면 특정 시간에 선택한 페이지를 게시 취소하는 워크플로가 시작됩니다.

   >[!NOTE]
   >
   >나중에 게시/게시 취소를 취소하려면 [워크플로 콘솔](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance)로 이동하여 해당 워크플로를 종료합니다.

   >[!NOTE]
   >[미리보기](/help/sites-cloud/authoring/sites-console/previewing-content.md) 환경이 있는 경우 게시 관리 중에 **대상**&#x200B;을 선택할 수 있습니다.

1. 게시 취소를 완료하려면 [페이지를 게시](#manage-publication)하는 것처럼 마법사를 계속 사용하십시오.

   ![게시 취소 - 범위](/help/sites-cloud/authoring/assets/publishing-unpublish-scope.png)

## 트리 게시 및 게시 취소 {#publishing-and-unpublishing-a-tree}

동일한 루트 페이지 아래에서 수많은 콘텐츠 페이지를 입력하거나 업데이트한 경우 전체 트리를 한 번에 게시하면 더욱 편리할 수 있습니다.

Sites 콘솔에서 [게시 관리](#manage-publication) 옵션을 사용하여 이 작업을 수행할 수 있습니다.

1. 사이트 콘솔에서 게시 또는 게시 취소하려는 트리의 루트 페이지를 선택하고 **게시 관리**&#x200B;를 선택합니다.
1. **게시 관리** 마법사가 시작됩니다. 게시 또는 게시 취소하도록 선택하고 해당 작업이 수행되면 **다음**&#x200B;을 클릭하여 계속 진행합니다.
1. **범위** 단계에서 루트 페이지를 선택하고 **하위 포함**&#x200B;을 선택합니다.

   ![게시 관리 페이지 선택](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. **하위 항목 포함** 대화 상자에서 다음 작업을 수행합니다.

   * **하위 항목 포함** 선택
   * **바로 아래 하위만 포함** 선택
   * **이미 게시된 페이지만 포함** 선택 해제
   * 필요한 경우 **수정된 페이지만 포함** 구성

   이들 옵션은 기본적으로 선택되어 있으므로 반드시 구성해야 합니다. **확인**&#x200B;을 사용하여 선택을 확인하면 콘텐츠가 게시/게시 취소에 추가됩니다.

   ![트리 게시에 하위 항목 추가](/help/sites-cloud/authoring/assets/publishing-include-children-tree.png)

1. **게시 관리** 마법사에서 이후에 추가 페이지를 추가하거나 선택한 페이지를 제거하여 선택을 맞춤화할 수 있습니다.

   **게시된 참조** 옵션을 통해 게시되는 참조 자료도 검토할 수 있습니다.

1. [게시 관리 마법사를 정상적으로 계속 진행](#manage-publication)하여 트리 게시 또는 게시 취소를 완료합니다.

## 게시 상태 확인 {#determining-publication-status}

페이지의 게시 상태를 확인할 수 있습니다.

* [Sites 콘솔의 리소스 개요 정보](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources)에서

  ![카드 보기의 게시 상태](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

  게시 상태는 Sites 콘솔에 [카드](/help/sites-cloud/authoring/basic-handling.md#card-view), [열](/help/sites-cloud/authoring/basic-handling.md#column-view), [목록](/help/sites-cloud/authoring/basic-handling.md#list-view) 보기로 표시됩니다.

* [타임라인](/help/sites-cloud/authoring/basic-handling.md#timeline)에서

  ![타임라인 보기의 게시 상태](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* 페이지를 편집할 때 [페이지 정보 메뉴](/help/sites-cloud/authoring/page-editor/introduction.md#page-information)에서

  ![페이지 정보 메뉴의 게시 상태](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
