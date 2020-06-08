---
title: 폴더 및 컬렉션의 자산 검토
description: 폴더 또는 컬렉션 내의 에셋에 대한 검토 워크플로우를 설정하고 검토자 또는 크리에이티브 파트너와 공유하여 피드백을 얻을 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 3%

---


# 폴더 및 컬렉션의 자산 검토 {#review-folder-assets-and-collections}

AEM(Adobe Experience Manager) 자산을 사용하여 폴더 또는 컬렉션에 있는 자산에 대한 임시 검토 워크플로우를 설정할 수 있습니다. 검토자 또는 크리에이티브 파트너와 공유하여 피드백을 요청할 수 있습니다. 검토 워크플로우를 프로젝트와 연결하거나 독립적인 검토 작업을 만들 수 있습니다.

자산을 공유하면 검토자가 이를 승인하거나 거부할 수 있습니다. 알림은 다양한 작업 완료와 관련하여 의도한 수신자에게 통보하기 위해 워크플로우의 다양한 단계에서 전송됩니다. 예를 들어, 폴더 또는 컬렉션을 공유하면 검토자는 검토용으로 폴더/컬렉션이 공유되었다는 알림을 받습니다.

검토자가 검토를 완료한 후(자산을 승인하거나 거부함) 검토 완료 알림을 받게 됩니다.

## 폴더에 대한 검토 작업 만들기 {#creating-a-review-task-for-folders}

1. 자산 사용자 인터페이스에서 검토 작업을 만들 폴더를 선택합니다.
1. 도구 모음에서 검토 작업 **[!UICONTROL 만들기]** 아이콘을 탭/클릭하여 **[!UICONTROL 검토 작업]** 페이지를 엽니다. 도구 모음에 아이콘이 표시되지 않으면 **[!UICONTROL 자세히]** 를 탭/클릭한 다음 아이콘을 선택합니다.

   ![chlimage_1-403](assets/chlimage_1-403.png)

1. (선택 사항) **[!UICONTROL 프로젝트]** 목록에서 검토 작업을 연결할 프로젝트를 선택합니다. 기본적으로 없음 **** 옵션이 선택되어 있습니다. 프로젝트를 검토 작업에 연결하지 않으려면 이 선택 사항을 유지합니다.

   >[!NOTE]
   >
   >편집자 수준 이상의 권한이 있는 프로젝트만 프로젝트 **[!UICONTROL 목록에]** 표시됩니다.

1. 검토 작업의 이름을 입력하고 지정 대상 **[!UICONTROL 목록에서 승인자를]** 선택합니다.

   >[!NOTE]
   >
   >선택한 프로젝트의 멤버/그룹은 지정 대상 목록에서 승인자로 **[!UICONTROL 사용할 수]** 있습니다.

1. 검토 작업의 설명, 작업 우선순위 및 기한을 입력합니다.

   ![task_details](assets/task_details.png)

1. 고급 탭에서 URI를 만드는 데 사용할 레이블을 입력합니다.

   ![review_name](assets/review_name.png)

1. 제출을 탭/ **[!UICONTROL 클릭한]**&#x200B;다음 완료를 탭/ **[!UICONTROL 클릭하여]** 확인 메시지를 닫습니다. 새 작업에 대한 알림이 승인자에게 전송됩니다.
1. AEM 자산에 승인자로 로그인하고 자산 UI로 이동합니다. 자산을 승인하려면 **[!UICONTROL 알림]** 아이콘을 클릭/탭한 다음 목록에서 검토 작업을 선택합니다.

   ![알림](assets/notification.png)

1. 작업 **[!UICONTROL 검토]** 페이지에서 검토 작업의 세부 사항을 검토한 다음 검토를 탭/ **[!UICONTROL 클릭합니다]**.
1. [ **[!UICONTROL 검토 작업]** ] 페이지에서 자산을 선택하고 **[!UICONTROL 승인/거부]** 아이콘을 탭/클릭하여 적절히 승인하거나 거부합니다.

   ![review_task](assets/review_task.png)

