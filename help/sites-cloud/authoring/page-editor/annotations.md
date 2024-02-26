---
title: 페이지 주석 추가
description: 주석 모드를 사용해 콘텐츠 검토 프로세스를 지원하기 위해 스티커 메모를 사용하듯이 페이지에 주석 및 스케치를 남깁니다.
exl-id: a9cb9745-8140-4795-a5f9-fb3a1a299bd8
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 83%

---

# 페이지 주석 추가 {#adding-page-annotations}

디지털 경험 콘텐츠 만들기를 게시하기 전에 종종 토의와 피드백이 필요할 수 있습니다. 이 피드백 프로세스를 지원하기 위해 AEM에서는 콘텐츠에 주석을 추가할 수 있습니다.

주석은 페이지에 간단한 스케치 또는 메모(실제 스티커 메모와 유사함)를 추가합니다. 주석을 통해 다른 작성자 및 검토자에게 댓글 또는 질문을 남길 수 있습니다.

>[!TIP]
>
>[댓글](/help/sites-cloud/authoring/basic-handling.md#timeline)에서도 페이지에 대한 피드백을 제공할 수 있습니다.

주석을 작성 및 확인하는 데 특수 [모드](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)가 사용됩니다.

>[!TIP]
>
>필요에 따라 주석이 추가, 업데이트 또는 삭제될 때 알림 메시지를 보내는 [워크플로](/help/sites-cloud/authoring/workflows/overview.md)를 개발할 수도 있습니다.

## 주석 표시기 {#annotation-indicator}

주석은 편집 모드에 나타나지는 않지만, 도구 모음 상단 오른쪽에 있는 배지에 현재 페이지에 대해 존재하는 주석의 수가 표시됩니다. 배지는 기본 [주석] 아이콘을 대신하며 주석 모드로/에서 전환하는 빠른 링크로 작동합니다.

![주석 표시기](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## 주석 모드 {#annotate-mode}

주석은 주석 모드에서만 볼 수 있습니다.

1. 페이지 편집 시 도구 모음(오른쪽 상단)의 아이콘을 사용해 주석 모드로 들어갑니다.

   ![주석 버튼](/help/sites-cloud/authoring/assets/annotations.png)

   이제 기존의 모든 주석을 볼 수 있습니다.

   ![주석 예제](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. 주석을 선택하여 주석 대화 상자를 열고 세부 정보를 확인합니다.

   ![주석 세부 정보](/help/sites-cloud/authoring/assets/annotation-adding.png)

1. 주석 모드를 종료하고 이전에 사용한 모드로 돌아가려면 상단 도구 모음 오른쪽에 있는 x 버튼을 선택합니다.

## 주석 추가 및 편집 {#annotating-a-component}

주석 보기 이외에도 주석 모드에서는 콘텐츠의 주석을 만들기, 편집, 이동 또는 삭제할 수 있습니다.

1. 페이지에서 [주석 모드를 시작](#annotate-mode)합니다.

1. 주석 추가를 시작하려면 [주석 추가] 아이콘(도구 모음 왼쪽의 더하기 기호)을 선택합니다.

1. 필요한 구성 요소(파란색 테두리로 강조 표시되어 주석을 추가할 수 있는 구성 요소)를 선택하여 대화 상자를 엽니다.

   ![주석 추가](/help/sites-cloud/authoring/assets/annotation-adding.png)

   이 대화 상자에서는 적절한 필드 및/또는 아이콘을 사용하여 다음 작업을 할 수 있습니다.

   * 주석 텍스트를 입력합니다.
   * 스케치(선과 모양)를 만들어 구성 요소 영역을 강조 표시합니다.

     ![주석 스케치 버튼](/help/sites-cloud/authoring/assets/annotation-sketch.png)

     스케치를 만들 때 커서는 십자 모양으로 바뀝니다. 서로 구분되는 여러 선을 그릴 수 있습니다. 스케치 선은 주석 색상을 반영하며 화살표, 원 또는 타원 중 하나일 수 있습니다.

   * 색상을 선택 또는 변경합니다.

     ![주석 색상 견본 버튼](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

1. 대화 상자 외부를 클릭하거나 탭하면 주석 대화 상자를 닫을 수 있습니다. 스케치와 함께 주석의 잘린 보기가 표시됩니다.

   ![주석 스케치](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. 특정 주석의 편집이 끝나면 다음 작업을 수행할 수 있습니다.

   * 텍스트 표시자를 선택하여 주석을 엽니다. 열면 전체 텍스트를 보고, 변경 내용을 적용하거나 [주석을 삭제](#deleting-annotations)할 수 있습니다.
   * 텍스트 표시자의 위치를 변경합니다.
   * 스케치 선을 선택하여 해당 스케치를 선택하고 원하는 위치로 드래그합니다.
   * 구성 요소 이동 또는 복사
      * 모든 관련 주석과 해당 스케치가 이동 또는 복사되지만 단락을 기준으로 해당 위치는 그대로 유지됩니다.


>[!NOTE]
>
>다른 사용자가 잠근 페이지에는 주석을 추가할 수 없습니다.

>[!NOTE]
>
>개별 구성 요소의 정의에 따라 해당 구성 요소의 인스턴스에 주석을 달 수 있는지 여부가 결정됩니다.

## 주석 및 스케치 삭제 {#deleting-annotations}

주석 및 관련 스케치를 삭제할 수 있습니다.

1. 페이지에서 [주석 모드를 시작](#annotate-mode)합니다.

1. 텍스트 표시자를 선택하여 주석을 엽니다.

1. 삭제 아이콘을 선택합니다.

   ![주석 삭제](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. 주석 및 모든 관련 스케치가 삭제됩니다.

>[!NOTE]
>
>구성 요소를 삭제하면 해당 리소스에 첨부된 모든 주석과 스케치가 페이지에서의 위치와 관계없이 모두 삭제됩니다.

## 스케치만 삭제 {#deleting-sketches}

관련된 모든 스케치가 포함된 전체 주석 대신 특정 스케치만 삭제할 수 있습니다.

1. 페이지에서 [주석 모드를 시작](#annotate-mode)합니다.

1. 스케치를 선택합니다. AEM에서는 진한 파란색 상자로 강조 표시됩니다.

   ![삭제하려는 스케치를 선택합니다.](/help/sites-cloud/authoring/assets/annotation-sketch-delete.png)

1. 키보드에서 Delete 키를 누릅니다.

1. 스케치는 삭제되지만 주석은 유지됩니다.

## 기타 리소스에 주석 달기 {#annotating-other-resources}

구성 요소 외에도 다양한 리소스에 주석을 달 수 있습니다.

* 자산에 주석 달기 [자산에 주석 달기](/help/assets/manage-digital-assets.md#annotating)
* 비디오 자산에 주석 달기 [비디오 자산에 주석 달기](/help/assets/manage-video-assets.md#annotate-video-assets)
