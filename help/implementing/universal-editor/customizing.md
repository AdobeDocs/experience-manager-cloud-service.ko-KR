---
title: UI 맞춤화
description: 콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 UI를 사용자 지정할 수 있는 다양한 확장 지점에 대해 알아봅니다.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: 1bc65e65e6ce074a050e21137ce538b5c086665f
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 3%

---


# UI 맞춤화 {#customizing-ui}

콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 UI를 사용자 지정할 수 있는 다양한 확장 지점에 대해 알아봅니다.

## 게시 비활성화 {#disable-publish}

특정 작성 워크플로에서는 콘텐츠를 게시하기 전에 검토해야 합니다. 이러한 경우 작성자는 게시 옵션을 사용할 수 없습니다.

다음 **게시** 따라서 다음 메타데이터를 추가하여 앱에서 버튼을 완전히 억제할 수 있습니다.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## 구성 요소 필터링 {#filtering-components}

유니버설 편집기를 사용하는 경우 컨테이너 구성 요소별로 허용된 구성 요소를 제한할 수 있습니다. 이렇게 하려면 필터 정의를 가리키는 추가 스크립트 태그를 도입해야 합니다.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

필터 정의는 다음과 같을 수 있으며, 이렇게 하면 텍스트 및 이미지 추가만 허용하도록 컨테이너가 제한됩니다.

```json
[
  {
    "id": "container-filter",
     "components": ["text", "image"]
   }
]
```

그런 다음 속성을 추가하여 컨테이너 구성 요소에서 필터 정의를 참조할 수 있습니다 `data-aue-filter`를 통해 이전에 정의한 필터의 ID를 전달합니다.

```html
data-aue-filter="container-filter"
```

설정 `components` 필터 정의의 속성 `null` 필터가 없는 것처럼 모든 구성 요소를 허용합니다.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```
