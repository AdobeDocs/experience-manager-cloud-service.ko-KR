---
title: 페이지 편집기 제한 사항
description: 페이지 편집기는 오버레이를 사용하여 iframe에 한정된 컨텐츠와 상호 작용합니다. 이러한 상호 작용은 편집자와 개발자의 사용에 모두 제한을 만듭니다.
exl-id: 6a4f0e43-1076-4da9-95dc-9c5bf83e30d0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8b38e26b16c1fb565f122777f0577d332f62c39c
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 4%

---


# 페이지 편집기 제한 사항 {#editor-limitations}

[페이지 편집기](/help/sites-cloud/authoring/page-editor/introduction.md)에서 오버레이를 사용하여 iframe에 한정된 콘텐츠와 상호 작용합니다. 이러한 상호 작용은 편집기와 개발자의 사용에 모두 제한을 만듭니다. 이 페이지에서는 이러한 제한 사항을 요약하고 가능한 경우 해결 방법 또는 해결 방법을 제공합니다.

## 기능 제한 사항 {#functional-limitations}

작성자는 편집기를 사용하여 페이지를 작성할 때 다음과 같은 기능 제한을 받을 수 있습니다.

### 링크가 활성화되지 않음 {#links-not-active}

[페이지를 편집](/help/sites-cloud/authoring/page-editor/edit-content.md)할 때 링크가 활성화되지 않습니다.

* 콘텐츠의 링크를 사용하여 탐색하려면 [**미리 보기** 모드로 전환](/help/sites-cloud/authoring/page-editor/introduction.md#preview-mode)하세요.

### 구조 페이지 {#structure-pages}

페이지 이름을 `structure`로 지정할 수 없습니다. 이름이 `structure`인 페이지는 페이지 편집기에서 편집할 수 없습니다.

## CSS 제한 사항 {#css-limitations}

개발자는 편집기의 CSS 상호 작용에 다음과 같은 제한 사항이 있을 수 있습니다.

### 절대 위치 요소 {#absolutely-positioned-elements}

요소가 절대적으로 배치되면 해당 오버레이 위치에 문제가 발생할 수 있습니다.

* 이 경우 편집기에서 정확히 동일한 치수로 오버레이를 생성하므로 절대 위치에 있는 요소의 치수가 올바른지 확인하십시오.

### vh 단위 {#vh-units}

AEM에서 iframe 높이를 자동으로 조정해야 하므로 `vh` 단위가 지원되지 않습니다.

### 고정 배경 이미지 {#fixed-background-images}

고정 배경 이미지는 iframe 내에 포함되어 있으므로 스크롤할 때 고정으로 표시되지 않을 수 있습니다.

* 헤더 표시줄 작업에서 **게시됨으로 페이지 보기**&#x200B;를 선택하면 페이지가 제대로 표시됩니다.

### 100% 높이 {#height}

페이지의 본문 요소에서는 100% 높이가 지원되지 않습니다.

* 다음과 같이 본문 요소를 &quot;스트레칭&quot;하여 전체 화면 본문을 구현할 수 있습니다.

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### 여백 축소 {#margin-collapsing}

바디 요소의 첫 번째 자식 요소에 여백이 있으면 여백 축소 문제가 표시됩니다.

* 해결 방법은 다음과 같이 바디 요소 레벨에 클리어픽스를 추가하는 것입니다.

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
