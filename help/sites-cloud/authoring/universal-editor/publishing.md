---
title: 범용 편집기로 콘텐츠 게시
description: 범용 편집기가 콘텐츠를 게시하는 방식과 앱이 게시된 콘텐츠를 처리하는 방법에 대해 살펴보세요.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: c0714a7b74cd223ad4a405934c89a3146fb8b5c4
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 33%

---


# 범용 편집기로 콘텐츠 게시 {#publishing}

범용 편집기가 콘텐츠를 게시하는 방식과 앱이 게시된 콘텐츠를 처리하는 방법에 대해 살펴보세요.

>[!TIP]
>
>여기에 설명된 게시 프로세스는 범용 편집기의 표준 기본 기능입니다.
>
>또한 유니버설 편집기는 게시 프로세스를 지원할 수 있는 워크플로우를 위해 [확장 및 UI 확장성](/help/implementing/universal-editor/extending.md)을 지원하므로 게시 플로우가 달라질 수 있습니다.

## 범용 편집기에서 컨텐츠 게시 {#publishing-content}

콘텐츠 작성자는 콘텐츠를 게시할 준비가 되면 범용 편집기의 도구 모음에서 **게시** 아이콘을 탭하거나 클릭하면 됩니다.

![페이지 게시](assets/publish-menu.png)

1. 유니버설 편집기에서 [유니버설 편집기의 도구 모음에서 **게시** 아이콘을 탭하거나 클릭합니다.](/help/sites-cloud/authoring/universal-editor/navigation.md#publish)
1. [미리 보기 서비스](/help/sites-cloud/authoring/sites-console/previewing-content.md)를 사용할 수 있는 경우 콘텐츠를 게시하는 위치를 **[미리 보기](/help/sites-cloud/authoring/sites-console/previewing-content.md)**(사용 가능한 경우) 또는 **게시**&#x200B;로 선택할 수 있습니다.
1. **항목** 섹션에는 게시에 포함된 콘텐츠가 나열됩니다. 다음을 포함한 세부 정보를 표시하려면 **보기**&#x200B;를 탭하거나 클릭합니다.
   * 아직 게시되지 않은 **새**&#x200B;개 항목.
   * 게시되었지만 마지막 게시 이후에 수정된 **수정됨** 콘텐츠.
   * 게시 이후 수정되지 않고 게시된 **게시** 콘텐츠입니다.

   해당 항목 옆의 확인란을 탭하거나 클릭하여 필요에 따라 게시에서 해당 항목을 포함/제외합니다. **확장**&#x200B;을 탭하거나 클릭하여 세 가지 범주의 합계에 포함된 개별 항목을 보고 개별적으로 항목을 입력/제외할 수 있습니다.

   ![항목 게시](assets/publish-items.png)

   개요로 돌아가려면 **항목** 제목 옆에 있는 뒤로 화살표를 탭하거나 클릭합니다.

1. 게시하려면 **게시**, 중단하려면 **취소**&#x200B;를 탭하거나 클릭합니다.

>[!NOTE]
>
>미리 보기 [에 게시하는 옵션을 사용하지 않도록 설정](/help/implementing/universal-editor/customizing.md#publish-preview)할 수 있으므로 편집기에 나타나지 않을 수 있습니다.

## 유니버설 편집기에서 콘텐츠 게시 취소 {#unpublishing-content}

콘텐츠 게시 취소는 콘텐츠 게시와 유사한 방식으로 작동합니다. 콘텐츠 작성자가 게시에서 콘텐츠를 제거할 준비가 되면 범용 편집기의 도구 모음에서 줄임표 아이콘을 탭하거나 클릭한 다음 **게시 취소**&#x200B;를 탭하거나 클릭합니다.

[콘텐츠를 게시할 때와 동일한 방법으로 콘텐츠 게시를 취소할 수 있습니다.미리 보기 인스턴스에서 게시 취소(사용 가능한 경우) 및 게시 취소에 포함할 항목을 포함하는 ](#publishing-content).

## 사이트 콘솔에서 게시 및 게시 취소 {#publishing-sites-console}

Sites 콘솔에서 [을(를) 게시](/help/sites-cloud/authoring/sites-console/publishing-pages.md)할 수도 있습니다. 이 기능은 여러 페이지의 콘텐츠를 게시하거나 게시 또는 게시 취소를 예약하려는 경우에 유용합니다.

## 추가 리소스 {#additional-resources}

유니버설 편집기로 콘텐츠를 작성하는 방법에 대해 알아보려면 이 문서 를 참조하십시오.

* [범용 편집기로 콘텐츠 작성](authoring.md) - 콘텐츠 작성자가 범용 편집기를 사용하여 콘텐츠를 만드는 것이 얼마나 쉽고 직관적인지 알아봅니다.

범용 편집기의 기술적 세부 사항에 대해 자세히 알아보려면 이 개발자 문서를 참조하십시오.

* [범용 편집기 소개](/help/implementing/universal-editor/introduction.md) - 범용 편집기를 통해 모든 구현에서 콘텐츠의 모든 측면을 편집하여 뛰어난 경험을 제공하고, 콘텐츠 속도를 높이고, 최신 개발자 경험을 제공하는 방법에 대해 알아봅니다.
* [AEM에서 범용 편집기 시작하기](/help/implementing/universal-editor/getting-started.md) - 범용 편집기에 액세스하는 방법과 이를 사용하기 위해 첫 번째 AEM 앱 계측을 시작하는 방법을 알아봅니다.
* [범용 편집기 아키텍처](/help/implementing/universal-editor/architecture.md) - 범용 편집기의 아키텍처 및 해당 서비스와 계층 간에 데이터가 흐르는 방식에 대해 알아봅니다.
* [속성 및 유형](/help/implementing/universal-editor/attributes-types.md) - 범용 편집기에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
* [범용 편집기 인증](/help/implementing/universal-editor/authentication.md) - 범용 편집기의 인증 방법에 대해 알아봅니다.
