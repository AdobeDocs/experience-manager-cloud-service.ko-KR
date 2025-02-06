---
title: 필터링 구성 요소
description: 구성 요소 필터를 사용하여 유니버설 편집기에서 컨테이너당 허용된 구성 요소를 제한하는 방법에 대해 알아봅니다.
feature: Developing
role: Admin, Architect, Developer
exl-id: eeae8d7c-c563-4d9b-8c54-1098a4e98c18
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---

# 필터링 구성 요소 {#filtering-components}

구성 요소 필터를 사용하여 유니버설 편집기에서 컨테이너당 허용된 구성 요소를 제한하는 방법에 대해 알아봅니다.

## 필터 {#filters}

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

그런 다음 `data-aue-filter` 속성을 추가하고 이전에 정의한 필터의 ID를 전달하여 컨테이너 구성 요소에서 필터 정의를 참조할 수 있습니다.

```html
data-aue-filter="container-filter"
```

필터 정의의 `components` 특성을 `null`(으)로 설정하면 필터가 없는 것처럼 모든 구성 요소가 허용됩니다.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

>[!TIP]
>
>[유니버설 편집기 사용자 지정 및 확장](/help/implementing/universal-editor/customizing.md) 문서에서 유니버설 편집기에서 사용할 수 있는 다른 사용자 지정 및 확장 옵션에 대해 알아봅니다.