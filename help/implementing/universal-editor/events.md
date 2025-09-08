---
title: 범용 편집기 이벤트
description: 원격 앱에서 콘텐츠 또는 UI 변경에 반응하는 데 사용할 수 있는 범용 편집기에서 전송되는 다양한 이벤트에 대해 알아봅니다.
exl-id: c9f7c284-f378-4725-a4e6-e4799f0f8175
feature: Developing
role: Admin, Architect, Developer
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: ht
source-wordcount: '510'
ht-degree: 100%

---

# 범용 편집기 이벤트 {#events}

원격 앱에서 콘텐츠 또는 UI 변경에 반응하는 데 사용할 수 있는 범용 편집기에서 전송되는 다양한 이벤트에 대해 알아봅니다.

## 소개 {#introduction}

애플리케이션마다 페이지 또는 구성 요소 업데이트에 대한 요구 사항이 다를 수 있습니다. 따라서 범용 편집기는 정의된 이벤트를 원격 애플리케이션에 전송합니다. 원격 애플리케이션에 전송된 이벤트에 대한 사용자 정의 이벤트 리스너가 없는 경우 `universal-editor-cors` 패키지에서 제공하는 [대체 이벤트 리스너](#fallback-listeners)가 실행됩니다.

모든 이벤트는 원격 페이지의 영향을 받는 DOM 요소에서 호출됩니다. `universal-editor-cors` 패키지에서 제공하는 기본 이벤트 리스너가 등록된 `BODY` 요소로 이벤트가 버블링됩니다. 콘텐츠에 대한 이벤트와 UI에 대한 이벤트가 있습니다.

모든 이벤트는 명명 규칙을 따릅니다.

* `aue:<content-or-ui>-<event-name>`

예: `aue:content-update` 및 `aue:ui-select`

이벤트에는 요청 및 응답의 페이로드가 포함되며 해당 호출이 성공하면 트리거됩니다. 호출 및 페이로드 예시에 대한 자세한 내용은 [범용 편집기 호출](/help/implementing/universal-editor/calls.md) 설명서를 참조하십시오.

## 콘텐츠 업데이트 이벤트 {#content-events}

### aue:content-add {#content-add}

`aue:content-add` 이벤트는 새 구성 요소가 컨테이너에 추가될 때 트리거됩니다.

페이로드는 범용 편집기 서비스의 콘텐츠이며, 구성 요소 정의의 대체 콘텐츠가 포함됩니다.

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

`aue:content-details` 이벤트는 구성 요소가 속성 패널에 로드될 때 트리거됩니다.

페이로드는 구성 요소의 콘텐츠이며, 선택적으로 스키마입니다.

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

`aue:content-move` 이벤트는 구성 요소가 이동될 때 트리거됩니다.

페이로드는 구성 요소의 콘텐츠와 선택적으로 해당 스키마입니다.

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

`aue:content-patch` 이벤트는 속성 패널에서 구성 요소의 데이터가 업데이트될 때 트리거됩니다.

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

`aue:content-remove` 이벤트는 컨테이너에서 구성 요소가 제거될 때 트리거됩니다.

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

모든 콘텐츠 업데이트 이벤트의 경우 요청된 페이로드와 응답 페이로드가 이벤트로 전달됩니다. 예: 업데이트 호출의 경우:

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

### aue:ui-preview {#ui-preview}

이 `aue:ui-preview` 이벤트는 페이지의 편집 모드가 **미리보기**&#x200B;로 변경될 때 트리거됩니다.

이 이벤트의 페이로드는 비어 있습니다.

```json
{
    details: {}
}
```

### aue:ui-edit {#ui-edit}

이 `aue:ui-edit` 이벤트는 페이지의 편집 모드가 **편집**&#x200B;으로 변경될 때 트리거됩니다.

이 이벤트의 페이로드는 비어 있습니다.

```json
{
    details: {}
}
```

### aue:ui-viewport-change {#ui-viewport-change}

`aue:ui-viewport-change` 이벤트는 뷰포트 크기가 변경될 때 트리거됩니다.

페이로드는 뷰포트의 차원입니다.

```json
{
    details: {
        height: number?;        // height of the viewport. Undefined when fullscreen
        width: number?;         // width of the viewport. Undefined when fullscreen
    }
}
```

### aue:initialized {#initialized}

`aue:initialized` 이벤트는 원격 페이지가 범용 편집기에서 성공적으로 로드되었음을 알리기 위해 트리거됩니다.

이 이벤트의 페이로드는 비어 있습니다.

```json
{
    details: {}
}
```

## 대체 이벤트 리스너 {#fallback-listeners}

### 콘텐츠 업데이트 {#content-update-fallbacks}

| 이벤트 | 비헤이비어 |
|---|---|
| `aue:content-add` | 페이지 다시 로드 |
| `aue:content-details` | 아무 작업도 수행하지 않음 |
| `aue:content-move` | 구성 요소의 콘텐츠/구조를 대상 영역으로 이동 |
| `aue:content-patch` | 페이지 다시 로드 |
| `aue:content-remove` | DOM 요소 제거 |
| `aue:content-update` | 페이로드로 `innerHTML` 업데이트 |

### UI 이벤트 {#ui-event-fallbacks}

| 이벤트 | 비헤이비어 |
|---|---|
| `aue:ui-select` | 선택한 요소로 스크롤 |
| `aue:ui-preview` | HTML 태그에 `class="adobe-ue-preview"` 추가 |
| `aue:ui-edit` | HTML 태그에 `class=adobe-ue-edit"` 추가 |
| `aue:ui-viewport-change` | 아무 작업도 수행하지 않음 |
| `aue:initialized` | 아무 작업도 수행하지 않음 |

## 추가 리소스 {#additional-resources}

* [범용 편집기 호출](/help/implementing/universal-editor/calls.md)

