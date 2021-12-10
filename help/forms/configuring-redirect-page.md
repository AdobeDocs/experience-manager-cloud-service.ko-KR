---
title: 리디렉션 페이지를 구성하는 방법
description: 양식을 만드는 동안 양식 작성자가 구성할 수 있는 웹 페이지로 사용자를 리디렉션하는 방법을 알아봅니다.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: e4dc01d2-7c89-4bd8-af0a-1d2df4676a9a
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# 리디렉션 페이지 구성 {#configuring-redirect-page}

양식 작성자는 양식을 제출한 후 양식 사용자가 리디렉션되는 각 양식에 대해 페이지를 구성할 수 있습니다.

1. 편집 모드에서 구성 요소를 선택한 다음 ![필드 수준](assets/select_parent_icon.svg) > **[!UICONTROL 적응형 양식 컨테이너]**&#x200B;를 클릭한 다음 ![cmppr](assets/configure-icon.svg).

1. 사이드바에서 **[!UICONTROL 제출]**.

1. 아래의 리디렉션 페이지의 URL을 제공합니다 **[!UICONTROL 리디렉션 URL/경로]** 에서 **[!UICONTROL 제출]** 섹션을 참조하십시오.
1. 선택적으로, 제출 작업에서 REST에 제출 끝점 작업에 대해 리디렉션 페이지에 전달될 매개 변수를 구성할 수 있습니다.

   ![페이지 구성 리디렉션](assets/redirect-url.png)

   페이지 구성 리디렉션

양식 작성자는 감사 인사 페이지에 전달되는 다음 매개 변수를 사용할 수 있습니다. 사용 가능한 모든 제출 작업에 대해, `status` 및 `owner` 매개 변수가 전달됩니다. 이 두 매개 변수 외에 다음 제출 작업에 대한 몇 가지 추가 매개 변수가 전달됩니다.

* **[!UICONTROL REST 엔드포인트에 제출]**: 필드-매개 변수 매핑에 추가된 매개 변수가 전달됩니다. `status` 및 `owner` 이 제출 작업에서는 매개 변수가 전달되지 않습니다. 자세한 내용은 [REST 엔드포인트에 제출 작업 구성](configuring-submit-actions.md).
