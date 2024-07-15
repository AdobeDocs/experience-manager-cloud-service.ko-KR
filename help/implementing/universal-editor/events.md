---
title: 유니버설 편집기 이벤트
description: 범용 편집기에서 원격 앱의 콘텐츠 또는 UI 변경 사항에 대응하는 데 사용할 수 있도록 보내는 다양한 이벤트에 대해 알아봅니다.
exl-id: c9f7c284-f378-4725-a4e6-e4799f0f8175
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 2%

---

# 유니버설 편집기 이벤트 {#events}

범용 편집기에서 원격 앱의 콘텐츠 또는 UI 변경 사항에 대응하는 데 사용할 수 있도록 보내는 다양한 이벤트에 대해 알아봅니다.

## 소개 {#introduction}

애플리케이션에는 페이지 또는 구성 요소 업데이트에 대한 요구 사항이 다를 수 있습니다. 따라서 유니버설 편집기는 정의된 이벤트를 원격 응용 프로그램으로 보냅니다. 원격 응용 프로그램에 보낸 이벤트에 대한 사용자 지정 이벤트 수신기가 없는 경우 `universal-editor-cors` 패키지에서 제공하는 [대체 이벤트 수신기](#fallback-listeners)가 실행됩니다.

모든 이벤트는 원격 페이지의 영향을 받는 DOM 요소에서 호출됩니다. `universal-editor-cors` 패키지에서 제공한 기본 이벤트 수신기가 등록된 `BODY` 요소까지 이벤트가 버블링됩니다. 콘텐츠에는 이벤트가 있고 UI에는 이벤트가 있습니다.

모든 이벤트는 명명 규칙을 따릅니다.

* `aue:<content-or-ui>-<event-name>`

예: `aue:content-update` 및 `aue:ui-select`

이벤트에는 요청 및 응답의 페이로드가 포함되며 해당 호출이 성공하면 트리거됩니다. 호출 및 페이로드의 예제에 대한 자세한 내용은 [범용 편집기 호출](/help/implementing/universal-editor/calls.md) 문서를 참조하십시오.

## 컨텐츠 업데이트 이벤트 {#content-events}

### aue:content-add {#content-add}

새 구성 요소가 컨테이너에 추가되면 `aue:content-add` 이벤트가 트리거됩니다.

페이로드는 유니버설 편집기 서비스의 콘텐츠이며, 구성 요소 정의의 대체 콘텐츠는 입니다.

```json
{
    details: {
        request: request payload;   // what is sent to the service
        response: {                 // what is returned by the service
            resource: string;       // newly created content resource
            updates: [{
                resource: string;   // resource to update
                type: string;       // type of instrumentation
                content?: string;   // content to replace
            }]
        }
    }
}
```

### aue:content-details {#content-details}

구성 요소가 속성 레일에 로드되면 `aue:content-details` 이벤트가 트리거됩니다.

페이로드는 구성 요소의 콘텐츠 및 선택적으로 해당 스키마입니다.

```json
{
    details: {
        content: object             // content object
        model: [object]             // model object
        request: request payload;   // what is sent to the service
        response: response payload; // what is returned by the service
    }
}
```

### aue:content-move {#content-move}

구성 요소를 이동할 때 `aue:content-move` 이벤트가 트리거됩니다.

페이로드는 구성 요소, 소스 컨테이너 및 대상 컨테이너입니다.

```json
{
    details: {
        from: string;                   // container we move the component from
        component: string;              // component we move
        to: string;                     // container we move the component to
        before: string;                    // before which component shall we place the component
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-patch {#content-patch}

`aue:content-patch` 이벤트는 구성 요소의 데이터가 속성 레일에서 업데이트될 때 트리거됩니다.

페이로드는 업데이트된 속성의 JSON 패치입니다.

```json
{
    details: {
        patch: {
            name: string;               // attribute which is updated
            value: string;              // new value which is stored to the attribute
        },
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-remove {#content-remove}

`aue:content-remove` 이벤트는 구성 요소가 컨테이너에서 제거될 때 트리거됩니다.

페이로드는 제거된 구성 요소의 항목 ID입니다.

```json
{
    details: {
        resource: string;               // the resource which got removed
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-update {#content-update}

`aue:content-update` 이벤트는 구성 요소의 속성이 컨텍스트 내에서 업데이트될 때 트리거됩니다.

페이로드는 업데이트된 값입니다.

```json
{
    details: {
        value: string;                  // updated value
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service 
    }
}
```

### 페이로드 전달 {#passing-payloads}

모든 콘텐츠 업데이트 이벤트에 대해 요청된 페이로드와 응답 페이로드가 이벤트에 전달됩니다. 예: 업데이트 호출:

요청 페이로드:

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-p7452-e12433.adobeaemcloud.com"
    }
  ],
  "target": {
    "resource": "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
    "type": "text",
    "prop": "title"
  },
  "value": "Alhoa Spirit Northern Norway!"
}
```

응답 페이로드

```json
{
    "updates": [
        {
            "resource": "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
            "prop": "title",
            "type": "text"
        }
    ]
}
```

## UI 이벤트 {#ui-events}

### aue:ui-publish {#ui-publish}

`BODY` 수준에서 호출을 사용하여 콘텐츠가 게시될 때 `aue:ui-publish` 이벤트가 트리거됩니다.

페이로드는 항목 ID 및 게시 상태 목록입니다.

### aue:ui-select {#ui-select}

구성 요소를 선택하면 `aue:ui-select` 이벤트가 트리거됩니다.

페이로드는 선택한 구성 요소의 항목 ID, 항목 속성 및 항목 유형입니다.

```json
{
    details: {
        resource: string;       // resource of the selected
        prop: string;           // prop of the selected
        type: string;           // type of the selected
        selected: boolean;      // was selected or unselected
    }
}
```

### aue:ui-preview {#ui-preview}

페이지의 편집 모드가 **미리 보기**(으)로 변경되면 `aue:ui-preview` 이벤트가 트리거됩니다.

이 이벤트에 대한 페이로드가 비어 있습니다.

```json
{
    details: {}
}
```

### aue:ui-edit {#ui-edit}

페이지의 편집 모드가 **편집**(으)로 변경되면 `aue:ui-edit` 이벤트가 트리거됩니다.

이 이벤트에 대한 페이로드가 비어 있습니다.

```json
{
    details: {}
}
```

### aue:ui-viewport-change {#ui-viewport-change}

뷰포트 크기가 변경되면 `aue:ui-viewport-change` 이벤트가 트리거됩니다.

페이로드는 뷰포트의 차원입니다.

```json
{
    details: {
        height: number?;        // height of the viewport. Undefined when fullscreen
        width: number?;         // width of the viewport. Undefined when fullscreen
    }
}
```

### aue:초기화됨 {#initialized}

`aue:initialized` 이벤트가 트리거되어 원격 페이지가 유니버설 편집기에서 성공적으로 로드되었음을 알 수 있습니다.

이 이벤트에 대한 페이로드가 비어 있습니다.

```json
{
    details: {}
}
```

## 대체 이벤트 리스너 {#fallback-listeners}

### 콘텐츠 업데이트 {#content-update-fallbacks}

| 이벤트 | 동작 |
|---|---|
| `aue:content-add` | 페이지 다시 로드 |
| `aue:content-details` | 아무 작업도 하지 않음 |
| `aue:content-move` | 구성 요소의 콘텐츠/구조를 대상 영역으로 이동합니다. |
| `aue:content-patch` | 페이지 다시 로드 |
| `aue:content-remove` | DOM 요소 제거 |
| `aue:content-update` | 페이로드로 `innerHTML` 업데이트 |

### UI 이벤트 {#ui-event-fallbacks}

| 이벤트 | 동작 |
|---|---|
| `aue:ui-publish` | 아무 작업도 하지 않음 |
| `aue:ui-select` | 선택한 요소로 스크롤 |
| `aue:ui-preview` | HTML 태그에 `class="adobe-ue-preview"` 추가 |
| `aue:ui-edit` | HTML 태그에 `class=adobe-ue-edit"` 추가 |
| `aue:ui-viewport-change` | 아무 작업도 하지 않음 |
| `aue:initialized` | 아무 작업도 하지 않음 |

## 추가 리소스 {#additional-resources}

* [Universal Editor 호출](/help/implementing/universal-editor/calls.md)

