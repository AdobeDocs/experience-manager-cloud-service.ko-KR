---
title: 페이지 구성
description: AEM을 사용하여 웹 사이트를 구성하는 방법에 대해 알아봅니다.
exl-id: c57096ca-34fe-4b19-98e0-8f3cd43cf24e
source-git-commit: 1a4c5e618adaef99d82a00e1118d1a0f8536fc14
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 67%

---


# 페이지 구성 {#creating-and-organizing-pages}

AEM을 사용하여 웹 사이트를 구성하는 방법에 대해 알아봅니다. 페이지를 구성하는 방법을 이해하면 다음과 같은 작업을 수행할 수 있습니다 [새 페이지 만들기](/help/sites-cloud/authoring/sites-console/creating-pages.md) 및 [기존 페이지를 관리합니다.](/help/sites-cloud/authoring/sites-console/managing-pages.md)

{{edge-delivery-authoring}}

## 사이트 구성 {#organizing-your-site}

작성자는 AEM 내에서 사이트를 구성해야 합니다. 이 작업에는 콘텐츠 페이지 생성이 포함되며 이 페이지에 대한 이름 지정 작업도 포함되어 있어서

* 작성자가 작성 환경에서 페이지를 쉽게 찾을 수 있습니다.
* 사이트 방문자가 게시 환경에서 페이지를 쉽게 찾을 수 있습니다.

