---
title: Universal Editor 사용자 정의
description: 콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기를 사용자 지정하는 다양한 옵션에 대해 알아봅니다.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: cdad4954b13f5582bebfd604220da90529231ccd
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 10%

---


# Universal Editor 사용자 정의 {#customizing}

콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기를 사용자 지정하는 다양한 옵션에 대해 알아봅니다.

>[!TIP]
>
>또한 유니버설 편집기는 프로젝트 요구 사항에 맞게 기능을 확장할 수 있는 많은 [확장 지점](/help/implementing/universal-editor/extending.md)을 제공합니다.

## 게시 비활성화 {#disable-publish}

특정 작성 워크플로에서는 콘텐츠를 게시하기 전에 검토해야 합니다. 이러한 경우 작성자는 게시 옵션을 사용할 수 없습니다.

따라서 다음 메타데이터를 추가하여 **Publish** 단추를 앱에서 완전히 표시하지 않을 수 있습니다.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## 필터링 구성 요소 {#filtering-components}

구성 요소 필터를 사용하여 유니버설 편집기에서 컨테이너당 허용된 구성 요소를 제한할 수 있습니다. 자세한 내용은 [구성 요소 필터링](/help/implementing/universal-editor/filtering.md) 문서를 참조하십시오.

## [속성] 패널에서 구성 요소를 조건부로 표시 및 숨기기 {#conditionally-hide}

일반적으로 작성자가 구성 요소를 사용할 수 있지만 의미가 없는 상황이 있을 수 있습니다. 이러한 경우 구성 요소 모델의 [필드](/help/implementing/universal-editor/field-types.md#fields)에 `condition` 특성을 추가하여 속성 패널에서 구성 요소를 숨길 수 있습니다.

[JsonLogic 스키마](https://jsonlogic.com/)를 사용하여 조건을 정의할 수 있습니다. 조건이 true이면 필드가 표시됩니다. 조건이 false이면 필드가 숨겨집니다.

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

## 사용자 지정 미리보기 URL {#custom-preview-urls}

[편집기의 오른쪽 상단 도구 모음](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar)에서 **페이지 열기** 단추를 클릭하면 열리는 `urn:adobe:aue:config:preview` 메타 구성을 통해 사용자 지정 미리 보기 URL을 지정할 수 있습니다.

이 기능은 [WYSIWYG 작성 시 Edge Delivery Services를 사용하는](/help/edge/wysiwyg-authoring/authoring.md) 애플리케이션과 같이 특정 미리보기 요구 사항이 있는 애플리케이션에 특히 유용합니다.

이렇게 하려면 다음 예제와 같이 원하는 미리보기 URL을 계측된 앱의 메타 태그에 포함하기만 하면 됩니다.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```
