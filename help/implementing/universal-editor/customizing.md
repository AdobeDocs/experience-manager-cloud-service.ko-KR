---
title: 범용 편집기 사용자 지정 및 확장
description: 콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 UI를 사용자 지정할 수 있는 다양한 확장 지점 및 기타 기능에 대해 알아봅니다.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 1%

---


# 범용 편집기 사용자 지정 및 확장 {#customizing-extending}

콘텐츠 작성자의 요구 사항을 지원하도록 범용 편집기의 작성 환경을 사용자 정의할 수 있는 다양한 확장 지점 및 기타 기능에 대해 알아봅니다.

## 개요 {#overview}

유니버설 편집기를 사용하면 프로젝트의 요구 사항에 맞게 두 가지 유형을 조정할 수 있습니다.

* [범용 편집기 사용자 지정](#customizing) - 여러 사용자 지정 구성을 통해 범용 편집기의 표준 기능을 조정할 수 있습니다.
* [유니버설 편집기 UI 확장](#extending) - 프로젝트 요구 사항에 맞게 App Builder을 사용하여 유니버설 편집기의 UI를 확장할 수도 있습니다.

두 유형 모두 다음 섹션에 자세히 설명되어 있습니다.

## Universal Editor 사용자 정의 {#customizing}

유니버설 편집기는 기능을 사용자 지정할 수 있는 몇 가지 내장 옵션을 제공합니다.

### 게시 비활성화 {#disable-publish}

특정 작성 워크플로에서는 콘텐츠를 게시하기 전에 검토해야 합니다. 이러한 경우 작성자는 게시 옵션을 사용할 수 없습니다.

따라서 다음 메타데이터를 추가하여 **Publish** 단추를 앱에서 완전히 표시하지 않을 수 있습니다.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

### 구성 요소 필터링 {#filtering-components}

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

### 속성 레일에서 조건부로 구성 요소 표시 및 숨기기 {#conditionally-hide}

일반적으로 작성자가 구성 요소를 사용할 수 있지만 의미가 없는 상황이 있을 수 있습니다. 이러한 경우 구성 요소 모델의 [ 필드에 `condition` 특성을 추가하여 속성 레일에서 구성 요소를 숨길 수 있습니다.](/help/implementing/universal-editor/field-types.md#fields)

[JsonLogic 스키마를 사용하여 조건을 정의할 수 있습니다.](https://jsonlogic.com/) 조건이 true이면 필드가 표시됩니다. 조건이 false이면 필드가 숨겨집니다.

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

## 범용 편집기 UI 확장 {#extending}

Adobe Experience Cloud 서비스로서, App Builder 및 Experience Manager을 사용하여 유니버설 편집기의 UI를 확장할 수 있습니다.

UI 확장은 Adobe App Builder으로 구축된 JavaScript 애플리케이션으로, 범용 편집기와 같은 Adobe Experience Cloud 통합 셸에서 실행되는 UI 애플리케이션에 임베드할 수 있습니다. 헤더 메뉴 및 속성 레일에 고유한 버튼과 작업을 추가할 수 있을 뿐만 아니라 범용 편집기에 대한 고유한 이벤트를 만들 수도 있습니다.

이러한 가능성을 알아보려면 다음 리소스를 참조하십시오.

1. [UI 확장성](https://developer.adobe.com/uix/docs/) - UI 확장에 대한 개발자 설명서입니다.
1. [UI 확장성 안내서](https://developer.adobe.com/uix/docs/guides/) - 고유한 확장을 개발하는 방법에 대한 단계별 지침
1. [유니버설 편집기 확장 지점](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - 유니버설 편집기 특정 확장 지점 문서

>[!TIP]
>
>예제를 통한 학습을 선호하는 경우 [AEM UI 확장성 자습서를 참조하십시오.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview) 콘텐츠 조각 콘솔 확장에 중점을 두고 있지만 유니버설 편집기에서 UI 확장을 구현하는 개념은 동일합니다.

[AEM Sites에서 Extension Manager을 사용](https://developer.adobe.com/uix/docs/extension-manager/) 인스턴스별로 확장을 활성화하거나 비활성화하고, 유니버설 편집기의 확장을 포함한 Adobe의 자사 확장에 액세스할 수 있습니다.
