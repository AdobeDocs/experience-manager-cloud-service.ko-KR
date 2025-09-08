---
title: 필터링 구성 요소
description: 범용 편집기에서 구성 요소 필터를 사용하여 컨테이너당 허용되는 구성 요소를 제한하는 방법에 대해 알아봅니다.
feature: Developing
role: Admin, Architect, Developer
exl-id: eeae8d7c-c563-4d9b-8c54-1098a4e98c18
source-git-commit: cdad4954b13f5582bebfd604220da90529231ccd
workflow-type: ht
source-wordcount: '153'
ht-degree: 100%

---

# 필터링 구성 요소 {#filtering-components}

범용 편집기에서 구성 요소 필터를 사용하여 컨테이너당 허용되는 구성 요소를 제한하는 방법에 대해 알아봅니다.

## 필터 {#filters}

범용 편집기를 사용하는 경우 컨테이너 구성 요소당 허용되는 구성 요소를 제한할 수 있습니다. 이렇게 하려면 필터 정의를 가리키는 추가 스크립트 태그를 도입해야 합니다.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

필터 정의는 다음과 같을 수 있으며, 컨테이너에 텍스트와 이미지만 추가할 수 있도록 제한합니다.

```json
[
  {
    "id": "container-filter",
     "components": ["text", "image"]
   }
]
```

그런 다음 `data-aue-filter` 속성을 추가하여 이전에 정의한 필터의 ID를 전달하여 컨테이너 구성 요소에서 필터 정의를 참조할 수 있습니다.

```html
data-aue-filter="container-filter"
```

필터 정의의 `components` 속성을 `null`로 설정하면 필터가 없는 것처럼 모든 구성 요소를 허용합니다.

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
>문서에서 범용 편집기에 사용할 수 있는 다른 사용자 정의 및 확장 옵션에 대해 알아봅니다.
>
>* [범용 편집기 사용자 정의](/help/implementing/universal-editor/customizing.md)
>* [범용 편집기 확장](/help/implementing/universal-editor/extending.md)
