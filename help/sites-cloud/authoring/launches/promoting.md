---
title: 론치 홍보
description: 게시 전에 콘텐츠를 소스(프로덕션)로 다시 이동하려면 론치 페이지를 홍보해야 합니다.
exl-id: 5f5ed17c-43db-4ef6-ab79-c491326fa01c
source-git-commit: 47910a27118a11a8add6cbcba6a614c6314ffe2a
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 55%

---

# 론치 홍보 {#promoting-launches}

게시 전에 콘텐츠를 소스(프로덕션)로 다시 이동하려면 론치 페이지를 홍보해야 합니다. 론치 페이지가 홍보되면 해당 소스 페이지가 홍보된 페이지의 콘텐츠로 바뀝니다. 론치 페이지를 홍보할 때 사용할 수 있는 옵션은 다음과 같습니다.

* 현재 페이지만 홍보할지 전체 론치를 홍보할지 여부입니다.
* 현재 페이지의 하위 페이지를 승격할지 여부입니다.
* 전체 론치를 홍보할지 또는 변경된 페이지만 홍보할지 여부입니다.
* 홍보한 후 론치를 삭제할지 여부입니다.

>[!NOTE]
>
>론치 페이지를 타겟으로 승격시킨 후(**프로덕션**)을 활성화하면 **프로덕션** 페이지를 엔티티로 지정(프로세스를 보다 신속하게 수행)합니다. 페이지를 작업 흐름 패키지에 추가하고, 페이지 패키지를 활성화하는 작업 흐름용 페이로드로 사용합니다. 론치를 승격하려면 먼저 작업 흐름 패키지를 만들어야 합니다. [AEM 워크플로를 사용하여 홍보된 페이지 처리](#processing-promoted-pages-using-aem-workflow)를 참조하십시오.

>[!CAUTION]
>
>단일 론치를 동시에 홍보할 수 없습니다. 즉, 동일한 론치에 대해 두 가지 홍보 작업을 동시에 수행하면 로그에 충돌 오류와 함께 `Launch could not be promoted`라는 오류가 표시됩니다.

>[!CAUTION]
>
>에 대한 론치를 홍보할 때 *수정됨* 페이지, 소스 및 launch 분기 모두에서 수정 사항이 고려됩니다.

## 론치 페이지 홍보 {#promoting-launch-pages}

>[!NOTE]
>
>이 섹션에서는 론치 수준이 하나만 있는 경우 론치 페이지를 홍보하는 수동 작업을 다룹니다. 다음을 참조하십시오.
>
>* [중첩 론치 홍보](#promoting-a-nested-launch) 구조에 두 개 이상의 론치가 있는 경우.
>* [론치 - 이벤트 순서](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) 자동 홍보 및 게시에 대한 자세한 내용은 을 참조하십시오.
>


다음 중 하나에서 론치를 승격할 수 있습니다. **사이트** 콘솔 또는 **론치** 콘솔:

1. 열기:
   * 소스 페이지 탐색 시 **사이트 콘솔**:
      1. [참조 레일](/help/sites-cloud/authoring/fundamentals/environment-tools.md#references)을 연 다음 [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md)를 사용하여 필요한 소스 페이지를 선택합니다. 순서는 중요하지 않으므로 필요한 소스 페이지를 선택한 다음 참조 레일을 열 수도 있습니다. 모든 참조가 표시됩니다.
      1. 특정 론치 목록을 표시하려면 **론치**(예: 론치(1))를 선택합니다.
      1. 사용 가능한 작업을 표시하려면 특정 론치를 선택합니다.
      1. **론치 홍보**&#x200B;를 선택하여 마법사를 엽니다.
   * 론치 페이지 탐색 시 **사이트 콘솔**:
      1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md)를 사용하여 필요한 론치 페이지를 선택합니다.
      1. 도구 모음에 **홍보** 작업이 표시됩니다.
   * **론치** 콘솔:
      1. 론치를 선택합니다(썸네일 탭/클릭).
      1. 선택 **홍보**.
1. 첫 번째 단계에서 다음을 지정할 수 있습니다.
   * **대상**
      * **승격 후 실행 삭제**
   * **범위**
      * **전체 론치 홍보**
      * **수정된 페이지 홍보**
      * **승인된 페이지 홍보** - 론치 승인 워크플로에 따라 다름
      * **현재 페이지 홍보**
      * **현재 페이지 및 하위 페이지 홍보**

      예를 들어 수정된 페이지만 홍보하도록 선택하는 경우:

      ![론치 홍보](/help/sites-cloud/authoring/assets/launches-promote.png)

      >[!NOTE]
      >
      >중첩 론치가 있는 경우 단일 론치를 포함합니다. [중첩 론치 홍보](#promoting-a-nested-launch).
1. 선택 **다음** 계속합니다.
1. 홍보할 페이지를 검토할 수 있습니다. 이는 선택한 페이지 범위에 따라 달라집니다.

   ![홍보 검토](/help/sites-cloud/authoring/assets/launches-promote-review.png)

1. 선택 **홍보**.

## 편집 시 론치 페이지 홍보 {#promoting-launch-pages-when-editing}

론치 페이지를 편집할 때 **출시 홍보** 작업은에서 사용할 수도 있습니다. **페이지 정보**. 이 작업을 수행하면 필요한 정보를 수집하기 위한 마법사가 열립니다.

![사이트 정보로 론치 홍보](/help/sites-cloud/authoring/assets/launches-promote-page-info.png)

>[!NOTE]
>
>이 기능은 단일 및 [중첩 론치](#promoting-a-nested-launch).

## 중첩 론치 홍보 {#promoting-a-nested-launch}

중첩 론치를 만든 후 이를 루트 소스(프로덕션)를 포함한 모든 소스로 다시 홍보할 수 있습니다.

![중첩 론치](/help/sites-cloud/authoring/assets/launches-promoting-nested.png)

1. 중첩 론치 만들기의 경우처럼, **론치** 콘솔 또는 **참조** 레일로 이동한 후 필요한 론치를 선택합니다.
1. **론치 홍보**&#x200B;를 선택하여 마법사를 엽니다.
1. 다음과 같은 필수 세부 정보를 입력합니다.
   * **대상**
      * **홍보 대상** - 원하는 소스를 홍보할 수 있습니다.
      * **홍보 후 론치 삭제:** 선택한 론치를 홍보하면 여기에 중첩된 론치가 삭제됩니다.
   * **범위** - 여기에서 전체 론치를 홍보할지 또는 실제로 편집된 페이지만 홍보할지 여부를 선택할 수 있습니다. 후자의 경우 하위 페이지를 포함/제외하도록 선택할 수 있습니다. 기본 구성은 현재 페이지에 대한 페이지 변경 사항만 프로모션하는 것입니다.
      * **전체 론치 홍보**
      * **수정된 페이지 홍보**
      * **승인된 페이지 홍보** - 론치 승인 워크플로에 따라 다름
      * **현재 페이지 홍보**
      * **현재 페이지 및 하위 페이지 홍보**

   ![론치 홍보 설정](/help/sites-cloud/authoring/assets/launches-promote-settings.png)

1. **다음**&#x200B;을 선택합니다.
1. **홍보**&#x200B;를 선택하기 전에 홍보 세부 정보를 검토하십시오.

   ![홍보 설정 검토](/help/sites-cloud/authoring/assets/launches-promote-review-2.png)

   >[!NOTE]
   >
   >나열된 페이지는 다음에 따라 다릅니다. **범위** 가 정의되었으며 실제로 편집된 페이지일 수 있습니다.

1. 변경 사항이 프로모션되고 다음에 반영됩니다. **론치** 콘솔:

   ![론치 콘솔에서](/help/sites-cloud/authoring/assets/launches-console.png)

## AEM 워크플로를 사용하여 홍보된 페이지 처리 {#processing-promoted-pages-using-aem-workflow}

워크플로우 모델을 사용하여 판촉된 론치 페이지의 일괄 처리를 수행합니다.

1. 워크플로우 패키지를 만듭니다.
1. 작성자가 Launch 페이지를 홍보하면 워크플로우 패키지에 저장합니다.
1. 패키지를 페이로드로 사용하여 워크플로우 모델을 시작합니다.

페이지가 홍보될 때 워크플로를 자동으로 시작하려면 패키지 노드에 대한 워크플로 시작 관리자를 구성합니다. <!--To start a workflow automatically when pages are promoted, [configure a workflow launcher](/help/sites-administering/workflows-starting.md#workflows-launchers) for the package node.-->

예를 들어 작성자가 론치 페이지를 승격하면 페이지 활성화 요청을 자동으로 생성할 수 있습니다. 패키지 노드가 수정되면 활성화 요청 워크플로를 시작하도록 워크플로 시작 관리자를 구성합니다.

![홍보 워크플로](/help/sites-cloud/authoring/assets/launches-create-workflow.png)
