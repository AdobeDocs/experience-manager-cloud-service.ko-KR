---
title: UI 맞춤화
description: 콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 UI를 사용자 지정할 수 있는 다양한 확장 지점에 대해 알아봅니다.
source-git-commit: 65893c0c0dee37bed8ecfbb06a12e7c093c4397c
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# UI 맞춤화 {#customizing-ui}

콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 UI를 사용자 지정할 수 있는 다양한 확장 지점에 대해 알아봅니다.

## 게시 비활성화 {#disable-publish}

특정 작성 워크플로에서는 콘텐츠를 게시하기 전에 검토해야 합니다. 이러한 경우 작성자는 게시 옵션을 사용할 수 없습니다.

다음 **게시** 따라서 다음 메타데이터를 추가하여 앱에서 버튼을 완전히 억제할 수 있습니다.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```
