---
title: 페이지 생성 및 구성
description: AEM으로 페이지를 만들고 관리하여 웹 사이트를 구성하는 방법에 대해 알아봅니다.
exl-id: c57096ca-34fe-4b19-98e0-8f3cd43cf24e
source-git-commit: 53d4e22805774c0b994ee2bba429c19506639014
workflow-type: tm+mt
source-wordcount: '2543'
ht-degree: 100%

---


# 페이지 생성 및 구성 {#creating-and-organizing-pages}

이 문서에서는 해당 페이지에 [콘텐츠를 만들 수](/help/sites-cloud/authoring/fundamentals/editing-content.md) 있도록 Adobe Experience Manager Cloud Service로 페이지를 만들고 관리하는 방법을 설명합니다.

>[!NOTE]
>
>생성, 복사, 이동, 편집, 삭제와 같은 작업을 페이지에서 수행하기 위해서는 계정에 적절한 액세스 권한과 사용 권한이 있어야 합니다.
>
>문제가 발생하면 시스템 관리자에게 문의하십시오.

<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to take action on pages such as create, copy, move, edit, and delete.
-->

>[!TIP]
>
>페이지를 보다 효율적으로 구성할 수 있도록 해 주고 웹 사이트 콘솔에서 사용할 수 있는 다양한 [키보드 단축키](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)가 있습니다.

{{edge-delivery-authoring}}

## 웹 사이트 구성 {#organizing-your-website}

작성자는 AEM 내에서 웹 사이트를 구성해야 합니다. 이 작업에는 콘텐츠 페이지 생성이 포함되며 이 페이지에 대한 이름 지정 작업도 포함되어 있어서

* 작성자가 작성 환경에서 페이지를 쉽게 찾을 수 있습니다.
* 사이트 방문자가 게시 환경에서 페이지를 쉽게 찾을 수 있습니다.

