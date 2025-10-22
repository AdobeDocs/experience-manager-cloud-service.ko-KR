---
title: 범용 편집기 사용자 정의
description: 콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기를 사용자 정의하는 다양한 옵션에 대해 알아봅니다.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: cb3cf5ee6bb17c33c118c6463272922e0e212c1a
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 67%

---


# 범용 편집기 사용자 정의 {#customizing}

콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기를 사용자 정의하는 다양한 옵션에 대해 알아봅니다.

>[!TIP]
>
>범용 편집기는 또한 프로젝트 요구 사항을 충족하도록 기능을 확장할 수 있는 여러 [확장 지점](/help/implementing/universal-editor/extending.md)을 제공합니다.

## Meta 구성 태그 사용 {#meta-tags}

특정 작성 워크플로에서는 유니버설 편집기의 일부 기능을 사용해야 할 수 있으며 다른 기능은 사용해야 하지 않을 수 있습니다. 이러한 다양한 경우를 지원하기 위해 편집기의 특정 기능이나 버튼을 구성하거나 비활성화하는 데 메타 태그를 사용할 수 있습니다.

페이지의 `<head>` 섹션에서 이 태그를 사용하여 하나 이상의 기능을 비활성화하십시오.

```html
<meta name="urn:adobe:aue:config:disable" content="..." />
```

여러 기능을 비활성화하려면 쉼표로 구분된 값 목록을 제공합니다.

다음은 `content`에 대해 지원되는 값, 즉 메타 태그를 사용하여 비활성화할 수 있는 기능입니다.

| 컨텐츠 값 | 설명 |
|---|---|
| `publish` | 모든 [게시](/help/sites-cloud/authoring/universal-editor/publishing.md) 기능, 즉 [게시 단추](/help/sites-cloud/authoring/universal-editor/navigation.md#publish) 및 [게시 취소 단추](/help/sites-cloud/authoring/universal-editor/navigation.md#ellipsis) 사용 안 함 |
| `publish-live` | 라이브 [게시](/help/sites-cloud/authoring/universal-editor/publishing.md) 사용 안 함 |
| `publish-preview` | 미리 보기 게시 비활성화([미리 보기 서비스](/help/sites-cloud/authoring/sites-console/previewing-content.md)를 사용할 수 있는 경우) |
| `unpublish` | [게시 취소 단추](/help/sites-cloud/authoring/universal-editor/publishing.md#unpublishing-content) 사용 안 함([미리 보기 기능](/help/release-notes/universal-editor/preview.md)) |
| `copy` | [복사 및 붙여넣기 단추](/help/sites-cloud/authoring/universal-editor/authoring.md#copy-paste)를 사용하지 않도록 설정합니다. |
| `duplicate` | [중복 단추](/help/sites-cloud/authoring/universal-editor/navigation.md#duplicate)를 사용하지 않도록 설정합니다. |
| `header-open-page` | [페이지 열기 단추](/help/sites-cloud/authoring/universal-editor/navigation.md#open-page)를 사용하지 않도록 설정합니다. |

## 엔드포인트 변경 {#custom-endpoint}

Adobe에서 호스팅하는 범용 편집기 서비스를 사용하지 않고 자체 호스팅 버전을 사용하려면 메타 태그에서 이 설정을 지정할 수 있습니다. 자세한 내용은 [AEM에서 범용 편집기 시작하기](/help/implementing/universal-editor/getting-started.md##configuration-settings) 문서를 참조하십시오.

## 필터링 구성 요소 {#filtering-components}

범용 편집기에서 구성 요소 필터를 사용하여 컨테이너당 허용되는 구성 요소를 제한할 수 있습니다. 자세한 내용은 [필터링 구성 요소](/help/implementing/universal-editor/filtering.md) 문서를 참조하십시오.

## 속성 패널에서 구성 요소를 조건부로 표시 및 숨기기 {#conditionally-hide}

일반적으로 작성자가 사용할 수 있는 구성 요소가 하나 이상 있더라도 적합하지 않은 특정 상황이 있을 수 있습니다. 이러한 경우 [구성 요소 모델의 필드](/help/implementing/universal-editor/field-types.md#fields)에 `condition` 속성을 추가하여 속성 패널에서 구성 요소를 숨길 수 있습니다.

조건은 [JsonLogic 스키마](https://jsonlogic.com/)를 사용하여 정의할 수 있습니다. 조건이 true이면 필드가 표시됩니다. 조건이 false이면 필드가 숨겨집니다.

>[!BEGINTABS]

>[!TAB 샘플 모델]

```json
 {
    "id": "conditionally-revealed-component",
    "fields": [
      {
        "component": "boolean",
        "label": "Shall the text field be revealed?",
        "name": "reveal",
        "valueType": "boolean"
      },
      {
        "component": "text-input",
        "label": "Hidden text field",
        "name": "hidden-text",
        "valueType": "string",
        "condition": { "===": [{"var" : "reveal"}, true] }
      }
    ]
 }
```

>[!TAB 조건 False]

![숨겨진 텍스트 필드](assets/hidden.png)

>[!TAB 조건 True]

![표시된 텍스트 필드](assets/shown.png)

>[!ENDTABS]

## 사용자 정의 미리보기 URL {#custom-preview-urls}

[편집기의 오른쪽 상단 도구 모음](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar)에서 **페이지 열기** 버튼을 클릭할 때 열리는 `urn:adobe:aue:config:preview` 메타 구성을 통해 사용자 정의 미리보기 URL을 지정할 수 있습니다.

이렇게 하려면 다음 예시와 같이 계측된 앱의 메타 태그에 원하는 미리보기 URL을 포함하면 됩니다.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```
