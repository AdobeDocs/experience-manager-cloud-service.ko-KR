---
title: 편집기 제한 사항
description: 터치 지원 UI의 편집기는 오버레이를 사용하여 iframe에 한정된 컨텐츠와 상호 작용합니다. 이러한 상호 작용은 편집자와 개발자의 사용에 모두 제한을 만듭니다.
exl-id: 6a4f0e43-1076-4da9-95dc-9c5bf83e30d0
source-git-commit: bceec9ea6858b1c4c042ecd96f13ae5cac1bbee5
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 10%

---

# 편집기 제한 사항 {#editor-limitations}

터치 지원 UI의 편집기는 오버레이를 사용하여 iframe에 한정된 컨텐츠와 상호 작용합니다. 이러한 상호 작용은 편집자와 개발자의 사용에 모두 제한을 만듭니다. 이 페이지에서는 이러한 제한 사항을 요약하고 가능한 경우 해결 방법 또는 해결 방법을 제공합니다.

## 기능 제한 사항 {#functional-limitations}

작성자는 편집기를 사용하여 페이지를 작성할 때 다음과 같은 기능 제한을 받을 수 있습니다.

### 링크가 활성화되지 않음 {#links-not-active}

날짜 [페이지 편집](/help/sites-cloud/authoring/fundamentals/editing-content.md), 링크가 활성화되지 않았습니다.

* [다음으로 전환 **미리 보기** 모드](/help/sites-cloud/authoring/fundamentals/editing-content.md#preview-mode) 을 클릭하여 콘텐츠의 링크를 사용하여 탐색할 수 있습니다.

### 구조 페이지 {#structure-pages}

페이지 이름을 지정할 수 없습니다. `structure`. 이름이 지정된 페이지 `structure` 페이지 편집기에서 편집할 수 없습니다.

## CSS 제한 사항 {#css-limitations}

개발자는 편집기의 CSS 상호 작용에 다음과 같은 제한 사항이 있을 수 있습니다.

### 절대 위치 요소 {#absolutely-positioned-elements}

요소가 절대적으로 배치되면 해당 오버레이 위치에 문제가 발생할 수 있습니다.

* 이 경우 편집기에서 정확히 동일한 치수로 오버레이를 생성하므로 절대 위치에 있는 요소의 치수가 올바른지 확인하십시오.

### vh 단위 {#vh-units}

`vh` iframe 높이는 AEM에서 자동으로 조정해야 하므로 단위가 지원되지 않습니다.

### 고정 배경 이미지 {#fixed-background-images}

고정 배경 이미지는 iframe 내에 포함되어 있으므로 스크롤할 때 고정으로 표시되지 않을 수 있습니다.

* 선택 **페이지를 게시됨으로 보기** 헤더 막대에서 작업이 페이지를 제대로 표시합니다.

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