콘텐츠 구성에 도움이 되도록 [폴더](#creating-a-new-folder)를 사용할 수도 있습니다.

웹 사이트의 구조는 콘텐츠 페이지를 담는 트리로 생각할 수 있습니다. 이 콘텐츠 페이지의 이름은 URL을 구성하는 데 사용됩니다. 반면에 제목은 페이지 콘텐츠가 표시될 때 표시됩니다.

다음은 [WKND 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) 사이트에서 스케이트보드장(`la-skateparks`)에 대한 문서에 액세스하는 예를 보여 줍니다.

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

```xml
 /content
 /wknd
  /en
   /music
    /...
   /sports
    /la-skateparks
    /five-gyms-la
    /mountain-bike-routes
   /shopping
    /...
   /art
    /...
   /...
```

이 구조가 표시되는 **사이트** 콘솔에서는 [웹 사이트의 페이지를 모두 탐색](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)하고 페이지에서 작업을 수행할 수 있습니다. 새 사이트와 [새 페이지](#creating-a-new-page)를 만들 수도 있습니다.

어떤 지점에서든, 헤더 막대의 이동 경로를 통해 위쪽 분기를 볼 수 있습니다.

![이동 경로를 사용하여 탐색](/help/sites-cloud/authoring/assets/organizing-breadcrumbs.png)

### 페이지 이름 지정 규칙 {#page-naming-conventions}

새 페이지를 만드는 경우 다음과 같은 두 개의 주요 필드가 있습니다.

* **[제목](#title)**:

   * 콘솔에서 사용자에게 표시되고, 편집할 때 페이지 콘텐츠 상단에 표시됩니다.
   * 이 필드는 옵션입니다.

* **[이름](#name)**:

   * URI를 생성하는 데 사용됩니다.
   * 이 필드에 대한 사용자 입력은 옵션입니다. 지정하지 않을 경우 이름이 제목에서 파생됩니다. 자세한 내용은 [페이지 이름 제한 및 모범 사례](#page-name-restrictions-and-best-practices) 섹션을 참조하십시오.

#### 페이지 이름 제한 사항 및 모범 사례 {#page-name-restrictions-and-best-practices}

페이지 **제목** 및 **이름**&#x200B;은 별도로 작성할 수 있지만 관련되어 있습니다.

* 페이지를 생성할 때 **제목** 필드만 필요합니다. 페이지 생성 시 **이름**&#x200B;을 제공하지 않으면 AEM은 제목의 처음 64자에서 이름을 생성합니다(아래에 작성된 유효성 검사 관찰). 짧은 페이지 이름에 대한 모범 사례를 지원하기 위해 처음 64자만 사용됩니다.
* 작성자가 페이지 이름을 수동으로 지정하는 경우 64자 제한이 적용되지 않지만, 페이지 이름 길이에 대한 다른 기술 제한 사항은 적용될 수 있습니다.

>[!TIP]
>
>페이지 이름을 정의할 때 되도록이면 간단하게 지정하되, 함축적이며 기억하기 쉽게 지정하여 독자가 쉽게 이해할 수 있도록 하는 것이 좋습니다. 자세한 내용은 `title` 요소에 대한 [W3C 스타일 가이드](https://www.w3.org/Provider/Style/TITLE.html)를 참조하십시오.
>
>일부 브라우저(예: 이전 버전의 IE)는 특정 길이까지만 URL을 허용하므로 기술적인 이유로 페이지 이름을 짧게 유지하는 경우도 있습니다.

새 페이지를 생성 시 AEM은 AEM 및 JCR에서 지정한 [규칙에 따라 페이지 이름을 확인](/help/implementing/developing/introduction/naming-conventions.md)합니다.

허용되는 최소 문자는 다음과 같습니다.

* `a` ~ `z`
* `A` ~ `Z`
* `0` ~ `9`
* `_`(밑줄)
* `-`(하이픈/빼기)

허용되는 모든 문자에 대한 전체 상세 정보는 [이름 지정 규칙](/help/implementing/developing/introduction/naming-conventions.md)에서 찾을 수 있습니다.

>[!NOTE]
>
>페이지 이름은 150자로 제한됩니다.

#### 제목 {#title}

새 페이지를 만들 때 페이지 **제목**&#x200B;만 제공하면 AEM은 이 문자열에서 페이지 **이름**&#x200B;을 파생하고 AEM 및 JCR에서 지정한 [규칙에 따라 이름을 확인](/help/implementing/developing/introduction/naming-conventions.md)합니다.

**제목** 필드에는 잘못된 문자가 포함될 수 있지만, 파생되는 이름에서는 잘못된 문자가 대체됩니다. 예:

| 제목 | 파생되는 이름 |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;&#42;ç+ | `sc---c-.html` |

#### 이름 {#name}

새 페이지를 만들 때 페이지 **이름**&#x200B;을 제공하면 AEM이 AEM 및 JCR에서 지정한 [규칙에 따라 이름을 확인](/help/implementing/developing/introduction/naming-conventions.md)합니다. **이름** 필드에 잘못된 문자를 제출할 수 없습니다. AEM에서 유효하지 않은 문자를 발견하면 필드가 설명 메시지와 함께 강조 표시됩니다.

![유효하지 않은 페이지 이름을 입력하는 예](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>언어 루트가 아닌 경우 ISO-639-1에 따라 페이지 이름으로 정의된 두 문자 코드를 사용할 수 없습니다.
>
>자세한 내용은 [콘텐츠 번역 준비](/help/sites-cloud/administering/translation/preparation.md)를 참조하십시오.

### 템플릿 {#templates}

AEM에서 템플릿은 페이지의 전문 유형을 지정합니다. 템플릿은 만들어지는 새 페이지의 기초로 사용됩니다.

템플릿은 썸네일 이미지 및 기타 속성을 포함하는 페이지의 구조를 정의합니다. 예를 들어 제품 페이지, 사이트맵 및 연락처 정보에 대한 별도의 템플릿이 있을 수 있습니다. 템플릿은 [구성 요소](#components)로 구성됩니다.

AEM에는 특별히 제공되는 몇 개의 템플릿이 있습니다. 사용 가능한 템플릿은 개별 웹 사이트에 따라 다릅니다. 주요 필드는 다음과 같습니다.

* **제목**
결과 웹 페이지에 표시되는 제목입니다.

* **이름**
페이지 이름을 지정할 때 사용됩니다.

* **템플릿**
새 페이지를 생성하는 데 사용할 수 있는 템플릿 목록입니다.

>[!TIP]
>
>인스턴스에서 구성한 경우 [템플릿 작성자가 템플릿 편집기를 사용하여 템플릿을 만들 수 있습니다](/help/sites-cloud/authoring/features/templates.md).

### 구성 요소 {#components}

구성 요소는 특정 유형의 콘텐츠를 추가할 수 있도록 AEM에서 제공하는 요소입니다. AEM에는 다음과 같이 광범위한 기능을 제공하는 다양하고 특별한 구성 요소가 포함되어 있습니다.

* 텍스트
* 이미지
* 제목
* 회전판
* 기타

페이지를 생성하여 열면 [구성 요소 브라우저](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component)의 [구성 요소를 사용하여 콘텐츠를 추가](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser)할 수 있습니다.

>[!TIP]
>
>[구성 요소 콘솔](/help/sites-cloud/authoring/features/components-console.md)은 인스턴스에 대한 구성 요소 개요를 제공합니다.

## 페이지 관리 {#managing-pages}

### 새 페이지 만들기 {#creating-a-new-page}

모든 페이지가 미리 만들어져 있지 않다면 콘텐츠를 만들기 전에 먼저 페이지를 만들어야 합니다.

1. Sites 콘솔을 엽니다(예: `https://<host>:<port>/sites.html/content`).
1. 새 페이지를 만들 위치로 이동합니다.
1. 도구 모음에서 **만들기**&#x200B;를 사용하여 드롭다운 선택기를 연 다음, 목록에서 **페이지**&#x200B;를 선택합니다.

   ![페이지 만들기](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. 마법사의 첫 번째 단계에서 다음 중 하나를 수행할 수 있습니다.

   * 새 페이지를 만드는 데 사용할 템플릿을 선택한 후 **다음**&#x200B;을 클릭/탭하여 계속 진행합니다.

   * 프로세스를 중단하려면 **취소**&#x200B;를 클릭/탭합니다.

   ![새 페이지에 사용할 템플릿 선택](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. 마법사의 마지막 단계에서 다음 중 하나를 수행할 수 있습니다.

   * 세 탭을 사용하여 새 페이지에 지정할 [페이지 속성](/help/sites-cloud/authoring/fundamentals/page-properties.md)을 입력한 다음, 실제로 페이지를 만들려면 **만들기**&#x200B;를 클릭/탭합니다.

   * 선택한 템플릿으로 돌아가려면 **뒤로**&#x200B;를 사용하십시오.

   주요 필드는 다음과 같습니다.

   * **제목**:

      * 사용자에게 표시되며 필수입니다.

   * **이름**:

      * URI를 생성하는 데 사용됩니다. 지정하지 않을 경우 이름이 제목에서 파생됩니다.
      * 새 페이지를 만들 때 페이지 **이름**&#x200B;을 제공하면 AEM은 AEM 및 JCR에서 지정한 [규칙에 따라 이름을 확인](/help/implementing/developing/introduction/naming-conventions.md)합니다.
      * **이름** 필드에 **잘못된 문자를 제출**&#x200B;할 수 없습니다. AEM에서 잘못된 문자를 감지하면 필드가 강조 표시되고, 제거/교체가 필요한 문자를 나타내는 설명 메시지가 표시됩니다.

   >[!TIP]
   >
   >[페이지 이름 지정 규칙](#page-naming-conventions)을 참조하십시오.

   새 페이지를 만드는 데 필요한 최소 정보는 **제목**&#x200B;입니다.

   ![페이지 제목 입력](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. **만들기**&#x200B;를 클릭하여 프로세스를 완료하고 새 페이지를 만듭니다. 확인 대화 상자에 페이지를 즉시 **열지** 또는 콘솔로 돌아갈지(**완료**) 여부를 묻는 메시지가 표시됩니다.

   ![페이지 작성 성공](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   >[!NOTE]
   >
   >해당 위치에 이미 존재하는 이름을 사용하여 페이지를 만들 경우, 번호가 추가되어 변형된 이름이 자동으로 생성됩니다. 예를 들어 `beach`가 이미 존재하는 경우, 새 페이지는 `beach1`이 됩니다.

1. 콘솔로 돌아오면 새 페이지가 보입니다.

   ![결과 새 페이지](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!CAUTION]
>
>페이지가 만들어지면 해당 템플릿을 변경할 수 없습니다. 대신 [새 템플릿으로 론치를 만들 수는 있지만](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template) 그렇게 되면 존재하는 콘텐츠는 모두 잃게 됩니다.

### 편집할 페이지 열기 {#opening-a-page-for-editing}

페이지를 만들거나 기존 페이지로 이동한 후(콘솔에서), 열어서 편집할 수 있습니다.

1. **Sites** 콘솔을 엽니다.
1. 편집할 페이지가 표시될 때까지 탐색합니다.
1. 다음 중 하나를 사용하여 페이지를 선택합니다.

   * [빠른 작업](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) 및 도구 모음

   그런 다음 **편집** 아이콘을 선택하십시오.

   ![편집 버튼](/help/sites-cloud/authoring/assets/edit.png)

1. 페이지가 열리고, 원하는 대로 [페이지를 편집](/help/sites-cloud/authoring/fundamentals/editing-content.md)할 수 있습니다.

>[!NOTE]
>
>링크가 편집 모드에서 활성 상태가 아니므로 페이지 편집기에서 다른 페이지로 이동하는 것은 미리보기 모드에서만 가능합니다.

### 페이지 복사 및 붙여넣기 {#copying-and-pasting-a-page}

페이지 및 모든 하위 페이지를 새 위치에 복사할 수 있습니다.

1. **Sites** 콘솔에서 복사할 페이지가 표시될 때까지 탐색합니다.
1. 다음 중 하나를 사용하여 페이지를 선택합니다.

   * [빠른 작업](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) 및 도구 모음

   그런 다음 페이지 **복사** 아이콘을 선택합니다.

   ![복사](/help/sites-cloud/authoring/assets/copy.png)

1. 페이지의 새 사본을 위한 위치로 이동합니다.
1. 표시되는 **붙여넣기** 아이콘을 탭하거나 클릭합니다.

   ![붙여넣기](/help/sites-cloud/authoring/assets/paste.png)

1. 붙여넣기 대화 상자에 붙여넣기 트랜잭션 및 다음과 같은 기능에 대한 요약이 표시됩니다.
   * **새 사이트 이름:** 붙여넣은 페이지의 이름 바꾸기
   * **하위 항목을 포함하지 않고 붙여넣기:** 붙여넣을 때 선택한 페이지의 하위 페이지 생략(기본값: 하위 페이지도 붙여짐)

   ![붙여넣기 대화 상자](/help/sites-cloud/authoring/assets/paste-dialog.png)

1. **붙여넣기** 버튼을 탭하거나 클릭하여 붙여넣기 트랜잭션을 확인하고 새 페이지를 만듭니다.

>[!NOTE]
>
>페이지를 원본과 동일한 이름의 페이지가 이미 있는 위치에 복사하는 경우 숫자가 추가되어 변형된 이름이 자동으로 생성됩니다. 예를 들어 `beach`가 이미 존재하는 경우, `beach`를 사용하는 새 페이지는 `beach1`이 됩니다.

>[!NOTE]
>
>선택 모드에서 붙여넣기 작업을 시작하면 페이지가 복사되는 즉시 자동으로 종료됩니다.

### 페이지 이동 또는 이름 바꾸기 {#moving-or-renaming-a-page}

페이지 이동 절차와 이름 바꾸기 절차는 기본적으로 동일하며 두 작업은 모두 페이지 이동 마법사에 의해 처리됩니다. 이 마법사를 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 페이지를 이동하지 않고 이름을 변경합니다
* 이름을 변경하지 않고 페이지를 이동합니다
* 동시에 이동하여 이름을 변경합니다

AEM에서는 이름을 바꾸거나 이동하는 페이지를 참조하는 모든 내부 링크를 업데이트하는 기능을 제공합니다. 페이지별로 다른 기준을 적용할 수 있으므로 완벽한 유연성이 발휘됩니다.

1. 이동할 페이지가 표시될 때까지 탐색합니다.
1. 다음 중 하나를 사용하여 페이지를 선택합니다.

   * [빠른 작업](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources) 및 도구 모음

   그런 다음 페이지 **이동** 아이콘을 선택합니다.

   ![이동 버튼](/help/sites-cloud/authoring/assets/move.png)

   이렇게 하면 페이지 이동 마법사가 열립니다.

1. 마법사의 **이름 바꾸기** 단계에서 다음 중 하나를 수행할 수 있습니다.

   * 페이지가 이동되면 사용할 페이지의 이름을 지정한 후 **다음**&#x200B;을 클릭/탭하여 다음 단계로 진행합니다.
   * 프로세스를 중단하려면 **취소**&#x200B;를 클릭/탭합니다.

   ![페이지 이동 및 이름 바꾸기](/help/sites-cloud/authoring/assets/move-page-rename.png)

   페이지를 이동하는 경우에만 페이지 이름이 동일하게 유지될 수 있습니다.

   >[!NOTE]
   >
   >페이지를 동일한 이름의 페이지가 이미 있는 위치로 이동하는 경우 숫자가 추가되어 변형된 이름이 자동으로 생성됩니다. 예를 들어 `beach`가 이미 존재하는 경우, `beach`를 사용하는 새 페이지는 `beach1`이 됩니다.

1. 마법사의 **대상 선택** 단계에서 다음 중 하나를 수행할 수 있습니다.

   * [열 보기](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view)를 사용하여 페이지의 새 위치를 탐색할 수 있습니다.

      * 대상의 썸네일을 클릭하여 대상을 선택합니다.
      * 계속하려면 **다음**&#x200B;을 클릭하십시오.

   * **뒤로**&#x200B;를 사용하여 페이지 이름 지정으로 돌아갑니다.

   >[!NOTE]
   >
   >기본적으로 이동/이름을 바꾼 페이지의 상위 페이지는 대상으로 선택됩니다.

   ![페이지 이동 대상 선택](/help/sites-cloud/authoring/assets/move-page-destination.png)

   >[!NOTE]
   >
   >페이지를 동일한 이름의 페이지가 이미 있는 위치로 이동하는 경우 숫자가 추가되어 변형된 이름이 자동으로 생성됩니다. 예를 들어 `winter`가 이미 존재하는 경우, `winter`는 `winter1`이 됩니다.

1. 페이지가 연결되거나 참조된 경우 또는 게시된 경우, 세부 사항이 **조정/다시 게시** 단계에서 나열됩니다.

   조정 및/또는 다시 게시해야 하는 사항을 적절히 표시할 수 있습니다.

   >[!NOTE]
   >
   >페이지가 연결 또는 참조되지 않은 경우 이 단계를 사용할 수 없습니다.

   ![이동 시 페이지 다시 게시](/help/sites-cloud/authoring/assets/move-page-republish.png)

1. **이동**&#x200B;을 선택하면 프로세스가 완료되고 페이지가 적절하게 이동되거나 페이지 이름이 변경됩니다.

>[!NOTE]
>
>페이지가 이미 게시된 경우, 페이지를 이동하면 자동으로 게시가 취소됩니다. 기본적으로 이동이 완료되면 다시 게시되지만, **조정/다시 게시** 단계에서 **다시 게시** 필드를 선택 해제하여 변경할 수 있습니다.

>[!NOTE]
>
>페이지가 어떤 식으로든 참조되지 않는 경우, **조정/다시 게시** 단계는 무시됩니다.

>[!NOTE]
>
>페이지 이름 바꾸기는 새 페이지 이름을 지정할 때의 [페이지 이름 지정 규칙](#page-naming-conventions)을 따릅니다.

>[!NOTE]
>
>페이지는 페이지가 기반으로 하는 템플릿이 허용되는 위치로만 이동할 수 있습니다. 자세한 내용은 [템플릿 가용성](/help/implementing/developing/components/templates.md#template-availability)을 참조하십시오.

#### 비동기 작업 {#asynchronous-actions}

일반적으로 페이지 이동 또는 이름 바꾸기 작업은 즉시 수행됩니다. 이 작업은 동기 처리로 간주되며 작업이 완료될 때까지 UI의 추가 작업이 차단됩니다.

그러나 영향을 받은 페이지 수가 정의된 제한을 초과하는 경우, 작업은 비동기적으로 처리되므로 페이지 이동 또는 이름 바꾸기 작업에 의해 방해받지 않고 사용자가 UI에서 계속 작성할 수 있습니다.

* 위의 마지막 단계에서 **이동**&#x200B;을 클릭하면 AEM이 구성된 제한을 확인합니다.
* 영향을 받는 페이지 수가 제한보다 적은 경우 동기 작업을 수행합니다.
* 영향을 받는 페이지 수가 제한보다 많은 경우 비동기 작업을 수행합니다.
   * 사용자는 비동기 작업을 수행할 시점을 정의해야 합니다
      * **이제** 비동기 작업의 실행을 즉시 시작합니다.
      * **나중에** 사용자는 비동기 작업이 시작될 시기를 정의할 수 있습니다.

        ![비동기 페이지 이동](/help/sites-cloud/authoring/assets/asynchronous-page-move.png)

비동기 작업의 상태는 **전역 탐색** -> **도구** -> **작업** -> **작업**&#x200B;의 [**비동기 작업 상태** 대시보드](/help/operations/asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations)에서 확인할 수 있습니다.

>[!NOTE]
>
>비동기 작업 처리와 페이지 이동/이름 바꾸기 작업에 대한 제한을 구성하는 방법에 대한 자세한 내용은 작업 사용 안내서에서 [비동기 작업](/help/operations/asynchronous-jobs.md) 문서를 참조하십시오.

### 페이지 삭제 {#deleting-a-page}

1. 삭제할 페이지가 표시될 때까지 탐색합니다.
1. [선택 모드](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)를 사용하여 필요한 페이지를 선택한 다음, 도구 모음에서&#x200B;**삭제**&#x200B;를 사용합니다.

   ![삭제 버튼](/help/sites-cloud/authoring/assets/delete.png)

   >[!NOTE]
   >
   >보안 규정에 따라, **삭제** 페이지 아이콘은 빠른 작업으로 사용할 수 없습니다.

1. 확인을 묻는 대화 상자가 표시됩니다.

   ![대화 상자 삭제](/help/sites-cloud/authoring/assets/delete-page.png)

   * **삭제하기 전에 페이지를 보관하시겠습니까?** - 이 확인란을 선택한 경우 삭제하도록 선택한 페이지의 버전이 삭제 시 생성됩니다.
      * [버전은 나중에 복원할 수 있습니다](/help/sites-cloud/authoring/features/page-versions.md).
      * 이전 버전 없이 삭제된 페이지는 복원할 수 없습니다.
   * **취소**&#x200B;를 사용하여 작업을 중단하거나,
   * **삭제**&#x200B;를 사용하여 작업을 확인합니다.

      * 페이지에 참조가 없으면 페이지가 삭제됩니다.
      * 페이지에 참조가 있으면 메시지 상자에 **하나 이상의 페이지가 참조되었다**&#x200B;고 표시됩니다. **강제 삭제**&#x200B;나 **취소**&#x200B;를 선택할 수 있습니다.

>[!NOTE]
>
>페이지가 이미 게시되어 있으면 삭제하기 전에 자동으로 게시 취소됩니다.

### 페이지 잠금 {#locking-a-page}

콘솔에서 또는 개별 페이지를 편집할 때 [페이지 잠금/잠금 해제](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page)할 수 있습니다. 페이지가 잠겨 있는지 여부도 두 위치 모두에 표시됩니다.

![잠금 버튼](/help/sites-cloud/authoring/assets/lock.png)
![잠금 해제 버튼](/help/sites-cloud/authoring/assets/unlock.png)

### 새 폴더 만들기 {#creating-a-new-folder}

파일 및 페이지 구성에 도움이 되도록 폴더를 만들 수 있습니다.

1. **Sites** 콘솔을 열고 필요한 위치로 이동합니다.
1. 옵션 목록을 열려면 도구 모음에서 **만들기**&#x200B;를 선택합니다.
1. 폴더 대화 상자를 열려면 **폴더**&#x200B;를 선택합니다. 여기에서 **이름** 및 **제목**&#x200B;을 입력할 수 있습니다.

   ![폴더 만들기](/help/sites-cloud/authoring/assets/organizing-create-folder.png)

1. 폴더를 만들려면 **만들기**&#x200B;를 선택합니다.

>[!NOTE]
>
>폴더도 새 폴더 이름을 지정할 때 [페이지 이름 지정 규칙](#page-naming-conventions)을 따릅니다.

>[!CAUTION]
>
>* 폴더는 **Sites**&#x200B;나 다른 폴더 아래에서만 직접 만들 수 있습니다. 페이지 아래에서는 만들 수 없습니다.
>* 표준 작업인 이동, 복사, 붙여넣기, 삭제, 게시, 게시 취소 및 보기/편집 속성은 폴더에서 수행할 수 있습니다.
>* Live Copy 내에서는 폴더를 선택할 수 없습니다.
