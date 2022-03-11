---
title: 페이지 버전 사용
description: 페이지 버전 생성, 비교 및 복원
exl-id: 33d8e43c-594d-4bba-9631-b2c42a1e910f
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 66%

---

# 페이지 버전 사용 {#working-with-page-versions}

버전 관리를 통해 특정 시점의 페이지 &quot;스냅샷&quot;을 만들 수 있습니다. 버전 관리로 다음과 같은 작업을 수행할 수 있습니다.

* 페이지의 버전을 생성합니다.
* 하나 이상의 이전 버전을 다음 위치로 복원합니다.
   * 페이지 변경 사항을 실행 취소합니다.
   * 삭제된 페이지를 복원합니다.
   * 지정된 날짜 및 시간에 따라 트리를 복원합니다.
* 버전을 미리 봅니다.
* 페이지의 현재 버전을 이전 버전과 비교합니다.
   * 텍스트와 이미지의 차이가 강조 표시됩니다.
* 타임워프는 페이지 버전을 사용하여 게시 환경의 상태를 확인합니다.

## 새 버전 만들기 {#creating-a-new-version}

다음에서 리소스 버전을 만들 수 있습니다.

* [타임라인 레일](#creating-a-new-version-timeline)
* [만들기](#creating-a-new-version-create-with-a-selected-resource) 옵션(리소스를 선택한 경우)

### 새 버전 만들기 - 타임라인 {#creating-a-new-version-timeline}

1. 버전을 만들 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다 .
1. **타임라인** 레일을 엽니다.
1. 주석 필드 옆에 있는 생략 부호를 클릭/탭하여 옵션을 나열합니다.

   ![타임라인 레일의 버전](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. **다른 버전으로 저장**&#x200B;을 선택합니다.
1. 필요한 경우 **레이블** 및 **댓글**&#x200B;을 입력합니다.

   ![버전에 대한 레이블 추가](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. **만들기**&#x200B;로 새 버전을 확인합니다.

   타임라인에 있는 정보가 새 버전을 가리키도록 업데이트됩니다.

### 새 버전 만들기 - 선택한 리소스로 만들기 {#creating-a-new-version-create-with-a-selected-resource}

1. 버전을 만들 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다 .
1. 도구 모음에서 **만들기** 옵션을 선택합니다.
1. 동일한 대화 상자가 열립니다. 필요한 경우 **레이블** 및 **댓글**&#x200B;을 입력할 수 있습니다.
1. **만들기**&#x200B;로 새 버전을 확인합니다.

새 버전을 나타내기 위해 업데이트된 정보가 포함된 타임라인이 열립니다.

## 버전 복원 {#reinstating-versions}

페이지의 버전을 만들면 이전 버전을 활성화하는 다양한 방법이 있습니다.

* a **이 버전으로 되돌리기** 옵션 [타임라인](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) 레일

   선택한 페이지의 이전 버전을 복원합니다.

* a **복원** 맨 위의 옵션 [작업 도구 모음](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)

   * **버전 복원**

      현재 선택한 폴더에 지정된 페이지의 버전을 복원합니다. 또한 이전에 삭제한 페이지 복원을 포함할 수 있습니다.

   * **트리 복원**

      지정된 날짜 및 시간으로 전체 트리 버전을 복원합니다. 여기에는 이전에 삭제한 페이지가 포함될 수 있습니다.

>[!NOTE]
>
>페이지를 복원할 때, 만들어진 버전은 새 분기의 일부가 됩니다.
>
>예시:
>
>1. 페이지의 버전을 임의로 만듭니다.
>1. 초기 레이블 및 버전 노드 이름은 1.0, 1.1, 1.2 등이 됩니다.
>1. 첫 번째 버전을 복원합니다. 예: 1.0
>1. 다시 새 버전을 만듭니다.
>1. 생성된 레이블 및 노드 이름은 이제 1.0.0, 1.0.1, 1.0.2 등이 됩니다.


### 버전으로 되돌리기 {#revert-to-a-version}

종료 **되돌리기** 선택한 페이지를 이전 버전으로 변환:

1. 이전 버전으로 되돌릴 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다 .
1. Open the **Timeline** column and select either **Show All** or **Versions**. The page versions for the selected page will be listed.
1. 되돌아갈 버전을 선택합니다. 가능한 옵션이 표시됩니다.

   ![이 버전으로 되돌리기](/help/sites-cloud/authoring/assets/versions-revert.png)

1. **이 버전으로 되돌리기**&#x200B;를 선택합니다. 선택한 버전이 복원되고 타임라인의 정보가 업데이트됩니다.

### 버전 복원 {#restore-version}

이 방법은 현재 폴더 내에서 지정된 페이지의 버전을 복원하는 데 사용할 수 있습니다. 이전에 삭제한 페이지 복원을 포함할 수도 있습니다.

1. 및 로 이동합니다. [선택](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources): 필수 폴더입니다.

1. 선택 **복원**, 그런 다음 **버전 복원** 맨 위에서 [작업 도구 모음](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar).

   >[!NOTE]
   >
   >다음 중 한 경우에 해당됩니다.
   >* 하위 페이지가 없는 단일 페이지를 선택했습니다.
   >* 또는 폴더의 페이지 중 어느 것도 버전을 가지고 있지 않습니다.

   >
   >해당 버전이 없으므로 표시가 비어 있습니다.

1. 사용 가능한 버전이 나열됩니다.

   ![버전 복원 - 폴더의 모든 페이지 목록](/help/sites-cloud/authoring/assets/versions-restore-version-01.png)

1. 특정 페이지의 경우 아래의 드롭다운 선택기를 사용하십시오 **버전으로 복원** 을 눌러 해당 페이지에 필요한 버전을 선택합니다.

   ![버전 복원 - 버전 선택](/help/sites-cloud/authoring/assets/versions-restore-version-02.png)

1. 기본 디스플레이에서 복원할 필수 페이지를 선택합니다.

   ![버전 복원 - 페이지 선택](/help/sites-cloud/authoring/assets/versions-restore-version-03.png)

1. 선택 **복원** 선택한 버전의 선택한 페이지에 대해 현재 버전으로 복원할 수 있습니다.

>[!NOTE]
>
>필요한 페이지와 관련 버전을 선택하는 순서는 교환이 가능합니다.

### 트리 복원 {#restore-tree}

이 방법은 지정된 날짜 및 시간에 트리 버전을 복원하는 데 사용할 수 있습니다. 여기에는 이전에 삭제한 페이지가 포함될 수 있습니다.

1. 및 로 이동합니다. [선택](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources): 필수 폴더입니다.

1. 선택 **복원**, 그런 다음 **트리 복원** 맨 위에서 [작업 도구 모음](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar). 트리의 최신 버전이 표시됩니다.

   ![트리 복원](/help/sites-cloud/authoring/assets/versions-restore-tree-01.png)

1. 에서 날짜 및 시간 선택기를 사용합니다. **날짜의 최신 버전** 트리의 다른 버전을 선택하려면 복원할 트리입니다.

1. 플래그 설정 **보존된 버전이 없는 페이지** 필요한 경우:

   * 활성(선택) 상태인 경우, 버전이 지정되지 않은 페이지는 그대로 유지되며 복원의 영향을 받지 않습니다.

   * 비활성(선택되지 않음)이면 버전이 지정되지 않은 페이지가 버전이 지정된 트리에 없으므로 제거됩니다.

1. 선택 **복원** 선택한 버전의 트리가 *현재* 버전.

## 버전 미리 보기 {#previewing-a-version}

특정 버전을 미리 볼 수 있습니다.

1. 비교할 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다 .
1. Open the **Timeline** column and select either **Show All** or **Versions**.
1. 페이지 버전이 나열됩니다. 미리 볼 버전을 선택합니다.

   ![버전 미리 보기](/help/sites-cloud/authoring/assets/versions-revert.png)

1. **미리 보기**&#x200B;를 선택합니다. 페이지가 새 탭에 표시됩니다.

   >[!CAUTION]
   >
   >페이지가 이동된 경우 이동 전에 만든 버전에서는 더 이상 미리 보기를 수행할 수 없습니다.
   >
   >미리 보기에 문제가 발생한 경우 페이지에 대한 [타임라인](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)에서 페이지가 이동되었는지 확인합니다.

## 현재 페이지와 버전 비교 {#comparing-a-version-with-current-page}

이전 버전을 현재 페이지와 비교하려면 다음을 수행합니다.

1. 비교할 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다 .
1. 를 엽니다. **타임라인** 열을 선택하고 **모두 표시** 또는 **버전**.
1. 페이지 버전이 나열됩니다. 비교할 버전을 선택합니다.

   ![버전 비교](/help/sites-cloud/authoring/assets/versions-revert.png)

1. **현재와 비교**&#x200B;를 선택합니다. [페이지 차이](/help/sites-cloud/authoring/features/page-diff.md)가 열리고 차이점이 표시됩니다.

## 타임워프 {#timewarp}

타임워프는 과거의 특정 시점에 *게시된* 페이지의 상태를 시뮬레이션하도록 디자인된 기능입니다.

>[!NOTE]
>
>[타임워프는 론치와 함께 사용하여 미래를 미리 볼 수도 있습니다](/help/sites-cloud/authoring/launches/preview.md).

컨텐츠 작성은 지속적인 공동 작업 프로세스이므로 타임워프는 컨텐츠 작성자가 컨텐츠가 변경된 방식을 파악하기 위해 시간에 따라 게시된 웹 사이트를 추적할 수 있도록 하는 데 목적이 있습니다. 이 기능은 페이지 버전을 사용하여 게시 환경의 상태를 확인합니다.

이를 위해 진행되는 작업:

* 시스템은 선택한 시간에 활성화되어 있던 페이지 버전을 찾습니다.
* 즉, 표시되는 버전은 Timewarp에서 선택한 시점 *이전에* 생성/활성화되었음을 의미합니다.
* 삭제된 페이지로 이동하더라도 페이지의 이전 버전이 보관소에서 남아 있어 사용할 수 있는 경우에는 해당 페이지가 렌더링됩니다.
* 게시된 버전을 찾을 수 없으면 타임워프는 작성 환경의 현재 페이지 상태로 돌아갑니다. 그래야만 더 이상 검색할 수 없음을 의미하는 오류/404 페이지가 나타나지 않기 때문입니다.

### 타임워프 사용 {#using-timewarp}

타임워프는 페이지 편집기의 [모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)입니다. 이를 시작하려면 다른 모드처럼 전환하면 됩니다.

1. 타임워프를 시작하려는 페이지 편집기를 시작한 다음 [모드 선택]에서 **타임워프**&#x200B;를 선택합니다.

   ![타임워프 모드](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. In the dialogue set a target date and time and click or tap **Set Date**. If you do not select a time, the current time will default.

   ![타임워프 대상 날짜](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. 이 페이지는 날짜 설정에 따라 표시됩니다. 창 상단에 파란색 상태 표시줄이 표시되면 타임워프 모드입니다. 상태 표시줄의 링크를 사용하여 새 대상 날짜를 선택하거나 타임워프 모드를 종료합니다.

   ![타임워프 모드에서](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### 타임워프 제한 사항 {#timewarp-limitations}

타임워프는 선택한 시점의 페이지를 재현하는 데 최선의 노력을 다합니다. 그러나 AEM에서 컨텐츠를 지속해서 작성하는 과정의 복잡성으로 인해 항상 그럴 수는 없습니다. 타임워프를 사용할 때에는 다음 제한 사항을 염두에 두어야 합니다.

* **타임워프는 게시된 페이지를 기반으로 작동합니다.** 타임워프는 사용자가 페이지를 이전에 게시한 적이 있는 경우에만 제대로 작동합니다. 그렇지 않으면 작성 환경에 현재 페이지가 표시됩니다.
* **타임워프는 페이지 버전을 사용합니다.** 리포지토리에서 제거/삭제된 페이지로 이동하더라도 페이지의 이전 버전이 리포지토리에 남아 있어 사용할 수 있는 경우 해당 페이지가 제대로 렌더링됩니다.
* **제거된 버전은 타임워프에 영향을 줍니다.** 리포지토리에서 버전이 제거되면 타임워프는 올바른 보기를 표시할 수 없습니다.
* **타임워프는 읽기 전용입니다.** 페이지의 이전 버전은 편집할 수 없으며, 볼 수만 있습니다. 이전 버전을 복원하려면 [복원](#revert-to-a-version)을 사용하여 수동으로 복원해야 합니다.
* **타임워프는 페이지 컨텐츠만을 기반으로 합니다.** 웹 사이트를 렌더링하기 위한 요소(예: 코드, css, 자산/이미지 등)가 변경된 경우 리포지토리에서는 해당 항목의 버전이 관리되지 않으므로 보기가 원래와 달라집니다.

>[!CAUTION]
>
>타임워프는 작성자가 컨텐츠를 이해하고 작성하는 데 도움이 되는 도구로 설계되었습니다. 감사 로그나 법적 목적이 아닙니다.
