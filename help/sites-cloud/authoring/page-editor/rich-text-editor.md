---
title: ' [!DNL Adobe Experience Manager] 에서 리치 텍스트 편집기를 사용하여 콘텐츠를 작성합니다.'
description: ' [!DNL Experience Manager] 리치 텍스트 편집기를 사용하여 콘텐츠를 작성합니다.'
exl-id: 15c175f8-11de-4475-87a9-920219a4c004
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 95%

---

# 리치 텍스트 편집기를 사용하여 콘텐츠를 작성합니다. {#use-rich-text-editor-to-author-content}

리치 텍스트 편집기(RTE)는 텍스트 콘텐츠를 [!DNL Adobe Experience Manager]에 추가할 수 있는 기본 빌딩 블록입니다. 또한 작성을 허용하는 다른 많은 구성 요소는 RTE를 기반으로 합니다. Experience Manager 개발자는 RTE를 사용자 정의하고 관리자는 작성자가 사용하도록 RTE를 구성할 수 있습니다.

## 바로 편집 {#in-place-editing}

한 번의 클릭으로 텍스트 기반 구성 요소를 선택하여 [구성 요소 도구 모음을 표시합니다.](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser)

![구성 요소 도구 모음](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

다시 클릭하거나 처음에 구성 요소를 선택하고 느리게 더블 클릭하면 즉석 편집이 열립니다. 편집 모드에는 도구 모음이 포함되어 있습니다. 콘텐츠를 편집하고 기본적인 서식 변경을 수행할 수 있습니다.

![RTE를 사용하여 즉석 편집](/help/sites-cloud/authoring/assets/rte-in-place-editing.png)

일반적으로 도구 모음은 다음과 같은 옵션을 제공합니다.

* **서식**: 텍스트를 굵게 또는 기울임체로 강조하거나 텍스트에 밑줄을 긋습니다.
* **목록**: 글머리 기호 또는 번호 매기기 목록을 만들고 들여쓰기를 설정합니다.
* **하이퍼링크**: 링크를 만듭니다.
* **연결 해제**: 하이퍼링크를 제거합니다.
* **전체 화면**: 전체 화면 모드로 편집기를 엽니다.
* **닫기**: 편집을 중지합니다.
* **저장**: 변경 사항을 저장합니다.

## 전체 화면 편집 {#full-screen-editing}

텍스트 기반 구성 요소의 경우 ![도구 모음](/help/sites-cloud/authoring/assets/editing-full-screen.png)에서 전체 화면 모드 [RTE 전체 화면 버튼](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser)을 클릭하여 리치 텍스트 편집기를 열고 나머지 페이지 콘텐츠를 숨깁니다.

전체 화면 모드에서는 작성에 사용할 수 있는 구성된 모든 옵션이 표시됩니다. 사용 가능한 옵션은 [구성에 따라 달라집니다](/help/implementing/developing/extending/rich-text-editor.md).

![전체 화면 모드의 RTE](/help/sites-cloud/authoring/assets/rte-full-screen.png)

리치 텍스트 편집기 추가 옵션은 다음과 같습니다.

* **앵커**: 나중에 연결하거나 참조를 생성할 수 있는 텍스트에 앵커를 생성합니다.
* **왼쪽으로 텍스트 정렬**.
* **텍스트를 가운데로**.
* **오른쪽으로 텍스트 정렬**.

최소화를 클릭하여 전체 화면 모드를 닫습니다.

>[!TIP]
>
>중첩된 목록을 [!DNL Microsoft Word]에서 RTE로 복사하면 일관되지 않은 결과를 얻을 수 있습니다. 대신 텍스트로 붙여넣고 수동 조정을 수행합니다.

>[!MORELIKETHIS]
>
>* [리치 텍스트 편집기 구성](/help/implementing/developing/extending/rich-text-editor.md)
