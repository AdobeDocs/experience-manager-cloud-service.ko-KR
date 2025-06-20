---
title: 페이지 편집기로 콘텐츠 게시
description: 페이지 편집기에서 콘텐츠를 게시하는 방법에 대해 알아봅니다.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 5871e04d3bd78bdd8df55d42e7619c98ea3f38ca
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 50%

---


# 사이트 편집기를 사용하여 콘텐츠 게시 {#publishing}

페이지 편집기에서 콘텐츠를 게시하는 방법에 대해 알아봅니다.

## 페이지 편집기에서 게시 {#publishing-from-the-page-editor}

[페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)에서 페이지를 편집하는 경우 편집기에서 직접 게시할 수 있습니다.

1. **페이지 정보** 아이콘을 선택하여 메뉴를 열고 **페이지 게시** 옵션을 엽니다.

   ![페이지 옵션을 통해 페이지 게시](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. 페이지에 게시해야 하는 참조가 있는지에 따라 다음과 같이 달라집니다.

   * 게시할 참조가 없으면 페이지가 직접 게시됩니다.
   * 페이지에 게시해야 하는 참조가 있을 경우, **게시 마법사**&#x200B;에 나열되며 여기서 다음과 같은 작업을 수행할 수 있습니다.
      * 페이지와 함께 게시할 자산, 태그 등을 지정한 다음 **게시**&#x200B;를 사용하여 프로세스를 완료합니다.
      * **취소**&#x200B;를 사용하여 작업을 중단합니다.

   ![페이지를 사용하여 참조 게시](/help/sites-cloud/authoring/assets/publishing-references.png)

1. **게시**&#x200B;를 선택하면 페이지가 게시 환경에 복제됩니다. 페이지 편집기에 게시 작업을 확인하는 정보 배너가 표시됩니다.

   ![게시 상태 정보 배너](/help/sites-cloud/authoring/assets/publishing-info.png)

   콘솔에서 동일한 페이지를 볼 때 업데이트된 게시 상태가 표시됩니다.

   ![Sites 콘솔 열 보기의 페이지 게시 상태](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>페이지 편집기에서 게시하면 약식 게시가 됩니다. 즉, 선택한 페이지만 게시되고 하위 페이지는 게시되지 않습니다.

>[!NOTE]
>
>편집기의 [별칭](/help/sites-cloud/authoring/sites-console/page-properties.md#advanced)을 통해 액세스하는 페이지는 게시할 수 없습니다. 편집기의 [게시] 옵션은 실제 경로를 통해 액세스하는 페이지에 대해서만 사용할 수 있습니다.

## 페이지 편집기에서 게시 취소 {#unpublishing}

페이지 편집기를 사용하여 페이지를 편집할 때 해당 페이지의 게시를 취소하려면 [페이지를 게시](#publishing-from-the-editor)하는 것과 마찬가지로 **페이지 정보** 메뉴에서 **페이지 게시 취소**&#x200B;를 선택합니다.

>[!NOTE]
>
>편집기의 [별칭](/help/sites-cloud/authoring/sites-console/page-properties.md#advanced)을 통해 액세스하는 페이지는 게시를 취소할 수 없습니다. 편집기의 [게시] 옵션은 실제 경로를 통해 액세스하는 페이지에 대해서만 사용할 수 있습니다.

## 사이트 콘솔에서 게시 및 게시 취소 {#publishing-sites-console}

Sites 콘솔에서 [을(를) 게시](/help/sites-cloud/authoring/sites-console/publishing-pages.md)할 수도 있습니다. 이 기능은 여러 페이지의 콘텐츠를 게시하거나 게시 또는 게시 취소를 예약하려는 경우에 유용합니다.