콘텐츠 구성에 도움이 되도록 [폴더](#creating-a-new-folder)를 사용할 수도 있습니다.

웹 사이트의 구조는 콘텐츠 페이지를 담는 트리로 생각할 수 있습니다. 이 콘텐츠 페이지의 이름은 URL을 구성하는 데 사용됩니다. 반면에 제목은 페이지 콘텐츠가 표시될 때 표시됩니다.

다음은 의 예입니다. [WKND 자습서](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) 사이트, 스케이트보드장에 대한 기사(`la-skateparks`)에 액세스할 수 있습니다.

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

이 구조는 다음에서 볼 수 있습니다. [**사이트** 콘솔,](/help/sites-cloud/authoring/sites-console/introduction.md) 웹 사이트의 페이지를 탐색하고 페이지에서 작업을 수행할 수 있는 위치.

## 페이지 이름 지정 규칙 {#page-naming-conventions}

페이지를 만들 때 두 개의 주요 필드가 있습니다.

* **[제목](#title)**:
   * 콘솔에서 사용자에게 표시되고, 편집할 때 페이지 콘텐츠 상단에 표시됩니다.
   * 이 필드는 옵션입니다.
* **[이름](#name)**:
   * URI를 생성하는 데 사용됩니다.
   * 이 필드에 대한 사용자 입력은 옵션입니다. 지정하지 않을 경우 이름이 제목에서 파생됩니다. 자세한 내용은 [페이지 이름 제한 및 모범 사례](#page-name-restrictions-and-best-practices) 섹션을 참조하십시오.

### 페이지 이름 제한 사항 및 모범 사례 {#page-name-restrictions-and-best-practices}

페이지 **제목** 및 **이름**&#x200B;은 별도로 작성할 수 있지만 관련되어 있습니다.

* 페이지를 생성할 때 **제목** 필드만 필요합니다. 페이지 생성 시 **이름**&#x200B;을 제공하지 않으면 AEM은 제목의 처음 64자에서 이름을 생성합니다(아래에 작성된 유효성 검사 관찰). 짧은 페이지 이름에 대한 모범 사례를 지원하기 위해 처음 64자만 사용됩니다.
* 작성자가 페이지 이름을 수동으로 지정하는 경우 64자 제한이 적용되지 않지만, 페이지 이름 길이에 대한 다른 기술 제한 사항은 적용될 수 있습니다.

>[!TIP]
>
>페이지 이름을 정의할 때 되도록이면 간단하게 지정하되, 함축적이며 기억하기 쉽게 지정하여 독자가 쉽게 이해할 수 있도록 하는 것이 좋습니다. 자세한 내용은 `title` 요소에 대한 [W3C 스타일 가이드](https://www.w3.org/Provider/Style/TITLE.html)를 참조하십시오.
>
>일부 브라우저(예: 이전 버전의 IE)는 특정 길이까지만 URL을 허용하므로 기술적인 이유로 페이지 이름을 짧게 유지하는 경우도 있습니다.

페이지를 만들 때 AEM [규칙에 따라 페이지 이름을 확인합니다.](/help/implementing/developing/introduction/naming-conventions.md) AEM 및 JCR에서 적용합니다.

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

### 제목 {#title}

페이지만 제공하는 경우 **제목** 페이지를 만들 때 AEM은 페이지를 파생합니다 **이름** 이 문자열에서 [규칙에 따라 이름 확인](/help/implementing/developing/introduction/naming-conventions.md) AEM 및 JCR에서 적용합니다.

**제목** 필드에는 잘못된 문자가 포함될 수 있지만, 파생되는 이름에서는 잘못된 문자가 대체됩니다. 예:

| 제목 | 파생되는 이름 |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;&#42;ç+ | `sc---c-.html` |

### 이름 {#name}

페이지를 제공할 때 **이름** 페이지를 만들 때 AEM [규칙에 따라 이름을 확인합니다.](/help/implementing/developing/introduction/naming-conventions.md) AEM 및 JCR에서 적용합니다. **이름** 필드에 잘못된 문자를 제출할 수 없습니다. AEM에서 유효하지 않은 문자를 발견하면 필드가 설명 메시지와 함께 강조 표시됩니다.

![유효하지 않은 페이지 이름을 입력하는 예](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>언어 루트가 아닌 경우 ISO-639-1에 따라 페이지 이름으로 정의된 두 문자 코드를 사용할 수 없습니다.
>
>자세한 내용은 [콘텐츠 번역 준비](/help/sites-cloud/administering/translation/preparation.md)를 참조하십시오.

## 템플릿 {#templates}

AEM에서 [템플릿](/help/sites-cloud/authoring/sites-console/templates.md) 는 만들어지는 새 페이지의 기반으로 사용되는 특수한 유형의 페이지입니다.

템플릿은 썸네일 이미지 및 기타 속성을 포함하는 페이지의 구조를 정의합니다. 예를 들어 제품 페이지, 사이트맵 및 연락처 정보에 대한 별도의 템플릿이 있을 수 있습니다. 템플릿은 [구성 요소](#components)로 구성됩니다.

AEM에는 특별히 제공되는 몇 개의 템플릿이 있습니다. 사용 가능한 템플릿은 개별 웹 사이트에 따라 다릅니다. 주요 필드는 다음과 같습니다.

* **제목** - 결과 웹 페이지에 표시되는 제목
* **이름** - 페이지 이름을 지정할 때 사용됩니다.
* **템플릿** - 새 페이지를 생성하는 데 사용할 수 있는 템플릿 목록

## 구성 요소 {#components}

[구성 요소](/help/implementing/developing/components/overview.md) 는 특정 유형의 컨텐츠를 추가할 수 있도록 AEM에서 제공하는 요소입니다. AEM에는 다음과 같은 기본 제공 구성 요소가 포함되어 있습니다. [핵심 구성 요소](/help/implementing/developing/components/overview.md#core-components) 포괄적인 기능을 제공합니다. 구성 요소의 몇 가지 예는 다음과 같습니다.

* 텍스트
* 이미지
* 제목
* 회전판
* 기타

페이지를 생성하여 열면 [구성 요소 브라우저](/help/sites-cloud/authoring/page-editor/edit-content.md#inserting-a-component)의 [구성 요소를 사용하여 콘텐츠를 추가](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser)할 수 있습니다.

>[!TIP]
>
>[구성 요소 콘솔](/help/sites-cloud/authoring/components-console.md)은 인스턴스에 대한 구성 요소 개요를 제공합니다.