1. 도구 모음에서 **[!UICONTROL 완료]** 아이콘을 탭/클릭합니다. 대화 상자에서 주석을 입력하고 완료를 탭/ **[!UICONTROL 클릭하여]** 확인합니다.
1. 자산 UI로 이동하고 폴더를 엽니다. 자산에 대한 승인 상태 아이콘은 카드 보기 및 목록 보기 모두에 나타납니다.

   **카드 보기**

   ![chlimage_1-404](assets/chlimage_1-404.png)

   **목록 보기**

   ![review_status_listview](assets/review_status_listview.png)

## 컬렉션에 대한 검토 작업 만들기 {#creating-a-review-task-for-collections}

1. 컬렉션 페이지에서 검토 작업을 만들 컬렉션을 선택합니다.
1. 도구 모음에서 검토 작업 **[!UICONTROL 만들기]** 아이콘을 탭/클릭하여 **[!UICONTROL 검토 작업]** 페이지를 엽니다. 도구 모음에 아이콘이 표시되지 않으면 **[!UICONTROL 자세히]** 를 탭/클릭한 다음 아이콘을 선택합니다.

   ![chlimage_1-405](assets/chlimage_1-405.png)

1. (선택 사항) **[!UICONTROL 프로젝트]** 목록에서 검토 작업을 연결할 프로젝트를 선택합니다. 기본적으로 없음 **** 옵션이 선택되어 있습니다. 프로젝트를 검토 작업에 연결하지 않으려면 이 선택 사항을 유지합니다.

   >[!NOTE]
   >
   >편집자 수준 이상의 권한이 있는 프로젝트만 프로젝트 **[!UICONTROL 목록에]** 표시됩니다.

1. 검토 작업의 이름을 입력하고 지정 대상 **[!UICONTROL 목록에서 승인자를]** 선택합니다.

   >[!NOTE]
   >
   >선택한 프로젝트의 멤버/그룹은 지정 대상 목록에서 승인자로 **[!UICONTROL 사용할 수]** 있습니다.

1. 검토 작업의 설명, 작업 우선순위 및 기한을 입력합니다.

   ![task_details-collection](assets/task_details-collection.png)

1. 제출을 탭/ **[!UICONTROL 클릭한]**&#x200B;다음 완료를 탭/ **[!UICONTROL 클릭하여]** 확인 메시지를 닫습니다. 새 작업에 대한 알림이 승인자에게 전송됩니다.
1. AEM 자산에 승인자로 로그인하고 자산 콘솔로 이동합니다. 자산을 승인하려면 **[!UICONTROL 알림]** 아이콘을 탭/클릭한 다음 목록에서 검토 작업을 선택합니다.
1. 작업 **[!UICONTROL 검토]** 페이지에서 검토 작업의 세부 사항을 검토한 다음 검토를 탭/ **[!UICONTROL 클릭합니다]**.
1. 컬렉션의 모든 에셋이 검토 페이지에 표시됩니다. 자산을 선택하고 승인/ **[!UICONTROL 거부]** 아이콘을 탭/클릭하여 자산을 적절히 승인하거나 거부합니다.

   ![review_task_collection](assets/review_task_collection.png)

1. 도구 모음에서 **[!UICONTROL 완료]** 아이콘을 탭/클릭합니다. 대화 상자에서 주석을 입력하고 완료를 탭/ **[!UICONTROL 클릭하여]** 확인합니다.
1. 컬렉션 콘솔로 이동하고 컬렉션을 엽니다. 자산에 대한 승인 상태 아이콘은 카드 보기 및 목록 보기 모두에 나타납니다.

   **카드 보기**

   ![collection_reviewstatuscardview](assets/collection_reviewstatuscardview.png)

   **목록 보기**

   ![collection_reviewstatuslistview](assets/collection_reviewstatuslistview.png)

