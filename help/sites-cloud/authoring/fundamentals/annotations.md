---
title: 페이지 주석 추가
description: 컨텐츠와 직접 관련된 많은 구성 요소를 사용하여 주석을 추가할 수 있습니다.
exl-id: a9cb9745-8140-4795-a5f9-fb3a1a299bd8
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 100%

---

# 페이지 주석 추가 {#adding-page-annotations}

웹 사이트의 페이지에 컨텐츠를 추가할 때는 컨텐츠를 실제로 게시하기 전에 논의를 거쳐야 하는 경우가 많습니다. 이 과정을 돕기 위해 컨텐츠와 직접적으로 관련된(예를 들어 레이아웃과는 반대로) 많은 구성 요소는 주석을 추가할 수 있습니다.

주석을 달면 페이지에 색상이 있는 스케치/스티커 메모가 생깁니다. 주석을 사용하는 사용자(또는 다른 사용자)는 다른 작성자/검토자에 대한 댓글 및/또는 질문을 할 수 있습니다.

>[!NOTE]
>
>[댓글](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)에서도 페이지에 대한 피드백을 제공할 수 있습니다.

## 주석 {#annotations}

주석을 작성 및 확인하는 데 특수 [모드](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)가 사용됩니다.

>[!CAUTION]
>
>리소스(예: 구성 요소)를 삭제하면 해당 리소스에 첨부된 주석과 스케치가 페이지에서의 위치와 관계없이 모두 삭제됩니다.

>[!NOTE]
>
>필요에 따라 주석이 추가, 업데이트 또는 삭제될 때 알림 메시지를 보내는 워크플로우를 개발할 수도 있습니다.

### 구성 요소에 주석 추가 {#annotating-a-component}

주석 모드에서는 컨텐츠에 대한 주석을 생성, 편집, 이동 또는 삭제할 수 있습니다.

1. 페이지 편집 시 도구 모음(오른쪽 상단)에 있는 아이콘을 사용하여 주석 모드로 전환할 수 있습니다.

   ![주석 단추](/help/sites-cloud/authoring/assets/annotations.png)

   이제 기존의 모든 주석을 볼 수 있습니다.

   >[!NOTE]
   >
   >주석 모드를 끝내려면 상단 도구 모음 오른쪽에 있는 [주석] 아이콘(x 기호)을 탭하거나 클릭합니다.

1. 주석 추가를 시작하려면 [주석 추가] 아이콘(도구 모음 왼쪽의 더하기 기호)을 클릭하거나 탭합니다.

   >[!NOTE]
   >
   >주석 추가를 중지하고 보기로 돌아가려면 상단 도구 모음 왼쪽에 있는 [취소] 아이콘(흰색 원으로 둘러싸인 x 기호)을 탭하거나 클릭합니다.

1. 필요한 구성 요소(파란색 테두리로 강조 표시되고 주석을 추가할 수 있는 구성 요소)를 클릭/탭하여 주석을 추가하고 대화 상자를 엽니다.

   ![주석 추가](/help/sites-cloud/authoring/assets/annotation-adding.png)

   이 대화 상자에서는 적절한 필드 및/또는 아이콘을 사용하여 다음 작업을 할 수 있습니다.

   * 주석 텍스트 입력
   * 스케치(선과 모양)를 만들어 구성 요소 영역 강조 표시


      ![주석 스케치 단추](/help/sites-cloud/authoring/assets/annotation-sketch.png)

      스케치를 만들 때 커서는 십자 모양으로 바뀝니다. 서로 구분되는 여러 선을 그릴 수 있습니다. 스케치 선은 주석 색상을 반영하며 화살표, 원 또는 타원 중 하나일 수 있습니다.

   * 색상 선택/변경:

      ![주석 색상 견본 단추](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

   * 주석 삭제

      ![주석 삭제 단추](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. 대화 상자의 외부를 클릭/탭하여 주석 대화 상자를 닫을 수 있습니다. 스케치가 있는 잘린 주석 보기(첫 번째 단어)가 표시됩니다.

   ![주석 스케치](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. 특정 주석의 편집이 끝나면 다음 작업을 할 수 있습니다.

   * 텍스트 마커를 클릭/탭하여 주석 열기. 일단 열면 전체 텍스트를 보거나, 변경 작업을 수행하거나, 주석을 삭제할 수 있습니다.

      * 스케치는 주석과 별도로 삭제할 수 없습니다.
   * 텍스트 마커 위치 변경.
   * 스케치 선을 클릭/탭하여 해당 스케치를 선택하고 원하는 위치로 드래그.
   * 구성 요소 이동 또는 복사

      * 모든 관련 주석 및 그 스케치도 이동하거나 복사되며, 단락을 기준으로 해당 위치가 그대로 유지됩니다.


1. 주석 모드를 끝내고 이전에 사용한 모드로 돌아가려면 상단 도구 모음 오른쪽에 있는 [주석] 아이콘(x 기호)을 탭하거나 클릭합니다.

>[!NOTE]
>
>다른 사용자가 잠근 페이지에는 주석을 추가할 수 없습니다.

>[!NOTE]
>
>개별 구성 요소의 정의에 따라 해당 구성 요소의 인스턴스에 주석을 달 수 있는지 여부가 결정됩니다.

## 주석 표시기 {#annotation-indicator}

주석은 편집 모드에 나타나지는 않지만, 도구 모음 상단 오른쪽에 있는 배지에 현재 페이지에 대해 존재하는 주석의 수가 표시됩니다. 배지는 기본 [주석] 아이콘을 대신하며 주석 모드로/에서 전환하는 빠른 링크로 작동합니다.

![주석 표시기](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## 기타 리소스에 주석 달기 {#annotating-other-resources}

구성 요소 외에, 다양한 리소스에 주석을 달 수 있습니다.

* 자산에 주석 달기 [자산에 주석 달기](/help/assets/manage-digital-assets.md#annotating)
* 비디오 자산에 주석 달기 [비디오 자산에 주석 달기](/help/assets/manage-video-assets.md#annotate-video-assets)
