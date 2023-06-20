---
title: 페이지 버전을 사용하여 작업
description: 페이지 버전 만들기, 비교 및 복원
exl-id: 33d8e43c-594d-4bba-9631-b2c42a1e910f
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1512'
ht-degree: 76%

---

# 페이지 버전을 사용하여 작업 {#working-with-page-versions}

버전 관리는 특정 시점에 페이지의 &quot;스냅샷&quot;을 만듭니다. 버전 관리를 사용하여 다음 작업을 수행할 수 있습니다.

* 페이지 버전을 만듭니다.
* 하나 이상의 페이지의 이전 버전을 복원하여 다음과 같은 작업을 수행할 수 있습니다.
   * 페이지에 적용된 변경 내용 실행 취소
   * 삭제된 페이지 복원
   * 지정된 날짜 및 시간의 트리 복원
* 버전 미리보기
* 페이지의 현재 버전과 이전 버전 비교
   * 텍스트 및 이미지의 차이점이 강조 표시됩니다.
* 타임워프는 페이지 버전을 사용하여 게시 환경의 상태를 파악합니다.

## 새 버전 만들기 {#creating-a-new-version}

다음에서 리소스 버전을 만들 수 있습니다.

* [타임라인 레일](#creating-a-new-version-timeline)
* [만들기](#creating-a-new-version-create-with-a-selected-resource) 옵션(리소스를 선택한 경우)

### 새 버전 만들기 - 타임라인 {#creating-a-new-version-timeline}

1. 버전을 만들 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다.
1. **타임라인** 레일을 엽니다.
1. 주석 필드 옆에 있는 생략 부호를 클릭/탭하여 옵션을 나열합니다.

   ![타임라인 레일의 버전](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. 선택 **다른 버전으로 저장**.
1. 입력 **레이블** 및 **댓글** 필요한 경우.

   ![버전에 대한 레이블 추가](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. **만들기**&#x200B;로 새 버전을 확인합니다.

   타임라인에 있는 정보가 새 버전을 가리키도록 업데이트됩니다.

### 새 버전 만들기 - 선택한 리소스로 만들기 {#creating-a-new-version-create-with-a-selected-resource}

1. 버전을 만들 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다.
1. 다음 항목 선택 **만들기** 도구 모음의 옵션입니다.
1. 동일한 대화 상자가 열립니다. 필요한 경우 **레이블** 및 **댓글**&#x200B;을 입력할 수 있습니다.
1. **만들기**&#x200B;로 새 버전을 확인합니다.

새 버전을 나타내기 위해 업데이트된 정보가 포함된 타임라인이 열립니다.

## 버전 복원 {#reinstating-versions}

페이지 버전을 만든 후 다양한 방법을 사용하여 이전 버전을 복원할 수 있습니다.

* [타임라인](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) 레일의 **이 버전으로 되돌리기** 옵션

  선택한 페이지의 이전 버전을 복원합니다.

* 상단 [작업 도구 모음](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)의 **복원** 옵션

   * **버전 복원**

     현재 선택된 폴더 내에 있는 지정된 페이지의 버전을 복원합니다. 이렇게 하면 이전에 삭제된 페이지도 복원할 수 있습니다.

   * **트리 복원**

     지정된 날짜 및 시간의 전체 트리의 버전을 복원합니다. 이렇게 하면 이전에 삭제된 페이지도 복원할 수 있습니다.

>[!NOTE]
>
>페이지를 복원하면 생성된 버전은 새 분기의 일부가 됩니다.
>
>예시:
>
>1. 페이지의 버전을 임의로 만듭니다.
>1. 초기 레이블 및 버전 노드 이름은 1.0, 1.1, 1.2 등입니다.
>1. 첫 번째 버전 1.0을 복원합니다.
>1. 새 버전을 다시 만듭니다.
>1. 이제 생성된 레이블 및 노드 이름은 1.0.0, 1.0.1, 1.0.2 등입니다.

### 버전으로 되돌리기 {#revert-to-a-version}

선택한 페이지를 이전 버전으로 **되돌리려면** 다음 작업을 수행하십시오.

1. 이전 버전으로 되돌릴 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다.
1. **타임라인** 열을 연 다음 **모두 표시** 또는 **버전** 중 하나를 선택합니다. 선택한 페이지의 페이지 버전이 나열됩니다.
1. 되돌아갈 버전을 선택합니다. 가능한 옵션이 표시됩니다.

   ![이 버전으로 되돌리기](/help/sites-cloud/authoring/assets/versions-revert.png)

1. **이 버전으로 되돌리기**&#x200B;를 선택합니다. 선택한 버전이 복원되고 타임라인의 정보가 업데이트됩니다.

### 버전 복원 {#restore-version}

이 방법을 사용하여 현재 폴더 내에 있는 지정된 페이지의 버전을 복원할 수 있습니다. 이렇게 하면 이전에 삭제된 페이지도 복원할 수 있습니다.

1. 필요한 폴더로 이동한 다음 [선택](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)합니다.

1. 상단의 [작업 도구 모음](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)에서 **복원**&#x200B;을 선택한 다음 **버전 복원**&#x200B;을 선택합니다.

   >[!NOTE]
   >
   >다음 중 하나의 경우:
   >* 하위 페이지가 없는 단일 페이지를 선택함
   >* 폴더에 버전이 있는 페이지가 없음
   >
   >해당하는 버전이 없기 때문에 빈 화면이 표시됩니다.

1. 사용 가능한 버전이 나열됩니다.

   ![버전 복원 - 폴더 내 모든 페이지 목록](/help/sites-cloud/authoring/assets/versions-restore-version-01.png)

1. 특정 페이지의 경우 **버전으로 복원**&#x200B;에 있는 드롭다운 선택기를 사용하여 해당 페이지에 필요한 버전을 선택하십시오.

   ![버전 복원 - 버전 선택](/help/sites-cloud/authoring/assets/versions-restore-version-02.png)

1. 메인 화면에서 복원이 필요한 페이지를 선택합니다.

   ![버전 복원 - 페이지 선택](/help/sites-cloud/authoring/assets/versions-restore-version-03.png)

1. 선택한 페이지의 선택한 버전에 대해 **복원**&#x200B;을 선택하여 현재 버전으로 복원합니다.

>[!NOTE]
>
>필요한 페이지 및 관련 버전을 선택하는 순서를 변경할 수 있습니다.

### 트리 복원 {#restore-tree}

이 방법을 사용하여 지정된 날짜 및 시간의 트리 버전을 복원할 수 있습니다. 이렇게 하면 이전에 삭제된 페이지도 복원할 수 있습니다.

1. 필요한 폴더로 이동한 다음 [선택](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)합니다.

1. 상단의 [작업 도구 모음](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar)에서 **복원**&#x200B;을 선택한 다음 **트리 복원**&#x200B;을 선택합니다. 최신 버전의 트리가 표시됩니다.

   ![트리 복원](/help/sites-cloud/authoring/assets/versions-restore-tree-01.png)

1. **지정일의 최신 버전**&#x200B;에서 날짜 및 시간 선택기를 사용하여 복원할 트리의 다른 버전을 선택합니다.

1. 필요에 따라 플래그 **보존된 버전이 없는 페이지**&#x200B;를 설정합니다.

   * 활성화(선택)하면 버전이 없는 페이지가 유지되며 복원의 영향을 받지 않습니다.

   * 비활성화(선택 해제)하면 버전이 없는 페이지는 버전이 있는 트리에 존재하지 않으므로 제거됩니다.

1. 선택한 트리 버전에 대해 **복원**&#x200B;을 선택하여 *현재* 버전으로 복원합니다.

## 버전 미리보기 {#previewing-a-version}

특정 버전을 미리 볼 수 있습니다.

1. 비교할 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다.
1. **타임라인** 열을 연 다음 **모두 표시** 또는 **버전** 중 하나를 선택합니다.
1. 페이지 버전이 나열됩니다. 미리 보려는 버전을 선택합니다.

   ![버전 미리보기](/help/sites-cloud/authoring/assets/versions-revert.png)

1. **미리보기**&#x200B;를 선택합니다. 페이지가 새 탭에 표시됩니다.

   >[!CAUTION]
   >
   >페이지가 이동된 경우 이동 전에 만든 버전에서는 더 이상 미리보기를 수행할 수 없습니다.
   >
   >미리보기에 문제가 발생한 경우 페이지에 대한 [타임라인](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)에서 페이지가 이동되었는지 확인합니다.

## 현재 페이지와 버전 비교 {#comparing-a-version-with-current-page}

이전 버전을 현재 페이지와 비교하려면 다음 작업을 수행합니다.

1. 비교할 페이지로 이동하여 표시합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)로 페이지를 선택합니다.
1. **타임라인** 열을 연 다음 **모두 표시** 또는 **버전** 중 하나를 선택합니다.
1. 페이지 버전이 나열됩니다. 비교할 버전을 선택합니다.

   ![버전 비교](/help/sites-cloud/authoring/assets/versions-revert.png)

1. 선택 **현재 항목에 비교**. 다음 [페이지 비교](/help/sites-cloud/authoring/features/page-diff.md) 을 열고 차이점을 표시합니다.

## 타임워프 {#timewarp}

타임워프는 과거의 특정 시점에 *게시된* 페이지의 상태를 시뮬레이션하도록 설계된 기능입니다.

>[!TIP]
>
>[타임워프를 런치와 함께 사용하여 향후 상태를 미리 볼 수도 있습니다.](/help/sites-cloud/authoring/launches/preview.md)

콘텐츠 작성은 지속적인 공동 작업 프로세스이므로 타임워프는 콘텐츠 작성자가 콘텐츠가 변경된 방식을 이해할 수 있도록 시간에 따라 게시된 웹 사이트를 추적할 수 있도록 하는 데 목적이 있습니다. 이 기능은 페이지 버전을 사용하여 게시 환경의 상태를 확인합니다.

이를 위해 진행되는 작업:

* 시스템은 선택한 시간에 활성화된 페이지 버전을 찾습니다.
* 이는 표시된 버전이 생성/활성화되었음을 의미합니다. *다음 이전* 타임워프에서 선택한 시점입니다.
* 삭제된 페이지로 이동하더라도 페이지의 이전 버전이 보관소에서 남아 있어 사용할 수 있는 경우에는 해당 페이지가 렌더링됩니다.
* 게시된 버전을 찾을 수 없으면 타임워프는 작성 환경의 현재 페이지 상태로 돌아갑니다. 그래야만 더 이상 검색할 수 없음을 의미하는 오류/404 페이지가 나타나지 않기 때문입니다.

### 타임워프 사용 {#using-timewarp}

타임워프는 [모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) 페이지 편집기의 시작하려면 다른 모드와 마찬가지로 전환하면 됩니다.

1. 타임워프를 시작하려는 페이지의 편집기를 시작한 다음 을 선택합니다. **타임워프** 을 선택합니다.

   ![타임워프 모드](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. In the dialogue set a target date and time and click or tap **Set Date**. If you do not select a time, the current time will default.

   ![타임워프 대상 날짜](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. 날짜 설정을 기반으로 페이지가 표시됩니다. 타임워프 모드는 창 상단의 파란색 상태 표시줄을 통해 표시됩니다. 상태 표시줄의 링크를 사용하여 새 대상 날짜를 선택하거나 타임워프 모드를 종료하십시오.

   ![타임워프 모드에서](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### 타임워프 제한 사항 {#timewarp-limitations}

타임워프는 선택한 시점의 페이지를 재현하는 데 최선의 노력을 다합니다. 그러나 AEM에서 콘텐츠를 지속해서 작성하는 과정의 복잡성으로 인해 항상 그럴 수는 없습니다. 타임워프를 사용할 때에는 다음 제한 사항을 염두에 두어야 합니다.

* **타임워프는 게시된 페이지를 기반으로 작동합니다.** 타임워프는 사용자가 페이지를 이전에 게시한 적이 있는 경우에만 제대로 작동합니다. 그렇지 않으면 작성 환경에 현재 페이지가 표시됩니다.
* **타임워프는 페이지 버전을 사용합니다.** 저장소에서 제거/삭제된 페이지로 이동하더라도 페이지의 이전 버전이 저장소에 남아 있어 사용할 수 있는 경우 해당 페이지가 제대로 렌더링됩니다.
* **제거된 버전은 타임워프에 영향을 줍니다.** 저장소에서 버전이 제거되면 타임워프는 올바른 보기를 표시할 수 없습니다.
* **타임워프는 읽기 전용입니다.** 페이지의 이전 버전은 편집할 수 없으며, 볼 수만 있습니다. 이전 버전을 복원하려면 [복원](#revert-to-a-version)을 사용하여 수동으로 복원해야 합니다.
* **타임워프는 페이지 콘텐츠만을 기반으로 합니다.** 웹 사이트를 렌더링하기 위한 요소(예: 코드, css, 에셋/이미지 등)가 변경된 경우 저장소에서는 해당 항목의 버전이 관리되지 않으므로 보기가 원래와 달라집니다.

>[!CAUTION]
>
>타임워프는 작성자가 콘텐츠를 이해하고 작성하는 데 도움이 되는 도구로 설계되었습니다. 감사 로그나 법적 목적이 아닙니다.
