---
title: 리디렉션 페이지를 구성하는 방법
description: 양식을 만드는 동안 양식 작성자가 구성할 수 있는 웹 페이지로 사용자를 리디렉션하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: e4dc01d2-7c89-4bd8-af0a-1d2df4676a9a
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---

# 리디렉션 페이지 구성 {#configuring-redirect-page}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-redirect-page.html) |
| AEM as a Cloud Service | 이 문서 |

양식 작성자는 양식을 제출한 후 양식 사용자가 리디렉션되는 각 양식에 대한 페이지를 구성할 수 있습니다.

1. 편집 모드에서 구성 요소를 선택한 다음 ![필드 수준](assets/select_parent_icon.svg) > **[!UICONTROL 적응형 양식 컨테이너]**&#x200B;를 클릭하고 ![cmpr](assets/configure-icon.svg)을 클릭합니다.

1. 사이드바에서 **[!UICONTROL 제출]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 제출]** 섹션의 **[!UICONTROL 리디렉션 URL/경로]** 아래에 리디렉션 페이지의 URL을 제공하십시오.
1. 선택 사항으로, 제출 작업에서 REST에 제출 엔드포인트 작업의 경우 리디렉션 페이지에 전달할 매개 변수를 구성할 수 있습니다.

   ![페이지 구성 리디렉션](assets/redirect-url.png)

   페이지 구성 리디렉션

양식 작성자는 감사 인사 페이지에 전달되는 다음 매개 변수를 사용할 수 있습니다. 사용 가능한 모든 제출 액션에 대해 `status` 및 `owner` 매개 변수가 전달됩니다. 이 두 매개 변수 외에도 다음 제출 액션에 대해 몇 가지 추가 매개 변수가 전달됩니다.

* **[!UICONTROL REST 끝점에 제출]**: 필드 대 매개 변수 매핑에 대해 추가된 매개 변수가 전달됩니다. 이 제출 액션에서 `status` 및 `owner` 매개 변수가 전달되지 않습니다. 자세한 내용은 [REST 끝점에 제출 동작 구성](configuring-submit-actions.md)을 참조하십시오.

>[!MORELIKETHIS]
>
>* [리디렉션 페이지 또는 감사 메시지 구성](/help/forms/configure-redirect-page-or-thank-you-message.md)
